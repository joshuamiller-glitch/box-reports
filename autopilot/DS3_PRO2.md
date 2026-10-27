# DS3 T-PULLBACK PRO, parts P2 (levels by the auction) and P3 (statistical pullback) - PRO2 (D3PRO2)
Generated 2026-10-27T04:44:42Z. Research only; nothing here is a live recommendation. DS2 bracket and execution fixed (60-pt stop, 1.0R, flat 16:55, 10 lots S10x1 + XJ, per-book locks, $4.84 RT), MAPPED pricing for all 104 scored cells, DIRECT L2 replay for the finalists.
Preregs (sha256 in autopilot/DECISIONS.md, written before any scoring): PRO2A 30 cells `9a8488d946d0`, PRO2B 17 cells `c0ad5c8bf9df`, PRO2C 28 cells `058421806469`, PRO2D 30 cells `bd19d187d8ed` = 105 cells (PRO2D = the directive's 3x3 grids around the four PASS cells, prereg'd after the PRE/holdout look, disclosed). Truncation-invariance audit (data cut at 62%): all 105 event lists and all 32 level series identical before the cut, 0 mismatches (out/PRO2/PRO2_trunc_audit.json).
Level series published for PRO1 / the learned detector: `l2vast/ds3/out/PRO_levels.parquet` (1.31M 1-min bars; per bar `bar_min`, `asof_ns` = bar close time, and per level type the price: VWAP, VWAP_m1/p1/m2/p2, AVWAP_flip, AVWAP_swL, AVWAP_swH, dPOC/dVAH/dVAL, pdPOC/pdVAH/pdVAL, HVN5_dn/up, LVN5_dn/up, ONH, ONL, FLIP, IMP38/50/62_up/dn, PPL_dn/up, CONF_dn/up and CONF_n_dn/up (cluster size), ST10). Every value at bar i uses bars <= i only (prior-session objects use completed sessions); float32; `_dn` = level below the prior close (support for a long), `_up` = above (resistance for a short).

## 1. Verdicts

Mapped rule (T-PULLBACK prereg rule: trades/wk >= 3, PRE > 0, WF week-block CI excludes 0, HOLD > 0, second holdout > 0, placebo rank on PRE >= 0.95, 2x-cost WF > 0; PASS all, CANDIDATE all but one): **4 PASS, 14 CANDIDATE, 86 DEAD** of 104 scored cells (+1 cell with < 100 trades: PRO_ER6_n40_EMA5, reported DEAD/too few). DIRECT L2 replay covers 14 finalist cells: PRO_EMA200_CONF2_T1 DEAD (cover 0.89), PRO_EMA200_dPOC_T1 DEAD (cover 0.90), PRO_ER4_EMA5 PASS (cover 0.93), PRO_ER5_EMA5 PASS (cover 0.93), PRO_KAL_k0.0 PASS (cover 0.87), PRO_KAL_k0.5 DEAD (cover 0.87), PRO_RIB1m_q20 DEAD (cover 0.89), PRO_RIB1m_q30 CANDIDATE (cover 0.89), PRO_RIB5m_q20 DEAD (cover 0.91), PRO_ST10_CONF2_T1_2nd DEAD (cover 0.90), PRO_ST10_CONF2_T2 DEAD (cover 0.90), PRO_Z120_t2.0 DEAD (cover 0.89), PRO_Z20_t1.0 CANDIDATE (cover 0.87), PRO_Z60_t1.0 CANDIDATE (cover 0.88).

**Best-of-N null.** N = 104 cells scored (ledger +105 trials: A 30, B 17, C 28, D 30). The null = maximum over the 104 cells of the PRE weekly mean of one timing-destroyed placebo draw per cell (4000 resamples): median $10,494/wk, 95th percentile $14,917/wk. The best real PRE weekly mean is $9,178/wk (`PRO_Z120_t1.5`): **no cell above the best-of-N 95% line** - the mapped PASS/CANDIDATE labels are therefore not evidence of an edge beyond what the best of 104 random-timing books would show. MDE (80% power, 5%, 2.8 x SE): WF weekly mean $2,406-15,422/wk; paired per trade vs ST 2.8-15.5 pt; vs the base pullback cell 0.0-33.6 pt. Every null below is read against those MDEs (a null here is not evidence of absence unless the effect predicted is above the MDE, which none was).

### 1a. PASS and CANDIDATE cells (mapped), all columns
| cell | grp | trades/wk | win% | PRE $k/wk | WF $k/wk [CI] | HOLD $k/wk | SPAN2 $k/wk | HOLD Sharpe | placebo PRE | 2x-cost WF $k | corr ST | paired vs ST pt [CI] / MDE | paired vs BASE pt [CI] / MDE | verdict (mapped) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PRO_KAL_s0.5_k0.25 | D | 31.2 | 52 | 7.9 | 16.7 [7.1,27.1] | 26.1 | -5.2 | 2.88 | 0.95 | 12.1 | 0.30 | 0.4 [-1.9,2.6] / 3.1 | -16.2 [-21.3,-11.1] / 7.1 | CANDIDATE |
| PRO_RIB1m_q30_M5 | D | 24.1 | 52 | 3.9 | 11.7 [2.2,21.0] | 19.9 | 4.2 | 2.59 | 0.85 | 8.6 | 0.44 | -6.6 [-9.1,-4.0] / 3.6 | -19.0 [-21.9,-16.1] / 4.3 | CANDIDATE |
| PRO_Z20_t1.0 | C | 31.5 | 51 | 8.9 | 13.8 [4.7,22.5] | 19.0 | -3.4 | 2.41 | 0.97 | 8.9 | 0.38 | 2.4 [-0.2,5.1] / 3.7 | -15.7 [-20.1,-11.3] / 6.5 | CANDIDATE |
| PRO_KAL_s0.5_k0.0 | D | 31.1 | 51 | 0.8 | 11.0 [1.4,21.4] | 22.0 | 3.0 | 2.41 | 0.72 | 8.0 | 0.27 | -1.6 [-3.6,0.5] / 3.0 | -19.9 [-25.0,-14.2] / 7.7 | CANDIDATE |
| PRO_RIB1m_q20 | C | 23.7 | 51 | 2.4 | 9.2 [0.7,17.9] | 16.4 | 4.5 | 2.39 | 0.82 | 6.2 | 0.40 | -7.7 [-10.3,-5.1] / 3.7 | -19.4 [-22.4,-16.3] / 4.4 | CANDIDATE |
| PRO_RIB1m_q25_M5 | D | 23.5 | 52 | 2.5 | 9.8 [0.4,19.1] | 17.7 | 1.8 | 2.31 | 0.60 | 6.6 | 0.41 | -6.7 [-9.0,-4.1] / 3.7 | -18.6 [-21.5,-15.8] / 4.0 | CANDIDATE |
| PRO_RIB1m_q25_M10 | D | 24.2 | 52 | 3.7 | 10.1 [1.4,19.5] | 16.9 | 2.0 | 2.28 | 0.93 | 6.2 | 0.42 | -7.0 [-9.4,-4.5] / 3.5 | -18.9 [-21.9,-16.0] / 4.3 | CANDIDATE |
| PRO_RIB1m_q30_M20 | D | 25.6 | 52 | 5.7 | 11.0 [1.3,20.6] | 16.7 | 6.0 | 2.24 | 0.90 | 8.5 | 0.47 | -7.4 [-9.9,-4.8] / 3.6 | -20.6 [-23.9,-17.3] / 4.7 | CANDIDATE |
| PRO_RIB1m_q35_M5 | D | 24.9 | 52 | 2.1 | 10.1 [0.6,20.3] | 18.6 | 3.3 | 2.23 | 0.70 | 7.2 | 0.47 | -7.6 [-10.0,-5.0] / 3.6 | -19.4 [-22.5,-16.4] / 4.2 | CANDIDATE |
| PRO_RIB1m_q30 | C | 24.8 | 52 | 5.4 | 10.3 [1.3,19.6] | 15.4 | 4.8 | 2.04 | 0.95 | 7.4 | 0.46 | -7.2 [-9.7,-4.8] / 3.6 | -20.0 [-22.9,-17.0] / 4.4 | PASS |
| PRO_RIB1m_q35_M20 | D | 26.2 | 51 | 4.8 | 10.8 [0.8,20.3] | 17.1 | 5.5 | 2.04 | 0.80 | 6.8 | 0.50 | -7.4 [-9.9,-4.8] / 3.6 | -20.4 [-23.5,-17.1] / 4.5 | CANDIDATE |
| PRO_Z60_t1.0 | C | 30.6 | 51 | 8.0 | 11.5 [1.9,21.3] | 15.2 | 6.3 | 1.91 | 0.97 | 7.0 | 0.39 | 9.4 [7.0,11.7] / 3.4 | -7.7 [-10.6,-4.9] / 4.1 | PASS |
| PRO_KAL_k0.0 | C | 32.0 | 51 | 8.0 | 13.0 [3.2,23.0] | 18.2 | 0.1 | 1.86 | 0.97 | 10.7 | 0.22 | -2.7 [-5.1,-0.4] / 3.4 | -18.6 [-23.6,-14.0] / 6.9 | PASS |
| PRO_ER5_EMA5 | C | 3.1 | 57 | 4.7 | 5.0 [1.8,8.6] | 5.2 | 2.2 | 1.77 | 1.00 | 4.4 | 0.24 | 17.4 [7.8,28.5] / 14.7 | -0.3 [-0.8,-0.0] / 0.6 | PASS |
| PRO_ER4_EMA5 | C | 7.8 | 53 | 5.8 | 5.6 [0.9,10.7] | 5.3 | -1.8 | 1.30 | 1.00 | 4.6 | 0.36 | 12.0 [6.6,17.4] / 7.9 | -0.4 [-0.7,-0.1] / 0.4 | CANDIDATE |
| PRO_ER4_n40_EMA5 | D | 2.8* | 56 | 5.7 | 4.5 [1.4,7.4] | 3.1 | 1.6 | 1.12 | 1.00 | 4.0 | 0.21 | 14.1 [4.4,24.6] / 14.1 | -0.6 [-1.0,-0.2] / 0.6 | CANDIDATE |
| PRO_ER6_n20_EMA5 | D | 0.9* | 60 | 2.2 | 2.0 [0.3,3.7] | 1.7 | 0.8 | 1.11 | 1.00 | 1.8 | 0.19 | nan [nan,nan] / nan | 0.0 [0.0,0.0] / 0.0 | CANDIDATE |
| PRO_Z120_t2.0 | C | 24.3 | 51 | 7.8 | 6.6 [-1.7,15.7] | 5.2 | 2.7 | 0.62 | 0.95 | 3.9 | 0.34 | 14.8 [11.4,18.3] / 5.0 | 4.1 [2.1,6.1] / 2.9 | CANDIDATE |

