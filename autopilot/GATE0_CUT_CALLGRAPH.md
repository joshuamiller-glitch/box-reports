# GATE0_CUT_CALLGRAPH (ZL-4) - PRE-PROOF. NO PASS CLAIM. Gate 0 NOT passed; no gate0 JSON; A-G not launched.
2026-11-07. DS7.cs sha 54697597... (read, line numbers below); frozen file sha 424c68da...; prereg l2vast/ds3/prereg/ZL4_prereg.md sha 33702dfb... (DECISIONS.md, logged before scoring). Code l2vast/ds3/code/replica/zl4_extract_lead.py, zl4_score.py (+ /mnt/l2/l2vast/_zl4/{feas4,proof4}.py); bulk /mnt/l2/l2vast/_zl4/. Seal: ds3_all_ea/manifest_after.json 759f2258... identical before/after; only _zl4 written.

## 1. Call graph (own reading, before ZL-2/3 text)
- ONE entry: OnMarketData (L3113), Last prints of the chart instrument only (Bid/Ask events just set lastBid/lastAsk, L3144-45). now = State==Realtime ? Globals.Now : e.Time (L3141) - the PC clock at callback time, NOT the exchange stamp.
- Per print, in order (L3150): L2OnPrint(now,px,v,sgn) ONLY if sgn!=0 (sgn from lastBid/lastAsk quote events) -> L2OnDepthSnapshot (L1397; MedLevel 0.001 EWMA of (top5bid+top5ask)/10 every print, seeded at first, needs >=5 levels/side; L1404) -> L2ThSnapshot (L1550) -> then books loop (L3152): AdvExt/AdvExtTime updated by strict new extreme of the PRINT price (L3160) -> ManageThL2 (L3166) -> ManagePolicy (L3167).
- OnMarketDepth (L1338) does NOT call any snapshot code: it only maintains position-keyed arrays (20 slots/side; Remove shifts down, Add shifts up, Update overwrites; N=max/inc/dec) and depLast = Globals.Now (L1348). Snapshots therefore see whatever depth events NT8 had delivered BEFORE this Last callback.
- L2ThSnapshot: per prior-snapshot price level, nowSz by PRICE match in current arrays (L1561); vanished inside best => 0, beyond best => skipped; traded = sum of l2.Prints size at that exact price with ticks >= t0 where t0 = previous snapshot's now (includes the previous print AND the current print, already appended at L3150); cancelled = max(0,dec-traded); row (now,cb,ca) appended from the 2nd snapshot; list pruned BY COUNT (>5000 rows -> drop oldest 2500, L1565), not by time. traded is never reset: it is a time filter on l2.Prints (pruned 20000/10000).
- PulledSupport (L1570): own side, rows with ticks >= now-5s, scan back until older.
- ManageThL2 (L1572): skip ExitPending; trail check; DepthLive (L1353: depLast <120 s and N>=5 each side); throttle ThL2LastEval set when evaluated (after DepthLive passes, for profit AND loss side, L1580; NOT reset by fills, only by ResetTrade L302); loss: -unreal>=30 (unreal vs b.EntryPx = running weighted fill avg, price = print px), MedLevel>0, pulled>=30*Med, newMae=(now-AdvExtTime)<=5 (L1603-06).
- ManagePolicy (L2174): separate throttle PolicyLastEval (ThEvalFrequencySecs=1, L401; reset at every fill by ResetTh L293), no DepthLive gate, pct = unreal/|EntryPx-StopPx| (StopPx = ORIGINAL arm stop for L2-gated books, L2791), pulled_mult via same PulledSupport.
- Fills: each fill (L3047-50) sets EntryPx = weighted avg, AdvExt=EntryPx, AdvExtTime=fill time (so after the 30% add the adverse extreme restarts: newMae only becomes MORE permissive).
- Findings: ZL-3's port matches this graph line by line (regression C0 = 46/29/17/10 identical). No hidden call path, no MedLevel update from depth events, no extra reset of traded, no depth-keyed snapshot, no time-based pruning. Position-keyed vs price-keyed is equivalent for any consistent Add/Remove/Update stream (arrays equal the true top-N at every inter-event instant); divergence needs the NT8 event interleaving vs Last (= the S/lag/lead conventions) or a feed whose Add does not remove the pushed-off level (N grows to 20, stale tail) - unobservable here.

## 2. Candidates scored (prereg, STRICT window, 92 live cuts; FALSE = held trade the sim cuts)
| cand | reading | MATCH | SIM_EARLY | MISS | FALSE |
|--|--|--|--|--|--|
| C0 | ZL-3 S0P0C0G0 control | 46 | 29 | 17 | 10 |
| C1 | count-pruned pulledLog (5000/2500) | 46 | 29 | 17 | 10 |
| C2/C7 | book leads Last 50 ms (without/with prune) | 49 | 32 | 11 | 9 |
| C3/C8 | 100 ms | 49 | 32 | 11 | 9 |
| C4/C9 | 250 ms | 46 | 30 | 16 | 9 |
| C5/C10 | 500 ms | 49 | 29 | 14 | 9 |
| C6/C11 | 1000 ms | 47 | 30 | 15 | 8 |
Count-prune never binds. Selection rule picks C2 (49): NOT >=88, 9 false cuts. No reading reproduces the cuts. Feasibility (some armed print in [f-2.5 s,f] with pm>=30): 77 (C0), 82/79/78/78/78 (lead 50..1000) of 92; the same ~13-15 cuts stay below 30 under every convention.

## 3. Concrete proof trades (owned data cannot carry the decision)
- M7 and P7, Thu 11-05 03:48:37 ET (idx 170/171): both long, -32.0/-32.4 pts at the exit print 28339.25/28338.75, live ThL2Cut. Decision-window best armed pulled_mult (own bid cancels net of trades, 5 s, per-print cadence): pulled 32/35 contracts, MedLevel 2.74, pm 11.7/12.8 (needs >=82.3 contracts). Across the 6 conventions (C0, lead 50-1000) pm = 9.4-15.1, never near 30. ZL-3 per-record cadence on the same event: 93-249 contracts. Same-second dual cut = one real market event the live DOM scored >=30, the owned stream scores ~10 or ~10x.
- X5 Mon 11-02 04:06:50 (idx 14): short, -36.0; pulled 33, Med 2.35, pm 14.0 (13-17 all conventions).
- Opposite side: P7 Mon 11-02 10:05:28 (idx 28): sim pulled 343, Med 2.73, pm 125.5, unreal -30.19, secs_ext 0.12; live held 254 s more (PolicyCut at 10:09:42, -35.9). H7 idx 31 pm 57.6 (335 s), M7 idx 33 pm 68.1 (515 s). Large margins on the sim side: live cannot have had pm<30 from a scale error; its DOM/Last interleaving differs.
- Because the same convention swings pm by 3-10x on single events and in both directions, the decision is carried by sub-second NT8 depth/Last ordering and conflation that mbp-10 does not contain; the owned data can bound it (MATCH 46-52 under 40+ conventions) but not determine it. Remaining unobservables: e0 (pre-add avg, ~0.9 pt), policy arm 0.5*|avg-ArmStopPx| (<30 by ~0.5-1 pt), stale DOM tail.
