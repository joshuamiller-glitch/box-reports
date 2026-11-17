# DS3_REBUILD_S1R - Stage 1R: every entry condition re-scored by the user's rolling rule on the RAW books (W-S1R)

1. WHICH WORK under the user's rule (recent-data picks, refit every 2 weeks, OOS chained, label needs excess over the shifted-label / random-skip / nonsense nulls): none. WEAK-BUT-POSITIVE (positive OOS but not clearly past the nulls): 2, 6, 7, 8, 1c, 1e.
2. WHICH DO NOT: 1, 3, 4, 5, 9, 10, 1a, 1b, 1d, 1f, 1g, 1h, 5a, 5b, ALL (BEST-AVAILABLE-NOT-PROVEN: the rolling picks do not beat what the same procedure earns on shifted labels / random skips). Control columns (nonsense / random / planted) under the same procedure: NONS=BEST-AVAILABLE-NOT-PROVEN, RAND=WEAK-BUT-POSITIVE, PLANT=CONFIRMED.
3. ALL families pooled, top-5 picks, trailing 6M, 15% prior-year gate, next 2 weeks chained over 1 book x session cells: BEST-AVAILABLE-NOT-PROVEN; OOS dMeanR -0.008 R, dUlcer -18.6%, persistence 42% (bar 60%) vs shifted-label nulls -0.000 R / -13.7% (see the first table for the sub-families).
4. TODAY'S PICKS (refit ending 2026-10-30, pick window 2026-05-01..2026-10-30 / 3M 2026-08-01..): per book x session in the "Current picks" section below (top 5 and the best pick per family, with 6M and 3M effect, prior-year 15/30 flags, feed need and whether D7 can compute it live); CSVs /mnt/l2/l2vast/_s1r/eval/picks_now_all.csv and picks_now_family.csv.
5. DATA END 2026-10-30 (engine store ends there; November 2026 is not in the raw engine base so it could not be extended); cells done 1/15 as of 2026-11-17 19:39 UTC; first table 00:20Z, full set 06:20Z; wait-then-enter / early-exit and the score votes are in their own sections. Label scale: CONFIRMED / LEAD / WEAK-BUT-POSITIVE / BEST-AVAILABLE-NOT-PROVEN (rules below).

> VALIDATION (FIRST PASS, written 2026-11-17 19:39 UTC): rule = the user's standing selection rule (autopilot/DIRECTIVE_SELECTION_RULE_20261117.md, STAGE1R order 18:17Z): pick on the TRAILING 6 months (3 months shown beside), refit every 14 days from 2023-10-02 to 2026-10-31, prior-years check = not-a-disaster at 15%/30%, validated by walking the procedure forward (OOS pieces chained), NOT a frozen holdout. Trials counted: 63626 candidate columns x 2 sides x 3 actions per cell and refit (65,192 columns in the stage-1 store; 63,626 at-entry-clean + 299 controls scored here) x 15 cells x 79 refits x 2 windows x 4 label versions; correction = nulls (shifted labels 11/23/37 days, nonsense/random/planted columns, 10 random persistent skips with the same share and action), plus the label rules below; no White RC/SPA/DSR/PBO is computed (a rolling pick procedure is evaluated by its OOS excess over nulls instead); NOT engine-exact (raw-chassis trade P&L at base lots, $4.84 RT), no re-entry or freed-book effects; the engine-exact stage-2 run comes later via the lead. Data end 2026-10-30; pick-window end 2026-10-30; refit date 2026-10-31.

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
| 1     | F1 confluence library (all)                                                | BEST-AVAILABLE-NOT-PROVEN |       -0.007 |         -19.1 | 20267/24887           |     -29 | 77%        | 38%       |               0.001 |                -20.9 | no                   | 60%/10%                           |           1 | no                 |
| 2     | candle counting, ICT 7-13-21, IRL/ERL                                      | WEAK-BUT-POSITIVE         |        0.001 |         -15   | 21259/24887           |     -12 | 79%        | 49%       |              -0.012 |                -12.7 | no                   | 50%/30%                           |           2 | no                 |
| 3     | levels and zones (own zones, session/round levels)                         | BEST-AVAILABLE-NOT-PROVEN |        0.013 |         -31.5 | 17001/24887           |      13 | 78%        | 38%       |               0.014 |                -33.3 | no                   | 70%/50%                           |           1 | yes                |
| 4     | range forecasts (HAR / options / UW / own bar)                             | BEST-AVAILABLE-NOT-PROVEN |        0.005 |         -44.2 | 14735/24887           |      -5 | 78%        | 44%       |               0.008 |                -30   | no                   | 100%/50%                          |           1 | no                 |
| 5     | F5 order flow (all)                                                        | BEST-AVAILABLE-NOT-PROVEN |        0.003 |         -20.9 | 19053/24887           |     -14 | 70%        | 40%       |               0.011 |                -36.6 | no                   | 30%/80%                           |           1 | yes                |
| 6     | other markets and breadth                                                  | WEAK-BUT-POSITIVE         |        0.022 |         -26.5 | 17825/24887           |      28 | 75%        | 45%       |              -0.01  |                -20   | no                   | 60%/100%                          |           2 | yes                |
| 7     | Unusual Whales options / positioning                                       | WEAK-BUT-POSITIVE         |        0.005 |          -2.7 | 26367/24887           |      11 | 96%        | 47%       |              -0.015 |                  6.5 | no                   | 50%/90%                           |           0 | no                 |
| 8     | day / regime / time of day / calendar                                      | WEAK-BUT-POSITIVE         |        0.005 |         -29.8 | 16627/24887           |      -2 | 80%        | 44%       |              -0.01  |                 -8.7 | yes                  | 80%/60%                           |           2 | yes                |
| 9     | causal trade context (raw)                                                 | BEST-AVAILABLE-NOT-PROVEN |        0.016 |         -29.4 | 18810/24887           |      22 | 82%        | 47%       |               0.022 |                -32.1 | no                   | 90%/100%                          |           3 | yes                |
| 10    | TICK internals                                                             | BEST-AVAILABLE-NOT-PROVEN |        0.008 |         -23.3 | 19965/24887           |       6 | 81%        | 51%       |              -0.004 |                -23.7 | no                   | 50%/30%                           |           3 | no                 |
| 1a    | confluence: named indicators / session anchors                             | BEST-AVAILABLE-NOT-PROVEN |        0.015 |         -22.2 | 19868/24887           |       8 | 70%        | 52%       |              -0     |                -39   | no                   | 30%/90%                           |           2 | yes                |
| 1b    | confluence: entry-table universe                                           | BEST-AVAILABLE-NOT-PROVEN |       -0.01  |         -18.1 | 20608/24887           |     -38 | 71%        | 48%       |               0.014 |                -35.7 | no                   | 10%/30%                           |           1 | yes                |
| 1c    | confluence: oscillators                                                    | WEAK-BUT-POSITIVE         |        0.026 |         -34.4 | 16986/24887           |      29 | 70%        | 45%       |              -0.004 |                -32.8 | no                   | 80%/100%                          |           3 | yes                |
| 1d    | confluence: trend                                                          | BEST-AVAILABLE-NOT-PROVEN |        0.008 |         -35.8 | 16823/24887           |      -5 | 70%        | 50%       |               0.017 |                -34.2 | no                   | 100%/80%                          |           3 | yes                |
| 1e    | confluence: SMC / ICT structure                                            | WEAK-BUT-POSITIVE         |        0.02  |         -38.4 | 15166/24887           |      24 | 75%        | 54%       |               0.004 |                -22.6 | yes                  | 80%/80%                           |           2 | yes                |
| 1f    | confluence: vol / squeeze / state / ML                                     | BEST-AVAILABLE-NOT-PROVEN |       -0.016 |         -12   | 20215/24887           |     -50 | 72%        | 45%       |               0     |                -23.1 | no                   | 30%/10%                           |           1 | yes                |
| 1g    | confluence: alternate-bar indicators (HA, range, renko, tick, volume bars) | BEST-AVAILABLE-NOT-PROVEN |       -0.013 |         -18.7 | 19708/24887           |     -43 | 73%        | 42%       |              -0.019 |                  1.7 | no                   | 30%/20%                           |           1 | no                 |
| 1h    | confluence: alt-bar agreement                                              | BEST-AVAILABLE-NOT-PROVEN |        0.009 |         -36.7 | 15385/24887           |      -1 | 74%        | 47%       |               0.014 |                -37.4 | no                   | 100%/80%                          |           2 | no                 |
| 5a    | order flow: tape prints and speed                                          | BEST-AVAILABLE-NOT-PROVEN |       -0.008 |          -5.2 | 23919/24887           |     -32 | 77%        | 42%       |               0.008 |                -37.4 | no                   | 0%/20%                            |           1 | yes                |
| 5b    | order flow: L3 / L2 book / flow library                                    | BEST-AVAILABLE-NOT-PROVEN |        0.009 |         -25.7 | 18098/24887           |      -3 | 71%        | 40%       |               0.011 |                -33.6 | no                   | 50%/90%                           |           1 | no                 |
| ALL   | ALL families pooled                                                        | BEST-AVAILABLE-NOT-PROVEN |       -0.008 |         -18.6 | 20677/24887           |     -32 | 77%        | 42%       |              -0     |                -13.7 | no                   | 70%/10%                           |           1 | no                 |
| NONS  | CONTROL nonsense columns (200)                                             | BEST-AVAILABLE-NOT-PROVEN |       -0.002 |         -28.1 | 17063/24887           |     -29 | 62%        | 51%       |               0.009 |                -34.6 | no                   | 50%/50%                           |           1 | no                 |
| RAND  | CONTROL persistent random columns (90)                                     | WEAK-BUT-POSITIVE         |        0.016 |         -43.5 | 15286/24887           |      13 | 73%        | 43%       |               0.004 |                -23.8 | yes                  | 90%/90%                           |           2 | no                 |
| PLANT | CONTROL planted-edge columns (9)                                           | CONFIRMED                 |        0.031 |         -16.8 | 22176/24887           |      99 | 111%       | 64%       |              -0.017 |                 25.6 | yes                  | 100%/100%                         |           2 | yes                |

