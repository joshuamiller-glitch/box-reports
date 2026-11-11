# ORDER (user, 2026-11-11 21:20Z) — THROUGHPUT
The box is RAM-bound (187 GB, ~12 exact workers at 6-14 GB, CPU 25-40%), with 1,500+ exact jobs queued. One agent, 2 h, without touching results:
1. Profile one exact month-run: what holds the memory (1-s state arrays, print tape, trade lists, per-set copies?). Report GB by object.
2. Cut it: load the month's state arrays ONCE as read-only shared memory / np.memmap files that every worker maps (no per-process copy); load only the columns and sessions a set needs; free the tape after the trade list is built; float32 where float64 is not needed for prices at tick precision (prove bit-identical trade lists on 202610 and 202608 before switching anything).
3. Target: <= 2.5 GB private memory per worker so 28-30 workers run under the 40 GB guard. Identity test (trade-for-trade vs the current engine on two months, all four bases) is the gate; if it fails, revert and report.
4. Then re-order the queue: P7 FIX and its joint stage, T-NEAR-ZONE exact, T-EARLY-CUT exact, T-WORKS JN05, then the rest. Report jobs/hour before and after in MORNING.md.
If RAM is still the limit after this, quote in MORNING.md what a second box or a RAM upgrade at the host costs per month — do not buy.