Failed criteria: PRO_Z20_t1.0: SPAN2>0; PRO_Z120_t2.0: WF_CI>0; PRO_RIB1m_q20: plc>=.95; PRO_ER4_EMA5: SPAN2>0; PRO_KAL_s0.5_k0.0: plc>=.95; PRO_KAL_s0.5_k0.25: SPAN2>0; PRO_RIB1m_q25_M5: plc>=.95; PRO_RIB1m_q25_M10: plc>=.95; PRO_RIB1m_q30_M5: plc>=.95; PRO_RIB1m_q30_M20: plc>=.95; PRO_RIB1m_q35_M5: plc>=.95; PRO_RIB1m_q35_M20: plc>=.95; PRO_ER4_n40_EMA5: tpw>=3; PRO_ER6_n20_EMA5: tpw>=3. `*` = LOW-FREQUENCY (< 3 trades/wk, kept). $k/wk at 10 lots, per-book locks, net of mapped live cost. Paired columns are per-trade point differences (cell minus reference) on same-side trades within +/-15 min, with the session-block bootstrap CI and the paired MDE.

### 1b. Top 20 by holdout Sharpe (all 104 scored cells)
| cell | grp | trades/wk | win% | PRE $k/wk | WF $k/wk [CI] | HOLD $k/wk | SPAN2 $k/wk | HOLD Sharpe | placebo PRE | 2x-cost WF $k | corr ST | paired vs ST pt [CI] / MDE | paired vs BASE pt [CI] / MDE | verdict (mapped) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PRO_KAL_s0.5_k0.5 | D | 30.5 | 51 | -2.2 | 10.3 [1.1,19.4] | 23.8 | 1.2 | 3.06 | 0.65 | 6.6 | 0.39 | 1.0 [-1.1,3.1] / 3.1 | -17.0 [-21.9,-12.4] / 6.7 | DEAD |
| PRO_KAL_s0.5_k0.25 | D | 31.2 | 52 | 7.9 | 16.7 [7.1,27.1] | 26.1 | -5.2 | 2.88 | 0.95 | 12.1 | 0.30 | 0.4 [-1.9,2.6] / 3.1 | -16.2 [-21.3,-11.1] / 7.1 | CANDIDATE |
| PRO_RIB1m_q30_M5 | D | 24.1 | 52 | 3.9 | 11.7 [2.2,21.0] | 19.9 | 4.2 | 2.59 | 0.85 | 8.6 | 0.44 | -6.6 [-9.1,-4.0] / 3.6 | -19.0 [-21.9,-16.1] / 4.3 | CANDIDATE |
| PRO_ST10_CONF2_T1_2nd | A | 26.0 | 51 | -2.3 | 9.2 [-0.5,18.5] | 21.5 | -1.8 | 2.57 | 0.62 | 5.7 | 0.49 | 8.0 [5.3,10.7] / 3.9 | 1.6 [-0.6,4.0] / 3.3 | DEAD |
| PRO_Z60_t0.75 | D | 30.7 | 51 | 2.4 | 11.9 [1.6,22.5] | 22.0 | -0.6 | 2.51 | 0.68 | 7.4 | 0.49 | 9.8 [7.5,12.4] / 3.4 | -7.8 [-10.9,-4.9] / 4.2 | DEAD |
| PRO_Z20_t1.0 | C | 31.5 | 51 | 8.9 | 13.8 [4.7,22.5] | 19.0 | -3.4 | 2.41 | 0.97 | 8.9 | 0.38 | 2.4 [-0.2,5.1] / 3.7 | -15.7 [-20.1,-11.3] / 6.5 | CANDIDATE |
| PRO_KAL_s0.5_k0.0 | D | 31.1 | 51 | 0.8 | 11.0 [1.4,21.4] | 22.0 | 3.0 | 2.41 | 0.72 | 8.0 | 0.27 | -1.6 [-3.6,0.5] / 3.0 | -19.9 [-25.0,-14.2] / 7.7 | CANDIDATE |
| PRO_RIB1m_q20 | C | 23.7 | 51 | 2.4 | 9.2 [0.7,17.9] | 16.4 | 4.5 | 2.39 | 0.82 | 6.2 | 0.40 | -7.7 [-10.3,-5.1] / 3.7 | -19.4 [-22.4,-16.3] / 4.4 | CANDIDATE |
| PRO_ST10_ONL_T1 | A | 2.8* | 51 | -3.1 | 1.2 [-1.7,4.2] | 5.7 | -1.8 | 2.37 | 0.03 | 0.8 | 0.19 | 2.2 [-6.5,11.5] / 12.5 | -9.3 [-22.0,3.5] / 18.0 | DEAD |
| PRO_KAL_s2.0_k0.5 | D | 31.5 | 51 | -1.2 | 8.8 [-0.8,18.9] | 19.7 | -3.9 | 2.33 | 0.53 | 4.2 | 0.33 | -2.0 [-4.2,0.4] / 3.2 | -18.6 [-23.8,-13.6] / 7.2 | DEAD |
| PRO_RIB1m_q25_M20 | D | 25.0 | 51 | 1.3 | 8.8 [-0.2,17.5] | 16.8 | 3.9 | 2.31 | 0.80 | 5.7 | 0.44 | -6.9 [-9.5,-4.5] / 3.7 | -19.7 [-22.8,-16.4] / 4.7 | DEAD |
| PRO_RIB1m_q25_M5 | D | 23.5 | 52 | 2.5 | 9.8 [0.4,19.1] | 17.7 | 1.8 | 2.31 | 0.60 | 6.6 | 0.41 | -6.7 [-9.0,-4.1] / 3.7 | -18.6 [-21.5,-15.8] / 4.0 | CANDIDATE |
| PRO_RIB1m_q25_M10 | D | 24.2 | 52 | 3.7 | 10.1 [1.4,19.5] | 16.9 | 2.0 | 2.28 | 0.93 | 6.2 | 0.42 | -7.0 [-9.4,-4.5] / 3.5 | -18.9 [-21.9,-16.0] / 4.3 | CANDIDATE |
| PRO_RIB1m_q30_M20 | D | 25.6 | 52 | 5.7 | 11.0 [1.3,20.6] | 16.7 | 6.0 | 2.24 | 0.90 | 8.5 | 0.47 | -7.4 [-9.9,-4.8] / 3.6 | -20.6 [-23.9,-17.3] / 4.7 | CANDIDATE |
| PRO_RIB1m_q35_M5 | D | 24.9 | 52 | 2.1 | 10.1 [0.6,20.3] | 18.6 | 3.3 | 2.23 | 0.70 | 7.2 | 0.47 | -7.6 [-10.0,-5.0] / 3.6 | -19.4 [-22.5,-16.4] / 4.2 | CANDIDATE |
| PRO_RIB1m_q30 | C | 24.8 | 52 | 5.4 | 10.3 [1.3,19.6] | 15.4 | 4.8 | 2.04 | 0.95 | 7.4 | 0.46 | -7.2 [-9.7,-4.8] / 3.6 | -20.0 [-22.9,-17.0] / 4.4 | PASS |
| PRO_RIB1m_q35_M20 | D | 26.2 | 51 | 4.8 | 10.8 [0.8,20.3] | 17.1 | 5.5 | 2.04 | 0.80 | 6.8 | 0.50 | -7.4 [-9.9,-4.8] / 3.6 | -20.4 [-23.5,-17.1] / 4.5 | CANDIDATE |
| PRO_EMA200_dPOC_T1 | B | 21.5 | 51 | -4.2 | 4.4 [-3.2,12.4] | 13.8 | 10.2 | 1.99 | 0.50 | 1.9 | 0.30 | 4.1 [0.6,7.4] / 5.0 | -3.8 [-7.3,-0.8] / 4.7 | DEAD |
| PRO_EMA200_CONF2_T1 | B | 27.5 | 50 | -4.9 | 4.7 [-3.8,12.8] | 15.1 | -1.0 | 1.99 | 0.45 | -0.1 | 0.41 | 6.1 [3.3,9.0] / 4.1 | -2.5 [-5.1,0.2] / 4.0 | DEAD |
| PRO_ST10_CONF2_T2 | A | 25.3 | 51 | -1.6 | 6.6 [-1.8,15.3] | 15.5 | 9.7 | 1.96 | 0.72 | 3.5 | 0.54 | -2.7 [-4.8,-0.5] / 3.2 | -12.1 [-15.1,-8.8] / 4.5 | DEAD |

