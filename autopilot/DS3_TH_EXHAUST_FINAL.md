# DS3_TH_EXHAUST_FINAL - two-sided per-book exit policy, drawdown first
Label: state base, universe U2 (U2 = full S1b tick-close never-cut, 43 months + live-week entries); entry match to the live week below .85: PRE-PROOF. USD per ISO week at live lots net of 4.84/contract; windows as of 2026-11-09.

## Box-confirmation items for v1.5 fidelity
v1.5 NOT VERIFIED: the v1.5 source is absent from the box (requested from the user); no match with v1.5 is claimed for any item. What follows is the treatment of the state build used by every number on this page.
1. A level present at s-1 and absent at s: cancelled size = max(0, size(s-1) - size(s) - traded at that price in (s-1, s]); absent at s counts as size 0 when the price is inside or better than the visible top-10 range of row s; it is IGNORED when it fell outside the visible top 10 (worse than the 10th level of a full 10-level book; about 64 M levels per side over the history, ~0.8 per side per second, mostly price moves). Box treatment (state build) + v1.5 NOT VERIFIED.
2. Seconds with no feed event: one row per session second, book carried forward, zero cancels and zero prints. Box treatment (state build) + v1.5 NOT VERIFIED.
3. newMae tie rule: a tie with the running adverse extreme counts as new (DS3_TH_STATE section 2). Box treatment (state build) + v1.5 NOT VERIFIED.
Null audit: placebo version 2 (causal, leak-tested; EXH_API section 9). Placebo p of cells scored with the version-1 (leaky) null were recomputed or set to NaN (shown as nan, treated as 1.0 by the labels).
Evidence level: stage S1 rows are first-order (each trade alone on its stored path, bracket exits at level, 1-s decision latency, 0.80 pt market-exit cost); rows marked S2 went through the replica engine cascade (re-entries, locks, stack gates). Entry match to the live week is below .85, so the page is PRE-PROOF.


## Reference rows (live v1.5 / never-cut / plain 60/60)
Levels: USD per ISO week, net of 4.84/contract, with the single largest-|delta| week (the carrying week) dropped from the MEANS; they differ from the plain-mean levels in TH_STATE_BASE_S1.md. maxDD and worst-20 are on all weeks.

