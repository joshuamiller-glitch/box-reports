# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T04:00:01Z | CORES reading: 2026-11-19 03:55Z | guard sample: 2026-11-19T03:50:01Z
Lead: last LEAD NOTE 15 min ago | last transcript activity 2 min ago | last watchdog line: 2026-11-19 03:12Z WATCHDOG L1 fired: E
github relay last pull OK at 2026-11-19T03:59Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 71.12 | 27 | 42 | 101 | 582 | n/a | n/a | 298 | 60.4 (0.044 GB/h, n/a h) |
| server2 | 100 | 64 | 106.85 | 13 | 2474 | 101 | 96 | 137520 | 27.8 h | 26944 | 407.6 (0.03 GB/h, n/a h) |
| serverA | 100 | 128 | 188.35 | 61 (grid) + 77 (engine) | 272 | 0 | 160 | 85378 | 156.9 h | 6309 | 830.0 (0.005 GB/h, n/a h) |
| serverB | 100 | 128 | 167.5 | 61 (grid) + 69 (engine) | 457 | 0 | 200 | 79852 | 87.4 h | 6289 | 412.2 (0.008 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 126352 lines pending; fleet rate 2076 set-months/h => 60.9 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
