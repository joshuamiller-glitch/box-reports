# STATUS_NOW (written 2026-11-28 03:30Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-28 03:30Z | box1: busy 91%, load1 25.79, workers 13, MemAvail 80 GB | server2: busy 98%, load1 87.04, workers 28, MemAvail 643 GB | pending box1-eligible 497893 / server2-eligible 51485 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 187.67, workers 105 (grid) + 99 (engine), 128 threads, MemAvail 848 GB | serverB: busy 100%, load1 198.26, workers 105 (grid) + 98 (engine), 128 threads, MemAvail 782 GB | serverC: busy 100%, load1 161.44, workers 1 (grid) + 138 (engine), 128 threads, MemAvail 1237 GB | serverD: busy 100%, load1 178.17, workers 1 (grid) + 147 (engine), 64 threads, MemAvail 1224 GB

## UTC TIME WRITTEN
2026-11-28 03:30Z

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
Server 1 (this box): MemAvail 79.7 GB; live reservations 2 (2 GB); workers 13, of which TP-adopted 13 (RSS 16.9 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=24 LOAD_CAP=40 | load1/5/15: 25.79, 39.52, 50.60
  by tag: NYE quota 16 running 13 hungry False RSS 16.9 GB PSS 15.4 GB
  cell-months finished last hour (DONE markers): 
  top running jobs: TL3_NYE_Lc7e92730_ALN (x29);TL3_NYE_L71ad6c47_ALN (x1);
Server 2 (rs4 metal): load / disk / tp_launch procs: 87.73, 85.76, 83.91|/dev/md2         28T  2.8T   26T  11% /mnt/l2|48|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261127_2342Z_Josh-desk-v0_2_2-relay-decisions-on-the-four-defects.md 20261127_2359Z_Josh-hourly-line-overdue.md 20261128_0110Z_Josh-match-csvs-as-md-pages.md 20261128_0240Z_Josh-read-the-desk-scorecard-on-the-runnable-window-now.md 20261128_0322Z_Josh-desk-v0_2_2-failed-attribution-then-v0_3.md
