# DS3_SESSION2_D_D6LINE - the D6 line on the MEASURED basis (D3SA, DIRECTIVE_D6_PRIORITY item 3), 2026-10-28
Research only; no live change; UNTOUCHED never read. Built from DS3_SESSION2_A_D6.md (prereg SSA_prereg.md sha256 73f0a1cab5b210ace5f503abf3b69e061ea24ccfc5468eca3736baa65cc8e762 + addendum e9742d74c6c5cefe974f6d421bbc0fe8414054e9e9984f5ebb1c43fd3017d3cd). Code l2vast/ds3/code/ssa/ssa_line.py, tables out/ssa/line.md. Selection of legs is on MEASURED PRE only (t of the PRE per-trade mean, mean > 0, one cell per cluster, at most 3 per session) among cell-sessions that pass the MEASURED tier gate (HOLD, H25, H26 > 0); HOLD is the one look.

## THE D6 CONFIGURATION LINE (D6 legs, MEASURED basis)
**ASIA = none passes the MEASURED gate (monitor only, 1 lot each: ba2/SM_t60_sst, PB7_PB5_depth_atr0.5_W15_s+0, TB4W_03_time_15s_ST3_E20_1_T2; each SESSION-CANDIDATE on STORED, +0.42 / +1.42 / +0.34 pts HOLD measured but each fails one HOLD half and sits inside its MDE) ; LONDON = none (IF/CRT negative on every measured basis) ; PRE = none ; NYAM = ba2/HM_t75_s90 at 1 lot (SESSION-CANDIDATE on MEASURED, BOF not cleared; half size; MEASURED break-even slippage PRE +10.1 / HOLD +5.45 pts/trade; 30-lot scale would be 30 lots = $54k risk per trade, not recommended) ; NYPM = none ; CLOSE = none.**
Everything else of the D6 list (IF_30s_eb ASIA/PRE, IF_15s_eb NY-AM, CRT_M15_M1_close(_ib), CRT_H1_30s_close, ba2/KB_t60_s75 ASIA, TB4B) is OUT on the measured basis; E1A_RENKOC5 has no measured series (stored +11.86, minimum monitor).
Handoff rule: run to bracket (as replayed), flat 16:55 ET; flat-at-session-end was NOT replayed. Exposure to that choice: 41% of ba2/HM_t75_s90 NY-AM trades exit after 12:00 ET (mean +5.1 pts vs +11.5 inside the window); ASIA monitors 41-56% exit after 02:00. If D6 flattens at the session end the measured numbers do not apply to those trades.

## Series on the MEASURED basis (equal risk by 1/PRE-SD, lots summing to 30 NQ lots, per-leg session-book lock R = median stop $ x lots, -2R/+5R)
## LINE_D6 (D6 legs only)

| session   | cell           |   lots_30lot_scale |   lots_1000_risk_class |   stop_pts_median |   pre_t_meas |   hold_wk |   pre_wk |    x_wk |   n_trades |
|:----------|:---------------|-------------------:|-----------------------:|------------------:|-------------:|----------:|---------:|--------:|-----------:|
| NY-AM     | ba2/HM_t75_s90 |                 30 |                      1 |                90 |         2.97 |   17367.3 |  33454.2 | 20488.5 |        780 |

|      |   weeks |    mean |       sd |   maxdd |   worst_week |       worst20_own |   corr |     mde |   stack_mean |   add_in_stack_worst20 |
|:-----|--------:|--------:|---------:|--------:|-------------:|------------------:|-------:|--------:|-------------:|-----------------------:|
| PRE  |      75 | 33454.2 | 102323   |  300892 |      -205570 |      -1.85065e+06 |    0.3 | 33082.7 |      44127.1 |                    nan |
| HOLD |      32 | 17367.3 | 115132   |  467322 |      -195426 |      -1.07973e+06 |    0   | 56987.3 |      52447.7 |                    nan |
| X    |      44 | 20488.6 |  75044.2 |  279915 |      -173844 | -842918           |   -0.1 | 31677.4 |      20616.2 |                    nan |
| FULL |     149 | 26619.5 |  98413.9 |  487105 |      -205570 |      -2.69533e+06 |    0.2 | 22574.7 |      39563.6 |                 308627 |

