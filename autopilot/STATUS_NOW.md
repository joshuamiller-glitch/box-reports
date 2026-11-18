# STATUS_NOW (written 2026-11-18 23:45Z by status_now.py; judgment sections from STATUS_NOTES.md)

LEAD SILENT 40 MIN (CORES.md says no real lead note in MORNING.md for 40+ min)

LATEST CORES.md LINE: 2026-11-18 23:45Z | box1: busy 100%, load1 72.86, workers 27, MemAvail 53 GB | server2: busy 100%, load1 132.70, workers 13, MemAvail 1022 GB | pending box1-eligible 40902 / server2-eligible 41829 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 320.06, workers 189 (grid) + 53 (engine), 128 threads, MemAvail 1130 GB | serverB: busy 100%, load1 290.55, workers 187 (grid) + 55 (engine), 128 threads, MemAvail 910 GB

## UTC TIME WRITTEN
2026-11-18 23:45Z

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
Server 1 (this box): MemAvail 54.3 GB; live reservations 8 (8 GB); workers 27, of which TP-adopted 27 (RSS 45.3 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=32 LOAD_CAP=40 | load1/5/15: 72.86, 73.13, 73.78
  by tag: NT quota 8 running 6 hungry True RSS 9.7 GB PSS 8.4 GB; NYL quota 12 running 8 hungry True RSS 14.1 GB PSS 11.2 GB; NYR quota 16 running 11 hungry True RSS 18.2 GB PSS 15.5 GB; LON quota 12 running 2 hungry True RSS 3.3 GB PSS 3.0 GB; NT quota 0 running 6 hungry False RSS 9.7 GB PSS 8.4 GB
  cell-months finished last hour (DONE markers): 901
  top running jobs: TL3_NT_CT19_SH_K7_k4 (x12);TL3_NYE_Laf0d78ab_RK7 (x10);TL3_NYE_L4d803f17_RK7 (x8);
Server 2 (rs4 metal): load / disk / tp_launch procs: 130.91, 137.38, 134.25|/dev/md2         28T  1.5T   27T   6% /mnt/l2|18|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261118_2118Z_NIGHT-STANDING-ORDERS-act-without-new-orders.md 20261118_2057Z_luck-test-add-whole-history-column-beside-L6M.md 20261118_2128Z_R3-null-sanity-check-NYAM-below-chance.md 20261118_2218Z_after-R3-sanity-null-is-the-judge-queues-real-pass1-rate.md 20261118_2236Z_box1-root-disk-9GB-guard-it-and-engine-queue.md
