# REDO_TAIL4_RETIE (TAIL-4, 2026-11-01 ~22:00Z): every NOT-TIED ledger row classified

Universe: ledger rows (in_old_ledger) of scored_rows_latest.csv with tie != tied, using the REDO-4 tie logic of assemble.py: 1,385 NOT TIED + 4 tie unknown = 1,389 rows (the 1,361 of the 21:17Z count plus rows from later vectors). All 1,389 classified, 0 unclassified.
File: out/recent_wins/redo/NOT_TIED_CLASSIFICATION.csv (rkey, program, cause_class, cause_detail, resolved_by, status, old stored L3M, redo L3M, variant old/new L3M, variant_file). D6_TB4B old-prefix windows (all windows): NOT_TIED_D6TB4B_oldprefix_values.csv. Workers' bulk: /mnt/l2/l2vast/ds3_redo_tail4/. Code: code/recent_wins_redo/TAIL4/. No other agent's vector changed. No PASS claims.

| cause class | rows | resolution |
|---|---|---|
| D6_TB4B (THL 137, THP 121, EXP1 30, CUTWAIT 11) | 299 | TIED in old-prefix variant (100%); variant L3M equals redo L3M because the L3M window is after 2026-02-06; the old-prefix variant matters for old windows/HOLD |
| BARS-ENG | 497 (493 NOT TIED + 4 unknown) | assembly artifact: view AND-ed the earlier B vector flag; delivered D1 vector ties (1 TIED, 496 TIED_TAPE2: stored file predates the TAPE-2 de-dup fix, row equals the TAPE-2 rebuild) |
| META FS2 | 442 | 363 explained, pinned counterfactual ties bit-exact; 79 (H3 logistic head) irreproducible: original code on original inputs misses its own stored predictions on 44,289/47,131 rows |
| EINT2 | 46 | NEW (TAIL-4): counterfactual with stored old multipliers pinned on old tids through the REDO lock engine: 46/46 reproduce stored old L3M at 1e-6/$1 (monthend flags, corr median fill) |
| EINT1 bar_vol_rel | 20 | counterfactual ties 20/20 (D2); new-window cf values added by TAIL-4 from the cf daily lines |
| CONFIRM-BARS 25 + CF-SUBMIN 2 | 27 | NEW (TAIL-4): program's own bars_ext/subm_ext unchanged on the ORIGINAL bar store (out/bars_store) with redo layers: 27/27 tie stored old L3M (pts and $ 1e-6). Defective-tape days all <= 20260202 so new windows (2026-05..10) contain no defective bar |
| UF-ENTRY c1 21 / c2 31 / c3 1 | 53 | tied at store whole-dollar rounding (|d$| max 0.47/0.50/0.44 < 0.5); the view AND-ed a stricter flag. The "0.51 $" row of TAIL-6 is not among the ledger rows (all ledger c1 rows <0.5) |
| UF-LOSS c3 | 1 | stored live $ 23,590 inconsistent with its own pts (954 x 0.671 x 20 x 7 = 89,664); pts-level L3M ties; declared irreproducible |
| THPC2 loss qr/haz | 4 | declared irreproducible: one rng stream for profit then loss fits shifts when data extends; no stored RNG state |

Net: tied variant exists for 1,305 rows; explicit irreproducible declaration for 84 (79 H3, 4 THPC2 loss, 1 UF-LOSS c3). Not in this ledger list: THL2 reg cells (8 non-ledger L2P cells), D8 and new D7 tie files (all True).
Old L3M -> redo L3M means (view only; units differ): D6_TB4B THL +3.36->-1.96 pts, THP +3.52->+2.37, EXP1 +2.39->-3.21, CUTWAIT +5,764->-1,858 $/wk; BARS-ENG +3.44->-4.65 pts; META FS2 +6,890->-2,411 $/wk (H3: +8,699->-2,492); EINT2 +4,230->-454; EINT1 +7,113->+3,149 (cf +3,078); CONFIRM/SUBMIN +1.7->-0.5 pts.
