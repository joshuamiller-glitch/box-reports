# DS3_MANCINI - Mancini frame as stand-alone NQ books: failed breakdown (A), back-test (B), level set incl. a simple ascending trendline (MN-1, written Sat 2026-10-31). POST-HOC, nothing here is a PASS, nothing promoted

**DATA line.** On disk: NQ tick tape 2023-02..2026-10, 1-s and 1-min tables with mbp-10 summaries (bsz/asz 1-10), ES/RTY, raw mbp-10. Used: the ds3_g2 1-s print path (per print-second high / low / last, back-adjusted continuous frame, 36.56M seconds 2023-02-08..2026-02-06, indexed by a hard-coded prefix so nothing past the 20260206 cap is read; the 2026-02 mbp table is not opened, so capacity is NaN after 2026-01-30), 1-min / 15-min / 1-h bars built from it, 1-s bsz/asz1-5 for capacity, ON-set daily P&L from out/onset. **To buy: nothing.**

Prereg `l2vast/ds3/prereg/MANCINI_prereg.md` sha256 `2dd627cd...` (logged in DECISIONS.md before any selection statistic; three development runs printed only n and the PRE+X' mean of A(6,15,1), A(3,30,3), B(1): -1.52 / -1.41 / -1.62). Selection `out/mancini/sel_selection.json` sha256 `e8b65af1...` logged before the recent look; ONE recent look at the carried cells, none for the other cells. dead_lookup before scoring: 0 hits for mancini / failed_breakdown / back-test / trendline / flush over the 1,382,271 stored specs, 0 of 40 sampled specs EXACT/NEAR; nearest stored work is ZONES_2 / POI_MAP / NTZ (levels as a FILTER, TARGET or STOP of the live books' signals), L2EB PDL/PDH and ZENL2 previous-day-extreme entries on other triggers; **new here:** a level REACTION traded as an entry on its own (flush-and-reclaim, break-and-retest), the swing / prior-day / overnight / midpoint set in one book, and the trendline (a named gap in the POI README). Capped 20260206, UNTOUCHED never read. Code `l2vast/ds3/code/mancini/`, out `l2vast/ds3/out/mancini/`, rows `out/recent_wins/mancini.csv`.

## Page 1

**Plain sentence.** The Mancini frame as stand-alone NQ books is a null: of 640 cells (failed breakdown A and back-test B over a 22,803-instance level set that includes the new simple ascending trendline TL, x tested-once, x level or fixed-60 target, x four level sets, x all-sessions or RTH-only) 9 were positive in both PRE and X' (chance expectation 8.0; family reality-check p 1.00, 0 Romano-Wolf survivors, back-test B: 2 of 64 cells positive in PRE, 0 in X') and in the one recent look they are mostly negative: 2 of 9 positive in L6M, 0 PASS, 0 CANDIDATE, literal TOLERANT 0, STRICT 1, NOW-ONLY 2; the best, TLONLY A F10 W5 h3 fix60, earns +2.49 pts per trade L6M (MDE 14.7, 63 trades, 2.2 a week; HOLD +1.43, PRE +1.63, X' +0.84) with M -0.46, LIVE-CAL +1.77, 1-s delay +4.83, its direction flipped (longs +7.2 / +10.1 in PRE / X' and -1.8 in L6M, shorts -5.0 / -13.9 and +7.6), random-level and shuffled-day placebo ranks 0.69 / 0.59, and +0.56k/wk L6M on the ON set at 5 contracts (MDE 3.0k); the trendline does carry the selection (7 of the 9 are TL-only, flush 10) but across all 160 TL-only cells the X' median is -3.1 and the PRE median -0.2.

