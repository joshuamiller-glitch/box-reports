# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T03:20:01Z | CORES reading: 2026-11-19 03:15Z | guard sample: 2026-11-19T03:10:01Z
Lead: last LEAD NOTE 1 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-19 03:12Z WATCHDOG L1 fired: E
github relay last pull OK at 2026-11-19T03:19Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 63.91 | 26 | 50 | 27 | 596 | n/a | n/a | 298 | 60.5 (0.046 GB/h, n/a h) |
| server2 | 100 | 64 | 97.64 | 14 | 2000 | 27 | 104 | 139814 | 35.0 h | 26963 | 407.6 (0.032 GB/h, n/a h) |
| serverA | 100 | 128 | 188.82 | 61 (grid) + 75 (engine) | 115 | 0 | 174 | 85538 | 371.9 h | 6312 | 830.0 (0.008 GB/h, n/a h) |
| serverB | 100 | 128 | 173.07 | 61 (grid) + 64 (engine) | 387 | 0 | 202 | 80524 | 104.0 h | 6294 | 412.2 (0.008 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 112404 lines pending; fleet rate 2152 set-months/h => 52.2 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): E:serverA:grid workers 60 but 115 results in 30 min (usual 811)

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
