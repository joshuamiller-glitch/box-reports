# STATUS_NOW (written 2026-11-23 18:15Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-23 18:15Z | box1: busy 100%, load1 79.38, workers 22, MemAvail 64 GB | server2: busy 97%, load1 86.21, workers 26, MemAvail 857 GB | pending box1-eligible 940919 / server2-eligible 124167 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 157.36, workers 105 (grid) + 102 (engine), 128 threads, MemAvail 990 GB | serverB: busy 100%, load1 186.43, workers 105 (grid) + 99 (engine), 128 threads, MemAvail 950 GB | serverC: busy 99%, load1 136.48, workers 1 (grid) + 138 (engine), 128 threads, MemAvail 1364 GB | serverD: busy 96%, load1 64.27, workers 1 (grid) + 67 (engine), 64 threads, MemAvail 1434 GB

## UTC TIME WRITTEN
2026-11-23 18:15Z

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
Server 1 (this box): MemAvail 63.0 GB; live reservations 5 (5 GB); workers 22, of which TP-adopted 21 (RSS 26.8 GB) vs others 1 (RSS 1.2 GB)
  caps: WORKER_CAP=24 LOAD_CAP=40 | load1/5/15: 86.80, 79.17, 72.82
  by tag: NYR quota 12 running 14 hungry False RSS 18.2 GB PSS 15.2 GB; TOOLS quota 0 running 7 hungry False RSS 8.6 GB PSS 7.8 GB; REST quota 0 running 1 hungry False RSS 1.2 GB PSS 1.1 GB
  cell-months finished last hour (DONE markers): 
  top running jobs: TL3_NYE_L651b760c_ALNCT14p (x12);TL3_NYE_L651b760c_ALNCT7p (x10);TL3_NYE_L651b760c_ALNCT21p (x10);
Server 2 (rs4 metal): load / disk / tp_launch procs: 84.03, 86.03, 85.87|/dev/md2         28T  2.8T   26T  10% /mnt/l2|52|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261123_1725Z_Josh-carry-over-first-and-fitted-combined.md 20261123_1840Z_Josh-fit-at-two-lots-only.md 20261123_1745Z_nypm-volume-book-inputs-for-the-port.md 20261123_1750Z_Josh-time-window-blocks-all-30min.md 20261123_1810Z_Josh-nypm-fit-first-and-keys-at-once.md
