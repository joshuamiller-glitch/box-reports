# REDO_BARS_ENG - BAR-ENG ledger rows extended to label day 20261030 (D1, T-RECENT-REDO section 4), 2026-11-01 ~18:05Z

Status: DONE for all **2,765 / 2,765** BARS-ENG ledger rows (and the other 1,561 stored BARS-ENG rows, 4,326 in all). 0 unextendable. 0 not tied. Research only, no PASS claims, frozen parameters (no refit, no new cells), no approximation, no carry-forward. DEAD_CELLS.csv untouched: no new cell was scored (every cell is a stored cell), so no append_cells call.

## Method
* Builder = the program's own code (`l2vast/ds3/code/bars_eng/be_lib.py` engines ST HM KB SM PE WT MV PB PB7 DN and the be_run / be_brk simulation: 60/60, 30/30, 45/45, 75/75, 90/90, 60-stop/prior-day-level target; WT 45/33.75 shape) via REDO-1's copy `code/cap/redo_be_lib.py` (cap 20261031, 1-s path ds3_g2_redo, aux 1-min bars redo for the 1-min controls). Driver: `code/recent_wins_redo/D1/d1_build.py` (inputs re-pointed to `out/bars_redo`, the de-duplicated-tape tick library; **bpm frozen at the original old-window value**, `_bpm_lib.csv bpm_orig`, per DS3_DATA_REDO_BARS). Only the 3,582 trade files that exist in the stored dirs (+ 50 controls) were rebuilt; 2 workers, OMP/MKL=1, about 15 min wall.
* Trade files (full history 20230403..20261030, same schema as the stored ones): `out/recent_wins/redo/bars_eng/trades/<dir>/<bar>__<eng>__<var>.parquet`; the directory is a symlink to /mnt/l2/l2vast/ds3_redo_d1/trades (1.2 GB; the root disk was 100% full at 17:55Z, see caveats).
* Row vector = trades of the row's session (ALL = every trade). Windows from `code/cap/windows.py` (L1M L2M L3M L6M HOLD MID PRE X'). Per window: per-contract mean M (pts), n trades, MDE = 2.8 x SE of the trade-level mean (the SAME definition as the stored MDE_L3M; not the weekly MDE of windows.py), usd at live lots (pts x 20 x lots; lots ST/HM/MV/PB/DN/PB7 10, WT 7, KB 5.2, SM 7.4, PE 5.6 = the stored usd_live_L3M rule), 1-min control mean per window (ctl_<w>).

## Files (out/recent_wins/redo/bars_eng/)
* `row_windows.parquet` / `.csv`: 4,326 rows = row_id, rkey, in_old_ledger, cell, book, bar, var, bracket, session, then for L1M|L2M|L3M|L6M|HOLD|MID|PRE|X': mean, _n, _mde, _usd; `old_L3M_stored` (old L3M to Feb-06, beside), old_*_stored / old_*_rebuilt for L3M n, usd, MDE, L6M, HOLD, PRE, X on the OLD windows; ctl_<window>; `tie_status` (TIED | TIED_TAPE2), `tie_maxrel`, `file_tie`.
* `file_tie.csv`: tie-out per trade file (rebuilt <= 20260206 vs stored vs TAPE-2). `vec_full.parquet`: daily vectors (rkey, ld, pts, pts2, n, usd) 20230403..20261030 for all 4,326 rows. `unextendable.csv`: empty (header only).
* For REDO-4: `out/recent_wins/redo/vec/D1__BARS-ENG.parquet` (2,765 ledger rkeys, 20251101..20261030, columns rkey, ld, usd, pts, n, pts2; n = trades that day, so L3M = sum(pts)/sum(n)). Logs: build_*.log, tie.log. Code: `code/recent_wins_redo/D1/`.

## Tie-out (old period 20230403..20260206, rebuilt vs stored, 1e-6 per contract, plus identical trade keys ld/dec/side/type/exit)
| level | count | result |
|---|---|---|
| trade files, cells | 3,582 | **1,632 bit-identical to the stored file**; **1,949 differ from the stored file and equal TAPE-2's rebuilt file exactly** (the 11 defective-tape store months: 20230403 20230703 20231002 20240603 20240902 20241202 20250203 20250303 20250602 20251103 20260202; first differing trade on a defective day in 1,947 of 1,949, the other 2 are recursive-indicator carry-over; stored vs TAPE-2 differ by a different trade count in 1,563 files and in values in 386); **1 mismatch** |
| controls (native 1-min, aux redo) | 50 | 50 / 50 bit-identical to stored |
| ledger rows (2,765) | 2,765 | **1,697 TIED** (all of L3M, n, usd, MDE, L6M, HOLD, PRE, X within 1e-6 of the stored ledger row, max rel 2.5e-16); **1,068 TIED_TAPE2** (differ from the stored row only because the stored file predates the TAPE-2 fix; the row equals TAPE-2's rebuild; 490 of them move the old L3M by > 1e-6, max |d| 6.09 pts per contract on a small-n cell); 0 NOT_TIED |
| all 4,326 stored rows | 4,326 | 2,688 TIED, 1,638 TIED_TAPE2, 0 not tied |
The 11-defective-month values: TAPE-2's rebuilt values are used (my rebuild from out/bars_redo equals them bit for bit), as ordered. The stored ledger numbers (old L3M) are kept beside, unchanged.

Mismatch (1 file, no ledger row affected): `trades/renko_48__DN__D` has 6,378 trades in the old period vs 6,377 stored and in TAPE-2: one extra DN trade (session 'close', label day 20260206, filled 16:44 ET, a stop-order bracket whose renko-bar order window ends on the first bar of the next session). The old run dropped it by its own data-cap guard (`d1 < CUT_S - 3600`, the old cap), the extended run lifts the guard, so it is a cap-boundary effect, not a data difference. The ledger rows of this file (DN renko_48 60/60 D pre) are TIED.

## What moved (descriptive only; no rule is selected on L1M / L2M)
Of the 2,765 old-ledger rows (all had positive old L3M and L6M): new L1M > 0 in 929, L2M > 0 in 835, L3M > 0 in 634, L6M > 0 in 526, HOLD > 0 in 710, MID > 0 in 746; positive in both new L3M and new L6M: 265. Median n: L1M 49, L2M 86, L3M 123, L6M 293, HOLD 515, MID 115 (most cells sit below their MDE; MDE is in the table). Largest new L3M $ rows are PB (time_5m 75/75 G ALL +7.7 pts over 244 trades, MDE 12.7, below it).

## Unextendable rows
None (0). Every ledger row had its stored trade file, bar type and control rebuilt.

## Caveats
* The root filesystem (/dev/md0) hit 100% (28 KB free) at ~17:55Z while D1 ran: 25 jobs of an optional pass failed with ENOSPC and were re-run; all outputs were checked after the re-run. Trade files were moved to /mnt/l2 (symlink). Other agents may also be hit; free space was 0.7 GB at 18:05Z.
* DN / PB7 rows exist only at 60/60 (as stored). DN renko-class order sims use the same 'close' session label as stored.
* bpm frozen at the old value (the G variants keep their definition); over the new window the market prints up to 30% more bars/min (DS3_DATA_REDO_BARS), so a refit of g would change some G cells: not done (frozen parameters).
