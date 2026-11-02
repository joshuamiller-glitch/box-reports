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

# NEW WINDOWS - s3 action per line, BASE D7 v1.2 INTERIM (the D7 v1.3 re-run follows; every table header states its base). Written 2026-11-01 ~23:50Z. Research only, Shadow, no PASS claims, everything post-hoc.
Prereg addendum `l2vast/ds3/prereg/ZONES3_S3_V12_prereg.md` sha256 b45d2a818d25d4f3feef3c103dd5d8f9e297005516e85a2a1cefa9432772b95e (DECISIONS.md, before any v1.2 statistic). Code `l2vast/ds3/code/zones3_s3/` (z3lib4 = v1.2, z3lib5 = v1.3; run_grid4/5, run_plc4, wf4, wf_engine, wf_an, robust4, report4); outputs `l2vast/ds3/out/zones3/s3_v12/` (cells_table_N.csv, report_tables.md = the full per-line x per-action table with 8 windows, placebo_ranks.csv, robust_N.csv, wf_*.csv, wf_engine_table.csv) and `s3_v13/` (v1.3 re-run). Fills: N (engine default); M/LC for finalists pending (memory-bound). Windows L1M..X' plus SEL = PRE u X'.
**Reference (v1.2, lock 12R):** F9 22.1k/wk, maxDD 127.8k; L6M 26.0k/127.8k; HOLD 22.0k/127.8k; MID 11.3k/92.1k; PRE 13.2k/113.8k; X' -5.4k/276.9k. Shipped action = HALF on the 7 non-OTE lines at D20, B73 on OTE-62 within 30 (unit O62_30). Tie-outs exact: shipped cells delta 0.0; zone-off vs HALF x2 (the `take` mechanism) 0.0; the 12R lock and U7 pass count converge (5 passes).

