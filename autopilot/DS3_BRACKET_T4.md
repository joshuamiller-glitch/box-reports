# DS3 T-BRACKET-PM tier-4 pullback entries: sections A, D, G (D3BL4)

Written 2026-10-27T08:20Z. Research only; no live recommendation. Entries: 6 PRO2 + 8 PB3 (registry tier4). Sections B (near-target) and C (scale-out) are scored by D3NT and the T2 agent. Trend entries not run (mapped-only).

**Cells scored: A 392, D 420, G1 420, G2 420 (total 1652); PASS 0, CANDIDATE 3, DEAD 1649 (mapped-screen verdicts; no direct L2 replay was run, see blockers).**

## Section A - bracket shape incl. negative-R and structure stop (392 cells = 14 x 28)

Cells scored: 392; verdicts (mapped screen): {'DEAD': 391, 'CANDIDATE': 1}. Cells with paired WF CI lower bound > 0: 11 (expected by chance at one-sided 2.5%: 9.8).

| entry | cells | median paired pts/trade | best [CI] | median MDE | share >0 | PASS | CANDIDATE |
|--|--|--|--|--|--|--|--|
| PB3B_R10_P3 | 28 | -0.76 | +0.39 [-0.58,+1.32] (R10_P3_t45_s50) | 1.88 | 0.18 | 0 | 0 |
| PB3B_R5_P1 | 28 | -1.35 | +0.09 [-0.47,+0.60] (R5_P1_t60_s50) | 1.61 | 0.07 | 0 | 0 |
| PB3B_R5_P3 | 28 | -0.83 | +0.22 [-0.68,+1.23] (R5_P3_t45_s50) | 1.85 | 0.07 | 0 | 0 |
| PB3B_R60_P2 | 28 | -0.24 | +0.12 [-0.60,+0.85] (R60_P2_t45_s60) | 1.78 | 0.18 | 0 | 0 |
| PB3B_R60_P3 | 28 | -0.68 | +0.18 [-1.95,+2.33] (R60_P3_t90_s90) | 1.92 | 0.07 | 0 | 0 |
| PB3D_R3_P2 | 28 | -0.93 | +0.56 [-0.61,+1.71] (R3_P2_t45_s50) | 2.20 | 0.21 | 0 | 0 |
| PB3E_D_R3_P2_40_1.5R | 28 | -0.20 | +1.50 [-0.12,+3.06] (D_R3_P2_40_1.5R_t45_s75) | 2.19 | 0.36 | 0 | 0 |
| PB3F_D_R3_P2_60_2R_bracket | 28 | +1.97 | +3.28 [+0.72,+5.77] (_R3_P2_60_2R_bracket_t45_s50) | 3.61 | 0.82 | 0 | 1 |
| PRO_ER4_EMA5 | 28 | -0.97 | +0.30 [-1.60,+1.99] (ER4_EMA5_t60_s40) | 3.70 | 0.11 | 0 | 0 |
| PRO_ER5_EMA5 | 28 | -1.28 | +2.09 [-3.06,+7.12] (ER5_EMA5_t120_s60) | 5.67 | 0.32 | 0 | 0 |
| PRO_KAL_k0.0 | 28 | -0.30 | +0.72 [-0.30,+1.74] (KAL_k0.0_t30_s40) | 1.59 | 0.43 | 0 | 0 |
| PRO_RIB1m_q30 | 28 | -0.78 | +0.40 [-0.49,+1.22] (RIB1m_q30_t45_s60) | 1.90 | 0.14 | 0 | 0 |
| PRO_Z20_t1.0 | 28 | -0.22 | +0.47 [-0.53,+1.52] (Z20_t1.0_t30_sst) | 1.47 | 0.43 | 0 | 0 |
| PRO_Z60_t1.0 | 28 | -0.36 | +0.55 [-0.23,+1.34] (Z60_t1.0_t45_s50) | 1.63 | 0.32 | 0 | 0 |

Null reading: the median paired MDE above is the smallest effect that could have been seen at 80% power; effects below it are not excluded. Mechanism of the nulls: a closer target / wider stop (negative-R) buys win rate but with zero gross drift only changes the exit-type cost mix (stop-join 1.01 pt); the calibrated mapping charges closer targets about -1 pt per trade more. Placebo (same bracket on random-time entries) is in every row.