Counts (per-contract gate AND 5-contract stack gate vs the ON set, TOLERANT = T-SIXTY addendum literal): of the 9 carried cells STRICT 1, TOLERANT 0, TOL-B (post-hoc) 0, TOL-nc (post-hoc) 0, NOW-ONLY 2; of all 640 cells 0 are TOLERANT by construction (non-carried cells have no recent statistic). Tiers: PASS 0, CANDIDATE 0, DEAD 9. STRICT is not a subset of TOLERANT: the one STRICT cell fails the PRE worst-20 clause (rule -749k vs stack -737k) and the 1-s vs 3-s delay check (+4.83 vs +2.49). Mean persistence score of the carried cells 0.36; every shrunk size 0.

### Table 1 - carried cells, per contract first (NQ, 1 contract, net pts per trade after 0.242 commission, N fills, 3-s decision delay; MDE = 2.8 x day-clustered SE; M = worst print of the delay second; LIVE_CAL = stop fill 2.45; MNQ = 0.89 pt round-turn fee, FEES.md; stack = +5 contracts added to the ON set, $k/wk)

| cell | n L6M | N L3M | L6M | HOLD | PRE | X' | MDE L6M | 1-s L6M | M L6M | LIVE-CAL L6M | MNQ L6M | tpw | stack L3M | L6M | HOLD | PRE | X' (MDE L6M) | 12R L6M / PRE | STRICT / TOL / NOW | tier | persist | size |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TLONLY A F10 W15 h1 lvl | 149 | -2.55 | -3.57 | -3.06 | +1.11 | +0.28 | 6.76 | -3.12 | -4.89 | -4.29 | -4.22 | 5.3 | -1.46 | -1.90 | -1.58 | +0.52 | +0.08 (3.15) | -0.58 / +0.15 | n/n/n | DEAD | 0.33 | 0.00 |
| TLONLY A F10 W15 h3 lvl | 85 | -0.41 | -2.04 | -1.85 | +1.31 | +0.15 | 8.57 | -2.35 | -3.17 | -2.68 | -2.68 | 3.0 | -0.13 | -0.62 | -0.57 | +0.38 | +0.02 (2.16) | +0.12 / +0.42 | n/n/n | DEAD | 0.33 | 0.00 |
| TLONLY A F10 W30 h3 fix60 | 89 | +5.70 | +0.40 | -0.27 | +2.75 | +1.96 | 11.65 | +2.30 | -1.29 | -0.34 | -0.24 | 3.2 | +1.95 | +0.13 | -0.09 | +0.82 | +0.36 (3.02) | +1.03 / +0.86 | n/n/Y | DEAD | 0.44 | 0.00 |
| TLONLY A F10 W30 h3 lvl | 92 | -2.38 | -2.31 | -1.82 | +1.10 | +1.17 | 8.29 | -2.07 | -3.25 | -2.95 | -2.95 | 3.3 | -0.83 | -0.76 | -0.61 | +0.34 | +0.22 (2.53) | +0.03 / +0.22 | n/n/n | DEAD | 0.33 | 0.00 |
| TLONLY A F10 W5 h1 fix60 | 119 | -2.33 | -1.39 | -1.97 | +1.56 | +1.54 | 8.94 | -0.60 | -2.77 | -2.21 | -2.04 | 4.2 | -1.05 | -0.59 | -0.82 | +0.58 | +0.30 (3.74) | -0.31 / +0.22 | n/n/n | DEAD | 0.33 | 0.00 |
| TLONLY A F10 W5 h1 lvl | 127 | -3.74 | -3.80 | -3.18 | +0.60 | +0.74 | 6.72 | -3.19 | -5.34 | -4.52 | -4.45 | 4.5 | -1.82 | -1.72 | -1.42 | +0.23 | +0.15 (2.72) | -0.90 / -0.29 | n/n/n | DEAD | 0.33 | 0.00 |
| MAJOR A F10 W5 h1 fix60 once | 284 | +0.37 | -1.48 | -0.52 | +0.09 | +0.23 | 6.37 | -0.58 | -2.09 | -2.31 | -2.13 | 10.1 | +0.39 | -1.50 | -0.52 | +0.09 | +0.12 (5.96) | +0.23 / +0.29 | n/n/n | DEAD | 0.34 | 0.00 |
| TLONLY A F10 W5 h3 fix60 | 63 | +7.22 | +2.49 | +1.43 | +1.63 | +0.84 | 14.69 | +4.83 | -0.46 | +1.77 | +1.85 | 2.2 | +1.81 | +0.56 | +0.34 | +0.36 | +0.10 (3.02) | +0.90 / +0.55 | Y/n/Y | DEAD | 0.41 | 0.00 |
| MAJOR A F10 W5 h3 fix60 once | 148 | +3.27 | -1.33 | +0.16 | +1.19 | +0.90 | 9.58 | +0.22 | -1.51 | -2.12 | -1.98 | 5.3 | +1.68 | -0.70 | +0.09 | +0.60 | +0.33 (4.42) | -0.54 / +0.12 | n/n/n | DEAD | 0.39 | 0.00 |

