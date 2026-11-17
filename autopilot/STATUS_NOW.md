# STATUS_NOW (written 2026-11-17 17:15Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-17 17:15Z | box1: busy 99%, load1 35.70, workers 31, MemAvail 84 GB | server2: busy 100%, load1 89.78, workers 92, MemAvail 1388 GB | pending box1-eligible 36729 / server2-eligible 40043 (shared queues count in both; unleased, not DONE)

## UTC TIME WRITTEN
2026-11-17 17:15Z

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
Server 1 (this box): MemAvail 85.1 GB; live reservations 8 (8 GB); workers 31, of which TP-adopted 31 (RSS 50.1 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=32 LOAD_CAP=40 | load1/5/15: 35.89, 34.89, 34.58
  by tag: MA quota 8 running 2 hungry True RSS 3.1 GB PSS 2.9 GB; MC quota 6 running 3 hungry True RSS 5.4 GB PSS 4.5 GB; ME quota 6 running 4 hungry True RSS 7.3 GB PSS 6.1 GB; MB quota 6 running 3 hungry True RSS 4.9 GB PSS 4.6 GB; MF quota 4 running 3 hungry True RSS 5.0 GB PSS 4.2 GB; S3 quota 6 running 1 hungry True RSS 0.7 GB PSS 0.5 GB; JV quota 6 running 13 hungry False RSS 20.7 GB PSS 16.4 GB; DD quota 4 running 1 hungry True RSS 1.6 GB PSS 1.3 GB
  cell-months finished last hour (DONE markers): 1694
  top running jobs: TL3_ME_C_LH_K2_S26 (x8);TL3_MB_ORBASIA15S60_L2 (x6);TL3_MA_R2A_JL2 (x4);
Server 2 (rs4 metal): load / disk / tp_launch procs: 89.73, 91.04, 91.52|/dev/md2         28T  882G   28T   4% /mnt/l2|180|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261117_1342Z_MAJOR-CHANGES-PROGRAMME.md 20261117_1346Z_MAJOR-F-new-london-and-newyork-books.md 20261117_1426Z_major-follow-ups-late-entry-and-same-side-losers.md 20261117_1447Z_DELIVERABLES-every-part-ends-in-a-setting.md 20261117_1509Z_day-done-conditional-resume.md
