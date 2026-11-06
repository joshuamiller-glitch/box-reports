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

## R2 BTCM count test: STOPPED by order of the lead (2026-11-06); handed to S4b's fee-adjusted null (prereg T2_BTCM_NULL_FEE_PREREG.md)
Correction of my interim statement: the 119 clear / 1,358 tolerant counts that my fast re-implementation of the S4b gate reproduced are the FEE-LESS counts (the post-patch engine, t2_lib.sim_one with the fee-points argument, was used with T2_FEEPTS at its default 0, i.e. the original fee-less grid; my note 'the current engine includes the fee fix' was wrong for that run). S4b's fee-adjusted counts are 62 (tolerant + persistence) and 540 tolerant, and the old p .01 (100 random-side worlds) also belongs to the fee-less 119. No fresh-world result of mine for BTCM exists (the worlds had not completed when the run was stopped); the fee-adjusted BTCM family null is S4b's. Nothing in this page presents 119 as a fee-adjusted count; the R2 row of the status table reads: old p .01 (fee-less, 119) -> new fee-adjusted test owned by S4b, pending; label: WATCH of the BTCM cluster stays as S4b set it.
Correction (appended): one fee-LESS shifted-trigger world did complete before the stop (tolerant 2,106, clear 14, max t_min 2.87; file /mnt/l2/l2vast/ds3_t2/BTCM_rep_0.pkl); it is one world, not a test, and it is fee-less, so it is not used.

## R1 GC count excess: 1,000 fresh worlds per kind (seeds 1000-1999; family.py unchanged: 448 signal sets x 5 sessions x {ATR3, $1,200} x R1.5 x T60, 4,200 cells with >= 100 trades; same tolerant gate; 12,200 s on 4 workers)
Real values (unchanged): 493 of 4,200 cells pass the tolerant gate; max HOLD mean $1,407 a week; max L6M Calmar 0.654.
| statistic | null | old p (100 worlds) | new p (1,000 worlds) [95% CI] | null median / p95 / max |
|--|--|--|--|--|
| gate-passer count, random side | 493 | 0.0099 | **0.0010 [0.0010, 0.0047]** (0 of 1,000 worlds reach 493) | 252 / 281 / 323 |
| gate-passer count, shifted trigger (1-5 label days) | 493 | 0.0099 | **0.0010 [0.0010, 0.0047]** (0 of 1,000 reach 493) | 393 / 425 / 453 |
| max HOLD mean $/wk, random side | 1,407 | 0.861 | 0.845 [0.821, 0.867] | median 1,644, p95 2,214 |
| max HOLD mean $/wk, shifted | 1,407 | 0.584 | 0.621 [0.591, 0.652] | median 1,484, p95 2,114 |
| max L6M Calmar, random side / shifted | 0.654 | 0.713 / 0.990 | 0.704 [0.675, 0.732] / 0.989 [0.980, 0.995] | - |
**Plain sentence: the GC count excess is real and now pinned down: none of 2,000 fresh worlds reaches the 493 tolerant cells (random-side maximum 323, shifted-trigger maximum 453, so the shifted null is the closer one: 493 is 40 above its largest of 1,000 worlds), p = 0.001 on both nulls with an upper 95% bound of 0.005; the single-cell statistics stay well inside the nulls (max HOLD p .85 / .62, max L6M Calmar p .70 / .99), so there is still no GC cell better than the best of a random family. Label unchanged: GC = REGIME (a real 2026 trend-regime count excess, negative in 2013-2023 for all 40 finalists), not a book.**

