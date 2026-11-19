# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T00:50:01Z | CORES reading: 2026-11-19 00:45Z | guard sample: 2026-11-19T00:40:01Z
Lead: last LEAD NOTE 2 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-18 23:26Z WATCHDOG L1 fired: C
github relay last pull OK at 2026-11-19T00:49Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 72.51 | 28 | 18 | 16 | 490 | n/a | n/a | 300 | 60.6 (-25.515 GB/h, n/a h) |
| server2 | 100 | 64 | 120.05 | 13 | 4090 | 16 | 117 | 139610 | 17.1 h | 27046 | 407.7 (0.032 GB/h, n/a h) |
| serverA | 100 | 128 | 207.65 | 97 (grid) + 57 (engine) | 1444 | 0 | 96 | 128593 | 44.5 h | 6327 | 830.0 (0.008 GB/h, n/a h) |
| serverB | 100 | 128 | 166.06 | 99 (grid) + 56 (engine) | 1339 | 0 | 124 | 123351 | 46.1 h | 6311 | 412.3 (0.008 GB/h, n/a h) |

questions for Josh: 4 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 54558 lines pending; fleet rate 1654 set-months/h => 33.0 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
