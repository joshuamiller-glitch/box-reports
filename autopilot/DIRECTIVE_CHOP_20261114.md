USER ORDER — T-CHOP: ALL RESOURCES ON CHOP DAYS. 2026-11-14. Research only; nothing on the execution server or any live chart changes. Save verbatim as DIRECTIVE_CHOP_20261114.md, log within 15 minutes, start now.

WHY. DS3_POSTMORTEM: the 20 worst weeks are many small state cuts in low-efficiency sessions (753 StateCut trades, -$1.18M of -$2.1M), not full stops or re-entries. That is the target. T-CHOP goes to the FRONT of the queue with at least 60% of cores. Keep running behind it: priority 1 (live cut bug), priority 4 (joint v2.0, finish JV_AB's last two windows), priority 12 (refit). Everything else from the two earlier orders drops to what is left.

STEP 1 — LABEL (after the fact, for scoring only). Per session and per day, 43 months: efficiency ratio, number of crossings of the session mean, range used vs net move, and D7's own result (cuts per target, net of the stack). Define CHOP as the worst tercile and show that the label captures the dollars: share of the 20 worst weeks and 40 worst days it explains. Fix the label before step 2.

STEP 2 — FORECAST, two clocks, benchmarked against "yesterday was chop" and ATR:
(a) BEFORE the session: open vs prior value area / prior range / prior close (market profile: inside value, outside value, gap), prior-session efficiency and its 3- and 5-day run, overnight range vs ATR, the range forecast on the box, calendar flags (day before FOMC / CPI / NFP, day after a >2 ATR day, holiday week, opex week and day, month-end), VIX level and curve, Cboe implied correlation and VVIX (free daily; fetch them).
(b) DURING the session, at 15 / 30 / 60 / 90 minutes and rolling: efficiency so far; volume vs the same clock's normal; points moved per contract traded; mean crossings so far; index disagreement (rolling correlation and return dispersion of NQ, ES, RTY, YM; NQ-vs-ES relative strength flips); order book balance from mbp-10 (depth both sides vs normal, cancel rate, time the inside quote sits unchanged); NQ options implied move vs move so far; D7's own cluster (cuts with no target in the last 30 / 60 / 120 min, per book and stack-wide).
Report for each input: does it forecast CHOP for the rest of the session, by how much over the benchmark, session by session, with shifted-day placebos.

STEP 3 — WHAT D7 DOES ON A CHOP CALL (exact engine, JN05W2, all layers ON; the call is causal). Not only "skip":
1. stand down: no new entries for the rest of the session, or for N minutes, per book and stack-wide;
2. half size;
3. chop mode: nearer target (0.5 / 0.67 x), take at the session mean, tighter time stop, no re-entry on the same side inside the box;
4. favour the mean-reversion book and bench the trend / pullback books, by size not on/off;
5. lower the day-done and stack caps for that session only;
6. the exit: when the call flips back to trend (range expansion, efficiency recovering), restore everything at once. Report what each action costs on days wrongly called and on the best-5 weeks.

STEP 4 — OUTSIDE DATA, QUOTE ONLY. Quote 1-minute bars for the Nasdaq-100 components back to 2023-04 (Databento equities; also state what Massive / Polygon stocks would cost) to build true breadth, up-volume share, dispersion and average pairwise correlation. Do NOT buy. Before quoting, test the cheap proxy already on the box: the megacap 1-minute prices from the UW pull (7 names) as a mini breadth / dispersion measure. If the proxy forecasts CHOP, say so and the user will approve the purchase.

RULES. Session by session. L3M and L6M from today first, then HOLD, PRE, X', GAP; tolerant gate; a lead must hold in recent AND older windows. Drawdown first (max DD, worst week, cuts per week, best-5 weeks kept, winning weeks turned losing), then mean. Judge drawdown against exact placebos and with week 2026-W44 removed. Walk-forward every 2 weeks. "Nothing" is not a deliverable: deliver the best chop call and the best action per session with its evidence.

REPORT. DS3_CHOP.md, plain one-line verdict at the top. Step 1 and the first forecast table within 3 hours; step 3 first exact results within 8 hours; hourly status line in MORNING.md.
