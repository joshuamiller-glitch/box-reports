# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T02:15:01Z | CORES reading: 2026-11-19 02:10Z | guard sample: 2026-11-19T02:10:01Z
Lead: last LEAD NOTE 20 min ago | last transcript activity 0 min ago | last watchdog line: 2026-11-19 01:42Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-19T02:14Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 66.39 | 23 | 38 | 15 | 464 | n/a | n/a | 299 | 60.5 (-14.727 GB/h, n/a h) |
| server2 | 100 | 64 | 98.18 | 12 | 1699 | 15 | 96 | 141415 | 41.6 h | 26988 | 407.6 (0.031 GB/h, n/a h) |
| serverA | 95 | 128 | 122.69 | 61 (grid) + 51 (engine) | 770 | 0 | 87 | 85741 | 55.7 h | 6318 | 830.0 (0.005 GB/h, n/a h) |
| serverB | 93 | 128 | 118.72 | 61 (grid) + 53 (engine) | 396 | 0 | 138 | 79165 | 100.0 h | 6303 | 412.2 (0.009 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 91250 lines pending; fleet rate 1570 set-months/h => 58.1 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
