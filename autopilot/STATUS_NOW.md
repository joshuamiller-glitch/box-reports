# STATUS_NOW (written 2026-11-23 11:15Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-23 11:15Z | box1: busy 99%, load1 48.63, workers 17, MemAvail 79 GB | server2: busy 97%, load1 87.93, workers 24, MemAvail 737 GB | pending box1-eligible 954739 / server2-eligible 140013 (shared queues count in both; unleased, not DONE) | serverA: busy 99%, load1 179.66, workers 105 (grid) + 100 (engine), 128 threads, MemAvail 1019 GB | serverB: busy 100%, load1 170.48, workers 105 (grid) + 95 (engine), 128 threads, MemAvail 994 GB | serverC: busy 82%, load1 119.49, workers 1 (grid) + 139 (engine), 128 threads, MemAvail 1377 GB | serverD: busy 86%, load1 56.38, workers 1 (grid) + 58 (engine), 64 threads, MemAvail 1468 GB

## UTC TIME WRITTEN
2026-11-23 11:15Z

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
Server 1 (this box): MemAvail 78.4 GB; live reservations 1 (1 GB); workers 17, of which TP-adopted 16 (RSS 22.4 GB) vs others 1 (RSS 1.2 GB)
  caps: WORKER_CAP=24 LOAD_CAP=40 | load1/5/15: 48.63, 64.40, 62.57
  by tag: NYR quota 12 running 13 hungry False RSS 18.9 GB PSS 15.6 GB; TOOLS quota 0 running 3 hungry False RSS 3.4 GB PSS 3.0 GB; REST quota 0 running 1 hungry False RSS 1.2 GB PSS 1.1 GB
  cell-months finished last hour (DONE markers): 9819
  top running jobs: TL3_NYE_L4666c5cb_RK7CT14m (x12);TL3_NYE_L4666c5cb_RK7CT7m (x8);TL3_NYE_L4666c5cb_RK7CT21m (x6);
Server 2 (rs4 metal): load / disk / tp_launch procs: 85.20, 85.70, 85.41|/dev/md2         28T  2.8T   26T  10% /mnt/l2|54|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261123_0640Z_Josh-asia-daily-loss-stop-test.md 20261123_0645Z_Josh-session-end-run-vs-flatten-test.md 20261123_0740Z_Josh-depth-book-lock-info.md 20261123_0745Z_Josh-all-session-combined-numbers.md 20261123_0750Z_Josh-cross-session-locks-test.md
