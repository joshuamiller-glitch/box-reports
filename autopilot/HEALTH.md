# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T22:20:01Z | CORES reading: 2026-11-18 22:15Z | guard sample: 2026-11-18T22:10:01Z
Lead: last LEAD NOTE 2 min ago | last transcript activity 2 min ago | last watchdog line: 2026-11-18 22:18Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-18T22:19Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | disk free GB |
|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 86.21 | 19 | 17 | 49 | 451 | n/a | n/a | 354 |
| server2 | 100 | 64 | 86.99 | 13 | 3624 | 135 | 108 | 27731 | 3.8 h | 27217 |
| serverA | 100 | 128 | 347.32 | 93 (grid) + 57 (engine) | 688 | 11 | 85 | 158737 | 115.4 h | 6338 |
| serverB | 100 | 128 | 304.67 | 89 (grid) + 53 (engine) | 472 | 0 | 156 | 147199 | 155.9 h | 6325 |

questions for Josh: 3 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 5234 lines pending; fleet rate 1600 set-months/h => 3.3 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
