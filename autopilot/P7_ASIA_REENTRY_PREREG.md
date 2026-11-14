# P7 ASIA RE-ENTRY PREREG (W-PR, PRIORITY 3, 2026-11-14)
Base: JN05W2 exact engine (all layers ON, incl. existing c_gov: skip after >=2 same-side losers with no new session extreme). Hook: code/th_p7re/pr_hooks.py (outermost), identity proof TL3_PR_ID (empty par) must equal JN05W2 202610 (598 trades, net 25943.82).
Scope: P7, Asia (18:00-02:00 ET), signal second only. Loser = closed P7-Asia trade net_fee<0 (one loser is enough, not two).
Cells (15): BLK_EXT BLK_ENT BLK_M30 BLK_M60 BLK_M120 BLK_OPP BLK_HL | HALF | CAP2 CAP3 CAP4 | RCAP10 RCAP15 RCAP20 | SN. Specs: see pr_hooks.py docstring.
Stages: L3M (202608-202610) all cells -> L6M (202605-07) + HOLD (202511-202604) + PRE (202410-202506) + X'/GAP (all 43 months 202304-202610) for cells passing the tolerant gate in L3M, plus any cell leading on first-order tables. Gate: maxDD not worse by >2%, worst week not worse by >2% of ref, mean not lower by >3%, in every window present, at least one window with DD cut >0; lead must hold in BOTH recent and older windows.
Metrics: max DD (cum daily), worst week, full stops/wk, best-5 weeks kept, winning weeks turned losing, mean $/wk; also stack-with-2026-W44-removed.
Placebos on finalists: pa (random block, same eligibility, same-count in expectation, 3 seeds) and sh (evidence on price path 11/23/37 days earlier).
Walk-forward every 2 weeks on first-order table (pick best rule by trailing data, apply to next 2 weeks).
