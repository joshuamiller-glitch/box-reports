# ENTRY_MATCH - closing the entry match of the S1-COMB engine on the live blind week (PRE-PROOF)
**Label: base = replica engine with TH-L2-S as live cell; PRE-PROOF until the user lifts it. (U) does NOT reach .85; (C) does. Nothing here lifts the S2 label.**
Prereg: autopilot/ENTRY_MATCH_PREREG.md (sha line in DECISIONS.md); code code/entry_match/ (copy of replica/, th_redo/, hist_pipe/ with EM_* switches + em_core.py, match.py, em_run.py, em_census.py, em_chain.py, mk_report.py); private tree /mnt/l2/l2vast/_entry_match/ (runs/, logs/); seal ds3_all_ea/manifest_after.json sha256 759f2258daac9d28 before and after (unchanged); live file sha 424c68da...a927112 (187 rows), DS7.cs sha 54697597...; the headline run never reads the live file.

## 1. Metrics (exact; fixed in the prereg before the iterations marked "registered")
- Entry stamp: live entryTime (ET, second); engine floor((first fill ns - 1.0 s)/1e9) = order second. Match = same book, same side, |dt| <= 2 s, one-to-one (smallest |dt| first). Outage window Tue 02:55-08:20 ET excluded on both sides (no live entry inside; no engine entry inside).
- Lots of a matched pair (live qty vs engine FILLED and PLANNED lots): EQ filled equal; PLAN planned lots = live qty but fills differ (the 30 % add / 1-lot slice timing; sizing logic agrees); AMB the smaller equals the 70 % first tranche of the larger; BAD otherwise.
- **U** = matched / (nL + nE - matched) on the S1-COMB blind-week run. U_nolots (any lots), U_strict (EQ only), **U_main (EQ+PLAN+AMB)**.
- **C** (DIAGNOSTIC, labelled; reads live exit times/prices/P&L and the live entry stamps): engine ENTRY logic with the book states driven by the live exits: engine exits/cuts/locks-exits switched off; an engine entry within +-2 s/same side of an unclaimed live trade claims it and is closed at the live exit second/price; engine signals while a live trade of that book is open (outside +-2 s of its entry) are blocked; an engine entry with no live trade to claim is an EXTRA entry (kept open with the engine's own stop/target, zero P&L, force-closed 3 s before the next live entry of that book); book realized P&L for day/week locks = live net P&L - 1.18 USD x qty, injected at the live exit for claimed AND unclaimed live trades (C2); C3 = C2 + the lock peak uses the live qty of the claimed trade (shows the lock rule is right once lots are right).

## 2. Results per iteration (S1-COMB blind week, 187 live rows; matched / U_main / U_nolots; extras and live-only in brackets)
| iteration | U (unconditional, S1-COMB) | C2 (live exits drive the books) | note |
|--|--|--|--|
| R0a S1 base as built (hist adapter, settled config, PERIODS off, 10 warm days) | 136 / **.556** / .604 (38 / 51) | - | the earlier "about 100 of 187" was not reproduced exactly with this metric (its criterion is not documented) |
| R0a + tick close | 137 / .575 / .617 (35 / 50) | - | |
| R0b ITER14_PRM period facts on the original arrays (engine = headline u5 + state cut) | 148 / **.662** / .685 (29 / 39) | 176 / .828 / .854 (19 / 11) | HOLD (old cut) U_main .724 |
| exploration before prereg: F1 BAR_CLOSE=tick (NT8 closes a bar on the first tick of the next bar) | 150 / .695 / .711 (24 / 37) | 181 / .863 / .900 (14 / 6) | stamps exact in 176 of 181 pairs (timer: 153); the 28 early stamps were quiet minutes |
| exploration: slice gap 100/200/500 ms (timer close) | - | 500 ms: 176 / .862 (15 / 11); with all final switches 500 ms: 184 / .933 / .953 (6 / 3) | NOT adopted (see 4) |
| exploration: bar-series back-fill instead of hole | - | 179 / .841 (15 / 8) | rejected, hole kept |
| F2 v1.3 TrendSize half-even rounding before Mon 13:30 ET (user-stated observation P7 Sun 19:11 = 10 lots) | = | = (planned 11 -> 10, lots chain agrees) | adopted |
| F7a X3/X4 bars break at the session open (NT8 break-at-EOD) | - | 183 / .873 / .910 (14 / 4) | both X4 live entries match to the second (02:21:06, 04:39:15) |
| F7b Range bar closes when range >= 32 ticks | - | 184 / .882 / .920 (13 / 3) | X3 08:31:06 matches to the second; 08:37:26 and 08:38:41 still match |
| F7c extras held with the engine's own bracket (not closed after 1 s) | - | 184 / **.896** / .934 (10 / 3) | removes the cluster artefact |
| **FINAL U** (all switches; S1-COMB / S1-UNIF / S1-LIVE / HOLD) | **153 / .719 / .736 (21 / 34)**; UNIF 147 / .702 / .728; LIVE 137 / .644 / .668; HOLD 174 / .776 / .809 | - | |
| **FINAL C2** | - | **184 / .896 / .934 (10 / 3)**; strict .780 | |
| FINAL C3 (lock peak with live qty) | - | 184 / **.914** / **.953** (6 / 3); strict .795 | the 4 P7 post-BookLock extras vanish |
| C1 (no live P&L injection, engine P&L only) | - | 166 / .806 / .843 (10 / 21) | the lock/day-cap states need the live P&L path |
| BIP order asc / desc (sensitivity of F1-F7 final) | - | asc .859 (bad lots 8), desc .873 | default five_first kept |
Sensitivity sets are not selected on the metric except where marked adopted; adopted = F1, F2, F7a-c. F7a/b/c were chosen on live entries of 3 X books (7 live rows) and F1 on 186 stamps: both are convention choices with exact-second evidence, not tuning knobs, but they ARE evidence read from the live file.
**Regression (all switches off):** HOLD = 201 trades, +55,890.00, trade-for-trade identical to runs/u5 (iter14 headline); S1-COMB all-off = the unmodified R0b trade list (177 trades) identical.

## 3. Verdict against the bar
- **(U) .85 is not reachable from the owned tape**: best U on the S1-COMB run is .719 (U_nolots .736); the better cut proxies do not reach it (HOLD old per-print cut .776). The user's own statement stands: the live cut is a feed artefact.
- **(C) is reached**: C2 U_main .896 (nolots .934), C3 .914 (.953), every pre-registered metric >= .85 except the strict-lots variant (.780/.795), whose gap is the add timing (section 4).
- **Share of the 55 U mismatches (34 live-only + 21 engine-only) by first divergence**: 35 (64 %) lie in chains rooted at a different exit/cut (19 roots below); 13 (24 %) are lock states derived from P&L paths that differ (10 engine day/week halts: K7 Tue 10:57/11:33, K7 Wed 11:06-14:33, P7 Thu 10:39; 3 engine entries after the live P7 BookLock 07:25:04, which needs the live lots) = 48 of 55 (87 %) trace to the exit/cut path or to P&L/lots that depend on it; 7 (13 %) are raw-signal differences (4 absent, 3 extra; section 5). Of 153 matched pairs 83 have exits >5 s apart (70 agree).
- Pairs: sizing chain (session table x ER ladder x SS x NTZ) planned lots = live qty in **177 of 184** matched pairs (C2); filled lots equal in 167. SS slots/NTZ/session tables/ER ladder/EntriesPerDirection/day caps/week floor/U7 blackout/ExitPending: no mismatch traced to them in C2 (the 7 non-agreeing sizes are add-gate cases). Locks: CheckLimits +5R/-2R, give-back arm +2R keep 50 %, SizeMult in BookR, 1.18 RT in lock accounting, week roll: the K7 day-loss cap states and the P7 BookLock reproduce when the P&L path and lots are live (C2/C3); with engine P&L only (C1) 21 live entries are lost to the cap cascade.
- Signal second: after F1 the 181 pairs found at a 6-s tolerance are 176 exact and 5 at -1 s, vs 153 exact with timer closing (28 pairs with the engine stamp 1-4 s early). P7 PB3B 45-s confirm times (:15/:30/:45) match to the second. BIP order five_first confirmed (asc/desc worse in lots only).

## 4. Findings about the port (C# facts)
- Bar closes: NT8 closes a time bar on the first tick of the next bar (P9_NT8_SPEC line 10 says the entry call is the first tick after the bar closes); engine switch BAR_CLOSE=tick (already a pre-registered convention of the engine). **Port to the base: set BAR_CLOSE='tick' in state_base._prm()/HIST_PRM; it is the only F-switch that matters for the history months (X books are off there); re-running the 43 months is a separate order (not started here).**
- Reserve add (L2Pump/L2AddStage): the C# drops unsent 1-lot slices when the add confirms (SlicesSent = Qty, v2.1c) and routes an add that confirms before the first fill callback through SubmitEntry because InTrade needs PosQty > 0; the port does both literally. Live reaches full lots where the engine's gates confirm in 1.2-2 s (PLAN 11 pairs) and sometimes does not add where the engine does (AMB 2, BAD 2 of 4). Mean |avg entry diff| of 63 pairs with equal lots: 0.93 pt at the C# default 2000 ms slices vs 1.43-1.46 pt at 100-500 ms, so the slice gap is NOT changed; at 500 ms C2 would read .933 (lots BAD 2). The remaining lots gap is DOM-state/callback timing, not a sizing rule.
- L2 list caps (Imb/Depth 5000 -> 2500) are not modelled and were not tested: they can only matter above ~80 Last events per second.

## 5. Per-trade table of remaining mismatches (C2 FINAL; times ET)
### C2 lots: matched pairs whose lots differ (17)
| kind | book | live_t | live_q | eng_q | cause |
|--|--|--|--|--|--|
| PAIR-PLAN | M7 | 11-02 08:20:00 | 3 | 2 | PLAN: add confirmed within the 1-lot slice schedule; unsent slices dropped (C# L2AddStage SlicesSent=Qty); sizing agrees (planned 3) |
| PAIR-BAD | P7 | 11-03 10:46:30 | 4 | 2 | BAD (port-faithful race): add confirmed 0.9 s after the entry, before the first-fill callback (InTrade needs PosQty>0) -> SubmitEntry path, planned 1; needs the NT8 fill-callback latency (engine 1.0 s) |
| PAIR-AMB | K7 | 11-03 18:39:00 | 1 | 2 | AMB: live reserve add did not fire, engine add fired (8-gate state from the NT8 DOM vs mbp-10) |
| PAIR-PLAN | P7 | 11-03 18:56:01 | 4 | 2 | PLAN: add/slice timing (planned 4 = live 4) |
| PAIR-PLAN | P7 | 11-03 21:56:00 | 4 | 2 | PLAN: add/slice timing |
| PAIR-PLAN | U7 | 11-04 00:00:00 | 4 | 2 | PLAN: add/slice timing |
| PAIR-PLAN | P7 | 11-04 00:30:00 | 7 | 3 | PLAN: add at 1.9 s drops 3 unsent slices (live 7 = all slices + add after 8 s or no early add) |
| PAIR-PLAN | P7 | 11-04 00:53:00 | 7 | 3 | PLAN: add/slice timing |
| PAIR-PLAN | P7 | 11-04 01:31:01 | 7 | 3 | PLAN: add/slice timing |
| PAIR-PLAN | P7 | 11-04 03:36:00 | 4 | 2 | PLAN: add/slice timing |
| PAIR-PLAN | M7 | 11-04 06:00:00 | 1 | 2 | PLAN/race: add before the first-fill callback (planned 1, filled 2); live 1 = no add |
| PAIR-AMB | U7 | 11-04 07:10:00 | 1 | 2 | AMB: live reserve add did not fire, engine add fired |
| PAIR-BAD | P7 | 11-04 07:25:00 | 5 | 3 | BAD: live no add (5 = first tranche), engine add early (slices dropped, filled 3) |
| PAIR-PLAN | P7 | 11-05 02:53:04 | 7 | 5 | PLAN: add/slice timing |
| PAIR-PLAN | P7 | 11-05 04:01:00 | 4 | 3 | PLAN: add/slice timing |
| PAIR-BAD | P7 | 11-05 08:09:00 | 4 | 2 | BAD (race): add 0.9 s after entry, before first-fill callback -> SubmitEntry path, planned 1 |
| PAIR-BAD | P7 | 11-05 10:39:00 | 5 | 3 | BAD: live no add (5 = first tranche), engine add early (filled 3) |

### C2 live-only entries (3)
| book | live_t | live_q | live_exit | cause |
|--|--|--|--|--|
| M7 | 11-02 10:02:00 | 1 | ThL2Cut | raw signal absent: MV net vote -3 at 10:02 (L15 z -0.66, L30 -0.23, L60 -0.71, L120 -0.09, L240 -0.57); the 4th vote needs L30 z <= -0.5; engine 4-vote signals at 09:57 only. Feed/bar-close difference at the 10:00 ISM release (recv/event clock differs in 19 of 5165 minutes, none here) |
| K7 | 11-02 10:36:00 | 1 | PolicyCut | raw signal absent: engine Keltner already above the upper band at 10:33 by 2.32 pt (c-up), so no cross at 10:36; live needs a band >= 2.3 pt higher at 10:33 (ATR/EMA path from NT8 history bars) |
| M7 | 11-02 11:21:00 | 1 | Target | raw signal timing: engine MV signal fires at 11:17 (net -4), live 11:21 (engine -3 at 11:21); paired with the engine-only 11:17 below |

### C2 engine-only (extra) entries (10)
| book | eng_t | eng_q | cause |
|--|--|--|--|
| X3 | 11-02 08:45:00 | 2 | X3 Range-32 Keltner signal after the three live X3 trades (08:31-08:43); live none: X3 range-bar/Keltner internals unknown (unknown input) |
| M7 | 11-02 11:17:00 | 1 | raw signal timing (see live-only M7 11:21) |
| K7 | 11-03 08:21:01 | 1 | Tue 08:20 reconnect edge: engine bar-series hole model gives a K7 Keltner flip at 08:21; live took M7/U7 at 08:20:00 (exits 08:26:42/44) and then no K7/M7/P7 entry until P7 10:20:15 (only O7 09:41) (NT8 reconnect handling unknown) |
| M7 | 11-03 08:27:00 | 1 | Tue reconnect edge (same) |
| H7 | 11-03 11:00:00 | 1 | H7 5-min HMA/VWAP cross (Hm5) in engine, none live: raw signal difference (feed/history) |
| P7 | 11-03 19:15:00 | 4 | P7 PB3B signal in engine, none live (live K7 took 19:15:00, P7 did not): raw signal difference; 4 min before the 19:19 stall start |
| P7 | 11-04 07:28:00 | 7 | live P7 BookLock 07:25:04 (give-back lock); engine lock needs the live lots in the peak (C3 removes it) |
| P7 | 11-04 07:43:00 | 5 | same lock (removed in C3) |
| P7 | 11-04 08:05:00 | 2 | same lock (removed in C3) |
| P7 | 11-04 11:24:00 | 3 | same lock (removed in C3) |

## 6. U: mismatches by cause and the chain roots
### U mismatches (55) by first-divergence class
| cat | n |
|--|--|
| EXIT-CASCADE | 35 |
| LOCK-STATE (engine day/week halt) | 10 |
| LOCK-STATE (live BookLock earlier) | 3 |
| SIGNAL absent | 4 |
| SIGNAL extra | 3 |


### U mismatches not in an exit-cascade chain (20)
| book | kind | t | cat |
|--|--|--|--|
| H7 | EO | 11-03 11:00:00 | SIGNAL extra |
| K7 | LO | 11-02 10:36:00 | SIGNAL absent |
| K7 | LO | 11-03 10:57:00 | LOCK-STATE (engine day/week halt) |
| K7 | LO | 11-03 11:33:00 | LOCK-STATE (engine day/week halt) |
| K7 | LO | 11-04 11:06:00 | LOCK-STATE (engine day/week halt) |
| K7 | LO | 11-04 11:24:00 | LOCK-STATE (engine day/week halt) |
| K7 | LO | 11-04 11:45:00 | LOCK-STATE (engine day/week halt) |
| K7 | LO | 11-04 12:27:00 | LOCK-STATE (engine day/week halt) |
| K7 | LO | 11-04 13:39:00 | LOCK-STATE (engine day/week halt) |
| K7 | LO | 11-04 14:09:00 | LOCK-STATE (engine day/week halt) |
| K7 | LO | 11-04 14:33:00 | LOCK-STATE (engine day/week halt) |
| M7 | LO | 11-02 10:02:00 | SIGNAL absent |
| M7 | EO | 11-02 11:17:00 | SIGNAL extra |
| M7 | LO | 11-02 11:21:00 | SIGNAL absent |
| M7 | EO | 11-03 08:27:00 | SIGNAL extra |
| P7 | EO | 11-04 07:43:00 | LOCK-STATE (live BookLock earlier) |
| P7 | EO | 11-04 08:05:00 | LOCK-STATE (live BookLock earlier) |
| P7 | EO | 11-04 11:24:00 | LOCK-STATE (live BookLock earlier) |
| P7 | LO | 11-05 10:39:00 | LOCK-STATE (engine day/week halt) |
| P7 | LO | 11-05 11:04:30 | SIGNAL absent |

### U chain roots (19 chains rooted at a different exit; 35 descendant mismatches)
| book | root_t | n_desc | live_exit | live_exit_t | eng_exit | eng_exit_t | dx |
|--|--|--|--|--|--|--|--|
| A7 | Sun 11-01 20:12:00 | 2 | ThL2Trail | 11-01 21:54:37 | Target | 11-01 22:25:05 | 1828 |
| A7 | Tue 11-03 20:32:00 | 2 | PolicyCut | 11-03 20:35:04 | Target | 11-03 20:40:41 | 337 |
| A7 | Wed 11-04 00:17:00 | 2 | PolicyCut | 11-04 00:21:54 | Target | 11-04 00:43:25 | 1291 |
| K7 | Mon 11-02 20:09:00 | 1 | PolicyCut | 11-02 22:36:58 | StateCut | 11-02 20:11:24 | -8734 |
| K7 | Sun 11-01 22:48:00 | 3 | ThL2Cut | 11-02 01:20:34 | StopJoinFallback | 11-02 02:33:47 | 4393 |
| K7 | Tue 11-03 01:21:00 | 1 | ThL2Cut | 11-03 01:30:05 | StopJoin | 11-03 01:38:12 | 487 |
| K7 | Tue 11-03 01:48:01 | 1 | Stop | 11-03 02:55:35 | StateCut | 11-03 01:50:19 | -3916 |
| K7 | Wed 11-04 21:51:00 | 2 | Target | 11-04 22:53:11 | StateCut | 11-04 21:58:36 | -3275 |
| M7 | Mon 11-02 06:58:00 | 1 | PolicyTake | 11-02 08:05:20 | Target | 11-02 08:31:33 | 1573 |
| M7 | Thu 11-05 02:53:04 | 2 | Target | 11-05 03:17:20 | StateCut | 11-05 03:03:54 | -806 |
| M7 | Thu 11-05 05:08:00 | 2 | ThL2Cut | 11-05 07:22:47 | StateCut | 11-05 07:25:08 | 141 |
| M7 | Wed 11-04 02:18:00 | 1 | Target | 11-04 03:04:42 | Target | 11-04 03:05:18 | 36 |
| P7 | Mon 11-02 18:47:01 | 1 | PolicyCut | 11-02 20:29:16 | StateCut | 11-02 21:13:39 | 2663 |
| P7 | Sun 11-01 19:11:03 | 9 | Target | 11-01 20:25:34 | StateCut | 11-01 19:31:26 | -3248 |
| P7 | Thu 11-05 03:33:02 | 1 | ThL2Cut | 11-05 03:48:37 | StateCut | 11-05 04:02:53 | 856 |
| P7 | Thu 11-05 07:58:00 | 1 | PolicyCut | 11-05 08:04:52 | StateCut | 11-05 08:43:59 | 2347 |
| P7 | Tue 11-03 18:13:03 | 1 | PolicyCut | 11-03 18:37:42 | StateCut | 11-03 18:34:42 | -180 |
| P7 | Wed 11-04 19:27:00 | 1 | Target | 11-04 19:57:29 | StateCut | 11-04 19:31:40 | -1549 |
| P7 | Wed 11-04 21:31:00 | 1 | ThL2Cut | 11-04 21:34:08 | StateCut | 11-04 21:50:15 | 967 |

## 7. Inputs still unknown (cannot be closed from the owned tape)
1. Saved slice gap (StSliceGapMs/HmSliceGapMs), NT8 fill-callback latency (engine 1.0 s) and the NT8 DOM/event ordering behind the 8 add gates: they decide whether the 30 % add lands in 1-2 s or later (11 PLAN + 4 BAD + 2 AMB pairs).
2. The live per-print cut (feed artefact): 35 + 13 of 55 U mismatches.
3. Reconnect behaviour of NT8 on Tue 08:20 (hole vs back-fill vs catch-up; K7 08:21 and M7 08:27 are engine-only, live silent 08:27-10:20 except O7) and the exact stall starts (02:10 / 19:19 used).
4. NT8 history bars vs tape bars near data releases (M7 10:02 and 11:21, K7 10:36, H7 Tue 11:00, P7 Tue 19:15, X3 08:45 internals).
5. v1.3 saved panel for the old period (TrendSize rounding adopted from one observation; ER thresholds; OTE/NTZ/SS panel values), the live commission schedule (1.18 RT used).
6. X books: lots/brackets and the Keltner/range internals after 08:38 (7 live rows; 1 mismatch left in C2: X3 08:45).

## 8. Files / reproduction
python3 -I code/entry_match/em_run.py LABEL BASE [drive=1] [BAR_CLOSE='tick' EM_TR_OLD='round' EM_XBREAK=1 EM_RANGE_GE=1 EM_LOCKLIVEQTY=1 EM_LIVEPNL=False EM_SLICE_MS=2000]; BASE in HOLD, S1-COMB, S1-UNIF, S1-LIVE, NOCUT. Final switch set = "BAR_CLOSE='tick' EM_TR_OLD='round' EM_XBREAK=1 EM_RANGE_GE=1". Runs: /mnt/l2/l2vast/_entry_match/runs/{u_comb,u_hold,u_live,u_unif,fin_c2,fin_c3,fin_c1,fin_sl500,reg_hold,reg_comb,...}. em_census.py LABEL (pair table), em_chain.py LABEL [refine|roots], rescore.py LABELS.
Disclosure: R0b, F1, the slice-gap and back-fill sensitivities and the first F7 runs were scored before the prereg sha line existed (listed above as exploration); the final switch set, the extras-hold rule (F7c) and C3 were added after reading C2 results and are reported with the same status.
