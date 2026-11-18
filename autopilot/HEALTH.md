# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T21:45:01Z | CORES reading: 2026-11-18 21:40Z | guard sample: 2026-11-18T21:40:01Z
Lead: last LEAD NOTE 43 min ago | last transcript activity 4 min ago | last watchdog line: 2026-11-18 21:42Z WATCHDOG L1 fired: C
github relay last pull OK at 2026-11-18T21:44Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | disk free GB |
|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 70.86 | 18 | 58 | 30 | 408 | n/a | n/a | 354 |
| server2 | 100 | 64 | 104.04 | 14 | 1291 | 46 | 101 | 31329 | 12.1 h | 27253 |
| serverA | 100 | 128 | 262.82 | 93 (grid) + 57 (engine) | 1004 | 0 | 71 | 159615 | 79.5 h | 6341 |
| serverB | 100 | 128 | 253.76 | 89 (grid) + 55 (engine) | 1177 | 5 | 129 | 147916 | 62.8 h | 6328 |

questions for Josh: 3 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 5768 lines pending; fleet rate 1418 set-months/h => 4.1 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
