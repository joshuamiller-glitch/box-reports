# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T22:30:01Z | CORES reading: 2026-11-18 22:25Z | guard sample: 2026-11-18T22:20:01Z
Lead: last LEAD NOTE 3 min ago | last transcript activity 2 min ago | last watchdog line: 2026-11-18 22:18Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-18T22:29Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | disk free GB |
|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 79.78 | 29 | 27 | 37 | 463 | n/a | n/a | 354 |
| server2 | 98 | 64 | 77.63 | 12 | 3239 | 52 | 108 | 27731 | 4.3 h | 27205 |
| serverA | 100 | 128 | 266.54 | 97 (grid) + 57 (engine) | 567 | 11 | 97 | 158737 | 140.0 h | 6338 |
| serverB | 100 | 128 | 250.01 | 99 (grid) + 57 (engine) | 381 | 0 | 156 | 147199 | 193.2 h | 6324 |

questions for Josh: 3 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 6752 lines pending; fleet rate 1648 set-months/h => 4.1 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
