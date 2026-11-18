# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T23:20:01Z | CORES reading: 2026-11-18 23:15Z | guard sample: 2026-11-18T23:10:01Z
Lead: last LEAD NOTE 35 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-18 22:34Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-18T23:19Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 71.13 | 30 | 20 | 118 | 424 | n/a | n/a | 301 | 60.7 (-94.776 GB/h, n/a h) |
| server2 | 100 | 64 | 119.15 | 14 | 4088 | 118 | 90 | 25670 | 3.1 h | 27151 | 407.7 (0.032 GB/h, n/a h) |
| serverA | 100 | 128 | 322.71 | 189 (grid) + 57 (engine) | 1700 | 0 | 69 | 154343 | 45.4 h | 6334 | 830.0 (0.0 GB/h, n/a h) |
| serverB | 100 | 128 | 304.19 | 187 (grid) + 53 (engine) | 2089 | 0 | 127 | 141937 | 34.0 h | 6318 | 412.3 (0.0 GB/h, n/a h) |

questions for Josh: 3 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 32774 lines pending; fleet rate 1420 set-months/h => 23.1 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
