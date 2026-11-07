# MON_READY - Monday 2026-11-09 readiness (written Sat 2026-11-07 05:15Z by MON-READY; Shadow only, no PASS claims)

## Pipeline map
- 13:00Z `zones3/standing/monday_all.sh` (pid 3715292, next fire 2026-11-09T13:00Z) -> `monday_all.py` -> bt/nyam/fade/sizer/nyam-regime runners + runners.json (SHADOW-2, live_monitor). Appends ONE block to MORNING.md; state `autopilot/monday_all_state.json` (absent now = fine). Reads `forward_register/{bt,nyam,fade,sizer_shadow,shadow2}` and `forward_register/tape.csv`.
- 14:00Z `code/watch/watch_all.sh` (pid 674892) -> `watch_all.py` (registry `watch_registry.json`, sha-gated spec/plugin/amendment) -> appends to `autopilot/WATCH_REGISTER.md`.

## WATCH plugins and input end dates (on disk, 2026-11-07)
| watch | data input | ends | Monday status expected |
|--|--|--|--|
| RTY_PREMARKET | tables/RTY/1s | 2026-10-30 21:00Z | NO-DATA (floor 11-01 23:00Z). Nothing in the Sat pull feeds RTY |
| MONDAY_LONG (+AMEND1 bf02a93c14c2, intact) | tables/NQ/1min | 2026-11-05 16:05Z | ACCUMULATING N=0/26 (week 1 = Mon 11-09, first read Tue 11-10) |
| CL_DONCHIAN | find_c/cache_c/CL.npz | 2026-10-16 20:59Z | NO-DATA (floor 10-17). topup_ohlcv1m_CL_20261013_20261031.dbn.zst exists but is NOT in the npz |
| MBT_ASIA_KELTNER | ds3_instr/MBT_1m.npz (+topup MBT file) | 2026-10-31 23:43Z | NO-DATA (floor 11-01 00:00Z); the topup also ends 10-31 |
| GC_TREND | find_c/cache_c/GC.npz | 2026-10-16 20:59Z | NO-DATA (floor 11-08 22:00Z; start LD 11-09, so Monday has no completed day anyway) |
| NQ_PDL | instr_1s/NQ_S*.npy (ends 10-16) + forward_register/ohlcv1s/NQ_*.npz (dir does not exist) | none forward | NO-DATA unless tape_to_ohlcv1s.py is run after the tape exists |
Ends 2026-11-05 only for MONDAY_LONG (NQ tables). Nothing else reaches 11-05.

## Dry runs (private scratch /mnt/l2/l2vast/_mon_ready/; MORNING.md and WATCH_REGISTER.md md5 unchanged)
- `watch_all.py --dry` on a copy of code/watch with OUT redirected (the real one writes BADPRINTS_*.csv into out/watch even in --dry): 0.4 s, all 6 rows produced, no errors. Only MONDAY_LONG scored; the rest NO-DATA as above.
- `monday_all.py --dry --week 1` (no run-date override exists; flag is --dry/--week): 1.5 s wall, all 7 runners rc=0. All forward registers have 0 signal rows, so every row is "no data yet". With a synthetic tape via MONDAY_TAPE the FEED/TAPE row turns OK. The real tape-present scoring path is not exercised until real tape and signals exist.
- `hm_feed.py --verify` now: "no ohlcv-1s lines" (rc 0). `log_spend.py` dry: nothing pulled yet. Both expected pre-pull.

## sat_pull.sh review (read only; pid 1176261 alive, sleeping to 08:05Z)
OK: window 2026-11-01T23:00Z..11-07T00:00Z; floor and 8h license lag satisfied at 08:05Z; key from `bash -ic` (exported ~/.bashrc line 120, after the interactive guard); abort range cost 0.9-1.5 and records 250k-330k aborts via python exit 1 (also aborts when dry fails: empty COST makes float('') raise); paths exist (hmfwd, shadow, data_fwd, forward_register); --execute needs the exact CONFIRM string; pull_nov also checks max-usd 2.00 and SPEND remaining ($8000 - $7311.63 = $688; runbook says true spent is $7,288.26 +LEAN item discrepancy, harmless); log_spend parses MANIFEST only (idempotent).
Issues:
1. No tape_to_ohlcv1s.py step (PF-3): NQ_PDL gets no forward file. Run by hand after the tape: `python3 -I zones3/standing/tape_to_ohlcv1s.py` (writes forward_register/ohlcv1s/, refuses to overwrite).
2. No `set -e` / pull-rc gate: if the pull returns nonzero (REFUSED, partial) the script still runs log_spend, hm_feed and feed_check. Harmless (they read MANIFEST; log_spend logs only existing lines), but the log then reads as noise; look at the "pull rc=" line first.
3. Log filters every line containing "key" (grep -v -i), which could hide an unrelated error line mentioning "key" (e.g. a KeyError traceback).
4. hm_feed --tape-out runs even when --verify fails; check the log for FAIL before trusting tape.csv.
5. feed_check defaults to --end 2026-11-06T22:00Z: fine for week 1.
No fatal bug found.

## Monday checklist
Saturday/Sunday
1. `tail sat_pull.log` (/mnt/l2/l2vast/raw/NQ_sat_pull/sat_pull.log): expect `dry: cost=~1.14 records=~311169`, `pull rc=0`, SPEND update, hm_feed `--verify` no FAIL, feed_check `ALL CHECKS PASSED` (5 trade dates, 0 prints in ET 17:xx, first print Sun 23:00Z).
2. If ABORT line: do not rerun blindly; check quote vs range, then user OK per runbook.
3. Confirm `forward_register/tape.csv` exists and `data_fwd/MANIFEST.jsonl` has one line; add DECISIONS.md spend line (log_spend prints it).
4. Run `tape_to_ohlcv1s.py` (issue 1). Optionally decide on topping up CL/GC/MBT/RTY inputs (needs purchase approval; not done by anything scheduled).
Monday
5. Before 13:00Z: `ps` shows monday_all.sh 3715292 and watch_all.sh 674892; `MemAvailable` fine; nothing else holds /tmp/monday_all.lock.
6. After 13:00Z inspect FIRST the `FEED / TAPE` row of the new MORNING.md block: must say OK with last second ~Fri 11-06 21:59Z. "NO TAPE" = n0/$0 rows mean no outcome data.
7. Runner status line: all rc=0. Registers have 0 signals until the box logs Monday-week signals (live D7 files MISSING is expected).
8. After 14:00Z: WATCH_REGISTER.md new block. Expect 5 NO-DATA rows + MONDAY_LONG ACCUMULATING; any REFUSED-* row means a sha changed (spec, plugin or amendment): do not edit specs, report. Monday-long amendment stays as filed.
9. Known false alarm: check_monday_preflight.sh rejects the real tape header (runbook section 3).
All WATCH rows are Shadow only; statuses are not decisions.
