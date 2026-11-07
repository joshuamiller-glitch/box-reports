# MON_READY2 - Monday scoring path on the REAL tape (Sat 2026-11-07 ~08:40Z; Shadow only, no PASS claims, nothing purchased)

Private scratch /mnt/l2/l2vast/_mon_ready2/ (copy of code/watch + code/zones3, autopilot/forward_register/out paths sed-redirected into scratch; real MORNING.md and WATCH_REGISTER.md md5 unchanged, nothing newer than the start marker in forward_register/ or out/watch). Specs, plugins, amendment untouched (the nq_pdl plugin must be the byte-original: sed on it makes its sha refuse, so scratch reads the real forward npz read-only).

## watch_all.py --dry (4.8 s with NQ_PDL scoring; 0.4 s before the forward file)
| watch | status | note |
|--|--|--|
| RTY_PREMARKET | NO-DATA | last table second 2026-10-30 21:00Z |
| MONDAY_LONG (+AMEND1 bf02a93c14c2) | ACCUMULATING N=0/26 | data to 11-05 16:05Z; bad prints 0 of 5197 |
| CL_DONCHIAN | NO-DATA | last 10-16 20:59Z |
| MBT_ASIA_KELTNER | NO-DATA | last 10-31 23:43Z |
| GC_TREND | NO-DATA | floor 11-08 22:00Z |
| NQ_PDL | ACCUMULATING N=0 of 60 | data to 2026-11-06 21:59:59Z; 0 trades |
No REFUSED row on the byte-original files.

## NQ_PDL with the forward file
Plugin loads NQ_20261101_20261106.npz. 562 events total, exactly 1 in the forward week (label day 11-04, up). Per spec section 3 the forward sample starts the label day after the first COMPLETE forward ISO week: forward_start_ld = 20261109, so 0 signals and 0 trades are scored for week 1. The first scored NQ_PDL trades can only come from Mon 11-09 onward (needs the next weekly ohlcv-1s pull). Cosmetic: the status text still says "waiting for the weekly NQ ohlcv-1s pull".

## MONDAY_LONG, Monday 11-02
START=20261109 in the plugin, so N toward 26 = 0 forward Mondays. The raw 11-02 Monday exists in the NQ 1-min table (forward=False diagnostic: ret -129.1 bps, net -129.9 bps, MNQ usd -742) but is excluded by the spec as filed (week 1 = 11-09). Not counted, not scored. Tue 11-03 and Wed 11-04 are non-Monday days.

## monday_all.py --dry --week 1 (1.7 s wall, 14.3 s CPU; earlier synthetic-tape dry run 1.5 s)
- FEED / TAPE: OK, last second 2026-11-06 21:59:59 UTC (tape has 326,164 data rows).
- All 7 runners rc=0. Every register has 0 signal rows, so BT, NY-AM, top-3 fade, sizer, SHADOW-2 and the Q13/DIS rows all say "no data yet"; LM 1-6 NO DATA (missing/empty csvs). No tape-present scoring is exercised until the box logs signals.

## Bugs / notes (report only)
1. Cosmetic stale NQ_PDL text above. 2. Dry mode of watch_all.py writes BADPRINTS_*.csv into the OUT dir (known). 3. The real tape did not change any WATCH status vs the earlier dry run except NQ_PDL (NO-DATA -> ACCUMULATING). No functional bug found.
