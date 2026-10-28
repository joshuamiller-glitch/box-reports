# DS3_DIV_GC - gold (GC) one-rule-per-window cells (D3DVC, 2026-10-28)

Research only; no live / execution / chart change; no download, no purchase; UNTOUCHED (trade dates after 2026-02-06) never read. Prereg `l2vast/ds3/prereg/D3DVC_prereg.md` sha256 9cd38a51b0be5a75a73ca696cf5defb9feb30cf787aade1a47e8afdf185108b9 (17 cells = CL 7 + GC 10, written and logged in DECISIONS.md before any P&L; ledger +17). Pre-holdout text `DS3_DVC_GC_PREHOLD.md` (WFPRE only), ONE main-holdout look per group + the 2023-span look logged (tracks DS3_DVC_GC, _SPAN2). Code `l2vast/ds3/code/dvc/`, outputs `l2vast/ds3/out/dvc/` (final.pkl, score_PRE.pkl, per-symbol pickles, stack_daily.csv).

## Verdict (headline)
**No GC cell is CONFIRMED or CANDIDATE; 10 of 10 are DEAD** (fee line WEAK, ceiling would be CANDIDATE). The best one, **GC_ONL** (long at the 13:30 settle, flat the next day 08:20, Mon-Thu), earns WF +$341/wk [135, 546] (MDE 293; one-sided p about 0.001, Bonferroni over the 17 registered cells about 0.01), HOLD +$284 [-50, 618], X +$217, every calendar year positive (2023 +$83, 2024 +$368, 2025 +$300, 2026 +$803 in 6 weeks), both halves positive (+$234, +$358), 2x-cost +$318, SI sibling WF +$173 / HOLD +$224. It FAILS the placebo-(b) gate: the random-clock overnight long (random entry 13:00-16:30 ET, random exit 07:00-10:00 next day) earns almost the same (effect +$37 in WF, rank 0.87, CI includes 0; HOLD (b) effect -$27) and placebo (a) is positive only because the random-direction placebo averages the gold uptrend (long and short) to zero (+$346). Reading: the 13:30->08:20 clock adds nothing over being long gold overnight; the cell is the gold bull market of 2023-2026 harvested in the overnight hours, at about 0.35 lots per $1,000 of risk. It fails 'hold' (HOLD (b) effect <= 0) and best_of_N (placebo-(b) effect +$37 vs the family p95 of +$449), so it is DEAD under the program's gates, with the failed gates named. If a long-gold overnight exposure were wanted for its own sake (beta, not clock edge), it is the one to examine (stack correlation +0.13 ALL, its weekly $ in the stack's 20 worst weeks -$1,436, i.e. no hedge).
- The GC drift cells (D1645L, D0500L, D1245L) have WF means of +$63, +$126, +$44 per week (all inside MDE 290-430), pass placebo (a) (random direction costs ~ -$300 to -$400/wk, so the real direction is better than a coin flip) but the same gross edge of ~2 ticks is eaten by the 2.48-tick cost: 2x-cost WF -$396, -$142, -$207 (all negative), and the 2023 span (X) is -$458 / -$476 for D0500L / D1245L, i.e. the effect is not there before 2024. GC_D0500L is the best of this group: WF +$126 [-86, 337], HOLD +$330 [-65, 725], pre/post-2025 -$171/+$178 (fails halves, 2023 -$391), X -$458 (fails span2), sibling SI WF -$396 (fails).
- The settle event drift (D1330L) is zero (WF -$22) and the PM-fix continuation E1000C is zero (WF +$34 [-221, 289], 2026 -$920 in 6 weeks); the AM-fix continuation E0530C is negative (WF -$264 [-498, -31]) exactly as the selection-span descriptive (-0.37 ticks, t -0.4) said.
- The range cells (R0830, R0930, R1000) are -$24, -$128, -$178 per week in WF (all CIs include zero), 2x-cost -$300 to -$410; they beat the random-clock placebo (b), which loses more, so a (b) pass is not evidence of an edge here.
- Stack: weekly correlations within +/-0.20 (GC_E1000C -0.20, GC_ONL +0.13): no cell is correlated with the live stack; none earns enough, net of a defensible cost, to be a diversifier.

