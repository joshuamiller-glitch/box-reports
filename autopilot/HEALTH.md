# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T21:40:01Z | CORES reading: 2026-11-18 21:35Z | guard sample: 2026-11-18T21:30:01Z
Lead: last LEAD NOTE 38 min ago | last transcript activity 2 min ago | last watchdog line: 2026-11-18 21:28Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-18T21:39Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | disk free GB |
|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 68.75 | 16 | 90 | 30 | 420 | n/a | n/a | 354 |
| server2 | 100 | 64 | 106.07 | 14 | 1545 | 51 | 102 | 32371 | 10.5 h | 27260 |
| serverA | 100 | 128 | 263.72 | 93 (grid) + 57 (engine) | 1115 | 16 | 73 | 160632 | 72.0 h | 6341 |
| serverB | 100 | 128 | 248.19 | 89 (grid) + 55 (engine) | 1539 | 16 | 128 | 149241 | 48.5 h | 6329 |

questions for Josh: 3 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 5844 lines pending; fleet rate 1446 set-months/h => 4.0 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
