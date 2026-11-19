# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T04:20:01Z | CORES reading: 2026-11-19 04:15Z | guard sample: 2026-11-19T04:10:01Z
Lead: last LEAD NOTE 12 min ago | last transcript activity 3 min ago | last watchdog line: 2026-11-19 03:12Z WATCHDOG L1 fired: E
github relay last pull OK at 2026-11-19T04:19Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 74.44 | 24 | 106 | 8 | 528 | n/a | n/a | 298 | 60.4 (0.042 GB/h, n/a h) |
| server2 | 100 | 64 | 91.05 | 13 | 1920 | 8 | 95 | 137520 | 35.8 h | 26934 | 407.6 (0.029 GB/h, n/a h) |
| serverA | 100 | 128 | 168.57 | 61 (grid) + 75 (engine) | 279 | 0 | 147 | 85378 | 153.0 h | 6307 | 830.0 (0.004 GB/h, n/a h) |
| serverB | 100 | 128 | 159.99 | 61 (grid) + 67 (engine) | 565 | 0 | 186 | 79852 | 70.7 h | 6287 | 412.2 (0.01 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 141626 lines pending; fleet rate 1912 set-months/h => 74.1 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
