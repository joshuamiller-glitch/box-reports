# TOP-50 FOLLOW-UPS DATE (W-NYENG, 2026-11-19 20:25Z; order 2025Z item 4)

Goal: the top 50 own-merit cells per session (NY AM 50 cells, Asia 50 cells after twin removal; REPLACE-K7 / REPLACE-A7 sets) have prior years (37 months), 30 date-shift controls (180), layers (347, W-LAYERS cost) and the exit run (309).

| session | cells | prior years left | controls left | layers left | exit rows left | total left |
|---|---|---|---|---|---|---|
| NYAM | 50 | 1685 | 8560 | 16912 | 15390 | 42547 |
| Asia | 50 | 987 | 8084 | 14444 | 15292 | 38807 |
| **both** | | 2672 | 16644 | 31356 | 30682 | **81354** |

Measured (last 60 min, DONE files): follow-up groups landed {'STK': 419, 'layers': 264, 'controls': 338, 'exit': 128, 'ranked prior years': 227, 'urgent': 28} = **1404 set-months/h**; mean lease to done 221 s => one engine slot lands 16.3 set-months/h; per host landed: {'box1/dallas': 928, '206.223.224.21': 1909, '109.94.96.39': 1694, '67.213.127.157': 82}.

| scenario | follow-up rate | arithmetic | top-50 follow-ups done |
|---|---|---|---|
| current (no C/D) | 1404 /h | 81354 left / (1404 + 0 slots x 16.3) | 2026-11-22 06:22Z (58 h) |
| + Server C at cap 3 (first-dispatch test) | 1453 /h | 81354 left / (1404 + 3 slots x 16.3) | 2026-11-22 04:25Z (56 h) |
| + Server C ramped to 100 slots | 3033 /h | 81354 left / (1404 + 100 slots x 16.3) | 2026-11-20 23:14Z (27 h) |
| + C 100 and D 100 slots (rented for this work) | 4663 /h | 81354 left / (1404 + 200 slots x 16.3) | 2026-11-20 13:52Z (17 h) |

Notes: first looks are not changed (70% of the mix); the exit rows also wait for the exit-family builders; layers by W-LAYERS and exit rows by W-EXITENG consume the same follow-up stream (60% ranked / 20% exit / 20% STK shares inside it); C/D slot counts are the lead figures, the per-slot rate is the measured one above. ranked_follow() now queues the top-50 prior years + controls fully (not only below 6,000 pending) as each first look completes.
