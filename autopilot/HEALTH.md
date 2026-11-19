# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T02:25:01Z | CORES reading: 2026-11-19 02:20Z | guard sample: 2026-11-19T02:20:01Z
Lead: last LEAD NOTE 8 min ago | last transcript activity 1 min ago | last watchdog line: 2026-11-19 02:16Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-19T02:24Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 63.23 | 25 | 34 | 15 | 483 | n/a | n/a | 299 | 60.5 (-14.065 GB/h, n/a h) |
| server2 | 100 | 64 | 86.15 | 14 | 1125 | 15 | 92 | 141303 | 62.8 h | 26986 | 407.6 (0.03 GB/h, n/a h) |
| serverA | 90 | 128 | 124.35 | 61 (grid) + 76 (engine) | 811 | 0 | 93 | 84883 | 52.3 h | 6317 | 830.0 (0.004 GB/h, n/a h) |
| serverB | 94 | 128 | 137.49 | 61 (grid) + 77 (engine) | 245 | 0 | 147 | 79165 | 161.6 h | 6302 | 412.2 (0.009 GB/h, n/a h) |

questions for Josh: 6 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 95243 lines pending; fleet rate 1630 set-months/h => 58.4 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
