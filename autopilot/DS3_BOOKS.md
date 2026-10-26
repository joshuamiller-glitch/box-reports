# DS3_BOOKS - EDITION 2 (D3L, 2026-10-26; edition 1 kept as DS3_BOOKS_ED1.md). Research only; no spec is a live recommendation.
Companion to autopilot/DS3_PORTFOLIO.md (T-G2 scoring, verdict line) and the exact rules + identity tests in autopilot/DS3_SPEC_<book>.md (D3X). Every book below: NQ, NT8 1-minute chart data only (no L2 at runtime), 10 nominal lots, stop 60 pt, R = 10 x 60 x $20 = $12,000; per-book locks (identical in book-R): day -2R / +5R = -$24,000 / +$60,000, give-back arm +2R = +$24,000 keep 50%, cap off, week floor 12R = -$144,000; at the 14/14 scale (R = $16,800): -$33,600 / +$84,000 / arm $33,600 / floor -$201,600. Execution mode: separate NT8 strategy per book (own lock group), same account as DS2. Costs: live (stop-join 1.01 pt, market 0.995 pt, $4.84 RT) in the DS2/T-B series; the T-ENTRY series use the direct-L2 execution layer (S10x1 market slices 2 s apart, stop-join XJ3: a 3 s passive limit then market, second-level timers, unvalidated live; with default Market/Native stop execution the realised cost is higher).

## The DS3 set (T-G2, selected on WF-PRE): 2 PASS + 1 carried book
| book | status | instrument / bars | signal rule | stop / target / exit | session (ET) | nominal lots | exec |
|---|---|---|---|---|---|---|---|
| TE7_kelt3m_n14_m1.0 | **PASS** (bar: all met; grid fragile, see PORTFOLIO) | NQ, 3-min bars + 1-min data series | Keltner break: mid = EMA(Close,14), ATR(10) (first value H-L, Wilder recursion), upper/lower = mid +/- 1.0 ATR; buy on the first bar whose Close is above upper, sell on the first below lower (edge-triggered per side), read on the closed bar | stop 60 pt, target 60 pt (1.0R) OCO from entry, flat 16:55 | entries 18:00-14:59; signal bars ending 15:00-17:59 ignored; lock engine blocks 18:00-18:05 and 15:00-16:54 | 10 | market entry (10 x 1-lot slices, 2 s apart), stop-market + limit target OCO, stop-join timer; OnBarClose |
| TE6_st10m_n7_m3.0 | **PASS** (family-redundant with the live WT10 book: rule distinct, 40% same-bar-and-side entries, weekly corr 0.52-0.54) | NQ, 10-min bars + 1-min series | Supertrend as tested (NOT the textbook flip): ATR(7) first value H-L, Wilder recursion; hl2 +/- 3.0 ATR; final bands ratchet on the previous Close; direction flips when Close crosses the CURRENT bar's band; signal = flip bar; no EMA filter | stop 60, target 60, flat 16:55 | as above | 10 | as above |
| TB7_ORBNY_k3_P60_N | DEAD on the book bar (marginal Sharpe negative in WF and holdout; 2023-04..24-01 -$137/wk); scored because the prereg selected it | NQ, 3-min | NY opening range break (L, buffer re-fit monthly from 15/30/60 min x 0/5/10 pt, trailing 6 months), see DS3_SPEC_TB7_ORBNY_k3_P60_N.md | stop 60 pt from entry-bar open, flat 16:57 | entries before 15:00 | 10 | exact 1-s locks (D3B) |
The monthly parameter file for TB7 (45 months) is required to reproduce its series; the two T-ENTRY books have fixed parameters. CANDIDATE: TE7_emax5m_f30_s50 (EMA 30/50 cross of Close on 5-min bars; same bracket; fails only the WF-PRE marginal-Sharpe test). Same-cluster, not counted separately: TE6_st10m_n10_m3.0 (== TE1_st_10m), TE6_st10m_n14_m3.0.

## Sizing in DualStrat2 terms (average NQ lots in the WF window from monthly risk-parity weights; per-book -2R/+5R scale with lots)
| line | kelt3m | st10m_n7 | TB7 | total | per-book day -2R / +5R at those lots (R = lots x 60 x $20) |
|---|---|---|---|---|---|
| equal weekly SD with DS2 | 10.5 | 16.4 | 12.9 | 39.8 (breaches the 50-cap bound, peaks sum 72) | kelt -25.2k/+63k; st10m -39.4k/+98.4k; TB7 -31k/+77.4k |
| same 27-contract budget | 7.1 | 11.1 | 8.7 | 27.0 (peaks sum 49) | kelt -17.0k/+42.6k; st10m -26.6k/+66.6k; TB7 -20.9k/+52.2k |
| half of the equal-SD scale | 5.2 | 8.2 | 6.4 | 19.9 | scale linearly |
| inside DS2 + DS3 (DS3 peak 23) | 3.4 | 5.2 | 4.1 | 12.7 | scale linearly |
Weights are re-estimated monthly (inverse trailing 26-week SD), so the lots above are averages; the live implementation would need the monthly lots file. Lots are not integers on average: the exact lots must be rounded and the locks re-run (not done).

