T-SESSION-2 — answers to DS3_SESSION_FINAL's questions, and the re-runs (2026-10-28)

Research only. No live, execution-server or chart change. UNTOUCHED never read. Redact account ids. The user's session rule stands for everything here: score by entry session, never kill a cell for being one-session, best-of-F is a label and a sizing hint, not a gate; SESSION-CANDIDATE / SESSION-PASS tiers as in T-SESSION-RESCORE.

Answers to the four questions

(1) YES — wire the SESSION_REGISTER entries into ap_forward_register.py as shadow/paper records: the 1 SESSION-PASS, the 12 cost-robust pairs at half size, and the 94 cluster representatives (one per cluster, best PRE cell) as shadow rows; label each with its session, basis (mapped / direct), best-of-F label, and the slippage break-even. (2) YES — the live-latency re-run (item A below) is the priority; it decides whether the session pairs exist. (3) YES — entry-clock re-runs of the summary-only families (item B), in the order given. (4) WT 12:00-15:00 block: carry as a WATCH row in the register only (not live-eligible: PRE-insignificant).

A. Live-latency re-run of the session-candidate legs (replay, memory-aware, FIRST)

For every SESSION-CANDIDATE and SESSION-PASS cell-session in DS3_SESSION_2_LEDGER (the 94 cluster representatives at least; all 408 if the replay budget allows — state which), and every leg of the 27 passing pairs: replay on the 1-s/L2 direct path with live-latency fills (market entry +1 tick with the queue model, 1-s and 3-s placement delay variants, stop-market with measured slippage, limit targets on trade-through only, $4.84 RT), restricted to the cell's session window, exact per-book locks. Report per cell-session: stored-fill mean vs direct mean (pts/trade and $/wk), the slippage break-even and whether it clears it at 1-s and 3-s delay, HOLD, 2023 span, by year, MDE. Then re-score the 27 pairs and the 5 live-book carrier cells on the direct basis: stack-add at 10/20/30% risk, worst-20-weeks $, correlation. Verdict line: how many of the 94 clusters / 27 pairs survive live latency; the best 5 with their numbers. Anything surviving gets the Sim spec (session window in ET, exact rule, lots at $1,000 risk, costs) — these go into the D6 session container.

B. Entry-clock re-runs of the summary-only families (CPU-only, in this order; write trade tables with entry time, pnl, basis for every cell so the session score is a filter from now on)

B1 T-OPEN B2 (11,953 cells: OR/DR/cond/B3GRID/ORre/PB/SECONDOPENS/PM/FADE/GAP/CONF) — the entry clock is the point of that program; score by sub-window 09:30-09:45 / 09:45-10:00 / 10:00-10:30 / 10:30-11:00 as well as the six sessions. B2 T-PBX (374) and T-PULLBACK2/3 (193). B3 T-BRACKET grids (6,885) and T-HOLD (5,088): session-restricted bracket shapes. B4 T-WASHOUT (1,488), T-PYRAMID (850), T-SESSLOCK (798). B5 T-B/TB (389+276, day-only: rebuild with entry clock), T-E/TE (296), T-C (280), T-FOOTPRINT (202), T-A (142), TR2/TR4 (133), the rest (T-D, TI, H2, TK, TSBS, TSF, TG, TJ). B6 The 31,097-series pool: only if a cell's generating rule is on disk and cheap (state which are reconstructible); otherwise list them as not re-runnable. For each family after the re-run: the T-SESSION-RESCORE item 2 scoring (PRE selection, one HOLD look per family, SESSION-CANDIDATE / SESSION-PASS tiers, best-of-F as label), report DS3_SESSION_2_<family>.md, and the running table "dead pooled, alive in a session" appended to DS3_SESSION_2_LEDGER.md. Every family that completes feeds its survivors into item A's replay queue.

C. The 2023 problem (Asia / London negative in 2023)

For the session survivors: characterise 2023-04..2024-01 in that session (realised range, trend persistence, volume) vs 2024-26; is the sign flip a volatility-regime effect (the cells only earn when the session's median range is above X) and does a session-range gate (known at the session open from the prior sessions) fix 2023 without costing 2024-26? Scored as a gate cell per survivor, PRE-selected, one HOLD look.

D. Session pairs into a book (for D6)

From A's survivors: the portfolio solve by session — for each session, the best 1-3 cells at equal risk with the lock engine; then the six-session book as one series: weekly mean, SD, maxDD, worst week, worst-20-weeks $, correlation to the live stack, stack-add at 10/20/30% risk; and the plain line per session: "ASIA = cell X at N lots, LONDON = ..., NYAM = ..., NYPM = ..., none for PRE/CLOSE". That line is the D6 configuration.

Reporting

DS3_SESSION2_A.md (live-latency; first), DS3_SESSION2_B_<family>.md as each lands, DS3_SESSION2_C.md, DS3_SESSION2_D.md (the D6 line), MORNING.md every 2 h, DS3_SESSION2_FINAL.md. Replay governor: add the A workers to PRIO_ALLOW (backup first) — this program outranks the remaining T-ZEN items (MGMT, MX, L2, M9), which continue on spare slots.