Per-session $/wk of the book at the 30-lot scale:

|       |   PRE_$wk |   HOLD_$wk |   X_$wk |   FULL_$wk |
|:------|----------:|-----------:|--------:|-----------:|
| NY-AM |     33454 |      17367 |   20489 |      26620 |

Stack-add (line scaled to 10/20/30% of the stack PRE weekly SD): 10%: HOLD add 2,227/wk, PRE 4,289, X 2,627, HOLD stack SD 153,144, HOLD maxDD stack 578,442 -> 597,432, add in the stack's 20 worst weeks 39,568; 20%: HOLD add 4,453/wk, PRE 8,578, X 5,254, HOLD stack SD 155,791, HOLD maxDD stack 578,442 -> 616,421, add in the stack's 20 worst weeks 79,136; 30%: HOLD add 6,680/wk, PRE 12,867, X 7,880, HOLD stack SD 159,764, HOLD maxDD stack 578,442 -> 635,410, add in the stack's 20 worst weeks 118,704

## LINE_WIDE (any replayed cell-session)

| session   | cell            |   lots_30lot_scale |   lots_1000_risk_class |   stop_pts_median |   pre_t_meas |   hold_wk |   pre_wk |     x_wk |   n_trades |
|:----------|:----------------|-------------------:|-----------------------:|------------------:|-------------:|----------:|---------:|---------:|-----------:|
| ASIA      | ba2/EM_t60_s40  |                  4 |                      1 |             40    |         2.55 |    769.24 |  1921    |  -567.46 |        566 |
| ASIA      | ba2/SM_t75_sst  |                  3 |                      2 |             20    |         2.55 |    393.1  |  1245.99 |   698.34 |        522 |
| ASIA      | ba2/HM_t90_s50  |                  2 |                      1 |             50    |         1.53 |   1447    |  1134.25 | -1219.92 |       1100 |
| LONDON    | IF_3m_tg_pd     |                  3 |                      5 |              9    |         1.07 |    634.17 |   463.34 | -1258.4  |       1151 |
| LONDON    | IF_5m_tg_pd     |                  3 |                      5 |              9    |         0.97 |   1052.86 |   317.59 |   215.92 |        850 |
| PREOPEN   | IF_3m_tg_so     |                  7 |                      5 |              9.5  |         0.37 |    206.18 |   185.09 |  -670.13 |        390 |
| NY-AM     | ba2/HM_t75_s90  |                  2 |                      1 |             90    |         2.97 |   1157.82 |  2230.28 |  1365.9  |        780 |
| NY-AM     | SB_HM_st_sig0   |                  5 |                      2 |             22.75 |         2.2  |    725.06 |  1296.54 |   751.38 |        326 |
| NY-AM     | ba2/ST_t120_s50 |                  1 |                      1 |             50    |         1.95 |   1039.93 |   957.82 |   339    |       1270 |

|      |   weeks |   mean |      sd |   maxdd |   worst_week |   worst20_own |   corr |     mde |   stack_mean |   add_in_stack_worst20 |
|:-----|--------:|-------:|--------:|--------:|-------------:|--------------:|-------:|--------:|-------------:|-----------------------:|
| PRE  |      75 | 9751.9 | 17936.4 | 32192.3 |     -27826.1 |       -252599 |    0.5 |  5799.1 |      44127.1 |                  nan   |
| HOLD |      32 | 7425.4 | 21707.8 | 65177.2 |     -25585.5 |       -119062 |    0.4 | 10744.8 |      52447.7 |                  nan   |
| X    |      44 | -345.4 | 17161.3 | 78966.3 |     -43781.4 |       -300707 |    0.1 |  7244   |      20616.2 |                  nan   |
| FULL |     149 | 6401.4 | 19022.2 | 78966.3 |     -43781.4 |       -463126 |    0.4 |  4363.4 |      39563.6 |               -10295.6 |

