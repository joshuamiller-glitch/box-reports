# DS3_DIV_6E - 6E (Euro FX) intraday window rules, section 2 (D3DVR, 2026-10-28)

**Verdict (6E): 0 CONFIRMED / 0 PASS / 0 CANDIDATE / 10 DEAD of 10 preregistered cells.** Every cell loses money net of cost in WF (the only exceptions to a negative HOLD or X are single noise reads on cells with a CI spanning zero), and the loss is the round-trip cost, not a wrong sign: the gross (zero-cost) edge per trade is -0.005 to +0.111 R across the cells while the cost per trade is 0.10 to 0.32 R (R = the $1,000 risk unit). No rule is added to the stack; no CONFIRMED rule means no weekly-$ or worst-20-weeks line to report. Best cell by WF mean: E_DR_0300L (-299/wk, MDE 318), failed gates mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N.

Prereg: autopilot/DECISIONS.md line 'D3DVR PREREG' (master sha256 29950f8693554c9419e9aef94d05f182c23288460e69a6e40b960f33ffe1319a; 6E file sha256 8f40d5802161db686f936ea5dc364a4cd9e1f5c8bb82ec168a89eeb79748afac; l2vast/ds3/prereg/DVR_6E_prereg.md), written before any cell was scored (one smoke-test total of E_RG_1000 was printed before it; disclosed). Pre-holdout texts autopilot/DS3_DVR_<group>_PREHOLD.md, one logged HOLD look per group plus the X look. Code l2vast/ds3/code/dvr/ (dvr_core, dvr_cells, dvr_sel, dvr_prereg, dvr_run, dvr_score, dvr_looks, dvr_audit, dvr_report, stack_series); outputs l2vast/ds3/out/dvr/. Research only; no live/execution/chart change; no download or purchase; UNTOUCHED (trade dates after 2026-02-06) never read.

Basis: 1-min bars (D3CX-conservative fills, harness rewritten for ET-clock windows; engine identity audit vs an independent python re-implementation on 7 cells x (real, random sides) = 14 comparisons over every day, 0 mismatches). Fees: 6E 5.30 RT (FEES.md 6E ADDENDUM: commission/clearing/routing NT-published, exchange+NFA third-party = WEAK); sibling 6B 4.84 ES proxy (WEAK, no 6B line); 6E tick 0.00005 = $6.25 ($125,000/pt), 6B tick 0.0001 = $6.25 ($62,500/pt); slippage 1 tick/side, stop 2 ticks (D3CX). Equal $1,000 risk per trade (range/event: the stop; drift: the median window range as the unit, no stop), fractional lots, one trade per cell per day. Windows: WFPRE 2024-02-01..2025-06-30, WF 2024-02-01..2026-02-06, HOLD 2025-07-01..2026-02-06, X 2023-04-01..2024-01-31 (second holdout), years from 2023-02-10; 2026 = Jan 1..Feb 6 (5 weeks). All dollars are per week at $1,000 risk per trade, mean [95% CI] (MDE = 2.8 SE).

## Table 1 - main results (tier, failed gates, windows)

