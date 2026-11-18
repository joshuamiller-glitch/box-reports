# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T22:25:02Z | CORES reading: 2026-11-18 22:20Z | guard sample: 2026-11-18T22:20:01Z
Lead: last LEAD NOTE 3 min ago | last transcript activity 3 min ago | last watchdog line: 2026-11-18 22:18Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-18T22:24Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | disk free GB |
|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 89.03 | 20 | 27 | 37 | 463 | n/a | n/a | 354 |
| server2 | 100 | 64 | 74.79 | 14 | 3239 | 52 | 108 | 27731 | 4.3 h | 27205 |
| serverA | 100 | 128 | 346.31 | 93 (grid) + 55 (engine) | 567 | 11 | 97 | 158737 | 140.0 h | 6338 |
| serverB | 100 | 128 | 304.42 | 89 (grid) + 55 (engine) | 381 | 0 | 156 | 147199 | 193.2 h | 6324 |

questions for Josh: 3 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 6415 lines pending; fleet rate 1648 set-months/h => 3.9 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