### 1c. 3x3 neighbour grids around the four PASS cells (PRO2D + the PRO2C grid)
| centre | cells in grid | PRE>0 | WF>0 | WF CI>0 | HOLD>0 | SPAN2>0 | placebo>=.95 | not DEAD | sign agreement (>=75% of PRE,WF,HOLD all > 0) |
|---|---|---|---|---|---|---|---|---|---|
| PRO_Z60_t1.0 | 11 | 8/11 | 11/11 | 2/11 | 11/11 | 4/11 | 2/11 | 1/11 | DISAGREE |
| PRO_KAL_k0.0 | 9 | 7/9 | 9/9 | 4/9 | 9/9 | 7/9 | 2/9 | 3/9 | agree |
| PRO_RIB1m_q30 | 10 | 10/10 | 10/10 | 8/10 | 10/10 | 10/10 | 1/10 | 8/10 | agree |
| PRO_ER5_EMA5 | 9 | 8/9 | 9/9 | 4/9 | 8/9 | 7/9 | 5/9 | 4/9 | agree |

## 2. P2 - levels by the auction (PRO2A + PRO2B, 47 cells)
| cell | grp | trades/wk | win% | PRE $k/wk | WF $k/wk [CI] | HOLD $k/wk | SPAN2 $k/wk | HOLD Sharpe | placebo PRE | 2x-cost WF $k | corr ST | paired vs ST pt [CI] / MDE | paired vs BASE pt [CI] / MDE | verdict (mapped) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PRO_ST10_dPOC_T1_2nd | A | 16.5 | 52 | 6.0 | 6.2 [-2.0,14.4] | 6.3 | 3.8 | 0.88 | 0.82 | 3.7 | 0.34 | 4.0 [-0.0,8.2] / 5.7 | -4.0 [-7.6,-0.5] / 5.1 | DEAD |
| PRO_HMA55_AVWAP_flip_T1 | B | 20.5 | 51 | 5.5 | 4.0 [-4.4,11.5] | 2.4 | 1.7 | 0.32 | 0.88 | 1.6 | 0.17 | 3.1 [-0.1,6.6] / 4.7 | -8.8 [-12.5,-5.5] / 5.1 | DEAD |
| PRO_EMA200_HVN5_T1 | B | 19.6 | 50 | 5.0 | 0.4 [-8.0,9.0] | -4.6 | -5.8 | -0.69 | 0.95 | -0.9 | 0.10 | 1.6 [-1.7,5.1] / 4.8 | -1.1 [-5.0,2.8] / 5.5 | DEAD |
| PRO_ST10_IMP62_T1 | A | 18.4 | 50 | 4.4 | 1.8 [-5.6,9.7] | -0.9 | 7.7 | -0.13 | 0.93 | -0.4 | 0.34 | 8.2 [5.0,11.6] / 4.8 | 0.1 [-2.9,3.2] / 4.3 | DEAD |
| PRO_ST10_AVWAP_sw_T1 | A | 27.1 | 50 | 3.5 | 3.6 [-6.0,13.7] | 3.7 | 0.4 | 0.39 | 0.82 | -0.4 | 0.61 | 1.9 [0.0,3.9] / 2.8 | -10.8 [-13.3,-8.4] / 3.5 | DEAD |
| PRO_ST10_AVWAP_flip_T1 | A | 20.4 | 51 | 3.3 | 6.1 [-2.5,13.9] | 9.1 | 5.6 | 1.17 | 0.70 | 3.3 | 0.23 | 1.1 [-2.3,4.4] / 4.8 | -6.3 [-9.7,-3.1] / 4.7 | DEAD |
| PRO_ST10_AVWAP_flip_T2 | A | 19.0 | 51 | 3.0 | 5.0 [-3.5,13.2] | 7.1 | 5.8 | 0.88 | 0.80 | 3.1 | 0.24 | -1.8 [-5.1,1.5] / 4.8 | -13.1 [-17.1,-8.8] / 6.1 | DEAD |
| PRO_ST10_dVAL_T1 | A | 13.6 | 51 | 2.6 | 1.8 [-5.1,8.3] | 0.9 | -3.6 | 0.15 | 0.90 | 0.1 | 0.25 | 0.4 [-4.2,5.2] / 6.8 | -1.7 [-6.4,3.3] / 6.7 | DEAD |
| PRO_ST10_AVWAP_flip_T1_2nd | A | 15.7 | 51 | 2.6 | 2.7 [-4.2,9.7] | 2.8 | 10.8 | 0.44 | 0.75 | 1.4 | 0.34 | 2.1 [-1.0,5.3] / 4.6 | -8.9 [-13.2,-5.2] / 5.8 | DEAD |
| PRO_ST10_pdVAH_T1 | A | 5.7 | 51 | 1.9 | 1.6 [-2.3,5.9] | 1.3 | -4.3 | 0.39 | 0.88 | 0.9 | 0.11 | 4.0 [-2.4,10.5] / 9.2 | 2.8 [-4.5,9.5] / 10.0 | DEAD |
| PRO_ST10_PPL_T1 | A | 22.8 | 50 | 1.8 | 2.4 [-6.4,11.7] | 3.0 | 8.5 | 0.37 | 0.82 | -1.9 | 0.50 | 7.9 [4.8,11.5] / 4.8 | 0.8 [-1.2,2.9] / 3.1 | DEAD |
| PRO_PRIORDIR_pdPOC_T1 | B | 7.0 | 52 | 1.2 | 2.5 [-2.1,6.9] | 3.9 | -2.5 | 1.11 | 0.88 | 1.2 | -0.00 | 6.3 [-3.4,15.4] / 13.3 | 3.7 [-3.5,10.9] / 10.4 | DEAD |
| PRO_ST10_dVAH_T1 | A | 13.2 | 50 | 1.0 | 0.2 [-7.0,6.8] | -0.6 | -0.4 | -0.11 | 0.62 | -1.2 | 0.29 | 5.2 [0.9,10.0] / 6.8 | 3.0 [-1.7,7.5] / 6.3 | DEAD |
| PRO_ST10_pdVAL_T1 | A | 5.2 | 50 | 1.0 | 0.3 [-3.4,4.3] | -0.4 | -1.4 | -0.12 | 0.72 | -0.2 | 0.10 | -1.6 [-7.7,4.4] / 8.6 | -2.9 [-11.8,5.8] / 12.4 | DEAD |
| PRO_ST10_dPOC_T2 | A | 19.2 | 51 | 0.9 | 5.5 [-2.4,14.7] | 10.4 | 5.1 | 1.44 | 0.80 | 2.8 | 0.33 | 2.1 [-1.6,5.7] / 5.1 | -10.3 [-13.7,-6.7] / 5.0 | DEAD |
| PRO_HMA55_IMP50_T1 | B | 17.5 | 51 | 0.9 | 3.7 [-2.9,9.6] | 6.7 | 2.3 | 1.13 | 0.75 | 2.2 | 0.39 | 6.3 [3.3,9.2] / 4.3 | -4.7 [-8.1,-1.6] / 4.7 | DEAD |
| PRO_ST10_VWAPb1_T1_2nd | A | 6.8 | 51 | 0.3 | 0.8 [-4.6,6.0] | 1.3 | 2.8 | 0.29 | 0.53 | 0.0 | -0.04 | 8.3 [1.0,17.0] / 11.5 | 4.5 [-0.1,9.6] / 7.1 | DEAD |
| PRO_ST10_LVN5_T1 | A | 17.1 | 49 | 0.1 | -3.6 [-10.1,3.7] | -7.6 | -8.5 | -1.20 | 0.72 | -5.1 | 0.28 | 2.5 [-1.7,6.4] / 5.9 | -0.1 [-4.6,4.7] / 6.5 | DEAD |
| PRO_ST10_VWAPb1_T1 | A | 10.2 | 50 | -0.2 | -1.5 [-7.5,4.6] | -2.8 | -3.4 | -0.59 | 0.72 | -2.2 | -0.08 | 13.9 [7.7,20.2] / 8.8 | 11.4 [6.0,16.8] / 7.6 | DEAD |
| PRO_ST10_CONF2_T1_W10 | B | 27.5 | 51 | -0.3 | 6.5 [-2.7,15.7] | 13.8 | -4.1 | 1.78 | 0.57 | 3.4 | 0.52 | 6.2 [3.7,8.6] / 3.7 | -1.8 [-4.5,0.6] / 3.7 | DEAD |
| PRO_HMA55_pdPOC_T1 | B | 6.4 | 51 | -0.5 | 1.1 [-3.3,5.5] | 2.9 | -3.9 | 0.72 | 0.45 | 0.7 | 0.18 | 6.3 [0.4,12.1] / 8.4 | -3.3 [-10.6,3.2] / 9.8 | DEAD |
| PRO_HMA55_CONF2_T1 | B | 27.4 | 49 | -0.7 | -2.5 [-11.0,6.9] | -4.5 | -8.2 | -0.57 | 0.62 | -3.0 | 0.40 | 6.4 [3.6,9.2] / 4.0 | -4.2 [-7.0,-1.6] / 3.9 | DEAD |
| PRO_EMA200_pdPOC_T1 | B | 6.4 | 51 | -0.7 | 0.8 [-3.7,5.6] | 2.5 | -0.7 | 0.67 | 0.33 | 0.1 | 0.08 | 4.3 [-2.5,11.1] / 9.9 | -2.7 [-8.6,3.4] / 8.8 | DEAD |
| PRO_ST10_PPL_T1_2nd | A | 16.6 | 50 | -0.7 | 1.4 [-6.9,9.4] | 3.8 | 5.3 | 0.59 | 0.45 | -1.6 | 0.40 | 5.9 [1.7,10.6] / 6.5 | -1.7 [-4.4,0.9] / 3.9 | DEAD |
| PRO_HMA55_dPOC_T1 | B | 21.5 | 49 | -0.8 | -1.6 [-9.5,6.6] | -2.6 | -0.8 | -0.36 | 0.57 | -3.6 | 0.12 | 4.3 [1.1,7.6] / 4.7 | -6.4 [-10.1,-2.6] / 5.5 | DEAD |
| PRO_ST10_IMP38_T1 | A | 21.2 | 50 | -0.8 | 1.8 [-7.0,10.5] | 4.5 | 5.8 | 0.59 | 0.60 | -0.2 | 0.31 | 2.3 [-0.6,5.6] / 4.5 | -6.0 [-8.8,-3.2] / 4.1 | DEAD |
| PRO_ST10_ONH_T1 | A | 3.3 | 49 | -1.5 | -1.3 [-4.2,1.8] | -1.0 | 2.6 | -0.40 | 0.50 | -1.5 | 0.18 | -3.7 [-11.8,3.8] / 11.3 | -10.7 [-19.0,-2.1] / 12.1 | DEAD |
| PRO_ST10_CONF2_T2 | A | 25.3 | 51 | -1.6 | 6.6 [-1.8,15.3] | 15.5 | 9.7 | 1.96 | 0.72 | 3.5 | 0.54 | -2.7 [-4.8,-0.5] / 3.2 | -12.1 [-15.1,-8.8] / 4.5 | DEAD |
| PRO_PRIORDIR_AVWAP_flip_T1 | B | 18.7 | 50 | -1.7 | 1.6 [-6.8,8.9] | 5.2 | 1.8 | 0.71 | 0.45 | -0.5 | 0.05 | 7.7 [3.5,12.0] / 6.2 | -4.5 [-8.9,-0.3] / 6.3 | DEAD |
| PRO_ST10_pdPOC_T2 | A | 5.9 | 49 | -1.9 | -1.3 [-5.9,3.6] | -0.5 | -4.9 | -0.13 | 0.35 | -1.8 | 0.28 | -2.8 [-8.9,3.8] / 9.3 | -7.1 [-12.7,-1.4] / 8.1 | DEAD |
| PRO_ST10_CONF2_T1_W60 | B | 27.6 | 50 | -2.1 | 5.1 [-4.0,14.4] | 13.0 | -3.1 | 1.58 | 0.45 | 3.1 | 0.53 | 6.2 [3.7,9.0] / 3.8 | -1.9 [-4.5,0.5] / 3.6 | DEAD |
| PRO_ST10_CONF2_T1_2nd | A | 26.0 | 51 | -2.3 | 9.2 [-0.5,18.5] | 21.5 | -1.8 | 2.57 | 0.62 | 5.7 | 0.49 | 8.0 [5.3,10.7] / 3.9 | 1.6 [-0.6,4.0] / 3.3 | DEAD |
| PRO_EMA200_AVWAP_flip_T1 | B | 20.1 | 50 | -2.5 | 0.6 [-8.0,7.9] | 4.0 | 4.0 | 0.51 | 0.45 | -2.5 | 0.20 | 5.0 [0.9,9.0] / 5.6 | -5.2 [-8.8,-1.8] / 5.1 | DEAD |
| PRO_ST10_CONF2_T1 | A | 27.6 | 50 | -2.8 | 4.3 [-4.8,13.5] | 11.9 | -3.1 | 1.46 | 0.40 | 2.4 | 0.52 | 6.1 [3.5,8.9] / 3.9 | -2.1 [-4.6,0.3] / 3.5 | DEAD |
| PRO_PRIORDIR_CONF2_T1 | B | 27.3 | 50 | -2.9 | 0.7 [-9.0,11.5] | 4.5 | -5.4 | 0.48 | 0.45 | -3.1 | 0.10 | 8.7 [5.3,12.4] / 5.0 | -0.4 [-3.4,3.0] / 4.4 | DEAD |
| PRO_ST10_ONL_T1 | A | 2.8* | 51 | -3.1 | 1.2 [-1.7,4.2] | 5.7 | -1.8 | 2.37 | 0.03 | 0.8 | 0.19 | 2.2 [-6.5,11.5] / 12.5 | -9.3 [-22.0,3.5] / 18.0 | DEAD |
| PRO_ST10_dPOC_T1 | A | 21.4 | 51 | -3.2 | 5.0 [-3.5,14.4] | 13.9 | 3.6 | 1.78 | 0.23 | 2.7 | 0.36 | 2.4 [-0.6,5.4] / 4.2 | -3.7 [-6.8,-0.8] / 4.3 | DEAD |
| PRO_ST10_VWAPb2_T1 | A | 5.3 | 49 | -3.3 | -1.5 [-5.8,2.6] | 0.5 | 0.2 | 0.14 | 0.17 | -2.0 | 0.08 | 22.8 [13.1,34.1] / 15.5 | 12.3 [5.8,19.4] / 9.8 | DEAD |
| PRO_EMA200_IMP50_T1 | B | 16.6 | 50 | -3.5 | 1.7 [-4.9,8.0] | 7.3 | 0.6 | 1.11 | 0.35 | -0.3 | 0.27 | 6.9 [3.8,10.0] / 4.6 | -3.7 [-7.3,-0.0] / 5.1 | DEAD |
| PRO_ST10_pdPOC_T1_2nd | A | 4.2 | 48 | -4.0 | -2.3 [-5.6,1.1] | -0.4 | -3.1 | -0.13 | 0.05 | -2.5 | 0.24 | 7.3 [-0.8,15.3] / 11.4 | -8.1 [-15.7,-0.3] / 10.7 | DEAD |
| PRO_ST10_pdPOC_T1 | A | 6.5 | 49 | -4.1 | -2.4 [-7.0,2.2] | -0.6 | -2.3 | -0.15 | 0.07 | -3.2 | 0.28 | 3.9 [-2.3,10.1] / 9.1 | -1.8 [-7.1,3.1] / 7.3 | DEAD |
| PRO_EMA200_dPOC_T1 | B | 21.5 | 51 | -4.2 | 4.4 [-3.2,12.4] | 13.8 | 10.2 | 1.99 | 0.50 | 1.9 | 0.30 | 4.1 [0.6,7.4] / 5.0 | -3.8 [-7.3,-0.8] / 4.7 | DEAD |
| PRO_EMA200_CONF2_T1 | B | 27.5 | 50 | -4.9 | 4.7 [-3.8,12.8] | 15.1 | -1.0 | 1.99 | 0.45 | -0.1 | 0.41 | 6.1 [3.3,9.0] / 4.1 | -2.5 [-5.1,0.2] / 4.0 | DEAD |
| PRO_ST10_HVN5_T2 | A | 17.1 | 49 | -5.1 | -1.9 [-8.9,5.5] | 1.5 | -4.7 | 0.26 | 0.17 | -4.0 | 0.29 | -8.2 [-11.9,-4.7] / 5.3 | -12.9 [-17.2,-8.6] / 6.3 | DEAD |
| PRO_HMA55_HVN5_T1 | B | 20.1 | 48 | -6.0 | -7.5 [-14.9,0.0] | -9.0 | -8.7 | -1.36 | 0.35 | -8.9 | 0.23 | 1.4 [-2.0,5.0] / 5.1 | -4.4 [-8.7,0.3] / 6.4 | DEAD |
| PRO_ST10_HVN5_T1 | A | 19.7 | 49 | -6.5 | -4.6 [-12.7,3.2] | -2.5 | -5.5 | -0.37 | 0.23 | -6.5 | 0.33 | -1.0 [-4.5,2.4] / 5.0 | -1.5 [-5.2,2.1] / 5.1 | DEAD |
| PRO_ST10_IMP50_T1 | A | 20.1 | 49 | -6.7 | -1.0 [-8.5,5.8] | 5.2 | 2.4 | 0.66 | 0.20 | -2.7 | 0.36 | 6.8 [3.8,10.0] / 4.4 | -4.2 [-7.6,-1.1] / 4.6 | DEAD |

