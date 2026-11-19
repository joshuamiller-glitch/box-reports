# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T03:10:01Z | CORES reading: 2026-11-19 03:05Z | guard sample: 2026-11-19T03:00:02Z
Lead: last LEAD NOTE 17 min ago | last transcript activity 6 min ago | last watchdog line: 2026-11-19 03:02Z WATCHDOG L1 fired: E
github relay last pull OK at 2026-11-19T03:09Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 62.18 | 19 | 29 | 27 | 598 | n/a | n/a | 299 | 60.5 (0.047 GB/h, n/a h) |
| server2 | 100 | 64 | 100.03 | 14 | 1987 | 25 | 106 | 141104 | 35.5 h | 26967 | 407.6 (0.031 GB/h, n/a h) |
| serverA | 100 | 128 | 209.16 | 61 (grid) + 73 (engine) | 166 | 0 | 172 | 85699 | 258.1 h | 6313 | 830.0 (0.006 GB/h, n/a h) |
| serverB | 100 | 128 | 169.15 | 61 (grid) + 71 (engine) | 473 | 0 | 199 | 81030 | 85.7 h | 6295 | 412.2 (0.008 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 110345 lines pending; fleet rate 2150 set-months/h => 51.3 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): E:serverA:grid workers 60 but 166 results in 30 min (usual 903)

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
