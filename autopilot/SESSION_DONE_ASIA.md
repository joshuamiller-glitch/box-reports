# SESSION_DONE_ASIA (DRAFT, W-ASIAFINAL, updated ~13:45Z 2026-11-24; NOT declared; read-only compile, gaps flagged)
STATUS: DONE steps a-b. c exit verdicts below (computed read-only by W-ASIAFINAL from landed sets; scorer stage 2 page not posted by W-EXITENG). d joint (W-LAYERS2 running, new stack not fitted). e coding specs: complete in D8_BUILD_SPEC.md (book blocks), listed below.
Pool 87 (hash 0d89b81689), unchanged since 06:08Z. The 17 books of the 598 landed rows are judged: all 17 fail (aln_state), so the pool cannot change from them.

## Final books and sizes per FINAL (1-lot base dollars)
| loop | books (size) | controls | L6M ulcer / $wk | L3M $wk | 2023 / 2024 / 2025 $wk |
|---|---|---|---|---|---|
| asia-own, own-recent (equal) | L385f4f2e.J502 (1) | 30/27/30 | 469 / 2,157 | 2,514 | 40 / 217 / 179 |
| asia-stay, stay-w | Lb0e6dfa3.BRF40_80 (1) | 29/20/30 | 2,643 / 2,969 | 1,930 | 386 / 506 / 690 |
| asia-own-w | Lb0e6dfa3.BRF40_80, L385f4f2e.J502, L9c2622b0.BRP45, L4aaacdb2.BRP30 (all 1) | 30/26/30 | 2,604 / 7,107 | 5,884 | 727 / 1,214 / 890 |

## Bare vs bare D7 (BARE_D7_YARDSTICK.md, 11-20; bare D7 Asia stack 1 lot: L6M $5,654/wk at ulcer 13,133, L3M $3,191)
At equal ulcer the bare D7 stack gives: J502 case (ulcer 469) $137/wk L6M; weighted mix (ulcer 2,604) $762/wk L6M, L3M $415 (weighted page), prior years 2023/24/25 $3 / $267 / $188 at the same-risk basis. Stack vs bare L6M: +$2,020/wk (J502), weighted $7,107 vs $762. L3M and prior years beside as in the table above. Stay-final vs bare at its ulcer: NOT IN FILES (not extracted).

## The five books
Stay (in a FINAL): Lb0e6dfa3.BRF40_80, L385f4f2e.J502. Go (pool members, in no FINAL): L92a90948, L6b373671.BRP60, L578701ed.

## Exit-run verdicts (c). Sources: _exiteng/stack_exit_state.json (stage 1 = exit ulcer below the bare set on L6M and L3M), landed exit sets, bare R0 reference. 1-lot $/wk
| member | result | numbers |
|---|---|---|
| L385f4f2e.J502 | NO EXIT KEPT (all 8 families fail stage 1) | bare ulcer L6M 469, L3M 519; best-ulcer exit flowp_v15_t2 L6M ulcer 786 mean $162; others ulcer 1,774-3,805 |
| Lb0e6dfa3.BRF40_80 | NO EXIT KEPT (all 8 families fail stage 1) | bare L6M ulcer 2,643; exits 4,253-32,541; L3M bare 3,040, exits 3,131-16,264 |
| L9c2622b0.BRP45 | NO EXIT KEPT by my reading (flowp_v15_t2 passes stage 1, fails on money) | L6M ulcer 1,272 vs 2,369 bare, but mean $244 vs $1,845; L3M mean $72 vs $1,523; 2023/24/25 mean -$48 / -$111 / -$302 vs bare +$301 / +$442 / +$424; 2025 ulcer 10,960 vs 5,292. 30/30 controls landed, real beats 30 of 30 (a low-activity effect). The other 7 families fail stage 1 |
| L4aaacdb2.BRP30 | NO EXIT KEPT by my reading (same pattern) | flowp_v15_t2 L6M ulcer 850 vs 1,348, mean $15 vs $531; L3M $15 vs $374; 2023/24/25 -$25 / -$123 / -$108 vs bare +$205 / +$70 / +$147; controls 29 of 30. Others fail stage 1 |
Caveat: the stage-2 PASS/FAIL line is not posted by W-EXITENG; the "kept" rule used by D8_EXIT_SCREEN (L6M>0, L3M>0, no red prior year, lowest ulcer) rejects flowp_v15_t2 on both books because every prior year is negative. D8_EXIT_SCREEN.md separately lists screen exits for Lb0e6dfa3 (clock 0825/0955/1155 + vol stop 1.5, +284 L6M) and L9c2622b0 (both sides same clock+vol stop +211; long-only wall/swing-trail +158): these are on the cell's own base entries, not at the stack bracket, and were not confirmed at the stack bracket. Treat the bare bracket as the stack-bracket answer unless W-EXITENG says otherwise.

