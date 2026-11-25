# NY AM 30-MINUTE BLOCK TEST (family TW) on the new fit and books

Research only. Written 2026-11-25 18:05 UTC by code/th_tw/tw_nyam_page.py (scorer tw_score.py, builder tw_gen_nyam.py, hook tw_hooks.py, driver tw_nyam.py). Order: Josh 2026-11-25 15:08Z via the relay. Method, gates and labels exactly as D8_TIME_WINDOWS.md: each 30-minute block of NY AM 09:30-12:00 ET (5 blocks) removed in turn as NEW ENTRIES only (order time in ET, follows daylight time); open trades, brackets and every layer untouched; same engine, 2-lot pick sets. Pick window end 2026-10: L6M = 2026-05..10, L3M = 2026-08..10; prior years 2023-04..2025-12 (no 2025-11). Daily series: house convention (exit date +7h, gross - 4.84 x lots), zero-filled on the pick's trading days. Ulcer = RMS drawdown of the daily cumulative P&L (primary), % = change vs the pick row of the same unit (negative = better).

Verdict = walk-forward persistence >= 0.58 AND prior years not RED (> 30% worse equal-risk $/wk) AND L6M ulcer lower AND L3M ulcer not higher; CHECK = the block removes more than 40% of the trades of a period (never PASS); NO-GAIN = gate ok, ulcer not lower; FAIL = gate failed. Null = best-of-5 blocks under a date-shift of the signal clock (200 draws): the real best must beat 4 of the first 5 draws.

## Best block per subject and unit (from the tables below)

