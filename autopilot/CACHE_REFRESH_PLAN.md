# CACHE_REFRESH_PLAN - engine and standing-program caches: inventory and the refresh procedure 2026-10-31 -> now (DIS-BI, CAL, 2026-11-05)
Plan only: no cache was rebuilt, no file edited, nothing bought. Inventory = (a) a runtime trace of every file the engine (`sizer_harness` -> `d7_v13t/d7_v13y/de_engine`, the same base `ledger_monthly.py` re-reads) and each Monday runner opens (Python audit hook on `--selftest` runs; traces in `/mnt/l2/l2vast/ds3_base4/cache_plan/`), (b) last dates read from the files, (c) builders and procedures from `DS3_DATA_REDO*.md`, `RUNBOOK_WEEKLY_EXTENSION.md`, `HM_FORWARD_FEED.md`, `code/cap/`. Statements marked (unverified) were not run.

## 0. Verdict
1. **Every engine cache is current to label day 2026-10-30, the last day of owned NQ/ES/RTY data** (REDO-1, 2026-11-01). Nothing is stale *below* that date except the four caches in section 3 (class A), which end 2026-10-16 although data to 10-30 is on disk; they can be refreshed now at $0.
2. **No owned data exists for label days from 2026-11-02 on.** The only ways to get it are the two approved weekly buys: the **L2 mbp-10 extension** (NQ+ES+RTY, about $36-38/week, runbook step 15, approved with a $700 L2-extension cap; $105.6 spent on 3 weeks, last week bought is 202644 = 10-24..10-30) and the **NQ ohlcv-1s feed** ($1.15/week, from Sat 2026-11-07). Neither is scheduled; both are manual and need the Databento key. Remaining budget: $8,000 cap - $7,288.26 = **$711.74** (SPEND.json itself still shows $7,226.94: the $61.315 LEAN purchase is only in DECISIONS.md and the receipt).
3. **The ohlcv-1s feed alone cannot keep the engine at full fidelity.** It refreshes the price-only caches (1-s path, 1-min bars, `nq_min`, `minute.parquet`, `nsec`, time-chart bar stores, Shadow2 books). It cannot refresh anything built from trades or the L2 book: the tick-bar library (44 types), the L2 feature tables (dp10s, ldp10s, gates), `l2set_redo` (the TH-L2 cut inputs, 23.6 M rows), `BL/BS/ja/jb`, the L2SE entry-veto features and the DIS-E refill-failure count. Those need the weekly mbp-10 extension (or D7 logging, see D7_LOGGING_REQUEST.md, which logs the cut inputs only for the live trades).
4. **The December ledger refit (2026-12-01 02:00Z) will repeat the same data**: it "does NOT refresh market data or engine caches" and the day axis is hard-coded to 2026-10-30 (section 4). It will run fine, but its answer sentence cannot change unless the caches are rebuilt first.
5. Two correctness hazards for any rebuild after 10-30: US DST ended 2026-11-01 (hard-coded UTC-4 offsets in `jb_prep.py`, `jb_worker.py` and `hm4` columns, runbook DST warning) and the Dec-2026 contract roll (~2026-12-15, Mar-2027 contracts).

## 1. Owned data by instrument and date (DS3_DATA_REDO.md section C, LEAN receipt, traces)
| data | NQ | ES | RTY | YM | 9 LEAN symbols (6E 6J BTC CL GC MBT NKD ZB ZN) | other 17 outrights |
|--|--|--|--|--|--|--|
| mbp-10 raw (L2), tape de-dup, L2 tables (1min/1s/100ms/sweeps/vpin/events) | 2026-10-30 | 2026-10-30 | 2026-10-30 | no | no | no |
| 1-min bars | 10-30 (series_NQ.npz, ohlcv1m) | 10-30 | 10-30 (5 partial days) | 10-16 | top-up bought to 10-30 (BTC/MBT 10-31); series files end 10-13/10-16 until merged | 10-16 |
| 1-s | path 10-30 (`ds3_g2_redo`); `instr_1s` 10-16 | `instr_1s` 10-16 | `instr_1s` 10-16 | - | NKD, 6J ohlcv-1s to 10-30 (LEAN) | - |
| trades | derived from mbp-10 to 10-30 | same | same | no | NKD trades to 10-30 | no |
| label days 2026-11-02 onward | none yet | none | none | none | none | none |
First forward data: the HM feed starts at the forward floor 2026-11-01T22:00Z; the weekly L2 extension for week 202645 would start 2026-10-31T00:00Z.

