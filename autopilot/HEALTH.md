# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T21:55:01Z | CORES reading: 2026-11-18 21:50Z | guard sample: 2026-11-18T21:50:01Z
Lead: last LEAD NOTE 7 min ago | last transcript activity 0 min ago | last watchdog line: 2026-11-18 21:42Z WATCHDOG L1 fired: C
github relay last pull OK at 2026-11-18T21:54Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | disk free GB |
|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 72.54 | 16 | 44 | 18 | 417 | n/a | n/a | 354 |
| server2 | 100 | 64 | 83.54 | 14 | 1931 | 107 | 101 | 31329 | 8.1 h | 27247 |
| serverA | 100 | 128 | 268.25 | 93 (grid) + 57 (engine) | 1042 | 11 | 78 | 159615 | 76.6 h | 6340 |
| serverB | 100 | 128 | 273.34 | 89 (grid) + 54 (engine) | 788 | 5 | 132 | 147916 | 93.9 h | 6326 |

questions for Josh: 3 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 5621 lines pending; fleet rate 1456 set-months/h => 3.9 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
