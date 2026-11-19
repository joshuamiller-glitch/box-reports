# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T01:35:01Z | CORES reading: 2026-11-19 01:30Z | guard sample: 2026-11-19T01:30:02Z
Lead: last LEAD NOTE 7 min ago | last transcript activity 0 min ago | last watchdog line: 2026-11-19 01:24Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-19T01:34Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 79.23 | 29 | 43 | 30 | 469 | n/a | n/a | 299 | 60.5 (-18.139 GB/h, n/a h) |
| server2 | 99 | 64 | 119.67 | 14 | 3079 | 30 | 104 | 141576 | 23.0 h | 27009 | 407.6 (0.033 GB/h, n/a h) |
| serverA | 99 | 128 | 149.07 | 61 (grid) + 57 (engine) | 1846 | 0 | 77 | 86584 | 23.5 h | 6322 | 830.0 (0.006 GB/h, n/a h) |
| serverB | 100 | 128 | 171.53 | 99 (grid) + 57 (engine) | 617 | 0 | 142 | 80021 | 64.8 h | 6305 | 412.3 (0.005 GB/h, n/a h) |

questions for Josh: 4 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 68476 lines pending; fleet rate 1584 set-months/h => 43.2 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
