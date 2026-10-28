# DS3_DIV_CL - crude oil (CL) one-rule-per-window cells (D3DVC, 2026-10-28)

Research only; no live / execution / chart change; no download, no purchase; UNTOUCHED (trade dates after 2026-02-06) never read. Prereg `l2vast/ds3/prereg/D3DVC_prereg.md` sha256 9cd38a51b0be5a75a73ca696cf5defb9feb30cf787aade1a47e8afdf185108b9 (17 cells = CL 7 + GC 10, written and logged in DECISIONS.md before any P&L; ledger +17). Pre-holdout text `DS3_DVC_CL_PREHOLD.md` (WFPRE only), ONE main-holdout look per group + the 2023-span look logged (tracks DS3_DVC_CL, _SPAN2). Code `l2vast/ds3/code/dvc/`, outputs `l2vast/ds3/out/dvc/` (final.pkl, score_PRE.pkl, per-symbol pickles, stack_daily.csv).

## Verdict (headline)
**No CL cell is CONFIRMED, CANDIDATE or even LEAD. 7 of 7 are DEAD.** The ceiling would have been CANDIDATE anyway (fee line WEAK: ES 4.84 proxy, FEES.md has no CL line).
- The two 15-min drift cells (CL_D1430L settle long, CL_D1400S short) have a real selection-span gross drift (+2.0 and +1.9 ticks, t 3.4 and 2.5) but it is 0.8x the 2.48-tick round-trip cost, so the net is about zero: D1430L WF -$75/wk [-282, 132] (MDE 296), HOLD -$379, and it fails the half test (pre-2025 -$23, post-2025 -$297) and the 2x-cost gate (-$569); D1400S is negative in WF (-$332 [-579, -85]) with a CI that excludes zero on the wrong side.
- The three range-expansion cells (R0900, R0930, R1000) lose $430-480/wk in WF with a CI wholly below zero (R0900 [-690, -163], R0930 [-743, -209], R1000 [-676, -193]): stop-entry slippage (2 ticks) + 1-tick flat + fee on a 40-tick stop cost about 0.1 R per trade at 4.2-4.5 trades/wk, and the breakout continuation after a quiet 15-min box is about zero (mean R -0.09 to -0.11, WF). They beat placebo (b) only because a random-clock breakout loses even more (-$700+): that is not an edge.
- The EIA cell (CL_E1030C, Wed 10:30, continuation of the first 5-min move) is about zero and negative: WF -$95/wk [-239, 49] (MDE 206), ~0.9 trades/wk; the +3.3 tick selection-span continuation (t +0.8) did not persist (first-5-min continuation is not distinguishable from noise, the 2025 year is -$183).
- The overnight cell CL_ONL (long 14:30 settle -> next 09:00, Mon-Thu, 3.6 trades/wk) is the only CL cell with positive WF/HOLD/X/halves/years (WF +$80/wk [-101, 262], MDE 259; HOLD +$46; X +$213; every year positive; pre/post-2025 +$123/+$47; 2x-cost +$30) but it is inside its MDE and fails the placebos (a rank 0.88, b rank 0.95 with effect CI including 0): the random overnight clock earns almost as much, i.e. it is generic crude-long overnight exposure, not a settle-to-open edge. Sibling RB/HO: WF +$45, HOLD +$31 (weak, same sign).
- Stack: all weekly correlations are within +/-0.16 (CL_R1000 +0.16, CL_ONL -0.09), i.e. these cells are uncorrelated to the live stack, but a diversifier has to earn money first and none does.

