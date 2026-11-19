# STATUS_NOW (written 2026-11-19 20:00Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-19 20:00Z | box1: busy 100%, load1 69.83, workers 17, MemAvail 48 GB | server2: busy 100%, load1 136.13, workers 28, MemAvail 1093 GB | pending box1-eligible 51372 / server2-eligible 57666 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 234.29, workers 105 (grid) + 101 (engine), 128 threads, MemAvail 1101 GB | serverB: busy 100%, load1 218.10, workers 105 (grid) + 101 (engine), 128 threads, MemAvail 909 GB

## UTC TIME WRITTEN
2026-11-19 20:00Z

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
Server 1 (this box): MemAvail 47.2 GB; live reservations 10 (10 GB); workers 17, of which TP-adopted 17 (RSS 25.4 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=36 LOAD_CAP=40 | load1/5/15: 69.83, 69.14, 76.70
  by tag: NYR quota 12 running 8 hungry True RSS 11.3 GB PSS 8.8 GB; ASI quota 14 running 3 hungry True RSS 4.1 GB PSS 3.6 GB; EXE quota 2 running 3 hungry False RSS 5.8 GB PSS 4.1 GB; NYL quota 5 running 2 hungry True RSS 2.7 GB PSS 2.3 GB; LON quota 12 running 1 hungry True RSS 1.5 GB PSS 1.0 GB
  cell-months finished last hour (DONE markers): 5408
  top running jobs: TL3_NYE_L21f079b6_RK7CT35m (x10);TL3_NYE_L21f079b6_RK7CT42m (x8);TL3_NYL_Ldcdb0b6exA7_DD15 (x2);
Server 2 (rs4 metal): load / disk / tp_launch procs: 135.37, 139.71, 141.21|/dev/md2         28T  2.3T   26T   9% /mnt/l2|56|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261119_1806Z_Josh-best-books-on-own-merit-not-vs-D7.md 20261119_1823Z_STATUS-QUESTION-coverage-by-component.md 20261119_1850Z_PASS-2-plan-prepare-now-start-when-first-looks-finish.md 20261119_1917Z_cold-archive-move-yes.md 20261119_1933Z_fast-share-stack-kinds.md