## 0. Plain sentence (v1.2 interim)
**On the shipped v1.2 base no single action beats the shipped HALF in every window; the one cell that cuts the maxDD in every window is reverting all 7 lines from HALF to SKIP (ALL7 skip: maxDD cut vs shipped +50 / +24 / +11 / +11 / +28 / +24 / +13 % in L1M / L3M / L6M / HOLD / MID / PRE / X', mean change +4.0k / +2.4k / -0.2k / -1.2k / -4.1k / +0.6k / +3.2k per week), but its month-block-bootstrap 90% interval of the cut is -22%..+34% (HOLD) and -20%..+41% (ALL), P(cut>0) 0.67-0.74, and dropping the single largest losing week of the shipped drawdown episode keeps the cut positive only by 2-7%: it is a LEAD with a weak sign, not a robust cut, and the same-volume placebo has only 6-8 draws so far.** The monthly-refit zone file does NOT beat the fixed layer over 2024-01..2026-10 (section 3). Cut percentages of +-10..30% appear for almost any perturbation of one line (the 12R lock and U7 make the drawdown path-dependent), which is why nothing is called a lead without the robustness block.

## 1. Ranked zone lines (v1.2 interim; cut = maxDD change vs the shipped layer, + = smaller; dmean $k/wk; labels provisional)
| rank | cell | key numbers | label |
|---|---|---|---|
| 1 | ALL7 skip (HALF -> SKIP on all 7 lines) | cut L1M +50 L3M +24 L6M +11 HOLD +11 MID +28 PRE +24 X' +13; mean -0.2k L6M, -1.2k HOLD, -4.1k MID, +0.6k PRE, +3.2k X'; boot CI HOLD -22..+34%, drop-5-weeks min +1.9% | LEAD (weak; STRICT n, TOL n, NOW n; not RISK-KEEP: cut < 20% outside L1M/MID) |
| 2 | OTE705 rb (30% rests at the line after the reclaim) | L6M +31, HOLD +31, MID +44; PRE -19, X' -6; mean +3.0k L6M, +4.4k HOLD | (L6M only), fails PRE; NOW-ONLY gate Y |
| 3 | ALL7 d3 (delay 3 min) | L6M +21, HOLD +20; PRE -122, SEL -37 | ONE-WEEK (drop of one episode week removes the cut) |
| 4 | OTE705 skip | SEL +17, X' +17, MID +53; HOLD -5, PRE -10 | mixed |
| 5 | O62_30 skip / half / take (vs shipped B73) | L6M/HOLD +16 / -16 / -4; MID +49/+49/+52; mean L6M -2.5k / -0.7k / ? ; SEL -0.5 / +7 / -3 | ONE-WEEK on MID; the B73 vs skip choice is not decided by drawdown |
The MID cut of +50% appears for ~20 different cells (a shipped-path week the lock stops at, any perturbation removes it): MID is not evidence for any single cell. Full per-line tables in `report_tables.md` (kijun1h, PDmid, bar4hmid, kc4h, camH3, OTE705, OTE79, STK7, ALL7, O62_30 x 11 actions x 8 windows with MDE, vs-skip cut, STRICT/TOL/NOW-ONLY).

## 2. Honest and post-hoc picks (v1.2 interim, per unit)
HONEST (selected on PRE+X' Calmar, PRE and X' both not worse, judged on L6M/HOLD/MID): kijun1h skip, PDmid take, bar4hmid skip, kc4h skip, camH3 d3, OTE705 half (= keep), OTE79 skip, STK7 half (= keep), ALL7 skip, O62_30 B73 (= keep); Calmar gains <= 0.01 each. POST-HOC (L6M, TOLERANT gate): bar4hmid skip, kc4h take, OTE79 skip, all other lines keep HALF / B73. Picks agree only on bar4hmid / OTE79 skip.

## 3. Purged walk-forward of the zone policy (owner: Z3; v1.2 interim; action dimension, D = 20 fresh until Z2's candidate grid exists)
Each month 2024-01..2026-10: per unit, choose the action with the best trailing 6 (and 12) month Calmar of (shipped + that cell's daily delta), 5 trading-day purge, keep shipped unless Calmar improves; apply to the month; chains are re-run as REAL engine composites (additive-delta stacking is not reliable: additive all-skip PRE cut -47% vs the engine ALL7-skip +24%).
| series (engine) | cut WF 2024-01..26-10 | cut PRE | cut MID | cut L6M | cut HOLD | cut L3M | mean change WF / L6M ($/wk) |
|---|---|---|---|---|---|---|---|
| shipped fixed v1.2 layer | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| no zone layer (ALL7 take) | -57% | -76% | +38% | -18% | -18% | -60% | +0.3k / -0.2k |
| all 7 lines skip | +11% | +24% | +28% | +11% | +11% | +24% | +0.9k / -0.2k |
| WF6 chain | -69% | -90% | +53% | +30% | +30% | +11% | -1.3k / +1.6k |
| WF12 chain | -47% | -66% | +54% | +36% | +35% | -6% | -2.4k / +1.3k |
Random-action chains (10 draws, same unit-months): WF6 / WF12 cut rank in WF 0.00 / 0.20 (worse than random), PRE 0.00 / 0.20; L6M 1.00 / 1.00, MID 1.00 / 1.00. **Verdict (v1.2 interim): the monthly-refit chain does not beat the fixed layer over 2024-2026 (maxDD 69% / 47% larger, mean lower); it looks good only on the last 6-9 months (L6M / MID), which is where its training windows overlap the evaluation regime. 247 of 306 unit-months pick an action other than the shipped one (the table flips constantly): unstable.** Labelled (L6M only).

## 4. Robustness (robust_N.csv; v1.2 interim; HOLD / ALL / PRE / MID windows)
Week carrying the shipped maxDD: HOLD / F9 = week of 2026-07-27 (127.8k), MID = 2026-03-23 (92.1k), PRE = 2024-04-22 (113.8k), ALL = 2023-08-14 (276.9k). ONE-WEEK flags: ALL7 d3 and rt (HOLD/MID), OTE705 rb (MID), O62_30 skip/half/rt (HOLD/MID), kijun1h skip, camH3 d3, OTE79 skip (ALL). Leave-one-month-out minimum cut for ALL7 skip: -2.3% (HOLD), -4.2% (ALL), -20% (PRE). Month-block bootstrap P(cut>0): ALL7 skip 0.67-0.74, OTE705 rb HOLD 0.95 (but PRE 0.10), O62_30 take MID 0.96.
Not yet done: definition sensitivity (D +-25/50%, freshness, line parameter variants; Z2 grid), vol terciles, 1-s/3-s decision delay, shuffled-day and full same-volume placebos at >= 60 draws, M/LC fills, equal-risk runs. Per book x session cubes are stored in each grid pickle (`cube` 6 x 6 x ND).

# s3 action per line - BASE D7 v1.3 (re-run of the full 101-cell N grid, written 2026-11-02 00:10Z). Research only, Shadow, no PASS claims, post-hoc.
Base v1.3 (d7_v13.run_v13, lock 12R, U7, gated take lines U6/P6; ASSUMED profit reading): L6M 21.3k/wk, maxDD 94.1k; PRE 2.9k/175.1k; MID 19.7k/43.1k (lead's figures; shipped cells tie delta 0.0 in my grid). Outputs `out/zones3/s3_v13/` (cells_table_N.csv, wf_*, robust_N.csv, assign.json), code z3lib5/run_grid5/wf5/wf_engine5/wf_an5/robust5/rank5. Prereg addendum as above (same cells, new base). Placebo draws on v1.3 for 10 finalist cells (40 draws, N fills) are running; M/LC fills and the Z2 grid input are pending.
**Plain sentence (v1.3):** on the v1.3 base the v1.2 lead disappears: reverting all 7 lines from HALF to SKIP now cuts the maxDD +7.5 / +61 / +17.5 / +15 / +5 % in L1M / L3M / L6M / HOLD / MID but ADDS 2.8% in PRE and 19% in X' (mean +3.1k to +14.8k/wk in L1M/L3M/L6M, -7.3k in MID, +5.6k PRE), its HOLD cut is ONE-WEEK (drop the 2026-08-17 week and it is -3.4%), the month-block bootstrap P(cut>0) is 0.40 (HOLD) and 0.62 (ALL), and the monthly-refit chains do not beat the fixed layer. No action on any line is RISK-KEEP; the honest (PRE+X'-selected) pick for every one of the 7 lines and for ALL7 is to keep HALF, and for OTE-62 to keep B73. The signal moved with the base between v1.2 and v1.3 (ALL7 skip L6M +11% -> +17.5%, PRE +24% -> -2.8%), which is the sign that these maxDD cuts are path noise of the lock and not line information.
| rank | cell (v1.3) | key numbers | label |
|---|---|---|---|
| 1 | ALL7 skip | cut L3M +61, L6M +17.5, HOLD +15, MID +5, PRE -3, X' -19; mean L3M +14.8k, L6M +5.7k, MID -7.3k | (L6M/L3M only), ONE-WEEK on HOLD; NOW-ONLY gate Y, STRICT n, TOL n |
| 2 | ALL7 rt (line -2 ticks) | cut L3M +60, L6M +20, HOLD +20; MID -28, PRE -19, X' -17; mean L6M +12.3k | (L6M only), FRAGILE (signs flip across windows) |
| 3 | OTE705 skip | cut L3M +6, L6M +3, HOLD +3, PRE +1, SEL +9; X' -3, MID 0; mean L6M +8.8k | TOLERANT gate Y (the only cell passing STRICT-ish TOL), cut < 10%, ONE-WEEK on ALL: small, not a drawdown lead |
| 4 | OTE705 rb | cut L3M +46, L6M +19; PRE -17, X' -11, SEL -24 | (L6M only) |
| 5 | O62_30 half / skip (vs shipped B73) | half: L6M +17, HOLD +17, MID 0, PRE -16; skip: L6M +19, MID -1.5, PRE -10, X' -22 | (L6M only); B73 stays |
OTE-62 B73 D30 vs alternatives on the nine months: replacing B73 by half or skip trades a +17-19% L6M cut for PRE -10..-16% and X' -16..-22%; the mean difference is +4.0k (half) / +4.4k (skip) in L6M but not in MID (0): the B73 choice is not decided by drawdown on either base; the v1.2 'B73 loses mean in F9' result does not carry over cleanly to v1.3.
## Walk-forward (v1.3; engine chains; 10 random-action chains)
| series | cut WF 24-01..26-10 | PRE | MID | L6M | HOLD | L3M | mean change WF ($/wk) |
|---|---|---|---|---|---|---|---|
| no zone layer (ALL7 take) | -26% | -26% | -32% | -18% | -18% | +15% | +2.5k |
| all 7 skip | -3% | -3% | +5% | +17.5% | +15% | +61% | +3.5k |
| WF6 chain | -27% | -27% | -1% | +16% | +16% | -6% | -1.0k |
| WF12 chain | -35% | -35% | -23% | -18% | -18% | -55% | -0.8k |
**Verdict (v1.3): the monthly-refit zone file does NOT beat the fixed shipped layer** (WF6 / WF12 maxDD 27% / 35% larger over 2024-01..2026-10 and lower mean; only the 6-month chain matches it on L6M/HOLD, +16%, rank 1.00 vs random chains but one window); 283 of 306 unit-months differ from shipped (the fit flips every month). Random action chains are worse still (mean cut -60%), so the chain beats random but not the fixed layer. D/freshness are not refit yet (Z2's candidate grid file not available).
## Robustness (v1.3, robust_N.csv)
Weeks carrying the shipped maxDD: HOLD/L6M 2026-08-17 (94.1k), MID 2026-03-23 (43.1k), PRE and ALL 2025-02-24 (175.1k / 265.3k). ALL7 skip HOLD ONE-WEEK; OTE705 skip ALL ONE-WEEK; O62_30 skip/half/rt/take MID cuts are 0..-36% (no cut). Bootstrap 90% intervals of the cut contain zero for every finalist except OTE705 rb HOLD (-0.2..-8%: negative end only). Still pending: definition sensitivity D +-25/50%, freshness/line-parameter variants, vol terciles, 1-s/3-s delay on acting variants, shuffled-day placebo, M/LC fills, equal-risk runs, per-book x session tables for the finalists (cubes stored).
Correction to the v1.3 robustness paragraph: for OTE705 rb HOLD the month-block bootstrap 90% interval of the cut is -8.4%..+21.7% (P(cut>0) 0.83), leave-one-month-out minimum -0.2%, drop-5-weeks minimum +1.9%: positive in HOLD but it is -17% in PRE and -24% in SEL, so it stays (L6M only). All other finalist intervals contain zero.
