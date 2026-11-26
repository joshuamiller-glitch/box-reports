# Test 8: level books that trade BOTH sides, judged against drift, one named version (ordered by the relay under Josh's standing order)

Josh, 26 Nov 18:22Z, verbatim: "this is the order to you once the results come back in order a new test over the next 48 hours and keep reporting to me"

(relay) My design. Research only. Test 7: long-only level books are drift; the only group with something beyond drift is level books that trade both sides (+343 vs null +45, p 0.021, exploratory). That group was found by looking, so it needs its own clean check and a forward record.

PRIMARY (named now): the Test 5 primary rule unchanged, candidate set (3) of Test 6, restricted to level-module books that take BOTH long and short entries (a both-sides cell, or a long cell and a short cell of the same book both qualifying at that date, held as one book at half weight each). Hold all, equal weight, 13 weeks.
JUDGED ON EXCESS OVER THE DRIFT NULL (Test 7 part B method, 200 draws), per session and summed: PASS = excess > 0, real beats >= 95% of draws, weekly paired bootstrap p <= 0.10. No best-of penalty (one version). Report also raw $/lot/wk, max DD, worst week, L3M, L6M, by year, books held per date, and the result in NQ down weeks vs up weeks.
ROBUSTNESS (reference rows only, not candidates): t>=3 instead of 4; excluding the single largest level type; first half vs second half of the span.
THE LIST TODAY: Asia and NY AM both-sides level books held at the last date: id, level type, action, bar type and size, bracket, trades per side, $/lot/wk per side by year. Mark D8Asia.cs / twin / new (relay confirms).
FORWARD REGISTER: seed 20261128, draw two Asia stacks and two NY AM stacks of 6 from that list (fewer if the list is shorter; say so), name them A4-A5, N4-N5, add to FORWARD_REGISTER_STACKS.md, scored weekly with the others, nothing re-drawn.
EXACT: held cells of the primary, bare R0, held periods; the four new stacks bare and with the session's live account layers, 42 months; the drift null on exact rows where the engine allows (post the count first).
Page TEST8_TWO_SIDED_LEVELS.md, answer first, recent first. Quick-screen parts now on server C; exact rows behind Test 6's. Post a LEAD TO JOSH line with the time estimate.
