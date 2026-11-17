# DS3_REBUILD_S1R - Stage 1R: every entry condition re-scored by the user's rolling rule on the RAW books (W-S1R)

1. WHICH WORK under the user's rule (recent-data picks, refit every 2 weeks, OOS chained, label needs excess over the shifted-label / random-skip / nonsense nulls): none. WEAK-BUT-POSITIVE (positive OOS but not clearly past the nulls): 4, 8, 1g.
2. WHICH DO NOT: 1, 2, 3, 5, 6, 7, 9, 10, 1a, 1b, 1c, 1d, 1e, 1f, 1h, 5a, 5b, ALL (BEST-AVAILABLE-NOT-PROVEN: the rolling picks do not beat what the same procedure earns on shifted labels / random skips). Control columns (nonsense / random / planted) under the same procedure: NONS=BEST-AVAILABLE-NOT-PROVEN, RAND=BEST-AVAILABLE-NOT-PROVEN, PLANT=CONFIRMED.
3. ALL families pooled, top-5 picks, trailing 6M, 15% prior-year gate, next 2 weeks chained over 15 book x session cells: BEST-AVAILABLE-NOT-PROVEN; OOS dMeanR -0.001 R, dUlcer -23.6%, persistence 48% (bar 60%) vs shifted-label nulls 0.000 R / -16.9% (see the first table for the sub-families).
4. TODAY'S PICKS (refit ending 2026-10-30, pick window 2026-05-01..2026-10-30 / 3M 2026-08-01..): per book x session in the "Current picks" section below (top 5 and the best pick per family, with 6M and 3M effect, prior-year 15/30 flags, feed need and whether D7 can compute it live); CSVs /mnt/l2/l2vast/_s1r/eval/picks_now_all.csv and picks_now_family.csv.
5. DATA END 2026-10-30 (engine store ends there; November 2026 is not in the raw engine base so it could not be extended); cells done 15/15 as of 2026-11-17 21:57 UTC; first table 00:20Z, full set 06:20Z; wait-then-enter / early-exit and the score votes are in their own sections. Label scale: CONFIRMED / LEAD / WEAK-BUT-POSITIVE / BEST-AVAILABLE-NOT-PROVEN (rules below).

> VALIDATION (FIRST PASS, written 2026-11-17 21:57 UTC): rule = the user's standing selection rule (autopilot/DIRECTIVE_SELECTION_RULE_20261117.md, STAGE1R order 18:17Z): pick on the TRAILING 6 months (3 months shown beside), refit every 14 days from 2023-10-02 to 2026-10-31, prior-years check = not-a-disaster at 15%/30%, validated by walking the procedure forward (OOS pieces chained), NOT a frozen holdout. Trials counted: 63626 candidate columns x 2 sides x 3 actions per cell and refit (65,192 columns in the stage-1 store; 63,626 at-entry-clean + 299 controls scored here) x 15 cells x 79 refits x 2 windows x 4 label versions; correction = nulls (shifted labels 11/23/37 days, nonsense/random/planted columns, 10 random persistent skips with the same share and action), plus the label rules below; no White RC/SPA/DSR/PBO is computed (a rolling pick procedure is evaluated by its OOS excess over nulls instead); NOT engine-exact (raw-chassis trade P&L at base lots, $4.84 RT), no re-entry or freed-book effects; the engine-exact stage-2 run comes later via the lead. Data end 2026-10-30; pick-window end 2026-10-30; refit date 2026-10-31.

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
| 1     | F1 confluence library (all)                                                | BEST-AVAILABLE-NOT-PROVEN |       -0.001 |         -22.4 | 163196/221578         |   -4054 | 73%        | 48%       |               0     |                -19.1 | no                   | 80%/10%                           |           2 | no                 |
| 2     | candle counting, ICT 7-13-21, IRL/ERL                                      | BEST-AVAILABLE-NOT-PROVEN |       -0.002 |          -6.2 | 211774/221578         |   -2934 | 79%        | 48%       |               0.001 |                -19.3 | no                   | 30%/40%                           |           2 | no                 |
| 3     | levels and zones (own zones, session/round levels)                         | BEST-AVAILABLE-NOT-PROVEN |       -0.001 |          -0.1 | 220331/221578         |   -1275 | 93%        | 47%       |              -0.002 |                 -5.7 | no                   | 30%/0%                            |           1 | no                 |
| 4     | range forecasts (HAR / options / UW / own bar)                             | WEAK-BUT-POSITIVE         |        0.003 |         -11   | 210105/221578         |   -1157 | 84%        | 51%       |               0     |                 -9.5 | no                   | 20%/90%                           |           2 | yes                |
| 5     | F5 order flow (all)                                                        | BEST-AVAILABLE-NOT-PROVEN |        0.004 |         -13.6 | 208440/221578         |   -3642 | 74%        | 50%       |               0     |                -26.2 | no                   | 10%/100%                          |           3 | yes                |
| 6     | other markets and breadth                                                  | BEST-AVAILABLE-NOT-PROVEN |       -0.001 |         -22.3 | 191372/221578         |   -3469 | 75%        | 50%       |               0     |                -30.8 | no                   | 70%/20%                           |           1 | yes                |
| 7     | Unusual Whales options / positioning                                       | BEST-AVAILABLE-NOT-PROVEN |        0.002 |         -17.3 | 206748/221578         |   -1370 | 85%        | 52%       |               0.003 |                -16.4 | no                   | 80%/90%                           |           2 | yes                |
| 8     | day / regime / time of day / calendar                                      | WEAK-BUT-POSITIVE         |        0     |         -18.7 | 182004/221578         |   -2095 | 81%        | 50%       |               0     |                -13.6 | no                   | 100%/70%                          |           2 | yes                |
| 9     | causal trade context (raw)                                                 | BEST-AVAILABLE-NOT-PROVEN |        0.002 |         -12.6 | 206794/221578         |   -1435 | 86%        | 50%       |               0.001 |                -12.7 | no                   | 100%/100%                         |           3 | yes                |
| 10    | TICK internals                                                             | BEST-AVAILABLE-NOT-PROVEN |       -0.002 |          -1.8 | 212222/221578         |    -936 | 92%        | 49%       |               0.001 |                 -7   | no                   | 40%/0%                            |           1 | no                 |
| 1a    | confluence: named indicators / session anchors                             | BEST-AVAILABLE-NOT-PROVEN |        0.001 |         -12.1 | 186843/221578         |   -4514 | 72%        | 51%       |              -0.002 |                -22.7 | no                   | 0%/20%                            |           2 | yes                |
| 1b    | confluence: entry-table universe                                           | BEST-AVAILABLE-NOT-PROVEN |       -0.001 |         -26.6 | 162961/221578         |   -3734 | 72%        | 49%       |               0     |                -19.4 | no                   | 90%/40%                           |           2 | no                 |
| 1c    | confluence: oscillators                                                    | BEST-AVAILABLE-NOT-PROVEN |       -0     |         -21.9 | 178297/221578         |   -3619 | 72%        | 52%       |              -0.001 |                -25.1 | no                   | 70%/70%                           |           2 | yes                |
| 1d    | confluence: trend                                                          | BEST-AVAILABLE-NOT-PROVEN |        0     |         -19.8 | 168102/221578         |   -4383 | 72%        | 50%       |               0     |                -19.7 | no                   | 60%/50%                           |           2 | yes                |
| 1e    | confluence: SMC / ICT structure                                            | BEST-AVAILABLE-NOT-PROVEN |        0     |          -7.9 | 237921/221578         |   -4110 | 76%        | 50%       |               0.001 |                -18.6 | no                   | 10%/80%                           |           1 | no                 |
| 1f    | confluence: vol / squeeze / state / ML                                     | BEST-AVAILABLE-NOT-PROVEN |       -0.002 |         -20.8 | 172324/221578         |   -3936 | 76%        | 50%       |              -0.001 |                -15.4 | no                   | 70%/40%                           |           1 | no                 |
| 1g    | confluence: alternate-bar indicators (HA, range, renko, tick, volume bars) | WEAK-BUT-POSITIVE         |        0     |         -31.5 | 149515/221578         |   -3528 | 72%        | 49%       |               0     |                -21.2 | no                   | 90%/50%                           |           2 | no                 |
| 1h    | confluence: alt-bar agreement                                              | BEST-AVAILABLE-NOT-PROVEN |       -0.004 |          -7.7 | 202734/221578         |   -4245 | 75%        | 49%       |              -0.001 |                -18.4 | no                   | 0%/30%                            |           1 | yes                |
| 5a    | order flow: tape prints and speed                                          | BEST-AVAILABLE-NOT-PROVEN |       -0.001 |          -8.2 | 211824/221578         |   -3863 | 77%        | 49%       |               0.001 |                -23.1 | no                   | 10%/20%                           |           2 | yes                |
| 5b    | order flow: L3 / L2 book / flow library                                    | BEST-AVAILABLE-NOT-PROVEN |        0.004 |         -19.9 | 180329/221578         |   -3931 | 74%        | 50%       |               0.001 |                -25.8 | no                   | 50%/100%                          |           3 | yes                |
| ALL   | ALL families pooled                                                        | BEST-AVAILABLE-NOT-PROVEN |       -0.001 |         -23.6 | 166794/221578         |   -4066 | 74%        | 48%       |               0     |                -16.9 | no                   | 90%/20%                           |           1 | no                 |
| NONS  | CONTROL nonsense columns (200)                                             | BEST-AVAILABLE-NOT-PROVEN |        0     |         -31.7 | 163057/221578         |   -6051 | 62%        | 50%       |               0.001 |                -34.4 | no                   | 90%/30%                           |           2 | yes                |
| RAND  | CONTROL persistent random columns (90)                                     | BEST-AVAILABLE-NOT-PROVEN |        0.001 |         -23   | 184697/221578         |   -3458 | 74%        | 51%       |               0     |                -29.2 | no                   | 90%/90%                           |           3 | no                 |
| PLANT | CONTROL planted-edge columns (9)                                           | CONFIRMED                 |        0.048 |         -39.4 | 182066/221578         |   22528 | 112%       | 92%       |              -0.057 |                573.8 | yes                  | 100%/100%                         |           3 | yes                |

