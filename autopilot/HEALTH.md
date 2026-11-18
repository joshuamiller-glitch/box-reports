# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T23:00:01Z | CORES reading: 2026-11-18 22:55Z | guard sample: 2026-11-18T22:50:01Z
Lead: last LEAD NOTE 15 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-18 22:34Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-18T22:59Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 74.01 | 34 | 50 | 18 | 435 | n/a | n/a | 301 | 60.7 (None GB/h, n/a h) |
| server2 | 100 | 64 | 127.99 | 14 | 2560 | 9 | 89 | 26264 | 5.1 h | 27173 | 407.7 (None GB/h, n/a h) |
| serverA | 100 | 128 | 334.97 | 189 (grid) + 57 (engine) | 572 | 0 | 73 | 155197 | 135.7 h | 6336 | 830.0 (None GB/h, n/a h) |
| serverB | 100 | 128 | 306.72 | 187 (grid) + 52 (engine) | 695 | 0 | 126 | 143064 | 102.9 h | 6321 | 412.3 (None GB/h, n/a h) |

questions for Josh: 3 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 25516 lines pending; fleet rate 1446 set-months/h => 17.6 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
