# DS3_RANGEUSE - T-RANGEUSE: the walk-forward range forecast on D7 dials (W-RU). Rebuilt 2026-11-14T01:58Z by code/th_rangeuse/ru_loop.sh (every 3 h). Research only, NO PASS claim.
**VERDICT (plain): No result yet: 44 of 98 cells have the full L3M (3 months) scored in the exact engine, none has L6M yet; ranking needs L3M+L6M, placebo and permuted null. Running: ru_driver (8 chains, tag RU) and ru_loop (3-hourly rebuild).**

Prereg: autopilot/RANGEUSE_PREREG.md (sha in DECISIONS.md, logged before scoring). Order: DIRECTIVE_UW_3PART_20261113.md PART 2. Base JN05W2 exact engine, all layers ON. Identity: TL3_RU_ID 202610 (hook path active at neutral multipliers): 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL.
Months scored (cells with all months of the window / 98 cells): L3M 44, L6M 0, HOLD 0, PREUW 0. Driver: 221 jobs wanted, 8 chains running, 1794621454.

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
| all | a | -7217 $/wk, DD -43.9%, ww -20213, stops 11.64(10.35), b5 73%, w2l 1 | n/a | n/a | n/a |
| all | b | -8028 $/wk, DD -32.6%, ww -15525, stops 17.12(10.35), b5 84%, w2l 2 | n/a | n/a | n/a |
| all | c | -6967 $/wk, DD -9.6%, ww -3770, stops 13.77(10.35), b5 79%, w2l 3 | n/a | n/a | n/a |
| all | **b-a** | -811 $/wk, DD +11.3 pts, ww +4688 | n/a | n/a | n/a |
| all | **c-a** | +250 $/wk, DD +34.3 pts, ww +16443 | n/a | n/a | n/a |
| asia | a | -8158 $/wk, DD -57.6%, ww -29397, stops 6.39(6.24), b5 64%, w2l 0 | n/a | n/a | n/a |
| asia | b | -3571 $/wk, DD -14.4%, ww -20299, stops 8.52(6.24), b5 74%, w2l 1 | n/a | n/a | n/a |
| asia | c | -5645 $/wk, DD -25.0%, ww -15742, stops 6.85(6.24), b5 67%, w2l 1 | n/a | n/a | n/a |
| asia | **b-a** | +4587 $/wk, DD +43.2 pts, ww +9098 | n/a | n/a | n/a |
| asia | **c-a** | +2513 $/wk, DD +32.6 pts, ww +13655 | n/a | n/a | n/a |
| london | a | +518 $/wk, DD -7.5%, ww +1021, stops 2.74(2.74), b5 96%, w2l 0 | n/a | n/a | n/a |
| london | b | -2903 $/wk, DD +26.4%, ww +4826, stops 5.40(2.74), b5 66%, w2l 2 | n/a | n/a | n/a |
| london | c | -655 $/wk, DD +9.2%, ww -4653, stops 3.50(2.74), b5 88%, w2l 1 | n/a | n/a | n/a |
| london | **b-a** | -3422 $/wk, DD +33.9 pts, ww +3805 | n/a | n/a | n/a |
| london | **c-a** | -1173 $/wk, DD +16.7 pts, ww -5674 | n/a | n/a | n/a |
| nyam | a | +452 $/wk, DD +17.9%, ww -2881, stops 1.98(1.29), b5 92%, w2l 0 | n/a | n/a | n/a |
| nyam | b | -389 $/wk, DD -14.2%, ww -2625, stops 2.21(1.29), b5 61%, w2l 1 | n/a | n/a | n/a |
| nyam | c | -856 $/wk, DD -49.7%, ww -3697, stops 2.43(1.29), b5 63%, w2l 3 | n/a | n/a | n/a |
| nyam | **b-a** | -841 $/wk, DD -32.1 pts, ww +256 | n/a | n/a | n/a |
| nyam | **c-a** | -1308 $/wk, DD -67.6 pts, ww -816 | n/a | n/a | n/a |
| nypm | a | -30 $/wk, DD +7.3%, ww -286, stops 0.53(0.08), b5 135%, w2l 3 | n/a | n/a | n/a |
| nypm | b | -1164 $/wk, DD -29.4%, ww -412, stops 0.99(0.08), b5 36%, w2l 3 | n/a | n/a | n/a |
| nypm | c | +189 $/wk, DD +31.4%, ww +1255, stops 0.99(0.08), b5 122%, w2l 3 | n/a | n/a | n/a |
| nypm | **b-a** | -1135 $/wk, DD -36.7 pts, ww -125 | n/a | n/a | n/a |
| nypm | **c-a** | +218 $/wk, DD +24.1 pts, ww +1541 | n/a | n/a | n/a |

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
| all | a | -7420 $/wk, DD -10.2%, ww -2364, stops 12.40(10.35), b5 73%, w2l 1 | n/a | n/a | n/a |
| all | b | -6971 $/wk, DD -25.9%, ww -14627, stops 11.95(10.35), b5 89%, w2l 1 | n/a | n/a | n/a |
| all | c | -5225 $/wk, DD -5.9%, ww -1261, stops 12.71(10.35), b5 90%, w2l 1 | n/a | n/a | n/a |
| all | **b-a** | +448 $/wk, DD -15.7 pts, ww -12263 | n/a | n/a | n/a |
| all | **c-a** | +2195 $/wk, DD +4.3 pts, ww +1103 | n/a | n/a | n/a |
| asia | a | -5194 $/wk, DD -18.4%, ww -18623, stops 7.76(6.24), b5 84%, w2l 1 | n/a | n/a | n/a |
| asia | b | -4116 $/wk, DD -5.3%, ww -18193, stops 7.99(6.24), b5 91%, w2l 1 | n/a | n/a | n/a |
| asia | c | -4006 $/wk, DD -8.3%, ww -16882, stops 8.29(6.24), b5 89%, w2l 1 | n/a | n/a | n/a |
| asia | **b-a** | +1079 $/wk, DD +13.1 pts, ww +430 | n/a | n/a | n/a |
| asia | **c-a** | +1189 $/wk, DD +10.1 pts, ww +1742 | n/a | n/a | n/a |
| london | a | -326 $/wk, DD -3.0%, ww +2741, stops 3.42(2.74), b5 89%, w2l 0 | n/a | n/a | n/a |
| london | b | -1751 $/wk, DD -14.5%, ww -366, stops 3.04(2.74), b5 84%, w2l 0 | n/a | n/a | n/a |
| london | c | +504 $/wk, DD +4.0%, ww +2112, stops 3.20(2.74), b5 89%, w2l 0 | n/a | n/a | n/a |
| london | **b-a** | -1424 $/wk, DD -11.4 pts, ww -3107 | n/a | n/a | n/a |
| london | **c-a** | +830 $/wk, DD +7.0 pts, ww -629 | n/a | n/a | n/a |
| nyam | a | -822 $/wk, DD +16.2%, ww +514, stops 1.14(1.29), b5 49%, w2l 2 | n/a | n/a | n/a |
| nyam | b | -323 $/wk, DD +17.6%, ww -54, stops 0.84(1.29), b5 66%, w2l 2 | n/a | n/a | n/a |
| nyam | c | -608 $/wk, DD -0.1%, ww -4307, stops 0.99(1.29), b5 78%, w2l 1 | n/a | n/a | n/a |
| nyam | **b-a** | +499 $/wk, DD +1.4 pts, ww -568 | n/a | n/a | n/a |
| nyam | **c-a** | +215 $/wk, DD -16.3 pts, ww -4821 | n/a | n/a | n/a |
| nypm | a | -1077 $/wk, DD -16.0%, ww -145, stops 0.08(0.08), b5 23%, w2l 3 | n/a | n/a | n/a |
| nypm | b | -781 $/wk, DD +5.4%, ww +1073, stops 0.08(0.08), b5 16%, w2l 4 | n/a | n/a | n/a |
| nypm | c | -1116 $/wk, DD -47.0%, ww +757, stops 0.23(0.08), b5 10%, w2l 4 | n/a | n/a | n/a |
| nypm | **b-a** | +295 $/wk, DD +21.4 pts, ww +1218 | n/a | n/a | n/a |
| nypm | **c-a** | -39 $/wk, DD -31.0 pts, ww +902 | n/a | n/a | n/a |

