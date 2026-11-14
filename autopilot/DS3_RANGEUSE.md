# DS3_RANGEUSE - T-RANGEUSE: the walk-forward range forecast on D7 dials (W-RU). Rebuilt 2026-11-14T04:58Z by code/th_rangeuse/ru_loop.sh (every 3 h). Research only, NO PASS claim.
**VERDICT (plain): 16 cells scored through L6M; 0 (cell,scope) pass the tolerant gate with a drawdown cut in recent AND older windows (leads, before placebo/null); placebo/null/gain-of-(b,(c) over (a) below. No PASS claim.**

Prereg: autopilot/RANGEUSE_PREREG.md (sha in DECISIONS.md, logged before scoring). Order: DIRECTIVE_UW_3PART_20261113.md PART 2. Base JN05W2 exact engine, all layers ON. Identity: TL3_RU_ID 202610 (hook path active at neutral multipliers): 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL.
Months scored (cells with all months of the window / 98 cells): L3M 98, L6M 16, HOLD 0, PREUW 0. Driver: 228 jobs wanted, 8 chains running, 1794632258.

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
| all | a | -7420 $/wk, DD -10.2%, ww -2364, stops 12.40(10.35), b5 73%, w2l 1 | -6054 $/wk, DD -10.2%, ww -15359, stops 17.39(10.99), b5 81%, w2l 1 | n/a | n/a |
| all | b | -6971 $/wk, DD -25.9%, ww -14627, stops 11.95(10.35), b5 89%, w2l 1 | -5427 $/wk, DD -25.9%, ww -14627, stops 16.55(10.99), b5 89%, w2l 2 | n/a | n/a |
| all | c | -5225 $/wk, DD -5.9%, ww -1261, stops 12.71(10.35), b5 90%, w2l 1 | -6151 $/wk, DD -5.9%, ww -10598, stops 17.50(10.99), b5 87%, w2l 1 | n/a | n/a |
| all | **b-a** | +448 $/wk, DD -15.7 pts, ww -12263 | +628 $/wk, DD -15.7 pts, ww +732 | n/a | n/a |
| all | **c-a** | +2195 $/wk, DD +4.3 pts, ww +1103 | -97 $/wk, DD +4.3 pts, ww +4761 | n/a | n/a |
| asia | a | -5194 $/wk, DD -18.4%, ww -18623, stops 7.76(6.24), b5 84%, w2l 1 | -4668 $/wk, DD -18.4%, ww -22431, stops 10.23(6.35), b5 90%, w2l 2 | n/a | n/a |
| asia | b | -4116 $/wk, DD -5.3%, ww -18193, stops 7.99(6.24), b5 91%, w2l 1 | -4166 $/wk, DD -5.6%, ww -18193, stops 9.78(6.35), b5 89%, w2l 3 | n/a | n/a |
| asia | c | -4006 $/wk, DD -8.3%, ww -16882, stops 8.29(6.24), b5 89%, w2l 1 | -5429 $/wk, DD -8.3%, ww -18591, stops 10.23(6.35), b5 89%, w2l 3 | n/a | n/a |
| asia | **b-a** | +1079 $/wk, DD +13.1 pts, ww +430 | +502 $/wk, DD +12.8 pts, ww +4238 | n/a | n/a |
| asia | **c-a** | +1189 $/wk, DD +10.1 pts, ww +1742 | -761 $/wk, DD +10.1 pts, ww +3841 | n/a | n/a |
| london | a | -326 $/wk, DD -3.0%, ww +2741, stops 3.42(2.74), b5 89%, w2l 0 | -339 $/wk, DD -3.0%, ww +2741, stops 4.64(2.89), b5 82%, w2l 0 | n/a | n/a |
| london | b | -1751 $/wk, DD -14.5%, ww -366, stops 3.04(2.74), b5 84%, w2l 0 | -145 $/wk, DD -14.5%, ww -366, stops 4.53(2.89), b5 89%, w2l 0 | n/a | n/a |
| london | c | +504 $/wk, DD +4.0%, ww +2112, stops 3.20(2.74), b5 89%, w2l 0 | +904 $/wk, DD +4.0%, ww +2112, stops 4.79(2.89), b5 93%, w2l 0 | n/a | n/a |
| london | **b-a** | -1424 $/wk, DD -11.4 pts, ww -3107 | +194 $/wk, DD -11.4 pts, ww -3107 | n/a | n/a |
| london | **c-a** | +830 $/wk, DD +7.0 pts, ww -629 | +1243 $/wk, DD +7.0 pts, ww -629 | n/a | n/a |
| nyam | a | -822 $/wk, DD +16.2%, ww +514, stops 1.14(1.29), b5 49%, w2l 2 | -432 $/wk, DD -33.3%, ww -2933, stops 2.13(1.67), b5 92%, w2l 4 | n/a | n/a |
| nyam | b | -323 $/wk, DD +17.6%, ww -54, stops 0.84(1.29), b5 66%, w2l 2 | -757 $/wk, DD -70.2%, ww -2800, stops 1.94(1.67), b5 82%, w2l 4 | n/a | n/a |
| nyam | c | -608 $/wk, DD -0.1%, ww -4307, stops 0.99(1.29), b5 78%, w2l 1 | -903 $/wk, DD -84.8%, ww -3985, stops 2.13(1.67), b5 81%, w2l 4 | n/a | n/a |
| nyam | **b-a** | +499 $/wk, DD +1.4 pts, ww -568 | -325 $/wk, DD -36.9 pts, ww +133 | n/a | n/a |
| nyam | **c-a** | +215 $/wk, DD -16.3 pts, ww -4821 | -471 $/wk, DD -51.5 pts, ww -1052 | n/a | n/a |
| nypm | a | -1077 $/wk, DD -16.0%, ww -145, stops 0.08(0.08), b5 23%, w2l 3 | -615 $/wk, DD -16.0%, ww -145, stops 0.38(0.08), b5 88%, w2l 5 | n/a | n/a |
| nypm | b | -781 $/wk, DD +5.4%, ww +1073, stops 0.08(0.08), b5 16%, w2l 4 | -358 $/wk, DD +5.4%, ww +1073, stops 0.30(0.08), b5 79%, w2l 4 | n/a | n/a |
| nypm | c | -1116 $/wk, DD -47.0%, ww +757, stops 0.23(0.08), b5 10%, w2l 4 | -723 $/wk, DD -47.0%, ww +757, stops 0.34(0.08), b5 72%, w2l 4 | n/a | n/a |
| nypm | **b-a** | +295 $/wk, DD +21.4 pts, ww +1218 | +256 $/wk, DD +21.4 pts, ww +1218 | n/a | n/a |
| nypm | **c-a** | -39 $/wk, DD -31.0 pts, ww +902 | -108 $/wk, DD -31.0 pts, ww +902 | n/a | n/a |

**D3T** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -4471 $/wk, DD -2.1%, ww -722, stops 11.57(10.35), b5 90%, w2l 1 | -3713 $/wk, DD -2.1%, ww -11797, stops 14.38(10.99), b5 99%, w2l 1 | n/a | n/a |
| all | b | -5003 $/wk, DD +6.5%, ww -32, stops 11.03(10.35), b5 88%, w2l 2 | -2173 $/wk, DD +6.5%, ww -32, stops 13.54(10.99), b5 101%, w2l 2 | n/a | n/a |
| all | c | -3585 $/wk, DD -17.3%, ww -11955, stops 11.72(10.35), b5 91%, w2l 0 | -2699 $/wk, DD -17.3%, ww -11955, stops 13.77(10.99), b5 100%, w2l 0 | n/a | n/a |
| all | **b-a** | -532 $/wk, DD +8.5 pts, ww +690 | +1540 $/wk, DD +8.5 pts, ww +11764 | n/a | n/a |
| all | **c-a** | +885 $/wk, DD -15.2 pts, ww -11233 | +1014 $/wk, DD -15.2 pts, ww -159 | n/a | n/a |
| asia | a | -2429 $/wk, DD -8.9%, ww -14670, stops 7.08(6.24), b5 99%, w2l 1 | -3111 $/wk, DD -22.6%, ww -16077, stops 8.26(6.35), b5 104%, w2l 4 | n/a | n/a |
| asia | b | -3340 $/wk, DD +6.7%, ww -13308, stops 7.15(6.24), b5 89%, w2l 0 | -1843 $/wk, DD +6.7%, ww -13308, stops 7.76(6.35), b5 92%, w2l 1 | n/a | n/a |
| asia | c | -3140 $/wk, DD +0.9%, ww -8722, stops 7.15(6.24), b5 96%, w2l 0 | -3525 $/wk, DD -4.8%, ww -16077, stops 7.80(6.35), b5 97%, w2l 3 | n/a | n/a |
| asia | **b-a** | -911 $/wk, DD +15.6 pts, ww +1363 | +1268 $/wk, DD +29.4 pts, ww +2770 | n/a | n/a |
| asia | **c-a** | -711 $/wk, DD +9.8 pts, ww +5948 | -414 $/wk, DD +17.8 pts, ww +0 | n/a | n/a |
| london | a | -690 $/wk, DD -15.8%, ww +1175, stops 3.20(2.74), b5 99%, w2l 0 | +508 $/wk, DD -15.8%, ww +1175, stops 3.77(2.89), b5 92%, w2l 0 | n/a | n/a |
| london | b | -582 $/wk, DD +5.3%, ww +943, stops 2.66(2.74), b5 87%, w2l 0 | +462 $/wk, DD +5.3%, ww +943, stops 3.54(2.89), b5 92%, w2l 0 | n/a | n/a |
| london | c | -251 $/wk, DD -23.1%, ww +0, stops 3.20(2.74), b5 105%, w2l 0 | +1232 $/wk, DD -23.1%, ww +0, stops 3.73(2.89), b5 108%, w2l 0 | n/a | n/a |
| london | **b-a** | +108 $/wk, DD +21.1 pts, ww -231 | -46 $/wk, DD +21.1 pts, ww -231 | n/a | n/a |
| london | **c-a** | +439 $/wk, DD -7.3 pts, ww -1175 | +724 $/wk, DD -7.3 pts, ww -1175 | n/a | n/a |
| nyam | a | -249 $/wk, DD +22.4%, ww +817, stops 1.22(1.29), b5 71%, w2l 1 | -517 $/wk, DD -49.4%, ww -2170, stops 2.13(1.67), b5 93%, w2l 4 | n/a | n/a |
| nyam | b | -131 $/wk, DD +12.8%, ww +592, stops 1.14(1.29), b5 82%, w2l 1 | -194 $/wk, DD -13.7%, ww -2170, stops 2.02(1.67), b5 87%, w2l 2 | n/a | n/a |
| nyam | c | +489 $/wk, DD +0.3%, ww +592, stops 1.22(1.29), b5 106%, w2l 1 | +17 $/wk, DD -36.8%, ww -2770, stops 2.05(1.67), b5 106%, w2l 2 | n/a | n/a |
| nyam | **b-a** | +118 $/wk, DD -9.6 pts, ww -225 | +323 $/wk, DD +35.8 pts, ww +0 | n/a | n/a |
| nyam | **c-a** | +739 $/wk, DD -22.0 pts, ww -225 | +534 $/wk, DD +12.7 pts, ww -600 | n/a | n/a |
| nypm | a | -1102 $/wk, DD -26.6%, ww -373, stops 0.08(0.08), b5 35%, w2l 3 | -594 $/wk, DD -26.6%, ww -373, stops 0.23(0.08), b5 94%, w2l 3 | n/a | n/a |
| nypm | b | -950 $/wk, DD -18.2%, ww +168, stops 0.08(0.08), b5 32%, w2l 4 | -598 $/wk, DD -18.2%, ww +168, stops 0.23(0.08), b5 89%, w2l 6 | n/a | n/a |
| nypm | c | -684 $/wk, DD -22.2%, ww +308, stops 0.15(0.08), b5 63%, w2l 3 | -424 $/wk, DD -22.2%, ww +308, stops 0.19(0.08), b5 101%, w2l 3 | n/a | n/a |
| nypm | **b-a** | +153 $/wk, DD +8.4 pts, ww +540 | -4 $/wk, DD +8.4 pts, ww +540 | n/a | n/a |
| nypm | **c-a** | +419 $/wk, DD +4.5 pts, ww +680 | +170 $/wk, DD +4.5 pts, ww +680 | n/a | n/a |

**D3M** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -7996 $/wk, DD -20.7%, ww -4703, stops 14.08(10.35), b5 73%, w2l 1 | n/a | n/a | n/a |
| all | b | -9138 $/wk, DD -34.0%, ww -17212, stops 12.55(10.35), b5 88%, w2l 1 | n/a | n/a | n/a |
| all | c | -8118 $/wk, DD -44.9%, ww -22415, stops 14.99(10.35), b5 87%, w2l 2 | n/a | n/a | n/a |
| all | **b-a** | -1142 $/wk, DD -13.3 pts, ww -12509 | n/a | n/a | n/a |
| all | **c-a** | -122 $/wk, DD -24.2 pts, ww -17712 | n/a | n/a | n/a |
| asia | a | -5714 $/wk, DD -32.6%, ww -20911, stops 8.67(6.24), b5 83%, w2l 1 | n/a | n/a | n/a |
| asia | b | -6686 $/wk, DD -29.0%, ww -24077, stops 8.52(6.24), b5 85%, w2l 1 | n/a | n/a | n/a |
| asia | c | -6628 $/wk, DD -39.4%, ww -23527, stops 8.90(6.24), b5 72%, w2l 1 | n/a | n/a | n/a |
| asia | **b-a** | -973 $/wk, DD +3.5 pts, ww -3166 | n/a | n/a | n/a |
| asia | **c-a** | -914 $/wk, DD -6.9 pts, ww -2616 | n/a | n/a | n/a |
| london | a | +35 $/wk, DD +1.1%, ww +5824, stops 4.11(2.74), b5 89%, w2l 0 | n/a | n/a | n/a |
| london | b | -1763 $/wk, DD -17.4%, ww +3187, stops 2.89(2.74), b5 84%, w2l 0 | n/a | n/a | n/a |
| london | c | +658 $/wk, DD -10.7%, ww +3546, stops 4.72(2.74), b5 96%, w2l 0 | n/a | n/a | n/a |
| london | **b-a** | -1798 $/wk, DD -18.5 pts, ww -2637 | n/a | n/a | n/a |
| london | **c-a** | +622 $/wk, DD -11.8 pts, ww -2279 | n/a | n/a | n/a |
| nyam | a | -1363 $/wk, DD +20.9%, ww +870, stops 1.22(1.29), b5 27%, w2l 2 | n/a | n/a | n/a |
| nyam | b | -13 $/wk, DD +26.0%, ww -833, stops 0.99(1.29), b5 71%, w2l 1 | n/a | n/a | n/a |
| nyam | c | -1191 $/wk, DD -29.4%, ww -4922, stops 1.14(1.29), b5 49%, w2l 2 | n/a | n/a | n/a |
| nyam | **b-a** | +1350 $/wk, DD +5.0 pts, ww -1703 | n/a | n/a | n/a |
| nyam | **c-a** | +173 $/wk, DD -50.3 pts, ww -5792 | n/a | n/a | n/a |
| nypm | a | -954 $/wk, DD +6.1%, ww +1628, stops 0.08(0.08), b5 11%, w2l 3 | n/a | n/a | n/a |
| nypm | b | -675 $/wk, DD +6.8%, ww +1366, stops 0.15(0.08), b5 19%, w2l 4 | n/a | n/a | n/a |
| nypm | c | -957 $/wk, DD -10.6%, ww +1428, stops 0.23(0.08), b5 17%, w2l 3 | n/a | n/a | n/a |
| nypm | **b-a** | +279 $/wk, DD +0.8 pts, ww -262 | n/a | n/a | n/a |
| nypm | **c-a** | -3 $/wk, DD -16.6 pts, ww -201 | n/a | n/a | n/a |

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
| all | a | -7856 $/wk, DD -8.6%, ww -1378, stops 9.13(10.35), b5 57%, w2l 1 | -12801 $/wk, DD -8.6%, ww -1378, stops 9.70(10.99), b5 73%, w2l 4 | n/a | n/a |
| all | b | -10753 $/wk, DD -4.3%, ww -107, stops 8.83(10.35), b5 42%, w2l 2 | -9439 $/wk, DD -4.3%, ww -107, stops 9.70(10.99), b5 71%, w2l 3 | n/a | n/a |
| all | c | -103 $/wk, DD +33.6%, ww +17543, stops 8.83(10.35), b5 78%, w2l 1 | -1200 $/wk, DD +33.6%, ww +17543, stops 9.43(10.99), b5 94%, w2l 1 | n/a | n/a |
| all | **b-a** | -2898 $/wk, DD +4.3 pts, ww +1271 | +3363 $/wk, DD +4.3 pts, ww +1271 | n/a | n/a |
| all | **c-a** | +7753 $/wk, DD +42.2 pts, ww +18921 | +11602 $/wk, DD +42.2 pts, ww +18921 | n/a | n/a |
| asia | a | -5301 $/wk, DD -11.3%, ww -5486, stops 5.93(6.24), b5 103%, w2l 1 | -7981 $/wk, DD -11.3%, ww -5486, stops 5.90(6.35), b5 102%, w2l 3 | n/a | n/a |
| asia | b | -5747 $/wk, DD -8.6%, ww -4149, stops 6.01(6.24), b5 81%, w2l 2 | -5949 $/wk, DD -8.6%, ww -4149, stops 6.24(6.35), b5 85%, w2l 4 | n/a | n/a |
| asia | c | +2444 $/wk, DD +26.5%, ww +8989, stops 5.55(6.24), b5 109%, w2l 1 | -1038 $/wk, DD +26.5%, ww +8989, stops 5.63(6.35), b5 97%, w2l 4 | n/a | n/a |
| asia | **b-a** | -447 $/wk, DD +2.8 pts, ww +1337 | +2032 $/wk, DD +2.8 pts, ww +1337 | n/a | n/a |
| asia | **c-a** | +7745 $/wk, DD +37.8 pts, ww +14475 | +6942 $/wk, DD +37.8 pts, ww +14475 | n/a | n/a |
| london | a | -926 $/wk, DD +5.8%, ww -8782, stops 1.98(2.74), b5 73%, w2l 0 | -2210 $/wk, DD -17.2%, ww -8782, stops 2.28(2.89), b5 76%, w2l 1 | n/a | n/a |
| london | b | -3018 $/wk, DD +31.9%, ww -2814, stops 1.75(2.74), b5 45%, w2l 0 | -988 $/wk, DD +31.9%, ww -2814, stops 1.94(2.89), b5 60%, w2l 0 | n/a | n/a |
| london | c | -3139 $/wk, DD +25.3%, ww -400, stops 1.90(2.74), b5 62%, w2l 2 | -352 $/wk, DD +25.3%, ww -400, stops 2.24(2.89), b5 74%, w2l 2 | n/a | n/a |
| london | **b-a** | -2092 $/wk, DD +26.1 pts, ww +5968 | +1222 $/wk, DD +49.1 pts, ww +5968 | n/a | n/a |
| london | **c-a** | -2213 $/wk, DD +19.5 pts, ww +8382 | +1858 $/wk, DD +42.5 pts, ww +8382 | n/a | n/a |
| nyam | a | -627 $/wk, DD -2.6%, ww -2863, stops 1.14(1.29), b5 85%, w2l 3 | -1360 $/wk, DD -75.1%, ww -1497, stops 1.45(1.67), b5 64%, w2l 5 | n/a | n/a |
| nyam | b | -1465 $/wk, DD -28.2%, ww +2509, stops 0.99(1.29), b5 66%, w2l 3 | -1918 $/wk, DD -85.4%, ww -1252, stops 1.45(1.67), b5 67%, w2l 5 | n/a | n/a |
| nyam | c | +1150 $/wk, DD +33.8%, ww +3493, stops 1.29(1.29), b5 91%, w2l 2 | +449 $/wk, DD +28.6%, ww +3080, stops 1.48(1.67), b5 69%, w2l 3 | n/a | n/a |
| nyam | **b-a** | -838 $/wk, DD -25.6 pts, ww +5373 | -558 $/wk, DD -10.3 pts, ww +245 | n/a | n/a |
| nyam | **c-a** | +1777 $/wk, DD +36.4 pts, ww +6356 | +1809 $/wk, DD +103.8 pts, ww +4576 | n/a | n/a |
| nypm | a | -1002 $/wk, DD -86.6%, ww -275, stops 0.08(0.08), b5 29%, w2l 4 | -1251 $/wk, DD -86.6%, ww -275, stops 0.08(0.08), b5 31%, w2l 7 | n/a | n/a |
| nypm | b | -523 $/wk, DD +34.9%, ww +822, stops 0.08(0.08), b5 68%, w2l 1 | -583 $/wk, DD +31.9%, ww +822, stops 0.08(0.08), b5 77%, w2l 2 | n/a | n/a |
| nypm | c | -558 $/wk, DD -25.9%, ww -183, stops 0.08(0.08), b5 15%, w2l 3 | -258 $/wk, DD -25.9%, ww -183, stops 0.08(0.08), b5 87%, w2l 4 | n/a | n/a |
| nypm | **b-a** | +479 $/wk, DD +121.5 pts, ww +1097 | +667 $/wk, DD +118.5 pts, ww +1097 | n/a | n/a |
| nypm | **c-a** | +444 $/wk, DD +60.7 pts, ww +92 | +993 $/wk, DD +60.7 pts, ww +92 | n/a | n/a |

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
| all | b | -5257 $/wk, DD +9.9%, ww +5619, stops 9.59(10.35), b5 65%, w2l 1 | n/a | n/a | n/a |
| all | c | -2076 $/wk, DD +30.7%, ww +7445, stops 9.66(10.35), b5 85%, w2l 1 | n/a | n/a | n/a |
| all | **b-a** | -2645 $/wk, DD +25.9 pts, ww +11172 | n/a | n/a | n/a |
| all | **c-a** | +535 $/wk, DD +46.6 pts, ww +12998 | n/a | n/a | n/a |
| asia | a | -512 $/wk, DD -11.5%, ww -5570, stops 6.32(6.24), b5 100%, w2l 1 | -3202 $/wk, DD -11.5%, ww -6217, stops 6.20(6.35), b5 100%, w2l 1 | n/a | n/a |
| asia | b | -1319 $/wk, DD +8.0%, ww -2121, stops 6.09(6.24), b5 104%, w2l 1 | n/a | n/a | n/a |
| asia | c | +2288 $/wk, DD +24.3%, ww -8025, stops 5.86(6.24), b5 111%, w2l 1 | n/a | n/a | n/a |
| asia | **b-a** | -807 $/wk, DD +19.5 pts, ww +3449 | n/a | n/a | n/a |
| asia | **c-a** | +2800 $/wk, DD +35.8 pts, ww -2455 | n/a | n/a | n/a |
| london | a | -2337 $/wk, DD -24.8%, ww -10688, stops 2.43(2.74), b5 78%, w2l 0 | -1512 $/wk, DD -24.8%, ww -10688, stops 2.59(2.89), b5 86%, w2l 0 | n/a | n/a |
| london | b | -2998 $/wk, DD +32.5%, ww -6174, stops 2.21(2.74), b5 54%, w2l 1 | n/a | n/a | n/a |
| london | c | -4751 $/wk, DD -10.1%, ww -5106, stops 2.59(2.74), b5 69%, w2l 2 | n/a | n/a | n/a |
| london | **b-a** | -661 $/wk, DD +57.3 pts, ww +4514 | n/a | n/a | n/a |
| london | **c-a** | -2415 $/wk, DD +14.7 pts, ww +5582 | n/a | n/a | n/a |
| nyam | a | +661 $/wk, DD -9.6%, ww +826, stops 1.14(1.29), b5 117%, w2l 3 | -69 $/wk, DD -1.7%, ww +3414, stops 1.37(1.67), b5 97%, w2l 4 | n/a | n/a |
| nyam | b | +10 $/wk, DD +23.6%, ww -1872, stops 1.22(1.29), b5 91%, w2l 1 | n/a | n/a | n/a |
| nyam | c | +594 $/wk, DD +33.2%, ww +173, stops 1.14(1.29), b5 73%, w2l 1 | n/a | n/a | n/a |
| nyam | **b-a** | -651 $/wk, DD +33.2 pts, ww -2698 | n/a | n/a | n/a |
| nyam | **c-a** | -67 $/wk, DD +42.8 pts, ww -653 | n/a | n/a | n/a |
| nypm | a | -424 $/wk, DD -19.9%, ww +232, stops 0.08(0.08), b5 99%, w2l 2 | -754 $/wk, DD -19.9%, ww +232, stops 0.08(0.08), b5 50%, w2l 2 | n/a | n/a |
| nypm | b | -950 $/wk, DD -49.7%, ww -248, stops 0.08(0.08), b5 38%, w2l 3 | n/a | n/a | n/a |
| nypm | c | -207 $/wk, DD +17.2%, ww +2284, stops 0.08(0.08), b5 61%, w2l 2 | n/a | n/a | n/a |
| nypm | **b-a** | -526 $/wk, DD -29.7 pts, ww -480 | n/a | n/a | n/a |
| nypm | **c-a** | +217 $/wk, DD +37.2 pts, ww +2052 | n/a | n/a | n/a |

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
| all | a | -3374 $/wk, DD +30.3%, ww +12801, stops 7.68(10.35), b5 77%, w2l 2 | n/a | n/a | n/a |
| all | b | -9442 $/wk, DD -6.6%, ww +7549, stops 7.46(10.35), b5 67%, w2l 3 | n/a | n/a | n/a |
| all | c | -4492 $/wk, DD +36.2%, ww +16680, stops 7.68(10.35), b5 77%, w2l 3 | n/a | n/a | n/a |
| all | **b-a** | -6068 $/wk, DD -36.9 pts, ww -5252 | n/a | n/a | n/a |
| all | **c-a** | -1118 $/wk, DD +5.9 pts, ww +3879 | n/a | n/a | n/a |
| asia | a | -8204 $/wk, DD +33.2%, ww +434, stops 4.18(6.24), b5 48%, w2l 2 | n/a | n/a | n/a |
| asia | b | -5372 $/wk, DD +36.7%, ww +8193, stops 4.26(6.24), b5 64%, w2l 0 | n/a | n/a | n/a |
| asia | c | -3594 $/wk, DD +39.8%, ww -4497, stops 4.49(6.24), b5 55%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | +2831 $/wk, DD +3.6 pts, ww +7759 | n/a | n/a | n/a |
| asia | **c-a** | +4610 $/wk, DD +6.6 pts, ww -4931 | n/a | n/a | n/a |
| london | a | +4852 $/wk, DD +20.3%, ww +2731, stops 1.60(2.74), b5 118%, w2l 1 | n/a | n/a | n/a |
| london | b | -2945 $/wk, DD +30.7%, ww +3850, stops 1.52(2.74), b5 64%, w2l 3 | n/a | n/a | n/a |
| london | c | -1951 $/wk, DD +11.6%, ww +7446, stops 1.83(2.74), b5 69%, w2l 2 | n/a | n/a | n/a |
| london | **b-a** | -7797 $/wk, DD +10.4 pts, ww +1119 | n/a | n/a | n/a |
| london | **c-a** | -6803 $/wk, DD -8.7 pts, ww +4715 | n/a | n/a | n/a |
| nyam | a | +474 $/wk, DD +9.9%, ww -1768, stops 1.75(1.29), b5 85%, w2l 2 | n/a | n/a | n/a |
| nyam | b | -115 $/wk, DD -6.8%, ww -4730, stops 1.52(1.29), b5 71%, w2l 2 | n/a | n/a | n/a |
| nyam | c | +2073 $/wk, DD +44.4%, ww +1358, stops 1.29(1.29), b5 83%, w2l 2 | n/a | n/a | n/a |
| nyam | **b-a** | -589 $/wk, DD -16.7 pts, ww -2962 | n/a | n/a | n/a |
| nyam | **c-a** | +1599 $/wk, DD +34.5 pts, ww +3126 | n/a | n/a | n/a |
| nypm | a | -496 $/wk, DD -47.1%, ww -653, stops 0.15(0.08), b5 86%, w2l 4 | n/a | n/a | n/a |
| nypm | b | -1010 $/wk, DD -155.0%, ww -3994, stops 0.15(0.08), b5 61%, w2l 4 | n/a | n/a | n/a |
| nypm | c | -1019 $/wk, DD -76.8%, ww -244, stops 0.08(0.08), b5 34%, w2l 3 | n/a | n/a | n/a |
| nypm | **b-a** | -514 $/wk, DD -107.9 pts, ww -3341 | n/a | n/a | n/a |
| nypm | **c-a** | -523 $/wk, DD -29.7 pts, ww +408 | n/a | n/a | n/a |

**D4II1** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -3937 $/wk, DD -16.1%, ww -6232, stops 10.27(10.35), b5 77%, w2l 0 | n/a | n/a | n/a |
| all | b | -2053 $/wk, DD +12.0%, ww +6618, stops 10.20(10.35), b5 77%, w2l 1 | n/a | n/a | n/a |
| all | c | -1435 $/wk, DD +15.8%, ww +8264, stops 9.97(10.35), b5 86%, w2l 1 | n/a | n/a | n/a |
| all | **b-a** | +1884 $/wk, DD +28.2 pts, ww +12850 | n/a | n/a | n/a |
| all | **c-a** | +2502 $/wk, DD +31.9 pts, ww +14496 | n/a | n/a | n/a |
| asia | a | -1857 $/wk, DD -9.9%, ww -4797, stops 6.47(6.24), b5 103%, w2l 0 | n/a | n/a | n/a |
| asia | b | +1780 $/wk, DD +8.2%, ww -1241, stops 6.39(6.24), b5 106%, w2l 0 | n/a | n/a | n/a |
| asia | c | +1423 $/wk, DD +7.4%, ww -3821, stops 5.93(6.24), b5 103%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | +3637 $/wk, DD +18.1 pts, ww +3556 | n/a | n/a | n/a |
| asia | **c-a** | +3281 $/wk, DD +17.3 pts, ww +976 | n/a | n/a | n/a |
| london | a | -2334 $/wk, DD -9.5%, ww -6221, stops 2.59(2.74), b5 73%, w2l 0 | n/a | n/a | n/a |
| london | b | -2317 $/wk, DD +35.8%, ww -6158, stops 2.28(2.74), b5 64%, w2l 1 | n/a | n/a | n/a |
| london | c | -3262 $/wk, DD +14.1%, ww -2826, stops 2.66(2.74), b5 73%, w2l 2 | n/a | n/a | n/a |
| london | **b-a** | +17 $/wk, DD +45.2 pts, ww +63 | n/a | n/a | n/a |
| london | **c-a** | -929 $/wk, DD +23.6 pts, ww +3395 | n/a | n/a | n/a |
| nyam | a | +525 $/wk, DD +11.3%, ww -1454, stops 1.14(1.29), b5 115%, w2l 2 | n/a | n/a | n/a |
| nyam | b | -514 $/wk, DD -13.6%, ww +130, stops 1.45(1.29), b5 96%, w2l 2 | n/a | n/a | n/a |
| nyam | c | +628 $/wk, DD +37.5%, ww +1493, stops 1.29(1.29), b5 84%, w2l 2 | n/a | n/a | n/a |
| nyam | **b-a** | -1039 $/wk, DD -24.9 pts, ww +1584 | n/a | n/a | n/a |
| nyam | **c-a** | +102 $/wk, DD +26.2 pts, ww +2948 | n/a | n/a | n/a |
| nypm | a | -271 $/wk, DD -13.5%, ww +526, stops 0.08(0.08), b5 92%, w2l 1 | n/a | n/a | n/a |
| nypm | b | -1003 $/wk, DD -42.2%, ww +97, stops 0.08(0.08), b5 24%, w2l 4 | n/a | n/a | n/a |
| nypm | c | -224 $/wk, DD -17.8%, ww +232, stops 0.08(0.08), b5 81%, w2l 3 | n/a | n/a | n/a |
| nypm | **b-a** | -732 $/wk, DD -28.7 pts, ww -429 | n/a | n/a | n/a |
| nypm | **c-a** | +47 $/wk, DD -4.3 pts, ww -294 | n/a | n/a | n/a |

**D4III1** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -382 $/wk, DD +3.6%, ww +643, stops 10.35(10.35), b5 87%, w2l 0 | n/a | n/a | n/a |
| all | b | -734 $/wk, DD +14.1%, ww +3999, stops 10.35(10.35), b5 84%, w2l 0 | n/a | n/a | n/a |
| all | c | -191 $/wk, DD +3.3%, ww +746, stops 10.12(10.35), b5 100%, w2l 1 | n/a | n/a | n/a |
| all | **b-a** | -352 $/wk, DD +10.4 pts, ww +3355 | n/a | n/a | n/a |
| all | **c-a** | +191 $/wk, DD -0.3 pts, ww +102 | n/a | n/a | n/a |
| asia | a | -2700 $/wk, DD +6.0%, ww +434, stops 6.24(6.24), b5 90%, w2l 1 | n/a | n/a | n/a |
| asia | b | +854 $/wk, DD +8.6%, ww +249, stops 6.16(6.24), b5 105%, w2l 0 | n/a | n/a | n/a |
| asia | c | -776 $/wk, DD +7.1%, ww -3596, stops 6.24(6.24), b5 93%, w2l 1 | n/a | n/a | n/a |
| asia | **b-a** | +3554 $/wk, DD +2.7 pts, ww -185 | n/a | n/a | n/a |
| asia | **c-a** | +1923 $/wk, DD +1.1 pts, ww -4030 | n/a | n/a | n/a |
| london | a | +2290 $/wk, DD +16.4%, ww +5209, stops 2.59(2.74), b5 106%, w2l 0 | n/a | n/a | n/a |
| london | b | -392 $/wk, DD +16.2%, ww +4005, stops 2.66(2.74), b5 88%, w2l 0 | n/a | n/a | n/a |
| london | c | +1295 $/wk, DD +15.7%, ww +6915, stops 2.36(2.74), b5 103%, w2l 0 | n/a | n/a | n/a |
| london | **b-a** | -2683 $/wk, DD -0.3 pts, ww -1204 | n/a | n/a | n/a |
| london | **c-a** | -996 $/wk, DD -0.7 pts, ww +1706 | n/a | n/a | n/a |
| nyam | a | +683 $/wk, DD -21.8%, ww -4321, stops 1.45(1.29), b5 104%, w2l 1 | n/a | n/a | n/a |
| nyam | b | -170 $/wk, DD -20.3%, ww -6230, stops 1.45(1.29), b5 92%, w2l 3 | n/a | n/a | n/a |
| nyam | c | +15 $/wk, DD -16.8%, ww -4321, stops 1.45(1.29), b5 60%, w2l 0 | n/a | n/a | n/a |
| nyam | **b-a** | -853 $/wk, DD +1.5 pts, ww -1909 | n/a | n/a | n/a |
| nyam | **c-a** | -667 $/wk, DD +5.0 pts, ww +0 | n/a | n/a | n/a |
| nypm | a | -655 $/wk, DD -78.4%, ww -286, stops 0.08(0.08), b5 92%, w2l 0 | n/a | n/a | n/a |
| nypm | b | -1026 $/wk, DD -56.2%, ww +111, stops 0.08(0.08), b5 61%, w2l 3 | n/a | n/a | n/a |
| nypm | c | -725 $/wk, DD -19.5%, ww -286, stops 0.08(0.08), b5 44%, w2l 1 | n/a | n/a | n/a |
| nypm | **b-a** | -371 $/wk, DD +22.2 pts, ww +397 | n/a | n/a | n/a |
| nypm | **c-a** | -69 $/wk, DD +58.9 pts, ww +0 | n/a | n/a | n/a |

**D4I125** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -2158 $/wk, DD +30.4%, ww +13288, stops 8.60(10.35), b5 79%, w2l 1 | n/a | n/a | n/a |
| all | b | -8986 $/wk, DD +24.4%, ww +5216, stops 8.14(10.35), b5 68%, w2l 3 | n/a | n/a | n/a |
| all | c | -4586 $/wk, DD +22.7%, ww +13782, stops 8.22(10.35), b5 79%, w2l 3 | n/a | n/a | n/a |
| all | **b-a** | -6828 $/wk, DD -6.0 pts, ww -8072 | n/a | n/a | n/a |
| all | **c-a** | -2428 $/wk, DD -7.7 pts, ww +494 | n/a | n/a | n/a |
| asia | a | -6096 $/wk, DD +37.9%, ww +434, stops 4.95(6.24), b5 52%, w2l 2 | n/a | n/a | n/a |
| asia | b | -5000 $/wk, DD +34.3%, ww +434, stops 4.57(6.24), b5 60%, w2l 0 | n/a | n/a | n/a |
| asia | c | -2980 $/wk, DD +39.8%, ww -4497, stops 5.02(6.24), b5 59%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | +1097 $/wk, DD -3.6 pts, ww +0 | n/a | n/a | n/a |
| asia | **c-a** | +3117 $/wk, DD +1.9 pts, ww -4931 | n/a | n/a | n/a |
| london | a | +4077 $/wk, DD +17.0%, ww +902, stops 1.83(2.74), b5 121%, w2l 0 | n/a | n/a | n/a |
| london | b | -3402 $/wk, DD +9.1%, ww +5049, stops 1.90(2.74), b5 59%, w2l 2 | n/a | n/a | n/a |
| london | c | -2565 $/wk, DD +7.9%, ww +10854, stops 1.75(2.74), b5 63%, w2l 2 | n/a | n/a | n/a |
| london | **b-a** | -7479 $/wk, DD -7.9 pts, ww +4147 | n/a | n/a | n/a |
| london | **c-a** | -6642 $/wk, DD -9.1 pts, ww +9952 | n/a | n/a | n/a |
| nyam | a | -78 $/wk, DD -11.6%, ww -6114, stops 1.75(1.29), b5 88%, w2l 3 | n/a | n/a | n/a |
| nyam | b | +452 $/wk, DD +3.4%, ww -6584, stops 1.52(1.29), b5 84%, w2l 2 | n/a | n/a | n/a |
| nyam | c | +1515 $/wk, DD +26.6%, ww -1092, stops 1.37(1.29), b5 79%, w2l 0 | n/a | n/a | n/a |
| nyam | **b-a** | +530 $/wk, DD +14.9 pts, ww -469 | n/a | n/a | n/a |
| nyam | **c-a** | +1593 $/wk, DD +38.1 pts, ww +5023 | n/a | n/a | n/a |
| nypm | a | -61 $/wk, DD -64.8%, ww +822, stops 0.08(0.08), b5 106%, w2l 3 | n/a | n/a | n/a |
| nypm | b | -1037 $/wk, DD -160.4%, ww -3994, stops 0.15(0.08), b5 61%, w2l 3 | n/a | n/a | n/a |
| nypm | c | -557 $/wk, DD -15.3%, ww -244, stops 0.08(0.08), b5 53%, w2l 2 | n/a | n/a | n/a |
| nypm | **b-a** | -975 $/wk, DD -95.6 pts, ww -4816 | n/a | n/a | n/a |
| nypm | **c-a** | -495 $/wk, DD +49.4 pts, ww -1067 | n/a | n/a | n/a |

**D4II125** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -1553 $/wk, DD -14.5%, ww -5282, stops 10.42(10.35), b5 87%, w2l 0 | n/a | n/a | n/a |
| all | b | -3564 $/wk, DD +12.9%, ww +6917, stops 9.97(10.35), b5 77%, w2l 1 | n/a | n/a | n/a |
| all | c | -671 $/wk, DD +13.1%, ww +6820, stops 9.89(10.35), b5 92%, w2l 1 | n/a | n/a | n/a |
| all | **b-a** | -2011 $/wk, DD +27.4 pts, ww +12199 | n/a | n/a | n/a |
| all | **c-a** | +882 $/wk, DD +27.5 pts, ww +12101 | n/a | n/a | n/a |
| asia | a | -770 $/wk, DD -9.6%, ww -4637, stops 6.54(6.24), b5 102%, w2l 0 | n/a | n/a | n/a |
| asia | b | +563 $/wk, DD +6.9%, ww -501, stops 6.24(6.24), b5 99%, w2l 0 | n/a | n/a | n/a |
| asia | c | +901 $/wk, DD +2.3%, ww -2781, stops 5.86(6.24), b5 105%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | +1333 $/wk, DD +16.5 pts, ww +4136 | n/a | n/a | n/a |
| asia | **c-a** | +1670 $/wk, DD +11.9 pts, ww +1856 | n/a | n/a | n/a |
| london | a | -1253 $/wk, DD -1.0%, ww -1913, stops 2.66(2.74), b5 88%, w2l 0 | n/a | n/a | n/a |
| london | b | -2861 $/wk, DD +33.3%, ww -3583, stops 2.36(2.74), b5 58%, w2l 1 | n/a | n/a | n/a |
| london | c | -2248 $/wk, DD +20.3%, ww +938, stops 2.66(2.74), b5 79%, w2l 1 | n/a | n/a | n/a |
| london | **b-a** | -1608 $/wk, DD +34.2 pts, ww -1670 | n/a | n/a | n/a |
| london | **c-a** | -995 $/wk, DD +21.3 pts, ww +2851 | n/a | n/a | n/a |
| nyam | a | +691 $/wk, DD +15.7%, ww +1483, stops 1.14(1.29), b5 108%, w2l 2 | n/a | n/a | n/a |
| nyam | b | -310 $/wk, DD -10.1%, ww -1922, stops 1.29(1.29), b5 100%, w2l 2 | n/a | n/a | n/a |
| nyam | c | +854 $/wk, DD +37.5%, ww +1503, stops 1.29(1.29), b5 94%, w2l 1 | n/a | n/a | n/a |
| nyam | **b-a** | -1001 $/wk, DD -25.8 pts, ww -3405 | n/a | n/a | n/a |
| nyam | **c-a** | +164 $/wk, DD +21.7 pts, ww +20 | n/a | n/a | n/a |
| nypm | a | -221 $/wk, DD -24.0%, ww +376, stops 0.08(0.08), b5 94%, w2l 0 | n/a | n/a | n/a |
| nypm | b | -956 $/wk, DD -42.2%, ww +97, stops 0.08(0.08), b5 22%, w2l 3 | n/a | n/a | n/a |
| nypm | c | -178 $/wk, DD +23.2%, ww +2467, stops 0.08(0.08), b5 78%, w2l 3 | n/a | n/a | n/a |
| nypm | **b-a** | -735 $/wk, DD -18.2 pts, ww -279 | n/a | n/a | n/a |
| nypm | **c-a** | +43 $/wk, DD +47.2 pts, ww +2090 | n/a | n/a | n/a |

**D4III125** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | +910 $/wk, DD +3.0%, ww +726, stops 10.58(10.35), b5 94%, w2l 0 | n/a | n/a | n/a |
| all | b | -4087 $/wk, DD -8.3%, ww -6184, stops 10.50(10.35), b5 78%, w2l 0 | n/a | n/a | n/a |
| all | c | +103 $/wk, DD +3.1%, ww +1537, stops 10.04(10.35), b5 97%, w2l 1 | n/a | n/a | n/a |
| all | **b-a** | -4997 $/wk, DD -11.3 pts, ww -6911 | n/a | n/a | n/a |
| all | **c-a** | -807 $/wk, DD +0.0 pts, ww +810 | n/a | n/a | n/a |
| asia | a | -1036 $/wk, DD +8.2%, ww +434, stops 6.24(6.24), b5 94%, w2l 1 | n/a | n/a | n/a |
| asia | b | -910 $/wk, DD +5.9%, ww +434, stops 6.24(6.24), b5 94%, w2l 1 | n/a | n/a | n/a |
| asia | c | -277 $/wk, DD +0.4%, ww -2746, stops 6.16(6.24), b5 94%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | +127 $/wk, DD -2.3 pts, ww +0 | n/a | n/a | n/a |
| asia | **c-a** | +759 $/wk, DD -7.8 pts, ww -3180 | n/a | n/a | n/a |
| london | a | +2101 $/wk, DD +18.3%, ww +8479, stops 2.82(2.74), b5 109%, w2l 0 | n/a | n/a | n/a |
| london | b | -1798 $/wk, DD +0.1%, ww +6145, stops 2.66(2.74), b5 73%, w2l 0 | n/a | n/a | n/a |
| london | c | +872 $/wk, DD +6.6%, ww +8170, stops 2.43(2.74), b5 100%, w2l 0 | n/a | n/a | n/a |
| london | **b-a** | -3899 $/wk, DD -18.3 pts, ww -2334 | n/a | n/a | n/a |
| london | **c-a** | -1229 $/wk, DD -11.7 pts, ww -309 | n/a | n/a | n/a |
| nyam | a | +542 $/wk, DD -22.0%, ww -4321, stops 1.45(1.29), b5 99%, w2l 0 | n/a | n/a | n/a |
| nyam | b | -292 $/wk, DD -52.4%, ww -6230, stops 1.52(1.29), b5 73%, w2l 1 | n/a | n/a | n/a |
| nyam | c | +371 $/wk, DD +2.8%, ww -4321, stops 1.37(1.29), b5 71%, w2l 0 | n/a | n/a | n/a |
| nyam | **b-a** | -833 $/wk, DD -30.4 pts, ww -1909 | n/a | n/a | n/a |
| nyam | **c-a** | -170 $/wk, DD +24.8 pts, ww +0 | n/a | n/a | n/a |
| nypm | a | -697 $/wk, DD -87.2%, ww -286, stops 0.08(0.08), b5 92%, w2l 0 | n/a | n/a | n/a |
| nypm | b | -1088 $/wk, DD -110.2%, ww -1102, stops 0.08(0.08), b5 77%, w2l 1 | n/a | n/a | n/a |
| nypm | c | -863 $/wk, DD -38.6%, ww -479, stops 0.08(0.08), b5 42%, w2l 1 | n/a | n/a | n/a |
| nypm | **b-a** | -391 $/wk, DD -23.0 pts, ww -816 | n/a | n/a | n/a |
| nypm | **c-a** | -166 $/wk, DD +48.6 pts, ww -193 | n/a | n/a | n/a |

### Dial 5 replace atr_rel in live layers (REG half-size, skip) by the forecast ratio (A-cells = live atr_rel reference)

**D5R13F** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -306 $/wk, DD -2.5%, ww +492, stops 10.20(10.35), b5 101%, w2l 1 | n/a | n/a | n/a |
| all | b | -1183 $/wk, DD +16.9%, ww +10345, stops 10.20(10.35), b5 100%, w2l 1 | n/a | n/a | n/a |
| all | c | +713 $/wk, DD +19.7%, ww +10871, stops 10.20(10.35), b5 102%, w2l 0 | n/a | n/a | n/a |
| all | **b-a** | -877 $/wk, DD +19.4 pts, ww +9852 | n/a | n/a | n/a |
| all | **c-a** | +1018 $/wk, DD +22.2 pts, ww +10378 | n/a | n/a | n/a |
| asia | a | -454 $/wk, DD +7.1%, ww +492, stops 6.16(6.24), b5 94%, w2l 0 | n/a | n/a | n/a |
| asia | b | -123 $/wk, DD +24.1%, ww +5507, stops 6.24(6.24), b5 92%, w2l 0 | n/a | n/a | n/a |
| asia | c | -283 $/wk, DD +24.1%, ww +6386, stops 6.16(6.24), b5 90%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | +331 $/wk, DD +17.0 pts, ww +5014 | n/a | n/a | n/a |
| asia | **c-a** | +172 $/wk, DD +17.0 pts, ww +5894 | n/a | n/a | n/a |
| london | a | +226 $/wk, DD +7.1%, ww +0, stops 2.66(2.74), b5 100%, w2l 0 | n/a | n/a | n/a |
| london | b | -419 $/wk, DD +0.0%, ww +0, stops 2.59(2.74), b5 95%, w2l 0 | n/a | n/a | n/a |
| london | c | +373 $/wk, DD +9.1%, ww +0, stops 2.66(2.74), b5 100%, w2l 1 | n/a | n/a | n/a |
| london | **b-a** | -645 $/wk, DD -7.1 pts, ww +0 | n/a | n/a | n/a |
| london | **c-a** | +147 $/wk, DD +2.1 pts, ww +0 | n/a | n/a | n/a |
| nyam | a | -77 $/wk, DD +1.0%, ww +0, stops 1.29(1.29), b5 97%, w2l 0 | n/a | n/a | n/a |
| nyam | b | -456 $/wk, DD +26.5%, ww +0, stops 1.29(1.29), b5 70%, w2l 1 | n/a | n/a | n/a |
| nyam | c | +441 $/wk, DD +26.5%, ww +0, stops 1.29(1.29), b5 100%, w2l 0 | n/a | n/a | n/a |
| nyam | **b-a** | -379 $/wk, DD +25.5 pts, ww +0 | n/a | n/a | n/a |
| nyam | **c-a** | +518 $/wk, DD +25.5 pts, ww +0 | n/a | n/a | n/a |
| nypm | a | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | n/a | n/a | n/a |
| nypm | b | -184 $/wk, DD -0.0%, ww +0, stops 0.08(0.08), b5 64%, w2l 0 | n/a | n/a | n/a |
| nypm | c | +182 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | n/a | n/a | n/a |
| nypm | **b-a** | -184 $/wk, DD -0.0 pts, ww +0 | n/a | n/a | n/a |
| nypm | **c-a** | +182 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |

**D5R115F** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -912 $/wk, DD -1.0%, ww +1267, stops 10.20(10.35), b5 102%, w2l 1 | n/a | n/a | n/a |
| all | b | -4417 $/wk, DD +14.1%, ww +10636, stops 10.04(10.35), b5 96%, w2l 2 | n/a | n/a | n/a |
| all | c | -5275 $/wk, DD +14.6%, ww +13161, stops 10.12(10.35), b5 88%, w2l 2 | n/a | n/a | n/a |
| all | **b-a** | -3505 $/wk, DD +15.2 pts, ww +9369 | n/a | n/a | n/a |
| all | **c-a** | -4363 $/wk, DD +15.6 pts, ww +11894 | n/a | n/a | n/a |
| asia | a | -720 $/wk, DD +8.7%, ww +1280, stops 6.16(6.24), b5 90%, w2l 0 | n/a | n/a | n/a |
| asia | b | -1730 $/wk, DD +20.6%, ww +7005, stops 6.16(6.24), b5 83%, w2l 0 | n/a | n/a | n/a |
| asia | c | -1829 $/wk, DD +20.6%, ww +7005, stops 6.16(6.24), b5 83%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | -1010 $/wk, DD +11.8 pts, ww +5725 | n/a | n/a | n/a |
| asia | **c-a** | -1109 $/wk, DD +11.8 pts, ww +5725 | n/a | n/a | n/a |
| london | a | -127 $/wk, DD +7.1%, ww +0, stops 2.66(2.74), b5 95%, w2l 0 | n/a | n/a | n/a |
| london | b | -1157 $/wk, DD -1.8%, ww -1199, stops 2.59(2.74), b5 84%, w2l 1 | n/a | n/a | n/a |
| london | c | -1865 $/wk, DD +6.5%, ww -1199, stops 2.59(2.74), b5 77%, w2l 1 | n/a | n/a | n/a |
| london | **b-a** | -1031 $/wk, DD -8.9 pts, ww -1199 | n/a | n/a | n/a |
| london | **c-a** | -1739 $/wk, DD -0.6 pts, ww -1199 | n/a | n/a | n/a |
| nyam | a | +395 $/wk, DD +8.6%, ww +0, stops 1.29(1.29), b5 97%, w2l 0 | n/a | n/a | n/a |
| nyam | b | -1279 $/wk, DD -22.6%, ww +0, stops 1.22(1.29), b5 60%, w2l 2 | n/a | n/a | n/a |
| nyam | c | -692 $/wk, DD -25.9%, ww +0, stops 1.29(1.29), b5 72%, w2l 1 | n/a | n/a | n/a |
| nyam | **b-a** | -1674 $/wk, DD -31.2 pts, ww +0 | n/a | n/a | n/a |
| nyam | **c-a** | -1088 $/wk, DD -34.5 pts, ww +0 | n/a | n/a | n/a |
| nypm | a | -460 $/wk, DD -27.2%, ww -286, stops 0.08(0.08), b5 82%, w2l 0 | n/a | n/a | n/a |
| nypm | b | -251 $/wk, DD -0.0%, ww +316, stops 0.08(0.08), b5 55%, w2l 0 | n/a | n/a | n/a |
| nypm | c | -888 $/wk, DD -48.0%, ww -286, stops 0.08(0.08), b5 39%, w2l 1 | n/a | n/a | n/a |
| nypm | **b-a** | +210 $/wk, DD +27.2 pts, ww +602 | n/a | n/a | n/a |
| nypm | **c-a** | -427 $/wk, DD -20.8 pts, ww +0 | n/a | n/a | n/a |

**D5SK13F** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -764 $/wk, DD -0.2%, ww +43, stops 9.82(10.35), b5 100%, w2l 1 | n/a | n/a | n/a |
| all | b | -1574 $/wk, DD +12.9%, ww +10306, stops 9.21(10.35), b5 100%, w2l 1 | n/a | n/a | n/a |
| all | c | -777 $/wk, DD -16.2%, ww +10525, stops 9.05(10.35), b5 101%, w2l 1 | n/a | n/a | n/a |
| all | **b-a** | -810 $/wk, DD +13.1 pts, ww +10264 | n/a | n/a | n/a |
| all | **c-a** | -13 $/wk, DD -16.0 pts, ww +10483 | n/a | n/a | n/a |
| asia | a | +595 $/wk, DD +39.0%, ww +4539, stops 5.48(6.24), b5 92%, w2l 0 | n/a | n/a | n/a |
| asia | b | +23 $/wk, DD +59.8%, ww +12753, stops 5.02(6.24), b5 79%, w2l 0 | n/a | n/a | n/a |
| asia | c | -215 $/wk, DD +59.8%, ww +12753, stops 4.72(6.24), b5 78%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | -572 $/wk, DD +20.8 pts, ww +8214 | n/a | n/a | n/a |
| asia | **c-a** | -810 $/wk, DD +20.8 pts, ww +8214 | n/a | n/a | n/a |
| london | a | +295 $/wk, DD +9.8%, ww +0, stops 2.89(2.74), b5 99%, w2l 0 | n/a | n/a | n/a |
| london | b | -883 $/wk, DD +0.0%, ww +0, stops 2.66(2.74), b5 91%, w2l 0 | n/a | n/a | n/a |
| london | c | -325 $/wk, DD +9.8%, ww +0, stops 2.66(2.74), b5 103%, w2l 1 | n/a | n/a | n/a |
| london | **b-a** | -1178 $/wk, DD -9.8 pts, ww +0 | n/a | n/a | n/a |
| london | **c-a** | -621 $/wk, DD -0.0 pts, ww +0 | n/a | n/a | n/a |
| nyam | a | -1463 $/wk, DD -27.0%, ww +0, stops 1.37(1.29), b5 62%, w2l 2 | n/a | n/a | n/a |
| nyam | b | -388 $/wk, DD +30.8%, ww +0, stops 1.45(1.29), b5 72%, w2l 1 | n/a | n/a | n/a |
| nyam | c | +147 $/wk, DD +23.7%, ww -642, stops 1.52(1.29), b5 96%, w2l 1 | n/a | n/a | n/a |
| nyam | **b-a** | +1075 $/wk, DD +57.8 pts, ww +0 | n/a | n/a | n/a |
| nyam | **c-a** | +1610 $/wk, DD +50.8 pts, ww -642 | n/a | n/a | n/a |
| nypm | a | -191 $/wk, DD -28.6%, ww +0, stops 0.08(0.08), b5 98%, w2l 0 | n/a | n/a | n/a |
| nypm | b | -326 $/wk, DD -0.0%, ww +0, stops 0.08(0.08), b5 67%, w2l 0 | n/a | n/a | n/a |
| nypm | c | -384 $/wk, DD -28.6%, ww +0, stops 0.15(0.08), b5 95%, w2l 0 | n/a | n/a | n/a |
| nypm | **b-a** | -135 $/wk, DD +28.6 pts, ww +0 | n/a | n/a | n/a |
| nypm | **c-a** | -193 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |

**D5LO8F** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -816 $/wk, DD +0.0%, ww +0, stops 10.27(10.35), b5 98%, w2l 0 | n/a | n/a | n/a |
| all | b | -634 $/wk, DD +7.1%, ww +3713, stops 10.12(10.35), b5 92%, w2l 0 | n/a | n/a | n/a |
| all | c | -862 $/wk, DD +7.1%, ww +3713, stops 10.20(10.35), b5 99%, w2l 0 | n/a | n/a | n/a |
| all | **b-a** | +182 $/wk, DD +7.1 pts, ww +3713 | n/a | n/a | n/a |
| all | **c-a** | -46 $/wk, DD +7.1 pts, ww +3713 | n/a | n/a | n/a |
| asia | a | +48 $/wk, DD +0.0%, ww +0, stops 6.16(6.24), b5 100%, w2l 0 | n/a | n/a | n/a |
| asia | b | +922 $/wk, DD +7.7%, ww +434, stops 6.09(6.24), b5 94%, w2l 0 | n/a | n/a | n/a |
| asia | c | +99 $/wk, DD +7.7%, ww +434, stops 6.16(6.24), b5 94%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | +873 $/wk, DD +7.7 pts, ww +434 | n/a | n/a | n/a |
| asia | **c-a** | +50 $/wk, DD +7.7 pts, ww +434 | n/a | n/a | n/a |
| london | a | -167 $/wk, DD -1.2%, ww +0, stops 2.74(2.74), b5 100%, w2l 0 | n/a | n/a | n/a |
| london | b | -626 $/wk, DD +21.9%, ww +950, stops 2.66(2.74), b5 90%, w2l 0 | n/a | n/a | n/a |
| london | c | +155 $/wk, DD +9.6%, ww +0, stops 2.66(2.74), b5 102%, w2l 0 | n/a | n/a | n/a |
| london | **b-a** | -459 $/wk, DD +23.0 pts, ww +950 | n/a | n/a | n/a |
| london | **c-a** | +322 $/wk, DD +10.8 pts, ww +0 | n/a | n/a | n/a |
| nyam | a | -611 $/wk, DD -4.9%, ww -2951, stops 1.29(1.29), b5 94%, w2l 0 | n/a | n/a | n/a |
| nyam | b | -627 $/wk, DD -18.9%, ww -413, stops 1.29(1.29), b5 89%, w2l 2 | n/a | n/a | n/a |
| nyam | c | -713 $/wk, DD -33.8%, ww -413, stops 1.29(1.29), b5 87%, w2l 2 | n/a | n/a | n/a |
| nyam | **b-a** | -16 $/wk, DD -14.1 pts, ww +2538 | n/a | n/a | n/a |
| nyam | **c-a** | -102 $/wk, DD -28.9 pts, ww +2538 | n/a | n/a | n/a |
| nypm | a | -86 $/wk, DD -0.0%, ww +0, stops 0.08(0.08), b5 89%, w2l 2 | n/a | n/a | n/a |
| nypm | b | -302 $/wk, DD -0.0%, ww +0, stops 0.08(0.08), b5 72%, w2l 2 | n/a | n/a | n/a |
| nypm | c | -402 $/wk, DD +1.5%, ww +0, stops 0.08(0.08), b5 62%, w2l 0 | n/a | n/a | n/a |
| nypm | **b-a** | -216 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| nypm | **c-a** | -317 $/wk, DD +1.5 pts, ww +0 | n/a | n/a | n/a |

**D5R13A** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | x | -509 $/wk, DD +14.4%, ww +10121, stops 10.35(10.35), b5 101%, w2l 0 | n/a | n/a | n/a |
| asia | x | +439 $/wk, DD +11.4%, ww +1681, stops 6.16(6.24), b5 105%, w2l 0 | n/a | n/a | n/a |
| london | x | -924 $/wk, DD +0.9%, ww +0, stops 2.82(2.74), b5 96%, w2l 0 | n/a | n/a | n/a |
| nyam | x | +132 $/wk, DD +15.5%, ww +1902, stops 1.29(1.29), b5 82%, w2l 2 | n/a | n/a | n/a |
| nypm | x | -155 $/wk, DD -7.6%, ww +0, stops 0.08(0.08), b5 89%, w2l 0 | n/a | n/a | n/a |

**D5SK15A** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | x | +1476 $/wk, DD +21.5%, ww +6238, stops 9.05(10.35), b5 106%, w2l 0 | n/a | n/a | n/a |
| asia | x | +2093 $/wk, DD +45.6%, ww +11057, stops 5.93(6.24), b5 100%, w2l 0 | n/a | n/a | n/a |
| london | x | -1594 $/wk, DD +0.0%, ww +0, stops 2.82(2.74), b5 95%, w2l 0 | n/a | n/a | n/a |
| nyam | x | +1141 $/wk, DD +56.6%, ww +4530, stops 0.30(1.29), b5 74%, w2l 2 | n/a | n/a | n/a |
| nypm | x | -164 $/wk, DD +37.4%, ww +1185, stops 0.00(0.08), b5 109%, w2l 3 | n/a | n/a | n/a |

### Dial 6 entry distance (split-add dip MINDIP)

**D6T** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | +810 $/wk, DD -6.0%, ww -3395, stops 10.58(10.35), b5 100%, w2l 0 | n/a | n/a | n/a |
| all | b | +1059 $/wk, DD -10.8%, ww -5916, stops 10.65(10.35), b5 97%, w2l 0 | n/a | n/a | n/a |
| all | c | +1288 $/wk, DD -4.9%, ww -2798, stops 10.58(10.35), b5 96%, w2l 0 | n/a | n/a | n/a |
| all | **b-a** | +249 $/wk, DD -4.8 pts, ww -2521 | n/a | n/a | n/a |
| all | **c-a** | +478 $/wk, DD +1.2 pts, ww +597 | n/a | n/a | n/a |
| asia | a | +882 $/wk, DD -14.5%, ww -7268, stops 6.24(6.24), b5 108%, w2l 1 | n/a | n/a | n/a |
| asia | b | +1146 $/wk, DD -11.8%, ww -5936, stops 6.24(6.24), b5 107%, w2l 0 | n/a | n/a | n/a |
| asia | c | +1488 $/wk, DD -13.2%, ww -6646, stops 6.24(6.24), b5 107%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | +265 $/wk, DD +2.8 pts, ww +1332 | n/a | n/a | n/a |
| asia | **c-a** | +606 $/wk, DD +1.3 pts, ww +622 | n/a | n/a | n/a |
| london | a | +266 $/wk, DD +6.1%, ww +95, stops 2.89(2.74), b5 99%, w2l 0 | n/a | n/a | n/a |
| london | b | -60 $/wk, DD +7.5%, ww +1482, stops 2.97(2.74), b5 96%, w2l 0 | n/a | n/a | n/a |
| london | c | -177 $/wk, DD -0.2%, ww +0, stops 2.89(2.74), b5 96%, w2l 0 | n/a | n/a | n/a |
| london | **b-a** | -326 $/wk, DD +1.4 pts, ww +1387 | n/a | n/a | n/a |
| london | **c-a** | -443 $/wk, DD -6.3 pts, ww -95 | n/a | n/a | n/a |
| nyam | a | +4 $/wk, DD -10.2%, ww -160, stops 1.37(1.29), b5 98%, w2l 0 | n/a | n/a | n/a |
| nyam | b | +25 $/wk, DD +12.2%, ww -160, stops 1.37(1.29), b5 96%, w2l 0 | n/a | n/a | n/a |
| nyam | c | +306 $/wk, DD +12.3%, ww -5, stops 1.37(1.29), b5 96%, w2l 0 | n/a | n/a | n/a |
| nyam | **b-a** | +21 $/wk, DD +22.4 pts, ww +0 | n/a | n/a | n/a |
| nyam | **c-a** | +302 $/wk, DD +22.6 pts, ww +155 | n/a | n/a | n/a |
| nypm | a | -342 $/wk, DD -39.9%, ww -286, stops 0.08(0.08), b5 100%, w2l 0 | n/a | n/a | n/a |
| nypm | b | -52 $/wk, DD +2.5%, ww +0, stops 0.08(0.08), b5 101%, w2l 0 | n/a | n/a | n/a |
| nypm | c | -329 $/wk, DD -37.4%, ww -286, stops 0.08(0.08), b5 101%, w2l 0 | n/a | n/a | n/a |
| nypm | **b-a** | +290 $/wk, DD +42.3 pts, ww +286 | n/a | n/a | n/a |
| nypm | **c-a** | +13 $/wk, DD +2.5 pts, ww +0 | n/a | n/a | n/a |

**D6C** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | +126 $/wk, DD -13.3%, ww -7179, stops 10.58(10.35), b5 103%, w2l 0 | n/a | n/a | n/a |
| all | b | +561 $/wk, DD -4.2%, ww -2435, stops 10.58(10.35), b5 93%, w2l 0 | n/a | n/a | n/a |
| all | c | +1041 $/wk, DD -4.6%, ww -2655, stops 10.50(10.35), b5 95%, w2l 0 | n/a | n/a | n/a |
| all | **b-a** | +434 $/wk, DD +9.1 pts, ww +4743 | n/a | n/a | n/a |
| all | **c-a** | +915 $/wk, DD +8.7 pts, ww +4523 | n/a | n/a | n/a |
| asia | a | -118 $/wk, DD -22.3%, ww -11052, stops 6.24(6.24), b5 107%, w2l 1 | n/a | n/a | n/a |
| asia | b | +503 $/wk, DD -12.2%, ww -6168, stops 6.24(6.24), b5 100%, w2l 0 | n/a | n/a | n/a |
| asia | c | +1046 $/wk, DD -12.9%, ww -6488, stops 6.24(6.24), b5 105%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | +621 $/wk, DD +10.1 pts, ww +4883 | n/a | n/a | n/a |
| asia | **c-a** | +1164 $/wk, DD +9.4 pts, ww +4563 | n/a | n/a | n/a |
| london | a | +112 $/wk, DD -0.2%, ww +5, stops 2.89(2.74), b5 100%, w2l 0 | n/a | n/a | n/a |
| london | b | +158 $/wk, DD +10.9%, ww +1532, stops 2.89(2.74), b5 97%, w2l 0 | n/a | n/a | n/a |
| london | c | -294 $/wk, DD -6.0%, ww +1424, stops 2.89(2.74), b5 96%, w2l 0 | n/a | n/a | n/a |
| london | **b-a** | +46 $/wk, DD +11.1 pts, ww +1527 | n/a | n/a | n/a |
| london | **c-a** | -406 $/wk, DD -5.8 pts, ww +1419 | n/a | n/a | n/a |
| nyam | a | +448 $/wk, DD -14.0%, ww -711, stops 1.37(1.29), b5 116%, w2l 0 | n/a | n/a | n/a |
| nyam | b | +222 $/wk, DD +10.3%, ww -663, stops 1.37(1.29), b5 95%, w2l 0 | n/a | n/a | n/a |
| nyam | c | +640 $/wk, DD +17.6%, ww -663, stops 1.29(1.29), b5 96%, w2l 0 | n/a | n/a | n/a |
| nyam | **b-a** | -226 $/wk, DD +24.3 pts, ww +48 | n/a | n/a | n/a |
| nyam | **c-a** | +193 $/wk, DD +31.5 pts, ww +48 | n/a | n/a | n/a |
| nypm | a | -315 $/wk, DD -34.3%, ww -196, stops 0.08(0.08), b5 101%, w2l 0 | n/a | n/a | n/a |
| nypm | b | -322 $/wk, DD -35.8%, ww -286, stops 0.08(0.08), b5 101%, w2l 0 | n/a | n/a | n/a |
| nypm | c | -351 $/wk, DD -37.4%, ww -286, stops 0.08(0.08), b5 99%, w2l 0 | n/a | n/a | n/a |
| nypm | **b-a** | -7 $/wk, DD -1.5 pts, ww -90 | n/a | n/a | n/a |
| nypm | **c-a** | -36 $/wk, DD -3.1 pts, ww -90 | n/a | n/a | n/a |

**D6KT** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -1487 $/wk, DD -12.3%, ww -6659, stops 10.50(10.35), b5 100%, w2l 0 | n/a | n/a | n/a |
| all | b | -2027 $/wk, DD -20.6%, ww -10988, stops 10.35(10.35), b5 97%, w2l 0 | n/a | n/a | n/a |
| all | c | -2233 $/wk, DD -29.1%, ww -15444, stops 10.42(10.35), b5 99%, w2l 0 | n/a | n/a | n/a |
| all | **b-a** | -540 $/wk, DD -8.3 pts, ww -4329 | n/a | n/a | n/a |
| all | **c-a** | -746 $/wk, DD -16.8 pts, ww -8785 | n/a | n/a | n/a |
| asia | a | -1610 $/wk, DD -16.2%, ww -8076, stops 6.24(6.24), b5 100%, w2l 0 | n/a | n/a | n/a |
| asia | b | -1907 $/wk, DD -8.1%, ww -4176, stops 6.24(6.24), b5 96%, w2l 0 | n/a | n/a | n/a |
| asia | c | -2414 $/wk, DD -20.0%, ww -9928, stops 6.24(6.24), b5 96%, w2l 1 | n/a | n/a | n/a |
| asia | **b-a** | -297 $/wk, DD +8.1 pts, ww +3900 | n/a | n/a | n/a |
| asia | **c-a** | -804 $/wk, DD -3.8 pts, ww -1852 | n/a | n/a | n/a |
| london | a | +364 $/wk, DD -7.4%, ww -1284, stops 2.89(2.74), b5 104%, w2l 0 | n/a | n/a | n/a |
| london | b | -361 $/wk, DD -9.7%, ww -664, stops 2.82(2.74), b5 105%, w2l 1 | n/a | n/a | n/a |
| london | c | -190 $/wk, DD -11.9%, ww +0, stops 2.82(2.74), b5 106%, w2l 0 | n/a | n/a | n/a |
| london | **b-a** | -725 $/wk, DD -2.3 pts, ww +620 | n/a | n/a | n/a |
| london | **c-a** | -554 $/wk, DD -4.5 pts, ww +1284 | n/a | n/a | n/a |
| nyam | a | +100 $/wk, DD -3.1%, ww -2951, stops 1.29(1.29), b5 99%, w2l 0 | n/a | n/a | n/a |
| nyam | b | -246 $/wk, DD +6.5%, ww +0, stops 1.22(1.29), b5 86%, w2l 0 | n/a | n/a | n/a |
| nyam | c | +484 $/wk, DD +18.3%, ww +0, stops 1.29(1.29), b5 97%, w2l 0 | n/a | n/a | n/a |
| nyam | **b-a** | -346 $/wk, DD +9.5 pts, ww +2951 | n/a | n/a | n/a |
| nyam | **c-a** | +384 $/wk, DD +21.3 pts, ww +2951 | n/a | n/a | n/a |
| nypm | a | -341 $/wk, DD -35.9%, ww -538, stops 0.08(0.08), b5 113%, w2l 1 | n/a | n/a | n/a |
| nypm | b | +487 $/wk, DD -27.3%, ww -855, stops 0.08(0.08), b5 100%, w2l 1 | n/a | n/a | n/a |
| nypm | c | -112 $/wk, DD -48.2%, ww -1784, stops 0.08(0.08), b5 95%, w2l 1 | n/a | n/a | n/a |
| nypm | **b-a** | +828 $/wk, DD +8.6 pts, ww -316 | n/a | n/a | n/a |
| nypm | **c-a** | +229 $/wk, DD -12.3 pts, ww -1246 | n/a | n/a | n/a |

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
| all | a | -52 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a |
| all | b | -135 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 99%, w2l 0 | n/a | n/a | n/a |
| all | c | -7 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 99%, w2l 0 | n/a | n/a | n/a |
| all | **b-a** | -84 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| all | **c-a** | +45 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| asia | a | -20 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 100%, w2l 0 | n/a | n/a | n/a |
| asia | b | -135 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 99%, w2l 0 | n/a | n/a | n/a |
| asia | c | -27 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 99%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | -115 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| asia | **c-a** | -7 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| london | a | -31 $/wk, DD -0.6%, ww +0, stops 2.74(2.74), b5 100%, w2l 0 | n/a | n/a | n/a |
| london | b | +0 $/wk, DD +0.0%, ww +0, stops 2.74(2.74), b5 100%, w2l 0 | n/a | n/a | n/a |
| london | c | -80 $/wk, DD -0.6%, ww +0, stops 2.74(2.74), b5 100%, w2l 0 | n/a | n/a | n/a |
| london | **b-a** | +31 $/wk, DD +0.6 pts, ww +0 | n/a | n/a | n/a |
| london | **c-a** | -48 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| nyam | a | +0 $/wk, DD +0.0%, ww +0, stops 1.29(1.29), b5 100%, w2l 0 | n/a | n/a | n/a |
| nyam | b | +0 $/wk, DD +0.0%, ww +0, stops 1.29(1.29), b5 100%, w2l 0 | n/a | n/a | n/a |
| nyam | c | +100 $/wk, DD +6.8%, ww +0, stops 1.29(1.29), b5 100%, w2l 0 | n/a | n/a | n/a |
| nyam | **b-a** | +0 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| nyam | **c-a** | +100 $/wk, DD +6.8 pts, ww +0 | n/a | n/a | n/a |
| nypm | a | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | n/a | n/a | n/a |
| nypm | b | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | n/a | n/a | n/a |
| nypm | c | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | n/a | n/a | n/a |
| nypm | **b-a** | +0 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| nypm | **c-a** | +0 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |

**D6HC** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -163 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 100%, w2l 0 | n/a | n/a | n/a |
| all | b | +24 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 99%, w2l 0 | n/a | n/a | n/a |
| all | c | -7 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 99%, w2l 0 | n/a | n/a | n/a |
| all | **b-a** | +187 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| all | **c-a** | +156 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| asia | a | +5 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 100%, w2l 0 | n/a | n/a | n/a |
| asia | b | -27 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 99%, w2l 0 | n/a | n/a | n/a |
| asia | c | -27 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 99%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | -32 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| asia | **c-a** | -32 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| london | a | -168 $/wk, DD -0.6%, ww +0, stops 2.74(2.74), b5 98%, w2l 0 | n/a | n/a | n/a |
| london | b | -48 $/wk, DD +0.0%, ww +0, stops 2.74(2.74), b5 100%, w2l 0 | n/a | n/a | n/a |
| london | c | -80 $/wk, DD -0.6%, ww +0, stops 2.74(2.74), b5 100%, w2l 0 | n/a | n/a | n/a |
| london | **b-a** | +120 $/wk, DD +0.6 pts, ww +0 | n/a | n/a | n/a |
| london | **c-a** | +89 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| nyam | a | +0 $/wk, DD +0.0%, ww +0, stops 1.29(1.29), b5 100%, w2l 0 | n/a | n/a | n/a |
| nyam | b | +100 $/wk, DD +6.8%, ww +0, stops 1.29(1.29), b5 100%, w2l 0 | n/a | n/a | n/a |
| nyam | c | +100 $/wk, DD +6.8%, ww +0, stops 1.29(1.29), b5 100%, w2l 0 | n/a | n/a | n/a |
| nyam | **b-a** | +100 $/wk, DD +6.8 pts, ww +0 | n/a | n/a | n/a |
| nyam | **c-a** | +100 $/wk, DD +6.8 pts, ww +0 | n/a | n/a | n/a |
| nypm | a | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | n/a | n/a | n/a |
| nypm | b | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | n/a | n/a | n/a |
| nypm | c | +0 $/wk, DD +0.0%, ww +0, stops 0.08(0.08), b5 100%, w2l 0 | n/a | n/a | n/a |
| nypm | **b-a** | +0 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| nypm | **c-a** | +0 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |

### Dial 7 lock levels (BookLock peak 2R threshold)

**D7T** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | +353 $/wk, DD +7.2%, ww +3778, stops 9.89(10.35), b5 100%, w2l 0 | n/a | n/a | n/a |
| all | b | -2051 $/wk, DD +0.0%, ww +0, stops 10.35(10.35), b5 91%, w2l 0 | n/a | n/a | n/a |
| all | c | -2388 $/wk, DD +7.2%, ww +3778, stops 10.12(10.35), b5 93%, w2l 0 | n/a | n/a | n/a |
| all | **b-a** | -2404 $/wk, DD -7.2 pts, ww -3778 | n/a | n/a | n/a |
| all | **c-a** | -2740 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| asia | a | +646 $/wk, DD +0.0%, ww +0, stops 5.93(6.24), b5 100%, w2l 0 | n/a | n/a | n/a |
| asia | b | -922 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 93%, w2l 0 | n/a | n/a | n/a |
| asia | c | -1181 $/wk, DD +0.0%, ww +0, stops 6.16(6.24), b5 93%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | -1569 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| asia | **c-a** | -1827 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| london | a | -466 $/wk, DD +0.0%, ww +0, stops 2.66(2.74), b5 90%, w2l 0 | n/a | n/a | n/a |
| london | b | -1200 $/wk, DD +1.1%, ww +0, stops 2.82(2.74), b5 91%, w2l 0 | n/a | n/a | n/a |
| london | c | -1205 $/wk, DD +1.1%, ww +0, stops 2.74(2.74), b5 87%, w2l 0 | n/a | n/a | n/a |
| london | **b-a** | -733 $/wk, DD +1.1 pts, ww +0 | n/a | n/a | n/a |
| london | **c-a** | -739 $/wk, DD +1.1 pts, ww +0 | n/a | n/a | n/a |
| nyam | a | +782 $/wk, DD +28.4%, ww +658, stops 1.22(1.29), b5 102%, w2l 0 | n/a | n/a | n/a |
| nyam | b | +402 $/wk, DD +35.4%, ww +658, stops 1.22(1.29), b5 91%, w2l 1 | n/a | n/a | n/a |
| nyam | c | +609 $/wk, DD +24.0%, ww +658, stops 1.14(1.29), b5 94%, w2l 0 | n/a | n/a | n/a |
| nyam | **b-a** | -380 $/wk, DD +7.0 pts, ww +0 | n/a | n/a | n/a |
| nyam | **c-a** | -174 $/wk, DD -4.4 pts, ww +0 | n/a | n/a | n/a |
| nypm | a | -609 $/wk, DD -39.9%, ww -286, stops 0.08(0.08), b5 96%, w2l 2 | n/a | n/a | n/a |
| nypm | b | -332 $/wk, DD -9.3%, ww +0, stops 0.08(0.08), b5 96%, w2l 2 | n/a | n/a | n/a |
| nypm | c | -609 $/wk, DD -39.9%, ww -286, stops 0.08(0.08), b5 96%, w2l 2 | n/a | n/a | n/a |
| nypm | **b-a** | +278 $/wk, DD +30.6 pts, ww +286 | n/a | n/a | n/a |
| nypm | **c-a** | +0 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |

**D7C** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -760 $/wk, DD +0.0%, ww +0, stops 10.04(10.35), b5 95%, w2l 0 | n/a | n/a | n/a |
| all | b | -1052 $/wk, DD +0.0%, ww +0, stops 10.20(10.35), b5 99%, w2l 0 | n/a | n/a | n/a |
| all | c | -788 $/wk, DD +0.0%, ww +0, stops 10.20(10.35), b5 101%, w2l 0 | n/a | n/a | n/a |
| all | **b-a** | -292 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| all | **c-a** | -27 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| asia | a | -517 $/wk, DD +0.0%, ww +0, stops 5.93(6.24), b5 94%, w2l 0 | n/a | n/a | n/a |
| asia | b | -442 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 98%, w2l 0 | n/a | n/a | n/a |
| asia | c | -329 $/wk, DD +0.0%, ww +0, stops 6.24(6.24), b5 98%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | +74 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| asia | **c-a** | +187 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| london | a | -389 $/wk, DD +1.7%, ww +0, stops 2.74(2.74), b5 94%, w2l 0 | n/a | n/a | n/a |
| london | b | -1220 $/wk, DD +1.1%, ww +0, stops 2.74(2.74), b5 90%, w2l 0 | n/a | n/a | n/a |
| london | c | -1070 $/wk, DD +1.1%, ww +0, stops 2.74(2.74), b5 92%, w2l 0 | n/a | n/a | n/a |
| london | **b-a** | -831 $/wk, DD -0.6 pts, ww +0 | n/a | n/a | n/a |
| london | **c-a** | -681 $/wk, DD -0.6 pts, ww +0 | n/a | n/a | n/a |
| nyam | a | +347 $/wk, DD +23.9%, ww +658, stops 1.29(1.29), b5 96%, w2l 0 | n/a | n/a | n/a |
| nyam | b | +943 $/wk, DD +33.6%, ww +658, stops 1.14(1.29), b5 112%, w2l 1 | n/a | n/a | n/a |
| nyam | c | +943 $/wk, DD +26.6%, ww +658, stops 1.14(1.29), b5 115%, w2l 0 | n/a | n/a | n/a |
| nyam | **b-a** | +595 $/wk, DD +9.7 pts, ww +0 | n/a | n/a | n/a |
| nyam | **c-a** | +596 $/wk, DD +2.6 pts, ww +0 | n/a | n/a | n/a |
| nypm | a | -202 $/wk, DD -9.3%, ww +0, stops 0.08(0.08), b5 96%, w2l 2 | n/a | n/a | n/a |
| nypm | b | -332 $/wk, DD -9.3%, ww +0, stops 0.08(0.08), b5 96%, w2l 2 | n/a | n/a | n/a |
| nypm | c | -332 $/wk, DD -9.3%, ww +0, stops 0.08(0.08), b5 96%, w2l 2 | n/a | n/a | n/a |
| nypm | **b-a** | -130 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |
| nypm | **c-a** | -130 $/wk, DD +0.0 pts, ww +0 | n/a | n/a | n/a |

## 3. Best setting per dial and per session (drawdown first: L6M + HOLD maxDD cut, tolerant gate; status says which windows it holds in)
| dial | scope | best cell | status | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|---|---|
| D2 | all | D2F_c | fails recent gate | -6967 $/wk, DD -9.6%, ww -3770, stops 13.77(10.35), b5 79%, w2l 3 | -2999 $/wk, DD -9.6%, ww -3770, stops 11.26(10.99), b5 76%, w2l 4 | n/a | n/a |
| D2 | asia | D2F_b | fails recent gate | -3571 $/wk, DD -14.4%, ww -20299, stops 8.52(6.24), b5 74%, w2l 1 | -2696 $/wk, DD -14.4%, ww -20299, stops 6.12(6.35), b5 72%, w2l 2 | n/a | n/a |
| D2 | london | D2F_b | fails recent gate | -2903 $/wk, DD +26.4%, ww +4826, stops 5.40(2.74), b5 66%, w2l 2 | -255 $/wk, DD +26.4%, ww +4826, stops 4.03(2.89), b5 79%, w2l 3 | n/a | n/a |
| D2 | nyam | D2F_a | fails recent gate | +452 $/wk, DD +17.9%, ww -2881, stops 1.98(1.29), b5 92%, w2l 0 | -130 $/wk, DD -27.1%, ww -294, stops 1.98(1.67), b5 108%, w2l 2 | n/a | n/a |
| D2 | nypm | D2F_a | fails recent gate | -30 $/wk, DD +7.3%, ww -286, stops 0.53(0.08), b5 135%, w2l 3 | -812 $/wk, DD +7.3%, ww -286, stops 0.38(0.08), b5 45%, w2l 4 | n/a | n/a |
| D3 | all | D3T_b | fails recent gate | -5003 $/wk, DD +6.5%, ww -32, stops 11.03(10.35), b5 88%, w2l 2 | -2173 $/wk, DD +6.5%, ww -32, stops 13.54(10.99), b5 101%, w2l 2 | n/a | n/a |
| D3 | asia | D3T_b | fails recent gate | -3340 $/wk, DD +6.7%, ww -13308, stops 7.15(6.24), b5 89%, w2l 0 | -1843 $/wk, DD +6.7%, ww -13308, stops 7.76(6.35), b5 92%, w2l 1 | n/a | n/a |
| D3 | london | D3C_c | recent only (older not yet scored) | +504 $/wk, DD +4.0%, ww +2112, stops 3.20(2.74), b5 89%, w2l 0 | +904 $/wk, DD +4.0%, ww +2112, stops 4.79(2.89), b5 93%, w2l 0 | n/a | n/a |
| D3 | nyam | D3T_b | fails recent gate | -131 $/wk, DD +12.8%, ww +592, stops 1.14(1.29), b5 82%, w2l 1 | -194 $/wk, DD -13.7%, ww -2170, stops 2.02(1.67), b5 87%, w2l 2 | n/a | n/a |
| D3 | nypm | D3C_b | fails recent gate | -781 $/wk, DD +5.4%, ww +1073, stops 0.08(0.08), b5 16%, w2l 4 | -358 $/wk, DD +5.4%, ww +1073, stops 0.30(0.08), b5 79%, w2l 4 | n/a | n/a |
| D4 | all | D4II05_c | fails recent gate | -103 $/wk, DD +33.6%, ww +17543, stops 8.83(10.35), b5 78%, w2l 1 | -1200 $/wk, DD +33.6%, ww +17543, stops 9.43(10.99), b5 94%, w2l 1 | n/a | n/a |
| D4 | asia | D4I05_b | fails recent gate | -13211 $/wk, DD +59.2%, ww +11105, stops 1.90(6.24), b5 15%, w2l 3 | -13450 $/wk, DD +31.0%, ww +11105, stops 1.79(6.35), b5 24%, w2l 6 | n/a | n/a |
| D4 | london | D4I05_c | fails recent gate | -2111 $/wk, DD +57.9%, ww +15873, stops 0.46(2.74), b5 33%, w2l 3 | -966 $/wk, DD +53.3%, ww +15873, stops 1.03(2.89), b5 36%, w2l 4 | n/a | n/a |
| D4 | nyam | D4II05_c | recent only (older not yet scored) | +1150 $/wk, DD +33.8%, ww +3493, stops 1.29(1.29), b5 91%, w2l 2 | +449 $/wk, DD +28.6%, ww +3080, stops 1.48(1.67), b5 69%, w2l 3 | n/a | n/a |
| D4 | nypm | D4II05_b | fails recent gate | -523 $/wk, DD +34.9%, ww +822, stops 0.08(0.08), b5 68%, w2l 1 | -583 $/wk, DD +31.9%, ww +822, stops 0.08(0.08), b5 77%, w2l 2 | n/a | n/a |

## 4. Strength, plainly
- Cells passing the tolerant gate in L3M+L6M (scope all): 0 of 16 scored; of them also passing every older window: 0.
- Gain of the better forecast over (a) (scope all, L6M, both maxDD cut and mean better than (a)): (b) 3 of 5 families, (c) 3 of 5 families. Chance for a coin flip would be about half.

## 5. Placebo (forecast shifted 11/23/37 trading days) and family null (forecast permuted within month, seeds 1-3) beside the finalists
Finalists not chosen yet (needs L6M of the grid).

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
| D4II05 | a | event days | -3466 $/wk, DD +4.6%, ww +5921, stops 3.42(4.11), b5 63%, w2l 2 | n/a |
| D4II05 | a | non-event days | -9335 $/wk, DD -48.5%, ww -2723, stops 6.28(6.89), b5 77%, w2l 3 | n/a |
| D4II05 | a | high-impact days | -958 $/wk, DD +21.8%, ww +681, stops 0.95(1.26), b5 66%, w2l 2 | n/a |
| D4II05 | a | non-high days | -11843 $/wk, DD -61.2%, ww -5233, stops 8.75(9.74), b5 76%, w2l 3 | n/a |
| D4II05 | b | event days | -831 $/wk, DD +4.7%, ww +9294, stops 3.31(4.11), b5 79%, w2l 2 | n/a |
| D4II05 | b | non-event days | -8608 $/wk, DD +29.5%, ww -3404, stops 6.39(6.89), b5 62%, w2l 2 | n/a |
| D4II05 | b | high-impact days | -409 $/wk, DD +25.9%, ww +831, stops 0.91(1.26), b5 78%, w2l 1 | n/a |
| D4II05 | b | non-high days | -9029 $/wk, DD -12.9%, ww +1151, stops 8.79(9.74), b5 65%, w2l 3 | n/a |
| D4II05 | c | event days | +1591 $/wk, DD +51.6%, ww +13142, stops 3.46(4.11), b5 86%, w2l 0 | n/a |
| D4II05 | c | non-event days | -2790 $/wk, DD +34.2%, ww -2607, stops 5.97(6.89), b5 82%, w2l 2 | n/a |
| D4II05 | c | high-impact days | -549 $/wk, DD +26.0%, ww +831, stops 0.99(1.26), b5 83%, w2l 1 | n/a |
| D4II05 | c | non-high days | -651 $/wk, DD -0.7%, ww +2833, stops 8.45(9.74), b5 84%, w2l 2 | n/a |
| D4I05 | a | event days | -3484 $/wk, DD -30.4%, ww +544, stops 1.94(4.11), b5 28%, w2l 2 | n/a |
| D4I05 | a | non-event days | -14959 $/wk, DD -16.9%, ww -6606, stops 3.31(6.89), b5 31%, w2l 4 | n/a |
| D4I05 | a | high-impact days | -431 $/wk, DD +63.2%, ww +657, stops 0.42(1.26), b5 52%, w2l 1 | n/a |
| D4I05 | a | non-high days | -18012 $/wk, DD -50.5%, ww +4859, stops 4.83(9.74), b5 23%, w2l 7 | n/a |
| D4I05 | b | event days | -1511 $/wk, DD +56.7%, ww +13852, stops 1.79(4.11), b5 37%, w2l 1 | n/a |
| D4I05 | b | non-event days | -15410 $/wk, DD +9.9%, ww +1389, stops 2.97(6.89), b5 18%, w2l 6 | n/a |
| D4I05 | b | high-impact days | -308 $/wk, DD +61.1%, ww +4394, stops 0.53(1.26), b5 48%, w2l 1 | n/a |
| D4I05 | b | non-high days | -16614 $/wk, DD -30.9%, ww +4103, stops 4.22(9.74), b5 18%, w2l 7 | n/a |
| D4I05 | c | event days | -2951 $/wk, DD +15.2%, ww +3410, stops 2.21(4.11), b5 40%, w2l 1 | n/a |
| D4I05 | c | non-event days | -13224 $/wk, DD +25.0%, ww -6816, stops 2.85(6.89), b5 29%, w2l 4 | n/a |
| D4I05 | c | high-impact days | -1772 $/wk, DD +21.0%, ww +831, stops 0.65(1.26), b5 56%, w2l 1 | n/a |
| D4I05 | c | non-high days | -14403 $/wk, DD +0.5%, ww -4102, stops 4.41(9.74), b5 26%, w2l 6 | n/a |
| D3T | a | event days | -849 $/wk, DD -29.1%, ww -1115, stops 5.36(4.11), b5 102%, w2l 2 | n/a |
| D3T | a | non-event days | -2864 $/wk, DD -48.0%, ww -13208, stops 9.02(6.89), b5 94%, w2l 0 | n/a |
| D3T | a | high-impact days | -45 $/wk, DD -9.6%, ww -4041, stops 1.75(1.26), b5 105%, w2l 1 | n/a |
| D3T | a | non-high days | -3669 $/wk, DD -24.6%, ww -22854, stops 12.63(9.74), b5 97%, w2l 1 | n/a |
| D3T | b | event days | -220 $/wk, DD -29.1%, ww +643, stops 4.83(4.11), b5 96%, w2l 0 | n/a |
| D3T | b | non-event days | -1953 $/wk, DD -31.2%, ww -10953, stops 8.71(6.89), b5 98%, w2l 0 | n/a |
| D3T | b | high-impact days | +437 $/wk, DD +13.6%, ww -374, stops 1.45(1.26), b5 109%, w2l 2 | n/a |
| D3T | b | non-high days | -2610 $/wk, DD -7.7%, ww -5318, stops 12.10(9.74), b5 101%, w2l 2 | n/a |
| D3T | c | event days | -1182 $/wk, DD -39.0%, ww +2444, stops 5.21(4.11), b5 97%, w2l 1 | n/a |
| D3T | c | non-event days | -1518 $/wk, DD -30.3%, ww -7837, stops 8.56(6.89), b5 101%, w2l 0 | n/a |
| D3T | c | high-impact days | +37 $/wk, DD -9.3%, ww -374, stops 1.64(1.26), b5 105%, w2l 1 | n/a |
| D3T | c | non-high days | -2736 $/wk, DD -43.5%, ww -17483, stops 12.14(9.74), b5 104%, w2l 1 | n/a |
| D3C | a | event days | -878 $/wk, DD +8.5%, ww +1454, stops 6.20(4.11), b5 97%, w2l 1 | n/a |
| D3C | a | non-event days | -5176 $/wk, DD -49.0%, ww -11624, stops 11.18(6.89), b5 80%, w2l 1 | n/a |
| D3C | a | high-impact days | +89 $/wk, DD -16.1%, ww -4433, stops 2.05(1.26), b5 105%, w2l 1 | n/a |
| D3C | a | non-high days | -6143 $/wk, DD -47.3%, ww -26417, stops 15.33(9.74), b5 81%, w2l 2 | n/a |
| D3C | b | event days | -2550 $/wk, DD -118.7%, ww -465, stops 5.67(4.11), b5 99%, w2l 1 | n/a |
| D3C | b | non-event days | -2877 $/wk, DD -30.3%, ww -11938, stops 10.88(6.89), b5 96%, w2l 1 | n/a |
| D3C | b | high-impact days | +124 $/wk, DD -2.4%, ww -2188, stops 1.94(1.26), b5 111%, w2l 2 | n/a |
| D3C | b | non-high days | -5551 $/wk, DD -52.7%, ww -18949, stops 14.61(9.74), b5 97%, w2l 3 | n/a |
| D3C | c | event days | -2573 $/wk, DD -88.3%, ww -80, stops 6.20(4.11), b5 96%, w2l 1 | n/a |
| D3C | c | non-event days | -3578 $/wk, DD -64.4%, ww -24759, stops 11.30(6.89), b5 99%, w2l 2 | n/a |
| D3C | c | high-impact days | -347 $/wk, DD -9.6%, ww -2241, stops 2.09(1.26), b5 106%, w2l 2 | n/a |
| D3C | c | non-high days | -5804 $/wk, DD -61.9%, ww -21656, stops 15.41(9.74), b5 101%, w2l 2 | n/a |
| D2F | a | event days | -1203 $/wk, DD -15.9%, ww +10313, stops 3.88(4.11), b5 74%, w2l 2 | n/a |
| D2F | a | non-event days | -4257 $/wk, DD +6.9%, ww -13848, stops 6.24(6.89), b5 79%, w2l 0 | n/a |
| D2F | a | high-impact days | +329 $/wk, DD +32.6%, ww +2724, stops 1.33(1.26), b5 76%, w2l 3 | n/a |
| D2F | a | non-high days | -5789 $/wk, DD -85.9%, ww -27948, stops 8.79(9.74), b5 74%, w2l 0 | n/a |
| D2F | b | event days | -623 $/wk, DD -19.0%, ww +8556, stops 5.29(4.11), b5 83%, w2l 4 | n/a |
| D2F | b | non-event days | -4973 $/wk, DD -12.9%, ww -14819, stops 7.46(6.89), b5 87%, w2l 0 | n/a |
| D2F | b | high-impact days | +1612 $/wk, DD +38.6%, ww +1368, stops 1.33(1.26), b5 92%, w2l 2 | n/a |
| D2F | b | non-high days | -7208 $/wk, DD -70.2%, ww -23115, stops 11.41(9.74), b5 79%, w2l 3 | n/a |
| D2F | c | event days | -313 $/wk, DD +22.2%, ww +11891, stops 4.79(4.11), b5 80%, w2l 3 | n/a |
| D2F | c | non-event days | -2685 $/wk, DD +27.6%, ww -5180, stops 6.47(6.89), b5 85%, w2l 0 | n/a |
| D2F | c | high-impact days | +2148 $/wk, DD +43.7%, ww +5115, stops 1.33(1.26), b5 97%, w2l 2 | n/a |
| D2F | c | non-high days | -5147 $/wk, DD -28.9%, ww -7422, stops 9.93(9.74), b5 75%, w2l 4 | n/a |
| D4II075 | a | event days | -459 $/wk, DD +12.7%, ww -1473, stops 3.65(4.11), b5 93%, w2l 1 | n/a |
| D4II075 | a | non-event days | -5079 $/wk, DD -1.7%, ww -4633, stops 6.58(6.89), b5 93%, w2l 2 | n/a |
| D4II075 | a | high-impact days | -410 $/wk, DD +10.0%, ww +831, stops 1.10(1.26), b5 88%, w2l 1 | n/a |
| D4II075 | a | non-high days | -5127 $/wk, DD -23.1%, ww -17856, stops 9.13(9.74), b5 92%, w2l 3 | n/a |
| D4II075 | b | event days | n/a | n/a |
| D4II075 | b | non-event days | n/a | n/a |
| D4II075 | b | high-impact days | n/a | n/a |
| D4II075 | b | non-high days | n/a | n/a |
| D4II075 | c | event days | n/a | n/a |
| D4II075 | c | non-event days | n/a | n/a |
| D4II075 | c | high-impact days | n/a | n/a |
| D4II075 | c | non-high days | n/a | n/a |