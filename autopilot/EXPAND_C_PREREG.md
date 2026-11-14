# EXPAND_C_PREREG (W-EC, T-EXPAND family C), 2026-11-14 ~21:10Z, logged before scoring
Base JN05W2 exact engine (TP_ENGINE=1, all layers ON, measured fills, $4.84 RT), hook code/th_expand_c/ec3_hooks.py (additive, outermost), cells code/th_expand_c/ec_cells.py.
Sessions: asia 18:00-02:00, london 02:00-08:30, pre 08:30-09:30 (engine has no entries: vacuous), nyam 09:30-12:00, nypm 12:00-15:00, l90 14:30-16:00 (engine entries only to ~15:00). Each rule gates its own session only.
(1) range-used-up: F = W-R2 session forecast (fc_r2_har HAR, fc_r2_v1 HAR+CME, used only at now >= t_avail) x last 1m close; rem = F - range so far from the forecast read start; skip / half / shrink if stop*target_r > k*rem; k .5/.75/1/1.25 (+1.5/2 later); books K7 P7 U7 H7 M7 A7 O7.
(2) clock: no new entries in last 15/30/45 min, first 5/10/15(/30) min of the session; all books, then per book.
(3) caps on closed trades inside the session instance (R = $1,200): loss_r 1/1.5/2/3, profit_r 2/3/4, closes n 3/5/8/12, conjunction n 4/8/12 with net <= -1/-2 R (C22 session version); stack-wide and per book.
(4) neighbour sessions tested for every rule (no transfer assumed).
Gate: tolerant (maxDD not worse than 2%, worst week not worse than 2% of ref, mean not lower than 3%) in session scope; promotion L3M -> L6M -> HOLD -> GAP -> PRE -> X'; lead = gate in all present windows and L6M DD cut > 0. Placebos: forecast shifted 11/23/37 panel days (range-so-far real) for RU skip cells passing L3M. Identity: TL3_EC_ID / ID0 on 202610 = 598 trades 25,943.82. W44-removed DD beside every DD. No PASS claims.
