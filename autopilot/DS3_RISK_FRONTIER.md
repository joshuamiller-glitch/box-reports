# DS3_RISK_FRONTIER: one risk-dial frontier (PE weight x net-lot cap x re-entry pause x loss gate) on the real engine (DIS-BA)

Author ZL-2, 2026-11-04. Scope note l2vast/ds3/prereg/DISBA_scope.md sha256 b42669863139967cbd0bcd18504da73feb0428959bbc6d30f3e818660caac618 (DECISIONS.md, before any outcome). **A table for the user to read a risk appetite from; NO recommendation; no PASS claims; nothing live.** All cells are in-sample on 2023-26 (a single path of the engine each). CSV for plotting (all 92 cells, every metric, frontier flag): l2vast/ds3/out/dis_ba/DS3_RISK_FRONTIER.csv. Code l2vast/ds3/code/dis_x/rf_lib.py, rf_an.py.

## Plain sentence
Across the 90 TH-on cells, the dials trade mean against drawdown roughly one for one at a price of about $90-$150 of weekly mean per $1,000 of maxDD removed for the PE-weight and 1R-gate cells on the frontier and $390-$1,440 for the cap-only cells at live weights (the full-period mean ranges $9.5k to $17.7k per week and the worst-of maxDD over HOLD, PRE and 2026 ranges $58k to $131k; the live cell is $17.7k and $122k), the frontier is built only from the PE lot weight (0.75 or 0.5), the net-lot cap (8-14) and the 1R loss gate, the re-entry pause (15 or 30 minutes) is on no frontier cell (it lowers the mean by $1.0k or $2.0k per week and lowers the 2026 drawdown but not the worst-of drawdown), the smallest steps are the net-lot cap 14 or 12 at the live weights (mean -$0.4k and -$1.0k per week for only $0.3k and $2.6k of worst-of maxDD, i.e. dear per $1k removed, but they cut the synthetic tail from $522k to $464k and $435k) and the largest reduction (worst-of maxDD $58k, mean $11.3k, 2026 maxDD $33k, synthetic tail $319k) costs 36% of the live mean, every frontier cell is significantly below the live mean in paired weekly differences, the live cell is not dominated by any of the 91 other cells but is dominating only 16 of them, and the TH-off reference rows are $2.0k to $3.3k per week lower with a maxDD of $160k to $175k.

