# PREREG_FAKEFILL (W-FAKEFILL, order 1156Z item 1) - written before any scan result was read
SCAN DEFINITION (code/th_fakefill/scan.py): every trades.parquet under /mnt/l2/l2vast (find -name trades.parquet), READ-ONLY. Flags per trade:
F1 entry_px < 1000 ; F2 exit_px < 1000 ; F3 |gross| / max(lots,1) > 20,000 USD ; F4 exit_ns more than 600 s after the last print at or before it in the engine tape cache /mnt/l2/l2vast/_grid/tape/<ym>/ts.npy (exit month tape, then neighbour months; NaN = no tape coverage, counted as 'nogap', not flagged).
(The order's 10-minute rule = 600 s for the SCAN. The CONVENTION for builders and the launcher guard is N = 120 s, see DECISIONS.md.)
Counts are reported per tree (path up to the set directory) and per set family; '0 found' stated explicitly.
EXPOSED SESSION ENDS (code/th_fakefill/expo.py): ET session ends 02:00 (Asia), 08:30 (London), 12:00 (NY AM), 16:00 (NY PM) for every calendar date 2023-04-03..2026-10-31; exposed if the last print at or before the end is > 120 s early and not before the session's start.
Known first scan error corrected before reading results: the first F4 pass used the tape of the month of the FIRST exit in a file (wrong month for trades near a month boundary: 16,233 false F4 hits); superseded by the per-trade month tape + neighbour recheck (scan.py now).