Same, trailing 3M picks:
| set   | what                                                                       | label                     |   OOS dMeanR |   OOS dUlcer% | dMaxDD$ (rule/base)   |   d$/wk | exposure   | persist   |   shift-null dMeanR |   shift-null dUlcer% | beats all 3 shifts   | beats random-skip draws (dU/dm)   |   thirds ok | 3M-window agrees   |
|:------|:---------------------------------------------------------------------------|:--------------------------|-------------:|--------------:|:----------------------|--------:|:-----------|:----------|--------------------:|---------------------:|:---------------------|:----------------------------------|------------:|:-------------------|
| 1     | F1 confluence library (all)                                                | BEST-AVAILABLE-NOT-PROVEN |       -0.001 |         -27.1 | 171192/225455         |   -3572 | 74%        | 49%       |              -0     |                -12.9 | no                   | /                                 |           1 | no                 |
| 2     | candle counting, ICT 7-13-21, IRL/ERL                                      | BEST-AVAILABLE-NOT-PROVEN |       -0.003 |         -16.9 | 202107/225455         |   -3551 | 79%        | 49%       |               0.001 |                -13.6 | no                   | /                                 |           1 | no                 |
| 3     | levels and zones (own zones, session/round levels)                         | BEST-AVAILABLE-NOT-PROVEN |       -0.003 |           8.5 | 256486/225455         |   -2156 | 92%        | 48%       |              -0.002 |                 -2.4 | no                   | /                                 |           1 | no                 |
| 4     | range forecasts (HAR / options / UW / own bar)                             | WEAK-BUT-POSITIVE         |        0.002 |         -12.2 | 200101/225455         |   -1146 | 82%        | 54%       |              -0.001 |                 -9.3 | no                   | /                                 |           2 | yes                |
| 5     | F5 order flow (all)                                                        | BEST-AVAILABLE-NOT-PROVEN |        0.002 |         -12.7 | 197602/225455         |   -4234 | 74%        | 53%       |               0.002 |                -22.9 | no                   | /                                 |           1 | yes                |
| 6     | other markets and breadth                                                  | BEST-AVAILABLE-NOT-PROVEN |        0.001 |         -24.4 | 177643/225455         |   -3005 | 75%        | 52%       |               0.001 |                -28.9 | no                   | /                                 |           2 | no                 |
| 7     | Unusual Whales options / positioning                                       | BEST-AVAILABLE-NOT-PROVEN |        0.001 |         -14.7 | 208285/225455         |   -2102 | 85%        | 50%       |               0.002 |                -19.1 | no                   | /                                 |           2 | yes                |
| 8     | day / regime / time of day / calendar                                      | WEAK-BUT-POSITIVE         |        0     |         -23   | 174249/225455         |   -2395 | 80%        | 51%       |              -0.001 |                -16.8 | yes                  | /                                 |           2 | yes                |
| 9     | causal trade context (raw)                                                 | WEAK-BUT-POSITIVE         |        0.001 |         -11.4 | 203080/225455         |   -1728 | 85%        | 50%       |              -0.002 |                 -5.3 | yes                  | /                                 |           1 | yes                |
| 10    | TICK internals                                                             | BEST-AVAILABLE-NOT-PROVEN |       -0.001 |          -2.7 | 209390/225455         |    -660 | 92%        | 45%       |               0.001 |                 -6.2 | no                   | /                                 |           1 | no                 |
| 1a    | confluence: named indicators / session anchors                             | BEST-AVAILABLE-NOT-PROVEN |        0.001 |         -23.6 | 192779/225455         |   -3795 | 71%        | 51%       |              -0.001 |                -24.4 | no                   | /                                 |           2 | yes                |
| 1b    | confluence: entry-table universe                                           | BEST-AVAILABLE-NOT-PROVEN |       -0.001 |         -26.4 | 179710/225455         |   -4382 | 73%        | 50%       |               0.002 |                -21.4 | no                   | /                                 |           1 | no                 |
| 1c    | confluence: oscillators                                                    | BEST-AVAILABLE-NOT-PROVEN |        0.001 |         -26.1 | 166425/225455         |   -3719 | 74%        | 48%       |               0.002 |                -28.5 | no                   | /                                 |           3 | no                 |
| 1d    | confluence: trend                                                          | WEAK-BUT-POSITIVE         |        0.001 |         -28.9 | 161695/225455         |   -3446 | 73%        | 50%       |              -0     |                -19   | no                   | /                                 |           2 | yes                |
| 1e    | confluence: SMC / ICT structure                                            | BEST-AVAILABLE-NOT-PROVEN |       -0.003 |         -13.5 | 208641/225455         |   -4474 | 76%        | 48%       |               0.001 |                -22.9 | no                   | /                                 |           0 | yes                |
| 1f    | confluence: vol / squeeze / state / ML                                     | BEST-AVAILABLE-NOT-PROVEN |       -0.001 |         -18.6 | 185849/225455         |   -4207 | 76%        | 49%       |              -0.001 |                -19.2 | no                   | /                                 |           1 | no                 |
| 1g    | confluence: alternate-bar indicators (HA, range, renko, tick, volume bars) | BEST-AVAILABLE-NOT-PROVEN |       -0.001 |         -27.5 | 163148/225455         |   -4114 | 74%        | 49%       |               0     |                -18.8 | no                   | /                                 |           1 | yes                |
| 1h    | confluence: alt-bar agreement                                              | WEAK-BUT-POSITIVE         |        0.001 |         -33.2 | 155562/225455         |   -2608 | 75%        | 51%       |               0     |                -21.4 | no                   | /                                 |           2 | no                 |
| 5a    | order flow: tape prints and speed                                          | BEST-AVAILABLE-NOT-PROVEN |        0     |         -16.6 | 191637/225455         |   -3427 | 76%        | 51%       |              -0     |                -17.7 | no                   | /                                 |           1 | no                 |
| 5b    | order flow: L3 / L2 book / flow library                                    | BEST-AVAILABLE-NOT-PROVEN |        0.002 |         -17   | 186260/225455         |   -4124 | 74%        | 51%       |               0.002 |                -21.3 | no                   | /                                 |           2 | yes                |
| ALL   | ALL families pooled                                                        | BEST-AVAILABLE-NOT-PROVEN |       -0.002 |         -24.9 | 174280/225455         |   -4067 | 75%        | 49%       |              -0     |                -10.2 | no                   | /                                 |           1 | no                 |
| NONS  | CONTROL nonsense columns (200)                                             | BEST-AVAILABLE-NOT-PROVEN |        0.001 |         -30   | 165282/225455         |   -5634 | 62%        | 50%       |               0     |                -34.9 | no                   | /                                 |           2 | yes                |
| RAND  | CONTROL persistent random columns (90)                                     | BEST-AVAILABLE-NOT-PROVEN |       -0.001 |         -19.4 | 190711/225455         |   -3936 | 74%        | 48%       |               0.001 |                -27.3 | no                   | /                                 |           2 | yes                |
| PLANT | CONTROL planted-edge columns (9)                                           | WEAK-BUT-POSITIVE         |        0.046 |         -39.2 | 184575/225455         |   21467 | 111%       | 92%       |              -0.052 |                453.8 | yes                  | /                                 |           3 | yes                |

