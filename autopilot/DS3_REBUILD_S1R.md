# DS3_REBUILD_S1R - Stage 1R: every entry condition re-scored by the user's rolling rule on the RAW books (W-S1R)

1. WHICH WORK under the user's rule (recent-data picks, refit every 2 weeks, OOS chained, label needs excess over the shifted-label / random-skip / nonsense nulls): none. WEAK-BUT-POSITIVE (positive OOS but not clearly past the nulls): 3, 5, 6, 9, 10, 1f, 1h, 5a, 5b.
2. WHICH DO NOT: 1, 2, 4, 7, 8, 1a, 1b, 1c, 1d, 1e, 1g, ALL (BEST-AVAILABLE-NOT-PROVEN: the rolling picks do not beat what the same procedure earns on shifted labels / random skips). Control columns (nonsense / random / planted) under the same procedure: NONS=BEST-AVAILABLE-NOT-PROVEN, RAND=BEST-AVAILABLE-NOT-PROVEN, PLANT=WEAK-BUT-POSITIVE.
3. ALL families pooled, top-5 picks, trailing 6M, 15% prior-year gate, next 2 weeks chained over 1 book x session cells: BEST-AVAILABLE-NOT-PROVEN; OOS dMeanR -0.026 R, dUlcer -8.0%, persistence 35% (bar 60%) vs shifted-label nulls 0.058 R / -47.3% (see the first table for the sub-families).
4. TODAY'S PICKS (refit ending 2026-10-30, pick window 2026-05-01..2026-10-30 / 3M 2026-08-01..): per book x session in the "Current picks" section below (top 5 and the best pick per family, with 6M and 3M effect, prior-year 15/30 flags, feed need and whether D7 can compute it live); CSVs /mnt/l2/l2vast/_s1r/eval/picks_now_all.csv and picks_now_family.csv.
5. DATA END 2026-10-30 (engine store ends there; November 2026 is not in the raw engine base so it could not be extended); cells done 1/15 as of 2026-11-17 18:32 UTC; first table 00:20Z, full set 06:20Z; wait-then-enter / early-exit and the score votes are in their own sections. Label scale: CONFIRMED / LEAD / WEAK-BUT-POSITIVE / BEST-AVAILABLE-NOT-PROVEN (rules below).

> VALIDATION (FIRST PASS, written 2026-11-17 18:32 UTC): rule = the user's standing selection rule (autopilot/DIRECTIVE_SELECTION_RULE_20261117.md, STAGE1R order 18:17Z): pick on the TRAILING 6 months (3 months shown beside), refit every 14 days from 2023-10-02 to 2026-10-31, prior-years check = not-a-disaster at 15%/30%, validated by walking the procedure forward (OOS pieces chained), NOT a frozen holdout. Trials counted: 63626 candidate columns x 2 sides x 3 actions per cell and refit (65,192 columns in the stage-1 store; 63,626 at-entry-clean + 299 controls scored here) x 15 cells x 79 refits x 2 windows x 4 label versions; correction = nulls (shifted labels 11/23/37 days, nonsense/random/planted columns, 10 random persistent skips with the same share and action), plus the label rules below; no White RC/SPA/DSR/PBO is computed (a rolling pick procedure is evaluated by its OOS excess over nulls instead); NOT engine-exact (raw-chassis trade P&L at base lots, $4.84 RT), no re-entry or freed-book effects; the engine-exact stage-2 run comes later via the lead. Data end 2026-10-30; pick-window end 2026-10-30; refit date 2026-10-31.

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
| 1     | F1 confluence library (all)                                                | BEST-AVAILABLE-NOT-PROVEN |       -0.044 |          -8.3 | 6118/9842             |    -532 | 9%         | 36%       |               0.148 |                 -8.7 | no                   | 10%/20%                           |           2 | no                 |
| 2     | candle counting, ICT 7-13-21, IRL/ERL                                      | BEST-AVAILABLE-NOT-PROVEN |        0.108 |         -44   | 3528/9842             |    -511 | 8%         | 31%       |               0.148 |                -72.7 | no                   | 10%/70%                           |           2 | no                 |
| 3     | levels and zones (own zones, session/round levels)                         | WEAK-BUT-POSITIVE         |        0.023 |         -16.3 | 8448/9842             |     -58 | 83%        | 41%       |              -0.012 |                -14.8 | no                   | 10%/20%                           |           1 | no                 |
| 4     | range forecasts (HAR / options / UW / own bar)                             | BEST-AVAILABLE-NOT-PROVEN |       -0.054 |          47.6 | 9445/9842             |    -445 | 29%        | 32%       |              -0.158 |                 27.6 | no                   | 0%/60%                            |           2 | no                 |
| 5     | F5 order flow (all)                                                        | WEAK-BUT-POSITIVE         |        0.51  |         -68.7 | 3648/9842             |    -449 | 8%         | 34%       |               0.067 |                -58.6 | yes                  | 40%/100%                          |           3 | no                 |
| 6     | other markets and breadth                                                  | WEAK-BUT-POSITIVE         |        0.237 |         -63   | 3078/9842             |    -455 | 11%        | 34%       |               0.033 |                -57.4 | yes                  | 50%/80%                           |           3 | no                 |
| 7     | Unusual Whales options / positioning                                       | BEST-AVAILABLE-NOT-PROVEN |       -0.114 |          34.4 | 9842/9842             |    -417 | 49%        | 31%       |              -0.022 |                 12.8 | no                   | 0%/0%                             |           1 | no                 |
| 8     | day / regime / time of day / calendar                                      | BEST-AVAILABLE-NOT-PROVEN |       -0.078 |         -57.9 | 3743/9842             |    -517 | 15%        | 36%       |              -0.142 |                -42.4 | yes                  | 30%/10%                           |           0 | no                 |
| 9     | causal trade context (raw)                                                 | WEAK-BUT-POSITIVE         |        0.04  |         -48.7 | 5471/9842             |    -327 | 38%        | 34%       |              -0.062 |                -24   | no                   | 50%/70%                           |           2 | no                 |
| 10    | TICK internals                                                             | WEAK-BUT-POSITIVE         |        0.056 |         -52.2 | 4105/9842             |    -435 | 20%        | 31%       |              -0.078 |                -10   | yes                  | 40%/50%                           |           1 | no                 |
| 1a    | confluence: named indicators / session anchors                             | BEST-AVAILABLE-NOT-PROVEN |        0.281 |         -54.9 | 2987/9842             |    -518 | 5%         | 34%       |               0.203 |                -68.7 | no                   | 0%/50%                            |           2 | no                 |
| 1b    | confluence: entry-table universe                                           | BEST-AVAILABLE-NOT-PROVEN |        0.213 |         -55.4 | 3398/9842             |    -507 | 7%         | 34%       |              -0.066 |                -59.5 | no                   | 50%/90%                           |           2 | no                 |
| 1c    | confluence: oscillators                                                    | BEST-AVAILABLE-NOT-PROVEN |        0.099 |         -42.1 | 3892/9842             |    -501 | 10%        | 32%       |               0.001 |                -56.6 | no                   | 10%/60%                           |           2 | no                 |
| 1d    | confluence: trend                                                          | BEST-AVAILABLE-NOT-PROVEN |       -0.053 |         -63.9 | 2415/9842             |    -536 | 9%         | 32%       |               0.116 |                -21.3 | no                   | 20%/20%                           |           1 | no                 |
| 1e    | confluence: SMC / ICT structure                                            | BEST-AVAILABLE-NOT-PROVEN |        0.185 |         -48.6 | 4510/9842             |    -444 | 14%        | 34%       |               0.067 |                -67   | no                   | 30%/60%                           |           2 | no                 |
| 1f    | confluence: vol / squeeze / state / ML                                     | WEAK-BUT-POSITIVE         |        0.199 |         -67   | 2722/9842             |    -497 | 8%         | 32%       |               0.088 |                -64.9 | no                   | 40%/70%                           |           2 | no                 |
| 1g    | confluence: alternate-bar indicators (HA, range, renko, tick, volume bars) | BEST-AVAILABLE-NOT-PROVEN |       -0.399 |         104.1 | 12076/9842            |    -605 | 9%         | 34%       |              -0.22  |                 24.8 | no                   | 0%/0%                             |           0 | no                 |
| 1h    | confluence: alt-bar agreement                                              | WEAK-BUT-POSITIVE         |        0.285 |         -79.3 | 2327/9842             |    -477 | 8%         | 35%       |               0.048 |                -47.2 | yes                  | 50%/70%                           |           3 | no                 |
| 5a    | order flow: tape prints and speed                                          | WEAK-BUT-POSITIVE         |        0.226 |         -64.5 | 4111/9842             |    -476 | 10%        | 38%       |               0.035 |                -55.3 | yes                  | 60%/70%                           |           2 | no                 |
| 5b    | order flow: L3 / L2 book / flow library                                    | WEAK-BUT-POSITIVE         |        0.373 |         -70.6 | 3497/9842             |    -431 | 11%        | 38%       |               0.006 |                -57.6 | yes                  | 60%/100%                          |           3 | no                 |
| ALL   | ALL families pooled                                                        | BEST-AVAILABLE-NOT-PROVEN |       -0.026 |          -8   | 5063/9842             |    -518 | 12%        | 35%       |               0.058 |                -47.3 | no                   | 40%/50%                           |           1 | no                 |
| NONS  | CONTROL nonsense columns (200)                                             | BEST-AVAILABLE-NOT-PROVEN |        0.158 |         -69   | 2501/9842             |    -478 | 11%        | 32%       |               0.209 |                -65.2 | no                   | 30%/60%                           |           2 | no                 |
| RAND  | CONTROL persistent random columns (90)                                     | BEST-AVAILABLE-NOT-PROVEN |       -0.113 |         -58.1 | 3966/9842             |    -546 | 9%         | 32%       |               0.001 |                -38.5 | no                   | 20%/30%                           |           1 | no                 |
| PLANT | CONTROL planted-edge columns (9)                                           | WEAK-BUT-POSITIVE         |        1.681 |         -93.6 | 547/9842              |     -91 | 11%        | 46%       |               0.262 |                 44.4 | yes                  | 100%/100%                         |           3 | no                 |

