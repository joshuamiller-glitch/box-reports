# DS3_REBUILD_S1R - Stage 1R: every entry condition re-scored by the user's rolling rule on the RAW books (W-S1R)

1. WHICH WORK under the user's rule (recent-data picks, refit every 2 weeks, OOS chained, label needs excess over the shifted-label / random-skip / nonsense nulls): 1d (confluence: dMeanR +0.023, ulcer -46.7% vs shift-null -0.002 / -20.0%). WEAK-BUT-POSITIVE (positive OOS but not clearly past the nulls): 3, 5, 8, 9, 1a, 1h, 5a, 5b.
2. WHICH DO NOT: 1, 2, 4, 6, 7, 10, 1b, 1c, 1e, 1f, 1g, ALL (BEST-AVAILABLE-NOT-PROVEN: the rolling picks do not beat what the same procedure earns on shifted labels / random skips). Control columns (nonsense / random / planted) under the same procedure: NONS=BEST-AVAILABLE-NOT-PROVEN, RAND=WEAK-BUT-POSITIVE, PLANT=CONFIRMED.
3. ALL families pooled, top-5 picks, trailing 6M, 15% prior-year gate, next 2 weeks chained over 2 book x session cells: BEST-AVAILABLE-NOT-PROVEN; OOS dMeanR -0.000 R, dUlcer -25.7%, persistence 44% (bar 60%) vs shifted-label nulls -0.003 R / -10.2% (see the first table for the sub-families).
4. TODAY'S PICKS (refit ending 2026-10-30, pick window 2026-05-01..2026-10-30 / 3M 2026-08-01..): per book x session in the "Current picks" section below (top 5 and the best pick per family, with 6M and 3M effect, prior-year 15/30 flags, feed need and whether D7 can compute it live); CSVs /mnt/l2/l2vast/_s1r/eval/picks_now_all.csv and picks_now_family.csv.
5. DATA END 2026-10-30 (engine store ends there; November 2026 is not in the raw engine base so it could not be extended); cells done 2/15 as of 2026-11-17 20:05 UTC; first table 00:20Z, full set 06:20Z; wait-then-enter / early-exit and the score votes are in their own sections. Label scale: CONFIRMED / LEAD / WEAK-BUT-POSITIVE / BEST-AVAILABLE-NOT-PROVEN (rules below).

> VALIDATION (FIRST PASS, written 2026-11-17 20:05 UTC): rule = the user's standing selection rule (autopilot/DIRECTIVE_SELECTION_RULE_20261117.md, STAGE1R order 18:17Z): pick on the TRAILING 6 months (3 months shown beside), refit every 14 days from 2023-10-02 to 2026-10-31, prior-years check = not-a-disaster at 15%/30%, validated by walking the procedure forward (OOS pieces chained), NOT a frozen holdout. Trials counted: 63626 candidate columns x 2 sides x 3 actions per cell and refit (65,192 columns in the stage-1 store; 63,626 at-entry-clean + 299 controls scored here) x 15 cells x 79 refits x 2 windows x 4 label versions; correction = nulls (shifted labels 11/23/37 days, nonsense/random/planted columns, 10 random persistent skips with the same share and action), plus the label rules below; no White RC/SPA/DSR/PBO is computed (a rolling pick procedure is evaluated by its OOS excess over nulls instead); NOT engine-exact (raw-chassis trade P&L at base lots, $4.84 RT), no re-entry or freed-book effects; the engine-exact stage-2 run comes later via the lead. Data end 2026-10-30; pick-window end 2026-10-30; refit date 2026-10-31.

## Rule and procedure (what was run)
- Base: RAW book trades (K7 M7 P7 U7 A7 H7 O7; 21,049 trades; per book x session cell, 15 cells; the same stage-0 raw base as stage 1). Dollar columns $4.84 RT at base lots (x1.75 live-lot scaling is linear in these units and not shown separately). Ulcer = RMS of daily drawdown of the cell P&L (PRIMARY); mean R per unit of size.
- Candidates at each refit: every at-entry column (names with delay >= 5 s, "ahead" and stack-based context columns excluded from this table; the honest wait/early-exit versions are in their own section) x side (yes / no) x action (skip, half size, x1.5). Ranking on the trailing window: percentile-rank(delta mean R) + percentile-rank(-delta ulcer) among rules that improve both; the acted-on share must be 5-70% of trades; top 60 per family, picks diversified (flag correlation < 0.8).
- Not-a-disaster check on each prior 365-day block before the pick window: GREEN = ulcer <= +15% and mean not worse than 15% (floor 0.03 R) vs doing nothing; AMBER 15-30%; RED > 30%. Gate g15 keeps GREEN only, g30 keeps GREEN+AMBER, g0 no gate (reference). Early refits (first months) have no prior block: the check is vacuous there and is stated.
- Picks traded on the next 2 weeks (also 1 month and 3 months; each horizon re-picks at its own spacing and chains non-overlapping pieces). N = 1, 3, 5, 10 picks per cell; several picks multiply their size factors (capped at x1.5). Persistence = share of refit periods in which the picks made more $ than no rule among periods where a pick acted.
- Nulls with the identical procedure: outcome labels shifted by 11 / 23 / 37 days in the pick phase (picks chosen on the wrong labels, traded on TRUE outcomes); 10 random persistent skip draws with the same share and action per pick; the 200 nonsense, 90 persistent-random and 9 planted columns run as ordinary candidate families.
- Label: CONFIRMED = dMeanR > 0 and dUlcer < 0 OOS, persistence > 60%, beats all three shifted-label nulls on both, beats >= 90% of random-skip draws on both, positive in >= 2 of 3 time thirds, and the 3M-window pick also positive. LEAD = same with persistence > 55%, random >= 75%. WEAK-BUT-POSITIVE = positive OOS and better than the mean of the shifted nulls. Otherwise BEST-AVAILABLE-NOT-PROVEN. Primary setting N=5, 6M, g15, next 2 weeks; other settings in the tables.

## FIRST TABLE: family and sub-family (N=5 picks, trailing 6M, 15% prior-year gate, next-2-weeks chained OOS, all cells done)
| set   | what                                                                       | label                     |   OOS dMeanR |   OOS dUlcer% | dMaxDD$ (rule/base)   |   d$/wk | exposure   | persist   |   shift-null dMeanR |   shift-null dUlcer% | beats all 3 shifts   | beats random-skip draws (dU/dm)   |   thirds ok | 3M-window agrees   |
|:------|:---------------------------------------------------------------------------|:--------------------------|-------------:|--------------:|:----------------------|--------:|:-----------|:----------|--------------------:|---------------------:|:---------------------|:----------------------------------|------------:|:-------------------|
| 1     | F1 confluence library (all)                                                | BEST-AVAILABLE-NOT-PROVEN |        0     |         -31.9 | 53693/74495           |    -180 | 72%        | 42%       |               0.001 |                -19.7 | no                   | 80%/60%                           |           2 | yes                |
| 2     | candle counting, ICT 7-13-21, IRL/ERL                                      | BEST-AVAILABLE-NOT-PROVEN |        0.002 |         -24.9 | 58215/74495           |    -104 | 79%        | 48%       |              -0.001 |                -24.9 | no                   | 70%/80%                           |           1 | no                 |
| 3     | levels and zones (own zones, session/round levels)                         | WEAK-BUT-POSITIVE         |        0.006 |          -8.1 | 69913/74495           |      91 | 93%        | 44%       |              -0.001 |                 -2.7 | yes                  | 80%/80%                           |           1 | no                 |
| 4     | range forecasts (HAR / options / UW / own bar)                             | BEST-AVAILABLE-NOT-PROVEN |        0.002 |         -10.2 | 72189/74495           |      -4 | 92%        | 48%       |               0.002 |                -18.7 | no                   | 60%/40%                           |           1 | no                 |
| 5     | F5 order flow (all)                                                        | WEAK-BUT-POSITIVE         |        0.001 |         -28   | 54004/74495           |    -171 | 75%        | 43%       |               0     |                -18.9 | no                   | 50%/50%                           |           2 | yes                |
| 6     | other markets and breadth                                                  | BEST-AVAILABLE-NOT-PROVEN |        0.002 |         -14.6 | 61966/74495           |    -168 | 76%        | 46%       |               0.003 |                -37.6 | no                   | 60%/50%                           |           2 | no                 |
| 7     | Unusual Whales options / positioning                                       | BEST-AVAILABLE-NOT-PROVEN |       -0.003 |          16.4 | 88117/74495           |    -167 | 89%        | 47%       |               0.002 |                -12.3 | no                   | 0%/20%                            |           1 | no                 |
| 8     | day / regime / time of day / calendar                                      | WEAK-BUT-POSITIVE         |        0.001 |         -30   | 57443/74495           |    -120 | 82%        | 42%       |              -0.003 |                 -9.6 | no                   | 100%/70%                          |           2 | yes                |
| 9     | causal trade context (raw)                                                 | WEAK-BUT-POSITIVE         |        0.005 |         -27.6 | 63780/74495           |     -21 | 85%        | 48%       |              -0.002 |                  0.5 | yes                  | 100%/100%                         |           2 | yes                |
| 10    | TICK internals                                                             | BEST-AVAILABLE-NOT-PROVEN |        0.001 |           0.2 | 75496/74495           |       6 | 97%        | 51%       |              -0.001 |                  1.4 | yes                  | 20%/30%                           |           1 | no                 |
| 1a    | confluence: named indicators / session anchors                             | WEAK-BUT-POSITIVE         |        0.001 |         -25.4 | 54999/74495           |    -205 | 72%        | 52%       |              -0.001 |                -15.9 | yes                  | 70%/60%                           |           1 | yes                |
| 1b    | confluence: entry-table universe                                           | BEST-AVAILABLE-NOT-PROVEN |        0.001 |         -18.2 | 63053/74495           |    -161 | 71%        | 52%       |               0.004 |                -33.1 | no                   | 40%/70%                           |           2 | yes                |
| 1c    | confluence: oscillators                                                    | BEST-AVAILABLE-NOT-PROVEN |        0.007 |         -15.1 | 60011/74495           |     -82 | 73%        | 51%       |              -0.002 |                -28.9 | no                   | 30%/100%                          |           2 | yes                |
| 1d    | confluence: trend                                                          | LEAD                      |        0.023 |         -46.7 | 47443/74495           |     236 | 70%        | 55%       |              -0.002 |                -20   | yes                  | 100%/100%                         |           3 | yes                |
| 1e    | confluence: SMC / ICT structure                                            | BEST-AVAILABLE-NOT-PROVEN |        0.008 |         -22   | 65025/74495           |     -34 | 77%        | 53%       |               0.001 |                -27.9 | no                   | 90%/100%                          |           2 | yes                |
| 1f    | confluence: vol / squeeze / state / ML                                     | BEST-AVAILABLE-NOT-PROVEN |        0     |         -30.7 | 53260/74495           |    -130 | 76%        | 49%       |               0.007 |                -28.9 | no                   | 60%/60%                           |           1 | no                 |
| 1g    | confluence: alternate-bar indicators (HA, range, renko, tick, volume bars) | BEST-AVAILABLE-NOT-PROVEN |       -0.002 |         -28.4 | 56584/74495           |    -203 | 73%        | 43%       |              -0.004 |                -14.5 | no                   | 50%/20%                           |           1 | yes                |
| 1h    | confluence: alt-bar agreement                                              | WEAK-BUT-POSITIVE         |        0.007 |         -28   | 53487/74495           |     -33 | 77%        | 54%       |              -0.002 |                -16   | yes                  | 90%/70%                           |           2 | no                 |
| 5a    | order flow: tape prints and speed                                          | WEAK-BUT-POSITIVE         |        0.005 |         -38.5 | 42433/74495           |     -60 | 75%        | 46%       |               0     |                -18.2 | no                   | 90%/80%                           |           2 | yes                |
| 5b    | order flow: L3 / L2 book / flow library                                    | WEAK-BUT-POSITIVE         |        0.001 |         -24.1 | 56897/74495           |    -145 | 78%        | 48%       |              -0     |                -19.2 | no                   | 60%/40%                           |           2 | no                 |
| ALL   | ALL families pooled                                                        | BEST-AVAILABLE-NOT-PROVEN |       -0     |         -25.7 | 57805/74495           |    -180 | 73%        | 44%       |              -0.003 |                -10.2 | no                   | 50%/60%                           |           1 | yes                |
| NONS  | CONTROL nonsense columns (200)                                             | BEST-AVAILABLE-NOT-PROVEN |        0.008 |         -32.9 | 47334/74495           |    -101 | 64%        | 56%       |               0.001 |                -35   | no                   | 60%/100%                          |           2 | yes                |
| RAND  | CONTROL persistent random columns (90)                                     | WEAK-BUT-POSITIVE         |        0.005 |         -31   | 55727/74495           |     -48 | 80%        | 50%       |               0.003 |                -27.5 | no                   | 90%/100%                          |           3 | no                 |
| PLANT | CONTROL planted-edge columns (9)                                           | CONFIRMED                 |        0.047 |         -43.7 | 52847/74495           |    1552 | 112%       | 81%       |              -0.048 |                137.2 | yes                  | 100%/100%                         |           3 | yes                |

Same, trailing 3M picks:
| set   | what                                                                       | label                     |   OOS dMeanR |   OOS dUlcer% | dMaxDD$ (rule/base)   |   d$/wk | exposure   | persist   |   shift-null dMeanR |   shift-null dUlcer% | beats all 3 shifts   | beats random-skip draws (dU/dm)   |   thirds ok | 3M-window agrees   |
|:------|:---------------------------------------------------------------------------|:--------------------------|-------------:|--------------:|:----------------------|--------:|:-----------|:----------|--------------------:|---------------------:|:---------------------|:----------------------------------|------------:|:-------------------|
| 1     | F1 confluence library (all)                                                | WEAK-BUT-POSITIVE         |        0.003 |         -23   | 62474/79778           |    -114 | 76%        | 45%       |              -0     |                -19.3 | no                   | /                                 |           2 | yes                |
| 2     | candle counting, ICT 7-13-21, IRL/ERL                                      | BEST-AVAILABLE-NOT-PROVEN |       -0.006 |         -17.1 | 72159/79778           |    -262 | 81%        | 50%       |               0.002 |                -32.9 | no                   | /                                 |           2 | yes                |
| 3     | levels and zones (own zones, session/round levels)                         | BEST-AVAILABLE-NOT-PROVEN |       -0.002 |           6.8 | 84426/79778           |     -96 | 94%        | 50%       |              -0.006 |                  7.1 | no                   | /                                 |           2 | yes                |
| 4     | range forecasts (HAR / options / UW / own bar)                             | BEST-AVAILABLE-NOT-PROVEN |       -0.004 |         -11.4 | 67504/79778           |    -127 | 90%        | 51%       |               0.004 |                 -6.4 | no                   | /                                 |           1 | yes                |
| 5     | F5 order flow (all)                                                        | WEAK-BUT-POSITIVE         |        0.001 |         -30.9 | 53207/79778           |    -170 | 75%        | 47%       |              -0.004 |                -12.2 | no                   | /                                 |           1 | yes                |
| 6     | other markets and breadth                                                  | BEST-AVAILABLE-NOT-PROVEN |       -0.005 |          -7.9 | 68761/79778           |    -274 | 75%        | 52%       |               0.002 |                -33.5 | no                   | /                                 |           1 | yes                |
| 7     | Unusual Whales options / positioning                                       | BEST-AVAILABLE-NOT-PROVEN |       -0.003 |           3.3 | 82113/79778           |    -141 | 87%        | 51%       |               0.001 |                 -8.7 | no                   | /                                 |           1 | no                 |
| 8     | day / regime / time of day / calendar                                      | WEAK-BUT-POSITIVE         |        0.004 |         -38.7 | 52552/79778           |     -43 | 80%        | 56%       |              -0.005 |                 -6.6 | yes                  | /                                 |           2 | yes                |
| 9     | causal trade context (raw)                                                 | WEAK-BUT-POSITIVE         |        0.002 |         -25.5 | 60362/79778           |     -73 | 84%        | 52%       |              -0.004 |                  1.8 | yes                  | /                                 |           2 | yes                |
| 10    | TICK internals                                                             | BEST-AVAILABLE-NOT-PROVEN |       -0.002 |           1.8 | 82180/79778           |     -29 | 98%        | 32%       |              -0.001 |                 -0.2 | no                   | /                                 |           1 | no                 |
| 1a    | confluence: named indicators / session anchors                             | WEAK-BUT-POSITIVE         |        0.013 |         -31.7 | 54604/79778           |      53 | 72%        | 53%       |               0     |                -16.7 | yes                  | /                                 |           3 | yes                |
| 1b    | confluence: entry-table universe                                           | BEST-AVAILABLE-NOT-PROVEN |        0     |         -24.5 | 62527/79778           |    -189 | 76%        | 46%       |               0.002 |                -28.2 | no                   | /                                 |           2 | yes                |
| 1c    | confluence: oscillators                                                    | WEAK-BUT-POSITIVE         |        0.003 |         -31.9 | 55064/79778           |    -117 | 76%        | 50%       |               0     |                -29.1 | no                   | /                                 |           2 | yes                |
| 1d    | confluence: trend                                                          | WEAK-BUT-POSITIVE         |        0.015 |         -36.1 | 51070/79778           |      85 | 74%        | 57%       |               0.002 |                -31.6 | no                   | /                                 |           3 | yes                |
| 1e    | confluence: SMC / ICT structure                                            | BEST-AVAILABLE-NOT-PROVEN |        0     |         -13.8 | 68333/79778           |    -147 | 78%        | 55%       |               0.001 |                -24.9 | no                   | /                                 |           2 | yes                |
| 1f    | confluence: vol / squeeze / state / ML                                     | BEST-AVAILABLE-NOT-PROVEN |       -0.001 |         -21   | 65428/79778           |    -184 | 77%        | 47%       |              -0.001 |                -14.6 | no                   | /                                 |           1 | yes                |
| 1g    | confluence: alternate-bar indicators (HA, range, renko, tick, volume bars) | BEST-AVAILABLE-NOT-PROVEN |        0.002 |         -22.8 | 70680/79778           |    -130 | 75%        | 54%       |               0.001 |                -25.1 | no                   | /                                 |           1 | no                 |
| 1h    | confluence: alt-bar agreement                                              | BEST-AVAILABLE-NOT-PROVEN |       -0.004 |         -26   | 54123/79778           |    -241 | 76%        | 46%       |              -0.004 |                -12.3 | no                   | /                                 |           1 | yes                |
| 5a    | order flow: tape prints and speed                                          | WEAK-BUT-POSITIVE         |        0.009 |         -45   | 40542/79778           |     -41 | 72%        | 47%       |               0.001 |                -22.5 | yes                  | /                                 |           2 | yes                |
| 5b    | order flow: L3 / L2 book / flow library                                    | BEST-AVAILABLE-NOT-PROVEN |       -0.008 |         -22.8 | 58543/79778           |    -305 | 79%        | 46%       |               0.001 |                -17   | no                   | /                                 |           0 | yes                |
| ALL   | ALL families pooled                                                        | WEAK-BUT-POSITIVE         |        0.002 |         -28.4 | 61824/79778           |    -102 | 76%        | 47%       |               0.002 |                -19.1 | no                   | /                                 |           1 | no                 |
| NONS  | CONTROL nonsense columns (200)                                             | BEST-AVAILABLE-NOT-PROVEN |        0.005 |         -31.9 | 57631/79778           |    -152 | 64%        | 50%       |              -0.002 |                -36.2 | no                   | /                                 |           2 | yes                |
| RAND  | CONTROL persistent random columns (90)                                     | BEST-AVAILABLE-NOT-PROVEN |       -0.002 |         -31.2 | 57140/79778           |    -173 | 79%        | 49%       |               0.004 |                -33.4 | no                   | /                                 |           2 | yes                |
| PLANT | CONTROL planted-edge columns (9)                                           | WEAK-BUT-POSITIVE         |        0.043 |         -46.3 | 53037/79778           |    1348 | 111%       | 89%       |              -0.06  |                142.1 | yes                  | /                                 |           3 | yes                |

