# DS3_SPEC_TB9_RENKO_c5_k1_A3_N - executability spec and identity test (D3X, 2026-10-26)

**STATUS: NOT A BOOK (lead D3L, 2026-10-26): DEAD after the exact-lock re-score (WF -$244/wk, HOLD -$2,475/wk, unlocked -$12.7k/wk). The rule below is executable (identity passes) but the book has no edge; file kept for the record, not for implementation.**

Research output for the Sim leader; NOT a live recommendation. No execution-server, chart or live change. Written by D3X from the box's own independent replay (l2vast/ds3/code/x_replay.py, x_tb.py, x_locks.py); all numbers re-derived from the 1-minute Databento files.

**Verdict: DELIVERABLE** (NT8 1-minute data only, no L2, no sub-second timing). Identity: library vs the replay = 0 mismatching trades of 1801 (0.00%) when the replay uses the library's own hindsight data-gap flag; against the NT8-CAUSAL rule written below the mismatch is 0.06% of trades (0 missing entries, 1 exit/price differences; limit 2%).

## 1. Book in one line

TB9_RENKO_c5_k1_A3_N: track verdict **CANDIDATE** (T-B, prereg 9); family RENKO, 1-minute bars, stop 3.0 x ATR(14) of the 1-min bars evaluated at the signal bar close, exit code A3.

## 2. Rule an NT8 strategy must reproduce

- **Instrument / bars:** NQ (front month, continuous, MergeBackAdjusted) 1-MINUTE time bars (the Renko logic below runs on 1-minute CLOSES inside the strategy; it is NOT the NT8 Renko bar type, which is built from ticks). NT8 stamps a bar with its END time: bar start = Time[0] - 1 min.
- **Indicator / state:** Renko state machine on 1-minute closes, brick size B and confirmation count N from the monthly schedule (grid B in {12,20,30} pts, N = 5 fixed for this book; centre B=20). Per label day (reset at 18:00 ET): anchor a = first close; dir dr=0; run=0; st=0. On each closed 1-min bar with close c: if dr>=0 and c >= a+B: k=floor((c-a)/B); a+=k*B; run = (dr==+1 ? run+k : k); dr=+1. elif dr<=0 and c <= a-B: k=floor((a-c)/B); a-=k*B; run = (dr==-1 ? run+k : k); dr=-1. elif dr==+1 and c <= a-2B: k=floor((a-c)/B)-1; a-=(k+1)*B; dr=-1; run=k. elif dr==-1 and c >= a+2B: k=floor((c-a)/B)-1; a+=(k+1)*B; dr=+1; run=k. Then if dr != 0 and run >= N: st = dr (st is sticky: it is NOT cleared by a reversal whose run < N).
- **Signal:** Target position = st (0 until the first confirmed run of the label day).
- **Entry:** Flat and st != 0 and st != blocked at the close of 1-min bar i: market order at the open of bar i+1 (modelled open +/- 0.995 pt) if bar i+1 START is before 15:00 ET or at/after 18:05 ET, and bar i is not the force-flat bar. Reversal: market exit at the open of bar i+1 and market entry the same bar in the new direction.
- **Exit / stop:** (a) Protective stop-market 3.0 x ATR(14) of the 1-min bars evaluated at the signal bar close (nominal about 29.8 pt; lots 20.1 so that R = lots x nominal stop x $20 = 12,000) from the OPEN of the entry bar, active from the entry bar; modelled fill = stop -/+ 1.01 pt, gap fills at the bar open -/+ 1.01 pt; tested on the 1-min High/Low (stop first inside a bar). (b) Signal reversal. (c) Force-flat: market exit at the close of the 1-min bar that starts at 16:54 ET (exit about 16:55) and on CME early-close days at the close of the final bar. (d) Data gap: if a 1-min bar opens later than one bar after the previous bar (a minute with no trade) while a position is open, the position is closed at the open of that post-gap bar (NT8-causal rule; the library closed it at the previous close using hindsight). After a stop-out no new entry in the stopped direction until st changes. No target.
- **Session window (ET):** Entries any time except bars that START in [15:00, 18:05) ET (so effectively 18:05 to 14:59 ET, all three sessions). Flat by 16:55 ET. Median holding time about 51 min.
- **Order types:** entries and signal exits MARKET (sent on bar close, filled at next bar open in the model, 0.995 pt adverse = 4 ticks of cost already counted); protective STOP-MARKET (modelled 1.01 pt through the stop); no limit orders, no target; Calculate = OnBarClose; one position at a time; one stop order working at all times while in position.
- **Lots / dollars:** scored at 20.1042 NQ lots with R = 12,000 (= lots x nominal stop 29.84 pt x $20 = 11,998). Per-book locks (closed-trade approximation, see 8): day -2R = -$24,000, day +5R = +$60,000, give-back arm +2R = +$24,000 (once the day's realised P&L has peaked at or above +2R, stop for the day when realised falls to 50% of that peak), week floor -12R = -$144,000, cap off. At the 14/14 scale (R = 16,800) the same book is 28.1 lots with -2R = -$33,600, +5R = +$84,000, give-back arm $33,600, week floor -$201,600. DS2 sizing (ST10/HM10 = 10 lots, WT7 = 7 lots) is the reference.
- **Execution mode:** NT8 strategy on a 1-minute NQ chart, Calculate OnBarClose, tick-replay off, own per-book lock group (does not net with or lock DS2 books); can run in the same account as DS2.

### Monthly parameter schedule (walk-forward re-fit; REQUIRED to reproduce the series)

At the first trading day of each calendar month the box computes, for each grid point, the sum of per-lot net dollars (pts x $20 - $4.84) of that point's trades ENTERED in the previous 6 calendar months and CLOSED before the 1st of the month, picks the argmax; if the best-covered grid point has fewer than 20 such trades it uses the centre point. The 3x3 grid is [(12.0, 5.0), (20.0, 5.0), (30.0, 5.0)], centre index 1 = (20.0, 5.0). The strategy reads the chosen tuple from a small parameter file (one line per month; the box publishes the next month's line on the last weekend of the month). A second independent implementation of the re-fit (x_tb.refit) reproduces all 45 library schedule months with 0 differences. Last six months of the schedule (month: grid index): 202605: 2, 202606: 2, 202607: 2, 202608: 2, 202609: 2, 202610: 1. The re-fit is part of the rule: fixed-centre-parameter WF-PRE mean is $2,133/wk against $12,931/wk re-fitted (row fields fixed_center_WFPRE_mean, WFPRE_mean); if the fixed book is not clearly worse, the schedule file can be dropped and the centre used.