Same, trailing 3M picks:
| set   | what                                                                       | label                     |   OOS dMeanR |   OOS dUlcer% | dMaxDD$ (rule/base)   |   d$/wk | exposure   | persist   |   shift-null dMeanR |   shift-null dUlcer% | beats all 3 shifts   | beats random-skip draws (dU/dm)   |   thirds ok | 3M-window agrees   |
|:------|:---------------------------------------------------------------------------|:--------------------------|-------------:|--------------:|:----------------------|--------:|:-----------|:----------|--------------------:|---------------------:|:---------------------|:----------------------------------|------------:|:-------------------|
| 1     | F1 confluence library (all)                                                | BEST-AVAILABLE-NOT-PROVEN |       -0.006 |         -37.5 | 7140/9422             |     -22 | 77%        | 44%       |              -0.011 |                 -9.4 | no                   | /                                 |           1 | no                 |
| 2     | candle counting, ICT 7-13-21, IRL/ERL                                      | BEST-AVAILABLE-NOT-PROVEN |       -0     |         -18.1 | 8737/9422             |     -19 | 74%        | 50%       |               0.002 |                -19.9 | no                   | /                                 |           1 | yes                |
| 3     | levels and zones (own zones, session/round levels)                         | WEAK-BUT-POSITIVE         |        0.021 |         -40.9 | 8159/9422             |       7 | 83%        | 50%       |               0.018 |                 -6.3 | no                   | /                                 |           3 | yes                |
| 4     | range forecasts (HAR / options / UW / own bar)                             | BEST-AVAILABLE-NOT-PROVEN |       -0.032 |          -9.2 | 7575/9422             |     -42 | 82%        | 45%       |               0.029 |                -29.2 | no                   | /                                 |           0 | yes                |
| 5     | F5 order flow (all)                                                        | BEST-AVAILABLE-NOT-PROVEN |        0.013 |         -23.3 | 8147/9422             |      -9 | 73%        | 44%       |               0.016 |                -23.6 | no                   | /                                 |           2 | yes                |
| 6     | other markets and breadth                                                  | BEST-AVAILABLE-NOT-PROVEN |        0     |         -33.7 | 6710/9422             |     -22 | 70%        | 45%       |               0.014 |                -26.6 | no                   | /                                 |           1 | yes                |
| 7     | Unusual Whales options / positioning                                       | BEST-AVAILABLE-NOT-PROVEN |       -0.013 |           2.6 | 10601/9422            |     -16 | 96%        | 44%       |              -0.027 |                -10.4 | no                   | /                                 |           0 | yes                |
| 8     | day / regime / time of day / calendar                                      | WEAK-BUT-POSITIVE         |        0.003 |         -26.7 | 5430/9422             |     -17 | 73%        | 44%       |              -0.006 |                -18.6 | no                   | /                                 |           1 | yes                |
| 9     | causal trade context (raw)                                                 | BEST-AVAILABLE-NOT-PROVEN |        0.015 |          -8.4 | 8496/9422             |       0 | 82%        | 44%       |               0.047 |                 -9.8 | no                   | /                                 |           2 | yes                |
| 10    | TICK internals                                                             | BEST-AVAILABLE-NOT-PROVEN |       -0.012 |         -25.4 | 7079/9422             |     -31 | 71%        | 32%       |              -0.008 |                 -2.8 | no                   | /                                 |           1 | yes                |
| 1a    | confluence: named indicators / session anchors                             | WEAK-BUT-POSITIVE         |        0.011 |         -20.5 | 7352/9422             |     -18 | 65%        | 47%       |              -0     |                -14.2 | no                   | /                                 |           2 | yes                |
| 1b    | confluence: entry-table universe                                           | WEAK-BUT-POSITIVE         |        0.032 |         -50.8 | 5697/9422             |       8 | 75%        | 53%       |               0.016 |                -30.4 | yes                  | /                                 |           2 | no                 |
| 1c    | confluence: oscillators                                                    | WEAK-BUT-POSITIVE         |        0.029 |         -50.9 | 6469/9422             |      -1 | 69%        | 56%       |               0.02  |                -27.9 | no                   | /                                 |           1 | yes                |
| 1d    | confluence: trend                                                          | WEAK-BUT-POSITIVE         |        0.048 |         -64.3 | 4010/9422             |       9 | 66%        | 38%       |               0.009 |                -27.2 | yes                  | /                                 |           3 | yes                |
| 1e    | confluence: SMC / ICT structure                                            | BEST-AVAILABLE-NOT-PROVEN |        0.003 |          -6   | 8719/9422             |     -16 | 75%        | 56%       |              -0.006 |                -14.4 | no                   | /                                 |           2 | yes                |
| 1f    | confluence: vol / squeeze / state / ML                                     | WEAK-BUT-POSITIVE         |        0.017 |         -55.1 | 5178/9422             |      -9 | 70%        | 50%       |              -0.006 |                -21.8 | yes                  | /                                 |           2 | no                 |
| 1g    | confluence: alternate-bar indicators (HA, range, renko, tick, volume bars) | BEST-AVAILABLE-NOT-PROVEN |       -0.001 |         -31.1 | 6506/9422             |     -19 | 75%        | 44%       |               0.001 |                -29.4 | no                   | /                                 |           2 | no                 |
| 1h    | confluence: alt-bar agreement                                              | BEST-AVAILABLE-NOT-PROVEN |       -0.003 |         -15.2 | 8922/9422             |     -23 | 73%        | 36%       |               0.008 |                -40   | no                   | /                                 |           2 | yes                |
| 5a    | order flow: tape prints and speed                                          | BEST-AVAILABLE-NOT-PROVEN |        0.03  |         -21.8 | 8260/9422             |      -1 | 69%        | 35%       |               0.001 |                -28   | no                   | /                                 |           2 | no                 |
| 5b    | order flow: L3 / L2 book / flow library                                    | BEST-AVAILABLE-NOT-PROVEN |       -0.013 |         -12   | 8955/9422             |     -29 | 75%        | 41%       |               0.015 |                -24.8 | no                   | /                                 |           1 | yes                |
| ALL   | ALL families pooled                                                        | BEST-AVAILABLE-NOT-PROVEN |       -0.016 |         -26.9 | 8755/9422             |     -30 | 78%        | 45%       |               0.023 |                -33.8 | no                   | /                                 |           0 | no                 |
| NONS  | CONTROL nonsense columns (200)                                             | BEST-AVAILABLE-NOT-PROVEN |       -0.015 |         -13.5 | 8285/9422             |     -38 | 63%        | 38%       |              -0.005 |                -22.9 | no                   | /                                 |           1 | no                 |
| RAND  | CONTROL persistent random columns (90)                                     | BEST-AVAILABLE-NOT-PROVEN |       -0.007 |         -28.3 | 8007/9422             |     -28 | 69%        | 36%       |               0.014 |                -36.1 | no                   | /                                 |           0 | yes                |
| PLANT | CONTROL planted-edge columns (9)                                           | WEAK-BUT-POSITIVE         |        0.002 |          -6.2 | 9422/9422             |       4 | 102%       | 50%       |              -0.017 |                 12.3 | yes                  | /                                 |           0 | yes                |

