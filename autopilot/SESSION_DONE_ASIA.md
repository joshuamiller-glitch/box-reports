# SESSION_DONE_ASIA (DRAFT, W-ASIAFINAL, ~13:40Z 2026-11-24; NOT declared; read-only compile, gaps flagged)
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

## New books, coding spec (as far as files give it)
- L9c2622b0.BRP45: bar pnf_7 (point-and-figure, price-path, unaffected by print rule), trigger levels_vwap break {n 3, k 0.5}, plain60/60 base; step-2 shape BRP45 (R0BR, truly bare). Exit result (D8_EXIT_SCREEN): long-only best stop wall 2 + swing trail 1, +158 L6M; both-side best clock 0825/0955/1155 + vol stop 1.5, +211; short-only no eligible exit. Exit run rows: EXflowp_v15_t2 38 set-months, EXv25_t2 6, EXpk56622e 6, EXbricks3_v25 6, CEX families v25_t2/sar/oppx/flow/bricks3 6 each. GAPS: exact BRP45 bracket numbers, inputs file, parity vectors: not assembled.
- L4aaacdb2.BRP30: bar and trigger NOT FOUND in D8_EXIT_SCREEN (0 rows); only the set name/shape BRP30 and CANC base (42 months landed). Exit run rows present: CEXflowp_v15_t2 38, CEXv25_t2 / sar_v40 / sar_v15 / oppx_v25 / oppx_v15_t2 / flow_v25 / bricks3_v25 6 each; no D8_EXIT_SCREEN verdict. GAP: bar rule, trigger, bracket, exit result.
- Lb0e6dfa3.BRF40_80: tm240 (time bar) structure_libpattern nr n7, bracket F40_80; exit screen: clock + vol stop +284 L6M; exit rows EXv25_t2 6, EXbricks3 6, CEX v25_t2/sar_v40/sar_v15/oppx_v25/oppx_v15_t2/flow_v25/flowp_v15_t2/bricks3_v25 6 each.
- L385f4f2e.J502: spec already in D8_BUILD_SPEC.md option A; exit rows EXflowp_v15_t2 39, CEXflowp 38, J502CEX* families 6 each.

## Layers
Joint stage (ASIA_JOINT_TABLE 13:07Z): J502 NOT KEPT (no combo beats reference, keeps today's settings); no rows for Lb0e6dfa3, L9c2622b0, L4aaacdb2 = not fitted. fitted_books.json Asia holds only M7ea48296. Luck test for the new mix: controls 30/26/30 (loop result). 2-lot fit of the new stack: not started.
Gates NOT blocking the pick: weighted-loop "waiting 30 sets" (counter artifact, controls L6M-only, all landed); "28 waiting for controls" (31 W-BRKT books early-stopped D_stop, failed gate d by design); "books fitted 1 of 87" (counts fitted_books.json; fits follow the pick).