## By number of picks (N) and prior-year gate (all families pooled and each main family, 6M, next 2 weeks)
| set   | gate   |   N | label                     |   dMeanR |   dUlcer% | persist   |   shift dMeanR |   shift dUlcer% | rnd beaten dU/dm   |
|:------|:-------|----:|:--------------------------|---------:|----------:|:----------|---------------:|----------------:|:-------------------|
| ALL   | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.001 |      -5   | 43%       |          0.009 |            -6.8 | /                  |
| ALL   | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0     |      -0.7 | 41%       |         -0.002 |           -10.2 | /                  |
| ALL   | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.006 |       1   | 44%       |         -0.004 |           -17.7 | /                  |
| ALL   | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.004 |     -11.8 | 45%       |         -0.003 |           -18.3 | /                  |
| ALL   | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.001 |       4.4 | 46%       |         -0.004 |            -8.8 | 30%/60%            |
| ALL   | g15    |   3 | WEAK-BUT-POSITIVE         |    0.008 |     -21.9 | 50%       |         -0.004 |            -3.8 | 70%/90%            |
| ALL   | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0     |     -25.7 | 44%       |         -0.003 |           -10.2 | 50%/60%            |
| ALL   | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -17.4 | 47%       |         -0.004 |           -18.5 | 50%/50%            |
| ALL   | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.011 |      29.6 | 41%       |          0.004 |            -3.8 | /                  |
| ALL   | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -9.1 | 43%       |          0.002 |           -14   | /                  |
| ALL   | g30    |   5 | WEAK-BUT-POSITIVE         |    0.003 |     -25.4 | 45%       |         -0.003 |           -10.1 | /                  |
| ALL   | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0     |     -23.3 | 47%       |         -0.002 |           -15.6 | /                  |
| 1     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.014 |      53.1 | 38%       |         -0.004 |            13.5 | /                  |
| 1     | g0     |   3 | WEAK-BUT-POSITIVE         |    0.002 |      -0.5 | 44%       |         -0.007 |             1.9 | /                  |
| 1     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0     |      -7.2 | 43%       |         -0.002 |            -9.9 | /                  |
| 1     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -14.2 | 44%       |         -0.003 |           -15.6 | /                  |
| 1     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.017 |       4.4 | 41%       |          0.005 |           -22.7 | 40%/10%            |
| 1     | g15    |   3 | WEAK-BUT-POSITIVE         |    0.005 |     -35.2 | 46%       |         -0     |           -13.6 | 90%/70%            |
| 1     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0     |     -31.9 | 42%       |          0.001 |           -19.7 | 80%/60%            |
| 1     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -22.2 | 44%       |         -0.004 |           -18.4 | 60%/50%            |
| 1     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.01  |       0.2 | 41%       |          0.007 |           -12.2 | /                  |
| 1     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0     |     -26.1 | 41%       |          0     |            -7.7 | /                  |
| 1     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |     -27.3 | 44%       |          0.001 |           -14.5 | /                  |
| 1     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |     -24.1 | 42%       |         -0.001 |           -18   | /                  |
| 2     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.006 |      20.7 | 47%       |         -0     |           -11   | /                  |
| 2     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.007 |       4.8 | 52%       |         -0.004 |           -20.5 | /                  |
| 2     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.004 |     -16.4 | 47%       |         -0.002 |           -25.4 | /                  |
| 2     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |     -15   | 49%       |          0     |           -32.4 | /                  |
| 2     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |    0     |       2.8 | 43%       |         -0.012 |            11.9 | 40%/50%            |
| 2     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0     |     -15.7 | 48%       |         -0.004 |           -20.2 | 50%/70%            |
| 2     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -24.9 | 48%       |         -0.001 |           -24.9 | 70%/80%            |
| 2     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.004 |     -25.4 | 52%       |          0.001 |           -27.5 | 80%/100%           |
| 2     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.008 |      30.5 | 46%       |         -0.014 |            20.2 | /                  |
| 2     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |     -14   | 47%       |         -0.003 |           -16.5 | /                  |
| 2     | g30    |   5 | WEAK-BUT-POSITIVE         |    0.001 |     -21.4 | 52%       |         -0.005 |           -17.7 | /                  |
| 2     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.004 |     -22.6 | 52%       |         -0     |           -26.5 | /                  |
| 3     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.001 |      16.2 | 47%       |          0.003 |            -1.9 | /                  |
| 3     | g0     |   3 | WEAK-BUT-POSITIVE         |    0.002 |      -2.3 | 47%       |          0.001 |             3   | /                  |
| 3     | g0     |   5 | WEAK-BUT-POSITIVE         |    0.004 |      -1.7 | 47%       |          0.001 |             1.2 | /                  |
| 3     | g0     |  10 | WEAK-BUT-POSITIVE         |    0.004 |      -2   | 47%       |          0     |             1.2 | /                  |
| 3     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.005 |       1.2 | 43%       |          0     |            -2.3 | 40%/60%            |
| 3     | g15    |   3 | WEAK-BUT-POSITIVE         |    0.005 |      -7.5 | 44%       |         -0     |            -2.9 | 80%/60%            |
| 3     | g15    |   5 | WEAK-BUT-POSITIVE         |    0.006 |      -8.1 | 44%       |         -0.001 |            -2.7 | 80%/80%            |
| 3     | g15    |  10 | WEAK-BUT-POSITIVE         |    0.006 |      -8.1 | 44%       |         -0.001 |            -2.6 | 80%/80%            |
| 3     | g30    |   1 | WEAK-BUT-POSITIVE         |    0.005 |      -6   | 45%       |          0.001 |            -0.8 | /                  |
| 3     | g30    |   3 | WEAK-BUT-POSITIVE         |    0.005 |      -8.9 | 48%       |          0     |             0.3 | /                  |
| 3     | g30    |   5 | WEAK-BUT-POSITIVE         |    0.006 |      -9.3 | 49%       |          0     |            -1.4 | /                  |
| 3     | g30    |  10 | WEAK-BUT-POSITIVE         |    0.006 |      -9.3 | 49%       |          0     |            -1.4 | /                  |
| 4     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.006 |      -0.8 | 44%       |          0.016 |           -26.4 | /                  |
| 4     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.006 |     -27.5 | 45%       |          0.008 |           -29.8 | /                  |
| 4     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.003 |     -16.1 | 47%       |          0.006 |           -23.7 | /                  |
| 4     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.005 |     -17   | 51%       |          0.006 |           -21.3 | /                  |
| 4     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |       9.7 | 46%       |          0.003 |            -1   | 10%/10%            |
| 4     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |      -8.7 | 51%       |          0.002 |           -18.6 | 50%/40%            |
| 4     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -10.2 | 48%       |          0.002 |           -18.7 | 60%/40%            |
| 4     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.003 |     -10.3 | 50%       |          0.002 |           -18.1 | 60%/60%            |
| 4     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |       2.4 | 47%       |          0.004 |            -4.5 | /                  |
| 4     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.003 |      -3   | 50%       |          0.003 |           -20.5 | /                  |
| 4     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.001 |      -9   | 48%       |          0.004 |           -22.8 | /                  |
| 4     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.003 |     -10.1 | 53%       |          0.003 |           -18.6 | /                  |
| 5     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.012 |      12   | 51%       |         -0.007 |             6.8 | /                  |
| 5     | g0     |   3 | WEAK-BUT-POSITIVE         |    0.005 |     -21.3 | 49%       |          0.003 |           -21.2 | /                  |
| 5     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |    0     |     -18.8 | 46%       |          0.006 |           -32.9 | /                  |
| 5     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |     -27.6 | 44%       |          0.003 |           -35.6 | /                  |
| 5     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.009 |      -7.2 | 48%       |         -0.001 |            -6.4 | 50%/30%            |
| 5     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0     |     -19.7 | 45%       |          0.004 |           -29.3 | 80%/70%            |
| 5     | g15    |   5 | WEAK-BUT-POSITIVE         |    0.001 |     -28   | 43%       |          0     |           -18.9 | 50%/50%            |
| 5     | g15    |  10 | WEAK-BUT-POSITIVE         |    0.002 |     -31.8 | 46%       |          0.001 |           -23.8 | 90%/60%            |
| 5     | g30    |   1 | WEAK-BUT-POSITIVE         |    0.009 |     -20.6 | 47%       |         -0.011 |             5.6 | /                  |
| 5     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.001 |     -18.5 | 45%       |          0.001 |           -19.9 | /                  |
| 5     | g30    |   5 | WEAK-BUT-POSITIVE         |    0.005 |     -24.7 | 48%       |         -0.005 |           -17.7 | /                  |
| 5     | g30    |  10 | WEAK-BUT-POSITIVE         |    0.005 |     -31.8 | 45%       |         -0.003 |           -22.2 | /                  |
| 6     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.017 |      40.7 | 44%       |         -0.011 |            -4.2 | /                  |
| 6     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |      11.1 | 50%       |         -0.004 |           -21.5 | /                  |
| 6     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.005 |      -4.1 | 46%       |          0.002 |           -36.3 | /                  |
| 6     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |      -7.4 | 48%       |         -0.001 |           -37.3 | /                  |
| 6     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |       0   | 49%       |         -0.012 |           -17.9 | 60%/40%            |
| 6     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.011 |     -22.3 | 54%       |          0.001 |           -29.7 | 60%/80%            |
| 6     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -14.6 | 46%       |          0.003 |           -37.6 | 60%/50%            |
| 6     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -8.9 | 44%       |         -0.001 |           -37.5 | 0%/20%             |
| 6     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.023 |      25.7 | 40%       |         -0.008 |           -11.3 | /                  |
| 6     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.004 |     -10.5 | 52%       |         -0.002 |           -31.5 | /                  |
| 6     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0     |      -3.3 | 48%       |          0.003 |           -39.6 | /                  |
| 6     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -7.3 | 44%       |         -0.001 |           -37.5 | /                  |
| 7     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      11   | 43%       |         -0.001 |             1   | /                  |
| 7     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |       7.2 | 49%       |         -0.001 |            -4.3 | /                  |
| 7     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |       1.8 | 52%       |         -0.001 |            -5.5 | /                  |
| 7     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |       6.3 | 44%       |          0     |            -5.7 | /                  |
| 7     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |       1.8 | 47%       |          0.001 |            -3.1 | 40%/50%            |
| 7     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |       5.9 | 48%       |          0     |            -8.8 | 10%/40%            |
| 7     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |      16.4 | 47%       |          0.002 |           -12.3 | 0%/20%             |
| 7     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |       9.7 | 47%       |          0.002 |           -11.2 | 0%/10%             |
| 7     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.004 |       6.1 | 44%       |          0.001 |            -1.9 | /                  |
| 7     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |       3.2 | 48%       |         -0     |            -5.1 | /                  |
| 7     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |       4.2 | 47%       |          0.001 |            -5.7 | /                  |
| 7     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |       7.6 | 43%       |          0.001 |            -8.4 | /                  |
| 8     | g0     |   1 | WEAK-BUT-POSITIVE         |    0.019 |     -28.6 | 46%       |         -0.012 |            -2.6 | /                  |
| 8     | g0     |   3 | WEAK-BUT-POSITIVE         |    0.009 |     -25.4 | 54%       |         -0.004 |           -13.4 | /                  |
| 8     | g0     |   5 | WEAK-BUT-POSITIVE         |    0.006 |     -24.3 | 58%       |         -0.003 |           -14.8 | /                  |
| 8     | g0     |  10 | WEAK-BUT-POSITIVE         |    0.001 |     -18   | 54%       |          0     |           -17   | /                  |
| 8     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.009 |       7.6 | 43%       |         -0.012 |            12   | 20%/30%            |
| 8     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -20.6 | 45%       |         -0.006 |            -6.9 | 80%/60%            |
| 8     | g15    |   5 | WEAK-BUT-POSITIVE         |    0.001 |     -30   | 42%       |         -0.003 |            -9.6 | 100%/70%           |
| 8     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.004 |     -18.6 | 51%       |         -0     |            -9.5 | 80%/20%            |
| 8     | g30    |   1 | WEAK-BUT-POSITIVE         |    0.004 |     -15.3 | 45%       |         -0.014 |             9.8 | /                  |
| 8     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.001 |     -12.4 | 50%       |         -0.005 |           -12.7 | /                  |
| 8     | g30    |   5 | WEAK-BUT-POSITIVE         |    0.002 |     -21.9 | 42%       |         -0.002 |           -16.2 | /                  |
| 8     | g30    |  10 | WEAK-BUT-POSITIVE         |    0.001 |     -22.5 | 51%       |         -0.001 |           -11.6 | /                  |
| 9     | g0     |   1 | WEAK-BUT-POSITIVE         |    0.036 |     -46.5 | 53%       |          0.005 |            -1.1 | /                  |
| 9     | g0     |   3 | WEAK-BUT-POSITIVE         |    0.008 |     -30.7 | 50%       |         -0.001 |             2.5 | /                  |
| 9     | g0     |   5 | WEAK-BUT-POSITIVE         |    0.007 |     -30.2 | 49%       |          0.001 |            -7.7 | /                  |
| 9     | g0     |  10 | WEAK-BUT-POSITIVE         |    0.006 |     -24.4 | 51%       |          0     |            -5   | /                  |
| 9     | g15    |   1 | LEAD                      |    0.021 |     -39.8 | 56%       |          0     |             5.9 | 100%/100%          |
| 9     | g15    |   3 | WEAK-BUT-POSITIVE         |    0.011 |     -40   | 52%       |         -0.003 |             4.1 | 100%/100%          |
| 9     | g15    |   5 | WEAK-BUT-POSITIVE         |    0.005 |     -27.6 | 48%       |         -0.002 |             0.5 | 100%/100%          |
| 9     | g15    |  10 | WEAK-BUT-POSITIVE         |    0.007 |     -26.6 | 51%       |         -0.002 |             3.5 | 100%/100%          |
| 9     | g30    |   1 | WEAK-BUT-POSITIVE         |    0.018 |     -38.6 | 51%       |          0.004 |             1.3 | /                  |
| 9     | g30    |   3 | WEAK-BUT-POSITIVE         |    0.009 |     -32.7 | 53%       |          0     |             0.6 | /                  |
| 9     | g30    |   5 | WEAK-BUT-POSITIVE         |    0.005 |     -29.4 | 48%       |         -0     |            -1.2 | /                  |
| 9     | g30    |  10 | WEAK-BUT-POSITIVE         |    0.003 |     -20.9 | 50%       |         -0     |             0.6 | /                  |
| 10    | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.01  |      12.9 | 36%       |         -0.002 |             0.4 | /                  |
| 10    | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |       3.4 | 35%       |         -0     |             0.7 | /                  |
| 10    | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |      -0.1 | 52%       |         -0     |            -0.2 | /                  |
| 10    | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |    0     |       0.2 | 46%       |         -0     |            -0.2 | /                  |
| 10    | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.007 |       5.9 | 43%       |         -0.002 |             2.3 | 0%/0%              |
| 10    | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0     |       0.4 | 44%       |          0     |             0.7 | 30%/30%            |
| 10    | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.001 |       0.2 | 51%       |         -0.001 |             1.4 | 20%/30%            |
| 10    | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0     |       1   | 49%       |         -0     |             0.8 | 20%/50%            |
| 10    | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.007 |       7.1 | 44%       |         -0.004 |             4.5 | /                  |
| 10    | g30    |   3 | WEAK-BUT-POSITIVE         |    0     |      -0.7 | 49%       |         -0     |             0.5 | /                  |
| 10    | g30    |   5 | WEAK-BUT-POSITIVE         |    0.001 |      -0.4 | 51%       |         -0     |             0.7 | /                  |
| 10    | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.001 |       0.1 | 49%       |         -0     |             0.3 | /                  |

## By horizon (picks traded the next 2 weeks / 1 month / 3 months; ALL pooled and main families; N=5, 6M, g15)
| set   | horizon   | label                     |   dMeanR |   dUlcer% | persist   |   shift dMeanR |   shift dUlcer% |
|:------|:----------|:--------------------------|---------:|----------:|:----------|---------------:|----------------:|
| ALL   | 2W        | BEST-AVAILABLE-NOT-PROVEN |   -0     |     -25.7 | 44%       |         -0.003 |           -10.2 |
| ALL   | 1M        | WEAK-BUT-POSITIVE         |    0.004 |     -19.6 | 57%       |         -0.003 |            -3.6 |
| ALL   | 3M        | BEST-AVAILABLE-NOT-PROVEN |   -0.006 |     -12.6 | 58%       |         -0.005 |            -5.1 |
| 1     | 2W        | BEST-AVAILABLE-NOT-PROVEN |    0     |     -31.9 | 42%       |          0.001 |           -19.7 |
| 1     | 1M        | WEAK-BUT-POSITIVE         |    0.004 |     -32   | 54%       |         -0.002 |           -11.9 |
| 1     | 3M        | BEST-AVAILABLE-NOT-PROVEN |   -0.007 |     -12   | 50%       |         -0.004 |            -8.2 |
| 2     | 2W        | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -24.9 | 48%       |         -0.001 |           -24.9 |
| 2     | 1M        | BEST-AVAILABLE-NOT-PROVEN |   -0.007 |     -13.1 | 49%       |         -0.003 |           -21   |
| 2     | 3M        | BEST-AVAILABLE-NOT-PROVEN |   -0.004 |     -16.3 | 46%       |         -0.005 |           -18.4 |
| 3     | 2W        | WEAK-BUT-POSITIVE         |    0.006 |      -8.1 | 44%       |         -0.001 |            -2.7 |
| 3     | 1M        | BEST-AVAILABLE-NOT-PROVEN |    0.004 |       1.3 | 51%       |          0.003 |            -3.2 |
| 3     | 3M        | BEST-AVAILABLE-NOT-PROVEN |    0     |       4.2 | 57%       |          0.001 |            -0.3 |
| 4     | 2W        | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -10.2 | 48%       |          0.002 |           -18.7 |
| 4     | 1M        | BEST-AVAILABLE-NOT-PROVEN |    0.006 |     -16.3 | 59%       |          0.002 |           -20.8 |
| 4     | 3M        | WEAK-BUT-POSITIVE         |    0.009 |     -19.3 | 68%       |         -0.001 |            -9.8 |
| 5     | 2W        | WEAK-BUT-POSITIVE         |    0.001 |     -28   | 43%       |          0     |           -18.9 |
| 5     | 1M        | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |     -23.9 | 42%       |          0.003 |           -25   |
| 5     | 3M        | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -30.6 | 46%       |          0.009 |           -36.9 |
| 6     | 2W        | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -14.6 | 46%       |          0.003 |           -37.6 |
| 6     | 1M        | BEST-AVAILABLE-NOT-PROVEN |    0.004 |     -18.6 | 49%       |          0.002 |           -33.3 |
| 6     | 3M        | BEST-AVAILABLE-NOT-PROVEN |   -0.008 |       2.5 | 46%       |          0.001 |           -32.6 |
| 7     | 2W        | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |      16.4 | 47%       |          0.002 |           -12.3 |
| 7     | 1M        | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      14.6 | 54%       |          0.001 |           -15.9 |
| 7     | 3M        | BEST-AVAILABLE-NOT-PROVEN |    0.003 |      -3.1 | 50%       |          0.001 |           -14.9 |
| 8     | 2W        | WEAK-BUT-POSITIVE         |    0.001 |     -30   | 42%       |         -0.003 |            -9.6 |
| 8     | 1M        | WEAK-BUT-POSITIVE         |    0.005 |     -28.4 | 56%       |         -0.004 |            -3.5 |
| 8     | 3M        | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |     -11.6 | 50%       |          0.002 |           -14.6 |
| 9     | 2W        | WEAK-BUT-POSITIVE         |    0.005 |     -27.6 | 48%       |         -0.002 |             0.5 |
| 9     | 1M        | WEAK-BUT-POSITIVE         |    0.009 |     -31.4 | 67%       |         -0.002 |             3.6 |
| 9     | 3M        | WEAK-BUT-POSITIVE         |    0.011 |     -31.9 | 64%       |          0.001 |            -7.9 |
| 10    | 2W        | BEST-AVAILABLE-NOT-PROVEN |    0.001 |       0.2 | 51%       |         -0.001 |             1.4 |
| 10    | 1M        | BEST-AVAILABLE-NOT-PROVEN |    0.001 |       2.3 | 62%       |          0.001 |             0.9 |
| 10    | 3M        | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |       7.7 | 69%       |         -0     |            -0.4 |

