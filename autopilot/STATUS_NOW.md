# STATUS_NOW (written 2026-11-26 02:15Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-26 02:15Z | box1: busy 100%, load1 66.25, workers 13, MemAvail 59 GB | server2: busy 98%, load1 88.61, workers 28, MemAvail 561 GB | pending box1-eligible 514244 / server2-eligible 4907 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 185.75, workers 105 (grid) + 102 (engine), 128 threads, MemAvail 898 GB | serverB: busy 100%, load1 181.94, workers 105 (grid) + 101 (engine), 128 threads, MemAvail 862 GB | serverC: busy 100%, load1 139.02, workers 1 (grid) + 140 (engine), 128 threads, MemAvail 1312 GB | serverD: busy 99%, load1 65.82, workers 1 (grid) + 63 (engine), 64 threads, MemAvail 1416 GB

## UTC TIME WRITTEN
2026-11-26 02:15Z

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
Server 1 (this box): MemAvail 59.1 GB; live reservations 5 (5 GB); workers 13, of which TP-adopted 13 (RSS 17.8 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=24 LOAD_CAP=40 | load1/5/15: 66.25, 68.03, 61.59
  by tag: NYR quota 12 running 6 hungry True RSS 7.5 GB PSS 6.8 GB; NYE quota 16 running 7 hungry False RSS 10.3 GB PSS 9.5 GB
  cell-months finished last hour (DONE markers): 
  top running jobs: TL3_NYE_Lc17dd748_ALNCT7p (x12);TL3_NYE_Lc17dd748_ALNCT14p (x8);TL3_NYE_Lc17dd748_ALN (x6);
Server 2 (rs4 metal): load / disk / tp_launch procs: 92.00, 88.48, 86.20|/dev/md2         28T  2.8T   26T  10% /mnt/l2|54|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261125_1930Z_Josh-combined-all-sessions-fitted-at-6-and-best-session-lots.md 20261125_2057Z_Josh-pick-best-recent-that-passes-prior-years.md 20261125_2120Z_Josh-selection-rule-bake-off-walk-forward.md 20261125_2240Z_Josh-frontier-on-filter-first-picks-and-keys.md 20261126_0025Z_Josh-London-pick-that-passes.md
