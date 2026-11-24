# STATUS_NOW (written 2026-11-24 17:30Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-24 17:30Z | box1: busy 99%, load1 49.98, workers 14, MemAvail 65 GB | server2: busy 83%, load1 52.32, workers 0, MemAvail 965 GB | pending box1-eligible 809514 / server2-eligible 111 (shared queues count in both; unleased, not DONE) | serverA: busy 82%, load1 87.97, workers 105 (grid) + 0 (engine), 128 threads, MemAvail 1079 GB | serverB: busy 79%, load1 76.95, workers 105 (grid) + 0 (engine), 128 threads, MemAvail 1026 GB | serverC: busy 41%, load1 10.74, workers 1 (grid) + 36 (engine), 128 threads, MemAvail 1492 GB | serverD: busy 36%, load1 4.12, workers 1 (grid) + 0 (engine), 64 threads, MemAvail 1496 GB

## UTC TIME WRITTEN
2026-11-24 17:30Z

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
Server 1 (this box): MemAvail 63.5 GB; live reservations 2 (2 GB); workers 14, of which TP-adopted 14 (RSS 19.7 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=24 LOAD_CAP=40 | load1/5/15: 53.11, 53.78, 59.27
  by tag: NYR quota 12 running 14 hungry False RSS 19.7 GB PSS 16.0 GB
  cell-months finished last hour (DONE markers): 
  top running jobs: TL3_NYE_L672dd8a4_ALNCT7m (x12);TL3_NYE_L672dd8a4_ALNCT14m (x12);TL3_NYE_L672dd8a4_ALNCT21m (x4);
Server 2 (rs4 metal): load / disk / tp_launch procs: 52.05, 67.17, 77.69|/dev/md2         28T  2.8T   26T  10% /mnt/l2|0|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261124_0250Z_Josh-depth-book-repeat-stops-skip-rule.md 20261124_0345Z_asia-step-a-counts-do-not-agree.md 20261124_0432Z_carryover-and-session-end-status.md 20261124_1316Z_Josh-deliver-asia-final-now.md 20261124_1320Z_asia-final-looks-stalled-30-sets-28-controls.md