## By number of picks (N) and prior-year gate (all families pooled and each main family, 6M, next 2 weeks)
| set   | gate   |   N | label                     |   dMeanR |   dUlcer% | persist   |   shift dMeanR |   shift dUlcer% | rnd beaten dU/dm   |
|:------|:-------|----:|:--------------------------|---------:|----------:|:----------|---------------:|----------------:|:-------------------|
| ALL   | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.006 |       0.2 | 49%       |         -0.002 |             3.6 | /                  |
| ALL   | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |      -2.9 | 49%       |         -0.002 |           -15.9 | /                  |
| ALL   | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |      -6.8 | 49%       |          0     |           -15.5 | /                  |
| ALL   | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -11.4 | 48%       |          0     |           -18.7 | /                  |
| ALL   | g15    |   1 | WEAK-BUT-POSITIVE         |    0.008 |     -27.4 | 52%       |         -0.002 |            13.8 | 90%/100%           |
| ALL   | g15    |   3 | WEAK-BUT-POSITIVE         |    0.003 |     -30.7 | 51%       |         -0.001 |           -13.1 | 90%/80%            |
| ALL   | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -23.6 | 48%       |          0     |           -16.9 | 90%/20%            |
| ALL   | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -24.3 | 48%       |         -0     |           -21.2 | 80%/10%            |
| ALL   | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |    0     |      21.1 | 49%       |         -0     |            -1.1 | /                  |
| ALL   | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.001 |     -13.6 | 50%       |          0.001 |           -15.1 | /                  |
| ALL   | g30    |   5 | WEAK-BUT-POSITIVE         |    0.001 |     -14.6 | 48%       |          0.001 |           -13.5 | /                  |
| ALL   | g30    |  10 | WEAK-BUT-POSITIVE         |    0.001 |     -21.8 | 47%       |          0.001 |           -18.9 | /                  |
| 1     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.004 |     -12.9 | 48%       |          0.001 |             3.1 | /                  |
| 1     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0     |     -11.5 | 48%       |          0     |           -12.4 | /                  |
| 1     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |      -9.9 | 51%       |          0.001 |           -16.7 | /                  |
| 1     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -17.1 | 49%       |         -0     |           -19.1 | /                  |
| 1     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0     |     -16.2 | 48%       |         -0.002 |            18.6 | 70%/0%             |
| 1     | g15    |   3 | WEAK-BUT-POSITIVE         |    0.002 |     -27.4 | 49%       |          0     |           -11.5 | 90%/60%            |
| 1     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -22.4 | 48%       |          0     |           -19.1 | 80%/10%            |
| 1     | g15    |  10 | WEAK-BUT-POSITIVE         |    0     |     -27.3 | 48%       |         -0.001 |           -21.5 | 90%/20%            |
| 1     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |      20.2 | 47%       |          0     |             7.5 | /                  |
| 1     | g30    |   3 | WEAK-BUT-POSITIVE         |    0.001 |     -19   | 49%       |          0     |           -10.6 | /                  |
| 1     | g30    |   5 | WEAK-BUT-POSITIVE         |    0.001 |     -19.4 | 48%       |          0     |           -13.8 | /                  |
| 1     | g30    |  10 | WEAK-BUT-POSITIVE         |    0     |     -21   | 48%       |         -0     |           -19.4 | /                  |
| 2     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.011 |      58.5 | 48%       |          0.001 |           -12.7 | /                  |
| 2     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.007 |      17.2 | 48%       |          0     |           -18.5 | /                  |
| 2     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |      -4.7 | 47%       |          0.001 |           -21.6 | /                  |
| 2     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -4.7 | 49%       |          0     |           -19.3 | /                  |
| 2     | g15    |   1 | WEAK-BUT-POSITIVE         |    0.001 |     -11.2 | 50%       |          0     |             7.3 | 90%/80%            |
| 2     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |      -7.1 | 48%       |          0     |           -18.7 | 40%/30%            |
| 2     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -6.2 | 48%       |          0.001 |           -19.3 | 30%/40%            |
| 2     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -6   | 48%       |          0.001 |           -16.8 | 20%/30%            |
| 2     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |      14.5 | 49%       |         -0.001 |             6.2 | /                  |
| 2     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -9   | 48%       |         -0     |           -12.4 | /                  |
| 2     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -2.9 | 50%       |         -0     |           -15.1 | /                  |
| 2     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |      -6.8 | 48%       |         -0     |           -12.5 | /                  |
| 3     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.004 |      21.5 | 48%       |         -0.001 |            -9.5 | /                  |
| 3     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -3.3 | 48%       |         -0.003 |            -6.8 | /                  |
| 3     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -0.8 | 47%       |         -0.002 |            -4.4 | /                  |
| 3     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -0.2 | 47%       |         -0.002 |            -5.4 | /                  |
| 3     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.004 |      17.7 | 46%       |         -0.003 |             0.3 | 10%/0%             |
| 3     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |       2.6 | 47%       |         -0.002 |            -4.6 | 20%/0%             |
| 3     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |      -0.1 | 47%       |         -0.002 |            -5.7 | 30%/0%             |
| 3     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |       0.1 | 46%       |         -0.001 |            -6.3 | 30%/0%             |
| 3     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      14.8 | 48%       |         -0.002 |             2.6 | /                  |
| 3     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |       1.5 | 47%       |         -0.002 |             0.1 | /                  |
| 3     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -1.2 | 47%       |         -0.002 |            -0.2 | /                  |
| 3     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -0.8 | 47%       |         -0.002 |            -0.5 | /                  |
| 4     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |      -4.1 | 47%       |          0.002 |            -7.6 | /                  |
| 4     | g0     |   3 | WEAK-BUT-POSITIVE         |    0.003 |     -10.5 | 49%       |          0.001 |            -6.4 | /                  |
| 4     | g0     |   5 | WEAK-BUT-POSITIVE         |    0.004 |     -15.7 | 50%       |          0.001 |            -7.9 | /                  |
| 4     | g0     |  10 | WEAK-BUT-POSITIVE         |    0.003 |     -17.8 | 51%       |          0.001 |           -11.2 | /                  |
| 4     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.001 |      27.1 | 46%       |          0.002 |           -12   | 0%/30%             |
| 4     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |      -4.7 | 52%       |          0.001 |            -7.4 | 0%/70%             |
| 4     | g15    |   5 | WEAK-BUT-POSITIVE         |    0.003 |     -11   | 51%       |          0     |            -9.5 | 20%/90%            |
| 4     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -10.3 | 52%       |          0.001 |           -10.8 | 50%/90%            |
| 4     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |      20.7 | 46%       |          0.003 |            -8.8 | /                  |
| 4     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |      -2.3 | 51%       |          0.002 |            -4.6 | /                  |
| 4     | g30    |   5 | WEAK-BUT-POSITIVE         |    0.003 |     -10   | 51%       |          0.001 |            -6.7 | /                  |
| 4     | g30    |  10 | WEAK-BUT-POSITIVE         |    0.002 |     -12.8 | 53%       |          0.001 |            -8.4 | /                  |
| 5     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.005 |      16.9 | 50%       |         -0.002 |             8.1 | /                  |
| 5     | g0     |   3 | WEAK-BUT-POSITIVE         |    0.005 |     -23.3 | 52%       |         -0     |           -14.1 | /                  |
| 5     | g0     |   5 | WEAK-BUT-POSITIVE         |    0.005 |     -25.8 | 53%       |         -0     |           -22.9 | /                  |
| 5     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.003 |     -26.2 | 50%       |          0     |           -31.8 | /                  |
| 5     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0     |       1   | 51%       |          0.003 |            -3.1 | 20%/40%            |
| 5     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.004 |     -10.1 | 51%       |          0.001 |           -26   | 20%/90%            |
| 5     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.004 |     -13.6 | 50%       |          0     |           -26.2 | 10%/100%           |
| 5     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -16.3 | 49%       |          0.001 |           -25.1 | 10%/100%           |
| 5     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |      -7.4 | 50%       |          0     |            -7.6 | /                  |
| 5     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.005 |     -21.4 | 52%       |         -0     |           -27.7 | /                  |
| 5     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.004 |     -17.3 | 51%       |         -0     |           -30.3 | /                  |
| 5     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -16.4 | 50%       |          0     |           -24.2 | /                  |
| 6     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.007 |      30   | 45%       |          0.001 |            -9.1 | /                  |
| 6     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |       8.6 | 49%       |          0.002 |           -32.9 | /                  |
| 6     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |     -14.1 | 48%       |          0.003 |           -34.3 | /                  |
| 6     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -24.7 | 48%       |          0.002 |           -32.4 | /                  |
| 6     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.007 |      15.6 | 46%       |         -0.002 |            -8.4 | 0%/0%              |
| 6     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -24.9 | 51%       |          0.002 |           -30.7 | 80%/60%            |
| 6     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -22.3 | 50%       |          0     |           -30.8 | 70%/20%            |
| 6     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0     |     -22.5 | 49%       |          0.001 |           -28.6 | 60%/40%            |
| 6     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.008 |      29.7 | 44%       |          0     |            -6   | /                  |
| 6     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -8.7 | 50%       |          0     |           -26.5 | /                  |
| 6     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0     |     -21.8 | 51%       |          0.001 |           -27.7 | /                  |
| 6     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -19.9 | 49%       |          0.001 |           -29.7 | /                  |
| 7     | g0     |   1 | WEAK-BUT-POSITIVE         |    0.005 |     -19.5 | 51%       |          0.004 |            -2.5 | /                  |
| 7     | g0     |   3 | WEAK-BUT-POSITIVE         |    0.004 |     -24   | 54%       |          0.004 |           -14.2 | /                  |
| 7     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.003 |     -22.1 | 54%       |          0.003 |           -12.1 | /                  |
| 7     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -20.6 | 53%       |          0.003 |           -16.8 | /                  |
| 7     | g15    |   1 | WEAK-BUT-POSITIVE         |    0.005 |     -19.9 | 52%       |          0.004 |           -11.4 | 80%/90%            |
| 7     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.003 |     -21.1 | 53%       |          0.003 |           -15.4 | 90%/100%           |
| 7     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -17.3 | 52%       |          0.003 |           -16.4 | 80%/90%            |
| 7     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.001 |     -18.1 | 51%       |          0.002 |           -17.4 | 100%/100%          |
| 7     | g30    |   1 | WEAK-BUT-POSITIVE         |    0.004 |     -15.2 | 51%       |          0.003 |            -0.6 | /                  |
| 7     | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.003 |     -21.8 | 53%       |          0.003 |           -13.7 | /                  |
| 7     | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -17.8 | 52%       |          0.003 |           -14.9 | /                  |
| 7     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -19.5 | 51%       |          0.003 |           -16.9 | /                  |
| 8     | g0     |   1 | WEAK-BUT-POSITIVE         |    0.002 |     -10.8 | 46%       |         -0.001 |             0.1 | /                  |
| 8     | g0     |   3 | WEAK-BUT-POSITIVE         |    0.003 |     -13   | 50%       |         -0.001 |           -10.3 | /                  |
| 8     | g0     |   5 | WEAK-BUT-POSITIVE         |    0.003 |     -23.6 | 51%       |         -0.001 |           -12.9 | /                  |
| 8     | g0     |  10 | WEAK-BUT-POSITIVE         |    0.001 |     -19.4 | 50%       |          0     |           -16.3 | /                  |
| 8     | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.004 |      10.7 | 45%       |         -0.001 |            -7.1 | 20%/10%            |
| 8     | g15    |   3 | WEAK-BUT-POSITIVE         |    0.002 |     -20.5 | 50%       |         -0     |           -14   | 90%/100%           |
| 8     | g15    |   5 | WEAK-BUT-POSITIVE         |    0     |     -18.7 | 50%       |          0     |           -13.6 | 100%/70%           |
| 8     | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -13.8 | 50%       |         -0     |           -15.4 | 70%/30%            |
| 8     | g30    |   1 | WEAK-BUT-POSITIVE         |    0.002 |      -0.3 | 45%       |         -0     |             2.4 | /                  |
| 8     | g30    |   3 | WEAK-BUT-POSITIVE         |    0.003 |     -16.7 | 50%       |          0     |           -13.9 | /                  |
| 8     | g30    |   5 | WEAK-BUT-POSITIVE         |    0.003 |     -19.3 | 49%       |          0.001 |           -16.9 | /                  |
| 8     | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |    0     |     -17   | 51%       |          0     |           -16.5 | /                  |
| 9     | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.001 |     -10   | 51%       |          0.004 |             5.2 | /                  |
| 9     | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -12.9 | 51%       |          0.004 |           -16.5 | /                  |
| 9     | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -13.1 | 49%       |          0.003 |           -18.2 | /                  |
| 9     | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -15.1 | 49%       |          0.002 |           -16.3 | /                  |
| 9     | g15    |   1 | WEAK-BUT-POSITIVE         |    0.006 |      -3.3 | 52%       |          0.001 |            -2.6 | 70%/100%           |
| 9     | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -10.4 | 50%       |          0.001 |           -11.1 | 80%/100%           |
| 9     | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -12.6 | 50%       |          0.001 |           -12.7 | 100%/100%          |
| 9     | g15    |  10 | WEAK-BUT-POSITIVE         |    0.003 |     -14.6 | 49%       |          0     |           -12.9 | 100%/100%          |
| 9     | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |    0.004 |      -5   | 53%       |          0.003 |            -6.1 | /                  |
| 9     | g30    |   3 | WEAK-BUT-POSITIVE         |    0.003 |     -16.2 | 50%       |          0.002 |           -15.4 | /                  |
| 9     | g30    |   5 | WEAK-BUT-POSITIVE         |    0.002 |     -15.4 | 49%       |          0.001 |           -15   | /                  |
| 9     | g30    |  10 | WEAK-BUT-POSITIVE         |    0.002 |     -17.4 | 49%       |          0.001 |           -14.9 | /                  |
| 10    | g0     |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0     |       2.3 | 49%       |         -0.001 |            -2.3 | /                  |
| 10    | g0     |   3 | BEST-AVAILABLE-NOT-PROVEN |    0     |      -2.6 | 49%       |         -0     |            -7.1 | /                  |
| 10    | g0     |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0     |      -2.6 | 53%       |         -0     |            -7.3 | /                  |
| 10    | g0     |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |      -3.1 | 47%       |          0.001 |            -7.1 | /                  |
| 10    | g15    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |       0.6 | 48%       |          0.001 |            -5.3 | 20%/10%            |
| 10    | g15    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |      -0.9 | 48%       |          0.002 |            -7.5 | 30%/20%            |
| 10    | g15    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -1.8 | 49%       |          0.001 |            -7   | 40%/0%             |
| 10    | g15    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |      -2.4 | 48%       |          0.001 |            -6.3 | 70%/10%            |
| 10    | g30    |   1 | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |       1.6 | 49%       |         -0.001 |            -5.6 | /                  |
| 10    | g30    |   3 | BEST-AVAILABLE-NOT-PROVEN |   -0     |      -1.4 | 50%       |          0.001 |            -7.4 | /                  |
| 10    | g30    |   5 | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |      -2.3 | 47%       |          0.001 |            -7.6 | /                  |
| 10    | g30    |  10 | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -1.5 | 45%       |          0     |            -6.9 | /                  |

