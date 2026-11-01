# REDO-1B bars (2026-11-01): tick-bar library and bar store through label day 20261030, de-duplicated tape only

Research only. Originals untouched. All code is new: `l2vast/ds3/code/cap/redo_{e1_cache,barlib_build,barlib_assemble,vol_tieout,store_build,store_tieout,bpm}.py`; the old builders (`barlib/bl_core.py`, `bars/bars_build.py`, `bars_io.py`, `e1_ticks.labday`) are imported unchanged, inputs re-pointed by monkeypatch (`redo_store_build.py`).

## What was built
| item | path | content |
|---|---|---|
| new E1 tick cache + tl_* sidecars | /mnt/l2/l2vast/ds3_redo/cache/ (14 GB) | 361,080,074 front-contract ticks, 48 tape files of `NQ_dropin_redo` (months 2023-02..2026-10 + 3 ext weeks), 45 label-day-month chunks. Offsets to the library 1-min basis from `ds3_g2_redo/{MIN,c}.npy` |
| tick-bar library | out/bars_redo/<44 types>.parquet (-> /mnt/l2/l2vast/ds3_redo/bars_redo, 4.2 GB) | 150,000,440 rows (old 148,767,832), label days 20230201..20261030; schema/dtypes as the stored files |
| full library rebuild (scratch) | /mnt/l2/l2vast/ds3_redo/barlib_full/ | all 44 types from the new cache (assembled files equal it exactly: `final_equals_full_rebuild` True for 44/44) |
| bar store | out/bars_store_redo/<type>/<size>/YYYYMM.parquet (+ `_meta_YYYYMM.parquet`), 164 series x 43 months (202304..202610) = 7,052 symlinks, 0 dangling | clean old months -> original `out/bars_store` files; the 11 defective old months and 202603..202610 -> rebuilt files in /mnt/l2/l2vast/ds3_redo/bars_store_full/ (23 GB; ALL 43 months were rebuilt there) |

Assembly rule of the library: stored rows for non-defective old label days <= 20260206; rebuilt rows for the 11 old defective days (20230403, 20230703, 20231002, 20240603, 20240902, 20241202, 20250203, 20250303, 20250602, 20251103, 20260202) and every label day >= 20260209.

