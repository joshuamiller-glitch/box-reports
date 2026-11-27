# Find out WHAT THE QUICK SCREEN DID to get its lift, behaviour by behaviour, and reproduce that in the exact engine (order from Josh, relayed)

Josh, 27 Nov 15:30Z, verbatim: "if it's 220% and drops because it cuts trades short and doesn't re-enter - find out what the quick screen is doing to get 220 lift behavior wise with trade frequency and do that"

(relay) My reading. Part of the 15:29Z diagnosis (item 0), made specific. Asia MF1 first, same signals, same months, both simulators. Research only.
1. BEHAVIOUR TABLE, quick screen versus exact engine, side by side: signals seen; entries taken; entries skipped because a position was open; re-entries after a managed exit (how soon, same side or not, their P&L); trades per week; loop actions per trade and per decision minute (take-all, tighten, part, trail); share of trades the loop touched; where in the trade it acted (open R, minutes in); how trades ended (safety stop, loop exit, bell, target) with counts and dollars; average loss of a loop-closed trade; average win of a trade that ran to the bell. One line saying where the +$140k of quick-screen lift comes from by row (smaller losers / bigger winners / fewer or more trades) and where the exact engine loses it.
2. MATCH THE FREQUENCY, THEN JUDGE: run the exact engine FORCED to the quick screen's behaviour, one change at a time, so the cause is isolated:
 a. the quick screen's exact entry list (same entries, nothing extra, nothing blocked) with the loop's quick-screen actions replayed at their timestamps: does the exact engine then show the lift (if yes, the idea is real and the gap is entries and wiring; if no, the quick screen's fills or paths are wrong);
 b. the engine's own entry logic with slot lock L1 (no re-entry until the original trade would have ended) and with L0, with the FIXED hook making the same decisions as training;
 c. the same with the book's own target kept.
3. Then adopt as the engine's default whatever re-entry behaviour reproduces the lift honestly (most likely the slot lock), state it in ALGO_SPEC.md, and re-run Asia MF1 and one NY AM book on the bare entries (rows A-E of 15:29Z).
Post the behaviour table in a LEAD TO JOSH line as soon as it exists; exact engine numbers only for any gain.