## By horizon (picks traded the next 2 weeks / 1 month / 3 months; ALL pooled and main families; N=5, 6M, g15)
| set   | horizon   | label                     |   dMeanR |   dUlcer% | persist   |   shift dMeanR |   shift dUlcer% |
|:------|:----------|:--------------------------|---------:|----------:|:----------|---------------:|----------------:|
| ALL   | 2W        | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -23.6 | 48%       |          0     |           -16.9 |
| ALL   | 1M        | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |     -19.6 | 48%       |          0     |           -15   |
| ALL   | 3M        | BEST-AVAILABLE-NOT-PROVEN |   -0     |     -24.1 | 47%       |         -0.002 |           -13.7 |
| 1     | 2W        | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -22.4 | 48%       |          0     |           -19.1 |
| 1     | 1M        | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |     -15   | 48%       |          0.001 |           -16.9 |
| 1     | 3M        | WEAK-BUT-POSITIVE         |    0.001 |     -19.9 | 46%       |         -0.001 |           -17.5 |
| 2     | 2W        | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -6.2 | 48%       |          0.001 |           -19.3 |
| 2     | 1M        | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |      -6.9 | 52%       |          0.001 |           -14.5 |
| 2     | 3M        | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -12.6 | 48%       |         -0     |           -15.8 |
| 3     | 2W        | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |      -0.1 | 47%       |         -0.002 |            -5.7 |
| 3     | 1M        | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |      -1.7 | 49%       |         -0.002 |            -6.1 |
| 3     | 3M        | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -4.5 | 48%       |         -0.002 |            -4.1 |
| 4     | 2W        | WEAK-BUT-POSITIVE         |    0.003 |     -11   | 51%       |          0     |            -9.5 |
| 4     | 1M        | WEAK-BUT-POSITIVE         |    0.006 |     -12.6 | 56%       |          0     |            -8.4 |
| 4     | 3M        | BEST-AVAILABLE-NOT-PROVEN |    0.004 |     -10.9 | 54%       |          0     |           -13.2 |
| 5     | 2W        | BEST-AVAILABLE-NOT-PROVEN |    0.004 |     -13.6 | 50%       |          0     |           -26.2 |
| 5     | 1M        | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -14.2 | 51%       |         -0     |           -26   |
| 5     | 3M        | BEST-AVAILABLE-NOT-PROVEN |    0     |     -16.5 | 51%       |          0.001 |           -29.1 |
| 6     | 2W        | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -22.3 | 50%       |          0     |           -30.8 |
| 6     | 1M        | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -17.1 | 48%       |         -0     |           -24.6 |
| 6     | 3M        | BEST-AVAILABLE-NOT-PROVEN |   -0.003 |     -18   | 49%       |          0.001 |           -24.7 |
| 7     | 2W        | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -17.3 | 52%       |          0.003 |           -16.4 |
| 7     | 1M        | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -19.8 | 55%       |          0.003 |           -15.5 |
| 7     | 3M        | BEST-AVAILABLE-NOT-PROVEN |    0     |     -12.6 | 53%       |          0.002 |            -8.3 |
| 8     | 2W        | WEAK-BUT-POSITIVE         |    0     |     -18.7 | 50%       |          0     |           -13.6 |
| 8     | 1M        | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |     -17.1 | 52%       |         -0     |           -11.5 |
| 8     | 3M        | WEAK-BUT-POSITIVE         |    0     |     -16.1 | 51%       |         -0.001 |            -7.3 |
| 9     | 2W        | BEST-AVAILABLE-NOT-PROVEN |    0.002 |     -12.6 | 50%       |          0.001 |           -12.7 |
| 9     | 1M        | WEAK-BUT-POSITIVE         |    0.003 |     -13.1 | 52%       |          0     |           -10.6 |
| 9     | 3M        | WEAK-BUT-POSITIVE         |    0.005 |     -16.9 | 53%       |          0     |           -10.6 |
| 10    | 2W        | BEST-AVAILABLE-NOT-PROVEN |   -0.002 |      -1.8 | 49%       |          0.001 |            -7   |
| 10    | 1M        | BEST-AVAILABLE-NOT-PROVEN |   -0.001 |      -5   | 48%       |          0.001 |            -6.1 |
| 10    | 3M        | BEST-AVAILABLE-NOT-PROVEN |    0     |      -3.3 | 51%       |          0.001 |            -4.9 |