## By number of picks (N) and prior-year gate (all families pooled and each main family, 6M, next 2 weeks)
| set   | gate   |   N | label                     |   dMeanR |   dUlcer% | persist   |   shift dMeanR |   shift dUlcer% | rnd beaten dU/dm   |
|:------|:-------|----:|:--------------------------|---------:|----------:|:----------|---------------:|----------------:|:-------------------|
| ALL   | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.015 |      14.3 | 41%       |         -0.005 |             5.9 | /                  |
| ALL   | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.01  |     -12.6 | 41%       |         -0.01  |            -2.9 | /                  |
| ALL   | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.011 |       7.3 | 45%       |         -0.017 |            -5.4 | /                  |
| ALL   | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.006 |      -6.1 | 45%       |         -0.013 |            -6.4 | /                  |
| ALL   | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.027 |       2.7 | 51%       |         -0.033 |            19.9 | 30%/90%            |
| ALL   | g15    |   3 | WEAK-BUT-POSITIVE         |    0.019 |     -34.7 | 48%       |         -0.01  |            -4.7 | 90%/80%            |
| ALL   | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.008 |     -18.6 | 42%       |         -0     |           -13.7 | 70%/10%            |
| ALL   | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.008 |     -21.6 | 49%       |         -0.014 |            -6.6 | 70%/30%            |
| ALL   | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.011 |      -7.1 | 41%       |         -0.011 |            29.6 | /                  |
| ALL   | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.011 |     -16.2 | 43%       |         -0.011 |            10.2 | /                  |
| ALL   | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.013 |       4.9 | 42%       |         -0.006 |            -3   | /                  |
| ALL   | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.012 |      -7.2 | 48%       |         -0.007 |            -6.1 | /                  |
| 1     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.02  |      10.4 | 32%       |         -0.017 |           -11.8 | /                  |
| 1     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.025 |      -7.4 | 42%       |         -0.019 |           -10.2 | /                  |
| 1     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.024 |     -15.3 | 41%       |         -0.004 |           -18.3 | /                  |
| 1     | g0     |  10 | WEAK-BUT-POSITIVE         |    0.011 |     -22.4 | 41%       |         -0.01  |            -7.3 | /                  |
| 1     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |      -2.4 | 40%       |         -0.018 |            -3.7 | 20%/20%            |
| 1     | g15    |   3 | WEAK-BUT-POSITIVE         |    0.007 |     -19.4 | 44%       |         -0.005 |           -15.4 | 50%/50%            |
| 1     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.007 |     -19.1 | 38%       |          0.001 |           -20.9 | 60%/10%            |
| 1     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.006 |     -20.8 | 36%       |         -0.009 |           -17.5 | 40%/40%            |
| 1     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |      11.3 | 43%       |         -0.006 |            -0.9 | /                  |
| 1     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0     |     -12.6 | 38%       |         -0.001 |            -6.8 | /                  |
| 1     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.008 |      -4.6 | 44%       |          0.002 |           -18.8 | /                  |
| 1     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.009 |      -9.6 | 36%       |         -0.007 |            -6.9 | /                  |
| 2     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.016 |      41.8 | 48%       |         -0.017 |             0.6 | /                  |
| 2     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.043 |      39.2 | 52%       |         -0.017 |            -4.8 | /                  |
| 2     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.035 |      13.2 | 44%       |         -0.016 |           -12.9 | /                  |
| 2     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.017 |     -15.3 | 48%       |         -0.008 |           -27.1 | /                  |
| 2     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.009 |       0.5 | 41%       |         -0.034 |            26.6 | 40%/40%            |
| 2     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.017 |       7.7 | 44%       |         -0.017 |            -0.7 | 10%/10%            |
| 2     | g15    |   5 | WEAK-BUT-POSITIVE         |    0.001 |     -15   | 49%       |         -0.012 |           -12.7 | 50%/30%            |
| 2     | g15    |  10 | WEAK-BUT-POSITIVE         |    0.007 |     -24.1 | 55%       |         -0.005 |           -23.6 | 90%/80%            |
| 2     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.004 |      14.6 | 49%       |         -0.035 |            21.8 | /                  |
| 2     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.021 |      13.8 | 44%       |         -0.019 |            -0.8 | /                  |
| 2     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.011 |      -5.4 | 51%       |         -0.015 |            -8.9 | /                  |
| 2     | g30    |  10 | WEAK-BUT-POSITIVE         |    0.012 |     -20.6 | 55%       |         -0.007 |           -20.2 | /                  |
| 3     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.018 |     -26.2 | 45%       |          0.02  |           -21.2 | /                  |
| 3     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.015 |     -23.9 | 44%       |          0.029 |           -27.3 | /                  |
| 3     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.017 |     -24.9 | 47%       |          0.025 |           -27.8 | /                  |
| 3     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.017 |     -25.8 | 47%       |          0.026 |           -28.2 | /                  |
| 3     | g15    |   1 | WEAK-BUT-POSITIVE         |    0.02  |     -31   | 33%       |          0.013 |           -29.8 | 80%/60%            |
| 3     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.01  |     -25.9 | 38%       |          0.015 |           -32.7 | 60%/50%            |
| 3     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.013 |     -31.5 | 38%       |          0.014 |           -33.3 | 70%/50%            |
| 3     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.013 |     -31.5 | 38%       |          0.015 |           -33.8 | 70%/50%            |
| 3     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.011 |     -29.2 | 36%       |          0.02  |           -31.1 | /                  |
| 3     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.007 |     -26.1 | 42%       |          0.021 |           -29.9 | /                  |
| 3     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.011 |     -31.6 | 43%       |          0.02  |           -30.6 | /                  |
| 3     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.011 |     -31.6 | 43%       |          0.021 |           -31.1 | /                  |
| 4     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.021 |     -10.1 | 46%       |          0.028 |           -34.3 | /                  |
| 4     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.006 |     -29.1 | 36%       |          0.02  |           -30.2 | /                  |
| 4     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.007 |     -33.9 | 47%       |          0.017 |           -27.6 | /                  |
| 4     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.007 |     -36.6 | 51%       |          0.015 |           -29.3 | /                  |
| 4     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.016 |     -42.2 | 44%       |          0.028 |           -35.5 | 90%/30%            |
| 4     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.001 |     -50.5 | 43%       |          0.012 |           -32.8 | 100%/40%           |
| 4     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.005 |     -44.2 | 44%       |          0.008 |           -30   | 100%/50%           |
| 4     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.006 |     -45.8 | 48%       |          0.008 |           -32   | 100%/60%           |
| 4     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.013 |     -41.6 | 48%       |          0.03  |           -33.5 | /                  |
| 4     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.007 |     -45.8 | 41%       |          0.017 |           -32.8 | /                  |
| 4     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0     |     -40   | 46%       |          0.01  |           -29.2 | /                  |
| 4     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.003 |     -42.5 | 51%       |          0.011 |           -31.2 | /                  |
| 5     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.03  |      41.5 | 54%       |          0.027 |           -19.8 | /                  |
| 5     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.006 |     -17.7 | 46%       |          0.022 |           -33   | /                  |
| 5     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |     -13.9 | 41%       |          0.016 |           -35.7 | /                  |
| 5     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.008 |     -12.8 | 44%       |          0.012 |           -35.7 | /                  |
| 5     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.043 |     -26.1 | 48%       |          0.017 |           -26.3 | 80%/90%            |
| 5     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.006 |     -33   | 46%       |          0.014 |           -34.4 | 90%/50%            |
| 5     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.003 |     -20.9 | 40%       |          0.011 |           -36.6 | 30%/80%            |
| 5     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.003 |     -20.9 | 48%       |          0.013 |           -37.2 | 20%/70%            |
| 5     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.007 |      -7   | 45%       |          0.002 |           -24.2 | /                  |
| 5     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -30   | 45%       |          0.016 |           -33.3 | /                  |
| 5     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.003 |     -20.1 | 45%       |          0.012 |           -32.6 | /                  |
| 5     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.016 |     -24.2 | 44%       |          0.013 |           -37.7 | /                  |
| 6     | g0     |   1 | WEAK-BUT-POSITIVE         |    0.01  |     -15.6 | 45%       |         -0.005 |            -6.9 | /                  |
| 6     | g0     |   3 | WEAK-BUT-POSITIVE         |    0.007 |     -28.2 | 44%       |         -0.016 |           -18.6 | /                  |
| 6     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -19.9 | 42%       |         -0.017 |           -25.4 | /                  |
| 6     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -21.4 | 41%       |         -0.012 |           -25.4 | /                  |
| 6     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |     -24.8 | 47%       |         -0.018 |             8.7 | 70%/30%            |
| 6     | g15    |   3 | WEAK-BUT-POSITIVE         |    0.022 |     -31   | 45%       |         -0.01  |            -4.2 | 70%/90%            |
| 6     | g15    |   5 | WEAK-BUT-POSITIVE         |    0.022 |     -26.5 | 45%       |         -0.01  |           -20   | 60%/100%           |
| 6     | g15    |  10 | WEAK-BUT-POSITIVE         |    0.02  |     -28.2 | 46%       |         -0.007 |           -25.1 | 70%/100%           |
| 6     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.016 |     -25   | 42%       |         -0.009 |             0.8 | /                  |
| 6     | g30    |   3 | WEAK-BUT-POSITIVE         |    0.016 |     -26.6 | 49%       |         -0.012 |           -13.7 | /                  |
| 6     | g30    |   5 | WEAK-BUT-POSITIVE         |    0.016 |     -22.3 | 46%       |         -0.008 |           -21.1 | /                  |
| 6     | g30    |  10 | WEAK-BUT-POSITIVE         |    0.016 |     -28.6 | 49%       |         -0.008 |           -24   | /                  |
| 7     | g0     |   1 | WEAK-BUT-POSITIVE         |    0     |      -2.4 | 41%       |         -0.017 |             7.7 | /                  |
| 7     | g0     |   3 | WEAK-BUT-POSITIVE         |    0.005 |      -2.8 | 45%       |         -0.027 |            14.9 | /                  |
| 7     | g0     |   5 | WEAK-BUT-POSITIVE         |    0.006 |      -2.9 | 48%       |         -0.025 |             9.3 | /                  |
| 7     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |      -1.2 | 41%       |         -0.014 |             4.8 | /                  |
| 7     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.004 |       6.9 | 53%       |         -0.015 |             6.6 | 10%/60%            |
| 7     | g15    |   3 | WEAK-BUT-POSITIVE         |    0.001 |      -2.1 | 48%       |         -0.023 |            12.9 | 10%/80%            |
| 7     | g15    |   5 | WEAK-BUT-POSITIVE         |    0.005 |      -2.7 | 47%       |         -0.015 |             6.5 | 50%/90%            |
| 7     | g15    |  10 | WEAK-BUT-POSITIVE         |    0.006 |      -2.4 | 49%       |         -0.01  |             4.1 | 40%/90%            |
| 7     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.007 |       8.2 | 44%       |         -0.017 |             6.6 | /                  |
| 7     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.001 |       0.1 | 51%       |         -0.024 |            13.7 | /                  |
| 7     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -0.9 | 46%       |         -0.019 |             7.8 | /                  |
| 7     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |      -1.8 | 39%       |         -0.011 |             4.3 | /                  |
| 8     | g0     |   1 | WEAK-BUT-POSITIVE         |    0.055 |     -43.5 | 46%       |         -0.031 |            24.9 | /                  |
| 8     | g0     |   3 | WEAK-BUT-POSITIVE         |    0.031 |     -38   | 53%       |         -0.016 |            -1   | /                  |
| 8     | g0     |   5 | WEAK-BUT-POSITIVE         |    0.029 |     -41.9 | 57%       |         -0.002 |           -15.1 | /                  |
| 8     | g0     |  10 | WEAK-BUT-POSITIVE         |    0.017 |     -26.4 | 54%       |          0.001 |           -20.1 | /                  |
| 8     | g15    |   1 | WEAK-BUT-POSITIVE         |    0.004 |     -21.2 | 49%       |         -0.047 |            39.1 | 100%/50%           |
| 8     | g15    |   3 | WEAK-BUT-POSITIVE         |    0.002 |     -26.7 | 42%       |         -0.018 |             0   | 60%/50%            |
| 8     | g15    |   5 | WEAK-BUT-POSITIVE         |    0.005 |     -29.8 | 44%       |         -0.01  |            -8.7 | 80%/60%            |
| 8     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.008 |     -13.8 | 51%       |          0.001 |           -18.4 | 40%/30%            |
| 8     | g30    |   1 | WEAK-BUT-POSITIVE         |    0.037 |     -31.4 | 47%       |         -0.041 |            36.1 | /                  |
| 8     | g30    |   3 | WEAK-BUT-POSITIVE         |    0.011 |     -26.7 | 45%       |         -0.018 |             0.4 | /                  |
| 8     | g30    |   5 | WEAK-BUT-POSITIVE         |    0.022 |     -36   | 44%       |         -0.009 |           -10.3 | /                  |
| 8     | g30    |  10 | WEAK-BUT-POSITIVE         |    0.01  |     -19.8 | 46%       |         -0.002 |           -19   | /                  |
| 9     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.019 |      -3.3 | 47%       |         -0.004 |           -20.1 | /                  |
| 9     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.006 |      -6.8 | 41%       |          0.007 |           -28.6 | /                  |
| 9     | g0     |   5 | WEAK-BUT-POSITIVE         |    0.012 |     -32.4 | 50%       |          0.009 |           -31.2 | /                  |
| 9     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.011 |     -28.2 | 44%       |          0.012 |           -32.3 | /                  |
| 9     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.015 |      -0.6 | 50%       |          0.013 |           -21.9 | 40%/70%            |
| 9     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.005 |     -18.9 | 42%       |          0.022 |           -30.3 | 80%/80%            |
| 9     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.016 |     -29.4 | 47%       |          0.022 |           -32.1 | 90%/100%           |
| 9     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.014 |     -28.4 | 46%       |          0.022 |           -32.1 | 80%/100%           |
| 9     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.006 |      17.9 | 47%       |          0.014 |           -23   | /                  |
| 9     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.004 |     -13   | 44%       |          0.022 |           -29.5 | /                  |
| 9     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.014 |     -27.3 | 49%       |          0.023 |           -31.2 | /                  |
| 9     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.013 |     -26   | 48%       |          0.024 |           -31.8 | /                  |
| 10    | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.071 |      93.9 | 36%       |         -0.019 |            -5.4 | /                  |
| 10    | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.022 |       3.3 | 35%       |         -0.004 |           -26.8 | /                  |
| 10    | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.004 |     -16.1 | 52%       |         -0.001 |           -26.6 | /                  |
| 10    | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -20.1 | 46%       |         -0.002 |           -22.1 | /                  |
| 10    | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.049 |      87.8 | 43%       |         -0.019 |            -5   | 0%/0%              |
| 10    | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0     |     -14.4 | 44%       |         -0     |           -26.8 | 20%/30%            |
| 10    | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.008 |     -23.3 | 51%       |         -0.004 |           -23.7 | 50%/30%            |
| 10    | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.003 |     -14.1 | 49%       |         -0.001 |           -22.6 | 40%/50%            |
| 10    | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.047 |      73.7 | 44%       |         -0.034 |             7.2 | /                  |
| 10    | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.001 |     -13   | 49%       |         -0.001 |           -26.9 | /                  |
| 10    | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.007 |     -20.3 | 51%       |         -0.003 |           -24.5 | /                  |
| 10    | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.004 |     -14   | 49%       |         -0.004 |           -21.3 | /                  |

