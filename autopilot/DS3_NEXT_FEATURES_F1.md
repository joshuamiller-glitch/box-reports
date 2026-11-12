# DS3_NEXT_FEATURES_F1 — T-NEXT-FEATURES items 1 (stack-level evidence) and 6 (after a halt/lock), W-F1

Generated 2026-11-12 18:51 UTC. Exact engine, one set per job, reference = JN05W2 (live panel base + F3 + E1 + C22 + BR3S + FLAT45K, 43 exact months) on the same months. Shadow only, no PASS claim. Prereg autopilot/NEXTF1_PREREG.md. Thresholds are counts (no dollar thresholds), so they transfer unchanged to x1.75 lots; the half-size rounding does not.

Hook code/th_nextf/nf_hooks.py (outermost of the hooklist). **sev**: N same-side losing closed trades by ANY book in the ET six-session, no new session extreme in the trade direction beyond the extreme at the last failure exit (completed 1-min bars) -> skip (S) or half (H) for every book on that side; suffix N = scorecard convention (opposite-side trades do not end the run). **ah**: previous 18:00-ET day ended day-halted by the loss cap (L), give-back lock (K) or either (E) -> first signal dropped (S) or first sized entry halved (H).

Baseline stack same-side losing run (behavioural scorecard c convention): JN05W2 L6M max 13 / p95 6, HOLD max 13 / p95 6; target max <= 6.

## 0. Trend-week clause first (L6M weekly check, 5 best JN05W2 weeks kept, JN05W2 winning weeks turned losing) and L6M/HOLD summary

| set | months | 5 best wks kept | winning wks turned losing | L6M cut % | L6M d mean/wk (all wks) | L6M run max/p95 (ref 13/6) | HOLD cut % | HOLD d mean/wk | HOLD run max/p95 | WF cut / beat |
|--|--|--|--|--|--|--|--|--|--|--|
| NF_AHH_E | 5 | (running) |||||||||
| NF_AHH_L | 6 | 100% ($316k of $316k) | 0 of 20 | -10.0 | -143 | 13/6 | - | - | -/- | - |
| NF_AHS_E | 2 | (running) |||||||||
| NF_AHS_L | 2 | (running) |||||||||
| NF_D_OB_best_m2_J | 6 | 69% ($218k of $316k) | 1 of 20 | 14.4 | -7348 | 10/6 | - | - | -/- | - |
| NF_D_OB_best_m2_L | 6 | 95% ($300k of $316k) | 2 of 20 | -59.4 | -5847 | 10/5 | - | - | -/- | - |
| NF_D_PL_day_half_m1p5_J | 6 | 70% ($222k of $316k) | 1 of 20 | 34.3 | -6489 | 14/6 | - | - | -/- | - |
| NF_D_PL_day_half_m1p5_L | 7 | 94% ($297k of $316k) | 1 of 20 | 4.3 | -2652 | 14/6 | - | - | -/- | - |
| NF_D_PL_day_half_m2_J | 6 | 70% ($222k of $316k) | 0 of 20 | 33.3 | -6436 | 14/6 | - | - | -/- | - |
| NF_D_PL_day_half_m2_L | 6 | 94% ($297k of $316k) | 0 of 20 | 4.3 | -1542 | 14/6 | - | - | -/- | - |
| NF_D_ST_half_2_J | 6 | 65% ($207k of $316k) | 2 of 20 | 35.7 | -7005 | 14/6 | - | - | -/- | - |
| NF_D_ST_half_2_L | 7 | 86% ($271k of $316k) | 0 of 20 | -2.2 | -3688 | 13/6 | - | - | -/- | - |
| NF_D_ST_half_3_J | 6 | 74% ($234k of $316k) | 1 of 20 | 25.9 | -5702 | 14/6 | - | - | -/- | - |
| NF_D_ST_half_4_J | 6 | 74% ($233k of $316k) | 1 of 20 | 34.1 | -5031 | 14/6 | - | - | -/- | - |
| NF_D_WD_fresh_3_J | 6 | 44% ($139k of $316k) | 3 of 20 | 54.0 | -11643 | 14/5 | - | - | -/- | - |
| NF_D_WD_half_3_L | 6 | 92% ($293k of $316k) | 0 of 20 | 12.8 | -1544 | 13/6 | - | - | -/- | - |
| NF_SEV2HN | 9 | 90% ($286k of $316k) | 0 of 20 | -51.7 | -2096 | 14/6 | - | - | -/- | - |
| NF_SEV2S | 0 | (running) |||||||||
| NF_SEV3H | 3 | (running) |||||||||
| NF_SEV3HN | 6 | 100% ($315k of $316k) | 0 of 20 | -14.2 | -3 | 14/6 | - | - | -/- | - |
| NF_SEV3S | 1 | (running) |||||||||
| NF_SEV3SN | 6 | 87% ($274k of $316k) | 1 of 20 | -85.4 | -3265 | 10/5 | - | - | -/- | - |
| NF_SEV4HN | 1 | (running) |||||||||
| NF_SEV4SN | 7 | 90% ($286k of $316k) | 0 of 20 | -28.3 | -1487 | 11/5 | - | - | -/- | - |

cut % = maxDD of the stack vs JN05W2 (positive = shallower); d mean = all-weeks mean difference ($/wk); a window appears only when all its months are present. PRE / X' / GAP follow for cells with L6M cut >= 5% and d mean >= -$1,000/wk (prereg).

Identity: NF_ID99 (hook on, rule never fires) is trade-for-trade identical to JN05W2 on 202610 (598 trades, net $25,943.82).