## Standalone backtest expectation (WF 142 weeks 2024-02..2026-10, per-book locks, 10 nominal lots, live/direct cost)
| book | mean $/wk | SD | trades/wk | win rate | avg win / avg loss $ | maxDD | worst wk | HOLD $/wk | 2023-04..24-01 $/wk | WF at 2x (D3E / D3B) |
|---|---|---|---|---|---|---|---|---|---|---|
| TE7_kelt3m_n14_m1.0 | 16,838 | 59,572 | 26.8 | 52% | 11,302 / -10,858 | 336,626 | -124,049 | 12,773 | +6,365 | 12,395 |
| TE6_st10m_n7_m3.0 | 9,130 | 35,530 | 12.2 | 53% | 11,184 / -11,309 | 197,422 | -98,857 | 9,423 | +3,468 | 6,716 |
| TE7_emax5m_f30_s50 | 7,142 | 34,206 | 11.8 | 53% | 11,245 / -11,276 | 177,083 | -74,291 | 10,120 | +1,349 | 4,257 |
| TB7_ORBNY_k3_P60_N | 6,074 | 47,887 | 6.0 | 32% | 27,629 / -11,660 | 392,931 | -80,089 | 4,812 | -137 | 3,873 |
Win/loss columns are pre-lock closed trades (T-ENTRY from the direct L2 replay; TB7 from the T-B trade table). Reference books: ST10 WF 14,350 / SD 57,331 / 26 tr/wk / HOLD 16,463; HM10 10,052 / 53,295 / 24 / 10,598; WT7 1,438 / 27,750 / 38 / 786.

## Weekly correlations (WF, per-book-lock series)
| | kelt3m | st10m_n7 | TB7 | emax5m | ST10 | HM10 | WT7 | DS2 (sum) |
|---|---|---|---|---|---|---|---|---|
| TE7_kelt3m_n14_m1.0 | 1.00 | -0.12 | 0.06 | 0.05 | 0.33 | 0.33 | 0.21 | 0.40 |
| TE6_st10m_n7_m3.0 | -0.12 | 1.00 | 0.07 | 0.31 | 0.09 | -0.03 | 0.18 | 0.08 |
| TB7_ORBNY_k3_P60_N | 0.06 | 0.07 | 1.00 | 0.13 | 0.13 | 0.25 | 0.10 | 0.22 |
Among the three-book set every pair is <= 0.07 (cap 0.5). Corr of the 3-book DS3 portfolio to DS2: 0.38. st10m cluster: n10-n7 0.81, n14-n7 0.66; n7 vs library WT10 0.54.

## Not in the set
ST10 (add-one marginal Sharpe -0.07 at WF-PRE; per-book timing placebo 0.68; in edition 1 it was a CANDIDATE, not in ed.2's pre-stage selection), HM10, WT7 (negative marginal), TB1_ST_k15, TB9_RENKO_c2 (negative marginal, negative 2023-04..24-01), TB9_RENKO_c5 (DEAD, exact-lock WF -$244/wk), st10m n10/n14 (cluster), TF1_FOMC_NY (a CANDIDATE entry filter, below its MDE), all other tracks DEAD. **ST and HM are not in the DS3 set.**

## Caveats for any implementation
Rules are written from the box's replay (identity mismatch 0.83% kelt, 1.05% st10m_n7, 1.38% emax; limit 2%). The T-ENTRY books' dollars depend on the S10x1 + XJ3 execution layer (not validated in live NT8); a plain Market/Native implementation costs more. The T-ENTRY PASS verdicts come from a 191-cell search; the DS3 Sharpe numbers are selection-inflated (DS3_PORTFOLIO.md).

Note (D3X check): D3E's table uses 143 WF weeks and shows TE7_kelt3m_n14_m1.0 WF $16,863, TE6_st10m_n7_m3.0 $8,749 (emax5m $7,142); this file uses the 142-week WF window of Set A/DS2 ($16,838 / $9,130 / $7,142). Same series, one week difference in the window. 2-week Sim-leader specs for the three top books: autopilot/DS3_SIM_TE7_kelt3m_n14_m1.0.md, DS3_SIM_TE6_st10m_n7_m3.0.md, DS3_SIM_TE7_emax5m_f30_s50.md (the mean cannot be confirmed in 2 weeks; pass/fail rests on trade count, entry match >= 95%, bracket presence, slippage vs model, lock events).
