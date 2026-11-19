# STATUS_NOW (written 2026-11-19 05:45Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-19 05:45Z | box1: busy 100%, load1 72.83, workers 27, MemAvail 63 GB | server2: busy 100%, load1 98.53, workers 14, MemAvail 947 GB | pending box1-eligible 181642 / server2-eligible 181654 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 197.22, workers 61 (grid) + 64 (engine), 128 threads, MemAvail 1237 GB | serverB: busy 100%, load1 193.44, workers 61 (grid) + 65 (engine), 128 threads, MemAvail 1193 GB

## UTC TIME WRITTEN
2026-11-19 05:45Z

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
Server 1 (this box): MemAvail 64.0 GB; live reservations 0 (0 GB); workers 27, of which TP-adopted 27 (RSS 44.1 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=32 LOAD_CAP=40 | load1/5/15: 72.83, 73.44, 72.97
  by tag: ASI quota 16 running 6 hungry True RSS 9.3 GB PSS 8.5 GB; NYR quota 16 running 15 hungry True RSS 24.5 GB PSS 22.7 GB; LON quota 12 running 6 hungry True RSS 10.3 GB PSS 9.4 GB
  cell-months finished last hour (DONE markers): 1188
  top running jobs: TL3_NYW_L11631333_ADD (x30);TL3_LON_LA4_ADD (x12);TL3_ASI_AB2_ALL (x12);
Server 2 (rs4 metal): load / disk / tp_launch procs: 99.09, 99.56, 96.52|/dev/md2         28T  1.7T   27T   7% /mnt/l2|24|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261119_0224Z_NO-SHORTCUTS-full-exit-run-and-100pct-machines.md 20261119_0228Z_SEQUENCE-Asia-NYAM-fully-first-then-London-then-NYPM.md 20261119_0325Z_Frankfurt-grid-still-low-after-pause-49-workers-not-computing.md 20261119_0400Z_ASIA-status-page-Asia-is-first.md 20261119_0432Z_Dallas-guard-E-and-live-agent-list.md