## 2. Engine caches (traced from `Harness().run()`, `rows()`, `features()`, `BookHarness()`; the redo path map `code/cap/engine_redo/redo_boot.py` redirects every old path to the `*_redo` file)
| cache (path under outputs/l2vast/ds3 unless absolute) | last date | builder | refresh (today) | who |
|--|--|--|--|--|
| `/mnt/l2/l2vast/ds3_g2_redo/{SS,SH,SL,SC}.npy` + 9 arrays + 4 event lists (1-s path) | 2026-10-30 20:59 | `cap/redo_g2_dump.py` (+ `redo_*` path builders) | append from the extended tape; old prefix must stay bit-identical | REDO-1 workers, manual |
| `/mnt/l2/l2vast/ds3_l2set_redo/glob/{BL,BS,ja,jb}.npy` | 10-30 | `cap/engine_redo/redo_ls_glob.py` | needs L2 | REDO-1T3b |
| `out/bars_redo/time_1m.parquet` + 43 more types (tick-bar library) | ld 20261030 | `cap/redo_e1_cache.py`, `redo_barlib_build.py`, `redo_barlib_assemble.py` | needs trades (tick cache 361 M ticks, 14 GB `ds3_redo/cache`) | REDO-1B |
| `out/bars_store_redo/tc/*/YYYYMM.parquet` (164 series; the engine reads tc/45s to 202602 and older months by fallback) | 202610 (day 20261030) | `cap/redo_store_build.py`, `redo_store_tieout.py`, `redo_bpm.py` | time-chart series OK from 1-s; trade-based series need ticks | REDO-1B |
| `out/redo/rows/*_redo.parquet` (ST HM KB SM WT PB7 PE PB DN CR MV MA rows), `out/redo/rows/pb7_rows_redo.parquet` | 20261030 | `cap/redo_rows_*.py`, `redo_pe.py`, `redo_pb.py`, `redo_dn_cr.py`, `redo_tr1.py` | rerun on the extended F (firmlib arrays) | REDO-1T1/T2 |
| `out/thp_redo/trade_index.parquet` (69,660 trades, 59 cols), `out/thp_redo/wf/c3/cache/` | 20261030 | `cap/thp_redo/*`, `cap/engine_redo/redo_c3_path.py` | needs rows + path (+ L2 columns) | REDO-1T3 |
| `out/dipentry_redo/trades_arm.parquet`, `out/trendgate_redo/store/{universe,chart_5m}.parquet`, `out/eint1dd_redo/masks.pkl`, `out/confirm_redo/bars/15m.npz`, `out/poi_store_redo/` (8 streams, features.npy, index.csv) | 20261030 | `engine_redo/redo_trades_arm.py`, `redo_universe_er.py`, `redo_masks.py`, `redo_gen_poi.py`, `redo_poi_feats.py` | price-based, rerun after bars | REDO-1T3b |
| `out/l2set_redo/{entry/lgb_pred.npy, joint/streams.pkl, loss/rows.parquet, loss/tidx_cut.parquet}` | 10-30 | `engine_redo/redo_l2s_rows.py`, `redo_ls_build.py` | **needs L2 (TH-L2 cut inputs)** | REDO-1T3b |
| `/mnt/l2/l2vast/ds3_thp_redo/aux/aux_bar.npz` (34 cols), `out/redo/dv2a/day_labels.parquet` | 10-30 (VIX NaN after 10-16) | `cap/redo_aux.py`, `redo_day_labels.py` | aux needs volume (mbp-10 or ohlcv); VIX needs a free CBOE CSV | REDO-1 |
| `out/cap/CAP.json`, `cap/windows.py` (CAP 20261031), `redo_boot.py` constants `CUT_LD=20261031`, `CUT_S=1793394000`, `END='2026-10-30'` | - | hand-edited | **must be bumped before any engine run past 10-30** | REDO-1 |
| `/mnt/l2/l2vast/ds3_base4/ts2_flags.npz` (A06/B02 slot flags), `/mnt/l2/l2vast/ds3_sizer/feat_signal.parquet` (88,490 rows), `/mnt/l2/l2vast/ds3_zones3_new/sizer_cache/rows.pkl` + `ts2_*_live_p*.npy` (engine run caches) | 20261030 | `d7base/build_sizer_feats*.py`, `zones3/sizer/sizer_harness.py` | rerun after the rows above (row count grows, `kin` alignment is asserted) | ZL-2 / BASE-4 |
| `/mnt/l2/l2vast/ds3_zones3_new/discover_cache/stack_q1a_ts2.npz` (core, cube, days), `book_harness` caches | 20261030 | `BookHarness.stack()` | rerun `h.run(None)` after the engine caches (15 s) | ZL-2 / CAL |
| `out/redo/engine/d7_base_literal_redo.npz` (tie-out of the D7 base) | 20261030 | `engine_redo/run_d7_redo.py` | regenerate for the new tie-out | REDO-1T3b |