CANDIDATE (mapped screen, direct replay pending): T4A_PB3F_D_R3_P2_60_2R_bracket_t45_s75 paired +3.06 [+0.70,+5.73], MDE 3.61, hold +4.33, failed ['placebo<0.95']. PB3F base is the 2R/120-pt target; closer-target cells revert towards its 1R sibling PB3D_R3_P2 (own direct series exists): redundant with the PB3D sibling, no new information

PB3F note: its base bracket is 60 stop / 120 target (2R); every closer-target cell gains about +2 to +3 pts/trade versus that base, which is the reversion to its 1R sibling PB3D_R3_P2 (which has its own direct series): no new information. Per-session / long-short / quiet-wide paired deltas, hurdle (required vs observed win rate), weekly mean/SD/maxDD, 2x cost and the equal-risk columns are in rows/DS3_TBRACKET_T4A.json.

## Section D - pyramiding and stop handling D1-D4 (420 cells = 14 x 30)

Cells scored: 420; verdicts (mapped screen): {'DEAD': 418, 'CANDIDATE': 2}. Cells with paired WF CI lower bound > 0: 1 (expected by chance at one-sided 2.5%: 10.5).

| entry | cells | median paired pts/trade | best [CI] | median MDE | share >0 | PASS | CANDIDATE |
|--|--|--|--|--|--|--|--|
| PB3B_R10_P3 | 30 | -0.90 | +0.94 [-0.41,+2.24] (R10_P3_D1_N30_f50_m1_s30_G3) | 1.39 | 0.13 | 0 | 0 |
| PB3B_R5_P1 | 30 | -1.19 | +0.25 [-0.23,+0.72] (R5_P1_D4_SG_f50_m1_s30_G1) | 1.25 | 0.03 | 0 | 0 |
| PB3B_R5_P3 | 30 | -1.42 | +0.46 [-0.79,+1.73] (R5_P3_D1_N30_f50_m1_s30_G3) | 1.38 | 0.13 | 0 | 0 |
| PB3B_R60_P2 | 30 | -1.16 | -0.11 [-0.60,+0.38] (R60_P2_D4_SG_f50_m1_s30_G1) | 1.37 | 0.00 | 0 | 0 |
| PB3B_R60_P3 | 30 | -1.19 | -0.05 [-0.66,+0.50] (R60_P3_D4_SG_f50_m1_s30_G1) | 1.42 | 0.00 | 0 | 0 |
| PB3D_R3_P2 | 30 | -1.12 | +0.37 [-0.19,+0.93] (R3_P2_D4_SG_f50_m1_s30_G1) | 1.59 | 0.03 | 0 | 0 |
| PB3E_D_R3_P2_40_1.5R | 30 | -1.72 | +0.32 [-0.10,+0.73] (_40_1.5R_D4_SG_f50_m1_s30_G1) | 1.25 | 0.10 | 0 | 0 |
| PB3F_D_R3_P2_60_2R_bracket | 30 | -0.99 | +0.83 [-1.58,+3.12] (bracket_D1_N30_f50_m2_s15_G1) | 3.26 | 0.10 | 0 | 0 |
| PRO_ER4_EMA5 | 30 | -0.57 | +0.77 [-0.35,+1.82] (ER4_EMA5_D1_SG_f50_m1_s30_G1) | 2.67 | 0.20 | 0 | 0 |
| PRO_ER5_EMA5 | 30 | -0.78 | +2.27 [-0.50,+4.94] (R5_EMA5_D1_N15_f50_m1_s30_G1) | 4.02 | 0.43 | 0 | 2 |
| PRO_KAL_k0.0 | 30 | -1.08 | +0.45 [-0.48,+1.49] (AL_k0.0_D1_N30_f50_m1_s30_G3) | 1.15 | 0.07 | 0 | 0 |
| PRO_RIB1m_q30 | 30 | -1.08 | +0.25 [-0.27,+0.79] (IB1m_q30_D4_SG_f50_m1_s30_G1) | 1.52 | 0.17 | 0 | 0 |
| PRO_Z20_t1.0 | 30 | -1.02 | +0.26 [-0.65,+1.21] (20_t1.0_D1_N30_f50_m1_s30_G3) | 1.11 | 0.10 | 0 | 0 |
| PRO_Z60_t1.0 | 30 | -1.24 | +0.21 [-0.78,+1.26] (60_t1.0_D2_N30_f50_m1_s30_G3) | 1.20 | 0.10 | 0 | 0 |