## By horizon (picks traded the next 2 weeks / 1 month / 3 months; ALL pooled and main families; N=5, 6M, g15)
| set   | horizon   | label                     |   dMeanR |   dUlcer% | persist   |   shift dMeanR |   shift dUlcer% |
|:------|:----------|:--------------------------|---------:|----------:|:----------|---------------:|----------------:|
| ALL   | 2W        | BEST-AVAILABLE-NOT-PROVEN |   -0.008 |     -18.6 | 42%       |         -0     |           -13.7 |
| ALL   | 1M        | WEAK-BUT-POSITIVE         |    0.012 |     -24.1 | 60%       |         -0.005 |           -15.2 |
| ALL   | 3M        | BEST-AVAILABLE-NOT-PROVEN |   -0.011 |      -2.6 | 54%       |         -0.003 |           -17   |
| 1     | 2W        | BEST-AVAILABLE-NOT-PROVEN |   -0.007 |     -19.1 | 38%       |          0.001 |           -20.9 |
| 1     | 1M        | WEAK-BUT-POSITIVE         |    0.013 |     -22.3 | 52%       |         -0.004 |           -21.8 |
| 1     | 3M        | WEAK-BUT-POSITIVE         |    0.006 |     -29.2 | 46%       |         -0.008 |           -10.7 |
| 2     | 2W        | WEAK-BUT-POSITIVE         |    0.001 |     -15   | 49%       |         -0.012 |           -12.7 |
| 2     | 1M        | BEST-AVAILABLE-NOT-PROVEN |   -0.011 |      -1.1 | 57%       |         -0.007 |           -18.9 |
| 2     | 3M        | WEAK-BUT-POSITIVE         |    0.005 |     -12.6 | 46%       |         -0.018 |            -5.5 |
| 3     | 2W        | BEST-AVAILABLE-NOT-PROVEN |    0.013 |     -31.5 | 38%       |          0.014 |           -33.3 |
| 3     | 1M        | WEAK-BUT-POSITIVE         |    0.027 |     -41.6 | 56%       |          0.018 |           -28.4 |
| 3     | 3M        | WEAK-BUT-POSITIVE         |    0.011 |     -35.9 | 70%       |         -0.002 |           -23.9 |
| 4     | 2W        | BEST-AVAILABLE-NOT-PROVEN |    0.005 |     -44.2 | 44%       |          0.008 |           -30   |
| 4     | 1M        | WEAK-BUT-POSITIVE         |    0.008 |     -42.4 | 48%       |          0.004 |           -27.4 |
| 4     | 3M        | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |     -33.2 | 60%       |         -0.001 |           -23.2 |
| 5     | 2W        | BEST-AVAILABLE-NOT-PROVEN |    0.003 |     -20.9 | 40%       |          0.011 |           -36.6 |
| 5     | 1M        | BEST-AVAILABLE-NOT-PROVEN |   -0.006 |     -12.5 | 35%       |          0.014 |           -39.2 |
| 5     | 3M        | BEST-AVAILABLE-NOT-PROVEN |   -0.011 |     -19.4 | 38%       |          0.019 |           -41.6 |
| 6     | 2W        | WEAK-BUT-POSITIVE         |    0.022 |     -26.5 | 45%       |         -0.01  |           -20   |
| 6     | 1M        | WEAK-BUT-POSITIVE         |    0.02  |     -23.3 | 48%       |         -0.021 |           -14.8 |
| 6     | 3M        | WEAK-BUT-POSITIVE         |    0     |     -24.6 | 54%       |         -0.017 |           -22.2 |
| 7     | 2W        | WEAK-BUT-POSITIVE         |    0.005 |      -2.7 | 47%       |         -0.015 |             6.5 |
| 7     | 1M        | WEAK-BUT-POSITIVE         |    0.011 |      -5.7 | 48%       |         -0.017 |            11.1 |
| 7     | 3M        | WEAK-BUT-POSITIVE         |    0.014 |      -6.4 | 50%       |         -0.022 |            15   |
| 8     | 2W        | WEAK-BUT-POSITIVE         |    0.005 |     -29.8 | 44%       |         -0.01  |            -8.7 |
| 8     | 1M        | WEAK-BUT-POSITIVE         |    0.019 |     -37   | 62%       |         -0.008 |           -17.1 |
| 8     | 3M        | WEAK-BUT-POSITIVE         |    0.014 |     -28.4 | 62%       |         -0.006 |           -17.8 |
| 9     | 2W        | BEST-AVAILABLE-NOT-PROVEN |    0.016 |     -29.4 | 47%       |          0.022 |           -32.1 |
| 9     | 1M        | BEST-AVAILABLE-NOT-PROVEN |    0.019 |     -31   | 71%       |          0.024 |           -36.5 |
| 9     | 3M        | BEST-AVAILABLE-NOT-PROVEN |    0.026 |     -31.9 | 67%       |          0.024 |           -36.5 |
| 10    | 2W        | BEST-AVAILABLE-NOT-PROVEN |    0.008 |     -23.3 | 51%       |         -0.004 |           -23.7 |
| 10    | 1M        | BEST-AVAILABLE-NOT-PROVEN |    0.003 |     -15.8 | 62%       |          0.003 |           -27.7 |
| 10    | 3M        | BEST-AVAILABLE-NOT-PROVEN |   -0.01  |     -20.1 | 69%       |         -0.005 |           -22.8 |

