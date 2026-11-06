# DS3_BLIND_WEEK - SEALED prediction of the live D7 week (box engine, blind)

Blind replay of the live D7 week by the research box (BASE-4 lead; ZL-2 data, Z1 old panel, S4a lock rules/config). Span Sun 2026-11-01 18:00 ET -> 2026-11-05 11:05 ET. Config frozen in autopilot/BLIND_WEEK_CONFIG_FREEZE.md (sha256 703f167d...). Nothing under data/live/ was opened, parsed or imported by me or the helpers before this page was written. Research only; this is a prediction, not a result; no PASS claim.

## 1. Predicted result
**Net P&L (after fees, closed trades): +34,879 $.** 182 trades closed (82 longs, 100 shorts), 0 open at the end of the span. Max lots in one trade: 7. Worst trade: -5,861 $ (P6 short, entered Thu 07:58 ET). Maximum drawdown of the realised cumulative P&L: -25,893 $ (peak-to-trough ending Tue 01:30 ET). Realised path: min -19,166 $, max +47,409 $.

| book | trades | net $ | long | short | max lots | worst trade $ |
|--|--|--|--|--|--|--|
| A6 | 18 | +9,067 | 6 | 12 | 2 | -1,254 |
| H6 | 19 | +9,266 | 5 | 14 | 4 | -2,482 |
| K6 | 61 | +10,319 | 27 | 34 | 3 | -1,716 |
| M6 | 29 | +2,490 | 20 | 9 | 3 | -1,870 |
| P6 | 43 | +2,404 | 19 | 24 | 7 | -5,861 |
| U6 | 7 | +6,675 | 3 | 4 | 6 | -3,969 |
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
| Thu 11-05 | 27 | -1,612 | 13 | 14 | +34,878 |

By entry date: Sun 11-01 5 trades +2,952 $, Mon 11-02 26 trades -20,635 $, Tue 11-03 65 trades +22,926 $, Wed 11-04 59 trades +31,247 $, Thu 11-05 27 trades -1,612 $.

Exits by type (count, net $): lock 4, -3,429; other 2, +1,733; stop 7, -14,338; target 84, +190,459; thl2_cut 85, -139,546. thl2_cut = TH-L2 panel cut; policy_cut = loss-line cut that fires before the panel cut; lock = per-book day give-back / week floor flatten; other = profit tighten, add-leg or unclassified exits (counted, not hidden).

Per book and day ($):
| book | Sun 11-01 | Mon 11-02 | Tue 11-03 | Wed 11-04 | Thu 11-05 |
|--|--|--|--|--|--|
| H6 | +1,379 | -3,204 | +6,539 | +4,098 | +454 |
| A6 | +1,941 | +0 | +2,214 | +5,917 | -1,005 |
| K6 | +354 | -1,868 | +3,471 | +4,837 | +3,525 |
| P6 | +0 | -6,976 | +6,595 | +3,834 | -1,049 |
| X4 | +0 | -1,517 | +0 | +0 | +0 |
| U6 | +0 | -3,969 | +7,346 | +7,356 | -4,058 |
| M6 | +0 | -1,247 | -1,989 | +5,206 | +520 |
| X5 | +0 | +2,390 | +0 | +0 | +0 |
| X3 | +0 | -6,215 | +0 | +0 | +0 |

Lock events (per-book lock exits; the day give-back halts the book to the 18:00 label-day roll): A6 Sun 20:59 (-450 $); K6 Mon 10:15 (+26 $); H6 Wed 01:13 (-2,001 $); A6 Thu 01:15 (-1,005 $).
The directive says P7 (P6 here) was day-halted by give-back Wed 01:44 and K7 (K6) ~Thu 04:35; these were NOT used as inputs. In this replay P6 had 0 lock exits and K6 1 (times above).

## 2. How it was built

Engine: d7_v13t / lots_ts2 truth base (U7 exact blackout, per-book locks, legs lockfix, Native stops, 70/30 split, OTE-62 B73 D30, live lot order) run three times on the full span with the period configurations of blind_config.py (P0 old panel to Mon 08:50 ET, P1 v1.3 defaults ER x0.5/x1.5 to Mon 13:30, P2 Q1-A ER x0.5/x1.0 after) and composed by ENTRY time; X3/X4/X5 old-panel trades from Z1's tape simulation (5 trades, window busy mode); P0 signal state = Z1's 4-slot rank code (K7 SkipBot3, P7 SkipTop3 + SizeHi, H7 SkipBot3) instead of the engine's three rules; entry blocks 09:00-09:59 / 18:00-18:04 / 15:00-17:59 ET and the Tue 19:52-19:55 restart window applied in all periods; loss-line cut from Mon 08:20 ET alongside the panel cut. Fills: first fill 1 s after the 1-min close, targets at nominal, stops 2.45 pt worse, market exits 0.80 pt, flatten 16:55 ET. Data: NQZ6 mbp-10 reduced by ZL-2 (de-duplicated tape, 1-s path, L2 tables) through 2026-11-05 11:05 ET. Trade list: autopilot/DS3_BLIND_WEEK_trades.parquet / .csv (one row per trade: signal_sec, book, side, lots, entry_ts, exit_ts, entry_px, exit_px, exit_type, net_usd, session, period, closed); entry_px / exit_px are the engine's library entry price and the exit level / path close (not volume-weighted over slices); signal_sec equals the entry second.

