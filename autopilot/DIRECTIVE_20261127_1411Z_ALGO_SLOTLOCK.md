# Algo build: the freed-entry effect must be a DESIGN CHOICE, not an accident: slot lock and re-entry policy rows (relay note under Josh's standing algo order)

Josh, 27 Nov 13:07Z, verbatim: "we have a strategy now we need to make it an algo using all available tools - the server is to not stop until it's coded"

(relay) My design. Your stub replay showed 442 -> 1,506 trades when managed exits free the book (the same thing that killed AS8). Josh's own design standard is that the algo must not keep re-entering the same failed idea. So every managed replay runs with these rows side by side, from loop A onward:
 L0. free (as now): the book may re-enter as soon as the managed exit is done.
 L1. SLOT LOCK: after a managed exit the book may not re-enter until the time its original trade would have ended (first of: back-up stop, the reference bracket's target or stop on the tape, session end).
 L2. COOLDOWN: no re-entry for N minutes after a managed exit (N = 15, 45), and no same-side re-entry until price has moved 0.5R away from the exit price.
 L3. EVIDENCE GATE: re-entry allowed only if the loop's own score (or rule state) is not AGAINST that side at the new signal.
Report trades per day, income, max DD and worst week for each, and which row a discretionary trader would recognise. Prefer L1 as the default unless another row is clearly better.
Also noted from ALGO_LOOP_A's rarity check (R1, R2, R4 would have left trades that then did better by 0.1-0.25R): before loosening or tightening thresholds by hand, give the per-rule table of WHERE in the trade each rule fired (open R, minutes in, distance to stop and to next liquidity) for the cases it helped and the cases it hurt; loop A2 is written from that table and logged in ALGO_LOG.md.
Databento equities quote: Josh has been told it needs his word; nothing to do until he answers.
