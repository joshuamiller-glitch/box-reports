# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T00:00:01Z | CORES reading: 2026-11-18 23:55Z | guard sample: 2026-11-18T23:50:01Z
Lead: last LEAD NOTE 18 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-18 23:26Z WATCHDOG L1 fired: C
github relay last pull OK at 2026-11-18T23:59Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 73.07 | 31 | 24 | 2 | 440 | n/a | n/a | 301 | 60.6 (-42.978 GB/h, n/a h) |
| server2 | 100 | 64 | 109.64 | 14 | 4255 | 0 | 95 | 25221 | 3.0 h | 27122 | 407.7 (0.031 GB/h, n/a h) |
| serverA | 100 | 128 | 320.1 | 189 (grid) + 57 (engine) | 784 | 0 | 62 | 152930 | 97.5 h | 6331 | 830.0 (0.006 GB/h, n/a h) |
| serverB | 100 | 128 | 284.96 | 187 (grid) + 52 (engine) | 853 | 0 | 128 | 139977 | 82.0 h | 6315 | 412.3 (0.013 GB/h, n/a h) |

questions for Josh: 4 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 44445 lines pending; fleet rate 1450 set-months/h => 30.7 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
