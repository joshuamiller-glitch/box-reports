# Order 0315Z Sun Nov 22 — written by the relay (Claude), not typed by Josh — plumbing check (no new test)
The relay's order channel closes at about 03:50Z. Please answer before then.

At 03:07Z all six Asia stack loops show "step run/1 ... last_progress 02:06Z" with NEW pids (19439-19882):
- asia-own / asia-stay / asia-own-l3g / asia-stay-l3g: waiting on 15 sets, 61 minutes with no progress;
- asia-own-w / asia-stay-w: waiting on 60 sets, 61 minutes with no progress.
At 01:52Z the weighted loops were reported "on pool 47, add round 2". Now they are back at step 1.

1. W-COMBO: were all the loops restarted at about 02:06Z (why: driver restart? pool change?). Was the weighted loops' round-2 work lost, against the "a running pass finishes and posts its FINAL first" rule you confirmed at 01:52Z? If a restart is ever needed again tonight, resume from the completed steps (the landed set results are still there) rather than from step 1.
2. W-GRIDOPS + LEAD: 15 sets x 42 months should take minutes at the head of the queue, yet nothing landed in an hour. Are the stack-loop rows (STK / loop add-round sets, and the weighted x4 sets) still served FIRST, ahead of the metered share heads at queue lines 8-13 (Asia stage C 40%, NY AM B/C, London, NY PM, item 6)? If the share heads now sit in front of them, give the stack-loop rows a guaranteed head (first call on slots; they are small) so the Asia and NY AM stack searches never wait behind first looks and luck controls. Same for the stack-rule / daily-stop fit rows when W-LAYERS queues them.
3. LEAD: post the corrected ETA for the first Asia FINAL (equal and weighted) and the first NY AM FINAL with the new books, and keep a watch tonight: any stack loop with no progress for 45 minutes gets one LEAD line saying why and what was done.
