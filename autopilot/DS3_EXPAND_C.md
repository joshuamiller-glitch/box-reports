# DS3_EXPAND_C - T-EXPAND family C: rules that belong to one session (W-EC). Rebuilt 2026-11-16T12:34Z by code/th_expand_c/ec_page.py. Research only, NO PASS claim.

**VERDICT (plain): 408 cell-months done over 59 cells; 34 cells pass the tolerant gate in L3M, 0 pass the STRICT gate in every present window; 0 pass the TOLERANT lead gate (recent clearly positive and beating placebos, older DD <= 10% deeper, mean >= -5%). Strict leads: none yet. Tolerant leads: none yet. FIRST PASS, no PASS claim.**

Prereg autopilot/EXPAND_C_PREREG.md (sha in DECISIONS.md). Base JN05W2 exact engine, all layers ON. Identity: TL3_EC_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL | TL3_EC_ID0 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL | TL3_EC_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL | TL3_EC_ID0 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL | TL3_EC_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL | TL3_EC_ID0 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL

Forecast windows: the W-R2 files (HAR, HAR+CME) start 2023-10-16, so X' months 2023-04..2023-10-15 are inactive (= JN05W2) for range-used-up cells. Pre (08:30-09:30) has no D7 entries, so pre cells are vacuous and not run. Last 90 minutes (14:30-16:00): D7 only enters until ~15:00 (K7).
LOT BASIS (one line): all numbers are BASE (box) lots, live = x1.75; raw engine net_fee charges $1.18 per contract round turn with the engine fills, not FEES.md $4.84; "fee4.84" = d mean/wk repriced at $4.84 RT per contract on the change in contracts per week (page code only, no rerun).
Row format: delta vs JN05W2 in the rule's own session scope: d mean, max-DD cut % (positive = smaller; /x = with 2026-W44 removed), d worst week, full stops/wk cell(ref), best-5 weeks kept, winning weeks turned losing, X = fails tolerant gate.

## Stage counts and nonsense rate (placebo = forecast shifted 11/23/37 days)

| window | real cells done | pass strict gate | pass tolerant | placebo cells done | placebo pass strict gate | random-skip controls done | random-skip pass strict gate |
|---|---|---|---|---|---|---|---|
| L3M | 19 | 12 | 9 | 24 | 21 | 16 | 1 |
| L6M | 11 | 4 | 0 | 23 | 6 | 14 | 3 |
| HOLD | 4 | 3 | 3 | 0 | 0 | 0 | 0 |
| GAP | 3 | 3 | 3 | 0 | 0 | 0 | 0 |
| PRE | 1 | 1 | 1 | 0 | 0 | 0 | 0 |
| X' | 1 | 1 | 1 | 0 | 0 | 0 | 0 |

PATH EFFECT = FREED-BOOK REPLACEMENT (generic, autopilot/PATH_EFFECT_RULE.md): every skip-type cell that passes L3M is read against an engine random skip at the same keep share (cell trades / JN05W2 trades in the scope over L3M, 2 seeds, hook rs); a skip cell is only called better than the base if it also beats that control on DD and mean. Headline rows are BASE lots; live = x1.75 (P7 cap 14,700 live = 8,400 base). Closest to live: nothing in family C is near a live change yet; the nearest candidates are the nyam / nypm HAR skip cells (L3M pass, L6M fail) and the l90 cells, which barely act.

## Range-used-up (1)

**asia**

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL | lead |
|---|---|---|---|---|---|---|---|---|
| RU_asia_hS1 | -3645 $/wk (fee4.84 -3442), DD +46%/+0, ww +434, st 4.26(6.24), b5 56%, w2l 1 X |  |  |  |  |  |  |  |
| RU_asia_hS125 | -5016 $/wk (fee4.84 -4840), DD +43%/+0, ww +434, st 4.49(6.24), b5 53%, w2l 2 X |  |  |  |  |  |  |  |
| RU_asia_vS1 | -6862 $/wk (fee4.84 -6657), DD +27%/-34, ww +434, st 4.18(6.24), b5 38%, w2l 3 X |  |  |  |  |  |  |  |
| RU_asia_hS075 | -6875 $/wk (fee4.84 -6617), DD +36%/-18, ww +9318, st 3.73(6.24), b5 54%, w2l 2 X |  |  |  |  |  |  |  |
| RU_asia_hS05 | -9604 $/wk (fee4.84 -9234), DD +18%/-51, ww +8197, st 2.13(6.24), b5 43%, w2l 1 X |  |  |  |  |  |  |  |

