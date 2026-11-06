# DS3_REPLICATION - high-precision nulls for the WATCH items (S4a, 2026-11-06); new, append-only
Research only, Shadow only, no PASS claim, no purchase. Prereg l2vast/ds3/prereg/REPLICATION_prereg.md sha256 c1fa2d7a6426f13977e5861a8a245cb63fe54242b1fcca72b5cc136c399841d4 (DECISIONS.md, filed before any fresh-world statistic). p = (1 + k)/(N + 1), k = number of fresh worlds at or beyond the real value; the 95% interval is the Clopper-Pearson interval of k/N mapped to p. Items not recomputed (cited as is): CHAR-A's 2,000-draw Monday table (replaced here by 20,000 draws), S4b's 600-world crypto-cluster test (conditional on the selected region, DS3_INSTR2_BTC.md section 5), ALLINST 200-world joint null.

## Status table (filled as items finish; R1/R2 are the long runs)
| item | old p | new p (CI) | label change |
|--|--|--|--|
| R1 GC count excess 493 of 4,200 | .0099 (100 worlds per kind) | see R1 block (running) | pending |
| R2 BTCM clear-cell count 119 | .01 (100 random-side worlds) | see R2 block (running) | pending |
| R3 equity Monday, joint equity family minimum (RTY Monday) | .15 (2,000 draws) | 0.141 [0.137, 0.146] (20,000 draws) | none: stays best-of-F / WATCH-REGIME |
| R4 FIND_DAILY 36 tolerant cells | min family p .33 random-side / .48 shift (200 worlds) | min 0.593 / 0.240 (1,000 worlds); none <= .10 on either | none: LEAD 0 |
| R5 6E TSMOM-252 vol | shift .005 vs random-side 1.00 | shift .005 (1,000 worlds) vs random-side 1.00; the shift null is the contaminated one | none: NULL |

## R3 equity Monday: 20,000 fresh weekday-permutation draws (CHAR-A statistic: Monday excess over the other days of the same ISO week, full-day bps, permutation paired by week, code monday.py; new seeds)
Families: JOINT equity (ES NQ RTY YM x 5 weekdays = 20 cells, the same random keys for the four indices), ALL 65 cells (13 instruments x 5 weekdays; the nine controls with independent draws), and EQ4 (equal-notional average, 5 cells).
| index | Monday excess bps | z | raw p [95% CI] (old) | family p: joint equity 20 (old) | family p, all 65 cells |
|--|--|--|--|--|--|
| ES | +8.1 | +1.84 | 0.0654 [0.0621, 0.0690] (old 0.075) | 0.508 (old 0.52) | 0.971 |
| NQ | +12.2 | +2.17 | 0.0296 [0.0273, 0.0320] (old 0.034) | 0.281 (old 0.29) | 0.800 |
| RTY | +19.4 | +2.48 | 0.0140 [0.0125, 0.0158] (old 0.013) | 0.141 (old 0.15) | 0.506 |
| YM | +7.2 | +1.69 | 0.0912 [0.0872, 0.0953] (old 0.103) | 0.617 (old 0.63) | 0.992 |
| EQ4 | +9.8 | +2.09 | 0.0359 [0.0334, 0.0386] (old 0.038) | 0.159 (5-cell, old .17) | 0.860 |
Control instruments (45 cells): minimum all-65 family p 0.505; the largest raw hits are ZB Monday -7.0 bps (p .013), CL Monday -26 bps (.021), BTC Thursday -53 bps (.026), MBT Monday +59 bps (.035): controls reach the same raw |z| 2.1-2.5 as the equity indices. Pre/post-2023 break (weekly Monday excess, era split at 2023-04-01 and sup-|t| scan over break dates 2016..2025, 20,000 label permutations each):
| series | pre-2023 mean bps | 2023+ mean bps | Delta [95% CI] | split-2023 permutation p (old) | sup-t scan p (old) |
|--|--|--|--|--|--|
| ES | +2.7 | +21.9 | +19.2 [+2.9, +35.3] | 0.042 (old 0.051) | 0.0086 (old 0.009) |
| NQ | +5.8 | +28.4 | +22.6 [+0.8, +43.9] | 0.054 (old 0.064) | 0.0055 (old 0.005) |
| RTY | +16.4 | +23.2 | +6.9 [-21.6, +35.3] | 0.649 (old 0.648) | 0.8382 (old 0.849) |
| YM | +4.0 | +15.6 | +11.6 [-4.2, +27.0] | 0.213 (old 0.216) | 0.0213 (old 0.023) |
| EQ4 | +4.9 | +22.3 | +17.4 [+0.4, +34.6] | 0.083 (old 0.077) | 0.0050 (old 0.003) |
**Plain sentence: with 20,000 draws the Monday excess has the same size as CHAR-A's 2,000-draw estimate and the same verdict: the raw p of each index moves by less than .01, but once the five weekdays and four indices are searched together the best equity cell (RTY Monday) has family p 0.141 [0.137, 0.146] (> .10; old .15), and across all 65 cells no cell is below 0.51. The break is real in the weekly series (sup-t p .005-.021 for ES, NQ, YM and EQ4; split-2023 p .042-.213; RTY already +16 bps before 2023, p .65), so Monday is a 2023+ level shift in the equity indices that is not distinguishable from a best-of-family draw: label unchanged, best-of-F, WATCH / REGIME (WATCH_MONDAY_LONG_SPEC.md stays a forward Shadow watch only).**

