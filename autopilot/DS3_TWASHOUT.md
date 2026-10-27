# DS3 T-WASHOUT (D3WO): washout as a paired ENTRY CONDITION on ST, HM, KB, SM, EM and every PASS/CANDIDATE entry in the bracket registry
Written 2026-10-27. Research only; no live/chart/execution change. Preregs: l2vast/ds3/prereg/WO_<entry>_<A|B>_prereg.md (64 files, <=24 cells each, sha256 logged in DECISIONS.md before any scored cell). Code l2vast/ds3/code/wo/. Rows l2vast/ds3/rows/DS3_TWASHOUT.json (1,488 cells). Pre-holdout text DS3_TWASHOUT_PREHOLD.md.

## 1. Verdict
1,488 cells (32 entries x CCI n{14,20,27,40} x k{10,18,30} x {entry bar, 5-min}; pullback >= {0.5,1.0,1.5} x ATR14; RSI14 30/70 cross; k{10,18,30}). **0 PASS, 4 CANDIDATE, 1,484 DEAD.** Ledger +1,488.
Best cell: **HM, CCI(20) k=10 on 1-min bars (WO_HM_cci_b1_n20_k10)**: take 40%, paired lift +2.05 pt per kept trade [+0.05,+3.89] (WF), holdout +1.36, WF-PRE +2.97, placebo 0.98, mirror -1.35 [-2.57,-0.03], win 54.0% vs 52.3% base vs 51.2% mirror; weekly $ at 10 lots 11,523 vs 9,785 base (fewer trades, MORE dollars: 40% fewer trades), maxDD 205k vs 252k, equal-risk (14.2 lots) +$1.8k/wk vs ST10 and +$5.5k/wk vs HM10 at equal weekly SD, DS3 marginal Sharpe +0.39 WF / +0.29 HOLD. V2 verdict would be PASS but it FAILS the DS3 extra "second span (2023-04..2024-01) lift > 0" (-1.87 pt), so CANDIDATE. 
The 4 CANDIDATE (series in l2vast/ds3/out/SERIES/DS3_TWASHOUT__*.parquet, paper_all struct48/paper_all/ds3_WO_*.json): HM cci b1 n20 k10 (above); PRO2_RIB1m_q30 cci b1 n20 k10 (lift +1.91 [-0.35,4.09], eq-risk -$1.4k vs ST10, marginal +0.22); TE6_st10m_n10_m3.5 cci b10 n27 k18 (+1.39 [-0.24,3.02], marginal -0.18, no real value); TE7_boll3m_n20_m1.5 pb b5 x1.5 k10 (+0.57 [0.02,1.08], take 84%, i.e. barely a filter, marginal +0.36).
No cell beats its entry's best-of-N placebo p95 on the WF window (beats_bestN_WF false for all 71 finalists); the stage-1 PRE screen had 8 cells above it, none survived the holdout/second span.

## 2. Mirror: do entries WITHOUT a prior washout fade?
Mostly NO. Over all 1,488 cells (PRE): mean lift of washout-kept CCI cells -0.28 pt, mirror (no washout) lift -0.04 pt (CCI), +0.06 (RSI); the pullback-ATR condition is true for 98.7% of trades (take-rate), so its mirror is a handful of odd trades (not interpretable). By book (CCI cells, PRE): 1-min HM/RIB1m: kept +0.42, mirror -0.36; pullback books: -0.80 / -0.06; trend entries: +0.04 / +0.02. Only HM (24 CCI cells: 7 with placebo >= .95, 5 with PRE CI > 0, all mirror lifts negative) and PRO2_RIB1m show a coherent "breakouts without a washout fade" pattern, and the 2023-04..2024-01 span reverses it (HM kept lift -1.87). ST, KB, SM, EM, and 3-/5-/10-min trend entries show nothing: the hypothesis "breakouts into extended strength fade" is NOT supported for the trend-entry family, and only weakly for the 1-min HM book (CANDIDATE, one span disagrees).

## 3. Tier-1 table (WF-PRE, all cells, mean per family): lift = kept minus all, pt/trade
| entry | family | cells | take | mean lift | best lift | mean mirror lift | placebo>=.95 | CI>0 |
|--|--|--|--|--|--|--|--|--|
| EM | cci | 12 | 0.48 | +0.94 | +2.67 | -0.44 | 0 | 0 |
| EM | pb | 9 | 0.98 | +0.11 | +0.87 | +11.74 | 0 | 0 |
| EM | rsi | 3 | 0.13 | -13.89 | -3.01 | +0.90 | 0 | 0 |
| HM | cci | 24 | 0.42 | +1.01 | +5.19 | -0.22 | 7 | 5 |
| HM | pb | 18 | 0.98 | +0.00 | +0.22 | +11.25 | 0 | 0 |
| HM | rsi | 6 | 0.07 | -4.59 | +4.25 | +0.09 | 0 | 0 |
| KB | cci | 24 | 0.49 | -0.49 | +0.97 | +0.80 | 0 | 0 |
| KB | pb | 18 | 0.98 | +0.06 | +0.60 | -4.05 | 0 | 0 |
| KB | rsi | 6 | 0.17 | +1.68 | +7.92 | -0.13 | 1 | 0 |
| SM | cci | 24 | 0.67 | +0.88 | +3.53 | -1.47 | 0 | 0 |
| SM | pb | 18 | 0.98 | +0.06 | +0.70 | -2.51 | 0 | 0 |
| SM | rsi | 6 | 0.25 | +0.61 | +3.55 | -0.25 | 0 | 0 |
| ST | cci | 24 | 0.48 | -0.75 | +1.73 | +0.23 | 0 | 0 |
| ST | pb | 18 | 0.99 | +0.01 | +0.16 | +18.10 | 0 | 0 |
| ST | rsi | 6 | 0.09 | -4.00 | +0.91 | +0.34 | 0 | 0 |
(The pullback-ATR family has take ~0.98: it removes almost nothing; RSI-cross takes 7-25% and is noisy: MDE 6-15 pt/trade.)
Full per-cell numbers (all 32 entries) are in the rows file; entries are KB, SM, EM, ST10, HM10 (tier 1) and 27 T-ENTRY / PRO2 / PB3 PASS-CANDIDATE books.