Per-session $/wk of the book at the 30-lot scale:

|         |   PRE_$wk |   HOLD_$wk |   X_$wk |   FULL_$wk |
|:--------|----------:|-----------:|--------:|-----------:|
| ASIA    |      4301 |       2609 |   -1089 |       2404 |
| LONDON  |       781 |       1687 |   -1042 |        448 |
| PREOPEN |       185 |        206 |    -670 |        -60 |
| NY-AM   |      4485 |       2923 |    2456 |       3610 |

Stack-add (line scaled to 10/20/30% of the stack PRE weekly SD): 10%: HOLD add 5,431/wk, PRE 7,132, X -253, HOLD stack SD 158,228, HOLD maxDD stack 578,442 -> 624,687, add in the stack's 20 worst weeks -7,530; 20%: HOLD add 10,862/wk, PRE 14,265, X -505, HOLD stack SD 165,847, HOLD maxDD stack 578,442 -> 670,932, add in the stack's 20 worst weeks -15,060; 30%: HOLD add 16,292/wk, PRE 21,397, X -758, HOLD stack SD 174,582, HOLD maxDD stack 578,442 -> 717,177, add in the stack's 20 worst weeks -22,590


## Reading
- The D6-only line is a single NY-AM leg: PRE +33.5k/wk, HOLD +17.4k/wk, 2023 span +20.5k/wk at the 30-lot scale (MDE 33k PRE / 57k HOLD / 32k X): positive in every window but inside its MDE in HOLD and in the X span; weekly SD 102k-115k, maxDD 301k-467k, worst week -206k (30 lots on a 90-pt stop is not a sensible size; scale by lots/30). Correlation to the live stack 0.30 (PRE), 0.00 (HOLD), -0.10 (2023 span). Stack-add at 10/20/30% of the stack PRE SD: HOLD +2.2k / +4.5k / +6.7k per week; it adds 40k / 79k / 119k in the stack's 20 worst weeks (full span) but lifts the HOLD stack maxDD (578k -> 597k / 616k / 635k).
- The wider line (any replayed cell-session passing MEASURED, PRE-ranked; these cells do NOT all have NT8 specs, only the item-1 cells do) is positive in PRE (+9.8k/wk) and HOLD (+7.4k/wk) but NEGATIVE in the 2023 span (-0.3k/wk) and does not hedge the stack's bad weeks (add in the 20 worst stack weeks is negative at every risk level); correlation to the stack 0.5 (PRE) and 0.4 (HOLD). It is an honest upper bound for what a measured-basis session book looks like, not the D6 line.
- Net: on live-latency fills the session book collapses from six sessions of IC/CRT/ICT legs to one measured-positive leg (NY-AM HM) and a few minimum-size monitors. The earlier PAIR-PASS stack-add numbers (11-32k/wk at 20% risk) do not survive: the measured HOLD add of every complete pair is negative.



## D3SQ queue refresh (SSA_Q_addendum)
2026-10-28 22:49Z after q1 (TOPEN); queue waves so far [1]: ASIA = no new queue book, LONDON = no new queue book, PRE = no new queue book, NYAM = TOPEN_B2_OR30m_stp_ge0.5_F60 [NY-AM] (MEASURED HOLD +5.38 pts, MDE 14.5, 1 lots, edge-beyond-beta yes), NYPM = no new queue book. CLOSE: no new queue book.


