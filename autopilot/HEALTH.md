# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T03:25:01Z | CORES reading: 2026-11-19 03:20Z | guard sample: 2026-11-19T03:20:01Z
Lead: last LEAD NOTE 6 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-19 03:12Z WATCHDOG L1 fired: E
github relay last pull OK at 2026-11-19T03:24Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 69.76 | 25 | 76 | 27 | 571 | n/a | n/a | 298 | 60.5 (0.048 GB/h, n/a h) |
| server2 | 100 | 64 | 96.52 | 14 | 2279 | 27 | 98 | 139814 | 30.7 h | 26960 | 407.6 (0.031 GB/h, n/a h) |
| serverA | 100 | 128 | 188.9 | 61 (grid) + 77 (engine) | 164 | 0 | 160 | 85538 | 260.8 h | 6311 | 830.0 (0.008 GB/h, n/a h) |
| serverB | 100 | 128 | 173.15 | 61 (grid) + 71 (engine) | 683 | 0 | 201 | 80524 | 58.9 h | 6292 | 412.2 (0.004 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 113993 lines pending; fleet rate 2060 set-months/h => 55.3 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