P2 summary: 47 level cells; PRE > 0 in 18, WF > 0 in 34, WF CI excludes 0 in 0, HOLD > 0 in 33, SPAN2 > 0 in 22, placebo >= .95 in 1; mapped PASS/CANDIDATE in P2: 0. Mean paired delta vs the base pullback cell -3.4 pt/trade; 2 cells significantly better than the base cell, 22 significantly worse.

First vs second touch and trigger T1 vs T2 (same level, same regime; means over the matched cells):
- first touch T1 | second touch T1: PRE -0.9 vs 0.3 $k/wk, WF 2.3 vs 3.0, HOLD 5.8 vs 5.9 (means over 6 paired cells)
- T1 first-close-back | T2 break of the touch bar extreme: PRE -2.7 vs -0.9 $k/wk, WF 1.7 vs 2.8, HOLD 6.4 vs 6.8 (means over 5 paired cells)
- confluence W=30 | W=10/60/30: PRE -2.8 vs -1.7 $k/wk, WF 4.3 vs 5.3, HOLD 11.9 vs 12.9 (means over 3 paired cells)
- regime ST10 | EMA200: PRE -3.3 vs -1.8 $k/wk, WF 1.2 vs 2.1, HOLD 6.2 vs 6.3 (means over 6 paired cells)
- regime ST10 | HMA55: PRE -3.3 vs -0.3 $k/wk, WF 1.2 vs -0.5, HOLD 6.2 vs -0.7 (means over 6 paired cells)

