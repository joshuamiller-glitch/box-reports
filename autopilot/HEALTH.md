# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T03:00:02Z | CORES reading: 2026-11-19 02:55Z | guard sample: 2026-11-19T02:50:01Z
Lead: last LEAD NOTE 7 min ago | last transcript activity 7 min ago | last watchdog line: 2026-11-19 02:16Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-19T02:59Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 59.66 | 21 | 18 | 40 | 591 | n/a | n/a | 299 | 60.5 (0.047 GB/h, n/a h) |
| server2 | 100 | 64 | 96.62 | 11 | 2275 | 40 | 105 | 141104 | 31.0 h | 26976 | 407.6 (0.031 GB/h, n/a h) |
| serverA | 100 | 128 | 201.95 | 61 (grid) + 77 (engine) | 642 | 0 | 165 | 85699 | 66.7 h | 6313 | 830.0 (0.006 GB/h, n/a h) |
| serverB | 100 | 128 | 184.65 | 61 (grid) + 77 (engine) | 569 | 0 | 200 | 81030 | 71.2 h | 6297 | 412.2 (0.008 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 107873 lines pending; fleet rate 2122 set-months/h => 50.8 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
