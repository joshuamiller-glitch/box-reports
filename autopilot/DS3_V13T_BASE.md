# D7 V13T BASE (truth base after the user answers, BASE-4, 2026-11-02T13:14Z)

**Call:** `import sys; sys.path.insert(0,"l2vast/ds3/code/d7base"); import d7_v13t as V13T; r = V13T.run_v13t(ov=None)` = V13Z with lines EMPTY and lock none (per-book locks only) plus the per-book lock exit-cancel fix (`lockfix="legs"` default; `lockfix=False` == V13Z exactly, tie-out max|cube diff| 0.0 $); `mktcost=0.80` sets the market-exit cost of the TH-L2 loss cut to the live 0.80 pt (shift +0.195 pt per lot; default 0.995 as built). `import use_t` is not needed: run_v13t patches and restores. Episodes lookup: DS3_ZONES_EPISODES_V13Y.md (V13Z lines-on cubes; recompute with the V13T cubes).

**User answers applied:** fill basis N; the five take lines pulled from live (lines empty); resting 30% cancelled on ANY exit (L2Disarm first); no combined stack lock (lock none = per-book 12R week floor + day give-back arm 2R keep 50% + per-book daily max P/L + ER(20)); live take grid 1 s; market exit 0.80 +- 0.22.

## Base lines (lock none): mean $k/wk (MDE) / maxDD $k / worst-20 $k / Calmar
| base | F9 | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|
| V13Z lines-empty, lock none (old lock engine) | 33.7 (28.6) / DD 132.1 / w20 -297 / Cal 0.26 | 12.7 (94.8) / DD 97.7 / w20 -98 / Cal 0.13 | 23.4 (65.9) / DD 97.7 / w20 -134 / Cal 0.24 | 15.5 (45.8) / DD 97.7 / w20 -166 / Cal 0.16 | 37.1 (37.9) / DD 132.1 / w20 120 / Cal 0.28 | 31.2 (23.5) / DD 139.2 / w20 -541 / Cal 0.22 | 23.3 (33.0) / DD 51.2 / w20 -75 / Cal 0.46 | 17.1 (14.8) / DD 166.3 / w20 -753 / Cal 0.10 | 4.7 (12.3) / DD 91.2 / w20 -446 / Cal 0.05 |
| V13T lockfix OFF (== V13Z) | 33.7 (28.6) / DD 132.1 / w20 -297 / Cal 0.26 | 12.7 (94.8) / DD 97.7 / w20 -98 / Cal 0.13 | 23.4 (65.9) / DD 97.7 / w20 -134 / Cal 0.24 | 15.5 (45.8) / DD 97.7 / w20 -166 / Cal 0.16 | 37.1 (37.9) / DD 132.1 / w20 120 / Cal 0.28 | 31.2 (23.5) / DD 139.2 / w20 -541 / Cal 0.22 | 23.3 (33.0) / DD 51.2 / w20 -75 / Cal 0.46 | 17.1 (14.8) / DD 166.3 / w20 -753 / Cal 0.10 | 4.7 (12.3) / DD 91.2 / w20 -446 / Cal 0.05 |
| V13T lockfix=cancel (cancel + 70%-leg flatten only) | 33.3 (28.6) / DD 136.3 / w20 -306 / Cal 0.24 | 12.5 (95.1) / DD 98.2 / w20 -98 / Cal 0.13 | 23.2 (65.9) / DD 98.2 / w20 -135 / Cal 0.24 | 15.2 (45.8) / DD 98.2 / w20 -167 / Cal 0.16 | 36.7 (37.9) / DD 136.3 / w20 113 / Cal 0.27 | 30.9 (23.5) / DD 140.8 / w20 -551 / Cal 0.22 | 22.9 (33.1) / DD 52.8 / w20 -77 / Cal 0.43 | 17.0 (14.8) / DD 166.3 / w20 -757 / Cal 0.10 | 4.7 (12.3) / DD 91.7 / w20 -448 / Cal 0.05 |
| V13T lockfix=legs (DEFAULT) | 32.8 (29.0) / DD 163.6 / w20 -325 / Cal 0.20 | 12.5 (93.2) / DD 95.3 / w20 -95 / Cal 0.13 | 21.2 (67.1) / DD 95.3 / w20 -132 / Cal 0.22 | 14.0 (46.4) / DD 95.3 / w20 -166 / Cal 0.15 | 35.8 (38.6) / DD 163.6 / w20 79 / Cal 0.22 | 29.4 (24.0) / DD 163.6 / w20 -606 / Cal 0.18 | 23.5 (32.5) / DD 44.9 / w20 -69 / Cal 0.52 | 16.9 (15.4) / DD 167.2 / w20 -796 / Cal 0.10 | 4.6 (12.3) / DD 94.2 / w20 -451 / Cal 0.05 |
| V13T legs + market-exit cost 0.80 | 33.9 (28.9) / DD 149.2 / w20 -303 / Cal 0.23 | 13.3 (92.5) / DD 93.7 / w20 -94 / Cal 0.14 | 22.1 (66.8) / DD 93.7 / w20 -130 / Cal 0.24 | 14.9 (46.2) / DD 93.7 / w20 -162 / Cal 0.16 | 36.9 (38.5) / DD 149.2 / w20 102 / Cal 0.25 | 30.6 (23.8) / DD 149.2 / w20 -571 / Cal 0.21 | 24.2 (32.6) / DD 43.4 / w20 -69 / Cal 0.56 | 17.5 (15.4) / DD 165.0 / w20 -783 / Cal 0.11 | 5.0 (12.3) / DD 91.9 / w20 -443 / Cal 0.05 |


