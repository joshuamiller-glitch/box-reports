# DS3_DIV_ZN - ZN (10-year note) intraday window rules, section 2 (D3DVR, 2026-10-28)

**Verdict (ZN): 0 CONFIRMED / 0 PASS / 0 CANDIDATE / 8 DEAD of 8 preregistered cells.** Every cell loses money net of cost in WF (the only exceptions to a negative HOLD or X are single noise reads on cells with a CI spanning zero), and the loss is the round-trip cost, not a wrong sign: the gross (zero-cost) edge per trade is -0.073 to +0.178 R across the cells while the cost per trade is 0.18 to 0.68 R (R = the $1,000 risk unit). No rule is added to the stack; no CONFIRMED rule means no weekly-$ or worst-20-weeks line to report. Best cell by WF mean: ZN_EV_NFPC (-0/wk, MDE 136), failed gates min_n, mean_up, beats_a, beats_b, cost2x_pre, year_share, span2, best_of_N.

Prereg: autopilot/DECISIONS.md line 'D3DVR PREREG' (master sha256 29950f8693554c9419e9aef94d05f182c23288460e69a6e40b960f33ffe1319a; ZN file sha256 13fb34e25d2e4a1e298773701b1835ca795bf3647ffe6b03090d97ae0f70ce35; l2vast/ds3/prereg/DVR_ZN_prereg.md), written before any cell was scored (one smoke-test total of E_RG_1000 was printed before it; disclosed). Pre-holdout texts autopilot/DS3_DVR_<group>_PREHOLD.md, one logged HOLD look per group plus the X look. Code l2vast/ds3/code/dvr/ (dvr_core, dvr_cells, dvr_sel, dvr_prereg, dvr_run, dvr_score, dvr_looks, dvr_audit, dvr_report, stack_series); outputs l2vast/ds3/out/dvr/. Research only; no live/execution/chart change; no download or purchase; UNTOUCHED (trade dates after 2026-02-06) never read.

Basis: 1-min bars (D3CX-conservative fills, harness rewritten for ET-clock windows; engine identity audit vs an independent python re-implementation on 7 cells x (real, random sides) = 14 comparisons over every day, 0 mismatches). Fees: ZN absent from FEES.md: 4.84 RT ES proxy (WEAK; probably conservative), siblings ZB/ZF the same; ZN tick 1/64 pt = $15.625 (min tick 1/2 of 1/32, verified from the data), $1000/pt; ZB tick 1/32 = $31.25; ZF tick 1/128 = $7.8125; slippage 1 tick/side, stop 2 ticks (D3CX). Equal $1,000 risk per trade (range/event: the stop; drift: the median window range as the unit, no stop), fractional lots, one trade per cell per day. Windows: WFPRE 2024-02-01..2025-06-30, WF 2024-02-01..2026-02-06, HOLD 2025-07-01..2026-02-06, X 2023-04-01..2024-01-31 (second holdout), years from 2023-02-10; 2026 = Jan 1..Feb 6 (5 weeks). All dollars are per week at $1,000 risk per trade, mean [95% CI] (MDE = 2.8 SE).

## Table 1 - main results (tier, failed gates, windows)

