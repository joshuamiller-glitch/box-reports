# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T02:45:02Z | CORES reading: 2026-11-19 02:40Z | guard sample: 2026-11-19T02:40:01Z
Lead: last LEAD NOTE 10 min ago | last transcript activity 2 min ago | last watchdog line: 2026-11-19 02:16Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-19T02:44Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 63.28 | 23 | 29 | 40 | 564 | n/a | n/a | 299 | 60.5 (0.048 GB/h, n/a h) |
| server2 | 100 | 64 | 104.49 | 14 | 2431 | 40 | 97 | 141104 | 29.0 h | 26979 | 407.6 (0.029 GB/h, n/a h) |
| serverA | 100 | 128 | 169.25 | 61 (grid) + 75 (engine) | 1138 | 0 | 142 | 85699 | 37.7 h | 6314 | 830.0 (0.004 GB/h, n/a h) |
| serverB | 100 | 128 | 181.15 | 61 (grid) + 73 (engine) | 580 | 0 | 188 | 81030 | 69.9 h | 6298 | 412.2 (0.008 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 105125 lines pending; fleet rate 1982 set-months/h => 53.0 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
