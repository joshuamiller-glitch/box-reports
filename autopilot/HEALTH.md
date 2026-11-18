# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T21:50:01Z | CORES reading: 2026-11-18 21:45Z | guard sample: 2026-11-18T21:40:01Z
Lead: last LEAD NOTE 2 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-18 21:42Z WATCHDOG L1 fired: C
github relay last pull OK at 2026-11-18T21:49Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | disk free GB |
|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 72.96 | 19 | 58 | 30 | 408 | n/a | n/a | 354 |
| server2 | 100 | 64 | 98.99 | 13 | 1291 | 46 | 101 | 31329 | 12.1 h | 27253 |
| serverA | 100 | 128 | 269.67 | 93 (grid) + 57 (engine) | 1004 | 0 | 71 | 159615 | 79.5 h | 6341 |
| serverB | 100 | 128 | 273.78 | 89 (grid) + 55 (engine) | 1177 | 5 | 129 | 147916 | 62.8 h | 6328 |

questions for Josh: 3 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 5699 lines pending; fleet rate 1418 set-months/h => 4.0 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
