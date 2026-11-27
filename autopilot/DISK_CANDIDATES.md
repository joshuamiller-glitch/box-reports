# DISK CANDIDATES for /mnt/l2 on box1 (W-DISK, written 2026-11-27 ~04:35Z; READ-ONLY survey, nothing moved/deleted/written under /mnt/l2)

Headline: /mnt/l2 = 3.5 TB, 35 GB free (100%). Fill ~30 GB/day (290 GB free on 11-19 19:45Z per DISK_TREES_INVENTORY.md -> 35 GB now) = ~1.2 days to a hard stop. Other servers have huge free space (VERIFIED df): C 67.213.127.157 27 TB free (5% used), D 72.46.85.15 28 TB free, A 207.188.7.103 26 TB free, B 206.223.224.21 5.6 TB free, fra 109.94.96.39 5.7 TB free. Root fs on box1 is also tight (43 GB free, 90%), so nothing can be moved "back" to root.

Recoverable (apparent GB, not read for >=7 days by atime): LOW risk ~94 GB, MEDIUM ~1,140 GB (copy-first, replicated or low-reference), HIGH ~1,140 GB (raw purchased data / symlink targets). Biggest single, cleanest win by risk/size: raw NQ/ES/RTY mbp-10 months, 680 GB, unread 7 d, copy to C then free (needs Josh's order; HIGH because it is bought data with no second copy).

## How read (VERIFIED vs READING)
- VERIFIED: sizes (du -sx per dir, find -printf apparent bytes, GB = 1e9 unless "G" from du), file counts, mtime min/max, remote presence and counts (ssh ls/du/find, read-only), C cold_archive hash-verified copies (from COLD_ARCHIVE_LOG.md, sha256 equal), open files (scan of /proc/*/fd and cwd at ~04:10Z), running command lines.
- READING / UNRELIABLE: atime. Mount is ext4 `relatime` (atime moves at most once per 24 h on read, and any hashing/backup scan resets it: e.g. cold_copy reads on 11-19..11-23 set atime on shuf/ds3_l2h/ds3_redo_d8). "Not read 7 d" below = no file atime in last 7 d; treat as a hint, not proof. NQ_mbo shows atime < 2 d on ~all files but no process had them open: some scan or batch read them; reader unknown.
- READING: "code refs" = substring grep of <repo>/{code,outputs/code} (*.py/*.sh, no .bak) for "/<dirname>". Paths built dynamically (ds3_%s etc.) are missed; old research code under outputs/l2vast/ds3/code was NOT rescanned (see DISK_TREES_INVENTORY.md: tables 230, ds3_v2tree 30, ds3_redo 15 refs there). Inbound symlinks exist for tables (262), ds3_v2tree (40), ds3_redo (6,500), ds3_thp (2,279): moving them dangles those links (DISK_TREES_INBOUND_SYMLINKS.txt).
- Replica check = same dir name on other server with same file count and same GB (NOT hash-verified) unless noted.
- Raw data per directory sums: l2vast 2.92 TB (586 dirs) + rootmoves 267 + rootmoved 57 + moved_from_root 21 + snapshots 6 + pylib 1 GB.

## 1. Table: biggest trees (GB apparent | files | mtime oldest..newest | not-read-7d GB | code refs all/recent(>=11-20)/running | copy elsewhere)
| GB | path | what it is | mtime | not read 7 d (GB) | refs all/recent/running | copy elsewhere |
|---|---|---|---|---|---|---|
| 948 | l2vast/raw | Databento raw: NQ mbp-10 months 2023-02..2026-10 (NQ/GLBX-20261013.. 309 GB + back/ 17 + ext/ 19), ES mbp-10 (177 GB), RTY (83), NQ_mbo daily MBO (259; Y2023..Y2025 + L3M + TAIL), NQ_opts 10, NQ_blind 4, NQ_mbp10_extra 12 | 10-19..11-26 | 680 (NQ/ES/RTY mbp-10 all unread; NQ_mbo read < 2 d) | raw/NQ 26 files, NQ_mbo 20, ES 3, RTY 2 / ps 0 | NONE (no raw/ or *.dbn.zst of mbp-10 on C, D, B, fra; A only has small _newdata/asia) |
| 268 | rootmoves (4 dirs) | outputs_b8_cache 137, outputs_a5_post_cache 44, data_autopilot 38 (opts, opt0dte), data_databento 31 (old B10/CL/ES/GC/NQ/RTY/ZN trades, mbp10) | 10-13..10-31 | 267 | symlink targets: box1 data/databento (92 code files), data/autopilot (55), outputs/b8/cache, outputs/a5/post/cache | none |
| 259 | l2vast/_th_state | state base: s345 212 (exact_b/_mat 196 GB, 194 M_* matrices from 11-19), s2 17, profit 12, base 11 | 11-08..11-27 | 256 | 273 / 1 / 1 running | partial: other servers hold 7 GB of _th_state (A 6.4 G has exact_b/_mat dir) NOT the 196 GB |
| 240 | l2vast/_th_tp | MONTH CACHES (cache/ = 88 monthly dirs, 223 GB) + CAPS.txt + .bak_* | 11-11..11-27 | 3 (HOT: 2,040 open fds) | 41 / 6 / 0 | YES on all 5 servers (C, D, A, B, fra: 223G, 6116 files each) |
| 201 | l2vast/tables | NQ 95 / ES 64 / RTY 33 / NQ_back / ES_back: bar/tape/event tables by month | 10-19..11-06 | 190 | 17 / 13 / 0 (+262 inbound symlinks) | none |
| 136 | l2vast/ds3_v2tree | v2 tree (aux, hilo, malayer, derived) | 11-06 | 136 | 0 / 0 / 0 (30 refs old research code, 40 inbound symlinks) | none |
| 109 | l2vast/_grid | grid arrays: res 102 (results), tape 6, logs | 11-17..11-27 | 4 (HOT: 4,608 open fds in tape) | 91 / 11 / 1 | partial (A 1,870 G, B 213, fra 165 hold more grid res; C 6 G, D 1 G) |
| 91.5 | l2vast/_replica2 | T-REPLICA-2 cut-input convention search (cache, labels, live_frozen) | 11-07 | 91.5 | 1 / 0 / 0 (code/mbo_book/mk_trades.py) | none |
| 80.5 | l2vast/_bars | bar/feature stores: book 19, feat_d 16, feat_c 16, book_asia 3 | 11-17..11-27 | 1.5 (HOT: 972 open fds feat_d) | 99 / 13 / 0 | YES (C 52 G, A 49 G, B and fra 55 G, counts 41-54 k; slightly different counts) |
| 57 | rootmoved | outputs/autopilot b, i, ddmin and n5 moved off root on 11-18 (MANIFEST.txt) | 10-16..11-27 | 53 | 1 / 0 / 0 (via symlinks outputs/autopilot/{b,i,ddmin}, outputs/n5) | none |
| 47.5 | l2vast/ds3_redo | ds3 redo stores (barlib_full, bars_store_full, cache) | 11-01 | 47.5 | 0 / 0 / 0 (6,500 inbound symlinks) | none |
| 46.6 | l2vast/_hist_replica | historical replica coverage/cuts (coverage.csv.bak__* files) | 11-07..11-27 | 38.9 | 38 / 1 / 0 | YES on all 5 (35 G, 982 files) |
| 45.4 | l2vast/_confl | T-CONFLUENCE outputs (altbars, c4, cf2) | 11-14..11-27 | 45.4 | 265 / 0 / 0 | partial (A has 6 G) |
| 45.3 | l2vast/ds3 | ds3 caches/code/out/discover_data | 10-26..11-06 | 44.6 | 76 / 2 / 39 (substring hits ds3_*) | none |
| 43.6 | l2vast/_mbo_book | MBO book convention table, d1, full_ev_seq | 11-08 | 43.6 | 7 / 0 / 0 | none |
| 40.1 | l2vast/ds3_thp | thp data (data/ open by 10 procs) | 10-29..11-01 | 15.2 | 1 / 0 / 30 running | PARTIAL on C cold_archive (24 G, 1,935 of 2,390 files) |
| 35.0 | l2vast/_th_exh | T-TH-EXHAUST cells, ledgers | 11-09..11-27 | 34.6 | 97 / 0 / 0 | none |
| 29.7 | l2vast/_th_redo_replica | TH redo replica cells | 11-07..11-08 | 29.7 | 44 / 0 / 0 | none |
| 27.8 | l2vast/ds3_redo_d8 | D8 redo | 11-01 | 27.8 | 0 / 0 / 0 | YES hash-verified C cold_archive (554 files, 11-23 log) |
| 27.4 | l2vast/ds3_zones3_new | zones discovery cache + logs | 11-01..11-27 | 26.9 | 1 / 0 / 0 | none |
| 24.8 | l2vast/ds3_l2h | l2h arrays | 10-29 | 24.8 | 0 / 0 / 0 | YES hash-verified C (155 files, 11-19/11-19) |
| 21.1 | moved_from_root_20261101 | g1 (11 GB EM_* npz, G1 cells) + inst5 (9.5 GB) | 10-26..10-31 | 21.1 | 0 / 0 / 0 | none |
| 19.6 | l2vast/_reread | B_meta, F_trades parquet, caches | 11-17 | 19.6 | 7 / 0 / 1 running | none |
| 19.0 | l2vast/_nye | NY events (fresh, 139 k files) | 11-18..11-27 | 0 (hot) | 74 / 26 / 0 | YES (counts within 1-4%) |
| 18.4 | l2vast/shuf | shuffle-null outputs | 10-19..10-20 | 18.4 | 3 (name = null mode, not the path) | YES hash-verified C (3,362 files) |
| 16.8 | l2vast/_engvslive | engine-vs-live comparison; work/ open by 15 fds | 11-14..11-17 | 16.7 | 34 / 0 / 0 | YES on all 5 (16 G, 1,487 files) |
| 15.4 / 10.3 | l2vast/_th_fd, ds3_all_ea | FD experiments; ea all-set | 11-09..11-10 / 11-06 | 13.1 / 10.3 | 71 / 0 / 0 ; 6 / 0 / 0 | YES on all 5 (10 G each, 31 and 122 files) |
| ~460 | ds3_* others (ds3_base4 18, ds3_l2h_redo 17, ds3_h7hist 17, ds3_l2feat 17, ds3_v2 17, ds3_redo_B 16, ds3_l2set_blind 13.5, ds3_d5_work 13.5, ds3_redo_d6t 11, ds3_l2sp_redo 11, ds3_thp_c2_redo 10.5 ...) + find_1ba 13.5, find_c 12, pairP2 12.7, _hist_replica_RTY 11 | old _ds3/find/pair experiment outputs | 10-19..11-27 | ~450 | 0 refs each in current code | none |
| 6.3 | snapshots | autopilot snapshots written by snap_loop.sh (running) | to 11-27 | 0 | 0 / 0 / 2 running | none, KEEP |
| 0.9 | pylib | python libs (PYTHONPATH) | 10-19 | 0.9 | 1 | none, KEEP |
Groups: ds3* 616 GB in 265 dirs; _th_* 580 GB in 35 dirs; _major_* 63 GB; find_* 31.5; uw/uwbooks 23; instr* 11; _test* 0.5 GB (all active: written today).

Small things you named (VERIFIED): _split/*.bak_* 29 MB, _reorder/copy_q*.txt + .bak 46 MB: both are LIVE (reorder tool running now, files edited 02:22-03:14Z today). _test3..12 total ~0.5 GB, all written today: not stale. These ~75 MB are not worth the risk; do not touch. All *.bak/*.log/*.tmp scan not completed (find over 3 TB too slow; first 1,885 logs are KB-size): logs/backups are NOT where the space is.

## 2. Open right now (VERIFIED, /proc fd scan 04:10Z): do not touch
_grid/tape (4,608 fds), _th_tp/cache (2,040), _bars/feat_d (972), _chop/a2, _s2/ql_*, _fastladder/featcache, _th_sz/ijk/exact/runs_rf, _deepen_la/a, _engvslive/work, _dynexit/x8, ds3_thp/data, ds3_g2/*.npy, many */admit.log, _best/cron.lock. Running cmdlines also touch _s2, _s1r, _reorder, _th_state/base_b_rollfix, _wf_m9, _dynml.

## 3. MOVE CANDIDATES, ranked (recover = GB not read >=7 d)
| # | tree | recover | risk | what breaks if wrong | basis |
|---|---|---|---|---|---|
| 1 | shuf + ds3_l2h + ds3_redo_d8 | 71 GB | LOW | code that hard-codes l2vast/shuf, ds3_l2h, ds3_redo_d8 paths (inventory: 0, 1, 0 inbound symlinks; 0 current refs; W-ARCH already hash-verified copies on C cold_archive) | hash-verified |
| 2 | _th_fd (13) + ds3_all_ea (10) | 23 GB | LOW | replica on all 5 servers by count/size; hash not checked; 71+6 refs in code none recent | count only |
| 3 | _hist_replica 39 + _engvslive 17 | 56 GB | LOW-MED | both replicated 5x by count/size; _hist_replica still being written (coverage.csv, 11-27), _engvslive/work has open fds: free only the non-open part after a hash compare | count only |
| 4 | ds3_* / find_* / pairP2 experiment trees (list in table: ~460 GB incl. ds3_v2tree 136, ds3_redo 47.5, ds3 45) | ~450 GB | MEDIUM | 0 current-code refs but inbound symlinks (ds3_v2tree 40, ds3_redo 6,500 into ds3_tape_dedup etc.) dangle; ds3_* names built dynamically; ds3_thp is in use by 30 procs, exclude | copy first to C, verify, then Josh orders delete |
| 5 | _replica2 91, _mbo_book 44, _th_redo_replica 30, _th_exh 35, _confl 45, _reread 20, _th_zn 15, _nz2 15, _th_ptr 11, _hist_replica_RTY 11, uw 11, uwbooks 14 | ~340 GB | MEDIUM | each has code refs in current code (mbo_book, th_state_score, th_exh...) but nothing recent; a re-run of those programs would find paths missing | not replicated: copy first |
| 6 | _th_state/s345/exact_b/_mat (196 GB; s345 total 212) | 212 GB | MEDIUM | nz_exact, nz_page3, nz2 scripts and health.py reference exact_b/_mat; 10 files there written today so a job may still touch it | only 6.4 GB of _th_state on any other server |
| 7 | moved_from_root_20261101 21 + rootmoved 53 | 74 GB | MEDIUM | rootmoved are targets of symlinks outputs/autopilot/{b,i,ddmin}, outputs/n5; moved_from_root has 0 refs | none replicated |
| 8 | tables (NQ 95, ES 64, RTY 33, *_back 7) | 190 GB | HIGH | 262 inbound symlinks (ds3_tape_dedup/...) and 13 current code files reference tables | none replicated |
| 9 | rootmoves (data_databento 31, data_autopilot 38, b8 cache 137, a5 cache 44) | 267 GB | HIGH | box1 symlinks data/databento, data/autopilot, outputs/b8/cache (92 + 55 code files read them) | none replicated; unread 7 d |
| 10 | raw mbp-10 NQ 309+36, ES 189, RTY 83 | ~620 GB (NQ_blind/opts/extra +12..) | HIGH | purchased Databento data with NO other copy anywhere; engines rebuilding a month (th_tp/build_202611.py, hist_pipe, replica/sim.py read raw/NQ/) would fail; month caches in _th_tp/cache already exist on 5 servers, but a bug-fix rebuild needs raw | unread 7 d (atime) |
| - | raw/NQ_mbo (259 GB) | 0 | KEEP | read < 2 d by some job | reading |

Do not move: _th_tp/cache, _grid (hot), _bars (hot), snapshots, pylib, _nye, anything in section 2.

## 4. Totals (GB, apparent, unread >=7 d; copy to C/D first in every case)
- LOW (rows 1-2): ~94 GB. Rows 1+2 alone buy ~3 days at 30 GB/day.
- LOW-MEDIUM (row 3): +56 GB.
- MEDIUM (rows 4-7): ~1,075 GB (450 + 340 + 212 + 74).
- HIGH (rows 8-10): ~1,077 GB (190 + 267 + 620).
- Sum if everything went: ~2.3 TB (of 3.5). Free after LOW only ~130 GB; after rows 1-6 ~1.2 TB.

## 5. How to move (TEXT ONLY, not run; copies, then Josh gives a free order; keep sha verification as W-ARCH did)
Existing verified tool: `cd <repo>/outputs && nice -n19 python3 code/th_arch/cold_copy.py <tree> C 16`  (tree under /mnt/l2/l2vast, dest C:/mnt/l2/cold_archive/<tree>/, sha256 verify, never deletes).
Raw months (not under th_arch convention; plain rsync then checksum dry-run):
```
nice -n19 ionice -c3 rsync -a --partial --bwlimit=60000 --info=progress2 /mnt/l2/l2vast/raw/ES/ ubuntu@67.213.127.157:/mnt/l2/cold_archive/raw/ES/
nice -n19 ionice -c3 rsync -a --partial --bwlimit=60000 --info=progress2 /mnt/l2/l2vast/raw/RTY/ ubuntu@67.213.127.157:/mnt/l2/cold_archive/raw/RTY/
nice -n19 ionice -c3 rsync -a --partial --bwlimit=60000 --info=progress2 /mnt/l2/l2vast/raw/NQ/ ubuntu@67.213.127.157:/mnt/l2/cold_archive/raw/NQ/
# verify (no changes, size+checksum): must print nothing
rsync -anc --itemize-changes /mnt/l2/l2vast/raw/ES/ ubuntu@67.213.127.157:/mnt/l2/cold_archive/raw/ES/
```
Second copy (for two copies of bought data): same commands to D `ubuntu@72.46.85.15:/mnt/l2/cold_archive/raw/...`.
Experiment trees: `cold_copy.py ds3_v2tree C`, `... ds3_redo C`, `... tables C` (then re-point or accept dangling links; list in autopilot/DISK_TREES_INBOUND_SYMLINKS.txt).
s345: `rsync -a --partial /mnt/l2/l2vast/_th_state/s345/ ubuntu@67.213.127.157:/mnt/l2/cold_archive/_th_state_s345/`.
Throughput seen: 25 GB in 0.3 h (~80 GB/h per tree run); raw 680 GB ~ 8-9 h to C. Source reads are on a busy md1 array; run nice/ionice 3 and expect slowdown to live jobs.
Bring-back: reverse rsync from C; with 27 TB free there is no space problem there, only the box1 symlinks.

## 6. Process notes
Scratch/results: <tmp> I started du/find with nice/ionice 3 only; killed my own long find (pid) at the end; no pkill used.