## 3. Standing-program caches (what the Monday runners, the monitor, the ledger and the loops read)
| program | cache read | last date | builder | note / class |
|--|--|--|--|--|
| nyam_regime_monthly (first Monday of the month) | `out/def/NQ.parquet` (1-min, ET index, raw frame) | **2026-10-16** | not found in code (built 10-26 by the autopilot 1-min merge: `data/autopilot/ohlcv1m` + `ap_ext_ohlcv.py` pattern) | **class A**: ohlcv1m has NQ/ES/RTY to 10-30; its monthly read says "as of 20261016"; YM stays at 10-16 (no data) |
| same, plus Q4 / DISCOVER studies | `out/def/{ES,RTY,YM}.parquet` | 10-16 | same | class A (YM none) |
| fade_forward_weekly, shadow2_weekly default path (`fade_engine.path_nq()`) and fade selftest | `/mnt/l2/l2vast/instr_1s/NQ_S{S,H,L,C,O,V}.npy` (also ES, RTY, CL ...) | **2026-10-16 20:59** (46.09 M s) | `INSTR_ENGINE.md` / `fade_engine` `I1.load` (builder not located) | class A for NQ/ES/RTY (extend from `ds3_g2_redo` and L2 1-s tables to 10-30). **Correction to SHADOW_READINESS.md: the default history-only path ends 10-16, not 10-30**; BASE-4's `--tape` fix is therefore essential |
| Shadow2 books, verify | `/mnt/l2/l2vast/fade_lv/nq_min.npz`, `ds3_fade/minute.parquet`, `ds3_dise/dise_minute.parquet`, `ds3_zl1_s2/nsec_0.npy` | 10-30 | `fade_lv` / `ds3_fade` builders (not located), `ds3_dise` RF from L2 tables | class B for price columns, **C for DIS-E RF** |
| Shadow2 research lists | `ds3_disb/events.parquet`, `q13/events.parquet`, `ds3_zones3_new/Z2_disk/dk_events.pkl`, `ds3_dc/weekends.pkl` | 10-30 | per-line libs (`disb_lib`, `q13_lib`, `dk_events`, `dc_sunday`) | regenerate only for the research comparison |
| nyam_forward_weekly / regime | `out/nyam_corrected_daily.pkl`, `out/famD_bars.npz`, `stack_q1a_ts2.npz` | 10-30 | `zones3/nyam/corrected_study.py`, `famD` | class B |
| sizer_forward_weekly | `ds3_base4/sp_research.npz` (88,490 rows), `sp_verify.pkl`, `forward_register/sizer_shadow/seed/{rv_seed,rank_seed}.csv` (rv to 10-29), bars_redo / bars_store_redo | 10-30 | `zones3/sizer_shadow/make_seed.py` | seeds are extended by the live log itself |
| bt_forward_weekly | `ds3_zones3_new/zl1/{base_rows_ynone.pkl, feats_bt.npz}` | 10-30 (feats_bt keys not dated) | `zones3/zl1` | needs rows + L2 columns (unverified which) |
| fade_loop (fade_consolidate), fade_cond | `out/fade_cond_tables.parquet`, `struct48/out/setA_daily.parquet` | setA **10-16** | `fade_cond.py`, struct48 | setA class A/B |
| live_monitor | `live_monitor_baselines.json` (built 11-04), `stack_q1a_ts2.npz`, `q4_series_px.npz`, `out/def/{NQ,ES}.parquet`, `feat_signal.parquet`, `rows.pkl` | 10-16 / 10-30 | `live_monitor.py --build` | rerun `--build` after class A so R4-R7 baselines include 10-19..10-30 |
| exit_loop / thp_daily | family pages `DS3_EXIT_N_*.md`, `THP_POLICY_D7_N.txt` | pages | `zones3_s5/exit_integrator.py` | reads pages, not market data |
| ledger_monthly | engine caches of section 2 via `d7base/lvq.py` | 10-30 | - | see section 5 |
| ds3_lead, snapshot loops, box-reports sync | none (pages only) | - | - | no market-data cache |

