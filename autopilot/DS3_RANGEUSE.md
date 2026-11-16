# DS3_RANGEUSE - T-RANGEUSE: the walk-forward range forecast on D7 dials (W-RU). Rebuilt 2026-11-16T17:18Z by code/th_rangeuse/ru_loop.sh (every 3 h). Research only, NO PASS claim.
**VERDICT (plain): 74 cells scored through L6M; 6 (cell,scope) pass the tolerant gate with a drawdown cut in recent AND older windows (leads, before placebo/null); placebo/null/gain-of-(b,(c) over (a) below. No PASS claim.**

Prereg: autopilot/RANGEUSE_PREREG.md (sha in DECISIONS.md, logged before scoring). Order: DIRECTIVE_UW_3PART_20261113.md PART 2. Base JN05W2 exact engine, all layers ON. Identity: TL3_RU_ID 202610 (hook path active at neutral multipliers): 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL.
Months scored (cells with all months of the window / 98 cells): L3M 98, L6M 74, HOLD 50, PREUW 38. Driver: 0 jobs wanted, 0 chains running, 1794849511.

## 0. Method (short)
- Forecast = walk-forward ridge (expanding, min 120 days, refit every 10 trading days) of the session ln range at the reading used by the trade (asia/london R0 prior close; nyam R2 09:30 before 10:00 else R3 10:00; nypm R3). (a) ATR benchmark only, (b) ATR + IV term (NDX/QQQ/SPX), (c) full UW (b + SPX/QQQ flip, SPX/ALL4 gamma, NDX/SPX IV level, tide). Forecast points = predicted ln range x last close; ratio = prediction / expanding median of the past predictions; terciles from the expanding past. First forecasts exist from ~2025-03, so PREUW (2024-10..2025-06) is mostly unscored by the rule (rule inactive without a forecast = same as JN05W2).
- Cells run in the exact engine (own hook module ru_hooks.py, no shared engine file edited) as JN05W2 + one dial. Metrics vs JN05W2 on the same months: mean $/wk change, maxDD change in % (positive = smaller drawdown), worst-week change $, full stops/wk (cell(ref)), best-5 weeks kept % (cell $ in the 5 best JN05W2 weeks / their $), winning weeks turned losing. Per session = the same run sliced by entry session (asia london nyam nypm), books interact only through the shared engine.
- Tolerant gate per window: maxDD not worse by more than 2%, worst week not worse by more than 2% of the reference worst week, mean not lower than the reference by more than 3% of the reference mean $/wk. A LEAD must pass in L3M, L6M AND the older windows (HOLD, PREUW where scored); a lead is only called strong when it beats placebos (forecast shifted 11/23/37 days) and the permuted family null in section 5.
- Primary comparison = (b) over (a); (c) over (a) is secondary because (c) overfits. Ranking uses L3M + L6M (+HOLD when present) together, never one month; placebo and permuted null decide strength.
- Question per dial = gain of (b) and (c) over (a), not over no rule. Section 2 shows no-rule (JN05W2 = zero row), a, then b-a and c-a.

## 1. Forecast quality (out of sample, whole history ~2025-03..2026-11; R2 vs expanding mean of the target; all three share the walk-forward)
| session (reading) | R2 a ATR | R2 b +IV term | R2 c full UW | R2 L6M a/b/c | n |
|---|---|---|---|---|---|
| asia (R0) | 0.193 | 0.393 | 0.357 | 0.072/0.255/0.260 | 428 |
| london (R0) | 0.158 | 0.297 | 0.178 | -0.166/-0.015/-0.194 | 428 |
| nyam (R2) | 0.257 | 0.269 | 0.233 | 0.202/0.146/0.078 | 428 |
| nyam2 (R3) | 0.322 | 0.311 | 0.275 | 0.262/0.204/0.164 | 428 |
| nypm (R3) | 0.258 | 0.239 | 0.128 | -0.044/-0.024/-0.159 | 414 |

Note: (c) uses many UW columns and is NOT better than (b) out of sample in most sessions here: the ridge overfits (c); the IV-term group carries almost all of the UW range signal. This is stated so that "(c) gains over (a)" is read with that in mind.

## 2. Per dial: every cell, scope all and per session (exact engine, delta vs JN05W2; b-a and c-a gain rows)
### Dial 1 target-only scaling (stop unchanged)

**D1T1** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -6102 $/wk, DD -25.1%, ww -15344, stops 10.04(10.35), b5 92%, w2l 1 | n/a | n/a | n/a |
| all | b | -3494 $/wk, DD +26.0%, ww -2412, stops 10.20(10.35), b5 88%, w2l 1 | n/a | n/a | n/a |
| all | c | -3452 $/wk, DD +5.7%, ww +3376, stops 10.20(10.35), b5 90%, w2l 1 | n/a | n/a | n/a |
| all | **b-a** | +2608 $/wk, DD +51.1 pts, ww +12932 | n/a | n/a | n/a |
| all | **c-a** | +2650 $/wk, DD +30.9 pts, ww +18720 | n/a | n/a | n/a |
| asia | a | -2538 $/wk, DD -31.1%, ww -24789, stops 6.01(6.24), b5 100%, w2l 0 | n/a | n/a | n/a |
| asia | b | -775 $/wk, DD +12.8%, ww -17877, stops 6.62(6.24), b5 96%, w2l 1 | n/a | n/a | n/a |
| asia | c | -1401 $/wk, DD -12.3%, ww -18567, stops 6.47(6.24), b5 94%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | +1764 $/wk, DD +43.9 pts, ww +6912 | n/a | n/a | n/a |
| asia | **c-a** | +1137 $/wk, DD +18.7 pts, ww +6221 | n/a | n/a | n/a |
| london | a | -2145 $/wk, DD -11.4%, ww +596, stops 2.89(2.74), b5 78%, w2l 0 | n/a | n/a | n/a |
| london | b | -745 $/wk, DD +26.0%, ww +8983, stops 2.43(2.74), b5 78%, w2l 1 | n/a | n/a | n/a |
| london | c | -1104 $/wk, DD +1.2%, ww +1259, stops 2.51(2.74), b5 88%, w2l 1 | n/a | n/a | n/a |
| london | **b-a** | +1400 $/wk, DD +37.3 pts, ww +8386 | n/a | n/a | n/a |
| london | **c-a** | +1041 $/wk, DD +12.6 pts, ww +663 | n/a | n/a | n/a |
| nyam | a | -525 $/wk, DD +33.3%, ww -1606, stops 1.07(1.29), b5 60%, w2l 1 | n/a | n/a | n/a |
| nyam | b | -888 $/wk, DD +3.1%, ww -5528, stops 1.07(1.29), b5 61%, w2l 1 | n/a | n/a | n/a |
| nyam | c | -407 $/wk, DD -15.5%, ww -5528, stops 1.07(1.29), b5 82%, w2l 2 | n/a | n/a | n/a |
| nyam | **b-a** | -364 $/wk, DD -30.2 pts, ww -3922 | n/a | n/a | n/a |
| nyam | **c-a** | +118 $/wk, DD -48.8 pts, ww -3922 | n/a | n/a | n/a |
| nypm | a | -894 $/wk, DD -0.0%, ww +316, stops 0.08(0.08), b5 22%, w2l 2 | n/a | n/a | n/a |
| nypm | b | -1086 $/wk, DD -6.5%, ww +0, stops 0.08(0.08), b5 -2%, w2l 4 | n/a | n/a | n/a |
| nypm | c | -541 $/wk, DD -5.1%, ww +0, stops 0.15(0.08), b5 49%, w2l 2 | n/a | n/a | n/a |
| nypm | **b-a** | -192 $/wk, DD -6.5 pts, ww -316 | n/a | n/a | n/a |
| nypm | **c-a** | +354 $/wk, DD -5.1 pts, ww -316 | n/a | n/a | n/a |

**D1T2** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -9750 $/wk, DD -17.0%, ww -13340, stops 11.64(10.35), b5 82%, w2l 1 | n/a | n/a | n/a |
| all | b | -8671 $/wk, DD -25.4%, ww -15481, stops 11.34(10.35), b5 84%, w2l 1 | n/a | n/a | n/a |
| all | c | -8309 $/wk, DD -37.7%, ww -14423, stops 11.26(10.35), b5 94%, w2l 2 | n/a | n/a | n/a |
| all | **b-a** | +1079 $/wk, DD -8.4 pts, ww -2141 | n/a | n/a | n/a |
| all | **c-a** | +1441 $/wk, DD -20.7 pts, ww -1083 | n/a | n/a | n/a |
| asia | a | -5048 $/wk, DD -43.5%, ww -24880, stops 7.08(6.24), b5 68%, w2l 1 | n/a | n/a | n/a |
| asia | b | -5761 $/wk, DD -42.5%, ww -24261, stops 6.62(6.24), b5 71%, w2l 1 | n/a | n/a | n/a |
| asia | c | -3573 $/wk, DD -36.0%, ww -20985, stops 6.39(6.24), b5 79%, w2l 1 | n/a | n/a | n/a |
| asia | **b-a** | -713 $/wk, DD +1.0 pts, ww +619 | n/a | n/a | n/a |
| asia | **c-a** | +1475 $/wk, DD +7.5 pts, ww +3896 | n/a | n/a | n/a |
| london | a | -1923 $/wk, DD -17.5%, ww -5575, stops 2.97(2.74), b5 76%, w2l 1 | n/a | n/a | n/a |
| london | b | -564 $/wk, DD +7.3%, ww -1649, stops 3.12(2.74), b5 75%, w2l 1 | n/a | n/a | n/a |
| london | c | -3314 $/wk, DD -19.1%, ww -5097, stops 3.35(2.74), b5 53%, w2l 3 | n/a | n/a | n/a |
| london | **b-a** | +1359 $/wk, DD +24.9 pts, ww +3926 | n/a | n/a | n/a |
| london | **c-a** | -1391 $/wk, DD -1.5 pts, ww +478 | n/a | n/a | n/a |
| nyam | a | -1944 $/wk, DD -36.5%, ww -6003, stops 1.52(1.29), b5 42%, w2l 1 | n/a | n/a | n/a |
| nyam | b | -2076 $/wk, DD -40.0%, ww -6003, stops 1.52(1.29), b5 38%, w2l 2 | n/a | n/a | n/a |
| nyam | c | -736 $/wk, DD +3.4%, ww -6003, stops 1.45(1.29), b5 61%, w2l 0 | n/a | n/a | n/a |
| nyam | **b-a** | -132 $/wk, DD -3.5 pts, ww +0 | n/a | n/a | n/a |
| nyam | **c-a** | +1208 $/wk, DD +40.0 pts, ww +0 | n/a | n/a | n/a |
| nypm | a | -835 $/wk, DD +5.4%, ww -286, stops 0.08(0.08), b5 56%, w2l 4 | n/a | n/a | n/a |
| nypm | b | -270 $/wk, DD +15.3%, ww -1266, stops 0.08(0.08), b5 105%, w2l 2 | n/a | n/a | n/a |
| nypm | c | -686 $/wk, DD +27.7%, ww -286, stops 0.08(0.08), b5 76%, w2l 4 | n/a | n/a | n/a |
| nypm | **b-a** | +565 $/wk, DD +9.9 pts, ww -980 | n/a | n/a | n/a |
| nypm | **c-a** | +149 $/wk, DD +22.3 pts, ww +0 | n/a | n/a | n/a |

**D1C** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -9740 $/wk, DD -31.0%, ww -16151, stops 10.35(10.35), b5 79%, w2l 1 | n/a | n/a | n/a |
| all | b | -3827 $/wk, DD -18.7%, ww -17246, stops 10.58(10.35), b5 93%, w2l 1 | n/a | n/a | n/a |
| all | c | -4893 $/wk, DD -15.0%, ww -8349, stops 10.73(10.35), b5 87%, w2l 1 | n/a | n/a | n/a |
| all | **b-a** | +5913 $/wk, DD +12.3 pts, ww -1095 | n/a | n/a | n/a |
| all | **c-a** | +4847 $/wk, DD +16.0 pts, ww +7802 | n/a | n/a | n/a |
| asia | a | -6849 $/wk, DD -55.2%, ww -26716, stops 6.70(6.24), b5 82%, w2l 0 | n/a | n/a | n/a |
| asia | b | -1404 $/wk, DD -29.7%, ww -24356, stops 6.54(6.24), b5 98%, w2l 1 | n/a | n/a | n/a |
| asia | c | -3777 $/wk, DD -30.9%, ww -23958, stops 6.54(6.24), b5 87%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | +5445 $/wk, DD +25.6 pts, ww +2359 | n/a | n/a | n/a |
| asia | **c-a** | +3071 $/wk, DD +24.3 pts, ww +2758 | n/a | n/a | n/a |
| london | a | -1478 $/wk, DD -9.3%, ww +361, stops 2.51(2.74), b5 65%, w2l 0 | n/a | n/a | n/a |
| london | b | -1435 $/wk, DD +17.7%, ww +1, stops 2.89(2.74), b5 77%, w2l 2 | n/a | n/a | n/a |
| london | c | -786 $/wk, DD -13.6%, ww -7476, stops 2.97(2.74), b5 95%, w2l 1 | n/a | n/a | n/a |
| london | **b-a** | +43 $/wk, DD +27.0 pts, ww -359 | n/a | n/a | n/a |
| london | **c-a** | +692 $/wk, DD -4.4 pts, ww -7837 | n/a | n/a | n/a |
| nyam | a | -561 $/wk, DD +0.1%, ww -4893, stops 1.07(1.29), b5 76%, w2l 1 | n/a | n/a | n/a |
| nyam | b | +641 $/wk, DD +38.8%, ww -1783, stops 1.07(1.29), b5 75%, w2l 1 | n/a | n/a | n/a |
| nyam | c | -142 $/wk, DD +6.2%, ww -3296, stops 1.07(1.29), b5 75%, w2l 1 | n/a | n/a | n/a |
| nyam | **b-a** | +1202 $/wk, DD +38.8 pts, ww +3110 | n/a | n/a | n/a |
| nyam | **c-a** | +419 $/wk, DD +6.2 pts, ww +1597 | n/a | n/a | n/a |
| nypm | a | -853 $/wk, DD -16.7%, ww -286, stops 0.08(0.08), b5 59%, w2l 2 | n/a | n/a | n/a |
| nypm | b | -1629 $/wk, DD -67.0%, ww -286, stops 0.08(0.08), b5 3%, w2l 5 | n/a | n/a | n/a |
| nypm | c | -188 $/wk, DD +57.3%, ww +2276, stops 0.15(0.08), b5 79%, w2l 3 | n/a | n/a | n/a |
| nypm | **b-a** | -776 $/wk, DD -50.4 pts, ww +0 | n/a | n/a | n/a |
| nypm | **c-a** | +665 $/wk, DD +74.0 pts, ww +2562 | n/a | n/a | n/a |

### Dial 2 constant dollar risk (stop scaled, lots inverse; H = half version)

**D2F** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -7217 $/wk, DD -43.9%, ww -20213, stops 11.64(10.35), b5 73%, w2l 1 | -5461 $/wk, DD -43.9%, ww -20213, stops 10.12(10.99), b5 64%, w2l 1 | n/a | n/a |
| all | b | -8028 $/wk, DD -32.6%, ww -15525, stops 17.12(10.35), b5 84%, w2l 2 | -5596 $/wk, DD -32.6%, ww -15525, stops 12.74(10.99), b5 79%, w2l 3 | n/a | n/a |
| all | c | -6967 $/wk, DD -9.6%, ww -3770, stops 13.77(10.35), b5 79%, w2l 3 | -2999 $/wk, DD -9.6%, ww -3770, stops 11.26(10.99), b5 76%, w2l 4 | n/a | n/a |
| all | **b-a** | -811 $/wk, DD +11.3 pts, ww +4688 | -135 $/wk, DD +11.3 pts, ww +4688 | n/a | n/a |
| all | **c-a** | +250 $/wk, DD +34.3 pts, ww +16443 | +2462 $/wk, DD +34.3 pts, ww +16443 | n/a | n/a |
| asia | a | -8158 $/wk, DD -57.6%, ww -29397, stops 6.39(6.24), b5 64%, w2l 0 | -1686 $/wk, DD -57.6%, ww -29397, stops 5.02(6.35), b5 79%, w2l 0 | n/a | n/a |
| asia | b | -3571 $/wk, DD -14.4%, ww -20299, stops 8.52(6.24), b5 74%, w2l 1 | -2696 $/wk, DD -14.4%, ww -20299, stops 6.12(6.35), b5 72%, w2l 2 | n/a | n/a |
| asia | c | -5645 $/wk, DD -25.0%, ww -15742, stops 6.85(6.24), b5 67%, w2l 1 | -2036 $/wk, DD -25.0%, ww -15742, stops 5.33(6.35), b5 75%, w2l 2 | n/a | n/a |
| asia | **b-a** | +4587 $/wk, DD +43.2 pts, ww +9098 | -1009 $/wk, DD +43.2 pts, ww +9098 | n/a | n/a |
| asia | **c-a** | +2513 $/wk, DD +32.6 pts, ww +13655 | -350 $/wk, DD +32.6 pts, ww +13655 | n/a | n/a |
| london | a | +518 $/wk, DD -7.5%, ww +1021, stops 2.74(2.74), b5 96%, w2l 0 | -2832 $/wk, DD -57.7%, ww +1021, stops 2.74(2.89), b5 68%, w2l 4 | n/a | n/a |
| london | b | -2903 $/wk, DD +26.4%, ww +4826, stops 5.40(2.74), b5 66%, w2l 2 | -255 $/wk, DD +26.4%, ww +4826, stops 4.03(2.89), b5 79%, w2l 3 | n/a | n/a |
| london | c | -655 $/wk, DD +9.2%, ww -4653, stops 3.50(2.74), b5 88%, w2l 1 | +756 $/wk, DD +9.2%, ww -4653, stops 3.35(2.89), b5 83%, w2l 2 | n/a | n/a |
| london | **b-a** | -3422 $/wk, DD +33.9 pts, ww +3805 | +2577 $/wk, DD +84.1 pts, ww +3805 | n/a | n/a |
| london | **c-a** | -1173 $/wk, DD +16.7 pts, ww -5674 | +3588 $/wk, DD +66.9 pts, ww -5674 | n/a | n/a |
| nyam | a | +452 $/wk, DD +17.9%, ww -2881, stops 1.98(1.29), b5 92%, w2l 0 | -130 $/wk, DD -27.1%, ww -294, stops 1.98(1.67), b5 108%, w2l 2 | n/a | n/a |
| nyam | b | -389 $/wk, DD -14.2%, ww -2625, stops 2.21(1.29), b5 61%, w2l 1 | -787 $/wk, DD -66.0%, ww -2195, stops 2.05(1.67), b5 81%, w2l 3 | n/a | n/a |
| nyam | c | -856 $/wk, DD -49.7%, ww -3697, stops 2.43(1.29), b5 63%, w2l 3 | -507 $/wk, DD -27.5%, ww -1109, stops 1.94(1.67), b5 90%, w2l 5 | n/a | n/a |
| nyam | **b-a** | -841 $/wk, DD -32.1 pts, ww +256 | -657 $/wk, DD -38.8 pts, ww -1901 | n/a | n/a |
| nyam | **c-a** | -1308 $/wk, DD -67.6 pts, ww -816 | -377 $/wk, DD -0.4 pts, ww -816 | n/a | n/a |
| nypm | a | -30 $/wk, DD +7.3%, ww -286, stops 0.53(0.08), b5 135%, w2l 3 | -812 $/wk, DD +7.3%, ww -286, stops 0.38(0.08), b5 45%, w2l 4 | n/a | n/a |
| nypm | b | -1164 $/wk, DD -29.4%, ww -412, stops 0.99(0.08), b5 36%, w2l 3 | -1858 $/wk, DD -71.1%, ww -2062, stops 0.53(0.08), b5 -1%, w2l 5 | n/a | n/a |
| nypm | c | +189 $/wk, DD +31.4%, ww +1255, stops 0.99(0.08), b5 122%, w2l 3 | -1213 $/wk, DD -51.8%, ww -4789, stops 0.65(0.08), b5 -4%, w2l 6 | n/a | n/a |
| nypm | **b-a** | -1135 $/wk, DD -36.7 pts, ww -125 | -1045 $/wk, DD -78.4 pts, ww -1776 | n/a | n/a |
| nypm | **c-a** | +218 $/wk, DD +24.1 pts, ww +1541 | -400 $/wk, DD -59.1 pts, ww -4503 | n/a | n/a |

**D2H** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -10054 $/wk, DD -49.0%, ww -21594, stops 11.79(10.35), b5 69%, w2l 1 | n/a | n/a | n/a |
| all | b | -9947 $/wk, DD -43.2%, ww -19786, stops 17.50(10.35), b5 79%, w2l 1 | n/a | n/a | n/a |
| all | c | -10106 $/wk, DD -47.9%, ww -22512, stops 14.68(10.35), b5 77%, w2l 3 | n/a | n/a | n/a |
| all | **b-a** | +107 $/wk, DD +5.8 pts, ww +1808 | n/a | n/a | n/a |
| all | **c-a** | -53 $/wk, DD +1.1 pts, ww -918 | n/a | n/a | n/a |
| asia | a | -8176 $/wk, DD -68.8%, ww -33566, stops 6.39(6.24), b5 65%, w2l 0 | n/a | n/a | n/a |
| asia | b | -5288 $/wk, DD -44.0%, ww -21538, stops 8.60(6.24), b5 76%, w2l 1 | n/a | n/a | n/a |
| asia | c | -7761 $/wk, DD -50.5%, ww -24707, stops 6.77(6.24), b5 69%, w2l 1 | n/a | n/a | n/a |
| asia | **b-a** | +2888 $/wk, DD +24.9 pts, ww +12028 | n/a | n/a | n/a |
| asia | **c-a** | +414 $/wk, DD +18.3 pts, ww +8859 | n/a | n/a | n/a |
| london | a | -517 $/wk, DD -6.2%, ww +1811, stops 3.04(2.74), b5 80%, w2l 0 | n/a | n/a | n/a |
| london | b | -2868 $/wk, DD +22.4%, ww +808, stops 5.55(2.74), b5 65%, w2l 2 | n/a | n/a | n/a |
| london | c | -1372 $/wk, DD +2.0%, ww -5821, stops 4.03(2.74), b5 89%, w2l 1 | n/a | n/a | n/a |
| london | **b-a** | -2351 $/wk, DD +28.6 pts, ww -1003 | n/a | n/a | n/a |
| london | **c-a** | -854 $/wk, DD +8.2 pts, ww -7632 | n/a | n/a | n/a |
| nyam | a | -973 $/wk, DD +22.0%, ww -2432, stops 1.75(1.29), b5 50%, w2l 1 | n/a | n/a | n/a |
| nyam | b | -14 $/wk, DD +6.6%, ww -2021, stops 2.05(1.29), b5 58%, w2l 0 | n/a | n/a | n/a |
| nyam | c | -524 $/wk, DD -32.0%, ww -3041, stops 2.43(1.29), b5 65%, w2l 2 | n/a | n/a | n/a |
| nyam | **b-a** | +959 $/wk, DD -15.3 pts, ww +411 | n/a | n/a | n/a |
| nyam | **c-a** | +449 $/wk, DD -54.0 pts, ww -608 | n/a | n/a | n/a |
| nypm | a | -388 $/wk, DD +9.2%, ww -286, stops 0.61(0.08), b5 80%, w2l 2 | n/a | n/a | n/a |
| nypm | b | -1778 $/wk, DD -97.1%, ww -1960, stops 1.29(0.08), b5 8%, w2l 5 | n/a | n/a | n/a |
| nypm | c | -450 $/wk, DD +41.3%, ww +839, stops 1.45(0.08), b5 83%, w2l 2 | n/a | n/a | n/a |
| nypm | **b-a** | -1390 $/wk, DD -106.3 pts, ww -1673 | n/a | n/a | n/a |
| nypm | **c-a** | -62 $/wk, DD +32.1 pts, ww +1125 | n/a | n/a | n/a |

### Dial 3 cut levels in forecast-range units (state-cut arm + K7 flat cut)

**D3C** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -7420 $/wk, DD -10.2%, ww -2364, stops 12.40(10.35), b5 73%, w2l 1 | -6054 $/wk, DD -10.2%, ww -15359, stops 17.39(10.99), b5 81%, w2l 1 | -1402 $/wk, DD -32.4%, ww -21950, stops 16.84(10.66), b5 88%, w2l 3 | -544 $/wk, DD +0.0%, ww +0, stops 9.03(9.31), b5 99%, w2l 0 |
| all | b | -6971 $/wk, DD -25.9%, ww -14627, stops 11.95(10.35), b5 89%, w2l 1 | -5427 $/wk, DD -25.9%, ww -14627, stops 16.55(10.99), b5 89%, w2l 2 | -1341 $/wk, DD -17.0%, ww -19204, stops 17.16(10.66), b5 91%, w2l 4 | -689 $/wk, DD +0.0%, ww +0, stops 9.15(9.31), b5 86%, w2l 0 |
| all | c | -5225 $/wk, DD -5.9%, ww -1261, stops 12.71(10.35), b5 90%, w2l 1 | -6151 $/wk, DD -5.9%, ww -10598, stops 17.50(10.99), b5 87%, w2l 1 | -1417 $/wk, DD -18.0%, ww -19763, stops 17.28(10.66), b5 88%, w2l 4 | -746 $/wk, DD +0.0%, ww +0, stops 9.38(9.31), b5 84%, w2l 1 |
| all | **b-a** | +448 $/wk, DD -15.7 pts, ww -12263 | +628 $/wk, DD -15.7 pts, ww +732 | +60 $/wk, DD +15.4 pts, ww +2746 | -145 $/wk, DD +0.0 pts, ww +0 |
| all | **c-a** | +2195 $/wk, DD +4.3 pts, ww +1103 | -97 $/wk, DD +4.3 pts, ww +4761 | -16 $/wk, DD +14.5 pts, ww +2187 | -201 $/wk, DD +0.0 pts, ww +0 |
| asia | a | -5194 $/wk, DD -18.4%, ww -18623, stops 7.76(6.24), b5 84%, w2l 1 | -4668 $/wk, DD -18.4%, ww -22431, stops 10.23(6.35), b5 90%, w2l 2 | -2950 $/wk, DD -5.8%, ww -2387, stops 9.15(5.87), b5 86%, w2l 2 | -47 $/wk, DD +0.0%, ww +0, stops 4.05(4.18), b5 104%, w2l 1 |
| asia | b | -4116 $/wk, DD -5.3%, ww -18193, stops 7.99(6.24), b5 91%, w2l 1 | -4166 $/wk, DD -5.6%, ww -18193, stops 9.78(6.35), b5 89%, w2l 3 | -2670 $/wk, DD -5.2%, ww -7157, stops 9.24(5.87), b5 87%, w2l 3 | -1132 $/wk, DD +0.0%, ww +0, stops 4.15(4.18), b5 77%, w2l 1 |
| asia | c | -4006 $/wk, DD -8.3%, ww -16882, stops 8.29(6.24), b5 89%, w2l 1 | -5429 $/wk, DD -8.3%, ww -18591, stops 10.23(6.35), b5 89%, w2l 3 | -3237 $/wk, DD -5.0%, ww -7715, stops 9.36(5.87), b5 88%, w2l 4 | -1539 $/wk, DD +0.0%, ww +0, stops 4.21(4.18), b5 76%, w2l 1 |
| asia | **b-a** | +1079 $/wk, DD +13.1 pts, ww +430 | +502 $/wk, DD +12.8 pts, ww +4238 | +280 $/wk, DD +0.5 pts, ww -4769 | -1085 $/wk, DD +0.0 pts, ww +0 |
| asia | **c-a** | +1189 $/wk, DD +10.1 pts, ww +1742 | -761 $/wk, DD +10.1 pts, ww +3841 | -287 $/wk, DD +0.7 pts, ww -5328 | -1492 $/wk, DD +0.0 pts, ww +0 |
| london | a | -326 $/wk, DD -3.0%, ww +2741, stops 3.42(2.74), b5 89%, w2l 0 | -339 $/wk, DD -3.0%, ww +2741, stops 4.64(2.89), b5 82%, w2l 0 | +774 $/wk, DD -3.0%, ww +2741, stops 4.43(2.61), b5 87%, w2l 2 | -8 $/wk, DD +0.0%, ww +0, stops 3.03(3.08), b5 89%, w2l 1 |
| london | b | -1751 $/wk, DD -14.5%, ww -366, stops 3.04(2.74), b5 84%, w2l 0 | -145 $/wk, DD -14.5%, ww -366, stops 4.53(2.89), b5 89%, w2l 0 | +521 $/wk, DD -14.5%, ww -366, stops 4.70(2.61), b5 89%, w2l 2 | +757 $/wk, DD +0.0%, ww +0, stops 2.92(3.08), b5 103%, w2l 1 |
| london | c | +504 $/wk, DD +4.0%, ww +2112, stops 3.20(2.74), b5 89%, w2l 0 | +904 $/wk, DD +4.0%, ww +2112, stops 4.79(2.89), b5 93%, w2l 0 | +1140 $/wk, DD +4.0%, ww +2112, stops 4.66(2.61), b5 90%, w2l 3 | +840 $/wk, DD +0.0%, ww +0, stops 3.05(3.08), b5 103%, w2l 0 |
| london | **b-a** | -1424 $/wk, DD -11.4 pts, ww -3107 | +194 $/wk, DD -11.4 pts, ww -3107 | -253 $/wk, DD -11.4 pts, ww -3107 | +765 $/wk, DD +0.0 pts, ww +0 |
| london | **c-a** | +830 $/wk, DD +7.0 pts, ww -629 | +1243 $/wk, DD +7.0 pts, ww -629 | +366 $/wk, DD +7.0 pts, ww -629 | +848 $/wk, DD +0.0 pts, ww +0 |
| nyam | a | -822 $/wk, DD +16.2%, ww +514, stops 1.14(1.29), b5 49%, w2l 2 | -432 $/wk, DD -33.3%, ww -2933, stops 2.13(1.67), b5 92%, w2l 4 | +753 $/wk, DD +28.6%, ww -265, stops 2.84(2.15), b5 111%, w2l 6 | -358 $/wk, DD -0.6%, ww +0, stops 1.90(2.00), b5 88%, w2l 1 |
| nyam | b | -323 $/wk, DD +17.6%, ww -54, stops 0.84(1.29), b5 66%, w2l 2 | -757 $/wk, DD -70.2%, ww -2800, stops 1.94(1.67), b5 82%, w2l 4 | +603 $/wk, DD +34.7%, ww +620, stops 2.80(2.15), b5 110%, w2l 5 | -247 $/wk, DD +11.5%, ww +0, stops 1.97(2.00), b5 100%, w2l 1 |
| nyam | c | -608 $/wk, DD -0.1%, ww -4307, stops 0.99(1.29), b5 78%, w2l 1 | -903 $/wk, DD -84.8%, ww -3985, stops 2.13(1.67), b5 81%, w2l 4 | +653 $/wk, DD +38.6%, ww -2351, stops 2.95(2.15), b5 112%, w2l 4 | +158 $/wk, DD +23.3%, ww +0, stops 1.92(2.00), b5 97%, w2l 0 |
| nyam | **b-a** | +499 $/wk, DD +1.4 pts, ww -568 | -325 $/wk, DD -36.9 pts, ww +133 | -150 $/wk, DD +6.2 pts, ww +885 | +110 $/wk, DD +12.1 pts, ww +0 |
| nyam | **c-a** | +215 $/wk, DD -16.3 pts, ww -4821 | -471 $/wk, DD -51.5 pts, ww -1052 | -99 $/wk, DD +10.0 pts, ww -2086 | +516 $/wk, DD +23.9 pts, ww +0 |
| nypm | a | -1077 $/wk, DD -16.0%, ww -145, stops 0.08(0.08), b5 23%, w2l 3 | -615 $/wk, DD -16.0%, ww -145, stops 0.38(0.08), b5 88%, w2l 5 | +22 $/wk, DD +15.4%, ww +3015, stops 0.42(0.04), b5 88%, w2l 8 | -131 $/wk, DD -13.6%, ww +0, stops 0.05(0.05), b5 93%, w2l 0 |
| nypm | b | -781 $/wk, DD +5.4%, ww +1073, stops 0.08(0.08), b5 16%, w2l 4 | -358 $/wk, DD +5.4%, ww +1073, stops 0.30(0.08), b5 79%, w2l 4 | +205 $/wk, DD +26.3%, ww +3190, stops 0.42(0.04), b5 79%, w2l 8 | -67 $/wk, DD +4.7%, ww -63, stops 0.10(0.05), b5 93%, w2l 1 |
| nypm | c | -1116 $/wk, DD -47.0%, ww +757, stops 0.23(0.08), b5 10%, w2l 4 | -723 $/wk, DD -47.0%, ww +757, stops 0.34(0.08), b5 72%, w2l 4 | +26 $/wk, DD +19.1%, ww +3190, stops 0.31(0.04), b5 72%, w2l 7 | -204 $/wk, DD -1.1%, ww +0, stops 0.21(0.05), b5 75%, w2l 0 |
| nypm | **b-a** | +295 $/wk, DD +21.4 pts, ww +1218 | +256 $/wk, DD +21.4 pts, ww +1218 | +183 $/wk, DD +10.9 pts, ww +175 | +65 $/wk, DD +18.3 pts, ww -63 |
| nypm | **c-a** | -39 $/wk, DD -31.0 pts, ww +902 | -108 $/wk, DD -31.0 pts, ww +902 | +4 $/wk, DD +3.7 pts, ww +175 | -73 $/wk, DD +12.5 pts, ww +0 |

**D3T** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -4471 $/wk, DD -2.1%, ww -722, stops 11.57(10.35), b5 90%, w2l 1 | -3713 $/wk, DD -2.1%, ww -11797, stops 14.38(10.99), b5 99%, w2l 1 | +356 $/wk, DD -21.3%, ww -18342, stops 13.94(10.66), b5 101%, w2l 2 | -1356 $/wk, DD +0.0%, ww +0, stops 9.05(9.31), b5 95%, w2l 0 |
| all | b | -5003 $/wk, DD +6.5%, ww -32, stops 11.03(10.35), b5 88%, w2l 2 | -2173 $/wk, DD +6.5%, ww -32, stops 13.54(10.99), b5 101%, w2l 2 | -201 $/wk, DD -28.8%, ww -20833, stops 13.31(10.66), b5 98%, w2l 4 | -1876 $/wk, DD +0.0%, ww +0, stops 9.13(9.31), b5 78%, w2l 0 |
| all | c | -3585 $/wk, DD -17.3%, ww -11955, stops 11.72(10.35), b5 91%, w2l 0 | -2699 $/wk, DD -17.3%, ww -11955, stops 13.77(10.99), b5 100%, w2l 0 | -419 $/wk, DD -41.8%, ww -20833, stops 13.35(10.66), b5 98%, w2l 2 | -1513 $/wk, DD +0.0%, ww +0, stops 9.13(9.31), b5 81%, w2l 0 |
| all | **b-a** | -532 $/wk, DD +8.5 pts, ww +690 | +1540 $/wk, DD +8.5 pts, ww +11764 | -557 $/wk, DD -7.5 pts, ww -2491 | -520 $/wk, DD +0.0 pts, ww +0 |
| all | **c-a** | +885 $/wk, DD -15.2 pts, ww -11233 | +1014 $/wk, DD -15.2 pts, ww -159 | -775 $/wk, DD -20.6 pts, ww -2491 | -158 $/wk, DD +0.0 pts, ww +0 |
| asia | a | -2429 $/wk, DD -8.9%, ww -14670, stops 7.08(6.24), b5 99%, w2l 1 | -3111 $/wk, DD -22.6%, ww -16077, stops 8.26(6.35), b5 104%, w2l 4 | -1472 $/wk, DD -2.6%, ww +44, stops 7.56(5.87), b5 101%, w2l 4 | -926 $/wk, DD +0.0%, ww +0, stops 4.10(4.18), b5 99%, w2l 1 |
| asia | b | -3340 $/wk, DD +6.7%, ww -13308, stops 7.15(6.24), b5 89%, w2l 0 | -1843 $/wk, DD +6.7%, ww -13308, stops 7.76(6.35), b5 92%, w2l 1 | -1932 $/wk, DD -4.9%, ww -2428, stops 7.23(5.87), b5 88%, w2l 2 | -2041 $/wk, DD +0.0%, ww +0, stops 4.10(4.18), b5 72%, w2l 1 |
| asia | c | -3140 $/wk, DD +0.9%, ww -8722, stops 7.15(6.24), b5 96%, w2l 0 | -3525 $/wk, DD -4.8%, ww -16077, stops 7.80(6.35), b5 97%, w2l 3 | -2670 $/wk, DD -5.5%, ww -2428, stops 7.27(5.87), b5 93%, w2l 3 | -1881 $/wk, DD +0.0%, ww +0, stops 4.13(4.18), b5 72%, w2l 1 |
| asia | **b-a** | -911 $/wk, DD +15.6 pts, ww +1363 | +1268 $/wk, DD +29.4 pts, ww +2770 | -459 $/wk, DD -2.3 pts, ww -2472 | -1115 $/wk, DD +0.0 pts, ww +0 |
| asia | **c-a** | -711 $/wk, DD +9.8 pts, ww +5948 | -414 $/wk, DD +17.8 pts, ww +0 | -1197 $/wk, DD -3.0 pts, ww -2472 | -955 $/wk, DD +0.0 pts, ww +0 |
| london | a | -690 $/wk, DD -15.8%, ww +1175, stops 3.20(2.74), b5 99%, w2l 0 | +508 $/wk, DD -15.8%, ww +1175, stops 3.77(2.89), b5 92%, w2l 0 | +1060 $/wk, DD -15.8%, ww +1175, stops 3.62(2.61), b5 98%, w2l 2 | -11 $/wk, DD +0.0%, ww +0, stops 2.97(3.08), b5 86%, w2l 1 |
| london | b | -582 $/wk, DD +5.3%, ww +943, stops 2.66(2.74), b5 87%, w2l 0 | +462 $/wk, DD +5.3%, ww +943, stops 3.54(2.89), b5 92%, w2l 0 | +1033 $/wk, DD +5.3%, ww +943, stops 3.45(2.61), b5 96%, w2l 1 | +639 $/wk, DD +0.0%, ww +0, stops 2.97(3.08), b5 100%, w2l 0 |
| london | c | -251 $/wk, DD -23.1%, ww +0, stops 3.20(2.74), b5 105%, w2l 0 | +1232 $/wk, DD -23.1%, ww +0, stops 3.73(2.89), b5 108%, w2l 0 | +1505 $/wk, DD -23.1%, ww +0, stops 3.45(2.61), b5 108%, w2l 1 | +637 $/wk, DD +0.0%, ww +0, stops 3.00(3.08), b5 101%, w2l 0 |
| london | **b-a** | +108 $/wk, DD +21.1 pts, ww -231 | -46 $/wk, DD +21.1 pts, ww -231 | -28 $/wk, DD +21.1 pts, ww -231 | +650 $/wk, DD +0.0 pts, ww +0 |
| london | **c-a** | +439 $/wk, DD -7.3 pts, ww -1175 | +724 $/wk, DD -7.3 pts, ww -1175 | +445 $/wk, DD -7.3 pts, ww -1175 | +647 $/wk, DD +0.0 pts, ww +0 |
| nyam | a | -249 $/wk, DD +22.4%, ww +817, stops 1.22(1.29), b5 71%, w2l 1 | -517 $/wk, DD -49.4%, ww -2170, stops 2.13(1.67), b5 93%, w2l 4 | +709 $/wk, DD +22.4%, ww -611, stops 2.57(2.15), b5 106%, w2l 4 | -323 $/wk, DD +6.2%, ww +0, stops 1.92(2.00), b5 93%, w2l 1 |
| nyam | b | -131 $/wk, DD +12.8%, ww +592, stops 1.14(1.29), b5 82%, w2l 1 | -194 $/wk, DD -13.7%, ww -2170, stops 2.02(1.67), b5 87%, w2l 2 | +793 $/wk, DD +30.2%, ww +1768, stops 2.44(2.15), b5 99%, w2l 4 | -361 $/wk, DD -2.1%, ww +0, stops 2.00(2.00), b5 95%, w2l 1 |
| nyam | c | +489 $/wk, DD +0.3%, ww +592, stops 1.22(1.29), b5 106%, w2l 1 | +17 $/wk, DD -36.8%, ww -2770, stops 2.05(1.67), b5 106%, w2l 2 | +755 $/wk, DD +16.5%, ww +1278, stops 2.47(2.15), b5 104%, w2l 3 | -230 $/wk, DD +6.3%, ww +0, stops 1.95(2.00), b5 98%, w2l 1 |
| nyam | **b-a** | +118 $/wk, DD -9.6 pts, ww -225 | +323 $/wk, DD +35.8 pts, ww +0 | +84 $/wk, DD +7.8 pts, ww +2378 | -38 $/wk, DD -8.2 pts, ww +0 |
| nyam | **c-a** | +739 $/wk, DD -22.0 pts, ww -225 | +534 $/wk, DD +12.7 pts, ww -600 | +46 $/wk, DD -5.9 pts, ww +1888 | +93 $/wk, DD +0.1 pts, ww +0 |
| nypm | a | -1102 $/wk, DD -26.6%, ww -373, stops 0.08(0.08), b5 35%, w2l 3 | -594 $/wk, DD -26.6%, ww -373, stops 0.23(0.08), b5 94%, w2l 3 | +59 $/wk, DD +21.9%, ww +1688, stops 0.19(0.04), b5 94%, w2l 5 | -96 $/wk, DD -11.1%, ww +0, stops 0.05(0.05), b5 97%, w2l 1 |
| nypm | b | -950 $/wk, DD -18.2%, ww +168, stops 0.08(0.08), b5 32%, w2l 4 | -598 $/wk, DD -18.2%, ww +168, stops 0.23(0.08), b5 89%, w2l 6 | -95 $/wk, DD +11.8%, ww +1688, stops 0.19(0.04), b5 89%, w2l 9 | -113 $/wk, DD -4.3%, ww +0, stops 0.05(0.05), b5 97%, w2l 1 |
| nypm | c | -684 $/wk, DD -22.2%, ww +308, stops 0.15(0.08), b5 63%, w2l 3 | -424 $/wk, DD -22.2%, ww +308, stops 0.19(0.08), b5 101%, w2l 3 | -9 $/wk, DD +10.5%, ww +1688, stops 0.15(0.04), b5 101%, w2l 5 | -39 $/wk, DD +1.7%, ww +0, stops 0.05(0.05), b5 97%, w2l 1 |
| nypm | **b-a** | +153 $/wk, DD +8.4 pts, ww +540 | -4 $/wk, DD +8.4 pts, ww +540 | -154 $/wk, DD -10.1 pts, ww +0 | -16 $/wk, DD +6.8 pts, ww +0 |
| nypm | **c-a** | +419 $/wk, DD +4.5 pts, ww +680 | +170 $/wk, DD +4.5 pts, ww +680 | -68 $/wk, DD -11.4 pts, ww +0 | +58 $/wk, DD +12.8 pts, ww +0 |

**D3M** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -7996 $/wk, DD -20.7%, ww -4703, stops 14.08(10.35), b5 73%, w2l 1 | -6914 $/wk, DD -24.6%, ww -24396, stops 22.79(10.99), b5 81%, w2l 2 | n/a | n/a |
| all | b | -9138 $/wk, DD -34.0%, ww -17212, stops 12.55(10.35), b5 88%, w2l 1 | -6682 $/wk, DD -34.0%, ww -17212, stops 22.14(10.99), b5 87%, w2l 1 | n/a | n/a |
| all | c | -8118 $/wk, DD -44.9%, ww -22415, stops 14.99(10.35), b5 87%, w2l 2 | -7170 $/wk, DD -44.9%, ww -22415, stops 23.89(10.99), b5 80%, w2l 3 | n/a | n/a |
| all | **b-a** | -1142 $/wk, DD -13.3 pts, ww -12509 | +232 $/wk, DD -9.4 pts, ww +7184 | n/a | n/a |
| all | **c-a** | -122 $/wk, DD -24.2 pts, ww -17712 | -256 $/wk, DD -20.3 pts, ww +1981 | n/a | n/a |
| asia | a | -5714 $/wk, DD -32.6%, ww -20911, stops 8.67(6.24), b5 83%, w2l 1 | -4462 $/wk, DD -32.6%, ww -25776, stops 12.97(6.35), b5 93%, w2l 3 | n/a | n/a |
| asia | b | -6686 $/wk, DD -29.0%, ww -24077, stops 8.52(6.24), b5 85%, w2l 1 | -5646 $/wk, DD -29.0%, ww -24077, stops 12.14(6.35), b5 89%, w2l 3 | n/a | n/a |
| asia | c | -6628 $/wk, DD -39.4%, ww -23527, stops 8.90(6.24), b5 72%, w2l 1 | -6229 $/wk, DD -39.4%, ww -27153, stops 12.71(6.35), b5 88%, w2l 3 | n/a | n/a |
| asia | **b-a** | -973 $/wk, DD +3.5 pts, ww -3166 | -1184 $/wk, DD +3.5 pts, ww +1699 | n/a | n/a |
| asia | **c-a** | -914 $/wk, DD -6.9 pts, ww -2616 | -1767 $/wk, DD -6.9 pts, ww -1377 | n/a | n/a |
| london | a | +35 $/wk, DD +1.1%, ww +5824, stops 4.11(2.74), b5 89%, w2l 0 | -316 $/wk, DD +1.1%, ww +5824, stops 6.39(2.89), b5 72%, w2l 0 | n/a | n/a |
| london | b | -1763 $/wk, DD -17.4%, ww +3187, stops 2.89(2.74), b5 84%, w2l 0 | +369 $/wk, DD -17.4%, ww +3187, stops 6.16(2.89), b5 83%, w2l 0 | n/a | n/a |
| london | c | +658 $/wk, DD -10.7%, ww +3546, stops 4.72(2.74), b5 96%, w2l 0 | +787 $/wk, DD -10.7%, ww +3546, stops 7.23(2.89), b5 83%, w2l 0 | n/a | n/a |
| london | **b-a** | -1798 $/wk, DD -18.5 pts, ww -2637 | +685 $/wk, DD -18.5 pts, ww -2637 | n/a | n/a |
| london | **c-a** | +622 $/wk, DD -11.8 pts, ww -2279 | +1103 $/wk, DD -11.8 pts, ww -2279 | n/a | n/a |
| nyam | a | -1363 $/wk, DD +20.9%, ww +870, stops 1.22(1.29), b5 27%, w2l 2 | -987 $/wk, DD -71.7%, ww -8622, stops 2.89(1.67), b5 83%, w2l 4 | n/a | n/a |
| nyam | b | -13 $/wk, DD +26.0%, ww -833, stops 0.99(1.29), b5 71%, w2l 1 | -830 $/wk, DD -115.8%, ww -10635, stops 3.23(1.67), b5 85%, w2l 3 | n/a | n/a |
| nyam | c | -1191 $/wk, DD -29.4%, ww -4922, stops 1.14(1.29), b5 49%, w2l 2 | -820 $/wk, DD -128.0%, ww -9031, stops 3.42(1.67), b5 86%, w2l 4 | n/a | n/a |
| nyam | **b-a** | +1350 $/wk, DD +5.0 pts, ww -1703 | +158 $/wk, DD -44.1 pts, ww -2013 | n/a | n/a |
| nyam | **c-a** | +173 $/wk, DD -50.3 pts, ww -5792 | +167 $/wk, DD -56.3 pts, ww -409 | n/a | n/a |
| nypm | a | -954 $/wk, DD +6.1%, ww +1628, stops 0.08(0.08), b5 11%, w2l 3 | -1149 $/wk, DD +6.1%, ww +171, stops 0.53(0.08), b5 59%, w2l 5 | n/a | n/a |
| nypm | b | -675 $/wk, DD +6.8%, ww +1366, stops 0.15(0.08), b5 19%, w2l 4 | -575 $/wk, DD +4.8%, ww +1366, stops 0.61(0.08), b5 71%, w2l 6 | n/a | n/a |
| nypm | c | -957 $/wk, DD -10.6%, ww +1428, stops 0.23(0.08), b5 17%, w2l 3 | -908 $/wk, DD -18.6%, ww +898, stops 0.53(0.08), b5 59%, w2l 4 | n/a | n/a |
| nypm | **b-a** | +279 $/wk, DD +0.8 pts, ww -262 | +574 $/wk, DD -1.2 pts, ww +1195 | n/a | n/a |
| nypm | **c-a** | -3 $/wk, DD -16.6 pts, ww -201 | +240 $/wk, DD -24.7 pts, ww +727 | n/a | n/a |

### Dial 4 range used up (I skip / II take profit early / III shrink target; k in name 05=0.5 075 1 125)

**D4I05** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -17155 $/wk, DD -37.7%, ww +6545, stops 4.49(10.35), b5 33%, w2l 5 | -18443 $/wk, DD -37.7%, ww +6545, stops 5.25(10.99), b5 29%, w2l 7 | n/a | n/a |
| all | b | -18999 $/wk, DD +23.0%, ww +15161, stops 3.80(10.35), b5 5%, w2l 3 | -16921 $/wk, DD -0.9%, ww +15161, stops 4.76(10.99), b5 24%, w2l 4 | n/a | n/a |
| all | c | -16297 $/wk, DD +17.1%, ww +19115, stops 4.34(10.35), b5 34%, w2l 5 | -16175 $/wk, DD +10.3%, ww +6955, stops 5.06(10.99), b5 24%, w2l 7 | n/a | n/a |
| all | **b-a** | -1844 $/wk, DD +60.7 pts, ww +8616 | +1521 $/wk, DD +36.8 pts, ww +8616 | n/a | n/a |
| all | **c-a** | +858 $/wk, DD +54.8 pts, ww +12570 | +2268 $/wk, DD +48.1 pts, ww +411 | n/a | n/a |
| asia | a | -10750 $/wk, DD +8.8%, ww +4518, stops 2.28(6.24), b5 44%, w2l 3 | -14519 $/wk, DD +8.8%, ww +4518, stops 2.17(6.35), b5 34%, w2l 5 | n/a | n/a |
| asia | b | -13211 $/wk, DD +59.2%, ww +11105, stops 1.90(6.24), b5 15%, w2l 3 | -13450 $/wk, DD +31.0%, ww +11105, stops 1.79(6.35), b5 24%, w2l 6 | n/a | n/a |
| asia | c | -13431 $/wk, DD +12.5%, ww +10439, stops 2.74(6.24), b5 29%, w2l 2 | -13009 $/wk, DD +12.5%, ww +10439, stops 2.36(6.35), b5 31%, w2l 5 | n/a | n/a |
| asia | **b-a** | -2461 $/wk, DD +50.4 pts, ww +6587 | +1069 $/wk, DD +22.2 pts, ww +6587 | n/a | n/a |
| asia | **c-a** | -2681 $/wk, DD +3.6 pts, ww +5922 | +1510 $/wk, DD +3.6 pts, ww +5922 | n/a | n/a |
| london | a | -4272 $/wk, DD +17.8%, ww -1546, stops 0.99(2.74), b5 42%, w2l 2 | -543 $/wk, DD +9.2%, ww -1546, stops 1.18(2.89), b5 61%, w2l 3 | n/a | n/a |
| london | b | -3118 $/wk, DD +36.7%, ww +11561, stops 0.61(2.74), b5 25%, w2l 1 | -642 $/wk, DD +36.7%, ww +11561, stops 1.03(2.89), b5 33%, w2l 2 | n/a | n/a |
| london | c | -2111 $/wk, DD +57.9%, ww +15873, stops 0.46(2.74), b5 33%, w2l 3 | -966 $/wk, DD +53.3%, ww +15873, stops 1.03(2.89), b5 36%, w2l 4 | n/a | n/a |
| london | **b-a** | +1154 $/wk, DD +18.9 pts, ww +13107 | -99 $/wk, DD +27.5 pts, ww +13107 | n/a | n/a |
| london | **c-a** | +2162 $/wk, DD +40.1 pts, ww +17419 | -422 $/wk, DD +44.1 pts, ww +17419 | n/a | n/a |
| nyam | a | -482 $/wk, DD -10.2%, ww -1334, stops 1.07(1.29), b5 43%, w2l 4 | -1529 $/wk, DD -68.2%, ww -4710, stops 1.75(1.67), b5 46%, w2l 7 | n/a | n/a |
| nyam | b | -682 $/wk, DD +17.7%, ww -608, stops 1.07(1.29), b5 47%, w2l 5 | -1306 $/wk, DD -16.6%, ww +1979, stops 1.75(1.67), b5 59%, w2l 9 | n/a | n/a |
| nyam | c | +29 $/wk, DD +21.9%, ww +4131, stops 1.07(1.29), b5 32%, w2l 5 | -1462 $/wk, DD -30.6%, ww +3050, stops 1.56(1.67), b5 31%, w2l 9 | n/a | n/a |
| nyam | **b-a** | -200 $/wk, DD +27.9 pts, ww +726 | +223 $/wk, DD +51.6 pts, ww +6689 | n/a | n/a |
| nyam | **c-a** | +510 $/wk, DD +32.1 pts, ww +5465 | +67 $/wk, DD +37.6 pts, ww +7761 | n/a | n/a |
| nypm | a | -1651 $/wk, DD -236.7%, ww -3463, stops 0.15(0.08), b5 -10%, w2l 3 | -1851 $/wk, DD -236.7%, ww -3463, stops 0.15(0.08), b5 36%, w2l 8 | n/a | n/a |
| nypm | b | -1989 $/wk, DD -268.8%, ww -4062, stops 0.23(0.08), b5 -52%, w2l 5 | -1523 $/wk, DD -268.8%, ww -4062, stops 0.19(0.08), b5 50%, w2l 8 | n/a | n/a |
| nypm | c | -784 $/wk, DD -57.6%, ww +215, stops 0.08(0.08), b5 25%, w2l 4 | -738 $/wk, DD -57.6%, ww +215, stops 0.11(0.08), b5 77%, w2l 6 | n/a | n/a |
| nypm | **b-a** | -338 $/wk, DD -32.0 pts, ww -599 | +328 $/wk, DD -32.0 pts, ww -599 | n/a | n/a |
| nypm | **c-a** | +867 $/wk, DD +179.1 pts, ww +3678 | +1113 $/wk, DD +179.1 pts, ww +3678 | n/a | n/a |

**D4II05** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -7856 $/wk, DD -8.6%, ww -1378, stops 9.13(10.35), b5 57%, w2l 1 | -12801 $/wk, DD -8.6%, ww -1378, stops 9.70(10.99), b5 73%, w2l 4 | -10058 $/wk, DD +8.4%, ww +17397, stops 9.05(10.66), b5 62%, w2l 8 | -701 $/wk, DD +0.0%, ww +0, stops 8.87(9.31), b5 87%, w2l 1 |
| all | b | -10753 $/wk, DD -4.3%, ww -107, stops 8.83(10.35), b5 42%, w2l 2 | -9439 $/wk, DD -4.3%, ww -107, stops 9.70(10.99), b5 71%, w2l 3 | -7545 $/wk, DD -0.6%, ww -1086, stops 9.19(10.66), b5 63%, w2l 6 | +491 $/wk, DD +0.0%, ww +0, stops 8.72(9.31), b5 83%, w2l 0 |
| all | c | -103 $/wk, DD +33.6%, ww +17543, stops 8.83(10.35), b5 78%, w2l 1 | -1200 $/wk, DD +33.6%, ww +17543, stops 9.43(10.99), b5 94%, w2l 1 | -5923 $/wk, DD -50.3%, ww +2768, stops 8.92(10.66), b5 77%, w2l 6 | +1219 $/wk, DD +0.0%, ww +0, stops 8.69(9.31), b5 88%, w2l 0 |
| all | **b-a** | -2898 $/wk, DD +4.3 pts, ww +1271 | +3363 $/wk, DD +4.3 pts, ww +1271 | +2513 $/wk, DD -9.0 pts, ww -18483 | +1193 $/wk, DD +0.0 pts, ww +0 |
| all | **c-a** | +7753 $/wk, DD +42.2 pts, ww +18921 | +11602 $/wk, DD +42.2 pts, ww +18921 | +4135 $/wk, DD -58.7 pts, ww -14629 | +1921 $/wk, DD +0.0 pts, ww +0 |
| asia | a | -5301 $/wk, DD -11.3%, ww -5486, stops 5.93(6.24), b5 103%, w2l 1 | -7981 $/wk, DD -11.3%, ww -5486, stops 5.90(6.35), b5 102%, w2l 3 | -6910 $/wk, DD +14.5%, ww +23111, stops 5.31(5.87), b5 82%, w2l 7 | -835 $/wk, DD +0.0%, ww +0, stops 4.03(4.18), b5 81%, w2l 1 |
| asia | b | -5747 $/wk, DD -8.6%, ww -4149, stops 6.01(6.24), b5 81%, w2l 2 | -5949 $/wk, DD -8.6%, ww -4149, stops 6.24(6.35), b5 85%, w2l 4 | -5498 $/wk, DD -7.2%, ww -3965, stops 5.50(5.87), b5 76%, w2l 7 | -94 $/wk, DD +0.0%, ww +0, stops 3.90(4.18), b5 76%, w2l 0 |
| asia | c | +2444 $/wk, DD +26.5%, ww +8989, stops 5.55(6.24), b5 109%, w2l 1 | -1038 $/wk, DD +26.5%, ww +8989, stops 5.63(6.35), b5 97%, w2l 4 | -4437 $/wk, DD -20.4%, ww -2437, stops 5.29(5.87), b5 83%, w2l 8 | +612 $/wk, DD +0.0%, ww +0, stops 3.95(4.18), b5 81%, w2l 0 |
| asia | **b-a** | -447 $/wk, DD +2.8 pts, ww +1337 | +2032 $/wk, DD +2.8 pts, ww +1337 | +1411 $/wk, DD -21.6 pts, ww -27076 | +741 $/wk, DD +0.0 pts, ww +0 |
| asia | **c-a** | +7745 $/wk, DD +37.8 pts, ww +14475 | +6942 $/wk, DD +37.8 pts, ww +14475 | +2473 $/wk, DD -34.9 pts, ww -25548 | +1448 $/wk, DD +0.0 pts, ww +0 |
| london | a | -926 $/wk, DD +5.8%, ww -8782, stops 1.98(2.74), b5 73%, w2l 0 | -2210 $/wk, DD -17.2%, ww -8782, stops 2.28(2.89), b5 76%, w2l 1 | -1402 $/wk, DD -53.2%, ww -8782, stops 2.05(2.61), b5 62%, w2l 4 | -18 $/wk, DD +0.0%, ww +0, stops 2.92(3.08), b5 87%, w2l 2 |
| london | b | -3018 $/wk, DD +31.9%, ww -2814, stops 1.75(2.74), b5 45%, w2l 0 | -988 $/wk, DD +31.9%, ww -2814, stops 1.94(2.89), b5 60%, w2l 0 | -1051 $/wk, DD +11.4%, ww -2814, stops 2.03(2.61), b5 63%, w2l 0 | +826 $/wk, DD +0.0%, ww +0, stops 2.87(3.08), b5 89%, w2l 1 |
| london | c | -3139 $/wk, DD +25.3%, ww -400, stops 1.90(2.74), b5 62%, w2l 2 | -352 $/wk, DD +25.3%, ww -400, stops 2.24(2.89), b5 74%, w2l 2 | -1549 $/wk, DD -45.7%, ww -400, stops 2.17(2.61), b5 67%, w2l 5 | +947 $/wk, DD +0.0%, ww +0, stops 2.90(3.08), b5 96%, w2l 1 |
| london | **b-a** | -2092 $/wk, DD +26.1 pts, ww +5968 | +1222 $/wk, DD +49.1 pts, ww +5968 | +352 $/wk, DD +64.6 pts, ww +5968 | +844 $/wk, DD +0.0 pts, ww +0 |
| london | **c-a** | -2213 $/wk, DD +19.5 pts, ww +8382 | +1858 $/wk, DD +42.5 pts, ww +8382 | -146 $/wk, DD +7.5 pts, ww +8382 | +965 $/wk, DD +0.0 pts, ww +0 |
| nyam | a | -627 $/wk, DD -2.6%, ww -2863, stops 1.14(1.29), b5 85%, w2l 3 | -1360 $/wk, DD -75.1%, ww -1497, stops 1.45(1.67), b5 64%, w2l 5 | -893 $/wk, DD +32.5%, ww +7144, stops 1.63(2.15), b5 63%, w2l 9 | +254 $/wk, DD +31.9%, ww +0, stops 1.85(2.00), b5 90%, w2l 1 |
| nyam | b | -1465 $/wk, DD -28.2%, ww +2509, stops 0.99(1.29), b5 66%, w2l 3 | -1918 $/wk, DD -85.4%, ww -1252, stops 1.45(1.67), b5 67%, w2l 5 | -815 $/wk, DD +38.3%, ww +10200, stops 1.61(2.15), b5 80%, w2l 7 | -92 $/wk, DD +25.5%, ww +0, stops 1.90(2.00), b5 93%, w2l 1 |
| nyam | c | +1150 $/wk, DD +33.8%, ww +3493, stops 1.29(1.29), b5 91%, w2l 2 | +449 $/wk, DD +28.6%, ww +3080, stops 1.48(1.67), b5 69%, w2l 3 | +190 $/wk, DD +56.4%, ww +10647, stops 1.40(2.15), b5 54%, w2l 7 | -102 $/wk, DD +22.6%, ww +0, stops 1.79(2.00), b5 89%, w2l 0 |
| nyam | **b-a** | -838 $/wk, DD -25.6 pts, ww +5373 | -558 $/wk, DD -10.3 pts, ww +245 | +78 $/wk, DD +5.8 pts, ww +3056 | -346 $/wk, DD -6.3 pts, ww +0 |
| nyam | **c-a** | +1777 $/wk, DD +36.4 pts, ww +6356 | +1809 $/wk, DD +103.8 pts, ww +4576 | +1083 $/wk, DD +23.9 pts, ww +3503 | -357 $/wk, DD -9.3 pts, ww +0 |
| nypm | a | -1002 $/wk, DD -86.6%, ww -275, stops 0.08(0.08), b5 29%, w2l 4 | -1251 $/wk, DD -86.6%, ww -275, stops 0.08(0.08), b5 31%, w2l 7 | -853 $/wk, DD -45.5%, ww +1630, stops 0.06(0.04), b5 31%, w2l 13 | -102 $/wk, DD +6.8%, ww +0, stops 0.08(0.05), b5 72%, w2l 1 |
| nypm | b | -523 $/wk, DD +34.9%, ww +822, stops 0.08(0.08), b5 68%, w2l 1 | -583 $/wk, DD +31.9%, ww +822, stops 0.08(0.08), b5 77%, w2l 2 | -181 $/wk, DD +0.8%, ww +1951, stops 0.04(0.04), b5 77%, w2l 6 | -149 $/wk, DD +11.0%, ww +0, stops 0.05(0.05), b5 69%, w2l 2 |
| nypm | c | -558 $/wk, DD -25.9%, ww -183, stops 0.08(0.08), b5 15%, w2l 3 | -258 $/wk, DD -25.9%, ww -183, stops 0.08(0.08), b5 87%, w2l 4 | -127 $/wk, DD +10.6%, ww +2797, stops 0.06(0.04), b5 87%, w2l 8 | -237 $/wk, DD +6.7%, ww +0, stops 0.05(0.05), b5 67%, w2l 2 |
| nypm | **b-a** | +479 $/wk, DD +121.5 pts, ww +1097 | +667 $/wk, DD +118.5 pts, ww +1097 | +672 $/wk, DD +46.3 pts, ww +321 | -47 $/wk, DD +4.2 pts, ww +0 |
| nypm | **c-a** | +444 $/wk, DD +60.7 pts, ww +92 | +993 $/wk, DD +60.7 pts, ww +92 | +726 $/wk, DD +56.1 pts, ww +1166 | -135 $/wk, DD -0.1 pts, ww +0 |

**D4III05** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -3781 $/wk, DD -15.6%, ww -14636, stops 9.82(10.35), b5 65%, w2l 1 | n/a | n/a | n/a |
| all | b | -7835 $/wk, DD +14.8%, ww +3138, stops 9.51(10.35), b5 58%, w2l 2 | n/a | n/a | n/a |
| all | c | -3306 $/wk, DD +6.9%, ww +3588, stops 9.66(10.35), b5 81%, w2l 1 | n/a | n/a | n/a |
| all | **b-a** | -4055 $/wk, DD +30.4 pts, ww +17774 | n/a | n/a | n/a |
| all | **c-a** | +475 $/wk, DD +22.4 pts, ww +18224 | n/a | n/a | n/a |
| asia | a | -2046 $/wk, DD +20.3%, ww -1599, stops 5.93(6.24), b5 101%, w2l 0 | n/a | n/a | n/a |
| asia | b | -5078 $/wk, DD +6.4%, ww -2891, stops 5.93(6.24), b5 87%, w2l 1 | n/a | n/a | n/a |
| asia | c | -55 $/wk, DD -5.3%, ww -4715, stops 6.01(6.24), b5 102%, w2l 1 | n/a | n/a | n/a |
| asia | **b-a** | -3032 $/wk, DD -13.9 pts, ww -1291 | n/a | n/a | n/a |
| asia | **c-a** | +1991 $/wk, DD -25.5 pts, ww -3116 | n/a | n/a | n/a |
| london | a | -687 $/wk, DD -12.5%, ww -3133, stops 2.51(2.74), b5 91%, w2l 1 | n/a | n/a | n/a |
| london | b | -459 $/wk, DD +34.7%, ww +5297, stops 2.13(2.74), b5 71%, w2l 1 | n/a | n/a | n/a |
| london | c | -941 $/wk, DD +27.1%, ww +1661, stops 2.28(2.74), b5 76%, w2l 1 | n/a | n/a | n/a |
| london | **b-a** | +228 $/wk, DD +47.2 pts, ww +8429 | n/a | n/a | n/a |
| london | **c-a** | -254 $/wk, DD +39.6 pts, ww +4794 | n/a | n/a | n/a |
| nyam | a | -40 $/wk, DD -7.4%, ww -5605, stops 1.29(1.29), b5 77%, w2l 2 | n/a | n/a | n/a |
| nyam | b | -1008 $/wk, DD +19.4%, ww -1176, stops 1.37(1.29), b5 42%, w2l 2 | n/a | n/a | n/a |
| nyam | c | -1232 $/wk, DD +11.2%, ww -362, stops 1.29(1.29), b5 63%, w2l 3 | n/a | n/a | n/a |
| nyam | **b-a** | -967 $/wk, DD +26.8 pts, ww +4429 | n/a | n/a | n/a |
| nyam | **c-a** | -1191 $/wk, DD +18.6 pts, ww +5243 | n/a | n/a | n/a |
| nypm | a | -1007 $/wk, DD -74.0%, ww -1262, stops 0.08(0.08), b5 60%, w2l 1 | n/a | n/a | n/a |
| nypm | b | -1291 $/wk, DD -66.8%, ww -856, stops 0.08(0.08), b5 44%, w2l 3 | n/a | n/a | n/a |
| nypm | c | -1079 $/wk, DD -58.9%, ww -1136, stops 0.08(0.08), b5 32%, w2l 3 | n/a | n/a | n/a |
| nypm | **b-a** | -283 $/wk, DD +7.1 pts, ww +405 | n/a | n/a | n/a |
| nypm | **c-a** | -71 $/wk, DD +15.1 pts, ww +125 | n/a | n/a | n/a |

**D4I075** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -7503 $/wk, DD +4.5%, ww +1612, stops 6.92(10.35), b5 60%, w2l 2 | n/a | n/a | n/a |
| all | b | -13182 $/wk, DD +34.8%, ww +16026, stops 6.32(10.35), b5 44%, w2l 2 | n/a | n/a | n/a |
| all | c | -7154 $/wk, DD +2.5%, ww -401, stops 7.00(10.35), b5 67%, w2l 3 | n/a | n/a | n/a |
| all | **b-a** | -5679 $/wk, DD +30.3 pts, ww +14413 | n/a | n/a | n/a |
| all | **c-a** | +349 $/wk, DD -1.9 pts, ww -2013 | n/a | n/a | n/a |
| asia | a | -6661 $/wk, DD +13.0%, ww +8600, stops 3.58(6.24), b5 46%, w2l 2 | n/a | n/a | n/a |
| asia | b | -9955 $/wk, DD +29.9%, ww +4518, stops 3.58(6.24), b5 47%, w2l 2 | n/a | n/a | n/a |
| asia | c | -4529 $/wk, DD +34.3%, ww +4387, stops 4.26(6.24), b5 57%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | -3294 $/wk, DD +16.9 pts, ww -4082 | n/a | n/a | n/a |
| asia | **c-a** | +2132 $/wk, DD +21.3 pts, ww -4213 | n/a | n/a | n/a |
| london | a | -711 $/wk, DD -2.2%, ww +334, stops 1.52(2.74), b5 80%, w2l 0 | n/a | n/a | n/a |
| london | b | -1098 $/wk, DD +60.3%, ww +16284, stops 1.07(2.74), b5 56%, w2l 2 | n/a | n/a | n/a |
| london | c | -3171 $/wk, DD -1.9%, ww +9862, stops 1.37(2.74), b5 53%, w2l 2 | n/a | n/a | n/a |
| london | **b-a** | -387 $/wk, DD +62.5 pts, ww +15950 | n/a | n/a | n/a |
| london | **c-a** | -2460 $/wk, DD +0.2 pts, ww +9528 | n/a | n/a | n/a |
| nyam | a | +561 $/wk, DD +2.4%, ww -1492, stops 1.67(1.29), b5 84%, w2l 3 | n/a | n/a | n/a |
| nyam | b | +5 $/wk, DD +3.6%, ww -470, stops 1.52(1.29), b5 50%, w2l 2 | n/a | n/a | n/a |
| nyam | c | +1364 $/wk, DD +37.8%, ww -462, stops 1.29(1.29), b5 66%, w2l 3 | n/a | n/a | n/a |
| nyam | **b-a** | -556 $/wk, DD +1.2 pts, ww +1022 | n/a | n/a | n/a |
| nyam | **c-a** | +803 $/wk, DD +35.4 pts, ww +1031 | n/a | n/a | n/a |
| nypm | a | -692 $/wk, DD -129.2%, ww -1590, stops 0.15(0.08), b5 101%, w2l 4 | n/a | n/a | n/a |
| nypm | b | -2134 $/wk, DD -279.1%, ww -4662, stops 0.15(0.08), b5 10%, w2l 5 | n/a | n/a | n/a |
| nypm | c | -818 $/wk, DD -42.2%, ww +215, stops 0.08(0.08), b5 26%, w2l 3 | n/a | n/a | n/a |
| nypm | **b-a** | -1442 $/wk, DD -149.8 pts, ww -3072 | n/a | n/a | n/a |
| nypm | **c-a** | -126 $/wk, DD +87.1 pts, ww +1805 | n/a | n/a | n/a |

**D4II075** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -2612 $/wk, DD -16.0%, ww -5553, stops 9.97(10.35), b5 78%, w2l 0 | -5537 $/wk, DD -16.0%, ww -6798, stops 10.23(10.99), b5 94%, w2l 1 | n/a | n/a |
| all | b | -5257 $/wk, DD +9.9%, ww +5619, stops 9.59(10.35), b5 65%, w2l 1 | -4668 $/wk, DD +9.9%, ww +5619, stops 10.12(10.99), b5 84%, w2l 1 | n/a | n/a |
| all | c | -2076 $/wk, DD +30.7%, ww +7445, stops 9.66(10.35), b5 85%, w2l 1 | -2171 $/wk, DD +30.7%, ww +7445, stops 9.97(10.99), b5 101%, w2l 2 | n/a | n/a |
| all | **b-a** | -2645 $/wk, DD +25.9 pts, ww +11172 | +869 $/wk, DD +25.9 pts, ww +12418 | n/a | n/a |
| all | **c-a** | +535 $/wk, DD +46.6 pts, ww +12998 | +3366 $/wk, DD +46.6 pts, ww +14244 | n/a | n/a |
| asia | a | -512 $/wk, DD -11.5%, ww -5570, stops 6.32(6.24), b5 100%, w2l 1 | -3202 $/wk, DD -11.5%, ww -6217, stops 6.20(6.35), b5 100%, w2l 1 | n/a | n/a |
| asia | b | -1319 $/wk, DD +8.0%, ww -2121, stops 6.09(6.24), b5 104%, w2l 1 | -1729 $/wk, DD +8.0%, ww -2121, stops 6.12(6.35), b5 102%, w2l 1 | n/a | n/a |
| asia | c | +2288 $/wk, DD +24.3%, ww -8025, stops 5.86(6.24), b5 111%, w2l 1 | +31 $/wk, DD +20.3%, ww -8025, stops 5.78(6.35), b5 106%, w2l 2 | n/a | n/a |
| asia | **b-a** | -807 $/wk, DD +19.5 pts, ww +3449 | +1473 $/wk, DD +19.5 pts, ww +4096 | n/a | n/a |
| asia | **c-a** | +2800 $/wk, DD +35.8 pts, ww -2455 | +3233 $/wk, DD +31.8 pts, ww -1807 | n/a | n/a |
| london | a | -2337 $/wk, DD -24.8%, ww -10688, stops 2.43(2.74), b5 78%, w2l 0 | -1512 $/wk, DD -24.8%, ww -10688, stops 2.59(2.89), b5 86%, w2l 0 | n/a | n/a |
| london | b | -2998 $/wk, DD +32.5%, ww -6174, stops 2.21(2.74), b5 54%, w2l 1 | -1751 $/wk, DD +32.5%, ww -6174, stops 2.32(2.89), b5 69%, w2l 2 | n/a | n/a |
| london | c | -4751 $/wk, DD -10.1%, ww -5106, stops 2.59(2.74), b5 69%, w2l 2 | -2315 $/wk, DD -10.1%, ww -5106, stops 2.62(2.89), b5 74%, w2l 2 | n/a | n/a |
| london | **b-a** | -661 $/wk, DD +57.3 pts, ww +4514 | -238 $/wk, DD +57.3 pts, ww +4514 | n/a | n/a |
| london | **c-a** | -2415 $/wk, DD +14.7 pts, ww +5582 | -802 $/wk, DD +14.7 pts, ww +5582 | n/a | n/a |
| nyam | a | +661 $/wk, DD -9.6%, ww +826, stops 1.14(1.29), b5 117%, w2l 3 | -69 $/wk, DD -1.7%, ww +3414, stops 1.37(1.67), b5 97%, w2l 4 | n/a | n/a |
| nyam | b | +10 $/wk, DD +23.6%, ww -1872, stops 1.22(1.29), b5 91%, w2l 1 | -632 $/wk, DD -29.9%, ww -1695, stops 1.60(1.67), b5 75%, w2l 2 | n/a | n/a |
| nyam | c | +594 $/wk, DD +33.2%, ww +173, stops 1.14(1.29), b5 73%, w2l 1 | +284 $/wk, DD -35.1%, ww +661, stops 1.48(1.67), b5 97%, w2l 3 | n/a | n/a |
| nyam | **b-a** | -651 $/wk, DD +33.2 pts, ww -2698 | -563 $/wk, DD -28.2 pts, ww -5108 | n/a | n/a |
| nyam | **c-a** | -67 $/wk, DD +42.8 pts, ww -653 | +352 $/wk, DD -33.4 pts, ww -2753 | n/a | n/a |
| nypm | a | -424 $/wk, DD -19.9%, ww +232, stops 0.08(0.08), b5 99%, w2l 2 | -754 $/wk, DD -19.9%, ww +232, stops 0.08(0.08), b5 50%, w2l 2 | n/a | n/a |
| nypm | b | -950 $/wk, DD -49.7%, ww -248, stops 0.08(0.08), b5 38%, w2l 3 | -557 $/wk, DD -49.7%, ww -248, stops 0.08(0.08), b5 62%, w2l 4 | n/a | n/a |
| nypm | c | -207 $/wk, DD +17.2%, ww +2284, stops 0.08(0.08), b5 61%, w2l 2 | -171 $/wk, DD +17.2%, ww +1546, stops 0.08(0.08), b5 70%, w2l 4 | n/a | n/a |
| nypm | **b-a** | -526 $/wk, DD -29.7 pts, ww -480 | +198 $/wk, DD -29.7 pts, ww -480 | n/a | n/a |
| nypm | **c-a** | +217 $/wk, DD +37.2 pts, ww +2052 | +584 $/wk, DD +37.2 pts, ww +1314 | n/a | n/a |

**D4III075** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -618 $/wk, DD +2.2%, ww -1335, stops 9.97(10.35), b5 84%, w2l 0 | n/a | n/a | n/a |
| all | b | -5177 $/wk, DD +13.4%, ww +4469, stops 9.89(10.35), b5 72%, w2l 1 | n/a | n/a | n/a |
| all | c | -1736 $/wk, DD +14.4%, ww +6168, stops 10.35(10.35), b5 96%, w2l 1 | n/a | n/a | n/a |
| all | **b-a** | -4559 $/wk, DD +11.2 pts, ww +5804 | n/a | n/a | n/a |
| all | **c-a** | -1118 $/wk, DD +12.2 pts, ww +7504 | n/a | n/a | n/a |
| asia | a | -1238 $/wk, DD +4.1%, ww +289, stops 6.24(6.24), b5 92%, w2l 0 | n/a | n/a | n/a |
| asia | b | -385 $/wk, DD +0.4%, ww -821, stops 6.01(6.24), b5 102%, w2l 0 | n/a | n/a | n/a |
| asia | c | -537 $/wk, DD +6.6%, ww -5288, stops 6.16(6.24), b5 98%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | +853 $/wk, DD -3.7 pts, ww -1110 | n/a | n/a | n/a |
| asia | **c-a** | +701 $/wk, DD +2.4 pts, ww -5577 | n/a | n/a | n/a |
| london | a | +1033 $/wk, DD -1.6%, ww -2586, stops 2.36(2.74), b5 98%, w2l 0 | n/a | n/a | n/a |
| london | b | -2910 $/wk, DD +8.9%, ww -845, stops 2.51(2.74), b5 63%, w2l 1 | n/a | n/a | n/a |
| london | c | -109 $/wk, DD +15.4%, ww +4321, stops 2.66(2.74), b5 90%, w2l 0 | n/a | n/a | n/a |
| london | **b-a** | -3943 $/wk, DD +10.5 pts, ww +1741 | n/a | n/a | n/a |
| london | **c-a** | -1142 $/wk, DD +17.0 pts, ww +6907 | n/a | n/a | n/a |
| nyam | a | +342 $/wk, DD +1.2%, ww -2762, stops 1.29(1.29), b5 95%, w2l 2 | n/a | n/a | n/a |
| nyam | b | -912 $/wk, DD -20.2%, ww -4661, stops 1.29(1.29), b5 54%, w2l 3 | n/a | n/a | n/a |
| nyam | c | -131 $/wk, DD -13.4%, ww -3051, stops 1.45(1.29), b5 62%, w2l 1 | n/a | n/a | n/a |
| nyam | **b-a** | -1255 $/wk, DD -21.4 pts, ww -1899 | n/a | n/a | n/a |
| nyam | **c-a** | -474 $/wk, DD -14.6 pts, ww -289 | n/a | n/a | n/a |
| nypm | a | -756 $/wk, DD -43.3%, ww +316, stops 0.08(0.08), b5 74%, w2l 2 | n/a | n/a | n/a |
| nypm | b | -970 $/wk, DD -33.8%, ww +1, stops 0.08(0.08), b5 48%, w2l 1 | n/a | n/a | n/a |
| nypm | c | -959 $/wk, DD -67.3%, ww -1198, stops 0.08(0.08), b5 42%, w2l 2 | n/a | n/a | n/a |
| nypm | **b-a** | -214 $/wk, DD +9.5 pts, ww -315 | n/a | n/a | n/a |
| nypm | **c-a** | -203 $/wk, DD -24.0 pts, ww -1514 | n/a | n/a | n/a |

**D4I1** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -3374 $/wk, DD +30.3%, ww +12801, stops 7.68(10.35), b5 77%, w2l 2 | -6639 $/wk, DD +29.4%, ww +12801, stops 8.18(10.99), b5 55%, w2l 2 | -4632 $/wk, DD +21.6%, ww +9662, stops 7.67(10.66), b5 60%, w2l 7 | +294 $/wk, DD +0.0%, ww +0, stops 8.62(9.31), b5 104%, w2l 0 |
| all | b | -9442 $/wk, DD -6.6%, ww +7549, stops 7.46(10.35), b5 67%, w2l 3 | -10325 $/wk, DD -6.6%, ww +7549, stops 7.91(10.99), b5 40%, w2l 4 | -7800 $/wk, DD -3.4%, ww -5933, stops 7.25(10.66), b5 33%, w2l 8 | -1402 $/wk, DD +0.0%, ww +0, stops 8.51(9.31), b5 92%, w2l 1 |
| all | c | -4492 $/wk, DD +36.2%, ww +16680, stops 7.68(10.35), b5 77%, w2l 3 | -8276 $/wk, DD +36.2%, ww +16680, stops 8.14(10.99), b5 66%, w2l 5 | -5085 $/wk, DD +23.9%, ww +9872, stops 7.19(10.66), b5 54%, w2l 8 | -1152 $/wk, DD +0.0%, ww +0, stops 8.44(9.31), b5 99%, w2l 1 |
| all | **b-a** | -6068 $/wk, DD -36.9 pts, ww -5252 | -3686 $/wk, DD -36.0 pts, ww -5252 | -3168 $/wk, DD -24.9 pts, ww -15595 | -1695 $/wk, DD +0.0 pts, ww +0 |
| all | **c-a** | -1118 $/wk, DD +5.9 pts, ww +3879 | -1637 $/wk, DD +6.8 pts, ww +3879 | -452 $/wk, DD +2.3 pts, ww +210 | -1446 $/wk, DD +0.0 pts, ww +0 |
| asia | a | -8204 $/wk, DD +33.2%, ww +434, stops 4.18(6.24), b5 48%, w2l 2 | -7864 $/wk, DD +33.2%, ww +434, stops 3.84(6.35), b5 43%, w2l 3 | -6810 $/wk, DD +22.5%, ww +33071, stops 3.47(5.87), b5 54%, w2l 8 | -1009 $/wk, DD +0.0%, ww +0, stops 3.79(4.18), b5 94%, w2l 2 |
| asia | b | -5372 $/wk, DD +36.7%, ww +8193, stops 4.26(6.24), b5 64%, w2l 0 | -6720 $/wk, DD +36.7%, ww +8193, stops 3.80(6.35), b5 47%, w2l 2 | -7576 $/wk, DD +5.6%, ww -3312, stops 3.32(5.87), b5 41%, w2l 7 | -2158 $/wk, DD +0.0%, ww +0, stops 3.77(4.18), b5 80%, w2l 3 |
| asia | c | -3594 $/wk, DD +39.8%, ww -4497, stops 4.49(6.24), b5 55%, w2l 0 | -5878 $/wk, DD +27.6%, ww -4497, stops 4.22(6.35), b5 51%, w2l 2 | -6053 $/wk, DD +15.3%, ww +4798, stops 3.51(5.87), b5 46%, w2l 6 | -1702 $/wk, DD +0.0%, ww +0, stops 3.74(4.18), b5 89%, w2l 3 |
| asia | **b-a** | +2831 $/wk, DD +3.6 pts, ww +7759 | +1144 $/wk, DD +3.6 pts, ww +7759 | -766 $/wk, DD -16.8 pts, ww -36383 | -1149 $/wk, DD +0.0 pts, ww +0 |
| asia | **c-a** | +4610 $/wk, DD +6.6 pts, ww -4931 | +1986 $/wk, DD -5.6 pts, ww -4931 | +758 $/wk, DD -7.1 pts, ww -28273 | -692 $/wk, DD +0.0 pts, ww +0 |
| london | a | +4852 $/wk, DD +20.3%, ww +2731, stops 1.60(2.74), b5 118%, w2l 1 | +2506 $/wk, DD +20.3%, ww +2731, stops 2.05(2.89), b5 95%, w2l 1 | +1702 $/wk, DD +20.3%, ww +2731, stops 1.94(2.61), b5 103%, w2l 7 | +1297 $/wk, DD +0.0%, ww +0, stops 2.77(3.08), b5 90%, w2l 0 |
| london | b | -2945 $/wk, DD +30.7%, ww +3850, stops 1.52(2.74), b5 64%, w2l 3 | -1768 $/wk, DD +30.7%, ww +3850, stops 2.02(2.89), b5 69%, w2l 4 | -554 $/wk, DD +30.7%, ww +3850, stops 1.98(2.61), b5 77%, w2l 6 | +764 $/wk, DD +0.0%, ww +0, stops 2.74(3.08), b5 94%, w2l 1 |
| london | c | -1951 $/wk, DD +11.6%, ww +7446, stops 1.83(2.74), b5 69%, w2l 2 | -1293 $/wk, DD +11.6%, ww +7446, stops 2.05(2.89), b5 80%, w2l 3 | -23 $/wk, DD +11.6%, ww +7446, stops 1.90(2.61), b5 85%, w2l 7 | +887 $/wk, DD +0.0%, ww +0, stops 2.87(3.08), b5 92%, w2l 1 |
| london | **b-a** | -7797 $/wk, DD +10.4 pts, ww +1119 | -4273 $/wk, DD +10.4 pts, ww +1119 | -2256 $/wk, DD +10.4 pts, ww +1119 | -533 $/wk, DD +0.0 pts, ww +0 |
| london | **c-a** | -6803 $/wk, DD -8.7 pts, ww +4715 | -3798 $/wk, DD -8.7 pts, ww +4715 | -1725 $/wk, DD -8.7 pts, ww +4715 | -410 $/wk, DD +0.0 pts, ww +0 |
| nyam | a | +474 $/wk, DD +9.9%, ww -1768, stops 1.75(1.29), b5 85%, w2l 2 | -416 $/wk, DD -5.9%, ww +819, stops 2.13(1.67), b5 59%, w2l 6 | +792 $/wk, DD +54.4%, ww +3416, stops 2.15(2.15), b5 89%, w2l 7 | +181 $/wk, DD +15.5%, ww +0, stops 2.00(2.00), b5 93%, w2l 0 |
| nyam | b | -115 $/wk, DD -6.8%, ww -4730, stops 1.52(1.29), b5 71%, w2l 2 | -1164 $/wk, DD -35.4%, ww -2143, stops 1.94(1.67), b5 53%, w2l 6 | +638 $/wk, DD +55.0%, ww +4443, stops 1.84(2.15), b5 81%, w2l 8 | +164 $/wk, DD +10.6%, ww +0, stops 1.95(2.00), b5 91%, w2l 0 |
| nyam | c | +2073 $/wk, DD +44.4%, ww +1358, stops 1.29(1.29), b5 83%, w2l 2 | -580 $/wk, DD -59.9%, ww +1196, stops 1.79(1.67), b5 30%, w2l 5 | +946 $/wk, DD +31.4%, ww +2798, stops 1.73(2.15), b5 65%, w2l 8 | +41 $/wk, DD +31.9%, ww +0, stops 1.77(2.00), b5 98%, w2l 1 |
| nyam | **b-a** | -589 $/wk, DD -16.7 pts, ww -2962 | -748 $/wk, DD -29.5 pts, ww -2962 | -154 $/wk, DD +0.6 pts, ww +1027 | -17 $/wk, DD -4.9 pts, ww +0 |
| nyam | **c-a** | +1599 $/wk, DD +34.5 pts, ww +3126 | -163 $/wk, DD -54.0 pts, ww +376 | +155 $/wk, DD -23.0 pts, ww -618 | -140 $/wk, DD +16.4 pts, ww +0 |
| nypm | a | -496 $/wk, DD -47.1%, ww -653, stops 0.15(0.08), b5 86%, w2l 4 | -864 $/wk, DD -47.1%, ww -1521, stops 0.15(0.08), b5 47%, w2l 7 | -315 $/wk, DD +6.4%, ww +2959, stops 0.12(0.04), b5 47%, w2l 12 | -174 $/wk, DD -17.3%, ww +0, stops 0.05(0.05), b5 85%, w2l 0 |
| nypm | b | -1010 $/wk, DD -155.0%, ww -3994, stops 0.15(0.08), b5 61%, w2l 4 | -673 $/wk, DD -155.0%, ww -3994, stops 0.15(0.08), b5 69%, w2l 6 | -308 $/wk, DD +0.8%, ww +1157, stops 0.12(0.04), b5 69%, w2l 12 | -171 $/wk, DD -22.9%, ww +0, stops 0.05(0.05), b5 88%, w2l 0 |
| nypm | c | -1019 $/wk, DD -76.8%, ww -244, stops 0.08(0.08), b5 34%, w2l 3 | -526 $/wk, DD -76.8%, ww -244, stops 0.08(0.08), b5 80%, w2l 4 | +45 $/wk, DD +11.1%, ww +1938, stops 0.06(0.04), b5 80%, w2l 10 | -378 $/wk, DD -18.4%, ww +0, stops 0.05(0.05), b5 56%, w2l 2 |
| nypm | **b-a** | -514 $/wk, DD -107.9 pts, ww -3341 | +191 $/wk, DD -107.9 pts, ww -2473 | +8 $/wk, DD -5.6 pts, ww -1802 | +3 $/wk, DD -5.6 pts, ww +0 |
| nypm | **c-a** | -523 $/wk, DD -29.7 pts, ww +408 | +338 $/wk, DD -29.7 pts, ww +1276 | +360 $/wk, DD +4.7 pts, ww -1021 | -204 $/wk, DD -1.1 pts, ww +0 |

**D4II1** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -3937 $/wk, DD -16.1%, ww -6232, stops 10.27(10.35), b5 77%, w2l 0 | -4925 $/wk, DD -16.1%, ww -6232, stops 10.46(10.99), b5 96%, w2l 1 | -3951 $/wk, DD -0.7%, ww -7029, stops 9.95(10.66), b5 80%, w2l 5 | n/a |
| all | b | -2053 $/wk, DD +12.0%, ww +6618, stops 10.20(10.35), b5 77%, w2l 1 | -2306 $/wk, DD +12.0%, ww +3010, stops 10.54(10.99), b5 84%, w2l 1 | -2474 $/wk, DD +11.0%, ww -493, stops 10.11(10.66), b5 78%, w2l 3 | n/a |
| all | c | -1435 $/wk, DD +15.8%, ww +8264, stops 9.97(10.35), b5 86%, w2l 1 | -717 $/wk, DD +15.8%, ww +8264, stops 10.16(10.99), b5 105%, w2l 2 | -2085 $/wk, DD +11.7%, ww +2818, stops 9.72(10.66), b5 95%, w2l 5 | n/a |
| all | **b-a** | +1884 $/wk, DD +28.2 pts, ww +12850 | +2619 $/wk, DD +28.2 pts, ww +9242 | +1477 $/wk, DD +11.7 pts, ww +6536 | n/a |
| all | **c-a** | +2502 $/wk, DD +31.9 pts, ww +14496 | +4209 $/wk, DD +31.9 pts, ww +14496 | +1866 $/wk, DD +12.4 pts, ww +9846 | n/a |
| asia | a | -1857 $/wk, DD -9.9%, ww -4797, stops 6.47(6.24), b5 103%, w2l 0 | -3358 $/wk, DD -9.9%, ww -6691, stops 6.16(6.35), b5 100%, w2l 0 | -3298 $/wk, DD -1.4%, ww -133, stops 5.58(5.87), b5 96%, w2l 1 | n/a |
| asia | b | +1780 $/wk, DD +8.2%, ww -1241, stops 6.39(6.24), b5 106%, w2l 0 | +589 $/wk, DD +8.2%, ww -1241, stops 6.24(6.35), b5 104%, w2l 0 | -1170 $/wk, DD -0.7%, ww -2787, stops 5.70(5.87), b5 89%, w2l 3 | n/a |
| asia | c | +1423 $/wk, DD +7.4%, ww -3821, stops 5.93(6.24), b5 103%, w2l 0 | +279 $/wk, DD +7.4%, ww -3821, stops 5.90(6.35), b5 104%, w2l 0 | -1811 $/wk, DD -14.6%, ww -4428, stops 5.56(5.87), b5 99%, w2l 4 | n/a |
| asia | **b-a** | +3637 $/wk, DD +18.1 pts, ww +3556 | +3946 $/wk, DD +18.1 pts, ww +5450 | +2128 $/wk, DD +0.6 pts, ww -2653 | n/a |
| asia | **c-a** | +3281 $/wk, DD +17.3 pts, ww +976 | +3637 $/wk, DD +17.3 pts, ww +2870 | +1487 $/wk, DD -13.2 pts, ww -4295 | n/a |
| london | a | -2334 $/wk, DD -9.5%, ww -6221, stops 2.59(2.74), b5 73%, w2l 0 | -872 $/wk, DD -9.5%, ww -6221, stops 2.78(2.89), b5 83%, w2l 0 | -876 $/wk, DD -9.5%, ww -6221, stops 2.40(2.61), b5 82%, w2l 1 | n/a |
| london | b | -2317 $/wk, DD +35.8%, ww -6158, stops 2.28(2.74), b5 64%, w2l 1 | -1822 $/wk, DD +35.8%, ww -6158, stops 2.43(2.89), b5 72%, w2l 1 | -981 $/wk, DD +4.5%, ww -6158, stops 2.30(2.61), b5 75%, w2l 2 | n/a |
| london | c | -3262 $/wk, DD +14.1%, ww -2826, stops 2.66(2.74), b5 73%, w2l 2 | -712 $/wk, DD +14.1%, ww -2826, stops 2.62(2.89), b5 82%, w2l 3 | -691 $/wk, DD +14.1%, ww -2826, stops 2.36(2.61), b5 73%, w2l 6 | n/a |
| london | **b-a** | +17 $/wk, DD +45.2 pts, ww +63 | -950 $/wk, DD +45.2 pts, ww +63 | -105 $/wk, DD +14.0 pts, ww +63 | n/a |
| london | **c-a** | -929 $/wk, DD +23.6 pts, ww +3395 | +160 $/wk, DD +23.6 pts, ww +3395 | +184 $/wk, DD +23.6 pts, ww +3395 | n/a |
| nyam | a | +525 $/wk, DD +11.3%, ww -1454, stops 1.14(1.29), b5 115%, w2l 2 | -271 $/wk, DD +0.1%, ww -795, stops 1.45(1.67), b5 100%, w2l 2 | +384 $/wk, DD +31.5%, ww +2946, stops 1.94(2.15), b5 81%, w2l 5 | n/a |
| nyam | b | -514 $/wk, DD -13.6%, ww +130, stops 1.45(1.29), b5 96%, w2l 2 | -233 $/wk, DD +11.4%, ww +1971, stops 1.79(1.67), b5 67%, w2l 2 | +62 $/wk, DD +18.5%, ww +3200, stops 2.07(2.15), b5 77%, w2l 3 | n/a |
| nyam | c | +628 $/wk, DD +37.5%, ww +1493, stops 1.29(1.29), b5 84%, w2l 2 | -104 $/wk, DD -21.3%, ww -2080, stops 1.56(1.67), b5 72%, w2l 3 | +710 $/wk, DD +47.1%, ww +5734, stops 1.76(2.15), b5 91%, w2l 6 | n/a |
| nyam | **b-a** | -1039 $/wk, DD -24.9 pts, ww +1584 | +37 $/wk, DD +11.3 pts, ww +2766 | -322 $/wk, DD -13.0 pts, ww +254 | n/a |
| nyam | **c-a** | +102 $/wk, DD +26.2 pts, ww +2948 | +167 $/wk, DD -21.4 pts, ww -1285 | +326 $/wk, DD +15.5 pts, ww +2788 | n/a |
| nypm | a | -271 $/wk, DD -13.5%, ww +526, stops 0.08(0.08), b5 92%, w2l 1 | -424 $/wk, DD -13.5%, ww +526, stops 0.08(0.08), b5 51%, w2l 1 | -161 $/wk, DD -1.5%, ww -134, stops 0.04(0.04), b5 51%, w2l 4 | n/a |
| nypm | b | -1003 $/wk, DD -42.2%, ww +97, stops 0.08(0.08), b5 24%, w2l 4 | -839 $/wk, DD -42.2%, ww +97, stops 0.08(0.08), b5 49%, w2l 4 | -385 $/wk, DD +5.8%, ww +2684, stops 0.04(0.04), b5 49%, w2l 8 | n/a |
| nypm | c | -224 $/wk, DD -17.8%, ww +232, stops 0.08(0.08), b5 81%, w2l 3 | -180 $/wk, DD -17.8%, ww -300, stops 0.08(0.08), b5 83%, w2l 4 | -293 $/wk, DD -27.5%, ww +1730, stops 0.04(0.04), b5 83%, w2l 9 | n/a |
| nypm | **b-a** | -732 $/wk, DD -28.7 pts, ww -429 | -415 $/wk, DD -28.7 pts, ww -429 | -224 $/wk, DD +7.2 pts, ww +2818 | n/a |
| nypm | **c-a** | +47 $/wk, DD -4.3 pts, ww -294 | +245 $/wk, DD -4.3 pts, ww -826 | -132 $/wk, DD -26.0 pts, ww +1863 | n/a |

**D4III1** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -382 $/wk, DD +3.6%, ww +643, stops 10.35(10.35), b5 87%, w2l 0 | -3871 $/wk, DD +3.6%, ww +643, stops 10.16(10.99), b5 82%, w2l 0 | -1743 $/wk, DD +3.7%, ww +5652, stops 9.70(10.66), b5 85%, w2l 2 | -2713 $/wk, DD +0.0%, ww +0, stops 9.08(9.31), b5 82%, w2l 0 |
| all | b | -734 $/wk, DD +14.1%, ww +3999, stops 10.35(10.35), b5 84%, w2l 0 | -3204 $/wk, DD +14.1%, ww +3999, stops 10.20(10.99), b5 75%, w2l 0 | -1694 $/wk, DD +13.9%, ww +5482, stops 9.74(10.66), b5 71%, w2l 3 | -1487 $/wk, DD +0.0%, ww +0, stops 9.03(9.31), b5 88%, w2l 0 |
| all | c | -191 $/wk, DD +3.3%, ww +746, stops 10.12(10.35), b5 100%, w2l 1 | -3220 $/wk, DD +3.3%, ww +746, stops 10.16(10.99), b5 88%, w2l 1 | -1318 $/wk, DD +16.6%, ww +5088, stops 9.70(10.66), b5 77%, w2l 3 | -2189 $/wk, DD +0.0%, ww +0, stops 9.08(9.31), b5 90%, w2l 1 |
| all | **b-a** | -352 $/wk, DD +10.4 pts, ww +3355 | +667 $/wk, DD +10.4 pts, ww +3355 | +49 $/wk, DD +10.1 pts, ww -170 | +1226 $/wk, DD +0.0 pts, ww +0 |
| all | **c-a** | +191 $/wk, DD -0.3 pts, ww +102 | +651 $/wk, DD -0.3 pts, ww +102 | +426 $/wk, DD +12.9 pts, ww -564 | +524 $/wk, DD +0.0 pts, ww +0 |
| asia | a | -2700 $/wk, DD +6.0%, ww +434, stops 6.24(6.24), b5 90%, w2l 1 | -3730 $/wk, DD +6.0%, ww +434, stops 6.09(6.35), b5 75%, w2l 2 | -3036 $/wk, DD +5.4%, ww +3506, stops 5.52(5.87), b5 76%, w2l 3 | -2246 $/wk, DD -4.6%, ww +0, stops 4.10(4.18), b5 78%, w2l 3 |
| asia | b | +854 $/wk, DD +8.6%, ww +249, stops 6.16(6.24), b5 105%, w2l 0 | -1460 $/wk, DD +8.6%, ww +249, stops 5.93(6.35), b5 81%, w2l 1 | -2248 $/wk, DD +9.0%, ww -693, stops 5.41(5.87), b5 68%, w2l 4 | -1573 $/wk, DD +0.0%, ww +0, stops 4.05(4.18), b5 81%, w2l 1 |
| asia | c | -776 $/wk, DD +7.1%, ww -3596, stops 6.24(6.24), b5 93%, w2l 1 | -2696 $/wk, DD +7.1%, ww -3596, stops 6.09(6.35), b5 75%, w2l 2 | -2628 $/wk, DD +7.7%, ww -2081, stops 5.54(5.87), b5 69%, w2l 5 | -1414 $/wk, DD +0.0%, ww +0, stops 4.05(4.18), b5 83%, w2l 1 |
| asia | **b-a** | +3554 $/wk, DD +2.7 pts, ww -185 | +2271 $/wk, DD +2.7 pts, ww -185 | +788 $/wk, DD +3.7 pts, ww -4199 | +673 $/wk, DD +4.6 pts, ww +0 |
| asia | **c-a** | +1923 $/wk, DD +1.1 pts, ww -4030 | +1034 $/wk, DD +1.1 pts, ww -4030 | +408 $/wk, DD +2.3 pts, ww -5587 | +832 $/wk, DD +4.6 pts, ww +0 |
| london | a | +2290 $/wk, DD +16.4%, ww +5209, stops 2.59(2.74), b5 106%, w2l 0 | +583 $/wk, DD +16.4%, ww +5209, stops 2.43(2.89), b5 94%, w2l 0 | +494 $/wk, DD +16.4%, ww +5209, stops 2.21(2.61), b5 101%, w2l 1 | +223 $/wk, DD +0.0%, ww +0, stops 2.95(3.08), b5 90%, w2l 0 |
| london | b | -392 $/wk, DD +16.2%, ww +4005, stops 2.66(2.74), b5 88%, w2l 0 | -710 $/wk, DD +16.2%, ww +4005, stops 2.59(2.89), b5 86%, w2l 0 | -221 $/wk, DD +12.8%, ww +4005, stops 2.34(2.61), b5 95%, w2l 2 | +365 $/wk, DD +0.0%, ww +0, stops 2.92(3.08), b5 92%, w2l 1 |
| london | c | +1295 $/wk, DD +15.7%, ww +6915, stops 2.36(2.74), b5 103%, w2l 0 | +413 $/wk, DD +15.7%, ww +6915, stops 2.43(2.89), b5 101%, w2l 0 | +802 $/wk, DD +15.7%, ww +3808, stops 2.19(2.61), b5 103%, w2l 1 | -206 $/wk, DD +0.0%, ww +0, stops 3.08(3.08), b5 92%, w2l 1 |
| london | **b-a** | -2683 $/wk, DD -0.3 pts, ww -1204 | -1293 $/wk, DD -0.3 pts, ww -1204 | -715 $/wk, DD -3.6 pts, ww -1204 | +142 $/wk, DD +0.0 pts, ww +0 |
| london | **c-a** | -996 $/wk, DD -0.7 pts, ww +1706 | -170 $/wk, DD -0.7 pts, ww +1706 | +309 $/wk, DD -0.7 pts, ww -1401 | -429 $/wk, DD +0.0 pts, ww +0 |
| nyam | a | +683 $/wk, DD -21.8%, ww -4321, stops 1.45(1.29), b5 104%, w2l 1 | +9 $/wk, DD +5.0%, ww -1734, stops 1.56(1.67), b5 86%, w2l 2 | +793 $/wk, DD +32.1%, ww +2388, stops 1.94(2.15), b5 92%, w2l 6 | -272 $/wk, DD -20.6%, ww +0, stops 1.97(2.00), b5 82%, w2l 0 |
| nyam | b | -170 $/wk, DD -20.3%, ww -6230, stops 1.45(1.29), b5 92%, w2l 3 | -309 $/wk, DD +6.2%, ww -3643, stops 1.60(1.67), b5 74%, w2l 4 | +772 $/wk, DD +51.4%, ww +3655, stops 1.96(2.15), b5 85%, w2l 6 | -62 $/wk, DD +5.9%, ww +0, stops 2.00(2.00), b5 80%, w2l 0 |
| nyam | c | +15 $/wk, DD -16.8%, ww -4321, stops 1.45(1.29), b5 60%, w2l 0 | -337 $/wk, DD +6.9%, ww -1734, stops 1.56(1.67), b5 61%, w2l 1 | +786 $/wk, DD +60.5%, ww +3522, stops 1.94(2.15), b5 79%, w2l 4 | -283 $/wk, DD +0.4%, ww +0, stops 1.90(2.00), b5 79%, w2l 1 |
| nyam | **b-a** | -853 $/wk, DD +1.5 pts, ww -1909 | -318 $/wk, DD +1.2 pts, ww -1909 | -21 $/wk, DD +19.3 pts, ww +1267 | +210 $/wk, DD +26.5 pts, ww +0 |
| nyam | **c-a** | -667 $/wk, DD +5.0 pts, ww +0 | -346 $/wk, DD +1.9 pts, ww +0 | -7 $/wk, DD +28.3 pts, ww +1134 | -11 $/wk, DD +21.0 pts, ww +0 |
| nypm | a | -655 $/wk, DD -78.4%, ww -286, stops 0.08(0.08), b5 92%, w2l 0 | -733 $/wk, DD -78.4%, ww -286, stops 0.08(0.08), b5 60%, w2l 1 | +6 $/wk, DD +52.5%, ww +1685, stops 0.04(0.04), b5 60%, w2l 6 | -418 $/wk, DD -23.2%, ww +0, stops 0.05(0.05), b5 74%, w2l 2 |
| nypm | b | -1026 $/wk, DD -56.2%, ww +111, stops 0.08(0.08), b5 61%, w2l 3 | -725 $/wk, DD -56.2%, ww -1109, stops 0.08(0.08), b5 74%, w2l 4 | +2 $/wk, DD +35.9%, ww +2179, stops 0.04(0.04), b5 74%, w2l 7 | -217 $/wk, DD -12.8%, ww +0, stops 0.05(0.05), b5 82%, w2l 1 |
| nypm | c | -725 $/wk, DD -19.5%, ww -286, stops 0.08(0.08), b5 44%, w2l 1 | -600 $/wk, DD -19.5%, ww -814, stops 0.08(0.08), b5 63%, w2l 2 | -278 $/wk, DD -13.4%, ww +1630, stops 0.04(0.04), b5 63%, w2l 8 | -286 $/wk, DD -1.3%, ww +0, stops 0.05(0.05), b5 66%, w2l 1 |
| nypm | **b-a** | -371 $/wk, DD +22.2 pts, ww +397 | +8 $/wk, DD +22.2 pts, ww -823 | -4 $/wk, DD -16.6 pts, ww +495 | +201 $/wk, DD +10.4 pts, ww +0 |
| nypm | **c-a** | -69 $/wk, DD +58.9 pts, ww +0 | +133 $/wk, DD +58.9 pts, ww -528 | -284 $/wk, DD -65.9 pts, ww -55 | +132 $/wk, DD +21.9 pts, ww +0 |

**D4I125** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -2158 $/wk, DD +30.4%, ww +13288, stops 8.60(10.35), b5 79%, w2l 1 | -5655 $/wk, DD +29.9%, ww +13288, stops 8.75(10.99), b5 60%, w2l 1 | -3933 $/wk, DD +7.8%, ww +814, stops 8.23(10.66), b5 67%, w2l 5 | +8 $/wk, DD +0.0%, ww +0, stops 8.79(9.31), b5 103%, w2l 0 |
| all | b | -8986 $/wk, DD +24.4%, ww +5216, stops 8.14(10.35), b5 68%, w2l 3 | -10075 $/wk, DD +24.4%, ww +5216, stops 8.48(10.99), b5 42%, w2l 3 | -8437 $/wk, DD -20.8%, ww +907, stops 7.96(10.66), b5 39%, w2l 8 | -303 $/wk, DD +0.0%, ww +0, stops 8.62(9.31), b5 100%, w2l 1 |
| all | c | -4586 $/wk, DD +22.7%, ww +13782, stops 8.22(10.35), b5 79%, w2l 3 | -9491 $/wk, DD +22.7%, ww +13782, stops 8.45(10.99), b5 57%, w2l 5 | -7188 $/wk, DD +5.1%, ww -7409, stops 7.77(10.66), b5 51%, w2l 7 | -586 $/wk, DD +0.0%, ww +0, stops 8.46(9.31), b5 104%, w2l 1 |
| all | **b-a** | -6828 $/wk, DD -6.0 pts, ww -8072 | -4420 $/wk, DD -5.5 pts, ww -8072 | -4504 $/wk, DD -28.6 pts, ww +93 | -312 $/wk, DD +0.0 pts, ww +0 |
| all | **c-a** | -2428 $/wk, DD -7.7 pts, ww +494 | -3836 $/wk, DD -7.2 pts, ww +494 | -3256 $/wk, DD -2.7 pts, ww -8224 | -594 $/wk, DD +0.0 pts, ww +0 |
| asia | a | -6096 $/wk, DD +37.9%, ww +434, stops 4.95(6.24), b5 52%, w2l 2 | -6895 $/wk, DD +37.8%, ww +434, stops 4.30(6.35), b5 46%, w2l 3 | -5990 $/wk, DD +7.6%, ww +33071, stops 3.85(5.87), b5 59%, w2l 8 | -1406 $/wk, DD +0.0%, ww +0, stops 3.85(4.18), b5 94%, w2l 2 |
| asia | b | -5000 $/wk, DD +34.3%, ww +434, stops 4.57(6.24), b5 60%, w2l 0 | -6549 $/wk, DD +34.3%, ww +434, stops 4.18(6.35), b5 48%, w2l 2 | -8020 $/wk, DD -5.1%, ww +2875, stops 3.72(5.87), b5 42%, w2l 8 | -1773 $/wk, DD -6.9%, ww +0, stops 3.82(4.18), b5 89%, w2l 3 |
| asia | c | -2980 $/wk, DD +39.8%, ww -4497, stops 5.02(6.24), b5 59%, w2l 0 | -5748 $/wk, DD +27.6%, ww -4497, stops 4.53(6.35), b5 47%, w2l 1 | -7171 $/wk, DD +6.4%, ww -3312, stops 3.97(5.87), b5 47%, w2l 6 | -1378 $/wk, DD +0.0%, ww +0, stops 3.77(4.18), b5 92%, w2l 2 |
| asia | **b-a** | +1097 $/wk, DD -3.6 pts, ww +0 | +346 $/wk, DD -3.5 pts, ww +0 | -2030 $/wk, DD -12.6 pts, ww -30196 | -367 $/wk, DD -6.9 pts, ww +0 |
| asia | **c-a** | +3117 $/wk, DD +1.9 pts, ww -4931 | +1147 $/wk, DD -10.2 pts, ww -4931 | -1181 $/wk, DD -1.2 pts, ww -36383 | +28 $/wk, DD +0.0 pts, ww +0 |
| london | a | +4077 $/wk, DD +17.0%, ww +902, stops 1.83(2.74), b5 121%, w2l 0 | +2758 $/wk, DD +17.0%, ww +902, stops 2.17(2.89), b5 94%, w2l 0 | +1943 $/wk, DD +17.0%, ww +902, stops 2.03(2.61), b5 102%, w2l 3 | +1151 $/wk, DD +0.0%, ww +0, stops 2.90(3.08), b5 88%, w2l 0 |
| london | b | -3402 $/wk, DD +9.1%, ww +5049, stops 1.90(2.74), b5 59%, w2l 2 | -1796 $/wk, DD +9.1%, ww +5049, stops 2.21(2.89), b5 70%, w2l 2 | -668 $/wk, DD +9.1%, ww +5049, stops 2.19(2.61), b5 82%, w2l 4 | +1458 $/wk, DD +0.0%, ww +0, stops 2.77(3.08), b5 92%, w2l 0 |
| london | c | -2565 $/wk, DD +7.9%, ww +10854, stops 1.75(2.74), b5 63%, w2l 2 | -2283 $/wk, DD -9.4%, ww +10854, stops 2.09(2.89), b5 66%, w2l 3 | -555 $/wk, DD -29.3%, ww +10854, stops 1.99(2.61), b5 81%, w2l 7 | +1060 $/wk, DD +0.0%, ww +0, stops 2.87(3.08), b5 92%, w2l 1 |
| london | **b-a** | -7479 $/wk, DD -7.9 pts, ww +4147 | -4554 $/wk, DD -7.9 pts, ww +4147 | -2611 $/wk, DD -7.9 pts, ww +4147 | +307 $/wk, DD +0.0 pts, ww +0 |
| london | **c-a** | -6642 $/wk, DD -9.1 pts, ww +9952 | -5041 $/wk, DD -26.4 pts, ww +9952 | -2498 $/wk, DD -46.3 pts, ww +9952 | -91 $/wk, DD +0.0 pts, ww +0 |
| nyam | a | -78 $/wk, DD -11.6%, ww -6114, stops 1.75(1.29), b5 88%, w2l 3 | -910 $/wk, DD -45.4%, ww -3527, stops 2.17(1.67), b5 54%, w2l 6 | +461 $/wk, DD +39.4%, ww +2213, stops 2.24(2.15), b5 86%, w2l 10 | +398 $/wk, DD +15.5%, ww +0, stops 2.00(2.00), b5 93%, w2l 1 |
| nyam | b | +452 $/wk, DD +3.4%, ww -6584, stops 1.52(1.29), b5 84%, w2l 2 | -761 $/wk, DD +3.6%, ww -3996, stops 1.94(1.67), b5 52%, w2l 4 | +544 $/wk, DD +62.2%, ww +6242, stops 1.96(2.15), b5 79%, w2l 9 | +204 $/wk, DD +12.8%, ww +0, stops 1.97(2.00), b5 93%, w2l 0 |
| nyam | c | +1515 $/wk, DD +26.6%, ww -1092, stops 1.37(1.29), b5 79%, w2l 0 | -937 $/wk, DD -35.3%, ww +1187, stops 1.75(1.67), b5 33%, w2l 4 | +478 $/wk, DD +38.8%, ww +2798, stops 1.76(2.15), b5 60%, w2l 5 | +87 $/wk, DD +31.9%, ww +0, stops 1.77(2.00), b5 95%, w2l 1 |
| nyam | **b-a** | +530 $/wk, DD +14.9 pts, ww -469 | +148 $/wk, DD +49.0 pts, ww -469 | +84 $/wk, DD +22.7 pts, ww +4028 | -194 $/wk, DD -2.7 pts, ww +0 |
| nyam | **c-a** | +1593 $/wk, DD +38.1 pts, ww +5023 | -27 $/wk, DD +10.1 pts, ww +4714 | +17 $/wk, DD -0.6 pts, ww +584 | -312 $/wk, DD +16.4 pts, ww +0 |
| nypm | a | -61 $/wk, DD -64.8%, ww +822, stops 0.08(0.08), b5 106%, w2l 3 | -608 $/wk, DD -64.8%, ww -1521, stops 0.11(0.08), b5 56%, w2l 6 | -347 $/wk, DD -1.1%, ww +2015, stops 0.10(0.04), b5 56%, w2l 10 | -135 $/wk, DD -16.1%, ww +0, stops 0.05(0.05), b5 90%, w2l 0 |
| nypm | b | -1037 $/wk, DD -160.4%, ww -3994, stops 0.15(0.08), b5 61%, w2l 3 | -969 $/wk, DD -160.4%, ww -3994, stops 0.15(0.08), b5 57%, w2l 4 | -294 $/wk, DD +22.0%, ww +1157, stops 0.10(0.04), b5 57%, w2l 8 | -192 $/wk, DD -27.4%, ww +0, stops 0.05(0.05), b5 90%, w2l 0 |
| nypm | c | -557 $/wk, DD -15.3%, ww -244, stops 0.08(0.08), b5 53%, w2l 2 | -522 $/wk, DD -15.3%, ww -244, stops 0.08(0.08), b5 63%, w2l 4 | +60 $/wk, DD +16.6%, ww +2231, stops 0.04(0.04), b5 63%, w2l 10 | -354 $/wk, DD -15.0%, ww +0, stops 0.05(0.05), b5 61%, w2l 2 |
| nypm | **b-a** | -975 $/wk, DD -95.6 pts, ww -4816 | -361 $/wk, DD -95.6 pts, ww -2473 | +53 $/wk, DD +23.2 pts, ww -857 | -57 $/wk, DD -11.4 pts, ww +0 |
| nypm | **c-a** | -495 $/wk, DD +49.4 pts, ww -1067 | +86 $/wk, DD +49.4 pts, ww +1276 | +406 $/wk, DD +17.7 pts, ww +217 | -219 $/wk, DD +1.0 pts, ww +0 |

**D4II125** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -1553 $/wk, DD -14.5%, ww -5282, stops 10.42(10.35), b5 87%, w2l 0 | -3147 $/wk, DD -14.5%, ww -5282, stops 10.58(10.99), b5 102%, w2l 0 | -2833 $/wk, DD +5.8%, ww +1604, stops 10.18(10.66), b5 86%, w2l 4 | n/a |
| all | b | -3564 $/wk, DD +12.9%, ww +6917, stops 9.97(10.35), b5 77%, w2l 1 | -3144 $/wk, DD +12.9%, ww +6383, stops 10.65(10.99), b5 86%, w2l 1 | -2569 $/wk, DD +5.2%, ww +5599, stops 10.34(10.66), b5 75%, w2l 4 | n/a |
| all | c | -671 $/wk, DD +13.1%, ww +6820, stops 9.89(10.35), b5 92%, w2l 1 | -844 $/wk, DD +13.1%, ww +6820, stops 10.23(10.99), b5 106%, w2l 2 | -1486 $/wk, DD +16.6%, ww +1273, stops 9.82(10.66), b5 98%, w2l 4 | n/a |
| all | **b-a** | -2011 $/wk, DD +27.4 pts, ww +12199 | +2 $/wk, DD +27.4 pts, ww +11665 | +264 $/wk, DD -0.5 pts, ww +3995 | n/a |
| all | **c-a** | +882 $/wk, DD +27.5 pts, ww +12101 | +2303 $/wk, DD +27.5 pts, ww +12101 | +1348 $/wk, DD +10.8 pts, ww -331 | n/a |
| asia | a | -770 $/wk, DD -9.6%, ww -4637, stops 6.54(6.24), b5 102%, w2l 0 | -2321 $/wk, DD -9.6%, ww -4637, stops 6.28(6.35), b5 102%, w2l 0 | -2492 $/wk, DD +6.2%, ww +3154, stops 5.70(5.87), b5 98%, w2l 2 | n/a |
| asia | b | +563 $/wk, DD +6.9%, ww -501, stops 6.24(6.24), b5 99%, w2l 0 | +187 $/wk, DD +6.9%, ww -501, stops 6.32(6.35), b5 101%, w2l 0 | -1074 $/wk, DD +7.3%, ww +103, stops 5.79(5.87), b5 93%, w2l 3 | n/a |
| asia | c | +901 $/wk, DD +2.3%, ww -2781, stops 5.86(6.24), b5 105%, w2l 0 | +26 $/wk, DD +2.3%, ww -2781, stops 5.90(6.35), b5 104%, w2l 0 | -1450 $/wk, DD -8.1%, ww -3298, stops 5.58(5.87), b5 99%, w2l 4 | n/a |
| asia | **b-a** | +1333 $/wk, DD +16.5 pts, ww +4136 | +2508 $/wk, DD +16.5 pts, ww +4136 | +1418 $/wk, DD +1.1 pts, ww -3050 | n/a |
| asia | **c-a** | +1670 $/wk, DD +11.9 pts, ww +1856 | +2347 $/wk, DD +11.9 pts, ww +1856 | +1042 $/wk, DD -14.3 pts, ww -6452 | n/a |
| london | a | -1253 $/wk, DD -1.0%, ww -1913, stops 2.66(2.74), b5 88%, w2l 0 | -413 $/wk, DD -1.0%, ww -1913, stops 2.78(2.89), b5 96%, w2l 0 | -525 $/wk, DD -1.0%, ww -1913, stops 2.45(2.61), b5 96%, w2l 2 | n/a |
| london | b | -2861 $/wk, DD +33.3%, ww -3583, stops 2.36(2.74), b5 58%, w2l 1 | -2130 $/wk, DD +33.3%, ww -3583, stops 2.55(2.89), b5 69%, w2l 1 | -1041 $/wk, DD +0.6%, ww -3583, stops 2.36(2.61), b5 70%, w2l 2 | n/a |
| london | c | -2248 $/wk, DD +20.3%, ww +938, stops 2.66(2.74), b5 79%, w2l 1 | -838 $/wk, DD +20.3%, ww +938, stops 2.70(2.89), b5 88%, w2l 2 | -752 $/wk, DD +7.3%, ww +938, stops 2.44(2.61), b5 77%, w2l 4 | n/a |
| london | **b-a** | -1608 $/wk, DD +34.2 pts, ww -1670 | -1716 $/wk, DD +34.2 pts, ww -1670 | -516 $/wk, DD +1.6 pts, ww -1670 | n/a |
| london | **c-a** | -995 $/wk, DD +21.3 pts, ww +2851 | -425 $/wk, DD +21.3 pts, ww +2851 | -227 $/wk, DD +8.3 pts, ww +2851 | n/a |
| nyam | a | +691 $/wk, DD +15.7%, ww +1483, stops 1.14(1.29), b5 108%, w2l 2 | +26 $/wk, DD +13.7%, ww -245, stops 1.45(1.67), b5 99%, w2l 3 | +106 $/wk, DD +25.7%, ww +1456, stops 1.99(2.15), b5 86%, w2l 5 | n/a |
| nyam | b | -310 $/wk, DD -10.1%, ww -1922, stops 1.29(1.29), b5 100%, w2l 2 | -541 $/wk, DD +2.1%, ww -1739, stops 1.71(1.67), b5 70%, w2l 3 | -174 $/wk, DD +12.2%, ww +3475, stops 2.15(2.15), b5 75%, w2l 4 | n/a |
| nyam | c | +854 $/wk, DD +37.5%, ww +1503, stops 1.29(1.29), b5 94%, w2l 1 | +356 $/wk, DD +3.7%, ww -1440, stops 1.56(1.67), b5 81%, w2l 2 | +974 $/wk, DD +43.2%, ww +7571, stops 1.76(2.15), b5 91%, w2l 4 | n/a |
| nyam | **b-a** | -1001 $/wk, DD -25.8 pts, ww -3405 | -567 $/wk, DD -11.7 pts, ww -1494 | -280 $/wk, DD -13.4 pts, ww +2019 | n/a |
| nyam | **c-a** | +164 $/wk, DD +21.7 pts, ww +20 | +330 $/wk, DD -10.0 pts, ww -1195 | +868 $/wk, DD +17.5 pts, ww +6115 | n/a |
| nypm | a | -221 $/wk, DD -24.0%, ww +376, stops 0.08(0.08), b5 94%, w2l 0 | -438 $/wk, DD -24.0%, ww +376, stops 0.08(0.08), b5 52%, w2l 0 | +77 $/wk, DD +28.8%, ww -415, stops 0.04(0.04), b5 52%, w2l 1 | n/a |
| nypm | b | -956 $/wk, DD -42.2%, ww +97, stops 0.08(0.08), b5 22%, w2l 3 | -660 $/wk, DD -42.2%, ww +97, stops 0.08(0.08), b5 64%, w2l 3 | -280 $/wk, DD +3.1%, ww +2879, stops 0.04(0.04), b5 64%, w2l 8 | n/a |
| nypm | c | -178 $/wk, DD +23.2%, ww +2467, stops 0.08(0.08), b5 78%, w2l 3 | -387 $/wk, DD +23.2%, ww +538, stops 0.08(0.08), b5 78%, w2l 4 | -258 $/wk, DD -6.0%, ww +1585, stops 0.04(0.04), b5 78%, w2l 7 | n/a |
| nypm | **b-a** | -735 $/wk, DD -18.2 pts, ww -279 | -222 $/wk, DD -18.2 pts, ww -279 | -357 $/wk, DD -25.7 pts, ww +3294 | n/a |
| nypm | **c-a** | +43 $/wk, DD +47.2 pts, ww +2090 | +51 $/wk, DD +47.2 pts, ww +162 | -336 $/wk, DD -34.8 pts, ww +2000 | n/a |

**D4III125** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | +910 $/wk, DD +3.0%, ww +726, stops 10.58(10.35), b5 94%, w2l 0 | -2210 $/wk, DD +3.0%, ww +726, stops 10.23(10.99), b5 85%, w2l 0 | -968 $/wk, DD +2.7%, ww -5401, stops 9.80(10.66), b5 91%, w2l 1 | -3059 $/wk, DD +0.0%, ww +0, stops 9.15(9.31), b5 79%, w2l 0 |
| all | b | -4087 $/wk, DD -8.3%, ww -6184, stops 10.50(10.35), b5 78%, w2l 0 | -5438 $/wk, DD -8.3%, ww -6184, stops 10.31(10.99), b5 70%, w2l 0 | -2727 $/wk, DD +14.2%, ww +5792, stops 9.86(10.66), b5 66%, w2l 3 | -1477 $/wk, DD +0.0%, ww +0, stops 9.05(9.31), b5 88%, w2l 0 |
| all | c | +103 $/wk, DD +3.1%, ww +1537, stops 10.04(10.35), b5 97%, w2l 1 | -3613 $/wk, DD +3.1%, ww +1537, stops 10.20(10.99), b5 87%, w2l 1 | -1838 $/wk, DD +15.8%, ww -1134, stops 9.80(10.66), b5 80%, w2l 3 | -2599 $/wk, DD +0.0%, ww +0, stops 9.15(9.31), b5 91%, w2l 1 |
| all | **b-a** | -4997 $/wk, DD -11.3 pts, ww -6911 | -3228 $/wk, DD -11.3 pts, ww -6911 | -1759 $/wk, DD +11.5 pts, ww +11193 | +1582 $/wk, DD +0.0 pts, ww +0 |
| all | **c-a** | -807 $/wk, DD +0.0 pts, ww +810 | -1403 $/wk, DD +0.0 pts, ww +810 | -870 $/wk, DD +13.1 pts, ww +4268 | +460 $/wk, DD +0.0 pts, ww +0 |
| asia | a | -1036 $/wk, DD +8.2%, ww +434, stops 6.24(6.24), b5 94%, w2l 1 | -2318 $/wk, DD +8.2%, ww +434, stops 6.05(6.35), b5 77%, w2l 2 | -2040 $/wk, DD +10.1%, ww +4042, stops 5.52(5.87), b5 78%, w2l 3 | -2480 $/wk, DD -18.5%, ww +0, stops 4.15(4.18), b5 77%, w2l 3 |
| asia | b | -910 $/wk, DD +5.9%, ww +434, stops 6.24(6.24), b5 94%, w2l 1 | -2437 $/wk, DD +5.9%, ww +434, stops 6.01(6.35), b5 78%, w2l 2 | -2504 $/wk, DD +13.8%, ww +1032, stops 5.45(5.87), b5 69%, w2l 3 | -1660 $/wk, DD +0.0%, ww +0, stops 4.10(4.18), b5 82%, w2l 2 |
| asia | c | -277 $/wk, DD +0.4%, ww -2746, stops 6.16(6.24), b5 94%, w2l 0 | -2803 $/wk, DD +0.4%, ww -2746, stops 6.05(6.35), b5 75%, w2l 1 | -2613 $/wk, DD +10.3%, ww -1088, stops 5.58(5.87), b5 71%, w2l 3 | -1563 $/wk, DD +0.0%, ww +0, stops 4.13(4.18), b5 83%, w2l 1 |
| asia | **b-a** | +127 $/wk, DD -2.3 pts, ww +0 | -119 $/wk, DD -2.3 pts, ww +0 | -465 $/wk, DD +3.7 pts, ww -3010 | +821 $/wk, DD +18.5 pts, ww +0 |
| asia | **c-a** | +759 $/wk, DD -7.8 pts, ww -3180 | -486 $/wk, DD -7.8 pts, ww -3180 | -573 $/wk, DD +0.3 pts, ww -5130 | +918 $/wk, DD +18.5 pts, ww +0 |
| london | a | +2101 $/wk, DD +18.3%, ww +8479, stops 2.82(2.74), b5 109%, w2l 0 | +874 $/wk, DD +18.3%, ww +8479, stops 2.55(2.89), b5 96%, w2l 0 | +338 $/wk, DD +18.3%, ww +2594, stops 2.28(2.61), b5 102%, w2l 2 | -181 $/wk, DD +0.0%, ww +0, stops 2.95(3.08), b5 88%, w2l 0 |
| london | b | -1798 $/wk, DD +0.1%, ww +6145, stops 2.66(2.74), b5 73%, w2l 0 | -1687 $/wk, DD +0.1%, ww +6145, stops 2.59(2.89), b5 76%, w2l 0 | -681 $/wk, DD +0.1%, ww +6145, stops 2.38(2.61), b5 87%, w2l 2 | +459 $/wk, DD +0.0%, ww +0, stops 2.90(3.08), b5 92%, w2l 0 |
| london | c | +872 $/wk, DD +6.6%, ww +8170, stops 2.43(2.74), b5 100%, w2l 0 | -26 $/wk, DD +6.6%, ww +8170, stops 2.55(2.89), b5 95%, w2l 0 | +188 $/wk, DD +6.6%, ww -188, stops 2.24(2.61), b5 98%, w2l 1 | -564 $/wk, DD +0.0%, ww +0, stops 3.08(3.08), b5 94%, w2l 1 |
| london | **b-a** | -3899 $/wk, DD -18.3 pts, ww -2334 | -2561 $/wk, DD -18.3 pts, ww -2334 | -1020 $/wk, DD -18.3 pts, ww +3551 | +641 $/wk, DD +0.0 pts, ww +0 |
| london | **c-a** | -1229 $/wk, DD -11.7 pts, ww -309 | -900 $/wk, DD -11.7 pts, ww -309 | -151 $/wk, DD -11.7 pts, ww -2782 | -383 $/wk, DD +0.0 pts, ww +0 |
| nyam | a | +542 $/wk, DD -22.0%, ww -4321, stops 1.45(1.29), b5 99%, w2l 0 | +86 $/wk, DD +4.9%, ww -1734, stops 1.56(1.67), b5 86%, w2l 1 | +787 $/wk, DD +23.1%, ww +2738, stops 1.96(2.15), b5 95%, w2l 4 | -153 $/wk, DD -8.4%, ww +0, stops 2.00(2.00), b5 84%, w2l 0 |
| nyam | b | -292 $/wk, DD -52.4%, ww -6230, stops 1.52(1.29), b5 73%, w2l 1 | -478 $/wk, DD -18.8%, ww -3643, stops 1.64(1.67), b5 65%, w2l 2 | +669 $/wk, DD +47.4%, ww +3785, stops 1.99(2.15), b5 85%, w2l 4 | -16 $/wk, DD +10.2%, ww +0, stops 2.00(2.00), b5 82%, w2l 0 |
| nyam | c | +371 $/wk, DD +2.8%, ww -4321, stops 1.37(1.29), b5 71%, w2l 0 | -220 $/wk, DD -6.9%, ww -1734, stops 1.52(1.67), b5 62%, w2l 1 | +876 $/wk, DD +53.5%, ww +5524, stops 1.94(2.15), b5 80%, w2l 3 | -121 $/wk, DD +10.3%, ww +0, stops 1.90(2.00), b5 80%, w2l 1 |
| nyam | **b-a** | -833 $/wk, DD -30.4 pts, ww -1909 | -564 $/wk, DD -23.7 pts, ww -1909 | -118 $/wk, DD +24.3 pts, ww +1047 | +137 $/wk, DD +18.7 pts, ww +0 |
| nyam | **c-a** | -170 $/wk, DD +24.8 pts, ww +0 | -305 $/wk, DD -11.7 pts, ww +0 | +89 $/wk, DD +30.4 pts, ww +2786 | +32 $/wk, DD +18.7 pts, ww +0 |
| nypm | a | -697 $/wk, DD -87.2%, ww -286, stops 0.08(0.08), b5 92%, w2l 0 | -852 $/wk, DD -87.2%, ww -383, stops 0.08(0.08), b5 62%, w2l 1 | -53 $/wk, DD +43.9%, ww +1630, stops 0.04(0.04), b5 62%, w2l 5 | -244 $/wk, DD -5.4%, ww +0, stops 0.05(0.05), b5 70%, w2l 1 |
| nypm | b | -1088 $/wk, DD -110.2%, ww -1102, stops 0.08(0.08), b5 77%, w2l 1 | -836 $/wk, DD -110.2%, ww -1102, stops 0.08(0.08), b5 81%, w2l 2 | -210 $/wk, DD +34.8%, ww +1820, stops 0.04(0.04), b5 81%, w2l 6 | -261 $/wk, DD -11.5%, ww +0, stops 0.05(0.05), b5 82%, w2l 1 |
| nypm | c | -863 $/wk, DD -38.6%, ww -479, stops 0.08(0.08), b5 42%, w2l 1 | -564 $/wk, DD -38.6%, ww -479, stops 0.08(0.08), b5 60%, w2l 2 | -289 $/wk, DD +0.4%, ww +1585, stops 0.04(0.04), b5 60%, w2l 8 | -351 $/wk, DD -15.4%, ww +0, stops 0.05(0.05), b5 67%, w2l 2 |
| nypm | **b-a** | -391 $/wk, DD -23.0 pts, ww -816 | +17 $/wk, DD -23.0 pts, ww -719 | -157 $/wk, DD -9.1 pts, ww +190 | -17 $/wk, DD -6.1 pts, ww +0 |
| nypm | **c-a** | -166 $/wk, DD +48.6 pts, ww -193 | +288 $/wk, DD +48.6 pts, ww -96 | -236 $/wk, DD -43.5 pts, ww -45 | -106 $/wk, DD -10.0 pts, ww +0 |

### Dial 5 replace atr_rel in live layers (REG half-size, skip) by the forecast ratio (A-cells = live atr_rel reference)

**D5R13F** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -306 $/wk, DD -2.5%, ww +492, stops 10.20(10.35), b5 101%, w2l 1 | -2822 $/wk, DD -2.5%, ww +492, stops 10.77(10.99), b5 87%, w2l 1 | -1740 $/wk, DD +18.4%, ww -2664, stops 10.55(10.66), b5 83%, w2l 1 | -14 $/wk, DD +0.0%, ww +0, stops 9.31(9.31), b5 100%, w2l 0 |
| all | b | -1183 $/wk, DD +16.9%, ww +10345, stops 10.20(10.35), b5 100%, w2l 1 | -1592 $/wk, DD +16.9%, ww +10345, stops 10.80(10.99), b5 93%, w2l 1 | +501 $/wk, DD +12.4%, ww +10865, stops 10.55(10.66), b5 92%, w2l 1 | -508 $/wk, DD +0.0%, ww +0, stops 9.28(9.31), b5 94%, w2l 0 |
| all | c | +713 $/wk, DD +19.7%, ww +10871, stops 10.20(10.35), b5 102%, w2l 0 | -1989 $/wk, DD +19.7%, ww +8672, stops 10.84(10.99), b5 92%, w2l 1 | -381 $/wk, DD +12.4%, ww +18631, stops 10.53(10.66), b5 90%, w2l 1 | -828 $/wk, DD +0.0%, ww +0, stops 9.28(9.31), b5 93%, w2l 0 |
| all | **b-a** | -877 $/wk, DD +19.4 pts, ww +9852 | +1230 $/wk, DD +19.4 pts, ww +9852 | +2242 $/wk, DD -5.9 pts, ww +13529 | -494 $/wk, DD +0.0 pts, ww +0 |
| all | **c-a** | +1018 $/wk, DD +22.2 pts, ww +10378 | +833 $/wk, DD +22.2 pts, ww +8179 | +1360 $/wk, DD -5.9 pts, ww +21295 | -815 $/wk, DD +0.0 pts, ww +0 |
| asia | a | -454 $/wk, DD +7.1%, ww +492, stops 6.16(6.24), b5 94%, w2l 0 | -1549 $/wk, DD +7.1%, ww +492, stops 6.28(6.35), b5 83%, w2l 0 | -593 $/wk, DD +15.3%, ww +0, stops 5.81(5.87), b5 88%, w2l 0 | +0 $/wk, DD +0.0%, ww +0, stops 4.18(4.18), b5 100%, w2l 0 |
| asia | b | -123 $/wk, DD +24.1%, ww +5507, stops 6.24(6.24), b5 92%, w2l 0 | -1449 $/wk, DD +24.1%, ww +5507, stops 6.28(6.35), b5 85%, w2l 0 | +462 $/wk, DD +53.9%, ww +29914, stops 5.79(5.87), b5 92%, w2l 0 | -647 $/wk, DD +0.0%, ww +0, stops 4.18(4.18), b5 92%, w2l 0 |
| asia | c | -283 $/wk, DD +24.1%, ww +6386, stops 6.16(6.24), b5 90%, w2l 0 | -1950 $/wk, DD +24.1%, ww +6386, stops 6.24(6.35), b5 84%, w2l 0 | -180 $/wk, DD +52.5%, ww +29914, stops 5.77(5.87), b5 92%, w2l 0 | -854 $/wk, DD +0.0%, ww +0, stops 4.18(4.18), b5 92%, w2l 0 |
| asia | **b-a** | +331 $/wk, DD +17.0 pts, ww +5014 | +101 $/wk, DD +17.0 pts, ww +5014 | +1054 $/wk, DD +38.6 pts, ww +29914 | -647 $/wk, DD +0.0 pts, ww +0 |
| asia | **c-a** | +172 $/wk, DD +17.0 pts, ww +5894 | -400 $/wk, DD +17.0 pts, ww +5894 | +413 $/wk, DD +37.2 pts, ww +29914 | -854 $/wk, DD +0.0 pts, ww +0 |
| london | a | +226 $/wk, DD +7.1%, ww +0, stops 2.66(2.74), b5 100%, w2l 0 | -486 $/wk, DD +7.1%, ww +0, stops 2.74(2.89), b5 100%, w2l 1 | -521 $/wk, DD +7.1%, ww +0, stops 2.57(2.61), b5 93%, w2l 1 | -14 $/wk, DD +0.0%, ww +0, stops 3.08(3.08), b5 100%, w2l 0 |
| london | b | -419 $/wk, DD +0.0%, ww +0, stops 2.59(2.74), b5 95%, w2l 0 | +14 $/wk, DD +0.0%, ww +0, stops 2.74(2.89), b5 95%, w2l 1 | -351 $/wk, DD +0.0%, ww +0, stops 2.53(2.61), b5 80%, w2l 1 | +17 $/wk, DD +0.0%, ww +0, stops 3.08(3.08), b5 100%, w2l 0 |
| london | c | +373 $/wk, DD +9.1%, ww +0, stops 2.66(2.74), b5 100%, w2l 1 | -375 $/wk, DD +9.1%, ww +0, stops 2.82(2.89), b5 104%, w2l 2 | -587 $/wk, DD +9.1%, ww +0, stops 2.53(2.61), b5 88%, w2l 2 | -77 $/wk, DD +0.0%, ww +0, stops 3.08(3.08), b5 97%, w2l 0 |
| london | **b-a** | -645 $/wk, DD -7.1 pts, ww +0 | +500 $/wk, DD -7.1 pts, ww +0 | +170 $/wk, DD -7.1 pts, ww +0 | +31 $/wk, DD +0.0 pts, ww +0 |
| london | **c-a** | +147 $/wk, DD +2.1 pts, ww +0 | +110 $/wk, DD +2.1 pts, ww +0 | -66 $/wk, DD +2.1 pts, ww +0 | -63 $/wk, DD +0.0 pts, ww +0 |
| nyam | a | -77 $/wk, DD +1.0%, ww +0, stops 1.29(1.29), b5 97%, w2l 0 | -596 $/wk, DD +0.9%, ww +2587, stops 1.67(1.67), b5 91%, w2l 2 | -526 $/wk, DD +0.2%, ww +0, stops 2.13(2.15), b5 86%, w2l 4 | +0 $/wk, DD +0.0%, ww +0, stops 2.00(2.00), b5 100%, w2l 0 |
| nyam | b | -456 $/wk, DD +26.5%, ww +0, stops 1.29(1.29), b5 70%, w2l 1 | +18 $/wk, DD +16.1%, ww +2587, stops 1.71(1.67), b5 82%, w2l 2 | +231 $/wk, DD +1.9%, ww +0, stops 2.19(2.15), b5 91%, w2l 3 | +97 $/wk, DD +5.4%, ww +0, stops 1.97(2.00), b5 100%, w2l 0 |
| nyam | c | +441 $/wk, DD +26.5%, ww +0, stops 1.29(1.29), b5 100%, w2l 0 | +251 $/wk, DD +10.4%, ww +2587, stops 1.71(1.67), b5 99%, w2l 1 | +183 $/wk, DD -0.2%, ww +0, stops 2.19(2.15), b5 89%, w2l 2 | +55 $/wk, DD +7.5%, ww +0, stops 1.97(2.00), b5 100%, w2l 0 |
| nyam | **b-a** | -379 $/wk, DD +25.5 pts, ww +0 | +614 $/wk, DD +15.3 pts, ww +0 | +757 $/wk, DD +1.6 pts, ww +0 | +97 $/wk, DD +5.4 pts, ww +0 |
| nyam | **c-a** | +518 $/wk, DD +25.5 pts, ww +0 | +846 $/wk, DD +9.5 pts, ww +0 | +708 $/wk, DD -0.4 pts, ww +0 | +55 $/wk, DD +7.5 pts, ww +0 |
| nypm | a | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | -191 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 93%, w2l 0 | -101 $/wk, DD -0.9%, ww +2809, stops 0.04(0.04), b5 93%, w2l 1 | +0 $/wk, DD +0.0%, ww +0, stops 0.05(0.05), b5 100%, w2l 0 |
| nypm | b | -184 $/wk, DD -0.0%, ww +0, stops 0.08(0.08), b5 64%, w2l 0 | -176 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 80%, w2l 0 | +160 $/wk, DD +5.0%, ww +2809, stops 0.04(0.04), b5 80%, w2l 0 | +25 $/wk, DD +3.7%, ww +0, stops 0.05(0.05), b5 100%, w2l 0 |
| nypm | c | +182 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | +85 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | +203 $/wk, DD +4.9%, ww +2722, stops 0.04(0.04), b5 100%, w2l 0 | +48 $/wk, DD +7.0%, ww +0, stops 0.05(0.05), b5 100%, w2l 0 |
| nypm | **b-a** | -184 $/wk, DD -0.0 pts, ww +0 | +16 $/wk, DD +0.0 pts, ww +0 | +261 $/wk, DD +5.9 pts, ww +0 | +25 $/wk, DD +3.7 pts, ww +0 |
| nypm | **c-a** | +182 $/wk, DD +0.0 pts, ww +0 | +276 $/wk, DD +0.0 pts, ww +0 | +304 $/wk, DD +5.8 pts, ww -88 | +48 $/wk, DD +7.0 pts, ww +0 |

**D5R115F** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -912 $/wk, DD -1.0%, ww +1267, stops 10.20(10.35), b5 102%, w2l 1 | -3895 $/wk, DD -1.0%, ww +1267, stops 10.73(10.99), b5 86%, w2l 1 | n/a | n/a |
| all | b | -4417 $/wk, DD +14.1%, ww +10636, stops 10.04(10.35), b5 96%, w2l 2 | -5091 $/wk, DD +14.1%, ww +10636, stops 10.73(10.99), b5 89%, w2l 2 | n/a | n/a |
| all | c | -5275 $/wk, DD +14.6%, ww +13161, stops 10.12(10.35), b5 88%, w2l 2 | -5026 $/wk, DD +14.6%, ww +8544, stops 10.80(10.99), b5 88%, w2l 2 | n/a | n/a |
| all | **b-a** | -3505 $/wk, DD +15.2 pts, ww +9369 | -1195 $/wk, DD +15.2 pts, ww +9369 | n/a | n/a |
| all | **c-a** | -4363 $/wk, DD +15.6 pts, ww +11894 | -1131 $/wk, DD +15.6 pts, ww +7277 | n/a | n/a |
| asia | a | -720 $/wk, DD +8.7%, ww +1280, stops 6.16(6.24), b5 90%, w2l 0 | -3006 $/wk, DD +8.7%, ww +1280, stops 6.24(6.35), b5 81%, w2l 1 | n/a | n/a |
| asia | b | -1730 $/wk, DD +20.6%, ww +7005, stops 6.16(6.24), b5 83%, w2l 0 | -3203 $/wk, DD +20.6%, ww +7005, stops 6.24(6.35), b5 80%, w2l 0 | n/a | n/a |
| asia | c | -1829 $/wk, DD +20.6%, ww +7005, stops 6.16(6.24), b5 83%, w2l 0 | -2787 $/wk, DD +20.6%, ww +7005, stops 6.24(6.35), b5 82%, w2l 0 | n/a | n/a |
| asia | **b-a** | -1010 $/wk, DD +11.8 pts, ww +5725 | -197 $/wk, DD +11.8 pts, ww +5725 | n/a | n/a |
| asia | **c-a** | -1109 $/wk, DD +11.8 pts, ww +5725 | +220 $/wk, DD +11.8 pts, ww +5725 | n/a | n/a |
| london | a | -127 $/wk, DD +7.1%, ww +0, stops 2.66(2.74), b5 95%, w2l 0 | -794 $/wk, DD +7.1%, ww +0, stops 2.74(2.89), b5 95%, w2l 1 | n/a | n/a |
| london | b | -1157 $/wk, DD -1.8%, ww -1199, stops 2.59(2.74), b5 84%, w2l 1 | -1138 $/wk, DD -1.8%, ww -1199, stops 2.74(2.89), b5 90%, w2l 2 | n/a | n/a |
| london | c | -1865 $/wk, DD +6.5%, ww -1199, stops 2.59(2.74), b5 77%, w2l 1 | -1190 $/wk, DD +6.5%, ww -1199, stops 2.78(2.89), b5 86%, w2l 2 | n/a | n/a |
| london | **b-a** | -1031 $/wk, DD -8.9 pts, ww -1199 | -344 $/wk, DD -8.9 pts, ww -1199 | n/a | n/a |
| london | **c-a** | -1739 $/wk, DD -0.6 pts, ww -1199 | -396 $/wk, DD -0.6 pts, ww -1199 | n/a | n/a |
| nyam | a | +395 $/wk, DD +8.6%, ww +0, stops 1.29(1.29), b5 97%, w2l 0 | +124 $/wk, DD -2.8%, ww +2587, stops 1.67(1.67), b5 91%, w2l 2 | n/a | n/a |
| nyam | b | -1279 $/wk, DD -22.6%, ww +0, stops 1.22(1.29), b5 60%, w2l 2 | -568 $/wk, DD +4.4%, ww +2587, stops 1.67(1.67), b5 82%, w2l 3 | n/a | n/a |
| nyam | c | -692 $/wk, DD -25.9%, ww +0, stops 1.29(1.29), b5 72%, w2l 1 | -521 $/wk, DD +1.8%, ww +2587, stops 1.71(1.67), b5 84%, w2l 3 | n/a | n/a |
| nyam | **b-a** | -1674 $/wk, DD -31.2 pts, ww +0 | -692 $/wk, DD +7.3 pts, ww +0 | n/a | n/a |
| nyam | **c-a** | -1088 $/wk, DD -34.5 pts, ww +0 | -644 $/wk, DD +4.7 pts, ww +0 | n/a | n/a |
| nypm | a | -460 $/wk, DD -27.2%, ww -286, stops 0.08(0.08), b5 82%, w2l 0 | -219 $/wk, DD -27.2%, ww -286, stops 0.08(0.08), b5 87%, w2l 0 | n/a | n/a |
| nypm | b | -251 $/wk, DD -0.0%, ww +316, stops 0.08(0.08), b5 55%, w2l 0 | -181 $/wk, DD +0.0%, ww +316, stops 0.08(0.08), b5 79%, w2l 0 | n/a | n/a |
| nypm | c | -888 $/wk, DD -48.0%, ww -286, stops 0.08(0.08), b5 39%, w2l 1 | -529 $/wk, DD -48.0%, ww -286, stops 0.08(0.08), b5 81%, w2l 1 | n/a | n/a |
| nypm | **b-a** | +210 $/wk, DD +27.2 pts, ww +602 | +38 $/wk, DD +27.2 pts, ww +602 | n/a | n/a |
| nypm | **c-a** | -427 $/wk, DD -20.8 pts, ww +0 | -310 $/wk, DD -20.8 pts, ww +0 | n/a | n/a |

**D5SK13F** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -764 $/wk, DD -0.2%, ww +43, stops 9.82(10.35), b5 100%, w2l 1 | -6534 $/wk, DD -0.2%, ww +43, stops 8.60(10.99), b5 68%, w2l 2 | -3735 $/wk, DD +0.9%, ww -5482, stops 8.19(10.66), b5 63%, w2l 3 | -24 $/wk, DD +0.0%, ww +0, stops 9.28(9.31), b5 100%, w2l 0 |
| all | b | -1574 $/wk, DD +12.9%, ww +10306, stops 9.21(10.35), b5 100%, w2l 1 | -6332 $/wk, DD +12.9%, ww +10306, stops 7.88(10.99), b5 81%, w2l 3 | -3434 $/wk, DD +32.5%, ww +21358, stops 7.35(10.66), b5 82%, w2l 5 | -1194 $/wk, DD +0.0%, ww +0, stops 9.15(9.31), b5 84%, w2l 0 |
| all | c | -777 $/wk, DD -16.2%, ww +10525, stops 9.05(10.35), b5 101%, w2l 1 | -7797 $/wk, DD -16.2%, ww +10525, stops 7.99(10.99), b5 80%, w2l 3 | -5037 $/wk, DD +32.5%, ww +23651, stops 7.44(10.66), b5 77%, w2l 6 | -2064 $/wk, DD +0.0%, ww +0, stops 9.05(9.31), b5 83%, w2l 1 |
| all | **b-a** | -810 $/wk, DD +13.1 pts, ww +10264 | +203 $/wk, DD +13.1 pts, ww +10264 | +301 $/wk, DD +31.6 pts, ww +26840 | -1170 $/wk, DD +0.0 pts, ww +0 |
| all | **c-a** | -13 $/wk, DD -16.0 pts, ww +10483 | -1262 $/wk, DD -16.0 pts, ww +10483 | -1303 $/wk, DD +31.6 pts, ww +29133 | -2041 $/wk, DD +0.0 pts, ww +0 |
| asia | a | +595 $/wk, DD +39.0%, ww +4539, stops 5.48(6.24), b5 92%, w2l 0 | -4514 $/wk, DD +39.0%, ww +4539, stops 4.30(6.35), b5 60%, w2l 0 | -2834 $/wk, DD +4.3%, ww +0, stops 4.01(5.87), b5 69%, w2l 1 | +0 $/wk, DD +0.0%, ww +0, stops 4.18(4.18), b5 100%, w2l 0 |
| asia | b | +23 $/wk, DD +59.8%, ww +12753, stops 5.02(6.24), b5 79%, w2l 0 | -6394 $/wk, DD +51.0%, ww +12753, stops 3.96(6.35), b5 60%, w2l 3 | -2927 $/wk, DD +69.8%, ww +42160, stops 3.53(5.87), b5 77%, w2l 6 | -1585 $/wk, DD +0.0%, ww +0, stops 4.13(4.18), b5 81%, w2l 0 |
| asia | c | -215 $/wk, DD +59.8%, ww +12753, stops 4.72(6.24), b5 78%, w2l 0 | -6292 $/wk, DD +54.6%, ww +12753, stops 3.92(6.35), b5 60%, w2l 2 | -3206 $/wk, DD +55.0%, ww +37248, stops 3.57(5.87), b5 77%, w2l 5 | -2178 $/wk, DD +0.0%, ww +0, stops 4.10(4.18), b5 81%, w2l 0 |
| asia | **b-a** | -572 $/wk, DD +20.8 pts, ww +8214 | -1880 $/wk, DD +12.0 pts, ww +8214 | -93 $/wk, DD +65.5 pts, ww +42160 | -1585 $/wk, DD +0.0 pts, ww +0 |
| asia | **c-a** | -810 $/wk, DD +20.8 pts, ww +8214 | -1778 $/wk, DD +15.6 pts, ww +8214 | -372 $/wk, DD +50.6 pts, ww +37248 | -2178 $/wk, DD +0.0 pts, ww +0 |
| london | a | +295 $/wk, DD +9.8%, ww +0, stops 2.89(2.74), b5 99%, w2l 0 | +284 $/wk, DD +9.8%, ww +0, stops 2.82(2.89), b5 90%, w2l 0 | +600 $/wk, DD +9.8%, ww +0, stops 2.36(2.61), b5 95%, w2l 0 | -42 $/wk, DD +0.0%, ww +0, stops 3.08(3.08), b5 100%, w2l 0 |
| london | b | -883 $/wk, DD +0.0%, ww +0, stops 2.66(2.74), b5 91%, w2l 0 | +1432 $/wk, DD -0.0%, ww +0, stops 2.43(2.89), b5 91%, w2l 1 | +63 $/wk, DD +0.0%, ww +0, stops 2.01(2.61), b5 65%, w2l 2 | -72 $/wk, DD +0.0%, ww +0, stops 3.08(3.08), b5 92%, w2l 0 |
| london | c | -325 $/wk, DD +9.8%, ww +0, stops 2.66(2.74), b5 103%, w2l 1 | -459 $/wk, DD +9.8%, ww +0, stops 2.59(2.89), b5 109%, w2l 2 | -1358 $/wk, DD +9.8%, ww +0, stops 2.21(2.61), b5 80%, w2l 4 | -335 $/wk, DD +0.0%, ww +0, stops 3.00(3.08), b5 88%, w2l 0 |
| london | **b-a** | -1178 $/wk, DD -9.8 pts, ww +0 | +1148 $/wk, DD -9.8 pts, ww +0 | -538 $/wk, DD -9.8 pts, ww +0 | -29 $/wk, DD +0.0 pts, ww +0 |
| london | **c-a** | -621 $/wk, DD -0.0 pts, ww +0 | -743 $/wk, DD -0.0 pts, ww +0 | -1959 $/wk, DD -0.0 pts, ww +0 | -293 $/wk, DD +0.0 pts, ww +0 |
| nyam | a | -1463 $/wk, DD -27.0%, ww +0, stops 1.37(1.29), b5 62%, w2l 2 | -1317 $/wk, DD -39.8%, ww +2042, stops 1.41(1.67), b5 61%, w2l 3 | -1278 $/wk, DD +3.2%, ww -4600, stops 1.76(2.15), b5 39%, w2l 5 | -6 $/wk, DD -0.0%, ww +0, stops 1.97(2.00), b5 102%, w2l 0 |
| nyam | b | -388 $/wk, DD +30.8%, ww +0, stops 1.45(1.29), b5 72%, w2l 1 | -587 $/wk, DD +19.4%, ww +2587, stops 1.41(1.67), b5 57%, w2l 3 | -613 $/wk, DD +24.7%, ww +0, stops 1.76(2.15), b5 39%, w2l 6 | +325 $/wk, DD +21.4%, ww +0, stops 1.90(2.00), b5 102%, w2l 0 |
| nyam | c | +147 $/wk, DD +23.7%, ww -642, stops 1.52(1.29), b5 96%, w2l 1 | -349 $/wk, DD +10.1%, ww +1945, stops 1.37(1.67), b5 78%, w2l 3 | -421 $/wk, DD +27.3%, ww +0, stops 1.59(2.15), b5 42%, w2l 6 | +245 $/wk, DD +21.4%, ww +0, stops 1.90(2.00), b5 102%, w2l 0 |
| nyam | **b-a** | +1075 $/wk, DD +57.8 pts, ww +0 | +730 $/wk, DD +59.1 pts, ww +546 | +665 $/wk, DD +21.4 pts, ww +4600 | +331 $/wk, DD +21.4 pts, ww +0 |
| nyam | **c-a** | +1610 $/wk, DD +50.8 pts, ww -642 | +968 $/wk, DD +49.9 pts, ww -97 | +856 $/wk, DD +24.0 pts, ww +4600 | +251 $/wk, DD +21.4 pts, ww +0 |
| nypm | a | -191 $/wk, DD -28.6%, ww +0, stops 0.08(0.08), b5 98%, w2l 0 | -988 $/wk, DD -28.6%, ww +0, stops 0.08(0.08), b5 57%, w2l 2 | -223 $/wk, DD +36.9%, ww +1806, stops 0.06(0.04), b5 57%, w2l 3 | +24 $/wk, DD +3.6%, ww +0, stops 0.05(0.05), b5 100%, w2l 0 |
| nypm | b | -326 $/wk, DD -0.0%, ww +0, stops 0.08(0.08), b5 67%, w2l 0 | -783 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 44%, w2l 2 | +43 $/wk, DD +49.4%, ww +4154, stops 0.04(0.04), b5 44%, w2l 2 | +138 $/wk, DD +11.0%, ww +0, stops 0.05(0.05), b5 100%, w2l 0 |
| nypm | c | -384 $/wk, DD -28.6%, ww +0, stops 0.15(0.08), b5 95%, w2l 0 | -697 $/wk, DD -28.6%, ww -547, stops 0.11(0.08), b5 74%, w2l 3 | -52 $/wk, DD +10.1%, ww +648, stops 0.08(0.04), b5 74%, w2l 4 | +204 $/wk, DD +20.4%, ww +0, stops 0.05(0.05), b5 100%, w2l 0 |
| nypm | **b-a** | -135 $/wk, DD +28.6 pts, ww +0 | +205 $/wk, DD +28.6 pts, ww +0 | +266 $/wk, DD +12.5 pts, ww +2348 | +113 $/wk, DD +7.3 pts, ww +0 |
| nypm | **c-a** | -193 $/wk, DD +0.0 pts, ww +0 | +291 $/wk, DD +0.0 pts, ww -547 | +172 $/wk, DD -26.8 pts, ww -1158 | +179 $/wk, DD +16.8 pts, ww +0 |

**D5LO8F** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -816 $/wk, DD +0.0%, ww +0, stops 10.27(10.35), b5 98%, w2l 0 | -427 $/wk, DD +0.0%, ww +0, stops 10.96(10.99), b5 100%, w2l 0 | -913 $/wk, DD +4.6%, ww +0, stops 10.64(10.66), b5 96%, w2l 0 | n/a |
| all | b | -634 $/wk, DD +7.1%, ww +3713, stops 10.12(10.35), b5 92%, w2l 0 | -754 $/wk, DD +7.1%, ww +3713, stops 10.88(10.99), b5 99%, w2l 0 | -1747 $/wk, DD -3.8%, ww +0, stops 10.61(10.66), b5 90%, w2l 2 | n/a |
| all | c | -862 $/wk, DD +7.1%, ww +3713, stops 10.20(10.35), b5 99%, w2l 0 | -360 $/wk, DD +7.1%, ww +3713, stops 10.84(10.99), b5 102%, w2l 0 | -1246 $/wk, DD +9.2%, ww +0, stops 10.61(10.66), b5 92%, w2l 1 | n/a |
| all | **b-a** | +182 $/wk, DD +7.1 pts, ww +3713 | -327 $/wk, DD +7.1 pts, ww +3713 | -835 $/wk, DD -8.3 pts, ww +0 | n/a |
| all | **c-a** | -46 $/wk, DD +7.1 pts, ww +3713 | +67 $/wk, DD +7.1 pts, ww +3713 | -334 $/wk, DD +4.6 pts, ww +0 | n/a |
| asia | a | +48 $/wk, DD +0.0%, ww +0, stops 6.16(6.24), b5 100%, w2l 0 | -194 $/wk, DD +0.0%, ww +0, stops 6.32(6.35), b5 100%, w2l 0 | -608 $/wk, DD -0.0%, ww +0, stops 5.85(5.87), b5 100%, w2l 0 | n/a |
| asia | b | +922 $/wk, DD +7.7%, ww +434, stops 6.09(6.24), b5 94%, w2l 0 | -71 $/wk, DD +7.7%, ww +434, stops 6.28(6.35), b5 97%, w2l 0 | -747 $/wk, DD +2.2%, ww +0, stops 5.79(5.87), b5 94%, w2l 0 | n/a |
| asia | c | +99 $/wk, DD +7.7%, ww +434, stops 6.16(6.24), b5 94%, w2l 0 | -65 $/wk, DD +7.7%, ww +434, stops 6.28(6.35), b5 97%, w2l 0 | -645 $/wk, DD +2.2%, ww +0, stops 5.79(5.87), b5 93%, w2l 0 | n/a |
| asia | **b-a** | +873 $/wk, DD +7.7 pts, ww +434 | +123 $/wk, DD +7.7 pts, ww +434 | -139 $/wk, DD +2.2 pts, ww +0 | n/a |
| asia | **c-a** | +50 $/wk, DD +7.7 pts, ww +434 | +129 $/wk, DD +7.7 pts, ww +434 | -37 $/wk, DD +2.2 pts, ww +0 | n/a |
| london | a | -167 $/wk, DD -1.2%, ww +0, stops 2.74(2.74), b5 100%, w2l 0 | +79 $/wk, DD -1.2%, ww +0, stops 2.89(2.89), b5 100%, w2l 0 | -136 $/wk, DD -1.2%, ww +0, stops 2.61(2.61), b5 100%, w2l 0 | n/a |
| london | b | -626 $/wk, DD +21.9%, ww +950, stops 2.66(2.74), b5 90%, w2l 0 | -151 $/wk, DD +21.9%, ww +950, stops 2.85(2.89), b5 95%, w2l 0 | -549 $/wk, DD -12.3%, ww +950, stops 2.61(2.61), b5 95%, w2l 2 | n/a |
| london | c | +155 $/wk, DD +9.6%, ww +0, stops 2.66(2.74), b5 102%, w2l 0 | +227 $/wk, DD +9.6%, ww +0, stops 2.82(2.89), b5 109%, w2l 0 | -387 $/wk, DD +3.6%, ww +0, stops 2.61(2.61), b5 106%, w2l 2 | n/a |
| london | **b-a** | -459 $/wk, DD +23.0 pts, ww +950 | -230 $/wk, DD +23.0 pts, ww +950 | -414 $/wk, DD -11.1 pts, ww +950 | n/a |
| london | **c-a** | +322 $/wk, DD +10.8 pts, ww +0 | +147 $/wk, DD +10.8 pts, ww +0 | -252 $/wk, DD +4.7 pts, ww +0 | n/a |
| nyam | a | -611 $/wk, DD -4.9%, ww -2951, stops 1.29(1.29), b5 94%, w2l 0 | -270 $/wk, DD +0.0%, ww -364, stops 1.67(1.67), b5 101%, w2l 0 | -165 $/wk, DD +5.0%, ww +2087, stops 2.15(2.15), b5 93%, w2l 0 | n/a |
| nyam | b | -627 $/wk, DD -18.9%, ww -413, stops 1.29(1.29), b5 89%, w2l 2 | -286 $/wk, DD +0.0%, ww +0, stops 1.67(1.67), b5 102%, w2l 2 | -321 $/wk, DD +0.2%, ww +647, stops 2.17(2.15), b5 92%, w2l 3 | n/a |
| nyam | c | -713 $/wk, DD -33.8%, ww -413, stops 1.29(1.29), b5 87%, w2l 2 | -294 $/wk, DD -4.4%, ww +0, stops 1.67(1.67), b5 99%, w2l 2 | -189 $/wk, DD +11.4%, ww +2721, stops 2.17(2.15), b5 92%, w2l 2 | n/a |
| nyam | **b-a** | -16 $/wk, DD -14.1 pts, ww +2538 | -16 $/wk, DD +0.0 pts, ww +364 | -156 $/wk, DD -4.8 pts, ww -1439 | n/a |
| nyam | **c-a** | -102 $/wk, DD -28.9 pts, ww +2538 | -24 $/wk, DD -4.4 pts, ww +364 | -24 $/wk, DD +6.4 pts, ww +635 | n/a |
| nypm | a | -86 $/wk, DD -0.0%, ww +0, stops 0.08(0.08), b5 89%, w2l 2 | -43 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 2 | -4 $/wk, DD -2.6%, ww +0, stops 0.04(0.04), b5 100%, w2l 3 | n/a |
| nypm | b | -302 $/wk, DD -0.0%, ww +0, stops 0.08(0.08), b5 72%, w2l 2 | -246 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 93%, w2l 2 | -130 $/wk, DD -1.0%, ww +0, stops 0.04(0.04), b5 93%, w2l 2 | n/a |
| nypm | c | -402 $/wk, DD +1.5%, ww +0, stops 0.08(0.08), b5 62%, w2l 0 | -228 $/wk, DD +1.5%, ww +0, stops 0.08(0.08), b5 86%, w2l 0 | -24 $/wk, DD +13.4%, ww +0, stops 0.04(0.04), b5 86%, w2l 0 | n/a |
| nypm | **b-a** | -216 $/wk, DD +0.0 pts, ww +0 | -203 $/wk, DD +0.0 pts, ww +0 | -126 $/wk, DD +1.6 pts, ww +0 | n/a |
| nypm | **c-a** | -317 $/wk, DD +1.5 pts, ww +0 | -185 $/wk, DD +1.5 pts, ww +0 | -21 $/wk, DD +16.1 pts, ww +0 | n/a |

**D5R13A** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | x | -509 $/wk, DD +14.4%, ww +10121, stops 10.35(10.35), b5 101%, w2l 0 | -739 $/wk, DD +14.4%, ww +10121, stops 10.92(10.99), b5 96%, w2l 0 | -447 $/wk, DD +10.4%, ww +3298, stops 10.59(10.66), b5 87%, w2l 1 | -410 $/wk, DD +11.0%, ww +2521, stops 9.28(9.31), b5 91%, w2l 0 |
| asia | x | +439 $/wk, DD +11.4%, ww +1681, stops 6.16(6.24), b5 105%, w2l 0 | +577 $/wk, DD +11.4%, ww +1681, stops 6.20(6.35), b5 98%, w2l 0 | -754 $/wk, DD +0.7%, ww -815, stops 5.75(5.87), b5 93%, w2l 0 | -282 $/wk, DD +30.1%, ww +2331, stops 4.13(4.18), b5 93%, w2l 0 |
| london | x | -924 $/wk, DD +0.9%, ww +0, stops 2.82(2.74), b5 96%, w2l 0 | -670 $/wk, DD +0.9%, ww +0, stops 2.93(2.89), b5 95%, w2l 0 | -226 $/wk, DD +0.9%, ww +0, stops 2.61(2.61), b5 102%, w2l 0 | -565 $/wk, DD +12.4%, ww -3077, stops 3.15(3.08), b5 87%, w2l 1 |
| nyam | x | +132 $/wk, DD +15.5%, ww +1902, stops 1.29(1.29), b5 82%, w2l 2 | -325 $/wk, DD -11.4%, ww +4156, stops 1.71(1.67), b5 92%, w2l 5 | +184 $/wk, DD +25.9%, ww +1282, stops 2.19(2.15), b5 84%, w2l 6 | +827 $/wk, DD +18.5%, ww +2005, stops 1.92(2.00), b5 86%, w2l 2 |
| nypm | x | -155 $/wk, DD -7.6%, ww +0, stops 0.08(0.08), b5 89%, w2l 0 | -322 $/wk, DD -7.6%, ww +0, stops 0.08(0.08), b5 75%, w2l 1 | +348 $/wk, DD +29.7%, ww +1224, stops 0.04(0.04), b5 75%, w2l 1 | -390 $/wk, DD -32.3%, ww -291, stops 0.08(0.05), b5 56%, w2l 4 |

**D5SK15A** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | x | +1476 $/wk, DD +21.5%, ww +6238, stops 9.05(10.35), b5 106%, w2l 0 | -2231 $/wk, DD +21.5%, ww +6238, stops 8.79(10.99), b5 88%, w2l 0 | -438 $/wk, DD +14.9%, ww +9570, stops 7.77(10.66), b5 84%, w2l 1 | -2224 $/wk, DD -15.7%, ww -1574, stops 6.82(9.31), b5 64%, w2l 3 |
| asia | x | +2093 $/wk, DD +45.6%, ww +11057, stops 5.93(6.24), b5 100%, w2l 0 | +1033 $/wk, DD +45.6%, ww +9851, stops 5.48(6.35), b5 92%, w2l 0 | +224 $/wk, DD +22.4%, ww +16638, stops 4.95(5.87), b5 87%, w2l 1 | -903 $/wk, DD +21.8%, ww +6046, stops 3.46(4.18), b5 96%, w2l 3 |
| london | x | -1594 $/wk, DD +0.0%, ww +0, stops 2.82(2.74), b5 95%, w2l 0 | -1143 $/wk, DD +0.0%, ww +0, stops 2.78(2.89), b5 96%, w2l 0 | -714 $/wk, DD +0.0%, ww +0, stops 2.45(2.61), b5 102%, w2l 3 | -645 $/wk, DD +16.2%, ww -4093, stops 2.77(3.08), b5 69%, w2l 1 |
| nyam | x | +1141 $/wk, DD +56.6%, ww +4530, stops 0.30(1.29), b5 74%, w2l 2 | -984 $/wk, DD +51.4%, ww +7118, stops 0.53(1.67), b5 29%, w2l 5 | +114 $/wk, DD +82.9%, ww +19346, stops 0.36(2.15), b5 31%, w2l 10 | -643 $/wk, DD +37.1%, ww +2838, stops 0.59(2.00), b5 21%, w2l 4 |
| nypm | x | -164 $/wk, DD +37.4%, ww +1185, stops 0.00(0.08), b5 109%, w2l 3 | -1138 $/wk, DD +37.4%, ww +1185, stops 0.00(0.08), b5 27%, w2l 5 | -62 $/wk, DD +55.7%, ww +3653, stops 0.00(0.04), b5 27%, w2l 8 | -33 $/wk, DD +41.4%, ww +3687, stops 0.00(0.05), b5 4%, w2l 6 |

### Dial 6 entry distance (split-add dip MINDIP)

**D6T** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | +810 $/wk, DD -6.0%, ww -3395, stops 10.58(10.35), b5 100%, w2l 0 | +68 $/wk, DD -6.0%, ww -3395, stops 11.15(10.99), b5 102%, w2l 0 | +163 $/wk, DD -3.1%, ww -8559, stops 10.66(10.66), b5 102%, w2l 1 | n/a |
| all | b | +1059 $/wk, DD -10.8%, ww -5916, stops 10.65(10.35), b5 97%, w2l 0 | -276 $/wk, DD -10.8%, ww -5916, stops 11.18(10.99), b5 99%, w2l 0 | +68 $/wk, DD -11.7%, ww -3648, stops 10.72(10.66), b5 99%, w2l 1 | n/a |
| all | c | +1288 $/wk, DD -4.9%, ww -2798, stops 10.58(10.35), b5 96%, w2l 0 | -246 $/wk, DD -4.9%, ww -2798, stops 11.15(10.99), b5 99%, w2l 0 | +298 $/wk, DD -10.2%, ww -3648, stops 10.68(10.66), b5 98%, w2l 1 | n/a |
| all | **b-a** | +249 $/wk, DD -4.8 pts, ww -2521 | -344 $/wk, DD -4.8 pts, ww -2521 | -95 $/wk, DD -8.6 pts, ww +4911 | n/a |
| all | **c-a** | +478 $/wk, DD +1.2 pts, ww +597 | -314 $/wk, DD +1.2 pts, ww +597 | +135 $/wk, DD -7.1 pts, ww +4911 | n/a |
| asia | a | +882 $/wk, DD -14.5%, ww -7268, stops 6.24(6.24), b5 108%, w2l 1 | +21 $/wk, DD -14.5%, ww -7268, stops 6.43(6.35), b5 108%, w2l 1 | +495 $/wk, DD +0.2%, ww +1052, stops 5.89(5.87), b5 102%, w2l 2 | n/a |
| asia | b | +1146 $/wk, DD -11.8%, ww -5936, stops 6.24(6.24), b5 107%, w2l 0 | -194 $/wk, DD -11.8%, ww -5936, stops 6.39(6.35), b5 105%, w2l 0 | +331 $/wk, DD +3.0%, ww +4844, stops 5.87(5.87), b5 97%, w2l 0 | n/a |
| asia | c | +1488 $/wk, DD -13.2%, ww -6646, stops 6.24(6.24), b5 107%, w2l 0 | -92 $/wk, DD -13.2%, ww -6646, stops 6.39(6.35), b5 105%, w2l 0 | +475 $/wk, DD +4.0%, ww +4844, stops 5.87(5.87), b5 97%, w2l 0 | n/a |
| asia | **b-a** | +265 $/wk, DD +2.8 pts, ww +1332 | -215 $/wk, DD +2.8 pts, ww +1332 | -164 $/wk, DD +2.8 pts, ww +3793 | n/a |
| asia | **c-a** | +606 $/wk, DD +1.3 pts, ww +622 | -113 $/wk, DD +1.3 pts, ww +622 | -20 $/wk, DD +3.8 pts, ww +3793 | n/a |
| london | a | +266 $/wk, DD +6.1%, ww +95, stops 2.89(2.74), b5 99%, w2l 0 | +753 $/wk, DD +6.1%, ww +95, stops 2.93(2.89), b5 99%, w2l 0 | -203 $/wk, DD +6.1%, ww +95, stops 2.63(2.61), b5 89%, w2l 2 | n/a |
| london | b | -60 $/wk, DD +7.5%, ww +1482, stops 2.97(2.74), b5 96%, w2l 0 | +473 $/wk, DD +7.5%, ww +1482, stops 3.01(2.89), b5 100%, w2l 0 | -171 $/wk, DD +7.5%, ww +1482, stops 2.68(2.61), b5 90%, w2l 1 | n/a |
| london | c | -177 $/wk, DD -0.2%, ww +0, stops 2.89(2.74), b5 96%, w2l 0 | +436 $/wk, DD -0.2%, ww +0, stops 2.97(2.89), b5 99%, w2l 0 | -58 $/wk, DD -0.2%, ww +0, stops 2.65(2.61), b5 89%, w2l 1 | n/a |
| london | **b-a** | -326 $/wk, DD +1.4 pts, ww +1387 | -280 $/wk, DD +1.4 pts, ww +1387 | +32 $/wk, DD +1.4 pts, ww +1387 | n/a |
| london | **c-a** | -443 $/wk, DD -6.3 pts, ww -95 | -317 $/wk, DD -6.3 pts, ww -95 | +145 $/wk, DD -6.3 pts, ww -95 | n/a |
| nyam | a | +4 $/wk, DD -10.2%, ww -160, stops 1.37(1.29), b5 98%, w2l 0 | -437 $/wk, DD -0.7%, ww +690, stops 1.71(1.67), b5 99%, w2l 1 | -156 $/wk, DD +7.1%, ww -10, stops 2.11(2.15), b5 84%, w2l 3 | n/a |
| nyam | b | +25 $/wk, DD +12.2%, ww -160, stops 1.37(1.29), b5 96%, w2l 0 | -430 $/wk, DD +0.6%, ww +690, stops 1.71(1.67), b5 98%, w2l 1 | -192 $/wk, DD +5.4%, ww -65, stops 2.13(2.15), b5 85%, w2l 3 | n/a |
| nyam | c | +306 $/wk, DD +12.3%, ww -5, stops 1.37(1.29), b5 96%, w2l 0 | -267 $/wk, DD -1.5%, ww +730, stops 1.71(1.67), b5 98%, w2l 1 | -124 $/wk, DD +5.9%, ww -10, stops 2.13(2.15), b5 85%, w2l 3 | n/a |
| nyam | **b-a** | +21 $/wk, DD +22.4 pts, ww +0 | +6 $/wk, DD +1.3 pts, ww +0 | -36 $/wk, DD -1.7 pts, ww -55 | n/a |
| nyam | **c-a** | +302 $/wk, DD +22.6 pts, ww +155 | +170 $/wk, DD -0.8 pts, ww +40 | +31 $/wk, DD -1.3 pts, ww +0 | n/a |
| nypm | a | -342 $/wk, DD -39.9%, ww -286, stops 0.08(0.08), b5 100%, w2l 0 | -270 $/wk, DD -39.9%, ww -286, stops 0.08(0.08), b5 100%, w2l 1 | +27 $/wk, DD +5.2%, ww +2706, stops 0.04(0.04), b5 100%, w2l 1 | n/a |
| nypm | b | -52 $/wk, DD +2.5%, ww +0, stops 0.08(0.08), b5 101%, w2l 0 | -125 $/wk, DD +2.5%, ww +0, stops 0.08(0.08), b5 100%, w2l 1 | +100 $/wk, DD +5.2%, ww +2706, stops 0.04(0.04), b5 100%, w2l 1 | n/a |
| nypm | c | -329 $/wk, DD -37.4%, ww -286, stops 0.08(0.08), b5 101%, w2l 0 | -323 $/wk, DD -37.4%, ww -286, stops 0.08(0.08), b5 96%, w2l 1 | +5 $/wk, DD +5.2%, ww +2706, stops 0.04(0.04), b5 96%, w2l 1 | n/a |
| nypm | **b-a** | +290 $/wk, DD +42.3 pts, ww +286 | +145 $/wk, DD +42.3 pts, ww +286 | +73 $/wk, DD +0.0 pts, ww +0 | n/a |
| nypm | **c-a** | +13 $/wk, DD +2.5 pts, ww +0 | -53 $/wk, DD +2.5 pts, ww +0 | -21 $/wk, DD +0.0 pts, ww +0 | n/a |

**D6C** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | +126 $/wk, DD -13.3%, ww -7179, stops 10.58(10.35), b5 103%, w2l 0 | -801 $/wk, DD -13.3%, ww -7179, stops 11.18(10.99), b5 101%, w2l 0 | -400 $/wk, DD -3.1%, ww +1529, stops 10.74(10.66), b5 101%, w2l 1 | +149 $/wk, DD +0.0%, ww +0, stops 9.28(9.31), b5 100%, w2l 0 |
| all | b | +561 $/wk, DD -4.2%, ww -2435, stops 10.58(10.35), b5 93%, w2l 0 | -250 $/wk, DD -4.2%, ww -2435, stops 11.18(10.99), b5 99%, w2l 0 | +43 $/wk, DD -2.1%, ww -3648, stops 10.72(10.66), b5 99%, w2l 1 | +103 $/wk, DD +0.0%, ww +0, stops 9.28(9.31), b5 98%, w2l 0 |
| all | c | +1041 $/wk, DD -4.6%, ww -2655, stops 10.50(10.35), b5 95%, w2l 0 | -75 $/wk, DD -4.6%, ww -2655, stops 11.07(10.99), b5 98%, w2l 0 | -187 $/wk, DD -10.6%, ww -10743, stops 10.66(10.66), b5 99%, w2l 1 | +120 $/wk, DD +0.0%, ww +0, stops 9.28(9.31), b5 97%, w2l 0 |
| all | **b-a** | +434 $/wk, DD +9.1 pts, ww +4743 | +551 $/wk, DD +9.1 pts, ww +4743 | +442 $/wk, DD +1.1 pts, ww -5178 | -45 $/wk, DD +0.0 pts, ww +0 |
| all | **c-a** | +915 $/wk, DD +8.7 pts, ww +4523 | +726 $/wk, DD +8.7 pts, ww +4523 | +213 $/wk, DD -7.5 pts, ww -12272 | -29 $/wk, DD +0.0 pts, ww +0 |
| asia | a | -118 $/wk, DD -22.3%, ww -11052, stops 6.24(6.24), b5 107%, w2l 1 | -1097 $/wk, DD -22.3%, ww -11052, stops 6.43(6.35), b5 102%, w2l 1 | -286 $/wk, DD +1.1%, ww +2117, stops 5.89(5.87), b5 99%, w2l 1 | -2 $/wk, DD +0.0%, ww +0, stops 4.15(4.18), b5 101%, w2l 1 |
| asia | b | +503 $/wk, DD -12.2%, ww -6168, stops 6.24(6.24), b5 100%, w2l 0 | -467 $/wk, DD -12.2%, ww -6168, stops 6.39(6.35), b5 100%, w2l 0 | +218 $/wk, DD +3.1%, ww +4844, stops 5.87(5.87), b5 95%, w2l 0 | +98 $/wk, DD +0.0%, ww +0, stops 4.15(4.18), b5 98%, w2l 1 |
| asia | c | +1046 $/wk, DD -12.9%, ww -6488, stops 6.24(6.24), b5 105%, w2l 0 | -441 $/wk, DD -12.9%, ww -6488, stops 6.39(6.35), b5 104%, w2l 0 | +48 $/wk, DD -4.1%, ww -2394, stops 5.87(5.87), b5 95%, w2l 0 | +42 $/wk, DD +0.0%, ww +0, stops 4.15(4.18), b5 98%, w2l 1 |
| asia | **b-a** | +621 $/wk, DD +10.1 pts, ww +4883 | +630 $/wk, DD +10.1 pts, ww +4883 | +504 $/wk, DD +2.0 pts, ww +2727 | +100 $/wk, DD +0.0 pts, ww +0 |
| asia | **c-a** | +1164 $/wk, DD +9.4 pts, ww +4563 | +657 $/wk, DD +9.4 pts, ww +4563 | +334 $/wk, DD -5.2 pts, ww -4511 | +44 $/wk, DD +0.0 pts, ww +0 |
| london | a | +112 $/wk, DD -0.2%, ww +5, stops 2.89(2.74), b5 100%, w2l 0 | +1074 $/wk, DD -0.2%, ww +5, stops 2.93(2.89), b5 100%, w2l 0 | +214 $/wk, DD -0.2%, ww +5, stops 2.65(2.61), b5 91%, w2l 0 | +50 $/wk, DD +0.0%, ww +0, stops 3.08(3.08), b5 98%, w2l 0 |
| london | b | +158 $/wk, DD +10.9%, ww +1532, stops 2.89(2.74), b5 97%, w2l 0 | +930 $/wk, DD +10.9%, ww +1532, stops 2.97(2.89), b5 100%, w2l 0 | -13 $/wk, DD +10.9%, ww +1532, stops 2.67(2.61), b5 90%, w2l 1 | -72 $/wk, DD +0.0%, ww +0, stops 3.08(3.08), b5 98%, w2l 0 |
| london | c | -294 $/wk, DD -6.0%, ww +1424, stops 2.89(2.74), b5 96%, w2l 0 | +690 $/wk, DD -6.0%, ww +1424, stops 2.93(2.89), b5 99%, w2l 0 | -185 $/wk, DD -6.0%, ww +1424, stops 2.65(2.61), b5 89%, w2l 1 | -32 $/wk, DD +0.0%, ww +0, stops 3.08(3.08), b5 98%, w2l 0 |
| london | **b-a** | +46 $/wk, DD +11.1 pts, ww +1527 | -144 $/wk, DD +11.1 pts, ww +1527 | -228 $/wk, DD +11.1 pts, ww +1527 | -122 $/wk, DD +0.0 pts, ww +0 |
| london | **c-a** | -406 $/wk, DD -5.8 pts, ww +1419 | -384 $/wk, DD -5.8 pts, ww +1419 | -400 $/wk, DD -5.8 pts, ww +1419 | -81 $/wk, DD +0.0 pts, ww +0 |
| nyam | a | +448 $/wk, DD -14.0%, ww -711, stops 1.37(1.29), b5 116%, w2l 0 | -603 $/wk, DD -23.0%, ww +541, stops 1.75(1.67), b5 99%, w2l 1 | -398 $/wk, DD +7.4%, ww +30, stops 2.17(2.15), b5 85%, w2l 4 | +127 $/wk, DD -4.6%, ww +0, stops 2.00(2.00), b5 100%, w2l 0 |
| nyam | b | +222 $/wk, DD +10.3%, ww -663, stops 1.37(1.29), b5 95%, w2l 0 | -390 $/wk, DD -25.5%, ww +541, stops 1.75(1.67), b5 105%, w2l 1 | -162 $/wk, DD +6.7%, ww -65, stops 2.15(2.15), b5 90%, w2l 4 | +125 $/wk, DD -4.7%, ww +0, stops 2.00(2.00), b5 100%, w2l 0 |
| nyam | c | +640 $/wk, DD +17.6%, ww -663, stops 1.29(1.29), b5 96%, w2l 0 | -70 $/wk, DD +2.0%, ww +710, stops 1.67(1.67), b5 98%, w2l 1 | -58 $/wk, DD +7.0%, ww -65, stops 2.11(2.15), b5 83%, w2l 4 | +159 $/wk, DD -0.0%, ww +0, stops 2.00(2.00), b5 100%, w2l 0 |
| nyam | **b-a** | -226 $/wk, DD +24.3 pts, ww +48 | +213 $/wk, DD -2.5 pts, ww +0 | +236 $/wk, DD -0.7 pts, ww -95 | -2 $/wk, DD -0.1 pts, ww +0 |
| nyam | **c-a** | +193 $/wk, DD +31.5 pts, ww +48 | +533 $/wk, DD +25.1 pts, ww +168 | +340 $/wk, DD -0.4 pts, ww -95 | +32 $/wk, DD +4.5 pts, ww +0 |
| nypm | a | -315 $/wk, DD -34.3%, ww -196, stops 0.08(0.08), b5 101%, w2l 0 | -174 $/wk, DD -34.3%, ww -196, stops 0.08(0.08), b5 100%, w2l 1 | +70 $/wk, DD +1.3%, ww +1823, stops 0.04(0.04), b5 100%, w2l 1 | -26 $/wk, DD -3.9%, ww +0, stops 0.05(0.05), b5 100%, w2l 0 |
| nypm | b | -322 $/wk, DD -35.8%, ww -286, stops 0.08(0.08), b5 101%, w2l 0 | -323 $/wk, DD -35.8%, ww -286, stops 0.08(0.08), b5 96%, w2l 1 | -0 $/wk, DD +5.3%, ww +2706, stops 0.04(0.04), b5 96%, w2l 1 | -47 $/wk, DD -7.0%, ww +0, stops 0.05(0.05), b5 100%, w2l 0 |
| nypm | c | -351 $/wk, DD -37.4%, ww -286, stops 0.08(0.08), b5 99%, w2l 0 | -254 $/wk, DD -37.4%, ww -286, stops 0.08(0.08), b5 96%, w2l 1 | +9 $/wk, DD -0.1%, ww +1823, stops 0.04(0.04), b5 96%, w2l 1 | -49 $/wk, DD -7.3%, ww +0, stops 0.05(0.05), b5 100%, w2l 0 |
| nypm | **b-a** | -7 $/wk, DD -1.5 pts, ww -90 | -149 $/wk, DD -1.5 pts, ww -90 | -70 $/wk, DD +4.0 pts, ww +883 | -21 $/wk, DD -3.1 pts, ww +0 |
| nypm | **c-a** | -36 $/wk, DD -3.1 pts, ww -90 | -80 $/wk, DD -3.1 pts, ww -90 | -61 $/wk, DD -1.3 pts, ww +0 | -23 $/wk, DD -3.4 pts, ww +0 |

**D6KT** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -1487 $/wk, DD -12.3%, ww -6659, stops 10.50(10.35), b5 100%, w2l 0 | -2327 $/wk, DD -12.3%, ww -6659, stops 10.92(10.99), b5 97%, w2l 0 | n/a | n/a |
| all | b | -2027 $/wk, DD -20.6%, ww -10988, stops 10.35(10.35), b5 97%, w2l 0 | -2452 $/wk, DD -20.6%, ww -10988, stops 10.80(10.99), b5 97%, w2l 0 | n/a | n/a |
| all | c | -2233 $/wk, DD -29.1%, ww -15444, stops 10.42(10.35), b5 99%, w2l 0 | -1533 $/wk, DD -29.1%, ww -15444, stops 10.84(10.99), b5 98%, w2l 1 | n/a | n/a |
| all | **b-a** | -540 $/wk, DD -8.3 pts, ww -4329 | -125 $/wk, DD -8.3 pts, ww -4329 | n/a | n/a |
| all | **c-a** | -746 $/wk, DD -16.8 pts, ww -8785 | +794 $/wk, DD -16.8 pts, ww -8785 | n/a | n/a |
| asia | a | -1610 $/wk, DD -16.2%, ww -8076, stops 6.24(6.24), b5 100%, w2l 0 | -199 $/wk, DD -16.2%, ww -8076, stops 6.28(6.35), b5 97%, w2l 0 | n/a | n/a |
| asia | b | -1907 $/wk, DD -8.1%, ww -4176, stops 6.24(6.24), b5 96%, w2l 0 | -274 $/wk, DD -8.1%, ww -4176, stops 6.28(6.35), b5 97%, w2l 0 | n/a | n/a |
| asia | c | -2414 $/wk, DD -20.0%, ww -9928, stops 6.24(6.24), b5 96%, w2l 1 | -42 $/wk, DD -20.0%, ww -9928, stops 6.28(6.35), b5 99%, w2l 1 | n/a | n/a |
| asia | **b-a** | -297 $/wk, DD +8.1 pts, ww +3900 | -75 $/wk, DD +8.1 pts, ww +3900 | n/a | n/a |
| asia | **c-a** | -804 $/wk, DD -3.8 pts, ww -1852 | +157 $/wk, DD -3.8 pts, ww -1852 | n/a | n/a |
| london | a | +364 $/wk, DD -7.4%, ww -1284, stops 2.89(2.74), b5 104%, w2l 0 | +197 $/wk, DD -7.4%, ww -1284, stops 2.97(2.89), b5 101%, w2l 0 | n/a | n/a |
| london | b | -361 $/wk, DD -9.7%, ww -664, stops 2.82(2.74), b5 105%, w2l 1 | -543 $/wk, DD -9.7%, ww -664, stops 2.89(2.89), b5 103%, w2l 1 | n/a | n/a |
| london | c | -190 $/wk, DD -11.9%, ww +0, stops 2.82(2.74), b5 106%, w2l 0 | +132 $/wk, DD -11.9%, ww +0, stops 2.85(2.89), b5 106%, w2l 0 | n/a | n/a |
| london | **b-a** | -725 $/wk, DD -2.3 pts, ww +620 | -740 $/wk, DD -2.3 pts, ww +620 | n/a | n/a |
| london | **c-a** | -554 $/wk, DD -4.5 pts, ww +1284 | -65 $/wk, DD -4.5 pts, ww +1284 | n/a | n/a |
| nyam | a | +100 $/wk, DD -3.1%, ww -2951, stops 1.29(1.29), b5 99%, w2l 0 | -880 $/wk, DD -45.4%, ww -364, stops 1.64(1.67), b5 96%, w2l 2 | n/a | n/a |
| nyam | b | -246 $/wk, DD +6.5%, ww +0, stops 1.22(1.29), b5 86%, w2l 0 | -936 $/wk, DD -28.2%, ww +1027, stops 1.60(1.67), b5 89%, w2l 1 | n/a | n/a |
| nyam | c | +484 $/wk, DD +18.3%, ww +0, stops 1.29(1.29), b5 97%, w2l 0 | -696 $/wk, DD -35.9%, ww -79, stops 1.67(1.67), b5 89%, w2l 1 | n/a | n/a |
| nyam | **b-a** | -346 $/wk, DD +9.5 pts, ww +2951 | -56 $/wk, DD +17.3 pts, ww +1391 | n/a | n/a |
| nyam | **c-a** | +384 $/wk, DD +21.3 pts, ww +2951 | +184 $/wk, DD +9.5 pts, ww +285 | n/a | n/a |
| nypm | a | -341 $/wk, DD -35.9%, ww -538, stops 0.08(0.08), b5 113%, w2l 1 | -1445 $/wk, DD -35.9%, ww -538, stops 0.04(0.08), b5 56%, w2l 4 | n/a | n/a |
| nypm | b | +487 $/wk, DD -27.3%, ww -855, stops 0.08(0.08), b5 100%, w2l 1 | -698 $/wk, DD -27.3%, ww -855, stops 0.04(0.08), b5 70%, w2l 4 | n/a | n/a |
| nypm | c | -112 $/wk, DD -48.2%, ww -1784, stops 0.08(0.08), b5 95%, w2l 1 | -926 $/wk, DD -48.2%, ww -1784, stops 0.04(0.08), b5 67%, w2l 2 | n/a | n/a |
| nypm | **b-a** | +828 $/wk, DD +8.6 pts, ww -316 | +747 $/wk, DD +8.6 pts, ww -316 | n/a | n/a |
| nypm | **c-a** | +229 $/wk, DD -12.3 pts, ww -1246 | +519 $/wk, DD -12.3 pts, ww -1246 | n/a | n/a |

**D6KC** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -949 $/wk, DD -12.1%, ww -6575, stops 10.50(10.35), b5 106%, w2l 0 | n/a | n/a | n/a |
| all | b | -2633 $/wk, DD -28.5%, ww -15124, stops 10.42(10.35), b5 99%, w2l 0 | n/a | n/a | n/a |
| all | c | -2476 $/wk, DD -31.1%, ww -16469, stops 10.58(10.35), b5 99%, w2l 0 | n/a | n/a | n/a |
| all | **b-a** | -1684 $/wk, DD -16.4 pts, ww -8549 | n/a | n/a | n/a |
| all | **c-a** | -1527 $/wk, DD -18.9 pts, ww -9894 | n/a | n/a | n/a |
| asia | a | -1097 $/wk, DD -12.4%, ww -6256, stops 6.24(6.24), b5 101%, w2l 0 | n/a | n/a | n/a |
| asia | b | -2161 $/wk, DD -20.0%, ww -9928, stops 6.24(6.24), b5 93%, w2l 0 | n/a | n/a | n/a |
| asia | c | -2724 $/wk, DD -20.0%, ww -9928, stops 6.24(6.24), b5 91%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | -1065 $/wk, DD -7.6 pts, ww -3672 | n/a | n/a | n/a |
| asia | **c-a** | -1628 $/wk, DD -7.6 pts, ww -3672 | n/a | n/a | n/a |
| london | a | +417 $/wk, DD -5.4%, ww -3857, stops 2.82(2.74), b5 103%, w2l 0 | n/a | n/a | n/a |
| london | b | +383 $/wk, DD -10.2%, ww -2235, stops 2.89(2.74), b5 102%, w2l 0 | n/a | n/a | n/a |
| london | c | +1117 $/wk, DD +1.6%, ww -1059, stops 2.89(2.74), b5 108%, w2l 0 | n/a | n/a | n/a |
| london | **b-a** | -34 $/wk, DD -4.8 pts, ww +1621 | n/a | n/a | n/a |
| london | **c-a** | +700 $/wk, DD +7.0 pts, ww +2798 | n/a | n/a | n/a |
| nyam | a | -466 $/wk, DD -48.9%, ww -3838, stops 1.37(1.29), b5 95%, w2l 0 | n/a | n/a | n/a |
| nyam | b | -724 $/wk, DD -35.7%, ww -5402, stops 1.22(1.29), b5 88%, w2l 0 | n/a | n/a | n/a |
| nyam | c | -1087 $/wk, DD -65.3%, ww -5201, stops 1.37(1.29), b5 82%, w2l 0 | n/a | n/a | n/a |
| nyam | **b-a** | -258 $/wk, DD +13.3 pts, ww -1563 | n/a | n/a | n/a |
| nyam | **c-a** | -621 $/wk, DD -16.4 pts, ww -1363 | n/a | n/a | n/a |
| nypm | a | +196 $/wk, DD -4.9%, ww -286, stops 0.08(0.08), b5 127%, w2l 1 | n/a | n/a | n/a |
| nypm | b | -131 $/wk, DD -47.4%, ww -399, stops 0.08(0.08), b5 79%, w2l 2 | n/a | n/a | n/a |
| nypm | c | +217 $/wk, DD -41.9%, ww -950, stops 0.08(0.08), b5 118%, w2l 1 | n/a | n/a | n/a |
| nypm | **b-a** | -327 $/wk, DD -42.5 pts, ww -113 | n/a | n/a | n/a |
| nypm | **c-a** | +21 $/wk, DD -37.0 pts, ww -664 | n/a | n/a | n/a |

**D6HT** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -52 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | +1 $/wk, DD +0.0%, ww +0, stops 11.03(10.99), b5 100%, w2l 0 | n/a | n/a |
| all | b | -135 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 99%, w2l 0 | +8 $/wk, DD +0.0%, ww +0, stops 10.99(10.99), b5 100%, w2l 0 | n/a | n/a |
| all | c | -7 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 99%, w2l 0 | +72 $/wk, DD +0.0%, ww +0, stops 10.99(10.99), b5 100%, w2l 0 | n/a | n/a |
| all | **b-a** | -84 $/wk, DD +0.0 pts, ww +0 | +7 $/wk, DD +0.0 pts, ww +0 | n/a | n/a |
| all | **c-a** | +45 $/wk, DD +0.0 pts, ww +0 | +71 $/wk, DD +0.0 pts, ww +0 | n/a | n/a |
| asia | a | -20 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 100%, w2l 0 | -10 $/wk, DD +0.0%, ww +0, stops 6.35(6.35), b5 100%, w2l 0 | n/a | n/a |
| asia | b | -135 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 99%, w2l 0 | -68 $/wk, DD +0.0%, ww +0, stops 6.35(6.35), b5 100%, w2l 0 | n/a | n/a |
| asia | c | -27 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 99%, w2l 0 | -14 $/wk, DD +0.0%, ww +0, stops 6.35(6.35), b5 100%, w2l 0 | n/a | n/a |
| asia | **b-a** | -115 $/wk, DD +0.0 pts, ww +0 | -57 $/wk, DD +0.0 pts, ww +0 | n/a | n/a |
| asia | **c-a** | -7 $/wk, DD +0.0 pts, ww +0 | -3 $/wk, DD +0.0 pts, ww +0 | n/a | n/a |
| london | a | -31 $/wk, DD -0.6%, ww +0, stops 2.74(2.74), b5 100%, w2l 0 | +11 $/wk, DD -0.6%, ww +0, stops 2.93(2.89), b5 100%, w2l 0 | n/a | n/a |
| london | b | +0 $/wk, DD +0.0%, ww +0, stops 2.74(2.74), b5 100%, w2l 0 | +76 $/wk, DD +0.0%, ww +0, stops 2.89(2.89), b5 100%, w2l 0 | n/a | n/a |
| london | c | -80 $/wk, DD -0.6%, ww +0, stops 2.74(2.74), b5 100%, w2l 0 | +36 $/wk, DD -0.6%, ww +0, stops 2.89(2.89), b5 100%, w2l 0 | n/a | n/a |
| london | **b-a** | +31 $/wk, DD +0.6 pts, ww +0 | +65 $/wk, DD +0.6 pts, ww +0 | n/a | n/a |
| london | **c-a** | -48 $/wk, DD +0.0 pts, ww +0 | +25 $/wk, DD -0.0 pts, ww +0 | n/a | n/a |
| nyam | a | +0 $/wk, DD +0.0%, ww +0, stops 1.29(1.29), b5 100%, w2l 0 | +0 $/wk, DD +0.0%, ww +0, stops 1.67(1.67), b5 100%, w2l 0 | n/a | n/a |
| nyam | b | +0 $/wk, DD +0.0%, ww +0, stops 1.29(1.29), b5 100%, w2l 0 | +0 $/wk, DD +0.0%, ww +0, stops 1.67(1.67), b5 100%, w2l 0 | n/a | n/a |
| nyam | c | +100 $/wk, DD +6.8%, ww +0, stops 1.29(1.29), b5 100%, w2l 0 | +50 $/wk, DD +0.0%, ww +0, stops 1.67(1.67), b5 100%, w2l 0 | n/a | n/a |
| nyam | **b-a** | +0 $/wk, DD +0.0 pts, ww +0 | +0 $/wk, DD +0.0 pts, ww +0 | n/a | n/a |
| nyam | **c-a** | +100 $/wk, DD +6.8 pts, ww +0 | +50 $/wk, DD +0.0 pts, ww +0 | n/a | n/a |
| nypm | a | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | n/a | n/a |
| nypm | b | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | n/a | n/a |
| nypm | c | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | n/a | n/a |
| nypm | **b-a** | +0 $/wk, DD +0.0 pts, ww +0 | +0 $/wk, DD +0.0 pts, ww +0 | n/a | n/a |
| nypm | **c-a** | +0 $/wk, DD +0.0 pts, ww +0 | +0 $/wk, DD +0.0 pts, ww +0 | n/a | n/a |

**D6HC** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -163 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | -55 $/wk, DD +0.0%, ww +0, stops 11.03(10.99), b5 100%, w2l 0 | n/a | n/a |
| all | b | +24 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 99%, w2l 0 | +88 $/wk, DD +0.0%, ww +0, stops 10.99(10.99), b5 100%, w2l 0 | n/a | n/a |
| all | c | -7 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 99%, w2l 0 | +72 $/wk, DD +0.0%, ww +0, stops 10.99(10.99), b5 100%, w2l 0 | n/a | n/a |
| all | **b-a** | +187 $/wk, DD +0.0 pts, ww +0 | +143 $/wk, DD +0.0 pts, ww +0 | n/a | n/a |
| all | **c-a** | +156 $/wk, DD +0.0 pts, ww +0 | +127 $/wk, DD +0.0 pts, ww +0 | n/a | n/a |
| asia | a | +5 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 100%, w2l 0 | +3 $/wk, DD +0.0%, ww +0, stops 6.35(6.35), b5 100%, w2l 0 | n/a | n/a |
| asia | b | -27 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 99%, w2l 0 | -14 $/wk, DD +0.0%, ww +0, stops 6.35(6.35), b5 100%, w2l 0 | n/a | n/a |
| asia | c | -27 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 99%, w2l 0 | -14 $/wk, DD +0.0%, ww +0, stops 6.35(6.35), b5 100%, w2l 0 | n/a | n/a |
| asia | **b-a** | -32 $/wk, DD +0.0 pts, ww +0 | -16 $/wk, DD +0.0 pts, ww +0 | n/a | n/a |
| asia | **c-a** | -32 $/wk, DD +0.0 pts, ww +0 | -16 $/wk, DD +0.0 pts, ww +0 | n/a | n/a |
| london | a | -168 $/wk, DD -0.6%, ww +0, stops 2.74(2.74), b5 98%, w2l 0 | -58 $/wk, DD -0.6%, ww +0, stops 2.93(2.89), b5 100%, w2l 0 | n/a | n/a |
| london | b | -48 $/wk, DD +0.0%, ww +0, stops 2.74(2.74), b5 100%, w2l 0 | +51 $/wk, DD +0.0%, ww +0, stops 2.89(2.89), b5 100%, w2l 0 | n/a | n/a |
| london | c | -80 $/wk, DD -0.6%, ww +0, stops 2.74(2.74), b5 100%, w2l 0 | +36 $/wk, DD -0.6%, ww +0, stops 2.89(2.89), b5 100%, w2l 0 | n/a | n/a |
| london | **b-a** | +120 $/wk, DD +0.6 pts, ww +0 | +109 $/wk, DD +0.6 pts, ww +0 | n/a | n/a |
| london | **c-a** | +89 $/wk, DD +0.0 pts, ww +0 | +93 $/wk, DD -0.0 pts, ww +0 | n/a | n/a |
| nyam | a | +0 $/wk, DD +0.0%, ww +0, stops 1.29(1.29), b5 100%, w2l 0 | +0 $/wk, DD +0.0%, ww +0, stops 1.67(1.67), b5 100%, w2l 0 | n/a | n/a |
| nyam | b | +100 $/wk, DD +6.8%, ww +0, stops 1.29(1.29), b5 100%, w2l 0 | +50 $/wk, DD +0.0%, ww +0, stops 1.67(1.67), b5 100%, w2l 0 | n/a | n/a |
| nyam | c | +100 $/wk, DD +6.8%, ww +0, stops 1.29(1.29), b5 100%, w2l 0 | +50 $/wk, DD +0.0%, ww +0, stops 1.67(1.67), b5 100%, w2l 0 | n/a | n/a |
| nyam | **b-a** | +100 $/wk, DD +6.8 pts, ww +0 | +50 $/wk, DD +0.0 pts, ww +0 | n/a | n/a |
| nyam | **c-a** | +100 $/wk, DD +6.8 pts, ww +0 | +50 $/wk, DD +0.0 pts, ww +0 | n/a | n/a |
| nypm | a | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | n/a | n/a |
| nypm | b | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | n/a | n/a |
| nypm | c | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | n/a | n/a |
| nypm | **b-a** | +0 $/wk, DD +0.0 pts, ww +0 | +0 $/wk, DD +0.0 pts, ww +0 | n/a | n/a |
| nypm | **c-a** | +0 $/wk, DD +0.0 pts, ww +0 | +0 $/wk, DD +0.0 pts, ww +0 | n/a | n/a |

### Dial 7 lock levels (BookLock peak 2R threshold)

**D7T** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | +353 $/wk, DD +7.2%, ww +3778, stops 9.89(10.35), b5 100%, w2l 0 | +731 $/wk, DD +7.2%, ww +3778, stops 10.84(10.99), b5 101%, w2l 0 | +696 $/wk, DD -1.2%, ww +45, stops 10.64(10.66), b5 102%, w2l 0 | -449 $/wk, DD +0.0%, ww +0, stops 9.23(9.31), b5 99%, w2l 0 |
| all | b | -2051 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 91%, w2l 0 | -648 $/wk, DD +0.0%, ww +0, stops 10.99(10.99), b5 98%, w2l 0 | -171 $/wk, DD -0.0%, ww +45, stops 10.70(10.66), b5 99%, w2l 0 | -1150 $/wk, DD +0.0%, ww +0, stops 9.26(9.31), b5 88%, w2l 0 |
| all | c | -2388 $/wk, DD +7.2%, ww +3778, stops 10.12(10.35), b5 93%, w2l 0 | -880 $/wk, DD +7.2%, ww +3778, stops 10.88(10.99), b5 98%, w2l 0 | -319 $/wk, DD +5.0%, ww +45, stops 10.59(10.66), b5 99%, w2l 0 | -1171 $/wk, DD +0.0%, ww +0, stops 9.26(9.31), b5 87%, w2l 0 |
| all | **b-a** | -2404 $/wk, DD -7.2 pts, ww -3778 | -1379 $/wk, DD -7.2 pts, ww -3778 | -867 $/wk, DD +1.2 pts, ww +0 | -701 $/wk, DD +0.0 pts, ww +0 |
| all | **c-a** | -2740 $/wk, DD +0.0 pts, ww +0 | -1611 $/wk, DD +0.0 pts, ww +0 | -1016 $/wk, DD +6.2 pts, ww +0 | -722 $/wk, DD +0.0 pts, ww +0 |
| asia | a | +646 $/wk, DD +0.0%, ww +0, stops 5.93(6.24), b5 100%, w2l 0 | +630 $/wk, DD +0.0%, ww +0, stops 6.32(6.35), b5 101%, w2l 0 | +339 $/wk, DD -2.9%, ww +0, stops 5.89(5.87), b5 101%, w2l 0 | +23 $/wk, DD +0.0%, ww +0, stops 4.15(4.18), b5 100%, w2l 0 |
| asia | b | -922 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 93%, w2l 0 | -340 $/wk, DD +0.0%, ww +0, stops 6.39(6.35), b5 95%, w2l 0 | -45 $/wk, DD -0.5%, ww +0, stops 5.91(5.87), b5 96%, w2l 0 | -730 $/wk, DD +0.0%, ww +0, stops 4.15(4.18), b5 86%, w2l 0 |
| asia | c | -1181 $/wk, DD +0.0%, ww +0, stops 6.16(6.24), b5 93%, w2l 0 | -464 $/wk, DD +0.0%, ww +0, stops 6.35(6.35), b5 95%, w2l 0 | -216 $/wk, DD -5.4%, ww +0, stops 5.89(5.87), b5 96%, w2l 0 | -730 $/wk, DD +0.0%, ww +0, stops 4.15(4.18), b5 86%, w2l 0 |
| asia | **b-a** | -1569 $/wk, DD +0.0 pts, ww +0 | -970 $/wk, DD +0.0 pts, ww +0 | -385 $/wk, DD +2.5 pts, ww +0 | -753 $/wk, DD +0.0 pts, ww +0 |
| asia | **c-a** | -1827 $/wk, DD +0.0 pts, ww +0 | -1093 $/wk, DD +0.0 pts, ww +0 | -556 $/wk, DD -2.5 pts, ww +0 | -753 $/wk, DD +0.0 pts, ww +0 |
| london | a | -466 $/wk, DD +0.0%, ww +0, stops 2.66(2.74), b5 90%, w2l 0 | +355 $/wk, DD +0.0%, ww +0, stops 2.82(2.89), b5 99%, w2l 0 | +245 $/wk, DD +0.0%, ww +0, stops 2.59(2.61), b5 99%, w2l 0 | -213 $/wk, DD +0.0%, ww +0, stops 3.08(3.08), b5 101%, w2l 0 |
| london | b | -1200 $/wk, DD +1.1%, ww +0, stops 2.82(2.74), b5 91%, w2l 0 | -44 $/wk, DD +1.1%, ww +0, stops 2.89(2.89), b5 97%, w2l 0 | -120 $/wk, DD +1.1%, ww +0, stops 2.63(2.61), b5 98%, w2l 0 | -174 $/wk, DD +0.0%, ww +0, stops 3.08(3.08), b5 100%, w2l 0 |
| london | c | -1205 $/wk, DD +1.1%, ww +0, stops 2.74(2.74), b5 87%, w2l 0 | +39 $/wk, DD +1.1%, ww +0, stops 2.85(2.89), b5 100%, w2l 0 | +6 $/wk, DD +1.1%, ww +0, stops 2.57(2.61), b5 100%, w2l 0 | -174 $/wk, DD +0.0%, ww +0, stops 3.08(3.08), b5 100%, w2l 0 |
| london | **b-a** | -733 $/wk, DD +1.1 pts, ww +0 | -399 $/wk, DD +1.1 pts, ww +0 | -365 $/wk, DD +1.1 pts, ww +0 | +39 $/wk, DD +0.0 pts, ww +0 |
| london | **c-a** | -739 $/wk, DD +1.1 pts, ww +0 | -317 $/wk, DD +1.1 pts, ww +0 | -239 $/wk, DD +1.1 pts, ww +0 | +39 $/wk, DD +0.0 pts, ww +0 |
| nyam | a | +782 $/wk, DD +28.4%, ww +658, stops 1.22(1.29), b5 102%, w2l 0 | +131 $/wk, DD -2.7%, ww +0, stops 1.64(1.67), b5 103%, w2l 1 | +115 $/wk, DD -6.2%, ww -1080, stops 2.13(2.15), b5 100%, w2l 1 | -35 $/wk, DD -0.4%, ww +0, stops 1.95(2.00), b5 100%, w2l 0 |
| nyam | b | +402 $/wk, DD +35.4%, ww +658, stops 1.22(1.29), b5 91%, w2l 1 | +51 $/wk, DD -2.7%, ww +0, stops 1.64(1.67), b5 98%, w2l 1 | +33 $/wk, DD -7.4%, ww -1080, stops 2.11(2.15), b5 97%, w2l 1 | -203 $/wk, DD -7.3%, ww +0, stops 1.97(2.00), b5 92%, w2l 0 |
| nyam | c | +609 $/wk, DD +24.0%, ww +658, stops 1.14(1.29), b5 94%, w2l 0 | -1 $/wk, DD -2.7%, ww +0, stops 1.60(1.67), b5 98%, w2l 1 | +70 $/wk, DD -6.0%, ww -1080, stops 2.09(2.15), b5 97%, w2l 1 | -203 $/wk, DD -7.3%, ww +0, stops 1.97(2.00), b5 92%, w2l 0 |
| nyam | **b-a** | -380 $/wk, DD +7.0 pts, ww +0 | -80 $/wk, DD +0.0 pts, ww +0 | -81 $/wk, DD -1.2 pts, ww +0 | -168 $/wk, DD -6.8 pts, ww +0 |
| nyam | **c-a** | -174 $/wk, DD -4.4 pts, ww +0 | -132 $/wk, DD +0.0 pts, ww +0 | -44 $/wk, DD +0.1 pts, ww +0 | -168 $/wk, DD -6.8 pts, ww +0 |
| nypm | a | -609 $/wk, DD -39.9%, ww -286, stops 0.08(0.08), b5 96%, w2l 2 | -385 $/wk, DD -39.9%, ww -286, stops 0.08(0.08), b5 100%, w2l 2 | -3 $/wk, DD +15.8%, ww +1951, stops 0.04(0.04), b5 100%, w2l 2 | -225 $/wk, DD -5.9%, ww +0, stops 0.05(0.05), b5 87%, w2l 0 |
| nypm | b | -332 $/wk, DD -9.3%, ww +0, stops 0.08(0.08), b5 96%, w2l 2 | -315 $/wk, DD -9.3%, ww +0, stops 0.08(0.08), b5 95%, w2l 2 | -39 $/wk, DD +3.9%, ww +1951, stops 0.06(0.04), b5 95%, w2l 4 | -43 $/wk, DD +7.2%, ww +0, stops 0.05(0.05), b5 87%, w2l 0 |
| nypm | c | -609 $/wk, DD -39.9%, ww -286, stops 0.08(0.08), b5 96%, w2l 2 | -454 $/wk, DD -39.9%, ww -286, stops 0.08(0.08), b5 95%, w2l 2 | -179 $/wk, DD -1.9%, ww +1951, stops 0.04(0.04), b5 95%, w2l 5 | -65 $/wk, DD +13.2%, ww +0, stops 0.05(0.05), b5 87%, w2l 0 |
| nypm | **b-a** | +278 $/wk, DD +30.6 pts, ww +286 | +70 $/wk, DD +30.6 pts, ww +286 | -36 $/wk, DD -12.0 pts, ww +0 | +181 $/wk, DD +13.2 pts, ww +0 |
| nypm | **c-a** | +0 $/wk, DD +0.0 pts, ww +0 | -69 $/wk, DD +0.0 pts, ww +0 | -176 $/wk, DD -17.8 pts, ww +0 | +160 $/wk, DD +19.1 pts, ww +0 |

**D7C** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -760 $/wk, DD +0.0%, ww +0, stops 10.04(10.35), b5 95%, w2l 0 | +462 $/wk, DD +0.0%, ww +0, stops 10.96(10.99), b5 102%, w2l 0 | +493 $/wk, DD -1.2%, ww +45, stops 10.68(10.66), b5 100%, w2l 0 | -339 $/wk, DD +0.0%, ww +0, stops 9.23(9.31), b5 102%, w2l 0 |
| all | b | -1052 $/wk, DD +0.0%, ww +0, stops 10.20(10.35), b5 99%, w2l 0 | -159 $/wk, DD +0.0%, ww +0, stops 10.92(10.99), b5 97%, w2l 0 | +68 $/wk, DD +1.4%, ww +45, stops 10.64(10.66), b5 98%, w2l 0 | -899 $/wk, DD +0.0%, ww +0, stops 9.26(9.31), b5 94%, w2l 0 |
| all | c | -788 $/wk, DD +0.0%, ww +0, stops 10.20(10.35), b5 101%, w2l 0 | +106 $/wk, DD +0.0%, ww +0, stops 10.92(10.99), b5 98%, w2l 0 | +273 $/wk, DD +5.0%, ww +45, stops 10.59(10.66), b5 97%, w2l 0 | -747 $/wk, DD +0.0%, ww +0, stops 9.26(9.31), b5 94%, w2l 0 |
| all | **b-a** | -292 $/wk, DD +0.0 pts, ww +0 | -621 $/wk, DD +0.0 pts, ww +0 | -425 $/wk, DD +2.6 pts, ww +0 | -560 $/wk, DD +0.0 pts, ww +0 |
| all | **c-a** | -27 $/wk, DD +0.0 pts, ww +0 | -357 $/wk, DD +0.0 pts, ww +0 | -219 $/wk, DD +6.2 pts, ww +0 | -409 $/wk, DD +0.0 pts, ww +0 |
| asia | a | -517 $/wk, DD +0.0%, ww +0, stops 5.93(6.24), b5 94%, w2l 0 | +48 $/wk, DD +0.0%, ww +0, stops 6.32(6.35), b5 97%, w2l 0 | +46 $/wk, DD -2.9%, ww +0, stops 5.89(5.87), b5 97%, w2l 0 | +134 $/wk, DD +0.0%, ww +0, stops 4.15(4.18), b5 102%, w2l 0 |
| asia | b | -442 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 98%, w2l 0 | -57 $/wk, DD +0.0%, ww +0, stops 6.39(6.35), b5 96%, w2l 0 | +55 $/wk, DD -2.1%, ww +0, stops 5.89(5.87), b5 96%, w2l 0 | -451 $/wk, DD +0.0%, ww +0, stops 4.15(4.18), b5 91%, w2l 0 |
| asia | c | -329 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 98%, w2l 0 | -105 $/wk, DD +0.0%, ww +0, stops 6.39(6.35), b5 95%, w2l 0 | -11 $/wk, DD -2.1%, ww +0, stops 5.89(5.87), b5 95%, w2l 0 | -451 $/wk, DD +0.0%, ww +0, stops 4.15(4.18), b5 91%, w2l 0 |
| asia | **b-a** | +74 $/wk, DD +0.0 pts, ww +0 | -106 $/wk, DD +0.0 pts, ww +0 | +9 $/wk, DD +0.9 pts, ww +0 | -585 $/wk, DD +0.0 pts, ww +0 |
| asia | **c-a** | +187 $/wk, DD +0.0 pts, ww +0 | -153 $/wk, DD +0.0 pts, ww +0 | -57 $/wk, DD +0.9 pts, ww +0 | -585 $/wk, DD +0.0 pts, ww +0 |
| london | a | -389 $/wk, DD +1.7%, ww +0, stops 2.74(2.74), b5 94%, w2l 0 | +578 $/wk, DD +1.7%, ww +0, stops 2.89(2.89), b5 100%, w2l 0 | +314 $/wk, DD +1.7%, ww +0, stops 2.63(2.61), b5 100%, w2l 0 | -213 $/wk, DD +0.0%, ww +0, stops 3.08(3.08), b5 101%, w2l 0 |
| london | b | -1220 $/wk, DD +1.1%, ww +0, stops 2.74(2.74), b5 90%, w2l 0 | +51 $/wk, DD +1.1%, ww +0, stops 2.85(2.89), b5 97%, w2l 0 | -47 $/wk, DD +1.1%, ww +0, stops 2.61(2.61), b5 98%, w2l 0 | -244 $/wk, DD +0.0%, ww +0, stops 3.08(3.08), b5 100%, w2l 0 |
| london | c | -1070 $/wk, DD +1.1%, ww +0, stops 2.74(2.74), b5 92%, w2l 0 | +228 $/wk, DD +1.1%, ww +0, stops 2.85(2.89), b5 99%, w2l 0 | +106 $/wk, DD +1.1%, ww +0, stops 2.57(2.61), b5 99%, w2l 0 | -85 $/wk, DD +0.0%, ww +0, stops 3.08(3.08), b5 100%, w2l 0 |
| london | **b-a** | -831 $/wk, DD -0.6 pts, ww +0 | -526 $/wk, DD -0.6 pts, ww +0 | -361 $/wk, DD -0.6 pts, ww +0 | -31 $/wk, DD +0.0 pts, ww +0 |
| london | **c-a** | -681 $/wk, DD -0.6 pts, ww +0 | -350 $/wk, DD -0.6 pts, ww +0 | -208 $/wk, DD -0.6 pts, ww +0 | +128 $/wk, DD +0.0 pts, ww +0 |
| nyam | a | +347 $/wk, DD +23.9%, ww +658, stops 1.29(1.29), b5 96%, w2l 0 | +105 $/wk, DD -2.8%, ww -21, stops 1.67(1.67), b5 106%, w2l 1 | +86 $/wk, DD -5.6%, ww -1080, stops 2.13(2.15), b5 100%, w2l 1 | -35 $/wk, DD -0.4%, ww +0, stops 1.95(2.00), b5 100%, w2l 0 |
| nyam | b | +943 $/wk, DD +33.6%, ww +658, stops 1.14(1.29), b5 112%, w2l 1 | +194 $/wk, DD -2.7%, ww +0, stops 1.60(1.67), b5 99%, w2l 3 | +98 $/wk, DD -7.9%, ww -1080, stops 2.09(2.15), b5 98%, w2l 3 | -145 $/wk, DD -7.0%, ww +0, stops 1.97(2.00), b5 96%, w2l 0 |
| nyam | c | +943 $/wk, DD +26.6%, ww +658, stops 1.14(1.29), b5 115%, w2l 0 | +242 $/wk, DD -2.7%, ww +0, stops 1.60(1.67), b5 101%, w2l 2 | +149 $/wk, DD -5.8%, ww -1080, stops 2.09(2.15), b5 97%, w2l 2 | -147 $/wk, DD -7.3%, ww +0, stops 1.97(2.00), b5 96%, w2l 0 |
| nyam | **b-a** | +595 $/wk, DD +9.7 pts, ww +0 | +89 $/wk, DD +0.1 pts, ww +21 | +12 $/wk, DD -2.3 pts, ww +0 | -110 $/wk, DD -6.6 pts, ww +0 |
| nyam | **c-a** | +596 $/wk, DD +2.6 pts, ww +0 | +138 $/wk, DD +0.1 pts, ww +21 | +63 $/wk, DD -0.2 pts, ww +0 | -112 $/wk, DD -6.8 pts, ww +0 |
| nypm | a | -202 $/wk, DD -9.3%, ww +0, stops 0.08(0.08), b5 96%, w2l 2 | -268 $/wk, DD -9.3%, ww +0, stops 0.08(0.08), b5 100%, w2l 2 | +46 $/wk, DD +14.2%, ww +1951, stops 0.04(0.04), b5 100%, w2l 2 | -225 $/wk, DD -5.9%, ww +0, stops 0.05(0.05), b5 87%, w2l 0 |
| nypm | b | -332 $/wk, DD -9.3%, ww +0, stops 0.08(0.08), b5 96%, w2l 2 | -346 $/wk, DD -9.3%, ww +0, stops 0.08(0.08), b5 95%, w2l 2 | -38 $/wk, DD +6.6%, ww +1951, stops 0.06(0.04), b5 95%, w2l 4 | -59 $/wk, DD +7.2%, ww +0, stops 0.05(0.05), b5 87%, w2l 0 |
| nypm | c | -332 $/wk, DD -9.3%, ww +0, stops 0.08(0.08), b5 96%, w2l 2 | -260 $/wk, DD -9.3%, ww +0, stops 0.08(0.08), b5 95%, w2l 2 | +29 $/wk, DD +10.6%, ww +1951, stops 0.04(0.04), b5 95%, w2l 4 | -65 $/wk, DD +13.2%, ww +0, stops 0.05(0.05), b5 87%, w2l 0 |
| nypm | **b-a** | -130 $/wk, DD +0.0 pts, ww +0 | -78 $/wk, DD +0.0 pts, ww +0 | -85 $/wk, DD -7.6 pts, ww +0 | +166 $/wk, DD +13.2 pts, ww +0 |
| nypm | **c-a** | -130 $/wk, DD +0.0 pts, ww +0 | +8 $/wk, DD +0.0 pts, ww +0 | -17 $/wk, DD -3.6 pts, ww +0 | +160 $/wk, DD +19.1 pts, ww +0 |

## 3. Best setting per dial and per session (drawdown first: L6M + HOLD maxDD cut, tolerant gate; status says which windows it holds in)
| dial | scope | best cell | status | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|---|---|
| D2 | all | D2F_c | fails recent gate | -6967 $/wk, DD -9.6%, ww -3770, stops 13.77(10.35), b5 79%, w2l 3 | -2999 $/wk, DD -9.6%, ww -3770, stops 11.26(10.99), b5 76%, w2l 4 | n/a | n/a |
| D2 | asia | D2F_b | fails recent gate | -3571 $/wk, DD -14.4%, ww -20299, stops 8.52(6.24), b5 74%, w2l 1 | -2696 $/wk, DD -14.4%, ww -20299, stops 6.12(6.35), b5 72%, w2l 2 | n/a | n/a |
| D2 | london | D2F_b | fails recent gate | -2903 $/wk, DD +26.4%, ww +4826, stops 5.40(2.74), b5 66%, w2l 2 | -255 $/wk, DD +26.4%, ww +4826, stops 4.03(2.89), b5 79%, w2l 3 | n/a | n/a |
| D2 | nyam | D2F_a | fails recent gate | +452 $/wk, DD +17.9%, ww -2881, stops 1.98(1.29), b5 92%, w2l 0 | -130 $/wk, DD -27.1%, ww -294, stops 1.98(1.67), b5 108%, w2l 2 | n/a | n/a |
| D2 | nypm | D2F_a | fails recent gate | -30 $/wk, DD +7.3%, ww -286, stops 0.53(0.08), b5 135%, w2l 3 | -812 $/wk, DD +7.3%, ww -286, stops 0.38(0.08), b5 45%, w2l 4 | n/a | n/a |
| D3 | all | D3T_b | fails recent gate | -5003 $/wk, DD +6.5%, ww -32, stops 11.03(10.35), b5 88%, w2l 2 | -2173 $/wk, DD +6.5%, ww -32, stops 13.54(10.99), b5 101%, w2l 2 | -201 $/wk, DD -28.8%, ww -20833, stops 13.31(10.66), b5 98%, w2l 4 | -1876 $/wk, DD +0.0%, ww +0, stops 9.13(9.31), b5 78%, w2l 0 |
| D3 | asia | D3T_b | fails recent gate | -3340 $/wk, DD +6.7%, ww -13308, stops 7.15(6.24), b5 89%, w2l 0 | -1843 $/wk, DD +6.7%, ww -13308, stops 7.76(6.35), b5 92%, w2l 1 | -1932 $/wk, DD -4.9%, ww -2428, stops 7.23(5.87), b5 88%, w2l 2 | -2041 $/wk, DD +0.0%, ww +0, stops 4.10(4.18), b5 72%, w2l 1 |
| D3 | london | D3C_c | LEAD (recent+older gate) | +504 $/wk, DD +4.0%, ww +2112, stops 3.20(2.74), b5 89%, w2l 0 | +904 $/wk, DD +4.0%, ww +2112, stops 4.79(2.89), b5 93%, w2l 0 | +1140 $/wk, DD +4.0%, ww +2112, stops 4.66(2.61), b5 90%, w2l 3 | +840 $/wk, DD +0.0%, ww +0, stops 3.05(3.08), b5 103%, w2l 0 |
| D3 | nyam | D3T_b | fails recent gate | -131 $/wk, DD +12.8%, ww +592, stops 1.14(1.29), b5 82%, w2l 1 | -194 $/wk, DD -13.7%, ww -2170, stops 2.02(1.67), b5 87%, w2l 2 | +793 $/wk, DD +30.2%, ww +1768, stops 2.44(2.15), b5 99%, w2l 4 | -361 $/wk, DD -2.1%, ww +0, stops 2.00(2.00), b5 95%, w2l 1 |
| D3 | nypm | D3C_b | fails recent gate | -781 $/wk, DD +5.4%, ww +1073, stops 0.08(0.08), b5 16%, w2l 4 | -358 $/wk, DD +5.4%, ww +1073, stops 0.30(0.08), b5 79%, w2l 4 | +205 $/wk, DD +26.3%, ww +3190, stops 0.42(0.04), b5 79%, w2l 8 | -67 $/wk, DD +4.7%, ww -63, stops 0.10(0.05), b5 93%, w2l 1 |
| D4 | all | D4I1_c | fails recent gate | -4492 $/wk, DD +36.2%, ww +16680, stops 7.68(10.35), b5 77%, w2l 3 | -8276 $/wk, DD +36.2%, ww +16680, stops 8.14(10.99), b5 66%, w2l 5 | -5085 $/wk, DD +23.9%, ww +9872, stops 7.19(10.66), b5 54%, w2l 8 | -1152 $/wk, DD +0.0%, ww +0, stops 8.44(9.31), b5 99%, w2l 1 |
| D4 | asia | D4I05_b | fails recent gate | -13211 $/wk, DD +59.2%, ww +11105, stops 1.90(6.24), b5 15%, w2l 3 | -13450 $/wk, DD +31.0%, ww +11105, stops 1.79(6.35), b5 24%, w2l 6 | n/a | n/a |
| D4 | london | D4I1_a | LEAD (recent+older gate) | +4852 $/wk, DD +20.3%, ww +2731, stops 1.60(2.74), b5 118%, w2l 1 | +2506 $/wk, DD +20.3%, ww +2731, stops 2.05(2.89), b5 95%, w2l 1 | +1702 $/wk, DD +20.3%, ww +2731, stops 1.94(2.61), b5 103%, w2l 7 | +1297 $/wk, DD +0.0%, ww +0, stops 2.77(3.08), b5 90%, w2l 0 |
| D4 | nyam | D4II05_c | recent pass, older FAILS | +1150 $/wk, DD +33.8%, ww +3493, stops 1.29(1.29), b5 91%, w2l 2 | +449 $/wk, DD +28.6%, ww +3080, stops 1.48(1.67), b5 69%, w2l 3 | +190 $/wk, DD +56.4%, ww +10647, stops 1.40(2.15), b5 54%, w2l 7 | -102 $/wk, DD +22.6%, ww +0, stops 1.79(2.00), b5 89%, w2l 0 |
| D4 | nypm | D4II05_b | fails recent gate | -523 $/wk, DD +34.9%, ww +822, stops 0.08(0.08), b5 68%, w2l 1 | -583 $/wk, DD +31.9%, ww +822, stops 0.08(0.08), b5 77%, w2l 2 | -181 $/wk, DD +0.8%, ww +1951, stops 0.04(0.04), b5 77%, w2l 6 | -149 $/wk, DD +11.0%, ww +0, stops 0.05(0.05), b5 69%, w2l 2 |
| D5 | all | D5SK13F_b | fails recent gate | -1574 $/wk, DD +12.9%, ww +10306, stops 9.21(10.35), b5 100%, w2l 1 | -6332 $/wk, DD +12.9%, ww +10306, stops 7.88(10.99), b5 81%, w2l 3 | -3434 $/wk, DD +32.5%, ww +21358, stops 7.35(10.66), b5 82%, w2l 5 | -1194 $/wk, DD +0.0%, ww +0, stops 9.15(9.31), b5 84%, w2l 0 |
| D5 | asia | D5SK13F_b | fails recent gate | +23 $/wk, DD +59.8%, ww +12753, stops 5.02(6.24), b5 79%, w2l 0 | -6394 $/wk, DD +51.0%, ww +12753, stops 3.96(6.35), b5 60%, w2l 3 | -2927 $/wk, DD +69.8%, ww +42160, stops 3.53(5.87), b5 77%, w2l 6 | -1585 $/wk, DD +0.0%, ww +0, stops 4.13(4.18), b5 81%, w2l 0 |
| D5 | london | D5SK13F_a | LEAD (recent+older gate) | +295 $/wk, DD +9.8%, ww +0, stops 2.89(2.74), b5 99%, w2l 0 | +284 $/wk, DD +9.8%, ww +0, stops 2.82(2.89), b5 90%, w2l 0 | +600 $/wk, DD +9.8%, ww +0, stops 2.36(2.61), b5 95%, w2l 0 | -42 $/wk, DD +0.0%, ww +0, stops 3.08(3.08), b5 100%, w2l 0 |
| D5 | nyam | D5R13F_c | LEAD (recent+older gate) | +441 $/wk, DD +26.5%, ww +0, stops 1.29(1.29), b5 100%, w2l 0 | +251 $/wk, DD +10.4%, ww +2587, stops 1.71(1.67), b5 99%, w2l 1 | +183 $/wk, DD -0.2%, ww +0, stops 2.19(2.15), b5 89%, w2l 2 | +55 $/wk, DD +7.5%, ww +0, stops 1.97(2.00), b5 100%, w2l 0 |
| D5 | nypm | D5R13F_c | recent pass, older FAILS | +182 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | +85 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | +203 $/wk, DD +4.9%, ww +2722, stops 0.04(0.04), b5 100%, w2l 0 | +48 $/wk, DD +7.0%, ww +0, stops 0.05(0.05), b5 100%, w2l 0 |
| D6 | all | D6HT_a | recent only (older not yet scored) | -52 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | +1 $/wk, DD +0.0%, ww +0, stops 11.03(10.99), b5 100%, w2l 0 | n/a | n/a |
| D6 | asia | D6HT_a | recent only (older not yet scored) | -20 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 100%, w2l 0 | -10 $/wk, DD +0.0%, ww +0, stops 6.35(6.35), b5 100%, w2l 0 | n/a | n/a |
| D6 | london | D6HT_b | recent only (older not yet scored) | +0 $/wk, DD +0.0%, ww +0, stops 2.74(2.74), b5 100%, w2l 0 | +76 $/wk, DD +0.0%, ww +0, stops 2.89(2.89), b5 100%, w2l 0 | n/a | n/a |
| D6 | nyam | D6HT_c | recent only (older not yet scored) | +100 $/wk, DD +6.8%, ww +0, stops 1.29(1.29), b5 100%, w2l 0 | +50 $/wk, DD +0.0%, ww +0, stops 1.67(1.67), b5 100%, w2l 0 | n/a | n/a |
| D6 | nypm | D6HT_a | recent only (older not yet scored) | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | n/a | n/a |
| D7 | all | D7T_c | fails recent gate | -2388 $/wk, DD +7.2%, ww +3778, stops 10.12(10.35), b5 93%, w2l 0 | -880 $/wk, DD +7.2%, ww +3778, stops 10.88(10.99), b5 98%, w2l 0 | -319 $/wk, DD +5.0%, ww +45, stops 10.59(10.66), b5 99%, w2l 0 | -1171 $/wk, DD +0.0%, ww +0, stops 9.26(9.31), b5 87%, w2l 0 |
| D7 | asia | D7T_b | fails recent gate | -922 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 93%, w2l 0 | -340 $/wk, DD +0.0%, ww +0, stops 6.39(6.35), b5 95%, w2l 0 | -45 $/wk, DD -0.5%, ww +0, stops 5.91(5.87), b5 96%, w2l 0 | -730 $/wk, DD +0.0%, ww +0, stops 4.15(4.18), b5 86%, w2l 0 |
| D7 | london | D7C_a | fails recent gate | -389 $/wk, DD +1.7%, ww +0, stops 2.74(2.74), b5 94%, w2l 0 | +578 $/wk, DD +1.7%, ww +0, stops 2.89(2.89), b5 100%, w2l 0 | +314 $/wk, DD +1.7%, ww +0, stops 2.63(2.61), b5 100%, w2l 0 | -213 $/wk, DD +0.0%, ww +0, stops 3.08(3.08), b5 101%, w2l 0 |
| D7 | nyam | D7T_b | fails recent gate | +402 $/wk, DD +35.4%, ww +658, stops 1.22(1.29), b5 91%, w2l 1 | +51 $/wk, DD -2.7%, ww +0, stops 1.64(1.67), b5 98%, w2l 1 | +33 $/wk, DD -7.4%, ww -1080, stops 2.11(2.15), b5 97%, w2l 1 | -203 $/wk, DD -7.3%, ww +0, stops 1.97(2.00), b5 92%, w2l 0 |
| D7 | nypm | D7C_a | fails recent gate | -202 $/wk, DD -9.3%, ww +0, stops 0.08(0.08), b5 96%, w2l 2 | -268 $/wk, DD -9.3%, ww +0, stops 0.08(0.08), b5 100%, w2l 2 | +46 $/wk, DD +14.2%, ww +1951, stops 0.04(0.04), b5 100%, w2l 2 | -225 $/wk, DD -5.9%, ww +0, stops 0.05(0.05), b5 87%, w2l 0 |

## 4. Strength, plainly
- Cells passing the tolerant gate in L3M+L6M (scope all): 8 of 74 scored; of them also passing every older window: 0.
- Gain of the better forecast over (a) (scope all, L6M, both maxDD cut and mean better than (a)): (b) 10 of 24 families, (c) 9 of 24 families. Chance for a coin flip would be about half.

## 5. Placebo (forecast shifted 11/23/37 trading days) and family null (forecast permuted within month, seeds 1-3) beside the finalists
| finalist | scope | real L6M | pl11 | pl23 | pl37 | perm1 | perm2 | perm3 |
|---|---|---|---|---|---|---|---|---|
| D5R13A_x | all | -739 $/wk, DD +14.4%, ww +10121, stops 10.92(10.99), b5 96%, w2l 0 | -739 $/wk, DD +14.4%, ww +10121, stops 10.92(10.99), b5 96%, w2l 0 | -739 $/wk, DD +14.4%, ww +10121, stops 10.92(10.99), b5 96%, w2l 0 | -739 $/wk, DD +14.4%, ww +10121, stops 10.92(10.99), b5 96%, w2l 0 | -739 $/wk, DD +14.4%, ww +10121, stops 10.92(10.99), b5 96%, w2l 0 | -739 $/wk, DD +14.4%, ww +10121, stops 10.92(10.99), b5 96%, w2l 0 | -739 $/wk, DD +14.4%, ww +10121, stops 10.92(10.99), b5 96%, w2l 0 |
| D7T_a | all | +731 $/wk, DD +7.2%, ww +3778, stops 10.84(10.99), b5 101%, w2l 0 | -231 $/wk, DD -4.5%, ww -2339, stops 11.15(10.99), b5 100%, w2l 0 | +1240 $/wk, DD +0.0%, ww +0, stops 11.15(10.99), b5 101%, w2l 0 | +374 $/wk, DD -8.5%, ww -4423, stops 11.11(10.99), b5 99%, w2l 0 | +1221 $/wk, DD -4.6%, ww -2398, stops 11.07(10.99), b5 99%, w2l 0 | +1614 $/wk, DD +7.2%, ww +3778, stops 11.18(10.99), b5 101%, w2l 0 | +697 $/wk, DD -4.5%, ww -2339, stops 11.15(10.99), b5 101%, w2l 0 |

## 6. What could not be hooked
- Dial 6 Keltner band multiple (K7 entry band, default 1.0 x ATR on 3-min bars) and chase_k limit (threshold 1.0 of the P7 ctxcut fresh/rechase cell choice) ARE hooked in ru_hooks.py (flag path: kb.bar patched per bar with the multiplier from the forecast ratio; ctxcut thr scaled per entry); identity proof TL3_RU_ID2 202610 = 598 trades / 25943.82 with both at neutral. Families D6KT/D6KC (Keltner), D6HT/D6HC (chase_k). Pullback trigger depth inside the signal engine (PbEngine) is still not hooked.
- Dial 3: the state-cut arm (points), the state-cut pct multiple (mult), the ctxcut cells (same _cell path) and the K7 flat cut d are scaled (families D3C, D3T = arm+flat; D3M = arm+flat+mult).
- Dial 4 uses the session range printed so far from NQ 1-min bars completed before the signal second; (ii) uses the same calculation live every second.
- Dial 8 JOINT and the PART 3 event/non-event split: appended when W-CAL flags land (autopilot/DS3_UWCAL.md) and top-3 per dial exist: section 7.

## 7. Joint (dial 8)
Not built yet.

## 8. PART 3: event days vs non-event days (dials scored separately)
Event day = W-CAL ev_day (any scheduled release/auction/chair/earnings; ~39% of days); high-impact = hi_day (~12%). Same exact runs, trades split by entry Globex day; mean is $/wk of the full window so event + non-event add up.

| family | fc | split | L6M | HOLD |
|---|---|---|---|---|
| D4I1 | a | event days | +51 $/wk, DD +23.9%, ww +9414, stops 3.23(4.11), b5 70%, w2l 0 | -1696 $/wk, DD +23.1%, ww +2404, stops 3.18(4.16), b5 69%, w2l 4 |
| D4I1 | a | non-event days | -6690 $/wk, DD +6.2%, ww -11383, stops 4.95(6.89), b5 68%, w2l 3 | -2936 $/wk, DD +40.7%, ww +17641, stops 4.49(6.50), b5 70%, w2l 5 |
| D4I1 | a | high-impact days | +1322 $/wk, DD +21.1%, ww +505, stops 0.80(1.26), b5 88%, w2l 0 | +649 $/wk, DD -13.0%, ww +6964, stops 1.07(1.42), b5 89%, w2l 1 |
| D4I1 | a | non-high days | -7961 $/wk, DD +4.6%, ww +12174, stops 7.38(9.74), b5 57%, w2l 4 | -5281 $/wk, DD +34.1%, ww +9662, stops 6.60(9.24), b5 66%, w2l 7 |
| D4I1 | b | event days | -1919 $/wk, DD -19.2%, ww +2003, stops 3.12(4.11), b5 53%, w2l 2 | -2880 $/wk, DD +22.3%, ww +2003, stops 2.78(4.16), b5 56%, w2l 6 |
| D4I1 | b | non-event days | -8406 $/wk, DD -10.8%, ww -20791, stops 4.79(6.89), b5 58%, w2l 3 | -4920 $/wk, DD +1.5%, ww -9155, stops 4.47(6.50), b5 65%, w2l 6 |
| D4I1 | b | high-impact days | -609 $/wk, DD -25.8%, ww -7684, stops 0.88(1.26), b5 71%, w2l 1 | -436 $/wk, DD -25.8%, ww +6285, stops 0.96(1.42), b5 76%, w2l 2 |
| D4I1 | b | non-high days | -9716 $/wk, DD +3.0%, ww +1842, stops 7.04(9.74), b5 46%, w2l 5 | -7364 $/wk, DD -8.5%, ww -5933, stops 6.29(9.24), b5 54%, w2l 9 |
| D4I1 | c | event days | +66 $/wk, DD +1.9%, ww +10920, stops 3.23(4.11), b5 68%, w2l 1 | -1314 $/wk, DD +40.7%, ww +3661, stops 2.88(4.16), b5 70%, w2l 4 |
| D4I1 | c | non-event days | -8342 $/wk, DD -65.9%, ww -9949, stops 4.91(6.89), b5 78%, w2l 3 | -3771 $/wk, DD -8.3%, ww +6649, stops 4.32(6.50), b5 81%, w2l 8 |
| D4I1 | c | high-impact days | +699 $/wk, DD +45.4%, ww +831, stops 0.80(1.26), b5 82%, w2l 0 | +261 $/wk, DD +5.6%, ww +7486, stops 0.94(1.42), b5 87%, w2l 1 |
| D4I1 | c | non-high days | -8975 $/wk, DD -61.5%, ww -265, stops 7.34(9.74), b5 66%, w2l 5 | -5346 $/wk, DD +7.7%, ww +9872, stops 6.25(9.24), b5 71%, w2l 8 |
| D4I125 | a | event days | -110 $/wk, DD -21.4%, ww +8979, stops 3.42(4.11), b5 71%, w2l 0 | -1709 $/wk, DD +12.8%, ww +2404, stops 3.36(4.16), b5 75%, w2l 3 |
| D4I125 | a | non-event days | -5544 $/wk, DD +15.1%, ww -6544, stops 5.33(6.89), b5 75%, w2l 3 | -2223 $/wk, DD +33.2%, ww +7930, stops 4.87(6.50), b5 77%, w2l 4 |
| D4I125 | a | high-impact days | +1214 $/wk, DD +21.7%, ww +505, stops 0.88(1.26), b5 89%, w2l 0 | +752 $/wk, DD -0.4%, ww +6964, stops 1.11(1.42), b5 90%, w2l 0 |
| D4I125 | a | non-high days | -6869 $/wk, DD +5.3%, ww +6092, stops 7.88(9.74), b5 63%, w2l 3 | -4685 $/wk, DD +18.9%, ww +814, stops 7.12(9.24), b5 72%, w2l 6 |
| D4I125 | b | event days | -1993 $/wk, DD -7.8%, ww +9018, stops 3.35(4.11), b5 54%, w2l 2 | -3131 $/wk, DD -21.0%, ww +2404, stops 3.11(4.16), b5 58%, w2l 5 |
| D4I125 | b | non-event days | -8081 $/wk, DD -21.1%, ww -20860, stops 5.14(6.89), b5 62%, w2l 3 | -5306 $/wk, DD +4.2%, ww -2316, stops 4.85(6.50), b5 67%, w2l 6 |
| D4I125 | b | high-impact days | +369 $/wk, DD +16.8%, ww +831, stops 0.91(1.26), b5 76%, w2l 1 | -299 $/wk, DD -29.1%, ww +6285, stops 1.04(1.42), b5 80%, w2l 2 |
| D4I125 | b | non-high days | -10444 $/wk, DD -6.6%, ww +691, stops 7.57(9.74), b5 50%, w2l 5 | -8138 $/wk, DD -1.0%, ww +907, stops 6.92(9.24), b5 59%, w2l 9 |
| D4I125 | c | event days | -154 $/wk, DD -5.5%, ww +9966, stops 3.31(4.11), b5 65%, w2l 2 | -1735 $/wk, DD +36.2%, ww +1535, stops 3.05(4.16), b5 76%, w2l 4 |
| D4I125 | c | non-event days | -9337 $/wk, DD -57.0%, ww -8979, stops 5.14(6.89), b5 76%, w2l 3 | -5454 $/wk, DD -43.1%, ww -10632, stops 4.72(6.50), b5 76%, w2l 6 |
| D4I125 | c | high-impact days | +818 $/wk, DD +45.4%, ww +831, stops 0.80(1.26), b5 85%, w2l 0 | +193 $/wk, DD +6.5%, ww +6970, stops 1.02(1.42), b5 89%, w2l 0 |
| D4I125 | c | non-high days | -10308 $/wk, DD -51.0%, ww -265, stops 7.65(9.74), b5 62%, w2l 5 | -7381 $/wk, DD -11.5%, ww -7409, stops 6.75(9.24), b5 65%, w2l 6 |
| D4II075 | a | event days | -459 $/wk, DD +12.7%, ww -1473, stops 3.65(4.11), b5 93%, w2l 1 | n/a |
| D4II075 | a | non-event days | -5079 $/wk, DD -1.7%, ww -4633, stops 6.58(6.89), b5 93%, w2l 2 | n/a |
| D4II075 | a | high-impact days | -410 $/wk, DD +10.0%, ww +831, stops 1.10(1.26), b5 88%, w2l 1 | n/a |
| D4II075 | a | non-high days | -5127 $/wk, DD -23.1%, ww -17856, stops 9.13(9.74), b5 92%, w2l 3 | n/a |
| D4II075 | b | event days | -56 $/wk, DD +15.7%, ww +11977, stops 3.65(4.11), b5 91%, w2l 1 | n/a |
| D4II075 | b | non-event days | -4612 $/wk, DD +16.1%, ww -5092, stops 6.47(6.89), b5 78%, w2l 1 | n/a |
| D4II075 | b | high-impact days | -806 $/wk, DD +13.2%, ww +831, stops 1.03(1.26), b5 82%, w2l 1 | n/a |
| D4II075 | b | non-high days | -3863 $/wk, DD -28.3%, ww -4887, stops 9.09(9.74), b5 80%, w2l 2 | n/a |
| D4II075 | c | event days | +269 $/wk, DD +22.1%, ww +10635, stops 3.65(4.11), b5 98%, w2l 2 | n/a |
| D4II075 | c | non-event days | -2441 $/wk, DD +38.6%, ww -6350, stops 6.32(6.89), b5 95%, w2l 1 | n/a |
| D4II075 | c | high-impact days | -44 $/wk, DD +21.4%, ww +831, stops 1.10(1.26), b5 89%, w2l 1 | n/a |
| D4II075 | c | non-high days | -2127 $/wk, DD +6.1%, ww -7317, stops 8.86(9.74), b5 95%, w2l 1 | n/a |
| D5SK13F | a | event days | -1307 $/wk, DD +0.0%, ww +0, stops 3.27(4.11), b5 83%, w2l 1 | -497 $/wk, DD +33.3%, ww +0, stops 3.07(4.16), b5 77%, w2l 1 |
| D5SK13F | a | non-event days | -5227 $/wk, DD +9.9%, ww +1554, stops 5.33(6.89), b5 73%, w2l 1 | -3238 $/wk, DD -13.5%, ww -8705, stops 5.12(6.50), b5 68%, w2l 2 |
| D5SK13F | a | high-impact days | -1371 $/wk, DD +1.4%, ww +0, stops 1.10(1.26), b5 79%, w2l 1 | +204 $/wk, DD +1.4%, ww +0, stops 1.02(1.42), b5 79%, w2l 1 |
| D5SK13F | a | non-high days | -5163 $/wk, DD -0.3%, ww +2554, stops 7.49(9.74), b5 67%, w2l 2 | -3939 $/wk, DD -11.3%, ww -5482, stops 7.17(9.24), b5 62%, w2l 5 |
| D5SK13F | b | event days | -588 $/wk, DD +8.2%, ww +6977, stops 3.23(4.11), b5 86%, w2l 1 | -1248 $/wk, DD +32.6%, ww +1967, stops 3.03(4.16), b5 81%, w2l 3 |
| D5SK13F | b | non-event days | -5744 $/wk, DD +19.3%, ww -4188, stops 4.64(6.89), b5 89%, w2l 4 | -2186 $/wk, DD +51.2%, ww +25137, stops 4.32(6.50), b5 83%, w2l 6 |
| D5SK13F | b | high-impact days | -522 $/wk, DD -8.5%, ww -2356, stops 0.88(1.26), b5 89%, w2l 1 | +614 $/wk, DD -8.5%, ww +0, stops 0.94(1.42), b5 89%, w2l 1 |
| D5SK13F | b | non-high days | -5810 $/wk, DD +9.8%, ww +11385, stops 7.00(9.74), b5 81%, w2l 5 | -4048 $/wk, DD +47.9%, ww +21358, stops 6.41(9.24), b5 78%, w2l 9 |
| D5SK13F | c | event days | -2606 $/wk, DD -12.6%, ww +7196, stops 3.04(4.11), b5 75%, w2l 2 | -2321 $/wk, DD +31.9%, ww +1967, stops 2.82(4.16), b5 69%, w2l 3 |
| D5SK13F | c | non-event days | -5191 $/wk, DD +5.3%, ww +0, stops 4.95(6.89), b5 86%, w2l 3 | -2717 $/wk, DD +39.6%, ww +28406, stops 4.62(6.50), b5 80%, w2l 7 |
| D5SK13F | c | high-impact days | -1307 $/wk, DD -21.3%, ww -2356, stops 0.80(1.26), b5 79%, w2l 3 | -126 $/wk, DD -21.3%, ww +0, stops 0.82(1.42), b5 67%, w2l 3 |
| D5SK13F | c | non-high days | -6490 $/wk, DD +3.9%, ww +5013, stops 7.19(9.74), b5 81%, w2l 4 | -4911 $/wk, DD +41.0%, ww +23651, stops 6.62(9.24), b5 77%, w2l 8 |
| D5R13F | a | event days | -454 $/wk, DD +0.0%, ww +0, stops 4.07(4.11), b5 93%, w2l 0 | +7 $/wk, DD +14.9%, ww +0, stops 4.08(4.16), b5 91%, w2l 0 |
| D5R13F | a | non-event days | -2368 $/wk, DD +0.9%, ww -88, stops 6.70(6.89), b5 88%, w2l 1 | -1747 $/wk, DD -12.1%, ww -5886, stops 6.46(6.50), b5 85%, w2l 1 |
| D5R13F | a | high-impact days | -170 $/wk, DD +8.0%, ww +0, stops 1.26(1.26), b5 91%, w2l 1 | +310 $/wk, DD +8.0%, ww +0, stops 1.38(1.42), b5 91%, w2l 1 |
| D5R13F | a | non-high days | -2653 $/wk, DD -3.4%, ww -2997, stops 9.51(9.74), b5 87%, w2l 1 | -2050 $/wk, DD +3.8%, ww -2664, stops 9.17(9.24), b5 83%, w2l 2 |
| D5R13F | b | event days | +614 $/wk, DD +8.2%, ww +10378, stops 4.11(4.11), b5 95%, w2l 0 | +461 $/wk, DD +16.5%, ww +1967, stops 4.12(4.16), b5 93%, w2l 0 |
| D5R13F | b | non-event days | -2206 $/wk, DD +5.2%, ww -1120, stops 6.70(6.89), b5 95%, w2l 0 | +41 $/wk, DD +41.4%, ww +22407, stops 6.42(6.50), b5 93%, w2l 0 |
| D5R13F | b | high-impact days | +348 $/wk, DD -4.1%, ww -685, stops 1.29(1.26), b5 95%, w2l 1 | +446 $/wk, DD -4.1%, ww +0, stops 1.42(1.42), b5 95%, w2l 1 |
| D5R13F | b | non-high days | -1939 $/wk, DD +17.8%, ww +4842, stops 9.51(9.74), b5 93%, w2l 1 | +55 $/wk, DD +34.2%, ww +10865, stops 9.13(9.24), b5 91%, w2l 1 |
| D5R13F | c | event days | -97 $/wk, DD +9.9%, ww +10378, stops 4.18(4.11), b5 89%, w2l 1 | +160 $/wk, DD +16.5%, ww +1967, stops 4.14(4.16), b5 88%, w2l 1 |
| D5R13F | c | non-event days | -1892 $/wk, DD +8.9%, ww +0, stops 6.66(6.89), b5 95%, w2l 0 | -541 $/wk, DD +33.4%, ww +22407, stops 6.39(6.50), b5 91%, w2l 1 |
| D5R13F | c | high-impact days | +206 $/wk, DD +3.5%, ww -685, stops 1.33(1.26), b5 91%, w2l 1 | +305 $/wk, DD +3.5%, ww +0, stops 1.44(1.42), b5 86%, w2l 1 |
| D5R13F | c | non-high days | -2195 $/wk, DD +19.3%, ww -2386, stops 9.51(9.74), b5 93%, w2l 1 | -685 $/wk, DD +34.2%, ww +18631, stops 9.09(9.24), b5 91%, w2l 1 |
| D4II1 | a | event days | -1388 $/wk, DD -22.6%, ww -1680, stops 3.77(4.11), b5 99%, w2l 1 | -278 $/wk, DD +25.9%, ww -1680, stops 3.84(4.16), b5 95%, w2l 3 |
| D4II1 | a | non-event days | -3537 $/wk, DD +6.4%, ww +3978, stops 6.70(6.89), b5 91%, w2l 2 | -3673 $/wk, DD -53.7%, ww -10251, stops 6.12(6.50), b5 83%, w2l 4 |
| D4II1 | a | high-impact days | -57 $/wk, DD +17.5%, ww +505, stops 1.14(1.26), b5 92%, w2l 0 | -9 $/wk, DD +6.5%, ww +11687, stops 1.34(1.42), b5 90%, w2l 0 |
| D4II1 | a | non-high days | -4868 $/wk, DD -37.7%, ww -12742, stops 9.32(9.74), b5 86%, w2l 2 | -3942 $/wk, DD -15.6%, ww -7029, stops 8.61(9.24), b5 82%, w2l 5 |
| D4II1 | b | event days | +791 $/wk, DD +43.1%, ww +10635, stops 3.77(4.11), b5 95%, w2l 1 | -60 $/wk, DD +42.3%, ww +4105, stops 3.72(4.16), b5 80%, w2l 4 |
| D4II1 | b | non-event days | -3097 $/wk, DD -0.6%, ww -9286, stops 6.77(6.89), b5 90%, w2l 1 | -2414 $/wk, DD -1.1%, ww -3715, stops 6.39(6.50), b5 85%, w2l 2 |
| D4II1 | b | high-impact days | -683 $/wk, DD +18.2%, ww +831, stops 0.99(1.26), b5 79%, w2l 1 | +73 $/wk, DD +18.2%, ww +11582, stops 1.23(1.42), b5 84%, w2l 1 |
| D4II1 | b | non-high days | -1623 $/wk, DD -0.9%, ww -8048, stops 9.55(9.74), b5 91%, w2l 2 | -2547 $/wk, DD -1.9%, ww -493, stops 8.88(9.24), b5 87%, w2l 5 |
| D4II1 | c | event days | +1224 $/wk, DD +33.8%, ww +9572, stops 3.73(4.11), b5 106%, w2l 1 | -539 $/wk, DD +5.5%, ww -2856, stops 3.68(4.16), b5 92%, w2l 3 |
| D4II1 | c | non-event days | -1940 $/wk, DD +35.9%, ww -8257, stops 6.43(6.89), b5 100%, w2l 1 | -1547 $/wk, DD +5.0%, ww -405, stops 6.04(6.50), b5 98%, w2l 2 |
| D4II1 | c | high-impact days | +387 $/wk, DD +26.2%, ww +831, stops 1.07(1.26), b5 95%, w2l 0 | +740 $/wk, DD +20.0%, ww +10611, stops 1.19(1.42), b5 96%, w2l 0 |
| D4II1 | c | non-high days | -1103 $/wk, DD -3.3%, ww -5287, stops 9.09(9.74), b5 99%, w2l 2 | -2825 $/wk, DD -0.9%, ww +2818, stops 8.53(9.24), b5 97%, w2l 6 |
| D4II125 | a | event days | -1268 $/wk, DD -26.7%, ww -2765, stops 3.92(4.11), b5 101%, w2l 1 | -763 $/wk, DD +19.1%, ww -2765, stops 3.97(4.16), b5 98%, w2l 4 |
| D4II125 | a | non-event days | -1878 $/wk, DD +21.5%, ww -224, stops 6.66(6.89), b5 99%, w2l 1 | -2070 $/wk, DD -19.7%, ww +4373, stops 6.21(6.50), b5 90%, w2l 3 |
| D4II125 | a | high-impact days | -83 $/wk, DD +14.8%, ww +505, stops 1.18(1.26), b5 93%, w2l 0 | -184 $/wk, DD +13.6%, ww +3152, stops 1.40(1.42), b5 92%, w2l 0 |
| D4II125 | a | non-high days | -3064 $/wk, DD -32.0%, ww -7046, stops 9.40(9.74), b5 94%, w2l 1 | -2650 $/wk, DD -10.1%, ww +1604, stops 8.78(9.24), b5 90%, w2l 5 |
| D4II125 | b | event days | +15 $/wk, DD +6.3%, ww +10920, stops 3.84(4.11), b5 101%, w2l 1 | -44 $/wk, DD +43.4%, ww +5408, stops 3.85(4.16), b5 87%, w2l 3 |
| D4II125 | b | non-event days | -3159 $/wk, DD -2.3%, ww -8495, stops 6.81(6.89), b5 91%, w2l 0 | -2526 $/wk, DD -8.6%, ww +2376, stops 6.48(6.50), b5 86%, w2l 1 |
| D4II125 | b | high-impact days | -390 $/wk, DD +16.8%, ww +831, stops 1.07(1.26), b5 86%, w2l 1 | +405 $/wk, DD +16.8%, ww +11687, stops 1.27(1.42), b5 88%, w2l 1 |
| D4II125 | b | non-high days | -2754 $/wk, DD +5.1%, ww -4675, stops 9.59(9.74), b5 89%, w2l 1 | -2975 $/wk, DD +3.5%, ww +5599, stops 9.07(9.24), b5 85%, w2l 4 |
| D4II125 | c | event days | +601 $/wk, DD +28.1%, ww +7556, stops 3.77(4.11), b5 103%, w2l 1 | -326 $/wk, DD +35.4%, ww -1250, stops 3.76(4.16), b5 94%, w2l 3 |
| D4II125 | c | non-event days | -1445 $/wk, DD +35.0%, ww -5922, stops 6.47(6.89), b5 104%, w2l 1 | -1159 $/wk, DD +4.8%, ww -1949, stops 6.06(6.50), b5 100%, w2l 3 |
| D4II125 | c | high-impact days | +456 $/wk, DD +26.1%, ww +831, stops 1.07(1.26), b5 97%, w2l 0 | +970 $/wk, DD +23.8%, ww +12050, stops 1.21(1.42), b5 103%, w2l 0 |
| D4II125 | c | non-high days | -1300 $/wk, DD -7.7%, ww -1093, stops 9.17(9.74), b5 102%, w2l 2 | -2456 $/wk, DD -0.4%, ww +1273, stops 8.61(9.24), b5 100%, w2l 5 |
| D4III1 | a | event days | -2614 $/wk, DD -39.5%, ww +33, stops 3.69(4.11), b5 78%, w2l 0 | -1160 $/wk, DD +10.0%, ww +33, stops 3.76(4.16), b5 84%, w2l 1 |
| D4III1 | a | non-event days | -1257 $/wk, DD +29.9%, ww -3015, stops 6.47(6.89), b5 89%, w2l 1 | -583 $/wk, DD +1.5%, ww +6764, stops 5.95(6.50), b5 86%, w2l 2 |
| D4III1 | a | high-impact days | -600 $/wk, DD +5.0%, ww +505, stops 1.07(1.26), b5 85%, w2l 1 | +180 $/wk, DD +5.0%, ww +4098, stops 1.23(1.42), b5 92%, w2l 1 |
| D4III1 | a | non-high days | -3272 $/wk, DD -1.5%, ww +678, stops 9.09(9.74), b5 81%, w2l 0 | -1924 $/wk, DD -7.7%, ww +5652, stops 8.48(9.24), b5 84%, w2l 1 |
| D4III1 | b | event days | -2593 $/wk, DD +8.1%, ww +2537, stops 3.61(4.11), b5 70%, w2l 0 | -1791 $/wk, DD +18.4%, ww +2537, stops 3.72(4.16), b5 71%, w2l 1 |
| D4III1 | b | non-event days | -612 $/wk, DD +29.4%, ww -2875, stops 6.58(6.89), b5 83%, w2l 1 | +97 $/wk, DD +6.8%, ww +2260, stops 6.02(6.50), b5 82%, w2l 2 |
| D4III1 | b | high-impact days | -1430 $/wk, DD +19.5%, ww -402, stops 1.03(1.26), b5 75%, w2l 2 | -859 $/wk, DD +18.5%, ww +821, stops 1.25(1.42), b5 84%, w2l 3 |
| D4III1 | b | non-high days | -1774 $/wk, DD -8.1%, ww -3969, stops 9.17(9.74), b5 77%, w2l 1 | -835 $/wk, DD -0.2%, ww +5482, stops 8.50(9.24), b5 79%, w2l 3 |
| D4III1 | c | event days | -1138 $/wk, DD -24.3%, ww -141, stops 3.69(4.11), b5 76%, w2l 0 | -641 $/wk, DD +24.9%, ww -141, stops 3.72(4.16), b5 83%, w2l 1 |
| D4III1 | c | non-event days | -2082 $/wk, DD +15.4%, ww -6168, stops 6.47(6.89), b5 92%, w2l 1 | -677 $/wk, DD +6.1%, ww +1866, stops 5.98(6.50), b5 93%, w2l 2 |
| D4III1 | c | high-impact days | -647 $/wk, DD +26.9%, ww -580, stops 1.03(1.26), b5 86%, w2l 1 | -313 $/wk, DD +18.6%, ww +2785, stops 1.23(1.42), b5 94%, w2l 1 |
| D4III1 | c | non-high days | -2573 $/wk, DD -11.8%, ww -3048, stops 9.13(9.74), b5 83%, w2l 1 | -1005 $/wk, DD +0.2%, ww +5088, stops 8.48(9.24), b5 85%, w2l 3 |
## Target capped at the forecast
**VERDICT (plain, not a PASS; FIRST PASS; 15 of 26 global exact cap cells scored in L3M, per book x session exact cells still running): planted-edge check PASSED through the exact engine (look-ahead oracle target 0.9 x realised MFE: +85531 $/wk, DD +67.0%, ww +64263; this is a mechanism check, NOT a result); the reachable move is only weakly forecastable (R2 on ln MFE 0.03-0.14, quantile calibration good); in the exact L3M cells the cap at the forecast 50th-percentile move (horizon = 75th-percentile holding time) gives +1486 $/wk, DD -0.5%, ww -240 and the 75th-percentile cap +177 $/wk, DD +0.0%, ww +0, the remaining-range caps cut drawdown (own k1.0 -6226 $/wk, DD +27.0%, ww +12290; HAR k1.0 -7259 $/wk, DD +39.4%, ww +17319) but cost thousands per week. Best exact L3M cap cell inside the mean gate by DD: PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time (DD +7.9%, -120 $/wk). L6M/HOLD/older still to run before any verdict.**

Planted-edge check (H1) for the capping mechanism: cells `tcoracle0.9` / `0.6` set the target to 0.9 / 0.6 x the REALISED maximum favourable move (look-ahead, only to prove the mechanism can show an edge through the exact engine); they must come out strongly positive. Status below in the exact table. Until they do, an exact cap verdict is not stated.

Definition. Reachable move = maximum favourable excursion from the signal-second bar close over the book-session holding horizon H (H50/H75 = median / 75th percentile holding time of that book+session, causal), points. Model: walk-forward ridge (14-day blocks, expanding, min 90 days, per session) on ln((MFE+2)/price) from the Dial 10 own-bar inputs (last 15/30/60/120 min range and vol, same-clock normal, own session level, range used so far, elapsed fraction) plus the side-aware room in the session range so far; quantiles q = fitted + empirical training-residual quantile (50/60/75/90). Cap: target = min(book target 60 pts [58 after fills], q-quantile), stop, lots and every other level unchanged. Remaining-range cap: target = min(book target, k x (session range forecast - range printed so far)), forecast = own (price x exp(sf20), mean of the last 20 sessions) or T-RANGE2 HAR (fc_r2_har, available-epoch checked). Small caps (< 30 pts = 0.5 x stop): take / skip / half. EV target: argmax over T in [20, book target or 300] of T x P(MFE>=T) - stop x (1-P) with the lognormal forecast (ignores the stop-first ordering, so optimistic). Extension: if the forecast median MFE is >= m x book target, target = min(q50, 2 x book target). Lots/base basis: dollars are BASE lots (live x1.75 = multiply by 1.75); fee columns $4.84 beside raw $1.18 where shown.

### Item 1: calibration of the forecast quantiles (share of trades whose realized MFE exceeded the forecast quantile; a q-quantile should be exceeded 1-q of the time = 0.50 / 0.40 / 0.25 / 0.10) and R2 of ln MFE, per session
| H | session | window | n | >q50 | >q60 | >q75 | >q90 | R2 ln MFE | median q75 (pts) | share q75 < 60 |
|---|---|---|---|---|---|---|---|---|---|---|
| 50 | asia | older (<2026-05) | 5119 | 0.51 | 0.41 | 0.26 | 0.12 | 0.121 | 80 | 0.222 |
| 50 | asia | L6M | 2006 | 0.49 | 0.38 | 0.23 | 0.08 | 0.058 | 111 | 0.047 |
| 50 | asia | L3M | 875 | 0.46 | 0.34 | 0.20 | 0.07 | -0.014 | 90 | 0.098 |
| 50 | london | older (<2026-05) | 4892 | 0.51 | 0.41 | 0.26 | 0.11 | 0.142 | 62 | 0.438 |
| 50 | london | L6M | 1406 | 0.48 | 0.37 | 0.23 | 0.08 | 0.028 | 76 | 0.166 |
| 50 | london | L3M | 673 | 0.48 | 0.37 | 0.24 | 0.07 | -0.008 | 68 | 0.247 |
| 50 | nyam | older (<2026-05) | 4142 | 0.47 | 0.38 | 0.24 | 0.11 | 0.077 | 63 | 0.397 |
| 50 | nyam | L6M | 600 | 0.51 | 0.40 | 0.24 | 0.09 | 0.097 | 83 | 0.157 |
| 50 | nyam | L3M | 271 | 0.51 | 0.38 | 0.20 | 0.06 | 0.077 | 68 | 0.258 |
| 50 | nypm | older (<2026-05) | 817 | 0.48 | 0.40 | 0.26 | 0.13 | 0.073 | 62 | 0.419 |
| 50 | nypm | L6M | 150 | 0.59 | 0.50 | 0.33 | 0.13 | 0.221 | 71 | 0.307 |
| 50 | nypm | L3M | 56 | 0.50 | 0.36 | 0.21 | 0.09 | 0.104 | 54 | 0.589 |
| 50 | all | older (<2026-05) | 14970 | 0.50 | 0.40 | 0.26 | 0.12 | 0.123 | 68 | 0.352 |
| 50 | all | L6M | 4162 | 0.49 | 0.38 | 0.23 | 0.08 | 0.080 | 91 | 0.113 |
| 50 | all | L3M | 1875 | 0.47 | 0.36 | 0.21 | 0.07 | 0.014 | 76 | 0.189 |
| 75 | asia | older (<2026-05) | 5119 | 0.52 | 0.41 | 0.26 | 0.12 | 0.134 | 122 | 0.032 |
| 75 | asia | L6M | 2006 | 0.50 | 0.40 | 0.24 | 0.08 | 0.027 | 178 | 0.000 |
| 75 | asia | L3M | 875 | 0.45 | 0.35 | 0.20 | 0.05 | -0.016 | 156 | 0.000 |
| 75 | london | older (<2026-05) | 4891 | 0.51 | 0.42 | 0.27 | 0.11 | 0.157 | 101 | 0.100 |
| 75 | london | L6M | 1406 | 0.49 | 0.37 | 0.21 | 0.08 | 0.069 | 118 | 0.001 |
| 75 | london | L3M | 673 | 0.49 | 0.38 | 0.21 | 0.09 | 0.025 | 108 | 0.000 |
| 75 | nyam | older (<2026-05) | 4142 | 0.48 | 0.38 | 0.23 | 0.10 | 0.065 | 91 | 0.081 |
| 75 | nyam | L6M | 600 | 0.50 | 0.40 | 0.24 | 0.10 | 0.098 | 125 | 0.015 |
| 75 | nyam | L3M | 271 | 0.44 | 0.34 | 0.19 | 0.05 | 0.051 | 103 | 0.015 |
| 75 | nypm | older (<2026-05) | 812 | 0.49 | 0.37 | 0.26 | 0.11 | 0.043 | 87 | 0.095 |
| 75 | nypm | L6M | 150 | 0.53 | 0.46 | 0.34 | 0.17 | 0.179 | 117 | 0.013 |
| 75 | nypm | L3M | 56 | 0.41 | 0.30 | 0.21 | 0.07 | -0.076 | 93 | 0.036 |
| 75 | all | older (<2026-05) | 14964 | 0.51 | 0.40 | 0.25 | 0.11 | 0.131 | 102 | 0.071 |
| 75 | all | L6M | 4162 | 0.50 | 0.39 | 0.23 | 0.09 | 0.079 | 149 | 0.003 |
| 75 | all | L3M | 1875 | 0.46 | 0.36 | 0.20 | 0.06 | 0.032 | 128 | 0.003 |

### Items 3 and 4 (and 2): offline replay of the caps on the JN05W2 trade paths, all 43 months (estimate: 1-min paths, cap counted only before the exit bar, so cut/stop ordering is conservative; the exact cells below decide). d mean $/wk and DD cut % vs JN05W2 on the same trades, scope all, then per session for the cap with the most trades capped
| cap | small-cap rule | scope | window | d mean $/wk (live x1.75) | DD cut % | d worst week | d stops/wk | share capped | share where cap hit |
|---|---|---|---|---|---|---|---|---|---|
| q50_H50 | take | all | L3M | +409 (+715) | -3.9 | -1411 | +0.00 | 0.82 | 0.45 |
| q50_H50 | take | all | L6M | -96 (-169) | -3.9 | -1411 | +0.00 | 0.62 | 0.33 |
| q50_H50 | take | all | OLDER | -1795 (-3141) | +12.0 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | skip | all | L3M | -1581 (-2767) | -5.0 | -1996 | +0.00 | 0.82 | 0.45 |
| q50_H50 | skip | all | L6M | -1445 (-2528) | -5.0 | -1996 | +0.00 | 0.62 | 0.33 |
| q50_H50 | skip | all | OLDER | -2271 (-3975) | +17.4 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | half | all | L3M | -586 (-1026) | -4.4 | -1704 | +0.00 | 0.82 | 0.45 |
| q50_H50 | half | all | L6M | -771 (-1348) | -4.4 | -1704 | +0.00 | 0.62 | 0.33 |
| q50_H50 | half | all | OLDER | -2033 (-3558) | +16.5 | +13127 | +0.00 | 0.80 | 0.45 |
| q60_H50 | take | all | L3M | -1525 (-2668) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | take | all | L6M | -839 (-1469) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | take | all | OLDER | -1296 (-2267) | +12.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | skip | all | L3M | -3272 (-5726) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | skip | all | L6M | -1811 (-3170) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | skip | all | OLDER | -1648 (-2885) | +8.8 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | half | all | L3M | -2398 (-4197) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | half | all | L6M | -1325 (-2319) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | half | all | OLDER | -1472 (-2576) | +10.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q75_H50 | take | all | L3M | +414 (+725) | -0.4 | -214 | +0.00 | 0.21 | 0.11 |
| q75_H50 | take | all | L6M | -44 (-77) | -0.4 | -214 | +0.00 | 0.13 | 0.06 |
| q75_H50 | take | all | OLDER | -719 (-1258) | -1.1 | +13801 | +0.00 | 0.37 | 0.18 |
| q90_H50 | take | all | L3M | +191 (+334) | +0.0 | +0 | +0.00 | 0.02 | 0.01 |
| q90_H50 | take | all | L6M | +142 (+249) | +0.0 | +0 | +0.00 | 0.01 | 0.01 |
| q90_H50 | take | all | OLDER | -169 (-296) | -1.8 | +1686 | +0.00 | 0.08 | 0.03 |
| q50_H75 | take | all | L3M | +128 (+225) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | take | all | L6M | +624 (+1092) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | take | all | OLDER | -931 (-1628) | -13.1 | +11346 | +0.00 | 0.51 | 0.26 |
| q50_H75 | skip | all | L3M | +178 (+312) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | skip | all | L6M | +685 (+1198) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | skip | all | OLDER | -1302 (-2279) | -4.6 | +14384 | +0.00 | 0.51 | 0.26 |
| q50_H75 | half | all | L3M | +153 (+268) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | half | all | L6M | +654 (+1145) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | half | all | OLDER | -1116 (-1954) | -8.8 | +12865 | +0.00 | 0.51 | 0.26 |
| q60_H75 | take | all | L3M | +830 (+1452) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | take | all | L6M | +379 (+664) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | take | all | OLDER | -478 (-836) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | skip | all | L3M | +958 (+1677) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | skip | all | L6M | +421 (+737) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | skip | all | OLDER | -402 (-703) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | half | all | L3M | +894 (+1564) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | half | all | L6M | +400 (+700) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | half | all | OLDER | -440 (-769) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q75_H75 | take | all | L3M | +236 (+413) | +0.0 | +0 | +0.00 | 0.01 | 0.00 |
| q75_H75 | take | all | L6M | +105 (+185) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q75_H75 | take | all | OLDER | -255 (-446) | -1.9 | +1485 | +0.00 | 0.08 | 0.04 |
| q90_H75 | take | all | L3M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | L6M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | OLDER | +10 (+18) | -0.4 | +0 | +0.00 | 0.01 | 0.00 |
| rem_own_k0.5 | take | all | L3M | -6674 (-11680) | +8.8 | -1861 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | take | all | L6M | -13204 (-23108) | +8.7 | -1861 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | take | all | OLDER | -7381 (-12916) | -40.2 | +20529 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | skip | all | L3M | -5271 (-9225) | +21.7 | +2982 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | skip | all | L6M | -10625 (-18594) | +21.7 | +2982 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | skip | all | OLDER | -6272 (-10977) | +17.3 | +21712 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | half | all | L3M | -5973 (-10452) | +16.3 | +560 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | half | all | L6M | -11915 (-20851) | +16.3 | +560 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | half | all | OLDER | -6827 (-11946) | +0.6 | +23150 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.75 | take | all | L3M | -7140 (-12494) | +9.6 | +3294 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | take | all | L6M | -10636 (-18614) | +9.6 | +3294 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | take | all | OLDER | -5846 (-10230) | -24.0 | +12208 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | skip | all | L3M | -3661 (-6406) | +10.3 | +4045 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | skip | all | L6M | -6650 (-11638) | +10.3 | +4045 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | skip | all | OLDER | -3856 (-6749) | +16.1 | +19073 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | half | all | L3M | -5400 (-9450) | +13.0 | +3670 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | half | all | L6M | -8643 (-15126) | +13.0 | +3670 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | half | all | OLDER | -4851 (-8489) | +13.0 | +20157 | +0.00 | 0.73 | 0.53 |
| rem_own_k1.0 | take | all | L3M | -5516 (-9653) | +18.3 | +9104 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | take | all | L6M | -8765 (-15339) | +18.3 | +9104 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | take | all | OLDER | -5714 (-9999) | -58.2 | +11926 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | skip | all | L3M | -3265 (-5714) | +15.0 | +8858 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | skip | all | L6M | -5683 (-9944) | +15.0 | +8858 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | skip | all | OLDER | -3872 (-6775) | -61.0 | +20250 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | half | all | L3M | -4391 (-7683) | +18.5 | +8981 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | half | all | L6M | -7224 (-12642) | +18.5 | +8981 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | half | all | OLDER | -4793 (-8387) | -58.0 | +21393 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.25 | take | all | L3M | -3112 (-5446) | +24.4 | +13750 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | take | all | L6M | -8275 (-14481) | +24.4 | +13750 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | take | all | OLDER | -5400 (-9450) | -15.5 | +4336 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | skip | all | L3M | -456 (-797) | +22.4 | +13720 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | skip | all | L6M | -4232 (-7405) | +22.4 | +13720 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | skip | all | OLDER | -3310 (-5792) | -36.4 | +22803 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | half | all | L3M | -1784 (-3121) | +25.2 | +15286 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | half | all | L6M | -6253 (-10943) | +25.2 | +15286 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | half | all | OLDER | -4355 (-7621) | -18.3 | +15544 | +0.00 | 0.54 | 0.41 |

Per session, q60 H75 take-anyway and remaining-range k=1.25 (own):
| cap | session | window | d mean $/wk | DD cut % | d worst week | share capped |
|---|---|---|---|---|---|---|
| q60_H75 | asia | L3M | +221 | +0.0 | +0 | 0.02 |
| q60_H75 | asia | L6M | +110 | +0.0 | +0 | 0.01 |
| q60_H75 | asia | OLDER | -124 | -0.0 | +0 | 0.23 |
| q60_H75 | london | L3M | +745 | +3.8 | +0 | 0.16 |
| q60_H75 | london | L6M | +330 | +3.8 | +0 | 0.12 |
| q60_H75 | london | OLDER | -294 | -2.1 | +0 | 0.35 |
| q60_H75 | nyam | L3M | +61 | -7.2 | +0 | 0.15 |
| q60_H75 | nyam | L6M | -14 | +0.0 | +0 | 0.10 |
| q60_H75 | nyam | OLDER | -37 | -6.0 | +1403 | 0.37 |
| q60_H75 | nypm | L3M | -197 | -0.0 | +0 | 0.41 |
| q60_H75 | nypm | L6M | -47 | +0.0 | +0 | 0.20 |
| q60_H75 | nypm | OLDER | -22 | -5.4 | +0 | 0.33 |
| rem_own_k1.25 | asia | L3M | -4547 | +35.2 | +434 | 0.37 |
| rem_own_k1.25 | asia | L6M | -6717 | +27.1 | +434 | 0.38 |
| rem_own_k1.25 | asia | OLDER | -4532 | -27.4 | +10774 | 0.62 |
| rem_own_k1.25 | london | L3M | +2278 | +46.3 | +12347 | 0.24 |
| rem_own_k1.25 | london | L6M | +1196 | +46.3 | +12347 | 0.30 |
| rem_own_k1.25 | london | OLDER | -510 | +12.9 | +3024 | 0.51 |
| rem_own_k1.25 | nyam | L3M | -650 | +20.0 | +0 | 0.24 |
| rem_own_k1.25 | nyam | L6M | -2127 | -8.9 | +1531 | 0.39 |
| rem_own_k1.25 | nyam | OLDER | -53 | +10.3 | +7327 | 0.47 |
| rem_own_k1.25 | nypm | L3M | -192 | +21.8 | +1203 | 0.45 |
| rem_own_k1.25 | nypm | L6M | -627 | +21.8 | +1203 | 0.50 |
| rem_own_k1.25 | nypm | OLDER | -304 | -2.4 | -831 | 0.50 |

### Item 4 per book x session (all 43 months): trades whose 60-pt target lies beyond the forecast quantile, their fixed-target result, the capped replay, and how far trades run past the cap
| book | session | cap | trades | share beyond | fixed-target hit rate | fixed avg $/trade | capped avg $/trade | avg points run past cap |
|---|---|---|---|---|---|---|---|---|
| A7 | asia | q50_H75 | 1156 | 0.25 | 0.50 | 60 | 87 | 10.4 |
| A7 | asia | q60_H75 | 1156 | 0.13 | 0.47 | 4 | 26 | 8.8 |
| A7 | asia | q75_H75 | 1156 | 0.03 | 0.48 | 19 | 6 | 11.1 |
| A7 | asia | rem_own_k0.75 | 1156 | 0.74 | 0.52 | 126 | 22 | 32.9 |
| H7 | asia | q50_H75 | 700 | 0.33 | 0.49 | 164 | 181 | 11.3 |
| H7 | asia | q60_H75 | 700 | 0.18 | 0.56 | 447 | 414 | 10.7 |
| H7 | asia | q75_H75 | 700 | 0.02 | 0.50 | -318 | -267 | 16.1 |
| H7 | asia | rem_own_k0.75 | 700 | 0.71 | 0.48 | 208 | 55 | 27.8 |
| H7 | nyam | q50_H75 | 348 | 0.49 | 0.46 | 84 | 25 | 8.9 |
| H7 | nyam | q60_H75 | 348 | 0.25 | 0.47 | 96 | 46 | 7.4 |
| H7 | nyam | q75_H75 | 348 | 0.06 | 0.33 | -113 | -12 | 4.7 |
| H7 | nyam | rem_own_k0.75 | 348 | 0.66 | 0.47 | 62 | -35 | 23.3 |
| K7 | asia | q50_H75 | 2596 | 0.32 | 0.44 | 102 | 74 | 9.7 |
| K7 | asia | q60_H75 | 2596 | 0.19 | 0.44 | 111 | 90 | 7.6 |
| K7 | asia | q75_H75 | 2596 | 0.04 | 0.40 | 26 | 1 | 6.1 |
| K7 | asia | rem_own_k0.75 | 2596 | 0.68 | 0.44 | 88 | 0 | 27.2 |
| K7 | london | q50_H75 | 1781 | 0.57 | 0.43 | 62 | 37 | 10.9 |
| K7 | london | q60_H75 | 1781 | 0.33 | 0.44 | 60 | 35 | 9.4 |
| K7 | london | q75_H75 | 1781 | 0.12 | 0.48 | 138 | 101 | 6.5 |
| K7 | london | rem_own_k0.75 | 1781 | 0.69 | 0.43 | 45 | -12 | 27.4 |
| K7 | nyam | q50_H75 | 1565 | 0.57 | 0.42 | 21 | 18 | 10.0 |
| K7 | nyam | q60_H75 | 1565 | 0.32 | 0.40 | -4 | -17 | 9.0 |
| K7 | nyam | q75_H75 | 1565 | 0.07 | 0.41 | 40 | 36 | 16.3 |
| K7 | nyam | rem_own_k0.75 | 1565 | 0.70 | 0.39 | -21 | -38 | 26.0 |
| K7 | nypm | q50_H75 | 1136 | 0.50 | 0.36 | 65 | 54 | 8.1 |
| K7 | nypm | q60_H75 | 1136 | 0.31 | 0.34 | 62 | 48 | 5.6 |
| K7 | nypm | q75_H75 | 1136 | 0.09 | 0.29 | 155 | 179 | 3.5 |
| K7 | nypm | rem_own_k0.75 | 1136 | 0.71 | 0.37 | 72 | -30 | 23.7 |
| M7 | london | q50_H75 | 2489 | 0.42 | 0.43 | 45 | 40 | 10.0 |
| M7 | london | q60_H75 | 2489 | 0.24 | 0.43 | 32 | 26 | 8.2 |
| M7 | london | q75_H75 | 2489 | 0.06 | 0.38 | -74 | -97 | 7.1 |
| M7 | london | rem_own_k0.75 | 2489 | 0.59 | 0.39 | -40 | -29 | 22.9 |
| M7 | nyam | q50_H75 | 1496 | 0.52 | 0.43 | 49 | 22 | 8.6 |
| M7 | nyam | q60_H75 | 1496 | 0.27 | 0.44 | 76 | 57 | 7.2 |
| M7 | nyam | q75_H75 | 1496 | 0.06 | 0.44 | 127 | 131 | 4.9 |
| M7 | nyam | rem_own_k0.75 | 1496 | 0.69 | 0.42 | 30 | -36 | 27.3 |
| O7 | nyam | q50_H75 | 452 | 0.58 | 0.32 | 205 | 91 | 20.5 |
| O7 | nyam | q60_H75 | 452 | 0.37 | 0.31 | 156 | 118 | 16.9 |
| O7 | nyam | q75_H75 | 452 | 0.08 | 0.20 | -192 | -145 | 9.5 |
| O7 | nyam | rem_own_k0.75 | 452 | 0.31 | 0.30 | 120 | 82 | 20.6 |
| P7 | asia | q50_H75 | 2161 | 0.29 | 0.46 | 391 | 341 | 10.2 |
| P7 | asia | q60_H75 | 2161 | 0.16 | 0.48 | 487 | 484 | 9.3 |
| P7 | asia | q75_H75 | 2161 | 0.02 | 0.55 | 1227 | 969 | 5.7 |
| P7 | asia | rem_own_k0.75 | 2161 | 0.70 | 0.44 | 447 | 130 | 26.6 |
| P7 | london | q50_H75 | 1537 | 0.62 | 0.38 | 74 | 27 | 10.0 |
| P7 | london | q60_H75 | 1537 | 0.41 | 0.38 | 67 | 36 | 7.8 |
| P7 | london | q75_H75 | 1537 | 0.15 | 0.41 | 124 | 59 | 5.3 |
| P7 | london | rem_own_k0.75 | 1537 | 0.72 | 0.37 | -19 | -13 | 23.8 |
| P7 | nyam | q50_H75 | 1050 | 0.72 | 0.38 | 38 | 150 | 13.2 |
| P7 | nyam | q60_H75 | 1050 | 0.48 | 0.37 | -7 | 28 | 10.9 |
| P7 | nyam | q75_H75 | 1050 | 0.15 | 0.33 | -88 | -96 | 13.3 |
| P7 | nyam | rem_own_k0.75 | 1050 | 0.71 | 0.37 | -43 | 67 | 33.2 |
| U7 | asia | q50_H75 | 686 | 0.28 | 0.54 | 412 | 320 | 10.4 |
| U7 | asia | q60_H75 | 686 | 0.15 | 0.50 | 322 | 270 | 8.0 |
| U7 | asia | q75_H75 | 686 | 0.03 | 0.47 | -260 | -383 | 6.8 |
| U7 | asia | rem_own_k0.75 | 686 | 0.74 | 0.53 | 375 | 4 | 30.5 |
| U7 | london | q50_H75 | 645 | 0.27 | 0.46 | -102 | -183 | 8.7 |
| U7 | london | q60_H75 | 645 | 0.13 | 0.46 | -173 | -182 | 7.8 |
| U7 | london | q75_H75 | 645 | 0.03 | 0.50 | -396 | -466 | 5.4 |
| U7 | london | rem_own_k0.75 | 645 | 0.68 | 0.51 | 166 | 14 | 24.5 |

### Exact cap cells (global: all books at once; L3M, L6M when promoted; delta vs JN05W2)
| cell | L3M | L6M | HOLD | d mean/wk at $4.84 L3M |
|---|---|---|---|---|
| quantile 50 cap, horizon = 75th-percentile holding time | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | +1452 (lots +9/wk) |
| quantile 60 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 75 cap, horizon = 75th-percentile holding time | +177 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 101%, w2l 0 | n/a | n/a | +176 (lots +0/wk) |
| quantile 90 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 60 cap, horizon = median holding time | -1554 $/wk, DD +2.5%, ww +1445, stops 10.42(10.35), b5 89%, w2l 1 | n/a | n/a | -1658 (lots +29/wk) |
| quantile 75 cap, horizon = median holding time | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=0.5 | -8393 $/wk, DD +2.1%, ww +5889, stops 7.76(10.35), b5 57%, w2l 3 | n/a | n/a | -8805 (lots +113/wk) |
| remaining-range cap, forecast own 20-session mean, k=0.75 | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=1.0 | -6226 $/wk, DD +27.0%, ww +12290, stops 8.98(10.35), b5 66%, w2l 2 | n/a | n/a | -6458 (lots +63/wk) |
| remaining-range cap, forecast own 20-session mean, k=1.25 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.5 | -10795 $/wk, DD +40.3%, ww +11430, stops 7.00(10.35), b5 51%, w2l 4 | n/a | n/a | -11257 (lots +126/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.75 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.0 | -7259 $/wk, DD +39.4%, ww +17319, stops 7.76(10.35), b5 65%, w2l 2 | n/a | n/a | -7570 (lots +85/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.25 | pending | | | |
| EV-best target, bounded by the book target | -14326 $/wk, DD -25.6%, ww -15613, stops 8.45(10.35), b5 46%, w2l 3 | n/a | n/a | -14639 (lots +86/wk) |
| EV-best target, unbounded | pending | | | |
| extension m=1.0 | -110 $/wk, DD -53.4%, ww -2988, stops 11.72(10.35), b5 124%, w2l 2 | n/a | n/a | -18 (lots -25/wk) |
| extension m=1.5 | pending | | | |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts skipped | +1443 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | n/a | n/a | +1410 (lots +9/wk) |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts at half size | pending | | | |
| PLANTED-EDGE CHECK (look-ahead oracle 0.9 x realised MFE, not a result) | +85531 $/wk, DD +67.0%, ww +64263, stops 6.54(10.35), b5 259%, w2l 0 | n/a | n/a | +85219 (lots +85/wk) |
| PLANTED-EDGE CHECK (oracle 0.6 x realised MFE, not a result) | pending | | | |
| PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 | n/a | -125 (lots +1/wk) |
| PLACEBO pl23: quantile 50 cap, horizon = 75th-percentile holding time | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 | n/a | -871 (lots +3/wk) |
| PLACEBO pl37: quantile 50 cap, horizon = 75th-percentile holding time | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 | n/a | -612 (lots +2/wk) |
| PLACEBO plR1: quantile 50 cap, horizon = 75th-percentile holding time | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 | n/a | -670 (lots +4/wk) |

### The one candidate: forecast-quantile-50 cap, horizon = 75th-percentile holding time (L3M mean-only so far): all windows, W44 removed, placebos
| window | scope all | W44 removed |
|---|---|---|
| L3M | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 |
| L6M | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 |
| HOLD | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 |
| MID | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 |
| PREUW | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 |
Placebos (same cap, forecast features taken n sessions earlier at the same clock / a random earlier session), L3M then L6M when run:
| placebo | L3M | L6M |
|---|---|---|
| pl11 | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 |
| pl23 | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 |
| pl37 | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 |
| plR1 | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 |

### Per book x session exact cap cells (clean: one book in one session)
| slice | cap | L3M | May-Jul |
|---|---|---|---|
| A7 asia | quantile 50 cap, horizon = 75th-percentile holding time | -17 (live -30; $4.84 -17) DD +0.0% ww +0 stops 4.03(4.03) | n/a |

### FOR THE LIVE BUILD (what D7 computes at the signal second)
From its own 1-minute bars: last 15/30/60/120-minute range and realised vol, same-offset range over the previous 20 sessions (median), session ranges of the last 5/20 sessions, range so far, the entry position in the session range (favourable-side room), elapsed fraction of the session, ln of the book-session horizon; a small coefficient table per session (15 weights, mean, sd, intercept, four residual quantile offsets) refit every 14 days and shipped as a static file. Cap = min(60, price x exp(prediction + quantile offset) - 2); orders: the target limit is placed at the capped price. The remaining-range version needs the HAR session forecast (T-RANGE2 file) or D7 computes its own 20-session mean. No intraday feed from the box.


## Per book and session, clean, and the assembled stack
**STATUS (plain, not a PASS; B1 in progress, no "nothing passes" verdict is allowed until it is done): single-book single-session cells scored in L3M for 14 of 14 slices; slice picks so far: {}.**

Method (user order PART B, 2026-11-15): each cell = the Dial 10 hook restricted to ONE book in ONE session (every other book/session unchanged at JN05W2), exact engine, all layers ON, live caps. Dollars are BASE lots; the x1.75 live figure sits beside each headline (live); the $4.84 figure reprices every contract at the FEES.md $4.84 RT (engine raw $1.18). Compared on the same book x session slice of JN05W2 (day locks/caps still interact across books, which is why the cells are run for real and not sliced from the global run). B1a settings per slice: direction both / narrow-only / wide-only x gearing 0.5 / 1.0 at the 75th-percentile horizon, plus narrow/wide g1.0 at the median horizon; "fixed" = JN05W2 itself. Walk-forward: the pick for each slice is made on 2026-05..07 only (older than L3M); L3M (2026-08..10) is then out-of-sample. B1b (around each pick): lots cap 1.5/3, lots follow half the change, dead band 0/20%, target ratio 0.8/1.2, lever stop-only (sl: stop W, lots inverse, target in the same points) / target-only (tg) / size-only (sz: bracket fixed, lots follow the forecast), noise floor k = 3/4/5 x recent 5-minute ATR (bracket never narrower), clips 25..120 / 20..150.

### B1 table: per slice, every cell (L3M, delta vs JN05W2 same slice; May-Jul = the selection window)
| slice | setting | May-Jul (selection) | L3M (out of sample) | L6M |
|---|---|---|---|---|
| A7 asia | both/g1.0/H75 | -374 (live -654; $4.84 -370) DD -10.9% ww -261 stops 2.97(3.88) | +47 (live +83; $4.84 +40) DD +25.6% ww +1495 stops 5.55(4.03) | -163 (live -286; $4.84 -165) DD -29.2% ww +1253 stops 4.26(3.96) |
| A7 asia | narrow/g1.0/H75 | -419 (live -733; $4.84 -423) DD -0.6% ww -175 stops 4.49(3.88) | -18 (live -32; $4.84 -26) DD +17.7% ww +722 stops 5.63(4.03) | -219 (live -383; $4.84 -224) DD -19.1% ww +722 stops 5.06(3.96) |
| A7 asia | both/g0.5/H75 | -556 (live -973; $4.84 -553) DD -9.2% ww +72 stops 3.50(3.88) | -192 (live -336; $4.84 -195) DD +10.1% ww +412 stops 5.10(4.03) | -374 (live -654; $4.84 -374) DD -36.6% ww +412 stops 4.30(3.96) |
| A7 asia | narrow/g0.5/H75 | -350 (live -612; $4.84 -352) DD +0.0% ww +0 stops 4.34(3.88) | -186 (live -325; $4.84 -189) DD +10.0% ww +552 stops 5.10(4.03) | -268 (live -469; $4.84 -270) DD -15.8% ww +552 stops 4.72(3.96) |
| A7 asia | wide/g1.0/H75 | +19 (live +33; $4.84 +26) DD -10.9% ww +283 stops 2.51(3.88) | -15 (live -26; $4.84 -14) DD +2.4% ww -426 stops 3.96(4.03) | +2 (live +3; $4.84 +6) DD -13.6% ww -426 stops 3.23(3.96) |
| A7 asia | wide/g0.5/H75 | n/a | -1 (live -1; $4.84 -1) DD +1.4% ww -140 stops 4.03(4.03) | n/a |
| A7 asia | wide/g1.0/H50 | n/a | -48 (live -85; $4.84 -48) DD -3.0% ww -426 stops 3.88(4.03) | n/a |
| A7 asia | narrow/g1.0/H50 | n/a | -159 (live -279; $4.84 -171) DD -8.3% ww +877 stops 5.93(4.03) | n/a |
| H7 asia | wide/g0.5/H75 | n/a | +123 (live +215; $4.84 +123) DD +0.0% ww +0 stops 0.23(0.23) | n/a |
| H7 asia | wide/g1.0/H75 | n/a | -67 (live -118; $4.84 -67) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | wide/g1.0/H50 | n/a | -312 (live -546; $4.84 -312) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | both/g1.0/H75 | +1123 (live +1965; $4.84 +1129) DD +6.5% ww +1483 stops 0.53(0.61) | +177 (live +309; $4.84 +163) DD -33.6% ww -1228 stops 0.61(0.23) | +650 (live +1137; $4.84 +646) DD +6.5% ww +1483 stops 0.57(0.42) |
| H7 asia | narrow/g1.0/H75 | n/a | +244 (live +427; $4.84 +230) DD -33.6% ww -1228 stops 0.53(0.23) | n/a |
| H7 asia | both/g0.5/H75 | n/a | -574 (live -1004; $4.84 -580) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g0.5/H75 | n/a | -697 (live -1219; $4.84 -703) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g1.0/H50 | n/a | -355 (live -621; $4.84 -372) DD -120.5% ww -2166 stops 0.53(0.23) | n/a |
| H7 nyam | narrow/g1.0/H50 | n/a | +252 (live +441; $4.84 +252) DD +60.4% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | both/g1.0/H75 | n/a | +281 (live +491; $4.84 +280) DD +57.7% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | narrow/g1.0/H75 | -187 (live -328; $4.84 -188) DD -4.0% ww +0 stops 0.53(0.46) | +258 (live +452; $4.84 +258) DD +57.7% ww +480 stops 0.30(0.38) | +35 (live +62; $4.84 +35) DD +24.1% ww +480 stops 0.42(0.42) |
| H7 nyam | both/g0.5/H75 | +103 (live +180; $4.84 +103) DD +29.2% ww -83 stops 0.46(0.46) | +87 (live +153; $4.84 +87) DD +2.2% ww +195 stops 0.38(0.38) | +95 (live +167; $4.84 +95) DD +2.2% ww +195 stops 0.42(0.42) |
| H7 nyam | narrow/g0.5/H75 | n/a | +77 (live +134; $4.84 +77) DD +2.2% ww +195 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g0.5/H75 | n/a | +11 (live +19; $4.84 +11) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H75 | n/a | +22 (live +39; $4.84 +22) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H50 | n/a | +30 (live +53; $4.84 +30) DD +0.0% ww +0 stops 0.30(0.38) | n/a |
| K7 asia | wide/g1.0/H75 | n/a | +297 (live +520; $4.84 +298) DD +0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | wide/g0.5/H75 | n/a | -54 (live -94; $4.84 -54) DD -0.7% ww -404 stops 0.00(0.00) | n/a |
| K7 asia | narrow/g0.5/H75 | n/a | +1877 (live +3285; $4.84 +1855) DD -19.6% ww -2412 stops 0.00(0.00) | n/a |
| K7 asia | both/g0.5/H75 | n/a | +1823 (live +3191; $4.84 +1801) DD -28.8% ww -3232 stops 0.00(0.00) | n/a |
| K7 asia | wide/g1.0/H50 | n/a | -401 (live -702; $4.84 -400) DD -35.9% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | both/g1.0/H75 | n/a | +1292 (live +2261; $4.84 +1220) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H75 | n/a | +912 (live +1595; $4.84 +838) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H50 | n/a | +355 (live +621; $4.84 +268) DD -86.2% ww -5644 stops 0.00(0.00) | n/a |
| K7 london | both/g0.5/H75 | n/a | -9 (live -15; $4.84 -14) DD +8.7% ww +4326 stops 0.23(0.30) | n/a |
| K7 london | wide/g0.5/H75 | n/a | +27 (live +48; $4.84 +29) DD +0.5% ww +0 stops 0.30(0.30) | n/a |
| K7 london | wide/g1.0/H50 | n/a | +431 (live +755; $4.84 +433) DD -3.3% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g0.5/H75 | n/a | -123 (live -215; $4.84 -130) DD -4.2% ww +4733 stops 0.23(0.30) | n/a |
| K7 london | wide/g1.0/H75 | n/a | +157 (live +274; $4.84 +160) DD -4.8% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g1.0/H50 | n/a | -182 (live -319; $4.84 -204) DD -13.7% ww +3097 stops 0.23(0.30) | n/a |
| K7 london | both/g1.0/H75 | n/a | +481 (live +841; $4.84 +462) DD -25.5% ww +4257 stops 0.38(0.30) | n/a |
| K7 london | narrow/g1.0/H75 | n/a | -31 (live -55; $4.84 -55) DD -42.3% ww +4122 stops 0.38(0.30) | n/a |
| K7 nyam | narrow/g1.0/H50 | n/a | +769 (live +1345; $4.84 +761) DD +51.0% ww +2185 stops 0.00(0.00) | n/a |
| K7 nyam | both/g1.0/H75 | n/a | +1160 (live +2030; $4.84 +1153) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g1.0/H75 | n/a | +984 (live +1722; $4.84 +977) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g0.5/H75 | n/a | +668 (live +1170; $4.84 +667) DD +40.3% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | both/g0.5/H75 | n/a | +806 (live +1410; $4.84 +805) DD +39.5% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H75 | n/a | +176 (live +308; $4.84 +176) DD -0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H50 | n/a | +252 (live +441; $4.84 +253) DD -0.3% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g0.5/H75 | n/a | +137 (live +241; $4.84 +137) DD -0.8% ww +0 stops 0.00(0.00) | n/a |
| K7 nypm | wide/g1.0/H50 | n/a | +442 (live +773; $4.84 +442) DD +17.3% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | wide/g1.0/H75 | n/a | +70 (live +122; $4.84 +70) DD +13.1% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | both/g1.0/H75 | n/a | -184 (live -322; $4.84 -197) DD +9.8% ww +1145 stops 0.15(0.08) | n/a |
| K7 nypm | wide/g0.5/H75 | n/a | -4 (live -8; $4.84 -4) DD -1.5% ww -38 stops 0.00(0.08) | n/a |
| K7 nypm | narrow/g1.0/H50 | n/a | +48 (live +84; $4.84 +32) DD -1.9% ww +105 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g1.0/H75 | n/a | -254 (live -445; $4.84 -267) DD -3.3% ww +990 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g0.5/H75 | n/a | -266 (live -465; $4.84 -269) DD -26.7% ww +140 stops 0.08(0.08) | n/a |
| K7 nypm | both/g0.5/H75 | n/a | -270 (live -473; $4.84 -274) DD -27.3% ww +102 stops 0.00(0.08) | n/a |
| M7 london | wide/g1.0/H75 | n/a | +1614 (live +2824; $4.84 +1616) DD +4.9% ww +1190 stops 0.53(0.91) | n/a |
| M7 london | wide/g0.5/H75 | n/a | +688 (live +1204; $4.84 +689) DD +4.4% ww +1400 stops 0.84(0.91) | n/a |
| M7 london | wide/g1.0/H50 | n/a | +538 (live +942; $4.84 +540) DD -1.3% ww -80 stops 0.84(0.91) | n/a |
| M7 london | both/g0.5/H75 | n/a | +1147 (live +2008; $4.84 +1139) DD -8.1% ww +130 stops 1.07(0.91) | n/a |
| M7 london | narrow/g0.5/H75 | n/a | +417 (live +730; $4.84 +408) DD -10.9% ww -1075 stops 1.14(0.91) | n/a |
| M7 london | narrow/g1.0/H50 | n/a | +476 (live +833; $4.84 +446) DD -19.9% ww +1144 stops 1.45(0.91) | n/a |
| M7 london | narrow/g1.0/H75 | n/a | -366 (live -640; $4.84 -390) DD -20.4% ww +80 stops 1.29(0.91) | n/a |
| M7 london | both/g1.0/H75 | n/a | +1142 (live +1999; $4.84 +1121) DD -23.2% ww -729 stops 0.91(0.91) | n/a |
| M7 nyam | narrow/g1.0/H50 | n/a | +439 (live +769; $4.84 +424) DD +26.0% ww -222 stops 0.38(0.23) | n/a |
| M7 nyam | both/g0.5/H75 | n/a | +79 (live +138; $4.84 +75) DD +0.8% ww +194 stops 0.30(0.23) | n/a |
| M7 nyam | narrow/g0.5/H75 | n/a | +73 (live +127; $4.84 +69) DD +0.8% ww +194 stops 0.38(0.23) | n/a |
| M7 nyam | wide/g0.5/H75 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H75 | n/a | +16 (live +28; $4.84 +16) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H50 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | both/g1.0/H75 | n/a | +419 (live +733; $4.84 +405) DD -6.8% ww -991 stops 0.46(0.23) | n/a |
| M7 nyam | narrow/g1.0/H75 | n/a | +402 (live +704; $4.84 +388) DD -6.8% ww -991 stops 0.53(0.23) | n/a |
| P7 asia | narrow/g1.0/H50 | n/a | -3918 (live -6857; $4.84 -4186) DD -0.4% ww -4286 stops 0.46(0.15) | n/a |
| P7 asia | both/g0.5/H75 | n/a | -5946 (live -10406; $4.84 -6044) DD -1.0% ww +6944 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g0.5/H75 | n/a | -5762 (live -10084; $4.84 -5860) DD -1.0% ww +9022 stops 0.15(0.15) | n/a |
| P7 asia | wide/g0.5/H75 | n/a | -184 (live -322; $4.84 -183) DD -4.9% ww -2079 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g1.0/H75 | n/a | -2696 (live -4718; $4.84 -2882) DD -7.8% ww -10346 stops 0.53(0.15) | n/a |
| P7 asia | wide/g1.0/H50 | n/a | -816 (live -1428; $4.84 -812) DD -22.6% ww -9033 stops 0.15(0.15) | n/a |
| P7 asia | wide/g1.0/H75 | n/a | -491 (live -858; $4.84 -490) DD -25.2% ww -10331 stops 0.15(0.15) | n/a |
| P7 asia | both/g1.0/H75 | n/a | -3315 (live -5802; $4.84 -3501) DD -36.1% ww -13164 stops 0.53(0.15) | n/a |
| P7 london | both/g0.5/H75 | n/a | +894 (live +1565; $4.84 +886) DD +29.6% ww -1633 stops 0.08(0.08) | n/a |
| P7 london | narrow/g0.5/H75 | n/a | +386 (live +675; $4.84 +375) DD +28.5% ww -1328 stops 0.08(0.08) | n/a |
| P7 london | narrow/g1.0/H50 | n/a | +927 (live +1622; $4.84 +895) DD +19.7% ww -3009 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H75 | n/a | -142 (live -249; $4.84 -138) DD +2.7% ww -458 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H50 | n/a | +265 (live +464; $4.84 +266) DD +1.1% ww +0 stops 0.08(0.08) | n/a |
| P7 london | wide/g0.5/H75 | n/a | +385 (live +674; $4.84 +387) DD -1.9% ww -238 stops 0.08(0.08) | n/a |
| P7 london | both/g1.0/H75 | n/a | +1179 (live +2064; $4.84 +1145) DD -9.8% ww -5408 stops 0.15(0.08) | n/a |
| P7 london | narrow/g1.0/H75 | n/a | +1322 (live +2313; $4.84 +1282) DD -14.4% ww -5203 stops 0.15(0.08) | n/a |
| P7 nyam | both/g1.0/H75 | n/a | +697 (live +1220; $4.84 +685) DD +51.3% ww +354 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g1.0/H75 | n/a | +543 (live +951; $4.84 +529) DD +45.9% ww +324 stops 0.30(0.38) | n/a |
| P7 nyam | both/g0.5/H75 | n/a | +105 (live +184; $4.84 +99) DD +36.7% ww +238 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g0.5/H75 | n/a | -13 (live -23; $4.84 -20) DD +36.4% ww +262 stops 0.30(0.38) | n/a |
| P7 nyam | wide/g0.5/H75 | n/a | +118 (live +207; $4.84 +119) DD +0.3% ww -25 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H75 | n/a | +16 (live +27; $4.84 +17) DD -7.5% ww -105 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H50 | n/a | -544 (live -952; $4.84 -543) DD -47.7% ww -3348 stops 0.38(0.38) | n/a |
| U7 asia | narrow/g1.0/H50 | n/a | +1222 (live +2139; $4.84 +1201) DD +15.6% ww -265 stops 1.90(1.83) | n/a |
| U7 asia | both/g1.0/H75 | n/a | +71 (live +124; $4.84 +56) DD +8.3% ww -1836 stops 1.98(1.83) | n/a |
| U7 asia | narrow/g1.0/H75 | n/a | +502 (live +879; $4.84 +487) DD +8.3% ww +983 stops 1.98(1.83) | n/a |
| U7 asia | both/g0.5/H75 | n/a | -800 (live -1399; $4.84 -808) DD +6.6% ww -2883 stops 2.05(1.83) | n/a |
| U7 asia | narrow/g0.5/H75 | n/a | -162 (live -284; $4.84 -170) DD +6.6% ww +57 stops 2.05(1.83) | n/a |
| U7 asia | wide/g0.5/H75 | n/a | -637 (live -1115; $4.84 -637) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H75 | n/a | -431 (live -755; $4.84 -431) DD +0.0% ww -1836 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H50 | n/a | -648 (live -1134; $4.84 -648) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 london | narrow/g0.5/H75 | n/a | +393 (live +687; $4.84 +392) DD +17.2% ww +1796 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H75 | n/a | +246 (live +431; $4.84 +243) DD +3.1% ww -1185 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H50 | n/a | -41 (live -72; $4.84 -48) DD -9.9% ww -1991 stops 1.52(1.45) | n/a |
| U7 london | both/g0.5/H75 | n/a | -891 (live -1560; $4.84 -890) DD -25.4% ww -3538 stops 1.52(1.45) | n/a |
| U7 london | wide/g1.0/H50 | n/a | -839 (live -1468; $4.84 -837) DD -33.9% ww -4122 stops 1.37(1.45) | n/a |
| U7 london | wide/g0.5/H75 | n/a | -1284 (live -2247; $4.84 -1282) DD -44.3% ww -6280 stops 1.52(1.45) | n/a |
| U7 london | both/g1.0/H75 | n/a | -1728 (live -3025; $4.84 -1729) DD -105.5% ww -7540 stops 1.60(1.45) | n/a |
| U7 london | wide/g1.0/H75 | n/a | -1975 (live -3455; $4.84 -1972) DD -109.8% ww -6355 stops 1.60(1.45) | n/a |

### Summary per slice: pick made on May-Jul, result on L3M
| slice | pick | L3M result of the pick | verdict |
|---|---|---|---|
| A7 asia | pending | | |
| H7 asia | pending | | |
| H7 nyam | pending | | |
| K7 asia | pending | | |
| K7 london | pending | | |
| K7 nyam | pending | | |
| K7 nypm | pending | | |
| M7 london | pending | | |
| M7 nyam | pending | | |
| P7 asia | pending | | |
| P7 london | pending | | |
| P7 nyam | pending | | |
| U7 asia | pending | | |
| U7 london | pending | | |

### B2: why the global version adds full stops (narrow-only/both g1.0 H75 cell, L3M, trade tables)
Reference JN05W2 L3M (no O7): 1855 trades, stop rate 0.071, 132 stops (13 weeks).

**M1_75_g10_c1_d10_c20_tb_B**: 2038 trades (+183 vs JN05W2), stops 173 (+41), stop rate 0.085 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 437 | 0.103 | 3.05 | 94 |
| (40, 50] | 721 | 0.074 | 2.36 | 271 |
| (50, 55] | 232 | 0.099 | 1.97 | 169 |
| (55, 60] | 435 | 0.076 | 1.87 | 76 |
| (60, 70] | 75 | 0.120 | 2.01 | -385 |
| (70, 80] | 62 | 0.048 | 1.68 | -284 |
| (80, 101] | 76 | 0.092 | 1.13 | -591 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1543 | 0.069 | 2.21 | 54 |
| (3.0, 4.0] | 294 | 0.116 | 2.29 | 239 |
| (4.0, 5.0] | 74 | 0.108 | 2.31 | 364 |
| (5.0, 6.0] | 6 | 0.167 | 2.50 | 172 |
| (6.0, 8.0] | 4 | 0.000 | 1.00 | -119 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1068 | 0.096 | 1.00 | 4 |
| (1, 2] | 385 | 0.078 | 2.00 | 115 |
| (2, 3] | 215 | 0.093 | 3.00 | 23 |
| (3, 5] | 195 | 0.062 | 4.46 | 256 |
| (5, 8] | 138 | 0.065 | 6.70 | 690 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

**M1_75_g10_c1_d10_c20_tb_N**: 2072 trades (+217 vs JN05W2), stops 178 (+46), stop rate 0.086 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 449 | 0.105 | 3.02 | 97 |
| (40, 50] | 725 | 0.073 | 2.35 | 272 |
| (50, 55] | 236 | 0.102 | 1.97 | 150 |
| (55, 60] | 662 | 0.082 | 1.82 | -29 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1644 | 0.072 | 2.18 | 50 |
| (3.0, 4.0] | 264 | 0.121 | 2.38 | 348 |
| (4.0, 5.0] | 44 | 0.091 | 3.11 | 1063 |
| (5.0, 6.0] | 3 | 0.000 | 3.33 | 68 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1073 | 0.095 | 1.00 | 8 |
| (1, 2] | 413 | 0.085 | 2.00 | 117 |
| (2, 3] | 197 | 0.081 | 3.00 | 213 |
| (3, 5] | 217 | 0.074 | 4.43 | 196 |
| (5, 8] | 135 | 0.067 | 6.74 | 714 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

Reading of the W/ATR5 table: ATR5 = mean range of the last 14 five-minute buckets in points; a bracket 3x ATR5 or less is within ordinary 5-minute noise. The noise-floor cells (floor 3/4/5 x ATR5, narrowing only) are listed in B3.


### B3: levers (stop-only / target-only / both / size-only) and noise floor, per slice
| slice | cell | L3M | May-Jul |
|---|---|---|---|

### B4: assembled stack (each slice at its own walk-forward pick, run together)
(not run yet: starts when every slice has a pick)


## Dial 9: whole bracket at constant R
**VERDICT (plain, not a PASS): 118 of 120 cells scored through L3M, 3 through L6M, 0 through HOLD; 2 (cell,scope) leads pass the tolerant gate in every scored window (1 at scope all) - before placebo.**

Identity: TL3_D9_ID 202610 (hook active at W=60): 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL. Prereg autopilot/DIAL9_PREREG.md (sha line in DECISIONS.md). Order: ADDENDUM_CHOP_DIAL9_20261114.md. Code code/th_dial9 (d9_hooks.py reuses th_rangeuse forecasts fc.parquet a/b/c). Engine dollars are BASE lots (live x1.75).
Definition: W = clip(book stop x Wtab/60, 30, 100); target = W x the book own target/stop ratio; lots = base x min(cap, stop/W) rounded half-up (min 1); cap 1.5 or 2 on increases. Maps T1 40/60/100, T2 45/60/80 (tercile of the expanding past predictions), C continuous (range ratio exp(pred-fref) x 60, clip 30..100). Version S = stop+target only (BookLock held at base dollars); version A = also state-cut arm and ctxcut arms, K7 flat cut, TH-L2 LOSS_MIN and TIGHT_TRAIL, MINDIP add dip, BookLock R from actual lots (all x W/stop). Not scalable: the hard-coded 30-pt profit-side tighten threshold inside sim.py. Halves B both, N narrow-only (W<=stop), W wide-only (W>=stop). Cap 15 = x1.5, 20 = x2 (wide-only has no increase). Fees and measured slippage are charged by the engine at the real lot count.
LOT/FEE BASIS: all sets are BASE (box) lots, live = x1.75; the engine charges its own raw $1.18/contract RT (net_fee) with the engine fills, not the FEES.md $4.84 RT. All tables above use raw net_fee. The last two columns of the per-cell table reprice the delta mean/wk at $4.84 RT per contract (net - lots x 3.66 per trade, cell and JN05W2 alike, no rerun) next to the lot change per week. Lot increases (cap x1.5/x2) raise fees, so the repriced column matters most here.
Windows: L3M, L6M first, then HOLD/PRE for cells that pass; GAP/MID = 2026-02-07..2026-04-30 is scored by this module (own additive window definition, inside HOLD). X' (2023-04..2024-01) and most of PRE cannot be scored: the walk-forward forecasts start ~2025-03 (min 120 days), so the rule is inactive there and every cell equals JN05W2; reported as not scorable, not as a pass.

### Which half and which scaling carries it (median over cells, scope all; delta vs JN05W2; DD cut + = smaller drawdown)
| group | cells L3M | median DD cut L3M % | median d mean L3M $/wk | median d worst week L3M | median d full stops/wk | L6M median DD cut % / d mean / cells |
|---|---|---|---|---|---|---|
| version S | 59 | -1.6 | -576 | -40 | +1.60 | -10.0 / -6259 / 2 |
| version A | 59 | -0.4 | -2562 | +0 | +0.00 | +6.8 / +259 / 1 |
| both halves | 48 | -10.6 | -3873 | -5035 | +0.08 | +6.8 / -3663 / 3 |
| narrow-only | 48 | +0.0 | -83 | +0 | +0.65 | n/a |
| wide-only | 22 | -16.9 | -3190 | -4791 | -0.68 | n/a |
| cap 1.5 (both/narrow) | 48 | -0.2 | -853 | +0 | +0.27 | +6.8 / -3663 / 3 |
| cap 2 (both/narrow) | 48 | -0.2 | -853 | +0 | +0.27 | n/a |
| fc a | 30 | -5.3 | -131 | -3070 | +0.08 | n/a |
| fc b | 30 | -0.1 | -2159 | -40 | +0.15 | +6.8 / +259 / 1 |
| fc c | 28 | -1.6 | -2050 | +0 | +0.04 | +17.7 / -3663 / 1 |
| fc r (R2 HAR+CME) | 30 | -3.0 | -308 | +0 | +0.00 | -37.7 / -8855 / 1 |
| map T1 | 40 | -10.6 | -2484 | -3513 | +0.76 | -10.0 / -6259 / 2 |
| map T2 | 40 | -12.0 | -4753 | -6809 | +0.53 | n/a |
| map C | 38 | +0.0 | -77 | +110 | +0.00 | +6.8 / +259 / 1 |

Cross: version x half (L3M scope all, median DD cut % / median d mean $/wk)
| | both | narrow-only | wide-only |
|---|---|---|---|
| version S | -12.9 / -2847 (n=24) | +0.0 / -68 (n=24) | -14.3 / -1646 (n=11) |
| version A | -7.6 / -5126 (n=24) | +0.0 / -101 (n=24) | -19.4 / -3209 (n=11) |

### Per cell, scope all (sorted by L3M drawdown cut; L6M and HOLD when present)
| cell | L3M | L6M | HOLD | MID(GAP) | PRE | d mean/wk at $4.84 RT L3M | at $4.84 L6M |
|---|---|---|---|---|---|---|---|
| S_c_T1_B_15 | -2406 $/wk, DD +17.7%, ww +8971, stops 16.74(10.35), b5 94%, w2l 1 | -3663 $/wk, DD +17.7%, ww +8971, stops 12.86(10.99), b5 83%, w2l 1 | n/a | n/a | n/a | -2475 (lots +19/wk) | -3567 (lots -26/wk) |
| S_c_T1_B_20 | -2406 $/wk, DD +17.7%, ww +8971, stops 16.74(10.35), b5 94%, w2l 1 | n/a | n/a | n/a | n/a | -2475 (lots +19/wk) | n/a |
| S_c_T1_W_x | -576 $/wk, DD +14.5%, ww +12639, stops 9.05(10.35), b5 102%, w2l 1 | n/a | n/a | n/a | n/a | -491 (lots -23/wk) | n/a |
| A_b_T2_N_15 | -4951 $/wk, DD +12.9%, ww +6743, stops 11.41(10.35), b5 79%, w2l 2 | n/a | n/a | n/a | n/a | -5070 (lots +32/wk) | n/a |
| A_c_T2_N_15 | -2952 $/wk, DD +12.9%, ww +6743, stops 10.96(10.35), b5 90%, w2l 0 | n/a | n/a | n/a | n/a | -3040 (lots +24/wk) | n/a |
| A_b_T2_N_20 | -4951 $/wk, DD +12.9%, ww +6743, stops 11.41(10.35), b5 79%, w2l 2 | n/a | n/a | n/a | n/a | -5070 (lots +32/wk) | n/a |
| A_c_T2_N_20 | -2952 $/wk, DD +12.9%, ww +6743, stops 10.96(10.35), b5 90%, w2l 0 | n/a | n/a | n/a | n/a | -3040 (lots +24/wk) | n/a |
| A_a_C_B_15 | +821 $/wk, DD +7.9%, ww +4125, stops 10.42(10.35), b5 99%, w2l 0 | n/a | n/a | -827 $/wk, DD +3.0%, ww -257, stops 11.05(10.88), b5 97%, w2l 0 | n/a | +819 (lots +0/wk) | n/a |
| A_a_C_B_20 | +821 $/wk, DD +7.9%, ww +4125, stops 10.42(10.35), b5 99%, w2l 0 | n/a | n/a | n/a | n/a | +819 (lots +0/wk) | n/a |
| A_a_C_W_x | +879 $/wk, DD +7.9%, ww +4125, stops 10.42(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +877 (lots +0/wk) | n/a |
| A_b_T1_N_15 | -2562 $/wk, DD +7.3%, ww +1929, stops 11.34(10.35), b5 86%, w2l 1 | n/a | n/a | n/a | n/a | -2778 (lots +59/wk) | n/a |
| A_b_T1_N_20 | -2562 $/wk, DD +7.3%, ww +1929, stops 11.34(10.35), b5 86%, w2l 1 | n/a | n/a | n/a | n/a | -2778 (lots +59/wk) | n/a |
| A_b_C_B_15 | +805 $/wk, DD +6.8%, ww +3510, stops 10.35(10.35), b5 100%, w2l 0 | +259 $/wk, DD +6.8%, ww +3510, stops 10.92(10.99), b5 102%, w2l 0 | n/a | n/a | n/a | +801 (lots +1/wk) | +255 (lots +1/wk) |
| A_b_C_B_20 | +805 $/wk, DD +6.8%, ww +3510, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +801 (lots +1/wk) | n/a |
| S_b_T2_N_15 | -1581 $/wk, DD +6.6%, ww +3426, stops 16.21(10.35), b5 79%, w2l 1 | n/a | n/a | n/a | n/a | -1659 (lots +21/wk) | n/a |
| S_c_T2_N_15 | -1186 $/wk, DD +6.6%, ww +3426, stops 15.45(10.35), b5 92%, w2l 1 | n/a | n/a | n/a | n/a | -1257 (lots +19/wk) | n/a |
| S_b_T2_N_20 | -1581 $/wk, DD +6.6%, ww +3426, stops 16.21(10.35), b5 79%, w2l 1 | n/a | n/a | n/a | n/a | -1659 (lots +21/wk) | n/a |
| S_c_T2_N_20 | -1186 $/wk, DD +6.6%, ww +3426, stops 15.45(10.35), b5 92%, w2l 1 | n/a | n/a | n/a | n/a | -1257 (lots +19/wk) | n/a |
| A_b_C_W_x | +892 $/wk, DD +6.5%, ww +3385, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +888 (lots +1/wk) | n/a |
| A_c_C_B_15 | +622 $/wk, DD +3.4%, ww +3360, stops 10.42(10.35), b5 102%, w2l 0 | n/a | n/a | n/a | n/a | +618 (lots +1/wk) | n/a |
| A_c_C_B_20 | +622 $/wk, DD +3.4%, ww +3360, stops 10.42(10.35), b5 102%, w2l 0 | n/a | n/a | n/a | n/a | +618 (lots +1/wk) | n/a |
| S_b_C_W_x | -234 $/wk, DD +0.5%, ww +230, stops 10.27(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -234 (lots +0/wk) | n/a |
| S_b_C_B_15 | -331 $/wk, DD +0.4%, ww +190, stops 10.27(10.35), b5 99%, w2l 0 | n/a | n/a | n/a | n/a | -331 (lots +0/wk) | n/a |
| S_b_C_B_20 | -331 $/wk, DD +0.4%, ww +190, stops 10.27(10.35), b5 99%, w2l 0 | n/a | n/a | n/a | n/a | -331 (lots +0/wk) | n/a |
| A_a_T2_N_15 | +1035 $/wk, DD +0.4%, ww +197, stops 10.58(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +929 (lots +29/wk) | n/a |
| A_a_T2_N_20 | +1035 $/wk, DD +0.4%, ww +197, stops 10.58(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +929 (lots +29/wk) | n/a |
| A_b_C_N_15 | -87 $/wk, DD +0.2%, ww +125, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -87 (lots +0/wk) | n/a |
| A_b_C_N_20 | -87 $/wk, DD +0.2%, ww +125, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -87 (lots +0/wk) | n/a |
| S_a_C_B_15 | -188 $/wk, DD +0.2%, ww +110, stops 10.35(10.35), b5 99%, w2l 0 | n/a | n/a | n/a | n/a | -188 (lots -0/wk) | n/a |
| S_a_C_B_20 | -188 $/wk, DD +0.2%, ww +110, stops 10.35(10.35), b5 99%, w2l 0 | n/a | n/a | n/a | n/a | -188 (lots -0/wk) | n/a |
| S_a_C_W_x | -130 $/wk, DD +0.2%, ww +110, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -130 (lots -0/wk) | n/a |
| S_r_T1_N_15 | +953 $/wk, DD +0.0%, ww +0, stops 14.99(10.35), b5 104%, w2l 0 | n/a | n/a | n/a | n/a | +881 (lots +19/wk) | n/a |
| A_r_T1_N_15 | +1392 $/wk, DD +0.0%, ww +0, stops 10.65(10.35), b5 101%, w2l 0 | n/a | n/a | n/a | n/a | +1311 (lots +22/wk) | n/a |
| S_r_T1_N_20 | +953 $/wk, DD +0.0%, ww +0, stops 14.99(10.35), b5 104%, w2l 0 | n/a | n/a | n/a | n/a | +881 (lots +19/wk) | n/a |
| A_r_T1_N_20 | +1392 $/wk, DD +0.0%, ww +0, stops 10.65(10.35), b5 101%, w2l 0 | n/a | n/a | n/a | n/a | +1311 (lots +22/wk) | n/a |
| S_r_T2_N_15 | +454 $/wk, DD +0.0%, ww +0, stops 12.86(10.35), b5 99%, w2l 0 | n/a | n/a | n/a | n/a | +428 (lots +7/wk) | n/a |
| A_r_T2_N_15 | +672 $/wk, DD +0.0%, ww +0, stops 10.50(10.35), b5 98%, w2l 0 | n/a | n/a | n/a | n/a | +643 (lots +8/wk) | n/a |
| S_r_C_N_15 | -20 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -20 (lots +0/wk) | n/a |
| A_r_C_N_15 | -114 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -114 (lots -0/wk) | n/a |
| S_a_C_N_15 | -58 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -58 (lots +0/wk) | n/a |
| A_a_C_N_15 | -58 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -58 (lots +0/wk) | n/a |
| S_c_C_N_15 | -79 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -79 (lots +0/wk) | n/a |
| A_c_C_N_15 | -76 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -76 (lots +0/wk) | n/a |
| S_r_T2_N_20 | +454 $/wk, DD +0.0%, ww +0, stops 12.86(10.35), b5 99%, w2l 0 | n/a | n/a | n/a | n/a | +428 (lots +7/wk) | n/a |
| A_r_T2_N_20 | +672 $/wk, DD +0.0%, ww +0, stops 10.50(10.35), b5 98%, w2l 0 | n/a | n/a | n/a | n/a | +643 (lots +8/wk) | n/a |
| S_r_C_N_20 | -20 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -20 (lots +0/wk) | n/a |
| A_r_C_N_20 | -114 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -114 (lots -0/wk) | n/a |
| S_a_C_N_20 | -58 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -58 (lots +0/wk) | n/a |
| A_a_C_N_20 | -58 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -58 (lots +0/wk) | n/a |
| S_c_C_N_20 | -79 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -79 (lots +0/wk) | n/a |
| A_c_C_N_20 | -76 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -76 (lots +0/wk) | n/a |
| S_b_C_N_15 | -97 $/wk, DD -0.1%, ww -40, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -97 (lots +0/wk) | n/a |
| S_b_C_N_20 | -97 $/wk, DD -0.1%, ww -40, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -97 (lots +0/wk) | n/a |
| A_r_C_B_15 | +370 $/wk, DD -0.4%, ww +225, stops 10.35(10.35), b5 102%, w2l 0 | n/a | n/a | n/a | n/a | +366 (lots +1/wk) | n/a |
| A_r_C_B_20 | +370 $/wk, DD -0.4%, ww +225, stops 10.35(10.35), b5 102%, w2l 0 | n/a | n/a | n/a | n/a | +366 (lots +1/wk) | n/a |
| A_r_C_W_x | +484 $/wk, DD -0.4%, ww +225, stops 10.35(10.35), b5 102%, w2l 0 | n/a | n/a | n/a | n/a | +480 (lots +1/wk) | n/a |
| S_a_T2_N_15 | +2271 $/wk, DD -1.0%, ww -530, stops 14.76(10.35), b5 94%, w2l 0 | n/a | n/a | n/a | n/a | +2187 (lots +23/wk) | n/a |
| S_a_T2_N_20 | +2271 $/wk, DD -1.0%, ww -530, stops 14.76(10.35), b5 94%, w2l 0 | n/a | n/a | n/a | n/a | +2187 (lots +23/wk) | n/a |
| S_b_T1_W_x | -1646 $/wk, DD -1.0%, ww -801, stops 9.21(10.35), b5 96%, w2l 0 | n/a | n/a | n/a | n/a | -1583 (lots -17/wk) | n/a |
| S_c_C_B_15 | -353 $/wk, DD -1.6%, ww +230, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -354 (lots +0/wk) | n/a |
| S_c_C_B_20 | -353 $/wk, DD -1.6%, ww +230, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -354 (lots +0/wk) | n/a |
| A_b_T2_B_15 | -11214 $/wk, DD -3.8%, ww -9974, stops 10.80(10.35), b5 75%, w2l 3 | n/a | n/a | n/a | n/a | -11290 (lots +21/wk) | n/a |
| A_b_T2_B_20 | -11214 $/wk, DD -3.8%, ww -9974, stops 10.80(10.35), b5 75%, w2l 3 | n/a | n/a | n/a | n/a | -11290 (lots +21/wk) | n/a |
| A_a_T1_N_15 | -1550 $/wk, DD -5.3%, ww -7516, stops 11.03(10.35), b5 88%, w2l 0 | n/a | n/a | n/a | n/a | -1730 (lots +49/wk) | n/a |
| A_a_T1_N_20 | -1550 $/wk, DD -5.3%, ww -7516, stops 11.03(10.35), b5 88%, w2l 0 | n/a | n/a | n/a | n/a | -1730 (lots +49/wk) | n/a |
| A_b_T1_B_15 | -5950 $/wk, DD -5.4%, ww -6662, stops 10.50(10.35), b5 88%, w2l 2 | n/a | n/a | n/a | n/a | -6104 (lots +42/wk) | n/a |
| A_b_T1_B_20 | -5950 $/wk, DD -5.4%, ww -6662, stops 10.50(10.35), b5 88%, w2l 2 | n/a | n/a | n/a | n/a | -6104 (lots +42/wk) | n/a |
| S_r_C_B_15 | -521 $/wk, DD -5.5%, ww -2905, stops 10.27(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -521 (lots +0/wk) | n/a |
| S_r_C_B_20 | -521 $/wk, DD -5.5%, ww -2905, stops 10.27(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -521 (lots +0/wk) | n/a |
| S_r_C_W_x | -501 $/wk, DD -5.5%, ww -2905, stops 10.27(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | -502 (lots +0/wk) | n/a |
| A_c_T1_W_x | -1339 $/wk, DD -5.6%, ww +378, stops 9.51(10.35), b5 105%, w2l 1 | n/a | n/a | n/a | n/a | -1240 (lots -27/wk) | n/a |
| S_a_T1_N_15 | +652 $/wk, DD -5.9%, ww -3070, stops 18.11(10.35), b5 92%, w2l 0 | n/a | n/a | n/a | n/a | +500 (lots +42/wk) | n/a |
| S_a_T1_N_20 | +652 $/wk, DD -5.9%, ww -3070, stops 18.11(10.35), b5 92%, w2l 0 | n/a | n/a | n/a | n/a | +500 (lots +42/wk) | n/a |
| S_c_T1_N_15 | -1693 $/wk, DD -7.2%, ww -3759, stops 17.80(10.35), b5 93%, w2l 0 | n/a | n/a | n/a | n/a | -1846 (lots +42/wk) | n/a |
| S_c_T1_N_20 | -1693 $/wk, DD -7.2%, ww -3759, stops 17.80(10.35), b5 93%, w2l 0 | n/a | n/a | n/a | n/a | -1846 (lots +42/wk) | n/a |
| A_c_T2_B_15 | -7941 $/wk, DD -9.7%, ww -5562, stops 10.20(10.35), b5 84%, w2l 2 | n/a | n/a | n/a | n/a | -7984 (lots +12/wk) | n/a |
| A_c_T2_B_20 | -7941 $/wk, DD -9.7%, ww -5562, stops 10.20(10.35), b5 84%, w2l 2 | n/a | n/a | n/a | n/a | -7984 (lots +12/wk) | n/a |
| S_b_T1_N_15 | -1757 $/wk, DD -10.6%, ww -5550, stops 19.71(10.35), b5 88%, w2l 1 | n/a | n/a | n/a | n/a | -1918 (lots +44/wk) | n/a |
| S_b_T1_N_20 | -1757 $/wk, DD -10.6%, ww -5550, stops 19.71(10.35), b5 88%, w2l 1 | n/a | n/a | n/a | n/a | -1918 (lots +44/wk) | n/a |
| A_b_T1_W_x | -3209 $/wk, DD -11.2%, ww -9671, stops 9.59(10.35), b5 101%, w2l 1 | n/a | n/a | n/a | n/a | -3140 (lots -19/wk) | n/a |
| S_b_T1_B_15 | -3788 $/wk, DD -11.5%, ww -6260, stops 18.79(10.35), b5 84%, w2l 1 | n/a | n/a | n/a | n/a | -3887 (lots +27/wk) | n/a |
| S_b_T1_B_20 | -3788 $/wk, DD -11.5%, ww -6260, stops 18.79(10.35), b5 84%, w2l 1 | n/a | n/a | n/a | n/a | -3887 (lots +27/wk) | n/a |
| S_a_T1_W_x | -1109 $/wk, DD -14.3%, ww -5657, stops 9.51(10.35), b5 102%, w2l 1 | n/a | n/a | n/a | n/a | -1046 (lots -17/wk) | n/a |
| S_b_T2_B_15 | -6363 $/wk, DD -14.3%, ww -4654, stops 15.60(10.35), b5 75%, w2l 2 | n/a | n/a | n/a | n/a | -6405 (lots +11/wk) | n/a |
| S_b_T2_B_20 | -6363 $/wk, DD -14.3%, ww -4654, stops 15.60(10.35), b5 75%, w2l 2 | n/a | n/a | n/a | n/a | -6405 (lots +11/wk) | n/a |
| A_b_T2_W_x | -6174 $/wk, DD -19.4%, ww -10660, stops 9.74(10.35), b5 96%, w2l 1 | n/a | n/a | n/a | n/a | -6129 (lots -12/wk) | n/a |
| S_a_T1_B_15 | -131 $/wk, DD -20.1%, ww -8727, stops 17.35(10.35), b5 94%, w2l 1 | n/a | n/a | n/a | n/a | -222 (lots +25/wk) | n/a |
| S_a_T1_B_20 | -131 $/wk, DD -20.1%, ww -8727, stops 17.35(10.35), b5 94%, w2l 1 | n/a | n/a | n/a | n/a | -222 (lots +25/wk) | n/a |
| S_b_T2_W_x | -4790 $/wk, DD -20.8%, ww -8056, stops 9.59(10.35), b5 96%, w2l 1 | n/a | n/a | n/a | n/a | -4751 (lots -10/wk) | n/a |
| A_c_T1_N_15 | -4930 $/wk, DD -22.7%, ww -2300, stops 11.18(10.35), b5 90%, w2l 0 | n/a | n/a | n/a | n/a | -5100 (lots +46/wk) | n/a |
| A_c_T1_N_20 | -4930 $/wk, DD -22.7%, ww -2300, stops 11.18(10.35), b5 90%, w2l 0 | n/a | n/a | n/a | n/a | -5100 (lots +46/wk) | n/a |
| S_c_T2_B_15 | -4753 $/wk, DD -24.8%, ww -10137, stops 14.68(10.35), b5 91%, w2l 2 | n/a | n/a | n/a | n/a | -4792 (lots +11/wk) | n/a |
| S_c_T2_B_20 | -4753 $/wk, DD -24.8%, ww -10137, stops 14.68(10.35), b5 91%, w2l 2 | n/a | n/a | n/a | n/a | -4792 (lots +11/wk) | n/a |
| A_a_T1_W_x | -3171 $/wk, DD -24.9%, ww -17289, stops 10.27(10.35), b5 99%, w2l 1 | n/a | n/a | n/a | n/a | -3102 (lots -19/wk) | n/a |
| A_a_T1_B_15 | -4301 $/wk, DD -25.1%, ww -17407, stops 10.73(10.35), b5 86%, w2l 1 | n/a | n/a | n/a | n/a | -4416 (lots +31/wk) | n/a |
| A_a_T1_B_20 | -4301 $/wk, DD -25.1%, ww -17407, stops 10.73(10.35), b5 86%, w2l 1 | n/a | n/a | n/a | n/a | -4416 (lots +31/wk) | n/a |
| A_c_T2_W_x | -4912 $/wk, DD -25.3%, ww -13745, stops 9.59(10.35), b5 94%, w2l 1 | n/a | n/a | n/a | n/a | -4865 (lots -13/wk) | n/a |
| S_c_T2_W_x | -3504 $/wk, DD -31.3%, ww -13539, stops 9.43(10.35), b5 99%, w2l 1 | n/a | n/a | n/a | n/a | -3470 (lots -9/wk) | n/a |
| S_r_T1_W_x | -7087 $/wk, DD -36.5%, ww +10885, stops 7.76(10.35), b5 91%, w2l 3 | n/a | n/a | n/a | n/a | -6906 (lots -50/wk) | n/a |
| S_r_T1_B_15 | -6331 $/wk, DD -37.7%, ww +10114, stops 11.95(10.35), b5 95%, w2l 3 | -8855 $/wk, DD -37.7%, ww +10114, stops 8.48(10.99), b5 73%, w2l 4 | n/a | n/a | n/a | -6217 (lots -31/wk) | -8571 (lots -78/wk) |
| S_r_T1_B_20 | -6331 $/wk, DD -37.7%, ww +10114, stops 11.95(10.35), b5 95%, w2l 3 | n/a | n/a | n/a | n/a | -6217 (lots -31/wk) | n/a |
| A_c_T1_B_15 | -6477 $/wk, DD -46.3%, ww -5416, stops 10.27(10.35), b5 95%, w2l 2 | n/a | n/a | n/a | n/a | -6554 (lots +21/wk) | n/a |
| A_c_T1_B_20 | -6477 $/wk, DD -46.3%, ww -5416, stops 10.27(10.35), b5 95%, w2l 2 | n/a | n/a | n/a | n/a | -6554 (lots +21/wk) | n/a |
| A_a_T2_B_15 | -3957 $/wk, DD -47.7%, ww -22180, stops 10.20(10.35), b5 98%, w2l 1 | n/a | n/a | n/a | n/a | -4023 (lots +18/wk) | n/a |
| A_a_T2_B_20 | -3957 $/wk, DD -47.7%, ww -22180, stops 10.20(10.35), b5 98%, w2l 1 | n/a | n/a | n/a | n/a | -4023 (lots +18/wk) | n/a |
| A_a_T2_W_x | -5280 $/wk, DD -53.7%, ww -25309, stops 10.27(10.35), b5 98%, w2l 1 | n/a | n/a | n/a | n/a | -5243 (lots -10/wk) | n/a |
| S_a_T2_W_x | -5563 $/wk, DD -53.7%, ww -24191, stops 9.82(10.35), b5 101%, w2l 1 | n/a | n/a | n/a | n/a | -5525 (lots -10/wk) | n/a |
| S_a_T2_B_15 | -3288 $/wk, DD -54.7%, ww -24721, stops 14.30(10.35), b5 95%, w2l 1 | n/a | n/a | n/a | n/a | -3335 (lots +13/wk) | n/a |
| S_a_T2_B_20 | -3288 $/wk, DD -54.7%, ww -24721, stops 14.30(10.35), b5 95%, w2l 1 | n/a | n/a | n/a | n/a | -3335 (lots +13/wk) | n/a |
| S_r_T2_W_x | -11550 $/wk, DD -59.4%, ww -13996, stops 8.90(10.35), b5 101%, w2l 3 | n/a | n/a | n/a | n/a | -11450 (lots -27/wk) | n/a |
| S_r_T2_B_15 | -11461 $/wk, DD -62.0%, ww -13996, stops 11.18(10.35), b5 100%, w2l 3 | n/a | n/a | n/a | n/a | -11388 (lots -20/wk) | n/a |
| S_r_T2_B_20 | -11461 $/wk, DD -62.0%, ww -13996, stops 11.18(10.35), b5 100%, w2l 3 | n/a | n/a | n/a | n/a | -11388 (lots -20/wk) | n/a |
| A_r_T1_B_15 | -9605 $/wk, DD -78.1%, ww -3267, stops 8.90(10.35), b5 85%, w2l 3 | n/a | n/a | n/a | n/a | -9471 (lots -37/wk) | n/a |
| A_r_T1_B_20 | -9605 $/wk, DD -78.1%, ww -3267, stops 8.90(10.35), b5 85%, w2l 3 | n/a | n/a | n/a | n/a | -9471 (lots -37/wk) | n/a |
| A_r_T1_W_x | -10702 $/wk, DD -88.6%, ww -3924, stops 8.45(10.35), b5 85%, w2l 3 | n/a | n/a | n/a | n/a | -10491 (lots -58/wk) | n/a |
| A_r_T2_B_15 | -12271 $/wk, DD -109.2%, ww -12951, stops 9.97(10.35), b5 99%, w2l 1 | n/a | n/a | n/a | n/a | -12184 (lots -24/wk) | n/a |
| A_r_T2_B_20 | -12271 $/wk, DD -109.2%, ww -12951, stops 9.97(10.35), b5 99%, w2l 1 | n/a | n/a | n/a | n/a | -12184 (lots -24/wk) | n/a |
| A_r_T2_W_x | -12515 $/wk, DD -114.9%, ww -15687, stops 9.74(10.35), b5 101%, w2l 2 | n/a | n/a | n/a | n/a | -12400 (lots -31/wk) | n/a |

### Per session (asia london nyam nypm): best 3 cells per session by L3M drawdown cut that stay inside the tolerant gate on mean (L3M), with L6M/HOLD
**asia**
| cell | L3M | L6M | HOLD |
|---|---|---|---|
| A_a_C_B_15 | +441 $/wk, DD +0.6%, ww +298, stops 6.32(6.24), b5 101%, w2l 0 | n/a | n/a |
| A_a_C_B_20 | +441 $/wk, DD +0.6%, ww +298, stops 6.32(6.24), b5 101%, w2l 0 | n/a | n/a |
| A_a_C_W_x | +468 $/wk, DD +0.6%, ww +298, stops 6.32(6.24), b5 101%, w2l 0 | n/a | n/a |

**london**
| cell | L3M | L6M | HOLD |
|---|---|---|---|
| A_r_T2_N_15 | -7 $/wk, DD +14.7%, ww +5589, stops 3.04(2.74), b5 104%, w2l 0 | n/a | n/a |
| A_r_T2_N_20 | -7 $/wk, DD +14.7%, ww +5589, stops 3.04(2.74), b5 104%, w2l 0 | n/a | n/a |
| A_r_T1_N_15 | +6 $/wk, DD +10.4%, ww +4733, stops 3.04(2.74), b5 102%, w2l 0 | n/a | n/a |

**nyam**
| cell | L3M | L6M | HOLD |
|---|---|---|---|
| S_b_T1_B_15 | +495 $/wk, DD +43.1%, ww +2175, stops 2.43(1.29), b5 82%, w2l 1 | n/a | n/a |
| S_b_T1_B_20 | +495 $/wk, DD +43.1%, ww +2175, stops 2.43(1.29), b5 82%, w2l 1 | n/a | n/a |
| S_c_T1_B_15 | +320 $/wk, DD +33.1%, ww +773, stops 2.89(1.29), b5 80%, w2l 1 | -134 $/wk, DD -21.8%, ww +290, stops 2.13(1.67), b5 117%, w2l 3 | n/a |

**nypm**
| cell | L3M | L6M | HOLD |
|---|---|---|---|
| S_b_T1_N_15 | +619 $/wk, DD +58.6%, ww +1780, stops 0.84(0.08), b5 126%, w2l 0 | n/a | n/a |
| S_b_T1_N_20 | +619 $/wk, DD +58.6%, ww +1780, stops 0.84(0.08), b5 126%, w2l 0 | n/a | n/a |
| S_b_T1_B_15 | +118 $/wk, DD +31.5%, ww +460, stops 0.91(0.08), b5 108%, w2l 0 | n/a | n/a |

### Leads (tolerant gate in every scored window incl. L3M and L6M, DD cut > 0 in some window)
| cell | scope | L6M DD cut % | L6M d mean | windows | W44 removed L3M / L6M |
|---|---|---|---|---|---|
| A_b_C_B_15 | all | +6.8 | +259 | 2 | +538 $/wk, DD +0.6%, ww -72, stops 9.43(9.43), b5 100%, w2l 0 / +125 $/wk, DD +0.6%, ww -973, stops 10.46(10.54), b5 102%, w2l 0 |
| A_b_C_B_15 | london | +0.3 | +819 | 2 | +119 $/wk, DD +0.3%, ww +0, stops 2.59(2.59), b5 102%, w2l 0 / +671 $/wk, DD +0.3%, ww +0, stops 2.89(2.82), b5 103%, w2l 0 |

### Finalists: W44-removed and powered-horizon drawdown (FIRST PASS; scope all)
| finalist | W44 removed L3M | W44 removed L6M | powered-horizon DD (L6M weeks, else L3M) |
|---|---|---|---|
| A_b_C_B_15 | +538 $/wk, DD +0.6%, ww -72, stops 9.43(9.43), b5 100%, w2l 0 | +125 $/wk, DD +0.6%, ww -973, stops 10.46(10.54), b5 102%, w2l 0 | maxDD@186wk median -66154 vs ref -66904; 5th pct -112008 vs -112335 (weeks 27) |
| S_c_T1_B_15 | -3089 $/wk, DD +2.6%, ww +5183, stops 16.05(9.43), b5 94%, w2l 1 | -4005 $/wk, DD +2.6%, ww +5183, stops 12.52(10.54), b5 83%, w2l 1 | maxDD@186wk median -52374 vs ref -66904; 5th pct -83096 vs -112335 (weeks 27) |
| S_c_T1_B_20 | -3089 $/wk, DD +2.6%, ww +5183, stops 16.05(9.43), b5 94%, w2l 1 | n/a | maxDD@186wk median -82181 vs ref -90453; 5th pct -130998 vs -145482 (weeks 13) |

### Placebos (forecast shifted 11 / 23 / 37 trading days) beside the finalists, scope all, L6M (a real lead must beat all three)
| finalist | real L6M | pl11 | pl23 | pl37 |
|---|---|---|---|---|
| A_b_C_B_15 | +259 $/wk, DD +6.8%, ww +3510, stops 10.92(10.99), b5 102%, w2l 0 | -296 $/wk, DD -0.1%, ww -32, stops 11.07(10.99), b5 100%, w2l 0 | -393 $/wk, DD -0.0%, ww -10, stops 11.15(10.99), b5 96%, w2l 0 | -20 $/wk, DD -0.2%, ww -158, stops 11.03(10.99), b5 96%, w2l 0 |
| S_c_T1_B_15 | -3663 $/wk, DD +17.7%, ww +8971, stops 12.86(10.99), b5 83%, w2l 1 | -1839 $/wk, DD +5.8%, ww +14702, stops 13.12(10.99), b5 61%, w2l 2 | -8243 $/wk, DD -39.7%, ww -4609, stops 11.64(10.99), b5 52%, w2l 4 | -10289 $/wk, DD -69.4%, ww +3061, stops 11.11(10.99), b5 62%, w2l 3 |
| S_c_T1_B_20 | n/a | -1839 $/wk, DD +5.8%, ww +14702, stops 13.12(10.99), b5 61%, w2l 2 | -8243 $/wk, DD -39.7%, ww -4609, stops 11.64(10.99), b5 52%, w2l 4 | -10289 $/wk, DD -69.4%, ww +3061, stops 11.11(10.99), b5 62%, w2l 3 |

### Walk-forward every 2 weeks (pick on data before the block, apply to the next 2 weeks; scope all; needs L6M cells)
Blocks 9 (07-10..). Walk-forward: net 344022, maxDD -48690, worst week -32860 vs JN05W2 same days: net 337180, maxDD -52233, worst week -36371. Picks: 07-10 JN05W2 (no rule); 07-24 JN05W2 (no rule); 08-07 JN05W2 (no rule); 08-21 JN05W2 (no rule); 09-04 JN05W2 (no rule); 09-18 A_b_C_B_15; 10-02 A_b_C_B_15; 10-16 A_b_C_B_15; 10-30 A_b_C_B_15.

### Reading
Drawdown first; a result needs the gate in recent AND older windows and has to beat the 11/23/37-day placebos. Cells in the tables above that cut drawdown only through L3M, or only with full stops up, are not leads. No PASS claim.
## Target capped at the forecast
**VERDICT (plain, not a PASS; FIRST PASS; 15 of 26 global exact cap cells scored in L3M, per book x session exact cells still running): planted-edge check PASSED through the exact engine (look-ahead oracle target 0.9 x realised MFE: +85531 $/wk, DD +67.0%, ww +64263; this is a mechanism check, NOT a result); the reachable move is only weakly forecastable (R2 on ln MFE 0.03-0.14, quantile calibration good); in the exact L3M cells the cap at the forecast 50th-percentile move (horizon = 75th-percentile holding time) gives +1486 $/wk, DD -0.5%, ww -240 and the 75th-percentile cap +177 $/wk, DD +0.0%, ww +0, the remaining-range caps cut drawdown (own k1.0 -6226 $/wk, DD +27.0%, ww +12290; HAR k1.0 -7259 $/wk, DD +39.4%, ww +17319) but cost thousands per week. Best exact L3M cap cell inside the mean gate by DD: PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time (DD +7.9%, -120 $/wk). L6M/HOLD/older still to run before any verdict.**

Planted-edge check (H1) for the capping mechanism: cells `tcoracle0.9` / `0.6` set the target to 0.9 / 0.6 x the REALISED maximum favourable move (look-ahead, only to prove the mechanism can show an edge through the exact engine); they must come out strongly positive. Status below in the exact table. Until they do, an exact cap verdict is not stated.

Definition. Reachable move = maximum favourable excursion from the signal-second bar close over the book-session holding horizon H (H50/H75 = median / 75th percentile holding time of that book+session, causal), points. Model: walk-forward ridge (14-day blocks, expanding, min 90 days, per session) on ln((MFE+2)/price) from the Dial 10 own-bar inputs (last 15/30/60/120 min range and vol, same-clock normal, own session level, range used so far, elapsed fraction) plus the side-aware room in the session range so far; quantiles q = fitted + empirical training-residual quantile (50/60/75/90). Cap: target = min(book target 60 pts [58 after fills], q-quantile), stop, lots and every other level unchanged. Remaining-range cap: target = min(book target, k x (session range forecast - range printed so far)), forecast = own (price x exp(sf20), mean of the last 20 sessions) or T-RANGE2 HAR (fc_r2_har, available-epoch checked). Small caps (< 30 pts = 0.5 x stop): take / skip / half. EV target: argmax over T in [20, book target or 300] of T x P(MFE>=T) - stop x (1-P) with the lognormal forecast (ignores the stop-first ordering, so optimistic). Extension: if the forecast median MFE is >= m x book target, target = min(q50, 2 x book target). Lots/base basis: dollars are BASE lots (live x1.75 = multiply by 1.75); fee columns $4.84 beside raw $1.18 where shown.

### Item 1: calibration of the forecast quantiles (share of trades whose realized MFE exceeded the forecast quantile; a q-quantile should be exceeded 1-q of the time = 0.50 / 0.40 / 0.25 / 0.10) and R2 of ln MFE, per session
| H | session | window | n | >q50 | >q60 | >q75 | >q90 | R2 ln MFE | median q75 (pts) | share q75 < 60 |
|---|---|---|---|---|---|---|---|---|---|---|
| 50 | asia | older (<2026-05) | 5119 | 0.51 | 0.41 | 0.26 | 0.12 | 0.121 | 80 | 0.222 |
| 50 | asia | L6M | 2006 | 0.49 | 0.38 | 0.23 | 0.08 | 0.058 | 111 | 0.047 |
| 50 | asia | L3M | 875 | 0.46 | 0.34 | 0.20 | 0.07 | -0.014 | 90 | 0.098 |
| 50 | london | older (<2026-05) | 4892 | 0.51 | 0.41 | 0.26 | 0.11 | 0.142 | 62 | 0.438 |
| 50 | london | L6M | 1406 | 0.48 | 0.37 | 0.23 | 0.08 | 0.028 | 76 | 0.166 |
| 50 | london | L3M | 673 | 0.48 | 0.37 | 0.24 | 0.07 | -0.008 | 68 | 0.247 |
| 50 | nyam | older (<2026-05) | 4142 | 0.47 | 0.38 | 0.24 | 0.11 | 0.077 | 63 | 0.397 |
| 50 | nyam | L6M | 600 | 0.51 | 0.40 | 0.24 | 0.09 | 0.097 | 83 | 0.157 |
| 50 | nyam | L3M | 271 | 0.51 | 0.38 | 0.20 | 0.06 | 0.077 | 68 | 0.258 |
| 50 | nypm | older (<2026-05) | 817 | 0.48 | 0.40 | 0.26 | 0.13 | 0.073 | 62 | 0.419 |
| 50 | nypm | L6M | 150 | 0.59 | 0.50 | 0.33 | 0.13 | 0.221 | 71 | 0.307 |
| 50 | nypm | L3M | 56 | 0.50 | 0.36 | 0.21 | 0.09 | 0.104 | 54 | 0.589 |
| 50 | all | older (<2026-05) | 14970 | 0.50 | 0.40 | 0.26 | 0.12 | 0.123 | 68 | 0.352 |
| 50 | all | L6M | 4162 | 0.49 | 0.38 | 0.23 | 0.08 | 0.080 | 91 | 0.113 |
| 50 | all | L3M | 1875 | 0.47 | 0.36 | 0.21 | 0.07 | 0.014 | 76 | 0.189 |
| 75 | asia | older (<2026-05) | 5119 | 0.52 | 0.41 | 0.26 | 0.12 | 0.134 | 122 | 0.032 |
| 75 | asia | L6M | 2006 | 0.50 | 0.40 | 0.24 | 0.08 | 0.027 | 178 | 0.000 |
| 75 | asia | L3M | 875 | 0.45 | 0.35 | 0.20 | 0.05 | -0.016 | 156 | 0.000 |
| 75 | london | older (<2026-05) | 4891 | 0.51 | 0.42 | 0.27 | 0.11 | 0.157 | 101 | 0.100 |
| 75 | london | L6M | 1406 | 0.49 | 0.37 | 0.21 | 0.08 | 0.069 | 118 | 0.001 |
| 75 | london | L3M | 673 | 0.49 | 0.38 | 0.21 | 0.09 | 0.025 | 108 | 0.000 |
| 75 | nyam | older (<2026-05) | 4142 | 0.48 | 0.38 | 0.23 | 0.10 | 0.065 | 91 | 0.081 |
| 75 | nyam | L6M | 600 | 0.50 | 0.40 | 0.24 | 0.10 | 0.098 | 125 | 0.015 |
| 75 | nyam | L3M | 271 | 0.44 | 0.34 | 0.19 | 0.05 | 0.051 | 103 | 0.015 |
| 75 | nypm | older (<2026-05) | 812 | 0.49 | 0.37 | 0.26 | 0.11 | 0.043 | 87 | 0.095 |
| 75 | nypm | L6M | 150 | 0.53 | 0.46 | 0.34 | 0.17 | 0.179 | 117 | 0.013 |
| 75 | nypm | L3M | 56 | 0.41 | 0.30 | 0.21 | 0.07 | -0.076 | 93 | 0.036 |
| 75 | all | older (<2026-05) | 14964 | 0.51 | 0.40 | 0.25 | 0.11 | 0.131 | 102 | 0.071 |
| 75 | all | L6M | 4162 | 0.50 | 0.39 | 0.23 | 0.09 | 0.079 | 149 | 0.003 |
| 75 | all | L3M | 1875 | 0.46 | 0.36 | 0.20 | 0.06 | 0.032 | 128 | 0.003 |

### Items 3 and 4 (and 2): offline replay of the caps on the JN05W2 trade paths, all 43 months (estimate: 1-min paths, cap counted only before the exit bar, so cut/stop ordering is conservative; the exact cells below decide). d mean $/wk and DD cut % vs JN05W2 on the same trades, scope all, then per session for the cap with the most trades capped
| cap | small-cap rule | scope | window | d mean $/wk (live x1.75) | DD cut % | d worst week | d stops/wk | share capped | share where cap hit |
|---|---|---|---|---|---|---|---|---|---|
| q50_H50 | take | all | L3M | +409 (+715) | -3.9 | -1411 | +0.00 | 0.82 | 0.45 |
| q50_H50 | take | all | L6M | -96 (-169) | -3.9 | -1411 | +0.00 | 0.62 | 0.33 |
| q50_H50 | take | all | OLDER | -1795 (-3141) | +12.0 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | skip | all | L3M | -1581 (-2767) | -5.0 | -1996 | +0.00 | 0.82 | 0.45 |
| q50_H50 | skip | all | L6M | -1445 (-2528) | -5.0 | -1996 | +0.00 | 0.62 | 0.33 |
| q50_H50 | skip | all | OLDER | -2271 (-3975) | +17.4 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | half | all | L3M | -586 (-1026) | -4.4 | -1704 | +0.00 | 0.82 | 0.45 |
| q50_H50 | half | all | L6M | -771 (-1348) | -4.4 | -1704 | +0.00 | 0.62 | 0.33 |
| q50_H50 | half | all | OLDER | -2033 (-3558) | +16.5 | +13127 | +0.00 | 0.80 | 0.45 |
| q60_H50 | take | all | L3M | -1525 (-2668) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | take | all | L6M | -839 (-1469) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | take | all | OLDER | -1296 (-2267) | +12.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | skip | all | L3M | -3272 (-5726) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | skip | all | L6M | -1811 (-3170) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | skip | all | OLDER | -1648 (-2885) | +8.8 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | half | all | L3M | -2398 (-4197) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | half | all | L6M | -1325 (-2319) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | half | all | OLDER | -1472 (-2576) | +10.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q75_H50 | take | all | L3M | +414 (+725) | -0.4 | -214 | +0.00 | 0.21 | 0.11 |
| q75_H50 | take | all | L6M | -44 (-77) | -0.4 | -214 | +0.00 | 0.13 | 0.06 |
| q75_H50 | take | all | OLDER | -719 (-1258) | -1.1 | +13801 | +0.00 | 0.37 | 0.18 |
| q90_H50 | take | all | L3M | +191 (+334) | +0.0 | +0 | +0.00 | 0.02 | 0.01 |
| q90_H50 | take | all | L6M | +142 (+249) | +0.0 | +0 | +0.00 | 0.01 | 0.01 |
| q90_H50 | take | all | OLDER | -169 (-296) | -1.8 | +1686 | +0.00 | 0.08 | 0.03 |
| q50_H75 | take | all | L3M | +128 (+225) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | take | all | L6M | +624 (+1092) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | take | all | OLDER | -931 (-1628) | -13.1 | +11346 | +0.00 | 0.51 | 0.26 |
| q50_H75 | skip | all | L3M | +178 (+312) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | skip | all | L6M | +685 (+1198) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | skip | all | OLDER | -1302 (-2279) | -4.6 | +14384 | +0.00 | 0.51 | 0.26 |
| q50_H75 | half | all | L3M | +153 (+268) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | half | all | L6M | +654 (+1145) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | half | all | OLDER | -1116 (-1954) | -8.8 | +12865 | +0.00 | 0.51 | 0.26 |
| q60_H75 | take | all | L3M | +830 (+1452) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | take | all | L6M | +379 (+664) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | take | all | OLDER | -478 (-836) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | skip | all | L3M | +958 (+1677) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | skip | all | L6M | +421 (+737) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | skip | all | OLDER | -402 (-703) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | half | all | L3M | +894 (+1564) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | half | all | L6M | +400 (+700) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | half | all | OLDER | -440 (-769) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q75_H75 | take | all | L3M | +236 (+413) | +0.0 | +0 | +0.00 | 0.01 | 0.00 |
| q75_H75 | take | all | L6M | +105 (+185) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q75_H75 | take | all | OLDER | -255 (-446) | -1.9 | +1485 | +0.00 | 0.08 | 0.04 |
| q90_H75 | take | all | L3M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | L6M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | OLDER | +10 (+18) | -0.4 | +0 | +0.00 | 0.01 | 0.00 |
| rem_own_k0.5 | take | all | L3M | -6674 (-11680) | +8.8 | -1861 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | take | all | L6M | -13204 (-23108) | +8.7 | -1861 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | take | all | OLDER | -7381 (-12916) | -40.2 | +20529 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | skip | all | L3M | -5271 (-9225) | +21.7 | +2982 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | skip | all | L6M | -10625 (-18594) | +21.7 | +2982 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | skip | all | OLDER | -6272 (-10977) | +17.3 | +21712 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | half | all | L3M | -5973 (-10452) | +16.3 | +560 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | half | all | L6M | -11915 (-20851) | +16.3 | +560 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | half | all | OLDER | -6827 (-11946) | +0.6 | +23150 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.75 | take | all | L3M | -7140 (-12494) | +9.6 | +3294 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | take | all | L6M | -10636 (-18614) | +9.6 | +3294 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | take | all | OLDER | -5846 (-10230) | -24.0 | +12208 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | skip | all | L3M | -3661 (-6406) | +10.3 | +4045 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | skip | all | L6M | -6650 (-11638) | +10.3 | +4045 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | skip | all | OLDER | -3856 (-6749) | +16.1 | +19073 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | half | all | L3M | -5400 (-9450) | +13.0 | +3670 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | half | all | L6M | -8643 (-15126) | +13.0 | +3670 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | half | all | OLDER | -4851 (-8489) | +13.0 | +20157 | +0.00 | 0.73 | 0.53 |
| rem_own_k1.0 | take | all | L3M | -5516 (-9653) | +18.3 | +9104 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | take | all | L6M | -8765 (-15339) | +18.3 | +9104 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | take | all | OLDER | -5714 (-9999) | -58.2 | +11926 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | skip | all | L3M | -3265 (-5714) | +15.0 | +8858 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | skip | all | L6M | -5683 (-9944) | +15.0 | +8858 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | skip | all | OLDER | -3872 (-6775) | -61.0 | +20250 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | half | all | L3M | -4391 (-7683) | +18.5 | +8981 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | half | all | L6M | -7224 (-12642) | +18.5 | +8981 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | half | all | OLDER | -4793 (-8387) | -58.0 | +21393 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.25 | take | all | L3M | -3112 (-5446) | +24.4 | +13750 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | take | all | L6M | -8275 (-14481) | +24.4 | +13750 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | take | all | OLDER | -5400 (-9450) | -15.5 | +4336 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | skip | all | L3M | -456 (-797) | +22.4 | +13720 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | skip | all | L6M | -4232 (-7405) | +22.4 | +13720 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | skip | all | OLDER | -3310 (-5792) | -36.4 | +22803 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | half | all | L3M | -1784 (-3121) | +25.2 | +15286 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | half | all | L6M | -6253 (-10943) | +25.2 | +15286 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | half | all | OLDER | -4355 (-7621) | -18.3 | +15544 | +0.00 | 0.54 | 0.41 |

Per session, q60 H75 take-anyway and remaining-range k=1.25 (own):
| cap | session | window | d mean $/wk | DD cut % | d worst week | share capped |
|---|---|---|---|---|---|---|
| q60_H75 | asia | L3M | +221 | +0.0 | +0 | 0.02 |
| q60_H75 | asia | L6M | +110 | +0.0 | +0 | 0.01 |
| q60_H75 | asia | OLDER | -124 | -0.0 | +0 | 0.23 |
| q60_H75 | london | L3M | +745 | +3.8 | +0 | 0.16 |
| q60_H75 | london | L6M | +330 | +3.8 | +0 | 0.12 |
| q60_H75 | london | OLDER | -294 | -2.1 | +0 | 0.35 |
| q60_H75 | nyam | L3M | +61 | -7.2 | +0 | 0.15 |
| q60_H75 | nyam | L6M | -14 | +0.0 | +0 | 0.10 |
| q60_H75 | nyam | OLDER | -37 | -6.0 | +1403 | 0.37 |
| q60_H75 | nypm | L3M | -197 | -0.0 | +0 | 0.41 |
| q60_H75 | nypm | L6M | -47 | +0.0 | +0 | 0.20 |
| q60_H75 | nypm | OLDER | -22 | -5.4 | +0 | 0.33 |
| rem_own_k1.25 | asia | L3M | -4547 | +35.2 | +434 | 0.37 |
| rem_own_k1.25 | asia | L6M | -6717 | +27.1 | +434 | 0.38 |
| rem_own_k1.25 | asia | OLDER | -4532 | -27.4 | +10774 | 0.62 |
| rem_own_k1.25 | london | L3M | +2278 | +46.3 | +12347 | 0.24 |
| rem_own_k1.25 | london | L6M | +1196 | +46.3 | +12347 | 0.30 |
| rem_own_k1.25 | london | OLDER | -510 | +12.9 | +3024 | 0.51 |
| rem_own_k1.25 | nyam | L3M | -650 | +20.0 | +0 | 0.24 |
| rem_own_k1.25 | nyam | L6M | -2127 | -8.9 | +1531 | 0.39 |
| rem_own_k1.25 | nyam | OLDER | -53 | +10.3 | +7327 | 0.47 |
| rem_own_k1.25 | nypm | L3M | -192 | +21.8 | +1203 | 0.45 |
| rem_own_k1.25 | nypm | L6M | -627 | +21.8 | +1203 | 0.50 |
| rem_own_k1.25 | nypm | OLDER | -304 | -2.4 | -831 | 0.50 |

### Item 4 per book x session (all 43 months): trades whose 60-pt target lies beyond the forecast quantile, their fixed-target result, the capped replay, and how far trades run past the cap
| book | session | cap | trades | share beyond | fixed-target hit rate | fixed avg $/trade | capped avg $/trade | avg points run past cap |
|---|---|---|---|---|---|---|---|---|
| A7 | asia | q50_H75 | 1156 | 0.25 | 0.50 | 60 | 87 | 10.4 |
| A7 | asia | q60_H75 | 1156 | 0.13 | 0.47 | 4 | 26 | 8.8 |
| A7 | asia | q75_H75 | 1156 | 0.03 | 0.48 | 19 | 6 | 11.1 |
| A7 | asia | rem_own_k0.75 | 1156 | 0.74 | 0.52 | 126 | 22 | 32.9 |
| H7 | asia | q50_H75 | 700 | 0.33 | 0.49 | 164 | 181 | 11.3 |
| H7 | asia | q60_H75 | 700 | 0.18 | 0.56 | 447 | 414 | 10.7 |
| H7 | asia | q75_H75 | 700 | 0.02 | 0.50 | -318 | -267 | 16.1 |
| H7 | asia | rem_own_k0.75 | 700 | 0.71 | 0.48 | 208 | 55 | 27.8 |
| H7 | nyam | q50_H75 | 348 | 0.49 | 0.46 | 84 | 25 | 8.9 |
| H7 | nyam | q60_H75 | 348 | 0.25 | 0.47 | 96 | 46 | 7.4 |
| H7 | nyam | q75_H75 | 348 | 0.06 | 0.33 | -113 | -12 | 4.7 |
| H7 | nyam | rem_own_k0.75 | 348 | 0.66 | 0.47 | 62 | -35 | 23.3 |
| K7 | asia | q50_H75 | 2596 | 0.32 | 0.44 | 102 | 74 | 9.7 |
| K7 | asia | q60_H75 | 2596 | 0.19 | 0.44 | 111 | 90 | 7.6 |
| K7 | asia | q75_H75 | 2596 | 0.04 | 0.40 | 26 | 1 | 6.1 |
| K7 | asia | rem_own_k0.75 | 2596 | 0.68 | 0.44 | 88 | 0 | 27.2 |
| K7 | london | q50_H75 | 1781 | 0.57 | 0.43 | 62 | 37 | 10.9 |
| K7 | london | q60_H75 | 1781 | 0.33 | 0.44 | 60 | 35 | 9.4 |
| K7 | london | q75_H75 | 1781 | 0.12 | 0.48 | 138 | 101 | 6.5 |
| K7 | london | rem_own_k0.75 | 1781 | 0.69 | 0.43 | 45 | -12 | 27.4 |
| K7 | nyam | q50_H75 | 1565 | 0.57 | 0.42 | 21 | 18 | 10.0 |
| K7 | nyam | q60_H75 | 1565 | 0.32 | 0.40 | -4 | -17 | 9.0 |
| K7 | nyam | q75_H75 | 1565 | 0.07 | 0.41 | 40 | 36 | 16.3 |
| K7 | nyam | rem_own_k0.75 | 1565 | 0.70 | 0.39 | -21 | -38 | 26.0 |
| K7 | nypm | q50_H75 | 1136 | 0.50 | 0.36 | 65 | 54 | 8.1 |
| K7 | nypm | q60_H75 | 1136 | 0.31 | 0.34 | 62 | 48 | 5.6 |
| K7 | nypm | q75_H75 | 1136 | 0.09 | 0.29 | 155 | 179 | 3.5 |
| K7 | nypm | rem_own_k0.75 | 1136 | 0.71 | 0.37 | 72 | -30 | 23.7 |
| M7 | london | q50_H75 | 2489 | 0.42 | 0.43 | 45 | 40 | 10.0 |
| M7 | london | q60_H75 | 2489 | 0.24 | 0.43 | 32 | 26 | 8.2 |
| M7 | london | q75_H75 | 2489 | 0.06 | 0.38 | -74 | -97 | 7.1 |
| M7 | london | rem_own_k0.75 | 2489 | 0.59 | 0.39 | -40 | -29 | 22.9 |
| M7 | nyam | q50_H75 | 1496 | 0.52 | 0.43 | 49 | 22 | 8.6 |
| M7 | nyam | q60_H75 | 1496 | 0.27 | 0.44 | 76 | 57 | 7.2 |
| M7 | nyam | q75_H75 | 1496 | 0.06 | 0.44 | 127 | 131 | 4.9 |
| M7 | nyam | rem_own_k0.75 | 1496 | 0.69 | 0.42 | 30 | -36 | 27.3 |
| O7 | nyam | q50_H75 | 452 | 0.58 | 0.32 | 205 | 91 | 20.5 |
| O7 | nyam | q60_H75 | 452 | 0.37 | 0.31 | 156 | 118 | 16.9 |
| O7 | nyam | q75_H75 | 452 | 0.08 | 0.20 | -192 | -145 | 9.5 |
| O7 | nyam | rem_own_k0.75 | 452 | 0.31 | 0.30 | 120 | 82 | 20.6 |
| P7 | asia | q50_H75 | 2161 | 0.29 | 0.46 | 391 | 341 | 10.2 |
| P7 | asia | q60_H75 | 2161 | 0.16 | 0.48 | 487 | 484 | 9.3 |
| P7 | asia | q75_H75 | 2161 | 0.02 | 0.55 | 1227 | 969 | 5.7 |
| P7 | asia | rem_own_k0.75 | 2161 | 0.70 | 0.44 | 447 | 130 | 26.6 |
| P7 | london | q50_H75 | 1537 | 0.62 | 0.38 | 74 | 27 | 10.0 |
| P7 | london | q60_H75 | 1537 | 0.41 | 0.38 | 67 | 36 | 7.8 |
| P7 | london | q75_H75 | 1537 | 0.15 | 0.41 | 124 | 59 | 5.3 |
| P7 | london | rem_own_k0.75 | 1537 | 0.72 | 0.37 | -19 | -13 | 23.8 |
| P7 | nyam | q50_H75 | 1050 | 0.72 | 0.38 | 38 | 150 | 13.2 |
| P7 | nyam | q60_H75 | 1050 | 0.48 | 0.37 | -7 | 28 | 10.9 |
| P7 | nyam | q75_H75 | 1050 | 0.15 | 0.33 | -88 | -96 | 13.3 |
| P7 | nyam | rem_own_k0.75 | 1050 | 0.71 | 0.37 | -43 | 67 | 33.2 |
| U7 | asia | q50_H75 | 686 | 0.28 | 0.54 | 412 | 320 | 10.4 |
| U7 | asia | q60_H75 | 686 | 0.15 | 0.50 | 322 | 270 | 8.0 |
| U7 | asia | q75_H75 | 686 | 0.03 | 0.47 | -260 | -383 | 6.8 |
| U7 | asia | rem_own_k0.75 | 686 | 0.74 | 0.53 | 375 | 4 | 30.5 |
| U7 | london | q50_H75 | 645 | 0.27 | 0.46 | -102 | -183 | 8.7 |
| U7 | london | q60_H75 | 645 | 0.13 | 0.46 | -173 | -182 | 7.8 |
| U7 | london | q75_H75 | 645 | 0.03 | 0.50 | -396 | -466 | 5.4 |
| U7 | london | rem_own_k0.75 | 645 | 0.68 | 0.51 | 166 | 14 | 24.5 |

### Exact cap cells (global: all books at once; L3M, L6M when promoted; delta vs JN05W2)
| cell | L3M | L6M | HOLD | d mean/wk at $4.84 L3M |
|---|---|---|---|---|
| quantile 50 cap, horizon = 75th-percentile holding time | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | +1452 (lots +9/wk) |
| quantile 60 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 75 cap, horizon = 75th-percentile holding time | +177 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 101%, w2l 0 | n/a | n/a | +176 (lots +0/wk) |
| quantile 90 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 60 cap, horizon = median holding time | -1554 $/wk, DD +2.5%, ww +1445, stops 10.42(10.35), b5 89%, w2l 1 | n/a | n/a | -1658 (lots +29/wk) |
| quantile 75 cap, horizon = median holding time | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=0.5 | -8393 $/wk, DD +2.1%, ww +5889, stops 7.76(10.35), b5 57%, w2l 3 | n/a | n/a | -8805 (lots +113/wk) |
| remaining-range cap, forecast own 20-session mean, k=0.75 | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=1.0 | -6226 $/wk, DD +27.0%, ww +12290, stops 8.98(10.35), b5 66%, w2l 2 | n/a | n/a | -6458 (lots +63/wk) |
| remaining-range cap, forecast own 20-session mean, k=1.25 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.5 | -10795 $/wk, DD +40.3%, ww +11430, stops 7.00(10.35), b5 51%, w2l 4 | n/a | n/a | -11257 (lots +126/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.75 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.0 | -7259 $/wk, DD +39.4%, ww +17319, stops 7.76(10.35), b5 65%, w2l 2 | n/a | n/a | -7570 (lots +85/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.25 | pending | | | |
| EV-best target, bounded by the book target | -14326 $/wk, DD -25.6%, ww -15613, stops 8.45(10.35), b5 46%, w2l 3 | n/a | n/a | -14639 (lots +86/wk) |
| EV-best target, unbounded | pending | | | |
| extension m=1.0 | -110 $/wk, DD -53.4%, ww -2988, stops 11.72(10.35), b5 124%, w2l 2 | n/a | n/a | -18 (lots -25/wk) |
| extension m=1.5 | pending | | | |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts skipped | +1443 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | n/a | n/a | +1410 (lots +9/wk) |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts at half size | pending | | | |
| PLANTED-EDGE CHECK (look-ahead oracle 0.9 x realised MFE, not a result) | +85531 $/wk, DD +67.0%, ww +64263, stops 6.54(10.35), b5 259%, w2l 0 | n/a | n/a | +85219 (lots +85/wk) |
| PLANTED-EDGE CHECK (oracle 0.6 x realised MFE, not a result) | pending | | | |
| PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 | n/a | -125 (lots +1/wk) |
| PLACEBO pl23: quantile 50 cap, horizon = 75th-percentile holding time | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 | n/a | -871 (lots +3/wk) |
| PLACEBO pl37: quantile 50 cap, horizon = 75th-percentile holding time | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 | n/a | -612 (lots +2/wk) |
| PLACEBO plR1: quantile 50 cap, horizon = 75th-percentile holding time | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 | n/a | -670 (lots +4/wk) |

### The one candidate: forecast-quantile-50 cap, horizon = 75th-percentile holding time (L3M mean-only so far): all windows, W44 removed, placebos
| window | scope all | W44 removed |
|---|---|---|
| L3M | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 |
| L6M | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 |
| HOLD | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 |
| MID | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 |
| PREUW | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 |
Placebos (same cap, forecast features taken n sessions earlier at the same clock / a random earlier session), L3M then L6M when run:
| placebo | L3M | L6M |
|---|---|---|
| pl11 | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 |
| pl23 | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 |
| pl37 | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 |
| plR1 | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 |

### Per book x session exact cap cells (clean: one book in one session)
| slice | cap | L3M | May-Jul |
|---|---|---|---|
| A7 asia | quantile 50 cap, horizon = 75th-percentile holding time | -17 (live -30; $4.84 -17) DD +0.0% ww +0 stops 4.03(4.03) | n/a |

### FOR THE LIVE BUILD (what D7 computes at the signal second)
From its own 1-minute bars: last 15/30/60/120-minute range and realised vol, same-offset range over the previous 20 sessions (median), session ranges of the last 5/20 sessions, range so far, the entry position in the session range (favourable-side room), elapsed fraction of the session, ln of the book-session horizon; a small coefficient table per session (15 weights, mean, sd, intercept, four residual quantile offsets) refit every 14 days and shipped as a static file. Cap = min(60, price x exp(prediction + quantile offset) - 2); orders: the target limit is placed at the capped price. The remaining-range version needs the HAR session forecast (T-RANGE2 file) or D7 computes its own 20-session mean. No intraday feed from the box.


## Per book and session, clean, and the assembled stack
**STATUS (plain, not a PASS; B1 in progress, no "nothing passes" verdict is allowed until it is done): single-book single-session cells scored in L3M for 14 of 14 slices; slice picks so far: {}.**

Method (user order PART B, 2026-11-15): each cell = the Dial 10 hook restricted to ONE book in ONE session (every other book/session unchanged at JN05W2), exact engine, all layers ON, live caps. Dollars are BASE lots; the x1.75 live figure sits beside each headline (live); the $4.84 figure reprices every contract at the FEES.md $4.84 RT (engine raw $1.18). Compared on the same book x session slice of JN05W2 (day locks/caps still interact across books, which is why the cells are run for real and not sliced from the global run). B1a settings per slice: direction both / narrow-only / wide-only x gearing 0.5 / 1.0 at the 75th-percentile horizon, plus narrow/wide g1.0 at the median horizon; "fixed" = JN05W2 itself. Walk-forward: the pick for each slice is made on 2026-05..07 only (older than L3M); L3M (2026-08..10) is then out-of-sample. B1b (around each pick): lots cap 1.5/3, lots follow half the change, dead band 0/20%, target ratio 0.8/1.2, lever stop-only (sl: stop W, lots inverse, target in the same points) / target-only (tg) / size-only (sz: bracket fixed, lots follow the forecast), noise floor k = 3/4/5 x recent 5-minute ATR (bracket never narrower), clips 25..120 / 20..150.

### B1 table: per slice, every cell (L3M, delta vs JN05W2 same slice; May-Jul = the selection window)
| slice | setting | May-Jul (selection) | L3M (out of sample) | L6M |
|---|---|---|---|---|
| A7 asia | both/g1.0/H75 | -374 (live -654; $4.84 -370) DD -10.9% ww -261 stops 2.97(3.88) | +47 (live +83; $4.84 +40) DD +25.6% ww +1495 stops 5.55(4.03) | -163 (live -286; $4.84 -165) DD -29.2% ww +1253 stops 4.26(3.96) |
| A7 asia | narrow/g1.0/H75 | -419 (live -733; $4.84 -423) DD -0.6% ww -175 stops 4.49(3.88) | -18 (live -32; $4.84 -26) DD +17.7% ww +722 stops 5.63(4.03) | -219 (live -383; $4.84 -224) DD -19.1% ww +722 stops 5.06(3.96) |
| A7 asia | both/g0.5/H75 | -556 (live -973; $4.84 -553) DD -9.2% ww +72 stops 3.50(3.88) | -192 (live -336; $4.84 -195) DD +10.1% ww +412 stops 5.10(4.03) | -374 (live -654; $4.84 -374) DD -36.6% ww +412 stops 4.30(3.96) |
| A7 asia | narrow/g0.5/H75 | -350 (live -612; $4.84 -352) DD +0.0% ww +0 stops 4.34(3.88) | -186 (live -325; $4.84 -189) DD +10.0% ww +552 stops 5.10(4.03) | -268 (live -469; $4.84 -270) DD -15.8% ww +552 stops 4.72(3.96) |
| A7 asia | wide/g1.0/H75 | +19 (live +33; $4.84 +26) DD -10.9% ww +283 stops 2.51(3.88) | -15 (live -26; $4.84 -14) DD +2.4% ww -426 stops 3.96(4.03) | +2 (live +3; $4.84 +6) DD -13.6% ww -426 stops 3.23(3.96) |
| A7 asia | wide/g0.5/H75 | n/a | -1 (live -1; $4.84 -1) DD +1.4% ww -140 stops 4.03(4.03) | n/a |
| A7 asia | wide/g1.0/H50 | n/a | -48 (live -85; $4.84 -48) DD -3.0% ww -426 stops 3.88(4.03) | n/a |
| A7 asia | narrow/g1.0/H50 | n/a | -159 (live -279; $4.84 -171) DD -8.3% ww +877 stops 5.93(4.03) | n/a |
| H7 asia | wide/g0.5/H75 | n/a | +123 (live +215; $4.84 +123) DD +0.0% ww +0 stops 0.23(0.23) | n/a |
| H7 asia | wide/g1.0/H75 | n/a | -67 (live -118; $4.84 -67) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | wide/g1.0/H50 | n/a | -312 (live -546; $4.84 -312) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | both/g1.0/H75 | +1123 (live +1965; $4.84 +1129) DD +6.5% ww +1483 stops 0.53(0.61) | +177 (live +309; $4.84 +163) DD -33.6% ww -1228 stops 0.61(0.23) | +650 (live +1137; $4.84 +646) DD +6.5% ww +1483 stops 0.57(0.42) |
| H7 asia | narrow/g1.0/H75 | n/a | +244 (live +427; $4.84 +230) DD -33.6% ww -1228 stops 0.53(0.23) | n/a |
| H7 asia | both/g0.5/H75 | n/a | -574 (live -1004; $4.84 -580) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g0.5/H75 | n/a | -697 (live -1219; $4.84 -703) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g1.0/H50 | n/a | -355 (live -621; $4.84 -372) DD -120.5% ww -2166 stops 0.53(0.23) | n/a |
| H7 nyam | narrow/g1.0/H50 | n/a | +252 (live +441; $4.84 +252) DD +60.4% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | both/g1.0/H75 | n/a | +281 (live +491; $4.84 +280) DD +57.7% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | narrow/g1.0/H75 | -187 (live -328; $4.84 -188) DD -4.0% ww +0 stops 0.53(0.46) | +258 (live +452; $4.84 +258) DD +57.7% ww +480 stops 0.30(0.38) | +35 (live +62; $4.84 +35) DD +24.1% ww +480 stops 0.42(0.42) |
| H7 nyam | both/g0.5/H75 | +103 (live +180; $4.84 +103) DD +29.2% ww -83 stops 0.46(0.46) | +87 (live +153; $4.84 +87) DD +2.2% ww +195 stops 0.38(0.38) | +95 (live +167; $4.84 +95) DD +2.2% ww +195 stops 0.42(0.42) |
| H7 nyam | narrow/g0.5/H75 | n/a | +77 (live +134; $4.84 +77) DD +2.2% ww +195 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g0.5/H75 | n/a | +11 (live +19; $4.84 +11) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H75 | n/a | +22 (live +39; $4.84 +22) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H50 | n/a | +30 (live +53; $4.84 +30) DD +0.0% ww +0 stops 0.30(0.38) | n/a |
| K7 asia | wide/g1.0/H75 | n/a | +297 (live +520; $4.84 +298) DD +0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | wide/g0.5/H75 | n/a | -54 (live -94; $4.84 -54) DD -0.7% ww -404 stops 0.00(0.00) | n/a |
| K7 asia | narrow/g0.5/H75 | n/a | +1877 (live +3285; $4.84 +1855) DD -19.6% ww -2412 stops 0.00(0.00) | n/a |
| K7 asia | both/g0.5/H75 | n/a | +1823 (live +3191; $4.84 +1801) DD -28.8% ww -3232 stops 0.00(0.00) | n/a |
| K7 asia | wide/g1.0/H50 | n/a | -401 (live -702; $4.84 -400) DD -35.9% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | both/g1.0/H75 | n/a | +1292 (live +2261; $4.84 +1220) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H75 | n/a | +912 (live +1595; $4.84 +838) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H50 | n/a | +355 (live +621; $4.84 +268) DD -86.2% ww -5644 stops 0.00(0.00) | n/a |
| K7 london | both/g0.5/H75 | n/a | -9 (live -15; $4.84 -14) DD +8.7% ww +4326 stops 0.23(0.30) | n/a |
| K7 london | wide/g0.5/H75 | n/a | +27 (live +48; $4.84 +29) DD +0.5% ww +0 stops 0.30(0.30) | n/a |
| K7 london | wide/g1.0/H50 | n/a | +431 (live +755; $4.84 +433) DD -3.3% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g0.5/H75 | n/a | -123 (live -215; $4.84 -130) DD -4.2% ww +4733 stops 0.23(0.30) | n/a |
| K7 london | wide/g1.0/H75 | n/a | +157 (live +274; $4.84 +160) DD -4.8% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g1.0/H50 | n/a | -182 (live -319; $4.84 -204) DD -13.7% ww +3097 stops 0.23(0.30) | n/a |
| K7 london | both/g1.0/H75 | n/a | +481 (live +841; $4.84 +462) DD -25.5% ww +4257 stops 0.38(0.30) | n/a |
| K7 london | narrow/g1.0/H75 | n/a | -31 (live -55; $4.84 -55) DD -42.3% ww +4122 stops 0.38(0.30) | n/a |
| K7 nyam | narrow/g1.0/H50 | n/a | +769 (live +1345; $4.84 +761) DD +51.0% ww +2185 stops 0.00(0.00) | n/a |
| K7 nyam | both/g1.0/H75 | n/a | +1160 (live +2030; $4.84 +1153) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g1.0/H75 | n/a | +984 (live +1722; $4.84 +977) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g0.5/H75 | n/a | +668 (live +1170; $4.84 +667) DD +40.3% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | both/g0.5/H75 | n/a | +806 (live +1410; $4.84 +805) DD +39.5% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H75 | n/a | +176 (live +308; $4.84 +176) DD -0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H50 | n/a | +252 (live +441; $4.84 +253) DD -0.3% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g0.5/H75 | n/a | +137 (live +241; $4.84 +137) DD -0.8% ww +0 stops 0.00(0.00) | n/a |
| K7 nypm | wide/g1.0/H50 | n/a | +442 (live +773; $4.84 +442) DD +17.3% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | wide/g1.0/H75 | n/a | +70 (live +122; $4.84 +70) DD +13.1% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | both/g1.0/H75 | n/a | -184 (live -322; $4.84 -197) DD +9.8% ww +1145 stops 0.15(0.08) | n/a |
| K7 nypm | wide/g0.5/H75 | n/a | -4 (live -8; $4.84 -4) DD -1.5% ww -38 stops 0.00(0.08) | n/a |
| K7 nypm | narrow/g1.0/H50 | n/a | +48 (live +84; $4.84 +32) DD -1.9% ww +105 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g1.0/H75 | n/a | -254 (live -445; $4.84 -267) DD -3.3% ww +990 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g0.5/H75 | n/a | -266 (live -465; $4.84 -269) DD -26.7% ww +140 stops 0.08(0.08) | n/a |
| K7 nypm | both/g0.5/H75 | n/a | -270 (live -473; $4.84 -274) DD -27.3% ww +102 stops 0.00(0.08) | n/a |
| M7 london | wide/g1.0/H75 | n/a | +1614 (live +2824; $4.84 +1616) DD +4.9% ww +1190 stops 0.53(0.91) | n/a |
| M7 london | wide/g0.5/H75 | n/a | +688 (live +1204; $4.84 +689) DD +4.4% ww +1400 stops 0.84(0.91) | n/a |
| M7 london | wide/g1.0/H50 | n/a | +538 (live +942; $4.84 +540) DD -1.3% ww -80 stops 0.84(0.91) | n/a |
| M7 london | both/g0.5/H75 | n/a | +1147 (live +2008; $4.84 +1139) DD -8.1% ww +130 stops 1.07(0.91) | n/a |
| M7 london | narrow/g0.5/H75 | n/a | +417 (live +730; $4.84 +408) DD -10.9% ww -1075 stops 1.14(0.91) | n/a |
| M7 london | narrow/g1.0/H50 | n/a | +476 (live +833; $4.84 +446) DD -19.9% ww +1144 stops 1.45(0.91) | n/a |
| M7 london | narrow/g1.0/H75 | n/a | -366 (live -640; $4.84 -390) DD -20.4% ww +80 stops 1.29(0.91) | n/a |
| M7 london | both/g1.0/H75 | n/a | +1142 (live +1999; $4.84 +1121) DD -23.2% ww -729 stops 0.91(0.91) | n/a |
| M7 nyam | narrow/g1.0/H50 | n/a | +439 (live +769; $4.84 +424) DD +26.0% ww -222 stops 0.38(0.23) | n/a |
| M7 nyam | both/g0.5/H75 | n/a | +79 (live +138; $4.84 +75) DD +0.8% ww +194 stops 0.30(0.23) | n/a |
| M7 nyam | narrow/g0.5/H75 | n/a | +73 (live +127; $4.84 +69) DD +0.8% ww +194 stops 0.38(0.23) | n/a |
| M7 nyam | wide/g0.5/H75 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H75 | n/a | +16 (live +28; $4.84 +16) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H50 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | both/g1.0/H75 | n/a | +419 (live +733; $4.84 +405) DD -6.8% ww -991 stops 0.46(0.23) | n/a |
| M7 nyam | narrow/g1.0/H75 | n/a | +402 (live +704; $4.84 +388) DD -6.8% ww -991 stops 0.53(0.23) | n/a |
| P7 asia | narrow/g1.0/H50 | n/a | -3918 (live -6857; $4.84 -4186) DD -0.4% ww -4286 stops 0.46(0.15) | n/a |
| P7 asia | both/g0.5/H75 | n/a | -5946 (live -10406; $4.84 -6044) DD -1.0% ww +6944 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g0.5/H75 | n/a | -5762 (live -10084; $4.84 -5860) DD -1.0% ww +9022 stops 0.15(0.15) | n/a |
| P7 asia | wide/g0.5/H75 | n/a | -184 (live -322; $4.84 -183) DD -4.9% ww -2079 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g1.0/H75 | n/a | -2696 (live -4718; $4.84 -2882) DD -7.8% ww -10346 stops 0.53(0.15) | n/a |
| P7 asia | wide/g1.0/H50 | n/a | -816 (live -1428; $4.84 -812) DD -22.6% ww -9033 stops 0.15(0.15) | n/a |
| P7 asia | wide/g1.0/H75 | n/a | -491 (live -858; $4.84 -490) DD -25.2% ww -10331 stops 0.15(0.15) | n/a |
| P7 asia | both/g1.0/H75 | n/a | -3315 (live -5802; $4.84 -3501) DD -36.1% ww -13164 stops 0.53(0.15) | n/a |
| P7 london | both/g0.5/H75 | n/a | +894 (live +1565; $4.84 +886) DD +29.6% ww -1633 stops 0.08(0.08) | n/a |
| P7 london | narrow/g0.5/H75 | n/a | +386 (live +675; $4.84 +375) DD +28.5% ww -1328 stops 0.08(0.08) | n/a |
| P7 london | narrow/g1.0/H50 | n/a | +927 (live +1622; $4.84 +895) DD +19.7% ww -3009 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H75 | n/a | -142 (live -249; $4.84 -138) DD +2.7% ww -458 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H50 | n/a | +265 (live +464; $4.84 +266) DD +1.1% ww +0 stops 0.08(0.08) | n/a |
| P7 london | wide/g0.5/H75 | n/a | +385 (live +674; $4.84 +387) DD -1.9% ww -238 stops 0.08(0.08) | n/a |
| P7 london | both/g1.0/H75 | n/a | +1179 (live +2064; $4.84 +1145) DD -9.8% ww -5408 stops 0.15(0.08) | n/a |
| P7 london | narrow/g1.0/H75 | n/a | +1322 (live +2313; $4.84 +1282) DD -14.4% ww -5203 stops 0.15(0.08) | n/a |
| P7 nyam | both/g1.0/H75 | n/a | +697 (live +1220; $4.84 +685) DD +51.3% ww +354 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g1.0/H75 | n/a | +543 (live +951; $4.84 +529) DD +45.9% ww +324 stops 0.30(0.38) | n/a |
| P7 nyam | both/g0.5/H75 | n/a | +105 (live +184; $4.84 +99) DD +36.7% ww +238 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g0.5/H75 | n/a | -13 (live -23; $4.84 -20) DD +36.4% ww +262 stops 0.30(0.38) | n/a |
| P7 nyam | wide/g0.5/H75 | n/a | +118 (live +207; $4.84 +119) DD +0.3% ww -25 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H75 | n/a | +16 (live +27; $4.84 +17) DD -7.5% ww -105 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H50 | n/a | -544 (live -952; $4.84 -543) DD -47.7% ww -3348 stops 0.38(0.38) | n/a |
| U7 asia | narrow/g1.0/H50 | n/a | +1222 (live +2139; $4.84 +1201) DD +15.6% ww -265 stops 1.90(1.83) | n/a |
| U7 asia | both/g1.0/H75 | n/a | +71 (live +124; $4.84 +56) DD +8.3% ww -1836 stops 1.98(1.83) | n/a |
| U7 asia | narrow/g1.0/H75 | n/a | +502 (live +879; $4.84 +487) DD +8.3% ww +983 stops 1.98(1.83) | n/a |
| U7 asia | both/g0.5/H75 | n/a | -800 (live -1399; $4.84 -808) DD +6.6% ww -2883 stops 2.05(1.83) | n/a |
| U7 asia | narrow/g0.5/H75 | n/a | -162 (live -284; $4.84 -170) DD +6.6% ww +57 stops 2.05(1.83) | n/a |
| U7 asia | wide/g0.5/H75 | n/a | -637 (live -1115; $4.84 -637) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H75 | n/a | -431 (live -755; $4.84 -431) DD +0.0% ww -1836 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H50 | n/a | -648 (live -1134; $4.84 -648) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 london | narrow/g0.5/H75 | n/a | +393 (live +687; $4.84 +392) DD +17.2% ww +1796 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H75 | n/a | +246 (live +431; $4.84 +243) DD +3.1% ww -1185 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H50 | n/a | -41 (live -72; $4.84 -48) DD -9.9% ww -1991 stops 1.52(1.45) | n/a |
| U7 london | both/g0.5/H75 | n/a | -891 (live -1560; $4.84 -890) DD -25.4% ww -3538 stops 1.52(1.45) | n/a |
| U7 london | wide/g1.0/H50 | n/a | -839 (live -1468; $4.84 -837) DD -33.9% ww -4122 stops 1.37(1.45) | n/a |
| U7 london | wide/g0.5/H75 | n/a | -1284 (live -2247; $4.84 -1282) DD -44.3% ww -6280 stops 1.52(1.45) | n/a |
| U7 london | both/g1.0/H75 | n/a | -1728 (live -3025; $4.84 -1729) DD -105.5% ww -7540 stops 1.60(1.45) | n/a |
| U7 london | wide/g1.0/H75 | n/a | -1975 (live -3455; $4.84 -1972) DD -109.8% ww -6355 stops 1.60(1.45) | n/a |

### Summary per slice: pick made on May-Jul, result on L3M
| slice | pick | L3M result of the pick | verdict |
|---|---|---|---|
| A7 asia | pending | | |
| H7 asia | pending | | |
| H7 nyam | pending | | |
| K7 asia | pending | | |
| K7 london | pending | | |
| K7 nyam | pending | | |
| K7 nypm | pending | | |
| M7 london | pending | | |
| M7 nyam | pending | | |
| P7 asia | pending | | |
| P7 london | pending | | |
| P7 nyam | pending | | |
| U7 asia | pending | | |
| U7 london | pending | | |

### B2: why the global version adds full stops (narrow-only/both g1.0 H75 cell, L3M, trade tables)
Reference JN05W2 L3M (no O7): 1855 trades, stop rate 0.071, 132 stops (13 weeks).

**M1_75_g10_c1_d10_c20_tb_B**: 2038 trades (+183 vs JN05W2), stops 173 (+41), stop rate 0.085 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 437 | 0.103 | 3.05 | 94 |
| (40, 50] | 721 | 0.074 | 2.36 | 271 |
| (50, 55] | 232 | 0.099 | 1.97 | 169 |
| (55, 60] | 435 | 0.076 | 1.87 | 76 |
| (60, 70] | 75 | 0.120 | 2.01 | -385 |
| (70, 80] | 62 | 0.048 | 1.68 | -284 |
| (80, 101] | 76 | 0.092 | 1.13 | -591 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1543 | 0.069 | 2.21 | 54 |
| (3.0, 4.0] | 294 | 0.116 | 2.29 | 239 |
| (4.0, 5.0] | 74 | 0.108 | 2.31 | 364 |
| (5.0, 6.0] | 6 | 0.167 | 2.50 | 172 |
| (6.0, 8.0] | 4 | 0.000 | 1.00 | -119 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1068 | 0.096 | 1.00 | 4 |
| (1, 2] | 385 | 0.078 | 2.00 | 115 |
| (2, 3] | 215 | 0.093 | 3.00 | 23 |
| (3, 5] | 195 | 0.062 | 4.46 | 256 |
| (5, 8] | 138 | 0.065 | 6.70 | 690 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

**M1_75_g10_c1_d10_c20_tb_N**: 2072 trades (+217 vs JN05W2), stops 178 (+46), stop rate 0.086 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 449 | 0.105 | 3.02 | 97 |
| (40, 50] | 725 | 0.073 | 2.35 | 272 |
| (50, 55] | 236 | 0.102 | 1.97 | 150 |
| (55, 60] | 662 | 0.082 | 1.82 | -29 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1644 | 0.072 | 2.18 | 50 |
| (3.0, 4.0] | 264 | 0.121 | 2.38 | 348 |
| (4.0, 5.0] | 44 | 0.091 | 3.11 | 1063 |
| (5.0, 6.0] | 3 | 0.000 | 3.33 | 68 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1073 | 0.095 | 1.00 | 8 |
| (1, 2] | 413 | 0.085 | 2.00 | 117 |
| (2, 3] | 197 | 0.081 | 3.00 | 213 |
| (3, 5] | 217 | 0.074 | 4.43 | 196 |
| (5, 8] | 135 | 0.067 | 6.74 | 714 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

Reading of the W/ATR5 table: ATR5 = mean range of the last 14 five-minute buckets in points; a bracket 3x ATR5 or less is within ordinary 5-minute noise. The noise-floor cells (floor 3/4/5 x ATR5, narrowing only) are listed in B3.


### B3: levers (stop-only / target-only / both / size-only) and noise floor, per slice
| slice | cell | L3M | May-Jul |
|---|---|---|---|

### B4: assembled stack (each slice at its own walk-forward pick, run together)
(not run yet: starts when every slice has a pick)


## Target capped at the forecast
**VERDICT (plain, not a PASS; FIRST PASS; 15 of 26 global exact cap cells scored in L3M, per book x session exact cells still running): planted-edge check PASSED through the exact engine (look-ahead oracle target 0.9 x realised MFE: +85531 $/wk, DD +67.0%, ww +64263; this is a mechanism check, NOT a result); the reachable move is only weakly forecastable (R2 on ln MFE 0.03-0.14, quantile calibration good); in the exact L3M cells the cap at the forecast 50th-percentile move (horizon = 75th-percentile holding time) gives +1486 $/wk, DD -0.5%, ww -240 and the 75th-percentile cap +177 $/wk, DD +0.0%, ww +0, the remaining-range caps cut drawdown (own k1.0 -6226 $/wk, DD +27.0%, ww +12290; HAR k1.0 -7259 $/wk, DD +39.4%, ww +17319) but cost thousands per week. Best exact L3M cap cell inside the mean gate by DD: PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time (DD +7.9%, -120 $/wk). L6M/HOLD/older still to run before any verdict.**

Planted-edge check (H1) for the capping mechanism: cells `tcoracle0.9` / `0.6` set the target to 0.9 / 0.6 x the REALISED maximum favourable move (look-ahead, only to prove the mechanism can show an edge through the exact engine); they must come out strongly positive. Status below in the exact table. Until they do, an exact cap verdict is not stated.

Definition. Reachable move = maximum favourable excursion from the signal-second bar close over the book-session holding horizon H (H50/H75 = median / 75th percentile holding time of that book+session, causal), points. Model: walk-forward ridge (14-day blocks, expanding, min 90 days, per session) on ln((MFE+2)/price) from the Dial 10 own-bar inputs (last 15/30/60/120 min range and vol, same-clock normal, own session level, range used so far, elapsed fraction) plus the side-aware room in the session range so far; quantiles q = fitted + empirical training-residual quantile (50/60/75/90). Cap: target = min(book target 60 pts [58 after fills], q-quantile), stop, lots and every other level unchanged. Remaining-range cap: target = min(book target, k x (session range forecast - range printed so far)), forecast = own (price x exp(sf20), mean of the last 20 sessions) or T-RANGE2 HAR (fc_r2_har, available-epoch checked). Small caps (< 30 pts = 0.5 x stop): take / skip / half. EV target: argmax over T in [20, book target or 300] of T x P(MFE>=T) - stop x (1-P) with the lognormal forecast (ignores the stop-first ordering, so optimistic). Extension: if the forecast median MFE is >= m x book target, target = min(q50, 2 x book target). Lots/base basis: dollars are BASE lots (live x1.75 = multiply by 1.75); fee columns $4.84 beside raw $1.18 where shown.

### Item 1: calibration of the forecast quantiles (share of trades whose realized MFE exceeded the forecast quantile; a q-quantile should be exceeded 1-q of the time = 0.50 / 0.40 / 0.25 / 0.10) and R2 of ln MFE, per session
| H | session | window | n | >q50 | >q60 | >q75 | >q90 | R2 ln MFE | median q75 (pts) | share q75 < 60 |
|---|---|---|---|---|---|---|---|---|---|---|
| 50 | asia | older (<2026-05) | 5119 | 0.51 | 0.41 | 0.26 | 0.12 | 0.121 | 80 | 0.222 |
| 50 | asia | L6M | 2006 | 0.49 | 0.38 | 0.23 | 0.08 | 0.058 | 111 | 0.047 |
| 50 | asia | L3M | 875 | 0.46 | 0.34 | 0.20 | 0.07 | -0.014 | 90 | 0.098 |
| 50 | london | older (<2026-05) | 4892 | 0.51 | 0.41 | 0.26 | 0.11 | 0.142 | 62 | 0.438 |
| 50 | london | L6M | 1406 | 0.48 | 0.37 | 0.23 | 0.08 | 0.028 | 76 | 0.166 |
| 50 | london | L3M | 673 | 0.48 | 0.37 | 0.24 | 0.07 | -0.008 | 68 | 0.247 |
| 50 | nyam | older (<2026-05) | 4142 | 0.47 | 0.38 | 0.24 | 0.11 | 0.077 | 63 | 0.397 |
| 50 | nyam | L6M | 600 | 0.51 | 0.40 | 0.24 | 0.09 | 0.097 | 83 | 0.157 |
| 50 | nyam | L3M | 271 | 0.51 | 0.38 | 0.20 | 0.06 | 0.077 | 68 | 0.258 |
| 50 | nypm | older (<2026-05) | 817 | 0.48 | 0.40 | 0.26 | 0.13 | 0.073 | 62 | 0.419 |
| 50 | nypm | L6M | 150 | 0.59 | 0.50 | 0.33 | 0.13 | 0.221 | 71 | 0.307 |
| 50 | nypm | L3M | 56 | 0.50 | 0.36 | 0.21 | 0.09 | 0.104 | 54 | 0.589 |
| 50 | all | older (<2026-05) | 14970 | 0.50 | 0.40 | 0.26 | 0.12 | 0.123 | 68 | 0.352 |
| 50 | all | L6M | 4162 | 0.49 | 0.38 | 0.23 | 0.08 | 0.080 | 91 | 0.113 |
| 50 | all | L3M | 1875 | 0.47 | 0.36 | 0.21 | 0.07 | 0.014 | 76 | 0.189 |
| 75 | asia | older (<2026-05) | 5119 | 0.52 | 0.41 | 0.26 | 0.12 | 0.134 | 122 | 0.032 |
| 75 | asia | L6M | 2006 | 0.50 | 0.40 | 0.24 | 0.08 | 0.027 | 178 | 0.000 |
| 75 | asia | L3M | 875 | 0.45 | 0.35 | 0.20 | 0.05 | -0.016 | 156 | 0.000 |
| 75 | london | older (<2026-05) | 4891 | 0.51 | 0.42 | 0.27 | 0.11 | 0.157 | 101 | 0.100 |
| 75 | london | L6M | 1406 | 0.49 | 0.37 | 0.21 | 0.08 | 0.069 | 118 | 0.001 |
| 75 | london | L3M | 673 | 0.49 | 0.38 | 0.21 | 0.09 | 0.025 | 108 | 0.000 |
| 75 | nyam | older (<2026-05) | 4142 | 0.48 | 0.38 | 0.23 | 0.10 | 0.065 | 91 | 0.081 |
| 75 | nyam | L6M | 600 | 0.50 | 0.40 | 0.24 | 0.10 | 0.098 | 125 | 0.015 |
| 75 | nyam | L3M | 271 | 0.44 | 0.34 | 0.19 | 0.05 | 0.051 | 103 | 0.015 |
| 75 | nypm | older (<2026-05) | 812 | 0.49 | 0.37 | 0.26 | 0.11 | 0.043 | 87 | 0.095 |
| 75 | nypm | L6M | 150 | 0.53 | 0.46 | 0.34 | 0.17 | 0.179 | 117 | 0.013 |
| 75 | nypm | L3M | 56 | 0.41 | 0.30 | 0.21 | 0.07 | -0.076 | 93 | 0.036 |
| 75 | all | older (<2026-05) | 14964 | 0.51 | 0.40 | 0.25 | 0.11 | 0.131 | 102 | 0.071 |
| 75 | all | L6M | 4162 | 0.50 | 0.39 | 0.23 | 0.09 | 0.079 | 149 | 0.003 |
| 75 | all | L3M | 1875 | 0.46 | 0.36 | 0.20 | 0.06 | 0.032 | 128 | 0.003 |

### Items 3 and 4 (and 2): offline replay of the caps on the JN05W2 trade paths, all 43 months (estimate: 1-min paths, cap counted only before the exit bar, so cut/stop ordering is conservative; the exact cells below decide). d mean $/wk and DD cut % vs JN05W2 on the same trades, scope all, then per session for the cap with the most trades capped
| cap | small-cap rule | scope | window | d mean $/wk (live x1.75) | DD cut % | d worst week | d stops/wk | share capped | share where cap hit |
|---|---|---|---|---|---|---|---|---|---|
| q50_H50 | take | all | L3M | +409 (+715) | -3.9 | -1411 | +0.00 | 0.82 | 0.45 |
| q50_H50 | take | all | L6M | -96 (-169) | -3.9 | -1411 | +0.00 | 0.62 | 0.33 |
| q50_H50 | take | all | OLDER | -1795 (-3141) | +12.0 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | skip | all | L3M | -1581 (-2767) | -5.0 | -1996 | +0.00 | 0.82 | 0.45 |
| q50_H50 | skip | all | L6M | -1445 (-2528) | -5.0 | -1996 | +0.00 | 0.62 | 0.33 |
| q50_H50 | skip | all | OLDER | -2271 (-3975) | +17.4 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | half | all | L3M | -586 (-1026) | -4.4 | -1704 | +0.00 | 0.82 | 0.45 |
| q50_H50 | half | all | L6M | -771 (-1348) | -4.4 | -1704 | +0.00 | 0.62 | 0.33 |
| q50_H50 | half | all | OLDER | -2033 (-3558) | +16.5 | +13127 | +0.00 | 0.80 | 0.45 |
| q60_H50 | take | all | L3M | -1525 (-2668) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | take | all | L6M | -839 (-1469) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | take | all | OLDER | -1296 (-2267) | +12.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | skip | all | L3M | -3272 (-5726) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | skip | all | L6M | -1811 (-3170) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | skip | all | OLDER | -1648 (-2885) | +8.8 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | half | all | L3M | -2398 (-4197) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | half | all | L6M | -1325 (-2319) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | half | all | OLDER | -1472 (-2576) | +10.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q75_H50 | take | all | L3M | +414 (+725) | -0.4 | -214 | +0.00 | 0.21 | 0.11 |
| q75_H50 | take | all | L6M | -44 (-77) | -0.4 | -214 | +0.00 | 0.13 | 0.06 |
| q75_H50 | take | all | OLDER | -719 (-1258) | -1.1 | +13801 | +0.00 | 0.37 | 0.18 |
| q90_H50 | take | all | L3M | +191 (+334) | +0.0 | +0 | +0.00 | 0.02 | 0.01 |
| q90_H50 | take | all | L6M | +142 (+249) | +0.0 | +0 | +0.00 | 0.01 | 0.01 |
| q90_H50 | take | all | OLDER | -169 (-296) | -1.8 | +1686 | +0.00 | 0.08 | 0.03 |
| q50_H75 | take | all | L3M | +128 (+225) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | take | all | L6M | +624 (+1092) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | take | all | OLDER | -931 (-1628) | -13.1 | +11346 | +0.00 | 0.51 | 0.26 |
| q50_H75 | skip | all | L3M | +178 (+312) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | skip | all | L6M | +685 (+1198) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | skip | all | OLDER | -1302 (-2279) | -4.6 | +14384 | +0.00 | 0.51 | 0.26 |
| q50_H75 | half | all | L3M | +153 (+268) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | half | all | L6M | +654 (+1145) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | half | all | OLDER | -1116 (-1954) | -8.8 | +12865 | +0.00 | 0.51 | 0.26 |
| q60_H75 | take | all | L3M | +830 (+1452) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | take | all | L6M | +379 (+664) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | take | all | OLDER | -478 (-836) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | skip | all | L3M | +958 (+1677) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | skip | all | L6M | +421 (+737) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | skip | all | OLDER | -402 (-703) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | half | all | L3M | +894 (+1564) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | half | all | L6M | +400 (+700) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | half | all | OLDER | -440 (-769) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q75_H75 | take | all | L3M | +236 (+413) | +0.0 | +0 | +0.00 | 0.01 | 0.00 |
| q75_H75 | take | all | L6M | +105 (+185) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q75_H75 | take | all | OLDER | -255 (-446) | -1.9 | +1485 | +0.00 | 0.08 | 0.04 |
| q90_H75 | take | all | L3M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | L6M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | OLDER | +10 (+18) | -0.4 | +0 | +0.00 | 0.01 | 0.00 |
| rem_own_k0.5 | take | all | L3M | -6674 (-11680) | +8.8 | -1861 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | take | all | L6M | -13204 (-23108) | +8.7 | -1861 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | take | all | OLDER | -7381 (-12916) | -40.2 | +20529 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | skip | all | L3M | -5271 (-9225) | +21.7 | +2982 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | skip | all | L6M | -10625 (-18594) | +21.7 | +2982 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | skip | all | OLDER | -6272 (-10977) | +17.3 | +21712 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | half | all | L3M | -5973 (-10452) | +16.3 | +560 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | half | all | L6M | -11915 (-20851) | +16.3 | +560 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | half | all | OLDER | -6827 (-11946) | +0.6 | +23150 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.75 | take | all | L3M | -7140 (-12494) | +9.6 | +3294 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | take | all | L6M | -10636 (-18614) | +9.6 | +3294 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | take | all | OLDER | -5846 (-10230) | -24.0 | +12208 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | skip | all | L3M | -3661 (-6406) | +10.3 | +4045 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | skip | all | L6M | -6650 (-11638) | +10.3 | +4045 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | skip | all | OLDER | -3856 (-6749) | +16.1 | +19073 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | half | all | L3M | -5400 (-9450) | +13.0 | +3670 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | half | all | L6M | -8643 (-15126) | +13.0 | +3670 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | half | all | OLDER | -4851 (-8489) | +13.0 | +20157 | +0.00 | 0.73 | 0.53 |
| rem_own_k1.0 | take | all | L3M | -5516 (-9653) | +18.3 | +9104 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | take | all | L6M | -8765 (-15339) | +18.3 | +9104 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | take | all | OLDER | -5714 (-9999) | -58.2 | +11926 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | skip | all | L3M | -3265 (-5714) | +15.0 | +8858 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | skip | all | L6M | -5683 (-9944) | +15.0 | +8858 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | skip | all | OLDER | -3872 (-6775) | -61.0 | +20250 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | half | all | L3M | -4391 (-7683) | +18.5 | +8981 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | half | all | L6M | -7224 (-12642) | +18.5 | +8981 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | half | all | OLDER | -4793 (-8387) | -58.0 | +21393 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.25 | take | all | L3M | -3112 (-5446) | +24.4 | +13750 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | take | all | L6M | -8275 (-14481) | +24.4 | +13750 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | take | all | OLDER | -5400 (-9450) | -15.5 | +4336 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | skip | all | L3M | -456 (-797) | +22.4 | +13720 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | skip | all | L6M | -4232 (-7405) | +22.4 | +13720 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | skip | all | OLDER | -3310 (-5792) | -36.4 | +22803 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | half | all | L3M | -1784 (-3121) | +25.2 | +15286 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | half | all | L6M | -6253 (-10943) | +25.2 | +15286 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | half | all | OLDER | -4355 (-7621) | -18.3 | +15544 | +0.00 | 0.54 | 0.41 |

Per session, q60 H75 take-anyway and remaining-range k=1.25 (own):
| cap | session | window | d mean $/wk | DD cut % | d worst week | share capped |
|---|---|---|---|---|---|---|
| q60_H75 | asia | L3M | +221 | +0.0 | +0 | 0.02 |
| q60_H75 | asia | L6M | +110 | +0.0 | +0 | 0.01 |
| q60_H75 | asia | OLDER | -124 | -0.0 | +0 | 0.23 |
| q60_H75 | london | L3M | +745 | +3.8 | +0 | 0.16 |
| q60_H75 | london | L6M | +330 | +3.8 | +0 | 0.12 |
| q60_H75 | london | OLDER | -294 | -2.1 | +0 | 0.35 |
| q60_H75 | nyam | L3M | +61 | -7.2 | +0 | 0.15 |
| q60_H75 | nyam | L6M | -14 | +0.0 | +0 | 0.10 |
| q60_H75 | nyam | OLDER | -37 | -6.0 | +1403 | 0.37 |
| q60_H75 | nypm | L3M | -197 | -0.0 | +0 | 0.41 |
| q60_H75 | nypm | L6M | -47 | +0.0 | +0 | 0.20 |
| q60_H75 | nypm | OLDER | -22 | -5.4 | +0 | 0.33 |
| rem_own_k1.25 | asia | L3M | -4547 | +35.2 | +434 | 0.37 |
| rem_own_k1.25 | asia | L6M | -6717 | +27.1 | +434 | 0.38 |
| rem_own_k1.25 | asia | OLDER | -4532 | -27.4 | +10774 | 0.62 |
| rem_own_k1.25 | london | L3M | +2278 | +46.3 | +12347 | 0.24 |
| rem_own_k1.25 | london | L6M | +1196 | +46.3 | +12347 | 0.30 |
| rem_own_k1.25 | london | OLDER | -510 | +12.9 | +3024 | 0.51 |
| rem_own_k1.25 | nyam | L3M | -650 | +20.0 | +0 | 0.24 |
| rem_own_k1.25 | nyam | L6M | -2127 | -8.9 | +1531 | 0.39 |
| rem_own_k1.25 | nyam | OLDER | -53 | +10.3 | +7327 | 0.47 |
| rem_own_k1.25 | nypm | L3M | -192 | +21.8 | +1203 | 0.45 |
| rem_own_k1.25 | nypm | L6M | -627 | +21.8 | +1203 | 0.50 |
| rem_own_k1.25 | nypm | OLDER | -304 | -2.4 | -831 | 0.50 |

### Item 4 per book x session (all 43 months): trades whose 60-pt target lies beyond the forecast quantile, their fixed-target result, the capped replay, and how far trades run past the cap
| book | session | cap | trades | share beyond | fixed-target hit rate | fixed avg $/trade | capped avg $/trade | avg points run past cap |
|---|---|---|---|---|---|---|---|---|
| A7 | asia | q50_H75 | 1156 | 0.25 | 0.50 | 60 | 87 | 10.4 |
| A7 | asia | q60_H75 | 1156 | 0.13 | 0.47 | 4 | 26 | 8.8 |
| A7 | asia | q75_H75 | 1156 | 0.03 | 0.48 | 19 | 6 | 11.1 |
| A7 | asia | rem_own_k0.75 | 1156 | 0.74 | 0.52 | 126 | 22 | 32.9 |
| H7 | asia | q50_H75 | 700 | 0.33 | 0.49 | 164 | 181 | 11.3 |
| H7 | asia | q60_H75 | 700 | 0.18 | 0.56 | 447 | 414 | 10.7 |
| H7 | asia | q75_H75 | 700 | 0.02 | 0.50 | -318 | -267 | 16.1 |
| H7 | asia | rem_own_k0.75 | 700 | 0.71 | 0.48 | 208 | 55 | 27.8 |
| H7 | nyam | q50_H75 | 348 | 0.49 | 0.46 | 84 | 25 | 8.9 |
| H7 | nyam | q60_H75 | 348 | 0.25 | 0.47 | 96 | 46 | 7.4 |
| H7 | nyam | q75_H75 | 348 | 0.06 | 0.33 | -113 | -12 | 4.7 |
| H7 | nyam | rem_own_k0.75 | 348 | 0.66 | 0.47 | 62 | -35 | 23.3 |
| K7 | asia | q50_H75 | 2596 | 0.32 | 0.44 | 102 | 74 | 9.7 |
| K7 | asia | q60_H75 | 2596 | 0.19 | 0.44 | 111 | 90 | 7.6 |
| K7 | asia | q75_H75 | 2596 | 0.04 | 0.40 | 26 | 1 | 6.1 |
| K7 | asia | rem_own_k0.75 | 2596 | 0.68 | 0.44 | 88 | 0 | 27.2 |
| K7 | london | q50_H75 | 1781 | 0.57 | 0.43 | 62 | 37 | 10.9 |
| K7 | london | q60_H75 | 1781 | 0.33 | 0.44 | 60 | 35 | 9.4 |
| K7 | london | q75_H75 | 1781 | 0.12 | 0.48 | 138 | 101 | 6.5 |
| K7 | london | rem_own_k0.75 | 1781 | 0.69 | 0.43 | 45 | -12 | 27.4 |
| K7 | nyam | q50_H75 | 1565 | 0.57 | 0.42 | 21 | 18 | 10.0 |
| K7 | nyam | q60_H75 | 1565 | 0.32 | 0.40 | -4 | -17 | 9.0 |
| K7 | nyam | q75_H75 | 1565 | 0.07 | 0.41 | 40 | 36 | 16.3 |
| K7 | nyam | rem_own_k0.75 | 1565 | 0.70 | 0.39 | -21 | -38 | 26.0 |
| K7 | nypm | q50_H75 | 1136 | 0.50 | 0.36 | 65 | 54 | 8.1 |
| K7 | nypm | q60_H75 | 1136 | 0.31 | 0.34 | 62 | 48 | 5.6 |
| K7 | nypm | q75_H75 | 1136 | 0.09 | 0.29 | 155 | 179 | 3.5 |
| K7 | nypm | rem_own_k0.75 | 1136 | 0.71 | 0.37 | 72 | -30 | 23.7 |
| M7 | london | q50_H75 | 2489 | 0.42 | 0.43 | 45 | 40 | 10.0 |
| M7 | london | q60_H75 | 2489 | 0.24 | 0.43 | 32 | 26 | 8.2 |
| M7 | london | q75_H75 | 2489 | 0.06 | 0.38 | -74 | -97 | 7.1 |
| M7 | london | rem_own_k0.75 | 2489 | 0.59 | 0.39 | -40 | -29 | 22.9 |
| M7 | nyam | q50_H75 | 1496 | 0.52 | 0.43 | 49 | 22 | 8.6 |
| M7 | nyam | q60_H75 | 1496 | 0.27 | 0.44 | 76 | 57 | 7.2 |
| M7 | nyam | q75_H75 | 1496 | 0.06 | 0.44 | 127 | 131 | 4.9 |
| M7 | nyam | rem_own_k0.75 | 1496 | 0.69 | 0.42 | 30 | -36 | 27.3 |
| O7 | nyam | q50_H75 | 452 | 0.58 | 0.32 | 205 | 91 | 20.5 |
| O7 | nyam | q60_H75 | 452 | 0.37 | 0.31 | 156 | 118 | 16.9 |
| O7 | nyam | q75_H75 | 452 | 0.08 | 0.20 | -192 | -145 | 9.5 |
| O7 | nyam | rem_own_k0.75 | 452 | 0.31 | 0.30 | 120 | 82 | 20.6 |
| P7 | asia | q50_H75 | 2161 | 0.29 | 0.46 | 391 | 341 | 10.2 |
| P7 | asia | q60_H75 | 2161 | 0.16 | 0.48 | 487 | 484 | 9.3 |
| P7 | asia | q75_H75 | 2161 | 0.02 | 0.55 | 1227 | 969 | 5.7 |
| P7 | asia | rem_own_k0.75 | 2161 | 0.70 | 0.44 | 447 | 130 | 26.6 |
| P7 | london | q50_H75 | 1537 | 0.62 | 0.38 | 74 | 27 | 10.0 |
| P7 | london | q60_H75 | 1537 | 0.41 | 0.38 | 67 | 36 | 7.8 |
| P7 | london | q75_H75 | 1537 | 0.15 | 0.41 | 124 | 59 | 5.3 |
| P7 | london | rem_own_k0.75 | 1537 | 0.72 | 0.37 | -19 | -13 | 23.8 |
| P7 | nyam | q50_H75 | 1050 | 0.72 | 0.38 | 38 | 150 | 13.2 |
| P7 | nyam | q60_H75 | 1050 | 0.48 | 0.37 | -7 | 28 | 10.9 |
| P7 | nyam | q75_H75 | 1050 | 0.15 | 0.33 | -88 | -96 | 13.3 |
| P7 | nyam | rem_own_k0.75 | 1050 | 0.71 | 0.37 | -43 | 67 | 33.2 |
| U7 | asia | q50_H75 | 686 | 0.28 | 0.54 | 412 | 320 | 10.4 |
| U7 | asia | q60_H75 | 686 | 0.15 | 0.50 | 322 | 270 | 8.0 |
| U7 | asia | q75_H75 | 686 | 0.03 | 0.47 | -260 | -383 | 6.8 |
| U7 | asia | rem_own_k0.75 | 686 | 0.74 | 0.53 | 375 | 4 | 30.5 |
| U7 | london | q50_H75 | 645 | 0.27 | 0.46 | -102 | -183 | 8.7 |
| U7 | london | q60_H75 | 645 | 0.13 | 0.46 | -173 | -182 | 7.8 |
| U7 | london | q75_H75 | 645 | 0.03 | 0.50 | -396 | -466 | 5.4 |
| U7 | london | rem_own_k0.75 | 645 | 0.68 | 0.51 | 166 | 14 | 24.5 |

### Exact cap cells (global: all books at once; L3M, L6M when promoted; delta vs JN05W2)
| cell | L3M | L6M | HOLD | d mean/wk at $4.84 L3M |
|---|---|---|---|---|
| quantile 50 cap, horizon = 75th-percentile holding time | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | +1452 (lots +9/wk) |
| quantile 60 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 75 cap, horizon = 75th-percentile holding time | +177 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 101%, w2l 0 | n/a | n/a | +176 (lots +0/wk) |
| quantile 90 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 60 cap, horizon = median holding time | -1554 $/wk, DD +2.5%, ww +1445, stops 10.42(10.35), b5 89%, w2l 1 | n/a | n/a | -1658 (lots +29/wk) |
| quantile 75 cap, horizon = median holding time | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=0.5 | -8393 $/wk, DD +2.1%, ww +5889, stops 7.76(10.35), b5 57%, w2l 3 | n/a | n/a | -8805 (lots +113/wk) |
| remaining-range cap, forecast own 20-session mean, k=0.75 | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=1.0 | -6226 $/wk, DD +27.0%, ww +12290, stops 8.98(10.35), b5 66%, w2l 2 | n/a | n/a | -6458 (lots +63/wk) |
| remaining-range cap, forecast own 20-session mean, k=1.25 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.5 | -10795 $/wk, DD +40.3%, ww +11430, stops 7.00(10.35), b5 51%, w2l 4 | n/a | n/a | -11257 (lots +126/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.75 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.0 | -7259 $/wk, DD +39.4%, ww +17319, stops 7.76(10.35), b5 65%, w2l 2 | n/a | n/a | -7570 (lots +85/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.25 | pending | | | |
| EV-best target, bounded by the book target | -14326 $/wk, DD -25.6%, ww -15613, stops 8.45(10.35), b5 46%, w2l 3 | n/a | n/a | -14639 (lots +86/wk) |
| EV-best target, unbounded | pending | | | |
| extension m=1.0 | -110 $/wk, DD -53.4%, ww -2988, stops 11.72(10.35), b5 124%, w2l 2 | n/a | n/a | -18 (lots -25/wk) |
| extension m=1.5 | pending | | | |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts skipped | +1443 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | n/a | n/a | +1410 (lots +9/wk) |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts at half size | pending | | | |
| PLANTED-EDGE CHECK (look-ahead oracle 0.9 x realised MFE, not a result) | +85531 $/wk, DD +67.0%, ww +64263, stops 6.54(10.35), b5 259%, w2l 0 | n/a | n/a | +85219 (lots +85/wk) |
| PLANTED-EDGE CHECK (oracle 0.6 x realised MFE, not a result) | pending | | | |
| PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 | n/a | -125 (lots +1/wk) |
| PLACEBO pl23: quantile 50 cap, horizon = 75th-percentile holding time | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 | n/a | -871 (lots +3/wk) |
| PLACEBO pl37: quantile 50 cap, horizon = 75th-percentile holding time | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 | n/a | -612 (lots +2/wk) |
| PLACEBO plR1: quantile 50 cap, horizon = 75th-percentile holding time | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 | n/a | -670 (lots +4/wk) |

### The one candidate: forecast-quantile-50 cap, horizon = 75th-percentile holding time (L3M mean-only so far): all windows, W44 removed, placebos
| window | scope all | W44 removed |
|---|---|---|
| L3M | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 |
| L6M | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 |
| HOLD | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 |
| MID | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 |
| PREUW | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 |
Placebos (same cap, forecast features taken n sessions earlier at the same clock / a random earlier session), L3M then L6M when run:
| placebo | L3M | L6M |
|---|---|---|
| pl11 | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 |
| pl23 | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 |
| pl37 | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 |
| plR1 | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 |

### Per book x session exact cap cells (clean: one book in one session)
| slice | cap | L3M | May-Jul |
|---|---|---|---|
| A7 asia | quantile 50 cap, horizon = 75th-percentile holding time | -17 (live -30; $4.84 -17) DD +0.0% ww +0 stops 4.03(4.03) | n/a |

### FOR THE LIVE BUILD (what D7 computes at the signal second)
From its own 1-minute bars: last 15/30/60/120-minute range and realised vol, same-offset range over the previous 20 sessions (median), session ranges of the last 5/20 sessions, range so far, the entry position in the session range (favourable-side room), elapsed fraction of the session, ln of the book-session horizon; a small coefficient table per session (15 weights, mean, sd, intercept, four residual quantile offsets) refit every 14 days and shipped as a static file. Cap = min(60, price x exp(prediction + quantile offset) - 2); orders: the target limit is placed at the capped price. The remaining-range version needs the HAR session forecast (T-RANGE2 file) or D7 computes its own 20-session mean. No intraday feed from the box.


## Per book and session, clean, and the assembled stack
**STATUS (plain, not a PASS; B1 in progress, no "nothing passes" verdict is allowed until it is done): single-book single-session cells scored in L3M for 14 of 14 slices; slice picks so far: {}.**

Method (user order PART B, 2026-11-15): each cell = the Dial 10 hook restricted to ONE book in ONE session (every other book/session unchanged at JN05W2), exact engine, all layers ON, live caps. Dollars are BASE lots; the x1.75 live figure sits beside each headline (live); the $4.84 figure reprices every contract at the FEES.md $4.84 RT (engine raw $1.18). Compared on the same book x session slice of JN05W2 (day locks/caps still interact across books, which is why the cells are run for real and not sliced from the global run). B1a settings per slice: direction both / narrow-only / wide-only x gearing 0.5 / 1.0 at the 75th-percentile horizon, plus narrow/wide g1.0 at the median horizon; "fixed" = JN05W2 itself. Walk-forward: the pick for each slice is made on 2026-05..07 only (older than L3M); L3M (2026-08..10) is then out-of-sample. B1b (around each pick): lots cap 1.5/3, lots follow half the change, dead band 0/20%, target ratio 0.8/1.2, lever stop-only (sl: stop W, lots inverse, target in the same points) / target-only (tg) / size-only (sz: bracket fixed, lots follow the forecast), noise floor k = 3/4/5 x recent 5-minute ATR (bracket never narrower), clips 25..120 / 20..150.

### B1 table: per slice, every cell (L3M, delta vs JN05W2 same slice; May-Jul = the selection window)
| slice | setting | May-Jul (selection) | L3M (out of sample) | L6M |
|---|---|---|---|---|
| A7 asia | both/g1.0/H75 | -374 (live -654; $4.84 -370) DD -10.9% ww -261 stops 2.97(3.88) | +47 (live +83; $4.84 +40) DD +25.6% ww +1495 stops 5.55(4.03) | -163 (live -286; $4.84 -165) DD -29.2% ww +1253 stops 4.26(3.96) |
| A7 asia | narrow/g1.0/H75 | -419 (live -733; $4.84 -423) DD -0.6% ww -175 stops 4.49(3.88) | -18 (live -32; $4.84 -26) DD +17.7% ww +722 stops 5.63(4.03) | -219 (live -383; $4.84 -224) DD -19.1% ww +722 stops 5.06(3.96) |
| A7 asia | both/g0.5/H75 | -556 (live -973; $4.84 -553) DD -9.2% ww +72 stops 3.50(3.88) | -192 (live -336; $4.84 -195) DD +10.1% ww +412 stops 5.10(4.03) | -374 (live -654; $4.84 -374) DD -36.6% ww +412 stops 4.30(3.96) |
| A7 asia | narrow/g0.5/H75 | -350 (live -612; $4.84 -352) DD +0.0% ww +0 stops 4.34(3.88) | -186 (live -325; $4.84 -189) DD +10.0% ww +552 stops 5.10(4.03) | -268 (live -469; $4.84 -270) DD -15.8% ww +552 stops 4.72(3.96) |
| A7 asia | wide/g1.0/H75 | +19 (live +33; $4.84 +26) DD -10.9% ww +283 stops 2.51(3.88) | -15 (live -26; $4.84 -14) DD +2.4% ww -426 stops 3.96(4.03) | +2 (live +3; $4.84 +6) DD -13.6% ww -426 stops 3.23(3.96) |
| A7 asia | wide/g0.5/H75 | n/a | -1 (live -1; $4.84 -1) DD +1.4% ww -140 stops 4.03(4.03) | n/a |
| A7 asia | wide/g1.0/H50 | n/a | -48 (live -85; $4.84 -48) DD -3.0% ww -426 stops 3.88(4.03) | n/a |
| A7 asia | narrow/g1.0/H50 | n/a | -159 (live -279; $4.84 -171) DD -8.3% ww +877 stops 5.93(4.03) | n/a |
| H7 asia | wide/g0.5/H75 | n/a | +123 (live +215; $4.84 +123) DD +0.0% ww +0 stops 0.23(0.23) | n/a |
| H7 asia | wide/g1.0/H75 | n/a | -67 (live -118; $4.84 -67) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | wide/g1.0/H50 | n/a | -312 (live -546; $4.84 -312) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | both/g1.0/H75 | +1123 (live +1965; $4.84 +1129) DD +6.5% ww +1483 stops 0.53(0.61) | +177 (live +309; $4.84 +163) DD -33.6% ww -1228 stops 0.61(0.23) | +650 (live +1137; $4.84 +646) DD +6.5% ww +1483 stops 0.57(0.42) |
| H7 asia | narrow/g1.0/H75 | n/a | +244 (live +427; $4.84 +230) DD -33.6% ww -1228 stops 0.53(0.23) | n/a |
| H7 asia | both/g0.5/H75 | n/a | -574 (live -1004; $4.84 -580) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g0.5/H75 | n/a | -697 (live -1219; $4.84 -703) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g1.0/H50 | n/a | -355 (live -621; $4.84 -372) DD -120.5% ww -2166 stops 0.53(0.23) | n/a |
| H7 nyam | narrow/g1.0/H50 | n/a | +252 (live +441; $4.84 +252) DD +60.4% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | both/g1.0/H75 | n/a | +281 (live +491; $4.84 +280) DD +57.7% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | narrow/g1.0/H75 | -187 (live -328; $4.84 -188) DD -4.0% ww +0 stops 0.53(0.46) | +258 (live +452; $4.84 +258) DD +57.7% ww +480 stops 0.30(0.38) | +35 (live +62; $4.84 +35) DD +24.1% ww +480 stops 0.42(0.42) |
| H7 nyam | both/g0.5/H75 | +103 (live +180; $4.84 +103) DD +29.2% ww -83 stops 0.46(0.46) | +87 (live +153; $4.84 +87) DD +2.2% ww +195 stops 0.38(0.38) | +95 (live +167; $4.84 +95) DD +2.2% ww +195 stops 0.42(0.42) |
| H7 nyam | narrow/g0.5/H75 | n/a | +77 (live +134; $4.84 +77) DD +2.2% ww +195 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g0.5/H75 | n/a | +11 (live +19; $4.84 +11) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H75 | n/a | +22 (live +39; $4.84 +22) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H50 | n/a | +30 (live +53; $4.84 +30) DD +0.0% ww +0 stops 0.30(0.38) | n/a |
| K7 asia | wide/g1.0/H75 | n/a | +297 (live +520; $4.84 +298) DD +0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | wide/g0.5/H75 | n/a | -54 (live -94; $4.84 -54) DD -0.7% ww -404 stops 0.00(0.00) | n/a |
| K7 asia | narrow/g0.5/H75 | n/a | +1877 (live +3285; $4.84 +1855) DD -19.6% ww -2412 stops 0.00(0.00) | n/a |
| K7 asia | both/g0.5/H75 | n/a | +1823 (live +3191; $4.84 +1801) DD -28.8% ww -3232 stops 0.00(0.00) | n/a |
| K7 asia | wide/g1.0/H50 | n/a | -401 (live -702; $4.84 -400) DD -35.9% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | both/g1.0/H75 | n/a | +1292 (live +2261; $4.84 +1220) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H75 | n/a | +912 (live +1595; $4.84 +838) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H50 | n/a | +355 (live +621; $4.84 +268) DD -86.2% ww -5644 stops 0.00(0.00) | n/a |
| K7 london | both/g0.5/H75 | n/a | -9 (live -15; $4.84 -14) DD +8.7% ww +4326 stops 0.23(0.30) | n/a |
| K7 london | wide/g0.5/H75 | n/a | +27 (live +48; $4.84 +29) DD +0.5% ww +0 stops 0.30(0.30) | n/a |
| K7 london | wide/g1.0/H50 | n/a | +431 (live +755; $4.84 +433) DD -3.3% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g0.5/H75 | n/a | -123 (live -215; $4.84 -130) DD -4.2% ww +4733 stops 0.23(0.30) | n/a |
| K7 london | wide/g1.0/H75 | n/a | +157 (live +274; $4.84 +160) DD -4.8% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g1.0/H50 | n/a | -182 (live -319; $4.84 -204) DD -13.7% ww +3097 stops 0.23(0.30) | n/a |
| K7 london | both/g1.0/H75 | n/a | +481 (live +841; $4.84 +462) DD -25.5% ww +4257 stops 0.38(0.30) | n/a |
| K7 london | narrow/g1.0/H75 | n/a | -31 (live -55; $4.84 -55) DD -42.3% ww +4122 stops 0.38(0.30) | n/a |
| K7 nyam | narrow/g1.0/H50 | n/a | +769 (live +1345; $4.84 +761) DD +51.0% ww +2185 stops 0.00(0.00) | n/a |
| K7 nyam | both/g1.0/H75 | n/a | +1160 (live +2030; $4.84 +1153) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g1.0/H75 | n/a | +984 (live +1722; $4.84 +977) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g0.5/H75 | n/a | +668 (live +1170; $4.84 +667) DD +40.3% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | both/g0.5/H75 | n/a | +806 (live +1410; $4.84 +805) DD +39.5% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H75 | n/a | +176 (live +308; $4.84 +176) DD -0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H50 | n/a | +252 (live +441; $4.84 +253) DD -0.3% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g0.5/H75 | n/a | +137 (live +241; $4.84 +137) DD -0.8% ww +0 stops 0.00(0.00) | n/a |
| K7 nypm | wide/g1.0/H50 | n/a | +442 (live +773; $4.84 +442) DD +17.3% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | wide/g1.0/H75 | n/a | +70 (live +122; $4.84 +70) DD +13.1% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | both/g1.0/H75 | n/a | -184 (live -322; $4.84 -197) DD +9.8% ww +1145 stops 0.15(0.08) | n/a |
| K7 nypm | wide/g0.5/H75 | n/a | -4 (live -8; $4.84 -4) DD -1.5% ww -38 stops 0.00(0.08) | n/a |
| K7 nypm | narrow/g1.0/H50 | n/a | +48 (live +84; $4.84 +32) DD -1.9% ww +105 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g1.0/H75 | n/a | -254 (live -445; $4.84 -267) DD -3.3% ww +990 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g0.5/H75 | n/a | -266 (live -465; $4.84 -269) DD -26.7% ww +140 stops 0.08(0.08) | n/a |
| K7 nypm | both/g0.5/H75 | n/a | -270 (live -473; $4.84 -274) DD -27.3% ww +102 stops 0.00(0.08) | n/a |
| M7 london | wide/g1.0/H75 | n/a | +1614 (live +2824; $4.84 +1616) DD +4.9% ww +1190 stops 0.53(0.91) | n/a |
| M7 london | wide/g0.5/H75 | n/a | +688 (live +1204; $4.84 +689) DD +4.4% ww +1400 stops 0.84(0.91) | n/a |
| M7 london | wide/g1.0/H50 | n/a | +538 (live +942; $4.84 +540) DD -1.3% ww -80 stops 0.84(0.91) | n/a |
| M7 london | both/g0.5/H75 | n/a | +1147 (live +2008; $4.84 +1139) DD -8.1% ww +130 stops 1.07(0.91) | n/a |
| M7 london | narrow/g0.5/H75 | n/a | +417 (live +730; $4.84 +408) DD -10.9% ww -1075 stops 1.14(0.91) | n/a |
| M7 london | narrow/g1.0/H50 | n/a | +476 (live +833; $4.84 +446) DD -19.9% ww +1144 stops 1.45(0.91) | n/a |
| M7 london | narrow/g1.0/H75 | n/a | -366 (live -640; $4.84 -390) DD -20.4% ww +80 stops 1.29(0.91) | n/a |
| M7 london | both/g1.0/H75 | n/a | +1142 (live +1999; $4.84 +1121) DD -23.2% ww -729 stops 0.91(0.91) | n/a |
| M7 nyam | narrow/g1.0/H50 | n/a | +439 (live +769; $4.84 +424) DD +26.0% ww -222 stops 0.38(0.23) | n/a |
| M7 nyam | both/g0.5/H75 | n/a | +79 (live +138; $4.84 +75) DD +0.8% ww +194 stops 0.30(0.23) | n/a |
| M7 nyam | narrow/g0.5/H75 | n/a | +73 (live +127; $4.84 +69) DD +0.8% ww +194 stops 0.38(0.23) | n/a |
| M7 nyam | wide/g0.5/H75 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H75 | n/a | +16 (live +28; $4.84 +16) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H50 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | both/g1.0/H75 | n/a | +419 (live +733; $4.84 +405) DD -6.8% ww -991 stops 0.46(0.23) | n/a |
| M7 nyam | narrow/g1.0/H75 | n/a | +402 (live +704; $4.84 +388) DD -6.8% ww -991 stops 0.53(0.23) | n/a |
| P7 asia | narrow/g1.0/H50 | n/a | -3918 (live -6857; $4.84 -4186) DD -0.4% ww -4286 stops 0.46(0.15) | n/a |
| P7 asia | both/g0.5/H75 | n/a | -5946 (live -10406; $4.84 -6044) DD -1.0% ww +6944 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g0.5/H75 | n/a | -5762 (live -10084; $4.84 -5860) DD -1.0% ww +9022 stops 0.15(0.15) | n/a |
| P7 asia | wide/g0.5/H75 | n/a | -184 (live -322; $4.84 -183) DD -4.9% ww -2079 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g1.0/H75 | n/a | -2696 (live -4718; $4.84 -2882) DD -7.8% ww -10346 stops 0.53(0.15) | n/a |
| P7 asia | wide/g1.0/H50 | n/a | -816 (live -1428; $4.84 -812) DD -22.6% ww -9033 stops 0.15(0.15) | n/a |
| P7 asia | wide/g1.0/H75 | n/a | -491 (live -858; $4.84 -490) DD -25.2% ww -10331 stops 0.15(0.15) | n/a |
| P7 asia | both/g1.0/H75 | n/a | -3315 (live -5802; $4.84 -3501) DD -36.1% ww -13164 stops 0.53(0.15) | n/a |
| P7 london | both/g0.5/H75 | n/a | +894 (live +1565; $4.84 +886) DD +29.6% ww -1633 stops 0.08(0.08) | n/a |
| P7 london | narrow/g0.5/H75 | n/a | +386 (live +675; $4.84 +375) DD +28.5% ww -1328 stops 0.08(0.08) | n/a |
| P7 london | narrow/g1.0/H50 | n/a | +927 (live +1622; $4.84 +895) DD +19.7% ww -3009 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H75 | n/a | -142 (live -249; $4.84 -138) DD +2.7% ww -458 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H50 | n/a | +265 (live +464; $4.84 +266) DD +1.1% ww +0 stops 0.08(0.08) | n/a |
| P7 london | wide/g0.5/H75 | n/a | +385 (live +674; $4.84 +387) DD -1.9% ww -238 stops 0.08(0.08) | n/a |
| P7 london | both/g1.0/H75 | n/a | +1179 (live +2064; $4.84 +1145) DD -9.8% ww -5408 stops 0.15(0.08) | n/a |
| P7 london | narrow/g1.0/H75 | n/a | +1322 (live +2313; $4.84 +1282) DD -14.4% ww -5203 stops 0.15(0.08) | n/a |
| P7 nyam | both/g1.0/H75 | n/a | +697 (live +1220; $4.84 +685) DD +51.3% ww +354 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g1.0/H75 | n/a | +543 (live +951; $4.84 +529) DD +45.9% ww +324 stops 0.30(0.38) | n/a |
| P7 nyam | both/g0.5/H75 | n/a | +105 (live +184; $4.84 +99) DD +36.7% ww +238 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g0.5/H75 | n/a | -13 (live -23; $4.84 -20) DD +36.4% ww +262 stops 0.30(0.38) | n/a |
| P7 nyam | wide/g0.5/H75 | n/a | +118 (live +207; $4.84 +119) DD +0.3% ww -25 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H75 | n/a | +16 (live +27; $4.84 +17) DD -7.5% ww -105 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H50 | n/a | -544 (live -952; $4.84 -543) DD -47.7% ww -3348 stops 0.38(0.38) | n/a |
| U7 asia | narrow/g1.0/H50 | n/a | +1222 (live +2139; $4.84 +1201) DD +15.6% ww -265 stops 1.90(1.83) | n/a |
| U7 asia | both/g1.0/H75 | n/a | +71 (live +124; $4.84 +56) DD +8.3% ww -1836 stops 1.98(1.83) | n/a |
| U7 asia | narrow/g1.0/H75 | n/a | +502 (live +879; $4.84 +487) DD +8.3% ww +983 stops 1.98(1.83) | n/a |
| U7 asia | both/g0.5/H75 | n/a | -800 (live -1399; $4.84 -808) DD +6.6% ww -2883 stops 2.05(1.83) | n/a |
| U7 asia | narrow/g0.5/H75 | n/a | -162 (live -284; $4.84 -170) DD +6.6% ww +57 stops 2.05(1.83) | n/a |
| U7 asia | wide/g0.5/H75 | n/a | -637 (live -1115; $4.84 -637) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H75 | n/a | -431 (live -755; $4.84 -431) DD +0.0% ww -1836 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H50 | n/a | -648 (live -1134; $4.84 -648) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 london | narrow/g0.5/H75 | n/a | +393 (live +687; $4.84 +392) DD +17.2% ww +1796 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H75 | n/a | +246 (live +431; $4.84 +243) DD +3.1% ww -1185 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H50 | n/a | -41 (live -72; $4.84 -48) DD -9.9% ww -1991 stops 1.52(1.45) | n/a |
| U7 london | both/g0.5/H75 | n/a | -891 (live -1560; $4.84 -890) DD -25.4% ww -3538 stops 1.52(1.45) | n/a |
| U7 london | wide/g1.0/H50 | n/a | -839 (live -1468; $4.84 -837) DD -33.9% ww -4122 stops 1.37(1.45) | n/a |
| U7 london | wide/g0.5/H75 | n/a | -1284 (live -2247; $4.84 -1282) DD -44.3% ww -6280 stops 1.52(1.45) | n/a |
| U7 london | both/g1.0/H75 | n/a | -1728 (live -3025; $4.84 -1729) DD -105.5% ww -7540 stops 1.60(1.45) | n/a |
| U7 london | wide/g1.0/H75 | n/a | -1975 (live -3455; $4.84 -1972) DD -109.8% ww -6355 stops 1.60(1.45) | n/a |

### Summary per slice: pick made on May-Jul, result on L3M
| slice | pick | L3M result of the pick | verdict |
|---|---|---|---|
| A7 asia | pending | | |
| H7 asia | pending | | |
| H7 nyam | pending | | |
| K7 asia | pending | | |
| K7 london | pending | | |
| K7 nyam | pending | | |
| K7 nypm | pending | | |
| M7 london | pending | | |
| M7 nyam | pending | | |
| P7 asia | pending | | |
| P7 london | pending | | |
| P7 nyam | pending | | |
| U7 asia | pending | | |
| U7 london | pending | | |

### B2: why the global version adds full stops (narrow-only/both g1.0 H75 cell, L3M, trade tables)
Reference JN05W2 L3M (no O7): 1855 trades, stop rate 0.071, 132 stops (13 weeks).

**M1_75_g10_c1_d10_c20_tb_B**: 2038 trades (+183 vs JN05W2), stops 173 (+41), stop rate 0.085 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 437 | 0.103 | 3.05 | 94 |
| (40, 50] | 721 | 0.074 | 2.36 | 271 |
| (50, 55] | 232 | 0.099 | 1.97 | 169 |
| (55, 60] | 435 | 0.076 | 1.87 | 76 |
| (60, 70] | 75 | 0.120 | 2.01 | -385 |
| (70, 80] | 62 | 0.048 | 1.68 | -284 |
| (80, 101] | 76 | 0.092 | 1.13 | -591 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1543 | 0.069 | 2.21 | 54 |
| (3.0, 4.0] | 294 | 0.116 | 2.29 | 239 |
| (4.0, 5.0] | 74 | 0.108 | 2.31 | 364 |
| (5.0, 6.0] | 6 | 0.167 | 2.50 | 172 |
| (6.0, 8.0] | 4 | 0.000 | 1.00 | -119 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1068 | 0.096 | 1.00 | 4 |
| (1, 2] | 385 | 0.078 | 2.00 | 115 |
| (2, 3] | 215 | 0.093 | 3.00 | 23 |
| (3, 5] | 195 | 0.062 | 4.46 | 256 |
| (5, 8] | 138 | 0.065 | 6.70 | 690 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

**M1_75_g10_c1_d10_c20_tb_N**: 2072 trades (+217 vs JN05W2), stops 178 (+46), stop rate 0.086 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 449 | 0.105 | 3.02 | 97 |
| (40, 50] | 725 | 0.073 | 2.35 | 272 |
| (50, 55] | 236 | 0.102 | 1.97 | 150 |
| (55, 60] | 662 | 0.082 | 1.82 | -29 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1644 | 0.072 | 2.18 | 50 |
| (3.0, 4.0] | 264 | 0.121 | 2.38 | 348 |
| (4.0, 5.0] | 44 | 0.091 | 3.11 | 1063 |
| (5.0, 6.0] | 3 | 0.000 | 3.33 | 68 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1073 | 0.095 | 1.00 | 8 |
| (1, 2] | 413 | 0.085 | 2.00 | 117 |
| (2, 3] | 197 | 0.081 | 3.00 | 213 |
| (3, 5] | 217 | 0.074 | 4.43 | 196 |
| (5, 8] | 135 | 0.067 | 6.74 | 714 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

Reading of the W/ATR5 table: ATR5 = mean range of the last 14 five-minute buckets in points; a bracket 3x ATR5 or less is within ordinary 5-minute noise. The noise-floor cells (floor 3/4/5 x ATR5, narrowing only) are listed in B3.


### B3: levers (stop-only / target-only / both / size-only) and noise floor, per slice
| slice | cell | L3M | May-Jul |
|---|---|---|---|

### B4: assembled stack (each slice at its own walk-forward pick, run together)
(not run yet: starts when every slice has a pick)


## Target capped at the forecast
**VERDICT (plain, not a PASS; FIRST PASS; 15 of 26 global exact cap cells scored in L3M, per book x session exact cells still running): planted-edge check PASSED through the exact engine (look-ahead oracle target 0.9 x realised MFE: +85531 $/wk, DD +67.0%, ww +64263; this is a mechanism check, NOT a result); the reachable move is only weakly forecastable (R2 on ln MFE 0.03-0.14, quantile calibration good); in the exact L3M cells the cap at the forecast 50th-percentile move (horizon = 75th-percentile holding time) gives +1486 $/wk, DD -0.5%, ww -240 and the 75th-percentile cap +177 $/wk, DD +0.0%, ww +0, the remaining-range caps cut drawdown (own k1.0 -6226 $/wk, DD +27.0%, ww +12290; HAR k1.0 -7259 $/wk, DD +39.4%, ww +17319) but cost thousands per week. Best exact L3M cap cell inside the mean gate by DD: PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time (DD +7.9%, -120 $/wk). L6M/HOLD/older still to run before any verdict.**

Planted-edge check (H1) for the capping mechanism: cells `tcoracle0.9` / `0.6` set the target to 0.9 / 0.6 x the REALISED maximum favourable move (look-ahead, only to prove the mechanism can show an edge through the exact engine); they must come out strongly positive. Status below in the exact table. Until they do, an exact cap verdict is not stated.

Definition. Reachable move = maximum favourable excursion from the signal-second bar close over the book-session holding horizon H (H50/H75 = median / 75th percentile holding time of that book+session, causal), points. Model: walk-forward ridge (14-day blocks, expanding, min 90 days, per session) on ln((MFE+2)/price) from the Dial 10 own-bar inputs (last 15/30/60/120 min range and vol, same-clock normal, own session level, range used so far, elapsed fraction) plus the side-aware room in the session range so far; quantiles q = fitted + empirical training-residual quantile (50/60/75/90). Cap: target = min(book target 60 pts [58 after fills], q-quantile), stop, lots and every other level unchanged. Remaining-range cap: target = min(book target, k x (session range forecast - range printed so far)), forecast = own (price x exp(sf20), mean of the last 20 sessions) or T-RANGE2 HAR (fc_r2_har, available-epoch checked). Small caps (< 30 pts = 0.5 x stop): take / skip / half. EV target: argmax over T in [20, book target or 300] of T x P(MFE>=T) - stop x (1-P) with the lognormal forecast (ignores the stop-first ordering, so optimistic). Extension: if the forecast median MFE is >= m x book target, target = min(q50, 2 x book target). Lots/base basis: dollars are BASE lots (live x1.75 = multiply by 1.75); fee columns $4.84 beside raw $1.18 where shown.

### Item 1: calibration of the forecast quantiles (share of trades whose realized MFE exceeded the forecast quantile; a q-quantile should be exceeded 1-q of the time = 0.50 / 0.40 / 0.25 / 0.10) and R2 of ln MFE, per session
| H | session | window | n | >q50 | >q60 | >q75 | >q90 | R2 ln MFE | median q75 (pts) | share q75 < 60 |
|---|---|---|---|---|---|---|---|---|---|---|
| 50 | asia | older (<2026-05) | 5119 | 0.51 | 0.41 | 0.26 | 0.12 | 0.121 | 80 | 0.222 |
| 50 | asia | L6M | 2006 | 0.49 | 0.38 | 0.23 | 0.08 | 0.058 | 111 | 0.047 |
| 50 | asia | L3M | 875 | 0.46 | 0.34 | 0.20 | 0.07 | -0.014 | 90 | 0.098 |
| 50 | london | older (<2026-05) | 4892 | 0.51 | 0.41 | 0.26 | 0.11 | 0.142 | 62 | 0.438 |
| 50 | london | L6M | 1406 | 0.48 | 0.37 | 0.23 | 0.08 | 0.028 | 76 | 0.166 |
| 50 | london | L3M | 673 | 0.48 | 0.37 | 0.24 | 0.07 | -0.008 | 68 | 0.247 |
| 50 | nyam | older (<2026-05) | 4142 | 0.47 | 0.38 | 0.24 | 0.11 | 0.077 | 63 | 0.397 |
| 50 | nyam | L6M | 600 | 0.51 | 0.40 | 0.24 | 0.09 | 0.097 | 83 | 0.157 |
| 50 | nyam | L3M | 271 | 0.51 | 0.38 | 0.20 | 0.06 | 0.077 | 68 | 0.258 |
| 50 | nypm | older (<2026-05) | 817 | 0.48 | 0.40 | 0.26 | 0.13 | 0.073 | 62 | 0.419 |
| 50 | nypm | L6M | 150 | 0.59 | 0.50 | 0.33 | 0.13 | 0.221 | 71 | 0.307 |
| 50 | nypm | L3M | 56 | 0.50 | 0.36 | 0.21 | 0.09 | 0.104 | 54 | 0.589 |
| 50 | all | older (<2026-05) | 14970 | 0.50 | 0.40 | 0.26 | 0.12 | 0.123 | 68 | 0.352 |
| 50 | all | L6M | 4162 | 0.49 | 0.38 | 0.23 | 0.08 | 0.080 | 91 | 0.113 |
| 50 | all | L3M | 1875 | 0.47 | 0.36 | 0.21 | 0.07 | 0.014 | 76 | 0.189 |
| 75 | asia | older (<2026-05) | 5119 | 0.52 | 0.41 | 0.26 | 0.12 | 0.134 | 122 | 0.032 |
| 75 | asia | L6M | 2006 | 0.50 | 0.40 | 0.24 | 0.08 | 0.027 | 178 | 0.000 |
| 75 | asia | L3M | 875 | 0.45 | 0.35 | 0.20 | 0.05 | -0.016 | 156 | 0.000 |
| 75 | london | older (<2026-05) | 4891 | 0.51 | 0.42 | 0.27 | 0.11 | 0.157 | 101 | 0.100 |
| 75 | london | L6M | 1406 | 0.49 | 0.37 | 0.21 | 0.08 | 0.069 | 118 | 0.001 |
| 75 | london | L3M | 673 | 0.49 | 0.38 | 0.21 | 0.09 | 0.025 | 108 | 0.000 |
| 75 | nyam | older (<2026-05) | 4142 | 0.48 | 0.38 | 0.23 | 0.10 | 0.065 | 91 | 0.081 |
| 75 | nyam | L6M | 600 | 0.50 | 0.40 | 0.24 | 0.10 | 0.098 | 125 | 0.015 |
| 75 | nyam | L3M | 271 | 0.44 | 0.34 | 0.19 | 0.05 | 0.051 | 103 | 0.015 |
| 75 | nypm | older (<2026-05) | 812 | 0.49 | 0.37 | 0.26 | 0.11 | 0.043 | 87 | 0.095 |
| 75 | nypm | L6M | 150 | 0.53 | 0.46 | 0.34 | 0.17 | 0.179 | 117 | 0.013 |
| 75 | nypm | L3M | 56 | 0.41 | 0.30 | 0.21 | 0.07 | -0.076 | 93 | 0.036 |
| 75 | all | older (<2026-05) | 14964 | 0.51 | 0.40 | 0.25 | 0.11 | 0.131 | 102 | 0.071 |
| 75 | all | L6M | 4162 | 0.50 | 0.39 | 0.23 | 0.09 | 0.079 | 149 | 0.003 |
| 75 | all | L3M | 1875 | 0.46 | 0.36 | 0.20 | 0.06 | 0.032 | 128 | 0.003 |

### Items 3 and 4 (and 2): offline replay of the caps on the JN05W2 trade paths, all 43 months (estimate: 1-min paths, cap counted only before the exit bar, so cut/stop ordering is conservative; the exact cells below decide). d mean $/wk and DD cut % vs JN05W2 on the same trades, scope all, then per session for the cap with the most trades capped
| cap | small-cap rule | scope | window | d mean $/wk (live x1.75) | DD cut % | d worst week | d stops/wk | share capped | share where cap hit |
|---|---|---|---|---|---|---|---|---|---|
| q50_H50 | take | all | L3M | +409 (+715) | -3.9 | -1411 | +0.00 | 0.82 | 0.45 |
| q50_H50 | take | all | L6M | -96 (-169) | -3.9 | -1411 | +0.00 | 0.62 | 0.33 |
| q50_H50 | take | all | OLDER | -1795 (-3141) | +12.0 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | skip | all | L3M | -1581 (-2767) | -5.0 | -1996 | +0.00 | 0.82 | 0.45 |
| q50_H50 | skip | all | L6M | -1445 (-2528) | -5.0 | -1996 | +0.00 | 0.62 | 0.33 |
| q50_H50 | skip | all | OLDER | -2271 (-3975) | +17.4 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | half | all | L3M | -586 (-1026) | -4.4 | -1704 | +0.00 | 0.82 | 0.45 |
| q50_H50 | half | all | L6M | -771 (-1348) | -4.4 | -1704 | +0.00 | 0.62 | 0.33 |
| q50_H50 | half | all | OLDER | -2033 (-3558) | +16.5 | +13127 | +0.00 | 0.80 | 0.45 |
| q60_H50 | take | all | L3M | -1525 (-2668) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | take | all | L6M | -839 (-1469) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | take | all | OLDER | -1296 (-2267) | +12.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | skip | all | L3M | -3272 (-5726) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | skip | all | L6M | -1811 (-3170) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | skip | all | OLDER | -1648 (-2885) | +8.8 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | half | all | L3M | -2398 (-4197) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | half | all | L6M | -1325 (-2319) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | half | all | OLDER | -1472 (-2576) | +10.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q75_H50 | take | all | L3M | +414 (+725) | -0.4 | -214 | +0.00 | 0.21 | 0.11 |
| q75_H50 | take | all | L6M | -44 (-77) | -0.4 | -214 | +0.00 | 0.13 | 0.06 |
| q75_H50 | take | all | OLDER | -719 (-1258) | -1.1 | +13801 | +0.00 | 0.37 | 0.18 |
| q90_H50 | take | all | L3M | +191 (+334) | +0.0 | +0 | +0.00 | 0.02 | 0.01 |
| q90_H50 | take | all | L6M | +142 (+249) | +0.0 | +0 | +0.00 | 0.01 | 0.01 |
| q90_H50 | take | all | OLDER | -169 (-296) | -1.8 | +1686 | +0.00 | 0.08 | 0.03 |
| q50_H75 | take | all | L3M | +128 (+225) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | take | all | L6M | +624 (+1092) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | take | all | OLDER | -931 (-1628) | -13.1 | +11346 | +0.00 | 0.51 | 0.26 |
| q50_H75 | skip | all | L3M | +178 (+312) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | skip | all | L6M | +685 (+1198) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | skip | all | OLDER | -1302 (-2279) | -4.6 | +14384 | +0.00 | 0.51 | 0.26 |
| q50_H75 | half | all | L3M | +153 (+268) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | half | all | L6M | +654 (+1145) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | half | all | OLDER | -1116 (-1954) | -8.8 | +12865 | +0.00 | 0.51 | 0.26 |
| q60_H75 | take | all | L3M | +830 (+1452) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | take | all | L6M | +379 (+664) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | take | all | OLDER | -478 (-836) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | skip | all | L3M | +958 (+1677) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | skip | all | L6M | +421 (+737) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | skip | all | OLDER | -402 (-703) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | half | all | L3M | +894 (+1564) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | half | all | L6M | +400 (+700) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | half | all | OLDER | -440 (-769) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q75_H75 | take | all | L3M | +236 (+413) | +0.0 | +0 | +0.00 | 0.01 | 0.00 |
| q75_H75 | take | all | L6M | +105 (+185) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q75_H75 | take | all | OLDER | -255 (-446) | -1.9 | +1485 | +0.00 | 0.08 | 0.04 |
| q90_H75 | take | all | L3M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | L6M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | OLDER | +10 (+18) | -0.4 | +0 | +0.00 | 0.01 | 0.00 |
| rem_own_k0.5 | take | all | L3M | -6674 (-11680) | +8.8 | -1861 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | take | all | L6M | -13204 (-23108) | +8.7 | -1861 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | take | all | OLDER | -7381 (-12916) | -40.2 | +20529 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | skip | all | L3M | -5271 (-9225) | +21.7 | +2982 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | skip | all | L6M | -10625 (-18594) | +21.7 | +2982 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | skip | all | OLDER | -6272 (-10977) | +17.3 | +21712 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | half | all | L3M | -5973 (-10452) | +16.3 | +560 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | half | all | L6M | -11915 (-20851) | +16.3 | +560 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | half | all | OLDER | -6827 (-11946) | +0.6 | +23150 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.75 | take | all | L3M | -7140 (-12494) | +9.6 | +3294 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | take | all | L6M | -10636 (-18614) | +9.6 | +3294 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | take | all | OLDER | -5846 (-10230) | -24.0 | +12208 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | skip | all | L3M | -3661 (-6406) | +10.3 | +4045 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | skip | all | L6M | -6650 (-11638) | +10.3 | +4045 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | skip | all | OLDER | -3856 (-6749) | +16.1 | +19073 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | half | all | L3M | -5400 (-9450) | +13.0 | +3670 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | half | all | L6M | -8643 (-15126) | +13.0 | +3670 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | half | all | OLDER | -4851 (-8489) | +13.0 | +20157 | +0.00 | 0.73 | 0.53 |
| rem_own_k1.0 | take | all | L3M | -5516 (-9653) | +18.3 | +9104 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | take | all | L6M | -8765 (-15339) | +18.3 | +9104 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | take | all | OLDER | -5714 (-9999) | -58.2 | +11926 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | skip | all | L3M | -3265 (-5714) | +15.0 | +8858 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | skip | all | L6M | -5683 (-9944) | +15.0 | +8858 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | skip | all | OLDER | -3872 (-6775) | -61.0 | +20250 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | half | all | L3M | -4391 (-7683) | +18.5 | +8981 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | half | all | L6M | -7224 (-12642) | +18.5 | +8981 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | half | all | OLDER | -4793 (-8387) | -58.0 | +21393 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.25 | take | all | L3M | -3112 (-5446) | +24.4 | +13750 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | take | all | L6M | -8275 (-14481) | +24.4 | +13750 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | take | all | OLDER | -5400 (-9450) | -15.5 | +4336 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | skip | all | L3M | -456 (-797) | +22.4 | +13720 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | skip | all | L6M | -4232 (-7405) | +22.4 | +13720 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | skip | all | OLDER | -3310 (-5792) | -36.4 | +22803 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | half | all | L3M | -1784 (-3121) | +25.2 | +15286 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | half | all | L6M | -6253 (-10943) | +25.2 | +15286 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | half | all | OLDER | -4355 (-7621) | -18.3 | +15544 | +0.00 | 0.54 | 0.41 |

Per session, q60 H75 take-anyway and remaining-range k=1.25 (own):
| cap | session | window | d mean $/wk | DD cut % | d worst week | share capped |
|---|---|---|---|---|---|---|
| q60_H75 | asia | L3M | +221 | +0.0 | +0 | 0.02 |
| q60_H75 | asia | L6M | +110 | +0.0 | +0 | 0.01 |
| q60_H75 | asia | OLDER | -124 | -0.0 | +0 | 0.23 |
| q60_H75 | london | L3M | +745 | +3.8 | +0 | 0.16 |
| q60_H75 | london | L6M | +330 | +3.8 | +0 | 0.12 |
| q60_H75 | london | OLDER | -294 | -2.1 | +0 | 0.35 |
| q60_H75 | nyam | L3M | +61 | -7.2 | +0 | 0.15 |
| q60_H75 | nyam | L6M | -14 | +0.0 | +0 | 0.10 |
| q60_H75 | nyam | OLDER | -37 | -6.0 | +1403 | 0.37 |
| q60_H75 | nypm | L3M | -197 | -0.0 | +0 | 0.41 |
| q60_H75 | nypm | L6M | -47 | +0.0 | +0 | 0.20 |
| q60_H75 | nypm | OLDER | -22 | -5.4 | +0 | 0.33 |
| rem_own_k1.25 | asia | L3M | -4547 | +35.2 | +434 | 0.37 |
| rem_own_k1.25 | asia | L6M | -6717 | +27.1 | +434 | 0.38 |
| rem_own_k1.25 | asia | OLDER | -4532 | -27.4 | +10774 | 0.62 |
| rem_own_k1.25 | london | L3M | +2278 | +46.3 | +12347 | 0.24 |
| rem_own_k1.25 | london | L6M | +1196 | +46.3 | +12347 | 0.30 |
| rem_own_k1.25 | london | OLDER | -510 | +12.9 | +3024 | 0.51 |
| rem_own_k1.25 | nyam | L3M | -650 | +20.0 | +0 | 0.24 |
| rem_own_k1.25 | nyam | L6M | -2127 | -8.9 | +1531 | 0.39 |
| rem_own_k1.25 | nyam | OLDER | -53 | +10.3 | +7327 | 0.47 |
| rem_own_k1.25 | nypm | L3M | -192 | +21.8 | +1203 | 0.45 |
| rem_own_k1.25 | nypm | L6M | -627 | +21.8 | +1203 | 0.50 |
| rem_own_k1.25 | nypm | OLDER | -304 | -2.4 | -831 | 0.50 |

### Item 4 per book x session (all 43 months): trades whose 60-pt target lies beyond the forecast quantile, their fixed-target result, the capped replay, and how far trades run past the cap
| book | session | cap | trades | share beyond | fixed-target hit rate | fixed avg $/trade | capped avg $/trade | avg points run past cap |
|---|---|---|---|---|---|---|---|---|
| A7 | asia | q50_H75 | 1156 | 0.25 | 0.50 | 60 | 87 | 10.4 |
| A7 | asia | q60_H75 | 1156 | 0.13 | 0.47 | 4 | 26 | 8.8 |
| A7 | asia | q75_H75 | 1156 | 0.03 | 0.48 | 19 | 6 | 11.1 |
| A7 | asia | rem_own_k0.75 | 1156 | 0.74 | 0.52 | 126 | 22 | 32.9 |
| H7 | asia | q50_H75 | 700 | 0.33 | 0.49 | 164 | 181 | 11.3 |
| H7 | asia | q60_H75 | 700 | 0.18 | 0.56 | 447 | 414 | 10.7 |
| H7 | asia | q75_H75 | 700 | 0.02 | 0.50 | -318 | -267 | 16.1 |
| H7 | asia | rem_own_k0.75 | 700 | 0.71 | 0.48 | 208 | 55 | 27.8 |
| H7 | nyam | q50_H75 | 348 | 0.49 | 0.46 | 84 | 25 | 8.9 |
| H7 | nyam | q60_H75 | 348 | 0.25 | 0.47 | 96 | 46 | 7.4 |
| H7 | nyam | q75_H75 | 348 | 0.06 | 0.33 | -113 | -12 | 4.7 |
| H7 | nyam | rem_own_k0.75 | 348 | 0.66 | 0.47 | 62 | -35 | 23.3 |
| K7 | asia | q50_H75 | 2596 | 0.32 | 0.44 | 102 | 74 | 9.7 |
| K7 | asia | q60_H75 | 2596 | 0.19 | 0.44 | 111 | 90 | 7.6 |
| K7 | asia | q75_H75 | 2596 | 0.04 | 0.40 | 26 | 1 | 6.1 |
| K7 | asia | rem_own_k0.75 | 2596 | 0.68 | 0.44 | 88 | 0 | 27.2 |
| K7 | london | q50_H75 | 1781 | 0.57 | 0.43 | 62 | 37 | 10.9 |
| K7 | london | q60_H75 | 1781 | 0.33 | 0.44 | 60 | 35 | 9.4 |
| K7 | london | q75_H75 | 1781 | 0.12 | 0.48 | 138 | 101 | 6.5 |
| K7 | london | rem_own_k0.75 | 1781 | 0.69 | 0.43 | 45 | -12 | 27.4 |
| K7 | nyam | q50_H75 | 1565 | 0.57 | 0.42 | 21 | 18 | 10.0 |
| K7 | nyam | q60_H75 | 1565 | 0.32 | 0.40 | -4 | -17 | 9.0 |
| K7 | nyam | q75_H75 | 1565 | 0.07 | 0.41 | 40 | 36 | 16.3 |
| K7 | nyam | rem_own_k0.75 | 1565 | 0.70 | 0.39 | -21 | -38 | 26.0 |
| K7 | nypm | q50_H75 | 1136 | 0.50 | 0.36 | 65 | 54 | 8.1 |
| K7 | nypm | q60_H75 | 1136 | 0.31 | 0.34 | 62 | 48 | 5.6 |
| K7 | nypm | q75_H75 | 1136 | 0.09 | 0.29 | 155 | 179 | 3.5 |
| K7 | nypm | rem_own_k0.75 | 1136 | 0.71 | 0.37 | 72 | -30 | 23.7 |
| M7 | london | q50_H75 | 2489 | 0.42 | 0.43 | 45 | 40 | 10.0 |
| M7 | london | q60_H75 | 2489 | 0.24 | 0.43 | 32 | 26 | 8.2 |
| M7 | london | q75_H75 | 2489 | 0.06 | 0.38 | -74 | -97 | 7.1 |
| M7 | london | rem_own_k0.75 | 2489 | 0.59 | 0.39 | -40 | -29 | 22.9 |
| M7 | nyam | q50_H75 | 1496 | 0.52 | 0.43 | 49 | 22 | 8.6 |
| M7 | nyam | q60_H75 | 1496 | 0.27 | 0.44 | 76 | 57 | 7.2 |
| M7 | nyam | q75_H75 | 1496 | 0.06 | 0.44 | 127 | 131 | 4.9 |
| M7 | nyam | rem_own_k0.75 | 1496 | 0.69 | 0.42 | 30 | -36 | 27.3 |
| O7 | nyam | q50_H75 | 452 | 0.58 | 0.32 | 205 | 91 | 20.5 |
| O7 | nyam | q60_H75 | 452 | 0.37 | 0.31 | 156 | 118 | 16.9 |
| O7 | nyam | q75_H75 | 452 | 0.08 | 0.20 | -192 | -145 | 9.5 |
| O7 | nyam | rem_own_k0.75 | 452 | 0.31 | 0.30 | 120 | 82 | 20.6 |
| P7 | asia | q50_H75 | 2161 | 0.29 | 0.46 | 391 | 341 | 10.2 |
| P7 | asia | q60_H75 | 2161 | 0.16 | 0.48 | 487 | 484 | 9.3 |
| P7 | asia | q75_H75 | 2161 | 0.02 | 0.55 | 1227 | 969 | 5.7 |
| P7 | asia | rem_own_k0.75 | 2161 | 0.70 | 0.44 | 447 | 130 | 26.6 |
| P7 | london | q50_H75 | 1537 | 0.62 | 0.38 | 74 | 27 | 10.0 |
| P7 | london | q60_H75 | 1537 | 0.41 | 0.38 | 67 | 36 | 7.8 |
| P7 | london | q75_H75 | 1537 | 0.15 | 0.41 | 124 | 59 | 5.3 |
| P7 | london | rem_own_k0.75 | 1537 | 0.72 | 0.37 | -19 | -13 | 23.8 |
| P7 | nyam | q50_H75 | 1050 | 0.72 | 0.38 | 38 | 150 | 13.2 |
| P7 | nyam | q60_H75 | 1050 | 0.48 | 0.37 | -7 | 28 | 10.9 |
| P7 | nyam | q75_H75 | 1050 | 0.15 | 0.33 | -88 | -96 | 13.3 |
| P7 | nyam | rem_own_k0.75 | 1050 | 0.71 | 0.37 | -43 | 67 | 33.2 |
| U7 | asia | q50_H75 | 686 | 0.28 | 0.54 | 412 | 320 | 10.4 |
| U7 | asia | q60_H75 | 686 | 0.15 | 0.50 | 322 | 270 | 8.0 |
| U7 | asia | q75_H75 | 686 | 0.03 | 0.47 | -260 | -383 | 6.8 |
| U7 | asia | rem_own_k0.75 | 686 | 0.74 | 0.53 | 375 | 4 | 30.5 |
| U7 | london | q50_H75 | 645 | 0.27 | 0.46 | -102 | -183 | 8.7 |
| U7 | london | q60_H75 | 645 | 0.13 | 0.46 | -173 | -182 | 7.8 |
| U7 | london | q75_H75 | 645 | 0.03 | 0.50 | -396 | -466 | 5.4 |
| U7 | london | rem_own_k0.75 | 645 | 0.68 | 0.51 | 166 | 14 | 24.5 |

### Exact cap cells (global: all books at once; L3M, L6M when promoted; delta vs JN05W2)
| cell | L3M | L6M | HOLD | d mean/wk at $4.84 L3M |
|---|---|---|---|---|
| quantile 50 cap, horizon = 75th-percentile holding time | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | +1452 (lots +9/wk) |
| quantile 60 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 75 cap, horizon = 75th-percentile holding time | +177 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 101%, w2l 0 | n/a | n/a | +176 (lots +0/wk) |
| quantile 90 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 60 cap, horizon = median holding time | -1554 $/wk, DD +2.5%, ww +1445, stops 10.42(10.35), b5 89%, w2l 1 | n/a | n/a | -1658 (lots +29/wk) |
| quantile 75 cap, horizon = median holding time | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=0.5 | -8393 $/wk, DD +2.1%, ww +5889, stops 7.76(10.35), b5 57%, w2l 3 | n/a | n/a | -8805 (lots +113/wk) |
| remaining-range cap, forecast own 20-session mean, k=0.75 | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=1.0 | -6226 $/wk, DD +27.0%, ww +12290, stops 8.98(10.35), b5 66%, w2l 2 | n/a | n/a | -6458 (lots +63/wk) |
| remaining-range cap, forecast own 20-session mean, k=1.25 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.5 | -10795 $/wk, DD +40.3%, ww +11430, stops 7.00(10.35), b5 51%, w2l 4 | n/a | n/a | -11257 (lots +126/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.75 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.0 | -7259 $/wk, DD +39.4%, ww +17319, stops 7.76(10.35), b5 65%, w2l 2 | n/a | n/a | -7570 (lots +85/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.25 | pending | | | |
| EV-best target, bounded by the book target | -14326 $/wk, DD -25.6%, ww -15613, stops 8.45(10.35), b5 46%, w2l 3 | n/a | n/a | -14639 (lots +86/wk) |
| EV-best target, unbounded | pending | | | |
| extension m=1.0 | -110 $/wk, DD -53.4%, ww -2988, stops 11.72(10.35), b5 124%, w2l 2 | n/a | n/a | -18 (lots -25/wk) |
| extension m=1.5 | pending | | | |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts skipped | +1443 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | n/a | n/a | +1410 (lots +9/wk) |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts at half size | pending | | | |
| PLANTED-EDGE CHECK (look-ahead oracle 0.9 x realised MFE, not a result) | +85531 $/wk, DD +67.0%, ww +64263, stops 6.54(10.35), b5 259%, w2l 0 | n/a | n/a | +85219 (lots +85/wk) |
| PLANTED-EDGE CHECK (oracle 0.6 x realised MFE, not a result) | pending | | | |
| PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 | n/a | -125 (lots +1/wk) |
| PLACEBO pl23: quantile 50 cap, horizon = 75th-percentile holding time | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 | n/a | -871 (lots +3/wk) |
| PLACEBO pl37: quantile 50 cap, horizon = 75th-percentile holding time | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 | n/a | -612 (lots +2/wk) |
| PLACEBO plR1: quantile 50 cap, horizon = 75th-percentile holding time | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 | n/a | -670 (lots +4/wk) |

### The one candidate: forecast-quantile-50 cap, horizon = 75th-percentile holding time (L3M mean-only so far): all windows, W44 removed, placebos
| window | scope all | W44 removed |
|---|---|---|
| L3M | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 |
| L6M | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 |
| HOLD | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 |
| MID | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 |
| PREUW | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 |
Placebos (same cap, forecast features taken n sessions earlier at the same clock / a random earlier session), L3M then L6M when run:
| placebo | L3M | L6M |
|---|---|---|
| pl11 | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 |
| pl23 | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 |
| pl37 | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 |
| plR1 | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 |

### Per book x session exact cap cells (clean: one book in one session)
| slice | cap | L3M | May-Jul |
|---|---|---|---|
| A7 asia | quantile 50 cap, horizon = 75th-percentile holding time | -17 (live -30; $4.84 -17) DD +0.0% ww +0 stops 4.03(4.03) | n/a |

### FOR THE LIVE BUILD (what D7 computes at the signal second)
From its own 1-minute bars: last 15/30/60/120-minute range and realised vol, same-offset range over the previous 20 sessions (median), session ranges of the last 5/20 sessions, range so far, the entry position in the session range (favourable-side room), elapsed fraction of the session, ln of the book-session horizon; a small coefficient table per session (15 weights, mean, sd, intercept, four residual quantile offsets) refit every 14 days and shipped as a static file. Cap = min(60, price x exp(prediction + quantile offset) - 2); orders: the target limit is placed at the capped price. The remaining-range version needs the HAR session forecast (T-RANGE2 file) or D7 computes its own 20-session mean. No intraday feed from the box.


## Per book and session, clean, and the assembled stack
**STATUS (plain, not a PASS; B1 in progress, no "nothing passes" verdict is allowed until it is done): single-book single-session cells scored in L3M for 14 of 14 slices; slice picks so far: {}.**

Method (user order PART B, 2026-11-15): each cell = the Dial 10 hook restricted to ONE book in ONE session (every other book/session unchanged at JN05W2), exact engine, all layers ON, live caps. Dollars are BASE lots; the x1.75 live figure sits beside each headline (live); the $4.84 figure reprices every contract at the FEES.md $4.84 RT (engine raw $1.18). Compared on the same book x session slice of JN05W2 (day locks/caps still interact across books, which is why the cells are run for real and not sliced from the global run). B1a settings per slice: direction both / narrow-only / wide-only x gearing 0.5 / 1.0 at the 75th-percentile horizon, plus narrow/wide g1.0 at the median horizon; "fixed" = JN05W2 itself. Walk-forward: the pick for each slice is made on 2026-05..07 only (older than L3M); L3M (2026-08..10) is then out-of-sample. B1b (around each pick): lots cap 1.5/3, lots follow half the change, dead band 0/20%, target ratio 0.8/1.2, lever stop-only (sl: stop W, lots inverse, target in the same points) / target-only (tg) / size-only (sz: bracket fixed, lots follow the forecast), noise floor k = 3/4/5 x recent 5-minute ATR (bracket never narrower), clips 25..120 / 20..150.

### B1 table: per slice, every cell (L3M, delta vs JN05W2 same slice; May-Jul = the selection window)
| slice | setting | May-Jul (selection) | L3M (out of sample) | L6M |
|---|---|---|---|---|
| A7 asia | both/g1.0/H75 | -374 (live -654; $4.84 -370) DD -10.9% ww -261 stops 2.97(3.88) | +47 (live +83; $4.84 +40) DD +25.6% ww +1495 stops 5.55(4.03) | -163 (live -286; $4.84 -165) DD -29.2% ww +1253 stops 4.26(3.96) |
| A7 asia | narrow/g1.0/H75 | -419 (live -733; $4.84 -423) DD -0.6% ww -175 stops 4.49(3.88) | -18 (live -32; $4.84 -26) DD +17.7% ww +722 stops 5.63(4.03) | -219 (live -383; $4.84 -224) DD -19.1% ww +722 stops 5.06(3.96) |
| A7 asia | both/g0.5/H75 | -556 (live -973; $4.84 -553) DD -9.2% ww +72 stops 3.50(3.88) | -192 (live -336; $4.84 -195) DD +10.1% ww +412 stops 5.10(4.03) | -374 (live -654; $4.84 -374) DD -36.6% ww +412 stops 4.30(3.96) |
| A7 asia | narrow/g0.5/H75 | -350 (live -612; $4.84 -352) DD +0.0% ww +0 stops 4.34(3.88) | -186 (live -325; $4.84 -189) DD +10.0% ww +552 stops 5.10(4.03) | -268 (live -469; $4.84 -270) DD -15.8% ww +552 stops 4.72(3.96) |
| A7 asia | wide/g1.0/H75 | +19 (live +33; $4.84 +26) DD -10.9% ww +283 stops 2.51(3.88) | -15 (live -26; $4.84 -14) DD +2.4% ww -426 stops 3.96(4.03) | +2 (live +3; $4.84 +6) DD -13.6% ww -426 stops 3.23(3.96) |
| A7 asia | wide/g0.5/H75 | n/a | -1 (live -1; $4.84 -1) DD +1.4% ww -140 stops 4.03(4.03) | n/a |
| A7 asia | wide/g1.0/H50 | n/a | -48 (live -85; $4.84 -48) DD -3.0% ww -426 stops 3.88(4.03) | n/a |
| A7 asia | narrow/g1.0/H50 | n/a | -159 (live -279; $4.84 -171) DD -8.3% ww +877 stops 5.93(4.03) | n/a |
| H7 asia | wide/g0.5/H75 | n/a | +123 (live +215; $4.84 +123) DD +0.0% ww +0 stops 0.23(0.23) | n/a |
| H7 asia | wide/g1.0/H75 | n/a | -67 (live -118; $4.84 -67) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | wide/g1.0/H50 | n/a | -312 (live -546; $4.84 -312) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | both/g1.0/H75 | +1123 (live +1965; $4.84 +1129) DD +6.5% ww +1483 stops 0.53(0.61) | +177 (live +309; $4.84 +163) DD -33.6% ww -1228 stops 0.61(0.23) | +650 (live +1137; $4.84 +646) DD +6.5% ww +1483 stops 0.57(0.42) |
| H7 asia | narrow/g1.0/H75 | n/a | +244 (live +427; $4.84 +230) DD -33.6% ww -1228 stops 0.53(0.23) | n/a |
| H7 asia | both/g0.5/H75 | n/a | -574 (live -1004; $4.84 -580) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g0.5/H75 | n/a | -697 (live -1219; $4.84 -703) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g1.0/H50 | n/a | -355 (live -621; $4.84 -372) DD -120.5% ww -2166 stops 0.53(0.23) | n/a |
| H7 nyam | narrow/g1.0/H50 | n/a | +252 (live +441; $4.84 +252) DD +60.4% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | both/g1.0/H75 | n/a | +281 (live +491; $4.84 +280) DD +57.7% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | narrow/g1.0/H75 | -187 (live -328; $4.84 -188) DD -4.0% ww +0 stops 0.53(0.46) | +258 (live +452; $4.84 +258) DD +57.7% ww +480 stops 0.30(0.38) | +35 (live +62; $4.84 +35) DD +24.1% ww +480 stops 0.42(0.42) |
| H7 nyam | both/g0.5/H75 | +103 (live +180; $4.84 +103) DD +29.2% ww -83 stops 0.46(0.46) | +87 (live +153; $4.84 +87) DD +2.2% ww +195 stops 0.38(0.38) | +95 (live +167; $4.84 +95) DD +2.2% ww +195 stops 0.42(0.42) |
| H7 nyam | narrow/g0.5/H75 | n/a | +77 (live +134; $4.84 +77) DD +2.2% ww +195 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g0.5/H75 | n/a | +11 (live +19; $4.84 +11) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H75 | n/a | +22 (live +39; $4.84 +22) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H50 | n/a | +30 (live +53; $4.84 +30) DD +0.0% ww +0 stops 0.30(0.38) | n/a |
| K7 asia | wide/g1.0/H75 | n/a | +297 (live +520; $4.84 +298) DD +0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | wide/g0.5/H75 | n/a | -54 (live -94; $4.84 -54) DD -0.7% ww -404 stops 0.00(0.00) | n/a |
| K7 asia | narrow/g0.5/H75 | n/a | +1877 (live +3285; $4.84 +1855) DD -19.6% ww -2412 stops 0.00(0.00) | n/a |
| K7 asia | both/g0.5/H75 | n/a | +1823 (live +3191; $4.84 +1801) DD -28.8% ww -3232 stops 0.00(0.00) | n/a |
| K7 asia | wide/g1.0/H50 | n/a | -401 (live -702; $4.84 -400) DD -35.9% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | both/g1.0/H75 | n/a | +1292 (live +2261; $4.84 +1220) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H75 | n/a | +912 (live +1595; $4.84 +838) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H50 | n/a | +355 (live +621; $4.84 +268) DD -86.2% ww -5644 stops 0.00(0.00) | n/a |
| K7 london | both/g0.5/H75 | n/a | -9 (live -15; $4.84 -14) DD +8.7% ww +4326 stops 0.23(0.30) | n/a |
| K7 london | wide/g0.5/H75 | n/a | +27 (live +48; $4.84 +29) DD +0.5% ww +0 stops 0.30(0.30) | n/a |
| K7 london | wide/g1.0/H50 | n/a | +431 (live +755; $4.84 +433) DD -3.3% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g0.5/H75 | n/a | -123 (live -215; $4.84 -130) DD -4.2% ww +4733 stops 0.23(0.30) | n/a |
| K7 london | wide/g1.0/H75 | n/a | +157 (live +274; $4.84 +160) DD -4.8% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g1.0/H50 | n/a | -182 (live -319; $4.84 -204) DD -13.7% ww +3097 stops 0.23(0.30) | n/a |
| K7 london | both/g1.0/H75 | n/a | +481 (live +841; $4.84 +462) DD -25.5% ww +4257 stops 0.38(0.30) | n/a |
| K7 london | narrow/g1.0/H75 | n/a | -31 (live -55; $4.84 -55) DD -42.3% ww +4122 stops 0.38(0.30) | n/a |
| K7 nyam | narrow/g1.0/H50 | n/a | +769 (live +1345; $4.84 +761) DD +51.0% ww +2185 stops 0.00(0.00) | n/a |
| K7 nyam | both/g1.0/H75 | n/a | +1160 (live +2030; $4.84 +1153) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g1.0/H75 | n/a | +984 (live +1722; $4.84 +977) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g0.5/H75 | n/a | +668 (live +1170; $4.84 +667) DD +40.3% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | both/g0.5/H75 | n/a | +806 (live +1410; $4.84 +805) DD +39.5% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H75 | n/a | +176 (live +308; $4.84 +176) DD -0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H50 | n/a | +252 (live +441; $4.84 +253) DD -0.3% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g0.5/H75 | n/a | +137 (live +241; $4.84 +137) DD -0.8% ww +0 stops 0.00(0.00) | n/a |
| K7 nypm | wide/g1.0/H50 | n/a | +442 (live +773; $4.84 +442) DD +17.3% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | wide/g1.0/H75 | n/a | +70 (live +122; $4.84 +70) DD +13.1% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | both/g1.0/H75 | n/a | -184 (live -322; $4.84 -197) DD +9.8% ww +1145 stops 0.15(0.08) | n/a |
| K7 nypm | wide/g0.5/H75 | n/a | -4 (live -8; $4.84 -4) DD -1.5% ww -38 stops 0.00(0.08) | n/a |
| K7 nypm | narrow/g1.0/H50 | n/a | +48 (live +84; $4.84 +32) DD -1.9% ww +105 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g1.0/H75 | n/a | -254 (live -445; $4.84 -267) DD -3.3% ww +990 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g0.5/H75 | n/a | -266 (live -465; $4.84 -269) DD -26.7% ww +140 stops 0.08(0.08) | n/a |
| K7 nypm | both/g0.5/H75 | n/a | -270 (live -473; $4.84 -274) DD -27.3% ww +102 stops 0.00(0.08) | n/a |
| M7 london | wide/g1.0/H75 | n/a | +1614 (live +2824; $4.84 +1616) DD +4.9% ww +1190 stops 0.53(0.91) | n/a |
| M7 london | wide/g0.5/H75 | n/a | +688 (live +1204; $4.84 +689) DD +4.4% ww +1400 stops 0.84(0.91) | n/a |
| M7 london | wide/g1.0/H50 | n/a | +538 (live +942; $4.84 +540) DD -1.3% ww -80 stops 0.84(0.91) | n/a |
| M7 london | both/g0.5/H75 | n/a | +1147 (live +2008; $4.84 +1139) DD -8.1% ww +130 stops 1.07(0.91) | n/a |
| M7 london | narrow/g0.5/H75 | n/a | +417 (live +730; $4.84 +408) DD -10.9% ww -1075 stops 1.14(0.91) | n/a |
| M7 london | narrow/g1.0/H50 | n/a | +476 (live +833; $4.84 +446) DD -19.9% ww +1144 stops 1.45(0.91) | n/a |
| M7 london | narrow/g1.0/H75 | n/a | -366 (live -640; $4.84 -390) DD -20.4% ww +80 stops 1.29(0.91) | n/a |
| M7 london | both/g1.0/H75 | n/a | +1142 (live +1999; $4.84 +1121) DD -23.2% ww -729 stops 0.91(0.91) | n/a |
| M7 nyam | narrow/g1.0/H50 | n/a | +439 (live +769; $4.84 +424) DD +26.0% ww -222 stops 0.38(0.23) | n/a |
| M7 nyam | both/g0.5/H75 | n/a | +79 (live +138; $4.84 +75) DD +0.8% ww +194 stops 0.30(0.23) | n/a |
| M7 nyam | narrow/g0.5/H75 | n/a | +73 (live +127; $4.84 +69) DD +0.8% ww +194 stops 0.38(0.23) | n/a |
| M7 nyam | wide/g0.5/H75 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H75 | n/a | +16 (live +28; $4.84 +16) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H50 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | both/g1.0/H75 | n/a | +419 (live +733; $4.84 +405) DD -6.8% ww -991 stops 0.46(0.23) | n/a |
| M7 nyam | narrow/g1.0/H75 | n/a | +402 (live +704; $4.84 +388) DD -6.8% ww -991 stops 0.53(0.23) | n/a |
| P7 asia | narrow/g1.0/H50 | n/a | -3918 (live -6857; $4.84 -4186) DD -0.4% ww -4286 stops 0.46(0.15) | n/a |
| P7 asia | both/g0.5/H75 | n/a | -5946 (live -10406; $4.84 -6044) DD -1.0% ww +6944 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g0.5/H75 | n/a | -5762 (live -10084; $4.84 -5860) DD -1.0% ww +9022 stops 0.15(0.15) | n/a |
| P7 asia | wide/g0.5/H75 | n/a | -184 (live -322; $4.84 -183) DD -4.9% ww -2079 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g1.0/H75 | n/a | -2696 (live -4718; $4.84 -2882) DD -7.8% ww -10346 stops 0.53(0.15) | n/a |
| P7 asia | wide/g1.0/H50 | n/a | -816 (live -1428; $4.84 -812) DD -22.6% ww -9033 stops 0.15(0.15) | n/a |
| P7 asia | wide/g1.0/H75 | n/a | -491 (live -858; $4.84 -490) DD -25.2% ww -10331 stops 0.15(0.15) | n/a |
| P7 asia | both/g1.0/H75 | n/a | -3315 (live -5802; $4.84 -3501) DD -36.1% ww -13164 stops 0.53(0.15) | n/a |
| P7 london | both/g0.5/H75 | n/a | +894 (live +1565; $4.84 +886) DD +29.6% ww -1633 stops 0.08(0.08) | n/a |
| P7 london | narrow/g0.5/H75 | n/a | +386 (live +675; $4.84 +375) DD +28.5% ww -1328 stops 0.08(0.08) | n/a |
| P7 london | narrow/g1.0/H50 | n/a | +927 (live +1622; $4.84 +895) DD +19.7% ww -3009 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H75 | n/a | -142 (live -249; $4.84 -138) DD +2.7% ww -458 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H50 | n/a | +265 (live +464; $4.84 +266) DD +1.1% ww +0 stops 0.08(0.08) | n/a |
| P7 london | wide/g0.5/H75 | n/a | +385 (live +674; $4.84 +387) DD -1.9% ww -238 stops 0.08(0.08) | n/a |
| P7 london | both/g1.0/H75 | n/a | +1179 (live +2064; $4.84 +1145) DD -9.8% ww -5408 stops 0.15(0.08) | n/a |
| P7 london | narrow/g1.0/H75 | n/a | +1322 (live +2313; $4.84 +1282) DD -14.4% ww -5203 stops 0.15(0.08) | n/a |
| P7 nyam | both/g1.0/H75 | n/a | +697 (live +1220; $4.84 +685) DD +51.3% ww +354 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g1.0/H75 | n/a | +543 (live +951; $4.84 +529) DD +45.9% ww +324 stops 0.30(0.38) | n/a |
| P7 nyam | both/g0.5/H75 | n/a | +105 (live +184; $4.84 +99) DD +36.7% ww +238 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g0.5/H75 | n/a | -13 (live -23; $4.84 -20) DD +36.4% ww +262 stops 0.30(0.38) | n/a |
| P7 nyam | wide/g0.5/H75 | n/a | +118 (live +207; $4.84 +119) DD +0.3% ww -25 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H75 | n/a | +16 (live +27; $4.84 +17) DD -7.5% ww -105 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H50 | n/a | -544 (live -952; $4.84 -543) DD -47.7% ww -3348 stops 0.38(0.38) | n/a |
| U7 asia | narrow/g1.0/H50 | n/a | +1222 (live +2139; $4.84 +1201) DD +15.6% ww -265 stops 1.90(1.83) | n/a |
| U7 asia | both/g1.0/H75 | n/a | +71 (live +124; $4.84 +56) DD +8.3% ww -1836 stops 1.98(1.83) | n/a |
| U7 asia | narrow/g1.0/H75 | n/a | +502 (live +879; $4.84 +487) DD +8.3% ww +983 stops 1.98(1.83) | n/a |
| U7 asia | both/g0.5/H75 | n/a | -800 (live -1399; $4.84 -808) DD +6.6% ww -2883 stops 2.05(1.83) | n/a |
| U7 asia | narrow/g0.5/H75 | n/a | -162 (live -284; $4.84 -170) DD +6.6% ww +57 stops 2.05(1.83) | n/a |
| U7 asia | wide/g0.5/H75 | n/a | -637 (live -1115; $4.84 -637) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H75 | n/a | -431 (live -755; $4.84 -431) DD +0.0% ww -1836 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H50 | n/a | -648 (live -1134; $4.84 -648) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 london | narrow/g0.5/H75 | n/a | +393 (live +687; $4.84 +392) DD +17.2% ww +1796 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H75 | n/a | +246 (live +431; $4.84 +243) DD +3.1% ww -1185 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H50 | n/a | -41 (live -72; $4.84 -48) DD -9.9% ww -1991 stops 1.52(1.45) | n/a |
| U7 london | both/g0.5/H75 | n/a | -891 (live -1560; $4.84 -890) DD -25.4% ww -3538 stops 1.52(1.45) | n/a |
| U7 london | wide/g1.0/H50 | n/a | -839 (live -1468; $4.84 -837) DD -33.9% ww -4122 stops 1.37(1.45) | n/a |
| U7 london | wide/g0.5/H75 | n/a | -1284 (live -2247; $4.84 -1282) DD -44.3% ww -6280 stops 1.52(1.45) | n/a |
| U7 london | both/g1.0/H75 | n/a | -1728 (live -3025; $4.84 -1729) DD -105.5% ww -7540 stops 1.60(1.45) | n/a |
| U7 london | wide/g1.0/H75 | n/a | -1975 (live -3455; $4.84 -1972) DD -109.8% ww -6355 stops 1.60(1.45) | n/a |

### Summary per slice: pick made on May-Jul, result on L3M
| slice | pick | L3M result of the pick | verdict |
|---|---|---|---|
| A7 asia | pending | | |
| H7 asia | pending | | |
| H7 nyam | pending | | |
| K7 asia | pending | | |
| K7 london | pending | | |
| K7 nyam | pending | | |
| K7 nypm | pending | | |
| M7 london | pending | | |
| M7 nyam | pending | | |
| P7 asia | pending | | |
| P7 london | pending | | |
| P7 nyam | pending | | |
| U7 asia | pending | | |
| U7 london | pending | | |

### B2: why the global version adds full stops (narrow-only/both g1.0 H75 cell, L3M, trade tables)
Reference JN05W2 L3M (no O7): 1855 trades, stop rate 0.071, 132 stops (13 weeks).

**M1_75_g10_c1_d10_c20_tb_B**: 2038 trades (+183 vs JN05W2), stops 173 (+41), stop rate 0.085 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 437 | 0.103 | 3.05 | 94 |
| (40, 50] | 721 | 0.074 | 2.36 | 271 |
| (50, 55] | 232 | 0.099 | 1.97 | 169 |
| (55, 60] | 435 | 0.076 | 1.87 | 76 |
| (60, 70] | 75 | 0.120 | 2.01 | -385 |
| (70, 80] | 62 | 0.048 | 1.68 | -284 |
| (80, 101] | 76 | 0.092 | 1.13 | -591 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1543 | 0.069 | 2.21 | 54 |
| (3.0, 4.0] | 294 | 0.116 | 2.29 | 239 |
| (4.0, 5.0] | 74 | 0.108 | 2.31 | 364 |
| (5.0, 6.0] | 6 | 0.167 | 2.50 | 172 |
| (6.0, 8.0] | 4 | 0.000 | 1.00 | -119 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1068 | 0.096 | 1.00 | 4 |
| (1, 2] | 385 | 0.078 | 2.00 | 115 |
| (2, 3] | 215 | 0.093 | 3.00 | 23 |
| (3, 5] | 195 | 0.062 | 4.46 | 256 |
| (5, 8] | 138 | 0.065 | 6.70 | 690 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

**M1_75_g10_c1_d10_c20_tb_N**: 2072 trades (+217 vs JN05W2), stops 178 (+46), stop rate 0.086 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 449 | 0.105 | 3.02 | 97 |
| (40, 50] | 725 | 0.073 | 2.35 | 272 |
| (50, 55] | 236 | 0.102 | 1.97 | 150 |
| (55, 60] | 662 | 0.082 | 1.82 | -29 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1644 | 0.072 | 2.18 | 50 |
| (3.0, 4.0] | 264 | 0.121 | 2.38 | 348 |
| (4.0, 5.0] | 44 | 0.091 | 3.11 | 1063 |
| (5.0, 6.0] | 3 | 0.000 | 3.33 | 68 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1073 | 0.095 | 1.00 | 8 |
| (1, 2] | 413 | 0.085 | 2.00 | 117 |
| (2, 3] | 197 | 0.081 | 3.00 | 213 |
| (3, 5] | 217 | 0.074 | 4.43 | 196 |
| (5, 8] | 135 | 0.067 | 6.74 | 714 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

Reading of the W/ATR5 table: ATR5 = mean range of the last 14 five-minute buckets in points; a bracket 3x ATR5 or less is within ordinary 5-minute noise. The noise-floor cells (floor 3/4/5 x ATR5, narrowing only) are listed in B3.


### B3: levers (stop-only / target-only / both / size-only) and noise floor, per slice
| slice | cell | L3M | May-Jul |
|---|---|---|---|

### B4: assembled stack (each slice at its own walk-forward pick, run together)
(not run yet: starts when every slice has a pick)


## Target capped at the forecast
**VERDICT (plain, not a PASS; FIRST PASS; 15 of 26 global exact cap cells scored in L3M, per book x session exact cells still running): planted-edge check PASSED through the exact engine (look-ahead oracle target 0.9 x realised MFE: +85531 $/wk, DD +67.0%, ww +64263; this is a mechanism check, NOT a result); the reachable move is only weakly forecastable (R2 on ln MFE 0.03-0.14, quantile calibration good); in the exact L3M cells the cap at the forecast 50th-percentile move (horizon = 75th-percentile holding time) gives +1486 $/wk, DD -0.5%, ww -240 and the 75th-percentile cap +177 $/wk, DD +0.0%, ww +0, the remaining-range caps cut drawdown (own k1.0 -6226 $/wk, DD +27.0%, ww +12290; HAR k1.0 -7259 $/wk, DD +39.4%, ww +17319) but cost thousands per week. Best exact L3M cap cell inside the mean gate by DD: PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time (DD +7.9%, -120 $/wk). L6M/HOLD/older still to run before any verdict.**

Planted-edge check (H1) for the capping mechanism: cells `tcoracle0.9` / `0.6` set the target to 0.9 / 0.6 x the REALISED maximum favourable move (look-ahead, only to prove the mechanism can show an edge through the exact engine); they must come out strongly positive. Status below in the exact table. Until they do, an exact cap verdict is not stated.

Definition. Reachable move = maximum favourable excursion from the signal-second bar close over the book-session holding horizon H (H50/H75 = median / 75th percentile holding time of that book+session, causal), points. Model: walk-forward ridge (14-day blocks, expanding, min 90 days, per session) on ln((MFE+2)/price) from the Dial 10 own-bar inputs (last 15/30/60/120 min range and vol, same-clock normal, own session level, range used so far, elapsed fraction) plus the side-aware room in the session range so far; quantiles q = fitted + empirical training-residual quantile (50/60/75/90). Cap: target = min(book target 60 pts [58 after fills], q-quantile), stop, lots and every other level unchanged. Remaining-range cap: target = min(book target, k x (session range forecast - range printed so far)), forecast = own (price x exp(sf20), mean of the last 20 sessions) or T-RANGE2 HAR (fc_r2_har, available-epoch checked). Small caps (< 30 pts = 0.5 x stop): take / skip / half. EV target: argmax over T in [20, book target or 300] of T x P(MFE>=T) - stop x (1-P) with the lognormal forecast (ignores the stop-first ordering, so optimistic). Extension: if the forecast median MFE is >= m x book target, target = min(q50, 2 x book target). Lots/base basis: dollars are BASE lots (live x1.75 = multiply by 1.75); fee columns $4.84 beside raw $1.18 where shown.

### Item 1: calibration of the forecast quantiles (share of trades whose realized MFE exceeded the forecast quantile; a q-quantile should be exceeded 1-q of the time = 0.50 / 0.40 / 0.25 / 0.10) and R2 of ln MFE, per session
| H | session | window | n | >q50 | >q60 | >q75 | >q90 | R2 ln MFE | median q75 (pts) | share q75 < 60 |
|---|---|---|---|---|---|---|---|---|---|---|
| 50 | asia | older (<2026-05) | 5119 | 0.51 | 0.41 | 0.26 | 0.12 | 0.121 | 80 | 0.222 |
| 50 | asia | L6M | 2006 | 0.49 | 0.38 | 0.23 | 0.08 | 0.058 | 111 | 0.047 |
| 50 | asia | L3M | 875 | 0.46 | 0.34 | 0.20 | 0.07 | -0.014 | 90 | 0.098 |
| 50 | london | older (<2026-05) | 4892 | 0.51 | 0.41 | 0.26 | 0.11 | 0.142 | 62 | 0.438 |
| 50 | london | L6M | 1406 | 0.48 | 0.37 | 0.23 | 0.08 | 0.028 | 76 | 0.166 |
| 50 | london | L3M | 673 | 0.48 | 0.37 | 0.24 | 0.07 | -0.008 | 68 | 0.247 |
| 50 | nyam | older (<2026-05) | 4142 | 0.47 | 0.38 | 0.24 | 0.11 | 0.077 | 63 | 0.397 |
| 50 | nyam | L6M | 600 | 0.51 | 0.40 | 0.24 | 0.09 | 0.097 | 83 | 0.157 |
| 50 | nyam | L3M | 271 | 0.51 | 0.38 | 0.20 | 0.06 | 0.077 | 68 | 0.258 |
| 50 | nypm | older (<2026-05) | 817 | 0.48 | 0.40 | 0.26 | 0.13 | 0.073 | 62 | 0.419 |
| 50 | nypm | L6M | 150 | 0.59 | 0.50 | 0.33 | 0.13 | 0.221 | 71 | 0.307 |
| 50 | nypm | L3M | 56 | 0.50 | 0.36 | 0.21 | 0.09 | 0.104 | 54 | 0.589 |
| 50 | all | older (<2026-05) | 14970 | 0.50 | 0.40 | 0.26 | 0.12 | 0.123 | 68 | 0.352 |
| 50 | all | L6M | 4162 | 0.49 | 0.38 | 0.23 | 0.08 | 0.080 | 91 | 0.113 |
| 50 | all | L3M | 1875 | 0.47 | 0.36 | 0.21 | 0.07 | 0.014 | 76 | 0.189 |
| 75 | asia | older (<2026-05) | 5119 | 0.52 | 0.41 | 0.26 | 0.12 | 0.134 | 122 | 0.032 |
| 75 | asia | L6M | 2006 | 0.50 | 0.40 | 0.24 | 0.08 | 0.027 | 178 | 0.000 |
| 75 | asia | L3M | 875 | 0.45 | 0.35 | 0.20 | 0.05 | -0.016 | 156 | 0.000 |
| 75 | london | older (<2026-05) | 4891 | 0.51 | 0.42 | 0.27 | 0.11 | 0.157 | 101 | 0.100 |
| 75 | london | L6M | 1406 | 0.49 | 0.37 | 0.21 | 0.08 | 0.069 | 118 | 0.001 |
| 75 | london | L3M | 673 | 0.49 | 0.38 | 0.21 | 0.09 | 0.025 | 108 | 0.000 |
| 75 | nyam | older (<2026-05) | 4142 | 0.48 | 0.38 | 0.23 | 0.10 | 0.065 | 91 | 0.081 |
| 75 | nyam | L6M | 600 | 0.50 | 0.40 | 0.24 | 0.10 | 0.098 | 125 | 0.015 |
| 75 | nyam | L3M | 271 | 0.44 | 0.34 | 0.19 | 0.05 | 0.051 | 103 | 0.015 |
| 75 | nypm | older (<2026-05) | 812 | 0.49 | 0.37 | 0.26 | 0.11 | 0.043 | 87 | 0.095 |
| 75 | nypm | L6M | 150 | 0.53 | 0.46 | 0.34 | 0.17 | 0.179 | 117 | 0.013 |
| 75 | nypm | L3M | 56 | 0.41 | 0.30 | 0.21 | 0.07 | -0.076 | 93 | 0.036 |
| 75 | all | older (<2026-05) | 14964 | 0.51 | 0.40 | 0.25 | 0.11 | 0.131 | 102 | 0.071 |
| 75 | all | L6M | 4162 | 0.50 | 0.39 | 0.23 | 0.09 | 0.079 | 149 | 0.003 |
| 75 | all | L3M | 1875 | 0.46 | 0.36 | 0.20 | 0.06 | 0.032 | 128 | 0.003 |

### Items 3 and 4 (and 2): offline replay of the caps on the JN05W2 trade paths, all 43 months (estimate: 1-min paths, cap counted only before the exit bar, so cut/stop ordering is conservative; the exact cells below decide). d mean $/wk and DD cut % vs JN05W2 on the same trades, scope all, then per session for the cap with the most trades capped
| cap | small-cap rule | scope | window | d mean $/wk (live x1.75) | DD cut % | d worst week | d stops/wk | share capped | share where cap hit |
|---|---|---|---|---|---|---|---|---|---|
| q50_H50 | take | all | L3M | +409 (+715) | -3.9 | -1411 | +0.00 | 0.82 | 0.45 |
| q50_H50 | take | all | L6M | -96 (-169) | -3.9 | -1411 | +0.00 | 0.62 | 0.33 |
| q50_H50 | take | all | OLDER | -1795 (-3141) | +12.0 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | skip | all | L3M | -1581 (-2767) | -5.0 | -1996 | +0.00 | 0.82 | 0.45 |
| q50_H50 | skip | all | L6M | -1445 (-2528) | -5.0 | -1996 | +0.00 | 0.62 | 0.33 |
| q50_H50 | skip | all | OLDER | -2271 (-3975) | +17.4 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | half | all | L3M | -586 (-1026) | -4.4 | -1704 | +0.00 | 0.82 | 0.45 |
| q50_H50 | half | all | L6M | -771 (-1348) | -4.4 | -1704 | +0.00 | 0.62 | 0.33 |
| q50_H50 | half | all | OLDER | -2033 (-3558) | +16.5 | +13127 | +0.00 | 0.80 | 0.45 |
| q60_H50 | take | all | L3M | -1525 (-2668) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | take | all | L6M | -839 (-1469) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | take | all | OLDER | -1296 (-2267) | +12.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | skip | all | L3M | -3272 (-5726) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | skip | all | L6M | -1811 (-3170) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | skip | all | OLDER | -1648 (-2885) | +8.8 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | half | all | L3M | -2398 (-4197) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | half | all | L6M | -1325 (-2319) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | half | all | OLDER | -1472 (-2576) | +10.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q75_H50 | take | all | L3M | +414 (+725) | -0.4 | -214 | +0.00 | 0.21 | 0.11 |
| q75_H50 | take | all | L6M | -44 (-77) | -0.4 | -214 | +0.00 | 0.13 | 0.06 |
| q75_H50 | take | all | OLDER | -719 (-1258) | -1.1 | +13801 | +0.00 | 0.37 | 0.18 |
| q90_H50 | take | all | L3M | +191 (+334) | +0.0 | +0 | +0.00 | 0.02 | 0.01 |
| q90_H50 | take | all | L6M | +142 (+249) | +0.0 | +0 | +0.00 | 0.01 | 0.01 |
| q90_H50 | take | all | OLDER | -169 (-296) | -1.8 | +1686 | +0.00 | 0.08 | 0.03 |
| q50_H75 | take | all | L3M | +128 (+225) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | take | all | L6M | +624 (+1092) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | take | all | OLDER | -931 (-1628) | -13.1 | +11346 | +0.00 | 0.51 | 0.26 |
| q50_H75 | skip | all | L3M | +178 (+312) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | skip | all | L6M | +685 (+1198) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | skip | all | OLDER | -1302 (-2279) | -4.6 | +14384 | +0.00 | 0.51 | 0.26 |
| q50_H75 | half | all | L3M | +153 (+268) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | half | all | L6M | +654 (+1145) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | half | all | OLDER | -1116 (-1954) | -8.8 | +12865 | +0.00 | 0.51 | 0.26 |
| q60_H75 | take | all | L3M | +830 (+1452) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | take | all | L6M | +379 (+664) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | take | all | OLDER | -478 (-836) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | skip | all | L3M | +958 (+1677) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | skip | all | L6M | +421 (+737) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | skip | all | OLDER | -402 (-703) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | half | all | L3M | +894 (+1564) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | half | all | L6M | +400 (+700) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | half | all | OLDER | -440 (-769) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q75_H75 | take | all | L3M | +236 (+413) | +0.0 | +0 | +0.00 | 0.01 | 0.00 |
| q75_H75 | take | all | L6M | +105 (+185) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q75_H75 | take | all | OLDER | -255 (-446) | -1.9 | +1485 | +0.00 | 0.08 | 0.04 |
| q90_H75 | take | all | L3M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | L6M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | OLDER | +10 (+18) | -0.4 | +0 | +0.00 | 0.01 | 0.00 |
| rem_own_k0.5 | take | all | L3M | -6674 (-11680) | +8.8 | -1861 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | take | all | L6M | -13204 (-23108) | +8.7 | -1861 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | take | all | OLDER | -7381 (-12916) | -40.2 | +20529 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | skip | all | L3M | -5271 (-9225) | +21.7 | +2982 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | skip | all | L6M | -10625 (-18594) | +21.7 | +2982 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | skip | all | OLDER | -6272 (-10977) | +17.3 | +21712 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | half | all | L3M | -5973 (-10452) | +16.3 | +560 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | half | all | L6M | -11915 (-20851) | +16.3 | +560 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | half | all | OLDER | -6827 (-11946) | +0.6 | +23150 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.75 | take | all | L3M | -7140 (-12494) | +9.6 | +3294 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | take | all | L6M | -10636 (-18614) | +9.6 | +3294 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | take | all | OLDER | -5846 (-10230) | -24.0 | +12208 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | skip | all | L3M | -3661 (-6406) | +10.3 | +4045 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | skip | all | L6M | -6650 (-11638) | +10.3 | +4045 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | skip | all | OLDER | -3856 (-6749) | +16.1 | +19073 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | half | all | L3M | -5400 (-9450) | +13.0 | +3670 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | half | all | L6M | -8643 (-15126) | +13.0 | +3670 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | half | all | OLDER | -4851 (-8489) | +13.0 | +20157 | +0.00 | 0.73 | 0.53 |
| rem_own_k1.0 | take | all | L3M | -5516 (-9653) | +18.3 | +9104 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | take | all | L6M | -8765 (-15339) | +18.3 | +9104 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | take | all | OLDER | -5714 (-9999) | -58.2 | +11926 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | skip | all | L3M | -3265 (-5714) | +15.0 | +8858 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | skip | all | L6M | -5683 (-9944) | +15.0 | +8858 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | skip | all | OLDER | -3872 (-6775) | -61.0 | +20250 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | half | all | L3M | -4391 (-7683) | +18.5 | +8981 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | half | all | L6M | -7224 (-12642) | +18.5 | +8981 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | half | all | OLDER | -4793 (-8387) | -58.0 | +21393 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.25 | take | all | L3M | -3112 (-5446) | +24.4 | +13750 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | take | all | L6M | -8275 (-14481) | +24.4 | +13750 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | take | all | OLDER | -5400 (-9450) | -15.5 | +4336 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | skip | all | L3M | -456 (-797) | +22.4 | +13720 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | skip | all | L6M | -4232 (-7405) | +22.4 | +13720 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | skip | all | OLDER | -3310 (-5792) | -36.4 | +22803 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | half | all | L3M | -1784 (-3121) | +25.2 | +15286 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | half | all | L6M | -6253 (-10943) | +25.2 | +15286 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | half | all | OLDER | -4355 (-7621) | -18.3 | +15544 | +0.00 | 0.54 | 0.41 |

Per session, q60 H75 take-anyway and remaining-range k=1.25 (own):
| cap | session | window | d mean $/wk | DD cut % | d worst week | share capped |
|---|---|---|---|---|---|---|
| q60_H75 | asia | L3M | +221 | +0.0 | +0 | 0.02 |
| q60_H75 | asia | L6M | +110 | +0.0 | +0 | 0.01 |
| q60_H75 | asia | OLDER | -124 | -0.0 | +0 | 0.23 |
| q60_H75 | london | L3M | +745 | +3.8 | +0 | 0.16 |
| q60_H75 | london | L6M | +330 | +3.8 | +0 | 0.12 |
| q60_H75 | london | OLDER | -294 | -2.1 | +0 | 0.35 |
| q60_H75 | nyam | L3M | +61 | -7.2 | +0 | 0.15 |
| q60_H75 | nyam | L6M | -14 | +0.0 | +0 | 0.10 |
| q60_H75 | nyam | OLDER | -37 | -6.0 | +1403 | 0.37 |
| q60_H75 | nypm | L3M | -197 | -0.0 | +0 | 0.41 |
| q60_H75 | nypm | L6M | -47 | +0.0 | +0 | 0.20 |
| q60_H75 | nypm | OLDER | -22 | -5.4 | +0 | 0.33 |
| rem_own_k1.25 | asia | L3M | -4547 | +35.2 | +434 | 0.37 |
| rem_own_k1.25 | asia | L6M | -6717 | +27.1 | +434 | 0.38 |
| rem_own_k1.25 | asia | OLDER | -4532 | -27.4 | +10774 | 0.62 |
| rem_own_k1.25 | london | L3M | +2278 | +46.3 | +12347 | 0.24 |
| rem_own_k1.25 | london | L6M | +1196 | +46.3 | +12347 | 0.30 |
| rem_own_k1.25 | london | OLDER | -510 | +12.9 | +3024 | 0.51 |
| rem_own_k1.25 | nyam | L3M | -650 | +20.0 | +0 | 0.24 |
| rem_own_k1.25 | nyam | L6M | -2127 | -8.9 | +1531 | 0.39 |
| rem_own_k1.25 | nyam | OLDER | -53 | +10.3 | +7327 | 0.47 |
| rem_own_k1.25 | nypm | L3M | -192 | +21.8 | +1203 | 0.45 |
| rem_own_k1.25 | nypm | L6M | -627 | +21.8 | +1203 | 0.50 |
| rem_own_k1.25 | nypm | OLDER | -304 | -2.4 | -831 | 0.50 |

### Item 4 per book x session (all 43 months): trades whose 60-pt target lies beyond the forecast quantile, their fixed-target result, the capped replay, and how far trades run past the cap
| book | session | cap | trades | share beyond | fixed-target hit rate | fixed avg $/trade | capped avg $/trade | avg points run past cap |
|---|---|---|---|---|---|---|---|---|
| A7 | asia | q50_H75 | 1156 | 0.25 | 0.50 | 60 | 87 | 10.4 |
| A7 | asia | q60_H75 | 1156 | 0.13 | 0.47 | 4 | 26 | 8.8 |
| A7 | asia | q75_H75 | 1156 | 0.03 | 0.48 | 19 | 6 | 11.1 |
| A7 | asia | rem_own_k0.75 | 1156 | 0.74 | 0.52 | 126 | 22 | 32.9 |
| H7 | asia | q50_H75 | 700 | 0.33 | 0.49 | 164 | 181 | 11.3 |
| H7 | asia | q60_H75 | 700 | 0.18 | 0.56 | 447 | 414 | 10.7 |
| H7 | asia | q75_H75 | 700 | 0.02 | 0.50 | -318 | -267 | 16.1 |
| H7 | asia | rem_own_k0.75 | 700 | 0.71 | 0.48 | 208 | 55 | 27.8 |
| H7 | nyam | q50_H75 | 348 | 0.49 | 0.46 | 84 | 25 | 8.9 |
| H7 | nyam | q60_H75 | 348 | 0.25 | 0.47 | 96 | 46 | 7.4 |
| H7 | nyam | q75_H75 | 348 | 0.06 | 0.33 | -113 | -12 | 4.7 |
| H7 | nyam | rem_own_k0.75 | 348 | 0.66 | 0.47 | 62 | -35 | 23.3 |
| K7 | asia | q50_H75 | 2596 | 0.32 | 0.44 | 102 | 74 | 9.7 |
| K7 | asia | q60_H75 | 2596 | 0.19 | 0.44 | 111 | 90 | 7.6 |
| K7 | asia | q75_H75 | 2596 | 0.04 | 0.40 | 26 | 1 | 6.1 |
| K7 | asia | rem_own_k0.75 | 2596 | 0.68 | 0.44 | 88 | 0 | 27.2 |
| K7 | london | q50_H75 | 1781 | 0.57 | 0.43 | 62 | 37 | 10.9 |
| K7 | london | q60_H75 | 1781 | 0.33 | 0.44 | 60 | 35 | 9.4 |
| K7 | london | q75_H75 | 1781 | 0.12 | 0.48 | 138 | 101 | 6.5 |
| K7 | london | rem_own_k0.75 | 1781 | 0.69 | 0.43 | 45 | -12 | 27.4 |
| K7 | nyam | q50_H75 | 1565 | 0.57 | 0.42 | 21 | 18 | 10.0 |
| K7 | nyam | q60_H75 | 1565 | 0.32 | 0.40 | -4 | -17 | 9.0 |
| K7 | nyam | q75_H75 | 1565 | 0.07 | 0.41 | 40 | 36 | 16.3 |
| K7 | nyam | rem_own_k0.75 | 1565 | 0.70 | 0.39 | -21 | -38 | 26.0 |
| K7 | nypm | q50_H75 | 1136 | 0.50 | 0.36 | 65 | 54 | 8.1 |
| K7 | nypm | q60_H75 | 1136 | 0.31 | 0.34 | 62 | 48 | 5.6 |
| K7 | nypm | q75_H75 | 1136 | 0.09 | 0.29 | 155 | 179 | 3.5 |
| K7 | nypm | rem_own_k0.75 | 1136 | 0.71 | 0.37 | 72 | -30 | 23.7 |
| M7 | london | q50_H75 | 2489 | 0.42 | 0.43 | 45 | 40 | 10.0 |
| M7 | london | q60_H75 | 2489 | 0.24 | 0.43 | 32 | 26 | 8.2 |
| M7 | london | q75_H75 | 2489 | 0.06 | 0.38 | -74 | -97 | 7.1 |
| M7 | london | rem_own_k0.75 | 2489 | 0.59 | 0.39 | -40 | -29 | 22.9 |
| M7 | nyam | q50_H75 | 1496 | 0.52 | 0.43 | 49 | 22 | 8.6 |
| M7 | nyam | q60_H75 | 1496 | 0.27 | 0.44 | 76 | 57 | 7.2 |
| M7 | nyam | q75_H75 | 1496 | 0.06 | 0.44 | 127 | 131 | 4.9 |
| M7 | nyam | rem_own_k0.75 | 1496 | 0.69 | 0.42 | 30 | -36 | 27.3 |
| O7 | nyam | q50_H75 | 452 | 0.58 | 0.32 | 205 | 91 | 20.5 |
| O7 | nyam | q60_H75 | 452 | 0.37 | 0.31 | 156 | 118 | 16.9 |
| O7 | nyam | q75_H75 | 452 | 0.08 | 0.20 | -192 | -145 | 9.5 |
| O7 | nyam | rem_own_k0.75 | 452 | 0.31 | 0.30 | 120 | 82 | 20.6 |
| P7 | asia | q50_H75 | 2161 | 0.29 | 0.46 | 391 | 341 | 10.2 |
| P7 | asia | q60_H75 | 2161 | 0.16 | 0.48 | 487 | 484 | 9.3 |
| P7 | asia | q75_H75 | 2161 | 0.02 | 0.55 | 1227 | 969 | 5.7 |
| P7 | asia | rem_own_k0.75 | 2161 | 0.70 | 0.44 | 447 | 130 | 26.6 |
| P7 | london | q50_H75 | 1537 | 0.62 | 0.38 | 74 | 27 | 10.0 |
| P7 | london | q60_H75 | 1537 | 0.41 | 0.38 | 67 | 36 | 7.8 |
| P7 | london | q75_H75 | 1537 | 0.15 | 0.41 | 124 | 59 | 5.3 |
| P7 | london | rem_own_k0.75 | 1537 | 0.72 | 0.37 | -19 | -13 | 23.8 |
| P7 | nyam | q50_H75 | 1050 | 0.72 | 0.38 | 38 | 150 | 13.2 |
| P7 | nyam | q60_H75 | 1050 | 0.48 | 0.37 | -7 | 28 | 10.9 |
| P7 | nyam | q75_H75 | 1050 | 0.15 | 0.33 | -88 | -96 | 13.3 |
| P7 | nyam | rem_own_k0.75 | 1050 | 0.71 | 0.37 | -43 | 67 | 33.2 |
| U7 | asia | q50_H75 | 686 | 0.28 | 0.54 | 412 | 320 | 10.4 |
| U7 | asia | q60_H75 | 686 | 0.15 | 0.50 | 322 | 270 | 8.0 |
| U7 | asia | q75_H75 | 686 | 0.03 | 0.47 | -260 | -383 | 6.8 |
| U7 | asia | rem_own_k0.75 | 686 | 0.74 | 0.53 | 375 | 4 | 30.5 |
| U7 | london | q50_H75 | 645 | 0.27 | 0.46 | -102 | -183 | 8.7 |
| U7 | london | q60_H75 | 645 | 0.13 | 0.46 | -173 | -182 | 7.8 |
| U7 | london | q75_H75 | 645 | 0.03 | 0.50 | -396 | -466 | 5.4 |
| U7 | london | rem_own_k0.75 | 645 | 0.68 | 0.51 | 166 | 14 | 24.5 |

### Exact cap cells (global: all books at once; L3M, L6M when promoted; delta vs JN05W2)
| cell | L3M | L6M | HOLD | d mean/wk at $4.84 L3M |
|---|---|---|---|---|
| quantile 50 cap, horizon = 75th-percentile holding time | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | +1452 (lots +9/wk) |
| quantile 60 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 75 cap, horizon = 75th-percentile holding time | +177 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 101%, w2l 0 | n/a | n/a | +176 (lots +0/wk) |
| quantile 90 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 60 cap, horizon = median holding time | -1554 $/wk, DD +2.5%, ww +1445, stops 10.42(10.35), b5 89%, w2l 1 | n/a | n/a | -1658 (lots +29/wk) |
| quantile 75 cap, horizon = median holding time | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=0.5 | -8393 $/wk, DD +2.1%, ww +5889, stops 7.76(10.35), b5 57%, w2l 3 | n/a | n/a | -8805 (lots +113/wk) |
| remaining-range cap, forecast own 20-session mean, k=0.75 | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=1.0 | -6226 $/wk, DD +27.0%, ww +12290, stops 8.98(10.35), b5 66%, w2l 2 | n/a | n/a | -6458 (lots +63/wk) |
| remaining-range cap, forecast own 20-session mean, k=1.25 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.5 | -10795 $/wk, DD +40.3%, ww +11430, stops 7.00(10.35), b5 51%, w2l 4 | n/a | n/a | -11257 (lots +126/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.75 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.0 | -7259 $/wk, DD +39.4%, ww +17319, stops 7.76(10.35), b5 65%, w2l 2 | n/a | n/a | -7570 (lots +85/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.25 | pending | | | |
| EV-best target, bounded by the book target | -14326 $/wk, DD -25.6%, ww -15613, stops 8.45(10.35), b5 46%, w2l 3 | n/a | n/a | -14639 (lots +86/wk) |
| EV-best target, unbounded | pending | | | |
| extension m=1.0 | -110 $/wk, DD -53.4%, ww -2988, stops 11.72(10.35), b5 124%, w2l 2 | n/a | n/a | -18 (lots -25/wk) |
| extension m=1.5 | pending | | | |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts skipped | +1443 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | n/a | n/a | +1410 (lots +9/wk) |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts at half size | pending | | | |
| PLANTED-EDGE CHECK (look-ahead oracle 0.9 x realised MFE, not a result) | +85531 $/wk, DD +67.0%, ww +64263, stops 6.54(10.35), b5 259%, w2l 0 | n/a | n/a | +85219 (lots +85/wk) |
| PLANTED-EDGE CHECK (oracle 0.6 x realised MFE, not a result) | pending | | | |
| PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 | n/a | -125 (lots +1/wk) |
| PLACEBO pl23: quantile 50 cap, horizon = 75th-percentile holding time | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 | n/a | -871 (lots +3/wk) |
| PLACEBO pl37: quantile 50 cap, horizon = 75th-percentile holding time | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 | n/a | -612 (lots +2/wk) |
| PLACEBO plR1: quantile 50 cap, horizon = 75th-percentile holding time | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 | n/a | -670 (lots +4/wk) |

### The one candidate: forecast-quantile-50 cap, horizon = 75th-percentile holding time (L3M mean-only so far): all windows, W44 removed, placebos
| window | scope all | W44 removed |
|---|---|---|
| L3M | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 |
| L6M | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 |
| HOLD | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 |
| MID | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 |
| PREUW | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 |
Placebos (same cap, forecast features taken n sessions earlier at the same clock / a random earlier session), L3M then L6M when run:
| placebo | L3M | L6M |
|---|---|---|
| pl11 | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 |
| pl23 | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 |
| pl37 | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 |
| plR1 | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 |

### Per book x session exact cap cells (clean: one book in one session)
| slice | cap | L3M | May-Jul |
|---|---|---|---|
| A7 asia | quantile 50 cap, horizon = 75th-percentile holding time | -17 (live -30; $4.84 -17) DD +0.0% ww +0 stops 4.03(4.03) | n/a |

### FOR THE LIVE BUILD (what D7 computes at the signal second)
From its own 1-minute bars: last 15/30/60/120-minute range and realised vol, same-offset range over the previous 20 sessions (median), session ranges of the last 5/20 sessions, range so far, the entry position in the session range (favourable-side room), elapsed fraction of the session, ln of the book-session horizon; a small coefficient table per session (15 weights, mean, sd, intercept, four residual quantile offsets) refit every 14 days and shipped as a static file. Cap = min(60, price x exp(prediction + quantile offset) - 2); orders: the target limit is placed at the capped price. The remaining-range version needs the HAR session forecast (T-RANGE2 file) or D7 computes its own 20-session mean. No intraday feed from the box.


## Per book and session, clean, and the assembled stack
**STATUS (plain, not a PASS; B1 in progress, no "nothing passes" verdict is allowed until it is done): single-book single-session cells scored in L3M for 14 of 14 slices; slice picks so far: {}.**

Method (user order PART B, 2026-11-15): each cell = the Dial 10 hook restricted to ONE book in ONE session (every other book/session unchanged at JN05W2), exact engine, all layers ON, live caps. Dollars are BASE lots; the x1.75 live figure sits beside each headline (live); the $4.84 figure reprices every contract at the FEES.md $4.84 RT (engine raw $1.18). Compared on the same book x session slice of JN05W2 (day locks/caps still interact across books, which is why the cells are run for real and not sliced from the global run). B1a settings per slice: direction both / narrow-only / wide-only x gearing 0.5 / 1.0 at the 75th-percentile horizon, plus narrow/wide g1.0 at the median horizon; "fixed" = JN05W2 itself. Walk-forward: the pick for each slice is made on 2026-05..07 only (older than L3M); L3M (2026-08..10) is then out-of-sample. B1b (around each pick): lots cap 1.5/3, lots follow half the change, dead band 0/20%, target ratio 0.8/1.2, lever stop-only (sl: stop W, lots inverse, target in the same points) / target-only (tg) / size-only (sz: bracket fixed, lots follow the forecast), noise floor k = 3/4/5 x recent 5-minute ATR (bracket never narrower), clips 25..120 / 20..150.

### B1 table: per slice, every cell (L3M, delta vs JN05W2 same slice; May-Jul = the selection window)
| slice | setting | May-Jul (selection) | L3M (out of sample) | L6M |
|---|---|---|---|---|
| A7 asia | both/g1.0/H75 | -374 (live -654; $4.84 -370) DD -10.9% ww -261 stops 2.97(3.88) | +47 (live +83; $4.84 +40) DD +25.6% ww +1495 stops 5.55(4.03) | -163 (live -286; $4.84 -165) DD -29.2% ww +1253 stops 4.26(3.96) |
| A7 asia | narrow/g1.0/H75 | -419 (live -733; $4.84 -423) DD -0.6% ww -175 stops 4.49(3.88) | -18 (live -32; $4.84 -26) DD +17.7% ww +722 stops 5.63(4.03) | -219 (live -383; $4.84 -224) DD -19.1% ww +722 stops 5.06(3.96) |
| A7 asia | both/g0.5/H75 | -556 (live -973; $4.84 -553) DD -9.2% ww +72 stops 3.50(3.88) | -192 (live -336; $4.84 -195) DD +10.1% ww +412 stops 5.10(4.03) | -374 (live -654; $4.84 -374) DD -36.6% ww +412 stops 4.30(3.96) |
| A7 asia | narrow/g0.5/H75 | -350 (live -612; $4.84 -352) DD +0.0% ww +0 stops 4.34(3.88) | -186 (live -325; $4.84 -189) DD +10.0% ww +552 stops 5.10(4.03) | -268 (live -469; $4.84 -270) DD -15.8% ww +552 stops 4.72(3.96) |
| A7 asia | wide/g1.0/H75 | +19 (live +33; $4.84 +26) DD -10.9% ww +283 stops 2.51(3.88) | -15 (live -26; $4.84 -14) DD +2.4% ww -426 stops 3.96(4.03) | +2 (live +3; $4.84 +6) DD -13.6% ww -426 stops 3.23(3.96) |
| A7 asia | wide/g0.5/H75 | n/a | -1 (live -1; $4.84 -1) DD +1.4% ww -140 stops 4.03(4.03) | n/a |
| A7 asia | wide/g1.0/H50 | n/a | -48 (live -85; $4.84 -48) DD -3.0% ww -426 stops 3.88(4.03) | n/a |
| A7 asia | narrow/g1.0/H50 | n/a | -159 (live -279; $4.84 -171) DD -8.3% ww +877 stops 5.93(4.03) | n/a |
| H7 asia | wide/g0.5/H75 | n/a | +123 (live +215; $4.84 +123) DD +0.0% ww +0 stops 0.23(0.23) | n/a |
| H7 asia | wide/g1.0/H75 | n/a | -67 (live -118; $4.84 -67) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | wide/g1.0/H50 | n/a | -312 (live -546; $4.84 -312) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | both/g1.0/H75 | +1123 (live +1965; $4.84 +1129) DD +6.5% ww +1483 stops 0.53(0.61) | +177 (live +309; $4.84 +163) DD -33.6% ww -1228 stops 0.61(0.23) | +650 (live +1137; $4.84 +646) DD +6.5% ww +1483 stops 0.57(0.42) |
| H7 asia | narrow/g1.0/H75 | n/a | +244 (live +427; $4.84 +230) DD -33.6% ww -1228 stops 0.53(0.23) | n/a |
| H7 asia | both/g0.5/H75 | n/a | -574 (live -1004; $4.84 -580) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g0.5/H75 | n/a | -697 (live -1219; $4.84 -703) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g1.0/H50 | n/a | -355 (live -621; $4.84 -372) DD -120.5% ww -2166 stops 0.53(0.23) | n/a |
| H7 nyam | narrow/g1.0/H50 | n/a | +252 (live +441; $4.84 +252) DD +60.4% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | both/g1.0/H75 | n/a | +281 (live +491; $4.84 +280) DD +57.7% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | narrow/g1.0/H75 | -187 (live -328; $4.84 -188) DD -4.0% ww +0 stops 0.53(0.46) | +258 (live +452; $4.84 +258) DD +57.7% ww +480 stops 0.30(0.38) | +35 (live +62; $4.84 +35) DD +24.1% ww +480 stops 0.42(0.42) |
| H7 nyam | both/g0.5/H75 | +103 (live +180; $4.84 +103) DD +29.2% ww -83 stops 0.46(0.46) | +87 (live +153; $4.84 +87) DD +2.2% ww +195 stops 0.38(0.38) | +95 (live +167; $4.84 +95) DD +2.2% ww +195 stops 0.42(0.42) |
| H7 nyam | narrow/g0.5/H75 | n/a | +77 (live +134; $4.84 +77) DD +2.2% ww +195 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g0.5/H75 | n/a | +11 (live +19; $4.84 +11) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H75 | n/a | +22 (live +39; $4.84 +22) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H50 | n/a | +30 (live +53; $4.84 +30) DD +0.0% ww +0 stops 0.30(0.38) | n/a |
| K7 asia | wide/g1.0/H75 | n/a | +297 (live +520; $4.84 +298) DD +0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | wide/g0.5/H75 | n/a | -54 (live -94; $4.84 -54) DD -0.7% ww -404 stops 0.00(0.00) | n/a |
| K7 asia | narrow/g0.5/H75 | n/a | +1877 (live +3285; $4.84 +1855) DD -19.6% ww -2412 stops 0.00(0.00) | n/a |
| K7 asia | both/g0.5/H75 | n/a | +1823 (live +3191; $4.84 +1801) DD -28.8% ww -3232 stops 0.00(0.00) | n/a |
| K7 asia | wide/g1.0/H50 | n/a | -401 (live -702; $4.84 -400) DD -35.9% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | both/g1.0/H75 | n/a | +1292 (live +2261; $4.84 +1220) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H75 | n/a | +912 (live +1595; $4.84 +838) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H50 | n/a | +355 (live +621; $4.84 +268) DD -86.2% ww -5644 stops 0.00(0.00) | n/a |
| K7 london | both/g0.5/H75 | n/a | -9 (live -15; $4.84 -14) DD +8.7% ww +4326 stops 0.23(0.30) | n/a |
| K7 london | wide/g0.5/H75 | n/a | +27 (live +48; $4.84 +29) DD +0.5% ww +0 stops 0.30(0.30) | n/a |
| K7 london | wide/g1.0/H50 | n/a | +431 (live +755; $4.84 +433) DD -3.3% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g0.5/H75 | n/a | -123 (live -215; $4.84 -130) DD -4.2% ww +4733 stops 0.23(0.30) | n/a |
| K7 london | wide/g1.0/H75 | n/a | +157 (live +274; $4.84 +160) DD -4.8% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g1.0/H50 | n/a | -182 (live -319; $4.84 -204) DD -13.7% ww +3097 stops 0.23(0.30) | n/a |
| K7 london | both/g1.0/H75 | n/a | +481 (live +841; $4.84 +462) DD -25.5% ww +4257 stops 0.38(0.30) | n/a |
| K7 london | narrow/g1.0/H75 | n/a | -31 (live -55; $4.84 -55) DD -42.3% ww +4122 stops 0.38(0.30) | n/a |
| K7 nyam | narrow/g1.0/H50 | n/a | +769 (live +1345; $4.84 +761) DD +51.0% ww +2185 stops 0.00(0.00) | n/a |
| K7 nyam | both/g1.0/H75 | n/a | +1160 (live +2030; $4.84 +1153) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g1.0/H75 | n/a | +984 (live +1722; $4.84 +977) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g0.5/H75 | n/a | +668 (live +1170; $4.84 +667) DD +40.3% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | both/g0.5/H75 | n/a | +806 (live +1410; $4.84 +805) DD +39.5% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H75 | n/a | +176 (live +308; $4.84 +176) DD -0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H50 | n/a | +252 (live +441; $4.84 +253) DD -0.3% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g0.5/H75 | n/a | +137 (live +241; $4.84 +137) DD -0.8% ww +0 stops 0.00(0.00) | n/a |
| K7 nypm | wide/g1.0/H50 | n/a | +442 (live +773; $4.84 +442) DD +17.3% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | wide/g1.0/H75 | n/a | +70 (live +122; $4.84 +70) DD +13.1% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | both/g1.0/H75 | n/a | -184 (live -322; $4.84 -197) DD +9.8% ww +1145 stops 0.15(0.08) | n/a |
| K7 nypm | wide/g0.5/H75 | n/a | -4 (live -8; $4.84 -4) DD -1.5% ww -38 stops 0.00(0.08) | n/a |
| K7 nypm | narrow/g1.0/H50 | n/a | +48 (live +84; $4.84 +32) DD -1.9% ww +105 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g1.0/H75 | n/a | -254 (live -445; $4.84 -267) DD -3.3% ww +990 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g0.5/H75 | n/a | -266 (live -465; $4.84 -269) DD -26.7% ww +140 stops 0.08(0.08) | n/a |
| K7 nypm | both/g0.5/H75 | n/a | -270 (live -473; $4.84 -274) DD -27.3% ww +102 stops 0.00(0.08) | n/a |
| M7 london | wide/g1.0/H75 | n/a | +1614 (live +2824; $4.84 +1616) DD +4.9% ww +1190 stops 0.53(0.91) | n/a |
| M7 london | wide/g0.5/H75 | n/a | +688 (live +1204; $4.84 +689) DD +4.4% ww +1400 stops 0.84(0.91) | n/a |
| M7 london | wide/g1.0/H50 | n/a | +538 (live +942; $4.84 +540) DD -1.3% ww -80 stops 0.84(0.91) | n/a |
| M7 london | both/g0.5/H75 | n/a | +1147 (live +2008; $4.84 +1139) DD -8.1% ww +130 stops 1.07(0.91) | n/a |
| M7 london | narrow/g0.5/H75 | n/a | +417 (live +730; $4.84 +408) DD -10.9% ww -1075 stops 1.14(0.91) | n/a |
| M7 london | narrow/g1.0/H50 | n/a | +476 (live +833; $4.84 +446) DD -19.9% ww +1144 stops 1.45(0.91) | n/a |
| M7 london | narrow/g1.0/H75 | n/a | -366 (live -640; $4.84 -390) DD -20.4% ww +80 stops 1.29(0.91) | n/a |
| M7 london | both/g1.0/H75 | n/a | +1142 (live +1999; $4.84 +1121) DD -23.2% ww -729 stops 0.91(0.91) | n/a |
| M7 nyam | narrow/g1.0/H50 | n/a | +439 (live +769; $4.84 +424) DD +26.0% ww -222 stops 0.38(0.23) | n/a |
| M7 nyam | both/g0.5/H75 | n/a | +79 (live +138; $4.84 +75) DD +0.8% ww +194 stops 0.30(0.23) | n/a |
| M7 nyam | narrow/g0.5/H75 | n/a | +73 (live +127; $4.84 +69) DD +0.8% ww +194 stops 0.38(0.23) | n/a |
| M7 nyam | wide/g0.5/H75 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H75 | n/a | +16 (live +28; $4.84 +16) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H50 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | both/g1.0/H75 | n/a | +419 (live +733; $4.84 +405) DD -6.8% ww -991 stops 0.46(0.23) | n/a |
| M7 nyam | narrow/g1.0/H75 | n/a | +402 (live +704; $4.84 +388) DD -6.8% ww -991 stops 0.53(0.23) | n/a |
| P7 asia | narrow/g1.0/H50 | n/a | -3918 (live -6857; $4.84 -4186) DD -0.4% ww -4286 stops 0.46(0.15) | n/a |
| P7 asia | both/g0.5/H75 | n/a | -5946 (live -10406; $4.84 -6044) DD -1.0% ww +6944 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g0.5/H75 | n/a | -5762 (live -10084; $4.84 -5860) DD -1.0% ww +9022 stops 0.15(0.15) | n/a |
| P7 asia | wide/g0.5/H75 | n/a | -184 (live -322; $4.84 -183) DD -4.9% ww -2079 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g1.0/H75 | n/a | -2696 (live -4718; $4.84 -2882) DD -7.8% ww -10346 stops 0.53(0.15) | n/a |
| P7 asia | wide/g1.0/H50 | n/a | -816 (live -1428; $4.84 -812) DD -22.6% ww -9033 stops 0.15(0.15) | n/a |
| P7 asia | wide/g1.0/H75 | n/a | -491 (live -858; $4.84 -490) DD -25.2% ww -10331 stops 0.15(0.15) | n/a |
| P7 asia | both/g1.0/H75 | n/a | -3315 (live -5802; $4.84 -3501) DD -36.1% ww -13164 stops 0.53(0.15) | n/a |
| P7 london | both/g0.5/H75 | n/a | +894 (live +1565; $4.84 +886) DD +29.6% ww -1633 stops 0.08(0.08) | n/a |
| P7 london | narrow/g0.5/H75 | n/a | +386 (live +675; $4.84 +375) DD +28.5% ww -1328 stops 0.08(0.08) | n/a |
| P7 london | narrow/g1.0/H50 | n/a | +927 (live +1622; $4.84 +895) DD +19.7% ww -3009 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H75 | n/a | -142 (live -249; $4.84 -138) DD +2.7% ww -458 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H50 | n/a | +265 (live +464; $4.84 +266) DD +1.1% ww +0 stops 0.08(0.08) | n/a |
| P7 london | wide/g0.5/H75 | n/a | +385 (live +674; $4.84 +387) DD -1.9% ww -238 stops 0.08(0.08) | n/a |
| P7 london | both/g1.0/H75 | n/a | +1179 (live +2064; $4.84 +1145) DD -9.8% ww -5408 stops 0.15(0.08) | n/a |
| P7 london | narrow/g1.0/H75 | n/a | +1322 (live +2313; $4.84 +1282) DD -14.4% ww -5203 stops 0.15(0.08) | n/a |
| P7 nyam | both/g1.0/H75 | n/a | +697 (live +1220; $4.84 +685) DD +51.3% ww +354 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g1.0/H75 | n/a | +543 (live +951; $4.84 +529) DD +45.9% ww +324 stops 0.30(0.38) | n/a |
| P7 nyam | both/g0.5/H75 | n/a | +105 (live +184; $4.84 +99) DD +36.7% ww +238 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g0.5/H75 | n/a | -13 (live -23; $4.84 -20) DD +36.4% ww +262 stops 0.30(0.38) | n/a |
| P7 nyam | wide/g0.5/H75 | n/a | +118 (live +207; $4.84 +119) DD +0.3% ww -25 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H75 | n/a | +16 (live +27; $4.84 +17) DD -7.5% ww -105 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H50 | n/a | -544 (live -952; $4.84 -543) DD -47.7% ww -3348 stops 0.38(0.38) | n/a |
| U7 asia | narrow/g1.0/H50 | n/a | +1222 (live +2139; $4.84 +1201) DD +15.6% ww -265 stops 1.90(1.83) | n/a |
| U7 asia | both/g1.0/H75 | n/a | +71 (live +124; $4.84 +56) DD +8.3% ww -1836 stops 1.98(1.83) | n/a |
| U7 asia | narrow/g1.0/H75 | n/a | +502 (live +879; $4.84 +487) DD +8.3% ww +983 stops 1.98(1.83) | n/a |
| U7 asia | both/g0.5/H75 | n/a | -800 (live -1399; $4.84 -808) DD +6.6% ww -2883 stops 2.05(1.83) | n/a |
| U7 asia | narrow/g0.5/H75 | n/a | -162 (live -284; $4.84 -170) DD +6.6% ww +57 stops 2.05(1.83) | n/a |
| U7 asia | wide/g0.5/H75 | n/a | -637 (live -1115; $4.84 -637) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H75 | n/a | -431 (live -755; $4.84 -431) DD +0.0% ww -1836 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H50 | n/a | -648 (live -1134; $4.84 -648) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 london | narrow/g0.5/H75 | n/a | +393 (live +687; $4.84 +392) DD +17.2% ww +1796 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H75 | n/a | +246 (live +431; $4.84 +243) DD +3.1% ww -1185 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H50 | n/a | -41 (live -72; $4.84 -48) DD -9.9% ww -1991 stops 1.52(1.45) | n/a |
| U7 london | both/g0.5/H75 | n/a | -891 (live -1560; $4.84 -890) DD -25.4% ww -3538 stops 1.52(1.45) | n/a |
| U7 london | wide/g1.0/H50 | n/a | -839 (live -1468; $4.84 -837) DD -33.9% ww -4122 stops 1.37(1.45) | n/a |
| U7 london | wide/g0.5/H75 | n/a | -1284 (live -2247; $4.84 -1282) DD -44.3% ww -6280 stops 1.52(1.45) | n/a |
| U7 london | both/g1.0/H75 | n/a | -1728 (live -3025; $4.84 -1729) DD -105.5% ww -7540 stops 1.60(1.45) | n/a |
| U7 london | wide/g1.0/H75 | n/a | -1975 (live -3455; $4.84 -1972) DD -109.8% ww -6355 stops 1.60(1.45) | n/a |

### Summary per slice: pick made on May-Jul, result on L3M
| slice | pick | L3M result of the pick | verdict |
|---|---|---|---|
| A7 asia | pending | | |
| H7 asia | pending | | |
| H7 nyam | pending | | |
| K7 asia | pending | | |
| K7 london | pending | | |
| K7 nyam | pending | | |
| K7 nypm | pending | | |
| M7 london | pending | | |
| M7 nyam | pending | | |
| P7 asia | pending | | |
| P7 london | pending | | |
| P7 nyam | pending | | |
| U7 asia | pending | | |
| U7 london | pending | | |

### B2: why the global version adds full stops (narrow-only/both g1.0 H75 cell, L3M, trade tables)
Reference JN05W2 L3M (no O7): 1855 trades, stop rate 0.071, 132 stops (13 weeks).

**M1_75_g10_c1_d10_c20_tb_B**: 2038 trades (+183 vs JN05W2), stops 173 (+41), stop rate 0.085 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 437 | 0.103 | 3.05 | 94 |
| (40, 50] | 721 | 0.074 | 2.36 | 271 |
| (50, 55] | 232 | 0.099 | 1.97 | 169 |
| (55, 60] | 435 | 0.076 | 1.87 | 76 |
| (60, 70] | 75 | 0.120 | 2.01 | -385 |
| (70, 80] | 62 | 0.048 | 1.68 | -284 |
| (80, 101] | 76 | 0.092 | 1.13 | -591 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1543 | 0.069 | 2.21 | 54 |
| (3.0, 4.0] | 294 | 0.116 | 2.29 | 239 |
| (4.0, 5.0] | 74 | 0.108 | 2.31 | 364 |
| (5.0, 6.0] | 6 | 0.167 | 2.50 | 172 |
| (6.0, 8.0] | 4 | 0.000 | 1.00 | -119 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1068 | 0.096 | 1.00 | 4 |
| (1, 2] | 385 | 0.078 | 2.00 | 115 |
| (2, 3] | 215 | 0.093 | 3.00 | 23 |
| (3, 5] | 195 | 0.062 | 4.46 | 256 |
| (5, 8] | 138 | 0.065 | 6.70 | 690 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

**M1_75_g10_c1_d10_c20_tb_N**: 2072 trades (+217 vs JN05W2), stops 178 (+46), stop rate 0.086 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 449 | 0.105 | 3.02 | 97 |
| (40, 50] | 725 | 0.073 | 2.35 | 272 |
| (50, 55] | 236 | 0.102 | 1.97 | 150 |
| (55, 60] | 662 | 0.082 | 1.82 | -29 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1644 | 0.072 | 2.18 | 50 |
| (3.0, 4.0] | 264 | 0.121 | 2.38 | 348 |
| (4.0, 5.0] | 44 | 0.091 | 3.11 | 1063 |
| (5.0, 6.0] | 3 | 0.000 | 3.33 | 68 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1073 | 0.095 | 1.00 | 8 |
| (1, 2] | 413 | 0.085 | 2.00 | 117 |
| (2, 3] | 197 | 0.081 | 3.00 | 213 |
| (3, 5] | 217 | 0.074 | 4.43 | 196 |
| (5, 8] | 135 | 0.067 | 6.74 | 714 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

Reading of the W/ATR5 table: ATR5 = mean range of the last 14 five-minute buckets in points; a bracket 3x ATR5 or less is within ordinary 5-minute noise. The noise-floor cells (floor 3/4/5 x ATR5, narrowing only) are listed in B3.


### B3: levers (stop-only / target-only / both / size-only) and noise floor, per slice
| slice | cell | L3M | May-Jul |
|---|---|---|---|

### B4: assembled stack (each slice at its own walk-forward pick, run together)
(not run yet: starts when every slice has a pick)


## Target capped at the forecast
**VERDICT (plain, not a PASS; FIRST PASS; 15 of 26 global exact cap cells scored in L3M, per book x session exact cells still running): planted-edge check PASSED through the exact engine (look-ahead oracle target 0.9 x realised MFE: +85531 $/wk, DD +67.0%, ww +64263; this is a mechanism check, NOT a result); the reachable move is only weakly forecastable (R2 on ln MFE 0.03-0.14, quantile calibration good); in the exact L3M cells the cap at the forecast 50th-percentile move (horizon = 75th-percentile holding time) gives +1486 $/wk, DD -0.5%, ww -240 and the 75th-percentile cap +177 $/wk, DD +0.0%, ww +0, the remaining-range caps cut drawdown (own k1.0 -6226 $/wk, DD +27.0%, ww +12290; HAR k1.0 -7259 $/wk, DD +39.4%, ww +17319) but cost thousands per week. Best exact L3M cap cell inside the mean gate by DD: PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time (DD +7.9%, -120 $/wk). L6M/HOLD/older still to run before any verdict.**

Planted-edge check (H1) for the capping mechanism: cells `tcoracle0.9` / `0.6` set the target to 0.9 / 0.6 x the REALISED maximum favourable move (look-ahead, only to prove the mechanism can show an edge through the exact engine); they must come out strongly positive. Status below in the exact table. Until they do, an exact cap verdict is not stated.

Definition. Reachable move = maximum favourable excursion from the signal-second bar close over the book-session holding horizon H (H50/H75 = median / 75th percentile holding time of that book+session, causal), points. Model: walk-forward ridge (14-day blocks, expanding, min 90 days, per session) on ln((MFE+2)/price) from the Dial 10 own-bar inputs (last 15/30/60/120 min range and vol, same-clock normal, own session level, range used so far, elapsed fraction) plus the side-aware room in the session range so far; quantiles q = fitted + empirical training-residual quantile (50/60/75/90). Cap: target = min(book target 60 pts [58 after fills], q-quantile), stop, lots and every other level unchanged. Remaining-range cap: target = min(book target, k x (session range forecast - range printed so far)), forecast = own (price x exp(sf20), mean of the last 20 sessions) or T-RANGE2 HAR (fc_r2_har, available-epoch checked). Small caps (< 30 pts = 0.5 x stop): take / skip / half. EV target: argmax over T in [20, book target or 300] of T x P(MFE>=T) - stop x (1-P) with the lognormal forecast (ignores the stop-first ordering, so optimistic). Extension: if the forecast median MFE is >= m x book target, target = min(q50, 2 x book target). Lots/base basis: dollars are BASE lots (live x1.75 = multiply by 1.75); fee columns $4.84 beside raw $1.18 where shown.

### Item 1: calibration of the forecast quantiles (share of trades whose realized MFE exceeded the forecast quantile; a q-quantile should be exceeded 1-q of the time = 0.50 / 0.40 / 0.25 / 0.10) and R2 of ln MFE, per session
| H | session | window | n | >q50 | >q60 | >q75 | >q90 | R2 ln MFE | median q75 (pts) | share q75 < 60 |
|---|---|---|---|---|---|---|---|---|---|---|
| 50 | asia | older (<2026-05) | 5119 | 0.51 | 0.41 | 0.26 | 0.12 | 0.121 | 80 | 0.222 |
| 50 | asia | L6M | 2006 | 0.49 | 0.38 | 0.23 | 0.08 | 0.058 | 111 | 0.047 |
| 50 | asia | L3M | 875 | 0.46 | 0.34 | 0.20 | 0.07 | -0.014 | 90 | 0.098 |
| 50 | london | older (<2026-05) | 4892 | 0.51 | 0.41 | 0.26 | 0.11 | 0.142 | 62 | 0.438 |
| 50 | london | L6M | 1406 | 0.48 | 0.37 | 0.23 | 0.08 | 0.028 | 76 | 0.166 |
| 50 | london | L3M | 673 | 0.48 | 0.37 | 0.24 | 0.07 | -0.008 | 68 | 0.247 |
| 50 | nyam | older (<2026-05) | 4142 | 0.47 | 0.38 | 0.24 | 0.11 | 0.077 | 63 | 0.397 |
| 50 | nyam | L6M | 600 | 0.51 | 0.40 | 0.24 | 0.09 | 0.097 | 83 | 0.157 |
| 50 | nyam | L3M | 271 | 0.51 | 0.38 | 0.20 | 0.06 | 0.077 | 68 | 0.258 |
| 50 | nypm | older (<2026-05) | 817 | 0.48 | 0.40 | 0.26 | 0.13 | 0.073 | 62 | 0.419 |
| 50 | nypm | L6M | 150 | 0.59 | 0.50 | 0.33 | 0.13 | 0.221 | 71 | 0.307 |
| 50 | nypm | L3M | 56 | 0.50 | 0.36 | 0.21 | 0.09 | 0.104 | 54 | 0.589 |
| 50 | all | older (<2026-05) | 14970 | 0.50 | 0.40 | 0.26 | 0.12 | 0.123 | 68 | 0.352 |
| 50 | all | L6M | 4162 | 0.49 | 0.38 | 0.23 | 0.08 | 0.080 | 91 | 0.113 |
| 50 | all | L3M | 1875 | 0.47 | 0.36 | 0.21 | 0.07 | 0.014 | 76 | 0.189 |
| 75 | asia | older (<2026-05) | 5119 | 0.52 | 0.41 | 0.26 | 0.12 | 0.134 | 122 | 0.032 |
| 75 | asia | L6M | 2006 | 0.50 | 0.40 | 0.24 | 0.08 | 0.027 | 178 | 0.000 |
| 75 | asia | L3M | 875 | 0.45 | 0.35 | 0.20 | 0.05 | -0.016 | 156 | 0.000 |
| 75 | london | older (<2026-05) | 4891 | 0.51 | 0.42 | 0.27 | 0.11 | 0.157 | 101 | 0.100 |
| 75 | london | L6M | 1406 | 0.49 | 0.37 | 0.21 | 0.08 | 0.069 | 118 | 0.001 |
| 75 | london | L3M | 673 | 0.49 | 0.38 | 0.21 | 0.09 | 0.025 | 108 | 0.000 |
| 75 | nyam | older (<2026-05) | 4142 | 0.48 | 0.38 | 0.23 | 0.10 | 0.065 | 91 | 0.081 |
| 75 | nyam | L6M | 600 | 0.50 | 0.40 | 0.24 | 0.10 | 0.098 | 125 | 0.015 |
| 75 | nyam | L3M | 271 | 0.44 | 0.34 | 0.19 | 0.05 | 0.051 | 103 | 0.015 |
| 75 | nypm | older (<2026-05) | 812 | 0.49 | 0.37 | 0.26 | 0.11 | 0.043 | 87 | 0.095 |
| 75 | nypm | L6M | 150 | 0.53 | 0.46 | 0.34 | 0.17 | 0.179 | 117 | 0.013 |
| 75 | nypm | L3M | 56 | 0.41 | 0.30 | 0.21 | 0.07 | -0.076 | 93 | 0.036 |
| 75 | all | older (<2026-05) | 14964 | 0.51 | 0.40 | 0.25 | 0.11 | 0.131 | 102 | 0.071 |
| 75 | all | L6M | 4162 | 0.50 | 0.39 | 0.23 | 0.09 | 0.079 | 149 | 0.003 |
| 75 | all | L3M | 1875 | 0.46 | 0.36 | 0.20 | 0.06 | 0.032 | 128 | 0.003 |

### Items 3 and 4 (and 2): offline replay of the caps on the JN05W2 trade paths, all 43 months (estimate: 1-min paths, cap counted only before the exit bar, so cut/stop ordering is conservative; the exact cells below decide). d mean $/wk and DD cut % vs JN05W2 on the same trades, scope all, then per session for the cap with the most trades capped
| cap | small-cap rule | scope | window | d mean $/wk (live x1.75) | DD cut % | d worst week | d stops/wk | share capped | share where cap hit |
|---|---|---|---|---|---|---|---|---|---|
| q50_H50 | take | all | L3M | +409 (+715) | -3.9 | -1411 | +0.00 | 0.82 | 0.45 |
| q50_H50 | take | all | L6M | -96 (-169) | -3.9 | -1411 | +0.00 | 0.62 | 0.33 |
| q50_H50 | take | all | OLDER | -1795 (-3141) | +12.0 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | skip | all | L3M | -1581 (-2767) | -5.0 | -1996 | +0.00 | 0.82 | 0.45 |
| q50_H50 | skip | all | L6M | -1445 (-2528) | -5.0 | -1996 | +0.00 | 0.62 | 0.33 |
| q50_H50 | skip | all | OLDER | -2271 (-3975) | +17.4 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | half | all | L3M | -586 (-1026) | -4.4 | -1704 | +0.00 | 0.82 | 0.45 |
| q50_H50 | half | all | L6M | -771 (-1348) | -4.4 | -1704 | +0.00 | 0.62 | 0.33 |
| q50_H50 | half | all | OLDER | -2033 (-3558) | +16.5 | +13127 | +0.00 | 0.80 | 0.45 |
| q60_H50 | take | all | L3M | -1525 (-2668) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | take | all | L6M | -839 (-1469) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | take | all | OLDER | -1296 (-2267) | +12.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | skip | all | L3M | -3272 (-5726) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | skip | all | L6M | -1811 (-3170) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | skip | all | OLDER | -1648 (-2885) | +8.8 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | half | all | L3M | -2398 (-4197) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | half | all | L6M | -1325 (-2319) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | half | all | OLDER | -1472 (-2576) | +10.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q75_H50 | take | all | L3M | +414 (+725) | -0.4 | -214 | +0.00 | 0.21 | 0.11 |
| q75_H50 | take | all | L6M | -44 (-77) | -0.4 | -214 | +0.00 | 0.13 | 0.06 |
| q75_H50 | take | all | OLDER | -719 (-1258) | -1.1 | +13801 | +0.00 | 0.37 | 0.18 |
| q90_H50 | take | all | L3M | +191 (+334) | +0.0 | +0 | +0.00 | 0.02 | 0.01 |
| q90_H50 | take | all | L6M | +142 (+249) | +0.0 | +0 | +0.00 | 0.01 | 0.01 |
| q90_H50 | take | all | OLDER | -169 (-296) | -1.8 | +1686 | +0.00 | 0.08 | 0.03 |
| q50_H75 | take | all | L3M | +128 (+225) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | take | all | L6M | +624 (+1092) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | take | all | OLDER | -931 (-1628) | -13.1 | +11346 | +0.00 | 0.51 | 0.26 |
| q50_H75 | skip | all | L3M | +178 (+312) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | skip | all | L6M | +685 (+1198) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | skip | all | OLDER | -1302 (-2279) | -4.6 | +14384 | +0.00 | 0.51 | 0.26 |
| q50_H75 | half | all | L3M | +153 (+268) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | half | all | L6M | +654 (+1145) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | half | all | OLDER | -1116 (-1954) | -8.8 | +12865 | +0.00 | 0.51 | 0.26 |
| q60_H75 | take | all | L3M | +830 (+1452) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | take | all | L6M | +379 (+664) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | take | all | OLDER | -478 (-836) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | skip | all | L3M | +958 (+1677) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | skip | all | L6M | +421 (+737) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | skip | all | OLDER | -402 (-703) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | half | all | L3M | +894 (+1564) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | half | all | L6M | +400 (+700) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | half | all | OLDER | -440 (-769) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q75_H75 | take | all | L3M | +236 (+413) | +0.0 | +0 | +0.00 | 0.01 | 0.00 |
| q75_H75 | take | all | L6M | +105 (+185) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q75_H75 | take | all | OLDER | -255 (-446) | -1.9 | +1485 | +0.00 | 0.08 | 0.04 |
| q90_H75 | take | all | L3M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | L6M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | OLDER | +10 (+18) | -0.4 | +0 | +0.00 | 0.01 | 0.00 |
| rem_own_k0.5 | take | all | L3M | -6674 (-11680) | +8.8 | -1861 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | take | all | L6M | -13204 (-23108) | +8.7 | -1861 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | take | all | OLDER | -7381 (-12916) | -40.2 | +20529 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | skip | all | L3M | -5271 (-9225) | +21.7 | +2982 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | skip | all | L6M | -10625 (-18594) | +21.7 | +2982 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | skip | all | OLDER | -6272 (-10977) | +17.3 | +21712 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | half | all | L3M | -5973 (-10452) | +16.3 | +560 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | half | all | L6M | -11915 (-20851) | +16.3 | +560 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | half | all | OLDER | -6827 (-11946) | +0.6 | +23150 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.75 | take | all | L3M | -7140 (-12494) | +9.6 | +3294 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | take | all | L6M | -10636 (-18614) | +9.6 | +3294 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | take | all | OLDER | -5846 (-10230) | -24.0 | +12208 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | skip | all | L3M | -3661 (-6406) | +10.3 | +4045 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | skip | all | L6M | -6650 (-11638) | +10.3 | +4045 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | skip | all | OLDER | -3856 (-6749) | +16.1 | +19073 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | half | all | L3M | -5400 (-9450) | +13.0 | +3670 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | half | all | L6M | -8643 (-15126) | +13.0 | +3670 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | half | all | OLDER | -4851 (-8489) | +13.0 | +20157 | +0.00 | 0.73 | 0.53 |
| rem_own_k1.0 | take | all | L3M | -5516 (-9653) | +18.3 | +9104 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | take | all | L6M | -8765 (-15339) | +18.3 | +9104 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | take | all | OLDER | -5714 (-9999) | -58.2 | +11926 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | skip | all | L3M | -3265 (-5714) | +15.0 | +8858 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | skip | all | L6M | -5683 (-9944) | +15.0 | +8858 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | skip | all | OLDER | -3872 (-6775) | -61.0 | +20250 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | half | all | L3M | -4391 (-7683) | +18.5 | +8981 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | half | all | L6M | -7224 (-12642) | +18.5 | +8981 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | half | all | OLDER | -4793 (-8387) | -58.0 | +21393 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.25 | take | all | L3M | -3112 (-5446) | +24.4 | +13750 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | take | all | L6M | -8275 (-14481) | +24.4 | +13750 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | take | all | OLDER | -5400 (-9450) | -15.5 | +4336 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | skip | all | L3M | -456 (-797) | +22.4 | +13720 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | skip | all | L6M | -4232 (-7405) | +22.4 | +13720 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | skip | all | OLDER | -3310 (-5792) | -36.4 | +22803 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | half | all | L3M | -1784 (-3121) | +25.2 | +15286 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | half | all | L6M | -6253 (-10943) | +25.2 | +15286 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | half | all | OLDER | -4355 (-7621) | -18.3 | +15544 | +0.00 | 0.54 | 0.41 |

Per session, q60 H75 take-anyway and remaining-range k=1.25 (own):
| cap | session | window | d mean $/wk | DD cut % | d worst week | share capped |
|---|---|---|---|---|---|---|
| q60_H75 | asia | L3M | +221 | +0.0 | +0 | 0.02 |
| q60_H75 | asia | L6M | +110 | +0.0 | +0 | 0.01 |
| q60_H75 | asia | OLDER | -124 | -0.0 | +0 | 0.23 |
| q60_H75 | london | L3M | +745 | +3.8 | +0 | 0.16 |
| q60_H75 | london | L6M | +330 | +3.8 | +0 | 0.12 |
| q60_H75 | london | OLDER | -294 | -2.1 | +0 | 0.35 |
| q60_H75 | nyam | L3M | +61 | -7.2 | +0 | 0.15 |
| q60_H75 | nyam | L6M | -14 | +0.0 | +0 | 0.10 |
| q60_H75 | nyam | OLDER | -37 | -6.0 | +1403 | 0.37 |
| q60_H75 | nypm | L3M | -197 | -0.0 | +0 | 0.41 |
| q60_H75 | nypm | L6M | -47 | +0.0 | +0 | 0.20 |
| q60_H75 | nypm | OLDER | -22 | -5.4 | +0 | 0.33 |
| rem_own_k1.25 | asia | L3M | -4547 | +35.2 | +434 | 0.37 |
| rem_own_k1.25 | asia | L6M | -6717 | +27.1 | +434 | 0.38 |
| rem_own_k1.25 | asia | OLDER | -4532 | -27.4 | +10774 | 0.62 |
| rem_own_k1.25 | london | L3M | +2278 | +46.3 | +12347 | 0.24 |
| rem_own_k1.25 | london | L6M | +1196 | +46.3 | +12347 | 0.30 |
| rem_own_k1.25 | london | OLDER | -510 | +12.9 | +3024 | 0.51 |
| rem_own_k1.25 | nyam | L3M | -650 | +20.0 | +0 | 0.24 |
| rem_own_k1.25 | nyam | L6M | -2127 | -8.9 | +1531 | 0.39 |
| rem_own_k1.25 | nyam | OLDER | -53 | +10.3 | +7327 | 0.47 |
| rem_own_k1.25 | nypm | L3M | -192 | +21.8 | +1203 | 0.45 |
| rem_own_k1.25 | nypm | L6M | -627 | +21.8 | +1203 | 0.50 |
| rem_own_k1.25 | nypm | OLDER | -304 | -2.4 | -831 | 0.50 |

### Item 4 per book x session (all 43 months): trades whose 60-pt target lies beyond the forecast quantile, their fixed-target result, the capped replay, and how far trades run past the cap
| book | session | cap | trades | share beyond | fixed-target hit rate | fixed avg $/trade | capped avg $/trade | avg points run past cap |
|---|---|---|---|---|---|---|---|---|
| A7 | asia | q50_H75 | 1156 | 0.25 | 0.50 | 60 | 87 | 10.4 |
| A7 | asia | q60_H75 | 1156 | 0.13 | 0.47 | 4 | 26 | 8.8 |
| A7 | asia | q75_H75 | 1156 | 0.03 | 0.48 | 19 | 6 | 11.1 |
| A7 | asia | rem_own_k0.75 | 1156 | 0.74 | 0.52 | 126 | 22 | 32.9 |
| H7 | asia | q50_H75 | 700 | 0.33 | 0.49 | 164 | 181 | 11.3 |
| H7 | asia | q60_H75 | 700 | 0.18 | 0.56 | 447 | 414 | 10.7 |
| H7 | asia | q75_H75 | 700 | 0.02 | 0.50 | -318 | -267 | 16.1 |
| H7 | asia | rem_own_k0.75 | 700 | 0.71 | 0.48 | 208 | 55 | 27.8 |
| H7 | nyam | q50_H75 | 348 | 0.49 | 0.46 | 84 | 25 | 8.9 |
| H7 | nyam | q60_H75 | 348 | 0.25 | 0.47 | 96 | 46 | 7.4 |
| H7 | nyam | q75_H75 | 348 | 0.06 | 0.33 | -113 | -12 | 4.7 |
| H7 | nyam | rem_own_k0.75 | 348 | 0.66 | 0.47 | 62 | -35 | 23.3 |
| K7 | asia | q50_H75 | 2596 | 0.32 | 0.44 | 102 | 74 | 9.7 |
| K7 | asia | q60_H75 | 2596 | 0.19 | 0.44 | 111 | 90 | 7.6 |
| K7 | asia | q75_H75 | 2596 | 0.04 | 0.40 | 26 | 1 | 6.1 |
| K7 | asia | rem_own_k0.75 | 2596 | 0.68 | 0.44 | 88 | 0 | 27.2 |
| K7 | london | q50_H75 | 1781 | 0.57 | 0.43 | 62 | 37 | 10.9 |
| K7 | london | q60_H75 | 1781 | 0.33 | 0.44 | 60 | 35 | 9.4 |
| K7 | london | q75_H75 | 1781 | 0.12 | 0.48 | 138 | 101 | 6.5 |
| K7 | london | rem_own_k0.75 | 1781 | 0.69 | 0.43 | 45 | -12 | 27.4 |
| K7 | nyam | q50_H75 | 1565 | 0.57 | 0.42 | 21 | 18 | 10.0 |
| K7 | nyam | q60_H75 | 1565 | 0.32 | 0.40 | -4 | -17 | 9.0 |
| K7 | nyam | q75_H75 | 1565 | 0.07 | 0.41 | 40 | 36 | 16.3 |
| K7 | nyam | rem_own_k0.75 | 1565 | 0.70 | 0.39 | -21 | -38 | 26.0 |
| K7 | nypm | q50_H75 | 1136 | 0.50 | 0.36 | 65 | 54 | 8.1 |
| K7 | nypm | q60_H75 | 1136 | 0.31 | 0.34 | 62 | 48 | 5.6 |
| K7 | nypm | q75_H75 | 1136 | 0.09 | 0.29 | 155 | 179 | 3.5 |
| K7 | nypm | rem_own_k0.75 | 1136 | 0.71 | 0.37 | 72 | -30 | 23.7 |
| M7 | london | q50_H75 | 2489 | 0.42 | 0.43 | 45 | 40 | 10.0 |
| M7 | london | q60_H75 | 2489 | 0.24 | 0.43 | 32 | 26 | 8.2 |
| M7 | london | q75_H75 | 2489 | 0.06 | 0.38 | -74 | -97 | 7.1 |
| M7 | london | rem_own_k0.75 | 2489 | 0.59 | 0.39 | -40 | -29 | 22.9 |
| M7 | nyam | q50_H75 | 1496 | 0.52 | 0.43 | 49 | 22 | 8.6 |
| M7 | nyam | q60_H75 | 1496 | 0.27 | 0.44 | 76 | 57 | 7.2 |
| M7 | nyam | q75_H75 | 1496 | 0.06 | 0.44 | 127 | 131 | 4.9 |
| M7 | nyam | rem_own_k0.75 | 1496 | 0.69 | 0.42 | 30 | -36 | 27.3 |
| O7 | nyam | q50_H75 | 452 | 0.58 | 0.32 | 205 | 91 | 20.5 |
| O7 | nyam | q60_H75 | 452 | 0.37 | 0.31 | 156 | 118 | 16.9 |
| O7 | nyam | q75_H75 | 452 | 0.08 | 0.20 | -192 | -145 | 9.5 |
| O7 | nyam | rem_own_k0.75 | 452 | 0.31 | 0.30 | 120 | 82 | 20.6 |
| P7 | asia | q50_H75 | 2161 | 0.29 | 0.46 | 391 | 341 | 10.2 |
| P7 | asia | q60_H75 | 2161 | 0.16 | 0.48 | 487 | 484 | 9.3 |
| P7 | asia | q75_H75 | 2161 | 0.02 | 0.55 | 1227 | 969 | 5.7 |
| P7 | asia | rem_own_k0.75 | 2161 | 0.70 | 0.44 | 447 | 130 | 26.6 |
| P7 | london | q50_H75 | 1537 | 0.62 | 0.38 | 74 | 27 | 10.0 |
| P7 | london | q60_H75 | 1537 | 0.41 | 0.38 | 67 | 36 | 7.8 |
| P7 | london | q75_H75 | 1537 | 0.15 | 0.41 | 124 | 59 | 5.3 |
| P7 | london | rem_own_k0.75 | 1537 | 0.72 | 0.37 | -19 | -13 | 23.8 |
| P7 | nyam | q50_H75 | 1050 | 0.72 | 0.38 | 38 | 150 | 13.2 |
| P7 | nyam | q60_H75 | 1050 | 0.48 | 0.37 | -7 | 28 | 10.9 |
| P7 | nyam | q75_H75 | 1050 | 0.15 | 0.33 | -88 | -96 | 13.3 |
| P7 | nyam | rem_own_k0.75 | 1050 | 0.71 | 0.37 | -43 | 67 | 33.2 |
| U7 | asia | q50_H75 | 686 | 0.28 | 0.54 | 412 | 320 | 10.4 |
| U7 | asia | q60_H75 | 686 | 0.15 | 0.50 | 322 | 270 | 8.0 |
| U7 | asia | q75_H75 | 686 | 0.03 | 0.47 | -260 | -383 | 6.8 |
| U7 | asia | rem_own_k0.75 | 686 | 0.74 | 0.53 | 375 | 4 | 30.5 |
| U7 | london | q50_H75 | 645 | 0.27 | 0.46 | -102 | -183 | 8.7 |
| U7 | london | q60_H75 | 645 | 0.13 | 0.46 | -173 | -182 | 7.8 |
| U7 | london | q75_H75 | 645 | 0.03 | 0.50 | -396 | -466 | 5.4 |
| U7 | london | rem_own_k0.75 | 645 | 0.68 | 0.51 | 166 | 14 | 24.5 |

### Exact cap cells (global: all books at once; L3M, L6M when promoted; delta vs JN05W2)
| cell | L3M | L6M | HOLD | d mean/wk at $4.84 L3M |
|---|---|---|---|---|
| quantile 50 cap, horizon = 75th-percentile holding time | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | +1452 (lots +9/wk) |
| quantile 60 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 75 cap, horizon = 75th-percentile holding time | +177 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 101%, w2l 0 | n/a | n/a | +176 (lots +0/wk) |
| quantile 90 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 60 cap, horizon = median holding time | -1554 $/wk, DD +2.5%, ww +1445, stops 10.42(10.35), b5 89%, w2l 1 | n/a | n/a | -1658 (lots +29/wk) |
| quantile 75 cap, horizon = median holding time | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=0.5 | -8393 $/wk, DD +2.1%, ww +5889, stops 7.76(10.35), b5 57%, w2l 3 | n/a | n/a | -8805 (lots +113/wk) |
| remaining-range cap, forecast own 20-session mean, k=0.75 | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=1.0 | -6226 $/wk, DD +27.0%, ww +12290, stops 8.98(10.35), b5 66%, w2l 2 | n/a | n/a | -6458 (lots +63/wk) |
| remaining-range cap, forecast own 20-session mean, k=1.25 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.5 | -10795 $/wk, DD +40.3%, ww +11430, stops 7.00(10.35), b5 51%, w2l 4 | n/a | n/a | -11257 (lots +126/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.75 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.0 | -7259 $/wk, DD +39.4%, ww +17319, stops 7.76(10.35), b5 65%, w2l 2 | n/a | n/a | -7570 (lots +85/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.25 | pending | | | |
| EV-best target, bounded by the book target | -14326 $/wk, DD -25.6%, ww -15613, stops 8.45(10.35), b5 46%, w2l 3 | n/a | n/a | -14639 (lots +86/wk) |
| EV-best target, unbounded | pending | | | |
| extension m=1.0 | -110 $/wk, DD -53.4%, ww -2988, stops 11.72(10.35), b5 124%, w2l 2 | n/a | n/a | -18 (lots -25/wk) |
| extension m=1.5 | pending | | | |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts skipped | +1443 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | n/a | n/a | +1410 (lots +9/wk) |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts at half size | pending | | | |
| PLANTED-EDGE CHECK (look-ahead oracle 0.9 x realised MFE, not a result) | +85531 $/wk, DD +67.0%, ww +64263, stops 6.54(10.35), b5 259%, w2l 0 | n/a | n/a | +85219 (lots +85/wk) |
| PLANTED-EDGE CHECK (oracle 0.6 x realised MFE, not a result) | pending | | | |
| PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 | n/a | -125 (lots +1/wk) |
| PLACEBO pl23: quantile 50 cap, horizon = 75th-percentile holding time | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 | n/a | -871 (lots +3/wk) |
| PLACEBO pl37: quantile 50 cap, horizon = 75th-percentile holding time | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 | n/a | -612 (lots +2/wk) |
| PLACEBO plR1: quantile 50 cap, horizon = 75th-percentile holding time | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 | n/a | -670 (lots +4/wk) |

### The one candidate: forecast-quantile-50 cap, horizon = 75th-percentile holding time (L3M mean-only so far): all windows, W44 removed, placebos
| window | scope all | W44 removed |
|---|---|---|
| L3M | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 |
| L6M | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 |
| HOLD | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 |
| MID | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 |
| PREUW | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 |
Placebos (same cap, forecast features taken n sessions earlier at the same clock / a random earlier session), L3M then L6M when run:
| placebo | L3M | L6M |
|---|---|---|
| pl11 | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 |
| pl23 | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 |
| pl37 | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 |
| plR1 | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 |

### Per book x session exact cap cells (clean: one book in one session)
| slice | cap | L3M | May-Jul |
|---|---|---|---|
| A7 asia | quantile 50 cap, horizon = 75th-percentile holding time | -17 (live -30; $4.84 -17) DD +0.0% ww +0 stops 4.03(4.03) | n/a |

### FOR THE LIVE BUILD (what D7 computes at the signal second)
From its own 1-minute bars: last 15/30/60/120-minute range and realised vol, same-offset range over the previous 20 sessions (median), session ranges of the last 5/20 sessions, range so far, the entry position in the session range (favourable-side room), elapsed fraction of the session, ln of the book-session horizon; a small coefficient table per session (15 weights, mean, sd, intercept, four residual quantile offsets) refit every 14 days and shipped as a static file. Cap = min(60, price x exp(prediction + quantile offset) - 2); orders: the target limit is placed at the capped price. The remaining-range version needs the HAR session forecast (T-RANGE2 file) or D7 computes its own 20-session mean. No intraday feed from the box.


## Per book and session, clean, and the assembled stack
**STATUS (plain, not a PASS; B1 in progress, no "nothing passes" verdict is allowed until it is done): single-book single-session cells scored in L3M for 15 of 14 slices; slice picks so far: {}.**

Method (user order PART B, 2026-11-15): each cell = the Dial 10 hook restricted to ONE book in ONE session (every other book/session unchanged at JN05W2), exact engine, all layers ON, live caps. Dollars are BASE lots; the x1.75 live figure sits beside each headline (live); the $4.84 figure reprices every contract at the FEES.md $4.84 RT (engine raw $1.18). Compared on the same book x session slice of JN05W2 (day locks/caps still interact across books, which is why the cells are run for real and not sliced from the global run). B1a settings per slice: direction both / narrow-only / wide-only x gearing 0.5 / 1.0 at the 75th-percentile horizon, plus narrow/wide g1.0 at the median horizon; "fixed" = JN05W2 itself. Walk-forward: the pick for each slice is made on 2026-05..07 only (older than L3M); L3M (2026-08..10) is then out-of-sample. B1b (around each pick): lots cap 1.5/3, lots follow half the change, dead band 0/20%, target ratio 0.8/1.2, lever stop-only (sl: stop W, lots inverse, target in the same points) / target-only (tg) / size-only (sz: bracket fixed, lots follow the forecast), noise floor k = 3/4/5 x recent 5-minute ATR (bracket never narrower), clips 25..120 / 20..150.

### B1 table: per slice, every cell (L3M, delta vs JN05W2 same slice; May-Jul = the selection window)
| slice | setting | May-Jul (selection) | L3M (out of sample) | L6M |
|---|---|---|---|---|
| A7 asia | both/g1.0/H75 | -374 (live -654; $4.84 -370) DD -10.9% ww -261 stops 2.97(3.88) | +47 (live +83; $4.84 +40) DD +25.6% ww +1495 stops 5.55(4.03) | -163 (live -286; $4.84 -165) DD -29.2% ww +1253 stops 4.26(3.96) |
| A7 asia | narrow/g1.0/H75 | -419 (live -733; $4.84 -423) DD -0.6% ww -175 stops 4.49(3.88) | -18 (live -32; $4.84 -26) DD +17.7% ww +722 stops 5.63(4.03) | -219 (live -383; $4.84 -224) DD -19.1% ww +722 stops 5.06(3.96) |
| A7 asia | both/g0.5/H75 | -556 (live -973; $4.84 -553) DD -9.2% ww +72 stops 3.50(3.88) | -192 (live -336; $4.84 -195) DD +10.1% ww +412 stops 5.10(4.03) | -374 (live -654; $4.84 -374) DD -36.6% ww +412 stops 4.30(3.96) |
| A7 asia | narrow/g0.5/H75 | -350 (live -612; $4.84 -352) DD +0.0% ww +0 stops 4.34(3.88) | -186 (live -325; $4.84 -189) DD +10.0% ww +552 stops 5.10(4.03) | -268 (live -469; $4.84 -270) DD -15.8% ww +552 stops 4.72(3.96) |
| A7 asia | wide/g1.0/H75 | +19 (live +33; $4.84 +26) DD -10.9% ww +283 stops 2.51(3.88) | -15 (live -26; $4.84 -14) DD +2.4% ww -426 stops 3.96(4.03) | +2 (live +3; $4.84 +6) DD -13.6% ww -426 stops 3.23(3.96) |
| A7 asia | wide/g0.5/H75 | n/a | -1 (live -1; $4.84 -1) DD +1.4% ww -140 stops 4.03(4.03) | n/a |
| A7 asia | wide/g1.0/H50 | n/a | -48 (live -85; $4.84 -48) DD -3.0% ww -426 stops 3.88(4.03) | n/a |
| A7 asia | narrow/g1.0/H50 | n/a | -159 (live -279; $4.84 -171) DD -8.3% ww +877 stops 5.93(4.03) | n/a |
| H7 asia | wide/g0.5/H75 | n/a | +123 (live +215; $4.84 +123) DD +0.0% ww +0 stops 0.23(0.23) | n/a |
| H7 asia | wide/g1.0/H75 | n/a | -67 (live -118; $4.84 -67) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | wide/g1.0/H50 | n/a | -312 (live -546; $4.84 -312) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | both/g1.0/H75 | +1123 (live +1965; $4.84 +1129) DD +6.5% ww +1483 stops 0.53(0.61) | +177 (live +309; $4.84 +163) DD -33.6% ww -1228 stops 0.61(0.23) | +650 (live +1137; $4.84 +646) DD +6.5% ww +1483 stops 0.57(0.42) |
| H7 asia | narrow/g1.0/H75 | n/a | +244 (live +427; $4.84 +230) DD -33.6% ww -1228 stops 0.53(0.23) | n/a |
| H7 asia | both/g0.5/H75 | n/a | -574 (live -1004; $4.84 -580) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g0.5/H75 | n/a | -697 (live -1219; $4.84 -703) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g1.0/H50 | n/a | -355 (live -621; $4.84 -372) DD -120.5% ww -2166 stops 0.53(0.23) | n/a |
| H7 nyam | narrow/g1.0/H50 | n/a | +252 (live +441; $4.84 +252) DD +60.4% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | both/g1.0/H75 | n/a | +281 (live +491; $4.84 +280) DD +57.7% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | narrow/g1.0/H75 | -187 (live -328; $4.84 -188) DD -4.0% ww +0 stops 0.53(0.46) | +258 (live +452; $4.84 +258) DD +57.7% ww +480 stops 0.30(0.38) | +35 (live +62; $4.84 +35) DD +24.1% ww +480 stops 0.42(0.42) |
| H7 nyam | both/g0.0/H50 | -58 (live -102; $4.84 -58) DD +9.4% ww +0 stops 0.46(0.46) | +221 (live +387; $4.84 +221) DD +54.7% ww +195 stops 0.15(0.38) | +82 (live +143; $4.84 +81) DD +33.9% ww +195 stops 0.30(0.42) |
| H7 nyam | both/g0.5/H75 | +103 (live +180; $4.84 +103) DD +29.2% ww -83 stops 0.46(0.46) | +87 (live +153; $4.84 +87) DD +2.2% ww +195 stops 0.38(0.38) | +95 (live +167; $4.84 +95) DD +2.2% ww +195 stops 0.42(0.42) |
| H7 nyam | narrow/g0.5/H75 | n/a | +77 (live +134; $4.84 +77) DD +2.2% ww +195 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g0.5/H75 | n/a | +11 (live +19; $4.84 +11) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H75 | n/a | +22 (live +39; $4.84 +22) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H50 | n/a | +30 (live +53; $4.84 +30) DD +0.0% ww +0 stops 0.30(0.38) | n/a |
| K7 asia | wide/g1.0/H75 | n/a | +297 (live +520; $4.84 +298) DD +0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | wide/g0.5/H75 | n/a | -54 (live -94; $4.84 -54) DD -0.7% ww -404 stops 0.00(0.00) | n/a |
| K7 asia | narrow/g0.5/H75 | n/a | +1877 (live +3285; $4.84 +1855) DD -19.6% ww -2412 stops 0.00(0.00) | n/a |
| K7 asia | both/g0.5/H75 | n/a | +1823 (live +3191; $4.84 +1801) DD -28.8% ww -3232 stops 0.00(0.00) | n/a |
| K7 asia | wide/g1.0/H50 | n/a | -401 (live -702; $4.84 -400) DD -35.9% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | both/g1.0/H75 | n/a | +1292 (live +2261; $4.84 +1220) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H75 | n/a | +912 (live +1595; $4.84 +838) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H50 | n/a | +355 (live +621; $4.84 +268) DD -86.2% ww -5644 stops 0.00(0.00) | n/a |
| K7 london | both/g0.5/H75 | n/a | -9 (live -15; $4.84 -14) DD +8.7% ww +4326 stops 0.23(0.30) | n/a |
| K7 london | wide/g0.5/H75 | n/a | +27 (live +48; $4.84 +29) DD +0.5% ww +0 stops 0.30(0.30) | n/a |
| K7 london | wide/g1.0/H50 | n/a | +431 (live +755; $4.84 +433) DD -3.3% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g0.5/H75 | n/a | -123 (live -215; $4.84 -130) DD -4.2% ww +4733 stops 0.23(0.30) | n/a |
| K7 london | wide/g1.0/H75 | n/a | +157 (live +274; $4.84 +160) DD -4.8% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g1.0/H50 | n/a | -182 (live -319; $4.84 -204) DD -13.7% ww +3097 stops 0.23(0.30) | n/a |
| K7 london | both/g1.0/H75 | n/a | +481 (live +841; $4.84 +462) DD -25.5% ww +4257 stops 0.38(0.30) | n/a |
| K7 london | narrow/g1.0/H75 | n/a | -31 (live -55; $4.84 -55) DD -42.3% ww +4122 stops 0.38(0.30) | n/a |
| K7 nyam | both/g0.0/H50 | -488 (live -855; $4.84 -488) DD -38.7% ww -514 stops 0.08(0.08) | +1078 (live +1886; $4.84 +1069) DD +53.9% ww +1605 stops 0.00(0.00) | +295 (live +516; $4.84 +290) DD +50.6% ww +1605 stops 0.04(0.04) |
| K7 nyam | narrow/g1.0/H50 | n/a | +769 (live +1345; $4.84 +761) DD +51.0% ww +2185 stops 0.00(0.00) | n/a |
| K7 nyam | both/g1.0/H75 | n/a | +1160 (live +2030; $4.84 +1153) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g1.0/H75 | n/a | +984 (live +1722; $4.84 +977) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g0.5/H75 | n/a | +668 (live +1170; $4.84 +667) DD +40.3% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | both/g0.5/H75 | n/a | +806 (live +1410; $4.84 +805) DD +39.5% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H75 | n/a | +176 (live +308; $4.84 +176) DD -0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H50 | n/a | +252 (live +441; $4.84 +253) DD -0.3% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g0.5/H75 | n/a | +137 (live +241; $4.84 +137) DD -0.8% ww +0 stops 0.00(0.00) | n/a |
| K7 nypm | wide/g1.0/H50 | n/a | +442 (live +773; $4.84 +442) DD +17.3% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | wide/g1.0/H75 | n/a | +70 (live +122; $4.84 +70) DD +13.1% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | both/g1.0/H75 | n/a | -184 (live -322; $4.84 -197) DD +9.8% ww +1145 stops 0.15(0.08) | n/a |
| K7 nypm | wide/g0.5/H75 | n/a | -4 (live -8; $4.84 -4) DD -1.5% ww -38 stops 0.00(0.08) | n/a |
| K7 nypm | narrow/g1.0/H50 | n/a | +48 (live +84; $4.84 +32) DD -1.9% ww +105 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g1.0/H75 | n/a | -254 (live -445; $4.84 -267) DD -3.3% ww +990 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g0.5/H75 | n/a | -266 (live -465; $4.84 -269) DD -26.7% ww +140 stops 0.08(0.08) | n/a |
| K7 nypm | both/g0.5/H75 | n/a | -270 (live -473; $4.84 -274) DD -27.3% ww +102 stops 0.00(0.08) | n/a |
| M7 london | wide/g1.0/H75 | n/a | +1614 (live +2824; $4.84 +1616) DD +4.9% ww +1190 stops 0.53(0.91) | n/a |
| M7 london | wide/g0.5/H75 | n/a | +688 (live +1204; $4.84 +689) DD +4.4% ww +1400 stops 0.84(0.91) | n/a |
| M7 london | wide/g1.0/H50 | n/a | +538 (live +942; $4.84 +540) DD -1.3% ww -80 stops 0.84(0.91) | n/a |
| M7 london | both/g0.5/H75 | n/a | +1147 (live +2008; $4.84 +1139) DD -8.1% ww +130 stops 1.07(0.91) | n/a |
| M7 london | narrow/g0.5/H75 | n/a | +417 (live +730; $4.84 +408) DD -10.9% ww -1075 stops 1.14(0.91) | n/a |
| M7 london | narrow/g1.0/H50 | n/a | +476 (live +833; $4.84 +446) DD -19.9% ww +1144 stops 1.45(0.91) | n/a |
| M7 london | narrow/g1.0/H75 | n/a | -366 (live -640; $4.84 -390) DD -20.4% ww +80 stops 1.29(0.91) | n/a |
| M7 london | both/g1.0/H75 | n/a | +1142 (live +1999; $4.84 +1121) DD -23.2% ww -729 stops 0.91(0.91) | n/a |
| M7 nyam | narrow/g1.0/H50 | n/a | +439 (live +769; $4.84 +424) DD +26.0% ww -222 stops 0.38(0.23) | n/a |
| M7 nyam | both/g0.5/H75 | n/a | +79 (live +138; $4.84 +75) DD +0.8% ww +194 stops 0.30(0.23) | n/a |
| M7 nyam | narrow/g0.5/H75 | n/a | +73 (live +127; $4.84 +69) DD +0.8% ww +194 stops 0.38(0.23) | n/a |
| M7 nyam | wide/g0.5/H75 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H75 | n/a | +16 (live +28; $4.84 +16) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H50 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | both/g1.0/H75 | n/a | +419 (live +733; $4.84 +405) DD -6.8% ww -991 stops 0.46(0.23) | n/a |
| M7 nyam | narrow/g1.0/H75 | n/a | +402 (live +704; $4.84 +388) DD -6.8% ww -991 stops 0.53(0.23) | n/a |
| P7 asia | both/g0.0/H50 | -5189 (live -9081; $4.84 -4987) DD +44.9% ww +11844 stops 0.00(0.00) | -703 (live -1230; $4.84 -620) DD +51.2% ww +20259 stops 0.08(0.15) | -2946 (live -5156; $4.84 -2804) DD +51.2% ww +17717 stops 0.04(0.08) |
| P7 asia | narrow/g1.0/H50 | n/a | -3918 (live -6857; $4.84 -4186) DD -0.4% ww -4286 stops 0.46(0.15) | n/a |
| P7 asia | both/g0.5/H75 | n/a | -5946 (live -10406; $4.84 -6044) DD -1.0% ww +6944 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g0.5/H75 | n/a | -5762 (live -10084; $4.84 -5860) DD -1.0% ww +9022 stops 0.15(0.15) | n/a |
| P7 asia | wide/g0.5/H75 | n/a | -184 (live -322; $4.84 -183) DD -4.9% ww -2079 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g1.0/H75 | n/a | -2696 (live -4718; $4.84 -2882) DD -7.8% ww -10346 stops 0.53(0.15) | n/a |
| P7 asia | wide/g1.0/H50 | n/a | -816 (live -1428; $4.84 -812) DD -22.6% ww -9033 stops 0.15(0.15) | n/a |
| P7 asia | wide/g1.0/H75 | n/a | -491 (live -858; $4.84 -490) DD -25.2% ww -10331 stops 0.15(0.15) | n/a |
| P7 asia | both/g1.0/H75 | n/a | -3315 (live -5802; $4.84 -3501) DD -36.1% ww -13164 stops 0.53(0.15) | n/a |
| P7 london | both/g0.5/H75 | n/a | +894 (live +1565; $4.84 +886) DD +29.6% ww -1633 stops 0.08(0.08) | n/a |
| P7 london | narrow/g0.5/H75 | n/a | +386 (live +675; $4.84 +375) DD +28.5% ww -1328 stops 0.08(0.08) | n/a |
| P7 london | narrow/g1.0/H50 | n/a | +927 (live +1622; $4.84 +895) DD +19.7% ww -3009 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H75 | n/a | -142 (live -249; $4.84 -138) DD +2.7% ww -458 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H50 | n/a | +265 (live +464; $4.84 +266) DD +1.1% ww +0 stops 0.08(0.08) | n/a |
| P7 london | wide/g0.5/H75 | n/a | +385 (live +674; $4.84 +387) DD -1.9% ww -238 stops 0.08(0.08) | n/a |
| P7 london | both/g1.0/H75 | n/a | +1179 (live +2064; $4.84 +1145) DD -9.8% ww -5408 stops 0.15(0.08) | n/a |
| P7 london | narrow/g1.0/H75 | n/a | +1322 (live +2313; $4.84 +1282) DD -14.4% ww -5203 stops 0.15(0.08) | n/a |
| P7 nyam | both/g1.0/H75 | n/a | +697 (live +1220; $4.84 +685) DD +51.3% ww +354 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g1.0/H75 | n/a | +543 (live +951; $4.84 +529) DD +45.9% ww +324 stops 0.30(0.38) | n/a |
| P7 nyam | both/g0.5/H75 | n/a | +105 (live +184; $4.84 +99) DD +36.7% ww +238 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g0.5/H75 | n/a | -13 (live -23; $4.84 -20) DD +36.4% ww +262 stops 0.30(0.38) | n/a |
| P7 nyam | wide/g0.5/H75 | n/a | +118 (live +207; $4.84 +119) DD +0.3% ww -25 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H75 | n/a | +16 (live +27; $4.84 +17) DD -7.5% ww -105 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H50 | n/a | -544 (live -952; $4.84 -543) DD -47.7% ww -3348 stops 0.38(0.38) | n/a |
| U7 asia | narrow/g1.0/H50 | n/a | +1222 (live +2139; $4.84 +1201) DD +15.6% ww -265 stops 1.90(1.83) | n/a |
| U7 asia | both/g1.0/H75 | n/a | +71 (live +124; $4.84 +56) DD +8.3% ww -1836 stops 1.98(1.83) | n/a |
| U7 asia | narrow/g1.0/H75 | n/a | +502 (live +879; $4.84 +487) DD +8.3% ww +983 stops 1.98(1.83) | n/a |
| U7 asia | both/g0.5/H75 | n/a | -800 (live -1399; $4.84 -808) DD +6.6% ww -2883 stops 2.05(1.83) | n/a |
| U7 asia | narrow/g0.5/H75 | n/a | -162 (live -284; $4.84 -170) DD +6.6% ww +57 stops 2.05(1.83) | n/a |
| U7 asia | wide/g0.5/H75 | n/a | -637 (live -1115; $4.84 -637) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H75 | n/a | -431 (live -755; $4.84 -431) DD +0.0% ww -1836 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H50 | n/a | -648 (live -1134; $4.84 -648) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 london | narrow/g0.5/H75 | n/a | +393 (live +687; $4.84 +392) DD +17.2% ww +1796 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H75 | n/a | +246 (live +431; $4.84 +243) DD +3.1% ww -1185 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H50 | n/a | -41 (live -72; $4.84 -48) DD -9.9% ww -1991 stops 1.52(1.45) | n/a |
| U7 london | both/g0.5/H75 | n/a | -891 (live -1560; $4.84 -890) DD -25.4% ww -3538 stops 1.52(1.45) | n/a |
| U7 london | wide/g1.0/H50 | n/a | -839 (live -1468; $4.84 -837) DD -33.9% ww -4122 stops 1.37(1.45) | n/a |
| U7 london | wide/g0.5/H75 | n/a | -1284 (live -2247; $4.84 -1282) DD -44.3% ww -6280 stops 1.52(1.45) | n/a |
| U7 london | both/g1.0/H75 | n/a | -1728 (live -3025; $4.84 -1729) DD -105.5% ww -7540 stops 1.60(1.45) | n/a |
| U7 london | wide/g1.0/H75 | n/a | -1975 (live -3455; $4.84 -1972) DD -109.8% ww -6355 stops 1.60(1.45) | n/a |

### Summary per slice: pick made on May-Jul, result on L3M
| slice | pick | L3M result of the pick | verdict |
|---|---|---|---|
| A7 asia | pending | | |
| H7 asia | pending | | |
| H7 nyam | pending | | |
| K7 asia | pending | | |
| K7 london | pending | | |
| K7 nyam | pending | | |
| K7 nypm | pending | | |
| M7 london | pending | | |
| M7 nyam | pending | | |
| P7 asia | pending | | |
| P7 london | pending | | |
| P7 nyam | pending | | |
| U7 asia | pending | | |
| U7 london | pending | | |

### B2: why the global version adds full stops (narrow-only/both g1.0 H75 cell, L3M, trade tables)
Reference JN05W2 L3M (no O7): 1855 trades, stop rate 0.071, 132 stops (13 weeks).

**M1_75_g10_c1_d10_c20_tb_B**: 2038 trades (+183 vs JN05W2), stops 173 (+41), stop rate 0.085 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 437 | 0.103 | 3.05 | 94 |
| (40, 50] | 721 | 0.074 | 2.36 | 271 |
| (50, 55] | 232 | 0.099 | 1.97 | 169 |
| (55, 60] | 435 | 0.076 | 1.87 | 76 |
| (60, 70] | 75 | 0.120 | 2.01 | -385 |
| (70, 80] | 62 | 0.048 | 1.68 | -284 |
| (80, 101] | 76 | 0.092 | 1.13 | -591 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1543 | 0.069 | 2.21 | 54 |
| (3.0, 4.0] | 294 | 0.116 | 2.29 | 239 |
| (4.0, 5.0] | 74 | 0.108 | 2.31 | 364 |
| (5.0, 6.0] | 6 | 0.167 | 2.50 | 172 |
| (6.0, 8.0] | 4 | 0.000 | 1.00 | -119 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1068 | 0.096 | 1.00 | 4 |
| (1, 2] | 385 | 0.078 | 2.00 | 115 |
| (2, 3] | 215 | 0.093 | 3.00 | 23 |
| (3, 5] | 195 | 0.062 | 4.46 | 256 |
| (5, 8] | 138 | 0.065 | 6.70 | 690 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

**M1_75_g10_c1_d10_c20_tb_N**: 2072 trades (+217 vs JN05W2), stops 178 (+46), stop rate 0.086 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 449 | 0.105 | 3.02 | 97 |
| (40, 50] | 725 | 0.073 | 2.35 | 272 |
| (50, 55] | 236 | 0.102 | 1.97 | 150 |
| (55, 60] | 662 | 0.082 | 1.82 | -29 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1644 | 0.072 | 2.18 | 50 |
| (3.0, 4.0] | 264 | 0.121 | 2.38 | 348 |
| (4.0, 5.0] | 44 | 0.091 | 3.11 | 1063 |
| (5.0, 6.0] | 3 | 0.000 | 3.33 | 68 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1073 | 0.095 | 1.00 | 8 |
| (1, 2] | 413 | 0.085 | 2.00 | 117 |
| (2, 3] | 197 | 0.081 | 3.00 | 213 |
| (3, 5] | 217 | 0.074 | 4.43 | 196 |
| (5, 8] | 135 | 0.067 | 6.74 | 714 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

Reading of the W/ATR5 table: ATR5 = mean range of the last 14 five-minute buckets in points; a bracket 3x ATR5 or less is within ordinary 5-minute noise. The noise-floor cells (floor 3/4/5 x ATR5, narrowing only) are listed in B3.


### B3: levers (stop-only / target-only / both / size-only) and noise floor, per slice
| slice | cell | L3M | May-Jul |
|---|---|---|---|

### B4: assembled stack (each slice at its own walk-forward pick, run together)
(not run yet: starts when every slice has a pick)


## Target capped at the forecast
**VERDICT (plain, not a PASS; FIRST PASS; 15 of 26 global exact cap cells scored in L3M, per book x session exact cells still running): planted-edge check PASSED through the exact engine (look-ahead oracle target 0.9 x realised MFE: +85531 $/wk, DD +67.0%, ww +64263; this is a mechanism check, NOT a result); the reachable move is only weakly forecastable (R2 on ln MFE 0.03-0.14, quantile calibration good); in the exact L3M cells the cap at the forecast 50th-percentile move (horizon = 75th-percentile holding time) gives +1486 $/wk, DD -0.5%, ww -240 and the 75th-percentile cap +177 $/wk, DD +0.0%, ww +0, the remaining-range caps cut drawdown (own k1.0 -6226 $/wk, DD +27.0%, ww +12290; HAR k1.0 -7259 $/wk, DD +39.4%, ww +17319) but cost thousands per week. Best exact L3M cap cell inside the mean gate by DD: PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time (DD +7.9%, -120 $/wk). L6M/HOLD/older still to run before any verdict.**

Planted-edge check (H1) for the capping mechanism: cells `tcoracle0.9` / `0.6` set the target to 0.9 / 0.6 x the REALISED maximum favourable move (look-ahead, only to prove the mechanism can show an edge through the exact engine); they must come out strongly positive. Status below in the exact table. Until they do, an exact cap verdict is not stated.

Definition. Reachable move = maximum favourable excursion from the signal-second bar close over the book-session holding horizon H (H50/H75 = median / 75th percentile holding time of that book+session, causal), points. Model: walk-forward ridge (14-day blocks, expanding, min 90 days, per session) on ln((MFE+2)/price) from the Dial 10 own-bar inputs (last 15/30/60/120 min range and vol, same-clock normal, own session level, range used so far, elapsed fraction) plus the side-aware room in the session range so far; quantiles q = fitted + empirical training-residual quantile (50/60/75/90). Cap: target = min(book target 60 pts [58 after fills], q-quantile), stop, lots and every other level unchanged. Remaining-range cap: target = min(book target, k x (session range forecast - range printed so far)), forecast = own (price x exp(sf20), mean of the last 20 sessions) or T-RANGE2 HAR (fc_r2_har, available-epoch checked). Small caps (< 30 pts = 0.5 x stop): take / skip / half. EV target: argmax over T in [20, book target or 300] of T x P(MFE>=T) - stop x (1-P) with the lognormal forecast (ignores the stop-first ordering, so optimistic). Extension: if the forecast median MFE is >= m x book target, target = min(q50, 2 x book target). Lots/base basis: dollars are BASE lots (live x1.75 = multiply by 1.75); fee columns $4.84 beside raw $1.18 where shown.

### Item 1: calibration of the forecast quantiles (share of trades whose realized MFE exceeded the forecast quantile; a q-quantile should be exceeded 1-q of the time = 0.50 / 0.40 / 0.25 / 0.10) and R2 of ln MFE, per session
| H | session | window | n | >q50 | >q60 | >q75 | >q90 | R2 ln MFE | median q75 (pts) | share q75 < 60 |
|---|---|---|---|---|---|---|---|---|---|---|
| 50 | asia | older (<2026-05) | 5119 | 0.51 | 0.41 | 0.26 | 0.12 | 0.121 | 80 | 0.222 |
| 50 | asia | L6M | 2006 | 0.49 | 0.38 | 0.23 | 0.08 | 0.058 | 111 | 0.047 |
| 50 | asia | L3M | 875 | 0.46 | 0.34 | 0.20 | 0.07 | -0.014 | 90 | 0.098 |
| 50 | london | older (<2026-05) | 4892 | 0.51 | 0.41 | 0.26 | 0.11 | 0.142 | 62 | 0.438 |
| 50 | london | L6M | 1406 | 0.48 | 0.37 | 0.23 | 0.08 | 0.028 | 76 | 0.166 |
| 50 | london | L3M | 673 | 0.48 | 0.37 | 0.24 | 0.07 | -0.008 | 68 | 0.247 |
| 50 | nyam | older (<2026-05) | 4142 | 0.47 | 0.38 | 0.24 | 0.11 | 0.077 | 63 | 0.397 |
| 50 | nyam | L6M | 600 | 0.51 | 0.40 | 0.24 | 0.09 | 0.097 | 83 | 0.157 |
| 50 | nyam | L3M | 271 | 0.51 | 0.38 | 0.20 | 0.06 | 0.077 | 68 | 0.258 |
| 50 | nypm | older (<2026-05) | 817 | 0.48 | 0.40 | 0.26 | 0.13 | 0.073 | 62 | 0.419 |
| 50 | nypm | L6M | 150 | 0.59 | 0.50 | 0.33 | 0.13 | 0.221 | 71 | 0.307 |
| 50 | nypm | L3M | 56 | 0.50 | 0.36 | 0.21 | 0.09 | 0.104 | 54 | 0.589 |
| 50 | all | older (<2026-05) | 14970 | 0.50 | 0.40 | 0.26 | 0.12 | 0.123 | 68 | 0.352 |
| 50 | all | L6M | 4162 | 0.49 | 0.38 | 0.23 | 0.08 | 0.080 | 91 | 0.113 |
| 50 | all | L3M | 1875 | 0.47 | 0.36 | 0.21 | 0.07 | 0.014 | 76 | 0.189 |
| 75 | asia | older (<2026-05) | 5119 | 0.52 | 0.41 | 0.26 | 0.12 | 0.134 | 122 | 0.032 |
| 75 | asia | L6M | 2006 | 0.50 | 0.40 | 0.24 | 0.08 | 0.027 | 178 | 0.000 |
| 75 | asia | L3M | 875 | 0.45 | 0.35 | 0.20 | 0.05 | -0.016 | 156 | 0.000 |
| 75 | london | older (<2026-05) | 4891 | 0.51 | 0.42 | 0.27 | 0.11 | 0.157 | 101 | 0.100 |
| 75 | london | L6M | 1406 | 0.49 | 0.37 | 0.21 | 0.08 | 0.069 | 118 | 0.001 |
| 75 | london | L3M | 673 | 0.49 | 0.38 | 0.21 | 0.09 | 0.025 | 108 | 0.000 |
| 75 | nyam | older (<2026-05) | 4142 | 0.48 | 0.38 | 0.23 | 0.10 | 0.065 | 91 | 0.081 |
| 75 | nyam | L6M | 600 | 0.50 | 0.40 | 0.24 | 0.10 | 0.098 | 125 | 0.015 |
| 75 | nyam | L3M | 271 | 0.44 | 0.34 | 0.19 | 0.05 | 0.051 | 103 | 0.015 |
| 75 | nypm | older (<2026-05) | 812 | 0.49 | 0.37 | 0.26 | 0.11 | 0.043 | 87 | 0.095 |
| 75 | nypm | L6M | 150 | 0.53 | 0.46 | 0.34 | 0.17 | 0.179 | 117 | 0.013 |
| 75 | nypm | L3M | 56 | 0.41 | 0.30 | 0.21 | 0.07 | -0.076 | 93 | 0.036 |
| 75 | all | older (<2026-05) | 14964 | 0.51 | 0.40 | 0.25 | 0.11 | 0.131 | 102 | 0.071 |
| 75 | all | L6M | 4162 | 0.50 | 0.39 | 0.23 | 0.09 | 0.079 | 149 | 0.003 |
| 75 | all | L3M | 1875 | 0.46 | 0.36 | 0.20 | 0.06 | 0.032 | 128 | 0.003 |

### Items 3 and 4 (and 2): offline replay of the caps on the JN05W2 trade paths, all 43 months (estimate: 1-min paths, cap counted only before the exit bar, so cut/stop ordering is conservative; the exact cells below decide). d mean $/wk and DD cut % vs JN05W2 on the same trades, scope all, then per session for the cap with the most trades capped
| cap | small-cap rule | scope | window | d mean $/wk (live x1.75) | DD cut % | d worst week | d stops/wk | share capped | share where cap hit |
|---|---|---|---|---|---|---|---|---|---|
| q50_H50 | take | all | L3M | +409 (+715) | -3.9 | -1411 | +0.00 | 0.82 | 0.45 |
| q50_H50 | take | all | L6M | -96 (-169) | -3.9 | -1411 | +0.00 | 0.62 | 0.33 |
| q50_H50 | take | all | OLDER | -1795 (-3141) | +12.0 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | skip | all | L3M | -1581 (-2767) | -5.0 | -1996 | +0.00 | 0.82 | 0.45 |
| q50_H50 | skip | all | L6M | -1445 (-2528) | -5.0 | -1996 | +0.00 | 0.62 | 0.33 |
| q50_H50 | skip | all | OLDER | -2271 (-3975) | +17.4 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | half | all | L3M | -586 (-1026) | -4.4 | -1704 | +0.00 | 0.82 | 0.45 |
| q50_H50 | half | all | L6M | -771 (-1348) | -4.4 | -1704 | +0.00 | 0.62 | 0.33 |
| q50_H50 | half | all | OLDER | -2033 (-3558) | +16.5 | +13127 | +0.00 | 0.80 | 0.45 |
| q60_H50 | take | all | L3M | -1525 (-2668) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | take | all | L6M | -839 (-1469) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | take | all | OLDER | -1296 (-2267) | +12.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | skip | all | L3M | -3272 (-5726) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | skip | all | L6M | -1811 (-3170) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | skip | all | OLDER | -1648 (-2885) | +8.8 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | half | all | L3M | -2398 (-4197) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | half | all | L6M | -1325 (-2319) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | half | all | OLDER | -1472 (-2576) | +10.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q75_H50 | take | all | L3M | +414 (+725) | -0.4 | -214 | +0.00 | 0.21 | 0.11 |
| q75_H50 | take | all | L6M | -44 (-77) | -0.4 | -214 | +0.00 | 0.13 | 0.06 |
| q75_H50 | take | all | OLDER | -719 (-1258) | -1.1 | +13801 | +0.00 | 0.37 | 0.18 |
| q90_H50 | take | all | L3M | +191 (+334) | +0.0 | +0 | +0.00 | 0.02 | 0.01 |
| q90_H50 | take | all | L6M | +142 (+249) | +0.0 | +0 | +0.00 | 0.01 | 0.01 |
| q90_H50 | take | all | OLDER | -169 (-296) | -1.8 | +1686 | +0.00 | 0.08 | 0.03 |
| q50_H75 | take | all | L3M | +128 (+225) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | take | all | L6M | +624 (+1092) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | take | all | OLDER | -931 (-1628) | -13.1 | +11346 | +0.00 | 0.51 | 0.26 |
| q50_H75 | skip | all | L3M | +178 (+312) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | skip | all | L6M | +685 (+1198) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | skip | all | OLDER | -1302 (-2279) | -4.6 | +14384 | +0.00 | 0.51 | 0.26 |
| q50_H75 | half | all | L3M | +153 (+268) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | half | all | L6M | +654 (+1145) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | half | all | OLDER | -1116 (-1954) | -8.8 | +12865 | +0.00 | 0.51 | 0.26 |
| q60_H75 | take | all | L3M | +830 (+1452) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | take | all | L6M | +379 (+664) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | take | all | OLDER | -478 (-836) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | skip | all | L3M | +958 (+1677) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | skip | all | L6M | +421 (+737) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | skip | all | OLDER | -402 (-703) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | half | all | L3M | +894 (+1564) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | half | all | L6M | +400 (+700) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | half | all | OLDER | -440 (-769) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q75_H75 | take | all | L3M | +236 (+413) | +0.0 | +0 | +0.00 | 0.01 | 0.00 |
| q75_H75 | take | all | L6M | +105 (+185) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q75_H75 | take | all | OLDER | -255 (-446) | -1.9 | +1485 | +0.00 | 0.08 | 0.04 |
| q90_H75 | take | all | L3M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | L6M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | OLDER | +10 (+18) | -0.4 | +0 | +0.00 | 0.01 | 0.00 |
| rem_own_k0.5 | take | all | L3M | -6674 (-11680) | +8.8 | -1861 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | take | all | L6M | -13204 (-23108) | +8.7 | -1861 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | take | all | OLDER | -7381 (-12916) | -40.2 | +20529 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | skip | all | L3M | -5271 (-9225) | +21.7 | +2982 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | skip | all | L6M | -10625 (-18594) | +21.7 | +2982 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | skip | all | OLDER | -6272 (-10977) | +17.3 | +21712 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | half | all | L3M | -5973 (-10452) | +16.3 | +560 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | half | all | L6M | -11915 (-20851) | +16.3 | +560 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | half | all | OLDER | -6827 (-11946) | +0.6 | +23150 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.75 | take | all | L3M | -7140 (-12494) | +9.6 | +3294 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | take | all | L6M | -10636 (-18614) | +9.6 | +3294 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | take | all | OLDER | -5846 (-10230) | -24.0 | +12208 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | skip | all | L3M | -3661 (-6406) | +10.3 | +4045 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | skip | all | L6M | -6650 (-11638) | +10.3 | +4045 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | skip | all | OLDER | -3856 (-6749) | +16.1 | +19073 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | half | all | L3M | -5400 (-9450) | +13.0 | +3670 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | half | all | L6M | -8643 (-15126) | +13.0 | +3670 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | half | all | OLDER | -4851 (-8489) | +13.0 | +20157 | +0.00 | 0.73 | 0.53 |
| rem_own_k1.0 | take | all | L3M | -5516 (-9653) | +18.3 | +9104 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | take | all | L6M | -8765 (-15339) | +18.3 | +9104 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | take | all | OLDER | -5714 (-9999) | -58.2 | +11926 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | skip | all | L3M | -3265 (-5714) | +15.0 | +8858 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | skip | all | L6M | -5683 (-9944) | +15.0 | +8858 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | skip | all | OLDER | -3872 (-6775) | -61.0 | +20250 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | half | all | L3M | -4391 (-7683) | +18.5 | +8981 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | half | all | L6M | -7224 (-12642) | +18.5 | +8981 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | half | all | OLDER | -4793 (-8387) | -58.0 | +21393 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.25 | take | all | L3M | -3112 (-5446) | +24.4 | +13750 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | take | all | L6M | -8275 (-14481) | +24.4 | +13750 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | take | all | OLDER | -5400 (-9450) | -15.5 | +4336 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | skip | all | L3M | -456 (-797) | +22.4 | +13720 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | skip | all | L6M | -4232 (-7405) | +22.4 | +13720 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | skip | all | OLDER | -3310 (-5792) | -36.4 | +22803 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | half | all | L3M | -1784 (-3121) | +25.2 | +15286 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | half | all | L6M | -6253 (-10943) | +25.2 | +15286 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | half | all | OLDER | -4355 (-7621) | -18.3 | +15544 | +0.00 | 0.54 | 0.41 |

Per session, q60 H75 take-anyway and remaining-range k=1.25 (own):
| cap | session | window | d mean $/wk | DD cut % | d worst week | share capped |
|---|---|---|---|---|---|---|
| q60_H75 | asia | L3M | +221 | +0.0 | +0 | 0.02 |
| q60_H75 | asia | L6M | +110 | +0.0 | +0 | 0.01 |
| q60_H75 | asia | OLDER | -124 | -0.0 | +0 | 0.23 |
| q60_H75 | london | L3M | +745 | +3.8 | +0 | 0.16 |
| q60_H75 | london | L6M | +330 | +3.8 | +0 | 0.12 |
| q60_H75 | london | OLDER | -294 | -2.1 | +0 | 0.35 |
| q60_H75 | nyam | L3M | +61 | -7.2 | +0 | 0.15 |
| q60_H75 | nyam | L6M | -14 | +0.0 | +0 | 0.10 |
| q60_H75 | nyam | OLDER | -37 | -6.0 | +1403 | 0.37 |
| q60_H75 | nypm | L3M | -197 | -0.0 | +0 | 0.41 |
| q60_H75 | nypm | L6M | -47 | +0.0 | +0 | 0.20 |
| q60_H75 | nypm | OLDER | -22 | -5.4 | +0 | 0.33 |
| rem_own_k1.25 | asia | L3M | -4547 | +35.2 | +434 | 0.37 |
| rem_own_k1.25 | asia | L6M | -6717 | +27.1 | +434 | 0.38 |
| rem_own_k1.25 | asia | OLDER | -4532 | -27.4 | +10774 | 0.62 |
| rem_own_k1.25 | london | L3M | +2278 | +46.3 | +12347 | 0.24 |
| rem_own_k1.25 | london | L6M | +1196 | +46.3 | +12347 | 0.30 |
| rem_own_k1.25 | london | OLDER | -510 | +12.9 | +3024 | 0.51 |
| rem_own_k1.25 | nyam | L3M | -650 | +20.0 | +0 | 0.24 |
| rem_own_k1.25 | nyam | L6M | -2127 | -8.9 | +1531 | 0.39 |
| rem_own_k1.25 | nyam | OLDER | -53 | +10.3 | +7327 | 0.47 |
| rem_own_k1.25 | nypm | L3M | -192 | +21.8 | +1203 | 0.45 |
| rem_own_k1.25 | nypm | L6M | -627 | +21.8 | +1203 | 0.50 |
| rem_own_k1.25 | nypm | OLDER | -304 | -2.4 | -831 | 0.50 |

### Item 4 per book x session (all 43 months): trades whose 60-pt target lies beyond the forecast quantile, their fixed-target result, the capped replay, and how far trades run past the cap
| book | session | cap | trades | share beyond | fixed-target hit rate | fixed avg $/trade | capped avg $/trade | avg points run past cap |
|---|---|---|---|---|---|---|---|---|
| A7 | asia | q50_H75 | 1156 | 0.25 | 0.50 | 60 | 87 | 10.4 |
| A7 | asia | q60_H75 | 1156 | 0.13 | 0.47 | 4 | 26 | 8.8 |
| A7 | asia | q75_H75 | 1156 | 0.03 | 0.48 | 19 | 6 | 11.1 |
| A7 | asia | rem_own_k0.75 | 1156 | 0.74 | 0.52 | 126 | 22 | 32.9 |
| H7 | asia | q50_H75 | 700 | 0.33 | 0.49 | 164 | 181 | 11.3 |
| H7 | asia | q60_H75 | 700 | 0.18 | 0.56 | 447 | 414 | 10.7 |
| H7 | asia | q75_H75 | 700 | 0.02 | 0.50 | -318 | -267 | 16.1 |
| H7 | asia | rem_own_k0.75 | 700 | 0.71 | 0.48 | 208 | 55 | 27.8 |
| H7 | nyam | q50_H75 | 348 | 0.49 | 0.46 | 84 | 25 | 8.9 |
| H7 | nyam | q60_H75 | 348 | 0.25 | 0.47 | 96 | 46 | 7.4 |
| H7 | nyam | q75_H75 | 348 | 0.06 | 0.33 | -113 | -12 | 4.7 |
| H7 | nyam | rem_own_k0.75 | 348 | 0.66 | 0.47 | 62 | -35 | 23.3 |
| K7 | asia | q50_H75 | 2596 | 0.32 | 0.44 | 102 | 74 | 9.7 |
| K7 | asia | q60_H75 | 2596 | 0.19 | 0.44 | 111 | 90 | 7.6 |
| K7 | asia | q75_H75 | 2596 | 0.04 | 0.40 | 26 | 1 | 6.1 |
| K7 | asia | rem_own_k0.75 | 2596 | 0.68 | 0.44 | 88 | 0 | 27.2 |
| K7 | london | q50_H75 | 1781 | 0.57 | 0.43 | 62 | 37 | 10.9 |
| K7 | london | q60_H75 | 1781 | 0.33 | 0.44 | 60 | 35 | 9.4 |
| K7 | london | q75_H75 | 1781 | 0.12 | 0.48 | 138 | 101 | 6.5 |
| K7 | london | rem_own_k0.75 | 1781 | 0.69 | 0.43 | 45 | -12 | 27.4 |
| K7 | nyam | q50_H75 | 1565 | 0.57 | 0.42 | 21 | 18 | 10.0 |
| K7 | nyam | q60_H75 | 1565 | 0.32 | 0.40 | -4 | -17 | 9.0 |
| K7 | nyam | q75_H75 | 1565 | 0.07 | 0.41 | 40 | 36 | 16.3 |
| K7 | nyam | rem_own_k0.75 | 1565 | 0.70 | 0.39 | -21 | -38 | 26.0 |
| K7 | nypm | q50_H75 | 1136 | 0.50 | 0.36 | 65 | 54 | 8.1 |
| K7 | nypm | q60_H75 | 1136 | 0.31 | 0.34 | 62 | 48 | 5.6 |
| K7 | nypm | q75_H75 | 1136 | 0.09 | 0.29 | 155 | 179 | 3.5 |
| K7 | nypm | rem_own_k0.75 | 1136 | 0.71 | 0.37 | 72 | -30 | 23.7 |
| M7 | london | q50_H75 | 2489 | 0.42 | 0.43 | 45 | 40 | 10.0 |
| M7 | london | q60_H75 | 2489 | 0.24 | 0.43 | 32 | 26 | 8.2 |
| M7 | london | q75_H75 | 2489 | 0.06 | 0.38 | -74 | -97 | 7.1 |
| M7 | london | rem_own_k0.75 | 2489 | 0.59 | 0.39 | -40 | -29 | 22.9 |
| M7 | nyam | q50_H75 | 1496 | 0.52 | 0.43 | 49 | 22 | 8.6 |
| M7 | nyam | q60_H75 | 1496 | 0.27 | 0.44 | 76 | 57 | 7.2 |
| M7 | nyam | q75_H75 | 1496 | 0.06 | 0.44 | 127 | 131 | 4.9 |
| M7 | nyam | rem_own_k0.75 | 1496 | 0.69 | 0.42 | 30 | -36 | 27.3 |
| O7 | nyam | q50_H75 | 452 | 0.58 | 0.32 | 205 | 91 | 20.5 |
| O7 | nyam | q60_H75 | 452 | 0.37 | 0.31 | 156 | 118 | 16.9 |
| O7 | nyam | q75_H75 | 452 | 0.08 | 0.20 | -192 | -145 | 9.5 |
| O7 | nyam | rem_own_k0.75 | 452 | 0.31 | 0.30 | 120 | 82 | 20.6 |
| P7 | asia | q50_H75 | 2161 | 0.29 | 0.46 | 391 | 341 | 10.2 |
| P7 | asia | q60_H75 | 2161 | 0.16 | 0.48 | 487 | 484 | 9.3 |
| P7 | asia | q75_H75 | 2161 | 0.02 | 0.55 | 1227 | 969 | 5.7 |
| P7 | asia | rem_own_k0.75 | 2161 | 0.70 | 0.44 | 447 | 130 | 26.6 |
| P7 | london | q50_H75 | 1537 | 0.62 | 0.38 | 74 | 27 | 10.0 |
| P7 | london | q60_H75 | 1537 | 0.41 | 0.38 | 67 | 36 | 7.8 |
| P7 | london | q75_H75 | 1537 | 0.15 | 0.41 | 124 | 59 | 5.3 |
| P7 | london | rem_own_k0.75 | 1537 | 0.72 | 0.37 | -19 | -13 | 23.8 |
| P7 | nyam | q50_H75 | 1050 | 0.72 | 0.38 | 38 | 150 | 13.2 |
| P7 | nyam | q60_H75 | 1050 | 0.48 | 0.37 | -7 | 28 | 10.9 |
| P7 | nyam | q75_H75 | 1050 | 0.15 | 0.33 | -88 | -96 | 13.3 |
| P7 | nyam | rem_own_k0.75 | 1050 | 0.71 | 0.37 | -43 | 67 | 33.2 |
| U7 | asia | q50_H75 | 686 | 0.28 | 0.54 | 412 | 320 | 10.4 |
| U7 | asia | q60_H75 | 686 | 0.15 | 0.50 | 322 | 270 | 8.0 |
| U7 | asia | q75_H75 | 686 | 0.03 | 0.47 | -260 | -383 | 6.8 |
| U7 | asia | rem_own_k0.75 | 686 | 0.74 | 0.53 | 375 | 4 | 30.5 |
| U7 | london | q50_H75 | 645 | 0.27 | 0.46 | -102 | -183 | 8.7 |
| U7 | london | q60_H75 | 645 | 0.13 | 0.46 | -173 | -182 | 7.8 |
| U7 | london | q75_H75 | 645 | 0.03 | 0.50 | -396 | -466 | 5.4 |
| U7 | london | rem_own_k0.75 | 645 | 0.68 | 0.51 | 166 | 14 | 24.5 |

### Exact cap cells (global: all books at once; L3M, L6M when promoted; delta vs JN05W2)
| cell | L3M | L6M | HOLD | d mean/wk at $4.84 L3M |
|---|---|---|---|---|
| quantile 50 cap, horizon = 75th-percentile holding time | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | +1452 (lots +9/wk) |
| quantile 60 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 75 cap, horizon = 75th-percentile holding time | +177 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 101%, w2l 0 | n/a | n/a | +176 (lots +0/wk) |
| quantile 90 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 60 cap, horizon = median holding time | -1554 $/wk, DD +2.5%, ww +1445, stops 10.42(10.35), b5 89%, w2l 1 | n/a | n/a | -1658 (lots +29/wk) |
| quantile 75 cap, horizon = median holding time | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=0.5 | -8393 $/wk, DD +2.1%, ww +5889, stops 7.76(10.35), b5 57%, w2l 3 | n/a | n/a | -8805 (lots +113/wk) |
| remaining-range cap, forecast own 20-session mean, k=0.75 | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=1.0 | -6226 $/wk, DD +27.0%, ww +12290, stops 8.98(10.35), b5 66%, w2l 2 | n/a | n/a | -6458 (lots +63/wk) |
| remaining-range cap, forecast own 20-session mean, k=1.25 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.5 | -10795 $/wk, DD +40.3%, ww +11430, stops 7.00(10.35), b5 51%, w2l 4 | n/a | n/a | -11257 (lots +126/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.75 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.0 | -7259 $/wk, DD +39.4%, ww +17319, stops 7.76(10.35), b5 65%, w2l 2 | n/a | n/a | -7570 (lots +85/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.25 | pending | | | |
| EV-best target, bounded by the book target | -14326 $/wk, DD -25.6%, ww -15613, stops 8.45(10.35), b5 46%, w2l 3 | n/a | n/a | -14639 (lots +86/wk) |
| EV-best target, unbounded | pending | | | |
| extension m=1.0 | -110 $/wk, DD -53.4%, ww -2988, stops 11.72(10.35), b5 124%, w2l 2 | n/a | n/a | -18 (lots -25/wk) |
| extension m=1.5 | pending | | | |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts skipped | +1443 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | n/a | n/a | +1410 (lots +9/wk) |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts at half size | pending | | | |
| PLANTED-EDGE CHECK (look-ahead oracle 0.9 x realised MFE, not a result) | +85531 $/wk, DD +67.0%, ww +64263, stops 6.54(10.35), b5 259%, w2l 0 | n/a | n/a | +85219 (lots +85/wk) |
| PLANTED-EDGE CHECK (oracle 0.6 x realised MFE, not a result) | pending | | | |
| PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 | n/a | -125 (lots +1/wk) |
| PLACEBO pl23: quantile 50 cap, horizon = 75th-percentile holding time | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 | n/a | -871 (lots +3/wk) |
| PLACEBO pl37: quantile 50 cap, horizon = 75th-percentile holding time | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 | n/a | -612 (lots +2/wk) |
| PLACEBO plR1: quantile 50 cap, horizon = 75th-percentile holding time | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 | n/a | -670 (lots +4/wk) |

### The one candidate: forecast-quantile-50 cap, horizon = 75th-percentile holding time (L3M mean-only so far): all windows, W44 removed, placebos
| window | scope all | W44 removed |
|---|---|---|
| L3M | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 |
| L6M | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 |
| HOLD | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 |
| MID | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 |
| PREUW | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 |
Placebos (same cap, forecast features taken n sessions earlier at the same clock / a random earlier session), L3M then L6M when run:
| placebo | L3M | L6M |
|---|---|---|
| pl11 | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 |
| pl23 | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 |
| pl37 | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 |
| plR1 | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 |

### Per book x session exact cap cells (clean: one book in one session)
| slice | cap | L3M | May-Jul |
|---|---|---|---|
| A7 asia | quantile 50 cap, horizon = 75th-percentile holding time | -17 (live -30; $4.84 -17) DD +0.0% ww +0 stops 4.03(4.03) | n/a |

### FOR THE LIVE BUILD (what D7 computes at the signal second)
From its own 1-minute bars: last 15/30/60/120-minute range and realised vol, same-offset range over the previous 20 sessions (median), session ranges of the last 5/20 sessions, range so far, the entry position in the session range (favourable-side room), elapsed fraction of the session, ln of the book-session horizon; a small coefficient table per session (15 weights, mean, sd, intercept, four residual quantile offsets) refit every 14 days and shipped as a static file. Cap = min(60, price x exp(prediction + quantile offset) - 2); orders: the target limit is placed at the capped price. The remaining-range version needs the HAR session forecast (T-RANGE2 file) or D7 computes its own 20-session mean. No intraday feed from the box.


## Per book and session, clean, and the assembled stack
**STATUS (plain, not a PASS; B1 in progress, no "nothing passes" verdict is allowed until it is done): single-book single-session cells scored in L3M for 15 of 14 slices; slice picks so far: {}.**

Method (user order PART B, 2026-11-15): each cell = the Dial 10 hook restricted to ONE book in ONE session (every other book/session unchanged at JN05W2), exact engine, all layers ON, live caps. Dollars are BASE lots; the x1.75 live figure sits beside each headline (live); the $4.84 figure reprices every contract at the FEES.md $4.84 RT (engine raw $1.18). Compared on the same book x session slice of JN05W2 (day locks/caps still interact across books, which is why the cells are run for real and not sliced from the global run). B1a settings per slice: direction both / narrow-only / wide-only x gearing 0.5 / 1.0 at the 75th-percentile horizon, plus narrow/wide g1.0 at the median horizon; "fixed" = JN05W2 itself. Walk-forward: the pick for each slice is made on 2026-05..07 only (older than L3M); L3M (2026-08..10) is then out-of-sample. B1b (around each pick): lots cap 1.5/3, lots follow half the change, dead band 0/20%, target ratio 0.8/1.2, lever stop-only (sl: stop W, lots inverse, target in the same points) / target-only (tg) / size-only (sz: bracket fixed, lots follow the forecast), noise floor k = 3/4/5 x recent 5-minute ATR (bracket never narrower), clips 25..120 / 20..150.

### B1 table: per slice, every cell (L3M, delta vs JN05W2 same slice; May-Jul = the selection window)
| slice | setting | May-Jul (selection) | L3M (out of sample) | L6M |
|---|---|---|---|---|
| A7 asia | both/g1.0/H75 | -374 (live -654; $4.84 -370) DD -10.9% ww -261 stops 2.97(3.88) | +47 (live +83; $4.84 +40) DD +25.6% ww +1495 stops 5.55(4.03) | -163 (live -286; $4.84 -165) DD -29.2% ww +1253 stops 4.26(3.96) |
| A7 asia | narrow/g1.0/H75 | -419 (live -733; $4.84 -423) DD -0.6% ww -175 stops 4.49(3.88) | -18 (live -32; $4.84 -26) DD +17.7% ww +722 stops 5.63(4.03) | -219 (live -383; $4.84 -224) DD -19.1% ww +722 stops 5.06(3.96) |
| A7 asia | both/g0.5/H75 | -556 (live -973; $4.84 -553) DD -9.2% ww +72 stops 3.50(3.88) | -192 (live -336; $4.84 -195) DD +10.1% ww +412 stops 5.10(4.03) | -374 (live -654; $4.84 -374) DD -36.6% ww +412 stops 4.30(3.96) |
| A7 asia | narrow/g0.5/H75 | -350 (live -612; $4.84 -352) DD +0.0% ww +0 stops 4.34(3.88) | -186 (live -325; $4.84 -189) DD +10.0% ww +552 stops 5.10(4.03) | -268 (live -469; $4.84 -270) DD -15.8% ww +552 stops 4.72(3.96) |
| A7 asia | wide/g1.0/H75 | +19 (live +33; $4.84 +26) DD -10.9% ww +283 stops 2.51(3.88) | -15 (live -26; $4.84 -14) DD +2.4% ww -426 stops 3.96(4.03) | +2 (live +3; $4.84 +6) DD -13.6% ww -426 stops 3.23(3.96) |
| A7 asia | wide/g0.5/H75 | n/a | -1 (live -1; $4.84 -1) DD +1.4% ww -140 stops 4.03(4.03) | n/a |
| A7 asia | wide/g1.0/H50 | n/a | -48 (live -85; $4.84 -48) DD -3.0% ww -426 stops 3.88(4.03) | n/a |
| A7 asia | narrow/g1.0/H50 | n/a | -159 (live -279; $4.84 -171) DD -8.3% ww +877 stops 5.93(4.03) | n/a |
| H7 asia | wide/g0.5/H75 | n/a | +123 (live +215; $4.84 +123) DD +0.0% ww +0 stops 0.23(0.23) | n/a |
| H7 asia | wide/g1.0/H75 | n/a | -67 (live -118; $4.84 -67) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | wide/g1.0/H50 | n/a | -312 (live -546; $4.84 -312) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | both/g1.0/H75 | +1123 (live +1965; $4.84 +1129) DD +6.5% ww +1483 stops 0.53(0.61) | +177 (live +309; $4.84 +163) DD -33.6% ww -1228 stops 0.61(0.23) | +650 (live +1137; $4.84 +646) DD +6.5% ww +1483 stops 0.57(0.42) |
| H7 asia | narrow/g1.0/H75 | n/a | +244 (live +427; $4.84 +230) DD -33.6% ww -1228 stops 0.53(0.23) | n/a |
| H7 asia | both/g0.5/H75 | n/a | -574 (live -1004; $4.84 -580) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g0.5/H75 | n/a | -697 (live -1219; $4.84 -703) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g1.0/H50 | n/a | -355 (live -621; $4.84 -372) DD -120.5% ww -2166 stops 0.53(0.23) | n/a |
| H7 nyam | narrow/g1.0/H50 | n/a | +252 (live +441; $4.84 +252) DD +60.4% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | both/g1.0/H75 | n/a | +281 (live +491; $4.84 +280) DD +57.7% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | narrow/g1.0/H75 | -187 (live -328; $4.84 -188) DD -4.0% ww +0 stops 0.53(0.46) | +258 (live +452; $4.84 +258) DD +57.7% ww +480 stops 0.30(0.38) | +35 (live +62; $4.84 +35) DD +24.1% ww +480 stops 0.42(0.42) |
| H7 nyam | both/g0.0/H50 | -58 (live -102; $4.84 -58) DD +9.4% ww +0 stops 0.46(0.46) | +221 (live +387; $4.84 +221) DD +54.7% ww +195 stops 0.15(0.38) | +82 (live +143; $4.84 +81) DD +33.9% ww +195 stops 0.30(0.42) |
| H7 nyam | both/g0.5/H75 | +103 (live +180; $4.84 +103) DD +29.2% ww -83 stops 0.46(0.46) | +87 (live +153; $4.84 +87) DD +2.2% ww +195 stops 0.38(0.38) | +95 (live +167; $4.84 +95) DD +2.2% ww +195 stops 0.42(0.42) |
| H7 nyam | narrow/g0.5/H75 | n/a | +77 (live +134; $4.84 +77) DD +2.2% ww +195 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g0.5/H75 | n/a | +11 (live +19; $4.84 +11) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H75 | n/a | +22 (live +39; $4.84 +22) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H50 | n/a | +30 (live +53; $4.84 +30) DD +0.0% ww +0 stops 0.30(0.38) | n/a |
| K7 asia | wide/g1.0/H75 | n/a | +297 (live +520; $4.84 +298) DD +0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | wide/g0.5/H75 | n/a | -54 (live -94; $4.84 -54) DD -0.7% ww -404 stops 0.00(0.00) | n/a |
| K7 asia | narrow/g0.5/H75 | n/a | +1877 (live +3285; $4.84 +1855) DD -19.6% ww -2412 stops 0.00(0.00) | n/a |
| K7 asia | both/g0.5/H75 | n/a | +1823 (live +3191; $4.84 +1801) DD -28.8% ww -3232 stops 0.00(0.00) | n/a |
| K7 asia | wide/g1.0/H50 | n/a | -401 (live -702; $4.84 -400) DD -35.9% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | both/g1.0/H75 | n/a | +1292 (live +2261; $4.84 +1220) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H75 | n/a | +912 (live +1595; $4.84 +838) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H50 | n/a | +355 (live +621; $4.84 +268) DD -86.2% ww -5644 stops 0.00(0.00) | n/a |
| K7 london | both/g0.5/H75 | n/a | -9 (live -15; $4.84 -14) DD +8.7% ww +4326 stops 0.23(0.30) | n/a |
| K7 london | wide/g0.5/H75 | n/a | +27 (live +48; $4.84 +29) DD +0.5% ww +0 stops 0.30(0.30) | n/a |
| K7 london | wide/g1.0/H50 | n/a | +431 (live +755; $4.84 +433) DD -3.3% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g0.5/H75 | n/a | -123 (live -215; $4.84 -130) DD -4.2% ww +4733 stops 0.23(0.30) | n/a |
| K7 london | wide/g1.0/H75 | n/a | +157 (live +274; $4.84 +160) DD -4.8% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g1.0/H50 | n/a | -182 (live -319; $4.84 -204) DD -13.7% ww +3097 stops 0.23(0.30) | n/a |
| K7 london | both/g1.0/H75 | n/a | +481 (live +841; $4.84 +462) DD -25.5% ww +4257 stops 0.38(0.30) | n/a |
| K7 london | narrow/g1.0/H75 | n/a | -31 (live -55; $4.84 -55) DD -42.3% ww +4122 stops 0.38(0.30) | n/a |
| K7 nyam | both/g0.0/H50 | -488 (live -855; $4.84 -488) DD -38.7% ww -514 stops 0.08(0.08) | +1078 (live +1886; $4.84 +1069) DD +53.9% ww +1605 stops 0.00(0.00) | +295 (live +516; $4.84 +290) DD +50.6% ww +1605 stops 0.04(0.04) |
| K7 nyam | narrow/g1.0/H50 | n/a | +769 (live +1345; $4.84 +761) DD +51.0% ww +2185 stops 0.00(0.00) | n/a |
| K7 nyam | both/g1.0/H75 | n/a | +1160 (live +2030; $4.84 +1153) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g1.0/H75 | n/a | +984 (live +1722; $4.84 +977) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g0.5/H75 | n/a | +668 (live +1170; $4.84 +667) DD +40.3% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | both/g0.5/H75 | n/a | +806 (live +1410; $4.84 +805) DD +39.5% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H75 | n/a | +176 (live +308; $4.84 +176) DD -0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H50 | n/a | +252 (live +441; $4.84 +253) DD -0.3% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g0.5/H75 | n/a | +137 (live +241; $4.84 +137) DD -0.8% ww +0 stops 0.00(0.00) | n/a |
| K7 nypm | wide/g1.0/H50 | n/a | +442 (live +773; $4.84 +442) DD +17.3% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | wide/g1.0/H75 | n/a | +70 (live +122; $4.84 +70) DD +13.1% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | both/g1.0/H75 | n/a | -184 (live -322; $4.84 -197) DD +9.8% ww +1145 stops 0.15(0.08) | n/a |
| K7 nypm | wide/g0.5/H75 | n/a | -4 (live -8; $4.84 -4) DD -1.5% ww -38 stops 0.00(0.08) | n/a |
| K7 nypm | narrow/g1.0/H50 | n/a | +48 (live +84; $4.84 +32) DD -1.9% ww +105 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g1.0/H75 | n/a | -254 (live -445; $4.84 -267) DD -3.3% ww +990 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g0.5/H75 | n/a | -266 (live -465; $4.84 -269) DD -26.7% ww +140 stops 0.08(0.08) | n/a |
| K7 nypm | both/g0.5/H75 | n/a | -270 (live -473; $4.84 -274) DD -27.3% ww +102 stops 0.00(0.08) | n/a |
| M7 london | wide/g1.0/H75 | n/a | +1614 (live +2824; $4.84 +1616) DD +4.9% ww +1190 stops 0.53(0.91) | n/a |
| M7 london | wide/g0.5/H75 | n/a | +688 (live +1204; $4.84 +689) DD +4.4% ww +1400 stops 0.84(0.91) | n/a |
| M7 london | wide/g1.0/H50 | n/a | +538 (live +942; $4.84 +540) DD -1.3% ww -80 stops 0.84(0.91) | n/a |
| M7 london | both/g0.5/H75 | n/a | +1147 (live +2008; $4.84 +1139) DD -8.1% ww +130 stops 1.07(0.91) | n/a |
| M7 london | narrow/g0.5/H75 | n/a | +417 (live +730; $4.84 +408) DD -10.9% ww -1075 stops 1.14(0.91) | n/a |
| M7 london | narrow/g1.0/H50 | n/a | +476 (live +833; $4.84 +446) DD -19.9% ww +1144 stops 1.45(0.91) | n/a |
| M7 london | narrow/g1.0/H75 | n/a | -366 (live -640; $4.84 -390) DD -20.4% ww +80 stops 1.29(0.91) | n/a |
| M7 london | both/g1.0/H75 | n/a | +1142 (live +1999; $4.84 +1121) DD -23.2% ww -729 stops 0.91(0.91) | n/a |
| M7 nyam | narrow/g1.0/H50 | n/a | +439 (live +769; $4.84 +424) DD +26.0% ww -222 stops 0.38(0.23) | n/a |
| M7 nyam | both/g0.5/H75 | n/a | +79 (live +138; $4.84 +75) DD +0.8% ww +194 stops 0.30(0.23) | n/a |
| M7 nyam | narrow/g0.5/H75 | n/a | +73 (live +127; $4.84 +69) DD +0.8% ww +194 stops 0.38(0.23) | n/a |
| M7 nyam | wide/g0.5/H75 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H75 | n/a | +16 (live +28; $4.84 +16) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H50 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | both/g1.0/H75 | n/a | +419 (live +733; $4.84 +405) DD -6.8% ww -991 stops 0.46(0.23) | n/a |
| M7 nyam | narrow/g1.0/H75 | n/a | +402 (live +704; $4.84 +388) DD -6.8% ww -991 stops 0.53(0.23) | n/a |
| P7 asia | both/g0.0/H50 | -5189 (live -9081; $4.84 -4987) DD +44.9% ww +11844 stops 0.00(0.00) | -703 (live -1230; $4.84 -620) DD +51.2% ww +20259 stops 0.08(0.15) | -2946 (live -5156; $4.84 -2804) DD +51.2% ww +17717 stops 0.04(0.08) |
| P7 asia | narrow/g1.0/H50 | n/a | -3918 (live -6857; $4.84 -4186) DD -0.4% ww -4286 stops 0.46(0.15) | n/a |
| P7 asia | both/g0.5/H75 | n/a | -5946 (live -10406; $4.84 -6044) DD -1.0% ww +6944 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g0.5/H75 | n/a | -5762 (live -10084; $4.84 -5860) DD -1.0% ww +9022 stops 0.15(0.15) | n/a |
| P7 asia | wide/g0.5/H75 | n/a | -184 (live -322; $4.84 -183) DD -4.9% ww -2079 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g1.0/H75 | n/a | -2696 (live -4718; $4.84 -2882) DD -7.8% ww -10346 stops 0.53(0.15) | n/a |
| P7 asia | wide/g1.0/H50 | n/a | -816 (live -1428; $4.84 -812) DD -22.6% ww -9033 stops 0.15(0.15) | n/a |
| P7 asia | wide/g1.0/H75 | n/a | -491 (live -858; $4.84 -490) DD -25.2% ww -10331 stops 0.15(0.15) | n/a |
| P7 asia | both/g1.0/H75 | n/a | -3315 (live -5802; $4.84 -3501) DD -36.1% ww -13164 stops 0.53(0.15) | n/a |
| P7 london | both/g0.5/H75 | n/a | +894 (live +1565; $4.84 +886) DD +29.6% ww -1633 stops 0.08(0.08) | n/a |
| P7 london | narrow/g0.5/H75 | n/a | +386 (live +675; $4.84 +375) DD +28.5% ww -1328 stops 0.08(0.08) | n/a |
| P7 london | narrow/g1.0/H50 | n/a | +927 (live +1622; $4.84 +895) DD +19.7% ww -3009 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H75 | n/a | -142 (live -249; $4.84 -138) DD +2.7% ww -458 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H50 | n/a | +265 (live +464; $4.84 +266) DD +1.1% ww +0 stops 0.08(0.08) | n/a |
| P7 london | wide/g0.5/H75 | n/a | +385 (live +674; $4.84 +387) DD -1.9% ww -238 stops 0.08(0.08) | n/a |
| P7 london | both/g1.0/H75 | n/a | +1179 (live +2064; $4.84 +1145) DD -9.8% ww -5408 stops 0.15(0.08) | n/a |
| P7 london | narrow/g1.0/H75 | n/a | +1322 (live +2313; $4.84 +1282) DD -14.4% ww -5203 stops 0.15(0.08) | n/a |
| P7 nyam | both/g1.0/H75 | n/a | +697 (live +1220; $4.84 +685) DD +51.3% ww +354 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g1.0/H75 | n/a | +543 (live +951; $4.84 +529) DD +45.9% ww +324 stops 0.30(0.38) | n/a |
| P7 nyam | both/g0.5/H75 | n/a | +105 (live +184; $4.84 +99) DD +36.7% ww +238 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g0.5/H75 | n/a | -13 (live -23; $4.84 -20) DD +36.4% ww +262 stops 0.30(0.38) | n/a |
| P7 nyam | wide/g0.5/H75 | n/a | +118 (live +207; $4.84 +119) DD +0.3% ww -25 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H75 | n/a | +16 (live +27; $4.84 +17) DD -7.5% ww -105 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H50 | n/a | -544 (live -952; $4.84 -543) DD -47.7% ww -3348 stops 0.38(0.38) | n/a |
| U7 asia | narrow/g1.0/H50 | n/a | +1222 (live +2139; $4.84 +1201) DD +15.6% ww -265 stops 1.90(1.83) | n/a |
| U7 asia | both/g1.0/H75 | n/a | +71 (live +124; $4.84 +56) DD +8.3% ww -1836 stops 1.98(1.83) | n/a |
| U7 asia | narrow/g1.0/H75 | n/a | +502 (live +879; $4.84 +487) DD +8.3% ww +983 stops 1.98(1.83) | n/a |
| U7 asia | both/g0.5/H75 | n/a | -800 (live -1399; $4.84 -808) DD +6.6% ww -2883 stops 2.05(1.83) | n/a |
| U7 asia | narrow/g0.5/H75 | n/a | -162 (live -284; $4.84 -170) DD +6.6% ww +57 stops 2.05(1.83) | n/a |
| U7 asia | wide/g0.5/H75 | n/a | -637 (live -1115; $4.84 -637) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H75 | n/a | -431 (live -755; $4.84 -431) DD +0.0% ww -1836 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H50 | n/a | -648 (live -1134; $4.84 -648) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 london | narrow/g0.5/H75 | n/a | +393 (live +687; $4.84 +392) DD +17.2% ww +1796 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H75 | n/a | +246 (live +431; $4.84 +243) DD +3.1% ww -1185 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H50 | n/a | -41 (live -72; $4.84 -48) DD -9.9% ww -1991 stops 1.52(1.45) | n/a |
| U7 london | both/g0.5/H75 | n/a | -891 (live -1560; $4.84 -890) DD -25.4% ww -3538 stops 1.52(1.45) | n/a |
| U7 london | wide/g1.0/H50 | n/a | -839 (live -1468; $4.84 -837) DD -33.9% ww -4122 stops 1.37(1.45) | n/a |
| U7 london | wide/g0.5/H75 | n/a | -1284 (live -2247; $4.84 -1282) DD -44.3% ww -6280 stops 1.52(1.45) | n/a |
| U7 london | both/g1.0/H75 | n/a | -1728 (live -3025; $4.84 -1729) DD -105.5% ww -7540 stops 1.60(1.45) | n/a |
| U7 london | wide/g1.0/H75 | n/a | -1975 (live -3455; $4.84 -1972) DD -109.8% ww -6355 stops 1.60(1.45) | n/a |

### Summary per slice: pick made on May-Jul, result on L3M
| slice | pick | L3M result of the pick | verdict |
|---|---|---|---|
| A7 asia | pending | | |
| H7 asia | pending | | |
| H7 nyam | pending | | |
| K7 asia | pending | | |
| K7 london | pending | | |
| K7 nyam | pending | | |
| K7 nypm | pending | | |
| M7 london | pending | | |
| M7 nyam | pending | | |
| P7 asia | pending | | |
| P7 london | pending | | |
| P7 nyam | pending | | |
| U7 asia | pending | | |
| U7 london | pending | | |

### B2: why the global version adds full stops (narrow-only/both g1.0 H75 cell, L3M, trade tables)
Reference JN05W2 L3M (no O7): 1855 trades, stop rate 0.071, 132 stops (13 weeks).

**M1_75_g10_c1_d10_c20_tb_B**: 2038 trades (+183 vs JN05W2), stops 173 (+41), stop rate 0.085 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 437 | 0.103 | 3.05 | 94 |
| (40, 50] | 721 | 0.074 | 2.36 | 271 |
| (50, 55] | 232 | 0.099 | 1.97 | 169 |
| (55, 60] | 435 | 0.076 | 1.87 | 76 |
| (60, 70] | 75 | 0.120 | 2.01 | -385 |
| (70, 80] | 62 | 0.048 | 1.68 | -284 |
| (80, 101] | 76 | 0.092 | 1.13 | -591 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1543 | 0.069 | 2.21 | 54 |
| (3.0, 4.0] | 294 | 0.116 | 2.29 | 239 |
| (4.0, 5.0] | 74 | 0.108 | 2.31 | 364 |
| (5.0, 6.0] | 6 | 0.167 | 2.50 | 172 |
| (6.0, 8.0] | 4 | 0.000 | 1.00 | -119 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1068 | 0.096 | 1.00 | 4 |
| (1, 2] | 385 | 0.078 | 2.00 | 115 |
| (2, 3] | 215 | 0.093 | 3.00 | 23 |
| (3, 5] | 195 | 0.062 | 4.46 | 256 |
| (5, 8] | 138 | 0.065 | 6.70 | 690 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

**M1_75_g10_c1_d10_c20_tb_N**: 2072 trades (+217 vs JN05W2), stops 178 (+46), stop rate 0.086 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 449 | 0.105 | 3.02 | 97 |
| (40, 50] | 725 | 0.073 | 2.35 | 272 |
| (50, 55] | 236 | 0.102 | 1.97 | 150 |
| (55, 60] | 662 | 0.082 | 1.82 | -29 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1644 | 0.072 | 2.18 | 50 |
| (3.0, 4.0] | 264 | 0.121 | 2.38 | 348 |
| (4.0, 5.0] | 44 | 0.091 | 3.11 | 1063 |
| (5.0, 6.0] | 3 | 0.000 | 3.33 | 68 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1073 | 0.095 | 1.00 | 8 |
| (1, 2] | 413 | 0.085 | 2.00 | 117 |
| (2, 3] | 197 | 0.081 | 3.00 | 213 |
| (3, 5] | 217 | 0.074 | 4.43 | 196 |
| (5, 8] | 135 | 0.067 | 6.74 | 714 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

Reading of the W/ATR5 table: ATR5 = mean range of the last 14 five-minute buckets in points; a bracket 3x ATR5 or less is within ordinary 5-minute noise. The noise-floor cells (floor 3/4/5 x ATR5, narrowing only) are listed in B3.


### B3: levers (stop-only / target-only / both / size-only) and noise floor, per slice
| slice | cell | L3M | May-Jul |
|---|---|---|---|

### B4: assembled stack (each slice at its own walk-forward pick, run together)
(not run yet: starts when every slice has a pick)


## Target capped at the forecast
**VERDICT (plain, not a PASS; FIRST PASS; 15 of 26 global exact cap cells scored in L3M, per book x session exact cells still running): planted-edge check PASSED through the exact engine (look-ahead oracle target 0.9 x realised MFE: +85531 $/wk, DD +67.0%, ww +64263; this is a mechanism check, NOT a result); the reachable move is only weakly forecastable (R2 on ln MFE 0.03-0.14, quantile calibration good); in the exact L3M cells the cap at the forecast 50th-percentile move (horizon = 75th-percentile holding time) gives +1486 $/wk, DD -0.5%, ww -240 and the 75th-percentile cap +177 $/wk, DD +0.0%, ww +0, the remaining-range caps cut drawdown (own k1.0 -6226 $/wk, DD +27.0%, ww +12290; HAR k1.0 -7259 $/wk, DD +39.4%, ww +17319) but cost thousands per week. Best exact L3M cap cell inside the mean gate by DD: PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time (DD +7.9%, -120 $/wk). L6M/HOLD/older still to run before any verdict.**

Planted-edge check (H1) for the capping mechanism: cells `tcoracle0.9` / `0.6` set the target to 0.9 / 0.6 x the REALISED maximum favourable move (look-ahead, only to prove the mechanism can show an edge through the exact engine); they must come out strongly positive. Status below in the exact table. Until they do, an exact cap verdict is not stated.

Definition. Reachable move = maximum favourable excursion from the signal-second bar close over the book-session holding horizon H (H50/H75 = median / 75th percentile holding time of that book+session, causal), points. Model: walk-forward ridge (14-day blocks, expanding, min 90 days, per session) on ln((MFE+2)/price) from the Dial 10 own-bar inputs (last 15/30/60/120 min range and vol, same-clock normal, own session level, range used so far, elapsed fraction) plus the side-aware room in the session range so far; quantiles q = fitted + empirical training-residual quantile (50/60/75/90). Cap: target = min(book target 60 pts [58 after fills], q-quantile), stop, lots and every other level unchanged. Remaining-range cap: target = min(book target, k x (session range forecast - range printed so far)), forecast = own (price x exp(sf20), mean of the last 20 sessions) or T-RANGE2 HAR (fc_r2_har, available-epoch checked). Small caps (< 30 pts = 0.5 x stop): take / skip / half. EV target: argmax over T in [20, book target or 300] of T x P(MFE>=T) - stop x (1-P) with the lognormal forecast (ignores the stop-first ordering, so optimistic). Extension: if the forecast median MFE is >= m x book target, target = min(q50, 2 x book target). Lots/base basis: dollars are BASE lots (live x1.75 = multiply by 1.75); fee columns $4.84 beside raw $1.18 where shown.

### Item 1: calibration of the forecast quantiles (share of trades whose realized MFE exceeded the forecast quantile; a q-quantile should be exceeded 1-q of the time = 0.50 / 0.40 / 0.25 / 0.10) and R2 of ln MFE, per session
| H | session | window | n | >q50 | >q60 | >q75 | >q90 | R2 ln MFE | median q75 (pts) | share q75 < 60 |
|---|---|---|---|---|---|---|---|---|---|---|
| 50 | asia | older (<2026-05) | 5119 | 0.51 | 0.41 | 0.26 | 0.12 | 0.121 | 80 | 0.222 |
| 50 | asia | L6M | 2006 | 0.49 | 0.38 | 0.23 | 0.08 | 0.058 | 111 | 0.047 |
| 50 | asia | L3M | 875 | 0.46 | 0.34 | 0.20 | 0.07 | -0.014 | 90 | 0.098 |
| 50 | london | older (<2026-05) | 4892 | 0.51 | 0.41 | 0.26 | 0.11 | 0.142 | 62 | 0.438 |
| 50 | london | L6M | 1406 | 0.48 | 0.37 | 0.23 | 0.08 | 0.028 | 76 | 0.166 |
| 50 | london | L3M | 673 | 0.48 | 0.37 | 0.24 | 0.07 | -0.008 | 68 | 0.247 |
| 50 | nyam | older (<2026-05) | 4142 | 0.47 | 0.38 | 0.24 | 0.11 | 0.077 | 63 | 0.397 |
| 50 | nyam | L6M | 600 | 0.51 | 0.40 | 0.24 | 0.09 | 0.097 | 83 | 0.157 |
| 50 | nyam | L3M | 271 | 0.51 | 0.38 | 0.20 | 0.06 | 0.077 | 68 | 0.258 |
| 50 | nypm | older (<2026-05) | 817 | 0.48 | 0.40 | 0.26 | 0.13 | 0.073 | 62 | 0.419 |
| 50 | nypm | L6M | 150 | 0.59 | 0.50 | 0.33 | 0.13 | 0.221 | 71 | 0.307 |
| 50 | nypm | L3M | 56 | 0.50 | 0.36 | 0.21 | 0.09 | 0.104 | 54 | 0.589 |
| 50 | all | older (<2026-05) | 14970 | 0.50 | 0.40 | 0.26 | 0.12 | 0.123 | 68 | 0.352 |
| 50 | all | L6M | 4162 | 0.49 | 0.38 | 0.23 | 0.08 | 0.080 | 91 | 0.113 |
| 50 | all | L3M | 1875 | 0.47 | 0.36 | 0.21 | 0.07 | 0.014 | 76 | 0.189 |
| 75 | asia | older (<2026-05) | 5119 | 0.52 | 0.41 | 0.26 | 0.12 | 0.134 | 122 | 0.032 |
| 75 | asia | L6M | 2006 | 0.50 | 0.40 | 0.24 | 0.08 | 0.027 | 178 | 0.000 |
| 75 | asia | L3M | 875 | 0.45 | 0.35 | 0.20 | 0.05 | -0.016 | 156 | 0.000 |
| 75 | london | older (<2026-05) | 4891 | 0.51 | 0.42 | 0.27 | 0.11 | 0.157 | 101 | 0.100 |
| 75 | london | L6M | 1406 | 0.49 | 0.37 | 0.21 | 0.08 | 0.069 | 118 | 0.001 |
| 75 | london | L3M | 673 | 0.49 | 0.38 | 0.21 | 0.09 | 0.025 | 108 | 0.000 |
| 75 | nyam | older (<2026-05) | 4142 | 0.48 | 0.38 | 0.23 | 0.10 | 0.065 | 91 | 0.081 |
| 75 | nyam | L6M | 600 | 0.50 | 0.40 | 0.24 | 0.10 | 0.098 | 125 | 0.015 |
| 75 | nyam | L3M | 271 | 0.44 | 0.34 | 0.19 | 0.05 | 0.051 | 103 | 0.015 |
| 75 | nypm | older (<2026-05) | 812 | 0.49 | 0.37 | 0.26 | 0.11 | 0.043 | 87 | 0.095 |
| 75 | nypm | L6M | 150 | 0.53 | 0.46 | 0.34 | 0.17 | 0.179 | 117 | 0.013 |
| 75 | nypm | L3M | 56 | 0.41 | 0.30 | 0.21 | 0.07 | -0.076 | 93 | 0.036 |
| 75 | all | older (<2026-05) | 14964 | 0.51 | 0.40 | 0.25 | 0.11 | 0.131 | 102 | 0.071 |
| 75 | all | L6M | 4162 | 0.50 | 0.39 | 0.23 | 0.09 | 0.079 | 149 | 0.003 |
| 75 | all | L3M | 1875 | 0.46 | 0.36 | 0.20 | 0.06 | 0.032 | 128 | 0.003 |

### Items 3 and 4 (and 2): offline replay of the caps on the JN05W2 trade paths, all 43 months (estimate: 1-min paths, cap counted only before the exit bar, so cut/stop ordering is conservative; the exact cells below decide). d mean $/wk and DD cut % vs JN05W2 on the same trades, scope all, then per session for the cap with the most trades capped
| cap | small-cap rule | scope | window | d mean $/wk (live x1.75) | DD cut % | d worst week | d stops/wk | share capped | share where cap hit |
|---|---|---|---|---|---|---|---|---|---|
| q50_H50 | take | all | L3M | +409 (+715) | -3.9 | -1411 | +0.00 | 0.82 | 0.45 |
| q50_H50 | take | all | L6M | -96 (-169) | -3.9 | -1411 | +0.00 | 0.62 | 0.33 |
| q50_H50 | take | all | OLDER | -1795 (-3141) | +12.0 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | skip | all | L3M | -1581 (-2767) | -5.0 | -1996 | +0.00 | 0.82 | 0.45 |
| q50_H50 | skip | all | L6M | -1445 (-2528) | -5.0 | -1996 | +0.00 | 0.62 | 0.33 |
| q50_H50 | skip | all | OLDER | -2271 (-3975) | +17.4 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | half | all | L3M | -586 (-1026) | -4.4 | -1704 | +0.00 | 0.82 | 0.45 |
| q50_H50 | half | all | L6M | -771 (-1348) | -4.4 | -1704 | +0.00 | 0.62 | 0.33 |
| q50_H50 | half | all | OLDER | -2033 (-3558) | +16.5 | +13127 | +0.00 | 0.80 | 0.45 |
| q60_H50 | take | all | L3M | -1525 (-2668) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | take | all | L6M | -839 (-1469) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | take | all | OLDER | -1296 (-2267) | +12.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | skip | all | L3M | -3272 (-5726) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | skip | all | L6M | -1811 (-3170) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | skip | all | OLDER | -1648 (-2885) | +8.8 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | half | all | L3M | -2398 (-4197) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | half | all | L6M | -1325 (-2319) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | half | all | OLDER | -1472 (-2576) | +10.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q75_H50 | take | all | L3M | +414 (+725) | -0.4 | -214 | +0.00 | 0.21 | 0.11 |
| q75_H50 | take | all | L6M | -44 (-77) | -0.4 | -214 | +0.00 | 0.13 | 0.06 |
| q75_H50 | take | all | OLDER | -719 (-1258) | -1.1 | +13801 | +0.00 | 0.37 | 0.18 |
| q90_H50 | take | all | L3M | +191 (+334) | +0.0 | +0 | +0.00 | 0.02 | 0.01 |
| q90_H50 | take | all | L6M | +142 (+249) | +0.0 | +0 | +0.00 | 0.01 | 0.01 |
| q90_H50 | take | all | OLDER | -169 (-296) | -1.8 | +1686 | +0.00 | 0.08 | 0.03 |
| q50_H75 | take | all | L3M | +128 (+225) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | take | all | L6M | +624 (+1092) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | take | all | OLDER | -931 (-1628) | -13.1 | +11346 | +0.00 | 0.51 | 0.26 |
| q50_H75 | skip | all | L3M | +178 (+312) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | skip | all | L6M | +685 (+1198) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | skip | all | OLDER | -1302 (-2279) | -4.6 | +14384 | +0.00 | 0.51 | 0.26 |
| q50_H75 | half | all | L3M | +153 (+268) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | half | all | L6M | +654 (+1145) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | half | all | OLDER | -1116 (-1954) | -8.8 | +12865 | +0.00 | 0.51 | 0.26 |
| q60_H75 | take | all | L3M | +830 (+1452) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | take | all | L6M | +379 (+664) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | take | all | OLDER | -478 (-836) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | skip | all | L3M | +958 (+1677) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | skip | all | L6M | +421 (+737) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | skip | all | OLDER | -402 (-703) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | half | all | L3M | +894 (+1564) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | half | all | L6M | +400 (+700) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | half | all | OLDER | -440 (-769) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q75_H75 | take | all | L3M | +236 (+413) | +0.0 | +0 | +0.00 | 0.01 | 0.00 |
| q75_H75 | take | all | L6M | +105 (+185) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q75_H75 | take | all | OLDER | -255 (-446) | -1.9 | +1485 | +0.00 | 0.08 | 0.04 |
| q90_H75 | take | all | L3M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | L6M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | OLDER | +10 (+18) | -0.4 | +0 | +0.00 | 0.01 | 0.00 |
| rem_own_k0.5 | take | all | L3M | -6674 (-11680) | +8.8 | -1861 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | take | all | L6M | -13204 (-23108) | +8.7 | -1861 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | take | all | OLDER | -7381 (-12916) | -40.2 | +20529 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | skip | all | L3M | -5271 (-9225) | +21.7 | +2982 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | skip | all | L6M | -10625 (-18594) | +21.7 | +2982 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | skip | all | OLDER | -6272 (-10977) | +17.3 | +21712 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | half | all | L3M | -5973 (-10452) | +16.3 | +560 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | half | all | L6M | -11915 (-20851) | +16.3 | +560 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | half | all | OLDER | -6827 (-11946) | +0.6 | +23150 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.75 | take | all | L3M | -7140 (-12494) | +9.6 | +3294 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | take | all | L6M | -10636 (-18614) | +9.6 | +3294 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | take | all | OLDER | -5846 (-10230) | -24.0 | +12208 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | skip | all | L3M | -3661 (-6406) | +10.3 | +4045 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | skip | all | L6M | -6650 (-11638) | +10.3 | +4045 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | skip | all | OLDER | -3856 (-6749) | +16.1 | +19073 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | half | all | L3M | -5400 (-9450) | +13.0 | +3670 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | half | all | L6M | -8643 (-15126) | +13.0 | +3670 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | half | all | OLDER | -4851 (-8489) | +13.0 | +20157 | +0.00 | 0.73 | 0.53 |
| rem_own_k1.0 | take | all | L3M | -5516 (-9653) | +18.3 | +9104 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | take | all | L6M | -8765 (-15339) | +18.3 | +9104 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | take | all | OLDER | -5714 (-9999) | -58.2 | +11926 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | skip | all | L3M | -3265 (-5714) | +15.0 | +8858 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | skip | all | L6M | -5683 (-9944) | +15.0 | +8858 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | skip | all | OLDER | -3872 (-6775) | -61.0 | +20250 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | half | all | L3M | -4391 (-7683) | +18.5 | +8981 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | half | all | L6M | -7224 (-12642) | +18.5 | +8981 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | half | all | OLDER | -4793 (-8387) | -58.0 | +21393 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.25 | take | all | L3M | -3112 (-5446) | +24.4 | +13750 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | take | all | L6M | -8275 (-14481) | +24.4 | +13750 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | take | all | OLDER | -5400 (-9450) | -15.5 | +4336 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | skip | all | L3M | -456 (-797) | +22.4 | +13720 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | skip | all | L6M | -4232 (-7405) | +22.4 | +13720 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | skip | all | OLDER | -3310 (-5792) | -36.4 | +22803 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | half | all | L3M | -1784 (-3121) | +25.2 | +15286 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | half | all | L6M | -6253 (-10943) | +25.2 | +15286 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | half | all | OLDER | -4355 (-7621) | -18.3 | +15544 | +0.00 | 0.54 | 0.41 |

Per session, q60 H75 take-anyway and remaining-range k=1.25 (own):
| cap | session | window | d mean $/wk | DD cut % | d worst week | share capped |
|---|---|---|---|---|---|---|
| q60_H75 | asia | L3M | +221 | +0.0 | +0 | 0.02 |
| q60_H75 | asia | L6M | +110 | +0.0 | +0 | 0.01 |
| q60_H75 | asia | OLDER | -124 | -0.0 | +0 | 0.23 |
| q60_H75 | london | L3M | +745 | +3.8 | +0 | 0.16 |
| q60_H75 | london | L6M | +330 | +3.8 | +0 | 0.12 |
| q60_H75 | london | OLDER | -294 | -2.1 | +0 | 0.35 |
| q60_H75 | nyam | L3M | +61 | -7.2 | +0 | 0.15 |
| q60_H75 | nyam | L6M | -14 | +0.0 | +0 | 0.10 |
| q60_H75 | nyam | OLDER | -37 | -6.0 | +1403 | 0.37 |
| q60_H75 | nypm | L3M | -197 | -0.0 | +0 | 0.41 |
| q60_H75 | nypm | L6M | -47 | +0.0 | +0 | 0.20 |
| q60_H75 | nypm | OLDER | -22 | -5.4 | +0 | 0.33 |
| rem_own_k1.25 | asia | L3M | -4547 | +35.2 | +434 | 0.37 |
| rem_own_k1.25 | asia | L6M | -6717 | +27.1 | +434 | 0.38 |
| rem_own_k1.25 | asia | OLDER | -4532 | -27.4 | +10774 | 0.62 |
| rem_own_k1.25 | london | L3M | +2278 | +46.3 | +12347 | 0.24 |
| rem_own_k1.25 | london | L6M | +1196 | +46.3 | +12347 | 0.30 |
| rem_own_k1.25 | london | OLDER | -510 | +12.9 | +3024 | 0.51 |
| rem_own_k1.25 | nyam | L3M | -650 | +20.0 | +0 | 0.24 |
| rem_own_k1.25 | nyam | L6M | -2127 | -8.9 | +1531 | 0.39 |
| rem_own_k1.25 | nyam | OLDER | -53 | +10.3 | +7327 | 0.47 |
| rem_own_k1.25 | nypm | L3M | -192 | +21.8 | +1203 | 0.45 |
| rem_own_k1.25 | nypm | L6M | -627 | +21.8 | +1203 | 0.50 |
| rem_own_k1.25 | nypm | OLDER | -304 | -2.4 | -831 | 0.50 |

### Item 4 per book x session (all 43 months): trades whose 60-pt target lies beyond the forecast quantile, their fixed-target result, the capped replay, and how far trades run past the cap
| book | session | cap | trades | share beyond | fixed-target hit rate | fixed avg $/trade | capped avg $/trade | avg points run past cap |
|---|---|---|---|---|---|---|---|---|
| A7 | asia | q50_H75 | 1156 | 0.25 | 0.50 | 60 | 87 | 10.4 |
| A7 | asia | q60_H75 | 1156 | 0.13 | 0.47 | 4 | 26 | 8.8 |
| A7 | asia | q75_H75 | 1156 | 0.03 | 0.48 | 19 | 6 | 11.1 |
| A7 | asia | rem_own_k0.75 | 1156 | 0.74 | 0.52 | 126 | 22 | 32.9 |
| H7 | asia | q50_H75 | 700 | 0.33 | 0.49 | 164 | 181 | 11.3 |
| H7 | asia | q60_H75 | 700 | 0.18 | 0.56 | 447 | 414 | 10.7 |
| H7 | asia | q75_H75 | 700 | 0.02 | 0.50 | -318 | -267 | 16.1 |
| H7 | asia | rem_own_k0.75 | 700 | 0.71 | 0.48 | 208 | 55 | 27.8 |
| H7 | nyam | q50_H75 | 348 | 0.49 | 0.46 | 84 | 25 | 8.9 |
| H7 | nyam | q60_H75 | 348 | 0.25 | 0.47 | 96 | 46 | 7.4 |
| H7 | nyam | q75_H75 | 348 | 0.06 | 0.33 | -113 | -12 | 4.7 |
| H7 | nyam | rem_own_k0.75 | 348 | 0.66 | 0.47 | 62 | -35 | 23.3 |
| K7 | asia | q50_H75 | 2596 | 0.32 | 0.44 | 102 | 74 | 9.7 |
| K7 | asia | q60_H75 | 2596 | 0.19 | 0.44 | 111 | 90 | 7.6 |
| K7 | asia | q75_H75 | 2596 | 0.04 | 0.40 | 26 | 1 | 6.1 |
| K7 | asia | rem_own_k0.75 | 2596 | 0.68 | 0.44 | 88 | 0 | 27.2 |
| K7 | london | q50_H75 | 1781 | 0.57 | 0.43 | 62 | 37 | 10.9 |
| K7 | london | q60_H75 | 1781 | 0.33 | 0.44 | 60 | 35 | 9.4 |
| K7 | london | q75_H75 | 1781 | 0.12 | 0.48 | 138 | 101 | 6.5 |
| K7 | london | rem_own_k0.75 | 1781 | 0.69 | 0.43 | 45 | -12 | 27.4 |
| K7 | nyam | q50_H75 | 1565 | 0.57 | 0.42 | 21 | 18 | 10.0 |
| K7 | nyam | q60_H75 | 1565 | 0.32 | 0.40 | -4 | -17 | 9.0 |
| K7 | nyam | q75_H75 | 1565 | 0.07 | 0.41 | 40 | 36 | 16.3 |
| K7 | nyam | rem_own_k0.75 | 1565 | 0.70 | 0.39 | -21 | -38 | 26.0 |
| K7 | nypm | q50_H75 | 1136 | 0.50 | 0.36 | 65 | 54 | 8.1 |
| K7 | nypm | q60_H75 | 1136 | 0.31 | 0.34 | 62 | 48 | 5.6 |
| K7 | nypm | q75_H75 | 1136 | 0.09 | 0.29 | 155 | 179 | 3.5 |
| K7 | nypm | rem_own_k0.75 | 1136 | 0.71 | 0.37 | 72 | -30 | 23.7 |
| M7 | london | q50_H75 | 2489 | 0.42 | 0.43 | 45 | 40 | 10.0 |
| M7 | london | q60_H75 | 2489 | 0.24 | 0.43 | 32 | 26 | 8.2 |
| M7 | london | q75_H75 | 2489 | 0.06 | 0.38 | -74 | -97 | 7.1 |
| M7 | london | rem_own_k0.75 | 2489 | 0.59 | 0.39 | -40 | -29 | 22.9 |
| M7 | nyam | q50_H75 | 1496 | 0.52 | 0.43 | 49 | 22 | 8.6 |
| M7 | nyam | q60_H75 | 1496 | 0.27 | 0.44 | 76 | 57 | 7.2 |
| M7 | nyam | q75_H75 | 1496 | 0.06 | 0.44 | 127 | 131 | 4.9 |
| M7 | nyam | rem_own_k0.75 | 1496 | 0.69 | 0.42 | 30 | -36 | 27.3 |
| O7 | nyam | q50_H75 | 452 | 0.58 | 0.32 | 205 | 91 | 20.5 |
| O7 | nyam | q60_H75 | 452 | 0.37 | 0.31 | 156 | 118 | 16.9 |
| O7 | nyam | q75_H75 | 452 | 0.08 | 0.20 | -192 | -145 | 9.5 |
| O7 | nyam | rem_own_k0.75 | 452 | 0.31 | 0.30 | 120 | 82 | 20.6 |
| P7 | asia | q50_H75 | 2161 | 0.29 | 0.46 | 391 | 341 | 10.2 |
| P7 | asia | q60_H75 | 2161 | 0.16 | 0.48 | 487 | 484 | 9.3 |
| P7 | asia | q75_H75 | 2161 | 0.02 | 0.55 | 1227 | 969 | 5.7 |
| P7 | asia | rem_own_k0.75 | 2161 | 0.70 | 0.44 | 447 | 130 | 26.6 |
| P7 | london | q50_H75 | 1537 | 0.62 | 0.38 | 74 | 27 | 10.0 |
| P7 | london | q60_H75 | 1537 | 0.41 | 0.38 | 67 | 36 | 7.8 |
| P7 | london | q75_H75 | 1537 | 0.15 | 0.41 | 124 | 59 | 5.3 |
| P7 | london | rem_own_k0.75 | 1537 | 0.72 | 0.37 | -19 | -13 | 23.8 |
| P7 | nyam | q50_H75 | 1050 | 0.72 | 0.38 | 38 | 150 | 13.2 |
| P7 | nyam | q60_H75 | 1050 | 0.48 | 0.37 | -7 | 28 | 10.9 |
| P7 | nyam | q75_H75 | 1050 | 0.15 | 0.33 | -88 | -96 | 13.3 |
| P7 | nyam | rem_own_k0.75 | 1050 | 0.71 | 0.37 | -43 | 67 | 33.2 |
| U7 | asia | q50_H75 | 686 | 0.28 | 0.54 | 412 | 320 | 10.4 |
| U7 | asia | q60_H75 | 686 | 0.15 | 0.50 | 322 | 270 | 8.0 |
| U7 | asia | q75_H75 | 686 | 0.03 | 0.47 | -260 | -383 | 6.8 |
| U7 | asia | rem_own_k0.75 | 686 | 0.74 | 0.53 | 375 | 4 | 30.5 |
| U7 | london | q50_H75 | 645 | 0.27 | 0.46 | -102 | -183 | 8.7 |
| U7 | london | q60_H75 | 645 | 0.13 | 0.46 | -173 | -182 | 7.8 |
| U7 | london | q75_H75 | 645 | 0.03 | 0.50 | -396 | -466 | 5.4 |
| U7 | london | rem_own_k0.75 | 645 | 0.68 | 0.51 | 166 | 14 | 24.5 |

### Exact cap cells (global: all books at once; L3M, L6M when promoted; delta vs JN05W2)
| cell | L3M | L6M | HOLD | d mean/wk at $4.84 L3M |
|---|---|---|---|---|
| quantile 50 cap, horizon = 75th-percentile holding time | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | +1452 (lots +9/wk) |
| quantile 60 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 75 cap, horizon = 75th-percentile holding time | +177 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 101%, w2l 0 | n/a | n/a | +176 (lots +0/wk) |
| quantile 90 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 60 cap, horizon = median holding time | -1554 $/wk, DD +2.5%, ww +1445, stops 10.42(10.35), b5 89%, w2l 1 | n/a | n/a | -1658 (lots +29/wk) |
| quantile 75 cap, horizon = median holding time | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=0.5 | -8393 $/wk, DD +2.1%, ww +5889, stops 7.76(10.35), b5 57%, w2l 3 | n/a | n/a | -8805 (lots +113/wk) |
| remaining-range cap, forecast own 20-session mean, k=0.75 | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=1.0 | -6226 $/wk, DD +27.0%, ww +12290, stops 8.98(10.35), b5 66%, w2l 2 | n/a | n/a | -6458 (lots +63/wk) |
| remaining-range cap, forecast own 20-session mean, k=1.25 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.5 | -10795 $/wk, DD +40.3%, ww +11430, stops 7.00(10.35), b5 51%, w2l 4 | n/a | n/a | -11257 (lots +126/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.75 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.0 | -7259 $/wk, DD +39.4%, ww +17319, stops 7.76(10.35), b5 65%, w2l 2 | n/a | n/a | -7570 (lots +85/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.25 | pending | | | |
| EV-best target, bounded by the book target | -14326 $/wk, DD -25.6%, ww -15613, stops 8.45(10.35), b5 46%, w2l 3 | n/a | n/a | -14639 (lots +86/wk) |
| EV-best target, unbounded | pending | | | |
| extension m=1.0 | -110 $/wk, DD -53.4%, ww -2988, stops 11.72(10.35), b5 124%, w2l 2 | n/a | n/a | -18 (lots -25/wk) |
| extension m=1.5 | pending | | | |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts skipped | +1443 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | n/a | n/a | +1410 (lots +9/wk) |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts at half size | pending | | | |
| PLANTED-EDGE CHECK (look-ahead oracle 0.9 x realised MFE, not a result) | +85531 $/wk, DD +67.0%, ww +64263, stops 6.54(10.35), b5 259%, w2l 0 | n/a | n/a | +85219 (lots +85/wk) |
| PLANTED-EDGE CHECK (oracle 0.6 x realised MFE, not a result) | pending | | | |
| PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 | n/a | -125 (lots +1/wk) |
| PLACEBO pl23: quantile 50 cap, horizon = 75th-percentile holding time | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 | n/a | -871 (lots +3/wk) |
| PLACEBO pl37: quantile 50 cap, horizon = 75th-percentile holding time | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 | n/a | -612 (lots +2/wk) |
| PLACEBO plR1: quantile 50 cap, horizon = 75th-percentile holding time | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 | n/a | -670 (lots +4/wk) |

### The one candidate: forecast-quantile-50 cap, horizon = 75th-percentile holding time (L3M mean-only so far): all windows, W44 removed, placebos
| window | scope all | W44 removed |
|---|---|---|
| L3M | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 |
| L6M | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 |
| HOLD | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 |
| MID | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 |
| PREUW | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 |
Placebos (same cap, forecast features taken n sessions earlier at the same clock / a random earlier session), L3M then L6M when run:
| placebo | L3M | L6M |
|---|---|---|
| pl11 | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 |
| pl23 | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 |
| pl37 | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 |
| plR1 | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 |

### Per book x session exact cap cells (clean: one book in one session)
| slice | cap | L3M | May-Jul |
|---|---|---|---|
| A7 asia | quantile 50 cap, horizon = 75th-percentile holding time | -17 (live -30; $4.84 -17) DD +0.0% ww +0 stops 4.03(4.03) | n/a |

### FOR THE LIVE BUILD (what D7 computes at the signal second)
From its own 1-minute bars: last 15/30/60/120-minute range and realised vol, same-offset range over the previous 20 sessions (median), session ranges of the last 5/20 sessions, range so far, the entry position in the session range (favourable-side room), elapsed fraction of the session, ln of the book-session horizon; a small coefficient table per session (15 weights, mean, sd, intercept, four residual quantile offsets) refit every 14 days and shipped as a static file. Cap = min(60, price x exp(prediction + quantile offset) - 2); orders: the target limit is placed at the capped price. The remaining-range version needs the HAR session forecast (T-RANGE2 file) or D7 computes its own 20-session mean. No intraday feed from the box.


## Per book and session, clean, and the assembled stack
**STATUS (plain, not a PASS; B1 in progress, no "nothing passes" verdict is allowed until it is done): single-book single-session cells scored in L3M for 15 of 14 slices; slice picks so far: {}.**

Method (user order PART B, 2026-11-15): each cell = the Dial 10 hook restricted to ONE book in ONE session (every other book/session unchanged at JN05W2), exact engine, all layers ON, live caps. Dollars are BASE lots; the x1.75 live figure sits beside each headline (live); the $4.84 figure reprices every contract at the FEES.md $4.84 RT (engine raw $1.18). Compared on the same book x session slice of JN05W2 (day locks/caps still interact across books, which is why the cells are run for real and not sliced from the global run). B1a settings per slice: direction both / narrow-only / wide-only x gearing 0.5 / 1.0 at the 75th-percentile horizon, plus narrow/wide g1.0 at the median horizon; "fixed" = JN05W2 itself. Walk-forward: the pick for each slice is made on 2026-05..07 only (older than L3M); L3M (2026-08..10) is then out-of-sample. B1b (around each pick): lots cap 1.5/3, lots follow half the change, dead band 0/20%, target ratio 0.8/1.2, lever stop-only (sl: stop W, lots inverse, target in the same points) / target-only (tg) / size-only (sz: bracket fixed, lots follow the forecast), noise floor k = 3/4/5 x recent 5-minute ATR (bracket never narrower), clips 25..120 / 20..150.

### B1 table: per slice, every cell (L3M, delta vs JN05W2 same slice; May-Jul = the selection window)
| slice | setting | May-Jul (selection) | L3M (out of sample) | L6M |
|---|---|---|---|---|
| A7 asia | both/g1.0/H75 | -374 (live -654; $4.84 -370) DD -10.9% ww -261 stops 2.97(3.88) | +47 (live +83; $4.84 +40) DD +25.6% ww +1495 stops 5.55(4.03) | -163 (live -286; $4.84 -165) DD -29.2% ww +1253 stops 4.26(3.96) |
| A7 asia | narrow/g1.0/H75 | -419 (live -733; $4.84 -423) DD -0.6% ww -175 stops 4.49(3.88) | -18 (live -32; $4.84 -26) DD +17.7% ww +722 stops 5.63(4.03) | -219 (live -383; $4.84 -224) DD -19.1% ww +722 stops 5.06(3.96) |
| A7 asia | both/g0.5/H75 | -556 (live -973; $4.84 -553) DD -9.2% ww +72 stops 3.50(3.88) | -192 (live -336; $4.84 -195) DD +10.1% ww +412 stops 5.10(4.03) | -374 (live -654; $4.84 -374) DD -36.6% ww +412 stops 4.30(3.96) |
| A7 asia | narrow/g0.5/H75 | -350 (live -612; $4.84 -352) DD +0.0% ww +0 stops 4.34(3.88) | -186 (live -325; $4.84 -189) DD +10.0% ww +552 stops 5.10(4.03) | -268 (live -469; $4.84 -270) DD -15.8% ww +552 stops 4.72(3.96) |
| A7 asia | wide/g1.0/H75 | +19 (live +33; $4.84 +26) DD -10.9% ww +283 stops 2.51(3.88) | -15 (live -26; $4.84 -14) DD +2.4% ww -426 stops 3.96(4.03) | +2 (live +3; $4.84 +6) DD -13.6% ww -426 stops 3.23(3.96) |
| A7 asia | wide/g0.5/H75 | n/a | -1 (live -1; $4.84 -1) DD +1.4% ww -140 stops 4.03(4.03) | n/a |
| A7 asia | wide/g1.0/H50 | n/a | -48 (live -85; $4.84 -48) DD -3.0% ww -426 stops 3.88(4.03) | n/a |
| A7 asia | narrow/g1.0/H50 | n/a | -159 (live -279; $4.84 -171) DD -8.3% ww +877 stops 5.93(4.03) | n/a |
| H7 asia | wide/g0.5/H75 | n/a | +123 (live +215; $4.84 +123) DD +0.0% ww +0 stops 0.23(0.23) | n/a |
| H7 asia | wide/g1.0/H75 | n/a | -67 (live -118; $4.84 -67) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | wide/g1.0/H50 | n/a | -312 (live -546; $4.84 -312) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | both/g0.0/H50 | -1623 (live -2840; $4.84 -1619) DD +11.0% ww +3643 stops 0.46(0.61) | -972 (live -1701; $4.84 -967) DD -31.5% ww +0 stops 0.46(0.23) | -1298 (live -2271; $4.84 -1293) DD +11.0% ww +3643 stops 0.46(0.42) |
| H7 asia | both/g1.0/H75 | +1123 (live +1965; $4.84 +1129) DD +6.5% ww +1483 stops 0.53(0.61) | +177 (live +309; $4.84 +163) DD -33.6% ww -1228 stops 0.61(0.23) | +650 (live +1137; $4.84 +646) DD +6.5% ww +1483 stops 0.57(0.42) |
| H7 asia | narrow/g1.0/H75 | n/a | +244 (live +427; $4.84 +230) DD -33.6% ww -1228 stops 0.53(0.23) | n/a |
| H7 asia | both/g0.5/H75 | n/a | -574 (live -1004; $4.84 -580) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g0.5/H75 | n/a | -697 (live -1219; $4.84 -703) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g1.0/H50 | n/a | -355 (live -621; $4.84 -372) DD -120.5% ww -2166 stops 0.53(0.23) | n/a |
| H7 nyam | narrow/g1.0/H50 | n/a | +252 (live +441; $4.84 +252) DD +60.4% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | both/g1.0/H75 | n/a | +281 (live +491; $4.84 +280) DD +57.7% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | narrow/g1.0/H75 | -187 (live -328; $4.84 -188) DD -4.0% ww +0 stops 0.53(0.46) | +258 (live +452; $4.84 +258) DD +57.7% ww +480 stops 0.30(0.38) | +35 (live +62; $4.84 +35) DD +24.1% ww +480 stops 0.42(0.42) |
| H7 nyam | both/g0.0/H50 | -58 (live -102; $4.84 -58) DD +9.4% ww +0 stops 0.46(0.46) | +221 (live +387; $4.84 +221) DD +54.7% ww +195 stops 0.15(0.38) | +82 (live +143; $4.84 +81) DD +33.9% ww +195 stops 0.30(0.42) |
| H7 nyam | both/g0.5/H75 | +103 (live +180; $4.84 +103) DD +29.2% ww -83 stops 0.46(0.46) | +87 (live +153; $4.84 +87) DD +2.2% ww +195 stops 0.38(0.38) | +95 (live +167; $4.84 +95) DD +2.2% ww +195 stops 0.42(0.42) |
| H7 nyam | narrow/g0.5/H75 | n/a | +77 (live +134; $4.84 +77) DD +2.2% ww +195 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g0.5/H75 | n/a | +11 (live +19; $4.84 +11) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H75 | n/a | +22 (live +39; $4.84 +22) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H50 | n/a | +30 (live +53; $4.84 +30) DD +0.0% ww +0 stops 0.30(0.38) | n/a |
| K7 asia | wide/g1.0/H75 | n/a | +297 (live +520; $4.84 +298) DD +0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | wide/g0.5/H75 | n/a | -54 (live -94; $4.84 -54) DD -0.7% ww -404 stops 0.00(0.00) | n/a |
| K7 asia | narrow/g0.5/H75 | n/a | +1877 (live +3285; $4.84 +1855) DD -19.6% ww -2412 stops 0.00(0.00) | n/a |
| K7 asia | both/g0.5/H75 | n/a | +1823 (live +3191; $4.84 +1801) DD -28.8% ww -3232 stops 0.00(0.00) | n/a |
| K7 asia | wide/g1.0/H50 | n/a | -401 (live -702; $4.84 -400) DD -35.9% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | both/g1.0/H75 | n/a | +1292 (live +2261; $4.84 +1220) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H75 | n/a | +912 (live +1595; $4.84 +838) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H50 | n/a | +355 (live +621; $4.84 +268) DD -86.2% ww -5644 stops 0.00(0.00) | n/a |
| K7 london | both/g0.5/H75 | n/a | -9 (live -15; $4.84 -14) DD +8.7% ww +4326 stops 0.23(0.30) | n/a |
| K7 london | wide/g0.5/H75 | n/a | +27 (live +48; $4.84 +29) DD +0.5% ww +0 stops 0.30(0.30) | n/a |
| K7 london | wide/g1.0/H50 | n/a | +431 (live +755; $4.84 +433) DD -3.3% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g0.5/H75 | n/a | -123 (live -215; $4.84 -130) DD -4.2% ww +4733 stops 0.23(0.30) | n/a |
| K7 london | wide/g1.0/H75 | n/a | +157 (live +274; $4.84 +160) DD -4.8% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g1.0/H50 | n/a | -182 (live -319; $4.84 -204) DD -13.7% ww +3097 stops 0.23(0.30) | n/a |
| K7 london | both/g1.0/H75 | n/a | +481 (live +841; $4.84 +462) DD -25.5% ww +4257 stops 0.38(0.30) | n/a |
| K7 london | narrow/g1.0/H75 | n/a | -31 (live -55; $4.84 -55) DD -42.3% ww +4122 stops 0.38(0.30) | n/a |
| K7 nyam | both/g0.0/H50 | -488 (live -855; $4.84 -488) DD -38.7% ww -514 stops 0.08(0.08) | +1078 (live +1886; $4.84 +1069) DD +53.9% ww +1605 stops 0.00(0.00) | +295 (live +516; $4.84 +290) DD +50.6% ww +1605 stops 0.04(0.04) |
| K7 nyam | narrow/g1.0/H50 | n/a | +769 (live +1345; $4.84 +761) DD +51.0% ww +2185 stops 0.00(0.00) | n/a |
| K7 nyam | both/g1.0/H75 | n/a | +1160 (live +2030; $4.84 +1153) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g1.0/H75 | n/a | +984 (live +1722; $4.84 +977) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g0.5/H75 | n/a | +668 (live +1170; $4.84 +667) DD +40.3% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | both/g0.5/H75 | n/a | +806 (live +1410; $4.84 +805) DD +39.5% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H75 | n/a | +176 (live +308; $4.84 +176) DD -0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H50 | n/a | +252 (live +441; $4.84 +253) DD -0.3% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g0.5/H75 | n/a | +137 (live +241; $4.84 +137) DD -0.8% ww +0 stops 0.00(0.00) | n/a |
| K7 nypm | wide/g1.0/H50 | n/a | +442 (live +773; $4.84 +442) DD +17.3% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | wide/g1.0/H75 | n/a | +70 (live +122; $4.84 +70) DD +13.1% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | both/g1.0/H75 | n/a | -184 (live -322; $4.84 -197) DD +9.8% ww +1145 stops 0.15(0.08) | n/a |
| K7 nypm | wide/g0.5/H75 | n/a | -4 (live -8; $4.84 -4) DD -1.5% ww -38 stops 0.00(0.08) | n/a |
| K7 nypm | narrow/g1.0/H50 | n/a | +48 (live +84; $4.84 +32) DD -1.9% ww +105 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g1.0/H75 | n/a | -254 (live -445; $4.84 -267) DD -3.3% ww +990 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g0.5/H75 | n/a | -266 (live -465; $4.84 -269) DD -26.7% ww +140 stops 0.08(0.08) | n/a |
| K7 nypm | both/g0.5/H75 | n/a | -270 (live -473; $4.84 -274) DD -27.3% ww +102 stops 0.00(0.08) | n/a |
| M7 london | wide/g1.0/H75 | n/a | +1614 (live +2824; $4.84 +1616) DD +4.9% ww +1190 stops 0.53(0.91) | n/a |
| M7 london | wide/g0.5/H75 | n/a | +688 (live +1204; $4.84 +689) DD +4.4% ww +1400 stops 0.84(0.91) | n/a |
| M7 london | wide/g1.0/H50 | n/a | +538 (live +942; $4.84 +540) DD -1.3% ww -80 stops 0.84(0.91) | n/a |
| M7 london | both/g0.5/H75 | n/a | +1147 (live +2008; $4.84 +1139) DD -8.1% ww +130 stops 1.07(0.91) | n/a |
| M7 london | narrow/g0.5/H75 | n/a | +417 (live +730; $4.84 +408) DD -10.9% ww -1075 stops 1.14(0.91) | n/a |
| M7 london | narrow/g1.0/H50 | n/a | +476 (live +833; $4.84 +446) DD -19.9% ww +1144 stops 1.45(0.91) | n/a |
| M7 london | narrow/g1.0/H75 | n/a | -366 (live -640; $4.84 -390) DD -20.4% ww +80 stops 1.29(0.91) | n/a |
| M7 london | both/g1.0/H75 | n/a | +1142 (live +1999; $4.84 +1121) DD -23.2% ww -729 stops 0.91(0.91) | n/a |
| M7 nyam | narrow/g1.0/H50 | n/a | +439 (live +769; $4.84 +424) DD +26.0% ww -222 stops 0.38(0.23) | n/a |
| M7 nyam | both/g0.5/H75 | n/a | +79 (live +138; $4.84 +75) DD +0.8% ww +194 stops 0.30(0.23) | n/a |
| M7 nyam | narrow/g0.5/H75 | n/a | +73 (live +127; $4.84 +69) DD +0.8% ww +194 stops 0.38(0.23) | n/a |
| M7 nyam | wide/g0.5/H75 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H75 | n/a | +16 (live +28; $4.84 +16) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H50 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | both/g1.0/H75 | n/a | +419 (live +733; $4.84 +405) DD -6.8% ww -991 stops 0.46(0.23) | n/a |
| M7 nyam | narrow/g1.0/H75 | n/a | +402 (live +704; $4.84 +388) DD -6.8% ww -991 stops 0.53(0.23) | n/a |
| P7 asia | both/g0.0/H50 | -5189 (live -9081; $4.84 -4987) DD +44.9% ww +11844 stops 0.00(0.00) | -703 (live -1230; $4.84 -620) DD +51.2% ww +20259 stops 0.08(0.15) | -2946 (live -5156; $4.84 -2804) DD +51.2% ww +17717 stops 0.04(0.08) |
| P7 asia | narrow/g1.0/H50 | n/a | -3918 (live -6857; $4.84 -4186) DD -0.4% ww -4286 stops 0.46(0.15) | n/a |
| P7 asia | both/g0.5/H75 | n/a | -5946 (live -10406; $4.84 -6044) DD -1.0% ww +6944 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g0.5/H75 | n/a | -5762 (live -10084; $4.84 -5860) DD -1.0% ww +9022 stops 0.15(0.15) | n/a |
| P7 asia | wide/g0.5/H75 | n/a | -184 (live -322; $4.84 -183) DD -4.9% ww -2079 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g1.0/H75 | n/a | -2696 (live -4718; $4.84 -2882) DD -7.8% ww -10346 stops 0.53(0.15) | n/a |
| P7 asia | wide/g1.0/H50 | n/a | -816 (live -1428; $4.84 -812) DD -22.6% ww -9033 stops 0.15(0.15) | n/a |
| P7 asia | wide/g1.0/H75 | n/a | -491 (live -858; $4.84 -490) DD -25.2% ww -10331 stops 0.15(0.15) | n/a |
| P7 asia | both/g1.0/H75 | n/a | -3315 (live -5802; $4.84 -3501) DD -36.1% ww -13164 stops 0.53(0.15) | n/a |
| P7 london | both/g0.5/H75 | n/a | +894 (live +1565; $4.84 +886) DD +29.6% ww -1633 stops 0.08(0.08) | n/a |
| P7 london | narrow/g0.5/H75 | n/a | +386 (live +675; $4.84 +375) DD +28.5% ww -1328 stops 0.08(0.08) | n/a |
| P7 london | narrow/g1.0/H50 | n/a | +927 (live +1622; $4.84 +895) DD +19.7% ww -3009 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H75 | n/a | -142 (live -249; $4.84 -138) DD +2.7% ww -458 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H50 | n/a | +265 (live +464; $4.84 +266) DD +1.1% ww +0 stops 0.08(0.08) | n/a |
| P7 london | wide/g0.5/H75 | n/a | +385 (live +674; $4.84 +387) DD -1.9% ww -238 stops 0.08(0.08) | n/a |
| P7 london | both/g1.0/H75 | n/a | +1179 (live +2064; $4.84 +1145) DD -9.8% ww -5408 stops 0.15(0.08) | n/a |
| P7 london | narrow/g1.0/H75 | n/a | +1322 (live +2313; $4.84 +1282) DD -14.4% ww -5203 stops 0.15(0.08) | n/a |
| P7 nyam | both/g1.0/H75 | n/a | +697 (live +1220; $4.84 +685) DD +51.3% ww +354 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g1.0/H75 | n/a | +543 (live +951; $4.84 +529) DD +45.9% ww +324 stops 0.30(0.38) | n/a |
| P7 nyam | both/g0.5/H75 | n/a | +105 (live +184; $4.84 +99) DD +36.7% ww +238 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g0.5/H75 | n/a | -13 (live -23; $4.84 -20) DD +36.4% ww +262 stops 0.30(0.38) | n/a |
| P7 nyam | wide/g0.5/H75 | n/a | +118 (live +207; $4.84 +119) DD +0.3% ww -25 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H75 | n/a | +16 (live +27; $4.84 +17) DD -7.5% ww -105 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H50 | n/a | -544 (live -952; $4.84 -543) DD -47.7% ww -3348 stops 0.38(0.38) | n/a |
| U7 asia | narrow/g1.0/H50 | n/a | +1222 (live +2139; $4.84 +1201) DD +15.6% ww -265 stops 1.90(1.83) | n/a |
| U7 asia | both/g1.0/H75 | n/a | +71 (live +124; $4.84 +56) DD +8.3% ww -1836 stops 1.98(1.83) | n/a |
| U7 asia | narrow/g1.0/H75 | n/a | +502 (live +879; $4.84 +487) DD +8.3% ww +983 stops 1.98(1.83) | n/a |
| U7 asia | both/g0.5/H75 | n/a | -800 (live -1399; $4.84 -808) DD +6.6% ww -2883 stops 2.05(1.83) | n/a |
| U7 asia | narrow/g0.5/H75 | n/a | -162 (live -284; $4.84 -170) DD +6.6% ww +57 stops 2.05(1.83) | n/a |
| U7 asia | wide/g0.5/H75 | n/a | -637 (live -1115; $4.84 -637) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H75 | n/a | -431 (live -755; $4.84 -431) DD +0.0% ww -1836 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H50 | n/a | -648 (live -1134; $4.84 -648) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 london | narrow/g0.5/H75 | n/a | +393 (live +687; $4.84 +392) DD +17.2% ww +1796 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H75 | n/a | +246 (live +431; $4.84 +243) DD +3.1% ww -1185 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H50 | n/a | -41 (live -72; $4.84 -48) DD -9.9% ww -1991 stops 1.52(1.45) | n/a |
| U7 london | both/g0.5/H75 | n/a | -891 (live -1560; $4.84 -890) DD -25.4% ww -3538 stops 1.52(1.45) | n/a |
| U7 london | wide/g1.0/H50 | n/a | -839 (live -1468; $4.84 -837) DD -33.9% ww -4122 stops 1.37(1.45) | n/a |
| U7 london | wide/g0.5/H75 | n/a | -1284 (live -2247; $4.84 -1282) DD -44.3% ww -6280 stops 1.52(1.45) | n/a |
| U7 london | both/g1.0/H75 | n/a | -1728 (live -3025; $4.84 -1729) DD -105.5% ww -7540 stops 1.60(1.45) | n/a |
| U7 london | wide/g1.0/H75 | n/a | -1975 (live -3455; $4.84 -1972) DD -109.8% ww -6355 stops 1.60(1.45) | n/a |

### Summary per slice: pick made on May-Jul, result on L3M
| slice | pick | L3M result of the pick | verdict |
|---|---|---|---|
| A7 asia | pending | | |
| H7 asia | pending | | |
| H7 nyam | pending | | |
| K7 asia | pending | | |
| K7 london | pending | | |
| K7 nyam | pending | | |
| K7 nypm | pending | | |
| M7 london | pending | | |
| M7 nyam | pending | | |
| P7 asia | pending | | |
| P7 london | pending | | |
| P7 nyam | pending | | |
| U7 asia | pending | | |
| U7 london | pending | | |

### B2: why the global version adds full stops (narrow-only/both g1.0 H75 cell, L3M, trade tables)
Reference JN05W2 L3M (no O7): 1855 trades, stop rate 0.071, 132 stops (13 weeks).

**M1_75_g10_c1_d10_c20_tb_B**: 2038 trades (+183 vs JN05W2), stops 173 (+41), stop rate 0.085 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 437 | 0.103 | 3.05 | 94 |
| (40, 50] | 721 | 0.074 | 2.36 | 271 |
| (50, 55] | 232 | 0.099 | 1.97 | 169 |
| (55, 60] | 435 | 0.076 | 1.87 | 76 |
| (60, 70] | 75 | 0.120 | 2.01 | -385 |
| (70, 80] | 62 | 0.048 | 1.68 | -284 |
| (80, 101] | 76 | 0.092 | 1.13 | -591 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1543 | 0.069 | 2.21 | 54 |
| (3.0, 4.0] | 294 | 0.116 | 2.29 | 239 |
| (4.0, 5.0] | 74 | 0.108 | 2.31 | 364 |
| (5.0, 6.0] | 6 | 0.167 | 2.50 | 172 |
| (6.0, 8.0] | 4 | 0.000 | 1.00 | -119 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1068 | 0.096 | 1.00 | 4 |
| (1, 2] | 385 | 0.078 | 2.00 | 115 |
| (2, 3] | 215 | 0.093 | 3.00 | 23 |
| (3, 5] | 195 | 0.062 | 4.46 | 256 |
| (5, 8] | 138 | 0.065 | 6.70 | 690 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

**M1_75_g10_c1_d10_c20_tb_N**: 2072 trades (+217 vs JN05W2), stops 178 (+46), stop rate 0.086 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 449 | 0.105 | 3.02 | 97 |
| (40, 50] | 725 | 0.073 | 2.35 | 272 |
| (50, 55] | 236 | 0.102 | 1.97 | 150 |
| (55, 60] | 662 | 0.082 | 1.82 | -29 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1644 | 0.072 | 2.18 | 50 |
| (3.0, 4.0] | 264 | 0.121 | 2.38 | 348 |
| (4.0, 5.0] | 44 | 0.091 | 3.11 | 1063 |
| (5.0, 6.0] | 3 | 0.000 | 3.33 | 68 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1073 | 0.095 | 1.00 | 8 |
| (1, 2] | 413 | 0.085 | 2.00 | 117 |
| (2, 3] | 197 | 0.081 | 3.00 | 213 |
| (3, 5] | 217 | 0.074 | 4.43 | 196 |
| (5, 8] | 135 | 0.067 | 6.74 | 714 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

Reading of the W/ATR5 table: ATR5 = mean range of the last 14 five-minute buckets in points; a bracket 3x ATR5 or less is within ordinary 5-minute noise. The noise-floor cells (floor 3/4/5 x ATR5, narrowing only) are listed in B3.


### B3: levers (stop-only / target-only / both / size-only) and noise floor, per slice
| slice | cell | L3M | May-Jul |
|---|---|---|---|

### B4: assembled stack (each slice at its own walk-forward pick, run together)
(not run yet: starts when every slice has a pick)


## Target capped at the forecast
**VERDICT (plain, not a PASS; FIRST PASS; 15 of 26 global exact cap cells scored in L3M, per book x session exact cells still running): planted-edge check PASSED through the exact engine (look-ahead oracle target 0.9 x realised MFE: +85531 $/wk, DD +67.0%, ww +64263; this is a mechanism check, NOT a result); the reachable move is only weakly forecastable (R2 on ln MFE 0.03-0.14, quantile calibration good); in the exact L3M cells the cap at the forecast 50th-percentile move (horizon = 75th-percentile holding time) gives +1486 $/wk, DD -0.5%, ww -240 and the 75th-percentile cap +177 $/wk, DD +0.0%, ww +0, the remaining-range caps cut drawdown (own k1.0 -6226 $/wk, DD +27.0%, ww +12290; HAR k1.0 -7259 $/wk, DD +39.4%, ww +17319) but cost thousands per week. Best exact L3M cap cell inside the mean gate by DD: PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time (DD +7.9%, -120 $/wk). L6M/HOLD/older still to run before any verdict.**

Planted-edge check (H1) for the capping mechanism: cells `tcoracle0.9` / `0.6` set the target to 0.9 / 0.6 x the REALISED maximum favourable move (look-ahead, only to prove the mechanism can show an edge through the exact engine); they must come out strongly positive. Status below in the exact table. Until they do, an exact cap verdict is not stated.

Definition. Reachable move = maximum favourable excursion from the signal-second bar close over the book-session holding horizon H (H50/H75 = median / 75th percentile holding time of that book+session, causal), points. Model: walk-forward ridge (14-day blocks, expanding, min 90 days, per session) on ln((MFE+2)/price) from the Dial 10 own-bar inputs (last 15/30/60/120 min range and vol, same-clock normal, own session level, range used so far, elapsed fraction) plus the side-aware room in the session range so far; quantiles q = fitted + empirical training-residual quantile (50/60/75/90). Cap: target = min(book target 60 pts [58 after fills], q-quantile), stop, lots and every other level unchanged. Remaining-range cap: target = min(book target, k x (session range forecast - range printed so far)), forecast = own (price x exp(sf20), mean of the last 20 sessions) or T-RANGE2 HAR (fc_r2_har, available-epoch checked). Small caps (< 30 pts = 0.5 x stop): take / skip / half. EV target: argmax over T in [20, book target or 300] of T x P(MFE>=T) - stop x (1-P) with the lognormal forecast (ignores the stop-first ordering, so optimistic). Extension: if the forecast median MFE is >= m x book target, target = min(q50, 2 x book target). Lots/base basis: dollars are BASE lots (live x1.75 = multiply by 1.75); fee columns $4.84 beside raw $1.18 where shown.

### Item 1: calibration of the forecast quantiles (share of trades whose realized MFE exceeded the forecast quantile; a q-quantile should be exceeded 1-q of the time = 0.50 / 0.40 / 0.25 / 0.10) and R2 of ln MFE, per session
| H | session | window | n | >q50 | >q60 | >q75 | >q90 | R2 ln MFE | median q75 (pts) | share q75 < 60 |
|---|---|---|---|---|---|---|---|---|---|---|
| 50 | asia | older (<2026-05) | 5119 | 0.51 | 0.41 | 0.26 | 0.12 | 0.121 | 80 | 0.222 |
| 50 | asia | L6M | 2006 | 0.49 | 0.38 | 0.23 | 0.08 | 0.058 | 111 | 0.047 |
| 50 | asia | L3M | 875 | 0.46 | 0.34 | 0.20 | 0.07 | -0.014 | 90 | 0.098 |
| 50 | london | older (<2026-05) | 4892 | 0.51 | 0.41 | 0.26 | 0.11 | 0.142 | 62 | 0.438 |
| 50 | london | L6M | 1406 | 0.48 | 0.37 | 0.23 | 0.08 | 0.028 | 76 | 0.166 |
| 50 | london | L3M | 673 | 0.48 | 0.37 | 0.24 | 0.07 | -0.008 | 68 | 0.247 |
| 50 | nyam | older (<2026-05) | 4142 | 0.47 | 0.38 | 0.24 | 0.11 | 0.077 | 63 | 0.397 |
| 50 | nyam | L6M | 600 | 0.51 | 0.40 | 0.24 | 0.09 | 0.097 | 83 | 0.157 |
| 50 | nyam | L3M | 271 | 0.51 | 0.38 | 0.20 | 0.06 | 0.077 | 68 | 0.258 |
| 50 | nypm | older (<2026-05) | 817 | 0.48 | 0.40 | 0.26 | 0.13 | 0.073 | 62 | 0.419 |
| 50 | nypm | L6M | 150 | 0.59 | 0.50 | 0.33 | 0.13 | 0.221 | 71 | 0.307 |
| 50 | nypm | L3M | 56 | 0.50 | 0.36 | 0.21 | 0.09 | 0.104 | 54 | 0.589 |
| 50 | all | older (<2026-05) | 14970 | 0.50 | 0.40 | 0.26 | 0.12 | 0.123 | 68 | 0.352 |
| 50 | all | L6M | 4162 | 0.49 | 0.38 | 0.23 | 0.08 | 0.080 | 91 | 0.113 |
| 50 | all | L3M | 1875 | 0.47 | 0.36 | 0.21 | 0.07 | 0.014 | 76 | 0.189 |
| 75 | asia | older (<2026-05) | 5119 | 0.52 | 0.41 | 0.26 | 0.12 | 0.134 | 122 | 0.032 |
| 75 | asia | L6M | 2006 | 0.50 | 0.40 | 0.24 | 0.08 | 0.027 | 178 | 0.000 |
| 75 | asia | L3M | 875 | 0.45 | 0.35 | 0.20 | 0.05 | -0.016 | 156 | 0.000 |
| 75 | london | older (<2026-05) | 4891 | 0.51 | 0.42 | 0.27 | 0.11 | 0.157 | 101 | 0.100 |
| 75 | london | L6M | 1406 | 0.49 | 0.37 | 0.21 | 0.08 | 0.069 | 118 | 0.001 |
| 75 | london | L3M | 673 | 0.49 | 0.38 | 0.21 | 0.09 | 0.025 | 108 | 0.000 |
| 75 | nyam | older (<2026-05) | 4142 | 0.48 | 0.38 | 0.23 | 0.10 | 0.065 | 91 | 0.081 |
| 75 | nyam | L6M | 600 | 0.50 | 0.40 | 0.24 | 0.10 | 0.098 | 125 | 0.015 |
| 75 | nyam | L3M | 271 | 0.44 | 0.34 | 0.19 | 0.05 | 0.051 | 103 | 0.015 |
| 75 | nypm | older (<2026-05) | 812 | 0.49 | 0.37 | 0.26 | 0.11 | 0.043 | 87 | 0.095 |
| 75 | nypm | L6M | 150 | 0.53 | 0.46 | 0.34 | 0.17 | 0.179 | 117 | 0.013 |
| 75 | nypm | L3M | 56 | 0.41 | 0.30 | 0.21 | 0.07 | -0.076 | 93 | 0.036 |
| 75 | all | older (<2026-05) | 14964 | 0.51 | 0.40 | 0.25 | 0.11 | 0.131 | 102 | 0.071 |
| 75 | all | L6M | 4162 | 0.50 | 0.39 | 0.23 | 0.09 | 0.079 | 149 | 0.003 |
| 75 | all | L3M | 1875 | 0.46 | 0.36 | 0.20 | 0.06 | 0.032 | 128 | 0.003 |

### Items 3 and 4 (and 2): offline replay of the caps on the JN05W2 trade paths, all 43 months (estimate: 1-min paths, cap counted only before the exit bar, so cut/stop ordering is conservative; the exact cells below decide). d mean $/wk and DD cut % vs JN05W2 on the same trades, scope all, then per session for the cap with the most trades capped
| cap | small-cap rule | scope | window | d mean $/wk (live x1.75) | DD cut % | d worst week | d stops/wk | share capped | share where cap hit |
|---|---|---|---|---|---|---|---|---|---|
| q50_H50 | take | all | L3M | +409 (+715) | -3.9 | -1411 | +0.00 | 0.82 | 0.45 |
| q50_H50 | take | all | L6M | -96 (-169) | -3.9 | -1411 | +0.00 | 0.62 | 0.33 |
| q50_H50 | take | all | OLDER | -1795 (-3141) | +12.0 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | skip | all | L3M | -1581 (-2767) | -5.0 | -1996 | +0.00 | 0.82 | 0.45 |
| q50_H50 | skip | all | L6M | -1445 (-2528) | -5.0 | -1996 | +0.00 | 0.62 | 0.33 |
| q50_H50 | skip | all | OLDER | -2271 (-3975) | +17.4 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | half | all | L3M | -586 (-1026) | -4.4 | -1704 | +0.00 | 0.82 | 0.45 |
| q50_H50 | half | all | L6M | -771 (-1348) | -4.4 | -1704 | +0.00 | 0.62 | 0.33 |
| q50_H50 | half | all | OLDER | -2033 (-3558) | +16.5 | +13127 | +0.00 | 0.80 | 0.45 |
| q60_H50 | take | all | L3M | -1525 (-2668) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | take | all | L6M | -839 (-1469) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | take | all | OLDER | -1296 (-2267) | +12.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | skip | all | L3M | -3272 (-5726) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | skip | all | L6M | -1811 (-3170) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | skip | all | OLDER | -1648 (-2885) | +8.8 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | half | all | L3M | -2398 (-4197) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | half | all | L6M | -1325 (-2319) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | half | all | OLDER | -1472 (-2576) | +10.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q75_H50 | take | all | L3M | +414 (+725) | -0.4 | -214 | +0.00 | 0.21 | 0.11 |
| q75_H50 | take | all | L6M | -44 (-77) | -0.4 | -214 | +0.00 | 0.13 | 0.06 |
| q75_H50 | take | all | OLDER | -719 (-1258) | -1.1 | +13801 | +0.00 | 0.37 | 0.18 |
| q90_H50 | take | all | L3M | +191 (+334) | +0.0 | +0 | +0.00 | 0.02 | 0.01 |
| q90_H50 | take | all | L6M | +142 (+249) | +0.0 | +0 | +0.00 | 0.01 | 0.01 |
| q90_H50 | take | all | OLDER | -169 (-296) | -1.8 | +1686 | +0.00 | 0.08 | 0.03 |
| q50_H75 | take | all | L3M | +128 (+225) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | take | all | L6M | +624 (+1092) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | take | all | OLDER | -931 (-1628) | -13.1 | +11346 | +0.00 | 0.51 | 0.26 |
| q50_H75 | skip | all | L3M | +178 (+312) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | skip | all | L6M | +685 (+1198) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | skip | all | OLDER | -1302 (-2279) | -4.6 | +14384 | +0.00 | 0.51 | 0.26 |
| q50_H75 | half | all | L3M | +153 (+268) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | half | all | L6M | +654 (+1145) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | half | all | OLDER | -1116 (-1954) | -8.8 | +12865 | +0.00 | 0.51 | 0.26 |
| q60_H75 | take | all | L3M | +830 (+1452) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | take | all | L6M | +379 (+664) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | take | all | OLDER | -478 (-836) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | skip | all | L3M | +958 (+1677) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | skip | all | L6M | +421 (+737) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | skip | all | OLDER | -402 (-703) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | half | all | L3M | +894 (+1564) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | half | all | L6M | +400 (+700) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | half | all | OLDER | -440 (-769) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q75_H75 | take | all | L3M | +236 (+413) | +0.0 | +0 | +0.00 | 0.01 | 0.00 |
| q75_H75 | take | all | L6M | +105 (+185) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q75_H75 | take | all | OLDER | -255 (-446) | -1.9 | +1485 | +0.00 | 0.08 | 0.04 |
| q90_H75 | take | all | L3M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | L6M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | OLDER | +10 (+18) | -0.4 | +0 | +0.00 | 0.01 | 0.00 |
| rem_own_k0.5 | take | all | L3M | -6674 (-11680) | +8.8 | -1861 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | take | all | L6M | -13204 (-23108) | +8.7 | -1861 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | take | all | OLDER | -7381 (-12916) | -40.2 | +20529 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | skip | all | L3M | -5271 (-9225) | +21.7 | +2982 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | skip | all | L6M | -10625 (-18594) | +21.7 | +2982 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | skip | all | OLDER | -6272 (-10977) | +17.3 | +21712 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | half | all | L3M | -5973 (-10452) | +16.3 | +560 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | half | all | L6M | -11915 (-20851) | +16.3 | +560 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | half | all | OLDER | -6827 (-11946) | +0.6 | +23150 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.75 | take | all | L3M | -7140 (-12494) | +9.6 | +3294 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | take | all | L6M | -10636 (-18614) | +9.6 | +3294 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | take | all | OLDER | -5846 (-10230) | -24.0 | +12208 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | skip | all | L3M | -3661 (-6406) | +10.3 | +4045 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | skip | all | L6M | -6650 (-11638) | +10.3 | +4045 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | skip | all | OLDER | -3856 (-6749) | +16.1 | +19073 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | half | all | L3M | -5400 (-9450) | +13.0 | +3670 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | half | all | L6M | -8643 (-15126) | +13.0 | +3670 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | half | all | OLDER | -4851 (-8489) | +13.0 | +20157 | +0.00 | 0.73 | 0.53 |
| rem_own_k1.0 | take | all | L3M | -5516 (-9653) | +18.3 | +9104 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | take | all | L6M | -8765 (-15339) | +18.3 | +9104 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | take | all | OLDER | -5714 (-9999) | -58.2 | +11926 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | skip | all | L3M | -3265 (-5714) | +15.0 | +8858 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | skip | all | L6M | -5683 (-9944) | +15.0 | +8858 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | skip | all | OLDER | -3872 (-6775) | -61.0 | +20250 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | half | all | L3M | -4391 (-7683) | +18.5 | +8981 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | half | all | L6M | -7224 (-12642) | +18.5 | +8981 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | half | all | OLDER | -4793 (-8387) | -58.0 | +21393 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.25 | take | all | L3M | -3112 (-5446) | +24.4 | +13750 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | take | all | L6M | -8275 (-14481) | +24.4 | +13750 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | take | all | OLDER | -5400 (-9450) | -15.5 | +4336 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | skip | all | L3M | -456 (-797) | +22.4 | +13720 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | skip | all | L6M | -4232 (-7405) | +22.4 | +13720 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | skip | all | OLDER | -3310 (-5792) | -36.4 | +22803 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | half | all | L3M | -1784 (-3121) | +25.2 | +15286 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | half | all | L6M | -6253 (-10943) | +25.2 | +15286 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | half | all | OLDER | -4355 (-7621) | -18.3 | +15544 | +0.00 | 0.54 | 0.41 |

Per session, q60 H75 take-anyway and remaining-range k=1.25 (own):
| cap | session | window | d mean $/wk | DD cut % | d worst week | share capped |
|---|---|---|---|---|---|---|
| q60_H75 | asia | L3M | +221 | +0.0 | +0 | 0.02 |
| q60_H75 | asia | L6M | +110 | +0.0 | +0 | 0.01 |
| q60_H75 | asia | OLDER | -124 | -0.0 | +0 | 0.23 |
| q60_H75 | london | L3M | +745 | +3.8 | +0 | 0.16 |
| q60_H75 | london | L6M | +330 | +3.8 | +0 | 0.12 |
| q60_H75 | london | OLDER | -294 | -2.1 | +0 | 0.35 |
| q60_H75 | nyam | L3M | +61 | -7.2 | +0 | 0.15 |
| q60_H75 | nyam | L6M | -14 | +0.0 | +0 | 0.10 |
| q60_H75 | nyam | OLDER | -37 | -6.0 | +1403 | 0.37 |
| q60_H75 | nypm | L3M | -197 | -0.0 | +0 | 0.41 |
| q60_H75 | nypm | L6M | -47 | +0.0 | +0 | 0.20 |
| q60_H75 | nypm | OLDER | -22 | -5.4 | +0 | 0.33 |
| rem_own_k1.25 | asia | L3M | -4547 | +35.2 | +434 | 0.37 |
| rem_own_k1.25 | asia | L6M | -6717 | +27.1 | +434 | 0.38 |
| rem_own_k1.25 | asia | OLDER | -4532 | -27.4 | +10774 | 0.62 |
| rem_own_k1.25 | london | L3M | +2278 | +46.3 | +12347 | 0.24 |
| rem_own_k1.25 | london | L6M | +1196 | +46.3 | +12347 | 0.30 |
| rem_own_k1.25 | london | OLDER | -510 | +12.9 | +3024 | 0.51 |
| rem_own_k1.25 | nyam | L3M | -650 | +20.0 | +0 | 0.24 |
| rem_own_k1.25 | nyam | L6M | -2127 | -8.9 | +1531 | 0.39 |
| rem_own_k1.25 | nyam | OLDER | -53 | +10.3 | +7327 | 0.47 |
| rem_own_k1.25 | nypm | L3M | -192 | +21.8 | +1203 | 0.45 |
| rem_own_k1.25 | nypm | L6M | -627 | +21.8 | +1203 | 0.50 |
| rem_own_k1.25 | nypm | OLDER | -304 | -2.4 | -831 | 0.50 |

### Item 4 per book x session (all 43 months): trades whose 60-pt target lies beyond the forecast quantile, their fixed-target result, the capped replay, and how far trades run past the cap
| book | session | cap | trades | share beyond | fixed-target hit rate | fixed avg $/trade | capped avg $/trade | avg points run past cap |
|---|---|---|---|---|---|---|---|---|
| A7 | asia | q50_H75 | 1156 | 0.25 | 0.50 | 60 | 87 | 10.4 |
| A7 | asia | q60_H75 | 1156 | 0.13 | 0.47 | 4 | 26 | 8.8 |
| A7 | asia | q75_H75 | 1156 | 0.03 | 0.48 | 19 | 6 | 11.1 |
| A7 | asia | rem_own_k0.75 | 1156 | 0.74 | 0.52 | 126 | 22 | 32.9 |
| H7 | asia | q50_H75 | 700 | 0.33 | 0.49 | 164 | 181 | 11.3 |
| H7 | asia | q60_H75 | 700 | 0.18 | 0.56 | 447 | 414 | 10.7 |
| H7 | asia | q75_H75 | 700 | 0.02 | 0.50 | -318 | -267 | 16.1 |
| H7 | asia | rem_own_k0.75 | 700 | 0.71 | 0.48 | 208 | 55 | 27.8 |
| H7 | nyam | q50_H75 | 348 | 0.49 | 0.46 | 84 | 25 | 8.9 |
| H7 | nyam | q60_H75 | 348 | 0.25 | 0.47 | 96 | 46 | 7.4 |
| H7 | nyam | q75_H75 | 348 | 0.06 | 0.33 | -113 | -12 | 4.7 |
| H7 | nyam | rem_own_k0.75 | 348 | 0.66 | 0.47 | 62 | -35 | 23.3 |
| K7 | asia | q50_H75 | 2596 | 0.32 | 0.44 | 102 | 74 | 9.7 |
| K7 | asia | q60_H75 | 2596 | 0.19 | 0.44 | 111 | 90 | 7.6 |
| K7 | asia | q75_H75 | 2596 | 0.04 | 0.40 | 26 | 1 | 6.1 |
| K7 | asia | rem_own_k0.75 | 2596 | 0.68 | 0.44 | 88 | 0 | 27.2 |
| K7 | london | q50_H75 | 1781 | 0.57 | 0.43 | 62 | 37 | 10.9 |
| K7 | london | q60_H75 | 1781 | 0.33 | 0.44 | 60 | 35 | 9.4 |
| K7 | london | q75_H75 | 1781 | 0.12 | 0.48 | 138 | 101 | 6.5 |
| K7 | london | rem_own_k0.75 | 1781 | 0.69 | 0.43 | 45 | -12 | 27.4 |
| K7 | nyam | q50_H75 | 1565 | 0.57 | 0.42 | 21 | 18 | 10.0 |
| K7 | nyam | q60_H75 | 1565 | 0.32 | 0.40 | -4 | -17 | 9.0 |
| K7 | nyam | q75_H75 | 1565 | 0.07 | 0.41 | 40 | 36 | 16.3 |
| K7 | nyam | rem_own_k0.75 | 1565 | 0.70 | 0.39 | -21 | -38 | 26.0 |
| K7 | nypm | q50_H75 | 1136 | 0.50 | 0.36 | 65 | 54 | 8.1 |
| K7 | nypm | q60_H75 | 1136 | 0.31 | 0.34 | 62 | 48 | 5.6 |
| K7 | nypm | q75_H75 | 1136 | 0.09 | 0.29 | 155 | 179 | 3.5 |
| K7 | nypm | rem_own_k0.75 | 1136 | 0.71 | 0.37 | 72 | -30 | 23.7 |
| M7 | london | q50_H75 | 2489 | 0.42 | 0.43 | 45 | 40 | 10.0 |
| M7 | london | q60_H75 | 2489 | 0.24 | 0.43 | 32 | 26 | 8.2 |
| M7 | london | q75_H75 | 2489 | 0.06 | 0.38 | -74 | -97 | 7.1 |
| M7 | london | rem_own_k0.75 | 2489 | 0.59 | 0.39 | -40 | -29 | 22.9 |
| M7 | nyam | q50_H75 | 1496 | 0.52 | 0.43 | 49 | 22 | 8.6 |
| M7 | nyam | q60_H75 | 1496 | 0.27 | 0.44 | 76 | 57 | 7.2 |
| M7 | nyam | q75_H75 | 1496 | 0.06 | 0.44 | 127 | 131 | 4.9 |
| M7 | nyam | rem_own_k0.75 | 1496 | 0.69 | 0.42 | 30 | -36 | 27.3 |
| O7 | nyam | q50_H75 | 452 | 0.58 | 0.32 | 205 | 91 | 20.5 |
| O7 | nyam | q60_H75 | 452 | 0.37 | 0.31 | 156 | 118 | 16.9 |
| O7 | nyam | q75_H75 | 452 | 0.08 | 0.20 | -192 | -145 | 9.5 |
| O7 | nyam | rem_own_k0.75 | 452 | 0.31 | 0.30 | 120 | 82 | 20.6 |
| P7 | asia | q50_H75 | 2161 | 0.29 | 0.46 | 391 | 341 | 10.2 |
| P7 | asia | q60_H75 | 2161 | 0.16 | 0.48 | 487 | 484 | 9.3 |
| P7 | asia | q75_H75 | 2161 | 0.02 | 0.55 | 1227 | 969 | 5.7 |
| P7 | asia | rem_own_k0.75 | 2161 | 0.70 | 0.44 | 447 | 130 | 26.6 |
| P7 | london | q50_H75 | 1537 | 0.62 | 0.38 | 74 | 27 | 10.0 |
| P7 | london | q60_H75 | 1537 | 0.41 | 0.38 | 67 | 36 | 7.8 |
| P7 | london | q75_H75 | 1537 | 0.15 | 0.41 | 124 | 59 | 5.3 |
| P7 | london | rem_own_k0.75 | 1537 | 0.72 | 0.37 | -19 | -13 | 23.8 |
| P7 | nyam | q50_H75 | 1050 | 0.72 | 0.38 | 38 | 150 | 13.2 |
| P7 | nyam | q60_H75 | 1050 | 0.48 | 0.37 | -7 | 28 | 10.9 |
| P7 | nyam | q75_H75 | 1050 | 0.15 | 0.33 | -88 | -96 | 13.3 |
| P7 | nyam | rem_own_k0.75 | 1050 | 0.71 | 0.37 | -43 | 67 | 33.2 |
| U7 | asia | q50_H75 | 686 | 0.28 | 0.54 | 412 | 320 | 10.4 |
| U7 | asia | q60_H75 | 686 | 0.15 | 0.50 | 322 | 270 | 8.0 |
| U7 | asia | q75_H75 | 686 | 0.03 | 0.47 | -260 | -383 | 6.8 |
| U7 | asia | rem_own_k0.75 | 686 | 0.74 | 0.53 | 375 | 4 | 30.5 |
| U7 | london | q50_H75 | 645 | 0.27 | 0.46 | -102 | -183 | 8.7 |
| U7 | london | q60_H75 | 645 | 0.13 | 0.46 | -173 | -182 | 7.8 |
| U7 | london | q75_H75 | 645 | 0.03 | 0.50 | -396 | -466 | 5.4 |
| U7 | london | rem_own_k0.75 | 645 | 0.68 | 0.51 | 166 | 14 | 24.5 |

### Exact cap cells (global: all books at once; L3M, L6M when promoted; delta vs JN05W2)
| cell | L3M | L6M | HOLD | d mean/wk at $4.84 L3M |
|---|---|---|---|---|
| quantile 50 cap, horizon = 75th-percentile holding time | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | +1452 (lots +9/wk) |
| quantile 60 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 75 cap, horizon = 75th-percentile holding time | +177 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 101%, w2l 0 | n/a | n/a | +176 (lots +0/wk) |
| quantile 90 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 60 cap, horizon = median holding time | -1554 $/wk, DD +2.5%, ww +1445, stops 10.42(10.35), b5 89%, w2l 1 | n/a | n/a | -1658 (lots +29/wk) |
| quantile 75 cap, horizon = median holding time | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=0.5 | -8393 $/wk, DD +2.1%, ww +5889, stops 7.76(10.35), b5 57%, w2l 3 | n/a | n/a | -8805 (lots +113/wk) |
| remaining-range cap, forecast own 20-session mean, k=0.75 | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=1.0 | -6226 $/wk, DD +27.0%, ww +12290, stops 8.98(10.35), b5 66%, w2l 2 | n/a | n/a | -6458 (lots +63/wk) |
| remaining-range cap, forecast own 20-session mean, k=1.25 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.5 | -10795 $/wk, DD +40.3%, ww +11430, stops 7.00(10.35), b5 51%, w2l 4 | n/a | n/a | -11257 (lots +126/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.75 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.0 | -7259 $/wk, DD +39.4%, ww +17319, stops 7.76(10.35), b5 65%, w2l 2 | n/a | n/a | -7570 (lots +85/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.25 | pending | | | |
| EV-best target, bounded by the book target | -14326 $/wk, DD -25.6%, ww -15613, stops 8.45(10.35), b5 46%, w2l 3 | n/a | n/a | -14639 (lots +86/wk) |
| EV-best target, unbounded | pending | | | |
| extension m=1.0 | -110 $/wk, DD -53.4%, ww -2988, stops 11.72(10.35), b5 124%, w2l 2 | n/a | n/a | -18 (lots -25/wk) |
| extension m=1.5 | pending | | | |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts skipped | +1443 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | n/a | n/a | +1410 (lots +9/wk) |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts at half size | pending | | | |
| PLANTED-EDGE CHECK (look-ahead oracle 0.9 x realised MFE, not a result) | +85531 $/wk, DD +67.0%, ww +64263, stops 6.54(10.35), b5 259%, w2l 0 | n/a | n/a | +85219 (lots +85/wk) |
| PLANTED-EDGE CHECK (oracle 0.6 x realised MFE, not a result) | pending | | | |
| PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 | n/a | -125 (lots +1/wk) |
| PLACEBO pl23: quantile 50 cap, horizon = 75th-percentile holding time | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 | n/a | -871 (lots +3/wk) |
| PLACEBO pl37: quantile 50 cap, horizon = 75th-percentile holding time | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 | n/a | -612 (lots +2/wk) |
| PLACEBO plR1: quantile 50 cap, horizon = 75th-percentile holding time | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 | n/a | -670 (lots +4/wk) |

### The one candidate: forecast-quantile-50 cap, horizon = 75th-percentile holding time (L3M mean-only so far): all windows, W44 removed, placebos
| window | scope all | W44 removed |
|---|---|---|
| L3M | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 |
| L6M | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 |
| HOLD | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 |
| MID | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 |
| PREUW | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 |
Placebos (same cap, forecast features taken n sessions earlier at the same clock / a random earlier session), L3M then L6M when run:
| placebo | L3M | L6M |
|---|---|---|
| pl11 | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 |
| pl23 | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 |
| pl37 | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 |
| plR1 | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 |

### Per book x session exact cap cells (clean: one book in one session)
| slice | cap | L3M | May-Jul |
|---|---|---|---|
| A7 asia | quantile 50 cap, horizon = 75th-percentile holding time | -17 (live -30; $4.84 -17) DD +0.0% ww +0 stops 4.03(4.03) | n/a |

### FOR THE LIVE BUILD (what D7 computes at the signal second)
From its own 1-minute bars: last 15/30/60/120-minute range and realised vol, same-offset range over the previous 20 sessions (median), session ranges of the last 5/20 sessions, range so far, the entry position in the session range (favourable-side room), elapsed fraction of the session, ln of the book-session horizon; a small coefficient table per session (15 weights, mean, sd, intercept, four residual quantile offsets) refit every 14 days and shipped as a static file. Cap = min(60, price x exp(prediction + quantile offset) - 2); orders: the target limit is placed at the capped price. The remaining-range version needs the HAR session forecast (T-RANGE2 file) or D7 computes its own 20-session mean. No intraday feed from the box.


## Per book and session, clean, and the assembled stack
**STATUS (plain, not a PASS; B1 in progress, no "nothing passes" verdict is allowed until it is done): single-book single-session cells scored in L3M for 15 of 14 slices; slice picks so far: {}.**

Method (user order PART B, 2026-11-15): each cell = the Dial 10 hook restricted to ONE book in ONE session (every other book/session unchanged at JN05W2), exact engine, all layers ON, live caps. Dollars are BASE lots; the x1.75 live figure sits beside each headline (live); the $4.84 figure reprices every contract at the FEES.md $4.84 RT (engine raw $1.18). Compared on the same book x session slice of JN05W2 (day locks/caps still interact across books, which is why the cells are run for real and not sliced from the global run). B1a settings per slice: direction both / narrow-only / wide-only x gearing 0.5 / 1.0 at the 75th-percentile horizon, plus narrow/wide g1.0 at the median horizon; "fixed" = JN05W2 itself. Walk-forward: the pick for each slice is made on 2026-05..07 only (older than L3M); L3M (2026-08..10) is then out-of-sample. B1b (around each pick): lots cap 1.5/3, lots follow half the change, dead band 0/20%, target ratio 0.8/1.2, lever stop-only (sl: stop W, lots inverse, target in the same points) / target-only (tg) / size-only (sz: bracket fixed, lots follow the forecast), noise floor k = 3/4/5 x recent 5-minute ATR (bracket never narrower), clips 25..120 / 20..150.

### B1 table: per slice, every cell (L3M, delta vs JN05W2 same slice; May-Jul = the selection window)
| slice | setting | May-Jul (selection) | L3M (out of sample) | L6M |
|---|---|---|---|---|
| A7 asia | both/g1.0/H75 | -374 (live -654; $4.84 -370) DD -10.9% ww -261 stops 2.97(3.88) | +47 (live +83; $4.84 +40) DD +25.6% ww +1495 stops 5.55(4.03) | -163 (live -286; $4.84 -165) DD -29.2% ww +1253 stops 4.26(3.96) |
| A7 asia | narrow/g1.0/H75 | -419 (live -733; $4.84 -423) DD -0.6% ww -175 stops 4.49(3.88) | -18 (live -32; $4.84 -26) DD +17.7% ww +722 stops 5.63(4.03) | -219 (live -383; $4.84 -224) DD -19.1% ww +722 stops 5.06(3.96) |
| A7 asia | both/g0.5/H75 | -556 (live -973; $4.84 -553) DD -9.2% ww +72 stops 3.50(3.88) | -192 (live -336; $4.84 -195) DD +10.1% ww +412 stops 5.10(4.03) | -374 (live -654; $4.84 -374) DD -36.6% ww +412 stops 4.30(3.96) |
| A7 asia | narrow/g0.5/H75 | -350 (live -612; $4.84 -352) DD +0.0% ww +0 stops 4.34(3.88) | -186 (live -325; $4.84 -189) DD +10.0% ww +552 stops 5.10(4.03) | -268 (live -469; $4.84 -270) DD -15.8% ww +552 stops 4.72(3.96) |
| A7 asia | wide/g1.0/H75 | +19 (live +33; $4.84 +26) DD -10.9% ww +283 stops 2.51(3.88) | -15 (live -26; $4.84 -14) DD +2.4% ww -426 stops 3.96(4.03) | +2 (live +3; $4.84 +6) DD -13.6% ww -426 stops 3.23(3.96) |
| A7 asia | wide/g0.5/H75 | n/a | -1 (live -1; $4.84 -1) DD +1.4% ww -140 stops 4.03(4.03) | n/a |
| A7 asia | wide/g1.0/H50 | n/a | -48 (live -85; $4.84 -48) DD -3.0% ww -426 stops 3.88(4.03) | n/a |
| A7 asia | narrow/g1.0/H50 | n/a | -159 (live -279; $4.84 -171) DD -8.3% ww +877 stops 5.93(4.03) | n/a |
| H7 asia | wide/g0.5/H75 | n/a | +123 (live +215; $4.84 +123) DD +0.0% ww +0 stops 0.23(0.23) | n/a |
| H7 asia | wide/g1.0/H75 | n/a | -67 (live -118; $4.84 -67) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | wide/g1.0/H50 | n/a | -312 (live -546; $4.84 -312) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | both/g0.0/H50 | -1623 (live -2840; $4.84 -1619) DD +11.0% ww +3643 stops 0.46(0.61) | -972 (live -1701; $4.84 -967) DD -31.5% ww +0 stops 0.46(0.23) | -1298 (live -2271; $4.84 -1293) DD +11.0% ww +3643 stops 0.46(0.42) |
| H7 asia | both/g1.0/H75 | +1123 (live +1965; $4.84 +1129) DD +6.5% ww +1483 stops 0.53(0.61) | +177 (live +309; $4.84 +163) DD -33.6% ww -1228 stops 0.61(0.23) | +650 (live +1137; $4.84 +646) DD +6.5% ww +1483 stops 0.57(0.42) |
| H7 asia | narrow/g1.0/H75 | n/a | +244 (live +427; $4.84 +230) DD -33.6% ww -1228 stops 0.53(0.23) | n/a |
| H7 asia | both/g0.5/H75 | n/a | -574 (live -1004; $4.84 -580) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g0.5/H75 | n/a | -697 (live -1219; $4.84 -703) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g1.0/H50 | n/a | -355 (live -621; $4.84 -372) DD -120.5% ww -2166 stops 0.53(0.23) | n/a |
| H7 nyam | narrow/g1.0/H50 | n/a | +252 (live +441; $4.84 +252) DD +60.4% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | both/g1.0/H75 | n/a | +281 (live +491; $4.84 +280) DD +57.7% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | narrow/g1.0/H75 | -187 (live -328; $4.84 -188) DD -4.0% ww +0 stops 0.53(0.46) | +258 (live +452; $4.84 +258) DD +57.7% ww +480 stops 0.30(0.38) | +35 (live +62; $4.84 +35) DD +24.1% ww +480 stops 0.42(0.42) |
| H7 nyam | both/g0.0/H50 | -58 (live -102; $4.84 -58) DD +9.4% ww +0 stops 0.46(0.46) | +221 (live +387; $4.84 +221) DD +54.7% ww +195 stops 0.15(0.38) | +82 (live +143; $4.84 +81) DD +33.9% ww +195 stops 0.30(0.42) |
| H7 nyam | both/g0.5/H75 | +103 (live +180; $4.84 +103) DD +29.2% ww -83 stops 0.46(0.46) | +87 (live +153; $4.84 +87) DD +2.2% ww +195 stops 0.38(0.38) | +95 (live +167; $4.84 +95) DD +2.2% ww +195 stops 0.42(0.42) |
| H7 nyam | narrow/g0.5/H75 | n/a | +77 (live +134; $4.84 +77) DD +2.2% ww +195 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g0.5/H75 | n/a | +11 (live +19; $4.84 +11) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H75 | n/a | +22 (live +39; $4.84 +22) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H50 | n/a | +30 (live +53; $4.84 +30) DD +0.0% ww +0 stops 0.30(0.38) | n/a |
| K7 asia | wide/g1.0/H75 | n/a | +297 (live +520; $4.84 +298) DD +0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | wide/g0.5/H75 | n/a | -54 (live -94; $4.84 -54) DD -0.7% ww -404 stops 0.00(0.00) | n/a |
| K7 asia | narrow/g0.5/H75 | n/a | +1877 (live +3285; $4.84 +1855) DD -19.6% ww -2412 stops 0.00(0.00) | n/a |
| K7 asia | both/g0.5/H75 | n/a | +1823 (live +3191; $4.84 +1801) DD -28.8% ww -3232 stops 0.00(0.00) | n/a |
| K7 asia | wide/g1.0/H50 | n/a | -401 (live -702; $4.84 -400) DD -35.9% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | both/g1.0/H75 | n/a | +1292 (live +2261; $4.84 +1220) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H75 | n/a | +912 (live +1595; $4.84 +838) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H50 | n/a | +355 (live +621; $4.84 +268) DD -86.2% ww -5644 stops 0.00(0.00) | n/a |
| K7 london | both/g0.5/H75 | n/a | -9 (live -15; $4.84 -14) DD +8.7% ww +4326 stops 0.23(0.30) | n/a |
| K7 london | wide/g0.5/H75 | n/a | +27 (live +48; $4.84 +29) DD +0.5% ww +0 stops 0.30(0.30) | n/a |
| K7 london | wide/g1.0/H50 | n/a | +431 (live +755; $4.84 +433) DD -3.3% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g0.5/H75 | n/a | -123 (live -215; $4.84 -130) DD -4.2% ww +4733 stops 0.23(0.30) | n/a |
| K7 london | wide/g1.0/H75 | n/a | +157 (live +274; $4.84 +160) DD -4.8% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g1.0/H50 | n/a | -182 (live -319; $4.84 -204) DD -13.7% ww +3097 stops 0.23(0.30) | n/a |
| K7 london | both/g1.0/H75 | n/a | +481 (live +841; $4.84 +462) DD -25.5% ww +4257 stops 0.38(0.30) | n/a |
| K7 london | narrow/g1.0/H75 | n/a | -31 (live -55; $4.84 -55) DD -42.3% ww +4122 stops 0.38(0.30) | n/a |
| K7 nyam | both/g0.0/H50 | -488 (live -855; $4.84 -488) DD -38.7% ww -514 stops 0.08(0.08) | +1078 (live +1886; $4.84 +1069) DD +53.9% ww +1605 stops 0.00(0.00) | +295 (live +516; $4.84 +290) DD +50.6% ww +1605 stops 0.04(0.04) |
| K7 nyam | narrow/g1.0/H50 | n/a | +769 (live +1345; $4.84 +761) DD +51.0% ww +2185 stops 0.00(0.00) | n/a |
| K7 nyam | both/g1.0/H75 | n/a | +1160 (live +2030; $4.84 +1153) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g1.0/H75 | n/a | +984 (live +1722; $4.84 +977) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g0.5/H75 | n/a | +668 (live +1170; $4.84 +667) DD +40.3% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | both/g0.5/H75 | n/a | +806 (live +1410; $4.84 +805) DD +39.5% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H75 | n/a | +176 (live +308; $4.84 +176) DD -0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H50 | n/a | +252 (live +441; $4.84 +253) DD -0.3% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g0.5/H75 | n/a | +137 (live +241; $4.84 +137) DD -0.8% ww +0 stops 0.00(0.00) | n/a |
| K7 nypm | wide/g1.0/H50 | n/a | +442 (live +773; $4.84 +442) DD +17.3% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | wide/g1.0/H75 | n/a | +70 (live +122; $4.84 +70) DD +13.1% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | both/g1.0/H75 | n/a | -184 (live -322; $4.84 -197) DD +9.8% ww +1145 stops 0.15(0.08) | n/a |
| K7 nypm | wide/g0.5/H75 | n/a | -4 (live -8; $4.84 -4) DD -1.5% ww -38 stops 0.00(0.08) | n/a |
| K7 nypm | narrow/g1.0/H50 | n/a | +48 (live +84; $4.84 +32) DD -1.9% ww +105 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g1.0/H75 | n/a | -254 (live -445; $4.84 -267) DD -3.3% ww +990 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g0.5/H75 | n/a | -266 (live -465; $4.84 -269) DD -26.7% ww +140 stops 0.08(0.08) | n/a |
| K7 nypm | both/g0.5/H75 | n/a | -270 (live -473; $4.84 -274) DD -27.3% ww +102 stops 0.00(0.08) | n/a |
| M7 london | wide/g1.0/H75 | n/a | +1614 (live +2824; $4.84 +1616) DD +4.9% ww +1190 stops 0.53(0.91) | n/a |
| M7 london | wide/g0.5/H75 | n/a | +688 (live +1204; $4.84 +689) DD +4.4% ww +1400 stops 0.84(0.91) | n/a |
| M7 london | wide/g1.0/H50 | n/a | +538 (live +942; $4.84 +540) DD -1.3% ww -80 stops 0.84(0.91) | n/a |
| M7 london | both/g0.5/H75 | n/a | +1147 (live +2008; $4.84 +1139) DD -8.1% ww +130 stops 1.07(0.91) | n/a |
| M7 london | narrow/g0.5/H75 | n/a | +417 (live +730; $4.84 +408) DD -10.9% ww -1075 stops 1.14(0.91) | n/a |
| M7 london | narrow/g1.0/H50 | n/a | +476 (live +833; $4.84 +446) DD -19.9% ww +1144 stops 1.45(0.91) | n/a |
| M7 london | narrow/g1.0/H75 | n/a | -366 (live -640; $4.84 -390) DD -20.4% ww +80 stops 1.29(0.91) | n/a |
| M7 london | both/g1.0/H75 | n/a | +1142 (live +1999; $4.84 +1121) DD -23.2% ww -729 stops 0.91(0.91) | n/a |
| M7 nyam | narrow/g1.0/H50 | n/a | +439 (live +769; $4.84 +424) DD +26.0% ww -222 stops 0.38(0.23) | n/a |
| M7 nyam | both/g0.5/H75 | n/a | +79 (live +138; $4.84 +75) DD +0.8% ww +194 stops 0.30(0.23) | n/a |
| M7 nyam | narrow/g0.5/H75 | n/a | +73 (live +127; $4.84 +69) DD +0.8% ww +194 stops 0.38(0.23) | n/a |
| M7 nyam | wide/g0.5/H75 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H75 | n/a | +16 (live +28; $4.84 +16) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H50 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | both/g1.0/H75 | n/a | +419 (live +733; $4.84 +405) DD -6.8% ww -991 stops 0.46(0.23) | n/a |
| M7 nyam | narrow/g1.0/H75 | n/a | +402 (live +704; $4.84 +388) DD -6.8% ww -991 stops 0.53(0.23) | n/a |
| P7 asia | both/g0.0/H50 | -5189 (live -9081; $4.84 -4987) DD +44.9% ww +11844 stops 0.00(0.00) | -703 (live -1230; $4.84 -620) DD +51.2% ww +20259 stops 0.08(0.15) | -2946 (live -5156; $4.84 -2804) DD +51.2% ww +17717 stops 0.04(0.08) |
| P7 asia | narrow/g1.0/H50 | n/a | -3918 (live -6857; $4.84 -4186) DD -0.4% ww -4286 stops 0.46(0.15) | n/a |
| P7 asia | both/g0.5/H75 | n/a | -5946 (live -10406; $4.84 -6044) DD -1.0% ww +6944 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g0.5/H75 | n/a | -5762 (live -10084; $4.84 -5860) DD -1.0% ww +9022 stops 0.15(0.15) | n/a |
| P7 asia | wide/g0.5/H75 | n/a | -184 (live -322; $4.84 -183) DD -4.9% ww -2079 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g1.0/H75 | n/a | -2696 (live -4718; $4.84 -2882) DD -7.8% ww -10346 stops 0.53(0.15) | n/a |
| P7 asia | wide/g1.0/H50 | n/a | -816 (live -1428; $4.84 -812) DD -22.6% ww -9033 stops 0.15(0.15) | n/a |
| P7 asia | wide/g1.0/H75 | n/a | -491 (live -858; $4.84 -490) DD -25.2% ww -10331 stops 0.15(0.15) | n/a |
| P7 asia | both/g1.0/H75 | n/a | -3315 (live -5802; $4.84 -3501) DD -36.1% ww -13164 stops 0.53(0.15) | n/a |
| P7 london | both/g0.5/H75 | n/a | +894 (live +1565; $4.84 +886) DD +29.6% ww -1633 stops 0.08(0.08) | n/a |
| P7 london | narrow/g0.5/H75 | n/a | +386 (live +675; $4.84 +375) DD +28.5% ww -1328 stops 0.08(0.08) | n/a |
| P7 london | narrow/g1.0/H50 | n/a | +927 (live +1622; $4.84 +895) DD +19.7% ww -3009 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H75 | n/a | -142 (live -249; $4.84 -138) DD +2.7% ww -458 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H50 | n/a | +265 (live +464; $4.84 +266) DD +1.1% ww +0 stops 0.08(0.08) | n/a |
| P7 london | wide/g0.5/H75 | n/a | +385 (live +674; $4.84 +387) DD -1.9% ww -238 stops 0.08(0.08) | n/a |
| P7 london | both/g1.0/H75 | n/a | +1179 (live +2064; $4.84 +1145) DD -9.8% ww -5408 stops 0.15(0.08) | n/a |
| P7 london | narrow/g1.0/H75 | n/a | +1322 (live +2313; $4.84 +1282) DD -14.4% ww -5203 stops 0.15(0.08) | n/a |
| P7 nyam | both/g0.0/H50 | -1333 (live -2333; $4.84 -1305) DD +88.2% ww +6983 stops 0.00(0.08) | +198 (live +346; $4.84 +220) DD +55.7% ww +1594 stops 0.15(0.38) | -568 (live -994; $4.84 -542) DD +59.1% ww +4666 stops 0.08(0.23) |
| P7 nyam | both/g1.0/H75 | n/a | +697 (live +1220; $4.84 +685) DD +51.3% ww +354 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g1.0/H75 | n/a | +543 (live +951; $4.84 +529) DD +45.9% ww +324 stops 0.30(0.38) | n/a |
| P7 nyam | both/g0.5/H75 | n/a | +105 (live +184; $4.84 +99) DD +36.7% ww +238 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g0.5/H75 | n/a | -13 (live -23; $4.84 -20) DD +36.4% ww +262 stops 0.30(0.38) | n/a |
| P7 nyam | wide/g0.5/H75 | n/a | +118 (live +207; $4.84 +119) DD +0.3% ww -25 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H75 | n/a | +16 (live +27; $4.84 +17) DD -7.5% ww -105 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H50 | n/a | -544 (live -952; $4.84 -543) DD -47.7% ww -3348 stops 0.38(0.38) | n/a |
| U7 asia | narrow/g1.0/H50 | n/a | +1222 (live +2139; $4.84 +1201) DD +15.6% ww -265 stops 1.90(1.83) | n/a |
| U7 asia | both/g1.0/H75 | n/a | +71 (live +124; $4.84 +56) DD +8.3% ww -1836 stops 1.98(1.83) | n/a |
| U7 asia | narrow/g1.0/H75 | n/a | +502 (live +879; $4.84 +487) DD +8.3% ww +983 stops 1.98(1.83) | n/a |
| U7 asia | both/g0.5/H75 | n/a | -800 (live -1399; $4.84 -808) DD +6.6% ww -2883 stops 2.05(1.83) | n/a |
| U7 asia | narrow/g0.5/H75 | n/a | -162 (live -284; $4.84 -170) DD +6.6% ww +57 stops 2.05(1.83) | n/a |
| U7 asia | wide/g0.5/H75 | n/a | -637 (live -1115; $4.84 -637) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H75 | n/a | -431 (live -755; $4.84 -431) DD +0.0% ww -1836 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H50 | n/a | -648 (live -1134; $4.84 -648) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 london | narrow/g0.5/H75 | n/a | +393 (live +687; $4.84 +392) DD +17.2% ww +1796 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H75 | n/a | +246 (live +431; $4.84 +243) DD +3.1% ww -1185 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H50 | n/a | -41 (live -72; $4.84 -48) DD -9.9% ww -1991 stops 1.52(1.45) | n/a |
| U7 london | both/g0.5/H75 | n/a | -891 (live -1560; $4.84 -890) DD -25.4% ww -3538 stops 1.52(1.45) | n/a |
| U7 london | wide/g1.0/H50 | n/a | -839 (live -1468; $4.84 -837) DD -33.9% ww -4122 stops 1.37(1.45) | n/a |
| U7 london | wide/g0.5/H75 | n/a | -1284 (live -2247; $4.84 -1282) DD -44.3% ww -6280 stops 1.52(1.45) | n/a |
| U7 london | both/g1.0/H75 | n/a | -1728 (live -3025; $4.84 -1729) DD -105.5% ww -7540 stops 1.60(1.45) | n/a |
| U7 london | wide/g1.0/H75 | n/a | -1975 (live -3455; $4.84 -1972) DD -109.8% ww -6355 stops 1.60(1.45) | n/a |

### Summary per slice: pick made on May-Jul, result on L3M
| slice | pick | L3M result of the pick | verdict |
|---|---|---|---|
| A7 asia | pending | | |
| H7 asia | pending | | |
| H7 nyam | pending | | |
| K7 asia | pending | | |
| K7 london | pending | | |
| K7 nyam | pending | | |
| K7 nypm | pending | | |
| M7 london | pending | | |
| M7 nyam | pending | | |
| P7 asia | pending | | |
| P7 london | pending | | |
| P7 nyam | pending | | |
| U7 asia | pending | | |
| U7 london | pending | | |

### B2: why the global version adds full stops (narrow-only/both g1.0 H75 cell, L3M, trade tables)
Reference JN05W2 L3M (no O7): 1855 trades, stop rate 0.071, 132 stops (13 weeks).

**M1_75_g10_c1_d10_c20_tb_B**: 2038 trades (+183 vs JN05W2), stops 173 (+41), stop rate 0.085 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 437 | 0.103 | 3.05 | 94 |
| (40, 50] | 721 | 0.074 | 2.36 | 271 |
| (50, 55] | 232 | 0.099 | 1.97 | 169 |
| (55, 60] | 435 | 0.076 | 1.87 | 76 |
| (60, 70] | 75 | 0.120 | 2.01 | -385 |
| (70, 80] | 62 | 0.048 | 1.68 | -284 |
| (80, 101] | 76 | 0.092 | 1.13 | -591 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1543 | 0.069 | 2.21 | 54 |
| (3.0, 4.0] | 294 | 0.116 | 2.29 | 239 |
| (4.0, 5.0] | 74 | 0.108 | 2.31 | 364 |
| (5.0, 6.0] | 6 | 0.167 | 2.50 | 172 |
| (6.0, 8.0] | 4 | 0.000 | 1.00 | -119 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1068 | 0.096 | 1.00 | 4 |
| (1, 2] | 385 | 0.078 | 2.00 | 115 |
| (2, 3] | 215 | 0.093 | 3.00 | 23 |
| (3, 5] | 195 | 0.062 | 4.46 | 256 |
| (5, 8] | 138 | 0.065 | 6.70 | 690 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

**M1_75_g10_c1_d10_c20_tb_N**: 2072 trades (+217 vs JN05W2), stops 178 (+46), stop rate 0.086 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 449 | 0.105 | 3.02 | 97 |
| (40, 50] | 725 | 0.073 | 2.35 | 272 |
| (50, 55] | 236 | 0.102 | 1.97 | 150 |
| (55, 60] | 662 | 0.082 | 1.82 | -29 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1644 | 0.072 | 2.18 | 50 |
| (3.0, 4.0] | 264 | 0.121 | 2.38 | 348 |
| (4.0, 5.0] | 44 | 0.091 | 3.11 | 1063 |
| (5.0, 6.0] | 3 | 0.000 | 3.33 | 68 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1073 | 0.095 | 1.00 | 8 |
| (1, 2] | 413 | 0.085 | 2.00 | 117 |
| (2, 3] | 197 | 0.081 | 3.00 | 213 |
| (3, 5] | 217 | 0.074 | 4.43 | 196 |
| (5, 8] | 135 | 0.067 | 6.74 | 714 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

Reading of the W/ATR5 table: ATR5 = mean range of the last 14 five-minute buckets in points; a bracket 3x ATR5 or less is within ordinary 5-minute noise. The noise-floor cells (floor 3/4/5 x ATR5, narrowing only) are listed in B3.


### B3: levers (stop-only / target-only / both / size-only) and noise floor, per slice
| slice | cell | L3M | May-Jul |
|---|---|---|---|

### B4: assembled stack (each slice at its own walk-forward pick, run together)
(not run yet: starts when every slice has a pick)


## Target capped at the forecast
**VERDICT (plain, not a PASS; FIRST PASS; 15 of 26 global exact cap cells scored in L3M, per book x session exact cells still running): planted-edge check PASSED through the exact engine (look-ahead oracle target 0.9 x realised MFE: +85531 $/wk, DD +67.0%, ww +64263; this is a mechanism check, NOT a result); the reachable move is only weakly forecastable (R2 on ln MFE 0.03-0.14, quantile calibration good); in the exact L3M cells the cap at the forecast 50th-percentile move (horizon = 75th-percentile holding time) gives +1486 $/wk, DD -0.5%, ww -240 and the 75th-percentile cap +177 $/wk, DD +0.0%, ww +0, the remaining-range caps cut drawdown (own k1.0 -6226 $/wk, DD +27.0%, ww +12290; HAR k1.0 -7259 $/wk, DD +39.4%, ww +17319) but cost thousands per week. Best exact L3M cap cell inside the mean gate by DD: PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time (DD +7.9%, -120 $/wk). L6M/HOLD/older still to run before any verdict.**

Planted-edge check (H1) for the capping mechanism: cells `tcoracle0.9` / `0.6` set the target to 0.9 / 0.6 x the REALISED maximum favourable move (look-ahead, only to prove the mechanism can show an edge through the exact engine); they must come out strongly positive. Status below in the exact table. Until they do, an exact cap verdict is not stated.

Definition. Reachable move = maximum favourable excursion from the signal-second bar close over the book-session holding horizon H (H50/H75 = median / 75th percentile holding time of that book+session, causal), points. Model: walk-forward ridge (14-day blocks, expanding, min 90 days, per session) on ln((MFE+2)/price) from the Dial 10 own-bar inputs (last 15/30/60/120 min range and vol, same-clock normal, own session level, range used so far, elapsed fraction) plus the side-aware room in the session range so far; quantiles q = fitted + empirical training-residual quantile (50/60/75/90). Cap: target = min(book target 60 pts [58 after fills], q-quantile), stop, lots and every other level unchanged. Remaining-range cap: target = min(book target, k x (session range forecast - range printed so far)), forecast = own (price x exp(sf20), mean of the last 20 sessions) or T-RANGE2 HAR (fc_r2_har, available-epoch checked). Small caps (< 30 pts = 0.5 x stop): take / skip / half. EV target: argmax over T in [20, book target or 300] of T x P(MFE>=T) - stop x (1-P) with the lognormal forecast (ignores the stop-first ordering, so optimistic). Extension: if the forecast median MFE is >= m x book target, target = min(q50, 2 x book target). Lots/base basis: dollars are BASE lots (live x1.75 = multiply by 1.75); fee columns $4.84 beside raw $1.18 where shown.

### Item 1: calibration of the forecast quantiles (share of trades whose realized MFE exceeded the forecast quantile; a q-quantile should be exceeded 1-q of the time = 0.50 / 0.40 / 0.25 / 0.10) and R2 of ln MFE, per session
| H | session | window | n | >q50 | >q60 | >q75 | >q90 | R2 ln MFE | median q75 (pts) | share q75 < 60 |
|---|---|---|---|---|---|---|---|---|---|---|
| 50 | asia | older (<2026-05) | 5119 | 0.51 | 0.41 | 0.26 | 0.12 | 0.121 | 80 | 0.222 |
| 50 | asia | L6M | 2006 | 0.49 | 0.38 | 0.23 | 0.08 | 0.058 | 111 | 0.047 |
| 50 | asia | L3M | 875 | 0.46 | 0.34 | 0.20 | 0.07 | -0.014 | 90 | 0.098 |
| 50 | london | older (<2026-05) | 4892 | 0.51 | 0.41 | 0.26 | 0.11 | 0.142 | 62 | 0.438 |
| 50 | london | L6M | 1406 | 0.48 | 0.37 | 0.23 | 0.08 | 0.028 | 76 | 0.166 |
| 50 | london | L3M | 673 | 0.48 | 0.37 | 0.24 | 0.07 | -0.008 | 68 | 0.247 |
| 50 | nyam | older (<2026-05) | 4142 | 0.47 | 0.38 | 0.24 | 0.11 | 0.077 | 63 | 0.397 |
| 50 | nyam | L6M | 600 | 0.51 | 0.40 | 0.24 | 0.09 | 0.097 | 83 | 0.157 |
| 50 | nyam | L3M | 271 | 0.51 | 0.38 | 0.20 | 0.06 | 0.077 | 68 | 0.258 |
| 50 | nypm | older (<2026-05) | 817 | 0.48 | 0.40 | 0.26 | 0.13 | 0.073 | 62 | 0.419 |
| 50 | nypm | L6M | 150 | 0.59 | 0.50 | 0.33 | 0.13 | 0.221 | 71 | 0.307 |
| 50 | nypm | L3M | 56 | 0.50 | 0.36 | 0.21 | 0.09 | 0.104 | 54 | 0.589 |
| 50 | all | older (<2026-05) | 14970 | 0.50 | 0.40 | 0.26 | 0.12 | 0.123 | 68 | 0.352 |
| 50 | all | L6M | 4162 | 0.49 | 0.38 | 0.23 | 0.08 | 0.080 | 91 | 0.113 |
| 50 | all | L3M | 1875 | 0.47 | 0.36 | 0.21 | 0.07 | 0.014 | 76 | 0.189 |
| 75 | asia | older (<2026-05) | 5119 | 0.52 | 0.41 | 0.26 | 0.12 | 0.134 | 122 | 0.032 |
| 75 | asia | L6M | 2006 | 0.50 | 0.40 | 0.24 | 0.08 | 0.027 | 178 | 0.000 |
| 75 | asia | L3M | 875 | 0.45 | 0.35 | 0.20 | 0.05 | -0.016 | 156 | 0.000 |
| 75 | london | older (<2026-05) | 4891 | 0.51 | 0.42 | 0.27 | 0.11 | 0.157 | 101 | 0.100 |
| 75 | london | L6M | 1406 | 0.49 | 0.37 | 0.21 | 0.08 | 0.069 | 118 | 0.001 |
| 75 | london | L3M | 673 | 0.49 | 0.38 | 0.21 | 0.09 | 0.025 | 108 | 0.000 |
| 75 | nyam | older (<2026-05) | 4142 | 0.48 | 0.38 | 0.23 | 0.10 | 0.065 | 91 | 0.081 |
| 75 | nyam | L6M | 600 | 0.50 | 0.40 | 0.24 | 0.10 | 0.098 | 125 | 0.015 |
| 75 | nyam | L3M | 271 | 0.44 | 0.34 | 0.19 | 0.05 | 0.051 | 103 | 0.015 |
| 75 | nypm | older (<2026-05) | 812 | 0.49 | 0.37 | 0.26 | 0.11 | 0.043 | 87 | 0.095 |
| 75 | nypm | L6M | 150 | 0.53 | 0.46 | 0.34 | 0.17 | 0.179 | 117 | 0.013 |
| 75 | nypm | L3M | 56 | 0.41 | 0.30 | 0.21 | 0.07 | -0.076 | 93 | 0.036 |
| 75 | all | older (<2026-05) | 14964 | 0.51 | 0.40 | 0.25 | 0.11 | 0.131 | 102 | 0.071 |
| 75 | all | L6M | 4162 | 0.50 | 0.39 | 0.23 | 0.09 | 0.079 | 149 | 0.003 |
| 75 | all | L3M | 1875 | 0.46 | 0.36 | 0.20 | 0.06 | 0.032 | 128 | 0.003 |

### Items 3 and 4 (and 2): offline replay of the caps on the JN05W2 trade paths, all 43 months (estimate: 1-min paths, cap counted only before the exit bar, so cut/stop ordering is conservative; the exact cells below decide). d mean $/wk and DD cut % vs JN05W2 on the same trades, scope all, then per session for the cap with the most trades capped
| cap | small-cap rule | scope | window | d mean $/wk (live x1.75) | DD cut % | d worst week | d stops/wk | share capped | share where cap hit |
|---|---|---|---|---|---|---|---|---|---|
| q50_H50 | take | all | L3M | +409 (+715) | -3.9 | -1411 | +0.00 | 0.82 | 0.45 |
| q50_H50 | take | all | L6M | -96 (-169) | -3.9 | -1411 | +0.00 | 0.62 | 0.33 |
| q50_H50 | take | all | OLDER | -1795 (-3141) | +12.0 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | skip | all | L3M | -1581 (-2767) | -5.0 | -1996 | +0.00 | 0.82 | 0.45 |
| q50_H50 | skip | all | L6M | -1445 (-2528) | -5.0 | -1996 | +0.00 | 0.62 | 0.33 |
| q50_H50 | skip | all | OLDER | -2271 (-3975) | +17.4 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | half | all | L3M | -586 (-1026) | -4.4 | -1704 | +0.00 | 0.82 | 0.45 |
| q50_H50 | half | all | L6M | -771 (-1348) | -4.4 | -1704 | +0.00 | 0.62 | 0.33 |
| q50_H50 | half | all | OLDER | -2033 (-3558) | +16.5 | +13127 | +0.00 | 0.80 | 0.45 |
| q60_H50 | take | all | L3M | -1525 (-2668) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | take | all | L6M | -839 (-1469) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | take | all | OLDER | -1296 (-2267) | +12.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | skip | all | L3M | -3272 (-5726) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | skip | all | L6M | -1811 (-3170) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | skip | all | OLDER | -1648 (-2885) | +8.8 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | half | all | L3M | -2398 (-4197) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | half | all | L6M | -1325 (-2319) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | half | all | OLDER | -1472 (-2576) | +10.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q75_H50 | take | all | L3M | +414 (+725) | -0.4 | -214 | +0.00 | 0.21 | 0.11 |
| q75_H50 | take | all | L6M | -44 (-77) | -0.4 | -214 | +0.00 | 0.13 | 0.06 |
| q75_H50 | take | all | OLDER | -719 (-1258) | -1.1 | +13801 | +0.00 | 0.37 | 0.18 |
| q90_H50 | take | all | L3M | +191 (+334) | +0.0 | +0 | +0.00 | 0.02 | 0.01 |
| q90_H50 | take | all | L6M | +142 (+249) | +0.0 | +0 | +0.00 | 0.01 | 0.01 |
| q90_H50 | take | all | OLDER | -169 (-296) | -1.8 | +1686 | +0.00 | 0.08 | 0.03 |
| q50_H75 | take | all | L3M | +128 (+225) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | take | all | L6M | +624 (+1092) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | take | all | OLDER | -931 (-1628) | -13.1 | +11346 | +0.00 | 0.51 | 0.26 |
| q50_H75 | skip | all | L3M | +178 (+312) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | skip | all | L6M | +685 (+1198) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | skip | all | OLDER | -1302 (-2279) | -4.6 | +14384 | +0.00 | 0.51 | 0.26 |
| q50_H75 | half | all | L3M | +153 (+268) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | half | all | L6M | +654 (+1145) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | half | all | OLDER | -1116 (-1954) | -8.8 | +12865 | +0.00 | 0.51 | 0.26 |
| q60_H75 | take | all | L3M | +830 (+1452) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | take | all | L6M | +379 (+664) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | take | all | OLDER | -478 (-836) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | skip | all | L3M | +958 (+1677) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | skip | all | L6M | +421 (+737) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | skip | all | OLDER | -402 (-703) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | half | all | L3M | +894 (+1564) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | half | all | L6M | +400 (+700) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | half | all | OLDER | -440 (-769) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q75_H75 | take | all | L3M | +236 (+413) | +0.0 | +0 | +0.00 | 0.01 | 0.00 |
| q75_H75 | take | all | L6M | +105 (+185) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q75_H75 | take | all | OLDER | -255 (-446) | -1.9 | +1485 | +0.00 | 0.08 | 0.04 |
| q90_H75 | take | all | L3M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | L6M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | OLDER | +10 (+18) | -0.4 | +0 | +0.00 | 0.01 | 0.00 |
| rem_own_k0.5 | take | all | L3M | -6674 (-11680) | +8.8 | -1861 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | take | all | L6M | -13204 (-23108) | +8.7 | -1861 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | take | all | OLDER | -7381 (-12916) | -40.2 | +20529 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | skip | all | L3M | -5271 (-9225) | +21.7 | +2982 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | skip | all | L6M | -10625 (-18594) | +21.7 | +2982 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | skip | all | OLDER | -6272 (-10977) | +17.3 | +21712 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | half | all | L3M | -5973 (-10452) | +16.3 | +560 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | half | all | L6M | -11915 (-20851) | +16.3 | +560 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | half | all | OLDER | -6827 (-11946) | +0.6 | +23150 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.75 | take | all | L3M | -7140 (-12494) | +9.6 | +3294 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | take | all | L6M | -10636 (-18614) | +9.6 | +3294 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | take | all | OLDER | -5846 (-10230) | -24.0 | +12208 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | skip | all | L3M | -3661 (-6406) | +10.3 | +4045 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | skip | all | L6M | -6650 (-11638) | +10.3 | +4045 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | skip | all | OLDER | -3856 (-6749) | +16.1 | +19073 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | half | all | L3M | -5400 (-9450) | +13.0 | +3670 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | half | all | L6M | -8643 (-15126) | +13.0 | +3670 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | half | all | OLDER | -4851 (-8489) | +13.0 | +20157 | +0.00 | 0.73 | 0.53 |
| rem_own_k1.0 | take | all | L3M | -5516 (-9653) | +18.3 | +9104 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | take | all | L6M | -8765 (-15339) | +18.3 | +9104 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | take | all | OLDER | -5714 (-9999) | -58.2 | +11926 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | skip | all | L3M | -3265 (-5714) | +15.0 | +8858 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | skip | all | L6M | -5683 (-9944) | +15.0 | +8858 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | skip | all | OLDER | -3872 (-6775) | -61.0 | +20250 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | half | all | L3M | -4391 (-7683) | +18.5 | +8981 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | half | all | L6M | -7224 (-12642) | +18.5 | +8981 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | half | all | OLDER | -4793 (-8387) | -58.0 | +21393 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.25 | take | all | L3M | -3112 (-5446) | +24.4 | +13750 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | take | all | L6M | -8275 (-14481) | +24.4 | +13750 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | take | all | OLDER | -5400 (-9450) | -15.5 | +4336 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | skip | all | L3M | -456 (-797) | +22.4 | +13720 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | skip | all | L6M | -4232 (-7405) | +22.4 | +13720 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | skip | all | OLDER | -3310 (-5792) | -36.4 | +22803 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | half | all | L3M | -1784 (-3121) | +25.2 | +15286 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | half | all | L6M | -6253 (-10943) | +25.2 | +15286 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | half | all | OLDER | -4355 (-7621) | -18.3 | +15544 | +0.00 | 0.54 | 0.41 |

Per session, q60 H75 take-anyway and remaining-range k=1.25 (own):
| cap | session | window | d mean $/wk | DD cut % | d worst week | share capped |
|---|---|---|---|---|---|---|
| q60_H75 | asia | L3M | +221 | +0.0 | +0 | 0.02 |
| q60_H75 | asia | L6M | +110 | +0.0 | +0 | 0.01 |
| q60_H75 | asia | OLDER | -124 | -0.0 | +0 | 0.23 |
| q60_H75 | london | L3M | +745 | +3.8 | +0 | 0.16 |
| q60_H75 | london | L6M | +330 | +3.8 | +0 | 0.12 |
| q60_H75 | london | OLDER | -294 | -2.1 | +0 | 0.35 |
| q60_H75 | nyam | L3M | +61 | -7.2 | +0 | 0.15 |
| q60_H75 | nyam | L6M | -14 | +0.0 | +0 | 0.10 |
| q60_H75 | nyam | OLDER | -37 | -6.0 | +1403 | 0.37 |
| q60_H75 | nypm | L3M | -197 | -0.0 | +0 | 0.41 |
| q60_H75 | nypm | L6M | -47 | +0.0 | +0 | 0.20 |
| q60_H75 | nypm | OLDER | -22 | -5.4 | +0 | 0.33 |
| rem_own_k1.25 | asia | L3M | -4547 | +35.2 | +434 | 0.37 |
| rem_own_k1.25 | asia | L6M | -6717 | +27.1 | +434 | 0.38 |
| rem_own_k1.25 | asia | OLDER | -4532 | -27.4 | +10774 | 0.62 |
| rem_own_k1.25 | london | L3M | +2278 | +46.3 | +12347 | 0.24 |
| rem_own_k1.25 | london | L6M | +1196 | +46.3 | +12347 | 0.30 |
| rem_own_k1.25 | london | OLDER | -510 | +12.9 | +3024 | 0.51 |
| rem_own_k1.25 | nyam | L3M | -650 | +20.0 | +0 | 0.24 |
| rem_own_k1.25 | nyam | L6M | -2127 | -8.9 | +1531 | 0.39 |
| rem_own_k1.25 | nyam | OLDER | -53 | +10.3 | +7327 | 0.47 |
| rem_own_k1.25 | nypm | L3M | -192 | +21.8 | +1203 | 0.45 |
| rem_own_k1.25 | nypm | L6M | -627 | +21.8 | +1203 | 0.50 |
| rem_own_k1.25 | nypm | OLDER | -304 | -2.4 | -831 | 0.50 |

### Item 4 per book x session (all 43 months): trades whose 60-pt target lies beyond the forecast quantile, their fixed-target result, the capped replay, and how far trades run past the cap
| book | session | cap | trades | share beyond | fixed-target hit rate | fixed avg $/trade | capped avg $/trade | avg points run past cap |
|---|---|---|---|---|---|---|---|---|
| A7 | asia | q50_H75 | 1156 | 0.25 | 0.50 | 60 | 87 | 10.4 |
| A7 | asia | q60_H75 | 1156 | 0.13 | 0.47 | 4 | 26 | 8.8 |
| A7 | asia | q75_H75 | 1156 | 0.03 | 0.48 | 19 | 6 | 11.1 |
| A7 | asia | rem_own_k0.75 | 1156 | 0.74 | 0.52 | 126 | 22 | 32.9 |
| H7 | asia | q50_H75 | 700 | 0.33 | 0.49 | 164 | 181 | 11.3 |
| H7 | asia | q60_H75 | 700 | 0.18 | 0.56 | 447 | 414 | 10.7 |
| H7 | asia | q75_H75 | 700 | 0.02 | 0.50 | -318 | -267 | 16.1 |
| H7 | asia | rem_own_k0.75 | 700 | 0.71 | 0.48 | 208 | 55 | 27.8 |
| H7 | nyam | q50_H75 | 348 | 0.49 | 0.46 | 84 | 25 | 8.9 |
| H7 | nyam | q60_H75 | 348 | 0.25 | 0.47 | 96 | 46 | 7.4 |
| H7 | nyam | q75_H75 | 348 | 0.06 | 0.33 | -113 | -12 | 4.7 |
| H7 | nyam | rem_own_k0.75 | 348 | 0.66 | 0.47 | 62 | -35 | 23.3 |
| K7 | asia | q50_H75 | 2596 | 0.32 | 0.44 | 102 | 74 | 9.7 |
| K7 | asia | q60_H75 | 2596 | 0.19 | 0.44 | 111 | 90 | 7.6 |
| K7 | asia | q75_H75 | 2596 | 0.04 | 0.40 | 26 | 1 | 6.1 |
| K7 | asia | rem_own_k0.75 | 2596 | 0.68 | 0.44 | 88 | 0 | 27.2 |
| K7 | london | q50_H75 | 1781 | 0.57 | 0.43 | 62 | 37 | 10.9 |
| K7 | london | q60_H75 | 1781 | 0.33 | 0.44 | 60 | 35 | 9.4 |
| K7 | london | q75_H75 | 1781 | 0.12 | 0.48 | 138 | 101 | 6.5 |
| K7 | london | rem_own_k0.75 | 1781 | 0.69 | 0.43 | 45 | -12 | 27.4 |
| K7 | nyam | q50_H75 | 1565 | 0.57 | 0.42 | 21 | 18 | 10.0 |
| K7 | nyam | q60_H75 | 1565 | 0.32 | 0.40 | -4 | -17 | 9.0 |
| K7 | nyam | q75_H75 | 1565 | 0.07 | 0.41 | 40 | 36 | 16.3 |
| K7 | nyam | rem_own_k0.75 | 1565 | 0.70 | 0.39 | -21 | -38 | 26.0 |
| K7 | nypm | q50_H75 | 1136 | 0.50 | 0.36 | 65 | 54 | 8.1 |
| K7 | nypm | q60_H75 | 1136 | 0.31 | 0.34 | 62 | 48 | 5.6 |
| K7 | nypm | q75_H75 | 1136 | 0.09 | 0.29 | 155 | 179 | 3.5 |
| K7 | nypm | rem_own_k0.75 | 1136 | 0.71 | 0.37 | 72 | -30 | 23.7 |
| M7 | london | q50_H75 | 2489 | 0.42 | 0.43 | 45 | 40 | 10.0 |
| M7 | london | q60_H75 | 2489 | 0.24 | 0.43 | 32 | 26 | 8.2 |
| M7 | london | q75_H75 | 2489 | 0.06 | 0.38 | -74 | -97 | 7.1 |
| M7 | london | rem_own_k0.75 | 2489 | 0.59 | 0.39 | -40 | -29 | 22.9 |
| M7 | nyam | q50_H75 | 1496 | 0.52 | 0.43 | 49 | 22 | 8.6 |
| M7 | nyam | q60_H75 | 1496 | 0.27 | 0.44 | 76 | 57 | 7.2 |
| M7 | nyam | q75_H75 | 1496 | 0.06 | 0.44 | 127 | 131 | 4.9 |
| M7 | nyam | rem_own_k0.75 | 1496 | 0.69 | 0.42 | 30 | -36 | 27.3 |
| O7 | nyam | q50_H75 | 452 | 0.58 | 0.32 | 205 | 91 | 20.5 |
| O7 | nyam | q60_H75 | 452 | 0.37 | 0.31 | 156 | 118 | 16.9 |
| O7 | nyam | q75_H75 | 452 | 0.08 | 0.20 | -192 | -145 | 9.5 |
| O7 | nyam | rem_own_k0.75 | 452 | 0.31 | 0.30 | 120 | 82 | 20.6 |
| P7 | asia | q50_H75 | 2161 | 0.29 | 0.46 | 391 | 341 | 10.2 |
| P7 | asia | q60_H75 | 2161 | 0.16 | 0.48 | 487 | 484 | 9.3 |
| P7 | asia | q75_H75 | 2161 | 0.02 | 0.55 | 1227 | 969 | 5.7 |
| P7 | asia | rem_own_k0.75 | 2161 | 0.70 | 0.44 | 447 | 130 | 26.6 |
| P7 | london | q50_H75 | 1537 | 0.62 | 0.38 | 74 | 27 | 10.0 |
| P7 | london | q60_H75 | 1537 | 0.41 | 0.38 | 67 | 36 | 7.8 |
| P7 | london | q75_H75 | 1537 | 0.15 | 0.41 | 124 | 59 | 5.3 |
| P7 | london | rem_own_k0.75 | 1537 | 0.72 | 0.37 | -19 | -13 | 23.8 |
| P7 | nyam | q50_H75 | 1050 | 0.72 | 0.38 | 38 | 150 | 13.2 |
| P7 | nyam | q60_H75 | 1050 | 0.48 | 0.37 | -7 | 28 | 10.9 |
| P7 | nyam | q75_H75 | 1050 | 0.15 | 0.33 | -88 | -96 | 13.3 |
| P7 | nyam | rem_own_k0.75 | 1050 | 0.71 | 0.37 | -43 | 67 | 33.2 |
| U7 | asia | q50_H75 | 686 | 0.28 | 0.54 | 412 | 320 | 10.4 |
| U7 | asia | q60_H75 | 686 | 0.15 | 0.50 | 322 | 270 | 8.0 |
| U7 | asia | q75_H75 | 686 | 0.03 | 0.47 | -260 | -383 | 6.8 |
| U7 | asia | rem_own_k0.75 | 686 | 0.74 | 0.53 | 375 | 4 | 30.5 |
| U7 | london | q50_H75 | 645 | 0.27 | 0.46 | -102 | -183 | 8.7 |
| U7 | london | q60_H75 | 645 | 0.13 | 0.46 | -173 | -182 | 7.8 |
| U7 | london | q75_H75 | 645 | 0.03 | 0.50 | -396 | -466 | 5.4 |
| U7 | london | rem_own_k0.75 | 645 | 0.68 | 0.51 | 166 | 14 | 24.5 |

### Exact cap cells (global: all books at once; L3M, L6M when promoted; delta vs JN05W2)
| cell | L3M | L6M | HOLD | d mean/wk at $4.84 L3M |
|---|---|---|---|---|
| quantile 50 cap, horizon = 75th-percentile holding time | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | +1452 (lots +9/wk) |
| quantile 60 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 75 cap, horizon = 75th-percentile holding time | +177 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 101%, w2l 0 | n/a | n/a | +176 (lots +0/wk) |
| quantile 90 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 60 cap, horizon = median holding time | -1554 $/wk, DD +2.5%, ww +1445, stops 10.42(10.35), b5 89%, w2l 1 | n/a | n/a | -1658 (lots +29/wk) |
| quantile 75 cap, horizon = median holding time | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=0.5 | -8393 $/wk, DD +2.1%, ww +5889, stops 7.76(10.35), b5 57%, w2l 3 | n/a | n/a | -8805 (lots +113/wk) |
| remaining-range cap, forecast own 20-session mean, k=0.75 | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=1.0 | -6226 $/wk, DD +27.0%, ww +12290, stops 8.98(10.35), b5 66%, w2l 2 | n/a | n/a | -6458 (lots +63/wk) |
| remaining-range cap, forecast own 20-session mean, k=1.25 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.5 | -10795 $/wk, DD +40.3%, ww +11430, stops 7.00(10.35), b5 51%, w2l 4 | n/a | n/a | -11257 (lots +126/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.75 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.0 | -7259 $/wk, DD +39.4%, ww +17319, stops 7.76(10.35), b5 65%, w2l 2 | n/a | n/a | -7570 (lots +85/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.25 | pending | | | |
| EV-best target, bounded by the book target | -14326 $/wk, DD -25.6%, ww -15613, stops 8.45(10.35), b5 46%, w2l 3 | n/a | n/a | -14639 (lots +86/wk) |
| EV-best target, unbounded | pending | | | |
| extension m=1.0 | -110 $/wk, DD -53.4%, ww -2988, stops 11.72(10.35), b5 124%, w2l 2 | n/a | n/a | -18 (lots -25/wk) |
| extension m=1.5 | pending | | | |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts skipped | +1443 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | n/a | n/a | +1410 (lots +9/wk) |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts at half size | pending | | | |
| PLANTED-EDGE CHECK (look-ahead oracle 0.9 x realised MFE, not a result) | +85531 $/wk, DD +67.0%, ww +64263, stops 6.54(10.35), b5 259%, w2l 0 | n/a | n/a | +85219 (lots +85/wk) |
| PLANTED-EDGE CHECK (oracle 0.6 x realised MFE, not a result) | pending | | | |
| PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 | n/a | -125 (lots +1/wk) |
| PLACEBO pl23: quantile 50 cap, horizon = 75th-percentile holding time | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 | n/a | -871 (lots +3/wk) |
| PLACEBO pl37: quantile 50 cap, horizon = 75th-percentile holding time | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 | n/a | -612 (lots +2/wk) |
| PLACEBO plR1: quantile 50 cap, horizon = 75th-percentile holding time | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 | n/a | -670 (lots +4/wk) |

### The one candidate: forecast-quantile-50 cap, horizon = 75th-percentile holding time (L3M mean-only so far): all windows, W44 removed, placebos
| window | scope all | W44 removed |
|---|---|---|
| L3M | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 |
| L6M | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 |
| HOLD | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 |
| MID | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 |
| PREUW | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 |
Placebos (same cap, forecast features taken n sessions earlier at the same clock / a random earlier session), L3M then L6M when run:
| placebo | L3M | L6M |
|---|---|---|
| pl11 | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 |
| pl23 | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 |
| pl37 | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 |
| plR1 | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 |

### Per book x session exact cap cells (clean: one book in one session)
| slice | cap | L3M | May-Jul |
|---|---|---|---|
| A7 asia | quantile 50 cap, horizon = 75th-percentile holding time | -17 (live -30; $4.84 -17) DD +0.0% ww +0 stops 4.03(4.03) | n/a |

### FOR THE LIVE BUILD (what D7 computes at the signal second)
From its own 1-minute bars: last 15/30/60/120-minute range and realised vol, same-offset range over the previous 20 sessions (median), session ranges of the last 5/20 sessions, range so far, the entry position in the session range (favourable-side room), elapsed fraction of the session, ln of the book-session horizon; a small coefficient table per session (15 weights, mean, sd, intercept, four residual quantile offsets) refit every 14 days and shipped as a static file. Cap = min(60, price x exp(prediction + quantile offset) - 2); orders: the target limit is placed at the capped price. The remaining-range version needs the HAR session forecast (T-RANGE2 file) or D7 computes its own 20-session mean. No intraday feed from the box.


## Per book and session, clean, and the assembled stack
**STATUS (plain, not a PASS; B1 in progress, no "nothing passes" verdict is allowed until it is done): single-book single-session cells scored in L3M for 15 of 14 slices; slice picks so far: {}.**

Method (user order PART B, 2026-11-15): each cell = the Dial 10 hook restricted to ONE book in ONE session (every other book/session unchanged at JN05W2), exact engine, all layers ON, live caps. Dollars are BASE lots; the x1.75 live figure sits beside each headline (live); the $4.84 figure reprices every contract at the FEES.md $4.84 RT (engine raw $1.18). Compared on the same book x session slice of JN05W2 (day locks/caps still interact across books, which is why the cells are run for real and not sliced from the global run). B1a settings per slice: direction both / narrow-only / wide-only x gearing 0.5 / 1.0 at the 75th-percentile horizon, plus narrow/wide g1.0 at the median horizon; "fixed" = JN05W2 itself. Walk-forward: the pick for each slice is made on 2026-05..07 only (older than L3M); L3M (2026-08..10) is then out-of-sample. B1b (around each pick): lots cap 1.5/3, lots follow half the change, dead band 0/20%, target ratio 0.8/1.2, lever stop-only (sl: stop W, lots inverse, target in the same points) / target-only (tg) / size-only (sz: bracket fixed, lots follow the forecast), noise floor k = 3/4/5 x recent 5-minute ATR (bracket never narrower), clips 25..120 / 20..150.

### B1 table: per slice, every cell (L3M, delta vs JN05W2 same slice; May-Jul = the selection window)
| slice | setting | May-Jul (selection) | L3M (out of sample) | L6M |
|---|---|---|---|---|
| A7 asia | both/g1.0/H75 | -374 (live -654; $4.84 -370) DD -10.9% ww -261 stops 2.97(3.88) | +47 (live +83; $4.84 +40) DD +25.6% ww +1495 stops 5.55(4.03) | -163 (live -286; $4.84 -165) DD -29.2% ww +1253 stops 4.26(3.96) |
| A7 asia | narrow/g1.0/H75 | -419 (live -733; $4.84 -423) DD -0.6% ww -175 stops 4.49(3.88) | -18 (live -32; $4.84 -26) DD +17.7% ww +722 stops 5.63(4.03) | -219 (live -383; $4.84 -224) DD -19.1% ww +722 stops 5.06(3.96) |
| A7 asia | both/g0.5/H75 | -556 (live -973; $4.84 -553) DD -9.2% ww +72 stops 3.50(3.88) | -192 (live -336; $4.84 -195) DD +10.1% ww +412 stops 5.10(4.03) | -374 (live -654; $4.84 -374) DD -36.6% ww +412 stops 4.30(3.96) |
| A7 asia | narrow/g0.5/H75 | -350 (live -612; $4.84 -352) DD +0.0% ww +0 stops 4.34(3.88) | -186 (live -325; $4.84 -189) DD +10.0% ww +552 stops 5.10(4.03) | -268 (live -469; $4.84 -270) DD -15.8% ww +552 stops 4.72(3.96) |
| A7 asia | wide/g1.0/H75 | +19 (live +33; $4.84 +26) DD -10.9% ww +283 stops 2.51(3.88) | -15 (live -26; $4.84 -14) DD +2.4% ww -426 stops 3.96(4.03) | +2 (live +3; $4.84 +6) DD -13.6% ww -426 stops 3.23(3.96) |
| A7 asia | wide/g0.5/H75 | n/a | -1 (live -1; $4.84 -1) DD +1.4% ww -140 stops 4.03(4.03) | n/a |
| A7 asia | wide/g1.0/H50 | n/a | -48 (live -85; $4.84 -48) DD -3.0% ww -426 stops 3.88(4.03) | n/a |
| A7 asia | narrow/g1.0/H50 | n/a | -159 (live -279; $4.84 -171) DD -8.3% ww +877 stops 5.93(4.03) | n/a |
| H7 asia | wide/g0.5/H75 | n/a | +123 (live +215; $4.84 +123) DD +0.0% ww +0 stops 0.23(0.23) | n/a |
| H7 asia | wide/g1.0/H75 | n/a | -67 (live -118; $4.84 -67) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | wide/g1.0/H50 | n/a | -312 (live -546; $4.84 -312) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | both/g0.0/H50 | -1623 (live -2840; $4.84 -1619) DD +11.0% ww +3643 stops 0.46(0.61) | -972 (live -1701; $4.84 -967) DD -31.5% ww +0 stops 0.46(0.23) | -1298 (live -2271; $4.84 -1293) DD +11.0% ww +3643 stops 0.46(0.42) |
| H7 asia | both/g1.0/H75 | +1123 (live +1965; $4.84 +1129) DD +6.5% ww +1483 stops 0.53(0.61) | +177 (live +309; $4.84 +163) DD -33.6% ww -1228 stops 0.61(0.23) | +650 (live +1137; $4.84 +646) DD +6.5% ww +1483 stops 0.57(0.42) |
| H7 asia | narrow/g1.0/H75 | n/a | +244 (live +427; $4.84 +230) DD -33.6% ww -1228 stops 0.53(0.23) | n/a |
| H7 asia | both/g0.5/H75 | n/a | -574 (live -1004; $4.84 -580) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g0.5/H75 | n/a | -697 (live -1219; $4.84 -703) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g1.0/H50 | n/a | -355 (live -621; $4.84 -372) DD -120.5% ww -2166 stops 0.53(0.23) | n/a |
| H7 nyam | narrow/g1.0/H50 | n/a | +252 (live +441; $4.84 +252) DD +60.4% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | both/g1.0/H75 | n/a | +281 (live +491; $4.84 +280) DD +57.7% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | narrow/g1.0/H75 | -187 (live -328; $4.84 -188) DD -4.0% ww +0 stops 0.53(0.46) | +258 (live +452; $4.84 +258) DD +57.7% ww +480 stops 0.30(0.38) | +35 (live +62; $4.84 +35) DD +24.1% ww +480 stops 0.42(0.42) |
| H7 nyam | both/g0.0/H50 | -58 (live -102; $4.84 -58) DD +9.4% ww +0 stops 0.46(0.46) | +221 (live +387; $4.84 +221) DD +54.7% ww +195 stops 0.15(0.38) | +82 (live +143; $4.84 +81) DD +33.9% ww +195 stops 0.30(0.42) |
| H7 nyam | both/g0.5/H75 | +103 (live +180; $4.84 +103) DD +29.2% ww -83 stops 0.46(0.46) | +87 (live +153; $4.84 +87) DD +2.2% ww +195 stops 0.38(0.38) | +95 (live +167; $4.84 +95) DD +2.2% ww +195 stops 0.42(0.42) |
| H7 nyam | narrow/g0.5/H75 | n/a | +77 (live +134; $4.84 +77) DD +2.2% ww +195 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g0.5/H75 | n/a | +11 (live +19; $4.84 +11) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H75 | n/a | +22 (live +39; $4.84 +22) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H50 | n/a | +30 (live +53; $4.84 +30) DD +0.0% ww +0 stops 0.30(0.38) | n/a |
| K7 asia | wide/g1.0/H75 | n/a | +297 (live +520; $4.84 +298) DD +0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | wide/g0.5/H75 | n/a | -54 (live -94; $4.84 -54) DD -0.7% ww -404 stops 0.00(0.00) | n/a |
| K7 asia | narrow/g0.5/H75 | n/a | +1877 (live +3285; $4.84 +1855) DD -19.6% ww -2412 stops 0.00(0.00) | n/a |
| K7 asia | both/g0.5/H75 | n/a | +1823 (live +3191; $4.84 +1801) DD -28.8% ww -3232 stops 0.00(0.00) | n/a |
| K7 asia | wide/g1.0/H50 | n/a | -401 (live -702; $4.84 -400) DD -35.9% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | both/g1.0/H75 | n/a | +1292 (live +2261; $4.84 +1220) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H75 | n/a | +912 (live +1595; $4.84 +838) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H50 | n/a | +355 (live +621; $4.84 +268) DD -86.2% ww -5644 stops 0.00(0.00) | n/a |
| K7 london | both/g0.5/H75 | n/a | -9 (live -15; $4.84 -14) DD +8.7% ww +4326 stops 0.23(0.30) | n/a |
| K7 london | wide/g0.5/H75 | n/a | +27 (live +48; $4.84 +29) DD +0.5% ww +0 stops 0.30(0.30) | n/a |
| K7 london | wide/g1.0/H50 | n/a | +431 (live +755; $4.84 +433) DD -3.3% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g0.5/H75 | n/a | -123 (live -215; $4.84 -130) DD -4.2% ww +4733 stops 0.23(0.30) | n/a |
| K7 london | wide/g1.0/H75 | n/a | +157 (live +274; $4.84 +160) DD -4.8% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g1.0/H50 | n/a | -182 (live -319; $4.84 -204) DD -13.7% ww +3097 stops 0.23(0.30) | n/a |
| K7 london | both/g1.0/H75 | n/a | +481 (live +841; $4.84 +462) DD -25.5% ww +4257 stops 0.38(0.30) | n/a |
| K7 london | narrow/g1.0/H75 | n/a | -31 (live -55; $4.84 -55) DD -42.3% ww +4122 stops 0.38(0.30) | n/a |
| K7 nyam | both/g0.0/H50 | -645 (live -1129; $4.84 -647) DD -55.9% ww -1158 stops 0.08(0.08) | +805 (live +1408; $4.84 +793) DD +62.7% ww +1729 stops 0.00(0.00) | +80 (live +139; $4.84 +73) DD +44.5% ww +1153 stops 0.04(0.04) |
| K7 nyam | both/g0.0/H50 | -488 (live -855; $4.84 -488) DD -38.7% ww -514 stops 0.08(0.08) | +1078 (live +1886; $4.84 +1069) DD +53.9% ww +1605 stops 0.00(0.00) | +295 (live +516; $4.84 +290) DD +50.6% ww +1605 stops 0.04(0.04) |
| K7 nyam | narrow/g1.0/H50 | n/a | +769 (live +1345; $4.84 +761) DD +51.0% ww +2185 stops 0.00(0.00) | n/a |
| K7 nyam | both/g1.0/H75 | n/a | +1160 (live +2030; $4.84 +1153) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g1.0/H75 | n/a | +984 (live +1722; $4.84 +977) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g0.5/H75 | n/a | +668 (live +1170; $4.84 +667) DD +40.3% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | both/g0.5/H75 | n/a | +806 (live +1410; $4.84 +805) DD +39.5% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H75 | n/a | +176 (live +308; $4.84 +176) DD -0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H50 | n/a | +252 (live +441; $4.84 +253) DD -0.3% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g0.5/H75 | n/a | +137 (live +241; $4.84 +137) DD -0.8% ww +0 stops 0.00(0.00) | n/a |
| K7 nypm | wide/g1.0/H50 | n/a | +442 (live +773; $4.84 +442) DD +17.3% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | wide/g1.0/H75 | n/a | +70 (live +122; $4.84 +70) DD +13.1% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | both/g1.0/H75 | n/a | -184 (live -322; $4.84 -197) DD +9.8% ww +1145 stops 0.15(0.08) | n/a |
| K7 nypm | wide/g0.5/H75 | n/a | -4 (live -8; $4.84 -4) DD -1.5% ww -38 stops 0.00(0.08) | n/a |
| K7 nypm | narrow/g1.0/H50 | n/a | +48 (live +84; $4.84 +32) DD -1.9% ww +105 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g1.0/H75 | n/a | -254 (live -445; $4.84 -267) DD -3.3% ww +990 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g0.5/H75 | n/a | -266 (live -465; $4.84 -269) DD -26.7% ww +140 stops 0.08(0.08) | n/a |
| K7 nypm | both/g0.5/H75 | n/a | -270 (live -473; $4.84 -274) DD -27.3% ww +102 stops 0.00(0.08) | n/a |
| M7 london | wide/g1.0/H75 | n/a | +1614 (live +2824; $4.84 +1616) DD +4.9% ww +1190 stops 0.53(0.91) | n/a |
| M7 london | wide/g0.5/H75 | n/a | +688 (live +1204; $4.84 +689) DD +4.4% ww +1400 stops 0.84(0.91) | n/a |
| M7 london | wide/g1.0/H50 | n/a | +538 (live +942; $4.84 +540) DD -1.3% ww -80 stops 0.84(0.91) | n/a |
| M7 london | both/g0.5/H75 | n/a | +1147 (live +2008; $4.84 +1139) DD -8.1% ww +130 stops 1.07(0.91) | n/a |
| M7 london | narrow/g0.5/H75 | n/a | +417 (live +730; $4.84 +408) DD -10.9% ww -1075 stops 1.14(0.91) | n/a |
| M7 london | narrow/g1.0/H50 | n/a | +476 (live +833; $4.84 +446) DD -19.9% ww +1144 stops 1.45(0.91) | n/a |
| M7 london | narrow/g1.0/H75 | n/a | -366 (live -640; $4.84 -390) DD -20.4% ww +80 stops 1.29(0.91) | n/a |
| M7 london | both/g1.0/H75 | n/a | +1142 (live +1999; $4.84 +1121) DD -23.2% ww -729 stops 0.91(0.91) | n/a |
| M7 nyam | narrow/g1.0/H50 | n/a | +439 (live +769; $4.84 +424) DD +26.0% ww -222 stops 0.38(0.23) | n/a |
| M7 nyam | both/g0.5/H75 | n/a | +79 (live +138; $4.84 +75) DD +0.8% ww +194 stops 0.30(0.23) | n/a |
| M7 nyam | narrow/g0.5/H75 | n/a | +73 (live +127; $4.84 +69) DD +0.8% ww +194 stops 0.38(0.23) | n/a |
| M7 nyam | wide/g0.5/H75 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H75 | n/a | +16 (live +28; $4.84 +16) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H50 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | both/g1.0/H75 | n/a | +419 (live +733; $4.84 +405) DD -6.8% ww -991 stops 0.46(0.23) | n/a |
| M7 nyam | narrow/g1.0/H75 | n/a | +402 (live +704; $4.84 +388) DD -6.8% ww -991 stops 0.53(0.23) | n/a |
| M7 nyam | both/g0.0/H50 | -130 (live -227; $4.84 -131) DD -16.3% ww -1329 stops 0.61(0.61) | +102 (live +179; $4.84 +99) DD -11.5% ww +0 stops 0.23(0.23) | -14 (live -24; $4.84 -16) DD -19.5% ww -1329 stops 0.42(0.42) |
| P7 asia | both/g0.0/H50 | -5189 (live -9081; $4.84 -4987) DD +44.9% ww +11844 stops 0.00(0.00) | -703 (live -1230; $4.84 -620) DD +51.2% ww +20259 stops 0.08(0.15) | -2946 (live -5156; $4.84 -2804) DD +51.2% ww +17717 stops 0.04(0.08) |
| P7 asia | both/g0.0/H50 | -6897 (live -12069; $4.84 -6699) DD +42.2% ww +13069 stops 0.00(0.00) | -322 (live -564; $4.84 -245) DD +51.2% ww +19309 stops 0.08(0.15) | -3609 (live -6317; $4.84 -3472) DD +51.2% ww +18942 stops 0.04(0.08) |
| P7 asia | narrow/g1.0/H50 | n/a | -3918 (live -6857; $4.84 -4186) DD -0.4% ww -4286 stops 0.46(0.15) | n/a |
| P7 asia | both/g0.5/H75 | n/a | -5946 (live -10406; $4.84 -6044) DD -1.0% ww +6944 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g0.5/H75 | n/a | -5762 (live -10084; $4.84 -5860) DD -1.0% ww +9022 stops 0.15(0.15) | n/a |
| P7 asia | wide/g0.5/H75 | n/a | -184 (live -322; $4.84 -183) DD -4.9% ww -2079 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g1.0/H75 | n/a | -2696 (live -4718; $4.84 -2882) DD -7.8% ww -10346 stops 0.53(0.15) | n/a |
| P7 asia | wide/g1.0/H50 | n/a | -816 (live -1428; $4.84 -812) DD -22.6% ww -9033 stops 0.15(0.15) | n/a |
| P7 asia | wide/g1.0/H75 | n/a | -491 (live -858; $4.84 -490) DD -25.2% ww -10331 stops 0.15(0.15) | n/a |
| P7 asia | both/g1.0/H75 | n/a | -3315 (live -5802; $4.84 -3501) DD -36.1% ww -13164 stops 0.53(0.15) | n/a |
| P7 london | both/g0.5/H75 | n/a | +894 (live +1565; $4.84 +886) DD +29.6% ww -1633 stops 0.08(0.08) | n/a |
| P7 london | narrow/g0.5/H75 | n/a | +386 (live +675; $4.84 +375) DD +28.5% ww -1328 stops 0.08(0.08) | n/a |
| P7 london | narrow/g1.0/H50 | n/a | +927 (live +1622; $4.84 +895) DD +19.7% ww -3009 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H75 | n/a | -142 (live -249; $4.84 -138) DD +2.7% ww -458 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H50 | n/a | +265 (live +464; $4.84 +266) DD +1.1% ww +0 stops 0.08(0.08) | n/a |
| P7 london | wide/g0.5/H75 | n/a | +385 (live +674; $4.84 +387) DD -1.9% ww -238 stops 0.08(0.08) | n/a |
| P7 london | both/g1.0/H75 | n/a | +1179 (live +2064; $4.84 +1145) DD -9.8% ww -5408 stops 0.15(0.08) | n/a |
| P7 london | narrow/g1.0/H75 | n/a | +1322 (live +2313; $4.84 +1282) DD -14.4% ww -5203 stops 0.15(0.08) | n/a |
| P7 nyam | both/g0.0/H50 | -1333 (live -2333; $4.84 -1305) DD +88.2% ww +6983 stops 0.00(0.08) | +198 (live +346; $4.84 +220) DD +55.7% ww +1594 stops 0.15(0.38) | -568 (live -994; $4.84 -542) DD +59.1% ww +4666 stops 0.08(0.23) |
| P7 nyam | both/g1.0/H75 | n/a | +697 (live +1220; $4.84 +685) DD +51.3% ww +354 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g1.0/H75 | n/a | +543 (live +951; $4.84 +529) DD +45.9% ww +324 stops 0.30(0.38) | n/a |
| P7 nyam | both/g0.5/H75 | n/a | +105 (live +184; $4.84 +99) DD +36.7% ww +238 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g0.5/H75 | n/a | -13 (live -23; $4.84 -20) DD +36.4% ww +262 stops 0.30(0.38) | n/a |
| P7 nyam | wide/g0.5/H75 | n/a | +118 (live +207; $4.84 +119) DD +0.3% ww -25 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H75 | n/a | +16 (live +27; $4.84 +17) DD -7.5% ww -105 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H50 | n/a | -544 (live -952; $4.84 -543) DD -47.7% ww -3348 stops 0.38(0.38) | n/a |
| U7 asia | narrow/g1.0/H50 | n/a | +1222 (live +2139; $4.84 +1201) DD +15.6% ww -265 stops 1.90(1.83) | n/a |
| U7 asia | both/g1.0/H75 | n/a | +71 (live +124; $4.84 +56) DD +8.3% ww -1836 stops 1.98(1.83) | n/a |
| U7 asia | narrow/g1.0/H75 | n/a | +502 (live +879; $4.84 +487) DD +8.3% ww +983 stops 1.98(1.83) | n/a |
| U7 asia | both/g0.5/H75 | n/a | -800 (live -1399; $4.84 -808) DD +6.6% ww -2883 stops 2.05(1.83) | n/a |
| U7 asia | narrow/g0.5/H75 | n/a | -162 (live -284; $4.84 -170) DD +6.6% ww +57 stops 2.05(1.83) | n/a |
| U7 asia | wide/g0.5/H75 | n/a | -637 (live -1115; $4.84 -637) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H75 | n/a | -431 (live -755; $4.84 -431) DD +0.0% ww -1836 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H50 | n/a | -648 (live -1134; $4.84 -648) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 london | narrow/g0.5/H75 | n/a | +393 (live +687; $4.84 +392) DD +17.2% ww +1796 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H75 | n/a | +246 (live +431; $4.84 +243) DD +3.1% ww -1185 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H50 | n/a | -41 (live -72; $4.84 -48) DD -9.9% ww -1991 stops 1.52(1.45) | n/a |
| U7 london | both/g0.5/H75 | n/a | -891 (live -1560; $4.84 -890) DD -25.4% ww -3538 stops 1.52(1.45) | n/a |
| U7 london | wide/g1.0/H50 | n/a | -839 (live -1468; $4.84 -837) DD -33.9% ww -4122 stops 1.37(1.45) | n/a |
| U7 london | wide/g0.5/H75 | n/a | -1284 (live -2247; $4.84 -1282) DD -44.3% ww -6280 stops 1.52(1.45) | n/a |
| U7 london | both/g1.0/H75 | n/a | -1728 (live -3025; $4.84 -1729) DD -105.5% ww -7540 stops 1.60(1.45) | n/a |
| U7 london | wide/g1.0/H75 | n/a | -1975 (live -3455; $4.84 -1972) DD -109.8% ww -6355 stops 1.60(1.45) | n/a |

### Summary per slice: pick made on May-Jul, result on L3M
| slice | pick | L3M result of the pick | verdict |
|---|---|---|---|
| A7 asia | pending | | |
| H7 asia | pending | | |
| H7 nyam | pending | | |
| K7 asia | pending | | |
| K7 london | pending | | |
| K7 nyam | pending | | |
| K7 nypm | pending | | |
| M7 london | pending | | |
| M7 nyam | pending | | |
| P7 asia | pending | | |
| P7 london | pending | | |
| P7 nyam | pending | | |
| U7 asia | pending | | |
| U7 london | pending | | |

### B2: why the global version adds full stops (narrow-only/both g1.0 H75 cell, L3M, trade tables)
Reference JN05W2 L3M (no O7): 1855 trades, stop rate 0.071, 132 stops (13 weeks).

**M1_75_g10_c1_d10_c20_tb_B**: 2038 trades (+183 vs JN05W2), stops 173 (+41), stop rate 0.085 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 437 | 0.103 | 3.05 | 94 |
| (40, 50] | 721 | 0.074 | 2.36 | 271 |
| (50, 55] | 232 | 0.099 | 1.97 | 169 |
| (55, 60] | 435 | 0.076 | 1.87 | 76 |
| (60, 70] | 75 | 0.120 | 2.01 | -385 |
| (70, 80] | 62 | 0.048 | 1.68 | -284 |
| (80, 101] | 76 | 0.092 | 1.13 | -591 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1543 | 0.069 | 2.21 | 54 |
| (3.0, 4.0] | 294 | 0.116 | 2.29 | 239 |
| (4.0, 5.0] | 74 | 0.108 | 2.31 | 364 |
| (5.0, 6.0] | 6 | 0.167 | 2.50 | 172 |
| (6.0, 8.0] | 4 | 0.000 | 1.00 | -119 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1068 | 0.096 | 1.00 | 4 |
| (1, 2] | 385 | 0.078 | 2.00 | 115 |
| (2, 3] | 215 | 0.093 | 3.00 | 23 |
| (3, 5] | 195 | 0.062 | 4.46 | 256 |
| (5, 8] | 138 | 0.065 | 6.70 | 690 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

**M1_75_g10_c1_d10_c20_tb_N**: 2072 trades (+217 vs JN05W2), stops 178 (+46), stop rate 0.086 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 449 | 0.105 | 3.02 | 97 |
| (40, 50] | 725 | 0.073 | 2.35 | 272 |
| (50, 55] | 236 | 0.102 | 1.97 | 150 |
| (55, 60] | 662 | 0.082 | 1.82 | -29 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1644 | 0.072 | 2.18 | 50 |
| (3.0, 4.0] | 264 | 0.121 | 2.38 | 348 |
| (4.0, 5.0] | 44 | 0.091 | 3.11 | 1063 |
| (5.0, 6.0] | 3 | 0.000 | 3.33 | 68 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1073 | 0.095 | 1.00 | 8 |
| (1, 2] | 413 | 0.085 | 2.00 | 117 |
| (2, 3] | 197 | 0.081 | 3.00 | 213 |
| (3, 5] | 217 | 0.074 | 4.43 | 196 |
| (5, 8] | 135 | 0.067 | 6.74 | 714 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

Reading of the W/ATR5 table: ATR5 = mean range of the last 14 five-minute buckets in points; a bracket 3x ATR5 or less is within ordinary 5-minute noise. The noise-floor cells (floor 3/4/5 x ATR5, narrowing only) are listed in B3.


### B3: levers (stop-only / target-only / both / size-only) and noise floor, per slice
| slice | cell | L3M | May-Jul |
|---|---|---|---|

### B4: assembled stack (each slice at its own walk-forward pick, run together)
(not run yet: starts when every slice has a pick)


## Target capped at the forecast
**VERDICT (plain, not a PASS; FIRST PASS; 15 of 26 global exact cap cells scored in L3M, per book x session exact cells still running): planted-edge check PASSED through the exact engine (look-ahead oracle target 0.9 x realised MFE: +85531 $/wk, DD +67.0%, ww +64263; this is a mechanism check, NOT a result); the reachable move is only weakly forecastable (R2 on ln MFE 0.03-0.14, quantile calibration good); in the exact L3M cells the cap at the forecast 50th-percentile move (horizon = 75th-percentile holding time) gives +1486 $/wk, DD -0.5%, ww -240 and the 75th-percentile cap +177 $/wk, DD +0.0%, ww +0, the remaining-range caps cut drawdown (own k1.0 -6226 $/wk, DD +27.0%, ww +12290; HAR k1.0 -7259 $/wk, DD +39.4%, ww +17319) but cost thousands per week. Best exact L3M cap cell inside the mean gate by DD: PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time (DD +7.9%, -120 $/wk). L6M/HOLD/older still to run before any verdict.**

Planted-edge check (H1) for the capping mechanism: cells `tcoracle0.9` / `0.6` set the target to 0.9 / 0.6 x the REALISED maximum favourable move (look-ahead, only to prove the mechanism can show an edge through the exact engine); they must come out strongly positive. Status below in the exact table. Until they do, an exact cap verdict is not stated.

Definition. Reachable move = maximum favourable excursion from the signal-second bar close over the book-session holding horizon H (H50/H75 = median / 75th percentile holding time of that book+session, causal), points. Model: walk-forward ridge (14-day blocks, expanding, min 90 days, per session) on ln((MFE+2)/price) from the Dial 10 own-bar inputs (last 15/30/60/120 min range and vol, same-clock normal, own session level, range used so far, elapsed fraction) plus the side-aware room in the session range so far; quantiles q = fitted + empirical training-residual quantile (50/60/75/90). Cap: target = min(book target 60 pts [58 after fills], q-quantile), stop, lots and every other level unchanged. Remaining-range cap: target = min(book target, k x (session range forecast - range printed so far)), forecast = own (price x exp(sf20), mean of the last 20 sessions) or T-RANGE2 HAR (fc_r2_har, available-epoch checked). Small caps (< 30 pts = 0.5 x stop): take / skip / half. EV target: argmax over T in [20, book target or 300] of T x P(MFE>=T) - stop x (1-P) with the lognormal forecast (ignores the stop-first ordering, so optimistic). Extension: if the forecast median MFE is >= m x book target, target = min(q50, 2 x book target). Lots/base basis: dollars are BASE lots (live x1.75 = multiply by 1.75); fee columns $4.84 beside raw $1.18 where shown.

### Item 1: calibration of the forecast quantiles (share of trades whose realized MFE exceeded the forecast quantile; a q-quantile should be exceeded 1-q of the time = 0.50 / 0.40 / 0.25 / 0.10) and R2 of ln MFE, per session
| H | session | window | n | >q50 | >q60 | >q75 | >q90 | R2 ln MFE | median q75 (pts) | share q75 < 60 |
|---|---|---|---|---|---|---|---|---|---|---|
| 50 | asia | older (<2026-05) | 5119 | 0.51 | 0.41 | 0.26 | 0.12 | 0.121 | 80 | 0.222 |
| 50 | asia | L6M | 2006 | 0.49 | 0.38 | 0.23 | 0.08 | 0.058 | 111 | 0.047 |
| 50 | asia | L3M | 875 | 0.46 | 0.34 | 0.20 | 0.07 | -0.014 | 90 | 0.098 |
| 50 | london | older (<2026-05) | 4892 | 0.51 | 0.41 | 0.26 | 0.11 | 0.142 | 62 | 0.438 |
| 50 | london | L6M | 1406 | 0.48 | 0.37 | 0.23 | 0.08 | 0.028 | 76 | 0.166 |
| 50 | london | L3M | 673 | 0.48 | 0.37 | 0.24 | 0.07 | -0.008 | 68 | 0.247 |
| 50 | nyam | older (<2026-05) | 4142 | 0.47 | 0.38 | 0.24 | 0.11 | 0.077 | 63 | 0.397 |
| 50 | nyam | L6M | 600 | 0.51 | 0.40 | 0.24 | 0.09 | 0.097 | 83 | 0.157 |
| 50 | nyam | L3M | 271 | 0.51 | 0.38 | 0.20 | 0.06 | 0.077 | 68 | 0.258 |
| 50 | nypm | older (<2026-05) | 817 | 0.48 | 0.40 | 0.26 | 0.13 | 0.073 | 62 | 0.419 |
| 50 | nypm | L6M | 150 | 0.59 | 0.50 | 0.33 | 0.13 | 0.221 | 71 | 0.307 |
| 50 | nypm | L3M | 56 | 0.50 | 0.36 | 0.21 | 0.09 | 0.104 | 54 | 0.589 |
| 50 | all | older (<2026-05) | 14970 | 0.50 | 0.40 | 0.26 | 0.12 | 0.123 | 68 | 0.352 |
| 50 | all | L6M | 4162 | 0.49 | 0.38 | 0.23 | 0.08 | 0.080 | 91 | 0.113 |
| 50 | all | L3M | 1875 | 0.47 | 0.36 | 0.21 | 0.07 | 0.014 | 76 | 0.189 |
| 75 | asia | older (<2026-05) | 5119 | 0.52 | 0.41 | 0.26 | 0.12 | 0.134 | 122 | 0.032 |
| 75 | asia | L6M | 2006 | 0.50 | 0.40 | 0.24 | 0.08 | 0.027 | 178 | 0.000 |
| 75 | asia | L3M | 875 | 0.45 | 0.35 | 0.20 | 0.05 | -0.016 | 156 | 0.000 |
| 75 | london | older (<2026-05) | 4891 | 0.51 | 0.42 | 0.27 | 0.11 | 0.157 | 101 | 0.100 |
| 75 | london | L6M | 1406 | 0.49 | 0.37 | 0.21 | 0.08 | 0.069 | 118 | 0.001 |
| 75 | london | L3M | 673 | 0.49 | 0.38 | 0.21 | 0.09 | 0.025 | 108 | 0.000 |
| 75 | nyam | older (<2026-05) | 4142 | 0.48 | 0.38 | 0.23 | 0.10 | 0.065 | 91 | 0.081 |
| 75 | nyam | L6M | 600 | 0.50 | 0.40 | 0.24 | 0.10 | 0.098 | 125 | 0.015 |
| 75 | nyam | L3M | 271 | 0.44 | 0.34 | 0.19 | 0.05 | 0.051 | 103 | 0.015 |
| 75 | nypm | older (<2026-05) | 812 | 0.49 | 0.37 | 0.26 | 0.11 | 0.043 | 87 | 0.095 |
| 75 | nypm | L6M | 150 | 0.53 | 0.46 | 0.34 | 0.17 | 0.179 | 117 | 0.013 |
| 75 | nypm | L3M | 56 | 0.41 | 0.30 | 0.21 | 0.07 | -0.076 | 93 | 0.036 |
| 75 | all | older (<2026-05) | 14964 | 0.51 | 0.40 | 0.25 | 0.11 | 0.131 | 102 | 0.071 |
| 75 | all | L6M | 4162 | 0.50 | 0.39 | 0.23 | 0.09 | 0.079 | 149 | 0.003 |
| 75 | all | L3M | 1875 | 0.46 | 0.36 | 0.20 | 0.06 | 0.032 | 128 | 0.003 |

### Items 3 and 4 (and 2): offline replay of the caps on the JN05W2 trade paths, all 43 months (estimate: 1-min paths, cap counted only before the exit bar, so cut/stop ordering is conservative; the exact cells below decide). d mean $/wk and DD cut % vs JN05W2 on the same trades, scope all, then per session for the cap with the most trades capped
| cap | small-cap rule | scope | window | d mean $/wk (live x1.75) | DD cut % | d worst week | d stops/wk | share capped | share where cap hit |
|---|---|---|---|---|---|---|---|---|---|
| q50_H50 | take | all | L3M | +409 (+715) | -3.9 | -1411 | +0.00 | 0.82 | 0.45 |
| q50_H50 | take | all | L6M | -96 (-169) | -3.9 | -1411 | +0.00 | 0.62 | 0.33 |
| q50_H50 | take | all | OLDER | -1795 (-3141) | +12.0 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | skip | all | L3M | -1581 (-2767) | -5.0 | -1996 | +0.00 | 0.82 | 0.45 |
| q50_H50 | skip | all | L6M | -1445 (-2528) | -5.0 | -1996 | +0.00 | 0.62 | 0.33 |
| q50_H50 | skip | all | OLDER | -2271 (-3975) | +17.4 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | half | all | L3M | -586 (-1026) | -4.4 | -1704 | +0.00 | 0.82 | 0.45 |
| q50_H50 | half | all | L6M | -771 (-1348) | -4.4 | -1704 | +0.00 | 0.62 | 0.33 |
| q50_H50 | half | all | OLDER | -2033 (-3558) | +16.5 | +13127 | +0.00 | 0.80 | 0.45 |
| q60_H50 | take | all | L3M | -1525 (-2668) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | take | all | L6M | -839 (-1469) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | take | all | OLDER | -1296 (-2267) | +12.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | skip | all | L3M | -3272 (-5726) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | skip | all | L6M | -1811 (-3170) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | skip | all | OLDER | -1648 (-2885) | +8.8 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | half | all | L3M | -2398 (-4197) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | half | all | L6M | -1325 (-2319) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | half | all | OLDER | -1472 (-2576) | +10.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q75_H50 | take | all | L3M | +414 (+725) | -0.4 | -214 | +0.00 | 0.21 | 0.11 |
| q75_H50 | take | all | L6M | -44 (-77) | -0.4 | -214 | +0.00 | 0.13 | 0.06 |
| q75_H50 | take | all | OLDER | -719 (-1258) | -1.1 | +13801 | +0.00 | 0.37 | 0.18 |
| q90_H50 | take | all | L3M | +191 (+334) | +0.0 | +0 | +0.00 | 0.02 | 0.01 |
| q90_H50 | take | all | L6M | +142 (+249) | +0.0 | +0 | +0.00 | 0.01 | 0.01 |
| q90_H50 | take | all | OLDER | -169 (-296) | -1.8 | +1686 | +0.00 | 0.08 | 0.03 |
| q50_H75 | take | all | L3M | +128 (+225) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | take | all | L6M | +624 (+1092) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | take | all | OLDER | -931 (-1628) | -13.1 | +11346 | +0.00 | 0.51 | 0.26 |
| q50_H75 | skip | all | L3M | +178 (+312) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | skip | all | L6M | +685 (+1198) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | skip | all | OLDER | -1302 (-2279) | -4.6 | +14384 | +0.00 | 0.51 | 0.26 |
| q50_H75 | half | all | L3M | +153 (+268) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | half | all | L6M | +654 (+1145) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | half | all | OLDER | -1116 (-1954) | -8.8 | +12865 | +0.00 | 0.51 | 0.26 |
| q60_H75 | take | all | L3M | +830 (+1452) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | take | all | L6M | +379 (+664) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | take | all | OLDER | -478 (-836) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | skip | all | L3M | +958 (+1677) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | skip | all | L6M | +421 (+737) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | skip | all | OLDER | -402 (-703) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | half | all | L3M | +894 (+1564) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | half | all | L6M | +400 (+700) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | half | all | OLDER | -440 (-769) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q75_H75 | take | all | L3M | +236 (+413) | +0.0 | +0 | +0.00 | 0.01 | 0.00 |
| q75_H75 | take | all | L6M | +105 (+185) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q75_H75 | take | all | OLDER | -255 (-446) | -1.9 | +1485 | +0.00 | 0.08 | 0.04 |
| q90_H75 | take | all | L3M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | L6M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | OLDER | +10 (+18) | -0.4 | +0 | +0.00 | 0.01 | 0.00 |
| rem_own_k0.5 | take | all | L3M | -6674 (-11680) | +8.8 | -1861 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | take | all | L6M | -13204 (-23108) | +8.7 | -1861 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | take | all | OLDER | -7381 (-12916) | -40.2 | +20529 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | skip | all | L3M | -5271 (-9225) | +21.7 | +2982 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | skip | all | L6M | -10625 (-18594) | +21.7 | +2982 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | skip | all | OLDER | -6272 (-10977) | +17.3 | +21712 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | half | all | L3M | -5973 (-10452) | +16.3 | +560 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | half | all | L6M | -11915 (-20851) | +16.3 | +560 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | half | all | OLDER | -6827 (-11946) | +0.6 | +23150 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.75 | take | all | L3M | -7140 (-12494) | +9.6 | +3294 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | take | all | L6M | -10636 (-18614) | +9.6 | +3294 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | take | all | OLDER | -5846 (-10230) | -24.0 | +12208 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | skip | all | L3M | -3661 (-6406) | +10.3 | +4045 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | skip | all | L6M | -6650 (-11638) | +10.3 | +4045 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | skip | all | OLDER | -3856 (-6749) | +16.1 | +19073 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | half | all | L3M | -5400 (-9450) | +13.0 | +3670 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | half | all | L6M | -8643 (-15126) | +13.0 | +3670 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | half | all | OLDER | -4851 (-8489) | +13.0 | +20157 | +0.00 | 0.73 | 0.53 |
| rem_own_k1.0 | take | all | L3M | -5516 (-9653) | +18.3 | +9104 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | take | all | L6M | -8765 (-15339) | +18.3 | +9104 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | take | all | OLDER | -5714 (-9999) | -58.2 | +11926 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | skip | all | L3M | -3265 (-5714) | +15.0 | +8858 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | skip | all | L6M | -5683 (-9944) | +15.0 | +8858 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | skip | all | OLDER | -3872 (-6775) | -61.0 | +20250 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | half | all | L3M | -4391 (-7683) | +18.5 | +8981 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | half | all | L6M | -7224 (-12642) | +18.5 | +8981 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | half | all | OLDER | -4793 (-8387) | -58.0 | +21393 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.25 | take | all | L3M | -3112 (-5446) | +24.4 | +13750 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | take | all | L6M | -8275 (-14481) | +24.4 | +13750 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | take | all | OLDER | -5400 (-9450) | -15.5 | +4336 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | skip | all | L3M | -456 (-797) | +22.4 | +13720 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | skip | all | L6M | -4232 (-7405) | +22.4 | +13720 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | skip | all | OLDER | -3310 (-5792) | -36.4 | +22803 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | half | all | L3M | -1784 (-3121) | +25.2 | +15286 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | half | all | L6M | -6253 (-10943) | +25.2 | +15286 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | half | all | OLDER | -4355 (-7621) | -18.3 | +15544 | +0.00 | 0.54 | 0.41 |

Per session, q60 H75 take-anyway and remaining-range k=1.25 (own):
| cap | session | window | d mean $/wk | DD cut % | d worst week | share capped |
|---|---|---|---|---|---|---|
| q60_H75 | asia | L3M | +221 | +0.0 | +0 | 0.02 |
| q60_H75 | asia | L6M | +110 | +0.0 | +0 | 0.01 |
| q60_H75 | asia | OLDER | -124 | -0.0 | +0 | 0.23 |
| q60_H75 | london | L3M | +745 | +3.8 | +0 | 0.16 |
| q60_H75 | london | L6M | +330 | +3.8 | +0 | 0.12 |
| q60_H75 | london | OLDER | -294 | -2.1 | +0 | 0.35 |
| q60_H75 | nyam | L3M | +61 | -7.2 | +0 | 0.15 |
| q60_H75 | nyam | L6M | -14 | +0.0 | +0 | 0.10 |
| q60_H75 | nyam | OLDER | -37 | -6.0 | +1403 | 0.37 |
| q60_H75 | nypm | L3M | -197 | -0.0 | +0 | 0.41 |
| q60_H75 | nypm | L6M | -47 | +0.0 | +0 | 0.20 |
| q60_H75 | nypm | OLDER | -22 | -5.4 | +0 | 0.33 |
| rem_own_k1.25 | asia | L3M | -4547 | +35.2 | +434 | 0.37 |
| rem_own_k1.25 | asia | L6M | -6717 | +27.1 | +434 | 0.38 |
| rem_own_k1.25 | asia | OLDER | -4532 | -27.4 | +10774 | 0.62 |
| rem_own_k1.25 | london | L3M | +2278 | +46.3 | +12347 | 0.24 |
| rem_own_k1.25 | london | L6M | +1196 | +46.3 | +12347 | 0.30 |
| rem_own_k1.25 | london | OLDER | -510 | +12.9 | +3024 | 0.51 |
| rem_own_k1.25 | nyam | L3M | -650 | +20.0 | +0 | 0.24 |
| rem_own_k1.25 | nyam | L6M | -2127 | -8.9 | +1531 | 0.39 |
| rem_own_k1.25 | nyam | OLDER | -53 | +10.3 | +7327 | 0.47 |
| rem_own_k1.25 | nypm | L3M | -192 | +21.8 | +1203 | 0.45 |
| rem_own_k1.25 | nypm | L6M | -627 | +21.8 | +1203 | 0.50 |
| rem_own_k1.25 | nypm | OLDER | -304 | -2.4 | -831 | 0.50 |

### Item 4 per book x session (all 43 months): trades whose 60-pt target lies beyond the forecast quantile, their fixed-target result, the capped replay, and how far trades run past the cap
| book | session | cap | trades | share beyond | fixed-target hit rate | fixed avg $/trade | capped avg $/trade | avg points run past cap |
|---|---|---|---|---|---|---|---|---|
| A7 | asia | q50_H75 | 1156 | 0.25 | 0.50 | 60 | 87 | 10.4 |
| A7 | asia | q60_H75 | 1156 | 0.13 | 0.47 | 4 | 26 | 8.8 |
| A7 | asia | q75_H75 | 1156 | 0.03 | 0.48 | 19 | 6 | 11.1 |
| A7 | asia | rem_own_k0.75 | 1156 | 0.74 | 0.52 | 126 | 22 | 32.9 |
| H7 | asia | q50_H75 | 700 | 0.33 | 0.49 | 164 | 181 | 11.3 |
| H7 | asia | q60_H75 | 700 | 0.18 | 0.56 | 447 | 414 | 10.7 |
| H7 | asia | q75_H75 | 700 | 0.02 | 0.50 | -318 | -267 | 16.1 |
| H7 | asia | rem_own_k0.75 | 700 | 0.71 | 0.48 | 208 | 55 | 27.8 |
| H7 | nyam | q50_H75 | 348 | 0.49 | 0.46 | 84 | 25 | 8.9 |
| H7 | nyam | q60_H75 | 348 | 0.25 | 0.47 | 96 | 46 | 7.4 |
| H7 | nyam | q75_H75 | 348 | 0.06 | 0.33 | -113 | -12 | 4.7 |
| H7 | nyam | rem_own_k0.75 | 348 | 0.66 | 0.47 | 62 | -35 | 23.3 |
| K7 | asia | q50_H75 | 2596 | 0.32 | 0.44 | 102 | 74 | 9.7 |
| K7 | asia | q60_H75 | 2596 | 0.19 | 0.44 | 111 | 90 | 7.6 |
| K7 | asia | q75_H75 | 2596 | 0.04 | 0.40 | 26 | 1 | 6.1 |
| K7 | asia | rem_own_k0.75 | 2596 | 0.68 | 0.44 | 88 | 0 | 27.2 |
| K7 | london | q50_H75 | 1781 | 0.57 | 0.43 | 62 | 37 | 10.9 |
| K7 | london | q60_H75 | 1781 | 0.33 | 0.44 | 60 | 35 | 9.4 |
| K7 | london | q75_H75 | 1781 | 0.12 | 0.48 | 138 | 101 | 6.5 |
| K7 | london | rem_own_k0.75 | 1781 | 0.69 | 0.43 | 45 | -12 | 27.4 |
| K7 | nyam | q50_H75 | 1565 | 0.57 | 0.42 | 21 | 18 | 10.0 |
| K7 | nyam | q60_H75 | 1565 | 0.32 | 0.40 | -4 | -17 | 9.0 |
| K7 | nyam | q75_H75 | 1565 | 0.07 | 0.41 | 40 | 36 | 16.3 |
| K7 | nyam | rem_own_k0.75 | 1565 | 0.70 | 0.39 | -21 | -38 | 26.0 |
| K7 | nypm | q50_H75 | 1136 | 0.50 | 0.36 | 65 | 54 | 8.1 |
| K7 | nypm | q60_H75 | 1136 | 0.31 | 0.34 | 62 | 48 | 5.6 |
| K7 | nypm | q75_H75 | 1136 | 0.09 | 0.29 | 155 | 179 | 3.5 |
| K7 | nypm | rem_own_k0.75 | 1136 | 0.71 | 0.37 | 72 | -30 | 23.7 |
| M7 | london | q50_H75 | 2489 | 0.42 | 0.43 | 45 | 40 | 10.0 |
| M7 | london | q60_H75 | 2489 | 0.24 | 0.43 | 32 | 26 | 8.2 |
| M7 | london | q75_H75 | 2489 | 0.06 | 0.38 | -74 | -97 | 7.1 |
| M7 | london | rem_own_k0.75 | 2489 | 0.59 | 0.39 | -40 | -29 | 22.9 |
| M7 | nyam | q50_H75 | 1496 | 0.52 | 0.43 | 49 | 22 | 8.6 |
| M7 | nyam | q60_H75 | 1496 | 0.27 | 0.44 | 76 | 57 | 7.2 |
| M7 | nyam | q75_H75 | 1496 | 0.06 | 0.44 | 127 | 131 | 4.9 |
| M7 | nyam | rem_own_k0.75 | 1496 | 0.69 | 0.42 | 30 | -36 | 27.3 |
| O7 | nyam | q50_H75 | 452 | 0.58 | 0.32 | 205 | 91 | 20.5 |
| O7 | nyam | q60_H75 | 452 | 0.37 | 0.31 | 156 | 118 | 16.9 |
| O7 | nyam | q75_H75 | 452 | 0.08 | 0.20 | -192 | -145 | 9.5 |
| O7 | nyam | rem_own_k0.75 | 452 | 0.31 | 0.30 | 120 | 82 | 20.6 |
| P7 | asia | q50_H75 | 2161 | 0.29 | 0.46 | 391 | 341 | 10.2 |
| P7 | asia | q60_H75 | 2161 | 0.16 | 0.48 | 487 | 484 | 9.3 |
| P7 | asia | q75_H75 | 2161 | 0.02 | 0.55 | 1227 | 969 | 5.7 |
| P7 | asia | rem_own_k0.75 | 2161 | 0.70 | 0.44 | 447 | 130 | 26.6 |
| P7 | london | q50_H75 | 1537 | 0.62 | 0.38 | 74 | 27 | 10.0 |
| P7 | london | q60_H75 | 1537 | 0.41 | 0.38 | 67 | 36 | 7.8 |
| P7 | london | q75_H75 | 1537 | 0.15 | 0.41 | 124 | 59 | 5.3 |
| P7 | london | rem_own_k0.75 | 1537 | 0.72 | 0.37 | -19 | -13 | 23.8 |
| P7 | nyam | q50_H75 | 1050 | 0.72 | 0.38 | 38 | 150 | 13.2 |
| P7 | nyam | q60_H75 | 1050 | 0.48 | 0.37 | -7 | 28 | 10.9 |
| P7 | nyam | q75_H75 | 1050 | 0.15 | 0.33 | -88 | -96 | 13.3 |
| P7 | nyam | rem_own_k0.75 | 1050 | 0.71 | 0.37 | -43 | 67 | 33.2 |
| U7 | asia | q50_H75 | 686 | 0.28 | 0.54 | 412 | 320 | 10.4 |
| U7 | asia | q60_H75 | 686 | 0.15 | 0.50 | 322 | 270 | 8.0 |
| U7 | asia | q75_H75 | 686 | 0.03 | 0.47 | -260 | -383 | 6.8 |
| U7 | asia | rem_own_k0.75 | 686 | 0.74 | 0.53 | 375 | 4 | 30.5 |
| U7 | london | q50_H75 | 645 | 0.27 | 0.46 | -102 | -183 | 8.7 |
| U7 | london | q60_H75 | 645 | 0.13 | 0.46 | -173 | -182 | 7.8 |
| U7 | london | q75_H75 | 645 | 0.03 | 0.50 | -396 | -466 | 5.4 |
| U7 | london | rem_own_k0.75 | 645 | 0.68 | 0.51 | 166 | 14 | 24.5 |

### Exact cap cells (global: all books at once; L3M, L6M when promoted; delta vs JN05W2)
| cell | L3M | L6M | HOLD | d mean/wk at $4.84 L3M |
|---|---|---|---|---|
| quantile 50 cap, horizon = 75th-percentile holding time | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | +1452 (lots +9/wk) |
| quantile 60 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 75 cap, horizon = 75th-percentile holding time | +177 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 101%, w2l 0 | n/a | n/a | +176 (lots +0/wk) |
| quantile 90 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 60 cap, horizon = median holding time | -1554 $/wk, DD +2.5%, ww +1445, stops 10.42(10.35), b5 89%, w2l 1 | n/a | n/a | -1658 (lots +29/wk) |
| quantile 75 cap, horizon = median holding time | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=0.5 | -8393 $/wk, DD +2.1%, ww +5889, stops 7.76(10.35), b5 57%, w2l 3 | n/a | n/a | -8805 (lots +113/wk) |
| remaining-range cap, forecast own 20-session mean, k=0.75 | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=1.0 | -6226 $/wk, DD +27.0%, ww +12290, stops 8.98(10.35), b5 66%, w2l 2 | n/a | n/a | -6458 (lots +63/wk) |
| remaining-range cap, forecast own 20-session mean, k=1.25 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.5 | -10795 $/wk, DD +40.3%, ww +11430, stops 7.00(10.35), b5 51%, w2l 4 | n/a | n/a | -11257 (lots +126/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.75 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.0 | -7259 $/wk, DD +39.4%, ww +17319, stops 7.76(10.35), b5 65%, w2l 2 | n/a | n/a | -7570 (lots +85/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.25 | pending | | | |
| EV-best target, bounded by the book target | -14326 $/wk, DD -25.6%, ww -15613, stops 8.45(10.35), b5 46%, w2l 3 | n/a | n/a | -14639 (lots +86/wk) |
| EV-best target, unbounded | pending | | | |
| extension m=1.0 | -110 $/wk, DD -53.4%, ww -2988, stops 11.72(10.35), b5 124%, w2l 2 | n/a | n/a | -18 (lots -25/wk) |
| extension m=1.5 | pending | | | |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts skipped | +1443 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | n/a | n/a | +1410 (lots +9/wk) |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts at half size | pending | | | |
| PLANTED-EDGE CHECK (look-ahead oracle 0.9 x realised MFE, not a result) | +85531 $/wk, DD +67.0%, ww +64263, stops 6.54(10.35), b5 259%, w2l 0 | n/a | n/a | +85219 (lots +85/wk) |
| PLANTED-EDGE CHECK (oracle 0.6 x realised MFE, not a result) | pending | | | |
| PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 | n/a | -125 (lots +1/wk) |
| PLACEBO pl23: quantile 50 cap, horizon = 75th-percentile holding time | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 | n/a | -871 (lots +3/wk) |
| PLACEBO pl37: quantile 50 cap, horizon = 75th-percentile holding time | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 | n/a | -612 (lots +2/wk) |
| PLACEBO plR1: quantile 50 cap, horizon = 75th-percentile holding time | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 | n/a | -670 (lots +4/wk) |

### The one candidate: forecast-quantile-50 cap, horizon = 75th-percentile holding time (L3M mean-only so far): all windows, W44 removed, placebos
| window | scope all | W44 removed |
|---|---|---|
| L3M | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 |
| L6M | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 |
| HOLD | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 |
| MID | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 |
| PREUW | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 |
Placebos (same cap, forecast features taken n sessions earlier at the same clock / a random earlier session), L3M then L6M when run:
| placebo | L3M | L6M |
|---|---|---|
| pl11 | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 |
| pl23 | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 |
| pl37 | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 |
| plR1 | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 |

### Per book x session exact cap cells (clean: one book in one session)
| slice | cap | L3M | May-Jul |
|---|---|---|---|
| A7 asia | quantile 50 cap, horizon = 75th-percentile holding time | -17 (live -30; $4.84 -17) DD +0.0% ww +0 stops 4.03(4.03) | n/a |

### FOR THE LIVE BUILD (what D7 computes at the signal second)
From its own 1-minute bars: last 15/30/60/120-minute range and realised vol, same-offset range over the previous 20 sessions (median), session ranges of the last 5/20 sessions, range so far, the entry position in the session range (favourable-side room), elapsed fraction of the session, ln of the book-session horizon; a small coefficient table per session (15 weights, mean, sd, intercept, four residual quantile offsets) refit every 14 days and shipped as a static file. Cap = min(60, price x exp(prediction + quantile offset) - 2); orders: the target limit is placed at the capped price. The remaining-range version needs the HAR session forecast (T-RANGE2 file) or D7 computes its own 20-session mean. No intraday feed from the box.


## Per book and session, clean, and the assembled stack
**STATUS (plain, not a PASS; B1 in progress, no "nothing passes" verdict is allowed until it is done): single-book single-session cells scored in L3M for 15 of 14 slices; slice picks so far: {}.**

Method (user order PART B, 2026-11-15): each cell = the Dial 10 hook restricted to ONE book in ONE session (every other book/session unchanged at JN05W2), exact engine, all layers ON, live caps. Dollars are BASE lots; the x1.75 live figure sits beside each headline (live); the $4.84 figure reprices every contract at the FEES.md $4.84 RT (engine raw $1.18). Compared on the same book x session slice of JN05W2 (day locks/caps still interact across books, which is why the cells are run for real and not sliced from the global run). B1a settings per slice: direction both / narrow-only / wide-only x gearing 0.5 / 1.0 at the 75th-percentile horizon, plus narrow/wide g1.0 at the median horizon; "fixed" = JN05W2 itself. Walk-forward: the pick for each slice is made on 2026-05..07 only (older than L3M); L3M (2026-08..10) is then out-of-sample. B1b (around each pick): lots cap 1.5/3, lots follow half the change, dead band 0/20%, target ratio 0.8/1.2, lever stop-only (sl: stop W, lots inverse, target in the same points) / target-only (tg) / size-only (sz: bracket fixed, lots follow the forecast), noise floor k = 3/4/5 x recent 5-minute ATR (bracket never narrower), clips 25..120 / 20..150.

### B1 table: per slice, every cell (L3M, delta vs JN05W2 same slice; May-Jul = the selection window)
| slice | setting | May-Jul (selection) | L3M (out of sample) | L6M |
|---|---|---|---|---|
| A7 asia | both/g1.0/H75 | -374 (live -654; $4.84 -370) DD -10.9% ww -261 stops 2.97(3.88) | +47 (live +83; $4.84 +40) DD +25.6% ww +1495 stops 5.55(4.03) | -163 (live -286; $4.84 -165) DD -29.2% ww +1253 stops 4.26(3.96) |
| A7 asia | narrow/g1.0/H75 | -419 (live -733; $4.84 -423) DD -0.6% ww -175 stops 4.49(3.88) | -18 (live -32; $4.84 -26) DD +17.7% ww +722 stops 5.63(4.03) | -219 (live -383; $4.84 -224) DD -19.1% ww +722 stops 5.06(3.96) |
| A7 asia | both/g0.5/H75 | -556 (live -973; $4.84 -553) DD -9.2% ww +72 stops 3.50(3.88) | -192 (live -336; $4.84 -195) DD +10.1% ww +412 stops 5.10(4.03) | -374 (live -654; $4.84 -374) DD -36.6% ww +412 stops 4.30(3.96) |
| A7 asia | narrow/g0.5/H75 | -350 (live -612; $4.84 -352) DD +0.0% ww +0 stops 4.34(3.88) | -186 (live -325; $4.84 -189) DD +10.0% ww +552 stops 5.10(4.03) | -268 (live -469; $4.84 -270) DD -15.8% ww +552 stops 4.72(3.96) |
| A7 asia | wide/g1.0/H75 | +19 (live +33; $4.84 +26) DD -10.9% ww +283 stops 2.51(3.88) | -15 (live -26; $4.84 -14) DD +2.4% ww -426 stops 3.96(4.03) | +2 (live +3; $4.84 +6) DD -13.6% ww -426 stops 3.23(3.96) |
| A7 asia | wide/g0.5/H75 | n/a | -1 (live -1; $4.84 -1) DD +1.4% ww -140 stops 4.03(4.03) | n/a |
| A7 asia | wide/g1.0/H50 | n/a | -48 (live -85; $4.84 -48) DD -3.0% ww -426 stops 3.88(4.03) | n/a |
| A7 asia | narrow/g1.0/H50 | n/a | -159 (live -279; $4.84 -171) DD -8.3% ww +877 stops 5.93(4.03) | n/a |
| H7 asia | wide/g0.5/H75 | n/a | +123 (live +215; $4.84 +123) DD +0.0% ww +0 stops 0.23(0.23) | n/a |
| H7 asia | wide/g1.0/H75 | n/a | -67 (live -118; $4.84 -67) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | wide/g1.0/H50 | n/a | -312 (live -546; $4.84 -312) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | both/g0.0/H50 | -1623 (live -2840; $4.84 -1619) DD +11.0% ww +3643 stops 0.46(0.61) | -972 (live -1701; $4.84 -967) DD -31.5% ww +0 stops 0.46(0.23) | -1298 (live -2271; $4.84 -1293) DD +11.0% ww +3643 stops 0.46(0.42) |
| H7 asia | both/g1.0/H75 | +1123 (live +1965; $4.84 +1129) DD +6.5% ww +1483 stops 0.53(0.61) | +177 (live +309; $4.84 +163) DD -33.6% ww -1228 stops 0.61(0.23) | +650 (live +1137; $4.84 +646) DD +6.5% ww +1483 stops 0.57(0.42) |
| H7 asia | narrow/g1.0/H75 | n/a | +244 (live +427; $4.84 +230) DD -33.6% ww -1228 stops 0.53(0.23) | n/a |
| H7 asia | both/g0.5/H75 | n/a | -574 (live -1004; $4.84 -580) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g0.5/H75 | n/a | -697 (live -1219; $4.84 -703) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g1.0/H50 | n/a | -355 (live -621; $4.84 -372) DD -120.5% ww -2166 stops 0.53(0.23) | n/a |
| H7 nyam | narrow/g1.0/H50 | n/a | +252 (live +441; $4.84 +252) DD +60.4% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | both/g1.0/H75 | n/a | +281 (live +491; $4.84 +280) DD +57.7% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | narrow/g1.0/H75 | -187 (live -328; $4.84 -188) DD -4.0% ww +0 stops 0.53(0.46) | +258 (live +452; $4.84 +258) DD +57.7% ww +480 stops 0.30(0.38) | +35 (live +62; $4.84 +35) DD +24.1% ww +480 stops 0.42(0.42) |
| H7 nyam | both/g0.0/H50 | -58 (live -102; $4.84 -58) DD +9.4% ww +0 stops 0.46(0.46) | +221 (live +387; $4.84 +221) DD +54.7% ww +195 stops 0.15(0.38) | +82 (live +143; $4.84 +81) DD +33.9% ww +195 stops 0.30(0.42) |
| H7 nyam | both/g0.0/H50 | -8 (live -14; $4.84 -8) DD +9.4% ww +0 stops 0.46(0.46) | +202 (live +353; $4.84 +202) DD +54.7% ww +195 stops 0.15(0.38) | +97 (live +170; $4.84 +97) DD +33.9% ww +195 stops 0.30(0.42) |
| H7 nyam | both/g0.5/H75 | +103 (live +180; $4.84 +103) DD +29.2% ww -83 stops 0.46(0.46) | +87 (live +153; $4.84 +87) DD +2.2% ww +195 stops 0.38(0.38) | +95 (live +167; $4.84 +95) DD +2.2% ww +195 stops 0.42(0.42) |
| H7 nyam | narrow/g0.5/H75 | n/a | +77 (live +134; $4.84 +77) DD +2.2% ww +195 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g0.5/H75 | n/a | +11 (live +19; $4.84 +11) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H75 | n/a | +22 (live +39; $4.84 +22) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H50 | n/a | +30 (live +53; $4.84 +30) DD +0.0% ww +0 stops 0.30(0.38) | n/a |
| K7 asia | wide/g1.0/H75 | n/a | +297 (live +520; $4.84 +298) DD +0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | wide/g0.5/H75 | n/a | -54 (live -94; $4.84 -54) DD -0.7% ww -404 stops 0.00(0.00) | n/a |
| K7 asia | narrow/g0.5/H75 | n/a | +1877 (live +3285; $4.84 +1855) DD -19.6% ww -2412 stops 0.00(0.00) | n/a |
| K7 asia | both/g0.5/H75 | n/a | +1823 (live +3191; $4.84 +1801) DD -28.8% ww -3232 stops 0.00(0.00) | n/a |
| K7 asia | wide/g1.0/H50 | n/a | -401 (live -702; $4.84 -400) DD -35.9% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | both/g1.0/H75 | n/a | +1292 (live +2261; $4.84 +1220) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H75 | n/a | +912 (live +1595; $4.84 +838) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H50 | n/a | +355 (live +621; $4.84 +268) DD -86.2% ww -5644 stops 0.00(0.00) | n/a |
| K7 london | both/g0.5/H75 | n/a | -9 (live -15; $4.84 -14) DD +8.7% ww +4326 stops 0.23(0.30) | n/a |
| K7 london | wide/g0.5/H75 | n/a | +27 (live +48; $4.84 +29) DD +0.5% ww +0 stops 0.30(0.30) | n/a |
| K7 london | wide/g1.0/H50 | n/a | +431 (live +755; $4.84 +433) DD -3.3% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g0.5/H75 | n/a | -123 (live -215; $4.84 -130) DD -4.2% ww +4733 stops 0.23(0.30) | n/a |
| K7 london | wide/g1.0/H75 | n/a | +157 (live +274; $4.84 +160) DD -4.8% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g1.0/H50 | n/a | -182 (live -319; $4.84 -204) DD -13.7% ww +3097 stops 0.23(0.30) | n/a |
| K7 london | both/g1.0/H75 | n/a | +481 (live +841; $4.84 +462) DD -25.5% ww +4257 stops 0.38(0.30) | n/a |
| K7 london | narrow/g1.0/H75 | n/a | -31 (live -55; $4.84 -55) DD -42.3% ww +4122 stops 0.38(0.30) | n/a |
| K7 nyam | both/g0.0/H50 | -645 (live -1129; $4.84 -647) DD -55.9% ww -1158 stops 0.08(0.08) | +805 (live +1408; $4.84 +793) DD +62.7% ww +1729 stops 0.00(0.00) | +80 (live +139; $4.84 +73) DD +44.5% ww +1153 stops 0.04(0.04) |
| K7 nyam | both/g0.0/H50 | -488 (live -855; $4.84 -488) DD -38.7% ww -514 stops 0.08(0.08) | +1078 (live +1886; $4.84 +1069) DD +53.9% ww +1605 stops 0.00(0.00) | +295 (live +516; $4.84 +290) DD +50.6% ww +1605 stops 0.04(0.04) |
| K7 nyam | narrow/g1.0/H50 | n/a | +769 (live +1345; $4.84 +761) DD +51.0% ww +2185 stops 0.00(0.00) | n/a |
| K7 nyam | both/g1.0/H75 | n/a | +1160 (live +2030; $4.84 +1153) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g1.0/H75 | n/a | +984 (live +1722; $4.84 +977) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g0.5/H75 | n/a | +668 (live +1170; $4.84 +667) DD +40.3% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | both/g0.5/H75 | n/a | +806 (live +1410; $4.84 +805) DD +39.5% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H75 | n/a | +176 (live +308; $4.84 +176) DD -0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H50 | n/a | +252 (live +441; $4.84 +253) DD -0.3% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g0.5/H75 | n/a | +137 (live +241; $4.84 +137) DD -0.8% ww +0 stops 0.00(0.00) | n/a |
| K7 nypm | wide/g1.0/H50 | n/a | +442 (live +773; $4.84 +442) DD +17.3% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | wide/g1.0/H75 | n/a | +70 (live +122; $4.84 +70) DD +13.1% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | both/g1.0/H75 | n/a | -184 (live -322; $4.84 -197) DD +9.8% ww +1145 stops 0.15(0.08) | n/a |
| K7 nypm | wide/g0.5/H75 | n/a | -4 (live -8; $4.84 -4) DD -1.5% ww -38 stops 0.00(0.08) | n/a |
| K7 nypm | narrow/g1.0/H50 | n/a | +48 (live +84; $4.84 +32) DD -1.9% ww +105 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g1.0/H75 | n/a | -254 (live -445; $4.84 -267) DD -3.3% ww +990 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g0.5/H75 | n/a | -266 (live -465; $4.84 -269) DD -26.7% ww +140 stops 0.08(0.08) | n/a |
| K7 nypm | both/g0.5/H75 | n/a | -270 (live -473; $4.84 -274) DD -27.3% ww +102 stops 0.00(0.08) | n/a |
| M7 london | wide/g1.0/H75 | n/a | +1614 (live +2824; $4.84 +1616) DD +4.9% ww +1190 stops 0.53(0.91) | n/a |
| M7 london | wide/g0.5/H75 | n/a | +688 (live +1204; $4.84 +689) DD +4.4% ww +1400 stops 0.84(0.91) | n/a |
| M7 london | wide/g1.0/H50 | n/a | +538 (live +942; $4.84 +540) DD -1.3% ww -80 stops 0.84(0.91) | n/a |
| M7 london | both/g0.5/H75 | n/a | +1147 (live +2008; $4.84 +1139) DD -8.1% ww +130 stops 1.07(0.91) | n/a |
| M7 london | narrow/g0.5/H75 | n/a | +417 (live +730; $4.84 +408) DD -10.9% ww -1075 stops 1.14(0.91) | n/a |
| M7 london | narrow/g1.0/H50 | n/a | +476 (live +833; $4.84 +446) DD -19.9% ww +1144 stops 1.45(0.91) | n/a |
| M7 london | narrow/g1.0/H75 | n/a | -366 (live -640; $4.84 -390) DD -20.4% ww +80 stops 1.29(0.91) | n/a |
| M7 london | both/g1.0/H75 | n/a | +1142 (live +1999; $4.84 +1121) DD -23.2% ww -729 stops 0.91(0.91) | n/a |
| M7 nyam | narrow/g1.0/H50 | n/a | +439 (live +769; $4.84 +424) DD +26.0% ww -222 stops 0.38(0.23) | n/a |
| M7 nyam | both/g0.5/H75 | n/a | +79 (live +138; $4.84 +75) DD +0.8% ww +194 stops 0.30(0.23) | n/a |
| M7 nyam | narrow/g0.5/H75 | n/a | +73 (live +127; $4.84 +69) DD +0.8% ww +194 stops 0.38(0.23) | n/a |
| M7 nyam | wide/g0.5/H75 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H75 | n/a | +16 (live +28; $4.84 +16) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H50 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | both/g1.0/H75 | n/a | +419 (live +733; $4.84 +405) DD -6.8% ww -991 stops 0.46(0.23) | n/a |
| M7 nyam | narrow/g1.0/H75 | n/a | +402 (live +704; $4.84 +388) DD -6.8% ww -991 stops 0.53(0.23) | n/a |
| M7 nyam | both/g0.0/H50 | -130 (live -227; $4.84 -131) DD -16.3% ww -1329 stops 0.61(0.61) | +102 (live +179; $4.84 +99) DD -11.5% ww +0 stops 0.23(0.23) | -14 (live -24; $4.84 -16) DD -19.5% ww -1329 stops 0.42(0.42) |
| P7 asia | both/g0.0/H50 | -5189 (live -9081; $4.84 -4987) DD +44.9% ww +11844 stops 0.00(0.00) | -703 (live -1230; $4.84 -620) DD +51.2% ww +20259 stops 0.08(0.15) | -2946 (live -5156; $4.84 -2804) DD +51.2% ww +17717 stops 0.04(0.08) |
| P7 asia | both/g0.0/H50 | -6897 (live -12069; $4.84 -6699) DD +42.2% ww +13069 stops 0.00(0.00) | -322 (live -564; $4.84 -245) DD +51.2% ww +19309 stops 0.08(0.15) | -3609 (live -6317; $4.84 -3472) DD +51.2% ww +18942 stops 0.04(0.08) |
| P7 asia | narrow/g1.0/H50 | n/a | -3918 (live -6857; $4.84 -4186) DD -0.4% ww -4286 stops 0.46(0.15) | n/a |
| P7 asia | both/g0.5/H75 | n/a | -5946 (live -10406; $4.84 -6044) DD -1.0% ww +6944 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g0.5/H75 | n/a | -5762 (live -10084; $4.84 -5860) DD -1.0% ww +9022 stops 0.15(0.15) | n/a |
| P7 asia | wide/g0.5/H75 | n/a | -184 (live -322; $4.84 -183) DD -4.9% ww -2079 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g1.0/H75 | n/a | -2696 (live -4718; $4.84 -2882) DD -7.8% ww -10346 stops 0.53(0.15) | n/a |
| P7 asia | wide/g1.0/H50 | n/a | -816 (live -1428; $4.84 -812) DD -22.6% ww -9033 stops 0.15(0.15) | n/a |
| P7 asia | wide/g1.0/H75 | n/a | -491 (live -858; $4.84 -490) DD -25.2% ww -10331 stops 0.15(0.15) | n/a |
| P7 asia | both/g1.0/H75 | n/a | -3315 (live -5802; $4.84 -3501) DD -36.1% ww -13164 stops 0.53(0.15) | n/a |
| P7 london | both/g0.5/H75 | n/a | +894 (live +1565; $4.84 +886) DD +29.6% ww -1633 stops 0.08(0.08) | n/a |
| P7 london | narrow/g0.5/H75 | n/a | +386 (live +675; $4.84 +375) DD +28.5% ww -1328 stops 0.08(0.08) | n/a |
| P7 london | narrow/g1.0/H50 | n/a | +927 (live +1622; $4.84 +895) DD +19.7% ww -3009 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H75 | n/a | -142 (live -249; $4.84 -138) DD +2.7% ww -458 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H50 | n/a | +265 (live +464; $4.84 +266) DD +1.1% ww +0 stops 0.08(0.08) | n/a |
| P7 london | wide/g0.5/H75 | n/a | +385 (live +674; $4.84 +387) DD -1.9% ww -238 stops 0.08(0.08) | n/a |
| P7 london | both/g1.0/H75 | n/a | +1179 (live +2064; $4.84 +1145) DD -9.8% ww -5408 stops 0.15(0.08) | n/a |
| P7 london | narrow/g1.0/H75 | n/a | +1322 (live +2313; $4.84 +1282) DD -14.4% ww -5203 stops 0.15(0.08) | n/a |
| P7 nyam | both/g0.0/H50 | -1333 (live -2333; $4.84 -1305) DD +88.2% ww +6983 stops 0.00(0.08) | +198 (live +346; $4.84 +220) DD +55.7% ww +1594 stops 0.15(0.38) | -568 (live -994; $4.84 -542) DD +59.1% ww +4666 stops 0.08(0.23) |
| P7 nyam | both/g1.0/H75 | n/a | +697 (live +1220; $4.84 +685) DD +51.3% ww +354 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g1.0/H75 | n/a | +543 (live +951; $4.84 +529) DD +45.9% ww +324 stops 0.30(0.38) | n/a |
| P7 nyam | both/g0.5/H75 | n/a | +105 (live +184; $4.84 +99) DD +36.7% ww +238 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g0.5/H75 | n/a | -13 (live -23; $4.84 -20) DD +36.4% ww +262 stops 0.30(0.38) | n/a |
| P7 nyam | wide/g0.5/H75 | n/a | +118 (live +207; $4.84 +119) DD +0.3% ww -25 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H75 | n/a | +16 (live +27; $4.84 +17) DD -7.5% ww -105 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H50 | n/a | -544 (live -952; $4.84 -543) DD -47.7% ww -3348 stops 0.38(0.38) | n/a |
| U7 asia | narrow/g1.0/H50 | n/a | +1222 (live +2139; $4.84 +1201) DD +15.6% ww -265 stops 1.90(1.83) | n/a |
| U7 asia | both/g1.0/H75 | n/a | +71 (live +124; $4.84 +56) DD +8.3% ww -1836 stops 1.98(1.83) | n/a |
| U7 asia | narrow/g1.0/H75 | n/a | +502 (live +879; $4.84 +487) DD +8.3% ww +983 stops 1.98(1.83) | n/a |
| U7 asia | both/g0.5/H75 | n/a | -800 (live -1399; $4.84 -808) DD +6.6% ww -2883 stops 2.05(1.83) | n/a |
| U7 asia | narrow/g0.5/H75 | n/a | -162 (live -284; $4.84 -170) DD +6.6% ww +57 stops 2.05(1.83) | n/a |
| U7 asia | wide/g0.5/H75 | n/a | -637 (live -1115; $4.84 -637) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H75 | n/a | -431 (live -755; $4.84 -431) DD +0.0% ww -1836 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H50 | n/a | -648 (live -1134; $4.84 -648) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 london | narrow/g0.5/H75 | n/a | +393 (live +687; $4.84 +392) DD +17.2% ww +1796 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H75 | n/a | +246 (live +431; $4.84 +243) DD +3.1% ww -1185 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H50 | n/a | -41 (live -72; $4.84 -48) DD -9.9% ww -1991 stops 1.52(1.45) | n/a |
| U7 london | both/g0.5/H75 | n/a | -891 (live -1560; $4.84 -890) DD -25.4% ww -3538 stops 1.52(1.45) | n/a |
| U7 london | wide/g1.0/H50 | n/a | -839 (live -1468; $4.84 -837) DD -33.9% ww -4122 stops 1.37(1.45) | n/a |
| U7 london | wide/g0.5/H75 | n/a | -1284 (live -2247; $4.84 -1282) DD -44.3% ww -6280 stops 1.52(1.45) | n/a |
| U7 london | both/g1.0/H75 | n/a | -1728 (live -3025; $4.84 -1729) DD -105.5% ww -7540 stops 1.60(1.45) | n/a |
| U7 london | wide/g1.0/H75 | n/a | -1975 (live -3455; $4.84 -1972) DD -109.8% ww -6355 stops 1.60(1.45) | n/a |

### Summary per slice: pick made on May-Jul, result on L3M
| slice | pick | L3M result of the pick | verdict |
|---|---|---|---|
| A7 asia | pending | | |
| H7 asia | pending | | |
| H7 nyam | pending | | |
| K7 asia | pending | | |
| K7 london | pending | | |
| K7 nyam | pending | | |
| K7 nypm | pending | | |
| M7 london | pending | | |
| M7 nyam | pending | | |
| P7 asia | pending | | |
| P7 london | pending | | |
| P7 nyam | pending | | |
| U7 asia | pending | | |
| U7 london | pending | | |

### B2: why the global version adds full stops (narrow-only/both g1.0 H75 cell, L3M, trade tables)
Reference JN05W2 L3M (no O7): 1855 trades, stop rate 0.071, 132 stops (13 weeks).

**M1_75_g10_c1_d10_c20_tb_B**: 2038 trades (+183 vs JN05W2), stops 173 (+41), stop rate 0.085 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 437 | 0.103 | 3.05 | 94 |
| (40, 50] | 721 | 0.074 | 2.36 | 271 |
| (50, 55] | 232 | 0.099 | 1.97 | 169 |
| (55, 60] | 435 | 0.076 | 1.87 | 76 |
| (60, 70] | 75 | 0.120 | 2.01 | -385 |
| (70, 80] | 62 | 0.048 | 1.68 | -284 |
| (80, 101] | 76 | 0.092 | 1.13 | -591 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1543 | 0.069 | 2.21 | 54 |
| (3.0, 4.0] | 294 | 0.116 | 2.29 | 239 |
| (4.0, 5.0] | 74 | 0.108 | 2.31 | 364 |
| (5.0, 6.0] | 6 | 0.167 | 2.50 | 172 |
| (6.0, 8.0] | 4 | 0.000 | 1.00 | -119 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1068 | 0.096 | 1.00 | 4 |
| (1, 2] | 385 | 0.078 | 2.00 | 115 |
| (2, 3] | 215 | 0.093 | 3.00 | 23 |
| (3, 5] | 195 | 0.062 | 4.46 | 256 |
| (5, 8] | 138 | 0.065 | 6.70 | 690 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

**M1_75_g10_c1_d10_c20_tb_N**: 2072 trades (+217 vs JN05W2), stops 178 (+46), stop rate 0.086 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 449 | 0.105 | 3.02 | 97 |
| (40, 50] | 725 | 0.073 | 2.35 | 272 |
| (50, 55] | 236 | 0.102 | 1.97 | 150 |
| (55, 60] | 662 | 0.082 | 1.82 | -29 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1644 | 0.072 | 2.18 | 50 |
| (3.0, 4.0] | 264 | 0.121 | 2.38 | 348 |
| (4.0, 5.0] | 44 | 0.091 | 3.11 | 1063 |
| (5.0, 6.0] | 3 | 0.000 | 3.33 | 68 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1073 | 0.095 | 1.00 | 8 |
| (1, 2] | 413 | 0.085 | 2.00 | 117 |
| (2, 3] | 197 | 0.081 | 3.00 | 213 |
| (3, 5] | 217 | 0.074 | 4.43 | 196 |
| (5, 8] | 135 | 0.067 | 6.74 | 714 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

Reading of the W/ATR5 table: ATR5 = mean range of the last 14 five-minute buckets in points; a bracket 3x ATR5 or less is within ordinary 5-minute noise. The noise-floor cells (floor 3/4/5 x ATR5, narrowing only) are listed in B3.


### B3: levers (stop-only / target-only / both / size-only) and noise floor, per slice
| slice | cell | L3M | May-Jul |
|---|---|---|---|

### B4: assembled stack (each slice at its own walk-forward pick, run together)
(not run yet: starts when every slice has a pick)


## Target capped at the forecast
**VERDICT (plain, not a PASS; FIRST PASS; 15 of 26 global exact cap cells scored in L3M, per book x session exact cells still running): planted-edge check PASSED through the exact engine (look-ahead oracle target 0.9 x realised MFE: +85531 $/wk, DD +67.0%, ww +64263; this is a mechanism check, NOT a result); the reachable move is only weakly forecastable (R2 on ln MFE 0.03-0.14, quantile calibration good); in the exact L3M cells the cap at the forecast 50th-percentile move (horizon = 75th-percentile holding time) gives +1486 $/wk, DD -0.5%, ww -240 and the 75th-percentile cap +177 $/wk, DD +0.0%, ww +0, the remaining-range caps cut drawdown (own k1.0 -6226 $/wk, DD +27.0%, ww +12290; HAR k1.0 -7259 $/wk, DD +39.4%, ww +17319) but cost thousands per week. Best exact L3M cap cell inside the mean gate by DD: PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time (DD +7.9%, -120 $/wk). L6M/HOLD/older still to run before any verdict.**

Planted-edge check (H1) for the capping mechanism: cells `tcoracle0.9` / `0.6` set the target to 0.9 / 0.6 x the REALISED maximum favourable move (look-ahead, only to prove the mechanism can show an edge through the exact engine); they must come out strongly positive. Status below in the exact table. Until they do, an exact cap verdict is not stated.

Definition. Reachable move = maximum favourable excursion from the signal-second bar close over the book-session holding horizon H (H50/H75 = median / 75th percentile holding time of that book+session, causal), points. Model: walk-forward ridge (14-day blocks, expanding, min 90 days, per session) on ln((MFE+2)/price) from the Dial 10 own-bar inputs (last 15/30/60/120 min range and vol, same-clock normal, own session level, range used so far, elapsed fraction) plus the side-aware room in the session range so far; quantiles q = fitted + empirical training-residual quantile (50/60/75/90). Cap: target = min(book target 60 pts [58 after fills], q-quantile), stop, lots and every other level unchanged. Remaining-range cap: target = min(book target, k x (session range forecast - range printed so far)), forecast = own (price x exp(sf20), mean of the last 20 sessions) or T-RANGE2 HAR (fc_r2_har, available-epoch checked). Small caps (< 30 pts = 0.5 x stop): take / skip / half. EV target: argmax over T in [20, book target or 300] of T x P(MFE>=T) - stop x (1-P) with the lognormal forecast (ignores the stop-first ordering, so optimistic). Extension: if the forecast median MFE is >= m x book target, target = min(q50, 2 x book target). Lots/base basis: dollars are BASE lots (live x1.75 = multiply by 1.75); fee columns $4.84 beside raw $1.18 where shown.

### Item 1: calibration of the forecast quantiles (share of trades whose realized MFE exceeded the forecast quantile; a q-quantile should be exceeded 1-q of the time = 0.50 / 0.40 / 0.25 / 0.10) and R2 of ln MFE, per session
| H | session | window | n | >q50 | >q60 | >q75 | >q90 | R2 ln MFE | median q75 (pts) | share q75 < 60 |
|---|---|---|---|---|---|---|---|---|---|---|
| 50 | asia | older (<2026-05) | 5119 | 0.51 | 0.41 | 0.26 | 0.12 | 0.121 | 80 | 0.222 |
| 50 | asia | L6M | 2006 | 0.49 | 0.38 | 0.23 | 0.08 | 0.058 | 111 | 0.047 |
| 50 | asia | L3M | 875 | 0.46 | 0.34 | 0.20 | 0.07 | -0.014 | 90 | 0.098 |
| 50 | london | older (<2026-05) | 4892 | 0.51 | 0.41 | 0.26 | 0.11 | 0.142 | 62 | 0.438 |
| 50 | london | L6M | 1406 | 0.48 | 0.37 | 0.23 | 0.08 | 0.028 | 76 | 0.166 |
| 50 | london | L3M | 673 | 0.48 | 0.37 | 0.24 | 0.07 | -0.008 | 68 | 0.247 |
| 50 | nyam | older (<2026-05) | 4142 | 0.47 | 0.38 | 0.24 | 0.11 | 0.077 | 63 | 0.397 |
| 50 | nyam | L6M | 600 | 0.51 | 0.40 | 0.24 | 0.09 | 0.097 | 83 | 0.157 |
| 50 | nyam | L3M | 271 | 0.51 | 0.38 | 0.20 | 0.06 | 0.077 | 68 | 0.258 |
| 50 | nypm | older (<2026-05) | 817 | 0.48 | 0.40 | 0.26 | 0.13 | 0.073 | 62 | 0.419 |
| 50 | nypm | L6M | 150 | 0.59 | 0.50 | 0.33 | 0.13 | 0.221 | 71 | 0.307 |
| 50 | nypm | L3M | 56 | 0.50 | 0.36 | 0.21 | 0.09 | 0.104 | 54 | 0.589 |
| 50 | all | older (<2026-05) | 14970 | 0.50 | 0.40 | 0.26 | 0.12 | 0.123 | 68 | 0.352 |
| 50 | all | L6M | 4162 | 0.49 | 0.38 | 0.23 | 0.08 | 0.080 | 91 | 0.113 |
| 50 | all | L3M | 1875 | 0.47 | 0.36 | 0.21 | 0.07 | 0.014 | 76 | 0.189 |
| 75 | asia | older (<2026-05) | 5119 | 0.52 | 0.41 | 0.26 | 0.12 | 0.134 | 122 | 0.032 |
| 75 | asia | L6M | 2006 | 0.50 | 0.40 | 0.24 | 0.08 | 0.027 | 178 | 0.000 |
| 75 | asia | L3M | 875 | 0.45 | 0.35 | 0.20 | 0.05 | -0.016 | 156 | 0.000 |
| 75 | london | older (<2026-05) | 4891 | 0.51 | 0.42 | 0.27 | 0.11 | 0.157 | 101 | 0.100 |
| 75 | london | L6M | 1406 | 0.49 | 0.37 | 0.21 | 0.08 | 0.069 | 118 | 0.001 |
| 75 | london | L3M | 673 | 0.49 | 0.38 | 0.21 | 0.09 | 0.025 | 108 | 0.000 |
| 75 | nyam | older (<2026-05) | 4142 | 0.48 | 0.38 | 0.23 | 0.10 | 0.065 | 91 | 0.081 |
| 75 | nyam | L6M | 600 | 0.50 | 0.40 | 0.24 | 0.10 | 0.098 | 125 | 0.015 |
| 75 | nyam | L3M | 271 | 0.44 | 0.34 | 0.19 | 0.05 | 0.051 | 103 | 0.015 |
| 75 | nypm | older (<2026-05) | 812 | 0.49 | 0.37 | 0.26 | 0.11 | 0.043 | 87 | 0.095 |
| 75 | nypm | L6M | 150 | 0.53 | 0.46 | 0.34 | 0.17 | 0.179 | 117 | 0.013 |
| 75 | nypm | L3M | 56 | 0.41 | 0.30 | 0.21 | 0.07 | -0.076 | 93 | 0.036 |
| 75 | all | older (<2026-05) | 14964 | 0.51 | 0.40 | 0.25 | 0.11 | 0.131 | 102 | 0.071 |
| 75 | all | L6M | 4162 | 0.50 | 0.39 | 0.23 | 0.09 | 0.079 | 149 | 0.003 |
| 75 | all | L3M | 1875 | 0.46 | 0.36 | 0.20 | 0.06 | 0.032 | 128 | 0.003 |

### Items 3 and 4 (and 2): offline replay of the caps on the JN05W2 trade paths, all 43 months (estimate: 1-min paths, cap counted only before the exit bar, so cut/stop ordering is conservative; the exact cells below decide). d mean $/wk and DD cut % vs JN05W2 on the same trades, scope all, then per session for the cap with the most trades capped
| cap | small-cap rule | scope | window | d mean $/wk (live x1.75) | DD cut % | d worst week | d stops/wk | share capped | share where cap hit |
|---|---|---|---|---|---|---|---|---|---|
| q50_H50 | take | all | L3M | +409 (+715) | -3.9 | -1411 | +0.00 | 0.82 | 0.45 |
| q50_H50 | take | all | L6M | -96 (-169) | -3.9 | -1411 | +0.00 | 0.62 | 0.33 |
| q50_H50 | take | all | OLDER | -1795 (-3141) | +12.0 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | skip | all | L3M | -1581 (-2767) | -5.0 | -1996 | +0.00 | 0.82 | 0.45 |
| q50_H50 | skip | all | L6M | -1445 (-2528) | -5.0 | -1996 | +0.00 | 0.62 | 0.33 |
| q50_H50 | skip | all | OLDER | -2271 (-3975) | +17.4 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | half | all | L3M | -586 (-1026) | -4.4 | -1704 | +0.00 | 0.82 | 0.45 |
| q50_H50 | half | all | L6M | -771 (-1348) | -4.4 | -1704 | +0.00 | 0.62 | 0.33 |
| q50_H50 | half | all | OLDER | -2033 (-3558) | +16.5 | +13127 | +0.00 | 0.80 | 0.45 |
| q60_H50 | take | all | L3M | -1525 (-2668) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | take | all | L6M | -839 (-1469) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | take | all | OLDER | -1296 (-2267) | +12.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | skip | all | L3M | -3272 (-5726) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | skip | all | L6M | -1811 (-3170) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | skip | all | OLDER | -1648 (-2885) | +8.8 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | half | all | L3M | -2398 (-4197) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | half | all | L6M | -1325 (-2319) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | half | all | OLDER | -1472 (-2576) | +10.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q75_H50 | take | all | L3M | +414 (+725) | -0.4 | -214 | +0.00 | 0.21 | 0.11 |
| q75_H50 | take | all | L6M | -44 (-77) | -0.4 | -214 | +0.00 | 0.13 | 0.06 |
| q75_H50 | take | all | OLDER | -719 (-1258) | -1.1 | +13801 | +0.00 | 0.37 | 0.18 |
| q90_H50 | take | all | L3M | +191 (+334) | +0.0 | +0 | +0.00 | 0.02 | 0.01 |
| q90_H50 | take | all | L6M | +142 (+249) | +0.0 | +0 | +0.00 | 0.01 | 0.01 |
| q90_H50 | take | all | OLDER | -169 (-296) | -1.8 | +1686 | +0.00 | 0.08 | 0.03 |
| q50_H75 | take | all | L3M | +128 (+225) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | take | all | L6M | +624 (+1092) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | take | all | OLDER | -931 (-1628) | -13.1 | +11346 | +0.00 | 0.51 | 0.26 |
| q50_H75 | skip | all | L3M | +178 (+312) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | skip | all | L6M | +685 (+1198) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | skip | all | OLDER | -1302 (-2279) | -4.6 | +14384 | +0.00 | 0.51 | 0.26 |
| q50_H75 | half | all | L3M | +153 (+268) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | half | all | L6M | +654 (+1145) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | half | all | OLDER | -1116 (-1954) | -8.8 | +12865 | +0.00 | 0.51 | 0.26 |
| q60_H75 | take | all | L3M | +830 (+1452) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | take | all | L6M | +379 (+664) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | take | all | OLDER | -478 (-836) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | skip | all | L3M | +958 (+1677) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | skip | all | L6M | +421 (+737) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | skip | all | OLDER | -402 (-703) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | half | all | L3M | +894 (+1564) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | half | all | L6M | +400 (+700) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | half | all | OLDER | -440 (-769) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q75_H75 | take | all | L3M | +236 (+413) | +0.0 | +0 | +0.00 | 0.01 | 0.00 |
| q75_H75 | take | all | L6M | +105 (+185) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q75_H75 | take | all | OLDER | -255 (-446) | -1.9 | +1485 | +0.00 | 0.08 | 0.04 |
| q90_H75 | take | all | L3M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | L6M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | OLDER | +10 (+18) | -0.4 | +0 | +0.00 | 0.01 | 0.00 |
| rem_own_k0.5 | take | all | L3M | -6674 (-11680) | +8.8 | -1861 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | take | all | L6M | -13204 (-23108) | +8.7 | -1861 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | take | all | OLDER | -7381 (-12916) | -40.2 | +20529 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | skip | all | L3M | -5271 (-9225) | +21.7 | +2982 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | skip | all | L6M | -10625 (-18594) | +21.7 | +2982 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | skip | all | OLDER | -6272 (-10977) | +17.3 | +21712 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | half | all | L3M | -5973 (-10452) | +16.3 | +560 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | half | all | L6M | -11915 (-20851) | +16.3 | +560 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | half | all | OLDER | -6827 (-11946) | +0.6 | +23150 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.75 | take | all | L3M | -7140 (-12494) | +9.6 | +3294 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | take | all | L6M | -10636 (-18614) | +9.6 | +3294 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | take | all | OLDER | -5846 (-10230) | -24.0 | +12208 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | skip | all | L3M | -3661 (-6406) | +10.3 | +4045 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | skip | all | L6M | -6650 (-11638) | +10.3 | +4045 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | skip | all | OLDER | -3856 (-6749) | +16.1 | +19073 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | half | all | L3M | -5400 (-9450) | +13.0 | +3670 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | half | all | L6M | -8643 (-15126) | +13.0 | +3670 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | half | all | OLDER | -4851 (-8489) | +13.0 | +20157 | +0.00 | 0.73 | 0.53 |
| rem_own_k1.0 | take | all | L3M | -5516 (-9653) | +18.3 | +9104 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | take | all | L6M | -8765 (-15339) | +18.3 | +9104 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | take | all | OLDER | -5714 (-9999) | -58.2 | +11926 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | skip | all | L3M | -3265 (-5714) | +15.0 | +8858 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | skip | all | L6M | -5683 (-9944) | +15.0 | +8858 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | skip | all | OLDER | -3872 (-6775) | -61.0 | +20250 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | half | all | L3M | -4391 (-7683) | +18.5 | +8981 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | half | all | L6M | -7224 (-12642) | +18.5 | +8981 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | half | all | OLDER | -4793 (-8387) | -58.0 | +21393 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.25 | take | all | L3M | -3112 (-5446) | +24.4 | +13750 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | take | all | L6M | -8275 (-14481) | +24.4 | +13750 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | take | all | OLDER | -5400 (-9450) | -15.5 | +4336 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | skip | all | L3M | -456 (-797) | +22.4 | +13720 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | skip | all | L6M | -4232 (-7405) | +22.4 | +13720 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | skip | all | OLDER | -3310 (-5792) | -36.4 | +22803 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | half | all | L3M | -1784 (-3121) | +25.2 | +15286 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | half | all | L6M | -6253 (-10943) | +25.2 | +15286 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | half | all | OLDER | -4355 (-7621) | -18.3 | +15544 | +0.00 | 0.54 | 0.41 |

Per session, q60 H75 take-anyway and remaining-range k=1.25 (own):
| cap | session | window | d mean $/wk | DD cut % | d worst week | share capped |
|---|---|---|---|---|---|---|
| q60_H75 | asia | L3M | +221 | +0.0 | +0 | 0.02 |
| q60_H75 | asia | L6M | +110 | +0.0 | +0 | 0.01 |
| q60_H75 | asia | OLDER | -124 | -0.0 | +0 | 0.23 |
| q60_H75 | london | L3M | +745 | +3.8 | +0 | 0.16 |
| q60_H75 | london | L6M | +330 | +3.8 | +0 | 0.12 |
| q60_H75 | london | OLDER | -294 | -2.1 | +0 | 0.35 |
| q60_H75 | nyam | L3M | +61 | -7.2 | +0 | 0.15 |
| q60_H75 | nyam | L6M | -14 | +0.0 | +0 | 0.10 |
| q60_H75 | nyam | OLDER | -37 | -6.0 | +1403 | 0.37 |
| q60_H75 | nypm | L3M | -197 | -0.0 | +0 | 0.41 |
| q60_H75 | nypm | L6M | -47 | +0.0 | +0 | 0.20 |
| q60_H75 | nypm | OLDER | -22 | -5.4 | +0 | 0.33 |
| rem_own_k1.25 | asia | L3M | -4547 | +35.2 | +434 | 0.37 |
| rem_own_k1.25 | asia | L6M | -6717 | +27.1 | +434 | 0.38 |
| rem_own_k1.25 | asia | OLDER | -4532 | -27.4 | +10774 | 0.62 |
| rem_own_k1.25 | london | L3M | +2278 | +46.3 | +12347 | 0.24 |
| rem_own_k1.25 | london | L6M | +1196 | +46.3 | +12347 | 0.30 |
| rem_own_k1.25 | london | OLDER | -510 | +12.9 | +3024 | 0.51 |
| rem_own_k1.25 | nyam | L3M | -650 | +20.0 | +0 | 0.24 |
| rem_own_k1.25 | nyam | L6M | -2127 | -8.9 | +1531 | 0.39 |
| rem_own_k1.25 | nyam | OLDER | -53 | +10.3 | +7327 | 0.47 |
| rem_own_k1.25 | nypm | L3M | -192 | +21.8 | +1203 | 0.45 |
| rem_own_k1.25 | nypm | L6M | -627 | +21.8 | +1203 | 0.50 |
| rem_own_k1.25 | nypm | OLDER | -304 | -2.4 | -831 | 0.50 |

### Item 4 per book x session (all 43 months): trades whose 60-pt target lies beyond the forecast quantile, their fixed-target result, the capped replay, and how far trades run past the cap
| book | session | cap | trades | share beyond | fixed-target hit rate | fixed avg $/trade | capped avg $/trade | avg points run past cap |
|---|---|---|---|---|---|---|---|---|
| A7 | asia | q50_H75 | 1156 | 0.25 | 0.50 | 60 | 87 | 10.4 |
| A7 | asia | q60_H75 | 1156 | 0.13 | 0.47 | 4 | 26 | 8.8 |
| A7 | asia | q75_H75 | 1156 | 0.03 | 0.48 | 19 | 6 | 11.1 |
| A7 | asia | rem_own_k0.75 | 1156 | 0.74 | 0.52 | 126 | 22 | 32.9 |
| H7 | asia | q50_H75 | 700 | 0.33 | 0.49 | 164 | 181 | 11.3 |
| H7 | asia | q60_H75 | 700 | 0.18 | 0.56 | 447 | 414 | 10.7 |
| H7 | asia | q75_H75 | 700 | 0.02 | 0.50 | -318 | -267 | 16.1 |
| H7 | asia | rem_own_k0.75 | 700 | 0.71 | 0.48 | 208 | 55 | 27.8 |
| H7 | nyam | q50_H75 | 348 | 0.49 | 0.46 | 84 | 25 | 8.9 |
| H7 | nyam | q60_H75 | 348 | 0.25 | 0.47 | 96 | 46 | 7.4 |
| H7 | nyam | q75_H75 | 348 | 0.06 | 0.33 | -113 | -12 | 4.7 |
| H7 | nyam | rem_own_k0.75 | 348 | 0.66 | 0.47 | 62 | -35 | 23.3 |
| K7 | asia | q50_H75 | 2596 | 0.32 | 0.44 | 102 | 74 | 9.7 |
| K7 | asia | q60_H75 | 2596 | 0.19 | 0.44 | 111 | 90 | 7.6 |
| K7 | asia | q75_H75 | 2596 | 0.04 | 0.40 | 26 | 1 | 6.1 |
| K7 | asia | rem_own_k0.75 | 2596 | 0.68 | 0.44 | 88 | 0 | 27.2 |
| K7 | london | q50_H75 | 1781 | 0.57 | 0.43 | 62 | 37 | 10.9 |
| K7 | london | q60_H75 | 1781 | 0.33 | 0.44 | 60 | 35 | 9.4 |
| K7 | london | q75_H75 | 1781 | 0.12 | 0.48 | 138 | 101 | 6.5 |
| K7 | london | rem_own_k0.75 | 1781 | 0.69 | 0.43 | 45 | -12 | 27.4 |
| K7 | nyam | q50_H75 | 1565 | 0.57 | 0.42 | 21 | 18 | 10.0 |
| K7 | nyam | q60_H75 | 1565 | 0.32 | 0.40 | -4 | -17 | 9.0 |
| K7 | nyam | q75_H75 | 1565 | 0.07 | 0.41 | 40 | 36 | 16.3 |
| K7 | nyam | rem_own_k0.75 | 1565 | 0.70 | 0.39 | -21 | -38 | 26.0 |
| K7 | nypm | q50_H75 | 1136 | 0.50 | 0.36 | 65 | 54 | 8.1 |
| K7 | nypm | q60_H75 | 1136 | 0.31 | 0.34 | 62 | 48 | 5.6 |
| K7 | nypm | q75_H75 | 1136 | 0.09 | 0.29 | 155 | 179 | 3.5 |
| K7 | nypm | rem_own_k0.75 | 1136 | 0.71 | 0.37 | 72 | -30 | 23.7 |
| M7 | london | q50_H75 | 2489 | 0.42 | 0.43 | 45 | 40 | 10.0 |
| M7 | london | q60_H75 | 2489 | 0.24 | 0.43 | 32 | 26 | 8.2 |
| M7 | london | q75_H75 | 2489 | 0.06 | 0.38 | -74 | -97 | 7.1 |
| M7 | london | rem_own_k0.75 | 2489 | 0.59 | 0.39 | -40 | -29 | 22.9 |
| M7 | nyam | q50_H75 | 1496 | 0.52 | 0.43 | 49 | 22 | 8.6 |
| M7 | nyam | q60_H75 | 1496 | 0.27 | 0.44 | 76 | 57 | 7.2 |
| M7 | nyam | q75_H75 | 1496 | 0.06 | 0.44 | 127 | 131 | 4.9 |
| M7 | nyam | rem_own_k0.75 | 1496 | 0.69 | 0.42 | 30 | -36 | 27.3 |
| O7 | nyam | q50_H75 | 452 | 0.58 | 0.32 | 205 | 91 | 20.5 |
| O7 | nyam | q60_H75 | 452 | 0.37 | 0.31 | 156 | 118 | 16.9 |
| O7 | nyam | q75_H75 | 452 | 0.08 | 0.20 | -192 | -145 | 9.5 |
| O7 | nyam | rem_own_k0.75 | 452 | 0.31 | 0.30 | 120 | 82 | 20.6 |
| P7 | asia | q50_H75 | 2161 | 0.29 | 0.46 | 391 | 341 | 10.2 |
| P7 | asia | q60_H75 | 2161 | 0.16 | 0.48 | 487 | 484 | 9.3 |
| P7 | asia | q75_H75 | 2161 | 0.02 | 0.55 | 1227 | 969 | 5.7 |
| P7 | asia | rem_own_k0.75 | 2161 | 0.70 | 0.44 | 447 | 130 | 26.6 |
| P7 | london | q50_H75 | 1537 | 0.62 | 0.38 | 74 | 27 | 10.0 |
| P7 | london | q60_H75 | 1537 | 0.41 | 0.38 | 67 | 36 | 7.8 |
| P7 | london | q75_H75 | 1537 | 0.15 | 0.41 | 124 | 59 | 5.3 |
| P7 | london | rem_own_k0.75 | 1537 | 0.72 | 0.37 | -19 | -13 | 23.8 |
| P7 | nyam | q50_H75 | 1050 | 0.72 | 0.38 | 38 | 150 | 13.2 |
| P7 | nyam | q60_H75 | 1050 | 0.48 | 0.37 | -7 | 28 | 10.9 |
| P7 | nyam | q75_H75 | 1050 | 0.15 | 0.33 | -88 | -96 | 13.3 |
| P7 | nyam | rem_own_k0.75 | 1050 | 0.71 | 0.37 | -43 | 67 | 33.2 |
| U7 | asia | q50_H75 | 686 | 0.28 | 0.54 | 412 | 320 | 10.4 |
| U7 | asia | q60_H75 | 686 | 0.15 | 0.50 | 322 | 270 | 8.0 |
| U7 | asia | q75_H75 | 686 | 0.03 | 0.47 | -260 | -383 | 6.8 |
| U7 | asia | rem_own_k0.75 | 686 | 0.74 | 0.53 | 375 | 4 | 30.5 |
| U7 | london | q50_H75 | 645 | 0.27 | 0.46 | -102 | -183 | 8.7 |
| U7 | london | q60_H75 | 645 | 0.13 | 0.46 | -173 | -182 | 7.8 |
| U7 | london | q75_H75 | 645 | 0.03 | 0.50 | -396 | -466 | 5.4 |
| U7 | london | rem_own_k0.75 | 645 | 0.68 | 0.51 | 166 | 14 | 24.5 |

### Exact cap cells (global: all books at once; L3M, L6M when promoted; delta vs JN05W2)
| cell | L3M | L6M | HOLD | d mean/wk at $4.84 L3M |
|---|---|---|---|---|
| quantile 50 cap, horizon = 75th-percentile holding time | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | +1452 (lots +9/wk) |
| quantile 60 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 75 cap, horizon = 75th-percentile holding time | +177 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 101%, w2l 0 | n/a | n/a | +176 (lots +0/wk) |
| quantile 90 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 60 cap, horizon = median holding time | -1554 $/wk, DD +2.5%, ww +1445, stops 10.42(10.35), b5 89%, w2l 1 | n/a | n/a | -1658 (lots +29/wk) |
| quantile 75 cap, horizon = median holding time | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=0.5 | -8393 $/wk, DD +2.1%, ww +5889, stops 7.76(10.35), b5 57%, w2l 3 | n/a | n/a | -8805 (lots +113/wk) |
| remaining-range cap, forecast own 20-session mean, k=0.75 | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=1.0 | -6226 $/wk, DD +27.0%, ww +12290, stops 8.98(10.35), b5 66%, w2l 2 | n/a | n/a | -6458 (lots +63/wk) |
| remaining-range cap, forecast own 20-session mean, k=1.25 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.5 | -10795 $/wk, DD +40.3%, ww +11430, stops 7.00(10.35), b5 51%, w2l 4 | n/a | n/a | -11257 (lots +126/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.75 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.0 | -7259 $/wk, DD +39.4%, ww +17319, stops 7.76(10.35), b5 65%, w2l 2 | n/a | n/a | -7570 (lots +85/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.25 | pending | | | |
| EV-best target, bounded by the book target | -14326 $/wk, DD -25.6%, ww -15613, stops 8.45(10.35), b5 46%, w2l 3 | n/a | n/a | -14639 (lots +86/wk) |
| EV-best target, unbounded | pending | | | |
| extension m=1.0 | -110 $/wk, DD -53.4%, ww -2988, stops 11.72(10.35), b5 124%, w2l 2 | n/a | n/a | -18 (lots -25/wk) |
| extension m=1.5 | pending | | | |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts skipped | +1443 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | n/a | n/a | +1410 (lots +9/wk) |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts at half size | pending | | | |
| PLANTED-EDGE CHECK (look-ahead oracle 0.9 x realised MFE, not a result) | +85531 $/wk, DD +67.0%, ww +64263, stops 6.54(10.35), b5 259%, w2l 0 | n/a | n/a | +85219 (lots +85/wk) |
| PLANTED-EDGE CHECK (oracle 0.6 x realised MFE, not a result) | pending | | | |
| PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 | n/a | -125 (lots +1/wk) |
| PLACEBO pl23: quantile 50 cap, horizon = 75th-percentile holding time | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 | n/a | -871 (lots +3/wk) |
| PLACEBO pl37: quantile 50 cap, horizon = 75th-percentile holding time | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 | n/a | -612 (lots +2/wk) |
| PLACEBO plR1: quantile 50 cap, horizon = 75th-percentile holding time | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 | n/a | -670 (lots +4/wk) |

### The one candidate: forecast-quantile-50 cap, horizon = 75th-percentile holding time (L3M mean-only so far): all windows, W44 removed, placebos
| window | scope all | W44 removed |
|---|---|---|
| L3M | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 |
| L6M | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 |
| HOLD | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 |
| MID | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 |
| PREUW | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 |
Placebos (same cap, forecast features taken n sessions earlier at the same clock / a random earlier session), L3M then L6M when run:
| placebo | L3M | L6M |
|---|---|---|
| pl11 | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 |
| pl23 | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 |
| pl37 | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 |
| plR1 | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 |

### Per book x session exact cap cells (clean: one book in one session)
| slice | cap | L3M | May-Jul |
|---|---|---|---|
| A7 asia | quantile 50 cap, horizon = 75th-percentile holding time | -17 (live -30; $4.84 -17) DD +0.0% ww +0 stops 4.03(4.03) | n/a |

### FOR THE LIVE BUILD (what D7 computes at the signal second)
From its own 1-minute bars: last 15/30/60/120-minute range and realised vol, same-offset range over the previous 20 sessions (median), session ranges of the last 5/20 sessions, range so far, the entry position in the session range (favourable-side room), elapsed fraction of the session, ln of the book-session horizon; a small coefficient table per session (15 weights, mean, sd, intercept, four residual quantile offsets) refit every 14 days and shipped as a static file. Cap = min(60, price x exp(prediction + quantile offset) - 2); orders: the target limit is placed at the capped price. The remaining-range version needs the HAR session forecast (T-RANGE2 file) or D7 computes its own 20-session mean. No intraday feed from the box.


## Per book and session, clean, and the assembled stack
**STATUS (plain, not a PASS; B1 in progress, no "nothing passes" verdict is allowed until it is done): single-book single-session cells scored in L3M for 15 of 14 slices; slice picks so far: {}.**

Method (user order PART B, 2026-11-15): each cell = the Dial 10 hook restricted to ONE book in ONE session (every other book/session unchanged at JN05W2), exact engine, all layers ON, live caps. Dollars are BASE lots; the x1.75 live figure sits beside each headline (live); the $4.84 figure reprices every contract at the FEES.md $4.84 RT (engine raw $1.18). Compared on the same book x session slice of JN05W2 (day locks/caps still interact across books, which is why the cells are run for real and not sliced from the global run). B1a settings per slice: direction both / narrow-only / wide-only x gearing 0.5 / 1.0 at the 75th-percentile horizon, plus narrow/wide g1.0 at the median horizon; "fixed" = JN05W2 itself. Walk-forward: the pick for each slice is made on 2026-05..07 only (older than L3M); L3M (2026-08..10) is then out-of-sample. B1b (around each pick): lots cap 1.5/3, lots follow half the change, dead band 0/20%, target ratio 0.8/1.2, lever stop-only (sl: stop W, lots inverse, target in the same points) / target-only (tg) / size-only (sz: bracket fixed, lots follow the forecast), noise floor k = 3/4/5 x recent 5-minute ATR (bracket never narrower), clips 25..120 / 20..150.

### B1 table: per slice, every cell (L3M, delta vs JN05W2 same slice; May-Jul = the selection window)
| slice | setting | May-Jul (selection) | L3M (out of sample) | L6M |
|---|---|---|---|---|
| A7 asia | both/g1.0/H75 | -374 (live -654; $4.84 -370) DD -10.9% ww -261 stops 2.97(3.88) | +47 (live +83; $4.84 +40) DD +25.6% ww +1495 stops 5.55(4.03) | -163 (live -286; $4.84 -165) DD -29.2% ww +1253 stops 4.26(3.96) |
| A7 asia | narrow/g1.0/H75 | -419 (live -733; $4.84 -423) DD -0.6% ww -175 stops 4.49(3.88) | -18 (live -32; $4.84 -26) DD +17.7% ww +722 stops 5.63(4.03) | -219 (live -383; $4.84 -224) DD -19.1% ww +722 stops 5.06(3.96) |
| A7 asia | both/g0.5/H75 | -556 (live -973; $4.84 -553) DD -9.2% ww +72 stops 3.50(3.88) | -192 (live -336; $4.84 -195) DD +10.1% ww +412 stops 5.10(4.03) | -374 (live -654; $4.84 -374) DD -36.6% ww +412 stops 4.30(3.96) |
| A7 asia | narrow/g0.5/H75 | -350 (live -612; $4.84 -352) DD +0.0% ww +0 stops 4.34(3.88) | -186 (live -325; $4.84 -189) DD +10.0% ww +552 stops 5.10(4.03) | -268 (live -469; $4.84 -270) DD -15.8% ww +552 stops 4.72(3.96) |
| A7 asia | wide/g1.0/H75 | +19 (live +33; $4.84 +26) DD -10.9% ww +283 stops 2.51(3.88) | -15 (live -26; $4.84 -14) DD +2.4% ww -426 stops 3.96(4.03) | +2 (live +3; $4.84 +6) DD -13.6% ww -426 stops 3.23(3.96) |
| A7 asia | wide/g0.5/H75 | n/a | -1 (live -1; $4.84 -1) DD +1.4% ww -140 stops 4.03(4.03) | n/a |
| A7 asia | wide/g1.0/H50 | n/a | -48 (live -85; $4.84 -48) DD -3.0% ww -426 stops 3.88(4.03) | n/a |
| A7 asia | narrow/g1.0/H50 | n/a | -159 (live -279; $4.84 -171) DD -8.3% ww +877 stops 5.93(4.03) | n/a |
| H7 asia | wide/g0.5/H75 | n/a | +123 (live +215; $4.84 +123) DD +0.0% ww +0 stops 0.23(0.23) | n/a |
| H7 asia | wide/g1.0/H75 | n/a | -67 (live -118; $4.84 -67) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | wide/g1.0/H50 | n/a | -312 (live -546; $4.84 -312) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | both/g0.0/H50 | -1814 (live -3175; $4.84 -1811) DD +9.9% ww +1967 stops 0.68(0.61) | -3 (live -5; $4.84 +3) DD -4.1% ww +0 stops 0.46(0.23) | -908 (live -1590; $4.84 -904) DD +9.9% ww +1967 stops 0.57(0.42) |
| H7 asia | both/g0.0/H50 | -1623 (live -2840; $4.84 -1619) DD +11.0% ww +3643 stops 0.46(0.61) | -972 (live -1701; $4.84 -967) DD -31.5% ww +0 stops 0.46(0.23) | -1298 (live -2271; $4.84 -1293) DD +11.0% ww +3643 stops 0.46(0.42) |
| H7 asia | both/g1.0/H75 | +1123 (live +1965; $4.84 +1129) DD +6.5% ww +1483 stops 0.53(0.61) | +177 (live +309; $4.84 +163) DD -33.6% ww -1228 stops 0.61(0.23) | +650 (live +1137; $4.84 +646) DD +6.5% ww +1483 stops 0.57(0.42) |
| H7 asia | narrow/g1.0/H75 | n/a | +244 (live +427; $4.84 +230) DD -33.6% ww -1228 stops 0.53(0.23) | n/a |
| H7 asia | both/g0.5/H75 | n/a | -574 (live -1004; $4.84 -580) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g0.5/H75 | n/a | -697 (live -1219; $4.84 -703) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g1.0/H50 | n/a | -355 (live -621; $4.84 -372) DD -120.5% ww -2166 stops 0.53(0.23) | n/a |
| H7 nyam | narrow/g1.0/H50 | n/a | +252 (live +441; $4.84 +252) DD +60.4% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | both/g1.0/H75 | n/a | +281 (live +491; $4.84 +280) DD +57.7% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | narrow/g1.0/H75 | -187 (live -328; $4.84 -188) DD -4.0% ww +0 stops 0.53(0.46) | +258 (live +452; $4.84 +258) DD +57.7% ww +480 stops 0.30(0.38) | +35 (live +62; $4.84 +35) DD +24.1% ww +480 stops 0.42(0.42) |
| H7 nyam | both/g0.0/H50 | -58 (live -102; $4.84 -58) DD +9.4% ww +0 stops 0.46(0.46) | +221 (live +387; $4.84 +221) DD +54.7% ww +195 stops 0.15(0.38) | +82 (live +143; $4.84 +81) DD +33.9% ww +195 stops 0.30(0.42) |
| H7 nyam | both/g0.0/H50 | -8 (live -14; $4.84 -8) DD +9.4% ww +0 stops 0.46(0.46) | +202 (live +353; $4.84 +202) DD +54.7% ww +195 stops 0.15(0.38) | +97 (live +170; $4.84 +97) DD +33.9% ww +195 stops 0.30(0.42) |
| H7 nyam | both/g0.5/H75 | +103 (live +180; $4.84 +103) DD +29.2% ww -83 stops 0.46(0.46) | +87 (live +153; $4.84 +87) DD +2.2% ww +195 stops 0.38(0.38) | +95 (live +167; $4.84 +95) DD +2.2% ww +195 stops 0.42(0.42) |
| H7 nyam | narrow/g0.5/H75 | n/a | +77 (live +134; $4.84 +77) DD +2.2% ww +195 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g0.5/H75 | n/a | +11 (live +19; $4.84 +11) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H75 | n/a | +22 (live +39; $4.84 +22) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H50 | n/a | +30 (live +53; $4.84 +30) DD +0.0% ww +0 stops 0.30(0.38) | n/a |
| K7 asia | wide/g1.0/H75 | n/a | +297 (live +520; $4.84 +298) DD +0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | wide/g0.5/H75 | n/a | -54 (live -94; $4.84 -54) DD -0.7% ww -404 stops 0.00(0.00) | n/a |
| K7 asia | narrow/g0.5/H75 | n/a | +1877 (live +3285; $4.84 +1855) DD -19.6% ww -2412 stops 0.00(0.00) | n/a |
| K7 asia | both/g0.5/H75 | n/a | +1823 (live +3191; $4.84 +1801) DD -28.8% ww -3232 stops 0.00(0.00) | n/a |
| K7 asia | wide/g1.0/H50 | n/a | -401 (live -702; $4.84 -400) DD -35.9% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | both/g1.0/H75 | n/a | +1292 (live +2261; $4.84 +1220) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H75 | n/a | +912 (live +1595; $4.84 +838) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H50 | n/a | +355 (live +621; $4.84 +268) DD -86.2% ww -5644 stops 0.00(0.00) | n/a |
| K7 london | both/g0.5/H75 | n/a | -9 (live -15; $4.84 -14) DD +8.7% ww +4326 stops 0.23(0.30) | n/a |
| K7 london | wide/g0.5/H75 | n/a | +27 (live +48; $4.84 +29) DD +0.5% ww +0 stops 0.30(0.30) | n/a |
| K7 london | wide/g1.0/H50 | n/a | +431 (live +755; $4.84 +433) DD -3.3% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g0.5/H75 | n/a | -123 (live -215; $4.84 -130) DD -4.2% ww +4733 stops 0.23(0.30) | n/a |
| K7 london | wide/g1.0/H75 | n/a | +157 (live +274; $4.84 +160) DD -4.8% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g1.0/H50 | n/a | -182 (live -319; $4.84 -204) DD -13.7% ww +3097 stops 0.23(0.30) | n/a |
| K7 london | both/g1.0/H75 | n/a | +481 (live +841; $4.84 +462) DD -25.5% ww +4257 stops 0.38(0.30) | n/a |
| K7 london | narrow/g1.0/H75 | n/a | -31 (live -55; $4.84 -55) DD -42.3% ww +4122 stops 0.38(0.30) | n/a |
| K7 nyam | both/g0.0/H50 | -645 (live -1129; $4.84 -647) DD -55.9% ww -1158 stops 0.08(0.08) | +805 (live +1408; $4.84 +793) DD +62.7% ww +1729 stops 0.00(0.00) | +80 (live +139; $4.84 +73) DD +44.5% ww +1153 stops 0.04(0.04) |
| K7 nyam | both/g0.0/H50 | -488 (live -855; $4.84 -488) DD -38.7% ww -514 stops 0.08(0.08) | +1078 (live +1886; $4.84 +1069) DD +53.9% ww +1605 stops 0.00(0.00) | +295 (live +516; $4.84 +290) DD +50.6% ww +1605 stops 0.04(0.04) |
| K7 nyam | narrow/g1.0/H50 | n/a | +769 (live +1345; $4.84 +761) DD +51.0% ww +2185 stops 0.00(0.00) | n/a |
| K7 nyam | both/g1.0/H75 | n/a | +1160 (live +2030; $4.84 +1153) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g1.0/H75 | n/a | +984 (live +1722; $4.84 +977) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g0.5/H75 | n/a | +668 (live +1170; $4.84 +667) DD +40.3% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | both/g0.5/H75 | n/a | +806 (live +1410; $4.84 +805) DD +39.5% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H75 | n/a | +176 (live +308; $4.84 +176) DD -0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H50 | n/a | +252 (live +441; $4.84 +253) DD -0.3% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g0.5/H75 | n/a | +137 (live +241; $4.84 +137) DD -0.8% ww +0 stops 0.00(0.00) | n/a |
| K7 nypm | wide/g1.0/H50 | n/a | +442 (live +773; $4.84 +442) DD +17.3% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | wide/g1.0/H75 | n/a | +70 (live +122; $4.84 +70) DD +13.1% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | both/g1.0/H75 | n/a | -184 (live -322; $4.84 -197) DD +9.8% ww +1145 stops 0.15(0.08) | n/a |
| K7 nypm | wide/g0.5/H75 | n/a | -4 (live -8; $4.84 -4) DD -1.5% ww -38 stops 0.00(0.08) | n/a |
| K7 nypm | narrow/g1.0/H50 | n/a | +48 (live +84; $4.84 +32) DD -1.9% ww +105 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g1.0/H75 | n/a | -254 (live -445; $4.84 -267) DD -3.3% ww +990 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g0.5/H75 | n/a | -266 (live -465; $4.84 -269) DD -26.7% ww +140 stops 0.08(0.08) | n/a |
| K7 nypm | both/g0.5/H75 | n/a | -270 (live -473; $4.84 -274) DD -27.3% ww +102 stops 0.00(0.08) | n/a |
| M7 london | wide/g1.0/H75 | n/a | +1614 (live +2824; $4.84 +1616) DD +4.9% ww +1190 stops 0.53(0.91) | n/a |
| M7 london | wide/g0.5/H75 | n/a | +688 (live +1204; $4.84 +689) DD +4.4% ww +1400 stops 0.84(0.91) | n/a |
| M7 london | wide/g1.0/H50 | n/a | +538 (live +942; $4.84 +540) DD -1.3% ww -80 stops 0.84(0.91) | n/a |
| M7 london | both/g0.5/H75 | n/a | +1147 (live +2008; $4.84 +1139) DD -8.1% ww +130 stops 1.07(0.91) | n/a |
| M7 london | narrow/g0.5/H75 | n/a | +417 (live +730; $4.84 +408) DD -10.9% ww -1075 stops 1.14(0.91) | n/a |
| M7 london | narrow/g1.0/H50 | n/a | +476 (live +833; $4.84 +446) DD -19.9% ww +1144 stops 1.45(0.91) | n/a |
| M7 london | narrow/g1.0/H75 | n/a | -366 (live -640; $4.84 -390) DD -20.4% ww +80 stops 1.29(0.91) | n/a |
| M7 london | both/g1.0/H75 | n/a | +1142 (live +1999; $4.84 +1121) DD -23.2% ww -729 stops 0.91(0.91) | n/a |
| M7 nyam | narrow/g1.0/H50 | n/a | +439 (live +769; $4.84 +424) DD +26.0% ww -222 stops 0.38(0.23) | n/a |
| M7 nyam | both/g0.5/H75 | n/a | +79 (live +138; $4.84 +75) DD +0.8% ww +194 stops 0.30(0.23) | n/a |
| M7 nyam | narrow/g0.5/H75 | n/a | +73 (live +127; $4.84 +69) DD +0.8% ww +194 stops 0.38(0.23) | n/a |
| M7 nyam | wide/g0.5/H75 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H75 | n/a | +16 (live +28; $4.84 +16) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H50 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | both/g1.0/H75 | n/a | +419 (live +733; $4.84 +405) DD -6.8% ww -991 stops 0.46(0.23) | n/a |
| M7 nyam | narrow/g1.0/H75 | n/a | +402 (live +704; $4.84 +388) DD -6.8% ww -991 stops 0.53(0.23) | n/a |
| M7 nyam | both/g0.0/H50 | -130 (live -227; $4.84 -131) DD -16.3% ww -1329 stops 0.61(0.61) | +102 (live +179; $4.84 +99) DD -11.5% ww +0 stops 0.23(0.23) | -14 (live -24; $4.84 -16) DD -19.5% ww -1329 stops 0.42(0.42) |
| P7 asia | both/g0.0/H50 | -5189 (live -9081; $4.84 -4987) DD +44.9% ww +11844 stops 0.00(0.00) | -703 (live -1230; $4.84 -620) DD +51.2% ww +20259 stops 0.08(0.15) | -2946 (live -5156; $4.84 -2804) DD +51.2% ww +17717 stops 0.04(0.08) |
| P7 asia | both/g0.0/H50 | -6897 (live -12069; $4.84 -6699) DD +42.2% ww +13069 stops 0.00(0.00) | -322 (live -564; $4.84 -245) DD +51.2% ww +19309 stops 0.08(0.15) | -3609 (live -6317; $4.84 -3472) DD +51.2% ww +18942 stops 0.04(0.08) |
| P7 asia | narrow/g1.0/H50 | n/a | -3918 (live -6857; $4.84 -4186) DD -0.4% ww -4286 stops 0.46(0.15) | n/a |
| P7 asia | both/g0.5/H75 | n/a | -5946 (live -10406; $4.84 -6044) DD -1.0% ww +6944 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g0.5/H75 | n/a | -5762 (live -10084; $4.84 -5860) DD -1.0% ww +9022 stops 0.15(0.15) | n/a |
| P7 asia | wide/g0.5/H75 | n/a | -184 (live -322; $4.84 -183) DD -4.9% ww -2079 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g1.0/H75 | n/a | -2696 (live -4718; $4.84 -2882) DD -7.8% ww -10346 stops 0.53(0.15) | n/a |
| P7 asia | wide/g1.0/H50 | n/a | -816 (live -1428; $4.84 -812) DD -22.6% ww -9033 stops 0.15(0.15) | n/a |
| P7 asia | wide/g1.0/H75 | n/a | -491 (live -858; $4.84 -490) DD -25.2% ww -10331 stops 0.15(0.15) | n/a |
| P7 asia | both/g1.0/H75 | n/a | -3315 (live -5802; $4.84 -3501) DD -36.1% ww -13164 stops 0.53(0.15) | n/a |
| P7 london | both/g0.5/H75 | n/a | +894 (live +1565; $4.84 +886) DD +29.6% ww -1633 stops 0.08(0.08) | n/a |
| P7 london | narrow/g0.5/H75 | n/a | +386 (live +675; $4.84 +375) DD +28.5% ww -1328 stops 0.08(0.08) | n/a |
| P7 london | narrow/g1.0/H50 | n/a | +927 (live +1622; $4.84 +895) DD +19.7% ww -3009 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H75 | n/a | -142 (live -249; $4.84 -138) DD +2.7% ww -458 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H50 | n/a | +265 (live +464; $4.84 +266) DD +1.1% ww +0 stops 0.08(0.08) | n/a |
| P7 london | wide/g0.5/H75 | n/a | +385 (live +674; $4.84 +387) DD -1.9% ww -238 stops 0.08(0.08) | n/a |
| P7 london | both/g1.0/H75 | n/a | +1179 (live +2064; $4.84 +1145) DD -9.8% ww -5408 stops 0.15(0.08) | n/a |
| P7 london | narrow/g1.0/H75 | n/a | +1322 (live +2313; $4.84 +1282) DD -14.4% ww -5203 stops 0.15(0.08) | n/a |
| P7 nyam | both/g0.0/H50 | -1333 (live -2333; $4.84 -1305) DD +88.2% ww +6983 stops 0.00(0.08) | +198 (live +346; $4.84 +220) DD +55.7% ww +1594 stops 0.15(0.38) | -568 (live -994; $4.84 -542) DD +59.1% ww +4666 stops 0.08(0.23) |
| P7 nyam | both/g1.0/H75 | n/a | +697 (live +1220; $4.84 +685) DD +51.3% ww +354 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g1.0/H75 | n/a | +543 (live +951; $4.84 +529) DD +45.9% ww +324 stops 0.30(0.38) | n/a |
| P7 nyam | both/g0.5/H75 | n/a | +105 (live +184; $4.84 +99) DD +36.7% ww +238 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g0.5/H75 | n/a | -13 (live -23; $4.84 -20) DD +36.4% ww +262 stops 0.30(0.38) | n/a |
| P7 nyam | wide/g0.5/H75 | n/a | +118 (live +207; $4.84 +119) DD +0.3% ww -25 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H75 | n/a | +16 (live +27; $4.84 +17) DD -7.5% ww -105 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H50 | n/a | -544 (live -952; $4.84 -543) DD -47.7% ww -3348 stops 0.38(0.38) | n/a |
| U7 asia | narrow/g1.0/H50 | n/a | +1222 (live +2139; $4.84 +1201) DD +15.6% ww -265 stops 1.90(1.83) | n/a |
| U7 asia | both/g1.0/H75 | n/a | +71 (live +124; $4.84 +56) DD +8.3% ww -1836 stops 1.98(1.83) | n/a |
| U7 asia | narrow/g1.0/H75 | n/a | +502 (live +879; $4.84 +487) DD +8.3% ww +983 stops 1.98(1.83) | n/a |
| U7 asia | both/g0.5/H75 | n/a | -800 (live -1399; $4.84 -808) DD +6.6% ww -2883 stops 2.05(1.83) | n/a |
| U7 asia | narrow/g0.5/H75 | n/a | -162 (live -284; $4.84 -170) DD +6.6% ww +57 stops 2.05(1.83) | n/a |
| U7 asia | wide/g0.5/H75 | n/a | -637 (live -1115; $4.84 -637) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H75 | n/a | -431 (live -755; $4.84 -431) DD +0.0% ww -1836 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H50 | n/a | -648 (live -1134; $4.84 -648) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 london | narrow/g0.5/H75 | n/a | +393 (live +687; $4.84 +392) DD +17.2% ww +1796 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H75 | n/a | +246 (live +431; $4.84 +243) DD +3.1% ww -1185 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H50 | n/a | -41 (live -72; $4.84 -48) DD -9.9% ww -1991 stops 1.52(1.45) | n/a |
| U7 london | both/g0.5/H75 | n/a | -891 (live -1560; $4.84 -890) DD -25.4% ww -3538 stops 1.52(1.45) | n/a |
| U7 london | wide/g1.0/H50 | n/a | -839 (live -1468; $4.84 -837) DD -33.9% ww -4122 stops 1.37(1.45) | n/a |
| U7 london | wide/g0.5/H75 | n/a | -1284 (live -2247; $4.84 -1282) DD -44.3% ww -6280 stops 1.52(1.45) | n/a |
| U7 london | both/g1.0/H75 | n/a | -1728 (live -3025; $4.84 -1729) DD -105.5% ww -7540 stops 1.60(1.45) | n/a |
| U7 london | wide/g1.0/H75 | n/a | -1975 (live -3455; $4.84 -1972) DD -109.8% ww -6355 stops 1.60(1.45) | n/a |

### Summary per slice: pick made on May-Jul, result on L3M
| slice | pick | L3M result of the pick | verdict |
|---|---|---|---|
| A7 asia | pending | | |
| H7 asia | pending | | |
| H7 nyam | pending | | |
| K7 asia | pending | | |
| K7 london | pending | | |
| K7 nyam | pending | | |
| K7 nypm | pending | | |
| M7 london | pending | | |
| M7 nyam | pending | | |
| P7 asia | pending | | |
| P7 london | pending | | |
| P7 nyam | pending | | |
| U7 asia | pending | | |
| U7 london | pending | | |

### B2: why the global version adds full stops (narrow-only/both g1.0 H75 cell, L3M, trade tables)
Reference JN05W2 L3M (no O7): 1855 trades, stop rate 0.071, 132 stops (13 weeks).

**M1_75_g10_c1_d10_c20_tb_B**: 2038 trades (+183 vs JN05W2), stops 173 (+41), stop rate 0.085 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 437 | 0.103 | 3.05 | 94 |
| (40, 50] | 721 | 0.074 | 2.36 | 271 |
| (50, 55] | 232 | 0.099 | 1.97 | 169 |
| (55, 60] | 435 | 0.076 | 1.87 | 76 |
| (60, 70] | 75 | 0.120 | 2.01 | -385 |
| (70, 80] | 62 | 0.048 | 1.68 | -284 |
| (80, 101] | 76 | 0.092 | 1.13 | -591 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1543 | 0.069 | 2.21 | 54 |
| (3.0, 4.0] | 294 | 0.116 | 2.29 | 239 |
| (4.0, 5.0] | 74 | 0.108 | 2.31 | 364 |
| (5.0, 6.0] | 6 | 0.167 | 2.50 | 172 |
| (6.0, 8.0] | 4 | 0.000 | 1.00 | -119 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1068 | 0.096 | 1.00 | 4 |
| (1, 2] | 385 | 0.078 | 2.00 | 115 |
| (2, 3] | 215 | 0.093 | 3.00 | 23 |
| (3, 5] | 195 | 0.062 | 4.46 | 256 |
| (5, 8] | 138 | 0.065 | 6.70 | 690 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

**M1_75_g10_c1_d10_c20_tb_N**: 2072 trades (+217 vs JN05W2), stops 178 (+46), stop rate 0.086 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 449 | 0.105 | 3.02 | 97 |
| (40, 50] | 725 | 0.073 | 2.35 | 272 |
| (50, 55] | 236 | 0.102 | 1.97 | 150 |
| (55, 60] | 662 | 0.082 | 1.82 | -29 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1644 | 0.072 | 2.18 | 50 |
| (3.0, 4.0] | 264 | 0.121 | 2.38 | 348 |
| (4.0, 5.0] | 44 | 0.091 | 3.11 | 1063 |
| (5.0, 6.0] | 3 | 0.000 | 3.33 | 68 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1073 | 0.095 | 1.00 | 8 |
| (1, 2] | 413 | 0.085 | 2.00 | 117 |
| (2, 3] | 197 | 0.081 | 3.00 | 213 |
| (3, 5] | 217 | 0.074 | 4.43 | 196 |
| (5, 8] | 135 | 0.067 | 6.74 | 714 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

Reading of the W/ATR5 table: ATR5 = mean range of the last 14 five-minute buckets in points; a bracket 3x ATR5 or less is within ordinary 5-minute noise. The noise-floor cells (floor 3/4/5 x ATR5, narrowing only) are listed in B3.


### B3: levers (stop-only / target-only / both / size-only) and noise floor, per slice
| slice | cell | L3M | May-Jul |
|---|---|---|---|

### B4: assembled stack (each slice at its own walk-forward pick, run together)
(not run yet: starts when every slice has a pick)


## Target capped at the forecast
**VERDICT (plain, not a PASS; FIRST PASS; 15 of 26 global exact cap cells scored in L3M, per book x session exact cells still running): planted-edge check PASSED through the exact engine (look-ahead oracle target 0.9 x realised MFE: +85531 $/wk, DD +67.0%, ww +64263; this is a mechanism check, NOT a result); the reachable move is only weakly forecastable (R2 on ln MFE 0.03-0.14, quantile calibration good); in the exact L3M cells the cap at the forecast 50th-percentile move (horizon = 75th-percentile holding time) gives +1486 $/wk, DD -0.5%, ww -240 and the 75th-percentile cap +177 $/wk, DD +0.0%, ww +0, the remaining-range caps cut drawdown (own k1.0 -6226 $/wk, DD +27.0%, ww +12290; HAR k1.0 -7259 $/wk, DD +39.4%, ww +17319) but cost thousands per week. Best exact L3M cap cell inside the mean gate by DD: PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time (DD +7.9%, -120 $/wk). L6M/HOLD/older still to run before any verdict.**

Planted-edge check (H1) for the capping mechanism: cells `tcoracle0.9` / `0.6` set the target to 0.9 / 0.6 x the REALISED maximum favourable move (look-ahead, only to prove the mechanism can show an edge through the exact engine); they must come out strongly positive. Status below in the exact table. Until they do, an exact cap verdict is not stated.

Definition. Reachable move = maximum favourable excursion from the signal-second bar close over the book-session holding horizon H (H50/H75 = median / 75th percentile holding time of that book+session, causal), points. Model: walk-forward ridge (14-day blocks, expanding, min 90 days, per session) on ln((MFE+2)/price) from the Dial 10 own-bar inputs (last 15/30/60/120 min range and vol, same-clock normal, own session level, range used so far, elapsed fraction) plus the side-aware room in the session range so far; quantiles q = fitted + empirical training-residual quantile (50/60/75/90). Cap: target = min(book target 60 pts [58 after fills], q-quantile), stop, lots and every other level unchanged. Remaining-range cap: target = min(book target, k x (session range forecast - range printed so far)), forecast = own (price x exp(sf20), mean of the last 20 sessions) or T-RANGE2 HAR (fc_r2_har, available-epoch checked). Small caps (< 30 pts = 0.5 x stop): take / skip / half. EV target: argmax over T in [20, book target or 300] of T x P(MFE>=T) - stop x (1-P) with the lognormal forecast (ignores the stop-first ordering, so optimistic). Extension: if the forecast median MFE is >= m x book target, target = min(q50, 2 x book target). Lots/base basis: dollars are BASE lots (live x1.75 = multiply by 1.75); fee columns $4.84 beside raw $1.18 where shown.

### Item 1: calibration of the forecast quantiles (share of trades whose realized MFE exceeded the forecast quantile; a q-quantile should be exceeded 1-q of the time = 0.50 / 0.40 / 0.25 / 0.10) and R2 of ln MFE, per session
| H | session | window | n | >q50 | >q60 | >q75 | >q90 | R2 ln MFE | median q75 (pts) | share q75 < 60 |
|---|---|---|---|---|---|---|---|---|---|---|
| 50 | asia | older (<2026-05) | 5119 | 0.51 | 0.41 | 0.26 | 0.12 | 0.121 | 80 | 0.222 |
| 50 | asia | L6M | 2006 | 0.49 | 0.38 | 0.23 | 0.08 | 0.058 | 111 | 0.047 |
| 50 | asia | L3M | 875 | 0.46 | 0.34 | 0.20 | 0.07 | -0.014 | 90 | 0.098 |
| 50 | london | older (<2026-05) | 4892 | 0.51 | 0.41 | 0.26 | 0.11 | 0.142 | 62 | 0.438 |
| 50 | london | L6M | 1406 | 0.48 | 0.37 | 0.23 | 0.08 | 0.028 | 76 | 0.166 |
| 50 | london | L3M | 673 | 0.48 | 0.37 | 0.24 | 0.07 | -0.008 | 68 | 0.247 |
| 50 | nyam | older (<2026-05) | 4142 | 0.47 | 0.38 | 0.24 | 0.11 | 0.077 | 63 | 0.397 |
| 50 | nyam | L6M | 600 | 0.51 | 0.40 | 0.24 | 0.09 | 0.097 | 83 | 0.157 |
| 50 | nyam | L3M | 271 | 0.51 | 0.38 | 0.20 | 0.06 | 0.077 | 68 | 0.258 |
| 50 | nypm | older (<2026-05) | 817 | 0.48 | 0.40 | 0.26 | 0.13 | 0.073 | 62 | 0.419 |
| 50 | nypm | L6M | 150 | 0.59 | 0.50 | 0.33 | 0.13 | 0.221 | 71 | 0.307 |
| 50 | nypm | L3M | 56 | 0.50 | 0.36 | 0.21 | 0.09 | 0.104 | 54 | 0.589 |
| 50 | all | older (<2026-05) | 14970 | 0.50 | 0.40 | 0.26 | 0.12 | 0.123 | 68 | 0.352 |
| 50 | all | L6M | 4162 | 0.49 | 0.38 | 0.23 | 0.08 | 0.080 | 91 | 0.113 |
| 50 | all | L3M | 1875 | 0.47 | 0.36 | 0.21 | 0.07 | 0.014 | 76 | 0.189 |
| 75 | asia | older (<2026-05) | 5119 | 0.52 | 0.41 | 0.26 | 0.12 | 0.134 | 122 | 0.032 |
| 75 | asia | L6M | 2006 | 0.50 | 0.40 | 0.24 | 0.08 | 0.027 | 178 | 0.000 |
| 75 | asia | L3M | 875 | 0.45 | 0.35 | 0.20 | 0.05 | -0.016 | 156 | 0.000 |
| 75 | london | older (<2026-05) | 4891 | 0.51 | 0.42 | 0.27 | 0.11 | 0.157 | 101 | 0.100 |
| 75 | london | L6M | 1406 | 0.49 | 0.37 | 0.21 | 0.08 | 0.069 | 118 | 0.001 |
| 75 | london | L3M | 673 | 0.49 | 0.38 | 0.21 | 0.09 | 0.025 | 108 | 0.000 |
| 75 | nyam | older (<2026-05) | 4142 | 0.48 | 0.38 | 0.23 | 0.10 | 0.065 | 91 | 0.081 |
| 75 | nyam | L6M | 600 | 0.50 | 0.40 | 0.24 | 0.10 | 0.098 | 125 | 0.015 |
| 75 | nyam | L3M | 271 | 0.44 | 0.34 | 0.19 | 0.05 | 0.051 | 103 | 0.015 |
| 75 | nypm | older (<2026-05) | 812 | 0.49 | 0.37 | 0.26 | 0.11 | 0.043 | 87 | 0.095 |
| 75 | nypm | L6M | 150 | 0.53 | 0.46 | 0.34 | 0.17 | 0.179 | 117 | 0.013 |
| 75 | nypm | L3M | 56 | 0.41 | 0.30 | 0.21 | 0.07 | -0.076 | 93 | 0.036 |
| 75 | all | older (<2026-05) | 14964 | 0.51 | 0.40 | 0.25 | 0.11 | 0.131 | 102 | 0.071 |
| 75 | all | L6M | 4162 | 0.50 | 0.39 | 0.23 | 0.09 | 0.079 | 149 | 0.003 |
| 75 | all | L3M | 1875 | 0.46 | 0.36 | 0.20 | 0.06 | 0.032 | 128 | 0.003 |

### Items 3 and 4 (and 2): offline replay of the caps on the JN05W2 trade paths, all 43 months (estimate: 1-min paths, cap counted only before the exit bar, so cut/stop ordering is conservative; the exact cells below decide). d mean $/wk and DD cut % vs JN05W2 on the same trades, scope all, then per session for the cap with the most trades capped
| cap | small-cap rule | scope | window | d mean $/wk (live x1.75) | DD cut % | d worst week | d stops/wk | share capped | share where cap hit |
|---|---|---|---|---|---|---|---|---|---|
| q50_H50 | take | all | L3M | +409 (+715) | -3.9 | -1411 | +0.00 | 0.82 | 0.45 |
| q50_H50 | take | all | L6M | -96 (-169) | -3.9 | -1411 | +0.00 | 0.62 | 0.33 |
| q50_H50 | take | all | OLDER | -1795 (-3141) | +12.0 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | skip | all | L3M | -1581 (-2767) | -5.0 | -1996 | +0.00 | 0.82 | 0.45 |
| q50_H50 | skip | all | L6M | -1445 (-2528) | -5.0 | -1996 | +0.00 | 0.62 | 0.33 |
| q50_H50 | skip | all | OLDER | -2271 (-3975) | +17.4 | +13127 | +0.00 | 0.80 | 0.45 |
| q50_H50 | half | all | L3M | -586 (-1026) | -4.4 | -1704 | +0.00 | 0.82 | 0.45 |
| q50_H50 | half | all | L6M | -771 (-1348) | -4.4 | -1704 | +0.00 | 0.62 | 0.33 |
| q50_H50 | half | all | OLDER | -2033 (-3558) | +16.5 | +13127 | +0.00 | 0.80 | 0.45 |
| q60_H50 | take | all | L3M | -1525 (-2668) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | take | all | L6M | -839 (-1469) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | take | all | OLDER | -1296 (-2267) | +12.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | skip | all | L3M | -3272 (-5726) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | skip | all | L6M | -1811 (-3170) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | skip | all | OLDER | -1648 (-2885) | +8.8 | +15462 | +0.00 | 0.66 | 0.35 |
| q60_H50 | half | all | L3M | -2398 (-4197) | +4.5 | +2462 | +0.00 | 0.61 | 0.31 |
| q60_H50 | half | all | L6M | -1325 (-2319) | +4.5 | +2462 | +0.00 | 0.42 | 0.21 |
| q60_H50 | half | all | OLDER | -1472 (-2576) | +10.7 | +15462 | +0.00 | 0.66 | 0.35 |
| q75_H50 | take | all | L3M | +414 (+725) | -0.4 | -214 | +0.00 | 0.21 | 0.11 |
| q75_H50 | take | all | L6M | -44 (-77) | -0.4 | -214 | +0.00 | 0.13 | 0.06 |
| q75_H50 | take | all | OLDER | -719 (-1258) | -1.1 | +13801 | +0.00 | 0.37 | 0.18 |
| q90_H50 | take | all | L3M | +191 (+334) | +0.0 | +0 | +0.00 | 0.02 | 0.01 |
| q90_H50 | take | all | L6M | +142 (+249) | +0.0 | +0 | +0.00 | 0.01 | 0.01 |
| q90_H50 | take | all | OLDER | -169 (-296) | -1.8 | +1686 | +0.00 | 0.08 | 0.03 |
| q50_H75 | take | all | L3M | +128 (+225) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | take | all | L6M | +624 (+1092) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | take | all | OLDER | -931 (-1628) | -13.1 | +11346 | +0.00 | 0.51 | 0.26 |
| q50_H75 | skip | all | L3M | +178 (+312) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | skip | all | L6M | +685 (+1198) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | skip | all | OLDER | -1302 (-2279) | -4.6 | +14384 | +0.00 | 0.51 | 0.26 |
| q50_H75 | half | all | L3M | +153 (+268) | -0.5 | -241 | +0.00 | 0.30 | 0.15 |
| q50_H75 | half | all | L6M | +654 (+1145) | -0.5 | -241 | +0.00 | 0.20 | 0.10 |
| q50_H75 | half | all | OLDER | -1116 (-1954) | -8.8 | +12865 | +0.00 | 0.51 | 0.26 |
| q60_H75 | take | all | L3M | +830 (+1452) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | take | all | L6M | +379 (+664) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | take | all | OLDER | -478 (-836) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | skip | all | L3M | +958 (+1677) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | skip | all | L6M | +421 (+737) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | skip | all | OLDER | -402 (-703) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q60_H75 | half | all | L3M | +894 (+1564) | -0.1 | -30 | +0.00 | 0.10 | 0.05 |
| q60_H75 | half | all | L6M | +400 (+700) | -0.1 | -30 | +0.00 | 0.07 | 0.03 |
| q60_H75 | half | all | OLDER | -440 (-769) | +4.1 | +8380 | +0.00 | 0.31 | 0.15 |
| q75_H75 | take | all | L3M | +236 (+413) | +0.0 | +0 | +0.00 | 0.01 | 0.00 |
| q75_H75 | take | all | L6M | +105 (+185) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q75_H75 | take | all | OLDER | -255 (-446) | -1.9 | +1485 | +0.00 | 0.08 | 0.04 |
| q90_H75 | take | all | L3M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | L6M | +0 (+0) | +0.0 | +0 | +0.00 | 0.00 | 0.00 |
| q90_H75 | take | all | OLDER | +10 (+18) | -0.4 | +0 | +0.00 | 0.01 | 0.00 |
| rem_own_k0.5 | take | all | L3M | -6674 (-11680) | +8.8 | -1861 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | take | all | L6M | -13204 (-23108) | +8.7 | -1861 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | take | all | OLDER | -7381 (-12916) | -40.2 | +20529 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | skip | all | L3M | -5271 (-9225) | +21.7 | +2982 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | skip | all | L6M | -10625 (-18594) | +21.7 | +2982 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | skip | all | OLDER | -6272 (-10977) | +17.3 | +21712 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.5 | half | all | L3M | -5973 (-10452) | +16.3 | +560 | +0.00 | 0.67 | 0.44 |
| rem_own_k0.5 | half | all | L6M | -11915 (-20851) | +16.3 | +560 | +0.00 | 0.68 | 0.48 |
| rem_own_k0.5 | half | all | OLDER | -6827 (-11946) | +0.6 | +23150 | +0.00 | 0.88 | 0.64 |
| rem_own_k0.75 | take | all | L3M | -7140 (-12494) | +9.6 | +3294 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | take | all | L6M | -10636 (-18614) | +9.6 | +3294 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | take | all | OLDER | -5846 (-10230) | -24.0 | +12208 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | skip | all | L3M | -3661 (-6406) | +10.3 | +4045 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | skip | all | L6M | -6650 (-11638) | +10.3 | +4045 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | skip | all | OLDER | -3856 (-6749) | +16.1 | +19073 | +0.00 | 0.73 | 0.53 |
| rem_own_k0.75 | half | all | L3M | -5400 (-9450) | +13.0 | +3670 | +0.00 | 0.45 | 0.30 |
| rem_own_k0.75 | half | all | L6M | -8643 (-15126) | +13.0 | +3670 | +0.00 | 0.50 | 0.36 |
| rem_own_k0.75 | half | all | OLDER | -4851 (-8489) | +13.0 | +20157 | +0.00 | 0.73 | 0.53 |
| rem_own_k1.0 | take | all | L3M | -5516 (-9653) | +18.3 | +9104 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | take | all | L6M | -8765 (-15339) | +18.3 | +9104 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | take | all | OLDER | -5714 (-9999) | -58.2 | +11926 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | skip | all | L3M | -3265 (-5714) | +15.0 | +8858 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | skip | all | L6M | -5683 (-9944) | +15.0 | +8858 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | skip | all | OLDER | -3872 (-6775) | -61.0 | +20250 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.0 | half | all | L3M | -4391 (-7683) | +18.5 | +8981 | +0.00 | 0.36 | 0.25 |
| rem_own_k1.0 | half | all | L6M | -7224 (-12642) | +18.5 | +8981 | +0.00 | 0.41 | 0.31 |
| rem_own_k1.0 | half | all | OLDER | -4793 (-8387) | -58.0 | +21393 | +0.00 | 0.61 | 0.46 |
| rem_own_k1.25 | take | all | L3M | -3112 (-5446) | +24.4 | +13750 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | take | all | L6M | -8275 (-14481) | +24.4 | +13750 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | take | all | OLDER | -5400 (-9450) | -15.5 | +4336 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | skip | all | L3M | -456 (-797) | +22.4 | +13720 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | skip | all | L6M | -4232 (-7405) | +22.4 | +13720 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | skip | all | OLDER | -3310 (-5792) | -36.4 | +22803 | +0.00 | 0.54 | 0.41 |
| rem_own_k1.25 | half | all | L3M | -1784 (-3121) | +25.2 | +15286 | +0.00 | 0.31 | 0.22 |
| rem_own_k1.25 | half | all | L6M | -6253 (-10943) | +25.2 | +15286 | +0.00 | 0.36 | 0.28 |
| rem_own_k1.25 | half | all | OLDER | -4355 (-7621) | -18.3 | +15544 | +0.00 | 0.54 | 0.41 |

Per session, q60 H75 take-anyway and remaining-range k=1.25 (own):
| cap | session | window | d mean $/wk | DD cut % | d worst week | share capped |
|---|---|---|---|---|---|---|
| q60_H75 | asia | L3M | +221 | +0.0 | +0 | 0.02 |
| q60_H75 | asia | L6M | +110 | +0.0 | +0 | 0.01 |
| q60_H75 | asia | OLDER | -124 | -0.0 | +0 | 0.23 |
| q60_H75 | london | L3M | +745 | +3.8 | +0 | 0.16 |
| q60_H75 | london | L6M | +330 | +3.8 | +0 | 0.12 |
| q60_H75 | london | OLDER | -294 | -2.1 | +0 | 0.35 |
| q60_H75 | nyam | L3M | +61 | -7.2 | +0 | 0.15 |
| q60_H75 | nyam | L6M | -14 | +0.0 | +0 | 0.10 |
| q60_H75 | nyam | OLDER | -37 | -6.0 | +1403 | 0.37 |
| q60_H75 | nypm | L3M | -197 | -0.0 | +0 | 0.41 |
| q60_H75 | nypm | L6M | -47 | +0.0 | +0 | 0.20 |
| q60_H75 | nypm | OLDER | -22 | -5.4 | +0 | 0.33 |
| rem_own_k1.25 | asia | L3M | -4547 | +35.2 | +434 | 0.37 |
| rem_own_k1.25 | asia | L6M | -6717 | +27.1 | +434 | 0.38 |
| rem_own_k1.25 | asia | OLDER | -4532 | -27.4 | +10774 | 0.62 |
| rem_own_k1.25 | london | L3M | +2278 | +46.3 | +12347 | 0.24 |
| rem_own_k1.25 | london | L6M | +1196 | +46.3 | +12347 | 0.30 |
| rem_own_k1.25 | london | OLDER | -510 | +12.9 | +3024 | 0.51 |
| rem_own_k1.25 | nyam | L3M | -650 | +20.0 | +0 | 0.24 |
| rem_own_k1.25 | nyam | L6M | -2127 | -8.9 | +1531 | 0.39 |
| rem_own_k1.25 | nyam | OLDER | -53 | +10.3 | +7327 | 0.47 |
| rem_own_k1.25 | nypm | L3M | -192 | +21.8 | +1203 | 0.45 |
| rem_own_k1.25 | nypm | L6M | -627 | +21.8 | +1203 | 0.50 |
| rem_own_k1.25 | nypm | OLDER | -304 | -2.4 | -831 | 0.50 |

### Item 4 per book x session (all 43 months): trades whose 60-pt target lies beyond the forecast quantile, their fixed-target result, the capped replay, and how far trades run past the cap
| book | session | cap | trades | share beyond | fixed-target hit rate | fixed avg $/trade | capped avg $/trade | avg points run past cap |
|---|---|---|---|---|---|---|---|---|
| A7 | asia | q50_H75 | 1156 | 0.25 | 0.50 | 60 | 87 | 10.4 |
| A7 | asia | q60_H75 | 1156 | 0.13 | 0.47 | 4 | 26 | 8.8 |
| A7 | asia | q75_H75 | 1156 | 0.03 | 0.48 | 19 | 6 | 11.1 |
| A7 | asia | rem_own_k0.75 | 1156 | 0.74 | 0.52 | 126 | 22 | 32.9 |
| H7 | asia | q50_H75 | 700 | 0.33 | 0.49 | 164 | 181 | 11.3 |
| H7 | asia | q60_H75 | 700 | 0.18 | 0.56 | 447 | 414 | 10.7 |
| H7 | asia | q75_H75 | 700 | 0.02 | 0.50 | -318 | -267 | 16.1 |
| H7 | asia | rem_own_k0.75 | 700 | 0.71 | 0.48 | 208 | 55 | 27.8 |
| H7 | nyam | q50_H75 | 348 | 0.49 | 0.46 | 84 | 25 | 8.9 |
| H7 | nyam | q60_H75 | 348 | 0.25 | 0.47 | 96 | 46 | 7.4 |
| H7 | nyam | q75_H75 | 348 | 0.06 | 0.33 | -113 | -12 | 4.7 |
| H7 | nyam | rem_own_k0.75 | 348 | 0.66 | 0.47 | 62 | -35 | 23.3 |
| K7 | asia | q50_H75 | 2596 | 0.32 | 0.44 | 102 | 74 | 9.7 |
| K7 | asia | q60_H75 | 2596 | 0.19 | 0.44 | 111 | 90 | 7.6 |
| K7 | asia | q75_H75 | 2596 | 0.04 | 0.40 | 26 | 1 | 6.1 |
| K7 | asia | rem_own_k0.75 | 2596 | 0.68 | 0.44 | 88 | 0 | 27.2 |
| K7 | london | q50_H75 | 1781 | 0.57 | 0.43 | 62 | 37 | 10.9 |
| K7 | london | q60_H75 | 1781 | 0.33 | 0.44 | 60 | 35 | 9.4 |
| K7 | london | q75_H75 | 1781 | 0.12 | 0.48 | 138 | 101 | 6.5 |
| K7 | london | rem_own_k0.75 | 1781 | 0.69 | 0.43 | 45 | -12 | 27.4 |
| K7 | nyam | q50_H75 | 1565 | 0.57 | 0.42 | 21 | 18 | 10.0 |
| K7 | nyam | q60_H75 | 1565 | 0.32 | 0.40 | -4 | -17 | 9.0 |
| K7 | nyam | q75_H75 | 1565 | 0.07 | 0.41 | 40 | 36 | 16.3 |
| K7 | nyam | rem_own_k0.75 | 1565 | 0.70 | 0.39 | -21 | -38 | 26.0 |
| K7 | nypm | q50_H75 | 1136 | 0.50 | 0.36 | 65 | 54 | 8.1 |
| K7 | nypm | q60_H75 | 1136 | 0.31 | 0.34 | 62 | 48 | 5.6 |
| K7 | nypm | q75_H75 | 1136 | 0.09 | 0.29 | 155 | 179 | 3.5 |
| K7 | nypm | rem_own_k0.75 | 1136 | 0.71 | 0.37 | 72 | -30 | 23.7 |
| M7 | london | q50_H75 | 2489 | 0.42 | 0.43 | 45 | 40 | 10.0 |
| M7 | london | q60_H75 | 2489 | 0.24 | 0.43 | 32 | 26 | 8.2 |
| M7 | london | q75_H75 | 2489 | 0.06 | 0.38 | -74 | -97 | 7.1 |
| M7 | london | rem_own_k0.75 | 2489 | 0.59 | 0.39 | -40 | -29 | 22.9 |
| M7 | nyam | q50_H75 | 1496 | 0.52 | 0.43 | 49 | 22 | 8.6 |
| M7 | nyam | q60_H75 | 1496 | 0.27 | 0.44 | 76 | 57 | 7.2 |
| M7 | nyam | q75_H75 | 1496 | 0.06 | 0.44 | 127 | 131 | 4.9 |
| M7 | nyam | rem_own_k0.75 | 1496 | 0.69 | 0.42 | 30 | -36 | 27.3 |
| O7 | nyam | q50_H75 | 452 | 0.58 | 0.32 | 205 | 91 | 20.5 |
| O7 | nyam | q60_H75 | 452 | 0.37 | 0.31 | 156 | 118 | 16.9 |
| O7 | nyam | q75_H75 | 452 | 0.08 | 0.20 | -192 | -145 | 9.5 |
| O7 | nyam | rem_own_k0.75 | 452 | 0.31 | 0.30 | 120 | 82 | 20.6 |
| P7 | asia | q50_H75 | 2161 | 0.29 | 0.46 | 391 | 341 | 10.2 |
| P7 | asia | q60_H75 | 2161 | 0.16 | 0.48 | 487 | 484 | 9.3 |
| P7 | asia | q75_H75 | 2161 | 0.02 | 0.55 | 1227 | 969 | 5.7 |
| P7 | asia | rem_own_k0.75 | 2161 | 0.70 | 0.44 | 447 | 130 | 26.6 |
| P7 | london | q50_H75 | 1537 | 0.62 | 0.38 | 74 | 27 | 10.0 |
| P7 | london | q60_H75 | 1537 | 0.41 | 0.38 | 67 | 36 | 7.8 |
| P7 | london | q75_H75 | 1537 | 0.15 | 0.41 | 124 | 59 | 5.3 |
| P7 | london | rem_own_k0.75 | 1537 | 0.72 | 0.37 | -19 | -13 | 23.8 |
| P7 | nyam | q50_H75 | 1050 | 0.72 | 0.38 | 38 | 150 | 13.2 |
| P7 | nyam | q60_H75 | 1050 | 0.48 | 0.37 | -7 | 28 | 10.9 |
| P7 | nyam | q75_H75 | 1050 | 0.15 | 0.33 | -88 | -96 | 13.3 |
| P7 | nyam | rem_own_k0.75 | 1050 | 0.71 | 0.37 | -43 | 67 | 33.2 |
| U7 | asia | q50_H75 | 686 | 0.28 | 0.54 | 412 | 320 | 10.4 |
| U7 | asia | q60_H75 | 686 | 0.15 | 0.50 | 322 | 270 | 8.0 |
| U7 | asia | q75_H75 | 686 | 0.03 | 0.47 | -260 | -383 | 6.8 |
| U7 | asia | rem_own_k0.75 | 686 | 0.74 | 0.53 | 375 | 4 | 30.5 |
| U7 | london | q50_H75 | 645 | 0.27 | 0.46 | -102 | -183 | 8.7 |
| U7 | london | q60_H75 | 645 | 0.13 | 0.46 | -173 | -182 | 7.8 |
| U7 | london | q75_H75 | 645 | 0.03 | 0.50 | -396 | -466 | 5.4 |
| U7 | london | rem_own_k0.75 | 645 | 0.68 | 0.51 | 166 | 14 | 24.5 |

### Exact cap cells (global: all books at once; L3M, L6M when promoted; delta vs JN05W2)
| cell | L3M | L6M | HOLD | d mean/wk at $4.84 L3M |
|---|---|---|---|---|
| quantile 50 cap, horizon = 75th-percentile holding time | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | +1452 (lots +9/wk) |
| quantile 60 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 75 cap, horizon = 75th-percentile holding time | +177 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 101%, w2l 0 | n/a | n/a | +176 (lots +0/wk) |
| quantile 90 cap, horizon = 75th-percentile holding time | pending | | | |
| quantile 60 cap, horizon = median holding time | -1554 $/wk, DD +2.5%, ww +1445, stops 10.42(10.35), b5 89%, w2l 1 | n/a | n/a | -1658 (lots +29/wk) |
| quantile 75 cap, horizon = median holding time | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=0.5 | -8393 $/wk, DD +2.1%, ww +5889, stops 7.76(10.35), b5 57%, w2l 3 | n/a | n/a | -8805 (lots +113/wk) |
| remaining-range cap, forecast own 20-session mean, k=0.75 | pending | | | |
| remaining-range cap, forecast own 20-session mean, k=1.0 | -6226 $/wk, DD +27.0%, ww +12290, stops 8.98(10.35), b5 66%, w2l 2 | n/a | n/a | -6458 (lots +63/wk) |
| remaining-range cap, forecast own 20-session mean, k=1.25 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.5 | -10795 $/wk, DD +40.3%, ww +11430, stops 7.00(10.35), b5 51%, w2l 4 | n/a | n/a | -11257 (lots +126/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=0.75 | pending | | | |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.0 | -7259 $/wk, DD +39.4%, ww +17319, stops 7.76(10.35), b5 65%, w2l 2 | n/a | n/a | -7570 (lots +85/wk) |
| remaining-range cap, forecast T-RANGE2 HAR, k=1.25 | pending | | | |
| EV-best target, bounded by the book target | -14326 $/wk, DD -25.6%, ww -15613, stops 8.45(10.35), b5 46%, w2l 3 | n/a | n/a | -14639 (lots +86/wk) |
| EV-best target, unbounded | pending | | | |
| extension m=1.0 | -110 $/wk, DD -53.4%, ww -2988, stops 11.72(10.35), b5 124%, w2l 2 | n/a | n/a | -18 (lots -25/wk) |
| extension m=1.5 | pending | | | |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts skipped | +1443 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | n/a | n/a | +1410 (lots +9/wk) |
| quantile 50 cap, horizon = 75th-percentile holding time, caps < 30 pts at half size | pending | | | |
| PLANTED-EDGE CHECK (look-ahead oracle 0.9 x realised MFE, not a result) | +85531 $/wk, DD +67.0%, ww +64263, stops 6.54(10.35), b5 259%, w2l 0 | n/a | n/a | +85219 (lots +85/wk) |
| PLANTED-EDGE CHECK (oracle 0.6 x realised MFE, not a result) | pending | | | |
| PLACEBO pl11: quantile 50 cap, horizon = 75th-percentile holding time | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 | n/a | -125 (lots +1/wk) |
| PLACEBO pl23: quantile 50 cap, horizon = 75th-percentile holding time | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 | n/a | -871 (lots +3/wk) |
| PLACEBO pl37: quantile 50 cap, horizon = 75th-percentile holding time | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 | n/a | -612 (lots +2/wk) |
| PLACEBO plR1: quantile 50 cap, horizon = 75th-percentile holding time | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 | n/a | -670 (lots +4/wk) |

### The one candidate: forecast-quantile-50 cap, horizon = 75th-percentile holding time (L3M mean-only so far): all windows, W44 removed, placebos
| window | scope all | W44 removed |
|---|---|---|
| L3M | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 | +1486 $/wk, DD -0.5%, ww -240, stops 10.12(10.35), b5 101%, w2l 0 |
| L6M | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 | +721 $/wk, DD -0.5%, ww -240, stops 10.80(10.99), b5 101%, w2l 0 |
| HOLD | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 | -807 $/wk, DD -5.3%, ww -1223, stops 10.59(10.66), b5 98%, w2l 2 |
| MID | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 | -1977 $/wk, DD +4.2%, ww +2535, stops 10.63(10.88), b5 103%, w2l 1 |
| PREUW | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 | -2044 $/wk, DD +7.8%, ww +14602, stops 9.44(9.31), b5 100%, w2l 3 |
Placebos (same cap, forecast features taken n sessions earlier at the same clock / a random earlier session), L3M then L6M when run:
| placebo | L3M | L6M |
|---|---|---|
| pl11 | -120 $/wk, DD +7.9%, ww +4202, stops 10.20(10.35), b5 98%, w2l 0 | -1209 $/wk, DD +7.9%, ww +4202, stops 10.80(10.99), b5 91%, w2l 0 |
| pl23 | -859 $/wk, DD -5.3%, ww -2539, stops 10.12(10.35), b5 101%, w2l 0 | -1357 $/wk, DD -5.3%, ww -2539, stops 10.92(10.99), b5 98%, w2l 0 |
| pl37 | -606 $/wk, DD +9.1%, ww +4306, stops 10.35(10.35), b5 99%, w2l 0 | -2237 $/wk, DD +9.1%, ww +4306, stops 10.99(10.99), b5 95%, w2l 0 |
| plR1 | -657 $/wk, DD -5.3%, ww -2771, stops 10.04(10.35), b5 99%, w2l 0 | -1688 $/wk, DD -5.3%, ww -2771, stops 10.77(10.99), b5 99%, w2l 0 |

### Per book x session exact cap cells (clean: one book in one session)
| slice | cap | L3M | May-Jul |
|---|---|---|---|
| A7 asia | quantile 50 cap, horizon = 75th-percentile holding time | -17 (live -30; $4.84 -17) DD +0.0% ww +0 stops 4.03(4.03) | n/a |

### FOR THE LIVE BUILD (what D7 computes at the signal second)
From its own 1-minute bars: last 15/30/60/120-minute range and realised vol, same-offset range over the previous 20 sessions (median), session ranges of the last 5/20 sessions, range so far, the entry position in the session range (favourable-side room), elapsed fraction of the session, ln of the book-session horizon; a small coefficient table per session (15 weights, mean, sd, intercept, four residual quantile offsets) refit every 14 days and shipped as a static file. Cap = min(60, price x exp(prediction + quantile offset) - 2); orders: the target limit is placed at the capped price. The remaining-range version needs the HAR session forecast (T-RANGE2 file) or D7 computes its own 20-session mean. No intraday feed from the box.


## Per book and session, clean, and the assembled stack
**STATUS (plain, not a PASS; B1 in progress, no "nothing passes" verdict is allowed until it is done): single-book single-session cells scored in L3M for 15 of 14 slices; slice picks so far: {}.**

Method (user order PART B, 2026-11-15): each cell = the Dial 10 hook restricted to ONE book in ONE session (every other book/session unchanged at JN05W2), exact engine, all layers ON, live caps. Dollars are BASE lots; the x1.75 live figure sits beside each headline (live); the $4.84 figure reprices every contract at the FEES.md $4.84 RT (engine raw $1.18). Compared on the same book x session slice of JN05W2 (day locks/caps still interact across books, which is why the cells are run for real and not sliced from the global run). B1a settings per slice: direction both / narrow-only / wide-only x gearing 0.5 / 1.0 at the 75th-percentile horizon, plus narrow/wide g1.0 at the median horizon; "fixed" = JN05W2 itself. Walk-forward: the pick for each slice is made on 2026-05..07 only (older than L3M); L3M (2026-08..10) is then out-of-sample. B1b (around each pick): lots cap 1.5/3, lots follow half the change, dead band 0/20%, target ratio 0.8/1.2, lever stop-only (sl: stop W, lots inverse, target in the same points) / target-only (tg) / size-only (sz: bracket fixed, lots follow the forecast), noise floor k = 3/4/5 x recent 5-minute ATR (bracket never narrower), clips 25..120 / 20..150.

### B1 table: per slice, every cell (L3M, delta vs JN05W2 same slice; May-Jul = the selection window)
| slice | setting | May-Jul (selection) | L3M (out of sample) | L6M |
|---|---|---|---|---|
| A7 asia | both/g1.0/H75 | -374 (live -654; $4.84 -370) DD -10.9% ww -261 stops 2.97(3.88) | +47 (live +83; $4.84 +40) DD +25.6% ww +1495 stops 5.55(4.03) | -163 (live -286; $4.84 -165) DD -29.2% ww +1253 stops 4.26(3.96) |
| A7 asia | narrow/g1.0/H75 | -419 (live -733; $4.84 -423) DD -0.6% ww -175 stops 4.49(3.88) | -18 (live -32; $4.84 -26) DD +17.7% ww +722 stops 5.63(4.03) | -219 (live -383; $4.84 -224) DD -19.1% ww +722 stops 5.06(3.96) |
| A7 asia | both/g0.5/H75 | -556 (live -973; $4.84 -553) DD -9.2% ww +72 stops 3.50(3.88) | -192 (live -336; $4.84 -195) DD +10.1% ww +412 stops 5.10(4.03) | -374 (live -654; $4.84 -374) DD -36.6% ww +412 stops 4.30(3.96) |
| A7 asia | narrow/g0.5/H75 | -350 (live -612; $4.84 -352) DD +0.0% ww +0 stops 4.34(3.88) | -186 (live -325; $4.84 -189) DD +10.0% ww +552 stops 5.10(4.03) | -268 (live -469; $4.84 -270) DD -15.8% ww +552 stops 4.72(3.96) |
| A7 asia | wide/g1.0/H75 | +19 (live +33; $4.84 +26) DD -10.9% ww +283 stops 2.51(3.88) | -15 (live -26; $4.84 -14) DD +2.4% ww -426 stops 3.96(4.03) | +2 (live +3; $4.84 +6) DD -13.6% ww -426 stops 3.23(3.96) |
| A7 asia | wide/g0.5/H75 | n/a | -1 (live -1; $4.84 -1) DD +1.4% ww -140 stops 4.03(4.03) | n/a |
| A7 asia | wide/g1.0/H50 | n/a | -48 (live -85; $4.84 -48) DD -3.0% ww -426 stops 3.88(4.03) | n/a |
| A7 asia | narrow/g1.0/H50 | n/a | -159 (live -279; $4.84 -171) DD -8.3% ww +877 stops 5.93(4.03) | n/a |
| H7 asia | wide/g0.5/H75 | n/a | +123 (live +215; $4.84 +123) DD +0.0% ww +0 stops 0.23(0.23) | n/a |
| H7 asia | wide/g1.0/H75 | n/a | -67 (live -118; $4.84 -67) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | wide/g1.0/H50 | n/a | -312 (live -546; $4.84 -312) DD +0.0% ww +0 stops 0.30(0.23) | n/a |
| H7 asia | both/g0.0/H50 | -1814 (live -3175; $4.84 -1811) DD +9.9% ww +1967 stops 0.68(0.61) | -3 (live -5; $4.84 +3) DD -4.1% ww +0 stops 0.46(0.23) | -908 (live -1590; $4.84 -904) DD +9.9% ww +1967 stops 0.57(0.42) |
| H7 asia | both/g0.0/H50 | -1623 (live -2840; $4.84 -1619) DD +11.0% ww +3643 stops 0.46(0.61) | -972 (live -1701; $4.84 -967) DD -31.5% ww +0 stops 0.46(0.23) | -1298 (live -2271; $4.84 -1293) DD +11.0% ww +3643 stops 0.46(0.42) |
| H7 asia | both/g1.0/H75 | +1123 (live +1965; $4.84 +1129) DD +6.5% ww +1483 stops 0.53(0.61) | +177 (live +309; $4.84 +163) DD -33.6% ww -1228 stops 0.61(0.23) | +650 (live +1137; $4.84 +646) DD +6.5% ww +1483 stops 0.57(0.42) |
| H7 asia | narrow/g1.0/H75 | n/a | +244 (live +427; $4.84 +230) DD -33.6% ww -1228 stops 0.53(0.23) | n/a |
| H7 asia | both/g0.5/H75 | n/a | -574 (live -1004; $4.84 -580) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g0.5/H75 | n/a | -697 (live -1219; $4.84 -703) DD -92.7% ww -2409 stops 0.53(0.23) | n/a |
| H7 asia | narrow/g1.0/H50 | n/a | -355 (live -621; $4.84 -372) DD -120.5% ww -2166 stops 0.53(0.23) | n/a |
| H7 nyam | narrow/g1.0/H50 | n/a | +252 (live +441; $4.84 +252) DD +60.4% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | both/g1.0/H75 | n/a | +281 (live +491; $4.84 +280) DD +57.7% ww +480 stops 0.30(0.38) | n/a |
| H7 nyam | narrow/g1.0/H75 | -187 (live -328; $4.84 -188) DD -4.0% ww +0 stops 0.53(0.46) | +258 (live +452; $4.84 +258) DD +57.7% ww +480 stops 0.30(0.38) | +35 (live +62; $4.84 +35) DD +24.1% ww +480 stops 0.42(0.42) |
| H7 nyam | both/g0.0/H50 | -58 (live -102; $4.84 -58) DD +9.4% ww +0 stops 0.46(0.46) | +221 (live +387; $4.84 +221) DD +54.7% ww +195 stops 0.15(0.38) | +82 (live +143; $4.84 +81) DD +33.9% ww +195 stops 0.30(0.42) |
| H7 nyam | both/g0.0/H50 | -8 (live -14; $4.84 -8) DD +9.4% ww +0 stops 0.46(0.46) | +202 (live +353; $4.84 +202) DD +54.7% ww +195 stops 0.15(0.38) | +97 (live +170; $4.84 +97) DD +33.9% ww +195 stops 0.30(0.42) |
| H7 nyam | both/g0.5/H75 | +103 (live +180; $4.84 +103) DD +29.2% ww -83 stops 0.46(0.46) | +87 (live +153; $4.84 +87) DD +2.2% ww +195 stops 0.38(0.38) | +95 (live +167; $4.84 +95) DD +2.2% ww +195 stops 0.42(0.42) |
| H7 nyam | narrow/g0.5/H75 | n/a | +77 (live +134; $4.84 +77) DD +2.2% ww +195 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g0.5/H75 | n/a | +11 (live +19; $4.84 +11) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H75 | n/a | +22 (live +39; $4.84 +22) DD +0.0% ww +0 stops 0.38(0.38) | n/a |
| H7 nyam | wide/g1.0/H50 | n/a | +30 (live +53; $4.84 +30) DD +0.0% ww +0 stops 0.30(0.38) | n/a |
| K7 asia | wide/g1.0/H75 | n/a | +297 (live +520; $4.84 +298) DD +0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | wide/g0.5/H75 | n/a | -54 (live -94; $4.84 -54) DD -0.7% ww -404 stops 0.00(0.00) | n/a |
| K7 asia | narrow/g0.5/H75 | n/a | +1877 (live +3285; $4.84 +1855) DD -19.6% ww -2412 stops 0.00(0.00) | n/a |
| K7 asia | both/g0.5/H75 | n/a | +1823 (live +3191; $4.84 +1801) DD -28.8% ww -3232 stops 0.00(0.00) | n/a |
| K7 asia | wide/g1.0/H50 | n/a | -401 (live -702; $4.84 -400) DD -35.9% ww +0 stops 0.00(0.00) | n/a |
| K7 asia | both/g1.0/H75 | n/a | +1292 (live +2261; $4.84 +1220) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H75 | n/a | +912 (live +1595; $4.84 +838) DD -46.3% ww -1012 stops 0.15(0.00) | n/a |
| K7 asia | narrow/g1.0/H50 | n/a | +355 (live +621; $4.84 +268) DD -86.2% ww -5644 stops 0.00(0.00) | n/a |
| K7 london | both/g0.5/H75 | n/a | -9 (live -15; $4.84 -14) DD +8.7% ww +4326 stops 0.23(0.30) | n/a |
| K7 london | wide/g0.5/H75 | n/a | +27 (live +48; $4.84 +29) DD +0.5% ww +0 stops 0.30(0.30) | n/a |
| K7 london | wide/g1.0/H50 | n/a | +431 (live +755; $4.84 +433) DD -3.3% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g0.5/H75 | n/a | -123 (live -215; $4.84 -130) DD -4.2% ww +4733 stops 0.23(0.30) | n/a |
| K7 london | wide/g1.0/H75 | n/a | +157 (live +274; $4.84 +160) DD -4.8% ww +0 stops 0.30(0.30) | n/a |
| K7 london | narrow/g1.0/H50 | n/a | -182 (live -319; $4.84 -204) DD -13.7% ww +3097 stops 0.23(0.30) | n/a |
| K7 london | both/g1.0/H75 | n/a | +481 (live +841; $4.84 +462) DD -25.5% ww +4257 stops 0.38(0.30) | n/a |
| K7 london | narrow/g1.0/H75 | n/a | -31 (live -55; $4.84 -55) DD -42.3% ww +4122 stops 0.38(0.30) | n/a |
| K7 nyam | both/g0.0/H50 | -645 (live -1129; $4.84 -647) DD -55.9% ww -1158 stops 0.08(0.08) | +805 (live +1408; $4.84 +793) DD +62.7% ww +1729 stops 0.00(0.00) | +80 (live +139; $4.84 +73) DD +44.5% ww +1153 stops 0.04(0.04) |
| K7 nyam | both/g0.0/H50 | -488 (live -855; $4.84 -488) DD -38.7% ww -514 stops 0.08(0.08) | +1078 (live +1886; $4.84 +1069) DD +53.9% ww +1605 stops 0.00(0.00) | +295 (live +516; $4.84 +290) DD +50.6% ww +1605 stops 0.04(0.04) |
| K7 nyam | narrow/g1.0/H50 | n/a | +769 (live +1345; $4.84 +761) DD +51.0% ww +2185 stops 0.00(0.00) | n/a |
| K7 nyam | both/g1.0/H75 | n/a | +1160 (live +2030; $4.84 +1153) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g1.0/H75 | n/a | +984 (live +1722; $4.84 +977) DD +49.1% ww +2130 stops 0.00(0.00) | n/a |
| K7 nyam | narrow/g0.5/H75 | n/a | +668 (live +1170; $4.84 +667) DD +40.3% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | both/g0.5/H75 | n/a | +806 (live +1410; $4.84 +805) DD +39.5% ww +1383 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H75 | n/a | +176 (live +308; $4.84 +176) DD -0.0% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g1.0/H50 | n/a | +252 (live +441; $4.84 +253) DD -0.3% ww +0 stops 0.00(0.00) | n/a |
| K7 nyam | wide/g0.5/H75 | n/a | +137 (live +241; $4.84 +137) DD -0.8% ww +0 stops 0.00(0.00) | n/a |
| K7 nypm | wide/g1.0/H50 | n/a | +442 (live +773; $4.84 +442) DD +17.3% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | wide/g1.0/H75 | n/a | +70 (live +122; $4.84 +70) DD +13.1% ww -90 stops 0.00(0.08) | n/a |
| K7 nypm | both/g1.0/H75 | n/a | -184 (live -322; $4.84 -197) DD +9.8% ww +1145 stops 0.15(0.08) | n/a |
| K7 nypm | wide/g0.5/H75 | n/a | -4 (live -8; $4.84 -4) DD -1.5% ww -38 stops 0.00(0.08) | n/a |
| K7 nypm | narrow/g1.0/H50 | n/a | +48 (live +84; $4.84 +32) DD -1.9% ww +105 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g1.0/H75 | n/a | -254 (live -445; $4.84 -267) DD -3.3% ww +990 stops 0.23(0.08) | n/a |
| K7 nypm | narrow/g0.5/H75 | n/a | -266 (live -465; $4.84 -269) DD -26.7% ww +140 stops 0.08(0.08) | n/a |
| K7 nypm | both/g0.5/H75 | n/a | -270 (live -473; $4.84 -274) DD -27.3% ww +102 stops 0.00(0.08) | n/a |
| M7 london | wide/g1.0/H75 | n/a | +1614 (live +2824; $4.84 +1616) DD +4.9% ww +1190 stops 0.53(0.91) | n/a |
| M7 london | wide/g0.5/H75 | n/a | +688 (live +1204; $4.84 +689) DD +4.4% ww +1400 stops 0.84(0.91) | n/a |
| M7 london | wide/g1.0/H50 | n/a | +538 (live +942; $4.84 +540) DD -1.3% ww -80 stops 0.84(0.91) | n/a |
| M7 london | both/g0.5/H75 | n/a | +1147 (live +2008; $4.84 +1139) DD -8.1% ww +130 stops 1.07(0.91) | n/a |
| M7 london | narrow/g0.5/H75 | n/a | +417 (live +730; $4.84 +408) DD -10.9% ww -1075 stops 1.14(0.91) | n/a |
| M7 london | narrow/g1.0/H50 | n/a | +476 (live +833; $4.84 +446) DD -19.9% ww +1144 stops 1.45(0.91) | n/a |
| M7 london | narrow/g1.0/H75 | n/a | -366 (live -640; $4.84 -390) DD -20.4% ww +80 stops 1.29(0.91) | n/a |
| M7 london | both/g1.0/H75 | n/a | +1142 (live +1999; $4.84 +1121) DD -23.2% ww -729 stops 0.91(0.91) | n/a |
| M7 nyam | narrow/g1.0/H50 | n/a | +439 (live +769; $4.84 +424) DD +26.0% ww -222 stops 0.38(0.23) | n/a |
| M7 nyam | both/g0.5/H75 | n/a | +79 (live +138; $4.84 +75) DD +0.8% ww +194 stops 0.30(0.23) | n/a |
| M7 nyam | narrow/g0.5/H75 | n/a | +73 (live +127; $4.84 +69) DD +0.8% ww +194 stops 0.38(0.23) | n/a |
| M7 nyam | wide/g0.5/H75 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H75 | n/a | +16 (live +28; $4.84 +16) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | wide/g1.0/H50 | n/a | +6 (live +11; $4.84 +6) DD +0.0% ww +0 stops 0.15(0.23) | n/a |
| M7 nyam | both/g1.0/H75 | n/a | +419 (live +733; $4.84 +405) DD -6.8% ww -991 stops 0.46(0.23) | n/a |
| M7 nyam | narrow/g1.0/H75 | n/a | +402 (live +704; $4.84 +388) DD -6.8% ww -991 stops 0.53(0.23) | n/a |
| M7 nyam | both/g0.0/H50 | -130 (live -227; $4.84 -131) DD -16.3% ww -1329 stops 0.61(0.61) | +102 (live +179; $4.84 +99) DD -11.5% ww +0 stops 0.23(0.23) | -14 (live -24; $4.84 -16) DD -19.5% ww -1329 stops 0.42(0.42) |
| P7 asia | both/g0.0/H50 | -5189 (live -9081; $4.84 -4987) DD +44.9% ww +11844 stops 0.00(0.00) | -703 (live -1230; $4.84 -620) DD +51.2% ww +20259 stops 0.08(0.15) | -2946 (live -5156; $4.84 -2804) DD +51.2% ww +17717 stops 0.04(0.08) |
| P7 asia | both/g0.0/H50 | -6897 (live -12069; $4.84 -6699) DD +42.2% ww +13069 stops 0.00(0.00) | -322 (live -564; $4.84 -245) DD +51.2% ww +19309 stops 0.08(0.15) | -3609 (live -6317; $4.84 -3472) DD +51.2% ww +18942 stops 0.04(0.08) |
| P7 asia | narrow/g1.0/H50 | n/a | -3918 (live -6857; $4.84 -4186) DD -0.4% ww -4286 stops 0.46(0.15) | n/a |
| P7 asia | both/g0.5/H75 | n/a | -5946 (live -10406; $4.84 -6044) DD -1.0% ww +6944 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g0.5/H75 | n/a | -5762 (live -10084; $4.84 -5860) DD -1.0% ww +9022 stops 0.15(0.15) | n/a |
| P7 asia | wide/g0.5/H75 | n/a | -184 (live -322; $4.84 -183) DD -4.9% ww -2079 stops 0.15(0.15) | n/a |
| P7 asia | narrow/g1.0/H75 | n/a | -2696 (live -4718; $4.84 -2882) DD -7.8% ww -10346 stops 0.53(0.15) | n/a |
| P7 asia | wide/g1.0/H50 | n/a | -816 (live -1428; $4.84 -812) DD -22.6% ww -9033 stops 0.15(0.15) | n/a |
| P7 asia | wide/g1.0/H75 | n/a | -491 (live -858; $4.84 -490) DD -25.2% ww -10331 stops 0.15(0.15) | n/a |
| P7 asia | both/g1.0/H75 | n/a | -3315 (live -5802; $4.84 -3501) DD -36.1% ww -13164 stops 0.53(0.15) | n/a |
| P7 london | both/g0.5/H75 | n/a | +894 (live +1565; $4.84 +886) DD +29.6% ww -1633 stops 0.08(0.08) | n/a |
| P7 london | narrow/g0.5/H75 | n/a | +386 (live +675; $4.84 +375) DD +28.5% ww -1328 stops 0.08(0.08) | n/a |
| P7 london | narrow/g1.0/H50 | n/a | +927 (live +1622; $4.84 +895) DD +19.7% ww -3009 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H75 | n/a | -142 (live -249; $4.84 -138) DD +2.7% ww -458 stops 0.08(0.08) | n/a |
| P7 london | wide/g1.0/H50 | n/a | +265 (live +464; $4.84 +266) DD +1.1% ww +0 stops 0.08(0.08) | n/a |
| P7 london | wide/g0.5/H75 | n/a | +385 (live +674; $4.84 +387) DD -1.9% ww -238 stops 0.08(0.08) | n/a |
| P7 london | both/g1.0/H75 | n/a | +1179 (live +2064; $4.84 +1145) DD -9.8% ww -5408 stops 0.15(0.08) | n/a |
| P7 london | narrow/g1.0/H75 | n/a | +1322 (live +2313; $4.84 +1282) DD -14.4% ww -5203 stops 0.15(0.08) | n/a |
| P7 nyam | both/g0.0/H50 | -1333 (live -2333; $4.84 -1305) DD +88.2% ww +6983 stops 0.00(0.08) | +198 (live +346; $4.84 +220) DD +55.7% ww +1594 stops 0.15(0.38) | -568 (live -994; $4.84 -542) DD +59.1% ww +4666 stops 0.08(0.23) |
| P7 nyam | both/g1.0/H75 | n/a | +697 (live +1220; $4.84 +685) DD +51.3% ww +354 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g1.0/H75 | n/a | +543 (live +951; $4.84 +529) DD +45.9% ww +324 stops 0.30(0.38) | n/a |
| P7 nyam | both/g0.5/H75 | n/a | +105 (live +184; $4.84 +99) DD +36.7% ww +238 stops 0.30(0.38) | n/a |
| P7 nyam | narrow/g0.5/H75 | n/a | -13 (live -23; $4.84 -20) DD +36.4% ww +262 stops 0.30(0.38) | n/a |
| P7 nyam | wide/g0.5/H75 | n/a | +118 (live +207; $4.84 +119) DD +0.3% ww -25 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H75 | n/a | +16 (live +27; $4.84 +17) DD -7.5% ww -105 stops 0.38(0.38) | n/a |
| P7 nyam | wide/g1.0/H50 | n/a | -544 (live -952; $4.84 -543) DD -47.7% ww -3348 stops 0.38(0.38) | n/a |
| U7 asia | narrow/g1.0/H50 | n/a | +1222 (live +2139; $4.84 +1201) DD +15.6% ww -265 stops 1.90(1.83) | n/a |
| U7 asia | both/g1.0/H75 | n/a | +71 (live +124; $4.84 +56) DD +8.3% ww -1836 stops 1.98(1.83) | n/a |
| U7 asia | narrow/g1.0/H75 | n/a | +502 (live +879; $4.84 +487) DD +8.3% ww +983 stops 1.98(1.83) | n/a |
| U7 asia | both/g0.5/H75 | n/a | -800 (live -1399; $4.84 -808) DD +6.6% ww -2883 stops 2.05(1.83) | n/a |
| U7 asia | narrow/g0.5/H75 | n/a | -162 (live -284; $4.84 -170) DD +6.6% ww +57 stops 2.05(1.83) | n/a |
| U7 asia | wide/g0.5/H75 | n/a | -637 (live -1115; $4.84 -637) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H75 | n/a | -431 (live -755; $4.84 -431) DD +0.0% ww -1836 stops 1.83(1.83) | n/a |
| U7 asia | wide/g1.0/H50 | n/a | -648 (live -1134; $4.84 -648) DD +0.0% ww -2883 stops 1.83(1.83) | n/a |
| U7 london | narrow/g0.5/H75 | n/a | +393 (live +687; $4.84 +392) DD +17.2% ww +1796 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H75 | n/a | +246 (live +431; $4.84 +243) DD +3.1% ww -1185 stops 1.45(1.45) | n/a |
| U7 london | narrow/g1.0/H50 | n/a | -41 (live -72; $4.84 -48) DD -9.9% ww -1991 stops 1.52(1.45) | n/a |
| U7 london | both/g0.5/H75 | n/a | -891 (live -1560; $4.84 -890) DD -25.4% ww -3538 stops 1.52(1.45) | n/a |
| U7 london | wide/g1.0/H50 | n/a | -839 (live -1468; $4.84 -837) DD -33.9% ww -4122 stops 1.37(1.45) | n/a |
| U7 london | wide/g0.5/H75 | n/a | -1284 (live -2247; $4.84 -1282) DD -44.3% ww -6280 stops 1.52(1.45) | n/a |
| U7 london | both/g1.0/H75 | n/a | -1728 (live -3025; $4.84 -1729) DD -105.5% ww -7540 stops 1.60(1.45) | n/a |
| U7 london | wide/g1.0/H75 | n/a | -1975 (live -3455; $4.84 -1972) DD -109.8% ww -6355 stops 1.60(1.45) | n/a |

### Summary per slice: pick made on May-Jul, result on L3M
| slice | pick | L3M result of the pick | verdict |
|---|---|---|---|
| A7 asia | pending | | |
| H7 asia | pending | | |
| H7 nyam | pending | | |
| K7 asia | pending | | |
| K7 london | pending | | |
| K7 nyam | pending | | |
| K7 nypm | pending | | |
| M7 london | pending | | |
| M7 nyam | pending | | |
| P7 asia | pending | | |
| P7 london | pending | | |
| P7 nyam | pending | | |
| U7 asia | pending | | |
| U7 london | pending | | |

### B2: why the global version adds full stops (narrow-only/both g1.0 H75 cell, L3M, trade tables)
Reference JN05W2 L3M (no O7): 1855 trades, stop rate 0.071, 132 stops (13 weeks).

**M1_75_g10_c1_d10_c20_tb_B**: 2038 trades (+183 vs JN05W2), stops 173 (+41), stop rate 0.085 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 437 | 0.103 | 3.05 | 94 |
| (40, 50] | 721 | 0.074 | 2.36 | 271 |
| (50, 55] | 232 | 0.099 | 1.97 | 169 |
| (55, 60] | 435 | 0.076 | 1.87 | 76 |
| (60, 70] | 75 | 0.120 | 2.01 | -385 |
| (70, 80] | 62 | 0.048 | 1.68 | -284 |
| (80, 101] | 76 | 0.092 | 1.13 | -591 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1543 | 0.069 | 2.21 | 54 |
| (3.0, 4.0] | 294 | 0.116 | 2.29 | 239 |
| (4.0, 5.0] | 74 | 0.108 | 2.31 | 364 |
| (5.0, 6.0] | 6 | 0.167 | 2.50 | 172 |
| (6.0, 8.0] | 4 | 0.000 | 1.00 | -119 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1068 | 0.096 | 1.00 | 4 |
| (1, 2] | 385 | 0.078 | 2.00 | 115 |
| (2, 3] | 215 | 0.093 | 3.00 | 23 |
| (3, 5] | 195 | 0.062 | 4.46 | 256 |
| (5, 8] | 138 | 0.065 | 6.70 | 690 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

**M1_75_g10_c1_d10_c20_tb_N**: 2072 trades (+217 vs JN05W2), stops 178 (+46), stop rate 0.086 vs 0.071. The stop count rises both because there are more trades (narrow brackets resolve faster, the book re-enters) and because the per-trade stop rate in the narrowest buckets is higher.

| width bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 40] | 449 | 0.105 | 3.02 | 97 |
| (40, 50] | 725 | 0.073 | 2.35 | 272 |
| (50, 55] | 236 | 0.102 | 1.97 | 150 |
| (55, 60] | 662 | 0.082 | 1.82 | -29 |

| W/ATR5 bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0.0, 3.0] | 1644 | 0.072 | 2.18 | 50 |
| (3.0, 4.0] | 264 | 0.121 | 2.38 | 348 |
| (4.0, 5.0] | 44 | 0.091 | 3.11 | 1063 |
| (5.0, 6.0] | 3 | 0.000 | 3.33 | 68 |

| lots bucket | trades | stop rate | mean lots | net $/trade |
|---|---|---|---|---|
| (0, 1] | 1073 | 0.095 | 1.00 | 8 |
| (1, 2] | 413 | 0.085 | 2.00 | 117 |
| (2, 3] | 197 | 0.081 | 3.00 | 213 |
| (3, 5] | 217 | 0.074 | 4.43 | 196 |
| (5, 8] | 135 | 0.067 | 6.74 | 714 |
| (8, 14] | 37 | 0.000 | 10.00 | 508 |

Reading of the W/ATR5 table: ATR5 = mean range of the last 14 five-minute buckets in points; a bracket 3x ATR5 or less is within ordinary 5-minute noise. The noise-floor cells (floor 3/4/5 x ATR5, narrowing only) are listed in B3.


### B3: levers (stop-only / target-only / both / size-only) and noise floor, per slice
| slice | cell | L3M | May-Jul |
|---|---|---|---|

### B4: assembled stack (each slice at its own walk-forward pick, run together)
(not run yet: starts when every slice has a pick)


## Dial 10: trade-horizon bracket
**VERDICT (plain, not a PASS): 387 of 597 registered cells scored through L3M, 208 through L6M, 91 through HOLD; 22 (cell,scope) leads pass the tolerant gate in every scored window (5 at scope all) - before placebo; this is the GLOBAL one-setting-for-all-books family only, the per-book per-session test (B1) is in the section above and still running. Best L3M cell inside the mean gate: M1_50_g00_c1_d10_c20_tb_B_tcoracle0.9T75 (DD +67.0%, +85531 $/wk).**

Identity: TL3_D10_M1_50_g00_c1_d10_c20_tb_B 202610 (hook active, g=0): 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL. Prereg autopilot/DIAL10_PREREG.md (sha line in DECISIONS.md 2026-11-14T22:33Z). Order: ADDENDUM_DIAL10_20261114.md. Code code/th_dial10 (d10_core.py features, d10_coef.py coefficient table, d10_hooks.py hook, d10_driver.py). Bulk /mnt/l2/l2vast/_dial10. Tag D10 (quota 3).
**LOT BASIS**: engine dollars are BASE lots (live user lots x1.75, live caps = engine caps x1.75); the engine charges its raw $1.18/contract RT with the engine fills, FEES.md says $4.84 RT. Every $ column is raw $1.18 unless it says $4.84; the $4.84 columns reprice delta mean/wk as net - lots x 3.66 per trade for cell and JN05W2 alike (no rerun) and show the lot change per week.
Definition: at the signal second the hook computes EM = expected NQ range over the book+session holding horizon H (H50 = median, H75 = 75th pct of the book+session holding time, causal) from own 1-min bars (last 15/30/60/120 min range and realised vol, same-clock normal level of the previous 20 sessions, own session level, range used so far, elapsed fraction) with a walk-forward ridge (coefficients refit every 14 days; M2 adds the T-RANGE2 session forecast and calendar flags). r = EM / ref, ref = trailing-120-day median of the fitted EM for that book+session (so k = stop/ref is fitted on earlier data and tracks price/vol level). W = clip(stop x r^g, lo, hi) with dead band |r-1|<=db => W=stop. Version A: target, state-cut arm and ctxcut arms, K7 flat cut, TH-L2 LOSS_MIN and TIGHT_TRAIL, MINDIP add dip, BookLock R from actual lots and the profit-side 30-point tighten threshold all scale with W/stop. Lots: c = constant dollars at the stop (lots x stop/W, increase capped x1.5/x2/x3, wide brackets reduce lots), h = lots follow half the change in W. O7 fixed. Cell name = TL3_D10_<forecast>_<H tag>_g<10g>_c<clip 1=30..100 2=25..120 3=20..150>_d<db %>_<lots><cap x10>_t<target ratio: b book own, 08 10 12 15 x W, m moving>_<half B both N narrow-only W wide-only>.
**The hard-coded 30-point profit-side tighten threshold (sim.py manage_th_l2, `unreal < 30.0`)** is fixed through the hook: while the old-panel profit tighten is on (before 2026-11-02 08:50 ET; none of it in the live panel after that), the hook shows sim an entry reference shifted so that unreal/W-ratio is tested against 30, i.e. the trigger becomes 30 x W/stop points of open profit (tight trail already scaled via TIGHT_TRAIL). Pair cells with `_x30` in the name run the unfixed version. Effect: narrow brackets start the profit tighten earlier (at 30W/stop), wide ones later; it only matters in months before 2026-11-02, never after.

### Holding time per book and session (JN05W2 exact trades, all 43 months, minutes)
| book | session | trades | median | 75th pct | last causal H50 / H75 used |
|---|---|---|---|---|---|
| A7 | asia | 1156 | 144 | 409 | 152 / 423 |
| H7 | asia | 700 | 229 | 511 | 244 / 515 |
| H7 | nyam | 348 | 43 | 117 | 43 / 117 |
| K7 | asia | 2596 | 88 | 270 | 91 / 279 |
| K7 | london | 1781 | 64 | 139 | 64 / 140 |
| K7 | nyam | 1565 | 23 | 64 | 23 / 64 |
| K7 | nypm | 1136 | 42 | 103 | 42 / 103 |
| M7 | london | 2489 | 73 | 172 | 74 / 174 |
| M7 | nyam | 1496 | 22 | 60 | 22 / 60 |
| O7 | nyam | 452 | 14 | 33 | 15 / 33 |
| P7 | asia | 2161 | 96 | 325 | 98 / 332 |
| P7 | london | 1537 | 60 | 136 | 60 / 136 |
| P7 | nyam | 1050 | 24 | 57 | 24 / 57 |
| U7 | asia | 686 | 201 | 456 | 208 / 459 |
| U7 | london | 645 | 109 | 243 | 110 / 244 |

Heavy tail: some holds run for days (stop-less P7/K7 waiting); H is clipped to 5..600 min (median) and 8..900 (75th).

### FORECAST QUALITY TABLE: expected NQ move over the trade horizon, walk-forward (14-day blocks, expanding, min 90 days), R2 / Spearman rank, per session
Target = ln(high-low over the next H minutes / price) at each trade signal second of JN05W2 (H = causal median holding time of that book+session, tag 50; 75th pct tag 75). B0 is the session-start forecast the first Dial 9 used (available since 2025-03-19), B2 the T-RANGE2 v1 session forecast (HAR+CME, from 2023-10), both fed through the same ridge with ln H. Window "since 2025-03" is the like-for-like sample (all models on the same trades); "ALL43" scores M1/B1 on every trade from ~2023-05 (each model only where its input exists, n differs).

**Horizon = median holding time**
| session | window | n (like-for-like) | B0 start fc b (D9) | B2 T-RANGE2 | B1 own sess level | **M1 bars only** | M1 w/o same-clock | M2 +T-RANGE2+cal (file) |
|---|---|---|---|---|---|---|---|---|
| asia | since 2025-03 | 4424 | 0.32 / 0.55 | 0.36 / 0.57 | 0.19 / 0.42 | 0.49 / 0.68 | 0.42 / 0.61 | 0.49 / 0.68 |
| asia | L6M | 2006 | 0.26 / 0.52 | 0.33 / 0.57 | 0.25 / 0.50 | 0.46 / 0.67 | 0.37 / 0.60 | 0.46 / 0.66 |
| asia | L3M | 875 | 0.12 / 0.41 | 0.16 / 0.44 | 0.07 / 0.34 | 0.27 / 0.55 | 0.25 / 0.50 | 0.28 / 0.56 |
| asia | ALL43 (M1/B1) | 7125 | 0.32 / 0.55 | 0.33 / 0.56 | 0.11 / 0.35 | 0.50 / 0.68 | 0.45 / 0.63 | 0.51 / 0.69 |
| london | since 2025-03 | 3535 | 0.19 / 0.46 | 0.28 / 0.55 | 0.08 / 0.34 | 0.45 / 0.67 | 0.36 / 0.60 | 0.46 / 0.68 |
| london | L6M | 1406 | 0.10 / 0.38 | 0.22 / 0.48 | 0.07 / 0.28 | 0.32 / 0.58 | 0.25 / 0.51 | 0.34 / 0.59 |
| london | L3M | 673 | 0.07 / 0.30 | 0.09 / 0.32 | -0.09 / 0.19 | 0.13 / 0.43 | 0.06 / 0.40 | 0.18 / 0.45 |
| london | ALL43 (M1/B1) | 6298 | 0.19 / 0.46 | 0.37 / 0.57 | 0.14 / 0.38 | 0.55 / 0.71 | 0.46 / 0.65 | 0.56 / 0.72 |
| nyam | since 2025-03 | 1955 | 0.16 / 0.43 | 0.24 / 0.51 | 0.01 / 0.22 | 0.50 / 0.71 | 0.50 / 0.71 | 0.51 / 0.71 |
| nyam | L6M | 600 | 0.23 / 0.53 | 0.28 / 0.56 | 0.05 / 0.26 | 0.61 / 0.78 | 0.61 / 0.78 | 0.61 / 0.78 |
| nyam | L3M | 271 | -0.08 / 0.33 | 0.04 / 0.35 | -0.35 / 0.10 | 0.42 / 0.64 | 0.43 / 0.65 | 0.44 / 0.65 |
| nyam | ALL43 (M1/B1) | 4742 | 0.16 / 0.43 | 0.30 / 0.53 | 0.11 / 0.34 | 0.53 / 0.70 | 0.53 / 0.70 | 0.53 / 0.71 |
| nypm | since 2025-03 | 326 | 0.13 / 0.41 | 0.35 / 0.65 | 0.05 / 0.20 | 0.53 / 0.72 | 0.53 / 0.72 | 0.56 / 0.74 |
| nypm | L6M | 150 | 0.20 / 0.51 | 0.37 / 0.69 | 0.08 / 0.26 | 0.61 / 0.79 | 0.61 / 0.79 | 0.64 / 0.80 |
| nypm | L3M | 56 | -0.33 / 0.12 | -0.18 / 0.16 | -0.82 / -0.06 | 0.19 / 0.54 | 0.17 / 0.53 | 0.25 / 0.50 |
| nypm | ALL43 (M1/B1) | 967 | 0.13 / 0.41 | 0.21 / 0.54 | 0.09 / 0.29 | 0.50 / 0.68 | 0.50 / 0.68 | 0.51 / 0.69 |

**Horizon = 75th percentile holding time**
| session | window | n (like-for-like) | B0 start fc b (D9) | B2 T-RANGE2 | B1 own sess level | **M1 bars only** | M1 w/o same-clock | M2 +T-RANGE2+cal (file) |
|---|---|---|---|---|---|---|---|---|
| asia | since 2025-03 | 4424 | 0.30 / 0.54 | 0.35 / 0.54 | 0.14 / 0.36 | 0.44 / 0.65 | 0.36 / 0.58 | 0.45 / 0.66 |
| asia | L6M | 2006 | 0.12 / 0.45 | 0.23 / 0.49 | 0.19 / 0.44 | 0.32 / 0.59 | 0.18 / 0.50 | 0.32 / 0.59 |
| asia | L3M | 875 | -0.11 / 0.27 | -0.01 / 0.31 | -0.07 / 0.21 | 0.05 / 0.40 | -0.02 / 0.39 | 0.06 / 0.41 |
| asia | ALL43 (M1/B1) | 7125 | 0.30 / 0.54 | 0.30 / 0.53 | 0.09 / 0.32 | 0.49 / 0.67 | 0.43 / 0.62 | 0.49 / 0.68 |
| london | since 2025-03 | 3535 | 0.16 / 0.42 | 0.23 / 0.49 | 0.07 / 0.33 | 0.56 / 0.75 | 0.48 / 0.69 | 0.57 / 0.76 |
| london | L6M | 1406 | 0.07 / 0.29 | 0.14 / 0.41 | 0.06 / 0.27 | 0.47 / 0.68 | 0.37 / 0.61 | 0.48 / 0.68 |
| london | L3M | 673 | 0.03 / 0.23 | 0.02 / 0.27 | -0.10 / 0.26 | 0.31 / 0.61 | 0.23 / 0.54 | 0.35 / 0.60 |
| london | ALL43 (M1/B1) | 6297 | 0.16 / 0.42 | 0.31 / 0.52 | 0.12 / 0.34 | 0.59 / 0.76 | 0.53 / 0.72 | 0.61 / 0.77 |
| nyam | since 2025-03 | 1955 | 0.18 / 0.46 | 0.27 / 0.54 | 0.04 / 0.28 | 0.47 / 0.69 | 0.47 / 0.69 | 0.48 / 0.70 |
| nyam | L6M | 600 | 0.22 / 0.51 | 0.26 / 0.55 | 0.09 / 0.33 | 0.55 / 0.74 | 0.55 / 0.74 | 0.54 / 0.73 |
| nyam | L3M | 271 | -0.08 / 0.27 | 0.06 / 0.37 | -0.24 / 0.23 | 0.33 / 0.56 | 0.34 / 0.58 | 0.34 / 0.56 |
| nyam | ALL43 (M1/B1) | 4742 | 0.18 / 0.46 | 0.31 / 0.54 | 0.11 / 0.34 | 0.48 / 0.67 | 0.47 / 0.67 | 0.48 / 0.68 |
| nypm | since 2025-03 | 326 | 0.18 / 0.41 | 0.38 / 0.67 | 0.04 / 0.16 | 0.45 / 0.65 | 0.44 / 0.64 | 0.51 / 0.70 |
| nypm | L6M | 150 | 0.24 / 0.49 | 0.42 / 0.72 | 0.07 / 0.26 | 0.54 / 0.73 | 0.54 / 0.72 | 0.61 / 0.77 |
| nypm | L3M | 56 | -0.81 / 0.15 | -0.52 / 0.07 | -1.58 / -0.18 | -0.56 / 0.30 | -0.64 / 0.28 | -0.40 / 0.25 |
| nypm | ALL43 (M1/B1) | 962 | 0.18 / 0.41 | 0.23 / 0.54 | 0.06 / 0.25 | 0.40 / 0.62 | 0.40 / 0.61 | 0.43 / 0.65 |

Reading: cell = R2 / Spearman. Out-of-sample, no look-ahead (inputs closed bars up to the signal second; training targets ended before the block start). "Bars only" = D7 can compute everything from its own 1-minute bars plus a small coefficient table that is refit every 14 days; M2 needs the T-RANGE2 file and the calendar. Not a PASS claim: a better forecast does not by itself make a better bracket (exact cells below decide).


### Which setting carries it (median over cells, scope all, delta vs JN05W2; DD cut + = smaller drawdown; cells of the plain family only, no book/session restriction)
| group | cells L3M | median DD cut L3M % | median d mean L3M $/wk | median d worst week L3M | median d full stops/wk | L6M median DD cut % / d mean / cells |
|---|---|---|---|---|---|---|
| g=0.5 | 6 | -10.9 | -3267 | -3640 | +1.41 | -10.9 / -4207 / 6 |
| g=1.0 | 61 | -7.3 | -4332 | -2716 | +2.74 | -7.9 / -2767 / 16 |
| g=1.5 | 14 | -24.2 | -9917 | -8149 | +3.96 | -19.5 / -7725 / 1 |
| g=2.0 | 6 | -54.3 | -11675 | -4932 | +4.18 | -97.4 / -6163 / 1 |
| clip=1 | 51 | -7.6 | -3321 | -2716 | +2.59 | -14.4 / -3584 / 15 |
| clip=2 | 29 | -14.4 | -7400 | -4214 | +3.35 | -7.5 / -3555 / 5 |
| clip=3 | 8 | -18.3 | -7847 | -4405 | +3.77 | -12.7 / -4193 / 4 |
| tag=50 | 28 | -20.5 | -6312 | -7032 | +3.08 | -17.5 / -3785 / 10 |
| tag=75 | 60 | -7.3 | -4536 | -2581 | +2.85 | -3.7 / -2465 / 14 |
| db=0 | 6 | -4.4 | -3308 | -2989 | +3.23 | -4.7 / -2454 / 1 |
| db=10 | 76 | -14.4 | -5659 | -4085 | +3.01 | -12.7 / -3569 / 22 |
| db=20 | 6 | +2.5 | -1901 | +2207 | +2.66 | -18.0 / -3931 / 1 |
| lots=c15 | 6 | -8.2 | -4353 | -2553 | +3.16 | -8.5 / -3215 / 2 |
| lots=c20 | 70 | -14.4 | -5036 | -3969 | +2.93 | -11.1 / -3555 / 19 |
| lots=c30 | 6 | -4.8 | -3613 | -1831 | +3.20 | -12.3 / -2579 / 2 |
| lots=h | 6 | -12.0 | -9251 | -6042 | +2.59 | -16.6 / -5544 / 1 |
| tr=08 | 4 | +2.3 | -5800 | +3333 | +2.13 | n/a |
| tr=10 | 4 | -2.5 | -1797 | -810 | +3.20 | -1.3 / -2207 / 2 |
| tr=12 | 4 | -62.2 | -8339 | -17857 | +3.31 | n/a |
| tr=15 | 5 | -29.4 | -6990 | -11398 | +3.58 | n/a |
| tr=b | 66 | -12.0 | -4911 | -4085 | +3.04 | -14.4 / -3684 / 22 |
| tr=m | 5 | -7.6 | -6257 | -3998 | +2.51 | n/a |
| half=B | 60 | -16.9 | -5986 | -4620 | +3.12 | -14.4 / -3785 / 19 |
| half=N | 14 | +0.1 | -2737 | +154 | +3.50 | +0.1 / -2202 / 5 |
| half=W | 14 | -7.3 | -1406 | -2716 | -0.30 | n/a |
| fc=M1 | 83 | -11.0 | -4933 | -3816 | +3.12 | -11.1 / -3555 / 23 |
| fc=M2 | 5 | -36.2 | -11406 | -10331 | +2.59 | -36.2 / -6578 / 1 |

### Per cell, scope all (sorted by L3M drawdown cut; L6M, HOLD, GAP/MID and PRE when present)
| cell | L3M | L6M | HOLD | MID(GAP) | PRE | d mean/wk at $4.84 L3M | at $4.84 L6M |
|---|---|---|---|---|---|---|---|
| M1_50_g00_c1_d10_c20_tb_B_tcoracle0.9T75 | +85531 $/wk, DD +67.0%, ww +64263, stops 6.54(10.35), b5 259%, w2l 0 | n/a | n/a | n/a | n/a | +85219 (lots +85/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40 | +147 $/wk, DD +62.9%, ww +29432, stops 9.89(10.35), b5 73%, w2l 0 | -1909 $/wk, DD +62.3%, ww +26117, stops 11.07(10.99), b5 64%, w2l 0 | -1834 $/wk, DD +27.0%, ww +21859, stops 10.64(10.66), b5 64%, w2l 5 | -4651 $/wk, DD +14.9%, ww +28035, stops 10.54(10.88), b5 62%, w2l 2 | -4868 $/wk, DD +13.1%, ww +23441, stops 9.23(9.31), b5 48%, w2l 3 | +307 (lots -44/wk) | -1680 (lots -63/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40s102 | -1113 $/wk, DD +61.7%, ww +29033, stops 10.12(10.35), b5 72%, w2l 0 | -3565 $/wk, DD +56.3%, ww +23942, stops 11.03(10.99), b5 64%, w2l 0 | -2899 $/wk, DD +27.2%, ww +16532, stops 10.53(10.66), b5 69%, w2l 4 | -5782 $/wk, DD +14.2%, ww +13310, stops 10.20(10.88), b5 70%, w2l 2 | -4824 $/wk, DD +11.9%, ww +23442, stops 9.13(9.31), b5 50%, w2l 3 | -936 (lots -48/wk) | -3315 (lots -68/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60s103 | -1046 $/wk, DD +60.8%, ww +23767, stops 10.27(10.35), b5 83%, w2l 0 | -3084 $/wk, DD +60.1%, ww +23767, stops 10.80(10.99), b5 72%, w2l 0 | n/a | n/a | n/a | -861 (lots -50/wk) | -2824 (lots -71/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s1p60 | +1046 $/wk, DD +60.0%, ww +25364, stops 12.17(10.35), b5 83%, w2l 0 | -2165 $/wk, DD +58.3%, ww +25364, stops 12.86(10.99), b5 67%, w2l 0 | -2892 $/wk, DD +20.8%, ww +15454, stops 12.56(10.66), b5 72%, w2l 4 | -4796 $/wk, DD +12.5%, ww +12232, stops 12.40(10.88), b5 75%, w2l 2 | n/a | +1220 (lots -47/wk) | -1918 (lots -68/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx45x60 | -2138 $/wk, DD +58.8%, ww +23369, stops 10.80(10.35), b5 74%, w2l 0 | -3632 $/wk, DD +58.8%, ww +23369, stops 11.15(10.99), b5 70%, w2l 0 | -3232 $/wk, DD +19.2%, ww +24040, stops 10.68(10.66), b5 73%, w2l 4 | -4089 $/wk, DD +28.7%, ww +20817, stops 10.46(10.88), b5 71%, w2l 2 | n/a | -1952 (lots -51/wk) | -3377 (lots -70/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60s102 | -1508 $/wk, DD +58.7%, ww +21213, stops 10.27(10.35), b5 78%, w2l 0 | -3257 $/wk, DD +58.7%, ww +21213, stops 10.80(10.99), b5 70%, w2l 0 | n/a | n/a | n/a | -1320 (lots -51/wk) | -2996 (lots -71/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60 | -2959 $/wk, DD +57.9%, ww +21434, stops 10.04(10.35), b5 75%, w2l 1 | -4470 $/wk, DD +57.9%, ww +21434, stops 10.65(10.99), b5 67%, w2l 1 | -3794 $/wk, DD +17.3%, ww +24303, stops 10.45(10.66), b5 74%, w2l 5 | -2765 $/wk, DD +31.7%, ww +24273, stops 10.29(10.88), b5 70%, w2l 2 | n/a | -2780 (lots -49/wk) | -4217 (lots -69/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s3p81 | -1472 $/wk, DD +57.2%, ww +23874, stops 10.35(10.35), b5 80%, w2l 0 | -3618 $/wk, DD +57.2%, ww +23874, stops 10.96(10.99), b5 71%, w2l 0 | n/a | n/a | n/a | -1283 (lots -52/wk) | -3362 (lots -70/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s3p60 | -614 $/wk, DD +57.1%, ww +23582, stops 12.10(10.35), b5 76%, w2l 0 | -3092 $/wk, DD +57.1%, ww +23582, stops 12.86(10.99), b5 69%, w2l 0 | -3044 $/wk, DD +11.4%, ww +20993, stops 12.24(10.66), b5 71%, w2l 4 | -3735 $/wk, DD +6.4%, ww +24515, stops 12.06(10.88), b5 76%, w2l 2 | n/a | -455 (lots -43/wk) | -2858 (lots -64/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40s103 | +340 $/wk, DD +56.9%, ww +28027, stops 10.04(10.35), b5 80%, w2l 0 | -1838 $/wk, DD +56.9%, ww +28027, stops 10.99(10.99), b5 69%, w2l 0 | -2711 $/wk, DD +16.7%, ww +21859, stops 10.66(10.66), b5 64%, w2l 4 | -4539 $/wk, DD +29.6%, ww +28238, stops 10.46(10.88), b5 61%, w2l 2 | -4213 $/wk, DD +21.5%, ww +23590, stops 9.21(9.31), b5 53%, w2l 2 | +526 (lots -51/wk) | -1592 (lots -67/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60s101 | -1656 $/wk, DD +56.9%, ww +23969, stops 10.27(10.35), b5 77%, w2l 0 | -3525 $/wk, DD +56.9%, ww +23969, stops 10.77(10.99), b5 69%, w2l 0 | -3190 $/wk, DD +20.7%, ww +24703, stops 10.51(10.66), b5 74%, w2l 5 | -3398 $/wk, DD +30.1%, ww +26037, stops 10.37(10.88), b5 70%, w2l 2 | n/a | -1470 (lots -51/wk) | -3268 (lots -70/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2 | -1570 $/wk, DD +56.8%, ww +22941, stops 10.27(10.35), b5 77%, w2l 0 | n/a | n/a | n/a | n/a | -1375 (lots -53/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bM7_sam_JL2_ddvote_w_aT20 | -1570 $/wk, DD +56.8%, ww +22941, stops 10.27(10.35), b5 77%, w2l 0 | -3060 $/wk, DD +56.8%, ww +22941, stops 10.88(10.99), b5 73%, w2l 0 | -2987 $/wk, DD +19.2%, ww +23935, stops 10.53(10.66), b5 74%, w2l 4 | -3748 $/wk, DD +29.0%, ww +21071, stops 10.29(10.88), b5 69%, w2l 2 | n/a | -1375 (lots -53/wk) | -2796 (lots -72/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bO7_sam_JL2_ddvote_w_aT20 | -1570 $/wk, DD +56.8%, ww +22941, stops 10.27(10.35), b5 77%, w2l 0 | -3060 $/wk, DD +56.8%, ww +22941, stops 10.88(10.99), b5 73%, w2l 0 | -2987 $/wk, DD +19.2%, ww +23935, stops 10.53(10.66), b5 74%, w2l 4 | -3748 $/wk, DD +29.0%, ww +21071, stops 10.29(10.88), b5 69%, w2l 2 | n/a | -1375 (lots -53/wk) | -2796 (lots -72/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bO7_sam_JL2_ddvote_w_aT25 | -1570 $/wk, DD +56.8%, ww +22941, stops 10.27(10.35), b5 77%, w2l 0 | -3060 $/wk, DD +56.8%, ww +22941, stops 10.88(10.99), b5 73%, w2l 0 | -2987 $/wk, DD +19.2%, ww +23935, stops 10.53(10.66), b5 74%, w2l 4 | -3748 $/wk, DD +29.0%, ww +21071, stops 10.29(10.88), b5 69%, w2l 2 | n/a | -1375 (lots -53/wk) | -2796 (lots -72/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_JL2_gb40B40 | -1440 $/wk, DD +56.8%, ww +24681, stops 10.04(10.35), b5 78%, w2l 0 | -2978 $/wk, DD +56.8%, ww +24681, stops 10.73(10.99), b5 72%, w2l 0 | -2910 $/wk, DD +21.2%, ww +23935, stops 10.38(10.66), b5 73%, w2l 4 | -3448 $/wk, DD +29.0%, ww +21071, stops 10.12(10.88), b5 69%, w2l 2 | n/a | -1245 (lots -53/wk) | -2715 (lots -72/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_JL2_gb50B40 | -1459 $/wk, DD +56.8%, ww +24596, stops 10.04(10.35), b5 77%, w2l 0 | -2963 $/wk, DD +56.8%, ww +24596, stops 10.73(10.99), b5 72%, w2l 0 | -2914 $/wk, DD +21.1%, ww +23935, stops 10.38(10.66), b5 73%, w2l 4 | -3473 $/wk, DD +29.0%, ww +21071, stops 10.12(10.88), b5 69%, w2l 2 | n/a | -1264 (lots -53/wk) | -2699 (lots -72/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_JL2_gb40B30 | -2061 $/wk, DD +56.8%, ww +22941, stops 10.27(10.35), b5 75%, w2l 0 | -3367 $/wk, DD +56.8%, ww +22941, stops 10.84(10.99), b5 72%, w2l 0 | -3207 $/wk, DD +20.4%, ww +23484, stops 10.51(10.66), b5 71%, w2l 4 | -4372 $/wk, DD +29.0%, ww +20261, stops 10.29(10.88), b5 66%, w2l 2 | n/a | -1867 (lots -53/wk) | -3104 (lots -72/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s2p92 | -3013 $/wk, DD +56.6%, ww +21370, stops 9.97(10.35), b5 73%, w2l 0 | -2983 $/wk, DD +56.6%, ww +21370, stops 10.77(10.99), b5 75%, w2l 0 | -2111 $/wk, DD +9.0%, ww +23322, stops 10.30(10.66), b5 77%, w2l 4 | +177 $/wk, DD +35.5%, ww +20541, stops 9.87(10.88), b5 75%, w2l 1 | n/a | -2825 (lots -51/wk) | -2731 (lots -69/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s2p81 | -3135 $/wk, DD +56.1%, ww +21341, stops 9.97(10.35), b5 72%, w2l 0 | -3478 $/wk, DD +56.1%, ww +21341, stops 10.84(10.99), b5 74%, w2l 0 | n/a | n/a | n/a | -2941 (lots -53/wk) | -3221 (lots -70/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40s103 | -1004 $/wk, DD +56.0%, ww +23340, stops 11.41(10.35), b5 80%, w2l 0 | -2950 $/wk, DD +56.0%, ww +23340, stops 12.36(10.99), b5 75%, w2l 0 | -3088 $/wk, DD +12.9%, ww +21714, stops 12.43(10.66), b5 71%, w2l 3 | -4265 $/wk, DD +29.0%, ww +21318, stops 12.40(10.88), b5 66%, w2l 1 | n/a | -820 (lots -50/wk) | -2696 (lots -69/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60s101 | -722 $/wk, DD +56.0%, ww +22141, stops 10.27(10.35), b5 83%, w2l 0 | -2640 $/wk, DD +56.0%, ww +22141, stops 10.88(10.99), b5 76%, w2l 0 | n/a | n/a | n/a | -531 (lots -52/wk) | -2380 (lots -71/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60s103 | -1044 $/wk, DD +56.0%, ww +22541, stops 10.27(10.35), b5 79%, w2l 0 | -2789 $/wk, DD +56.0%, ww +22541, stops 10.88(10.99), b5 74%, w2l 0 | -3125 $/wk, DD +21.6%, ww +24171, stops 10.55(10.66), b5 70%, w2l 4 | -4601 $/wk, DD +27.9%, ww +20949, stops 10.37(10.88), b5 65%, w2l 2 | n/a | -853 (lots -52/wk) | -2527 (lots -72/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_gb40B40 | -645 $/wk, DD +55.9%, ww +22941, stops 10.27(10.35), b5 82%, w2l 0 | -2797 $/wk, DD +55.9%, ww +22941, stops 10.88(10.99), b5 74%, w2l 0 | -2792 $/wk, DD +18.2%, ww +24446, stops 10.55(10.66), b5 74%, w2l 4 | -4243 $/wk, DD +29.9%, ww +21224, stops 10.37(10.88), b5 68%, w2l 2 | n/a | -457 (lots -51/wk) | -2539 (lots -71/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40s101 | -368 $/wk, DD +55.8%, ww +21377, stops 11.72(10.35), b5 85%, w2l 0 | -2517 $/wk, DD +55.8%, ww +21377, stops 12.59(10.99), b5 76%, w2l 0 | -2683 $/wk, DD +16.7%, ww +23238, stops 12.56(10.66), b5 74%, w2l 4 | -3846 $/wk, DD +29.8%, ww +21359, stops 11.98(10.88), b5 69%, w2l 2 | n/a | -185 (lots -50/wk) | -2265 (lots -69/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s1p35 | -243 $/wk, DD +55.5%, ww +24610, stops 11.34(10.35), b5 84%, w2l 0 | -2131 $/wk, DD +55.5%, ww +24610, stops 12.10(10.99), b5 69%, w2l 0 | -2869 $/wk, DD +17.5%, ww +17265, stops 11.64(10.66), b5 72%, w2l 4 | -5139 $/wk, DD +14.1%, ww +14042, stops 11.22(10.88), b5 69%, w2l 2 | -3747 $/wk, DD +16.8%, ww +21980, stops 9.82(9.31), b5 53%, w2l 0 | -61 (lots -50/wk) | -1881 (lots -68/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s3p35 | -348 $/wk, DD +55.4%, ww +24399, stops 11.49(10.35), b5 78%, w2l 0 | -2404 $/wk, DD +55.4%, ww +24399, stops 11.83(10.99), b5 70%, w2l 0 | -2995 $/wk, DD +12.7%, ww +22396, stops 11.45(10.66), b5 71%, w2l 4 | -4448 $/wk, DD +14.3%, ww +21310, stops 11.39(10.88), b5 69%, w2l 2 | -4658 $/wk, DD +22.8%, ww +22030, stops 9.64(9.31), b5 54%, w2l 1 | -172 (lots -48/wk) | -2158 (lots -67/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s3p81 | -1229 $/wk, DD +55.1%, ww +20887, stops 12.55(10.35), b5 75%, w2l 0 | -3280 $/wk, DD +55.1%, ww +20887, stops 13.43(10.99), b5 69%, w2l 0 | -3325 $/wk, DD +5.2%, ww +20301, stops 12.73(10.66), b5 72%, w2l 5 | -3386 $/wk, DD +14.1%, ww +32710, stops 12.48(10.88), b5 72%, w2l 3 | n/a | -1073 (lots -43/wk) | -3054 (lots -62/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40s101 | -3497 $/wk, DD +54.6%, ww +24004, stops 12.10(10.35), b5 74%, w2l 2 | -4579 $/wk, DD +54.6%, ww +24004, stops 12.63(10.99), b5 71%, w2l 2 | -3961 $/wk, DD +24.1%, ww +28381, stops 11.85(10.66), b5 63%, w2l 7 | -2301 $/wk, DD +34.8%, ww +28998, stops 11.55(10.88), b5 70%, w2l 2 | n/a | -3304 (lots -53/wk) | -4318 (lots -71/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40 | -46 $/wk, DD +54.5%, ww +21776, stops 13.39(10.35), b5 85%, w2l 0 | -2571 $/wk, DD +54.5%, ww +21776, stops 14.04(10.99), b5 75%, w2l 0 | -2954 $/wk, DD +7.7%, ww +19997, stops 14.27(10.66), b5 72%, w2l 4 | -5116 $/wk, DD +31.6%, ww +21318, stops 13.83(10.88), b5 63%, w2l 2 | n/a | +123 (lots -46/wk) | -2330 (lots -66/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40s102 | -380 $/wk, DD +54.5%, ww +21138, stops 11.87(10.35), b5 82%, w2l 0 | -2761 $/wk, DD +54.5%, ww +21138, stops 12.52(10.99), b5 73%, w2l 0 | -2969 $/wk, DD +13.3%, ww +22473, stops 12.31(10.66), b5 73%, w2l 5 | -4098 $/wk, DD +29.1%, ww +21186, stops 11.98(10.88), b5 68%, w2l 2 | n/a | -199 (lots -49/wk) | -2510 (lots -69/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60 | -452 $/wk, DD +54.5%, ww +22540, stops 10.27(10.35), b5 83%, w2l 0 | -2683 $/wk, DD +54.5%, ww +22540, stops 10.88(10.99), b5 74%, w2l 0 | n/a | n/a | -4813 $/wk, DD +23.4%, ww +24830, stops 9.05(9.31), b5 55%, w2l 1 | -265 (lots -51/wk) | -2425 (lots -70/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60s102 | -649 $/wk, DD +54.5%, ww +22018, stops 10.27(10.35), b5 82%, w2l 0 | -2830 $/wk, DD +54.5%, ww +22018, stops 10.88(10.99), b5 73%, w2l 0 | -2886 $/wk, DD +18.7%, ww +23535, stops 10.55(10.66), b5 72%, w2l 4 | -3961 $/wk, DD +30.6%, ww +20671, stops 10.37(10.88), b5 69%, w2l 2 | n/a | -459 (lots -52/wk) | -2569 (lots -71/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_JL2_gb40B40 | -1700 $/wk, DD +54.2%, ww +22941, stops 10.35(10.35), b5 76%, w2l 0 | -3901 $/wk, DD +54.2%, ww +22941, stops 10.92(10.99), b5 72%, w2l 0 | -3224 $/wk, DD +22.1%, ww +24071, stops 10.49(10.66), b5 73%, w2l 4 | -3172 $/wk, DD +27.4%, ww +24611, stops 10.12(10.88), b5 70%, w2l 2 | n/a | -1502 (lots -54/wk) | -3637 (lots -72/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40s101 | -1282 $/wk, DD +54.1%, ww +21959, stops 10.12(10.35), b5 74%, w2l 0 | -3339 $/wk, DD +54.1%, ww +21959, stops 11.03(10.99), b5 69%, w2l 0 | -2502 $/wk, DD +31.2%, ww +23532, stops 10.55(10.66), b5 74%, w2l 5 | -4372 $/wk, DD +24.6%, ww +28433, stops 10.46(10.88), b5 63%, w2l 3 | -5359 $/wk, DD +14.9%, ww +23441, stops 9.26(9.31), b5 45%, w2l 3 | -1104 (lots -49/wk) | -3093 (lots -67/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s1p81 | +233 $/wk, DD +54.0%, ww +24228, stops 10.50(10.35), b5 85%, w2l 0 | -2776 $/wk, DD +54.0%, ww +24228, stops 10.99(10.99), b5 70%, w2l 0 | n/a | n/a | n/a | +419 (lots -51/wk) | -2520 (lots -70/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s3p92 | -1206 $/wk, DD +53.5%, ww +23074, stops 10.20(10.35), b5 84%, w2l 0 | -3692 $/wk, DD +53.5%, ww +23074, stops 10.84(10.99), b5 73%, w2l 0 | n/a | n/a | n/a | -1021 (lots -51/wk) | -3439 (lots -69/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_gb50B20 | -1287 $/wk, DD +53.4%, ww +22160, stops 10.27(10.35), b5 80%, w2l 0 | -3405 $/wk, DD +53.4%, ww +22160, stops 10.88(10.99), b5 71%, w2l 0 | -3337 $/wk, DD +14.9%, ww +23541, stops 10.57(10.66), b5 70%, w2l 4 | -4716 $/wk, DD +31.5%, ww +20319, stops 10.37(10.88), b5 63%, w2l 2 | n/a | -1105 (lots -50/wk) | -3150 (lots -70/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s2p35 | +197 $/wk, DD +53.3%, ww +22115, stops 11.26(10.35), b5 81%, w2l 0 | -1404 $/wk, DD +53.3%, ww +22115, stops 12.02(10.99), b5 75%, w2l 0 | -2094 $/wk, DD +10.8%, ww +23494, stops 11.51(10.66), b5 69%, w2l 4 | -2802 $/wk, DD +33.1%, ww +20272, stops 11.72(10.88), b5 68%, w2l 2 | -4821 $/wk, DD +37.5%, ww +24801, stops 9.87(9.31), b5 54%, w2l 1 | +381 (lots -50/wk) | -1157 (lots -67/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s1p92 | +305 $/wk, DD +53.0%, ww +23711, stops 10.50(10.35), b5 85%, w2l 0 | -2125 $/wk, DD +53.0%, ww +23711, stops 10.99(10.99), b5 71%, w2l 0 | -2534 $/wk, DD +19.5%, ww +15897, stops 10.57(10.66), b5 74%, w2l 3 | -4358 $/wk, DD +21.4%, ww +12675, stops 10.20(10.88), b5 66%, w2l 2 | n/a | +490 (lots -51/wk) | -1873 (lots -69/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s2p81 | -2961 $/wk, DD +52.9%, ww +22118, stops 12.17(10.35), b5 72%, w2l 0 | -2053 $/wk, DD +52.9%, ww +22118, stops 14.04(10.99), b5 74%, w2l 0 | -1887 $/wk, DD +7.5%, ww +18242, stops 12.93(10.66), b5 72%, w2l 4 | -891 $/wk, DD +29.1%, ww +15019, stops 12.14(10.88), b5 72%, w2l 2 | n/a | -2801 (lots -44/wk) | -1831 (lots -61/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s2p60 | -1042 $/wk, DD +52.9%, ww +22118, stops 11.95(10.35), b5 75%, w2l 0 | -1803 $/wk, DD +52.9%, ww +22118, stops 13.01(10.99), b5 75%, w2l 0 | -1596 $/wk, DD +12.9%, ww +24560, stops 12.25(10.66), b5 74%, w2l 4 | -509 $/wk, DD +24.6%, ww +23875, stops 12.06(10.88), b5 69%, w2l 1 | n/a | -873 (lots -46/wk) | -1567 (lots -65/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40s102 | -3195 $/wk, DD +52.3%, ww +22798, stops 11.64(10.35), b5 78%, w2l 0 | -4172 $/wk, DD +52.3%, ww +22798, stops 12.25(10.99), b5 69%, w2l 0 | -4165 $/wk, DD +20.2%, ww +19938, stops 11.55(10.66), b5 65%, w2l 4 | -5250 $/wk, DD +18.6%, ww +16715, stops 11.72(10.88), b5 72%, w2l 2 | n/a | -2993 (lots -55/wk) | -3911 (lots -71/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_JL2_gb60B30 | -2833 $/wk, DD +52.1%, ww +22941, stops 10.35(10.35), b5 75%, w2l 1 | -4331 $/wk, DD +52.1%, ww +22941, stops 10.80(10.99), b5 71%, w2l 1 | -3115 $/wk, DD +21.3%, ww +21751, stops 10.41(10.66), b5 74%, w2l 5 | -2894 $/wk, DD +24.2%, ww +26073, stops 10.12(10.88), b5 70%, w2l 2 | n/a | -2630 (lots -55/wk) | -4061 (lots -74/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40s103 | -2805 $/wk, DD +46.3%, ww +23610, stops 11.64(10.35), b5 78%, w2l 1 | -3489 $/wk, DD +46.3%, ww +23610, stops 12.21(10.99), b5 73%, w2l 1 | -3043 $/wk, DD +21.3%, ww +28704, stops 11.62(10.66), b5 72%, w2l 5 | -2200 $/wk, DD +40.3%, ww +26988, stops 11.22(10.88), b5 70%, w2l 2 | n/a | -2607 (lots -54/wk) | -3228 (lots -71/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s1p81 | +50 $/wk, DD +45.5%, ww +22324, stops 12.71(10.35), b5 83%, w2l 1 | -2825 $/wk, DD +45.5%, ww +22324, stops 13.66(10.99), b5 64%, w2l 1 | -3184 $/wk, DD +13.9%, ww +20411, stops 13.19(10.66), b5 72%, w2l 5 | -5038 $/wk, DD +14.0%, ww +17189, stops 12.90(10.88), b5 73%, w2l 2 | n/a | +222 (lots -47/wk) | -2581 (lots -66/wk) |
| M1_50_g00_c1_d10_c20_tb_B_JL2_ddvwap_w_aK | -411 $/wk, DD +45.4%, ww +12941, stops 10.65(10.35), b5 97%, w2l 0 | -3553 $/wk, DD +45.4%, ww +12941, stops 11.07(10.99), b5 59%, w2l 0 | -3133 $/wk, DD +21.7%, ww +23708, stops 10.59(10.66), b5 69%, w2l 4 | -5348 $/wk, DD +12.1%, ww +20486, stops 10.20(10.88), b5 61%, w2l 2 | -5244 $/wk, DD +34.4%, ww +25255, stops 8.79(9.31), b5 62%, w2l 2 | -198 (lots -58/wk) | -3266 (lots -78/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_JL2_gb50B40 | -2599 $/wk, DD +41.2%, ww +19127, stops 10.35(10.35), b5 66%, w2l 0 | -5038 $/wk, DD +41.2%, ww +19127, stops 10.88(10.99), b5 60%, w2l 0 | -3945 $/wk, DD +18.0%, ww +20223, stops 10.51(10.66), b5 68%, w2l 5 | -3968 $/wk, DD +40.2%, ww +20785, stops 10.20(10.88), b5 75%, w2l 2 | n/a | -2436 (lots -45/wk) | -4799 (lots -65/wk) |
| M1_50_g00_c1_d10_c20_tb_B_tcremhar05T75 | -10795 $/wk, DD +40.3%, ww +11430, stops 7.00(10.35), b5 51%, w2l 4 | n/a | n/a | n/a | n/a | -11257 (lots +126/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_tcremhar10T75 | -7259 $/wk, DD +39.4%, ww +17319, stops 7.76(10.35), b5 65%, w2l 2 | n/a | n/a | n/a | n/a | -7570 (lots +85/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_JL2_gb40B40 | -2741 $/wk, DD +39.4%, ww +18199, stops 10.42(10.35), b5 68%, w2l 0 | -6049 $/wk, DD +39.4%, ww +18199, stops 10.96(10.99), b5 59%, w2l 0 | -4336 $/wk, DD +18.8%, ww +20037, stops 10.55(10.66), b5 66%, w2l 5 | -3842 $/wk, DD +32.6%, ww +16815, stops 10.37(10.88), b5 72%, w2l 2 | n/a | -2590 (lots -41/wk) | -5818 (lots -63/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40 | -3987 $/wk, DD +37.3%, ww +22661, stops 13.70(10.35), b5 67%, w2l 1 | -4120 $/wk, DD +37.3%, ww +22661, stops 14.57(10.99), b5 71%, w2l 1 | -4168 $/wk, DD +21.5%, ww +26230, stops 13.37(10.66), b5 63%, w2l 5 | -5059 $/wk, DD +15.2%, ww +23008, stops 13.16(10.88), b5 70%, w2l 2 | n/a | -3808 (lots -49/wk) | -3874 (lots -67/wk) |
| M1_50_g00_c1_d10_c20_tb_B_tcremown10T75 | -6226 $/wk, DD +27.0%, ww +12290, stops 8.98(10.35), b5 66%, w2l 2 | n/a | n/a | n/a | n/a | -6458 (lots +63/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x40s1 | +930 $/wk, DD +25.4%, ww +10509, stops 11.49(10.35), b5 96%, w2l 0 | +284 $/wk, DD +25.4%, ww +7146, stops 12.17(10.99), b5 100%, w2l 0 | -437 $/wk, DD -5.2%, ww +3352, stops 11.66(10.66), b5 95%, w2l 4 | -575 $/wk, DD +2.2%, ww +6298, stops 11.89(10.88), b5 102%, w2l 2 | -868 $/wk, DD +3.1%, ww -1, stops 9.69(9.31), b5 93%, w2l 0 | +912 (lots +5/wk) | +275 (lots +3/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx40x90 | -1332 $/wk, DD +24.5%, ww +14953, stops 10.27(10.35), b5 98%, w2l 1 | -2641 $/wk, DD +24.5%, ww +6860, stops 10.88(10.99), b5 98%, w2l 1 | n/a | n/a | n/a | -1323 (lots -3/wk) | -2637 (lots -1/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx60x90 | -2670 $/wk, DD +22.8%, ww +11680, stops 10.42(10.35), b5 96%, w2l 1 | -1093 $/wk, DD +22.8%, ww +11680, stops 11.03(10.99), b5 98%, w2l 1 | n/a | n/a | n/a | -2652 (lots -5/wk) | -1081 (lots -3/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x60 | +900 $/wk, DD +22.5%, ww +10172, stops 10.73(10.35), b5 98%, w2l 0 | +710 $/wk, DD +22.5%, ww +5127, stops 11.34(10.99), b5 98%, w2l 1 | +948 $/wk, DD +5.3%, ww +2668, stops 10.85(10.66), b5 96%, w2l 1 | +597 $/wk, DD +2.4%, ww -554, stops 10.96(10.88), b5 106%, w2l 0 | -203 $/wk, DD +2.9%, ww +1125, stops 9.26(9.31), b5 98%, w2l 0 | +885 (lots +4/wk) | +692 (lots +5/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx60x40 | +303 $/wk, DD +22.1%, ww +10998, stops 12.40(10.35), b5 90%, w2l 0 | +708 $/wk, DD +22.1%, ww +8715, stops 13.62(10.99), b5 98%, w2l 0 | -536 $/wk, DD -13.4%, ww +4266, stops 12.70(10.66), b5 96%, w2l 4 | -1973 $/wk, DD +1.2%, ww +2963, stops 12.90(10.88), b5 102%, w2l 1 | n/a | +291 (lots +4/wk) | +694 (lots +4/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x40s2 | -1125 $/wk, DD +22.1%, ww +11862, stops 11.34(10.35), b5 96%, w2l 0 | -176 $/wk, DD +22.1%, ww +11862, stops 12.10(10.99), b5 100%, w2l 1 | -1031 $/wk, DD -3.4%, ww +3720, stops 11.60(10.66), b5 94%, w2l 4 | -2353 $/wk, DD +3.1%, ww +771, stops 11.89(10.88), b5 99%, w2l 1 | -1464 $/wk, DD +4.8%, ww -1, stops 9.67(9.31), b5 87%, w2l 0 | -1138 (lots +4/wk) | -190 (lots +4/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x40 | +1149 $/wk, DD +20.9%, ww +12597, stops 12.63(10.35), b5 94%, w2l 0 | +1150 $/wk, DD +20.9%, ww +9505, stops 13.81(10.99), b5 99%, w2l 0 | -166 $/wk, DD -7.2%, ww +4623, stops 12.96(10.66), b5 93%, w2l 4 | -3119 $/wk, DD -4.7%, ww +2391, stops 13.33(10.88), b5 101%, w2l 1 | -1699 $/wk, DD +11.6%, ww +5169, stops 10.18(9.31), b5 87%, w2l 0 | +1119 (lots +8/wk) | +1123 (lots +8/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x90s1 | +2118 $/wk, DD +20.0%, ww +11372, stops 9.51(10.35), b5 101%, w2l 0 | +1334 $/wk, DD +20.0%, ww +5614, stops 10.12(10.99), b5 103%, w2l 0 | +779 $/wk, DD -3.2%, ww -223, stops 9.82(10.66), b5 103%, w2l 0 | -784 $/wk, DD -3.3%, ww -3445, stops 9.95(10.88), b5 100%, w2l 0 | +61 $/wk, DD +6.6%, ww -1, stops 8.92(9.31), b5 100%, w2l 0 | +2099 (lots +5/wk) | +1320 (lots +4/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx40x60 | +53 $/wk, DD +19.7%, ww +8749, stops 10.12(10.35), b5 100%, w2l 0 | -355 $/wk, DD +19.7%, ww +8749, stops 10.84(10.99), b5 94%, w2l 0 | -341 $/wk, DD +8.8%, ww -2324, stops 10.61(10.66), b5 101%, w2l 1 | -360 $/wk, DD +3.7%, ww +886, stops 10.80(10.88), b5 101%, w2l 1 | n/a | +36 (lots +5/wk) | -365 (lots +3/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x40s3 | +1384 $/wk, DD +18.1%, ww +9334, stops 11.03(10.35), b5 96%, w2l 0 | +805 $/wk, DD +18.1%, ww +9334, stops 12.06(10.99), b5 100%, w2l 1 | -188 $/wk, DD -4.1%, ww -2105, stops 11.58(10.66), b5 102%, w2l 2 | -678 $/wk, DD -6.2%, ww -5328, stops 11.64(10.88), b5 100%, w2l 0 | -309 $/wk, DD +3.0%, ww +399, stops 9.54(9.31), b5 92%, w2l 0 | +1375 (lots +3/wk) | +790 (lots +4/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx40x90 | -837 $/wk, DD +16.5%, ww +7135, stops 10.12(10.35), b5 92%, w2l 0 | -2284 $/wk, DD +16.5%, ww +7135, stops 10.88(10.99), b5 93%, w2l 0 | n/a | n/a | n/a | -846 (lots +3/wk) | -2279 (lots -2/wk) |
| M1_75_g10_c1_d10_c20_tb_W_bK7_sas | +691 $/wk, DD +16.3%, ww +8619, stops 10.27(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +692 (lots -0/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x90s2 | +907 $/wk, DD +16.2%, ww +8536, stops 9.13(10.35), b5 106%, w2l 0 | +411 $/wk, DD +16.2%, ww +8536, stops 10.08(10.99), b5 101%, w2l 0 | +67 $/wk, DD +5.8%, ww +1236, stops 9.82(10.66), b5 103%, w2l 0 | -507 $/wk, DD -1.4%, ww -1987, stops 9.87(10.88), b5 101%, w2l 0 | +485 $/wk, DD +8.3%, ww -1, stops 8.97(9.31), b5 102%, w2l 0 | +899 (lots +2/wk) | +400 (lots +3/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x90 | +1830 $/wk, DD +13.7%, ww +8914, stops 7.99(10.35), b5 101%, w2l 0 | +975 $/wk, DD +13.7%, ww +8914, stops 8.79(10.99), b5 99%, w2l 0 | +917 $/wk, DD +0.7%, ww -2284, stops 8.88(10.66), b5 100%, w2l 0 | -950 $/wk, DD -3.1%, ww -5507, stops 9.36(10.88), b5 98%, w2l 0 | +384 $/wk, DD +9.4%, ww +33, stops 8.62(9.31), b5 99%, w2l 0 | +1810 (lots +5/wk) | +958 (lots +5/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x90s3 | +3022 $/wk, DD +13.6%, ww +9860, stops 9.59(10.35), b5 105%, w2l 0 | +1972 $/wk, DD +13.6%, ww +9860, stops 10.08(10.99), b5 103%, w2l 1 | +728 $/wk, DD +3.7%, ww +1236, stops 9.90(10.66), b5 102%, w2l 1 | -1181 $/wk, DD -1.4%, ww -1987, stops 10.12(10.88), b5 95%, w2l 0 | +578 $/wk, DD +6.6%, ww +399, stops 9.08(9.31), b5 100%, w2l 0 | +3005 (lots +5/wk) | +1955 (lots +5/wk) |
| M1_75_g10_c1_d10_c20_t08_W | -1835 $/wk, DD +13.2%, ww +6516, stops 9.21(10.35), b5 82%, w2l 0 | n/a | n/a | n/a | n/a | -1901 (lots +18/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx40x60 | +534 $/wk, DD +12.1%, ww +9089, stops 10.12(10.35), b5 100%, w2l 0 | +282 $/wk, DD +12.1%, ww +9089, stops 10.73(10.99), b5 106%, w2l 0 | +123 $/wk, DD +1.9%, ww +5020, stops 10.62(10.66), b5 100%, w2l 0 | -607 $/wk, DD -1.1%, ww +2477, stops 11.30(10.88), b5 99%, w2l 0 | +14 $/wk, DD +11.3%, ww +9617, stops 9.28(9.31), b5 103%, w2l 0 | +501 (lots +9/wk) | +257 (lots +7/wk) |
| M1_75_g10_c1_d10_c20_tb_B_bK7_sas | +479 $/wk, DD +11.3%, ww +1079, stops 10.42(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +421 (lots +16/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx85x60 | +52 $/wk, DD +10.9%, ww +9854, stops 10.73(10.35), b5 99%, w2l 0 | +384 $/wk, DD +10.9%, ww +9854, stops 11.03(10.99), b5 103%, w2l 0 | +742 $/wk, DD +5.5%, ww -1453, stops 10.66(10.66), b5 104%, w2l 0 | +1046 $/wk, DD +1.3%, ww -1895, stops 10.88(10.88), b5 103%, w2l 0 | +62 $/wk, DD -1.5%, ww -1860, stops 9.38(9.31), b5 97%, w2l 0 | +51 (lots +0/wk) | +387 (lots -1/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx85x60 | -292 $/wk, DD +10.0%, ww -331, stops 10.50(10.35), b5 102%, w2l 0 | -1196 $/wk, DD +10.0%, ww -331, stops 10.99(10.99), b5 92%, w2l 0 | n/a | n/a | n/a | -286 (lots -2/wk) | -1182 (lots -4/wk) |
| M1_75_g05_c1_d10_c20_tb_B_bM7_slo | +525 $/wk, DD +9.7%, ww +3120, stops 10.58(10.35), b5 102%, w2l 0 | n/a | n/a | n/a | n/a | +520 (lots +1/wk) | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bK7_slo | +95 $/wk, DD +9.7%, ww -935, stops 10.42(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +77 (lots +5/wk) | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bK7_slo | +67 $/wk, DD +9.7%, ww +2585, stops 10.20(10.35), b5 101%, w2l 0 | n/a | n/a | n/a | n/a | +53 (lots +4/wk) | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bM7_slo | +1130 $/wk, DD +9.5%, ww +4114, stops 10.42(10.35), b5 100%, w2l 0 | n/a | n/a | n/a | n/a | +1118 (lots +3/wk) | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx40x40 | -2415 $/wk, DD +9.5%, ww -707, stops 10.27(10.35), b5 104%, w2l 1 | -773 $/wk, DD +9.5%, ww -707, stops 11.15(10.99), b5 99%, w2l 1 | n/a | n/a | n/a | -2509 (lots +26/wk) | -887 (lots +31/wk) |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx85x40 | -112 $/wk, DD +9.5%, ww +4687, stops 10.65(10.35), b5 98%, w2l 0 | -455 $/wk, DD +9.5%, ww +4687, stops 11.34(10.99), b5 93%, w2l 0 | +172 $/wk, DD +3.1%, ww -719, stops 11.01(10.66), b5 94%, w2l 2 | +608 $/wk, DD -5.3%, ww -3325, stops 11.22(10.88), b5 108%, w2l 0 | -36 $/wk, DD -12.7%, ww +881, stops 9.56(9.31), b5 109%, w2l 1 | -136 (lots +7/wk) | -475 (lots +6/wk) |
(307 more cells in /mnt/l2/l2vast/_dial10/cells.json)

### Narrow-only and wide-only for the leading cells (item 8; same cell, half B / N / W)
| base cell | half | L3M | L6M |
|---|---|---|---|
| (the N/W variants exist for g1 c1 H50/H75; the finalists get theirs from wave 2) | | | |

### Per book and per session (item 2): effect of the best whole-system cell on each book x session, and the best setting per book x session
Slice of the exact trade tables (books interact through day locks and caps, so single-book cells in the next table are the clean test). For every book x session the cell with the largest drawdown cut inside the tolerant mean gate in L3M (and in L6M when scored) is listed; "stays fixed" = no cell cuts drawdown inside the gate there.
| book | session | trades L3M | best cell | L3M | L6M | verdict |
|---|---|---|---|---|---|---|
| A7 | asia | 160 | M1_75_g10_c1_d10_c20_t08_N | +320 $/wk, DD +39.7%, ww +2974, stops 5.25(4.03), b5 6%, w2l 4 | n/a | L3M only |
| H7 | asia | 67 | M1_75_g10_c1_d10_c20_t15_N | +547 $/wk, DD +20.8%, ww -41, stops 0.53(0.23), b5 96%, w2l 3 | n/a | L3M only |
| H7 | nyam | 17 | M1_50_g15_c2_d10_c20_tm_B | +303 $/wk, DD +65.0%, ww +597, stops 0.15(0.38), b5 88%, w2l 0 | n/a | L3M only |
| K7 | asia | 333 | M1_75_g10_c2_d10_c20_t08_B | +1214 $/wk, DD +7.3%, ww +266, stops 0.15(0.00), b5 105%, w2l 1 | n/a | L3M only |
| K7 | london | 210 | M1_75_g10_c1_d10_c20_t12_N | +773 $/wk, DD +24.7%, ww +5048, stops 0.30(0.30), b5 82%, w2l 1 | n/a | L3M only |
| K7 | nyam | 88 | M1_50_g15_c2_d20_c20_tb_B | +1107 $/wk, DD +80.1%, ww +2337, stops 0.00(0.00), b5 86%, w2l 1 | n/a | L3M only |
| K7 | nypm | 56 | none inside the gate | | | stays fixed (no cell cuts DD inside the gate) |
| M7 | london | 248 | M1_75_g10_c1_d10_c20_t12_W | +268 $/wk, DD +10.6%, ww +559, stops 0.76(0.91), b5 102%, w2l 0 | n/a | L3M only |
| M7 | nyam | 88 | M1_75_g20_c1_d10_c20_tb_B | +242 $/wk, DD +52.6%, ww +1195, stops 0.30(0.23), b5 35%, w2l 0 | n/a | L3M only |
| P7 | asia | 243 | none inside the gate | | | stays fixed (no cell cuts DD inside the gate) |
| P7 | london | 166 | M1_50_g15_c2_d10_c20_tb_B | +619 $/wk, DD +45.5%, ww +3969, stops 0.15(0.08), b5 74%, w2l 1 | n/a | L3M only |
| P7 | nyam | 58 | M1_75_g10_c1_d10_h_tb_N | +1506 $/wk, DD +74.0%, ww +3983, stops 0.08(0.38), b5 23%, w2l 1 | n/a | L3M only |
| U7 | asia | 72 | M1_75_g10_c1_d10_h_tb_N | +654 $/wk, DD +37.1%, ww +1407, stops 1.90(1.83), b5 88%, w2l 1 | n/a | L3M only |
| U7 | london | 49 | none inside the gate | | | stays fixed (no cell cuts DD inside the gate) |

Single-book and book x session cells (wave 3, clean test of item 2; same config as the wave-2 best; vs JN05W2 on the same book/session slice):
| cell | slice | L3M | L6M |
|---|---|---|---|
| M1_75_g05_c1_d10_c20_tb_B_bA7_sas | A7/as | -192 $/wk, DD +10.1%, ww +412, stops 5.10(4.03), b5 81%, w2l 0 | -374 $/wk, DD -36.6%, ww +412, stops 4.30(3.96), b5 93%, w2l 1 |
| M1_75_g10_c1_d10_c20_tb_B_bA7_sas | A7/as | +47 $/wk, DD +25.6%, ww +1495, stops 5.55(4.03), b5 65%, w2l 0 | -163 $/wk, DD -29.2%, ww +1253, stops 4.26(3.96), b5 74%, w2l 0 |
| M1_75_g05_c1_d10_c20_tb_N_bA7_sas | A7/as | -186 $/wk, DD +10.0%, ww +552, stops 5.10(4.03), b5 81%, w2l 0 | -268 $/wk, DD -15.8%, ww +552, stops 4.72(3.96), b5 87%, w2l 0 |
| M1_75_g10_c1_d10_c20_tb_N_bA7_sas | A7/as | -18 $/wk, DD +17.7%, ww +722, stops 5.63(4.03), b5 65%, w2l 0 | -219 $/wk, DD -19.1%, ww +722, stops 5.06(3.96), b5 86%, w2l 0 |
| M1_75_g05_c1_d10_c20_tb_W_bA7_sas | A7/as | -1 $/wk, DD +1.4%, ww -140, stops 4.03(4.03), b5 100%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bA7_sas | A7/as | -15 $/wk, DD +2.4%, ww -426, stops 3.96(4.03), b5 100%, w2l 0 | +2 $/wk, DD -13.6%, ww -426, stops 3.23(3.96), b5 88%, w2l 0 |
| M1_50_g10_c1_d10_c20_tb_N_bA7_sas | A7/as | -159 $/wk, DD -8.3%, ww +877, stops 5.93(4.03), b5 9%, w2l 3 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bA7_sas | A7/as | -48 $/wk, DD -3.0%, ww -426, stops 3.88(4.03), b5 100%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bH7_sas | H7/as | -574 $/wk, DD -92.7%, ww -2409, stops 0.53(0.23), b5 111%, w2l 4 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bH7_sas | H7/as | +177 $/wk, DD -33.6%, ww -1228, stops 0.61(0.23), b5 93%, w2l 2 | +650 $/wk, DD +6.5%, ww +1483, stops 0.57(0.42), b5 116%, w2l 4 |
| M1_75_g05_c1_d10_c20_tb_N_bH7_sas | H7/as | -697 $/wk, DD -92.7%, ww -2409, stops 0.53(0.23), b5 101%, w2l 4 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bH7_sas | H7/as | +244 $/wk, DD -33.6%, ww -1228, stops 0.53(0.23), b5 98%, w2l 2 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bH7_sas | H7/as | +123 $/wk, DD +0.0%, ww +0, stops 0.23(0.23), b5 110%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bH7_sas | H7/as | -67 $/wk, DD +0.0%, ww +0, stops 0.30(0.23), b5 95%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bH7_sas | H7/as | -355 $/wk, DD -120.5%, ww -2166, stops 0.53(0.23), b5 102%, w2l 4 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bH7_sas | H7/as | -312 $/wk, DD +0.0%, ww +0, stops 0.30(0.23), b5 74%, w2l 1 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bH7_sam | H7/am | +87 $/wk, DD +15.5%, ww +1898, stops 0.61(0.61), b5 97%, w2l 0 | +95 $/wk, DD -20.4%, ww -213, stops 0.84(0.84), b5 108%, w2l 0 |
| M1_75_g10_c1_d10_c20_tb_B_bH7_sam | H7/am | +281 $/wk, DD +12.6%, ww +1893, stops 0.53(0.61), b5 110%, w2l 1 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bH7_sam | H7/am | +77 $/wk, DD +15.5%, ww +1898, stops 0.61(0.61), b5 97%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bH7_sam | H7/am | +258 $/wk, DD +12.6%, ww +1893, stops 0.53(0.61), b5 110%, w2l 1 | +35 $/wk, DD -19.5%, ww +0, stops 0.84(0.84), b5 100%, w2l 1 |
| M1_75_g05_c1_d10_c20_tb_W_bH7_sam | H7/am | +11 $/wk, DD +0.0%, ww +0, stops 0.61(0.61), b5 100%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bH7_sam | H7/am | +22 $/wk, DD +0.0%, ww +0, stops 0.61(0.61), b5 100%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bH7_sam | H7/am | +252 $/wk, DD +13.2%, ww +1853, stops 0.53(0.61), b5 109%, w2l 1 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bH7_sam | H7/am | +30 $/wk, DD +0.8%, ww +0, stops 0.53(0.61), b5 100%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bK7_sas | K7/as | +1823 $/wk, DD -28.8%, ww -3232, stops 0.00(0.00), b5 119%, w2l 2 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bK7_sas | K7/as | +1292 $/wk, DD -46.3%, ww -1012, stops 0.15(0.00), b5 124%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bK7_sas | K7/as | +1877 $/wk, DD -19.6%, ww -2412, stops 0.00(0.00), b5 119%, w2l 2 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bK7_sas | K7/as | +912 $/wk, DD -46.3%, ww -1012, stops 0.15(0.00), b5 125%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bK7_sas | K7/as | -54 $/wk, DD -0.7%, ww -404, stops 0.00(0.00), b5 100%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bK7_sas | K7/as | +297 $/wk, DD +0.0%, ww +0, stops 0.00(0.00), b5 100%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bK7_sas | K7/as | +355 $/wk, DD -86.2%, ww -5644, stops 0.00(0.00), b5 127%, w2l 1 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bK7_sas | K7/as | -401 $/wk, DD -35.9%, ww +0, stops 0.00(0.00), b5 90%, w2l 1 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bK7_slo | K7/lo | -9 $/wk, DD +8.7%, ww +4326, stops 0.23(0.30), b5 91%, w2l 1 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bK7_slo | K7/lo | +481 $/wk, DD -25.5%, ww +4257, stops 0.38(0.30), b5 53%, w2l 3 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bK7_slo | K7/lo | -123 $/wk, DD -4.2%, ww +4733, stops 0.23(0.30), b5 82%, w2l 2 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bK7_slo | K7/lo | -31 $/wk, DD -42.3%, ww +4122, stops 0.38(0.30), b5 45%, w2l 3 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bK7_slo | K7/lo | +27 $/wk, DD +0.5%, ww +0, stops 0.30(0.30), b5 106%, w2l 1 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bK7_slo | K7/lo | +157 $/wk, DD -4.8%, ww +0, stops 0.30(0.30), b5 99%, w2l 1 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bK7_slo | K7/lo | -182 $/wk, DD -13.7%, ww +3097, stops 0.23(0.30), b5 45%, w2l 2 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bK7_slo | K7/lo | +431 $/wk, DD -3.3%, ww +0, stops 0.30(0.30), b5 103%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bK7_sam | K7/am | +672 $/wk, DD -0.0%, ww +0, stops 0.38(0.38), b5 103%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bK7_sam | K7/am | +879 $/wk, DD -0.0%, ww +0, stops 0.38(0.38), b5 107%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bK7_sam | K7/am | +535 $/wk, DD -0.0%, ww +0, stops 0.38(0.38), b5 100%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bK7_sam | K7/am | +703 $/wk, DD -0.0%, ww +0, stops 0.38(0.38), b5 103%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bK7_sam | K7/am | +137 $/wk, DD +0.0%, ww +0, stops 0.38(0.38), b5 103%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bK7_sam | K7/am | +176 $/wk, DD +0.0%, ww +0, stops 0.38(0.38), b5 104%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bK7_sam | K7/am | +416 $/wk, DD -0.0%, ww +0, stops 0.38(0.38), b5 102%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bK7_sam | K7/am | +252 $/wk, DD +0.0%, ww +0, stops 0.38(0.38), b5 105%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bK7_spm | K7/pm | -270 $/wk, DD -24.3%, ww +0, stops 0.30(0.38), b5 102%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bK7_spm | K7/pm | -184 $/wk, DD -15.3%, ww +0, stops 0.46(0.38), b5 105%, w2l 1 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bK7_spm | K7/pm | -266 $/wk, DD -24.6%, ww +0, stops 0.38(0.38), b5 102%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bK7_spm | K7/pm | -254 $/wk, DD -21.6%, ww +0, stops 0.53(0.38), b5 105%, w2l 1 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bK7_spm | K7/pm | -4 $/wk, DD +0.0%, ww +0, stops 0.30(0.38), b5 100%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bK7_spm | K7/pm | +70 $/wk, DD +0.0%, ww +0, stops 0.30(0.38), b5 100%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bK7_spm | K7/pm | +48 $/wk, DD -16.0%, ww +0, stops 0.53(0.38), b5 105%, w2l 1 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bK7_spm | K7/pm | +442 $/wk, DD -0.0%, ww +0, stops 0.30(0.38), b5 100%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bM7_slo | M7/lo | +1147 $/wk, DD -8.1%, ww +130, stops 1.07(0.91), b5 127%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bM7_slo | M7/lo | +1142 $/wk, DD -23.2%, ww -729, stops 0.91(0.91), b5 138%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bM7_slo | M7/lo | +417 $/wk, DD -10.9%, ww -1075, stops 1.14(0.91), b5 107%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bM7_slo | M7/lo | -366 $/wk, DD -20.4%, ww +80, stops 1.29(0.91), b5 79%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bM7_slo | M7/lo | +688 $/wk, DD +4.4%, ww +1400, stops 0.84(0.91), b5 119%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bM7_slo | M7/lo | +1614 $/wk, DD +4.9%, ww +1190, stops 0.53(0.91), b5 162%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bM7_slo | M7/lo | +476 $/wk, DD -19.9%, ww +1144, stops 1.45(0.91), b5 89%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bM7_slo | M7/lo | +538 $/wk, DD -1.3%, ww -80, stops 0.84(0.91), b5 134%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bM7_sam | M7/am | +23 $/wk, DD -9.0%, ww -2038, stops 1.22(1.14), b5 103%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bM7_sam | M7/am | +363 $/wk, DD -3.3%, ww -218, stops 1.37(1.14), b5 105%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bM7_sam | M7/am | +17 $/wk, DD -9.0%, ww -2038, stops 1.29(1.14), b5 103%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bM7_sam | M7/am | +346 $/wk, DD -3.3%, ww -218, stops 1.45(1.14), b5 105%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bM7_sam | M7/am | +6 $/wk, DD +0.0%, ww +0, stops 1.07(1.14), b5 100%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bM7_sam | M7/am | +16 $/wk, DD +0.0%, ww +0, stops 1.07(1.14), b5 100%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bM7_sam | M7/am | +383 $/wk, DD +0.3%, ww -530, stops 1.29(1.14), b5 108%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bM7_sam | M7/am | +6 $/wk, DD +0.0%, ww +0, stops 1.07(1.14), b5 100%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bP7_sas | P7/as | -5946 $/wk, DD -1.0%, ww +6944, stops 0.15(0.15), b5 50%, w2l 2 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bP7_sas | P7/as | -3315 $/wk, DD -36.1%, ww -13164, stops 0.53(0.15), b5 77%, w2l 2 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bP7_sas | P7/as | -5762 $/wk, DD -1.0%, ww +9022, stops 0.15(0.15), b5 50%, w2l 2 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bP7_sas | P7/as | -2696 $/wk, DD -7.8%, ww -10346, stops 0.53(0.15), b5 75%, w2l 2 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bP7_sas | P7/as | -184 $/wk, DD -4.9%, ww -2079, stops 0.15(0.15), b5 100%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bP7_sas | P7/as | -491 $/wk, DD -25.2%, ww -10331, stops 0.15(0.15), b5 102%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bP7_sas | P7/as | -3918 $/wk, DD -0.4%, ww -4286, stops 0.46(0.15), b5 71%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bP7_sas | P7/as | -816 $/wk, DD -22.6%, ww -9033, stops 0.15(0.15), b5 100%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bP7_slo | P7/lo | +894 $/wk, DD +29.6%, ww -1633, stops 0.08(0.08), b5 88%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bP7_slo | P7/lo | +1179 $/wk, DD -9.8%, ww -5408, stops 0.15(0.08), b5 114%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bP7_slo | P7/lo | +386 $/wk, DD +28.5%, ww -1328, stops 0.08(0.08), b5 76%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bP7_slo | P7/lo | +1322 $/wk, DD -14.4%, ww -5203, stops 0.15(0.08), b5 116%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bP7_slo | P7/lo | +385 $/wk, DD -1.9%, ww -238, stops 0.08(0.08), b5 112%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bP7_slo | P7/lo | -142 $/wk, DD +2.7%, ww -458, stops 0.08(0.08), b5 97%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bP7_slo | P7/lo | +927 $/wk, DD +19.7%, ww -3009, stops 0.08(0.08), b5 87%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bP7_slo | P7/lo | +265 $/wk, DD +1.1%, ww +0, stops 0.08(0.08), b5 110%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bP7_sam | P7/am | +105 $/wk, DD +0.0%, ww +0, stops 0.53(0.61), b5 96%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bP7_sam | P7/am | +697 $/wk, DD +0.0%, ww +0, stops 0.53(0.61), b5 94%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bP7_sam | P7/am | -13 $/wk, DD +0.0%, ww +0, stops 0.53(0.61), b5 95%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bP7_sam | P7/am | +543 $/wk, DD +0.0%, ww +0, stops 0.53(0.61), b5 94%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bP7_sam | P7/am | +118 $/wk, DD +0.0%, ww +0, stops 0.61(0.61), b5 100%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bP7_sam | P7/am | +16 $/wk, DD +0.0%, ww +0, stops 0.61(0.61), b5 99%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bP7_sam | P7/am | -544 $/wk, DD +0.0%, ww +0, stops 0.61(0.61), b5 95%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bU7_sas | U7/as | -800 $/wk, DD +6.6%, ww -2883, stops 2.05(1.83), b5 92%, w2l 2 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bU7_sas | U7/as | +71 $/wk, DD +8.3%, ww -1836, stops 1.98(1.83), b5 93%, w2l 3 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bU7_sas | U7/as | -162 $/wk, DD +6.6%, ww +57, stops 2.05(1.83), b5 92%, w2l 1 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bU7_sas | U7/as | +502 $/wk, DD +8.3%, ww +983, stops 1.98(1.83), b5 92%, w2l 2 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bU7_sas | U7/as | -637 $/wk, DD +0.0%, ww -2883, stops 1.83(1.83), b5 100%, w2l 1 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bU7_sas | U7/as | -431 $/wk, DD +0.0%, ww -1836, stops 1.83(1.83), b5 101%, w2l 1 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bU7_sas | U7/as | +1222 $/wk, DD +15.6%, ww -265, stops 1.90(1.83), b5 88%, w2l 2 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bU7_sas | U7/as | -648 $/wk, DD +0.0%, ww -2883, stops 1.83(1.83), b5 100%, w2l 2 | n/a |
| M1_75_g05_c1_d10_c20_tb_B_bU7_slo | U7/lo | -891 $/wk, DD -25.4%, ww -3538, stops 1.52(1.45), b5 50%, w2l 2 | n/a |
| M1_75_g10_c1_d10_c20_tb_B_bU7_slo | U7/lo | -1728 $/wk, DD -105.5%, ww -7540, stops 1.60(1.45), b5 59%, w2l 2 | n/a |
| M1_75_g05_c1_d10_c20_tb_N_bU7_slo | U7/lo | +393 $/wk, DD +17.2%, ww +1796, stops 1.45(1.45), b5 91%, w2l 0 | n/a |
| M1_75_g10_c1_d10_c20_tb_N_bU7_slo | U7/lo | +246 $/wk, DD +3.1%, ww -1185, stops 1.45(1.45), b5 97%, w2l 0 | n/a |
| M1_75_g05_c1_d10_c20_tb_W_bU7_slo | U7/lo | -1284 $/wk, DD -44.3%, ww -6280, stops 1.52(1.45), b5 59%, w2l 2 | n/a |
| M1_75_g10_c1_d10_c20_tb_W_bU7_slo | U7/lo | -1975 $/wk, DD -109.8%, ww -6355, stops 1.60(1.45), b5 63%, w2l 2 | n/a |
| M1_50_g10_c1_d10_c20_tb_N_bU7_slo | U7/lo | -41 $/wk, DD -9.9%, ww -1991, stops 1.52(1.45), b5 102%, w2l 0 | n/a |
| M1_50_g10_c1_d10_c20_tb_W_bU7_slo | U7/lo | -839 $/wk, DD -33.9%, ww -4122, stops 1.37(1.45), b5 81%, w2l 1 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_tcq50T75 | A7/as | -17 $/wk, DD +0.0%, ww +0, stops 4.03(4.03), b5 98%, w2l 0 | n/a |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x40 | A7/as | +205 $/wk, DD +24.7%, ww +2588, stops 6.62(4.03), b5 38%, w2l 2 | +400 $/wk, DD +24.7%, ww +2274, stops 6.96(3.96), b5 104%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x60 | A7/as | -373 $/wk, DD -2.3%, ww +1411, stops 4.49(4.03), b5 47%, w2l 2 | -111 $/wk, DD -19.9%, ww +1207, stops 4.34(3.96), b5 98%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x90 | A7/as | -20 $/wk, DD -34.2%, ww -532, stops 1.52(4.03), b5 113%, w2l 3 | -415 $/wk, DD -93.7%, ww -532, stops 1.60(3.96), b5 94%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx60x40 | A7/as | +879 $/wk, DD +38.1%, ww +2338, stops 6.24(4.03), b5 67%, w2l 1 | +620 $/wk, DD +18.3%, ww -327, stops 6.73(3.96), b5 113%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx60x90 | A7/as | -23 $/wk, DD -68.2%, ww -4785, stops 1.45(4.03), b5 133%, w2l 1 | -86 $/wk, DD -127.0%, ww -4785, stops 1.37(3.96), b5 86%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx85x40 | A7/as | -159 $/wk, DD -54.1%, ww -2126, stops 6.54(4.03), b5 75%, w2l 3 | -39 $/wk, DD -90.5%, ww -2126, stops 6.73(3.96), b5 114%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx85x60 | A7/as | -614 $/wk, DD -87.0%, ww -2571, stops 4.41(4.03), b5 89%, w2l 3 | -384 $/wk, DD -176.9%, ww -2571, stops 3.99(3.96), b5 99%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx85x90 | A7/as | -944 $/wk, DD -175.4%, ww -3751, stops 1.37(4.03), b5 73%, w2l 3 | -235 $/wk, DD -260.9%, ww -3751, stops 1.26(3.96), b5 92%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx40x40 | H7/as | -350 $/wk, DD -97.5%, ww -2100, stops 0.53(0.23), b5 115%, w2l 4 | -546 $/wk, DD -29.3%, ww +2102, stops 0.80(0.42), b5 65%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx40x60 | H7/as | -311 $/wk, DD -42.9%, ww -1200, stops 0.30(0.23), b5 65%, w2l 3 | -623 $/wk, DD +2.3%, ww +2567, stops 0.49(0.42), b5 64%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx40x90 | H7/as | -393 $/wk, DD +47.1%, ww +341, stops 0.23(0.23), b5 52%, w2l 2 | -634 $/wk, DD +19.0%, ww +3419, stops 0.11(0.42), b5 41%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx60x40 | H7/as | -205 $/wk, DD -91.8%, ww -2847, stops 0.53(0.23), b5 167%, w2l 3 | -32 $/wk, DD -25.6%, ww +1674, stops 0.76(0.42), b5 116%, w2l 6 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx60x90 | H7/as | -720 $/wk, DD +4.5%, ww -1633, stops 0.23(0.23), b5 21%, w2l 5 | -673 $/wk, DD +20.7%, ww +1566, stops 0.11(0.42), b5 62%, w2l 6 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx85x40 | H7/as | +151 $/wk, DD -129.9%, ww -2100, stops 0.61(0.23), b5 215%, w2l 4 | +241 $/wk, DD -50.5%, ww +2102, stops 0.80(0.42), b5 106%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx85x60 | H7/as | -336 $/wk, DD -59.3%, ww -2623, stops 0.30(0.23), b5 116%, w2l 4 | -265 $/wk, DD -6.6%, ww +0, stops 0.49(0.42), b5 88%, w2l 7 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx85x90 | H7/as | -1014 $/wk, DD -17.5%, ww -4123, stops 0.30(0.23), b5 41%, w2l 6 | -731 $/wk, DD +1.4%, ww +398, stops 0.15(0.42), b5 53%, w2l 8 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx40x40 | H7/am | +23 $/wk, DD -31.6%, ww +1516, stops 0.61(0.61), b5 120%, w2l 1 | +79 $/wk, DD -6.0%, ww +1937, stops 0.88(0.84), b5 108%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx40x60 | H7/am | +201 $/wk, DD +13.6%, ww +1980, stops 0.38(0.61), b5 100%, w2l 1 | -8 $/wk, DD +2.6%, ww +1138, stops 0.72(0.84), b5 97%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx40x90 | H7/am | +112 $/wk, DD +1.8%, ww +1980, stops 0.23(0.61), b5 94%, w2l 1 | -67 $/wk, DD -2.3%, ww +1138, stops 0.57(0.84), b5 101%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx60x40 | H7/am | -307 $/wk, DD -106.7%, ww -1634, stops 0.84(0.61), b5 129%, w2l 1 | -68 $/wk, DD -35.5%, ww -1173, stops 1.07(0.84), b5 108%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx60x90 | H7/am | -9 $/wk, DD -0.5%, ww +1614, stops 0.38(0.61), b5 91%, w2l 0 | -12 $/wk, DD -6.6%, ww -213, stops 0.65(0.84), b5 105%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx85x40 | H7/am | -265 $/wk, DD -106.7%, ww -1634, stops 0.91(0.61), b5 130%, w2l 1 | +276 $/wk, DD -35.5%, ww -1173, stops 1.10(0.84), b5 117%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx85x60 | H7/am | -138 $/wk, DD -39.2%, ww +0, stops 0.76(0.61), b5 98%, w2l 1 | +121 $/wk, DD +4.2%, ww +0, stops 0.91(0.84), b5 104%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx85x90 | H7/am | -323 $/wk, DD -66.9%, ww +1270, stops 0.53(0.61), b5 85%, w2l 1 | +41 $/wk, DD -9.5%, ww -213, stops 0.72(0.84), b5 110%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx40x40 | K7/as | +2200 $/wk, DD -27.4%, ww -2748, stops 0.08(0.00), b5 154%, w2l 1 | +2615 $/wk, DD -21.0%, ww -4436, stops 0.46(0.08), b5 110%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx40x60 | K7/as | +1019 $/wk, DD -23.2%, ww -2510, stops 0.00(0.00), b5 89%, w2l 1 | +841 $/wk, DD +1.5%, ww -1768, stops 0.08(0.08), b5 81%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx40x90 | K7/as | -1386 $/wk, DD -74.1%, ww -8079, stops 0.08(0.00), b5 26%, w2l 3 | -1634 $/wk, DD -34.2%, ww -4193, stops 0.04(0.08), b5 41%, w2l 6 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx60x40 | K7/as | +2577 $/wk, DD -42.7%, ww -6350, stops 0.15(0.00), b5 161%, w2l 3 | +2934 $/wk, DD +6.2%, ww -2464, stops 0.49(0.08), b5 134%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx60x90 | K7/as | -1015 $/wk, DD -79.0%, ww -2751, stops 0.00(0.00), b5 47%, w2l 2 | -358 $/wk, DD -34.0%, ww +1135, stops 0.00(0.08), b5 70%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx85x40 | K7/as | +2627 $/wk, DD -107.1%, ww -13878, stops 0.00(0.00), b5 118%, w2l 3 | +3367 $/wk, DD -44.0%, ww -9992, stops 0.38(0.08), b5 143%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx85x60 | K7/as | +42 $/wk, DD -42.9%, ww -5353, stops 0.00(0.00), b5 36%, w2l 3 | +1029 $/wk, DD -26.4%, ww -3515, stops 0.08(0.08), b5 113%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sas_fx85x90 | K7/as | -637 $/wk, DD -7.8%, ww -3407, stops 0.00(0.00), b5 20%, w2l 3 | +821 $/wk, DD +19.8%, ww +480, stops 0.00(0.08), b5 72%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx40x40 | K7/lo | -636 $/wk, DD -128.9%, ww -1301, stops 0.53(0.30), b5 -16%, w2l 5 | -1500 $/wk, DD -294.8%, ww -1301, stops 0.42(0.27), b5 1%, w2l 10 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx40x60 | K7/lo | +294 $/wk, DD +29.6%, ww -309, stops 0.08(0.30), b5 44%, w2l 2 | +155 $/wk, DD +12.7%, ww -309, stops 0.15(0.27), b5 55%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx40x90 | K7/lo | -653 $/wk, DD -21.1%, ww +4018, stops 0.08(0.30), b5 -11%, w2l 4 | -1042 $/wk, DD -114.8%, ww +3418, stops 0.08(0.27), b5 1%, w2l 7 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx60x40 | K7/lo | -867 $/wk, DD -63.8%, ww +1839, stops 0.61(0.30), b5 59%, w2l 3 | -1438 $/wk, DD -193.9%, ww -2533, stops 0.57(0.27), b5 51%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx60x90 | K7/lo | -908 $/wk, DD -13.7%, ww +5133, stops 0.15(0.30), b5 32%, w2l 2 | -642 $/wk, DD -45.8%, ww +3893, stops 0.08(0.27), b5 68%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx85x40 | K7/lo | -545 $/wk, DD -129.7%, ww -2936, stops 0.53(0.30), b5 13%, w2l 4 | -2467 $/wk, DD -482.9%, ww -4381, stops 0.53(0.27), b5 -25%, w2l 9 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx85x60 | K7/lo | -162 $/wk, DD +20.8%, ww +4081, stops 0.46(0.30), b5 40%, w2l 2 | -600 $/wk, DD -46.0%, ww +1757, stops 0.38(0.27), b5 4%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_fx85x90 | K7/lo | -1172 $/wk, DD -8.8%, ww +2119, stops 0.23(0.30), b5 -22%, w2l 4 | -1026 $/wk, DD -95.7%, ww +2119, stops 0.15(0.27), b5 -27%, w2l 8 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_fx40x40 | K7/am | +1701 $/wk, DD -3.6%, ww -522, stops 0.53(0.38), b5 104%, w2l 0 | -117 $/wk, DD +14.2%, ww -836, stops 0.72(0.46), b5 89%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_fx40x60 | K7/am | +1360 $/wk, DD +0.0%, ww +0, stops 0.38(0.38), b5 105%, w2l 0 | +457 $/wk, DD +13.6%, ww -390, stops 0.46(0.46), b5 95%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_fx40x90 | K7/am | +1057 $/wk, DD -2.6%, ww -105, stops 0.38(0.38), b5 107%, w2l 0 | +562 $/wk, DD +8.4%, ww -1130, stops 0.42(0.46), b5 94%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_fx60x40 | K7/am | +974 $/wk, DD -3.6%, ww -522, stops 0.61(0.38), b5 109%, w2l 1 | -332 $/wk, DD -9.4%, ww -522, stops 0.76(0.46), b5 100%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_fx60x90 | K7/am | -137 $/wk, DD -21.9%, ww -105, stops 0.38(0.38), b5 103%, w2l 2 | -327 $/wk, DD -9.4%, ww -330, stops 0.42(0.46), b5 98%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_fx85x40 | K7/am | +974 $/wk, DD -9.3%, ww -1751, stops 0.53(0.38), b5 102%, w2l 0 | -365 $/wk, DD +5.3%, ww -1751, stops 0.72(0.46), b5 94%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_fx85x60 | K7/am | -270 $/wk, DD -15.2%, ww -1528, stops 0.38(0.38), b5 95%, w2l 0 | -155 $/wk, DD +7.4%, ww -1528, stops 0.46(0.46), b5 93%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_fx85x90 | K7/am | -1093 $/wk, DD -60.0%, ww -2500, stops 0.38(0.38), b5 89%, w2l 1 | -929 $/wk, DD -14.7%, ww -2500, stops 0.42(0.46), b5 93%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_spm_fx40x40 | K7/pm | -113 $/wk, DD -11.0%, ww +0, stops 0.38(0.38), b5 101%, w2l 2 | -17 $/wk, DD +20.4%, ww +0, stops 0.49(0.46), b5 103%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_spm_fx40x60 | K7/pm | -167 $/wk, DD -0.0%, ww +0, stops 0.38(0.38), b5 95%, w2l 1 | -75 $/wk, DD +6.9%, ww +0, stops 0.46(0.46), b5 104%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_spm_fx40x90 | K7/pm | +189 $/wk, DD +0.0%, ww +0, stops 0.30(0.38), b5 94%, w2l 0 | -367 $/wk, DD +10.3%, ww -316, stops 0.42(0.46), b5 95%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_spm_fx60x40 | K7/pm | +247 $/wk, DD -20.5%, ww +0, stops 0.38(0.38), b5 105%, w2l 1 | +323 $/wk, DD +6.2%, ww +0, stops 0.49(0.46), b5 107%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_spm_fx60x90 | K7/pm | +75 $/wk, DD +0.0%, ww +0, stops 0.30(0.38), b5 93%, w2l 1 | -307 $/wk, DD -1.9%, ww +0, stops 0.42(0.46), b5 95%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_spm_fx85x40 | K7/pm | +718 $/wk, DD -34.3%, ww +0, stops 0.38(0.38), b5 116%, w2l 1 | +1235 $/wk, DD +3.7%, ww +0, stops 0.49(0.46), b5 107%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_spm_fx85x60 | K7/pm | +167 $/wk, DD -3.3%, ww +0, stops 0.38(0.38), b5 106%, w2l 0 | +524 $/wk, DD -12.3%, ww -2618, stops 0.46(0.46), b5 102%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_spm_fx85x90 | K7/pm | -2 $/wk, DD +0.0%, ww +0, stops 0.30(0.38), b5 95%, w2l 1 | -10 $/wk, DD +13.8%, ww +0, stops 0.38(0.46), b5 100%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_slo_fx40x40 | M7/lo | -2038 $/wk, DD -44.1%, ww -1957, stops 1.90(0.91), b5 60%, w2l 3 | -863 $/wk, DD -80.0%, ww -1957, stops 2.17(0.84), b5 79%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_slo_fx40x60 | M7/lo | -505 $/wk, DD +24.7%, ww +4006, stops 0.68(0.91), b5 47%, w2l 2 | +586 $/wk, DD +24.7%, ww +4006, stops 0.68(0.84), b5 84%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_slo_fx40x90 | M7/lo | -243 $/wk, DD +27.6%, ww +4508, stops 0.23(0.91), b5 65%, w2l 0 | +82 $/wk, DD +19.2%, ww +4508, stops 0.19(0.84), b5 62%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_slo_fx60x40 | M7/lo | -143 $/wk, DD -35.0%, ww -7887, stops 1.98(0.91), b5 126%, w2l 1 | -462 $/wk, DD -59.1%, ww -7887, stops 2.28(0.84), b5 124%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_slo_fx60x90 | M7/lo | +456 $/wk, DD +24.4%, ww +2810, stops 0.15(0.91), b5 98%, w2l 0 | +203 $/wk, DD +24.1%, ww +2810, stops 0.23(0.84), b5 79%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_slo_fx85x40 | M7/lo | -782 $/wk, DD -57.9%, ww -5887, stops 1.90(0.91), b5 62%, w2l 3 | +188 $/wk, DD -109.7%, ww -5887, stops 1.98(0.84), b5 86%, w2l 6 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_slo_fx85x60 | M7/lo | -862 $/wk, DD -13.2%, ww +1000, stops 0.99(0.91), b5 42%, w2l 1 | -634 $/wk, DD -87.2%, ww +1000, stops 0.76(0.84), b5 45%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_slo_fx85x90 | M7/lo | +656 $/wk, DD +25.6%, ww +4310, stops 0.30(0.91), b5 101%, w2l 0 | +947 $/wk, DD +13.2%, ww +4310, stops 0.30(0.84), b5 72%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_sam_fx40x40 | M7/am | +16 $/wk, DD +0.0%, ww +576, stops 1.60(1.14), b5 101%, w2l 1 | -1471 $/wk, DD -96.6%, ww -771, stops 2.02(1.26), b5 93%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_sam_fx40x60 | M7/am | -641 $/wk, DD -1.0%, ww -1093, stops 1.14(1.14), b5 80%, w2l 1 | -824 $/wk, DD -28.2%, ww -1093, stops 1.22(1.26), b5 86%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_sam_fx40x90 | M7/am | -941 $/wk, DD -9.5%, ww -2243, stops 1.14(1.14), b5 87%, w2l 0 | -993 $/wk, DD -54.0%, ww -2243, stops 1.03(1.26), b5 96%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_sam_fx60x40 | M7/am | +584 $/wk, DD -16.4%, ww -1769, stops 1.67(1.14), b5 136%, w2l 1 | -622 $/wk, DD -83.7%, ww -1769, stops 1.98(1.26), b5 114%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_sam_fx60x90 | M7/am | -694 $/wk, DD -10.3%, ww -737, stops 1.14(1.14), b5 96%, w2l 0 | -507 $/wk, DD -37.6%, ww -737, stops 1.03(1.26), b5 101%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_sam_fx85x40 | M7/am | +680 $/wk, DD -19.9%, ww -2720, stops 1.67(1.14), b5 123%, w2l 1 | -419 $/wk, DD -38.8%, ww -2720, stops 2.02(1.26), b5 108%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_sam_fx85x60 | M7/am | +145 $/wk, DD -5.3%, ww -2264, stops 1.14(1.14), b5 102%, w2l 0 | +363 $/wk, DD -4.5%, ww -2264, stops 1.26(1.26), b5 109%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_sam_fx85x90 | M7/am | -39 $/wk, DD -2.5%, ww -3020, stops 1.14(1.14), b5 106%, w2l 0 | +195 $/wk, DD -1.7%, ww -3020, stops 1.03(1.26), b5 117%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_fx40x40 | P7/as | -1998 $/wk, DD +2.2%, ww +3504, stops 0.38(0.15), b5 77%, w2l 2 | -2485 $/wk, DD -139.6%, ww +3504, stops 0.38(0.08), b5 76%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_fx40x60 | P7/as | +1709 $/wk, DD -10.8%, ww -4303, stops 0.08(0.15), b5 86%, w2l 1 | -173 $/wk, DD -10.8%, ww -4303, stops 0.04(0.08), b5 75%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_fx40x90 | P7/as | -276 $/wk, DD -16.0%, ww -6252, stops 0.00(0.15), b5 69%, w2l 3 | -2594 $/wk, DD -16.0%, ww -6252, stops 0.00(0.08), b5 64%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_fx60x40 | P7/as | -22 $/wk, DD -8.9%, ww +3400, stops 0.61(0.15), b5 87%, w2l 1 | -731 $/wk, DD -91.8%, ww +3400, stops 0.57(0.08), b5 100%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_fx60x90 | P7/as | -748 $/wk, DD -21.0%, ww -8247, stops 0.00(0.15), b5 70%, w2l 1 | -3283 $/wk, DD -21.0%, ww -8247, stops 0.00(0.08), b5 76%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_fx85x40 | P7/as | -2998 $/wk, DD -56.3%, ww -581, stops 0.68(0.15), b5 90%, w2l 2 | -2074 $/wk, DD -95.9%, ww -581, stops 0.72(0.08), b5 85%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_fx85x60 | P7/as | +1657 $/wk, DD -26.7%, ww -10608, stops 0.30(0.15), b5 107%, w2l 1 | +1783 $/wk, DD -26.7%, ww -10608, stops 0.19(0.08), b5 96%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_fx85x90 | P7/as | -1216 $/wk, DD -15.2%, ww -5963, stops 0.00(0.15), b5 62%, w2l 1 | -4208 $/wk, DD -15.2%, ww -5963, stops 0.08(0.08), b5 62%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_slo_fx40x40 | P7/lo | -646 $/wk, DD -23.7%, ww -9688, stops 0.15(0.08), b5 85%, w2l 3 | -1137 $/wk, DD -118.0%, ww -9688, stops 0.23(0.19), b5 91%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_slo_fx40x60 | P7/lo | +991 $/wk, DD +42.4%, ww -57, stops 0.08(0.08), b5 75%, w2l 0 | +158 $/wk, DD +7.8%, ww -57, stops 0.08(0.19), b5 82%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_slo_fx40x90 | P7/lo | -818 $/wk, DD +54.1%, ww +2856, stops 0.08(0.08), b5 48%, w2l 2 | -301 $/wk, DD +46.5%, ww +2330, stops 0.08(0.19), b5 56%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_slo_fx60x40 | P7/lo | -1503 $/wk, DD -73.4%, ww -9391, stops 0.15(0.08), b5 111%, w2l 1 | -1951 $/wk, DD -182.9%, ww -9391, stops 0.23(0.19), b5 104%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_slo_fx60x90 | P7/lo | -968 $/wk, DD +16.1%, ww +756, stops 0.08(0.08), b5 86%, w2l 2 | -775 $/wk, DD -2.6%, ww -1655, stops 0.15(0.19), b5 71%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_slo_fx85x40 | P7/lo | -2397 $/wk, DD -40.0%, ww -11199, stops 0.30(0.08), b5 34%, w2l 2 | -2714 $/wk, DD -202.1%, ww -11199, stops 0.30(0.19), b5 21%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_slo_fx85x60 | P7/lo | -461 $/wk, DD +14.4%, ww +1011, stops 0.23(0.08), b5 64%, w2l 0 | -1331 $/wk, DD -83.0%, ww -3165, stops 0.27(0.19), b5 31%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_slo_fx85x90 | P7/lo | -940 $/wk, DD +28.1%, ww +2210, stops 0.23(0.08), b5 75%, w2l 0 | -219 $/wk, DD +28.1%, ww +497, stops 0.23(0.19), b5 52%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_fx40x40 | P7/am | -905 $/wk, DD +0.0%, ww +0, stops 0.46(0.61), b5 89%, w2l 0 | -942 $/wk, DD +0.0%, ww +0, stops 0.49(0.49), b5 93%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_fx40x60 | P7/am | -182 $/wk, DD +0.0%, ww +0, stops 0.53(0.61), b5 98%, w2l 0 | -1 $/wk, DD +0.0%, ww +0, stops 0.46(0.49), b5 96%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_fx40x90 | P7/am | -139 $/wk, DD +0.0%, ww +0, stops 0.30(0.61), b5 102%, w2l 0 | -205 $/wk, DD +0.0%, ww +0, stops 0.38(0.49), b5 95%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_fx60x40 | P7/am | -441 $/wk, DD +0.0%, ww +0, stops 0.46(0.61), b5 92%, w2l 0 | +70 $/wk, DD +0.0%, ww +0, stops 0.49(0.49), b5 98%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_fx60x90 | P7/am | -519 $/wk, DD +0.0%, ww +0, stops 0.30(0.61), b5 102%, w2l 1 | -224 $/wk, DD +0.0%, ww +0, stops 0.38(0.49), b5 100%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_fx85x40 | P7/am | -1404 $/wk, DD +0.0%, ww +0, stops 0.53(0.61), b5 80%, w2l 0 | -803 $/wk, DD +0.0%, ww +0, stops 0.53(0.49), b5 93%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_fx85x60 | P7/am | -1227 $/wk, DD +0.0%, ww +0, stops 0.68(0.61), b5 83%, w2l 0 | -215 $/wk, DD +0.0%, ww +0, stops 0.53(0.49), b5 97%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_fx85x90 | P7/am | -824 $/wk, DD +0.0%, ww +0, stops 0.38(0.61), b5 94%, w2l 1 | +152 $/wk, DD +0.0%, ww +0, stops 0.42(0.49), b5 101%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx40x40 | U7/as | +1733 $/wk, DD +30.8%, ww -4307, stops 1.75(1.83), b5 114%, w2l 2 | +1503 $/wk, DD +30.8%, ww +260, stops 2.09(1.83), b5 110%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx40x60 | U7/as | -178 $/wk, DD +35.0%, ww +1288, stops 1.45(1.83), b5 79%, w2l 2 | +147 $/wk, DD +35.0%, ww +3310, stops 1.37(1.83), b5 86%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx40x90 | U7/as | -1860 $/wk, DD -31.7%, ww -1661, stops 0.76(1.83), b5 53%, w2l 2 | -678 $/wk, DD -31.7%, ww +2542, stops 0.65(1.83), b5 66%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx60x40 | U7/as | +920 $/wk, DD -22.1%, ww -3107, stops 2.59(1.83), b5 121%, w2l 3 | +1009 $/wk, DD -24.8%, ww -2681, stops 2.89(1.83), b5 117%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx60x90 | U7/as | -2913 $/wk, DD -36.2%, ww -6366, stops 0.84(1.83), b5 56%, w2l 4 | -1600 $/wk, DD -36.2%, ww -1838, stops 0.76(1.83), b5 61%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx85x40 | U7/as | +355 $/wk, DD -65.8%, ww -7904, stops 2.89(1.83), b5 139%, w2l 5 | +1392 $/wk, DD -153.6%, ww -3337, stops 3.20(1.83), b5 100%, w2l 6 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx85x60 | U7/as | -3502 $/wk, DD -115.3%, ww -8377, stops 2.43(1.83), b5 77%, w2l 5 | -941 $/wk, DD -192.1%, ww -3810, stops 2.21(1.83), b5 59%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx85x90 | U7/as | -3324 $/wk, DD -105.3%, ww -7522, stops 0.99(1.83), b5 70%, w2l 4 | -1303 $/wk, DD -159.6%, ww -2955, stops 0.88(1.83), b5 43%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_slo_fx40x40 | U7/lo | -96 $/wk, DD -41.7%, ww -2340, stops 1.52(1.45), b5 65%, w2l 1 | -448 $/wk, DD -80.2%, ww -9069, stops 1.86(1.60), b5 82%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_slo_fx40x60 | U7/lo | -136 $/wk, DD +39.0%, ww +931, stops 1.07(1.45), b5 66%, w2l 0 | -782 $/wk, DD -8.2%, ww -2521, stops 1.33(1.60), b5 59%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_slo_fx40x90 | U7/lo | +201 $/wk, DD +39.9%, ww +398, stops 0.61(1.45), b5 65%, w2l 0 | -459 $/wk, DD -29.8%, ww -1075, stops 0.84(1.60), b5 56%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_slo_fx60x40 | U7/lo | +467 $/wk, DD -23.3%, ww +860, stops 1.75(1.45), b5 86%, w2l 1 | +596 $/wk, DD -23.3%, ww -7869, stops 2.05(1.60), b5 110%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_slo_fx60x90 | U7/lo | -32 $/wk, DD -12.7%, ww -2350, stops 0.68(1.45), b5 82%, w2l 0 | -350 $/wk, DD -12.7%, ww -896, stops 0.99(1.60), b5 71%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_slo_fx85x40 | U7/lo | +657 $/wk, DD -50.8%, ww -1813, stops 1.90(1.45), b5 80%, w2l 1 | -1502 $/wk, DD -374.1%, ww -8247, stops 2.32(1.60), b5 41%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_slo_fx85x60 | U7/lo | -1165 $/wk, DD -102.3%, ww -4462, stops 1.67(1.45), b5 70%, w2l 1 | -2222 $/wk, DD -236.5%, ww -5405, stops 1.98(1.60), b5 30%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_slo_fx85x90 | U7/lo | -1307 $/wk, DD -134.1%, ww -850, stops 0.84(1.45), b5 51%, w2l 3 | -661 $/wk, DD -134.1%, ww +604, stops 1.10(1.60), b5 36%, w2l 6 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x40s1 | A7/as | -85 $/wk, DD -17.0%, ww +673, stops 5.48(4.03), b5 64%, w2l 2 | +80 $/wk, DD -17.0%, ww -2130, stops 5.36(3.96), b5 118%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x40s2 | A7/as | +111 $/wk, DD +22.4%, ww +517, stops 5.25(4.03), b5 89%, w2l 0 | -160 $/wk, DD +10.2%, ww +517, stops 5.21(3.96), b5 93%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x40s3 | A7/as | +243 $/wk, DD +29.7%, ww -1424, stops 4.95(4.03), b5 61%, w2l 1 | +81 $/wk, DD +12.5%, ww -1424, stops 5.17(3.96), b5 100%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x90s1 | A7/as | -23 $/wk, DD -0.7%, ww +1475, stops 3.12(4.03), b5 82%, w2l 0 | +232 $/wk, DD -15.1%, ww +1475, stops 2.97(3.96), b5 107%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x90s2 | A7/as | +55 $/wk, DD -19.0%, ww +1866, stops 2.74(4.03), b5 135%, w2l 2 | -540 $/wk, DD -41.4%, ww +1265, stops 3.04(3.96), b5 95%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x90s3 | A7/as | +10 $/wk, DD -16.9%, ww -660, stops 3.20(4.03), b5 94%, w2l 1 | -41 $/wk, DD -53.6%, ww -660, stops 2.89(3.96), b5 103%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx40x40s1 | U7/as | +77 $/wk, DD -2.7%, ww -1716, stops 1.90(1.83), b5 106%, w2l 1 | +514 $/wk, DD -6.6%, ww +2851, stops 1.98(1.83), b5 104%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx40x40s2 | U7/as | +1223 $/wk, DD +0.1%, ww -427, stops 1.67(1.83), b5 120%, w2l 2 | +427 $/wk, DD -9.2%, ww -2199, stops 2.02(1.83), b5 114%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx40x40s3 | U7/as | +1405 $/wk, DD +2.6%, ww -349, stops 1.67(1.83), b5 127%, w2l 1 | +773 $/wk, DD -20.1%, ww -4846, stops 1.94(1.83), b5 124%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40 | A7/as | +128 $/wk, DD +12.5%, ww +2821, stops 7.53(4.03), b5 31%, w2l 2 | +401 $/wk, DD +12.5%, ww +2050, stops 7.88(3.96), b5 107%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40s101 | A7/as | +141 $/wk, DD -29.6%, ww +3271, stops 5.78(4.03), b5 62%, w2l 3 | +56 $/wk, DD -29.6%, ww +1628, stops 5.86(3.96), b5 83%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40s102 | A7/as | -734 $/wk, DD -56.0%, ww +189, stops 5.78(4.03), b5 66%, w2l 2 | -842 $/wk, DD -56.0%, ww +189, stops 5.59(3.96), b5 62%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx40x40s103 | A7/as | +433 $/wk, DD +7.5%, ww +3108, stops 5.48(4.03), b5 88%, w2l 1 | +136 $/wk, DD +7.5%, ww +1569, stops 5.44(3.96), b5 80%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40 | U7/as | +817 $/wk, DD +33.5%, ww -3187, stops 2.05(1.83), b5 98%, w2l 2 | +483 $/wk, DD +25.8%, ww +1380, stops 2.32(1.83), b5 101%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40s101 | U7/as | -1182 $/wk, DD -9.2%, ww -3181, stops 2.13(1.83), b5 78%, w2l 2 | -1103 $/wk, DD -9.2%, ww -2122, stops 2.17(1.83), b5 84%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40s102 | U7/as | -401 $/wk, DD +5.1%, ww -695, stops 2.05(1.83), b5 84%, w2l 2 | -926 $/wk, DD -6.4%, ww +3231, stops 2.21(1.83), b5 85%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_JL2_pol_fx40x40s103 | U7/as | +315 $/wk, DD +11.3%, ww -735, stops 1.90(1.83), b5 104%, w2l 1 | +49 $/wk, DD +9.3%, ww +1362, stops 2.02(1.83), b5 114%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40 | K7/am | +1028 $/wk, DD -2.2%, ww +2449, stops 3.65(0.38), b5 98%, w2l 1 | +23 $/wk, DD +25.9%, ww -1431, stops 3.69(0.46), b5 75%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40s101 | K7/am | +654 $/wk, DD +6.0%, ww +3031, stops 1.98(0.38), b5 102%, w2l 1 | +50 $/wk, DD +32.6%, ww +428, stops 2.24(0.46), b5 80%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40s102 | K7/am | +693 $/wk, DD +0.6%, ww -137, stops 2.13(0.38), b5 99%, w2l 1 | -168 $/wk, DD +28.8%, ww -137, stops 2.17(0.46), b5 71%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x40s103 | K7/am | +93 $/wk, DD +3.2%, ww +251, stops 1.67(0.38), b5 94%, w2l 1 | -345 $/wk, DD +24.4%, ww +251, stops 2.02(0.46), b5 69%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60 | K7/am | +697 $/wk, DD +3.2%, ww +2449, stops 0.53(0.38), b5 95%, w2l 1 | -52 $/wk, DD +30.7%, ww +1423, stops 0.53(0.46), b5 70%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60s101 | K7/am | +375 $/wk, DD +6.0%, ww +3249, stops 0.53(0.38), b5 98%, w2l 1 | -35 $/wk, DD +32.6%, ww +1423, stops 0.53(0.46), b5 74%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60s102 | K7/am | +500 $/wk, DD +6.0%, ww +1668, stops 0.53(0.38), b5 93%, w2l 1 | -199 $/wk, DD +32.6%, ww +1668, stops 0.53(0.46), b5 70%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60s103 | K7/am | +53 $/wk, DD +3.2%, ww +1268, stops 0.53(0.38), b5 94%, w2l 1 | -184 $/wk, DD +28.0%, ww +1268, stops 0.53(0.46), b5 71%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60 | K7/lo | -651 $/wk, DD +4.9%, ww -812, stops 0.08(0.30), b5 33%, w2l 2 | -619 $/wk, DD -16.1%, ww -812, stops 0.15(0.27), b5 43%, w2l 5 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60s101 | K7/lo | -21 $/wk, DD -7.4%, ww -349, stops 0.30(0.30), b5 76%, w2l 1 | -348 $/wk, DD -18.2%, ww -349, stops 0.23(0.27), b5 52%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60s102 | K7/lo | +395 $/wk, DD -12.7%, ww -596, stops 0.30(0.30), b5 103%, w2l 2 | +290 $/wk, DD -12.7%, ww -596, stops 0.23(0.27), b5 85%, w2l 4 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60s103 | K7/lo | +994 $/wk, DD +23.5%, ww +144, stops 0.15(0.30), b5 88%, w2l 0 | +475 $/wk, DD -9.1%, ww +144, stops 0.15(0.27), b5 78%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_JL2_pol_fx45x60 | A7/as | -231 $/wk, DD -2.4%, ww +156, stops 4.34(4.03), b5 51%, w2l 1 | +28 $/wk, DD -30.9%, ww +156, stops 4.22(3.96), b5 93%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bM7_sam_JL2_ddvote_w_aT20 | M7/am | +365 $/wk, DD +14.9%, ww +2032, stops 1.14(1.14), b5 94%, w2l 0 | -351 $/wk, DD -48.0%, ww +2032, stops 1.26(1.26), b5 84%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bO7_sam_JL2_ddvote_w_aT20 | O7/am | -102 $/wk, DD -20.4%, ww -321, stops 0.38(0.30), b5 100%, w2l 0 | -12 $/wk, DD -15.4%, ww +0, stops 0.65(0.57), b5 100%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bO7_sam_JL2_ddvote_w_aT25 | O7/am | -102 $/wk, DD -20.4%, ww -321, stops 0.38(0.30), b5 100%, w2l 0 | -12 $/wk, DD -15.4%, ww +0, stops 0.65(0.57), b5 100%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_JL2_gb60B30 | H7/as | -972 $/wk, DD -31.5%, ww +0, stops 0.46(0.23), b5 44%, w2l 6 | -1298 $/wk, DD +11.0%, ww +3643, stops 0.46(0.42), b5 55%, w2l 7 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_JL2_gb40B40 | H7/as | -3 $/wk, DD -4.1%, ww +0, stops 0.46(0.23), b5 89%, w2l 2 | -908 $/wk, DD +9.9%, ww +1967, stops 0.57(0.42), b5 45%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_JL2_gb40B40 | H7/am | +162 $/wk, DD +22.5%, ww +1740, stops 0.53(0.61), b5 81%, w2l 1 | -167 $/wk, DD +2.7%, ww +1023, stops 0.80(0.84), b5 84%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_JL2_gb50B40 | H7/am | +142 $/wk, DD +19.4%, ww +1655, stops 0.53(0.61), b5 82%, w2l 0 | -152 $/wk, DD +0.6%, ww +838, stops 0.80(0.84), b5 86%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_gb40B40 | K7/am | +504 $/wk, DD +6.0%, ww +2719, stops 0.53(0.38), b5 91%, w2l 1 | -166 $/wk, DD +32.6%, ww +2223, stops 0.53(0.46), b5 69%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_gb50B20 | K7/am | -46 $/wk, DD +7.3%, ww +1397, stops 0.53(0.38), b5 91%, w2l 1 | -728 $/wk, DD +33.5%, ww +1397, stops 0.53(0.46), b5 67%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_JL2_gb50B40 | P7/as | -703 $/wk, DD +51.2%, ww +20259, stops 0.08(0.15), b5 61%, w2l 1 | -2946 $/wk, DD +51.2%, ww +17717, stops 0.04(0.08), b5 50%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sas_JL2_gb40B40 | P7/as | -322 $/wk, DD +51.2%, ww +19309, stops 0.08(0.15), b5 65%, w2l 0 | -3609 $/wk, DD +51.2%, ww +18942, stops 0.04(0.08), b5 49%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_JL2_gb40B30 | P7/am | -4 $/wk, DD +32.6%, ww +16962, stops 0.38(0.61), b5 81%, w2l 0 | -1151 $/wk, DD +32.6%, ww +16962, stops 0.30(0.49), b5 64%, w2l 1 |

### Leads (tolerant gate in every scored window incl. L3M and L6M, DD cut > 0 in some window)
| cell | scope | L6M DD cut % | L6M d mean | windows | W44 removed L3M / L6M |
|---|---|---|---|---|---|
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60s101 | nyam | +42.3 | -19 | 2 | +1314 $/wk, DD +47.6%, ww +1732, stops 1.14(1.29), b5 86%, w2l 1 / -19 $/wk, DD +42.3%, ww +4319, stops 1.67(1.67), b5 64%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s3p92 | london | +28.2 | +336 | 2 | -34 $/wk, DD +28.2%, ww +6232, stops 2.51(2.74), b5 84%, w2l 0 / +336 $/wk, DD +28.2%, ww +6232, stops 2.74(2.89), b5 82%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x60 | all | +22.5 | +710 | 5 | +900 $/wk, DD +22.5%, ww +10172, stops 10.73(10.35), b5 98%, w2l 0 / +710 $/wk, DD +22.5%, ww +5127, stops 11.34(10.99), b5 98%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s2p81 | nyam | +22.1 | -28 | 4 | +818 $/wk, DD +44.9%, ww +2094, stops 1.29(1.29), b5 78%, w2l 1 / -28 $/wk, DD +22.1%, ww +3278, stops 2.05(1.67), b5 69%, w2l 3 |
| M1_50_g00_c1_d10_c20_tb_B_pl11_tcq50T75 | nypm | +16.5 | +245 | 2 | +245 $/wk, DD +16.5%, ww +185, stops 0.08(0.08), b5 131%, w2l 1 / +245 $/wk, DD +16.5%, ww +185, stops 0.08(0.08), b5 95%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_pl11_tcq50T75 | nyam | +8.0 | +173 | 2 | +622 $/wk, DD +14.2%, ww +0, stops 1.37(1.29), b5 103%, w2l 1 / +173 $/wk, DD +8.0%, ww +2555, stops 1.71(1.67), b5 91%, w2l 2 |
| M1_50_g00_c1_d10_c20_tb_B_bK7_slo_JL2_pol_fx40x60s103 | london | +7.2 | +647 | 2 | +44 $/wk, DD +7.2%, ww +6382, stops 2.43(2.74), b5 82%, w2l 0 / +647 $/wk, DD +7.2%, ww +6382, stops 2.66(2.89), b5 80%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sas_fx40x60 | london | +4.4 | +106 | 5 | +114 $/wk, DD +4.4%, ww +2874, stops 2.74(2.74), b5 99%, w2l 0 / +106 $/wk, DD +4.4%, ww +2874, stops 2.89(2.89), b5 100%, w2l 0 |
| M1_75_g10_c1_d10_c20_tb_N_bH7_sam | nyam | +0.8 | +35 | 2 | +258 $/wk, DD +6.8%, ww +285, stops 1.22(1.29), b5 96%, w2l 0 / +35 $/wk, DD +0.8%, ww +180, stops 1.67(1.67), b5 95%, w2l 0 |
| M1_75_g05_c1_d10_c20_tb_B_bH7_sam | nyam | +0.4 | +95 | 2 | +87 $/wk, DD +1.3%, ww +0, stops 1.29(1.29), b5 98%, w2l 0 / +95 $/wk, DD +0.4%, ww +90, stops 1.67(1.67), b5 96%, w2l 0 |
| M1_75_g10_c1_d10_c20_tb_B_bH7_sas | asia | +0.4 | +1181 | 2 | +689 $/wk, DD +0.4%, ww -346, stops 6.47(6.24), b5 101%, w2l 0 / +1181 $/wk, DD +0.4%, ww -346, stops 6.47(6.35), b5 98%, w2l 0 |
| M1_75_g10_c1_d10_c20_tb_B_bH7_sas | all | +0.4 | +1513 | 2 | +614 $/wk, DD +0.4%, ww +185, stops 10.58(10.35), b5 98%, w2l 0 / +1513 $/wk, DD +0.4%, ww +185, stops 11.18(10.99), b5 98%, w2l 0 |
| M1_75_g05_c1_d10_c20_tb_B_bA7_sas | all | +0.2 | -205 | 2 | -543 $/wk, DD +0.2%, ww +35, stops 11.26(10.35), b5 97%, w2l 0 / -205 $/wk, DD +0.2%, ww +35, stops 11.18(10.99), b5 99%, w2l 0 |
| M1_75_g10_c1_d10_c20_tb_W_bA7_sas | asia | +0.2 | +187 | 2 | -24 $/wk, DD +0.2%, ww -215, stops 6.16(6.24), b5 100%, w2l 0 / +187 $/wk, DD +0.2%, ww -215, stops 5.63(6.35), b5 99%, w2l 0 |
| M1_75_g10_c1_d10_c20_tb_W_bA7_sas | all | +0.2 | +777 | 2 | -24 $/wk, DD +0.2%, ww -215, stops 10.27(10.35), b5 100%, w2l 0 / +777 $/wk, DD +0.2%, ww -215, stops 10.27(10.99), b5 99%, w2l 0 |
| M1_75_g10_c1_d10_c20_tb_B_bA7_sas | asia | +0.1 | -326 | 2 | +481 $/wk, DD +0.1%, ww -232, stops 7.61(6.24), b5 97%, w2l 0 / -326 $/wk, DD +0.1%, ww -232, stops 6.62(6.35), b5 93%, w2l 0 |
| M1_75_g10_c1_d10_c20_tb_B_bA7_sas | all | +0.1 | +620 | 2 | +1092 $/wk, DD +0.1%, ww -232, stops 11.64(10.35), b5 96%, w2l 0 / +620 $/wk, DD +0.1%, ww -232, stops 11.18(10.99), b5 95%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx85x60 | london | +0.0 | +894 | 5 | +778 $/wk, DD +0.0%, ww +0, stops 2.66(2.74), b5 104%, w2l 0 / +894 $/wk, DD +0.0%, ww +0, stops 2.85(2.89), b5 104%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx40x60 | nyam | +0.0 | -8 | 2 | +201 $/wk, DD +4.5%, ww +0, stops 1.07(1.29), b5 99%, w2l 0 / -8 $/wk, DD +0.0%, ww +0, stops 1.56(1.67), b5 96%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bP7_sam_fx85x90 | asia | +0.0 | -137 | 5 | -274 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 100%, w2l 1 / -137 $/wk, DD +0.0%, ww +0, stops 6.35(6.35), b5 100%, w2l 1 |
| M1_50_g00_c1_d10_c20_tb_B_bU7_sas_fx85x40 | nyam | +0.0 | +68 | 2 | -15 $/wk, DD +11.8%, ww -160, stops 1.37(1.29), b5 93%, w2l 0 / +68 $/wk, DD +0.0%, ww +0, stops 1.75(1.67), b5 106%, w2l 0 |
| M1_50_g00_c1_d10_c20_tb_B_bH7_sam_fx40x40 | nyam | -0.8 | +79 | 2 | +23 $/wk, DD +2.3%, ww +62, stops 1.29(1.29), b5 91%, w2l 0 / +79 $/wk, DD -0.8%, ww -171, stops 1.71(1.67), b5 89%, w2l 0 |

### Placebos beside the finalists (forecast shifted 11 / 23 / 37 sessions at the same clock; random other session at the same clock), scope all, L6M (a real lead must beat all of them)
| finalist | real | pl11 | pl23 | pl37 | random |
|---|---|---|---|---|---|
| M1_50_g00_c1_d10_c20_tb_B_bK7_sam_JL2_pol_fx40x60s101 | -2640 $/wk, DD +56.0%, ww +22141, stops 10.88(10.99), b5 76%, w2l 0 | pending | pending | pending | pending |
| M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x60s3p92 | -3692 $/wk, DD +53.5%, ww +23074, stops 10.84(10.99), b5 73%, w2l 0 | pending | pending | pending | pending |
| M1_50_g00_c1_d10_c20_tb_B_bA7_sas_fx40x60 | +710 $/wk, DD +22.5%, ww +5127, stops 11.34(10.99), b5 98%, w2l 1 | pending | pending | pending | pending |

### Combined with the chop call and the trend-day call (item 7)
| cell | mode | L3M | L6M |
|---|---|---|---|

### FOR THE LIVE BUILD: what D7 needs at the signal second
1. Own 1-minute NQ bars only (closed bars up to the signal second): range and realised vol of the last 15/30/60/120 min; the same offset-into-session range over the previous 20 sessions (median); the range of the previous 5 and 20 sessions of the same session type; range so far in the current session; last close. D7 computes all of these itself from its own bars (preferred). 2. A small coefficient table (per session: 14 weights, mean, sd, intercept for the median-horizon and 75th-pct models) plus per book+session H50/H75 and ref EM, refit every 14 days: a static file pushed from the box every 2 weeks (the only file). 3. Nothing intraday from the box for M1. M2 (T-RANGE2 session forecast + calendar flags) needs the T-RANGE2 file and the event calendar at the session start: ranks below an equal M1 version. 4. The chop-call and trend-day cells additionally need those call files (not computable from D7 bars alone): rank below the bars-only version.

### Reading
Drawdown first; a result needs the gate in recent AND older windows and has to beat the placebos. Cells that cut drawdown only through L3M, or only with full stops up, are not leads. Expected move forecast quality (table above) is a forecasting result scored on all 43 months; the exact cells decide whether it makes a better bracket. No PASS claim.
