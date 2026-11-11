# DS3_WORKS - T-WORKS expand-what-works (aggregate page; built by W-J; 2026-11-11T13:38:44Z; Shadow only, no PASS claims)

Sections A, B, C are the workers' own pages (DS3_WORKS_A/B/C.md) merged below. Section D is W-J: the reference rows (JN04RM vs LPB_BASE), the JN05 composition and the REFIT 2026-11-22 preview. Every number is exact-engine, live panel base (P7 day cap 8,400 + table 7,4,0,4,0,0 + P7 cut 40/5x/w5/p3), reference LPB_BASE, ROLLFIX1.

## D0. Reference rows (exact, rule mode, 43 months)

| cell | window | mean $/wk | mean_ref (LPB_BASE) | maxDD | maxDD_ref | cut % | d mean | WF beat % | label |
|--|--|--|--|--|--|--|--|--|--|
| JN04RM | L1M | 10653 | 17539 | 27056 | 51253 | +47.2 | -6886 | 90 |  |
| JN04RM | L3M | 15022 | 17224 | 41699 | 77224 | +46.0 | -2202 | 90 |  |
| JN04RM | L6M | 19862 | 21495 | 41699 | 77224 | +46.0 | -1633 | 90 | OK-PRIOR (allow 25.0%, WF 90%) |
| JN04RM | HOLD | 12954 | 16540 | 72757 | 78842 | +7.7 | -3586 | 90 |  |
| JN04RM | PRE | 8714 | 10548 | 66714 | 99479 | +32.9 | -1834 | 90 |  |
| JN04RM | X' | 2195 | 2553 | 64077 | 122553 | +47.7 | -357 | 90 |  |

LPB_BASE is the reference itself (cut 0, d mean 0 by construction).

## D1. Harness reproduction check

| month | trades JN04RM / JN05W_REF | net JN04RM | net JN05W_REF | trade-by-trade identical (book, lots, entry_ns, exit_ns, net) |
|--|--|--|--|--|
| 202610 | 858 / 858 | 20778.50 | 20778.50 | IDENTICAL |
| 202608 | 695 / 695 | 38461.34 | 38461.34 | IDENTICAL |

Verdict: JN04RM reproduced through the W-J harness to the dollar.

## D2. JN05 composition and REFIT preview (W-J)

Status at the first build: harness ready, no A/B/C winners have landed, so JN05 has not been composed or scored.

Harness (code/th_works_j; reads and runs only; shared files append-only). mkset.py builds a set json as a copy of JN04RM with overrides (jnrule config, cde state rule, hooks/hooklist, mtab table, zact). run_one.sh runs ONE set per job through the IJK driver (jbjobs, JointRep, ROLLFIX1 patched engine) with one worker, gated on MemAvail of at least 62 GB sustained 60 s and aborting under 41 GB. score_w.py scores any runs_rf cell against the live panel base reference LPB_BASE on L1M, L3M, L6M, HOLD, PRE and X', with the bi-weekly walk-forward over the 43 contiguous months and the rule 2a label. A month of the full stack takes about four minutes on one worker, so a full 43-month set is about three hours on one worker. The new composition names carry the prefix JN05W because the name JN05 is already taken by an old IJK first-order stack (set json JN05.json, HOLD runs only).

Reproduction: JN04RM re-run through this harness as the set JN05W_REF (identical config, one set per job) is identical trade by trade to the stored JN04RM in 202610 (858 trades, net 20,778.50) and 202608 (695 trades, net 38,461.34); see D1. The scorer also reproduces the stored lpb_rm_scores.csv for JN04RM to the digit (L6M cut +46.0, mean 19,862 against LPB_BASE 21,495; HOLD +7.7; PRE +32.9; X' +47.7; WF 90%).

Plan once winners land. Candidate layers per family: dial layers from DS3_WORKS_A (performance gates, volatility dial, exposure caps), regime-conditional exits from DS3_WORKS_B, P7 re-entry and Asia rules from DS3_WORKS_C, plus the existing leads JX01 to JX07 (being re-run one set per job by SZ-CDE) and the C2 regime stacks. Each layer enters as top-K from its own page, then coordinate descent in the exact engine on top of JN04RM, one set per job, L6M then HOLD then PRE then X', then the 43-month walk-forward. Rule 2a floors apply: PRE mean not worse than the 25% floor, recents-first ranking. The two live weeks (frozen week 11-01..05 only; 11-09..11 live data is not on the box) are replayed through the engine replay (code/th_r13) with the JN05W rules at the end.

Not yet available: JN05W composition, live-week replay, REFIT 2026-11-22 preview with JN05W. For reference the existing first-order REFIT dry run (DS3_JOINT_2.md C3) does not select the four JN04 layers on the 26-week training window.


## A. Generalise the dials (W-A)

(DS3_WORKS_A.md has not landed yet at 2026-11-11T13:38:44Z)


## B. Regime-conditional exits (W-B)

(DS3_WORKS_B.md has not landed yet at 2026-11-11T13:38:44Z)


## C. P7 anatomy (W-C)

(DS3_WORKS_C.md has not landed yet at 2026-11-11T13:38:44Z)