Same, trailing 3M picks:


## By number of picks (N) and prior-year gate (all families pooled and each main family, 6M, next 2 weeks)
| set   | gate   |   N | label                     |   dMeanR |   dUlcer% | persist   |   shift dMeanR |   shift dUlcer% | rnd beaten dU/dm   |
|:------|:-------|----:|:--------------------------|---------:|----------:|:----------|---------------:|----------------:|:-------------------|
| ALL   | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.063 |      15.4 | 35%       |         -0.014 |             4.4 | /                  |
| ALL   | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.061 |     -11.2 | 34%       |          0.042 |           -13.9 | /                  |
| ALL   | g0     |   5 | WEAK-BUT-POSITIVE         |    0.125 |     -46.1 | 36%       |          0.007 |             6   | /                  |
| ALL   | g0     |  10 | WEAK-BUT-POSITIVE         |    1.174 |     -83.7 | 34%       |         -0.093 |           -36.8 | /                  |
| ALL   | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.016 |       2.6 | 44%       |         -0.026 |            -0.8 | 30%/50%            |
| ALL   | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.076 |     -27.4 | 36%       |         -0.028 |             1   | 40%/40%            |
| ALL   | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.026 |      -8   | 35%       |          0.058 |           -47.3 | 40%/50%            |
| ALL   | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.319 |     -77.6 | 32%       |          0.379 |           -68.9 | 60%/10%            |
| ALL   | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.006 |      14.7 | 39%       |         -0.038 |             3   | /                  |
| ALL   | g30    |   3 | WEAK-BUT-POSITIVE         |    0.096 |     -35.2 | 44%       |         -0.058 |             8.4 | /                  |
| ALL   | g30    |   5 | WEAK-BUT-POSITIVE         |    0.158 |     -51.1 | 39%       |          0.089 |           -18.9 | /                  |
| ALL   | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.232 |     -64.4 | 34%       |          0.235 |           -41   | /                  |
| 1     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.004 |      -0.8 | 40%       |          0.001 |             2.9 | /                  |
| 1     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.006 |      -9   | 35%       |          0.063 |           -25.9 | /                  |
| 1     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.03  |      -3.6 | 31%       |          0.049 |           -28   | /                  |
| 1     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.544 |     -68.8 | 32%       |          0.174 |           -73.8 | /                  |
| 1     | g15    |   1 | WEAK-BUT-POSITIVE         |    0.042 |     -26   | 46%       |         -0.009 |            -5.4 | 90%/90%            |
| 1     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.06  |      -2   | 36%       |         -0.015 |            12.9 | 10%/10%            |
| 1     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.044 |      -8.3 | 36%       |          0.148 |            -8.7 | 10%/20%            |
| 1     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.618 |     -75   | 32%       |          0.289 |           -62.4 | 50%/30%            |
| 1     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.001 |      -8.7 | 51%       |          0.007 |             2.5 | /                  |
| 1     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.023 |     -11.3 | 39%       |          0.044 |            -4.3 | /                  |
| 1     | g30    |   5 | WEAK-BUT-POSITIVE         |    0.092 |     -45.4 | 38%       |          0.088 |            -0.2 | /                  |
| 1     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.541 |     -30.3 | 32%       |          0.068 |           -34.8 | /                  |
| 2     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.159 |     106   | 31%       |          0.03  |            -7.8 | /                  |
| 2     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.206 |      17.5 | 34%       |          0.11  |           -51.8 | /                  |
| 2     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.308 |      22.1 | 30%       |         -0.053 |           -51.8 | /                  |
| 2     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.5   |     -84.1 | 34%       |          0.951 |           -99.6 | /                  |
| 2     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.085 |      70.3 | 32%       |          0.005 |           -25.4 | 10%/10%            |
| 2     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.064 |     -36.1 | 34%       |          0.101 |           -48.6 | 40%/40%            |
| 2     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.108 |     -44   | 31%       |          0.148 |           -72.7 | 10%/70%            |
| 2     | g15    |  10 | WEAK-BUT-POSITIVE         |    0.197 |     -84.3 | 31%       |         -0.013 |           -83.1 | 80%/90%            |
| 2     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.108 |      68.4 | 29%       |          0.007 |           -16.7 | /                  |
| 2     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.083 |     -30.1 | 32%       |          0.124 |           -54.8 | /                  |
| 2     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.036 |     -30.4 | 31%       |         -0.017 |           -55.3 | /                  |
| 2     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.57  |     -87.6 | 31%       |          0.066 |           -91.9 | /                  |
| 3     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.02  |     -17.5 | 34%       |          0.021 |           -18   | /                  |
| 3     | g0     |   3 | WEAK-BUT-POSITIVE         |    0.014 |     -30.6 | 38%       |         -0.004 |           -26.6 | /                  |
| 3     | g0     |   5 | WEAK-BUT-POSITIVE         |    0.021 |     -32.2 | 39%       |         -0.005 |           -26.9 | /                  |
| 3     | g0     |  10 | WEAK-BUT-POSITIVE         |    0.021 |     -32.2 | 39%       |         -0.005 |           -26.9 | /                  |
| 3     | g15    |   1 | WEAK-BUT-POSITIVE         |    0.001 |     -10.9 | 35%       |         -0.023 |            -5.4 | 40%/20%            |
| 3     | g15    |   3 | WEAK-BUT-POSITIVE         |    0.02  |     -14.9 | 39%       |         -0.011 |           -14.6 | 10%/20%            |
| 3     | g15    |   5 | WEAK-BUT-POSITIVE         |    0.023 |     -16.3 | 41%       |         -0.012 |           -14.8 | 10%/20%            |
| 3     | g15    |  10 | WEAK-BUT-POSITIVE         |    0.023 |     -16.3 | 41%       |         -0.012 |           -14.8 | 10%/20%            |
| 3     | g30    |   1 | WEAK-BUT-POSITIVE         |    0.004 |      -9.2 | 38%       |         -0.019 |            -7.1 | /                  |
| 3     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.019 |     -13.1 | 40%       |         -0.004 |           -16.5 | /                  |
| 3     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.022 |     -14.4 | 41%       |         -0.005 |           -16.6 | /                  |
| 3     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.022 |     -14.4 | 41%       |         -0.005 |           -16.6 | /                  |
| 4     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.062 |       7.6 | 38%       |         -0.115 |             9.8 | /                  |
| 4     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.095 |      41.3 | 38%       |         -0.151 |            10.7 | /                  |
| 4     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.293 |      72   | 33%       |         -0.222 |            32.1 | /                  |
| 4     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.497 |     109.5 | 31%       |         -0.381 |            59.2 | /                  |
| 4     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.029 |       6.9 | 32%       |         -0.074 |            16.9 | 40%/20%            |
| 4     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.01  |      45.3 | 35%       |         -0.121 |            14.7 | 0%/60%             |
| 4     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.054 |      47.6 | 32%       |         -0.158 |            27.6 | 0%/60%             |
| 4     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.094 |      48.6 | 35%       |         -0.185 |            24.8 | 0%/50%             |
| 4     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.08  |       6.6 | 31%       |         -0.064 |            14.2 | /                  |
| 4     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.078 |      48.5 | 37%       |         -0.138 |            18.5 | /                  |
| 4     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.131 |      52.7 | 32%       |         -0.189 |            28.8 | /                  |
| 4     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.119 |      53.9 | 34%       |         -0.206 |            35.1 | /                  |
| 5     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.081 |      34.1 | 41%       |         -0.006 |             0.5 | /                  |
| 5     | g0     |   3 | WEAK-BUT-POSITIVE         |    0.218 |     -56.2 | 36%       |          0.076 |           -49.6 | /                  |
| 5     | g0     |   5 | WEAK-BUT-POSITIVE         |    0.829 |     -86.7 | 36%       |         -0.061 |           -53.8 | /                  |
| 5     | g0     |  10 | WEAK-BUT-POSITIVE         |    1.978 |    -100   | 32%       |          0.07  |           -88.3 | /                  |
| 5     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.047 |      16.6 | 47%       |          0.028 |           -18   | 40%/100%           |
| 5     | g15    |   3 | WEAK-BUT-POSITIVE         |    0.231 |     -42   | 39%       |         -0.035 |           -39.8 | 80%/90%            |
| 5     | g15    |   5 | WEAK-BUT-POSITIVE         |    0.51  |     -68.7 | 34%       |          0.067 |           -58.6 | 40%/100%           |
| 5     | g15    |  10 | WEAK-BUT-POSITIVE         |    1.519 |     -94.9 | 35%       |          0.039 |           -72.4 | 60%/100%           |
| 5     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.025 |      23   | 46%       |          0.02  |           -17.5 | /                  |
| 5     | g30    |   3 | WEAK-BUT-POSITIVE         |    0.243 |     -44.9 | 38%       |         -0.041 |           -40.7 | /                  |
| 5     | g30    |   5 | WEAK-BUT-POSITIVE         |    0.516 |     -69.9 | 34%       |         -0.093 |           -50.6 | /                  |
| 5     | g30    |  10 | WEAK-BUT-POSITIVE         |    1.463 |     -96.5 | 32%       |         -0.119 |           -66.4 | /                  |
| 6     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.039 |     -41.7 | 42%       |          0.073 |           -20.5 | /                  |
| 6     | g0     |   3 | WEAK-BUT-POSITIVE         |    0.122 |     -55.3 | 36%       |         -0.05  |           -31.2 | /                  |
| 6     | g0     |   5 | WEAK-BUT-POSITIVE         |    0.403 |     -76.3 | 34%       |          0.105 |           -61.5 | /                  |
| 6     | g0     |  10 | WEAK-BUT-POSITIVE         |    0.536 |     -90.1 | 31%       |          0.15  |           -83.5 | /                  |
| 6     | g15    |   1 | WEAK-BUT-POSITIVE         |    0.141 |     -44.4 | 48%       |         -0.009 |           -14.4 | 100%/100%          |
| 6     | g15    |   3 | WEAK-BUT-POSITIVE         |    0.231 |     -48.1 | 36%       |         -0.024 |           -26.6 | 80%/90%            |
| 6     | g15    |   5 | WEAK-BUT-POSITIVE         |    0.237 |     -63   | 34%       |          0.033 |           -57.4 | 50%/80%            |
| 6     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.013 |     -67.8 | 34%       |          0.277 |           -81.3 | 0%/60%             |
| 6     | g30    |   1 | WEAK-BUT-POSITIVE         |    0.127 |     -44.3 | 48%       |          0.017 |           -16.9 | /                  |
| 6     | g30    |   3 | WEAK-BUT-POSITIVE         |    0.082 |     -41.8 | 35%       |          0.008 |           -34.7 | /                  |
| 6     | g30    |   5 | WEAK-BUT-POSITIVE         |    0.143 |     -62.2 | 31%       |         -0.043 |           -53.5 | /                  |
| 6     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.283 |     -66.3 | 34%       |          0.082 |           -77   | /                  |
| 7     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.11  |      30.6 | 24%       |         -0.05  |             7.4 | /                  |
| 7     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.141 |      42.3 | 33%       |         -0.03  |            23   | /                  |
| 7     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.119 |      40.2 | 29%       |         -0.017 |             6   | /                  |
| 7     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.096 |       4.6 | 31%       |         -0.035 |           -14.6 | /                  |
| 7     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.08  |      31.9 | 24%       |         -0.032 |             8.6 | 20%/0%             |
| 7     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.103 |      -5.2 | 39%       |         -0.028 |            20.3 | 50%/10%            |
| 7     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.114 |      34.4 | 31%       |         -0.022 |            12.8 | 0%/0%              |
| 7     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.071 |     -22.4 | 31%       |         -0.04  |            -4.1 | 60%/20%            |
| 7     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.086 |      27.8 | 23%       |         -0.033 |            12.7 | /                  |
| 7     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.098 |      -5.6 | 35%       |         -0.03  |            22.5 | /                  |
| 7     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.117 |      38.5 | 31%       |         -0.009 |             8.4 | /                  |
| 7     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.084 |     -21.7 | 31%       |         -0.02  |           -13.6 | /                  |
| 8     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.036 |       1.7 | 34%       |         -0.026 |            -8.7 | /                  |
| 8     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.114 |      36.5 | 29%       |         -0.13  |             6.4 | /                  |
| 8     | g0     |   5 | WEAK-BUT-POSITIVE         |    0.018 |     -57.3 | 31%       |         -0.1   |           -44.3 | /                  |
| 8     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.01  |     -73.9 | 32%       |         -0.28  |           -83.2 | /                  |
| 8     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.032 |      -9.5 | 39%       |         -0.003 |           -13.4 | 30%/50%            |
| 8     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.223 |     120.7 | 30%       |         -0.107 |            -4.9 | 0%/0%              |
| 8     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.078 |     -57.9 | 36%       |         -0.142 |           -42.4 | 30%/10%            |
| 8     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.055 |     -70.7 | 32%       |         -0.09  |           -69.3 | 20%/30%            |
| 8     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.039 |      -1.3 | 40%       |         -0.014 |            -8.1 | /                  |
| 8     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.131 |      75.4 | 35%       |         -0.061 |            -5.2 | /                  |
| 8     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.053 |     -42.6 | 36%       |         -0.006 |           -43.2 | /                  |
| 8     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.184 |     -59.7 | 35%       |          0.052 |           -79.4 | /                  |
| 9     | g0     |   1 | WEAK-BUT-POSITIVE         |    0.136 |     -35.8 | 38%       |         -0.018 |            -7.2 | /                  |
| 9     | g0     |   3 | WEAK-BUT-POSITIVE         |    0.096 |     -56.1 | 31%       |         -0.041 |             5.7 | /                  |
| 9     | g0     |   5 | WEAK-BUT-POSITIVE         |    0.103 |     -55.1 | 30%       |          0.022 |           -10.4 | /                  |
| 9     | g0     |  10 | WEAK-BUT-POSITIVE         |    0.175 |     -61.5 | 31%       |          0.004 |           -36.3 | /                  |
| 9     | g15    |   1 | WEAK-BUT-POSITIVE         |    0.029 |     -33.5 | 32%       |         -0.036 |           -13.9 | 90%/90%            |
| 9     | g15    |   3 | WEAK-BUT-POSITIVE         |    0     |     -37.4 | 33%       |         -0.052 |           -15.3 | 60%/50%            |
| 9     | g15    |   5 | WEAK-BUT-POSITIVE         |    0.04  |     -48.7 | 34%       |         -0.062 |           -24   | 50%/70%            |
| 9     | g15    |  10 | WEAK-BUT-POSITIVE         |    0.033 |     -48.3 | 34%       |         -0.065 |           -30.4 | 50%/70%            |
| 9     | g30    |   1 | WEAK-BUT-POSITIVE         |    0.049 |     -33.2 | 31%       |         -0.029 |           -13.8 | /                  |
| 9     | g30    |   3 | WEAK-BUT-POSITIVE         |    0.021 |     -45.3 | 28%       |         -0.049 |            -3.4 | /                  |
| 9     | g30    |   5 | WEAK-BUT-POSITIVE         |    0.129 |     -61.1 | 32%       |         -0.066 |           -18.3 | /                  |
| 9     | g30    |  10 | WEAK-BUT-POSITIVE         |    0.117 |     -61.5 | 32%       |         -0.085 |           -27.9 | /                  |
| 10    | g0     |   1 | WEAK-BUT-POSITIVE         |    0.063 |     -19   | 43%       |         -0.028 |            12.7 | /                  |
| 10    | g0     |   3 | WEAK-BUT-POSITIVE         |    0.156 |     -49   | 33%       |         -0.018 |            -8.8 | /                  |
| 10    | g0     |   5 | WEAK-BUT-POSITIVE         |    0.122 |     -69.8 | 31%       |         -0.091 |           -13.3 | /                  |
| 10    | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.169 |     -28.6 | 29%       |         -0.352 |            12.6 | /                  |
| 10    | g15    |   1 | WEAK-BUT-POSITIVE         |    0.014 |     -22.5 | 33%       |         -0.006 |           -13   | 60%/20%            |
| 10    | g15    |   3 | WEAK-BUT-POSITIVE         |    0.04  |     -54.8 | 34%       |         -0.067 |           -16   | 90%/50%            |
| 10    | g15    |   5 | WEAK-BUT-POSITIVE         |    0.056 |     -52.2 | 31%       |         -0.078 |           -10   | 40%/50%            |
| 10    | g15    |  10 | WEAK-BUT-POSITIVE         |    0.057 |     -45.9 | 31%       |         -0.081 |           -21.6 | 20%/70%            |
| 10    | g30    |   1 | WEAK-BUT-POSITIVE         |    0.013 |     -22.9 | 31%       |         -0.017 |           -15.2 | /                  |
| 10    | g30    |   3 | WEAK-BUT-POSITIVE         |    0.051 |     -55.4 | 35%       |         -0.073 |           -22.1 | /                  |
| 10    | g30    |   5 | WEAK-BUT-POSITIVE         |    0.082 |     -52.9 | 31%       |         -0.117 |           -12.9 | /                  |
| 10    | g30    |  10 | WEAK-BUT-POSITIVE         |    0.066 |     -48.9 | 31%       |         -0.17  |            -4.2 | /                  |

