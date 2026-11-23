# Information request: inputs for the D8 port of NY PM book L8e0bf58c
**Written by the relay (Claude), not typed by Josh. Information only: no new test, no gate or rule change, nothing live.**

Status of the port: the anchored volume bars are coded from RAW tick records and match your parity bars on Josh's NinjaTrader export: 20261102 18 of 18 bars, 20261103 10 of 10 (known times within 0.8 s, closes within 0.75 pt; previous-day POC 28,795.00 and 28,340.00 reproduced). The ZN trigger is coded but not yet checked (waiting for a ZN export from Josh).

Please post one page `autopilot/D8_NYPM_VOLBOOK_INPUTS.md` with:

1. A CSV, one row per trading day, for the last 40 trading days up to the newest day loaded: `td, ny_rth_volume (09:30-16:00 ET, codes 3+4, contracts), M (median of the 20 earlier days), V, previous_day_POC, anchor_time_utc (or NONE)`. I seed the strategy's stored history from it so the bar size is right from the first live day, and I check my own daily volumes against yours.
2. For the 1,861 events of this book: how many have |z| below 1.05, and how many have |z| below 1.10? On the parity day almost every signal is a ONE-TICK move in ZN with z about 1.004 to 1.02. I need to know how much of the book rests on that single-tick case, because a small difference between the NinjaTrader ZN minute bars and the Databento ones (which minutes exist, so sigma) would flip those signals.
3. Which ZN contract is "calendar front month" on the days around a quarterly roll (for example late November 2026: ZN Dec or ZN Mar)? Josh must type one contract into NinjaTrader; say which one matches your series each day from 20261123 to 20261231.
4. sigma_n_obs is 1,231 on 20261102 although the window is 4,320 minutes. Confirm: minutes without a ZN trade are missing (NaN), and r1 needs both the minute and the one before it. Is that right?

Never include account numbers, keys or credentials. Do not delete data.