- PRIMARY, whole mix: best 11:30-12:00, L6M ulcer +0.7% (L3M -4.3%), L6M $/wk 17907 vs pick 17388, removed 148 (L6M) / 58 (L3M), 2023/24/25 ulcer +nan / +nan / +nan, WF 0.57, verdict FAIL; null best-of-5 real beats 0 of first 5 (needs 4), p all draws 0.95; random-removal p 0.65
- PRIMARY, book M1: best 11:00-11:30, L6M ulcer -13.5% (L3M -19.3%), L6M $/wk 6779 vs pick 7635, removed 3 (L6M) / 0 (L3M), 2023/24/25 ulcer +nan / +nan / +nan, WF 0.50, verdict FAIL
- PRIMARY, book M2: best 10:00-10:30, L6M ulcer -25.6% (L3M -40.3%), L6M $/wk 1443 vs pick 262, removed 48 (L6M) / 18 (L3M), 2023/24/25 ulcer -18 / -16 / -25, WF 0.65, verdict PASS
- PRIMARY, book M3: best 10:00-10:30, L6M ulcer -24.0% (L3M -14.8%), L6M $/wk 1834 vs pick 1358, removed 18 (L6M) / 7 (L3M), 2023/24/25 ulcer -10 / +17 / +7, WF 0.65, verdict FAIL
- PRIMARY, book M4: best 10:30-11:00, L6M ulcer -1.6% (L3M +26.2%), L6M $/wk 3676 vs pick 5021, removed 67 (L6M) / 16 (L3M), 2023/24/25 ulcer +nan / +nan / +nan, WF 0.43, verdict FAIL
- PRIMARY, book M5: best 10:30-11:00, L6M ulcer -12.7% (L3M -20.2%), L6M $/wk 274 vs pick 272, removed 51 (L6M) / 20 (L3M), 2023/24/25 ulcer +nan / +nan / +nan, WF 0.29, verdict FAIL
- PRIMARY, book M6: best 11:30-12:00, L6M ulcer -14.3% (L3M -9.1%), L6M $/wk 2068 vs pick 2040, removed 35 (L6M) / 16 (L3M), 2023/24/25 ulcer +nan / +nan / +nan, WF 0.50, verdict FAIL
- PRIMARY, book M7: best 11:30-12:00, L6M ulcer -2.4% (L3M -3.9%), L6M $/wk 144 vs pick 108, removed 14 (L6M) / 6 (L3M), 2023/24/25 ulcer +nan / +nan / +nan, WF 0.64, verdict PASS
- PRIMARY, book M8: best 10:30-11:00, L6M ulcer -7.8% (L3M +0.0%), L6M $/wk 732 vs pick 752, removed 6 (L6M) / 3 (L3M), 2023/24/25 ulcer +nan / +nan / +nan, WF 0.71, verdict NO-GAIN
- PRIMARY, book M9: best 10:00-10:30, L6M ulcer -33.3% (L3M -17.2%), L6M $/wk 257 vs pick 205, removed 9 (L6M) / 4 (L3M), 2023/24/25 ulcer +nan / +nan / +nan, WF 0.79, verdict PASS
- BESIDE, whole mix: best 11:00-11:30, L6M ulcer -16.9% (L3M +6.2%), L6M $/wk 17550 vs pick 19159, removed 238 (L6M) / 106 (L3M), 2023/24/25 ulcer +nan / +nan / +nan, WF 0.50, verdict FAIL; null best-of-5 real beats 2 of first 5 (needs 4), p all draws 0.80; random-removal p 0.25
- BESIDE, book M1: best 11:00-11:30, L6M ulcer -12.9% (L3M -21.4%), L6M $/wk 4538 vs pick 4969, removed 14 (L6M) / 5 (L3M), 2023/24/25 ulcer +nan / +nan / +nan, WF 0.57, verdict FAIL
- BESIDE, book M2: best 11:30-12:00, L6M ulcer -9.0% (L3M +9.5%), L6M $/wk 2818 vs pick 2909, removed 20 (L6M) / 8 (L3M), 2023/24/25 ulcer +nan / +nan / +nan, WF 0.64, verdict NO-GAIN
- BESIDE, book M3: best 10:00-10:30, L6M ulcer -6.2% (L3M +2.1%), L6M $/wk 2464 vs pick 2355, removed 24 (L6M) / 10 (L3M), 2023/24/25 ulcer +nan / +nan / +nan, WF 0.57, verdict FAIL
- BESIDE, book M4: best 10:00-10:30, L6M ulcer -11.9% (L3M -10.2%), L6M $/wk 3047 vs pick 4340, removed 199 (L6M) / 56 (L3M), 2023/24/25 ulcer +nan / +nan / +nan, WF 0.50, verdict FAIL
- BESIDE, book M5: best 10:30-11:00, L6M ulcer -55.6% (L3M -50.3%), L6M $/wk 280 vs pick 334, removed 68 (L6M) / 30 (L3M), 2023/24/25 ulcer +nan / +nan / +nan, WF 0.43, verdict FAIL
- BESIDE, book M6: best 10:00-10:30, L6M ulcer -15.3% (L3M +26.2%), L6M $/wk 1638 vs pick 2850, removed 81 (L6M) / 32 (L3M), 2023/24/25 ulcer +nan / +nan / +nan, WF 0.50, verdict FAIL
- BESIDE, book M7: best 10:00-10:30, L6M ulcer -7.1% (L3M +50.5%), L6M $/wk 278 vs pick 458, removed 17 (L6M) / 8 (L3M), 2023/24/25 ulcer +nan / +nan / +nan, WF 0.43, verdict FAIL
- BESIDE, book M8: best 11:30-12:00, L6M ulcer -9.2% (L3M +0.8%), L6M $/wk 1261 vs pick 1259, removed 11 (L6M) / 3 (L3M), 2023/24/25 ulcer +nan / +nan / +nan, WF 0.86, verdict NO-GAIN

Fewer-trades control (Josh standing rule): for every block the same number of trades is removed AT RANDOM from the pick (any time of day, 20 draws) and the L6M ulcer change is recomputed: "random med" = median change, "p rand" = share of random draws that do as well as the real block (a small p means the gain is not just from taking fewer trades). "p shift" = same for the per-block date-shift null (the block placed at a random clock offset on each day). Bare = the truly bare row (no layers), reference only, never a candidate.

## PRIMARY: delivered weighted nine STKd8cd0279ff with pick JT91

Reference rows (stack, all books): pick = TL3_SR_NY_STKd8cd0279ff_BF1_JT91; bare = TL3_SR_NY_STKd8cd0279ff_BF1_BASE (reference only).

| row | L6M ulcer | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | L3M ulcer | L3M maxDD | L3M worst day | L3M worst wk | L3M $/wk | 2023 ulcer | 2024 ulcer | 2025 ulcer | 2023 $/wk | 2024 $/wk | 2025 $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| pick | 9465 | -25973 | -15186 | -7960 | 17388 | 8365 | -21737 | -11284 | -1575 | 10992 | 70766 | 12241 | 22161 | -2150 | 6015 | 6606 |
| bare | 28581 | -99970 | -83394 | -20048 | 51363 | 29290 | -99970 | -77369 | -16356 | 36277 | 45201 | 40989 | 58108 | 10796 | 7854 | 16106 |

### Whole mix (all books), blocks ranked by L6M ulcer (recent first: L6M with L3M beside, then 2023 / 2024 / 2025)