## 4. Refresh procedure 2026-10-31 -> now
Order matters: A (now, $0) -> B (after the first weekly buy) -> C (needs L2). Each step must show `old_part_identical true` / zero mismatches on the existing days before it is accepted (the REDO tie-out rule); keep `_bak` copies (cp -p) and log in DECISIONS.md.
**Phase A: close the gaps below owned data (no new data, $0, about 1-2 h each, unverified durations)**
1. `out/def/{NQ,ES,RTY}.parquet`: append 2026-10-17..10-30 from `data/autopilot/ohlcv1m/<SYM>_2026` (merge dedup, back-adjust at instrument-id changes as the existing builder does); YM, and every outright without data, stay at 10-16. Verify the first 1,697,227 NQ rows unchanged.
2. `instr_1s/{NQ,ES,RTY}_S*`: extend to 10-30 from the 1-s L2 tables / `ds3_g2_redo`; NQ first-open/volume arrays (`SO`, `SV`) from `tables/NQ/1s`. Check against `ds3_g2_redo` on overlap.
3. Complete the partial O6 trades (3 T-OPEN cells, "partial to 20261023") with `redo_o6.py` on `ds3_g2_redo` (path now reaches 10-30); fill `day_labels` VIX/other free series (CBOE `*_History.csv`, CFTC COT zips, runbook step 7, free but outside "owned data": mark as new free data).
4. Rebuild the derived price-only caches that point at the stale files: `struct48 setA_daily`, `live_monitor --build`, `nyam_regime_monthly` will then read through 10-30.
**Phase B: the weekly NQ ohlcv-1s feed ($1.15/week, Sat 2026-11-07 06:00Z or later, manual, guarded)**
5. `pull_nov.py` dry run -> user-confirmed `--execute --confirm` -> `data_fwd/` + `MANIFEST.jsonl` -> `hm_feed.py --verify` -> `--tape-out forward_register/tape.csv` (G2/G3 fixed by BASE-4).
6. Append to the 1-s path (`ds3_g2_redo` arrays) and 1-min caches (`aux_bar` OHLC columns, `nq_min.npz`, `ds3_fade/minute.parquet`, `nsec_0.npy`, `famD_bars.npz`) from the feed: ONE contract per trade date, `sec = ts_end/1e9 - 1`, DST now UTC-5 (see 8). Price-only Shadow lines (Q13, DIS-K, DIS-B, DIS-C) and the NY-AM fades read these.
**Phase C: full-fidelity engine refresh (needs the weekly mbp-10 extension, runbook step 15 and ADDENDUM 2026-10-26)**
7. Each Saturday after 06:00Z: quote (<= $40), log `L2EXT_<START>-<END>` in SPEND.json BEFORE submitting, submit NQ/ES/RTY day-split jobs, download, `l2v_ext_reduce.py <SYM> <dir> <YYYY-MM>__ext_<start>_<end>`, `l2v_ext_verify.py`, derive trades/ohlcv-1m (`autopilot/ext_1019/ext_week_derive.py`), then `ap_ext_build.py`, `b10_tickdbn2.py`, `ap_ext_h2.py`, edit `ins_env.py` LAST/FULL_END/CEND, rows (`ap_ext_er_gen.py`), `ap_ext_drv`, `ap_ext_icache`, forward chain. First missing week = 202645 (START 2026-10-31T00:00Z, END 2026-11-07T00:00Z), then one per Saturday.
8. Before running it past 10-30: **DST**: replace the hard-coded `hours=4` / UTC-4 offsets (`jb_prep.py`, `jb_worker.py` `utc_ns`, `hm4` columns) with a tz-aware ET conversion; keep results for 2026-03-08..11-01 identical (EDT).
9. Re-run the REDO builders append-only on the new weeks (`cap/tape_dedup_redo.py` -> `redo_g2_dump.py` -> `redo_e1_cache.py`/`redo_barlib_*` -> `redo_store_build.py` -> `redo_rows_*` -> `thp_redo` -> `engine_redo/redo_*`), after bumping `redo_boot.py` (`CUT_LD`, `CUT_S`, `END`), `CAP.json`, `windows.py` CAP and the `de_engine` day axis; then `redo_tieout.py` and `run_d7_redo.py` (19 stored checks must still tie to 0.0000 $/day on the old days).
10. Rerun `sizer_harness`: `rows.pkl`, `feat_signal.parquet` and `sp_research.npz` get new rows (88,490 now); the `kin` alignment assertion in `features()` will fail until all three agree; then `stack_q1a_ts2.npz`, `live_monitor --build`, `ledger_monthly.py --force` (or wait for 12-01).
11. Dec-2026 roll (~2026-12-15): confirm the unique instrument ids in the new files are NQ 261401 / ES 10252 / RTY 42012034 until the roll, then the Mar-2027 ids (`ext_week_derive.py` IID); S54-style second-contract roll windows are a separate buy (about $6.7 NQ / $5.5 ES per window).