Null reading as above. Pyramiding with any stop handling is negative on average; D4 (original stop on everything) is a doubling of exposure and not a risk-constant pyramid. Conservative mapping (no join bonus on modified stops).

CANDIDATE (mapped screen, both on PRO_ER5_EMA5, the smallest entry, 637 trades, MDE about 3 pts/trade, best of 30 cells x 14 entries): T4D_PRO_ER5_EMA5_D4_N15_f50_m1_s30_G1 paired +2.19 [-0.01,+4.59], hold +1.45, failed ['paired_CI_excludes0&maxDD_not_worse', 'year_share>60%']; T4D_PRO_ER5_EMA5_D4_SG_f50_m1_s30_G1 paired +0.81 [-0.29,+1.90], hold +1.32, failed ['paired_CI_excludes0&maxDD_not_worse']

Mean paired delta by cell over the 14 entries (pts/trade, matched pairs): best D4_PB_f50_m1_s30_G1 -0.07, D4_N15_f50_m1_s30_G1 -0.00, D4_SG_f50_m1_s30_G1 +0.16; worst D3_N15_f50_m1_s30_G1 -2.30, D3_N30_f100_m1_s30_G1 -2.28, D2_N30_f100_m1_s30_G1 -2.25.

## Section G1 - loss-side Trade Health (420 cells = 14 x 30, incl. live ST/HM controls, MAE-only, time-only)

Cells scored: 420; verdicts (mapped screen): {'DEAD': 420}. Cells with paired WF CI lower bound > 0: 0 (expected by chance at one-sided 2.5%: 10.5).

| entry | cells | median paired pts/trade | best [CI] | median MDE | share >0 | PASS | CANDIDATE |
|--|--|--|--|--|--|--|--|
| PB3B_R10_P3 | 30 | -1.27 | -0.26 [-1.97,+1.38] (_PB3_PB3B_R10_P3) | 2.65 | 0.00 | 0 | 0 |
| PB3B_R5_P1 | 30 | -1.08 | -0.13 [-1.71,+1.40] (_PB3_PB3B_R5_P1) | 2.19 | 0.00 | 0 | 0 |
| PB3B_R5_P3 | 30 | -1.83 | -0.23 [-1.54,+1.04] (_PB3_PB3B_R5_P3) | 2.61 | 0.00 | 0 | 0 |
| PB3B_R60_P2 | 30 | -0.88 | +0.41 [-1.10,+1.88] (_PB3_PB3B_R60_P2) | 2.50 | 0.03 | 0 | 0 |
| PB3B_R60_P3 | 30 | -1.07 | +0.31 [-1.05,+1.59] (_PB3_PB3B_R60_P3) | 2.74 | 0.03 | 0 | 0 |
| PB3D_R3_P2 | 30 | -2.50 | -0.94 [-2.74,+0.77] (_PB3_PB3D_R3_P2) | 3.14 | 0.00 | 0 | 0 |
| PB3E_D_R3_P2_40_1.5R | 30 | -1.60 | +0.00 [+0.00,+0.00] (_PB3_PB3E_D_R3_P2_40_1.5R) | 1.99 | 0.00 | 0 | 0 |
| PB3F_D_R3_P2_60_2R_bracket | 30 | -4.65 | -2.64 [-5.75,+0.39] (3_PB3F_D_R3_P2_60_2R_bracket) | 5.26 | 0.00 | 0 | 0 |
| PRO_ER4_EMA5 | 30 | -1.68 | +0.73 [-2.01,+3.35] (_PRO2_PRO_ER4_EMA5) | 5.14 | 0.03 | 0 | 0 |
| PRO_ER5_EMA5 | 30 | -3.44 | +1.14 [-2.81,+4.94] (_PRO2_PRO_ER5_EMA5) | 7.99 | 0.07 | 0 | 0 |
| PRO_KAL_k0.0 | 30 | -0.44 | +0.10 [-0.93,+1.12] (_PRO2_PRO_KAL_k0.0) | 1.94 | 0.03 | 0 | 0 |
| PRO_RIB1m_q30 | 30 | -1.57 | -0.20 [-1.65,+1.23] (_PRO2_PRO_RIB1m_q30) | 2.72 | 0.00 | 0 | 0 |
| PRO_Z20_t1.0 | 30 | -0.34 | +0.21 [-1.20,+1.54] (_PRO2_PRO_Z20_t1.0) | 1.94 | 0.10 | 0 | 0 |
| PRO_Z60_t1.0 | 30 | -0.82 | -0.25 [-1.58,+1.06] (_PRO2_PRO_Z60_t1.0) | 2.24 | 0.00 | 0 | 0 |

