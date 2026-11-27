# STATUS_NOW (written 2026-11-27 20:30Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-27 20:30Z | box1: busy 99%, load1 52.37, workers 12, MemAvail 69 GB | server2: busy 97%, load1 85.04, workers 24, MemAvail 581 GB | pending box1-eligible 500819 / server2-eligible 82444 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 193.40, workers 105 (grid) + 100 (engine), 128 threads, MemAvail 895 GB | serverB: busy 99%, load1 177.24, workers 105 (grid) + 91 (engine), 128 threads, MemAvail 917 GB | serverC: busy 100%, load1 232.93, workers 1 (grid) + 140 (engine), 128 threads, MemAvail 834 GB | serverD: busy 100%, load1 97.90, workers 1 (grid) + 101 (engine), 64 threads, MemAvail 1467 GB

## UTC TIME WRITTEN
2026-11-27 20:30Z

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
Server 1 (this box): MemAvail 67.8 GB; live reservations 1 (1 GB); workers 12, of which TP-adopted 12 (RSS 17.8 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=24 LOAD_CAP=40 | load1/5/15: 54.74, 60.28, 63.14
  by tag: NYR quota 12 running 12 hungry False RSS 17.8 GB PSS 14.7 GB
  cell-months finished last hour (DONE markers): 
  top running jobs: TL3_NYE_L33285244_ALNCT28p (x12);TL3_NYE_L33285244_ALNCT21p (x8);TL3_NYE_L33285244_ALNCT35p (x6);
Server 2 (rs4 metal): load / disk / tp_launch procs: 85.45, 85.66, 85.05|/dev/md2         28T  2.8T   26T  11% /mnt/l2|42|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261127_1850Z_Josh-prepare-the-data-shopping-list-estimate-no-spend.md 20261127_1913Z_Josh-does-an-existing-authority-cover-the-small-data-items.md 20261127_1940Z_Josh-restore-loss-side-rows-and-mix-level-price.md 20261127_2016Z_Josh-on-the-data-authority-his-words.md 20261127_2030Z_Josh-desk-manager-v0_2.md
