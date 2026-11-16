# HANDOFF W-LA -> W-EV: FLAT vs BOOK (DIRECTIVE_FLAT_VS_BOOK_20261116) - sets are built, nothing has run
28 exact sets TL3_EV_FB_* (EV admission prefix) on TL3_EV_JN05W2JL2 (all 43 months 202304..202610 exist in the reference), list in /mnt/l2/l2vast/_deepen_la/a/fb_cells.txt (priority order, identity first). Builder code/th_deepen_la/mk_fb.py (+ mk_lf.py mk()), hook code/th_deepen_la/la_hooks.py (identity proven for the no-op path on JN05W2: TL3_LA_ID 598 / 25,943.82). Run with the same chain as before (jn05_run2.py via tp_launch, tag EV).
IDENTITY FIRST: TL3_EV_FB_ID (K7 flat 45 re-expressed through the hook, no P7 flat) must equal TL3_EV_JN05W2JL2 on 202610 (net and trade count). The exit name of my flat is LaFlat (ec_hooks' K7 flat is EarlyCut); if the stack counts differ, stop and tell me.
## Units -> parameters (stop = 60 pts; flat = adverse mid move from the entry px, decision second r, exit mid(r+1) - 0.80)
| user | hook d (pts) |
|--|--|
| K7 -0.65 / -0.75 (live) / -0.85 | 39 / 45 / 51 |
| P7 -0.60 / -0.70 (live stand-in) / -0.80 | 36 / 42 / 48 |
The engine base JN05W2JL2 has K7 flat 45 (ec_hooks) and NO P7 flat; 'as live today' = K7 45 + P7 42 (cell A_KP).
## Switches (mk_lf.mk arguments; written into the set json)
- flat ON for a book: hooklist la_hooks par flat: [{book, sess:[s], d}, ...] one rule per session; the K7 ec_hooks flat rule is emptied (K7 flat lives in la_hooks).
- flat OFF: no flat rule for the book (K7={'all': None}).
- BOOK-BASED CUT OFF (flat only): la_hooks par scut: [{book:'K7'|'P7', nocut:true}] (also overrides the P7 F3 context cell). Book ON = no scut rule (engine lines unchanged: K7 45/10x/w2/p3 var 2; P7 fresh 45/5x/w5/p10, rechase 30/10x/w5/p2).
- BOOK ARM +-10: mk(..., arm={'K7': a, 'P7': a}) edits the set json: K7 by_unit arm (all six sessions, floor 15, var-2 lots scaling kept) and the P7 F3 fresh and rechase arms (+-10 pts each). 'Earlier' = -10, 'later' = +10.
## Cells (letters of the order)
ID | A_K7, A_P7, A_KP (book + flat) | B_K7 (K7 flat off, book on), B_P7 (= base reference row), B_KP (K7 flat off; P7 has none in base) | C_K7, C_P7, C_KP (flat only, that book's cut off) | D_K7_D39/D51, D_P7_D36/D48, D_KP_D39_D36/D51_D48 | E_{K7,P7,KP}_{M10,P10} | PC_{K7,P7}_Q{05,10,20}: persistent random-trigger controls (bucket 300, one draw per 5-min bucket per book and side, never re-drawn; marked trades cut at the first losing second after a hashed delay 0..30 min) REPLACING that book's flat: tune q until LaFlat/wk is within 20 % of the real flat's (A_K7 / A_P7), keep share not applicable.
## Scoring
code/th_deepen_la/la_score.py: score(cell, '202304') (ref_of() maps TL3_EV_FB_* to TL3_EV_JN05W2JL2): drawdown first (dd, dd_cut, dd44_cut with W44 removed, ww, best5, w2l, cuts_wk = StateCut/wk), d_mean and d_mean_484; weekly delta series la_weekly.py; weekly-cluster t / sign-flip p as in lf_page.py (copy it; it counts LaFlat per week and the $ of the cut trades vs the same entries in the reference, matched share = PATH_EFFECT caution). Windows: all six (L1M, L3M, L6M, HOLD, PRE, X', GAP) once the months are done.
## First read from my cells
None landed on JL2: my earlier JL cells (TL3_LA_L_*) never reached the engine (queue wait, LA quota went to 0) and are dropped. The only exact LA flat results are on the OLD base JN05W2 (not JL2): K7 flat -40 asia +$431/wk, london +$437/wk (L6M, $4.84, weekly t 0.7 / 1.3, DD cut 21.5 / 11.9 %, dd44 +6.5 / +12.6 %); P7 flat -40 loses money (asia -$951, london -$789, L6M); K7 state cut off beats the engine base (+$308/wk L6M, t 0.22) = live K7 is effectively flat-only. See DS3_DEEPEN_LOSS_LAYERS.md. Label these 'old base'.
