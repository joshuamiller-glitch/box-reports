# V19_SPEC_C22 - code-level definition of S6 C22 AS SCORED (W-S, written 2026-11-12 13:11Z)

Shadow only, no PASS claim. Source of truth: code/th_screens/scr_hooks.py (feature `conj`, exact engine hook) and scr_s6x.py (first-order replay). Set names: JN05W_S6_C22 (live panel base) and JN05W_S6_C22_RM (JN04RM).

## Verdict on the user reading: SAME, with two points to state in v1.9 and one variant run for the third
User reading: C22 = sum of all books trades today >= 22 AND sum of day P&L <= -$2,400, reset at 18:00 ET. As scored it is the same rule: all books, realised net P&L, threshold -$2,400 (= -2 R, R = $1,200 fixed dollars), reset at the market-closed hour. Differences that exist:
1. Reset clock. The scored label day rolls at 17:00 ET (instr2_eval convention: ET + 7 h; Saturday/Sunday roll to Monday), not 18:00 ET. Checked on all 20,807 LPB_BASE trades: 0 closes and 0 entry signals fall between 17:00 and 18:00 ET (flatten is 16:55, CME halt 17:00-18:00), and 0 trades get a different label day under an 18:00 roll. So 17:00 and 18:00 give identical results; in v1.9 either may be used. Sunday-evening and Friday-evening trades after the roll belong to the next business day (Mon).
2. What "trades" counts. As scored: CLOSED trade records of the day (one record per position exit, any exit name, see below). The user reading could also mean trades OPENED today (including positions still open). The two differ only by open positions at the check time and by trades opened before the roll that close today. That variant is run as set JN05W_S6_C22V19 (count = entries): trades opened since the roll (closed or still open) >= 22 AND realised day P&L <= -$2,400. Results go to DS3_SURVIVORS_S6.md when its months are in.
3. P&L is REALISED only (closed trades), net of fees ($4.84 per contract round trip), never mark-to-market of open positions. If NT8 uses open P&L too the rule would fire earlier; that is not what was scored.

## Exact definition as scored (evaluated at every NEW ENTRY signal second, before sizing)
- Which closes count: every closed trade record of the exact engine trade list, all seven books (K7 P7 U7 M7 A7 H7 O7), every exit name: Target, StateCut, StackCut, Stop, StopJoin, StopJoinFallback, TimeBlock, BookLock, RollFlat, O7 time exit. In the 3.5-year LPB_BASE list: Target 9,190, StateCut 7,110, StopJoin 1,642, StopJoinFallback 1,024, Stop 867, StackCut 416, TimeBlock 352, BookLock 168, RollFlat 33, O7 time exit 5. Partial exits would each count as one record (ProfitScale is not in the live panel base, so none occur there). The record is created at the exit second; only records with exit second <= the signal second count.
- Which P&L: sum of the same records net_fee (= gross minus fees, in dollars, at the lots traded), realised only.
- Threshold: day P&L / 1,200 <= -2, i.e. day P&L <= -$2,400, inclusive. R = $1,200 = 60 points x $20 x 1 lot: a FIXED dollar amount that does not scale with lots, books or session.
- Day: label day = ET clock + 7 h, weekend dates rolled to Monday (17:00 ET roll). Counter and P&L both restart at the roll.
- Action: skip the new entry signal of ANY book (log line "SKIP signal: SCR gate conj"). Open positions, their exits, stops, cuts, locks, the 30% add of an already-open entry, and other layers (LOT, REG, STACK, 7/4/4, P7 day cap 8,400) are untouched. Once the rule is true for a day it stays true unless the P&L recovers above -$2,400 (a late winner closing re-opens entries).
- Position in the engine: top of the class stack, in try_entry, before the base entry logic; first-order replica (scr_s6x.py) uses the identical definition on the trade list.
- v1.9 inputs NT8 needs: its own closed-trade log with exit time, net P&L; a day-reset timer at 17:00 ET; two scalars (stack_day_n, stack_day_pnl) updated on each exit; one comparison at each entry signal.

## Five worked rows from real days (LPB_BASE exact trade list; every entry signal of the day shown from the first firing minus context; "SKIP" = would be blocked)