## Effect of the lock exit-cancel fix and of mktcost 0.80 (V13T minus V13Z lines-empty)
| variant | F9 | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|
| cancel | d mean -0.4k (MDE 0.2); maxDD 132.1 -> 136.3 | d mean -0.2k (MDE 0.3); maxDD 97.7 -> 98.2 | d mean -0.3k (MDE 0.2); maxDD 97.7 -> 98.2 | d mean -0.2k (MDE 0.1); maxDD 97.7 -> 98.2 | d mean -0.4k (MDE 0.2); maxDD 132.1 -> 136.3 | d mean -0.3k (MDE 0.1); maxDD 139.2 -> 140.8 | d mean -0.4k (MDE 0.2); maxDD 51.2 -> 52.8 | d mean -0.1k (MDE 0.1); maxDD 166.3 -> 166.3 | d mean -0.0k (MDE 0.1); maxDD 91.2 -> 91.7 |
| legs | d mean -0.9k (MDE 2.0); maxDD 132.1 -> 163.6 | d mean -0.3k (MDE 2.1); maxDD 97.7 -> 95.3 | d mean -2.3k (MDE 6.4); maxDD 97.7 -> 95.3 | d mean -1.5k (MDE 4.5); maxDD 97.7 -> 95.3 | d mean -1.3k (MDE 2.7); maxDD 132.1 -> 163.6 | d mean -1.8k (MDE 2.8); maxDD 139.2 -> 163.6 | d mean +0.2k (MDE 1.8); maxDD 51.2 -> 44.9 | d mean -0.2k (MDE 2.0); maxDD 166.3 -> 167.2 | d mean -0.1k (MDE 0.3); maxDD 91.2 -> 94.2 |
| legs_mk80 | d mean +0.2k (MDE 2.0); maxDD 132.1 -> 149.2 | d mean +0.5k (MDE 2.7); maxDD 97.7 -> 93.7 | d mean -1.4k (MDE 6.5); maxDD 97.7 -> 93.7 | d mean -0.6k (MDE 4.5); maxDD 97.7 -> 93.7 | d mean -0.2k (MDE 2.6); maxDD 132.1 -> 149.2 | d mean -0.6k (MDE 2.9); maxDD 139.2 -> 149.2 | d mean +0.9k (MDE 1.8); maxDD 51.2 -> 43.4 | d mean +0.4k (MDE 2.0); maxDD 166.3 -> 165.0 | d mean +0.3k (MDE 0.3); maxDD 91.2 -> 91.9 |


## EXIT-CANCEL AUDIT (confirm that a resting add can never fill after the 70% leg has exited)
| exit type | handled by | status |
|---|---|---|
| original stop / target / session flat | add-fill kernels fill only before the original exit (limit k1-1 in the B73 kernel; same in the split kernel) | covered by construction |
| TH-L2 loss cut | V13Y compose fix (exit before the fill cancels the add; 70% leg only) | covered since V13Y |
| profit take / tighten lines | same compose hook | covered (lines are pulled from live; empty in V13T) |
| per-book lock: week floor 12R, day give-back arm 2R keep 50% | oc_lib._stage (old: valued both legs at the add price from entry and flattened both even when the add was unfilled) | NOT covered by V13Y/V13Z; FIXED in V13T. In the V13Z lines-empty lock-none run 735 trades were lock-forced and 283 of them (38%) were flattened while the add was still unfilled (lock 12R frame: 211 of 674) |
| per-book daily max P/L (pb_win 5R / pb_loss 2R) | entry gate on realised day P&L, no order carried through | no ordering issue |
| combined all-books stack lock (lock=12) | same flaw as the per-book stage | NOT fixed; not live; V13T uses lock none |
| Asia stack cut 50% at stop events | position-level lot cut at the stop | unchanged |
Generic 70/30 split rows and OTE-62 B73 rows are both covered (the same row structure: l1/l2, fill index, fill price). Remaining approximation: the lock MTM treats the cancelled add as never existing from the lock fire onward but, in lockfix=cancel mode, still values the pre-fill period with the full row; lockfix=legs removes that too (two legs, the add from its fill second).