## R4 FIND_DAILY: the 36 tolerant cells at 1,000 fresh worlds per null (world ids 1000-1999; old 200)
Data: the corrected daily build (roll-day H/L fix of 2026-11-06, DS3_FIND_DAILY.md reconciliation block; the fix moved 10 Donchian totals and no label). Family nulls: random-side maximum z median 2.73, p95 3.46; forward-shift median 2.71, p95 3.40 (old: 2.69/3.41 and 2.66/3.45).
Tolerant cells (family p of the 36; interval from the 1,000 worlds):
| cell | z random-side | p old -> new [CI] | z shift | p old -> new [CI] |
|--|--|--|--|--|
| ES MR_k5_th1.5 | 2.65 | 0.333 -> 0.593 [0.562, 0.624] | 2.30 | 0.871 -> 0.885 [0.864, 0.904] |
| RTY NIGHT_L | 2.55 | 0.473 -> 0.717 [0.688, 0.745] | n/a | 1.000 -> 1.000 [0.996, 1.000] |
| YM NIGHT_L | 2.16 | 0.955 -> 0.985 [0.975, 0.992] | n/a | 1.000 -> 1.000 [0.996, 1.000] |
| ES MR_k3_th1.5 | 2.09 | 0.985 -> 0.993 [0.986, 0.997] | 2.03 | 0.975 -> 0.985 [0.975, 0.992] |
| ES MR_k5_th1 | 2.06 | 0.990 -> 0.997 [0.991, 0.999] | 1.69 | 0.990 -> 0.998 [0.993, 1.000] |
| PORT MA_10_50 | 1.94 | 1.000 -> 1.000 [0.996, 1.000] | 0.94 | 1.000 -> 1.000 [0.996, 1.000] |
| PORT DON_N100_SAR | 1.84 | 1.000 -> 1.000 [0.996, 1.000] | 2.62 | 0.582 -> 0.604 [0.573, 0.635] |
| GC NIGHT_L | 1.79 | 1.000 -> 1.000 [0.996, 1.000] | n/a | 1.000 -> 1.000 [0.996, 1.000] |
| CL DON_N20_SAR | 1.68 | 1.000 -> 1.000 [0.996, 1.000] | 1.73 | 0.990 -> 0.998 [0.993, 1.000] |
| RTY WKND_L | 1.62 | 1.000 -> 1.000 [0.996, 1.000] | 0.81 | 1.000 -> 1.000 [0.996, 1.000] |
| GC MA_10_50 | 1.27 | 1.000 -> 1.000 [0.996, 1.000] | 1.34 | 1.000 -> 1.000 [0.996, 1.000] |
| MBT TSMOM_L126_vol | 1.24 | 1.000 -> 1.000 [0.996, 1.000] | 2.88 | 0.701 -> 0.352 [0.322, 0.382] |
| MBT TSMOM_L126_1lot | 1.22 | 1.000 -> 1.000 [0.996, 1.000] | 3.00 | 0.483 -> 0.240 [0.214, 0.267] |
| 6E TSMOM_L126_vol | 1.22 | 1.000 -> 1.000 [0.996, 1.000] | 2.12 | 0.945 -> 0.966 [0.953, 0.976] |
| PORT TSMOM_L126_vol | 1.19 | 1.000 -> 1.000 [0.996, 1.000] | 1.08 | 1.000 -> 1.000 [0.996, 1.000] |
| PORT TSMOM_L63_vol | 1.13 | 1.000 -> 1.000 [0.996, 1.000] | -0.01 | 1.000 -> 1.000 [0.996, 1.000] |
| 6E TSMOM_L126_1lot | 1.03 | 1.000 -> 1.000 [0.996, 1.000] | 1.88 | 0.990 -> 0.998 [0.993, 1.000] |
| GC TSMOM_L126_vol | 0.94 | 1.000 -> 1.000 [0.996, 1.000] | 1.95 | 0.990 -> 0.993 [0.986, 0.997] |
| CL DON_N40_SAR | 0.93 | 1.000 -> 1.000 [0.996, 1.000] | 1.27 | 1.000 -> 1.000 [0.996, 1.000] |
| PORT MA_20_100 | 0.90 | 1.000 -> 1.000 [0.996, 1.000] | -0.49 | 1.000 -> 1.000 [0.996, 1.000] |
| CL TSMOM_L252_1lot | 0.84 | 1.000 -> 1.000 [0.996, 1.000] | 1.53 | 1.000 -> 1.000 [0.996, 1.000] |
| CL TSMOM_L252_vol | 0.82 | 1.000 -> 1.000 [0.996, 1.000] | 1.27 | 1.000 -> 1.000 [0.996, 1.000] |
| 6E DON_N100_SAR | 0.82 | 1.000 -> 1.000 [0.996, 1.000] | 2.01 | 0.945 -> 0.986 [0.977, 0.992] |
| PORT TSMOM_L252_1lot | 0.79 | 1.000 -> 1.000 [0.996, 1.000] | -0.64 | 1.000 -> 1.000 [0.996, 1.000] |
| GC DON_N20_SAR | 0.78 | 1.000 -> 1.000 [0.996, 1.000] | 0.87 | 1.000 -> 1.000 [0.996, 1.000] |
| MBT MR_k1_th1.5 | 0.74 | 1.000 -> 1.000 [0.996, 1.000] | 0.81 | 1.000 -> 1.000 [0.996, 1.000] |
| CL DON_N60_EX | 0.71 | 1.000 -> 1.000 [0.996, 1.000] | 1.76 | 1.000 -> 0.998 [0.993, 1.000] |
| RTY DON_N60_SAR | 0.69 | 1.000 -> 1.000 [0.996, 1.000] | 1.78 | 0.995 -> 0.998 [0.993, 1.000] |
| NKD DON_N100_SAR | 0.66 | 1.000 -> 1.000 [0.996, 1.000] | 0.95 | 1.000 -> 1.000 [0.996, 1.000] |
| MBT TSMOM_L252_1lot | 0.65 | 1.000 -> 1.000 [0.996, 1.000] | 1.61 | 1.000 -> 0.999 [0.994, 1.000] |
| MBT TSMOM_L252_vol | 0.64 | 1.000 -> 1.000 [0.996, 1.000] | 1.37 | 1.000 -> 1.000 [0.996, 1.000] |
| MBT DON_N100_SAR | 0.51 | 1.000 -> 1.000 [0.996, 1.000] | 0.68 | 1.000 -> 1.000 [0.996, 1.000] |
| NKD MA_50_200 | 0.46 | 1.000 -> 1.000 [0.996, 1.000] | 0.60 | 1.000 -> 1.000 [0.996, 1.000] |
| GC DON_N40_SAR | 0.44 | 1.000 -> 1.000 [0.996, 1.000] | 0.05 | 1.000 -> 1.000 [0.996, 1.000] |
| MBT DON_N40_EX | 0.39 | 1.000 -> 1.000 [0.996, 1.000] | 1.00 | 1.000 -> 1.000 [0.996, 1.000] |
| MBT DON_N20_EX | 0.38 | 1.000 -> 1.000 [0.996, 1.000] | 0.55 | 1.000 -> 1.000 [0.996, 1.000] |
**Plain sentence: with 1,000 worlds per null no tolerant daily cell comes near the .10 bar: the smallest family p is 0.593 for the random-side null (ES 5-day reversal, which was .33 with 200 worlds - the 200-world value was optimistic) and 0.240 for the forward-shift null (MBT 126-day momentum, only 4.8 years of data), no cell is <= .10 on both nulls, and the CL Donchian-20 stop-and-reverse cell (watch-listed, spec filed) has 1.000 / 0.998: best-of-F with certainty. Labels unchanged (LEAD 0). The only cell of all 408 with a shift-null p below .10 is 6E TSMOM-252 (vol lots), p 0.005 [0.002, 0.011], which is not tolerant (R5).**

