# INCUBATION - how a D7 rule goes from Shadow to Live (owner W-DV; research only; FIRST PASS written 2026-11-16 ~20:30Z; fixed IN ADVANCE, edits only by dated amendment below)

VERDICT (data ends 2026-10-31; engine statistics from the exact engine on JL2 over HOLD+L6M, 52 weeks; no live Shadow event scored yet): this page fixes the metric, the event count, the go and drop thresholds and the scoring procedure for every Shadow switch in D7 v2.0 before any live Shadow line is read. Validation: trials = see TRIALS_LEDGER.csv (TB-k give-back N 135, TB-d against-the-day N 60, M7L N 258); correction = White RC / SPA / DSR (DV_FAMILY_SNOOP.csv): none of the three families is significant after snooping (give-back RC p .85, DSR .06 at N 135; M7 London / re-entry RC p .88, DSR .04 at N 258; against-the-day RC p .67), PBO 0.29-0.59 on 52 weeks (S 12/14/16; weak read); numbers shown are IN-SAMPLE engine statistics.

## 0. Rule that governs everything
**No rule moves Shadow -> Live on research alone unless it is CONFIRMED under the calibrated rule (DS3_PASS_RULE.md, W-PR2).** Incubation evidence below is NECESSARY, never sufficient: a switch goes Live only when (a) CONFIRMED under the calibrated rule on the then-current data, and (b) the incubation GO conditions below hold, and (c) the lead and the user decide. A switch that is not CONFIRMED stays in Shadow or is dropped, however good its shadow lines look. Shadow has two jobs: FIDELITY (does the live code do what the engine says) and NON-INFERIORITY / evidence (is the live per-event effect consistent with the engine). It cannot discover significance for low-rate rules in a few months (table 2 shows why).

## 1. The Shadow switches in D7 v2.0 (DS7.cs defaults, group 18; INSTALL.md)
| switch | live default setting | what the Shadow line prints (exact format in DS7.cs) |
|--|--|--|
| M7 LONDON CAP | Shadow, N = 3 | `<time> M7 SHADOW v1.9 M7-LONDON-CAP: <n> closed M7 trades this London session (cap 3) -> would be skipped` |
| GIVE-BACK EXIT | Shadow, `H7:asia:0.60:30;H7:nyam:0.40:40;K7:nyam:0.40:40;P7:asia:0.50:40;P7:nyam:0.40:30` | `<time> <book> SHADOW v2.0 GIVE-BACK at <unreal> pts: best was +<best> (rule: best >= B and gave back F%) -> would exit` |
| AGAINST-THE-DAY TARGET | Shadow, `M7:nyam:20;O7:nyam:20` | `<time> <book> SHADOW v2.0 AGAINST-THE-DAY: LONG\|SHORT against a UP\|DOWN day (<vote detail>) -> target 20 pts (would be; stays 59.5)` |
In Shadow the trade is still taken and still exits by its live rules, so the live fills.csv gives the actual outcome of every event; the counterfactual is computed from the Shadow line plus the 1-s tape (below).

