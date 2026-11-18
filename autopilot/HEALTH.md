# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-18T20:49:07Z | CORES reading: 2026-11-18 20:45Z | guard sample: 2026-11-18T20:48:47Z
Lead: last LEAD NOTE 6 min ago | last transcript activity 0 min ago | last watchdog line: none yet
github relay last pull OK at 2026-11-18T20:49Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | disk free GB |
|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 67.81 | 29 | 15 | 0 | 421 | n/a | n/a | 354 |
| server2 | 100 | 64 | 106.95 | 14 | 1144 | 85 | 108 | 33854 | 14.8 h | 27278 |
| serverA | 100 | 128 | 174.89 | 93 (grid) + 55 (engine) | 1326 | 0 | 54 | 160474 | 60.5 h | 6346 |
| serverB | 100 | 128 | 178.62 | 89 (grid) + 53 (engine) | 2384 | 32 | 109 | 149900 | 31.4 h | 6336 |

Engine queue (shared by box 1, server 2, A, B): 4172 lines pending; fleet rate 1384 set-months/h => 3.0 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
