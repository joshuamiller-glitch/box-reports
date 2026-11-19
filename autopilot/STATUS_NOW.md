# STATUS_NOW (written 2026-11-19 14:15Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-19 14:15Z | box1: busy 100%, load1 89.68, workers 32, MemAvail 51 GB | server2: busy 100%, load1 125.32, workers 25, MemAvail 968 GB | pending box1-eligible 64564 / server2-eligible 73992 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 173.91, workers 105 (grid) + 102 (engine), 128 threads, MemAvail 1269 GB | serverB: busy 100%, load1 145.94, workers 105 (grid) + 0 (engine), 128 threads, MemAvail 1234 GB

## UTC TIME WRITTEN
2026-11-19 14:15Z

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
Server 1 (this box): MemAvail 50.4 GB; live reservations 1 (1 GB); workers 32, of which TP-adopted 31 (RSS 52.6 GB) vs others 1 (RSS 1.0 GB)
  caps: WORKER_CAP=36 LOAD_CAP=40 | load1/5/15: 89.68, 88.00, 83.04
  by tag: ASI quota 16 running 15 hungry True RSS 27.2 GB PSS 21.6 GB; NYL quota 36 running 7 hungry True RSS 12.5 GB PSS 9.3 GB; NYR quota 11 running 4 hungry True RSS 6.0 GB PSS 5.5 GB; LON quota 12 running 2 hungry True RSS 2.5 GB PSS 2.0 GB; TOOLS quota 0 running 3 hungry False RSS 4.5 GB PSS 3.5 GB; REST quota 0 running 1 hungry False RSS 1.0 GB PSS 0.8 GB
  cell-months finished last hour (DONE markers): 3067
  top running jobs: TL3_ASI_L5c9e11b3_RA7CT35p (x8);TL3_CMB_DRY1 (x6);TL3_NYE_L3701b464_RK7 (x4);
Server 2 (rs4 metal): load / disk / tp_launch procs: 125.23, 119.32, 124.64|/dev/md2         28T  2.0T   26T   8% /mnt/l2|44|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261119_1233Z_Fast-share-dropped-calibration-cores.md 20261119_1324Z_Josh-decisions-persistence-058-addons.md 20261119_1337Z_Josh-finish-everything-before-build-go-faster.md 20261119_1407Z_Josh-REPLACE-ONLY.md 20261119_1410Z_Josh-combination-stage.md
