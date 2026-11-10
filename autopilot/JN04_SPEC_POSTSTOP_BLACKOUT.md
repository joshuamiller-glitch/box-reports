# JN04_SPEC_POSTSTOP_BLACKOUT - P7 post-stop / post-cut same-side 30-min blackout (R5_BO_3) as an exact live definition for D7 v1.6
REDO-R5, 2026-11-10 14:22Z. SHADOW / spec only, no PASS claim. **Label: LEAD (not CANDIDATE)**: exact windows below, placebo p .14 / .12, family p 1.00, HOLD window is deeper than live. Rule 2 / 2a: recents first (L6M +8%, d mean +$3.0k/wk); rule 2a PRE floor = 25% of the live PRE mean (PRE d mean +$10/wk is far inside it) -> OK-PRIOR; but the bi-weekly WF is a screen-only result and HOLD (-9%) fails, so no change is recommended on this evidence. This page only fixes WHAT the rule is, so it can be coded and run in Shadow.

## 1. The rule (exactly what the exact engine ran; code/th_r5/r5_hooks.py, `bo` key, exec_exit + try_entry)
- **Books:** P7 only (trigger book = blocked book = P7; no other book's exits trigger it, no other book's signals are blocked).
- **Trigger events (any one opens a window):** the full close of a P7 position (the last contract filled out) whose exit reason is
  1. **StateCut** (the v1.5 state loss cut; in the v1.4 file the same slot is the TH-L2 loss cut exit "ThL2Cut"),
  2. **Stop**: a stop exit of any of the three kinds the stop path produces - native stop ("Stop"), stop-join limit fill ("StopJoin"), stop-join market fallback ("StopJoinFallback"). The 80-pt catastrophe native stop, if it ever fills, is also a stop exit.
  **Not triggers:** Target, BookLock (give-back / week floor), StackCut, TimeBlock / session flat, RollFlat, day-halt exits, profit-take / tighten trail exits ("ThL2Trail", "PolicyTake"), partial target fills that leave contracts open. A **profit** exit never triggers it.
