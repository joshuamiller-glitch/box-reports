# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T03:45:01Z | CORES reading: 2026-11-19 03:40Z | guard sample: 2026-11-19T03:40:02Z
Lead: last LEAD NOTE 1 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-19 03:12Z WATCHDOG L1 fired: E
github relay last pull OK at 2026-11-19T03:44Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 62.12 | 23 | 59 | 101 | 571 | n/a | n/a | 298 | 60.5 (0.045 GB/h, n/a h) |
| server2 | 100 | 64 | 105.76 | 14 | 3080 | 100 | 92 | 137362 | 22.3 h | 26947 | 407.6 (0.029 GB/h, n/a h) |
| serverA | 100 | 128 | 181.71 | 61 (grid) + 73 (engine) | 237 | 0 | 162 | 85302 | 180.0 h | 6309 | 830.0 (0.006 GB/h, n/a h) |
| serverB | 100 | 128 | 170.05 | 61 (grid) + 73 (engine) | 678 | 0 | 195 | 79778 | 58.8 h | 6290 | 412.2 (0.008 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 120479 lines pending; fleet rate 2040 set-months/h => 59.1 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
