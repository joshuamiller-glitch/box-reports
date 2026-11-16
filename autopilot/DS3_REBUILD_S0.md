# DS3_REBUILD_S0 - T-REBUILD stage 0: raw base, each book alone with no layers (W-PM). DESIGN PAGE, no engine result yet.

VERDICT (data ends 2026-10-30; DESIGN ONLY, nothing run): stage 0 needs 10 raw single-book sets on the JL2 chassis (K7 M7 U7 P7 H7 A7 O7 and the shadow books X3 X4 X5 that the engine knows; 43 months each = 430 cell-months plus about 14 one-month identity proofs); S7 is in the engine book list but not in the live book set (needs enabling = 43 more), and X1 X2 X6 X7 X8 do not exist in the engine at all (flagged: they need a build before they can run raw); it waits for W-EV's list of layer switches, the "all layers off" config and a book mask, and for server 2 (PM quota is 0 on this box until the deadline work ends).

## What a raw book is
One book alone (book mask), JL2 chassis (same entry logic, bars, fills, fees), with every layer off: no JN04 LOT / SIGQ / REG sizers, no state cut or book cut line, no K7 flat -45 / P7 flat -42, no F3 context cut, no profit lines (K7 delta_mult lock, M7 tot_rel step, U7 delta_mult tighten), no governor / WL_E1, no ATR-SKIP, no post-exit blackout, no BREADTH skip, no NTZ half size, no DAY-DONE C22, no day caps, no session lot caps or lot tables (the book trades its native lots), no stack cut, no stack cap (the book is alone, so stack effects are absent by construction), fixed 60-pt stop and the book's own target. Exits: stop 60 / target as the book defines; exits recorded for every trade as a full 1-s path from the state-day mid arrays (MFE, MAE, time of each, time to exit), the same machinery as _early_cut/jn05w2_90.

## Books and their own brackets (engine tables STOPPTS/TARGETR)
K7 M7 U7 P7 H7 A7: stop 60, target 60 (1.0R). O7: stop 40, target 90 (2.25R). X3: stop 75, target 50. X4: stop 75, target 40. X5: stop 60, target 60. The fixed 60 stop applies except where the book's own bracket differs (O7, X3, X4 as listed). S7: not in LIVE_BOOKS, bracket to be taken from its DS7 line once enabled. X1 X2 X6 X7 X8: no engine definition found.

## Raw-trade table for Stage 1 (W-CF3): path and schema
/mnt/l2/l2vast/_rebuild/s0/<BOOK>/trades_raw.parquet + U.npy, built by code/th_pm/pm_rb_s0_build.py (smoke-tested on JL2 A7 202610). KEY = book7_sigts = '<book>_<signal second epoch>' (same convention as _early_cut meta columns book7 + sig_ts; join on (book7, sig_ts)). Columns: key, book, session (engine idx 0 asia 1 london 2 pre 3 nyam 4 nypm), sess, sig_ts, entry_ts, exit_ts, side, lots, entry_px, exit_px, exit_name, gross, net_fee, mfe, mae (pts, side-signed, from the 1-s mid path entry to exit), t_mfe, t_mae (s from entry), dur (s), path_off, path_len, month. Path pointer: U.npy float32, u = side*(mid - entry_px) per second; trade i path = U[path_off:path_off+path_len]. net_fee is at the engine fee $1.18/contract RT and base lots (x1.75 live; $4.84 repricing = lots x 3.66 per trade).

## Output (per book x session x window)
trades, mean per trade, net per week, max drawdown (daily equity), worst week, win rate, MFE and MAE distribution, time to MFE/MAE; windows L3M, L6M, HOLD, GAP, PRE, X' and all 43 months; columns at $4.84 RT and x1.75 live lots; the placebo for each number is the same book with entry times shifted by 11/23/37 days (nonsense rate printed beside). Scorer: code/th_pm/pm_rb.py (s0_book).

## Cells and budget
S0 cells TL3_RB_S0_<BOOK> (10) x 43 months = 430 cell-months; identity proofs TL3_RB_ID_<switch> on 202610 (inert setting equals JL2): about 14 cell-months. Priority order: L6M + HOLD months first (12 months x 7 = 84), then PRE, GAP, X' (217). At about 20 minutes per cell-month per worker (measured on this box) 315 cell-months is about 105 worker-hours, about 3.5 hours on a 30-worker pool.

## Status
Pending: layer-switch list and book mask from W-EV (asked 16 Nov); server 2 readiness from W-S2.
