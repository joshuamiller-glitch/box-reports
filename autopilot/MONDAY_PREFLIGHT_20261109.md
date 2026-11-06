# MONDAY_PREFLIGHT_20261109 - dry/test run of the Monday 13:00Z table and the 14:00Z WATCH register (BASE-4, 2026-11-06T04:10Z)
Research-side only. Nothing traded, bought or changed in a rule. No file under data/live/ was opened (checked statically and by an open() audit hook, section 4). Inputs read: MONDAY_RUNBOOK.md, FEED_RUNBOOK_20261107.md, DST_AUDIT_20261105.md, check_monday_preflight.sh, monday_all.py/.sh, runners.json, watch_all.py/.sh/registry/plugins. Scratch (synthetic register + tape, never the real forward_register): /mnt/l2/l2vast/ds3_base4/preflight/FR/. Audit logs: /mnt/l2/l2vast/ds3_base4/preflight/audit/.
Not run (blocked by the permission system, correctly): `pull_nov.py` dry run (it calls Databento's price-quote service). Everything below is offline.

## 0. Bottom line
- Monday 13:00Z `monday_all.sh` will fire (alive, next fire 2026-11-09T13:00:00Z) and the dry run of the whole table returns rc 0 on all seven jobs in 4 s. WATCH register `watch_all.sh` is alive (pid 674892); its dry run returns rc 0.
- Without the Saturday NQ ohlcv-1s pull, Monday's table shows: every timing row (NY-AM, fade, SHADOW-2, sleeve) "no data yet" / n0 / $0 / EARLY, the BT flip row "log not found / nothing to read", all six LM rows NO DATA. Before today's fix the table did not say WHY (a logged signal with no tape was counted as n0 $0 silently, test below); it now opens with a FEED / TAPE row "NO TAPE ... n0 means NO OUTCOME DATA, not no trades".
- With the pull (tape.csv built by `hm_feed.py --tape-out`), the same runners score the signals the box logged from 2026-11-04 on (synthetic test: fade signal scored, header `sec,open,high,low,close,vol` accepted by preflight and runner).
- 3 fixes of mine done (PF-1 tape row, PF-2 week label, PF-3 tape->ohlcv1s converter for the NQ_PDL watch). Items for the lead: section 6.

## 1. DST / UTC offsets - PASS
| check | result |
|--|--|
| ET = UTC-5 since 2026-11-01 02:00 ET (zoneinfo) | PASS: 2026-10-30 09:30 ET = 13:30Z (EDT); 2026-11-02 and 2026-11-09 09:30 ET = 14:30Z; 16:55 ET flat = 21:55Z |
| Monday 13:00Z = 08:00 EST, WATCH 14:00Z = 09:00 EST | PASS (both loops are UTC wall-clock schedules, no ET dependence; DST audit item 8) |
| Forward floor 2026-11-01T23:00Z = Sunday 18:00 EST = epoch 1793574000 | PASS in `hm_feed.FLOOR_S` (1793574000, was 22:00Z; fixed after DST-1 finding 3), `pull_nov.FLOOR` (23:00Z), `parse_d6_output_log.FLOOR_MS`, `fills_join`, `watch_core.FLOOR_TS` |
| DST-1 findings 2 and 7 (BT loader UTC date; double milliseconds) | PASS: `bt_forward_check.load` now uses the ET label day (wall clock + 6 h) and label-day weeks; `parse_d6_output_log` line 76 patched. Finding 1 (`jb_prep` hours=4) no longer present |
| DST-1 finding 5 / question 4.1 (HM VWAP reset clock fixed UTC-4 vs ET midnight) | OPEN, platform-owner question, no effect on the Monday table; decided by `hm_anchor_replay.py` once the platform's HM fills for 11-02..11-06 are available (that tool takes the user-supplied trade file as an argument; it is NOT part of Monday's runners and is run only on the lead's go) |

## 2. Inputs - which are still missing
| input | state | effect on Monday |
|--|--|--|
| `forward_register/tape.csv` (hm_feed --tape-out) | MISSING (no weekly file pulled; MANIFEST has no ohlcv-1s line; `data_fwd/` empty) | NY-AM, fade, SHADOW-2 rows cannot score anything after 2026-10-30; shown as "no data yet"/n0 plus the new NO TAPE row |
| Saturday pull NQ.v.0 ohlcv-1s 2026-11-01T23:00Z..2026-11-07T00:00Z (about $1.14, cap $2.00) | NOT DONE, needs the user's explicit OK (FEED_RUNBOOK_20261107.md; at or after 08:00Z Saturday) | as above |
| `forward_register/ohlcv1s/NQ_*.npz` (read by the NQ_PDL watch) | MISSING and nothing in the runbook produces it | NQ_PDL stays NO-DATA ("waiting for the weekly NQ ohlcv-1s pull"). Fix PF-3: `standing/tape_to_ohlcv1s.py` converts tape.csv to that file (tested on the synthetic tape: plugin coverage and run() accept it); add it as step 2b after `hm_feed.py --tape-out` |
| `forward_register/shadow2/` directory | ABSENT (preflight MISSING) | SHADOW-2 rows read "no signals logged since the start" (rc 0). Created by the box's writer, not by research code |
| bt/nyam/fade/sizer_shadow register dirs | exist, 0 signal files | "no data yet" |
| D7 logs `forward_register/live/{fills,signals,d6_stops,th_cuts,control_pnl}.csv` (directory absent) | MISSING (known) | LM 1-6 all NO DATA (0 metrics with data), rc 0 |
| NQ 1-min table through 2026-11-05 (`/mnt/l2/l2vast/tables/NQ/1min`) | present (ZL-2 pull, to 11-05 16:05Z) | MONDAY_LONG reads it: ACCUMULATING N=0 (week 1 = Mon 11-09, first read Tuesday 11-10, needs a later table) |
| RTY / CL / MBT / GC tables | RTY ends 10-30, CL ends 10-16, MBT ends 10-31 23:43Z, GC spec absent | RTY_PREMARKET, CL_DONCHIAN, MBT_ASIA_KELTNER = NO-DATA; GC_REGIME = SPEC-PENDING (owner ZL-1). Correct statuses, not errors |
| SPEND.json | `spent_usd` 7,311.63 of 8,000 now (runbook said 7,226.94; someone added items) | confirm the LEAN $61.315 item is included before the pull (lead) |

## 3. Preflight and dry-run results (PASS/FAIL per check)
| check | result |
|--|--|
| `check_monday_preflight.sh` | runs, exit 7 = the 7 known MISSING items (shadow2 dir, tape.csv, five live/*.csv). Loops alive (monday_all.sh, thp_daily.sh, ledger_monthly.sh), next fire 2026-11-09T13:00:00Z, MORNING.md writable, detail pages writable, standing code syntax ok |
| tape header check | PASS: header `sec,open,high,low,close,vol` is accepted (the "known false alarm" in the feed runbook is already fixed in the script, `.bak_pre_hdr`) - runbook text outdated |
| `monday_all.py --dry --force` | PASS rc 0 for BT, NY-AM, top-3, sizer, NYAM-monthly, SHADOW-2, LM; writes nothing (dry) |
| same with synthetic register + tape | PASS: fade VB2NYAM_T3 signal scored (n1 -$454); without the tape the same signal gives "week 0 n0 $0" (silent drop, now flagged by the FEED / TAPE row) |
| tests `test_g23.py`, `shadow2/test_g1.py`, `shadow2/test_oc_latch.py`, `shadow2_weekly --selftest` | all PASS |
| md5 of standing code vs DECISIONS.md | `monday_all.py` and `tape_to_ohlcv1s.py` logged after my edit. WARN fade_books.py, shadow2_books.py, sizer_forward_weekly.py, bt_forward_weekly.py changed after their last logged md5 (files dated 11-02..11-04, not edited by me today); I logged their observed md5s in DECISIONS.md (they pass syntax and tests) |
| `/tmp` 96% full | WARN: root fs 19 GB free, /tmp is 17 GB (not mine: ic_ev_full.pkl, sf_ev_*.pkl, pb2_ev_*). monday_all writes its scratch lines in /tmp and `/tmp/monday_all.lock`; a full root fs would break the run. Lead: ask owners to delete the large /tmp pickles (or move to /mnt/l2) before Monday |
| week label | FIXED (PF-2): block heading said "week 2" on Mon 11-09 (days//7+1) while the runners label the same signals "week 1"; now the count of completed weeks, 1 on 11-09 |
| default `--start 2026-11-04` | NOTE: the Monday runners ignore signals logged before 2026-11-04 (box start). Intended per runbook; the tape and the feed cover 11-02. If the box also logged 11-02/11-03 signals, set `MONDAY_START` (env) - lead to confirm |

## 4. Register plugins and files read (no data/live)
WATCH dry run (rc 0, 0.9 s): RTY_PREMARKET NO-DATA (last RTY table second 10-30 21:00Z); MONDAY_LONG ACCUMULATING N=0 of 26 (data to 11-05 16:05Z); CL_DONCHIAN NO-DATA (CL cache ends 10-16); MBT_ASIA_KELTNER NO-DATA (ends 10-31 23:43Z); GC_REGIME SPEC-PENDING; NQ_PDL NO-DATA (no forward file). Spec sha256 guards all match the registry (no REFUSED row).
Plugins load without error; fee/cost asserted at import: rty_premarket FEE 4.84 and TV>0, monday_long COST_PTS>0 and MNQ_PV 2.0, cl_donchian SLIP, FEE_SIDE, PV > 0, btcm_keltner FEE_PTS 17.8 and PTV 5.0, nq_pdl FEE_NQ 4.84, FEE_MNQ 1.28 and COST_PTS > 2 ticks. All five import in a `-I` interpreter; constants are hard-coded, none from the environment (T2_FEEPTS trap closed).
Files read, by runner (open() audit hook per runner, plus static grep; `P` = O/l2vast/ds3/code/zones3, FR = O/forward_register, O = <repo>/outputs; pyarrow/parquet opens are not visible to the hook, so for those the static grep is the evidence):
- BT flip: FR/bt/bt_flip_shadow.csv (or FR/bt_flip_shadow.csv); writes BT_FORWARD_WEEKLY.md and the MORNING block.
- NY-AM fades: FR/nyam/*_signals.csv, `--tape FR/tape.csv` (only if present), O/l2vast/ds3/out/cap/CAP.json, /mnt/l2/l2vast/ds3_g2_redo/{SS,SH,SL,SC}.npy (stored 1-s path, ends 2026-10-30).
- fade bundle: FR/fade/*_signals.csv (+ _fills.csv), tape, O/l2vast/struct48/out/setA_daily.parquet, /mnt/l2/l2vast/ds3_base4/{fade_shadow_verify.pkl, fs_stack.pkl}.
- sizer: FR/sizer_shadow/, /mnt/l2/l2vast/ds3_base4/{sp_research.npz, sp_verify.pkl}.
- NYAM monthly: FR/nyam/nyam_daily.csv, /mnt/l2/l2vast/ds3_zones3_new/discover_cache/stack_q1a_ts2.npz, out/def/NQ.parquet via the bar library.
- SHADOW-2 + sleeve: FR/shadow2/*_signals.csv, *_daycomplete.csv sidecars, tape, /mnt/l2/l2vast/ds3_zl1_s2/verify_all.pkl.
- LM: FR/live/*.csv (absent), tape, standing/live_monitor_baselines.json, /mnt/l2/l2vast/{ds3_q4/q4_series_px.npz, ds3_sizer/feat_signal.parquet, ds3_zones3_new/discover_cache/stack_q1a_ts2.npz, ds3_zones3_new/sizer_cache/rows.pkl}.
- monday_all: runners.json, state file autopilot/monday_all_state.json, /tmp scratch lines, appends MORNING.md.
- WATCH: watch_registry.json, autopilot/WATCH_*_SPEC.md, plugins, instr2_sessions.json, /mnt/l2/l2vast/find_c/cache_c/CL.npz, /mnt/l2/l2vast/ds3_instr/MBT_1m.npz, /mnt/l2/l2vast/tables/{RTY/1s, NQ/1min}, /mnt/l2/l2vast/instr_1s/NQ_S{S,O,H,L,C}.npy and FR/ohlcv1s/NQ_*.npz (NQ_PDL), find_c/cache_c/NQ.npz.
Result: NO runner reads data/live/, StratTrades_*, K4Trades_* or nt8log* (grep over zones3, discover, fade, d7base, sizer_s3, watch, shadow, hmfwd: 0 hits; audit logs: 0 hits). `forward_register/live/` is the platform-log drop folder of D7_LOGGING_REQUEST.md, a different folder from data/live/, and is currently absent. The runbook does not authorise any data/live read for Monday. Sealed blind-week files untouched.

## 5. Fix list
| id | item | owner | status |
|--|--|--|--|
| PF-1 | silent n0 $0 when logged signals have no tape | BASE-4 | DONE: FEED / TAPE row at the top of the Monday table (NO TAPE banner / tape last second) |
| PF-2 | block heading "week 2" on the first Monday vs runners' "week 1" | BASE-4 | DONE |
| PF-3 | nothing builds the NQ_PDL forward file `forward_register/ohlcv1s/NQ_*.npz` | BASE-4 (tool) | DONE: `standing/tape_to_ohlcv1s.py`; add to FEED_RUNBOOK after `--tape-out`: `python3 -I l2vast/ds3/code/zones3/standing/tape_to_ohlcv1s.py` |
| PF-4 | MONDAY_RUNBOOK / FEED_RUNBOOK text: header false alarm is fixed; "today MISSING" list | BASE-4 | note here (runbook pages left as written; this page supersedes) |
| PF-5 | `/tmp` 96% (root fs 19 GB free) | lead / owners of /tmp/*_ev_*.pkl | OPEN |
| PF-6 | SPEND.json: confirm LEAN $61.315 included before the pull; balance now 8,000 - 7,311.63 = 688.37 | lead | OPEN |
| PF-7 | Saturday pull needs the user's OK (step 2 of FEED_RUNBOOK); ready: window 2026-11-01T23:00Z..11-07T00:00Z, at or after 08:00Z | user via lead | OPEN |
| PF-8 | `forward_register/shadow2/` and `live/` dirs absent (created by the box writer / D7 logging) | box owner | OPEN, expected |
| PF-9 | `MONDAY_START` default 2026-11-04 vs feed from 11-02 | lead to confirm | OPEN |
| PF-10 | GC_REGIME spec missing (ZL-1); RTY/CL/MBT tables stop before the floors | ZL-1 / data owners | OPEN, statuses are correct as is |
| PF-11 | Free alternative to the pull for NQ prices only (lead decision, NOT done): the L2 1-s table `tables/NQ/1s/2026-11__ext_20261101_20261105.parquet` holds trade prices (trd_px_hi/lo/last) for 11-01 23:00Z..11-05 16:05Z, but it is the NQ blind-span data (sealed blind-week object) and the feed runbook forbids pointing scorers at both the feed and the L2 tables for the same weeks | lead | NOT used |
