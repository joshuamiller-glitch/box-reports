# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T23:05:01Z | CORES reading: 2026-11-18 23:00Z | guard sample: 2026-11-18T23:00:01Z
Lead: last LEAD NOTE 20 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-18 22:34Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-18T23:04Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 72.61 | 33 | 42 | 107 | 444 | n/a | n/a | 301 | 60.7 (None GB/h, n/a h) |
| server2 | 100 | 64 | 130.36 | 12 | 3011 | 101 | 86 | 25670 | 4.3 h | 27157 | 407.7 (None GB/h, n/a h) |
| serverA | 100 | 128 | 329.64 | 189 (grid) + 57 (engine) | 1356 | 0 | 63 | 154343 | 56.9 h | 6334 | 830.0 (None GB/h, n/a h) |
| serverB | 100 | 128 | 306.58 | 187 (grid) + 53 (engine) | 1842 | 0 | 122 | 141937 | 38.5 h | 6319 | 412.3 (None GB/h, n/a h) |

questions for Josh: 3 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 27642 lines pending; fleet rate 1430 set-months/h => 19.3 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
