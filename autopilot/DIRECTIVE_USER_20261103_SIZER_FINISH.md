# USER ORDER 2026-11-03 13:30Z: finish T-SIZER on all cores; answers from DS7.cs (replace every assumption)
LIVE ORDER OF LOT OPERATIONS: session-table lots -> A06 slot x0.5 (if the ENTRY ET half-hour is in the book's list) -> B02 x0.5 (K7/P7/H7, entries 10:30-17:59 ET, on a quiet-overnight day), both inside SessionLotsAt with ONE rounding floor(lots*mult+0.5), min 1 -> ER ladder (x0.5 below 0.30, x1.0 at/above, LIVE since 2026-11-02 19:30Z = Q1-A; rounded, min 1) -> signal-state (Shadow, no effect) -> zone HALF floor(lots*0.5+0.5), min 1. Live order is session -> slot/B02 -> ER -> zone (NOT session -> zone -> ER). Re-key the ts base to this order.
A06 lists (ET half-hour of the ENTRY): P7 0330,0500,0830; K7 0330,0400,0430,0500,0530,1430,1900,1930,2030,2100; H7 0400,0530,0830,1030,1230,1300,1400,1830; U7 0200,0830; S7 (not live) 0330,0430,0500,1130,1230,1400,1430,1900.
B02: at 10:30 ET, overnight range (18:00 -> 09:30 ET) vs median of the last 20; range < 0.85 x median -> QUIET -> K7/P7/H7 lots x0.5 for entries 10:30-17:59 ET; not re-evaluated during the day.
ER gap handling (live): ER(20) on the chart's 5-min series last 20 CLOSED bars, NO session-break logic (first signals after the 17:00-18:00 break / weekend use pre-break bars: the 4.4% stale case). No neutralise rule live; STALE_X1/X05 no flag -> leave as is.
Lock: per-book 12R week floor + 2R/50% day give-back + daily +-R caps, scope PerBook, lock R scaled only when mult > 1 (Q1-A has mult <= 1, so never). 'No give-back' = one episode, not changing.
Split for PE only: not changing; keep the split everywhere; forward register decides.
BT swing flip: coded in D7 v1.4 as Shadow (forward_register/bt_flip_shadow.csv + bt_flip_events.csv), installed Tue 2026-11-03; first Monday read 2026-11-09.
REMAINING T-SIZER (48-h final due Wed 2026-11-04 ~18:00Z):
 (1) Section 3.2 combinations (best 2-3 sizers; min-down / all-up / multiply) and 3.3 learned mapping (<=6 leaves, monotone, purged walk-forward, 3 seeds) on the re-keyed ts base; the pool exists (pool_inputs_s1/s2 with genuine PA9). Run it.
 (2) Section 3.5 sizer x lock re-tuned together under Q1-A: is 12R floor / 2R-50% give-back still the best lock under the size-down-only ladder.
 (3) Q1-A is the new reference for every table: re-state the top 20 cells of every section vs Q1-A (not vs the x1.5 ladder).
 (4) Lots distribution + worst-day exposure for Q1-A, the 3-tier cell, K_PE and the KB-asia weak flag, per book x session, in ONE table: SIZER_EXPOSURE.md.
 (5) Addendum 2.1 (sizer on the 30% add): 'no feature tells which adds to drop'; add ER-at-add x0.5/x1.0 cells under Q1-A, then close it.
 (6) Final: DS3_SIZER.md plain sentence + sizer_policy.txt proposal (even 'live Q1-A ladder, no change') + exact definitions of anything that beats Q1-A on L6M AND PRE with the carrying week dropped, placebo-clean, flagged the same hour.
Zero workers is never a state; MORNING.md every 30 min with the load line. After T-SIZER: standing programs (ledger monthly refit, THP_POLICY refit 23:00Z daily, forward register weekly), nothing idle: propose the next program in MORNING.md for the user's OK.