## 3. Uncertainty
The point estimate is the frozen configuration (BLIND_WEEK_CONFIG_FREEZE.md sha256 703f167d...) on the box's own engine; the band below is one-factor-at-a-time and is NOT a confidence interval. (1) Fill model: the engine fills on the 1-s path (first fill 1 s after the 1-min close, the whole size at once; the live 1-lot-per-2-s slicing is not modelled; stops 2.45 pt worse and market exits 0.80 pt are the constants measured on the old stack); ZL-2's fill-model band (stop cost, exit cost, extra cut cost; entry delay is not an engine switch and is not run) is in DS3_BLIND_WEEK_BAND.md, appended after the seal. (2) L2 reconstruction: the TH-L2 cut uses features rebuilt from the replayed mbp-10 stream by the research code (5-s pulled support and median level reproduce the stored table on 99.9996% of rows, DS3_TH_FIDELITY.md) and is evaluated on the stored 10-s decision grid; the live process may evaluate every second or every book event, which cuts more borderline wick trades and halves the post-cap cut gain (DS3_TH_CLOCK.md): of the 182 trades predicted here, TH-L2 cuts are the largest exit class, so this is the largest single modelling risk. (3) The 8-hour old-panel period (Sun 18:00 -> Mon 08:50 ET): the thick-book profit tighten is approximated by the engine's path trail (switching the tighten off changes the week by +3,172 $), the 4-slot signal state is Z1's reconstruction with the library rank history, not the live chart's own (using the engine's three rules instead changes the week by -5,144 $), X3/X4/X5 come from a separate tape simulation of 5 trades, the Mon 08:05-08:15 five-rule take file is not modelled, and whether the entry blocks apply in P0 changes the week by +0 $. (4) Period composition: the three period runs carry their own day/week lock states, so Monday's lock state is not the true mixed-configuration sequence; running every period with the Q1-A configuration changes the week by +8,359 $, and running P0 with the v1.3 defaults by +271 $; zones HALF instead of SKIP in P0 change it by -1,664 $. (5) Data: Databento flags 2026-11-01 as degraded; the 23:00Z-onward slice we hold (the last hour of the flagged day) shows 1 bad-ts record in 26.7M and no sequence or book-state flags, no gap at the Sunday open, so the L2 reconstruction risk from the flag is judged negligible for this slice (ZL-2 QA). The remaining gap is the part of 11-01 before 23:00Z, which is the Sunday pre-open and outside the replay window. (6) The policy loss line is implemented as a second cut set from the stored L2 rows (pct taken as a fraction of the stop distance) and is almost identical to the panel cut; the A06 slot and B02 lot rules are assumed live in all periods; the library trade rows for the new days come from the de-duplicated tape and the 1-s path, tied out to the stored rows on every old day.


## 4. Reproducibility (sha256 of what produced this page)
Harness (code/blind/): blind_run.py 0ad2308fde2b6e67; blind_config.py 62a9f3bd9bf2403b; blind_week.py d41f4f0f3c8ac3ea; blind_page.py 2aaa9cd6bd355125; blind_boot.py 35f314caf14ce781; mk_blind.py cffcd2631fc53b41; run_chain.sh a67c7967a025900d; lock_rules.py 13e45d191670d786; blind_unc_text.py 7df6ccc3527737c1; blind_sens.py 320f3b338cc0c911; 
Trade list: DS3_BLIND_WEEK_trades.parquet sha256 b739a9aad0f8bc47ef0d78e0f7199644f9c5e7ff8faff581cd1c8dbd72cd76d3; DS3_BLIND_WEEK_trades.csv sha256 1a167b037d0144ec4e2d3fa3139d9943c4639ca19a5707227c74f790fd00ab36. Engine run pickle /mnt/l2/l2vast/ds3_base4/blind_run_blind.pkl; sensitivities /mnt/l2/l2vast/ds3_base4/blind_sens_final.json (one factor at a time: P0 without blocks $+0 (no P0 entry falls in a block), engine 3 signal rules instead of the 4 slots -5,144, tighten off +3,172, zones HALF in P0 -1,664, all periods on the Q1-A configuration +8,359). ZL-2's fill-model band: DS3_BLIND_WEEK_BAND.md, appended after the seal (separate file, separate sha256).
Data: NQZ6 mbp-10 2026-11-01T23:00Z -> 2026-11-05T16:05Z (135.3M records, final tag 2026-11__ext_20261101_20261105), all *_blind trees verified P2 (identical to P1 through 13:25Z); the chain was rebuilt from scratch after the P1->P2 swap (a first run overlapping the swap was discarded). Seal time: see DECISIONS.md.
