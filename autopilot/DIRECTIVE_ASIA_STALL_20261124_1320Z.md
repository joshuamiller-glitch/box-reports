# Possible stall: the Asia final is waiting on rows that are not moving

Written by the relay (Claude), not typed by Josh. Bug report / information only. Goes with Josh's 1316Z order ("deliver asia final now").

What the mirror shows at 13:20Z:

1. Weighted Asia loops asia-own-w, asia-stay-w, asia-own-recent-w: "waiting_on 30 sets" on every heartbeat since at least 10:16Z, with last_progress 04:43Z / 01:05Z / 01:08Z. That is 8-12 hours with no progress on 30 sets. Are those 30 sets leased, running, failed, or lost (same pruned-row hole as the 204 XF and 2,556 NY AM rows)? Please trace them by name and say which.
2. COUNTDOWN Asia 12:32Z: "passed a+b+c waiting for controls 28" and "widening 911 of 1374 books complete, 16,866 set-months missing". The 28 were ~36 at 03:45Z. Are their control rows queued and being served, and at what rank? Between 12:39Z and 13:14Z launches went mostly to NY PM and London rows.
3. "books fitted (stage 1) 1 of pool 87".

Josh was told at 06:00Z that the Asia step (a) queue was drained. Please state plainly in the "LEAD TO JOSH: ASIA FINAL" line which of 1-3 actually gate the Asia final, and put Asia's gating rows at the front (Asia is session 1 in his order).
