# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T00:15:01Z | CORES reading: 2026-11-19 00:10Z | guard sample: 2026-11-19T00:10:01Z
Lead: last LEAD NOTE 13 min ago | last transcript activity 0 min ago | last watchdog line: 2026-11-18 23:26Z WATCHDOG L1 fired: C
github relay last pull OK at 2026-11-19T00:14Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 67.38 | 28 | 24 | 11 | 437 | n/a | n/a | 301 | 60.6 (-33.742 GB/h, n/a h) |
| server2 | 100 | 64 | 89.12 | 13 | 3912 | 11 | 101 | 24300 | 3.1 h | 27094 | 407.7 (0.036 GB/h, n/a h) |
| serverA | 100 | 128 | 231.19 | 97 (grid) + 57 (engine) | 879 | 0 | 64 | 91368 | 52.0 h | 6330 | 830.0 (0.011 GB/h, n/a h) |
| serverB | 98 | 128 | 176.63 | 99 (grid) + 55 (engine) | 721 | 0 | 128 | 86674 | 60.1 h | 6314 | 412.3 (0.01 GB/h, n/a h) |

questions for Josh: 4 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 46697 lines pending; fleet rate 1460 set-months/h => 32.0 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