| block ET | L6M ulcer % | L3M ulcer % | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | L3M $/wk | trades removed L6M / L3M | 2023 / 2024 / 2025 ulcer % | 2023 / 2024 / 2025 $/wk | WF persist | random med % | p rand | p shift | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 11:30-12:00 | +0.7 | -4.3 | -26219 | -15186 | -9121 | 17907 | 11440 | 148 / 58 | n/a / n/a / n/a | n/a / n/a / n/a | 0.57 | -3.8 | 0.65 | 0.10 | FAIL |
| 11:00-11:30 | +0.9 | +8.1 | -27273 | -15186 | -7302 | 15686 | 10785 | 139 / 57 | n/a / n/a / n/a | n/a / n/a / n/a | 0.36 | +1.7 | 0.40 | 0.30 | FAIL |
| 10:30-11:00 | +22.3 | -0.2 | -32320 | -15186 | -19486 | 15974 | 9125 | 204 / 74 | n/a / n/a / n/a | n/a / n/a / n/a | 0.57 | +0.0 | 1.00 | 0.85 | FAIL |
| 10:00-10:30 | +35.5 | +0.0 | -43451 | -15186 | -22391 | 15046 | 9920 | 317 / 89 | -22 / +15 / -30 | -988 / 6001 / 8534 | 0.47 | -1.3 | 1.00 | 0.75 | FAIL |
| 09:30-10:00 | +62.8 | +88.2 | -42581 | -13903 | -25186 | 5199 | 3744 | 609 / 170 | -51 / +505 / +8 | 1626 / 647 / 2733 | 0.54 | +1.4 | 0.95 | 1.00 | FAIL |

Pick reference (all books): L6M ulcer 9465, maxDD -25973, worst day -15186, worst wk -7960, $/wk 17388; L3M ulcer 8365, $/wk 10992.

Null (best-of-5 blocks, date-shift of the signal clock, 20 draws): real best L6M ulcer change +0.7%, null best median -11.8%; real beats 0 of the first 5 draws (needs 4) -> FAIL; beats 1 of 20 draws (p of null doing as well = 0.950).

Best block (whole mix, not CHECK): 11:30-12:00, L6M ulcer +0.7% (L3M -4.3%), verdict FAIL (walk-forward persistence 0.57 < 0.58); equal-risk view: $/wk x (pick ulcer / block ulcer) = 17774 vs pick 17388; random removal of the same 148 trades gives median -3.8% (p rand 0.65).

### Per book

#### book M1 (pick ref: L6M ulcer 9698, maxDD -29786, worst day -9574, worst wk -13272, $/wk 7635; L3M ulcer 12525)

| block ET | L6M ulcer % | L3M ulcer % | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | removed L6M / L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| 11:00-11:30 | -13.5 | -19.3 | -25051 | -9574 | -11499 | 6779 | 3 / 0 | n/a / n/a / n/a | 0.50 | FAIL |
| 11:30-12:00 | +1.2 | -0.1 | -29766 | -9574 | -13253 | 7648 | 14 / 4 | n/a / n/a / n/a | 0.71 | NO-GAIN |
| 10:30-11:00 | +9.1 | +2.2 | -29786 | -9574 | -13272 | 7126 | 12 / 4 | n/a / n/a / n/a | 0.36 | FAIL |
| 10:00-10:30 | +32.6 | +8.8 | -34000 | -14393 | -16377 | 5523 | 19 / 2 | -17 / -6 / -25 | 0.60 | NO-GAIN |
| 09:30-10:00 | +132.9 | -33.5 | -54812 | -20613 | -18965 | -258 | 66 / 27 | -54 / +112 / +268 | 0.54 | FAIL |

#### book M2 (pick ref: L6M ulcer 11989, maxDD -31286, worst day -8568, worst wk -14919, $/wk 262; L3M ulcer 10045)

| block ET | L6M ulcer % | L3M ulcer % | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | removed L6M / L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| 10:00-10:30 | -25.6 | -40.3 | -19057 | -8468 | -12161 | 1443 | 48 / 18 | -18 / -16 / -25 | 0.65 | PASS |
| 10:30-11:00 | -0.9 | -9.6 | -30124 | -8468 | -19393 | 358 | 28 / 14 | n/a / n/a / n/a | 0.57 | FAIL |
| 11:00-11:30 | +1.9 | -4.1 | -28602 | -8468 | -12575 | 302 | 14 / 9 | n/a / n/a / n/a | 0.64 | NO-GAIN |
| 11:30-12:00 | +2.5 | +2.5 | -32096 | -9379 | -15153 | 258 | 11 / 4 | n/a / n/a / n/a | 0.64 | NO-GAIN |
| 09:30-10:00 | +60.9 | -28.2 | -31219 | -14885 | -19699 | -1236 | 127 / 65 | +22 / -1 / -39 | 0.66 | CHECK (removes 55% of trades, > 40%) |

