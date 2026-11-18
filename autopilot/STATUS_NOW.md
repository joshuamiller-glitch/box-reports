# STATUS_NOW (written 2026-11-18 20:45Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-18 20:45Z | box1: busy 100%, load1 67.81, workers 29, MemAvail 56 GB | server2: busy 100%, load1 106.95, workers 14, MemAvail 1045 GB | pending box1-eligible 1996 / server2-eligible 4172 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 174.89, workers 93 (grid) + 55 (engine), 128 threads, MemAvail 1369 GB | serverB: busy 100%, load1 178.62, workers 89 (grid) + 53 (engine), 128 threads, MemAvail 1289 GB

## UTC TIME WRITTEN
2026-11-18 20:45Z

## NEEDS HELP
- Server 2: identity PASSED; first real jobs finished 18:48Z (T-REBUILD stage 0 raw books, K7 202610 92 s); ramp to knee running (cap 16 now); copy ~150/305 GB.
- Per-second MBO tables for 2026-11-01..11-05 are missing (W-CF2 checking raw files / quote only).

## NEEDS THE USER
- DS7.cs LINE 1790 BUG (v2.0): persist counter cleared on every winning second: the K7/U7/M7 book-reading profit lines (persist >= 2) can never fire live. You said keep them inert until the engine says whether firing helps: the 21:00Z page gives both worlds. (One-line fix in autopilot/DS7_PROFIT_LINES_SPEC.md.)
- JL2 does NOT model the persist=1 profit lines that DO fire live: size (replay): mean -3%, whole-stack max DD -74.4k -> -79.6k (L6M -22.6k -> -29.5k); P7 hit most. So live is ~5k DD worse than JL2 from these lines: engine build JL3 queued (W-EV).

## PASSED SINCE LAST FILE
- none (no candidate has beaten all its persistent-draw controls yet)

## FAILED / WITHDRAWN SINCE LAST FILE
- London range skip (LS1/LS125): no HOLD DD cut at any k; old random controls invalid; Off/Shadow.
- Profit lines K7 lock / U7 tighten / M7 step: 43-month replay net negative and dead live by the line 1790 bug.

## EACH SERVER
Server 1 (this box): MemAvail 56.9 GB; live reservations 5 (5 GB); workers 29, of which TP-adopted 29 (RSS 48.4 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=32 LOAD_CAP=40 | load1/5/15: 68.38, 69.23, 64.76
  by tag: NT quota 8 running 7 hungry True RSS 12.9 GB PSS 12.0 GB; NYL quota 12 running 10 hungry True RSS 13.8 GB PSS 12.5 GB; LON quota 8 running 6 hungry True RSS 9.9 GB PSS 8.4 GB; ASI quota 8 running 6 hungry True RSS 11.8 GB PSS 10.3 GB; NT quota 0 running 7 hungry False RSS 12.9 GB PSS 12.0 GB
  cell-months finished last hour (DONE markers): 578
  top running jobs: TL3_NT_LK_K7_a80_L50 (x12);TL3_LON_LB5_ADD (x12);TL3_ASI_AB5_ADD (x12);
Server 2 (rs4 metal): load / disk / tp_launch procs: 108.01, 99.74, 93.52|/dev/md2         28T  1.4T   27T   5% /mnt/l2|24|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261118_1932Z_thousands-pass-order-the-tests-cheapest-first.md 20261118_2013Z_engine-queue-empty-what-to-run-now.md 20261118_2024Z_exits-on-everything-measure-first.md 20261118_2042Z_luck-testing-budget-per-cell-pvalues-not-20-full-nulls.md 20261118_2052Z_NIGHT-SAFETY-no-repeat-of-the-7-hour-stall.md
- lead 20:44Z INBOX 20261118_2052Z_NIGHT-SAFETY-no-repeat-of-the-7-hour-stall.md received (auto-ack by inbox_watch.sh; the lead reads it next and logs the actio
