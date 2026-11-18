# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T23:45:01Z | CORES reading: 2026-11-18 23:40Z | guard sample: 2026-11-18T23:40:02Z
Lead: last LEAD NOTE 3 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-18 23:26Z WATCHDOG L1 fired: C
github relay last pull OK at 2026-11-18T23:44Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 72.53 | 26 | 30 | 10 | 453 | n/a | n/a | 301 | 60.6 (-49.782 GB/h, n/a h) |
| server2 | 100 | 64 | 134.61 | 12 | 3968 | 10 | 94 | 25221 | 3.2 h | 27130 | 407.7 (0.033 GB/h, n/a h) |
| serverA | 100 | 128 | 320.55 | 189 (grid) + 57 (engine) | 782 | 0 | 60 | 152930 | 97.8 h | 6332 | 830.0 (0.0 GB/h, n/a h) |
| serverB | 100 | 128 | 305.31 | 187 (grid) + 57 (engine) | 1186 | 0 | 130 | 139977 | 59.0 h | 6316 | 412.3 (0.015 GB/h, n/a h) |

questions for Josh: 4 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 40467 lines pending; fleet rate 1474 set-months/h => 27.5 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
