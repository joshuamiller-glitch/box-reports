# DS3_SPEC_ba2_KB_t60_s75_SESSION - executability spec and identity test (D3SSE2, 2026-10-28)

Research output for the Sim leader; NOT a live recommendation. No execution-server, chart or live change. **Session cell, tier SESSION-CANDIDATE (BOF not cleared), basis STORED (ledger label "rows-as-stored": exact bracket points from the 1-s path with the stored $100.13 per 10-lot trade cost; NOT mapped to P9 and NOT direct-L2). NOT live-eligible until the live-latency result (D3SA, DS3_SESSION2_A) lands.** Cell = ASIA entries (18:00-02:00 ET) of the live KB engine with the bracket target 60 pt / stop 75 pt.

Sources: ledger row "ba2/KB_t60_s75" (autopilot/DS3_SESSION_2_LEDGER.md section 3, line 56), rows l2vast/ds3/out/ba/rows2_KB_t60_s75.parquet (ledger_index cid 1616), generator l2vast/ds3/code/ba/ba_rows2.py (gen, lines 110-134 of that file), signal l2vast/ds3/code/te/te_sig.py fam_kelt (lines 98-100), cell definition te_cells.py lines 94-95, live spec autopilot/DS3_SPEC_TE7_kelt3m_n14_m1.0.md, live config autopilot/forward/series/DS3_LIVE_CONFIG.json book "KB".

## 0. Is it the live KB engine? (verified, not assumed)
**Yes for the entry rule; the bracket (stop 60 -> 75) and the session restriction are the only intended differences. Items that also differ are listed.**
- Live config book KB = cell TE7_kelt3m_n14_m1.0 (record ds3_TE_TE7_kelt3m_n14_m1.0, 10 lots, bracket 60/60, 26.8 trades/wk). ba_rows.py line 150: BOOKS['KB']='TE7_kelt3m_n14_m1.0'; ba_rows2.py events() line 109 builds the entries with te_cells.build of exactly that cell (kelt, k=3, n=14, m=1.0). Same signal function, same params as the live spec.
- Identity at the live bracket (run today): rows2_KB_t60_s60.parquet (this generator at 60/60) vs ba/rows_KB_t60_s60.parquet (built by te_core.gen_entries, the T-ENTRY base-row function): 8593 vs 8593 trades, 0 entries only in one file, 0 exit-bar differences, 0 point differences. The T-ENTRY base rows are the rows the live spec's NT8 identity test matched (DS3_SPEC_TE7 section 2: 8504 library trades, 0.51% entry mismatch). So with bracket 60/60 the ba2 generator IS the live KB engine; nothing else in the entry path changed.
- What differs from the live KB engine (complete list):
  1. **Stop 75 pt instead of 60 pt** (target stays 60 pt). R:R 0.8. Long/short symmetric. Risk per NQ lot rises from $1,200 to $1,500.
  2. **Different trade sequence.** Exits happen at different bars, so the one-open-trade rule drops different later signals: 7,572 trades over 2023-02-10..2026-10-23 (all hours) at 60/75 vs 8,593 at 60/60. The 60/75 trade list is not a subset of the live list.
  3. **Session restriction**: only entries whose entry-bar end stamp is 18:00-02:00 ET are in the cell (live KB trades 18:00-15:00). Exits are not session-limited (run to bracket or 16:55 flat).
  4. **Fills basis**: the cell $ are bracket points at the exact level (stop gap rule: stop fill = min/max(level, previous-second close), nt8sim STOP_GAP), entry at the open of the entry bar, cost $100.13 per 10-lot trade (read from the TP net convention). The live KB series in DS3_LIVE_CONFIG uses the direct-L2 S10x1 + XJ3 pricing; this cell has not been re-priced that way (D3SA pending).
  5. Locks: the live KB book runs day -2R/+5R, give-back, week floor in R = 10 x 60 x $20 = $12,000. The ledger numbers are WITHOUT locks (plain per-trade $). A session book needs its own lock thresholds (a 75-pt stop at 10 lots = $15,000 = 1.25 of the live R).
- Not changed: signal bars (3-min), indicator, edge trigger, 15:00-17:59 signal block, entry at next 1-min open, flat at 16:55, early-close handling (same functions).

