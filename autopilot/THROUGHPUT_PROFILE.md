# THROUGHPUT_PROFILE (W-T, 2026-11-11) - what holds the memory of one exact month-run

Run profiled: ijk JointRep, set JN04RM, month 202610 (10.4 M prints, 858 trades), one worker, in-process, current engine (th_sz_ijk/state_sizer_ijk.py unchanged). Script code/th_tp/tp_prof.py, raw json /mnt/l2/l2vast/_th_tp/prof_JN04RM_202610.json.

## Stage by stage (current engine)
| stage | RSS GB | note |
|---|---|---|
| imports (numba, pandas, engine) | 0.19 | |
| after HA.materialize (unpack ~21 day files, write npz) | 7.31 | day-file unpack high-water stays in the heap; npz is written to disk AND all arrays live in RAM |
| after Replica.load() | 7.40 | arrays re-read from the npz (the 7.2 GB heap is reused) |
| after run() | 10.97 (peak 13.3) | +3.6 GB during the run, NOT numpy arrays (array inventory 7.08 -> 7.11 GB) |
| after trades -> DataFrame (858 rows, 0.1 MB) | 10.97 | trade list / log (19 k) / trace (245 k tuples) are < 0.1 GB |

## GB by object after load() (numpy nbytes, total 7.08 GB)
- 100-ms book grid g_bpx/g_bsz/g_apx/g_asz: 4 x 0.548 = 2.19 GB (+ g_bucket, g_ts_recv 0.22)
- per-print 10-level book bpx/bsz/apx/asz: 4 x 0.417 = 1.67 GB
- L2 pre-computed columns L.* (a5 b5 ca cb ice* med rel sw* tot8 imb ..., 17 cols x 0.083): 1.4 GB
- print arrays and their derivations (ts, px, sz, ci, cts, csz, cpx, csg, cpos, si, sts, spos, rts, rpos, rcb, rca, RuleReplica3 _cdel/_sidx/_st/_sp): ~1.5 GB
- 1/3/5/10/15/45 s and X-bars, 1-min helper fields, state arrays (_sts/_smid/_smed/_cumb/_cuma 0.08), JN tables: < 0.1 GB
- trade list, log, trace, per-set copies: < 0.1 GB. Per-set copies do not exist in a batch (sets run in forked children that share the parent's pages copy-on-write).
- The +3.6 GB of the run phase is Python-heap / allocator growth (object census at the end shows only ~7 MB of live Python objects in the TP run, where it does not occur: anon grows 0.2 -> 0.4 GB). tracemalloc on the original run was ~6x slower and was aborted at 25 %, so the exact allocation site of the 3.6 GB is not attributed (likely the 10 M-element .tolist() transients of RuleReplica3.load and np.r_ copies fragmenting the glibc heap; irrelevant once the arrays are mapped).

## After: shared month cache (code/th_tp, TP_ENGINE=1)
Same cell (JN04RM 202610), cache hit:
| stage | RSS GB | PSS | anon (private) | file-backed mapped |
|---|---|---|---|---|
| after load() | 0.31 | 0.21 | 0.20 | 0.01 |
| after run() | 1.58 | 1.45 | 0.40 | 1.06 |
Private anonymous memory per worker = 0.4 GB (USS 1.44 GB only because this was the sole process mapping the month, so its touched cache pages show as Private_Clean; with several workers they are Shared and PSS divides them).
"Private" here = anonymous (heap) memory that the kernel cannot drop; file-backed mapped pages are page cache (reclaimable, shared by all workers of that month, counted in MemAvailable as cache).
4 workers at once on 202610 (JN04RM, LPB_EMPTY, LPB_BASE, RB_COMB), measured every 10 s: per worker max RSS 1.44 GB, PSS 1.32, anon 0.27; the four together RSS 5.6 GB, PSS 2.2 GB, anon 1.0 GB. Cell wall 94-102 s each (no slowdown). Samples /mnt/l2/l2vast/_th_tp/ntest/samples.txt (MemAvail in that file is dominated by the other agents' ~12 workers, not by these four).
Wall per cell-month: load+materialize 30 s -> 0.3 s; engine seconds unchanged (CPU bound, 77-130 s).
Cache cost: one set of .npy per month ~6.5-7 GB on /mnt/l2 (13 GB for 202608+202610); built once by the first worker needing it (flock, ~60 s), later workers map it. Rebuilt automatically when a day file changes (key = day-file mtime/size + engine prm).
Floats: nothing was down-cast (dtypes unchanged), so identity is by construction; float32 was not needed.
