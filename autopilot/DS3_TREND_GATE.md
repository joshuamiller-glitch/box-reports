# DS3_TREND_GATE - section C: the rules (agent TG-1, 2026-10-30)

Prereg autopilot/TG1_prereg.md sha256 c6de24a3577b20521c20ce2346d186023d4e45a8fa9edad5d032ed8d34ae7b95 (+ addenda 0, 1 in DECISIONS.md). Research only; UNTOUCHED never read; masks own and capped 20260206 (2026 = 5 real weeks, sign only; L3M view-only, never used to select). Selection on PRE + X' only; ONE recent look per group (hashes in DECISIONS.md). Primary unit: net pts per PLANNED lot on the 70/30 plain dip split, basis N, "lift" = mean of the KEPT trades minus the mean of all signals of the unit (so a gate with lift +2 makes each kept trade worth 2 pts more); per contract = sum pts / sum final lots; economic gain = (kept sum - all sum) / signals (the opportunity cost of the skipped trades is IN it); the lock-engine stack is the exact l2set engine ($/wk, 6 engine books ST HM WT KB SM PE; MV PB DN MA trade-level only). Method lesson (CF-A/B/ENG) applied: a result is trusted only if it holds per planned lot, per contract AND on the stack, and in the risk-matched frame it is labelled STRUCTURE.

## 0. Scoreboard by group

| group | cells_scored | eligible | selected | SEL_lift | Y26 | L3M | L6M | HOLD | share_L6M_pos | candidate |
|---|---|---|---|---|---|---|---|---|---|---|
| G1 single gates | 429025 | 6688 | 539 | 4.82 | -0.50 | -0.47 | -0.35 | -0.33 | 0.50 | 150 |
| G2 sizers (risk-matched) | 352002 | 7493 | 565 | 1.89 | 0.05 | -0.00 | 0.04 | 0.04 | 0.51 | 159 |
| G3 combinations | 37003 | 35957 | 120 | 5.31 | 0.34 | 0.16 | 0.29 | 0.14 | 0.56 | 35 |

Reading: the cells were chosen because they look good in PRE+X' (SEL_lift, in-sample); out of sample the same cells are worth about zero (L6M, HOLD, 2026 columns) and about half are positive, i.e. what selection found is what pure noise would give. PASS = 0 in every group.

## 1. G1 - single-measure gates (429,025 cells, 51 units: ALL10, ENG6, 10 books, 39 book x session; 1,197 measures x 8 skip rules)

Eligible on PRE+X' (lift>0 in PRE and X' separately on E_73 N and E_MKT N, E_73 LIVE-CAL>0 pooled, keep 30-97%, >=100 skipped, week-clustered lift t>=2): 6,688. Selected (top 5 per unit + top 2 per family): 539; 150 are positive in Y26, L6M, HOLD, PRE, X' on lift (planned lot and per contract, E_73 N, E_MKT N, LIVE-CAL) = CANDIDATE by sign; only 7 of the 539 have L6M lift outside their MDE; 6 of the CANDIDATEs (LEAD by size). Program validity over the 539 selected rows (qv, L6M mask): White RC best-cell p 0.149, studentised p 0.016, Romano-Wolf survivors 1, PBO 0.29, minimum backtest length None years, RC p adjusted for the cumulative 924,611 cells scored (UF cumulative 143,584 + this program's G1+G2) = 1.00. PASS requires the cumulative-adjusted p<=0.05 -> 0 PASS.

Top 25 CANDIDATEs by L6M lift (recent first; lift per PLANNED lot, E_73 N; selected on PRE+X' so PRE/X' are in-sample):

| cell | keep L6M | tpw kept | Y26 | L3M | L6M | MDE L6M | HOLD | PRE | X' | per contract L6M | econ L6M | skipped/kept mean L6M | placebo p (random gate / shuffled day) | RW p |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 5-min +DI minus -DI (7) [keepTop3] KB|asia | 0.31 | 3.68 | 11.42 | 18.75 | 15.58 | 9.57 | 14.43 | 7.82 | 7.16 | 15.79 | 4.36 | -6.3/+16.2 | 0.005/0.010 | 0.15 |
| large25_share_30m [keepTopHalf] SM|asia | 0.38 | 1.33 | 7.60 | 3.73 | 14.76 | 18.10 | 10.33 | 11.02 | 9.02 | 14.57 | 2.42 | -3.9/+19.7 | 0.080/0.050 | 0.98 |
| 1-hour Supertrend(7,2) distance (ATR) [keepTop3] HM|asia | 0.33 | 3.04 | 5.77 | 13.78 | 13.60 | 15.74 | 12.60 | 5.90 | 12.51 | 13.70 | 0.52 | -0.8/+19.5 | 0.010/0.010 | 0.83 |
| large10_bias_60m [keepTopHalf] PE|nypm | 0.41 | 3.36 | 22.11 | 13.53 | 11.77 | 14.45 | 11.20 | 5.37 | 6.16 | 11.79 | 6.00 | -10.1/+9.8 | 0.005/0.010 | 0.84 |
| corr_nq_ES_60 [keepBot3] PE | 0.19 | 8.25 | 13.82 | 13.28 | 11.43 | 8.52 | 10.66 | 5.51 | 0.99 | 11.40 | 1.57 | -1.9/+12.2 | 0.005/0.010 | 0.20 |
| skew_5d [keepTop3] HM|asia | 0.28 | 2.57 | 8.66 | 12.90 | 10.70 | 17.83 | 8.82 | 5.02 | 14.71 | 10.65 | -1.26 | +1.7/+16.6 | 0.030/0.020 | 1.00 |
| 5-min 20-bar Donchian width (ATR) [keepTopHalf] MV|asia | 0.43 | 4.68 | 8.29 | 9.98 | 10.32 | 7.96 | 8.60 | 4.26 | 12.96 | 10.25 | 3.68 | -6.4/+11.6 | 0.005/0.010 | 0.40 |
| 5-min Parabolic SAR run length [keepTop3] PB|asia | 0.36 | 3.21 | 18.58 | 10.44 | 10.24 | 11.19 | 8.07 | 12.07 | 2.32 | 10.31 | -3.34 | +5.3/+21.4 | 0.030/0.040 | 0.98 |
| 1-hour EMA ribbon expansion [keepBotHalf] PB|london | 0.34 | 2.29 | 2.10 | 8.25 | 9.68 | 18.45 | 7.19 | 10.58 | 4.74 | 9.45 | -2.82 | +4.2/+18.8 | 0.070/0.040 | 1.00 |
| pc1_share_60 [keepBot3] MA | 0.36 | 5.21 | 23.35 | 9.66 | 9.61 | 9.90 | 8.09 | 6.05 | 4.37 | 9.68 | -0.51 | +0.8/+15.8 | 0.010/0.020 | 0.79 |
| 1-min Aroon(25) oscillator [keepBotHalf] MV|nypm | 0.42 | 3.04 | 6.43 | 7.77 | 8.24 | 12.62 | 9.90 | 6.92 | 1.81 | 8.22 | 3.68 | -6.4/+7.9 | 0.010/0.020 | 0.99 |
| hmm2_high_1m [skipBot3] MA|london | 0.53 | 1.96 | 0.10 | 1.13 | 8.24 | 17.08 | 6.02 | 6.13 | 6.19 | 8.55 | 0.09 | -0.2/+17.4 | 0.075/0.030 | 1.00 |
| prev_er_rth [skipTop3] KB|nypm | 0.63 | 5.29 | 4.57 | 8.86 | 8.09 | 6.17 | 6.45 | 2.70 | 4.36 | 7.99 | 4.12 | -11.1/+10.7 | 0.010/0.020 | 0.01 |
| runsz100_5m [keepTopHalf] MA|asia | 0.42 | 2.18 | 3.29 | 5.95 | 7.96 | 15.75 | 6.28 | 4.96 | 10.21 | 7.89 | 2.91 | -5.0/+8.7 | 0.040/0.109 | 1.00 |
| 4-hour Parabolic SAR run length [keepTop3] PB|nyam | 0.34 | 2.71 | 2.73 | 12.29 | 7.94 | 16.19 | 6.23 | 6.80 | 7.95 | 7.77 | -1.27 | +1.9/+14.0 | 0.050/0.079 | 1.00 |
| 5-min Bollinger bandwidth [skipBot3] HM|asia | 0.42 | 3.86 | 3.45 | 7.57 | 7.66 | 10.32 | 7.39 | 5.48 | 12.35 | 7.83 | -0.23 | +0.4/+13.5 | 0.065/0.099 | 1.00 |
| sig_rv_5m [keepBot3] PB|london | 0.37 | 2.50 | 10.73 | 11.61 | 7.60 | 12.74 | 4.43 | 4.85 | 4.42 | 7.49 | -2.99 | +4.7/+16.7 | 0.045/0.158 | 1.00 |
| ret_ZN_1d [keepTop3] WT|nypm | 0.23 | 2.50 | 13.57 | 12.31 | 7.45 | 9.50 | 6.78 | 4.43 | 4.58 | 7.49 | 2.38 | -3.1/+6.6 | 0.010/0.020 | 1.00 |
| prev_er_rth [keepBotHalf] ST|nypm | 0.46 | 3.61 | 19.97 | 2.75 | 6.66 | 12.86 | 7.29 | 5.04 | 6.84 | 6.64 | 1.70 | -3.1/+9.2 | 0.035/0.020 | 1.00 |
| 1-min distance to PSAR (ATR) [keepBot3] SM|nyam | 0.40 | 1.36 | 7.71 | 17.73 | 6.47 | 21.01 | 5.55 | 15.10 | 15.66 | 6.71 | 0.58 | -1.0/+9.8 | 0.219/0.198 | 1.00 |
| sig_imb10_s [keepTop3] DN|asia | 0.42 | 2.68 | 9.78 | 1.99 | 6.35 | 17.29 | 5.27 | 7.06 | 7.91 | 6.61 | -3.33 | +5.7/+16.6 | 0.174/0.139 | 1.00 |
| hmm3_updown_5m [keepBotHalf] MA|london | 0.49 | 1.81 | 12.49 | 11.04 | 6.29 | 12.87 | 5.82 | 8.21 | 7.50 | 6.19 | -1.59 | +3.1/+15.4 | 0.129/0.168 | 1.00 |
| ret_RTY_1d [skipBot3] HM|asia | 0.73 | 6.71 | 8.25 | 8.74 | 6.29 | 6.89 | 6.07 | 2.40 | 6.10 | 6.39 | 2.96 | -10.8/+12.2 | 0.010/0.010 | 0.84 |
| 1-min Kaufman efficiency ratio(10) [keepBot3] HM|london | 0.36 | 2.71 | 3.99 | 0.82 | 6.14 | 13.62 | 5.22 | 11.96 | 11.27 | 6.12 | 1.67 | -2.6/+7.0 | 0.154/0.129 | 1.00 |
| sig_es_nq_div5 [skipTop3] SM|asia | 0.71 | 2.52 | 8.66 | 2.65 | 5.73 | 10.87 | 5.86 | 6.35 | 2.14 | 5.72 | 2.60 | -8.9/+10.7 | 0.085/0.099 | 1.00 |