## By windows (chained OOS pieces whose refit falls in the window; N=5, 6M picks, g15; real vs mean of shifted-label nulls)
| set   | window   |   n trades |   dMeanR |   dUlcer% | maxDD rule/base $   |   d$/wk (base lots, $4.84) | persist   |   shift-null dMeanR |   shift-null dUlcer% |
|:------|:---------|-----------:|---------:|----------:|:--------------------|---------------------------:|:----------|--------------------:|---------------------:|
| ALL   | L3M      |       1982 |    0.004 |     -31.4 | 137448/196262       |                      -3176 | 64%       |               0     |                 -9.8 |
| ALL   | L6M      |       4735 |   -0.004 |     -23.1 | 149937/196262       |                     -10350 | 50%       |               0     |                 -7.1 |
| ALL   | HOLD     |       3733 |    0.002 |     -23.2 | 166794/221578       |                      -1869 | 46%       |               0.002 |                -21.2 |
| ALL   | GAP      |       1179 |    0.001 |     -29   | 153118/206481       |                      -4580 | 55%       |              -0.003 |                -11.1 |
| ALL   | PRE      |       4480 |    0     |     -28.4 | 154070/216055       |                      -2340 | 45%       |               0.007 |                -22.8 |
| ALL   | XP       |       4442 |   -0.002 |     -18.9 | 95348/129220        |                      -2763 | 49%       |              -0.007 |                -14.2 |
| ALL   | POOLED   |      19108 |   -0.001 |     -23.6 | 166794/221578       |                      -4066 | 48%       |               0     |                -16.9 |
| 1     | L3M      |       1982 |    0.004 |     -36.7 | 124103/196262       |                      -2347 | 54%       |               0.001 |                -12.9 |
| 1     | L6M      |       4735 |   -0.005 |     -19.4 | 147130/196262       |                     -10958 | 46%       |               0.001 |                -12.2 |
| 1     | HOLD     |       3733 |   -0     |     -24.2 | 163196/221578       |                      -2536 | 47%       |               0.002 |                -24.7 |
| 1     | GAP      |       1179 |   -0.002 |     -31   | 149892/206481       |                      -4858 | 52%       |               0.001 |                -13.9 |
| 1     | PRE      |       4480 |    0.002 |     -33.5 | 147458/216055       |                      -1437 | 48%       |               0.006 |                -23.2 |
| 1     | XP       |       4442 |   -0     |      -5.4 | 107221/129220       |                      -2780 | 49%       |              -0.006 |                -14.1 |
| 1     | POOLED   |      19108 |   -0.001 |     -22.4 | 163196/221578       |                      -4054 | 48%       |               0     |                -19.1 |
| 2     | L3M      |       1982 |   -0.003 |      -4.5 | 183817/196262       |                      -4863 | 42%       |               0.007 |                -31.3 |
| 2     | L6M      |       4735 |   -0.003 |      11.5 | 211774/196262       |                      -5754 | 43%       |               0.004 |                -28.9 |
| 2     | HOLD     |       3733 |   -0.006 |      -5.8 | 210465/221578       |                      -2545 | 46%       |               0.003 |                -17.5 |
| 2     | GAP      |       1179 |   -0.005 |      -6.6 | 182433/206481       |                      -3276 | 48%       |              -0.003 |                -20.6 |
| 2     | PRE      |       4480 |    0.003 |     -23.2 | 179113/216055       |                      -1015 | 52%       |               0     |                -19.2 |
| 2     | XP       |       4442 |   -0.001 |     -15   | 102014/129220       |                      -2561 | 49%       |              -0.001 |                -19.7 |
| 2     | POOLED   |      19108 |   -0.002 |      -6.2 | 211774/221578       |                      -2934 | 48%       |               0.001 |                -19.3 |
| 3     | L3M      |       1982 |    0.001 |       0   | 197477/196262       |                       -182 | 42%       |               0.005 |                -20.8 |
| 3     | L6M      |       4735 |   -0     |       0.9 | 197477/196262       |                      -1028 | 46%       |               0.002 |                -16.7 |
| 3     | HOLD     |       3733 |    0     |       0.3 | 220331/221578       |                        -89 | 52%       |              -0.001 |                 -9.7 |
| 3     | GAP      |       1179 |   -0.008 |      -8.9 | 181210/206481       |                      -3622 | 44%       |              -0.002 |                 -9.8 |
| 3     | PRE      |       4480 |   -0.008 |      -4.9 | 197947/216055       |                      -2951 | 41%       |              -0.003 |                 -3.1 |
| 3     | XP       |       4442 |    0.006 |     -12   | 126703/129220       |                       -100 | 50%       |              -0.003 |                 -1.4 |
| 3     | POOLED   |      19108 |   -0.001 |      -0.1 | 220331/221578       |                      -1275 | 47%       |              -0.002 |                 -5.7 |
| 4     | L3M      |       1982 |    0.003 |     -22.7 | 152428/196262       |                        826 | 52%       |              -0.006 |                 -7   |
| 4     | L6M      |       4735 |    0.002 |     -23.4 | 152428/196262       |                      -1535 | 54%       |              -0.001 |                 -9.1 |
| 4     | HOLD     |       3733 |    0.01  |     -22.2 | 158148/221578       |                       2248 | 56%       |              -0.002 |                 -4.1 |
| 4     | GAP      |       1179 |   -0.001 |      -7.5 | 177442/206481       |                      -3722 | 51%       |               0.001 |                -16.4 |
| 4     | PRE      |       4480 |   -0.001 |       2.5 | 210105/216055       |                      -2778 | 50%       |               0.004 |                -22   |
| 4     | XP       |       4442 |    0.003 |       0.4 | 112239/129220       |                       -861 | 48%       |               0.001 |                -14.7 |
| 4     | POOLED   |      19108 |    0.003 |     -11   | 210105/221578       |                      -1157 | 51%       |               0     |                 -9.5 |
| 5     | L3M      |       1982 |    0.004 |     -20.1 | 153640/196262       |                      -2564 | 48%       |              -0.002 |                -29.7 |
| 5     | L6M      |       4735 |    0.003 |     -21.8 | 153640/196262       |                      -5149 | 48%       |              -0     |                -27.1 |
| 5     | HOLD     |       3733 |    0.007 |     -12.5 | 208440/221578       |                      -1611 | 52%       |               0.002 |                -26.9 |
| 5     | GAP      |       1179 |    0     |     -20   | 163224/206481       |                      -3533 | 48%       |              -0.005 |                -28   |
| 5     | PRE      |       4480 |    0.004 |     -18.6 | 173274/216055       |                      -4166 | 50%       |               0.004 |                -34.5 |
| 5     | XP       |       4442 |    0.006 |     -28.4 | 89293/129220        |                      -2653 | 51%       |              -0.003 |                -22.7 |
| 5     | POOLED   |      19108 |    0.004 |     -13.6 | 208440/221578       |                      -3642 | 50%       |               0     |                -26.2 |
| 6     | L3M      |       1982 |   -0.001 |      -8.2 | 173310/196262       |                      -5595 | 47%       |               0.003 |                -42.3 |
| 6     | L6M      |       4735 |   -0.001 |       2.5 | 191372/196262       |                      -6442 | 51%       |               0.003 |                -33.5 |
| 6     | HOLD     |       3733 |    0.004 |     -31   | 144715/221578       |                       -128 | 49%       |              -0     |                -35.6 |
| 6     | GAP      |       1179 |    0.001 |     -18.3 | 165102/206481       |                      -4116 | 52%       |              -0.004 |                -36.2 |
| 6     | PRE      |       4480 |   -0.001 |     -35   | 139936/216055       |                      -3200 | 49%       |               0.003 |                -36.3 |
| 6     | XP       |       4442 |   -0.003 |     -17   | 110372/129220       |                      -2998 | 51%       |              -0.002 |                -20   |
| 6     | POOLED   |      19108 |   -0.001 |     -22.3 | 191372/221578       |                      -3469 | 50%       |               0     |                -30.8 |
| 7     | L3M      |       1982 |    0.003 |     -15.8 | 173170/196262       |                      -3531 | 54%       |               0.002 |                -28.8 |
| 7     | L6M      |       4735 |   -0.004 |       8.8 | 206748/196262       |                      -9804 | 49%       |              -0.002 |                -17.4 |
| 7     | HOLD     |       3733 |    0.004 |     -45.5 | 125813/221578       |                       2772 | 47%       |               0.003 |                -23.2 |
| 7     | GAP      |       1179 |    0.012 |     -24   | 157522/206481       |                      -1062 | 55%       |              -0.005 |                -13.3 |
| 7     | PRE      |       4480 |    0.003 |     -13.6 | 167810/216055       |                        502 | 51%       |               0.01  |                -22.8 |
| 7     | XP       |       4442 |   -0.002 |       1.8 | 129220/129220       |                       -664 | 67%       |               0.001 |                 -0.2 |
| 7     | POOLED   |      19108 |    0.002 |     -17.3 | 206748/221578       |                      -1370 | 52%       |               0.003 |                -16.4 |
| 8     | L3M      |       1982 |   -0.005 |     -11.9 | 170467/196262       |                      -7190 | 44%       |               0.004 |                -19.2 |
| 8     | L6M      |       4735 |   -0     |     -14.1 | 170467/196262       |                      -3175 | 48%       |               0.003 |                -17   |
| 8     | HOLD     |       3733 |   -0.005 |     -19.4 | 181745/221578       |                       -915 | 46%       |              -0.001 |                -14.4 |
| 8     | GAP      |       1179 |   -0     |      -9.2 | 182004/206481       |                      -3190 | 48%       |               0.001 |                -12.1 |
| 8     | PRE      |       4480 |   -0     |     -23   | 169394/216055       |                      -1970 | 55%       |              -0.001 |                -20.4 |
| 8     | XP       |       4442 |    0.008 |     -20.4 | 97089/129220        |                      -1565 | 50%       |               0.001 |                -12.6 |
| 8     | POOLED   |      19108 |    0     |     -18.7 | 182004/221578       |                      -2095 | 50%       |               0     |                -13.6 |
| 9     | L3M      |       1982 |    0     |     -10.2 | 181048/196262       |                      -1317 | 45%       |               0.003 |                -18.2 |
| 9     | L6M      |       4735 |   -0.001 |     -10.8 | 181048/196262       |                      -3504 | 45%       |              -0.001 |                  5.4 |
| 9     | HOLD     |       3733 |    0.008 |     -12.5 | 206794/221578       |                       2693 | 51%       |              -0.002 |                -14.9 |
| 9     | GAP      |       1179 |   -0.003 |     -11.5 | 182073/206481       |                      -3414 | 47%       |               0.005 |                -21.7 |
| 9     | PRE      |       4480 |    0.003 |     -16.6 | 182707/216055       |                       -641 | 54%       |               0.005 |                -22.9 |
| 9     | XP       |       4442 |    0.001 |      -8.9 | 112891/129220       |                      -2211 | 49%       |               0.002 |                -13.6 |
| 9     | POOLED   |      19108 |    0.002 |     -12.6 | 206794/221578       |                      -1435 | 50%       |               0.001 |                -12.7 |
| 10    | L3M      |       1982 |    0.004 |     -14.9 | 172950/196262       |                       1039 | 39%       |               0.003 |                -15.6 |
| 10    | L6M      |       4735 |    0.002 |      -7.6 | 182450/196262       |                         15 | 42%       |               0.001 |                -12.4 |
| 10    | HOLD     |       3733 |   -0     |      -4.3 | 209075/221578       |                       -290 | 54%       |               0.005 |                -14.8 |
| 10    | GAP      |       1179 |   -0.004 |       5.7 | 209474/206481       |                      -2016 | 38%       |              -0.002 |                  3.6 |
| 10    | PRE      |       4480 |   -0.002 |      -0.4 | 212222/216055       |                       -278 | 45%       |              -0     |                 -1.1 |
| 10    | XP       |       4442 |   -0.006 |       2.7 | 118871/129220       |                      -1960 | 55%       |              -0.003 |                 -0.8 |
| 10    | POOLED   |      19108 |   -0.002 |      -1.8 | 212222/221578       |                       -936 | 49%       |               0.001 |                 -7   |

## Time thirds (2023-10..2024-09, 2024-10..2025-09, 2025-10..2026-10), N=5, 6M, g15, next 2 weeks
| set   | T1                    | T2                    | T3                    |
|:------|:----------------------|:----------------------|:----------------------|
| ALL   | -0.001 R / -21.1% ulc | +0.000 R / -26.2% ulc | -0.002 R / -22.3% ulc |
| 1     | +0.000 R / -5.4% ulc  | +0.002 R / -30.7% ulc | -0.003 R / -21.3% ulc |
| 2     | +0.001 R / -15.8% ulc | +0.000 R / -16.5% ulc | -0.004 R / +2.7% ulc  |
| 3     | +0.007 R / -13.6% ulc | -0.008 R / +2.1% ulc  | -0.000 R / +1.5% ulc  |
| 4     | +0.004 R / -0.0% ulc  | -0.003 R / -0.5% ulc  | +0.007 R / -23.0% ulc |
| 5     | +0.006 R / -29.4% ulc | +0.005 R / -10.3% ulc | +0.003 R / -12.3% ulc |
| 6     | -0.004 R / -19.1% ulc | -0.001 R / -28.5% ulc | +0.002 R / -20.2% ulc |
| 7     | -0.002 R / +0.1% ulc  | +0.004 R / -14.1% ulc | +0.000 R / -24.8% ulc |
| 8     | +0.008 R / -18.9% ulc | +0.001 R / -19.5% ulc | -0.002 R / -18.0% ulc |
| 9     | +0.001 R / -8.2% ulc  | +0.002 R / -14.5% ulc | +0.003 R / -12.5% ulc |
| 10    | -0.006 R / +3.4% ulc  | -0.003 R / +0.9% ulc  | +0.001 R / -5.3% ulc  |
| 1a    | +0.003 R / -23.7% ulc | +0.001 R / -20.4% ulc | -0.000 R / -3.8% ulc  |
| 1b    | -0.005 R / -16.7% ulc | +0.000 R / -28.7% ulc | +0.001 R / -27.8% ulc |
| 1c    | -0.008 R / -11.5% ulc | +0.001 R / -6.8% ulc  | +0.003 R / -38.8% ulc |
| 1d    | +0.002 R / -14.4% ulc | -0.001 R / -26.2% ulc | +0.000 R / -17.2% ulc |
| 1e    | +0.009 R / -19.2% ulc | -0.001 R / +2.5% ulc  | -0.002 R / -13.8% ulc |
| 1f    | -0.002 R / -18.8% ulc | +0.001 R / -19.3% ulc | -0.003 R / -22.4% ulc |
| 1g    | +0.002 R / -26.6% ulc | +0.001 R / -31.0% ulc | -0.001 R / -33.2% ulc |
| 1h    | +0.001 R / -18.5% ulc | -0.008 R / -3.5% ulc  | -0.002 R / -8.4% ulc  |
| 5a    | +0.000 R / -27.7% ulc | -0.003 R / +5.5% ulc  | +0.000 R / -15.1% ulc |
| 5b    | +0.005 R / -31.0% ulc | +0.001 R / -16.1% ulc | +0.005 R / -20.2% ulc |
| NONS  | -0.003 R / -19.1% ulc | +0.002 R / -40.5% ulc | +0.001 R / -29.1% ulc |
| RAND  | +0.003 R / -24.7% ulc | +0.004 R / -28.0% ulc | +0.000 R / -19.1% ulc |
| PLANT | +0.048 R / -22.8% ulc | +0.048 R / -33.8% ulc | +0.048 R / -49.5% ulc |

