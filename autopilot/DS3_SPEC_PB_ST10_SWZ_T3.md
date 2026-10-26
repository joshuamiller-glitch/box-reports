# DS3_SPEC_PB_ST10_SWZ_T3 - executability spec and identity test (lead, 2026-10-26)

Research output for the Sim leader; NOT a live recommendation. No execution-server, chart or live change. Source: T-PULLBACK (autopilot/DS3_TPULLBACK.md; definitions l2vast/ds3/out/TPULLBACK_DEFS.md; prereg l2vast/ds3/prereg/TP_PB1.md). Replay: l2vast/ds3/code/x_pb.py (own bars, own indicators, own state machine, own 1-min bracket); library list: l2vast/ds3/code/x_pb_lib.py (tp_sig events -> te_core.gen_entries on the 1-s path).

**Status of the cell: CANDIDATE on the MAPPED basis only (fails placebo rank 0.93 < 0.95). The DIRECT L2 replay of the cell is NOT done (tp_direct is running); there is no direct verdict. The spec describes the rule exactly; it is not a statement that the rule has an edge.**

**Verdict on executability: DELIVERABLE (entry and bracket are 1-minute-bar logic with 5-min and 10-min aggregates built from the 1-minute bars; no L2 at runtime).** Identity: 6,027 library trades, 0.90% entry mismatch, 1.06% on entry + exit time + exit type, 1.05% with exit +/-2 min and 0.5 pt tolerance (limit 2%, as for the TE specs). The execution layer (10-lot slicing and stop-join) is the same second-level timer logic as the TE specs and is UNVALIDATED live.

## 1. Rule (NT8, OnBarClose on a 1-minute NQ series)
All indicator inputs are back-adjusted NQ (MergeBackAdjusted). Time is ET; bars are stamped with their END time in NT8. "Complete" aggregate bar: the 5-min (10-min) bucket whose last 1-minute bar has closed. Buckets are clock-aligned on the 18:00 ET session open (:00/:05/:10 ... ET), so they match NT8 time bars on a Globex template.