## 3. Identity test (box replay vs library series)

| check | n library | n replay | mismatches | % |
|---|---|---|---|---|
| library trades (stitched, pre-lock) vs replay with library gap flag | 1801 | 1801 | 0 | 0.00 |
| NT8-causal rule vs library (entry time, side, exit time, pts within 0.5) | 1801 | 1801 | 1 | 0.06 |
| locked daily P&L series, replay vs library (max abs daily difference, $) | 953 days | 953 days | hindsight 1.5e-09; causal 704 | - |
| monthly parameter schedule regenerated vs library | 45 months | 45 | 0 | 0.0 |

Cause of the causal-rule differences: the library flagged 'force-flat' on any bar followed by a data gap (a bar missing because no trade printed) and on the bar before CME early closes. Early closes are calendar-known and are in the NT8 rule (115 early-close days since 2013 in the data; hard-code the CME holiday calendar); mid-session minutes with no trade are not knowable in advance, so the causal rule closes at the first bar after the gap at its open (and does not skip an entry placed before the gap). Differences listed (entry epoch, side, library pts, causal pts, library exit type, causal exit type): [((1783045560, 1), 151.51000000000204, 149.76000000000204, 3, 6)]

Replay inputs: Databento 1-minute continuous .v.0 (volume roll) files, back-adjusted at each roll by the opening gap; own loader, own ET calendar (pandas tz), own indicator code (online bar-by-bar state machine, no vectorised library code). The monthly schedule table is an input; its regeneration is tested above. The verdict follows the directive rule (mismatch > 2% of trades = not deliverable).

## 4. Data, instrument, contract, roll

- Instrument NQ (E-mini Nasdaq-100, $20/pt, tick 0.25), front quarterly contract; research data are Databento 1-min .v.0 (volume-leader roll) back-adjusted. In NT8 use the continuous NQ contract with merge policy MergeBackAdjusted (the strategy must see the same back-adjusted history; the RENKO state is reset daily). The book is flat from 16:55 ET to 18:05 ET every day, so no trade is carried across a roll; replay trades spanning a roll bar: 0 of 1801.
- NT8 time bars are built from last-trade ticks, as Databento OHLCV-1m is; minutes without a trade have no bar in either. Expect small OHLC differences from vendor tick filtering; the replay is 1-minute-bar based so any intrabar order of high vs low is unknown (stop is assumed to be hit before any favourable move inside the same bar, entry bar included).
- Holidays and half days: no entry when no bars exist; on CME early-close days (13:00 or 13:15 ET close) the book is force-flat at the final bar's close (NT8: either Exit-on-session-close, which fires ~30 s earlier, or a bar-time check) - hard-code the CME equity holiday calendar; Juneteenth, Thanksgiving Friday, Dec 24, Jul 3 appear in the sample. Unplanned halts (e.g. the 2025-01-09 national day of mourning) fall under the data-gap rule.

