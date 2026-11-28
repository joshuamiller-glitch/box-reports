# STATUS_NOW (written 2026-11-28 09:00Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-28 09:00Z | box1: busy 99%, load1 79.79, workers 10, MemAvail 36 GB | server2: busy 94%, load1 79.68, workers 26, MemAvail 1080 GB | pending box1-eligible 495900 / server2-eligible 2005 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 179.02, workers 105 (grid) + 100 (engine), 128 threads, MemAvail 942 GB | serverB: busy 100%, load1 184.08, workers 105 (grid) + 95 (engine), 128 threads, MemAvail 901 GB | serverC: busy 100%, load1 137.70, workers 1 (grid) + 137 (engine), 128 threads, MemAvail 1371 GB | serverD: busy 100%, load1 148.00, workers 1 (grid) + 147 (engine), 64 threads, MemAvail 1365 GB

## UTC TIME WRITTEN
2026-11-28 09:00Z

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
Server 1 (this box): MemAvail 34.7 GB; live reservations 6 (6 GB); workers 10, of which TP-adopted 10 (RSS 14.3 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=24 LOAD_CAP=40 | load1/5/15: 79.79, 63.49, 59.99
  by tag: NYE quota 16 running 10 hungry False RSS 14.3 GB PSS 13.1 GB
  cell-months finished last hour (DONE markers): 
  top running jobs: TL3_NYE_Lebd51a93_ALN (x10);TL3_NYE_L6e2dc8de_ALNCT14m (x1);
Server 2 (rs4 metal): load / disk / tp_launch procs: 79.31, 80.54, 83.99|/dev/md2         28T  2.8T   26T  10% /mnt/l2|56|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261128_0110Z_Josh-match-csvs-as-md-pages.md 20261128_0240Z_Josh-read-the-desk-scorecard-on-the-runnable-window-now.md 20261128_0322Z_Josh-desk-v0_2_2-failed-attribution-then-v0_3.md 20261128_0552Z_Josh-rerun-what-moves-NQ-on-the-new-1s-data.md 20261128_0655Z_Josh-landscape-codes-target-and-fill-questions.md
