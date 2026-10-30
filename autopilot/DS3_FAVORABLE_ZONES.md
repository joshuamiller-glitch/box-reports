# DS3_FAVORABLE_ZONES - T-FAVORABLE-ZONES section B: the rules (FZ-1, 2026-10-30)

Research only. Prereg `autopilot/FZ_B_prereg.md` sha256 cf8f54cc... (+ B3 fallback and B8 addendum in DECISIONS.md); every group's selection file (PRE+X' only) was hashed in DECISIONS.md before its single recent look. Windows capped 20260206, UNTOUCHED never read, masks own (L6M 20250801.., HOLD 20250701.., 2026 20260101.., PRE 20240201..20250630, X' 20230401..20240131, L3M view-only). Location store = NTZ-1 poi_store (imported).

## 0. How to read this report (units)
* Bases: **M0** market at the signal, **S73** the 70/30 plain 3-pt dip split (the floor), **W0** pure wait (full lot at the 3-pt dip). Fill bases: **N** (no target-fill correction; primary), **M** (measured), **L** (LIVE-CAL: stop-class exits cost 2.45 instead of 1.01).
* Every take-only row: keep = share of signals entered; tpw = entered trades per week; kept / skipped = mean pts per planned lot of the entered / skipped signals (L6M, N); **add_pl** = kept mean minus the mean of ALL signals of the same base = the gain per entered trade (95% CI, week-clustered; MDE = 2.8 SE); **add_pc** = the same in pts per CONTRACT of final position; M, LIVE = add_pl on those bases; gain_wk = total change in planned-lot pts per week (entered sum minus all-signals sum) - negative when the skipped signals were worth taking; stackD = lock-engine stack $/wk minus the same base without the rule (L6M, HOLD), skipped signals removed from the engine; plc = rank of the real L6M add among 200 random fire-rate placebo draws (within book x session x week; 1/201 best); RW = survives the Romano-Wolf stepdown over the group's selected cells (L6M).
* A rule is **trusted** only if it holds in planned-lot AND contract units AND on the stack (CF-B lesson). Tiers: CONFIRMED = L6M add>0 in both units, HOLD>0, M and LIVE>0, 95% CI above 0, placebo p<=.05, RW survivor, stack not below the floor in L6M and HOLD; LEAD = those except the stack gate; CANDIDATE-RECENT = positive in L6M/HOLD/M/LIVE and (placebo or RW or CI above 0); SIGN-ONLY = positive sign in L6M and HOLD only (inside the noise); DEAD / BEST-AVAILABLE-NEGATIVE otherwise. Sizing/stop/reserve rules are STRUCTURE unless they beat their random-level placebo.

## 1. TAKE ONLY when the location is favourable (B1)
### Base M0: group validity over the 100 pooled-selected cells (L6M): White RC p 0.532, cumulative-adjusted p 1.00, Romano-Wolf survivors 0, PBO 0.51
#### M0: pooled top-12 of 100 (ranked on PRE+X' z)
Selected cells: 100; mean add per entered trade (N, pts/planned lot): PRE 2.15 | X' 4.32 | **L6M -0.09** | HOLD -0.31 | 2026 -0.62 | L3M(view) 0.02; share of cells with L6M add>0: 62%; mean keep rate L6M 29%; mean total change gain_wk L6M -788 planned-lot pts/week.

| location | keep | tpw | n | kept | skipped | add_pl_L6M | MDE | add_pc | M | LIVE | PRE | Xp | HOLD | Y26 | gain_wk | stackD_L6M | stackD_HOLD | plc | RW | tier | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| any ORB Lx1 30m behind <= 20 pts | 3% | 9.6 | 268 | 6.46 | 3.15 | 3.21 [-2.75,9.18] | 8.52 | 3.21 | 3.02 | 3.24 | 0.73 | 11.00 | -1.07 | 3.72 | -1067 | -52163 | -43705 | 93/201 | N | DEAD | HOLD+,placebo,RW,stack,CI>0 |
| mit ORB Lx1 30m behind <= 20 pts | 3% | 9.6 | 268 | 6.46 | 3.15 | 3.21 [-2.75,9.18] | 8.52 | 3.21 | 3.02 | 3.24 | 0.73 | 11.00 | -1.07 | 3.72 | -1067 | -52163 | -43705 | 113/201 | N | DEAD | HOLD+,placebo,RW,stack,CI>0 |
| book flag=dflip10 | 10% | 34.2 | 958 | 4.42 | 3.12 | 1.18 [-2.73,5.08] | 5.58 | 1.18 | 1.16 | 1.20 | 3.30 | 3.30 | 1.73 | -8.07 | -977 | -53652 | -41850 | 78/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| fresh ARR iplFVG 45s behind <= 5 pts | 6% | 22.5 | 631 | 4.38 | 3.17 | 1.14 [-3.51,5.78] | 6.64 | 1.14 | 1.14 | 1.16 | 2.84 | 7.97 | -0.45 | 2.05 | -1030 | -50331 | -42473 | 66/201 | N | DEAD | HOLD+,placebo,RW,stack,CI>0 |
| PRF-class POI behind <= 10 AND book defS | 20% | 71.2 | 1995 | 3.92 | 3.07 | 0.67 [-1.24,2.59] | 2.74 | 0.67 | 0.65 | 0.69 | 2.54 | 1.00 | -0.09 | 3.59 | -850 | -34519 | -32408 | 70/201 | N | DEAD | HOLD+,placebo,RW,stack,CI>0 |
| mit SWG f7H 1m behind <= 10 pts | 70% | 242.3 | 6785 | 3.57 | 2.50 | 0.33 [-0.73,1.39] | 1.52 | 0.33 | 0.33 | 0.34 | 0.50 | 1.75 | 0.32 | -0.69 | -263 | -24340 | -17085 | 6/201 | N | CANDIDATE-RECENT | RW,stack,CI>0 |
| mit FIB ote79_up 1h behind <= 5 pts | 1% | 4.0 | 113 | -1.85 | 3.30 | -5.10 [-15.20,5.00] | 14.43 | -5.10 | -4.84 | -5.15 | 9.19 | 7.80 | -3.40 | -25.05 | -1136 | -61585 | -48251 | 156/201 | N | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| any FIB ote79_up 1h behind <= 5 pts | 1% | 4.2 | 117 | -0.78 | 3.29 | -4.03 [-13.96,5.91] | 14.19 | -4.03 | -3.81 | -4.07 | 9.86 | 6.70 | -2.51 | -23.14 | -1132 | -61593 | -48258 | 144/201 | N | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| FIB-class POI behind <= 5 AND book defS | 18% | 62.2 | 1741 | 5.03 | 2.86 | 1.78 [-0.76,4.33] | 3.63 | 1.78 | 1.72 | 1.82 | 2.49 | 0.31 | 1.03 | 4.88 | -816 | -35240 | -31057 | 58/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| any SWG f7H 1m behind <= 10 pts | 70% | 244.2 | 6837 | 3.54 | 2.55 | 0.30 [-0.74,1.33] | 1.48 | 0.30 | 0.30 | 0.31 | 0.52 | 1.48 | 0.31 | -0.71 | -264 | -24690 | -16916 | 11/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| SWG-class POI behind <= 2 AND book defS | 24% | 82.2 | 2303 | 3.84 | 3.06 | 0.60 [-1.14,2.33] | 2.48 | 0.60 | 0.58 | 0.61 | 1.86 | 1.70 | 0.06 | 1.52 | -813 | -40193 | -36302 | 98/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| BOS-class POI behind <= 2 AND book defS | 12% | 41.0 | 1148 | 3.78 | 3.17 | 0.54 [-3.09,4.17] | 5.19 | 0.54 | 0.51 | 0.56 | 2.58 | 3.60 | -0.84 | -1.30 | -974 | -53144 | -48583 | 84/201 | N | DEAD | HOLD+,placebo,RW,stack,CI>0 |

#### M0: per-book top-3 (rule applied in that book only; PRE+X'-ranked per book; stack in the per-book engine rows below)

| book | location | keep | tpw | n | kept | skipped | add_pl_L6M | MDE | add_pc | PRE | Xp | HOLD | Y26 | gain_wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ST | any MAS bb_mid 4h behind <= 20 pts | 2% | 1.1 | 30 | -2.50 | 4.06 | -6.40 [-26.66,13.85] | 28.94 | -6.40 | 13.57 | 12.80 | -3.73 | 8.05 | -178 |
| ST | fresh ARR iFVG 45s behind <= 20 pts | 39% | 17.5 | 490 | 4.76 | 3.35 | 0.86 [-2.56,4.27] | 4.88 | 0.86 | 3.28 | 2.28 | 0.53 | -0.34 | -92 |
| ST | mit any CRT-class POI behind <= 2 pts | 6% | 2.8 | 77 | 7.46 | 3.67 | 3.56 [-7.47,14.60] | 15.77 | 3.56 | 6.25 | 14.28 | 5.42 | 2.21 | -154 |
| HM | any ARR OB 10m behind <= 2 pts | 14% | 4.5 | 127 | 3.25 | 4.98 | -1.49 [-10.67,7.70] | 13.12 | -1.49 | 7.55 | 6.71 | -1.03 | 2.35 | -139 |
| HM | mit ARR OB 10m behind <= 2 pts | 14% | 4.5 | 127 | 3.25 | 4.98 | -1.49 [-10.67,7.70] | 13.12 | -1.49 | 7.55 | 6.71 | -1.03 | 2.35 | -139 |
| HM | mit ARR OB 10m behind <= 0 pts (in-zone) | 13% | 4.1 | 115 | 5.77 | 4.59 | 1.03 [-9.37,11.44] | 14.86 | 1.03 | 8.07 | 5.18 | 0.64 | 10.09 | -130 |
| WT | any SES pre_H prev behind <= 10 pts | 2% | 1.4 | 40 | -1.79 | 1.87 | -3.57 [-16.01,8.87] | 17.77 | -3.57 | 14.24 | 7.71 | -2.81 | 10.76 | -111 |
| WT | mit SES pre_H prev behind <= 10 pts | 2% | 1.4 | 40 | -1.79 | 1.87 | -3.57 [-16.01,8.87] | 17.77 | -3.57 | 14.24 | 7.71 | -2.81 | 10.76 | -111 |
| WT | mit SWG f3H 3m behind <= 5 pts | 56% | 34.4 | 962 | 1.08 | 2.69 | -0.70 [-1.91,0.50] | 1.72 | -0.70 | 0.09 | 3.04 | -0.49 | -2.25 | -71 |
| KB | any ORB Hx2 60m behind <= 20 pts | 3% | 1.4 | 39 | -8.47 | 1.98 | -10.13 [-24.63,4.37] | 20.72 | -10.13 | 7.12 | 30.78 | -12.27 | -9.56 | -86 |
| KB | mit ORB Hx2 60m behind <= 20 pts | 3% | 1.4 | 39 | -8.47 | 1.98 | -10.13 [-24.63,4.37] | 20.72 | -10.13 | 7.12 | 30.78 | -12.27 | -9.56 | -86 |
| KB | any WYK sow_high 15m behind <= 20 pts | 3% | 1.5 | 43 | -4.97 | 1.89 | -6.62 [-24.01,10.76] | 24.83 | -6.62 | 2.20 | 21.33 | -1.31 | -46.87 | -82 |
| SM | fresh any SWG-class POI behind <= 15 pts | 82% | 9.1 | 256 | 3.58 | -3.04 | 1.22 [-2.04,4.48] | 4.66 | 1.22 | 1.29 | 2.50 | 1.80 | -0.98 | 6 |
| SM | mit SWG f7H 2m behind <= 20 pts | 79% | 8.9 | 248 | 4.20 | -4.58 | 1.85 [-1.48,5.17] | 4.75 | 1.85 | 1.72 | 2.27 | 2.43 | 4.46 | 11 |
| SM | any SWG f7H 2m behind <= 20 pts | 79% | 8.9 | 249 | 4.43 | -5.57 | 2.07 [-1.24,5.38] | 4.73 | 2.07 | 1.53 | 2.10 | 2.80 | 4.46 | 13 |
| PE | fresh ARR iplFVG 3m behind <= 5 pts | 2% | 0.7 | 19 | 12.00 | 0.48 | 11.34 [-19.02,41.71] | 43.38 | 11.34 | 15.57 | 14.03 | 11.19 | 15.13 | -20 |
| PE | book flag=bigp1 | 11% | 4.6 | 130 | -0.42 | 0.79 | -1.08 [-12.78,10.62] | 16.72 | -1.08 | 3.55 | 10.05 | 0.63 | 10.06 | -30 |
| PE | mit SWG f7H 1m behind <= 10 pts | 66% | 28.0 | 785 | 3.20 | -4.20 | 2.53 [-0.14,5.21] | 3.82 | 2.53 | 1.11 | 2.63 | 2.75 | -0.69 | 61 |
| PB | mit SWG f5H 2m behind <= 20 pts | 76% | 23.5 | 659 | 9.65 | -1.51 | 2.67 [0.90,4.44] | 2.53 | 2.67 | 0.76 | 3.25 | 2.89 | 3.69 | 11 |
| PB | any ARR iplFVG 45s behind <= 10 pts | 92% | 28.4 | 794 | 7.36 | 2.81 | 0.38 [-0.80,1.56] | 1.68 | 0.38 | 0.70 | 2.01 | 0.64 | -0.85 | -7 |
| PB | mit PRF lvn0 sw1h behind <= 15 pts | 4% | 1.2 | 33 | 9.29 | 6.89 | 2.30 [-15.02,19.63] | 24.75 | 2.30 | 16.61 | 7.70 | 2.96 | -26.50 | -205 |
| DN | any FIB ext162 5m behind <= 20 pts | 3% | 0.8 | 21 | 19.42 | 5.83 | 13.18 [-9.02,35.39] | 31.72 | 13.18 | 15.27 | 15.90 | 6.39 | -15.77 | -142 |
| DN | any FIB ext127 5m behind <= 20 pts | 8% | 2.1 | 58 | 3.89 | 6.45 | -2.35 [-15.79,11.09] | 19.20 | -2.35 | 9.06 | 10.27 | -1.64 | -4.49 | -148 |
| DN | fresh ARR BRK_CE 3m behind <= 20 pts | 9% | 2.2 | 63 | 2.82 | 6.57 | -3.42 [-19.74,12.90] | 23.32 | -3.42 | 8.21 | 6.48 | -6.64 | -15.43 | -150 |
| MV | any PIV classic_P rth behind <= 10 pts | 2% | 0.9 | 25 | -3.17 | 2.40 | -5.45 [-28.63,17.74] | 33.12 | -5.45 | 5.24 | 35.82 | -2.26 | -13.95 | -95 |
| MV | mit PIV classic_P rth behind <= 10 pts | 2% | 0.9 | 25 | -3.17 | 2.40 | -5.45 [-28.63,17.74] | 33.12 | -5.45 | 6.00 | 35.17 | -2.26 | -13.95 | -95 |
| MV | fresh FIB ret50 5m behind <= 15 pts | 7% | 2.6 | 74 | 6.88 | 1.96 | 4.60 [-7.70,16.89] | 17.57 | 4.60 | 9.83 | 11.09 | 1.40 | 18.90 | -74 |
| MA | any ARR FVG_CE 10m behind <= 5 pts | 17% | 2.5 | 71 | 10.93 | 5.89 | 4.16 [-9.52,17.84] | 19.54 | 4.16 | 9.35 | 7.96 | 3.76 | -7.64 | -71 |
| MA | any ARR iFVG 5m behind <= 2 pts | 54% | 7.8 | 219 | 12.29 | 0.35 | 5.52 [-0.26,11.30] | 8.26 | 5.52 | 5.03 | 3.43 | 4.96 | -1.95 | -2 |
| MA | any SWG f3H 2m behind <= 15 pts | 91% | 13.2 | 369 | 6.89 | 5.62 | 0.12 [-2.23,2.47] | 3.36 | 0.12 | 1.04 | 2.03 | 0.70 | 1.43 | -8 |

### Base S73: group validity over the 100 pooled-selected cells (L6M): White RC p 0.521, cumulative-adjusted p 1.00, Romano-Wolf survivors 0, PBO 0.56
#### S73: pooled top-12 of 100 (ranked on PRE+X' z)
Selected cells: 100; mean add per entered trade (N, pts/planned lot): PRE 2.07 | X' 4.19 | **L6M -0.57** | HOLD -0.78 | 2026 -2.06 | L3M(view) -0.47; share of cells with L6M add>0: 55%; mean keep rate L6M 30%; mean total change gain_wk L6M -786 planned-lot pts/week.

| location | keep | tpw | n | kept | skipped | add_pl_L6M | MDE | add_pc | M | LIVE | PRE | Xp | HOLD | Y26 | gain_wk | stackD_L6M | stackD_HOLD | plc | RW | tier | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| any ORB Lx1 30m behind <= 20 pts | 3% | 9.6 | 268 | 5.92 | 3.18 | 2.67 [-3.39,8.72] | 8.65 | 2.67 | 2.49 | 2.68 | 0.39 | 10.17 | -1.80 | 3.54 | -1077 | -63373 | -57435 | 105/201 | N | DEAD | HOLD+,placebo,RW,stack,CI>0 |
| mit ORB Lx1 30m behind <= 20 pts | 3% | 9.6 | 268 | 5.92 | 3.18 | 2.67 [-3.39,8.72] | 8.65 | 2.67 | 2.49 | 2.68 | 0.39 | 10.17 | -1.80 | 3.54 | -1077 | -63373 | -57435 | 123/201 | N | DEAD | HOLD+,placebo,RW,stack,CI>0 |
| fresh ARR iplFVG 45s behind <= 5 pts | 6% | 22.5 | 631 | 5.14 | 3.13 | 1.88 [-3.01,6.77] | 6.98 | 1.88 | 1.85 | 1.92 | 3.02 | 7.85 | 0.10 | 1.49 | -1018 | -59604 | -54416 | 59/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| book flag=dflip10 | 10% | 34.2 | 958 | 4.26 | 3.15 | 1.00 [-3.01,5.02] | 5.74 | 1.02 | 1.00 | 1.02 | 3.14 | 3.25 | 1.52 | -8.14 | -988 | -64400 | -55170 | 98/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| mit FIB ote79_up 1h behind <= 5 pts | 1% | 4.0 | 113 | -2.92 | 3.33 | -6.18 [-16.26,3.90] | 14.40 | -6.21 | -5.85 | -6.24 | 9.57 | 8.01 | -4.25 | -26.11 | -1145 | -72640 | -61512 | 166/201 | N | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| mit SWG f7H 1m behind <= 10 pts | 70% | 242.3 | 6785 | 3.61 | 2.45 | 0.35 [-0.70,1.41] | 1.51 | 0.36 | 0.35 | 0.36 | 0.48 | 1.71 | 0.35 | -0.70 | -258 | -30076 | -24316 | 5/201 | N | CANDIDATE-RECENT | RW,stack,CI>0 |
| any FIB ote79_up 1h behind <= 5 pts | 1% | 4.2 | 117 | -1.79 | 3.32 | -5.05 [-15.01,4.92] | 14.24 | -5.06 | -4.76 | -5.09 | 10.20 | 6.79 | -3.31 | -24.04 | -1141 | -72642 | -61513 | 163/201 | N | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| PRF-class POI behind <= 10 AND book defS | 20% | 71.2 | 1995 | 4.05 | 3.05 | 0.80 [-1.15,2.74] | 2.78 | 0.81 | 0.78 | 0.82 | 2.25 | 0.80 | 0.11 | 4.24 | -845 | -41781 | -41663 | 65/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| any SWG f7H 1m behind <= 10 pts | 70% | 244.2 | 6837 | 3.58 | 2.51 | 0.32 [-0.72,1.35] | 1.48 | 0.32 | 0.32 | 0.33 | 0.49 | 1.48 | 0.34 | -0.72 | -260 | -30632 | -23549 | 10/201 | N | CANDIDATE-RECENT | RW,stack,CI>0 |
| fresh ARR iplFVG 45s behind <= 15 pts | 22% | 75.6 | 2117 | 4.38 | 2.95 | 1.12 [-1.42,3.66] | 3.63 | 1.11 | 1.10 | 1.14 | 2.08 | 1.75 | 0.68 | 1.53 | -803 | -47462 | -45601 | 82/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| BOS-class POI behind <= 2 AND book defS | 12% | 41.0 | 1148 | 4.11 | 3.14 | 0.85 [-2.62,4.33] | 4.96 | 0.86 | 0.82 | 0.87 | 2.43 | 3.49 | -0.55 | -0.58 | -965 | -62350 | -60556 | 60/201 | N | DEAD | HOLD+,placebo,RW,stack,CI>0 |
| any WYK upthrust 15m behind <= 2 pts | 1% | 4.1 | 115 | -2.12 | 3.32 | -5.38 [-15.96,5.20] | 15.12 | -5.37 | -5.10 | -5.40 | 4.82 | 12.34 | -3.18 | -14.36 | -1142 | -74504 | -61966 | 191/201 | N | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |

#### S73: per-book top-3 (rule applied in that book only; PRE+X'-ranked per book; stack in the per-book engine rows below)

| book | location | keep | tpw | n | kept | skipped | add_pl_L6M | MDE | add_pc | PRE | Xp | HOLD | Y26 | gain_wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ST | mit any CRT-class POI behind <= 2 pts | 6% | 2.8 | 77 | 8.84 | 4.07 | 4.48 [-7.18,16.14] | 16.66 | 4.69 | 6.52 | 14.53 | 6.26 | -2.06 | -171 |
| ST | any MAS bb_mid 4h behind <= 20 pts | 2% | 1.1 | 30 | -3.14 | 4.55 | -7.51 [-27.09,12.08] | 27.98 | -7.50 | 13.16 | 14.58 | -5.48 | 6.53 | -199 |
| ST | any EQL EQH_tight 1m behind <= 20 pts | 48% | 21.3 | 597 | 5.01 | 3.78 | 0.64 [-2.51,3.80] | 4.50 | 0.67 | 2.81 | 1.48 | 0.86 | -2.23 | -89 |
| HM | any ARR OB 10m behind <= 2 pts | 14% | 4.5 | 127 | 2.99 | 4.53 | -1.33 [-10.58,7.93] | 13.22 | -1.35 | 7.40 | 6.44 | -0.90 | 3.93 | -127 |
| HM | mit ARR OB 10m behind <= 2 pts | 14% | 4.5 | 127 | 2.99 | 4.53 | -1.33 [-10.58,7.93] | 13.22 | -1.35 | 7.40 | 6.44 | -0.90 | 3.93 | -127 |
| HM | mit ARR OB 10m behind <= 0 pts (in-zone) | 13% | 4.1 | 115 | 5.45 | 4.15 | 1.13 [-9.33,11.59] | 14.94 | 1.10 | 7.86 | 5.10 | 0.85 | 11.74 | -118 |
| WT | any SES pre_H prev behind <= 10 pts | 2% | 1.4 | 40 | -2.94 | 1.99 | -4.81 [-16.73,7.11] | 17.03 | -4.87 | 13.42 | 6.42 | -4.29 | 8.93 | -118 |
| WT | mit SES pre_H prev behind <= 10 pts | 2% | 1.4 | 40 | -2.94 | 1.99 | -4.81 [-16.73,7.11] | 17.03 | -4.87 | 13.42 | 6.42 | -4.29 | 8.93 | -118 |
| WT | any SES pre_H prev behind <= 15 pts | 3% | 1.9 | 54 | -1.16 | 1.97 | -3.03 [-12.11,6.05] | 12.97 | -3.06 | 9.15 | 3.29 | -1.57 | 3.05 | -116 |
| KB | any ORB Hx2 60m behind <= 20 pts | 3% | 1.4 | 39 | -8.00 | 1.63 | -9.34 [-23.86,5.19] | 20.75 | -9.19 | 6.66 | 28.67 | -11.57 | -8.95 | -71 |
| KB | mit ORB Hx2 60m behind <= 20 pts | 3% | 1.4 | 39 | -8.00 | 1.63 | -9.34 [-23.86,5.19] | 20.75 | -9.19 | 6.66 | 28.67 | -11.57 | -8.95 | -71 |
| KB | any WYK sow_high 15m behind <= 20 pts | 3% | 1.5 | 43 | -6.27 | 1.60 | -7.60 [-24.89,9.68] | 24.70 | -7.68 | 0.65 | 21.46 | -1.97 | -46.63 | -70 |
| SM | fresh any SWG-class POI behind <= 15 pts | 82% | 9.1 | 256 | 4.88 | -4.01 | 1.64 [-1.57,4.85] | 4.58 | 1.63 | 1.41 | 2.52 | 1.79 | -0.58 | 8 |
| SM | mit SWG f7H 2m behind <= 20 pts | 79% | 8.9 | 248 | 5.37 | -4.76 | 2.13 [-1.20,5.46] | 4.76 | 2.12 | 1.68 | 2.18 | 2.36 | 5.01 | 11 |
| SM | any SWG f7H 2m behind <= 20 pts | 79% | 8.9 | 249 | 5.59 | -5.76 | 2.35 [-0.96,5.66] | 4.73 | 2.35 | 1.50 | 2.01 | 2.73 | 5.01 | 13 |
| PE | fresh ARR iplFVG 3m behind <= 5 pts | 2% | 0.7 | 19 | 10.62 | 0.64 | 9.82 [-20.01,39.65] | 42.62 | 10.00 | 15.77 | 12.70 | 9.70 | 15.67 | -27 |
| PE | book flag=bigp1 | 11% | 4.6 | 130 | 0.34 | 0.86 | -0.46 [-11.67,10.76] | 16.02 | -0.45 | 3.45 | 9.12 | 1.19 | 8.96 | -33 |
| PE | HTF tf=1h on 1h | 22% | 9.2 | 258 | 3.27 | 0.12 | 2.47 [-4.98,9.91] | 10.63 | 2.48 | 5.57 | 4.07 | 2.04 | -10.71 | -4 |
| PB | mit PRF lvn0 sw1h behind <= 15 pts | 4% | 1.2 | 33 | 8.79 | 7.52 | 1.22 [-15.83,18.27] | 24.36 | 1.22 | 15.43 | 10.49 | 1.96 | -26.62 | -224 |
| PB | mit SWG f5H 2m behind <= 20 pts | 76% | 23.5 | 659 | 10.62 | -2.14 | 3.05 [1.31,4.79] | 2.49 | 3.04 | 0.67 | 3.14 | 3.22 | 4.08 | 16 |
| PB | mit ARR OB_CE 2m behind <= 5 pts | 24% | 7.4 | 207 | 18.40 | 4.17 | 10.82 [4.31,17.34] | 9.31 | 10.90 | 3.53 | 7.53 | 9.50 | 14.14 | -98 |
| DN | any FIB ext162 5m behind <= 20 pts | 3% | 0.8 | 21 | 19.20 | 5.03 | 13.74 [-8.11,35.60] | 31.23 | 13.66 | 13.80 | 15.32 | 7.03 | -14.41 | -122 |
| DN | any FIB ext127 5m behind <= 20 pts | 8% | 2.1 | 58 | 3.17 | 5.67 | -2.29 [-15.54,10.96] | 18.92 | -2.30 | 7.80 | 9.97 | -1.42 | -6.54 | -130 |
| DN | fresh ARR BRK_CE 3m behind <= 20 pts | 9% | 2.2 | 63 | 2.16 | 5.78 | -3.30 [-19.26,12.67] | 22.81 | -3.31 | 8.22 | 6.78 | -6.70 | -14.10 | -132 |
| MV | any PIV classic_P rth behind <= 10 pts | 2% | 0.9 | 25 | -4.90 | 2.46 | -7.20 [-29.65,15.26] | 32.07 | -7.27 | 4.77 | 35.09 | -3.74 | -16.08 | -97 |
| MV | mit PIV classic_P rth behind <= 10 pts | 2% | 0.9 | 25 | -4.90 | 2.46 | -7.20 [-29.65,15.26] | 32.07 | -7.27 | 5.52 | 34.39 | -3.74 | -16.08 | -97 |
| MV | any KZ kz_ny_L prev behind <= 10 pts | 1% | 0.5 | 15 | 10.87 | 2.18 | 8.57 [-25.15,42.29] | 48.17 | 8.60 | 21.53 | 0.86 | -2.56 | -65.69 | -87 |
| MA | any ARR FVG_CE 10m behind <= 5 pts | 17% | 2.5 | 71 | 10.24 | 5.30 | 4.08 [-9.49,17.64] | 19.37 | 4.08 | 10.09 | 7.28 | 3.70 | -9.07 | -64 |
| MA | any SWG f7H 2m behind <= 15 pts | 80% | 11.6 | 324 | 5.87 | 7.31 | -0.29 [-3.38,2.80] | 4.42 | -0.29 | 1.92 | 2.30 | 0.14 | -1.75 | -22 |
| MA | any SWG f7H 1m behind <= 15 pts | 88% | 12.8 | 359 | 6.82 | 1.27 | 0.65 [-1.76,3.07] | 3.45 | 0.67 | 1.18 | 2.08 | 1.01 | 1.76 | -2 |

### Base W0: group validity over the 100 pooled-selected cells (L6M): White RC p 0.481, cumulative-adjusted p 1.00, Romano-Wolf survivors 1, PBO 0.67
#### W0: pooled top-12 of 100 (ranked on PRE+X' z)
Selected cells: 100; mean add per entered trade (N, pts/planned lot): PRE 1.75 | X' 3.70 | **L6M -0.65** | HOLD -0.60 | 2026 -2.77 | L3M(view) -0.80; share of cells with L6M add>0: 56%; mean keep rate L6M 32%; mean total change gain_wk L6M -747 planned-lot pts/week.

| location | keep | tpw | n | kept | skipped | add_pl_L6M | MDE | add_pc | M | LIVE | PRE | Xp | HOLD | Y26 | gain_wk | stackD_L6M | stackD_HOLD | plc | RW | tier | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book flag=dflip10 | 10% | 34.2 | 958 | 3.77 | 3.16 | 0.55 [-3.06,4.16] | 5.15 | 0.63 | 0.57 | 0.57 | 3.15 | 2.84 | 1.05 | -8.04 | -992 | -79703 | -68981 | 114/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| fresh ARR iplFVG 45s behind <= 5 pts | 6% | 22.5 | 631 | 5.60 | 3.06 | 2.38 [-2.52,7.28] | 6.99 | 2.49 | 2.29 | 2.42 | 2.55 | 7.44 | 0.81 | 0.35 | -995 | -71868 | -64768 | 27/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| mit FIB ote79_up 1h behind <= 5 pts | 1% | 4.0 | 113 | -2.80 | 3.29 | -6.03 [-16.35,4.30] | 14.75 | -6.56 | -5.63 | -6.07 | 9.70 | 7.00 | -4.00 | -21.33 | -1133 | -86102 | -73389 | 157/201 | N | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| any FIB ote79_up 1h behind <= 5 pts | 1% | 4.2 | 117 | -1.67 | 3.28 | -4.89 [-15.16,5.37] | 14.67 | -5.30 | -4.55 | -4.93 | 10.20 | 5.65 | -3.07 | -19.60 | -1128 | -86093 | -73381 | 160/201 | N | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| fresh ARR iplFVG 45s behind <= 15 pts | 22% | 75.6 | 2117 | 4.79 | 2.79 | 1.57 [-0.71,3.85] | 3.26 | 1.63 | 1.51 | 1.60 | 1.78 | 1.92 | 1.05 | 0.87 | -759 | -53245 | -51253 | 32/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| mit SWG f7H 1m behind <= 10 pts | 70% | 242.3 | 6785 | 3.72 | 2.07 | 0.50 [-0.50,1.50] | 1.43 | 0.54 | 0.49 | 0.51 | 0.43 | 1.57 | 0.51 | -1.02 | -219 | -20749 | -14477 | 3/201 | N | CANDIDATE-RECENT | RW,stack,CI>0 |
| fresh ARR iFVG 45s behind <= 20 pts | 37% | 128.7 | 3604 | 4.03 | 2.75 | 0.81 [-1.16,2.78] | 2.81 | 0.85 | 0.76 | 0.82 | 1.43 | 1.33 | 0.52 | 2.00 | -602 | -46528 | -41849 | 61/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| fresh ARR iplFVG 45s behind <= 20 pts | 28% | 98.6 | 2761 | 4.07 | 2.89 | 0.85 [-1.00,2.69] | 2.63 | 0.87 | 0.82 | 0.86 | 1.08 | 1.97 | 0.28 | 1.24 | -720 | -50583 | -50863 | 53/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| fresh ARR iFVG 30s behind <= 15 pts | 37% | 130.0 | 3641 | 3.90 | 2.82 | 0.68 [-0.97,2.33] | 2.36 | 0.72 | 0.62 | 0.69 | 1.04 | 1.72 | 0.23 | 1.20 | -614 | -38065 | -34985 | 82/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| OTE 1h | 2% | 6.3 | 176 | -1.25 | 3.31 | -4.47 [-15.00,6.05] | 15.03 | -4.80 | -4.26 | -4.51 | 8.21 | 6.45 | -2.85 | -10.50 | -1129 | -89855 | -76675 | 180/201 | N | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| any SWG f7H 1m behind <= 10 pts | 70% | 244.2 | 6837 | 3.67 | 2.17 | 0.45 [-0.54,1.44] | 1.41 | 0.48 | 0.44 | 0.46 | 0.43 | 1.37 | 0.49 | -1.03 | -225 | -22130 | -14826 | 4/201 | N | CANDIDATE-RECENT | RW,stack,CI>0 |
| mit ARR iFVG_CE 2m behind <= 2 pts | 20% | 69.6 | 1949 | 2.27 | 3.46 | -0.95 [-3.89,2.00] | 4.21 | -1.01 | -0.90 | -0.96 | 1.65 | 2.55 | -1.17 | -7.20 | -963 | -74403 | -68415 | 86/201 | N | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |

#### W0: per-book top-3 (rule applied in that book only; PRE+X'-ranked per book; stack in the per-book engine rows below)

| book | location | keep | tpw | n | kept | skipped | add_pl_L6M | MDE | add_pc | PRE | Xp | HOLD | Y26 | gain_wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ST | any MAS bb_mid 4h behind <= 20 pts | 2% | 1.1 | 30 | -4.49 | 4.60 | -8.87 [-25.68,7.94] | 24.02 | -9.46 | 11.46 | 17.39 | -8.39 | 4.13 | -201 |
| ST | any MAS ema100 1h behind <= 20 pts | 2% | 1.1 | 30 | 7.83 | 4.30 | 3.45 [-12.75,19.64] | 23.14 | 4.38 | 10.40 | 16.79 | -1.90 | 4.58 | -188 |
| ST | mit any CRT-class POI behind <= 2 pts | 6% | 2.8 | 77 | 4.30 | 4.39 | -0.08 [-11.29,11.12] | 16.01 | 0.29 | 5.59 | 15.67 | 2.11 | -10.57 | -185 |
| HM | any PRF lvn0 sw15 behind <= 15 pts | 9% | 2.9 | 82 | -5.43 | 4.81 | -9.32 [-21.66,3.03] | 17.63 | -9.94 | 9.49 | 15.21 | -8.00 | 22.34 | -142 |
| HM | mit PRF lvn0 sw15 behind <= 15 pts | 8% | 2.5 | 70 | -3.79 | 4.53 | -7.67 [-19.82,4.48] | 17.36 | -8.23 | 10.47 | 16.84 | -7.56 | 29.99 | -136 |
| HM | any ARR OB 10m behind <= 2 pts | 14% | 4.5 | 127 | 5.02 | 3.70 | 1.14 [-6.83,9.11] | 11.39 | 1.12 | 6.75 | 6.85 | 1.30 | 5.36 | -103 |
| WT | fresh FIB ret62 15m behind <= 20 pts | 3% | 1.9 | 54 | 0.74 | 2.29 | -1.51 [-12.50,9.49] | 15.71 | -1.63 | 5.12 | 11.19 | -0.49 | 16.37 | -135 |
| WT | mit SES pre_H prev behind <= 10 pts | 2% | 1.4 | 40 | -1.55 | 2.34 | -3.80 [-13.89,6.29] | 14.42 | -4.31 | 12.57 | 2.36 | -4.39 | 3.49 | -139 |
| WT | any SES pre_H prev behind <= 10 pts | 2% | 1.4 | 40 | -1.55 | 2.34 | -3.80 [-13.89,6.29] | 14.42 | -4.31 | 12.57 | 2.36 | -4.39 | 3.49 | -139 |
| KB | mit ORB Hx2 15m behind <= 15 pts | 3% | 1.2 | 35 | -5.90 | 1.82 | -7.51 [-20.08,5.07] | 17.97 | -7.98 | 12.19 | 16.66 | -5.18 | -13.19 | -79 |
| KB | any ORB Hx2 15m behind <= 15 pts | 3% | 1.2 | 35 | -5.90 | 1.82 | -7.51 [-20.08,5.07] | 17.97 | -7.98 | 12.19 | 16.66 | -5.18 | -13.19 | -79 |
| KB | any ARR FVG_CE 30m behind <= 5 pts | 3% | 1.4 | 39 | -3.39 | 1.76 | -4.99 [-19.92,9.93] | 21.32 | -5.61 | 6.94 | 18.19 | -0.41 | -15.00 | -77 |
| SM | ADVERSE disc/prem 15m >= 0.667 | 92% | 10.3 | 289 | 4.20 | 0.85 | 0.27 [-1.57,2.10] | 2.62 | 0.25 | 1.60 | 1.87 | 0.50 | -1.58 | -1 |
| SM | mit ARR iplFVG 30m behind <= 10 pts | 33% | 3.7 | 103 | 8.02 | 1.94 | 4.08 [-7.55,15.71] | 16.61 | 4.30 | 4.30 | 7.98 | 4.84 | -9.82 | -15 |
| SM | fresh any SWG-class POI behind <= 15 pts | 82% | 9.1 | 256 | 5.69 | -3.82 | 1.76 [-1.40,4.91] | 4.51 | 1.79 | 0.51 | 2.30 | 1.77 | -0.17 | 8 |
| PE | any ARR iFVG_CE 15s behind <= 15 pts | 94% | 40.1 | 1122 | 1.31 | -8.40 | 0.59 [-0.08,1.26] | 0.96 | 0.62 | 0.64 | 0.60 | 0.64 | 0.48 | 22 |
| PE | fresh ARR iFVG_CE 1m behind <= 5 pts | 11% | 4.5 | 127 | 7.36 | -0.07 | 6.64 [-1.18,14.47] | 11.18 | 7.03 | 4.68 | 8.42 | 6.02 | 10.44 | 3 |
| PE | fresh ARR iplFVG 3m behind <= 5 pts | 2% | 0.7 | 19 | 7.10 | 0.62 | 6.37 [-21.42,34.17] | 39.71 | 7.16 | 15.61 | 8.76 | 6.29 | 15.54 | -26 |
| PB | mit WYK sos_high 15m behind <= 15 pts | 2% | 0.7 | 19 | 26.40 | 6.84 | 19.13 [-0.19,38.45] | 27.59 | 18.69 | 9.99 | 21.48 | 22.10 | -28.01 | -207 |
| PB | any WYK sos_high 15m behind <= 15 pts | 2% | 0.7 | 19 | 26.40 | 6.84 | 19.13 [-0.19,38.45] | 27.59 | 18.69 | 9.99 | 21.48 | 22.10 | -28.01 | -207 |
| PB | mit WYK sos_high 15m behind <= 20 pts | 3% | 1.0 | 27 | 28.46 | 6.59 | 21.19 [3.51,38.87] | 25.26 | 21.85 | 8.10 | 16.34 | 20.57 | -28.01 | -197 |
| DN | fresh ARR FVG 1m behind <= 10 pts | 11% | 2.8 | 78 | 0.53 | 4.97 | -3.95 [-20.02,12.12] | 22.96 | -4.26 | 7.98 | 11.29 | -3.97 | -7.95 | -111 |
| DN | fresh ARR iFVG 45s behind <= 20 pts | 30% | 7.6 | 212 | 4.20 | 4.60 | -0.28 [-7.17,6.61] | 9.85 | -0.42 | 4.01 | 4.71 | -1.17 | 15.88 | -80 |
| DN | any FIB ext162 5m behind <= 20 pts | 3% | 0.8 | 21 | 17.85 | 4.06 | 13.37 [-7.24,33.98] | 29.45 | 13.90 | 10.26 | 12.71 | 7.12 | -11.96 | -99 |
| MV | mit KZ kz_ny_L prev behind <= 10 pts | 1% | 0.5 | 15 | 8.69 | 2.59 | 6.02 [-26.50,38.53] | 46.45 | 6.51 | 19.32 | 2.18 | -3.89 | -63.81 | -103 |
| MV | any KZ kz_ny_L prev behind <= 10 pts | 1% | 0.5 | 15 | 8.69 | 2.59 | 6.02 [-26.50,38.53] | 46.45 | 6.51 | 19.32 | 2.18 | -3.89 | -63.81 | -103 |
| MV | fresh FIB ret50 5m behind <= 15 pts | 7% | 2.6 | 74 | 6.29 | 2.41 | 3.62 [-7.79,15.03] | 16.30 | 3.76 | 9.92 | 11.74 | 0.19 | 13.05 | -91 |
| MA | any SWG f7H 2m behind <= 15 pts | 80% | 11.6 | 324 | 4.66 | 5.53 | -0.18 [-3.07,2.72] | 4.14 | -0.18 | 1.82 | 1.92 | 0.19 | -2.33 | -16 |
| MA | fresh BOS BOS_dn 1m behind <= 15 pts | 8% | 1.1 | 32 | 6.83 | 4.67 | 1.99 [-13.88,17.86] | 22.67 | 2.54 | 12.26 | 18.13 | 0.35 | -30.10 | -63 |
| MA | any ARR iFVG 5m behind <= 2 pts | 54% | 7.8 | 219 | 9.40 | -0.48 | 4.57 [-0.61,9.74] | 7.39 | 5.08 | 4.71 | 3.17 | 4.55 | -5.09 | 3 |

### 1c. Drift by quarter of the top-5 pooled take-only cells (base S73, N; add per entered trade, pts per planned lot) and the walk-forward view

| location | 2023Q2 | 2023Q3 | 2023Q4 | 2024Q1 | 2024Q2 | 2024Q3 | 2024Q4 | 2025Q1 | 2025Q2 | 2025Q3 | 2025Q4 | 2026Q1 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| any ORB Lx1 30m behind <= 20 pts | 11.7 | 10.3 | 8.6 | 28.2 | -7.2 | 10.5 | 11.3 | -1.0 | -8.8 | -14.4 | -1.1 | 3.5 |
| mit ORB Lx1 30m behind <= 20 pts | 11.7 | 10.3 | 8.6 | 28.2 | -7.2 | 10.5 | 11.3 | -1.0 | -8.8 | -14.4 | -1.1 | 3.5 |
| fresh ARR iplFVG 45s behind <= 5 pts | 2.4 | 6.9 | 9.8 | 10.7 | 5.8 | 1.9 | 0.7 | -0.8 | 6.2 | -2.3 | 1.9 | 1.5 |
| book flag=dflip10 | 3.2 | 2.1 | 3.1 | 1.9 | 3.6 | 3.9 | 0.4 | 3.3 | 4.9 | 1.5 | 5.8 | -8.1 |
| mit FIB ote79_up 1h behind <= 5 pts | 5.0 | 11.3 | 7.4 | 4.2 | 9.0 | 16.4 | 2.2 | 16.9 | 5.0 | 4.8 | -4.7 | -26.1 |

### 1d. Session columns of the top-5 pooled take-only cells (S73, N; add_pl in PRE | X' | L6M; kept n in L6M)

| location | asia | london | pre | nyam | nypm | close |
|---|---|---|---|---|---|---|
| any ORB Lx1 30m behind <= 20 pts | 2.9 | 16.6 | 9.4 (n52) | 5.5 | 4.6 | -18.6 (n61) | -14.5 | 25.2 | 36.6 (n9) | 2.4 | 9.0 | 5.0 (n63) | -5.5 | 5.5 | 7.7 (n80) | -12.0 | -15.5 | 56.9 (n3) |
| mit ORB Lx1 30m behind <= 20 pts | 2.9 | 16.6 | 9.4 (n52) | 5.5 | 4.6 | -18.6 (n61) | -14.5 | 25.2 | 36.6 (n9) | 2.4 | 9.0 | 5.0 (n63) | -5.5 | 5.5 | 7.7 (n80) | -12.0 | -15.5 | 56.9 (n3) |
| fresh ARR iplFVG 45s behind <= 5 pts | 5.4 | 7.3 | -0.6 (n256) | -3.6 | 10.2 | -3.8 (n181) | 6.6 | 8.7 | 19.0 (n22) | 9.2 | 10.7 | 17.9 (n90) | 3.7 | 2.1 | -2.9 (n81) | -10.1 | -0.2 | -27.5 (n1) |
| book flag=dflip10 | 5.7 | 2.6 | -4.0 (n260) | 3.5 | -0.6 | -3.0 (n162) | -2.2 | 2.8 | 17.4 (n50) | 0.7 | 5.3 | 4.6 (n333) | 5.2 | 4.9 | 0.6 (n151) | -18.1 | -39.7 | 41.3 (n2) |
| mit FIB ote79_up 1h behind <= 5 pts | 14.2 | 0.5 | -27.2 (n21) | 22.9 | 5.3 | 11.6 (n27) | -11.2 | 43.4 | 13.4 (n6) | 4.2 | 11.4 | -10.6 (n40) | -1.9 | 6.9 | -4.9 (n19) | 73.1 |  |  (n0) |

### 1e. Latency stress (market base M0, N; the top-30 pooled cells; entry at the close of second kin+lat, stop/target fixed by the signal price, trades whose base exit falls inside the delay not entered): mean add per entered trade

| window | delay 0 s | delay 1 s | delay 3 s |
|---|---|---|---|
| HOLD | -0.7 | -1.06 | -1.02 |
| L6M | -0.29 | -0.66 | -0.62 |
| PRE | 2.4 | 2.0 | 1.93 |

Stack lines of the per-book rules (ENGINE books): see `out/fz/B1/B1_stack.parquet` (scope = book).

## 2. SIZE BY LOCATION (B2)
Multiplier a on the favourable location / b elsewhere (schemes (a,b) = (1.5,1) (2,1) (1,0.5) (1.5,0.5) (2,0.5)); candidate locations = the 142 B1-selected masks; per base the top 100 (mask, scheme) by PRE+X' equal-exposure add. **eq_add** = sum(m y)/sum(m) - mean(y): the gain per unit of exposure at EQUAL total lots (the risk-matched report); raw_wk = total change in pts/week (more lots = more risk: a pure-leverage effect shows up here, not in eq_add); lev_L6M = the stack change the same exposure change would give by scaling EVERY trade uniformly (stackD above lev = location information; stackD at or below lev = leverage only); expo = mean multiplier. STRUCTURE for the leverage part.

### Base M0: 100 selected (mask, scheme) cells; mean eq_add PRE 0.32 | X' 0.48 | **L6M 0.12** | HOLD 0.04 | 2026 0.09; share L6M>0 86%; mean raw_wk L6M -3

| location | scheme | expo | eq_add_L6M | MDE | eq_add_pc | M | LIVE | PRE | Xp | HOLD | Y26 | raw_wk | stackD_L6M | stackD_HOLD | lev_L6M | tier | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book flag=dflip10 | 2.0/0.5 | 0.65 | 0.27 [-0.62,1.16] | 1.27 | 0.27 | 0.27 | 0.27 | 0.76 | 0.74 | 0.39 | -1.87 | -337 | -26928 | -21698 | -21669 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| book flag=dflip10 | 1.5/0.5 | 0.60 | 0.19 [-0.45,0.84] | 0.92 | 0.19 | 0.19 | 0.20 | 0.55 | 0.53 | 0.28 | -1.35 | -413 | -29975 | -24441 | -24693 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| book flag=dflip10 | 1.0/0.5 | 0.55 | 0.11 [-0.24,0.46] | 0.50 | 0.11 | 0.10 | 0.11 | 0.30 | 0.29 | 0.16 | -0.74 | -489 | -26637 | -21447 | -27716 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| book flag=dflip10 | 2.0/1.0 | 1.10 | 0.11 [-0.24,0.46] | 0.50 | 0.11 | 0.10 | 0.11 | 0.30 | 0.29 | 0.16 | -0.74 | 151 | 10558 | 11137 | 6046 | SIGN-ONLY | placebo,RW,CI>0 |
| book flag=dflip10 | 1.5/1.0 | 1.05 | 0.06 [-0.13,0.24] | 0.26 | 0.06 | 0.05 | 0.06 | 0.16 | 0.15 | 0.08 | -0.39 | 76 | 7938 | 7724 | 3023 | SIGN-ONLY | placebo,RW,CI>0 |
| fresh ARR iplFVG 45s behind <= 5 pts | 2.0/0.5 | 0.60 | 0.18 [-0.57,0.94] | 1.08 | 0.18 | 0.19 | 0.19 | 0.45 | 1.56 | -0.08 | 0.31 | -416 | -28378 | -27321 | -24765 | DEAD | HOLD+,placebo,RW,stack,CI>0 |
| fresh ARR iplFVG 45s behind <= 5 pts | 1.5/0.5 | 0.56 | 0.13 [-0.40,0.66] | 0.76 | 0.13 | 0.13 | 0.13 | 0.32 | 1.11 | -0.05 | 0.22 | -466 | -30116 | -27311 | -26756 | DEAD | HOLD+,placebo,RW,stack,CI>0 |
| fresh ARR iplFVG 45s behind <= 5 pts | 1.0/0.5 | 0.53 | 0.07 [-0.21,0.35] | 0.40 | 0.07 | 0.07 | 0.07 | 0.17 | 0.60 | -0.03 | 0.11 | -515 | -25643 | -23316 | -28747 | DEAD | HOLD+,placebo,RW,stack,CI>0 |
| fresh ARR iplFVG 45s behind <= 5 pts | 2.0/1.0 | 1.06 | 0.07 [-0.21,0.35] | 0.40 | 0.07 | 0.07 | 0.07 | 0.17 | 0.60 | -0.03 | 0.11 | 99 | 2045 | 3063 | 3982 | DEAD | HOLD+,placebo,RW,CI>0 |
| fresh ARR iplFVG 45s behind <= 5 pts | 1.5/1.0 | 1.03 | 0.04 [-0.11,0.18] | 0.21 | 0.04 | 0.04 | 0.04 | 0.09 | 0.31 | -0.01 | 0.06 | 49 | -411 | 1700 | 1991 | DEAD | HOLD+,placebo,RW,stack,CI>0 |
| PRF-class POI behind <= 10 AND book defS | 2.0/0.5 | 0.81 | 0.26 [-0.47,0.98] | 1.04 | 0.26 | 0.25 | 0.26 | 0.97 | 0.37 | -0.03 | 1.41 | -146 | -11664 | -15587 | -11852 | DEAD | HOLD+,placebo,RW,stack,CI>0 |
| PRF-class POI behind <= 10 AND book defS | 1.5/0.5 | 0.70 | 0.19 [-0.36,0.75] | 0.79 | 0.19 | 0.19 | 0.20 | 0.74 | 0.28 | -0.03 | 1.08 | -285 | -19839 | -21615 | -18148 | DEAD | HOLD+,placebo,RW,stack,CI>0 |

### Base S73: 100 selected (mask, scheme) cells; mean eq_add PRE 0.27 | X' 0.54 | **L6M 0.10** | HOLD 0.05 | 2026 -0.16; share L6M>0 80%; mean raw_wk L6M 65

| location | scheme | expo | eq_add_L6M | MDE | eq_add_pc | M | LIVE | PRE | Xp | HOLD | Y26 | raw_wk | stackD_L6M | stackD_HOLD | lev_L6M | tier | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book flag=dflip10 | 2.0/0.5 | 0.65 | 0.23 [-0.69,1.14] | 1.31 | 0.23 | 0.23 | 0.23 | 0.73 | 0.72 | 0.35 | -1.88 | -348 | -35152 | -32833 | -25426 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| book flag=dflip10 | 1.5/0.5 | 0.60 | 0.16 [-0.50,0.83] | 0.94 | 0.17 | 0.16 | 0.17 | 0.53 | 0.52 | 0.25 | -1.36 | -421 | -37477 | -34383 | -28973 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| book flag=dflip10 | 1.0/0.5 | 0.55 | 0.09 [-0.27,0.45] | 0.51 | 0.09 | 0.09 | 0.09 | 0.29 | 0.28 | 0.14 | -0.74 | -494 | -35117 | -32414 | -32520 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| book flag=dflip10 | 2.0/1.0 | 1.10 | 0.09 [-0.27,0.45] | 0.51 | 0.09 | 0.09 | 0.09 | 0.29 | 0.28 | 0.14 | -0.74 | 146 | 3064 | 4196 | 7094 | SIGN-ONLY | placebo,RW,CI>0 |
| book flag=dflip10 | 1.5/1.0 | 1.05 | 0.05 [-0.14,0.24] | 0.27 | 0.05 | 0.05 | 0.05 | 0.15 | 0.15 | 0.07 | -0.39 | 73 | 3389 | 3380 | 3547 | SIGN-ONLY | placebo,RW,CI>0 |
| fresh ARR iplFVG 45s behind <= 5 pts | 2.0/0.5 | 0.60 | 0.31 [-0.49,1.10] | 1.14 | 0.31 | 0.30 | 0.31 | 0.48 | 1.53 | 0.02 | 0.22 | -393 | -37313 | -37925 | -29058 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| fresh ARR iplFVG 45s behind <= 5 pts | 1.5/0.5 | 0.56 | 0.22 [-0.35,0.78] | 0.80 | 0.22 | 0.21 | 0.22 | 0.34 | 1.09 | 0.01 | 0.16 | -451 | -40658 | -40145 | -31395 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| fresh ARR iplFVG 45s behind <= 5 pts | 1.0/0.5 | 0.53 | 0.11 [-0.18,0.41] | 0.43 | 0.11 | 0.11 | 0.12 | 0.18 | 0.59 | 0.01 | 0.08 | -509 | -35679 | -35263 | -33731 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| fresh ARR iplFVG 45s behind <= 5 pts | 2.0/1.0 | 1.06 | 0.11 [-0.18,0.41] | 0.43 | 0.11 | 0.11 | 0.12 | 0.18 | 0.59 | 0.01 | 0.08 | 116 | 1051 | 137 | 4673 | SIGN-ONLY | placebo,RW,CI>0 |
| fresh ARR iplFVG 45s behind <= 5 pts | 1.5/1.0 | 1.03 | 0.06 [-0.09,0.21] | 0.22 | 0.06 | 0.06 | 0.06 | 0.09 | 0.31 | 0.00 | 0.04 | 58 | 2655 | 2722 | 2336 | SIGN-ONLY | placebo,RW,CI>0 |
| mit FIB ote79_up 1h behind <= 5 pts | 2.0/0.5 | 0.52 | -0.21 [-0.55,0.14] | 0.50 | -0.21 | -0.20 | -0.21 | 0.36 | 0.39 | -0.15 | -0.65 | -584 | -44120 | -40727 | -34812 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| mit FIB ote79_up 1h behind <= 5 pts | 1.5/0.5 | 0.51 | -0.14 [-0.37,0.09] | 0.33 | -0.14 | -0.13 | -0.14 | 0.24 | 0.26 | -0.10 | -0.44 | -579 | -41398 | -38141 | -35230 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |

### Base W0: 100 selected (mask, scheme) cells; mean eq_add PRE 0.29 | X' 0.52 | **L6M 0.08** | HOLD 0.03 | 2026 -0.30; share L6M>0 60%; mean raw_wk L6M 9

| location | scheme | expo | eq_add_L6M | MDE | eq_add_pc | M | LIVE | PRE | Xp | HOLD | Y26 | raw_wk | stackD_L6M | stackD_HOLD | lev_L6M | tier | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| book flag=dflip10 | 2.0/0.5 | 0.65 | 0.13 [-0.70,0.95] | 1.18 | 0.14 | 0.13 | 0.13 | 0.73 | 0.63 | 0.24 | -1.86 | -367 | -54307 | -49056 | -30180 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| book flag=dflip10 | 1.5/0.5 | 0.60 | 0.09 [-0.50,0.68] | 0.85 | 0.10 | 0.09 | 0.09 | 0.53 | 0.46 | 0.17 | -1.35 | -432 | -47911 | -43370 | -34390 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| book flag=dflip10 | 1.0/0.5 | 0.55 | 0.05 [-0.27,0.37] | 0.46 | 0.06 | 0.05 | 0.05 | 0.29 | 0.25 | 0.09 | -0.73 | -496 | -48200 | -44072 | -38600 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| book flag=dflip10 | 2.0/1.0 | 1.10 | 0.05 [-0.27,0.37] | 0.46 | 0.06 | 0.05 | 0.05 | 0.29 | 0.25 | 0.09 | -0.73 | 129 | -6591 | -6254 | 8421 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| book flag=dflip10 | 1.5/1.0 | 1.05 | 0.03 [-0.14,0.20] | 0.24 | 0.03 | 0.03 | 0.03 | 0.15 | 0.13 | 0.05 | -0.38 | 65 | -5440 | -5480 | 4210 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| fresh ARR iplFVG 45s behind <= 5 pts | 2.0/0.5 | 0.60 | 0.39 [-0.41,1.18] | 1.14 | 0.41 | 0.37 | 0.39 | 0.40 | 1.45 | 0.14 | 0.05 | -371 | -44102 | -42998 | -34491 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| fresh ARR iplFVG 45s behind <= 5 pts | 1.5/0.5 | 0.56 | 0.27 [-0.29,0.84] | 0.80 | 0.29 | 0.26 | 0.28 | 0.28 | 1.04 | 0.10 | 0.04 | -434 | -40213 | -38796 | -37264 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| fresh ARR iplFVG 45s behind <= 5 pts | 1.0/0.5 | 0.53 | 0.14 [-0.15,0.44] | 0.43 | 0.15 | 0.14 | 0.15 | 0.15 | 0.56 | 0.05 | 0.02 | -498 | -42207 | -40719 | -40038 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| fresh ARR iplFVG 45s behind <= 5 pts | 2.0/1.0 | 1.06 | 0.14 [-0.15,0.44] | 0.43 | 0.15 | 0.14 | 0.15 | 0.15 | 0.56 | 0.05 | 0.02 | 126 | -860 | -2478 | 5546 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| fresh ARR iplFVG 45s behind <= 5 pts | 1.5/1.0 | 1.03 | 0.07 [-0.08,0.23] | 0.22 | 0.08 | 0.07 | 0.08 | 0.08 | 0.29 | 0.03 | 0.01 | 63 | -4321 | -4599 | 2773 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| mit FIB ote79_up 1h behind <= 5 pts | 2.0/0.5 | 0.52 | -0.20 [-0.56,0.15] | 0.51 | -0.21 | -0.19 | -0.20 | 0.36 | 0.34 | -0.14 | -0.53 | -578 | -50233 | -45740 | -41321 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| mit FIB ote79_up 1h behind <= 5 pts | 1.5/0.5 | 0.51 | -0.14 [-0.38,0.10] | 0.34 | -0.14 | -0.13 | -0.14 | 0.24 | 0.23 | -0.10 | -0.36 | -572 | -48662 | -44374 | -41817 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |

### 2b. Location SCORE as a continuous sizer / threshold filter (weights = PRE+X' z of the B1 pooled top-60, fitted once; scored once)

| base | variant | expo | keep | tpw | eq_add_L6M | MDE | eq_add_pc | M | LIVE | PRE | Xp | HOLD | Y26 | raw_wk | stackD_L6M | stackD_HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M0 | cont_clip02 | 0.95 | 97% | 336.6 | 0.17 [-0.53,0.86] | 0.99 | 0.17 | 0.17 | 0.17 | 0.80 | 1.79 | 0.03 | -0.45 | 2 | -15496 | -11268 |
| M0 | half_clip02 | 0.98 | 100% | 347.9 | 0.07 [-0.26,0.41] | 0.48 | 0.07 | 0.08 | 0.08 | 0.40 | 0.93 | 0.00 | -0.23 | -0 | -4767 | -2673 |
| M0 | filt_p50 | 0.45 | 45% | 155.2 | -0.31 [-1.49,0.88] | 1.69 | -0.31 | -0.29 | -0.30 | 1.35 | 3.25 | -0.39 | -1.56 | -673 | -42251 | -33363 |
| M0 | filt_p70 | 0.27 | 27% | 92.4 | 0.36 [-1.39,2.12] | 2.51 | 0.36 | 0.38 | 0.38 | 2.04 | 4.90 | -0.26 | 0.76 | -796 | -38588 | -32974 |
| M0 | filt_p80 | 0.18 | 18% | 64.2 | 0.10 [-2.44,2.64] | 3.63 | 0.10 | 0.11 | 0.11 | 2.15 | 5.19 | -0.72 | 1.24 | -914 | -47433 | -39641 |
| S73 | cont_clip02 | 0.95 | 97% | 338.6 | 0.22 [-0.52,0.97] | 1.06 | 0.23 | 0.22 | 0.23 | 0.71 | 1.70 | 0.11 | -0.68 | 15 | -12687 | -9721 |
| S73 | half_clip02 | 0.97 | 100% | 347.9 | 0.11 [-0.25,0.47] | 0.52 | 0.11 | 0.11 | 0.11 | 0.35 | 0.88 | 0.05 | -0.33 | 8 | -2092 | -1673 |
| S73 | filt_p50 | 0.45 | 45% | 155.2 | 0.38 [-1.27,2.04] | 2.36 | 0.39 | 0.38 | 0.40 | 1.16 | 3.09 | 0.28 | -0.74 | -568 | -45907 | -39400 |
| S73 | filt_p70 | 0.27 | 27% | 92.9 | -0.07 [-2.02,1.88] | 2.79 | -0.07 | -0.06 | -0.06 | 2.11 | 4.12 | -0.51 | -2.28 | -837 | -52628 | -48219 |
| S73 | filt_p80 | 0.18 | 18% | 62.7 | 0.09 [-2.05,2.24] | 3.07 | 0.09 | 0.10 | 0.11 | 3.00 | 5.17 | -1.34 | -1.17 | -923 | -61468 | -59683 |
| W0 | cont_clip02 | 0.95 | 96% | 332.4 | 0.22 [-0.60,1.04] | 1.17 | 0.24 | 0.22 | 0.23 | 0.68 | 1.66 | 0.18 | -1.52 | 11 | -22742 | -16925 |
| W0 | half_clip02 | 0.97 | 100% | 347.9 | 0.11 [-0.29,0.51] | 0.57 | 0.11 | 0.11 | 0.11 | 0.34 | 0.86 | 0.09 | -0.72 | 5 | -17318 | -11980 |
| W0 | filt_p50 | 0.46 | 46% | 160.3 | 0.02 [-1.48,1.52] | 2.15 | 0.03 | 0.03 | 0.03 | 1.59 | 2.61 | -0.17 | -4.04 | -602 | -51298 | -44024 |
| W0 | filt_p70 | 0.27 | 27% | 92.9 | -0.45 [-2.94,2.05] | 3.57 | -0.48 | -0.43 | -0.44 | 2.63 | 3.40 | -0.70 | -4.93 | -864 | -73341 | -65660 |
| W0 | filt_p80 | 0.17 | 17% | 60.3 | -0.78 [-4.10,2.55] | 4.75 | -0.83 | -0.74 | -0.77 | 2.70 | 5.18 | -1.17 | -5.21 | -974 | -81860 | -72904 |

## 3. STOPS (and targets) AT THE LOCATION (B3) - STRUCTURE
When the POI is behind the entry the stop sits just beyond the POI near edge (+ buffer 2/4/8 pts) instead of the fixed 60; targets: unch (60) / rr1 (= stop) / rr2 (2 x stop) / liq (next fresh POI ahead >= 5 pts, minus 2 ticks); lots flat or risk-matched (min(2, 60/stop)). **0 of 1,632 cells per base passed the PRE+X' eligibility (every moved-stop cell lost pts per signal in both windows)**, so the table is the registered fallback: the best 20 per base by PRE+X' z regardless of sign (BEST-AVAILABLE-NEGATIVE). delta = change per ALL signals in pts per planned lot (risk-matched cells in risk-matched units); delta_kept = per entered signal; placebo = the same cell with the stop/target distances permuted among the kept trades within book (20 draws, N basis): the real minus placebo is what the LOCATION adds beyond "a tighter stop".

### Base M0 (fallback best-20)

| location | buf | target | lots | tpw | n | delta_L6M | delta_kept | M | LIVE | PRE | Xp | HOLD | placebo_mean_L6M | real_minus_placebo | placebo_rank |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| mit FIB ret38 4h behind <= 10 pts | 8.0 | unch | rm | 5.9 | 166 | 0.05 [-0.13,0.23] | 2.78 | 0.05 | 0.06 | -0.02 | -0.08 | 0.05 | -0.03 | 0.08 | 1/21 |
| any ORB Hx2 15m behind <= 5 pts | 8.0 | unch | rm | 3.2 | 91 | -0.13 [-0.28,0.01] | -14.28 | -0.12 | -0.13 | 0.01 | -0.30 | -0.14 | -0.14 | 0.00 | 7/21 |
| mit FIB ret38 4h behind <= 10 pts | 4.0 | unch | rm | 5.9 | 166 | -0.07 [-0.28,0.14] | -4.12 | -0.06 | -0.06 | -0.07 | -0.05 | -0.06 | -0.04 | -0.03 | 20/21 |
| any FIB ote79_up 1h behind <= 10 pts | 8.0 | unch | rm | 8.4 | 236 | 0.05 [-0.16,0.27] | 2.23 | 0.06 | 0.07 | -0.16 | 0.03 | 0.02 | 0.04 | 0.01 | 9/21 |
| mit any DEV-class POI behind <= 2 pts | 8.0 | unch | rm | 15.9 | 446 | -0.31 [-0.58,-0.03] | -6.69 | -0.25 | -0.28 | -0.08 | -0.20 | -0.27 | -0.30 | -0.00 | 10/21 |
| any FIB ote79_up 1h behind <= 10 pts | 8.0 | rr2 | rm | 8.4 | 236 | 0.05 [-0.15,0.25] | 1.95 | 0.03 | 0.06 | -0.19 | 0.08 | 0.05 | 0.03 | 0.02 | 8/21 |
| fresh BOS BOS_up 5m behind <= 10 pts | 8.0 | rr1 | rm | 4.5 | 127 | -0.19 [-0.35,-0.04] | -14.87 | -0.22 | -0.19 | -0.04 | -0.25 | -0.19 | -0.19 | -0.00 | 11/21 |
| fresh BOS BOS_up 5m behind <= 10 pts | 8.0 | rr1 | flat | 4.5 | 127 | -0.18 [-0.36,-0.01] | -14.19 | -0.18 | -0.18 | -0.04 | -0.24 | -0.19 | -0.18 | -0.00 | 11/21 |
| fresh ARR iFVG_CE 5m behind <= 10 pts | 8.0 | unch | rm | 14.7 | 411 | 0.18 [-0.02,0.39] | 4.35 | 0.18 | 0.21 | -0.15 | -0.08 | 0.15 | 0.14 | 0.05 | 5/21 |
| fresh BOS BOS_up 5m behind <= 10 pts | 8.0 | liq | flat | 4.5 | 127 | -0.17 [-0.36,0.01] | -13.13 | -0.18 | -0.16 | -0.04 | -0.26 | -0.18 | -0.17 | -0.00 | 15/21 |
| mit DEV sess_H so_far behind <= 2 pts | 8.0 | unch | rm | 6.9 | 194 | -0.11 [-0.25,0.03] | -5.50 | -0.09 | -0.10 | -0.09 | -0.09 | -0.09 | -0.10 | -0.01 | 14/21 |
| fresh BOS BOS_up 5m behind <= 10 pts | 8.0 | rr2 | rm | 4.5 | 127 | -0.17 [-0.33,-0.02] | -13.35 | -0.18 | -0.17 | -0.04 | -0.28 | -0.15 | -0.15 | -0.02 | 16/21 |
| mit FIB ret38 4h behind <= 10 pts | 2.0 | unch | rm | 5.9 | 166 | -0.09 [-0.28,0.11] | -5.19 | -0.07 | -0.08 | -0.11 | -0.06 | -0.08 | -0.05 | -0.04 | 20/21 |
| fresh BOS BOS_up 5m behind <= 10 pts | 8.0 | liq | rm | 4.5 | 127 | -0.17 [-0.34,0.01] | -12.76 | -0.21 | -0.16 | -0.04 | -0.28 | -0.18 | -0.16 | -0.00 | 15/21 |
| fresh BOS BOS_up 5m behind <= 10 pts | 4.0 | liq | flat | 4.5 | 127 | -0.17 [-0.36,0.02] | -13.14 | -0.17 | -0.16 | -0.04 | -0.27 | -0.18 | -0.17 | -0.00 | 19/21 |
| fresh BOS BOS_up 5m behind <= 10 pts | 2.0 | liq | flat | 4.5 | 127 | -0.17 [-0.36,0.02] | -13.03 | -0.17 | -0.16 | -0.04 | -0.26 | -0.19 | -0.17 | -0.00 | 15/21 |
| fresh BOS BOS_up 5m behind <= 10 pts | 2.0 | rr2 | flat | 4.5 | 127 | -0.18 [-0.36,-0.00] | -13.98 | -0.17 | -0.18 | -0.04 | -0.26 | -0.19 | -0.18 | -0.00 | 13/21 |
| fresh BOS BOS_up 5m behind <= 10 pts | 2.0 | rr1 | flat | 4.5 | 127 | -0.19 [-0.38,-0.00] | -14.55 | -0.18 | -0.18 | -0.04 | -0.26 | -0.20 | -0.18 | -0.01 | 21/21 |
| fresh BOS BOS_up 5m behind <= 10 pts | 4.0 | rr2 | flat | 4.5 | 127 | -0.20 [-0.38,-0.02] | -15.09 | -0.18 | -0.19 | -0.04 | -0.26 | -0.20 | -0.18 | -0.02 | 21/21 |
| mit FIB ret38 4h behind <= 10 pts | 8.0 | rr2 | rm | 5.9 | 166 | -0.01 [-0.16,0.15] | -0.30 | -0.03 | 0.00 | -0.10 | -0.13 | -0.00 | -0.07 | 0.06 | 1/21 |

### Base S73 (fallback best-20)

| location | buf | target | lots | tpw | n | delta_L6M | delta_kept | M | LIVE | PRE | Xp | HOLD | placebo_mean_L6M | real_minus_placebo | placebo_rank |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| mit FIB ret38 4h behind <= 10 pts | 8.0 | unch | rm | 5.9 | 166 | 0.05 [-0.13,0.22] | 2.72 | 0.04 | 0.06 | -0.03 | -0.08 | 0.04 | -0.04 | 0.09 | 1/21 |
| any ORB Hx2 15m behind <= 5 pts | 8.0 | unch | rm | 3.2 | 91 | -0.14 [-0.28,0.00] | -14.83 | -0.13 | -0.13 | 0.03 | -0.31 | -0.15 | -0.14 | 0.01 | 6/21 |
| any FIB ote79_up 1h behind <= 10 pts | 8.0 | unch | rm | 8.4 | 236 | 0.05 [-0.17,0.27] | 2.01 | 0.05 | 0.07 | -0.14 | 0.01 | -0.01 | 0.04 | 0.01 | 9/21 |
| mit FIB ret38 4h behind <= 10 pts | 4.0 | unch | rm | 5.9 | 166 | -0.09 [-0.30,0.12] | -5.05 | -0.07 | -0.08 | -0.08 | -0.07 | -0.09 | -0.05 | -0.03 | 20/21 |
| mit any DEV-class POI behind <= 2 pts | 8.0 | unch | rm | 15.9 | 446 | -0.29 [-0.59,0.01] | -6.36 | -0.24 | -0.26 | -0.09 | -0.19 | -0.26 | -0.29 | -0.00 | 10/21 |
| mit DEV day_H so_far behind <= 2 pts | 8.0 | unch | rm | 6.9 | 192 | -0.05 [-0.23,0.13] | -2.39 | -0.03 | -0.03 | -0.08 | -0.08 | -0.05 | -0.03 | -0.01 | 19/21 |
| fresh ARR iFVG_CE 5m behind <= 10 pts | 8.0 | unch | rm | 14.7 | 411 | 0.16 [-0.04,0.36] | 3.77 | 0.16 | 0.19 | -0.15 | -0.09 | 0.12 | 0.11 | 0.05 | 3/21 |
| any ORB Hx2 15m behind <= 5 pts | 8.0 | unch | flat | 3.2 | 91 | -0.11 [-0.24,0.03] | -11.51 | -0.09 | -0.10 | -0.01 | -0.25 | -0.11 | -0.11 | 0.00 | 6/21 |
| mit DEV sess_H so_far behind <= 2 pts | 8.0 | unch | rm | 6.9 | 194 | -0.11 [-0.26,0.03] | -5.72 | -0.09 | -0.10 | -0.09 | -0.09 | -0.09 | -0.10 | -0.01 | 14/21 |
| mit FIB ret38 4h behind <= 10 pts | 2.0 | unch | rm | 5.9 | 166 | -0.09 [-0.28,0.10] | -5.54 | -0.07 | -0.08 | -0.12 | -0.06 | -0.10 | -0.06 | -0.04 | 20/21 |
| fresh BOS BOS_up 5m behind <= 10 pts | 4.0 | rr2 | rm | 4.5 | 127 | -0.22 [-0.39,-0.05] | -16.79 | -0.22 | -0.21 | -0.04 | -0.30 | -0.20 | -0.18 | -0.04 | 21/21 |
| any FIB ote79_up 1h behind <= 10 pts | 8.0 | rr2 | rm | 8.4 | 236 | 0.05 [-0.15,0.26] | 2.20 | 0.03 | 0.07 | -0.20 | 0.03 | 0.02 | 0.04 | 0.01 | 6/21 |
| mit FIB ret38 4h behind <= 10 pts | 8.0 | unch | flat | 5.9 | 166 | -0.02 [-0.17,0.13] | -1.17 | -0.00 | -0.01 | -0.09 | -0.10 | -0.04 | -0.06 | 0.04 | 1/21 |
| fresh BOS BOS_up 5m behind <= 10 pts | 4.0 | rr2 | flat | 4.5 | 127 | -0.19 [-0.37,-0.02] | -14.85 | -0.18 | -0.19 | -0.04 | -0.27 | -0.19 | -0.17 | -0.02 | 21/21 |
| fresh BOS BOS_up 5m behind <= 10 pts | 8.0 | rr1 | flat | 4.5 | 127 | -0.17 [-0.34,0.00] | -12.99 | -0.17 | -0.16 | -0.05 | -0.25 | -0.18 | -0.18 | 0.01 | 6/21 |
| mit DEV day_H so_far behind <= 2 pts | 4.0 | unch | rm | 6.9 | 192 | -0.05 [-0.21,0.11] | -2.47 | -0.02 | -0.04 | -0.10 | -0.08 | -0.04 | -0.03 | -0.02 | 20/21 |
| fresh BOS BOS_up 5m behind <= 10 pts | 8.0 | liq | flat | 4.5 | 127 | -0.17 [-0.35,0.02] | -12.80 | -0.17 | -0.16 | -0.05 | -0.26 | -0.18 | -0.17 | -0.00 | 13/21 |
| any FIB ote79_up 1h behind <= 5 pts | 8.0 | unch | rm | 4.2 | 117 | 0.01 [-0.13,0.14] | 0.77 | 0.02 | 0.02 | -0.07 | -0.14 | -0.04 | 0.05 | -0.04 | 21/21 |
| fresh BOS BOS_up 5m behind <= 10 pts | 8.0 | rr1 | rm | 4.5 | 127 | -0.17 [-0.32,-0.02] | -13.07 | -0.20 | -0.16 | -0.05 | -0.27 | -0.17 | -0.18 | 0.01 | 6/21 |
| mit FIB ret38 4h behind <= 10 pts | 8.0 | rr2 | rm | 5.9 | 166 | 0.02 [-0.14,0.18] | 1.18 | -0.00 | 0.03 | -0.11 | -0.10 | 0.02 | -0.06 | 0.09 | 1/21 |

## 4. THE 30% RESTS AT THE LOCATION (B4, base S73) - STRUCTURE
The reserve (30%) rests as a limit at the POI near edge (lvl a) or 2 ticks nearer (lvl b) instead of the plain 3-pt dip, when 1 <= dip <= 30. R1: signals without the location keep the plain dip; R2: signals without the location are skipped (take-only + reserve at location). Compared with the floor (plain 3-pt dip) and with the same cell with the dip distances permuted within book (20 draws). delta = change per ALL signals (pts per planned lot); add_enter = entered mean minus the all-signals floor mean; pc = pts per contract of final position (rule vs floor) over the entered set.

### Rule R1 (other signals keep the plain dip): 17 PRE+X'-selected cells, top 15

| location | lvl | res_n_L6M | fill | tpw | delta_L6M | add_enter | pc_rule | pc_floor | M | LIVE | PRE | Xp | HOLD | placebo_mean | real_minus_placebo | rank | stackD_L6M_HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| any SWG f3H 10m behind <= 2 pts | a | 716 | 0.97 | 347.9 | -0.05 [-0.09,-0.01] | -0.05 | 3.21 | 3.26 | -0.05 | -0.05 | 0.02 | 0.02 | -0.05 | -0.04 | -0.00 | 11/21 | -1153 / -962 |
| mit SWG f3H 10m behind <= 2 pts | a | 711 | 0.97 | 347.9 | -0.05 [-0.09,-0.01] | -0.05 | 3.21 | 3.26 | -0.05 | -0.05 | 0.02 | 0.02 | -0.05 | -0.04 | -0.01 | 15/21 | -1153 / -962 |
| mit any CRT-class POI behind <= 2 pts | a | 331 | 0.97 | 347.9 | -0.01 [-0.03,0.02] | -0.01 | 3.25 | 3.26 | -0.01 | -0.01 | 0.00 | 0.02 | -0.01 | -0.00 | -0.00 | 14/21 | -788 / -839 |
| any SWG f3H 10m behind <= 2 pts | b | 395 | 0.96 | 347.9 | -0.06 [-0.11,-0.02] | -0.06 | 3.20 | 3.26 | -0.06 | -0.06 | 0.01 | 0.02 | -0.07 | -0.02 | -0.04 | 21/21 | -1201 / -813 |
| mit SWG f3H 10m behind <= 2 pts | b | 391 | 0.97 | 347.9 | -0.06 [-0.11,-0.02] | -0.06 | 3.20 | 3.26 | -0.06 | -0.06 | 0.01 | 0.02 | -0.07 | -0.03 | -0.03 | 21/21 | -1201 / -813 |
| fresh ARR OB 30s behind <= 10 pts | b | 1812 | 0.87 | 347.9 | -0.02 [-0.10,0.05] | -0.02 | 3.24 | 3.26 | -0.02 | -0.02 | 0.04 | 0.05 | -0.03 | 0.02 | -0.04 | 20/21 | 4508 / 3166 |
| fresh ARR OB 30s behind <= 10 pts | a | 1847 | 0.86 | 347.9 | -0.04 [-0.13,0.04] | -0.04 | 3.22 | 3.26 | -0.04 | -0.04 | 0.04 | 0.03 | -0.05 | 0.01 | -0.06 | 21/21 | 5293 / 3664 |
| any SWG f3H 10m behind <= 5 pts | a | 1876 | 0.95 | 347.9 | -0.01 [-0.09,0.06] | -0.01 | 3.25 | 3.26 | -0.01 | -0.01 | 0.02 | 0.02 | -0.03 | -0.03 | 0.01 | 6/21 | 4185 / 2934 |
| mit SWG f3H 10m behind <= 5 pts | a | 1869 | 0.95 | 347.9 | -0.01 [-0.09,0.06] | -0.01 | 3.25 | 3.26 | -0.01 | -0.01 | 0.02 | 0.02 | -0.03 | -0.04 | 0.02 | 5/21 | 4185 / 2934 |
| any SWG f3H 10m behind <= 5 pts | b | 1555 | 0.95 | 347.9 | -0.03 [-0.10,0.04] | -0.03 | 3.23 | 3.26 | -0.03 | -0.03 | 0.01 | 0.02 | -0.04 | -0.03 | -0.00 | 8/21 | 3379 / 3045 |
| mit SWG f3H 10m behind <= 5 pts | b | 1549 | 0.95 | 347.9 | -0.03 [-0.10,0.04] | -0.03 | 3.23 | 3.26 | -0.03 | -0.03 | 0.01 | 0.02 | -0.04 | -0.03 | -0.00 | 11/21 | 3379 / 3045 |
| any ARR FVG_CE 5m behind <= 2 pts | b | 303 | 0.99 | 347.9 | -0.01 [-0.03,0.02] | -0.01 | 3.25 | 3.26 | -0.01 | -0.01 | 0.00 | 0.00 | -0.02 | -0.03 | 0.02 | 4/21 | -123 / -904 |
| any any CRT-class POI behind <= 2 pts | a | 338 | 0.97 | 347.9 | -0.01 [-0.03,0.01] | -0.01 | 3.25 | 3.26 | -0.01 | -0.01 | 0.00 | 0.00 | -0.01 | -0.01 | -0.00 | 14/21 | -788 / -840 |
| fresh ARR iplFVG 45s behind <= 10 pts | a | 1327 | 0.89 | 347.9 | -0.02 [-0.08,0.03] | -0.02 | 3.23 | 3.26 | -0.02 | -0.02 | 0.00 | 0.04 | -0.03 | -0.01 | -0.01 | 14/21 | -1265 / -2104 |
| fresh ARR iplFVG 45s behind <= 2 pts | a | 132 | 0.98 | 347.9 | -0.00 [-0.01,0.00] | -0.00 | 3.26 | 3.26 | -0.00 | -0.00 | 0.00 | 0.00 | -0.00 | -0.01 | 0.01 | 6/21 | -424 / -360 |

### Rule R2 (other signals skipped): 30 PRE+X'-selected cells, top 15

| location | lvl | res_n_L6M | fill | tpw | delta_L6M | add_enter | pc_rule | pc_floor | M | LIVE | PRE | Xp | HOLD | placebo_mean | real_minus_placebo | rank | stackD_L6M_HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| fresh ARR iplFVG 45s behind <= 2 pts | a | 132 | 0.98 | 4.7 | -3.19 [-5.33,-1.05] | 1.85 | 5.08 | 3.26 | -1.00 | -2.56 | -1.50 | -0.23 | -2.51 | -3.19 | -0.00 | 13/21 | -68681 / -57368 |
| fresh ARR iplFVG 45s behind <= 5 pts | b | 488 | 0.94 | 17.4 | -3.04 [-5.22,-0.85] | 1.15 | 4.41 | 3.26 | -0.93 | -2.43 | -1.34 | 0.26 | -2.45 | -3.01 | -0.03 | 15/21 | -66352 / -58693 |
| fresh ARR iplFVG 45s behind <= 5 pts | a | 536 | 0.94 | 19.1 | -3.01 [-5.17,-0.85] | 1.18 | 4.44 | 3.26 | -0.92 | -2.41 | -1.34 | 0.31 | -2.42 | -2.99 | -0.02 | 15/21 | -64288 / -56858 |
| mit FIB ret38 4h behind <= 10 pts | b | 137 | 0.86 | 4.9 | -3.18 [-5.31,-1.04] | 2.60 | 5.93 | 3.26 | -0.99 | -2.55 | -1.44 | -0.31 | -2.47 | -3.18 | 0.00 | 10/21 | -72637 / -60849 |
| mit FIB ret38 4h behind <= 10 pts | a | 145 | 0.86 | 5.2 | -3.18 [-5.30,-1.05] | 2.29 | 5.61 | 3.26 | -0.99 | -2.55 | -1.44 | -0.31 | -2.47 | -3.18 | 0.01 | 7/21 | -72550 / -60765 |
| any OPN midnight d behind <= 10 pts | a | 313 | 0.88 | 11.2 | -3.21 [-5.44,-0.98] | -1.73 | 1.54 | 3.26 | -1.06 | -2.60 | -1.43 | -0.15 | -2.58 | -3.17 | -0.04 | 19/21 | -68528 / -60870 |
| mit OPN midnight d behind <= 10 pts | a | 310 | 0.88 | 11.1 | -3.19 [-5.42,-0.96] | -1.12 | 2.16 | 3.26 | -1.04 | -2.58 | -1.43 | -0.15 | -2.57 | -3.17 | -0.02 | 17/21 | -68055 / -60456 |
| any OPN midnight d behind <= 10 pts | b | 303 | 0.88 | 10.8 | -3.21 [-5.44,-0.97] | -1.68 | 1.59 | 3.26 | -1.06 | -2.60 | -1.45 | -0.16 | -2.57 | -3.18 | -0.03 | 17/21 | -68060 / -59976 |
| mit OPN midnight d behind <= 10 pts | b | 300 | 0.88 | 10.7 | -3.19 [-5.42,-0.96] | -1.05 | 2.23 | 3.26 | -1.04 | -2.58 | -1.45 | -0.16 | -2.55 | -3.17 | -0.01 | 14/21 | -67587 / -59562 |
| fresh BOS BOS_up 5m behind <= 10 pts | a | 121 | 0.86 | 4.3 | -3.08 [-5.30,-0.87] | 10.93 | 14.38 | 3.26 | -0.90 | -2.45 | -1.55 | -0.21 | -2.39 | -3.10 | 0.02 | 2/21 | -70053 / -58024 |
| any ARR OB 15m behind <= 10 pts | b | 424 | 0.86 | 15.1 | -3.06 [-5.23,-0.89] | 1.30 | 4.64 | 3.26 | -0.94 | -2.45 | -1.35 | -0.10 | -2.42 | -3.10 | 0.04 | 9/21 | -66302 / -56357 |
| mit FIB pd50 5m behind <= 5 pts | b | 135 | 0.92 | 4.8 | -3.25 [-5.43,-1.07] | -2.97 | 0.29 | 3.26 | -1.07 | -2.63 | -1.49 | -0.35 | -2.59 | -3.29 | 0.04 | 2/21 | -72622 / -61497 |
| any ARR OB 15m behind <= 10 pts | a | 452 | 0.87 | 16.1 | -3.05 [-5.20,-0.89] | 1.33 | 4.64 | 3.26 | -0.93 | -2.44 | -1.36 | -0.04 | -2.40 | -3.07 | 0.03 | 10/21 | -65785 / -55822 |
| fresh ARR iFVG_CE 5m behind <= 10 pts | b | 399 | 0.85 | 14.2 | -3.18 [-5.35,-1.01] | -1.31 | 1.98 | 3.26 | -1.05 | -2.57 | -1.35 | -0.20 | -2.47 | -3.19 | 0.01 | 5/21 | -70065 / -57195 |
| fresh ARR iFVG_CE 5m behind <= 10 pts | a | 408 | 0.84 | 14.6 | -3.21 [-5.39,-1.02] | -2.01 | 1.27 | 3.26 | -1.08 | -2.60 | -1.36 | -0.20 | -2.49 | -3.19 | -0.02 | 19/21 | -70594 / -57264 |

## 5. COMBINATIONS of locations (B5, CF-COMBO method)
Members: the B1 pooled-selected top 40 (<= 8 per family); pairs (AND), triples from the top 15, k-of-n (k=2,3 of the top 12), location AND signal-second book confirmation (dflip / reversal-imbalance / micro-price / refill / absorption / iceberg / imbalance-support / sweep / big print), and the four-legged location (POI behind AND discount/premium AND HTF agreement AND book defence; k>=4/3/2 legs). 1,540 cells per base; PRE+X' selection (the B1 eligibility), top 100 per base, one look. Post-signal confirmations (15-s HA flip etc.) belong to the confirm layer (CF-COMBO), not here.

### Base M0: group validity over the 100 selected cells (L6M): White RC p 0.482, cumulative-adjusted p 1.00, Romano-Wolf survivors 0, PBO 0.86
#### M0: top-12 combinations of 100 (PRE+X' z)
Selected cells: 100; mean add per entered trade (N, pts/planned lot): PRE 3.45 | X' 4.82 | **L6M 1.20** | HOLD 0.09 | 2026 0.06 | L3M(view) 0.66; share of cells with L6M add>0: 87%; mean keep rate L6M 13%; mean total change gain_wk L6M -938 planned-lot pts/week.

| location | keep | tpw | n | kept | skipped | add_pl_L6M | MDE | add_pc | M | LIVE | PRE | Xp | HOLD | Y26 | gain_wk | stackD_L6M | stackD_HOLD | plc | RW | tier | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 3of12 of top-12 locations | 31% | 109.0 | 3051 | 3.74 | 3.02 | 0.49 [-0.99,1.98] | 2.12 | 0.49 | 0.48 | 0.50 | 2.44 | 5.08 | -0.12 | -1.27 | -722 | -39109 | -36496 | 88/201 | N | DEAD | HOLD+,placebo,RW,stack,CI>0 |
| FIB-class POI behind <= 5 AND book defS AND mit ARR iFVG_CE 2m behind <= 2 pts | 4% | 14.4 | 403 | 6.25 | 3.11 | 3.01 [-2.75,8.77] | 8.23 | 3.01 | 2.87 | 3.06 | 6.99 | 7.09 | 1.27 | -8.29 | -1039 | -52246 | -42904 | 45/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| FIB-class POI behind <= 2 AND book defS AND mit ARR iFVG_CE 2m behind <= 2 pts | 3% | 12.1 | 340 | 6.64 | 3.12 | 3.40 [-2.87,9.67] | 8.96 | 3.40 | 3.25 | 3.46 | 7.86 | 8.52 | 1.47 | -6.64 | -1048 | -52199 | -42610 | 41/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| mit ORB Lx1 30m behind <= 20 pts AND fresh ARR iFVG 45s behind <= 20 pts | 1% | 3.1 | 86 | 3.27 | 3.24 | 0.03 [-14.02,14.08] | 20.07 | 0.03 | -0.01 | 0.02 | 4.04 | 14.93 | -4.98 | 0.58 | -1119 | -61264 | -49682 | 173/201 | N | DEAD | HOLD+,M&L+,placebo,RW,stack,CI>0 |
| any ORB Lx1 30m behind <= 20 pts AND fresh ARR iFVG 45s behind <= 20 pts | 1% | 3.1 | 86 | 3.27 | 3.24 | 0.03 [-14.02,14.08] | 20.07 | 0.03 | -0.01 | 0.02 | 4.04 | 14.93 | -4.98 | 0.58 | -1119 | -61264 | -49682 | 171/201 | N | DEAD | HOLD+,M&L+,placebo,RW,stack,CI>0 |
| PRF-class POI behind <= 10 AND book defS AND FIB-class POI behind <= 5 AND book defS AND BOS-class POI behind  | 8% | 28.1 | 788 | 6.54 | 2.95 | 3.30 [-0.64,7.23] | 5.63 | 3.30 | 3.18 | 3.36 | 4.54 | 4.68 | 1.16 | 5.98 | -945 | -45605 | -40521 | 24/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| FIB-class POI behind <= 5 AND book defS AND SWG-class POI behind <= 2 AND book defS AND BOS-class POI behind < | 9% | 31.6 | 884 | 4.61 | 3.11 | 1.37 [-2.28,5.01] | 5.21 | 1.37 | 1.31 | 1.40 | 4.59 | 4.43 | -0.05 | 2.53 | -983 | -50210 | -44355 | 86/201 | N | DEAD | HOLD+,placebo,RW,stack,CI>0 |
| FIB-class POI behind <= 5 AND book defS AND BOS-class POI behind <= 2 AND book defS | 9% | 31.6 | 884 | 4.61 | 3.11 | 1.37 [-2.28,5.01] | 5.21 | 1.37 | 1.31 | 1.40 | 4.56 | 4.50 | -0.05 | 2.53 | -983 | -50210 | -44355 | 76/201 | N | DEAD | HOLD+,placebo,RW,stack,CI>0 |
| mit SWG f7H 1m behind <= 10 pts AND confluence ntf>=2 within 5 (fresh) | 48% | 165.7 | 4640 | 3.62 | 2.90 | 0.38 [-1.36,2.11] | 2.48 | 0.38 | 0.38 | 0.39 | 0.62 | 2.25 | 0.05 | -1.15 | -528 | -20666 | -15771 | 60/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| FIB-class POI behind <= 5 AND book defS AND EQL-class POI behind <= 10 AND book defS | 13% | 46.0 | 1289 | 3.98 | 3.13 | 0.73 [-3.02,4.49] | 5.36 | 0.73 | 0.72 | 0.76 | 3.89 | 1.23 | -0.29 | 1.39 | -946 | -50160 | -43066 | 151/201 | N | DEAD | HOLD+,placebo,RW,stack,CI>0 |
| mit SWG f5H 1m behind <= 15 pts AND confluence ntf>=2 within 5 (fresh) | 54% | 187.1 | 5239 | 3.69 | 2.73 | 0.44 [-1.12,2.01] | 2.24 | 0.44 | 0.44 | 0.46 | 0.45 | 2.06 | 0.23 | -1.32 | -439 | -21121 | -14435 | 83/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| FIB-class POI behind <= 5 AND book defS AND mit SWG f5H 1m behind <= 10 pts | 14% | 49.4 | 1382 | 4.18 | 3.09 | 0.93 [-2.25,4.12] | 4.55 | 0.93 | 0.90 | 0.96 | 3.39 | 2.25 | 0.26 | 3.32 | -923 | -45347 | -38965 | 94/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |

### Base S73: group validity over the 100 selected cells (L6M): White RC p 0.442, cumulative-adjusted p 1.00, Romano-Wolf survivors 0, PBO 0.89
#### S73: top-12 combinations of 100 (PRE+X' z)
Selected cells: 100; mean add per entered trade (N, pts/planned lot): PRE 3.31 | X' 6.08 | **L6M 0.66** | HOLD -0.50 | 2026 -2.15 | L3M(view) 0.21; share of cells with L6M add>0: 76%; mean keep rate L6M 12%; mean total change gain_wk L6M -974 planned-lot pts/week.

| location | keep | tpw | n | kept | skipped | add_pl_L6M | MDE | add_pc | M | LIVE | PRE | Xp | HOLD | Y26 | gain_wk | stackD_L6M | stackD_HOLD | plc | RW | tier | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 3of12 of top-12 locations | 36% | 125.0 | 3499 | 3.65 | 3.04 | 0.39 [-1.19,1.98] | 2.26 | 0.40 | 0.40 | 0.41 | 2.39 | 4.04 | 0.18 | -0.85 | -677 | -37160 | -35487 | 96/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| FIB-class POI behind <= 5 AND book defS AND mit ARR iFVG_CE 2m behind <= 2 pts | 4% | 14.4 | 403 | 5.97 | 3.14 | 2.72 [-2.95,8.38] | 8.09 | 2.75 | 2.60 | 2.77 | 6.87 | 7.30 | 1.15 | -8.60 | -1047 | -62879 | -56093 | 56/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| mit ARR iFVG_CE 2m behind <= 2 pts AND FIB-class POI behind <= 2 AND book defS | 3% | 12.1 | 340 | 6.10 | 3.16 | 2.85 [-3.35,9.04] | 8.85 | 2.87 | 2.73 | 2.90 | 7.75 | 8.84 | 1.19 | -7.07 | -1059 | -63296 | -55907 | 50/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| FIB-class POI behind <= 2 AND book defS AND any ARR iFVG_CE 2m behind <= 2 pts | 4% | 12.4 | 346 | 6.00 | 3.16 | 2.74 [-3.64,9.12] | 9.11 | 2.75 | 2.63 | 2.79 | 7.43 | 9.10 | 1.13 | -7.07 | -1059 | -63058 | -55698 | 49/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| FIB-class POI behind <= 5 AND book defS AND any ARR iFVG_CE 2m behind <= 2 pts | 4% | 14.6 | 410 | 5.72 | 3.15 | 2.46 [-3.29,8.21] | 8.21 | 2.49 | 2.35 | 2.51 | 6.53 | 6.63 | 0.96 | -8.60 | -1050 | -62640 | -55884 | 55/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| mit SWG f7H 1m behind <= 10 pts AND confluence ntf>=2 within 5 (fresh) | 48% | 165.7 | 4640 | 3.65 | 2.90 | 0.39 [-1.32,2.11] | 2.45 | 0.40 | 0.40 | 0.41 | 0.68 | 2.27 | 0.09 | -1.30 | -528 | -28873 | -25103 | 68/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| mit ORB Lx1 30m behind <= 20 pts AND fresh ARR iFVG 45s behind <= 20 pts | 1% | 3.1 | 86 | 2.80 | 3.26 | -0.45 [-14.69,13.78] | 20.34 | -0.46 | -0.48 | -0.47 | 4.20 | 14.30 | -5.93 | -0.25 | -1125 | -71932 | -62927 | 178/201 | N | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| any ORB Lx1 30m behind <= 20 pts AND fresh ARR iFVG 45s behind <= 20 pts | 1% | 3.1 | 86 | 2.80 | 3.26 | -0.45 [-14.69,13.78] | 20.34 | -0.46 | -0.48 | -0.47 | 4.20 | 14.30 | -5.93 | -0.25 | -1125 | -71932 | -62927 | 171/201 | N | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| mit SWG f5H 1m behind <= 15 pts AND confluence ntf>=2 within 5 (fresh) | 54% | 187.1 | 5239 | 3.70 | 2.74 | 0.44 [-1.08,1.97] | 2.18 | 0.45 | 0.44 | 0.46 | 0.52 | 2.07 | 0.24 | -1.40 | -441 | -26052 | -21607 | 97/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| mit SWG f3H 2m behind <= 10 pts AND confluence ntf>=2 within 5 (fresh) | 49% | 172.0 | 4817 | 3.54 | 2.98 | 0.29 [-1.30,1.87] | 2.26 | 0.29 | 0.30 | 0.30 | 0.45 | 2.08 | 0.01 | -1.35 | -524 | -31066 | -27830 | 82/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| BOS-class POI behind <= 2 AND book defS AND FIB-class POI behind <= 5 AND book defS | 9% | 31.6 | 884 | 5.01 | 3.08 | 1.75 [-1.78,5.29] | 5.05 | 1.76 | 1.68 | 1.79 | 4.49 | 4.35 | 0.23 | 3.13 | -975 | -59913 | -57130 | 63/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| mit SWG f5H 1m behind <= 10 pts AND confluence ntf>=2 within 5 (fresh) | 51% | 177.7 | 4976 | 3.42 | 3.09 | 0.16 [-1.31,1.63] | 2.10 | 0.16 | 0.17 | 0.17 | 0.40 | 2.15 | -0.02 | -1.77 | -526 | -35681 | -29350 | 122/201 | N | DEAD | HOLD+,placebo,RW,stack,CI>0 |

### Base W0: group validity over the 100 selected cells (L6M): White RC p 0.065, cumulative-adjusted p 1.00, Romano-Wolf survivors 0, PBO 0.78
#### W0: top-12 combinations of 100 (PRE+X' z)
Selected cells: 100; mean add per entered trade (N, pts/planned lot): PRE 2.74 | X' 4.24 | **L6M 0.38** | HOLD 0.09 | 2026 -3.14 | L3M(view) 0.27; share of cells with L6M add>0: 75%; mean keep rate L6M 20%; mean total change gain_wk L6M -847 planned-lot pts/week.

| location | keep | tpw | n | kept | skipped | add_pl_L6M | MDE | add_pc | M | LIVE | PRE | Xp | HOLD | Y26 | gain_wk | stackD_L6M | stackD_HOLD | plc | RW | tier | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 3of12 of top-12 locations | 54% | 188.5 | 5278 | 4.71 | 1.46 | 1.49 [-0.06,3.04] | 2.21 | 1.59 | 1.45 | 1.52 | 1.33 | 2.06 | 1.36 | -0.72 | -233 | -19697 | -16101 | 2/201 | N | CANDIDATE-RECENT | RW,stack,CI>0 |
| confluence ntf>=2 within 5 (fresh) AND mit SWG f5H 1m behind <= 15 pts | 54% | 187.1 | 5239 | 3.64 | 2.74 | 0.41 [-0.96,1.79] | 1.96 | 0.45 | 0.41 | 0.43 | 0.55 | 1.85 | 0.30 | -1.66 | -441 | -34321 | -29595 | 111/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| fresh ARR iplFVG 45s behind <= 15 pts AND mit SWG f7H 1m behind <= 10 pts AND fresh ARR iFVG 45s behind <= 20  | 7% | 25.1 | 703 | 3.08 | 3.24 | -0.15 [-3.09,2.79] | 4.20 | -0.23 | -0.16 | -0.16 | 3.58 | 5.61 | -2.14 | -3.13 | -1044 | -78416 | -72701 | 123/201 | N | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| book flag=dflip10 AND mit SWG f7H 1m behind <= 10 pts AND mit SWG f5H 1m behind <= 15 pts | 7% | 23.2 | 650 | 3.89 | 3.18 | 0.66 [-3.86,5.19] | 6.46 | 0.74 | 0.69 | 0.68 | 4.23 | 5.68 | 1.29 | -10.16 | -1031 | -85605 | -74187 | 67/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| mit SWG f7H 1m behind <= 10 pts AND b_dflip10 | 7% | 23.2 | 650 | 3.89 | 3.18 | 0.66 [-3.86,5.19] | 6.46 | 0.74 | 0.69 | 0.68 | 4.23 | 5.68 | 1.29 | -10.16 | -1031 | -85605 | -74187 | 75/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| book flag=dflip10 AND mit SWG f7H 1m behind <= 10 pts AND any SWG f7H 1m behind <= 10 pts | 7% | 23.2 | 650 | 3.89 | 3.18 | 0.66 [-3.86,5.19] | 6.46 | 0.74 | 0.69 | 0.68 | 4.23 | 5.68 | 1.29 | -10.16 | -1031 | -85605 | -74187 | 73/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| book flag=dflip10 AND mit SWG f7H 1m behind <= 10 pts | 7% | 23.2 | 650 | 3.89 | 3.18 | 0.66 [-3.86,5.19] | 6.46 | 0.74 | 0.69 | 0.68 | 4.23 | 5.68 | 1.29 | -10.16 | -1031 | -85605 | -74187 | 72/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| mit SWG f7H 1m behind <= 10 pts AND any SWG f7H 1m behind <= 10 pts AND confluence ntf>=2 within 5 (fresh) | 48% | 165.7 | 4640 | 3.74 | 2.76 | 0.51 [-1.12,2.14] | 2.33 | 0.54 | 0.50 | 0.53 | 0.70 | 2.04 | 0.32 | -1.63 | -503 | -38486 | -32779 | 59/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| mit SWG f7H 1m behind <= 10 pts AND confluence ntf>=2 within 5 (fresh) | 48% | 165.7 | 4640 | 3.74 | 2.76 | 0.51 [-1.12,2.14] | 2.33 | 0.54 | 0.50 | 0.53 | 0.70 | 2.04 | 0.32 | -1.63 | -503 | -38486 | -32779 | 64/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| book flag=dflip10 AND any SWG f7H 1m behind <= 10 pts AND mit SWG f5H 1m behind <= 15 pts | 7% | 23.3 | 653 | 3.65 | 3.19 | 0.43 [-4.07,4.93] | 6.43 | 0.49 | 0.47 | 0.45 | 4.19 | 5.46 | 1.08 | -10.16 | -1036 | -85605 | -74187 | 82/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| any SWG f7H 1m behind <= 10 pts AND confluence ntf>=2 within 5 (fresh) AND mit SWG f5H 1m behind <= 15 pts | 48% | 166.5 | 4662 | 3.66 | 2.82 | 0.44 [-1.18,2.05] | 2.31 | 0.46 | 0.43 | 0.46 | 0.73 | 2.00 | 0.30 | -1.63 | -512 | -39752 | -33237 | 81/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |
| mit SWG f7H 1m behind <= 10 pts AND confluence ntf>=2 within 5 (fresh) AND mit SWG f5H 1m behind <= 15 pts | 48% | 165.7 | 4640 | 3.74 | 2.76 | 0.51 [-1.12,2.14] | 2.33 | 0.54 | 0.50 | 0.53 | 0.69 | 2.03 | 0.33 | -1.63 | -503 | -38486 | -32779 | 65/201 | N | SIGN-ONLY | placebo,RW,stack,CI>0 |

## 6. "FROM SUPPORT, INTO SPACE" (B8: favourable POI behind AND no trusted reversal POI ahead)
Trusted reversal POIs = the top-10 of NTZ-1's DS3_POI_MAP.md section 1 (PRE u X' ranking: PDX|rth|M, PIV|cam_H3|day, PIV|cam_L2|day, FIB|ret50|4h, KZ|kz_ny_H|prev, MAS|ich_kijun|1h, PRF|lvn1|sw1h, PDX|day|M, KZ|kz_london_H|prev, PIV|cam_H3|rth); blocked = any of them fresh ahead within min(td, 20) pts (12% of signals). Fixed list (no selection): space only, support only, support+space, and the B1 pooled top-20 locations alone vs + space. add = entered mean minus all-signals mean.