#### book M3 (pick ref: L6M ulcer 19272, maxDD -40746, worst day -8198, worst wk -23308, $/wk 1358; L3M ulcer 6549)

| block ET | L6M ulcer % | L3M ulcer % | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | removed L6M / L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| 10:00-10:30 | -24.0 | -14.8 | -38468 | -8198 | -23308 | 1834 | 18 / 7 | -10 / +17 / +7 | 0.65 | FAIL |
| 09:30-10:00 | -14.7 | +42.5 | -27098 | -4092 | -7136 | -198 | 120 / 58 | -74 / +5 / -78 | 0.83 | CHECK (removes 72% of trades, > 40%) |
| 11:30-12:00 | -3.4 | -3.6 | -40632 | -8198 | -23308 | 1669 | 7 / 1 | n/a / n/a / n/a | 0.93 | PASS |
| 10:30-11:00 | -1.3 | -1.6 | -40746 | -8198 | -23308 | 1519 | 6 / 1 | n/a / n/a / n/a | 0.86 | PASS |
| 11:00-11:30 | +3.3 | +0.0 | -41766 | -8198 | -24328 | 1244 | 3 / 1 | n/a / n/a / n/a | 0.79 | NO-GAIN |

#### book M4 (pick ref: L6M ulcer 6864, maxDD -17945, worst day -7936, worst wk -16135, $/wk 5021; L3M ulcer 6167)

| block ET | L6M ulcer % | L3M ulcer % | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | removed L6M / L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| 10:30-11:00 | -1.6 | +26.2 | -17146 | -7611 | -10911 | 3676 | 67 / 16 | n/a / n/a / n/a | 0.43 | FAIL |
| 11:30-12:00 | +0.2 | -4.9 | -17945 | -7936 | -16135 | 5160 | 21 / 8 | n/a / n/a / n/a | 0.71 | NO-GAIN |
| 11:00-11:30 | +55.2 | +28.3 | -20001 | -9968 | -18167 | 4131 | 43 / 15 | n/a / n/a / n/a | 0.50 | FAIL |
| 09:30-10:00 | +67.8 | -34.1 | -21292 | -16787 | -16787 | 1773 | 292 / 74 | +9 / +11 / +11 | 0.59 | CHECK (removes 56% of trades, > 40%) |
| 10:00-10:30 | +113.0 | -26.3 | -36342 | -9616 | -19037 | 3250 | 96 / 15 | -2 / -29 / -14 | 0.55 | FAIL |

#### book M5 (pick ref: L6M ulcer 5274, maxDD -11946, worst day -5833, worst wk -8636, $/wk 272; L3M ulcer 5505)

| block ET | L6M ulcer % | L3M ulcer % | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | removed L6M / L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| 09:30-10:00 | -25.1 | -9.5 | -11219 | -4699 | -6718 | 510 | 79 / 39 | -15 / -28 / +7 | 0.69 | CHECK (removes 40% of trades, > 40%) |
| 10:30-11:00 | -12.7 | -20.2 | -11325 | -6664 | -8776 | 274 | 51 / 20 | n/a / n/a / n/a | 0.29 | FAIL |
| 11:30-12:00 | -1.9 | -7.9 | -10811 | -4413 | -5672 | 236 | 34 / 13 | n/a / n/a / n/a | 0.43 | FAIL |
| 11:00-11:30 | +4.9 | -16.8 | -9997 | -5833 | -8956 | 404 | 32 / 15 | n/a / n/a / n/a | 0.43 | FAIL |
| 10:00-10:30 | +35.7 | +68.5 | -16074 | -4934 | -8487 | 202 | 60 / 29 | -12 / -9 / +30 | 0.54 | FAIL |

#### book M6 (pick ref: L6M ulcer 4248, maxDD -9719, worst day -6344, worst wk -6090, $/wk 2040; L3M ulcer 3577)

