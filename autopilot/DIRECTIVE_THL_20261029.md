T-TH-LOSS — the loss-side Trade Health search: adaptive, order-book-aware, every book, firm-grade (2026-10-29)

Research only. No live, execution-server or chart change. UNTOUCHED never read. Redact account ids. Runs beside T-TH-PROFIT on the same dataset machinery (THP A extended to the LOSS side), same MEASURED fills (market exit +1 tick on the 1-s path), same walk-forward protocol as the ADAPTIVE addendum (windows 1 week .. 12 months and EWMA half-lives 5/10/20 days; steps intraday / daily / weekly; online learners; ensembles; regime-conditioned; CUSUM re-fit trigger; meta-labelling). Session as a column everywhere. Budget 4-8 h on all cores, shared with T-TH-PROFIT.

The question

The live loss-side Trade Health (15 pts adverse, 3 of 3 conditions, 30 s) cuts a losing trade before its 60-pt stop. DS3_TH_LOSS (fixed rule, full history) found it hurts or is neutral on every book; the user runs it on because the one stretch it was off lost badly live. He wants the best possible ADAPTIVE loss-side policy: when a trade is under water, hold to the stop / cut now / tighten, decided from the trade's path, the order book and the tape, re-fitted on recent data and updating constantly. Fixed-rule history is cited, not re-run.

A. The dataset (extend THP A to every second UNDER WATER)

Every trade of every book (ST, HM, WT, KB, SM, PE, PB, DN, MV, MA, CR, basket legs, D6 session cells, O6), from the first second below entry to the exit, at every 1 s and every 1-min close: unrealised pts, MAE, time under water, seconds since the MAE, recovery from MAE (pts and %), velocity, efficiency, distance to the stop (pts, % of R) and to the target; the live rule's own three conditions as booleans. Order book (NQ mbp-10): depth imbalance 5/10 levels, size at the stop level ("is there a wall between me and my stop" / "is the stop sitting in thin book"), size at the current best on my side vs theirs, aggressor delta 10 s / 60 s, trade intensity vs the session median, large prints against me, absorption at the current price, pulled bids/offers, spread. Bars: ATR regime, VWAP and band distance, session H/L distance, opening-range edges, swing levels between price and the stop, Supertrend 1m/5m/10m state vs my side, 20-EMA slope. Cross-asset: ES/RTY move since entry in their ATR, ES-NQ divergence. Time: minute of day, session, minutes to the next clock release. Stack: other books' positions, day P&L. Labels: remaining P&L to the bracket exit from here, whether the target or the stop is hit first, max further adverse excursion, time to resolution.

B. Rule grids (baseline)

Paired vs hold-to-stop on identical entries: fixed adverse cuts (10/15/20/30/40 pts), time-under-water cuts (5/10/20/30/60 min below -X), MAE-recovery rules (cut if no recovery of Y% within N s), stall-under-water (no new MAE but no recovery), velocity against, the live rule and its grid (adverse 10-30, required 1-3, window 10-120 s), stop-tightening rules (stop to MAE + buffer after N s), partial cuts (half at -X), and the "do nothing until the stop" control. In-sample AND walk-forward, per book, session, year; the saved-loss / forfeited-recovery split (how many cut trades would have recovered to target).

C. Learned policies (walk-forward, re-fitted, online, ensembles, regime-conditioned, meta-labelled — exactly as the ADAPTIVE addendum)

Models predict P(stop before target from here) and E[remaining pts]; policy = hold / tighten / cut, action threshold on E[remaining] vs the cut cost; optimal-stopping tables; competing-risks hazard; change-point on the path; flow HMM (is the tape moving against me or just drifting); quantile regression (worst-case from here); sequence model last. Online learners after every closed trade; short/long ensembles; regime keys (realised vol, first-hour range, VIX tercile, time of day); CUSUM re-fit trigger; meta-labelling for cut size (full / half). Placebos: shuffled labels within day; random cuts at the same rate. Report the walk-forward chain as the primary result, by book / session / year, MDE, exit rate, saved vs forfeited, and the drift series of what the policy keys on.

D. Joint policy (both sides in one file)

The profit and loss policies are two halves of one state machine on an open trade. Evaluate them together on the stack (every book at once): weekly series, SD, maxDD, worst-20-weeks, vs the stack as it is, vs profit-only, vs loss-only. Report interaction (a loss cut that frees the book for a new entry — the re-entry effect is in the exact lock engine).

E. The policy file

Same THP_POLICY.json carries a loss section per book: feature grid (<= 4 features NT8 can compute: unrealised as % of stop, seconds under water, recovery from MAE, 60-s aggressor delta or depth imbalance), action per cell (hold / tighten with the new stop distance / cut), regime dimension, validity date, walk-forward number. Distilled from the best walk-forward policy, retained gain >= 80% stated. D6 reads it at the 18:00 session open (my side); missing/stale -> the book's own switch (TH-loss as configured).

Report

DS3_THL_A_DATA.md, DS3_THL_B_RULES.md, DS3_THL_WF.md (walk-forward table, drift, regime read, distilled policy), DS3_THL_FINAL.md with one verdict line per book and the stack line, and the plain sentence "re-fitting on the last N, the loss policy saves X pts/trade out of sample (MDE Y) on books A, B and costs on C" — or that nothing beats the stop. The joint file THP_POLICY.json after both finals. MORNING.md every 2 h.
