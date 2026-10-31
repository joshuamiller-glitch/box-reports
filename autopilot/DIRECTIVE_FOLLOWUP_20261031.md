# FOLLOW-UP ORDERS from tonight's findings — user directive pasted 2026-10-31 (~04:00Z by the user's clock) (verbatim)

FOLLOW-UP ORDERS from tonight's findings (user, 2026-10-31 ~04:00Z) — runs inside the 36-hour plan; section 1 first, before the Sunday brief

Research only. Same rules as PLAN36 (measured + live-cal fills, per contract first, recent-first, session column, QUANT-LAYER columns, prereg, dead cells, RECENT_WINS rows). Live lots for every question below: K6 2 (Asia/London/NY-AM/NY-PM), P6 7 (Asia/London/NY-AM), U6 4 (Asia/London), H6 4 Asia / 2 NY-AM, M6 2 (London/NY-AM), A6 1, O6 1; N6/S6/WT/MA not live; research/2.35 mapping is acceptable where a book's live lot is 0.

1. THE SUNDAY STACK, AS CODED (the number that matters most)
Score D6 v2.3b exactly as it will run Sunday 18:00 ET, jointly on the stack with the lock engine, recent-first, vs the stack as it is and vs each piece alone and each piece removed (leave-one-out):
70/30 split at 3 pt (1 book sign), stop at the original level, target re-based from the average;
PE confirmation in NY-AM and NY-PM only: the signal held for a 45-s three-bar (two candles against, then a candle closing beyond the previous candle's opposite extreme), entry at MARKET at that candle's close (not the limit at body mid), then the split; hold dies at the original stop level / opposite signal / session lots 0 / time block; no confirmation = no PE trade in those sessions; other sessions plain split;
ER(20) on 5-min at the signal: × 1.5 lots at/above 0.30, × 0.5 below, with the book's R and $ day locks multiplied by the day's largest multiplier (not the base-lot governors);
stack rule: when a book that ENTERED in Asia is stopped, cut the other same-side open books 50% at market, brackets re-sized;
no-trade set: a FRESH line among the 8 coded (PD mid, 1-h kijun, 4-h Keltner upper, 4-h bar mid, RTH Camarilla H3, 15-m OTE 62 / 70.5 / 79) within 20 pts between entry and target → skip (the 3 profile lines absent);
Native stops (1.28 pts) for every book. Report DS3_SUNDAY_STACK.md: weekly mean, SD, maxDD, worst-20-weeks in L3M / L6M / HOLD / PRE / X'; the leave-one-out table; the per-session table; the plain sentence "as coded, Sunday's D6 vs the stack as it is: X $/wk L6M (MDE Y), Z HOLD, W PRE"; and the one change, if any, that the numbers say to make before 18:00 ET. This goes into DS3_SUNDAY_BRIEF.md as its first table.

2. ES-leads-NQ sizer (N1 d: ≥ 0 in 6 of 6 windows — deepen and make it D6-ready)
Exact definition (ES move over the prior 15 / 30 / 60 s in ES ticks / ATR, sign vs the NQ signal, magnitude buckets), per session, as a sizer (× 0.5 / 1 / 1.5) and as a skip on the split base and with the ER sizer; placebo = time-shifted ES; the walk-forward threshold chain; capacity; the definition in D6 terms (D6 has an ES 1-min series as the basket leg; state whether 1-min closes suffice or ticks are needed). Report DS3_ESLEAD.md.

3. The ordered array combinations (CF-COMBO: 22 INFO candidates, "iplFVG / iFVG / FVG then OB within 60 s")
Pooled cross-stage stage done; then: the exact rule per book written as a D6 confirmation (which array on which timeframe first, which second, the window, the mechanic — market at the second print / limit at the OB mean / the split), the walk-forward chain with its last re-fit, placebos (random-level and shuffled-day on the ordered pair), capacity, the 1-s / 3-s delay, per session; the leave-the-second-out control (is the OB adding over the FVG alone?). Report DS3_CONFIRM_COMBOS_FINAL.md with the Sunday-style table.

4. KB regime tools (the only KB items alive)
(a) KB with ER ≥ 0.2 (the C2 note) and KB with the TG-1 chop filter: as a gate and as the × 0.5 / × 1.5 sizer, per session, with the split; (b) KB book-lean skip (N1 e: imb10 sign run ≥ 5 / 15 min against the signal → skip): definition, thresholds, per session, placebo (shuffled book), chain; (c) the two together. Report DS3_KB_REGIME.md.

5. HM 15-s four-up-closes after a dip (C2: +1.1 L6M / +1.4 HOLD, killed by a 3-s delay)
Recover it or drop it: the rule at a 1-s decision with a resting limit at the fourth candle's open / mid (so latency does not matter), the 2-s and 3-s delays, per session; if nothing survives the 3-s delay on a market entry, say "drop". Report in DS3_CONFIRM_2.md addendum.

6. No-trade set: isolate the information
The re-target beat random levels (rank 1.00) but the box said most of the gain is "which signals fire and shorter targets". Controls that settle it: (a) the same fired signals with a FIXED 40-pt target (no level), (b) the same signals re-targeted to a random level at the same distance, (c) the 8 coded lines only (the live set) vs the 11, per line (which line carries it), (d) D = 10 / 15 / 20 / 30 with the 8 lines, (e) skip vs re-target vs half on the 8-line set, all recent-first with the stack line. Report DS3_ZONES_2_ADDENDUM.md; if the 8-line skip is not ≥ 0 in L6M and HOLD on the stack, say so in one line for the brief.

7. Stop-join forward A/B (LIVE_STOP_JOIN lead)
Write the forward register spec: Native vs JoinThenMarket alternating by day (odd/even) per book from Monday, the fill-vs-stop-level measurement (each trade's real stop), the n needed to separate 1.28 from 2.45 at 95% (state it), the weekly line in MORNING.md. No research run; a 1-page spec: FORWARD_STOP_AB.md.

8. Risk-off, halt-resume, quit-when-up — status
These were ordered yesterday and have not started. Start them now in that order with the remaining agent slots; each reports its first-stage table before the Sunday brief or says it will not make it.

9. Reporting
DS3_SUNDAY_BRIEF.md (rewritten every 4 h from 06:00Z Saturday): first table = section 1; then the ON / SHADOW / OFF tables with the D6 group / property / value; then the open questions. MORNING.md every 2 h.
