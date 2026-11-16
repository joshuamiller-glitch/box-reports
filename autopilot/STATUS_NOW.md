# STATUS_NOW (written 2026-11-16 21:15Z by status_now.py; judgment sections from STATUS_NOTES.md)

LATEST CORES.md LINE: 2026-11-16 21:15Z | WARNING server2 below 85% busy for 2 readings in a row with jobs pending

## UTC TIME WRITTEN
2026-11-16 21:15Z

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
Server 1 (this box): MemAvail 86.6 GB; live reservations 17 (17 GB); workers 28, of which TP-adopted 28 (RSS 43.6 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=32 LOAD_CAP=40 | load1/5/15: 39.51, 38.66, 38.06
  by tag: CF quota 8 running 4 hungry True RSS 6.6 GB PSS 6.0 GB; D10 quota 12 running 13 hungry False RSS 19.6 GB PSS 17.2 GB; BD quota 10 running 1 hungry True RSS 1.5 GB PSS 1.4 GB; FL quota 8 running 3 hungry True RSS 5.0 GB PSS 4.2 GB; JV quota 14 running 3 hungry True RSS 3.9 GB PSS 3.5 GB; REST quota 99 running 4 hungry False RSS 7.0 GB PSS 6.4 GB
  cell-months finished last hour (DONE markers): 358
  top running jobs: TL3_CF_PD_L3C_P7A_K_JL2 (x6);TL3_D10_M1_50_g00_c1_d10_c20_tb_B_JL2_pol_fx40x40s3p35 (x4);TL3_JV_PL_noU (x2);
Server 2 (rs4 metal): load / disk / tp_launch procs: 39.34, 43.16, 68.39|/dev/md2         28T  854G   28T   3% /mnt/l2|138|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page; 20:30Z Step 2 engine rows (controls will not all finish: ENGINE ONLY rows); 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10) + profit-line leave-one-out both worlds (W-JV) + base-mismatch size (W-RP): on time so far.
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready for real jobs ~19:15Z (cap 16 ramp).
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261116_2000Z_desk-standard-validation.md 20261116_2017Z_rebuild-addendum3-exit-confluence.md 20261116_2028Z_use-ulcer-rescore-now.md 20261116_2101Z_older-windows-for-the-two-closest.md 20261116_2105Z_new-data-candidates-quotes-and-pilots.md
- lead 21:01Z INBOX 20261116_2105Z_new-data-candidates-quotes-and-pilots.md received (auto-ack by inbox_watch.sh; the lead reads it next and logs the action)
- INBOX 20261116_2101Z_older-windows-for-the-two-closest received - W-PR2 runs real cells for PREUW/X' (M7 London cap 3) and GAP/PREUW/X' (H7 NY AM 40/40 and 50
- INBOX 20261116_2105Z_new-data-candidates-quotes-and-pilots received - W-ND ranks/scopes 7 items, QUOTES ONLY (no purchase), free pilots 5-7 now, DS3_NEW_DATA_
