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

# NEW CAP interim 17:3xZ (T-RECENT-REDO; cap 2026-10-31; windows L1M|L2M|L3M|L6M|HOLD|MID|PRE|X'; plus SEL = PRE u X', F9 = 2026-02-07..10-31, OLD CAP L6M kept as L6M_old). Workers killed on the ledger-priority order. No PASS claims.
## Built / tie-out
- code/zones3_s3/z3lib3.py = z3lib2 + redo_boot.install() + windows.py (OUT = out/zones3/s3_redo/). Composite on the redo engine ties REDO-2: F9 23.9k/wk, maxDD 247.7k; L6M 27.4k/247.7k; HOLD 29.1k/247.7k; MID 13.8k/148.1k; PRE 241.2k, X' 120.5k; old L6M 41.1k/22.9k; diff vs plain composite 0.0. Zone skip rows 12,174 (was 9,642).
- Scripts with _r suffix are the new-cap copies (run_grid_r, run_plc_r (env J0, CELLS for finalists), run_er_r, run_comp_r, rank_r, final_r, forf_r), an3r.py (windows), extra_r.py (LOEO, per book x session; untested).
- Housekeeping: the first run_grid_r launch imported the OLD z3lib and rewrote the identical old-cap grid_*.pkl in out/zones3/s3 (deterministic, same inputs); logged in DECISIONS.md.
## Scored (new cap)
- Grid 330 cells (11 units x 10 actions x N/M/LC) done: out/zones3/s3_redo/grid_*.pkl, cells_table_{M,N,LC}.csv (all windows), forfeited.csv, assign.json (rank_r.py), calendar.npz.
- Placebo (random-level same-count, M, 40 draws x 90 cells): STOPPED at ~220 of 1,200 jobs per worker (partial plc_{0,1,2}_0.pkl, no ranks). Equal-risk, null, LOEO, composite, per book x session, >=200 draws on finalists: NOT run.
## First look (M, vs R0 = shipped all-skip; cut > 0 = smaller maxDD)
- L6M and F9 maxDD are the same episode (Oct 2026 week); un-skipping ALL lines changes it by -0.4% (F9) and raises mean +0.3k (F9) / +2.0k (L6M): the 8-line skip does nothing for drawdown on the nine new months (agrees with REDO-2), while on PRE+X' it still helps (ALL take SEL cut -24%).
- Honest per-line pick (selected on PRE+X'): unchanged PDmid rt, bar4hmid half, OTE79 wt (Calmar gains <= 0.003). Post-hoc pick (L6M, TOLERANT): OTE62 take / O62_30 take (drop the line; L6M mean +2.1k, cut +0.2%).
- Largest F9 cuts: OTE705 d5 +13.8%, d1 +11.3%, take +9.3%, d3 +8.7%, rb +8.5%, b73 +8.3% (mean +0.9k to +1.7k F9) but all negative on PRE+X' mean (-1.9k to -2.4k): recency-specific, not a rule.
- OTE-62 B73 D30 (O62_30 b73): F9 cut -0.8%, mean -1.5k F9 (+0.2k L6M, +1.0k SEL); MID mean -5.2k and cut -11%. The mean-vs-drawdown trade does not hold on the nine months: B73 loses mean in F9.
## Resume
cd l2vast/ds3/code/zones3_s3: `J0=0 python3 -I run_plc_r.py <sh> 3 40` (restart; partial files are keyed plc_<sh>_<J0>.pkl), run_er_r.py, run_comp_r.py, final_r.py, then finalists with CELLS=u:a,... J0=40 ND=200. Windows labels for tables from an3r.WALL.
