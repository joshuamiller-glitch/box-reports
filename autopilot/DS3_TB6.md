# DS3 TB6: time-of-day structural entries into the DS2 bracket (D3Q, addendum-2 B6)

Generated 2026-10-26T17:34:14Z. Research only; no execution-server/chart/live change. Prereg l2vast/ds3/prereg/T-Q_B6_prereg.md sha256 b7d997a83341201b8182a45be6dcc845a0eb29c48fd806c0a40621cfb0dd53d9 (25 cells). Rows l2vast/ds3/rows/DS3_TB6.json. Ledger +25. Holdout (2025-07+) and second holdout (2023-04..2024-01) looked once, track DS3_TQ_B6 (pre-holdout text autopilot/DS3_TQ_B6_PREHOLD.md).

## 1. Verdict
25 cells: {'DEAD': 25}. **No fixed-clock entry survives**: open-drive continuation at 18:00/02:00/09:30, the 10:00 ET reversal/knee-jerk, 15:30 MOC continuation and the 16:00 cash-close fade are all DEAD. The only PRE-pass cell (TB6_t1000_follow_L31, PRE +6.4k/wk) is negative on the holdout (-1.8k) and the second span (-5.3k). The 09:30 open-drive N=10/15 cells have positive sign in all three windows (WF +3.2k/+2.0k/wk, HOLD +2.9k/+0.7k, 2023 +2.5k/+1.7k) but the WF CI includes 0 (lower bound -0.3k/-1.8k), placebo rank 0.9 and WF MDE ~$3-4k/wk: a lead-sized hint that matches TE4_orb_ny_15 (also positive on PRE, negative on holdout), not a result. Fade controls are no better (18:00/02:00/09:30 fades: PRE -2.5k/-1.1k/-4.4k). The 15:30 and 16:00 cells are OUT-OF-DS2-WINDOW (DS2 blocks entries 15:00-16:54; the blocks were lifted for those cells only; flat 16:55 kept): all DEAD, all negative at 2x cost.
Not a DS3 book: no cell is PASS or CANDIDATE, so there is no SERIES file and no PAPER-ALL registration. Trades/wk 3.7-4.9 (the knee cells 3.7) so the rule-of-3 would have been met; the failure is the edge, not the count.

## 2. Method
T-ENTRY convention (autopilot/DS3_TENTRY.md): entry on the open of the 1-min bar after the clock bar (10:00 cells enter at 10:01 so the print reaction is observed), DS2 bracket 60-pt stop / 1.0R / flat 16:55, 10 lots with P9 mapped execution, per-book locks (day -2R/+5R, give-back 2R keep 50%, week floor 12R), $4.84 RT, one trade at a time. MAPPED basis (path-bracket sim + corrected-P9 year x exit map); no cell reached the DIRECT L2 stage except TB6_drive_570_N10 (top-20 by mapped holdout Sharpe; see DS3_TB7.md section on direct pricing, which covers all D3Q finalists). Verdict conditions: tpw>=3, PRE>0, WF CI>0, HOLD>0, SPAN2>0, timing-destroyed placebo rank>=0.95 on PRE, 2x-cost WF>0; PASS all, CANDIDATE all but one. Truncation-invariance audit (tb2_trunc.py: B3,B6,B7A,B7W events with data cut at 62%): 75 cells, 0 mismatches (as-of discipline: clock cells read only bars <= the signal bar).
Power: per-trade MDE ~3-4 pts (n ~1,000 WF trades per cell), weekly MDE $3-4k/wk on 143 WF weeks; predicted effect (+0.3 pt/trade, ~+$1.5k/wk) is BELOW MDE, so every null here is a null at the stated MDE, not a proof of absence of a +$1-3k/wk effect.
DSR with n_trials = cumulative ledger (~35k) is ~0 for every cell; best-of-25 is reported as best-of-25.