| block ET | L6M ulcer % | L3M ulcer % | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | removed L6M / L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| 11:30-12:00 | -14.3 | -9.1 | -9406 | -6344 | -6460 | 2068 | 35 / 16 | n/a / n/a / n/a | 0.50 | FAIL |
| 11:00-11:30 | -4.1 | +10.4 | -9801 | -6344 | -6555 | 2187 | 14 / 6 | n/a / n/a / n/a | 0.57 | FAIL |
| 10:30-11:00 | -2.5 | -10.1 | -10756 | -6344 | -4337 | 1874 | 34 / 14 | n/a / n/a / n/a | 0.43 | FAIL |
| 09:30-10:00 | +21.6 | -16.6 | -9996 | -5154 | -6625 | 435 | 157 / 73 | -44 / +45 / -25 | 0.65 | CHECK (removes 53% of trades, > 40%) |
| 10:00-10:30 | +49.0 | +44.4 | -16143 | -5268 | -5319 | 1540 | 77 / 25 | -27 / +11 / -12 | 0.52 | FAIL |

#### book M7 (pick ref: L6M ulcer 4270, maxDD -10468, worst day -2405, worst wk -5129, $/wk 108; L3M ulcer 6011)

| block ET | L6M ulcer % | L3M ulcer % | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | removed L6M / L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| 09:30-10:00 | -45.4 | -89.6 | -5774 | -2210 | -3059 | 303 | 39 / 17 | -37 / +1 / -25 | 0.65 | CHECK (removes 48% of trades, > 40%) |
| 11:30-12:00 | -2.4 | -3.9 | -10129 | -2405 | -5129 | 144 | 14 / 6 | n/a / n/a / n/a | 0.64 | PASS |
| 10:30-11:00 | +1.2 | +1.5 | -10468 | -2405 | -5129 | 166 | 5 / 2 | n/a / n/a / n/a | 0.86 | NO-GAIN |
| 10:00-10:30 | +26.7 | +22.8 | -10533 | -2405 | -5129 | -88 | 14 / 6 | n/a / n/a / n/a | 0.43 | FAIL |
| 11:00-11:30 | +39.5 | +14.0 | -13490 | -2405 | -5730 | -127 | 15 / 7 | n/a / n/a / n/a | 0.43 | FAIL |

#### book M8 (pick ref: L6M ulcer 1689, maxDD -4331, worst day -2401, worst wk -2446, $/wk 752; L3M ulcer 1124)

| block ET | L6M ulcer % | L3M ulcer % | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | removed L6M / L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| 09:30-10:00 | -24.8 | -28.1 | -2562 | -1410 | -2318 | 204 | 58 / 30 | -23 / -55 / -66 | 0.71 | CHECK (removes 64% of trades, > 40%) |
| 10:30-11:00 | -7.8 | +0.0 | -3850 | -2401 | -2379 | 732 | 6 / 3 | n/a / n/a / n/a | 0.71 | NO-GAIN |
| 11:30-12:00 | -5.2 | -16.7 | -3826 | -2401 | -2446 | 811 | 6 / 3 | n/a / n/a / n/a | 0.86 | PASS |
| 10:00-10:30 | +2.7 | +16.9 | -4331 | -2401 | -2446 | 609 | 22 / 11 | n/a / n/a / n/a | 0.57 | FAIL |
| 11:00-11:30 | +5.8 | +3.2 | -4331 | -2401 | -2446 | 561 | 6 / 3 | n/a / n/a / n/a | 0.71 | NO-GAIN |

#### book M9 (pick ref: L6M ulcer 1628, maxDD -3929, worst day -2205, worst wk -2085, $/wk 205; L3M ulcer 1308)

| block ET | L6M ulcer % | L3M ulcer % | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | removed L6M / L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| 09:30-10:00 | -40.3 | -58.7 | -2205 | -2205 | -2205 | 161 | 21 / 8 | -53 / -29 / +14 | 0.50 | CHECK (removes 41% of trades, > 40%) |
| 10:00-10:30 | -33.3 | -17.2 | -2709 | -1595 | -1425 | 257 | 9 / 4 | n/a / n/a / n/a | 0.79 | PASS |
| 11:00-11:30 | +5.3 | +17.6 | -3929 | -2205 | -2085 | 128 | 8 / 1 | n/a / n/a / n/a | 0.64 | NO-GAIN |
| 11:30-12:00 | +13.6 | +22.5 | -4069 | -1595 | -1475 | 185 | 6 / 3 | n/a / n/a / n/a | 0.71 | NO-GAIN |
| 10:30-11:00 | +20.0 | -18.3 | -4644 | -2205 | -2085 | 128 | 14 / 7 | n/a / n/a / n/a | 0.57 | FAIL |

