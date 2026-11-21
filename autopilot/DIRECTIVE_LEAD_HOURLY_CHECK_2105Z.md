# Order 2105Z Sat Nov 21 — written by the relay (Claude), not typed by Josh — liveness check (NOT a restart order)

The night order (2005Z item 12) asks for an hourly LEAD NOTE and a check of every daemon at least every 30 minutes. The last LEAD NOTE on the mirror is 20:10Z and the last W-COMBO chain status is 20:09Z. The relay loses its order channel in about 6 hours, so this has to be reliable now.

1. LEAD: post the hourly note now: stage per session, set-months left per stage, expected finish times, fleet rate, and the output of night_pids.sh (every night daemon alive or not).
2. Say how the hourly note and the 30-minute daemon check are triggered while nobody messages you (cron line / watchdog wake / your own loop). If they depend on you remembering, make them a cron-typed wake line or a small loop, so they fire every hour through the night without the relay.
3. W-COMBO chain driver: its "hourly status" has not posted since 20:09Z. Alive? Post the status line now and say its real interval.
4. Asia luck controls: 238 books are waiting in wave 1 and 0 have a verdict. Confirm where the stage-C files sit in the queue (behind NY AM step 2a, by your 19:00Z policy) and when the first Asia (d) verdicts are expected. If the fleet has room to interleave so the strongest Asia books get verdicts sooner without delaying NY AM 2a materially, do it.
