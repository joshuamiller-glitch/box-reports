# DS3_SPEC_TB1_ST_k15_P60_N - executability spec and identity test (D3X, 2026-10-26)

Research output for the Sim leader; NOT a live recommendation. No execution-server, chart or live change. Written by D3X from the box's own independent replay (l2vast/ds3/code/x_replay.py, x_tb.py, x_locks.py); all numbers re-derived from the 1-minute Databento files.

**Verdict: DELIVERABLE** (NT8 1-minute data only, no L2, no sub-second timing). Identity: library vs the replay = 0 mismatching trades of 4135 (0.00%) when the replay uses the library's own hindsight data-gap flag; against the NT8-CAUSAL rule written below the mismatch is 0.02% of trades (0 missing entries, 1 exit/price differences; limit 2%).

## 1. Book in one line

TB1_ST_k15_P60_N: track verdict **CANDIDATE** (T-B, prereg 1); family ST, 15-minute bars, stop fixed 60.00 pt, exit code P60.

## 2. Rule an NT8 strategy must reproduce

- **Instrument / bars:** NQ (front month, continuous, MergeBackAdjusted) 15-minute TIME bars aligned to the hour (bars at :00/:15/:30/:45 ET). NT8 stamps a bar with its END time.
- **Indicator / state:** Supertrend(period P, multiplier M) from the monthly schedule (grid P in {5,10,20} x M in {1.5,2.5,3.5}; centre P=10, M=2.5): ATR = Wilder ATR(P) (seed = SMA of the first P true ranges), median price hl2=(H+L)/2, ub=hl2+M*ATR, lb=hl2-M*ATR; final bands ratchet: fub=ub if (ub<fub[-1] or Close[-1]>fub[-1]) else fub[-1]; flb=lb if (lb>flb[-1] or Close[-1]<flb[-1]) else flb[-1]; direction d=+1 if Close>fub[-1], -1 if Close<flb[-1], else unchanged. State is NOT reset at the day boundary (runs continuously on the back-adjusted series; warm-up 3 months is plenty).
- **Signal:** Target position = d (always long or short once warm).
- **Entry:** Flat and d != 0 and d != blocked at the close of bar i: market order at the open of bar i+1 (modelled open +/- 0.995 pt) if bar i+1 START is before 15:00 ET or at/after 18:05 ET, and bar i is not the force-flat bar. A flip of d: market exit at the open of bar i+1 and market entry the same bar in the new direction.
- **Exit / stop:** (a) Protective stop-market 60.00 pt from the OPEN of the entry bar; modelled fill = stop -/+ 1.01 pt, gap fills at the bar open -/+ 1.01 pt; tested on the 15-min High/Low (stop first inside a bar). (b) Supertrend flip. (c) Force-flat: market exit at the close of the bar that contains 16:55 ET (first bar with end >= 16:55) and on CME early-close days at the final bar's close; the book is FLAT overnight (it re-enters at 18:05 ET or later if d still points one way and 18:05 <= start; blocked is cleared when d != blocked). (d) Data gap: if a bar opens later than one bar after the previous bar while a position is open, close at that bar's open. After a stop-out no new entry in the stopped direction until d flips. No target.
- **Session window (ET):** Entry bars must START before 15:00 ET or at/after 18:05 ET (i.e. 18:05-14:59 ET: Asia, London and NY). Flat by the 16:55 boundary bar close. Median holding time about 165 min.
- **Order types:** entries and signal exits MARKET (sent on bar close, filled at next bar open in the model, 0.995 pt adverse = 4 ticks of cost already counted); protective STOP-MARKET (modelled 1.01 pt through the stop); no limit orders, no target; Calculate = OnBarClose; one position at a time; one stop order working at all times while in position.
- **Lots / dollars:** scored at 10 NQ lots with R = 12,000 (= lots x nominal stop 60 pt x $20 = 12,000). Per-book locks (closed-trade approximation, see 8): day -2R = -$24,000, day +5R = +$60,000, give-back arm +2R = +$24,000 (once the day's realised P&L has peaked at or above +2R, stop for the day when realised falls to 50% of that peak), week floor -12R = -$144,000, cap off. At the 14/14 scale (R = 16,800) the same book is 14.0 lots with -2R = -$33,600, +5R = +$84,000, give-back arm $33,600, week floor -$201,600. DS2 sizing (ST10/HM10 = 10 lots, WT7 = 7 lots) is the reference.
- **Execution mode:** NT8 strategy on a 15-minute NQ chart, Calculate OnBarClose, tick-replay off, own per-book lock group (does not net with or lock DS2 books); can run in the same account as DS2.

### Monthly parameter schedule (walk-forward re-fit; REQUIRED to reproduce the series)

At the first trading day of each calendar month the box computes, for each grid point, the sum of per-lot net dollars (pts x $20 - $4.84) of that point's trades ENTERED in the previous 6 calendar months and CLOSED before the 1st of the month, picks the argmax; if the best-covered grid point has fewer than 20 such trades it uses the centre point. The 3x3 grid is [(5.0, 1.5), (5.0, 2.5), (5.0, 3.5), (10.0, 1.5), (10.0, 2.5), (10.0, 3.5), (20.0, 1.5), (20.0, 2.5), (20.0, 3.5)], centre index 4 = (10.0, 2.5). The strategy reads the chosen tuple from a small parameter file (one line per month; the box publishes the next month's line on the last weekend of the month). A second independent implementation of the re-fit (x_tb.refit) reproduces all 45 library schedule months with 0 differences. Last six months of the schedule (month: grid index): 202605: 1, 202606: 2, 202607: 4, 202608: 2, 202609: 2, 202610: 7. The re-fit is part of the rule: fixed-centre-parameter WF-PRE mean is $6,682/wk against $4,838/wk re-fitted (row fields fixed_center_WFPRE_mean, WFPRE_mean); if the fixed book is not clearly worse, the schedule file can be dropped and the centre used.

