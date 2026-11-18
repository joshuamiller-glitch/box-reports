# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T22:05:01Z | CORES reading: 2026-11-18 22:00Z | guard sample: 2026-11-18T22:00:01Z
Lead: last LEAD NOTE 17 min ago | last transcript activity 6 min ago | last watchdog line: 2026-11-18 21:42Z WATCHDOG L1 fired: C
github relay last pull OK at 2026-11-18T22:04Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | disk free GB |
|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 72.0 | 19 | 27 | 49 | 432 | n/a | n/a | 354 |
| server2 | 100 | 64 | 104.03 | 14 | 3257 | 134 | 108 | 31329 | 4.8 h | 27224 |
| serverA | 100 | 128 | 303.59 | 93 (grid) + 57 (engine) | 813 | 11 | 83 | 159615 | 98.2 h | 6339 |
| serverB | 100 | 128 | 271.24 | 89 (grid) + 57 (engine) | 578 | 0 | 148 | 147916 | 128.0 h | 6326 |

questions for Josh: 3 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 5458 lines pending; fleet rate 1542 set-months/h => 3.5 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
