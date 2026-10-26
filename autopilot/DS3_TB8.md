# DS3 TB8: scheduled-release event entries into the DS2 bracket (D3Q, addendum-2 B8)

Generated 2026-10-26T17:34:14Z. Research only. Prereg l2vast/ds3/prereg/T-Q_B8_prereg.md sha256 9cc49cd5cd26e686d440900013b33de2edac71a98ea9ea9ae47afb6cbb0fce2a (20 cells). Rows l2vast/ds3/rows/DS3_TB8.json. Ledger +20. Holdout and second holdout looked once, track DS3_TQ_B8 (autopilot/DS3_TQ_B8_PREHOLD.md).

## 1. Verdict
20 cells: {'DEAD': 20}. **Every event entry is DEAD and none is forward-measurable.** Event counts in the 3.7-year sample: CPI 44, NFP 42, FOMC 29 (CORE tier, VERIFIED calendar), Thursday claims 193 and 10:00 ISM 88 (RULE-based WIDE tier, unverified dates). Trades/wk (WF): CPI/NFP/FOMC 0.2-0.25, ISM 0.43, claims 0.6-1.0 - all < 3, which by the DS3 rule means NOT MEASURABLE FORWARD: none can be a DS3 book at any N, regardless of edge (the trades/wk condition fails by construction, so the best possible verdict is CANDIDATE and no cell reached it).
No sign pattern either: the 10-/20-/30-pt breakout WF per-trade means are CPI -0.8k/+0.6k/+2.0k, NFP +0.3k/+1.0k/+0.3k, FOMC -0.5k/-2.8k/-1.1k, claims -0.2k/+0.2k/-0.7k, ISM +1.3k/+0.7k/+0.5k $ per trade at 10 lots, every one with a CI spanning 0 and a per-trade MDE of $2.7-7.3k (14-36 pts). The pre-stated continuation direction is positive on 9 of 15 cells in WF but negative or ~0 on the second span for CPI/NFP/ISM (-0.2k to -6.2k), and the same-clock non-event-day controls are comparable (-0.8k..+0.7k). The FOMC fade control (+2.6k/trade, n=21, placebo 0.89) is a sign-flip of the FOMC continuation cell (-2.8k) - with n=21 and MDE $6.9k it is noise, not a reversal result.
Power statement: with n = 20-140 WF trades the paired and standalone MDEs are 14-36 pts per trade (the DS2 bracket moves +/-60); a real +5-10 pt event effect is far below MDE, so these are nulls at that MDE only.

## 2. Method
Calendar: free calendar l2vast/standS/event_calendar_core.csv (VERIFIED CORE tier: CPI/NFP 08:30, FOMC 14:00 statement; PROVENANCE l2vast/data_free/PROVENANCE.md and standS/S7_S12_DESIGN.md; fetched 2026-09-18); CLAIMS (Thursday 08:30) and ISM (10:00, 1st/3rd business day) are RULE-based WIDE tier, unverified. Print instant = event_ts_utc; P0 = close of the last NQ 1-s record before the print (within 300 s); trigger = first 1-s record within 15 min after the print with |close - P0| >= N points (N in 10, 20, 30) entered at that close (as-of: the trigger is complete at the end of that second; second-level path sim tb2_sec.py, which reproduces the minute-level T-ENTRY simulator trade-for-trade when fed bar-open seconds); DS2 bracket 60/60 flat 16:55, 10 lots, per-book locks, $4.84 RT, MAPPED P9 cost (a normal-market cost: OPTIMISTIC for fills inside a release spike - slippage in the first seconds of CPI/NFP/FOMC is several points; a direct replay would be required for any CANDIDATE, none arose). CPI/NFP/FOMC scored separately. Statistics are event-level (trade bootstrap 3,000 draws) because weekly series have <1 trade/wk; placebo = rank of the event mean among 3,000 equal-size random draws from trades of the same rule at the same clock on non-event weekdays (control days: all weekdays 2023-02-10..2026-10-22 without a calendar event at that clock). Verdict conditions as T-ENTRY with the event-bootstrap CI replacing the weekly CI. Paired vs ST10: ST10 and the event trade overlap in 2-17 trades per cell (column ST-overlap), too few for a paired test; no effect size is claimed.
Nearest scored cells: TF1_FOMC_NY (CANDIDATE filter, paired CI includes 0, MDE 48 pts) and TF2_CPI_LON (DEAD) - both calendar filters on a proxy book, not entries; FAILPRED calendar profile 7 of 714 flagged vs ~18 by chance.