## 3. Identity test (box replay vs library series)

| check | n library | n replay | mismatches | % |
|---|---|---|---|---|
| library trades (stitched, pre-lock) vs replay with library gap flag | 4135 | 4135 | 0 | 0.00 |
| NT8-causal rule vs library (entry time, side, exit time, pts within 0.5) | 4135 | 4135 | 1 | 0.02 |
| locked daily P&L series, replay vs library (max abs daily difference, $) | 953 days | 953 days | hindsight 2.2e-09; causal 4150 | - |
| monthly parameter schedule regenerated vs library | 45 months | 45 | 0 | 0.0 |

Cause of the causal-rule differences: the library flagged 'force-flat' on any bar followed by a data gap (a bar missing because no trade printed) and on the bar before CME early closes. Early closes are calendar-known and are in the NT8 rule (115 early-close days since 2013 in the data; hard-code the CME holiday calendar); mid-session minutes with no trade are not knowable in advance, so the causal rule closes at the first bar after the gap at its open (and does not skip an entry placed before the gap). Differences listed (entry epoch, side, library pts, causal pts, library exit type, causal exit type): [((1764286200, 1), 23.760000000002037, 44.51000000000204, 3, 6)]

Replay inputs: Databento 1-minute continuous .v.0 (volume roll) files, back-adjusted at each roll by the opening gap; own loader, own ET calendar (pandas tz), own indicator code (online bar-by-bar state machine, no vectorised library code). The monthly schedule table is an input; its regeneration is tested above. The verdict follows the directive rule (mismatch > 2% of trades = not deliverable).

## 4. Data, instrument, contract, roll

- Instrument NQ (E-mini Nasdaq-100, $20/pt, tick 0.25), front quarterly contract; research data are Databento 1-min .v.0 (volume-leader roll) back-adjusted. In NT8 use the continuous NQ contract with merge policy MergeBackAdjusted (the strategy must see the same back-adjusted history; the ST state is continuous across days, so adjusted history matters here). The book is flat from 16:55 ET to 18:05 ET every day, so no trade is carried across a roll; replay trades spanning a roll bar: 13 of 4135.
- NT8 time bars are built from last-trade ticks, as Databento OHLCV-1m is; minutes without a trade have no bar in either. Expect small OHLC differences from vendor tick filtering; the replay is 1-minute-bar based so any intrabar order of high vs low is unknown (stop is assumed to be hit before any favourable move inside the same bar, entry bar included).
- Holidays and half days: no entry when no bars exist; on CME early-close days (13:00 or 13:15 ET close) the book is force-flat at the final bar's close (NT8: either Exit-on-session-close, which fires ~30 s earlier, or a bar-time check) - hard-code the CME equity holiday calendar; Juneteenth, Thanksgiving Friday, Dec 24, Jul 3 appear in the sample. Unplanned halts (e.g. the 2025-01-09 national day of mourning) fall under the data-gap rule.

