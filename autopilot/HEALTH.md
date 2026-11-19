# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T01:25:01Z | CORES reading: 2026-11-19 01:20Z | guard sample: 2026-11-19T01:20:01Z
Lead: last LEAD NOTE 1 min ago | last transcript activity 0 min ago | last watchdog line: 2026-11-19 01:24Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-19T01:24Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 82.0 | 33 | 40 | 0 | 471 | n/a | n/a | 299 | 60.6 (-19.253 GB/h, n/a h) |
| server2 | 100 | 64 | 77.76 | 13 | 2398 | 0 | 106 | 138272 | 28.8 h | 27015 | 407.6 (0.033 GB/h, n/a h) |
| serverA | 97 | 128 | 128.35 | 61 (grid) + 57 (engine) | 1996 | 0 | 72 | 86584 | 21.7 h | 6322 | 830.0 (0.006 GB/h, n/a h) |
| serverB | 100 | 128 | 167.47 | 99 (grid) + 57 (engine) | 734 | 0 | 148 | 80021 | 54.5 h | 6306 | 412.3 (0.006 GB/h, n/a h) |

questions for Josh: 4 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 64931 lines pending; fleet rate 1594 set-months/h => 40.7 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