**D3T** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -4471 $/wk, DD -2.1%, ww -722, stops 11.57(10.35), b5 90%, w2l 1 | n/a | n/a | n/a |
| all | b | -5003 $/wk, DD +6.5%, ww -32, stops 11.03(10.35), b5 88%, w2l 2 | n/a | n/a | n/a |
| all | c | -3585 $/wk, DD -17.3%, ww -11955, stops 11.72(10.35), b5 91%, w2l 0 | n/a | n/a | n/a |
| all | **b-a** | -532 $/wk, DD +8.5 pts, ww +690 | n/a | n/a | n/a |
| all | **c-a** | +885 $/wk, DD -15.2 pts, ww -11233 | n/a | n/a | n/a |
| asia | a | -2429 $/wk, DD -8.9%, ww -14670, stops 7.08(6.24), b5 99%, w2l 1 | n/a | n/a | n/a |
| asia | b | -3340 $/wk, DD +6.7%, ww -13308, stops 7.15(6.24), b5 89%, w2l 0 | n/a | n/a | n/a |
| asia | c | -3140 $/wk, DD +0.9%, ww -8722, stops 7.15(6.24), b5 96%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | -911 $/wk, DD +15.6 pts, ww +1363 | n/a | n/a | n/a |
| asia | **c-a** | -711 $/wk, DD +9.8 pts, ww +5948 | n/a | n/a | n/a |
| london | a | -690 $/wk, DD -15.8%, ww +1175, stops 3.20(2.74), b5 99%, w2l 0 | n/a | n/a | n/a |
| london | b | -582 $/wk, DD +5.3%, ww +943, stops 2.66(2.74), b5 87%, w2l 0 | n/a | n/a | n/a |
| london | c | -251 $/wk, DD -23.1%, ww +0, stops 3.20(2.74), b5 105%, w2l 0 | n/a | n/a | n/a |
| london | **b-a** | +108 $/wk, DD +21.1 pts, ww -231 | n/a | n/a | n/a |
| london | **c-a** | +439 $/wk, DD -7.3 pts, ww -1175 | n/a | n/a | n/a |
| nyam | a | -249 $/wk, DD +22.4%, ww +817, stops 1.22(1.29), b5 71%, w2l 1 | n/a | n/a | n/a |
| nyam | b | -131 $/wk, DD +12.8%, ww +592, stops 1.14(1.29), b5 82%, w2l 1 | n/a | n/a | n/a |
| nyam | c | +489 $/wk, DD +0.3%, ww +592, stops 1.22(1.29), b5 106%, w2l 1 | n/a | n/a | n/a |
| nyam | **b-a** | +118 $/wk, DD -9.6 pts, ww -225 | n/a | n/a | n/a |
| nyam | **c-a** | +739 $/wk, DD -22.0 pts, ww -225 | n/a | n/a | n/a |
| nypm | a | -1102 $/wk, DD -26.6%, ww -373, stops 0.08(0.08), b5 35%, w2l 3 | n/a | n/a | n/a |
| nypm | b | -950 $/wk, DD -18.2%, ww +168, stops 0.08(0.08), b5 32%, w2l 4 | n/a | n/a | n/a |
| nypm | c | -684 $/wk, DD -22.2%, ww +308, stops 0.15(0.08), b5 63%, w2l 3 | n/a | n/a | n/a |
| nypm | **b-a** | +153 $/wk, DD +8.4 pts, ww +540 | n/a | n/a | n/a |
| nypm | **c-a** | +419 $/wk, DD +4.5 pts, ww +680 | n/a | n/a | n/a |