Confluence (>= 2 level families within 5 pts) as its own cell: PRO_ST10_CONF2_T1 PRE -2.8 / WF 4.3 / HOLD 11.9 $k/wk, placebo 0.40, paired vs base -2.1 pt; the confluence zone is present on ~80% of bars, so the touch fires 775 raw times a week - it is a dense level set, not a rare one. Single-level cells that trade >= 10/wk: AVWAP_flip_T1, AVWAP_sw_T1, VWAPb1_T1, dPOC_T1, dVAH_T1, dVAL_T1, HVN5_T1, LVN5_T1, IMP38_T1, IMP50_T1, IMP62_T1, PPL_T1.

## 3. P3 - statistical pullback (PRO2C + PRO2D, 58 cells)
| cell | grp | trades/wk | win% | PRE $k/wk | WF $k/wk [CI] | HOLD $k/wk | SPAN2 $k/wk | HOLD Sharpe | placebo PRE | 2x-cost WF $k | corr ST | paired vs ST pt [CI] / MDE | paired vs BASE pt [CI] / MDE | verdict (mapped) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PRO_Z120_t1.5 | C | 27.1 | 50 | 9.2 | 4.7 [-5.4,14.3] | -0.3 | -0.3 | -0.03 | 0.97 | 1.2 | 0.40 | 14.3 [11.3,17.2] / 4.3 | 3.0 [1.2,4.9] / 2.6 | DEAD |
| PRO_Z20_t1.0 | C | 31.5 | 51 | 8.9 | 13.8 [4.7,22.5] | 19.0 | -3.4 | 2.41 | 0.97 | 8.9 | 0.38 | 2.4 [-0.2,5.1] / 3.7 | -15.7 [-20.1,-11.3] / 6.5 | CANDIDATE |
| PRO_Z40_t1.25 | D | 30.1 | 51 | 8.3 | 7.3 [-2.4,17.6] | 6.0 | -4.5 | 0.67 | 1.00 | 3.0 | 0.39 | 8.8 [6.5,11.2] / 3.3 | -9.7 [-13.4,-6.1] / 5.1 | DEAD |
| PRO_Z60_t1.0 | C | 30.6 | 51 | 8.0 | 11.5 [1.9,21.3] | 15.2 | 6.3 | 1.91 | 0.97 | 7.0 | 0.39 | 9.4 [7.0,11.7] / 3.4 | -7.7 [-10.6,-4.9] / 4.1 | PASS |
| PRO_KAL_k0.0 | C | 32.0 | 51 | 8.0 | 13.0 [3.2,23.0] | 18.2 | 0.1 | 1.86 | 0.97 | 10.7 | 0.22 | -2.7 [-5.1,-0.4] / 3.4 | -18.6 [-23.6,-14.0] / 6.9 | PASS |
| PRO_KAL_s0.5_k0.25 | D | 31.2 | 52 | 7.9 | 16.7 [7.1,27.1] | 26.1 | -5.2 | 2.88 | 0.95 | 12.1 | 0.30 | 0.4 [-1.9,2.6] / 3.1 | -16.2 [-21.3,-11.1] / 7.1 | CANDIDATE |
| PRO_Z120_t2.0 | C | 24.3 | 51 | 7.8 | 6.6 [-1.7,15.7] | 5.2 | 2.7 | 0.62 | 0.95 | 3.9 | 0.34 | 14.8 [11.4,18.3] / 5.0 | 4.1 [2.1,6.1] / 2.9 | CANDIDATE |
| PRO_Z120_t1.0 | C | 27.8 | 50 | 7.2 | 3.5 [-5.4,12.8] | -0.5 | 2.0 | -0.06 | 0.93 | 1.0 | 0.46 | 11.7 [9.1,14.4] / 3.8 | -0.5 [-2.5,1.5] / 2.9 | DEAD |
| PRO_Z60_t1.5 | C | 29.7 | 50 | 7.1 | 5.4 [-3.8,14.7] | 3.4 | 2.3 | 0.44 | 0.93 | 2.3 | 0.36 | 10.7 [8.2,13.0] / 3.5 | -7.9 [-10.8,-5.2] / 4.1 | DEAD |
| PRO_ER4_EMA5 | C | 7.8 | 53 | 5.8 | 5.6 [0.9,10.7] | 5.3 | -1.8 | 1.30 | 1.00 | 4.6 | 0.36 | 12.0 [6.6,17.4] / 7.9 | -0.4 [-0.7,-0.1] / 0.4 | CANDIDATE |
| PRO_ER4_n40_EMA5 | D | 2.8* | 56 | 5.7 | 4.5 [1.4,7.4] | 3.1 | 1.6 | 1.12 | 1.00 | 4.0 | 0.21 | 14.1 [4.4,24.6] / 14.1 | -0.6 [-1.0,-0.2] / 0.6 | CANDIDATE |
| PRO_RIB1m_q30_M20 | D | 25.6 | 52 | 5.7 | 11.0 [1.3,20.6] | 16.7 | 6.0 | 2.24 | 0.90 | 8.5 | 0.47 | -7.4 [-9.9,-4.8] / 3.6 | -20.6 [-23.9,-17.3] / 4.7 | CANDIDATE |
| PRO_RIB1m_q30 | C | 24.8 | 52 | 5.4 | 10.3 [1.3,19.6] | 15.4 | 4.8 | 2.04 | 0.95 | 7.4 | 0.46 | -7.2 [-9.7,-4.8] / 3.6 | -20.0 [-22.9,-17.0] / 4.4 | PASS |
| PRO_Z20_t1.5 | C | 30.9 | 50 | 5.3 | 3.2 [-7.1,13.8] | 0.8 | -11.6 | 0.09 | 0.95 | -2.8 | 0.36 | 3.7 [0.9,6.4] / 3.8 | -17.9 [-22.8,-13.3] / 6.7 | DEAD |
| PRO_Z60_t2.0_ST10 | C | 25.4 | 50 | 5.1 | 4.4 [-5.4,12.8] | 3.4 | 5.4 | 0.47 | 0.88 | 1.3 | 0.52 | 13.0 [10.3,15.8] / 4.0 | -1.8 [-4.0,0.7] / 3.4 | DEAD |
| PRO_RIB1m_q35_M20 | D | 26.2 | 51 | 4.8 | 10.8 [0.8,20.3] | 17.1 | 5.5 | 2.04 | 0.80 | 6.8 | 0.50 | -7.4 [-9.9,-4.8] / 3.6 | -20.4 [-23.5,-17.1] / 4.5 | CANDIDATE |
| PRO_ER5_EMA5 | C | 3.1 | 57 | 4.7 | 5.0 [1.8,8.6] | 5.2 | 2.2 | 1.77 | 1.00 | 4.4 | 0.24 | 17.4 [7.8,28.5] / 14.7 | -0.3 [-0.8,-0.0] / 0.6 | PASS |
| PRO_Z60_t1.5_ST10 | C | 28.2 | 51 | 4.5 | 7.5 [-1.7,16.1] | 10.6 | 12.5 | 1.41 | 0.82 | 3.8 | 0.54 | 9.3 [7.0,11.6] / 3.2 | -5.5 [-8.1,-3.1] / 3.6 | DEAD |
| PRO_Z20_t2.0 | C | 27.6 | 50 | 4.4 | 1.3 [-8.8,10.5] | -2.1 | 7.0 | -0.23 | 0.85 | -1.7 | 0.25 | 5.6 [2.8,8.6] / 4.1 | -14.9 [-20.0,-9.6] / 7.3 | DEAD |
| PRO_ER5_n40_EMA5 | D | 0.8* | 58 | 4.3 | 1.5 [-0.2,3.3] | -1.6 | 1.6 | -1.12 | 1.00 | 1.4 | 0.15 | nan [nan,nan] / nan | -0.3 [-0.9,0.0] / 0.8 | DEAD |
| PRO_RIB1m_q30_M5 | D | 24.1 | 52 | 3.9 | 11.7 [2.2,21.0] | 19.9 | 4.2 | 2.59 | 0.85 | 8.6 | 0.44 | -6.6 [-9.1,-4.0] / 3.6 | -19.0 [-21.9,-16.1] / 4.3 | CANDIDATE |
| PRO_ER3_EMA5 | C | 14.0 | 52 | 3.9 | 6.5 [-0.3,13.6] | 9.3 | -0.3 | 1.66 | 0.75 | 4.7 | 0.43 | 9.4 [5.1,14.0] / 6.3 | -0.4 [-0.8,0.0] / 0.6 | DEAD |
| PRO_RIB1m_q25_M10 | D | 24.2 | 52 | 3.7 | 10.1 [1.4,19.5] | 16.9 | 2.0 | 2.28 | 0.93 | 6.2 | 0.42 | -7.0 [-9.4,-4.5] / 3.5 | -18.9 [-21.9,-16.0] / 4.3 | CANDIDATE |
| PRO_Z60_t1.25 | D | 30.1 | 50 | 3.4 | 6.7 [-2.5,16.2] | 10.3 | 3.4 | 1.33 | 0.90 | 2.6 | 0.41 | 10.1 [7.7,12.5] / 3.4 | -8.5 [-11.3,-5.7] / 3.9 | DEAD |
| PRO_RIB1m_q35_M10 | D | 25.4 | 51 | 3.2 | 9.6 [-0.1,19.5] | 16.4 | 5.2 | 1.91 | 0.80 | 6.5 | 0.47 | -7.3 [-9.9,-4.7] / 3.7 | -20.4 [-23.5,-17.4] / 4.5 | DEAD |
| PRO_KAL_s2.0_k0.25 | D | 31.8 | 50 | 3.0 | 6.8 [-2.4,16.5] | 10.8 | 1.9 | 1.16 | 0.75 | 4.8 | 0.32 | -2.5 [-4.8,-0.2] / 3.3 | -21.7 [-27.2,-16.7] / 7.5 | DEAD |
| PRO_RIB1m_q25_M5 | D | 23.5 | 52 | 2.5 | 9.8 [0.4,19.1] | 17.7 | 1.8 | 2.31 | 0.60 | 6.6 | 0.41 | -6.7 [-9.0,-4.1] / 3.7 | -18.6 [-21.5,-15.8] / 4.0 | CANDIDATE |
| PRO_Z60_t0.75 | D | 30.7 | 51 | 2.4 | 11.9 [1.6,22.5] | 22.0 | -0.6 | 2.51 | 0.68 | 7.4 | 0.49 | 9.8 [7.5,12.4] / 3.4 | -7.8 [-10.9,-4.9] / 4.2 | DEAD |
| PRO_RIB1m_q20 | C | 23.7 | 51 | 2.4 | 9.2 [0.7,17.9] | 16.4 | 4.5 | 2.39 | 0.82 | 6.2 | 0.40 | -7.7 [-10.3,-5.1] / 3.7 | -19.4 [-22.4,-16.3] / 4.4 | CANDIDATE |
| PRO_KAL_s1.0_k0.25 | D | 31.6 | 51 | 2.3 | 8.5 [-1.0,18.1] | 15.1 | 3.3 | 1.60 | 0.78 | 4.3 | 0.35 | -1.1 [-3.2,1.3] / 3.1 | -16.5 [-21.5,-12.1] / 6.9 | DEAD |
| PRO_ER6_n20_EMA5 | D | 0.9* | 60 | 2.2 | 2.0 [0.3,3.7] | 1.7 | 0.8 | 1.11 | 1.00 | 1.8 | 0.19 | nan [nan,nan] / nan | 0.0 [0.0,0.0] / 0.0 | CANDIDATE |
| PRO_RIB1m_q35_M5 | D | 24.9 | 52 | 2.1 | 10.1 [0.6,20.3] | 18.6 | 3.3 | 2.23 | 0.70 | 7.2 | 0.47 | -7.6 [-10.0,-5.0] / 3.6 | -19.4 [-22.5,-16.4] / 4.2 | CANDIDATE |
| PRO_Z60_t1.0_ST10 | C | 29.1 | 50 | 2.1 | 6.4 [-3.2,15.7] | 11.1 | 7.0 | 1.40 | 0.68 | 3.2 | 0.54 | 9.0 [6.5,11.3] / 3.4 | -6.9 [-9.7,-4.1] / 3.9 | DEAD |
| PRO_Z40_t1.0 | D | 30.6 | 50 | 1.9 | 4.3 [-4.8,14.0] | 6.8 | -2.9 | 0.78 | 0.78 | -0.3 | 0.39 | 7.7 [5.3,10.1] / 3.4 | -10.6 [-14.4,-7.1] / 5.2 | DEAD |
| PRO_KAL_k1.0 | C | 30.4 | 50 | 1.7 | 5.0 [-3.7,14.4] | 8.6 | -1.0 | 1.02 | 0.88 | 3.7 | 0.42 | 1.7 [-0.5,3.9] / 3.1 | -19.1 [-24.6,-14.2] / 7.4 | DEAD |
| PRO_ER4_n10_EMA5 | D | 12.4 | 52 | 1.5 | 5.3 [-0.7,12.0] | 9.4 | 7.6 | 1.89 | 0.80 | 3.7 | 0.34 | 10.8 [6.4,15.5] / 6.5 | 0.2 [-0.3,0.8] / 0.8 | DEAD |
| PRO_ER6_n10_EMA5 | D | 3.3 | 53 | 1.5 | 2.3 [-1.0,5.3] | 3.3 | 0.0 | 1.32 | 0.80 | 1.8 | 0.30 | 8.2 [0.2,16.4] / 11.5 | 0.2 [-0.8,1.5] / 1.7 | DEAD |
| PRO_KAL_k0.5 | C | 30.6 | 50 | 1.4 | 8.7 [-0.9,18.0] | 16.4 | 5.4 | 1.88 | 0.65 | 5.3 | 0.42 | 0.9 [-1.2,3.1] / 3.2 | -18.7 [-24.0,-13.8] / 7.4 | DEAD |
| PRO_KAL_k1.0_ST10 | C | 29.0 | 51 | 1.3 | 9.5 [-1.2,19.9] | 18.1 | 5.0 | 1.76 | 0.72 | 6.3 | 0.47 | 0.7 [-1.4,2.8] / 3.0 | -14.6 [-19.1,-10.6] / 6.4 | DEAD |
| PRO_KAL_k0.0_ST10 | C | 29.4 | 50 | 1.3 | 8.2 [-1.5,18.3] | 15.6 | 4.7 | 1.82 | 0.65 | 4.4 | 0.58 | -3.6 [-5.8,-1.5] / 3.1 | -13.8 [-17.6,-10.1] / 5.3 | DEAD |
| PRO_RIB1m_q25_M20 | D | 25.0 | 51 | 1.3 | 8.8 [-0.2,17.5] | 16.8 | 3.9 | 2.31 | 0.80 | 5.7 | 0.44 | -6.9 [-9.5,-4.5] / 3.7 | -19.7 [-22.8,-16.4] / 4.7 | DEAD |
| PRO_KAL_s2.0_k0.0 | D | 32.3 | 50 | 1.3 | 8.1 [-1.0,18.0] | 15.5 | 6.3 | 1.76 | 0.82 | 5.7 | 0.36 | -3.4 [-5.9,-0.9] / 3.6 | -21.8 [-27.3,-16.7] / 7.7 | DEAD |
| PRO_ER4_VWAP | C | 2.4* | 50 | 1.1 | 0.0 [-2.9,2.8] | -1.2 | -1.0 | -0.50 | 0.85 | -0.2 | 0.22 | 0.5 [-4.6,5.7] / 7.5 | 4.9 [-7.2,15.9] / 16.4 | DEAD |
| PRO_KAL_k0.5_ST10 | C | 29.9 | 50 | 0.9 | 6.0 [-4.1,15.2] | 11.5 | 6.9 | 1.28 | 0.65 | 2.6 | 0.61 | -1.7 [-3.8,0.1] / 2.8 | -14.1 [-18.3,-9.6] / 6.3 | DEAD |
| PRO_KAL_s0.5_k0.0 | D | 31.1 | 51 | 0.8 | 11.0 [1.4,21.4] | 22.0 | 3.0 | 2.41 | 0.72 | 8.0 | 0.27 | -1.6 [-3.6,0.5] / 3.0 | -19.9 [-25.0,-14.2] / 7.7 | CANDIDATE |
| PRO_ER5_VWAP | C | 1.0* | 53 | 0.6 | 0.7 [-1.1,2.5] | 0.7 | 0.8 | 0.54 | 0.60 | 0.5 | 0.18 | 3.3 [-1.4,8.6] / 7.9 | -6.6 [-30.4,17.6] / 33.6 | DEAD |
| PRO_Z40_t0.75 | D | 30.4 | 50 | 0.4 | 5.0 [-4.4,14.5] | 9.9 | -1.9 | 1.09 | 0.72 | 0.9 | 0.34 | 6.3 [4.0,8.6] / 3.4 | -11.0 [-15.2,-6.7] / 6.1 | DEAD |
| PRO_Z90_t1.25 | D | 27.9 | 50 | 0.0 | 1.5 [-9.2,13.0] | 3.0 | -1.4 | 0.29 | 0.55 | -2.0 | 0.41 | 12.1 [9.5,14.7] / 3.7 | -4.2 [-6.7,-1.7] / 3.6 | DEAD |
| PRO_ER5_n10_EMA5 | D | 7.1 | 52 | -0.8 | 2.6 [-2.2,7.0] | 6.3 | 3.3 | 1.80 | 0.55 | 1.7 | 0.35 | 10.4 [5.3,15.2] / 7.3 | 0.4 [-0.3,1.1] / 1.1 | DEAD |
| PRO_ER3_VWAP | C | 5.3 | 50 | -0.9 | 0.4 [-3.5,4.3] | 1.7 | 1.6 | 0.56 | 0.40 | -0.2 | 0.29 | 3.1 [-2.3,8.1] / 7.4 | 2.8 [-4.1,8.8] / 9.2 | DEAD |
| PRO_Z60_t2.0 | C | 27.1 | 50 | -1.1 | 1.8 [-7.5,11.3] | 5.1 | 3.3 | 0.64 | 0.62 | -1.6 | 0.30 | 12.6 [10.0,15.5] / 4.0 | -2.7 [-5.5,0.1] / 4.0 | DEAD |
| PRO_KAL_s2.0_k0.5 | D | 31.5 | 51 | -1.2 | 8.8 [-0.8,18.9] | 19.7 | -3.9 | 2.33 | 0.53 | 4.2 | 0.33 | -2.0 [-4.2,0.4] / 3.2 | -18.6 [-23.8,-13.6] / 7.2 | DEAD |
| PRO_KAL_s0.5_k0.5 | D | 30.5 | 51 | -2.2 | 10.3 [1.1,19.4] | 23.8 | 1.2 | 3.06 | 0.65 | 6.6 | 0.39 | 1.0 [-1.1,3.1] / 3.1 | -17.0 [-21.9,-12.4] / 6.7 | DEAD |
| PRO_Z90_t0.75 | D | 29.8 | 50 | -2.4 | 1.6 [-8.8,11.7] | 6.0 | -3.6 | 0.70 | 0.47 | -1.2 | 0.37 | 11.6 [9.2,14.2] / 3.6 | -5.9 [-8.6,-3.2] / 3.9 | DEAD |
| PRO_Z90_t1.0 | D | 29.4 | 50 | -3.3 | 2.1 [-7.6,12.1] | 7.9 | -1.5 | 0.94 | 0.47 | 0.0 | 0.34 | 11.5 [9.1,14.0] / 3.5 | -5.6 [-8.1,-2.9] / 3.6 | DEAD |
| PRO_RIB5m_q30 | C | 17.2 | 50 | -7.1 | 1.1 [-6.2,8.8] | 9.9 | 4.9 | 1.60 | 0.15 | -1.3 | 0.35 | -5.0 [-9.3,-0.4] / 6.5 | -23.1 [-29.5,-16.9] / 8.6 | DEAD |
| PRO_RIB5m_q20 | C | 15.2 | 50 | -9.1 | 0.2 [-6.7,7.7] | 10.3 | 7.9 | 1.88 | 0.05 | -1.3 | 0.33 | -4.5 [-9.7,0.7] / 7.2 | -24.7 [-32.5,-18.1] / 10.3 | DEAD |

