# STATUS_NOW (written 2026-11-16 20:15Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-16 20:15Z | box1: busy 95%, load1 34.06, workers 24, MemAvail 93 GB | server2: busy 100%, load1 94.57, workers 98, MemAvail 1374 GB (copying, 304 GB of 305 GB done) | jobs pending 3161

## UTC TIME WRITTEN
2026-11-16 20:15Z

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
Server 1 (this box): MemAvail 91.9 GB; live reservations 10 (10 GB); workers 24, of which TP-adopted 24 (RSS 39.7 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=32 LOAD_CAP=40 | load1/5/15: 34.14, 34.41, 33.43
  by tag: CF quota 4 running 3 hungry True RSS 4.6 GB PSS 4.2 GB; D10 quota 12 running 13 hungry False RSS 21.3 GB PSS 18.5 GB; BD quota 10 running 1 hungry True RSS 1.2 GB PSS 1.1 GB; RA quota 2 running 3 hungry False RSS 4.8 GB PSS 4.5 GB; REST quota 99 running 4 hungry False RSS 7.9 GB PSS 7.4 GB
  cell-months finished last hour (DONE markers): 737
  top running jobs: TL3_RA_JL2_PL3_M7L_CAP3 (x4);TL3_RA_JL2_M7L_CAP3 (x4);TL3_CF_PD_RS_P7A_JL2 (x4);
Server 2 (rs4 metal): load / disk / tp_launch procs: 94.57, 103.55, 100.71|/dev/md2         28T  853G   28T   3% /mnt/l2|191|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261116_1838Z_fill-the-cap.md 20261116_1840Z_core-meter-both-servers.md 20261116_1938Z_server2-ramp-faster-and-cores-file.md 20261116_1954Z_calibrate-the-pass-rule.md 20261116_2000Z_desk-standard-validation.md
- INBOX 20261116_1954Z_calibrate-the-pass-rule received - W-PR2 calibrates the pass rule (plants/noise, percentile over >=30 draws, week-bootstrap, right contro
- INBOX 20261116_2000Z_desk-standard-validation received - W-DV adds trial ledger + White RC/SPA/DSR/BH, CSCV PBO, DD block bootstrap, INCUBATION.md, page heade
