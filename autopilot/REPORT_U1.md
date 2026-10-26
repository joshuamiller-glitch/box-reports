# REPORT U1 - pair-complement sleeve (trades only when the pair is flat)

**NO - degenerate: the live pair has an open position in 57-81% of clean-window days at every 30-minute slot from 18:30 to 16:30 ET (minimum 26% at slot 34 = 10:30 ET), so the only 'pair-flat' slots (open position in < 15% of days) are 18:00-18:30 ET and the post-close slots. The 2013-22 development screen has 2 cells (slot 0 variants U and C), none eligible (>= 300 trades, >= 7/10 years; mean Sharpe 0.00 because the 18:00 slot is one bar after the maintenance break). FOUND 0.**

Pre-registered in PREREG_AUTOPILOT.md (STRUCTURAL BATCH U1-U3, 2026-10-16T15:03Z). Pair-flat slot rule: ET 30-min slot (since 18:00) where the live pair (ROWS_corrected_engine.parquet) has an open position in < 15% of business days 2023-08-01..2025-07-31 (clean window only). Sleeve: time-of-day drift on NQ ES RTY (U: sign of the 2013-22 mean slot return; C: continuation/reversal after the prior bar) for the flat slots, 1-bar hold, 1 tick/side + $4.36 RT.

Share of clean-window days with a pair position open at the start of each slot (slot 0 = 18:00 ET): 0:0.00, 1:0.57, 2:0.72, 3:0.78, 4:0.79, 5:0.78, 6:0.78, 7:0.77, 8:0.79, 9:0.78, 10:0.80, 11:0.80, 12:0.81, 13:0.81, 14:0.81, 15:0.80, 16:0.80, 17:0.78, 18:0.80, 19:0.78, 20:0.80, 21:0.79, 22:0.78, 23:0.80, 24:0.80, 25:0.79, 26:0.78, 27:0.74, 28:0.76, 29:0.76, 30:0.77, 31:0.67, 32:0.26, 33:0.65, 34:0.63, 35:0.69, 36:0.68, 37:0.70, 38:0.72, 39:0.67, 40:0.68, 41:0.69, 42:0.71, 43:0.59, 44:0.46, 45:0.40, 46:0.00, 47:0.00

Reading: the pair is so persistently in the market (HM/ST hold 1-2 hours per trade, several trades per day, 5/7 books active through the session) that a time-based complement does not exist; the complement would have to be defined by state (e.g. day lock, week floor) which is not observable ex ante and is the domain of the lock/risk-switch families already tested (B15, B16, C6-N1). Executability: n/a.

DONE U1