## By horizon (picks traded the next 2 weeks / 1 month / 3 months; ALL pooled and main families; N=5, 6M, g15)
| set   | horizon   | label                     |   dMeanR |   dUlcer% | persist   |   shift dMeanR |   shift dUlcer% |
|:------|:----------|:--------------------------|---------:|----------:|:----------|---------------:|----------------:|
| ALL   | 2W        | BEST-AVAILABLE-NOT-PROVEN |   -0.026 |      -8   | 35%       |          0.058 |           -47.3 |
| ALL   | 1M        | BEST-AVAILABLE-NOT-PROVEN |   -0.226 |      34.7 | 25%       |         -0.046 |           -45.4 |
| ALL   | 3M        | WEAK-BUT-POSITIVE         |    0.131 |     -65.1 | 8%        |         -0.004 |           -29.1 |
| 1     | 2W        | BEST-AVAILABLE-NOT-PROVEN |   -0.044 |      -8.3 | 36%       |          0.148 |            -8.7 |
| 1     | 1M        | BEST-AVAILABLE-NOT-PROVEN |   -0.08  |     -44.3 | 25%       |         -0.057 |            15.4 |
| 1     | 3M        | WEAK-BUT-POSITIVE         |    0.151 |     -55.7 | 8%        |          0.139 |           -22.2 |
| 2     | 2W        | BEST-AVAILABLE-NOT-PROVEN |    0.108 |     -44   | 31%       |          0.148 |           -72.7 |
| 2     | 1M        | BEST-AVAILABLE-NOT-PROVEN |    0.061 |     -44.1 | 30%       |          0.328 |           -59.5 |
| 2     | 3M        | BEST-AVAILABLE-NOT-PROVEN |   -0.066 |      -1.9 | 15%       |          0.372 |           -67   |
| 3     | 2W        | WEAK-BUT-POSITIVE         |    0.023 |     -16.3 | 41%       |         -0.012 |           -14.8 |
| 3     | 1M        | BEST-AVAILABLE-NOT-PROVEN |    0.017 |     -14.8 | 25%       |         -0.009 |           -17.7 |
| 3     | 3M        | BEST-AVAILABLE-NOT-PROVEN |    0.014 |     -16.7 | 29%       |          0.008 |           -19.3 |
| 4     | 2W        | BEST-AVAILABLE-NOT-PROVEN |   -0.054 |      47.6 | 32%       |         -0.158 |            27.6 |
| 4     | 1M        | BEST-AVAILABLE-NOT-PROVEN |   -0.09  |      38.6 | 26%       |         -0.145 |            19.9 |
| 4     | 3M        | BEST-AVAILABLE-NOT-PROVEN |   -0.125 |      -2.3 | 8%        |         -0.136 |             6   |
| 5     | 2W        | WEAK-BUT-POSITIVE         |    0.51  |     -68.7 | 34%       |          0.067 |           -58.6 |
| 5     | 1M        | WEAK-BUT-POSITIVE         |    0.821 |     -82.1 | 32%       |         -0.061 |           -52.2 |
| 5     | 3M        | WEAK-BUT-POSITIVE         |    0.321 |     -48   | 8%        |         -0.102 |           -41.1 |
| 6     | 2W        | WEAK-BUT-POSITIVE         |    0.237 |     -63   | 34%       |          0.033 |           -57.4 |
| 6     | 1M        | WEAK-BUT-POSITIVE         |    0.28  |     -68.6 | 32%       |          0.107 |           -64.9 |
| 6     | 3M        | WEAK-BUT-POSITIVE         |    0.279 |     -73.8 | 8%        |          0.158 |           -51.4 |
| 7     | 2W        | BEST-AVAILABLE-NOT-PROVEN |   -0.114 |      34.4 | 31%       |         -0.022 |            12.8 |
| 7     | 1M        | BEST-AVAILABLE-NOT-PROVEN |   -0.122 |      12.9 | 24%       |         -0.036 |            13.5 |
| 7     | 3M        | BEST-AVAILABLE-NOT-PROVEN |   -0.117 |      16.3 | 0%        |         -0.063 |            30.9 |
| 8     | 2W        | BEST-AVAILABLE-NOT-PROVEN |   -0.078 |     -57.9 | 36%       |         -0.142 |           -42.4 |
| 8     | 1M        | BEST-AVAILABLE-NOT-PROVEN |   -0.068 |     -51.4 | 32%       |         -0.208 |           -38.5 |
| 8     | 3M        | WEAK-BUT-POSITIVE         |    0.054 |     -56.9 | 8%        |         -0.06  |           -42.7 |
| 9     | 2W        | WEAK-BUT-POSITIVE         |    0.04  |     -48.7 | 34%       |         -0.062 |           -24   |
| 9     | 1M        | WEAK-BUT-POSITIVE         |    0.095 |     -53   | 31%       |         -0.024 |           -26.1 |
| 9     | 3M        | WEAK-BUT-POSITIVE         |    0.115 |     -54.8 | 8%        |         -0.007 |           -25.8 |
| 10    | 2W        | WEAK-BUT-POSITIVE         |    0.056 |     -52.2 | 31%       |         -0.078 |           -10   |
| 10    | 1M        | WEAK-BUT-POSITIVE         |    0.098 |     -68.5 | 28%       |         -0.081 |            -8.2 |
| 10    | 3M        | WEAK-BUT-POSITIVE         |    0.208 |     -64.9 | 15%       |         -0.05  |           -18.2 |

