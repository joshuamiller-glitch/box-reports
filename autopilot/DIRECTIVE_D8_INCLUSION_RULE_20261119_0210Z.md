# ORDER 20261119_0210Z: D8 inclusion rule (Josh, 02:08Z): "If the new books are better than the live books, they should go in D8"

Research only. This states the rule the D8 build spec is written to; nothing on the live chart changes.

1. RULE. A new book goes into D8 for a session when, in the exact engine against TODAY's stack, it is
   BETTER THAN THE LIVE BOOK(S) IT WOULD REPLACE in that session:
   - headline row = REPLACE (new book in, live book out of that session), ADD shown beside it;
   - drawdown first (stack ulcer / max drawdown / worst week not worse), then dollars per week;
   - picked on the trailing 6 months to today with the 3 months beside it; no red prior year
     (amber 15-30% worse is allowed and shown); persistence > 0.60;
   - evidence it is not luck: 30 date-shift engine controls, and the calibrated search-level check
     when it exists; a book that is better in the engine but not yet through the calibration is listed
     as "BETTER, calibration pending" and Josh decides.
   The bare-trigger screen (R0 / R3) only decides the ORDER cells reach the engine. The live books
   themselves fail R0 bare (LIVE_BOOKS_REFERENCE.md), so failing the bare screen excludes nothing.
2. So the engine queue order matters most now: per session in clock order, the cells most likely to beat
   the live book first; every engine-tested cell gets the REPLACE row against each live book of its
   session (and ADD), L6M + L3M, then prior years and controls for those not clearly worse.
   Keep one page per session: "beats live book X: yes / no / pending", sorted by drawdown change.
3. D8 is not held for exit recipes. Fixed-bracket books that meet the rule go into the D8 spec; a book whose
   exit-recipe version is better replaces its bracket version when that is tested (later build / refit).
   (Josh has NOT yet approved a full exit run; the 150-pair recommendation stays with him.)
4. Asia: same rule with the higher bar already ordered (beat the live Asia book on drawdown first AND
   dollars in L6M and L3M, no red prior year, controls).
5. Publish on SEARCH_STATUS.md: how many cells per session have a finished REPLACE row, how many beat
   their live book so far, and the date the D8 spec can be written under this rule.