## BESIDE: new eight STKd8w42 with pick JT154

Reference rows (stack, all books): pick = TL3_SR_NY_STKd8w42_BF1_JT154; bare = TL3_SR_NY_STKd8w42_BF1_BASE (reference only).

| row | L6M ulcer | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | L3M ulcer | L3M maxDD | L3M worst day | L3M worst wk | L3M $/wk | 2023 ulcer | 2024 ulcer | 2025 ulcer | 2023 $/wk | 2024 $/wk | 2025 $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| pick | 14720 | -46473 | -18671 | -17735 | 19159 | 10716 | -32268 | -18671 | -17735 | 13631 | 54235 | 37886 | 25605 | -656 | 2236 | 5724 |
| bare | 27178 | -97355 | -81333 | -15764 | 51505 | 28739 | -97355 | -80574 | -9208 | 35029 | 47077 | 48345 | 58643 | 10045 | 7774 | 15973 |

### Whole mix (all books), blocks ranked by L6M ulcer (recent first: L6M with L3M beside, then 2023 / 2024 / 2025)

| block ET | L6M ulcer % | L3M ulcer % | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | L3M $/wk | trades removed L6M / L3M | 2023 / 2024 / 2025 ulcer % | 2023 / 2024 / 2025 $/wk | WF persist | random med % | p rand | p shift | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 11:00-11:30 | -16.9 | +6.2 | -46473 | -18671 | -20665 | 17550 | 14562 | 238 / 106 | n/a / n/a / n/a | n/a / n/a / n/a | 0.50 | -2.2 | 0.25 | 0.45 | FAIL |
| 11:30-12:00 | -9.3 | +0.2 | -46473 | -18671 | -19992 | 18902 | 12792 | 211 / 91 | n/a / n/a / n/a | n/a / n/a / n/a | 0.50 | -2.8 | 0.25 | 0.20 | FAIL |
| 10:30-11:00 | +10.8 | -5.4 | -49979 | -18671 | -23435 | 16681 | 10603 | 339 / 131 | n/a / n/a / n/a | n/a / n/a / n/a | 0.43 | +9.5 | 0.60 | 0.65 | FAIL |
| 10:00-10:30 | +28.1 | +5.2 | -56285 | -18671 | -35780 | 14904 | 10492 | 497 / 168 | n/a / n/a / n/a | n/a / n/a / n/a | 0.36 | +1.1 | 1.00 | 0.90 | FAIL |
| 09:30-10:00 | +79.1 | +35.0 | -73361 | -16064 | -23294 | 7220 | 9317 | 953 / 256 | n/a / n/a / n/a | n/a / n/a / n/a | 0.36 | -13.3 | 1.00 | 1.00 | FAIL |

Pick reference (all books): L6M ulcer 14720, maxDD -46473, worst day -18671, worst wk -17735, $/wk 19159; L3M ulcer 10716, $/wk 13631.

Null (best-of-5 blocks, date-shift of the signal clock, 20 draws): real best L6M ulcer change -16.9%, null best median -20.3%; real beats 2 of the first 5 draws (needs 4) -> FAIL; beats 4 of 20 draws (p of null doing as well = 0.800).

Best block (whole mix, not CHECK): 11:00-11:30, L6M ulcer -16.9% (L3M +6.2%), verdict FAIL (walk-forward persistence 0.50 < 0.58); equal-risk view: $/wk x (pick ulcer / block ulcer) = 21122 vs pick 19159; random removal of the same 238 trades gives median -2.2% (p rand 0.25).

### Per book

#### book M1 (pick ref: L6M ulcer 15682, maxDD -39757, worst day -15046, worst wk -16741, $/wk 4969; L3M ulcer 15192)

| block ET | L6M ulcer % | L3M ulcer % | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | removed L6M / L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| 11:00-11:30 | -12.9 | -21.4 | -36265 | -15099 | -13611 | 4538 | 14 / 5 | n/a / n/a / n/a | 0.57 | FAIL |
| 11:30-12:00 | +0.4 | +2.9 | -39757 | -14682 | -15981 | 4970 | 18 / 9 | n/a / n/a / n/a | 0.86 | NO-GAIN |
| 10:30-11:00 | +8.1 | +15.1 | -34638 | -18097 | -16741 | 3293 | 24 / 10 | n/a / n/a / n/a | 0.36 | FAIL |
| 10:00-10:30 | +9.0 | +2.3 | -52148 | -24507 | -30806 | 4985 | 25 / 5 | n/a / n/a / n/a | 0.57 | FAIL |
| 09:30-10:00 | +124.4 | +17.7 | -67987 | -29768 | -24459 | -1654 | 92 / 36 | n/a / n/a / n/a | 0.50 | FAIL |

