# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T02:40:01Z | CORES reading: 2026-11-19 02:35Z | guard sample: 2026-11-19T02:30:02Z
Lead: last LEAD NOTE 5 min ago | last transcript activity 3 min ago | last watchdog line: 2026-11-19 02:16Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-19T02:39Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 67.2 | 24 | 41 | 40 | 505 | n/a | n/a | 299 | 60.5 (-9.472 GB/h, n/a h) |
| server2 | 100 | 64 | 112.03 | 14 | 1715 | 17 | 98 | 141303 | 41.2 h | 26983 | 407.6 (0.032 GB/h, n/a h) |
| serverA | 99 | 128 | 171.18 | 61 (grid) + 75 (engine) | 1124 | 0 | 114 | 84883 | 37.8 h | 6315 | 830.0 (0.004 GB/h, n/a h) |
| serverB | 99 | 128 | 189.68 | 61 (grid) + 75 (engine) | 444 | 0 | 167 | 79050 | 89.0 h | 6300 | 412.2 (0.008 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 103742 lines pending; fleet rate 1768 set-months/h => 58.7 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
