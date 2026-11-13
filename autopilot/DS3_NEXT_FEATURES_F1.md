# DS3_NEXT_FEATURES_F1 — T-NEXT-FEATURES items 1 (stack-level evidence) and 6 (after a halt/lock), W-F1

Generated 2026-11-13 18:38 UTC. Exact engine, one set per job, reference = JN05W2 (live panel base + F3 + E1 + C22 + BR3S + FLAT45K, 43 exact months) on the same months. Shadow only, no PASS claim. Prereg autopilot/NEXTF1_PREREG.md. Thresholds are counts (no dollar thresholds), so they transfer unchanged to x1.75 lots; the half-size rounding does not.

Hook code/th_nextf/nf_hooks.py (outermost of the hooklist). **sev**: N same-side losing closed trades by ANY book in the ET six-session, no new session extreme in the trade direction beyond the extreme at the last failure exit (completed 1-min bars) -> skip (S) or half (H) for every book on that side; suffix N = scorecard convention (opposite-side trades do not end the run). **ah**: previous 18:00-ET day ended day-halted by the loss cap (L), give-back lock (K) or either (E) -> first signal dropped (S) or first sized entry halved (H).

Baseline stack same-side losing run (behavioural scorecard c convention): JN05W2 L6M max 13 / p95 6, HOLD max 13 / p95 6; target max <= 6.

## 0. Trend-week clause first (L6M weekly check, 5 best JN05W2 weeks kept, JN05W2 winning weeks turned losing) and L6M/HOLD summary

