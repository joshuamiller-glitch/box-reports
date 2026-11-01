
## REDO-1T1 rows (2026-11-01, data-build sub-job; cap 20261031, last label day 20261030)

New files only (old files untouched), all under l2vast/ds3/out/redo/rows/ :
base_ST_redo, base_HM_redo, base_KB_redo, base_SM_redo, wt_rows_redo, pb7_rows_redo (.parquet). Builders unchanged (ba_rows2.gen(E,events(E),60,60); asm_lib.gen_wt_rows 45/33.75; pb7_build.signals('PB7','G',False)); only caps lifted in copies under code/cap/redo_*.py.
Aux 1-min bars: I had already built /mnt/l2/l2vast/ds3_thp/aux/aux_bar_redo.npz (code/cap/redo_aux.py) before REDO-1's message; PB7 rows were then re-run on REDO-1's /mnt/l2/l2vast/ds3_thp_redo/aux/aux_bar.npz -> byte-identical frame (DataFrame.equals True). The two aux files differ only in vol/eth_vwap/eth_sd/rth_vwap/rth_sd, from bar index 1299535 on (REDO-1's file has vol=0 there, i.e. the L2 1min ext-week files 2026-10__ext_* were not read; mine reads all files in tables/NQ/1min/*.parquet). PB7 does not use vol. ISSUE for REDO-1: vol (and VWAP/sd columns) in ds3_thp_redo aux are zero for the last ~20.6k bars (Oct 12-30).
Old aux prefix check (mine): all 34 columns bit-identical to aux_bar.npz on the first 1,059,591 bars (REDO-1's: same except as above, vol prefix identical).

### Tie-out (new vs old, rows with exit <= old last exit must be identical in all columns)
| book | old rows | new rows | added | new label-day range (entry) | identical prefix | straddling old end |
|---|---|---|---|---|---|---|
| ST | 8309 | 8395 | 86 | 2023-02-10..2026-10-30 | True | 0 |
| HM | 6311 | 6375 | 64 | same..2026-10-30 | True | 0 |
| KB | 8593 | 8701 | 108 | same..2026-10-30 | True | 0 |
| SM | 2397 | 2410 | 13 | same..2026-10-30 | True | 0 |
| WT | 11641 | 11757 | 116 | same..2026-10-30 | True | 0 |
| PB7 (A6) | 17031 (to ld 20260206) | 22357 | 5326 | ld 20230403..20261030 | True (ld<=20260206) | 0 |
Old ST/HM/KB/SM/WT files ended 2026-10-23 entries; added rows are all entered after the old last exit (ei > old max xi). PB7 old file ended at ld 20260206 (capped); the 5326 added are ld > 20260206.
KNOWN TRAP handled: TC._TP = out/redo/te_tape_bar_redo.npz set before events (code/cap/redo_rows_base.py).

### Independent recomputation (30 random label days after 20260206, seed 20261101; numpy scan on SH/SL/SC, no firmlib; code/cap/redo_rows_indep.py, redo_rows_indep_pb7.py)
Days: 20260209 0306 0312 0319 0326 0413 0414 0427 0430 0513 0522 0525 0527 0528 0601 0603 0604 0611 0615 0622 0707 0723 0803 0928 1001 1005 1009 1014 1026 1029.
| book | trades | entry px ok | exit type ok | exit px ok |
|---|---|---|---|---|
| ST | 446 | 446 | 446 | 446 |
| HM | 330 | 330 | 330 | 330 |
| KB | 480 | 480 | 480 | 480 |
| SM | 104 | 104 | 104 | 104 |
| WT | 613 | 613 | 613 | 613 |
| PB7 | 916 | 916 | 916 | 916 (also exit second index) |
(Entry check for the 1-min books is epx == o[ei] of the extended array; stop fills accepted at the stop level or worse by a gap.)

### Commands to extend next week (one worker, OMP/MKL/NUMBA threads=1, after the ds3_g2_redo arrays, te_tape_bar_redo.npz and aux file are re-extended)
cd l2vast/ds3/code/cap
nice python3 redo_rows_base.py ST,HM,KB,SM        # needs TC._TP cache at the new length (set inside the script; rebuild te_tape_bar_redo.npz first)
nice python3 redo_rows_wt.py
REDO_AUXF=/mnt/l2/l2vast/ds3_thp_redo/aux/aux_bar.npz nice python3 redo_rows_pb7.py   # CUT_LD/CUT_S in redo_be_lib.py (20261031 / 1793394000) must be raised
python3 redo_rows_tie.py ST,HM,KB,SM,WT,PB7 ; python3 redo_rows_indep.py ; python3 redo_rows_indep_pb7.py   # (update the old-file paths in redo_rows_tie.py to the *_redo files, and the sample days)
Optional aux rebuild: nice python3 redo_aux.py (writes /mnt/l2/l2vast/ds3_thp/aux/aux_bar_redo.npz; CUT_NS inside must be raised).
PE not built (another agent). Open: the 33 duplicate boundary minutes in tables/NQ/1min are double counted in vol by the (unchanged) thp_aux method, same as the old file.
