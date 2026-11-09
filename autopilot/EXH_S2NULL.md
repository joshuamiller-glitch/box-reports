# EXH_S2NULL - engine-level causal placebo for the Stage 2 candidates (auto 2026-11-09 14:46:48Z)
Method: autopilot/EXH_S2NULL_PREREG.md (null v2 inside the replica engine cascade: rand / shuf / shift-later-only; equal expected fire count per book-month). Statistic: book-scope weekly USD at live lots, net 4.84/contract (outputs/FEES.md); carrying week dropped for means. dd cut = never-cut maxDD minus rule maxDD (higher better); mean delta = rule minus never-cut weekly mean. p = (1+#placebo>=real)/(N+1); pmax = largest of the per-mode p (house convention). No PASS claim is made.
CAVEAT (lead 14:00Z): the live NQ book contained ES/RTY depth levels; the 92 live cuts and the 10 v1.5 state cuts of the 11-08/09 night (1 H7, 9 M7) are corrupted-book / bug exits and are NOT used here as truth or acceptance. Any live-week number quoted below (FAILS-LIVE-WEEK labels come from the Stage 1/2 ledger, the frozen live file ending 11-05) carries that caveat. This study uses no live-week data.

| set | book | window | draws | maxDD never | maxDD rule | dd cut | p(dd cut) pooled | pmax(modes) | mean delta/wk | p(mean) pooled | pmax(mean) | placebo median dd cut | placebo median mean | real fires | placebo fires (mean) | draws by mode |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| exla_pb1 | M7 | L6M | 2 | 48019 | 30434 | 17585 | 0.333 | 0.500 | 615 | 0.333 | 0.500 | 7852 | 414 | 303 | 270 | {'rand': 1, 'shuf': 1} |
| exla_pb1 | H7 | L6M | 2 | 16242 | 7348 | 8893 | 0.333 | 0.500 | 286 | 0.333 | 0.500 | -325 | -682 | 54 | 44 | {'rand': 1, 'shuf': 1} |
| exla_pb1 | O7 | L6M | 2 | 6958 | 5668 | 1290 | 0.667 | 1.000 | 70 | 0.667 | 1.000 | 391 | -47 | 38 | 34 | {'rand': 1, 'shuf': 1} |
| phi_pb | P7 | L6M | 3 | 203542 | 191674 | 11868 | 1.000 | 1.000 | 236 | 1.000 | 1.000 | 17127 | 1215 | 15 | 4 | {'rand': 1, 'shift': 1, 'shuf': 1} |
| phi_pb | O7 | L6M | 3 | 6958 | 4210 | 2748 | 0.250 | 0.500 | 251 | 0.250 | 0.500 | 2449 | 80 | 58 | 48 | {'rand': 1, 'shift': 1, 'shuf': 1} |
| phi_thick | K7 | L6M | 3 | 35969 | 20056 | 15913 | 0.250 | 0.500 | 656 | 0.250 | 0.500 | 1358 | -1047 | 440 | 358 | {'rand': 1, 'shift': 1, 'shuf': 1} |
| phi_thick | P7 | L6M | 3 | 203542 | 186789 | 16753 | 0.250 | 0.500 | 295 | 0.500 | 1.000 | 4883 | 63 | 15 | 4 | {'rand': 1, 'shift': 1, 'shuf': 1} |
| bc_c_uniform | K7 | L6M | 2 | 35969 | 25881 | 10088 | 0.333 | 0.500 | 305 | 0.333 | 0.500 | 7307 | 53 | 299 | 288 | {'rand': 1, 'shuf': 1} |

## Label effect (rule: placebo p <= 0.10 on the L6M dd cut is necessary for ENTER; otherwise the label stays as in EXH_STAGE2.md)
- exla_pb1 M7: ledger label CANDIDATE-DD; L6M dd cut 17585 (placebo median 7852), p pooled 0.333 / pmax 0.500 over 2 draws -> NOT TESTABLE YET: 2 draws cannot reach p <= 0.10 (need >= 9); label unchanged
- exla_pb1 H7: ledger label CANDIDATE-DD; L6M dd cut 8893 (placebo median -325), p pooled 0.333 / pmax 0.500 over 2 draws -> NOT TESTABLE YET: 2 draws cannot reach p <= 0.10 (need >= 9); label unchanged
- exla_pb1 O7: ledger label CANDIDATE-DD; L6M dd cut 1290 (placebo median 391), p pooled 0.667 / pmax 1.000 over 2 draws -> NOT TESTABLE YET: 2 draws cannot reach p <= 0.10 (need >= 9); label unchanged
- phi_pb P7: ledger label CANDIDATE-DD FAILS-LIVE-WEEK; L6M dd cut 11868 (placebo median 17127), p pooled 1.000 / pmax 1.000 over 3 draws -> NOT TESTABLE YET: 3 draws cannot reach p <= 0.10 (need >= 9); label unchanged
- phi_pb O7: ledger label CANDIDATE-DD; L6M dd cut 2748 (placebo median 2449), p pooled 0.250 / pmax 0.500 over 3 draws -> NOT TESTABLE YET: 3 draws cannot reach p <= 0.10 (need >= 9); label unchanged
- phi_thick K7: ledger label (not listed in Stage 2 table: K7 phi_thick); L6M dd cut 15913 (placebo median 1358), p pooled 0.250 / pmax 0.500 over 3 draws -> NOT TESTABLE YET: 3 draws cannot reach p <= 0.10 (need >= 9); label unchanged
- phi_thick P7: ledger label CANDIDATE-DD; L6M dd cut 16753 (placebo median 4883), p pooled 0.250 / pmax 0.500 over 3 draws -> NOT TESTABLE YET: 3 draws cannot reach p <= 0.10 (need >= 9); label unchanged
- bc_c_uniform K7: ledger label CANDIDATE-DD; L6M dd cut 10088 (placebo median 7307), p pooled 0.333 / pmax 0.500 over 2 draws -> NOT TESTABLE YET: 2 draws cannot reach p <= 0.10 (need >= 9); label unchanged
