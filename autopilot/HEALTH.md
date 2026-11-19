# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T04:30:01Z | CORES reading: 2026-11-19 04:25Z | guard sample: 2026-11-19T04:20:01Z
Lead: last LEAD NOTE 3 min ago | last transcript activity 2 min ago | last watchdog line: 2026-11-19 04:22Z WATCHDOG L1 fired: E
github relay last pull OK at 2026-11-19T04:29Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 82.9 | 25 | 105 | 8 | 512 | n/a | n/a | 298 | 60.4 (0.042 GB/h, n/a h) |
| server2 | 100 | 64 | 91.22 | 12 | ? | ? | ? | ? | ? | ? | ? |
| serverA | 100 | 128 | 171.29 | 61 (grid) + 71 (engine) | 259 | 0 | 145 | 85098 | 164.3 h | 6307 | 829.9 (0.006 GB/h, n/a h) |
| serverB | 100 | 128 | 155.7 | 61 (grid) + 73 (engine) | 761 | 0 | 180 | 79335 | 52.1 h | 6286 | 412.2 (0.01 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 148930 lines pending; fleet rate 1674 set-months/h => 89.0 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): E:server2:unreachable (IndexError('list index out of range'))

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
