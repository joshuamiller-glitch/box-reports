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

## 5 (top). Live-vs-model comparison, blind week (ZL-1; compare_live_model.py; schema mapping edit logged in DECISIONS.md before the run; config sha256 1b92b848ab5a7a720237dfaeefeea112459420573a245293c4c5e805966a6588; faithful criteria frozen and unchanged; the sealed page and trade lists were not touched; full block also in BLIND_COMPARE_BLOCK.md)

## LIVE-VS-MODEL COMPARISON - BLIND-W45 (ZL-1 compare_live_model.py, 2026-11-06T16:01Z)

BASE = sealed prediction file (BASE-4 engine, per-period config) vs live StratTrades_DS7_<acct>.csv sha d918fee4e83e1852. Live rows are slices aggregated to trades by (book, exit time, exit name, side); entry/exit times ET wall clock; net = pnlNet. Match key = signal second, +-2 s (per-book override {P6: 47}), same book and side. Realised closed-trade maxDD only (no open-trade MAE).

**the engine predicted +34879$ for the week; live made +104095$; the gap (+69216$) is explained by these contributions to live minus engine: trades live took that the engine did not (65) +70005$; different exit type on matched trades +34760$; trades the engine took that live did not (60) -29887$; fill/size differences on matched same-exit trades -5661$; the engine is NOT a faithful model of live D7 for this week (trade match below threshold, net gap above threshold, exit-type agreement below threshold, maxDD gap above threshold).**

### Totals and trade count

| | engine | live | delta (live-engine) |
|---|---|---|---|
| net $ | 34879 | 104095 | +69216 |
| trades | 182 | 187 | +5 |
| matched exact (+-tol) | 120 | | |
| matched near (<=120s, timing slip) | 2 | | |
| engine-only | 60 | | |
| live-only | 65 | | |
| matched / union | 49.4% | | |

Longs/shorts engine 82/100, live 85/102. Max lots in a trade: engine 7.0, live 10.0. Worst trade $: engine -5861, live -6510. Signal-second offset on matches: mean -0.72 s, median 0.00 s, max abs 63.0 s.

Match rate by tolerance on the signal second (same book and side, greedy nearest; live entryTime = FILL of the first slice, so +-2 s is expected to under-match): +-2 s: 120 pairs, matched/union 48.2%, share of engine trades 65.9%; +-60 s: 121 pairs, matched/union 48.8%, share of engine trades 66.5%; +-120 s: 122 pairs, matched/union 49.4%, share of engine trades 67.0%; +-300 s: 125 pairs, matched/union 51.2%, share of engine trades 68.7%; +-900 s: 128 pairs, matched/union 53.1%, share of engine trades 70.3%. +-300 and +-900 s are diagnostics only. The verdict criteria use the near tolerance (near_tol_sec = 120 s), as frozen.

### Per book

| book | n_pred | pred_net | pred_lots | n_live | live_net | live_lots | d_n | d_net |
|---|---|---|---|---|---|---|---|---|
| A7 | 18.0 | 9067.2 | 20.0 | 23 | -1415.0 | 23 | 5.0 | -10482.2 |
| H7 | 19.0 | 9266.2 | 46.0 | 3 | -770.0 | 4 | -16.0 | -10036.2 |
| K7 | 61.0 | 10319.1 | 70.0 | 64 | 16065.0 | 76 | 3.0 | 5745.9 |
| M7 | 29.0 | 2490.3 | 39.0 | 28 | 6015.0 | 37 | -1.0 | 3524.7 |
| O7 | 0.0 | 0.0 | 0.0 | 3 | 660.0 | 3 | 3.0 | 660.0 |
| P7 | 43.0 | 2403.6 | 206.0 | 53 | 86010.0 | 247 | 10.0 | 83606.4 |
| U7 | 7.0 | 6674.6 | 24.0 | 6 | -1755.0 | 19 | -1.0 | -8429.6 |
| X3 | 2.0 | -6215.4 | 4.0 | 3 | -905.0 | 6 | 1.0 | 5310.4 |
| X4 | 2.0 | -1517.4 | 4.0 | 2 | -170.0 | 4 | 0.0 | 1347.4 |
| X5 | 1.0 | 2390.3 | 2.0 | 2 | 360.0 | 4 | 1.0 | -2030.3 |

### Per day (ET calendar date of entry; Sun = Sun night)