### Base M0

| cell | keep | tpw | kept | skipped | add_L6M | MDE | add_pc | M | LIVE | PRE | Xp | HOLD | Y26 | gain_wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| space ahead only (no trusted reversal POI within min(td,20)) | 90% | 314.4 | 3.60 | -0.09 | 0.35 [-0.20,0.91] | 0.80 | 0.35 | 0.34 | 0.36 | 0.38 | 1.29 | 0.34 | -0.45 | 3 |
| support behind (fresh PDX-class <=5 or fresh 1-h POI <=5) | 2% | 5.6 | 9.35 | 3.14 | 6.10 [-3.57,15.78] | 13.82 | 6.10 | 5.94 | 6.17 | -7.54 | -1.69 | 3.29 | 2.32 | -1076 |
| support behind AND space ahead | 1% | 4.6 | 11.49 | 3.13 | 8.25 [-1.01,17.51] | 13.23 | 8.25 | 8.02 | 8.34 | -6.84 | 0.83 | 4.82 | -3.98 | -1075 |
| any ORB Lx1 30m behind <= 20 pts | 3% | 9.6 | 6.46 | 3.15 | 3.21 [-2.75,9.18] | 8.52 | 3.21 | 3.02 | 3.24 | 0.73 | 11.00 | -1.07 | 3.72 | -1067 |
| any ORB Lx1 30m behind <= 20 pts AND space ahead (no trusted reversal POI) | 3% | 9.0 | 5.89 | 3.17 | 2.65 [-3.74,9.04] | 9.13 | 2.65 | 2.47 | 2.67 | -0.92 | 8.48 | -0.70 | 2.21 | -1076 |
| mit ORB Lx1 30m behind <= 20 pts | 3% | 9.6 | 6.46 | 3.15 | 3.21 [-2.75,9.18] | 8.52 | 3.21 | 3.02 | 3.24 | 0.73 | 11.00 | -1.07 | 3.72 | -1067 |
| mit ORB Lx1 30m behind <= 20 pts AND space ahead (no trusted reversal POI) | 3% | 9.0 | 5.89 | 3.17 | 2.65 [-3.74,9.04] | 9.13 | 2.65 | 2.47 | 2.67 | -0.92 | 8.48 | -0.70 | 2.21 | -1076 |
| book flag=dflip10 | 10% | 34.2 | 4.42 | 3.12 | 1.18 [-2.73,5.08] | 5.58 | 1.18 | 1.16 | 1.20 | 3.30 | 3.30 | 1.73 | -8.07 | -977 |
| book flag=dflip10 AND space ahead (no trusted reversal POI) | 9% | 31.7 | 5.11 | 3.06 | 1.87 [-1.91,5.64] | 5.39 | 1.87 | 1.83 | 1.89 | 4.15 | 5.37 | 2.37 | -8.15 | -967 |
| fresh ARR iplFVG 45s behind <= 5 pts | 6% | 22.5 | 4.38 | 3.17 | 1.14 [-3.51,5.78] | 6.64 | 1.14 | 1.14 | 1.16 | 2.84 | 7.97 | -0.45 | 2.05 | -1030 |
| fresh ARR iplFVG 45s behind <= 5 pts AND space ahead (no trusted reversal POI) | 6% | 19.2 | 4.80 | 3.15 | 1.56 [-3.19,6.31] | 6.78 | 1.56 | 1.54 | 1.58 | 4.43 | 9.00 | -0.07 | 0.82 | -1036 |
| PRF-class POI behind <= 10 AND book defS | 20% | 71.2 | 3.92 | 3.07 | 0.67 [-1.24,2.59] | 2.74 | 0.67 | 0.65 | 0.69 | 2.54 | 1.00 | -0.09 | 3.59 | -850 |
| PRF-class POI behind <= 10 AND book defS AND space ahead (no trusted reversal POI) | 19% | 64.5 | 4.13 | 3.04 | 0.88 [-1.33,3.10] | 3.16 | 0.88 | 0.86 | 0.90 | 3.11 | 1.41 | 0.08 | 2.63 | -863 |
| mit SWG f7H 1m behind <= 10 pts | 70% | 242.3 | 3.57 | 2.50 | 0.33 [-0.73,1.39] | 1.52 | 0.33 | 0.33 | 0.34 | 0.50 | 1.75 | 0.32 | -0.69 | -263 |
| mit SWG f7H 1m behind <= 10 pts AND space ahead (no trusted reversal POI) | 61% | 213.6 | 4.13 | 1.84 | 0.88 [-0.59,2.36] | 2.11 | 0.88 | 0.87 | 0.90 | 0.85 | 3.21 | 0.81 | -1.03 | -247 |
| mit FIB ote79_up 1h behind <= 5 pts | 1% | 4.0 | -1.85 | 3.30 | -5.10 [-15.20,5.00] | 14.43 | -5.10 | -4.84 | -5.15 | 9.19 | 7.80 | -3.40 | -25.05 | -1136 |
| mit FIB ote79_up 1h behind <= 5 pts AND space ahead (no trusted reversal POI) | 1% | 3.4 | 3.93 | 3.24 | 0.69 [-9.49,10.86] | 14.53 | 0.69 | 0.73 | 0.70 | 9.92 | 9.34 | 1.67 | -17.47 | -1115 |
| any FIB ote79_up 1h behind <= 5 pts | 1% | 4.2 | -0.78 | 3.29 | -4.03 [-13.96,5.91] | 14.19 | -4.03 | -3.81 | -4.07 | 9.86 | 6.70 | -2.51 | -23.14 | -1132 |
| any FIB ote79_up 1h behind <= 5 pts AND space ahead (no trusted reversal POI) | 1% | 3.5 | 5.62 | 3.22 | 2.38 [-7.63,12.39] | 14.30 | 2.38 | 2.36 | 2.41 | 10.68 | 7.96 | 3.17 | -13.18 | -1109 |
| FIB-class POI behind <= 5 AND book defS | 18% | 62.2 | 5.03 | 2.86 | 1.78 [-0.76,4.33] | 3.63 | 1.78 | 1.72 | 1.82 | 2.49 | 0.31 | 1.03 | 4.88 | -816 |
| FIB-class POI behind <= 5 AND book defS AND space ahead (no trusted reversal POI) | 16% | 56.4 | 5.24 | 2.86 | 2.00 [-0.83,4.82] | 4.03 | 2.00 | 1.93 | 2.03 | 2.83 | 0.23 | 1.03 | 4.22 | -833 |
| any SWG f7H 1m behind <= 10 pts | 70% | 244.2 | 3.54 | 2.55 | 0.30 [-0.74,1.33] | 1.48 | 0.30 | 0.30 | 0.31 | 0.52 | 1.48 | 0.31 | -0.71 | -264 |
| any SWG f7H 1m behind <= 10 pts AND space ahead (no trusted reversal POI) | 62% | 215.3 | 4.11 | 1.84 | 0.86 [-0.57,2.30] | 2.05 | 0.86 | 0.85 | 0.88 | 0.87 | 2.92 | 0.79 | -1.05 | -244 |