## By windows (chained OOS pieces whose refit falls in the window; N=5, 6M picks, g15; real vs mean of shifted-label nulls)
| set   | window   |   n trades |   dMeanR |   dUlcer% | maxDD rule/base $   |   d$/wk (base lots, $4.84) | persist   |   shift-null dMeanR |   shift-null dUlcer% |
|:------|:---------|-----------:|---------:|----------:|:--------------------|---------------------------:|:----------|--------------------:|---------------------:|
| ALL   | L3M      |        227 |   -0.01  |     -13.6 | 29501/32328         |                       -477 | 58%       |              -0.003 |                 -6.8 |
| ALL   | L6M      |        542 |   -0.002 |     -24.3 | 57805/68577         |                        159 | 50%       |              -0.004 |                -13.6 |
| ALL   | HOLD     |        408 |    0.021 |     -47   | 27642/48345         |                        538 | 35%       |              -0.004 |                 -8.6 |
| ALL   | GAP      |         96 |   -0.005 |     -26.1 | 8765/12337          |                      -1024 | 64%       |               0.007 |                -30.9 |
| ALL   | PRE      |        465 |   -0.006 |       0.9 | 26762/22932         |                       -512 | 37%       |              -0.004 |                 -6.7 |
| ALL   | XP       |        412 |   -0.002 |     -11.7 | 29878/35276         |                       -135 | 47%       |              -0.003 |                -19.1 |
| ALL   | POOLED   |       1980 |   -0     |     -25.7 | 57805/74495         |                       -180 | 44%       |              -0.003 |                -10.2 |
| 1     | L3M      |        227 |   -0.014 |     -11.3 | 30278/32328         |                       -632 | 50%       |              -0.004 |                 -8.2 |
| 1     | L6M      |        542 |   -0.001 |     -33.8 | 53693/68577         |                        230 | 50%       |               0.001 |                -22.5 |
| 1     | HOLD     |        408 |    0.025 |     -47.5 | 27051/48345         |                        598 | 35%       |              -0     |                -15.6 |
| 1     | GAP      |         96 |   -0.021 |     -19.9 | 9996/12337          |                      -1227 | 50%       |               0.004 |                -32.1 |
| 1     | PRE      |        465 |   -0.011 |       3.1 | 26745/22932         |                       -599 | 34%       |              -0.001 |                 -8   |
| 1     | XP       |        412 |    0.001 |     -21.8 | 30125/35276         |                        -88 | 45%       |               0.001 |                -18.2 |
| 1     | POOLED   |       1980 |    0     |     -31.9 | 53693/74495         |                       -180 | 42%       |               0.001 |                -19.7 |
| 2     | L3M      |        227 |   -0.015 |      -1.4 | 32273/32328         |                       -526 | 25%       |               0.021 |                -32.4 |
| 2     | L6M      |        542 |    0.003 |     -22.3 | 58215/68577         |                        311 | 50%       |               0.007 |                -21.1 |
| 2     | HOLD     |        408 |    0.017 |     -25.1 | 35882/48345         |                        419 | 62%       |              -0.004 |                -20.6 |
| 2     | GAP      |         96 |   -0.014 |     -12.1 | 11571/12337         |                       -751 | 29%       |              -0.031 |                -26.7 |
| 2     | PRE      |        465 |   -0.003 |     -10.7 | 20305/22932         |                       -413 | 45%       |               0.007 |                -13.4 |
| 2     | XP       |        412 |   -0.003 |     -16   | 31911/35276         |                       -131 | 48%       |              -0.004 |                -29   |
| 2     | POOLED   |       1980 |    0.002 |     -24.9 | 58215/74495         |                       -104 | 48%       |              -0.001 |                -24.9 |
| 3     | L3M      |        227 |    0.021 |     -30.6 | 23265/32328         |                        899 | 80%       |              -0.001 |                -17.5 |
| 3     | L6M      |        542 |    0.007 |      -5.2 | 61609/68577         |                        399 | 60%       |              -0.004 |                 -7.5 |
| 3     | HOLD     |        408 |   -0.001 |      -2.5 | 49572/48345         |                         19 | 38%       |              -0.001 |                 -5   |
| 3     | GAP      |         96 |    0.012 |     -22.4 | 9664/12337          |                       -281 | 38%       |               0.023 |                -14.7 |
| 3     | PRE      |        465 |   -0.007 |      -8.3 | 21372/22932         |                       -201 | 39%       |               0.002 |                 -7.6 |
| 3     | XP       |        412 |    0.035 |     -38.9 | 23502/35276         |                        327 | 52%       |              -0.004 |                -17.4 |
| 3     | POOLED   |       1980 |    0.006 |      -8.1 | 69913/74495         |                         91 | 44%       |              -0.001 |                 -2.7 |
| 4     | L3M      |        227 |    0     |       8.9 | 35871/32328         |                         90 | 62%       |              -0.009 |                 -6.3 |
| 4     | L6M      |        542 |    0.001 |      -6.1 | 67677/68577         |                        228 | 59%       |              -0.002 |                -13.9 |
| 4     | HOLD     |        408 |   -0.01  |      -9.6 | 43345/48345         |                       -360 | 54%       |               0.003 |                -17.6 |
| 4     | GAP      |         96 |   -0.014 |      -9.3 | 10045/12337         |                       -511 | 38%       |               0.011 |                -29.3 |
| 4     | PRE      |        465 |   -0.021 |      40.4 | 36103/22932         |                       -547 | 42%       |              -0.004 |                -10.2 |
| 4     | XP       |        412 |    0.043 |     -54   | 21753/35276         |                        543 | 48%       |               0.02  |                -37   |
| 4     | POOLED   |       1980 |    0.002 |     -10.2 | 72189/74495         |                         -4 | 48%       |               0.002 |                -18.7 |
| 5     | L3M      |        227 |   -0.008 |     -18.2 | 26929/32328         |                       -420 | 25%       |               0.003 |                -20.3 |
| 5     | L6M      |        542 |    0.001 |     -23.9 | 54004/68577         |                        275 | 38%       |              -0.005 |                -20.1 |
| 5     | HOLD     |        408 |    0.01  |     -29.3 | 34893/48345         |                        277 | 62%       |               0.006 |                -24.4 |
| 5     | GAP      |         96 |   -0.014 |      -9.7 | 10060/12337         |                       -819 | 21%       |              -0.029 |                -21.2 |
| 5     | PRE      |        465 |   -0.001 |     -20   | 17885/22932         |                       -420 | 55%       |               0.009 |                -17.1 |
| 5     | XP       |        412 |   -0.003 |     -17.1 | 31150/35276         |                       -166 | 38%       |               0.005 |                -38.3 |
| 5     | POOLED   |       1980 |    0.001 |     -28   | 54004/74495         |                       -171 | 43%       |               0     |                -18.9 |
| 6     | L3M      |        227 |    0.003 |     -13.3 | 27873/32328         |                       -115 | 42%       |               0.021 |                -39.1 |
| 6     | L6M      |        542 |    0.008 |     -34.2 | 50357/68577         |                        485 | 42%       |               0.014 |                -39.7 |
| 6     | HOLD     |        408 |   -0.003 |     -11.7 | 43237/48345         |                        -86 | 35%       |               0.011 |                -40.6 |
| 6     | GAP      |         96 |    0.03  |     -28   | 8298/12337          |                       -719 | 64%       |              -0.023 |                -26.2 |
| 6     | PRE      |        465 |    0.002 |     -18.7 | 21484/22932         |                       -331 | 42%       |               0.005 |                -15.3 |
| 6     | XP       |        412 |   -0.007 |      -8.9 | 32584/35276         |                       -253 | 50%       |              -0.005 |                -34.8 |
| 6     | POOLED   |       1980 |    0.002 |     -14.6 | 61966/74495         |                       -168 | 46%       |               0.003 |                -37.6 |
| 7     | L3M      |        227 |    0.006 |      -6.1 | 31282/32328         |                        164 | 67%       |              -0.006 |                -10.1 |
| 7     | L6M      |        542 |   -0.004 |       3.8 | 70566/68577         |                       -191 | 54%       |              -0.004 |                -14.3 |
| 7     | HOLD     |        408 |   -0.02  |       2   | 49818/48345         |                       -557 | 23%       |              -0.002 |                -17.7 |
| 7     | GAP      |         96 |    0.002 |     -13.7 | 10718/12337         |                       -458 | 43%       |               0.01  |                -13.5 |
| 7     | PRE      |        465 |    0.019 |      -1.3 | 22121/22932         |                         64 | 53%       |               0.014 |                 -7.4 |
| 7     | XP       |        412 |   -0.005 |       0.9 | 35276/35276         |                        -87 | 100%      |               0.002 |                 -0.1 |
| 7     | POOLED   |       1980 |   -0.003 |      16.4 | 88117/74495         |                       -167 | 47%       |               0.002 |                -12.3 |
| 8     | L3M      |        227 |    0.005 |      -3.3 | 31333/32328         |                         95 | 42%       |              -0.004 |                -10.4 |
| 8     | L6M      |        542 |    0.006 |     -21.7 | 57443/68577         |                        328 | 50%       |              -0.002 |                -15.2 |
| 8     | HOLD     |        408 |    0.009 |     -38.5 | 31902/48345         |                        366 | 38%       |               0     |                -12.1 |
| 8     | GAP      |         96 |   -0.042 |     -12.2 | 10287/12337         |                      -1217 | 29%       |               0.007 |                -17.4 |
| 8     | PRE      |        465 |   -0.008 |     -12.4 | 19128/22932         |                       -415 | 39%       |              -0.008 |                 -0.9 |
| 8     | XP       |        412 |    0.011 |     -28.4 | 28757/35276         |                        -23 | 50%       |               0.001 |                -16.7 |
| 8     | POOLED   |       1980 |    0.001 |     -30   | 57443/74495         |                       -120 | 42%       |              -0.003 |                 -9.6 |
| 9     | L3M      |        227 |    0.002 |     -10.2 | 29307/32328         |                         69 | 55%       |               0.007 |                -13.7 |
| 9     | L6M      |        542 |   -0.003 |      -9.5 | 63780/68577         |                         20 | 52%       |               0.001 |                -18.8 |
| 9     | HOLD     |        408 |    0.027 |     -44.6 | 27807/48345         |                        655 | 58%       |              -0.004 |                 -2   |
| 9     | GAP      |         96 |   -0.024 |      -3.1 | 12092/12337         |                       -728 | 15%       |               0.011 |                -28.9 |
| 9     | PRE      |        465 |    0     |     -11.4 | 20544/22932         |                       -188 | 47%       |              -0.004 |                  9.3 |
| 9     | XP       |        412 |    0.011 |     -40.1 | 23632/35276         |                         30 | 52%       |               0.006 |                -12.4 |
| 9     | POOLED   |       1980 |    0.005 |     -27.6 | 63780/74495         |                        -21 | 48%       |              -0.002 |                  0.5 |
| 10    | L3M      |        227 |   -0.003 |      -1.2 | 31739/32328         |                        -83 | 33%       |              -0.004 |                 -2.8 |
| 10    | L6M      |        542 |   -0.001 |      -1   | 67871/68577         |                        -11 | 58%       |              -0.006 |                  1   |
| 10    | HOLD     |        408 |   -0.004 |       1.6 | 50652/48345         |                        -75 | 46%       |              -0.003 |                  0.3 |
| 10    | GAP      |         96 |    0.003 |      -1.2 | 11672/12337         |                        -39 | 33%       |              -0     |                 -2.7 |
| 10    | PRE      |        465 |   -0.004 |       2.9 | 24034/22932         |                        -80 | 32%       |              -0.006 |                  0.2 |
| 10    | XP       |        412 |    0.012 |      -8.1 | 33076/35276         |                        103 | 63%       |               0.014 |                -11.9 |
| 10    | POOLED   |       1980 |    0.001 |       0.2 | 75496/74495         |                          6 | 51%       |              -0.001 |                  1.4 |

## Time thirds (2023-10..2024-09, 2024-10..2025-09, 2025-10..2026-10), N=5, 6M, g15, next 2 weeks
| set   | T1                    | T2                    | T3                    |
|:------|:----------------------|:----------------------|:----------------------|
| ALL   | -0.002 R / -11.5% ulc | -0.007 R / +8.6% ulc  | +0.005 R / -35.6% ulc |
| 1     | +0.001 R / -21.4% ulc | -0.012 R / +15.9% ulc | +0.008 R / -42.4% ulc |
| 2     | -0.000 R / -15.7% ulc | -0.006 R / -7.4% ulc  | +0.008 R / -30.0% ulc |
| 3     | +0.035 R / -38.4% ulc | -0.006 R / -7.1% ulc  | +0.003 R / +0.0% ulc  |
| 4     | +0.045 R / -53.7% ulc | -0.020 R / +60.0% ulc | -0.002 R / -8.3% ulc  |
| 5     | -0.006 R / -16.9% ulc | +0.003 R / -23.7% ulc | +0.002 R / -32.4% ulc |
| 6     | -0.012 R / -9.0% ulc  | +0.009 R / -14.3% ulc | +0.005 R / -16.8% ulc |
| 7     | -0.005 R / +0.4% ulc  | +0.019 R / -5.5% ulc  | -0.009 R / +22.6% ulc |
| 8     | +0.010 R / -28.1% ulc | -0.011 R / -12.8% ulc | +0.004 R / -32.4% ulc |
| 9     | +0.016 R / -39.6% ulc | -0.006 R / -13.5% ulc | +0.006 R / -25.2% ulc |
| 10    | +0.012 R / -7.9% ulc  | -0.001 R / +3.7% ulc  | -0.001 R / +2.5% ulc  |
| 1a    | +0.002 R / +0.5% ulc  | -0.002 R / -43.0% ulc | +0.004 R / -35.5% ulc |
| 1b    | -0.012 R / -1.3% ulc  | +0.014 R / -31.8% ulc | +0.001 R / -25.2% ulc |
| 1c    | -0.000 R / +8.6% ulc  | +0.011 R / -20.4% ulc | +0.011 R / -25.4% ulc |
| 1d    | +0.027 R / -50.9% ulc | +0.010 R / -28.1% ulc | +0.027 R / -47.3% ulc |
| 1e    | +0.021 R / -36.9% ulc | +0.011 R / +13.6% ulc | +0.002 R / -21.5% ulc |
| 1f    | -0.007 R / -15.3% ulc | -0.003 R / -33.7% ulc | +0.004 R / -36.4% ulc |
| 1g    | -0.006 R / -24.2% ulc | -0.013 R / +29.1% ulc | +0.006 R / -38.0% ulc |
| 1h    | +0.010 R / -18.3% ulc | -0.005 R / -21.8% ulc | +0.012 R / -32.0% ulc |
| 5a    | -0.026 R / -16.0% ulc | +0.012 R / -35.3% ulc | +0.012 R / -49.6% ulc |
| 5b    | +0.002 R / -22.3% ulc | -0.013 R / -10.8% ulc | +0.009 R / -26.0% ulc |
| NONS  | -0.000 R / -31.7% ulc | +0.008 R / -33.7% ulc | +0.012 R / -33.8% ulc |
| RAND  | +0.004 R / -40.6% ulc | +0.004 R / -25.3% ulc | +0.007 R / -28.4% ulc |
| PLANT | +0.053 R / -44.7% ulc | +0.046 R / -30.7% ulc | +0.044 R / -44.6% ulc |

## Per book x session (ALL families pooled, N=5, 6M picks, g15, next 2 weeks) with shifted-label and random-skip nulls per cell
| cell (book_session)   |   trades OOS |   dMeanR |   dUlcer% | persist   |   shift dMeanR |   shift dUlcer% |   random-skip dMeanR |   random-skip dUlcer% | beats random dU/dm   |
|:----------------------|-------------:|---------:|----------:|:----------|---------------:|----------------:|---------------------:|----------------------:|:---------------------|
| H7_3                  |          356 |   -0.008 |     -18.6 | 42%       |         -0     |           -13.7 |                0.001 |                 -14.2 | 70%/10%              |
| K7_1                  |         1624 |    0.002 |     -32.6 | 46%       |         -0.003 |           -10.2 |               -0.003 |                 -19   | 90%/80%              |

Per cell by family (N=5, 6M, g15, 2 weeks): dMeanR / dUlcer% real vs shifted-label mean:
| cell   | 1                            | 2                            | 3                            | 4                            | 5                            | 6                            | 7                            | 8                            | 9                            | 10                           | ALL                          |
|:-------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|
| H7_3   | -0.007/-19% (sh +0.001/-21%) | +0.001/-15% (sh -0.012/-13%) | +0.013/-32% (sh +0.014/-33%) | +0.005/-44% (sh +0.008/-30%) | +0.003/-21% (sh +0.011/-37%) | +0.022/-27% (sh -0.010/-20%) | +0.005/-3% (sh -0.015/+7%)   | +0.005/-30% (sh -0.010/-9%)  | +0.016/-29% (sh +0.022/-32%) | +0.008/-23% (sh -0.004/-24%) | -0.008/-19% (sh -0.000/-14%) |
| K7_1   | +0.002/-39% (sh +0.001/-22%) | +0.002/-30% (sh +0.001/-27%) | +0.004/-5% (sh -0.004/-2%)   | +0.002/-6% (sh +0.001/-13%)  | +0.000/-33% (sh -0.002/-19%) | -0.002/-17% (sh +0.006/-42%) | -0.005/+17% (sh +0.006/-17%) | -0.000/-31% (sh -0.001/-10%) | +0.002/-28% (sh -0.007/+3%)  | +0.000/+0% (sh +0.000/+0%)   | +0.002/-33% (sh -0.003/-10%) |

## Persistence, turnover and decay of the picks (ALL families pooled, N=5, 6M, g15)
Turnover: mean share of the top-5 list retained from one refit to the next (higher = more stable picks): H7_3 24%, K7_1 28%; overall 26%.
Decay: summed gain/loss ($, base lots, $4.84) of the picks by how many 2-week blocks after the refit they are traded (0 = the next 2 weeks):
| set   | labels   | lag 0 (0-13 d)             | lag 1 (14-27 d)            | lag 2 (28-41 d)            | lag 3 (42-55 d)            | lag 4 (56-69 d)            | lag 5 (70-83 d)            |
|:------|:---------|:---------------------------|:---------------------------|:---------------------------|:---------------------------|:---------------------------|:---------------------------|
| ALL   | real     | -28232$ (46% of pieces >0) | -9209$ (42% of pieces >0)  | -42375$ (44% of pieces >0) | -17364$ (44% of pieces >0) | -33099$ (45% of pieces >0) | -10270$ (45% of pieces >0) |
| ALL   | shift11  | -29579$ (45% of pieces >0) | -43186$ (45% of pieces >0) | -14040$ (40% of pieces >0) | -31782$ (44% of pieces >0) | -29665$ (44% of pieces >0) | -12486$ (45% of pieces >0) |
| 1     | real     | -28168$ (44% of pieces >0) | -18152$ (44% of pieces >0) | -44316$ (40% of pieces >0) | -27184$ (45% of pieces >0) | -33794$ (45% of pieces >0) | -4840$ (49% of pieces >0)  |
| 1     | shift11  | -19914$ (44% of pieces >0) | -53733$ (40% of pieces >0) | -39362$ (39% of pieces >0) | -28872$ (44% of pieces >0) | -23142$ (40% of pieces >0) | -31040$ (40% of pieces >0) |
| 2     | real     | -16374$ (49% of pieces >0) | -28634$ (43% of pieces >0) | -24326$ (45% of pieces >0) | -24428$ (44% of pieces >0) | -17985$ (45% of pieces >0) | -11890$ (41% of pieces >0) |
| 2     | shift11  | -38377$ (44% of pieces >0) | -35631$ (45% of pieces >0) | -4090$ (43% of pieces >0)  | -196$ (50% of pieces >0)   | -38828$ (47% of pieces >0) | -24101$ (52% of pieces >0) |
| 3     | real     | 14470$ (44% of pieces >0)  | -6795$ (44% of pieces >0)  | -16119$ (42% of pieces >0) | -26320$ (40% of pieces >0) | -22026$ (41% of pieces >0) | -3200$ (44% of pieces >0)  |
| 3     | shift11  | -24698$ (35% of pieces >0) | -921$ (39% of pieces >0)   | 26$ (41% of pieces >0)     | -10533$ (42% of pieces >0) | -9717$ (41% of pieces >0)  | -8096$ (40% of pieces >0)  |
| 5     | real     | -27618$ (46% of pieces >0) | -32756$ (44% of pieces >0) | 1196$ (44% of pieces >0)   | -15850$ (45% of pieces >0) | -11019$ (39% of pieces >0) | -24649$ (46% of pieces >0) |
| 5     | shift11  | -53409$ (42% of pieces >0) | -46901$ (46% of pieces >0) | -28432$ (47% of pieces >0) | -37507$ (47% of pieces >0) | -44985$ (44% of pieces >0) | -19409$ (43% of pieces >0) |
| 7     | real     | -24784$ (50% of pieces >0) | -19662$ (47% of pieces >0) | -4654$ (44% of pieces >0)  | -19976$ (40% of pieces >0) | -1264$ (48% of pieces >0)  | -7925$ (51% of pieces >0)  |
| 7     | shift11  | 6302$ (43% of pieces >0)   | -19767$ (40% of pieces >0) | -22705$ (47% of pieces >0) | -30171$ (40% of pieces >0) | -7049$ (44% of pieces >0)  | -13862$ (42% of pieces >0) |
| 10    | real     | 940$ (48% of pieces >0)    | -4165$ (45% of pieces >0)  | -6263$ (42% of pieces >0)  | -4283$ (42% of pieces >0)  | -4574$ (38% of pieces >0)  | -3793$ (39% of pieces >0)  |
| 10    | shift11  | -5547$ (39% of pieces >0)  | -4303$ (45% of pieces >0)  | -6372$ (44% of pieces >0)  | -4193$ (45% of pieces >0)  | -2257$ (45% of pieces >0)  | -3568$ (46% of pieces >0)  |
| NONS  | real     | -9840$ (46% of pieces >0)  | -178$ (46% of pieces >0)   | -24657$ (44% of pieces >0) | -28925$ (43% of pieces >0) | -48461$ (42% of pieces >0) | -56044$ (43% of pieces >0) |
| NONS  | shift11  | -48449$ (42% of pieces >0) | -48771$ (46% of pieces >0) | -37700$ (47% of pieces >0) | -40197$ (49% of pieces >0) | -39085$ (46% of pieces >0) | -15563$ (43% of pieces >0) |

