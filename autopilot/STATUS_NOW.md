# STATUS_NOW (written 2026-11-19 07:00Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-19 07:00Z | box1: busy 100%, load1 81.36, workers 30, MemAvail 55 GB | server2: busy 100%, load1 119.70, workers 30, MemAvail 1075 GB | pending box1-eligible 129673 / server2-eligible 129685 (shared queues count in both; unleased, not DONE) | serverA: busy 100%, load1 226.38, workers 61 (grid) + 94 (engine), 128 threads, MemAvail 1187 GB | serverB: busy 100%, load1 233.91, workers 61 (grid) + 98 (engine), 128 threads, MemAvail 1152 GB

## UTC TIME WRITTEN
2026-11-19 07:00Z

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
Server 1 (this box): MemAvail 54.3 GB; live reservations 1 (1 GB); workers 30, of which TP-adopted 28 (RSS 47.7 GB) vs others 2 (RSS 2.0 GB)
  caps: WORKER_CAP=36 LOAD_CAP=40 | load1/5/15: 81.36, 76.11, 74.44
  by tag: ASI quota 16 running 6 hungry True RSS 10.3 GB PSS 9.3 GB; NYR quota 16 running 16 hungry False RSS 27.4 GB PSS 25.1 GB; LON quota 12 running 6 hungry True RSS 10.0 GB PSS 8.9 GB; REST quota 0 running 2 hungry False RSS 2.0 GB PSS 1.8 GB
  cell-months finished last hour (DONE markers): 1934
  top running jobs: TL3_NYW_Lfa1de080_ADD (x32);TL3_LON_LA4_RK7 (x12);TL3_ASI_L753bf92a_RK7 (x12);
Server 2 (rs4 metal): load / disk / tp_launch procs: 117.14, 119.72, 117.35|/dev/md2         28T  1.8T   27T   7% /mnt/l2|54|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261119_0325Z_Frankfurt-grid-still-low-after-pause-49-workers-not-computing.md 20261119_0400Z_ASIA-status-page-Asia-is-first.md 20261119_0432Z_Dallas-guard-E-and-live-agent-list.md 20261119_0613Z_cap-step-beyond-70-restate-dates-answer-alert-G.md 20261119_0633Z_engine-is-the-bottleneck-make-the-ladder-engine-faster.md
