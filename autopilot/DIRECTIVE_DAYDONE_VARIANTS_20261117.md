RESEARCH ORDER (relay, 11-17 13:31Z): DAY-DONE variants, from last night's live session. Low priority behind M7 London controls, FLAT vs BOOK JL3, stage 3.

Live fact (v2.0, night of 11-16): DAY-DONE (stack-wide: >= 22 closed trades and day P&L <= -4,200) tripped at 01:26 ET at 22 closes and -9,660 while several trades were open and in profit; those closed via take lines and the day finished -5,450. Every signal was then skipped from 01:50 ET to the 18:00 ET reset: the whole London session and the whole New York session. Stage 5 could not tell DAY-DONE from zero on the full history (recent-leaning).

Test on the engine (JL3; JL2 for comparison), 43 months, ulcer primary, windows L6M / HOLD / GAP / PRE / X' / pooled, 30 persistent random-day-halt controls matched on halted share of sessions:
 a. DAY-DONE as live (reference) and OFF.
 b. Count open (unrealised) P&L in the day figure at the moment of the check.
 c. Halt only until the next session boundary (Asia trip -> resume at London open; London trip -> resume at NY AM), instead of until 18:00 ET.
 d. Halt for N hours (2, 4) then resume.
 e. Thresholds grid: closes {18, 22, 26, 30} x day loss {-3,000, -4,200, -6,000, -8,000} for the live form and for (c).
 f. Per-book version: only the books that are net negative on the day stop.
Report for each: days halted, trades and dollars skipped after the halt (were the skipped sessions winners or losers on average), ulcer / mean / max DD / worst week, percentile vs controls. No removal of the live rule is implied: this is a search for a better SETTING of the same layer.

Research only.
