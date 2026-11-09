# ENTRY_MATCH_PREREG - registration of the entry-match metrics and the iteration plan (PRE-PROOF, 2026-11-08)
Label: base = replica engine with TH-L2-S as live cell; entries not live-matched (until this program lifts it); PRE-PROOF.
Disclosure (honest order of events): the tool was built and iteration 0 plus three exploratory sensitivities (BAR_CLOSE=tick, slice gap 100/200/500 ms, bar-series back-fill) were run BEFORE this file existed. Their numbers are reported as such in ENTRY_MATCH.md (section "exploration before prereg"). Every iteration after the sha line of this file in DECISIONS.md is registered here or in an addendum with its own sha line before it is scored.

## 1. Metrics (fixed now, not changed afterwards)
Live reference: data/live_frozen/StratTrades_DS7_<acct>_BLINDWEEK_reconstructed.csv (sha256 424c68da...a927112), 187 rows; Tue 02:55-08:20 ET entries excluded from both sides (none live; none engine). The headline engine run (U) never reads the live file. Only the diagnostic (C) reads live exit times/prices/P&L and the live entry stamps (to know when a live trade is open).
- Entry stamp: live = entryTime (ET, second). Engine = floor((first-fill ns - LAT_FILL 1.0 s) / 1e9), the order second (measured: 143 of 186 iter14 entries at exactly +1 s fill-minus-stamp, 169 within 2 s).
- Match: same book, same side, |stamp_engine - stamp_live| <= 2 s, one-to-one, smallest |dt| first.
- Lots classes of a matched pair (live qty vs engine FILLED lots; engine PLANNED lots b.qty incl. the add): EQ equal; PLAN planned lots == live qty, fill count differs (the 30 % add / 1-lot slice timing: the sizing logic agrees); AMB the smaller equals the 70 % first tranche of the larger (one side added, the other did not); BAD otherwise.
- U (unconditional) on the S1-COMB blind-week run: matched / union, union = nL + nE - matched. Reported as U_nolots (any lots), U_strict (EQ only), U_main (EQ + PLAN + AMB; the add-fill ambiguity is listed separately by class counts). Bar of the user: >= .85.
- C (conditional entry-logic fidelity, DIAGNOSTIC, labelled): the engine's ENTRY logic is replayed with the book states driven by the live exits: (i) engine exits/cuts/trails/locks-exits/stack cuts are switched off (wishes logged); (ii) an engine entry within +-2 s / same side of an unclaimed live trade claims it and is closed at the live exit second at the live exit price (engine lots); (iii) engine entries while a live trade of that book is open (outside +-2 s of its entry) are blocked (live-busy); (iv) an engine entry with no live trade to claim is an EXTRA entry, closed 1 s later at its fill price with zero P&L (it counts as an engine entry in the union); (v) book realized P&L (day/week lock accounting) = the live net P&L minus 1.18 USD x qty per live trade, injected at the live exit (for claimed and unclaimed live trades; labelled C2). Lock peaks use the engine's own open P&L and lots (no injection). C = matched / union with the same classes.
- Share of U mismatches whose first divergence traces to a different exit/cut: per mismatch, the first divergence of that book's timeline between live and engine (the busy/flat state, lots, locks, raw signal) is classified; rule written in ENTRY_MATCH.md section 5 before the numbers are read.

## 2. Iteration plan
Each switch is an EM_* / PRM key of code/entry_match/ (default = earlier behaviour); regression: all switches off reproduces HOLD 201 trades +55,890 (iter14 headline) exactly and the S1-COMB blind-week run of the unmodified copy.
- R0: baseline (S1-COMB with ITER14_PRM period facts; HOLD; C drive).
- F1 BAR_CLOSE = tick (pre-registered alternative convention of the engine; NT8 closes a time bar on the first tick of the next bar; evidence: exact-second agreement of live stamps).
- F2 v1.3 TrendSize rounding before Mon 13:30 ET (half-even, user-stated observation P7 Sun 19:11 = 10 lots).
- F3 NT8 L2 list caps (L2State.Imb/Depth 5000 -> 2500 trimming) in the add confirmation gates.
- F4 slice cadence: C# default 2000 ms kept; 100/200/500 ms reported as sensitivities only (live average entry price supports 2000 ms: mean |avg diff| 0.93 vs 1.43-1.46 pt on 63 common pairs).
- F5 signal-side checks (M7 MomentumVote, K7 Keltner, H7, X3/X4 bars) as diagnostics; no change without a C# defining reading.
- F6 locks: BookLock arithmetic on the live P&L path (replay) to separate the lock rule from the add-timing lots.
Addenda with their own sha lines are appended to DECISIONS.md before scoring.
