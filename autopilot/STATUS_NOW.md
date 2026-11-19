# STATUS_NOW (written 2026-11-19 23:15Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-19 23:15Z | WARNING serverC below 85% busy for 28 readings in a row with jobs pending

## UTC TIME WRITTEN
2026-11-19 23:15Z

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
Server 1 (this box): MemAvail 49.4 GB; live reservations 10 (10 GB); workers 16, of which TP-adopted 16 (RSS 25.3 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=36 LOAD_CAP=40 | load1/5/15: 54.85, 62.96, 71.59
  by tag: NYR quota 12 running 9 hungry True RSS 12.6 GB PSS 10.1 GB; ASI quota 14 running 3 hungry True RSS 4.9 GB PSS 4.0 GB; EXE quota 2 running 2 hungry False RSS 4.4 GB PSS 3.2 GB; LON quota 12 running 1 hungry True RSS 1.2 GB PSS 1.1 GB; TOOLS quota 0 running 1 hungry False RSS 2.1 GB PSS 1.6 GB
  cell-months finished last hour (DONE markers): 8915
  top running jobs: TL3_NYE_L9513708b_RK7CT84m (x7);TL3_NYE_L9513708b_RK7CT77m (x6);TL3_ASI_Med328272_RA7 (x4);
Server 2 (rs4 metal): load / disk / tp_launch procs: 117.57, 113.37, 116.90|/dev/md2         28T  2.5T   26T   9% /mnt/l2|56|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261119_2212Z_Josh-add-or-replace-open-and-fix-NYAM.md 20261119_2230Z_Josh-ALL-NEW-BOOKS-no-adds.md 20261119_2233Z_ADDENDUM-all-layers-refit-on-all-new-stack.md 20261119_2300Z_Singapore-slots-base-for-followups-wire-all-layers.md 20261119_2305Z_NIGHT-PROOF-six-machines-no-halt.md
