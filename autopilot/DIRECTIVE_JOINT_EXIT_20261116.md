# USER ORDER 2026-11-16 (verbatim): T-JOINT-EXIT
(starts 21:00Z, after DS3_BRACKET_DD_BUILD.md; runs beside FLAT_VS_BOOK). Base JL2, all six windows, drawdown first.
Single-layer results from today are the SCREEN only. Verdict = joint.
Per book (K7, P7, M7, U7, H7, A7, O7), vary TOGETHER:
 1. exit rule: top 3 from today's engine page for that book + as-live
 2. loss side: book cut + flat as live / flat level -10% / +10% / book-cut arm 10 pts earlier
 3. existing profit lines: as live / locks removed / takes removed (reference rows; the deliverable is the best SETTING, never "none")
 4. target the pct-based lines are scaled to: as live / rescaled to the new exit's typical exit distance
 5. lots: as live / constant-risk
Then across books: best per-book set combined, with the interaction table (does book A's change move book B's result). Report where a single winner from today LOSES once combined, and where a rule that failed alone passes in combination. Controls with the persistent draw. Page DS3_JOINT_EXIT.md, first table by 12:00Z tomorrow. Recents-first; note any setting that only works in L3M.

# PRIORITY before 21:00Z (user 11-16 ~18:20Z, verbatim): small: 4 cells x HOLD + L6M, take 4 workers
on JL2, leave-one-out for the three book-reading profit lines that become active in live tonight after the v1.9c book/tick fix:
 a. without "profit K7 * pct>=0.3 delta_mult>=5 lock 0 win=10 persist=10"
 b. without "profit U7 * pct>=0.4 delta_mult>=20 tighten 30 win=15 persist=5"
 c. without "profit M7 * pct>=0.3 tot_rel>=2 step 10 persist=2 wall_ticks=8"
 d. without all three
Drawdown first, mean, worst week, per book, vs JL2. Confirm JL2 has all three ON with the correct clean-book inputs. State plainly for each: keep, or it costs money. Report in DS3_BRACKET_DD_BUILD.md at 21:00Z.
