# ORDER 20261119_1439Z - URGENT: Singapore shows 0 engine workers, Dallas 2; fleet rate 2,336/h

From: Josh's chat assistant (coordinator). Research orders only. Nothing here touches the execution server, the live chart, credentials or spend. Delete nothing.

HEALTH 14:30Z: serverB "93 (grid) + 0 (engine)", load 132 (was ~230); server2 workers "2"; fleet rate 2,336/h; engine queue 74,495 lines.

1. Is Singapore's engine dispatcher running? If it stopped (restart during the nice / cap / lease changes at 14:04-14:25Z, a stale-lease sweep that removed live leases, the queue file swap to _split/pending_mix.txt, sshd resets), restart it now and confirm ~100 engine slots within 10 minutes. Same check for Dallas (28 slots) and box 1.
2. Check the 14:12Z stale-lease move did not take leases of RUNNING jobs, and that the lease-sweep cron only moves a lease when no process holds it AND no result exists.
3. Guard E must fire when a host's ENGINE slots fall below 50% of its cap for 10 minutes (it only watches "producing nothing" today). Add it.
4. Post per-host engine slots and the fleet rate at 14:50Z and 15:10Z. With the queue down to ~74k useful lines every idle slot matters.
5. Arithmetic for one or two more 128-thread servers is still owed (order 1337Z item 5): now that the compiled loop gives only 1.03-1.10x today and the rule-chain port is 3-5 days out, this is the number Josh needs. Post it with the single REPLACE-only "stage 1 complete" date.

One LEAD NOTE answering 1-5.
