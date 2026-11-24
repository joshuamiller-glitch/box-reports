# STATUS_NOW (written 2026-11-24 14:30Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-24 14:30Z | box1: busy 100%, load1 62.77, workers 19, MemAvail 54 GB | server2: busy 95%, load1 79.24, workers 28, MemAvail 1094 GB | pending box1-eligible 815373 / server2-eligible 20793 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 187.93, workers 105 (grid) + 98 (engine), 128 threads, MemAvail 1005 GB | serverB: busy 100%, load1 180.51, workers 105 (grid) + 102 (engine), 128 threads, MemAvail 952 GB | serverC: busy 100%, load1 136.09, workers 1 (grid) + 136 (engine), 128 threads, MemAvail 1403 GB | serverD: busy 99%, load1 63.40, workers 1 (grid) + 63 (engine), 64 threads, MemAvail 1450 GB

## UTC TIME WRITTEN
2026-11-24 14:30Z

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
Server 1 (this box): MemAvail 51.9 GB; live reservations 14 (14 GB); workers 19, of which TP-adopted 19 (RSS 24.6 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=24 LOAD_CAP=40 | load1/5/15: 62.77, 63.02, 64.80
  by tag: NYE quota 16 running 11 hungry False RSS 14.6 GB PSS 13.0 GB; LON quota 12 running 5 hungry True RSS 8.1 GB PSS 7.5 GB; TOOLS quota 0 running 3 hungry False RSS 2.0 GB PSS 1.6 GB
  cell-months finished last hour (DONE markers): 
  top running jobs: TL3_NYE_L934040dc_ALN (x30);TL3_SR_AS_STKd8da2eb47b_BF2_JT164 (x12);TL3_LON_M9cdef896_RM7 (x6);
Server 2 (rs4 metal): load / disk / tp_launch procs: 79.81, 82.50, 85.28|/dev/md2         28T  2.8T   26T  10% /mnt/l2|52|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261124_0250Z_Josh-depth-book-repeat-stops-skip-rule.md 20261124_0345Z_asia-step-a-counts-do-not-agree.md 20261124_0432Z_carryover-and-session-end-status.md 20261124_1316Z_Josh-deliver-asia-final-now.md 20261124_1320Z_asia-final-looks-stalled-30-sets-28-controls.md