### Dial 4 range used up (I skip / II take profit early / III shrink target; k in name 05=0.5 075 1 125)

**D4I05** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -17155 $/wk, DD -37.7%, ww +6545, stops 4.49(10.35), b5 33%, w2l 5 | n/a | n/a | n/a |
| all | b | -18999 $/wk, DD +23.0%, ww +15161, stops 3.80(10.35), b5 5%, w2l 3 | n/a | n/a | n/a |
| all | c | -16297 $/wk, DD +17.1%, ww +19115, stops 4.34(10.35), b5 34%, w2l 5 | n/a | n/a | n/a |
| all | **b-a** | -1844 $/wk, DD +60.7 pts, ww +8616 | n/a | n/a | n/a |
| all | **c-a** | +858 $/wk, DD +54.8 pts, ww +12570 | n/a | n/a | n/a |
| asia | a | -10750 $/wk, DD +8.8%, ww +4518, stops 2.28(6.24), b5 44%, w2l 3 | n/a | n/a | n/a |
| asia | b | -13211 $/wk, DD +59.2%, ww +11105, stops 1.90(6.24), b5 15%, w2l 3 | n/a | n/a | n/a |
| asia | c | -13431 $/wk, DD +12.5%, ww +10439, stops 2.74(6.24), b5 29%, w2l 2 | n/a | n/a | n/a |
| asia | **b-a** | -2461 $/wk, DD +50.4 pts, ww +6587 | n/a | n/a | n/a |
| asia | **c-a** | -2681 $/wk, DD +3.6 pts, ww +5922 | n/a | n/a | n/a |
| london | a | -4272 $/wk, DD +17.8%, ww -1546, stops 0.99(2.74), b5 42%, w2l 2 | n/a | n/a | n/a |
| london | b | -3118 $/wk, DD +36.7%, ww +11561, stops 0.61(2.74), b5 25%, w2l 1 | n/a | n/a | n/a |
| london | c | -2111 $/wk, DD +57.9%, ww +15873, stops 0.46(2.74), b5 33%, w2l 3 | n/a | n/a | n/a |
| london | **b-a** | +1154 $/wk, DD +18.9 pts, ww +13107 | n/a | n/a | n/a |
| london | **c-a** | +2162 $/wk, DD +40.1 pts, ww +17419 | n/a | n/a | n/a |
| nyam | a | -482 $/wk, DD -10.2%, ww -1334, stops 1.07(1.29), b5 43%, w2l 4 | n/a | n/a | n/a |
| nyam | b | -682 $/wk, DD +17.7%, ww -608, stops 1.07(1.29), b5 47%, w2l 5 | n/a | n/a | n/a |
| nyam | c | +29 $/wk, DD +21.9%, ww +4131, stops 1.07(1.29), b5 32%, w2l 5 | n/a | n/a | n/a |
| nyam | **b-a** | -200 $/wk, DD +27.9 pts, ww +726 | n/a | n/a | n/a |
| nyam | **c-a** | +510 $/wk, DD +32.1 pts, ww +5465 | n/a | n/a | n/a |
| nypm | a | -1651 $/wk, DD -236.7%, ww -3463, stops 0.15(0.08), b5 -10%, w2l 3 | n/a | n/a | n/a |
| nypm | b | -1989 $/wk, DD -268.8%, ww -4062, stops 0.23(0.08), b5 -52%, w2l 5 | n/a | n/a | n/a |
| nypm | c | -784 $/wk, DD -57.6%, ww +215, stops 0.08(0.08), b5 25%, w2l 4 | n/a | n/a | n/a |
| nypm | **b-a** | -338 $/wk, DD -32.0 pts, ww -599 | n/a | n/a | n/a |
| nypm | **c-a** | +867 $/wk, DD +179.1 pts, ww +3678 | n/a | n/a | n/a |

