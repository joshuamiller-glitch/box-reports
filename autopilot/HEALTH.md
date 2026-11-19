# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T03:05:01Z | CORES reading: 2026-11-19 03:00Z | guard sample: 2026-11-19T03:00:02Z
Lead: last LEAD NOTE 12 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-19 03:02Z WATCHDOG L1 fired: E
github relay last pull OK at 2026-11-19T03:04Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 64.1 | 25 | 29 | 27 | 598 | n/a | n/a | 299 | 60.5 (0.047 GB/h, n/a h) |
| server2 | 100 | 64 | 97.07 | 14 | 1987 | 25 | 106 | 141104 | 35.5 h | 26967 | 407.6 (0.031 GB/h, n/a h) |
| serverA | 100 | 128 | 209.38 | 61 (grid) + 75 (engine) | 166 | 0 | 172 | 85699 | 258.1 h | 6313 | 830.0 (0.006 GB/h, n/a h) |
| serverB | 100 | 128 | 181.05 | 61 (grid) + 77 (engine) | 473 | 0 | 199 | 81030 | 85.7 h | 6295 | 412.2 (0.008 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 108647 lines pending; fleet rate 2150 set-months/h => 50.5 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): E:serverA:grid workers 60 but 166 results in 30 min (usual 903)

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
