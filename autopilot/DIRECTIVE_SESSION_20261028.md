T-SESSION-RESCORE — every scored cell in the ledger, re-scored session by session (2026-10-28)

Research only. No live, execution-server or chart change. UNTOUCHED never read. No new cells, no new rules: this re-scores what already exists, restricted by entry session. The concern: the book searches (T-ENTRY, T-PBX, T-CHOP, D4 engines, T-TREND, the ICT/CZT/footprint blocks, T-DIVERSIFY) selected on the pooled all-hours number, so a rule that earns in one session and loses it back in another was labelled DEAD, and a book carried by one session was labelled "works all day".

Sessions (ET; entries by session, exits run to the bracket; the live blocks stay)

ASIA 18:00-02:00, LONDON 02:00-08:30, PRE 08:30-09:30, NY-AM 09:30-12:00, NY-PM 12:00-15:00, CLOSE 15:00-16:54; plus NY = NY-AM + NY-PM. Sessions are scored by ENTRY time; a trade belongs to the session it was entered in.

1. The live and Sim books first (cite the audit's book x session table; extend it)

ST, HM, WT, KB, SM, PE, PB, DN, MV, MA, CR, the basket: per session, weekly mean, SD, Sharpe, maxDD, worst-20-weeks share, trades/wk, by year, with MDE. The plain line per book: which session carries it, which session loses, and whether blocking its losing session (as a session-block sizing rule, live-eligible once scored) improves HOLD with the shifted-session placebo. This overlaps DS3_BLOCKRULES (five windows) — cite it and only report what is new (per-book, all six sessions).

2. The ledger (every cell with trade rows on disk — PASS, CANDIDATE and DEAD alike; state the count, and list separately every family whose cells have NO trade rows on disk (summary-only screens) with the cell count, so the user can order a re-run of those)

For each cell and each session: WF-PRE mean and effect vs its own placebo (random-in-regime where the cell has one, random-direction otherwise), trades/wk, win rate. Selection on PRE only: the cells whose best session has PRE effect > 0 with CI above 0 and >= 100 PRE trades, then ONE holdout look for those (list them in a PREHOLD file first). Multiplicity: F = cells x 6 sessions (state it; best-of-F applies). Report the top 30 session-restricted cells regardless of verdict with failed gate and MDE, and the table "cells DEAD pooled but PASS/CANDIDATE in one session" — that table is the point of the program. User rule for this program: nothing is killed for being one-session, and best-of-F is a LABEL, not a gate. (a) Every cell whose session PRE effect has CI above 0 (>= 100 PRE trades) is reported with its HOLD number, its 2023-span number and by-year, whatever best-of-F says; none is dropped from the report. (b) A cell that is PRE-significant in a session, HOLD-positive in that session, and positive in both HOLD years gets tier SESSION-CANDIDATE and is registered in the forward register as a session book regardless of best-of-F; best-of-F is printed beside it as the confidence label (and sizes it: CANDIDATE lots half of PASS lots in any portfolio line). (c) SESSION-PASS = (b) plus best-of-F cleared. (d) The pooled all-hours verdict is never used against a session cell.

3. Session-complementary pairs

Among the top session cells: pairs that earn in different sessions (an Asia rule + a NY rule) scored together as one book with the lock engine; correlation to the stack; stack-add at 10/20/30% risk; worst-20-weeks $. Verdict: whether any session-restricted cell or pair adds to the stack net of the books already in it.

4. Specs

For anything that passes: the cell's existing spec plus the session window in ET and the flat rule; one paragraph plain English.

Reporting

DS3_SESSION_1_BOOKS.md (item 1, with the live-eligible block lines), DS3_SESSION_2_LEDGER.md (the "dead pooled, alive in a session" table), DS3_SESSION_3_PAIRS.md, DS3_SESSION_FINAL.md with one verdict line per session: best cell, effect, MDE, stack-add. CPU-only (rows exist); use all cores.