## R5 6E TSMOM-252 (vol lots): why the shift null says p .005 and the random-side null says 1.00
Cell: 13-year net $77,367 at 86 sign episodes, long share 39%. Random-side null (1,000 worlds): total mean $-24,358, sd $85,428, so z = 1.19; forward-shift null (1,000 worlds, shifts of 21-252 days): mean $-103,076, sd $44,465, so z = 4.06. Daily 6E return autocorrelation at lags 1/5/21/63 days: -0.004, +0.018, -0.006, +0.001; correlation of the real position path with the shifted paths: 0.15.
Why they disagree: the shifted paths are not neutral. A 252-day momentum sign displaced forward by 21-252 days is a stale signal (trailing-return window ending s days ago, i.e. 12-month momentum skipping 1-12 months), and in 6E that stale signal LOSES (mean $-103,076, much worse than the random-side mean $-24,358): the shift null has a built-in negative drift because 6E mean-reverts at the 1-3 year horizon, and it is also narrower (sd $44,465 vs $85,428). Beating it says 'current-window momentum beats stale momentum', not 'momentum beats random direction'.
Calibration (each test applied to paths generated under the other null, 150 paths each): the SHIFT test applied to random-side world paths rejects at z > 1.645 in 0.113 of cases (nominal .05; mean z -0.91, sd 2.01: over-dispersed, not calibrated); the RANDOM-SIDE test applied to shifted world paths rejects in 0.000 (mean z -1.66: conservative against paths that carry a stale-signal loss).
**Plain sentence: for a slow trend cell the random-side (episode sign) null is the right one - it asks whether the direction is informative given the timing and episode lengths - and the shift null is not (it carries the instrument's own long-horizon reversal and is over-dispersed on calibration), so the p .005 is an artefact of comparing with a losing stale signal and the cell stays NULL (random-side z 1.19, family p 1.00; not tolerant: positive in 7 of 14 years).**
Correction (appended): in the R3 plain sentence 'moves by less than .01' should read 'by at most .012' (YM raw p .103 -> .091); no conclusion changes.
