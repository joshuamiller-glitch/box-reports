# USER PASTE 2026-11-02 02:45Z (saved verbatim)
D7 v1.3 EXACT. Base definitions, replace your assumptions:
U7 blackout: after a TH-L2 loss cut on U7, no SAME-SIDE U7 entry for 30 min (ThL2BlackoutMins=30, books "U7", same-side only). K7/H7/M7 = K6/H6/M6 code unchanged; NY-AM lots 1 (K7 "2,2,0,1,2,0", H7 "4,0,0,1,0,0", M7 "0,2,0,1,0,0"). TH-L2 profit rule OFF. Zones HALF D20, OTE-62 B73 D30. X1-X5 and signal-state Shadow. 12R per-book week floor; day give-back lock arm 2R keep 50% per book; ER(20) sizer running-max. Native stops.
THP_POLICY_D7.txt (live, exact text):
profit  K7    *       pct>=0.70 tot_rel>=1.2                tighten 30
profit  P7    *       pct>=0.50 ahead_rel>=1.5              take
profit  H7    *       pct>=0.30 ahead_rel>=1.5              take
profit  U7    *       pct>=0.17 tot_rel>=1.5                take
profit  *     *       pct>=0.70 ahead_rel>=1.2              take
Re-run any v1.3 finalist whose base was assumed; mark the old rows "assumed base". Score these 5 take lines themselves on the v1.3 base at live lots, Feb-Oct, drawdown first (that is still owed).
