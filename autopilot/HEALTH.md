# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T00:05:01Z | CORES reading: 2026-11-19 00:00Z | guard sample: 2026-11-19T00:00:01Z
Lead: last LEAD NOTE 3 min ago | last transcript activity 0 min ago | last watchdog line: 2026-11-18 23:26Z WATCHDOG L1 fired: C
github relay last pull OK at 2026-11-19T00:04Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 78.47 | 31 | 21 | 11 | 436 | n/a | n/a | 301 | 60.6 (-37.804 GB/h, n/a h) |
| server2 | 100 | 64 | 106.67 | 14 | 3412 | 11 | 98 | 24300 | 3.6 h | 27104 | 407.7 (0.027 GB/h, n/a h) |
| serverA | 100 | 128 | 320.69 | 189 (grid) + 57 (engine) | 928 | 0 | 57 | 151999 | 81.9 h | 6330 | 830.0 (0.011 GB/h, n/a h) |
| serverB | 100 | 128 | 282.43 | 187 (grid) + 55 (engine) | 716 | 0 | 125 | 139281 | 97.3 h | 6314 | 412.3 (0.011 GB/h, n/a h) |

questions for Josh: 4 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 44990 lines pending; fleet rate 1432 set-months/h => 31.4 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