## By windows (chained OOS pieces whose refit falls in the window; N=5, 6M picks, g15; real vs mean of shifted-label nulls)
| set   | window   |   n trades |   dMeanR |   dUlcer% | maxDD rule/base $   |   d$/wk (base lots, $4.84) | persist   |   shift-null dMeanR |   shift-null dUlcer% |
|:------|:---------|-----------:|---------:|----------:|:--------------------|---------------------------:|:----------|--------------------:|---------------------:|
| ALL   | L3M      |         27 |   -0.42  |     -63.6 | 1510/4139           |                       -330 | 33%       |              -0.38  |                -40.3 |
| ALL   | L6M      |         60 |   -0.65  |     -43.1 | 3597/8448           |                       -382 | 33%       |              -0.171 |                -58.7 |
| ALL   | HOLD     |         73 |    1.188 |     -94.3 | 397/4649            |                      -1067 | 23%       |               0.138 |                -51.8 |
| ALL   | GAP      |         38 |   -1.295 |     -54.6 | 995/4489            |                       -745 | 29%       |              -0.039 |               -100   |
| ALL   | PRE      |        117 |   -0.282 |      25   | 4354/7024           |                       -789 | 37%       |               0.098 |                -67.1 |
| ALL   | XP       |        132 |    0.469 |     -66.9 | 2402/9842           |                       -119 | 44%       |               0.069 |                -49.3 |
| ALL   | POOLED   |        433 |   -0.026 |      -8   | 5063/9842           |                       -518 | 35%       |               0.058 |                -47.3 |
| 1     | L3M      |         27 |   -0.589 |     -45.9 | 1596/4139           |                       -375 | 33%       |              -0.346 |                -73.3 |
| 1     | L6M      |         60 |   -0.758 |     -34.8 | 3782/8448           |                       -403 | 33%       |              -0.057 |                -76.5 |
| 1     | HOLD     |         73 |    1.244 |     -96.8 | 197/4649            |                      -1138 | 15%       |               0.134 |                -44   |
| 1     | GAP      |         38 |   -1.029 |     -42.6 | 2385/4489           |                       -843 | 29%       |               0.154 |               -100   |
| 1     | PRE      |        117 |   -0.076 |     -39.1 | 2340/7024           |                       -768 | 42%       |               0.234 |                -53.5 |
| 1     | XP       |        132 |    0.485 |     -63.6 | 2794/9842           |                       -101 | 48%       |               0.002 |                  2.4 |
| 1     | POOLED   |        433 |   -0.044 |      -8.3 | 6118/9842           |                       -532 | 36%       |               0.148 |                 -8.7 |
| 2     | L3M      |         27 |    1.287 |     -89.3 | 435/4139            |                         83 | 33%       |               0.093 |                -89.5 |
| 2     | L6M      |         60 |    0.198 |     -78.1 | 2937/8448           |                       -117 | 33%       |              -0.088 |                -87.8 |
| 2     | HOLD     |         73 |    0.793 |     -84.9 | 591/4649            |                      -1045 | 15%       |               0.239 |                -73.6 |
| 2     | GAP      |         38 |    0.001 |     -69.9 | 1046/4489           |                       -595 | 29%       |              -0.664 |                -61.9 |
| 2     | PRE      |        117 |    0.404 |     -64.1 | 1235/7024           |                       -711 | 37%       |              -0.009 |                -73   |
| 2     | XP       |        132 |   -0.423 |     -33   | 3204/9842           |                       -326 | 33%       |               0.243 |                -85.2 |
| 2     | POOLED   |        433 |    0.108 |     -44   | 3528/9842           |                       -511 | 31%       |               0.148 |                -72.7 |
| 3     | L3M      |         27 |    0     |       0   | 4139/4139           |                          0 |           |              -0.013 |                  0   |
| 3     | L6M      |         60 |    0     |       0   | 8448/8448           |                          0 |           |               0.011 |                 -6.4 |
| 3     | HOLD     |         73 |    0     |       0   | 4649/4649           |                          0 |           |              -0.014 |                 -8.8 |
| 3     | GAP      |         38 |   -0.047 |       2   | 4489/4489           |                       -143 | 0%        |              -0.034 |                 -8.2 |
| 3     | PRE      |        117 |   -0.081 |       5   | 7024/7024           |                       -265 | 17%       |              -0.121 |                  3   |
| 3     | XP       |        132 |    0.167 |     -49.5 | 4253/9842           |                         50 | 50%       |               0.082 |                -43.6 |
| 3     | POOLED   |        433 |    0.023 |     -16.3 | 8448/9842           |                        -58 | 41%       |              -0.012 |                -14.8 |
| 4     | L3M      |         27 |    0.15  |     -32.4 | 2429/4139           |                         43 | 67%       |              -0.034 |                -39.3 |
| 4     | L6M      |         60 |    0.024 |     -62.9 | 2429/8448           |                       -164 | 50%       |              -0.144 |                -53   |
| 4     | HOLD     |         73 |    0.267 |     -52.2 | 1725/4649           |                       -847 | 15%       |               0.143 |                -63.2 |
| 4     | GAP      |         38 |   -0.252 |     -37.5 | 2904/4489           |                       -630 | 29%       |              -0.043 |                -50.8 |
| 4     | PRE      |        117 |    0.166 |     -71.2 | 3059/7024           |                       -435 | 37%       |              -0.078 |                -27.8 |
| 4     | XP       |        132 |   -0.304 |     108.3 | 9445/9842           |                       -391 | 29%       |              -0.18  |                 57.2 |
| 4     | POOLED   |        433 |   -0.054 |      47.6 | 9445/9842           |                       -445 | 32%       |              -0.158 |                 27.6 |
| 5     | L3M      |         27 |    0.171 |     -59.3 | 1160/4139           |                       -182 | 33%       |              -0.297 |                -64.5 |
| 5     | L6M      |         60 |   -0.16  |     -80.2 | 1160/8448           |                       -256 | 33%       |               0.022 |                -68.6 |
| 5     | HOLD     |         73 |    1.288 |     -89   | 795/4649            |                       -791 | 23%       |              -0.071 |                -84.6 |
| 5     | GAP      |         38 |   -0.669 |     -37.8 | 3261/4489           |                       -791 | 43%       |              -0.367 |                -63.2 |
| 5     | PRE      |        117 |    0.475 |     -86.4 | 795/7024            |                       -586 | 37%       |               0.25  |                -78.1 |
| 5     | XP       |        132 |    1.427 |     -98.7 | 380/9842            |                       -234 | 37%       |               0.107 |                -63.7 |
| 5     | POOLED   |        433 |    0.51  |     -68.7 | 3648/9842           |                       -449 | 34%       |               0.067 |                -58.6 |
| 6     | L3M      |         27 |    1.661 |     -93.5 | 192/4139            |                        -17 | 50%       |              -0.178 |                -71.3 |
| 6     | L6M      |         60 |    0.278 |     -83.2 | 1538/8448           |                       -139 | 42%       |               0.037 |                -72.8 |
| 6     | HOLD     |         73 |    0.408 |     -70   | 1353/4649           |                      -1020 | 23%       |              -0.168 |                -33.8 |
| 6     | GAP      |         38 |    0.494 |     -70.4 | 800/4489            |                       -204 | 57%       |              -0.246 |                -74.7 |
| 6     | PRE      |        117 |    0.146 |     -72.4 | 1419/7024           |                       -730 | 37%       |              -0.254 |                -63.2 |
| 6     | XP       |        132 |    0.16  |     -61.3 | 3078/9842           |                       -225 | 30%       |               0.686 |                -79.8 |
| 6     | POOLED   |        433 |    0.237 |     -63   | 3078/9842           |                       -455 | 34%       |               0.033 |                -57.4 |
| 7     | L3M      |         27 |    0.073 |     -63.5 | 1253/4139           |                       -115 | 33%       |               0.092 |                -85.4 |
| 7     | L6M      |         60 |   -0.241 |     -43.3 | 3508/8448           |                       -309 | 33%       |              -0.16  |                -66.6 |
| 7     | HOLD     |         73 |   -0.707 |     -21.1 | 2386/4649           |                      -1299 | 15%       |              -0.032 |                -58.1 |
| 7     | GAP      |         38 |   -0.198 |     -23.9 | 3989/4489           |                       -591 | 29%       |              -0.014 |                -67.1 |
| 7     | PRE      |        117 |    0.06  |     -50.5 | 6024/7024           |                       -488 | 41%       |               0.103 |                 16.4 |
| 7     | XP       |        132 |    0     |       0   | 9842/9842           |                          0 |           |               0     |                  0   |
| 7     | POOLED   |        433 |   -0.114 |      34.4 | 9842/9842           |                       -417 | 31%       |              -0.022 |                 12.8 |
| 8     | L3M      |         27 |    0.192 |     -59.4 | 1288/4139           |                        -56 | 50%       |              -0.42  |                -50.4 |
| 8     | L6M      |         60 |   -0.016 |     -64.5 | 2258/8448           |                       -185 | 42%       |              -0.365 |                -35.2 |
| 8     | HOLD     |         73 |   -0.31  |     -66.2 | 1434/4649           |                      -1162 | 15%       |              -0.016 |                -27.9 |
| 8     | GAP      |         38 |    0.298 |     -72.9 | 1024/4489           |                       -319 | 43%       |              -0.156 |                -82.3 |
| 8     | PRE      |        117 |   -0.268 |     -63.1 | 3233/7024           |                       -790 | 37%       |              -0.166 |                -63.2 |
| 8     | XP       |        132 |   -0.043 |     -61.1 | 3130/9842           |                       -271 | 41%       |              -0.09  |                -55.5 |
| 8     | POOLED   |        433 |   -0.078 |     -57.9 | 3743/9842           |                       -517 | 36%       |              -0.142 |                -42.4 |
| 9     | L3M      |         27 |    0.096 |     -13.1 | 3094/4139           |                        121 | 67%       |              -0.348 |                -22.5 |
| 9     | L6M      |         60 |    0.024 |     -29.2 | 5471/8448           |                        -33 | 44%       |              -0.043 |                -40.6 |
| 9     | HOLD     |         73 |   -0.105 |       9.1 | 3964/4649           |                       -972 | 23%       |              -0.25  |                 -4.9 |
| 9     | GAP      |         38 |    0.124 |     -45.6 | 2889/4489           |                       -347 | 29%       |              -0.324 |                -51.1 |
| 9     | PRE      |        117 |    0.066 |     -45.8 | 3959/7024           |                       -363 | 39%       |              -0.03  |                -34   |
| 9     | XP       |        132 |    0.072 |     -76   | 3302/9842           |                       -192 | 33%       |               0.075 |                -45.1 |
| 9     | POOLED   |        433 |    0.04  |     -48.7 | 5471/9842           |                       -327 | 34%       |              -0.062 |                -24   |
| 10    | L3M      |         27 |    0.326 |     -65.6 | 1810/4139           |                         65 | 50%       |              -0.122 |                -32.7 |
| 10    | L6M      |         60 |    0.407 |     -81.5 | 1810/8448           |                         99 | 50%       |              -0.099 |                -56.2 |
| 10    | HOLD     |         73 |    0.266 |     -76.9 | 1226/4649           |                       -953 | 23%       |              -0.156 |                -15   |
| 10    | GAP      |         38 |    0.053 |     -46.9 | 2409/4489           |                       -383 | 29%       |              -0.274 |                -45.4 |
| 10    | PRE      |        117 |   -0.055 |     -63.8 | 2369/7024           |                       -689 | 26%       |              -0.096 |                -20.3 |
| 10    | XP       |        132 |   -0.2   |     -43.8 | 4105/9842           |                       -308 | 30%       |              -0.065 |                 -4   |
| 10    | POOLED   |        433 |    0.056 |     -52.2 | 4105/9842           |                       -435 | 31%       |              -0.078 |                -10   |