P3 summary: PRE > 0 in 48/57, WF > 0 in 57, WF CI excludes 0 in 19, HOLD > 0 in 52, SPAN2 > 0 in 41, placebo >= .95 in 14; mean paired delta vs the base pullback cell -10.8 pt/trade (43 significantly worse, 2 significantly better).

## 4. Long / short and predicted-quiet / predicted-wide (WF, $k/wk at 10 lots, trades/wk) for the non-DEAD cells
| cell | long | short | quiet | wide | verdict |
|---|---|---|---|---|---|
| PRO_KAL_s0.5_k0.25 | 11.5 (15.8/wk) | 5.2 (15.4/wk) | 3.5 (9.1/wk) | 13.3 (22.0/wk) | CANDIDATE |
| PRO_RIB1m_q30_M5 | 3.1 (12.2/wk) | 8.5 (11.9/wk) | 1.4 (6.6/wk) | 9.5 (17.3/wk) | CANDIDATE |
| PRO_Z20_t1.0 | 9.6 (16.0/wk) | 4.2 (15.4/wk) | 5.5 (9.3/wk) | 8.7 (21.9/wk) | CANDIDATE |
| PRO_KAL_s0.5_k0.0 | 7.8 (16.0/wk) | 3.2 (15.1/wk) | -2.0 (9.1/wk) | 13.0 (21.8/wk) | CANDIDATE |
| PRO_RIB1m_q20 | 3.0 (12.2/wk) | 6.2 (11.6/wk) | 0.3 (6.5/wk) | 8.9 (17.0/wk) | CANDIDATE |
| PRO_RIB1m_q25_M5 | 3.1 (12.0/wk) | 6.7 (11.5/wk) | 1.4 (6.4/wk) | 8.4 (17.0/wk) | CANDIDATE |
| PRO_RIB1m_q25_M10 | 3.8 (12.4/wk) | 6.3 (11.8/wk) | 1.0 (6.6/wk) | 9.1 (17.4/wk) | CANDIDATE |
| PRO_RIB1m_q30_M20 | 3.7 (13.0/wk) | 7.3 (12.6/wk) | 1.1 (6.8/wk) | 9.3 (18.5/wk) | CANDIDATE |
| PRO_RIB1m_q35_M5 | 4.1 (12.6/wk) | 6.0 (12.3/wk) | 0.3 (6.8/wk) | 9.0 (17.9/wk) | CANDIDATE |
| PRO_RIB1m_q30 | 3.1 (12.6/wk) | 7.2 (12.2/wk) | 0.5 (6.7/wk) | 9.0 (17.8/wk) | PASS |
| PRO_RIB1m_q35_M20 | 4.3 (13.2/wk) | 6.4 (13.0/wk) | 0.5 (7.0/wk) | 9.5 (18.9/wk) | CANDIDATE |
| PRO_Z60_t1.0 | 6.2 (15.2/wk) | 5.4 (15.4/wk) | 5.9 (9.1/wk) | 5.5 (21.2/wk) | PASS |
| PRO_KAL_k0.0 | 6.2 (16.3/wk) | 6.8 (15.8/wk) | 1.5 (9.6/wk) | 11.6 (22.3/wk) | PASS |
| PRO_ER5_EMA5 | 3.1 (2.0/wk) | 1.9 (1.1/wk) | 1.0 (0.8/wk) | 3.9 (2.3/wk) | PASS |
| PRO_ER4_EMA5 | 2.9 (4.7/wk) | 2.8 (3.1/wk) | 1.1 (2.2/wk) | 4.7 (5.6/wk) | CANDIDATE |
| PRO_ER4_n40_EMA5 | 2.8 (1.8/wk) | 1.7 (1.0/wk) | 1.6 (0.8/wk) | 2.8 (2.0/wk) | CANDIDATE |
| PRO_ER6_n20_EMA5 | 1.5 (0.6/wk) | 0.4 (0.3/wk) | 1.0 (0.2/wk) | 0.9 (0.6/wk) | CANDIDATE |
| PRO_Z120_t2.0 | 3.2 (12.7/wk) | 3.3 (11.5/wk) | 0.4 (6.9/wk) | 6.4 (17.2/wk) | CANDIDATE |

