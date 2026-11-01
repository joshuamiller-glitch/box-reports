# USER ORDER T-RECENT-REDO (2026-11-01 ~15:45Z), saved verbatim

T-RECENT-REDO — "recent" means FROM TODAY. Move the cap, rebuild every recent window, validate the method, re-read everything (user, 2026-11-01 ~15:45Z)

The user has learned that every "L3M / L6M" in this week's reports ends 2026-02-06. That is not what he asked for. From now on recent = recent. This directive supersedes the cap rule in PLAN36_BRIEF and every earlier window definition. Log the change in DECISIONS.md with the time; the old windows stay in the reports' history, nothing is deleted.

1. The cap and the windows (do this first, before any scoring)
Data cap = 2026-10-31 (the last complete day on disk; the de-duplicated tape copies from TAPE-1, not the originals with the stray Sunday hour). No UNTOUCHED holdout from here. Validation is by method (section 3) and by the forward register, not by a frozen future.
New windows, every report, every ledger, every program from now on:
L1M = 2026-10-01..10-31 (trailing 30 days) · L2M = 2026-09-01..10-31 (trailing 60 days) · L3M = 2026-08-01..10-31 · L6M = 2026-05-01..10-31 · HOLD = 2025-11-01..2026-10-31 · PRE = 2024-02..2025-06 and X' = 2023-04..2024-01 unchanged · MID = 2026-02-07..2026-04-30 (the months between the old cap and L6M, so nothing is skipped).
L1M and L2M are VIEW columns with n shown; no rule is selected on them (section 3 decides whether they ever can be).
Column order in every table, recent first: L1M | L2M | L3M | L6M | HOLD | MID | PRE | X'. MDE beside each. Session column stays. Three columns STRICT / TOLERANT / NOW-ONLY recomputed on the new windows (TOLERANT clause set unchanged: older windows ≥ −0.5 MDE, PRE worst-20 not worse than the stack's).
Rebuild the bar store, the 1-s arrays, the L2 tables, the trade library and the lock engine through 2026-10-31 (the ingest log shows mbp-10 and trades to 2026-10 on disk). State what is missing (days, instruments) in one table; do not synthesise.
2. First job: the window nobody has looked at (2026-02-07..2026-10-31)

Before anything is re-fitted, score as-shipped on the never-looked window, drawdown first, per book and session:

the live stack as it was (market entries, no rules) and D6 v2.3b / D7 v1.0d as shipped (70/30 dip 3; TH-L2 30/30 and −30/5 s/30×; PE 45-s NY; ER(20) sizer all books, running-max locks; Asia-only cut 50; 8-line zone skip D 20 with OTE-62 B73 D 30; signal-state rules as EF-2 scored them; X1-X5 at 2 lots; Native stop), and each piece alone and leave-one-out;
the ON / SHADOW / OFF lists of the Sunday brief, every row;
the six core books per session (the session-lot table) — which sessions paid Feb-Oct. Report DS3_FORWARD_FEB_OCT.md: mean, maxDD, worst weeks, Calmar, per book, per session, L1M..MID columns; the plain sentence "on the nine months nobody had seen, the Sunday composite made X $/wk vs Y as-is with maxDD A vs B; the pieces that held were …; the pieces that did not were …". This is the single most important number of the week; it goes to MORNING.md the moment it exists, then into the brief as section 0.
3. Validate the METHOD (the user's question: "how would we validate it if that's it?")

The selection method is "run what was positive in the trailing window." Test the method, not the rules, by walking it through history on the full data:

For every month M from 2024-01 to 2026-10: the set of rules positive in the trailing 30 / 60 / 90 / 180 / 365 days before M (per contract and stack; universe = every streamed series the ledgers hold, ~43,660, plus the ON/Shadow rules); their result in the next 30 and next 90 days after M; the share still positive; the shrinkage (next ÷ trailing magnitude); $/wk at live lots; by family; vs noise twins (same mean, shuffled months) and vs "pick everything."
The same with the TOLERANT gate added to each trailing window (trailing-positive AND older windows not broken) — the user's actual rule.
The same for combinations: trailing-90 AND trailing-180 both positive (the current rule), trailing-60 AND trailing-180, trailing-30 AND trailing-90.
The answer in one table: window | hit rate next 30 d | next 90 d | shrinkage | $/wk | vs noise | by family — and the plain sentences "a rule positive in the last 60 days stays positive next month X% (noise Y%); the best window for THIS market is W; adding the tolerant gate moves it to Z%". Report DS3_WINDOW_VALIDATION.md. If a window beats noise by a clear margin, that window becomes the ledger's selection window; if none does, say so and the ledger stays a view.
Also the regime question directly: is Feb-Oct 2026 more like L6M-old (Aug-Jan) or like PRE (2024-25) on the regime measures (vol tercile, trend persistence, session shares, book depth, ES correlation)? One paragraph, so the user knows which year the market currently resembles.
4. Re-read the ledger and the week's programs on the new windows
RECENT_WINS rebuilt: every row re-scored on L1M..MID; the persistence score, status (NEW / RISING / STABLE / FADING / STOPPED), drift sparkline and shrunk size recomputed with the new months; "turned on / faded / stopped since Feb" listed; the top 30 by shrunk $ at live lots re-ranked; a column "old L3M (to Feb-06)" kept beside the new one so the user sees what moved.
The SIXTY lists (≥ 0.60 / 0.70) re-cut; the DRAWDOWN tables (DS3_DRAWDOWN, EF-2, D7F, P70, FED, VOLSCALE, HEDGE) re-run on the new windows at live lots — one summary table "what changed on the real recent months"; anything that was OFF on the old windows and is positive and RISK-KEEP on the new ones is flagged for the user explicitly (and the reverse).
BETTER, ZONES-3 and the ZONES-3 addendum continue, on the new windows from the moment section 1 is done; whatever they already produced on the old windows is marked "old cap" and re-run.
5. Forward register from Monday

The register's clock starts Mon 2026-11-02 with D7's signals; weekly lines in MORNING.md; 13-week rule for any harm/futility call; the register IS the out-of-sample from here. Its first table compares D7's logged signals with the box's own signal reconstruction (the NT8 identity test for X1-X5 and the signal-state terciles).

6. Order and timing

Section 1 immediately (hours); section 2 as soon as the engines tie out (tonight); section 3 overnight; section 4 by Monday 12:00Z; MORNING.md every 2 h with the new windows in every line; the Sunday brief gets a "FEB-OCT" section 0 the moment section 2 lands, even if that is after 18:00 ET — the user will read it at the first pull.
