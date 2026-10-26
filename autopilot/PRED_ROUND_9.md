# PRED ROUND 9 - block B round 1 - B1B2B3

Best HOLDOUT F-R AUC: +15 POOLED 0.529 [-,-] | ASIA - | LONDON - | NY -
Best HOLDOUT F-R AUC: +30 POOLED 0.545 [-,-] | ASIA - | LONDON - | NY -
Best G HOLDOUT AUC: 0.583 [0.56,0.61]
Gap to FOUND: n/a AUC, n/a of 5 economic conditions short.
not found - short by n/a AUC and 5 of 5 economic conditions

prereg 783bce0b313e342c453efab40f0e0edf3e82153f693e7f9fa98ddd08c9795d50 ; trials added 1400 ; truncation audit {'decisions': 160, 'feature_checks': 41280, 'mismatches': 0, 'fixed_and_rerun': False, 'note': 'engine 160 decisions x 258 cols, 0 mismatches; minute builder 6 months, 0 mismatches after correcting the audit boundary (audit script compared the partial final minute; builder itself unchanged)'} ; holdout scored True ; feature store ['l2vast/pred/store/B1_round1.parquet', 'l2vast/pred/store/B2_round1.parquet', 'l2vast/pred/store/B3_round1.parquet', 'l2vast/pred/store/B1_round1_sig.parquet', 'l2vast/pred/store/B2_round1_sig.parquet', 'l2vast/pred/store/B3_round1_sig.parquet']

