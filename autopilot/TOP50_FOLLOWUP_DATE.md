# TOP-50 FOLLOW-UPS DATE (W-NYENG, 2026-11-19 21:20Z; order 2025Z item 4)

Goal: the top 50 own-merit cells per session (NY AM 50 cells, Asia 50 cells after twin removal; REPLACE-K7 / REPLACE-A7 sets) have prior years (37 months), 30 date-shift controls (180), layers (347, W-LAYERS cost) and the exit run (309).

| session | cells | prior years left | controls left | layers left | exit rows left | total left |
|---|---|---|---|---|---|---|
| NYAM | 50 | 1685 | 8130 | 16582 | 15390 | 41787 |
| Asia | 50 | 920 | 7354 | 14011 | 15292 | 37577 |
| **both** | | 2605 | 15484 | 30593 | 30682 | **79364** |

Measured (last 60 min, DONE files): follow-up groups landed {'exit': 170, 'layers': 942, 'controls': 1355, 'urgent': 46, 'ranked prior years': 216, 'STK': 46} = **2775 set-months/h**; mean lease to done 210 s => one engine slot lands 17.1 set-months/h; per host landed: {'67.213.127.157': 1890, '109.94.96.39': 1920, 'box1/dallas': 996, '206.223.224.21': 2086}.

| scenario | follow-up rate | arithmetic | top-50 follow-ups done |
|---|---|---|---|
| current (no C/D) | 2775 /h | 79364 left / (2775 + 0 slots x 17.1) | 2026-11-21 01:56Z (29 h) |
| + Server C at cap 3 (first-dispatch test) | 2826 /h | 79364 left / (2775 + 3 slots x 17.1) | 2026-11-21 01:24Z (28 h) |
| + Server C ramped to 100 slots | 4490 /h | 79364 left / (2775 + 100 slots x 17.1) | 2026-11-20 15:00Z (18 h) |
| + C 100 and D 100 slots (rented for this work) | 6205 /h | 79364 left / (2775 + 200 slots x 17.1) | 2026-11-20 10:07Z (13 h) |

Notes: first looks are not changed (70% of the mix); the exit rows also wait for the exit-family builders; layers by W-LAYERS and exit rows by W-EXITENG consume the same follow-up stream (60% ranked / 20% exit / 20% STK shares inside it); C/D slot counts are the lead figures, the per-slot rate is the measured one above. ranked_follow() now queues the top-50 prior years + controls fully (not only below 6,000 pending) as each first look completes.
