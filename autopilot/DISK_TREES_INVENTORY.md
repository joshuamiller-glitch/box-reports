# DISK TREES INVENTORY (W-GRIDOPS, CORRECTED 19:45Z; inventory only: nothing moved, nothing deleted)

CORRECTION: the 19:05Z version counted references only in outputs/code/ and by exact path, and said "0 references" for tables / ds3_v2tree / ds3_redo / ds3_thp / ds3_redo_d8 / ds3_l2h / shuf: WRONG. This version scans all 13,010 .py/.sh files (< 2 MB) under outputs/ (including the old research code in outputs/l2vast/ds3/code and outputs/autopilot/*/code), by path "l2vast/<tree>" and by quoted path segment in files that use l2vast, and counts INBOUND SYMLINKS (links elsewhere that point into the tree; they dangle after a move; full list autopilot/DISK_TREES_INBOUND_SYMLINKS.txt).

Disk: box 1 /mnt/l2 3.5 TB, 290 GB free (92%), fill ~0.8 GB/h; root fs 59 GB free (outputs/l2vast/ds3 = 239 GB old research tree on the ROOT fs).

| tree under /mnt/l2/l2vast | size | files referencing it: current code (outputs/code, autopilot) | old research code (outputs/l2vast/...) | of those modified < 14 d | inbound symlinks | example referencing files |
|---|---|---|---|---|---|---|
| tables | 187G | 8 | 230 | 68 | 262 | outputs/autopilot/alt_bar_identity/code_altA/td.py; outputs/autopilot/alt_bar_identity/code/ind.py; outputs/l2vast/standS4/roll_driver.sh |
| ds3_v2tree | 128G | 0 | 30 | 30 | 40 | outputs/l2vast/ds3/code/v2/v3_hilo.py |
| ds3_redo | 45G | 0 | 15 | 0 | 6500 | outputs/l2vast/ds3/code/cap/redo_store_build.py |
| ds3_thp | 38G | 0 | 52 | 32 | 2279 | outputs/l2vast/ds3/code/l2feat/l2f_t4.py |
| ds3_redo_d8 | 26G | 0 | 16 | 0 | 0 | outputs/l2vast/ds3/code/recent_wins_redo/T3/t3_p.py |
| ds3_l2h | 24G | 0 | 6 | 0 | 1 | outputs/l2vast/ds3/code/recent_wins_redo/D8/uf/uf_p1_common.py |
| shuf | 18G | 4 | 37 | 4 | 0 | outputs/code/th_exh/exh_metrics.py; outputs/code/th_exh/s2null.py; outputs/l2vast/ds3/code/uf7/report7.py |
| _replica2 | 86G | 1 | 0 | 1 | 0 | outputs/code/mbo_book/mk_trades.py |
| _mbo_book | 41G | 7 | 0 | 7 | 0 | outputs/code/mbo_book/run_score.py; outputs/code/mbo_book/mbo_conv.py |
| _th_redo_replica | 28G | 44 | 0 | 44 | 0 | outputs/code/th_state_score/stage2.py; outputs/code/th_state_score/prep.py |
| _th_exh | 27G | 97 | 0 | 97 | 0 | outputs/code/th_p7cut/export_joint.py; outputs/code/th_p7cut/score_p7.py |
| ds3 | 43G | 88 | 6008 | 875 | 0 | outputs/autopilot/bak_reg1_20261031_1436/pull_nov.py; outputs/autopilot/META_nightly.sh; outputs/l2vast/ds3/pl/loop.sh |
| ds3_zones3_new | 26G | 1 | 416 | 1 | 1 | outputs/code/th_major_b/inv_a.py; outputs/l2vast/ds3/code/dis_a/dis_lib.py |

Reading: a tree is only a safe cold-archive candidate when both reference counts are 0 or the referencing code is known dead, and its inbound symlinks are re-pointed or accepted as dangling. By this stricter count NONE of the 7 approved trees is reference-free: tables and ds3_* are read by old research code (dormant? not verified) and have inbound symlinks (ds3_redo 6.5k, ds3_thp 2.3k, tables 262). shuf is referenced only by outputs/l2vast/riskS5/l2shuf.py and by 40 files that use the quoted word. W-ARCH owns the move decision and the dangling-symlink list; the old copies stay until Josh pastes the free order.

NOTE (W-ARCH finding, 19:55Z): the "shuf" hits in current code (code/th_exh/exh_metrics.py, s2null.py) are the word "shuf" = a null-test MODE NAME, not the path /mnt/l2/l2vast/shuf; the 37 old-research hits and the quoted-word count are also name matches, so shuf is NOT referenced by path (verify before the free paste). tables stays HELD (real readers: ap_pl2_base2.py, alt_bar_identity td.py / ind.py).
