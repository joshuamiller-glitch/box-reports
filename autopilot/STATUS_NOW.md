# STATUS_NOW (written 2026-11-17 14:15Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-17 14:15Z | box1: busy 100%, load1 39.98, workers 24, MemAvail 84 GB | server2: busy 100%, load1 91.98, workers 95, MemAvail 1392 GB | pending box1-eligible 37889 / server2-eligible 39358 (shared queues count in both; unleased, not DONE)

## UTC TIME WRITTEN
2026-11-17 14:15Z

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
Server 1 (this box): MemAvail 83.9 GB; live reservations 4 (4 GB); workers 24, of which TP-adopted 24 (RSS 41.8 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=32 LOAD_CAP=40 | load1/5/15: 39.98, 38.79, 38.20
  by tag: CF quota 8 running 3 hungry True RSS 5.6 GB PSS 5.2 GB; MA quota 8 running 1 hungry True RSS 1.5 GB PSS 1.3 GB; JV quota 14 running 5 hungry True RSS 7.9 GB PSS 6.6 GB; RB quota 4 running 1 hungry True RSS 0.8 GB PSS 0.5 GB; TOOLS quota 8 running 14 hungry False RSS 26.0 GB PSS 20.7 G
  cell-months finished last hour (DONE markers): 1797
  top running jobs: TL3_ME_C_LH_K2_S40 (x6);TL3_DD_JL3_C (x4);TL3_CT_CH_H_M7L_S41 (x4);
Server 2 (rs4 metal): load / disk / tp_launch procs: 91.98, 90.09, 88.98|/dev/md2         28T  880G   28T   4% /mnt/l2|173|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261117_1331Z_day-done-variants-from-live-night.md 20261117_1334Z_stage3-brackets-by-environment.md 20261117_1337Z_exits-add-uw-levels-sizing-book-walls.md 20261117_1342Z_MAJOR-CHANGES-PROGRAMME.md 20261117_1346Z_MAJOR-F-new-london-and-newyork-books.md
