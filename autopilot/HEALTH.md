# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T00:30:01Z | CORES reading: 2026-11-19 00:25Z | guard sample: 2026-11-19T00:20:01Z
Lead: last LEAD NOTE 12 min ago | last transcript activity 2 min ago | last watchdog line: 2026-11-18 23:26Z WATCHDOG L1 fired: C
github relay last pull OK at 2026-11-19T00:29Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 67.9 | 28 | 24 | 9 | 459 | n/a | n/a | 300 | 60.6 (-30.469 GB/h, n/a h) |
| server2 | 97 | 64 | 80.86 | 14 | 5013 | 9 | 99 | 95614 | 9.5 h | 27074 | 407.7 (0.033 GB/h, n/a h) |
| serverA | 100 | 128 | 226.2 | 97 (grid) + 54 (engine) | 941 | 0 | 76 | 128593 | 68.3 h | 6329 | 830.0 (0.01 GB/h, n/a h) |
| serverB | 100 | 128 | 178.22 | 99 (grid) + 57 (engine) | 954 | 0 | 122 | 123351 | 64.6 h | 6313 | 412.3 (0.009 GB/h, n/a h) |

questions for Josh: 4 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 50028 lines pending; fleet rate 1512 set-months/h => 33.1 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