Adding "space ahead" to the 20 B1 locations changes add_pl by (mean): PRE 0.36, HOLD 0.62, L6M 0.63 pts per planned lot; share of the 20 improved in L6M 60%.

### Base S73

| cell | keep | tpw | kept | skipped | add_L6M | MDE | add_pc | M | LIVE | PRE | Xp | HOLD | Y26 | gain_wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| space ahead only (no trusted reversal POI within min(td,20)) | 90% | 314.4 | 3.65 | -0.43 | 0.39 [-0.17,0.96] | 0.81 | 0.39 | 0.38 | 0.40 | 0.39 | 1.30 | 0.37 | -0.46 | 15 |
| support behind (fresh PDX-class <=5 or fresh 1-h POI <=5) | 2% | 5.6 | 8.79 | 3.17 | 5.53 [-3.95,15.00] | 13.54 | 5.55 | 5.39 | 5.58 | -6.96 | -1.23 | 3.26 | 1.64 | -1084 |
| support behind AND space ahead | 1% | 4.6 | 11.22 | 3.15 | 7.96 [-1.12,17.04] | 12.97 | 7.93 | 7.74 | 8.05 | -6.53 | 1.27 | 5.10 | -4.18 | -1081 |
| any ORB Lx1 30m behind <= 20 pts | 3% | 9.6 | 5.92 | 3.18 | 2.67 [-3.39,8.72] | 8.65 | 2.67 | 2.49 | 2.68 | 0.39 | 10.17 | -1.80 | 3.54 | -1077 |
| any ORB Lx1 30m behind <= 20 pts AND space ahead (no trusted reversal POI) | 3% | 9.0 | 5.44 | 3.20 | 2.18 [-4.14,8.50] | 9.02 | 2.17 | 2.01 | 2.20 | -1.13 | 7.73 | -1.39 | 1.97 | -1084 |
| mit ORB Lx1 30m behind <= 20 pts | 3% | 9.6 | 5.92 | 3.18 | 2.67 [-3.39,8.72] | 8.65 | 2.67 | 2.49 | 2.68 | 0.39 | 10.17 | -1.80 | 3.54 | -1077 |
| mit ORB Lx1 30m behind <= 20 pts AND space ahead (no trusted reversal POI) | 3% | 9.0 | 5.44 | 3.20 | 2.18 [-4.14,8.50] | 9.02 | 2.17 | 2.01 | 2.20 | -1.13 | 7.73 | -1.39 | 1.97 | -1084 |
| fresh ARR iplFVG 45s behind <= 5 pts | 6% | 22.5 | 5.14 | 3.13 | 1.88 [-3.01,6.77] | 6.98 | 1.88 | 1.85 | 1.92 | 3.02 | 7.85 | 0.10 | 1.49 | -1018 |
| fresh ARR iplFVG 45s behind <= 5 pts AND space ahead (no trusted reversal POI) | 6% | 19.2 | 5.78 | 3.11 | 2.53 [-2.45,7.50] | 7.11 | 2.51 | 2.45 | 2.56 | 4.73 | 8.94 | 0.68 | 0.62 | -1022 |
| book flag=dflip10 | 10% | 34.2 | 4.26 | 3.15 | 1.00 [-3.01,5.02] | 5.74 | 1.02 | 1.00 | 1.02 | 3.14 | 3.25 | 1.52 | -8.14 | -988 |
| book flag=dflip10 AND space ahead (no trusted reversal POI) | 9% | 31.7 | 4.88 | 3.10 | 1.62 [-2.21,5.45] | 5.47 | 1.63 | 1.60 | 1.65 | 4.04 | 5.35 | 2.08 | -8.66 | -979 |
| mit FIB ote79_up 1h behind <= 5 pts | 1% | 4.0 | -2.92 | 3.33 | -6.18 [-16.26,3.90] | 14.40 | -6.21 | -5.85 | -6.24 | 9.57 | 8.01 | -4.25 | -26.11 | -1145 |
| mit FIB ote79_up 1h behind <= 5 pts AND space ahead (no trusted reversal POI) | 1% | 3.4 | 2.63 | 3.26 | -0.62 [-10.59,9.34] | 14.24 | -0.58 | -0.49 | -0.62 | 10.45 | 8.88 | 0.56 | -18.74 | -1124 |
| mit SWG f7H 1m behind <= 10 pts | 70% | 242.3 | 3.61 | 2.45 | 0.35 [-0.70,1.41] | 1.51 | 0.36 | 0.35 | 0.36 | 0.48 | 1.71 | 0.35 | -0.70 | -258 |
| mit SWG f7H 1m behind <= 10 pts AND space ahead (no trusted reversal POI) | 61% | 213.6 | 4.24 | 1.69 | 0.99 [-0.48,2.45] | 2.10 | 0.98 | 0.96 | 1.00 | 0.85 | 3.18 | 0.89 | -0.95 | -227 |
| any FIB ote79_up 1h behind <= 5 pts | 1% | 4.2 | -1.79 | 3.32 | -5.05 [-15.01,4.92] | 14.24 | -5.06 | -4.76 | -5.09 | 10.20 | 6.79 | -3.31 | -24.04 | -1141 |
| any FIB ote79_up 1h behind <= 5 pts AND space ahead (no trusted reversal POI) | 1% | 3.5 | 4.40 | 3.25 | 1.14 [-8.71,10.99] | 14.07 | 1.21 | 1.20 | 1.16 | 11.15 | 7.53 | 2.12 | -14.31 | -1118 |
| PRF-class POI behind <= 10 AND book defS | 20% | 71.2 | 4.05 | 3.05 | 0.80 [-1.15,2.74] | 2.78 | 0.81 | 0.78 | 0.82 | 2.25 | 0.80 | 0.11 | 4.24 | -845 |
| PRF-class POI behind <= 10 AND book defS AND space ahead (no trusted reversal POI) | 19% | 64.5 | 4.19 | 3.05 | 0.93 [-1.35,3.21] | 3.25 | 0.95 | 0.91 | 0.95 | 2.83 | 1.23 | 0.20 | 3.01 | -863 |
| any SWG f7H 1m behind <= 10 pts | 70% | 244.2 | 3.58 | 2.51 | 0.32 [-0.72,1.35] | 1.48 | 0.32 | 0.32 | 0.33 | 0.49 | 1.48 | 0.34 | -0.72 | -260 |
| any SWG f7H 1m behind <= 10 pts AND space ahead (no trusted reversal POI) | 62% | 215.3 | 4.21 | 1.71 | 0.95 [-0.48,2.39] | 2.04 | 0.95 | 0.93 | 0.97 | 0.86 | 2.93 | 0.87 | -0.97 | -226 |
| fresh ARR iplFVG 45s behind <= 15 pts | 22% | 75.6 | 4.38 | 2.95 | 1.12 [-1.42,3.66] | 3.63 | 1.11 | 1.10 | 1.14 | 2.08 | 1.75 | 0.68 | 1.53 | -803 |
| fresh ARR iplFVG 45s behind <= 15 pts AND space ahead (no trusted reversal POI) | 19% | 66.4 | 4.88 | 2.88 | 1.62 [-0.97,4.21] | 3.70 | 1.61 | 1.58 | 1.65 | 3.03 | 2.88 | 1.05 | 1.31 | -810 |