| set | months | 5 best wks kept | winning wks turned losing | L6M cut % | L6M d mean/wk (all wks) | L6M run max/p95 (ref 13/6) | HOLD cut % | HOLD d mean/wk | HOLD run max/p95 | WF cut / beat |
|--|--|--|--|--|--|--|--|--|--|--|
| NF_AHH_E | 12 | 98% ($310k of $316k) | 0 of 20 | -10.0 | -519 | 13/6 | -5.6 | -99 | 13/6 | - |
| NF_AHH_K | 12 | 98% ($311k of $316k) | 0 of 20 | 0.0 | -450 | 13/6 | -0.0 | -297 | 13/6 | - |
| NF_AHH_L | 12 | 100% ($316k of $316k) | 0 of 20 | -10.0 | -143 | 13/6 | -5.6 | 161 | 13/6 | - |
| NF_AHS_E | 12 | 96% ($304k of $316k) | 0 of 20 | -11.0 | -1224 | 12/6 | 1.1 | -648 | 12/6 | - |
| NF_AHS_K | 12 | 98% ($309k of $316k) | 0 of 20 | 0.0 | -718 | 12/6 | 1.6 | -418 | 12/6 | - |
| NF_AHS_L | 12 | 98% ($311k of $316k) | 0 of 20 | -11.0 | -505 | 13/6 | -0.5 | -231 | 13/6 | - |
| NF_D_OB_best_m2_J | 16 | 69% ($218k of $316k) | 1 of 20 | 14.4 | -7348 | 10/6 | 15.9 | -5581 | 10/5 | - |
| NF_D_OB_best_m2_L | 16 | 95% ($300k of $316k) | 2 of 20 | -59.4 | -5847 | 10/5 | -52.3 | -5116 | 10/5 | - |
| NF_D_PL_day_half_m1p5_J | 16 | 70% ($222k of $316k) | 1 of 20 | 34.3 | -6489 | 14/6 | 44.5 | -4033 | 14/6 | - |
| NF_D_PL_day_half_m1p5_L | 16 | 94% ($297k of $316k) | 1 of 20 | 4.3 | -2652 | 14/6 | 33.9 | -2062 | 14/6 | - |
| NF_D_PL_day_half_m2_J | 16 | 70% ($222k of $316k) | 0 of 20 | 33.3 | -6436 | 14/6 | 41.4 | -3998 | 14/6 | - |
| NF_D_PL_day_half_m2_L | 16 | 94% ($297k of $316k) | 0 of 20 | 4.3 | -1542 | 14/6 | 26.8 | -1422 | 14/6 | - |
| NF_D_ST_half_2_J | 16 | 65% ($207k of $316k) | 2 of 20 | 35.7 | -7005 | 14/6 | 35.9 | -4403 | 14/6 | - |
| NF_D_ST_half_2_L | 16 | 86% ($271k of $316k) | 0 of 20 | -2.2 | -3688 | 13/6 | 18.1 | -1798 | 13/6 | - |
| NF_D_ST_half_3_J | 16 | 74% ($234k of $316k) | 1 of 20 | 25.9 | -5702 | 14/6 | 17.3 | -4031 | 14/6 | - |
| NF_D_ST_half_3_L | 16 | 100% ($315k of $316k) | 0 of 20 | -37.0 | -1582 | 13/6 | 1.2 | -910 | 13/6 | - |
| NF_D_ST_half_4_J | 16 | 74% ($233k of $316k) | 1 of 20 | 34.1 | -5031 | 14/6 | 13.3 | -3766 | 14/6 | - |
| NF_D_ST_half_4_L | 16 | 100% ($318k of $316k) | 0 of 20 | -5.1 | -698 | 13/6 | -0.9 | -358 | 13/6 | - |
| NF_D_WD_fresh_3_J | 16 | 44% ($139k of $316k) | 3 of 20 | 54.0 | -11643 | 14/5 | 36.7 | -8328 | 14/5 | - |
| NF_D_WD_fresh_3_L | 16 | 63% ($198k of $316k) | 2 of 20 | 33.3 | -11252 | 13/5 | 5.2 | -7215 | 13/5 | - |
| NF_D_WD_half_3_J | 16 | 68% ($214k of $316k) | 1 of 20 | 42.3 | -5995 | 14/6 | 34.3 | -4271 | 14/6 | - |
| NF_D_WD_half_3_L | 16 | 92% ($293k of $316k) | 0 of 20 | 12.8 | -1544 | 13/6 | 11.6 | -565 | 13/6 | - |
| NF_D_WD_half_5_J | 16 | 70% ($222k of $316k) | 1 of 20 | 38.8 | -5215 | 14/6 | 38.6 | -3418 | 14/6 | - |
| NF_D_WD_half_5_L | 16 | 89% ($282k of $316k) | 0 of 20 | 19.2 | -1973 | 13/6 | -6.6 | -550 | 13/6 | - |
| NF_SEV2H | 12 | 96% ($304k of $316k) | 0 of 20 | -2.3 | -463 | 14/6 | 2.5 | -254 | 14/6 | - |
| NF_SEV2HN | 12 | 90% ($286k of $316k) | 0 of 20 | -51.7 | -2096 | 14/6 | -9.6 | -1605 | 14/6 | - |
| NF_SEV2S | 12 | 95% ($300k of $316k) | 1 of 20 | -4.6 | -143 | 11/6 | -26.0 | -746 | 11/5 | - |
| NF_SEV2SN | 12 | 70% ($221k of $316k) | 2 of 20 | -172.1 | -5974 | 10/5 | -56.6 | -5027 | 10/5 | - |
| NF_SEV3H | 12 | 100% ($315k of $316k) | 0 of 20 | -3.3 | 328 | 14/6 | 0.0 | -114 | 14/6 | - |
| NF_SEV3HN | 12 | 100% ($315k of $316k) | 0 of 20 | -14.2 | -3 | 14/6 | -10.3 | -461 | 14/6 | - |
| NF_SEV3S | 12 | 98% ($310k of $316k) | 0 of 20 | -10.1 | -328 | 11/6 | 0.7 | -687 | 11/6 | - |
| NF_SEV3SN | 12 | 87% ($274k of $316k) | 1 of 20 | -85.4 | -3265 | 10/5 | -22.8 | -3349 | 10/5 | - |
| NF_SEV4H | 12 | 99% ($313k of $316k) | 0 of 20 | 0.0 | -221 | 13/6 | 0.0 | -177 | 13/6 | - |
| NF_SEV4HN | 12 | 97% ($307k of $316k) | 0 of 20 | -8.5 | -247 | 14/6 | -22.3 | -443 | 14/6 | - |
| NF_SEV4S | 12 | 97% ($307k of $316k) | 0 of 20 | 0.0 | -515 | 13/6 | 0.0 | -375 | 13/6 | - |
| NF_SEV4SN | 12 | 90% ($286k of $316k) | 0 of 20 | -28.3 | -1487 | 11/5 | -21.5 | -867 | 11/5 | - |

cut % = maxDD of the stack vs JN05W2 (positive = shallower); d mean = all-weeks mean difference ($/wk); a window appears only when all its months are present. PRE / X' / GAP follow for cells with L6M cut >= 5% and d mean >= -$1,000/wk (prereg).

Identity: NF_ID99 (hook on, rule never fires) is trade-for-trade identical to JN05W2 on 202610 (598 trades, net $25,943.82).
