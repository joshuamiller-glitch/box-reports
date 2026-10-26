# DS3_SPEC_TB7_ORBNY_k3_P60_N - executability spec and identity test (D3X, 2026-10-26)

Research output for the Sim leader; NOT a live recommendation. No execution-server, chart or live change. Written by D3X from the box's own independent replay (l2vast/ds3/code/x_replay.py, x_tb.py, x_locks.py); all numbers re-derived from the 1-minute Databento files.

**Verdict: DELIVERABLE** (NT8 1-minute data only, no L2, no sub-second timing). Identity: library vs the replay = 0 mismatching trades of 1245 (0.00%) when the replay uses the library's own hindsight data-gap flag; against the NT8-CAUSAL rule written below the mismatch is 0.00% of trades (0 missing entries, 0 exit/price differences; limit 2%).

## 1. Book in one line

TB7_ORBNY_k3_P60_N: track verdict **CANDIDATE** (T-B, prereg 7); family ORBNY, 3-minute bars, stop fixed 60.00 pt, exit code P60.

## 2. Rule an NT8 strategy must reproduce

- **Instrument / bars:** NQ (front month, continuous, MergeBackAdjusted) 3-minute TIME bars, bars aligned to :00/:03/:06 ET (NT8 stamps a bar with its END time: bar start = Time[0] - 3 min). Session template: CME US Index Futures full ETH (18:00-17:00 ET), early-close days per CME calendar.
- **Indicator / state:** Opening range OR: over the bars whose START is in [09:30, 09:30+L) ET of the label day (label day runs 18:00 ET to 17:59 ET): ORhi = max High, ORlo = min Low. Day is tradable only if at least max(1, L/(2*3)) OR bars exist. L and buf come from the monthly parameter schedule below (grid L in {15,30,60} min x buf in {0,5,10} pts; centre L=30, buf=5).
- **Signal:** State s (reset to 0 at 18:00 ET each label day). On each CLOSED bar whose start is in [09:30+L, 16:30+L): if Close > ORhi + buf then s=+1; else if Close < ORlo - buf then s=-1; otherwise s unchanged (s is sticky until the end of the label day or a reversal). Target position = s.
- **Entry:** Flat and s != 0 and s != blocked, decided at the close of bar i: market order at the open of bar i+1 (modelled fill open +/- 0.995 pt) if bar i+1 START is before 15:00 ET or at/after 18:05 ET and bar i is not the force-flat bar. Reversal (s flips against the position): market exit at the open of bar i+1 and a market entry the same bar in the new direction.
- **Exit / stop:** (a) Protective stop-market 60.00 pt from the OPEN of the entry bar (not from the fill), placed as soon as the entry bar opens, active including the entry bar; modelled fill = stop -/+ 1.01 pt, gap through the stop fills at the bar open -/+ 1.01 pt; stop is tested on the 3-minute bar High/Low (stop first inside a bar). (b) Signal reversal (above). (c) Force-flat: market exit at the close of the bar that contains 16:55 ET (the first bar whose end is >= 16:55, i.e. the 16:54-16:57 bar, exit about 16:57 ET), and on CME early-close days at the close of the final bar (12:57-13:00 or 13:12-13:15). After a stop-out, no new entry in the stopped direction until s changes side (the sticky s means: no re-entry that label day unless it reverses). No target. One position, one entry per signal.
- **Session window (ET):** Entry decisions only on bars that START before 15:00 ET or at/after 18:05 ET (in practice the book trades the NY cash session after the opening range; the 18:05+ bars never fire because s resets to 0 each label day and the OR does not exist yet). Flat by 16:57 ET (16:55 boundary bar close). Median holding time about 138 min.
- **Order types:** entries and signal exits MARKET (sent on bar close, filled at next bar open in the model, 0.995 pt adverse = 4 ticks of cost already counted); protective STOP-MARKET (modelled 1.01 pt through the stop); no limit orders, no target; Calculate = OnBarClose; one position at a time; one stop order working at all times while in position.
- **Lots / dollars:** scored at 10 NQ lots with R = 12,000 (= lots x nominal stop 60 pt x $20 = 12,000). Per-book locks (closed-trade approximation, see 8): day -2R = -$24,000, day +5R = +$60,000, give-back arm +2R = +$24,000 (once the day's realised P&L has peaked at or above +2R, stop for the day when realised falls to 50% of that peak), week floor -12R = -$144,000, cap off. At the 14/14 scale (R = 16,800) the same book is 14.0 lots with -2R = -$33,600, +5R = +$84,000, give-back arm $33,600, week floor -$201,600. DS2 sizing (ST10/HM10 = 10 lots, WT7 = 7 lots) is the reference.
- **Execution mode:** NT8 strategy on a 3-minute NQ chart, Calculate OnBarClose, tick-replay off, own per-book lock group (does not net with or lock DS2 books); can run in the same account as DS2.

### Monthly parameter schedule (walk-forward re-fit; REQUIRED to reproduce the series)

At the first trading day of each calendar month the box computes, for each grid point, the sum of per-lot net dollars (pts x $20 - $4.84) of that point's trades ENTERED in the previous 6 calendar months and CLOSED before the 1st of the month, picks the argmax; if the best-covered grid point has fewer than 20 such trades it uses the centre point. The 3x3 grid is [(15.0, 0.0, 570.0), (15.0, 5.0, 570.0), (15.0, 10.0, 570.0), (30.0, 0.0, 570.0), (30.0, 5.0, 570.0), (30.0, 10.0, 570.0), (60.0, 0.0, 570.0), (60.0, 5.0, 570.0), (60.0, 10.0, 570.0)], centre index 4 = (30.0, 5.0, 570.0). The strategy reads the chosen tuple from a small parameter file (one line per month; the box publishes the next month's line on the last weekend of the month). A second independent implementation of the re-fit (x_tb.refit) reproduces all 45 library schedule months with 0 differences. Last six months of the schedule (month: grid index): 202605: 5, 202606: 5, 202607: 5, 202608: 8, 202609: 8, 202610: 8. The re-fit is part of the rule: fixed-centre-parameter WF-PRE mean is $2,023/wk against $11,804/wk re-fitted (row fields fixed_center_WFPRE_mean, WFPRE_mean); if the fixed book is not clearly worse, the schedule file can be dropped and the centre used.

