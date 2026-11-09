# DS3_TH_EXHAUST_FINAL - two-sided per-book exit policy, drawdown first   **[DRAFT SKELETON - compiled 2026-11-09 09:38Z]**
Label: state base, universe U2 (U2 = full S1b tick-close never-cut, 43 months + live-week entries); entry match to the live week below .85: PRE-PROOF. USD per ISO week at live lots net of 4.84/contract; windows as of 2026-11-09.

## Box-confirmation items for v1.5 fidelity
v1.5 NOT VERIFIED: the v1.5 source is absent from the box (requested from the user); no match with v1.5 is claimed for any item. What follows is the treatment of the state build used by every number on this page.
1. A level present at s-1 and absent at s: cancelled size = max(0, size(s-1) - size(s) - traded at that price in (s-1, s]); absent at s counts as size 0 when the price is inside or better than the visible top-10 range of row s; it is IGNORED when it fell outside the visible top 10 (worse than the 10th level of a full 10-level book; about 64 M levels per side over the history, ~0.8 per side per second, mostly price moves). Box treatment (state build) + v1.5 NOT VERIFIED.
2. Seconds with no feed event: one row per session second, book carried forward, zero cancels and zero prints. Box treatment (state build) + v1.5 NOT VERIFIED.
3. newMae tie rule: a tie with the running adverse extreme counts as new (DS3_TH_STATE section 2). Box treatment (state build) + v1.5 NOT VERIFIED.
Null audit: placebo version 2 (causal, leak-tested; EXH_API section 9). Placebo p of cells scored with the version-1 (leaky) null were recomputed or set to NaN (shown as nan, treated as 1.0 by the labels).
Evidence level: stage S1 rows are first-order (each trade alone on its stored path, bracket exits at level, 1-s decision latency, 0.80 pt market-exit cost); rows marked S2 went through the replica engine cascade (re-entries, locks, stack gates). Entry match to the live week is below .85, so the page is PRE-PROOF.


## Reference rows (live v1.5 / never-cut / plain 60/60)
| row | book | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S1b-COMB (live v1.5 seven state-cut lines, replica) | ALL | 11,588 | 35,818 | 20,608 | 23,721 | 15,294 | 9,807 | 13,959 | 1,679 | 82,873 | 144,002 | 190,560 |
| engine never-cut (= plain 60/60 in the replica, ENTRY_MATCH finding) | ALL | -14,622 | 23,859 | 8,518 | 13,389 | 9,695 | 4,729 | 12,875 | 1,870 | 191,045 | 130,824 | -63,404 |
| S1b-COMB (live v1.5 seven state-cut lines, replica) | K7 | 7,873 | 7,336 | 3,232 | 3,429 | 1,994 | 3,113 | 2,723 | 183 | 41,849 | 23,073 | -20,339 |
| engine never-cut (= plain 60/60 in the replica, ENTRY_MATCH finding) | K7 | 662 | 3,876 | 1,286 | 2,735 | 2,025 | 2,174 | 3,000 | 647 | 35,969 | 22,188 | -20,829 |
| S1b-COMB (live v1.5 seven state-cut lines, replica) | P7 | 5,700 | 21,351 | 15,192 | 14,220 | 9,899 | 4,615 | 6,054 | -143 | 96,490 | 106,914 | 53,844 |
| engine never-cut (= plain 60/60 in the replica, ENTRY_MATCH finding) | P7 | -8,308 | 13,521 | 6,656 | 4,434 | 3,922 | 328 | 4,982 | -581 | 203,542 | 122,169 | -181,468 |
| S1b-COMB (live v1.5 seven state-cut lines, replica) | M7 | 40 | 2,355 | -568 | -1,108 | -840 | -160 | 547 | 86 | 46,547 | 25,812 | -64,633 |
| engine never-cut (= plain 60/60 in the replica, ENTRY_MATCH finding) | M7 | -2,372 | 1,938 | -878 | -738 | -367 | 326 | 12 | 224 | 48,019 | 44,205 | -73,536 |
| S1b-COMB (live v1.5 seven state-cut lines, replica) | U7 | -3,377 | 2,510 | 1,393 | 3,493 | 2,197 | 3,362 | 1,481 | 1,112 | 16,419 | 39,155 | 8,146 |
| engine never-cut (= plain 60/60 in the replica, ENTRY_MATCH finding) | U7 | -3,891 | 2,598 | 1,466 | 3,588 | 2,313 | 2,607 | 1,431 | 1,117 | 17,816 | 39,542 | 17,704 |
| S1b-COMB (live v1.5 seven state-cut lines, replica) | A7 | -1,287 | 202 | 148 | 661 | 704 | 17 | 954 | 268 | 8,518 | 7,325 | -11,915 |
| engine never-cut (= plain 60/60 in the replica, ENTRY_MATCH finding) | A7 | -405 | 629 | 430 | 987 | 838 | 340 | 988 | 267 | 9,361 | 8,625 | -7,321 |
| S1b-COMB (live v1.5 seven state-cut lines, replica) | H7 | 3,186 | 1,936 | 1,001 | 2,757 | 665 | -1,000 | 1,583 | 320 | 8,818 | 19,256 | 11,007 |
| engine never-cut (= plain 60/60 in the replica, ENTRY_MATCH finding) | H7 | 928 | 1,595 | -290 | 2,330 | 407 | -989 | 1,816 | 270 | 16,242 | 18,436 | -13,688 |
| S1b-COMB (live v1.5 seven state-cut lines, replica) | O7 | -988 | -93 | 63 | 199 | 640 | -140 | 617 | -147 | 6,656 | 4,532 | -8,247 |
| engine never-cut (= plain 60/60 in the replica, ENTRY_MATCH finding) | O7 | -1,236 | -299 | -151 | 52 | 557 | -58 | 647 | -73 | 6,958 | 4,797 | -11,023 |