Cell labels: level set (TL = the triggering level is a trendline; MAJOR = every level except 15-min swings), setup A failed breakdown with flush F pts / reclaim W min / hold h 1-min closes, target (fix60 or the next level >= 20 pts away), 'once' = the level was touched exactly once before, 'RTH' = RTH-only variant (none carried). Full names in `out/mancini/final.pkl`. The 2026 view (15 trades or fewer per cell) is in the CSV only. Every row is post-hoc selected on PRE and X' and then looked at once.

### Table 2 - validity layer (carried cells; L6M, N, 3 s)

| cell | placebo random-level rank (mean / p95) | shuffled-day rank (mean / p95) | RW p | DSR | PBO (group) | CV folds + (fold means) | PRE+X' mean of the cell / its one-step neighbours | quarters + | roll-3m + | NW t (wk) | CI wk-block L6M | halves of L6M | win % | top-5% share | breakeven stop cost | capacity (contracts; median / p10 depth) | corr w stack |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TLONLY A F10 W15 h1 lvl | 0.24 (-1.75 / +2.46) | 0.27 (-1.73 / +2.85) | 0.99 | 0.000 | 0.58 | 2/5 [-0.97, -4.0, 2.24, 2.1, -3.06] | +0.89 / +0.06 | 4/12 | 14/33 | -1.75 | [-8.0,+0.3] | -6.12(n76) / -0.92(n73) | 38 | n/a | -4.57 | 4.8; 19 / 11 | +0.07 |
| TLONLY A F10 W15 h3 lvl | 0.55 (-2.23 / +3.04) | 0.39 (-0.61 / +7.51) | 0.99 | 0.001 | 0.58 | 3/5 [-3.45, 0.73, 1.02, 1.9, -1.85] | +1.04 / +0.29 | 8/12 | 17/33 | -0.86 | [-7.3,+2.9] | -4.55(n43) / +0.53(n42) | 42 | n/a | -2.40 | 4.8; 19 / 10 | -0.16 |
| TLONLY A F10 W30 h3 fix60 | 0.69 (-1.63 / +5.72) | 0.49 (+0.54 / +10.28) | 0.92 | 0.015 | 0.58 | 3/5 [-0.56, 1.11, 0.02, 4.06, -0.27] | +2.53 / +0.77 | 8/12 | 19/33 | +0.11 | [-6.2,+7.0] | -5.78(n45) / +6.72(n44) | 31 | 8.30 | +1.91 | 5.0; 20 / 10 | +0.04 |
| TLONLY A F10 W30 h3 lvl | 0.52 (-2.48 / +2.70) | 0.38 (-1.00 / +6.25) | 0.99 | 0.001 | 0.58 | 3/5 [-1.97, 1.98, 0.84, 1.13, -1.82] | +1.12 / +0.12 | 6/12 | 17/33 | -0.91 | [-7.6,+2.9] | -2.78(n47) / -1.82(n45) | 41 | n/a | -2.88 | 5.0; 20 / 10 | -0.04 |
| TLONLY A F10 W5 h1 fix60 | 0.53 (-1.61 / +4.10) | 0.53 (-1.37 / +6.64) | 0.99 | 0.004 | 0.58 | 2/5 [-4.53, -1.48, 2.02, 2.95, -1.97] | +1.56 / +0.65 | 6/12 | 16/33 | -0.56 | [-7.4,+5.3] | -2.06(n60) / -0.71(n59) | 29 | n/a | -0.71 | 4.8; 19 / 10 | +0.17 |
| TLONLY A F10 W5 h1 lvl | 0.19 (-1.45 / +2.83) | 0.27 (-1.52 / +4.28) | 0.99 | 0.000 | 0.58 | 2/5 [-1.82, -2.23, 0.53, 1.87, -3.18] | +0.63 / -0.04 | 6/12 | 16/33 | -2.07 | [-8.2,+0.2] | -5.45(n64) / -2.12(n63) | 37 | n/a | -4.82 | 4.9; 20 / 11 | +0.17 |
| MAJOR A F10 W5 h1 fix60 once | 0.69 (-2.45 / +0.89) | 0.57 (-2.04 / +2.88) | 0.99 | 0.001 | 0.58 | 3/5 [0.66, 0.38, 1.75, -0.96, -0.92] | +0.13 / -0.28 | 6/12 | 17/33 | -0.63 | [-5.8,+2.7] | -3.49(n144) / +0.58(n140) | 29 | n/a | -0.81 | 5.0; 20 / 11 | +0.05 |
| TLONLY A F10 W5 h3 fix60 | 0.69 (+0.26 / +8.48) | 0.59 (+1.18 / +14.01) | 0.81 | 0.033 | 0.58 | 3/5 [-2.74, 2.69, -3.15, 3.35, 1.43] | +1.44 / +0.98 | 8/12 | 19/33 | +0.51 | [-7.2,+11.8] | -6.66(n32) / +11.94(n31) | 35 | 1.52 | +5.31 | 5.0; 20 / 10 | +0.12 |
| MAJOR A F10 W5 h3 fix60 once | 0.76 (-3.24 / +1.48) | 0.52 (-1.32 / +6.72) | 0.99 | 0.004 | 0.58 | 2/5 [-0.81, -0.06, 0.69, 2.16, -0.24] | +1.10 / -0.41 | 8/12 | 21/33 | -0.44 | [-7.0,+4.9] | -6.55(n75) / +4.04(n73) | 31 | n/a | -0.69 | 5.2; 21 / 11 | -0.01 |