## 3. All cells (mapped; $k/wk at 10 lots; paired = candidate trade vs nearest same-side ST10 trade within 15 min)
| cell | flag | verdict (mapped) | failed | tr/wk | win | WF-PRE $k/wk | HOLD | 2023-04..24-01 | WF | WF CI | MDE wk | corr ST | placebo | 2x WF | dWK vs ST $k [CI] | paired vs ST pts/trade [CI] (MDE, n) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| TB6_drive_1080_N10 | NT8-bars | DEAD | WF_CI>0,HOLD>0,SPAN2>0,plc>=.95 | 4.9 | 0.51 | 1.6 | -0.3 | -3.1 | 0.7 | [-3.6,5.1] | 6.2 | -0.09 | 0.80 | 0.2 | -13.8 [-24.4,-3.2] | 4.4 [-2.4,10.9] (MDE 9.5, n=123) |
| TB6_drive_1080_N15 | NT8-bars | DEAD | PRE>0,WF_CI>0,SPAN2>0,plc>=.95 | 4.9 | 0.51 | -0.0 | 2.3 | -3.8 | 1.1 | [-2.9,5.6] | 6.1 | -0.05 |  | 0.5 | -13.4 [-24.0,-2.8] | -0.7 [-6.8,5.4] (MDE 8.8, n=143) |
| TB6_drive_120_N5 | NT8-bars | DEAD | PRE>0,WF_CI>0,HOLD>0,plc>=.95,x2_WF>0 | 4.9 | 0.49 | -2.0 | -1.4 | 1.5 | -1.8 | [-6.2,2.3] | 6.1 | 0.01 |  | -2.1 | -16.3 [-26.6,-6.5] | -12.8 [-23.8,-3.1] (MDE 15.2, n=35) |
| TB6_drive_120_N10 | NT8-bars | DEAD | WF_CI>0,HOLD>0,plc>=.95,x2_WF>0 | 4.9 | 0.49 | 0.2 | -4.5 | 2.2 | -2.1 | [-6.1,2.0] | 5.9 | -0.05 | 0.53 | -2.4 | -16.6 [-27.4,-6.5] | -2.4 [-9.0,3.1] (MDE 8.8, n=48) |
| TB6_drive_120_N15 | NT8-bars | DEAD | PRE>0,WF_CI>0,HOLD>0,plc>=.95,x2_WF>0 | 4.9 | 0.47 | -0.5 | -6.5 | 1.9 | -3.4 | [-7.0,0.6] | 5.6 | 0.06 |  | -3.6 | -17.9 [-28.1,-8.1] | -7.6 [-16.4,0.1] (MDE 12.3, n=52) |
| TB6_drive_570_N5 | NT8-bars | DEAD | WF_CI>0,HOLD>0,SPAN2>0,plc>=.95 | 4.9 | 0.51 | 3.4 | -2.3 | -2.3 | 0.7 | [-3.6,4.9] | 6.1 | 0.06 | 0.85 | 0.3 | -13.8 [-23.9,-4.2] | -2.4 [-10.3,6.0] (MDE 11.4, n=169) |
| TB6_drive_570_N10 | NT8-bars | DEAD | WF_CI>0,plc>=.95 | 4.9 | 0.54 | 3.4 | 2.9 | 2.5 | 3.2 | [-0.3,6.9] | 5.2 | 0.15 | 0.93 | 2.6 | -11.3 [-20.9,-2.7] | 1.2 [-5.3,8.1] (MDE 10.0, n=190) |
| TB6_drive_570_N15 | NT8-bars | DEAD | WF_CI>0,plc>=.95 | 4.9 | 0.52 | 3.1 | 0.7 | 1.7 | 2.0 | [-1.8,5.8] | 5.3 | 0.20 | 0.90 | 1.4 | -12.6 [-21.9,-3.4] | 2.2 [-5.4,9.7] (MDE 10.8, n=210) |
| TB6_driveF_1080_N10 | NT8-bars | DEAD | PRE>0,WF_CI>0,HOLD>0,plc>=.95,x2_WF>0 | 4.9 | 0.49 | -2.5 | -0.4 | 1.0 | -1.5 | [-5.8,2.8] | 6.2 | 0.09 |  | -1.8 | -16.0 [-25.8,-6.3] | 8.5 [1.3,17.0] (MDE 11.6, n=71) |
| TB6_driveF_120_N10 | NT8-bars | DEAD | PRE>0,WF_CI>0,SPAN2>0,plc>=.95 | 4.9 | 0.51 | -1.1 | 3.9 | -4.2 | 1.3 | [-2.8,5.3] | 5.9 | 0.05 |  | 0.8 | -13.2 [-23.1,-3.2] | n=25 |
| TB6_driveF_570_N10 | NT8-bars | DEAD | PRE>0,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95,x2_WF>0 | 4.9 | 0.46 | -4.4 | -3.6 | -4.6 | -4.0 | [-7.8,-0.5] | 5.2 | -0.15 |  | -4.3 | -18.5 [-29.1,-7.6] | 28.1 [15.3,41.2] (MDE 18.9, n=70) |
| TB6_t1000_fade_L31 | NT8-bars | DEAD | PRE>0,WF_CI>0,plc>=.95,x2_WF>0 | 4.9 | 0.47 | -7.4 | 1.0 | 3.2 | -3.4 | [-6.6,0.3] | 5.1 | -0.21 |  | -3.8 | -17.9 [-28.5,-7.7] | 22.1 [8.7,37.5] (MDE 20.7, n=36) |
| TB6_t1000_follow_L31 | NT8-bars | DEAD | WF_CI>0,HOLD>0,SPAN2>0 | 4.9 | 0.52 | 6.4 | -1.8 | -5.3 | 2.5 | [-1.1,5.7] | 5.1 | 0.21 | 0.97 | 2.0 | -12.0 [-21.1,-2.9] | 2.1 [-5.6,9.5] (MDE 10.6, n=184) |
| TB6_t1000_fade_L16 | NT8-bars | DEAD | PRE>0,WF_CI>0,SPAN2>0,plc>=.95,x2_WF>0 | 4.9 | 0.49 | -6.2 | 4.4 | -1.0 | -1.2 | [-5.5,3.2] | 6.1 | -0.15 |  | -1.7 | -15.7 [-27.0,-5.1] | 21.4 [8.8,34.4] (MDE 17.8, n=67) |
| TB6_t1000_follow_L16 | NT8-bars | DEAD | WF_CI>0,HOLD>0,SPAN2>0,x2_WF>0 | 4.9 | 0.50 | 5.2 | -5.1 | -1.0 | 0.3 | [-4.0,4.6] | 6.1 | 0.15 | 0.97 | -0.1 | -14.2 [-24.5,-4.5] | -1.7 [-9.5,6.3] (MDE 11.4, n=152) |
| TB6_knee_fade | NT8-bars | DEAD | PRE>0,WF_CI>0,plc>=.95,x2_WF>0 | 3.7 | 0.50 | -1.7 | 1.4 | 2.9 | -0.2 | [-3.8,3.4] | 5.0 | 0.08 |  | -0.5 | -14.7 [-25.2,-5.0] | 17.8 [6.1,29.7] (MDE 17.2, n=82) |
| TB6_knee_follow | NT8-bars | DEAD | WF_CI>0,HOLD>0,SPAN2>0,plc>=.95,x2_WF>0 | 3.7 | 0.50 | 1.0 | -1.9 | -4.3 | -0.4 | [-4.0,3.2] | 5.0 | -0.07 | 0.62 | -0.7 | -14.9 [-24.7,-5.0] | -2.4 [-12.7,8.2] (MDE 15.3, n=93) |
| TB6_moc1530_follow_L30 | NT8-bars | DEAD | PRE>0,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95,x2_WF>0 | 4.7 | 0.49 | -4.7 | -0.0 | -3.7 | -2.5 | [-5.6,0.7] | 4.5 | 0.03 |  | -3.2 | -17.0 [-27.1,-7.4] | n=0 |
| TB6_moc1530_fade_L30 | NT8-bars | DEAD | WF_CI>0,HOLD>0,x2_WF>0 | 4.7 | 0.49 | 3.1 | -1.6 | 0.8 | 0.9 | [-2.3,4.0] | 4.6 | -0.02 | 0.95 | -0.0 | -13.6 [-23.3,-4.2] | n=0 |
| TB6_moc1530_follow_L15 | NT8-bars | DEAD | WF_CI>0,HOLD>0,SPAN2>0,plc>=.95,x2_WF>0 | 4.7 | 0.50 | 0.3 | -1.5 | -2.0 | -0.6 | [-3.8,2.6] | 4.7 | -0.06 | 0.50 | -1.3 | -15.1 [-25.0,-5.1] | n=0 |
| TB6_moc1530_fade_L15 | NT8-bars | DEAD | PRE>0,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95,x2_WF>0 | 4.7 | 0.48 | -1.9 | -0.1 | -1.0 | -1.1 | [-4.3,2.2] | 4.7 | 0.06 |  | -1.9 | -15.6 [-25.5,-6.2] | n=0 |
| TB6_close1600_fade_L30 | NT8-bars | DEAD | PRE>0,WF_CI>0,SPAN2>0,plc>=.95,x2_WF>0 | 4.7 | 0.50 | -2.3 | 1.0 | -0.4 | -0.7 | [-2.9,1.8] | 3.2 | -0.03 |  | -1.7 | -15.2 [-25.0,-5.5] | n=0 |
| TB6_close1600_follow_L30 | NT8-bars | DEAD | WF_CI>0,HOLD>0,SPAN2>0,x2_WF>0 | 4.7 | 0.45 | 0.1 | -3.0 | -2.7 | -1.4 | [-3.8,0.8] | 3.2 | 0.03 | 0.95 | -2.5 | -15.9 [-26.0,-6.6] | n=0 |
| TB6_close1600_fade_L60 | NT8-bars | DEAD | PRE>0,WF_CI>0,HOLD>0,plc>=.95,x2_WF>0 | 4.7 | 0.48 | -2.0 | -1.1 | 0.3 | -1.6 | [-3.9,0.9] | 3.5 | -0.10 |  | -2.6 | -16.1 [-26.3,-6.3] | n=0 |
| TB6_close1600_follow_L60 | NT8-bars | DEAD | PRE>0,WF_CI>0,HOLD>0,SPAN2>0,plc>=.95,x2_WF>0 | 4.7 | 0.47 | -0.2 | -0.8 | -3.4 | -0.5 | [-3.0,1.8] | 3.4 | 0.11 |  | -1.6 | -15.0 [-24.8,-5.4] | n=0 |

Paired columns: the clock entries overlap ST10 trades rarely (n pairs in the table); where CI includes 0 the paired test is under-powered (MDE next to every estimate). Regime columns (A1 predicted-quiet / predicted-wide) are produced by the regime track (D3R) on the T-ENTRY/T-B families, not here; no B6 cell is a candidate for a regime gate.

## 4. Deliverability and one-line verdict
All B6 cells are NT8-bars (fixed clock on 1-min bars, no indicator): deliverable if there were an edge. Nearest scored cells: TE4_orb_{asia,london,ny}_15 (DEAD), FAILPRED calendar profile (7 of 714 flagged vs ~18 by chance), TF1/TF2 (CANDIDATE/DEAD filters).
**Verdict: B6 = 0 PASS, 0 CANDIDATE, 25 DEAD (best-of-25 hint: 09:30 open-drive N=10, sign-consistent but below MDE).**
