# Josh-cross-session-locks-test (research order, 2026-11-23 ~07:50Z)

Josh's words, verbatim (00:42 and 00:43 Mountain time = 07:42 / 07:43Z, 23 Nov):

> "we also don't have combined session locks right ? loss and profit yet?"

and, to the relay's proposal (test a whole-day loss stop, a whole-day profit lock, a whole-week floor and profit lock on the combined book, and carry-over rules between sessions; "Say yes and I'll send it"):

> "yes"

Everything below is the relay's reading (relay = Claude, not typed by Josh).

Context (relay): every D8 lock so far was fitted inside one session's stack. Nothing looks across sessions: Asia can lose and NY AM starts fresh. All four session stacks now exist (Asia pinned 5-book TL3_ALN_AS_STKd8106b26ef; NY AM settled 5-book TL3_ALN_NY_STKd8b76ecd35; London L19201dfc.BRF90_30, real FINAL pending; NY PM FINAL 4-book). Josh's standing rules apply: drawdown first; every layer ON with its best setting ("off" is the reference row, "none" is not a deliverable; weak-but-positive delivered for him to decide); joint, not sequential; pick on recent data (L6M with L3M beside), walk-forward at least 58%, prior years inside the not-a-disaster band, best-of-many null shown; bare D8 judged beside bare D7 only.

1. (relay) Base: the combined all-session book of order 0745Z (D8_ALL_SESSIONS_COMBINED.md), 1 / 2 / 4 lots per book, on two bases: (i) every session truly bare; (ii) every session with its own delivered joint layer pick where one exists (Asia BF4_JT1 or its re-run; NY AM / London / NY PM when theirs land), bare otherwise. Combinations: Asia + NY AM (the launch set), + London, all four.
2. (relay) Cross-session families to score (open P&L counts; checked at every print; say exactly what closes and when the halt lifts):
   a. WHOLE-DAY LOSS STOP: all books of all sessions halt for the rest of the trading date when the combined day P&L is at or below -$Y per lot-per-book (levels at least 3,000 / 4,000 / 5,000 / 6,000 / 8,000 / 10,000 / 12,000 / 16,000), variants: close open positions versus no new entries only.
   b. WHOLE-DAY PROFIT LOCK: (i) hard stop at +$Y per lot-per-book (levels at least 6,000 / 8,000 / 10,000 / 12,000 / 16,000 / 20,000 / 24,000); (ii) give-back lock: arm at +$A, halt when the day falls to a fraction of its peak (arm 6,000 / 10,000 / 16,000; keep 0.33 / 0.5 / 0.67).
   c. WHOLE-WEEK FLOOR and WHOLE-WEEK PROFIT LOCK on the combined book (floor levels and give-back levels of the same shape, in $ per lot-per-book).
   d. CARRY-OVER rules between sessions of the same trading date: after a losing earlier session (down more than X) the next session runs at half size / is skipped / runs normally; after a strongly winning earlier session (up more than X) the next session runs at half size / only until it gives back a fraction of the day's profit / normally. X on a small grid in $ per lot-per-book. Also the simplest form: next session half size after ANY losing earlier session.
   e. A reference row for each: off.
3. (relay) Stages: screen (each setting alone on both bases), then a joint over the cross-session families together; the session-level layer picks stay fixed inside this joint (they are the base), but report the interaction with the session-level daily stops (order 0640Z) and say if a session-level pick should be re-fitted once a cross-session rule is on.
4. (relay) Report per lot at 1 / 2 / 4: ulcer, max drawdown, worst week, worst day, $ per week, share of losing weeks; L6M and L3M; prior years; walk-forward and persistence versus the same book without the rule; year bands; null when it can run; and for each rule how many days / weeks it fired and what it cost on days that would have recovered.
5. (relay) Deliver the best setting of each family with its evidence and the exact engine definition (day / week boundaries, open P&L, what closes, when it lifts), so the D8 file can copy it. If the engine cannot run the sessions in one set, say so at step 0 with the smallest change needed (a merge of the per-session event streams with one cross-session hook is acceptable if it is proven identical to the separate runs with the rule off).
6. (relay) Priority: after the page of order 0745Z; fall-through behind the ordered fits, joints, exit verdicts and nulls, beside orders 0640Z and 0645Z, ahead of the lifted first-look tail. One line at start with rows, rate, ETA.
7. (relay) Not in this order: any spend, new machine or data purchase; no change to gates or to the pinned stacks.

Research only. Nothing here touches the execution server, any live chart, credentials, spend or data deletion.
