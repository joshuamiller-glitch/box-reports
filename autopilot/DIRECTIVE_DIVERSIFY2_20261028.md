# DIRECTIVE 2026-10-28 T-DIVERSIFY-2 (verbatim from user)

T-DIVERSIFY-2 — intraday diversifiers chosen by what the stack lacks (2026-10-28, runs after DIRECTIVE_DIVERSIFY T-DIVERSIFY intraday)

Research only. No live, execution-server or chart change. UNTOUCHED never read. No purchase or download without the user's OK. Redact account ids. Intraday only: every position flat by its session close (overnight close-to-open sleeves excepted, as in T-DIVERSIFY). Before scoring any cell, check the ledger (LEADERBOARD, TREND_LEADERBOARD, every DS3_*.md final): anything already scored is cited, not re-run. Same evidence rules as T-DIVERSIFY (small preregs, both placebos, by-year, sibling or pooled replication, 2x cost, MDE beside every mean). Objective throughout: marginal Sharpe added to the live stack at fixed risk and P&L in the stack's 20 worst weeks, never standalone return.

T-DIVERSIFY searches other markets by their own clock. This program searches by a different axis: what the stack is missing. A diversifier is anything that makes money where the stack loses, trades when the stack is flat, or is neutral to NQ direction by construction.

A. Diversification audit of the stack (first; descriptive; drives everything below)
On the live stack (ST/HM/WT + KB/SM/PE exact engine, 2023-04..now) decompose weekly P&L: by hour of day (ET, 30-min), by session (Asia 18:00-02:00, Europe 02:00-08:30, pre-US 08:30-09:30, RTH blocks, close), by day type (trend / range / reversal day: first-hour range and close-vs-open vs 20-day medians), by scheduled-event day vs not, by weekday, by VIX tercile, by month-end / opex week. Report: where the 20 worst weeks were lost (hours, day types), where the stack is flat (hours with < 10% of trades), the share of P&L from each session, and the single plain line: "the stack loses on X days in Y hours and is idle in Z hours". Every candidate below is then scored on those hours/day-types explicitly, not only overall.

B. Relative value intraday (market-neutral by construction: zero NQ beta)
Pairs, dollar-neutral both legs, signal = z-score of the 1-min log-ratio vs its intraday (rolling 60/120/240-min) mean, enter at |z| >= 2 (and 2.5), exit at z = 0 or flat at the session close, stop at |z| = 3.5 or 2x the median pair range; fees on both legs; both legs at equal $ risk. Pairs: NQ/ES, RTY/ES, YM/ES, NQ/RTY, ZN/ZB (or ZF/ZN), CL/RB, CL/HO, GC/SI (what exists on disk; mark NEEDS). Also the "laggard catch-up" variant at fixed clocks (10:00, 11:30, 14:00): go long the index that lags the others' first-hour move, short the leader, flat at 15:55. Per pair and pooled; replication = works on >= 3 of the index pairs or >= 2 of the commodity/rate pairs. Report the stack correlation (should be ~0) and the worst-20-weeks P&L.

C. Scheduled-event intraday books (calendar effects that are flat by the close — allowed under the no-swing rule)
Build the event calendar from fixed public schedules known to the box (FOMC statement 14:00 + presser 14:30 dates 2022-2026; CPI, PPI, NFP, retail sales 08:30; ISM 10:00; GDP 08:30; Treasury 10y/30y auctions 13:00; EIA crude Wed 10:30, NatGas Thu 10:30; opex third Friday; month-end and quarter-end; MSCI/S&P/Russell rebalance days) and confirm each release minute by its 1-min volume signature; label the calendar RECONSTRUCTED and list any date the volume signature does not confirm. If the box cannot assemble a date list, write the NEEDS line and the user supplies a CSV. Cells per event type (<= 6 each): first-1-min post-release range break with bracket 1x/1.5x the event's median post-release range, flat at +60/+120 min; the fade of the first 5-min move; the pre-event drift (enter 60 min before, flat at the release). Month-end: 15:00-16:00 equity-index flow (direction = sign of the month-to-date move, inverse), opex-Friday 14:00-16:00 pin fade, rebalance-day MOC. Score on NQ, ES, ZN, CL, GC as the events apply. Pooled across years; MDE beside each; these are few-trades-per-year cells, say so.

D. Stack-state conditional books (make money exactly where A says the stack loses)
New books whose trigger includes the stack's own state, exact lock engine, scored as a stack add only:
- Counter-trend after a loss cluster: after >= 2 trend-book stop-outs/TH cuts on the same side within 60 min, enter the opposite side at the next VWAP-band (1 sigma) touch, 60/60 (and 40/40), flat at session end. Also the version keyed to the KB stop only.
- Idle-hours book: a VWAP-band fade (and a 20-bar range break) that trades only in the hours A marks idle (likely 11:30-14:00 ET and parts of the night), bracket at the window's own median range; the point is trades in hours where the stack has none.
- Trend-day re-entry book: after a TH cut on ST/HM/KB, if the 5-min Supertrend is still in the trade's direction and price makes a new extreme within 30 min, re-enter with the original bracket (own lock). Scored vs the no-re-entry baseline; cite DS3_TH_LOSS.
- Reversal-day book: when the first hour closes against the overnight direction by > 1x its median range (A's reversal-day label), trade the reversal direction on the next pullback to VWAP, flat 15:55. Each <= 4 cells. Report every one on A's loss-hours and loss-day-types explicitly.

E. The MBO setups as diversifiers (cheap: they already exist)
The seven frozen NQ MBO setups in paper soak on the execution server: take their paper trade series (and the research backtest series where it exists), compute weekly correlation to the live stack, stack-add at 10/20/30% risk, worst-20-weeks P&L. No new cells; this is an audit. Say plainly whether any of the seven is a diversifier rather than another way of buying NQ trend.

F. Night-session map (NQ and ES; the stack trades these hours blind)
Time-of-day map 18:00-09:30 ET: Asia open 19:00-20:00, Europe open 02:00-03:00 (and 03:00 London), 08:30 pre-US; signed return, range, volume, by year. Then one rule per live window (Europe-open range break on NQ/ES with the window's own bracket, flat 08:00; Asia-open fade) <= 6 cells, scored on the stack's own night P&L from A as the comparator.

G. Internals NEEDS line
NYSE TICK / ADD / VOLD and the VIX intraday series are not on disk and Databento does not carry them. State what source would (NT8 feed symbols recorded forward; CBOE for VIX 1-min) and what the first study would be (TICK extremes as NQ reversal/continuation signal; VIX intraday spike as a stack gate). No scoring.

H. Portfolio and specs
For every CONFIRMED cell from B-F: stack-add at 10/20/30% risk, marginal Sharpe, maxDD change, worst-20-weeks $, weekly correlation; the solve for the best 2-3 at maxDD not worse; the Sim spec (instrument(s), session, exact ET times, order types, bracket in ticks, flat rule, lots at $1,000 risk and at the user's scale, costs, plain-English paragraph) codeable in NT8 without reading the study. For pairs: both legs' routing and the dollar-neutral lot rule.

Reporting
DS3_DIV2_A_AUDIT.md first (the plain line about where the stack loses and idles, with the tables). Then DS3_DIV2_<B..F>.md never-empty-handed (top cells regardless of verdict, failed gate, MDE, performance on the audit's loss-hours). MORNING.md every 2 h. DS3_DIV2_FINAL.md: one verdict line per family, and the one number — $ in the stack's 20 worst weeks at 20% risk.