## Basis (identical in both market files)
- 1-min OHLCV (Databento .v.0 volume-roll, back-adjusted; RB/HO/SI adjusted here with the same rule), D3CX conservative fills (market +1 tick, stop +2 ticks, limit/target on a 1-tick trade-through, stop-first, no target credit in the entry bar of a stop-entry). Fee $4.84 RT = ES proxy: **WEAK for CL, GC and all siblings; verdict ceiling CANDIDATE; 2x cost shown on every row.** CL tick $10, GC tick $10 (verified from the data's minimum price step: 0.01 and 0.1), RB/HO $4.20, SI $25. Equal $1,000 risk at the stop (fractional lots). The stop/bracket distances are 1.0x/1.5x (drift cells 1.5x stop, no target) of the market's own as-of 20-day median window range, rounded to the tick, floor 4 ticks.
- Windows: WFPRE 2024-02-01..2025-06-30, WF 2024-02-01..2026-02-06, HOLD 2025-07-01..2026-02-06 (~32 weeks), X 2023-04-01..2024-01-31, ALL 2023-02-10..2026-02-06. Weekly $ at $1,000 risk per trade.
- Selection disclosure: windows came from DS3_DIV_1_MAPS and were re-chosen with the selection span (to 2025-06-30) only; that span contains WFPRE and X, so those two are not out-of-sample for the window choice (the brackets are fixed multiples, not tuned). HOLD is the only data not used for the choice, with low power (MDE beside every HOLD number).
- Tiers: all gates pass = CANDIDATE (capped; would be PASS on a solid fee line); only best_of_N and/or sibling fail = LEAD; else DEAD. Gates: PRE min_n>=30, mean_up, beats_a, beats_b (effect CI lower > 0 and rank >= 0.95), cost2x_pre, year_share <= 60%; FINAL hold, span2, years (each year >= -MDE), halves (pre-2025 and post-2025 both > 0), best_of_N (placebo-(b) WFPRE effect > family p95 over 17 cells = $449/wk), sibling (sibling WF and HOLD mean > 0).  `year_share` is reported as failed when the WFPRE total is not positive.

## Per-cell verdict table

| cell | rule | trades/wk (WF) | WF $/wk [95% CI] (MDE) | HOLD $/wk [CI] (MDE) | X (2023-04..2024-01) | WF 2x cost | sibling RB, HO WF / HOLD | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|
| CL_D1430L | long 14:30-14:45 (settle window drift) | 4.8 | -75 [-282, 132] (MDE 296) | -379 [-762, 4] (MDE 547) | -105 (MDE 380) | -569 | 130 / -257 | DEAD | cost2x_pre, year_share, hold, span2, halves, best_of_N, sibling |
| CL_D1400S | short 14:00-14:15 | 4.9 | -332 [-579, -85] (MDE 353) | -377 [-818, 64] (MDE 630) | 47 (MDE 480) | -752 | -146 / -163 | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, halves, best_of_N, sibling |
| CL_E1030C | Wed 10:30 EIA, continue first-5-min move, +5..+35 | 1.0 | -95 [-239, 49] (MDE 206) | -52 [-300, 195] (MDE 354) | -77 (MDE 333) | -167 | -42 / -76 | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, halves, best_of_N, sibling |
| CL_R0900 | break of 08:45-09:00 range during 09:00-09:15 | 4.6 | -426 [-690, -163] (MDE 377) | -157 [-654, 339] (MDE 710) | -30 (MDE 471) | -932 | 5 / 261 | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, years, halves, best_of_N |
| CL_R0930 | break of 09:15-09:30 range during 09:30-09:45 | 4.3 | -476 [-743, -209] (MDE 381) | -195 [-699, 309] (MDE 720) | -238 (MDE 607) | -1,050 | -126 / -148 | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, years, halves, best_of_N, sibling |
| CL_R1000 | break of 09:45-10:00 range during 10:00-10:15 | 4.1 | -435 [-676, -193] (MDE 345) | -562 [-989, -136] (MDE 609) | -665 (MDE 457) | -895 | -25 / 10 | DEAD | mean_up, beats_a, cost2x_pre, year_share, hold, span2, years, halves, best_of_N, sibling |
| CL_ONL | long at 14:30 settle, flat next-day 09:00 (Mon-Thu entries) | 3.6 | 80 [-101, 262] (MDE 259) | 46 [-282, 373] (MDE 468) | 213 (MDE 385) | 30 | 45 / 31 | DEAD | beats_a, beats_b, year_share, best_of_N |

Predictions written before scoring (prereg): D cells -$100..+$40, R cells -$700..-$200, ON cells -$50..+$300, E cells -$150..+$60 per week. Outcome: the stated dollar ranges were missed by CL_D1400S (-$332 vs -$100..$0), CL_E1030C (-$95 vs -$60..+$60), GC_E0530C (-$264 vs -$150..$0), all on the negative side, and by GC_ONL (+$341 vs +$0..+$300, slightly better); the R cells fell inside their ranges (CL -$426..-$476, GC -$24..-$178); the prediction "any cell reaches CANDIDATE: ~10%" held (none).

## By calendar year (mean $/wk [95% CI] (MDE); 2023 from 02-10, 2026 = 02-01..02-06 only, ~5 weeks), and halves

| cell | 2023 | 2024 | 2025 | 2026 (5 wk) | pre-2025 half | post-2025 half | all-span ALL |
|---|---|---|---|---|---|---|---|
| CL_D1430L | -294 [-570, -19] (MDE 393) | 218 [-67, 503] (MDE 407) | -265 [-544, 14] (MDE 398) | -532 [-1,387, 323] (MDE 1,222) | -23 | -297 | -124 [-289, 40] (MDE 235) |
| CL_D1400S | -19 [-415, 377] (MDE 566) | -218 [-536, 101] (MDE 455) | -345 [-706, 16] (MDE 515) | -716 [-2,099, 666] (MDE 1,975) | -124 | -389 | -223 [-431, -15] (MDE 297) |
| CL_E1030C | -107 [-331, 117] (MDE 320) | -7 [-231, 217] (MDE 320) | -183 [-374, 9] (MDE 274) | 200 [-63, 463] (MDE 376) | -54 | -146 | -88 [-209, 32] (MDE 172) |
| CL_R0900 | -121 [-441, 200] (MDE 458) | -575 [-898, -252] (MDE 461) | -282 [-693, 129] (MDE 587) | 289 [-364, 942] (MDE 933) | -362 | -228 | -314 [-518, -111] (MDE 291) |
| CL_R0930 | -359 [-765, 47] (MDE 580) | -623 [-961, -286] (MDE 482) | -279 [-692, 134] (MDE 590) | 52 [-1,237, 1,341] (MDE 1,841) | -499 | -249 | -410 [-633, -187] (MDE 318) |
| CL_R1000 | -480 [-782, -178] (MDE 431) | -536 [-898, -175] (MDE 517) | -414 [-739, -90] (MDE 463) | -284 [-1,444, 876] (MDE 1,657) | -510 | -408 | -476 [-666, -285] (MDE 273) |
| CL_ONL | 96 [-168, 359] (MDE 376) | 147 [-69, 364] (MDE 309) | 11 [-279, 300] (MDE 413) | 362 [-539, 1,263] (MDE 1,287) | 123 | 47 | 96 [-52, 244] (MDE 212) |

## Placebos (WF window; 100 draws each; effect = real minus mean of draws, weekly $; CI by week bootstrap; rank = share of draws below the real; MDE beside each)

| cell | (a) random direction, same clock | (b) same rule, random clock | HOLD (a) eff rank | HOLD (b) eff rank | paired-(a) WF R/trade [CI] (MDE) | WF meanR / win / stop% / target% |
|---|---|---|---|---|---|---|
| CL_D1430L | 440 [257, 645] (MDE 287) r1.00 | 341 [150, 557] (MDE 296) r1.00 | 162 r0.79 | 88 r0.69 | +0.092 [+0.048, +0.136] (0.063) | -0.016 / 0.50 / 0.05 / 0.00 |
| CL_D1400S | 105 [-141, 337] (MDE 357) r0.86 | 97 [-150, 341] (MDE 357) r0.84 | 109 r0.73 | 121 r0.72 | +0.022 [-0.022, +0.065] (0.062) | -0.068 / 0.41 / 0.06 / 0.00 |
| CL_E1030C | -25 [-161, 120] (MDE 199) r0.40 | -8 [-152, 146] (MDE 204) r0.46 | 18 r0.54 | 44 r0.60 | -0.025 [-0.171, +0.120] (0.207) | -0.099 / 0.46 / 0.25 / 0.05 |
| CL_R0900 | 110 [-160, 374] (MDE 376) r0.79 | 302 [21, 577] (MDE 380) r0.99 | 386 r0.95 | 600 r1.00 | +0.024 [-0.032, +0.080] (0.080) | -0.093 / 0.46 / 0.15 / 0.04 |
| CL_R0930 | 17 [-243, 290] (MDE 386) r0.64 | 249 [-4, 537] (MDE 388) r0.97 | 378 r0.97 | 566 r0.99 | +0.004 [-0.054, +0.061] (0.082) | -0.111 / 0.41 / 0.13 / 0.04 |
| CL_R1000 | 74 [-159, 299] (MDE 337) r0.75 | 317 [72, 545] (MDE 349) r1.00 | 6 r0.54 | 234 r0.87 | +0.018 [-0.038, +0.074] (0.080) | -0.105 / 0.41 / 0.15 / 0.04 |
| CL_ONL | 89 [-90, 260] (MDE 274) r0.88 | 54 [11, 97] (MDE 66) r0.95 | 84 r0.70 | 51 r0.78 | +0.025 [-0.025, +0.074] (0.071) | +0.022 / 0.55 / 0.04 / 0.00 |

Reading the placebos: for the long-only cells (all D, ON) placebo (a) averages long and short and is cheap to beat in a trending market; (b) keeps the direction and is the test of the clock. For the R (stop-entry) cells every random clock loses more than the real one (costs of ~0.1 R per trade), so beating (b) there is not an edge: the real mean is what matters, and it is negative.

## Sibling replication (RB, HO, same ET clock and rules, own median ranges, $4.84 fee proxy; sign-level test, power low)

| cell | RB WF $/wk [CI] (MDE) | RB HOLD $/wk (MDE) | RB trades/wk | RB WF 2x | HO WF $/wk [CI] (MDE) | HO HOLD $/wk (MDE) | HO trades/wk | HO WF 2x | sibling gate |
|---|---|---|---|---|---|---|---|---|---|
| CL_D1430L | -28 [-244, 189] (MDE 309) | -295 (547) | 4.8 | -260 | 288 [65, 512] (MDE 319) | -219 (523) | 4.8 | 71 | FAIL |
| CL_D1400S | -250 [-471, -28] (MDE 317) | -255 (607) | 4.9 | -428 | -43 [-269, 183] (MDE 322) | -70 (549) | 4.9 | -203 | FAIL |
| CL_E1030C | -84 [-231, 62] (MDE 209) | -71 (376) | 1.0 | -111 | -0 [-132, 132] (MDE 188) | -82 (318) | 1.0 | -22 | FAIL |
| CL_R0900 | -3 [-249, 243] (MDE 351) | 431 (638) | 4.6 | -203 | 13 [-240, 265] (MDE 361) | 91 (677) | 4.6 | -170 | pass |
| CL_R0930 | -196 [-468, 75] (MDE 388) | -175 (775) | 4.5 | -420 | -56 [-294, 183] (MDE 341) | -121 (556) | 4.4 | -263 | FAIL |
| CL_R1000 | 54 [-186, 295] (MDE 344) | 7 (552) | 4.3 | -152 | -105 [-348, 139] (MDE 348) | 13 (589) | 4.4 | -296 | FAIL |
| CL_ONL | 39 [-117, 195] (MDE 223) | 91 (434) | 3.4 | 18 | 51 [-130, 232] (MDE 258) | -29 (492) | 3.6 | 32 | pass |

RB and HO have thin overnight bars (bars only in 64-65% of ET minutes; the signals need a bar at the stated minute, so the sibling trade counts are lower than CL where the market was thin) and their CL-clock windows are not their own structural events; a sibling failure on the 09:00-10:15 and 14:00-14:45 clocks is weak evidence about the CL effect, a sibling pass would have been supporting.

## Relation to the live stack (D3SL stack nominal daily P&L, weekly Pearson; cell at $1,000 risk per trade, stack at its own lots)

| cell | weekly corr ALL | weekly corr WF | cell $ in the stack's 20 worst weeks (ALL) | per-week avg | in 20 worst WF weeks | cell mean $/wk ALL |
|---|---|---|---|---|---|---|
| CL_D1430L | -0.01 | -0.09 | -6,159 | -308 | 3,133 | -124 |
| CL_D1400S | -0.03 | +0.00 | -2,140 | -107 | -9,696 | -223 |
| CL_E1030C | +0.01 | -0.14 | -3,532 | -177 | 2,081 | -88 |
| CL_R0900 | -0.01 | -0.09 | -14,747 | -737 | -10,784 | -314 |
| CL_R0930 | -0.04 | -0.01 | -3,127 | -156 | -5,363 | -410 |
| CL_R1000 | +0.16 | +0.24 | -9,980 | -499 | -20,937 | -476 |
| CL_ONL | -0.09 | -0.21 | 10,251 | 513 | 12,695 | 96 |

Worst-20 sums are noisy: a cell with weekly SD of ~$1,100 has a sum-of-20 SD of ~$4,900, so values within +/-$5k are indistinguishable from zero. None of the cells is a measurable hedge or a measurable drag on the stack; all correlations are within +/-0.2.

## Roll handling (explicit)

- Measured: the volume-roll bar (instrument_id change) falls at 18:00-20:00 ET in this data (CL 44 rolls up to 2026-02-06, 36 since 2023-02-10, 52 up to 2026-10-16; GC 18 / 15). So **no 03:00-17:00 intraday window contains a roll bar**; only the overnight cell spans it.
- ON cell: trades whose span contains a roll bar are skipped (primary): 21 of 722 signals (all dates). Including them changes the WF mean from 80 to 94: immaterial.
- Roll-labelled days (label date that holds a roll bar, i.e. the first session on the new contract): per-trade mean on those days vs the others, intraday cells:

| cell | roll-day trades (ALL) | mean $/trade on roll days | mean $/trade other days |
|---|---|---|---|
| CL_D1430L | 39 | -14 | -32 |
| CL_D1400S | 44 | -55 | -38 |
| CL_E1030C | 9 | -317 | -36 |
| CL_R0900 | 43 | -73 | -64 |
| CL_R0930 | 37 | -18 | -86 |
| CL_R1000 | 38 | -190 | -102 |
| CL_ONL | 0 | nan | 30 |

(Roll-day counts are 14-44 trades per cell; the differences are inside noise, e.g. a per-trade SD of ~$400 gives an SE of ~$65-100. No roll-day effect is claimed.)

## Top cells regardless of verdict (never empty-handed)
1. **CL_ONL** (long 14:30 -> next 09:00, Mon-Thu): WF +$80/wk [-101, 262], MDE 259; fails beats_a (WF rank 0.88), beats_b (WF rank 0.95, effect CI includes 0), year_share, best_of_N. All years and both halves positive. Needed to confirm at this size: MDE 259 vs mean 80 means ~1,500 weeks. Not a clock edge.
2. **CL_D1430L** (settle-window long): gross edge real (selection t 3.4) but 0.8x cost; WF -$75/wk [-282, 132] (MDE 296); fails cost2x_pre, hold, span2, halves, best_of_N, sibling.
3. **CL_E1030C** (Wed EIA continuation): WF -$95/wk [-239, 49] (MDE 206), ~0.9 trades/wk; fails mean_up and everything after.
What would change the answer: only a lower cost basis (limit/maker entries are outside the registered rule set), an NT statement line for CL and top-of-book data (P3 mbp-1 CL $57.31, user OK required) to calibrate stop slippage at 10:30. At 2.48 ticks per round trip the 15-min CL drifts (1.9-2.0 ticks) cannot pay.

## Print-level (tick trades) check
Not triggered: the program ran print-level stop/limit fill checks for cells reaching CANDIDATE/CONFIRMED and no CL cell did. Note that a 1-min bar's open is the first print of that minute by construction, so market-entry realism cannot be improved from trades alone (needs the quote: mbp-1, purchase P3, not bought).

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

