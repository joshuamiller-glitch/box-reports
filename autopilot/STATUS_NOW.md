# STATUS_NOW (written 2026-11-24 03:30Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-24 03:30Z | WARNING serverC below 85% busy for 5 readings in a row with jobs pending

## UTC TIME WRITTEN
2026-11-24 03:30Z

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
Server 1 (this box): MemAvail 76.9 GB; live reservations 4 (4 GB); workers 15, of which TP-adopted 14 (RSS 17.8 GB) vs others 1 (RSS 1.3 GB)
  caps: WORKER_CAP=24 LOAD_CAP=40 | load1/5/15: 53.35, 55.65, 64.16
  by tag: NYE quota 16 running 14 hungry False RSS 17.8 GB PSS 16.2 GB; REST quota 0 running 1 hungry False RSS 1.3 GB PSS 1.2 GB
  cell-months finished last hour (DONE markers): 
  top running jobs: TL3_NYE_Lb13de797_ALN (x28);TL3_NYE_Lcd88ca38_ALN (x2);TL3_NYE_La04876aa_ALN (x1);
Server 2 (rs4 metal): load / disk / tp_launch procs: 81.41, 82.61, 83.57|/dev/md2         28T  2.8T   26T  10% /mnt/l2|56|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261123_2005Z_Josh-state-cut-spec-for-ninjatrader.md 20261123_2010Z_Josh-combined-table-refresh-as-tonights-file.md 20261123_2135Z_Josh-one-session-at-a-time-asia-first.md 20261123_2330Z_time-windows-after-midnight-rows-look-broken.md 20261124_0250Z_Josh-depth-book-repeat-stops-skip-rule.md
