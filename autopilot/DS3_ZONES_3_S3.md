# DS3_ZONES_3_S3 - OLD CAP interim (checkpoint, T-RECENT-REDO; data cap 20260206; NOT final, no PASS claims, Shadow only)
Written on the Lead's stop order. Everything below is scored to the OLD CAP (2026-02-06) on the interim one-convention composite (not out/d7base). Re-run on the new cap (L1M|L2M|L3M|L6M|HOLD|MID|PRE|X') when REDO-1 and BASE-1 announce.

## Built
- Prereg l2vast/ds3/prereg/ZONES3_S3_prereg.md (copy autopilot/ZONES3_S3_prereg.md), sha256 31d875fcdb53fea4ec516dcaa54127c14f718ba24bdf8830f82d11260d7f36f6, in DECISIONS.md before scoring (its log stamp 15:42Z is wrong, true wall ~15:09Z; correction line appended).
- Code l2vast/ds3/code/zones3_s3/: z3k.py (B73/WT/RB 1-s kernels), z3lib.py + z3lib2.py (units, build_from, hooks into ss2_lib compose/build_rows, run_cell; z3lib2 is current), tie.py/tie2.py, run_grid.py, run_plc.py, run_er.py (not run), run_comp.py (not run), rank.py, forf.py, final.py (not run), an3.py.
- Units (exclusive ownership of R0's 9,642 skip rows): 8 lines, STK (>=2 lines), O62_30, ALL. Actions: skip(R0), take, half, rt (line-2 ticks), b73, wt, rb (30% rests at the line after trade-through; 1-tick retest; 60% haircut in LC), delay 1/3/5 min. PE-confirm and PB rows keep the shipped skip for entry-changing actions.
- Tie-outs exact: rows == int_split on the 8 engine books; shipped composite daily diff 0.0 (L6M maxDD 22.9k, HOLD 97.0k, PRE 241.2k, N basis); no-change replaced rows delta 0.0; B73/WT kernels == poi_sim net diff 0.0.

## Scored (old cap)
- Grid: 11 units x 10 actions x 3 bases (N shipped / M measured / LC = M + stop 2.45 + rb haircut) = 330 cells, done: out/zones3/s3/grid_{0,1,2}.pkl, cells_table_{M,N,LC}.csv (all windows incl. SEL = PRE u X'), forfeited.csv, calendar.npz, assign.json, dead_lookup_full.txt (NOT FOUND x6). Paths under l2vast/ds3/.
- Placebos: STOPPED at ~400 of 1,500 jobs per worker (partial plc_{0,1,2}.pkl, no ranks). Equal-risk, best-of-N null, leave-one-episode-out, composite runs, per book x session: NOT run.

## First look (M basis, vs R0 = shipped all-skip; cut > 0 = smaller maxDD; unranked, no placebo yet)
- No action beats skip on L6M maxDD for ALL lines: half -42%, rt -44%, wt -64%, b73 -97%, take -108% (SEL: half +5.8%, others -17% to -31%).
- Honest per-line pick (SEL Calmar, PRE and X' cut >= 0): PDmid rt, bar4hmid half, OTE79 wt (Calmar gains <= 0.003, noise); other lines stay skip. Post-hoc pick (L6M, TOLERANT): OTE62 wt (L6M Calmar +0.026, HOLD/SEL cut negative).
- OTE-62 'not always skip': OTE62/O62_30 with b73, half, d1-d5 raise weekly mean ~+0.8k to +1.5k (L6M) at a maxDD cost (L6M -5% to -31%); O62_30 b73 (D7 v1.0d) L6M cut -5.3%, mean +1.5k. A mean-vs-drawdown trade, not a drawdown win. Nothing RISK-KEEP.

## Resume
cd l2vast/ds3/code/zones3_s3: run_grid.py <shard> 3; run_plc.py <shard> 3 50; run_er.py; rank.py; run_comp.py; forf.py; final.py. New engine: re-point dd_lib import in z3lib2.py, rerun forf.py (writes calendar.npz).
