# STATUS_NOW (written 2026-11-17 07:00Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-17 07:00Z | box1: busy 100%, load1 43.12, workers 21, MemAvail 85 GB | server2: busy 100%, load1 118.84, workers 76, MemAvail 1388 GB | pending box1-eligible 1494 / server2-eligible 14265 (shared queues count in both; unleased, not DONE)

## UTC TIME WRITTEN
2026-11-17 07:00Z

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
Server 1 (this box): MemAvail 84.6 GB; live reservations 0 (0 GB); workers 21, of which TP-adopted 21 (RSS 39.8 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=32 LOAD_CAP=40 | load1/5/15: 43.12, 42.72, 41.66
  by tag: CF quota 8 running 3 hungry True RSS 4.5 GB PSS 4.0 GB; EV quota 8 running 1 hungry True RSS 1.8 GB PSS 1.7 GB; BD quota 10 running 7 hungry True RSS 12.7 GB PSS 11.2 GB; FL quota 8 running 7 hungry True RSS 14.8 GB PSS 10.0 GB; JV quota 14 running 2 hungry True RSS 3.9 GB PSS 3.2 GB; TOOLS quota 8 running 1 hungry False RSS 2.0 GB PSS 1.8 GB
  cell-months finished last hour (DONE markers): 335
  top running jobs: TL3_CF_ST_5_S_RND (x8);TL3_BD_F_fix_T35_H7_as_pl1_p18 (x4);TL3_BD_F_fix_T30_H7_as_pl3_p19 (x4);
Server 2 (rs4 metal): load / disk / tp_launch procs: 118.84, 119.29, 116.34|/dev/md2         28T  877G   28T   4% /mnt/l2|146|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261117_0024Z_lead-note-and-box1.md 20261117_0146Z_wake-test.md 20261117_0312Z_flat-vs-book-explain-a-kp.md 20261117_0400Z_refill-both-queues-before-they-drain.md 20261117_0545Z_stage1-survivors-lookahead-and-selection.md
