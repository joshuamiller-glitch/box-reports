# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T22:45:01Z | CORES reading: 2026-11-18 22:40Z | guard sample: 2026-11-18T22:40:01Z
Lead: last LEAD NOTE 18 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-18 22:34Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-18T22:44Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 67.99 | 24 | 52 | 6 | 468 | n/a | n/a | 325 | 24.2 (None GB/h, n/a h) |
| server2 | 100 | 64 | 124.93 | 12 | 2172 | 17 | 98 | 26264 | 6.0 h | 27182 | 407.7 (None GB/h, n/a h) |
| serverA | 100 | 128 | 332.94 | 189 (grid) + 57 (engine) | 523 | 11 | 90 | 155197 | 148.4 h | 6337 | 830.0 (None GB/h, n/a h) |
| serverB | 100 | 128 | 302.3 | 187 (grid) + 57 (engine) | 533 | 0 | 142 | 143064 | 134.2 h | 6322 | 412.3 (None GB/h, n/a h) |

questions for Josh: 3 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 11554 lines pending; fleet rate 1596 set-months/h => 7.2 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