Adding "space ahead" to the 20 B1 locations changes add_pl by (mean): PRE 0.37, HOLD 0.71, L6M 0.74 pts per planned lot; share of the 20 improved in L6M 70%.

### Base W0

| cell | keep | tpw | kept | skipped | add_L6M | MDE | add_pc | M | LIVE | PRE | Xp | HOLD | Y26 | gain_wk |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| space ahead only (no trusted reversal POI within min(td,20)) | 90% | 314.4 | 3.59 | -0.18 | 0.36 [-0.19,0.91] | 0.78 | 0.38 | 0.35 | 0.37 | 0.42 | 1.25 | 0.34 | -0.29 | 6 |
| support behind (fresh PDX-class <=5 or fresh 1-h POI <=5) | 2% | 5.6 | 8.83 | 3.13 | 5.60 [-3.72,14.93] | 13.32 | 6.04 | 5.45 | 5.67 | -7.77 | -0.80 | 3.50 | 3.73 | -1072 |
| support behind AND space ahead | 1% | 4.6 | 12.17 | 3.10 | 8.95 [-0.00,17.90] | 12.79 | 9.41 | 8.65 | 9.05 | -7.27 | 1.97 | 6.00 | 0.17 | -1065 |
| book flag=dflip10 | 10% | 34.2 | 3.77 | 3.16 | 0.55 [-3.06,4.16] | 5.15 | 0.63 | 0.57 | 0.57 | 3.15 | 2.84 | 1.05 | -8.04 | -992 |
| book flag=dflip10 AND space ahead (no trusted reversal POI) | 9% | 31.7 | 4.39 | 3.11 | 1.17 [-2.29,4.63] | 4.94 | 1.29 | 1.17 | 1.20 | 4.01 | 4.77 | 1.60 | -8.22 | -982 |
| fresh ARR iplFVG 45s behind <= 5 pts | 6% | 22.5 | 5.60 | 3.06 | 2.38 [-2.52,7.28] | 6.99 | 2.49 | 2.29 | 2.42 | 2.55 | 7.44 | 0.81 | 0.35 | -995 |
| fresh ARR iplFVG 45s behind <= 5 pts AND space ahead (no trusted reversal POI) | 6% | 19.2 | 5.83 | 3.07 | 2.61 [-2.40,7.61] | 7.15 | 2.70 | 2.49 | 2.64 | 4.30 | 8.68 | 1.07 | 0.33 | -1009 |
| mit FIB ote79_up 1h behind <= 5 pts | 1% | 4.0 | -2.80 | 3.29 | -6.03 [-16.35,4.30] | 14.75 | -6.56 | -5.63 | -6.07 | 9.70 | 7.00 | -4.00 | -21.33 | -1133 |
| mit FIB ote79_up 1h behind <= 5 pts AND space ahead (no trusted reversal POI) | 1% | 3.4 | 0.87 | 3.25 | -2.36 [-12.02,7.30] | 13.80 | -2.48 | -2.08 | -2.36 | 10.73 | 7.95 | -0.90 | -13.63 | -1119 |
| any FIB ote79_up 1h behind <= 5 pts | 1% | 4.2 | -1.67 | 3.28 | -4.89 [-15.16,5.37] | 14.67 | -5.30 | -4.55 | -4.93 | 10.20 | 5.65 | -3.07 | -19.60 | -1128 |
| any FIB ote79_up 1h behind <= 5 pts AND space ahead (no trusted reversal POI) | 1% | 3.5 | 2.65 | 3.23 | -0.57 [-10.17,9.03] | 13.71 | -0.47 | -0.37 | -0.55 | 11.28 | 6.73 | 0.67 | -9.56 | -1112 |
| fresh ARR iplFVG 45s behind <= 15 pts | 22% | 75.6 | 4.79 | 2.79 | 1.57 [-0.71,3.85] | 3.26 | 1.63 | 1.51 | 1.60 | 1.78 | 1.92 | 1.05 | 0.87 | -759 |
| fresh ARR iplFVG 45s behind <= 15 pts AND space ahead (no trusted reversal POI) | 19% | 66.4 | 5.01 | 2.80 | 1.79 [-0.49,4.07] | 3.25 | 1.87 | 1.72 | 1.82 | 2.67 | 3.03 | 1.19 | 1.07 | -789 |
| mit SWG f7H 1m behind <= 10 pts | 70% | 242.3 | 3.72 | 2.07 | 0.50 [-0.50,1.50] | 1.43 | 0.54 | 0.49 | 0.51 | 0.43 | 1.57 | 0.51 | -1.02 | -219 |
| mit SWG f7H 1m behind <= 10 pts AND space ahead (no trusted reversal POI) | 61% | 213.6 | 4.33 | 1.47 | 1.10 [-0.29,2.49] | 1.99 | 1.17 | 1.07 | 1.12 | 0.84 | 2.99 | 1.01 | -1.08 | -198 |
| fresh ARR iFVG 45s behind <= 20 pts | 37% | 128.7 | 4.03 | 2.75 | 0.81 [-1.16,2.78] | 2.81 | 0.85 | 0.76 | 0.82 | 1.43 | 1.33 | 0.52 | 2.00 | -602 |
| fresh ARR iFVG 45s behind <= 20 pts AND space ahead (no trusted reversal POI) | 33% | 114.0 | 4.71 | 2.50 | 1.48 [-0.55,3.52] | 2.91 | 1.57 | 1.42 | 1.50 | 2.31 | 2.88 | 1.11 | 1.76 | -585 |
| fresh ARR iplFVG 45s behind <= 20 pts | 28% | 98.6 | 4.07 | 2.89 | 0.85 [-1.00,2.69] | 2.63 | 0.87 | 0.82 | 0.86 | 1.08 | 1.97 | 0.28 | 1.24 | -720 |
| fresh ARR iplFVG 45s behind <= 20 pts AND space ahead (no trusted reversal POI) | 25% | 86.5 | 4.17 | 2.91 | 0.94 [-0.97,2.86] | 2.74 | 0.97 | 0.91 | 0.96 | 1.83 | 2.87 | 0.33 | 1.15 | -761 |
| fresh ARR iFVG 30s behind <= 15 pts | 37% | 130.0 | 3.90 | 2.82 | 0.68 [-0.97,2.33] | 2.36 | 0.72 | 0.62 | 0.69 | 1.04 | 1.72 | 0.23 | 1.20 | -614 |
| fresh ARR iFVG 30s behind <= 15 pts AND space ahead (no trusted reversal POI) | 33% | 115.6 | 4.52 | 2.58 | 1.30 [-0.58,3.18] | 2.69 | 1.37 | 1.21 | 1.32 | 1.90 | 3.01 | 0.81 | 1.70 | -599 |
| OTE 1h | 2% | 6.3 | -1.25 | 3.31 | -4.47 [-15.00,6.05] | 15.03 | -4.80 | -4.26 | -4.51 | 8.21 | 6.45 | -2.85 | -10.50 | -1129 |
| OTE 1h AND space ahead (no trusted reversal POI) | 2% | 5.5 | -2.19 | 3.31 | -5.42 [-16.25,5.42] | 15.48 | -5.80 | -5.17 | -5.47 | 9.04 | 9.48 | -3.61 | -8.29 | -1134 |