## By windows (chained OOS pieces whose refit falls in the window; N=5, 6M picks, g15; real vs mean of shifted-label nulls)
| set   | window   |   n trades |   dMeanR |   dUlcer% | maxDD rule/base $   |   d$/wk (base lots, $4.84) | persist   |   shift-null dMeanR |   shift-null dUlcer% |
|:------|:---------|-----------:|---------:|----------:|:--------------------|---------------------------:|:----------|--------------------:|---------------------:|
| ALL   | L3M      |         25 |   -0.007 |      -9   | 3453/3584           |                       -123 | 50%       |              -0.001 |                -17.2 |
| ALL   | L6M      |         53 |   -0.02  |     -11.5 | 3453/3584           |                       -169 | 42%       |              -0.006 |                -19.4 |
| ALL   | HOLD     |         52 |   -0.018 |     -36.4 | 5212/8141           |                        -39 | 23%       |               0.018 |                -29.6 |
| ALL   | GAP      |         27 |    0.012 |     -24.2 | 2836/3869           |                        -71 | 71%       |              -0.01  |                -32.6 |
| ALL   | PRE      |         88 |    0.003 |     -15.7 | 3972/4654           |                       -111 | 42%       |               0.018 |                -14.3 |
| ALL   | XP       |        123 |   -0.003 |     -17.1 | 20677/24265         |                         71 | 44%       |              -0.003 |                -15   |
| ALL   | POOLED   |        356 |   -0.008 |     -18.6 | 20677/24887         |                        -32 | 42%       |              -0     |                -13.7 |
| 1     | L3M      |         25 |   -0.007 |      -9   | 3453/3584           |                       -123 | 50%       |               0.012 |                -23.7 |
| 1     | L6M      |         53 |   -0.021 |     -12.5 | 3453/3584           |                       -178 | 42%       |               0.007 |                -25.4 |
| 1     | HOLD     |         52 |    0.002 |     -23.4 | 5913/8141           |                         -0 | 23%       |               0.014 |                -38.7 |
| 1     | GAP      |         27 |   -0.003 |     -27.6 | 2597/3869           |                        -99 | 43%       |              -0.001 |                -31.7 |
| 1     | PRE      |         88 |    0.004 |     -16.7 | 3852/4654           |                       -114 | 37%       |               0.014 |                -16.9 |
| 1     | XP       |        123 |   -0.006 |     -18.1 | 20267/24265         |                         74 | 41%       |               0.004 |                -21.6 |
| 1     | POOLED   |        356 |   -0.007 |     -19.1 | 20267/24887         |                        -29 | 38%       |               0.001 |                -20.9 |
| 2     | L3M      |         25 |   -0.062 |       8.5 | 3822/3584           |                       -213 | 17%       |              -0.007 |                -32.2 |
| 2     | L6M      |         53 |   -0.017 |       5.1 | 3822/3584           |                       -140 | 42%       |              -0.011 |                -30.5 |
| 2     | HOLD     |         52 |    0.051 |     -41.4 | 5331/8141           |                         93 | 69%       |              -0.01  |                -30.6 |
| 2     | GAP      |         27 |   -0.024 |     -13.3 | 3224/3869           |                       -106 | 29%       |               0.004 |                -31.8 |
| 2     | PRE      |         88 |    0.021 |     -25.7 | 3255/4654           |                        -70 | 53%       |              -0.012 |                -23.2 |
| 2     | XP       |        123 |   -0.01  |     -19.8 | 20236/24265         |                         59 | 44%       |              -0.007 |                -17.6 |
| 2     | POOLED   |        356 |    0.001 |     -15   | 21259/24887         |                        -12 | 49%       |              -0.012 |                -12.7 |
| 3     | L3M      |         25 |    0     |       0   | 3584/3584           |                          0 |           |              -0.038 |                 10.8 |
| 3     | L6M      |         53 |    0     |       0   | 3584/3584           |                          0 |           |              -0.022 |                  9.5 |
| 3     | HOLD     |         52 |   -0.041 |     -14.9 | 6372/8141           |                        -79 | 29%       |              -0.011 |                 -7.4 |
| 3     | GAP      |         27 |    0.01  |     -34   | 2147/3869           |                        -74 | 33%       |              -0     |                -19.6 |
| 3     | PRE      |         88 |   -0.01  |     -24.5 | 3867/4654           |                       -107 | 31%       |               0.042 |                -23   |
| 3     | XP       |        123 |    0.023 |     -29.6 | 16379/24265         |                        169 | 50%       |               0.009 |                -30.7 |
| 3     | POOLED   |        356 |    0.013 |     -31.5 | 17001/24887         |                         13 | 38%       |               0.014 |                -33.3 |
| 4     | L3M      |         25 |   -0.036 |      18.8 | 4181/3584           |                       -105 | 0%        |              -0.092 |                  9.2 |
| 4     | L6M      |         53 |   -0.042 |      16.1 | 4181/3584           |                       -143 | 20%       |              -0.015 |                  0.9 |
| 4     | HOLD     |         52 |    0.008 |     -37.1 | 5578/8141           |                          7 | 54%       |               0.014 |                -26.8 |
| 4     | GAP      |         27 |   -0.019 |      -5.8 | 3869/3869           |                        -95 | 50%       |              -0.043 |                -33.9 |
| 4     | PRE      |         88 |   -0.021 |     -11.6 | 4451/4654           |                       -161 | 47%       |               0.001 |                -12.9 |
| 4     | XP       |        123 |    0.034 |     -42.9 | 14395/24265         |                        174 | 41%       |               0.029 |                -28.1 |
| 4     | POOLED   |        356 |    0.005 |     -44.2 | 14735/24887         |                         -5 | 44%       |               0.008 |                -30   |
| 5     | L3M      |         25 |   -0.028 |      -3.6 | 3576/3584           |                       -143 | 17%       |              -0.004 |                -11.3 |
| 5     | L6M      |         53 |   -0.013 |     -12.1 | 3576/3584           |                       -154 | 25%       |              -0.006 |                 -8   |
| 5     | HOLD     |         52 |   -0.023 |      -7.9 | 6482/8141           |                        -48 | 54%       |              -0.016 |                -19.1 |
| 5     | GAP      |         27 |    0.042 |     -45.6 | 2224/3869           |                        -36 | 43%       |               0.044 |                -23.7 |
| 5     | PRE      |         88 |    0.051 |     -45.2 | 2575/4654           |                        -68 | 53%       |               0.026 |                -29.4 |
| 5     | XP       |        123 |   -0.013 |     -12   | 19053/24265         |                         86 | 33%       |               0.011 |                -34   |
| 5     | POOLED   |        356 |    0.003 |     -20.9 | 19053/24887         |                        -14 | 40%       |               0.011 |                -36.6 |
| 6     | L3M      |         25 |    0.037 |     -44.2 | 2506/3584           |                        -35 | 33%       |               0.014 |                -36.1 |
| 6     | L6M      |         53 |    0.017 |     -36.8 | 2825/3584           |                        -84 | 42%       |               0.003 |                -34.7 |
| 6     | HOLD     |         52 |   -0.017 |     -25.1 | 6421/8141           |                        -37 | 23%       |               0.001 |                -41.4 |
| 6     | GAP      |         27 |    0.106 |     -23.5 | 3253/3869           |                         78 | 71%       |              -0.01  |                -29.2 |
| 6     | PRE      |         88 |    0.008 |     -23.2 | 3191/4654           |                        -50 | 42%       |              -0.014 |                -19.5 |
| 6     | XP       |        123 |   -0.001 |     -19.4 | 17775/24265         |                        118 | 52%       |              -0.016 |                -20.4 |
| 6     | POOLED   |        356 |    0.022 |     -26.5 | 17825/24887         |                         28 | 45%       |              -0.01  |                -20   |
| 7     | L3M      |         25 |    0.061 |     -57.1 | 2237/3584           |                         42 | 67%       |              -0.036 |                -19.7 |
| 7     | L6M      |         53 |    0.042 |     -48.7 | 2237/3584           |                        -17 | 67%       |              -0.001 |                -20.1 |
| 7     | HOLD     |         52 |   -0.035 |     -12.4 | 6520/8141           |                        -76 | 15%       |              -0.022 |                 -8.6 |
| 7     | GAP      |         27 |    0.02  |     -12.1 | 3329/3869           |                        -18 | 43%       |               0.008 |                -26.1 |
| 7     | PRE      |         88 |    0.014 |      10   | 5019/4654           |                        111 | 53%       |               0     |                -17.8 |
| 7     | XP       |        123 |    0     |       0   | 24265/24265         |                          0 |           |               0     |                  0   |
| 7     | POOLED   |        356 |    0.005 |      -2.7 | 26367/24887         |                         11 | 47%       |              -0.015 |                  6.5 |
| 8     | L3M      |         25 |    0.023 |     -17   | 3141/3584           |                        -18 | 50%       |               0.007 |                -12.4 |
| 8     | L6M      |         53 |    0.022 |     -19.7 | 3141/3584           |                        -28 | 42%       |               0.002 |                -16.6 |
| 8     | HOLD     |         52 |   -0.065 |      20.8 | 7436/8141           |                       -135 | 38%       |               0.007 |                -16.7 |
| 8     | GAP      |         27 |   -0.007 |     -25.5 | 3018/3869           |                        -81 | 29%       |               0.009 |                -22.1 |
| 8     | PRE      |         88 |    0.004 |     -10.7 | 4068/4654           |                        -71 | 58%       |              -0.023 |                -12.8 |
| 8     | XP       |        123 |    0.022 |     -30.3 | 16603/24265         |                        149 | 44%       |              -0.021 |                -10.9 |
| 8     | POOLED   |        356 |    0.005 |     -29.8 | 16627/24887         |                         -2 | 44%       |              -0.01  |                 -8.7 |
| 9     | L3M      |         25 |    0.026 |     -20.2 | 3599/3584           |                        -58 | 40%       |              -0.004 |                -13.1 |
| 9     | L6M      |         53 |    0.007 |      -7.7 | 3599/3584           |                       -129 | 44%       |              -0.015 |                  1.3 |
| 9     | HOLD     |         52 |    0.05  |     -36.9 | 6020/8141           |                        105 | 64%       |               0.03  |                -27.2 |
| 9     | GAP      |         27 |    0     |      -9   | 3272/3869           |                        -44 | 17%       |               0.016 |                -26.5 |
| 9     | PRE      |         88 |    0.012 |     -14.8 | 4378/4654           |                        -50 | 35%       |               0.008 |                -10.4 |
| 9     | XP       |        123 |    0.016 |     -31.4 | 18571/24265         |                        114 | 56%       |               0.022 |                -32.1 |
| 9     | POOLED   |        356 |    0.016 |     -29.4 | 18810/24887         |                         22 | 47%       |               0.022 |                -32.1 |
| 10    | L3M      |         25 |   -0.003 |     -11.1 | 3195/3584           |                        -86 | 33%       |              -0.015 |                -21.9 |
| 10    | L6M      |         53 |    0.037 |     -16.9 | 3195/3584           |                        -11 | 58%       |              -0.001 |                -22.6 |
| 10    | HOLD     |         52 |   -0.037 |      -7.6 | 6561/8141           |                        -75 | 46%       |              -0.026 |                -18.9 |
| 10    | GAP      |         27 |    0.001 |     -17.8 | 3205/3869           |                        -42 | 33%       |              -0.032 |                -13.8 |
| 10    | PRE      |         88 |    0.007 |     -17.9 | 3781/4654           |                        -83 | 32%       |               0.004 |                -22.8 |
| 10    | XP       |        123 |    0.012 |     -24.7 | 19965/24265         |                        103 | 63%       |              -0.004 |                -21.1 |
| 10    | POOLED   |        356 |    0.008 |     -23.3 | 19965/24887         |                          6 | 51%       |              -0.004 |                -23.7 |

