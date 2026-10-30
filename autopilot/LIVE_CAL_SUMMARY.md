# LIVE_CAL_SUMMARY - live exit-fill calibration for UF cycle agents (BASISL part a, 2026-10-30)
Scope (user confirmation in DIRECTIVE_L2_UNTIL_FOUND_20261030.md: "read live exit fills from 2026-10-20 for cost calibration only"): real-account (<acct>) DualStrat2, DS3, DS5, DS6, DualStrat exits from 2026-10-20 ET; columns used: strategy/exit name, side, qty, entry/exit time, entry/exit price (no account id, no P&L columns); Sim files, K4 and nt8log not used; only aggregated tables written (out/basis_live/LIVE_CAL_AGG.md); no raw rows copied, no strategy scoring. Code: l2vast/ds3/code/basis_live/live_exit_cal.py, run_cal.py.
Coverage limit: the 1-s path ends 2026-10-23 21:00 UTC, so 51 of 252 exits (10-20..23) have a path price; exits after that have fill-vs-nominal only. Time alignment verified: 1-s rows are labelled at the END of the second (limit-target fills first appear in the row exit_second+1 s in 12 of 13 cases; offset applied).

## Fitted exit-cost model (pts, +ve = worse than reference)
| exit class | n (with path) | vs 1-s path last at exit second (mean, SE) | vs NOMINAL level | M / N / CONS expectation | closest |
|---|---|---|---|---|---|
| StopJoin (passive join filled) | 17 total / 11 | -0.80 (0.39) | -0.52 (n=8, 10-20..23) i.e. 0.52 BETTER | stop 1.01 / 1.01 / 2.02 | better than all (join fills at the stop) |
| StopJoinFallback (join timed out, market) | 12 / 9 | +0.86 (0.42) | +4.46 (n=12, SE 0.83) | 1.01 / 1.01 / 2.02 | vs path: M; vs nominal: worse than CONS |
| StopJoinRejected | 6 / 1 | +2.0 (n=1) | +2.11 (n=1) | | n too small |
| STOP-class pooled, true 60-pt stops (excl WT_Stop) | 21 | +0.05 (0.34) | +2.45 (SE ~0.75) | 1.01 / 1.01 / 2.02 | CONS (z +0.6) not M (z +1.9) |
| LossExit (TH/loss cut, market) | 123 / 14 | +0.80 (0.22) | | 0.995 / 0.995 / 1.99 | M (z -0.9) |
| ProfitExit (market) | 8 / 4 | +0.19 (0.28) | | 0.995 | M-or-better (n=4) |
| Lock exits | 8 / 3 | +1.83 (1.08) | | 0.995 | n=3 |
| Target (limit) | 55 / 13 | fill vs nominal level +0.0 (fills at entry +/-60.0, 59.9-60.1) | | corr 4.3 (2026) / 0 / 4.3 | N point estimate |
Stop cost model vs nominal: cost = p_FB x 4.46 - (1-p_FB) x 0.52 (+ rejects ~2.1); live p_FB = 12/21 = 0.57 -> 2.45. If the join worked (p_FB 0.2) the stop cost would be ~0.5; if every stop fell back it is 4.5. Stop-distance and year dependence cannot be fitted: all true stops are 60 pts, all 2026 (bucket table: 50-pt bin and 60-pt bin both inside SE).
Cost vs path (LossExit +0.80, FB +0.86) matches M's ~1.0 market slip; the difference between 4.46 (vs nominal) and 0.86 (vs path at exit second) is DELAY: the join waits several seconds after the stop level trades, and the price keeps moving before the market fallback.

## Touched-target fill rate (the M-vs-N question)
Path crossed entry +/-60 (live target distance is exactly 60.0 from the entry fill) in 11 trades with path coverage: all 11 ended as TARGET fills (fill rate 11/11, one-sided 95% lower bound 0.72). 10 of the 11 traded through by more than 2 ticks, 1 by 2 ticks; there were NO marginal touches (exactly at the level or 1 tick through). Two target fills were not matched by a path touch (path high 0.05 and 0.41 pt short): tick-source difference.
Reading: live is consistent with N (no target correction) as the point estimate, but the sample contains none of the marginal touches M's 4.3-pt correction models, and M itself implies ~3.6% unfilled touches, for which P(11/11) = 0.67; the test has no power to reject M. Say: "live supports N for through-by->2-tick touches (11/11); M-vs-N for marginal touches is UNDECIDED". Needed to decide: more weeks, and the tape for 10-24 onward.

## Reconciling 2.45 (LIVE_RECON) with +0.68 (LIVE_VS_REPLAY_P9_2026-10-26..29)
Both are fill vs entry-fill -/+ 60 (the same definition; +ve better in the P9 files). The +0.68 pools 26 'stop' exits: the 21 true 60-pt stops (mean -2.45, i.e. 2.45 worse) PLUS 5 WT_Stop exits whose stop is ~46-47 pts, so against the hard-coded 60-pt level they read +13.86 'better' (SE 0.13, an artefact). (21 x -2.45 + 5 x 13.86)/26 = +0.68. Excluding the WT_Stop exits both give -2.45 exactly. 2.45 is the correct figure; +0.68 is wrong and should not be used. 10-20..23 true stops: -2.01 (n=18); 10-24+ true stops: n=3, all fallbacks, -5.10.

## LIVE-CAL basis (use this in UF cycles)
stop-class exits 2.45 pt worse than the nominal stop level (SE ~0.75; rule: 0.52 better if joined, 4.46 worse if fallback; fallback share 0.57); market-class exits (loss/profit/time cuts) at M ~1.0 pt vs path (0.80 +/- 0.22 measured); targets filled at nominal (target correction 0 = N basis) as the point estimate with M's correction retained as the stress case. In BASIS_DEF terms: LIVE-CAL = LIVE-P9-T0 (point), LIVE-P9 (stop 2.45, target corr kept) = stress.
