# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T22:40:01Z | CORES reading: 2026-11-18 22:35Z | guard sample: 2026-11-18T22:36:47Z
Lead: last LEAD NOTE 13 min ago | last transcript activity 2 min ago | last watchdog line: 2026-11-18 22:34Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-18T22:39Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 64.61 | 31 | 49 | 6 | 464 | n/a | n/a | 354 | 8.2 (None GB/h, n/a h) |
| server2 | 100 | 64 | 121.11 | 12 | 2259 | 17 | 101 | 26264 | 5.8 h | 27183 | 407.7 (None GB/h, n/a h) |
| serverA | 100 | 128 | 338.12 | 189 (grid) + 56 (engine) | 472 | 11 | 91 | 155197 | 164.4 h | 6337 | 830.0 (None GB/h, n/a h) |
| serverB | 100 | 128 | 311.32 | 187 (grid) + 55 (engine) | 526 | 0 | 146 | 143064 | 136.0 h | 6323 | 412.3 (None GB/h, n/a h) |

questions for Josh: 3 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 9796 lines pending; fleet rate 1604 set-months/h => 6.1 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