## SCORES (equal-weight vote of the top 5 / top 10 recent conditions; g15 picks; rule = trade by thirds of the vote, next 2 weeks chained, 6M picks)
| set   |   K | rule       |   dMeanR |   dUlcer% |   d$/wk | persist   |   shift dMeanR |   shift dUlcer% | beats 3 shifts   |
|:------|----:|:-----------|---------:|----------:|--------:|:----------|---------------:|----------------:|:-----------------|
| ALL   |   5 | skip_low   |    0.013 |     -37.5 |    -105 | 48%       |          0.001 |           -20.9 | no               |
| ALL   |   5 | half_low   |    0.004 |     -27.8 |     -53 | 46%       |          0     |           -17.6 | no               |
| ALL   |   5 | boost_high |   -0     |      23.2 |     166 | 44%       |         -0.001 |            34.9 | no               |
| ALL   |  10 | skip_low   |    0.014 |     -14   |      49 | 51%       |         -0.016 |             3.9 | no               |
| ALL   |  10 | half_low   |    0.005 |     -21   |      25 | 49%       |         -0.006 |            -2.8 | yes              |
| ALL   |  10 | boost_high |   -0.001 |      24.1 |     114 | 44%       |         -0.006 |            43.4 | yes              |
| 1     |   5 | skip_low   |    0.015 |     -23.7 |     -93 | 50%       |         -0.001 |           -13.6 | no               |
| 1     |   5 | half_low   |    0.005 |     -34.2 |     -46 | 48%       |         -0     |           -15.2 | yes              |
| 1     |   5 | boost_high |   -0.003 |      17   |      57 | 42%       |         -0     |            29.7 | no               |
| 1     |  10 | skip_low   |    0.014 |     -32.3 |     -31 | 49%       |         -0.028 |            40.1 | yes              |
| 1     |  10 | half_low   |    0.005 |     -28.7 |     -15 | 47%       |         -0.011 |             0.9 | yes              |
| 1     |  10 | boost_high |    0.002 |      20.2 |     181 | 46%       |         -0.005 |            39.9 | yes              |
| 2     |   5 | skip_low   |   -0.007 |       2.5 |    -336 | 44%       |          0.004 |           -22.4 | no               |
| 2     |   5 | half_low   |   -0.002 |      -4.2 |    -168 | 43%       |          0.001 |           -23.2 | no               |
| 2     |   5 | boost_high |    0.003 |      24.7 |     315 | 46%       |         -0.001 |            23.7 | no               |
| 2     |  10 | skip_low   |    0.003 |     -17.6 |    -243 | 43%       |         -0     |           -11.7 | no               |
| 2     |  10 | half_low   |    0.001 |     -28.1 |    -121 | 43%       |         -0     |           -18.4 | no               |
| 2     |  10 | boost_high |    0.001 |      17.5 |     187 | 47%       |          0     |            13.3 | no               |
| 3     |   5 | skip_low   |    0.001 |     -12   |    -114 | 46%       |         -0.008 |             1.1 | no               |
| 3     |   5 | half_low   |    0     |      -9   |     -57 | 43%       |         -0.004 |            -1.2 | no               |
| 3     |   5 | boost_high |    0.001 |      10.1 |      67 | 43%       |          0.004 |             6   | no               |
| 3     |  10 | skip_low   |    0.001 |     -12   |    -114 | 46%       |         -0.009 |             1.3 | yes              |
| 3     |  10 | half_low   |    0     |      -9   |     -57 | 43%       |         -0.004 |            -1.1 | yes              |
| 3     |  10 | boost_high |    0.001 |      10.1 |      67 | 43%       |          0.004 |             6.4 | no               |
| 5     |   5 | skip_low   |    0.007 |     -33.7 |    -306 | 46%       |          0.006 |           -23.2 | no               |
| 5     |   5 | half_low   |    0.002 |     -27.9 |    -153 | 44%       |          0.002 |           -15.7 | no               |
| 5     |   5 | boost_high |   -0     |      15.1 |     141 | 43%       |          0     |            35.8 | no               |
| 5     |  10 | skip_low   |   -0.004 |     -31.6 |    -312 | 45%       |          0.004 |           -15.2 | no               |
| 5     |  10 | half_low   |   -0.001 |     -23.1 |    -156 | 43%       |          0.002 |           -16.2 | no               |
| 5     |  10 | boost_high |    0.002 |      10   |     182 | 48%       |          0     |            38.7 | no               |
| 7     |   5 | skip_low   |   -0.01  |      49.7 |    -351 | 46%       |          0.001 |           -14   | no               |
| 7     |   5 | half_low   |   -0.004 |      16.8 |    -176 | 44%       |          0     |           -13.1 | no               |
| 7     |   5 | boost_high |    0     |      43.2 |      89 | 41%       |          0.001 |            28   | no               |
| 7     |  10 | skip_low   |   -0.014 |      42.3 |    -540 | 52%       |         -0.004 |           -16   | no               |
| 7     |  10 | half_low   |   -0.006 |      12.3 |    -270 | 48%       |         -0.002 |           -13.2 | no               |
| 7     |  10 | boost_high |   -0     |      36.1 |      40 | 47%       |          0.001 |            30.1 | no               |
| 10    |   5 | skip_low   |   -0.001 |      -3   |     -50 | 45%       |          0.002 |            -1.3 | no               |
| 10    |   5 | half_low   |   -0.001 |      -1.9 |     -25 | 41%       |          0.001 |            -1.1 | no               |
| 10    |   5 | boost_high |    0.001 |      -1.8 |      29 | 46%       |         -0.001 |             1.9 | yes              |
| 10    |  10 | skip_low   |   -0.001 |      -1.5 |     -37 | 48%       |          0     |            -1   | no               |
| 10    |  10 | half_low   |   -0     |      -1.1 |     -18 | 46%       |          0     |            -0.9 | no               |
| 10    |  10 | boost_high |    0.001 |       0.2 |      30 | 44%       |          0     |             1   | no               |
| 1c    |   5 | skip_low   |    0.025 |      -3   |     -15 | 51%       |         -0.015 |             0.8 | no               |
| 1c    |   5 | half_low   |    0.009 |      -6.2 |      -7 | 47%       |         -0.005 |            -6   | no               |
| 1c    |   5 | boost_high |    0.003 |      39.5 |     253 | 46%       |         -0.005 |            39.1 | no               |
| 1c    |  10 | skip_low   |    0.002 |      -4.6 |    -344 | 49%       |          0.011 |           -20.7 | no               |
| 1c    |  10 | half_low   |    0.001 |     -10.1 |    -172 | 46%       |          0.004 |           -18.8 | no               |
| 1c    |  10 | boost_high |    0.006 |      18.1 |     331 | 52%       |         -0     |            26.2 | no               |
| 1d    |   5 | skip_low   |    0.04  |     -41.8 |     257 | 58%       |          0.007 |            -0.4 | no               |
| 1d    |   5 | half_low   |    0.014 |     -30   |     129 | 54%       |          0.003 |            -9.7 | yes              |
| 1d    |   5 | boost_high |    0.008 |       6.9 |     410 | 51%       |         -0     |            35   | yes              |
| 1d    |  10 | skip_low   |    0.027 |      -8.4 |      80 | 56%       |          0.012 |           -15   | no               |
| 1d    |  10 | half_low   |    0.01  |      -9.8 |      40 | 53%       |          0.004 |           -13.4 | no               |
| 1d    |  10 | boost_high |    0.004 |      12.6 |     279 | 54%       |          0.002 |            21.4 | no               |
| 1e    |   5 | skip_low   |    0.018 |      -7.5 |     -90 | 56%       |          0.007 |           -21.2 | no               |
| 1e    |   5 | half_low   |    0.007 |     -13.5 |     -45 | 53%       |          0.002 |           -18   | no               |
| 1e    |   5 | boost_high |    0.002 |      22.1 |     225 | 49%       |          0     |            27.3 | no               |
| 1e    |  10 | skip_low   |    0.02  |     -11.5 |     -29 | 57%       |         -0     |           -10.9 | no               |
| 1e    |  10 | half_low   |    0.008 |     -14.6 |     -15 | 55%       |         -0     |           -14   | no               |
| 1e    |  10 | boost_high |    0.004 |      20.1 |     251 | 55%       |         -0.003 |            32.1 | no               |
| 5a    |   5 | skip_low   |    0.019 |     -41.1 |     -33 | 48%       |         -0.009 |            13.7 | yes              |
| 5a    |   5 | half_low   |    0.007 |     -29.3 |     -17 | 47%       |         -0.003 |            -7.5 | yes              |
| 5a    |   5 | boost_high |    0.001 |      11.3 |     223 | 44%       |          0     |            30.7 | no               |
| 5a    |  10 | skip_low   |    0.024 |     -54.6 |     107 | 53%       |         -0.004 |            11   | yes              |
| 5a    |  10 | half_low   |    0.009 |     -36.6 |      53 | 51%       |         -0.001 |            -4.7 | yes              |
| 5a    |  10 | boost_high |    0     |      16.2 |     182 | 46%       |          0.001 |            20.4 | no               |
| 5b    |   5 | skip_low   |    0.015 |     -23.1 |    -161 | 52%       |          0.007 |           -20.4 | no               |
| 5b    |   5 | half_low   |    0.005 |     -21.2 |     -80 | 50%       |          0.002 |           -17.9 | no               |
| 5b    |   5 | boost_high |    0.004 |      22.4 |     249 | 52%       |          0     |            33.1 | no               |
| 5b    |  10 | skip_low   |    0.034 |     -42   |     132 | 52%       |         -0.003 |           -11.8 | yes              |
| 5b    |  10 | half_low   |    0.011 |     -30.6 |      66 | 50%       |         -0.001 |           -17.1 | yes              |
| 5b    |  10 | boost_high |    0.005 |      15.4 |     320 | 49%       |          0.003 |            23.2 | no               |
| NONS  |   5 | skip_low   |    0.035 |     -42.9 |     206 | 54%       |          0.002 |             3.5 | yes              |
| NONS  |   5 | half_low   |    0.012 |     -26.4 |     103 | 51%       |          0.001 |           -14.7 | yes              |
| NONS  |   5 | boost_high |    0.007 |      21   |     451 | 53%       |          0.002 |            24.7 | no               |
| NONS  |  10 | skip_low   |    0.045 |     -25.7 |     336 | 53%       |          0.002 |           -10.3 | no               |
| NONS  |  10 | half_low   |    0.015 |     -17.1 |     168 | 51%       |          0.001 |           -20.5 | no               |
| NONS  |  10 | boost_high |    0.006 |      26.7 |     340 | 52%       |          0.001 |            19.5 | no               |
| RAND  |   5 | skip_low   |    0.01  |     -25.9 |    -241 | 46%       |          0.008 |           -11.9 | no               |
| RAND  |   5 | half_low   |    0.004 |     -22.1 |    -120 | 44%       |          0.003 |           -13.9 | no               |
| RAND  |   5 | boost_high |    0.003 |      13.9 |     218 | 46%       |          0.001 |            35   | no               |
| RAND  |  10 | skip_low   |    0.019 |     -38.6 |    -115 | 52%       |          0.008 |           -25.5 | no               |
| RAND  |  10 | half_low   |    0.006 |     -27.1 |     -57 | 49%       |          0.003 |           -21.7 | no               |
| RAND  |  10 | boost_high |    0.002 |      17   |     176 | 49%       |          0.002 |            21.7 | no               |
| PLANT |   5 | skip_low   |    0.446 |     -93.1 |    5198 | 83%       |         -0.152 |           567.1 | yes              |
| PLANT |   5 | half_low   |    0.135 |     -83   |    2599 | 77%       |         -0.058 |           170.5 | yes              |
| PLANT |   5 | boost_high |    0.083 |     -59.4 |    2972 | 79%       |         -0.031 |           127.5 | yes              |
| PLANT |  10 | skip_low   |    0.355 |     -92   |    5219 | 81%       |         -0.153 |           567.3 | yes              |
| PLANT |  10 | half_low   |    0.125 |     -79.9 |    2610 | 75%       |         -0.058 |           170.5 | yes              |
| PLANT |  10 | boost_high |    0.08  |     -56.2 |    2943 | 76%       |         -0.031 |           127.7 | yes              |

Vote in thirds on the next 2 weeks (K=5; thirds cut at the pick-window terciles of the vote; real labels vs the shifted-label procedure):
| set   | labels   | low: share, meanR   | mid: share, meanR   | high: share, meanR   |   high-low meanR |
|:------|:---------|:--------------------|:--------------------|:---------------------|-----------------:|
| ALL   | real     | 46%, +0.015         | 11%, +0.098         | 43%, +0.028          |            0.014 |
| ALL   | shift11  | 44%, +0.012         | 10%, +0.135         | 46%, +0.024          |            0.012 |
| ALL   | shift23  | 46%, +0.043         | 7%, +0.030          | 47%, +0.016          |           -0.028 |
| ALL   | shift37  | 45%, +0.030         | 7%, +0.029          | 48%, +0.029          |           -0.001 |
| 1     | real     | 46%, +0.012         | 13%, +0.151         | 41%, +0.010          |           -0.001 |
| 1     | shift11  | 45%, +0.017         | 7%, +0.004          | 48%, +0.046          |            0.029 |
| 1     | shift23  | 46%, +0.041         | 7%, -0.059          | 48%, +0.031          |           -0.011 |
| 1     | shift37  | 45%, +0.033         | 6%, +0.166          | 49%, +0.009          |           -0.024 |
| 3     | real     | 18%, +0.026         | 68%, +0.030         | 14%, +0.048          |            0.022 |
| 3     | shift11  | 19%, +0.139         | 71%, -0.008         | 9%, +0.145           |            0.007 |
| 3     | shift23  | 26%, +0.056         | 58%, +0.003         | 16%, +0.073          |            0.017 |
| 3     | shift37  | 26%, +0.025         | 48%, -0.002         | 25%, +0.083          |            0.058 |
| 5     | real     | 51%, +0.023         | 7%, +0.082          | 42%, +0.029          |            0.006 |
| 5     | shift11  | 46%, +0.044         | 8%, -0.066          | 46%, +0.033          |           -0.011 |
| 5     | shift23  | 49%, +0.021         | 9%, +0.082          | 43%, +0.029          |            0.008 |
| 5     | shift37  | 48%, +0.005         | 9%, +0.132          | 43%, +0.034          |            0.03  |
| 7     | real     | 43%, +0.048         | 18%, +0.042         | 39%, +0.033          |           -0.015 |
| 7     | shift11  | 40%, +0.010         | 23%, +0.075         | 37%, +0.053          |            0.043 |
| 7     | shift23  | 46%, +0.067         | 8%, +0.065          | 46%, +0.011          |           -0.057 |
| 7     | shift37  | 45%, +0.002         | 11%, +0.185         | 44%, +0.046          |            0.045 |
| 10    | real     | 42%, +0.047         | 13%, -0.110         | 45%, +0.051          |            0.004 |
| 10    | shift11  | 41%, +0.037         | 15%, +0.073         | 44%, +0.004          |           -0.034 |
| 10    | shift23  | 42%, -0.026         | 16%, +0.194         | 41%, +0.029          |            0.055 |
| 10    | shift37  | 43%, +0.015         | 17%, +0.114         | 41%, +0.007          |           -0.007 |

## HONEST WAIT-THEN-ENTER / EARLY-EXIT versions of the delayed flow columns (rolling rule; 1,241 delayed columns x yes/no x {wait-then-enter, early exit}; N picks equal-split)
Wait-then-enter: wait D = 5/30/60/120 s, enter at +D only when the column is at its picked state, same stop/target distances from the new entry, trades already closed inside the wait are not entered. Early exit: entered at the signal, exit at the mark at +D when the column is at its picked state. dMeanR is per trade actually taken (wait rules take fewer trades: see the shift nulls, which have the same exposure drop).
| picks on   | gate   |   N |   dMeanR |   dUlcer% |   d$/wk | persist   |   shift dMeanR |   shift dUlcer% |   random-flag dMeanR |   random-flag dUlcer% | beats random dU/dm   |
|:-----------|:-------|----:|---------:|----------:|--------:|:----------|---------------:|----------------:|---------------------:|----------------------:|:---------------------|
| 6M         | g15    |   1 |   -0.001 |     -28.7 |  -13842 | 51%       |          0.002 |           -36.1 |               -0.001 |                 -17.1 | 30%/50%              |
| 6M         | g15    |   3 |   -0.006 |     -34   |  -13482 | 49%       |         -0.008 |           -57.5 |               -0.005 |                 -60.8 | 0%/40%               |
| 6M         | g15    |   5 |   -0.007 |     -59.4 |  -13499 | 50%       |         -0.009 |           -65.4 |               -0.005 |                 -72.1 | 0%/50%               |
| 6M         | g15    |  10 |   -0.003 |     -64.8 |  -13117 | 52%       |         -0.006 |           -68.1 |               -0.007 |                 -76.9 | 0%/90%               |
| 6M         | g30    |   1 |   -0.003 |     -30.3 |  -13720 | 51%       |          0     |           -34.5 |                      |                       |                      |
| 6M         | g30    |   3 |   -0.011 |     -42.4 |  -13752 | 49%       |         -0.007 |           -58.4 |                      |                       |                      |
| 6M         | g30    |   5 |   -0.009 |     -55.5 |  -13743 | 48%       |         -0.009 |           -60.9 |                      |                       |                      |
| 6M         | g30    |  10 |   -0.005 |     -59.2 |  -13365 | 50%       |         -0.005 |           -67.8 |                      |                       |                      |
| 3M         | g15    |   1 |   -0.013 |     -26.7 |  -13603 | 48%       |         -0.011 |            -2.1 |                      |                       |                      |
| 3M         | g15    |   3 |   -0.004 |     -55.2 |  -13130 | 50%       |         -0.012 |           -54.1 |                      |                       |                      |
| 3M         | g15    |   5 |   -0.009 |     -59.5 |  -13293 | 49%       |         -0.012 |           -60.7 |                      |                       |                      |
| 3M         | g15    |  10 |   -0.008 |     -70   |  -12865 | 49%       |         -0.011 |           -64.6 |                      |                       |                      |
| 3M         | g30    |   1 |   -0.001 |     -27.1 |  -13016 | 50%       |         -0.001 |           -22.5 |                      |                       |                      |
| 3M         | g30    |   3 |   -0     |     -57.5 |  -12801 | 50%       |         -0.014 |           -51.7 |                      |                       |                      |
| 3M         | g30    |   5 |   -0.002 |     -65.1 |  -12938 | 49%       |         -0.013 |           -63.2 |                      |                       |                      |
| 3M         | g30    |  10 |   -0.006 |     -64.8 |  -12739 | 49%       |         -0.01  |           -65.8 |                      |                       |                      |

Current wait / early-exit picks (g15, top 3 per cell):
| cell   |   rank | pick                                                     |   6M dMeanR |   6M dUlcer% | share   | feed      | D7 live                                   |
|:-------|-------:|:---------------------------------------------------------|------------:|-------------:|:--------|:----------|:------------------------------------------|
| A7_0   |      1 | WAIT 120 s then enter only if fl088_d120 is YES          |       0.219 |        -86   | 17%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| A7_0   |      2 | WAIT 5 s then enter only if fl102_d5 is YES              |       0.179 |        -77.3 | 26%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| A7_0   |      3 | WAIT 5 s then enter only if fl246_d5 is YES              |       0.235 |        -72.3 | 22%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| H7_0   |      1 | WAIT 60 s then enter only if fl134_d60 is YES            |       0.384 |        -93.6 | 16%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| H7_0   |      2 | WAIT 30 s then enter only if fl085_d30 is YES            |       0.52  |        -89.5 | 13%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| H7_0   |      3 | WAIT 120 s then enter only if fl088_d120 is YES          |       0.315 |        -91.6 | 20%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| H7_3   |      1 | WAIT 60 s then enter only if fl131_d60 is YES            |       0.308 |        -81   | 23%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| H7_3   |      2 | WAIT 60 s then enter only if fl047_d60 is YES            |       0.274 |        -80   | 28%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| H7_3   |      3 | WAIT 5 s then enter only if fl176_d5 is YES              |       0.311 |        -73   | 25%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| K7_0   |      1 | WAIT 5 s then enter only if fl150_d5 is YES              |       0.138 |        -89.2 | 17%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| K7_0   |      2 | WAIT 5 s then enter only if fl016_d5 is YES              |       0.142 |        -88   | 18%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| K7_0   |      3 | WAIT 30 s then enter only if fl095_d30 is YES            |       0.125 |        -83   | 22%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| K7_1   |      1 | WAIT 120 s then enter only if fl187_d120 is YES          |       0.138 |        -90.1 | 24%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| K7_1   |      2 | WAIT 60 s then enter only if fl237_d60 is YES            |       0.129 |        -88.9 | 14%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| K7_1   |      3 | WAIT 30 s then enter only if fl044_d30 is YES            |       0.132 |        -85.3 | 34%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| K7_3   |      1 | WAIT 5 s then enter only if fl212_d5 is YES              |       0.403 |        -96   | 15%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| K7_3   |      2 | WAIT 5 s then enter only if fl088_d5 is YES              |       0.279 |        -95.6 | 18%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| K7_3   |      3 | WAIT 60 s then enter only if fl148_d60 is YES            |       0.334 |        -92.9 | 13%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| K7_4   |      1 | WAIT 120 s then enter only if fl197_d120 is YES          |       0.161 |        -90.8 | 15%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| K7_4   |      2 | WAIT 5 s then enter only if c_N_se_d7_after_win60 is YES |       0.142 |        -83.4 | 19%     | no        | prints: computable                        |
| K7_4   |      3 | WAIT 60 s then enter only if fl203_d60 is YES            |       0.193 |        -80.4 | 15%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| M7_1   |      1 | WAIT 60 s then enter only if fl131_d60 is YES            |       0.132 |        -88.1 | 19%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| M7_1   |      2 | WAIT 5 s then enter only if fl055_d5 is YES              |       0.105 |        -90.2 | 15%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| M7_1   |      3 | WAIT 30 s then enter only if fl091_d30 is YES            |       0.116 |        -87.7 | 14%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| M7_3   |      1 | WAIT 5 s then enter only if fl015_d5 is YES              |       0.393 |        -91.3 | 18%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| M7_3   |      2 | WAIT 120 s then enter only if fl029_d120 is YES          |       0.248 |        -90.1 | 17%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| M7_3   |      3 | WAIT 60 s then enter only if fl161_d60 is YES            |       0.277 |        -85.8 | 13%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| O7_3   |      1 | WAIT 120 s then enter only if fl164_d120 is YES          |       0.789 |        -92.2 | 16%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| O7_3   |      2 | WAIT 30 s then enter only if fl233_d30 is YES            |       0.72  |        -94.9 | 14%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| O7_3   |      3 | WAIT 5 s then enter only if fl112_d5 is YES              |       0.932 |        -89   | 25%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| P7_0   |      1 | WAIT 120 s then enter only if fl164_d120 is YES          |       0.195 |        -82.6 | 16%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| P7_0   |      2 | WAIT 60 s then enter only if fl278_d60 is YES            |       0.184 |        -81.1 | 13%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| P7_0   |      3 | WAIT 5 s then enter only if fl192_d5 is YES              |       0.168 |        -72.6 | 13%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| P7_1   |      1 | WAIT 60 s then enter only if fl134_d60 is YES            |       0.268 |        -86.5 | 14%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| P7_1   |      2 | WAIT 5 s then enter only if fl151_d5 is YES              |       0.197 |        -84.4 | 13%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| P7_1   |      3 | WAIT 60 s then enter only if fl267_d60 is YES            |       0.137 |        -77.4 | 18%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| P7_3   |      1 | WAIT 5 s then enter only if fl247_d5 is YES              |       0.231 |        -90.8 | 13%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| P7_3   |      2 | WAIT 5 s then enter only if fl055_d5 is YES              |       0.181 |        -87.9 | 24%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| P7_3   |      3 | WAIT 30 s then enter only if fl139_d30 is YES            |       0.151 |        -90.8 | 14%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| U7_0   |      1 | WAIT 5 s then enter only if fl136_d5 is YES              |       0.336 |        -67.8 | 21%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| U7_0   |      2 | WAIT 5 s then enter only if fl087_d5 is YES              |       0.278 |        -67.4 | 13%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| U7_0   |      3 | WAIT 5 s then enter only if fl274_d5 is YES              |       0.228 |        -70.7 | 19%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| U7_1   |      1 | WAIT 120 s then enter only if fl073_d120 is YES          |       0.438 |        -84.4 | 17%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| U7_1   |      2 | WAIT 120 s then enter only if fl061_d120 is YES          |       0.529 |        -82.6 | 17%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |
| U7_1   |      3 | WAIT 120 s then enter only if fl024_d120 is YES          |       0.501 |        -82.8 | 18%     | mostly L3 | NO today (needs the delayed flow/L3 feed) |

## CURRENT PICKS (refit ending 2026-10-30; pick window trailing 6M 2026-05-01..2026-10-30, trailing 3M 2026-08-01..; data end 2026-10-30)
Each row: the rule in plain words, its effect on the pick window (6M and 3M: dMeanR in R, dUlcer% vs doing nothing), the share of trades it acts on, the prior-year check (GREEN <=15%, AMBER 15-30%, RED >30% worse than doing nothing on ulcer / mean in the worst prior 365-day block), feed needs, whether D7 can compute it live. ALL families pooled, gate 15% (strict) and 30%. Where the 6M and 3M numbers disagree in sign the pick is fragile. Prior-year reading: "ulcer +x%" = x% WORSE than doing nothing; "mean -x%" = mean R x% worse than doing nothing (a plus = better). Name decoder: c4_/n_/m_ = confluence-library or entry-table column (indicator token, bar token, state token); bar tokens ha1/ha3/ha5/ha15/ha60 = Heikin-Ashi bars of that many minutes, range8/range16 = range bars, renko8/renko16, tick2000, vol500/vol2000 = volume bars, 1m/3m/5m/15m/60m/1d = time frame; rise/fall = indicator rising/falling; with/against = in/against the trade direction; the column list with definitions is in the stage-1 store (/mnt/l2/l2vast/_s1r/cols.parquet).