| cell | rule | tier (fee-capped) | failed gates | tr/wk (WF) | WFPRE | WF | HOLD | X (2023-04..2024-01) | WF at 2x cost | WF at 0.5x cost (optimistic) |
|---|---|---|---|---|---|---|---|---|---|---|
| ZN_EV_1500F | 15:00 close: fade the first-5-min move, flat 15:35 | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | 3.62 | -2,538 [-2,924, -2,152] (551) | -2,285 [-2,595, -1,975] (443) | -1,621 [-2,060, -1,182] (627) | -2,491 [-3,086, -1,896] (850) | -5,379 | -888 |
| ZN_EV_0830F | 08:30 releases: fade the first-5-min move, flat 09:05 | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | 4.22 | -1,030 [-1,362, -698] (474) | -960 [-1,218, -702] (369) | -765 [-1,125, -405] (515) | -1,303 [-1,880, -727] (824) | -2,066 | -440 |
| ZN_EV_NFPC | 08:30 first-Friday (NFP proxy): continue the first-5-min move, flat 09:05 | DEAD | min_n, mean_up, beats_a, beats_b, cost2x_pre, year_share, span2, best_of_N | 0.22 | -28 [-148, 92] (171) | -0 [-96, 95] (136) | 65 [-80, 210] (208) | -93 [-256, 71] (234) | -62 | 19 |
| ZN_RG_1000 | 10:00-10:15 break of 09:45-10:00 range | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | 3.86 | -1,266 [-1,504, -1,027] (341) | -1,309 [-1,500, -1,118] (273) | -1,370 [-1,657, -1,084] (409) | -1,249 [-1,588, -910] (484) | -2,754 | -660 |
| ZN_RG_0930 | 09:30-09:45 break of 09:15-09:30 range | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | 4.04 | -1,689 [-1,898, -1,481] (298) | -1,662 [-1,825, -1,499] (232) | -1,546 [-1,795, -1,297] (356) | -1,611 [-1,874, -1,349] (375) | -3,064 | -982 |
| ZN_RG_0900 | 09:00-09:15 break of 08:45-09:00 range | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | 3.75 | -1,670 [-1,878, -1,462] (297) | -1,704 [-1,860, -1,547] (223) | -1,728 [-1,935, -1,521] (296) | -1,638 [-1,902, -1,374] (377) | -3,291 | -990 |
| ZN_DR_1545L | 15:45-16:00 long drift | DEAD | mean_up, cost2x_pre, year_share, hold, span2, best_of_N | 4.74 | -1,895 [-2,128, -1,662] (333) | -1,907 [-2,082, -1,731] (250) | -1,874 [-2,107, -1,640] (333) | -1,757 [-2,131, -1,382] (535) | -4,094 | -813 |
| ZN_DR_0815L | 08:15-08:30 long drift | DEAD | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | 4.91 | -1,057 [-1,283, -831] (323) | -1,046 [-1,223, -870] (252) | -989 [-1,246, -731] (367) | -810 [-1,154, -467] (491) | -2,179 | -480 |

## Table 2 - consistency by year and half (directive standard: every year > 0 or within MDE; both halves > 0)

| cell | 2023 (from 02-10) | 2024 | 2025 | 2026 (5 wk) | years ok (mean > -MDE) / years strictly positive | pre-2025 half | post-2025 half | halves both > 0 |
|---|---|---|---|---|---|---|---|---|
| ZN_EV_1500F | -2,348 [-2,951, -1,746] (861) | -2,762 [-3,177, -2,348] (593) | -1,894 [-2,345, -1,444] (643) | -1,774 [-3,002, -546] (1,754) | no / 0 of 4 | -2,568 [-2,927, -2,209] (513) | -1,915 [-2,337, -1,492] (604) | no |
| ZN_EV_0830F | -1,309 [-1,867, -752] (797) | -993 [-1,357, -629] (520) | -915 [-1,292, -539] (538) | -802 [-1,320, -284] (740) | no / 0 of 4 | -1,142 [-1,467, -817] (465) | -919 [-1,265, -574] (494) | no |
| ZN_EV_NFPC | -38 [-190, 115] (218) | -90 [-243, 63] (219) | 71 [-49, 191] (171) | -38 [-114, 37] (108) | yes / 1 of 4 | -66 [-173, 42] (154) | 61 [-49, 171] (157) | no |
| ZN_RG_1000 | -1,328 [-1,690, -965] (519) | -1,332 [-1,626, -1,037] (421) | -1,305 [-1,551, -1,060] (350) | -1,285 [-2,332, -239] (1,495) | no / 0 of 4 | -1,330 [-1,560, -1,100] (329) | -1,326 [-1,569, -1,083] (347) | no |
| ZN_RG_0930 | -1,686 [-1,965, -1,407] (399) | -1,679 [-1,913, -1,445] (334) | -1,560 [-1,783, -1,336] (319) | -1,725 [-2,676, -774] (1,359) | no / 0 of 4 | -1,682 [-1,862, -1,503] (257) | -1,604 [-1,822, -1,385] (313) | no |
| ZN_RG_0900 | -1,669 [-1,932, -1,407] (375) | -1,572 [-1,816, -1,328] (349) | -1,723 [-1,919, -1,526] (281) | -1,941 [-2,617, -1,265] (965) | no / 0 of 4 | -1,618 [-1,796, -1,439] (255) | -1,775 [-1,961, -1,589] (266) | no |
| ZN_DR_1545L | -1,905 [-2,257, -1,554] (502) | -1,888 [-2,199, -1,578] (444) | -1,758 [-1,977, -1,538] (313) | -1,958 [-2,913, -1,003] (1,364) | no / 0 of 4 | -1,896 [-2,128, -1,664] (332) | -1,809 [-2,024, -1,593] (308) | no |
| ZN_DR_0815L | -793 [-1,149, -438] (508) | -1,174 [-1,439, -909] (379) | -841 [-1,084, -598] (347) | -1,151 [-1,504, -798] (505) | no / 0 of 4 | -995 [-1,216, -775] (315) | -887 [-1,113, -662] (322) | no |

