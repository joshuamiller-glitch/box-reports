# DS3_RANGEUSE - T-RANGEUSE: the walk-forward range forecast on D7 dials (W-RU). Rebuilt 2026-11-14T13:59Z by code/th_rangeuse/ru_loop.sh (every 3 h). Research only, NO PASS claim.
**VERDICT (plain): 74 cells scored through L6M; 6 (cell,scope) pass the tolerant gate with a drawdown cut in recent AND older windows (leads, before placebo/null); placebo/null/gain-of-(b,(c) over (a) below. No PASS claim.**

Prereg: autopilot/RANGEUSE_PREREG.md (sha in DECISIONS.md, logged before scoring). Order: DIRECTIVE_UW_3PART_20261113.md PART 2. Base JN05W2 exact engine, all layers ON. Identity: TL3_RU_ID 202610 (hook path active at neutral multipliers): 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL.
Months scored (cells with all months of the window / 98 cells): L3M 98, L6M 74, HOLD 50, PREUW 38. Driver: 61 jobs wanted, 8 chains running, 1794664792.

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
| D5R13A_x | all | -739 $/wk, DD +14.4%, ww +10121, stops 10.92(10.99), b5 96%, w2l 0 | -739 $/wk, DD +14.4%, ww +10121, stops 10.92(10.99), b5 96%, w2l 0 | n/a | n/a | n/a | n/a | n/a |
| D7T_a | all | +731 $/wk, DD +7.2%, ww +3778, stops 10.84(10.99), b5 101%, w2l 0 | n/a | n/a | n/a | n/a | n/a | n/a |

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