## D3SQ queue refresh (SSA_Q_addendum)
2026-10-28 22:50Z after q1 (TOPEN); queue waves so far [1]: ASIA = no new queue book, LONDON = no new queue book, PRE = no new queue book, NYAM = TOPEN_B2_OR30m_stp_ge0.5_F60 [NY-AM] (MEASURED HOLD +5.38 pts, MDE 14.5, 1 lots, edge-beyond-beta yes), NYPM = no new queue book. CLOSE: no new queue book.


## D3SQ queue refresh (SSA_Q_addendum)
2026-10-28 22:58Z after q2 (sd2a); queue waves so far [1, 2]: ASIA = PRO_ER4_n40_EMA5 [ASIA] (MEASURED HOLD +10.64 pts, MDE 24.2, 1 lots, edge-beyond-beta yes), LONDON = TR1B_reg1m_n60_t3_r0.5 [LONDON] (MEASURED HOLD +5.12 pts, MDE 10.9, 1 lots, edge-beyond-beta no), PRE = TB4B_tick_17_tick_1000_ST60_SW38_T3 [PREOPEN] (MEASURED HOLD +10.07 pts, MDE 23.2, 1 lots, edge-beyond-beta yes), NYAM = TOPEN_B2_OR30m_stp_ge0.5_F60 [W3_1000-1030] (MEASURED HOLD +5.38 pts, MDE 14.5, 1 lots, edge-beyond-beta yes), NYPM = PRO1_AGG_RL3_EMA200_VWAP [NY-PM] (MEASURED HOLD +6.72 pts, MDE 19.7, 1 lots, edge-beyond-beta yes). CLOSE: no new queue book.


## D3SQ queue refresh (SSA_Q_addendum)
2026-10-29 00:12Z after q5 (sd56); queue waves so far [1, 2, 5]: ASIA = PRO_ER4_n40_EMA5 [ASIA] (MEASURED HOLD +10.64 pts, MDE 24.2, 1 lots, edge-beyond-beta yes), LONDON = TR1B_reg1m_n60_t3_r0.5 [LONDON] (MEASURED HOLD +5.12 pts, MDE 10.9, 1 lots, edge-beyond-beta no), PRE = TB4B_tick_17_tick_1000_ST60_SW38_T3 [PREOPEN] (MEASURED HOLD +10.07 pts, MDE 23.2, 1 lots, edge-beyond-beta yes), NYAM = TOPEN_B2_OR30m_stp_ge0.5_F60 [NY-AM] (MEASURED HOLD +5.38 pts, MDE 14.5, 1 lots, edge-beyond-beta yes), NYPM = PRO1_AGG_RL3_EMA200_VWAP [NY-PM] (MEASURED HOLD +6.72 pts, MDE 19.7, 1 lots, edge-beyond-beta yes). CLOSE: no new queue book.


## D3SQ queue refresh (SSA_Q_addendum)
2026-10-29 00:22Z after q4 (sd34); queue waves so far [1, 2, 4, 5]: ASIA = PRO_ER4_n40_EMA5 [ASIA] (MEASURED HOLD +10.64 pts, MDE 24.2, 1 lots, edge-beyond-beta yes), LONDON = TR1B_reg1m_n60_t3_r0.5 [LONDON] (MEASURED HOLD +5.12 pts, MDE 10.9, 1 lots, edge-beyond-beta no), PRE = TB4B_tick_17_tick_1000_ST60_SW38_T3 [PREOPEN] (MEASURED HOLD +10.07 pts, MDE 23.2, 1 lots, edge-beyond-beta yes), NYAM = TOPEN_B2_OR30m_stp_ge0.5_F60 [NY-AM] (MEASURED HOLD +5.38 pts, MDE 14.5, 1 lots, edge-beyond-beta yes), NYPM = PRO1_AGG_RL3_EMA200_VWAP [NY-PM] (MEASURED HOLD +6.72 pts, MDE 19.7, 1 lots, edge-beyond-beta yes). CLOSE: no new queue book.


