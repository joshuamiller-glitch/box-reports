# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T03:35:02Z | CORES reading: 2026-11-19 03:30Z | guard sample: 2026-11-19T03:30:01Z
Lead: last LEAD NOTE 16 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-19 03:12Z WATCHDOG L1 fired: E
github relay last pull OK at 2026-11-19T03:34Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 68.26 | 25 | 84 | 42 | 598 | n/a | n/a | 298 | 60.5 (0.048 GB/h, n/a h) |
| server2 | 100 | 64 | 105.53 | 14 | 3328 | 10 | 97 | 139814 | 21.0 h | 26949 | 407.6 (0.029 GB/h, n/a h) |
| serverA | 100 | 128 | 177.77 | 61 (grid) + 75 (engine) | 235 | 0 | 169 | 85538 | 182.0 h | 6310 | 830.0 (0.008 GB/h, n/a h) |
| serverB | 100 | 128 | 160.91 | 61 (grid) + 71 (engine) | 751 | 0 | 209 | 80524 | 53.6 h | 6291 | 412.2 (0.008 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 116796 lines pending; fleet rate 2146 set-months/h => 54.4 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
