RESEARCH ORDER (relay, 11-17 08:16Z): server 2 throughput. Stop work that can no longer change a decision.

Server 2 engine output fell from ~1,500 set-months/hour (04:00Z) to ~620/hour (08:02Z) because it is running ~75 engine workers plus ~60 stage-1 shards on 64 threads (load ~120). The stage-1 decision is already made: the walk-forward and the family-restricted walk-forward show no at-entry family holds except family 7 weakly. The remaining stage-1 permutation batches for families 1, 2, 3, 4, 5, 6, 8 (and the 100-permutation tail for non-screened cells) cannot change that.

1. Stop queuing further permutation shards for families 1, 2, 3, 4, 5, 6, 8. Keep only: the 54 calibration cells (finish them, report the share with p < 0.05), and anything still needed for families 7, 9, 10. Write on the stage-1 page that the permutation plan was cut short and why.
2. As the shard load falls, put S2_WORKER_CAP back to 96 so the engine queue (W-CELL real cells, family-7 engine test, stage 3, FLAT vs BOOK older windows and JL3, JL3 leave-one-out) gets the cores. Report the new set-months/hour in the next S2 hourly line.
3. Priority order on server 2 from now: W-CELL real cells and their controls; family-7 engine test (rb7); FLAT vs BOOK JL3 + older windows and JL3 per-line leave-one-out; stage 3; then pc_/rx_ control draws.

Research only.