Gate 15% (top 5 per book x session):
| cell   |   rank | pick                                                          | fam   |   6M dMeanR |   6M dUlcer% |   3M dMeanR |   3M dUlcer% | share of trades acted on   | prior years                           | feed                              | D7 live                                                                              |
|:-------|-------:|:--------------------------------------------------------------|:------|------------:|-------------:|------------:|-------------:|:---------------------------|:--------------------------------------|:----------------------------------|:-------------------------------------------------------------------------------------|
| A7_0   |      1 | SKIP the trade when c4_rfilt_ha5_rise is YES                  | 1g    |       0.119 |        -73.2 |       0.075 |        -68.5 | 50%                        | GREEN (<=15%: ulcer +10%, mean -8%)   | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| A7_0   |      2 | HALF size when c4_sebF_1m_fresh5 is NO                        | 1d    |       0.048 |        -39.3 |       0.037 |        -44.5 | 47%                        | GREEN (<=15%: ulcer -2%, mean -14%)   | NQ bars                           | yes: own bars                                                                        |
| A7_0   |      3 | HALF size when c4_alligator_vol2000_hold3 is NO               | 1g    |       0.05  |        -41.4 |       0.058 |        -35.3 | 50%                        | GREEN (<=15%: ulcer -13%, mean -14%)  | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| A7_0   |      4 | HALF size when n_ks_peak14_1m_ewith is YES                    | 1a    |       0.042 |        -36.9 |       0.014 |        -23.8 | 40%                        | GREEN (<=15%: ulcer +1%, mean -11%)   | NQ bars                           | yes: own bars/session anchors                                                        |
| A7_0   |      5 | HALF size when c4_w1_ichi_fast_tkkj_range16_rise is YES       | 1g    |       0.048 |        -34.9 |       0.049 |        -16.7 | 48%                        | GREEN (<=15%: ulcer -6%, mean +4%)    | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| H7_0   |      1 | HALF size when c4_chopF_5m_rise is YES                        | 1c    |       0.086 |        -58.6 |       0.061 |        -49.6 | 46%                        | GREEN (<=15%: ulcer -0%, mean +6%)    | NQ bars                           | yes: own bars                                                                        |
| H7_0   |      2 | SKIP the trade when c4_cdl_60m_with_ge2 is NO                 | 2     |       0.178 |        -70.9 |       0.133 |        -48.3 | 49%                        | GREEN (<=15%: ulcer -19%, mean +25%)  | NQ bars                           | yes: own bars                                                                        |
| H7_0   |      3 | HALF size when m_volosc_3m_hi is NO                           | 1b    |       0.074 |        -45.2 |       0.054 |        -37.8 | 48%                        | GREEN (<=15%: ulcer -17%, mean +7%)   | NQ bars                           | yes: own bars                                                                        |
| H7_0   |      4 | SKIP the trade when fl280_v0 is YES                           | 5b    |       0.173 |        -76.7 |       0.081 |        -52.1 | 49%                        | GREEN (<=15%: ulcer -2%, mean +3%)    | L3 / L2 book                      | NO today: needs L3 order-by-order / L2 book (live book is polluted by ES/RTY levels) |
| H7_0   |      5 | HALF size when m_di21_1m_rise is YES                          | 1b    |       0.066 |        -50.7 |       0.038 |        -38.8 | 49%                        | GREEN (<=15%: ulcer -15%, mean +18%)  | NQ bars                           | yes: own bars                                                                        |
| H7_3   |      1 | HALF size when c_A_px_ema50_1d is NO                          | 1b    |       0.081 |        -53.5 |             |              | 47%                        | GREEN (<=15%: ulcer -20%, mean +66%)  | NQ bars                           | yes: own bars                                                                        |
| H7_3   |      2 | SKIP the trade when c_I_YM_conf5 is NO                        | 6     |       0.3   |        -75.6 |             |              | 47%                        | GREEN (<=15%: ulcer -23%, mean +45%)  | ES/RTY/YM/rates/other markets     | NO today: other-market feeds not on the D7 chart                                     |
| H7_3   |      3 | SKIP the trade when c4_w1_atr_pct250_renko8_hi is NO          | 1g    |       0.234 |        -67.4 |             |              | 47%                        | GREEN (<=15%: ulcer +2%, mean +6%)    | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| H7_3   |      4 | SKIP the trade when c4_ichiS_score_15m_fresh5 is YES          | 1d    |       0.285 |        -66.2 |             |              | 42%                        | GREEN (<=15%: ulcer -24%, mean +105%) | NQ bars                           | yes: own bars                                                                        |
| H7_3   |      5 | HALF size when c4_ob_dres_tick2000_hi is NO                   | 1g    |       0.077 |        -46.1 |             |              | 43%                        | GREEN (<=15%: ulcer +5%, mean -5%)    | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| K7_0   |      1 | HALF size when m_aroon25_3m_ewith is YES                      | 1b    |       0.032 |        -51.8 |       0.028 |        -43.7 | 36%                        | GREEN (<=15%: ulcer +10%, mean -15%)  | NQ bars                           | yes: own bars                                                                        |
| K7_0   |      2 | SKIP the trade when c4_w1_linreg_slope10_renko8_rise is NO    | 1g    |       0.097 |        -75.3 |       0.131 |        -72.9 | 49%                        | GREEN (<=15%: ulcer -26%, mean +8%)   | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| K7_0   |      3 | HALF size when c4_stA_vol2000_hold3 is NO                     | 1g    |       0.031 |        -46.1 |       0.055 |        -40.9 | 50%                        | GREEN (<=15%: ulcer -23%, mean +28%)  | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| K7_0   |      4 | HALF size when c4_agr_ichiS_kj_fresh5_ge3 is NO               | 1h    |       0.026 |        -43   |       0.027 |        -33.5 | 44%                        | GREEN (<=15%: ulcer -13%, mean +2%)   | NQ prints -> alt bars             | yes, same as 1g                                                                      |
| K7_0   |      5 | SKIP the trade when n_rk_310_fast_60m_side is NO              | 1a    |       0.078 |        -79.9 |       0.136 |        -79.3 | 47%                        | GREEN (<=15%: ulcer -40%, mean +27%)  | NQ bars                           | yes: own bars/session anchors                                                        |
| K7_1   |      1 | HALF size when n_bk_failbo_std_60m_against_state is YES       | 1a    |       0.038 |        -59.7 |       0.035 |        -46.1 | 38%                        | GREEN (<=15%: ulcer -11%, mean +9%)   | NQ bars                           | yes: own bars/session anchors                                                        |
| K7_1   |      2 | SKIP the trade when c4_don10_pos_1d_rise is YES               | 1d    |       0.093 |        -82.8 |       0.111 |        -72.5 | 50%                        | GREEN (<=15%: ulcer +5%, mean +42%)   | NQ bars                           | yes: own bars                                                                        |
| K7_1   |      3 | HALF size when c4_w1_di21_ha60_rise is NO                     | 1g    |       0.036 |        -61.7 |       0.019 |        -21.5 | 43%                        | GREEN (<=15%: ulcer -17%, mean +6%)   | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| K7_1   |      4 | HALF size when c4_srsiF_vol500_rise is NO                     | 1g    |       0.04  |        -61.1 |       0.043 |        -37.9 | 41%                        | GREEN (<=15%: ulcer -5%, mean -8%)    | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| K7_1   |      5 | size x1.5 when m_trix30_3m_divwith is YES                     | 1b    |       0.03  |        -36.7 |       0.02  |        -10   | 18%                        | GREEN (<=15%: ulcer +8%, mean -3%)    | NQ bars                           | yes: own bars                                                                        |
| K7_3   |      1 | SKIP the trade when n_eh_roof_fast_1m_fresh5 is YES           | 1a    |       0.159 |        -81   |       0.236 |        -64.4 | 48%                        | GREEN (<=15%: ulcer -15%, mean +10%)  | NQ bars                           | yes: own bars/session anchors                                                        |
| K7_3   |      2 | size x1.5 when c4_stc_renko8_eenter is YES                    | 1g    |       0.028 |        -17   |       0.022 |          1   | 11%                        | GREEN (<=15%: ulcer +6%, mean -8%)    | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| K7_3   |      3 | SKIP the trade when c4_cdl_1m_with_gt_against is NO           | 2     |       0.124 |        -80.2 |       0.152 |        -65.7 | 37%                        | GREEN (<=15%: ulcer +12%, mean +14%)  | NQ bars                           | yes: own bars                                                                        |
| K7_3   |      4 | SKIP the trade when c4_seb_ha1_fresh5 is YES                  | 1g    |       0.146 |        -84.7 |       0.221 |        -73.5 | 48%                        | GREEN (<=15%: ulcer +4%, mean -5%)    | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| K7_3   |      5 | HALF size when c4_irl_a_pd_int_against_60 is YES              | 2     |       0.042 |        -53.8 |       0.028 |        -24   | 46%                        | GREEN (<=15%: ulcer -7%, mean +8%)    | NQ bars                           | yes: own bars                                                                        |
| K7_4   |      1 | SKIP the trade when c4_ichiS_chikou_ha60_hold3 is NO          | 1g    |       0.139 |        -79.3 |       0.238 |        -85.2 | 49%                        | GREEN (<=15%: ulcer -23%, mean +88%)  | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| K7_4   |      2 | HALF size when fl223_d1 is YES                                | 5b    |       0.045 |        -60   |       0.06  |        -50.9 | 41%                        | GREEN (<=15%: ulcer -23%, mean -4%)   | L3 / L2 book                      | NO today: needs L3 order-by-order / L2 book (live book is polluted by ES/RTY levels) |
| K7_4   |      3 | HALF size when c_T_l1_dur_ratio_gt1_L2 is YES                 | 5a    |       0.049 |        -53.1 |       0.046 |        -37.1 | 39%                        | GREEN (<=15%: ulcer -28%, mean +0%)   | NQ prints (+L3 for message rates) | prints yes (NT8); message rates need L3                                              |
| K7_4   |      4 | HALF size when c_N_ict_ntf_atkey_against_ge1 is YES           | 2     |       0.053 |        -60.5 |       0.069 |        -47.4 | 49%                        | GREEN (<=15%: ulcer -20%, mean +43%)  | NQ bars                           | yes: own bars                                                                        |
| K7_4   |      5 | HALF size when m_linreg_slope50_60m_side is NO                | 1b    |       0.043 |        -61.9 |       0.092 |        -61.1 | 41%                        | GREEN (<=15%: ulcer -10%, mean -9%)   | NQ bars                           | yes: own bars                                                                        |
| M7_1   |      1 | HALF size when n_rk_soup_fast_5m_against_state is NO          | 1a    |       0.041 |        -53.9 |       0.048 |        -32.7 | 44%                        | GREEN (<=15%: ulcer +7%, mean -7%)    | NQ bars                           | yes: own bars/session anchors                                                        |
| M7_1   |      2 | SKIP the trade when m_donchian50_pos_1d_side is NO            | 1b    |       0.092 |        -76.5 |       0.069 |        -55.4 | 48%                        | GREEN (<=15%: ulcer -30%, mean +57%)  | NQ bars                           | yes: own bars                                                                        |
| M7_1   |      3 | HALF size when c4_ichiF_thick_1d_rise is NO                   | 1d    |       0.036 |        -60.2 |       0.012 |        -33.2 | 41%                        | GREEN (<=15%: ulcer -27%, mean +57%)  | NQ bars                           | yes: own bars                                                                        |
| M7_1   |      4 | size x1.5 when c4_w1_cmo14_range16_ewith is YES               | 1g    |       0.024 |        -30   |       0.029 |         -8.7 | 28%                        | GREEN (<=15%: ulcer +9%, mean +1%)    | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| M7_1   |      5 | size x1.5 when n_fl_ofi1s_with is YES                         | 5b    |       0.027 |        -30   |       0.025 |        -15.1 | 26%                        | GREEN (<=15%: ulcer -3%, mean +13%)   | L3 / L2 book                      | NO today: needs L3 order-by-order / L2 book (live book is polluted by ES/RTY levels) |
| M7_3   |      1 | SKIP the trade when n_bk_failbo_fast_15m_against_state is YES | 1a    |       0.121 |        -75.4 |       0.128 |        -54   | 45%                        | GREEN (<=15%: ulcer -36%, mean -6%)   | NQ bars                           | yes: own bars/session anchors                                                        |
| M7_3   |      2 | size x1.5 when c_N_bkB_1_against_cur_ge3 is NO                | 2     |       0.028 |        -25.9 |      -0.006 |         31.4 | 22%                        | GREEN (<=15%: ulcer +14%, mean -9%)   | NQ bars                           | yes: own bars                                                                        |
| M7_3   |      3 | HALF size when c4_w1_vwma50_px_ha15_fresh5 is YES             | 1g    |       0.048 |        -57.7 |       0.017 |        -16.2 | 44%                        | GREEN (<=15%: ulcer +1%, mean -13%)   | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| M7_3   |      4 | SKIP the trade when fl114_d2 is NO                            | 5b    |       0.123 |        -73.8 |       0.154 |        -31.1 | 49%                        | GREEN (<=15%: ulcer -16%, mean -10%)  | L3 / L2 book                      | NO today: needs L3 order-by-order / L2 book (live book is polluted by ES/RTY levels) |
| M7_3   |      5 | SKIP the trade when c4_w1_demarker14_ha5_rise is NO           | 1g    |       0.094 |        -64.6 |       0.073 |        -41.1 | 39%                        | GREEN (<=15%: ulcer -1%, mean +4%)    | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| O7_3   |      1 | size x1.5 when c4_eqpool_up_1d_hi is NO                       | 1e    |       0.067 |         -2.5 |             |              | 37%                        | GREEN (<=15%: ulcer +0%, mean +0%)    | NQ bars                           | yes: own bars                                                                        |
| O7_3   |      2 | SKIP the trade when c4_obF_cnt_ha3_side is NO                 | 1g    |       0.495 |        -73.9 |             |              | 46%                        | GREEN (<=15%: ulcer +2%, mean -7%)    | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| O7_3   |      3 | HALF size when c4_w1_stoch21_range16_rise is NO               | 1g    |       0.136 |        -47   |             |              | 49%                        | GREEN (<=15%: ulcer -27%, mean +10%)  | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| O7_3   |      4 | SKIP the trade when c4_smiS_5m_fresh5 is YES                  | 1c    |       0.424 |        -66.6 |             |              | 49%                        | GREEN (<=15%: ulcer -15%, mean -12%)  | NQ bars                           | yes: own bars                                                                        |
| O7_3   |      5 | HALF size when c4_fvgF_cnt_ha3_side is NO                     | 1g    |       0.149 |        -39.9 |             |              | 43%                        | GREEN (<=15%: ulcer -8%, mean -11%)   | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| P7_0   |      1 | SKIP the trade when fl224_v0 is YES                           | 5b    |       0.087 |        -65.4 |       0.161 |        -42.1 | 40%                        | GREEN (<=15%: ulcer -15%, mean +11%)  | L3 / L2 book                      | NO today: needs L3 order-by-order / L2 book (live book is polluted by ES/RTY levels) |
| P7_0   |      2 | SKIP the trade when c4_agr_obS_dres_rise_ge6 is NO            | 1h    |       0.087 |        -63.2 |       0.058 |        -53   | 35%                        | GREEN (<=15%: ulcer +1%, mean +14%)   | NQ prints -> alt bars             | yes, same as 1g                                                                      |
| P7_0   |      3 | HALF size when c4_w1_adx21_ha60_hi_z1 is YES                  | 1g    |       0.028 |        -52.3 |       0.036 |        -40.2 | 50%                        | GREEN (<=15%: ulcer +5%, mean -8%)    | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| P7_0   |      4 | HALF size when c4_crsi_tick2000_divwith is YES                | 1g    |       0.033 |        -47.4 |       0.05  |        -27.3 | 25%                        | GREEN (<=15%: ulcer -7%, mean -1%)    | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| P7_0   |      5 | SKIP the trade when c_S_corr60_rty_ge0.7 is YES               | 1b    |       0.066 |        -63.5 |      -0.006 |        -18.3 | 49%                        | GREEN (<=15%: ulcer -5%, mean -10%)   | NQ bars                           | yes: own bars                                                                        |
| P7_1   |      1 | SKIP the trade when fl061_v0 is YES                           | 5b    |       0.099 |        -70   |       0.197 |        -81.7 | 49%                        | GREEN (<=15%: ulcer -41%, mean +7%)   | L3 / L2 book                      | NO today: needs L3 order-by-order / L2 book (live book is polluted by ES/RTY levels) |
| P7_1   |      2 | HALF size when c4_fractal_brk_renko16_hold3 is NO             | 1g    |       0.03  |        -43.3 |       0.029 |        -31.5 | 39%                        | GREEN (<=15%: ulcer -8%, mean -8%)    | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| P7_1   |      3 | size x1.5 when c4_w1_supertrend_14_4_range16_fresh5 is YES    | 1g    |       0.021 |        -24.1 |       0.025 |        -11.7 | 18%                        | GREEN (<=15%: ulcer +2%, mean -1%)    | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| P7_1   |      4 | HALF size when c4_agr_w1_hma_stack_fast_side_ge6 is YES       | 1h    |       0.04  |        -49.4 |       0.032 |        -39.6 | 38%                        | GREEN (<=15%: ulcer -7%, mean +9%)    | NQ prints -> alt bars             | yes, same as 1g                                                                      |
| P7_1   |      5 | SKIP the trade when c4_ichiF_thick_1m_rise is NO              | 1d    |       0.1   |        -61.8 |       0.103 |        -57.3 | 49%                        | GREEN (<=15%: ulcer -11%, mean -13%)  | NQ bars                           | yes: own bars                                                                        |
| P7_3   |      1 | SKIP the trade when c4_rviS_tick2000_fresh5 is YES            | 1g    |       0.121 |        -77.4 |       0.118 |        -68.1 | 40%                        | GREEN (<=15%: ulcer -40%, mean +33%)  | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| P7_3   |      2 | size x1.5 when c4_fp_5m_dtop_with is NO                       | 5a    |       0.028 |        -23.2 |       0.018 |         -6.1 | 18%                        | GREEN (<=15%: ulcer +7%, mean -2%)    | NQ prints (+L3 for message rates) | prints yes (NT8); message rates need L3                                              |
| P7_3   |      3 | HALF size when c4_zlemaS_px_60m_side is NO                    | 1d    |       0.066 |        -68   |       0.06  |        -58.1 | 32%                        | GREEN (<=15%: ulcer -22%, mean -4%)   | NQ bars                           | yes: own bars                                                                        |
| P7_3   |      4 | HALF size when m_macd19_39_9_line_60m_sig is NO               | 1b    |       0.058 |        -66.3 |       0.062 |        -60.6 | 44%                        | GREEN (<=15%: ulcer -7%, mean -15%)   | NQ bars                           | yes: own bars                                                                        |
| P7_3   |      5 | HALF size when c4_lrcF_slope_ha15_side is NO                  | 1g    |       0.049 |        -66.1 |       0.034 |        -57.8 | 47%                        | GREEN (<=15%: ulcer -24%, mean +3%)   | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| U7_0   |      1 | HALF size when c4_cdl_5m_nagainst3 is NO                      | 2     |       0.034 |        -30   |       0.012 |        -27.7 | 32%                        | GREEN (<=15%: ulcer -14%, mean +31%)  | NQ bars                           | yes: own bars                                                                        |
| U7_0   |      2 | HALF size when c4_chopF_1m_rise is NO                         | 1c    |       0.045 |        -35.3 |       0.06  |        -40.1 | 47%                        | GREEN (<=15%: ulcer -23%, mean -8%)   | NQ bars                           | yes: own bars                                                                        |
| U7_0   |      3 | SKIP the trade when c4_agr_fractal_brk_fresh5_ge3 is YES      | 1h    |       0.153 |        -46.4 |       0.216 |        -47.2 | 42%                        | GREEN (<=15%: ulcer +7%, mean -11%)   | NQ prints -> alt bars             | yes, same as 1g                                                                      |
| U7_0   |      4 | SKIP the trade when fl258_v0 is YES                           | 5b    |       0.21  |        -57.6 |       0.213 |        -58.8 | 49%                        | GREEN (<=15%: ulcer -28%, mean +56%)  | L3 / L2 book                      | NO today: needs L3 order-by-order / L2 book (live book is polluted by ES/RTY levels) |
| U7_0   |      5 | HALF size when c4_w1_stochrsi14_ha5_rise is YES               | 1g    |       0.049 |        -42.4 |       0.105 |        -48.5 | 50%                        | GREEN (<=15%: ulcer -9%, mean +9%)    | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| U7_1   |      1 | HALF size when c4_ssl_range16_hold3 is NO                     | 1g    |       0.098 |        -50.2 |       0.115 |        -51.8 | 40%                        | GREEN (<=15%: ulcer -7%, mean -11%)   | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| U7_1   |      2 | HALF size when m_sma50_px_15m_rise is YES                     | 1b    |       0.058 |        -37.1 |       0.066 |        -42.8 | 49%                        | GREEN (<=15%: ulcer -6%, mean -14%)   | NQ bars                           | yes: own bars                                                                        |
| U7_1   |      3 | SKIP the trade when c4_turt20_range8_hold3 is NO              | 1g    |       0.235 |        -70.7 |       0.318 |        -72.2 | 46%                        | GREEN (<=15%: ulcer -14%, mean +13%)  | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| U7_1   |      4 | HALF size when c4_w1_rsi14_ha15_fresh5 is NO                  | 1g    |       0.058 |        -37.7 |       0.088 |        -48.6 | 49%                        | GREEN (<=15%: ulcer -2%, mean -8%)    | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| U7_1   |      5 | SKIP the trade when c4_agr_ssl_against_ge3 is YES             | 1h    |       0.184 |        -70   |       0.129 |        -68.7 | 47%                        | GREEN (<=15%: ulcer -14%, mean -7%)   | NQ prints -> alt bars             | yes, same as 1g                                                                      |