## Time thirds (2023-10..2024-09, 2024-10..2025-09, 2025-10..2026-10), N=5, 6M, g15, next 2 weeks
| set   | T1                     | T2                     | T3                    |
|:------|:-----------------------|:-----------------------|:----------------------|
| ALL   | +0.493 R / -66.9% ulc  | -0.393 R / +49.5% ulc  | -0.183 R / -51.6% ulc |
| 1     | +0.376 R / -63.6% ulc  | +0.022 R / -22.8% ulc  | -0.649 R / -33.3% ulc |
| 2     | -0.399 R / -33.3% ulc  | +0.303 R / -63.8% ulc  | +0.244 R / -73.2% ulc |
| 3     | +0.136 R / -49.6% ulc  | -0.060 R / +11.0% ulc  | +0.000 R / +0.0% ulc  |
| 4     | -0.321 R / +107.2% ulc | +0.088 R / -55.4% ulc  | +0.047 R / -52.9% ulc |
| 5     | +1.451 R / -98.7% ulc  | +0.228 R / -81.4% ulc  | +0.568 R / -71.1% ulc |
| 6     | +0.183 R / -61.3% ulc  | +0.331 R / -68.0% ulc  | +0.185 R / -60.3% ulc |
| 7     | +0.000 R / +0.0% ulc   | +0.064 R / -41.8% ulc  | -0.489 R / +52.5% ulc |
| 8     | -0.019 R / -61.1% ulc  | -0.069 R / -40.1% ulc  | -0.144 R / -65.3% ulc |
| 9     | +0.066 R / -76.1% ulc  | +0.084 R / -46.7% ulc  | -0.063 R / -23.3% ulc |
| 10    | -0.176 R / -44.9% ulc  | -0.104 R / -56.7% ulc  | +0.306 R / -80.4% ulc |
| 1a    | +0.584 R / -90.0% ulc  | -0.429 R / -15.6% ulc  | +0.541 R / -84.1% ulc |
| 1b    | -0.228 R / -40.1% ulc  | +0.800 R / -75.6% ulc  | +0.102 R / -74.2% ulc |
| 1c    | -0.404 R / -41.1% ulc  | +0.354 R / -54.3% ulc  | +0.018 R / -39.6% ulc |
| 1d    | -0.085 R / -73.1% ulc  | -0.161 R / -51.0% ulc  | +0.129 R / -66.7% ulc |
| 1e    | +0.451 R / -75.0% ulc  | -0.024 R / +4.5% ulc   | +0.191 R / -75.1% ulc |
| 1f    | +0.946 R / -87.9% ulc  | -0.412 R / -44.0% ulc  | +0.130 R / -69.3% ulc |
| 1g    | -0.015 R / -32.0% ulc  | -0.362 R / +142.1% ulc | -0.797 R / -24.1% ulc |
| 1h    | +0.352 R / -76.8% ulc  | +0.776 R / -83.6% ulc  | +0.088 R / -79.6% ulc |
| 5a    | +0.535 R / -67.7% ulc  | +0.430 R / -74.7% ulc  | -0.091 R / -54.1% ulc |
| 5b    | +0.238 R / -82.1% ulc  | +0.246 R / -64.1% ulc  | +0.557 R / -81.2% ulc |
| NONS  | -0.193 R / -63.7% ulc  | +0.199 R / -68.7% ulc  | +0.433 R / -77.4% ulc |
| RAND  | +0.192 R / -81.2% ulc  | -0.084 R / -30.1% ulc  | -0.392 R / -53.3% ulc |
| PLANT | +1.536 R / -94.5% ulc  | +1.716 R / -95.5% ulc  | +1.778 R / -94.6% ulc |

