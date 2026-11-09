# EXH_S2NULL - engine-level causal placebo for the Stage 2 candidates (auto 2026-11-09 16:47:30Z)
Method: autopilot/EXH_S2NULL_PREREG.md (null v2 inside the replica engine cascade: rand / shuf / shift-later-only; equal expected fire count per book-month). Statistic: book-scope weekly USD at live lots, net 4.84/contract (outputs/FEES.md); carrying week dropped for means. dd cut = never-cut maxDD minus rule maxDD (higher better); mean delta = rule minus never-cut weekly mean. p = (1+#placebo>=real)/(N+1); pmax = largest of the per-mode p (house convention). No PASS claim is made.
CAVEAT (lead 14:00Z): the live NQ book contained ES/RTY depth levels; the 92 live cuts and the 10 v1.5 state cuts of the 11-08/09 night (1 H7, 9 M7) are corrupted-book / bug exits and are NOT used here as truth or acceptance. Any live-week number quoted below (FAILS-LIVE-WEEK labels come from the Stage 1/2 ledger, the frozen live file ending 11-05) carries that caveat. This study uses no live-week data.

| set | book | window | draws | maxDD never | maxDD rule | dd cut | p(dd cut) pooled | pmax(modes) | mean delta/wk | p(mean) pooled | pmax(mean) | placebo median dd cut | placebo median mean | real fires | placebo fires (mean) | draws by mode |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| exla_pb1 | M7 | L6M | 8 | 48019 | 30434 | 17585 | 0.111 | 0.333 | 615 | 0.333 | 1.000 | 8854 | 14 | 303 | 253 | {'rand': 3, 'shift': 2, 'shuf': 3} |
| exla_pb1 | H7 | L6M | 8 | 16242 | 7348 | 8893 | 0.111 | 0.333 | 286 | 0.111 | 0.333 | 1143 | -502 | 54 | 44 | {'rand': 3, 'shift': 2, 'shuf': 3} |
| exla_pb1 | O7 | L6M | 8 | 6958 | 5668 | 1290 | 0.333 | 0.750 | 70 | 0.667 | 1.000 | 919 | 76 | 38 | 29 | {'rand': 3, 'shift': 2, 'shuf': 3} |
| phi_pb | P7 | L6M | 3 | 203542 | 191674 | 11868 | 1.000 | 1.000 | 236 | 1.000 | 1.000 | 17127 | 1215 | 15 | 4 | {'rand': 1, 'shift': 1, 'shuf': 1} |
| phi_pb | O7 | L6M | 3 | 6958 | 4210 | 2748 | 0.250 | 0.500 | 251 | 0.250 | 0.500 | 2449 | 80 | 58 | 48 | {'rand': 1, 'shift': 1, 'shuf': 1} |
| phi_thick | K7 | L6M | 8 | 35969 | 20056 | 15913 | 0.222 | 0.500 | 656 | 0.222 | 0.500 | 7722 | -260 | 440 | 367 | {'rand': 3, 'shift': 2, 'shuf': 3} |
| phi_thick | P7 | L6M | 8 | 203542 | 186789 | 16753 | 0.111 | 0.333 | 295 | 0.333 | 0.750 | -169 | 81 | 15 | 3 | {'rand': 3, 'shift': 2, 'shuf': 3} |
| bc_c_uniform | K7 | L6M | 3 | 35969 | 25881 | 10088 | 0.500 | 1.000 | 305 | 0.500 | 1.000 | 9195 | 54 | 299 | 244 | {'rand': 1, 'shift': 1, 'shuf': 1} |

## Label effect (rule: placebo p <= 0.10 on the L6M dd cut is necessary for ENTER; otherwise the label stays as in EXH_STAGE2.md)
- exla_pb1 M7: ledger label CANDIDATE-DD; L6M dd cut 17585 (placebo median 8854), p pooled 0.111 / pmax 0.333 over 8 draws -> NOT TESTABLE YET: 8 draws cannot reach p <= 0.10 (need >= 9); label unchanged
- exla_pb1 H7: ledger label CANDIDATE-DD; L6M dd cut 8893 (placebo median 1143), p pooled 0.111 / pmax 0.333 over 8 draws -> NOT TESTABLE YET: 8 draws cannot reach p <= 0.10 (need >= 9); label unchanged
- exla_pb1 O7: ledger label CANDIDATE-DD; L6M dd cut 1290 (placebo median 919), p pooled 0.333 / pmax 0.750 over 8 draws -> NOT TESTABLE YET: 8 draws cannot reach p <= 0.10 (need >= 9); label unchanged
- phi_pb P7: ledger label CANDIDATE-DD FAILS-LIVE-WEEK; L6M dd cut 11868 (placebo median 17127), p pooled 1.000 / pmax 1.000 over 3 draws -> NOT TESTABLE YET: 3 draws cannot reach p <= 0.10 (need >= 9); label unchanged
- phi_pb O7: ledger label CANDIDATE-DD; L6M dd cut 2748 (placebo median 2449), p pooled 0.250 / pmax 0.500 over 3 draws -> NOT TESTABLE YET: 3 draws cannot reach p <= 0.10 (need >= 9); label unchanged
- phi_thick K7: ledger label (not listed in Stage 2 table: K7 phi_thick); L6M dd cut 15913 (placebo median 7722), p pooled 0.222 / pmax 0.500 over 8 draws -> NOT TESTABLE YET: 8 draws cannot reach p <= 0.10 (need >= 9); label unchanged
- phi_thick P7: ledger label CANDIDATE-DD; L6M dd cut 16753 (placebo median -169), p pooled 0.111 / pmax 0.333 over 8 draws -> NOT TESTABLE YET: 8 draws cannot reach p <= 0.10 (need >= 9); label unchanged
- bc_c_uniform K7: ledger label CANDIDATE-DD; L6M dd cut 10088 (placebo median 9195), p pooled 0.500 / pmax 1.000 over 3 draws -> NOT TESTABLE YET: 3 draws cannot reach p <= 0.10 (need >= 9); label unchanged

## Status at hand-back (2026-11-09 ~16:50Z; paused on lead order, no new workers launched)
- Draws (L6M months only; PRE not run for any set): exla_pb1 8, phi_thick 8, phi_pb 3, bc_c_uniform 3. Modes in the 8-draw sets: rand 3, shuf 3, shift 2. With 8 draws the smallest possible p is 0.111, so no candidate can reach p <= 0.10 yet; all labels unchanged.
- Engine determinism: exla_pb1 202610 re-run twice (sets s2null_deta/detb): trades.parquet byte-identical to each other and to the original run (758 trades, gross -31045.89). Holds.
- Reading at N=8: exla_pb1 M7 and H7 and phi_thick P7 reach p 0.111 (best possible) on the L6M dd cut pooled, but pmax over modes is 0.33 (2-3 draws per mode); phi_thick K7 p 0.22; exla_pb1 O7 p 0.33; phi_pb P7 is below placebo median (drop); phi_pb O7 and bc_c_uniform K7 have 3 draws only.
- Placebo fire counts are below real for P7 (3-4 vs 15): the causal bracket-first rule drops decisions after the bracket. Mean-delta p values: exla_pb1 H7 0.111, M7 0.333, phi_thick K7 0.22, P7 0.33.
- Resume: python3 code/th_exh/s2null_launch.py with env S2N_SETS=exla_pb1,phi_thick (args: maxdraw premax workers, e.g. 14 0 1), then s2null_score.py and s2null_report.py (writes EXH_S2NULL.md.new). Results JSON /mnt/l2/l2vast/_th_exh/stage2/s2null_results.json. PRE placebo needs about 17 extra months per draw-set.
