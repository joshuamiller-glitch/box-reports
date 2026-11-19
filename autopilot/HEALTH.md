# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T00:45:01Z | CORES reading: 2026-11-19 00:40Z | guard sample: 2026-11-19T00:40:01Z
Lead: last LEAD NOTE 13 min ago | last transcript activity 4 min ago | last watchdog line: 2026-11-18 23:26Z WATCHDOG L1 fired: C
github relay last pull OK at 2026-11-19T00:44Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 74.2 | 30 | 18 | 16 | 490 | n/a | n/a | 300 | 60.6 (-25.515 GB/h, n/a h) |
| server2 | 100 | 64 | 113.41 | 18 | 4090 | 16 | 117 | 139610 | 17.1 h | 27046 | 407.7 (0.032 GB/h, n/a h) |
| serverA | 100 | 128 | 212.55 | 97 (grid) + 55 (engine) | 1444 | 0 | 96 | 128593 | 44.5 h | 6327 | 830.0 (0.008 GB/h, n/a h) |
| serverB | 100 | 128 | 166.35 | 99 (grid) + 56 (engine) | 1339 | 0 | 124 | 123351 | 46.1 h | 6311 | 412.3 (0.008 GB/h, n/a h) |

questions for Josh: 4 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 53686 lines pending; fleet rate 1654 set-months/h => 32.5 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
