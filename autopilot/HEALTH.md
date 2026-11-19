# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T01:20:01Z | CORES reading: 2026-11-19 01:15Z | guard sample: 2026-11-19T01:10:01Z
Lead: last LEAD NOTE 4 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-18 23:26Z WATCHDOG L1 fired: C
github relay last pull OK at 2026-11-19T01:19Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 74.55 | 30 | 21 | 0 | 473 | n/a | n/a | 300 | 60.6 (-20.513 GB/h, n/a h) |
| server2 | 100 | 64 | 98.81 | 14 | 2720 | 0 | 108 | 138272 | 25.4 h | 27019 | 407.6 (0.035 GB/h, n/a h) |
| serverA | 100 | 128 | 130.16 | 61 (grid) + 56 (engine) | 1694 | 0 | 80 | 88567 | 26.1 h | 6323 | 830.0 (0.007 GB/h, n/a h) |
| serverB | 100 | 128 | 177.57 | 99 (grid) + 53 (engine) | 1113 | 0 | 143 | 80856 | 36.3 h | 6307 | 412.3 (0.006 GB/h, n/a h) |

questions for Josh: 4 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 63311 lines pending; fleet rate 1608 set-months/h => 39.4 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
