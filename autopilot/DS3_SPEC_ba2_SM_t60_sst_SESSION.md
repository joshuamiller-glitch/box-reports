# DS3_SPEC_ba2_SM_t60_sst_SESSION - executability spec and identity test (D3SSE2, 2026-10-28)

Research output for the Sim leader; NOT a live recommendation. No execution-server, chart or live change. **Session cell, tier SESSION-CANDIDATE (BOF not cleared), basis STORED (ledger label "rows-as-stored": exact bracket points from the 1-s path, stored $100.13 per 10-lot trade cost; NOT mapped to P9, NOT direct-L2). NOT live-eligible until the live-latency result (D3SA, DS3_SESSION2_A) lands.** Cell = ASIA entries (18:00-02:00 ET) of the live SM engine with a 60-pt target and a signal-bar STRUCTURE stop.

**Definition correction ("sst").** The coordinator note read "sst" as a Supertrend-line stop. The code says otherwise: the cell id is E_t{target}_s{stop} and the stop token is 'st', so "sst" = "s" + "st" = the STRUCTURE stop, not the Supertrend line. ba_rows2.py header and lines 118-120; ba_prereg2.py line 13: "structure stop (signal-bar extreme +5 pt)". A Supertrend-line stop is NOT what these rows contain.

Sources: ledger row "ba2/SM_t60_sst" (autopilot/DS3_SESSION_2_LEDGER.md line 100), rows l2vast/ds3/out/ba/rows2_SM_t60_sst.parquet (ledger_index cid 1672), generator l2vast/ds3/code/ba/ba_rows2.py (gen lines 110-134, K table line 105), signal l2vast/ds3/code/te/te_sig.py fam_st (line 92) + supertrend (lines 51-61) + atr_w (44-49), cell te_cells.py line 92, live spec autopilot/DS3_SPEC_TE6_st10m_n7_m3.0.md, live config DS3_LIVE_CONFIG.json book "SM".

