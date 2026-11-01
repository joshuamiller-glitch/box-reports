# REDO-1T3a THP + L2 features (2026-11-01, done 16:57Z)
Cap 20261031 (last trading day 20261030). All new trees are NEW dirs; old months are symlinks (<202602); 202602 and later rebuilt whole-month.

## Artifacts
- out/thp_redo/trade_index.parquet : 59 columns x 69,660 trades (final); trade_index_base33.parquet = 33-col base; coverage_dp1s_by_{book,sess_entry,year,win}.csv, table_size.json, thp_cov.log.
- /mnt/l2/l2vast/ds3_thp_redo/data/{dp1s,dp10s,dp1m,ldp1s,ldp10s,ldp1m}/book=B/year=Y/m=YYYYMM.parquet ; aux/tstats/YYYY-MM.parquet ; aux/{aux_bar.npz,l2_base_rate,l2_depth_base,l2_mod_depth8_base}.parquet
- /mnt/l2/l2vast/ds3_l2feat_redo/{dp10s,ldp10s,dp1m,ldp1m,t2_*,t3_*,t4_*,vpin_*}/book=B/m=YYYYMM.parquet (202304..202610), gates/YYYY-MM.parquet (2023-02..2026-10), t4_cols.json (copy of old)
- code: code/cap/thp_redo/ (thp_build win map +POST=3; thp_cov day_labels -> out/redo/dv2a), code/cap/l2feat_redo_{rt,build,gates,t2,t3,t4,add_vpin,at}.py (rt = reads main + __ext_ part files; tape reads use out/tape_dedup copies).

## Tie-out
| item | result |
|---|---|
| thp_build 202601 rebuilt in scratch vs old | 11,662,053 rows, 0 differing columns; tstats equal |
| thp_build 202602 old tids vs old | 2,006,531 rows, 0 diffs; tstats equal |
| trade_index 59 cols, 47,131 old tids vs out/thp | 58 non-key columns, 0 differing (tid set old subset of new, unique) |
| l2_depth_base / l2_mod_depth8_base old rows | 0 differing |
| gates 2026-02 rows <= old max ts | all 54 columns bit-identical |
| dp10s/ldp10s/dp1m/ldp1m/t2/vpin 202602 old tids (ST,KB,PE,CR sampled) | 0 differing columns |
| t3 (dp1m/ldp1m) 202602 old tids | 20-25 of 40 columns differ on ~9% rows, all 2026-02-01 23:28 .. 02-02 13:55: caused by the tape_dedup of NQ 2026-02 (12,511 duplicated head rows); new = deduped, intended |
| t4 202602 old tids | 24-39 of 324 columns differ: inherited from t3 dedup |
Row counts dp10s/ldp10s l2feat == thp_redo 1:1 (4,017,510 / 3,720,328 rows, 202602..202610).

## Open issues
- vix_prev NaN on 837 new trades (vix source not extended past some date; check day_labels).
- 20 trades n_dec NaN (dur_s=0), as before.
- t4 baseline for old months unchanged (prior-months-only), new months use the extended sample set.

## Next-week command lines (cd outputs/l2vast/ds3/code/cap/thp_redo; OMP/MKL/NUMBA threads=1; nice)
python3 thp_index.py ; thp_aux.py ; thp_l2pre.py ; thp_dayreg.py (as REDO-1) ; python3 thp_build.py YYYY-MM ... ; cp trade_index.parquet trade_index_base33.parquet ; python3 thp_cov.py
cd code/cap: python3 l2feat_redo_build.py prepass ; l2feat_redo_gates.py YYYY-MM ... ; l2feat_redo_build.py dp10s,dp1m YYYYMM ... ; l2feat_redo_t2.py dp1m YYYYMM ; l2feat_redo_add_vpin.py dp10s,dp1m YYYYMM ; l2feat_redo_t3.py YYYYMM ; l2feat_redo_t4.py base ; l2feat_redo_t4.py apply YYYYMM
Timing: whole thp_build month ~3-10 min; dp10s month ~1 min/book-mode group; parallel months OK (<=3 GB RSS each).
