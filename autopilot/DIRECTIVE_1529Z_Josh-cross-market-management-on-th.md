# Do it right: cross-market management on top of the BARE ENTRY, not crammed onto the fitted books (order from Josh, relayed)

Josh, 27 Nov 15:29Z, verbatim: "no something is not right - you are going to find a way for cross management to work on top of the bare entry - why are you trying to cram it on the fitted books - we may not need the fittings with this if all exits are actively managed - please do this right"

(relay) My reading. The design under test is: BARE entry signal of each book (no Trade Health, no zones, no sizer, no per-book fittings) + back-up safety stop + active management from the other instruments. The fitted live book is a REFERENCE to compare with at the end, not the base the loop is bolted onto. Research only; exact engine only (15:27Z).

0. FIRST, WHY THE MODEL DID NOT ACT (72 exits on ~1,800 trades): post the diagnosis today: per decision minute on the SAME trades, quick-screen features versus hook features one by one, predicted advantages both ways, action counts, share of minutes with a missing or stale feed, the minute schedule and the 1 s lag. Fix, prove equality on 400 states, re-run. Nothing below means anything until the loop does in the engine what it does in training.
1. SUBJECT = BARE ENTRIES: every signal of each book's bare trigger (R0: no layers, no Trade Health, one position per book), all four sessions, 1 lot and the live lots. Train the loop on the bare entries' own replayed paths (state every 60 s and, as a second version, every 15 s).
2. ROWS per book, exact engine, like with like:
 A. bare entry + the book's bracket (the bare reference);
 B. bare entry + safety stop (1.5x) + loss-side loop + own target;
 C. bare entry + safety stop + loss-side loop + profit side managed (trail chosen by the loop or the landscape trail; no fixed target);
 D. bare entry + own stop + loss-side loop + own target (loop only cuts earlier);
 E. the fitted live book as run (bracket + Trade Health + layers): shown beside, to answer Josh's question "do we still need the fittings".
 Judge B, C, D against A first (does management add to the bare entry), then against E (does bare + management match or beat the fitted book). Loss-side table first, then max DD, worst week, worst day, income, L3M and L6M first, by year, up weeks and down weeks, long and short separately. Random-management null on the best row. Re-entry rows L0 and L1.
3. SESSION LEVEL: each session's books all on their best bare + managed row, with ONLY the account-level safety rules (session stop, daily loss halt) and no per-book fittings, versus the live mix as run.
4. MAKE IT WORK, IN THIS ORDER, logging every version in ALGO_LOG.md: (a) the wiring fix; (b) the full instrument set (ES, RTY, YM, ZN, ZB, CL, GC, 6E, 6J, NKD) and relative-move features; (c) decision every 15 s instead of 60 s; (d) the label: advantage over the BOOK'S OWN BRACKET outcome instead of over holding to a wide stop (so the model learns to beat the bracket, which is the real comparison); (e) theta per book chosen on past data; (f) loss side with the own stop kept (row D) if the wide safety stop is what hurts. After each: exact rows for Asia MF1 and one NY AM book, then all books for the version that helps.
5. REPORT in plain words after each version: did bare + management beat the bare bracket; did it beat the fitted book; what the loop did (exits, saved stops, false exits).
The Sunday exit-management job (tested settings on every fitted live book) continues unchanged: it is the cover for Sunday whatever this finds.
