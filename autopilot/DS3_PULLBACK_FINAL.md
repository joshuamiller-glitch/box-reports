# DS3 T-PULLBACK (+ PRO) final report - PROVISIONAL (PL, 2026-10-27 ~05:40Z)
Provisional until D3PB base (direct replay 37/45 months), PRO3 (direct running), D3PB2/D3PB4/PRO1 (no rows files yet at this time) finish. Research only; no live recommendation. Full table: autopilot/PULLBACK_LEADERBOARD.md (regenerated every 25 min by l2vast/ds3/code/pl_leaderboard.py; direct verdict supersedes mapped; duplicates flagged; equal-risk columns added).

## Verdict line
Pullback: 3 PASS, 11 CANDIDATE on the DIRECT L2 basis (distinct series; mapped-only PASS/CANDIDATE awaiting direct replay: 61, mostly D3PB base and PRO3). Best: PRO_ER5_EMA5, +$4,866/wk standalone (10 lots), paired vs ST +17.0 pts/trade [6.3, 28.6], 3.1 trades/wk (at the LOW-FREQUENCY line), DS3 marginal Sharpe +0.56 (WF; HOLD +0.47), deliverable NT8 1-min bars (+ 10-min Supertrend from 1-min series), no tape needed.

## Direct-basis PASS / CANDIDATE (10 lots, S10x1 + XJ3, $/wk standalone; equal-risk per equal_risk.py)
| cell | verdict | tr/wk | $/wk | paired vs ST pts [CI] | HOLD | 2023 span | placebo | $/wk at equal risk (lots) | delta vs ST at equal risk | DS3 marg. Sharpe WF |
|---|---|---|---|---|---|---|---|---|---|---|
| PRO_ER5_EMA5 | PASS | 3.1 | 4,866 | +17.0 [6.3,28.6] | 5,724 | 2,862 | 1.00 | 11,590 (26.7) | -2,760 | +0.56 |
| PRO_ER4_EMA5 | PASS | 7.7 | 5,220 | +11.9 [6.0,17.8] | 5,355 | 33 | 1.00 | 9,048 (17.7) | -5,302 | +0.28 |
| PRO_KAL_k0.0 | PASS | 28.8 | 10,077 | -3.4 [-5.9,-0.8] | 15,449 | 2,447 | 0.97 | 9,670 (9.4) | -4,680 | -0.21 |
| PB3B_R5_P1 | CAND | 27.3 | 15,248 | -0.3 [-2.4,1.7] | 18,711 | 5,996 | 0.95 | 17,265 (11.5) | +2,915 | +0.26 |
| PB3B_R60_P2 (= PB3E_B_R60_P2_60_1R, duplicate) | CAND | 24.3 | 11,917 | +2.2 [-0.2,4.6] | 12,585 | 2,425 | 1.00 | 12,518 (9.9) | -1,832 | +0.21 |
| PB3B_R60_P3 | CAND | 23.0 | 8,004 | +0.2 [-3.3,3.8] | 10,933 | 1,150 | 1.00 | 9,158 (10.3) | -5,192 | +0.19 |
| PRO_Z20_t1.0 | CAND | 28.6 | 14,005 | +2.0 [-0.5,4.5] | 18,041 | -3,367 | 0.97 | 14,386 (10.0) | +36 | +0.09 |
| PB3D_R3_P2 (= PB3E_D_R3_P2_60_1R, duplicate) | CAND | 19.4 | 7,065 | +2.0 [-1.7,5.4] | 2,909 | -1,639 | 1.00 | 8,691 (12.1) | -5,659 | +0.03 |
| PB3B_R10_P3 | CAND | 23.3 | 6,493 | -2.9 [-5.6,0.0] | 7,498 | 9,754 | 0.90 | 6,571 (10.9) | -7,779 | -0.02 |
| PB3F_D_R3_P2_60_2R_bracket | CAND | 12.9 | 7,550 | -5.4 [-13.6,2.4] | 4,301 | 2,071 | 1.00 | 7,838 (10.7) | -6,512 | -0.03 |
| PB3B_R5_P3 | CAND | 23.9 | 7,065 | -0.1 [-3.0,2.5] | 9,813 | 5,791 | 0.97 | 7,999 (12.0) | -6,351 | -0.07 |
| PB3E_D_R3_P2_40_1.5R | CAND | 18.3 | 8,546 | +6.0 [1.0,10.9] | 4,763 | 1,507 | 1.00 | 8,341 (10.2) | -6,009 | -0.08 |
| PRO_Z60_t1.0 | CAND | 27.2 | 9,277 | +8.2 [6.0,10.6] | 10,583 | 7,660 | 0.97 | 8,651 (9.3) | -5,698 | -0.18 |
| PRO_RIB1m_q30 | CAND | 23.4 | 8,535 | -7.3 [-9.9,-4.8] | 12,598 | 6,605 | 0.95 | 8,121 (10.3) | -6,229 | -0.18 |
(PRO2: 3 direct PASS, 3 CAND; D3PB3: 21 direct finalists, 8 distinct CAND, 0 PASS; matches the lead's counts.) Equal-risk rule applied: no cell is DEAD solely for earning less than ST at equal lots; every cell above keeps its s48 verdict and shows the equal-risk delta. Only PB3B_R5_P1 beats ST10 at equal risk (+$2.9k/wk) with positive marginal DS3 Sharpe in WF and HOLD; ER5/ER4 add the most to DS3 but are thin (3-8 trades/wk, MDE of the paired effect 8-15 pts) and need 18-27 lots for equal risk.

## Best-of-N and multiplicity (honest context)
- 447 cells scored in the four rows files (D3PB base 157, D3PB3 141, PRO2 104, PRO3 45); plus D3PB2/D3PB4/PRO1 not yet in. Ledger ~35.5k cumulative.
- PRO2 best-of-N null: best real PRE mean $9.2k/wk vs placebo-max 95th percentile $14.9k/wk, so no PRO2 cell beats the best-of-104 random-timing line. PRO3: the four survivors are overlapping filters of one base cell (best of 19). D3PB3: expected 3.5 cells with paired-vs-ST CI above 0 by chance; 54 did, but pairing covers ~20% of trades.
- D3PB base: 78% of cells WF>0 and 81% HOLD>0 is mainly trend/bracket beta of 2024-26; the counter-trend fade of the same signals is negative in all 8 fade cells (mechanism sign = continuation), but no cell beats ST10 as a book (weekly diff negative for all 117 first-pass cells).
- The 3 PASS: PRO_KAL_k0.0 has a significantly NEGATIVE paired-vs-ST CI and negative DS3 marginal Sharpe, so its PASS is a standalone-drift PASS, not a timing improvement. ER4/ER5 are the only PASS with positive paired-vs-ST and positive marginal Sharpe, but they gate one base cell by trade count (3-8/wk); direct coverage 93%.
- Direct coverage caveat: PRO2 direct replay covers 42/45 months (cover 0.87-0.93; lost months fell back to mapped); 8 months of D3PB base are re-queued.

## P9 robustness: NOT run (honest gap)
Per the lead's instruction no replay workers were started, and the full block (full-grid stability, day-block bootstrap maxDD, VIX-tercile stress, fill-model/latency sensitivity, 1.5x/2x cost sweep, capacity curve to 42 lots) was not run by PL. Available already from the track agents: 2x cost WF (x2_WF in rows), 3x3 neighbour grids (neighbours_agree), counter-trend mirror (D3PB base: all 8 fade cells negative; no cell-specific mirrors for the PASS/CANDIDATE cells), capacity lots at zero mean and practical ceiling from equal_risk.py (ER5: practical ceiling 55 lots; ER4 27; Z20 22; KAL 19), peak-lot upper bound = nominal lots. Recommended next, once the replay governor allows: P9 on PRO_ER5_EMA5, PRO_ER4_EMA5, PB3B_R5_P1 only (cell-specific mirror, day-block bootstrap, VIX terciles, fill sensitivity).

## Specs / registration
PASS/CANDIDATE cells already registered by the track agents under l2vast/struct48/paper_all/ds3_*.json (PRO2/PRO3 and ds3_tpullback3_*); PL did not add entries. D3X parameter-level specs / identity tests for the PASS cells (exact NT8 bar type: NQ 1-min bars with 10-min Supertrend from the 1-min series, EMA5 pullback, efficiency-ratio gate) were NOT requested yet; all three PASS are bar-only (no tape dependence).

## Still open
D3PB base direct (8 months), D3PB2 and D3PB4 rows, PRO1 (P1 tape / P7 learned detector) rows, PRO3 direct (mapped: 2 PASS PRO3A_VOL/PRO3A_REL, 2 CAND), then re-run the leaderboard and update this report.
