# REDO-1T2 rows - trade-library rows through 20261030 (written 2026-11-01 by REDO-1T2; research only, new files only)

Cap 20261031 (last trading label day on disk Fri 20261030). Builders = the EXISTING ones, run unchanged on the extended F (firmlib arrays through 20261030); the only changes are in my own copies under `l2vast/ds3/code/cap/redo_*.py` (paths redirected to new files, no cap constants needed lifting because these builders have none; the caps lived in the downstream index/sb1 steps). Old files untouched.

## Files (all under l2vast/ds3/out/redo/rows/)
| book | new file | builder (existing) | my script |
|---|---|---|---|
| PE (P6) entries | PB3_PB3B_R5_P1_trades_redo.parquet | pb3_core2.events2(5,1,0,1) -> gen_pb2('60','1R') -> bl_registry.tl_from_tab (cell PB3B_R5_P1) | cap/redo_pe.py |
| PE base rows | base_PE_redo.parquet | ba_rows2.gen('PE', events, 60, 60) | cap/redo_pe.py |
| PB | PB_ST10_SWZ_T3_lib_trades_redo.parquet | x_pb_lib.py (tp_sig.pullback('ST10','SWZ','T3',W=30) -> te_core.gen_entries) | cap/redo_pb.py |
| DN (N6) | don_tt_map_redo.parquet (+ don_T_redo.parquet raw, don_daily_map_redo.parquet) | d4a/don_lib.py (tr2_lib.cands_S('DON15') + gen3 + map_pts + run_rows lots 10) | cap/redo_dn_cr.py DN |
| CR (C6) | crt_tt_asscored_cons_redo.parquet (+ crt_T_asscored_redo.parquet, crt_setups_redo.npy) | d4a/crt_lib.py as-scored arm, cons P (sf_fam.build + sf_lib.trades_from_setups + run_rows) | cap/redo_dn_cr.py CR |
| MV (M6) | xtr1_trades_TR1A_ens_s0.5_k4_redo.parquet | x_tr1.run('TR1A_ens_s0.5_k4') (independent 1-min replay, Databento ohlcv-1m) | cap/redo_tr1.py |
| MA (MA6) | xtr1_trades_TR1C_MAMA_10m_flip_redo.parquet | x_tr1.run('TR1C_MAMA_10m_flip') | cap/redo_tr1.py |
| O6 (3 cells) | O6_trades_redo.parquet | T-OPEN B2 harness pickles (see below) | cap/redo_o6.py |
Helpers: cap/redo_tie.py (tie-out), cap/redo_check_rows.py (independent recomputation), cap/redo_check_o6.py. Tie-out JSONs: tie_PE/PB/DN/CR/MVMA/O6.json, check_rows_redo.json, check_o6.json.

Traps handled: (1) te_core tape cache -> `TC._TP=out/redo/te_tape_bar_redo.npz` set before any build; (2) te_core.mapping()/map_pts rewrites out/te/p9map.json -> `TC.OUT` redirected to out/redo/te_out/ (DN, CR); (3) x_replay's own cache xbars/NQ.npz (ended 20261016, which is why the old MV/MA ended 10-16) -> rebuilt at /mnt/l2/l2vast/ds3_redo_xbars/NQ.npz (4,741,997 bars to 2026-10-30 20:59 UTC) via `X.CACHE`; (4) sys.argv is cleared by an imported module in the DN/CR chain -> argv captured first.