## Final status table (supersedes the interim one above)
| item | old p | new p (95% CI) | label change |
|--|--|--|--|
| R1 GC count excess 493 / 4,200 | .0099 / .0099 | .0010 / .0010 [.0010, .0047] (1,000 worlds per kind) | none: REGIME |
| R2 BTCM count (119 fee-less; fee-adjusted 62 / 540) | .01 (fee-less, 100 random-side worlds) | not run by S4a (stopped on the lead's order); fee-adjusted null owned by S4b | none from this page |
| R3 equity Monday joint family (RTY Monday) | .15 | .141 [.137, .146] (20,000 draws); all-65-cell family .506 | none: best-of-F, WATCH/REGIME |
| R4 FIND_DAILY 36 tolerant cells | .33 / .48 | .593 / .240 (1,000 worlds per null) | none: LEAD 0 |
| R5 6E TSMOM-252 | shift .005 / random-side 1.00 | shift .005 [.002, .012] / random-side 1.00 (1,000 worlds); the shift null is the contaminated one | none: NULL |
Correction (appended): R5 shift-null p for 6E TSMOM-252 is .0050 with 95% CI [.0021, .0112] (the final table row shows [.002, .012]).

## REPL-TICK (ZL-2, 2026-11-06; prereg l2vast/ds3/prereg/REPL_TICK_prereg.md sha256 f034c2249d55c7f0bee4118e413e458725014b2bdb2bc98f94d7e269369bd54f, logged before any fresh-world statistic)
Replication of four already-seen best-of-F tick-scale survivors at 2,000 fresh worlds, new seeds, two extra null types. Nothing live, no PASS claim. Real statistics tied out to the owners' stored values first (ES/RTY family: max |net difference| 6e-6 / 1.3e-5 ticks over 149 / 147 scored cells; EVENTS-1S t statistics identical; burst book at 100 worlds seed 1 gives p_book .08-.56 like the stored .08-.56). Nulls: N1 = the original (forward same-day shifts 120-1800 s for the passive items; control non-event days for (c); shift5 for (d)); N2 = random side / random sign at the same clock; N3 = same clock on another day of the same month (for (d): 'mdays', entry moved to a random day of the same month, plus the original 'side' and 'days'). p = (1+k)/(W+1), W = 2,000, Clopper-Pearson 95% CI on k/W. 'p_family' = Westfall-Young max-z over all scored cells (ES 149, RTY 147, EVENTS-1S RTY 1,152). Label rule fixed beforehand: KEEPS best-of-F label only if p <= .10 under all three nulls; DOWNGRADED to 'selection artefact' if p > .10 under N1; mixed = 'null-dependent, not confirmed'. Base: tick data, percent of nothing; cost = measured spread/fee model of each owner.
| item | old p | N1 p (CI) | N2 p (CI) | N3 p (CI) | label |
|--|--|--|--|--|--|
| (a) ES IB nypm all h300 passive, 257 orders, net +2.909 ticks/placed | cell .005, family .005 | cell .0005, family .0115 (.0074-.0171) | cell .037 (.030-.047), family .990 | cell .004 (.002-.008), family .346 | NULL-DEPENDENT, NOT CONFIRMED (cell-level passes all three; family-level only under N1) |
| (b) RTY PD pre all h30 passive, 98 orders, +3.827 | family .005 | family .0005 (.0005-.0023) | cell .051 (.042-.062), family .989 | cell .0005, family .0025 (.001-.0056) | NULL-DEPENDENT, NOT CONFIRMED |
| (b) RTY PD pre all h60, +6.460 | family .005 | family .0005 | cell .030 (.023-.038), family .965 | cell .0005, family .0005 | NULL-DEPENDENT, NOT CONFIRMED |
| (b) RTY PD pre all h5 (+1.242) / h300 (+5.828) | family .005 / .109 | .0005 / .114 (.101-.129) | cell .067 / .224; family .999 / 1.0 | family .0045 / .354 | h5 null-dependent; h300 stays NOT significant (as before) |
| (c) RTY FOMC shock D30 h120 cont, 18 events | family .044 | family .0435 (.035-.053) | family .183 (.166-.201) | family .0995 (.087-.113) | NULL-DEPENDENT, NOT CONFIRMED (cell p <= .003 under all) |
| (c) RTY CPI shock D30 h30 cont, 30 events | family .098 | family .0905 (.078-.104) | family .300 (.280-.320) | family .186 (.169-.204) | NULL-DEPENDENT, NOT CONFIRMED |
| (d) ES PD burst h60 taker, six 1S-FIX cells m1.0_tNone / m1.0_t1.0 / m1.5_tNone / m1.5_t1.0 / m2.0_tNone / m2.0_t1.0 | p_book .08-.56 | p_book (max over HOLD, L6M, stack gain, per kind shift5) all kinds: .118 / .050 / .195 / .244 / .323 / .547 | (max over shift5, side, days, mdays) | | only m1.0_t1.0 has p_book <= .10 (.050); other five DOWNGRADED (p > .10); joint WY over the 6 cells (HOLD mean, per kind, weakest) .10 / .11 / .17 / .47 / .15 / .27; L6M joint .25-.89 |
Reading. (1) The passive RTY pre-market and ES IB-edge results survive the ORIGINAL null (N1) and the same-month-day null at cell level, but the family-wise max-statistic p collapses under the random-side null (N2: .96-1.0): with a random side at the same clock the family contains cells whose chance maximum is as large, so these are not distinguishable from selected-cell noise at family level; the cell-level N2 p stays .03-.07. This is the null-dependence the rule labels. (2) The two EVENTS-1S RTY cells replicate N1 almost exactly (.0435 vs .044, .0905 vs .098) and weaken under N2 and N3 (FOMC .0995 under N3 sits at the threshold). (3) The ES burst book: the 2023-25 years are negative for every cell (m1.0_t1.0 yearly net at equal-risk lots -$27.6k, -$34.3k, -$22.4k, then +$0.8k in 2026), so the placebo p of the best cell does not turn it into a profitable book; 5 of 6 cells fail p <= .10.
Per-year (net per placed order, ticks; placed orders): (a) ES IB h300: 2025 +1.54 (99), 2026 +3.77 (158); quarters 2025Q3 +0.14, Q4 +3.14, 2026Q1 +9.24, Q2 +7.33, Q3 -1.89, Q4 -3.92. (b) RTY PD pre h30: 2025 +2.78 (34), 2026 +4.38 (64); quarters 2025Q3 +0.91, Q4 +4.90, 2026Q1 +11.65, Q2 -0.98, Q3 -0.48, Q4 +9.47; h60: 2025 +4.17, 2026 +7.68 (Q2 -2.65, Q3 -0.31). Both passive samples cover only 2025-09 to 2026-10 (data limit of the quote tape), three of the last four ES quarters and two of the last three RTY quarters are flat/negative. (c) FOMC shock events (18) 2023 2, 2024 7, 2025 6, 2026 3 (mean net ticks +64.5, +47.5, -1.0, +94.4); CPI shock events (30) 2023 2, 2024 8, 2025 11, 2026 9 (+1.5, +58.0, +16.8, +12.6). (d) 414 trades: 2023 51, 2024 133, 2025 118, 2026 112.
Tape-confirmed share (fills with a print through the level, or print volume at the level >= the queue ahead): ES IB h300 17.7% of 254 fills (through-print 1.2%); RTY PD pre h30 60.3% of 63 fills (through 25.4%), h60 59.4% of 64, h5 67.3% of 55, h300 57.4% of 68. The ES result therefore rests mostly on fills the tape cannot confirm; the RTY result is about 60% confirmed. (c) and (d) are market-order books, share not applicable.
Label changes: none upgraded; (a), (b), (c) -> 'null-dependent, not confirmed' (still best-of-F, no PASS); (d) five of six cells -> 'selection artefact' (p_book > .10 under the original placebos), m1.0_t1.0 stays weak (p .050, loses money 2023-25).
Files: code l2vast/ds3/code/repl_tick/{repl_family.py, repl_an_family.py, repl_ev.py, repl_burst.py}; outputs /mnt/l2/l2vast/repl_tick/{ES,RTY}_family_W2000.pkl, {ES,RTY}_an_W2000.pkl, RTY_ev_W2000.pkl, ES_burst_W2000_S20261111.pkl. Seeds 20261107-20261111 as in the prereg. Caveat: random-side family p near 1 reflects the many correlated cells of the max-statistic under that null; read the cell-level N2 p as well.


## Fee-adjusted fresh-world family null, BTCM full grid (S4b, 2026-11-06 07:17Z)
Prereg addendum autopilot/T2_BTCM_NULL_FEE_PREREG.md (sha256 e04082d8dab35e4dd4dc1258e85a71d58b7c463853940acc24b4fefc3728da72, before any fee-adjusted null world); code l2vast/ds3/code/t2/t2_null2.py; per-world vectors /mnt/l2/l2vast/ds3_t2/BTCM_fee_null2.pkl. Observed = the full 144,648-cell BTCM grid re-run with the MBT fee proxy $1.78 (17.8 points, half on every side incl. target exits) and the same slippage; each null world re-simulates the full grid with the same fee: random-side and forward-shifted-trigger placebos (the 'impossible' earlier-entry placebo is never used). Completed worlds: 132 random-side, 131 shifted-trigger (about 435 CPU-s per world, 5 workers, ~5 h budget). The p-values below replace the fee-less ones (count .01, max-stat .13).
| random side (N = 132 worlds) | observed (fee-adjusted) | null median / 95th / max | worlds >= observed | p = (k+1)/(N+1) | 95% CI of the true tail probability |
|---|---|---|---|---|---|
| tolerant cells | 540 | 400 / 563 / 632 | 12 | 0.098 | 0.048-0.153 |
| tolerant + persistent cells | 62 | 1 / 8 / 21 | 0 | 0.008 | 0.000-0.028 |
| distinct signal sets with a passing cell | 3 | 1 / 2 / 3 | 3 | 0.030 | 0.005-0.065 |
| max over cells of min(t_L6M, t_HOLD) | 2.77 | 2.65 / 3.25 / 4.17 | 41 | 0.316 | 0.233-0.397 |
| max full-sample t | 2.80 | 1.84 / 2.49 / 3.05 | 3 | 0.030 | 0.005-0.065 |

| forward-shifted trigger 5-60 min, same side (N = 131 worlds) | observed (fee-adjusted) | null median / 95th / max | worlds >= observed | p = (k+1)/(N+1) | 95% CI of the true tail probability |
|---|---|---|---|---|---|
| tolerant cells | 540 | 267 / 406 / 507 | 0 | 0.008 | 0.000-0.028 |
| tolerant + persistent cells | 62 | 1 / 8 / 16 | 0 | 0.008 | 0.000-0.028 |
| distinct signal sets with a passing cell | 3 | 1 / 2 / 4 | 4 | 0.038 | 0.008-0.076 |
| max over cells of min(t_L6M, t_HOLD) | 2.77 | 2.37 / 2.85 / 3.17 | 15 | 0.121 | 0.066-0.182 |
| max full-sample t | 2.80 | 1.94 / 2.60 / 2.86 | 1 | 0.015 | 0.000-0.042 |

Decision rule (fixed in the prereg): the cluster survives the family test only if S4 and S5 have p <= .10 against BOTH placebos. side: S4 p 0.316, S5 p 0.030 -> does not pass; shift: S4 p 0.121, S5 p 0.015 -> does not pass. 
Interpretation (S4b): 263 fee-adjusted worlds completed (132 random-side, 131 shifted-trigger; each world re-simulates the 144,648 cells). The preregistered rule (S4 AND S5 at p <= .10 against BOTH placebos) is NOT met because S4, the strength of the best cell in the RECENT windows (min of the L6M and HOLD t-statistics), is unremarkable against the null (p 0.32 random side, 0.12 shifted trigger; observed 2.77 vs null medians 2.65 and 2.37). What the fee-adjusted null does show is that the full-sample and persistence structure of the cluster is rarer than the placebos produce: max full-sample t 2.80 vs null 95th 2.49 / 2.60 (p 0.030 and 0.015, CI 0.005-0.065 and 0-0.042), tolerant + persistent cells 62 vs null max 21 / 16 (p 0.008 for both; the true tail probability is below 0.03), and 3 distinct signal sets vs null median 1 (p 0.03-0.04). The earlier fee-less statement 'count p .01 holds, max-stat p .13' is therefore replaced by: after the fee, the family-wise p of the best full-sample t is about 0.02-0.03 and the count test still holds, but the recent-window max-stat is not significant; the WATCH label is unchanged (the rule is not met), and the Shadow watch (WATCH_BTCM_KELTNER_SPEC.md) remains the only out-of-selection test. Caveats: the null re-uses the same entries / brackets with random side or delayed entry, so it tests direction and timing skill, not the Asia-session-clock choice; the fee, slippage and spread are proxies (MBT L2 / ticks not owned); 2022-2026 is one regime sample. Per-world vectors: /mnt/l2/l2vast/ds3_t2/BTCM_fee_null2.pkl.
