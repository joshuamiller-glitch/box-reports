# STATUS_NOW (written 2026-11-27 19:15Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-27 19:15Z | box1: busy 100%, load1 63.28, workers 9, MemAvail 69 GB | server2: busy 95%, load1 75.80, workers 27, MemAvail 1046 GB | pending box1-eligible 501319 / server2-eligible 90960 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 209.25, workers 105 (grid) + 100 (engine), 128 threads, MemAvail 806 GB | serverB: busy 100%, load1 203.17, workers 105 (grid) + 102 (engine), 128 threads, MemAvail 798 GB | serverC: busy 100%, load1 256.08, workers 1 (grid) + 138 (engine), 128 threads, MemAvail 744 GB | serverD: busy 100%, load1 102.71, workers 1 (grid) + 108 (engine), 64 threads, MemAvail 1458 GB

## UTC TIME WRITTEN
2026-11-27 19:15Z

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
Server 1 (this box): MemAvail 68.1 GB; live reservations 1 (1 GB); workers 9, of which TP-adopted 9 (RSS 12.9 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=24 LOAD_CAP=40 | load1/5/15: 63.28, 62.65, 58.63
  by tag: NYR quota 12 running 9 hungry True RSS 12.9 GB PSS 11.4 GB
  cell-months finished last hour (DONE markers): 
  top running jobs: TL3_NYE_L02b4fc0b_ALNCT21m (x12);TL3_NYE_L02b4fc0b_ALNCT14m (x12);TL3_NYE_L02b4fc0b_ALNCT7m (x4);
Server 2 (rs4 metal): load / disk / tp_launch procs: 77.48, 82.34, 89.21|/dev/md2         28T  2.8T   26T  11% /mnt/l2|54|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261127_1747Z_Josh-not-a-search-a-human-style-manager-on-proven-books.md 20261127_1754Z_Josh-what-moves-NQ-and-what-moves-before-NQ.md 20261127_1826Z_Josh-serverD-idle-fill-it.md 20261127_1850Z_Josh-prepare-the-data-shopping-list-estimate-no-spend.md 20261127_1913Z_Josh-does-an-existing-authority-cover-the-small-data-items.md