| cell | rule | tier (fee-capped) | failed gates | tr/wk (WF) | WFPRE | WF | HOLD | X (2023-04..2024-01) | WF at 2x cost | WF at 0.5x cost (optimistic) |
|---|---|---|---|---|---|---|---|---|---|---|
| E_EV_0830F | 08:30 releases: fade the first-5-min move, flat 09:05 | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | 4.67 | -411 [-734, -88] (461) | -453 [-732, -175] (398) | -538 [-1,074, -3] (765) | -260 [-799, 279] (770) | -952 | -189 |
| E_DR_1645L | 16:45-17:00 long | DEAD | mean_up, cost2x_pre, year_share, hold, span2 | 4.85 | -852 [-1,294, -410] (631) | -997 [-1,339, -655] (489) | -1,305 [-1,757, -852] (646) | -1,014 [-1,233, -796] (312) | -2,531 | -229 |
| E_DR_0745S | 07:45-08:00 short | DEAD | mean_up, cost2x_pre, year_share, hold, best_of_N | 4.91 | -299 [-492, -105] (277) | -405 [-578, -232] (247) | -642 [-983, -301] (487) | 93 [-148, 335] (345) | -987 | -114 |
| E_DR_0800L | 08:00-08:15 long | DEAD | mean_up, cost2x_pre, year_share, hold, span2 | 4.91 | -195 [-470, 80] (393) | -327 [-551, -103] (320) | -625 [-969, -282] (491) | -196 [-472, 81] (395) | -962 | -9 |
| E_DR_0245S | 02:45-03:00 short | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | 4.91 | -480 [-675, -285] (279) | -401 [-563, -240] (231) | -205 [-471, 61] (380) | -282 [-598, 34] (451) | -1,036 | -84 |
| E_DR_0300L | 03:00-03:15 long | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | 4.91 | -305 [-581, -28] (395) | -299 [-521, -76] (318) | -275 [-632, 82] (511) | -88 [-466, 290] (540) | -797 | -49 |
| E_DR_0430L | 04:30-04:45 long | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | 4.91 | -449 [-711, -186] (375) | -491 [-697, -285] (294) | -575 [-872, -278] (425) | -298 [-594, -1] (424) | -1,098 | -187 |
| E_RG_1000 | 10:00-10:15 break of 09:45-10:00 range | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | 4.26 | -274 [-481, -68] (295) | -315 [-492, -138] (253) | -400 [-738, -62] (483) | -144 [-422, 135] (398) | -786 | -98 |
| E_RG_1045 | 10:45-11:00 break of 10:30-10:45 range | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | 4.17 | -469 [-658, -281] (270) | -483 [-642, -323] (227) | -498 [-767, -230] (384) | -378 [-586, -171] (297) | -962 | -236 |
| E_RG_0900 | 09:00-09:15 break of 08:45-09:00 range | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | 4.10 | -570 [-759, -382] (270) | -565 [-725, -405] (229) | -536 [-835, -237] (427) | -534 [-878, -190] (491) | -1,111 | -289 |

## Table 2 - consistency by year and half (directive standard: every year > 0 or within MDE; both halves > 0)

| cell | 2023 (from 02-10) | 2024 | 2025 | 2026 (5 wk) | years ok (mean > -MDE) / years strictly positive | pre-2025 half | post-2025 half | halves both > 0 |
|---|---|---|---|---|---|---|---|---|
| E_EV_0830F | -502 [-970, -33] (669) | -795 [-1,182, -408] (553) | 82 [-323, 488] (579) | -1,054 [-2,111, 3] (1,510) | no / 1 of 4 | -657 [-958, -356] (430) | -34 [-428, 361] (564) | no |
| E_DR_1645L | -1,070 [-1,308, -832] (340) | -1,239 [-1,492, -985] (362) | -712 [-1,340, -84] (897) | -1,112 [-1,816, -408] (1,005) | no / 0 of 4 | -1,160 [-1,334, -985] (249) | -766 [-1,344, -187] (826) | no |
| E_DR_0745S | 19 [-250, 288] (384) | -376 [-599, -154] (318) | -383 [-647, -119] (377) | -493 [-1,126, 139] (904) | no / 1 of 4 | -190 [-367, -14] (252) | -401 [-649, -153] (354) | no |
| E_DR_0800L | -258 [-528, 11] (385) | -208 [-460, 44] (360) | -389 [-768, -10] (541) | -622 [-1,308, 65] (981) | yes / 0 of 4 | -232 [-415, -49] (262) | -420 [-773, -68] (504) | no |
| E_DR_0245S | -457 [-765, -148] (441) | -495 [-687, -303] (274) | -232 [-502, 39] (386) | -190 [-631, 251] (630) | no / 0 of 4 | -477 [-653, -300] (252) | -231 [-482, 19] (358) | no |
| E_DR_0300L | -181 [-542, 180] (516) | -464 [-676, -252] (302) | -110 [-504, 283] (562) | -369 [-870, 132] (716) | no / 0 of 4 | -331 [-535, -127] (292) | -139 [-502, 224] (519) | no |
| E_DR_0430L | -273 [-550, 3] (395) | -539 [-776, -301] (340) | -429 [-773, -84] (492) | -667 [-1,314, -20] (924) | no / 0 of 4 | -414 [-596, -232] (260) | -461 [-781, -141] (458) | no |
| E_RG_1000 | -133 [-405, 140] (389) | -277 [-525, -30] (353) | -369 [-614, -124] (350) | -16 [-883, 852] (1,239) | no / 0 of 4 | -209 [-392, -26] (261) | -339 [-578, -99] (343) | no |
| E_RG_1045 | -466 [-696, -236] (329) | -529 [-713, -344] (264) | -431 [-691, -170] (372) | -418 [-865, 28] (638) | no / 0 of 4 | -499 [-645, -354] (207) | -437 [-676, -197] (342) | no |
| E_RG_0900 | -529 [-858, -199] (471) | -581 [-791, -370] (300) | -596 [-849, -343] (361) | -398 [-813, 17] (593) | no / 0 of 4 | -556 [-746, -366] (271) | -586 [-819, -352] (334) | no |

