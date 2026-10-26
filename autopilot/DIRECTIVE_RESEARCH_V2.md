# DIRECTIVE RESEARCH V2 (user, 2026-10-24) — verbatim
RESEARCH V2 — how the box tests from now on. Standing rules; supersedes the pass rule in every earlier directive. STRUCT48 Tracks 1, 2, 4 continue, re-scored under these rules.
Unchanged: prereg before scoring, UNTOUCHED never read, no execution-server / chart / live change, no credentials, no downloads without my OK. Benchmark = live Set A, corrected P9, live cost.

1. Three verdicts, not two
Every scored cell gets exactly one:
PASS — WF mean up, holdout sign agrees, placebo rank >= 0.95, neighbours agree, and the effect clears the criterion sized to the object (section 3). Goes to a Sim leader for 2 weeks, scored against its own backtest expectation, then to me.
CANDIDATE — WF mean up, holdout sign agrees, placebo rank >= 0.90, neighbours agree, but the CI includes zero or one secondary condition fails. Registered automatically in PAPER-ALL within the same day, forward-scored weekly against its backtest expectation (section 5). Never binned.
DEAD — anything else. Listed once with the reason, never re-run with the same features. "Fails one condition" is no longer a death sentence; it is the definition of CANDIDATE. Every report lists all three tiers.

2. Power before scoring — the minimum detectable effect
Before any cell is run, the prereg states the mechanism in one sentence, the predicted effect ($/wk or pts/trade), and the minimum effect the test can detect at 80% power on the WF window. If the predicted effect is below the detectable one, the test is not run at the weekly level: it is run at the TRADE level (section 2b) or not at all. No more tests whose answer is guaranteed to be "CI includes zero".
2b. Trade-level paired scoring for anything that changes what D2 does to a trade it already takes (exits, brackets, slices, join timing, scale-out, pyramiding, re-arm, stop-count halts, session cutoffs): score the per-trade difference, paired on the same signal, with a trade-block bootstrap (blocks = session). 6,000 paired trades detect a 1-pt/trade effect; 100 weeks cannot. Weekly P&L is still reported, but the pass/candidate decision uses the paired test when the cell is a trade-modifier. Signal changes and new sleeves still use weekly scoring.

3. Criteria sized to the object
A trade-modifier: paired mean effect > 0 with the paired CI excluding 0, and maxDD not worse in the full sequence.
A sizing / lock / session rule: weekly mean not down and weekly SD or maxDD down with CI, or mean up with maxDD not worse.
A sleeve (new system run beside D2): judged at its own size on standalone holdout mean > 0, marginal portfolio Sharpe up at the tested risk ratio, correlation <= 0.5. "Cuts Set A's maxDD by 10%" is withdrawn — a 2-lot sleeve cannot move a $330k drawdown and was never going to.
An execution change: measured pts/trade with the paired test, no weekly test at all.

4. Hypotheses, not families
No agent generates families to keep cores busy. Every cell in a prereg has: mechanism (why the market would pay this), predicted effect, detectable effect, the object type from section 3, and the nearest previously-scored cell with its result (so nothing is re-tested under a new name). Preregs are capped at 30 cells each. Idle cores run the robustness backlog (section 7), never new noise. Priority order for new hypotheses, by where the edges have actually been found: execution and fills; sizing and locks; session structure; trade management; signal; new sleeves. Prediction of session outcome is closed unless a new data source arrives.

5. Forward paper is the real holdout
Every CANDIDATE and PASS is registered in PAPER-ALL the day it is scored, with its backtest expectation written down (mean/wk, SD, per-trade effect).
FORWARD_REGISTER.md, rewritten daily from the live-file push: for each registered cell, weeks live, realised vs expected, a running z-score, and a verdict: ON TRACK / BEHIND / PROMOTE (>= 6 weeks, realised within 1 SD of expected, sign right) / RETIRE (>= 8 weeks, more than 2 SD behind).
The live Set A vs Set B forward column stays; add the live join rate and slip to the same file. Live is the only holdout that cannot be peeked.

6. Re-open the near-misses now (first job, ~2 hours)
Re-score under sections 1–3 every cell of the last two weeks that cleared >= 70% of its old conditions. At minimum: RSI(2) dip-buy on NQ / ES / RTY (8 of 9); overnight drift unfiltered (fails CI only); soft half-size switch STACK-FB +5 theta0.3; BEST5 risk set (cap off, floor 12R, 14/10/10); PBDAY Set B; skip-join patch; stop-join wait variants; C5_m10 opening-range fade; TH cooldown cells with positive mean; any STRUCT48 Track 1/2/4 cell already scored. Write NEARMISS_RESCORE.md with the new verdict per cell and register every CANDIDATE in PAPER-ALL the same day.

7. Robustness backlog — what idle cores do instead of generating noise
In order: larger bootstraps on every CANDIDATE; re-score CANDIDATEs at 1.5x and 2x cost; CANDIDATEs on the 1-s tape where they were scored on 1-min; the combined system (all CANDIDATEs and PASSes stacked on Set A, scored once as one system with the full sequence test — this is where income shows up, and it has never been run); replication of each PASS with fresh seeds on a different window; live-vs-replay reconciliation per trade from the daily push.

8. Reporting
LEADERBOARD.md (one file, all tracks) rewritten every 2 h: cell, object type, test used (weekly / paired), effect with CI, placebo, holdout, verdict, forward status. MORNING.md leads with: PASSes, CANDIDATEs registered since last edition, forward register changes, the combined-system line, cores busy. Reports state the detectable effect next to every null so a null reads as "could not have seen less than X" instead of "nothing works".

# RESEARCH V2 addendum — handoff book (user, 2026-10-24) — verbatim
RESEARCH V2 addendum - handoff book: prereg and score, under the paired trade-level rules, a book that activates ONLY after an ST or HM stop-out in the same session and runs until session end or its own exit: (a) reverse at the stop fill (the stop IS the entry), bracket {20, 30, 40} pts stop / {1.0, 1.5} R, lots {4, 7}; (b) VWAP-reversion from the stop fill, target VWAP, stop 1.5x distance; (c) opening-range / prior-value re-entry after the stop; (d) re-entry in the ORIGINAL direction on a re-break of the stopped level within {15, 30} min. Each cell paired against "do nothing after the stop". Mechanism: a 67-pt stop-run exhausts the move. State the detectable effect. Register any CANDIDATE in PAPER-ALL same day.
