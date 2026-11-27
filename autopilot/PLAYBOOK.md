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

## CHANGES (counted): none.
