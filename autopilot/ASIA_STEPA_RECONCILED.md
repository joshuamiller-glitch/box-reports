# Asia step (a): ONE reconciled status (W-RECON, read-only, 2026-11-24 ~03:55Z)
Information only. Nothing queued, nothing edited, no rule change. Counts read from the result folders (runs_rf DONE files), _combo/aln_state.json, _combo/allnew_pending.txt, _split/pending_asia_all.txt, asia_all_feed.log, leases. Estimates are marked ESTIMATE.

## The short answer
Both counts are right; they count different things.
- W-GRIDOPS 9.2k/41,972 = rows still to run in pending_asia_all.txt = ONLY the 735 "unaffected-bar" Asia books (base + prior years + the controls already queued). 41,972 was the row count at 21:36Z; 9,250 left at 03:49Z.
- W-COMBO countdown "659 of 1,374" = all 1,374 first-look candidates, but it counts a plain BASE set for every one of them. For the 639 "affected-bar" books the BASE set is never run (they are judged on their own _CANC set). So its 25-27k "missing set-months" is inflated by 17,148 set-months that nobody needs.
- Josh's order 2135Z names the scope itself: step (a) = "the remaining ~485 of 735". So step (a) = the 735 unaffected books. The 735 in "440/460/507 of 735 unaffected complete" is the same 735.

## 1. Plain numbers (Asia, 1,374 candidates that passed a first look)
| group | books | state now |
|---|---|---|
| 1,374 all Asia first-look candidates (W-BEST new, L6M>0 and L3M>0, not stale, deduplicated) | 1,374 | |
| A. affected-bar books (judged on _CANC base) | 639 | DONE. 216 rejected at the first look on the _CANC bars (161 L6M<=0, 55 L3M<=0; only their L6M months were run, correctly not extended). 423 have all 42 months. 167 of those 423 pass the prior-year gate; all 167 have all 30 controls landed. Fully judged: 639 of 639. Rows missing: 0 needed |
| B. unaffected-bar books (BASE set) = step (a) proper | 735 | 532 have all 42 months (515 gated by ALN-AUTO + 17 landed in the last minutes, gated at next 5-min cycle). 203 not complete (7,875 set-months missing, 7,862 in the feed). 208 of 532 pass the prior-year gate (39%). 202 of those 208 (in state) have 30 controls queued: 190 decided (19 beat >=27 of 30), 12 undecided (2,107 control set-months still to land, 1,388 of them rows in the feed), ~6 not yet queued |

Fully judged (prior years + controls, pass or fail): 639 + about 510 = about 1,150 of 1,374. Remaining about 225 books (all inside group B): 203 not complete + 12 controls running + ~10 landed but not yet gated/controlled.
Group B alone: about 512 of 735 fully judged, about 223 remain (this is the "485 remaining" of 21:12Z, shrunk).

Set-months remaining (group B):
- in pending_asia_all.txt now: 9,250 (7,862 BASE/prior + 1,388 controls) at 03:49Z; plus ~480 already leased (running)
- NOT yet in the file (ESTIMATE): controls for books that pass the gate after they complete. 180 per passing book (30 controls x 6 months). Books still to be gated: 203 + ~17 = ~220. Pass rate so far 39% of completed (37% over all 795 Asia books in the state file; later-ranked books likely pass less). At 25-39%: 55-86 books x 180 = about 10k-15.5k rows. Planning figure 12k.
- Total still to run (ESTIMATE): 9.25k + 0.5k + ~12k = about 21.7k (range 19.5k-25k).
Rows missing from the feed that SHOULD be there: none. Every unaffected missing row (8,370 of 8,370) is either in the feed (7,974) or leased (476). The 17,148 affected-BASE set-months and the 7,776 _CANC prior-year months of the 216 first-look rejects are not in the feed on purpose.

## 2. What the numbers are
- 1,374 = all Asia candidates (combo_aln.candidates('AS',1500)); 735 = those whose bar family is unaffected by the print rule; 639 = affected (accumulating) families.
- 735 is the scope of step (a) per the order. Feed (asia_all_feed.py) takes only TL3_ALN_AS_* rows from allnew_pending.txt minus leased: it covers all of group B, and nothing of group A (group A finished through the _CANC/D8 path in the reselect loops).
- The countdown line (combo_reselect.countdown) uses ids = all 1,374 and the plain BASE name, so it cannot reach 1,374 of 1,374. Its "659 complete" = 515 (unaffected) + 144-176 (old BASE runs of affected books); the heartbeat line "507 of 735 unaffected" is the right progress meter for step (a).
- The earlier "440 -> 507 of 735" and the feed's 11.9k -> 9.2k are the same progress.

## 3. ETA (measured rate: 9,728 Asia lease starts in the last 60 min, 5,300 in the last 30 min = about 10k/h; feed net fall is slower because controls are appended as books pass)
- Step (a) on the full count (about 21.7k, range 19.5k-25k at 9.7k/h): 2.0 to 2.6 h, so about 05:55-06:30Z (planning 06:10Z). The raw feed (9.25k) alone would finish about 04:50Z (GRIDOPS 04:25-04:35Z used 11.9k at a higher rate and no new controls). Controls are appended at the end of allnew_pending, so the last 1.5-2 h is mostly control rows; the tail needs enough parallel leases (30 controls per book run in parallel, fine).
- Steps b-e after it (GRIDOPS 21:45Z figures, not re-measured by me): b re-run 2-3 h after the pool is final, c exit run ~1 h, d joint/2-lot/null ~2.5 h, e coding. Asia DONE a-e about 12:30-14:00Z if b starts on the final pool at ~06:15Z and runs strictly after (a). If b is allowed to start earlier on rounds (section 4), about 10:30-12:30Z. UNVERIFIED: b-d durations are from GRIDOPS, depend on W-COMBO/W-LAYERS2 round times.

## 4. Does step (b) wait? (from combo_reselect.py)
- It does NOT wait for step (a) to finish. The reselect loops run continuously: pool_status every 10 min, and when a stack run is 'done' and the pool list has changed it starts a new run ("RE-RUN WITH n pool books (was m)", old state kept as a _v<time> file). Inside a run, a round is never closed on partial evidence (waits for all its sets, ROUND INCOMPLETE after 6 h and keeps waiting).
- Pool now: 84 (passing a+b+c+d, whole Asia universe incl. bracket step-2 books); 36 waiting for controls. Group B should add roughly 8-10 more pool books (19 of 190 decided so far pass = 10%; ESTIMATE 6-12 from the books still to run).
- So rounds happen automatically as the pool grows. The round that counts as "Asia DONE" for step (b) is the FIRST re-run that starts after the pool is final = after the last control set of the 735 has landed and been decided and the pool list stops changing. Any earlier round is provisional. Nothing in the code marks that round; it has to be declared by W-COMBO/lead (the 'pool_cutoff' file was a one-off of 11-21 06:00Z). Decision for the lead, not made here.

## Could not verify
- Which of the 36 waiting-for-controls books belong to the 1,374 (many are bracket step-2 books, outside the 1,374; their controls come from the step-2 daemon, not this feed).
- Final pass rate of the 203 unfinished books (ranked lower: likely below 39%).
- Durations of b-e (taken from GRIDOPS 21:45Z).
- 130 books in aln_state.json are no longer in the candidate list (rank dropped); judged earlier, not counted above.