Adding "space ahead" to the 20 B1 locations changes add_pl by (mean): PRE 0.66, HOLD 0.58, L6M 0.72 pts per planned lot; share of the 20 improved in L6M 85%.

## 7. WALK-FORWARD RE-SELECTION CHAIN of the top-10 locations (B7)
Each month from 2024-02, the 10 best of the 11,422 locations by trailing add (n_kept>=100, keep<=85%, score add*sqrt(n)) on trades CLOSED before the refit; policy `any` = take if any of the 10 is true, `count` = size 1+0.25(count-1) capped 2, 0 if none. Lookbacks: anchored, rolling 12/6/3 months. No selection among the chain settings (all printed); every window from 2024-02 is out of sample.

| base | lookback | policy | keep | tpw | eq_add_PRE | eq_add_HOLD | eq_add_L6M | eq_add_pc_L6M | M | LIVE | Y26 | L3M_view | raw_wk_L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M0 | anch | any | 38% | 133.0 | -0.64 | 0.21 | 0.62 [-1.58,2.83] | 0.62 | 0.62 | 0.64 | -4.40 | -1.01 | -615 |
| M0 | anch | count | 38% | 133.0 | -0.72 | -0.02 | 0.54 [-1.65,2.73] | 0.54 | 0.54 | 0.55 | -4.75 | -1.14 | -584 |
| M0 | r12 | any | 19% | 67.4 | 0.42 | -0.00 | 0.61 [-3.25,4.48] | 0.61 | 0.59 | 0.61 | -8.69 | -1.52 | -869 |
| M0 | r12 | count | 19% | 67.4 | 0.41 | 0.13 | 0.85 [-2.99,4.69] | 0.85 | 0.82 | 0.85 | -9.65 | -1.43 | -771 |
| M0 | r6 | any | 31% | 107.2 | 0.23 | 0.26 | 0.24 [-3.13,3.61] | 0.24 | 0.24 | 0.24 | -1.39 | 1.20 | -755 |
| M0 | r6 | count | 31% | 107.2 | 0.12 | -0.34 | -0.31 [-4.08,3.46] | -0.31 | -0.28 | -0.31 | -0.68 | 1.06 | -693 |
| M0 | r3 | any | 29% | 101.0 | -0.14 | -0.04 | 0.04 [-2.39,2.48] | 0.04 | 0.04 | 0.04 | -3.16 | 0.38 | -797 |
| M0 | r3 | count | 29% | 101.0 | -0.10 | 0.18 | 0.59 [-2.27,3.46] | 0.59 | 0.57 | 0.59 | -3.12 | 0.59 | -650 |
| S73 | anch | any | 37% | 129.3 | -0.13 | 0.20 | 0.34 [-2.00,2.68] | 0.35 | 0.35 | 0.36 | -4.65 | -0.95 | -668 |
| S73 | anch | count | 37% | 129.3 | -0.43 | 0.02 | 0.23 [-2.04,2.49] | 0.23 | 0.24 | 0.24 | -4.85 | -1.00 | -648 |
| S73 | r12 | any | 23% | 78.8 | 0.03 | 0.50 | 0.40 [-2.95,3.75] | 0.41 | 0.38 | 0.40 | -3.65 | -0.66 | -845 |
| S73 | r12 | count | 23% | 78.8 | 0.22 | 0.48 | 0.56 [-2.73,3.85] | 0.57 | 0.54 | 0.56 | -4.35 | -0.71 | -770 |
| S73 | r6 | any | 32% | 112.5 | 0.48 | 0.51 | 0.55 [-2.63,3.73] | 0.55 | 0.55 | 0.56 | -1.75 | 1.85 | -705 |
| S73 | r6 | count | 32% | 112.5 | 0.20 | -0.05 | -0.02 [-3.65,3.62] | -0.01 | 0.01 | -0.01 | -0.99 | 1.55 | -638 |
| S73 | r3 | any | 32% | 112.2 | -0.53 | 0.47 | 0.45 [-1.93,2.82] | 0.46 | 0.44 | 0.45 | -1.83 | 1.68 | -718 |
| S73 | r3 | count | 32% | 112.2 | -0.44 | 0.41 | 0.67 [-2.10,3.43] | 0.67 | 0.65 | 0.67 | -2.37 | 1.60 | -591 |

