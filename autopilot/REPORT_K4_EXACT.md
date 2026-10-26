# REPORT K4_EXACT (2026-10-19) - FEES update first
Cost standard FEES.md (user): ES and NQ $4.84 round trip per contract (incl. $0.25/side routing), applied to all ES/NQ legs incl. the ES hedge; RTY, YM, GC, CL, ZN, 6E, 6J are NOT in the user's list, so they keep $4.36 (stated); +1 tick/side as before. Same METHOD-2 12/3/3, drift-matched null, fills at the next print (headline).
| 17-cell family | cost | hedged Sharpe | unhedged Sharpe | weekly mean h/u | p5 / p95 (hedged) | worst week h/u | max DD h/u | best-of-F 1208/761/594 (h ; u) | gates a-d |
|---|---|---|---|---|---|---|---|---|---|
| **NEW fees (headline fill, next print)** | ES/NQ 4.84, rest 4.36 | **1.161** | **1.418** | $2,019 / $2,465 | -$6,981 / +$16,592 | -$46,990 / -$49,704 | $74.4k / $72.4k | 0.000 / 0.000 / 0.000 ; 0.000 / 0.0001 / 0.0007 | pass |
| historical $4.36 (headline fill) | 4.36 | 1.163 | 1.419 | $2,021 / $2,466 | -$6,981 / +$16,596 | -$46,982 / -$49,700 | $74.4k / $72.4k | same | pass |
Fill-delay test with the new fees (Sharpe hedged / unhedged, x headline): next print 1.161 / 1.418; +1 s 1.156 / 1.414 (0.996 / 0.997); **+5 s 1.172 / 1.427 (1.009 / 1.006); +30 s 1.167 / 1.428 (1.005 / 1.007)**; +60 s 1.175 / 1.433. The 85% condition still passes (both). Hedge refit on the rescored family's own folds: 0.9027 ES (0.903 before): unchanged to 3 decimals; contracts per cell unchanged (gross 2.852 vs 2.853 NQ-eq). Effect of the fee change: -0.002 Sharpe hedged, -0.001 unhedged (K4 trades ~1.5 days/week with small size; the ES/NQ legs are a minority of fee-bearing contracts). Verdict unchanged: gates a-d pass, best-of-F fails. Zip re-shipped only with refreshed bands (hedge/weights change < 0.1%). Not verified: the fee proxies flagged in FEES.md (NQ, micros).

Directive K4-EXACT + user decision 'DECISIONS 10-19' (decide on the bar close, fill at the NEXT print + 1 tick is NOT lookahead; the 9 removed cells stay removed). Full per-cell inputs with availability times and code-line cites: outputs/k4/K4_EXACT_CELLS.csv.

