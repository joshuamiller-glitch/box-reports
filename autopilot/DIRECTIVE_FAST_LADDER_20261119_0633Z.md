# ORDER 20261119_0633Z: the true engine rate is ~1,410 set-months/h: make the LADDER engine itself faster

Research only. Read: 06:17Z rate reconciliation (HEALTH double-counted all night; true fleet ~1,410/h);
restated dates: 4 REPLACE rows ~Nov 20 17:00Z, first wave ~Nov 23, NY AM stage 1 ~Nov 26, Asia + NY AM
~Nov 29, whole ladder through everything ~31 fleet-days. Core count will not close that gap; method can.

1. WHERE THE TIME GOES. One ladder set-month costs 239-460 s of a core, yet the live stack's own trades in
   that month are IDENTICAL across thousands of ADD / REPLACE sets. Profile three typical ladder sets
   (Asia ADD, NY AM REPLACE-K7, NY AM REPLACE-P7): seconds in loading prints / bars, replaying the unchanged
   live books, the new book, the account layers (DAY-DONE, caps, locks), writing results.
2. FAST EXACT PATH for ladder rows (W-FASTR owns the method; its replay is already validated for a book's
   own layer settings). Build the equivalent for ADD / REPLACE rows:
   a. cache per month the baseline stack run (every live book's entries / exits / fills and the account-layer
      state per event) once;
   b. for a set, replay only what the new book changes: its own trades, plus the stack state from the first
      event where the new book's presence changes an account-layer decision (DAY-DONE count / dollars, day
      caps, position / lot limits, locks), re-running the rest of that day exactly; for REPLACE, the removed
      book's trades leave the stream the same way;
   c. IDENTITY TEST before any number is used: fast path == exact engine, trade for trade and to the cent, on
      at least 200 set-months spread over Asia / NY AM, ADD / REPLACE vs each live book, quiet and busy
      months, months where DAY-DONE trips; publish mismatches; a set whose month fails identity falls back
      to the exact engine automatically.
   d. State the measured speed-up (target: >= 10x on the ladder) and switch the ladder queues to it when
      the identity test passes; keep a 2% random re-check of fast results in the exact engine forever.
3. If (2) cannot be exact for some row types, say which and why, and what else removes work WITHOUT cutting
   candidates: sharing loaded month data between sets on one worker (batch several sets per process),
   in-RAM month stores on the 1.4 TB hosts, skipping months where the new book has no trade (the stack
   result equals the baseline by construction: prove it), compiled inner loop.
4. Meanwhile the ORDER of work decides what Josh gets first: Asia cells then NY AM cells most likely to beat
   their live book (block score, screen rank), their prior years / controls / exit rows right behind them,
   so the first wave of D8 candidates is complete as early as possible. Nothing is dropped.
5. One LEAD NOTE by 09:00Z: the profile, the plan, the identity-test design and a first measured speed-up;
   then the restated dates (first wave; Asia stage 1; NY AM stage 1; whole ladder) at the new rate.
6. Every figure Josh was given tonight from HEALTH.md's fleet rate was about 2x too high: list on
   QUESTIONS_FOR_JOSH.md which published dates are void and the corrected ones, in one table.
