# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T01:05:01Z | CORES reading: 2026-11-19 01:00Z | guard sample: 2026-11-19T01:00:01Z
Lead: last LEAD NOTE 17 min ago | last transcript activity 7 min ago | last watchdog line: 2026-11-18 23:26Z WATCHDOG L1 fired: C
github relay last pull OK at 2026-11-19T01:04Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 71.03 | 32 | 20 | 0 | 494 | n/a | n/a | 300 | 60.6 (-21.944 GB/h, n/a h) |
| server2 | 100 | 64 | 102.93 | 14 | 2299 | 0 | 121 | 138272 | 30.1 h | 27037 | 407.7 (0.034 GB/h, n/a h) |
| serverA | 100 | 128 | 142.58 | 61 (grid) + 53 (engine) | 1173 | 0 | 87 | 88567 | 37.8 h | 6325 | 830.0 (0.007 GB/h, n/a h) |
| serverB | 100 | 128 | 181.98 | 99 (grid) + 57 (engine) | 1350 | 0 | 138 | 80856 | 29.9 h | 6308 | 412.3 (0.007 GB/h, n/a h) |

questions for Josh: 4 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 59004 lines pending; fleet rate 1680 set-months/h => 35.1 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
