# SETUP_SERVER2 (W-S2) - second compute pool, ssh ubuntu@207.188.7.103 (64 cores, 1.5 TB, 4x7TB + 2x447GB NVMe, $5.44/h)
Rules: no Claude Code, no vendor/UW key, no /etc/trading, no private key on server 2; results are PULLED by this box. Absolute paths identical to this box.

## Log (UTC)
- 18:08Z inventory done (audit hook on a local run of TL3_S2ID_JL2 202610 = identical to stored: 642 trades, trades.parquet equal to TL3_EV_JN05W2JL2). Sets copied locally as TL3_S2ID_JL2 / TL3_S2ID_OLD (tiny scratch sets).
- 18:08Z server 2: passwordless sudo ok, python3.12, rsync, zstd present; /mnt absent, 4x7TB unmounted.
- 18:08Z network: RTT 105 ms (this box far from Dallas). 1 ssh/rsync stream ~8-10 MB/s (single TCP flow window bound); 8 parallel streams 64 MB/s. Plan: many parallel streams.

## Engine data subset (what jn05_run2 / sz_exact set-month opens; from audit + launcher)
- /mnt/l2/l2vast/_th_tp/cache 223 GB (shared month cache; keyed by day-file mtime_ns+size => day files must be copied with ns mtimes: rsync -a, verify base_key equality)
- /mnt/l2/l2vast/_hist_replica/days 35 GB (stat only on cache hit, but key needs them), _th_state/days 2.8 GB
- _th_fd/ser 8.3 GB + core_bars 0.9, _th_works 0.7, _th_joint 0.07, _early_cut 3.3, _th_screens 2.1, _engvslive 16 (store_1113 + work), _th_state/score 3.6, _th_state/s345 (nq1m_state etc; exact_b/sets), _th_sz/ijk/exact (sets/, tab_*.parquet; NOT runs_rf), ds3_all_ea 9.6
- code: outputs/code 65 MB, outputs/l2vast/ds3/code 190 MB; venv 1.9 GB (rebuild from pip freeze, 54 pkgs)
- Total ~ 270-300 GB. NOT the 3.2 TB raw L2.
- Time: at 8 streams 64 MB/s => ~75 min; 2 streams ~20 MB/s => ~4 h (too slow); using 8 streams, nice, ionice (best-effort class 7, not idle class which starves under 30 workers).

## Plan
A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E dispatcher code/th_s2/s2_dispatch.py + s2_pull.py + S2_WORKER_CAP F knee 16..128 G ready H hourly MORNING lines.
- 18:10Z server 2: mdadm RAID0 /dev/md2 (4x7TB) XFS noatime mounted /mnt/l2 (28 TB), owner ubuntu. apt: mdadm python3-venv python3-pip build-essential xfsprogs. venv rebuilt at <repo>/.venv from pip freeze (numpy 2.5.3 pandas 3.0.5 numba 0.67.0 identical to this box).
- 18:09Z rsync: code/th_s2/s2_sync.sh (8 streams, nice 19 ionice -c3, excludes keys/.env/pem/id_rsa*; scanned code trees for literal keys: none). Job list /mnt/l2/l2vast/_s2/jobs.txt, progress sync_done.txt. 4 other streams for 2026-10 cache + stores; /hist_replica/days split into 8 --files-from chunks (a single rsync of the dir ran only ~6 MB/s). Observed 55-80 MB/s total, 69 GB at 18:24Z.
- Local identity: TL3_S2ID_JL2 (copy of JL2 set) 202610 on this box: 642 trades, trades.parquet equal to stored TL3_EV_JN05W2JL2 -> set-name does not matter.
- Code written (not yet started): code/th_s2/s2_dispatch.py (dispatcher; queues listed in _s2/QUEUES.txt; leases _s2/leases/; cap S2_WORKER_CAP in CAPS.txt; ssh failure => no dispatch), s2_pull.py (pull run dirs, DONE last, drop line from queue), s2_remote_run.sh (server 2, scrubbed env), s2_knee.sh.
- 18:41Z IDENTITY PASS on server 2 (launched through s2_remote_run.sh = tp_launch.py + jn05_run2.py, TP_ENGINE=1, scrubbed env): JL2 202610 = 642 trades, net 27,487.58 (trades.parquet and mlog.parquet byte/value-equal to this box's TL3_EV_JN05W2JL2); old base JN05W2 202610 = 598 / 25,943.82 (equal). 2 concurrent jobs: 159 s / 153 s each. Day files kept ns mtimes (cache key matches). Copy still running at ~45-80 MB/s (133 GB at 18:39Z).
- 18:43Z POOL 2 LIVE: s2_dispatch.py (pid via ps), s2_pull.py, s2_state.py (S2_STATE.txt every 5 min + hourly MORNING line + S2 IDLE) running as nohup setsid on this box. QUEUES.txt order: D10 (END) > BD (END) > JOINT-EXIT > EV (FB) > REBUILD > FLOW > CONFL. END = take lines from the file end, skip only if a local tp_launch is running it. Dispatch gate: month cache dir present on server 2 (sync_done.txt), month < 202611 (extended store not on pool 2 yet), set json present. Failure handling: ssh failure => no dispatch; remote exit without DONE => parse runs_rf/<set>/<m>/ERROR, push the missing file, lease dropped, retried (max 12 pushes / 3 other failures).
- 18:43Z S2_WORKER_CAP=16 appended to /mnt/l2/l2vast/_th_tp/CAPS.txt (backup CAPS.txt.bak_s2_*). First real jobs done 18:45Z (TL3_RB_S0_K7 202610: 335 trades, 92 s).
- 18:48Z real ramp (s2_ramp.py) 16..128 in 12-min steps: results in ramp.csv/ramp.log under /mnt/l2/l2vast/_s2/, final cap written to CAPS.txt automatically.
- 18:57Z dispatcher rewritten (batch launch: one ssh per round, 8 push threads, 10 s loop; the first version launched ~3.5 s per job, too slow for short 40-90 s RB jobs). Ramp restarted at 16.
- 19:08Z ramp step 16 (real RB/D10/BD jobs): 123 completions after settle, 912 cell-months/h, mean engine secs 42, ~13.6 workers busy (short jobs), remote load1 max 14. Further steps in /mnt/l2/l2vast/_s2/ramp.log, ramp.csv; final cap auto-written to CAPS.txt (S2_WORKER_CAP). Copy ~85 pct done at 19:00Z (242 GB, 120-155 MB/s).
- Operations: daemons are nohup setsid on this box: s2_dispatch.py, s2_pull.py, s2_state.py, s2_ramp.py (explicit pids via ps). Stop dispatch: touch /mnt/l2/l2vast/_s2/STOP. Pool cap: append S2_WORKER_CAP=N to CAPS.txt.