| row | book | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| never-cut (NOCUT, = plain 60/60 in the replica) | ALL | -14,622 | 23,859 | 8,518 | 13,389 | 9,695 | 4,729 | 12,875 | 1,870 | 191,045 | 130,824 | -63,404 |
| HOLD-old (old live L2 cut) | ALL | 783 | 38,368 | 13,026 | 20,499 | 13,754 | 9,964 | 7,588 | 5,260 | 132,342 | 171,684 | 25,602 |
| S1b-COMB (live v1.5 seven state-cut lines) | ALL | -1,799 | 18,811 | 14,975 | 26,560 | 17,412 | 17,246 | 13,203 | 2,431 | 82,873 | 144,002 | 137,012 |
| S1b-UNIF (one cell for all books) | ALL | -15,356 | 28,860 | 3,866 | 14,267 | 11,192 | 10,913 | 13,197 | 2,001 | 185,610 | 137,647 | -102,473 |
| S1b-LIVE (30/30/5/1 cell on state) | ALL | -10,396 | 21,616 | 3,175 | 19,836 | 12,779 | 8,613 | 12,453 | 1,952 | 196,906 | 129,487 | -44,000 |
| never-cut (NOCUT, = plain 60/60 in the replica) | K7 | 662 | 3,876 | 1,286 | 2,735 | 2,025 | 2,174 | 3,000 | 647 | 35,969 | 22,188 | -20,829 |
| HOLD-old (old live L2 cut) | K7 | 4,376 | 2,717 | -206 | 2,315 | 1,294 | 214 | 1,789 | 1,091 | 31,791 | 43,726 | -39,563 |
| S1b-COMB (live v1.5 seven state-cut lines) | K7 | 4,426 | 6,727 | 2,383 | 2,681 | 1,684 | 4,950 | 2,926 | 396 | 41,849 | 23,073 | -30,965 |
| S1b-UNIF (one cell for all books) | K7 | 4,869 | 4,732 | 841 | 2,377 | 2,077 | 5,198 | 3,051 | 922 | 18,987 | 18,921 | -18,865 |
| S1b-LIVE (30/30/5/1 cell on state) | K7 | 323 | 3,107 | 984 | 3,566 | 1,545 | 2,382 | 3,109 | 592 | 37,425 | 21,298 | -13,916 |
| never-cut (NOCUT, = plain 60/60 in the replica) | P7 | -8,308 | 13,521 | 6,656 | 4,434 | 3,922 | 328 | 4,982 | -581 | 203,542 | 122,169 | -181,468 |
| HOLD-old (old live L2 cut) | P7 | -529 | 10,079 | 7,585 | 12,182 | 9,542 | 7,055 | 2,118 | 1,229 | 128,194 | 165,749 | -48,297 |
| S1b-COMB (live v1.5 seven state-cut lines) | P7 | -2,928 | 17,036 | 9,346 | 16,263 | 11,963 | 4,891 | 5,662 | 395 | 96,490 | 106,914 | 19,331 |
| S1b-UNIF (one cell for all books) | P7 | -12,449 | 11,933 | 1,519 | 5,912 | 5,167 | 5,823 | 5,706 | 200 | 196,293 | 111,170 | -154,283 |
| S1b-LIVE (30/30/5/1 cell on state) | P7 | -4,096 | 14,116 | 1,402 | 9,368 | 6,288 | 6,012 | 4,581 | -667 | 217,740 | 111,865 | -161,846 |
| never-cut (NOCUT, = plain 60/60 in the replica) | M7 | -2,372 | 1,938 | -878 | -738 | -367 | 326 | 12 | 224 | 48,019 | 44,205 | -73,536 |
| HOLD-old (old live L2 cut) | M7 | -1,737 | 2,836 | 29 | -1,349 | -793 | 2,150 | -180 | 140 | 63,275 | 41,730 | -93,690 |
| S1b-COMB (live v1.5 seven state-cut lines) | M7 | -1,305 | 412 | -1,678 | -1,150 | -758 | 1,825 | 602 | 248 | 46,547 | 25,812 | -69,923 |
| S1b-UNIF (one cell for all books) | M7 | -2,191 | 289 | -581 | -1,128 | -435 | 1,065 | 153 | 201 | 60,698 | 39,327 | -83,139 |
| S1b-LIVE (30/30/5/1 cell on state) | M7 | -2,438 | 1,876 | -606 | -84 | -12 | 1,086 | 203 | 65 | 45,180 | 46,357 | -75,226 |
| never-cut (NOCUT, = plain 60/60 in the replica) | U7 | -3,891 | 2,598 | 1,466 | 3,588 | 2,313 | 2,607 | 1,431 | 1,117 | 17,816 | 39,542 | 17,704 |
| HOLD-old (old live L2 cut) | U7 | -2,971 | 1,682 | 2,269 | 4,394 | 2,776 | 4,618 | 765 | 1,296 | 16,061 | 56,548 | 25,628 |
| S1b-COMB (live v1.5 seven state-cut lines) | U7 | -3,092 | 1,040 | 1,031 | 3,539 | 2,299 | 1,620 | 1,664 | 1,053 | 15,278 | 39,155 | 9,288 |
| S1b-UNIF (one cell for all books) | U7 | -4,310 | 2,300 | 1,233 | 3,184 | 1,789 | 2,053 | 1,697 | 1,273 | 17,442 | 48,367 | -16,051 |
| S1b-LIVE (30/30/5/1 cell on state) | U7 | -3,452 | 659 | 1,391 | 4,182 | 2,323 | 830 | 1,401 | 1,180 | 16,059 | 42,606 | 23,192 |
| never-cut (NOCUT, = plain 60/60 in the replica) | A7 | -405 | 629 | 430 | 987 | 838 | 340 | 988 | 267 | 9,361 | 8,625 | -7,321 |
| HOLD-old (old live L2 cut) | A7 | -43 | 693 | 645 | 1,365 | 849 | 522 | 781 | 471 | 6,972 | 7,224 | -1,687 |
| S1b-COMB (live v1.5 seven state-cut lines) | A7 | -1,257 | 706 | 496 | 579 | 612 | 469 | 991 | 267 | 8,518 | 7,325 | -11,794 |
| S1b-UNIF (one cell for all books) | A7 | -1,316 | 554 | 330 | 1,119 | 743 | 129 | 794 | 256 | 9,776 | 7,983 | -10,668 |
| S1b-LIVE (30/30/5/1 cell on state) | A7 | -202 | 924 | 520 | 1,239 | 791 | 346 | 943 | 267 | 9,663 | 9,385 | -8,502 |
| never-cut (NOCUT, = plain 60/60 in the replica) | H7 | 928 | 1,595 | -290 | 2,330 | 407 | -989 | 1,816 | 270 | 16,242 | 18,436 | -13,688 |
| HOLD-old (old live L2 cut) | H7 | 2,431 | 1,353 | 649 | 2,762 | 565 | -825 | 1,406 | 599 | 12,317 | 12,561 | 390 |
| S1b-COMB (live v1.5 seven state-cut lines) | H7 | 3,510 | 2,206 | 1,228 | 2,443 | 797 | -445 | 1,468 | 220 | 8,818 | 19,256 | 12,306 |
| S1b-UNIF (one cell for all books) | H7 | 1,277 | 2,317 | 209 | 2,516 | 505 | -1,115 | 1,735 | 34 | 16,068 | 18,436 | -19,153 |
| S1b-LIVE (30/30/5/1 cell on state) | H7 | 704 | 1,241 | -534 | 2,359 | 465 | -1,548 | 1,507 | 206 | 15,603 | 18,436 | -20,428 |
| never-cut (NOCUT, = plain 60/60 in the replica) | O7 | -1,236 | -299 | -151 | 52 | 557 | -58 | 647 | -73 | 6,958 | 4,797 | -11,023 |
| HOLD-old (old live L2 cut) | O7 | -745 | 368 | 202 | 116 | 360 | -604 | 392 | -150 | 5,513 | 5,222 | -8,543 |
| S1b-COMB (live v1.5 seven state-cut lines) | O7 | -1,153 | -478 | 189 | 357 | 674 | -127 | 646 | -69 | 6,656 | 4,532 | -8,908 |
| S1b-UNIF (one cell for all books) | O7 | -1,236 | -299 | -151 | 52 | 522 | -58 | 661 | -55 | 6,958 | 4,797 | -11,023 |
| S1b-LIVE (30/30/5/1 cell on state) | O7 | -1,236 | -540 | -205 | 208 | 607 | -26 | 688 | -73 | 8,806 | 4,797 | -12,796 |