## Per book x session (ALL families pooled, N=5, 6M picks, g15, next 2 weeks) with shifted-label and random-skip nulls per cell
| cell (book_session)   |   trades OOS |   dMeanR |   dUlcer% | persist   |   shift dMeanR |   shift dUlcer% |   random-skip dMeanR |   random-skip dUlcer% | beats random dU/dm   |
|:----------------------|-------------:|---------:|----------:|:----------|---------------:|----------------:|---------------------:|----------------------:|:---------------------|
| A7_0                  |         1069 |    0.01  |     -22.2 | 52%       |         -0.002 |           -12.8 |                0.003 |                 -20.4 | 60%/90%              |
| H7_0                  |          607 |    0.005 |     -18.5 | 60%       |         -0.003 |           -23.1 |               -0     |                 -23.2 | 20%/70%              |
| H7_3                  |          356 |   -0.008 |     -18.6 | 42%       |         -0     |           -13.7 |                0.001 |                 -14.2 | 70%/10%              |
| K7_0                  |         2011 |   -0.002 |      -5.3 | 48%       |          0.002 |           -17.9 |                0.001 |                 -24.5 | 0%/30%               |
| K7_1                  |         1624 |    0.002 |     -32.6 | 46%       |         -0.003 |           -10.2 |               -0.003 |                 -19   | 90%/80%              |
| K7_3                  |         1652 |   -0.007 |     -17.3 | 42%       |         -0.003 |           -15.6 |               -0.001 |                 -23.2 | 40%/30%              |
| K7_4                  |         1502 |    0.002 |     -14.9 | 56%       |          0.002 |           -21.6 |               -0.006 |                   1.5 | 80%/80%              |
| M7_1                  |         2043 |   -0.001 |     -19   | 44%       |          0.002 |           -19.1 |               -0.002 |                 -25   | 40%/70%              |
| M7_3                  |         1462 |   -0.007 |     -21.2 | 52%       |         -0.003 |           -14.2 |                0     |                 -16.9 | 80%/0%               |
| O7_3                  |          433 |   -0.027 |      -5.3 | 42%       |          0.005 |           -20.3 |                0.016 |                 -29.5 | 0%/0%                |
| P7_0                  |         1951 |   -0.003 |     -10.4 | 45%       |         -0.002 |           -16.2 |               -0.002 |                 -20.6 | 10%/40%              |
| P7_1                  |         1559 |   -0.003 |     -32.5 | 48%       |          0.009 |           -39.7 |                0.006 |                 -33.7 | 50%/10%              |
| P7_3                  |         1612 |    0.01  |     -44.7 | 54%       |         -0.004 |           -21.2 |                0.007 |                 -35.6 | 80%/80%              |
| U7_0                  |          614 |   -0.001 |      -9.3 | 44%       |         -0.001 |            -4.2 |                0.003 |                 -14.8 | 30%/20%              |
| U7_1                  |          613 |    0.002 |     -18.9 | 48%       |          0.015 |           -22   |               -0.001 |                  -3.3 | 100%/80%             |

Per cell by family (N=5, 6M, g15, 2 weeks): dMeanR / dUlcer% real vs shifted-label mean:
| cell   | 1                            | 2                            | 3                            | 4                            | 5                            | 6                            | 7                            | 8                            | 9                            | 10                           | ALL                          |
|:-------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|
| A7_0   | +0.010/-18% (sh -0.003/-19%) | -0.004/-0% (sh -0.005/-19%)  | -0.002/-7% (sh +0.001/-9%)   | +0.007/+17% (sh +0.001/-6%)  | -0.001/-17% (sh -0.002/-17%) | -0.010/-9% (sh -0.004/-15%)  | +0.002/-19% (sh +0.001/-13%) | -0.002/-6% (sh -0.004/-13%)  | +0.001/-7% (sh -0.004/-8%)   | +0.000/+0% (sh +0.000/+0%)   | +0.010/-22% (sh -0.002/-13%) |
| H7_0   | -0.006/-9% (sh +0.002/-25%)  | +0.003/-21% (sh +0.003/-23%) | +0.022/-29% (sh +0.009/-12%) | +0.019/-22% (sh +0.021/-22%) | -0.001/-21% (sh +0.007/-28%) | +0.001/-22% (sh +0.001/-21%) | +0.002/-7% (sh +0.020/-24%)  | +0.005/-16% (sh +0.004/-17%) | -0.008/+5% (sh +0.017/-20%)  | +0.000/+0% (sh +0.000/+0%)   | +0.005/-18% (sh -0.003/-23%) |
| H7_3   | -0.007/-19% (sh +0.001/-21%) | +0.001/-15% (sh -0.012/-13%) | +0.013/-32% (sh +0.014/-33%) | +0.005/-44% (sh +0.008/-30%) | +0.003/-21% (sh +0.011/-37%) | +0.022/-27% (sh -0.010/-20%) | +0.005/-3% (sh -0.015/+7%)   | +0.005/-30% (sh -0.010/-9%)  | +0.016/-29% (sh +0.022/-32%) | +0.008/-23% (sh -0.004/-24%) | -0.008/-19% (sh -0.000/-14%) |
| K7_0   | +0.001/-7% (sh +0.000/-17%)  | -0.016/-4% (sh +0.003/-24%)  | -0.005/-5% (sh -0.001/-7%)   | -0.000/-7% (sh -0.001/-13%)  | +0.004/-21% (sh -0.001/-26%) | +0.002/-15% (sh -0.005/-25%) | +0.015/-28% (sh +0.007/-14%) | -0.002/-12% (sh +0.003/-22%) | -0.003/-5% (sh +0.001/-15%)  | +0.000/+0% (sh +0.000/+0%)   | -0.002/-5% (sh +0.002/-18%)  |
| K7_1   | +0.002/-39% (sh +0.001/-22%) | +0.002/-30% (sh +0.001/-27%) | +0.004/-5% (sh -0.004/-2%)   | +0.002/-6% (sh +0.001/-13%)  | +0.000/-33% (sh -0.002/-19%) | -0.002/-17% (sh +0.006/-42%) | -0.005/+17% (sh +0.006/-17%) | -0.000/-31% (sh -0.001/-10%) | +0.002/-28% (sh -0.007/+3%)  | +0.000/+0% (sh +0.000/+0%)   | +0.002/-33% (sh -0.003/-10%) |
| K7_3   | -0.010/-15% (sh -0.005/-19%) | -0.007/-8% (sh +0.004/-35%)  | -0.005/-3% (sh -0.006/-6%)   | +0.008/-40% (sh -0.004/-4%)  | +0.008/-26% (sh +0.006/-35%) | -0.003/-36% (sh +0.002/-38%) | +0.001/-17% (sh +0.007/-17%) | -0.004/+7% (sh +0.009/-27%)  | -0.002/-12% (sh -0.005/-12%) | +0.000/-21% (sh +0.001/-37%) | -0.007/-17% (sh -0.003/-16%) |
| K7_4   | +0.004/-27% (sh +0.001/-27%) | -0.005/-0% (sh +0.007/-28%)  | -0.004/-0% (sh +0.001/-5%)   | -0.006/-29% (sh -0.009/+1%)  | +0.010/-28% (sh -0.003/-17%) | -0.004/-16% (sh -0.006/-4%)  | +0.001/+57% (sh +0.007/-6%)  | +0.006/-21% (sh -0.006/+1%)  | +0.006/-19% (sh +0.000/-17%) | -0.018/+34% (sh -0.004/-1%)  | +0.002/-15% (sh +0.002/-22%) |
| M7_1   | -0.006/-11% (sh +0.001/-26%) | +0.003/-32% (sh +0.001/-29%) | +0.002/-11% (sh +0.003/-20%) | +0.004/-13% (sh +0.005/-30%) | +0.013/-48% (sh +0.002/-33%) | -0.002/-11% (sh +0.002/-32%) | +0.005/-6% (sh -0.002/-3%)   | +0.003/-27% (sh +0.001/-20%) | -0.003/-4% (sh -0.001/-16%)  | +0.000/+0% (sh +0.000/+0%)   | -0.001/-19% (sh +0.002/-19%) |
| M7_3   | +0.002/-25% (sh -0.002/-21%) | -0.002/-1% (sh +0.007/-15%)  | -0.002/-3% (sh +0.001/-2%)   | -0.005/+7% (sh +0.006/-16%)  | +0.001/-32% (sh -0.004/-21%) | -0.013/-19% (sh +0.002/-24%) | +0.003/-4% (sh -0.004/-4%)   | -0.008/+0% (sh +0.003/-18%)  | +0.001/-12% (sh +0.008/-17%) | -0.004/-18% (sh +0.007/-23%) | -0.007/-21% (sh -0.003/-14%) |
| O7_3   | -0.024/-15% (sh +0.006/-15%) | +0.015/-23% (sh +0.005/-29%) | -0.001/-12% (sh -0.022/-10%) | -0.001/+5% (sh -0.004/+3%)   | +0.083/-34% (sh -0.022/-23%) | +0.011/-26% (sh +0.006/-30%) | -0.031/-9% (sh -0.010/-7%)   | -0.019/-18% (sh -0.018/-20%) | +0.055/-22% (sh +0.014/-18%) | -0.009/-10% (sh -0.007/-23%) | -0.027/-5% (sh +0.005/-20%)  |
| P7_0   | +0.000/-6% (sh +0.000/-19%)  | +0.006/-20% (sh -0.004/-11%) | -0.002/+3% (sh -0.001/-12%)  | -0.001/+7% (sh -0.001/-23%)  | -0.005/+1% (sh -0.005/-21%)  | +0.007/-13% (sh +0.002/-24%) | +0.009/-2% (sh +0.005/-12%)  | +0.010/-25% (sh +0.001/-16%) | +0.004/-17% (sh +0.001/-20%) | +0.000/+0% (sh +0.000/+0%)   | -0.003/-10% (sh -0.002/-16%) |
| P7_1   | -0.004/-34% (sh +0.009/-42%) | +0.001/-38% (sh -0.001/-22%) | -0.000/-7% (sh -0.002/-8%)   | +0.006/-11% (sh +0.007/-32%) | +0.002/-37% (sh +0.004/-32%) | +0.005/-32% (sh +0.001/-34%) | +0.009/-42% (sh +0.006/-37%) | +0.005/-32% (sh +0.007/-34%) | +0.004/-12% (sh -0.005/-21%) | +0.000/+0% (sh +0.000/+0%)   | -0.003/-33% (sh +0.009/-40%) |
| P7_3   | +0.006/-45% (sh -0.002/-19%) | +0.002/-38% (sh -0.000/-25%) | -0.001/-16% (sh -0.003/-5%)  | +0.017/-29% (sh -0.000/+6%)  | -0.001/+7% (sh +0.000/-15%)  | -0.003/-25% (sh -0.000/-30%) | +0.001/-8% (sh +0.001/+6%)   | -0.000/-10% (sh +0.002/-8%)  | +0.005/-37% (sh +0.008/-34%) | -0.005/-21% (sh +0.003/-32%) | +0.010/-45% (sh -0.004/-21%) |
| U7_0   | +0.004/-14% (sh -0.007/-6%)  | -0.008/-19% (sh +0.009/-23%) | -0.005/-9% (sh -0.001/-5%)   | +0.002/+3% (sh +0.003/-27%)  | -0.002/-31% (sh +0.011/-33%) | +0.000/-24% (sh +0.006/-23%) | -0.006/-9% (sh +0.001/-8%)   | -0.004/-24% (sh +0.001/-22%) | -0.001/-14% (sh +0.001/-10%) | +0.000/+0% (sh +0.000/+0%)   | -0.001/-9% (sh -0.001/-4%)   |
| U7_1   | +0.003/-28% (sh +0.009/-25%) | +0.003/-19% (sh -0.003/-13%) | -0.000/-9% (sh -0.002/-8%)   | -0.001/-1% (sh -0.007/-1%)   | -0.004/-13% (sh +0.001/-17%) | -0.001/-23% (sh +0.004/-20%) | -0.005/-4% (sh +0.011/-8%)   | +0.007/-19% (sh -0.001/-15%) | +0.005/-14% (sh +0.002/-22%) | +0.000/+0% (sh +0.000/+0%)   | +0.002/-19% (sh +0.015/-22%) |

