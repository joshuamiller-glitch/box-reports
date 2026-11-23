# STATUS_NOW (written 2026-11-23 15:00Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-23 15:00Z | box1: busy 99%, load1 66.48, workers 17, MemAvail 69 GB | server2: busy 98%, load1 87.26, workers 25, MemAvail 593 GB | pending box1-eligible 954707 / server2-eligible 136834 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 185.32, workers 105 (grid) + 99 (engine), 128 threads, MemAvail 1008 GB | serverB: busy 99%, load1 164.94, workers 105 (grid) + 90 (engine), 128 threads, MemAvail 984 GB | serverC: busy 96%, load1 134.80, workers 1 (grid) + 138 (engine), 128 threads, MemAvail 1374 GB | serverD: busy 96%, load1 59.21, workers 1 (grid) + 64 (engine), 64 threads, MemAvail 1439 GB

## UTC TIME WRITTEN
2026-11-23 15:00Z

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
Server 1 (this box): MemAvail 68.3 GB; live reservations 4 (4 GB); workers 17, of which TP-adopted 16 (RSS 21.2 GB) vs others 1 (RSS 1.2 GB)
  caps: WORKER_CAP=24 LOAD_CAP=40 | load1/5/15: 66.48, 62.61, 69.90
  by tag: NYR quota 12 running 1 hungry True RSS 1.6 GB PSS 1.4 GB; NYE quota 16 running 13 hungry False RSS 17.9 GB PSS 16.4 GB; TOOLS quota 0 running 2 hungry False RSS 1.7 GB PSS 1.5 GB; REST quota 0 running 1 hungry False RSS 1.2 GB PSS 1.1 GB
  cell-months finished last hour (DONE markers): 
  top running jobs: TL3_NYE_Ld7bd2998_ALN (x18);TL3_SR_NP_STKd893133bd8_BF2_DLB_DLB7 (x12);TL3_NYE_Ld300f2d3_ALN (x7);
Server 2 (rs4 metal): load / disk / tp_launch procs: 86.83, 86.60, 83.59|/dev/md2         28T  2.8T   26T  10% /mnt/l2|50|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261123_0640Z_Josh-asia-daily-loss-stop-test.md 20261123_0645Z_Josh-session-end-run-vs-flatten-test.md 20261123_0740Z_Josh-depth-book-lock-info.md 20261123_0745Z_Josh-all-session-combined-numbers.md 20261123_0750Z_Josh-cross-session-locks-test.md