### Lock-engine stack for the CANDIDATEs that touch engine books (unscaled, $/wk vs the same stack unfiltered; MDE = 2.8 SE of the weekly delta)

101 CANDIDATE cells touch engine books. Stack delta > 0 in both L6M and HOLD (E_73 N): 51; outside MDE in L6M: 0; mean delta over the 101: L6M +0.1k, HOLD -0.0k, PRE -0.2k, X' +1.0k, Y26 +4.8k per week (base stack L6M +72.1k, HOLD +61.3k, PRE +59.5k, X' +17.8k on E_73 N; +18.8k / +8.6k on the live-like market M base).

| cell | Y26 k$ | L6M k$ | MDE L6M k$ | HOLD k$ | PRE k$ | X' k$ | L6M k$ (mkt M) |
|---|---|---|---|---|---|---|---|
| ret_RTY_1d [skipBot3] HM|asia | 37.43 | 19.04 | 20.18 | 13.95 | 0.41 | 1.89 | 21.42 |
| 15m.don55_wexp [skipBot3] HM|asia | 33.59 | 12.47 | 12.87 | 10.02 | -0.51 | 4.49 | 9.83 |
| 15m.don55_wexp [keepTopHalf] HM|asia | 33.59 | 12.47 | 12.87 | 10.02 | -0.51 | 4.49 | 9.83 |
| skew_5d [keepTop3] HM|asia | 18.17 | 11.03 | 17.91 | 7.87 | -1.41 | 3.33 | 13.08 |
| 1h.st7_2_dist [keepTop3] HM|asia | 22.91 | 9.54 | 18.76 | 5.38 | -4.06 | 2.85 | 14.05 |
| 1m.er10 [keepBot3] HM|london | 11.82 | 4.98 | 12.80 | 3.22 | 1.48 | -2.33 | 4.70 |
| 3m.ich_thick [skipBot3] WT|london | 5.26 | 4.52 | 7.77 | 3.07 | 2.92 | 3.21 | 4.81 |
| 5m.bbw [skipBot3] HM|asia | 9.78 | 3.89 | 19.75 | 0.42 | -2.59 | -0.10 | 4.66 |
| vwap_slope15_rth [skipBot3] PE | 5.07 | 3.82 | 4.63 | 3.58 | 0.89 | 0.59 | 4.30 |
| large10_share_30m [skipBot3] WT | 4.30 | 3.76 | 12.00 | 2.08 | 1.25 | 2.09 | 3.94 |

No CANDIDATE is outside its stack MDE in L6M: the per-trade quality lift does not turn into dollars once the skipped trades are lost and the locks are re-run (CF-A/B/ENG lesson reproduced).

## 2. The directive-named rules as fixed plain gates (NOT selected; 14 rules, Bonferroni 14)

Conditions exactly as written in the directive (5-min unless stated; directional measures in the signal direction). All-signals unit ALL10 and the six-engine-book unit ENG6, E_73 N, per planned lot; 'pc' = per contract of final lots; 'econ' = opportunity-cost-inclusive gain per signal.

