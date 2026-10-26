2026-10-22T21:25:16Z trackDS300 started: PREREG frozen; building ds300lib/feature builders; block order F,E,C,B,G,H,J,I,A,D,M,K,L,N; workers 1 (<=8 allowed, nice 5)
2026-10-22T21:27:26Z block F: 38 cells scored in 3s (8 workers); gate a passers 4, a+b 2
2026-10-22T21:31:22Z block F DONE: nulls on 17 cells x 100 reps x 2 types in 239s total
2026-10-22T21:32:25Z block E: 40 cells scored in 3s (8 workers); gate a passers 15, a+b 7
2026-10-22T21:36:17Z block E DONE: nulls on 20 cells x 100 reps x 2 types in 235s total
2026-10-22T21:37:44Z block C: 68 cells scored in 21s (8 workers); gate a passers 5, a+b 1
2026-10-22T21:42:11Z block C DONE: nulls on 5 cells x 100 reps x 2 types in 287s total
2026-10-22T21:42:48Z block B: 22 cells scored in 2s (8 workers); gate a passers 4, a+b 4
2026-10-22T21:44:09Z block B DONE: nulls on 15 cells x 100 reps x 2 types in 83s total
2026-10-22T21:45:16Z trackDS300 blocks F,E,C,B done (nulls included); G,H,J,I running; next A,D,M,K,L,N; workers 8 nice 5; ETA all blocks ~3-4 h
2026-10-22T21:45:16Z block H: 37 cells scored in 2s (8 workers); gate a passers 6, a+b 3
2026-10-22T21:47:03Z block H DONE: nulls on 13 cells x 100 reps x 2 types in 108s total
2026-10-22T21:47:35Z block J: 9 cells scored in 1s (8 workers); gate a passers 1, a+b 0
2026-10-22T21:48:12Z block J DONE: nulls on 5 cells x 100 reps x 2 types in 38s total
2026-10-22T21:48:50Z block I: 35 cells scored in 2s (8 workers); gate a passers 10, a+b 3
2026-10-22T21:51:02Z block I DONE: nulls on 16 cells x 100 reps x 2 types in 134s total
2026-10-22T21:51:37Z block G: 16 cells scored in 2s (8 workers); gate a passers 4, a+b 0
2026-10-22T21:52:45Z block G DONE: nulls on 11 cells x 100 reps x 2 types in 71s total
2026-10-22T21:53:00Z blocks G,H,I,J done; A,K-prep(kfeat/lstate) running (8 workers)
2026-10-22T21:59:40Z block A: 33 cells scored in 6s (6 workers); gate a passers 2, a+b 0
2026-10-22T22:00:21Z block A DONE: nulls on 2 cells x 100 reps x 2 types in 47s total
2026-10-22T22:01:03Z block D: 25 cells scored in 10s (7 workers); gate a passers 5, a+b 3
2026-10-22T22:01:03Z block D DONE: nulls on 0 cells x 100 reps x 2 types in 10s total
2026-10-22T22:01:33Z block M: 4 cells scored in 1s (8 workers); gate a passers 2, a+b 0
2026-10-22T22:01:56Z block M DONE: nulls on 3 cells x 100 reps x 2 types in 24s total
2026-10-22T22:01:59Z block A,D done; M,K,L,I10 queued (lstate rerun for L11)
2026-10-22T22:02:26Z block B12: 2 cells scored in 1s (8 workers); gate a passers 0, a+b 0
2026-10-22T22:02:27Z block B12 DONE: nulls on 1 cells x 100 reps x 2 types in 2s total
2026-10-22T22:02:30Z block K: 40 cells scored in 3s (8 workers); gate a passers 8, a+b 3
2026-10-22T22:03:42Z block B12x: 2 cells scored in 0s (4 workers); gate a passers 0, a+b 0
2026-10-22T22:03:57Z block B12x DONE: nulls on 1 cells x 100 reps x 2 types in 15s total
2026-10-22T22:04:17Z block K DONE: nulls on 14 cells x 100 reps x 2 types in 110s total
2026-10-22T22:04:33Z blocks M,K done; L and I10 running; then O-battery + report
2026-10-22T22:05:14Z block L: 20 cells scored in 1s (8 workers); gate a passers 4, a+b 0
2026-10-22T22:06:47Z block L DONE: nulls on 13 cells x 100 reps x 2 types in 94s total
2026-10-22T22:07:17Z block I10: 3 cells scored in 1s (8 workers); gate a passers 0, a+b 0
2026-10-22T22:07:27Z block I10 DONE: nulls on 1 cells x 100 reps x 2 types in 10s total
2026-10-22T22:07:49Z all blocks scored (A-N except N execution replay; L13 GA & M19 report pending). Running O-battery + report; N block (sample-month L2 replay) waits for trackFIRM V6 (memory)
2026-10-22T22:10:56Z trackDS300: V6 done (REPORT_DS2_FIRM_V6.md present, no firm_replay running) -> direct L2 replay of regenerated a+b cells (C13 ST60-HM40, D9, D15, D16) on L8W months 2026-08/09/10, 6 workers ~15 GB each nice 10 (B14 limit entry not replayable)
2026-10-22T22:13:25Z trackDS300 STATUS: blocks F,E,C,B,G,H,J,I,A,D,M,K,L + I10/B12x scored (419 cells, nulls done): a-passers 71, a+b 27, a+b+c 0, a-d 0 (FOUND 0). Closest: L5 Bayesian-shrinkage size-8 (gate a,c,d pass; fails b - never fires in L8W, gain only in 2024-02..2025-04). Running: 12 direct L2 replays (6 workers ~15GB, nice 10) of C13 ST60-HM40/D9/D15/D16 on 2026-08..10; O reruns (1 worker). Block N sample-replay NOT RUN (see Q15). Next: report REPORT_DS2_300.md final in ~40 min. Workers now 7.
2026-10-22T23:25:42Z trackDS300 DONE (except block N execution variants, NOT RUN): REPORT_DS2_300.md written; 419 scored cells, 0 gate a-d passers; replay workers finished, 0 workers running.
2026-10-22T23:31:43Z trackDS300 Block N: 18 months paired replay launched, 9 workers nice 5
2026-10-23T00:13:00Z trackDS300 Block N interim: 5 of 18 months replayed (wave 1), appended to REPORT sec 7; 8 workers continue (nice 5, MemAvailable>=70 gate); final rescore when more months land
2026-10-23T01:29:08Z Block N DONE, 0 workers