## 5. Equal risk (user addendum) and DS3 marginal Sharpe, finalists (direct basis, 10 lots base; helper equal_risk.py)
| cell | basis | $/wk equal lots | $/wk equal risk | lots at equal risk | ST10 $/wk | delta vs ST at equal risk | capacity lots (mean>0) | practical ceiling lots | DS3 marginal Sharpe WF / HOLD / PRE |
|---|---|---|---|---|---|---|---|---|---|
| PRO_Z20_t1.0 | direct | 14455 | 14386 | 10.0 | 14350 | 36 | 88.0 | 22.0 | 0.093 / 0.182 / 0.006 |
| PRO_Z60_t1.0 | direct | 9254 | 8651 | 9.3 | 14350 | -5698 | 56.0 | 19.0 | -0.179 / -0.052 / -0.289 |
| PRO_KAL_k0.0 | direct | 10234 | 9670 | 9.4 | 14350 | -4680 | 59.0 | 19.0 | -0.208 / -0.044 / -0.352 |
| PRO_RIB1m_q30 | direct | 7863 | 8121 | 10.3 | 14350 | -6229 | 59.0 | 19.0 | -0.185 / -0.061 / -0.298 |
| PRO_ER4_EMA5 | direct | 5419 | 9048 | 17.7 | 14350 | -5302 | 137.0 | 27.0 | 0.275 / 0.143 / 0.415 |
| PRO_ER5_EMA5 | direct | 4745 | 11590 | 26.7 | 14350 | -2760 | None | 55.0 | 0.557 / 0.466 / 0.663 |

