# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T21:00:01Z | CORES reading: 2026-11-18 20:55Z | guard sample: 2026-11-18T20:48:47Z
Lead: last LEAD NOTE 7 min ago | last transcript activity 0 min ago | last watchdog line: 2026-11-18 20:58Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-18T20:59Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | disk free GB |
|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 56.89 | 13 | 15 | 0 | 421 | n/a | n/a | 354 |
| server2 | 100 | 64 | 82.78 | 10 | 1144 | 85 | 108 | 33854 | 14.8 h | 27278 |
| serverA | 100 | 128 | 177.29 | 93 (grid) + 57 (engine) | 1326 | 0 | 54 | 160474 | 60.5 h | 6346 |
| serverB | 100 | 128 | 171.77 | 89 (grid) + 55 (engine) | 2384 | 32 | 109 | 149900 | 31.4 h | 6336 |

questions for Josh: 2 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 4431 lines pending; fleet rate 1384 set-months/h => 3.2 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