## Per book x session (ALL families pooled, N=5, 6M picks, g15, next 2 weeks) with shifted-label and random-skip nulls per cell
| cell (book_session)   |   trades OOS |   dMeanR |   dUlcer% | persist   |   shift dMeanR |   shift dUlcer% |   random-skip dMeanR |   random-skip dUlcer% | beats random dU/dm   |
|:----------------------|-------------:|---------:|----------:|:----------|---------------:|----------------:|---------------------:|----------------------:|:---------------------|
| O7_3                  |          433 |   -0.026 |        -8 | 35%       |          0.058 |           -47.3 |                0.014 |                 -30.2 | 40%/50%              |

Per cell by family (N=5, 6M, g15, 2 weeks): dMeanR / dUlcer% real vs shifted-label mean:
| cell   | 1                          | 2                            | 3                            | 4                            | 5                            | 6                            | 7                            | 8                            | 9                            | 10                           | ALL                         |
|:-------|:---------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:----------------------------|
| O7_3   | -0.044/-8% (sh +0.148/-9%) | +0.108/-44% (sh +0.148/-73%) | +0.023/-16% (sh -0.012/-15%) | -0.054/+48% (sh -0.158/+28%) | +0.510/-69% (sh +0.067/-59%) | +0.237/-63% (sh +0.033/-57%) | -0.114/+34% (sh -0.022/+13%) | -0.078/-58% (sh -0.142/-42%) | +0.040/-49% (sh -0.062/-24%) | +0.056/-52% (sh -0.078/-10%) | -0.026/-8% (sh +0.058/-47%) |

## Persistence, turnover and decay of the picks (ALL families pooled, N=5, 6M, g15)
Turnover: mean share of the top-5 list retained from one refit to the next (higher = more stable picks): O7_3 25%; overall 25%.
Decay: summed gain/loss ($, base lots, $4.84) of the picks by how many 2-week blocks after the refit they are traded (0 = the next 2 weeks):
| set   | labels   | lag 0 (0-13 d)             | lag 1 (14-27 d)            | lag 2 (28-41 d)            | lag 3 (42-55 d)             | lag 4 (56-69 d)            | lag 5 (70-83 d)            |
|:------|:---------|:---------------------------|:---------------------------|:---------------------------|:----------------------------|:---------------------------|:---------------------------|
| ALL   | real     | -80159$ (36% of pieces >0) | -84680$ (34% of pieces >0) | -82755$ (34% of pieces >0) | -92302$ (29% of pieces >0)  | -90584$ (31% of pieces >0) | -90822$ (34% of pieces >0) |
| ALL   | shift11  | -68757$ (36% of pieces >0) | -69872$ (39% of pieces >0) | -77296$ (30% of pieces >0) | -83850$ (33% of pieces >0)  | -94223$ (30% of pieces >0) | -87345$ (33% of pieces >0) |
| 1     | real     | -82484$ (37% of pieces >0) | -81990$ (31% of pieces >0) | -89954$ (35% of pieces >0) | -77318$ (33% of pieces >0)  | -89916$ (32% of pieces >0) | -90784$ (33% of pieces >0) |
| 1     | shift11  | -57610$ (32% of pieces >0) | -72779$ (38% of pieces >0) | -64956$ (35% of pieces >0) | -84946$ (29% of pieces >0)  | -95486$ (26% of pieces >0) | -81338$ (34% of pieces >0) |
| 2     | real     | -79012$ (32% of pieces >0) | -86427$ (30% of pieces >0) | -88978$ (35% of pieces >0) | -103452$ (33% of pieces >0) | -95396$ (31% of pieces >0) | -85201$ (30% of pieces >0) |
| 2     | shift11  | -82101$ (32% of pieces >0) | -79143$ (34% of pieces >0) | -92157$ (34% of pieces >0) | -91332$ (32% of pieces >0)  | -92545$ (31% of pieces >0) | -89168$ (33% of pieces >0) |
| 3     | real     | -9240$ (38% of pieces >0)  | -9945$ (43% of pieces >0)  | -15544$ (35% of pieces >0) | -24504$ (35% of pieces >0)  | -17355$ (35% of pieces >0) | -17323$ (35% of pieces >0) |
| 3     | shift11  | -19453$ (29% of pieces >0) | -16325$ (32% of pieces >0) | -28671$ (27% of pieces >0) | -28553$ (31% of pieces >0)  | -30235$ (27% of pieces >0) | -26727$ (31% of pieces >0) |
| 5     | real     | -69264$ (35% of pieces >0) | -61517$ (39% of pieces >0) | -70898$ (32% of pieces >0) | -82904$ (35% of pieces >0)  | -92563$ (34% of pieces >0) | -77039$ (33% of pieces >0) |
| 5     | shift11  | -80304$ (35% of pieces >0) | -78040$ (35% of pieces >0) | -90465$ (34% of pieces >0) | -94154$ (32% of pieces >0)  | -95082$ (30% of pieces >0) | -97620$ (28% of pieces >0) |
| 7     | real     | -64460$ (33% of pieces >0) | -64356$ (33% of pieces >0) | -50278$ (36% of pieces >0) | -47627$ (37% of pieces >0)  | -42919$ (35% of pieces >0) | -49853$ (38% of pieces >0) |
| 7     | shift11  | -64619$ (35% of pieces >0) | -60860$ (35% of pieces >0) | -63665$ (33% of pieces >0) | -60621$ (30% of pieces >0)  | -51024$ (31% of pieces >0) | -55125$ (33% of pieces >0) |
| 10    | real     | -68038$ (32% of pieces >0) | -65665$ (31% of pieces >0) | -60705$ (33% of pieces >0) | -76500$ (32% of pieces >0)  | -80198$ (31% of pieces >0) | -76695$ (36% of pieces >0) |
| 10    | shift11  | -74600$ (28% of pieces >0) | -68654$ (29% of pieces >0) | -70894$ (32% of pieces >0) | -68092$ (33% of pieces >0)  | -77581$ (29% of pieces >0) | -61612$ (39% of pieces >0) |
| NONS  | real     | -73854$ (33% of pieces >0) | -90179$ (31% of pieces >0) | -78037$ (33% of pieces >0) | -89131$ (31% of pieces >0)  | -86745$ (32% of pieces >0) | -83809$ (32% of pieces >0) |
| NONS  | shift11  | -71753$ (34% of pieces >0) | -81833$ (30% of pieces >0) | -84298$ (33% of pieces >0) | -89824$ (29% of pieces >0)  | -79082$ (34% of pieces >0) | -85195$ (29% of pieces >0) |