**1.1 Regime (direction d, evaluated on every 1-min bar from the latest COMPLETE 10-min bar):** Supertrend on 10-min bars, ATR length 10, multiplier 3.0, median price (H+L)/2. As tested (NOT the textbook flip test): ATR recursion ATR[0] = H-L, then ATR[i] = (ATR[i-1]*9 + TR[i])/10 (TR = max(H-L, |H-C[1]|, |L-C[1]|)); ub = hl2 + 3*ATR, lb = hl2 - 3*ATR; fub = ub if (ub < fub[1] or Close[1] > fub[1]) else fub[1]; flb = lb if (lb > flb[1] or Close[1] < flb[1]) else flb[1]; d starts +1; if d == +1 and Close < flb (CURRENT bar's band) then d = -1; if d == -1 and Close > fub (current bar) then d = +1. d = +1 -> long-only, d = -1 -> short-only; no value before the first complete 10-min bar = no trade. Any change of d disarms the setup (1.4).

**1.2 Swings and the pullback zone (5-min bars):**
- Fractal strength 2: a 5-min bar j is a swing HIGH if H[j] > H[j-1], H[j] > H[j-2], H[j] >= H[j+1], H[j] >= H[j+2] (strict on the left, non-strict on the right); swing LOW mirrored (L[j] < L[j-1], L[j] < L[j-2], L[j] <= L[j+1], L[j] <= L[j+2]). It is CONFIRMED when bar j+2 completes, and is usable from that moment (so the earliest use is the 1-min bar that completes bar j+2, nothing earlier: no look-ahead).
- State, updated in confirmation order (if a high and a low confirm on the same 5-min bar the high is processed first): lastSH = latest confirmed swing high; SLbeforeSH = the latest confirmed swing low at the moment lastSH was confirmed; lastSL = latest confirmed swing low; SHbeforeSL = the latest confirmed swing high at the moment lastSL was confirmed. Both legs are kept at all times; there is no "which came last" test (a stale high is still used until a newer high confirms).
- Impulse leg for longs: from SLbeforeSH up to lastSH, range R = lastSH - SLbeforeSH (no minimum size, no sign check). For shorts: from SHbeforeSL down to lastSL, R = SHbeforeSL - lastSL.
- ZONE edges (long): level = lastSH - 0.382*R (38.2% retrace, the touch level); floor = lastSH - 0.618*R (61.8% retrace, the void edge). Short: level = lastSL + 0.382*R; floor = lastSL + 0.618*R. Both are recomputed on every 1-min bar from the then-current swing state (the level can move when a new swing confirms).

**1.3 Touch (evaluated on each completed 1-min bar i, with i-1 its predecessor):** Long: Low[i] <= level[i] AND Low[i-1] > level[i-1] (edge: previous bar's low was above the previous level) AND (floor is undefined OR Low[i] >= floor[i]) - the touch is void if the bar already reached the 61.8% retrace. Short: High[i] >= level[i] AND High[i-1] < level[i-1] AND (floor undefined OR High[i] <= floor[i]). Level undefined (no swing pair yet) = no touch. A touch needs d != 0.

**1.4 Arming (W = 30 bars, first touch):** when a touch occurs and the setup is not armed, arm it on that bar; it stays armed for the touch bar and the following 30 1-minute bars (armed while i <= touchbar + 30). A touch while already armed does nothing; after the armed window ends or a trade fires, the next touch arms it again. A touch counter resets if more than 30 bars passed since the first touch of a series (it matters only for the unused "second touch" variant). A change of regime direction disarms immediately.

**1.5 Trigger T3 (evaluated on each completed 1-min bar while armed, INCLUDING the touch bar):** RSI(2) of 1-minute closes, Wilder: gain/loss EMA with alpha 0.5, no SMA seed (first value 0, EMA recursion from bar 0 of the series: u[i] = 0.5*max(dC,0) + 0.5*u[i-1], d[i] = 0.5*max(-dC,0) + 0.5*d[i-1], RSI = 100 - 100/(1 + u/max(d, 1e-9))). Long (d == +1): RSI(2) < 10. Short (d == -1): RSI(2) > 90. First bar that satisfies it = signal bar; the setup is then disarmed (one trade per arming).

**1.6 Entry:** market order at the open of the 1-minute bar after the signal bar (the next bar must exist, i.e. no gap). Signal bars whose start is 15:00-17:59 ET are ignored (the lock engine also blocks entries 18:00-18:05 and 15:00-16:54). One open trade at a time in the book: signals while in a trade (or on the exit minute) are dropped, not queued. 10 lots as 10 x 1-lot market slices 2 s apart in the direct pricing (the same S10x1 convention as the TE specs).

**1.7 Exit / bracket (DS2 bracket, fixed 60/60):** stop-market 60 pt and limit target 60 pt (1.0R) OCO from the entry price; stop exits worked as touch-join for 3 s then market (XJ3, P9 mechanism, unvalidated live). Flat at 16:55 ET (market at the close of the bar ending >= 16:55; early-close days at the final bar). Replay convention if both levels fall in one 1-min bar: the stop is taken (the library resolves it on the 1-s tape).

**1.8 Sessions:** all hours (entries 18:00-14:59 ET window as above); by hour the 6,027 library entries are 6% 00-02 ET, 22% 03-08, 8% 08-09, 38% 09-15 and 25% 18-23 ET. Long/short 49.6% / 50.4%. Exits: 49.3% target, 46.0% stop, 4.7% 16:55 time exit; median hold 65 min.

**1.9 Lots / dollars:** 10 NQ lots, R = 10 x 60 x $20 = $12,000. Per-book locks in the series (exact 1-s mark-to-market engine): day -2R = -$24,000, +5R = +$60,000; give-back arm +2R = $24,000 keep 50%; week floor -12R = -$144,000; cap off. At the 14/14 scale (R = $16,800): -$33,600 / +$84,000 / arm $33,600 / week floor -$201,600.

**1.10 Warm-up:** the indicators run continuously from the series start (2022-06-01); the first counted trade is 2023-02-10. The rule needs a confirmed swing high AND a confirmed swing low on the 5-min bars, a first complete 10-min bar, and RSI(2) seeded at 0. Measured start-date sensitivity (independent replay, trades from 2024-04-01, 4,856 trades): starting the indicators 4 days, 7 days, 14 days, 2 months or 3 months before 2024-04-01 reproduces the full-history trade list with 0 entry mismatches in all five cases. Recommended NT8 setting: load at least 30 days of 1-minute history (the 4-day result is a sample statement for this period, not a proof for every possible start); do NOT start the chart on the day.

## 2. Identity test (replay vs library trade rows, 2023-02-10..2026-10-16)
| check | n library | n replay | mismatches | % |
|---|---|---|---|---|
| entries (time, side) | 6027 | 6025 | 54 | 0.90 |
| entry + exit time + exit type | 6027 | 6025 | 64 | 1.06 |
| entry + exit type, exit within 2 min, pts within 0.5 | 6027 | 6025 | 63 | 1.05 |

Residual (54 library entries absent from the replay, 52 replay entries absent from the library; 16 of each have a same-side entry within 3 minutes, i.e. a one-bar timing difference): 31 of the 54 library-only entries fall inside a replay trade and 26 of the 52 replay-only entries inside a library trade, i.e. the rest is the one-trade-at-a-time busy rule cascading from a different exit minute (stop and target in the same 1-min bar, resolved on the 1-s tape in the library and stop-first in the replay; 16:55 and early-close stamps). The replay uses independently built bars (x_replay, 18:00-ET-anchored buckets) and an independent as-of rule for the 5-min and 10-min aggregates (usable from the bucket's final minute, else from the next 1-min bar); the library uses epoch-minute buckets. The replay covers the base rows only; the S10x1 / XJ pricing (L2 queue model), the P9-style cost and the series' lock engine are not re-derived here. Data end of the replay file is 2026-10-16.

Files: l2vast/ds3/out/xpb/PB_ST10_SWZ_T3_lib_trades.parquet (library trade list, 6,092 rows to 2026-10-23, the 6,027 above end 2026-10-16), PB_ST10_SWZ_T3_xpb_trades.parquet (replay), x_pb_identity.json, x_pb_causes_warmup.json.

## 3. Data, roll, holidays
Continuous front NQ, back-adjusted; the 5-min swings and the Supertrend run on adjusted prices, so adjusted history matters. The book is flat 16:55-18:00 ET so no trade crosses a roll. Holidays and half days: no bars -> no trades; early closes flatten on the final bar.

## 4. NT8 implementation notes (UNTESTED in NT8)
- Build the 5-min and 10-min bars from the 1-minute series inside one OnBarUpdate (bucket complete when the 1-minute bar ending on the bucket boundary closes). Do NOT rely on added 5-min/10-min data series: the callback order of a 1-minute and a 5-minute series at the same timestamp decides whether the aggregate is complete on the signal bar, and the as-of rule here is "complete bucket only".
- The Supertrend flip uses the CURRENT bar's band (as tested); an indicator from the NT8 library is a different system.
- The swing state needs all confirmed swings back to the start of the warm-up; a stale swing is used until replaced, by design.

## 5. Position limits
10 lots, one position. With DS2 (10+10+7) the worst case is 37; other DS3 books add (lead's computation, see DS3_PORTFOLIO).

## 6. Backtest expectation (MAPPED basis, series l2vast/ds3/out/SERIES, 10 lots, exact locks; from autopilot/DS3_TPULLBACK.md)
| trades/wk | win | avg win | avg loss | PRE $/wk | WF $/wk | HOLD $/wk | HOLD Sharpe | 2023-04..2024-01 $/wk | long / short WF $/wk | corr ST | placebo rank | paired vs ST pts/trade [CI] (MDE) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 26.97 | 0.52 | $11,000 | -$10,795 | 6,067 | 12,067 | 18,414 | 2.38 | 2,530 | 9,893 / 2,174 | 0.45 | 0.93 | +13.4 [10.5, 16.3] (4.0, n 805) |

Trades/wk after the lock engine's entry blocks is lower than the about 31/wk of the raw list (6,027 trades over about 192 weeks, i.e. about 31/wk). Verdict CANDIDATE (mapped): failed placebo >= 0.95. The paired-vs-ST figure is the pullback entry's own advantage (see DS3_TPULLBACK.md); dWK vs ST is -$2,445/wk [-12,420, 7,176] at equal lots.

## 7. What could kill it
- Selection: one of 447 pullback cells scored (best-of-N; 49 of 447 have a paired CI above 0 against about 11 expected by chance); the placebo rank 0.93 is below the 0.95 bar.
- Pricing: MAPPED basis (path-table mapping); the direct L2 replay (queue model) is pending and mapped trailing/stop results have been overstated by 1.2-1.5 pts/trade in other tests (STRUCT48 SO2). No direct verdict exists.
- Execution: the 10x1 slicing and passive stop-join are unvalidated on the live copier; default Market/Native stops are worse.
- Rule details that must be reproduced exactly: the current-bar Supertrend flip, the strict/non-strict fractal comparison, the stale-swing state, the touch edge condition on the previous level, the RSI(2) seed, and the as-of aggregate rule.
- NT8 multi-series callback order (section 4).

## 8. Relation to other books (V2: nothing re-tested under a new name)
Same ST10 regime definition as the TE6 centre (10-min Supertrend, n 10 / mult 3.0, median price), so its direction overlaps ST10 and the TE6 st10m cells by construction; the entry is a pullback to a swing retrace zone with an RSI(2) trigger, not a flip entry. Correlation to ST10 weekly P&L 0.45. Not independent of the other PB_*_ST10_* cells or of the PB_HMA55_SWZ_T3 cell (they share the swing zone and the trigger).