## Persistence, turnover and decay of the picks (ALL families pooled, N=5, 6M, g15)
Turnover: mean share of the top-5 list retained from one refit to the next (higher = more stable picks): A7_0 30%, H7_0 29%, H7_3 24%, K7_0 29%, K7_1 28%, K7_3 31%, K7_4 29%, M7_1 31%, M7_3 30%, O7_3 23%, P7_0 28%, P7_1 24%, P7_3 29%, U7_0 25%, U7_1 30%; overall 28%.
Decay: summed gain/loss ($, base lots, $4.84) of the picks by how many 2-week blocks after the refit they are traded (0 = the next 2 weeks):
| set   | labels   | lag 0 (0-13 d)               | lag 1 (14-27 d)             | lag 2 (28-41 d)              | lag 3 (42-55 d)              | lag 4 (56-69 d)              | lag 5 (70-83 d)             |
|:------|:---------|:-----------------------------|:----------------------------|:-----------------------------|:-----------------------------|:-----------------------------|:----------------------------|
| ALL   | real     | -636276$ (45% of pieces >0)  | -720037$ (44% of pieces >0) | -608999$ (44% of pieces >0)  | -562926$ (44% of pieces >0)  | -551388$ (45% of pieces >0)  | -547643$ (44% of pieces >0) |
| ALL   | shift11  | -379966$ (47% of pieces >0)  | -336399$ (47% of pieces >0) | -450379$ (45% of pieces >0)  | -451067$ (44% of pieces >0)  | -474956$ (45% of pieces >0)  | -541785$ (45% of pieces >0) |
| 1     | real     | -618806$ (46% of pieces >0)  | -718255$ (44% of pieces >0) | -695044$ (43% of pieces >0)  | -520844$ (45% of pieces >0)  | -527231$ (44% of pieces >0)  | -542697$ (46% of pieces >0) |
| 1     | shift11  | -243350$ (46% of pieces >0)  | -380437$ (46% of pieces >0) | -587435$ (45% of pieces >0)  | -450211$ (43% of pieces >0)  | -617166$ (44% of pieces >0)  | -613713$ (43% of pieces >0) |
| 2     | real     | -464556$ (45% of pieces >0)  | -340641$ (45% of pieces >0) | -377016$ (43% of pieces >0)  | -280329$ (44% of pieces >0)  | -333622$ (44% of pieces >0)  | -450872$ (43% of pieces >0) |
| 2     | shift11  | -639600$ (44% of pieces >0)  | -592231$ (44% of pieces >0) | -657903$ (45% of pieces >0)  | -394602$ (47% of pieces >0)  | -562332$ (45% of pieces >0)  | -613889$ (45% of pieces >0) |
| 3     | real     | -203799$ (42% of pieces >0)  | -147160$ (41% of pieces >0) | -200307$ (43% of pieces >0)  | -203133$ (40% of pieces >0)  | -332876$ (41% of pieces >0)  | -247940$ (42% of pieces >0) |
| 3     | shift11  | -376841$ (41% of pieces >0)  | -381436$ (42% of pieces >0) | -362508$ (42% of pieces >0)  | -340078$ (41% of pieces >0)  | -335756$ (41% of pieces >0)  | -322927$ (41% of pieces >0) |
| 5     | real     | -557879$ (45% of pieces >0)  | -500230$ (45% of pieces >0) | -509749$ (45% of pieces >0)  | -668814$ (44% of pieces >0)  | -670960$ (42% of pieces >0)  | -486364$ (45% of pieces >0) |
| 5     | shift11  | -928605$ (43% of pieces >0)  | -764422$ (46% of pieces >0) | -786905$ (44% of pieces >0)  | -705521$ (44% of pieces >0)  | -727691$ (44% of pieces >0)  | -749614$ (44% of pieces >0) |
| 7     | real     | -185509$ (48% of pieces >0)  | -49412$ (46% of pieces >0)  | -7247$ (49% of pieces >0)    | -203534$ (46% of pieces >0)  | -147682$ (48% of pieces >0)  | -115492$ (48% of pieces >0) |
| 7     | shift11  | -99304$ (47% of pieces >0)   | -81164$ (47% of pieces >0)  | -126522$ (47% of pieces >0)  | -93579$ (45% of pieces >0)   | -89442$ (47% of pieces >0)   | -127693$ (46% of pieces >0) |
| 10    | real     | -139633$ (43% of pieces >0)  | -62970$ (44% of pieces >0)  | -29598$ (45% of pieces >0)   | -32234$ (43% of pieces >0)   | -42740$ (41% of pieces >0)   | -34741$ (43% of pieces >0)  |
| 10    | shift11  | -55173$ (43% of pieces >0)   | 18196$ (46% of pieces >0)   | -27353$ (44% of pieces >0)   | 21571$ (46% of pieces >0)    | 107$ (44% of pieces >0)      | -4895$ (44% of pieces >0)   |
| NONS  | real     | -944170$ (42% of pieces >0)  | -913976$ (42% of pieces >0) | -1004669$ (43% of pieces >0) | -1218331$ (43% of pieces >0) | -876370$ (44% of pieces >0)  | -899844$ (44% of pieces >0) |
| NONS  | shift11  | -1139574$ (44% of pieces >0) | -973464$ (45% of pieces >0) | -1069709$ (45% of pieces >0) | -1087698$ (47% of pieces >0) | -1181476$ (45% of pieces >0) | -899394$ (45% of pieces >0) |