**london**

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL | lead |
|---|---|---|---|---|---|---|---|---|
| RU_london_hS125 | +354 $/wk (fee4.84 +427), DD +31%/+31, ww +11322, st 2.05(2.74), b5 90%, w2l 0 | -33 $/wk (fee4.84 +30), DD +31%/+31, ww +11322, st 2.24(2.89), b5 87%, w2l 0 | -725 $/wk (fee4.84 -659), DD +29%/+29, ww +4364, st 2.09(2.61), b5 88%, w2l 4 X |  |  |  |  |  |
| &nbsp;&nbsp;engine random skip L3M (same keep share, seeds) | DD +13/+23, mean -265/-489 | | | | | | | |
| &nbsp;&nbsp;placebo L3M (pl11/23/37) | DD +20/+28/+21, mean +1717/+1831/+2180 | | | | | | | |
| &nbsp;&nbsp;engine random skip L6M (same keep share, seeds) | DD +13/+23, mean -133/-1051 | | | | | | | |
| &nbsp;&nbsp;placebo L6M (pl11/23/37) | DD +20/+28/+21, mean +1482/+1165/+1944 | | | | | | | |
| RU_london_hS1 | -329 $/wk (fee4.84 -247), DD +34%/+34, ww +13238, st 2.05(2.74), b5 76%, w2l 0 X |  |  |  |  |  |  |  |
| RU_london_hS075 | -1582 $/wk (fee4.84 -1466), DD +43%/+43, ww +10574, st 1.67(2.74), b5 59%, w2l 0 X |  |  |  |  |  |  |  |

**nyam**

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL | lead |
|---|---|---|---|---|---|---|---|---|
| RU_nyam_hS125 | +465 $/wk (fee4.84 +484), DD +34%/+39, ww +658, st 1.07(1.29), b5 87%, w2l 2 | -444 $/wk (fee4.84 -420), DD +21%/+21, ww +2244, st 1.45(1.67), b5 68%, w2l 3 X |  |  |  |  |  |  |
| &nbsp;&nbsp;engine random skip L3M (same keep share, seeds) | DD -67/-31, mean -960/-666 | | | | | | | |
| &nbsp;&nbsp;placebo L3M (pl11/23/37) | DD +1/+23/+19, mean -709/+617/+800 | | | | | | | |
| &nbsp;&nbsp;engine random skip L6M (same keep share, seeds) | DD -30/-2, mean -980/-910 | | | | | | | |
| &nbsp;&nbsp;placebo L6M (pl11/23/37) | DD +23/-3/+22, mean -908/-815/-325 | | | | | | | |
| RU_nyam_hS1 | +424 $/wk (fee4.84 +445), DD +34%/+39, ww +1280, st 1.07(1.29), b5 83%, w2l 2 | -414 $/wk (fee4.84 -388), DD +18%/+18, ww +2244, st 1.45(1.67), b5 69%, w2l 3 X |  |  |  |  |  |  |
| &nbsp;&nbsp;engine random skip L3M (same keep share, seeds) | DD -25/-42, mean -653/-1976 | | | | | | | |
| &nbsp;&nbsp;placebo L3M (pl11/23/37) | DD +1/+23/+19, mean -840/+134/+1137 | | | | | | | |
| &nbsp;&nbsp;engine random skip L6M (same keep share, seeds) | DD +2/-10, mean -565/-1251 | | | | | | | |
| &nbsp;&nbsp;placebo L6M (pl11/23/37) | DD +13/-5/+24, mean -1186/-1001/-181 | | | | | | | |
| RU_nyam_hS075 | +294 $/wk (fee4.84 +321), DD +27%/+32, ww +4232, st 0.91(1.29), b5 81%, w2l 3 | -510 $/wk (fee4.84 -478), DD +12%/+12, ww +1045, st 1.33(1.67), b5 59%, w2l 4 X |  |  |  |  |  |  |
| &nbsp;&nbsp;engine random skip L3M (same keep share, seeds) | DD -8/-13, mean +432/-218 | | | | | | | |
| &nbsp;&nbsp;placebo L3M (pl11/23/37) | DD +9/+9/+9, mean -187/+135/+723 | | | | | | | |
| &nbsp;&nbsp;engine random skip L6M (same keep share, seeds) | DD +16/+12, mean +277/-764 | | | | | | | |
| &nbsp;&nbsp;placebo L6M (pl11/23/37) | DD +23/-7/+14, mean -1215/-979/-443 | | | | | | | |
| RU_nyam_hS05 | +61 $/wk (fee4.84 +104), DD +46%/+51, ww +4095, st 0.53(1.29), b5 58%, w2l 3 | -1321 $/wk (fee4.84 -1271), DD +31%/+31, ww +3959, st 0.95(1.67), b5 24%, w2l 6 X |  |  |  |  |  |  |
| &nbsp;&nbsp;engine random skip L3M (same keep share, seeds) | DD +44/-4, mean +813/-722 | | | | | | | |