## Time thirds (2023-10..2024-09, 2024-10..2025-09, 2025-10..2026-10), N=5, 6M, g15, next 2 weeks
| set   | T1                    | T2                    | T3                    |
|:------|:----------------------|:----------------------|:----------------------|
| ALL   | -0.011 R / -17.6% ulc | +0.005 R / -19.5% ulc | -0.011 R / -34.3% ulc |
| 1     | -0.013 R / -18.5% ulc | +0.002 R / -21.3% ulc | -0.005 R / -35.2% ulc |
| 2     | -0.003 R / -20.5% ulc | +0.005 R / -27.0% ulc | +0.009 R / -22.9% ulc |
| 3     | +0.017 R / -28.6% ulc | -0.010 R / -26.7% ulc | -0.000 R / -2.7% ulc  |
| 4     | +0.034 R / -43.5% ulc | -0.016 R / -10.5% ulc | -0.010 R / -22.0% ulc |
| 5     | -0.014 R / -9.7% ulc  | +0.050 R / -44.4% ulc | -0.012 R / -25.7% ulc |
| 6     | -0.004 R / -17.4% ulc | +0.021 R / -20.6% ulc | +0.025 R / -42.3% ulc |
| 7     | +0.000 R / +0.0% ulc  | +0.012 R / +4.2% ulc  | -0.001 R / -0.9% ulc  |
| 8     | +0.013 R / -29.6% ulc | +0.009 R / -12.1% ulc | -0.026 R / +34.2% ulc |
| 9     | +0.021 R / -33.0% ulc | +0.001 R / -11.3% ulc | +0.017 R / -31.9% ulc |
| 10    | +0.009 R / -26.3% ulc | +0.013 R / -14.0% ulc | +0.000 R / -11.2% ulc |
| 1a    | -0.006 R / -22.4% ulc | +0.027 R / -30.0% ulc | +0.007 R / -53.3% ulc |
| 1b    | -0.011 R / -24.2% ulc | +0.010 R / -25.4% ulc | -0.024 R / -29.3% ulc |
| 1c    | +0.006 R / -28.8% ulc | +0.022 R / -15.9% ulc | +0.054 R / -66.6% ulc |
| 1d    | +0.019 R / -39.7% ulc | +0.000 R / -26.6% ulc | +0.001 R / -44.7% ulc |
| 1e    | +0.029 R / -30.0% ulc | -0.010 R / -13.7% ulc | +0.044 R / -48.2% ulc |
| 1f    | -0.005 R / -24.9% ulc | -0.043 R / -11.3% ulc | +0.002 R / -32.2% ulc |
| 1g    | -0.014 R / -16.3% ulc | +0.002 R / -29.8% ulc | -0.019 R / -39.7% ulc |
| 1h    | +0.037 R / -35.7% ulc | +0.007 R / -29.6% ulc | -0.004 R / -36.2% ulc |
| 5a    | -0.036 R / -16.8% ulc | +0.018 R / -36.5% ulc | -0.009 R / -22.7% ulc |
| 5b    | -0.002 R / -13.9% ulc | +0.052 R / -39.3% ulc | -0.007 R / -24.0% ulc |
| NONS  | -0.014 R / -29.1% ulc | -0.006 R / -28.1% ulc | +0.020 R / -20.3% ulc |
| RAND  | +0.040 R / -46.8% ulc | -0.012 R / -20.7% ulc | +0.012 R / -37.2% ulc |
| PLANT | +0.038 R / -15.3% ulc | +0.025 R / -4.1% ulc  | +0.028 R / +1.8% ulc  |

## Per book x session (ALL families pooled, N=5, 6M picks, g15, next 2 weeks) with shifted-label and random-skip nulls per cell
| cell (book_session)   |   trades OOS |   dMeanR |   dUlcer% | persist   |   shift dMeanR |   shift dUlcer% |   random-skip dMeanR |   random-skip dUlcer% | beats random dU/dm   |
|:----------------------|-------------:|---------:|----------:|:----------|---------------:|----------------:|---------------------:|----------------------:|:---------------------|
| H7_3                  |          356 |   -0.008 |     -18.6 | 42%       |             -0 |           -13.7 |                0.001 |                 -14.2 | 70%/10%              |

Per cell by family (N=5, 6M, g15, 2 weeks): dMeanR / dUlcer% real vs shifted-label mean:
| cell   | 1                            | 2                            | 3                            | 4                            | 5                            | 6                            | 7                          | 8                           | 9                            | 10                           | ALL                          |
|:-------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:---------------------------|:----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|
| H7_3   | -0.007/-19% (sh +0.001/-21%) | +0.001/-15% (sh -0.012/-13%) | +0.013/-32% (sh +0.014/-33%) | +0.005/-44% (sh +0.008/-30%) | +0.003/-21% (sh +0.011/-37%) | +0.022/-27% (sh -0.010/-20%) | +0.005/-3% (sh -0.015/+7%) | +0.005/-30% (sh -0.010/-9%) | +0.016/-29% (sh +0.022/-32%) | +0.008/-23% (sh -0.004/-24%) | -0.008/-19% (sh -0.000/-14%) |