| rule (kept side) | unit | keep | tpw kept L6M | lift Y26 | L6M | MDE | HOLD | PRE | X' | econ L6M | P(tgt) kept/skipped L6M | kept/skipped mean L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 5m ADX14>25 & 5m EMA50/200 sep>1 ATR (dir) | ALL10 | 0.29 | 99.68 | -4.34 | 1.47 | 4.92 | 1.46 | 1.19 | 2.72 | -1.90 | 0.54/0.52 | +4.7/+2.7 |
| 5m ADX14>25 & 5m EMA50/200 sep>1 ATR (dir) | ENG6 | 0.28 | 66.29 | -5.08 | 1.80 | 5.38 | 1.92 | 0.99 | 2.37 | -1.26 | 0.55/0.52 | +4.2/+1.7 |
| 5m EMA20/50 sep>1 ATR (dir) & ADX14>25 | ALL10 | 0.31 | 106.57 | -2.65 | 0.85 | 3.84 | 1.03 | 1.58 | 1.26 | -2.00 | 0.54/0.53 | +4.1/+2.9 |
| 5m EMA20/50 sep>1 ATR (dir) & ADX14>25 | ENG6 | 0.30 | 70.64 | -2.50 | 0.97 | 4.38 | 1.27 | 1.65 | 1.15 | -1.43 | 0.54/0.53 | +3.4/+2.0 |
| 15m ADX14>25 | ALL10 | 0.54 | 188.39 | -4.46 | 0.37 | 2.95 | 0.69 | 0.85 | 0.08 | -1.29 | 0.53/0.53 | +3.6/+2.8 |
| 15m ADX14>25 | ENG6 | 0.54 | 128.96 | -5.45 | -0.18 | 2.97 | 0.10 | 0.94 | 0.22 | -1.22 | 0.52/0.54 | +2.3/+2.7 |
| 5m ER20>=0.3 | ALL10 | 0.38 | 133.32 | 2.46 | 2.45 | 2.54 | 2.29 | 1.01 | 0.71 | -1.07 | 0.55/0.52 | +5.7/+1.7 |
| 5m ER20>=0.3 | ENG6 | 0.37 | 87.18 | 3.54 | 3.31 | 2.75 | 3.17 | 1.19 | 0.08 | -0.33 | 0.56/0.51 | +5.8/+0.5 |
| 5m Chop14<=61.8 | ALL10 | 0.93 | 323.43 | 0.57 | 0.29 | 0.71 | 0.20 | -0.21 | 0.12 | 0.04 | 0.53/0.49 | +3.5/-0.5 |
| 5m Chop14<=61.8 | ENG6 | 0.93 | 221.21 | 0.77 | 0.39 | 0.72 | 0.28 | -0.19 | -0.12 | 0.20 | 0.53/0.47 | +2.8/-3.0 |
| not squeeze (5m) | ALL10 | 0.88 | 305.96 | 0.42 | 0.72 | 0.94 | 0.56 | 0.37 | 0.43 | 0.24 | 0.54/0.48 | +4.0/-2.0 |
| not squeeze (5m) | ENG6 | 0.89 | 210.00 | 0.58 | 0.60 | 1.01 | 0.50 | 0.53 | 0.47 | 0.26 | 0.54/0.49 | +3.1/-2.2 |
| HTF agree (1h EMA20>50 in signal dir) | ALL10 | 0.52 | 179.93 | -3.14 | 0.07 | 3.73 | -0.29 | 0.25 | 1.21 | -1.53 | 0.53/0.53 | +3.3/+3.2 |
| HTF agree (1h EMA20>50 in signal dir) | ENG6 | 0.51 | 122.00 | -3.50 | 0.22 | 3.71 | -0.15 | 0.42 | 1.20 | -1.07 | 0.53/0.53 | +2.7/+2.2 |
| >=5 of 8 TF majority up (xtf.tf_majority>=3) | ALL10 | 0.59 | 205.36 | -1.76 | -0.10 | 2.76 | -0.24 | -0.01 | 1.36 | -1.40 | 0.53/0.53 | +3.2/+3.4 |
| >=5 of 8 TF majority up (xtf.tf_majority>=3) | ENG6 | 0.58 | 136.61 | -1.96 | 0.15 | 2.82 | 0.03 | 0.16 | 1.00 | -0.95 | 0.53/0.53 | +2.6/+2.2 |
| not extended (5m price within 3 ATR of EMA20) | ALL10 | 0.96 | 335.25 | 0.06 | -0.11 | 0.50 | -0.05 | -0.04 | -0.31 | -0.23 | 0.53/0.57 | +3.1/+6.3 |
| not extended (5m price within 3 ATR of EMA20) | ENG6 | 0.96 | 227.46 | -0.33 | -0.34 | 0.54 | -0.22 | -0.10 | -0.44 | -0.42 | 0.53/0.61 | +2.1/+10.5 |
| 3-index agree (ES,RTY,YM 1h all with signal) | ALL10 | 0.65 | 227.61 | 0.07 | 0.33 | 2.13 | 0.30 | -0.46 | 0.02 | -0.91 | 0.53/0.52 | +3.6/+2.6 |
| 3-index agree (ES,RTY,YM 1h all with signal) | ENG6 | 0.65 | 153.71 | 1.08 | 0.83 | 2.23 | 0.73 | -0.38 | 0.07 | -0.32 | 0.54/0.51 | +3.3/+0.9 |

The OFF side of the directive is the complement of the ON rule (ER<0.3, Chop>61.8, ADX<20, squeeze on are the skipped sets of the rows 'ER20>=0.3', 'Chop14<=61.8', 'ADX14>=20' (not run separately), 'not squeeze').

### 2b. Per book: 5-min ER(20) >= 0.3 (skip the chop side) - the one named rule positive in every window

| unit | pc Y26 | pc L6M | pc HOLD | pc PRE | pc X' | keep L6M | MDE pc L6M | tpw kept | tpw all | P(tgt) kept | P(tgt) skipped | econ L6M/signal |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL10 | 2.45 | 2.45 | 2.28 | 1.01 | 0.71 | 0.38 | 2.54 | 133.32 | 347.89 | 0.55 | 0.52 | -1.07 |
| DN | -0.93 | 1.87 | 1.63 | 0.47 | 1.01 | 0.43 | 5.05 | 10.75 | 25.04 | 0.55 | 0.53 | -2.33 |
| ENG6 | 3.54 | 3.30 | 3.16 | 1.20 | 0.08 | 0.37 | 2.75 | 87.18 | 237.00 | 0.56 | 0.51 | -0.33 |
| HM | -0.06 | 3.01 | 2.55 | -1.43 | 0.21 | 0.38 | 6.07 | 12.32 | 32.46 | 0.55 | 0.50 | -1.53 |
| KB | 6.07 | 5.28 | 5.32 | 0.73 | 1.41 | 0.36 | 5.35 | 16.00 | 44.89 | 0.54 | 0.48 | 1.03 |
| MA | -6.80 | -0.61 | -0.78 | -1.00 | 4.68 | 0.38 | 10.76 | 5.57 | 14.54 | 0.55 | 0.54 | -4.03 |
| MV | 2.15 | 0.11 | -0.10 | 0.75 | 4.17 | 0.41 | 5.06 | 16.43 | 40.39 | 0.51 | 0.51 | -1.32 |
| PB | -0.58 | 0.68 | 0.71 | 1.45 | -1.24 | 0.43 | 5.01 | 13.39 | 30.93 | 0.54 | 0.54 | -3.99 |
| PE | 2.25 | 3.30 | 2.57 | 2.49 | -1.11 | 0.41 | 5.66 | 17.32 | 42.64 | 0.52 | 0.47 | 0.87 |
| SM | 2.34 | 1.72 | 2.14 | 0.10 | 0.92 | 0.48 | 9.98 | 5.63 | 11.63 | 0.52 | 0.50 | -0.84 |
| ST | 8.31 | 3.75 | 4.25 | 3.16 | 0.55 | 0.38 | 5.87 | 16.89 | 44.86 | 0.56 | 0.49 | -1.31 |
| WT | 1.48 | 1.77 | 1.42 | 0.66 | -0.77 | 0.32 | 3.52 | 19.21 | 60.93 | 0.62 | 0.58 | -0.72 |

Plain sentence: "taking the engine books only when the 5-min Kaufman efficiency ratio(20) is >= 0.3 keeps 37% of signals and adds +3.3 pts per contract in the last 6 months (MDE 2.75), 87 trades/week of 237; the skipped 63% earned +0.5 pts per planned lot (kept +5.8); positive in HOLD (+3.2), PRE (+1.2), X' (+0.1)."  KB: keeps 36%, +5.3 pts per contract L6M (MDE 5.4), 16 trades/week of 45; PE +3.3 (5.7); ST +3.8 (5.9); HM +3.0 (6.1).