**nypm**

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL | lead |
|---|---|---|---|---|---|---|---|---|
| RU_nypm_hS1 | +345 $/wk (fee4.84 +347), DD +33%/+33, ww +0, st 0.08(0.08), b5 127%, w2l 0 | -149 $/wk (fee4.84 -144), DD +33%/+33, ww +0, st 0.08(0.08), b5 80%, w2l 1 X |  |  |  |  |  |  |
| &nbsp;&nbsp;engine random skip L3M (same keep share, seeds) | DD -3/-0, mean -250/-183 | | | | | | | |
| &nbsp;&nbsp;placebo L3M (pl11/23/37) | DD +27/+19/+19, mean +249/+275/+230 | | | | | | | |
| &nbsp;&nbsp;engine random skip L6M (same keep share, seeds) | DD -3/-0, mean -500/-40 | | | | | | | |
| &nbsp;&nbsp;placebo L6M (pl11/23/37) | DD +27/+19/+19, mean -315/-226/-290 | | | | | | | |
| RU_nypm_hS125 | +345 $/wk (fee4.84 +347), DD +33%/+33, ww +0, st 0.08(0.08), b5 127%, w2l 0 | -149 $/wk (fee4.84 -144), DD +33%/+33, ww +0, st 0.08(0.08), b5 80%, w2l 1 X |  |  |  |  |  |  |
| &nbsp;&nbsp;engine random skip L3M (same keep share, seeds) | DD -3/-0, mean -250/-183 | | | | | | | |
| &nbsp;&nbsp;placebo L3M (pl11/23/37) | DD +19/+19/+0, mean +207/+207/+0 | | | | | | | |
| &nbsp;&nbsp;engine random skip L6M (same keep share, seeds) | DD -3/-0, mean -500/-40 | | | | | | | |
| &nbsp;&nbsp;placebo L6M (pl11/23/37) | DD +19/+0, mean -336/-396 | | | | | | | |
| RU_nypm_hS075 | +309 $/wk (fee4.84 +312), DD +33%/+33, ww +0, st 0.08(0.08), b5 118%, w2l 0 | -274 $/wk (fee4.84 -268), DD +33%/+33, ww +0, st 0.08(0.08), b5 72%, w2l 1 X |  |  |  |  |  |  |
| &nbsp;&nbsp;engine random skip L3M (same keep share, seeds) | DD +9/+12, mean -377/-170 | | | | | | | |
| &nbsp;&nbsp;placebo L3M (pl11/23/37) | DD +37/+19/+19, mean +366/+322/+298 | | | | | | | |
| &nbsp;&nbsp;engine random skip L6M (same keep share, seeds) | DD +9/+12, mean -445/-89 | | | | | | | |
| &nbsp;&nbsp;placebo L6M (pl11/23/37) | DD +37/+19/+19, mean -439/-313/-233 | | | | | | | |
| RU_nypm_hS05 | +152 $/wk (fee4.84 +159), DD +53%/+53, ww +1194, st 0.08(0.08), b5 83%, w2l 1 |  |  |  |  |  |  |  |

**l90**

| cell | L3M | L6M | HOLD | GAP | PRE | X' | FULL | lead |
|---|---|---|---|---|---|---|---|---|
| RU_l90_hS075 | -49 $/wk (fee4.84 -49), DD +0%/-3, ww +0, st 10.35(10.35), b5 100%, w2l 0 | -5 $/wk (fee4.84 -5), DD +0%/-3, ww +0, st 10.99(10.99), b5 100%, w2l 0 | -3 $/wk (fee4.84 -2), DD +0%/+0, ww +0, st 10.66(10.66), b5 100%, w2l 0 | -6 $/wk (fee4.84 -4), DD +0%, ww +0, st 9.90(9.90), b5 99%, w2l 0 |  |  |  |  |
| RU_l90_hS1 | -91 $/wk (fee4.84 -91), DD +0%/-3, ww +0, st 10.35(10.35), b5 100%, w2l 0 | -46 $/wk (fee4.84 -45), DD +0%/-3, ww +0, st 10.99(10.99), b5 100%, w2l 0 | -23 $/wk (fee4.84 -23), DD +0%/+0, ww +0, st 10.66(10.66), b5 100%, w2l 0 | +9 $/wk (fee4.84 +10), DD +0%, ww +0, st 9.90(9.90), b5 99%, w2l 0 | -34 $/wk (fee4.84 -32), DD +0%, ww +0, st 9.43(9.43), b5 100%, w2l 0 | -5 $/wk (fee4.84 -4), DD +0%, ww +0, st 10.82(10.82), b5 100%, w2l 0 | -20 $/wk (fee4.84 -19), DD +0%/+0, ww +0, st 10.14(10.14), b5 100%, w2l 0 |  |
| &nbsp;&nbsp;placebo L3M (pl11/23/37) | DD +0/+0/+0, mean -91/+0/+0 | | | | | | | |
| &nbsp;&nbsp;placebo L6M (pl11/23/37) | DD +0/+0/+0, mean -145/-55/-182 | | | | | | | |
| RU_l90_hS125 | -91 $/wk (fee4.84 -91), DD +0%/-3, ww +0, st 10.35(10.35), b5 100%, w2l 0 | -46 $/wk (fee4.84 -45), DD +0%/-3, ww +0, st 10.99(10.99), b5 100%, w2l 0 | -23 $/wk (fee4.84 -23), DD +0%/+0, ww +0, st 10.66(10.66), b5 100%, w2l 0 | +9 $/wk (fee4.84 +10), DD +0%, ww +0, st 9.90(9.90), b5 99%, w2l 0 |  |  |  |  |

## Session clock (2)

## Session caps (3)

## Neighbour-session reading

Every rule is generated for every session; a pass in one session is not carried to another (cells are scored per session scope, see tables).