## 5. Which steps need new data, and the cost
| steps | new data? | cost | unlocks |
|--|--|--|--|
| 1-4 (class A) | no (VIX/COT free public CSVs optional) | $0 | monthly regime read through 10-30, runners' default path to 10-30, baselines |
| 5-6 (ohlcv-1s feed) | yes, NQ only | $1.15/week | 1-s path, 1-min bars and the price-only Shadow lines and fades from 11-02 on |
| 7-11 (mbp-10 extension) | yes, NQ+ES+RTY | about $36-38/week (cap $40, L2 total cap $700; remaining overall budget $711.74, about 18 weeks) | the whole engine, TH-L2/L2SE inputs, tick-bar library, DIS-E RF, ES/RTY rows; the December refit becoming informative |
Alternative to buying L2 for the engine: D7 logging of `th_cuts.csv` / `signals.csv` gives live cut inputs only, not the research feature tables.

## 6. December ledger refit and decisions
- `ledger_monthly.py` (12-01 02:00Z, needs >= 15 GB MemAvailable, 3 shards, writes under `/mnt/l2/l2vast/ds3_base4/lvs_q`) will run on the 10-30 base and produce an unchanged answer sentence; to make it informative, Phase C must be finished first (about 4-5 weekly buys by 12-01 if started 11-07: weeks 202645-202648).
- **Decisions for the user:** (1) continue the weekly mbp-10 extension (about $38/week) past week 202644 or stop at the price-only feed; (2) approve class A merges from owned files now; (3) whether to extend ES/RTY at all (ES/RTY are 30% of the L2 bill and feed only ES/RTY replication work); (4) the DST fix and the cap constants are code edits to the REDO/engine files; the owner (REDO-1/BASE-4) should make them.
