## REDO-1T3b lock-engine inputs (2026-11-01) - D7 engine + one-convention engine run to label day 20261030

Result: `D.run()` of BASE-1's D7 engine on the redo inputs returns the cube (11 books x 6 sessions x 935 label days, 20230403..20261030), 15 s per run. New files only; no old file edited or overwritten.

### Load the redo files in an engine
```python
import sys; sys.path.insert(0,'l2vast/ds3/code/cap/engine_redo')
import redo_boot; redo_boot.install()          # FIRST, before any engine import (env REDO_OFF=1 = old engine, 745 days)
sys.path.insert(0,'l2vast/ds3/code/d7base'); import d7lib as D   # D.run(...) as in out/d7base/README.md; oc_lib/ss2_lib/dd_lib are the same modules (oneconv runs through D.TIE)
```
redo_boot = (1) a path map redirecting every open/np.load/np.memmap/pd.read_parquet/read_csv/exists of an OLD input to its redo file (writes to old paths raise), (2) lifted literal caps (ls_data/de_common CUT, de_engine day axis 2023-04-03..2026-10-30, erdef.load5). Stats windows inside d7lib/dd_lib keep the OLD definitions; apply cap/windows.py to the daily series for the new windows. Scripts: `run_d7_redo.py <out.npz> [json cfg]`, `redo_tieout.py`, `redo_monthly_counts.py`. All in `l2vast/ds3/code/cap/engine_redo/`. Cube saved: `out/redo/engine/d7_base_literal_redo.npz`.

### Inputs (old -> redo), tie-out of the old part
| input | redo file | builder (engine_redo/) | tie-out |
|---|---|---|---|
| dipentry/trades_arm | out/dipentry_redo/trades_arm.parquet (69,660 rows, 66,133 sim_ok) | redo_trades_arm.py (+ redo_raw_events.py -> out/redo/engine/raw_events_redo.npz) | 47,131 old rows identical in all 63 columns except opp_s of 33 old rows (real extension: a later opposite signal now exists); raw events: 5 books prefix identical |
| trendgate universe + chart_5m (ER) | out/trendgate_redo/store/ (66,133 rows, 124 cols) | redo_universe_er.py | 44,370 old rows identical in all 124 columns; 6 order-flow columns (bar_delta_*, cvd_*) NaN for new rows (flow_1m not extended) |
| EF-2 masks | out/eint1dd_redo/masks.pkl (+feat_min.parquet) | redo_masks.py | 921,015 action cells on old d rows, 0 mismatches; sig_slope/sig_st1_dist_atr formula vs stored max diff 3.7e-7; assignment C keeps the 20260206 frozen cut |
| l2set bits/glob | /mnt/l2/l2vast/ds3_l2set_redo/{bits,glob} (month + weekly ext parts concatenated) | redo_ls_build.py, redo_ls_glob.py | 34 arrays identical on the old 36,558,644 prefix; new length 46,674,871; lgb_pred_redo = old + NaN (LGB gate not used by D7) |
| l2set loss rows / tidx_cut | out/l2set_redo/loss/{rows,tidx_cut}.parquet (rows 19,976,110 + 3,592,092) | redo_l2s_rows.py (needs ds3_l2feat_redo/ldp10s, ds3_thp_redo data) | old 19,976,110 rows identical in every column incl. z-scores |
| joint/streams.pkl | out/l2set_redo/joint/streams.pkl = copy of old | - | not used in the D7 path (comp 'E' only); loss/profit streams NOT extended |
| c3 path cache | out/thp_redo/wf/c3/cache/{tidx,path_off,path_px} (66,156 trades) | redo_c3_path.py (px from ds3_g2_redo SC, verified = THP dp1s px) | 395,151,175 old samples identical |
| POI store (SET8 only) | out/poi_store_redo/ (8 streams, features (8,66133,8), index.csv) | redo_gen_poi.py, redo_poi_feats.py | features of 44,370 old trades x 8 streams: 0 mismatches; streams: old rows identical, end/cap differ only for the last POI (old-cap truncation), one extra boundary POI in MAS ich_kijun 1h. rsim/ and the other 681 streams NOT built (D7 does not read them) |
| confirm bars | out/confirm_redo/bars/{15m,1h,4h,1d,1w,...}.npz | via redo_gen_poi.py (cf_engine.build_bars) | old bars identical |
| X1-X5 trades | out/tape_rescore_redo/d7_orig_<cell>_trades.parquet | redo_x_cells.py (bars_store_t3b view of bars_store_redo) | identical except the 11 defective first-days (below) |
| tc/45s, time_1m, SS/SH/SL/SC, pb7 rows | REDO-1B bars_store_redo / bars_redo, ds3_g2_redo, out/redo/rows/pb7_rows_redo | (other agents) | used as delivered |

