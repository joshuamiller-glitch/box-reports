# STATUS_NOW (written 2026-11-19 01:15Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-19 01:15Z | box1: busy 100%, load1 74.55, workers 30, MemAvail 59 GB | server2: busy 100%, load1 98.81, workers 14, MemAvail 1117 GB | pending box1-eligible 63145 / server2-eligible 63311 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 130.16, workers 61 (grid) + 56 (engine), 128 threads, MemAvail 1276 GB | serverB: busy 100%, load1 177.57, workers 99 (grid) + 53 (engine), 128 threads, MemAvail 1200 GB

## UTC TIME WRITTEN
2026-11-19 01:15Z

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
Server 1 (this box): MemAvail 58.1 GB; live reservations 4 (4 GB); workers 30, of which TP-adopted 30 (RSS 52.9 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=32 LOAD_CAP=40 | load1/5/15: 74.55, 76.42, 75.92
  by tag: NT quota 8 running 6 hungry True RSS 9.5 GB PSS 8.3 GB; NYL quota 12 running 12 hungry False RSS 21.8 GB PSS 16.9 GB; NYR quota 16 running 11 hungry True RSS 19.9 GB PSS 16.9 GB; ASI quota 16 running 1 hungry True RSS 1.7 GB PSS 1.5 GB; NT quota 0 running 6 hungry False RSS 9.5 GB PSS 8.3 GB
  cell-months finished last hour (DONE markers): 968
  top running jobs: TL3_NYE_L303fac79_RK7 (x12);TL3_NT_CT9_SH_K7_k2 (x12);TL3_NYE_L2ddcca42_RK7 (x10);
Server 2 (rs4 metal): load / disk / tp_launch procs: 96.91, 101.44, 103.90|/dev/md2         28T  1.6T   27T   6% /mnt/l2|24|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261118_2057Z_luck-test-add-whole-history-column-beside-L6M.md 20261118_2128Z_R3-null-sanity-check-NYAM-below-chance.md 20261118_2218Z_after-R3-sanity-null-is-the-judge-queues-real-pass1-rate.md 20261118_2236Z_box1-root-disk-9GB-guard-it-and-engine-queue.md 20261119_0017Z_exit-yield-to-150-pairs-oversubscription-dallas-queue.md