## Tie-out (new file vs old file; "prefix" = new rows with exit time <= old file's last exit, compared field for field over ALL columns)
| book / table | old rows | new rows | added | old last exit | new label-day range | identical prefix | straddling rows |
|---|---|---|---|---|---|---|---|
| PE entries (PB3B_R5_P1 trades) | 8,339 | 8,417 | 78 | 2026-10-23 13:59 (entry) | 20230210-20261030 | True | 0 |
| PE cell table (direct_D1_tabs PB3B_R5_P1) | 8,339 | 8,417 | 78 | 2026-10-23 15:08 | same | True | 0 |
| PE base_PE | 8,339 | 8,417 | 78 | 2026-10-23 15:08 | same | True | 0 |
| PB (lib_trades) | 6,092 | 6,150 | 58 | 2026-10-23 13:09 | same | True | 0 |
| DN don_tt_map (incl. f, net, LIN, DI lock columns) | 4,806 | 4,847 | 41 | 2026-10-23 10:43 | same | True | 0 |
| DN raw trade table don_T | 4,806 | 4,847 | 41 | same | same | True | 0 |
| CR crt_tt_asscored_cons (incl. f, net, P, kin, kout) | 3,617 | 3,638 | 21 | 2026-10-23 10:41 | same | True | 0 |
| CR raw trade table crt_T_asscored | 3,617 | 3,638 | 21 | same | same | True | 0 |
| MV xtr1 TR1A | 7,809 | 7,960 | 151 | 2026-10-16 14:56 | same | True | 0 |
| MA xtr1 TR1C | 2,955 | 2,997 | 42 | 2026-10-16 06:35 | same | True | 0 |
No old trade changed, none dropped, none straddles the old data end (every added row has entry and exit after the old last exit). MV/MA added rows include 2026-10-17..10-23 that the old files never had (their price cache stopped 10-16). Label-day = ET bar-open + 6 h, Sat/Sun to Mon.

## Independent recomputation (30 random new label days after 20260206, seed 20261101: numpy scan on ds3_g2_redo SH/SL/SC, stop first within a second, stop-gap rule min(level, previous-second close); all trades of those days)
| book | trades | entry price | exit type | exit price |
|---|---|---|---|---|
| PE | 460 | 460/460 (epx == 1-min open o[ei]; ei == bar of et_in 460/460) | 460/460 | 460/460 exact |
| PB | 313 | 313/313 | 313/313 | 313/313 |
| DN (stop-entry: level touched inside entry bar) | 232 | 232/232 | 232/232 | 232/232 |
| MV | 433 | 433/433 | 433/433 | 433/433 (exit px = E + stored pts) |
| MA (29 days have trades) | 127 | 127/127 | 127/127 | 127/127 |
| CR (dynamic ladder exit: only properties checkable) | 121 | 121/121 entry price inside the 1-s high-low range within +-5 s of kin | 121/121 valid type; 121/121 no stop-level breach before kout unless stop exit; 121/121 kout>=kin | 97/121 exit price inside the +-5 s range at kout; 121/121 xpx == epx + pts (the 24 outside are ladder/time exits priced off 1-min closes; the OLD file shows the same 71% rate) |
Entry price also against the independent Databento ohlcv-1m open (PE, 460 trades): the ohlcv cache has its own back-adjust offset (7 distinct offsets), after removing the per-day offset 457/460 exact, 458/460 within 0.25 pt. Entry price of CR: epx is a level (stop/limit) so only the range test is meaningful.

