# DS3_SMART_A2 — T-SMART items A2 (stack as one position), A4 (hedge instead of exit), A5 (stop-and-reverse, opposite-book conflict), W-SM2

Generated 2026-11-13 07:42 UTC. Exact engine, one set per job, reference = JN05W2 (live panel base + F3 + E1 + C22 + BR3S + FLAT45K, 43 exact months). Shadow only, no PASS claim.
**CAVEAT (every page):** the engine state cut fires in the engine but did NOT fire live on 11-11 (autopilot/DS3_P7_CUT_FIDELITY.md). Rules below are scored with the engine cuts as in JN05W2; the full-stop-only variants are added when that base exists. Prereg autopilot/SMART_A2_PREREG.md (sha 597c41f51e81ba3c). Hook code/th_sm2/sm2_hooks.py. R = $1,200 fixed; at the user lots (x1.75) fixed-dollar thresholds x1.75, count rules unchanged. Hedge fee 12.0 $/NQ-equivalent RT assumed (MNQ, unverified), bound 4.84.

## 0. Trend-week clause first (L6M weekly check, 5 best JN05W2 weeks kept, JN05W2 winning weeks turned losing) and L6M/HOLD summary

| set | months | 5 best wks kept | winning wks turned losing | L6M cut % | L6M d mean/wk (all wks) | L6M run max/p95 (ref 13/6) | HOLD cut % | HOLD d mean/wk | HOLD run max/p95 | WF cut / beat |
|--|--|--|--|--|--|--|--|--|--|--|
| SM_A1E_C10L | 9 | 76% ($239k of $316k) | 1 of 20 | -41.9 | -5318 | 15/7 | - | - | -/- | - |
| SM_A1E_L0L | 10 | 100% ($318k of $316k) | 0 of 20 | -1.4 | -13 | 11/6 | - | - | -/- | - |
| SM_A1E_XL | 36 | 100% ($315k of $316k) | 0 of 20 | 0.0 | 508 | 15/6 | -4.8 | 468 | 15/6 | - |
| SM_A1N_C10L | 10 | 44% ($139k of $316k) | 5 of 20 | -86.2 | -13319 | 9/6 | - | - | -/- | - |
| SM_A1N_L0L | 36 | 71% ($224k of $316k) | 2 of 20 | -72.2 | -6798 | 10/5 | -26.4 | -2859 | 10/5 | - |
| SM_A1N_XL | 9 | 68% ($216k of $316k) | 2 of 20 | -84.9 | -8032 | 10/5 | - | - | -/- | - |
| SM_A1_ID | 1 | (running) |||||||||
| SM_A1_NC0 | 34 | 70% ($223k of $316k) | 2 of 20 | -51.3 | -6993 | 10/5 | -56.9 | -3370 | 10/5 | - |
| SM_A1_T | 1 | (running) |||||||||
| SM_A6_freshNP7 | 11 | 81% ($257k of $316k) | 0 of 20 | 15.8 | -4947 | 10/5 | - | - | -/- | - |
| SM_A6_halfALL | 12 | 99% ($313k of $316k) | 0 of 20 | -5.2 | -1117 | 14/6 | -0.4 | -1188 | 14/6 | - |
| SM_A6_halfNP7 | 6 | 107% ($337k of $316k) | 0 of 20 | 11.8 | 383 | 13/6 | - | - | -/- | - |
| SM_A6_skipM7 | 12 | 100% ($316k of $316k) | 0 of 20 | -4.0 | -407 | 13/6 | 15.1 | 550 | 13/5 | - |
| SM_A6_skipNP7 | 11 | 88% ($278k of $316k) | 2 of 20 | -5.1 | -4620 | 9/5 | - | - | -/- | - |
| SM_A7_P7a | 9 | 88% ($278k of $316k) | 1 of 20 | 19.7 | -4317 | 14/6 | - | - | -/- | - |

cut % = maxDD of the stack vs JN05W2 (positive = shallower); d mean = all-weeks mean difference ($/wk); a window appears only when all its months are present. PRE / X' / GAP follow for cells with L6M cut >= 5% and d mean >= -$1,000/wk (prereg).

Identity gate: SM_ID99 (hook on, no rule fires) must equal JN05W2 on 202610 (598 trades, net $25,943.82) - see section I below once its month is DONE.


## NOCUT base (JN05W2_NOCUT = JN05W2 with the engine state cut OFF on all books: native 60 worked stop + 80 catastrophe only; FLAT45K, E1, C22, BR3S, F3 panel layers untouched; F3 context cut removed because it is a cut)

Compare every rule against this base: it is the engine as the live D7 behaved on 11-11 (state cut not firing). Reference below = JN05W2 (cut on).

**JN05W2_NOCUT**: 39 of 43 months DONE.

Trend-week clause (L6M, vs cut-on reference): 5 best weeks kept $227k of $316k (72%); winning weeks turned losing 2 of 20.

| window | maxDD $ (NOCUT) | maxDD $ (ref) | cut % | d mean/wk (all wks) | stack run max/p95 |
|--|--|--|--|--|--|
| L1M | 36253 | 36371 | 0.3 | -2728 | 8/5 |
| L3M | 36253 | 36371 | 0.3 | -1556 | 10/5 |
| L6M | 50815 | 36371 | -39.7 | -5410 | 10/5 |
| HOLD | 99884 | 63185 | -58.1 | -2907 | 10/5 |

**JN05W2J_NOCUT**: 27 of 43 months DONE.

Trend-week clause (L6M, vs cut-on reference): 5 best weeks kept $204k of $244k (83%); winning weeks turned losing 3 of 21.

| window | maxDD $ (NOCUT) | maxDD $ (ref) | cut % | d mean/wk (all wks) | stack run max/p95 |
|--|--|--|--|--|--|
| L1M | 28277 | 17862 | -58.3 | -7192 | 8/5 |
| L3M | 28277 | 17862 | -58.3 | -4597 | 10/5 |
| L6M | 36550 | 23965 | -52.5 | -4077 | 10/5 |
| HOLD | 83574 | 43622 | -91.6 | -3222 | 10/5 |