## D3SQ queue refresh (SSA_Q_addendum)
2026-10-29 00:50Z after q4 (sd34); queue waves so far [1, 2, 4, 5]: ASIA = PRO_ER4_n40_EMA5 [ASIA] (MEASURED HOLD +10.64 pts, MDE 24.2, 1 lots, edge-beyond-beta yes), LONDON = TR1B_reg1m_n60_t3_r0.5 [LONDON] (MEASURED HOLD +5.12 pts, MDE 10.9, 1 lots, edge-beyond-beta no), PRE = TB4B_tick_17_tick_1000_ST60_SW38_T3 [PREOPEN] (MEASURED HOLD +10.07 pts, MDE 23.2, 1 lots, edge-beyond-beta yes), NYAM = TOPEN_B2_OR30m_stp_ge0.5_F60 [NY-AM] (MEASURED HOLD +5.38 pts, MDE 14.5, 1 lots, edge-beyond-beta yes), NYPM = PRO1_AGG_RL3_EMA200_VWAP [NY-PM] (MEASURED HOLD +6.72 pts, MDE 19.7, 1 lots, edge-beyond-beta yes) PARTIAL waves: q2 sd2a: month 2023-12 missing (X span only; PRE/HOLD gates complete); q4 sd34: months 2025-06 (PRE), 2025-10 and 2025-11 (H25 HOLD) missing; HOLD/H25 gates INCOMPLETE; no sd34 cell is promoted on HOLD grounds, at most SESSION-CANDIDATE-PARTIAL; missing months not imputed. CLOSE: no new queue book.


## D3SQ queue refresh (SSA_Q_addendum)
2026-10-29 00:50Z after q4 (sd34); queue waves so far [1, 2, 4, 5]: ASIA = PRO_ER4_n40_EMA5 [ASIA] (MEASURED HOLD +10.64 pts, MDE 24.2, 1 lots, edge-beyond-beta yes), LONDON = TR1B_reg1m_n60_t3_r0.5 [LONDON] (MEASURED HOLD +5.12 pts, MDE 10.9, 1 lots, edge-beyond-beta no), PRE = TB4B_tick_17_tick_1000_ST60_SW38_T3 [PREOPEN] (MEASURED HOLD +10.07 pts, MDE 23.2, 1 lots, edge-beyond-beta yes), NYAM = TOPEN_B2_OR30m_stp_ge0.5_F60 [NY-AM] (MEASURED HOLD +5.38 pts, MDE 14.5, 1 lots, edge-beyond-beta yes), NYPM = PRO1_AGG_RL3_EMA200_VWAP [NY-PM] (MEASURED HOLD +6.72 pts, MDE 19.7, 1 lots, edge-beyond-beta yes) PARTIAL waves: q2 sd2a: month 2023-12 missing (X span only; PRE/HOLD gates complete); q4 sd34: months 2025-06 (PRE), 2025-10 and 2025-11 (H25 HOLD) missing; HOLD/H25 gates INCOMPLETE; no sd34 cell is promoted on HOLD grounds, at most SESSION-CANDIDATE-PARTIAL; missing months not imputed. CLOSE: no new queue book.


## D3SQ queue refresh (SSA_Q_addendum)
2026-10-29 00:50Z after q2 (sd2a); queue waves so far [1, 2, 4, 5]: ASIA = PRO_ER4_n40_EMA5 [ASIA] (MEASURED HOLD +10.64 pts, MDE 24.2, 1 lots, edge-beyond-beta yes), LONDON = TR1B_reg1m_n60_t3_r0.5 [LONDON] (MEASURED HOLD +5.12 pts, MDE 10.9, 1 lots, edge-beyond-beta no), PRE = TB4B_tick_17_tick_1000_ST60_SW38_T3 [PREOPEN] (MEASURED HOLD +10.07 pts, MDE 23.2, 1 lots, edge-beyond-beta yes), NYAM = TOPEN_B2_OR30m_stp_ge0.5_F60 [NY-AM] (MEASURED HOLD +5.38 pts, MDE 14.5, 1 lots, edge-beyond-beta yes), NYPM = PRO1_AGG_RL3_EMA200_VWAP [NY-PM] (MEASURED HOLD +6.72 pts, MDE 19.7, 1 lots, edge-beyond-beta yes) PARTIAL waves: q2 sd2a: month 2023-12 missing (X span only; PRE/HOLD gates complete); q4 sd34: months 2025-06 (PRE), 2025-10 and 2025-11 (H25 HOLD) missing; HOLD/H25 gates INCOMPLETE; no sd34 cell is promoted on HOLD grounds, at most SESSION-CANDIDATE-PARTIAL; missing months not imputed. CLOSE: no new queue book.


