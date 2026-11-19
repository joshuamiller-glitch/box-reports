# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T02:00:02Z | CORES reading: 2026-11-19 01:55Z | guard sample: 2026-11-19T01:50:01Z
Lead: last LEAD NOTE 5 min ago | last transcript activity 0 min ago | last watchdog line: 2026-11-19 01:42Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-19T01:59Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 67.07 | 19 | 50 | 30 | 473 | n/a | n/a | 299 | 60.5 (-16.256 GB/h, n/a h) |
| server2 | 100 | 64 | 113.04 | 13 | 1758 | 30 | 102 | 141415 | 40.2 h | 26992 | 407.6 (0.034 GB/h, n/a h) |
| serverA | 93 | 128 | 130.44 | 61 (grid) + 51 (engine) | 885 | 0 | 98 | 85741 | 48.4 h | 6320 | 830.0 (0.005 GB/h, n/a h) |
| serverB | 100 | 128 | 157.77 | 99 (grid) + 57 (engine) | 775 | 0 | 138 | 79283 | 51.2 h | 6304 | 412.2 (0.007 GB/h, n/a h) |

questions for Josh: 5 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 85447 lines pending; fleet rate 1622 set-months/h => 52.7 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
