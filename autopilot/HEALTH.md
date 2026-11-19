# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T00:35:01Z | CORES reading: 2026-11-19 00:30Z | guard sample: 2026-11-19T00:30:01Z
Lead: last LEAD NOTE 3 min ago | last transcript activity 2 min ago | last watchdog line: 2026-11-18 23:26Z WATCHDOG L1 fired: C
github relay last pull OK at 2026-11-19T00:34Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 73.05 | 28 | 26 | 16 | 486 | n/a | n/a | 300 | 60.6 (-27.774 GB/h, n/a h) |
| server2 | 100 | 64 | 103.46 | 18 | 5602 | 16 | 104 | 139610 | 12.5 h | 27071 | 407.7 (0.035 GB/h, n/a h) |
| serverA | 100 | 128 | 223.9 | 97 (grid) + 53 (engine) | 1220 | 0 | 89 | 128593 | 52.7 h | 6328 | 830.0 (0.009 GB/h, n/a h) |
| serverB | 100 | 128 | 169.66 | 99 (grid) + 55 (engine) | 1141 | 0 | 126 | 123351 | 54.1 h | 6312 | 412.3 (0.008 GB/h, n/a h) |

questions for Josh: 4 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 51459 lines pending; fleet rate 1610 set-months/h => 32.0 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