## SCORES (equal-weight vote of the top 5 / top 10 recent conditions; g15 picks; rule = trade by thirds of the vote, next 2 weeks chained, 6M picks)
| set   |   K | rule       |   dMeanR |   dUlcer% |   d$/wk | persist   |   shift dMeanR |   shift dUlcer% | beats 3 shifts   |
|:------|----:|:-----------|---------:|----------:|--------:|:----------|---------------:|----------------:|:-----------------|
| ALL   |   5 | skip_low   |   -0.003 |      -6.7 |   -7603 | 50%       |         -0     |            14.5 | no               |
| ALL   |   5 | half_low   |   -0.001 |     -16.3 |   -3801 | 49%       |         -0     |            -8.7 | no               |
| ALL   |   5 | boost_high |   -0.001 |      25.2 |    3453 | 50%       |         -0.001 |            33.9 | no               |
| ALL   |  10 | skip_low   |   -0.008 |      12.2 |   -7421 | 48%       |          0.001 |             1.2 | no               |
| ALL   |  10 | half_low   |   -0.003 |      -4.6 |   -3711 | 48%       |          0     |           -10.1 | no               |
| ALL   |  10 | boost_high |   -0.002 |      36.9 |    2703 | 49%       |         -0     |            25.9 | no               |
| 1     |   5 | skip_low   |   -0.003 |     -16.4 |   -7486 | 49%       |          0.003 |            -8   | no               |
| 1     |   5 | half_low   |   -0.001 |     -16.7 |   -3743 | 48%       |          0.001 |           -17.9 | no               |
| 1     |   5 | boost_high |   -0.002 |      33.2 |    3161 | 47%       |          0     |            29.9 | no               |
| 1     |  10 | skip_low   |   -0.004 |       7.9 |   -6731 | 47%       |         -0.004 |             3.2 | no               |
| 1     |  10 | half_low   |   -0.001 |      -4.2 |   -3365 | 47%       |         -0.002 |            -9.1 | no               |
| 1     |  10 | boost_high |   -0     |      28.6 |    3417 | 48%       |         -0.001 |            29.5 | no               |
| 2     |   5 | skip_low   |    0.007 |     -14.8 |   -3740 | 49%       |          0.002 |             3.4 | no               |
| 2     |   5 | half_low   |    0.003 |     -17.7 |   -1870 | 49%       |          0.001 |            -9.8 | no               |
| 2     |   5 | boost_high |    0.001 |      27   |    5012 | 49%       |         -0     |            39.1 | yes              |
| 2     |  10 | skip_low   |    0.006 |     -22.5 |   -3446 | 49%       |          0.005 |             6.4 | no               |
| 2     |  10 | half_low   |    0.002 |     -17.2 |   -1723 | 48%       |          0.002 |            -4.2 | no               |
| 2     |  10 | boost_high |   -0     |      27.3 |    4355 | 49%       |          0.001 |            41.7 | no               |
| 3     |   5 | skip_low   |   -0.005 |      19   |   -4172 | 47%       |         -0.005 |             1.8 | no               |
| 3     |   5 | half_low   |   -0.002 |      -1.8 |   -2086 | 46%       |         -0.002 |            -6.5 | no               |
| 3     |   5 | boost_high |   -0.001 |      14.1 |    1316 | 46%       |         -0.001 |            13.9 | no               |
| 3     |  10 | skip_low   |   -0.007 |      22.2 |   -5345 | 47%       |         -0.004 |             3.2 | no               |
| 3     |  10 | half_low   |   -0.003 |      -2.1 |   -2673 | 46%       |         -0.002 |            -6.5 | no               |
| 3     |  10 | boost_high |   -0.001 |      14.3 |     895 | 45%       |          0     |            13.6 | no               |
| 5     |   5 | skip_low   |    0.008 |      -8.7 |   -8620 | 51%       |         -0     |            -1.5 | no               |
| 5     |   5 | half_low   |    0.003 |     -13.6 |   -4310 | 50%       |         -0     |           -12.7 | no               |
| 5     |   5 | boost_high |    0.001 |      37.5 |    2584 | 49%       |          0     |            28.8 | no               |
| 5     |  10 | skip_low   |    0.011 |      -8.2 |   -6325 | 51%       |          0.003 |            -4.7 | no               |
| 5     |  10 | half_low   |    0.004 |     -10.5 |   -3162 | 50%       |          0.001 |           -11.3 | no               |
| 5     |  10 | boost_high |    0.001 |      34.3 |    2723 | 50%       |          0     |            26.6 | no               |
| 7     |   5 | skip_low   |    0.002 |       2.9 |   -4699 | 52%       |          0.006 |           -21.7 | no               |
| 7     |   5 | half_low   |    0.001 |     -11.4 |   -2349 | 51%       |          0.002 |           -18.7 | no               |
| 7     |   5 | boost_high |    0.001 |      13.4 |    3464 | 52%       |          0.001 |            23.8 | no               |
| 7     |  10 | skip_low   |    0.011 |     -25.3 |   -2100 | 54%       |          0.003 |           -27.5 | no               |
| 7     |  10 | half_low   |    0.004 |     -23.1 |   -1050 | 53%       |          0.001 |           -20.3 | no               |
| 7     |  10 | boost_high |    0.001 |      15   |    3268 | 52%       |          0.001 |            12.9 | no               |
| 10    |   5 | skip_low   |    0     |      -6.9 |    -921 | 50%       |          0.002 |           -10.1 | no               |
| 10    |   5 | half_low   |    0     |      -5   |    -460 | 49%       |          0.001 |            -7.8 | no               |
| 10    |   5 | boost_high |   -0.001 |      10.3 |     284 | 48%       |         -0     |             5.7 | no               |
| 10    |  10 | skip_low   |    0     |      -5.6 |   -1053 | 49%       |          0.002 |            -8.9 | no               |
| 10    |  10 | half_low   |    0     |      -5.7 |    -526 | 48%       |          0.001 |            -6.7 | no               |
| 10    |  10 | boost_high |   -0     |      11.4 |     280 | 48%       |         -0     |             4.5 | no               |
| 1c    |   5 | skip_low   |    0.013 |      -9.8 |   -3702 | 52%       |         -0.008 |             2   | no               |
| 1c    |   5 | half_low   |    0.004 |     -18.2 |   -1851 | 51%       |         -0.003 |           -13.9 | yes              |
| 1c    |   5 | boost_high |    0.001 |      24.2 |    4159 | 50%       |         -0.002 |            28.9 | yes              |
| 1c    |  10 | skip_low   |    0.004 |     -15.9 |   -4527 | 51%       |         -0.005 |             0.1 | yes              |
| 1c    |  10 | half_low   |    0.001 |     -18.9 |   -2263 | 50%       |         -0.002 |           -12   | yes              |
| 1c    |  10 | boost_high |    0.001 |      16.8 |    4370 | 51%       |         -0.001 |            28.7 | yes              |
| 1d    |   5 | skip_low   |    0.003 |      -7.8 |   -6642 | 52%       |         -0.002 |            15.4 | yes              |
| 1d    |   5 | half_low   |    0.001 |     -16.7 |   -3321 | 51%       |         -0.001 |            -3.5 | yes              |
| 1d    |   5 | boost_high |    0     |      25.8 |    3256 | 51%       |          0     |            35.4 | no               |
| 1d    |  10 | skip_low   |    0     |     -11.2 |   -5923 | 51%       |          0.005 |             4.5 | no               |
| 1d    |  10 | half_low   |    0     |     -13.8 |   -2962 | 50%       |          0.002 |            -6.9 | no               |
| 1d    |  10 | boost_high |   -0.001 |      24.7 |    2915 | 49%       |          0.001 |            26.2 | no               |
| 1e    |   5 | skip_low   |   -0.007 |      34.1 |   -8343 | 50%       |          0.004 |            12.7 | no               |
| 1e    |   5 | half_low   |   -0.003 |       1.8 |   -4171 | 49%       |          0.001 |            -9.6 | no               |
| 1e    |   5 | boost_high |   -0.001 |      42.4 |    2841 | 49%       |          0.001 |            30.1 | no               |
| 1e    |  10 | skip_low   |   -0     |       7.3 |   -6755 | 50%       |          0.006 |           -12.1 | no               |
| 1e    |  10 | half_low   |   -0     |     -12.8 |   -3377 | 49%       |          0.002 |           -15   | no               |
| 1e    |  10 | boost_high |    0.001 |      32.5 |    3290 | 51%       |          0.001 |            28.4 | no               |
| 5a    |   5 | skip_low   |   -0.001 |     -19.4 |   -7244 | 49%       |          0     |           -16.8 | no               |
| 5a    |   5 | half_low   |   -0     |     -18.1 |   -3622 | 48%       |          0     |           -17.5 | no               |
| 5a    |   5 | boost_high |   -0.001 |      28.9 |    2625 | 48%       |          0.001 |            22.9 | no               |
| 5a    |  10 | skip_low   |    0.004 |      26   |   -6586 | 51%       |          0.005 |           -16.9 | no               |
| 5a    |  10 | half_low   |    0.002 |       0.4 |   -3293 | 51%       |          0.002 |           -16.4 | no               |
| 5a    |  10 | boost_high |   -0     |      44   |    3049 | 51%       |          0.001 |            24.4 | no               |
| 5b    |   5 | skip_low   |    0.011 |      -5.5 |   -7647 | 51%       |          0.001 |            35.7 | yes              |
| 5b    |   5 | half_low   |    0.004 |     -16.6 |   -3824 | 50%       |          0     |            -5.2 | yes              |
| 5b    |   5 | boost_high |    0.003 |      36.8 |    3628 | 51%       |          0     |            33.3 | no               |
| 5b    |  10 | skip_low   |    0.016 |      -8.1 |   -5583 | 52%       |          0.002 |            19.2 | no               |
| 5b    |  10 | half_low   |    0.006 |     -13.7 |   -2792 | 51%       |          0.001 |           -11.9 | no               |
| 5b    |  10 | boost_high |    0.002 |      31.2 |    3110 | 51%       |          0.001 |            27.8 | no               |
| NONS  |   5 | skip_low   |    0.004 |      -3.4 |   -8127 | 50%       |         -0.001 |            -2.3 | no               |
| NONS  |   5 | half_low   |    0.001 |     -21.1 |   -4064 | 49%       |         -0     |           -18.2 | no               |
| NONS  |   5 | boost_high |    0.001 |      23.4 |    3623 | 50%       |          0     |            27.1 | no               |
| NONS  |  10 | skip_low   |    0.009 |      -8.3 |   -7109 | 50%       |         -0.001 |             5.9 | no               |
| NONS  |  10 | half_low   |    0.003 |     -15.2 |   -3554 | 49%       |         -0     |            -9.1 | no               |
| NONS  |  10 | boost_high |    0.001 |      24.9 |    3163 | 51%       |         -0     |            24.6 | no               |
| RAND  |   5 | skip_low   |    0.006 |     -33.3 |   -6560 | 51%       |          0.005 |           -14.3 | no               |
| RAND  |   5 | half_low   |    0.002 |     -22   |   -3280 | 50%       |          0.002 |           -18.2 | no               |
| RAND  |   5 | boost_high |    0.001 |      31.1 |    4347 | 51%       |          0     |            28   | no               |
| RAND  |  10 | skip_low   |    0.002 |     -18   |   -6137 | 50%       |         -0     |            -3.4 | no               |
| RAND  |  10 | half_low   |    0.001 |     -15.4 |   -3068 | 49%       |         -0     |           -12.4 | no               |
| RAND  |  10 | boost_high |    0.001 |      25.5 |    4206 | 50%       |          0.001 |            23.5 | no               |
| PLANT |   5 | skip_low   |    0.391 |     -93.6 |   67212 | 91%       |         -0.175 |          4089.1 | yes              |
| PLANT |   5 | half_low   |    0.13  |     -77   |   33606 | 89%       |         -0.067 |          1135.4 | yes              |
| PLANT |   5 | boost_high |    0.082 |     -51.4 |   42136 | 90%       |         -0.036 |           318.6 | yes              |
| PLANT |  10 | skip_low   |    0.396 |     -93.9 |   72299 | 91%       |         -0.178 |          4198.9 | yes              |
| PLANT |  10 | half_low   |    0.135 |     -78.6 |   36149 | 89%       |         -0.068 |          1174.4 | yes              |
| PLANT |  10 | boost_high |    0.084 |     -51   |   44331 | 89%       |         -0.036 |           321.1 | yes              |

Vote in thirds on the next 2 weeks (K=5; thirds cut at the pick-window terciles of the vote; real labels vs the shifted-label procedure):
| set   | labels   | low: share, meanR   | mid: share, meanR   | high: share, meanR   |   high-low meanR |
|:------|:---------|:--------------------|:--------------------|:---------------------|-----------------:|
| ALL   | real     | 45%, +0.045         | 7%, +0.042          | 47%, +0.039          |           -0.006 |
| ALL   | shift11  | 45%, +0.036         | 7%, +0.055          | 49%, +0.046          |            0.009 |
| ALL   | shift23  | 46%, +0.051         | 7%, +0.077          | 47%, +0.028          |           -0.023 |
| ALL   | shift37  | 46%, +0.040         | 7%, +0.070          | 47%, +0.040          |            0.001 |
| 1     | real     | 46%, +0.046         | 8%, +0.070          | 47%, +0.034          |           -0.012 |
| 1     | shift11  | 45%, +0.021         | 6%, +0.049          | 49%, +0.061          |            0.04  |
| 1     | shift23  | 46%, +0.049         | 6%, +0.038          | 48%, +0.036          |           -0.014 |
| 1     | shift37  | 46%, +0.045         | 7%, +0.061          | 47%, +0.037          |           -0.008 |
| 3     | real     | 25%, +0.059         | 52%, +0.031         | 23%, +0.035          |           -0.024 |
| 3     | shift11  | 29%, +0.076         | 45%, +0.026         | 26%, +0.022          |           -0.054 |
| 3     | shift23  | 26%, +0.045         | 49%, +0.042         | 25%, +0.031          |           -0.014 |
| 3     | shift37  | 27%, +0.053         | 47%, +0.028         | 26%, +0.053          |            0     |
| 5     | real     | 47%, +0.033         | 8%, +0.078          | 45%, +0.045          |            0.012 |
| 5     | shift11  | 44%, +0.050         | 10%, +0.004         | 47%, +0.043          |           -0.007 |
| 5     | shift23  | 44%, +0.039         | 9%, +0.030          | 47%, +0.047          |            0.008 |
| 5     | shift37  | 44%, +0.038         | 10%, +0.048         | 46%, +0.044          |            0.006 |
| 7     | real     | 46%, +0.039         | 11%, +0.010         | 43%, +0.046          |            0.006 |
| 7     | shift11  | 47%, +0.033         | 13%, +0.031         | 41%, +0.047          |            0.014 |
| 7     | shift23  | 46%, +0.031         | 10%, +0.051         | 44%, +0.044          |            0.013 |
| 7     | shift37  | 45%, +0.028         | 12%, +0.029         | 43%, +0.053          |            0.025 |
| 10    | real     | 45%, +0.040         | 11%, +0.058         | 44%, +0.030          |           -0.01  |
| 10    | shift11  | 42%, +0.032         | 13%, +0.017         | 45%, +0.048          |            0.016 |
| 10    | shift23  | 42%, +0.022         | 13%, +0.079         | 46%, +0.044          |            0.022 |
| 10    | shift37  | 44%, +0.036         | 11%, +0.111         | 45%, +0.025          |           -0.011 |

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