### 2c. Lock-engine stack for the named gates (ENG6, $/wk vs the unfiltered stack; unscaled = the skipped signals are lost; risk-matched = kept lots x 1/keep, cap 3.5 = STRUCTURE)

| base | frame | rule | keep | Y26 k$ | L3M | L6M | MDE L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|---|
| market-at-signal, meas | unscaled | ER20>=0.3 (5m) | 0.39 | 60.58 | 46.74 | 17.29 | 59.20 | 21.23 | -7.46 | -0.85 |
| market-at-signal, meas | unscaled | not squeeze (5m) | 0.90 | -0.29 | 2.93 | -2.34 | 24.62 | -3.69 | 7.41 | 5.88 |
| market-at-signal, meas | unscaled | Chop14<=61.8 (5m) | 0.94 | 6.69 | -0.90 | -1.66 | 17.45 | -3.92 | -7.81 | 2.48 |
| market-at-signal, meas | unscaled | ADX14>25 & EMA50/200 sep>1 (5m) | 0.27 | 2.43 | 12.60 | 5.39 | 69.38 | 11.07 | -16.85 | 8.36 |
| market-at-signal, meas | unscaled | ER20>=0.3 & not squeeze | 0.38 | 72.56 | 53.30 | 20.33 | 58.26 | 23.85 | -8.72 | 0.10 |
| market-at-signal, meas | unscaled | ER20>=0.25 (5m) | 0.48 | 78.30 | 54.83 | 29.15 | 59.24 | 29.94 | -13.07 | -1.06 |
| market-at-signal, meas | unscaled | ER20>=0.35 (5m) | 0.30 | 57.95 | 49.70 | 11.49 | 55.20 | 15.93 | -12.92 | 2.20 |
| market-at-signal, meas | unscaled | 15m ER20>=0.3 | 0.36 | 5.51 | 28.33 | 5.62 | 50.28 | 13.11 | -10.82 | -9.00 |
| market-at-signal, meas | unscaled | 1m ER20>=0.3 | 0.29 | 59.44 | 32.34 | -10.09 | 59.63 | -9.85 | -18.49 | 2.57 |
| market-at-signal, meas | riskmatched | ER20>=0.3 (5m) | 0.39 | 141.90 | 85.25 | 23.94 | 80.39 | 29.60 | -11.82 | 3.36 |
| market-at-signal, meas | riskmatched | not squeeze (5m) | 0.90 | -0.25 | 6.40 | 2.23 | 21.15 | -1.71 | 0.64 | 8.79 |
| market-at-signal, meas | riskmatched | Chop14<=61.8 (5m) | 0.94 | 10.65 | 6.98 | 5.01 | 18.55 | 0.79 | -8.87 | 6.78 |
| market-at-signal, meas | riskmatched | ADX14>25 & EMA50/200 sep>1 (5m) | 0.27 | 74.65 | 57.16 | 37.31 | 110.64 | 35.08 | -19.13 | 36.47 |
| market-at-signal, meas | riskmatched | ER20>=0.3 & not squeeze | 0.38 | 154.45 | 84.05 | 22.03 | 79.74 | 28.51 | -9.89 | 8.26 |
| market-at-signal, meas | riskmatched | ER20>=0.25 (5m) | 0.48 | 94.97 | 58.79 | 25.54 | 60.65 | 31.09 | -11.60 | 0.60 |
| market-at-signal, meas | riskmatched | ER20>=0.35 (5m) | 0.30 | 145.93 | 71.60 | 18.00 | 80.36 | 15.37 | -4.38 | 4.80 |
| market-at-signal, meas | riskmatched | 15m ER20>=0.3 | 0.36 | -31.29 | 3.66 | 1.56 | 71.21 | 3.98 | -23.62 | -5.46 |
| market-at-signal, meas | riskmatched | 1m ER20>=0.3 | 0.29 | 120.68 | 21.10 | -20.38 | 66.36 | -29.45 | -12.07 | 13.32 |
| 70/30 dip split, N | unscaled | ER20>=0.3 (5m) | 0.39 | 36.64 | 24.52 | -7.58 | 57.97 | -3.37 | -18.72 | -9.16 |
| 70/30 dip split, N | unscaled | not squeeze (5m) | 0.90 | 9.69 | 2.04 | -3.59 | 23.80 | -3.35 | 6.24 | 1.81 |
| 70/30 dip split, N | unscaled | Chop14<=61.8 (5m) | 0.94 | 3.44 | -2.55 | -2.45 | 14.21 | -5.13 | -6.38 | 0.80 |
| 70/30 dip split, N | unscaled | ADX14>25 & EMA50/200 sep>1 (5m) | 0.27 | -28.19 | -20.07 | -24.24 | 70.22 | -19.08 | -36.11 | -3.10 |
| 70/30 dip split, N | unscaled | ER20>=0.3 & not squeeze | 0.38 | 47.55 | 30.32 | -4.98 | 56.73 | -1.13 | -20.75 | -8.32 |
| 70/30 dip split, N | unscaled | ER20>=0.25 (5m) | 0.48 | 62.26 | 36.68 | 10.08 | 55.58 | 10.62 | -17.85 | -6.06 |
| 70/30 dip split, N | unscaled | ER20>=0.35 (5m) | 0.30 | 28.80 | 21.15 | -20.38 | 55.10 | -15.90 | -29.03 | -8.17 |
| 70/30 dip split, N | unscaled | 15m ER20>=0.3 | 0.36 | -10.20 | 6.73 | -20.47 | 53.28 | -14.01 | -27.79 | -19.56 |
| 70/30 dip split, N | unscaled | 1m ER20>=0.3 | 0.29 | 25.31 | 0.44 | -47.01 | 59.05 | -45.40 | -38.85 | -9.34 |
| 70/30 dip split, N | riskmatched | ER20>=0.3 (5m) | 0.39 | 118.76 | 68.10 | 18.19 | 79.39 | 24.07 | -19.76 | 3.86 |
| 70/30 dip split, N | riskmatched | not squeeze (5m) | 0.90 | 17.90 | 3.64 | 1.98 | 26.22 | 0.41 | 5.20 | 4.65 |
| 70/30 dip split, N | riskmatched | Chop14<=61.8 (5m) | 0.94 | 0.08 | -2.76 | 0.64 | 13.19 | -3.71 | -6.19 | 3.51 |
| 70/30 dip split, N | riskmatched | ADX14>25 & EMA50/200 sep>1 (5m) | 0.27 | 67.87 | 34.02 | 21.78 | 110.82 | 19.29 | -27.21 | 32.75 |
| 70/30 dip split, N | riskmatched | ER20>=0.3 & not squeeze | 0.38 | 131.80 | 71.96 | 12.60 | 82.75 | 19.06 | -19.42 | 13.04 |
| 70/30 dip split, N | riskmatched | ER20>=0.25 (5m) | 0.48 | 79.20 | 41.20 | 7.54 | 59.33 | 13.45 | -23.93 | 2.44 |
| 70/30 dip split, N | riskmatched | ER20>=0.35 (5m) | 0.30 | 130.87 | 54.96 | 5.22 | 75.77 | 0.28 | 2.32 | 3.63 |
| 70/30 dip split, N | riskmatched | 15m ER20>=0.3 | 0.36 | -70.73 | -27.18 | -29.35 | 64.52 | -28.14 | -39.63 | -8.09 |
| 70/30 dip split, N | riskmatched | 1m ER20>=0.3 | 0.29 | 124.92 | 12.49 | -34.30 | 79.01 | -47.12 | -4.59 | 7.17 |

