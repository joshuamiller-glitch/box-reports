# DS3_SPEC_ba2_HM_t75_s90_SESSION - executability spec and identity test (D3SSE2, 2026-10-28)

Research output for the Sim leader; NOT a live recommendation. No execution-server, chart or live change. **Session cell, tier SESSION-CANDIDATE (BOF not cleared), basis STORED (ledger label "rows-as-stored": exact bracket points from the 1-s path, stored $100.13 per 10-lot trade cost; NOT mapped to P9, NOT direct-L2). NOT live-eligible until the live-latency result (D3SA, DS3_SESSION2_A) lands.** Cell = NY-AM entries (09:30-12:00 ET) of the live DS2 HM engine with the bracket target 75 pt / stop 90 pt.

Sources: ledger row "ba2/HM_t75_s90" (autopilot/DS3_SESSION_2_LEDGER.md line 53), rows l2vast/ds3/out/ba/rows2_HM_t75_s90.parquet (ledger_index cid 1569), generator l2vast/ds3/code/ba/ba_rows2.py (events line 107-108, gen lines 110-134), HM signal code/census/night_ins/nt8sim.py own_signals (lines 120-142, HM at 128-129) via l2vast/pairP2/firm/firmlib.py signals() (lines 36-44) with the BENCH3 block, HM description autopilot/FR_SEC5.md (lines 3, 170-171) and P9_NT8_SPEC.md (lines 10, 69). There is no stand-alone "HM engine spec" file in autopilot/; the DS3_SPEC_ST10.md header names outputs/h2/DualStrat.cs as the NT8 source of the DS2 books (ST/HM). The DS2 live .cs (DualStrat2) was not re-read here.

## 0. Is it the live HM engine? (verified, not assumed)
**Yes for the entry signal and the book mechanics; the bracket and the session restriction are the intended differences. One live-parameter question (the 09:00-09:58 guard) is open and material; see item 6.**
- ba_rows2.py line 107-108: for E='HM' the entries are `[(b,s) for b,bk,s in F.signals() if bk=='HM']`, the same function that generates the benchmark rows ROWS_bench3 for the live HM book.
- Identity at the live bracket (run today): rows2_HM_t60_s60.parquet vs pairP/ROWS_bench3.parquet (book HM, 2023-02-10+): 6311 vs 6311 trades, 0 entries only in one file, 0 exit-bar differences, 0 point differences. So the generator at 60/60 IS the benchmark HM book row for row. (The benchmark itself was matched to the NT8 live trade list at 97.7% of HM trades after the ENGINE_RECON fixes, FR_SEC5 line 170.)
- What differs from the live HM engine (complete list):
  1. **Target 75 pt / stop 90 pt** instead of 60/60 (R:R 0.833). Stop risk per NQ lot $1,800 (live $1,200).
  2. **Different trade chain.** HM is a separate book with its own one-open-trade rule; with longer brackets the exits move, so the dropped signals differ: 4,660 trades (all hours, 2023-02-10..2026-10-23) at 75/90 vs 6,311 at 60/60.
  3. **Session restriction**: only entries with entry-bar end stamp 09:30-12:00 ET. Exits run to bracket or the 16:55 flat. **A NY-AM-only live book would NOT reproduce the ledger chain**: in the all-hours library chain a London/PRE HM trade still open at 09:30 suppresses signals; on 355 of 924 library days an HM trade entered earlier the same calendar morning was still open at 09:30 (computed on rows2_HM_t75_s90). A session-only book would take signals the library dropped (more trades; unknown expectancy). The ledger rows are the "filter an all-hours chain" definition.
  4. **No netting.** The library/benchmark treats ST and HM as independent books (BENCH3: no netting, swallowed entries included, orphan fills excluded). The live account nets ST/HM (an opposite entry closes the oldest opposite lot; orphan protective orders, FR_SEC5 line 170). A stand-alone HM session strategy is not affected, but inside the live account it is.
  5. Fills: stored bracket points (stop gap rule STOP_GAP), entry at the entry-bar open, cost $100.13 per 10-lot trade; the live-style pricing (S10x1 slicing, XJ3 stop-join) is not applied (D3SA pending).
  6. Locks: ledger $ are unlocked. Live R = 10 x 60 x $20 = $12,000; a 90-pt stop at 10 lots = $18,000 = 1.5 R.
- Not changed: signal definition (below), BENCH3 signal block (15:00-17:59 signal bars), entry at the next 1-min open, 16:55 flat, early-close handling.