Gate 30% (top 5 per book x session):
| cell   |   rank | pick                                                          | fam   |   6M dMeanR |   6M dUlcer% |   3M dMeanR |   3M dUlcer% | share of trades acted on   | prior years                                | feed                              | D7 live                                                                              |
|:-------|-------:|:--------------------------------------------------------------|:------|------------:|-------------:|------------:|-------------:|:---------------------------|:-------------------------------------------|:----------------------------------|:-------------------------------------------------------------------------------------|
| A7_0   |      1 | size x1.5 when n_eh_ss20_1m_nodiv is NO                       | 1a    |       0.026 |        -11.8 |       0.04  |         -8   | 28%                        | AMBER (15-30%: ulcer +27%, mean 3% worse)  | NQ bars                           | yes: own bars/session anchors                                                        |
| A7_0   |      2 | size x1.5 when fl231_d1 is YES                                | 5b    |       0.038 |        -24.4 |       0.038 |        -11.8 | 21%                        | AMBER (15-30%: ulcer +20%, mean 5% worse)  | L3 / L2 book                      | NO today: needs L3 order-by-order / L2 book (live book is polluted by ES/RTY levels) |
| A7_0   |      3 | SKIP the trade when c4_cdl_15m_with_gt_against is NO          | 2     |       0.142 |        -61.4 |       0.165 |        -58   | 44%                        | AMBER (15-30%: ulcer +15%, mean 21% worse) | NQ bars                           | yes: own bars                                                                        |
| A7_0   |      4 | size x1.5 when c4_cdl_5m_nwith3 is NO                         | 2     |       0.024 |         -6.7 |       0.024 |         -6.3 | 17%                        | AMBER (15-30%: ulcer +20%, mean -2% worse) | NQ bars                           | yes: own bars                                                                        |
| A7_0   |      5 | SKIP the trade when c4_ichi_chikou_tick2000_fresh5 is YES     | 1g    |       0.142 |        -61.3 |       0.18  |        -65.9 | 33%                        | AMBER (15-30%: ulcer +1%, mean 16% worse)  | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| H7_0   |      1 | SKIP the trade when n_eh_dcp_long_1d_hi is YES                | 1a    |       0.274 |        -88.3 |       0.186 |        -77.6 | 47%                        | AMBER (15-30%: ulcer +2%, mean 26% worse)  | NQ bars                           | yes: own bars/session anchors                                                        |
| H7_0   |      2 | SKIP the trade when c4_qqemod_hist_tick2000_fresh5 is YES     | 1g    |       0.232 |        -80.6 |       0.299 |        -75.3 | 37%                        | AMBER (15-30%: ulcer -9%, mean 19% worse)  | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| H7_0   |      3 | SKIP the trade when c4_cdl_60m_with_ge2 is NO                 | 2     |       0.178 |        -70.9 |       0.133 |        -48.3 | 49%                        | GREEN (<=15%: ulcer -19%, mean +25%)       | NQ bars                           | yes: own bars                                                                        |
| H7_0   |      4 | SKIP the trade when c4_agr_w1_cci20_eenter_z1_ge3 is NO       | 1h    |       0.259 |        -72.6 |       0.222 |        -75   | 47%                        | AMBER (15-30%: ulcer +15%, mean 12% worse) | NQ prints -> alt bars             | yes, same as 1g                                                                      |
| H7_0   |      5 | HALF size when c4_chopF_5m_rise is YES                        | 1c    |       0.086 |        -58.6 |       0.061 |        -49.6 | 46%                        | GREEN (<=15%: ulcer -0%, mean +6%)         | NQ bars                           | yes: own bars                                                                        |
| H7_3   |      1 | HALF size when n_dm_supply_line_3m_fresh5 is NO               | 1a    |       0.082 |        -53.3 |             |              | 47%                        | AMBER (15-30%: ulcer +11%, mean 30% worse) | NQ bars                           | yes: own bars/session anchors                                                        |
| H7_3   |      2 | HALF size when c_B14_avg_corr60_le0.2 is YES                  | 6     |       0.106 |        -48.7 |             |              | 42%                        | AMBER (15-30%: ulcer +7%, mean 25% worse)  | ES/RTY/YM/rates/other markets     | NO today: other-market feeds not on the D7 chart                                     |
| H7_3   |      3 | HALF size when c_A_px_ema50_1d is NO                          | 1b    |       0.081 |        -53.5 |             |              | 47%                        | GREEN (<=15%: ulcer -20%, mean +66%)       | NQ bars                           | yes: own bars                                                                        |
| H7_3   |      4 | SKIP the trade when c_I_YM_conf5 is NO                        | 6     |       0.3   |        -75.6 |             |              | 47%                        | GREEN (<=15%: ulcer -23%, mean +45%)       | ES/RTY/YM/rates/other markets     | NO today: other-market feeds not on the D7 chart                                     |
| H7_3   |      5 | SKIP the trade when c4_w1_atr_pct250_renko8_hi is NO          | 1g    |       0.234 |        -67.4 |             |              | 47%                        | GREEN (<=15%: ulcer +2%, mean +6%)         | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| K7_0   |      1 | HALF size when m_aroon25_3m_ewith is YES                      | 1b    |       0.032 |        -51.8 |       0.028 |        -43.7 | 36%                        | GREEN (<=15%: ulcer +10%, mean -15%)       | NQ bars                           | yes: own bars                                                                        |
| K7_0   |      2 | SKIP the trade when c4_w1_donchian10_width_vol500_rise is YES | 1g    |       0.073 |        -69   |       0.151 |        -82   | 44%                        | AMBER (15-30%: ulcer -14%, mean 26% worse) | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| K7_0   |      3 | size x1.5 when c4_stA21_vol500_hold3 is NO                    | 1g    |       0.022 |        -17.5 |       0.027 |         -6.1 | 31%                        | AMBER (15-30%: ulcer +25%, mean 7% worse)  | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| K7_0   |      4 | SKIP the trade when c4_w1_linreg_slope10_renko8_rise is NO    | 1g    |       0.097 |        -75.3 |       0.131 |        -72.9 | 49%                        | GREEN (<=15%: ulcer -26%, mean +8%)        | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| K7_0   |      5 | HALF size when c4_stA_vol2000_hold3 is NO                     | 1g    |       0.031 |        -46.1 |       0.055 |        -40.9 | 50%                        | GREEN (<=15%: ulcer -23%, mean +28%)       | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| K7_1   |      1 | HALF size when n_bk_failbo_std_60m_against_state is YES       | 1a    |       0.038 |        -59.7 |       0.035 |        -46.1 | 38%                        | GREEN (<=15%: ulcer -11%, mean +9%)        | NQ bars                           | yes: own bars/session anchors                                                        |
| K7_1   |      2 | SKIP the trade when c4_don10_pos_1d_rise is YES               | 1d    |       0.093 |        -82.8 |       0.111 |        -72.5 | 50%                        | GREEN (<=15%: ulcer +5%, mean +42%)        | NQ bars                           | yes: own bars                                                                        |
| K7_1   |      3 | size x1.5 when c4_chandF_15m_fresh5 is YES                    | 1d    |       0.026 |        -30.6 |       0.009 |         19.1 | 28%                        | AMBER (15-30%: ulcer +22%, mean 3% worse)  | NQ bars                           | yes: own bars                                                                        |
| K7_1   |      4 | HALF size when c4_w1_di21_ha60_rise is NO                     | 1g    |       0.036 |        -61.7 |       0.019 |        -21.5 | 43%                        | GREEN (<=15%: ulcer -17%, mean +6%)        | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| K7_1   |      5 | size x1.5 when c4_w1_demarker14_ha1_rise is NO                | 1g    |       0.027 |        -34.5 |       0.022 |          0.5 | 23%                        | AMBER (15-30%: ulcer +25%, mean 13% worse) | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| K7_3   |      1 | size x1.5 when c4_sdflipF_near_3m_side is YES                 | 1e    |       0.029 |        -15.2 |       0.018 |          9.9 | 32%                        | AMBER (15-30%: ulcer +17%, mean 18% worse) | NQ bars                           | yes: own bars                                                                        |
| K7_3   |      2 | SKIP the trade when c4_cdl_1m_with_gt_against is NO           | 2     |       0.124 |        -80.2 |       0.152 |        -65.7 | 37%                        | GREEN (<=15%: ulcer +12%, mean +14%)       | NQ bars                           | yes: own bars                                                                        |
| K7_3   |      3 | size x1.5 when c4_stc_renko8_eenter is YES                    | 1g    |       0.028 |        -17   |       0.022 |          1   | 11%                        | GREEN (<=15%: ulcer +6%, mean -8%)         | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| K7_3   |      4 | size x1.5 when m_linreg_slope50_60m_divwith is YES            | 1b    |       0.024 |        -13   |       0.036 |         -0.9 | 19%                        | AMBER (15-30%: ulcer +18%, mean 9% worse)  | NQ bars                           | yes: own bars                                                                        |
| K7_3   |      5 | SKIP the trade when n_eh_roof_fast_1m_fresh5 is YES           | 1a    |       0.159 |        -81   |       0.236 |        -64.4 | 48%                        | GREEN (<=15%: ulcer -15%, mean +10%)       | NQ bars                           | yes: own bars/session anchors                                                        |
| K7_4   |      1 | SKIP the trade when c4_ichiS_chikou_ha60_hold3 is NO          | 1g    |       0.139 |        -79.3 |       0.238 |        -85.2 | 49%                        | GREEN (<=15%: ulcer -23%, mean +88%)       | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| K7_4   |      2 | HALF size when c4_kvoS_ha60_side is NO                        | 1g    |       0.045 |        -59.7 |       0.092 |        -61.8 | 47%                        | AMBER (15-30%: ulcer -19%, mean 17% worse) | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| K7_4   |      3 | HALF size when fl223_d1 is YES                                | 5b    |       0.045 |        -60   |       0.06  |        -50.9 | 41%                        | GREEN (<=15%: ulcer -23%, mean -4%)        | L3 / L2 book                      | NO today: needs L3 order-by-order / L2 book (live book is polluted by ES/RTY levels) |
| K7_4   |      4 | HALF size when c4_chandF_ha60_side is NO                      | 1g    |       0.044 |        -63.6 |       0.082 |        -55.4 | 44%                        | AMBER (15-30%: ulcer -12%, mean 21% worse) | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| K7_4   |      5 | HALF size when c_T_l1_dur_ratio_gt1_L2 is YES                 | 5a    |       0.049 |        -53.1 |       0.046 |        -37.1 | 39%                        | GREEN (<=15%: ulcer -28%, mean +0%)        | NQ prints (+L3 for message rates) | prints yes (NT8); message rates need L3                                              |
| M7_1   |      1 | HALF size when n_rk_soup_fast_5m_against_state is NO          | 1a    |       0.041 |        -53.9 |       0.048 |        -32.7 | 44%                        | GREEN (<=15%: ulcer +7%, mean -7%)         | NQ bars                           | yes: own bars/session anchors                                                        |
| M7_1   |      2 | HALF size when c4_ichiF_thick_1d_rise is NO                   | 1d    |       0.036 |        -60.2 |       0.012 |        -33.2 | 41%                        | GREEN (<=15%: ulcer -27%, mean +57%)       | NQ bars                           | yes: own bars                                                                        |
| M7_1   |      3 | size x1.5 when c4_w1_cmo14_range16_ewith is YES               | 1g    |       0.024 |        -30   |       0.029 |         -8.7 | 28%                        | GREEN (<=15%: ulcer +9%, mean +1%)         | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| M7_1   |      4 | size x1.5 when n_fl_ofi1s_with is YES                         | 5b    |       0.027 |        -30   |       0.025 |        -15.1 | 26%                        | GREEN (<=15%: ulcer -3%, mean +13%)        | L3 / L2 book                      | NO today: needs L3 order-by-order / L2 book (live book is polluted by ES/RTY levels) |
| M7_1   |      5 | HALF size when c4_sqzmF_bright_vol2000_side is YES            | 1g    |       0.028 |        -51.7 |       0.03  |        -36.3 | 46%                        | AMBER (15-30%: ulcer -1%, mean 27% worse)  | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| M7_3   |      1 | size x1.5 when c_N_bkB_1_against_cur_ge3 is NO                | 2     |       0.028 |        -25.9 |      -0.006 |         31.4 | 22%                        | GREEN (<=15%: ulcer +14%, mean -9%)        | NQ bars                           | yes: own bars                                                                        |
| M7_3   |      2 | HALF size when c4_agr_sqzmF_on_hi_ge6 is YES                  | 1h    |       0.052 |        -57.2 |       0.051 |        -28.3 | 45%                        | AMBER (15-30%: ulcer -3%, mean 18% worse)  | NQ prints -> alt bars             | yes, same as 1g                                                                      |
| M7_3   |      3 | HALF size when c4_w1_aroon14_ha1_rise is NO                   | 1g    |       0.041 |        -58.4 |       0.021 |        -16.1 | 47%                        | AMBER (15-30%: ulcer -3%, mean 16% worse)  | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| M7_3   |      4 | SKIP the trade when c4_w1_willr7_tick2000_ewith is NO         | 1g    |       0.122 |        -72.8 |       0.117 |        -49.1 | 48%                        | AMBER (15-30%: ulcer -13%, mean 30% worse) | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| M7_3   |      5 | HALF size when c4_w1_vwma50_px_ha15_fresh5 is YES             | 1g    |       0.048 |        -57.7 |       0.017 |        -16.2 | 44%                        | GREEN (<=15%: ulcer +1%, mean -13%)        | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| O7_3   |      1 | size x1.5 when c4_eqpool_up_1d_hi is NO                       | 1e    |       0.067 |         -2.5 |             |              | 37%                        | GREEN (<=15%: ulcer +0%, mean +0%)         | NQ bars                           | yes: own bars                                                                        |
| O7_3   |      2 | SKIP the trade when c4_fvgF_near_3m_against is YES            | 1e    |       0.504 |        -75.9 |             |              | 49%                        | AMBER (15-30%: ulcer +14%, mean 20% worse) | NQ bars                           | yes: own bars                                                                        |
| O7_3   |      3 | SKIP the trade when c4_ob_dres_5m_hi is NO                    | 1e    |       0.586 |        -75   |             |              | 49%                        | AMBER (15-30%: ulcer +15%, mean 23% worse) | NQ bars                           | yes: own bars                                                                        |
| O7_3   |      4 | SKIP the trade when c4_obF_cnt_ha3_side is NO                 | 1g    |       0.495 |        -73.9 |             |              | 46%                        | GREEN (<=15%: ulcer +2%, mean -7%)         | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| O7_3   |      5 | size x1.5 when c4_w1_hma_stack_slow_tick2000_hold3 is YES     | 1g    |       0.1   |         -8   |             |              | 27%                        | AMBER (15-30%: ulcer +24%, mean 9% worse)  | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| P7_0   |      1 | SKIP the trade when m_donchian20_width_1d_hi is YES           | 1b    |       0.106 |        -80   |       0.144 |        -63.4 | 47%                        | AMBER (15-30%: ulcer +4%, mean 24% worse)  | NQ bars                           | yes: own bars                                                                        |
| P7_0   |      2 | HALF size when c4_sebS_ha60_side is NO                        | 1g    |       0.041 |        -50   |       0.023 |        -29.5 | 41%                        | AMBER (15-30%: ulcer +13%, mean 27% worse) | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| P7_0   |      3 | size x1.5 when c4_w1_hma200_px_ha5_side is NO                 | 1g    |       0.019 |        -35.7 |       0.019 |         -4.5 | 21%                        | AMBER (15-30%: ulcer +22%, mean 23% worse) | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| P7_0   |      4 | size x1.5 when c4_fp_60m_stack2_with is NO                    | 5a    |       0.026 |        -24.7 |       0.023 |          4.9 | 23%                        | AMBER (15-30%: ulcer +30%, mean 30% worse) | NQ prints (+L3 for message rates) | prints yes (NT8); message rates need L3                                              |
| P7_0   |      5 | HALF size when m_wave_short_hist_60m_fresh5 is YES            | 1b    |       0.034 |        -56.1 |       0.036 |        -40.6 | 46%                        | AMBER (15-30%: ulcer -3%, mean 26% worse)  | NQ bars                           | yes: own bars                                                                        |
| P7_1   |      1 | SKIP the trade when fl061_v0 is YES                           | 5b    |       0.099 |        -70   |       0.197 |        -81.7 | 49%                        | GREEN (<=15%: ulcer -41%, mean +7%)        | L3 / L2 book                      | NO today: needs L3 order-by-order / L2 book (live book is polluted by ES/RTY levels) |
| P7_1   |      2 | HALF size when c4_w1_roc10_ha5_rise is YES                    | 1g    |       0.043 |        -50.1 |       0.072 |        -43   | 47%                        | AMBER (15-30%: ulcer -16%, mean 19% worse) | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| P7_1   |      3 | HALF size when c4_fractal_brk_renko16_hold3 is NO             | 1g    |       0.03  |        -43.3 |       0.029 |        -31.5 | 39%                        | GREEN (<=15%: ulcer -8%, mean -8%)         | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| P7_1   |      4 | size x1.5 when c4_w1_supertrend_14_4_range16_fresh5 is YES    | 1g    |       0.021 |        -24.1 |       0.025 |        -11.7 | 18%                        | GREEN (<=15%: ulcer +2%, mean -1%)         | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| P7_1   |      5 | HALF size when c4_agr_w1_hma_stack_fast_side_ge6 is YES       | 1h    |       0.04  |        -49.4 |       0.032 |        -39.6 | 38%                        | GREEN (<=15%: ulcer -7%, mean +9%)         | NQ prints -> alt bars             | yes, same as 1g                                                                      |
| P7_3   |      1 | HALF size when c4_st_60m_sqzk10_fa_9p is YES                  | 1f    |       0.057 |        -62.8 |       0.052 |        -44.2 | 43%                        | AMBER (15-30%: ulcer +15%, mean 28% worse) | NQ bars                           | yes: own bars                                                                        |
| P7_3   |      2 | HALF size when c4_st_60m_macd_hist_against is YES             | 1f    |       0.053 |        -64.7 |       0.032 |        -54   | 44%                        | AMBER (15-30%: ulcer -9%, mean 26% worse)  | NQ bars                           | yes: own bars                                                                        |
| P7_3   |      3 | HALF size when c4_stcS_ha60_side is NO                        | 1g    |       0.088 |        -70.4 |       0.081 |        -60.7 | 44%                        | AMBER (15-30%: ulcer -5%, mean 18% worse)  | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| P7_3   |      4 | SKIP the trade when c4_rviS_tick2000_fresh5 is YES            | 1g    |       0.121 |        -77.4 |       0.118 |        -68.1 | 40%                        | GREEN (<=15%: ulcer -40%, mean +33%)       | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| P7_3   |      5 | size x1.5 when c4_fp_5m_dtop_with is NO                       | 5a    |       0.028 |        -23.2 |       0.018 |         -6.1 | 18%                        | GREEN (<=15%: ulcer +7%, mean -2%)         | NQ prints (+L3 for message rates) | prints yes (NT8); message rates need L3                                              |
| U7_0   |      1 | SKIP the trade when c4_cdl_5m_against_ge1 is NO               | 2     |       0.085 |        -40.4 |       0.03  |        -35.2 | 32%                        | GREEN (<=15%: ulcer -22%, mean +79%)       | NQ bars                           | yes: own bars                                                                        |
| U7_0   |      2 | HALF size when c_T_l1_depth_gt0.618_L2 is NO                  | 5a    |       0.056 |        -38.3 |       0.043 |        -34.1 | 36%                        | AMBER (15-30%: ulcer -1%, mean 19% worse)  | NQ prints (+L3 for message rates) | prints yes (NT8); message rates need L3                                              |
| U7_0   |      3 | HALF size when c4_chopF_1m_rise is NO                         | 1c    |       0.045 |        -35.3 |       0.06  |        -40.1 | 47%                        | GREEN (<=15%: ulcer -23%, mean -8%)        | NQ bars                           | yes: own bars                                                                        |
| U7_0   |      4 | SKIP the trade when c4_agr_fractal_brk_fresh5_ge3 is YES      | 1h    |       0.153 |        -46.4 |       0.216 |        -47.2 | 42%                        | GREEN (<=15%: ulcer +7%, mean -11%)        | NQ prints -> alt bars             | yes, same as 1g                                                                      |
| U7_0   |      5 | SKIP the trade when fl258_v0 is YES                           | 5b    |       0.21  |        -57.6 |       0.213 |        -58.8 | 49%                        | GREEN (<=15%: ulcer -28%, mean +56%)       | L3 / L2 book                      | NO today: needs L3 order-by-order / L2 book (live book is polluted by ES/RTY levels) |
| U7_1   |      1 | HALF size when c4_mc_comp2_ha5_fresh5 is NO                   | 1g    |       0.077 |        -38.1 |       0.076 |        -39.9 | 48%                        | AMBER (15-30%: ulcer +14%, mean 27% worse) | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| U7_1   |      2 | size x1.5 when c4_eqpool_dnF_range16_rise is NO               | 1g    |       0.031 |         -5.1 |       0.033 |         -8.7 | 14%                        | AMBER (15-30%: ulcer +29%, mean -0% worse) | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| U7_1   |      3 | size x1.5 when c4_sqzm_bright_renko8_side is YES              | 1g    |       0.071 |        -10.3 |       0.131 |        -24.3 | 37%                        | AMBER (15-30%: ulcer +30%, mean -2% worse) | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| U7_1   |      4 | size x1.5 when c4_w1_mfi21_ha15_rise is NO                    | 1g    |       0.052 |         -9.3 |       0.057 |        -11.1 | 23%                        | AMBER (15-30%: ulcer +16%, mean 7% worse)  | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |
| U7_1   |      5 | size x1.5 when c4_ker_abs_ha5_rise is NO                      | 1g    |       0.033 |         -5.6 |       0.04  |         -7.1 | 16%                        | AMBER (15-30%: ulcer +12%, mean 21% worse) | NQ prints -> alt bars             | yes if D7 builds HA/range/renko/tick/volume bars from prints (it has the prints)     |