Random-gate placebo (500 draws at the same keep rate, L6M lift per planned lot): ER20>=0.3 (5m): real +3.31 vs placebo 95th pct +1.34 (p 0.002); not squeeze (5m): real +0.60 vs placebo 95th pct +0.37 (p 0.004); Chop14<=61.8 (5m): real +0.39 vs placebo 95th pct +0.28 (p 0.020); ADX14>25 & EMA50/200 sep>1 (5m): real +1.80 vs placebo 95th pct +1.83 (p 0.056); ER20>=0.3 & not squeeze: real +3.50 vs placebo 95th pct +1.41 (p 0.002); ER20>=0.25 (5m): real +2.69 vs placebo 95th pct +1.13 (p 0.002); ER20>=0.35 (5m): real +3.18 vs placebo 95th pct +1.62 (p 0.002); 15m ER20>=0.3: real -0.00 vs placebo 95th pct +1.35 (p 0.505); 1m ER20>=0.3: real -0.06 vs placebo 95th pct +1.73 (p 0.493).

Reading: the 5-min ER>=0.3 rule is a real per-trade effect in 2025-26 (placebo p 0.002) and on the live-like market M base it is +17k/wk (L6M) / +21k/wk (HOLD) / +47k (L3M) on the unscaled stack, but PRE is -7.5k and X' -0.9k (and the 70/30 N base is -7.6k L6M, -18.7k PRE): the same regime pattern EINT1 found (strong in the last year, absent before). Time-frame neighbours fail (15-min ER and 1-min ER: lift 0, stack negative), so it is a 5-min-specific effect; thresholds 0.25/0.35 behave like 0.3.

## 3. G2 - sizers (lots x 0/0.5/1/1.5/2 by tercile; risk-matched lift)

352,002 cells (1,0 continuous measures x 7 schemes x 51 units: S1 0.5/1/1.5, S2 0/1/1, S3 1/1/2, S4 0.5/1/1, S5 1/1/0.5, S1r 1.5/1/0.5, S3r 2/1/1). Eligible 7,493; selected 565. Out of sample: mean risk-matched lift L6M +0.04, HOLD +0.04, 2026 +0.05 (in selection +1.89); positive in L6M, HOLD and 2026 with per-contract >0: 159; outside MDE in L6M: 8; economic gain (unscaled, per signal) positive in L6M: 290. By scheme (L6M mean lift): S1 +0.01, S1r -0.14, S2 +0.34, S3 +0.24, S3r -0.06, S4 +0.15, S5 -0.15. 0 PASS.

## 4. G3 - combinations (COMBOS method)

37,003 combinations (pairs, triples of the top-25, k-of-6 for k=3,4,5, four-legged) over the 12 main units; members = top-40 by G1 PRE+X' lift t. 120 selected (top 10 per unit). Out of sample mean lift L6M +0.29, HOLD +0.14, 2026 +0.34; positive in all five windows: 35 of 120. Combinations do not beat the singles: what ANDing adds in-sample (+5.3) is selection, not information.

## 5. G6 - bracket by regime

240 policies (12 units x top-20 measures x tercile -> best of 16 stop/target multiples); fitted on PRE+X' with a cross-fit (fit on one, test on the other) selection: 1 of 240 passes (ENG6 | 15-min Hurst(200)). Its recent look (gain per trade vs the booked bracket, market entry; pts): 

| cell | basis | Y26 | L3M | L6M | HOLD | PRE | X |
|---|---|---|---|---|---|---|---|
| ENG6|15m.hurst200 | M | -0.22 | 0.09 | 0.32 | 0.25 | 1.39 | 1.01 |
| ENG6|15m.hurst200 | N | -0.55 | -0.16 | 0.08 | 0.00 | 1.23 | 0.90 |

Unconditionally the best single bracket in PRE+X' is stop x1.0 / target x1.5 (+0.15 ALL10, +0.27 ENG6 pts/trade), i.e. brackets are still ~dead; conditioned on trend terciles the cross-fit gains are not positive in both halves for 239 of 240 policies. Brackets by regime: DEAD.

## 6. G7 - mirror and regime switch (preferred side per book fixed on PRE+X'; 18 registered cells)

V1 = keep only the preferred tercile of the regime measure (trend books high ADX/ER, chop-liking books the low tercile), V2 = skip only the non-preferred tercile, ALLTREND = every book takes the trend side. Lift = kept minus all (pts per planned lot, E_73 N, all 10 books pooled); stack = exact lock engine (6 engine books) delta in k$/wk vs the stack as it is.

| cell | Y26 | L6M | HOLD | PRE | X | keep | stk L6M | stk HOLD | stk PRE | stk X | stk MDE L6M | stk(mktM) L6M | stk(mktM) HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 15m.adx14|ALLTREND | -3.41 | 0.26 | 0.44 | 0.66 | 0.66 | 0.68 | -24.76 | -20.28 | -8.26 | -3.86 | 50.04 | -11.19 | -5.50 |
| 15m.adx14|V1 | -5.43 | 0.59 | 0.79 | 2.07 | -0.26 | 0.36 | -40.41 | -34.08 | -22.84 | -21.38 | 66.16 | -10.11 | -2.78 |
| 15m.adx14|V2 | -3.46 | 0.27 | 0.44 | 0.73 | 0.55 | 0.68 | -24.76 | -20.28 | -8.26 | -3.86 | 50.04 | -11.19 | -5.50 |
| 15m.er20|ALLTREND | -1.05 | -0.37 | -0.42 | -0.10 | -0.42 | 0.67 | -20.32 | -15.37 | -23.91 | -10.68 | 36.19 | -8.31 | -3.21 |
| 15m.er20|V1 | -4.15 | -0.23 | 0.05 | 1.94 | 0.43 | 0.34 | -34.97 | -31.05 | -17.30 | -13.44 | 54.06 | -4.12 | 1.06 |
| 15m.er20|V2 | -0.67 | -0.02 | -0.03 | 0.03 | 0.36 | 0.66 | -25.81 | -24.24 | -15.58 | -2.14 | 33.37 | -9.83 | -7.53 |
| 1h.adx14|ALLTREND | -0.71 | 0.18 | 0.08 | -0.31 | -0.23 | 0.68 | -21.77 | -19.82 | -25.88 | -12.31 | 57.02 | -5.84 | -2.51 |
| 1h.adx14|V1 | 0.83 | -0.15 | -0.15 | 0.69 | 1.44 | 0.35 | -53.81 | -45.53 | -31.55 | -9.74 | 53.41 | -20.03 | -11.49 |
| 1h.adx14|V2 | 0.28 | 0.01 | -0.10 | 0.17 | -0.31 | 0.64 | -33.83 | -30.61 | -19.63 | -17.12 | 41.42 | -13.85 | -12.07 |
| 5m.adx14|ALLTREND | -2.60 | 0.48 | 0.67 | 0.98 | 0.61 | 0.66 | -14.54 | -10.20 | -8.47 | 4.40 | 55.44 | -3.48 | 0.26 |
| 5m.adx14|V1 | 0.75 | 2.23 | 2.27 | 2.78 | 1.52 | 0.32 | -12.97 | -10.49 | -18.55 | -3.47 | 71.35 | 14.16 | 16.23 |
| 5m.adx14|V2 | -2.60 | 0.48 | 0.67 | 0.98 | 0.61 | 0.66 | -14.54 | -10.20 | -8.47 | 4.40 | 55.44 | -3.48 | 0.26 |
| 5m.chop14|ALLTREND | 2.36 | 1.51 | 1.47 | -0.14 | -0.14 | 0.65 | -1.81 | 1.60 | -13.53 | -16.33 | 46.55 | 11.34 | 13.77 |
| 5m.chop14|V1 | -1.47 | -0.09 | -0.49 | 0.73 | 0.87 | 0.33 | -37.11 | -37.15 | -38.43 | -9.45 | 50.59 | -6.88 | -7.06 |
| 5m.chop14|V2 | 1.14 | 0.12 | 0.03 | 0.48 | 0.04 | 0.68 | -17.44 | -15.37 | 0.64 | -15.39 | 50.13 | -2.96 | -1.52 |
| 5m.er20|ALLTREND | 0.10 | 1.02 | 0.89 | 0.24 | 0.51 | 0.66 | 5.55 | 2.12 | -15.74 | 1.28 | 46.85 | 13.63 | 11.11 |
| 5m.er20|V1 | 2.91 | 2.15 | 2.20 | 1.54 | 1.28 | 0.32 | -18.09 | -10.83 | -23.99 | -8.41 | 50.05 | 11.62 | 17.51 |
| 5m.er20|V2 | 0.52 | 0.75 | 0.65 | 0.44 | 0.31 | 0.66 | -9.56 | -8.64 | -15.85 | -2.85 | 44.97 | -0.92 | 0.19 |

