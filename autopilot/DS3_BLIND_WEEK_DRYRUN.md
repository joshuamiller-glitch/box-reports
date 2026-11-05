# DS3_BLIND_WEEK_DRYRUN - dry-run prediction on part 1 of the data (NOT the sealed page)

Blind replay of the live D7 week by the research box (BASE-4 lead; ZL-2 data, Z1 old panel, S4a lock rules/config). Span Sun 2026-11-01 18:00 ET -> 2026-11-05 08:25 ET. Config frozen in autopilot/BLIND_WEEK_CONFIG_FREEZE.md (sha256 703f167d...). Nothing under data/live/ was opened, parsed or imported by me or the helpers before this page was written. Research only; this is a prediction, not a result; no PASS claim.

## 1. Predicted result
**Net P&L (after fees, closed trades): +32,275 $.** 178 trades closed (82 longs, 96 shorts), 0 open at the end of the span. Max lots in one trade: 7. Worst trade: -5,861 $ (P6 short, entered Thu 07:58 ET). Maximum drawdown of the realised cumulative P&L: -25,893 $ (peak-to-trough ending Tue 01:30 ET). Realised path: min -19,166 $, max +47,409 $.

| book | trades | net $ | long | short | max lots | worst trade $ |
|--|--|--|--|--|--|--|
| A6 | 18 | +9,067 | 6 | 12 | 2 | -1,254 |
| H6 | 17 | +7,445 | 5 | 12 | 4 | -2,482 |
| K6 | 60 | +9,098 | 27 | 33 | 3 | -1,716 |
| M6 | 28 | +3,183 | 20 | 8 | 3 | -1,870 |
| P6 | 43 | +2,404 | 19 | 24 | 7 | -5,861 |
| U6 | 7 | +6,421 | 3 | 4 | 6 | -3,969 |
| X3 | 2 | -6,215 | 1 | 1 | 2 | -3,108 |
| X4 | 2 | -1,517 | 1 | 1 | 2 | -3,108 |
| X5 | 1 | +2,390 | 0 | 1 | 2 | +2,390 |

Session-day = ET calendar date of the EXIT (Sun = the Sunday-evening session 18:00-24:00; Mon..Thu as dated); P&L is realised on that day.
| day | trades | net $ | long | short | cumulative $ |
|--|--|--|--|--|--|
| Sun 11-01 | 4 | +3,673 | 4 | 0 | +3,673 |
| Mon 11-02 | 26 | -22,606 | 9 | 17 | -18,933 |
| Tue 11-03 | 66 | +24,176 | 24 | 42 | +5,243 |
| Wed 11-04 | 59 | +31,247 | 32 | 27 | +36,490 |
| Thu 11-05 | 23 | -4,216 | 13 | 10 | +32,274 |

By entry date: Sun 11-01 5 trades +2,952 $, Mon 11-02 26 trades -20,635 $, Tue 11-03 65 trades +22,926 $, Wed 11-04 59 trades +31,247 $, Thu 11-05 23 trades -4,216 $.

Exits by type (count, net $): lock 4, -3,429; other 2, +1,733; stop 7, -14,338; target 81, +187,416; thl2_cut 84, -139,107. thl2_cut = TH-L2 panel cut; policy_cut = loss-line cut that fires before the panel cut; lock = per-book day give-back / week floor flatten; other = profit tighten, add-leg or unclassified exits (counted, not hidden).

Per book and day ($):
| book | Sun 11-01 | Mon 11-02 | Tue 11-03 | Wed 11-04 | Thu 11-05 |
|--|--|--|--|--|--|
| H6 | +1,379 | -3,204 | +6,539 | +4,098 | -1,367 |
| A6 | +1,941 | +0 | +2,214 | +5,917 | -1,005 |
| K6 | +354 | -1,868 | +3,471 | +4,837 | +2,303 |
| P6 | +0 | -6,976 | +6,595 | +3,834 | -1,049 |
| X4 | +0 | -1,517 | +0 | +0 | +0 |
| U6 | +0 | -3,969 | +7,346 | +7,356 | -4,312 |
| M6 | +0 | -1,247 | -1,989 | +5,206 | +1,213 |
| X5 | +0 | +2,390 | +0 | +0 | +0 |
| X3 | +0 | -6,215 | +0 | +0 | +0 |