## 5. Fills and costs assumed

Commission+exchange $4.84 per contract round trip; market orders 0.995 pt adverse each side (live cost model); stop-market 1.01 pt through the stop; gaps fill at the open. No limit orders and no trade-through assumptions. Under the live model costs are already inside the series; the row's 2x-cost sign test is positive.

## 6. Position-limit interaction with DS2

One position at a time, so peak lots from this book = 20.1042 NQ. DS2 ST10/HM10/WT7 can hold 10+10+7 = 27; worst case concurrent = 47.1042 (limit 50; other DS3 books add to this and are counted by the lead in DS3_PORTFOLIO). Margin proxy: 20.1042 NQ intraday only (flat before 17:00 ET) - day-margin applies, no overnight margin.

## 7. Backtest expectation (replayed: closed-trade per-book locks, 142 WF weeks 2024-02..2026-10, live cost)

| WF mean/wk | SD/wk | maxDD (weekly) | worst week | trades/wk (kept) | win rate | avg win | avg loss | IS 2023-02..2024-01 mean/wk | HOLD 2025-07+ mean/wk | L8W mean/wk |
|---|---|---|---|---|---|---|---|---|---|---|
| 14,623 | 121,660 | 1,013,475 | -179,622 | 7.2 | 24% | 63,517 | -16,898 | 2,288 | 16,274 | -11,067 |

Track row (same series): WF mean 14,628, SD 121,657, maxDD 1,035,084, holdout 16,284, 2023-04..2024-01 span 7,866 (sign 1), placebo rank 1.0, MDE 28,602/wk, CI of mean [-5,310, 34,927]. Weekly corr: ST10 0.16, HM10 0.29, ST10+HM10 pair 0.26. Unlocked (no per-book locks) WF-PRE mean $-14,004/wk vs locked $12,931/wk.

### 7b. EXACT-lock expectation (supersedes the closed-trade numbers in 7; series l2vast/ds3/out/T-B/EXACT_TB9_RENKO_c5_k1_A3_N_1x.parquet, lock engine = mark-to-market, from the lead)

| WF mean/wk (exact) | WF SD | WF maxDD | WF Sharpe | HOLD mean | HOLD Sharpe | L8W mean | WF-PRE mean | IS mean | span 2023-04..2024-01 | WF unlocked (exact engine, no locks) | WF at 1.5x cost | WF at 2x cost | trades/wk | lots / peak lots |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| -244 | 59,145 | 751,565 | -0.03 | -2,475 | -0.27 | 45,207 | 1,781 | 5,166 | 2,664 | -12,700 | -1,371 | -3,688 | 6.0 | 20.104224776585674 / 40.20844955317135 |

## 8. Locks, and what the series does and does not contain

The series uses the track's CLOSED-TRADE approximation of the per-book locks (day realised -2R/+5R, give-back arm 2R keep 50%, week floor 12R; the check happens before each entry using already closed trades). The NT8 implementation would measure the day's P&L mark-to-market while a position is open (the exact engine l2vast/pairP2/firm/riskeng_pb.py does that for DS2), so the live lock behaviour differs from the closed-trade series in 7; the lead has re-scored the book with the exact MTM engine (7b), and 7b is the expectation to use. The lock arithmetic itself was re-implemented here (x_locks.py) and reproduces the library daily series to 1e-9 dollars on the library trades.

## 9. What could kill it

- About 30-45% of the signalled trades are skipped by the per-book day locks, and the unlocked series is flat to negative (row field unlocked_WFPRE_mean), so the book is a lock-conditioned trend scalper, not a stand-alone edge.
- High turnover (about 16-20 trades/wk) at 1-minute decision: slippage above 0.995 pt per market order erodes the mean quickly; NT8 data-gap behaviour (no bar for a quiet minute) matters.
- Renko logic runs on 1-minute CLOSES; implementing it on NT8's native tick Renko bars is a different system and is not covered by this spec.
- Edge depends on the per-book locks and on the monthly re-fit (see 2 and the unlocked / fixed-centre numbers in 7); a drift in either (e.g. the exact MTM lock engine) can remove most of the mean.
- Sample: the weekly mean is below the MDE for 80% power on 142 weeks; the 2023-04..2024-01 span and IS mean must agree with the sign: IS = 2,288/wk, span = 7,866/wk.
- Intrabar uncertainty: stop-vs-favourable ordering inside a bar is unknown (assumed adverse), real fills for market orders at the bar open may be worse than 0.995 pt in fast markets.
- NT8 vs vendor bars: any systematic difference in bar construction (late prints, session boundaries) changes Renko/ORB levels; a one-week Sim side-by-side with this replay should show the same entries; mismatch above 2% of trades in Sim means the NT8 code deviates.