## 3. All cells (mapped, $k per trade at 10 lots unless stated; MDE = 2.8 x SE of the WF trade mean)
| cell | events (3.7 y) | trades WF | tr/wk WF | verdict | failed | WF mean $k/trade [event-bootstrap CI] | PRE | HOLD (n) | 2023-04..24-01 | same-clock non-event-day control WF mean | placebo rank | per-trade MDE $k (pts) | 2x-cost WF mean | ST-overlap trades |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| TB8_CPI_N10 | 44 | 32 | 0.23 | DEAD | tpw>=3,PRE>0,WF_CI>0,SPAN2>0,plc>=.95,x2_WF>0 | -0.8 [-4.5,3.4] | -2.1 | 0.7 (15) | -0.2 | -0.5 | 0.44 | 5.7 (29) | -0.8 | 12 |
| TB8_CPI_N20 | 44 | 32 | 0.23 | DEAD | tpw>=3,PRE>0,WF_CI>0,SPAN2>0,plc>=.95 | 0.6 [-3.1,4.8] | -0.8 | 2.2 (15) | -2.6 | -0.8 | 0.75 | 5.7 (29) | 0.4 | 15 |
| TB8_CPI_N30 | 44 | 32 | 0.23 | DEAD | tpw>=3,WF_CI>0,SPAN2>0,plc>=.95 | 2.0 [-1.6,5.6] | 1.9 | 2.2 (15) | -2.6 | 0.1 | 0.80 | 5.6 (28) | 1.8 | 15 |
| TB8_CPI_N20_fade | 44 | 32 | 0.23 | DEAD | tpw>=3,WF_CI>0,HOLD>0,plc>=.95,x2_WF>0 | -0.8 [-4.9,3.5] | 0.6 | -2.3 (15) | 2.2 | 0.7 | 0.24 | 5.7 (29) | -0.8 | 5 |
| TB8_NFP_N10 | 42 | 31 | 0.22 | DEAD | tpw>=3,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95 | 0.3 [-4.0,4.1] | 1.9 | -1.7 (14) | -2.4 | -0.5 | 0.67 | 5.8 (29) | 0.2 | 10 |
| TB8_NFP_N20 | 42 | 31 | 0.22 | DEAD | tpw>=3,PRE>0,WF_CI>0,SPAN2>0,plc>=.95 | 1.0 [-2.8,4.7] | -0.8 | 3.1 (14) | -2.4 | -0.8 | 0.80 | 5.8 (29) | 0.8 | 13 |
| TB8_NFP_N30 | 42 | 31 | 0.22 | DEAD | tpw>=3,PRE>0,WF_CI>0,SPAN2>0,plc>=.95 | 0.3 [-4.1,4.6] | -0.8 | 1.5 (14) | -6.2 | 0.1 | 0.50 | 5.8 (29) | 0.1 | 13 |
| TB8_NFP_N20_fade | 42 | 31 | 0.22 | DEAD | tpw>=3,WF_CI>0,HOLD>0,plc>=.95,x2_WF>0 | -1.1 [-4.9,3.2] | 0.6 | -3.3 (14) | 2.0 | 0.7 | 0.19 | 5.8 (29) | -1.1 | 2 |
| TB8_FOMC_N10 | 29 | 21 | 0.15 | DEAD | tpw>=3,PRE>0,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95,x2_WF>0 | -0.5 [-4.9,3.9] | -1.0 | -0.1 (10) | -1.9 | -0.8 | 0.55 | 7.1 (36) | -0.5 | 3 |
| TB8_FOMC_N20 | 29 | 21 | 0.15 | DEAD | tpw>=3,PRE>0,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95,x2_WF>0 | -2.8 [-7.1,1.7] | -3.2 | -2.3 (10) | -1.9 | -0.1 | 0.12 | 6.9 (35) | -2.7 | 3 |
| TB8_FOMC_N30 | 28 | 20 | 0.14 | DEAD | tpw>=3,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95,x2_WF>0 | -1.1 [-5.7,3.5] | 0.0 | -2.3 (10) | -1.9 | -0.0 | 0.33 | 7.3 (36) | -1.1 | 3 |
| TB8_FOMC_N20_fade | 29 | 21 | 0.15 | DEAD | tpw>=3,WF_CI>0,plc>=.95 | 2.6 [-2.7,7.0] | 3.0 | 2.2 (10) | 1.5 | -0.1 | 0.89 | 6.9 (35) | 2.4 | 3 |
| TB8_CLAIMS_N10 | 186 | 138 | 0.98 | DEAD | tpw>=3,PRE>0,WF_CI>0,plc>=.95,x2_WF>0 | -0.2 [-2.1,1.7] | -1.5 | 1.3 (65) | 0.7 | -0.5 | 0.62 | 2.7 (13) | -0.3 | 17 |
| TB8_CLAIMS_N20 | 159 | 117 | 0.83 | DEAD | tpw>=3,PRE>0,WF_CI>0,SPAN2>0,plc>=.95 | 0.2 [-1.9,2.2] | -1.3 | 2.0 (54) | -0.3 | -0.8 | 0.84 | 3.0 (15) | 0.1 | 16 |
| TB8_CLAIMS_N30 | 117 | 88 | 0.62 | DEAD | tpw>=3,PRE>0,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95,x2_WF>0 | -0.7 [-3.1,1.7] | -1.3 | -0.1 (42) | -2.2 | 0.1 | 0.22 | 3.4 (17) | -0.8 | 15 |
| TB8_CLAIMS_N20_fade | 159 | 117 | 0.83 | DEAD | tpw>=3,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95,x2_WF>0 | -0.4 [-2.5,1.7] | 1.2 | -2.1 (54) | -0.1 | 0.7 | 0.16 | 3.0 (15) | -0.4 | 5 |
| TB8_ISM_N10 | 83 | 62 | 0.44 | DEAD | tpw>=3,PRE>0,WF_CI>0,SPAN2>0,plc>=.95 | 1.3 [-1.5,4.1] | -0.5 | 3.2 (29) | -5.5 | 0.4 | 0.72 | 4.0 (20) | 1.1 | 11 |
| TB8_ISM_N20 | 81 | 61 | 0.43 | DEAD | tpw>=3,PRE>0,WF_CI>0,SPAN2>0,plc>=.95 | 0.7 [-2.2,3.4] | -1.5 | 3.1 (29) | -2.8 | 0.3 | 0.62 | 4.1 (20) | 0.5 | 10 |
| TB8_ISM_N30 | 76 | 60 | 0.42 | DEAD | tpw>=3,PRE>0,WF_CI>0,SPAN2>0,plc>=.95 | 0.5 [-2.4,3.3] | -0.8 | 2.0 (28) | -3.6 | -0.1 | 0.66 | 4.1 (21) | 0.4 | 7 |
| TB8_ISM_N20_fade | 81 | 61 | 0.43 | DEAD | tpw>=3,WF_CI>0,HOLD>0,plc>=.95,x2_WF>0 | -0.8 [-3.6,2.0] | 1.4 | -3.3 (29) | 2.4 | -0.4 | 0.39 | 4.1 (20) | -0.8 | 14 |

## 4. Deliverability and one-line verdict
NT8-deliverable in principle (hard-coded date list + 1-s/tick data or 1-min bars; the 1-s trigger would need tick data or a 1-min approximation) but not worth building: no edge and < 1 trade/wk.
**Verdict: B8 = 0 PASS, 0 CANDIDATE, 20 DEAD; not measurable forward (0.2-1.0 trades/wk); MDE 14-36 pts/trade.**
