# STATUS_NOW (written 2026-11-27 04:45Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-27 04:45Z | box1: busy 99%, load1 93.71, workers 14, MemAvail 41 GB | server2: busy 97%, load1 85.96, workers 28, MemAvail 854 GB | pending box1-eligible 506451 / server2-eligible 138903 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 172.22, workers 105 (grid) + 100 (engine), 128 threads, MemAvail 949 GB | serverB: busy 100%, load1 194.73, workers 105 (grid) + 101 (engine), 128 threads, MemAvail 901 GB | serverC: busy 100%, load1 204.52, workers 1 (grid) + 137 (engine), 128 threads, MemAvail 1323 GB | serverD: busy 95%, load1 61.09, workers 1 (grid) + 59 (engine), 64 threads, MemAvail 1454 GB

## UTC TIME WRITTEN
2026-11-27 04:45Z

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
Server 1 (this box): MemAvail 39.6 GB; live reservations 7 (7 GB); workers 14, of which TP-adopted 14 (RSS 19.1 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=24 LOAD_CAP=40 | load1/5/15: 93.71, 93.42, 90.54
  by tag: NYR quota 12 running 14 hungry False RSS 19.1 GB PSS 16.2 GB
  cell-months finished last hour (DONE markers): 
  top running jobs: TL3_NYE_La8473645_ALNCT77m (x10);TL3_NYE_La8473645_ALNCT70m (x8);TL3_NYE_L2935a58f_ALNCT63p (x1);
Server 2 (rs4 metal): load / disk / tp_launch procs: 87.08, 87.16, 87.04|/dev/md2         28T  2.8T   26T  10% /mnt/l2|54|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261127_0340Z_Josh-exits-inputs-must-update-INSIDE-the-trade.md 20261127_0343Z_Josh-exits-also-judge-fixed-rules-straight-no-refit.md 20261127_0349Z_Josh-ORDER-realtime-exit-for-ALL-books-do-not-stop.md 20261127_0353Z_Josh-exits-X24-evidence-driven-moving-targets-and-adaptive-trail.md 20261127_0354Z_Josh-exit-engine-must-behave-like-an-algo.md
