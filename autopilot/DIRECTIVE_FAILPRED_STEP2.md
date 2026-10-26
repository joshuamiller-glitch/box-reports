# DIRECTIVE FAILPRED STEP 2 (user, 2026-10-23, user away; do not wait for the user at any point)
Runs automatically the moment REPORT_FAILPRED.md is written. Same rules: prereg frozen before any scored cell, UNTOUCHED never read, no execution-server or chart changes, no downloads, P9-corrected replay with live cost.

INPUT FROM STEP 1: Take the predictor at every horizon that passed the switch test in 2.5. If none passed, take the best WF cell at each of +15, +30, +60 and label every result NOT PASSED. Call the flagged sessions "chop sessions". The flag is as-of time h, never ex post. Report how many chop sessions there are per type, and the precision at that threshold, so every result below is read against the right base rate.

CANDIDATE SET (frozen, all scored, nothing added later). From time h to session end, in chop sessions only:
C0 flat (halt) - the baseline every row is measured against
C1 D2 same signals, bracket x0.5 (stop and target)
C2 D2 same signals, bracket x0.5, target only (stop unchanged)
C3 D2 with the trend condition inverted (fade the flip)
C4 VWAP reversion: enter toward VWAP when price is >= k x session-VWAP-band from it, k in {1.0,1.5,2.0}; exit at VWAP or stop at 1.5k
C5 opening-range fade: fade a break of the first-h-minute range when the break fails within m minutes, m in {5,10,15}; target range midpoint, stop beyond break extreme
C6 two-sided limit scalp around session VWAP, +-N pts, N in {10,15,20}, target VWAP, stop 1.5N, max one open per side
C7 prior-day value fade: fade touches of prior-day H/L/close, target 15 pts, stop 15 pts
C8 C4 and C6 with a time stop (exit after 20 / 40 min if not at target)
C9 the D2 pair as-is, in chop sessions only (so we see what the switch is removing)
Fixed-parameter cells only; no optimisation inside a cell. Total cells <= 40. List them in the prereg with their count.

ROBUSTNESS - every cell, no exceptions
R1 Walk-forward expanding window, monthly refit of the predictor only (strategies have no fitted parameters). The holdout is 2025-07 onward, scored once, after everything else is written.
R2 Cost: live model (stop-join 1.01 pts, limit fills only when price trades through the level by >= 1 tick, never fill-at-touch). Also report at 2x cost. Any cell whose sign flips at 2x cost is marked FRAGILE.
R3 Placebo A - same strategy on 500 random session sets of the same count and type mix as the chop set. Report the rank of the real result.
R4 Placebo B - same strategy on the sessions the predictor says are NOT chop. If it earns there too, it is not a chop strategy; mark GENERAL.
R5 Perfect-foresight ceiling - same strategy on the ex-post failing sessions (definition that step 1 found most predictable). Report capture % = real / ceiling.
R6 Weekly bootstrap CI (1,000 draws, block = week) of the difference vs C0. Pass requires CI excluding zero.
R7 Deflated Sharpe over the full cell count (<= 40 trials plus the step-1 search; use the true total).
R8 Stability: result by year, and by session type; fail if any year contributes > 60% of the gain.
R9 Look-ahead audit: the automated check that caught the VWAP-band mean in step 0, run on every feature and every entry rule here; any hit -> fix, re-run, note it.
R10 Trade-count sanity: cells with < 150 trades in WF are reported but cannot pass.
R11 Sequence test: run the real pair + candidate as a single system over the full tape (not sessions in isolation) so locks, give-back and position limits interact as live. Report weekly mean, SD, maxDD, worst week, L8W vs benchmark Set A and vs Set A + halt switch.

PASS = beats C0 on WF mean with R6 CI excluding zero, R3 rank >= 0.95, R4 not GENERAL, not FRAGILE, R8 ok, R10 ok, holdout sign agrees, and R11 shows maxDD not worse than Set A + halt switch. A cell that passes everything but one is reported with the one it failed, not hidden.

WIDENING - only if something passes. If one family passes, run one widening pass on that family only: a 3x3 parameter grid around the passing cell, scored identically. Report the grid whole; a passing cell whose neighbours all fail is marked ISOLATED and does not count.

REPORT_FAILPRED_STEP2.md: table 1 chop-session counts and precision per horizon; table 2 every cell x {WF mean/wk vs C0, CI, placebo A rank, placebo B result, ceiling capture, 2x cost sign, trades, pass/fail with reason}; table 3 R11 full-system rows for C0 (= Set A + switch) and any passer. Verdict, exactly: "Chop sessions are predictable at horizon h with precision p. Halting alone is worth +$X/wk, maxDD -$Y. Of 9 families, N beat halting: <list or 'none'>. Best: <cell>, +$Z/wk over halting, CI [..], placebo rank r, holdout s, ceiling capture c%." Then stop. After this report, resume the paused FOURTH replay (l2vast/fourth; FOURTH_BOOK_PROGRESS.md). Interim FAILPRED-2 block in MORNING.md every 2 h with ETAs.
