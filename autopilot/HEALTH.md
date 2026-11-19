# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T04:05:01Z | CORES reading: 2026-11-19 04:00Z | guard sample: 2026-11-19T04:01:09Z
Lead: last LEAD NOTE 3 min ago | last transcript activity 7 min ago | last watchdog line: 2026-11-19 03:12Z WATCHDOG L1 fired: E
github relay last pull OK at 2026-11-19T04:04Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 76.49 | 28 | 55 | 57 | 536 | n/a | n/a | 298 | 60.4 (0.044 GB/h, n/a h) |
| server2 | 100 | 64 | 97.88 | 11 | 1387 | 57 | 96 | 137520 | 49.6 h | 26936 | 407.6 (0.028 GB/h, n/a h) |
| serverA | 100 | 128 | 186.4 | 61 (grid) + 65 (engine) | 281 | 0 | 152 | 85378 | 151.9 h | 6308 | 830.0 (0.004 GB/h, n/a h) |
| serverB | 100 | 128 | 159.35 | 61 (grid) + 59 (engine) | 367 | 0 | 188 | 79852 | 108.8 h | 6288 | 412.2 (0.009 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 129510 lines pending; fleet rate 1944 set-months/h => 66.6 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
