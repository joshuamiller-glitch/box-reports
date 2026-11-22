# FAST_LADDER - make the ladder engine sets faster without cutting a candidate (W-FASTLADDER, order 0633Z)
written 2026-11-19 07:2xZ, revised 07:55Z (revision B added; refreshed as the identity test advances). Research only. Prereg: PREREG_FAST_LADDER.md sha256:da0a1a9c1134b4f3 (DECISIONS.md 06:32Z). Nothing is switched: no queue uses FL_FAST until the lead decides after identity passes on >= 200 set-months.

## 1. Profile (where one ladder set-month goes)
Method: one set-month run in-process through the production exact path (jn05_run2 header, JointRep + hook chain, TP month cache) under cProfile and without a profiler; harness = code/th_fastladder/profdrv.py; harness output equals the production result in runs_rf trade for trade (cmp 1e-9; tested on 3 production results).
Asia ADD TL3_ASI_L753bf92a_ADD 202608: 7.52 M prints, plain run 236 s wall / 229 s CPU (box 1 at load 70/32). NY AM RK7 TL3_NYE_L01811caa_RK7 and RP7 profile the same way (497 / 500 s under cProfile, 7.52 M prints, 5.3-5.7 M with a book in trade).
| share of the profile (before patches) | what |
|---|---|
| 75 % | sim.Replica.on_print (per print, 8 books) incl. the manage_th_l2 hook chain: ev_profit > ec_hooks > wb_hooks > state_base_b > rules_replica > adapter_replica > sim, 34 % |
| 19 % | adapter_replica._rule_call: the TH-rule probe wrapper, run at EVERY print and book (10 M calls) although the base routine it wraps is gated to once per second |
| 8-15 % | i_mixin._feat -> i_feat.build: 240-253 calls, 160-290 ms each (pandas strftime 86 ms per call; 720 np.load of the same 3 compressed core_bars npz) |
| 16 % | on_1m (bar handlers, r5/swb hooks) |
| 5 % | fixed per-process cost: module imports 7.6 s (i_feat module init 7.2 s), Bars5 / trading_day (255 k calls) |
| 0 % | month data loading: the mmap cache (tp_patch) already removed it. The cost is the stack replay itself, repeated in full for every set. |

