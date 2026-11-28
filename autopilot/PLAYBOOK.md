# PLAYBOOK v0.1 as implemented (W-DYNC, order 1723Z). 27 Nov ~18:05Z. FOURTH design; run ONCE as written; changes only if the tape review shows the LOGIC is wrong, each logged below with its reason.
Class code/th_dync/algo_playbook.py, class PLAYBOOK (extends MGMT: same vocabulary, vote logic, feed readers). Config for W-DYNH: code/th_dync/playbook_configs.json (manager block, feeds in dx_algo age1s / flow1s format, params per book: Asia MF1-3, NY AM MF1, MF2, MF4, MF5). Base: edge-beyond-drift book, bare entry, safety stop 1.5 x the book's own stop at entry, no fixed target.

## The numbers chosen where the playbook gave none (ONE value each, written here, never varied)
- MOVED = more than 1.0 of that instrument's own typical move (std of its changes over the previous 2 h, scaled by sqrt(horizon/60 s)); measured SINCE ENTRY for futures; last 5 minutes for stocks, ETFs, TICK, UW (their feeds carry windowed values).
- MAJORITY = more than half. "Voting screens" = screens with data in that session. "Most voting screens AGAINST" = more than half of the voting screens are AGAINST; "all" = every voting screen (at least 2).
- s5 = NQ's typical 5-minute move. WORKING = best open profit at least 2.0 s5. TRAIL = 2.0 s5 behind the best price; LOOSE trail 3.0 s5 when most voting screens are WITH; TIGHT 1.0 s5 after the half has been taken.
- A PART = one half of the open lots, rounded, at least one lot; with one lot a "take half" becomes "take all" (stated).
- "NQ dips" = open loss beyond 0.5 s5. "Meaningful peak" = best at least 1.0 s5.
- OBJECTIVE reference: the book's own old target distance T0 (tgt_ratio.json x the book's own stop); STALL = no new best for 1.5 x the time it took to reach the best (floor 30 s) once the best is at least 80% of T0; LEVEL AHEAD = a held liquidity pool (prior day/overnight high-low, swing, equal highs/lows, round-number/profile levels via W-DYNL pool state) closer than 0.5 s5; RANGE USED = the session's NQ range-to-date rank at least 0.8 vs the previous 20 sessions of the type at the same elapsed minute.
- CLOCK: N = minutes left to the session bell; distance wanted = T0 minus open profit; NQ covers sqrt(N) x its typical 1-minute move in N minutes.
- EVENT = a scheduled high-impact release within 5 minutes (calendar feed; absent today, so the rule is blind and says so).
- Decision every 15 s, order-change cap 6 per minute.

## THE EIGHT SCREENS (each votes WITH / AGAINST / NOTHING on the open trade; no valid member = ABSTAIN)
| # | screen | members as implemented | votes how | abstains when |
|---|---|---|---|---|
| 1 | NQ chart + clock | NQ move since entry | AGAINST if beyond -1.0 own move, WITH beyond +1.0 | never (clock enters through rule 5) |
| 2 | NQ tape / book | the 1-s adverse-flow flags (delta flip, absorption, book pulls, adverse wall, speed) | AGAINST if >= 3 of the 5 are adverse within 10 s; no WITH vote | feed missing for the month |
| 3 | ES, RTY, YM | quote mids (ES RTY), 1-min bars (YM) | majority of members | fewer than 1 valid |
| 4 | ZN ZB 6E 6J CL GC (+ NKD in Asia) | signs: ZN -, ZB - (bond rally is against a long), 6E +, 6J - (yen up is risk-off), CL +, GC -, NKD + | majority of valid members | none valid |
| 5 | internals | ^TICK (5-min mean vs its own 2-h behaviour, from 09:31 ET) | one member | Asia, London, any hour without TICK; ^TICKQ ^ADD ^UVOL ^DVOL have NO history on the box: not members |
| 6 | ^VIX, ^PCR | none on the box | | ALWAYS abstains (logged only when a live feed exists) |
| 7 | megacaps + ETFs | NVDA MSFT AAPL AMZN META GOOGL TSLA, QQQ, SPY (5-min); AVGO and ^NDX are not in the feed | majority of the nine | Asia, London (stocks bars exist only 04:00-20:00 ET, usable from the NY morning), history before 2024-10 |
| 8 | options flow / walls + calendar | UW QQQ ETF tide, net call minus put premium (5-min change, +120 s lag) | one member | Asia, London, before 2024-10; intraday walls only 9 days: not a member; calendar acts through rule 5 EVENT |
Screens with history per session (the voters): ASIA: 1, 2, 3, 4 (with NKD); 5-8 abstain. NY AM: 1, 2, 3, 4, 5, 7, 8; 6 abstains. NY PM / London: NOT READY on the age feed (no seconds outside Asia and NY AM): fallback inst1s closes for 3 and 4 only, to be health-tested.