## 1. Rule (NT8)
- **Bars:** NQ 1-minute time bars, END-time stamped in NT8, Globex template, label day 18:00-17:59 ET, continuous back-adjusted; the 1-min volume series is needed (VWAP). Calculate OnBarClose.
- **Series x:** x = Close - VWAP, where VWAP is a cumulative sum(Close*Volume)/max(sum(Volume),1) over the 1-minute bars of the VWAP day. The VWAP day resets at 00:00 on a FIXED UTC-4 clock (nt8sim line 124: key = (minute*60 - 4*3600)//86400), i.e. 00:00 ET in summer (EDT) and 23:00 ET in winter (EST); it is NOT the 18:00 session reset. NT8 matches this (FR_SEC5 line 170, 100% of bars to 0.0001 after the fix).
- **Hull MA:** hma(x,n) = WMA( 2*WMA(x, floor(n/2)) - WMA(x, n), round(sqrt(n)) ) with WMA linear weights 1..n, partial window (min_periods=1) at the start (night_ind.py lines 49-54). a = HMA(x,20) (sub-windows 10 and 4), b = HMA(x,55) (27 and 7).
- **EMA filter:** EMA(Close,200), alpha 2/201, seeded with the first close (night_ind _ema_k).
- **Signal (edge, closed bar):** buy when a crosses above b (a > b now, a[1] <= b[1]) AND b rising (b - b[1] > 0) AND Close > EMA200; sell when a crosses below b (a < b, a[1] >= b[1]) AND b falling (b - b[1] < 0) AND Close < EMA200 (nt8sim lines 128-129).
- **Entry:** market order at the open of the next 1-minute bar after the signal bar closes. Signal bars whose start minute is in 15:00-17:59 ET are dropped (firmlib._BLOCK = ~((hm>=1080)|(hm<900))). **The 09:00-09:58 guard is NOT in the library rows** (firmlib line 'bench3: signals allowed 18:00..14:59 ET (guard 09:00-09:58 removed)'; the rows contain HM entries from stamp 09:30). One open HM trade at a time (busy until the exit minute); signals on or before the exit minute are dropped. 10 lots as 10 x 1-lot slices 2 s apart in the direct pricing.
- **Session filter (this cell):** keep the trade if the entry-bar END stamp (ledger et_in = actual entry instant + 1 min) has minute-of-day in [09:30, 12:00) ET (ss2lib.sess_of_min 570 <= m < 720). Earliest observed 09:30, latest stamp 11:59. Note a stamp of 09:30 means the order went in at 09:29:00 (signal bar 09:28 start).
- **Bracket (this cell):** stop-market 90 pt = 360 ticks, limit target 75 pt = 300 ticks, OCO from the entry price. Observed: every target +75.00, every stop -90.00 pt (over all hours: 2372 targets, 1844 stops, 444 time exits). Note the generator passes the ratio 75/90 into the stop simulator (float multiply); the stored levels are exactly 75.00 and 90.00, so NT8 should use 300 and 360 ticks. Stop checked before target inside one second.
- **Flat rule:** market flat at the close of the bar ending >= 16:55 ET; early-close days flatten at the final bar. Time exits are 34 of 427 PRE trades (8%): a NY-AM entry can run up to 7 h; mean 91 bars (1.5 h), median 43 bars.
- **Session window (ET):** entries 09:30-12:00 only; no flatten at 12:00.
- **Order types:** MARKET entry (sliced in the direct pricing), STOP-MARKET + LIMIT target OCO, MARKET time exit. No stop-join in the stored $.
- **Lots at $1,000 risk per trade:** NQ risk per lot 90 x $20 = $1,800, so $1,000 = 0.56 NQ lot: not whole-lot tradable; MNQ ($180 stop risk per contract): 5 contracts = $900 (6 = $1,080). Reference sizing in the ledger: 10 NQ lots ($18,000 stop risk).
- **Costs:** $4.84 RT per contract commission (program convention; MNQ schedule user's); ledger $ include a stored all-in $100.13 per 10-lot trade (= 0.50 pt, composition not itemised). Net pts = pts - 0.50.

## 2. Identity test (runnable)
Rows: rows2_HM_t75_s90.parquet (et_in = entry-bar end stamp ET). Filter: label day (et_in + 6 h date) <= 20260206 and NY-AM by et_in minute-of-day in [570, 720).
| window (label days) | expected NY-AM trades | first et_in | last et_in | mean $/trade (10 lots) | win | exits T/S/TB |
|---|---|---|---|---|---|---|
| PRE 2024-02-01..2025-06-30 | **427** | 2024-02-02 10:42 | 2025-06-23 11:08 | 2,443 | 61.4% | 248 / 145 / 34 |
| HOLD 2025-07-01..2026-02-06 | **197** | 2025-07-01 11:12 | 2026-02-06 11:40 | 1,798 | 58.4% | 108 / 68 / 21 |
| 2023 span 2023-04-01..2024-01-31 | 156 | 2023-04-05 09:50 | 2024-01-31 11:56 | 2,103 | 59.6% | 78 / 46 / 32 |
| ALL 2023-02-10..2026-02-06 | 812 | 2023-02-10 09:53 | 2026-02-06 11:40 | 2,005 | 59.7% | 447 / 275 / 90 |
(The "first/last" are the first and last trades of the window, not the window edges.) Matches the ledger row (427, 2,443, HOLD 197 / 1,798, span 2,103).
**Test:** run NT8 HM (signal above) with 75/90 on the 1-min series through the full day (18:00 to 15:00 signals, 15:00-17:59 blocked, one open trade, **no 09:00-09:58 guard**) and filter by the entry-bar end stamp. Pass if: count within +/-2% per window, entry (minute, side) mismatch <= 3% (the benchmark-to-live HM match was 97.7%; the bar feed differs from the vendor by a tick on 3.3% of bars, FR_SEC5 line 170), exit type + exit minute (+/-2 min) mismatch <= 3%, mean pts within 0.5. Run the all-hours chain, not a NY-AM-only book (see 0.3).

## 3. Data, roll, holidays
Continuous front NQ; the VWAP/HMA/EMA200 run continuously, so adjusted history and the exact volume series matter (vendor volume vs NT8 feed differ on 4.8% of bars). Flat 16:55-18:00, no trade crosses a roll. Early closes flatten on the final bar.

## 4. Position limits
10 lots, one position per book. The same entries are what the live HM book takes at 60/60; as a replacement bracket for NY-AM entries it competes with the live HM book (do not run both). Stack concurrency is the lead's computation.

## 5. Backtest expectation (ledger, per trade at 10 lots, unlocked)
| window | n | trades/wk | mean $/trade | mean R (net 0.50 pt) | pts net | SE of R |
|---|---|---|---|---|---|---|
| PRE (75 wk) | 427 | 5.69 | 2,443 | +0.136 | +12.21 | 0.042 |
| HOLD (about 31.5 wk) | 197 | about 6.3 | 1,798 | +0.100 | +8.99 | 0.061 |
| 2023 span | 156 | about 3.6 | 2,103 | +0.117 | +10.52 | 0.065 |
PRE t 3.59, MDE per trade $1,904, HOLD both halves positive (H2-2025 816, 2026 stub 5,651 per trade), by year 2023 2,889 / 2024 2,768 / 2025 1,038 / 2026 stub 5,651, 2023 span positive (2,103) (ASIA/LONDON cells are negative there; NY-AM positive). At $1,000 risk per trade: PRE about +$136/trade (about $770/wk at 5.7 trades/wk), HOLD +$100.

## 6. What could kill it
- **The 09:00-09:58 guard (live parameter, open).** Roughly a quarter of the cell's trades have a signal bar in 09:00-09:58 (PRE 106 of 427, HOLD 59 of 197, 2023 span 35 of 156) and they carry the edge: mean $/trade in PRE 4,221 for those vs 1,856 for the rest; HOLD 2,246 vs 1,606. FR_SEC5 (line 3 and 170) describes the live NT8 HM as "entries 18:00-15:00 ET except 09:00-09:58"; P9_NT8_SPEC line 69 and firmlib say the BENCH3 benchmark removed that guard. Which is live today was not verifiable in the autopilot files (live DualStrat2 properties not read). If the live HM keeps the guard, the 09:30-09:58 part of this cell is not the live engine and the cell must be restricted to 09:59-12:00 (then the expected PRE count is about 321, mean about 1,856; HOLD about 138, 1,606).
- **Chain dependence** (0.3): a NY-AM-only build differs from the ledger chain on 38% of days.
- **Selection.** One of 54 bracket cells for HM; the same NY-AM entries at the live 60/60 bracket earn PRE 758 (554 trades), HOLD 1,305 (249), 2023 span 76 (245) per 10-lot trade. Pooled all-hours calibrated-mapped paired effect vs the live bracket +0.27 pt [-1.51, +2.03], MDE 2.49, HOLD -1.06, 2023 span -1.93 (out/ba/stage2_screen.csv; DS3_TBRACKET section 5: no HM cell had CI above 0). BOF not cleared; cluster 781.
- **Stored-fill dependence.** Break-even extra cost per trade from the ledger: HOLD 1,798/200 = **9.0 pt** (PRE 12.2 pt, 2023 span 10.5 pt), the widest margin of the three ba2 cells, against about 1-1.5 pt per stop exit from the live replay measurements (DS3_LIVE_CONFIG: entry +0.45, stop -0.52, fallback -1.74 pt). NY-AM entries are at the open volatility; stop-gap fills (min -107 pt seen in NT8 on 60-pt stops, FR_SEC5 line 169) matter more with a 90-pt stop (loss capped at -90 in the rows apart from the gap rule).
- **Few independent trades**: 427 PRE and 197 HOLD trades, HOLD t about 1.6 (mean R 0.10, SE 0.061); the HM benchmark itself lost edge after the engine reconciliation (HM 3.96 -> 1.53 pt/trade, FR_SEC5 line 171).
- Long holds (8% hit 16:55), news days (no calendar block), tie/ordering inside a 1-min bar, vendor vs NT8 volume/bar differences (VWAP-based signal).

## 7. Open items
- Confirm the live HM guard setting (09:00-09:58) from the live DualStrat2 properties (user side), then fix the cell window (09:30 vs 09:59).
- Direct-L2 re-run at the cell's lot level (D3SA / DS3_SESSION2_A_D6) is the eligibility gate. Session lock thresholds for a 90-pt stop; handoff rule (D3SD).