| family | h | session | model | AUC [CI] WF | AUC [CI] HOLDOUT | CPCV | strata-matched HOLD AUC | uncond HOLD AUC (activity) | noise | switch/gate d$/wk | d maxDD | placebo | pass | | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B1-resiliency-G | sig | POOLED | logit2 | 0.581 [0.56,0.60] | 0.583 [0.56,0.61] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B3-toxicity-G | sig | POOLED | logit2 | 0.581 [0.56,0.60] | 0.582 [0.56,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B-ctx-only-G | sig | POOLED | logit2 | 0.581 [0.56,0.60] | 0.581 [0.56,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B2-impact-G | sig | POOLED | logit2 | 0.582 [0.56,0.60] | 0.578 [0.56,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B123-b1b2b3-G | sig | POOLED | rf | 0.581 [0.56,0.60] | 0.578 [0.55,0.60] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B3-toxicity | +30 | POOLED | rf | - | 0.545 [-,-] | - | - | 0.689 | ok | - | - | - | - | stack | locked label (reference only) |
| B2-impact | +30 | POOLED | rf | - | 0.534 [-,-] | - | - | 0.681 | ok | - | - | - | - | stack | locked label (reference only) |
| B123-b1b2b3 | +30 | POOLED | rf | - | 0.533 [-,-] | - | - | 0.663 | ok | - | - | - | - | stack | locked label (reference only) |
| B123-b1b2b3 | +30 | POOLED | rf | - | 0.532 [-,-] | - | - | 0.638 | ok | - | - | - | - |  | locked label (reference only) |
| B1-resiliency | +30 | POOLED | rf | - | 0.530 [-,-] | - | - | 0.665 | ok | - | - | - | - | stack | locked label (reference only) |
| B2-impact | +15 | POOLED | rf | - | 0.529 [-,-] | - | - | 0.689 | ok | - | - | - | - | stack | locked label (reference only) |
| B123-b1b2b3 | +15 | POOLED | rf | - | 0.526 [-,-] | - | - | 0.634 | ok | - | - | - | - |  | locked label (reference only) |
| B1-resiliency | +15 | POOLED | rf | - | 0.526 [-,-] | - | - | 0.646 | ok | - | - | - | - | stack | locked label (reference only) |
| B3-toxicity | +10 | POOLED | stack | - | 0.526 [-,-] | - | - | 0.670 | - | - | - | - | - | stack | locked label (reference only) |
| B123-b1b2b3 | +20 | POOLED | rf | - | 0.524 [-,-] | - | - | 0.629 | ok | - | - | - | - |  | locked label (reference only) |
| B3-toxicity-G | sig | POOLED | rf | 0.513 [0.49,0.53] | 0.516 [0.49,0.55] | - | - | - | - | - | - | - | - | stack | locked label (reference only) |
| B3-toxicity | +15 | POOLED | rf | - | 0.514 [-,-] | - | - | 0.682 | ok | - | - | - | - | stack | locked label (reference only) |
| B123-b1b2b3 | +15 | POOLED | rf | - | 0.512 [-,-] | - | - | 0.637 | ok | - | - | - | - | stack | locked label (reference only) |
| B1-resiliency | pre | POOLED | rf | - | 0.511 [-,-] | - | - | 0.662 | ok | - | - | - | - | stack | locked label (reference only) |
| B123-b1b2b3-G | sig | POOLED | rf | 0.506 [0.49,0.52] | 0.509 [0.48,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| B2-impact-G | sig | POOLED | rf | 0.504 [0.49,0.52] | 0.506 [0.48,0.53] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| B1-resiliency-G | sig | POOLED | gbt3 | 0.509 [0.49,0.53] | 0.499 [0.48,0.52] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| B-ctx-only-G | sig | POOLED | gbt3 | 0.497 [0.48,0.51] | 0.486 [0.46,0.51] | - | - | - | - | - | - | - | - |  | locked label (reference only) |
| B1-resiliency | pre | ASIA | rf | - | - | - | - | 0.552 | ok | - | - | - | - | stack | locked label (reference only) |
| B1-resiliency | pre | LONDON | rf | - | - | - | - | 0.671 | ok | - | - | - | - | stack | locked label (reference only) |
| B1-resiliency | pre | NY | rf | - | - | - | - | 0.686 | ok | - | - | - | - | stack | locked label (reference only) |
| B1-resiliency | +15 | ASIA | rf | - | - | - | - | 0.515 | ok | - | - | - | - | stack | locked label (reference only) |
| B1-resiliency | +15 | LONDON | rf | - | - | - | - | 0.628 | ok | - | - | - | - | stack | locked label (reference only) |
| B1-resiliency | +15 | NY | rf | - | - | - | - | 0.684 | ok | - | - | - | - | stack | locked label (reference only) |
| B1-resiliency | +30 | ASIA | rf | - | - | - | - | 0.500 | ok | - | - | - | - | stack | locked label (reference only) |
| B1-resiliency | +30 | LONDON | rf | - | - | - | - | 0.647 | ok | - | - | - | - | stack | locked label (reference only) |
| B1-resiliency | +30 | NY | rf | - | - | - | - | 0.745 | ok | - | - | - | - | stack | locked label (reference only) |
| B2-impact | +15 | ASIA | rf | - | - | - | - | 0.541 | ok | - | - | - | - | stack | locked label (reference only) |
| B2-impact | +15 | LONDON | rf | - | - | - | - | 0.660 | ok | - | - | - | - | stack | locked label (reference only) |
| B2-impact | +15 | NY | rf | - | - | - | - | 0.789 | ok | - | - | - | - | stack | locked label (reference only) |
| B2-impact | +30 | ASIA | rf | - | - | - | - | 0.498 | ok | - | - | - | - | stack | locked label (reference only) |
| B2-impact | +30 | LONDON | rf | - | - | - | - | 0.676 | ok | - | - | - | - | stack | locked label (reference only) |
| B2-impact | +30 | NY | rf | - | - | - | - | 0.790 | ok | - | - | - | - | stack | locked label (reference only) |
| B3-toxicity | +10 | ASIA | stack | - | - | - | - | 0.528 | - | - | - | - | - | stack | locked label (reference only) |
| B3-toxicity | +10 | LONDON | stack | - | - | - | - | 0.651 | - | - | - | - | - | stack | locked label (reference only) |
| B3-toxicity | +10 | NY | stack | - | - | - | - | 0.775 | - | - | - | - | - | stack | locked label (reference only) |
| B3-toxicity | +15 | ASIA | rf | - | - | - | - | 0.527 | ok | - | - | - | - | stack | locked label (reference only) |
| B3-toxicity | +15 | LONDON | rf | - | - | - | - | 0.645 | ok | - | - | - | - | stack | locked label (reference only) |
| B3-toxicity | +15 | NY | rf | - | - | - | - | 0.796 | ok | - | - | - | - | stack | locked label (reference only) |
| B3-toxicity | +30 | ASIA | rf | - | - | - | - | 0.507 | ok | - | - | - | - | stack | locked label (reference only) |
| B3-toxicity | +30 | LONDON | rf | - | - | - | - | 0.674 | ok | - | - | - | - | stack | locked label (reference only) |
| B3-toxicity | +30 | NY | rf | - | - | - | - | 0.809 | ok | - | - | - | - | stack | locked label (reference only) |
| B123-b1b2b3 | +15 | ASIA | rf | - | - | - | - | 0.537 | ok | - | - | - | - |  | locked label (reference only) |
| B123-b1b2b3 | +15 | LONDON | rf | - | - | - | - | 0.600 | ok | - | - | - | - |  | locked label (reference only) |
| B123-b1b2b3 | +15 | NY | rf | - | - | - | - | 0.627 | ok | - | - | - | - |  | locked label (reference only) |
| B123-b1b2b3 | +20 | ASIA | rf | - | - | - | - | 0.509 | ok | - | - | - | - |  | locked label (reference only) |
| B123-b1b2b3 | +20 | LONDON | rf | - | - | - | - | 0.582 | ok | - | - | - | - |  | locked label (reference only) |
| B123-b1b2b3 | +20 | NY | rf | - | - | - | - | 0.639 | ok | - | - | - | - |  | locked label (reference only) |
| B123-b1b2b3 | +30 | ASIA | rf | - | - | - | - | 0.510 | ok | - | - | - | - |  | locked label (reference only) |
| B123-b1b2b3 | +30 | LONDON | rf | - | - | - | - | 0.584 | ok | - | - | - | - |  | locked label (reference only) |
| B123-b1b2b3 | +30 | NY | rf | - | - | - | - | 0.665 | ok | - | - | - | - |  | locked label (reference only) |
| B123-b1b2b3 | +15 | ASIA | rf | - | - | - | - | 0.495 | ok | - | - | - | - | stack | locked label (reference only) |
| B123-b1b2b3 | +15 | LONDON | rf | - | - | - | - | 0.618 | ok | - | - | - | - | stack | locked label (reference only) |
| B123-b1b2b3 | +15 | NY | rf | - | - | - | - | 0.683 | ok | - | - | - | - | stack | locked label (reference only) |
| B123-b1b2b3 | +30 | ASIA | rf | - | - | - | - | 0.497 | ok | - | - | - | - | stack | locked label (reference only) |
| B123-b1b2b3 | +30 | LONDON | rf | - | - | - | - | 0.652 | ok | - | - | - | - | stack | locked label (reference only) |
| B123-b1b2b3 | +30 | NY | rf | - | - | - | - | 0.733 | ok | - | - | - | - | stack | locked label (reference only) |

One-sentence notes:
- B1-resiliency 0 POOLED: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B1-resiliency 0 ASIA: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B1-resiliency 0 LONDON: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B1-resiliency 0 NY: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B1-resiliency 15 POOLED: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B1-resiliency 15 ASIA: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B1-resiliency 15 LONDON: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B1-resiliency 15 NY: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B1-resiliency 30 POOLED: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B1-resiliency 30 ASIA: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B1-resiliency 30 LONDON: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B1-resiliency 30 NY: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B2-impact 15 POOLED: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B2-impact 15 ASIA: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B2-impact 15 LONDON: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B2-impact 15 NY: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B2-impact 30 POOLED: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B2-impact 30 ASIA: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B2-impact 30 LONDON: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B2-impact 30 NY: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B3-toxicity 10 POOLED: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B3-toxicity 10 ASIA: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B3-toxicity 10 LONDON: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B3-toxicity 10 NY: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B3-toxicity 15 POOLED: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B3-toxicity 15 ASIA: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B3-toxicity 15 LONDON: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B3-toxicity 15 NY: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B3-toxicity 30 POOLED: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B3-toxicity 30 ASIA: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B3-toxicity 30 LONDON: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B3-toxicity 30 NY: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 15 POOLED: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 15 ASIA: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 15 LONDON: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 15 NY: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 20 POOLED: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 20 ASIA: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 20 LONDON: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 20 NY: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 30 POOLED: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 30 ASIA: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 30 LONDON: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 30 NY: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 15 POOLED: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 15 ASIA: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 15 LONDON: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 15 NY: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 30 POOLED: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 30 ASIA: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 30 LONDON: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B123-b1b2b3 30 NY: below R0 baseline on holdout (R0 +15 pooled 0.703); no econ grid run
- B-ctx-only-G -1 POOLED: G ~0.5 on stop_vs_target; stop_vs_rest ~0.58 is time-of-session (ctx-only equal)
- B1-resiliency-G -1 POOLED: G ~0.5 on stop_vs_target; stop_vs_rest ~0.58 is time-of-session (ctx-only equal)
- B2-impact-G -1 POOLED: G ~0.5 on stop_vs_target; stop_vs_rest ~0.58 is time-of-session (ctx-only equal)
- B3-toxicity-G -1 POOLED: G ~0.5 on stop_vs_target; stop_vs_rest ~0.58 is time-of-session (ctx-only equal)
- B123-b1b2b3-G -1 POOLED: G ~0.5 on stop_vs_target; stop_vs_rest ~0.58 is time-of-session (ctx-only equal)
- B-ctx-only-G -1 POOLED: G ~0.5 on stop_vs_target; stop_vs_rest ~0.58 is time-of-session (ctx-only equal)
- B1-resiliency-G -1 POOLED: G ~0.5 on stop_vs_target; stop_vs_rest ~0.58 is time-of-session (ctx-only equal)
- B2-impact-G -1 POOLED: G ~0.5 on stop_vs_target; stop_vs_rest ~0.58 is time-of-session (ctx-only equal)
- B3-toxicity-G -1 POOLED: G ~0.5 on stop_vs_target; stop_vs_rest ~0.58 is time-of-session (ctx-only equal)
- B123-b1b2b3-G -1 POOLED: G ~0.5 on stop_vs_target; stop_vs_rest ~0.58 is time-of-session (ctx-only equal)