## THE LIFE OF A TRADE (rule ids in the log)
1 JUST IN (safety stop only, best < 2.0 s5):
  J1 NQ dips and no other screen has moved (every other voting screen votes NOTHING or abstains) -> HOLD (logged).
  J2 most voting screens AGAINST before NQ has followed (screen 1 is not AGAINST) -> take half (once).
  J3 ALL voting screens AGAINST -> out.
2 WORKING (best >= 2.0 s5): stop to entry (rule NB / RT).
3 RUNNING (no target):
  R1 trail 2.0 s5 behind the best price (ratchet); WITH votes of most voting screens -> loose trail 3.0 s5 (RT).
  R2 two screens AGAINST -> take half and tighten the trail to 1.0 s5.
  R3 most voting screens AGAINST -> take all.
  R4 NQ makes a new best that neither the leaders (screen 3) NOR the internals (screen 5) confirm WITH -> take all. Needs both screens voting: it abstains in Asia (no internals).
4 AT AN OBJECTIVE (open profit >= 1.0 s5): O1 stall after most of the move; O2 a held level just ahead (prior high/low, round number, profile level; option wall when it exists); O3 session range used up -> take all.
5 CLOCK: C5 the bell closes the trade in N minutes and the distance still wanted exceeds what NQ covers in N minutes -> take all now. N3 one minute left in profit -> all. EV a scheduled release in 5 minutes: winner -> tighten to best - 1.0 s5; not working -> flat (calendar feed absent today).
6 AFTER EXIT: no re-entry of the same idea while the screens are still AGAINST it: method PLAYBOOK.snapshot(F, sec, side) returns True while a majority of the voting screens is AGAINST that side over the last 5 minutes; W-DYNH's re-entry gate (policy L3) calls it at the new signal and blocks the entry when True. Not part of the first rows unless W-DYNH wires the gate.
NEVER BEND: (i) once the best reached 80% of T0 the stop is at least entry (rule NB); (ii) once the peak is meaningful (>= 1.0 s5) the stop is at least half the peak (rule NB); (iii) no open profit into a forced close (N3, C5).

## SHADOW LOG (one line per decision / every 60 s, tab separated): ts_epoch | book | trade_id (entry sec + side) | PLAYBOOK | stage | open_s5 | best_s5 | votes "1:A 2:N 3:W 4:N 5:abs 6:abs 7:A 8:W" (A against, W with, N nothing, abs abstain) | n_against/n_voting | n_with/n_voting | members "NQ:-1.3,ES:-1.1,..." (own-move units, na = stale) | rule | action | frac | stop_to_R | reason | order_changes_last_min.

## SANITY (not a result; 20 safety-stop-only trades per book, first-fire shares per trade, Asia MF1 / NY AM MF5)
C5 55% / 15%, O3 15% / 20%, NB 25% / 30%, RT 25% / 10%, R2 5% / 5%, O1 5% / 15%; J3, J2, R3, R4 did not fire in this sample; no errors; 0 blind decisions. Watch items (stated, not changed): the 1-minute series in Asia (ZB, 6E, 6J) often show a since-entry z of 0.0 (no new bar since entry): they rarely vote; C5 fires on over half the Asia winners on a hold-to-session-end path.

