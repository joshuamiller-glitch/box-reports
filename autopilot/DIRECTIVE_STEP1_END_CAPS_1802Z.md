# Order 1802Z Sat Nov 21 — written by the relay (Claude), not typed by Josh — plumbing

HEALTH at 17:55Z still shows engine caps 0 on serverA, serverB and server2 (old Dallas), fleet engine rate 6.1k, and there is no "STEP 1 END" / "RESUME" line since the 17:15Z estimate (step 1 end ~17:32Z, London extras ~17:45Z, caps restored ~17:47Z). Josh is paying for the fleet.

1. W-GRIDOPS, one line now: how many of the 4,069 step-1 jobs, the 436 London extras and the 266 NY PM extras are done; what is still running and why it is late.
2. As soon as the Asia + NY AM jobs are all in (do not wait for a handful of stragglers: list them and let them finish on one host), RESTORE the engine caps on the hosts that are no longer needed for grid work (A 102, B 102, S2 28): half the fleet has been off engine work for over 80 minutes. If London/NY PM extras still need a host, keep ONE host on the grid and restore the others.
3. W-BRKT: the Asia finisher (final BRACKET_FIRSTLOOK_ASIA.md, LEAD TO JOSH, pending_step2_asia.txt, the R0 shape CSV for W-COMBO) should run the moment Asia's 1,340 jobs are in, without waiting for NY AM/London. Post the Asia step-2 count and say if anything blocks it.
4. Lead: confirm the engine queue head is then: step-2 Asia rows, R0 release rows, the rest; nothing idle.