| day | n_pred | pred_net | pred_lots | n_live | live_net | live_lots | d_n | d_net |
|---|---|---|---|---|---|---|---|---|
| Sun 11-01 | 5 | 2952.4 | 9.0 | 11 | 22400.0 | 32 | 6 | 19447.6 |
| Mon 11-02 | 26 | -20635.1 | 59.0 | 41 | 13965.0 | 85 | 15 | 34600.1 |
| Tue 11-03 | 65 | 22926.4 | 155.0 | 46 | 8675.0 | 116 | -19 | -14251.4 |
| Wed 11-04 | 59 | 31247.1 | 134.0 | 61 | 43615.0 | 118 | 2 | 12367.9 |
| Thu 11-05 | 27 | -1612.3 | 58.0 | 28 | 15440.0 | 72 | 1 | 17052.3 |

### Engine by config period at entry (P0 old panel, P1 Mon 08:50-13:30, P2 after)

| period | n_pred | pred_net |
|---|---|---|
| P0 | 17 | -10600.7 |
| P1 | 4 | -27.1 |
| P2 | 161 | 45506.4 |

Engine trades not closed by the span end: 0.

### Gap decomposition (live - engine, $)

| component | $ |
|---|---|
| live-only trades | +70005 |
| engine-only trades (sign flipped) | -29887 |
| matched, different exit type | +34760 |
| matched, same exit type (fills/size) | -5661 |
| total | +69216 |

### Exit-type match (matched pairs; rows = engine, cols = live); agreement 64.5% on 121 pairs whose engine exit type is known (engine type other excluded)

| exit_type | target | thl2_cut | policy_cut | lock | stop | flatten | other |
|---|---|---|---|---|---|---|---|
| target | 46 | 3 | 4 | 0 | 0 | 0 | 0 |
| thl2_cut | 5 | 32 | 20 | 1 | 2 | 0 | 0 |
| policy_cut | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| lock | 1 | 1 | 0 | 0 | 0 | 0 | 1 |
| stop | 0 | 3 | 2 | 0 | 0 | 0 | 0 |
| flatten | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| other | 0 | 0 | 0 | 0 | 0 | 0 | 1 |

Exit counts all trades: engine {'target': 84, 'thl2_cut': 85, 'lock': 4, 'stop': 7, 'other': 2}; live {'target': 86, 'thl2_cut': 53, 'policy_cut': 39, 'lock': 3, 'stop': 2, 'other': 4}.

### Fill / slippage deltas on matched pairs by engine exit type (adverse + = live worse)

| type | n | d_net_mean | d_net_per_lot | d_net_sum | d_lots | entry_adv_pts | exit_adv_pts |
|---|---|---|---|---|---|---|---|
| target | 53 | -329.9 | -252.6 | -17485.6 | -0.1 | 3.3 | 10.8 |
| thl2_cut | 60 | 661.5 | 108.8 | 39688.2 | -0.1 | 3.9 | -5.0 |
| lock | 3 | 747.8 | 747.8 | 2243.4 | -0.3 | 3.3 | -33.8 |
| stop | 5 | 893.4 | 617.3 | 4466.9 | 0.0 | 0.6 | -29.7 |
| other | 1 | 186.0 | 186.0 | 186.0 | 0.0 | 6.0 | -12.0 |

### maxDD path (realised, by exit time)

engine maxDD 25893$ (trough Tue 11-03 06:30Z); live maxDD 14490$ (trough Wed 11-04 01:03Z); gap 44.0%.
 Equity-curve correlation on a 49-point grid 0.901; largest |engine-live| 69216$ at Thu 11-05 16:05Z.


### Unmatched trades (by signal second; first 25 each)

engine-only:

| signal_sec | book | side | lots | exit_type | net |
|---|---|---|---|---|---|
| Sun 11-01 23:41Z | H7 | 1 | 3.0 | other | 1378.8 |
| Mon 11-02 03:36Z | K7 | 1 | 1.0 | thl2_cut | -721.1 |
| Mon 11-02 05:53Z | P7 | 1 | 4.0 | thl2_cut | -2659.1 |
| Mon 11-02 07:17Z | X4 | -1 | 2.0 | target | 1590.3 |
| Mon 11-02 07:36Z | K7 | -1 | 3.0 | thl2_cut | -1716.2 |
| Mon 11-02 08:28Z | X5 | -1 | 2.0 | target | 2390.3 |
| Mon 11-02 13:43Z | X3 | 1 | 2.0 | stop | -3107.7 |
| Mon 11-02 16:17Z | M7 | -1 | 1.0 | target | 1232.3 |
| Mon 11-02 16:28Z | H7 | -1 | 1.0 | thl2_cut | -676.2 |
| Tue 11-03 00:15Z | H7 | -1 | 2.0 | thl2_cut | -1238.7 |
| Tue 11-03 01:33Z | H7 | 1 | 2.0 | thl2_cut | -1288.6 |
| Tue 11-03 04:14Z | P7 | -1 | 7.0 | thl2_cut | -3819.3 |
| Tue 11-03 05:57Z | H7 | -1 | 2.0 | thl2_cut | -1103.6 |
| Tue 11-03 05:58Z | P7 | -1 | 4.0 | thl2_cut | 7715.8 |
| Tue 11-03 07:48Z | K7 | 1 | 1.0 | target | 1102.2 |
| Tue 11-03 07:56Z | M7 | 1 | 1.0 | thl2_cut | -563.1 |
| Tue 11-03 08:07Z | P7 | 1 | 4.0 | thl2_cut | -2207.5 |
| Tue 11-03 09:10Z | U7 | 1 | 2.0 | target | 2419.1 |
| Tue 11-03 09:38Z | P7 | 1 | 4.0 | target | 4876.7 |
| Tue 11-03 09:39Z | K7 | 1 | 1.0 | target | 1226.7 |
| Tue 11-03 09:44Z | M7 | 1 | 1.0 | target | 1226.7 |
| Tue 11-03 10:18Z | P7 | 1 | 4.0 | thl2_cut | -2447.3 |
| Tue 11-03 10:23Z | M7 | 1 | 2.0 | thl2_cut | -1372.7 |
| Tue 11-03 11:21Z | K7 | -1 | 1.0 | target | 1037.7 |
| Tue 11-03 11:54Z | M7 | -1 | 2.0 | target | 2464.7 |