## 2. What was built: exact-by-construction patches (code/th_fastladder/fl_patch.py; in memory only; opt in FL_FAST=1 through fl_launch.py; FL_OFF=name disables one)
| patch | change | why it is exact |
|---|---|---|
| P1/P2 rulecall | adapter RuleReplica.manage_th_l2 / manage_policy skip the probe wrapper when the base routine (sim.Replica) is gated off at this print (thr_block / pol_rules None / exit pending / policy triggered); cells with ext==2 always take the original path | the wrapper's tail only acts on a wish or an evaluation; when the gated base returns at once, the wrapper leaves no trace (probe, TH and rules restored; nprobe counter unused) |
| P3 onprint | sim.Replica.on_print with the Book.in_trade property inlined (side != 0 and pos_qty > 0), same loops and order | same expression |
| P4 strftime | DatelikeOps.strftime('%Y%m%d') from year/month/day | same 8-digit strings |
| P5 tdmemo | r13_rules.trading_day memoised per UTC hour | ET offsets are whole hours: the +6 h ET date can only change on a whole UTC hour |
| P6 npzmemo | np.load of _th_fd/core_bars/*.npz cached in the process, arrays shared read-only | same arrays; a write by a caller would raise, not corrupt |
| P7/P8 scopememo | RuleReplica3 rule-constant tests (A_KEYS, MY_KEYS, l2loss...) evaluated once per run; _scope memoised per (tag, entry_session, entry_ns) | the rule dict is constant during a run |
Measured (same set-month, same host, plain, no profiler, box 1 at load ~70): Asia ADD 202608: production path 229 s CPU -> 148.6 s CPU = **1.54x**, trades parquet identical to the production result.


## 2b. Revision B (opt in FL_NEXT=1 on top of FL_FAST=1; code/th_fastladder/fl_patch_next.py; identity-tested separately)
| patch | change | why it is exact |
|---|---|---|
| P9 featcache | i_mixin._feat -> i_feat.build result cached per host (sqlite, WAL), key (signal second, side) + version token (sha of i_feat.py + mtimes of its input files); a hit also skips the i_feat module init | build is a pure function of (second, side) [ATR5 = 15, ENTRY = second are constants in the call]; hit rate 240/240 on a rerun; cached row .equals() the computed row |
| P10 chainskip | after the manage_th_l2 / manage_policy hook chain has run for a book and left its gates closed (ThL2 evaluated or blocked, policy inert or blocked), later prints of the same gate window skip the whole chain unless the price touches one of the two per-print thresholds (th_l2_trail_px, ev_profit lock level) | audit of the 7 chain layers: ev_profit / ec_hooks / wb_hooks / state_base_b advance only when the 1-s sample index (now-1)//NS advances; base routines are gated by thr_block (gap mode: now - last < 1 s); policy returns at its gate before its trail check; chain classes outside the audited set or a rule with l1loss / l2loss / policy_profit keys disable the skip for the run. VERIFY mode (FL_VERIFY=1) ran the chain anyway on 141,650 sampled skippable prints of one month and compared book, layer-state, cuts, log, heap and trades signatures: 0 changes |
| P11 lockskip | per-2 s check_book_lock skipped for a book that is not in a trade when its P&L inputs and peaks are unchanged since its last check | unreal = 0 for a flat book, so the routine is a pure function of those inputs and a repeat call is a no-op; only when no 'lock' rule and cde code != 5 |
Measured Asia ADD 202608, plain, same host: production 229 s CPU -> rev A 148.6 s (1.54x) -> rev B 99.8 s (**2.3x**); trades parquet identical to the production result for every run (rev A 52 of 52 on the sample so far).
Profile after rev B (cProfile, 211 s): on_print loops 15 %, sim.run loop 8 %, first-print-of-second chain evaluations (manage_policy / th_l2 per second per in-trade book: 1.08 M evaluations) ~25 %, check_book_lock (in-trade books) 7 %, policy_poll 4 %, match_resting 3 %, on_1m bars 8 %. What is left is the intrinsic once-per-second evaluation of every open trade plus Python call overhead.

## 3. Identity test (PREREG_FAST_LADDER)
Sample: 217 set-months, fixed seed 20261119, stratified fam (Asia / NY AM) x kind (ADD, RA7, RK7) x month load (tercile of trades) + 25 months with a DayHalt exit, 25 with >= 5 StackCuts, 15 with a BookLock (sample file /mnt/l2/l2vast/_fastladder/sample.json). Reference = the production exact result already in runs_rf (no candidate re-scored). Criterion: same row count, columns, every int equal, floats equal to 1e-9. A mismatch is published and re-run on the unpatched path to tell a stale reference from a patch bug. Runner: id_run.py (6-8 procs on box 1 at nice 5; output runs_fl_id_fast/, results id_results_fast.csv). Status: see section 6.

## 4. The order's item 2 lever: baseline-stack cache + replay only the delta (scoping, requested 07:1xZ)
(a) Is it exactly reproducible in this engine? Structure: one Replica, ONE per-print loop, 8 books (K7 P7 M7 U7 H7 A7 O7 + the injected MF1/new book) in blist; Book objects hold their own P&L, day halt and week halt, BookLock (check_book_lock is per book, own day P&L). The books are coupled only through: (1) stack_on_stop (a stopped book entered in Asia cuts 50 % of every other same-side open book: StackCut), (2) hook-layer aggregates that read all books: DAY-DONE / SCR gate (closes today >= 22 and day <= -2R), same_side_lots_cap (cde_exact cap 6), P7 day cap panel, ctx tags that read s.trades, (3) shared market-driven state (bars, signal-state histories, trend ER) that does NOT depend on trades. A divergence rule would be: the stack equals the baseline until the first event at which the new book's state enters one of the aggregates in (1)-(2) in a way that flips a decision of another book; the new book is simulated by a shadow engine reading the baseline's recorded aggregates and, at the first flipped decision, the full exact engine resumes from a state checkpoint (fork-based) before that decision. That is reproducible in principle but needs (i) an inventory of every cross-book read in 7 hook layers + 3 injectors, (ii) the new book's own entry gates (they read the same aggregates) re-implemented against the recorded streams, (iii) checkpoint / resume. 
MEASURED value of the idea (diverge.py, prototype of the test on existing results): ADD set-months vs the baseline JL3 stack (TL3_CT_JL3_ID, same months): 200 set-months (80 Asia, 120 NY AM): the stack trajectory is identical in only 5.5 % of months (Asia 0 %, NY AM 9 %); the median first divergence is 13 % into the month (p10 2 %, p90 54 %); Asia: median first divergence 2 % into the month and 7.2 % of stack trades differ; NY AM: 26 % into the month, 0.6 % of trades differ. So the identical prefix to skip is ~13 % of the work on average, and after the first divergence the states differ although 99 % of trades match (no cheap re-convergence test). Conclusion: **the delta replay would save about 10-15 %, not 10x, and costs weeks of engine surgery with a high risk of silent inexactness: not recommended.**
(b) The identity design for the delta path would be the same as section 3 (trade for trade vs the exact engine on the same sample, DAY-DONE / StackCut / BookLock months included); the prototype on 200 set-months is the measurement above (it needs no engine change: it uses existing results).
(c) Batching option (several sets per process): fixed per-process costs are only ~5 % (imports 7.6 s, Bars5 / init ~8 s of ~335 profile-s), so batching saves <= 5 %. What IS shareable across the 7 sets of one cell-month (ADD, RA7, RK7, RP7, RM7, RH7, RU7) is i_feat.build: a pure function of (signal second, side) at 8-15 % of the CPU of every set: a per-month feature cache shared by the sets of a cell would save ~10-13 % of each of the 6 later sets on a host (cache is per host). Not built yet; exact by construction.

## 5. Outlook (honest)
Exact micro patches: 1.54x measured so far (target in the order: >= 10x). Candidates for more: i_feat.build cross-set cache (+10-13 %), fusing the 7-layer manage_th_l2 chain (state_base_b 15 s, ec_hooks 11 s, ev_profit 7 s, wb_hooks 8 s of ~335: needs a per-layer equivalence proof for each hook), the run-loop (min over 3 candidates per event, 18 s) -> maybe 1.8x in total. A real 10x needs a compiled (numba / C++) per-print core with the hook logic ported and identity-tested against the Python engine: weeks. The cheaper levers are the ones Josh already controls: engine workers (A/B cap 38 -> 70 measured +72 %) and the ORDER of work (Asia / NY AM first, candidates that beat the live book first); more machines add rate 1:1.

## 6. Status log
- 07:50Z: rev A identity: 52 of 52 identical (sample items 0-51 of 217; runner stopped to switch to rev B). Rev B (P1-P11, hashes in id_results_fastb.csv) identity on all 217 started 07:50Z, 8 procs at nice 5 on box 1 (MemAvail 50 GB), ETA ~09:30Z; results: /mnt/l2/l2vast/_fastladder/id_results_fastb.csv
- 07:17Z: P1-P8 1.54x on Asia ADD 202608; identity batch 1 (24 cases, older patch revisions): 15 of 15 finished identical; batch 2 (193 cases, final revision sha 819eaa97...) started 07:17Z, 4 procs.

<!--FLSTATUS-->
## 7. Identity status (auto, 13:50Z)
- rev A (P1-P8): 52 identical of 52 tested (failures: 0)
- rev B (P1-P11): 217 identical of 217 tested of 217 sample set-months (runner alive: yes); mean CPU per set-month in the test (contended host) 120 s
  - ASI ADD identical: 44
  - ASI RA7 identical: 38
  - NY ADD identical: 72
  - NY RK7 identical: 63
<!--/FLSTATUS-->
