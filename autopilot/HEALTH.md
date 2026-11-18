# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T21:15:01Z | CORES reading: 2026-11-18 21:10Z | guard sample: 2026-11-18T21:10:01Z
Lead: last LEAD NOTE 13 min ago | last transcript activity 2 min ago | last watchdog line: 2026-11-18 20:58Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-18T21:14Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | disk free GB |
|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 63.97 | 20 | 68 | 0 | 429 | n/a | n/a | 354 |
| server2 | 100 | 64 | 80.72 | 14 | 1697 | 171 | 108 | 32371 | 9.5 h | 27269 |
| serverA | 100 | 128 | 212.21 | 93 (grid) + 57 (engine) | 1154 | 16 | 68 | 160632 | 69.6 h | 6343 |
| serverB | 100 | 128 | 203.77 | 89 (grid) + 57 (engine) | 1664 | 32 | 117 | 149241 | 44.8 h | 6332 |

questions for Josh: 3 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 5312 lines pending; fleet rate 1444 set-months/h => 3.7 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
