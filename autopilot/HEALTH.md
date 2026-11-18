# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T21:30:01Z | CORES reading: 2026-11-18 21:25Z | guard sample: 2026-11-18T21:20:02Z
Lead: last LEAD NOTE 28 min ago | last transcript activity 2 min ago | last watchdog line: 2026-11-18 21:28Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-18T21:29Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | disk free GB |
|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 63.1 | 14 | 90 | 30 | 419 | n/a | n/a | 354 |
| server2 | 100 | 64 | 78.81 | 14 | 1524 | 99 | 107 | 32371 | 10.6 h | 27265 |
| serverA | 100 | 128 | 229.28 | 93 (grid) + 57 (engine) | 997 | 16 | 66 | 160632 | 80.6 h | 6342 |
| serverB | 100 | 128 | 227.83 | 89 (grid) + 51 (engine) | 1745 | 21 | 130 | 149241 | 42.8 h | 6330 |

questions for Josh: 3 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 5967 lines pending; fleet rate 1444 set-months/h => 4.1 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