## SIDE ROW: health vote (v0.2h) -- NOT the headline; the core above stays the eight screens, UNCHANGED (order 1736Z; pre-result amendment of 1733Z logged here)
v0.2h = PLAYBOOK v0.1 + a NINTH vote "the trade's own health", one set per book, a side row only. Class: the same PLAYBOOK class, param health true (default false: the core is untouched); config for W-DYNH: code/th_dync/playbook_configs_v02h.json (params_v02h per book; also params_timecut for the reference row). Same manager path.
The vote (measured against THIS BOOK'S OWN PRIOR WINNERS, causal: winners whose exit is before this trade's entry, expanding window, minimum 30 winners else the screen abstains; no free thresholds): MAE: deeper against than 90% of the book's winners ever went (R units of the trade's own stop) -> AGAINST; TIME UNDER WATER: under water longer than 90% of those winners ever were -> AGAINST; MFE by minute: the best open profit so far is below the 25th percentile of the winners' best at this minute -> AGAINST, above the median -> WITH. The screen votes AGAINST when at least two of the three measures are against; WITH when the MFE measure is WITH and no measure is against; else NOTHING. It counts like any screen in J2/J3/R2/R3 and never cuts alone. The hook's best_px, worst_px and uw_s are used when given (else the manager's own 15-s tracking).
Winner = a live-book trade that ended with a positive result (engine pts > 0), NQ 1-s path from instr_1s. Percentile table (all winners, whole history; the class uses the causal prefix) file code/th_dync/health_winners.npz (keys '<mix>_<book>_{exit,mae,tuw,mfe}', build_health_table.py):
| book | winners (n) | MAE p90 (R) | time under water p90 (s) | MFE at 10 min p25 / p50 (R) |
|---|---|---|---|---|
| AS MF1 | 904 | 0.75 | 8019 | 0.09 / 0.22 (minute 10) |
| AS MF2 | 327 | 0.50 | 6510 | 0.08 / 0.17 (minute 10) |
| AS MF3 | 1561 | 0.69 | 4421 | 0.13 / 0.32 (minute 10) |
| AS MF4 | 511 | 0.57 | 2389 | 0.14 / 0.38 (minute 10) |
| NY MF1 | 888 | 0.66 | 2669 | 0.15 / 0.31 (minute 10) |
| NY MF2 | 988 | 0.80 | 1501 | 0.38 / 0.70 (minute 10) |
| NY MF3 | 520 | 0.69 | 3438 | 0.17 / 0.35 (minute 10) |
| NY MF4 | 2313 | 0.64 | 1251 | 0.24 / 0.33 (minute 10) |
| NY MF5 | 1336 | 0.75 | 1507 | 0.34 / 0.67 (minute 10) |
| NY MF6 | 2027 | 0.60 | 1453 | 0.19 / 0.32 (minute 10) |
| NY MF7 | 544 | 0.59 | 2691 | 0.10 / 0.22 (minute 10) |
| NY MF8 | 609 | 0.66 | 1742 | 0.24 / 0.45 (minute 10) |
| NY MF9 | 441 | 0.62 | 2009 | 0.18 / 0.32 (minute 10) |
Counts: every book has more than 300 winners over the 42 months (enough for stable percentiles); the early part of the history is thin: the first weeks of 2023-04 have fewer than 30 prior winners and the vote abstains (health 'abs' in the log). The smallest books: Asia MF2 327, NY MF9 441, Asia MF4 511, NY MF3 520.
REFERENCE ROW (not a candidate): the BLIND PERCENTILE TIME CUT: param mode 'blind_time': the same time-under-water percentile acting ALONE: leave when the trade has been under water longer than 90% of the book's prior winners ever were; nothing else but the safety stop (config params_timecut; reference row algoR_timecut_pctile). Sanity (20 trades per book, safety-stop-only walks): it would fire on 30% (Asia MF1) / 10% (NY AM MF5) of trades.
RULE 6 reference: v0.2h is run with the re-entry gate (PLAYBOOK.snapshot) and a reference row WITHOUT the gate (v0.1h in W-DYNH's naming) so slot effects can be shown with and without rule 6; the manager is the same, the gate lives in the hook.
Sanity of the health vote (not a result): the vote returns N or W in the sample, A never in 20 trades per book; logged in the shadow line as 'health:mae x/p90 tuw x/p90 mfe x/p25'.

## CHANGES (counted): 1. PRE-RESULT: side row v0.2h (health vote) and the blind time-cut reference row added; core unchanged.

## CALENDAR-AWARE VERSION v0.3c (pre-result amendment 18:30Z; the core v0.1 rows already queued stay calendar-blind and are not touched)
v0.3c = core v0.1 + calendar rules, param cal true, ONE version run ONCE after the core replays (not searched). Reads feeds/calendar_<YYYY-MM>.parquet. EVENT rule (rule 5 pre-release): a high-importance release within 5 minutes (nxt_hi_min <= 5): winner (best >= 1.0 s5) -> stop to best - 1.0 s5; not working -> flat. Inside the window (5 min before to 5 min after a high-importance release) the vote rules and the objective/clock rules are suspended (winners keep their stop, the never-bend floors stay). Early-close day: the bell for the clock rule and the one-minute backstop is 13:00 ET. Holiday, opex, month/quarter end, roll week: context only. Config code/th_dync/playbook_configs_v03c.json.
LONDON / NY PM books added to playbook_configs.json (ready=false: the age feed has no seconds outside Asia and NY AM; inst1s trade-close fallback for NQ ES RTY ZN CL GC; sets with > 5% missing-feature minutes are data-starved): London MF1 (LO-CRUDE, tgt_ratio 0.333 = 90/30), London MF3 (LO-ZB, 0.5 = 120/60), NY PM MF2 (NP-ZN, 1.0), NY PM MF3 (NP-YM, 0.5 = 80/40). No range table / time-to-target / winners history there: O3, the stuck-loser rule and the health vote abstain.
## CHANGES (counted): 2. PRE-RESULT: v0.3c calendar-aware version; London/NY PM books and tgt_ratio keys. Core unchanged.

# PLAYBOOK v0.2 = DESK MANAGER v0.2 (order 2030Z): REPLACES v0.1 as the fourth design. Design change made before any v0.1 result was read by the relay (v0.1 rows already finished stay labelled v0.1; unstarted v0.1 rows voided and requeued as v0.2).
Class code/th_dync/algo_desk.py, class DESK (extends PLAYBOOK/MGMT machinery). Config for W-DYNH: code/th_dync/desk_configs.json (books: Asia MF1-3, NY AM MF1, MF2, MF4, MF5, London MF1 and MF3, NY PM MF2 and MF3; each with params_desk and params_desk_risk). Entry gate: code/th_dync/desk_gate.py. Run ONCE as written.
## Numbers chosen (ONE value each, never varied)
- MOVED = 1.0 of an instrument's own typical move (std of its changes over the previous 2 h, scaled by sqrt(horizon/60 s)): since entry for futures, last 5 minutes for stocks/ETFs/TICK/UW. MAJORITY = more than half of a seat's members. s5 = NQ's typical 5-minute move.
- UNIT = the book's own stop x 0.25. PROBATION until best open >= 1 unit; CONFIRMED (undefined in the order: chosen: the probation rules still apply) from 1 to 2 units; FREE TRADE from 2 units (stop to entry); RUNNER = FREE with at least one confirmed swing (structure trail available).
- SWING (S1): on NQ 1-minute closes since entry in the trade's frame: a swing against the trade = a close beyond the 2 closes on each side, confirmed 2 minutes later. Structure trail = the last swing level minus 0.1 s5; PRESS uses the swing before the last (skips one); after a DEFEND third, the nearest swing. Never looser than giving back half the peak.
- Seat members: S1 = swing structure (broken beyond the last swing = AGAINST; higher lows and above = WITH), session VWAP side (beyond 1 s5 = WITH / AGAINST; levels feed), 5-minute pace (beyond 1.0 of its own move); S2 = the 1-s adverse-flow flags (>= 3 of the 5 components within 10 s = AGAINST; no WITH side); S3 = ES RTY YM (+NKD in Asia) since entry, + ^TICK in NY; ^TICKQ ^ADD ^UVOL ^DVOL and cash ^NDX have no history on the box: not members; S4 = NVDA MSFT AAPL AMZN META GOOGL TSLA QQQ SPY (NY only; AVGO not in the feed); S5 = ZN(-) ZB(-) 6J(-) 6E(+) CL(+) GC(-), ^VIX ^PCR no history; S6 = UW QQQ tide (NY); option walls: intraday history only 9 days: not a member; calendar and the bell act through rules, not votes.
- CONVICTION = voting seats WITH minus AGAINST; PRESS >= +2, DEFEND <= -2, NORMAL otherwise; ABORT = every voting seat AGAINST (at least 3 voting) or S1 and S2 both AGAINST with nobody WITH. Fewer than 3 voting seats: FALLBACK = S1 + never-bend only.
- Take half = one half of the open lots rounded, at least 1 lot; with ONE lot a 'take half' / 'take a third' cannot be done: it becomes a structure-trail tightening only (the second objective and ABORT still take all).
- Objectives (in profit, best >= 1 unit): stall = no new best for 3 x the time the last unit took (floor 30 s); prior high/low = pdh pdl onh onl rth_hi rth_lo (levels feed) within 0.5 s5 ahead; round number = the next multiple of 100 NQ points within 0.5 s5 ahead; wall = the adverse-wall flag within 10 s (S2); liquidity level = W-DYNL pool ahead within 0.5 s5; session range used = rank >= 0.8 (range_table.json). First distinct objective -> half; second -> all; posture DEFEND -> all at once.
- Divergence: NQ makes a new best (>= 2 units) while no voting seat among S3 and S4 is WITH.
- Clock: distance wanted = old target distance T0 (tgt_ratio x the book's stop) minus open profit; exceeds sqrt(N) x NQ's typical 1-minute move -> take all. One minute left in profit -> all. 2 minutes before a top-tier release (cal true only): stop to structure.
- Never bend: (i) best >= 0.9 x T0 -> stop at entry; (ii) best >= 2 units -> stop at least half the peak; (iii) broker safety stop = 1.5 x the book's stop always live; (iv) only reduces risk.
- ENTRY GATE (desk_gate.py): late-entry = time left to the session bell <= the median holding time of the book's PRIOR winners (causal, >= 30 winners else pass); calendar blackout = 5 minutes before to 5 minutes after a top-tier release (calendar feed); stand-down = W-DYNH's reentry mode exit_level_or_15m. Session ends: Asia 02:00 ET, London 08:30, NY AM 12:00, NY PM 17:00.
- RISK SEAT: after two managed exits at a loss in a row in a session the book stands down for that session; DESK.stand_down(sec) for the hook; rows with (params_desk_risk) and without (params_desk) as separate sets.
## Seats that vote per session (the abstainers)
ASIA: S1 S2 S3 (+NKD) S5; abstain S4 S6 (and the VIX/PCR members of S5). LONDON: S1 S2 S3 S5 on the inst1s fallback (not ready until the health check); S4 S6 abstain. NY AM: S1 S2 S3 (+TICK) S4 S5 S6; S5 without VIX/PCR. NY PM: as NY AM on the fallback feed (not ready). A stale feed abstains (feed's stale_s).
## Shadow log line: epoch s | book | trade_id | state (PROBATION CONFIRMED FREE RUNNER OUT FALLBACK) | posture | votes "S1:N S2:A S3:W S4:abs S5:N S6:abs" | conviction/voting seats | rule | action | frac | price | reason.
## Sanity (not a result; 15 safety-stop-only trades per book, first-fire shares per trade, Asia MF1 / NY AM MF5): DF 20% / 27%, AB 13% / 7%, DV 27% / 13%, OB1 40% / 60%, OB2 20% / 47%, CL 33% / 0%; no errors. Entry gate sample (200 events per book): the late-entry rule blocks 161 of 200 Asia MF1 and 25 of 200 NY AM MF5 signals: the median winner holding time of Asia MF1 is long (winners include session-end exits): stated, not changed; the gate's counts go into the report.
## CHANGES (counted): 3. Design change made before any v0.1 result was read by the relay: v0.1 replaced by DESK v0.2 (rows: v0.1 finished kept and labelled; unstarted voided).

## CHANGES (counted): 4. v0.2.1: clock rule only within 30 minutes of the session bell ('one minute left in profit -> all' unchanged); reason: logic error in the clock rule (it fired from the first minutes of the session on the wide books: autopilot/DESK_CLOCK_FIRING.md). Nothing else changed. The v0.2 rows stay labelled v0.2.

## DESK v0.2.2 (change no. 5, reason 'defects found while writing the match file'; order 2342Z; relay decisions on the four defects)
Class DESK param v022 true (default false = v0.2.1 exactly: identity tested on the six match trades). Config code/th_dync/desk_configs_v022.json (params_desk and params_desk_risk: v022 true, clock_max_min 30). (1) POINTS: best open profit, 1-minute bars (swing levels), the managed stop and the unit are kept in points; s5 is applied at the moment of comparison at its current value; stages only move forward. (2) 1 lot (or no part possible) first objective: stop to the nearest swing (swing - 0.1 s5) or half the peak, whichever is tighter (ratchet only); second objective takes all. (3) Staleness judged on the quote's age column (age + seconds since the row <= the feed limit: NQ/ES/RTY mids 5 s, YM NKD 6J 6E ZB 1-min closes 150 s, ZN CL GC last trades 60 s); older = the member abstains. (4) FALLBACK unchanged. v0.2.1 and v0.2 rows stay labelled.
## CHANGES (counted): 5. v0.2.2: defects found while writing the match file (units drift, one-lot first objective, stale-feed test, forward-only stages); see DESK_V02_MATCH.md.

## DESK v0.3 (change no. 6, POST-RESULT; reason: the same-trade counts show the profit-side rules cut more winners than they save (NY AM: losers cut early +$8.08M, made worse -$0.80M; give-backs prevented +$3.62M, winners cut short -$8.32M); order 0322Z items 3-4)
ONE design, replayed once. THE BOOK KEEPS ITS OWN TARGET; the desk manages the LOSS SIDE and the CLOCK only. Class DESK param v03 true (v022 true; default false = v0.2.2 exactly: identity tested on the six match trades). Config code/th_dync/desk_configs_v03.json.
- Entry gate unchanged (late-entry, calendar blackout, stand-down). Stop at entry = the BOOK'S OWN stop (manager param safety_mult 1.0: the hook gives the trade the events' own stop_pts and own tgt_pts; the desk may only make the loss smaller). Reference row DK3W (not a candidate): the same with the 1.5x safety stop (params_desk_w, safety_mult 1.5).
- Acts only while the trade is under water or has not yet reached 1 unit (unit = own stop x 0.25) and at least three seats vote: DEFEND -> take half (once, also after a peak when the trade is back under water); ABORT -> out. FALLBACK (< 3 seats): no seat-driven action.
- Profit side: NO free-trade stop to entry, NO half-the-peak, NO structure trail, NO objectives, NO divergence exit, NO DEFEND third, no calendar tightening. Only (i) never-bend: best >= 0.9 x the book's own target distance (tgt_ratio x own stop) -> stop to entry; and the clock rule (v0.2.1: only within 30 minutes of the bell: distance still wanted > what NQ covers in the minutes left -> take it now; one minute left in profit -> all).
- Risk seat with / without as before (params_desk_risk / params_desk).
- Windows: Asia and London 2023-09..2026-10, NY AM / NY PM 2024-10..2026-10.
## CHANGES (counted): 6. v0.3: post-result; the book keeps its own target and the desk keeps only the loss side, never-bend (i) and the 30-minute clock (reason above).
