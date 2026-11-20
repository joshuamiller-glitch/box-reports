# ORDER 20261120_0924Z: 161 slots are on low-value work while NY AM first looks wait: use the freeze-allowed levers (queue rows only)

W-GRIDOPS 09:12Z: B first looks run on 169 slots (A 72, B 77, old Dallas 20) at ~190 s per job; Amsterdam C and new Dallas D run 161 slots of LIVE-BASE controls because few all-new lines reach the merge. Josh's direction since 22:30Z is all-new books only: live-base controls are the lowest-value work in the queue, and NY AM first looks are what London is waiting on. Fleet fast share is 9%.

1. Urgent row (the same freeze-allowed lever as the TL3_ALN_ row at 04:15Z): let C and D take the B-id NY AM first looks (TL3_NYE_B..._RK7) ahead of live-base controls. All-new lines (TL3_ALN_) keep their place in front. Report slots by class before / after and the new NY AM first-look finish time and London start time.
2. Fast path: are the B-id first-look sets on the exact engine only because their kind name is not in FAST_KINDS.txt? The L-id RK7 first looks ran fast. If the B kind is the same template with a different id letter, run the standard identity check (fast vs exact, >= 6 set-months identical across >= 2 books) and add it the usual way: this is the established procedure, not new code. If it needs code, say so and leave it for 14:00Z. Same question for TL3_NYE_*_RK7H and the P2JN kind (24 running exact).
3. The 606 dead lines: confirm W-NYENG has taken them out of its sources, so the London trigger can fire when the B first looks drain.
One answer in MORNING.md.