## 3. Identity test (box replay vs library series)

| check | n library | n replay | mismatches | % |
|---|---|---|---|---|
| library trades (stitched, pre-lock) vs replay with library gap flag | 1245 | 1245 | 0 | 0.00 |
| NT8-causal rule vs library (entry time, side, exit time, pts within 0.5) | 1245 | 1245 | 0 | 0.00 |
| locked daily P&L series, replay vs library (max abs daily difference, $) | 953 days | 953 days | hindsight 7.3e-10; causal 0 | - |
| monthly parameter schedule regenerated vs library | 45 months | 45 | 0 | 0.0 |

Cause of the causal-rule differences: the library flagged 'force-flat' on any bar followed by a data gap (a bar missing because no trade printed) and on the bar before CME early closes. Early closes are calendar-known and are in the NT8 rule (115 early-close days since 2013 in the data; hard-code the CME holiday calendar); mid-session minutes with no trade are not knowable in advance, so the causal rule closes at the first bar after the gap at its open (and does not skip an entry placed before the gap). No differences.

Replay inputs: Databento 1-minute continuous .v.0 (volume roll) files, back-adjusted at each roll by the opening gap; own loader, own ET calendar (pandas tz), own indicator code (online bar-by-bar state machine, no vectorised library code). The monthly schedule table is an input; its regeneration is tested above. The verdict follows the directive rule (mismatch > 2% of trades = not deliverable).

## 4. Data, instrument, contract, roll

- Instrument NQ (E-mini Nasdaq-100, $20/pt, tick 0.25), front quarterly contract; research data are Databento 1-min .v.0 (volume-leader roll) back-adjusted. In NT8 use the continuous NQ contract with merge policy MergeBackAdjusted (the strategy must see the same back-adjusted history; the ORBNY state is reset daily). The book is flat from 16:55 ET to 18:05 ET every day, so no trade is carried across a roll; replay trades spanning a roll bar: 0 of 1245.
- NT8 time bars are built from last-trade ticks, as Databento OHLCV-1m is; minutes without a trade have no bar in either. Expect small OHLC differences from vendor tick filtering; the replay is 1-minute-bar based so any intrabar order of high vs low is unknown (stop is assumed to be hit before any favourable move inside the same bar, entry bar included).
- Holidays and half days: no entry when no bars exist; on CME early-close days (13:00 or 13:15 ET close) the book is force-flat at the final bar's close (NT8: either Exit-on-session-close, which fires ~30 s earlier, or a bar-time check) - hard-code the CME equity holiday calendar; Juneteenth, Thanksgiving Friday, Dec 24, Jul 3 appear in the sample. Unplanned halts (e.g. the 2025-01-09 national day of mourning) fall under the data-gap rule.