live-only:

| entry_ts | book | side | lots | exit_type | net |
|---|---|---|---|---|---|
| Sun 11-01 23:36Z | P7 | 1 | 4 | target | 4805.0 |
| Sun 11-01 23:42Z | K7 | 1 | 3 | target | 3600.0 |
| Mon 11-02 00:11Z | P7 | 1 | 10 | target | 12010.0 |
| Mon 11-02 01:45Z | P7 | 1 | 4 | target | 4810.0 |
| Mon 11-02 03:13Z | A7 | 1 | 1 | lock | -395.0 |
| Mon 11-02 03:48Z | K7 | 1 | 3 | thl2_cut | -1900.0 |
| Mon 11-02 03:50Z | H7 | 1 | 2 | thl2_cut | -1370.0 |
| Mon 11-02 04:03Z | P7 | 1 | 2 | thl2_cut | -1405.0 |
| Mon 11-02 06:45Z | K7 | -1 | 1 | target | 1200.0 |
| Mon 11-02 07:21Z | X4 | -1 | 2 | target | 1600.0 |
| Mon 11-02 09:00Z | X5 | -1 | 2 | thl2_cut | -1405.0 |
| Mon 11-02 10:01Z | P7 | -1 | 3 | target | 3605.0 |
| Mon 11-02 11:58Z | M7 | -1 | 1 | other | 840.0 |
| Mon 11-02 12:20Z | X5 | -1 | 2 | other | 1765.0 |
| Mon 11-02 12:54Z | K7 | -1 | 1 | thl2_cut | -640.0 |
| Mon 11-02 13:20Z | M7 | -1 | 3 | policy_cut | -1775.0 |
| Mon 11-02 13:37Z | X3 | 1 | 2 | target | 2005.0 |
| Mon 11-02 13:38Z | X3 | -1 | 2 | thl2_cut | -1225.0 |
| Mon 11-02 15:02Z | M7 | -1 | 1 | thl2_cut | -575.0 |
| Mon 11-02 15:02Z | P7 | -1 | 4 | policy_cut | -2865.0 |
| Mon 11-02 15:25Z | H7 | 1 | 1 | policy_cut | -600.0 |
| Mon 11-02 15:36Z | K7 | 1 | 1 | policy_cut | -625.0 |
| Mon 11-02 15:54Z | K7 | -1 | 1 | target | 1200.0 |
| Mon 11-02 16:10Z | H7 | -1 | 1 | target | 1200.0 |
| Mon 11-02 16:12Z | K7 | -1 | 1 | target | 1200.0 |


Criteria (pre-stated in blind_cmp_config.json): {"min_matched_frac_of_union": 0.85, "max_abs_net_gap_frac": 0.15, "min_exit_type_agree": 0.8, "max_maxdd_gap_frac": 0.25}. Checks: {'matched': False, 'net': False, 'exits': False, 'dd': False}.