## Basis (identical in both market files)
- 1-min OHLCV (Databento .v.0 volume-roll, back-adjusted; RB/HO/SI adjusted here with the same rule), D3CX conservative fills (market +1 tick, stop +2 ticks, limit/target on a 1-tick trade-through, stop-first, no target credit in the entry bar of a stop-entry). Fee $4.84 RT = ES proxy: **WEAK for CL, GC and all siblings; verdict ceiling CANDIDATE; 2x cost shown on every row.** CL tick $10, GC tick $10 (verified from the data's minimum price step: 0.01 and 0.1), RB/HO $4.20, SI $25. Equal $1,000 risk at the stop (fractional lots). The stop/bracket distances are 1.0x/1.5x (drift cells 1.5x stop, no target) of the market's own as-of 20-day median window range, rounded to the tick, floor 4 ticks.
- Windows: WFPRE 2024-02-01..2025-06-30, WF 2024-02-01..2026-02-06, HOLD 2025-07-01..2026-02-06 (~32 weeks), X 2023-04-01..2024-01-31, ALL 2023-02-10..2026-02-06. Weekly $ at $1,000 risk per trade.
- Selection disclosure: windows came from DS3_DIV_1_MAPS and were re-chosen with the selection span (to 2025-06-30) only; that span contains WFPRE and X, so those two are not out-of-sample for the window choice (the brackets are fixed multiples, not tuned). HOLD is the only data not used for the choice, with low power (MDE beside every HOLD number).
- Tiers: all gates pass = CANDIDATE (capped; would be PASS on a solid fee line); only best_of_N and/or sibling fail = LEAD; else DEAD. Gates: PRE min_n>=30, mean_up, beats_a, beats_b (effect CI lower > 0 and rank >= 0.95), cost2x_pre, year_share <= 60%; FINAL hold, span2, years (each year >= -MDE), halves (pre-2025 and post-2025 both > 0), best_of_N (placebo-(b) WFPRE effect > family p95 over 17 cells = $449/wk), sibling (sibling WF and HOLD mean > 0).  `year_share` is reported as failed when the WFPRE total is not positive.

## Per-cell verdict table

| cell | rule | trades/wk (WF) | WF $/wk [95% CI] (MDE) | HOLD $/wk [CI] (MDE) | X (2023-04..2024-01) | WF 2x cost | sibling SI WF / HOLD | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|
| GC_D1645L | long 16:45-17:00 | 4.7 | 63 [-239, 366] (MDE 432) | -50 [-667, 566] (MDE 881) | 42 (MDE 591) | -396 | -667 / -412 | DEAD | beats_b, cost2x_pre, year_share, hold, halves, best_of_N, sibling |
| GC_D0500L | long 05:00-05:15 | 4.9 | 126 [-86, 337] (MDE 302) | 330 [-65, 725] (MDE 564) | -458 (MDE 458) | -142 | -396 / 162 | DEAD | cost2x_pre, year_share, span2, halves, best_of_N, sibling |
| GC_D1245L | long 12:45-13:00 | 4.9 | 44 [-160, 248] (MDE 291) | 44 [-295, 383] (MDE 484) | -476 (MDE 569) | -207 | -330 / -299 | DEAD | cost2x_pre, year_share, span2, halves, best_of_N, sibling |
| GC_D1330L | long 13:30-14:00 (settle event drift 0..+30) | 4.9 | -22 [-264, 221] (MDE 346) | 15 [-340, 369] (MDE 506) | -325 (MDE 459) | -230 | -118 / 94 | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, span2, halves, best_of_N, sibling |
| GC_E0530C | London AM fix 10:30 UK (~05:30 ET), continue first-5-min move, +5..+35 | 4.7 | -264 [-498, -31] (MDE 334) | -235 [-660, 190] (MDE 607) | -829 (MDE 690) | -532 | -529 / -463 | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, years, halves, best_of_N, sibling |
| GC_E1000C | London PM fix 15:00 UK (~10:00 ET), continue first-5-min move, +5..+35 | 4.9 | 34 [-221, 289] (MDE 364) | 6 [-500, 512] (MDE 723) | 43 (MDE 683) | -109 | -207 / -420 | DEAD | beats_a, beats_b, cost2x_pre, year_share, best_of_N, sibling |
| GC_R0830 | break of 08:15-08:30 range during 08:30-08:45 | 4.4 | -24 [-296, 247] (MDE 388) | 130 [-417, 677] (MDE 782) | 55 (MDE 599) | -298 | -267 / -195 | DEAD | mean_up, cost2x_pre, year_share, halves, best_of_N, sibling |
| GC_R0930 | break of 09:15-09:30 range during 09:30-09:45 | 4.7 | -128 [-414, 158] (MDE 408) | -137 [-615, 342] (MDE 684) | -379 (MDE 545) | -335 | -444 / -462 | DEAD | mean_up, beats_a, cost2x_pre, year_share, hold, span2, halves, best_of_N, sibling |
| GC_R1000 | break of 09:45-10:00 range during 10:00-10:15 | 4.5 | -178 [-449, 93] (MDE 387) | -7 [-522, 508] (MDE 736) | -427 (MDE 525) | -408 | -496 / -235 | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, halves, best_of_N, sibling |
| GC_ONL | long at 13:30 settle, flat next-day 08:20 (Mon-Thu entries) | 3.8 | 341 [135, 546] (MDE 293) | 284 [-50, 618] (MDE 477) | 217 (MDE 462) | 318 | 173 / 224 | DEAD | beats_b, hold, best_of_N |

Predictions written before scoring (prereg): D cells -$100..+$40, R cells -$700..-$200, ON cells -$50..+$300, E cells -$150..+$60 per week. Outcome: the stated dollar ranges were missed by CL_D1400S (-$332 vs -$100..$0), CL_E1030C (-$95 vs -$60..+$60), GC_E0530C (-$264 vs -$150..$0), all on the negative side, and by GC_ONL (+$341 vs +$0..+$300, slightly better); the R cells fell inside their ranges (CL -$426..-$476, GC -$24..-$178); the prediction "any cell reaches CANDIDATE: ~10%" held (none).

## By calendar year (mean $/wk [95% CI] (MDE); 2023 from 02-10, 2026 = 02-01..02-06 only, ~5 weeks), and halves

| cell | 2023 | 2024 | 2025 | 2026 (5 wk) | pre-2025 half | post-2025 half | all-span ALL |
|---|---|---|---|---|---|---|---|
| GC_D1645L | 73 [-371, 516] (MDE 633) | 242 [-211, 696] (MDE 648) | -298 [-591, -5] (MDE 418) | 1,762 [-267, 3,790] (MDE 2,897) | 163 | -90 | 70 [-173, 314] (MDE 348) |
| GC_D0500L | -391 [-698, -83] (MDE 439) | 23 [-232, 278] (MDE 364) | 123 [-220, 466] (MDE 490) | 630 [296, 964] (MDE 477) | -171 | 178 | -43 [-219, 132] (MDE 250) |
| GC_D1245L | -436 [-816, -55] (MDE 544) | 78 [-172, 328] (MDE 357) | -30 [-351, 290] (MDE 458) | -72 [-740, 595] (MDE 953) | -164 | -35 | -117 [-300, 65] (MDE 261) |
| GC_D1330L | -260 [-564, 44] (MDE 434) | -166 [-505, 174] (MDE 485) | 121 [-223, 466] (MDE 492) | -200 [-791, 391] (MDE 844) | -210 | 90 | -100 [-289, 88] (MDE 269) |
| GC_E0530C | -780 [-1,250, -310] (MDE 671) | -248 [-631, 136] (MDE 548) | -388 [-691, -84] (MDE 433) | -48 [-911, 815] (MDE 1,233) | -498 | -359 | -450 [-670, -230] (MDE 314) |
| GC_E1000C | -8 [-449, 433] (MDE 630) | 34 [-311, 379] (MDE 492) | 151 [-205, 506] (MDE 508) | -920 [-2,088, 247] (MDE 1,668) | 14 | 43 | 25 [-194, 244] (MDE 313) |
| GC_R0830 | -195 [-616, 225] (MDE 601) | -133 [-551, 285] (MDE 597) | 224 [-120, 567] (MDE 491) | -889 [-2,242, 465] (MDE 1,933) | -162 | 113 | -62 [-291, 167] (MDE 327) |
| GC_R0930 | -323 [-675, 28] (MDE 502) | -273 [-656, 111] (MDE 547) | 106 [-318, 530] (MDE 606) | -957 [-1,752, -162] (MDE 1,136) | -296 | -2 | -190 [-413, 34] (MDE 319) |
| GC_R1000 | -260 [-625, 105] (MDE 522) | -205 [-580, 170] (MDE 535) | -179 [-563, 205] (MDE 549) | -250 [-1,583, 1,084] (MDE 1,905) | -231 | -189 | -217 [-433, -1] (MDE 309) |
| GC_ONL | 83 [-204, 370] (MDE 410) | 368 [117, 620] (MDE 359) | 300 [-18, 619] (MDE 455) | 803 [-277, 1,884] (MDE 1,543) | 234 | 358 | 281 [115, 448] (MDE 238) |

## Placebos (WF window; 100 draws each; effect = real minus mean of draws, weekly $; CI by week bootstrap; rank = share of draws below the real; MDE beside each)

| cell | (a) random direction, same clock | (b) same rule, random clock | HOLD (a) eff rank | HOLD (b) eff rank | paired-(a) WF R/trade [CI] (MDE) | WF meanR / win / stop% / target% |
|---|---|---|---|---|---|---|
| GC_D1645L | 426 [177, 690] (MDE 373) r1.00 | 243 [-41, 562] (MDE 438) r0.97 | 123 r0.66 | 61 r0.67 | +0.091 [+0.040, +0.142] (0.073) | +0.014 / 0.46 / 0.07 / 0.00 |
| GC_D0500L | 419 [216, 633] (MDE 286) r1.00 | 323 [107, 553] (MDE 307) r1.00 | 583 r1.00 | 470 r0.96 | +0.086 [+0.042, +0.130] (0.063) | +0.026 / 0.52 / 0.06 / 0.00 |
| GC_D1245L | 352 [139, 574] (MDE 311) r1.00 | 228 [17, 434] (MDE 308) r0.98 | 292 r0.93 | 123 r0.69 | +0.072 [+0.031, +0.114] (0.060) | +0.009 / 0.52 / 0.06 / 0.00 |
| GC_D1330L | 182 [-60, 446] (MDE 342) r0.98 | 87 [-160, 369] (MDE 355) r0.77 | 125 r0.74 | 57 r0.61 | +0.037 [-0.007, +0.082] (0.064) | -0.004 / 0.50 / 0.07 / 0.00 |
| GC_E0530C | 67 [-175, 301] (MDE 335) r0.67 | 1 [-233, 254] (MDE 341) r0.59 | 87 r0.60 | 16 r0.55 | +0.014 [-0.045, +0.073] (0.084) | -0.056 / 0.47 / 0.17 / 0.06 |
| GC_E1000C | 122 [-138, 378] (MDE 367) r0.80 | 259 [5, 497] (MDE 363) r0.93 | 48 r0.54 | 207 r0.73 | +0.025 [-0.034, +0.084] (0.084) | +0.007 / 0.49 / 0.14 / 0.06 |
| GC_R0830 | 309 [62, 548] (MDE 368) r1.00 | 452 [197, 716] (MDE 370) r1.00 | 328 r0.89 | 485 r0.98 | +0.070 [+0.010, +0.130] (0.086) | -0.005 / 0.46 / 0.17 / 0.10 |
| GC_R0930 | 81 [-192, 361] (MDE 395) r0.71 | 356 [79, 635] (MDE 399) r1.00 | 105 r0.71 | 221 r0.79 | +0.017 [-0.039, +0.074] (0.081) | -0.027 / 0.45 / 0.13 / 0.05 |
| GC_R1000 | 69 [-181, 309] (MDE 348) r0.66 | 313 [49, 588] (MDE 393) r0.99 | 92 r0.59 | 371 r0.91 | +0.015 [-0.039, +0.070] (0.078) | -0.040 / 0.43 / 0.12 / 0.06 |
| GC_ONL | 346 [163, 538] (MDE 276) r1.00 | 37 [-25, 101] (MDE 90) r0.87 | 294 r0.95 | -27 r0.35 | +0.091 [+0.045, +0.138] (0.066) | +0.090 / 0.60 / 0.04 / 0.00 |

Reading the placebos: for the long-only cells (all D, ON) placebo (a) averages long and short and is cheap to beat in a trending market; (b) keeps the direction and is the test of the clock. For the R (stop-entry) cells every random clock loses more than the real one (costs of ~0.1 R per trade), so beating (b) there is not an edge: the real mean is what matters, and it is negative.

## Sibling replication (SI, same ET clock and rules, own median ranges, $4.84 fee proxy; sign-level test, power low)

| cell | SI WF $/wk [CI] (MDE) | SI HOLD $/wk (MDE) | SI trades/wk | SI WF 2x | sibling gate |
|---|---|---|---|---|---|
| GC_D1645L | -667 [-985, -348] (MDE 455) | -412 (903) | 4.7 | -1,868 | FAIL |
| GC_D0500L | -396 [-629, -164] (MDE 332) | 162 (685) | 4.9 | -994 | FAIL |
| GC_D1245L | -330 [-539, -120] (MDE 299) | -299 (712) | 4.8 | -881 | FAIL |
| GC_D1330L | -118 [-417, 181] (MDE 427) | 94 (601) | 4.8 | -586 | FAIL |
| GC_E0530C | -529 [-801, -256] (MDE 389) | -463 (599) | 4.4 | -1,197 | FAIL |
| GC_E1000C | -207 [-529, 115] (MDE 460) | -420 (731) | 4.7 | -494 | FAIL |
| GC_R0830 | -267 [-565, 32] (MDE 426) | -195 (719) | 4.3 | -879 | FAIL |
| GC_R0930 | -444 [-728, -159] (MDE 407) | -462 (855) | 4.6 | -906 | FAIL |
| GC_R1000 | -496 [-792, -200] (MDE 423) | -235 (950) | 4.1 | -910 | FAIL |
| GC_ONL | 173 [-3, 349] (MDE 252) | 224 (399) | 3.8 | 119 | pass |
## Relation to the live stack (D3SL stack nominal daily P&L, weekly Pearson; cell at $1,000 risk per trade, stack at its own lots)

| cell | weekly corr ALL | weekly corr WF | cell $ in the stack's 20 worst weeks (ALL) | per-week avg | in 20 worst WF weeks | cell mean $/wk ALL |
|---|---|---|---|---|---|---|
| GC_D1645L | +0.07 | +0.05 | -12,988 | -649 | 284 | 70 |
| GC_D0500L | +0.08 | +0.13 | 1,059 | 53 | 5,904 | -43 |
| GC_D1245L | +0.03 | +0.05 | -2,997 | -150 | 1,130 | -117 |
| GC_D1330L | -0.06 | -0.15 | -9,712 | -486 | 1,811 | -100 |
| GC_E0530C | -0.07 | +0.02 | -1,263 | -63 | -772 | -450 |
| GC_E1000C | -0.20 | -0.12 | 9,492 | 475 | -1,605 | 25 |
| GC_R0830 | +0.03 | +0.06 | -4,403 | -220 | 4,082 | -62 |
| GC_R0930 | +0.00 | +0.03 | -455 | -23 | -1,735 | -190 |
| GC_R1000 | +0.05 | +0.13 | -4,253 | -213 | -13,726 | -217 |
| GC_ONL | +0.13 | +0.06 | -1,436 | -72 | 5,244 | 281 |

Worst-20 sums are noisy: a cell with weekly SD of ~$1,100 has a sum-of-20 SD of ~$4,900, so values within +/-$5k are indistinguishable from zero. None of the cells is a measurable hedge or a measurable drag on the stack; all correlations are within +/-0.2.

## Roll handling (explicit)

- Measured: the volume-roll bar (instrument_id change) falls at 18:00-20:00 ET in this data (CL 44 rolls up to 2026-02-06, 36 since 2023-02-10, 52 up to 2026-10-16; GC 18 / 15). So **no 03:00-17:00 intraday window contains a roll bar**; only the overnight cell spans it.
- ON cell: trades whose span contains a roll bar are skipped (primary): 12 of 742 signals (all dates). Including them changes the WF mean from 341 to 339: immaterial.
- Roll-labelled days (label date that holds a roll bar, i.e. the first session on the new contract): per-trade mean on those days vs the others, intraday cells:

| cell | roll-day trades (ALL) | mean $/trade on roll days | mean $/trade other days |
|---|---|---|---|
| GC_D1645L | 16 | 200 | -10 |
| GC_D0500L | 18 | -125 | -13 |
| GC_D1245L | 18 | -173 | -36 |
| GC_D1330L | 18 | -224 | -30 |
| GC_E0530C | 18 | 336 | -95 |
| GC_E1000C | 18 | -122 | 3 |
| GC_R0830 | 16 | -137 | -26 |
| GC_R0930 | 17 | 234 | -48 |
| GC_R1000 | 14 | -203 | -46 |
| GC_ONL | 0 | nan | 59 |

(Roll-day counts are 14-44 trades per cell; the differences are inside noise, e.g. a per-trade SD of ~$400 gives an SE of ~$65-100. No roll-day effect is claimed.)

## Top cells regardless of verdict (never empty-handed)
1. **GC_ONL** (long 13:30 settle -> next 08:20, Mon-Thu, 3.8 trades/wk, ~0.35 lots per $1,000 risk): WF +$341/wk [135, 546], MDE 293; HOLD +$284 [-50, 618], MDE 477; X +$217; 2x cost +$318; all years and both halves positive; SI sibling WF +$173, HOLD +$224. **Failed gates: beats_b (rank 0.87, effect +$37, CI includes 0), hold ((b) effect in HOLD -$27), best_of_N (+$37 vs p95 +$449).** The clock adds nothing over a random overnight window: this is long-gold beta over a trending span (gold's strength 2023-2026), not an intraday-structure edge. The 2023 span cell value +$217 is also trend.
2. **GC_D0500L** (long 05:00-05:15): WF +$126/wk [-86, 337], MDE 302; HOLD +$330 [-65, 725], MDE 564; fails cost2x_pre (2x -$142), span2 (X -$458), halves (-$171/+$178), best_of_N, sibling (SI WF -$396).
3. **GC_D1645L** (long 16:45-17:00): WF +$63/wk [-239, 366], MDE 432; strongest selection-span t (+4.5) but 2x -$396, HOLD -$50, post-2025 half -$90, SI sibling -$667.
What would change the answer: a verified fee line (COMEX metals fees are likely at or above the 4.84 proxy, so it would worsen), a cost basis below 2.48 ticks, top-of-book data (P3 GC mbp-1 $70.26, user OK required), and a way to separate the overnight-long premium from the gold trend (not available from 3 years of one regime; the pre-2023 span is not used by this program).

## Print-level (tick trades) check
Not triggered: no GC cell reached CANDIDATE/CONFIRMED. The GC_ONL entry/exit are market orders at 13:30 and 08:20, where the 1-min bar's open equals the first print by construction; stop slippage is irrelevant there (stop 284 ticks, hit 4% of trades). The check that matters (quote-based spread at 08:20 and 13:30) needs mbp-1 (P3, not bought).

## Disclosures
1. Selection overlap: the windows come from the maps (trade dates to 2026-02-06 incl. HOLD) and were re-chosen with selection-span (to 2025-06-30) numbers only; that span contains WFPRE and X, so WFPRE/X are in-sample for the window choice. HOLD (~32 weeks) is the only data not used, with the MDEs shown. The selection rule (|t| >= 2 and |mean| >= 0.5x cost) plus the directive's named events produced 7 CL and 10 GC cells; F = 17 for the family best-of-N gate.
2. Fees WEAK (4.84 ES proxy for CL, GC, RB, HO, SI): CONFIRMED is not reportable; no cell reached even CANDIDATE.
3. Events have no calendar: CL Wed 10:30 is every Wednesday (holiday-shifted weeks and the occasional delayed EIA release are included; the cell has ~0.9 trades/wk); GC London fixes use Europe/London local time so their ET time shifts in the UK/US clock-mismatch weeks; early-close days are not removed (bars must exist at the required minutes, otherwise no trade).
4. Bar model limits: stop-first within a minute, no intrabar order; 1-tick adverse market fills and 2-tick stop slippage are assumptions without quote data; the fill-bar target is not credited in stop-entry cells.
5. Long-only cells and the gold uptrend (2023-2026) / crude's flat-to-down regime: placebo (a) does not control for the trend; (b) does.
6. Code notes: no bug was found during scoring. A dead expression in `run()` (fill for mode 1, `... if False else fillp[k]`) is harmless: entry fills for stop-entry cells come from the pre-priced array. Rolling medians are as-of (shift(1)) and need >= 10 prior values. Equal-risk lots are fractional (as in D3CX/D3CFA); at integer lots the small ON cells (0.35-0.5 lots) are not tradeable at $1,000 risk: one contract risks about $2,000-2,800.
7. The stack series is the D3SL nominal daily P&L (vs_lib.total(stack_books())), exported unchanged (WF baseline 45,947/wk reproduced); it excludes DS4/DS5 add-on books.
8. Siblings RB/HO/SI were back-adjusted here from their raw caches (additive roll-gap removal); the sibling runs have no placebos (real and 2x only).
9. Roll bars all sit at 18:00-20:00 ET, so the one place the CL contract rolls (52 to 2026-10-16, monthly) can touch these cells is the overnight cell, handled by skipping.

