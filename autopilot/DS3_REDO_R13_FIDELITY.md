# DS3_REDO_R13_FIDELITY - fidelity loop and fill model (REDO-R13; PRE-PROOF; FINAL version 2026-11-10 15:11Z)
**Label: base = S1b-COMB state engine (replica, tick bar close, TH-L2-S state cuts); entries NOT live-matched unconditionally (U_main 0.719 < .85): every page stays PRE-PROOF. No PASS claims, nothing goes live.** Code outputs/code/th_r13/ (r13_lib, r13_report, r13_page, r13_engine, monday_acceptance.py, panel_installed.json); prereg sha line in DECISIONS.md 2026-11-09T21:20Z; engine runs = the existing entry_match runs (read-only) + R13_reg_ucomb and R13_BLIND_FINAL (fresh runs via monday_acceptance.py --engine blind; trades.csv byte-identical to runs/u_comb; peak RSS 8.6 GB for the blind week, NOT the 1.9 GB of the 2-day hist smoke: earlier statement corrected); frozen live file only (sha 424c68da...a927112).

## SUMMARY BLOCK
| item | result |
|--|--|
| Data status | **The Monday live CSV is NOT on the box.** data/live/StratTrades_DS7_<acct>.csv is the 2026-11-08 22:05Z sync: last entryTime 2026-11-06 11:36 ET, last P7 exit 2026-11-05 20:28 ET; nothing after 11-05 20:28 ET exists and nothing after was read. The 11-02..11-05 rows of it were reconciled to the frozen reconstruction: all 187 frozen rows are in the unfrozen file with identical qty, times, prices, P&L, exit names (0 differences); 55 other rows lie after 11-05 11:05 ET. |
| (a) Entry match, state base, unconditional | U_main **0.719** (U_nolots 0.736, strict 0.633; 153 matched of 187 live / 174 engine; class A 34, class B 21). Target >= .85: **NOT met**. Same engine with the old per-print cut (what live ran in the blind week): 0.776. Conditional on live exits (C2/C3 diagnostic, ENTRY_MATCH.md): .896 / .914. |
| Why it cannot close on this week | 36 of the 55 unconditional mismatches (A 21 + B 15) are exit-cascade (the engine's state cut exits at other times than the live per-print cut, so books are open/flat at different moments), 12 (A 9 + B 3) are lock states fed by those P&L paths, 7 (A 4 + B 3) raw-signal differences. Closing the cascade alone would give U_nolots .90, cascade+locks .96 (table 1h). The blind-week live cut was a per-print NT8-DOM rule, v1.5 replaced it by the state cut: **the blind week is not a clean unconditional test for the state base; the first clean test is the Monday week (v1.5 live = state cuts), via monday_acceptance.py.** |
| Fixable engine settings found from DS7.cs / panel | none new beyond ENTRY_MATCH F1-F7 (tick close, half-even rounding, X-bar rules, extras held), which are already in the base. Session tables, lots chain, locks, skip slots: planned lots equal live qty in 177 of 184 pairs; no mismatch traced to them. Nothing was fitted to the live week. Open inputs listed in R13_INSTALLED_PANEL.md section 3. |
| (b) Fill drift, entries | engine pays **0.47 pt more** than live on the average entry (n=153, se 0.10); 1-lot market 0.33 (n=80); sliced + 30% add 0.71 (n=51); sliced no add 0.06 (n=9): the drift sits in the add. About $4,226 over the 153 pairs. |
| (b) Fill drift, market cuts | live adverse vs 1-s mid at stamp+1: **0.57 pt** (n=94, se 0.15; stamp+0 1.19, +2 0.59) vs engine model 0.80: the 0.80 basis is 0.23 pt pessimistic (inside ~1.5 se of the prior 0.80+-0.22); about $1,090 on the sample. Recalibrated central value 0.57 +- 0.15 (not applied to the base). |
| (b) Fill drift, targets | resting target at nominal both sides: live distance from own fill average 60.00, engine median difference 0.00 pt; fill second median 0 s (mean +1.9 s, p90 +6.6 s). No slippage to calibrate. |
| (b) Fill drift, stops | **live sample = 2 Stop exits** (K7 -83.00, M7 -80.75 from the entry average: both during the Tue 02:55-08:20 stall at the native 80 catastrophe level, i.e. +3.0 and +0.75 beyond 80) + 3 BookLock market exits. The 2.45-pt figure cannot be re-calibrated from the frozen week (n=2, both in the stall); join exits (`_StopJoin`, `_StopJoinFallback`) n=0 live vs 12 in the engine. Monday's file is the first chance (need >= 20 stops). |
| (c) Monday acceptance | code/th_r13/monday_acceptance.py written and regression-tested on the frozen week (U_main .719, identical to runs/u_comb); hist-week path smoke-tested (2 days, 1.9 GB peak, 19 s); stops cleanly with TAPE_MISSING.txt when the week's tape is absent (it is, for 11-06..11-13). Panel as installed: R13_INSTALLED_PANEL.md. |
| Needs from the user | brackets as installed, policy file text, P7 lot string, join/native stop modes, bug-exit list, DS7.cs v1.5, the week's live CSV + NQ mbp-10 tape (R13_INSTALLED_PANEL.md s3; MORNING_FLAGS.md). |

| ROLLFIX1 base | Entry match and fill tables re-run on the current state base ROLLFIX1 (S1BRF-COMB, base_b_rollfix, SZ_BASE_PROOF s10): ROLLFIX1 flattens positions only at the 14 contract-roll seconds (last roll 2026-09-15, none inside 11-01..11-05); 202610 base_b_rollfix trades are identical to base_b (823 trades, net 47,330.50), so every number of the frozen week is unchanged by ROLLFIX1 (fresh run R13_BLIND_FINAL = u_comb byte for byte). |
| Rule 2a (25% of live PRE mean) | live PRE mean $13,961/wk (Z.live_pre_mean ROLLFIX1), floor -$3,490/wk (Z.prior_info). Only label in R13's scope: the P7 cut 40/5x/w5/p3 (exact PRE maxDD +25.2% deeper, d mean -$1,056/wk, L6M cut +16.9%): mean floor now PASSES (-1,056 > -3,490), maxDD allowance 15% at WF 42-54% (< 60%) and 25% even at WF 70% (25.2 > 25): **RECENT-ONLY** unchanged (old -$1k label also RECENT-ONLY). Fidelity tables themselves carry no rule-2a labels. |
| Stop-fill caveat | every stop figure here is n = 2 (K7 Stop, M7 Stop; both in the Tue stall at the native 80 level) plus 3 BookLock; join fills n = 0. The 2.45-pt basis and the engine's native/join stop model are NOT validated by this week: treat every stop-fill-dependent result (R7, R9, R12, P7 7-lot stops) as using an uncalibrated basis until Monday's file has >= 20 stops. |
| Bug exits | the 10 v1.5 state cuts of 11-08/09 (1 H7 + 9 M7) are outside the frozen week (0 in it); monday_acceptance.py excludes them (panel.bug_*: H7/M7 cut exits, 11-08 18:00..11-09 09:00 ET window, assumed until the list arrives), from exit match, P&L by cause and fill tables, and flags same-book followers. |
| Monday acceptance status | installed panel in panel_installed.json = SZ-CORE LPB_BASE (P7 lots 7,4,0,4,0,0; P7 day cap 42,000 / 8,400; P7 cut 40/5x/w5/p3 from 11-09 20:30Z, v2 45/5x/w5/p10 before; other books S1b-COMB cells incl. H7 nyam override; brackets live 60/60, O7 40/90: **bracket retargets still not given, ask open in MORNING_FLAGS**). Script regression-tested twice on the frozen week; the new-week path runs but stops with TAPE_MISSING: hist day files end 2026-10-30, 1-s state days end 2026-11-05, so the week of 11-08 cannot be engine-run here. The unfrozen data/live DS7 file has a newer sync (mtime 11-09 22:05Z); per the R13 read rule only its 11-02..11-05 rows were used (reconciled, identical to the frozen file) and nothing later was read: running the acceptance on it is one command once the tape exists. |

## 1. ENTRY MATCH (a): diagnosis by class on the state base
Definitions (prereg, ENTRY_MATCH.md s1): stamp = live entryTime vs engine floor(first fill - 1 s); same book and side, |dt| <= 2 s, one-to-one; outage Tue 02:55-08:20 ET excluded on both sides. U = matched / (live + engine - matched). Classes: **A** live took / engine flat; **B** engine took / live flat; **P** both took with a deviation (second, lots, exit). Cause labels for A and B come from the engine's own skip reasons / open positions and from the live trade intervals; "cascade" = the other side's book is open or closed at a different time because exits differ.
### 1a. Match by run (live 187 rows; outage Tue 02:55-08:20 ET excluded on both sides; |dt| <= 2 s, one-to-one)
| run | nE | matched | lots_EQ | PLAN | AMB | BAD | U_nolots | U_strict | U_main | engine_only | live_only |
|--|--|--|--|--|--|--|--|--|--|--|--|
| S1b-COMB state base (u_comb) | 174 | 153 | 140 | 9 | 2 | 2 | 0.736 | 0.633 | 0.719 | 21 | 34 |
| S1-UNIF (u_unif) | 162 | 147 | 133 | 9 | 2 | 3 | 0.728 | 0.616 | 0.702 | 15 | 40 |
| S1-LIVE cell on state (u_live) | 155 | 137 | 124 | 8 | 2 | 3 | 0.668 | 0.569 | 0.644 | 18 | 50 |
| HOLD = old per-print cut, what live ran in the blind week (u_hold) | 202 | 174 | 159 | 9 | 2 | 4 | 0.809 | 0.691 | 0.776 | 28 | 13 |
| C2 diagnostic: live exits drive the books (fin_c2) | 194 | 184 | 167 | 11 | 2 | 4 | 0.934 | 0.780 | 0.896 | 10 | 3 |
| C3 diagnostic (fin_c3) | 190 | 184 | 167 | 11 | 2 | 4 | 0.953 | 0.795 | 0.914 | 6 | 3 |

### 1b. Mismatch classes on S1b-COMB (A = live took / engine flat; B = engine took / live flat; pnl = the trade's own net: live P&L for A, engine P&L for B)
| cls | cause | n | pnl |
|--|--|--|--|
| A | EXIT-CASCADE (engine position still open / differently timed exit) | 21 | 1942 |
| A | LOCK-STATE (engine day/week halt) | 9 | -156 |
| A | SIGNAL absent (no engine signal within 5 s) | 4 | 10786 |
| B | LIVE-HELD (live trade of the book still open: exit cascade) | 15 | 8420 |
| B | LOCK-STATE (live BookLock earlier) | 3 | 7253 |
| B | SIGNAL extra / live skipped (live flat) | 3 | 2015 |

### 1c. By book (live rows per book, class A and B counts)
| book | A | B | live_n |
|--|--|--|--|
| A7 | 5 | 1 | 23 |
| H7 | 0 | 1 | 3 |
| K7 | 12 | 6 | 64 |
| M7 | 6 | 4 | 28 |
| P7 | 11 | 9 | 53 |

### 1d. By time of day (ET hour bands; A+B)
| sess | A | B |
|--|--|--|
| asia 18-02 | 12 | 9 |
| london 02-08:29 | 8 | 9 |
| nypm/close 12+ | 4 | 0 |
| pre/nyam 09-11 | 10 | 3 |

### 1e. Pairs (153) with any deviation (second / lots / exit) beside the entry match
| both took, deviation in | n |
|--|--|
| exit differs | 76 |
| lots PLAN | 9 |
| second -1 | 4 |
| lots BAD | 2 |
| lots AMB | 2 |
| second -2 | 2 |

### 1f. Matched pairs by exit type pair (net $, 4.84 fee proxy removed in favour of the live 1.18/lot; engine net_fee)
| live_exit | eng_exit | n | live_pnl | eng_pnl | eng_minus_live |
|--|--|--|--|--|--|
| target | state/market cut | 4 | 23976 | -14136 | -38112 |
| target | target | 68 | 185207 | 167524 | -17683 |
| state/market cut | stop | 13 | -19979 | -35679 | -15700 |
| state/market cut | state/market cut | 52 | -85493 | -96880 | -11387 |
| BookLock | state/market cut | 1 | -96 | -3264 | -3168 |
| state/market cut | BookLock | 1 | -886 | -936 | -50 |
| stop | stop | 1 | -1616 | -1606 | 10 |
| BookLock | BookLock | 1 | -856 | -66 | 790 |
| stop | state/market cut | 1 | -1661 | -602 | 1059 |
| state/market cut | target | 11 | -7572 | 20580 | 28152 |

### 1g. P&L difference engine minus live by cause (blind week, S1b-COMB)
| item | $ |
|--|--|
| live total (187 rows, net of 1.18/lot) | 103596 |
| engine total (174 trades) | 52622 |
| difference | -50973 |
| = class A (live trades the engine lacks: minus their live P&L) | -12572 |
| + class B (engine-only trades: their engine P&L) | 17689 |
| + 153 matched pairs, engine minus live | -56090 |
| check (must be 0) | 0.00 |

### 1h. What U would be if a class were closed (all other mismatches left; lots/second ignored)
| scenario | U_nolots |
|--|--|
| as run | 0.736 |
| exit-cascade (A and B) closed | 0.902 |
| exit-cascade + lock-state closed | 0.963 |
| everything but raw-signal differences closed | 0.963 |

### 1i. Per-trade list of class A and B (S1b-COMB)
| cls | book | t | side | qty | cause | live_exit | pnl |
|--|--|--|--|--|--|--|--|
| B | P7 | 2026-11-01 19:46:00 | 1 | 2 | LIVE-HELD (live trade of the book still open: exit cascade) | Target | 2403 |
| B | P7 | 2026-11-01 20:25:02 | 1 | 6 | LIVE-HELD (live trade of the book still open: exit cascade) | Target | 7188 |
| A | P7 | 2026-11-01 20:45:00 | 1 | 4 | EXIT-CASCADE (engine position still open / differently timed exit) | Target | 4805 |
| A | A7 | 2026-11-01 22:13:00 | 1 | 1 | EXIT-CASCADE (engine position still open / differently timed exit) | BookLock | -396 |
| B | P7 | 2026-11-01 22:42:00 | 1 | 10 | LIVE-HELD (live trade of the book still open: exit cascade) | StateCut | -6847 |
| B | A7 | 2026-11-01 22:46:00 | 1 | 1 | LIVE-HELD (live trade of the book still open: exit cascade) | BookLock | -941 |
| A | P7 | 2026-11-01 23:03:00 | 1 | 2 | EXIT-CASCADE (engine position still open / differently timed exit) | ThL2Cut | -1407 |
| A | K7 | 2026-11-02 01:45:00 | -1 | 1 | EXIT-CASCADE (engine position still open / differently timed exit) | Target | 1199 |
| A | P7 | 2026-11-02 01:51:01 | -1 | 4 | EXIT-CASCADE (engine position still open / differently timed exit) | Target | 4795 |
| B | P7 | 2026-11-02 02:13:00 | -1 | 6 | LIVE-HELD (live trade of the book still open: exit cascade) | Target | 7183 |
| B | K7 | 2026-11-02 02:36:00 | -1 | 2 | LIVE-HELD (live trade of the book still open: exit cascade) | StateCut | -1689 |
| A | P7 | 2026-11-02 03:23:01 | -1 | 2 | EXIT-CASCADE (engine position still open / differently timed exit) | ThL2Cut | -2052 |
| A | P7 | 2026-11-02 05:01:00 | -1 | 3 | EXIT-CASCADE (engine position still open / differently timed exit) | Target | 3601 |
| B | K7 | 2026-11-02 05:30:00 | -1 | 1 | LIVE-HELD (live trade of the book still open: exit cascade) | Target | 1199 |
| A | M7 | 2026-11-02 08:20:00 | -1 | 3 | EXIT-CASCADE (engine position still open / differently timed exit) | PolicyCut | -1779 |
| A | M7 | 2026-11-02 10:02:00 | -1 | 1 | SIGNAL absent (no engine signal within 5 s) | ThL2Cut | -576 |
| A | K7 | 2026-11-02 10:36:00 | 1 | 1 | SIGNAL absent (no engine signal within 5 s) | PolicyCut | -626 |
| B | M7 | 2026-11-02 11:17:00 | -1 | 1 | SIGNAL extra / live skipped (live flat) | Target | 1199 |
| A | M7 | 2026-11-02 11:21:00 | -1 | 1 | EXIT-CASCADE (engine position still open / differently timed exit) | Target | 1199 |
| B | K7 | 2026-11-02 20:30:00 | 1 | 1 | LIVE-HELD (live trade of the book still open: exit cascade) | StopJoinFallback | -1176 |
| A | P7 | 2026-11-02 20:42:01 | -1 | 4 | EXIT-CASCADE (engine position still open / differently timed exit) | ThL2Cut | -2500 |
| A | K7 | 2026-11-03 01:36:01 | 1 | 1 | EXIT-CASCADE (engine position still open / differently timed exit) | ThL2Cut | -1031 |
| B | K7 | 2026-11-03 02:03:00 | -1 | 1 | LIVE-HELD (live trade of the book still open: exit cascade) | Stop | -1591 |
| B | M7 | 2026-11-03 08:27:00 | 1 | 1 | SIGNAL extra / live skipped (live flat) | Target | 1199 |
| A | K7 | 2026-11-03 10:57:00 | 1 | 1 | LOCK-STATE (engine day/week halt) | PolicyCut | -656 |
| B | H7 | 2026-11-03 11:00:00 | 1 | 1 | SIGNAL extra / live skipped (live flat) | StateCut | -382 |
| A | K7 | 2026-11-03 11:33:00 | -1 | 1 | LOCK-STATE (engine day/week halt) | ThL2Cut | -596 |
| B | P7 | 2026-11-03 18:36:00 | 1 | 3 | LIVE-HELD (live trade of the book still open: exit cascade) | StateCut | -2612 |
| A | A7 | 2026-11-03 20:36:00 | -1 | 1 | EXIT-CASCADE (engine position still open / differently timed exit) | Target | 1199 |
| A | A7 | 2026-11-03 20:40:00 | -1 | 1 | EXIT-CASCADE (engine position still open / differently timed exit) | PolicyCut | -851 |
| A | A7 | 2026-11-04 00:24:00 | 1 | 1 | EXIT-CASCADE (engine position still open / differently timed exit) | ThL2Cut | -521 |
| A | A7 | 2026-11-04 00:31:00 | 1 | 1 | EXIT-CASCADE (engine position still open / differently timed exit) | Target | 1199 |
| A | M7 | 2026-11-04 03:05:00 | 1 | 1 | EXIT-CASCADE (engine position still open / differently timed exit) | Target | 1199 |
| B | P7 | 2026-11-04 07:43:00 | -1 | 5 | LOCK-STATE (live BookLock earlier) | Target | 5999 |
| B | P7 | 2026-11-04 08:05:00 | -1 | 2 | LOCK-STATE (live BookLock earlier) | StopJoin | -2337 |
| A | K7 | 2026-11-04 11:06:00 | -1 | 1 | LOCK-STATE (engine day/week halt) | ThL2Cut | -656 |
| A | K7 | 2026-11-04 11:24:00 | -1 | 1 | LOCK-STATE (engine day/week halt) | Target | 1199 |
| B | P7 | 2026-11-04 11:24:00 | -1 | 3 | LOCK-STATE (live BookLock earlier) | Target | 3591 |
| A | K7 | 2026-11-04 11:45:00 | 1 | 1 | LOCK-STATE (engine day/week halt) | Target | 1199 |
| A | K7 | 2026-11-04 12:27:00 | 1 | 1 | LOCK-STATE (engine day/week halt) | PolicyCut | -651 |
| A | K7 | 2026-11-04 13:39:00 | -1 | 1 | LOCK-STATE (engine day/week halt) | Target | 1199 |
| A | K7 | 2026-11-04 14:09:00 | 1 | 1 | LOCK-STATE (engine day/week halt) | ThL2Cut | -586 |
| A | K7 | 2026-11-04 14:33:00 | -1 | 1 | LOCK-STATE (engine day/week halt) | PolicyCut | -606 |
| B | P7 | 2026-11-04 19:39:00 | -1 | 4 | LIVE-HELD (live trade of the book still open: exit cascade) | Target | 4785 |
| A | P7 | 2026-11-04 21:42:02 | 1 | 4 | EXIT-CASCADE (engine position still open / differently timed exit) | PolicyCut | -2625 |
| B | K7 | 2026-11-04 22:03:00 | -1 | 1 | LIVE-HELD (live trade of the book still open: exit cascade) | StateCut | -745 |
| B | K7 | 2026-11-04 22:45:01 | -1 | 1 | LIVE-HELD (live trade of the book still open: exit cascade) | Target | 1199 |
| B | M7 | 2026-11-05 03:17:00 | 1 | 2 | LIVE-HELD (live trade of the book still open: exit cascade) | StateCut | -1134 |
| A | M7 | 2026-11-05 03:41:00 | 1 | 1 | EXIT-CASCADE (engine position still open / differently timed exit) | ThL2Cut | -641 |
| A | P7 | 2026-11-05 04:01:00 | 1 | 4 | EXIT-CASCADE (engine position still open / differently timed exit) | ThL2Cut | -2770 |
| A | M7 | 2026-11-05 07:24:00 | -1 | 1 | EXIT-CASCADE (engine position still open / differently timed exit) | Target | 1199 |
| B | M7 | 2026-11-05 07:30:00 | -1 | 1 | LIVE-HELD (live trade of the book still open: exit cascade) | Target | 1199 |
| A | P7 | 2026-11-05 08:09:00 | -1 | 4 | EXIT-CASCADE (engine position still open / differently timed exit) | PolicyCut | -1880 |
| A | P7 | 2026-11-05 10:39:00 | -1 | 5 | SIGNAL absent (no engine signal within 5 s) | Target | 5994 |
| A | P7 | 2026-11-05 11:04:30 | -1 | 5 | SIGNAL absent (no engine signal within 5 s) | Target | 5994 |


## 2. FILL MODEL (b): engine vs live fills by order type (frozen week; the live file has one entry-average and one exit price per row, so the slice / add split exists only on the engine side)
### 2a. Entry fills: engine minus live average entry price, adverse-signed (+ = engine pays more), matched pairs, S1b-COMB engine
| row | n | mean_pts | median_pts | sd | se | p10 | p90 |
|--|--|--|--|--|--|--|--|
| entry: 1-lot single market order (A7/O7/1-lot books), lots equal | 80 | 0.33 | 0.25 | 0.96 | 0.11 | -0.25 | 1.00 |
|    of which K7 | 41 | 0.47 | 0.25 | 1.24 | 0.19 | 0.00 | 1.00 |
|    of which M7 | 15 | 0.05 | 0.00 | 0.30 | 0.08 | -0.40 | 0.40 |
|    of which A7 | 18 | 0.24 | 0.25 | 0.58 | 0.14 | 0.00 | 0.83 |
| entry: multi-lot sliced market, equal lots, no add in engine (1 lot / 2 s) | 9 | 0.06 | 0.08 | 0.32 | 0.11 | -0.20 | 0.34 |
| entry: sliced market + 30% add, equal lots (add present in engine) | 51 | 0.71 | 0.43 | 1.25 | 0.18 | -0.50 | 2.06 |
| entry: lots differ (PLAN/AMB/BAD; add timing) | 13 | 0.63 | 0.82 | 2.61 | 0.72 | -2.65 | 2.67 |
| entry: ALL matched pairs | 153 | 0.47 | 0.25 | 1.26 | 0.10 | -0.25 | 1.56 |

### 2b. Targets (resting limit; both at nominal from OWN fill average)
| row | n | mean_pts | median_pts | sd | se | p10 | p90 | live_dist_mean | eng_dist_mean |
|--|--|--|--|--|--|--|--|--|--|
| target distance from OWN fill average: engine minus live (pts; + = engine target further away) | 68 | -0.60 | 0.00 | 4.92 | 0.60 | -0.09 | 0.06 | 60.00 | 59.40 |
| target fill second: engine minus live (s) | 68 | 1.93 | 0.00 | 6.66 | 0.81 | 0.00 | 6.60 |  |  |
| target price level, engine minus live (pts, entry-avg drift included) | 68 | 0.03 | 0.25 | 5.19 | 0.63 | -0.50 | 2.00 |  |  |

### 2c. Market exits: live exit price vs the 1-s MBP-10 mid at stamp+lag (adverse pts) and the engine model
| row | n | mean_pts | median_pts | sd | se | p10 | p90 |
|--|--|--|--|--|--|--|--|
| live market cut (ThL2Cut/PolicyCut/ThL2Trail): live exit px vs 1-s mid at stamp+0 s (adverse pts) | 94 | 1.19 | 0.88 | 2.01 | 0.21 | -0.75 | 3.62 |
| live market cut (ThL2Cut/PolicyCut/ThL2Trail): live exit px vs 1-s mid at stamp+1 s (adverse pts) | 94 | 0.57 | 0.62 | 1.47 | 0.15 | -1.30 | 2.12 |
| live market cut (ThL2Cut/PolicyCut/ThL2Trail): live exit px vs 1-s mid at stamp+2 s (adverse pts) | 94 | 0.59 | 0.38 | 3.12 | 0.32 | -2.59 | 4.71 |
| live PolicyTake: live exit px vs 1-s mid at stamp+0 s (adverse pts) | 2 | 1.12 | 1.12 | 1.41 | 1.00 | 0.33 | 1.93 |
| live PolicyTake: live exit px vs 1-s mid at stamp+1 s (adverse pts) | 2 | -0.19 | -0.19 | 0.62 | 0.44 | -0.54 | 0.16 |
| live PolicyTake: live exit px vs 1-s mid at stamp+2 s (adverse pts) | 2 | -0.06 | -0.06 | 2.03 | 1.44 | -1.21 | 1.09 |
| live BookLock: live exit px vs 1-s mid at stamp+0 s (adverse pts) | 3 | 0.88 | 1.12 | 0.90 | 0.52 | 0.12 | 1.52 |
| live BookLock: live exit px vs 1-s mid at stamp+1 s (adverse pts) | 3 | 0.50 | 0.38 | 0.57 | 0.33 | 0.08 | 0.98 |
| live BookLock: live exit px vs 1-s mid at stamp+2 s (adverse pts) | 3 | 1.92 | 0.25 | 4.37 | 2.52 | -1.05 | 5.55 |
| live Stop (market at touch / native): live exit px vs 1-s mid at stamp+0 s (adverse pts) | 2 | 2.31 | 2.31 | 1.33 | 0.94 | 1.56 | 3.06 |
| live Stop (market at touch / native): live exit px vs 1-s mid at stamp+1 s (adverse pts) | 2 | 1.38 | 1.38 | 0.00 | 0.00 | 1.38 | 1.38 |
| live Stop (market at touch / native): live exit px vs 1-s mid at stamp+2 s (adverse pts) | 2 | 0.94 | 0.94 | 0.97 | 0.69 | 0.39 | 1.49 |
| engine StateCut fill vs mid at its exit second (adverse pts; model constant 0.80 on mid at decision+1 s) | 62 | 0.81 | 0.80 | 0.13 | 0.02 | 0.80 | 0.80 |
| engine Stop fill vs mid at exit second (adverse pts) | 5 | 1.93 | 0.75 | 2.50 | 1.12 | 0.62 | 4.33 |
| engine StopJoin fill vs mid at exit second (adverse pts) | 6 | -0.21 | -0.25 | 1.13 | 0.46 | -1.31 | 0.94 |
| engine StopJoinFallback fill vs mid at exit second (adverse pts) | 6 | -1.55 | 0.40 | 4.97 | 2.03 | -5.78 | 0.75 |
| engine BookLock fill vs mid at exit second (adverse pts) | 3 | 1.67 | 1.62 | 1.19 | 0.69 | 0.72 | 2.62 |

### 2d. Stops: adverse distance from entry average minus the 60-pt nominal
| row | n | mean_pts | median_pts | sd | se | p10 | p90 |
|--|--|--|--|--|--|--|--|
| live Stop/BookLock exits: adverse distance from entry avg minus 60 nominal (pts) | 5 | -14.28 | -17.25 | 35.98 | 16.09 | -50.68 | 22.10 |
| engine Stop: adverse distance from entry avg minus 60 nominal (pts) | 5 | 13.50 | 14.50 | 7.89 | 3.53 | 5.43 | 19.95 |
| engine StopJoin: adverse distance from entry avg minus 60 nominal (pts) | 6 | -2.17 | -2.06 | 2.43 | 0.99 | -4.56 | 0.12 |
| engine StopJoinFallback: adverse distance from entry avg minus 60 nominal (pts) | 6 | 1.71 | 0.17 | 5.75 | 2.35 | -2.19 | 7.15 |

### 2e. 1-lot market entries vs mid
| row | n | mean_pts | median_pts | sd | se | p10 | p90 |
|--|--|--|--|--|--|--|--|
| live 1-lot entries (all books): entry px minus 1-s mid at stamp+1 (adverse pts) | 105 | 0.38 | 0.38 | 1.70 | 0.17 | -1.25 | 1.83 |
| engine 1-lot entries (same pairs): entry px minus mid at its fill second | 80 | 0.69 | 0.62 | 2.03 | 0.23 | -1.00 | 1.75 |
| live 1-lot entries (same pairs): entry px minus mid at stamp+1 | 80 | 0.36 | 0.31 | 1.84 | 0.21 | -1.26 | 1.75 |

### 2g. Dollar size of the drift on this sample (sample = frozen week; not a weekly rate)
| item | n | usd |
|--|--|--|
| entries (matched pairs): engine pays more than live, $ over the sample | 153 | 4226 |
| market cuts: engine model 0.80 pt minus live adverse vs mid (stamp+1), $ over the sample (+ = engine more pessimistic) | 94 | 1090 |

### 2f. Engine-only: individual fills by kind (slice vs 30% add), fill minus the trade average (signed with side)
| kind | n | mean_fill_minus_avg |
|--|--|--|
| add | 78 | -2.74 |
| slice | 287 | 1.01 |


## 3. Reading
- Exit differences, not entries, carry the P&L gap: 153 matched pairs differ by -56k engine minus live; pairs where the live target was hit but the engine had cut (-38k, n=4) and live cuts that the engine stopped out or let run (see 1f) dominate; class A/B trades net -12.6k / +17.7k. The 68 target-target pairs still differ by -17.7k: 8 pairs with unequal lots (add timing) and engine StackCut partials (K7 stop -> cut 4 of 7 P7 lots at 11-03 01:38) that the live book did not have.
- The entry drift is an engine pessimism of about 0.3-0.7 pt per entry, mostly the 30% add (market add after a >= 3 pt dip + one L2 confirmation, fills at the confirmation second); the live add fills closer to the signal price. Candidate fix to test on Monday's file (not applied; would be fitting to one week): add fill at the L2 confirmation price instead of one engine second later.
- Engine sample sizes: all tables are one week (187 live rows, 153 pairs, 94 live market cuts, 68 targets, 2 stops, 0 joins).

## 4. Monday acceptance procedure (c)
See R13_INSTALLED_PANEL.md. One command: `python3 -I code/th_r13/monday_acceptance.py --live <csv> --start "2026-11-08 18:00" --end "2026-11-13 17:00" --label W46`. Output ACCEPTANCE.md: entry match, exit match (same class, within 5 s), mismatch classes, fill drift by order type with n, P&L difference by cause (class A / class B / pair exit-class differs / pair same class / bug-exit pairs excluded), bug-exit exclusions with same-book followers flagged. Prerequisite not on the box: the week's NQ tape (hist day files + 1-s state arrays); the script lists what is missing.
Bug exits to exclude: the 10 v1.5 state cuts of the night 11-08/09 (1 H7 + 9 M7; ES/RTY depth pollution fixed in v1.5a): rule used = live H7/M7 cut exits in the window 11-08 18:00 .. 11-09 09:00 ET (assumed window; the user's list replaces it).

## 5. REFIT 2026-11-22
Not a refit page: R13 has no tunable setting. Fidelity inputs to re-read on 11-22: the two Monday files (11-09 week, 11-16 week) via monday_acceptance.py.