## Persistence, turnover and decay of the picks (ALL families pooled, N=5, 6M, g15)
Turnover: mean share of the top-5 list retained from one refit to the next (higher = more stable picks): H7_3 24%; overall 24%.
Decay: summed gain/loss ($, base lots, $4.84) of the picks by how many 2-week blocks after the refit they are traded (0 = the next 2 weeks):
| set   | labels   | lag 0 (0-13 d)             | lag 1 (14-27 d)            | lag 2 (28-41 d)           | lag 3 (42-55 d)            | lag 4 (56-69 d)            | lag 5 (70-83 d)            |
|:------|:---------|:---------------------------|:---------------------------|:--------------------------|:---------------------------|:---------------------------|:---------------------------|
| ALL   | real     | -5664$ (46% of pieces >0)  | 683$ (41% of pieces >0)    | -2111$ (44% of pieces >0) | -2201$ (40% of pieces >0)  | -6886$ (43% of pieces >0)  | -4278$ (42% of pieces >0)  |
| ALL   | shift11  | -3107$ (42% of pieces >0)  | -4097$ (48% of pieces >0)  | -9415$ (42% of pieces >0) | -2385$ (44% of pieces >0)  | -4872$ (40% of pieces >0)  | -3318$ (42% of pieces >0)  |
| 1     | real     | -5168$ (44% of pieces >0)  | -2847$ (42% of pieces >0)  | -2917$ (41% of pieces >0) | -1301$ (42% of pieces >0)  | -7464$ (44% of pieces >0)  | -6119$ (45% of pieces >0)  |
| 1     | shift11  | -1437$ (39% of pieces >0)  | -6091$ (39% of pieces >0)  | -6979$ (42% of pieces >0) | -2383$ (41% of pieces >0)  | -11697$ (39% of pieces >0) | -10870$ (38% of pieces >0) |
| 2     | real     | -2255$ (51% of pieces >0)  | -5416$ (42% of pieces >0)  | -6083$ (44% of pieces >0) | 554$ (49% of pieces >0)    | 1373$ (47% of pieces >0)   | -3626$ (42% of pieces >0)  |
| 2     | shift11  | -10882$ (42% of pieces >0) | 1547$ (44% of pieces >0)   | -5218$ (41% of pieces >0) | -5587$ (44% of pieces >0)  | -9144$ (43% of pieces >0)  | -8268$ (46% of pieces >0)  |
| 3     | real     | 2006$ (34% of pieces >0)   | 4331$ (41% of pieces >0)   | -39$ (45% of pieces >0)   | 2358$ (39% of pieces >0)   | 7715$ (41% of pieces >0)   | 5903$ (45% of pieces >0)   |
| 3     | shift11  | 1459$ (39% of pieces >0)   | 9825$ (41% of pieces >0)   | 1363$ (40% of pieces >0)  | -2573$ (39% of pieces >0)  | 4190$ (40% of pieces >0)   | -3323$ (39% of pieces >0)  |
| 5     | real     | -1914$ (46% of pieces >0)  | -7301$ (41% of pieces >0)  | -3366$ (39% of pieces >0) | -4083$ (40% of pieces >0)  | -2000$ (34% of pieces >0)  | -6118$ (42% of pieces >0)  |
| 5     | shift11  | -5633$ (39% of pieces >0)  | -5406$ (44% of pieces >0)  | -4581$ (44% of pieces >0) | -1289$ (44% of pieces >0)  | -7773$ (44% of pieces >0)  | -2875$ (42% of pieces >0)  |
| 7     | real     | 1879$ (52% of pieces >0)   | 5529$ (51% of pieces >0)   | 703$ (48% of pieces >0)   | 602$ (47% of pieces >0)    | 273$ (48% of pieces >0)    | 5115$ (55% of pieces >0)   |
| 7     | shift11  | -10958$ (37% of pieces >0) | -10519$ (33% of pieces >0) | -9962$ (44% of pieces >0) | -14360$ (37% of pieces >0) | -9526$ (38% of pieces >0)  | -5073$ (36% of pieces >0)  |
| 10    | real     | 940$ (48% of pieces >0)    | -4165$ (45% of pieces >0)  | -6263$ (42% of pieces >0) | -4283$ (42% of pieces >0)  | -4574$ (38% of pieces >0)  | -3793$ (39% of pieces >0)  |
| 10    | shift11  | -5547$ (39% of pieces >0)  | -4303$ (45% of pieces >0)  | -6372$ (44% of pieces >0) | -4193$ (45% of pieces >0)  | -2257$ (45% of pieces >0)  | -3568$ (46% of pieces >0)  |
| NONS  | real     | -4932$ (47% of pieces >0)  | 880$ (44% of pieces >0)    | -710$ (42% of pieces >0)  | -2696$ (41% of pieces >0)  | -3044$ (38% of pieces >0)  | -3847$ (39% of pieces >0)  |
| NONS  | shift11  | -2$ (48% of pieces >0)     | 6$ (46% of pieces >0)      | 457$ (51% of pieces >0)   | 1539$ (49% of pieces >0)   | -2130$ (44% of pieces >0)  | -1480$ (46% of pieces >0)  |