Best single pick per family and cell (gate 15%): 
| cell   | family   | pick                                                          |   6M dMeanR |   6M dU% |   3M dMeanR |   3M dU% | prior   |
|:-------|:---------|:--------------------------------------------------------------|------------:|---------:|------------:|---------:|:--------|
| A7_0   | 1        | SKIP the trade when c4_rfilt_ha5_rise is YES                  |       0.119 |    -73.2 |       0.075 |    -68.5 | GREEN   |
| A7_0   | 2        | HALF size when c4_pitchfork_15m_eenter is YES                 |       0.041 |    -33.5 |       0.027 |    -22.6 | GREEN   |
| A7_0   | 3        | HALF size when c_Z3_SH_at5 is YES                             |       0.001 |    -11.7 |       0.003 |    -20.1 | GREEN   |
| A7_0   | 4        | HALF size when c_R2_uwb_hi3 is YES                            |       0.009 |    -28.4 |       0.023 |    -21.6 | GREEN   |
| A7_0   | 5        | SKIP the trade when fl005_d0 is YES                           |       0.08  |    -61.7 |       0.045 |    -54   | GREEN   |
| A7_0   | 6        | HALF size when c_B5_corr_NQ_MEGA_240_ge0.7 is NO              |       0.037 |    -35.3 |       0.033 |    -38   | GREEN   |
| A7_0   | 7        | SKIP the trade when c_J_flip_far100_NDX_vol is NO             |       0.074 |    -51.5 |       0.108 |    -59.2 | GREEN   |
| A7_0   | 8        | HALF size when n7_halfhour_post30_with is YES                 |       0.01  |    -22.2 |       0.026 |    -15.1 | GREEN   |
| A7_0   | 9        | size x1.5 when c_F9_day_ge3 is YES                            |       0.018 |     -4.8 |       0.027 |    -12.2 | GREEN   |
| A7_0   | 1a       | HALF size when n_ks_peak14_1m_ewith is YES                    |       0.042 |    -36.9 |       0.014 |    -23.8 | GREEN   |
| A7_0   | 1b       | HALF size when m_eom14_60m_side is NO                         |       0.05  |    -34   |       0.053 |    -20.8 | GREEN   |
| A7_0   | 1c       | HALF size when c4_smiS_15m_ewith is NO                        |       0.035 |    -32   |       0.05  |    -22.8 | GREEN   |
| A7_0   | 1d       | HALF size when c4_sebF_1m_fresh5 is NO                        |       0.048 |    -39.3 |       0.037 |    -44.5 | GREEN   |
| A7_0   | 1e       | HALF size when c4_fvgF_dsup_60m_rise is YES                   |       0.038 |    -28.9 |       0.04  |    -31.7 | GREEN   |
| A7_0   | 1f       | HALF size when c4_cvd_1d_rise is NO                           |       0.026 |    -31.8 |       0.061 |    -42.8 | GREEN   |
| A7_0   | 1g       | SKIP the trade when c4_rfilt_ha5_rise is YES                  |       0.119 |    -73.2 |       0.075 |    -68.5 | GREEN   |
| A7_0   | 1h       | HALF size when c4_agr_w1_aroon25_fresh5_ge3 is YES            |       0.035 |    -36.6 |       0.054 |    -36.8 | GREEN   |
| A7_0   | 5a       | SKIP the trade when c4_fp_5m_close_delta_with is NO           |       0.071 |    -38   |       0.089 |    -34.3 | GREEN   |
| A7_0   | 5b       | SKIP the trade when fl005_d0 is YES                           |       0.08  |    -61.7 |       0.045 |    -54   | GREEN   |
| H7_0   | 1        | HALF size when c4_chopF_5m_rise is YES                        |       0.086 |    -58.6 |       0.061 |    -49.6 | GREEN   |
| H7_0   | 2        | SKIP the trade when c4_cdl_60m_with_ge2 is NO                 |       0.178 |    -70.9 |       0.133 |    -48.3 | GREEN   |
| H7_0   | 3        | SKIP the trade when c_Z3_any_behind20 is YES                  |       0.075 |    -53.6 |       0.023 |    -32.3 | GREEN   |
| H7_0   | 4        | HALF size when c_R2_uwa_hi5 is YES                            |       0.012 |    -29.3 |      -0.016 |      0.8 | GREEN   |
| H7_0   | 5        | SKIP the trade when fl280_v0 is YES                           |       0.173 |    -76.7 |       0.081 |    -52.1 | GREEN   |
| H7_0   | 6        | SKIP the trade when c_B5_MEGA_15m_rsi_with is YES             |       0.156 |    -69.2 |       0.083 |    -53.7 | GREEN   |
| H7_0   | 7        | SKIP the trade when c_J_netgamma_pos_Nh_oi is YES             |       0.124 |    -64   |       0.136 |    -68   | GREEN   |
| H7_0   | 8        | SKIP the trade when c_B15_ZN_up_since_open_with is NO         |       0.114 |    -57.9 |       0.098 |    -67.1 | GREEN   |
| H7_0   | 9        | SKIP the trade when c_F9_prev_loss is YES                     |       0.123 |    -61.4 |       0.083 |    -25.8 | GREEN   |
| H7_0   | 1a       | HALF size when n_bk_micro_1m_with_rising is YES               |       0.051 |    -45.5 |       0.036 |    -27   | GREEN   |
| H7_0   | 1b       | HALF size when m_volosc_3m_hi is NO                           |       0.074 |    -45.2 |       0.054 |    -37.8 | GREEN   |
| H7_0   | 1c       | HALF size when c4_chopF_5m_rise is YES                        |       0.086 |    -58.6 |       0.061 |    -49.6 | GREEN   |
| H7_0   | 1d       | SKIP the trade when c4_ichiF_tk_60m_rise is YES               |       0.119 |    -70.5 |       0.102 |    -52.2 | GREEN   |
| H7_0   | 1e       | HALF size when c4_sdS_dsup_1d_hi is YES                       |       0.044 |    -42.7 |      -0.007 |    -10   | GREEN   |
| H7_0   | 1f       | HALF size when c4_delta_15m_rise is NO                        |       0.066 |    -42.2 |       0.082 |    -65.8 | GREEN   |
| H7_0   | 1g       | SKIP the trade when c4_w1_volosc_ha3_hi is NO                 |       0.217 |    -74.2 |       0.172 |    -48.4 | GREEN   |
| H7_0   | 1h       | SKIP the trade when c4_agr_chopF_lo_z1_ge3 is YES             |       0.115 |    -66.1 |       0.024 |    -38.6 | GREEN   |
| H7_0   | 5a       | HALF size when c_T_tps_W60_own_pct_hi is YES                  |       0.037 |    -38   |       0.032 |    -28.4 | GREEN   |
| H7_0   | 5b       | SKIP the trade when fl280_v0 is YES                           |       0.173 |    -76.7 |       0.081 |    -52.1 | GREEN   |
| H7_3   | 1        | HALF size when c_A_px_ema50_1d is NO                          |       0.081 |    -53.5 |             |          | GREEN   |
| H7_3   | 2        | SKIP the trade when c4_cdl_long_line_3m_fresh5 is YES         |       0.209 |    -51.4 |             |          | GREEN   |
| H7_3   | 3        | HALF size when c_Z3_any_behind20 is YES                       |       0.001 |    -29.7 |             |          | GREEN   |
| H7_3   | 5        | HALF size when c_T_cps_W60_diff_raw_lo is YES                 |       0.064 |    -41.2 |             |          | GREEN   |
| H7_3   | 6        | SKIP the trade when c_I_YM_conf5 is NO                        |       0.3   |    -75.6 |             |          | GREEN   |
| H7_3   | 7        | HALF size when c_J_gex_pos_QQQ_vol is NO                      |       0.075 |    -45.5 |             |          | GREEN   |
| H7_3   | 8        | HALF size when n7_tophour_post30_with is YES                  |       0.074 |    -35.1 |             |          | GREEN   |
| H7_3   | 9        | HALF size when c_F9_rechase20 is NO                           |       0.037 |    -27.4 |             |          | GREEN   |
| H7_3   | 10       | SKIP the trade when c_T_tick_cum_slope is NO                  |       0.115 |    -34.6 |             |          | GREEN   |
| H7_3   | 1a       | SKIP the trade when n8_cg_filled is YES                       |       0.312 |    -59.2 |             |          | GREEN   |
| H7_3   | 1b       | HALF size when c_A_px_ema50_1d is NO                          |       0.081 |    -53.5 |             |          | GREEN   |
| H7_3   | 1c       | HALF size when c4_elder_bull_3m_fresh5 is YES                 |       0.085 |    -50.9 |             |          | GREEN   |
| H7_3   | 1d       | SKIP the trade when c4_ichiS_score_15m_fresh5 is YES          |       0.285 |    -66.2 |             |          | GREEN   |
| H7_3   | 1e       | SKIP the trade when c4_fvg_cnt_60m_side is NO                 |       0.17  |    -57.5 |             |          | GREEN   |
| H7_3   | 1f       | SKIP the trade when c4_vp_fr1440_pocdist_gt1.5 is NO          |       0.224 |    -59   |             |          | GREEN   |
| H7_3   | 1g       | SKIP the trade when c4_w1_atr_pct250_renko8_hi is NO          |       0.234 |    -67.4 |             |          | GREEN   |
| H7_3   | 1h       | HALF size when c4_agr_obS_dres_hi_ge3 is YES                  |       0.059 |    -48.4 |             |          | GREEN   |
| H7_3   | 5a       | HALF size when c_T_cps_W60_diff_raw_lo is YES                 |       0.064 |    -41.2 |             |          | GREEN   |
| H7_3   | 5b       | size x1.5 when n_fl_qtr300_hi is YES                          |       0.05  |    -17.2 |             |          | GREEN   |
| K7_0   | 1        | HALF size when m_aroon25_3m_ewith is YES                      |       0.032 |    -51.8 |       0.028 |    -43.7 | GREEN   |
| K7_0   | 2        | HALF size when c_N_bkA_renko8_with_cur_ge2 is NO              |       0.026 |    -51.1 |       0.028 |    -42.6 | GREEN   |
| K7_0   | 3        | HALF size when c_Z3_any_behind20 is YES                       |       0.004 |    -24.1 |      -0.01  |    -11.4 | GREEN   |
| K7_0   | 4        | HALF size when c_R2_uwa_hi5 is YES                            |       0.014 |    -30.9 |       0.021 |    -18.9 | GREEN   |
| K7_0   | 5        | HALF size when fl011_v0 is NO                                 |       0.035 |    -45.1 |       0.026 |    -35.3 | GREEN   |
| K7_0   | 6        | HALF size when c_FL_6E_z1_with is YES                         |       0.027 |    -34.5 |       0.026 |    -30.7 | GREEN   |
| K7_0   | 7        | SKIP the trade when c_J_netgamma_pos_Nh_oi is YES             |       0.032 |    -76.1 |       0.087 |    -74.2 | GREEN   |
| K7_0   | 8        | SKIP the trade when c_B15_pc_eq_rose_prior_day is NO          |       0.026 |    -65   |       0.003 |    -68.4 | GREEN   |
| K7_0   | 9        | SKIP the trade when c_F9_gap_le300 is YES                     |       0.045 |    -56.2 |       0.054 |    -49.3 | GREEN   |
| K7_0   | 1a       | SKIP the trade when n_rk_310_fast_60m_side is NO              |       0.078 |    -79.9 |       0.136 |    -79.3 | GREEN   |
| K7_0   | 1b       | HALF size when m_aroon25_3m_ewith is YES                      |       0.032 |    -51.8 |       0.028 |    -43.7 | GREEN   |
| K7_0   | 1c       | HALF size when c4_mcmf_15m_side is NO                         |       0.033 |    -45.9 |       0.041 |    -42.4 | GREEN   |
| K7_0   | 1d       | HALF size when c4_stAS_60m_against is YES                     |       0.023 |    -42.9 |       0.032 |    -32.9 | GREEN   |
| K7_0   | 1e       | HALF size when c4_obS_dres_1m_rise is NO                      |       0.029 |    -44.5 |       0.023 |    -36.8 | GREEN   |
| K7_0   | 1f       | HALF size when c4_sqz_60m_onF is YES                          |       0.022 |    -35.7 |       0.02  |    -24.7 | GREEN   |
| K7_0   | 1g       | SKIP the trade when c4_w1_linreg_slope10_renko8_rise is NO    |       0.097 |    -75.3 |       0.131 |    -72.9 | GREEN   |
| K7_0   | 1h       | HALF size when c4_agr_ichiS_kj_fresh5_ge3 is NO               |       0.026 |    -43   |       0.027 |    -33.5 | GREEN   |
| K7_0   | 5a       | SKIP the trade when c_T_tps_W5_own_ratio_ge1.5 is NO          |       0.053 |    -59.6 |       0.097 |    -53.8 | GREEN   |
| K7_0   | 5b       | HALF size when fl011_v0 is NO                                 |       0.035 |    -45.1 |       0.026 |    -35.3 | GREEN   |
| K7_1   | 1        | HALF size when n_bk_failbo_std_60m_against_state is YES       |       0.038 |    -59.7 |       0.035 |    -46.1 | GREEN   |
| K7_1   | 2        | HALF size when c4_cdl_mat_hold_5m_fresh5 is YES               |       0.027 |    -44.6 |       0.035 |    -34.2 | GREEN   |
| K7_1   | 3        | HALF size when c_Z3_any_behind10 is YES                       |       0.002 |     -6.5 |       0.009 |     -8.4 | GREEN   |
| K7_1   | 4        | HALF size when c_R2_v1_hi5 is YES                             |       0.017 |    -52.5 |       0.012 |     -8.7 | GREEN   |
| K7_1   | 5        | SKIP the trade when c_T_cps_W30_other_ratio_ge1.5 is NO       |       0.09  |    -84.4 |       0.051 |    -49.2 | GREEN   |
| K7_1   | 6        | HALF size when c_B5_ALL_15m_macd_ge3of4 is NO                 |       0.028 |    -62.3 |       0.025 |    -30   | GREEN   |
| K7_1   | 7        | HALF size when c_J_0dte_flip_far50_Nh_vol is YES              |       0.022 |    -40   |       0.027 |    -26.4 | GREEN   |
| K7_1   | 8        | SKIP the trade when c_B15_vix_fell_prior_day_with is YES      |       0.088 |    -69.8 |       0.107 |    -67.4 | GREEN   |
| K7_1   | 9        | size x1.5 when c_F9_ss_loser_60m is YES                       |       0.012 |    -20.7 |       0.003 |     -3.6 | GREEN   |
| K7_1   | 1a       | HALF size when n_bk_failbo_std_60m_against_state is YES       |       0.038 |    -59.7 |       0.035 |    -46.1 | GREEN   |
| K7_1   | 1b       | size x1.5 when m_trix30_3m_divwith is YES                     |       0.03  |    -36.7 |       0.02  |    -10   | GREEN   |
| K7_1   | 1c       | size x1.5 when c4_kstS_3m_divwith is YES                      |       0.026 |    -30.3 |       0.022 |    -10.2 | GREEN   |
| K7_1   | 1d       | SKIP the trade when c4_don10_pos_1d_rise is YES               |       0.093 |    -82.8 |       0.111 |    -72.5 | GREEN   |
| K7_1   | 1e       | SKIP the trade when c4_fvgS_dsup_1d_rise is YES               |       0.043 |    -79.9 |       0.015 |    -25.2 | GREEN   |
| K7_1   | 1f       | HALF size when c4_sqz_alt_vol500_fired5_withF is YES          |       0.026 |    -49.8 |       0.027 |    -31.1 | GREEN   |
| K7_1   | 1g       | HALF size when c4_w1_di21_ha60_rise is NO                     |       0.036 |    -61.7 |       0.019 |    -21.5 | GREEN   |
| K7_1   | 1h       | HALF size when c4_agr_obS_dres_hi_ge6 is NO                   |       0.032 |    -52   |       0.001 |    -10.3 | GREEN   |
| K7_1   | 5a       | SKIP the trade when c_T_cps_W30_other_ratio_ge1.5 is NO       |       0.09  |    -84.4 |       0.051 |    -49.2 | GREEN   |
| K7_1   | 5b       | size x1.5 when fl122_d0 is YES                                |       0.022 |    -14.8 |       0.018 |     -7.9 | GREEN   |
| K7_3   | 1        | SKIP the trade when n_eh_roof_fast_1m_fresh5 is YES           |       0.159 |    -81   |       0.236 |    -64.4 | GREEN   |
| K7_3   | 2        | SKIP the trade when c4_cdl_1m_with_gt_against is NO           |       0.124 |    -80.2 |       0.152 |    -65.7 | GREEN   |
| K7_3   | 3        | HALF size when c_Z3_OR30L_behind20 is YES                     |       0.003 |     -4.7 |      -0.004 |     -1.8 | GREEN   |
| K7_3   | 4        | SKIP the trade when c_R2_uwc_hi3 is YES                       |       0.086 |    -64.1 |       0.045 |    -38.5 | GREEN   |
| K7_3   | 5        | SKIP the trade when fl001_d0 is YES                           |       0.099 |    -74.1 |       0.095 |    -57.7 | GREEN   |
| K7_3   | 6        | SKIP the trade when c_I_vix_below_5d is YES                   |       0.067 |    -64   |       0.001 |    -23.7 | GREEN   |
| K7_3   | 7        | SKIP the trade when c_J_ivshort_fell is NO                    |       0.1   |    -80.4 |       0.115 |    -77.1 | GREEN   |
| K7_3   | 8        | HALF size when c_B15_hy_narrowed_5d_with is YES               |       0.029 |    -43   |       0.02  |    -21.7 | GREEN   |
| K7_3   | 9        | SKIP the trade when c_F9_ge3_sess is YES                      |       0.031 |    -46.1 |       0.082 |    -49.4 | GREEN   |
| K7_3   | 10       | SKIP the trade when c_T10_f15_pos_with60 is YES               |       0.033 |    -72.7 |      -0.051 |    -42.4 | GREEN   |
| K7_3   | 1a       | SKIP the trade when n_eh_roof_fast_1m_fresh5 is YES           |       0.159 |    -81   |       0.236 |    -64.4 | GREEN   |
| K7_3   | 1b       | HALF size when m_trend_osc_1d_side is YES                     |       0.038 |    -52.6 |       0.034 |    -32.6 | GREEN   |
| K7_3   | 1c       | SKIP the trade when c4_rsima7_1m_fresh5 is YES                |       0.128 |    -83.9 |       0.164 |    -72.8 | GREEN   |
| K7_3   | 1d       | HALF size when c4_stA21_1d_against is NO                      |       0.036 |    -51.7 |       0.023 |    -23.7 | GREEN   |
| K7_3   | 1e       | SKIP the trade when c4_obS_dsup_1d_rise is NO                 |       0.093 |    -78.4 |       0.103 |    -64.6 | GREEN   |
| K7_3   | 1f       | HALF size when c4_lorF_3m_side is YES                         |       0.029 |    -36.8 |       0.046 |    -25.5 | GREEN   |
| K7_3   | 1g       | size x1.5 when c4_stc_renko8_eenter is YES                    |       0.028 |    -17   |       0.022 |      1   | GREEN   |
| K7_3   | 1h       | SKIP the trade when c4_agr_stcF_eleave_ge3 is YES             |       0.145 |    -83.8 |       0.138 |    -72.1 | GREEN   |
| K7_3   | 5a       | HALF size when c4_fp_1m_poc_with_3of5 is YES                  |       0.022 |    -38.2 |      -0.004 |    -15.2 | GREEN   |
| K7_3   | 5b       | SKIP the trade when fl001_d0 is YES                           |       0.099 |    -74.1 |       0.095 |    -57.7 | GREEN   |
| K7_4   | 1        | SKIP the trade when c4_ichiS_chikou_ha60_hold3 is NO          |       0.139 |    -79.3 |       0.238 |    -85.2 | GREEN   |
| K7_4   | 2        | HALF size when c_N_ict_ntf_atkey_against_ge1 is YES           |       0.053 |    -60.5 |       0.069 |    -47.4 | GREEN   |
| K7_4   | 4        | size x1.5 when c_R2_uwa_lo3 is YES                            |       0.003 |     -7.9 |       0.008 |     -9   | GREEN   |
| K7_4   | 5        | HALF size when fl223_d1 is YES                                |       0.045 |    -60   |       0.06  |    -50.9 | GREEN   |
| K7_4   | 6        | HALF size when c_FL_nqes_open5 is NO                          |       0.039 |    -58.3 |       0.074 |    -53.9 | GREEN   |
| K7_4   | 7        | SKIP the trade when c_J_em_used_lt0.75_Nh is YES              |       0.071 |    -61.3 |       0.146 |    -54.9 | GREEN   |
| K7_4   | 8        | HALF size when n7_w1400_1500_in_with is YES                   |       0.014 |    -26.9 |       0.035 |    -43   | GREEN   |
| K7_4   | 10       | size x1.5 when c_T10_f60_pos_with60 is YES                    |       0.011 |     -8.7 |       0.03  |     -3.7 | GREEN   |
| K7_4   | 1a       | HALF size when n_cn_rsi_pb_std_15m_against_state is YES       |       0.043 |    -57.6 |       0.08  |    -63.9 | GREEN   |
| K7_4   | 1b       | HALF size when m_linreg_slope50_60m_side is NO                |       0.043 |    -61.9 |       0.092 |    -61.1 | GREEN   |
| K7_4   | 1c       | SKIP the trade when c4_smieS_60m_side is NO                   |       0.104 |    -74.3 |       0.175 |    -74.8 | GREEN   |
| K7_4   | 1d       | SKIP the trade when c4_stP_60m_hold3 is NO                    |       0.13  |    -74.4 |       0.24  |    -73.8 | GREEN   |
| K7_4   | 1e       | SKIP the trade when c4_sd_near_mtf_n is YES                   |       0.109 |    -72.1 |       0.213 |    -69.1 | GREEN   |
| K7_4   | 1f       | SKIP the trade when c4_krS_dir_60m_side is NO                 |       0.091 |    -67.8 |       0.11  |    -59.7 | GREEN   |
| K7_4   | 1g       | SKIP the trade when c4_ichiS_chikou_ha60_hold3 is NO          |       0.139 |    -79.3 |       0.238 |    -85.2 | GREEN   |
| K7_4   | 1h       | HALF size when c4_agr_fvgF_in_against_ge3 is YES              |       0.036 |    -44.4 |       0.06  |    -53.1 | GREEN   |
| K7_4   | 5a       | HALF size when c_T_l1_dur_ratio_gt1_L2 is YES                 |       0.049 |    -53.1 |       0.046 |    -37.1 | GREEN   |
| K7_4   | 5b       | HALF size when fl223_d1 is YES                                |       0.045 |    -60   |       0.06  |    -50.9 | GREEN   |
| M7_1   | 1        | HALF size when n_rk_soup_fast_5m_against_state is NO          |       0.041 |    -53.9 |       0.048 |    -32.7 | GREEN   |
| M7_1   | 2        | size x1.5 when c4_chan_posS_60m_rise is YES                   |       0.025 |    -33   |       0.013 |     -7.3 | GREEN   |
| M7_1   | 4        | HALF size when c_R2_v1_ge100 is YES                           |       0.005 |     -4.2 |       0.016 |    -25.8 | GREEN   |
| M7_1   | 5        | size x1.5 when n_fl_ofi1s_with is YES                         |       0.027 |    -30   |       0.025 |    -15.1 | GREEN   |
| M7_1   | 6        | HALF size when n_sd_disp5_lo is NO                            |       0.031 |    -52.1 |       0.015 |    -36.2 | GREEN   |
| M7_1   | 7        | HALF size when c_J_beyond_flip_Nd_vol is NO                   |       0.019 |    -45.9 |       0.018 |    -15.2 | GREEN   |
| M7_1   | 8        | HALF size when c_B15_hy_narrowed_prior_day_with is YES        |       0.027 |    -49.7 |       0.025 |    -27.7 | GREEN   |
| M7_1   | 9        | HALF size when c_F9_ss_loser_prev is YES                      |       0.021 |    -27   |       0.012 |     -9.4 | GREEN   |
| M7_1   | 1a       | HALF size when n_rk_soup_fast_5m_against_state is NO          |       0.041 |    -53.9 |       0.048 |    -32.7 | GREEN   |
| M7_1   | 1b       | SKIP the trade when m_donchian50_pos_1d_side is NO            |       0.092 |    -76.5 |       0.069 |    -55.4 | GREEN   |
| M7_1   | 1c       | SKIP the trade when c4_smiS_1d_side is NO                     |       0.072 |    -73   |       0.028 |    -46.2 | GREEN   |
| M7_1   | 1d       | HALF size when c4_ichiF_thick_1d_rise is NO                   |       0.036 |    -60.2 |       0.012 |    -33.2 | GREEN   |
| M7_1   | 1e       | HALF size when c4_sdF_in_3m_fresh5 is YES                     |       0.034 |    -44.3 |       0.045 |    -26.9 | GREEN   |
| M7_1   | 1f       | SKIP the trade when c4_krF_px_1d_fresh5 is YES                |       0.066 |    -69.5 |       0.067 |    -50.9 | GREEN   |
| M7_1   | 1g       | size x1.5 when c4_w1_cmo14_range16_ewith is YES               |       0.024 |    -30   |       0.029 |     -8.7 | GREEN   |
| M7_1   | 1h       | HALF size when c4_agr_ichi_score_rise_ge3 is YES              |       0.022 |    -49.1 |       0.042 |    -43.6 | GREEN   |
| M7_1   | 5b       | size x1.5 when n_fl_ofi1s_with is YES                         |       0.027 |    -30   |       0.025 |    -15.1 | GREEN   |
| M7_3   | 1        | SKIP the trade when n_bk_failbo_fast_15m_against_state is YES |       0.121 |    -75.4 |       0.128 |    -54   | GREEN   |
| M7_3   | 2        | size x1.5 when c_N_bkB_1_against_cur_ge3 is NO                |       0.028 |    -25.9 |      -0.006 |     31.4 | GREEN   |
| M7_3   | 3        | HALF size when c_Z3_behind_cluster15_ge2 is YES               |       0.005 |    -15.8 |       0.005 |     13.5 | GREEN   |
| M7_3   | 4        | SKIP the trade when c_R2_uwc_hi3 is YES                       |       0.04  |    -47.2 |       0.042 |    -29.6 | GREEN   |
| M7_3   | 5        | SKIP the trade when fl114_d2 is NO                            |       0.123 |    -73.8 |       0.154 |    -31.1 | GREEN   |
| M7_3   | 6        | HALF size when c_B5_RTY_5m_hold21_with is NO                  |       0.031 |    -51.7 |       0.04  |     -3.5 | GREEN   |
| M7_3   | 7        | HALF size when c_J_gex_pos_SPY_oi is YES                      |       0.018 |    -43.2 |       0.004 |    -10.8 | GREEN   |
| M7_3   | 8        | size x1.5 when n16_last3_td_month is YES                      |       0.015 |    -20.9 |       0.01  |      2.1 | GREEN   |
| M7_3   | 9        | HALF size when c_F9_rechase0 is NO                            |       0.019 |    -26.1 |       0.044 |    -21.7 | GREEN   |
| M7_3   | 10       | SKIP the trade when c_T10_mean60_with is NO                   |       0.073 |    -49.7 |       0.093 |      5.9 | GREEN   |
| M7_3   | 1a       | SKIP the trade when n_bk_failbo_fast_15m_against_state is YES |       0.121 |    -75.4 |       0.128 |    -54   | GREEN   |
| M7_3   | 1b       | SKIP the trade when m_vwma8_px_1m_fresh5 is YES               |       0.104 |    -68.6 |       0.063 |    -10.6 | GREEN   |
| M7_3   | 1c       | HALF size when c4_smiF_1d_fresh5 is YES                       |       0.035 |    -53.9 |       0.013 |    -15.7 | GREEN   |
| M7_3   | 1d       | SKIP the trade when c4_mcg_slope_1m_fresh5 is YES             |       0.116 |    -69.7 |       0.043 |    -28.8 | GREEN   |
| M7_3   | 1e       | SKIP the trade when c4_fvgF_cnt_60m_rise is YES               |       0.079 |    -67.1 |       0.017 |     -6.6 | GREEN   |
| M7_3   | 1f       | HALF size when c4_sqz_alt_vol2000_onF is YES                  |       0.037 |    -52.1 |       0.046 |    -33.8 | GREEN   |
| M7_3   | 1g       | HALF size when c4_w1_vwma50_px_ha15_fresh5 is YES             |       0.048 |    -57.7 |       0.017 |    -16.2 | GREEN   |
| M7_3   | 1h       | HALF size when c4_agr_don55_pos_fresh5_ge3 is YES             |       0.039 |    -50.4 |       0.055 |    -29.1 | GREEN   |
| M7_3   | 5a       | size x1.5 when c4_fp_3m_poc_mig_all3 is YES                   |       0.027 |    -27.3 |       0.014 |     11.6 | GREEN   |
| M7_3   | 5b       | SKIP the trade when fl114_d2 is NO                            |       0.123 |    -73.8 |       0.154 |    -31.1 | GREEN   |
| O7_3   | 1        | size x1.5 when c4_eqpool_up_1d_hi is NO                       |       0.067 |     -2.5 |             |          | GREEN   |
| O7_3   | 2        | HALF size when c4_cdl_tweezer_60m_fresh5 is YES               |       0.109 |    -30.2 |             |          | GREEN   |
| O7_3   | 4        | SKIP the trade when c_R2_uwc_hi3 is YES                       |       0.185 |    -39   |             |          | GREEN   |
| O7_3   | 5        | HALF size when fl266_d2 is NO                                 |       0.147 |    -42.4 |             |          | GREEN   |
| O7_3   | 6        | HALF size when c_B5_YM_5m_macd_rising_with is YES             |       0.143 |    -35.2 |             |          | GREEN   |
| O7_3   | 7        | SKIP the trade when c_J_beyond_flip_Nd_oi is NO               |       0.156 |    -41.9 |             |          | GREEN   |
| O7_3   | 8        | HALF size when c_B15_6E_up_since_0930_with is YES             |       0.053 |    -26.9 |             |          | GREEN   |
| O7_3   | 9        | SKIP the trade when c_F9_prev3_loss is YES                    |       0.189 |    -52.1 |             |          | GREEN   |
| O7_3   | 10       | SKIP the trade when c_T10_pos60_against60 is YES              |       0.141 |    -50.4 |             |          | GREEN   |
| O7_3   | 1a       | HALF size when n_rk_soup_fast_3m_against_state is NO          |       0.15  |    -40.4 |             |          | GREEN   |
| O7_3   | 1b       | SKIP the trade when m_mfi7_agree3of4 is NO                    |       0.448 |    -66.5 |             |          | GREEN   |
| O7_3   | 1c       | SKIP the trade when c4_smiS_5m_fresh5 is YES                  |       0.424 |    -66.6 |             |          | GREEN   |
| O7_3   | 1d       | HALF size when c4_ichi_cloud_15m_against is YES               |       0.136 |    -41   |             |          | GREEN   |
| O7_3   | 1e       | size x1.5 when c4_eqpool_up_1d_hi is NO                       |       0.067 |     -2.5 |             |          | GREEN   |
| O7_3   | 1f       | HALF size when c4_avwap_swing_hi_60m_far is NO                |       0.13  |    -35.9 |             |          | GREEN   |
| O7_3   | 1g       | SKIP the trade when c4_obF_cnt_ha3_side is NO                 |       0.495 |    -73.9 |             |          | GREEN   |
| O7_3   | 1h       | HALF size when c4_agr_ichi_futcloud_hold3_ge6 is NO           |       0.12  |    -36.1 |             |          | GREEN   |
| O7_3   | 5a       | HALF size when c_T_l5_pbmed_mps_gt1.0_L0 is YES               |       0.091 |    -31.2 |             |          | GREEN   |
| O7_3   | 5b       | HALF size when fl266_d2 is NO                                 |       0.147 |    -42.4 |             |          | GREEN   |
| P7_0   | 1        | SKIP the trade when c4_agr_obS_dres_rise_ge6 is NO            |       0.087 |    -63.2 |       0.058 |    -53   | GREEN   |
| P7_0   | 2        | SKIP the trade when c_N_dm_60_cd_support_ge8 is YES           |       0.063 |    -59.1 |       0.038 |    -27.3 | GREEN   |
| P7_0   | 4        | SKIP the trade when c_R2_uwc_hi5 is YES                       |       0.077 |    -62.2 |       0.043 |    -24.1 | GREEN   |
| P7_0   | 5        | SKIP the trade when fl224_v0 is YES                           |       0.087 |    -65.4 |       0.161 |    -42.1 | GREEN   |
| P7_0   | 6        | SKIP the trade when c_I_NQ_leads_ES5 is NO                    |       0.053 |    -60   |       0.031 |    -26.5 | GREEN   |
| P7_0   | 7        | SKIP the trade when c_J_netgamma_pos_Nd_vol is NO             |       0.04  |    -48.8 |       0.042 |    -46.1 | GREEN   |
| P7_0   | 8        | SKIP the trade when c_B15_ZBminusZN_since_open_with is NO     |       0.037 |    -59.8 |       0.041 |    -27.9 | GREEN   |
| P7_0   | 9        | HALF size when c_F9_day_ge5 is YES                            |       0.005 |    -31.3 |       0.004 |     -9.2 | GREEN   |
| P7_0   | 1a       | SKIP the trade when n_ch_fosc_fast_15m_sig is YES             |       0.068 |    -63.3 |       0.123 |    -65.3 | GREEN   |
| P7_0   | 1b       | SKIP the trade when c_S_corr60_rty_ge0.7 is YES               |       0.066 |    -63.5 |      -0.006 |    -18.3 | GREEN   |
| P7_0   | 1c       | HALF size when c4_kvo_15m_fresh5 is YES                       |       0.023 |    -48.6 |       0.027 |    -16.3 | GREEN   |
| P7_0   | 1d       | HALF size when c4_t3_px_3m_divwith is YES                     |       0.027 |    -43.1 |       0.026 |    -20.4 | GREEN   |
| P7_0   | 1e       | HALF size when c4_eqpool_up_1d_rise is YES                    |       0.018 |    -49.5 |       0.003 |    -17.8 | GREEN   |
| P7_0   | 1f       | HALF size when c4_cvdS_60m_side is NO                         |       0.027 |    -48.3 |       0.018 |    -44.1 | GREEN   |
| P7_0   | 1g       | HALF size when c4_w1_adx21_ha60_hi_z1 is YES                  |       0.028 |    -52.3 |       0.036 |    -40.2 | GREEN   |
| P7_0   | 1h       | SKIP the trade when c4_agr_obS_dres_rise_ge6 is NO            |       0.087 |    -63.2 |       0.058 |    -53   | GREEN   |
| P7_0   | 5a       | SKIP the trade when c_T_mps_book_W5_own_pct_hi is YES         |       0.06  |    -61.4 |       0.043 |    -40.9 | GREEN   |
| P7_0   | 5b       | SKIP the trade when fl224_v0 is YES                           |       0.087 |    -65.4 |       0.161 |    -42.1 | GREEN   |
| P7_1   | 1        | HALF size when c4_fractal_brk_renko16_hold3 is NO             |       0.03  |    -43.3 |       0.029 |    -31.5 | GREEN   |
| P7_1   | 2        | HALF size when c_N_dm_5_flip_support_w5 is YES                |       0.031 |    -44.5 |       0.022 |    -33.9 | GREEN   |
| P7_1   | 4        | SKIP the trade when c_R2_har_tgtover075 is NO                 |       0.032 |    -46.1 |       0.045 |    -55.3 | GREEN   |
| P7_1   | 5        | SKIP the trade when fl061_v0 is YES                           |       0.099 |    -70   |       0.197 |    -81.7 | GREEN   |
| P7_1   | 6        | HALF size when c_I_ZN_with60 is NO                            |       0.021 |    -44.8 |       0.062 |    -39.1 | GREEN   |
| P7_1   | 7        | HALF size when c_J_beyond_flip_NDX_oi is NO                   |       0.021 |    -28.8 |       0.013 |    -14.3 | GREEN   |
| P7_1   | 8        | SKIP the trade when c_B15_ZBminusZN_since_open_with is YES    |       0.052 |    -66.7 |       0.113 |    -66.1 | GREEN   |
| P7_1   | 9        | size x1.5 when c_F9_ss_loser_30m is YES                       |       0.015 |     -6.7 |       0.015 |      0.1 | GREEN   |
| P7_1   | 1a       | SKIP the trade when n_bk_trendbars5_1m_rise is YES            |       0.083 |    -56   |       0.181 |    -73.3 | GREEN   |
| P7_1   | 1b       | HALF size when c_A_kc_out_3m is YES                           |       0.029 |    -44.7 |       0.041 |    -35.3 | GREEN   |
| P7_1   | 1c       | SKIP the trade when c4_wtS_60m_sig is NO                      |       0.069 |    -53.9 |       0.041 |    -42.3 | GREEN   |
| P7_1   | 1d       | SKIP the trade when c4_ichiF_thick_1m_rise is NO              |       0.1   |    -61.8 |       0.103 |    -57.3 | GREEN   |
| P7_1   | 1e       | SKIP the trade when c4_sdS_dsup_1d_rise is YES                |       0.073 |    -58.5 |       0.042 |    -49.7 | GREEN   |
| P7_1   | 1f       | HALF size when c4_vp_frsw_in_va is NO                         |       0.021 |    -40.5 |       0.034 |    -28.5 | GREEN   |
| P7_1   | 1g       | HALF size when c4_fractal_brk_renko16_hold3 is NO             |       0.03  |    -43.3 |       0.029 |    -31.5 | GREEN   |
| P7_1   | 1h       | HALF size when c4_agr_w1_hma_stack_fast_side_ge6 is YES       |       0.04  |    -49.4 |       0.032 |    -39.6 | GREEN   |
| P7_1   | 5a       | size x1.5 when c_T_tps_W5_own_pct_lo is YES                   |       0.021 |    -19.9 |       0.024 |     -3   | GREEN   |
| P7_1   | 5b       | SKIP the trade when fl061_v0 is YES                           |       0.099 |    -70   |       0.197 |    -81.7 | GREEN   |
| P7_3   | 1        | SKIP the trade when c4_rviS_tick2000_fresh5 is YES            |       0.121 |    -77.4 |       0.118 |    -68.1 | GREEN   |
| P7_3   | 2        | HALF size when c4_cdl_inside_break_15m_against5 is YES        |       0.032 |    -37.5 |       0.041 |    -24.8 | GREEN   |
| P7_3   | 3        | HALF size when c_Z3_behind_cluster15_ge2 is YES               |       0.011 |    -19   |       0.027 |    -33   | GREEN   |
| P7_3   | 4        | SKIP the trade when c_R2_uwa_hi3 is YES                       |       0.095 |    -71.1 |       0.008 |    -49.5 | GREEN   |
| P7_3   | 5        | size x1.5 when c4_fp_5m_dtop_with is NO                       |       0.028 |    -23.2 |       0.018 |     -6.1 | GREEN   |
| P7_3   | 6        | SKIP the trade when n_sd_rviv240_gt1 is YES                   |       0.12  |    -68   |       0.048 |    -48.1 | GREEN   |
| P7_3   | 7        | HALF size when c_J_tide_ncp_s_pos is NO                       |       0.048 |    -50.5 |       0.031 |    -27.5 | GREEN   |
| P7_3   | 8        | SKIP the trade when c_B15_cot_am_net_pct_le20 is YES          |       0.068 |    -62.6 |       0.012 |    -47.5 | GREEN   |
| P7_3   | 9        | SKIP the trade when c_F9_gap_le900 is YES                     |       0.022 |    -55.9 |      -0.015 |    -28.2 | GREEN   |
| P7_3   | 10       | SKIP the trade when c_T10_mean30_with is NO                   |       0.027 |    -49.7 |       0.076 |    -57.1 | GREEN   |
| P7_3   | 1a       | SKIP the trade when n_ks_peak14_60m_side is NO                |       0.153 |    -82.6 |       0.111 |    -75.4 | GREEN   |
| P7_3   | 1b       | HALF size when m_macd19_39_9_line_60m_sig is NO               |       0.058 |    -66.3 |       0.062 |    -60.6 | GREEN   |
| P7_3   | 1c       | HALF size when c4_stc_60m_eagainst is YES                     |       0.057 |    -62.2 |       0.044 |    -46.8 | GREEN   |
| P7_3   | 1d       | HALF size when c4_zlemaS_px_60m_side is NO                    |       0.066 |    -68   |       0.06  |    -58.1 | GREEN   |
| P7_3   | 1e       | SKIP the trade when c4_chochF_60m_against is YES              |       0.13  |    -76.1 |       0.069 |    -70.6 | GREEN   |
| P7_3   | 1f       | HALF size when c4_sqz_60m_mom_withF is NO                     |       0.04  |    -61.4 |       0.017 |    -50.9 | GREEN   |
| P7_3   | 1g       | SKIP the trade when c4_rviS_tick2000_fresh5 is YES            |       0.121 |    -77.4 |       0.118 |    -68.1 | GREEN   |
| P7_3   | 1h       | size x1.5 when c4_agr_fvgS_dsup_hi_ge6 is NO                  |       0.032 |    -22.6 |       0.038 |    -10.5 | GREEN   |
| P7_3   | 5a       | size x1.5 when c4_fp_5m_dtop_with is NO                       |       0.028 |    -23.2 |       0.018 |     -6.1 | GREEN   |
| P7_3   | 5b       | SKIP the trade when fl204_d1 is NO                            |       0.066 |    -71.6 |       0.005 |    -64.3 | GREEN   |
| U7_0   | 1        | HALF size when c4_chopF_1m_rise is NO                         |       0.045 |    -35.3 |       0.06  |    -40.1 | GREEN   |
| U7_0   | 2        | SKIP the trade when c4_cdl_5m_against_ge1 is NO               |       0.085 |    -40.4 |       0.03  |    -35.2 | GREEN   |
| U7_0   | 3        | HALF size when c_Z3_DL_at5 is YES                             |       0.023 |    -24.1 |       0.05  |    -35.4 | GREEN   |
| U7_0   | 4        | HALF size when c_R2_v1_tgtover075 is NO                       |       0.032 |    -29.5 |       0.05  |    -39   | GREEN   |
| U7_0   | 5        | SKIP the trade when fl258_v0 is YES                           |       0.21  |    -57.6 |       0.213 |    -58.8 | GREEN   |
| U7_0   | 6        | HALF size when c_I_6J_yen_weakening60 is NO                   |       0.025 |    -25.7 |       0.018 |    -23.2 | GREEN   |
| U7_0   | 7        | HALF size when c_J_beyond_flip_SPX_vol is NO                  |       0.039 |    -34   |       0.008 |    -32.8 | GREEN   |
| U7_0   | 8        | HALF size when c_B15_6E_up_since_open_with is NO              |       0.04  |    -29.4 |       0.057 |    -29.6 | GREEN   |
| U7_0   | 9        | HALF size when c_F9_rechase10 is NO                           |       0.037 |    -34.9 |       0.05  |    -37.3 | GREEN   |
| U7_0   | 1a       | HALF size when n_bk_trendbars5_15m_rise is YES                |       0.068 |    -41.2 |       0.12  |    -50   | GREEN   |
| U7_0   | 1b       | HALF size when c_A_hhhl_3m is NO                              |       0.048 |    -38.1 |       0.068 |    -43.5 | GREEN   |
| U7_0   | 1c       | HALF size when c4_chopF_1m_rise is NO                         |       0.045 |    -35.3 |       0.06  |    -40.1 | GREEN   |
| U7_0   | 1d       | HALF size when c4_utbotF_5m_fresh5 is YES                     |       0.043 |    -40.2 |       0.054 |    -44.3 | GREEN   |
| U7_0   | 1e       | HALF size when c4_obS_dres_3m_rise is YES                     |       0.064 |    -36.6 |       0.094 |    -39.6 | GREEN   |
| U7_0   | 1f       | SKIP the trade when c4_cvdF_5m_fresh5 is YES                  |       0.133 |    -48.1 |       0.099 |    -59.2 | GREEN   |
| U7_0   | 1g       | HALF size when c4_w1_stochrsi14_ha5_rise is YES               |       0.049 |    -42.4 |       0.105 |    -48.5 | GREEN   |
| U7_0   | 1h       | SKIP the trade when c4_agr_fractal_brk_fresh5_ge3 is YES      |       0.153 |    -46.4 |       0.216 |    -47.2 | GREEN   |
| U7_0   | 5a       | HALF size when c_T_share_tps_W300_other_pct_lo is YES         |       0.045 |    -28.1 |       0.004 |    -37.9 | GREEN   |
| U7_0   | 5b       | SKIP the trade when fl258_v0 is YES                           |       0.21  |    -57.6 |       0.213 |    -58.8 | GREEN   |
| U7_1   | 1        | HALF size when c4_ssl_range16_hold3 is NO                     |       0.098 |    -50.2 |       0.115 |    -51.8 | GREEN   |
| U7_1   | 2        | HALF size when c4_irl_any_ext_against_30 is YES               |       0.057 |    -33.7 |       0.034 |    -29   | GREEN   |
| U7_1   | 3        | SKIP the trade when c_Z3_cluster10_ge2 is YES                 |       0.001 |     -0.8 |      -0.006 |     -4   | GREEN   |
| U7_1   | 4        | HALF size when c_R2_uwb_lo3 is YES                            |       0.016 |    -10.7 |       0.013 |    -16.6 | GREEN   |
| U7_1   | 5        | HALF size when fl242_v0 is NO                                 |       0.061 |    -36.6 |       0.078 |    -48.4 | GREEN   |
| U7_1   | 6        | SKIP the trade when c_B5_MEGA_15m_macd_rising_with is YES     |       0.1   |    -40.1 |       0.124 |    -55.3 | GREEN   |
| U7_1   | 7        | SKIP the trade when c_J_beyond_flip_SPX_oi is YES             |       0.064 |    -41.1 |       0.152 |    -44.7 | GREEN   |
| U7_1   | 8        | HALF size when c_B15_curve_steepened_ge3bp is YES             |       0.027 |    -24.2 |       0.043 |    -29.3 | GREEN   |
| U7_1   | 9        | HALF size when c_F9_rechase0 is NO                            |       0.013 |     -1.4 |       0.043 |    -27.3 | GREEN   |
| U7_1   | 1a       | SKIP the trade when n_ch_fosc_fast_60m_nodiv is NO            |       0.128 |    -51.3 |       0.207 |    -70.1 | GREEN   |
| U7_1   | 1b       | HALF size when m_sma50_px_15m_rise is YES                     |       0.058 |    -37.1 |       0.066 |    -42.8 | GREEN   |
| U7_1   | 1c       | SKIP the trade when c4_crsiF_60m_nodiv is NO                  |       0.127 |    -46.6 |       0.16  |    -57.4 | GREEN   |
| U7_1   | 1d       | HALF size when c4_ichiF_thick_1d_rise is NO                   |       0.05  |    -36.9 |       0.083 |    -49.1 | GREEN   |
| U7_1   | 1e       | HALF size when c4_sdS_near_3m_against is NO                   |       0.042 |    -39.8 |       0.094 |    -48.7 | GREEN   |
| U7_1   | 1f       | HALF size when c4_sqz_alt_renko8_mom_rise_with is NO          |       0.077 |    -40   |       0.142 |    -50.7 | GREEN   |
| U7_1   | 1g       | HALF size when c4_ssl_range16_hold3 is NO                     |       0.098 |    -50.2 |       0.115 |    -51.8 | GREEN   |
| U7_1   | 1h       | SKIP the trade when c4_agr_ssl_against_ge3 is YES             |       0.184 |    -70   |       0.129 |    -68.7 | GREEN   |
| U7_1   | 5a       | SKIP the trade when c_T_mps_all_W5_own_ratio_ge2 is YES       |       0.139 |    -43.4 |       0.082 |    -44.1 | GREEN   |
| U7_1   | 5b       | HALF size when fl242_v0 is NO                                 |       0.061 |    -36.6 |       0.078 |    -48.4 | GREEN   |