## 5. Fills and costs assumed

Commission+exchange $4.84 per contract round trip; market orders 0.995 pt adverse each side (live cost model); stop-market 1.01 pt through the stop; gaps fill at the open. No limit orders and no trade-through assumptions. Under the live model costs are already inside the series; the row's 2x-cost sign test is positive.

## 6. Position-limit interaction with DS2

One position at a time, so peak lots from this book = 10 NQ. DS2 ST10/HM10/WT7 can hold 10+10+7 = 27; worst case concurrent = 37 (limit 50; other DS3 books add to this and are counted by the lead in DS3_PORTFOLIO). Margin proxy: 10 NQ intraday only (flat before 17:00 ET) - day-margin applies, no overnight margin.

## 7. Backtest expectation (replayed: closed-trade per-book locks, 142 WF weeks 2024-02..2026-10, live cost)

| WF mean/wk | SD/wk | maxDD (weekly) | worst week | trades/wk (kept) | win rate | avg win | avg loss | IS 2023-02..2024-01 mean/wk | HOLD 2025-07+ mean/wk | L8W mean/wk |
|---|---|---|---|---|---|---|---|---|---|---|
| 10,962 | 78,927 | 350,107 | -142,078 | 16.3 | 31% | 21,311 | -8,774 | 2,692 | 17,555 | -6,235 |

Track row (same series): WF mean 10,933, SD 78,905, maxDD 384,581, holdout 17,494, 2023-04..2024-01 span -2,415 (sign -1), placebo rank 1.0, MDE 18,551/wk, CI of mean [-1,352, 23,887]. Weekly corr: ST10 0.40, HM10 0.26, ST10+HM10 pair 0.40. Unlocked (no per-book locks) WF-PRE mean $2,065/wk vs locked $4,838/wk.

### 7b. EXACT-lock expectation (supersedes the closed-trade numbers in 7; series l2vast/ds3/out/T-B/EXACT_TB1_ST_k15_P60_N_1x.parquet, lock engine = mark-to-market, from the lead)

| WF mean/wk (exact) | WF SD | WF maxDD | WF Sharpe | HOLD mean | HOLD Sharpe | L8W mean | WF-PRE mean | IS mean | span 2023-04..2024-01 | WF unlocked (exact engine, no locks) | WF at 1.5x cost | WF at 2x cost | trades/wk | lots / peak lots |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 7,737 | 60,467 | 403,523 | 0.92 | 11,521 | 1.23 | 10,948 | 4,204 | 1,997 | -3,101 | 7,388 | 4,577 | 2,236 | 14.2 | 10.0 / 20.0 |

## 8. Locks, and what the series does and does not contain

The series uses the track's CLOSED-TRADE approximation of the per-book locks (day realised -2R/+5R, give-back arm 2R keep 50%, week floor 12R; the check happens before each entry using already closed trades). The NT8 implementation would measure the day's P&L mark-to-market while a position is open (the exact engine l2vast/pairP2/firm/riskeng_pb.py does that for DS2), so the live lock behaviour differs from the closed-trade series in 7; the lead has re-scored the book with the exact MTM engine (7b), and 7b is the expectation to use. The lock arithmetic itself was re-implemented here (x_locks.py) and reproduces the library daily series to 1e-9 dollars on the library trades.

## 9. What could kill it

- Supertrend trend-follow at 15-minute bars: whipsaw regimes (range days) lose repeatedly; 2026 carries ~44% of the WF gain (year-share check).
- State is continuous across days: a wrong back-adjustment or a missed roll in NT8 changes the band path.
- Edge depends on the per-book locks and on the monthly re-fit (see 2 and the unlocked / fixed-centre numbers in 7); a drift in either (e.g. the exact MTM lock engine) can remove most of the mean.
- Sample: the weekly mean is below the MDE for 80% power on 142 weeks; the 2023-04..2024-01 span and IS mean must agree with the sign: IS = 2,692/wk, span = -2,415/wk.
- Intrabar uncertainty: stop-vs-favourable ordering inside a bar is unknown (assumed adverse), real fills for market orders at the bar open may be worse than 0.995 pt in fast markets.
- NT8 vs vendor bars: any systematic difference in bar construction (late prints, session boundaries) changes Renko/ORB levels; a one-week Sim side-by-side with this replay should show the same entries; mismatch above 2% of trades in Sim means the NT8 code deviates.