## 0. Is it the live SM engine? (verified, not assumed)
**Yes for the entry rule. The stop (60 -> structure stop 20-120 pt) and the session restriction are the intended differences; the list below is complete.**
- DS3_LIVE_CONFIG book SM = TE6_st10m_n7_m3.0 (record ds3_TE_TE6_st10m_n7_m3.0, 10 lots, bracket 60/60, 12.2 trades/wk). ba_rows.py line 150: BOOKS['SM']='TE6_st10m_n7_m3.0'; ba_rows2.py line 109 builds events with te_cells.build of that cell (st, k=10, n=7, m=3.0).
- Identity at the live bracket (run today): rows2_SM_t60_s60.parquet vs ba/rows_SM_t60_s60.parquet (te_core.gen_entries, the T-ENTRY base rows the live spec's identity test used: 2382 library trades, 0.59% entry mismatch): 2397 vs 2397 trades, 0 entries only in one file, 0 exit-bar differences, 0 point differences.
- What differs from the live SM engine:
  1. **Stop = structure stop (variable 20-120 pt) instead of 60 pt; target stays 60 pt.** Exact rule in section 1. R:R varies per trade (60/20 = 3.0 at the floor). Median stop in ASIA 20.0-20.25 pt, mean 31 pt (PRE), 50% of PRE trades and 81% of 2023-span trades sit exactly on the 20-pt floor.
  2. **Different trade chain.** Exits move, so dropped signals differ: 2,874 trades (all hours, 2023-02-10..2026-10-23) at 60/sst vs 2,397 at 60/60 (more trades: shorter stops free the book earlier).
  3. **Session restriction**: entries with entry-bar end stamp 18:00-02:00 ET only; exits not session-limited (16:55 flat).
  4. Fills: stored bracket points (stop gap rule), entry at the entry-bar open, cost $100.13 per 10-lot trade; the live pricing (S10x1 slices + XJ3 stop-join) is not applied (D3SA pending). In the direct replay the stop distance is applied in ticks from each slice fill (ba_replay: ST = bracket x 4), so the stop LEVEL moves with entry slippage, whereas the rows put it at open -/+ sd.
  5. Locks: unlocked $ in the ledger. Live SM R = 10 x 60 x $20 = $12,000; this cell's risk per trade is 10 x sd x $20 = $4,000 at sd 20.
- Not changed: signal definition, 15:00-17:59 signal block, next-1-min-open entry, 16:55 flat.

## 1. Rule (NT8)
- **Bars:** signal on NQ 10-minute time bars (:00/:10/..., END-time stamped); a 1-minute series for the entry, the structure stop and the bracket. Globex, label day 18:00-17:59 ET, continuous back-adjusted.
- **Indicator (te_sig.supertrend, as tested, not the textbook flip test):** ATR(7): first value H-L, then ATR = (ATR[1]*6 + TR)/7, TR = max(H-L, |H-C[1]|, |L-C[1]|); hl2 = (H+L)/2; ub = hl2 + 3.0*ATR; lb = hl2 - 3.0*ATR; fub = ub if (ub < fub[1] or Close[1] > fub[1]) else fub[1]; flb = lb if (lb > flb[1] or Close[1] < flb[1]) else flb[1]; direction d starts +1; if d == +1 and Close < flb (current bar's band) then d = -1; if d == -1 and Close > fub (current bar) then d = +1.
- **Signal:** the 10-min bar on which d changes (edge only; +1 buy, -1 sell), read on the closed bar. No EMA filter.
- **Entry:** market order at the open of the next 1-minute bar after the signal bar closes (the next 1-min bar must be consecutive). Signals whose last minute starts in 15:00-17:59 ET are dropped. One open trade; signals on or before the exit minute are dropped. 10 lots as 10 x 1-lot slices 2 s apart in the direct pricing.
- **Structure stop (ba_rows2.gen lines 118-120, K['SM']=10):** let bar = the entry 1-min bar and px = its open. The k = 10 completed 1-min bars immediately before it (bars bar-10 .. bar-1, which are exactly the 10 minutes of the 10-min signal bar). Long: sd = px - min(Low over those 10 bars) + 5.0; short: sd = max(High over those 10 bars) - px + 5.0; sd = min(max(sd, 20.0), 120.0). Stop level = px - side*sd; stop-market = 4*sd ticks. sd lies on the 0.25 grid so ticks are integers.
- **Target:** limit 60 pt = 240 ticks, fixed (observed: every target exactly +60.00, 1136 targets of 2874 all-hours trades; stops are -sd: 562 exactly -20.0, 43 exactly -120.0). OCO from the entry; stop checked before target inside a second.
- **Flat rule:** market flat at the close of the bar ending >= 16:55 ET; early closes at the final bar. ASIA trades: mean 196 bars (3.3 h), median 136 bars; 4 time exits of 543 (all hours ASIA ALL).
- **Session filter:** keep a trade if the entry-bar END stamp (ledger et_in = entry instant + 1 min) has minute-of-day >= 18:00 or < 02:00 (ss2lib 1080 / 120). Earliest ASIA stamps are on 10-min boundaries +1 min (18:11, ...).
- **Order types:** MARKET entry (sliced in the direct pricing), STOP-MARKET + LIMIT target OCO, MARKET time exit; the stored $ include no stop-join.
- **Lots at $1,000 risk per trade (sd varies, so lots vary per trade):** NQ risk per lot = sd x $20: sd 20 -> $400 -> 2 NQ lots ($800); sd 25-50 -> 1 lot ($500-$1,000); sd > 50 -> 0 whole NQ lots. MNQ ($2/pt): n = floor(1000 / (2 x sd)): sd 20 -> 25 contracts, sd 33 -> 15, sd 60 -> 8, sd 120 -> 4. Ledger reference sizing: 10 NQ lots flat, so the ledger $ per trade is NOT constant risk.
- **Costs:** $4.84 RT per contract commission (program convention); ledger $ include a stored all-in $100.13 per 10-lot trade (= 0.50 pt, composition not itemised). A 0.50 pt cost is 2.5% of a 20-pt stop. Net pts = pts - 0.50.

## 2. Identity test (runnable)
Rows rows2_SM_t60_sst.parquet; filter: label day <= 20260206 and ASIA by et_in minute-of-day (>= 1080 or < 120).
| window (label days) | expected ASIA trades | first et_in | last et_in | mean $/trade (10 lots) | win | exits T/S/TB | trades at 20-pt floor |
|---|---|---|---|---|---|---|---|
| PRE 2024-02-01..2025-06-30 | **264** | 2024-02-04 19:51 | 2025-06-25 23:21 | 1,539 | 40.9% | 107 / 156 / 1 | 131 (50%), cap120: 5 |
| HOLD 2025-07-01..2026-02-06 | **123** | 2025-06-30 23:31 | 2026-02-05 20:51 | 459 | 34.1% | 42 / 81 / 0 | 62 |
| 2023 span 2023-04-01..2024-01-31 | 137 | 2023-04-02 18:11 | 2024-01-28 20:31 | 953 | 32.8% | 44 / 90 / 3 | 111 |
| ALL 2023-02-10..2026-02-06 | 543 | 2023-02-14 01:41 | 2026-02-05 20:51 | 1,175 | 37.4% | 201 / 338 / 4 | - |
Matches the ledger row (264, 1,539, HOLD 123 / 459, span 953).
**Test:** replay NT8 SM (ATR7 x 3.0 Supertrend, 10-min) with the structure stop through the full day (all-hours chain, then filter ASIA by the entry-bar end stamp; the ASIA chain is independent of other sessions because the book is flat 16:55-18:00). Per trade also check sd against the rows' `bracket` column (tolerance 0.25 pt). Pass if: count within +/-2% per window, entry (minute, side) mismatch <= 2% (live spec 0.59%), bracket sd equal within 0.25 pt on >= 98% of trades, exit type + exit minute (+/-2 min) mismatch <= 3%, mean pts within 0.5. Residuals as in the live spec (stop and target in one 1-min bar; with a 20-pt stop this tie case is MORE frequent than at 60/60, so replay on a 1-s or tick series if possible).

## 3. Data, roll, holidays
Continuous front NQ, back-adjusted; Supertrend runs continuously across days. The structure stop uses the 10 one-minute bars before entry, which on a 10-min boundary after a holiday/gap may include a prior-session minute only if bars are missing (the entry itself requires consecutive minutes). Flat 16:55-18:00, no roll crossing.

## 4. Position limits
10 lots (ledger) or the MNQ equivalent, one position per book. It trades the SAME entries as the live SM book; use it as a replacement bracket for ASIA, never in addition to the live SM book. Stack concurrency is the lead's computation.

## 5. Backtest expectation (ledger, per trade at 10 lots, unlocked)
| window | n | trades/wk | mean $/trade | mean R (net 0.50 pt, R = sd) | pts net | SE of R |
|---|---|---|---|---|---|---|
| PRE (75 wk) | 264 | 3.52 | 1,539 | +0.274 | +7.70 | 0.102 |
| HOLD (about 31.5 wk) | 123 | about 3.9 | 459 | +0.074 | +2.30 | 0.144 |
| 2023 span | 137 | about 3.2 | 953 | +0.214 | +4.76 | 0.153 |
PRE t 3.12, MDE per trade $1,380, HOLD H2-2025 246 / 2026 stub 1,339 per trade, by year 2023 926 / 2024 1,228 / 2025 1,148 / 2026 stub 1,339. At $1,000 risk per trade: PRE about +$274/trade (about $960/wk at 3.5 trades/wk), HOLD about +$74/trade.

## 6. What could kill it
- **It does not beat the live bracket in the session.** The same ASIA entries with the live 60/60 bracket (rows2_SM_t60_s60) earn PRE 1,840 (242 trades), HOLD 544 (113), 2023 span 467 (116) per 10-lot trade, versus 1,539 / 459 / 953 here. Pooled all-hours the calibrated-mapped paired effect of this bracket vs the live bracket is -0.88 pt [-2.55, +0.78], MDE 2.41, HOLD -0.63 (out/ba/stage2_screen.csv; DS3_TBRACKET section 5: no SM cell had CI above 0; the best SM cell was t60_s90). Unless the D3SA live-latency run reverses this, the live SM bracket is the better ASIA leg; the structure stop buys a different R profile, not a higher mean. BOF not cleared; cluster 802, all-hours pooled PRE mean 435 per trade.
- **Stop is mostly the 20-pt floor** (50% PRE, 81% 2023 span): the cell is effectively "60 target / 20 stop with a wider stop on wide signal bars". A 20-pt (80-tick) stop on NQ in ASIA is exposed to stop-fill slippage and noise; win rate 41% PRE, 34% HOLD (required win about 43% before cost at 60/20). Break-even extra cost per trade from the ledger: HOLD 459/200 = **2.3 pt** (PRE 7.7, 2023 span 4.8); the live replay costs of about 1.0-1.5 pt per stop exit (DS3_LIVE_CONFIG: entry +0.45, stop -0.52, fallback -1.74 pt) take about 45-65% of the HOLD edge (66% of HOLD trades are stop exits).
- **Stored-fill dependence** as above; the stop level is open -/+ sd in the rows but sd ticks from each fill in the direct replay.
- **HOLD t about 0.5** (mean R +0.074, SE 0.144); only 123 HOLD trades.
- Selection: one of 54 SM bracket cells (6 stops x 9 targets); 2023 span positive here, unlike most ASIA cells.
- Variable risk per trade: at a fixed 10 lots the dollar risk per trade runs $4,000-$24,000; with $1,000-risk sizing the MNQ count (4-25 contracts) means MNQ liquidity/commission, not NQ lots, drives the real outcome.
- Tie/ordering inside a 1-min bar is most important for a 20-pt stop. Vendor vs NT8 bar differences move the extremes used by the stop (sd quantised to 0.25 pt).

## 7. Open items
- Direct-L2 re-run at the cell's lot level (D3SA) is the eligibility gate; consider running SM_t60_s60 ASIA as the control in the same replay.
- Session lock thresholds for a variable-risk cell; handoff rule (D3SD).