Last re-fit (2026-02, base S73, rolling 6 m) picked: any FIB ext200 15m behind <= 20 pts; mit FIB ext200 15m behind <= 20 pts; fresh any 10m POI behind <= 20 pts; fresh SWG f5L 5m behind <= 20 pts; fresh PRF b2 day behind <= 15 pts; fresh SWG f3L 10m behind <= 20 pts; fresh ARR iplFVG 30m behind <= 20 pts; any FIB ote705_up 1d behind <= 15 pts; any MAS ema50 1h behind <= 15 pts; mit FIB ote705_up 1d behind <= 15 pts

Chain churn (S73, r6): mean Jaccard overlap of consecutive months' top-10 = 0.26 (1 = same ten each month).

## 8. EXTENSION location (B9; a post-hoc family, SECOND look on the premium/discount family - see DECISIONS.md disclosure)
Motivation: in section A (PRE and X' only) the ADVERSE side of premium/discount is the positive one: signals fired at the extreme of the dealing range in the signal direction (long near the high / short near the low) do better than signals fired in discount; deep discount (<= 0.2) is negative (-2 to -9 pts per contract) in PRE and X'. The B6 distillation independently returned "side-aligned position in the weekly range > 0.86" as its best single rule. B9 tests it as a take-only rule: disc >= 0.667/0.8/0.9/1.0 (1.0 = at/outside the swing-range extreme) on 10 dealing ranges, same eligibility and rank as B1. Prior-day/week/session ranges are live in D6.

### Base M0: 15 eligible/selected pooled cells

| location | keep | tpw | kept | skipped | add_L6M | MDE | add_pc | M | LIVE | PRE | Xp | HOLD | Y26 | L3M_view | gain_wk | tier | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| tf=week|disc>=0.9 | 27% | 93.6 | 5.60 | 2.38 | 2.35 [-1.47,6.17] | 5.45 | 2.35 | 2.29 | 2.39 | 3.48 | 1.72 | 2.61 | -5.29 | -0.45 | -605 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=1d|disc>=0.9 | 29% | 102.4 | 2.67 | 3.49 | -0.58 [-4.00,2.85] | 4.89 | -0.58 | -0.55 | -0.58 | 1.96 | 3.28 | -0.29 | -2.25 | -1.89 | -856 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=4h|disc>=1.0 | 30% | 103.0 | 3.21 | 3.26 | -0.03 [-4.07,4.00] | 5.76 | -0.03 | -0.01 | -0.03 | 1.86 | 1.95 | -0.10 | -6.07 | -2.62 | -798 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=1d|disc>=0.8 | 34% | 118.3 | 3.72 | 3.00 | 0.47 [-2.40,3.35] | 4.11 | 0.47 | 0.47 | 0.49 | 0.46 | 3.35 | 0.25 | -3.33 | -1.41 | -689 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=day|disc>=0.9 | 34% | 119.9 | 2.86 | 3.45 | -0.38 [-2.35,1.59] | 2.82 | -0.38 | -0.35 | -0.38 | 1.22 | 1.21 | -0.03 | -0.32 | -0.25 | -786 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=15m|disc>=0.667 | 80% | 279.7 | 3.64 | 1.62 | 0.40 [-0.27,1.07] | 0.96 | 0.40 | 0.38 | 0.40 | 0.41 | 0.03 | 0.39 | 0.78 | 0.56 | -110 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=week|disc>=0.8 | 40% | 137.8 | 4.65 | 2.32 | 1.41 [-1.47,4.28] | 4.11 | 1.41 | 1.37 | 1.43 | 1.27 | 1.00 | 1.48 | -1.84 | 0.80 | -488 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=1d|disc>=0.667 | 43% | 149.8 | 2.77 | 3.60 | -0.47 [-3.24,2.29] | 3.95 | -0.47 | -0.44 | -0.47 | 0.54 | 2.87 | -0.67 | -3.70 | -1.97 | -714 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=1d|disc>=1.0 | 24% | 85.2 | 0.87 | 4.01 | -2.37 [-6.85,2.10] | 6.39 | -2.37 | -2.28 | -2.39 | 1.46 | 2.02 | -2.00 | -5.77 | -5.02 | -1054 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=4h|disc>=0.9 | 36% | 123.9 | 2.85 | 3.46 | -0.39 [-3.84,3.06] | 4.93 | -0.39 | -0.36 | -0.39 | 1.21 | 1.78 | -0.47 | -4.64 | -2.02 | -775 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=week|disc>=1.0 | 2% | 5.9 | 6.34 | 3.19 | 3.09 [-3.78,9.97] | 9.82 | 3.09 | 3.09 | 3.13 | 5.31 | 0.24 | 2.39 | 15.63 | -0.53 | -1091 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=pweek|disc>=0.8 | 36% | 124.9 | 4.11 | 2.76 | 0.87 [-1.91,3.64] | 3.96 | 0.87 | 0.85 | 0.88 | 1.09 | 1.26 | 0.78 | -2.63 | -0.72 | -615 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=pweek|disc>=0.667 | 44% | 152.1 | 2.94 | 3.48 | -0.30 [-2.76,2.15] | 3.51 | -0.30 | -0.28 | -0.30 | 0.96 | 0.70 | -0.46 | -2.42 | -1.57 | -682 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=sess|disc>=0.8 | 58% | 201.2 | 3.98 | 2.24 | 0.74 [-0.73,2.20] | 2.10 | 0.74 | 0.71 | 0.74 | 0.54 | 0.20 | 0.77 | 3.96 | 1.50 | -328 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=week|disc>=0.667 | 52% | 181.7 | 4.67 | 1.69 | 1.43 [-0.42,3.27] | 2.64 | 1.43 | 1.38 | 1.45 | 0.72 | 0.50 | 1.14 | -1.55 | 1.29 | -280 | SIGN-ONLY | placebo,RW,stack,CI>0 |

### Base S73: 15 eligible/selected pooled cells

| location | keep | tpw | kept | skipped | add_L6M | MDE | add_pc | M | LIVE | PRE | Xp | HOLD | Y26 | L3M_view | gain_wk | tier | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| tf=week|disc>=0.9 | 27% | 93.6 | 5.49 | 2.44 | 2.23 [-1.58,6.04] | 5.45 | 2.23 | 2.17 | 2.27 | 3.40 | 1.60 | 2.51 | -5.39 | -0.45 | -620 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=1d|disc>=0.9 | 29% | 102.4 | 2.68 | 3.50 | -0.58 [-3.96,2.80] | 4.83 | -0.58 | -0.55 | -0.58 | 1.89 | 3.36 | -0.29 | -2.40 | -1.78 | -859 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=4h|disc>=1.0 | 30% | 103.0 | 3.11 | 3.32 | -0.15 [-4.19,3.90] | 5.78 | -0.15 | -0.12 | -0.14 | 2.00 | 1.78 | -0.20 | -6.16 | -2.64 | -813 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=1d|disc>=0.8 | 34% | 118.3 | 3.70 | 3.03 | 0.44 [-2.39,3.27] | 4.04 | 0.44 | 0.44 | 0.45 | 0.41 | 3.36 | 0.22 | -3.53 | -1.37 | -696 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=day|disc>=0.9 | 34% | 119.9 | 2.62 | 3.59 | -0.63 [-2.63,1.36] | 2.85 | -0.63 | -0.59 | -0.63 | 1.12 | 1.04 | -0.30 | -0.74 | -0.54 | -819 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=1d|disc>=1.0 | 24% | 85.2 | 0.85 | 4.04 | -2.40 [-6.83,2.03] | 6.33 | -2.40 | -2.31 | -2.43 | 1.38 | 2.15 | -2.02 | -5.77 | -4.88 | -1061 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=week|disc>=0.8 | 40% | 137.8 | 4.71 | 2.31 | 1.45 [-1.42,4.32] | 4.10 | 1.45 | 1.41 | 1.48 | 1.20 | 1.00 | 1.52 | -2.09 | 0.88 | -485 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=4h|disc>=0.9 | 36% | 123.9 | 2.74 | 3.55 | -0.52 [-4.00,2.95] | 4.97 | -0.52 | -0.48 | -0.52 | 1.23 | 1.64 | -0.58 | -4.96 | -2.11 | -794 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=1d|disc>=0.667 | 43% | 149.8 | 2.64 | 3.72 | -0.62 [-3.38,2.15] | 3.95 | -0.61 | -0.58 | -0.62 | 0.51 | 2.72 | -0.78 | -4.09 | -2.03 | -738 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=pweek|disc>=0.8 | 36% | 124.9 | 4.11 | 2.78 | 0.85 [-1.89,3.59] | 3.91 | 0.85 | 0.84 | 0.86 | 1.06 | 1.22 | 0.78 | -2.87 | -0.70 | -621 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=pweek|disc>=0.667 | 44% | 152.1 | 2.92 | 3.52 | -0.34 [-2.79,2.11] | 3.50 | -0.34 | -0.31 | -0.34 | 0.94 | 0.69 | -0.47 | -2.69 | -1.54 | -690 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=sess|disc>=0.8 | 58% | 201.2 | 3.78 | 2.54 | 0.53 [-0.93,1.99] | 2.08 | 0.53 | 0.51 | 0.53 | 0.54 | 0.03 | 0.58 | 3.82 | 1.20 | -372 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=week|disc>=0.667 | 52% | 181.7 | 4.69 | 1.69 | 1.43 [-0.40,3.27] | 2.62 | 1.43 | 1.39 | 1.46 | 0.66 | 0.47 | 1.13 | -1.74 | 1.26 | -282 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=4h|disc>=0.8 | 43% | 148.1 | 3.44 | 3.13 | 0.18 [-2.83,3.19] | 4.30 | 0.18 | 0.19 | 0.19 | 0.42 | 1.61 | 0.07 | -3.33 | -1.98 | -624 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=day|disc>=0.8 | 53% | 184.3 | 3.25 | 3.27 | -0.01 [-1.52,1.49] | 2.15 | -0.01 | -0.01 | -0.01 | 0.36 | 0.44 | 0.10 | -0.55 | -1.36 | -535 | BEST-AVAILABLE-NEGATIVE | L6M+/units,M&L+,placebo,RW,stack,CI>0 |

### Base W0: 15 eligible/selected pooled cells

| location | keep | tpw | kept | skipped | add_L6M | MDE | add_pc | M | LIVE | PRE | Xp | HOLD | Y26 | L3M_view | gain_wk | tier | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| tf=week|disc>=0.9 | 27% | 93.6 | 5.23 | 2.48 | 2.01 [-1.50,5.52] | 5.02 | 2.14 | 1.95 | 2.04 | 3.17 | 1.60 | 2.23 | -4.86 | -0.35 | -632 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=1d|disc>=0.9 | 29% | 102.4 | 2.73 | 3.43 | -0.49 [-3.39,2.41] | 4.15 | -0.52 | -0.45 | -0.49 | 1.86 | 2.97 | -0.22 | -1.91 | -1.34 | -842 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=4h|disc>=1.0 | 30% | 103.0 | 3.34 | 3.17 | 0.12 [-3.49,3.73] | 5.16 | 0.11 | 0.13 | 0.12 | 2.13 | 1.76 | 0.08 | -4.86 | -1.97 | -777 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=1d|disc>=0.8 | 34% | 118.3 | 3.73 | 2.96 | 0.51 [-1.88,2.90] | 3.42 | 0.56 | 0.51 | 0.52 | 0.60 | 3.09 | 0.32 | -3.01 | -1.04 | -680 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=4h|disc>=0.9 | 36% | 123.9 | 2.70 | 3.51 | -0.53 [-3.63,2.58] | 4.44 | -0.56 | -0.49 | -0.53 | 1.26 | 1.54 | -0.57 | -4.36 | -1.88 | -787 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=1d|disc>=1.0 | 24% | 85.2 | 1.09 | 3.92 | -2.14 [-5.95,1.68] | 5.45 | -2.28 | -2.04 | -2.16 | 1.38 | 1.90 | -1.80 | -4.80 | -4.10 | -1029 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=1d|disc>=0.667 | 43% | 149.8 | 2.66 | 3.65 | -0.56 [-3.00,1.88] | 3.48 | -0.59 | -0.52 | -0.56 | 0.62 | 2.20 | -0.64 | -3.81 | -1.81 | -723 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=week|disc>=0.8 | 40% | 137.8 | 4.72 | 2.25 | 1.49 [-1.07,4.05] | 3.66 | 1.60 | 1.45 | 1.52 | 1.08 | 0.98 | 1.50 | -1.45 | 1.25 | -472 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=pweek|disc>=0.8 | 36% | 124.9 | 4.04 | 2.76 | 0.82 [-1.59,3.23] | 3.44 | 0.90 | 0.81 | 0.84 | 1.15 | 0.92 | 0.82 | -2.30 | -0.40 | -616 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=day|disc>=0.9 | 34% | 119.9 | 2.23 | 3.75 | -0.99 [-2.82,0.84] | 2.61 | -1.06 | -0.94 | -1.00 | 0.92 | 0.73 | -0.70 | -1.18 | -0.98 | -854 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=pweek|disc>=0.667 | 44% | 152.1 | 2.96 | 3.43 | -0.27 [-2.46,1.93] | 3.14 | -0.27 | -0.24 | -0.26 | 0.91 | 0.39 | -0.30 | -2.09 | -1.18 | -672 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=week|disc>=0.667 | 52% | 181.7 | 4.68 | 1.63 | 1.46 [-0.16,3.08] | 2.31 | 1.57 | 1.41 | 1.48 | 0.68 | 0.45 | 1.13 | -1.27 | 1.46 | -271 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=4h|disc>=0.8 | 43% | 148.1 | 3.53 | 3.00 | 0.30 [-2.30,2.91] | 3.72 | 0.32 | 0.31 | 0.31 | 0.46 | 1.56 | 0.18 | -2.98 | -1.54 | -599 | SIGN-ONLY | placebo,RW,stack,CI>0 |
| tf=pday|disc>=1.0 | 27% | 93.6 | 3.15 | 3.25 | -0.07 [-3.61,3.47] | 5.06 | -0.10 | -0.06 | -0.06 | 1.00 | 0.17 | -0.22 | -4.10 | -2.08 | -826 | BEST-AVAILABLE-NEGATIVE | L6M+/units,HOLD+,M&L+,placebo,RW,stack,CI>0 |
| tf=pday|disc>=0.9 | 34% | 119.9 | 3.21 | 3.23 | -0.02 [-3.33,3.30] | 4.74 | -0.01 | 0.00 | -0.01 | 0.76 | 0.29 | 0.16 | -4.19 | -1.46 | -737 | BEST-AVAILABLE-NEGATIVE | L6M+/units,M&L+,placebo,RW,stack,CI>0 |

## 9. LEARNED location model, walk-forward (B6)
LightGBM (fixed: 300 trees, depth 4, lr 0.03, min leaf 100, subsample/colsample 0.7, L2 10) of the base pts per planned lot from ALL location features (premium/discount x10 ranges, OTE, HTF Supertrend/EMA/Ichimoku/BOS x5 TF, POI-behind distance/age/count per class, book flags, L2 imbalance/absorption/pull) + book/side/session/minute/sd/td; refit monthly from 2024-02 on trades CLOSED before the refit (anchored; roll12 = rolling 12 months); thresholds from the model's predictions on the last 2 months of the training set; policy by quantile: skip < q30, half < q50, full < q80, 1.5x < q92, 2x above (`graded`); `takeonly` = skip bucket only; `sizeonly` = skip bucket treated as full. **No parameter was tuned and nothing was selected, so every window from 2024-02 is out of sample.** `noloc` = the same model without any location feature (signal quality only: book, side, session, minute, sd, td); `shuf` = the location block permuted jointly within book x session x week (the shuffled-location placebo). eq_add = gain per unit of exposure at equal total lots.

### Base S73

| model | policy | keep | tpw | expo | eq_add_L6M | MDE | eq_add_pc | M | LIVE | PRE_oos | HOLD | Y26 | L3M_view | raw_wk_L6M | stackD_L6M_HOLD_PRE |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| real | graded | 68% | 235.7 | 0.70 | -0.19 [-2.16,1.77] | 2.80 | -0.19 | -0.18 | -0.19 | 0.06 | -0.41 | -2.28 | -1.28 | -390 | -25695 / -24137 / -765 |
| real | takeonly | 68% | 235.7 | 0.68 | -0.34 [-1.57,0.89] | 1.75 | -0.34 | -0.33 | -0.34 | -0.07 | -0.29 | -1.30 | -0.92 | -446 | -29895 / -24577 / -12606 |
| real | sizeonly | 100% | 347.9 | 1.02 | 0.09 [-0.64,0.82] | 1.04 | 0.09 | 0.10 | 0.10 | 0.09 | -0.09 | -0.67 | -0.27 | 56 | 9535 / 4263 / 2602 |
| roll12 | graded | 67% | 233.6 | 0.69 | 0.73 [-0.99,2.45] | 2.45 | 0.74 | 0.71 | 0.74 | 0.17 | 0.52 | -2.15 | -0.09 | -178 | -13413 / -6136 / -11962 |
| roll12 | takeonly | 67% | 233.6 | 0.67 | 0.28 [-0.52,1.08] | 1.14 | 0.29 | 0.27 | 0.28 | -0.35 | 0.09 | -0.10 | 0.14 | -307 | -19658 / -16701 / -19658 |
| roll12 | sizeonly | 100% | 347.9 | 1.02 | 0.31 [-0.53,1.15] | 1.20 | 0.31 | 0.30 | 0.31 | 0.35 | 0.30 | -1.29 | -0.16 | 129 | -1780 / 3200 / 2783 |
| noloc | graded | 70% | 245.2 | 0.75 | 0.44 [-0.80,1.68] | 1.77 | 0.44 | 0.41 | 0.43 | -0.96 | 0.59 | -0.07 | 1.22 | -171 | -9978 / -4969 / -35245 |
| noloc | takeonly | 70% | 245.2 | 0.70 | 0.01 [-0.91,0.94] | 1.32 | 0.02 | -0.00 | 0.01 | -0.06 | 0.15 | 0.29 | 0.52 | -331 | -17381 / -12587 / -21496 |
| noloc | sizeonly | 100% | 347.9 | 1.04 | 0.31 [-0.30,0.91] | 0.87 | 0.31 | 0.30 | 0.31 | -0.64 | 0.32 | -0.25 | 0.53 | 160 | 2151 / -992 / -23148 |

Shuffled-location placebo (S73): rank of the real location model among the shuffled-location draws (1/n+1 best)

| policy | window | real | no_location_model | shuffled_mean | shuffled_max | n_draws | rank |
|---|---|---|---|---|---|---|---|
| graded | PRE | 0.06 | -0.96 | 0.62 | 1.26 | 10 | 11/11 |
| graded | HOLD | -0.41 | 0.59 | 1.13 | 1.87 | 10 | 11/11 |
| graded | L6M | -0.19 | 0.44 | 0.95 | 1.71 | 10 | 11/11 |
| sizeonly | PRE | 0.09 | -0.64 | 0.28 | 0.45 | 10 | 10/11 |
| sizeonly | HOLD | -0.09 | 0.32 | 0.41 | 0.64 | 10 | 11/11 |
| sizeonly | L6M | 0.09 | 0.31 | 0.34 | 0.60 | 10 | 11/11 |
| takeonly | PRE | -0.07 | -0.06 | 0.26 | 0.75 | 10 | 10/11 |
| takeonly | HOLD | -0.29 | 0.15 | 0.59 | 1.49 | 10 | 11/11 |
| takeonly | L6M | -0.34 | 0.01 | 0.50 | 1.28 | 10 | 11/11 |

Same placebo on the lock-engine stack ($/wk vs the S73 floor, window means):

| policy | window | real_stackD | no_location_stackD | shuffled_mean | shuffled_max | n_draws | rank |
|---|---|---|---|---|---|---|---|
| graded | PRE | -765 | -35245 | -10028 | 2716 | 10 | 2/11 |
| graded | HOLD | -24137 | -4969 | 7847 | 23703 | 10 | 11/11 |
| graded | L6M | -25695 | -9978 | 5371 | 21118 | 10 | 10/11 |
| sizeonly | PRE | 2602 | -23148 | -838 | 6388 | 10 | 4/11 |
| sizeonly | HOLD | 4263 | -992 | 1405 | 14599 | 10 | 5/11 |
| sizeonly | L6M | 9535 | 2151 | 2753 | 17624 | 10 | 4/11 |
| takeonly | PRE | -12606 | -21496 | -11334 | -1081 | 10 | 6/11 |
| takeonly | HOLD | -24577 | -12587 | 1427 | 15483 | 10 | 11/11 |
| takeonly | L6M | -29895 | -17381 | -3426 | 13254 | 10 | 11/11 |

### Base M0

| model | policy | keep | tpw | expo | eq_add_L6M | MDE | eq_add_pc | M | LIVE | PRE_oos | HOLD | Y26 | L3M_view | raw_wk_L6M | stackD_L6M_HOLD_PRE |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| real | graded | 67% | 232.1 | 0.69 | -0.39 [-2.49,1.71] | 3.00 | -0.39 | -0.37 | -0.39 | 0.11 | -0.69 | -3.03 | -1.70 | -444 | -28633 / -26258 / -5029 |
| real | takeonly | 67% | 232.1 | 0.67 | 0.10 [-1.37,1.57] | 2.09 | 0.10 | 0.09 | 0.10 | -0.37 | -0.10 | -1.74 | -0.84 | -352 | -19493 / -19585 / -18113 |
| real | sizeonly | 100% | 347.9 | 1.02 | -0.33 [-1.04,0.38] | 1.02 | -0.33 | -0.31 | -0.33 | 0.32 | -0.40 | -0.88 | -0.61 | -92 | -21726 / -19795 / 8542 |
| noloc | graded | 71% | 245.4 | 0.75 | 0.44 [-0.65,1.53] | 1.56 | 0.44 | 0.42 | 0.43 | -0.99 | 0.60 | 0.09 | 1.32 | -166 | 391 / 4653 / -45917 |
| noloc | takeonly | 71% | 245.4 | 0.71 | 0.19 [-0.60,0.98] | 1.13 | 0.19 | 0.16 | 0.18 | -0.15 | 0.24 | 0.53 | 0.69 | -286 | -423 / 168 / -24399 |
| noloc | sizeonly | 100% | 347.9 | 1.05 | 0.19 [-0.37,0.75] | 0.80 | 0.19 | 0.19 | 0.19 | -0.59 | 0.27 | -0.29 | 0.49 | 121 | -7950 / -6191 / -18511 |

Shuffled-location placebo (M0): rank of the real location model among the shuffled-location draws (1/n+1 best)

| policy | window | real | no_location_model | shuffled_mean | shuffled_max | n_draws | rank |
|---|---|---|---|---|---|---|---|
| graded | PRE | 0.11 | -0.99 | 0.86 | 1.32 | 5 | 6/6 |
| graded | HOLD | -0.69 | 0.60 | 1.60 | 1.84 | 5 | 6/6 |
| graded | L6M | -0.39 | 0.44 | 1.34 | 1.65 | 5 | 6/6 |
| sizeonly | PRE | 0.32 | -0.59 | 0.41 | 0.51 | 5 | 5/6 |
| sizeonly | HOLD | -0.40 | 0.27 | 0.53 | 0.68 | 5 | 6/6 |
| sizeonly | L6M | -0.33 | 0.19 | 0.44 | 0.55 | 5 | 6/6 |
| takeonly | PRE | -0.37 | -0.15 | 0.34 | 0.70 | 5 | 6/6 |
| takeonly | HOLD | -0.10 | 0.24 | 0.88 | 1.05 | 5 | 6/6 |
| takeonly | L6M | 0.10 | 0.19 | 0.75 | 0.98 | 5 | 6/6 |

Same placebo on the lock-engine stack ($/wk vs the M0 floor, window means):

| policy | window | real_stackD | no_location_stackD | shuffled_mean | shuffled_max | n_draws | rank |
|---|---|---|---|---|---|---|---|
| graded | PRE | -5029 | -45917 | -10698 | 7265 | 5 | 2/6 |
| graded | HOLD | -26258 | 4653 | 24851 | 29769 | 5 | 6/6 |
| graded | L6M | -28633 | 391 | 19820 | 26534 | 5 | 6/6 |
| sizeonly | PRE | 8542 | -18511 | -6265 | -2451 | 5 | 1/6 |
| sizeonly | HOLD | -19795 | -6191 | 21684 | 32476 | 5 | 6/6 |
| sizeonly | L6M | -21726 | -7950 | 20625 | 29688 | 5 | 6/6 |
| takeonly | PRE | -18113 | -24399 | -9796 | 1338 | 5 | 5/6 |
| takeonly | HOLD | -19585 | 168 | 919 | 19115 | 5 | 6/6 |
| takeonly | L6M | -19493 | -423 | -3341 | 14341 | 5 | 6/6 |

Top features at the LAST re-fit (S73, anchored; gain-count importance): ptsrange_1h (165), ptsrange_15m (136), disc_1d (127), ptsrange_4h (121), week_rng (108), pos_week (103), disc_pweek (101), disc_pday (101), disc_4h (98), pos_1d (93), disc_week (92), ptsrange_1d (90), disc_1h (81), disc_5m (80), pos_1h (76)

### Would a simpler rule do the same? (qv.distill: best 1- and 2-feature threshold rule fitted on PRE+X', evaluated on L6M / HOLD; 1,780-1,885 rules searched; the S73 entered-set mean is the base)

| base | eval | k | rule | fit_mean | fit_n | fit_all_mean | eval_mean | eval_n | eval_all_mean |
|---|---|---|---|---|---|---|---|---|---|
| M0 | L6M | 1 | disc_week > 0.8631 | 3.79 | 10916 | 1.33 | 4.87 | 3115 | 3.24 |
| M0 | L6M | 2 | disc_1d > 0.03956 AND sess < 4 | 3.37 | 19483 | 1.33 | 3.29 | 5990 | 3.24 |
| M0 | HOLD | 1 | disc_week > 0.8631 | 3.79 | 10916 | 1.33 | 4.27 | 3339 | 2.55 |
| M0 | HOLD | 2 | disc_1d > 0.03956 AND sess < 4 | 3.37 | 19483 | 1.33 | 2.29 | 6590 | 2.55 |
| S73 | L6M | 1 | disc_4h > 1.199 | 4.75 | 6652 | 1.27 | 3.89 | 2059 | 3.26 |
| S73 | L6M | 2 | sess < 4 AND disc_1d > 0.03956 | 3.26 | 19483 | 1.27 | 3.17 | 5990 | 3.26 |
| S73 | HOLD | 1 | disc_4h > 1.199 | 4.75 | 6652 | 1.27 | 3.03 | 2219 | 2.59 |
| S73 | HOLD | 2 | sess < 4 AND disc_1d > 0.03956 | 3.26 | 19483 | 1.27 | 2.23 | 6590 | 2.59 |
