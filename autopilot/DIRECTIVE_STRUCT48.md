# DIRECTIVE STRUCT48 (user, 2026-10-24) — verbatim
STRUCT48 — 48-hour program: change what D2 does in a session, and what runs beside it. Replaces PRED as the box's priority.

Rules unchanged: prereg per track before any scored cell, UNTOUCHED never read, no execution-server / chart / live change, no credentials, no downloads or paid pulls. Benchmark = live Set A on the corrected P9 replay with live cost (stop-join 1.01 pt, $4.84 RT), 14/14, locks on. Scoring harness = FAILPRED Part 3 / STEP2 R1–R11: WF weekly mean / SD / maxDD / worst week / L8W, week-block bootstrap CI of the difference vs Set A, placebo (500 random rules of the same shape), deflated Sharpe on the cumulative ledger (continue from PRED's corrected count), 2x cost sign, no year > 60% of gain, holdout 2025-07+ scored once after the pre-holdout text is written, full-system sequence with locks / give-back / week floor / 50-contract limit. PASS = WF mean up, maxDD not worse, CI excludes 0, placebo rank >= 0.95, holdout sign agrees, and the two neighbouring cells agree in sign. Report every cell, pass or fail, with the conditions it failed.

PRED hand-off
PRED keeps only what is needed to finish the FOUND-protocol vetting of the block-I Asia +15 lead and the unlocked-label relabel/re-score of the leaderboard. Cap: 4 slots, 24 h. Write PRED_FINAL.md with the vetted Asia number, the unlocked leaderboard top 10, and one line: FOUND / not found. Then PRED stops; no new PRED families. All other PRED agents stop now; their running jobs are adopted or killed by the coordinator and the slots go to STRUCT48.

Utilisation
90% core floor applies. Tracks run in parallel from the start. Report per track in the MORNING block every 2 h: slots, cells scored / total, best cell so far, ETA.

Track 1 — structural session rules (start first; ~1/4 of cores; fixed grids, no optimisation inside a cell)
T1.1 Stop-count halt per book per session: after N stops (N in {1,2,3}) the book takes no new entries until the next session. Variants: pooled (either book's stops count for both), and with the -2R day lock left on / turned off, so we see whether this replaces it.
T1.2 Entry-window grid: no new Asia entries after {00:00, 00:30, 01:00, 01:30} ET; no new London entries after {07:30, 08:00, 08:30, 09:00}; NY first entry not before {09:30, 10:00, 10:30, 11:00}. All 64 combinations plus each session alone (12 cells). Open trades keep their brackets.
T1.3 Max entries per book per session in {1,2,3}; re-arm delay after a stop in {0,15,30,60} min; cross both.
T1.4 Direction-asymmetric parameters: longs and shorts separately — stop in {50,60,75}, target R in {1.0,1.5,2.0}, lots in {10,14}. Report the long-only and short-only P&L of Set A first so the asymmetry has a baseline.
T1.5 Combinations: the best passing cell of T1.1 x best of T1.2 x best of T1.3, scored once, with its neighbours.

Track 2 — diversification inside D2 (~1/4 of cores)
T2.1 Parameter ensemble: 6 D2 variants (ST period/multiplier +-1 step, stop {50,60,75}, target R {1.5,2.0}), each with 1/6 of the lots, run as one book; compare to the single-parameter book at equal total lots. Also 3-variant and 8-variant versions.
T2.2 Multi-timeframe vote: the ST signal computed on 1/2/3/5-min bars; enter on majority (>=3 of 4), size proportional to votes (2 -> 50%, 3 -> 75%, 4 -> 100%); same for HM.
T2.3 Book agreement: when ST and HM flip the same direction within N min (N in {5,15,30}), lots x {1.25,1.5}; when they hold opposite positions, lots x {0.5,0.75}. Keep the 50-contract limit in the sequence test.
T2.4 Pyramiding: add 50% at +30 pts in favour (stop for the add at entry); scale-out: 50% off at 1R, remainder trailed by {20,30} pts to 2R. Four cells each.
T2.5 The best of T2.1–T2.4 stacked with the best of Track 1, scored once.

Track 3 — second system, scored as a PORTFOLIO with D2 (~1/3 of cores; the real target of this program)
Score every candidate two ways: standalone, and as a portfolio with Set A at a fixed dollar-risk split (candidate sized so its standalone weekly SD = {0.25, 0.5, 1.0} x Set A's). The portfolio columns are what matter: weekly mean, SD, maxDD, worst week, correlation of weekly P&L with Set A. PASS for a second system = portfolio maxDD down >= 10% with portfolio mean not down, correlation <= 0.5, standalone mean > 0 after cost on the holdout, placebo and CI as above.
T3.1 D2 across markets: the same ST+HM signals, session lots and brackets (ATR-scaled to each market), on ES, RTY, YM, CL, GC, ZN, 6E, 6J. Each market standalone, then the equal-risk basket, then the basket with NQ. Use the S130_ES build as the template. Report the weekly correlation matrix.
T3.2 Different trigger on NQ: (a) opening-range breakout (15/30-min OR, volume >= 1.5x 20-day same-clock), (b) Donchian 20/55 on 5-min, (c) VWAP-trend (price and 20-bar VWAP slope agree, pullback-to-VWAP entry), (d) liquidity-sweep continuation (sweep of prior swing then reclaim within N bars, enter in the reclaim direction). Fixed brackets 60/1.5R, same session lots. Each standalone and with Set A.
T3.3 Different horizon on NQ: (a) multi-day swing — daily Supertrend / 20-day breakout, 2–5-day holds, fixed ATR stop, 2–4 lots; (b) overnight drift — long at 15:55 ET close, flat at 09:30 open, with a VIX-term and prior-day filter; (c) weekly-open breakout. Each standalone and with Set A.
T3.4 Portfolio assembly: the top 3 passing sleeves from T3.1–T3.3 with Set A, risk-parity weights, re-estimated monthly in WF; report the portfolio line vs Set A alone, and the L8W.

Track 4 — execution cost already on the table (~1/12 of cores; pure cost, no forecast)
T4.1 Skip-join patch: when the other book's stop-join is working, go straight to market on this book's stop (position-limit safe). Score the $/wk and the rejection count.
T4.2 Entry style: market (current) vs limit at the flip level with a 10-s then market fallback vs limit at level -2 ticks. Fill rule: trade-through only.
T4.3 Slice timing: 1 s / 2 s / 4 s between 1-lot slices, and 2-lot slices at 2 s.
T4.4 Stop-join wait: 2 s / 3 s / 5 s before market.

Reports
STRUCT48_LEADERBOARD.md rewritten every 2 h (track, cell, delta mean/wk, delta maxDD, CI, placebo, holdout, pass count of 6, neighbours agree Y/N). REPORT_STRUCT48_T<n>.md per track when complete. At 48 h: REPORT_STRUCT48.md with one table of every PASS, the combined best (Track 1 + 2 rule set, plus the Track 3 portfolio) scored once as a single system, and a verdict of this form: "Passing structural rules: <list or none>. Passing diversifiers: <list or none>. Combined vs Set A: +$X/wk, maxDD -$Y, SD -$Z, CI [..], holdout <sign>." No spec, no live recommendation — anything I decide to run goes through my own test-then-score rule. When a track finishes early its cores go to Track 3. If every track finishes before 48 h, generate the next 20 structural and diversification ideas, prereg the top 5, and run them; do not idle.
