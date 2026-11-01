# REDO_TAIL3 (TAIL-3, 2026-11-01 ~22:08Z)
Cap 20261030 (last session day), de-duplicated tape, program code unchanged (paths/cap only). All old windows tied first: bit-exact in every delivered row. Vectors in l2vast/ds3/out/recent_wins/redo/vec/ (T3__* and D7__*; each with tie/pend csv); window tables in out/recent_wins/redo/{exp1_loss,exp1_vollo,exp2b,exp2d}/. Code: l2vast/ds3/code/recent_wins_redo/T3/ (t3_*.py). Bulk: /mnt/l2/l2vast/ds3_redo_tail3/.

| item | ledger rows | extended | tied | NOT TIED | note | old L3M -> new L3M mean |
|---|---|---|---|---|---|---|
| EXP1 loss chains (P11) | 6 | 6 | 6 | 0 | streams = REDO-7 cells + D4 trades; entry/closed ts, vol tag identical on all old trades; chains via exp1_panel.run_chain; vec D7__EXP1-loss-chains | +0.059 -> +0.568 pts |
| EXP1 vol_lo+ON take@50% | 2 | 2 | 2 | 0 | v0 and causal key; vec D7__EXP1-volloON | +2.895 -> +2.384 pts |
| EXP2 (b) wide-bracket | 4 | 4 | 4 | 0 | chains (Ctx.chain) identical to stored on all old trades; vec D7__EXP2b | +0.413 -> -0.264 pts |
| EXP2 (d) joint stack | 2 (P, NB:B_FROZEN) | 2 (+3 non-ledger) | all | 0 | lock-engine lines on D5S REDO env, 773 old days diff 0.0; P uses REDO-8 ol_P.npz btab cell (validated by the joint tie); vec T3__EXP2d | see windows_EXP2d |
| EQR frame A | 38 | 38 | 38 | 0 | re-scored from _C_lj_main3: identical to C__EQR (already main3-based; main/main2 not used) ; T3__EQR-A | - |
| EQR frame B | 5 ledger (13 rkeys) | 13 | 13 | 0 | L2SL stack (ALL296 stream built under redo_boot) + EXP2 joint; T3__EQR-B | rkey mean $/wk +6,674 -> -7,411 |
| EQR frame H | 2 ledger (3 rkeys) | 3 | 3 | 0 | lp_stack on REDO env, series diff 0.0 to Feb-06; T3__EQR-H | +40,203 -> +15,850 $/wk |
| EQR frame F | 1 ledger (2 rkeys) | 2 | 2 | 0 | CUTWAIT res pkls (REDO-4C); T3__EQR-F | SM +9,035 -> +12,574; HM +3,909 -> -11,026 $/wk |
| EQR frame C (HM5R, HM5M, C1, A06+HM5R(+B02), HM5R+B02) | 6 | 0 | - | - | CANNOT EXTEND by 22:25Z: needs (i) section-E HM5 sibling per-trade P&L (stke_run machinery, 5-min bar rows on REDO tape, SEALED_e_hm.pkl) and (ii) the C1 chop-week trade-table simulation (stk_c); neither has a REDO builder | |
| EQR frame D PROFIT_alone | 1 | 0 | - | - | BLOCKED on REDO-8: needs dipentry add2_stacks.pkl (de_add2.py ported in D8/dipentry but life ticks dir /mnt/l2/l2vast/ds3_redo_d8/dipentry/life and add2_stacks.pkl not built) | |

Disclosure: no breach; no old-tree file written (t3_stream_all.py was run under redo_boot, output to /mnt/.../ds3_redo_tail3 only).