Program level over the carried cells (L6M, 9 daily series): group reality-check p 0.83, PBO 0.58, cumulative cells used for the Sidak line 3.1M. Purged 5-fold CV with 1-day embargo, cell chosen on four training folds among ALL 640 by mean N pts per trade, scored on the held-out fold: pooled out-of-sample -3.87 pts per trade over 196 trades (this CV runs on every day of every cell, as the INST-A CV did, and reports only the chosen cell's fold result; it is the one place a non-carried cell's recent days enter, as an aggregate; fold choices: f0 train +2.7 -> test -6.9 (n 19); f1 train +2.2 -> test -5.1 (n 41); f2 train +1.6 -> test -3.2 (n 56); f3 train +1.8 -> test +0.4 (n 36); f4 train +2.5 -> test -5.9 (n 44)). Family test on the SELECTION windows (all 614 cells with >= 100 PRE+X' trades): White RC p 1.00, Romano-Wolf survivors 0, best-cell DSR 7.3e-10, PBO 0.14, minimum backtest length 9.8 y at SR 1.

### Table 3 - the 640 cells in the SELECTION windows only (medians of the per-trade mean, N, 3 s; PRE 2024-02..2025-06, X' 2023-04..2024-01; no recent statistic of a non-carried cell exists)

| factor | level | cells | median PRE | median X' | cells positive PRE | positive X' | carried |
|---|---|---|---|---|---|---|---|
| setup | A | 576 | -1.58 | -1.18 | 81 | 62 | 9 |
| setup | B | 64 | -1.62 | -1.68 | 2 | 0 | 0 |
| level set | ALL | 160 | -1.76 | -1.03 | 0 | 17 | 0 |
| level set | MAJOR | 160 | -1.33 | -1.16 | 13 | 8 | 2 |
| level set | NOTL | 160 | -1.92 | -0.99 | 0 | 25 | 0 |
| level set | TLONLY | 160 | -0.23 | -3.06 | 70 | 12 | 7 |
| RTH-only | 0 | 320 | -1.42 | -1.23 | 63 | 30 | 9 |
| RTH-only | 1 | 320 | -1.80 | -1.23 | 20 | 32 | 0 |
| tested once | 0 | 320 | -1.54 | -1.20 | 33 | 13 | 7 |
| tested once | 1 | 320 | -1.74 | -1.29 | 50 | 49 | 2 |
| target | fix60 | 320 | -1.48 | -1.26 | 54 | 44 | 5 |
| target | lvl | 320 | -1.67 | -1.20 | 29 | 18 | 4 |
| flush pts | 0 | 64 | -1.62 | -1.68 | 2 | 0 | 0 |
| flush pts | 3 | 192 | -1.52 | -1.41 | 17 | 1 | 0 |
| flush pts | 6 | 192 | -1.57 | -1.03 | 27 | 18 | 0 |
| flush pts | 10 | 192 | -1.64 | -0.92 | 37 | 43 | 9 |
| reclaim min | 0 | 64 | -1.62 | -1.68 | 2 | 0 | 0 |
| reclaim min | 5 | 192 | -1.64 | -1.21 | 24 | 21 | 5 |
| reclaim min | 15 | 192 | -1.56 | -1.21 | 30 | 15 | 2 |
| reclaim min | 30 | 192 | -1.57 | -1.01 | 27 | 26 | 2 |
| hold bars | 1 | 320 | -1.68 | -1.35 | 41 | 32 | 4 |
| hold bars | 3 | 320 | -1.48 | -1.07 | 42 | 30 | 5 |

Reading. (1) The level sets ALL (trendline included) and NOTL lose in PRE and X' on the median (-1.0 to -1.9 pts per trade; costs alone are 1.28 stop slip on the 60-80% of trades that stop out plus 0.24 commission plus the entry tick); not one of their 320 cells is positive in PRE; MAJOR (no 15-min swings) has 13 positive in PRE and 8 in X'. (2) TL-only is the only level set whose cells are sometimes positive (70 of 160 in PRE, 12 in X'), the median PRE is -0.2 and the median X' -3.1: the TL result is not stable between the two selection windows, and 7 of 9 carried cells are TL-only flush-10 cells with 164-354 PRE and 52-124 X' trades per cell. (3) Back-test B loses everywhere (2 of 64 positive in PRE, 0 in X'). (4) Larger flush and longer hold are less negative; the RTH-only variant is not better (20 of 320 positive in PRE, 32 in X'). (5) The best cell's shuffled-day placebo (the same mechanical rule on another day's levels) averages +1.18 pts per trade in L6M with a 95th percentile of +14.0: the level content is not what pays. (6) Expected number of cells positive in both windows by chance, if the two signs were independent, is 8.0; 9 were carried.

### Table 4 - sessions of the carried cells (per trade, N, 3 s; entry session; n in brackets; L6M | PRE | X')

| cell | asia | london | pre | nyam | nypm | close |
|---|---|---|---|---|---|---|
| TLONLY A F10 W15 h1 lvl | -10.21 (14) / +9.61 / -9.11 | -4.79 (35) / +0.05 / +5.96 | -2.55 (12) / +0.99 / +6.31 | -3.00 (66) / -0.00 / -3.19 | +0.20 (12) / +1.88 / -1.73 | +0.42 (10) / -1.92 / +10.14 |
| TLONLY A F10 W15 h3 lvl | -7.46 (9) / +10.16 / -14.60 | -3.58 (25) / +1.47 / +4.94 | -6.31 (10) / +5.05 / +7.94 | +1.60 (28) / -4.79 / -3.53 | +3.86 (9) / +2.10 / +1.68 | -8.19 (4) / +4.03 / +2.27 |
| TLONLY A F10 W30 h3 fix60 | -16.42 (10) / +5.69 / -16.64 | +0.40 (30) / +4.89 / +2.52 | -6.71 (9) / +6.61 / +11.11 | +5.04 (27) / -1.42 / -1.90 | +14.16 (9) / +0.26 / +0.50 | -3.68 (4) / +3.06 / +11.12 |
| TLONLY A F10 W30 h3 lvl | -9.65 (11) / +10.06 / -16.64 | -1.23 (30) / +0.29 / +3.62 | -7.36 (10) / +5.35 / +7.94 | +0.19 (27) / -4.03 / +1.11 | +3.86 (9) / -1.52 / -1.35 | -7.05 (5) / +4.70 / +3.32 |
| TLONLY A F10 W5 h1 fix60 | -12.30 (8) / +11.48 / -23.61 | -8.80 (25) / +3.98 / +9.74 | -4.04 (9) / -1.61 / +1.24 | +0.55 (59) / +1.81 / -3.50 | +8.30 (9) / -5.42 / +4.38 | +9.14 (9) / -0.05 / +23.30 |
| TLONLY A F10 W5 h1 lvl | -12.49 (9) / +8.41 / -23.61 | -10.17 (25) / +0.68 / +11.21 | -1.21 (9) / -0.96 / +3.97 | -1.88 (65) / +0.18 / -3.41 | +2.60 (9) / -1.72 / +3.36 | -0.55 (10) / +1.18 / +15.25 |
| MAJOR A F10 W5 h1 fix60 once | -8.57 (22) / -1.55 / +20.62 | +11.52 (32) / +12.14 / +10.58 | +15.02 (9) / -10.56 / -16.56 | -2.11 (172) / +0.44 / -0.25 | -8.07 (34) / -1.78 / -0.36 | -6.55 (15) / +0.32 / +7.47 |
| TLONLY A F10 W5 h3 fix60 | -3.51 (4) / +9.54 / -28.27 | -11.50 (18) / +5.50 / -16.77 | -10.98 (6) / +7.26 / +10.24 | +12.19 (27) / -3.21 / -12.28 | +20.83 (6) / -1.86 / +9.59 | -4.99 (2) / +2.85 / +26.28 |
| MAJOR A F10 W5 h3 fix60 once | -4.42 (19) / +5.39 / +18.37 | +14.35 (21) / +7.71 / +3.15 | -13.87 (5) / -6.67 / -8.01 | -0.55 (80) / +1.03 / +0.28 | -11.66 (15) / -4.98 / +4.31 | -15.73 (8) / +11.24 / -0.68 |

(each session cell: L6M (n) / PRE / X'.) Long / short split of the carried cells, per trade L6M | PRE | X': TLONLY A F10 W15 h1 lvl: L -6.35|+2.01|+2.69 S -0.76|-0.07|-2.64; TLONLY A F10 W15 h3 lvl: L -6.14|+6.04|+2.48 S +2.37|-3.51|-2.98; TLONLY A F10 W30 h3 fix60: L -1.79|+7.59|+6.48 S +2.55|-1.89|-3.54; TLONLY A F10 W30 h3 lvl: L -4.24|+5.04|+1.18 S -0.37|-2.83|+1.15; TLONLY A F10 W5 h1 fix60: L -4.89|+4.70|+6.85 S +2.17|-2.58|-6.35; TLONLY A F10 W5 h1 lvl: L -5.18|+2.25|+2.89 S -2.34|-1.64|-2.34; MAJOR A F10 W5 h1 fix60 once: L -5.47|+1.79|+2.39 S +2.62|-1.99|-2.03; TLONLY A F10 W5 h3 fix60: L -1.82|+7.19|+10.06 S +7.55|-4.96|-13.90; MAJOR A F10 W5 h3 fix60 once: L -6.29|+3.15|+5.24 S +4.20|-1.32|-4.02.

### Table 5 - stack effect: the standalone book as an ADDITIONAL book on the ON set (oneconv engine daily P&L, $k/wk delta, paired-weekly MDE in brackets; PRE worst-20 weeks of the combined line vs the ON set alone)

| cell | 1 ctr no lock L6M | PRE | 5 ctr no lock L3M | L6M | HOLD | PRE | X' | 5 ctr 12R lock L6M | PRE | worst-20 PRE rule / ON set (no lock) | worst-20 PRE rule / ON set (12R) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| TLONLY A F10 W15 h1 lvl | -0.38 (0.63) | +0.10 | -1.46 (4.40) | -1.90 (3.15) | -1.58 (2.84) | +0.52 (2.01) | +0.08 (1.92) | -0.58 (2.71) | +0.15 (1.52) | -743 / -737 | -624 / -589 |
| TLONLY A F10 W15 h3 lvl | -0.12 (0.43) | +0.08 | -0.13 (3.13) | -0.62 (2.16) | -0.57 (2.02) | +0.38 (1.58) | +0.02 (1.57) | +0.12 (1.90) | +0.42 (1.28) | -748 / -737 | -631 / -589 |
| TLONLY A F10 W30 h3 fix60 | +0.03 (0.60) | +0.16 | +1.95 (4.22) | +0.13 (3.02) | -0.09 (2.98) | +0.82 (2.00) | +0.36 (2.62) | +1.03 (2.65) | +0.86 (1.73) | -754 / -737 | -629 / -589 |
| TLONLY A F10 W30 h3 lvl | -0.15 (0.51) | +0.07 | -0.83 (3.83) | -0.76 (2.53) | -0.61 (2.44) | +0.34 (1.54) | +0.22 (1.70) | +0.03 (2.26) | +0.22 (1.38) | -751 / -737 | -632 / -589 |
| TLONLY A F10 W5 h1 fix60 | -0.12 (0.75) | +0.12 | -1.05 (4.86) | -0.59 (3.74) | -0.82 (3.46) | +0.58 (2.19) | +0.30 (2.53) | -0.31 (2.90) | +0.22 (1.79) | -754 / -737 | -629 / -589 |
| TLONLY A F10 W5 h1 lvl | -0.34 (0.54) | +0.05 | -1.82 (3.94) | -1.72 (2.72) | -1.42 (2.48) | +0.23 (1.87) | +0.15 (1.47) | -0.90 (2.42) | -0.29 (1.45) | -730 / -737 | -628 / -589 |
| MAJOR A F10 W5 h1 fix60 once | -0.30 (1.19) | +0.02 | +0.39 (8.28) | -1.50 (5.96) | -0.52 (6.01) | +0.09 (4.09) | +0.12 (4.44) | +0.23 (4.66) | +0.29 (3.41) | -801 / -737 | -623 / -589 |
| TLONLY A F10 W5 h3 fix60 | +0.11 (0.60) | +0.07 | +1.81 (5.04) | +0.56 (3.02) | +0.34 (2.75) | +0.36 (1.81) | +0.10 (1.98) | +0.90 (2.46) | +0.55 (1.56) | -749 / -737 | -625 / -589 |
| MAJOR A F10 W5 h3 fix60 once | -0.14 (0.88) | +0.12 | +1.68 (6.16) | -0.70 (4.42) | +0.09 (4.11) | +0.60 (2.86) | +0.33 (2.93) | -0.54 (2.92) | +0.12 (2.54) | -735 / -737 | -633 / -589 |

ON set = DS3_ON_SET 'ON, K6 split, parity stop, slip +0.25' (out/onset: `ON|s0.25|k670|par|off`, and `...|12R_m1.0` for the combined-lock line). The 12R line removes standalone trades entered after the engine's lock-fire second in the same ISO week (fire times from the engine's own fire list); the standalone book has no lock of its own and trades a fixed 1 (or 5) contract, so the running-max sizing of the engine books does not act on it. Capacity is about 5 NQ contracts (25% of median top-5 depth 19-21 on the lifted side, p10 10-11): the 5-contract line is already at the limit.

## Method notes, gates and what is open

* Level set (all causal, +-3 pt zones, back-adjusted frame so no roll gaps): 15-min fractal swing H/L (4 bars each side, life 2 days), 1-h fractal H/L (3 each side, life 5 days), daily H/L of each of the last 5 completed label days, prior-RTH-day H/L, overnight H/L (from 09:30), midpoints (prior RTH, overnight, 5-day range), and TL = the line through the last two 15-min swing lows (ascending only, slope <= 0.01 pt/s, replaced when the next swing low confirms, <= 8 h). 22,803 instances, about 54 active at 10:00 ET (one per ~4.6 pts of a 250-pt day: dense, which is why the random-level placebo matters). 'Tested once' = exactly one earlier touch episode. Roles resolve from geometry (a flush below a level that price came from above = support).
* A: flush >= F below, reclaim (a close back above) within W minutes of the flush bar, hold h consecutive 1-min closes; long at the hold close, stop = flush low - 2, mirror short. B: close >= R + 3, pull back to within 3 pts inside 60 min, hold h closes, stop = pullback low - 2. Target the next other level >= 20 pts away (zone edge, <= 150 pts) else fixed 60, or fixed 60. Risk 3..40 pts, one position per cell, 6-h cap, flat 16:55 ET (15:55 RTH-only).
* Fills as INST-A: decision second = hold-bar close + 3 s (1 s beside); N: last print +1 tick; M: worst print of the second +1 tick and target needs a tick through; stop cost 1.28 (N, M), 2.45 (LIVE_CAL); 0.242 pt commission; MNQ column uses 0.89 pt per round turn (FEES.md $1.78 on $2 per point).
* Selection: mean > 0 in PRE and in X' (N, 3 s), n_PRE >= 40 and n_X' >= 30: 9 of 640. Gates and tiers as in the prereg (PASS needs TOLERANT, both placebo ranks >= 0.95, RW p <= 0.05 or group RC p < 0.10, delay within 20%, >= 3 of 5 CV folds); gates are computed on the 5-contract stack line (as INST-A), per-contract positivity in L3M and L6M also required for TOLERANT / NOW-ONLY. TOL-B (clause 5 loosened to PRE > -1.0 x L6M) and TOL-nc (clause 5 dropped) are shown beside the literal TOLERANT, post-hoc; headline = literal TOLERANT.
* Placebos: 500 draws each on L6M days (N, 3 s): random-level (every level instance, TL included, shifted by U(-40, +40) pts; fire counts stay within ~10% of the real counts, e.g. 135 vs 149) and shuffled-day (the level set of another label day of the same calendar year at the same clock time, prices re-based by the open difference). Rank = share of draws below the real value.
* Disclosed: (a) the full is_dead() run over all 640 specs was not done (a sampled 40 + the vocabulary search, as INST-5 did; the full run costs ~0.35 s per spec after a 40-s load and the spec grammar is new); (b) the 12R stack line is an approximation (standalone trades after the engine's fire second are dropped, the engine is not re-run with the extra book inside its MTM lock); (c) the CV uses all days of all cells but reports only the chosen cell; (d) capacity excludes 2026-02; (e) cumulative-trial count for the Sidak line is approximate (3.1M; qv.trials_total() raised on a None field); (f) trades per week are small (2-10), so every per-contract MDE is 6-15 pts.
* Structural questions (MORNING.md): none blocking. Interpretations made: 'hold 1 / 3 bars' = 1-min bars; the fractal orders (15-min 4, 1-h 3) and the lives (2 / 5 days) are mine, chosen so ~54 levels are active; TL = last two 15-min swing lows with the same fractal order.
* Nothing promoted. Dead cells: DEAD_CELLS +640 rows appended (append_cells; file not rebuilt).
