# DS3_SMART_A2 — T-SMART items A2 (stack as one position), A4 (hedge instead of exit), A5 (stop-and-reverse, opposite-book conflict), W-SM2

Generated 2026-11-12 18:39 UTC. Exact engine, one set per job, reference = JN05W2 (live panel base + F3 + E1 + C22 + BR3S + FLAT45K, 43 exact months). Shadow only, no PASS claim.
**CAVEAT (every page):** the engine state cut fires in the engine but did NOT fire live on 11-11 (autopilot/DS3_P7_CUT_FIDELITY.md). Rules below are scored with the engine cuts as in JN05W2; the full-stop-only variants are added when that base exists. Prereg autopilot/SMART_A2_PREREG.md (sha 597c41f51e81ba3c). Hook code/th_sm2/sm2_hooks.py. R = $1,200 fixed; at the user lots (x1.75) fixed-dollar thresholds x1.75, count rules unchanged. Hedge fee 12.0 $/NQ-equivalent RT assumed (MNQ, unverified), bound 4.84.

## 0. Trend-week clause first (L6M weekly check, 5 best JN05W2 weeks kept, JN05W2 winning weeks turned losing) and L6M/HOLD summary

| set | months | 5 best wks kept | winning wks turned losing | L6M cut % | L6M d mean/wk (all wks) | L6M run max/p95 (ref 13/6) | HOLD cut % | HOLD d mean/wk | HOLD run max/p95 | WF cut / beat |
|--|--|--|--|--|--|--|--|--|--|--|

cut % = maxDD of the stack vs JN05W2 (positive = shallower); d mean = all-weeks mean difference ($/wk); a window appears only when all its months are present. PRE / X' / GAP follow for cells with L6M cut >= 5% and d mean >= -$1,000/wk (prereg).

Identity: NF_ID99 (hook on, rule never fires) is trade-for-trade identical to JN05W2 on 202610 (598 trades, net $25,943.82).
