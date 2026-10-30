# QUANT-LAYER ADDENDUM — user directive pasted 2026-10-30 (verbatim)

QUANT-LAYER ADDENDUM — applies to EVERY program ordered today (CONFIRM-LAYER + COMBOS + BARS + SUB-MINUTE, BARS-ALL, SIGNAL-DECAY + REVERSE-CONFIRM, STACK-PARTIALS, RISK-OFF, NO-TRADE-ZONES, FAVORABLE-ZONES, TREND-GATE + addendum, the L2 cycles, RECENT_WINS): the tests a quant firm runs on a candidate before it is believed (2026-10-30)

Every program adds the following to its scoring and its final report. Nothing already in a directive is removed; this is the layer on top. Where a program's own text already has an item, it is done once.

1. Statistical validity (per cell and per program)
Multiple-testing control: White's reality check AND the Romano-Wolf stepdown (which cells survive, not just whether the best does) over each program's cells; the deflated Sharpe ratio (Bailey-López de Prado) per cell with the number of trials; the probability of backtest overfitting (PBO, combinatorially symmetric cross-validation) per program; the minimum backtest length implied by the number of trials.
Cross-validation that respects time: purged k-fold with embargo (trades overlapping a fold boundary removed; 1-day embargo), combinatorial purged CV for the learned layers; walk-forward with anchored AND rolling windows (3 / 6 / 12 months); report the dispersion of the out-of-sample estimate across folds, not one number.
Effective sample size: trades are not independent (books overlap, trades cluster in time): the day-clustered and week-clustered standard errors, the block bootstrap (blocks = days and = weeks) for every CI; the autocorrelation of weekly P&L and the Newey-West t-stat.
Placebos as a standard set on every cell: shuffled labels within day; shuffled features / levels / book (time-aligned); time-shifted features (60 s and 1 bar earlier); random rules at the same fire rate and the same time-since-entry distribution; the same rule on a shuffled-day market; the rank of the real cell among ≥ 200 placebo draws.
Sensitivity: every threshold ±25% and ±50% (the rule must not live on a knife edge); the parameter-surface plot (the neighbourhood of the chosen cell must be positive too — report the mean of the 8 neighbours); timeframe ±1 step; the result on the N / M / live-cal / conservative fill bases side by side.
Stability: the rolling 3-month estimate plotted through 2023-2026 (the drift series); the sign-agreement count across quarters; the "first half vs second half" split of every window; the regime split (vol tercile, day type, session) — a rule must be reported with the regime it works in.

2. Economic validity
Per-contract after ALL costs: commission 0.242 pt RT, the measured entry slip, the measured stop cost (2.45 vs nominal live; 0.5 with the join fix) and the target-fill correction, each as a column, and the breakeven cost (the slippage at which the rule's gain is zero).
Capacity: the number of contracts the rule's fills could absorb at the measured book depth at its entry/exit prices (the top-5 depth at those seconds); flag rules whose fills depend on < 10 contracts of depth.
Turnover and trades per week; the gain per trade AND per week; the gain concentrated in how few trades (the share of the gain from the top 5% of trades — a rule living on 3 trades is reported as such); the longest losing run in weeks.
Opportunity cost: the skipped-signal P&L beside every filter; the re-entry effect on the lock engine beside every exit.
Correlation with the stack as it is: the weekly P&L correlation of the rule's delta with the stack; the marginal Sharpe / marginal worst-20-weeks contribution (a rule that adds mean but correlates 0.9 with the stack is worth less than one that adds less at 0.2).

3. Information validity (for anything that claims a predictor)
The information coefficient (rank correlation of the rule's "signal" and the realised outcome) out of sample, with its decay by horizon (10 s .. 60 min); the IC's t-stat with day-clustered SE; the IC vs the shuffled and time-shifted placebos; the hit rate vs the base rate; the calibration curve of any probability model (predicted vs realised P(target) by decile); the Brier score vs the unconditional.
Feature attribution with drift: the top features at each re-fit and how they change by quarter; the learned rules extracted in words with their retained gain.
"Would a simpler rule do the same?": every learned cell beside its best single-feature and best two-feature distillation; the complexity penalty stated.

4. Execution validity
Latency: every rule evaluated with a 1-s and a 3-s delay between the trigger and the order (the live strategy runs on ticks but decides on bar closes / 1-s evaluations); the result at each delay.
Order type realism: market vs limit-at-best vs limit-in-structure, each on the measured basis for that order type; queue position for resting limits (the contracts ahead at placement; the fill probability model from the live calibration where available).
Partial fills and slicing: the 1-lot slice schedule as live (2-s gaps) applied to every entry/add/exit of ≥ 2 lots.
Live-replay reconciliation: for any rule that runs live, the forward register compares live fills to the replay at the trigger second (the P9 file method, with each trade's real stop, not a hard-coded 60).

5. Reporting standard (every final)
The one-page header of every final carries, for each promoted or CANDIDATE-RECENT cell: per-contract pts after all costs [block-bootstrap CI] | L3M / L6M / HOLD / PRE / X' | trades per week | fire rate | 1 of N cells | RC p (program) | Romano-Wolf survives Y/N | DSR | PBO | placebo rank | neighbourhood mean | breakeven slippage | capacity (contracts) | top-5%-of-trades share of gain | stack correlation | regime it works in | drift sign count | the plain sentence. A cell missing any column is not promoted. RECENT_WINS.md gains the same columns.

6. Priority
The validity layer runs on every cell that reaches CANDIDATE-RECENT or better (not on the DEAD mass), on the PRE-selected rows of every program, and on anything the user runs live; the DEAD rows get the RC / placebo columns only. Budget inside each program.
