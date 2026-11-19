# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T01:00:01Z | CORES reading: 2026-11-19 00:55Z | guard sample: 2026-11-19T00:50:01Z
Lead: last LEAD NOTE 12 min ago | last transcript activity 2 min ago | last watchdog line: 2026-11-18 23:26Z WATCHDOG L1 fired: C
github relay last pull OK at 2026-11-19T00:59Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 68.4 | 32 | 14 | 16 | 500 | n/a | n/a | 300 | 60.6 (-23.598 GB/h, n/a h) |
| server2 | 100 | 64 | 98.71 | 11 | 2951 | 15 | 124 | 139610 | 23.7 h | 27040 | 407.7 (0.037 GB/h, n/a h) |
| serverA | 100 | 128 | 150.3 | 61 (grid) + 57 (engine) | 1449 | 0 | 94 | 88567 | 30.6 h | 6326 | 830.0 (0.007 GB/h, n/a h) |
| serverB | 100 | 128 | 181.5 | 99 (grid) + 55 (engine) | 1533 | 0 | 132 | 80856 | 26.4 h | 6309 | 412.3 (0.007 GB/h, n/a h) |

questions for Josh: 4 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 57798 lines pending; fleet rate 1700 set-months/h => 34.0 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