## New books: coding specs (full text in D8_BUILD_SPEC.md between <!-- AUTO:BOOK:... --> markers; parity packs D8_PARITY_<id>_20261027/20261110.md)
- L9c2622b0.BRP45 (spec block lines 492-508): bar pnf_7 point-and-figure, box = max(1, round(7 x s_rng)) ticks (15 ticks 10-27, 21 ticks 11-10), 3-box reversal, one bar per completed column, unaffected by print rule, Asia 18:00-02:00 ET (th_bars/kernels.py k_pnf). Trigger trig_levels_vwap plain break n 3 k 0.5, unit 5.0 pts (D8_TRIGGER_DEFS 3.7): long when closes of bars j, j-1, j-2 > L + 2.5 and j-3 <= L + 2.5, short mirrored, lines VWAP0, YVWAP, AVPDH, AVPDL, WVWAP, MVWAP in Asia, first line that fires, both -> dropped. Both sides (the ladder label says long). Bracket fixed 45/45 pts, 1 lot, market entry at signal +2 s, fill +1 s walking the book, session-end flat 02:00 ET. Filter none. Inputs: NQ trades plus 1-minute NQ series for the VWAP lines. 5,845 events; trigger verified 5,845 of 5,845. Exit: none kept. GAP: 20261110 parity TRADES block OPEN (month not landed).
- L4aaacdb2.BRP30 (block lines 511-530): bar vsess_30 session-volume clock, threshold = max(trailing-20-session median Asia volume / 30, 1) contracts (2,076.7 on 10-27, 2,840.4 on 11-10), close at first print reaching it, run-merged prints (_CANC), affected by print rule. Trigger trig_bands_vwap break, minbars 20, k 1.0: per session tp = (h+l+c)/3, volume-weighted vwap and sd, bands vwap +- 1.0 sd defined from 0-based bar 20; long on first close above up, short on first close below lo. Both sides. Bracket fixed 30/30 pts, 1 lot, same entry rules. Filter none. Inputs NQ trades only. 1,485 events; verified 1,485 of 1,485. Exit: none kept. GAP: 20261110 parity TRADES block OPEN.
- Also needed from the same file: Lb0e6dfa3 block (line 311, tm240 libpattern nr n7, 40/80) and the J502 block (option A, line 53 area).

## Layers
Joint stage (W-LAYERS2 running; ASIA_JOINT_TABLE 13:07Z): J502 NOT KEPT (no combo beats reference, keeps today's settings); no rows for Lb0e6dfa3, L9c2622b0, L4aaacdb2 = not fitted. fitted_books.json Asia holds only M7ea48296. Luck test for the new mix: controls 30/26/30 (loop result). 2-lot fit of the new stack: not started.
Gates NOT blocking the pick: weighted-loop "waiting 30 sets" (counter artifact, controls L6M-only, all landed); "28 waiting for controls" (31 W-BRKT books early-stopped D_stop, failed gate d by design); "books fitted 1 of 87" (counts fitted_books.json; fits follow the pick).