Null reading: the live TH-loss rule (TH_LIVE_ST) is negative on 14 of 14 entries (see rows); no conditional rule beats a random-timing cut. Neighbour evaluations (4,438) are ledger-counted.

Live TH-loss on ST config (named control) per entry: PRO_ER4_EMA5 -1.25 (MDE 5.0); PRO_ER5_EMA5 -2.07 (MDE 7.5); PRO_KAL_k0.0 -0.35 (MDE 1.9); PRO_RIB1m_q30 -1.59 (MDE 2.7); PRO_Z60_t1.0 -0.64 (MDE 2.2); PRO_Z20_t1.0 -0.21 (MDE 1.9); PB3B_R10_P3 -1.05 (MDE 2.6); PB3B_R5_P1 -1.06 (MDE 2.2); PB3B_R5_P3 -1.57 (MDE 2.5); PB3B_R60_P2 -0.65 (MDE 2.5); PB3B_R60_P3 -0.83 (MDE 2.7); PB3D_R3_P2 -2.45 (MDE 3.1); PB3E_D_R3_P2_40_ -1.44 (MDE 1.9); PB3F_D_R3_P2_60_ -5.11 (MDE 5.1)

## Section G2 - profit-side Trade Health (420 cells = 14 x 30)

Cells scored: 420; verdicts (mapped screen): {'DEAD': 420}. Cells with paired WF CI lower bound > 0: 0 (expected by chance at one-sided 2.5%: 10.5).

| entry | cells | median paired pts/trade | best [CI] | median MDE | share >0 | PASS | CANDIDATE |
|--|--|--|--|--|--|--|--|
| PB3B_R10_P3 | 30 | -1.54 | +0.10 [-0.77,+0.95] (r4_t8_s1__PB3_PB3B_R10_P3) | 1.90 | 0.03 | 0 | 0 |
| PB3B_R5_P1 | 30 | -2.02 | -0.71 [-1.40,-0.07] (r4_t8_s1__PB3_PB3B_R5_P1) | 1.55 | 0.00 | 0 | 0 |
| PB3B_R5_P3 | 30 | -2.08 | -0.41 [-1.18,+0.41] (r4_t8_s1__PB3_PB3B_R5_P3) | 1.87 | 0.00 | 0 | 0 |
| PB3B_R60_P2 | 30 | -1.65 | -0.77 [-1.50,-0.02] (r4_t8_s1__PB3_PB3B_R60_P2) | 1.84 | 0.00 | 0 | 0 |
| PB3B_R60_P3 | 30 | -1.76 | -0.49 [-1.32,+0.36] (r4_t8_s1__PB3_PB3B_R60_P3) | 1.94 | 0.00 | 0 | 0 |
| PB3D_R3_P2 | 30 | -2.43 | -0.84 [-1.80,+0.14] (r4_t8_s1__PB3_PB3D_R3_P2) | 2.26 | 0.00 | 0 | 0 |
| PB3E_D_R3_P2_40_1.5R | 30 | -2.23 | -1.08 [-1.76,-0.41] (s1__PB3_PB3E_D_R3_P2_40_1.5R) | 1.67 | 0.00 | 0 | 0 |
| PB3F_D_R3_P2_60_2R_bracket | 30 | -1.51 | -0.38 [-2.90,+2.08] (3_PB3F_D_R3_P2_60_2R_bracket) | 3.96 | 0.00 | 0 | 0 |
| PRO_ER4_EMA5 | 30 | -2.58 | -0.19 [-1.68,+1.45] (r4_t8_s1__PRO2_PRO_ER4_EMA5) | 3.87 | 0.00 | 0 | 0 |
| PRO_ER5_EMA5 | 30 | -6.83 | -1.41 [-3.55,+0.79] (r4_t8_s1__PRO2_PRO_ER5_EMA5) | 5.79 | 0.00 | 0 | 0 |
| PRO_KAL_k0.0 | 30 | -1.48 | -0.33 [-0.93,+0.29] (r4_t8_s1__PRO2_PRO_KAL_k0.0) | 1.41 | 0.00 | 0 | 0 |
| PRO_RIB1m_q30 | 30 | -2.10 | -0.11 [-0.95,+0.68] (r4_t8_s1__PRO2_PRO_RIB1m_q30) | 1.93 | 0.00 | 0 | 0 |
| PRO_Z20_t1.0 | 30 | -1.84 | -0.31 [-0.94,+0.36] (r4_t8_s1__PRO2_PRO_Z20_t1.0) | 1.40 | 0.00 | 0 | 0 |
| PRO_Z60_t1.0 | 30 | -1.75 | -0.33 [-0.99,+0.35] (r4_t8_s1__PRO2_PRO_Z60_t1.0) | 1.57 | 0.00 | 0 | 0 |