## Table 3 - placebos (WF window, 40 draws each; effect = real minus mean of draws, $/wk [bootstrap CI] (MDE), rank = share of draws below the real), gross vs cost

| cell | (a) random direction, same clock | (b) random clock, same rule | HOLD (b) effect | paired-(a) WF R/trade [CI] | gross (0 cost) WF $/wk [CI] | gross R/trade | cost per trade (R) |
|---|---|---|---|---|---|---|---|
| E_EV_0830F | 117 [-152, 381] (394) rank 0.75 | 11 [-271, 286] (407) rank 0.55 | -60 rank 0.38 | +0.025 [-0.033, +0.083] (0.083) n 495 | 51 [-227, 329] | +0.011 | 0.108 |
| E_DR_1645L | 526 [224, 866] (484) rank 1.00 | 557 [229, 923] (508) rank 1.00 | 367 rank 0.80 | +0.108 [+0.046, +0.171] (0.089) n 514 | 538 [196, 880] | +0.111 | 0.316 |
| E_DR_0745S | 190 [16, 365] (251) rank 1.00 | 181 [1, 359] (249) rank 0.95 | 2 rank 0.42 | +0.039 [+0.001, +0.076] (0.053) n 520 | 177 [5, 349] | +0.036 | 0.119 |
| E_DR_0800L | 274 [70, 498] (318) rank 1.00 | 294 [69, 530] (341) rank 1.00 | -2 rank 0.53 | +0.056 [+0.013, +0.098] (0.061) n 520 | 308 [85, 532] | +0.063 | 0.129 |
| E_DR_0245S | 235 [54, 404] (247) rank 1.00 | 235 [56, 407] (246) rank 0.97 | 394 rank 1.00 | +0.048 [+0.005, +0.091] (0.062) n 520 | 234 [72, 396] | +0.048 | 0.129 |
| E_DR_0300L | 198 [-18, 400] (312) rank 0.97 | 202 [-20, 411] (315) rank 0.97 | 254 rank 0.95 | +0.040 [-0.003, +0.084] (0.062) n 520 | 200 [-22, 423] | +0.041 | 0.102 |
| E_DR_0430L | 98 [-96, 297] (291) rank 0.90 | 136 [-62, 338] (296) rank 0.90 | 74 rank 0.62 | +0.020 [-0.020, +0.060] (0.058) n 520 | 116 [-90, 323] | +0.024 | 0.124 |
| E_RG_1000 | 132 [-39, 302] (260) rank 0.88 | 65 [-98, 227] (253) rank 0.88 | -7 rank 0.53 | +0.031 [-0.011, +0.073] (0.060) n 452 | 119 [-59, 296] | +0.028 | 0.102 |
| E_RG_1045 | -4 [-166, 158] (226) rank 0.50 | -40 [-199, 133] (228) rank 0.23 | -63 rank 0.23 | -0.001 [-0.040, +0.038] (0.056) n 442 | 4 [-152, 161] | +0.001 | 0.117 |
| E_RG_0900 | -16 [-180, 138] (228) rank 0.38 | -68 [-237, 95] (237) rank 0.15 | -24 rank 0.38 | -0.004 [-0.042, +0.034] (0.054) n 435 | -22 [-180, 136] | -0.005 | 0.132 |

Best-of-N: p95 of the family-wise null of the max (b) effect over the 10 cells = 416 $/wk (WFPRE). The gross column is a diagnostic added after FINAL (dvr_audit.py, mult 0 = no slippage, no fee); it is not a gate and changes no tier. Placebo (a) effects are positive for the drift cells because a random side loses cost on both sides of the coin; (a) and (b) beat random but the cell stays negative net: beating a placebo that also pays the cost is not an edge over cost.

## Table 4 - sibling replication (same cell, the sibling's own warm-up distance, 4.84 WEAK fee, same windows)