## SCORES (equal-weight vote of the top 5 / top 10 recent conditions; g15 picks; rule = trade by thirds of the vote, next 2 weeks chained, 6M picks)
| set   |   K | rule       |   dMeanR |   dUlcer% |   d$/wk | persist   |   shift dMeanR |   shift dUlcer% | beats 3 shifts   |
|:------|----:|:-----------|---------:|----------:|--------:|:----------|---------------:|----------------:|:-----------------|
| ALL   |   5 | skip_low   |   -0.041 |      14   |    -281 | 34%       |         -0.053 |            12.2 | no               |
| ALL   |   5 | half_low   |   -0.016 |     -15.7 |    -141 | 34%       |         -0.019 |            -9.4 | no               |
| ALL   |   5 | boost_high |   -0.002 |      28.9 |     141 | 66%       |         -0.013 |            38.1 | no               |
| ALL   |  10 | skip_low   |    0.028 |       4   |    -158 | 42%       |         -0.034 |            15.8 | no               |
| ALL   |  10 | half_low   |    0.011 |      -5.1 |     -79 | 42%       |         -0.014 |            -3.9 | no               |
| ALL   |  10 | boost_high |   -0.011 |      34.7 |      92 | 63%       |         -0.005 |            28.6 | no               |
| 1     |   5 | skip_low   |   -0.045 |       1.3 |    -303 | 33%       |         -0.036 |            17.4 | no               |
| 1     |   5 | half_low   |   -0.016 |     -16.1 |    -151 | 33%       |         -0.013 |           -11.5 | no               |
| 1     |   5 | boost_high |    0     |      28.3 |     141 | 67%       |         -0.004 |            26.8 | no               |
| 1     |  10 | skip_low   |   -0.069 |      37.5 |    -295 | 35%       |         -0.011 |            -3.5 | no               |
| 1     |  10 | half_low   |   -0.027 |       5   |    -147 | 35%       |         -0.004 |           -10   | no               |
| 1     |  10 | boost_high |   -0.027 |      36.1 |      44 | 58%       |          0     |            27.4 | no               |
| 2     |   5 | skip_low   |   -0.032 |       6.7 |    -319 | 36%       |         -0.009 |           -15.3 | no               |
| 2     |   5 | half_low   |   -0.011 |     -11.5 |    -160 | 36%       |         -0.003 |           -18.6 | no               |
| 2     |   5 | boost_high |    0.002 |      32.7 |     127 | 59%       |         -0.009 |            29   | no               |
| 2     |  10 | skip_low   |   -0.062 |      26.6 |    -315 | 35%       |          0.014 |           -12.3 | no               |
| 2     |  10 | half_low   |   -0.023 |      -1.4 |    -158 | 35%       |          0.005 |           -15.9 | no               |
| 2     |  10 | boost_high |    0.002 |      26   |     122 | 60%       |          0.004 |            23.5 | no               |
| 3     |   5 | skip_low   |    0.006 |     -15.5 |     -89 | 42%       |         -0.028 |            -9.2 | no               |
| 3     |   5 | half_low   |    0.003 |     -11.7 |     -44 | 42%       |         -0.012 |           -10.2 | no               |
| 3     |   5 | boost_high |   -0.002 |       6.9 |      47 | 66%       |         -0.009 |            17.7 | yes              |
| 3     |  10 | skip_low   |    0.006 |     -15.5 |     -89 | 42%       |         -0.028 |            -9.2 | no               |
| 3     |  10 | half_low   |    0.003 |     -11.7 |     -44 | 42%       |         -0.012 |           -10.2 | no               |
| 3     |  10 | boost_high |   -0.002 |       6.9 |      47 | 66%       |         -0.01  |            18.1 | yes              |
| 5     |   5 | skip_low   |    0.115 |      -1.4 |     -92 | 46%       |          0.016 |           -10.9 | no               |
| 5     |   5 | half_low   |    0.042 |      -5.6 |     -46 | 46%       |          0.006 |           -14.3 | no               |
| 5     |   5 | boost_high |    0.031 |      35.6 |     223 | 69%       |         -0.004 |            30.2 | no               |
| 5     |  10 | skip_low   |    0.141 |      -0.1 |     -18 | 51%       |          0.017 |           -10.8 | no               |
| 5     |  10 | half_low   |    0.055 |      -6.3 |      -9 | 51%       |          0.006 |           -13.8 | no               |
| 5     |  10 | boost_high |    0.023 |      39.5 |     184 | 67%       |          0     |            31.1 | no               |
| 7     |   5 | skip_low   |   -0.118 |      27.6 |    -362 | 23%       |         -0.06  |             7.6 | no               |
| 7     |   5 | half_low   |   -0.047 |      -4.9 |    -181 | 23%       |         -0.024 |            -6   | no               |
| 7     |   5 | boost_high |   -0.026 |      18.1 |      20 | 52%       |         -0.009 |            17.3 | no               |
| 7     |  10 | skip_low   |   -0.062 |      -7.9 |    -257 | 30%       |         -0.034 |             6.6 | no               |
| 7     |  10 | half_low   |   -0.026 |      -8.7 |    -129 | 30%       |         -0.015 |            -2.9 | no               |
| 7     |  10 | boost_high |   -0.003 |      14.2 |      62 | 57%       |         -0.005 |            13.7 | no               |
| 10    |   5 | skip_low   |    0.037 |     -33.5 |    -230 | 37%       |         -0.005 |            -2   | yes              |
| 10    |   5 | half_low   |    0.013 |     -25.8 |    -115 | 37%       |         -0.002 |           -11.1 | yes              |
| 10    |   5 | boost_high |    0.008 |      29.9 |     141 | 64%       |         -0.012 |            28.1 | no               |
| 10    |  10 | skip_low   |    0.065 |     -36   |    -198 | 38%       |         -0.004 |            -3.1 | yes              |
| 10    |  10 | half_low   |    0.022 |     -24.5 |     -99 | 38%       |         -0.002 |           -14.6 | yes              |
| 10    |  10 | boost_high |    0.022 |      19.5 |     172 | 62%       |         -0.002 |            22.2 | no               |
| 1c    |   5 | skip_low   |   -0.004 |     -32   |    -233 | 45%       |         -0.008 |           -10.3 | no               |
| 1c    |   5 | half_low   |   -0.002 |     -22.2 |    -116 | 45%       |         -0.003 |           -15.1 | no               |
| 1c    |   5 | boost_high |   -0.001 |      21.6 |     128 | 56%       |         -0.006 |            29.9 | no               |
| 1c    |  10 | skip_low   |   -0.025 |     -23.9 |    -234 | 39%       |          0.048 |           -11.2 | no               |
| 1c    |  10 | half_low   |   -0.01  |     -18   |    -117 | 39%       |          0.018 |           -13.2 | no               |
| 1c    |  10 | boost_high |    0.016 |      25.7 |     153 | 61%       |          0.006 |            23.2 | no               |
| 1d    |   5 | skip_low   |    0.028 |     -20.7 |    -196 | 44%       |         -0.008 |            -2.3 | no               |
| 1d    |   5 | half_low   |    0.01  |     -15.3 |     -98 | 44%       |         -0.003 |           -10   | no               |
| 1d    |   5 | boost_high |    0.017 |      25.6 |     175 | 62%       |          0.008 |            32.2 | no               |
| 1d    |  10 | skip_low   |   -0.011 |     -15.8 |    -230 | 43%       |         -0.006 |            14.7 | no               |
| 1d    |  10 | half_low   |   -0.004 |     -14   |    -115 | 43%       |         -0.002 |            -6.3 | no               |
| 1d    |  10 | boost_high |    0.02  |      22.6 |     176 | 65%       |          0.014 |            21.2 | no               |
| 1e    |   5 | skip_low   |   -0.126 |      66.2 |    -415 | 33%       |          0.011 |           -16   | no               |
| 1e    |   5 | half_low   |   -0.044 |      -8.6 |    -208 | 33%       |          0.005 |           -18.6 | no               |
| 1e    |   5 | boost_high |   -0.012 |      29.4 |      93 | 55%       |          0.001 |            24.6 | no               |
| 1e    |  10 | skip_low   |    0.001 |     -20.1 |    -234 | 41%       |          0.011 |            -3.5 | no               |
| 1e    |  10 | half_low   |    0     |     -22.4 |    -117 | 41%       |          0.004 |           -13   | no               |
| 1e    |  10 | boost_high |   -0.011 |      23.3 |      93 | 52%       |          0.009 |            26.2 | no               |
| 5a    |   5 | skip_low   |   -0.043 |      14.4 |    -318 | 42%       |         -0.039 |            17   | no               |
| 5a    |   5 | half_low   |   -0.015 |     -10.4 |    -159 | 42%       |         -0.014 |           -10.4 | no               |
| 5a    |   5 | boost_high |   -0.009 |      33   |     111 | 58%       |         -0.003 |            29.6 | no               |
| 5a    |  10 | skip_low   |   -0.002 |      19.1 |    -242 | 43%       |         -0.049 |             1.4 | no               |
| 5a    |  10 | half_low   |   -0.001 |      -3.1 |    -121 | 43%       |         -0.018 |           -13.6 | no               |
| 5a    |  10 | boost_high |   -0.016 |      34.4 |      77 | 51%       |         -0.003 |            27.4 | no               |
| 5b    |   5 | skip_low   |    0.167 |     -12   |     -19 | 56%       |          0.023 |           -16.2 | no               |
| 5b    |   5 | half_low   |    0.062 |     -10.8 |      -9 | 56%       |          0.009 |           -15.9 | no               |
| 5b    |   5 | boost_high |    0.039 |      27.9 |     245 | 68%       |         -0.003 |            27.5 | no               |
| 5b    |  10 | skip_low   |    0.145 |     -26   |      -5 | 53%       |         -0.015 |           -10.6 | yes              |
| 5b    |  10 | half_low   |    0.057 |     -21.7 |      -2 | 53%       |         -0.006 |           -14.4 | yes              |
| 5b    |  10 | boost_high |    0.026 |      22.6 |     193 | 68%       |          0.003 |            23.2 | no               |
| NONS  |   5 | skip_low   |   -0.043 |       0.3 |    -322 | 37%       |          0.046 |           -17.9 | no               |
| NONS  |   5 | half_low   |   -0.015 |     -15.1 |    -161 | 37%       |          0.016 |           -23.6 | no               |
| NONS  |   5 | boost_high |   -0.011 |      24.9 |     104 | 57%       |          0.012 |            19.4 | no               |
| NONS  |  10 | skip_low   |   -0.032 |      -2.4 |    -250 | 36%       |          0.04  |           -11.2 | no               |
| NONS  |  10 | half_low   |   -0.012 |     -11.6 |    -125 | 36%       |          0.015 |           -16.6 | no               |
| NONS  |  10 | boost_high |   -0.003 |      20.2 |     114 | 59%       |          0.003 |            21.6 | no               |
| RAND  |   5 | skip_low   |    0.103 |     -24.9 |    -165 | 44%       |         -0.009 |           -14.7 | yes              |
| RAND  |   5 | half_low   |    0.035 |     -20.4 |     -82 | 44%       |         -0.003 |           -20.2 | no               |
| RAND  |   5 | boost_high |    0.015 |      28.9 |     166 | 64%       |         -0.004 |            26.7 | no               |
| RAND  |  10 | skip_low   |    0.003 |      22.4 |    -243 | 35%       |         -0.001 |            -9.9 | no               |
| RAND  |  10 | half_low   |    0.001 |      -7.2 |    -122 | 35%       |         -0     |           -16.9 | no               |
| RAND  |  10 | boost_high |    0.013 |      19.7 |     161 | 67%       |          0.001 |            23.2 | no               |
| PLANT |   5 | skip_low   |    0.9   |     -74.4 |     781 | 92%       |          0.007 |           377.6 | yes              |
| PLANT |   5 | half_low   |    0.314 |     -51.5 |     390 | 92%       |          0.001 |            20.8 | yes              |
| PLANT |   5 | boost_high |    0.206 |     -15.7 |     666 | 92%       |          0.006 |            44.4 | yes              |
| PLANT |  10 | skip_low   |    0.837 |     -71.3 |     729 | 90%       |          0.008 |           364.8 | yes              |
| PLANT |  10 | half_low   |    0.295 |     -48.1 |     364 | 90%       |          0.002 |            23.5 | yes              |
| PLANT |  10 | boost_high |    0.21  |     -13.9 |     668 | 91%       |          0.004 |            54.9 | yes              |