## 5.2 Ranked list of engine defects behind the gap (BASE-4; full evidence, 33 separate variant runs and helper pages in BLIND_DEFECTS_BASE4.md; helpers BLIND_DEFECTS_{Z1,S4A,ZL2,CHARC}.md; fixed harness blind_run.py sha 7a1562fc..., the sealed run/page/lists untouched; live file StratTrades_DS7_<acct>.csv sha256 d918fee4...)
The engine predicted +34,879 on 182 trades for the week Sun 11-01 18:00 ET to Thu 11-05 11:05 ET; live made +104,095 on 187 trades (P7 +86,010 on 53 trades vs engine P6 +2,404 on 43). The gap of +69,216 is explained by: (1) the engine's TH-L2 cut fires on 8 matched trades that live let run to target or held (+41.6k; P7 +36.5k, K7 +2.5k, M7 +2.7k; with the cut switched off the engine makes +94.9k, P7 +44.4k; no cut parameter reproduces live: best agreement is the base setting, 99 of 120 pairs); (2) 16 live P7 re-entries (+35.9k) that the engine cannot take because the signal library thins signals against the library's own nominal 60/60 trade instead of the engine's earlier cut exit (event-matched, not re-run); (3) the old-panel signal-state SKIP slots (P7 SkipTop3, K7 SkipBot3) that the engine applies Sun-Mon and live did not (+12.0k); offset by engine over-statements: 29.0k of engine-only trades live never took (HM 9.3k, SM 7.3k, KB 5.9k, PE 3.6k, MV 1.8k, PB 1.1k; HM VWAP-reset clock tested and rejected as the cause), entry fills 3.5 pt better than live fills (about 29k over 415 lots, embedded in the pairs), 10.2k of live TH-L2 cuts the engine does not make (A7 PB7 book), and one engine P7 trade booked +7.7k on an 18.75 pt adverse exit (ledger anomaly, unresolved). Not explained by: locks and caps (<3% each, D1 all locks off +7.9k and P7 unchanged), blocks, lots (equal on 113 of 120 pairs), the ER ladder, stops, targets (all 86 live targets fill at nominal), DST/clock. **The engine is NOT a faithful model of live D7 for this week**: it is wrong in level (-69k) and its dominant error has a stable direction (it over-cuts: engine cuts 63% of P7 trades, live 45%).
| rank | defect | $ in the gap (live minus engine) | confidence |
|--|--|--|--|
| 1 | TH-L2 cut fires where live held (8 pairs; engine fires on isolated 10-s rows: 4 of 5 single-row triggers not cut live vs 4 of 55 multi-row) | +41,572 | high that it is the largest exit defect; cause (L2 reconstruction / thick-book / persistence) open |
| 2 | Library busy-thinning removes P7 re-entries (16 trades; live-only P7 total +53,565 of which 17 trades +41.9k have no signal row) | +35,900 | medium-high (mechanism matched trade by trade; no engine re-run) |
| 3 | Engine-only trades live never took (HM, SM, KB, PE, MV, PB) | -29,014 | HM medium, others low |
| 4 | Entry fills too good in the engine (3.52 pt/lot; engine entry prices 3.4-5.3 pt better than the touch) | about -29,000, embedded in 1-3 | high (ZL-2) |
| 5 | P0 SKIP slots not applied live | +12,010 | medium-high; engine re-run with skips off lowers the engine by 3.3k (freed entries meet the over-cutting trigger) |
| 6 | Live cuts the engine does not make (A7) | -10,189 | medium |
| 7 | Data-tail boundary (P7 S5 at Thu 11:04:30) | +6,000 | high |
| 8 | PE 45-s confirmation / candidate flag (rows with lots > 0 not traded) | +5,135 | medium |
| 9 | Other live-only entries (M7 8, U7 1, K7 11, H7 3, O7 3) | +7,505 | low-medium |
| 10 | X panel (X5 cold start, X3/X4 chains) | +4,627 | medium |
| 11 | Engine ledger anomaly, one P7 trade | up to -9,300 (engine too high) | low-medium |

## 5.3 What changes in the live-vs-model register's first row
Row 1 (blind week W45, 2026-11-01 18:00 to 11-05 11:05 ET): engine (sealed) +34,879 / 182 trades; live +104,095 / 187 trades; gap +69,216; matched/union 49% at +-120 s; exit-type agreement 64.5%; maxDD 25.9k engine vs 14.5k live; all four frozen faithfulness criteria fail; status 'NOT FAITHFUL (level and trade set)'. The row carries the three-line cause (cut, busy-thinning, skip slots) with their dollars, and these changes: (a) the register no longer records the engine's P&L level as a forecast of live; it records direction-of-error counters instead: engine cut count vs live cut count on matched trades, live-only P7 entries (library thinning), engine-only trades; (b) the next weekly row runs the engine twice, as sealed and with the cut off, as a bracket (this week: 34.9k and 94.9k, live 104.1k), with the busy-thinning and skip-slot effects flagged rather than corrected; (c) the fix queue is items 1, 2, 5, 6 of 5.2 (cut persistence/L2 fidelity, engine-aware busy release which needs L2 loss rows for the new trade ids, live applies no P0 skips, cut coverage for the PB7 book), none applied to the sealed page. These are proposals for the lead; nothing here changes a live rule or a size.