## D3SQ queue refresh (SSA_Q_addendum)
2026-10-29 01:48Z after q3 (sd1); queue waves so far [1, 2, 3, 4, 5]: ASIA = FV|ASIA|tf-9500|{"entry": "c", "sing": 0, "size": 8, "tf": -9500}|none|B60/60|S [ASIA] (MEASURED HOLD +3.33 pts, MDE 6.8, 1 lots, edge-beyond-beta yes), LONDON = TR1B_reg1m_n60_t3_r0.5 [LONDON] (MEASURED HOLD +5.12 pts, MDE 10.9, 1 lots, edge-beyond-beta no), PRE = CRT|PRE|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B40/40|R [PREOPEN] (MEASURED HOLD +3.93 pts, MDE 10.9, 1 lots, edge-beyond-beta yes), NYAM = TOPEN_B2_OR30m_stp_ge0.5_F60 [W3_1000-1030] (MEASURED HOLD +5.38 pts, MDE 14.5, 1 lots, edge-beyond-beta yes), NYPM = CRT|NYPM|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|R [NY-PM] (MEASURED HOLD +5.34 pts, MDE 10.0, 1 lots, edge-beyond-beta yes) PARTIAL waves: q2 sd2a: month 2023-12 missing (X span only; PRE/HOLD gates complete); q4 sd34: months 2025-06 (PRE), 2025-10 and 2025-11 (H25 HOLD) missing; HOLD/H25 gates INCOMPLETE; no sd34 cell is promoted on HOLD grounds, at most SESSION-CANDIDATE-PARTIAL; missing months not imputed. CLOSE: no new queue book.


## D3SQ queue refresh (SSA_Q_addendum)
2026-10-29 01:48Z after q6 (sb3); queue waves so far [1, 2, 3, 4, 5, 6]: ASIA = FV|ASIA|tf-9500|{"entry": "c", "sing": 0, "size": 8, "tf": -9500}|none|B60/60|S [ASIA] (MEASURED HOLD +3.33 pts, MDE 6.8, 1 lots, edge-beyond-beta yes), LONDON = C5M1_NQ_775 [LONDON] (MEASURED HOLD +5.41 pts, MDE 23.9, 1 lots, edge-beyond-beta yes), PRE = CRT|PRE|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B40/40|R [PREOPEN] (MEASURED HOLD +3.93 pts, MDE 10.9, 1 lots, edge-beyond-beta yes), NYAM = TOPEN_B2_OR30m_stp_ge0.5_F60 [NY-AM] (MEASURED HOLD +5.38 pts, MDE 14.5, 1 lots, edge-beyond-beta yes), NYPM = CRT|NYPM|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|R [NY-PM] (MEASURED HOLD +5.34 pts, MDE 10.0, 1 lots, edge-beyond-beta yes) PARTIAL waves: q6 sb3: month 2025-10 (H25 HOLD) missing (worker killed); HOLD/H25 gates INCOMPLETE; tiers are SESSION-CANDIDATE-PARTIAL at most; missing month not imputed; q2 sd2a: month 2023-12 missing (X span only; PRE/HOLD gates complete); q4 sd34: months 2025-06 (PRE), 2025-10 and 2025-11 (H25 HOLD) missing; HOLD/H25 gates INCOMPLETE; no sd34 cell is promoted on HOLD grounds, at most SESSION-CANDIDATE-PARTIAL; missing months not imputed. CLOSE: no new queue book.