S1b-COMB vs never-cut, USD/wk (stack, carrying week dropped): L1M +12,824 (MDE 15,728), L2M +9,199 (MDE 11,442), L3M +6,130 (MDE 13,002), L6M +6,536 (MDE 9,935), HOLD +6,246 (MDE 6,998), MID +8,032 (MDE 14,081), PRE +1,599 (MDE 4,255), X' +772 (MDE 2,860). All below MDE. Windows here are as of 2026-11-09 (L1M 20261011-, L2M 20260911-, L3M 20260812-, L6M 20260512-), the ENTRY-MATCH / TH_STATE_BASE_S1B.md table uses windows as of 2026-10-31 (L1M +9,184, L2M +8,476, L3M +6,532, L6M +7,290; HOLD, MID, PRE, X' are identical): the L1M-L6M differences are the window shift; the base_b runs end 2026-10-31, so the live week (2026-11-02..05) is not in these reference rows.
Regression status: only a one-month tick/timer-close regression (202304) exists for the S1b engine base; none exists for the references (NOCUT, HOLD-old, S1b-UNIF, S1b-LIVE). The S1b references are the full 43-month rebuilds of ENTRY-MATCH (autopilot/TH_STATE_BASE_S1B.md).

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
| M7 | profit | I_decay | {"P": [9.0, 30.0, 5.0, 1.0, 0.3], "X0": 30, "Xmin": 5, "arm": 0.3, "ra | 21,793 / 44,425 | 52,180 / 50,321 | 383 | -673 | 3,872 | S1 | CANDIDATE-DD [rec-ok wf-ok plc-ok exposure] |
| U7 | loss | LBC_ice_ag_w10 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "ice_ag_w10", "mode | 6,061 / 21,561 | 35,033 / 42,226 | 809 | -624 | 2,829 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| U7 | profit | H_pcthour | {"P": [3.0, 0.3, 120.0, 510.0], "pct": 0.3, "window": "ldn"} | 8,700 / 21,561 | 42,735 / 42,226 | 153 | -1,294 | 7,540 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A7 | loss | D3_pullback | {"X": 20, "pb": 50} | 4,760 / 12,461 | 5,445 / 6,089 | 511 | -146 | -1,314 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A7 | profit | H_pcthour | {"P": [3.0, 0.4, 1080.0, 120.0], "pct": 0.4, "window": "asia"} | 3,268 / 12,461 | 6,089 / 6,089 | 427 | -289 | 665 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H7 | loss | LBC_sweep8_w10 | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w10", "mode | 4,988 / 15,477 | 15,783 / 20,667 | 1,281 | -138 | 394 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| H7 | profit | H_mom | {"P": [1.0, 9.0, 0.0, 1.0, 0.25, -1.0], "arm": 0.25, "feat": "vel30<=" | 5,961 / 15,477 | 10,161 / 20,667 | 137 | -975 | 2,524 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| O7 | loss | LBC_dtot8_rel_w15 | {"arm": 0.15, "arm_kind": "pct", "dir": -1, "feat": "dtot8_rel_w15", " | 2,725 / 7,469 | 5,195 / 5,102 | 325 | -395 | 940 | S1 | CANDIDATE-DD [rec-ok wf-ok plc-ok exposure] |
| O7 | profit | I_step | {"P": [7.0, 10.0, 1.0], "lag": 1, "step": 10} | 4,420 / 7,469 | 4,995 / 5,102 | 215 | -498 | 1,167 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

## Profit side: Stage 1 best vs Stage 2 engine-confirmed rule (per book)
| book | Stage 1 best profit (technique, L6M maxDD w/wo, L6M mean) | Stage 2 engine rule (set) | S2 L6M maxDD w/wo | S2 L6M mean | S2 PRE maxDD w/wo | S2 PRE mean | months run | verdict |
|---|---|---|---|---|---|---|---|---|
| K7 | J3_statescale, 8,893 / 20,902, 666 | I_bookarm X=20 arm=0.25 feat=ice_ag_w30 secs=30 thr=3 (phi_pb) | 23,159 / 35,969 | -1,689 | 19,141 / 22,188 | -719 | 43 | drawdown for profit (mean < 0) |
| K7 | J3_statescale, 8,893 / 20,902, 666 | H_thick arm=0.5 feat=tot_rel_slow secs=1 thr=2.0 (phi_thick) | 20,056 / 35,969 | 656 | 29,349 / 22,188 | -17 | 36 | L6M ok but PRE maxDD worse |
| P7 | H_gated, 71,485 / 133,887, 655 | H_pcthour pct=0.6 window=am (phi_pb) | 191,674 / 203,542 | 236 | 120,861 / 122,169 | 701 | 43 | engine-confirmed (dd lower, mean >= 0, PRE maxDD within +5%) |
| P7 | H_gated, 71,485 / 133,887, 655 | H_gated arm=0.7 feat=tot_rel_fast secs=1 thr=2 (phi_thick) | 186,789 / 203,542 | 295 | 121,413 / 122,169 | -163 | 36 | engine-confirmed (dd lower, mean >= 0, PRE maxDD within +5%) |
| M7 | I_decay, 21,793 / 44,425, 383 | H_tip pct=0 secs=600 (phi_pb) | 46,661 / 48,019 | -141 | 66,091 / 44,205 | -616 | 43 | drawdown for profit (mean < 0) |
| M7 | I_decay, 21,793 / 44,425, 383 | H_thick arm=0.1 feat=tot_rel_slow secs=1 thr=1.3 (phi_thick) | 30,068 / 48,019 | -389 | 67,688 / 44,205 | -577 | 36 | drawdown for profit (mean < 0) |
| U7 | H_pcthour, 8,700 / 21,561, 153 | H_pcthour pct=0.3 window=ldn (phi_pb) | 14,388 / 17,816 | -562 | 41,634 / 39,542 | -651 | 43 | drawdown for profit (mean < 0) |
| A7 | H_pcthour, 3,268 / 12,461, 427 | H_pcthour pct=0.4 window=asia (phi_pb) | 6,023 / 9,361 | -188 | 15,274 / 8,625 | -455 | 43 | drawdown for profit (mean < 0) |
| H7 | H_mom, 5,961 / 15,477, 137 | H_mom arm=0.25 feat=vel30<= secs=1 thr=0 (phi_pb) | 11,897 / 16,242 | -670 | 13,803 / 18,436 | -457 | 43 | drawdown for profit (mean < 0) |
| O7 | I_step, 4,420 / 7,469, 215 | I_step lag=1 step=10 (phi_pb) | 4,210 / 6,958 | 251 | 4,720 / 4,797 | -494 | 43 | engine-confirmed (dd lower, mean >= 0, PRE maxDD within +5%) |

Stage 2 overturns or fails to confirm the Stage 1 profit pick on 5 of 7 books (Stage 1 picks that cannot run through the engine count as not confirmed). Every book keeps a profit line below, labelled PRE-PROOF; only engine-confirmed rules are un-commented candidates, none is ENTER.

```
#! # profit K7 * [I_bookarm X=20 arm=0.25 feat=ice_ag_w30 secs=30 thr=3] (engine phi_pb; PRE-PROOF)   # NEEDS: exit action beyond take-at-pct; Stage 2 L6M maxDD 23,159/35,969, L6M mean -1,689
#! # profit K7 * [H_thick arm=0.5 feat=tot_rel_slow secs=1 thr=2.0] (engine phi_thick; PRE-PROOF)   # NEEDS: exit action beyond take-at-pct; Stage 2 L6M maxDD 20,056/35,969, L6M mean 656
# profit P7 * [H_pcthour pct=0.6 window=am] (engine phi_pb; PRE-PROOF)   # NEEDS: exit action beyond take-at-pct; Stage 2 L6M maxDD 191,674/203,542, L6M mean 236
# profit P7 * [H_gated arm=0.7 feat=tot_rel_fast secs=1 thr=2] (engine phi_thick; PRE-PROOF)   # NEEDS: exit action beyond take-at-pct; Stage 2 L6M maxDD 186,789/203,542, L6M mean 295
#! # profit M7 * [H_tip pct=0 secs=600] (engine phi_pb; PRE-PROOF)   # NEEDS: exit action beyond take-at-pct; Stage 2 L6M maxDD 46,661/48,019, L6M mean -141
#! # profit M7 * [H_thick arm=0.1 feat=tot_rel_slow secs=1 thr=1.3] (engine phi_thick; PRE-PROOF)   # NEEDS: exit action beyond take-at-pct; Stage 2 L6M maxDD 30,068/48,019, L6M mean -389
#! # profit U7 * [H_pcthour pct=0.3 window=ldn] (engine phi_pb; PRE-PROOF)   # NEEDS: exit action beyond take-at-pct; Stage 2 L6M maxDD 14,388/17,816, L6M mean -562
#! # profit A7 * [H_pcthour pct=0.4 window=asia] (engine phi_pb; PRE-PROOF)   # NEEDS: exit action beyond take-at-pct; Stage 2 L6M maxDD 6,023/9,361, L6M mean -188
#! # profit H7 * [H_mom arm=0.25 feat=vel30<= secs=1 thr=0] (engine phi_pb; PRE-PROOF)   # NEEDS: exit action beyond take-at-pct; Stage 2 L6M maxDD 11,897/16,242, L6M mean -670
# profit O7 * [I_step lag=1 step=10] (engine phi_pb; PRE-PROOF)   # NEEDS: exit action beyond take-at-pct; Stage 2 L6M maxDD 4,210/6,958, L6M mean 251
```

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
See autopilot/EXH_STAGE2.md (per completed set and per book: engine vs never-cut and vs S1b-COMB, live week, Stage 1 gain kept). The cells below are the only ones with engine-cascade evidence (weak = L6M maxDD lower and PRE within +5%; STRICT = both at least 2% lower); a label of CANDIDATE-DD without FAILS-LIVE-WEEK is the bar for a shadow forward test.

- ldef_perbook_u2 M7 (weak): L6M maxDD 37,288 vs 48,019, PRE maxDD 44,115 vs 44,205, L6M mean -133/wk, PRE mean -212/wk, live week -1,985, recents ok, label no; Stage 1 L6M gain kept in the engine: 35%.
- ldef_perbook_u2 U7 (weak): L6M maxDD 13,232 vs 17,816, PRE maxDD 39,558 vs 39,542, L6M mean -93/wk, PRE mean -369/wk, live week 346, recents ok, label no; Stage 1 L6M gain kept in the engine: 37%.
- ldef_perbook_u2 A7 (STRICT): L6M maxDD 5,897 vs 9,361, PRE maxDD 5,370 vs 8,625, L6M mean 129/wk, PRE mean -167/wk, live week -1,314, recents ok, label CANDIDATE-DD FAILS-LIVE-WEEK; Stage 1 L6M gain kept in the engine: 45%.
- ldef_perbook_u2 O7 (STRICT): L6M maxDD 6,088 vs 6,958, PRE maxDD 3,761 vs 4,797, L6M mean 155/wk, PRE mean -28/wk, live week -11, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: 63%.
- pjkl_PB P7 (weak): L6M maxDD 200,861 vs 203,542, PRE maxDD 120,071 vs 122,169, L6M mean 627/wk, PRE mean 66/wk, live week -1,177, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: 10%.
- pjkl_PB M7 (weak): L6M maxDD 45,824 vs 48,019, PRE maxDD 43,648 vs 44,205, L6M mean -186/wk, PRE mean -18/wk, live week -382, recents ok, label no; Stage 1 L6M gain kept in the engine: 11%.
- pjkl_PB U7 (STRICT): L6M maxDD 8,119 vs 17,816, PRE maxDD 30,546 vs 39,542, L6M mean -570/wk, PRE mean -299/wk, live week -2,110, recents ok, label no; Stage 1 L6M gain kept in the engine: 89%.
- pjkl_PB H7 (STRICT): L6M maxDD 12,781 vs 16,242, PRE maxDD 11,190 vs 18,436, L6M mean -348/wk, PRE mean -717/wk, live week 3,175, recents ok, label no; Stage 1 L6M gain kept in the engine: 45%.
- bc_a_recent M7 (STRICT): L6M maxDD 39,410 vs 48,019, PRE maxDD 28,806 vs 44,205, L6M mean 108/wk, PRE mean 449/wk, live week -620, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: n/a.
- bc_a_recent U7 (weak): L6M maxDD 14,897 vs 17,816, PRE maxDD 40,537 vs 39,542, L6M mean -550/wk, PRE mean -117/wk, live week 4,315, recents ok, label no; Stage 1 L6M gain kept in the engine: 19%.
- bc_m7_cps M7 (STRICT): L6M maxDD 46,847 vs 48,019, PRE maxDD 37,320 vs 44,205, L6M mean -338/wk, PRE mean -16/wk, live week -1,135, recents ok, label no; Stage 1 L6M gain kept in the engine: 4%.
- phi_pb K7 (STRICT): L6M maxDD 23,159 vs 35,969, PRE maxDD 19,141 vs 22,188, L6M mean -1,689/wk, PRE mean -719/wk, live week 619, recents ok, label no; Stage 1 L6M gain kept in the engine: 150%.
- phi_pb P7 (weak): L6M maxDD 191,674 vs 203,542, PRE maxDD 120,861 vs 122,169, L6M mean 236/wk, PRE mean 701/wk, live week -4,320, recents ok, label CANDIDATE-DD FAILS-LIVE-WEEK; Stage 1 L6M gain kept in the engine: 39%.
- phi_pb H7 (STRICT): L6M maxDD 11,897 vs 16,242, PRE maxDD 13,803 vs 18,436, L6M mean -670/wk, PRE mean -457/wk, live week 2,524, recents ok, label no; Stage 1 L6M gain kept in the engine: 46%.
- phi_pb O7 (weak): L6M maxDD 4,210 vs 6,958, PRE maxDD 4,720 vs 4,797, L6M mean 251/wk, PRE mean -494/wk, live week 1,167, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: 90%.
- exla_pb1 K7 (STRICT): L6M maxDD 32,823 vs 35,969, PRE maxDD 19,161 vs 22,188, L6M mean -179/wk, PRE mean -22/wk, live week 477, recents ok, label no; Stage 1 L6M gain kept in the engine: 40%.
- exla_pb1 P7 (STRICT): L6M maxDD 170,616 vs 203,542, PRE maxDD 111,795 vs 122,169, L6M mean -62/wk, PRE mean -825/wk, live week -15,056, recents ok, label no; Stage 1 L6M gain kept in the engine: 39%.
- exla_pb1 M7 (STRICT): L6M maxDD 30,434 vs 48,019, PRE maxDD 28,296 vs 44,205, L6M mean 615/wk, PRE mean 398/wk, live week 724, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: 57%.
- exla_pb1 U7 (weak): L6M maxDD 12,944 vs 17,816, PRE maxDD 40,501 vs 39,542, L6M mean 136/wk, PRE mean -243/wk, live week 0, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: 35%.
- exla_pb1 A7 (STRICT): L6M maxDD 6,849 vs 9,361, PRE maxDD 5,200 vs 8,625, L6M mean -532/wk, PRE mean -225/wk, live week -1,305, recents ok, label no; Stage 1 L6M gain kept in the engine: 34%.
- exla_pb1 H7 (STRICT): L6M maxDD 7,348 vs 16,242, PRE maxDD 16,721 vs 18,436, L6M mean 286/wk, PRE mean -157/wk, live week 319, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: 109%.
- exla_pb1 O7 (STRICT): L6M maxDD 5,668 vs 6,958, PRE maxDD 4,172 vs 4,797, L6M mean 70/wk, PRE mean 11/wk, live week 77, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: 54%.
- exla_pb2 K7 (STRICT): L6M maxDD 26,854 vs 35,969, PRE maxDD 20,717 vs 22,188, L6M mean -943/wk, PRE mean -625/wk, live week 312, recents ok, label no; Stage 1 L6M gain kept in the engine: 117%.
- exla_pb2 P7 (weak): L6M maxDD 159,250 vs 203,542, PRE maxDD 121,093 vs 122,169, L6M mean 822/wk, PRE mean 57/wk, live week -5,309, recents ok, label CANDIDATE-DD FAILS-LIVE-WEEK; Stage 1 L6M gain kept in the engine: 54%.
- exla_pb2 M7 (STRICT): L6M maxDD 24,083 vs 48,019, PRE maxDD 30,278 vs 44,205, L6M mean 245/wk, PRE mean 108/wk, live week -2,837, recents ok, label CANDIDATE-DD FAILS-LIVE-WEEK; Stage 1 L6M gain kept in the engine: 79%.
- exla_pb2 A7 (STRICT): L6M maxDD 6,128 vs 9,361, PRE maxDD 7,884 vs 8,625, L6M mean -187/wk, PRE mean -216/wk, live week -169, recents ok, label no; Stage 1 L6M gain kept in the engine: 45%.
- exla_pb2 H7 (STRICT): L6M maxDD 10,170 vs 16,242, PRE maxDD 17,557 vs 18,436, L6M mean -62/wk, PRE mean -21/wk, live week 194, recents ok, label no; Stage 1 L6M gain kept in the engine: 76%.
- exla_pb2 O7 (STRICT): L6M maxDD 5,668 vs 6,958, PRE maxDD 4,172 vs 4,797, L6M mean 70/wk, PRE mean 11/wk, live week 77, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: 54%.
- exla_uni K7 (STRICT): L6M maxDD 17,849 vs 35,969, PRE maxDD 17,751 vs 22,188, L6M mean -158/wk, PRE mean -640/wk, live week 2,312, recents ok, label no; Stage 1 L6M gain kept in the engine: n/a.
- exla_uni P7 (STRICT): L6M maxDD 164,061 vs 203,542, PRE maxDD 111,663 vs 122,169, L6M mean 617/wk, PRE mean -947/wk, live week -15,056, recents FAIL, label CANDIDATE-DD FAILS-LIVE-WEEK; Stage 1 L6M gain kept in the engine: 47%.
- exla_uni A7 (STRICT): L6M maxDD 7,915 vs 9,361, PRE maxDD 7,707 vs 8,625, L6M mean 158/wk, PRE mean -116/wk, live week -2,382, recents ok, label CANDIDATE-DD FAILS-LIVE-WEEK; Stage 1 L6M gain kept in the engine: 28%.
- exla_uni H7 (STRICT): L6M maxDD 14,871 vs 16,242, PRE maxDD 17,680 vs 18,436, L6M mean -21/wk, PRE mean -346/wk, live week 47, recents ok, label no; Stage 1 L6M gain kept in the engine: n/a.
- ldef_uniform_u2 P7 (weak): L6M maxDD 179,872 vs 203,542, PRE maxDD 126,002 vs 122,169, L6M mean 846/wk, PRE mean -179/wk, live week -24,336, recents ok, label CANDIDATE-DD FAILS-LIVE-WEEK; Stage 1 L6M gain kept in the engine: 38%.
- ldef_uniform_u2 M7 (STRICT): L6M maxDD 43,917 vs 48,019, PRE maxDD 30,453 vs 44,205, L6M mean -458/wk, PRE mean -183/wk, live week 3,427, recents ok, label no; Stage 1 L6M gain kept in the engine: 156%.
- ldef_uniform_u2 U7 (weak): L6M maxDD 13,577 vs 17,816, PRE maxDD 40,623 vs 39,542, L6M mean 94/wk, PRE mean -382/wk, live week 346, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: 40%.
- ldef_uniform_u2 A7 (STRICT): L6M maxDD 5,537 vs 9,361, PRE maxDD 5,415 vs 8,625, L6M mean 32/wk, PRE mean -240/wk, live week -1,018, recents ok, label CANDIDATE-DD FAILS-LIVE-WEEK; Stage 1 L6M gain kept in the engine: 50%.
- ldef_uniform_u2 H7 (STRICT): L6M maxDD 11,345 vs 16,242, PRE maxDD 16,436 vs 18,436, L6M mean -79/wk, PRE mean -536/wk, live week 660, recents ok, label no; Stage 1 L6M gain kept in the engine: n/a.
- pjkl_UNI H7 (weak): L6M maxDD 15,922 vs 16,242, PRE maxDD 18,436 vs 18,436, L6M mean 13/wk, PRE mean -18/wk, live week 0, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: 12%.
- bc_c_uniform K7 (STRICT): L6M maxDD 25,881 vs 35,969, PRE maxDD 21,466 vs 22,188, L6M mean 305/wk, PRE mean -310/wk, live week 1,817, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: n/a.
- bc_c_uniform P7 (weak): L6M maxDD 183,796 vs 203,542, PRE maxDD 123,623 vs 122,169, L6M mean 1,886/wk, PRE mean 136/wk, live week 2,806, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: 48%.
- bc_c_uniform U7 (weak): L6M maxDD 17,213 vs 17,816, PRE maxDD 41,373 vs 39,542, L6M mean 247/wk, PRE mean -95/wk, live week 0, recents ok, label CANDIDATE-DD; Stage 1 L6M gain kept in the engine: n/a.
- bc_c_uniform A7 (weak): L6M maxDD 8,444 vs 9,361, PRE maxDD 8,592 vs 8,625, L6M mean 108/wk, PRE mean 1/wk, live week -1,638, recents ok, label CANDIDATE-DD FAILS-LIVE-WEEK; Stage 1 L6M gain kept in the engine: 70%.
- bc_b_ddbest P7 (weak): L6M maxDD 144,229 vs 203,542, PRE maxDD 122,252 vs 122,169, L6M mean 3,966/wk, PRE mean -770/wk, live week -71,288, recents ok, label CANDIDATE-DD FAILS-LIVE-WEEK; Stage 1 L6M gain kept in the engine: 61%.

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
| A (EX-LA) | EXH_A.md | in | 11:36Z |
| B/C (EX-LBC) | EXH_BC.md | in | 11:45Z |
| D/E/F (EX-LDEF) | EXH_DEF.md | in | 11:31Z |
| G (EX-LG) | EXH_G.md | in | 11:22Z |
| H/I (EX-PHI) | EXH_HI.md | in | 12:20Z |
| J/K/L (EX-PJKL) | EXH_JKL.md | in | 12:02Z |

## wf-ok flags: what they mean
The wf flag on a candidate row is the TECHNIQUE-level walk-forward (picking among the cells of that one technique on trailing 26 weeks, applied to the next month; wf-ok = total delta >= 0 and WF maxDD within +5% of never-cut). It is a weak test: e.g. O7 loss LBC_dtot8_rel_w15 (13 cells) is wf-ok with +1,917 USD over 35 test months, but its WF maxDD equals the never-cut maxDD (7,469), i.e. the picks did not lower the drawdown, and the global picking procedure for O7 loss (6,272 cells) is wf-FAIL (-44,366). Read wf-ok as not-negative, not as out-of-sample drawdown evidence. No cell is ENTER.

## Final QA (3 random rows per section re-derived from the ledger / base_b trades)
QA (final, 2026-11-09 12:39Z): Reference rows: 3 random rows re-derived from base_b trades: 3/3 match (HOLD-old (old live L2  P7: OK; S1b-UNIF (one cell for ALL: OK; HOLD-old (old live L2  H7: OK). Per-book policy table: 3 random rows looked up in the ledger (U2, stage 1): 3/3 match (M7 loss F3_stop_extreme: OK; A7 profit H_pcthour: OK; P7 loss D3_pullback@after30: OK). Profit side table: 3 random rows vs the Stage 2 ledger rows of the set named in the row: 3/3 match (U7: OK; M7: OK; P7: OK). Engine evidence lines: 3 random lines vs the Stage 2 ledger: 3/3 match (ldef_perbook_u2 M7: OK; exla_uni P7: OK; pjkl_PB U7: OK). ALL SAMPLED ROWS MATCH.