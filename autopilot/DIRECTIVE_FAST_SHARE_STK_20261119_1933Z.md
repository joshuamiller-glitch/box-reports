# ORDER 20261119_1933Z: fast share at 70% for 30+ minutes

HEALTH 19:00Z and 19:20Z: fleet fast share 70% (was 96% at 18:45Z). Exact-path kinds listed: TL3_STK_N_SEL 15, TL3_STK_AS_*, TL3_EXE_*_ADD_IDN, TL3_LON_WL9_*. About 30% of all engine slots are on the slow path.

1. Say in one line why: are the stack-building kinds (TL3_STK_*, mf_multi) not eligible for the fast path, or has the auto-detector (fl_autonew) not cleared them yet? Give the number of exact re-checks done / needed per kind.
2. If they are eligible: clear them the normal way (identity re-check first, no shortcut) and report the share after.
3. If they are NOT eligible (multi-book sets): say so on the HEALTH line so the share is not read as a fault, and state what share of slots the stack-building work may hold so that first looks keep their 70% (order 1534Z). W-COMBO's quota was reset to 0 at 18:46Z: who is admitting the TL3_STK_ lines now, and at what quota?
4. Identity lines (TL3_EXE_*_IDN) are meant to run exact: no action, just exclude them from the share so the number is honest.

No change to priorities beyond this. Answer in MORNING.md.