### Row 1: label day 20260909 - the rule skips 6 entries worth -3282 $ of base P&L (negative = losers avoided)
| signal time ET | book | side | lots | exit | trade net $ | stack closes before | stack day P&L before $ | rule fires (skip) |
|---|---|---|---|---|---|---|---|---|
| 09-09 06:45:00 | K7 | S | 2 | Target | +2393 | 18 | -6386 |  |
| 09-09 08:06:00 | M7 | S | 1 | StateCut | -625 | 19 | -7630 |  |
| 09-09 10:15:00 | K7 | L | 1 | StateCut | -1040 | 21 | -5862 |  |
| 09-09 10:24:00 | K7 | S | 1 | StopJoin | -1206 | 22 | -6902 | SKIP |
| 09-09 10:49:00 | M7 | L | 1 | StateCut | -817 | 23 | -8108 | SKIP |
| 09-09 11:09:00 | K7 | S | 1 | Target | +1199 | 24 | -8925 | SKIP |
| 09-09 11:24:00 | K7 | S | 1 | StateCut | -850 | 25 | -7726 | SKIP |
| 09-09 12:18:00 | K7 | S | 1 | StopJoin | -1201 | 26 | -8576 | SKIP |
| 09-09 13:03:00 | K7 | L | 1 | TimeBlock | -406 | 27 | -9777 | SKIP |

### Row 2: label day 20260625 - the rule skips 10 entries worth -2926 $ of base P&L (negative = losers avoided)
| signal time ET | book | side | lots | exit | trade net $ | stack closes before | stack day P&L before $ | rule fires (skip) |
|---|---|---|---|---|---|---|---|---|
| 06-25 06:42:00 | P7 | S | 4 | StateCut | -4314 | 21 | +459 |  |
| 06-25 07:24:00 | M7 | S | 1 | StateCut | -780 | 22 | -456 |  |
| 06-25 08:06:00 | K7 | L | 1 | Target | +1199 | 23 | -1632 |  |
| 06-25 11:15:00 | K7 | S | 1 | Target | +1199 | 26 | -5526 | SKIP |
| 06-25 11:16:00 | M7 | S | 1 | StateCut | -792 | 27 | -4328 | SKIP |
| 06-25 11:42:00 | P7 | L | 1 | StateCut | -802 | 28 | -5120 | SKIP |
| 06-25 11:48:00 | K7 | L | 1 | StopJoinFallback | -1276 | 28 | -5120 | SKIP |
| 06-25 12:09:00 | K7 | L | 1 | Target | +1199 | 30 | -7198 | SKIP |
| 06-25 12:42:00 | K7 | S | 1 | Target | +1199 | 31 | -5999 | SKIP |
| 06-25 13:18:00 | K7 | L | 1 | StateCut | -777 | 32 | -4801 | SKIP |
| 06-25 14:00:00 | K7 | L | 1 | StopJoin | -1241 | 33 | -5578 | SKIP |

### Row 3: label day 20260713 - the rule skips 2 entries worth +7193 $ of base P&L (negative = losers avoided)
| signal time ET | book | side | lots | exit | trade net $ | stack closes before | stack day P&L before $ | rule fires (skip) |
|---|---|---|---|---|---|---|---|---|
| 07-13 02:11:00 | M7 | S | 1 | StateCut | -665 | 19 | -4042 |  |
| 07-13 03:24:00 | M7 | L | 1 | StateCut | -712 | 20 | -4707 |  |
| 07-13 04:07:00 | M7 | L | 1 | Target | +1199 | 21 | -5419 |  |
| 07-13 04:30:01 | U7 | L | 4 | Target | +4790 | 22 | -4220 | SKIP |
| 07-13 04:38:02 | M7 | L | 2 | Target | +2403 | 22 | -4220 | SKIP |
| 07-13 05:29:01 | M7 | L | 2 | StateCut | -1554 | 23 | -1818 |  |
| 07-13 08:21:00 | M7 | S | 1 | StateCut | -827 | 25 | +1418 |  |
| 07-13 09:45:00 | O7 | S | 1 | Stop | -766 | 26 | +591 |  |
| 07-13 10:03:00 | M7 | S | 1 | StateCut | -792 | 27 | -175 |  |
| 07-13 10:17:00 | M7 | S | 1 | StateCut | -797 | 28 | -967 |  |
| 07-13 11:52:00 | M7 | S | 1 | Target | +1199 | 29 | -1765 |  |