## Table 3 - placebos (WF window, 40 draws each; effect = real minus mean of draws, $/wk [bootstrap CI] (MDE), rank = share of draws below the real), gross vs cost

| cell | (a) random direction, same clock | (b) random clock, same rule | HOLD (b) effect | paired-(a) WF R/trade [CI] | gross (0 cost) WF $/wk [CI] | gross R/trade | cost per trade (R) |
|---|---|---|---|---|---|---|---|
| ZN_EV_1500F | 329 [98, 553] (340) rank 1.00 | 191 [-100, 483] (429) rank 0.85 | 593 rank 1.00 | +0.091 [+0.023, +0.158] (0.096) n 384 | 163 [-54, 379] | +0.045 | 0.676 |
| ZN_EV_0830F | 106 [-161, 358] (375) rank 0.82 | -148 [-399, 121] (377) rank 0.03 | -24 rank 0.42 | +0.025 [-0.032, +0.082] (0.081) n 447 | 44 [-208, 297] | +0.011 | 0.238 |
| ZN_EV_NFPC | 27 [-62, 117] (132) rank 0.72 | 35 [-57, 135] (135) rank 0.97 | 90 rank 1.00 | +0.123 [-0.307, +0.552] (0.614) n 23 | 39 [-52, 129] | +0.178 | 0.179 |
| ZN_RG_1000 | 36 [-129, 215] (247) rank 0.60 | 17 [-175, 198] (269) rank 0.57 | -131 rank 0.12 | +0.009 [-0.035, +0.053] (0.063) n 409 | -21 [-204, 162] | -0.005 | 0.334 |
| ZN_RG_0930 | -270 [-426, -119] (222) rank 0.00 | -317 [-477, -172] (223) rank 0.00 | -330 rank 0.00 | -0.067 [-0.101, -0.033] (0.049) n 428 | -292 [-434, -151] | -0.072 | 0.339 |
| ZN_RG_0900 | -287 [-422, -133] (210) rank 0.00 | -194 [-344, -34] (221) rank 0.00 | -332 rank 0.00 | -0.076 [-0.112, -0.041] (0.051) n 398 | -274 [-413, -135] | -0.073 | 0.381 |
| ZN_DR_1545L | 326 [149, 508] (258) rank 1.00 | 325 [147, 511] (257) rank 1.00 | 331 rank 0.97 | +0.069 [+0.022, +0.116] (0.067) n 502 | 281 [115, 447] | +0.059 | 0.462 |
| ZN_DR_0815L | 80 [-92, 256] (254) rank 0.82 | 75 [-104, 241] (249) rank 0.88 | 139 rank 0.93 | +0.016 [-0.015, +0.048] (0.045) n 520 | 87 [-89, 263] | +0.018 | 0.231 |

