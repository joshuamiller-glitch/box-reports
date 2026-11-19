# STATUS_NOW (written 2026-11-19 18:15Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-19 18:15Z | box1: busy 100%, load1 88.12, workers 38, MemAvail 60 GB | server2: busy 100%, load1 139.21, workers 28, MemAvail 948 GB | pending box1-eligible 54936 / server2-eligible 57164 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 235.43, workers 105 (grid) + 96 (engine), 128 threads, MemAvail 1153 GB | serverB: busy 100%, load1 221.14, workers 105 (grid) + 101 (engine), 128 threads, MemAvail 1111 GB

## UTC TIME WRITTEN
2026-11-19 18:15Z

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
Server 1 (this box): MemAvail 59.9 GB; live reservations 0 (0 GB); workers 38, of which TP-adopted 38 (RSS 57.5 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=36 LOAD_CAP=40 | load1/5/15: 88.27, 85.86, 82.29
  by tag: ASI quota 14 running 5 hungry True RSS 8.7 GB PSS 7.9 GB; EXE quota 2 running 5 hungry False RSS 8.7 GB PSS 6.9 GB; TOOLS quota 0 running 28 hungry False RSS 40.1 GB PSS 34.1 G
  cell-months finished last hour (DONE markers): 4768
  top running jobs: TL3_STK_E_ASIA (x12);TL3_STK_N_L01_K7 (x10);TL3_STK_N_L01 (x10);
Server 2 (rs4 metal): load / disk / tp_launch procs: 139.97, 139.77, 140.46|/dev/md2         28T  2.2T   26T   8% /mnt/l2|46|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261119_1439Z_URGENT-Singapore-engine-zero.md 20261119_1457Z_Fleet-rate-halved-why.md 20261119_1534Z_Fast-share-zero-first-looks-share-exit-driver.md 20261119_1750Z_Rate-dip-exit-families-base-lots.md 20261119_1806Z_Josh-best-books-on-own-merit-not-vs-D7.md