### Row 4: label day 20261030 - the rule skips 24 entries worth +8969 $ of base P&L (negative = losers avoided)
| signal time ET | book | side | lots | exit | trade net $ | stack closes before | stack day P&L before $ | rule fires (skip) |
|---|---|---|---|---|---|---|---|---|
| 10-30 00:03:01 | P7 | S | 4 | StateCut | -3204 | 19 | -2854 |  |
| 10-30 00:30:00 | U7 | L | 4 | StopJoin | -4715 | 21 | -4859 |  |
| 10-30 00:48:00 | K7 | L | 1 | StateCut | -627 | 21 | -4859 |  |
| 10-30 01:54:00 | K7 | S | 1 | StopJoin | -1181 | 22 | -5487 | SKIP |
| 10-30 02:31:00 | M7 | L | 1 | StateCut | -657 | 24 | -11382 | SKIP |
| 10-30 03:27:00 | K7 | S | 1 | Target | +1199 | 25 | -12040 | SKIP |
| 10-30 03:50:00 | M7 | S | 1 | StateCut | -630 | 25 | -12040 | SKIP |
| 10-30 04:10:00 | U7 | S | 4 | StateCut | -3844 | 26 | -10841 | SKIP |
| 10-30 04:18:00 | K7 | S | 1 | StateCut | -535 | 26 | -10841 | SKIP |
| 10-30 04:51:01 | K7 | L | 1 | StateCut | -525 | 28 | -15219 | SKIP |
| 10-30 05:20:00 | M7 | S | 1 | Target | +1199 | 29 | -15849 | SKIP |

### Row 5: FROZEN LIVE WEEK, label day 20261104 (live trade list, 180 trades in 11-01..05; first-order replay) - 2 entries skipped worth +4066 $ of live P&L
| signal time ET | book | side | lots | exit | trade net $ | stack closes before | stack day P&L before $ | rule fires (skip) |
|---|---|---|---|---|---|---|---|---|
| 11-03 22:15:00 | P7 | S | 4 | ThL2Cut | -2459 | 22 | +5880 |  |
| 11-03 22:52:00 | P7 | S | 7 | PolicyCut | -5069 | 24 | +2781 |  |
| 11-03 23:07:00 | P7 | S | 4 | PolicyCut | -2719 | 25 | -2288 |  |
| 11-03 23:18:01 | P7 | S | 4 | Target | +4776 | 26 | -5008 | SKIP |
| 11-03 23:24:00 | K7 | S | 1 | ThL2Cut | -710 | 26 | -5008 | SKIP |
| 11-03 23:42:00 | K7 | L | 1 | Target | +1195 | 28 | -942 |  |
| 11-04 00:00:00 | U7 | L | 4 | Target | +2386 | 29 | +253 |  |
| 11-04 00:04:00 | A7 | L | 1 | Target | +1195 | 30 | +2639 |  |
| 11-04 00:11:00 | A7 | L | 1 | PolicyCut | -685 | 31 | +3834 |  |
| 11-04 00:17:00 | A7 | L | 1 | PolicyCut | -675 | 32 | +3149 |  |
| 11-04 00:24:00 | A7 | L | 1 | ThL2Cut | -525 | 33 | +2474 |  |

(Live days with any firing in the frozen week: 20261104.)

Note on the worked rows: they replay the rule on the unmodified LPB_BASE list (first-order), so 'closes before' and 'day P&L before' keep counting the trades that the rule would have removed; in the exact engine a skipped entry never opens, so later counts are lower and the rule can re-open when a late winner pushes P&L above -$2,400. Exact sets: JN05W_S6_C22 / _RM (as scored) and JN05W_S6_C22V19 / _RM (entries-opened count) run L6M, HOLD, GAP, PRE, X' (runner pid 3065008).