## Tie-out (tick library; out/bars_redo/_tieout_old_clean_days.csv, _tieout_post_cap_days.csv, _rowcounts.csv)
| test | result |
|---|---|
| cache vs old cache, 45 chunks | 32 chunks bit-identical in all 10 arrays; the 13 differing chunks are exactly the 13 defective files (2023-04,07,10; 2024-06,09,12; 2025-02,03,06,11; 2026-02,03,08) plus 2026-10 (ext 1024-1030 added) |
| rebuilt vs stored rows, NON-defective old label days <= 20260206 (769 days) | **0 mismatching rows, 0 days with differences, in all 44 types** (e.g. time_1m 1,052,949 rows, tick_500 566,806, dollar_10M, time_1s ...) |
| stored (<= 20261023) vs rebuilt for label days 20260209..20261023 | identical on all days except 20260302 and 20260803 (the two post-cap defective files: all 44 types differ, as intended) and 20261023 (+1 row = the end-of-day partial bar, emitted on the next session's first tick which the old cache did not have; 18 of 44 types, the others drop/lack partials) |
| the 11 old defective days | rebuilt; row counts e.g. dollar_10M 229,983 -> 224,521; time bars keep their count and change only v (per-bar volume halves in the doubled hour) |
| volume (out/bars_redo/_vol_tieout.csv) | per label day sum(time_1m v) = de-duplicated tape volume = L2 1-min table trd_vol: **ratio 1.0000, exactly equal on 970 of 970 trading days** (190 new days 20260209..20261030, 11 old defective days, all old); sums ratio 1.0 (6 holiday days have no data) |

## Tie-out (bar store; out/bars_store_redo_tieout.csv)
* Clean old months (24 months x 164 series = 3,936 files) rebuilt from the dropin_redo tape: **3,936 of 3,936 bit-identical** to the stored `out/bars_store` files (table equality, all columns). So the builder, the h2root 1-s day files, the ds3_g2_redo arrays and the lifted caps reproduce the stored store exactly.
* Defective old months (11 x 164): rebuilt vs TAPE-2 `bars_store_t2` and vs TAPE-1 `bars_store_dedup`: **1,640 of 1,640 bit-identical for the 10 months 2023-04..2025-11** (all columns). 202602: my file holds the whole month (days to 20260227, cap lifted), t2/t1 stop at 20260206 (length differs in all 164, by design); restricted to day <= 20260206 my 202602 equals t2 in **164 of 164 series bit for bit** (8,114,384 rows). Versus the ORIGINAL store, 1,745 of 1,804 files change (59 do not, e.g. day-restart series with no row in the first hours).
* New months 202603..202610 (190 label days, all 164 series): tc/1m day volume vs library time_1m 0.9973..1.0000 (final partial minute dropped, same as the old store; 60 days below 1.0). `vol_ok` False on 6 roll days (20260317/18, 20260616/17, 20260915/16): on the first roll day the tape holds only the OLD contract (e.g. 20260317: tape/L2 1-min = 77,381 vs library 1-s 354,897), so the cumulative-volume placement falls back to the tape second (flagged `vol_ok`), as for the earlier roll days; prices fine.
* Post-cap 1-s day files carry `inst = 0`: the library contract is resolved from the tape window (one instr, or on roll windows the one whose volume equals the day's library 1-s volume, else the largest). For days <= 20260206 the stored inst is used.

## bpm decision (DS3_TAPE_DEDUP 6.3)
bpm = n_bars / n_1m_bars sets g = round(minutes x bpm). Rebuilt data, SAME window (<= 20260206): bpm moves 0.05% median-ish (mean |0.047|%, max 0.17%), **0 flips** in 164 store series / 44 library types (`_bpm_store.csv`, `_bpm_lib.csv`). Over the full window to 20261030 the bpm moves up to +30% (the market in Feb-Oct 2026 prints more per minute: 86 of 164 store series and 31 of 44 library types would change g). **Decision: keep bpm FROZEN at the old-window value (data <= 20260206, original files)**, so G variants keep their definition and old/new windows stay comparable; the tables carry both values, scorers may switch with a logged decision.

## Missing / notes
* Nothing missing for NQ through 20261030. Library label days 20230201..20261030; the store starts 202304 (FIRST_LD 20230403) as before.
* The 2026-11 month (starts Sun 2026-11-01) must be de-duplicated before use (CAP.json `next_defective_file`).
* Aux/other month-keyed readers must also read `tables/NQ/<tbl>/2026-10__ext_*.parquet`; this build does (tape, 1-s table).
* 4 new `RuntimeWarning` casts in linreg/hull (NaN->int8) are pre-existing behaviour.

## How to rebuild / extend next week
```
cd /tmp   # 1 worker, OMP/MKL/NUMBA threads 1
C=l2vast/ds3/code/cap
# 0. de-duplicate the new weekly ext tape into a NEW NQ_dropin_redo2 dir (tape_dedup_redo.py); point TAPE_DIR constants (TAPE in redo_e1_cache.py, TD in redo_store_build.py) at it
python3 $C/redo_e1_cache.py                                  # new E1 cache + sidecars (3 min)  [edit output dir C to a new directory first]
python3 $C/redo_barlib_build.py /mnt/l2/l2vast/ds3_redo/barlib_full2    # 44 types, ~4 min
python3 $C/redo_barlib_assemble.py                           # edit NEW/OUT dirs; writes tie-out csvs (~10 min)
python3 $C/redo_store_build.py 202611                        # month(s); REDO_STORE_OUT=<dir> to change output; ~40 s per month
python3 $C/redo_store_tieout.py                              # tie-out csv + symlink view (re-run is idempotent)
python3 $C/redo_vol_tieout.py; python3 $C/redo_bpm.py
```
Logs: /mnt/l2/l2vast/ds3_redo/logs/. Runtime for the whole job: cache 3 min, library 4 min + 10 min assemble, store 43 months about 25 min, tie-out 3 min.
