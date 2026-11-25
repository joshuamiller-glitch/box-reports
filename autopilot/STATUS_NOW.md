# STATUS_NOW (written 2026-11-25 11:15Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-25 11:15Z | box1: busy 99%, load1 67.15, workers 11, MemAvail 51 GB | server2: busy 98%, load1 85.27, workers 28, MemAvail 636 GB | pending box1-eligible 521079 / server2-eligible 38891 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 187.57, workers 105 (grid) + 101 (engine), 128 threads, MemAvail 952 GB | serverB: busy 100%, load1 177.91, workers 105 (grid) + 97 (engine), 128 threads, MemAvail 926 GB | serverC: busy 100%, load1 138.56, workers 1 (grid) + 140 (engine), 128 threads, MemAvail 1376 GB | serverD: busy 100%, load1 65.40, workers 1 (grid) + 61 (engine), 64 threads, MemAvail 1462 GB

## UTC TIME WRITTEN
2026-11-25 11:15Z

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
Server 1 (this box): MemAvail 50.4 GB; live reservations 13 (13 GB); workers 11, of which TP-adopted 11 (RSS 16.8 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=24 LOAD_CAP=40 | load1/5/15: 67.15, 64.16, 58.09
  by tag: NYR quota 12 running 10 hungry True RSS 14.9 GB PSS 12.1 GB; NYE quota 16 running 1 hungry False RSS 1.9 GB PSS 1.7 GB
  cell-months finished last hour (DONE markers): 
  top running jobs: TL3_NYE_La1b8f754_ALNCT56m (x12);TL3_NYE_La1b8f754_ALNCT63m (x10);TL3_SR_NY_STKd8w42_BF1_LOSSMF4_CX2 (x6);
Server 2 (rs4 metal): load / disk / tp_launch procs: 85.44, 87.31, 85.47|/dev/md2         28T  2.8T   26T  10% /mnt/l2|48|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261124_2214Z_Josh-restore-parked-weighted-nine-fit-rows.md 20261125_0140Z_Josh-NYAM-weighted-verdict-now.md 20261125_0215Z_nyam-jt91-coding-readings-to-confirm.md 20261125_0308Z_nyam-file-size-table-please.md 20261125_0848Z_nyam-new-member-Lca8ca9cb-spec-now.md
