# DS3_SPEC_TE6_st10m_n7_m3.0 - executability spec and identity test (D3X, 2026-10-26)

Research output for the Sim leader; NOT a live recommendation. No execution-server, chart or live change. Source: T-ENTRY (autopilot/DS3_TENTRY.md, group TE6); direct-L2 verdict **PASS** (mapped PASS). Replay: l2vast/ds3/code/x_te.py (own bars, own indicators, own bracket), compared with out/te/direct_tabs.pkl.

**Verdict: DELIVERABLE (entry and bracket are 1-minute-bar logic; no L2 at runtime). The execution layer (S10x1 slicing + XJ stop-join) is second-level timer logic, not sub-second, and is UNVALIDATED live.** Identity: 2382 library trades, 0.59% entry mismatch, 1.05% on entry + exit time + exit type, 0.92% with exit +/-2 min tolerance (limit 2%).

## 1. Rule (NT8)
- **Bars:** NQ 10-minute time bars, aligned to :00/:10/:20 ET (NT8 stamps bars with their END time), Globex template, label day 18:00-17:59 ET.
- **Indicator:** Supertrend (as tested, NOT the textbook flip test): ATR(n) with first value H-L and recursion ATR=(ATR[1]*(n-1)+TR)/n (n = 7); hl2=(H+L)/2; ub=hl2+3.0*ATR; lb=hl2-3.0*ATR; fub = ub if (ub<fub[1] or Close[1]>fub[1]) else fub[1]; flb = lb if (lb>flb[1] or Close[1]<flb[1]) else flb[1]; direction d starts +1; if d==+1 and Close<flb (CURRENT bar's band) then d=-1; if d==-1 and Close>fub (current bar) then d=+1.
- **Signal:** Signal = the bar on which d changes (edge only; +1 = buy, -1 = sell). No EMA filter. The signal is read on the CLOSED bar (Calculate OnBarClose).
- **Entry:** market order at the open of the next 1-minute bar after the signal bar closes (the next 1-min bar must exist, i.e. no gap). Signals whose bar's last minute starts in 15:00-17:59 ET are ignored. One open trade at a time per book: signals while the book is in a trade (or on the exit minute) are dropped, not queued. 10 lots as 10 x 1-lot market slices 2 s apart (S10x1_g2) in the direct pricing.
- **Exit / bracket:** stop-market 60 pt and limit target 60 pt (1.0R) OCO from the entry (rows: from the entry bar's open; direct replay: 240/240 ticks from each slice fill); stop exits are worked as touch-join for 3 s then market (XJ3). Flat at 16:55 ET (market at the close of the bar ending >= 16:55; early-close days at the final bar). If both levels fall in one 1-min bar the replay takes the stop (the library uses the 1-s tape).
- **Session window (ET):** entries 18:00-14:59 ET (signal bars ending in the 15:00-17:59 window are blocked; the lock engine also blocks entries 18:00-18:05 and 15:00-16:54). Flat by 16:55.
- **Order types:** MARKET entry (sliced), STOP-MARKET + LIMIT target OCO, MARKET time exit; stop-join is a timer that replaces the stop with a passive limit for 3 s (P9 mechanism, see autopilot/P9_NT8_SPEC.md; unvalidated live, needs OnMarketData bid/ask).
- **Lots / dollars:** 10 NQ lots, R = 10 x 60 x $20 = $12,000. Per-book locks (exact 1-s mark-to-market engine in the series): day -2R = -$24,000, +5R = +$60,000; give-back arm +2R = $24,000 keep 50%; week floor -12R = -$144,000; cap off. At the 14/14 scale (R = $16,800, 14 lots): -$33,600 / +$84,000 / arm $33,600 / week floor -$201,600.
- **Execution mode:** NT8 strategy on a 10-minute NQ chart (a 1-minute data series is needed for the entry and bracket), OnBarClose; own per-book lock group. With default Market/Native stop execution the realised cost is higher than the direct-L2 series assume.

## 2. Identity test (replay vs library trade rows, 2023-02-10..2026-10-16)
| check | n library | n replay | mismatches | % |
|---|---|---|---|---|
| entries (time, side) | 2382 | 2384 | 14 | 0.59 |
| entry + exit time + exit type | 2382 | 2384 | 25 | 1.05 |
| entry + exit type, exit within 2 min, pts within 0.5 | 2382 | 2384 | 22 | 0.92 |
Causes of the residual: stop/target both inside one 1-min bar (library resolves on 1-s data), exit stamps one minute apart, holiday early closes, and warm-up/seed differences early in the sample. The replay covers the base rows only; the S10x1 / XJ pricing (L2 queue model), the P9-style cost, and the lock engine of the series are not re-derived here.

## 3. Data, roll, holidays
Continuous front NQ, back-adjusted (MergeBackAdjusted in NT8); the indicators run continuously across days, so adjusted history matters; the book is flat 16:55-18:00 ET so no trade crosses a roll. Holidays and half days: no bars -> no trades; early closes (13:00/13:15 ET, Good Friday 09:15) flatten on the final bar. Data end of the 1-min file used here is 2026-10-16.

## 4. Position limits
10 lots, one position. With DS2 (10+10+7) the worst case is 37; other DS3 books add (lead's computation).

## 5. Fills and costs
Direct L2 replay (exec_engine_l2, queue model, 5 ms latency) of S10x1 entries and XJ3 stop exits, commission $4.84 RT; 2x-cost WF = 6,716/wk.

## 6. Backtest expectation (series l2vast/ds3/out/te/direct_daily.parquet column TE6_st10m_n7_m3.0, weekly $, 10 lots, exact locks)
| WF mean | WF SD | WF maxDD | WF CI | HOLD mean | HOLD Sharpe | 2023-04..2024-01 span | WF-PRE | trades/wk | win | avg win | avg loss | corr ST10 | corr HM10 | placebo (PRE) | MDE |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 8,749 | 35,698 | 197,422 | [2,653, 14,349] | 8,628 | 1.84 | 3,468 | 8,743 | 12.2 | 53% | 11,184 | -11,309 | 0.09 | -0.03 | 1.00 | 8,443 |

All T-ENTRY effects are below the MDE (screens, not established edges); DSR on the full 31k-trial ledger is near 0.

## 7. What could kill it
- Selection: best-of-191 cells; the series is the top of a screen whose predicted effect (+0.3 pt/trade) is below its MDE.
- Execution: the direct-L2 series assume 10x1 slicing and passive stop-join, unvalidated on the live copier; default Market/Native is worse.
- Bar/threshold details (current-bar band flip for Supertrend, first-bar ATR seed) must be reproduced exactly; a textbook Supertrend is a different system.
- Tie/ordering inside a 1-min bar and vendor-vs-NT8 bar differences.

## 8. Relation to the live WT10 book (V2: nothing re-tested under a new name)
WT10 = 10-min Wilder ATR14 x3.0 ratchet trail on Close (EMA off), same 60/60 bracket, signal blackout 09:00-09:58 and 15:00-17:59 ET. This cell differs in the band construction (median price, ratchet on previous close, flip on the current-bar band), ATR length (7), and in having no 09:00-09:58 blackout. Overlap (independent replay of both, whole sample): flip bars on the same 10-min bar and side 1979 of 4007 (within +/-1 bar 2521); trade entries sharing a 10-min bar and side with a WT10 entry 40% (within +/-1 bar 51%); unlocked weekly gross-pts correlation with WT10 0.52. It is a distinct rule of the same family, partly redundant with WT10: do not count it as independent of WT10 or of the other TE6 st10m cells.