## D3SQ queue refresh (SSA_Q_addendum)
2026-10-29 03:14Z after q7 (sd6b); queue waves so far [1, 2, 3, 4, 5, 6, 7]: ASIA = ba2/SM_t75_sst [ASIA] (MEASURED HOLD +6.01 pts, MDE 13.2, 2 lots, edge-beyond-beta yes), LONDON = C5M1_NQ_775 [LONDON] (MEASURED HOLD +5.41 pts, MDE 23.9, 1 lots, edge-beyond-beta yes), PRE = pb4:tick_1000|ST10|SW62|T2|60/60 [PREOPEN] (MEASURED HOLD +8.62 pts, MDE 24.2, 1 lots, edge-beyond-beta yes), NYAM = TOPEN_B2_OR30m_stp_ge0.5_F60 [NY-AM] (MEASURED HOLD +5.38 pts, MDE 14.5, 1 lots, edge-beyond-beta yes), NYPM = CRT|NYPM|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|R [NY-PM] (MEASURED HOLD +5.34 pts, MDE 10.0, 1 lots, edge-beyond-beta yes) PARTIAL waves: q6 sb3: month 2025-10 (H25 HOLD) missing (worker killed); HOLD/H25 gates INCOMPLETE; tiers are SESSION-CANDIDATE-PARTIAL at most; missing month not imputed; q2 sd2a: month 2023-12 missing (X span only; PRE/HOLD gates complete); q4 sd34: months 2025-06 (PRE), 2025-10 and 2025-11 (H25 HOLD) missing; HOLD/H25 gates INCOMPLETE; no sd34 cell is promoted on HOLD grounds, at most SESSION-CANDIDATE-PARTIAL; missing months not imputed. CLOSE: no new queue book.


## D3SQ queue refresh (SSA_Q_addendum)
2026-10-29 03:14Z after q8 (sb2); queue waves so far [1, 2, 3, 4, 5, 6, 7, 8]: ASIA = ba2/SM_t75_sst [ASIA] (MEASURED HOLD +6.01 pts, MDE 13.2, 2 lots, edge-beyond-beta yes), LONDON = PBX4_PBS_f60_T3_DFLIP [LONDON] (MEASURED HOLD +16.34 pts, MDE 29.2, 1 lots, edge-beyond-beta yes), PRE = pb4:tick_1000|ST10|SW62|T2|60/60 [PREOPEN] (MEASURED HOLD +8.62 pts, MDE 24.2, 1 lots, edge-beyond-beta yes), NYAM = TOPEN_B2_OR30m_stp_ge0.5_F60 [W3_1000-1030] (MEASURED HOLD +5.38 pts, MDE 14.5, 1 lots, edge-beyond-beta yes), NYPM = CRT|NYPM|tf-9500|{"L": 3, "buf": 0, "etf": -9500, "etype": "close", "htf": 30, "inside": 1, "s": 1, "stop": "s", "tmode": "SO"}|none|B50/50|R [NY-PM] (MEASURED HOLD +5.34 pts, MDE 10.0, 1 lots, edge-beyond-beta yes) PARTIAL waves: q6 sb3: month 2025-10 (H25 HOLD) missing (worker killed); HOLD/H25 gates INCOMPLETE; tiers are SESSION-CANDIDATE-PARTIAL at most; missing month not imputed; q2 sd2a: month 2023-12 missing (X span only; PRE/HOLD gates complete); q4 sd34: months 2025-06 (PRE), 2025-10 and 2025-11 (H25 HOLD) missing; HOLD/H25 gates INCOMPLETE; no sd34 cell is promoted on HOLD grounds, at most SESSION-CANDIDATE-PARTIAL; missing months not imputed. CLOSE: no new queue book.