Best-of-N: p95 of the family-wise null of the max (b) effect over the 8 cells = 418 $/wk (WFPRE). The gross column is a diagnostic added after FINAL (dvr_audit.py, mult 0 = no slippage, no fee); it is not a gate and changes no tier. Placebo (a) effects are positive for the drift cells because a random side loses cost on both sides of the coin; (a) and (b) beat random but the cell stays negative net: beating a placebo that also pays the cost is not an edge over cost.

## Table 4 - sibling replication (same cell, the sibling's own warm-up distance, 4.84 WEAK fee, same windows)

| cell | ZB WF $/wk [CI] (MDE) / HOLD / 2x / risk unit ticks | ZF WF $/wk [CI] (MDE) / HOLD / 2x / risk unit ticks | replicates (frozen R1 rule) |
|---|---|---|---|
| ZN_EV_1500F | -2,259 [-2,550, -1,968] (416) / -1,982 / -4,982 / 4 | -2,072 [-2,355, -1,790] (404) / -1,516 / -4,664 / 5 | no |
| ZN_EV_0830F | -1,137 [-1,405, -870] (382) / -865 / -2,147 / 10 | -1,007 [-1,294, -720] (410) / -814 / -2,042 / 12 | no |
| ZN_EV_NFPC | -7 [-99, 84] (131) / 100 / -46 / 10 | 15 [-86, 115] (144) / 77 / -22 / 12 | no |
| ZN_RG_1000 | -1,153 [-1,319, -986] (238) / -1,241 / -2,362 / 11 | -1,103 [-1,313, -893] (300) / -1,303 / -2,275 / 13 | no |
| ZN_RG_0930 | -1,536 [-1,704, -1,367] (241) / -1,588 / -2,879 / 10 | -1,403 [-1,569, -1,237] (237) / -1,342 / -2,726 / 12 | no |
| ZN_RG_0900 | -1,323 [-1,459, -1,186] (195) / -1,360 / -2,627 / 10 | -1,347 [-1,483, -1,211] (195) / -1,383 / -2,570 / 12 | no |
| ZN_DR_1545L | -1,545 [-1,685, -1,405] (200) / -1,506 / -3,239 / 6 | -1,724 [-1,927, -1,521] (290) / -1,895 / -3,787 / 6 | no |
| ZN_DR_0815L | -997 [-1,177, -817] (257) / -885 / -2,050 / 10 | -978 [-1,176, -780] (282) / -877 / -2,049 / 12 | no |

## Table 5 - link to the live stack (weekly P&L; stack = D3DVG baseline series; its WF mean is 45,947/wk on the full span to 2026-10 and 46,785/wk on the weeks to 2026-02-06 used here)

| cell | weekly corr to stack (WF) | (ALL 2023-02-10..) | cell $ in the stack's 20 worst WF weeks (sum / mean per week) | stack $ in those weeks | share of random-20-week draws at or below (p) | cell WF mean $/wk | stack WF mean $/wk (to 2026-02-06) |
|---|---|---|---|---|---|---|---|
| ZN_EV_1500F | +0.00 | -0.00 | -40,921 / -2,046 | -3,081,067 | 0.76 | -2,285 | 46,785 |
| ZN_EV_0830F | +0.16 | +0.16 | -24,116 / -1,206 | -3,081,067 | 0.18 | -960 | 46,785 |
| ZN_EV_NFPC | +0.07 | +0.12 | -955 / -48 | -3,081,067 | 0.34 | -0 | 46,785 |
| ZN_RG_1000 | -0.02 | -0.06 | -22,830 / -1,142 | -3,081,067 | 0.79 | -1,309 | 46,785 |
| ZN_RG_0930 | -0.02 | -0.02 | -32,947 / -1,647 | -3,081,067 | 0.54 | -1,662 | 46,785 |
| ZN_RG_0900 | -0.09 | -0.05 | -34,198 / -1,710 | -3,081,067 | 0.49 | -1,704 | 46,785 |
| ZN_DR_1545L | +0.11 | +0.11 | -42,500 / -2,125 | -3,081,067 | 0.12 | -1,907 | 46,785 |
| ZN_DR_0815L | +0.18 | +0.13 | -25,843 / -1,292 | -3,081,067 | 0.09 | -1,046 | 46,785 |