| cell | 6B WF $/wk [CI] (MDE) / HOLD / 2x / risk unit ticks | replicates (frozen R1 rule) |
|---|---|---|
| E_EV_0830F | -675 [-923, -427] (354) / -915 / -1,408 / 19 | no |
| E_DR_1645L | -1,701 [-1,978, -1,424] (395) / -2,170 / -3,891 / 6 | no |
| E_DR_0745S | -928 [-1,126, -731] (282) / -1,129 / -1,834 / 15 | no |
| E_DR_0800L | -736 [-925, -547] (270) / -1,073 / -1,640 / 15 | no |
| E_DR_0245S | -832 [-990, -674] (226) / -723 / -1,802 / 14 | no |
| E_DR_0300L | -634 [-837, -430] (291) / -671 / -1,348 / 19 | no |
| E_DR_0430L | -862 [-1,048, -677] (265) / -860 / -1,768 / 15 | no |
| E_RG_1000 | -581 [-736, -425] (222) / -638 / -1,223 / 25 | no |
| E_RG_1045 | -774 [-923, -625] (213) / -705 / -1,490 / 22 | no |
| E_RG_0900 | -935 [-1,082, -788] (210) / -727 / -1,772 / 19 | no |

## Table 5 - link to the live stack (weekly P&L; stack = D3DVG baseline series; its WF mean is 45,947/wk on the full span to 2026-10 and 46,785/wk on the weeks to 2026-02-06 used here)

| cell | weekly corr to stack (WF) | (ALL 2023-02-10..) | cell $ in the stack's 20 worst WF weeks (sum / mean per week) | stack $ in those weeks | share of random-20-week draws at or below (p) | cell WF mean $/wk | stack WF mean $/wk (to 2026-02-06) |
|---|---|---|---|---|---|---|---|
| E_EV_0830F | -0.04 | +0.01 | -2,577 / -129 | -3,081,067 | 0.87 | -453 | 46,785 |
| E_DR_1645L | +0.01 | -0.01 | -19,318 / -966 | -3,081,067 | 0.58 | -997 | 46,785 |
| E_DR_0745S | -0.03 | -0.01 | -8,565 / -428 | -3,081,067 | 0.44 | -405 | 46,785 |
| E_DR_0800L | +0.02 | +0.06 | -6,844 / -342 | -3,081,067 | 0.48 | -327 | 46,785 |
| E_DR_0245S | +0.11 | +0.02 | -10,889 / -544 | -3,081,067 | 0.19 | -401 | 46,785 |
| E_DR_0300L | -0.03 | -0.02 | -7,163 / -358 | -3,081,067 | 0.40 | -299 | 46,785 |
| E_DR_0430L | +0.11 | +0.07 | -13,459 / -673 | -3,081,067 | 0.20 | -491 | 46,785 |
| E_RG_1000 | -0.00 | -0.05 | -6,027 / -301 | -3,081,067 | 0.55 | -315 | 46,785 |
| E_RG_1045 | +0.01 | +0.02 | -7,571 / -379 | -3,081,067 | 0.73 | -483 | 46,785 |
| E_RG_0900 | +0.11 | +0.12 | -15,708 / -785 | -3,081,067 | 0.09 | -565 | 46,785 |

The cells are essentially uncorrelated with the stack (|corr| mostly < 0.2) but there is nothing to diversify with: a negative-mean book with ~0 correlation only subtracts. The 'worst 20 weeks' column is mostly the cell's own cost bleed in those weeks (its average week is already as negative), the p column shows where the sum sits relative to random 20-week draws of the cell itself.

## Top cells regardless of verdict (by WF mean $/wk at $1,000 risk)

| rank | cell | WF $/wk [CI] (MDE) | failed gates | CONFIRMED check (what fails) |
|---|---|---|---|---|
| 1 | E_DR_0300L | -299 [-521, -76] (318) | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | gates: mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N; years: Y2024; halves; WF placebos/2x; sibling |
| 2 | E_RG_1000 | -315 [-492, -138] (253) | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | gates: mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N; years: Y2025; halves; WF placebos/2x; sibling |
| 3 | E_DR_0800L | -327 [-551, -103] (320) | mean_up, cost2x_pre, year_share, hold, span2 | gates: mean_up, cost2x_pre, year_share, hold, span2; halves; WF placebos/2x; sibling |

