# V19_SPEC_E1 - WG_E1 / WL_E1 as scored (W-C, 2026-11-12 13:2xZ; Shadow only, no PASS claim)
Code: code/th_works_c/c_gov.py (engine hook, runs in try_entry and trend_size of the replica engine) with grammar and features in code/th_works_c/gov_lib.py. Rule list as scored (set json hooks.par.gov): `[{"when": {"sess": [0,1,3,4], "loss_same_ge": 2, "noevid": 1}, "act": "skip"}]`.

## What the rule does, in code terms
1. Book: P7 only (gov_book = "P7"). History is the engine's own P7 trades of this run (closed trades appended at exit); a skipped signal leaves no history.
2. Session scope: key = (trading date with the 18:00 ET roll, ET session index of the SIGNAL second): asia 18:00-01:59, london 02:00-08:29, pre 08:30-09:29, nyam 09:30-11:59, nypm 12:00-14:59, close 15:00+. The rule is active in asia, london, nyam, nypm (pre/close carry no P7 lots in the panel). A trade belongs to the session of its signal second; the run resets at every new session key.
3. Loser: trade net P&L < 0, net of the $4.84/contract round-trip fee (engine net_fee). A StateCut, stop or any other exit all count; a scratch that is +$1 gross but negative after fees counts as a loser.
4. Run: counted over the CLOSED trades of the session (exit second <= signal second), walking back from the last closed trade: consecutive same-side losers. Any winner, or any opposite-side trade, ends the count. loss_same_ge 2 therefore means: the two most recent closed trades of the session are same-side losers (this entry would be the 3rd same-side attempt).
5. New evidence (noevid = 0) when ANY of: (a) an opposite-side P7 entry was taken between the last failure's exit and this signal (open or closed); (b) the session extreme in the trade direction at the signal second is strictly beyond the extreme at the failed trade's exit second. noevid = 1 (rule fires, signal skipped) otherwise; if no bar of the session exists at either second the evidence is treated as absent.
6. Session extreme series: NQ 1-minute bars (roll-adjusted, instr 1-min file), running max of bar HIGH (long) / min of bar LOW (short) inside the session key, using only bars whose END is <= the second being asked (last completed bar, staleness <= 15 min). Not 1-s, not tick, not mid. The current price is NOT added: a P7 signal fires at the 1-minute bar close, so the last completed bar already contains the signal price; the only gap is the 45-s confirmation window.
7. Decision second: the P7 signal second (try_entry, before the confirmation / L2 arm / sizing). Action skip = signal dropped (not queued).

## The user's reading versus as scored
| element | user reading | as scored | verdict |
|---|---|---|---|
| loser | trade P&L < 0 | net P&L after fees < 0 | SAME (state: net of fees) |
| run reset: same-side winner | yes | yes (run walks back and stops at a winner) | SAME |
| run reset: opposite-side entry of the book | yes | an opposite trade that has closed ends the run; an opposite trade between the failure and the signal (even still open) counts as new evidence, so the entry is allowed in both cases | SAME in effect |
| run reset: new session | yes | yes (session key) | SAME |
| session clock | six-session clock | six-session ET clock with the 18:00 ET trading-date roll; pre and close not governed | SAME (P7 has no lots in pre/close) |
| session extreme | 1-min bar highs/lows of the six-session clock plus the current price | 1-min completed-bar highs/lows, strict >, compared between the failure exit second and the signal second; current price not added | DIFFERENT in detail: add max(bar extreme, live price) and expected effect null (signal fires at bar close) except inside the 45-s confirm window. Not run as WG_E1V19; say if you want it run exact |
| rule scope | not stated | P7 only | for K7/M7/P7+K7+M7 see WG_E1K / WG_E1M / WG_E1ALL (running) |
| second-attempt size | not in E1 | no size change (WG_E5 tested "2nd half": inside noise) | n/a |

## 5 worked rows (real P7 trades of LPB_BASE; the entry in the last line of each block is the 3rd same-side attempt without new evidence; WL_E1 skipped it in every case)
1. Session 2026-06-07 asia, long: 18:34:01 4 lots StateCut -$2,597; 18:49:00 4 lots StateCut -$3,959; 19:08:00 would be the 3rd long (run 2, session high at the failure exit 29,634.00, at the signal 29,634.00, no new high, no short entry): it lost -$2,529 (StateCut 19:17:36). Skipped.
2. Session 2026-07-08 london, short: 05:22:00 2 lots StateCut -$1,679; 06:02:01 4 lots (bigger second attempt) -$3,449; 07:08:00 2 lots would be the 3rd: no new low (29,203.00 both), result StopJoin -$2,342. Skipped.
3. Session 2026-08-03 london, short: 03:02:02 2 lots -$1,654; 03:18:00 2 lots -$1,649; 03:37:00 1 lot, no new low (28,857.00 both): result Target +$1,199. Skipped (a winner given up; the rule is blind to outcome).
4. Session 2026-08-21 nyam, short: 10:02:00 4 lots -$3,154; 10:13:00 2 lots -$1,534; 11:21:00 1 lot no new low (29,513.25) result StateCut -$787. Skipped.
5. Session 2026-10-14 asia, short: 20:00:00 7 lots -$3,409; 20:15:00 4 lots -$1,769; 21:08:00 4 lots, no new low (29,879.50) result StateCut -$2,469. Skipped.
Aggregate as scored: over 3.5 years LPB_BASE has 90 such 3rd-or-later attempts without evidence (53 of them losers, -$11.4k in the P7 stack list); WL_E1 removes them all.