## SCORES (equal-weight vote of the top 5 / top 10 recent conditions; g15 picks; rule = trade by thirds of the vote, next 2 weeks chained, 6M picks)
| set   |   K | rule       |   dMeanR |   dUlcer% |   d$/wk | persist   |   shift dMeanR |   shift dUlcer% | beats 3 shifts   |
|:------|----:|:-----------|---------:|----------:|--------:|:----------|---------------:|----------------:|:-----------------|
| ALL   |   5 | skip_low   |   -0.015 |     -28.3 |     -52 | 51%       |          0.029 |           -38.4 | no               |
| ALL   |   5 | half_low   |   -0.005 |     -15   |     -26 | 45%       |          0.01  |           -20.9 | no               |
| ALL   |   5 | boost_high |   -0.006 |      37.9 |      -4 | 42%       |          0.007 |            17.4 | no               |
| ALL   |  10 | skip_low   |   -0.05  |      31.2 |    -110 | 47%       |         -0.011 |            -6.1 | no               |
| ALL   |  10 | half_low   |   -0.02  |      11.5 |     -55 | 44%       |         -0.004 |            -7.9 | no               |
| ALL   |  10 | boost_high |   -0.004 |      23.4 |      -3 | 38%       |         -0.005 |            19.5 | no               |
| 1     |   5 | skip_low   |    0.001 |     -36.5 |     -26 | 53%       |          0.018 |           -44.2 | no               |
| 1     |   5 | half_low   |    0     |     -22.2 |     -13 | 49%       |          0.006 |           -24.4 | no               |
| 1     |   5 | boost_high |   -0.008 |      29.2 |     -12 | 37%       |          0.005 |            16.4 | no               |
| 1     |  10 | skip_low   |   -0.013 |      11.5 |     -46 | 46%       |         -0.044 |            11   | no               |
| 1     |  10 | half_low   |   -0.005 |       4.1 |     -23 | 43%       |         -0.017 |            -4   | no               |
| 1     |  10 | boost_high |    0.005 |      18.3 |      26 | 38%       |         -0.006 |            22.4 | no               |
| 2     |   5 | skip_low   |   -0.065 |      10.4 |    -125 | 42%       |         -0.015 |           -17.2 | no               |
| 2     |   5 | half_low   |   -0.023 |      -1.2 |     -62 | 40%       |         -0.005 |           -13.9 | no               |
| 2     |   5 | boost_high |   -0.009 |      35.4 |     -16 | 43%       |         -0.008 |            41.6 | no               |
| 2     |  10 | skip_low   |   -0.009 |     -16   |     -41 | 46%       |         -0.019 |            -8.5 | no               |
| 2     |  10 | half_low   |   -0.003 |     -21.7 |     -21 | 44%       |         -0.007 |           -12.9 | no               |
| 2     |  10 | boost_high |    0.005 |      11.4 |      29 | 49%       |         -0.009 |            30.3 | no               |
| 3     |   5 | skip_low   |    0.017 |     -52.1 |       8 | 44%       |          0.004 |           -34.7 | no               |
| 3     |   5 | half_low   |    0.007 |     -27   |       4 | 38%       |          0.002 |           -20   | no               |
| 3     |   5 | boost_high |    0     |      16.9 |      11 | 38%       |          0.013 |             3.4 | no               |
| 3     |  10 | skip_low   |    0.017 |     -52.1 |       8 | 44%       |          0.004 |           -34.7 | no               |
| 3     |  10 | half_low   |    0.007 |     -27   |       4 | 38%       |          0.002 |           -20   | no               |
| 3     |  10 | boost_high |    0     |      16.9 |      11 | 38%       |          0.013 |             3.4 | no               |
| 5     |   5 | skip_low   |    0.023 |     -19.1 |       4 | 48%       |          0.013 |           -38.5 | no               |
| 5     |   5 | half_low   |    0.008 |     -11.2 |       2 | 46%       |          0.005 |           -25.7 | no               |
| 5     |   5 | boost_high |    0.001 |      35   |      18 | 45%       |          0.002 |            19.5 | no               |
| 5     |  10 | skip_low   |   -0.056 |      29.2 |    -117 | 41%       |          0.04  |           -37.6 | no               |
| 5     |  10 | half_low   |   -0.021 |      10.7 |     -58 | 38%       |          0.015 |           -24.1 | no               |
| 5     |  10 | boost_high |    0.01  |      13.6 |      45 | 50%       |          0.005 |             9.7 | no               |
| 7     |   5 | skip_low   |   -0.044 |      17.3 |    -107 | 41%       |         -0.024 |            10.8 | no               |
| 7     |   5 | half_low   |   -0.019 |       3.1 |     -54 | 38%       |         -0.01  |             2.7 | no               |
| 7     |   5 | boost_high |    0.012 |       2.9 |      50 | 33%       |          0.01  |             0.1 | no               |
| 7     |  10 | skip_low   |   -0.002 |       1.7 |     -18 | 52%       |         -0.022 |            16.5 | no               |
| 7     |  10 | half_low   |   -0.001 |       0.6 |      -9 | 45%       |         -0.009 |             5.1 | no               |
| 7     |  10 | boost_high |    0.017 |       0.7 |      62 | 41%       |          0.017 |            -0.9 | no               |
| 10    |   5 | skip_low   |   -0.014 |      -0.4 |     -50 | 45%       |          0.014 |           -41.2 | no               |
| 10    |   5 | half_low   |   -0.005 |     -13.3 |     -25 | 41%       |          0.005 |           -24.6 | no               |
| 10    |   5 | boost_high |    0.004 |      23.2 |      29 | 46%       |         -0.003 |            20.1 | no               |
| 10    |  10 | skip_low   |   -0.006 |       0.9 |     -37 | 48%       |          0.001 |           -13.3 | no               |
| 10    |  10 | half_low   |   -0.002 |     -10.2 |     -18 | 46%       |          0     |            -9   | no               |
| 10    |  10 | boost_high |    0.005 |      25.8 |      30 | 44%       |          0.001 |            26.9 | no               |
| 1c    |   5 | skip_low   |    0.058 |     -57.8 |      65 | 50%       |         -0.01  |           -32.1 | yes              |
| 1c    |   5 | half_low   |    0.022 |     -33.8 |      32 | 43%       |         -0.003 |           -21.8 | yes              |
| 1c    |   5 | boost_high |    0.005 |      16.5 |      31 | 41%       |         -0.004 |            27.4 | yes              |
| 1c    |  10 | skip_low   |    0.052 |     -38.3 |      58 | 44%       |          0.013 |           -38.9 | no               |
| 1c    |  10 | half_low   |    0.02  |     -24.8 |      29 | 41%       |          0.005 |           -24.8 | no               |
| 1c    |  10 | boost_high |    0.01  |       5.6 |      44 | 44%       |          0.007 |             6.9 | no               |
| 1d    |   5 | skip_low   |    0.06  |     -53.2 |      64 | 55%       |          0.024 |           -37.9 | yes              |
| 1d    |   5 | half_low   |    0.022 |     -34   |      32 | 51%       |          0.009 |           -22.3 | yes              |
| 1d    |   5 | boost_high |    0.009 |       4.7 |      45 | 46%       |          0.004 |            21   | yes              |
| 1d    |  10 | skip_low   |    0.06  |     -49.8 |      75 | 55%       |          0.022 |           -43.9 | yes              |
| 1d    |  10 | half_low   |    0.023 |     -32.9 |      38 | 52%       |          0.009 |           -28.4 | yes              |
| 1d    |  10 | boost_high |    0.003 |      -1.7 |      23 | 44%       |          0.009 |            11.7 | no               |
| 1e    |   5 | skip_low   |    0.053 |     -45.8 |      61 | 59%       |         -0.004 |             8   | yes              |
| 1e    |   5 | half_low   |    0.02  |     -25.9 |      31 | 55%       |         -0.001 |            -1.3 | yes              |
| 1e    |   5 | boost_high |    0.01  |      16.5 |      46 | 48%       |          0.003 |            19.5 | no               |
| 1e    |  10 | skip_low   |    0.046 |     -34.6 |      59 | 61%       |          0.02  |           -18.1 | no               |
| 1e    |  10 | half_low   |    0.018 |     -18.6 |      29 | 59%       |          0.008 |           -13.4 | no               |
| 1e    |  10 | boost_high |    0.017 |       5.6 |      65 | 57%       |          0.003 |            21.4 | yes              |
| 5a    |   5 | skip_low   |   -0.017 |      23.5 |     -55 | 48%       |          0.005 |           -28.7 | no               |
| 5a    |   5 | half_low   |   -0.006 |       4.6 |     -27 | 46%       |          0.002 |           -25.4 | no               |
| 5a    |   5 | boost_high |   -0.008 |      44.2 |     -10 | 46%       |          0.003 |             8.7 | no               |
| 5a    |  10 | skip_low   |   -0.009 |      40   |     -42 | 46%       |          0.017 |           -38   | no               |
| 5a    |  10 | half_low   |   -0.003 |      15.9 |     -21 | 43%       |          0.007 |           -27.4 | no               |
| 5a    |  10 | boost_high |   -0.012 |      47.6 |     -24 | 41%       |          0.008 |            12.6 | no               |
| 5b    |   5 | skip_low   |    0.016 |      -1.9 |      -8 | 48%       |         -0.004 |           -30.4 | no               |
| 5b    |   5 | half_low   |    0.006 |      -3.1 |      -4 | 46%       |         -0.001 |           -21.1 | no               |
| 5b    |   5 | boost_high |    0.014 |      23.6 |      57 | 53%       |          0.002 |            17.7 | no               |
| 5b    |  10 | skip_low   |    0.013 |     -32.8 |     -10 | 44%       |          0.004 |           -25.9 | no               |
| 5b    |  10 | half_low   |    0.005 |     -19.2 |      -5 | 41%       |          0.001 |           -20.6 | no               |
| 5b    |  10 | boost_high |    0.002 |      13.4 |      18 | 42%       |          0.007 |            10.4 | no               |
| NONS  |   5 | skip_low   |   -0.037 |     -35.6 |     -83 | 53%       |          0.034 |           -38.6 | no               |
| NONS  |   5 | half_low   |   -0.012 |     -25.2 |     -42 | 48%       |          0.012 |           -21.5 | no               |
| NONS  |   5 | boost_high |   -0.004 |      27.5 |       0 | 50%       |          0.011 |            23.6 | no               |
| NONS  |  10 | skip_low   |   -0.025 |      -1.5 |     -67 | 45%       |          0.02  |           -35.2 | no               |
| NONS  |  10 | half_low   |   -0.009 |      -5.7 |     -33 | 41%       |          0.007 |           -20.3 | no               |
| NONS  |  10 | boost_high |    0.006 |      20.6 |      29 | 45%       |          0.007 |            18.9 | no               |
| RAND  |   5 | skip_low   |    0.053 |     -52.2 |      32 | 49%       |         -0.01  |           -14.2 | yes              |
| RAND  |   5 | half_low   |    0.017 |     -37.1 |      16 | 43%       |         -0.004 |           -10.8 | yes              |
| RAND  |   5 | boost_high |    0.012 |      12.9 |      51 | 43%       |          0.002 |            33.8 | yes              |
| RAND  |  10 | skip_low   |    0.043 |     -47.2 |      25 | 54%       |          0.02  |           -37   | no               |
| RAND  |  10 | half_low   |    0.015 |     -33.4 |      12 | 49%       |          0.007 |           -21.6 | yes              |
| RAND  |  10 | boost_high |    0.011 |       1.1 |      46 | 54%       |          0.008 |            25.9 | no               |
| PLANT |   5 | skip_low   |    0.106 |     -70.8 |     139 | 61%       |         -0.059 |            75.8 | yes              |
| PLANT |   5 | half_low   |    0.039 |     -62.7 |      69 | 51%       |         -0.022 |            31.1 | yes              |
| PLANT |   5 | boost_high |    0.035 |     -22.8 |     123 | 58%       |         -0.014 |            54   | yes              |
| PLANT |  10 | skip_low   |    0.098 |     -70.7 |     132 | 59%       |         -0.059 |            73.9 | yes              |
| PLANT |  10 | half_low   |    0.037 |     -59.5 |      66 | 49%       |         -0.022 |            29.8 | yes              |
| PLANT |  10 | boost_high |    0.033 |     -17.1 |     119 | 56%       |         -0.014 |            52.5 | yes              |

Vote in thirds on the next 2 weeks (K=5; thirds cut at the pick-window terciles of the vote; real labels vs the shifted-label procedure):
| set   | labels   | low: share, meanR   | mid: share, meanR   | high: share, meanR   |   high-low meanR |
|:------|:---------|:--------------------|:--------------------|:---------------------|-----------------:|
| ALL   | real     | 43%, +0.048         | 15%, +0.062         | 42%, -0.004          |           -0.052 |
| ALL   | shift11  | 50%, -0.007         | 6%, +0.105          | 44%, +0.058          |            0.064 |
| ALL   | shift23  | 42%, +0.008         | 16%, +0.075         | 42%, +0.031          |            0.024 |
| ALL   | shift37  | 43%, -0.019         | 14%, -0.071         | 43%, +0.107          |            0.127 |
| 1     | real     | 41%, +0.027         | 17%, +0.146         | 42%, -0.018          |           -0.044 |
| 1     | shift11  | 47%, +0.020         | 16%, -0.085         | 37%, +0.086          |            0.066 |
| 1     | shift23  | 40%, +0.049         | 17%, -0.008         | 43%, +0.023          |           -0.027 |
| 1     | shift37  | 44%, -0.050         | 13%, +0.152         | 43%, +0.073          |            0.122 |
| 3     | real     | 47%, -0.006         | 8%, -0.052          | 45%, +0.030          |            0.036 |
| 3     | shift11  | 37%, +0.062         | 34%, -0.155         | 29%, +0.240          |            0.178 |
| 3     | shift23  | 37%, +0.017         | 22%, -0.114         | 40%, +0.099          |            0.082 |
| 3     | shift37  | 31%, -0.061         | 27%, -0.132         | 42%, +0.080          |            0.141 |
| 5     | real     | 45%, -0.000         | 14%, +0.098         | 41%, +0.035          |            0.035 |
| 5     | shift11  | 50%, +0.037         | 13%, -0.063         | 37%, +0.050          |            0.013 |
| 5     | shift23  | 44%, +0.043         | 12%, +0.011         | 44%, +0.018          |           -0.025 |
| 5     | shift37  | 43%, -0.051         | 13%, +0.186         | 45%, +0.059          |            0.109 |
| 7     | real     | 33%, +0.193         | 9%, -0.042          | 58%, +0.107          |           -0.086 |
| 7     | shift11  | 53%, +0.079         | 15%, +0.212         | 32%, +0.152          |            0.073 |
| 7     | shift23  | 45%, +0.110         | 12%, +0.059         | 43%, +0.152          |            0.042 |
| 7     | shift37  | 47%, +0.062         | 21%, +0.359         | 33%, +0.061          |           -0.001 |
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
Each row: the rule in plain words, its effect on the pick window (6M and 3M: dMeanR in R, dUlcer% vs doing nothing), the share of trades it acts on, the prior-year check (GREEN <=15%, AMBER 15-30%, RED >30% worse than doing nothing on ulcer / mean in the worst prior 365-day block), feed needs, whether D7 can compute it live. ALL families pooled, gate 15% (strict) and 30%. Where the 6M and 3M numbers disagree in sign the pick is fragile.

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