**D4II05** (scope all unless noted; no-rule reference = 0 / 0 / 0)

| scope | fc | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|
| all | a | -7856 $/wk, DD -8.6%, ww -1378, stops 9.13(10.35), b5 57%, w2l 1 | n/a | n/a | n/a |
| all | b | -10753 $/wk, DD -4.3%, ww -107, stops 8.83(10.35), b5 42%, w2l 2 | n/a | n/a | n/a |
| all | c | -103 $/wk, DD +33.6%, ww +17543, stops 8.83(10.35), b5 78%, w2l 1 | n/a | n/a | n/a |
| all | **b-a** | -2898 $/wk, DD +4.3 pts, ww +1271 | n/a | n/a | n/a |
| all | **c-a** | +7753 $/wk, DD +42.2 pts, ww +18921 | n/a | n/a | n/a |
| asia | a | -5301 $/wk, DD -11.3%, ww -5486, stops 5.93(6.24), b5 103%, w2l 1 | n/a | n/a | n/a |
| asia | b | -5747 $/wk, DD -8.6%, ww -4149, stops 6.01(6.24), b5 81%, w2l 2 | n/a | n/a | n/a |
| asia | c | +2444 $/wk, DD +26.5%, ww +8989, stops 5.55(6.24), b5 109%, w2l 1 | n/a | n/a | n/a |
| asia | **b-a** | -447 $/wk, DD +2.8 pts, ww +1337 | n/a | n/a | n/a |
| asia | **c-a** | +7745 $/wk, DD +37.8 pts, ww +14475 | n/a | n/a | n/a |
| london | a | -926 $/wk, DD +5.8%, ww -8782, stops 1.98(2.74), b5 73%, w2l 0 | n/a | n/a | n/a |
| london | b | -3018 $/wk, DD +31.9%, ww -2814, stops 1.75(2.74), b5 45%, w2l 0 | n/a | n/a | n/a |
| london | c | -3139 $/wk, DD +25.3%, ww -400, stops 1.90(2.74), b5 62%, w2l 2 | n/a | n/a | n/a |
| london | **b-a** | -2092 $/wk, DD +26.1 pts, ww +5968 | n/a | n/a | n/a |
| london | **c-a** | -2213 $/wk, DD +19.5 pts, ww +8382 | n/a | n/a | n/a |
| nyam | a | -627 $/wk, DD -2.6%, ww -2863, stops 1.14(1.29), b5 85%, w2l 3 | n/a | n/a | n/a |
| nyam | b | -1465 $/wk, DD -28.2%, ww +2509, stops 0.99(1.29), b5 66%, w2l 3 | n/a | n/a | n/a |
| nyam | c | +1150 $/wk, DD +33.8%, ww +3493, stops 1.29(1.29), b5 91%, w2l 2 | n/a | n/a | n/a |
| nyam | **b-a** | -838 $/wk, DD -25.6 pts, ww +5373 | n/a | n/a | n/a |
| nyam | **c-a** | +1777 $/wk, DD +36.4 pts, ww +6356 | n/a | n/a | n/a |
| nypm | a | -1002 $/wk, DD -86.6%, ww -275, stops 0.08(0.08), b5 29%, w2l 4 | n/a | n/a | n/a |
| nypm | b | -523 $/wk, DD +34.9%, ww +822, stops 0.08(0.08), b5 68%, w2l 1 | n/a | n/a | n/a |
| nypm | c | -558 $/wk, DD -25.9%, ww -183, stops 0.08(0.08), b5 15%, w2l 3 | n/a | n/a | n/a |
| nypm | **b-a** | +479 $/wk, DD +121.5 pts, ww +1097 | n/a | n/a | n/a |
| nypm | **c-a** | +444 $/wk, DD +60.7 pts, ww +92 | n/a | n/a | n/a |

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
| all | a | -2612 $/wk, DD -16.0%, ww -5553, stops 9.97(10.35), b5 78%, w2l 0 | n/a | n/a | n/a |
| all | b | -5257 $/wk, DD +9.9%, ww +5619, stops 9.59(10.35), b5 65%, w2l 1 | n/a | n/a | n/a |
| all | c | -2076 $/wk, DD +30.7%, ww +7445, stops 9.66(10.35), b5 85%, w2l 1 | n/a | n/a | n/a |
| all | **b-a** | -2645 $/wk, DD +25.9 pts, ww +11172 | n/a | n/a | n/a |
| all | **c-a** | +535 $/wk, DD +46.6 pts, ww +12998 | n/a | n/a | n/a |
| asia | a | -512 $/wk, DD -11.5%, ww -5570, stops 6.32(6.24), b5 100%, w2l 1 | n/a | n/a | n/a |
| asia | b | -1319 $/wk, DD +8.0%, ww -2121, stops 6.09(6.24), b5 104%, w2l 1 | n/a | n/a | n/a |
| asia | c | +2288 $/wk, DD +24.3%, ww -8025, stops 5.86(6.24), b5 111%, w2l 1 | n/a | n/a | n/a |
| asia | **b-a** | -807 $/wk, DD +19.5 pts, ww +3449 | n/a | n/a | n/a |
| asia | **c-a** | +2800 $/wk, DD +35.8 pts, ww -2455 | n/a | n/a | n/a |
| london | a | -2337 $/wk, DD -24.8%, ww -10688, stops 2.43(2.74), b5 78%, w2l 0 | n/a | n/a | n/a |
| london | b | -2998 $/wk, DD +32.5%, ww -6174, stops 2.21(2.74), b5 54%, w2l 1 | n/a | n/a | n/a |
| london | c | -4751 $/wk, DD -10.1%, ww -5106, stops 2.59(2.74), b5 69%, w2l 2 | n/a | n/a | n/a |
| london | **b-a** | -661 $/wk, DD +57.3 pts, ww +4514 | n/a | n/a | n/a |
| london | **c-a** | -2415 $/wk, DD +14.7 pts, ww +5582 | n/a | n/a | n/a |
| nyam | a | +661 $/wk, DD -9.6%, ww +826, stops 1.14(1.29), b5 117%, w2l 3 | n/a | n/a | n/a |
| nyam | b | +10 $/wk, DD +23.6%, ww -1872, stops 1.22(1.29), b5 91%, w2l 1 | n/a | n/a | n/a |
| nyam | c | +594 $/wk, DD +33.2%, ww +173, stops 1.14(1.29), b5 73%, w2l 1 | n/a | n/a | n/a |
| nyam | **b-a** | -651 $/wk, DD +33.2 pts, ww -2698 | n/a | n/a | n/a |
| nyam | **c-a** | -67 $/wk, DD +42.8 pts, ww -653 | n/a | n/a | n/a |
| nypm | a | -424 $/wk, DD -19.9%, ww +232, stops 0.08(0.08), b5 99%, w2l 2 | n/a | n/a | n/a |
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
| all | **b-a** | +1884 $/wk, DD +28.2 pts, ww +12850 | n/a | n/a | n/a |
| asia | a | -1857 $/wk, DD -9.9%, ww -4797, stops 6.47(6.24), b5 103%, w2l 0 | n/a | n/a | n/a |
| asia | b | +1780 $/wk, DD +8.2%, ww -1241, stops 6.39(6.24), b5 106%, w2l 0 | n/a | n/a | n/a |
| asia | **b-a** | +3637 $/wk, DD +18.1 pts, ww +3556 | n/a | n/a | n/a |
| london | a | -2334 $/wk, DD -9.5%, ww -6221, stops 2.59(2.74), b5 73%, w2l 0 | n/a | n/a | n/a |
| london | b | -2317 $/wk, DD +35.8%, ww -6158, stops 2.28(2.74), b5 64%, w2l 1 | n/a | n/a | n/a |
| london | **b-a** | +17 $/wk, DD +45.2 pts, ww +63 | n/a | n/a | n/a |
| nyam | a | +525 $/wk, DD +11.3%, ww -1454, stops 1.14(1.29), b5 115%, w2l 2 | n/a | n/a | n/a |
| nyam | b | -514 $/wk, DD -13.6%, ww +130, stops 1.45(1.29), b5 96%, w2l 2 | n/a | n/a | n/a |
| nyam | **b-a** | -1039 $/wk, DD -24.9 pts, ww +1584 | n/a | n/a | n/a |
| nypm | a | -271 $/wk, DD -13.5%, ww +526, stops 0.08(0.08), b5 92%, w2l 1 | n/a | n/a | n/a |
| nypm | b | -1003 $/wk, DD -42.2%, ww +97, stops 0.08(0.08), b5 24%, w2l 4 | n/a | n/a | n/a |
| nypm | **b-a** | -732 $/wk, DD -28.7 pts, ww -429 | n/a | n/a | n/a |

### Dial 5 replace atr_rel in live layers (REG half-size, skip) by the forecast ratio (A-cells = live atr_rel reference)

### Dial 6 entry distance (split-add dip MINDIP)

### Dial 7 lock levels (BookLock peak 2R threshold)

## 3. Best setting per dial and per session (drawdown first: L6M + HOLD maxDD cut, tolerant gate; status says which windows it holds in)
| dial | scope | best cell | status | L3M | L6M | HOLD | PREUW |
|---|---|---|---|---|---|---|---|

## 4. Strength, plainly
No data yet.

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
W-CAL flags or scored cells not available yet.