# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T00:20:01Z | CORES reading: 2026-11-19 00:15Z | guard sample: 2026-11-19T00:19:07Z
Lead: last LEAD NOTE 2 min ago | last transcript activity 0 min ago | last watchdog line: 2026-11-18 23:26Z WATCHDOG L1 fired: C
github relay last pull OK at 2026-11-19T00:19Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 70.94 | 30 | 24 | 10 | 453 | n/a | n/a | 300 | 60.6 (-30.74 GB/h, n/a h) |
| server2 | 84 | 64 | 65.7 | 14 | 5138 | 10 | 98 | 95614 | 9.3 h | 27074 | 407.7 (0.033 GB/h, n/a h) |
| serverA | 100 | 128 | 219.79 | 97 (grid) + 57 (engine) | 901 | 0 | 74 | 128593 | 71.4 h | 6329 | 830.0 (0.01 GB/h, n/a h) |
| serverB | 98 | 128 | 206.81 | 99 (grid) + 57 (engine) | 859 | 0 | 121 | 123351 | 71.8 h | 6313 | 412.3 (0.009 GB/h, n/a h) |

questions for Josh: 4 open
Rule A (no machine < 90% of its real threads while work exists anywhere): BELOW 90%%: server2 84%


Engine queue (shared by box 1, server 2, A, B): 47654 lines pending; fleet rate 1492 set-months/h => 31.9 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
