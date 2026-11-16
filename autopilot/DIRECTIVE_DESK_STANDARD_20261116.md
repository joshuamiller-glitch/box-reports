INBOX ORDER 20261116_2000Z_desk-standard-validation (research only)
Adds to 20261116_1954Z_calibrate-the-pass-rule. Applies to T-REBUILD,
T-JOINT-EXIT and every later study. Server 2 capacity.

The user asked how a professional desk validates a strategy change. The
published standard has four parts we are only partly doing. Add them.

1. COUNT THE TRIALS, THEN CORRECT FOR THEM.
   For every family searched, keep a ledger: how many variants were tried
   (including discarded ones), on which windows. Report every "best of N"
   with a data-snooping test over the WHOLE family, not the winner alone:
   - White's Reality Check and Hansen's SPA test (stationary bootstrap of
     the weekly P&L differences vs JL2, 2,000 resamples) for "is the best
     of these N better than the benchmark";
   - the deflated Sharpe ratio (Bailey / Lopez de Prado) for the winner,
     using the real trial count;
   - Benjamini-Hochberg at 10% when a list of survivors is reported.
   Add these columns to DS3_PASS_RULE.md.

2. PROBABILITY OF BACKTEST OVERFITTING for every FITTED choice (T-REBUILD
   stage 2 scores, stage 3 exits, any setting picked by search):
   combinatorially symmetric cross-validation (split the weeks into 12-16
   blocks, all train/test combinations): how often the in-sample best
   lands in the bottom half out of sample (PBO), and the performance
   degradation slope. Purge 1 week between train and test blocks. A fitted
   choice with PBO above 0.5 is not a result. Report PBO beside the
   walk-forward number; they answer different questions.

3. DRAWDOWN AS A DISTRIBUTION, NOT ONE NUMBER.
   Stationary block bootstrap of weekly P&L (block length from the
   autocorrelation, state it): median max DD, 95th-percentile max DD,
   probability of a drawdown deeper than 1x, 2x, 3x average weekly
   profit, for JL2 and for each candidate. This is the number the user
   scales lots by. Put it on the first table of every page.

4. INCUBATION PROTOCOL (how a rule goes from research to live):
   write autopilot/INCUBATION.md: for each rule coded as a Shadow switch
   in D7 v2.0 (M7 London cap, give-back, against-the-day target), state
   IN ADVANCE: the metric, the number of shadow events needed, the
   threshold to go Live, and the threshold to drop it. Then score the
   shadow lines from each morning's NT8 Output log against that, and the
   engine's prediction for the same trades (live vs engine agreement per
   event). No rule moves from Shadow to Live on research alone unless it
   is CONFIRMED under the calibrated rule.

5. In every page header, one line: trials counted, method of correction,
   PBO if fitted, and whether the number shown is in-sample, walk-forward
   or untouched.