Preferences fixed on PRE+X' (books that PREFER THE CHOP SIDE, per regime measure): 5-min ADX14 none; 15-min ADX14 MA; 5-min ER20 HM, MA; 15-min ER20 SM, PB, WT, MA; 5-min Chop14 KB, HM, PB, DN, ST, MA (the chop-index sign is noisy); 1-hour ADX14 KB, SM, HM, MV, WT, MA. The preference changes with the measure and timeframe for almost every book (MV prefers chop only on the 1-hour ADX), so there is no stable 'fade book' to switch on in chop among these ten; MV (the mean-reversion cell) is NOT a chop book on these measures. Reading the table: 5m.adx14 and 5m.er20 V1 (keep only the trend tercile) raise the quality of the kept trades by +2.2 pts in L6M and are positive in all five windows (Y26 +0.75/+2.9, PRE +2.8/+1.5, X' +1.5/+1.3), but keep only 32% of the signals, so the unscaled lock-stack is -13k/-18k per week in L6M on the N base (MDE ~50-70k) and PRE -18.6k/-24k; on the live-like market-M base they are +14.2k/+11.6k (L6M) and +16.2k/+17.5k (HOLD), inside MDE. The regime-switch stack (trend books on in trend, fade books on in chop) therefore degenerates into 'trend gate for everyone' and does not beat the stack as it is.

### 2d. By session (ENG6, per contract of final lots, E_73 N)

| rule | session | keep L6M | tpw kept | pc Y26 | pc L6M | MDE | pc HOLD | pc PRE | pc X' |
|---|---|---|---|---|---|---|---|---|---|
| 5m ER20>=0.3 | ALL | 0.37 | 87.18 | 3.54 | 3.30 | 2.75 | 3.16 | 1.20 | 0.08 |
| 5m ER20>=0.3 | asia | 0.40 | 25.54 | 5.30 | 6.42 | 5.60 | 6.57 | 1.34 | 0.44 |
| 5m ER20>=0.3 | london | 0.41 | 20.14 | 0.31 | 1.25 | 5.09 | 1.28 | -1.54 | -0.05 |
| 5m ER20>=0.3 | pre | 0.40 | 4.75 | -8.60 | -0.63 | 12.70 | 0.11 | -0.04 | -3.54 |
| 5m ER20>=0.3 | nyam | 0.32 | 21.82 | 2.95 | 3.13 | 5.80 | 2.05 | 4.16 | -1.37 |
| 5m ER20>=0.3 | nypm | 0.35 | 14.71 | 9.48 | 2.28 | 5.90 | 2.53 | 1.80 | 2.28 |
| 5m not squeeze | ALL | 0.89 | 210.00 | 0.57 | 0.60 | 1.02 | 0.50 | 0.54 | 0.47 |
| 5m not squeeze | asia | 0.89 | 57.29 | 1.64 | 1.27 | 1.38 | 1.48 | 1.12 | 0.25 |
| 5m not squeeze | london | 0.92 | 45.61 | -1.32 | -0.68 | 1.11 | -0.94 | -0.06 | -0.41 |
| 5m not squeeze | pre | 0.88 | 10.36 | -4.91 | -0.88 | 3.95 | -1.51 | 0.08 | 0.42 |
| 5m not squeeze | nyam | 0.85 | 58.39 | 1.65 | 0.78 | 2.08 | 0.59 | 0.81 | 0.28 |
| 5m not squeeze | nypm | 0.89 | 37.96 | 1.35 | 1.15 | 1.65 | 1.00 | 0.30 | 1.50 |

## 7. G4 - the learned walk-forward gate (LightGBM on all 1,219 sided measures + book/session/clock; weekly refit; 3/6/12-month windows + ensemble)

Fitted only on trades CLOSED before each Monday refit (first test week 2023-07; 12m model expanding until it has 12 months). Regression target E_73 N pts per planned lot; classifier P(target). Policies use thresholds from the model's own past out-of-sample predictions. 20 pre-registered cells, one look, no selection. Lift = risk-matched mean(m*pts)/mean(m) minus the unfiltered mean (pts per planned lot).

| cell | Y26 | L3M | L6M | HOLD | PRE | X | MDE L6M | per contract L6M | econ L6M | market-base L6M |
|---|---|---|---|---|---|---|---|---|---|---|
| 12m|P1_skipBot33 | 0.83 | 0.81 | 0.27 | 0.29 | -0.06 | -0.74 | 1.36 | 0.27 | -0.40 | 0.29 |
| 12m|P2_skipBot20 | -0.00 | 0.17 | -0.40 | -0.34 | 0.23 | 0.17 | 0.88 | -0.40 | -0.65 | -0.43 |
| 12m|P3_size.5/1/1.5 | 0.32 | 0.27 | 0.23 | 0.18 | 0.04 | -0.34 | 0.86 | 0.23 | 0.70 | 0.22 |
| 12m|P4_size0/1/2 | 0.58 | 0.47 | 0.42 | 0.33 | 0.08 | -0.65 | 1.53 | 0.42 | 1.40 | 0.39 |
| 12m|P5_halfBot33 | 0.38 | 0.37 | 0.12 | 0.13 | -0.02 | -0.31 | 0.61 | 0.12 | -0.20 | 0.13 |
| 3m|P1_skipBot33 | 0.11 | -0.65 | -1.22 | -1.21 | -0.04 | -0.51 | 2.22 | -1.22 | -1.74 | -1.28 |
| 3m|P2_skipBot20 | 0.97 | -0.04 | -0.52 | -0.44 | 0.08 | -0.09 | 1.22 | -0.52 | -0.88 | -0.55 |
| 3m|P3_size.5/1/1.5 | -0.74 | -0.68 | -1.00 | -1.01 | 0.09 | -0.02 | 1.55 | -1.00 | -0.89 | -1.06 |
| 3m|P4_size0/1/2 | -1.47 | -1.27 | -1.91 | -1.96 | 0.18 | -0.04 | 2.98 | -1.91 | -1.77 | -2.02 |
| 3m|P5_halfBot33 | 0.05 | -0.29 | -0.52 | -0.51 | -0.02 | -0.21 | 0.94 | -0.52 | -0.87 | -0.54 |
| 6m|P1_skipBot33 | 0.60 | -1.78 | -1.42 | -1.32 | 0.61 | -0.62 | 2.11 | -1.42 | -1.82 | -1.46 |
| 6m|P2_skipBot20 | -0.39 | -1.18 | -0.90 | -0.89 | 0.12 | -0.18 | 1.30 | -0.90 | -1.15 | -0.92 |
| 6m|P3_size.5/1/1.5 | -0.22 | -1.01 | -0.74 | -0.77 | 0.17 | -0.06 | 1.14 | -0.74 | -0.50 | -0.77 |
| 6m|P4_size0/1/2 | -0.39 | -1.85 | -1.36 | -1.43 | 0.33 | -0.12 | 2.12 | -1.36 | -1.00 | -1.41 |
| 6m|P5_halfBot33 | 0.27 | -0.78 | -0.63 | -0.57 | 0.25 | -0.26 | 0.92 | -0.63 | -0.91 | -0.64 |
| ENS|P1_skipBot33 | 0.33 | -0.64 | -1.19 | -1.13 | 0.35 | -0.31 | 2.10 | -1.19 | -1.61 | -1.25 |
| ENS|P2_skipBot20 | 0.50 | -0.08 | -0.43 | -0.38 | 0.21 | -0.33 | 1.16 | -0.43 | -0.70 | -0.45 |
| ENS|P3_size.5/1/1.5 | -0.29 | -0.70 | -0.94 | -0.98 | 0.27 | -0.05 | 1.39 | -0.94 | -0.70 | -1.01 |
| ENS|P4_size0/1/2 | -0.54 | -1.27 | -1.72 | -1.82 | 0.52 | -0.10 | 2.56 | -1.72 | -1.39 | -1.85 |
| ENS|P5_halfBot33 | 0.15 | -0.29 | -0.53 | -0.49 | 0.15 | -0.13 | 0.92 | -0.53 | -0.80 | -0.56 |