Lock events (per-book lock exits; the day give-back halts the book to the 18:00 label-day roll): A6 Sun 20:59 (-450 $); K6 Mon 10:15 (+26 $); H6 Wed 01:13 (-2,001 $); A6 Thu 01:15 (-1,005 $).
The directive says P7 (P6 here) was day-halted by give-back Wed 01:44 and K7 (K6) ~Thu 04:35; these were NOT used as inputs. In this replay P6 had 0 lock exits and K6 1 (times above).

## 2. How it was built

Engine: d7_v13t / lots_ts2 truth base (U7 exact blackout, per-book locks, legs lockfix, Native stops, 70/30 split, OTE-62 B73 D30, live lot order) run three times on the full span with the period configurations of blind_config.py (P0 old panel to Mon 08:50 ET, P1 v1.3 defaults ER x0.5/x1.5 to Mon 13:30, P2 Q1-A ER x0.5/x1.0 after) and composed by ENTRY time; X3/X4/X5 old-panel trades from Z1's tape simulation (5 trades, window busy mode); P0 signal state = Z1's 4-slot rank code (K7 SkipBot3, P7 SkipTop3 + SizeHi, H7 SkipBot3) instead of the engine's three rules; entry blocks 09:00-09:59 / 18:00-18:04 / 15:00-17:59 ET and the Tue 19:52-19:55 restart window applied in all periods; loss-line cut from Mon 08:20 ET alongside the panel cut. Fills: first fill 1 s after the 1-min close, targets at nominal, stops 2.45 pt worse, market exits 0.80 pt, flatten 16:55 ET. Data: NQZ6 mbp-10 reduced by ZL-2 (de-duplicated tape, 1-s path, L2 tables) through 2026-11-05 08:25 ET. Trade list: autopilot/DS3_BLIND_WEEK_DRYRUN_trades.parquet / .csv (one row per trade: signal_sec, book, side, lots, entry_ts, exit_ts, entry_px, exit_px, exit_type, net_usd, session, period, closed); entry_px / exit_px are the engine's library entry price and the exit level / path close (not volume-weighted over slices); signal_sec equals the entry second.

## 3. Uncertainty
This is the dry run on part 1 of the data (through Thu 08:25 ET, L2 through 13:25Z); it is not the sealed answer. Known approximations in the point estimate: (1) fill model: the engine fills on the 1-s path (first fill 1 s after the 1-min close, the whole size at once; the live 1-lot-per-2-s slicing is not modelled; stops 2.45 pt and market exits 0.80 pt are the measured constants from the old stack); (2) L2 reconstruction: TH-L2 features are rebuilt from a replayed mbp-10 stream by the same code as the research base (the 5-s pulled support and median level reproduce the stored table on 99.9996% of rows, DS3_TH_FIDELITY.md), and the cut is evaluated on the stored 10-s decision grid; a live 1-s or event-driven evaluation would cut about twice as many borderline wick trades and halves the post-cap cut gain (DS3_TH_CLOCK.md); (3) the 8-hour old-panel period: thick-book profit tighten is approximated by the engine's path trail, the 4-slot state is Z1's reconstruction with the library rank history (not the live chart's own), X1-X5 come from a separate tape simulation, and the content of the Mon 08:05-08:15 five-rule take file is unknown and not modelled; (4) Monday: the three period runs each carry their own day/week lock state, so the Monday lock state is not the true mixed-config sequence; (5) Databento flags 2026-11-01 as degraded; ZL-2's QA of the part we hold (UTC 23:00-24:00 on 11-01) found no visible damage (monotonic receive times, no gap at the Sunday open); (6) the policy loss line is implemented as a second cut set from the stored L2 rows (pct taken as a fraction of the stop distance) and is almost identical to the panel cut; (7) the A06 slot and B02 lot rules are assumed live in all periods.