The cells are essentially uncorrelated with the stack (|corr| mostly < 0.2) but there is nothing to diversify with: a negative-mean book with ~0 correlation only subtracts. The 'worst 20 weeks' column is mostly the cell's own cost bleed in those weeks (its average week is already as negative), the p column shows where the sum sits relative to random 20-week draws of the cell itself.

## Top cells regardless of verdict (by WF mean $/wk at $1,000 risk)

| rank | cell | WF $/wk [CI] (MDE) | failed gates | CONFIRMED check (what fails) |
|---|---|---|---|---|
| 1 | ZN_EV_NFPC | -0 [-96, 95] (136) | min_n, mean_up, beats_a, beats_b, cost2x_pre, year_share, span2, best_of_N | gates: min_n, mean_up, beats_a, beats_b, cost2x_pre, year_share, span2, best_of_N; halves; WF placebos/2x; sibling |
| 2 | ZN_EV_0830F | -960 [-1,218, -702] (369) | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | gates: mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N; years: Y2023,Y2024,Y2025,Y2026; halves; WF placebos/2x; sibling |
| 3 | ZN_DR_0815L | -1,046 [-1,223, -870] (252) | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N | gates: mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N; years: Y2023,Y2024,Y2025,Y2026; halves; WF placebos/2x; sibling |

## Mechanisms and what the data say
- **Event and range cells (ZN).** The ZN risk unit is the median range of a 15-min window: 4-10 ticks ($62-$156 per lot). One tick of slippage each way plus 4.84 is $36 per lot round trip for a market-market trade (0.23-0.58 R) and 1-1.5 ticks more for a stop-entry; a cell needs a gross edge above that per trade to survive, and the gross diagnostic shows 0.00-0.18 R (the 18% is the 41-trade NFP proxy, inside its noise). The three range cells lose to a negative gross: breaks of the prior 15-min range at 09:00/09:30 *mean-revert* (gross -0.07 R, CI below zero in WF; this is the placebo-(a) rank 0.00 in WFPRE: the opposite direction is the better one), the 10:00 break is flat gross. The two event-fade cells (15:00, 08:30) have gross +0.05/+0.01 R, nowhere near cost.
- **Drift cells (ZN).** 15:45-16:00 long has a real gross edge in WF (+$281/wk, CI [115, 447], about 0.06 R/trade; selection-span t +3.1, 4 of 4 years), which is 0.15x the round-trip cost in bps, as the maps said; after cost it is -$1,907/wk (-0.6 R per trade) because the unit is a 5-tick window.
- **Fee.** ZN has no FEES.md line; 4.84 is the ES proxy and is probably conservative. It is not the driver: the slippage (2 ticks of a 1/64 contract) is $31.25 of the $36 per lot, and the 0.5x row (half slippage, half fee) is still negative for every cell except the 0.2-trades-per-week NFP proxy (+$19/wk on 41 trades, noise).
- **Tick data.** ZN trades are on disk (2023-02..2026-10-12) but were NOT used: no cell is net-positive on the conservative bar basis or on the optimistic 0.5x basis, so a print-level stop-fill study cannot change a verdict (it could only move the 2-tick stop assumption). NFP and 13:00 auction days are proxies (first Friday; no auction calendar on disk); the 13:00 auctions have no cell (the maps' event rule did not select them: range ratio 1.2, cont30 t -0.2).

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