## Mechanisms and what the data say
- **Drift cells (6E).** Several selection-span drifts persist in gross terms: 16:45-17:00 long +$538/wk [196, 880] (0.11 R/trade, 4 of 4 years in the selection span), 08:00-08:15 long +$308 [85, 532], 02:45 short +$234 [72, 396], 07:45 short +$177 [5, 349] (zero cost, WF). They beat both placebos in WFPRE for 16:45, 07:45 and 08:00 (rank 0.95-1.00), i.e. the *direction and clock* carry information. But the risk unit of a drift cell is the window's median range (9-28 ticks = $56-$175) and a round trip costs $12.5 slippage + $5.30 fee = $17.8 per lot, which is 0.10-0.32 R of the unit per trade against a gross of 0.02-0.11 R. Net WF -$299 to -$997/wk. The 16:45 cell is the extreme: nine-tick unit, 17.8 lots, 4.8 trades a week.
- **HOLD.** The late-span means in the maps already warned: 07:45 and 08:00 drifts are ~0 after 2025-06 (late +0.13 / +0.01 bps); gross HOLD is -$64 and +$6 per week; the 02:45 short and 03:00 long persist (gross HOLD +$426/+$221) but cost more than that.
- **Range and event cells (6E).** Breaks of the prior 15-min range have a gross of -0.005 to +0.03 R per trade (10:00: +$119/wk, CI [-59, 296]); the cost of a stop-entry (2 ticks) plus stop/flat exit (1-2 ticks) plus fee is 0.10-0.13 R per trade. The 08:30 fade has +0.01 R gross.
- **Fee and tick.** 6E 5.30 RT: commission/clearing/routing NT-published, exchange+NFA third-party (WEAK); 6B and the siblings run the 4.84 ES proxy. At the 0.5x row (6.25 + 2.65 per lot) E_DR_0800L reaches -$9/wk and E_DR_1645L -$229, still not positive. The real 6E quote is 1 tick wide on the front month, so a market order costs ~0.5 tick (the harness 1 tick is conservative); a passive limit entry would save more but the harness gives no credit to resting limits and 6E has no trades/quotes on disk (P1/P3 purchase lines unbought). The 0.5x row is therefore the realistic lower bound of cost and it is still negative.

## Disclosures
1. **Window choice is not out-of-sample.** The windows come from DS3_DIV_1_MAPS (trade dates 2022-06-01..2026-02-06). Direction and existence were fixed from the selection span (to 2025-06-30) by l2vast/ds3/code/dvr/dvr_sel.py (sel_span.json), but WFPRE and X lie inside that span, so they are in-sample for the choice; HOLD (2025-07..2026-02-06) was displayed by the maps (late-span column) though not used here. UNTOUCHED (after 2026-02-06) is the only unseen data and was not read. Every verdict here is negative, so the contamination can only have flattered the cells.
2. **One P&L number was seen before the prereg**: a smoke test printed the whole-span total of E_RG_1000 (negative). No definition, window, distance or gate was changed after it (logged in the prereg and DECISIONS.md).
3. **Stack series.** stack_series.py ran the shared D3DVG baseline (it computes through 2026-10-16 internally and printed the known WF/WFPRE means 45,947/44,127 per week before any cut); only days 2023-02-10..2026-02-06 were used afterwards (cut in dvr_score.stack_weekly). The stack is the D3DVG convention (10 x weights, exact lock engine, 50-contract cap, PB masked).
4. **Calendar proxies.** NFP = first Friday of the month (36-45 events; BLS occasionally releases on the 2nd Friday); ZN 13:00 auctions have no cell; releases at 08:30 are all days (no CPI/claims separation); early-close and holiday sessions are dropped by the < 40% bar-count rule.
5. **Drift cells have no stop**, the risk unit is the warm-up median window range (so 'equal $1,000 risk' is nominal); range and event cells size to the stop (a stop fill with 2 ticks slippage loses slightly more than $1,000).
6. **Bar basis.** Stop-first within a minute, no target credit in the stop-entry bar, a minute containing both range extremes is a no-trade (counted in the engine, <1% of days); limit/passive entries are not modelled, so a cell that needed queue-position fills to beat cost is untestable here. 1-tick market slippage is conservative for ZN and 6E (the half-spread is ~0.5 tick); the 0.5x-cost row is shown as the optimistic ceiling and no verdict uses it.
7. **Fees WEAK** (ZN, ZB, ZF, 6B: ES proxy; 6E exchange part third-party): ceiling CANDIDATE; irrelevant here because no cell reaches PASS.
8. **Sibling independence.** ZN/ZB/ZF are one rates factor (weekly P&L correlations high); a sibling pass would not have been independent evidence.
9. No bug was found; the engine matches an independent re-implementation exactly (14 audits, 0 mismatches). Two coding slips were fixed before the first scored cell (placebo arrays not sliced to the scoring days; paired test index) and are not scoring-related.