## 0. Method, hooks, tie-out
Engine V13T ts2 full stack, Q1-A ladder, locks re-run in every cell, corrected carrying weeks (windows by book_harness.CAR; the period statistics drop them), live cost frame; the live cell reproduces $2,520,149.07. Dials and hooks (existing only): PE lot weight folded into the ER-multiplier slot (DIS-AH convention: lots = round(lots after A06/B02 x ER multiplier x weight), PE rows only; lock governor keeps the ER multiplier alone; integer lots with min 1, so weight 0.75 changes few PE lots: 7 lots x 0.5 = 4 or 3.5->4, x 0.75 = 5); net-lot cap via stack_expo._pass/_state (the run_stack hook has no entry for a weighted base, so its fixed-point loop is re-implemented; the cap-8 cell reproduces DS3_EXPOSURE_CAP: $1,975k, peak net 11, and cap 8 / 10 / 12 / 14 totals agree); re-entry pause after a cut via extra_skip emulation (as in DS3_SLOT_CHANNEL; mask from the previous pass's cut trades); loss gate via OC.CFG['spec'] pb_loss; profit gate 5R live. Convergence: 31 of 92 cells did not reach the fixed point within 6 passes (30 of the 30-minute-pause cells and 1 of the 15-minute cells: the cap and pause masks oscillate); their reported values are the last iterate; the pause cells are therefore approximate. Columns: mean = full-period (148 non-carrying weeks) $k/week; maxDD = weekly-cumulative; worst-of = max(HOLD, PRE, 2026 maxDD); worst day and worst week over all days; synthetic tail = peak net lots x 1,449 pts x $20 (DS3_EXPOSURE_CAP method; 18 lots = $522k; the 70/30 position counted at full size); weeks under water = share of the 148 weeks below the running peak. Dead_lookup: DS3_BOOK_WEIGHTS (PE x0.5 -33% HOLD maxDD at -23% mean, rolling-origin fails), DS3_EXPOSURE_CAP (caps; rolling-origin: caps are the only rules with a constant sign out of sample), DS3_GATES (gate 1R vs 2R; pauses).

## 1. Live point and the Pareto frontier (full-period mean vs worst-of maxDD, TH on)
| cell | mean $k/wk | worst-of maxDD $k (HOLD/PRE/2026) | maxDD removed vs live $k | mean lost $k/wk | $ of weekly mean lost per $1k maxDD removed | 2026 mean / maxDD | HOLD dd | PRE dd | 2026 dd | worst day | worst week | synth. tail $k | weeks under water | peak net |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| w0.50 cap8 pause0 gate1R | 11.3 | 58.3 | 63.7 | 6.47 | 101 | 22.4 / 32.5 | 52.9 | 58.3 | 32.5 | -27.1 | -39.9 | 319 | 0.46 | 11 |
| w0.75 cap8 pause0 gate1R | 11.5 | 63.6 | 58.4 | 6.20 | 106 | 22.2 / 35.1 | 63.6 | 51.9 | 35.1 | -29.4 | -36.5 | 319 | 0.50 | 11 |
| w0.50 cap10 pause0 gate1R | 12.1 | 65.0 | 57.0 | 5.59 | 98 | 24.3 / 36.3 | 65.0 | 61.1 | 36.3 | -27.1 | -42.4 | 348 | 0.45 | 12 |
| w0.50 cap12 pause0 gate1R | 12.6 | 66.6 | 55.4 | 5.11 | 92 | 25.1 / 36.3 | 66.6 | 62.4 | 36.3 | -27.1 | -44.5 | 406 | 0.45 | 14 |
| w0.50 cap- pause0 gate1R | 12.9 | 67.5 | 54.5 | 4.78 | 88 | 25.7 / 36.3 | 67.5 | 63.0 | 36.3 | -27.1 | -44.0 | 435 | 0.45 | 15 |
| w0.75 cap12 pause0 gate1R | 13.1 | 77.8 | 44.2 | 4.61 | 104 | 25.2 / 39.3 | 77.8 | 60.7 | 39.3 | -29.8 | -41.2 | 406 | 0.47 | 14 |
| w0.75 cap- pause0 gate1R | 13.5 | 78.1 | 43.9 | 4.18 | 95 | 25.6 / 39.3 | 78.1 | 62.9 | 39.3 | -29.8 | -41.2 | 464 | 0.46 | 16 |
| w0.75 cap10 pause0 gate2R | 13.6 | 95.1 | 26.9 | 4.13 | 154 | 27.2 / 45.4 | 95.1 | 63.2 | 45.4 | -34.7 | -49.7 | 377 | 0.49 | 13 |
| w0.75 cap12 pause0 gate2R | 14.2 | 98.1 | 23.9 | 3.47 | 145 | 28.7 / 46.6 | 98.1 | 65.9 | 46.6 | -34.7 | -51.5 | 406 | 0.46 | 14 |
| w0.75 cap- pause0 gate2R | 14.6 | 98.4 | 23.6 | 3.07 | 130 | 29.3 / 46.6 | 98.4 | 65.3 | 46.6 | -34.7 | -51.5 | 464 | 0.45 | 16 |
| w1.00 cap10 pause0 gate2R | 15.5 | 117.6 | 4.4 | 2.23 | 507 | 30.0 / 53.5 | 117.6 | 65.8 | 53.5 | -35.2 | -62.1 | 377 | 0.49 | 13 |
| w1.00 cap12 pause0 gate2R | 16.7 | 119.4 | 2.6 | 1.02 | 386 | 32.9 / 61.3 | 119.4 | 72.1 | 61.3 | -37.1 | -61.3 | 435 | 0.45 | 15 |
| w1.00 cap14 pause0 gate2R | 17.3 | 121.7 | 0.3 | 0.42 | 1441 | 34.7 / 62.6 | 121.7 | 74.8 | 62.6 | -38.1 | -62.6 | 464 | 0.43 | 16 |
| w1.00 cap- pause0 gate2R (LIVE) | 17.7 | 122.0 | 0.0 | -0.00 | - | 35.3 / 62.6 | 122.0 | 75.1 | 62.6 | -38.1 | -62.6 | 522 | 0.44 | 18 |
"$ of weekly mean lost per $1k maxDD removed" is relative to the live cell. The frontier is the set of cells with no other cell that has a higher mean and a lower-or-equal worst-of maxDD (all 92 cells compared, TH-off rows included).

## 2. Other cells of interest (not on the frontier)
| cell | mean $k/wk | maxDD | Calmar | 2026 mean | 2026 maxDD | HOLD dd | PRE dd | L6M dd | X' dd | worst-of dd | worst day | worst week | synth. tail | weeks under water | peak net lots |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| w1.00 cap8 pause0 gate2R | 13.9 | 70.9 | 0.20 | 28.0 | 44.9 | 101.9 | 65.6 | 44.9 | 40.8 | 101.9 | -34.6 | -56.1 | 319 | 0.49 | 11 |
| w0.50 cap- pause0 gate2R | 13.0 | 61.3 | 0.21 | 26.1 | 41.8 | 82.4 | 61.3 | 41.8 | 34.8 | 82.4 | -32.2 | -45.1 | 435 | 0.45 | 15 |
| w0.50 cap8 pause0 gate2R | 11.3 | 61.1 | 0.18 | 22.0 | 35.9 | 75.2 | 55.7 | 35.9 | 31.8 | 75.2 | -30.9 | -42.6 | 319 | 0.47 | 11 |
| w1.00 cap- pause0 gate1R | 15.6 | 84.0 | 0.19 | 29.0 | 39.0 | 127.2 | 84.0 | 39.0 | 52.8 | 127.2 | -30.2 | -54.0 | 522 | 0.47 | 18 |
| w1.00 cap- pause15 gate2R | 16.2 | 83.5 | 0.19 | 33.1 | 60.1 | 124.7 | 80.1 | 60.1 | 50.0 | 124.7 | -38.1 | -62.2 | 522 | 0.47 | 18 |
| w1.00 cap- pause30 gate2R | 14.9 | 85.5 | 0.17 | 28.3 | 38.4 | 128.2 | 85.5 | 38.4 | 48.7 | 128.2 | -38.7 | -60.7 | 522 | 0.47 | 18 |
| w1.00 cap- pause30 gate1R | 13.6 | 88.8 | 0.15 | 25.8 | 30.6 | 112.0 | 88.8 | 30.6 | 52.1 | 112.0 | -29.7 | -55.3 | 522 | 0.49 | 18 |
| w0.50 cap- pause30 gate1R | 10.6 | 58.0 | 0.18 | 21.6 | 22.8 | 62.4 | 47.8 | 21.3 | 33.5 | 62.4 | -27.2 | -41.5 | 435 | 0.48 | 15 |
| w0.50 cap8 pause30 gate1R | 9.5 | 59.9 | 0.16 | 18.6 | 26.7 | 62.1 | 41.0 | 26.7 | 31.4 | 62.1 | -27.2 | -43.1 | 319 | 0.45 | 11 |
The 30-minute pause cells deliver the lowest 2026 maxDDs (w0.50 pause30 gate1R: 22.8k, mean 10.6k; w1.00 pause30 gate1R: 30.6k, mean 13.6k) but their HOLD maxDDs stay at $112k-$128k at live weights, which is why they are off the worst-of frontier.

## 3. TH-off reference rows
| cell | mean $k/wk | maxDD | Calmar | 2026 mean | 2026 maxDD | HOLD dd | PRE dd | L6M dd | X' dd | worst-of dd | worst day | worst week | synth. tail | weeks under water | peak net lots |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TH-OFF w1.00 cap- pause0 gate2R | 15.7 | 174.6 | 0.09 | 21.7 | 91.4 | 91.4 | 174.6 | 90.5 | 81.1 | 174.6 | -52.3 | -104.5 | 522 | 0.55 | 18 |
| TH-OFF w1.00 cap- pause0 gate1R | 14.4 | 159.9 | 0.09 | 18.8 | 74.0 | 110.2 | 159.9 | 50.2 | 93.8 | 159.9 | -34.1 | -64.1 | 522 | 0.55 | 18 |

## 4. Dial marginals (mean of the 90 TH-on cells at each level of one dial; the dials interact, read with the grid)
PE weight 1.0 / 0.75 / 0.5: mean $14.1k / $12.4k / $11.5k, worst-of maxDD $118k / $91k / $74k, 2026 maxDD $45k / $37k / $34k, synthetic tail $423k / $404k / $388k. Cap none / 14 / 12 / 10 / 8: mean $13.5k / $13.3k / $13.0k / $12.3k / $11.3k, worst-of maxDD $97k / $97k / $97k / $95k / $85k, synthetic tail $473k / $454k / $415k / $364k / $319k. Pause none / 15 / 30: mean $13.7k / $12.7k / $11.7k, worst-of maxDD $91k / $97k / $95k, 2026 maxDD $43k / $43k / $31k. Loss gate 2R / 1R: mean $13.1k / $12.2k, worst-of maxDD $101k / $87k, 2026 maxDD $42k / $36k.
Reading: the PE weight is the dial with the largest drawdown effect per dollar; the cap is the only dial that cuts the synthetic tail by itself; the pause moves the 2026 drawdown but not the worst-of drawdown; the 1R gate removes about $14k of the worst-of drawdown for about $0.9k per week on average.

## 5. Selection caution: rolling-origin and paired bootstrap
(i) The five frontier cells with the lowest mean cost per $1k removed (all w0.50 or w0.75 with the 1R gate): year-by-year deltas vs live, mean $k/wk / maxDD $k:
| cell | 2024 | 2025 | 2026 |
|---|---|---|---|
| w0.50 cap- pause0 gate1R | -3.3 / -12 | -5.1 / -17 | -9.6 / -26 |
| w0.50 cap12 pause0 gate1R | -3.6 / -13 | -5.4 / -17 | -10.3 / -26 |
| w0.75 cap- pause0 gate1R | -2.8 / -12 | -3.7 / -9 | -9.7 / -23 |
| w0.50 cap10 pause0 gate1R | -3.9 / -14 | -6.1 / -17 | -11.0 / -26 |
| w0.50 cap8 pause0 gate1R | -4.2 / -17 | -7.1 / -13 | -13.0 / -30 |
In each year the drawdown is lower and the mean is lower: the sign of the trade is constant, the mean cost is largest in 2026 (the high-return year).
(ii) Frontier re-derived on the training window 2023-04..2024-12, the five lowest-cost cells and their test results (2025-01..2026-10) vs live: w0.75 cap- gate2R: train mean -1.04k, maxDD -16k; TEST mean -3.20k, maxDD -24k (live test maxDD 122k); w0.75 cap14 gate2R: train -1.12k / -16k; TEST -3.36k / -24k; w0.75 cap8 gate2R: train -1.96k / -21k; TEST -5.77k / -36k; w0.50 cap- gate2R: train -1.93k / -20k; TEST -5.08k / -39k; w0.50 cap8 gate2R: train -2.51k / -25k; TEST -7.19k / -47k. The train-selected cells reduce the test drawdown by more than they did in training and cost more mean (the test window is the high-return, deeper-drawdown period); none selected the 1R gate on the training window.
Paired weekly differences vs live (148 weeks, 95% block-bootstrap CI, block 4), $ per week: w0.50 cap8 gate1R -6,466 [-9,309, -3,992]; w0.75 cap8 gate1R -6,195 [-9,138, -3,737]; w0.50 cap10 gate1R -5,586 [-8,130, -3,420]; w0.50 cap12 gate1R -5,113 [-7,604, -3,007]; w0.50 gate1R -4,778 [-7,338, -2,757]; w0.75 cap12 gate1R -4,612 [-7,055, -2,539]; w0.75 gate1R -4,184 [-6,451, -2,213]; w0.75 cap10 gate2R -4,132 [-6,141, -2,321]; w0.75 cap12 gate2R -3,472 [-5,219, -2,068]; w0.75 gate2R -3,071 [-4,737, -1,592]; w1.00 cap10 gate2R -2,228 [-3,472, -1,237]; w1.00 cap12 gate2R -1,020 [-1,650, -468]; w1.00 cap14 gate2R -422 [-698, -151]. Every frontier cell is below live in mean with an interval that excludes zero (the price of the lower drawdown is a certain, measurable one; the drawdown reduction in the 2023-26 sample is one path).

## Limits
* In-sample 2023-26 (187 weeks, one regime episode in 2026); the frontier is of historical drawdowns, not of a forecast distribution; the synthetic tail is a method, not a measurement.
* Lots are integers with a 1-lot minimum: the PE weight is coarse (7 lots), the cap is applied to the new entry only; the PE-weight fold uses the DIS-AH product-then-round convention, not the live order.
* 31 cells did not converge (pause cells); the lock governor does not see the PE weight or the cap (kept at the ER multiplier).
* Worst-of maxDD takes the maximum of three windows; other aggregations (for example a weighted sum) would change the frontier.

## AMENDMENT 2026-11-04 (ZL-2, appended): the 31 non-converged cells rerun to a fixed point
Request (lead): do not report the 31 cells (30 pause-30 cells, 1 pause-15 cell) as last iterates. Rerun (rf_fix.py): up to 20 passes of the same loop (cap pass, pause mask from the previous pass's cut trades, rerun), with a monotone-union damping fallback if a repeated state is detected; the fallback was not needed. Result: all 31 cells reach an exact fixed point (no taken row changes lots and the pause mask is unchanged) after 8-9 passes (the earlier limit was 6 passes, so the cells had not yet been declared converged although the values had stopped moving). New CSV: l2vast/ds3/out/dis_ba/DS3_RISK_FRONTIER_v2.csv (all 92 cells; the first CSV is unchanged); per-cell old-vs-new: out/dis_ba/rf_amend_changes.csv.
Changes: 29 of 31 cells are identical to the first table within 0.05% in mean and within $0.01k in every maxDD. Two cells change by more than 2% in one drawdown: w0.50 cap- pause30 gate1R and w0.50 cap14 pause30 gate1R, 2026 maxDD $22.78k -> $22.23k (-2.4%); their mean is unchanged ($10.59k, +0.04%) and their worst-of maxDD is unchanged ($62.42k). No cell changes by more than 2% in mean. FRONTIER MEMBERSHIP IS UNCHANGED: the same 14 cells (live included), the same costs per $1k removed, and the pause remains on no frontier cell. Every statement in sections 0-5 stands; the sentence in section 0 that 31 cells did not converge is superseded by this amendment (they all converge).
Corrected rows (v2; mean $k/wk, full-period maxDD, 2026 maxDD, HOLD maxDD, worst-of maxDD, synthetic tail $k, converged):
| cell | mean | maxDD | 2026 dd | HOLD dd | worst-of dd | tail | converged |
|---|---|---|---|---|---|---|---|
| w0.50 cap- pause30 gate1R | 10.59 | 58.0 | 22.2 | 62.4 | 62.4 | 435 | 1 |
| w0.50 cap- pause30 gate2R | 10.97 | 58.4 | 28.8 | 82.5 | 82.5 | 435 | 1 |
| w0.50 cap10 pause30 gate1R | 10.09 | 58.0 | 24.3 | 62.4 | 62.4 | 348 | 1 |
| w0.50 cap10 pause30 gate2R | 10.52 | 58.4 | 28.8 | 83.0 | 83.0 | 348 | 1 |
| w0.50 cap12 pause30 gate1R | 10.42 | 58.0 | 22.5 | 62.4 | 62.4 | 406 | 1 |
| w0.50 cap12 pause30 gate2R | 10.82 | 58.4 | 28.8 | 82.5 | 82.5 | 406 | 1 |
| w0.50 cap14 pause30 gate1R | 10.56 | 58.0 | 22.2 | 62.4 | 62.4 | 435 | 1 |
| w0.50 cap14 pause30 gate2R | 10.96 | 58.4 | 28.8 | 82.5 | 82.5 | 435 | 1 |
| w0.50 cap8 pause30 gate1R | 9.51 | 59.9 | 26.7 | 62.1 | 62.1 | 319 | 1 |
| w0.50 cap8 pause30 gate2R | 9.81 | 61.1 | 27.8 | 81.4 | 81.4 | 319 | 1 |
| w0.75 cap- pause30 gate1R | 11.62 | 64.0 | 27.1 | 85.1 | 85.1 | 464 | 1 |
| w0.75 cap- pause30 gate2R | 12.16 | 64.4 | 33.1 | 108.3 | 108.3 | 464 | 1 |
| w0.75 cap10 pause30 gate1R | 10.96 | 62.4 | 25.9 | 85.9 | 85.9 | 348 | 1 |
| w0.75 cap10 pause30 gate2R | 11.46 | 66.2 | 31.9 | 108.8 | 108.8 | 348 | 1 |
| w0.75 cap12 pause30 gate1R | 11.30 | 64.0 | 27.1 | 85.1 | 85.1 | 406 | 1 |
| w0.75 cap12 pause30 gate2R | 11.90 | 64.4 | 33.1 | 107.6 | 107.6 | 406 | 1 |
| w0.75 cap14 pause30 gate1R | 11.55 | 64.0 | 27.1 | 85.1 | 85.1 | 464 | 1 |
| w0.75 cap14 pause30 gate2R | 12.11 | 64.4 | 33.1 | 108.3 | 108.3 | 464 | 1 |
| w0.75 cap8 pause30 gate1R | 10.18 | 65.3 | 26.6 | 80.2 | 80.2 | 319 | 1 |
| w0.75 cap8 pause30 gate2R | 10.70 | 67.2 | 29.3 | 103.8 | 103.8 | 319 | 1 |
| w1.00 cap- pause30 gate1R | 13.61 | 88.8 | 30.6 | 112.0 | 112.0 | 522 | 1 |
| w1.00 cap- pause30 gate2R | 14.91 | 85.5 | 38.4 | 128.2 | 128.2 | 522 | 1 |
| w1.00 cap10 pause30 gate1R | 12.08 | 79.6 | 43.5 | 108.7 | 108.7 | 377 | 1 |
| w1.00 cap10 pause30 gate2R | 13.28 | 76.3 | 38.9 | 131.0 | 131.0 | 377 | 1 |
| w1.00 cap12 pause30 gate1R | 13.09 | 83.5 | 31.3 | 113.4 | 113.4 | 435 | 1 |
| w1.00 cap12 pause30 gate2R | 14.23 | 80.2 | 40.3 | 129.4 | 129.4 | 435 | 1 |
| w1.00 cap14 pause30 gate1R | 13.37 | 86.5 | 30.6 | 112.0 | 112.0 | 464 | 1 |
| w1.00 cap14 pause30 gate2R | 14.69 | 83.2 | 38.4 | 127.5 | 127.5 | 464 | 1 |
| w1.00 cap8 pause15 gate1R | 10.96 | 70.0 | 46.9 | 118.9 | 118.9 | 319 | 1 |
| w1.00 cap8 pause30 gate1R | 10.90 | 69.7 | 43.3 | 84.9 | 84.9 | 319 | 1 |
| w1.00 cap8 pause30 gate2R | 11.98 | 73.6 | 40.2 | 112.4 | 112.4 | 319 | 1 |
