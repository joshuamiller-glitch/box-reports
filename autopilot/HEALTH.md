# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T02:10:01Z | CORES reading: 2026-11-19 02:05Z | guard sample: 2026-11-19T02:00:02Z
Lead: last LEAD NOTE 15 min ago | last transcript activity 0 min ago | last watchdog line: 2026-11-19 01:42Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-19T02:09Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 67.21 | 25 | 44 | 15 | 477 | n/a | n/a | 299 | 60.5 (-15.453 GB/h, n/a h) |
| server2 | 100 | 64 | 116.96 | 14 | 1870 | 15 | 94 | 141415 | 37.8 h | 26990 | 407.6 (0.032 GB/h, n/a h) |
| serverA | 96 | 128 | 131.57 | 61 (grid) + 57 (engine) | 903 | 0 | 95 | 85741 | 47.5 h | 6319 | 830.0 (0.005 GB/h, n/a h) |
| serverB | 93 | 128 | 119.38 | 61 (grid) + 52 (engine) | 696 | 0 | 140 | 79165 | 56.9 h | 6303 | 412.2 (0.007 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 88710 lines pending; fleet rate 1612 set-months/h => 55.0 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
