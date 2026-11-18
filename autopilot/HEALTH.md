# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T23:35:01Z | CORES reading: 2026-11-18 23:30Z | guard sample: 2026-11-18T23:30:01Z
Lead: last LEAD NOTE 3 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-18 23:26Z WATCHDOG L1 fired: C
github relay last pull OK at 2026-11-18T23:34Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 74.22 | 26 | 27 | 21 | 438 | n/a | n/a | 301 | 60.7 (-59.148 GB/h, n/a h) |
| server2 | 100 | 64 | 118.42 | 14 | 3476 | 21 | 95 | 25221 | 3.6 h | 27141 | 407.7 (0.026 GB/h, n/a h) |
| serverA | 100 | 128 | 321.37 | 189 (grid) + 57 (engine) | 985 | 0 | 69 | 152930 | 77.6 h | 6332 | 830.0 (0.0 GB/h, n/a h) |
| serverB | 100 | 128 | 303.37 | 187 (grid) + 53 (engine) | 1338 | 0 | 132 | 139977 | 52.3 h | 6317 | 412.3 (0.018 GB/h, n/a h) |

questions for Josh: 4 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 38197 lines pending; fleet rate 1468 set-months/h => 26.0 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