#### book M2 (pick ref: L6M ulcer 6647, maxDD -19714, worst day -7241, worst wk -15846, $/wk 2909; L3M ulcer 6016)

| block ET | L6M ulcer % | L3M ulcer % | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | removed L6M / L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| 11:30-12:00 | -9.0 | +9.5 | -18277 | -8139 | -12102 | 2818 | 20 / 8 | n/a / n/a / n/a | 0.64 | NO-GAIN |
| 10:00-10:30 | -7.4 | -15.7 | -17081 | -7194 | -13202 | 2586 | 68 / 30 | n/a / n/a / n/a | 0.64 | PASS |
| 11:00-11:30 | +1.1 | +17.1 | -15564 | -7194 | -13501 | 2396 | 24 / 13 | n/a / n/a / n/a | 0.43 | FAIL |
| 09:30-10:00 | +27.3 | -8.1 | -25170 | -10639 | -14626 | 757 | 148 / 68 | n/a / n/a / n/a | 0.64 | CHECK (removes 43% of trades, > 40%) |
| 10:30-11:00 | +39.0 | +21.8 | -24148 | -9877 | -20279 | 2542 | 48 / 25 | n/a / n/a / n/a | 0.43 | FAIL |

#### book M3 (pick ref: L6M ulcer 16372, maxDD -40464, worst day -9489, worst wk -27388, $/wk 2355; L3M ulcer 6208)

| block ET | L6M ulcer % | L3M ulcer % | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | removed L6M / L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| 09:30-10:00 | -40.3 | +39.7 | -22645 | -6179 | -9934 | 158 | 134 / 59 | n/a / n/a / n/a | 0.71 | CHECK (removes 62% of trades, > 40%) |
| 10:00-10:30 | -6.2 | +2.1 | -41327 | -9489 | -27388 | 2464 | 24 / 10 | n/a / n/a / n/a | 0.57 | FAIL |
| 11:30-12:00 | +0.8 | -0.7 | -40464 | -9489 | -27388 | 2754 | 10 / 3 | n/a / n/a / n/a | 0.86 | NO-GAIN |
| 11:00-11:30 | +3.3 | -0.9 | -41410 | -9489 | -28333 | 1969 | 8 / 3 | n/a / n/a / n/a | 0.64 | NO-GAIN |
| 10:30-11:00 | +17.0 | -0.0 | -45629 | -9489 | -27388 | 1958 | 9 / 1 | n/a / n/a / n/a | 0.71 | NO-GAIN |

#### book M4 (pick ref: L6M ulcer 8870, maxDD -25664, worst day -9854, worst wk -20308, $/wk 4340; L3M ulcer 9406)

| block ET | L6M ulcer % | L3M ulcer % | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | removed L6M / L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| 10:00-10:30 | -11.9 | -10.2 | -21738 | -11139 | -10024 | 3047 | 199 / 56 | n/a / n/a / n/a | 0.50 | FAIL |
| 10:30-11:00 | -1.9 | +1.1 | -24571 | -9854 | -19215 | 4126 | 136 / 37 | n/a / n/a / n/a | 0.71 | NO-GAIN |
| 11:30-12:00 | +6.8 | -8.3 | -25652 | -9202 | -20295 | 4090 | 45 / 18 | n/a / n/a / n/a | 0.50 | FAIL |
| 11:00-11:30 | +6.8 | -14.4 | -21922 | -9202 | -16566 | 4156 | 80 / 30 | n/a / n/a / n/a | 0.64 | NO-GAIN |
| 09:30-10:00 | +89.5 | -76.4 | -36771 | -10235 | -17968 | 1902 | 415 / 125 | n/a / n/a / n/a | 0.57 | CHECK (removes 44% of trades, > 40%) |

#### book M5 (pick ref: L6M ulcer 10683, maxDD -20994, worst day -5813, worst wk -9962, $/wk 334; L3M ulcer 7948)