## 5. Fills and costs assumed

Commission+exchange $4.84 per contract round trip; market orders 0.995 pt adverse each side (live cost model); stop-market 1.01 pt through the stop; gaps fill at the open. No limit orders and no trade-through assumptions. Under the live model costs are already inside the series; the row's 2x-cost sign test is positive.

## 6. Position-limit interaction with DS2

One position at a time, so peak lots from this book = 10 NQ. DS2 ST10/HM10/WT7 can hold 10+10+7 = 27; worst case concurrent = 37 (limit 50; other DS3 books add to this and are counted by the lead in DS3_PORTFOLIO). Margin proxy: 10 NQ intraday only (flat before 17:00 ET) - day-margin applies, no overnight margin.

## 7. Backtest expectation (replayed: closed-trade per-book locks, 142 WF weeks 2024-02..2026-10, live cost)

| WF mean/wk | SD/wk | maxDD (weekly) | worst week | trades/wk (kept) | win rate | avg win | avg loss | IS 2023-02..2024-01 mean/wk | HOLD 2025-07+ mean/wk | L8W mean/wk |
|---|---|---|---|---|---|---|---|---|---|---|
| 6,866 | 60,970 | 452,643 | -99,595 | 6.1 | 32% | 27,955 | -11,666 | -2,341 | 1,319 | 3,070 |

Track row (same series): WF mean 6,866, SD 60,970, maxDD 465,093, holdout 1,319, 2023-04..2024-01 span 300 (sign 1), placebo rank 1.0, MDE 14,334/wk, CI of mean [-2,899, 16,425]. Weekly corr: ST10 0.14, HM10 0.22, ST10+HM10 pair 0.21. Unlocked (no per-book locks) WF-PRE mean $10,573/wk vs locked $11,804/wk.

### 7b. EXACT-lock expectation (supersedes the closed-trade numbers in 7; series l2vast/ds3/out/T-B/EXACT_TB7_ORBNY_k3_P60_N_1x.parquet, lock engine = mark-to-market, from the lead)

| WF mean/wk (exact) | WF SD | WF maxDD | WF Sharpe | HOLD mean | HOLD Sharpe | L8W mean | WF-PRE mean | IS mean | span 2023-04..2024-01 | WF unlocked (exact engine, no locks) | WF at 1.5x cost | WF at 2x cost | trades/wk | lots / peak lots |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6,074 | 47,887 | 392,931 | 0.91 | 4,812 | 0.69 | -5,281 | 7,137 | -877 | -137 | 6,121 | 5,033 | 3,873 | 6.0 | 10.0 / 20.0 |

## 8. Locks, and what the series does and does not contain

The series uses the track's CLOSED-TRADE approximation of the per-book locks (day realised -2R/+5R, give-back arm 2R keep 50%, week floor 12R; the check happens before each entry using already closed trades). The NT8 implementation would measure the day's P&L mark-to-market while a position is open (the exact engine l2vast/pairP2/firm/riskeng_pb.py does that for DS2), so the live lock behaviour differs from the closed-trade series in 7; the lead has re-scored the book with the exact MTM engine (7b), and 7b is the expectation to use. The lock arithmetic itself was re-implemented here (x_locks.py) and reproduces the library daily series to 1e-9 dollars on the library trades.

## 9. What could kill it

- Opening-range breakouts at the NY open have been DEAD in earlier STRUCT48 cells (T3.2 ORB NY fails holdout); this cell is the 3-minute, re-fitted version and its holdout (2025-07+) mean is thin relative to WF-PRE.
- Win rate about one third: long losing streaks at 60 pt stops (-$12k per loss at 10 lots) are normal; the week floor (12R = $144k) is wide.
- Edge depends on the per-book locks and on the monthly re-fit (see 2 and the unlocked / fixed-centre numbers in 7); a drift in either (e.g. the exact MTM lock engine) can remove most of the mean.
- Sample: the weekly mean is below the MDE for 80% power on 142 weeks; the 2023-04..2024-01 span and IS mean must agree with the sign: IS = -2,341/wk, span = 300/wk.
- Intrabar uncertainty: stop-vs-favourable ordering inside a bar is unknown (assumed adverse), real fills for market orders at the bar open may be worse than 0.995 pt in fast markets.
- NT8 vs vendor bars: any systematic difference in bar construction (late prints, session boundaries) changes Renko/ORB levels; a one-week Sim side-by-side with this replay should show the same entries; mismatch above 2% of trades in Sim means the NT8 code deviates.
