# DYNAMIC STOPS AND TARGETS, WALKED FORWARD, ON THE LIVE BOOKS: front of the queue (order from Josh, relayed)

Josh, 27 Nov 03:00Z, verbatim: "yes there has to be a way to predict volatility or range to a degree and adjust bracket sizes OR change how targets are reached with dynamic targeting....or dynamic stops - have we really explored that? and walk it forward? i thiknk these fixed brackets are crazy and make no sense"

(relay) What exists, as I read your pages (correct me in a LEAD TO JOSH line if wrong): D8_EXIT_SCREEN screened 68 exit recipes in 7 families on candidate cells, quick screen only, one pick on all data, no walk-forward, engine hooks only partly built; DS3_REBUILD_S3_ENV (brackets by environment) is a partial first pass on D7 and was never finished or assembled; the live books all run a FIXED bracket plus Trade Health. So the answer to Josh is "screened, never walked forward, never finished on the exact engine". This job finishes it. Research only. It goes to the FRONT, ahead of Q0's remaining rows; the M-programme runs beside it.

SUBJECTS: (1) the 20 live books, each alone bare, then inside its live session mix with the live layers; (2) the Test 5 primary qualifiers of Asia and NY AM (quick screen), so it is not only hindsight books.

EXIT FAMILIES (all of them; each book tries every family):
 X1 volatility-scaled bracket: stop and target = k x (a) ATR of the book's own bars at entry, (b) trailing 20-day session range, (c) the forecast range for the session (HAR/own-bar, and the UW forecast where history exists).
 X2 structure stop: beyond the last swing / the trigger's invalidation level / the nearest wall or volume node, with a volatility cap.
 X3 market target: next opposing level; measured move; share of the expected session range still left (forecast range minus range so far); minimum reward:risk filter.
 X4 trailing, no fixed target: chandelier/ATR trail; swing trail; trail on the trigger's own line; brick reversal.
 X5 staged: part off at 1R or first level, stop to breakeven, trail the rest (run at 2+ base lots).
 X6 time and behaviour: no-progress exit after N bars; target shrinking with session time left; exit on a volatility burst against the trade.
 X7 the existing families already built: SAR, opposite-signal, order-flow exit.
 Reference: the book's own fixed bracket; best fixed bracket re-picked on the same schedule (Part B of Test 3).

WALK-FORWARD: at each date use only data before it. PRIMARY (named now): per book, your existing exit pick rule (eligible = recent 6 and 3 months positive, >= 20 trades, no prior year more than 30% worse; best = lowest ulcer, then highest recent income) applied to data before the date, re-picked every 13 weeks; judged on the next period against the book's fixed bracket. Also at 4-week and 2-week re-pick steps (Josh's rhythm, shown first), and one row "family fixed, only its parameter re-picked". PASS per book and per session mix = shallower forward max drawdown or better worst week in at least two thirds of periods with income not lower by more than 10%; or higher income with drawdown not deeper. Drawdown first in every table, L3M and L6M first.

ALSO REPORT: per family, in how many books it was ever picked and how it did forward (which families are real and which are screen noise); a random-entry null on the finalists (same exits on random entries) so an exit that only harvests drift is marked; interaction with Trade Health (exit alone vs exit + the book's live Trade Health; say where they fight each other); pessimistic stop-fill label.

ENGINE: quick screen (gexit kernel) first for the whole thing on server C; exact engine for every family the hooks support today; for families not yet supported (continuous trail, multi-level staging, dynamic structure stop), build the research hooks as D8_EXIT_ENGINE_SUPPORT planned, with the identity tests, and say when each is ready. Post the set-month count and start with Asia and NY AM live books at once.
Pages: DYNEXIT_WF.md (answer first) and DYNEXIT_SPEC.md (what a winning exit would need coded, SPEC vs READING). Post a LEAD TO JOSH line with the time estimate.
