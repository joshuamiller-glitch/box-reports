# PREREG_LAYERS (W-LAYERS, 2026-11-19) - written before any layered set of a beats-live candidate is scored
Scope: engineering + the same selection protocol as XA3 (NEW_BOOK_LAYER_PLAN.md section 3), applied automatically to every D8 candidate with verdict 'yes' in D8_CANDIDATES.txt (REPLACE row of the book it beats is the base).
Sets: ID1-ID9 identity; 58 single-layer settings (TK 12, LK 9, CU 4, CX 3, CP 4, BO 3, NT 5, DD 18) + 14 W-FASTR picks; joint sets = best setting of every layer plus one-layer deviations to the 2nd/3rd best.
Identity criterion: each ID set equals its base row trade for trade (book, exit_ns, gross, lots, net_fee) on 202610 and 202608; any difference = FAIL, no fit set of that session is queued.
Fit window: last 6 months (202605-202610), 3 months beside (202608-202610). Metric order: stack ulcer first, worst week, max drawdown, mean $/week (base lots, $4.84 RT); eligibility: trades >= 80% of the base row and d ulcer < 0.
Prior years: top-2 eligible settings per layer on 202304-202604 (amber 15-30% worse, red > 30% worse vs the base). Joint: top-3 eligible per layer, L6M, then prior years + 30 layered date-shift controls (to follow). No label without the controls.
Verification of the generator: layer_gen.py verify rebuilds the XA3 sets and requires 81/81 identical JSONs (done 2026-11-19: 81/81).
Asia NTZ windows (no existing XA3 equivalent): 1800-1830, 1830-1900, 1900-1930, 1930-2000, 2000-2030 ET (the first five 30-minute windows of the session; events cluster 18:00-02:00 ET).
