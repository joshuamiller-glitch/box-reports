# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T21:05:01Z | CORES reading: 2026-11-18 21:00Z | guard sample: 2026-11-18T21:00:01Z
Lead: last LEAD NOTE 3 min ago | last transcript activity 3 min ago | last watchdog line: 2026-11-18 20:58Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-18T21:04Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | disk free GB |
|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 58.41 | 13 | 25 | 0 | 449 | n/a | n/a | 354 |
| server2 | 100 | 64 | 82.75 | 14 | 1275 | 176 | 108 | 33854 | 13.3 h | 27272 |
| serverA | 100 | 128 | 191.19 | 93 (grid) + 57 (engine) | 1132 | 0 | 63 | 160474 | 70.9 h | 6344 |
| serverB | 100 | 128 | 188.74 | 89 (grid) + 55 (engine) | 2116 | 21 | 119 | 149900 | 35.4 h | 6334 |

questions for Josh: 3 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 5071 lines pending; fleet rate 1478 set-months/h => 3.4 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