Only the 12-month model is >= 0 in L6M/HOLD/2026 (+0.1 to +0.8 pts, far inside the MDE of ~1.5-2) and it is negative in X'; the 3-month, 6-month and ensemble models are -0.4 to -1.9 pts in L6M and HOLD. Information validity (out-of-sample rank IC of the predicted pts with the realised pts, day-clustered t):

| model | Y26 | L3M | L6M | HOLD | PRE | X |
|---|---|---|---|---|---|---|
| 12m | -0.01 | 0.00 | -0.01 | -0.00 | 0.01 | -0.01 |
| 3m | -0.04 | -0.03 | -0.05 | -0.05 | 0.01 | 0.01 |
| 6m | -0.04 | -0.04 | -0.04 | -0.04 | 0.02 | -0.01 |
| ENS | -0.04 | -0.04 | -0.05 | -0.05 | 0.02 | -0.01 |

t (day-clustered):

| model | Y26 | L3M | L6M | HOLD | PRE | X |
|---|---|---|---|---|---|---|
| 12m | -0.47 | 0.03 | -0.25 | -0.23 | 0.66 | -0.58 |
| 3m | -1.06 | -1.42 | -2.75 | -2.61 | 1.08 | 0.19 |
| 6m | -1.67 | -2.31 | -2.47 | -2.40 | 1.26 | -0.23 |
| ENS | -1.35 | -1.94 | -2.82 | -2.69 | 1.42 | -0.22 |

The ensemble's IC is +0.02 in PRE (t 1.4) and -0.05 in L6M (t -2.8): the learned relationship INVERTED in 2025-26. Calibration of P(target): Brier Y26 0.2516 vs unconditional 0.2475, L3M 0.2520 vs unconditional 0.2493, L6M 0.2547 vs unconditional 0.2488, HOLD 0.2550 vs unconditional 0.2494, PRE 0.2523 vs unconditional 0.2496, X 0.2571 vs unconditional 0.2499 - worse than the unconditional rate in every window, i.e. no skill.

Shuffled-feature placebo (10 draws, every feature permuted within book-month, 3-month window, same pipeline): real policy lift vs the placebo draws (rank = share of draws >= real; 1.0 means the real model is BELOW every placebo):

| policy_win | Unnamed: 1 | real | placebo_mean | placebo_max | n | rank |
|---|---|---|---|---|---|---|
| P1_skipBot33 | L6M | -1.22 | -0.25 | 0.43 | 10.00 | 1.00 |
| P1_skipBot33 | HOLD | -1.21 | -0.31 | 0.29 | 10.00 | 1.00 |
| P1_skipBot33 | Y26 | 0.11 | 0.02 | 1.42 | 10.00 | 0.64 |
| P1_skipBot33 | PRE | -0.04 | 0.02 | 0.24 | 10.00 | 0.82 |
| P1_skipBot33 | X | -0.51 | -0.09 | 0.34 | 10.00 | 0.91 |
| P3_size.5/1/1.5 | L6M | -1.00 | -0.22 | 0.15 | 10.00 | 1.00 |
| P3_size.5/1/1.5 | HOLD | -1.01 | -0.27 | 0.09 | 10.00 | 1.00 |
| P3_size.5/1/1.5 | Y26 | -0.74 | -0.03 | 0.62 | 10.00 | 0.91 |
| P3_size.5/1/1.5 | PRE | 0.09 | -0.03 | 0.08 | 10.00 | 0.09 |
| P3_size.5/1/1.5 | X | -0.02 | -0.10 | 0.38 | 10.00 | 0.36 |
| P4_size0/1/2 | L6M | -1.91 | -0.40 | 0.27 | 10.00 | 1.00 |
| P4_size0/1/2 | HOLD | -1.96 | -0.51 | 0.17 | 10.00 | 1.00 |
| P4_size0/1/2 | Y26 | -1.47 | -0.06 | 1.17 | 10.00 | 0.91 |
| P4_size0/1/2 | PRE | 0.18 | -0.06 | 0.16 | 10.00 | 0.09 |
| P4_size0/1/2 | X | -0.04 | -0.20 | 0.72 | 10.00 | 0.36 |

The real learned gate does WORSE out of sample than a model fed shuffled features (L6M -1.2 vs -0.25 mean): it has learned PRE/X' structure that reversed. Distillation (best single and best two-feature rule fitted on PRE, mean pts of the fired trades in L6M; compare with the unconditional L6M mean of +3.2/trade on E_73 N): 

| k | rule | fit_mean | fit_n | eval_mean | eval_n | n_rules_searched |
|---|---|---|---|---|---|---|
| 1 | on_range_atrd > 0.5335 | 5.02 | 8424 | 3.24 | 4031 | 600 |
| 2 | 1h.lr_r220 > 0.5936 AND prev_er_rth < 0.2077 | 7.71 | 6005 | 2.53 | 2553 | 705 |

Feature importance and its drift by quarter (gain share of the 3-month model, top 8; overlap_prev = share of the top 8 that stays in the top 8 of the previous quarter): the top features turn over almost completely each quarter (mean overlap 0.29), the signature of a non-stationary relationship (full table out/trendgate/g4/importance_drift.csv). Latest quarter (2026Q1, 3m): 4-hour EMA ribbon expansion (0.014), 1-hour EMA ribbon expansion (0.011), ret_YM_1d (0.010), 30-min ATR(14) vs its 50-bar median (0.010), 15-min Kaufman efficiency ratio(50) (0.009), vr_q30_W1380 (0.009), daily Supertrend(10,3) signed age (0.008), vwap_dist_pts_eth (0.008).

## 8. G5 - walk-forward re-selection chain of the top-10 gates (the adaptive gate the user would run tonight)