Null reading as above; profit-side TH prior was negative (TH audit).

## Blockers and disclosures
- No direct L2 replay run: the only mapped CANDIDATEs are redundant (PB3F) or best-of-N on the smallest entry (PRO_ER5); D3BL asked to hold the pb3_direct orchestrator until a non-redundant finalist exists. MAPPED verdicts are screens; rows carry verdict PENDING_DIRECT for CANDIDATE.
- Section A mapping: D3BA calibrated exit-type correction (out/ba/calib_coef.pkl, interim at 2026-10-27 01:55Z; D3BA report not final) plus a per-entry offset to the entry's own direct base by exit type. Re-run (about 15 min) if D3BA recalibrates.
- Sections B and C not run here (D3NT / T2 agent). Combination section E not run (no PASS to combine).
- Holdout looks: DS3_BRACKET_T4A, T4D, T4G (G1), T4G2 once each (pre-holdout texts autopilot/DS3_BRACKET_T4*_PREHOLD.md). The entries had earlier holdout looks in their own tracks.
- Equal-risk columns (pnl_wk_equal_lots, pnl_wk_equal_risk, lots_equal_risk, capacity_lots_zero_mean, ds3_marginal_sharpe) are in cell["equal_risk"] of every row; marginal Sharpe only for CANDIDATEs (re-reads the holdout, ledgered by equal_risk).
- Code: l2vast/ds3/code/t4/ (t4_lib, t4_a*, t4_pycore, t4_d_*, t4_g1*, t4_g2*). Preregs: l2vast/ds3/prereg/T4A_*, T4D_*, T4G1_*, T4G2_*.
- Notes for D3BL: (1) bl_leaderboard.py main() filters rows to entries whose id starts with ST/HM/KB/SM/EM, so tier-4 rows (entry ids PRO2_*, PB3_*) are dropped until that filter is widened. (2) rows/DS3_TBRACKET_T4G2_copy.json was emptied to avoid double counting. (3) G1 cell PB3E best "+0.00 [0,0]" is a cell with no cuts. (4) Rows files: DS3_TBRACKET_T4A.json, DS3_TPYRAMID_T4.json, DS3_TBRACKET_T4G1.json, DS3_TBRACKET_T4G2.json. paper_all: ds3_T4A_PB3F_..._t45_s75, ds3_T4D_PRO_ER5_EMA5_D4_N15_..., ds3_T4D_PRO_ER5_EMA5_D4_SG_... (mapped-only CANDIDATEs, caveats in the files).
