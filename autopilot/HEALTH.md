# HEALTH (written by cron every 5 min, not by the lead)

UTC now: 2026-11-19T01:50:01Z | CORES reading: 2026-11-19 01:45Z | guard sample: 2026-11-19T01:40:01Z
Lead: last LEAD NOTE 4 min ago | last transcript activity 0 min ago | last watchdog line: 2026-11-19 01:42Z WATCHDOG L1 fired: A
github relay last pull OK at 2026-11-19T01:49Z

| machine | busy % | threads | load | workers | grid results / 30 min | error stubs / 30 min | engine set-months / 30 min | grid todo (own rows) | grid queue hours | data disk free GB | root disk free GB (fill GB/h, hours left) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| box1 | 100 | 32 | 71.01 | 29 | 53 | 30 | 478 | n/a | n/a | 299 | 60.5 (-17.146 GB/h, n/a h) |
| server2 | 100 | 64 | 100.14 | 12 | 2153 | 30 | 103 | 141576 | 32.9 h | 26995 | 407.6 (0.031 GB/h, n/a h) |
| serverA | 99 | 128 | 139.34 | 61 (grid) + 57 (engine) | 981 | 0 | 86 | 86584 | 44.1 h | 6321 | 830.0 (0.005 GB/h, n/a h) |
| serverB | 100 | 128 | 180.26 | 99 (grid) + 52 (engine) | 793 | 0 | 143 | 80021 | 50.5 h | 6305 | 412.3 (0.005 GB/h, n/a h) |

questions for Josh: 4 open
Rule A (no machine < 90% of its real threads while work exists anywhere): OK: all four >= 90%


Engine queue (shared by box 1, server 2, A, B): 71606 lines pending; fleet rate 1620 set-months/h => 44.2 h of queue left
Alerts from the guard (E = host producing nothing / unreachable, F = disk < 100 GB): none

Rule of thumb: every machine needs >= 12 h of queued work with no decision (grid queue hours per machine above; engine queue hours above).