Plain 60/60: in the replica the plain 60/60 run is trade-for-trade identical to the never-cut run (ENTRY_MATCH, S1 comparison); the S1b PLAIN6060 rebuild exists for part of the months only, so the never-cut row stands for it. The live v1.5 row is the S1b-COMB replica; the live-week actuals are in the held-out columns.

## Per-book two-sided policy (candidate per side: best label tier, then drawdown-first; survivors = CANDIDATE-DD, rec-ok, plc-ok, not FAILS-LIVE-WEEK; otherwise NO CUT / book default)
D7 v1.5 policy grammar used here: `loss <book> <session|*> <conds> cut` and `profit <book> <session|*> <conds> take|scale`, conds over pct mins secs_ext dd recov vel30 eff120 delta60 imb5 imb10 wall_* pulled_mult ice_against ahead_rel tot_rel; state-cut extensions named in DS3_TH_STATE section 2: win= (pulled/newMae window in seconds), persist= (consecutive seconds the whole condition holds), armlots= (lots-scaled arm: V1 clip(ARM*sqrt(4/lots),15,50) / V2 clip(ARM*sqrt(lots/4),15,50)); pct is relative to the book stop distance (60 pt; O7 40).

| book | side | technique | params | L6M maxDD w/wo | PRE maxDD w/wo | L6M mean | PRE mean | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|
| K7 | loss | LBC_adv_best_move | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "adv_best_move", "m | 8,636 / 20,902 | 23,900 / 26,707 | 1,123 | -1,202 | 126 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| K7 | profit | J3_statescale | {"a": 0.2, "f": "ahead_rel_slow", "rest": "trail", "s": 3, "th": 1.5,  | 8,893 / 20,902 | 23,892 / 26,707 | 666 | -673 | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| P7 | loss | D3_pullback@after30 | {"X": 20, "ctx": "after30", "pb": 40} | 38,077 / 133,887 | 57,033 / 109,442 | 3,938 | -5,504 | -3,790 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| P7 | profit | H_gated | {"P": [1.0, 2.0, 2.0, 1.0, 0.7, 1.0], "arm": 0.7, "feat": "tot_rel_fas | 71,485 / 133,887 | 107,157 / 109,442 | 655 | -2,499 | -1,317 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| M7 | loss | F3_stop_extreme | {"X": 10, "k": 0} | 13,450 / 44,425 | 45,329 / 50,321 | 737 | -812 | -1,985 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| M7 | profit | I_decay | {"P": [9.0, 30.0, 5.0, 1.0, 0.3], "X0": 30, "Xmin": 5, "arm": 0.3, "ra | 21,793 / 44,425 | 52,180 / 50,321 | 383 | -673 | 3,872 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| U7 | loss | LBC_ice_ag_w10 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "ice_ag_w10", "mode | 6,061 / 21,561 | 35,033 / 42,226 | 809 | -624 | 2,829 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| U7 | profit | H_pcthour | {"P": [3.0, 0.3, 120.0, 510.0], "pct": 0.3, "window": "ldn"} | 8,700 / 21,561 | 42,735 / 42,226 | 153 | -1,294 | 7,540 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A7 | loss | D3_pullback | {"X": 20, "pb": 50} | 4,760 / 12,461 | 5,445 / 6,089 | 511 | -146 | -1,314 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A7 | profit | H_pcthour | {"P": [3.0, 0.4, 1080.0, 120.0], "pct": 0.4, "window": "asia"} | 3,268 / 12,461 | 6,089 / 6,089 | 427 | -289 | 665 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H7 | loss | LBC_sweep8_w10 | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w10", "mode | 4,988 / 15,477 | 15,783 / 20,667 | 1,281 | -138 | 394 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| H7 | profit | H_mom | {"P": [1.0, 9.0, 0.0, 1.0, 0.25, -1.0], "arm": 0.25, "feat": "vel30<=" | 5,961 / 15,477 | 10,161 / 20,667 | 137 | -975 | 2,524 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| O7 | loss | LBC_dtot8_rel_w15 | {"arm": 0.15, "arm_kind": "pct", "dir": -1, "feat": "dtot8_rel_w15", " | 2,725 / 7,469 | 5,195 / 5,102 | 325 | -395 | 940 | S1 | CANDIDATE-DD [rec-ok wf-ok plc-ok exposure] |
| O7 | profit | I_step | {"P": [7.0, 10.0, 1.0], "lag": 1, "step": 10} | 4,420 / 7,469 | 4,995 / 5,102 | 215 | -498 | 1,167 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

## Policy lines in the v1.5 grammar (survivors live-readable; non-survivors and untranslatable cells commented with `#!`/`#`)
```
# loss K7 * LBC_adv_best_move {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "adv_best_move", "mode": "latch", "mont   # NEEDS: feature/field not in the v1.5 loss grammar
# profit K7 * J3_statescale {"a": 0.2, "f": "ahead_rel_slow", "rest": "trail", "s": 3, "th": 1.5, "x": 10}   # NEEDS: exit action/field not in the v1.5 profit grammar (take at pct only)
# loss P7 * D3_pullback@after30 {"X": 20, "ctx": "after30", "pb": 40}   # NEEDS: feature/field not in the v1.5 loss grammar
# profit P7 * H_gated {"P": [1.0, 2.0, 2.0, 1.0, 0.7, 1.0], "arm": 0.7, "feat": "tot_rel_fast", "secs": 1, "thr"   # NEEDS: exit action/field not in the v1.5 profit grammar (take at pct only)
# loss M7 * F3_stop_extreme {"X": 10, "k": 0}   # NEEDS: feature/field not in the v1.5 loss grammar
# profit M7 * I_decay {"P": [9.0, 30.0, 5.0, 1.0, 0.3], "X0": 30, "Xmin": 5, "arm": 0.3, "rate": 1}   # NEEDS: exit action/field not in the v1.5 profit grammar (take at pct only)
# loss U7 * LBC_ice_ag_w10 {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "ice_ag_w10", "mode": "cur", "months":    # NEEDS: feature/field not in the v1.5 loss grammar
# profit U7 * H_pcthour {"P": [3.0, 0.3, 120.0, 510.0], "pct": 0.3, "window": "ldn"}   # NEEDS: exit action/field not in the v1.5 profit grammar (take at pct only)
# loss A7 * D3_pullback {"X": 20, "pb": 50}   # NEEDS: feature/field not in the v1.5 loss grammar
# profit A7 * H_pcthour {"P": [3.0, 0.4, 1080.0, 120.0], "pct": 0.4, "window": "asia"}   # NEEDS: exit action/field not in the v1.5 profit grammar (take at pct only)
# loss H7 * LBC_sweep8_w10 {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w10", "mode": "latch", "months"   # NEEDS: feature/field not in the v1.5 loss grammar
# profit H7 * H_mom {"P": [1.0, 9.0, 0.0, 1.0, 0.25, -1.0], "arm": 0.25, "feat": "vel30<=", "secs": 1, "thr":    # NEEDS: exit action/field not in the v1.5 profit grammar (take at pct only)
# loss O7 * LBC_dtot8_rel_w15 {"arm": 0.15, "arm_kind": "pct", "dir": -1, "feat": "dtot8_rel_w15", "mode": "latch", "mon   # NEEDS: feature/field not in the v1.5 loss grammar
# profit O7 * I_step {"P": [7.0, 10.0, 1.0], "lag": 1, "step": 10}   # NEEDS: exit action/field not in the v1.5 profit grammar (take at pct only)
```

## Engine (Stage 2) evidence
See autopilot/EXH_STAGE2.md (per completed set and per book: engine vs never-cut and vs S1b-COMB, live week, Stage 1 gain kept). Strict engine survivors listed there are the only cells with cascade evidence.

## Fields the v1.5 grammar still lacks (for v1.6)
- state-cut extensions: pulled_mult as the exact state quantity with a per-rule window (win=), persist= (consecutive seconds), armlots= (lots-scaled arm), entry_session (the grammar matches the CURRENT session; scored scope is the ENTRY session), 1-s evaluation with 1 s decision latency and the 0.80 pt market-exit cost.
- loss technique D3_pullback: feature ?
- loss technique D3_pullback@after30: feature ?
- loss technique F3_stop_extreme: feature ?
- loss technique LBC_adv_best_move: feature adv_best_move
- loss technique LBC_dtot8_rel_w15: feature dtot8_rel_w15
- loss technique LBC_ice_ag_w10: feature ice_ag_w10
- loss technique LBC_sweep8_w10: feature sweep8_w10
- profit technique H_gated: {"P": [1.0, 2.0, 2.0, 1.0, 0.7, 1.0], "arm": 0.7, "feat": "tot_rel_fas
- profit technique H_mom: {"P": [1.0, 9.0, 0.0, 1.0, 0.25, -1.0], "arm": 0.25, "feat": "vel30<="
- profit technique H_pcthour: {"P": [3.0, 0.3, 120.0, 510.0], "pct": 0.3, "window": "ldn"}
- profit technique H_pcthour: {"P": [3.0, 0.4, 1080.0, 120.0], "pct": 0.4, "window": "asia"}
- profit technique I_decay: {"P": [9.0, 30.0, 5.0, 1.0, 0.3], "X0": 30, "Xmin": 5, "arm": 0.3, "ra
- profit technique I_step: {"P": [7.0, 10.0, 1.0], "lag": 1, "step": 10}
- profit technique J3_statescale: {"a": 0.2, "f": "ahead_rel_slow", "rest": "trail", "s": 3, "th": 1.5, 

## Method and nulls
Recents method L1M..L6M then HOLD/MID/PRE/X'; placebos v2 (causal, leak-tested), Westfall-Young family null (common permutations), purged monthly walk-forward, held-out live week; see autopilot/EXH_API.md sections 9-13 and DS3_TH_EXHAUST.md for the ranked tables. Family pages: EXH_*.md.

## Family sections (state at compile)
| family | file | status | last written |
|---|---|---|---|
| A (EX-LA) | EXH_A.md | in | 09:38Z |
| B/C (EX-LBC) | EXH_BC.md | in | 07:44Z |
| D/E/F (EX-LDEF) | EXH_DEF.md | in | 09:31Z |
| G (EX-LG) | EXH_G.md | in | 09:21Z |
| H/I (EX-PHI) | EXH_HI.md | in | 09:13Z |
| J/K/L (EX-PJKL) | EXH_JKL.md | in | 07:32Z |

## wf-ok flags: what they mean
The wf flag on a candidate row is the TECHNIQUE-level walk-forward (picking among the cells of that one technique on trailing 26 weeks, applied to the next month; wf-ok = total delta >= 0 and WF maxDD within +5% of never-cut). It is a weak test: e.g. O7 loss LBC_dtot8_rel_w15 (13 cells) is wf-ok with +1,917 USD over 35 test months, but its WF maxDD equals the never-cut maxDD (7,469), i.e. the picks did not lower the drawdown, and the global picking procedure for O7 loss (6,272 cells) is wf-FAIL (-44,366). Read wf-ok as not-negative, not as out-of-sample drawdown evidence. No cell is ENTER.