### Engine tie-out (redo run, first 745 days vs stored)
* 19 checks of d7base/tieout.py (COMP6 lock off/12/20/30, 12R m0 0.5, slip 0.45, ON set x5, ON+ER, join, EF-2 HM/KB/PE, AS-IS, AS-IS+L2SL U1, U3): max abs diff 0.0000 $/day each (out/redo/engine/tieout_redo.log, tieout_redo.json).
* Full D7 base (th_loss + th_profit on) vs out/d7base/series/base_literal.npz: six core books K6 P6 U6 H6 M6 A6 and X1, X2: max abs diff 0.0 $/day in every session. X3 pre / X4 london / X5 london differ on 6 cells, all on the label days whose ORIGINAL tape had the stray Sunday hour (20240902, 20250203, 20250303, 20251103, 20250203): max 3050 $/day (X3 pre 20250203/20251103). Expected: the bar store for those 11 months is now rebuilt from the de-duplicated tape (redo uses it by directive); not a bug. All other 6 x 11 x 745 cells are < 0.004.
* New 190 days: all finite, no (book, session) all-zero on the new days, 38 new weeks none zero (weekly $ min -85,629, max +177,132, mean 17,645; total +670,521). Per-month signals/trades per book: `out/redo/engine/d7_monthly_counts_redo.csv` (txt pivot of trades beside it); no book has a zero-trade month after 202602 (e.g. 202610: A6 57, H6 73, K6 184, M6 129, P6 177, U6 36, X1-X5 22/18/21/44/27).

### Not extended / caveats
LGB prediction array (NaN beyond old cap, unused); 6 order-flow chart_5m columns; joint/streams.pkl; poi rsim and 681 non-SET8 streams; rel_tot8 base (NaN beyond old cap, unused by D7). Assignment 'C' of the EF-2 masks stays the old-cap frozen cut. D7 stats windows inside d7lib remain old definitions.

### Extend next week (one worker)
```
cd l2vast/ds3/code/cap/engine_redo
# after trade_index_redo, ds3_g2_redo, bars_redo, bars_store_redo, ds3_l2feat_redo/ldp10s are extended (raise CUT_S 1793394000 / CUT_LD / END in redo_boot.py, redo_ls_build.py CUT_NS, redo_ls_glob.py CUT_S, redo_l2s_rows.py NOLD (=current tidx length))
nice python3 redo_raw_events.py; nice python3 redo_trades_arm.py; nice python3 redo_universe_er.py
nice python3 redo_ls_build.py 2026-11 ; nice python3 redo_ls_glob.py          # month files + weekly ext parts are concatenated automatically
nice python3 redo_c3_path.py; nice python3 redo_gen_poi.py && nice python3 redo_poi_feats.py
nice python3 redo_l2s_rows.py; nice python3 redo_masks.py; nice python3 redo_x_cells.py
nice python3 redo_tieout.py; nice python3 run_d7_redo.py ../../../out/redo/engine/d7_base_literal_redo.npz '{}'
```
(the tie-out scripts compare against the OLD stored files; for a second extension compare against the previous redo outputs instead.)
