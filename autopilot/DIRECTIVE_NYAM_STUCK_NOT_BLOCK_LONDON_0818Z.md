# ORDER 20261120_0818Z: NY AM first looks stuck on 237 cells: do not let them block London or the final NY AM run (research / queue lines only)

Lead 08:09Z: 606 set-months in 237 NY AM cells failed 6 times on the exit guard (time exit more than 3 h after the last tick, months 202605/06/07/09) and gave up. Agreed: the guard is a standard and is NOT changed tonight; the question is in QUESTIONS_FOR_JOSH.md for Josh. Meanwhile, nothing may sit idle waiting for sets that will never land.

1. COUNT: of the ~10,000 NY AM first-look lines W-NYENG reported queued at 05:43Z, how many are (a) landed since, (b) these 606 gave-up set-months, (c) still genuinely runnable? If (c) is ~0, NY AM first looks are DONE except the 237 cells: say so.
2. LONDON START: london_session_next waits for "queued + running = 0". Confirm the gave-up sets do not count as queued (if they do, move those lines to a parked file, a queue-file line change, so the trigger fires). Josh's order is Asia + NY AM, then London, then NY PM: London first looks start as soon as (c) is drained; state the time.
3. The 237 cells: mark them INCOMPLETE on the scorecards (not ranked on a last-6-months number that is missing months), list how many were in the top 150 or in the all-new pool / stacks (L7cc56d99, L488784d8, L063a587d, L2176f633, L05350e98, L6547965c: any of them?). Parked, not deleted.
4. Why did the SAME months pass for the other ~3,000 NY AM cells and for these cells' other books? Is it one exit type (time exits) or one bar type? One paragraph when W-NYENG has it. Also say plainly whether the already-landed results of other cells in those months could be wrong in the other direction (a trade the guard should have rejected but did not).
5. Freed capacity goes to: all-new prior years and luck controls for NY AM books waiting (19 pending), stack steps, then London.
Answer in MORNING.md.