- **Side:** the side of the position that closed (long position closed -> window blocks LONG signals only; short -> SHORT only). An opposite-side signal is NOT blocked.
- **Window:** starts at the **exit FILL time** (the fill callback of the last exiting contract, i.e. the trade's exit timestamp `exit_ns`, not the decision / request time) and lasts **30 minutes of absolute time (1,800 s, UTC epoch clock; no session or ET dependence, runs across the 17:00 ET roll and the session boundaries)**. Several windows can overlap (one per qualifying exit); a signal is blocked if ANY open window has the same side. A blocked signal never creates a trade, so it never opens a window itself (no cascade).
- **What is blocked:** the P7 ENTRY SIGNAL only, evaluated at the **signal second** (the instant TryEntry would receive it: bar close for the PB3B bar logic), before the 45-s confirmation / OTE hold / L2 arm / sizing. The signal is **dropped** (not queued, not re-armed after the window). Nothing already working is touched: an open position, its resting stop / target, an armed reserve add of a still-open trade are unaffected (a window can only open when the position is flat, so there is no add to cancel). A signal that was already accepted and is waiting in the 45-s confirm before the stop cannot exist (P7 was in a trade).
- **Evaluation order inside TryEntry:** the normal skips first (book disabled, in trade, ExitPending, entry pending, DayHalt / WeekHalt, time block, session lots 0); then the blackout check. So the blackout never changes day-halt / lock accounting and a halted book logs its usual reason; a signal blocked by the blackout does not consume a daily trade count or a lock state. ExitPending: the window opens only at the FILL, so a signal arriving while the exit is still pending is skipped by ExitPending as today (not by the blackout).
- **Tie rules:** a signal is blocked iff `exit_fill_time < signal_time < exit_fill_time + 1,800 s` for a same-side window (strict at the far end: a signal at exactly +1,800.000 s is allowed; a signal in the same second as the fill, processed after the fill, is blocked). Ordering inside one second follows the engine event order (fill callbacks before the bar-close signal handler); in live code set the window inside the exit-fill handler (OnExecutionUpdate) so any later TryEntry sees it.
- **Panel / code:** there is **no D7 v1.4 panel field** for the post-STOP trigger (ThL2BlackoutMins / ThL2BlackoutBooks / ThL2BlackoutSameSideOnly act on the loss CUT only). Proposed v1.6 fields: `PostExitBlackoutMode` (Off|Shadow|Live), `PostExitBlackoutBooks` = "P7", `PostExitBlackoutMins` = 30, `PostExitBlackoutSameSide` = true, `PostExitBlackoutOn` = "Stop,StateCut". Implementation: in the exit-fill handler, when the book is flat and the exit reason is in the list, `b.BlackoutUntil = max(b.BlackoutUntil, fillTime + N min)` per SIDE (two fields BlackoutUntilLong / BlackoutUntilShort, because overlapping windows of opposite sides must not overwrite each other); TryEntry skips when `now < BlackoutUntil[side]`. Policy line: "P7: after a Stop or StateCut exit, no same-side P7 signal for 30 minutes."
- **Quantities the live strategy cannot compute from chart data:** none. Needs only the book's own exit fill time, exit reason and position side, all known in OnExecutionUpdate. (The only dependency is that the v1.5 state cut is reported as an exit with a distinguishable name; if the cut fires through a different path name, add it to the trigger list.)

## 2. Verification that the written rule reproduces the exact trade set
- Exact run R5_BO_3 (S1b-COMB base, 39 months present): 2,347 P7 trigger exits = StateCut 1,945 + StopJoin 239 + StopJoinFallback 144 + Stop 19 (other P7 exits: Target 2,283, BookLock 52, TimeBlock 38, StackCut 15, RollFlat 10, none of them triggers).
- **Rule check on the output list:** applying the written rule to the run's own P7 trades (trigger exits above, same side, signal strictly inside 30 min after the exit fill) finds **0 taken P7 signals inside an open window (0 violations)**. The same check on the live-panel-base run (LPB_BASE_BO3, 545 P7 trigger exits, L6M) also finds **0 violations**.
- **Blocked-signal reconstruction:** of the P7 trades in the unblocked exact base list (S1b-COMB) that are absent from the blackout run, **390 are explained exactly by a window** (a same-side trigger exit of the blackout run 0.6-29.9 min before the base signal, median 15.9 min, triggers StateCut 335 / StopJoin 32 / StopJoinFallback 23); 105 are absent for a different reason (follow-on divergence: a different trade history after the first blocked signal shifts later entries, caps and locks). The exact run re-simulates the follow-ons, so the trade sets are not a pure subset; the rule itself holds with zero violations.

## 3. Five worked rows from the exact run (blocked signal = a base P7 signal that the blackout removed; times ET, absolute 30-min window)
| # | run month | trigger exit (type) | exit fill time ET | blocked signal time ET | minutes after exit | side | planned lots of the blocked signal |
|---|---|---|---|---|---|---|---|
| 1 | 202605 | StateCut | 2026-04-30 18:56:54 | 2026-04-30 19:13:01 | 16.1 | long | 4 |
| 2 | 202605 | StateCut | 2026-05-01 10:33:16 | 2026-05-01 11:00:00 | 26.7 | long | 7 |
| 3 | 202606 | StopJoin | 2026-06-10 06:30:42 | 2026-06-10 06:53:00 | 22.3 | short | 4 |
| 4 | 202606 | StopJoinFallback | 2026-06-07 18:55:46 | 2026-06-07 19:08:00 | 12.2 | long | 4 |
| 5 | 202306 | StopJoinFallback | 2023-06-28 11:25:04 | 2023-06-28 11:38:00 | 12.9 | long | 4 |

## 4. Four-window numbers
**(a) Exact S1b-COMB base (engine as the other R5 rows; ROLL-EXCL, all-weeks maxDD, carrying week dropped from means only), stack, R5_BO_3 vs the exact base:**

| window | live maxDD | with blackout maxDD | cut % | live worst-20 | with worst-20 | d mean $/wk |
|---|---|---|---|---|---|---|
| L6M | 79907 | 73475 | +8.0 | 165224 | 284546 | +3026 |
| HOLD | 99496 | 108430 | -9.0 | -575167 | -458087 | +2443 |
| PRE | 140288 | 127881 | +8.8 | -699709 | -680882 | +10 |
| X' | 128944 | 134598 | -4.4 | -347890 | -345832 | -11 |

**(b) LIVE PANEL base (P7 day cap 8,400 loss cap + 7/4/4 table (asia 7, london 4, nyam 4) + P7 state cut 40 / 5x / win 5 / pers 3 no newMae, all ON; sets LPB_BASE and LPB_BASE_BO3, built by REDO-R5 because no SZ-IJK live-panel set existed on the box; interpretation of "P7 day cap 8,400" = maximum daily LOSS 8,400 for P7 with the +42,000 profit cap kept; if SZ-IJK's base differs, rerun with its sets), blackout vs the same base:**

| window | live maxDD | with blackout maxDD | cut % | live worst-20 | with worst-20 | d mean $/wk |
|---|---|---|---|---|---|---|
| L6M | 77224 | 75509 | +2.2 | 102384 | 147680 | +1674 |
| HOLD | not complete | | | | | |
| PRE | not complete | | | | | |
| X' | not complete | | | | | |

Months complete for the live-panel rows: L6M (6 months) done, HOLD queued ahead of other tiers; PRE and X' were not requested of the queue (capacity); the table shows 'not complete' where a window is missing.

## 5. Notes
- The gain is mostly the post-STOP and post-cut re-entry avoidance on P7 in L6M; on the S1b-COMB base the HOLD window (Nov 2025 - Apr 2026) is deeper than live (-9%) and X' is -4%: it does not hold across windows. On the live-panel base L6M the cut is smaller (+2%) at +$1.7k/wk.
- Everything above is Shadow evidence; nothing goes live from this page. Files: code/th_r5/r5_hooks.py (rule), r5_spec_verify.py (rule check), /mnt/l2/l2vast/_th_r5/bo3_blocked.csv (all blocked signals), exact runs under _th_state/s345/exact_b/runs/R5_BO_3 and LPB_BASE*.