Mapped-basis equal-risk numbers for the other non-DEAD cells are in rows (`equal_risk_and_mix_into_DS3`, basis MAPPED, no marginal Sharpe run for them to avoid extra holdout re-reads). Per-cell daily series for the T-BRACKET-PM treatment: `l2vast/ds3/out/SERIES/DS3_PRO2__<cell>__direct.parquet` (finalists) and `__mapped.parquet` (all non-DEAD mapped cells); columns ld,pnl,pnl_1p5x,pnl_2x,trades (1.5x/2x columns equal 1x: not separately priced).

## 6. Mechanism-level diagnostic (descriptive, no verdict): does the level matter before any bracket?
Trend-signed move from the entry open to the close 60 min later after each P2 cell's entry events, minus the same-regime (ST10 side) same-ET-hour average 60-min move; session-block bootstrap, MDE = 2.8 x SE (points). PRE window: effects range -4.1 to 1.5 pt against MDEs of 1.5-16.4 pt; cells with |effect| > MDE in PRE: none. HOLD and SPAN2 are in out/PRO2/diag_fwd.pkl. Reading: touching and resuming from an auction level does not change the next-hour move by more than ~1 pt beyond what the trend and hour already give; every effect is inside its MDE, so the level-by-level nulls in section 2 are powered nulls for effects of the size the mechanism needs (>= 3 pt), not just under-powered ones for the smallest ones.

## 7. Direct L2 replay
Finalists replayed: 14 cells (top 10 by mapped holdout Sharpe with >= 3 trades/wk plus every non-DEAD cell at that time). Replay = exec_engine_l2 on raw mbp-10, S10x1 (2 s gap) + XJ3 stop-join, prop queue model, latency 5 ms. Coverage: 42 of 45 month files (60,313 of 67,956 unique trades, 88.8%; per-cell cover 0.87-0.93); months 2025-03, 2025-04, 2025-07 and 2026-10 lost their workers to memguard (-9/-15) and were NOT re-launched after the lead's governor ruling and a denied relaunch; their trades use the MAPPED price (disclosed; cover column in rows). Direct verdicts (same rule): PRO_EMA200_CONF2_T1 DEAD, PRO_EMA200_dPOC_T1 DEAD, PRO_ER4_EMA5 PASS, PRO_ER5_EMA5 PASS, PRO_KAL_k0.0 PASS, PRO_KAL_k0.5 DEAD, PRO_RIB1m_q20 DEAD, PRO_RIB1m_q30 CANDIDATE, PRO_RIB5m_q20 DEAD, PRO_ST10_CONF2_T1_2nd DEAD, PRO_ST10_CONF2_T2 DEAD, PRO_Z120_t2.0 DEAD, PRO_Z20_t1.0 CANDIDATE, PRO_Z60_t1.0 CANDIDATE.

## 8. Reading
- **P2 (levels by the auction): nothing.** 0 of 47 level cells has a WF week-block CI above 0, 1 reaches placebo 0.95 (and fails PRE), none is above the best-of-N null; paired vs the base pullback cell the levels are on average worse. The mechanism-level diagnostic (section 6) shows no level moves the next-hour trend-signed return by more than about 1.5 pt (MDE 1.5-16 pt). Confluence (>= 2 families within 5 pts) is present on ~80% of bars and behaves like the dense unconditional entry. First vs second touch and T1 vs T2 differences are inside noise (section 2 lines). VWAP +-1/2 sigma, value-area, POC, HVN/LVN, overnight H/L, anchored VWAPs, impulse fibs and previous pullback low: all inside noise. This is consistent with the earlier pullback study (0 of 41 levels respected).
- **P3 (statistical pullback): positive but it is drift, not timing.** Every z-score / Kalman / ribbon cell earns $4-14k/wk in WF and 24+ trades/wk, but (i) the best PRE mean ($9.2k/wk) is below the best-of-N null 95% line ($14.9k/wk), (ii) paired vs the base T-PULLBACK cell the statistical rules are on average ~9 pt/trade WORSE (many significantly), (iii) the 3x3 neighbour grids agree in sign (WF, HOLD > 0) but fail the placebo in most neighbours and the second holdout in several, (iv) both sides are positive in the long/short table (not a pure long-drift artefact) and the P&L is concentrated in predicted-wide sessions (quiet column near zero for the ribbon and Kalman cells). The efficiency-ratio gate (ER >= 0.4/0.5 on the base EMA5 pullback) is the only P3 idea that holds across all windows with high placebo rank, at 3-8 trades/wk (ER5 is at the 3/wk line, LOW-FREQUENCY flag in the table) and ER5-ER6 neighbours with larger thresholds are too thin to test (MDE huge).
- **Equal risk (addendum):** no PRO2 cell beats ST10 at equal weekly SD except PRO_Z20_t1.0 (+$36/wk, i.e. equal). They are not declared DEAD for earning less than ST; the table in section 5 gives the equal-risk and marginal-Sharpe numbers. Hurst was not run (ER used, stated in the prereg).
- **Executability:** all cells are bar-only NT8 rules (1-min bars + bar volume; 10-min Supertrend from the 1-min series). P2 volume-profile levels use the bar-spread profile approximation; a tick-built profile (NT8 can compute from tick data) would differ slightly and must be re-validated before any spec. No L2 at runtime. No cell is recommended; nothing is live.
- **Disclosures:** holdout/second-holdout looked once (DS3_PRO2 PREHOLD text, logged); PRO2D neighbour cells were prereg'd after that look; equal_risk/add_book re-read the holdout once per direct finalist (6 lines in l2vast/ds3/ledger/addbook_looks.jsonl); ledger +105 cells; timing placebo = 40 draws (resolution 0.025). T-BRACKET-PM treatment of the finalists: series are written to out/SERIES; the treatment itself is run by that track.

