RESEARCH ORDER (relay, 11-18 06:33Z): LEAD, WAKE. No lead note since 05:35Z (only automatic lines); order 0616Z was auto-acked at 06:15Z and not acted on. SERVER 2 has been under 85% busy for EIGHT readings (42% at 06:20Z and 06:25Z, load 27) and BOX 1 is now falling too (86% at 06:25Z, load 29). The user pays hourly and is asleep.
Do these now, in this order, and write one line when each is done:
1. Server 2: restart the grid loops (stage (d) rest of pass 1, stage (a2) exits, the LEVEL deep test of order 0602Z) with 56 workers; set the engine cap to 40 until the grid workers are all running; confirm busy >= 95%.
2. Box 1: refill to 32 workers (grid workers 20 -> 28 if memory allows above 40 GB, engine chains for NT controls / persist fix / SWA / SWB / P7L / ORB identity).
3. Say what stopped (agent finished and nothing queued? scorer / publisher lock? heartbeat?), and whether your own heartbeat loop is still running; restart it if not.
4. Then act on orders 0602Z (level cells deep test + P&F look-ahead check) and 0616Z.
Research only. No spend.