Score today: the family score is the equal-weight vote of the five picks above (+1 favourable state, -1 unfavourable, 0 unknown); D7 computes it live only if every pick in its list is computable live (last column); a cell whose top 5 are all L3 / UW / other-market columns cannot be run today.

## Reading, caveats and what goes to stage 2
- A pick procedure that "wins" by trading less is exposed by the random-skip draws (same share, same action) and by the shifted-label procedure; only the excess over them counts. Families whose rolling OOS beats the nulls go forward to stage 2 as one score per book, jointly with the bar swap, bracket picks and stack rules, then the exact engine with controls (not in this page).
- Family 1 holds 83% of the 63,626 columns (alt-bar copies of the same indicators): its selection pressure is the highest, so the shifted-label null for family 1 is the one to read; sub-families 1a-1h are shown separately.
- UW levels as exits, the bracket table, the bar swap, new books and behaviour rules (ordered 18:10Z / 18:13Z) are other agents' tables: this page covers the entry conditions, scores and the honest wait / early-exit versions. Level sets: own zones and session/round-number levels are in family 3 (68 at-entry columns); UW levels and own-book walls are in 7 / 5b where the stage-1 store has them.
- No engine cells were added. Scripts: code/th_s1r/ (s1r_assemble.py, s1r_core.py, s1r_eval.py, s1r_wait.py, s1r_weval.py, s1r_page.py); intermediates /mnt/l2/l2vast/_s1r/.
