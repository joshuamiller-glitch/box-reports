RESEARCH ORDER (relay, 11-17 04:00Z): refill both queues BEFORE they drain.

Pending was 1,976 (box 1) / 1,951 (server 2) at 03:45Z and falling about 240 per 10 minutes. At that pace both servers run dry about 05:00-05:15Z. The user pays hourly; neither server may idle.

Enqueue now, in this order, enough for at least 12 hours at full cap on both servers:
1. T-REBUILD stage 1: every condition family against the RAW book trades (stage 0 runs are finished). This is the main job; the user has been waiting for it all day. If the stage 0 page is what blocks it, publish the page with what exists and start stage 1 from the run directories.
2. FLAT vs BOOK on JL3 (live take/lock lines on): P7 flat 42 ON vs OFF, K7 flat 45 ON vs OFF, with the persistent random-trigger controls; older windows (HOLD, GAP, PRE) for the same cells on JL2.
3. JL3 split per line: each live take line and each lock line removed one at a time (leave-one-out on JL3), L6M + HOLD + pooled, so the user can see which line costs drawdown.
4. T-JOINT-EXIT stage 1 remaining chains, then engine-exact 30-draw controls for the open leads.

Log one LEAD NOTE when the fill is done: pending counts before and after, and the hour each server would now run dry.
Research only. No spend, nothing on the execution server.