## 1. Cell table (what the scored series actually did)
Common to the 16 index cells: decision features include px[e] = close of the bar OPENING 16:16 ET = the last print before 16:17:00 (ap_j_data.py:12-15); ADR = rolling-20 mean of prior full-session ranges (ap_i_common.py:21); VIX/VIX3M/VVIX same-date close, last DBIX print 16:15:01 (ap_k_fams.py:173-174); COT lagged to Tuesday+7d (:177); calendar flags; fill in the scored engine = the same px[e] +1 tick/side +$4.36 (ap_j_fams.py:34-38).
| cell | weight (pack) | clock / decision price | instruments, sides | hold, exit | verdict |
|---|---|---|---|---|---|
| K4_d2_1_0.08_longonly | 0.0380 | 16:17:00 ET (close of bar opening 16:16) / px[e] = print at 16:17:00 ET | ES,NQ,RTY,YM; LONG only (p>=0.58) | 1 label day; time exit at next label day's 16:17:00 print (px[e+1]) | SAME_PRINT |
| K4V2_d2_1_0.08_longonly | 0.0380 | 16:17:00 ET (close of bar opening 16:16) / px[e] = print at 16:17:00 ET | ES,NQ,RTY,YM; LONG only (p>=0.58) | 1 label day; time exit at next label day's 16:17:00 print (px[e+1]) | SAME_PRINT |
| R2_PRICE | 0.0196 | 16:17:00 ET (close of bar opening 16:16) / px[e] = print at 16:17:00 ET | ES,NQ,RTY,YM; LONG only (p>=0.58) | 1 label day; time exit at next label day's 16:17:00 print (px[e+1]) | SAME_PRINT |
| R2_PRICE+VIX | 0.0224 | 16:17:00 ET (close of bar opening 16:16) / px[e] = print at 16:17:00 ET | ES,NQ,RTY,YM; LONG only (p>=0.58) | 1 label day; time exit at next label day's 16:17:00 print (px[e+1]) | SAME_PRINT |
| R2_PRICE+COT | 0.0168 | 16:17:00 ET (close of bar opening 16:16) / px[e] = print at 16:17:00 ET | ES,NQ,RTY,YM; LONG only (p>=0.58) | 1 label day; time exit at next label day's 16:17:00 print (px[e+1]) | SAME_PRINT |
| R2_PRICE+CAL | 0.0000 | 16:17:00 ET (close of bar opening 16:16) / px[e] = print at 16:17:00 ET | ES,NQ,RTY,YM; LONG only (p>=0.58) | 1 label day; time exit at next label day's 16:17:00 print (px[e+1]) | SAME_PRINT |
| R2_FULL-VIX | 0.0361 | 16:17:00 ET (close of bar opening 16:16) / px[e] = print at 16:17:00 ET | ES,NQ,RTY,YM; LONG only (p>=0.58) | 1 label day; time exit at next label day's 16:17:00 print (px[e+1]) | SAME_PRINT |
| R2_FULL-COT | 0.0374 | 16:17:00 ET (close of bar opening 16:16) / px[e] = print at 16:17:00 ET | ES,NQ,RTY,YM; LONG only (p>=0.58) | 1 label day; time exit at next label day's 16:17:00 print (px[e+1]) | SAME_PRINT |
| R2_FULL-CAL | 0.0181 | 16:17:00 ET (close of bar opening 16:16) / px[e] = print at 16:17:00 ET | ES,NQ,RTY,YM; LONG only (p>=0.58) | 1 label day; time exit at next label day's 16:17:00 print (px[e+1]) | SAME_PRINT |
| R2_FULL | 0.0465 | 16:17:00 ET (close of bar opening 16:16) / px[e] = print at 16:17:00 ET | ES,NQ,RTY,YM; LONG only (p>=0.58) | 1 label day; time exit at next label day's 16:17:00 print (px[e+1]) | SAME_PRINT |
| R12_d2_1_0.08_longonly | 0.0531 | 16:17:00 ET (close of bar opening 16:16) / px[e] = print at 16:17:00 ET | ES,NQ,RTY,YM; LONG only | 1 label day; time exit px[e+1] | LOOKAHEAD_HARD |
| R12P_d2_1_0.08_longonly | 0.0531 | 16:17:00 ET (close of bar opening 16:16) / px[e] = print at 16:17:00 ET | ES,NQ,RTY,YM; LONG only | 1 label day; time exit px[e+1] | LOOKAHEAD_HARD |
| R3_ridge_0.08_1 | 0.0402 | 16:17:00 ET (close of bar opening 16:16) / px[e] = print at 16:17:00 ET | ES,NQ,RTY,YM; LONG only (p>=0.58) | 1 label day; time exit at next label day's 16:17:00 print (px[e+1]) | SAME_PRINT |
| R4_fixed_2_0.06 | 0.0316 | 16:17:00 ET (close of bar opening 16:16) / px[e] = print at 16:17:00 ET | ES,NQ,RTY,YM; LONG only (p>=0.58) | 2 label days; time exit at px[e+2] (the 17:00-print of the 2nd next label day); fixe | SAME_PRINT |
| RX5_ens | 0.0350 | 16:17:00 ET (close of bar opening 16:16) / px[e] = print at 16:17:00 ET | ES,NQ,RTY,YM; LONG only (p>=0.58) | 1 label day; time exit at next label day's 16:17:00 print (px[e+1]) | SAME_PRINT |
| RX6_ens | 0.0130 | 16:17:00 ET (close of bar opening 16:16) / px[e] = print at 16:17:00 ET | ES,NQ,RTY,YM; LONG only (p>=0.58) | 1 label day; time exit at next label day's 16:17:00 print (px[e+1]) | SAME_PRINT |
| RX7_0.04 | 0.0325 | 16:17:00 ET (close of bar opening 16:16) / px[e] = print at 16:17:00 ET | ES,NQ,RTY,YM; LONG if p>=0.58 AND SHORT if p<=0.46 (ap_rx_fams.py:51 mask  | 1 label day; time exit px[e+1] | SAME_PRINT |
| RX7P_asym | 0.0325 | 16:17:00 ET (close of bar opening 16:16) / px[e] = print at 16:17:00 ET | ES,NQ,RTY,YM; LONG if p>=0.58 AND SHORT if p<=0.46 (ap_rx_fams.py:51 mask  | 1 label day; time exit px[e+1] | SAME_PRINT |
| RX8_10_rsi65 | 0.0577 | 16:17:00 ET (RSI2 on the 16:17 px series, ap_rx_fams.py:130- / px[i] = print at 16:17:00 ET | ES,NQ,RTY,YM; LONG only (RSI2<10, px>SMA200, p>=0.5) | 1-7 label days; first of: px[j]<=px[i]-3*ADR[i] (checked on each day's 16:17 px), RSI2 | LOOKAHEAD_HARD |
| R9_2.0_4 | 0.0602 | 16:00:00 ET (daily-bar close) / B.C[i] = close of the 16:00 daily bar (ap_r_fams.p | ES,NQ,RTY,YM; LONG only | 2 label days (R9: up to 4; exit at 16:00 close 2 days later, or stop (3 ATR intraday for R10/RX*, | LOOKAHEAD_SAME_BAR |
| R10_0.1_0.0 | 0.0635 | 16:00:00 ET (daily-bar close) / B.C[i] = close of the 16:00 daily bar (ap_r_fams.p | ES,NQ,RTY,YM; LONG only | 2 label days (R9: up to 4; exit at 16:00 close 2 days later, or stop (3 ATR intraday for R10/RX*, | LOOKAHEAD_HARD |
| RX1_k4lo_half | 0.0618 | 16:00:00 ET (daily-bar close) / B.C[i] = close of the 16:00 daily bar (ap_r_fams.p | ES,NQ,RTY,YM; LONG only | 2 label days (R9: up to 4; exit at 16:00 close 2 days later, or stop (3 ATR intraday for R10/RX*, | LOOKAHEAD_SAME_BAR |
| RX2_2_2_0.5 | 0.0615 | 16:00:00 ET (daily-bar close) / B.C[i] = close of the 16:00 daily bar (ap_r_fams.p | ES,NQ,RTY,YM; LONG only | 2 label days (R9: up to 4; exit at 16:00 close 2 days later, or stop (3 ATR intraday for R10/RX*, | LOOKAHEAD_SAME_BAR |
| RX3_r5b_3 | 0.0628 | 16:00:00 ET (daily-bar close) / B.C[i] = close of the 16:00 daily bar (ap_r_fams.p | ES,NQ,RTY,YM; LONG only | 2 label days (R9: up to 4; exit at 16:00 close 2 days later, or stop (3 ATR intraday for R10/RX*, | LOOKAHEAD_SAME_BAR |
| RX11_F_shorten | 0.0601 | 16:00:00 ET (daily-bar close) / B.C[i] = close of the 16:00 daily bar (ap_r_fams.p | ES,NQ,RTY,YM; LONG only | 2 label days (R9: up to 4; exit at 16:00 close 2 days later, or stop (3 ATR intraday for R10/RX*, | LOOKAHEAD_SAME_BAR |
| R14_spec_follow_0.9 | 0.0087 | decision known at report publication (Fri 15:30 ET of the re / px[e] of the traded market at 16:17:00 ET | GC,CL,ZN,6E,6J; LONG and SHORT (follow spec: sign of (avg 52/104/156-wk perc | 5 label days; time exit px[e+5] (ap_j_fams.py:51 xx=e+5) | CLEAN |

## 2. Removed under item 2 (logged as RESEARCH ERRORS in autopilot/DECISIONS.md)
R12, R12P (same-day SKEW, end-of-day index, used at the 16:17 decision), R10 (filled at the 16:00 bar close but filtered by that day's 16:17 K4 probability), R9, RX1, RX2, RX3, RX11 (IBS from the 16:00 daily-bar close/high/low, filled at that same close; the user's own example), RX8 (a signal is kept only if a stop or RSI>65 exit occurs within 7 days: selection on the future). 9 cells, 53% of the pack's tilt weight. VIX9D/VIX6M are clean (DBIX prints to 16:15:01) but only R12/R12P used them. COT (Tuesday+7d, published Friday 15:30), ADR (shift 1), calendar flags, multi-day exits of R4/R14 (time exits) are clean.
Same-print pattern (decision on the 16:17:00 print, scored fill on that same print) in the 16 index cells: kept by the user's decision, tested below with the fill moved to the next print.

## 3. Rescore (METHOD-2 12/3/3 tilt OOS 2024-02..2026-10-16, 141 weeks; ES hedge beta refit on the family's own folds; drift-matched null (183 worlds) ; best-of-F = G^F, G from the pooled family null)
| family | hedged Sharpe | unhedged Sharpe | null rank h/u | gates a-d | best-of-F 1208 / 761 / 594 (hedged; unhedged) |
|---|---|---|---|---|---|
| pack 26 cells (library, as scored) | 1.80 | 2.24 | 1.00/1.00 | pass | 0.03 / 0.11 / 0.18 ; 0.79 / 0.86 / 0.89 |
| 17 cells as scored (fill at px[e]) | 1.14 | 1.42 | 0.995/1.00 | pass | 0.00 / 0.00 / 0.00 ; 0.00 / 0.00 / 0.00 |
| **17 cells, HEADLINE fill = first print >= 16:17:00.000 (+1 tick)** | **1.16** | **1.42** | 0.995 / 1.00 | pass (a-d) | **0.000 / 0.000 / 0.000 ; 0.000 / 0.0001 / 0.0007** |
| STRICT (clean cells only = R14) | 0.50 | 0.40 | 0.73 (signflip) | b,c,d FAIL | 0.00 |
Headline bands (sized to weekly SD $12,534, hedged / unhedged): net $285k / $348k; weekly mean $2,021 / $2,466; p5 -$6,981 / -$5,365; p95 +$16,596 / +$14,821; worst week -$46,982 / -$49,700; max DD $74.4k / $72.4k; CVaR5 -$18.1k / -$17.6k; halves Sharpe 1.55 & 0.78 (hedged), 1.54 & 2.37 (unhedged); bootstrap lower bound 0.046 / 0.176; corr to pair -0.05 / -0.04 (worst-decile 0.39 / 0.12); corr to ES weekly +0.36 unhedged, -0.03 hedged. Hedge 0.903 ES, gross 2.85 NQ-equivalents.
**Does K4 still pass?** Gates a-d: yes (single-family). Best-of-F at F_eff 1,208 / 761 / 594: NO (about 0; the family null G = 0.97 hedged / 0.99 unhedged is too low for hundreds of effective trials; the pack's own 26-cell result was already borderline: 0.03 hedged, 0.79 unhedged at 1,208). Hedged H2 Sharpe 0.78. PROVISIONAL at best; not FOUND-grade.

## 4. Fill-delay test (user condition: Sharpe at +5 s and +30 s >= 85% of the headline; headline = fill at the first print at/after 16:17:00.000 following the decision print, +1 tick/side)
Method: every distinct cell re-simulated with fills and daily marks at the delayed prices (entry, exit, marks; hedge legs too); delta prices from NQ/ES/RTY tick prints (back-adjusted series + tick differences), YM = ES % proxy, R14 markets = 1-minute bar opens interpolated. Calibration of my re-runs to the library series: r2 >= 0.998 per cell; delayed series = library + (delayed re-run - baseline re-run).
| fill | hedged Sharpe | x headline | unhedged Sharpe | x headline |
|---|---|---|---|---|
| as scored (px[e]) | 1.135 | 0.98 | 1.420 | 1.00 |
| next print (headline) | 1.163 | 1.000 | 1.419 | 1.000 |
| +1 s | 1.158 | 0.996 | 1.415 | 0.997 |
| +5 s | 1.173 | 1.009 | 1.428 | 1.006 |
| +30 s | 1.168 | 1.005 | 1.429 | 1.007 |
| +60 s | 1.177 | 1.012 | 1.433 | 1.010 |
Hedged and unhedged agree: the 85% test is passed with margin (thresholds 0.99 / 1.21); no print artifact. (Sharpe does not fall with delay: the decision print carries no exploitable edge of its own; mean signed move after the print is ~0.)

## 5. Lag-study reconciliation (done before this report)
The pack's lag study (ap_k4_lag.py) used as reference the LAST PRINT BEFORE 16:16:00 (close1616) and measured to the first print >= 16:17:00.5, a one-minute gap. The engine price is the last print before 16:17:00. Medians |move| (points): pack study NQ 2.25 / ES 0.50 / RTY 0.30; engine price -> first print >= 16:17:00.0: NQ 0.25 / ES 0.00 / RTY 0.10; -> >= 16:17:02: NQ 0.50 / ES 0.25 / RTY 0.10. The study's numbers are the one-minute gap between 16:16:00 and the engine price, not the engine-to-fill lag; both are small against the weekly mean, and the conclusion 'immaterial' stands for the engine-to-fill gap (and is confirmed by section 4).

## 6. VPS package (outputs/k4/k4_vps.zip, 25 files) - K4-EXACT 17 cells, clock 16:17 ET
SIGNAL_FILE_V4.md: per row entry_time_et, instrument, side LONG|SHORT|FLAT, hold_days, exit_rule; file K4_YYYYMMDD_1617.csv; RX7/RX7P SHORT legs (p<=0.46), R14 on GC/CL/ZN/6E/6J (LONG/SHORT, hold 5), R4 hold 2; ES hedge row (0.903 ES). Needs NT8 rows (row=1617 and row=close) for 9 instruments, DBIX vol (DBIX.CORE trades VIX/VIX3M/VVIX), CFTC fut_fin + com_disagg. All 17 cells are computable as scored from those inputs (R14 needs only prices/ADR of its 5 markets and CFTC).
Identity over the DBIX window 2026-10-05..10-16 (10 days): VPS vs box reference with the same frozen models: 10/10 days identical (0 differences in side/qty/p over 640 cell-instrument decisions); R14 chain logic equals the research R14 trades from 2026-03 (11/11; 17/18 from 2026-01); R14 had no entry in the window. VPS vs the research engine's orders (quarterly walk-forward models): 97.0% of cell decisions agree; entry rows research 24, VPS 29, common 17 (frozen vs quarterly model).
Box writer: it implements the retired 26-cell logic and the box has no GLBX live license (Databento Live: 'A live data license is required to access GLBX.MDP3'), so it can never source the NT8-type rows; it writes NO signal file ever (logged). DBIX.CORE live is licensed (verified).

## 7. Status changes for PAPER-ALL / league
- K4 26-cell rows (SK_K4BOOKS, hedged and unhedged): SUPERSEDED / VOID (contains 9 lookahead cells).
- K4-EXACT (17 cells): PROVISIONAL; gates a-d pass; best-of-F FAIL at F_eff 1,208/761/594; hedged H2 0.78. Strict R14-only: FAIL.
- The same-print convention is the user's accepted decision; the fill-delay condition passes.
## 8. Unvalidated / caveats
Real NT8 export (nine instruments, bar conventions), Windows/Task Scheduler, live 16:17 DBIX run, December roll, early closes; fill-delay data for YM/R14 are proxies; cell calibration residuals (R2_PRICE r2 0.9985 etc.); bands use research-engine series with my re-simulated fills; weights/hedge from fit window 2025-08-01..2026-07-31 (sized so hedged weekly SD is $12,534; this differs ~5% from the pack's sizing convention).