## 2. Engine prediction per switch (what the engine says the same rule does; JL2, HOLD+L6M, 52 weeks, BASE lots at $4.84 per contract; x1.75 for live lots)
Event = one affected trade. Advantage per event = $ the rule would have added (+) or cost (-) on that trade. sd = standard deviation across events. N for significance = events needed for the lower end of a 90% interval to clear 0 if the true mean equals the engine mean: (1.28 x sd / mean)^2, with the mean floored at $100 per event; weeks = N / rate.
| switch / line | engine events per week | engine mean advantage $/event | sd $/event | N for significance (weeks) | go path |
|--|--|--|--|--|--|
| M7 London cap 3 (blocked trades; 289 events in 52 wk; also 89 replacement trades the cap lets in, which Shadow cannot see) | 5.6 | +200 | 1,149 | 54 (10 wk) | SIGNIFICANCE track |
| give-back H7 asia 60% / 30 | 1.87 | -21 | 1,974 | none (mean <= 0) | none: engine does not support it |
| give-back H7 nyam 40% / 40 | 0.54 | +125 | 1,104 | 128 (237 wk) | NON-INFERIORITY + fidelity only |
| give-back K7 nyam 40% / 40 | 2.62 | +150 | 997 | 72 (27 wk) | SIGNIFICANCE track (borderline in the horizon) |
| give-back P7 asia 50% / 40 | 4.63 | -373 | 2,705 | none (mean <= 0) | none; early-drop track |
| give-back P7 nyam 40% / 30 | 0.62 | -171 | 1,469 | none (mean <= 0) | none |
| against-the-day M7 nyam T20 and O7 nyam T20 | 0 (engine changes 0 of 7,380 trades in 52 wk) | 0 | n/a | n/a | any live print is a FIDELITY FAILURE to investigate, not evidence |
Whole-stack effect (path effects, freed-book replacements, drawdown) is NOT measurable from Shadow lines; it comes only from the exact engine under the calibrated rule. DS3_BRACKET_DD_BUILD.md already shows that the engine stack DD effect of these three families is small or not beating controls; this is why (a) above is required.

## 3. Metrics, counts and thresholds (fixed now)
Primary metric P (per switch): mean advantage per event at $4.84, week-clustered bootstrap (4,000 resamples of calendar weeks, 90% interval), counterfactual computed as below. Fidelity metric F: share of live Shadow events that have an engine event for the same book within 60 s (F_live) and share of engine events in the same period that have a live Shadow event (F_engine); also the live mid (unreal) vs engine exit price gap at the event for give-back (median |gap| in points).
Counterfactual per event (code/th_validate/incubation_score.py `advantage`): M7 cap = minus the actual net of the trade that was taken in Shadow (blocking removes it); give-back = (unreal at the Shadow second - actual final points) x $20; against-the-day = (T - final points) x $20 if the 1-s tape shows the trade reached +T before its actual exit, else 0 (the line also needs the tape path: entry to exit from the state files).
| | GO (all must hold, plus section 0) | DROP / QUARANTINE |
|--|--|--|
| SIGNIFICANCE track (M7 cap; K7 nyam give-back) | events >= N_go = max(60, engine N) AND at least 8 weeks of events (K7 nyam: 72 events); P > 0 with the lower end of the 90% interval > 0; P >= 50% of the engine mean; F_live >= 0.80 and F_engine >= 0.80 | DROP when events >= 30 and the upper end of the 90% interval < 0; or when week 30 passes without GO. QUARANTINE (not a drop of the idea) when F_live < 0.50 or F_engine < 0.50 at >= 10 events: live and engine definitions differ; fix the code or the engine, restart the count |
| NON-INFERIORITY + fidelity track (H7 nyam give-back) | events >= 10 AND at least 12 weeks; lower end of the 90% interval > -$150/event (not worse than the claimed effect size); F_live and F_engine >= 0.80 | DROP when events >= 10 and the upper end < 0; time-out week 40 |
| no go path (engine mean <= 0: H7 asia, P7 asia, P7 nyam give-back) | none; stays Shadow for fidelity and for the engine's own recheck on new weeks; moves to a go track only if a later engine / calibrated-rule re-score turns the mean positive | DROP when events >= 30 and the upper end of the 90% interval < 0, or at week 30 |
| against-the-day (M7 nyam, O7 nyam) | none until the engine itself shows events with a positive effect; Shadow only checks the 3-of-4 vote | any live print while the engine predicts none: record the vote detail and compare the engine day-direction function; QUARANTINE until resolved |
Why these numbers: the engine sds make significance reachable only for the M7 cap (about 10 weeks) and K7 nyam give-back (about 27 weeks); for the rest a 6-month shadow cannot show a profit, so the realistic Shadow job there is fidelity plus non-inferiority, and the decision rests on the calibrated rule. The margin $150 is about the size of the engine means being claimed (125-150), so a line that loses more than it claims to gain is not allowed through.