## 1. Rule (NT8)
- **Bars:** NQ 3-minute time bars (:00/:03/..., aligned to the epoch minute // 3, which is clock-aligned in ET), END-time stamped in NT8; plus a 1-minute data series for the entry and the bracket. Globex template, label day 18:00-17:59 ET. Continuous back-adjusted front month.
- **Indicator (te_sig.fam_kelt):** mid = EMA(Close, 14), alpha = 2/15, seeded with the first close (te_sig.ema, line 40-43); ATR(10) with first value H-L and recursion ATR = (ATR[1]*9 + TR)/10, TR = max(H-L, |H-C[1]|, |L-C[1]|) (atr_w, lines 44-49; NOT an SMA seed); upper = mid + 1.0*ATR, lower = mid - 1.0*ATR (all on the same bar's values).
- **Signal (edge):** buy on the 3-min bar whose Close > upper while the previous bar's Close was not above its upper; sell on Close < lower while the previous bar was not below its lower; the two sides are edge-triggered independently. Read on the CLOSED bar (OnBarClose).
- **Entry:** market order at the open of the next 1-minute bar after the signal bar closes; the next 1-min bar must be consecutive (no gap), else no trade (te_sig.to_ev). Signals are dropped if the signal bar's LAST minute (bar-start minute-of-day) is in 15:00-17:59 ET (te_core._BLOCKSIG). One open trade at a time: a signal on or before the exit minute of the open trade (bar <= busy) is dropped, not queued (ba_rows2.gen line 114). 10 lots as 10 x 1-lot market slices 2 s apart in the direct pricing.
- **Session filter (this cell):** keep the trade if the entry-bar END stamp (= entry-bar start + 1 minute = actual entry instant + 1 min; the ledger column et_in) has minute-of-day >= 18:00 or < 02:00 (ss2lib.sess_of_min: m>=1080 or m<120). The earliest observed ASIA entry is 18:04 (3-min bar boundary), the latest 01:59 stamp. Signals outside the window are simply not taken; they still do NOT occupy the book in a session-only build (see 2, open item).
- **Bracket (this cell):** stop-market 75 pt = 300 ticks and limit target 60 pt = 240 ticks, OCO, from the entry price (rows: from the entry bar's open; replay in the direct arm: from each slice fill). Observed in the rows: every target is exactly +60.00 pt, every stop exactly -75.00 pt (4061 targets, 3125 stops, 386 time exits over all hours). If both levels fall in one second the sim checks the stop first.
- **Flat rule:** market flat at the close of the bar ending >= 16:55 ET (the blocked minute); early-close days flatten at the final bar. A trade entered at 18:00-01:59 therefore may run through London, PRE and NY (mean 345 bars = 5.7 h, median 250 bars in PRE; 2% of ASIA trades reach 16:55).
- **Session window (ET):** entries 18:00-02:00 only (see above). Handoff: nothing is closed at 02:00.
- **Order types:** MARKET entry (sliced in the direct pricing), STOP-MARKET + LIMIT target OCO, MARKET time exit. The XJ3 stop-join layer of the live spec is NOT part of this cell's stored $.
- **Lots at $1,000 risk per trade:** NQ risk per lot = 75 pt x $20 = $1,500, so $1,000 risk = 0.67 NQ lot = NOT whole-lot tradable on NQ; on MNQ ($2/pt, $150 stop risk per contract) 6 contracts = $900 risk (7 = $1,050). Reference sizing in the ledger: 10 NQ lots ($15,000 stop risk, 1.25 x the live R).
- **Costs:** $4.84 RT per contract commission as the program convention (applies per NQ lot; the MNQ commission schedule is the user's to set); ledger $ include a stored all-in cost of $100.13 per 10-lot trade (= 0.50 pt; this contains the commission and the execution-cost allowance, composition not itemised in ss2lib). Pts/trade net of that cost = pts - 0.50.

## 2. Identity test (runnable)
Rows: l2vast/ds3/out/ba/rows2_KB_t60_s75.parquet (columns et_in = entry-bar end stamp ET, ei/xi bar indices, side, pts, Exit name). Ledger filter: label day (et_in + 6 h, calendar date) <= 20260206 (the UNTOUCHED guard) and session ASIA by et_in minute-of-day (m>=1080 or m<120).
| window (label days) | expected ASIA trades | first et_in | last et_in | mean $/trade (10 lots, pts*200-100.13) | win | exits T/S/TB |
|---|---|---|---|---|---|---|
| PRE 2024-02-01..2025-06-30 | **704** | 2024-01-31 18:10 | 2025-06-29 19:40 | 1,445 | 61.4% | 427 / 271 / 6 |
| HOLD 2025-07-01..2026-02-06 | **321** | 2025-06-30 18:04 | 2026-02-06 01:43 | 600 | 57.9% | 186 / 133 / 2 |
| 2023 span 2023-04-01..2024-01-31 | 243 | 2023-04-02 18:04 | 2024-01-30 19:34 | 84 | 56.0% | 128 / 99 / 16 |
| ALL 2023-02-10..2026-02-06 | 1,311 | 2023-02-12 18:04 | 2026-02-06 01:43 | 928 | 59.3% | 764 / 522 / 25 |
These counts reproduce the ledger row (704, mean 1,445, HOLD 321 / 600, 2023 span 84).
**Test:** run the NT8 KB logic with stop 75 / target 60 on the 3-min + 1-min series with the all-hours one-at-a-time chain (do NOT switch off non-ASIA entries when building the reference: the library chain includes London/NY trades that keep the book busy), then filter to ASIA by the entry-bar end stamp. Pass if: trade count within +/-2% of the table per window, entry (minute, side) mismatch <= 2%, exit-type + exit-minute (+/-2 min) mismatch <= 3%, mean pts/trade within 0.5 pt. Known residuals (same causes as the live spec, 0.5-1%): stop and target both inside one 1-min bar (library uses the 1-s tape; a 1-min replay takes the stop), exit stamps one minute apart, holiday early closes, indicator warm-up. For a 75-pt stop with a 60-pt target the both-in-one-bar case is rarer than at 60/60.
Check on the session-only variant: for ASIA the all-hours chain and an ASIA-only book give the same entries (the book is flat 16:55-18:00 so nothing carries into 18:00 and signals before 18:00 are blocked), so the ASIA table above is also the expected count of an ASIA-only build. (For NY-AM cells this is NOT true; see the HM spec.)

## 3. Data, roll, holidays
Continuous front NQ, back-adjusted; indicators run continuously across days (MergeBackAdjusted). Flat 16:55-18:00 so no trade crosses a roll. No bars on holidays; early closes flatten on the final bar. Data end of the rows 2026-10-23, ledger window ends 2026-02-06.

## 4. Position limits
10 NQ lots (or the MNQ equivalent) and one position per book; concurrent with the live KB engine: the live KB book trades the same entries at the same minutes with a 60-pt stop. Running both would double-count the same signal; the session cell is a REPLACEMENT bracket for ASIA entries, not an add. Stack concurrency is the lead's computation.

## 5. Backtest expectation (ledger, per trade at 10 lots, unlocked)
| window | n | trades/wk | mean $/trade | mean R (net of 0.50 pt) | pts net | SE of R |
|---|---|---|---|---|---|---|
| PRE (75 wk) | 704 | 9.39 | 1,445 | +0.096 | +7.22 | 0.033 |
| HOLD (about 31 wk) | 321 | about 10.4 | 600 | +0.040 | +3.00 | 0.049 |
| 2023 span | 243 | about 5.7 | 84 | +0.006 | +0.42 | 0.056 |
PRE t 3.44, PRE MDE per trade $1,175, PRE CI above 0, HOLD both halves positive (H2-2025 494, 2026 stub 954). At $1,000 risk per trade the PRE expectation is about +$96/trade (R x $1,000), HOLD +$40, i.e. roughly $900 and $400 per week at 9.4 trades/wk. By year per trade (10 lots): 2023 659, 2024 1,113, 2025 991, 2026 stub 954.

## 6. What could kill it
- **Selection.** The bracket is one cell of a 9 x 6 grid per engine chosen by the session screen; the same entries at the live 60/60 bracket earn in ASIA PRE 767 (779 trades), HOLD 80 (371), 2023 span -391 (251) per 10-lot trade. The BA bracket grid pooled (all hours) found no cell with a paired CI above 0 vs the base; for this cell the calibrated-mapped paired effect is +0.01 pt [-0.63, +0.75] (MDE 1.04), HOLD -0.34, 2023 span +0.65 (autopilot/DS3_TBRACKET.md section 5, out/ba/stage2_screen.csv). Ledger: best-of-F not cleared (BOF: not cleared), cluster 788 (shared with 420 bracket variants).
- **Stored-fill dependence.** Rows are stored bracket points, not mapped and not direct. Slippage break-even from the ledger: HOLD mean $600 / (10 lots x $20) = **3.0 pt extra cost per trade** (PRE 7.2 pt, 2023 span 0.4 pt). The live replay measurements in DS3_LIVE_CONFIG (entry +0.45 pt, stop -0.52 pt, fallback -1.74 pt, target 0) cost roughly 1.0-1.5 pt per trade on a stop exit, i.e. a third to a half of the HOLD edge; the 2023-span break-even is already about 0.
- **2023 span** is flat (84/trade, +0.006 R), the ASIA-cell regime pattern (ASIA/LONDON cells earn from 2024; the 2023 span is the contrary year).
- **HOLD is weaker than PRE** (600 vs 1,445) and the HOLD t-stat is below 1 (mean R +0.04, SE 0.049).
- Long holds: mean 5.7 h; ASIA entries are exposed through London and NY news (no news block in the rule).
- Path dependence: trades dropped by the one-at-a-time rule differ from the live KB list; the identity must be run with the full chain.
- Tie/ordering inside a 1-min bar, vendor vs NT8 bar differences, EMA/ATR warm-up.
- Capacity/session handoff: no 02:00 flat; if the session book is required flat at 02:00 the stored numbers do not apply (re-run needed).

## 7. Open items
- Direct-L2 re-run at the cell's lot level (D3SA / DS3_SESSION2_A_D6) is the live-eligibility gate; this spec's $ are STORED.
- Session lock thresholds for a 75-pt stop; handoff rule (D3SD).