| block ET | L6M ulcer % | L3M ulcer % | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | removed L6M / L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| 10:30-11:00 | -55.6 | -50.3 | -11817 | -6769 | -10663 | 280 | 68 / 30 | n/a / n/a / n/a | 0.43 | FAIL |
| 09:30-10:00 | -33.3 | +0.3 | -18946 | -4879 | -10212 | 566 | 113 / 44 | n/a / n/a / n/a | 0.57 | FAIL |
| 11:30-12:00 | -4.5 | +4.7 | -18703 | -4064 | -5279 | 231 | 51 / 24 | n/a / n/a / n/a | 0.50 | FAIL |
| 11:00-11:30 | -4.1 | +1.3 | -17873 | -5813 | -9493 | 311 | 48 / 24 | n/a / n/a / n/a | 0.64 | NO-GAIN |
| 10:00-10:30 | +28.6 | +38.9 | -26039 | -5304 | -9574 | 7 | 78 / 32 | n/a / n/a / n/a | 0.64 | NO-GAIN |

#### book M6 (pick ref: L6M ulcer 12316, maxDD -33121, worst day -9514, worst wk -9149, $/wk 2850; L3M ulcer 2511)

| block ET | L6M ulcer % | L3M ulcer % | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | removed L6M / L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| 09:30-10:00 | -54.2 | -21.8 | -17267 | -7079 | -10098 | 2118 | 191 / 84 | n/a / n/a / n/a | 0.71 | CHECK (removes 47% of trades, > 40%) |
| 10:00-10:30 | -15.3 | +26.2 | -31514 | -9514 | -8836 | 1638 | 81 / 32 | n/a / n/a / n/a | 0.50 | FAIL |
| 10:30-11:00 | -11.9 | +8.0 | -34038 | -9514 | -8686 | 2632 | 47 / 18 | n/a / n/a / n/a | 0.50 | FAIL |
| 11:00-11:30 | -4.2 | +13.6 | -32488 | -9514 | -9689 | 2987 | 28 / 15 | n/a / n/a / n/a | 0.50 | FAIL |
| 11:30-12:00 | +32.2 | +12.4 | -41533 | -9514 | -11226 | 2592 | 39 / 17 | n/a / n/a / n/a | 0.43 | FAIL |

#### book M7 (pick ref: L6M ulcer 2547, maxDD -6038, worst day -2415, worst wk -2570, $/wk 458; L3M ulcer 1937)

| block ET | L6M ulcer % | L3M ulcer % | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | removed L6M / L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| 10:00-10:30 | -7.1 | +50.5 | -5623 | -2415 | -2570 | 278 | 17 / 8 | n/a / n/a / n/a | 0.43 | FAIL |
| 11:00-11:30 | -0.6 | +28.4 | -5993 | -2415 | -2469 | 238 | 23 / 11 | n/a / n/a / n/a | 0.43 | FAIL |
| 09:30-10:00 | +6.2 | -81.4 | -7283 | -2360 | -3144 | 401 | 45 / 19 | n/a / n/a / n/a | 0.64 | NO-GAIN |
| 11:30-12:00 | +7.1 | +8.8 | -6568 | -2415 | -2570 | 493 | 17 / 9 | n/a / n/a / n/a | 0.57 | FAIL |
| 10:30-11:00 | +24.4 | +24.6 | -6918 | -2415 | -2570 | 341 | 12 / 5 | n/a / n/a / n/a | 0.57 | FAIL |

#### book M8 (pick ref: L6M ulcer 4350, maxDD -10238, worst day -6138, worst wk -8916, $/wk 1259; L3M ulcer 3034)

| block ET | L6M ulcer % | L3M ulcer % | L6M maxDD | L6M worst day | L6M worst wk | L6M $/wk | removed L6M / L3M | 2023 / 2024 / 2025 ulcer % | WF persist | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| 11:30-12:00 | -9.2 | +0.8 | -9741 | -6138 | -8916 | 1261 | 11 / 3 | n/a / n/a / n/a | 0.86 | NO-GAIN |
| 11:00-11:30 | -3.9 | +4.2 | -9741 | -6138 | -8916 | 885 | 16 / 5 | n/a / n/a / n/a | 0.36 | FAIL |
| 09:30-10:00 | +0.1 | -22.8 | -11673 | -4624 | -6130 | 942 | 131 / 64 | n/a / n/a / n/a | 0.64 | CHECK (removes 50% of trades, > 40%) |
| 10:30-11:00 | +2.5 | +5.4 | -9741 | -6138 | -8916 | 1252 | 27 / 8 | n/a / n/a / n/a | 0.79 | NO-GAIN |
| 10:00-10:30 | +49.9 | +38.6 | -13439 | -6375 | -10780 | 1053 | 48 / 18 | n/a / n/a / n/a | 0.64 | NO-GAIN |
