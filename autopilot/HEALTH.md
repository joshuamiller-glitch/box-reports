# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T22:35:02Z | CORES reading: 2026-11-18 22:30Z | guard sample: 2026-11-18T22:30:01Z
Lead: last LEAD NOTE 8 min ago | last transcript activity 0 min ago | last watchdog line: 2026-11-18 22:34Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-18T22:34Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | disk free GB |
|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 69.37 | 33 | 36 | 6 | 450 | n/a | n/a | 354 |
| server2 | 100 | 64 | 178.01 | 14 | 2307 | 17 | 105 | 26264 | 5.7 h | 27192 |
| serverA | 100 | 128 | 340.51 | 189 (grid) + 53 (engine) | 459 | 11 | 93 | 155197 | 169.1 h | 6337 |
| serverB | 100 | 128 | 324.42 | 187 (grid) + 57 (engine) | 294 | 0 | 155 | 143064 | 243.3 h | 6323 |

questions for Josh: 3 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 8048 lines pending; fleet rate 1606 set-months/h => 5.0 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