Vote in thirds on the next 2 weeks (K=5; thirds cut at the pick-window terciles of the vote; real labels vs the shifted-label procedure):
| set   | labels   | low: share, meanR   | mid: share, meanR   | high: share, meanR   |   high-low meanR |
|:------|:---------|:--------------------|:--------------------|:---------------------|-----------------:|
| ALL   | real     | 39%, +0.334         | 10%, +0.071         | 51%, +0.261          |           -0.073 |
| ALL   | shift11  | 46%, +0.268         | 8%, +0.604          | 46%, +0.218          |           -0.05  |
| ALL   | shift23  | 52%, +0.292         | 5%, +0.173          | 43%, +0.254          |           -0.038 |
| ALL   | shift37  | 45%, +0.441         | 8%, +0.088          | 47%, +0.139          |           -0.302 |
| 1     | real     | 43%, +0.330         | 9%, -0.032          | 48%, +0.272          |           -0.058 |
| 1     | shift11  | 45%, +0.314         | 6%, +0.365          | 48%, +0.217          |           -0.096 |
| 1     | shift23  | 49%, +0.263         | 7%, +0.075          | 44%, +0.308          |            0.045 |
| 1     | shift37  | 48%, +0.357         | 5%, -0.128          | 47%, +0.226          |           -0.131 |
| 3     | real     | 38%, +0.240         | 23%, +0.496         | 39%, +0.249          |            0.009 |
| 3     | shift11  | 36%, +0.376         | 22%, +0.294         | 43%, +0.250          |           -0.125 |
| 3     | shift23  | 33%, +0.235         | 25%, +0.624         | 42%, +0.227          |           -0.007 |
| 3     | shift37  | 41%, +0.426         | 13%, +0.562         | 47%, +0.120          |           -0.306 |
| 5     | real     | 41%, +0.107         | 11%, +0.174         | 48%, +0.433          |            0.325 |
| 5     | shift11  | 44%, +0.212         | 11%, +0.357         | 45%, +0.306          |            0.094 |
| 5     | shift23  | 38%, +0.240         | 14%, +0.502         | 48%, +0.226          |           -0.014 |
| 5     | shift37  | 40%, +0.293         | 10%, +0.423         | 50%, +0.221          |           -0.072 |
| 7     | real     | 50%, +0.512         | 6%, +0.353          | 44%, +0.067          |           -0.445 |
| 7     | shift11  | 52%, +0.339         | 15%, +0.504         | 33%, +0.164          |           -0.175 |
| 7     | shift23  | 41%, +0.394         | 7%, +0.438          | 51%, +0.216          |           -0.179 |
| 7     | shift37  | 45%, +0.481         | 11%, -0.060         | 44%, +0.218          |           -0.263 |
| 10    | real     | 47%, +0.229         | 12%, +0.263         | 41%, +0.319          |            0.09  |
| 10    | shift11  | 42%, +0.240         | 13%, +0.556         | 45%, +0.213          |           -0.028 |
| 10    | shift23  | 38%, +0.299         | 14%, +0.464         | 48%, +0.190          |           -0.109 |
| 10    | shift37  | 41%, +0.299         | 14%, +0.379         | 45%, +0.210          |           -0.089 |

## HONEST WAIT-THEN-ENTER / EARLY-EXIT versions of the delayed flow columns (rolling rule; 1,241 delayed columns x yes/no x {wait-then-enter, early exit}; N picks equal-split)
Wait-then-enter: wait D = 5/30/60/120 s, enter at +D only when the column is at its picked state, same stop/target distances from the new entry, trades already closed inside the wait are not entered. Early exit: entered at the signal, exit at the mark at +D when the column is at its picked state. dMeanR is per trade actually taken (wait rules take fewer trades: see the shift nulls, which have the same exposure drop).
| picks on   | gate   |   N |   dMeanR |   dUlcer% |   d$/wk | persist   |   shift dMeanR |   shift dUlcer% |   random-flag dMeanR |   random-flag dUlcer% | beats random dU/dm   |
|:-----------|:-------|----:|---------:|----------:|--------:|:----------|---------------:|----------------:|---------------------:|----------------------:|:---------------------|
| 6M         | g15    |   1 |   -0.014 |      -7.5 |   -3469 | 39%       |         -0.006 |           -42.8 |               -0.004 |                 -38.1 | 20%/30%              |
| 6M         | g15    |   3 |   -0.023 |     -35.8 |   -3351 | 39%       |         -0.011 |           -58.7 |               -0.009 |                 -66   | 0%/10%               |
| 6M         | g15    |   5 |   -0.014 |     -56.9 |   -3197 | 40%       |         -0.016 |           -65.7 |               -0.012 |                 -70.8 | 0%/60%               |
| 6M         | g15    |  10 |    0.001 |     -66.4 |   -2953 | 39%       |         -0.008 |           -69.2 |               -0.012 |                 -73.9 | 0%/100%              |
| 6M         | g30    |   1 |   -0.022 |     -10   |   -3487 | 38%       |         -0.01  |           -38.2 |                      |                       |                      |
| 6M         | g30    |   3 |   -0.032 |     -17.8 |   -3485 | 39%       |         -0.013 |           -60.2 |                      |                       |                      |
| 6M         | g30    |   5 |   -0.016 |     -53.2 |   -3219 | 39%       |         -0.019 |           -63.4 |                      |                       |                      |
| 6M         | g30    |  10 |   -0.002 |     -64.7 |   -2977 | 39%       |         -0.009 |           -69.1 |                      |                       |                      |
| 3M         | g15    |   1 |   -0.054 |     -27.4 |   -3052 | 39%       |         -0.014 |           -31.3 |                      |                       |                      |
| 3M         | g15    |   3 |   -0.021 |     -54.9 |   -2629 | 44%       |         -0.02  |           -51.3 |                      |                       |                      |
| 3M         | g15    |   5 |   -0.015 |     -65.8 |   -2513 | 42%       |         -0.02  |           -58.6 |                      |                       |                      |
| 3M         | g15    |  10 |   -0.006 |     -77.4 |   -2406 | 43%       |         -0.016 |           -67.8 |                      |                       |                      |
| 3M         | g30    |   1 |   -0.03  |     -46.7 |   -2741 | 40%       |         -0.013 |           -38.7 |                      |                       |                      |
| 3M         | g30    |   3 |   -0.01  |     -62   |   -2474 | 44%       |         -0.026 |           -49.4 |                      |                       |                      |
| 3M         | g30    |   5 |    0     |     -77.3 |   -2332 | 42%       |         -0.021 |           -58   |                      |                       |                      |
| 3M         | g30    |  10 |    0.003 |     -78.3 |   -2270 | 42%       |         -0.012 |           -69.6 |                      |                       |                      |

Current wait / early-exit picks (g15, top 3 per cell):


## CURRENT PICKS (refit ending 2026-10-30; pick window trailing 6M 2026-05-01..2026-10-30, trailing 3M 2026-08-01..; data end 2026-10-30)
Each row: the rule in plain words, its effect on the pick window (6M and 3M: dMeanR in R, dUlcer% vs doing nothing), the share of trades it acts on, the prior-year check (GREEN <=15%, AMBER 15-30%, RED >30% worse than doing nothing on ulcer / mean in the worst prior 365-day block), feed needs, whether D7 can compute it live. ALL families pooled, gate 15% (strict) and 30%. Where the 6M and 3M numbers disagree in sign the pick is fragile.

Best single pick per family and cell (gate 15%): 
(none)

Score today: the family score is the equal-weight vote of the five picks above (+1 favourable state, -1 unfavourable, 0 unknown); D7 computes it live only if every pick in its list is computable live (last column); a cell whose top 5 are all L3 / UW / other-market columns cannot be run today.

## Reading, caveats and what goes to stage 2
- A pick procedure that "wins" by trading less is exposed by the random-skip draws (same share, same action) and by the shifted-label procedure; only the excess over them counts. Families whose rolling OOS beats the nulls go forward to stage 2 as one score per book, jointly with the bar swap, bracket picks and stack rules, then the exact engine with controls (not in this page).
- Family 1 holds 83% of the 63,626 columns (alt-bar copies of the same indicators): its selection pressure is the highest, so the shifted-label null for family 1 is the one to read; sub-families 1a-1h are shown separately.
- UW levels as exits, the bracket table, the bar swap, new books and behaviour rules (ordered 18:10Z / 18:13Z) are other agents' tables: this page covers the entry conditions, scores and the honest wait / early-exit versions. Level sets: own zones and session/round-number levels are in family 3 (68 at-entry columns); UW levels and own-book walls are in 7 / 5b where the stage-1 store has them.
- No engine cells were added. Scripts: code/th_s1r/ (s1r_assemble.py, s1r_core.py, s1r_eval.py, s1r_wait.py, s1r_weval.py, s1r_page.py); intermediates /mnt/l2/l2vast/_s1r/.
