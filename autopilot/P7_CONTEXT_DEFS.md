# P7_CONTEXT_DEFS - ONE definition of the P7 entry-context tags (W-B, written 2026-11-11 19:2xZ; W-C and W-B both use it; append-only, changes go in a dated section at the end)
All tags are causal at the P7 SIGNAL second (b.sig_ns) and fixed at entry.
- session: by the signal clock, ET: asia 18:00-01:59, london 02:00-08:29, pre 08:30-09:29, nyam 09:30-11:59, nypm 12:00-14:59, close 15:00+ (same as the D7 SessionNames).
- n_sess: index (1,2,3+) of this signal among P7 TAKEN trades (entries) of the same session and label day. 1st/2nd = "fresh" by order.
- gap_min: minutes from the last P7 exit (any exit name, any side) to the signal second; none = infinite. reentry_30 = gap_min < 30 (the live same-side blackout length).
- chase_k: ((signal price - session open price) x side) / ATR5 at the signal, session open = open of the first 1-min bar of the session, ATR5 = the 5-min ATR(14 Wilder) used by REG (r13_rules.Bars5). chasing = chase_k > 1.0 (grid 0.75-2.0).
- ctx tag (fixed at entry): "fresh" = n_sess <= 2 and not chasing and gap_min >= 30; "rechase" = everything else (3rd+, or inside 30 min of the last P7 exit, or chasing). Variants named in the sets: by lots (>=5 lots / <5), by side (long / short).
- leg (for D3/D5, W-C owns D3): since the last opposite-direction P7 SIGNAL (taken or not) or the session start; pullback number = count of same-direction P7 signals in the leg including this one.
Implementation: code/th_works_b/wb_ctx.py (engine hook state: last P7 exit time per label, session counters kept in the hook from the engine's own trades; chase_k from the 1-min bars of the engine).