## 4. Power
Predicted lifts (+0.8..+1.0 pt/trade) are below the per-trade MDE for every take-rate (2.8 x SE, no clustering: ~1.0-1.7 pt for 3,000-trade entries at 30-50% take, 3-9 pt for 5-15% take, 8-30 pt for low-frequency books like PRO2_ER5 with 3 tr/wk). Every null here reads "could not see less than the MDE in the cell's rows", not "no effect". The test is a screen; verdicts rest on sign across windows, placebo, neighbours, the mirror.

## 5. Method
Mapped screen (te_core path sim; ST/HM true corrected P9), each entry's own bracket and own trades (pure subset; trades skipped by the base while busy are not recovered), 10 lots, per-book locks (firmlib.Ctx.run keep mask). Flags as-of the last completed 1-min bar before entry; k-min bars aggregated like te_sig.agg. Definitions fixed in the preregs: CCI = (tp-SMA)/(0.015 mean dev) on (H+L+C)/3, long needs Lowest < -100 over the last k bars incl. the signal bar, short Highest > +100; pullback = max drawdown (long) / run-up (short) inside the last k bars >= X x Wilder ATR14; RSI = Wilder RSI14 literal cross (down-cross of 30 for longs, up-cross of 70 for shorts inside the window). Paired lift = mean(kept)-mean(all) with session (label-day) block bootstrap (2000 draws), placebo = random trade removal at the same take (1,000 draws, rank of the observed lift) plus best-of-N (p95 of the max over the entry's grid), neighbours = adjacent n / k / X (PRE lifts, all must share the sign). Stage 1 used WF-PRE only; PRE screen = lift > 0 and placebo >= 0.90 (71 cells); then ONE logged holdout + second-span look on those (WF/HOLD/SPAN2 lifts, weekly $, maxDD, 2x cost, year share of the lift, equal-risk scaling to the base's WF weekly SD, V2 verdict via s48score.verdict). DS3 extras (stricter than V2): second-span lift > 0 and equal-risk dollars not below base; each extra failure demotes one tier. Truncation/poison audit: 120 family x bar x parameter combos over 809k minutes, 0 mismatches (out/WO/trunc_audit.json).
Direct basis (finalists with WF paired CI > 0: 6 cells), re-using the base entries' existing per-trade L2 replays (S10x1_g2 + XJ3; coverage 89% for PRO2_RIB1m, 98% for TE7 books, remainder at mapped points; HM = live true P9): RIB1m n20 k18 lift +1.88 [0.77,3.02] WF, +1.20 holdout (CI includes 0), weekly $15.3k vs 8.5k base; RIB1m n14 k18 +1.34 [0.40,2.31]; n27 k18 +1.75; TE7_boll pb: +0.47 [-0.10,1.00] (CI includes 0 on direct); TE7_kelt20_1.0 pb: +0.12 [0.01,0.25] (take 99%, nothing). Details out/WO/direct_follow.json. These RIB1m k18 cells were V2 CANDIDATE and then demoted to DEAD only by the second-span extra (span2 -0.42, -0.38, -1.98).

## 6. Deviations and disclosures
- A pre-prereg smoke test printed the WF-PRE lift of two cells (KB cci b3 n20 k18 -0.09, ST cci b1 n20 k18 +0.44); both stay in the grid; nothing selected on them.
- TB1/TB7/TB9 (T-B bracket-registry books) were NOT included: their registry signal ids are not te_core bar indices (gen_entries did not reproduce them). T-TREND (TR1-TR3) and the mapped-only TPULLBACK/PRO1/PRO3 PASS/CANDIDATE books are NOT in the registry with trade lists and were not covered (pending). TA1 gated books and GC sleeves are derived/other-instrument and skipped. 32 entries covered (no identical series among them, checked by signal hash).
- "Entry bar size" for PRO2 (1-min triggers) and PB3 (P-minute trigger) is my reading of their specs; ST/HM = 1-min.
- RSI "crossing" implemented literally (cross events), CCI/pullback windows include the signal bar. Year-share test uses the per-trade lift contribution by year (the weekly-dollar version is vacuous for a filter).
- Neighbours are PRE neighbours (non-finalists get no holdout read). Verdict placebo = WF-window random removal.
- ds3_addbook/equal_risk was called for the 4 CANDIDATE (4 holdout re-reads, logged in l2vast/ds3/ledger/addbook_looks.jsonl). One holdout look for the track logged (DS3_TWASHOUT). UNTOUCHED data not read.
- Dropping trades: lift per kept trade is real for HM-1m-CCI but the 2023 span disagrees; 59 of the 71 finalists lose weekly dollars at equal lots.
