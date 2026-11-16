# STATUS_NOW (written 2026-11-16 18:31Z by status_now.py; judgment sections from STATUS_NOTES.md)

## UTC TIME WRITTEN
2026-11-16 18:31Z

## NEEDS HELP
- W-S2: server 2 copy/setup in progress (about 75-90 min copy); nothing blocked yet.
- Per-second MBO tables for 2026-11-01..11-05 are missing (W-CF2 checking raw files).

## NEEDS THE USER
- DS7.cs LINE 1790 BUG (v2.0): the persist counter is cleared on every winning second, so the K7/U7/M7 book-reading profit lines (persist >= 2) can never fire live. Fix in autopilot/DS7_PROFIT_LINES_SPEC.md (one line). Decide before tonight's install.
- Please confirm which profit-side lines are in v2.9 (policy file received; this is answered by it: the three lines ARE in the file but dead by the bug).

## PASSED SINCE LAST FILE
- none (no candidate has beaten all its persistent-draw controls yet)

## FAILED / WITHDRAWN SINCE LAST FILE
- London range skip (LS1/LS125): no HOLD DD cut at any k; old random controls invalid, status Off/Shadow.
- Profit lines K7 lock / U7 tighten / M7 step: 43-month replay net negative (and dead live because of the line 1790 bug).

## EACH SERVER
Server 1 (this box): MemAvail 85.2 GB; live reservations 9 (9 GB); workers 27, of which TP-adopted 27 (RSS 45.8 GB) vs others 0 (RSS 0.0 GB)
  caps: WORKER_CAP=28 LOAD_CAP=40 | load1/5/15: 36.16, 35.25, 34.47
  by tag: CF quota 4 running 3 hungry True RSS 5.0 GB PSS 4.4 GB; D10 quota 10 running 15 hungry False RSS 26.5 GB PSS 21.9 GB; BD quota 10 running 2 hungry True RSS 3.9 GB PSS 3.1 GB; FL quota 4 running 1 hungry True RSS 1.3 GB PSS 1.1 GB; RA quota 2 running 2 hungry False RSS 2.1 GB PSS 1.8 GB; REST quota 99 running 4 hungry False RSS 7.0 GB PSS 6.5 GB
  cell-months finished last hour (DONE markers): 338
  top running jobs: TL3_D10_M1_50_g00_c1_d10_c20_tb_B_JL2_ddvwap_w_aK (x6);TL3_FL_LEADL5_SKIP_PD (x4);TL3_D10_M1_50_g00_c1_d10_c20_tb_B_bM7_sam_JL2_ddvote_w_aT20 (x4);
Server 2 (rs4 metal): load / disk / tp_launch procs: 0.24, 0.53, 0.45|/dev/md2         28T  661G   28T   3% /mnt/l2|0|
  state: A inventory (done) B mount md0 RAID0 of 4 NVMe as /mnt/l2, packages C rsync code+data, venv D identity (JL2 202610=642/27,487.58; JN05W2 202610 598/25,943.82) E

## NEXT DEADLINES
- 19:00Z RA M7 cap-3 page, 21:00Z DS3_BRACKET_DD_BUILD.md (W-D10), profit-line leave-one-out section (W-JV, 21:00Z): on time so far.
- 20:30Z Step 2 engine rows (controls will not all finish: some rows ENGINE ONLY).
- 21:00Z quota switch: EV 4 (FLAT vs BOOK), JV 14 (T-JOINT-EXIT); server 2 ready ~21:00Z.
- 12:00Z 11-17: DS3_FLAT_VS_BOOK.md, DS3_JOINT_EXIT.md first table, DS3_REBUILD_S1.md first table.

## INBOX (last 5 received)
20261116_1825Z_test.md 20261116_1826Z_profit-lines-leave-one-out.md 20261116_1827Z_rebuild-addendum2-tape-speed.md 20261116_1830Z_status-file-and-faster-mirror.md
- lead 18:27Z INBOX 20261116_1826Z_profit-lines-leave-one-out.md: DUPLICATE of the pasted order (already in progress: W-JV world A/B, 4 workers, report 21:00Z i
- lead 18:27Z INBOX 20261116_1827Z_rebuild-addendum2-tape-speed.md: DUPLICATE of the pasted tape-speed order (assigned to W-CF2/W-FL1) EXCEPT the new last line:
- lead 18:30Z INBOX 20261116_1830Z_status-file-and-faster-mirror.md received (auto-ack by inbox_watch.sh; the lead reads it next and logs the action)