## O6 (open cells) - PARTIAL, through 20261023 only
What O6 is on disk: the live-book O6 = opening-drive cells from the T-OPEN B2 harness: `TOPEN_B2_OR30m_stp_ge0.5_F60` (session NY-AM), `TOPEN_B2_LV_RN_BH_F60` (W1_0930-0945), `TOPEN_B2_OR15m_stp_le1_F60` (NY-AM), bracket F60 (60/60 pts = 240/240 ticks), basis T, flat 16:00 ET; this is how abr/thp_lib.session_streams defines the three O6 streams from out/ssa/members_q1.parquet. The cell trades originate in out/topen_b2/grp_*/<variant>.pkl (`cells[('T','F60')]['pre_trades']`, t_in = entry second), were assembled by sb1_extract/sb1_surv (UNTOUCHED guard 20260206) into out/sb1/survivors_for_A.parquet and then into members_q1.
Built: `O6_trades_redo.parquet` = the same three cells straight from the pickles without the guard (columns book, cell, session, t_ent ns, side, st, tt (ticks), t_fl, lc, lots100, bracket, scored_basis, ld, entry_et, exit_et, reason, ptsE, dur_s), session windows as sb1_surv. Rows: OR30m 764 (148 after 0206), LV_RN_BH 398 (99), OR15m 465 (90); last label day 20261023 / 20261023 / 20261022.
Tie-out: rows with ld <= 20260206 equal survivors_for_A for the cell-session exactly (616/299/375 rows, 0 differing); members_q1 (594/293/361) is a strict subset (the SSA step de-duplicates entries across cell-sessions). Independent check (weak, E unknown: E taken as SC at the entry second; 30 days, 56 trades): exit type agrees 53/56, exit second within 2 s 29/56 (22 exact) - indicative only; the post-0206 pickle trades were produced by the old harness run and were NOT re-simulated by me.
MISSING: 20261026..20261030 for O6, because the whole block-(i) chain stops at 20261023: out/open/{nq_min,levels,calendar,opentype,preopen_0929,...}.parquet (op_a_min needs the E1 tick cache + nq_off_min.parquet, op_run needs daily_levels, pquiet (ends 10-16), ES/RTY/YM x1m (cache_te2 ends 10-16)), out/topen_b2/tape0912.npz (962 days, ends 20261023) and off2.npz, out/open2b2/events_all.parquet (LV_RN_BH events). To extend: rebuild those with REDO paths (op_a_min -> op_c_x1m -> op_e_tape -> op_run, o2_tape for tape0912, o3_build for events_all), then call o2_score.simulate(EvSet(ev),'F60','T') for the three variants (f31_or.make_variant(30,'stp','ge0.5'), (15,'stp','le1'), o3_var.make_variant('LV_RN_BH')). Not done here (multi-hour, cross-asset inputs partly end 10-16); no row for the 5 days was invented. O6 is also only these 3 cells: no other O6 trade list exists on disk (DS3_THP_A_DATA.md: no D6/O6 session-cell rows are stored; those are re-bracketed variants of the 11 engines and the q-wave replays).

## Exact command lines (extend next week; cap lifts automatically with the data, env OMP/MKL/NUMBA_NUM_THREADS=1)
Prerequisites first: the extended firmlib arrays, `out/redo/te_tape_bar_redo.npz` rebuilt to the new bar count (te_core.tape() with `_TP` set; any old-length cache breaks the shapes), the ohlcv-1m NQ_2026.dbn.zst updated, delete/rename /mnt/l2/l2vast/ds3_redo_xbars/NQ.npz (it is rebuilt from the dbn files when missing).
```
cd /tmp   # (any cwd) ; python3 without -I
nice python3 l2vast/ds3/code/cap/redo_pe.py          # PE entries + base_PE   (~1 min)
nice python3 .../code/cap/redo_pb.py                                                       # PB                     (~1 min)
nice python3 .../code/cap/redo_dn_cr.py DN ; nice python3 .../code/cap/redo_dn_cr.py CR    # DN, CR                 (~1 min each)
nice python3 .../code/cap/redo_tr1.py                                                      # MV + MA (rebuilds xbars cache, ~3 min)
nice python3 .../code/cap/redo_o6.py                                                       # O6 (only as far as the harness pickles reach)
PYTHONPATH=.../code nice python3 .../code/cap/redo_check_rows.py                           # independent 30-day check
```
Outputs overwrite the *_redo files of the previous week (they are new-name files, not the old library files). Each script prints/writes the tie-out against the old files (tie_*.json); if identical_prefix is not True stop and look.

## Open issues
1. O6 stops at 20261023 (see MISSING above); the 5 last days need the block-(i) rebuild.
2. Weekly lock columns (f, net) in DN/CR rows were reproduced exactly in the prefix, so the lock engine is causal on these tables; the new rows are on the extended F with the MAPPED P9 table (map_pts falls back to the last known year x exit-type correction for 2026 exits, as the old build did).
3. MV/MA are the independent replay (x_tr1) rows, as in the THP SRC table, not the library tab (out/TR1/direct_tabs.pkl); the independent replay differs from the library on ~1% of entries (x_tr1_identity json) - unchanged behaviour.
4. NQ ohlcv-1m has one partial day (20261019) in the inventory; it is inside the MV/MA replay input.
