# nyam-two-generic-book-specs (information only, 2026-11-22 ~22:00Z)

Written by the relay (Claude), not typed by Josh. Information / plumbing only: no new tests, no gate or rule change.

Context: D8 Asia compiled in NinjaTrader today; Josh's NT8 / CQG export for td 20261110 reproduced the box's Asia bars and signals (vol_2600 22 of 22 bars, tick_5000 5 of 5, frenko_40 66 of 66, Lb0e6dfa3 11 of 11 signals, the J502 event with all 10 flags). The NY AM stack TL3_ALN_NY_STKd8b76ecd35 is being coded now, bare first. Two of its five books only have a GENERIC AUTO BLOCK in D8_BUILD_SPEC.md and no signals on either parity day. Please, with their own agent now (almost no compute):

1. Lbb254083 (renko_80 + trig_xmarket_fx against_6J {"w": 15, "thr": 1.5}, bracket 45/45): a hand-written AUTO:BOOK block like the J502 one: the exact formula (which 6J series: 1-minute closes of the front month? return window, sigma window and minimum count, shift, sign convention of "against", level vs edge, what happens on missing minutes / contract change), bar rule (classic renko, B = max(2, round(80 x s_rng)), reversal 2B?), sides traded, and an independent re-implementation check against the engine events.
2. L8f11883e (time_m_20 + trig_levels_session_hl retest {"M": 10, "tol": 0.5}, bracket 30/90): the same: line list and when each line becomes known, u used by tol (plain 5.0 or native), the break-edge memory, T0 lookup, sides, and the re-implementation check.
3. For both: parity pages for the TWO MOST RECENT NY AM sessions on or before td 20261110 that have at least 2 signals each (bars, signals, trades, INPUTS incl. the 6J minute closes / line values used per event), named D8_PARITY_<id>_<td>.md.
4. For Lf0346d55 (top-of-book OFI) and L8cfda948 (block-print delta): on the parity page of td 20261110, add per-bar the feature value x, xs, sd and y for the NY AM bars, so the port can be checked bar by bar; and for L8cfda948 say how one aggressor order that fills against several resting orders appears in the raw MBO trade records (one record with the total size, or one record per resting order), because NinjaTrader's feed shows about 17% more trade ticks than the tape for the same session.

Research only. Nothing here touches the execution server, any live chart, credentials, spend or data deletion.
