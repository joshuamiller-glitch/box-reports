# MACHINES (order 1830Z, checked 2026-11-18 18:35Z): all four are compute pool only; rs4-metal-xlarge = AMD EPYC 9554P 64-core, 1 socket, 1.5 TB RAM
# box 1 (London, this machine): 32 threads (lead, engine + light grid); server 2 (Dallas, 207.188.7.103, rs4-metal-xlarge-dal-1): 64 threads, SMT OFF in firmware (smt/control = notsupported, 1 thread per core); A (Frankfurt, 109.94.96.39, rs4-metal-xlarge-fra-1): 128 threads (2 per core); B (Singapore, 206.223.224.21, rs4-metal-xlarge-sgp-1): 128 threads (2 per core)
# no cpuset / cgroup / taskset limit on server 2 (affinity mask all 64, cpuset.cpus.effective 0-63): it really is 64 threads
2026-11-18 07:35Z | box1: busy 95%, load1 29.85, workers 2, MemAvail 79 GB | server2: busy 50%, load1 31.53, workers 29, MemAvail 1219 GB | pending box1-eligible 3173 / server2-eligible 42386 (shared queues count in both; unleased, not DONE)
2026-11-18 07:35Z | WARNING server2 below 85% busy for 22 readings in a row with jobs pending
2026-11-18 07:35Z | AUTO-FILL step run: dispatcher alive pid 1240823/3551605
2026-11-18 07:35Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 45 min)
2026-11-18 07:40Z | box1: busy 95%, load1 31.75, workers 4, MemAvail 83 GB | server2: busy 43%, load1 26.15, workers 29, MemAvail 1319 GB | pending box1-eligible 3117 / server2-eligible 42330 (shared queues count in both; unleased, not DONE)
2026-11-18 07:40Z | WARNING server2 below 85% busy for 23 readings in a row with jobs pending
2026-11-18 07:40Z | AUTO-FILL step run: dispatcher alive pid 1240823/3556221
2026-11-18 07:40Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 50 min)
2026-11-18 07:45Z | box1: busy 96%, load1 32.35, workers 4, MemAvail 84 GB | server2: busy 42%, load1 27.44, workers 29, MemAvail 1316 GB | pending box1-eligible 4400 / server2-eligible 43613 (shared queues count in both; unleased, not DONE)
2026-11-18 07:45Z | WARNING server2 below 85% busy for 24 readings in a row with jobs pending
2026-11-18 07:45Z | AUTO-FILL step run: dispatcher alive pid 1240823/3561366
2026-11-18 07:45Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 55 min)
2026-11-18 07:50Z | box1: busy 97%, load1 32.87, workers 4, MemAvail 84 GB | server2: busy 41%, load1 26.08, workers 14, MemAvail 1319 GB | pending box1-eligible 4350 / server2-eligible 43563 (shared queues count in both; unleased, not DONE)
2026-11-18 07:50Z | WARNING server2 below 85% busy for 25 readings in a row with jobs pending
2026-11-18 07:50Z | AUTO-FILL step run: dispatcher alive pid 1240823/3566153
2026-11-18 07:55Z | box1: busy 97%, load1 33.38, workers 4, MemAvail 80 GB | server2: busy 40%, load1 25.71, workers 29, MemAvail 1322 GB | pending box1-eligible 4285 / server2-eligible 43498 (shared queues count in both; unleased, not DONE)
2026-11-18 07:55Z | WARNING server2 below 85% busy for 26 readings in a row with jobs pending
2026-11-18 07:55Z | AUTO-FILL step run: dispatcher alive pid 1240823/3570763
2026-11-18 08:00Z | box1: busy 99%, load1 35.97, workers 1, MemAvail 105 GB | server2: busy 43%, load1 27.12, workers 29, MemAvail 1328 GB | pending box1-eligible 4241 / server2-eligible 43454 (shared queues count in both; unleased, not DONE)
2026-11-18 08:00Z | WARNING server2 below 85% busy for 27 readings in a row with jobs pending
2026-11-18 08:00Z | AUTO-FILL step run: dispatcher alive pid 1240823/3576915
2026-11-18 08:05Z | box1: busy 98%, load1 33.27, workers 3, MemAvail 105 GB | server2: busy 41%, load1 27.21, workers 29, MemAvail 1317 GB | pending box1-eligible 4193 / server2-eligible 43406 (shared queues count in both; unleased, not DONE)
2026-11-18 08:05Z | WARNING server2 below 85% busy for 28 readings in a row with jobs pending
2026-11-18 08:05Z | AUTO-FILL step run: dispatcher alive pid 1240823/3582268
2026-11-18 08:10Z | box1: busy 98%, load1 35.20, workers 4, MemAvail 100 GB | server2: busy 41%, load1 26.99, workers 30, MemAvail 1316 GB | pending box1-eligible 4134 / server2-eligible 43347 (shared queues count in both; unleased, not DONE)
2026-11-18 08:10Z | WARNING server2 below 85% busy for 29 readings in a row with jobs pending
2026-11-18 08:10Z | AUTO-FILL step run: dispatcher alive pid 1240823/3587726
2026-11-18 08:15Z | box1: busy 93%, load1 30.80, workers 3, MemAvail 103 GB | server2: busy 41%, load1 25.64, workers 27, MemAvail 1327 GB | pending box1-eligible 4077 / server2-eligible 43290 (shared queues count in both; unleased, not DONE)
2026-11-18 08:15Z | WARNING server2 below 85% busy for 30 readings in a row with jobs pending
2026-11-18 08:15Z | AUTO-FILL step run: dispatcher alive pid 1240823/3592514
2026-11-18 08:20Z | box1: busy 97%, load1 32.81, workers 2, MemAvail 105 GB | server2: busy 41%, load1 25.69, workers 26, MemAvail 1322 GB | pending box1-eligible 4026 / server2-eligible 43239 (shared queues count in both; unleased, not DONE)
2026-11-18 08:20Z | WARNING server2 below 85% busy for 31 readings in a row with jobs pending
2026-11-18 08:20Z | AUTO-FILL step run: dispatcher alive pid 1240823/3597471
2026-11-18 08:25Z | box1: busy 98%, load1 35.10, workers 4, MemAvail 99 GB | server2: busy 41%, load1 26.93, workers 29, MemAvail 1317 GB | pending box1-eligible 3986 / server2-eligible 43199 (shared queues count in both; unleased, not DONE)
2026-11-18 08:25Z | WARNING server2 below 85% busy for 32 readings in a row with jobs pending
2026-11-18 08:25Z | AUTO-FILL step run: dispatcher alive pid 1240823/3602093
2026-11-18 08:30Z | box1: busy 93%, load1 21.28, workers 3, MemAvail 114 GB | server2: busy 51%, load1 35.48, workers 30, MemAvail 1161 GB | pending box1-eligible 3931 / server2-eligible 43144 (shared queues count in both; unleased, not DONE)
2026-11-18 08:30Z | WARNING server2 below 85% busy for 33 readings in a row with jobs pending
2026-11-18 08:30Z | AUTO-FILL step run: dispatcher alive pid 1240823/3611142
2026-11-18 08:30Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 40 min)
2026-11-18 08:35Z | box1: busy 99%, load1 38.59, workers 2, MemAvail 100 GB | server2: busy 51%, load1 31.46, workers 30, MemAvail 1202 GB | pending box1-eligible 3897 / server2-eligible 43110 (shared queues count in both; unleased, not DONE)
2026-11-18 08:35Z | WARNING server2 below 85% busy for 34 readings in a row with jobs pending
2026-11-18 08:35Z | AUTO-FILL step run: dispatcher alive pid 1240823/3618680
2026-11-18 08:35Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 45 min)
2026-11-18 08:40Z | box1: busy 100%, load1 36.55, workers 1, MemAvail 100 GB | server2: busy 44%, load1 26.83, workers 30, MemAvail 1319 GB | pending box1-eligible 3851 / server2-eligible 43064 (shared queues count in both; unleased, not DONE)
2026-11-18 08:40Z | WARNING server2 below 85% busy for 35 readings in a row with jobs pending
2026-11-18 08:40Z | AUTO-FILL step run: dispatcher alive pid 1240823/3623599
2026-11-18 08:40Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 50 min)
2026-11-18 08:45Z | box1: busy 100%, load1 36.34, workers 0, MemAvail 103 GB | server2: busy 42%, load1 27.08, workers 30, MemAvail 1315 GB | pending box1-eligible 3817 / server2-eligible 43030 (shared queues count in both; unleased, not DONE)
2026-11-18 08:45Z | WARNING server2 below 85% busy for 36 readings in a row with jobs pending
2026-11-18 08:45Z | AUTO-FILL step run: dispatcher alive pid 1240823/3628901
2026-11-18 08:45Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 55 min)
2026-11-18 08:50Z | box1: busy 99%, load1 39.70, workers 0, MemAvail 95 GB | server2: busy 42%, load1 27.15, workers 29, MemAvail 1321 GB | pending box1-eligible 3776 / server2-eligible 42989 (shared queues count in both; unleased, not DONE)
2026-11-18 08:50Z | WARNING server2 below 85% busy for 37 readings in a row with jobs pending
2026-11-18 08:50Z | AUTO-FILL step run: dispatcher alive pid 1240823/3633559
2026-11-18 08:55Z | box1: busy 96%, load1 31.63, workers 0, MemAvail 90 GB | server2: busy 42%, load1 27.11, workers 30, MemAvail 1316 GB | pending box1-eligible 3729 / server2-eligible 42942 (shared queues count in both; unleased, not DONE)
2026-11-18 08:55Z | WARNING server2 below 85% busy for 38 readings in a row with jobs pending
2026-11-18 08:55Z | AUTO-FILL step run: dispatcher alive pid 1240823/3637696
2026-11-18 09:00Z | box1: busy 92%, load1 29.49, workers 0, MemAvail 69 GB | server2: busy 43%, load1 27.31, workers 26, MemAvail 1322 GB | pending box1-eligible 3677 / server2-eligible 42890 (shared queues count in both; unleased, not DONE)
2026-11-18 09:00Z | WARNING server2 below 85% busy for 39 readings in a row with jobs pending
2026-11-18 09:00Z | AUTO-FILL step run: dispatcher alive pid 1240823/3642459
2026-11-18 09:05Z | box1: busy 90%, load1 35.65, workers 0, MemAvail 72 GB | server2: busy 42%, load1 26.89, workers 27, MemAvail 1320 GB | pending box1-eligible 3644 / server2-eligible 42857 (shared queues count in both; unleased, not DONE)
2026-11-18 09:05Z | WARNING server2 below 85% busy for 40 readings in a row with jobs pending
2026-11-18 09:05Z | AUTO-FILL step run: dispatcher alive pid 1240823/3648417
2026-11-18 09:10Z | box1: busy 92%, load1 29.73, workers 0, MemAvail 80 GB | server2: busy 41%, load1 26.21, workers 26, MemAvail 1321 GB | pending box1-eligible 3597 / server2-eligible 42806 (shared queues count in both; unleased, not DONE)
2026-11-18 09:10Z | WARNING server2 below 85% busy for 41 readings in a row with jobs pending
2026-11-18 09:10Z | AUTO-FILL step run: dispatcher alive pid 1240823/3654392
2026-11-18 09:15Z | box1: busy 94%, load1 30.42, workers 0, MemAvail 70 GB | server2: busy 42%, load1 26.81, workers 30, MemAvail 1316 GB | pending box1-eligible 3560 / server2-eligible 42773 (shared queues count in both; unleased, not DONE)
2026-11-18 09:15Z | WARNING server2 below 85% busy for 42 readings in a row with jobs pending
2026-11-18 09:15Z | AUTO-FILL step run: dispatcher alive pid 1240823/3659111
2026-11-18 09:20Z | box1: busy 88%, load1 27.00, workers 0, MemAvail 75 GB | server2: busy 41%, load1 27.16, workers 30, MemAvail 1317 GB | pending box1-eligible 3510 / server2-eligible 42723 (shared queues count in both; unleased, not DONE)
2026-11-18 09:20Z | WARNING server2 below 85% busy for 43 readings in a row with jobs pending
2026-11-18 09:20Z | AUTO-FILL step run: dispatcher alive pid 1240823/3664158
2026-11-18 09:25Z | box1: busy 86%, load1 28.04, workers 0, MemAvail 80 GB | server2: busy 42%, load1 27.38, workers 30, MemAvail 1316 GB | pending box1-eligible 3476 / server2-eligible 42689 (shared queues count in both; unleased, not DONE)
2026-11-18 09:25Z | WARNING server2 below 85% busy for 44 readings in a row with jobs pending
2026-11-18 09:25Z | AUTO-FILL step run: dispatcher alive pid 1240823/3667993
2026-11-18 09:30Z | box1: busy 92%, load1 28.80, workers 0, MemAvail 72 GB | server2: busy 51%, load1 36.17, workers 27, MemAvail 1163 GB | pending box1-eligible 3435 / server2-eligible 42648 (shared queues count in both; unleased, not DONE)
2026-11-18 09:30Z | WARNING server2 below 85% busy for 45 readings in a row with jobs pending
2026-11-18 09:30Z | AUTO-FILL step run: dispatcher alive pid 1240823/3672724
2026-11-18 09:30Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 40 min)
2026-11-18 09:35Z | box1: busy 96%, load1 31.15, workers 0, MemAvail 71 GB | server2: busy 52%, load1 31.35, workers 30, MemAvail 1206 GB | pending box1-eligible 3403 / server2-eligible 42616 (shared queues count in both; unleased, not DONE)
2026-11-18 09:35Z | WARNING server2 below 85% busy for 46 readings in a row with jobs pending
2026-11-18 09:35Z | AUTO-FILL step run: dispatcher alive pid 1240823/3677915
2026-11-18 09:35Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 45 min)
2026-11-18 09:40Z | box1: busy 95%, load1 38.13, workers 4, MemAvail 96 GB | server2: busy 44%, load1 27.08, workers 28, MemAvail 1319 GB | pending box1-eligible 3408 / server2-eligible 42621 (shared queues count in both; unleased, not DONE)
2026-11-18 09:40Z | WARNING server2 below 85% busy for 47 readings in a row with jobs pending
2026-11-18 09:40Z | AUTO-FILL step run: dispatcher alive pid 1240823/3682927
2026-11-18 09:40Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 50 min)
2026-11-18 09:45Z | box1: busy 100%, load1 40.15, workers 4, MemAvail 94 GB | server2: busy 42%, load1 27.66, workers 30, MemAvail 1315 GB | pending box1-eligible 3374 / server2-eligible 42587 (shared queues count in both; unleased, not DONE)
2026-11-18 09:45Z | WARNING server2 below 85% busy for 48 readings in a row with jobs pending
2026-11-18 09:45Z | AUTO-FILL step run: dispatcher alive pid 1240823/3688388
2026-11-18 09:45Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 55 min)
2026-11-18 09:50Z | box1: busy 100%, load1 39.33, workers 3, MemAvail 95 GB | server2: busy 42%, load1 27.18, workers 30, MemAvail 1319 GB | pending box1-eligible 3339 / server2-eligible 42552 (shared queues count in both; unleased, not DONE)
2026-11-18 09:50Z | WARNING server2 below 85% busy for 49 readings in a row with jobs pending
2026-11-18 09:50Z | AUTO-FILL step run: dispatcher alive pid 1240823/3693732
2026-11-18 09:55Z | box1: busy 100%, load1 40.03, workers 4, MemAvail 83 GB | server2: busy 42%, load1 26.69, workers 29, MemAvail 1318 GB | pending box1-eligible 3302 / server2-eligible 42515 (shared queues count in both; unleased, not DONE)
2026-11-18 09:55Z | WARNING server2 below 85% busy for 50 readings in a row with jobs pending
2026-11-18 09:55Z | AUTO-FILL step run: dispatcher alive pid 1240823/3698837
2026-11-18 10:00Z | box1: busy 97%, load1 34.19, workers 0, MemAvail 67 GB | server2: busy 43%, load1 27.18, workers 28, MemAvail 1319 GB | pending box1-eligible 3273 / server2-eligible 42486 (shared queues count in both; unleased, not DONE)
2026-11-18 10:00Z | WARNING server2 below 85% busy for 51 readings in a row with jobs pending
2026-11-18 10:00Z | AUTO-FILL step run: dispatcher alive pid 1240823/3703645
2026-11-18 10:05Z | box1: busy 92%, load1 28.97, workers 0, MemAvail 81 GB | server2: busy 43%, load1 26.93, workers 30, MemAvail 1318 GB | pending box1-eligible 3239 / server2-eligible 42452 (shared queues count in both; unleased, not DONE)
2026-11-18 10:05Z | WARNING server2 below 85% busy for 52 readings in a row with jobs pending
2026-11-18 10:05Z | AUTO-FILL step run: dispatcher alive pid 1240823/3708622
2026-11-18 10:10Z | box1: busy 79%, load1 24.90, workers 0, MemAvail 92 GB | server2: busy 42%, load1 26.56, workers 29, MemAvail 1320 GB | pending box1-eligible 3212 / server2-eligible 42425 (shared queues count in both; unleased, not DONE)
2026-11-18 10:10Z | WARNING server2 below 85% busy for 53 readings in a row with jobs pending
2026-11-18 10:10Z | AUTO-FILL step run: dispatcher alive pid 1240823/3715018
2026-11-18 10:15Z | box1: busy 82%, load1 27.28, workers 0, MemAvail 91 GB | server2: busy 43%, load1 27.20, workers 29, MemAvail 1318 GB | pending box1-eligible 3188 / server2-eligible 42401 (shared queues count in both; unleased, not DONE)
2026-11-18 10:15Z | WARNING box1 below 85% busy for 2 readings in a row with jobs pending
2026-11-18 10:15Z | WARNING server2 below 85% busy for 54 readings in a row with jobs pending
2026-11-18 10:15Z | box1 AUTO-FILL: SIGCONT of 0 stopped admission/launch/driver procs []; admit.log silent -3 s; ql_drivers alive before=19 restarted=[]; workers 0
2026-11-18 10:15Z | AUTO-FILL step run: dispatcher alive pid 1240823/3721169
2026-11-18 10:20Z | box1: busy 85%, load1 27.94, workers 0, MemAvail 91 GB | server2: busy 42%, load1 26.89, workers 30, MemAvail 1315 GB | pending box1-eligible 3155 / server2-eligible 42368 (shared queues count in both; unleased, not DONE)
2026-11-18 10:20Z | WARNING box1 below 85% busy for 3 readings in a row with jobs pending
2026-11-18 10:20Z | WARNING server2 below 85% busy for 55 readings in a row with jobs pending
2026-11-18 10:20Z | box1 AUTO-FILL: SIGCONT of 0 stopped admission/launch/driver procs []; admit.log silent -3 s; ql_drivers alive before=19 restarted=[]; workers 0
2026-11-18 10:20Z | AUTO-FILL step run: dispatcher alive pid 1240823/3726745
2026-11-18 10:25Z | box1: busy 83%, load1 29.91, workers 0, MemAvail 115 GB | server2: busy 42%, load1 27.02, workers 29, MemAvail 1317 GB | pending box1-eligible 3127 / server2-eligible 42340 (shared queues count in both; unleased, not DONE)
2026-11-18 10:25Z | WARNING box1 below 85% busy for 4 readings in a row with jobs pending
2026-11-18 10:25Z | WARNING server2 below 85% busy for 56 readings in a row with jobs pending
2026-11-18 10:25Z | box1 AUTO-FILL: SIGCONT of 0 stopped admission/launch/driver procs []; admit.log silent -3 s; ql_drivers alive before=19 restarted=[]; workers 0
2026-11-18 10:25Z | AUTO-FILL step run: dispatcher alive pid 1240823/3731811
2026-11-18 10:30Z | box1: busy 99%, load1 38.18, workers 0, MemAvail 110 GB | server2: busy 51%, load1 35.19, workers 29, MemAvail 1162 GB | pending box1-eligible 3094 / server2-eligible 42307 (shared queues count in both; unleased, not DONE)
2026-11-18 10:30Z | WARNING server2 below 85% busy for 57 readings in a row with jobs pending
2026-11-18 10:30Z | AUTO-FILL step run: dispatcher alive pid 1240823/3737920
2026-11-18 10:30Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 40 min)
2026-11-18 10:35Z | box1: busy 98%, load1 37.39, workers 1, MemAvail 104 GB | server2: busy 52%, load1 31.64, workers 30, MemAvail 1191 GB | pending box1-eligible 3062 / server2-eligible 42275 (shared queues count in both; unleased, not DONE)
2026-11-18 10:35Z | WARNING server2 below 85% busy for 58 readings in a row with jobs pending
2026-11-18 10:35Z | AUTO-FILL step run: dispatcher alive pid 1240823/3743916
2026-11-18 10:35Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 45 min)
2026-11-18 10:40Z | box1: busy 98%, load1 34.34, workers 0, MemAvail 89 GB | server2: busy 44%, load1 27.14, workers 28, MemAvail 1318 GB | pending box1-eligible 3036 / server2-eligible 42249 (shared queues count in both; unleased, not DONE)
2026-11-18 10:40Z | WARNING server2 below 85% busy for 59 readings in a row with jobs pending
2026-11-18 10:40Z | AUTO-FILL step run: dispatcher alive pid 1240823/3748895
2026-11-18 10:40Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 50 min)
2026-11-18 10:45Z | box1: busy 78%, load1 25.79, workers 0, MemAvail 87 GB | server2: busy 42%, load1 26.61, workers 28, MemAvail 1320 GB | pending box1-eligible 3001 / server2-eligible 42214 (shared queues count in both; unleased, not DONE)
2026-11-18 10:45Z | WARNING server2 below 85% busy for 60 readings in a row with jobs pending
2026-11-18 10:45Z | AUTO-FILL step run: dispatcher alive pid 1240823/3756886
2026-11-18 10:45Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 55 min)
2026-11-18 10:50Z | box1: busy 90%, load1 29.19, workers 0, MemAvail 87 GB | server2: busy 41%, load1 26.89, workers 30, MemAvail 1317 GB | pending box1-eligible 2953 / server2-eligible 42166 (shared queues count in both; unleased, not DONE)
2026-11-18 10:50Z | WARNING server2 below 85% busy for 61 readings in a row with jobs pending
2026-11-18 10:50Z | AUTO-FILL step run: dispatcher alive pid 1240823/3761954
2026-11-18 10:55Z | box1: busy 85%, load1 27.58, workers 1, MemAvail 78 GB | server2: busy 41%, load1 26.42, workers 29, MemAvail 1319 GB | pending box1-eligible 2906 / server2-eligible 42119 (shared queues count in both; unleased, not DONE)
2026-11-18 10:55Z | WARNING server2 below 85% busy for 62 readings in a row with jobs pending
2026-11-18 10:55Z | AUTO-FILL step run: dispatcher alive pid 1240823/3766726
2026-11-18 11:00Z | box1: busy 84%, load1 27.52, workers 0, MemAvail 85 GB | server2: busy 42%, load1 28.12, workers 28, MemAvail 1318 GB | pending box1-eligible 2867 / server2-eligible 42080 (shared queues count in both; unleased, not DONE)
2026-11-18 11:00Z | WARNING server2 below 85% busy for 63 readings in a row with jobs pending
2026-11-18 11:00Z | AUTO-FILL step run: dispatcher alive pid 1240823/3771566
2026-11-18 11:05Z | box1: busy 96%, load1 37.56, workers 0, MemAvail 101 GB | server2: busy 41%, load1 25.86, workers 29, MemAvail 1318 GB | pending box1-eligible 2823 / server2-eligible 42036 (shared queues count in both; unleased, not DONE)
2026-11-18 11:05Z | WARNING server2 below 85% busy for 64 readings in a row with jobs pending
2026-11-18 11:05Z | AUTO-FILL step run: dispatcher alive pid 1240823/3778568
2026-11-18 11:10Z | box1: busy 100%, load1 38.80, workers 0, MemAvail 107 GB | server2: busy 42%, load1 26.55, workers 30, MemAvail 1318 GB | pending box1-eligible 2783 / server2-eligible 41996 (shared queues count in both; unleased, not DONE)
2026-11-18 11:10Z | WARNING server2 below 85% busy for 65 readings in a row with jobs pending
2026-11-18 11:10Z | AUTO-FILL step run: dispatcher alive pid 1240823/3786782
2026-11-18 11:15Z | box1: busy 99%, load1 40.93, workers 0, MemAvail 102 GB | server2: busy 42%, load1 26.66, workers 29, MemAvail 1321 GB | pending box1-eligible 2750 / server2-eligible 41963 (shared queues count in both; unleased, not DONE)
2026-11-18 11:15Z | WARNING server2 below 85% busy for 66 readings in a row with jobs pending
2026-11-18 11:15Z | AUTO-FILL step run: dispatcher alive pid 1240823/3792963
2026-11-18 11:20Z | box1: busy 88%, load1 29.38, workers 0, MemAvail 81 GB | server2: busy 41%, load1 26.26, workers 30, MemAvail 1318 GB | pending box1-eligible 2703 / server2-eligible 41916 (shared queues count in both; unleased, not DONE)
2026-11-18 11:20Z | WARNING server2 below 85% busy for 67 readings in a row with jobs pending
2026-11-18 11:20Z | AUTO-FILL step run: dispatcher alive pid 1240823/3798016
2026-11-18 11:25Z | box1: busy 90%, load1 28.60, workers 0, MemAvail 85 GB | server2: busy 42%, load1 26.16, workers 29, MemAvail 1321 GB | pending box1-eligible 2657 / server2-eligible 41870 (shared queues count in both; unleased, not DONE)
2026-11-18 11:25Z | WARNING server2 below 85% busy for 68 readings in a row with jobs pending
2026-11-18 11:25Z | AUTO-FILL step run: dispatcher alive pid 1240823/3802560
2026-11-18 11:30Z | box1: busy 86%, load1 27.87, workers 1, MemAvail 84 GB | server2: busy 50%, load1 35.34, workers 30, MemAvail 1169 GB | pending box1-eligible 2615 / server2-eligible 41828 (shared queues count in both; unleased, not DONE)
2026-11-18 11:30Z | WARNING server2 below 85% busy for 69 readings in a row with jobs pending
2026-11-18 11:30Z | AUTO-FILL step run: dispatcher alive pid 1240823/3807413
2026-11-18 11:35Z | box1: busy 86%, load1 30.56, workers 0, MemAvail 86 GB | server2: busy 51%, load1 30.34, workers 30, MemAvail 1219 GB | pending box1-eligible 2571 / server2-eligible 41784 (shared queues count in both; unleased, not DONE)
2026-11-18 11:35Z | WARNING server2 below 85% busy for 70 readings in a row with jobs pending
2026-11-18 11:35Z | AUTO-FILL step run: dispatcher alive pid 1240823/3812134
2026-11-18 11:35Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 45 min)
2026-11-18 11:40Z | box1: busy 90%, load1 29.35, workers 0, MemAvail 78 GB | server2: busy 44%, load1 26.83, workers 28, MemAvail 1318 GB | pending box1-eligible 2532 / server2-eligible 41745 (shared queues count in both; unleased, not DONE)
2026-11-18 11:40Z | WARNING server2 below 85% busy for 71 readings in a row with jobs pending
2026-11-18 11:40Z | AUTO-FILL step run: dispatcher alive pid 1240823/3816657
2026-11-18 11:40Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 50 min)
2026-11-18 11:45Z | box1: busy 96%, load1 36.05, workers 1, MemAvail 76 GB | server2: busy 41%, load1 25.81, workers 29, MemAvail 1322 GB | pending box1-eligible 2490 / server2-eligible 41703 (shared queues count in both; unleased, not DONE)
2026-11-18 11:45Z | WARNING server2 below 85% busy for 72 readings in a row with jobs pending
2026-11-18 11:45Z | AUTO-FILL step run: dispatcher alive pid 1240823/3822395
2026-11-18 11:45Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 55 min)
2026-11-18 11:50Z | box1: busy 98%, load1 36.89, workers 0, MemAvail 84 GB | server2: busy 42%, load1 26.87, workers 29, MemAvail 1317 GB | pending box1-eligible 2446 / server2-eligible 41659 (shared queues count in both; unleased, not DONE)
2026-11-18 11:50Z | WARNING server2 below 85% busy for 73 readings in a row with jobs pending
2026-11-18 11:50Z | AUTO-FILL step run: dispatcher alive pid 1240823/3828907
2026-11-18 11:55Z | box1: busy 99%, load1 43.89, workers 4, MemAvail 96 GB | server2: busy 42%, load1 27.10, workers 27, MemAvail 1323 GB | pending box1-eligible 2418 / server2-eligible 41631 (shared queues count in both; unleased, not DONE)
2026-11-18 11:55Z | WARNING server2 below 85% busy for 74 readings in a row with jobs pending
2026-11-18 11:55Z | AUTO-FILL step run: dispatcher alive pid 1240823/3834364
2026-11-18 12:00Z | box1: busy 100%, load1 39.46, workers 1, MemAvail 97 GB | server2: busy 43%, load1 27.46, workers 30, MemAvail 1318 GB | pending box1-eligible 2372 / server2-eligible 41585 (shared queues count in both; unleased, not DONE)
2026-11-18 12:00Z | WARNING server2 below 85% busy for 75 readings in a row with jobs pending
2026-11-18 12:00Z | AUTO-FILL step run: dispatcher alive pid 1240823/3840415
2026-11-18 12:05Z | box1: busy 87%, load1 25.09, workers 3, MemAvail 81 GB | server2: busy 43%, load1 26.84, workers 30, MemAvail 1319 GB | pending box1-eligible 2338 / server2-eligible 41551 (shared queues count in both; unleased, not DONE)
2026-11-18 12:05Z | WARNING server2 below 85% busy for 76 readings in a row with jobs pending
2026-11-18 12:05Z | AUTO-FILL step run: dispatcher alive pid 1240823/3848097
2026-11-18 12:10Z | box1: busy 94%, load1 31.04, workers 1, MemAvail 84 GB | server2: busy 42%, load1 27.03, workers 30, MemAvail 1317 GB | pending box1-eligible 2306 / server2-eligible 41519 (shared queues count in both; unleased, not DONE)
2026-11-18 12:10Z | WARNING server2 below 85% busy for 77 readings in a row with jobs pending
2026-11-18 12:10Z | AUTO-FILL step run: dispatcher alive pid 1240823/3853501
2026-11-18 12:15Z | box1: busy 86%, load1 26.01, workers 0, MemAvail 84 GB | server2: busy 42%, load1 27.56, workers 29, MemAvail 1316 GB | pending box1-eligible 2277 / server2-eligible 41490 (shared queues count in both; unleased, not DONE)
2026-11-18 12:15Z | WARNING server2 below 85% busy for 78 readings in a row with jobs pending
2026-11-18 12:15Z | AUTO-FILL step run: dispatcher alive pid 1240823/3857986
2026-11-18 12:20Z | box1: busy 86%, load1 27.32, workers 0, MemAvail 76 GB | server2: busy 42%, load1 27.19, workers 29, MemAvail 1317 GB | pending box1-eligible 2246 / server2-eligible 41459 (shared queues count in both; unleased, not DONE)
2026-11-18 12:20Z | WARNING server2 below 85% busy for 79 readings in a row with jobs pending
2026-11-18 12:20Z | AUTO-FILL step run: dispatcher alive pid 1240823/3862902
2026-11-18 12:25Z | box1: busy 94%, load1 31.65, workers 0, MemAvail 89 GB | server2: busy 42%, load1 27.25, workers 30, MemAvail 1315 GB | pending box1-eligible 2217 / server2-eligible 41430 (shared queues count in both; unleased, not DONE)
2026-11-18 12:25Z | WARNING server2 below 85% busy for 80 readings in a row with jobs pending
2026-11-18 12:25Z | AUTO-FILL step run: dispatcher alive pid 1240823/3868183
2026-11-18 12:30Z | box1: busy 93%, load1 31.31, workers 0, MemAvail 86 GB | server2: busy 51%, load1 35.67, workers 29, MemAvail 1184 GB | pending box1-eligible 2184 / server2-eligible 41397 (shared queues count in both; unleased, not DONE)
2026-11-18 12:30Z | WARNING server2 below 85% busy for 81 readings in a row with jobs pending
2026-11-18 12:30Z | AUTO-FILL step run: dispatcher alive pid 1240823/3873716
2026-11-18 12:35Z | box1: busy 93%, load1 30.72, workers 0, MemAvail 79 GB | server2: busy 52%, load1 31.39, workers 29, MemAvail 1219 GB | pending box1-eligible 2157 / server2-eligible 41370 (shared queues count in both; unleased, not DONE)
2026-11-18 12:35Z | WARNING server2 below 85% busy for 82 readings in a row with jobs pending
2026-11-18 12:35Z | AUTO-FILL step run: dispatcher alive pid 1240823/3878911
2026-11-18 12:35Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 45 min)
2026-11-18 12:40Z | box1: busy 95%, load1 33.07, workers 0, MemAvail 82 GB | server2: busy 45%, load1 27.21, workers 28, MemAvail 1319 GB | pending box1-eligible 2133 / server2-eligible 41346 (shared queues count in both; unleased, not DONE)
2026-11-18 12:40Z | WARNING server2 below 85% busy for 83 readings in a row with jobs pending
2026-11-18 12:40Z | AUTO-FILL step run: dispatcher alive pid 1240823/3883692
2026-11-18 12:40Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 50 min)
2026-11-18 12:45Z | box1: busy 99%, load1 36.80, workers 4, MemAvail 100 GB | server2: busy 42%, load1 26.46, workers 29, MemAvail 1317 GB | pending box1-eligible 2107 / server2-eligible 41320 (shared queues count in both; unleased, not DONE)
2026-11-18 12:45Z | WARNING server2 below 85% busy for 84 readings in a row with jobs pending
2026-11-18 12:45Z | AUTO-FILL step run: dispatcher alive pid 1240823/3889081
2026-11-18 12:45Z | LEAD SILENT 40 MIN (no real lead note in MORNING.md for 55 min)
2026-11-18 12:50Z | box1: busy 98%, load1 39.93, workers 4, MemAvail 100 GB | server2: busy 42%, load1 26.91, workers 29, MemAvail 1317 GB | pending box1-eligible 2074 / server2-eligible 41287 (shared queues count in both; unleased, not DONE)
2026-11-18 12:50Z | WARNING server2 below 85% busy for 85 readings in a row with jobs pending
2026-11-18 12:50Z | AUTO-FILL step run: dispatcher alive pid 1240823/3896693
2026-11-18 12:55Z | box1: busy 91%, load1 38.00, workers 4, MemAvail 64 GB | server2: busy 42%, load1 26.58, workers 30, MemAvail 1320 GB | pending box1-eligible 2036 / server2-eligible 41249 (shared queues count in both; unleased, not DONE)
2026-11-18 12:55Z | WARNING server2 below 85% busy for 86 readings in a row with jobs pending
2026-11-18 12:55Z | AUTO-FILL step run: dispatcher alive pid 1240823/3903325
2026-11-18 13:00Z | box1: busy 99%, load1 33.72, workers 0, MemAvail 78 GB | server2: busy 43%, load1 27.23, workers 26, MemAvail 1321 GB | pending box1-eligible 2002 / server2-eligible 41215 (shared queues count in both; unleased, not DONE)
2026-11-18 13:00Z | WARNING server2 below 85% busy for 87 readings in a row with jobs pending
2026-11-18 13:00Z | AUTO-FILL step run: dispatcher alive pid 1240823/3908701
2026-11-18 13:05Z | box1: busy 95%, load1 32.33, workers 0, MemAvail 78 GB | server2: busy 43%, load1 31.41, workers 29, MemAvail 1443 GB | pending box1-eligible 1979 / server2-eligible 41192 (shared queues count in both; unleased, not DONE)
2026-11-18 13:05Z | WARNING server2 below 85% busy for 88 readings in a row with jobs pending
2026-11-18 13:05Z | AUTO-FILL step run: dispatcher alive pid 1240823/3913087
2026-11-18 13:10Z | box1: busy 94%, load1 31.39, workers 0, MemAvail 78 GB | server2: busy 71%, load1 54.57, workers 17, MemAvail 1402 GB | pending box1-eligible 1948 / server2-eligible 41161 (shared queues count in both; unleased, not DONE)
2026-11-18 13:10Z | WARNING server2 below 85% busy for 89 readings in a row with jobs pending
2026-11-18 13:10Z | AUTO-FILL step run: dispatcher alive pid 1240823/3918623
2026-11-18 13:15Z | box1: busy 98%, load1 45.15, workers 16, MemAvail 58 GB | server2: busy 73%, load1 34.41, workers 24, MemAvail 1425 GB | pending box1-eligible 2121 / server2-eligible 41334 (shared queues count in both; unleased, not DONE)
2026-11-18 13:15Z | WARNING server2 below 85% busy for 90 readings in a row with jobs pending
2026-11-18 13:15Z | AUTO-FILL step run: dispatcher alive pid 1240823/3925406
2026-11-18 13:20Z | box1: busy 100%, load1 37.80, workers 8, MemAvail 59 GB | server2: busy 47%, load1 38.69, workers 46, MemAvail 1385 GB | pending box1-eligible 2040 / server2-eligible 41250 (shared queues count in both; unleased, not DONE)
2026-11-18 13:20Z | WARNING server2 below 85% busy for 91 readings in a row with jobs pending
2026-11-18 13:20Z | AUTO-FILL step run: dispatcher alive pid 1240823/3930860
2026-11-18 13:25Z | box1: busy 99%, load1 40.36, workers 8, MemAvail 64 GB | server2: busy 75%, load1 48.50, workers 50, MemAvail 1375 GB | pending box1-eligible 1964 / server2-eligible 41177 (shared queues count in both; unleased, not DONE)
2026-11-18 13:25Z | WARNING server2 below 85% busy for 92 readings in a row with jobs pending
2026-11-18 13:25Z | AUTO-FILL step run: dispatcher alive pid 1240823/3936103
2026-11-18 13:30Z | box1: busy 100%, load1 39.00, workers 8, MemAvail 63 GB | server2: busy 90%, load1 97.17, workers 33, MemAvail 1254 GB | pending box1-eligible 1895 / server2-eligible 41108 (shared queues count in both; unleased, not DONE)
2026-11-18 13:35Z | box1: busy 99%, load1 34.58, workers 2, MemAvail 74 GB | server2: busy 100%, load1 97.00, workers 33, MemAvail 1269 GB | pending box1-eligible 1853 / server2-eligible 41058 (shared queues count in both; unleased, not DONE)
2026-11-18 13:40Z | box1: busy 99%, load1 44.18, workers 8, MemAvail 91 GB | server2: busy 100%, load1 99.34, workers 41, MemAvail 1293 GB | pending box1-eligible 1799 / server2-eligible 41012 (shared queues count in both; unleased, not DONE)
2026-11-18 13:45Z | box1: busy 100%, load1 43.01, workers 6, MemAvail 90 GB | server2: busy 100%, load1 91.45, workers 25, MemAvail 1329 GB | pending box1-eligible 1741 / server2-eligible 40954 (shared queues count in both; unleased, not DONE)
2026-11-18 13:50Z | box1: busy 100%, load1 41.29, workers 5, MemAvail 91 GB | server2: busy 100%, load1 79.27, workers 26, MemAvail 1393 GB | pending box1-eligible 1699 / server2-eligible 40912 (shared queues count in both; unleased, not DONE)
2026-11-18 13:55Z | box1: busy 100%, load1 45.45, workers 4, MemAvail 81 GB | server2: busy 100%, load1 79.40, workers 25, MemAvail 1367 GB | pending box1-eligible 1660 / server2-eligible 40873 (shared queues count in both; unleased, not DONE)
2026-11-18 14:00Z | box1: busy 99%, load1 38.43, workers 8, MemAvail 76 GB | server2: busy 100%, load1 79.63, workers 26, MemAvail 1342 GB | pending box1-eligible 1622 / server2-eligible 40835 (shared queues count in both; unleased, not DONE)
2026-11-18 14:05Z | box1: busy 99%, load1 34.40, workers 4, MemAvail 61 GB | server2: busy 100%, load1 79.59, workers 26, MemAvail 1334 GB | pending box1-eligible 1582 / server2-eligible 40795 (shared queues count in both; unleased, not DONE)
2026-11-18 14:10Z | box1: busy 99%, load1 35.83, workers 6, MemAvail 62 GB | server2: busy 100%, load1 72.63, workers 18, MemAvail 1370 GB | pending box1-eligible 1563 / server2-eligible 40776 (shared queues count in both; unleased, not DONE)
2026-11-18 14:15Z | box1: busy 100%, load1 40.86, workers 8, MemAvail 65 GB | server2: busy 100%, load1 74.65, workers 18, MemAvail 1375 GB | pending box1-eligible 1528 / server2-eligible 40741 (shared queues count in both; unleased, not DONE)
2026-11-18 14:20Z | box1: busy 100%, load1 36.76, workers 2, MemAvail 76 GB | server2: busy 100%, load1 81.35, workers 18, MemAvail 1318 GB | pending box1-eligible 1710 / server2-eligible 40923 (shared queues count in both; unleased, not DONE)
2026-11-18 14:25Z | box1: busy 99%, load1 44.81, workers 18, MemAvail 55 GB | server2: busy 100%, load1 90.18, workers 14, MemAvail 1356 GB | pending box1-eligible 1696 / server2-eligible 40909 (shared queues count in both; unleased, not DONE)
2026-11-18 14:30Z | box1: busy 99%, load1 33.81, workers 1, MemAvail 65 GB | server2: busy 100%, load1 85.84, workers 14, MemAvail 1276 GB | pending box1-eligible 1768 / server2-eligible 40981 (shared queues count in both; unleased, not DONE)
2026-11-18 14:35Z | box1: busy 100%, load1 48.88, workers 15, MemAvail 47 GB | server2: busy 100%, load1 80.59, workers 14, MemAvail 1208 GB | pending box1-eligible 1746 / server2-eligible 40959 (shared queues count in both; unleased, not DONE)
2026-11-18 14:40Z | box1: busy 99%, load1 47.93, workers 22, MemAvail 36 GB | server2: busy 100%, load1 81.15, workers 14, MemAvail 1299 GB | pending box1-eligible 1718 / server2-eligible 40931 (shared queues count in both; unleased, not DONE)
2026-11-18 14:45Z | box1: busy 100%, load1 42.25, workers 6, MemAvail 90 GB | server2: busy 100%, load1 72.61, workers 14, MemAvail 1283 GB | pending box1-eligible 1682 / server2-eligible 40895 (shared queues count in both; unleased, not DONE)
2026-11-18 14:50Z | box1: busy 99%, load1 45.99, workers 1, MemAvail 102 GB | server2: busy 100%, load1 86.91, workers 33, MemAvail 1238 GB | pending box1-eligible 1628 / server2-eligible 40841 (shared queues count in both; unleased, not DONE)
2026-11-18 14:55Z | box1: busy 99%, load1 38.64, workers 3, MemAvail 46 GB | server2: busy 100%, load1 97.95, workers 34, MemAvail 1290 GB | pending box1-eligible 1861 / server2-eligible 41074 (shared queues count in both; unleased, not DONE)
2026-11-18 15:00Z | box1: busy 99%, load1 38.57, workers 11, MemAvail 39 GB | server2: busy 100%, load1 90.34, workers 30, MemAvail 1317 GB | pending box1-eligible 1832 / server2-eligible 41045 (shared queues count in both; unleased, not DONE)
2026-11-18 15:05Z | box1: busy 100%, load1 38.42, workers 11, MemAvail 48 GB | server2: busy 100%, load1 88.79, workers 34, MemAvail 1256 GB | pending box1-eligible 1835 / server2-eligible 41048 (shared queues count in both; unleased, not DONE)
2026-11-18 15:10Z | box1: busy 100%, load1 41.14, workers 13, MemAvail 47 GB | server2: busy 100%, load1 88.40, workers 34, MemAvail 1260 GB | pending box1-eligible 2000 / server2-eligible 41213 (shared queues count in both; unleased, not DONE)
2026-11-18 15:15Z | box1: busy 100%, load1 40.93, workers 6, MemAvail 53 GB | server2: busy 100%, load1 93.88, workers 28, MemAvail 1316 GB | pending box1-eligible 1972 / server2-eligible 41185 (shared queues count in both; unleased, not DONE)
2026-11-18 15:20Z | box1: busy 100%, load1 43.13, workers 9, MemAvail 54 GB | server2: busy 100%, load1 85.73, workers 34, MemAvail 1333 GB | pending box1-eligible 1953 / server2-eligible 41166 (shared queues count in both; unleased, not DONE)
2026-11-18 15:25Z | box1: busy 100%, load1 41.80, workers 11, MemAvail 49 GB | server2: busy 100%, load1 86.75, workers 34, MemAvail 1305 GB | pending box1-eligible 1973 / server2-eligible 41186 (shared queues count in both; unleased, not DONE)
2026-11-18 15:30Z | box1: busy 100%, load1 42.17, workers 13, MemAvail 36 GB | server2: busy 100%, load1 92.14, workers 34, MemAvail 1218 GB | pending box1-eligible 1947 / server2-eligible 41160 (shared queues count in both; unleased, not DONE)
2026-11-18 15:35Z | box1: busy 100%, load1 41.79, workers 11, MemAvail 73 GB | server2: busy 100%, load1 93.82, workers 34, MemAvail 1166 GB | pending box1-eligible 1896 / server2-eligible 41109 (shared queues count in both; unleased, not DONE)
2026-11-18 15:40Z | box1: busy 100%, load1 40.65, workers 4, MemAvail 63 GB | server2: busy 100%, load1 88.56, workers 34, MemAvail 1230 GB | pending box1-eligible 1864 / server2-eligible 41077 (shared queues count in both; unleased, not DONE)
2026-11-18 15:45Z | box1: busy 100%, load1 39.77, workers 7, MemAvail 47 GB | server2: busy 100%, load1 88.50, workers 34, MemAvail 1258 GB | pending box1-eligible 2239 / server2-eligible 41452 (shared queues count in both; unleased, not DONE)
2026-11-18 15:50Z | box1: busy 100%, load1 37.64, workers 11, MemAvail 41 GB | server2: busy 100%, load1 89.08, workers 33, MemAvail 1278 GB | pending box1-eligible 2197 / server2-eligible 41530 (shared queues count in both; unleased, not DONE)
2026-11-18 15:55Z | box1: busy 100%, load1 38.22, workers 6, MemAvail 44 GB | server2: busy 100%, load1 84.80, workers 34, MemAvail 1344 GB | pending box1-eligible 2268 / server2-eligible 41481 (shared queues count in both; unleased, not DONE)
2026-11-18 16:00Z | box1: busy 100%, load1 46.21, workers 14, MemAvail 44 GB | server2: busy 100%, load1 82.57, workers 34, MemAvail 1360 GB | pending box1-eligible 2285 / server2-eligible 41498 (shared queues count in both; unleased, not DONE)
2026-11-18 16:05Z | box1: busy 100%, load1 37.43, workers 7, MemAvail 60 GB | server2: busy 100%, load1 81.97, workers 33, MemAvail 1373 GB | pending box1-eligible 2241 / server2-eligible 41454 (shared queues count in both; unleased, not DONE)
2026-11-18 16:10Z | box1: busy 100%, load1 42.52, workers 10, MemAvail 45 GB | server2: busy 100%, load1 81.69, workers 34, MemAvail 1375 GB | pending box1-eligible 2764 / server2-eligible 41977 (shared queues count in both; unleased, not DONE)
2026-11-18 16:15Z | box1: busy 100%, load1 44.66, workers 14, MemAvail 41 GB | server2: busy 100%, load1 82.22, workers 34, MemAvail 1379 GB | pending box1-eligible 2700 / server2-eligible 41913 (shared queues count in both; unleased, not DONE)
2026-11-18 16:20Z | box1: busy 100%, load1 40.79, workers 10, MemAvail 48 GB | server2: busy 100%, load1 82.30, workers 34, MemAvail 1384 GB | pending box1-eligible 2675 / server2-eligible 41888 (shared queues count in both; unleased, not DONE)
2026-11-18 16:25Z | box1: busy 100%, load1 44.49, workers 20, MemAvail 68 GB | server2: busy 100%, load1 81.63, workers 33, MemAvail 1386 GB | pending box1-eligible 2594 / server2-eligible 41807 (shared queues count in both; unleased, not DONE)
2026-11-18 16:30Z | box1: busy 100%, load1 43.47, workers 15, MemAvail 70 GB | server2: busy 100%, load1 91.73, workers 33, MemAvail 1288 GB | pending box1-eligible 2532 / server2-eligible 41745 (shared queues count in both; unleased, not DONE)
2026-11-18 16:35Z | box1: busy 100%, load1 43.47, workers 8, MemAvail 76 GB | server2: busy 100%, load1 94.91, workers 34, MemAvail 1229 GB | pending box1-eligible 2463 / server2-eligible 41676 (shared queues count in both; unleased, not DONE)
2026-11-18 16:40Z | box1: busy 100%, load1 46.84, workers 17, MemAvail 67 GB | server2: busy 100%, load1 91.90, workers 31, MemAvail 1262 GB | pending box1-eligible 2467 / server2-eligible 41680 (shared queues count in both; unleased, not DONE)
2026-11-18 16:45Z | box1: busy 100%, load1 39.86, workers 10, MemAvail 83 GB | server2: busy 100%, load1 86.15, workers 34, MemAvail 1245 GB | pending box1-eligible 2440 / server2-eligible 41653 (shared queues count in both; unleased, not DONE)
2026-11-18 16:50Z | box1: busy 100%, load1 39.41, workers 12, MemAvail 76 GB | server2: busy 100%, load1 85.89, workers 34, MemAvail 1349 GB | pending box1-eligible 2403 / server2-eligible 41616 (shared queues count in both; unleased, not DONE)
2026-11-18 16:55Z | box1: busy 100%, load1 48.38, workers 14, MemAvail 69 GB | server2: busy 100%, load1 80.49, workers 34, MemAvail 1372 GB | pending box1-eligible 2342 / server2-eligible 41554 (shared queues count in both; unleased, not DONE)
2026-11-18 17:00Z | box1: busy 100%, load1 39.48, workers 12, MemAvail 51 GB | server2: busy 100%, load1 81.54, workers 34, MemAvail 1325 GB | pending box1-eligible 2284 / server2-eligible 41497 (shared queues count in both; unleased, not DONE)
2026-11-18 17:05Z | box1: busy 100%, load1 38.30, workers 10, MemAvail 39 GB | server2: busy 100%, load1 81.49, workers 33, MemAvail 1324 GB | pending box1-eligible 2229 / server2-eligible 41442 (shared queues count in both; unleased, not DONE)
2026-11-18 17:10Z | box1: busy 100%, load1 40.97, workers 11, MemAvail 42 GB | server2: busy 100%, load1 80.12, workers 34, MemAvail 1353 GB | pending box1-eligible 2198 / server2-eligible 41411 (shared queues count in both; unleased, not DONE)
2026-11-18 17:15Z | box1: busy 100%, load1 42.79, workers 11, MemAvail 48 GB | server2: busy 100%, load1 80.98, workers 32, MemAvail 1359 GB | pending box1-eligible 2159 / server2-eligible 41371 (shared queues count in both; unleased, not DONE)
2026-11-18 17:20Z | box1: busy 100%, load1 46.37, workers 12, MemAvail 42 GB | server2: busy 100%, load1 66.48, workers 16, MemAvail 1365 GB | pending box1-eligible 2192 / server2-eligible 41405 (shared queues count in both; unleased, not DONE)
2026-11-18 17:25Z | box1: busy 100%, load1 39.73, workers 10, MemAvail 36 GB | server2: busy 100%, load1 92.78, workers 13, MemAvail 1385 GB | pending box1-eligible 2163 / server2-eligible 41376 (shared queues count in both; unleased, not DONE)
2026-11-18 17:30Z | box1: busy 100%, load1 49.50, workers 16, MemAvail 45 GB | server2: busy 100%, load1 118.05, workers 14, MemAvail 1290 GB | pending box1-eligible 2139 / server2-eligible 41352 (shared queues count in both; unleased, not DONE)
2026-11-18 17:35Z | box1: busy 100%, load1 43.82, workers 12, MemAvail 45 GB | server2: busy 100%, load1 105.28, workers 14, MemAvail 1236 GB | pending box1-eligible 2110 / server2-eligible 41323 (shared queues count in both; unleased, not DONE)
2026-11-18 17:40Z | box1: busy 100%, load1 37.59, workers 8, MemAvail 50 GB | server2: busy 100%, load1 101.11, workers 14, MemAvail 1202 GB | pending box1-eligible 2083 / server2-eligible 41296 (shared queues count in both; unleased, not DONE)
2026-11-18 17:45Z | box1: busy 100%, load1 45.45, workers 11, MemAvail 42 GB | server2: busy 100%, load1 100.28, workers 14, MemAvail 1156 GB | pending box1-eligible 2053 / server2-eligible 41266 (shared queues count in both; unleased, not DONE)
2026-11-18 17:50Z | box1: busy 100%, load1 42.89, workers 11, MemAvail 54 GB | server2: busy 100%, load1 97.70, workers 13, MemAvail 1194 GB | pending box1-eligible 2029 / server2-eligible 41242 (shared queues count in both; unleased, not DONE)
2026-11-18 17:55Z | box1: busy 100%, load1 41.65, workers 12, MemAvail 53 GB | server2: busy 100%, load1 100.97, workers 14, MemAvail 1196 GB | pending box1-eligible 2001 / server2-eligible 41214 (shared queues count in both; unleased, not DONE)
2026-11-18 18:00Z | box1: busy 100%, load1 41.50, workers 9, MemAvail 54 GB | server2: busy 100%, load1 98.09, workers 13, MemAvail 1279 GB | pending box1-eligible 1972 / server2-eligible 41185 (shared queues count in both; unleased, not DONE)
2026-11-18 18:05Z | box1: busy 100%, load1 44.16, workers 11, MemAvail 48 GB | server2: busy 100%, load1 93.16, workers 13, MemAvail 1303 GB | pending box1-eligible 1947 / server2-eligible 41160 (shared queues count in both; unleased, not DONE)
2026-11-18 18:10Z | box1: busy 100%, load1 41.13, workers 10, MemAvail 48 GB | server2: busy 100%, load1 91.60, workers 12, MemAvail 1301 GB | pending box1-eligible 1920 / server2-eligible 41133 (shared queues count in both; unleased, not DONE)
2026-11-18 18:15Z | box1: busy 100%, load1 49.71, workers 12, MemAvail 61 GB | server2: busy 100%, load1 91.82, workers 13, MemAvail 1284 GB | pending box1-eligible 1894 / server2-eligible 41107 (shared queues count in both; unleased, not DONE)
2026-11-18 18:20Z | box1: busy 100%, load1 42.79, workers 10, MemAvail 45 GB | server2: busy 100%, load1 92.05, workers 14, MemAvail 1272 GB | pending box1-eligible 1866 / server2-eligible 41079 (shared queues count in both; unleased, not DONE)
2026-11-18 18:25Z | box1: busy 100%, load1 52.78, workers 9, MemAvail 41 GB | server2: busy 100%, load1 92.66, workers 14, MemAvail 1274 GB | pending box1-eligible 1844 / server2-eligible 41057 (shared queues count in both; unleased, not DONE)