Each calendar month from 2023-10: all ~8.4k G1 cells of the unit are re-ranked on the trailing 26 closed weeks (lift t, keep 30-97%, lift>0); the top-10 vote (take if >=6 keep), the top-3 majority and the top-1 apply to the NEXT month's signals. Lift per contract (kept vs unfiltered, over the months the chain covers), E_73 N:

| unit | chain | Y26 | L3M | L6M | HOLD | PRE | X | MDE L6M | keep L6M | tpw kept | econ L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL10 | top1 | 0.76 | 0.27 | 0.43 | 0.18 | 0.33 | -2.11 | 1.84 | 0.70 | 244.82 | -0.66 |
| ALL10 | top10v6 | -0.25 | 0.80 | 0.81 | 0.62 | -0.39 | -0.83 | 1.82 | 0.68 | 237.14 | -0.49 |
| ALL10 | top3 | 0.24 | 0.57 | 0.52 | 0.37 | 0.48 | 0.38 | 1.80 | 0.71 | 248.43 | -0.56 |
| ENG6 | top1 | 0.49 | 0.78 | 0.71 | 0.57 | 0.17 | -1.59 | 1.81 | 0.78 | 185.18 | 0.02 |
| ENG6 | top10v6 | 4.61 | 1.68 | 0.67 | 0.47 | -0.24 | -1.56 | 2.11 | 0.65 | 155.18 | -0.41 |
| ENG6 | top3 | 3.53 | 1.58 | 1.08 | 0.84 | -0.51 | 0.47 | 1.98 | 0.67 | 159.93 | -0.07 |
| HM | top1 | 5.65 | 1.76 | -1.67 | -1.06 | 1.15 | 1.51 | 5.36 | 0.61 | 19.89 | -2.70 |
| HM | top10v6 | 0.43 | -3.47 | -5.74 | -4.15 | 0.07 | -4.60 | 5.83 | 0.50 | 16.18 | -5.03 |
| HM | top3 | -4.72 | -2.60 | -4.05 | -2.86 | 1.54 | -1.64 | 5.08 | 0.60 | 19.32 | -4.15 |
| KB | top1 | 3.06 | 2.19 | 1.26 | 0.84 | -0.64 | 0.23 | 3.97 | 0.68 | 30.71 | 0.44 |
| KB | top10v6 | 2.13 | 2.35 | 0.86 | 0.64 | -0.02 | -0.43 | 4.12 | 0.52 | 23.18 | -0.20 |
| KB | top3 | 9.65 | 3.60 | 2.40 | 1.45 | -0.43 | 0.75 | 4.29 | 0.50 | 22.64 | 0.55 |
| PE | top1 | 0.89 | 1.19 | 1.49 | 1.38 | -0.10 | 2.47 | 1.87 | 0.81 | 34.46 | 1.06 |
| PE | top10v6 | 2.53 | 1.67 | 1.42 | 0.95 | -0.12 | 1.24 | 2.18 | 0.81 | 34.50 | 1.00 |
| PE | top3 | -0.04 | 0.34 | 1.20 | 0.62 | 0.15 | 0.33 | 2.07 | 0.84 | 35.93 | 0.89 |
| SM | top1 | -3.84 | -0.74 | -0.51 | -0.41 | -0.77 | 2.26 | 5.32 | 0.74 | 8.59 | -1.22 |
| SM | top10v6 | 3.22 | -0.17 | 1.50 | 0.70 | 1.18 | -0.91 | 5.56 | 0.61 | 7.15 | -0.33 |
| SM | top3 | -5.69 | -1.71 | 0.33 | 0.08 | 0.08 | 3.21 | 4.86 | 0.70 | 8.11 | -0.74 |
| ST | top1 | 0.40 | 0.96 | 0.98 | 0.87 | 0.62 | -1.59 | 1.55 | 0.89 | 39.79 | 0.38 |
| ST | top10v6 | -0.08 | 2.10 | 1.37 | 1.35 | -0.31 | -1.49 | 2.67 | 0.73 | 32.75 | -0.19 |
| ST | top3 | 2.69 | 1.83 | 1.62 | 1.66 | 0.10 | -2.70 | 2.23 | 0.81 | 36.39 | 0.49 |
| WT | top1 | 1.08 | -1.11 | -0.96 | -0.23 | -0.38 | -0.95 | 2.91 | 0.44 | 26.54 | -1.47 |
| WT | top10v6 | 0.43 | -1.41 | -0.78 | -0.70 | -0.09 | -1.92 | 2.92 | 0.42 | 25.43 | -1.41 |
| WT | top3 | 0.25 | -1.82 | -1.15 | -0.52 | -0.23 | -1.86 | 2.38 | 0.48 | 29.32 | -1.52 |

The pooled chains (ALL10, ENG6) add +0.4..+1.1 pts per contract in L6M (MDE ~1.8-2.1) and are ~0 or negative in PRE and X'; KB/PE/ST are +0.9..+2.4 (inside MDE), HM and WT are negative. The last re-fit (as of 2026-02-06) for each unit is out/trendgate/g5/last_refit_<unit>.csv; ENG6: 
1m.slope_e200_3 [keepTop3] t=4.3 keep 31%; 3m.rsi_run50 [keepTop3] t=4.1 keep 32%; 1m.ext_200 [keepTop3] t=4.1 keep 31%; 3m.sep_20_50 [keepTop3] t=3.9 keep 32%; large10_bias_60m [keepTop3] t=3.9 keep 35%; idx4_agree_4h [skipBot10] t=3.9 keep 95%. Top of the list is a different measure family every month (see G4 drift): the adaptive gate has no persistent content.

## 9. Controls, validity layer and deviations
* Placebos: random gates at the same keep rate (200 draws per CANDIDATE, 500 for the named rules), shuffled-day regimes (feature series rolled by 20-80%, 100 draws), time-shifted features (5-min ER at signal-60 s and signal-300 s: the 5-min ER gate lift decays smoothly 3.30 -> 3.04 -> 1.77 per contract in L6M, i.e. a persistent-regime effect, not a last-bar artefact; 'not squeeze' 0.60 -> 0.58 -> 0.57), shuffled-feature runs of the learned gate (10 draws, prereg said 20: machine load, logged). Selection-aware control: the 539 / 565 / 120 selected cells have an out-of-sample mean lift of -0.35 / +0.04 / +0.29 vs +4.8 / +1.9 / +5.3 in selection, i.e. the selection effect is what noise gives.
* Method lesson applied: every gate/sizer is reported per planned lot, per contract of final lots and on the lock-engine stack, with trades/week and kept vs skipped P&L; the equal-risk frame (kept lots x 1/keep) is labelled STRUCTURE. The headline pattern: trend gates raise the quality of the kept trades (+1..+3 pts) but remove 60-70% of the signals, and the unscaled lock-stack loses 10-40k/wk; the risk-matched stack is inside its MDE and changes sign between windows.
* Bases: E_73 and E_MKT on N, M and LIVE-CAL (LIVE-CAL = N with the stop cost 2.45 instead of 1.01: stop exits -1.44 x final lots; an approximation, no live fill model). The lock-engine base on the market-at-signal M basis reproduces the reported stack (L6M +18.8k, HOLD +8.6k).
* Process disclosures (DECISIONS.md): the 14 directive-named fixed rules were evaluated after the map (addendum 1); G4 placebo 10 draws; HMM states separate mostly by variance (means ~0), so 'trend-up/trend-down' HMM probabilities are weak; swing/BOS/CHoCH, Wyckoff and Ehlers mode are simplified implementations; VPIN is on minute buckets; hurst/DFA/entropy are on 1-min and 5-min returns.
