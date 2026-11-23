# Josh-depth-book-lock-info (information request, 2026-11-23 ~07:40Z)

Josh's words, verbatim (00:35 and 00:37 Mountain time = 07:35 / 07:37Z, 23 Nov):

> "why was depth book locked out?"

and, to the relay's offer ("I can ask the box how often the lock ends the depth book's night after a single trade in the test, and what that book earns with the lock on versus off. That is information from results it already has, with no new runs."):

> "ask yes"

> "ALSO what is the trade frequency for the London book"

Everything below is the relay's reading (relay = Claude, not typed by Josh). INFORMATION ONLY from results already on disk: no new engine runs, no gate or rule change.

Context (relay): on the first live night (2 lots, joint pick BF4_JT1, BookLock BL2 = arm 1.5 R, give-back 50%, weekly floor -12 R) the depth book L578701ed (stop 30 / target 90) went +49 points on its first trade (arming the lock at 1.5 R = 45 points of ONE trade), pulled back to half the peak, was closed by the lock at +24.5 points and halted for the session; 10 later signals of that book were dropped. On a 30/90 book the lock can arm and fire inside a single trade.

1. For L578701ed inside the pinned 5-book Asia stack with BF4_JT1, at 1 / 2 / 4 lots, L6M and L3M (and the prior years if already on disk): number of nights the BookLock give-back fired; how many of those fired INSIDE THE FIRST TRADE of the night (peak and exit in the same trade); average number of later signals dropped on those nights; the P&L of the dropped signals if the bare events are on disk (what the book would have made or lost after the lock).
2. The same counts for the other four books (their stops are 40 or 60 points, so a single trade arms the lock less often): one line each.
3. From the existing screen rows: L578701ed's and the stack's ulcer / max DD / worst week / $ per week with BL off, BL2, and the levels that arm later (BL4-BL9, arm 2 R and 3 R). Say whether the screen or the joint ever scored BookLock per book (a different BL level for one book) or only one BL level for the whole stack; if only stack-wide, say what a per-book BL level would need (hook change or only new rows), without running it.
4. Confirm the engine's rule for the D8 port: open (unrealised) P&L counts in day and peak; evaluated at every price update while in a trade; R uses base lots (not the ER-sizer-halved lots of the trade); the halt lasts to the end of the session.
5. London book L19201dfc.BRF90_30: trades per London session (not events): L6M and L3M average and median, share of sessions with 0 trades, the busiest session, and the same per year 2023-2025; events dropped by the one-position rule per session.
6. In the Asia joint that is being re-run with the daily-loss family (order 0640Z): if it is free to do so, let the BookLock arm level vary over the levels already in the menu (it does already if BL is a joint family; just confirm).

No recommendation needed; Josh decides what, if anything, to test next.

Research only. Nothing here touches the execution server, any live chart, credentials, spend or data deletion.