## 4. Scoring procedure each morning (research only, no live change)
1. Inputs: the previous night's NT8 Output (saved nightly to incoming/d6_output_YYYYMMDD.txt per the brief) and fills.csv; log clock = NT8 PC local time (confirm against fills.csv timestamps on day 1; if it is not Eastern, correct).
2. `incubation_score.parse_log(text)` extracts the three Shadow line types into events (type, time, book tag, fields); lines that do not match the formats above are counted and listed (a format change in DS7.cs must be reported).
3. Outcomes: for each event find the trade in fills.csv (book tag, entry before the event time and exit after) and price it at $4.84 per contract; for give-back and against-the-day add the 1-s NQ path from entry to exit (state files, same loader as the replay) to get final points, MFE, and the $ counterfactual by `advantage`.
4. Engine prediction for the same trades: run the exact engine (admission files only: PRIORITY.txt append with backup / _s2/QUEUES.txt) on the same dates for JL2 and for the candidate cell with the rule Live (cells exist for the three families: TL3_RA_JL2_M7L_CAP3, TL3_D10_..._gbFFBnn, ..._ddvote_w_aT20); engine events = trades blocked (cap), trades with exit D10GiveBack (give-back), trades whose exit differs (against-the-day). Where the engine lags the live date (engine data end), use the literal DS7.cs replica (code/replica) on the raw feed for the event list and run the engine later. Match live events to engine events by book and time within 60 s; one row per event: live yes/no, engine yes/no, live mid vs engine price, advantage live-computed vs engine-computed.
5. Per day append to a table (autopilot/INCUBATION_LOG.csv, append-only): date, switch/line, events live, events engine, matched, F_live, F_engine, sum advantage live, sum advantage engine. Cumulative statistics (events, P, 90% week-clustered interval, F) are recomputed from the log, never edited.
6. Weekly (Mondays): one paragraph per switch against the table in section 3: events to date, P and interval, F, status (running / GO-eligible / quarantine / drop). A GO-eligible status is reported to the lead with the calibrated-rule status of the rule; the lead and user decide; nothing is switched by research.
7. Any event with a live-engine mismatch is listed with its vote detail or tick data so the DS7.cs reading (given in the INSTALL notes as "MY READING": give-back evaluated once a second on the book mid; session-block boundaries for the day vote; the 60-minute-earlier bar) can be corrected.
8. Overlap rule: events from the same trade for two switches are scored once per switch, never summed across switches.

## 5. Other Shadow-default switches in DS7.cs (not in the v2.0 INSTALL text; found in the defaults block; second tier, lead to confirm)
| switch | default | note |
|--|--|--|
| FLIP-LEVEL zone line (v1.4) | Shadow, reach 40 / break 10 / 4 h | box: MEAN-type lead, Shadow only; logs forward_register\bt_flip_shadow.csv; score per event: would-be action vs actual |
| signal-state rules Ss1-Ss4 (group 14) | Shadow: H7 slope skip bottom third; K7 ST1 distance skip top third; P7 ST1 distance size-hi; H7 ST1 distance skip bottom third | engine "removing all three was +8.3k/wk" noted in the DS7.cs header; each needs its own table here before any Live |
| FED blackout (group 13) | Shadow, dates typed in the panel | paper log of skipped signals; outcome = actual trade result of each |
| alt-bar slots X1-X5 | Off since v2.0 | no Shadow output |
| NKD near-zone take, DAY-DONE, BREADTH, JN04 layers, ATR-SKIP, post-stop blackout | Live (not Shadow) | out of scope here |
Second-tier switches use the same generic protocol (metric = advantage per event, N_go from the engine sd of that rule, same thresholds, section 0 applies); their engine statistics are to be added by dated amendment when W-PR2 / the lead lists them; nothing here sets a go threshold for them yet.

## 6. Amendments (append only)
- 2026-11-16 ~20:30Z W-DV: first version. Engine statistics from this page's computation on JL2 H12 (run dirs TL3_RA_JL2_M7L_CAP3 and the five TL3_D10_..._gb cells; blocked-trade key = book + signal ns).
