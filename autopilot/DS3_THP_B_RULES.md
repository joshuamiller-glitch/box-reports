# DS3_THP_B_RULES - T-TH-PROFIT section B: the classic rule grids vs hold-to-bracket (THPB)

Research only; nothing here is a live recommendation. Prereg l2vast/ds3/prereg/THPB_prereg.md sha256 5da5598e063445b219d41443ca178a37a359cc6561e0878aaf9f2290f1416f19; PRE-only text DS3_THP_B_PREHOLD.md (sha in DECISIONS.md); one logged holdout look per group F1..F12 (tracks THPB_F1..F12, l2vast/struct48/ledger/holdout_looks.jsonl). UNTOUCHED (> 2026-02-06) never read. Fees per FEES.md ($4.84/contract RT, identical in both arms). Code l2vast/ds3/code/thp_rules/ (thpr_kern.py kernel, thpr_lib.py streams/pricing, thpr_ana.py, thpr_pool.py, thpr_stack.py, thpr_repB.py); results l2vast/ds3/out/thp/rules/ (cells_B.parquet = every stream x rule cell; splits_B.parquet = by session and by year; pooled_*_B.parquet; stack_B.csv).

## Verdict

**0 PASS, 0 CANDIDATE, 3840 DEAD of 3840 stream x rule cells (20 streams x 192 rules). Pooled over the 11 intraday books (ST HM WT KB SM PE EM PB DN MV MA): 0 PASS / 0 CANDIDATE / 192 DEAD of 192 rules; pooled over the six stack books: 0 / 0 / 192.** 
**Plain answer.** No classic profit-side rule beats hold-to-bracket on identical entries, on any book, in-sample or in the holdout, on the MEASURED basis once the price-basis artefact below is removed. Pooled over the 11 intraday books (18,121 PRE trades, 7,747 HOLD trades) 0 of the 192 rules has a positive IN-SAMPLE (PRE) delta (best pooled: JADE min profit 40 / 3 of 4 / trail 4 at -0.06 pts/trade [-0.72,+0.59], MDE 0.94), the White reality check on PRE has p = 0.88 (best of 192), and not one rule is positive on the no-target-correction basis N in either window. The live JADE rule (20 / 3 of 4 / 8) costs -1.25 pts/trade IN-SAMPLE [-2.38,-0.11] (MDE 1.62; -$48.3k/wk at the books' lots) and -0.64 in the HOLDOUT [-2.39,+1.11] (MDE 2.49; -$18.5k/wk): it changes the exit on 70% of trades, lifts the win rate from 54% to 74%, saves +15.9 pts on the trades it helps and forfeits -17.2 pts on the rest, and on a per-book basis its PRE delta is negative on all 20 streams (CI excludes 0 on 8). Cross-check against the earlier JADE control on a different (MAPPED live-exit) basis, DS3_TH_G2.md paired WF pts/trade ST -1.77, HM -2.18, KB -1.51, SM -3.03, EM -1.19: this file, N basis PRE, ST -2.49, HM -1.37, KB -3.72, SM -2.88, EM -1.03 (same sign, same size). Prior results hold: DS3_EXITS_FINAL.md (246/246 DEAD) and DS3_TH_G2.md (150/150 DEAD).

**What looks like a positive and is not.** (1) 1,093 of the 3,840 cells have a positive HOLDOUT delta on the MEASURED basis M, but only 384 do on N and exactly one cell (WT F11_x30_be, +0.02 PRE / +0.25 HOLD, CI includes 0) is positive on N in both windows. The cause is the P9 target correction (-0.9 pt in 2023-24, -3.7 to -3.8 pts in 2025-26) applied to every bracket target exit: it is estimated on live rows that include live profit cuts, it penalises the baseline when it waits for the target, and it hands every early exit a credit. It is the directive's basis and is the primary one here, but every PASS/CANDIDATE gate also requires the rule to survive without it (gate NOTC). (2) The only cells with a PRE CI above zero (6 of 3,840, chance expectation 96) are the WT efficiency exits after +30 (ER over 120/300 s, at least 3 pts off the high): PRE +0.67 [+0.18,+1.17] (MDE 0.71), HOLD +1.62 [+0.78,+2.46] (MDE 1.19), X +0.45, placebo 1.00, neighbours agree, maxDD 255k better, stress basis positive; they fail year_share>60% (68%), NOTC (N-basis PRE -0.07) and the reality check (RC p = 0.07), three gates, so DEAD. WT's target is 33.75 pts, so the +30 arm sits 3.75 pts under the target and the exit mostly trades the target correction away. The efficiency threshold (0.2/0.3/0.4) does not bind: the 3-pt-off-high condition does the work, so the three thresholds are one rule. (3) The stack-level improvement in SD, maxDD and worst-20 weeks is reproduced by random exits that keep the rule's exit rate and its arm-to-exit delay distribution (section 9b): exiting early reduces variance by itself; it is not rule skill. Against that timing-matched placebo the live JADE ranks at or below the 17th percentile IN-SAMPLE on 17 of 20 streams (its timing is worse than random timing).

**Basis and scope caveats (read before using any number).** MEASURED = stop walk by year at 10 lots, market exit +1 tick at the close of the decision second, target at touch plus the P9 correction; MW/C/N shown. Locks (-2R/+5R, give-back arm, week floor) and the live TH loss rule are NOT in the stack-level rule series (labelled in section 9); the overlay rows add the rule-minus-hold delta to the actual stack. Not scored: CR (median stop 18 pts, below the 30-pt floor of the prereg for an absolute-point grid; a scale-out book modelled single-leg), D6 SM_t60_sst (median stop 20), ES and RTY basket legs (no 1-s path in the box; the B3 NQ leg is scored at 1 lot over multi-day holds and is tiny, n_PRE 78). The six D6 and three O6 session streams use the 10-lot unit; their sample is small (n_PRE 134-800). The timing-matched placebo (6h, 9b) and the kernel placebo mode it needs were added after the prereg freeze; the kernel rule semantics are unchanged (regression: max |difference| 4e-6 pts on 10 rules x 2 books against the sealed run) and no verdict uses it.


Prior result cited, not repeated: DS3_EXITS_FINAL.md (D3XT, 246/246 exit cells DEAD on ST, HM, KB, SM, EM, PB: no exit rule beats hold-to-bracket on average) and DS3_TH_G2.md (live profit-side JADE negative on ST, HM, KB, SM, EM, 150/150 DEAD). This file adds WT, PE, PB, DN, MV, MA, CR, D6 and O6 streams, a 192-rule grid on one MEASURED price basis, and the in-sample table as first-class output.

## 1. Scope: streams, sample sizes, the hold-to-bracket baseline (MEASURED basis, net pts/trade after the 0.242-pt fee)

| stream | trades | PRE | HOLD | X | lots | stop_med | tgt_med | base_net_PRE | base_net_HOLD | win_PRE | win_HOLD | RC_p |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B3_NQ | 180 | 78 | 36 | 66 | 1.0 | 1e+09 | 1e+09 | +25.48 | +84.18 | 0.60 | 0.64 | 0.643 |
| D6_HM_t75_s90_NYAM | 780 | 427 | 197 | 156 | 10.0 | 90 | 75 | +10.77 | +5.80 | 0.62 | 0.58 | 0.993 |
| D6_KB_t60_s75_ASIA | 1268 | 704 | 321 | 243 | 10.0 | 75 | 60 | +5.42 | +0.59 | 0.61 | 0.58 | 0.994 |
| D6_PB7_PB5_ASIA | 671 | 342 | 192 | 137 | 10.0 | 60 | 60 | +10.71 | +1.64 | 0.61 | 0.54 | 0.995 |
| D6_TB4B_ASIA | 843 | 450 | 200 | 193 | 10.0 | 60 | 60 | +7.32 | -7.70 | 0.58 | 0.46 | 0.869 |
| D6_TB4W_03_ASIA | 1421 | 800 | 369 | 252 | 10.0 | 60 | 60 | +4.37 | -0.05 | 0.56 | 0.53 | 0.942 |
| DN | 3272 | 1762 | 782 | 728 | 10.0 | 60 | 60 | +2.97 | +2.72 | 0.54 | 0.54 | 0.745 |
| EM | 1660 | 871 | 366 | 423 | 10.0 | 60 | 60 | +2.03 | +2.02 | 0.54 | 0.55 | 0.641 |
| HM | 2924 | 1561 | 698 | 665 | 10.0 | 60 | 60 | +0.35 | -0.43 | 0.52 | 0.52 | 0.459 |
| KB | 3444 | 1854 | 756 | 834 | 5.2 | 60 | 60 | +3.66 | +2.52 | 0.55 | 0.55 | 0.951 |
| MA | 1906 | 997 | 446 | 463 | 10.0 | 60 | 60 | +1.96 | +3.49 | 0.53 | 0.56 | 0.996 |
| MV | 3627 | 2025 | 845 | 757 | 10.0 | 60 | 60 | +1.96 | -2.24 | 0.53 | 0.50 | 0.864 |
| O6_LV_RN_BH | 293 | 134 | 78 | 81 | 10.0 | 60 | 60 | +11.59 | +4.37 | 0.62 | 0.55 | 0.956 |
| O6_OR15m_stp_le1 | 361 | 179 | 72 | 110 | 10.0 | 60 | 60 | +14.10 | +6.96 | 0.64 | 0.58 | 0.983 |
| O6_OR30m_stp_ge0.5 | 594 | 297 | 125 | 172 | 10.0 | 60 | 60 | +14.85 | +4.18 | 0.64 | 0.56 | 0.981 |
| PB | 4049 | 2261 | 965 | 823 | 10.0 | 60 | 60 | -1.43 | +3.27 | 0.50 | 0.55 | 0.234 |
| PE | 3248 | 1732 | 731 | 785 | 5.6 | 60 | 60 | +1.34 | +2.04 | 0.53 | 0.54 | 0.900 |
| SM | 1457 | 774 | 294 | 389 | 7.4 | 60 | 60 | +3.38 | -0.37 | 0.55 | 0.52 | 0.710 |
| ST | 3234 | 1717 | 765 | 752 | 10.0 | 60 | 60 | +1.15 | +1.08 | 0.52 | 0.54 | 0.925 |
| WT | 4762 | 2567 | 1099 | 1096 | 7.0 | 45 | 33.75 | -0.47 | -0.98 | 0.59 | 0.60 | 0.071 |


Streams listed but not scored: D6_SM_t60_sst_ASIA (median stop 20 pts < 30: the absolute-point grid cannot arm); basket legs ES and RTY (no 1-s path in the box; only the NQ leg of B3 is scored, as B3_NQ, multi-day time-exit baseline at 1 lot, labelled); CR is a single-leg simplification of a scale-out book with 8-24 pt stops, so most rules never arm there.

## 2. Multiplicity statement

Rules tried: 192 (12 groups) x 20 streams = 3840 cells, each with 20 placebo draws (76800 placebo runs); pooled cells 2 x 192. Cells with PRE delta > 0: 262 of 3840; with PRE CI lower bound > 0: 6 (chance count at 2.5% one-sided = 96); with PRE > 0 AND HOLD > 0: 139 (chance if independent ~ 960 at 25%, far more if the same bias moves both windows). White reality check on PRE, best of 192 per stream (p): B3_NQ 0.643, D6_HM_t75_s90_NYAM 0.993, D6_KB_t60_s75_ASIA 0.994, D6_PB7_PB5_ASIA 0.995, D6_TB4B_ASIA 0.869, D6_TB4W_03_ASIA 0.942, DN 0.745, EM 0.641, HM 0.459, KB 0.951, MA 0.996, MV 0.864, O6_LV_RN_BH 0.956, O6_OR15m_stp_le1 0.983, O6_OR30m_stp_ge0.5 0.981, PB 0.234, PE 0.900, SM 0.710, ST 0.925, WT 0.071. Pooled over the 11 intraday books RC p = 0.882 (best rule F10_m40_r3_t4, t -0.17); six stack books RC p = 0.914. Best-of-N therefore applies to every positive number below: a cell with a positive PRE delta is expected by chance in a grid this size.

## 3.IN-SAMPLE mean paired delta, pts/trade, mean over the rules of each group - IN-SAMPLE (PRE 2024-02..2025-06, raw)

| fam | B3_NQ | D6_HM_t75_s90_NYAM | D6_KB_t60_s75_ASIA | D6_PB7_PB5_ASIA | D6_TB4B_ASIA | D6_TB4W_03_ASIA | DN | EM | HM | KB | MA | MV | O6_LV_RN_BH | O6_OR15m_stp_le1 | O6_OR30m_stp_ge0.5 | PB | PE | SM | ST | WT | ALL(11 books) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F1 | -23.43 | -7.26 | -5.44 | -6.78 | -3.98 | -3.68 | -1.33 | -1.25 | -0.60 | -2.92 | -2.49 | -2.35 | -8.94 | -7.32 | -4.87 | -0.55 | -2.11 | -2.90 | -1.54 | -0.36 | -1.67 |
| F2 | -22.80 | -6.96 | -5.36 | -6.17 | -3.99 | -3.80 | -1.22 | -1.15 | -0.46 | -2.89 | -2.48 | -2.37 | -8.63 | -7.43 | -4.81 | -0.26 | -2.10 | -2.34 | -1.42 | -0.20 | -1.53 |
| F3 | -20.98 | -6.06 | -5.56 | -6.59 | -4.20 | -3.29 | -1.09 | -1.44 | -0.50 | -2.59 | -2.91 | -2.18 | -8.62 | -7.64 | -4.64 | -0.45 | -1.92 | -3.14 | -1.92 | -0.32 | -1.68 |
| F4 | -18.44 | -6.04 | -5.22 | -6.82 | -3.27 | -3.17 | -1.31 | -1.27 | -0.89 | -2.77 | -2.31 | -2.01 | -8.81 | -6.27 | -4.10 | -0.66 | -2.25 | -2.70 | -1.38 | -0.34 | -1.63 |
| F5 | -23.41 | -4.60 | -5.08 | -5.08 | -3.88 | -3.17 | -0.73 | -0.55 | -0.44 | -2.43 | -2.76 | -1.77 | -6.84 | -6.14 | -4.50 | -0.31 | -1.94 | -1.62 | -1.43 | -0.24 | -1.29 |
| F6 | -19.35 | -4.57 | -5.26 | -6.01 | -3.71 | -2.68 | -0.64 | -0.95 | -0.60 | -2.37 | -2.92 | -1.90 | -4.34 | -6.14 | -3.92 | -0.05 | -1.60 | -2.64 | -1.66 | -0.32 | -1.42 |
| F7 | -6.06 | -4.47 | -4.56 | -9.41 | -4.60 | -3.69 | -0.44 | -0.70 | -0.55 | -2.10 | -2.03 | -1.27 | -2.71 | -4.24 | -4.09 | +0.63 | -1.24 | -3.20 | -1.31 | -0.33 | -1.14 |
| F8 | -20.69 | -5.03 | -4.60 | -5.86 | -3.52 | -3.29 | -0.64 | +0.01 | +0.09 | -1.80 | -2.16 | -1.38 | -6.68 | -6.12 | -4.67 | +0.44 | -1.43 | -1.81 | -0.95 | +0.03 | -0.87 |
| F9 | -24.09 | -5.24 | -4.39 | -4.26 | -2.86 | -2.84 | -0.02 | +0.29 | +0.51 | -1.68 | -2.01 | -1.15 | -7.63 | -5.58 | -4.44 | +0.33 | -1.38 | -1.11 | -0.61 | +0.28 | -0.60 |
| F10 | -20.92 | -6.04 | -4.38 | -5.00 | -2.54 | -2.61 | -0.97 | -0.61 | -0.16 | -1.89 | -2.20 | -1.46 | -8.32 | -5.83 | -4.54 | -0.10 | -1.62 | -1.72 | -1.31 | -0.17 | -1.11 |
| F11 | -23.42 | -5.67 | -4.83 | -4.85 | -2.95 | -3.20 | -1.07 | -0.76 | -0.43 | -2.21 | -2.29 | -1.65 | -7.58 | -5.09 | -3.55 | -0.33 | -2.01 | -1.51 | -1.51 | -0.19 | -1.27 |
| F12 | -21.14 | -6.47 | -5.37 | -7.00 | -4.06 | -3.86 | -1.04 | -0.86 | -0.49 | -2.70 | -2.43 | -2.13 | -8.60 | -6.56 | -4.56 | -0.25 | -1.91 | -2.84 | -1.56 | -0.39 | -1.51 |

## 3.HOLDOUT mean paired delta, pts/trade, mean over the rules of each group - HOLDOUT (2025-07-01..2026-02-06, one look per group)

| fam | B3_NQ | D6_HM_t75_s90_NYAM | D6_KB_t60_s75_ASIA | D6_PB7_PB5_ASIA | D6_TB4B_ASIA | D6_TB4W_03_ASIA | DN | EM | HM | KB | MA | MV | O6_LV_RN_BH | O6_OR15m_stp_le1 | O6_OR30m_stp_ge0.5 | PB | PE | SM | ST | WT | ALL(11 books) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F1 | -64.74 | -5.62 | -0.95 | -3.01 | +6.49 | +0.49 | -1.03 | -1.47 | -0.97 | -3.48 | -4.41 | -0.39 | -2.77 | -5.57 | -0.69 | -2.26 | -2.30 | +0.77 | +0.05 | -0.14 | -1.42 |
| F2 | -63.80 | -5.99 | -1.25 | -3.69 | +6.81 | +0.16 | -0.60 | -0.52 | -0.77 | -3.68 | -4.37 | +0.00 | -3.83 | -4.86 | -1.18 | -2.04 | -1.87 | +0.70 | -0.05 | +0.34 | -1.17 |
| F3 | -65.43 | -4.78 | -1.38 | -3.13 | +6.55 | +0.25 | -1.60 | -1.44 | -0.84 | -3.17 | -4.13 | -0.61 | -2.30 | -4.96 | -2.76 | -1.96 | -2.70 | +0.11 | -0.16 | -0.09 | -1.51 |
| F4 | -51.71 | -5.08 | -0.41 | -2.20 | +6.68 | +1.04 | -0.66 | -1.80 | -0.53 | -3.23 | -4.66 | -0.47 | -0.75 | -5.16 | -0.81 | -2.52 | -2.20 | +0.39 | +0.20 | -0.19 | -1.42 |
| F5 | -64.03 | -4.49 | -1.46 | -2.39 | +6.55 | +0.82 | -0.76 | -0.87 | -0.85 | -2.63 | -3.75 | -0.65 | -1.58 | -4.14 | -2.64 | -1.51 | -1.67 | +0.72 | +0.36 | +0.23 | -1.04 |
| F6 | -64.85 | -1.36 | -0.97 | -1.99 | +6.88 | +0.60 | -1.61 | -1.61 | +0.03 | -2.36 | -3.77 | -0.58 | -1.27 | -3.14 | -3.47 | -2.24 | -2.33 | -0.14 | +0.28 | -0.18 | -1.32 |
| F7 | -56.73 | -0.13 | -1.87 | -2.55 | +5.55 | -0.28 | -2.11 | -0.52 | +0.03 | -2.57 | -1.37 | +0.18 | -1.38 | -2.75 | -2.92 | -2.46 | -2.64 | -0.12 | -0.79 | -0.05 | -1.13 |
| F8 | -61.75 | -3.18 | -0.81 | -2.45 | +7.80 | +1.48 | -0.08 | +0.11 | +0.23 | -2.06 | -2.67 | +0.24 | -1.98 | -4.28 | -1.98 | -1.00 | -1.40 | +1.59 | +0.61 | +0.67 | -0.34 |
| F9 | -60.80 | -5.02 | -0.40 | -1.75 | +7.49 | +1.55 | +0.67 | +0.88 | +0.05 | -2.34 | -2.79 | +0.64 | -2.43 | -2.68 | -1.17 | -0.34 | -0.41 | +2.55 | +1.38 | +1.19 | +0.13 |
| F10 | -61.86 | -4.86 | -0.97 | -1.86 | +5.09 | +1.02 | -0.58 | -0.74 | -0.41 | -2.37 | -3.49 | +0.06 | -1.77 | -4.40 | -1.38 | -1.29 | -1.54 | +1.07 | +0.27 | +0.13 | -0.81 |
| F11 | -59.55 | -7.05 | -1.78 | -2.38 | +4.69 | +0.37 | -0.84 | -0.53 | -1.31 | -3.20 | -3.94 | -1.00 | -3.79 | -2.80 | -2.37 | -1.84 | -1.91 | +0.88 | -0.27 | -0.01 | -1.27 |
| F12 | -69.95 | -5.36 | -1.30 | -2.33 | +7.41 | +0.41 | -0.58 | -0.49 | -0.44 | -3.66 | -3.39 | +0.11 | -2.68 | -4.93 | -1.69 | -2.16 | -2.21 | +1.05 | +0.02 | +0.24 | -1.05 |

## 3.X mean paired delta, pts/trade, mean over the rules of each group - X span (2023-04..2024-01)

| fam | B3_NQ | D6_HM_t75_s90_NYAM | D6_KB_t60_s75_ASIA | D6_PB7_PB5_ASIA | D6_TB4B_ASIA | D6_TB4W_03_ASIA | DN | EM | HM | KB | MA | MV | O6_LV_RN_BH | O6_OR15m_stp_le1 | O6_OR30m_stp_ge0.5 | PB | PE | SM | ST | WT | ALL(11 books) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F1 | -39.98 | -5.98 | +0.22 | -1.77 | -1.28 | +2.44 | +0.70 | -1.43 | -0.47 | +0.71 | -1.52 | +1.45 | +0.05 | +4.50 | -0.75 | -1.38 | -0.85 | -0.66 | -1.39 | -0.18 | -0.46 |
| F2 | -37.44 | -6.05 | -0.14 | -1.87 | -1.51 | +2.38 | +0.87 | -1.15 | -0.43 | +0.24 | -1.78 | +1.15 | +1.01 | +3.68 | -1.31 | -1.52 | -0.88 | -0.14 | -1.35 | -0.17 | -0.47 |
| F3 | -40.36 | -5.59 | -0.34 | -2.15 | -1.85 | +1.97 | +0.19 | -1.47 | -0.66 | +0.55 | -1.80 | +1.03 | +0.20 | +4.39 | -0.76 | -1.74 | -0.94 | -0.90 | -1.28 | -0.20 | -0.66 |
| F4 | -34.23 | -3.64 | +0.34 | -1.46 | -1.13 | +2.14 | +1.10 | -2.33 | +0.16 | +0.99 | -1.58 | +1.64 | +0.16 | +3.52 | -0.87 | -1.65 | -0.74 | -0.80 | -0.90 | -0.18 | -0.39 |
| F5 | -35.46 | -5.81 | +0.13 | -1.83 | -2.23 | +2.31 | +0.43 | -1.37 | -0.21 | +0.58 | -1.16 | +1.03 | +0.41 | +3.74 | -0.89 | -1.37 | -0.75 | +0.21 | -1.05 | -0.07 | -0.34 |
| F6 | -38.51 | -4.40 | -0.45 | -2.92 | -1.91 | +2.00 | +0.14 | -1.64 | -0.25 | +0.75 | -1.73 | +1.20 | +0.78 | +4.30 | -0.94 | -1.64 | -0.61 | -0.61 | -1.03 | -0.36 | -0.53 |
| F7 | -36.31 | -3.98 | -0.19 | -5.50 | -0.79 | -0.77 | -1.77 | -0.83 | -1.05 | -0.39 | -1.66 | -0.08 | -1.01 | +4.25 | +0.35 | -1.86 | -1.42 | -1.35 | -2.18 | -0.87 | -1.22 |
| F8 | -36.32 | -5.84 | +0.15 | -1.38 | -1.22 | +2.53 | +0.64 | -0.66 | -0.24 | +0.58 | -1.09 | +1.24 | +1.06 | +4.07 | -0.64 | -1.27 | -0.67 | -0.10 | -1.20 | +0.14 | -0.24 |
| F9 | -36.83 | -6.41 | +0.68 | -0.97 | -1.76 | +2.94 | +1.21 | -0.93 | -0.14 | +0.84 | -0.59 | +1.36 | +0.62 | +3.92 | -0.72 | -1.31 | -0.24 | +0.73 | -0.66 | +0.38 | +0.06 |
| F10 | -37.28 | -5.43 | -1.09 | -1.60 | -1.51 | +1.49 | +0.42 | -1.33 | -0.16 | +0.28 | -1.04 | +1.31 | +0.85 | +4.07 | -0.18 | -1.35 | -0.37 | -0.58 | -0.95 | -0.03 | -0.34 |
| F11 | -34.81 | -5.54 | +0.54 | -2.02 | -1.82 | +2.41 | +0.78 | -1.09 | -0.50 | +0.37 | -0.87 | +1.08 | +0.66 | +3.97 | -0.43 | -1.23 | -0.38 | +0.45 | -0.81 | +0.12 | -0.19 |
| F12 | -40.00 | -5.77 | -0.30 | -2.46 | -1.29 | +1.83 | +0.61 | -1.47 | -0.32 | +0.46 | -1.15 | +1.06 | +0.57 | +4.22 | -0.92 | -1.62 | -0.63 | -0.52 | -1.45 | -0.29 | -0.48 |

## 4. The live JADE rule (min profit 20, 3 of 4, 8-pt trail) vs hold-to-bracket, per book (IN-SAMPLE and HOLDOUT side by side)

| stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B3_NQ | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 78 | -20.17 [-75.19,+34.84] (78.59) | 36 | -61.09 [-145.72,+23.54] (120.90) | -38.51 (50.69) | -420|-1,375 | +79.35|-99.53 | 74 (95%) | +0.46 | 0.60>0.90 | 0.05|0.25 | -20.17|-19.85|-20.26 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05,n_PRE<100 |
| D6_HM_t75_s90_NYAM | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 427 | -7.02 [-12.75,-1.29] (8.18) | 197 | -2.55 [-10.58,+5.47] (11.46) | -6.83 (12.81) | -7,995|-3,144 | +22.71|-29.73 | 352 (82%) | -1.00 | 0.62>0.78 | 1.00|1.00 | -8.13|-7.43|-6.97 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_KB_t60_s75_ASIA | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 704 | -5.42 [-8.95,-1.89] (5.05) | 321 | -1.06 [-6.98,+4.85] (8.45) | -0.11 (9.50) | -10,173|-2,135 | +17.00|-22.42 | 542 (77%) | -0.88 | 0.61>0.79 | 1.00|1.00 | -6.70|-5.65|-5.27 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_PB7_PB5_ASIA | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 342 | -5.57 [-10.58,-0.56] (7.16) | 192 | -3.43 [-9.68,+2.83] (8.93) | -1.40 (12.03) | -5,079|-4,110 | +17.30|-22.87 | 279 (82%) | -0.81 | 0.61>0.83 | 1.00|0.90 | -6.86|-5.78|-5.52 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_TB4B_ASIA | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 450 | -3.91 [-8.38,+0.57] (6.39) | 200 | +8.21 [+0.99,+15.42] (10.31) | -1.21 (9.50) | -4,686|10,258 | +17.28|-21.19 | 348 (77%) | -0.79 | 0.58>0.79 | 1.00|1.00 | -5.12|-4.11|-3.89 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_TB4W_03_ASIA | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 800 | -3.55 [-6.62,-0.48] (4.38) | 369 | +0.17 [-4.41,+4.76] (6.55) | +2.46 (8.80) | -7,576|401 | +16.62|-20.17 | 588 (74%) | -0.83 | 0.56>0.75 | 1.00|1.00 | -4.74|-3.78|-3.44 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| DN | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 1762 | -0.92 [-3.11,+1.26] (3.12) | 782 | +0.26 [-3.04,+3.55] (4.71) | +0.84 (4.85) | -4,346|1,252 | +17.99|-18.92 | 1300 (74%) | -0.86 | 0.54>0.75 | 1.00|1.00 | -1.96|-1.24|-0.77 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| EM | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 871 | -0.05 [-3.10,+2.99] (4.35) | 366 | -0.52 [-5.40,+4.36] (6.97) | -2.24 (5.97) | -124|-1,185 | +18.75|-18.81 | 651 (75%) | -0.76 | 0.54>0.77 | 1.00|1.00 | -1.03|-0.32|-0.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| HM | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 1561 | -0.39 [-2.69,+1.91] (3.29) | 698 | +0.19 [-3.16,+3.54] (4.78) | +0.17 (4.89) | -1,620|830 | +18.39|-18.78 | 1143 (73%) | -0.73 | 0.52>0.75 | 1.00|1.00 | -1.37|-0.64|-0.20 | DEAD | mean_up,neighbours_agree,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| KB | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 1854 | -2.67 [-4.72,-0.62] (2.93) | 756 | -3.63 [-6.80,-0.46] (4.52) | +0.02 (4.43) | -7,142|-6,625 | +16.66|-19.33 | 1353 (73%) | -0.80 | 0.55>0.76 | 1.00|1.00 | -3.72|-2.94|-2.56 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| MA | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 997 | -2.27 [-5.13,+0.60] (4.09) | 446 | -3.82 [-8.15,+0.52] (6.19) | -1.05 (5.91) | -6,025|-10,641 | +16.85|-19.11 | 722 (72%) | -0.73 | 0.53>0.74 | 1.00|0.95 | -3.24|-2.52|-2.16 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| MV | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 2025 | -2.13 [-4.12,-0.14] (2.84) | 845 | +0.68 [-2.40,+3.75] (4.39) | +0.83 (4.63) | -11,502|3,569 | +16.76|-18.89 | 1454 (72%) | -0.80 | 0.53>0.74 | 1.00|1.00 | -3.14|-2.41|-2.00 | DEAD | mean_up,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| O6_LV_RN_BH | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 134 | -9.08 [-16.38,-1.78] (10.43) | 78 | -2.06 [-11.58,+7.45] (13.59) | +1.86 (15.14) | -3,245|-1,005 | +12.79|-21.87 | 98 (73%) | -0.98 | 0.62>0.70 | 0.70|0.95 | -10.11|-9.52|-8.53 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| O6_OR15m_stp_le1 | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 179 | -7.14 [-13.94,-0.34] (9.71) | 72 | -5.79 [-15.99,+4.41] (14.57) | +2.94 (12.05) | -3,408|-2,607 | +15.89|-23.03 | 143 (80%) | -1.10 | 0.64>0.82 | 1.00|0.25 | -8.31|-7.60|-6.82 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| O6_OR30m_stp_ge0.5 | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 297 | -5.07 [-10.44,+0.30] (7.67) | 125 | -0.47 [-8.26,+7.32] (11.13) | -3.21 (9.79) | -4,014|-365 | +17.04|-22.11 | 236 (79%) | -1.02 | 0.64>0.79 | 1.00|1.00 | -6.13|-5.52|-4.99 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| PB | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 2261 | -0.27 [-2.20,+1.67] (2.76) | 965 | -1.51 [-4.51,+1.49] (4.29) | -1.52 (4.28) | -1,612|-9,093 | +17.72|-17.99 | 1617 (72%) | -0.83 | 0.50>0.72 | 1.00|1.00 | -1.30|-0.54|-0.14 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| PE | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 1732 | -1.95 [-4.07,+0.17] (3.03) | 731 | -1.44 [-4.54,+1.66] (4.44) | -0.43 (4.50) | -5,138|-3,363 | +17.03|-18.98 | 1260 (73%) | -0.77 | 0.53>0.74 | 1.00|1.00 | -2.98|-2.21|-1.84 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| SM | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 774 | -1.90 [-5.14,+1.35] (4.63) | 294 | +1.75 [-3.97,+7.47] (8.17) | -0.09 (6.53) | -2,501|2,666 | +17.32|-19.21 | 565 (73%) | -0.74 | 0.55>0.75 | 1.00|1.00 | -2.88|-2.17|-1.82 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| ST | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 1717 | -1.45 [-3.69,+0.79] (3.20) | 765 | +0.51 [-2.79,+3.81] (4.72) | -1.52 (4.69) | -6,652|2,450 | +17.40|-18.85 | 1239 (72%) | -0.81 | 0.52>0.74 | 1.00|1.00 | -2.49|-1.73|-1.41 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| WT | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 2567 | -0.33 [-1.22,+0.55] (1.26) | 1099 | +0.35 [-1.00,+1.70] (1.93) | -0.00 (2.01) | -1,595|1,672 | +6.69|-7.03 | 1343 (52%) | -0.60 | 0.59>0.69 | 1.00|1.00 | -1.19|-0.52|-0.24 | DEAD | mean_up,neighbours_agree,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |


Pooled (cluster = label day x session across books):

| stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 11 BOOKS | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 18121 | -1.25 [-2.38,-0.11] (1.62) | 7747 | -0.64 [-2.39,+1.11] (2.49) | -0.37 (2.45) | -48,256|-18,468 | +15.92|-17.16 | 12647 (70%) | -0.76 | 0.54>0.74 | 1.00|1.00 | -2.24|-1.51|-1.13 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| STACK6 | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 10205 | -1.35 [-2.54,-0.15] (1.71) | 4343 | -0.55 [-2.40,+1.31] (2.65) | -0.31 (2.56) | -24,648|-2,370 | +14.65|-16.00 | 6903 (68%) | -0.73 | 0.55>0.73 | 1.00|1.00 | -2.33|-1.59|-1.24 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |


## 5. Per book: JADE control, best rule by IN-SAMPLE delta, best rule by HOLDOUT delta (regardless of verdict)

### B3_NQ

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | B3_NQ | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 78 | -20.17 [-75.19,+34.84] (78.59) | 36 | -61.09 [-145.72,+23.54] (120.90) | -38.51 (50.69) | -420|-1,375 | +79.35|-99.53 | 74 (95%) | +0.46 | 0.60>0.90 | 0.05|0.25 | -20.17|-19.85|-20.26 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05,n_PRE<100 |
| best IN-SAMPLE | B3_NQ | F7_t60_x10 | time stop 60 min if unrealised < +10 | 78 | +8.83 [-32.69,+50.35] (59.31) | 36 | -59.83 [-136.48,+16.83] (109.51) | -30.97 (47.52) | 184|-1,346 | +61.29|-52.46 | 45 (58%) | +0.00 | 0.60>0.41 | 0.95|0.05 | +8.83|+8.83|+8.83 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05,n_PRE<100 |
| best HOLDOUT | B3_NQ | F7_t20_x10 | time stop 20 min if unrealised < +10 | 78 | -10.06 [-51.44,+31.33] (59.12) | 36 | -26.40 [-88.09,+35.28] (88.12) | -33.52 (43.82) | -209|-594 | +50.31|-60.37 | 45 (58%) | +0.00 | 0.60>0.37 | 0.25|0.35 | -10.06|-10.06|-10.49 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05,n_PRE<100 |

### D6_HM_t75_s90_NYAM

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | D6_HM_t75_s90_NYAM | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 427 | -7.02 [-12.75,-1.29] (8.18) | 197 | -2.55 [-10.58,+5.47] (11.46) | -6.83 (12.81) | -7,995|-3,144 | +22.71|-29.73 | 352 (82%) | -1.00 | 0.62>0.78 | 1.00|1.00 | -8.13|-7.43|-6.97 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | D6_HM_t75_s90_NYAM | F6_tf5_a30 | EMA20 5-min touch after +30 | 427 | -1.49 [-5.43,+2.46] (5.64) | 197 | -1.83 [-7.30,+3.64] (7.82) | -2.85 (8.69) | -1,692|-2,256 | +9.98|-11.47 | 146 (34%) | -0.01 | 0.62>0.56 | 1.00|0.95 | -1.74|-1.43|-1.51 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | D6_HM_t75_s90_NYAM | F7_t60_x20 | time stop 60 min if unrealised < +20 | 427 | -3.15 [-6.78,+0.47] (5.17) | 197 | +1.56 [-3.73,+6.84] (7.55) | -1.60 (11.09) | -3,592|1,916 | +7.31|-10.46 | 122 (29%) | -0.28 | 0.62>0.56 | 0.60|0.90 | -3.34|-3.32|-3.12 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |

### D6_KB_t60_s75_ASIA

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | D6_KB_t60_s75_ASIA | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 704 | -5.42 [-8.95,-1.89] (5.05) | 321 | -1.06 [-6.98,+4.85] (8.45) | -0.11 (9.50) | -10,173|-2,135 | +17.00|-22.42 | 542 (77%) | -0.88 | 0.61>0.79 | 1.00|1.00 | -6.70|-5.65|-5.27 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | D6_KB_t60_s75_ASIA | F7_t60_x10 | time stop 60 min if unrealised < +10 | 704 | -1.74 [-5.49,+2.01] (5.36) | 321 | -3.90 [-9.13,+1.32] (7.46) | -0.02 (10.71) | -3,264|-7,834 | +17.23|-18.97 | 409 (58%) | -0.81 | 0.61>0.48 | 1.00|0.05 | -2.30|-2.16|-1.60 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | D6_KB_t60_s75_ASIA | F6_tf5_a10 | EMA20 5-min touch after +10 | 704 | -4.74 [-8.50,-0.98] (5.37) | 321 | +1.06 [-4.72,+6.84] (8.26) | -2.12 (10.27) | -8,899|2,133 | +17.42|-22.16 | 461 (65%) | -0.25 | 0.61>0.51 | 1.00|0.95 | -5.55|-4.72|-4.75 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |

### D6_PB7_PB5_ASIA

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | D6_PB7_PB5_ASIA | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 342 | -5.57 [-10.58,-0.56] (7.16) | 192 | -3.43 [-9.68,+2.83] (8.93) | -1.40 (12.03) | -5,079|-4,110 | +17.30|-22.87 | 279 (82%) | -0.81 | 0.61>0.83 | 1.00|0.90 | -6.86|-5.78|-5.52 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | D6_PB7_PB5_ASIA | F10_m30_r4_t16 | JADE min profit 30, 4 of 4, trail 16 | 342 | -2.28 [-6.07,+1.51] (5.41) | 192 | +0.13 [-4.58,+4.83] (6.72) | -1.28 (6.72) | -2,079|154 | +9.86|-12.14 | 156 (46%) | -0.69 | 0.61>0.68 | 1.00|1.00 | -3.00|-2.54|-2.08 | DEAD | mean_up,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | D6_PB7_PB5_ASIA | F10_m20_r4_t12 | JADE min profit 20, 4 of 4, trail 12 | 342 | -3.11 [-7.48,+1.25] (6.23) | 192 | +1.62 [-3.58,+6.82] (7.42) | +0.48 (8.10) | -2,839|1,944 | +12.90|-16.02 | 193 (56%) | -0.92 | 0.61>0.66 | 1.00|1.00 | -3.99|-3.48|-3.06 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |

### D6_TB4B_ASIA

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | D6_TB4B_ASIA | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 450 | -3.91 [-8.38,+0.57] (6.39) | 200 | +8.21 [+0.99,+15.42] (10.31) | -1.21 (9.50) | -4,686|10,258 | +17.28|-21.19 | 348 (77%) | -0.79 | 0.58>0.79 | 1.00|1.00 | -5.12|-4.11|-3.89 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | D6_TB4B_ASIA | F10_m40_r4_t4 | JADE min profit 40, 4 of 4, trail 4 | 450 | +0.14 [-2.51,+2.78] (3.78) | 200 | +2.11 [-2.01,+6.23] (5.88) | -1.10 (3.90) | 166|2,642 | +7.17|-7.04 | 139 (31%) | -0.57 | 0.58>0.64 | 1.00|1.00 | -0.37|-0.09|+0.28 | DEAD | neighbours_agree,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | D6_TB4B_ASIA | F8_a20_n60 | stall 60s without new MFE after +20 | 450 | -3.38 [-7.80,+1.03] (6.31) | 200 | +9.16 [+1.84,+16.48] (10.46) | -0.81 (9.59) | -4,061|11,448 | +17.57|-20.95 | 351 (78%) | -1.35 | 0.58>0.80 | 1.00|1.00 | -4.62|-3.96|-3.21 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |

### D6_TB4W_03_ASIA

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | D6_TB4W_03_ASIA | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 800 | -3.55 [-6.62,-0.48] (4.38) | 369 | +0.17 [-4.41,+4.76] (6.55) | +2.46 (8.80) | -7,576|401 | +16.62|-20.17 | 588 (74%) | -0.83 | 0.56>0.75 | 1.00|1.00 | -4.74|-3.78|-3.44 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | D6_TB4W_03_ASIA | F10_m40_r4_t4 | JADE min profit 40, 4 of 4, trail 4 | 800 | -0.18 [-1.92,+1.57] (2.49) | 369 | +3.13 [+0.28,+5.98] (4.07) | -0.02 (3.79) | -374|7,219 | +5.96|-6.13 | 221 (28%) | -0.53 | 0.56>0.61 | 1.00|1.00 | -0.66|-0.38|-0.04 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | D6_TB4W_03_ASIA | F10_m40_r4_t4 | JADE min profit 40, 4 of 4, trail 4 | 800 | -0.18 [-1.92,+1.57] (2.49) | 369 | +3.13 [+0.28,+5.98] (4.07) | -0.02 (3.79) | -374|7,219 | +5.96|-6.13 | 221 (28%) | -0.53 | 0.56>0.61 | 1.00|1.00 | -0.66|-0.38|-0.04 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |

### DN

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | DN | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 1762 | -0.92 [-3.11,+1.26] (3.12) | 782 | +0.26 [-3.04,+3.55] (4.71) | +0.84 (4.85) | -4,346|1,252 | +17.99|-18.92 | 1300 (74%) | -0.86 | 0.54>0.75 | 1.00|1.00 | -1.96|-1.24|-0.77 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | DN | F9e_a30_w300_t0.4 | efficiency exit: ER(300s)<0.4 and >=3pt off high after +30 | 1762 | +0.58 [-1.32,+2.47] (2.71) | 782 | +0.99 [-1.87,+3.86] (4.09) | +0.81 (4.23) | 2,709|4,860 | +13.94|-13.36 | 1135 (64%) | -1.06 | 0.54>0.69 | 1.00|1.00 | -0.43|+0.12|+0.73 | DEAD | paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | DN | F10_m30_r3_t4 | JADE min profit 30, 3 of 4, trail 4 | 1762 | -0.18 [-2.05,+1.70] (2.68) | 782 | +1.23 [-1.63,+4.08] (4.08) | +0.71 (4.16) | -825|5,999 | +13.64|-13.82 | 1115 (63%) | -1.05 | 0.54>0.70 | 1.00|1.00 | -1.16|-0.63|+0.03 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |

### EM

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | EM | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 871 | -0.05 [-3.10,+2.99] (4.35) | 366 | -0.52 [-5.40,+4.36] (6.97) | -2.24 (5.97) | -124|-1,185 | +18.75|-18.81 | 651 (75%) | -0.76 | 0.54>0.77 | 1.00|1.00 | -1.03|-0.32|-0.00 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | EM | F9e_a20_w300_t0.4 | efficiency exit: ER(300s)<0.4 and >=3pt off high after +20 | 871 | +1.24 [-1.82,+4.30] (4.38) | 366 | +0.54 [-4.39,+5.47] (7.04) | -1.28 (6.04) | 2,882|1,244 | +19.32|-18.08 | 651 (75%) | -1.13 | 0.54>0.76 | 1.00|1.00 | +0.27|+0.71|+1.32 | DEAD | paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | EM | F9e_a30_w300_t0.4 | efficiency exit: ER(300s)<0.4 and >=3pt off high after +30 | 871 | +0.45 [-2.23,+3.13] (3.83) | 366 | +2.08 [-2.19,+6.34] (6.09) | +0.09 (5.39) | 1,039|4,754 | +13.92|-13.47 | 567 (65%) | -1.03 | 0.54>0.69 | 1.00|1.00 | -0.52|-0.02|+0.55 | DEAD | neighbours_agree,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |

### HM

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | HM | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 1561 | -0.39 [-2.69,+1.91] (3.29) | 698 | +0.19 [-3.16,+3.54] (4.78) | +0.17 (4.89) | -1,620|830 | +18.39|-18.78 | 1143 (73%) | -0.73 | 0.52>0.75 | 1.00|1.00 | -1.37|-0.64|-0.20 | DEAD | mean_up,neighbours_agree,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | HM | F9e_a30_w300_t0.3 | efficiency exit: ER(300s)<0.3 and >=3pt off high after +30 | 1561 | +1.26 [-0.75,+3.27] (2.87) | 698 | -0.62 [-3.40,+2.17] (3.98) | -1.08 (4.12) | 5,255|-2,693 | +14.75|-13.49 | 1039 (67%) | -1.07 | 0.52>0.68 | 1.00|1.00 | +0.25|+0.79|+1.38 | DEAD | holdout_sign_agrees,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | HM | F7_t60_x20 | time stop 60 min if unrealised < +20 | 1561 | -1.02 [-2.98,+0.94] (2.80) | 698 | +2.12 [-0.78,+5.02] (4.14) | -0.40 (4.98) | -4,245|9,240 | +13.07|-14.09 | 830 (53%) | -0.70 | 0.52>0.47 | 0.05|1.00 | -1.49|-1.39|-0.93 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,SPAN2<=0,NOTC<=0,RC_p>0.05 |

### KB

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | KB | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 1854 | -2.67 [-4.72,-0.62] (2.93) | 756 | -3.63 [-6.80,-0.46] (4.52) | +0.02 (4.43) | -7,142|-6,625 | +16.66|-19.33 | 1353 (73%) | -0.80 | 0.55>0.76 | 1.00|1.00 | -3.72|-2.94|-2.56 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | KB | F10_m40_r3_t4 | JADE min profit 40, 3 of 4, trail 4 | 1854 | -0.30 [-1.74,+1.14] (2.06) | 756 | -0.54 [-2.66,+1.59] (3.04) | -0.22 (3.00) | -947|-848 | +8.65|-8.95 | 977 (53%) | -0.89 | 0.55>0.64 | 1.00|1.00 | -1.20|-0.68|-0.17 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | KB | F10_m40_r4_t4 | JADE min profit 40, 4 of 4, trail 4 | 1854 | -0.45 [-1.71,+0.81] (1.80) | 756 | -0.26 [-2.13,+1.62] (2.68) | -0.71 (2.31) | -1,356|-440 | +6.38|-6.83 | 556 (30%) | -0.50 | 0.55>0.60 | 1.00|1.00 | -0.91|-0.66|-0.37 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |

### MA

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | MA | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 997 | -2.27 [-5.13,+0.60] (4.09) | 446 | -3.82 [-8.15,+0.52] (6.19) | -1.05 (5.91) | -6,025|-10,641 | +16.85|-19.11 | 722 (72%) | -0.73 | 0.53>0.74 | 1.00|0.95 | -3.24|-2.52|-2.16 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | MA | F10_m40_r4_t4 | JADE min profit 40, 4 of 4, trail 4 | 997 | -0.89 [-2.57,+0.78] (2.39) | 446 | -2.09 [-4.73,+0.56] (3.78) | +0.18 (3.35) | -2,374|-5,819 | +5.70|-6.60 | 282 (28%) | -0.45 | 0.53>0.57 | 1.00|0.95 | -1.30|-1.09|-0.88 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | MA | F7_t60_x10 | time stop 60 min if unrealised < +10 | 997 | -1.24 [-3.43,+0.94] (3.12) | 446 | -0.36 [-3.49,+2.78] (4.49) | -0.40 (5.32) | -3,306|-990 | +9.87|-11.11 | 404 (41%) | -0.49 | 0.53>0.45 | 0.20|0.75 | -1.56|-1.52|-1.18 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |

### MV

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | MV | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 2025 | -2.13 [-4.12,-0.14] (2.84) | 845 | +0.68 [-2.40,+3.75] (4.39) | +0.83 (4.63) | -11,502|3,569 | +16.76|-18.89 | 1454 (72%) | -0.80 | 0.53>0.74 | 1.00|1.00 | -3.14|-2.41|-2.00 | DEAD | mean_up,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | MV | F10_m40_r3_t4 | JADE min profit 40, 3 of 4, trail 4 | 2025 | +0.14 [-1.26,+1.53] (1.99) | 845 | -0.06 [-2.12,+2.00] (2.94) | +0.95 (3.24) | 745|-327 | +8.65|-8.51 | 1010 (50%) | -0.83 | 0.53>0.63 | 1.00|1.00 | -0.69|-0.22|+0.23 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | MV | F9e_a20_w120_t0.2 | efficiency exit: ER(120s)<0.2 and >=3pt off high after +20 | 2025 | -1.37 [-3.39,+0.65] (2.89) | 845 | +1.65 [-1.52,+4.83] (4.53) | +1.33 (4.71) | -7,395|8,737 | +17.68|-19.05 | 1514 (75%) | -1.20 | 0.53>0.75 | 1.00|1.00 | -2.45|-1.90|-1.15 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |

### O6_LV_RN_BH

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | O6_LV_RN_BH | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 134 | -9.08 [-16.38,-1.78] (10.43) | 78 | -2.06 [-11.58,+7.45] (13.59) | +1.86 (15.14) | -3,245|-1,005 | +12.79|-21.87 | 98 (73%) | -0.98 | 0.62>0.70 | 0.70|0.95 | -10.11|-9.52|-8.53 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | O6_LV_RN_BH | F7_t20_x20 | time stop 20 min if unrealised < +20 | 134 | -0.02 [-5.25,+5.20] (7.46) | 78 | +1.71 [-3.34,+6.77] (7.22) | -4.95 (12.92) | -8|836 | +7.88|-7.91 | 39 (29%) | -0.34 | 0.62>0.62 | 0.75|0.80 | -0.25|-0.22|-0.05 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | O6_LV_RN_BH | F7_t20_x30 | time stop 20 min if unrealised < +30 | 134 | -1.20 [-6.76,+4.35] (7.93) | 78 | +2.00 [-3.68,+7.67] (8.11) | -2.91 (14.50) | -430|973 | +8.54|-9.75 | 47 (35%) | -0.39 | 0.62>0.63 | 0.65|0.80 | -1.49|-1.45|-1.26 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |

### O6_OR15m_stp_le1

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | O6_OR15m_stp_le1 | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 179 | -7.14 [-13.94,-0.34] (9.71) | 72 | -5.79 [-15.99,+4.41] (14.57) | +2.94 (12.05) | -3,408|-2,607 | +15.89|-23.03 | 143 (80%) | -1.10 | 0.64>0.82 | 1.00|0.25 | -8.31|-7.60|-6.82 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | O6_OR15m_stp_le1 | F7_t60_x10 | time stop 60 min if unrealised < +10 | 179 | -1.19 [-4.68,+2.30] (4.98) | 72 | +1.89 [-2.70,+6.48] (6.55) | +0.28 (7.69) | -568|850 | +4.19|-5.38 | 34 (19%) | -0.18 | 0.64>0.58 | 0.70|0.75 | -1.27|-1.32|-1.24 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | O6_OR15m_stp_le1 | F7_t60_x10 | time stop 60 min if unrealised < +10 | 179 | -1.19 [-4.68,+2.30] (4.98) | 72 | +1.89 [-2.70,+6.48] (6.55) | +0.28 (7.69) | -568|850 | +4.19|-5.38 | 34 (19%) | -0.18 | 0.64>0.58 | 0.70|0.75 | -1.27|-1.32|-1.24 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,NOTC<=0,RC_p>0.05 |

### O6_OR30m_stp_ge0.5

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | O6_OR30m_stp_ge0.5 | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 297 | -5.07 [-10.44,+0.30] (7.67) | 125 | -0.47 [-8.26,+7.32] (11.13) | -3.21 (9.79) | -4,014|-365 | +17.04|-22.11 | 236 (79%) | -1.02 | 0.64>0.79 | 1.00|1.00 | -6.13|-5.52|-4.99 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | O6_OR30m_stp_ge0.5 | F7_t60_x10 | time stop 60 min if unrealised < +10 | 297 | -0.52 [-2.94,+1.90] (3.46) | 125 | -1.37 [-4.36,+1.63] (4.28) | -0.90 (5.57) | -411|-1,067 | +3.61|-4.13 | 45 (15%) | -0.18 | 0.64>0.61 | 0.95|0.05 | -0.63|-0.62|-0.49 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | O6_OR30m_stp_ge0.5 | F8_a10_n60 | stall 60s without new MFE after +10 | 297 | -7.96 [-13.80,-2.12] (8.35) | 125 | +2.54 [-6.62,+11.70] (13.08) | +0.69 (11.04) | -6,304|1,984 | +18.87|-26.83 | 250 (84%) | -1.22 | 0.64>0.86 | 0.15|1.00 | -9.03|-8.57|-7.94 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |

### PB

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | PB | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 2261 | -0.27 [-2.20,+1.67] (2.76) | 965 | -1.51 [-4.51,+1.49] (4.29) | -1.52 (4.28) | -1,612|-9,093 | +17.72|-17.99 | 1617 (72%) | -0.83 | 0.50>0.72 | 1.00|1.00 | -1.30|-0.54|-0.14 | DEAD | mean_up,holdout_sign_agrees,neighbours_agree,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | PB | F7_t60_x30 | time stop 60 min if unrealised < +30 | 2261 | +1.46 [-0.08,+3.01] (2.21) | 965 | -2.22 [-4.54,+0.11] (3.33) | -2.76 (4.29) | 8,817|-13,359 | +13.00|-11.54 | 1098 (49%) | -0.63 | 0.50>0.50 | 0.85|0.05 | +1.06|+1.13|+1.60 | DEAD | holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | PB | F9e_a30_w300_t0.3 | efficiency exit: ER(300s)<0.3 and >=3pt off high after +30 | 2261 | +0.50 [-1.18,+2.18] (2.40) | 965 | +0.58 [-2.02,+3.18] (3.71) | -1.19 (3.67) | 3,006|3,509 | +13.67|-13.17 | 1439 (64%) | -1.09 | 0.50>0.65 | 1.00|1.00 | -0.54|+0.05|+0.70 | DEAD | paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |

### PE

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | PE | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 1732 | -1.95 [-4.07,+0.17] (3.03) | 731 | -1.44 [-4.54,+1.66] (4.44) | -0.43 (4.50) | -5,138|-3,363 | +17.03|-18.98 | 1260 (73%) | -0.77 | 0.53>0.74 | 1.00|1.00 | -2.98|-2.21|-1.84 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | PE | F7_t60_x10 | time stop 60 min if unrealised < +10 | 1732 | -0.01 [-1.75,+1.72] (2.48) | 731 | -2.09 [-4.70,+0.52] (3.73) | -0.83 (3.88) | -220|-5,138 | +11.46|-11.47 | 769 (44%) | -0.58 | 0.53>0.46 | 0.75|0.15 | -0.35|-0.32|+0.07 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | PE | F9e_a30_w300_t0.4 | efficiency exit: ER(300s)<0.4 and >=3pt off high after +30 | 1732 | -1.23 [-3.06,+0.60] (2.61) | 731 | +0.07 [-2.78,+2.91] (4.07) | -0.58 (3.84) | -3,131|487 | +12.67|-13.89 | 1126 (65%) | -1.07 | 0.53>0.67 | 1.00|1.00 | -2.26|-1.69|-1.09 | DEAD | mean_up,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |

### SM

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | SM | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 774 | -1.90 [-5.14,+1.35] (4.63) | 294 | +1.75 [-3.97,+7.47] (8.17) | -0.09 (6.53) | -2,501|2,666 | +17.32|-19.21 | 565 (73%) | -0.74 | 0.55>0.75 | 1.00|1.00 | -2.88|-2.17|-1.82 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | SM | F10_m40_r3_t4 | JADE min profit 40, 3 of 4, trail 4 | 774 | +0.74 [-1.64,+3.11] (3.39) | 294 | +3.09 [-0.93,+7.10] (5.73) | -0.01 (4.46) | 1,025|4,316 | +9.85|-9.11 | 415 (54%) | -0.82 | 0.55>0.65 | 1.00|1.00 | -0.08|+0.35|+0.83 | DEAD | neighbours_agree,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | SM | F9e_a20_w120_t0.2 | efficiency exit: ER(120s)<0.2 and >=3pt off high after +20 | 774 | -1.62 [-4.93,+1.70] (4.73) | 294 | +3.51 [-2.19,+9.21] (8.14) | +1.14 (6.70) | -2,157|5,218 | +18.07|-19.69 | 593 (77%) | -1.15 | 0.55>0.77 | 1.00|1.00 | -2.66|-2.17|-1.55 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,year_share>60%,NOTC<=0,RC_p>0.05 |

### ST

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | ST | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 1717 | -1.45 [-3.69,+0.79] (3.20) | 765 | +0.51 [-2.79,+3.81] (4.72) | -1.52 (4.69) | -6,652|2,450 | +17.40|-18.85 | 1239 (72%) | -0.81 | 0.52>0.74 | 1.00|1.00 | -2.49|-1.73|-1.41 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | ST | F9e_a30_w120_t0.4 | efficiency exit: ER(120s)<0.4 and >=3pt off high after +30 | 1717 | -0.14 [-2.17,+1.88] (2.89) | 765 | +1.79 [-1.23,+4.81] (4.31) | -0.69 (4.05) | -659|8,556 | +14.07|-14.21 | 1149 (67%) | -1.13 | 0.52>0.68 | 1.00|1.00 | -1.23|-0.62|+0.01 | DEAD | mean_up,paired_CI_excludes0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | ST | F9e_a20_w300_t0.2 | efficiency exit: ER(300s)<0.2 and >=3pt off high after +20 | 1717 | -0.99 [-3.21,+1.23] (3.17) | 765 | +1.84 [-1.50,+5.18] (4.77) | -0.73 (4.73) | -4,534|8,799 | +17.48|-18.47 | 1248 (73%) | -1.17 | 0.52>0.73 | 1.00|1.00 | -2.04|-1.51|-0.90 | DEAD | mean_up,paired_CI_excludes0,SPAN2<=0,NOTC<=0,RC_p>0.05 |

### WT

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| JADE live | WT | F10_m20_r3_t8 | JADE min profit 20, 3 of 4, trail 8 | 2567 | -0.33 [-1.22,+0.55] (1.26) | 1099 | +0.35 [-1.00,+1.70] (1.93) | -0.00 (2.01) | -1,595|1,672 | +6.69|-7.03 | 1343 (52%) | -0.60 | 0.59>0.69 | 1.00|1.00 | -1.19|-0.52|-0.24 | DEAD | mean_up,neighbours_agree,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | WT | F9e_a30_w120_t0.4 | efficiency exit: ER(120s)<0.4 and >=3pt off high after +30 | 2567 | +0.67 [+0.18,+1.17] (0.71) | 1099 | +1.62 [+0.78,+2.46] (1.19) | +0.45 (1.11) | 3,229|7,790 | +2.17|-1.49 | 979 (38%) | -0.69 | 0.59>0.62 | 1.00|1.00 | -0.07|+0.39|+0.70 | DEAD | year_share>60%,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | WT | F9e_a20_w120_t0.2 | efficiency exit: ER(120s)<0.2 and >=3pt off high after +20 | 2567 | +0.29 [-0.61,+1.20] (1.30) | 1099 | +1.69 [+0.29,+3.10] (2.01) | +0.63 (2.10) | 1,403|8,139 | +7.24|-6.95 | 1690 (66%) | -1.14 | 0.59>0.70 | 1.00|1.00 | -0.85|-0.19|+0.45 | DEAD | paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |

## 6. Top 10 cells by IN-SAMPLE delta (n_PRE >= 100) and top 10 by HOLDOUT delta (n_HOLD >= 50), regardless of verdict, with what killed each

### 6a. Top 10 by IN-SAMPLE (PRE) delta

| stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates | boot CI PRE|HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PB | F7_t60_x30 | time stop 60 min if unrealised < +30 | 2261 | +1.46 [-0.08,+3.01] (2.21) | 965 | -2.22 [-4.54,+0.11] (3.33) | -2.76 (4.29) | 8,817|-13,359 | +13.00|-11.54 | 1098 (49%) | -0.63 | 0.50>0.50 | 0.85|0.05 | +1.06|+1.13|+1.60 | DEAD | holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-0.11,+2.95]|[-4.44,-0.05] |
| HM | F9e_a30_w300_t0.3 | efficiency exit: ER(300s)<0.3 and >=3pt off high after +30 | 1561 | +1.26 [-0.75,+3.27] (2.87) | 698 | -0.62 [-3.40,+2.17] (3.98) | -1.08 (4.12) | 5,255|-2,693 | +14.75|-13.49 | 1039 (67%) | -1.07 | 0.52>0.68 | 1.00|1.00 | +0.25|+0.79|+1.38 | DEAD | holdout_sign_agrees,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-0.87,+3.34]|[-3.38,+2.28] |
| HM | F9e_a30_w300_t0.4 | efficiency exit: ER(300s)<0.4 and >=3pt off high after +30 | 1561 | +1.26 [-0.75,+3.27] (2.87) | 698 | -0.62 [-3.40,+2.17] (3.98) | -1.08 (4.12) | 5,250|-2,693 | +14.75|-13.49 | 1039 (67%) | -1.07 | 0.52>0.68 | 1.00|1.00 | +0.25|+0.79|+1.37 | DEAD | holdout_sign_agrees,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-0.87,+3.34]|[-3.38,+2.28] |
| HM | F9e_a30_w300_t0.2 | efficiency exit: ER(300s)<0.2 and >=3pt off high after +30 | 1561 | +1.25 [-0.76,+3.26] (2.87) | 698 | -0.63 [-3.41,+2.16] (3.98) | -1.04 (4.12) | 5,194|-2,736 | +14.75|-13.50 | 1038 (66%) | -1.07 | 0.52>0.68 | 1.00|1.00 | +0.24|+0.78|+1.36 | DEAD | holdout_sign_agrees,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-0.89,+3.33]|[-3.39,+2.28] |
| EM | F9e_a20_w300_t0.4 | efficiency exit: ER(300s)<0.4 and >=3pt off high after +20 | 871 | +1.24 [-1.82,+4.30] (4.38) | 366 | +0.54 [-4.39,+5.47] (7.04) | -1.28 (6.04) | 2,882|1,244 | +19.32|-18.08 | 651 (75%) | -1.13 | 0.54>0.76 | 1.00|1.00 | +0.27|+0.71|+1.32 | DEAD | paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-1.91,+4.17]|[-4.45,+5.59] |
| EM | F9e_a20_w300_t0.3 | efficiency exit: ER(300s)<0.3 and >=3pt off high after +20 | 871 | +1.24 [-1.82,+4.30] (4.38) | 366 | +0.54 [-4.39,+5.47] (7.04) | -1.28 (6.04) | 2,878|1,244 | +19.32|-18.08 | 651 (75%) | -1.13 | 0.54>0.76 | 1.00|1.00 | +0.27|+0.71|+1.32 | DEAD | paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-1.91,+4.17]|[-4.45,+5.59] |
| EM | F12_eff_st | efficiency 300s<0.3 after +20 + stall 300 s after +30 | 871 | +1.24 [-1.82,+4.30] (4.38) | 366 | +0.54 [-4.39,+5.47] (7.04) | -1.28 (6.04) | 2,878|1,244 | +19.32|-18.08 | 651 (75%) | -1.13 | 0.54>0.76 | 1.00|1.00 | +0.27|+0.71|+1.32 | DEAD | neighbours_agree(no grid),paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-1.91,+4.17]|[-4.45,+5.59] |
| EM | F9e_a20_w300_t0.2 | efficiency exit: ER(300s)<0.2 and >=3pt off high after +20 | 871 | +1.23 [-1.84,+4.29] (4.38) | 366 | +0.56 [-4.37,+5.49] (7.04) | -1.27 (6.04) | 2,848|1,289 | +19.32|-18.10 | 651 (75%) | -1.13 | 0.54>0.76 | 1.00|1.00 | +0.25|+0.70|+1.32 | DEAD | paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-1.93,+4.16]|[-4.43,+5.58] |
| PB | F7_t60_x10 | time stop 60 min if unrealised < +10 | 2261 | +1.20 [-0.14,+2.54] (1.92) | 965 | -1.94 [-3.92,+0.03] (2.82) | -2.28 (3.97) | 7,247|-11,718 | +9.74|-8.53 | 816 (36%) | -0.46 | 0.50>0.46 | 0.95|0.05 | +0.94|+0.95|+1.31 | DEAD | holdout_sign_agrees,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-0.15,+2.56]|[-3.87,-0.07] |
| HM | F9e_a30_w120_t0.4 | efficiency exit: ER(120s)<0.4 and >=3pt off high after +30 | 1561 | +1.08 [-0.94,+3.10] (2.89) | 698 | -0.64 [-3.47,+2.19] (4.05) | -1.04 (4.15) | 4,494|-2,786 | +14.83|-13.75 | 1054 (68%) | -1.09 | 0.52>0.69 | 1.00|1.00 | +0.04|+0.60|+1.26 | DEAD | holdout_sign_agrees,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-1.04,+3.14]|[-3.43,+2.29] |


### 6b. Top 10 by HOLDOUT delta

| stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates | boot CI PRE|HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| D6_TB4B_ASIA | F8_a20_n60 | stall 60s without new MFE after +20 | 450 | -3.38 [-7.80,+1.03] (6.31) | 200 | +9.16 [+1.84,+16.48] (10.46) | -0.81 (9.59) | -4,061|11,448 | +17.57|-20.95 | 351 (78%) | -1.35 | 0.58>0.80 | 1.00|1.00 | -4.62|-3.96|-3.21 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-7.76,+1.00]|[+1.97,+16.64] |
| D6_TB4B_ASIA | F10_m20_r3_t4 | JADE min profit 20, 3 of 4, trail 4 | 450 | -3.30 [-7.77,+1.17] (6.38) | 200 | +9.04 [+1.74,+16.33] (10.42) | -0.42 (9.49) | -3,959|11,297 | +17.54|-20.84 | 350 (78%) | -1.35 | 0.58>0.79 | 1.00|1.00 | -4.53|-3.87|-3.13 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-7.78,+1.00]|[+1.79,+16.24] |
| D6_TB4B_ASIA | F12_gb50_st300 | give-back 50% after +20 + stall 300 s after +20 | 450 | -3.26 [-7.59,+1.08] (6.19) | 200 | +9.03 [+1.90,+16.16] (10.19) | -0.69 (9.45) | -3,907|11,290 | +17.07|-20.32 | 337 (75%) | -0.83 | 0.58>0.80 | 1.00|1.00 | -4.41|-3.53|-3.18 | DEAD | mean_up,neighbours_agree(no grid),paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-7.42,+1.07]|[+1.94,+16.20] |
| D6_TB4B_ASIA | F8_a20_n300 | stall 300s without new MFE after +20 | 450 | -3.21 [-7.56,+1.14] (6.21) | 200 | +9.00 [+2.07,+15.92] (9.90) | -0.33 (9.38) | -3,850|11,246 | +16.30|-19.51 | 325 (72%) | -1.21 | 0.58>0.78 | 1.00|1.00 | -4.30|-3.74|-3.06 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-7.57,+1.23]|[+2.04,+15.98] |
| D6_TB4B_ASIA | F9v_a20_w120_p6 | velocity exit: adverse 6 pts over 120s after +20 | 450 | -3.63 [-8.06,+0.80] (6.33) | 200 | +8.97 [+1.82,+16.13] (10.22) | -0.13 (9.55) | -4,361|11,219 | +17.20|-20.84 | 340 (76%) | -1.29 | 0.58>0.78 | 1.00|1.00 | -4.80|-4.19|-3.30 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-8.07,+0.89]|[+1.63,+16.18] |
| D6_TB4B_ASIA | F8_a10_n300 | stall 300s without new MFE after +10 | 450 | -4.84 [-9.70,+0.03] (6.95) | 200 | +8.84 [+1.23,+16.44] (10.86) | -0.44 (10.79) | -5,804|11,045 | +20.65|-25.48 | 377 (84%) | -1.39 | 0.58>0.83 | 0.90|1.00 | -6.02|-5.46|-4.58 | DEAD | mean_up,placebo<0.95,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-9.33,-0.09]|[+1.25,+16.56] |
| D6_TB4B_ASIA | F12_lad3_st600 | ladder 3 + stall 600 s after +20 | 450 | -3.45 [-7.72,+0.81] (6.09) | 200 | +8.81 [+1.90,+15.72] (9.87) | -0.95 (9.41) | -4,144|11,009 | +16.19|-19.64 | 324 (72%) | -0.94 | 0.58>0.69 | 1.00|1.00 | -4.53|-3.83|-3.27 | DEAD | mean_up,neighbours_agree(no grid),paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-7.64,+0.99]|[+1.65,+15.63] |
| D6_TB4B_ASIA | F8_a20_n120 | stall 120s without new MFE after +20 | 450 | -3.18 [-7.53,+1.16] (6.20) | 200 | +8.77 [+1.55,+16.00] (10.32) | -0.68 (9.58) | -3,821|10,967 | +17.28|-20.46 | 343 (76%) | -1.30 | 0.58>0.80 | 1.00|1.00 | -4.36|-3.75|-3.03 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-7.43,+1.06]|[+1.49,+16.16] |
| D6_TB4B_ASIA | F1_a20_t20 | fixed trail 20 pts after +20 | 450 | -3.84 [-8.05,+0.37] (6.02) | 200 | +8.76 [+2.11,+15.42] (9.51) | -1.58 (9.12) | -4,605|10,955 | +15.75|-19.59 | 307 (68%) | -0.38 | 0.58>0.74 | 1.00|1.00 | -4.86|-3.83|-3.84 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-7.96,+0.32]|[+1.99,+15.20] |
| D6_TB4B_ASIA | F9e_a20_w300_t0.4 | efficiency exit: ER(300s)<0.4 and >=3pt off high after +20 | 450 | -3.62 [-8.00,+0.75] (6.25) | 200 | +8.75 [+1.48,+16.03] (10.39) | -0.77 (9.57) | -4,349|10,943 | +17.53|-21.16 | 355 (79%) | -1.38 | 0.58>0.79 | 1.00|1.00 | -4.88|-4.21|-3.39 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-7.96,+0.65]|[+1.54,+16.13] |


### 6c. Pooled over the 11 intraday books: top 10 rules by IN-SAMPLE delta

| stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 11 BOOKS | F10_m40_r3_t4 | JADE min profit 40, 3 of 4, trail 4 | 18121 | -0.06 [-0.72,+0.59] (0.94) | 7747 | +0.03 [-0.94,+1.00] (1.38) | -0.09 (1.48) | -1,549|2,722 | +7.42|-7.48 | 7911 (44%) | -0.73 | 0.54>0.62 | 1.00|1.00 | -0.79|-0.38|+0.04 | DEAD | mean_up,paired_CI_excludes0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | F9e_a30_w120_t0.4 | efficiency exit: ER(120s)<0.4 and >=3pt off high after +30 | 18121 | -0.14 [-1.05,+0.77] (1.30) | 7747 | +0.45 [-0.97,+1.87] (2.03) | +0.03 (2.04) | -3,171|22,728 | +12.14|-12.28 | 11397 (63%) | -1.05 | 0.54>0.67 | 1.00|1.00 | -1.16|-0.59|+0.00 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | F9e_a30_w120_t0.3 | efficiency exit: ER(120s)<0.3 and >=3pt off high after +30 | 18121 | -0.14 [-1.05,+0.77] (1.30) | 7747 | +0.45 [-0.97,+1.86] (2.03) | +0.03 (2.04) | -3,426|22,530 | +12.14|-12.28 | 11392 (63%) | -1.05 | 0.54>0.67 | 1.00|1.00 | -1.16|-0.59|-0.00 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | F9e_a30_w300_t0.4 | efficiency exit: ER(300s)<0.4 and >=3pt off high after +30 | 18121 | -0.14 [-1.05,+0.76] (1.29) | 7747 | +0.41 [-1.00,+1.83] (2.02) | +0.03 (2.04) | -3,140|21,078 | +11.83|-11.98 | 11041 (61%) | -1.01 | 0.54>0.67 | 1.00|1.00 | -1.12|-0.58|-0.03 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | F9e_a30_w300_t0.3 | efficiency exit: ER(300s)<0.3 and >=3pt off high after +30 | 18121 | -0.15 [-1.05,+0.75] (1.29) | 7747 | +0.41 [-1.00,+1.82] (2.02) | +0.03 (2.04) | -3,228|20,982 | +11.83|-11.98 | 11041 (61%) | -1.01 | 0.54>0.67 | 1.00|1.00 | -1.12|-0.58|-0.03 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | F9e_a30_w300_t0.2 | efficiency exit: ER(300s)<0.2 and >=3pt off high after +30 | 18121 | -0.15 [-1.06,+0.75] (1.29) | 7747 | +0.40 [-1.01,+1.82] (2.02) | +0.03 (2.03) | -3,539|20,672 | +11.83|-11.99 | 11033 (61%) | -1.01 | 0.54>0.67 | 1.00|1.00 | -1.13|-0.59|-0.03 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | F9e_a30_w120_t0.2 | efficiency exit: ER(120s)<0.2 and >=3pt off high after +30 | 18121 | -0.16 [-1.08,+0.75] (1.30) | 7747 | +0.45 [-0.97,+1.87] (2.02) | +0.01 (2.04) | -4,279|22,741 | +12.13|-12.30 | 11355 (63%) | -1.05 | 0.54>0.67 | 1.00|1.00 | -1.18|-0.61|-0.02 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | F10_m40_r4_t4 | JADE min profit 40, 4 of 4, trail 4 | 18121 | -0.26 [-0.82,+0.31] (0.81) | 7747 | -0.14 [-0.99,+0.70] (1.21) | +0.05 (1.13) | -9,317|-4,945 | +5.46|-5.71 | 4582 (25%) | -0.42 | 0.54>0.58 | 1.00|1.00 | -0.63|-0.43|-0.19 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | F10_m40_r2_t4 | JADE min profit 40, 2 of 4, trail 4 | 18121 | -0.26 [-0.93,+0.41] (0.96) | 7747 | -0.01 [-1.00,+0.98] (1.42) | -0.28 (1.50) | -9,833|2,236 | +7.66|-7.92 | 8727 (48%) | -0.62 | 0.54>0.62 | 1.00|1.00 | -1.09|-0.47|-0.19 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | F10_m40_r4_t8 | JADE min profit 40, 4 of 4, trail 8 | 18121 | -0.26 [-0.83,+0.30] (0.81) | 7747 | -0.17 [-1.01,+0.68] (1.21) | +0.04 (1.13) | -9,725|-5,824 | +5.45|-5.72 | 4569 (25%) | -0.40 | 0.54>0.58 | 1.00|1.00 | -0.64|-0.44|-0.20 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |


### 6d. Pooled over the 11 intraday books: top 10 rules by HOLDOUT delta

| stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 11 BOOKS | F9e_a30_w120_t0.4 | efficiency exit: ER(120s)<0.4 and >=3pt off high after +30 | 18121 | -0.14 [-1.05,+0.77] (1.30) | 7747 | +0.45 [-0.97,+1.87] (2.03) | +0.03 (2.04) | -3,171|22,728 | +12.14|-12.28 | 11397 (63%) | -1.05 | 0.54>0.67 | 1.00|1.00 | -1.16|-0.59|+0.00 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | F9e_a30_w120_t0.2 | efficiency exit: ER(120s)<0.2 and >=3pt off high after +30 | 18121 | -0.16 [-1.08,+0.75] (1.30) | 7747 | +0.45 [-0.97,+1.87] (2.02) | +0.01 (2.04) | -4,279|22,741 | +12.13|-12.30 | 11355 (63%) | -1.05 | 0.54>0.67 | 1.00|1.00 | -1.18|-0.61|-0.02 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | F9e_a30_w120_t0.3 | efficiency exit: ER(120s)<0.3 and >=3pt off high after +30 | 18121 | -0.14 [-1.05,+0.77] (1.30) | 7747 | +0.45 [-0.97,+1.86] (2.03) | +0.03 (2.04) | -3,426|22,530 | +12.14|-12.28 | 11392 (63%) | -1.05 | 0.54>0.67 | 1.00|1.00 | -1.16|-0.59|-0.00 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | F9e_a30_w300_t0.4 | efficiency exit: ER(300s)<0.4 and >=3pt off high after +30 | 18121 | -0.14 [-1.05,+0.76] (1.29) | 7747 | +0.41 [-1.00,+1.83] (2.02) | +0.03 (2.04) | -3,140|21,078 | +11.83|-11.98 | 11041 (61%) | -1.01 | 0.54>0.67 | 1.00|1.00 | -1.12|-0.58|-0.03 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | F9e_a30_w300_t0.3 | efficiency exit: ER(300s)<0.3 and >=3pt off high after +30 | 18121 | -0.15 [-1.05,+0.75] (1.29) | 7747 | +0.41 [-1.00,+1.82] (2.02) | +0.03 (2.04) | -3,228|20,982 | +11.83|-11.98 | 11041 (61%) | -1.01 | 0.54>0.67 | 1.00|1.00 | -1.12|-0.58|-0.03 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | F9e_a30_w300_t0.2 | efficiency exit: ER(300s)<0.2 and >=3pt off high after +30 | 18121 | -0.15 [-1.06,+0.75] (1.29) | 7747 | +0.40 [-1.01,+1.82] (2.02) | +0.03 (2.03) | -3,539|20,672 | +11.83|-11.99 | 11033 (61%) | -1.01 | 0.54>0.67 | 1.00|1.00 | -1.13|-0.59|-0.03 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | F9e_a20_w120_t0.2 | efficiency exit: ER(120s)<0.2 and >=3pt off high after +20 | 18121 | -0.66 [-1.81,+0.49] (1.65) | 7747 | +0.31 [-1.45,+2.08] (2.52) | +0.17 (2.51) | -23,215|19,567 | +16.69|-17.35 | 13384 (74%) | -1.19 | 0.54>0.75 | 1.00|1.00 | -1.74|-1.19|-0.43 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | F9e_a20_w120_t0.4 | efficiency exit: ER(120s)<0.4 and >=3pt off high after +20 | 18121 | -0.62 [-1.77,+0.53] (1.64) | 7747 | +0.29 [-1.48,+2.06] (2.53) | +0.18 (2.51) | -21,540|18,569 | +16.72|-17.34 | 13408 (74%) | -1.19 | 0.54>0.75 | 1.00|1.00 | -1.70|-1.15|-0.41 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | F9e_a20_w120_t0.3 | efficiency exit: ER(120s)<0.3 and >=3pt off high after +20 | 18121 | -0.62 [-1.77,+0.53] (1.64) | 7747 | +0.29 [-1.48,+2.06] (2.53) | +0.19 (2.51) | -21,709|18,539 | +16.71|-17.33 | 13404 (74%) | -1.19 | 0.54>0.75 | 1.00|1.00 | -1.71|-1.15|-0.41 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | F9e_a20_w300_t0.4 | efficiency exit: ER(300s)<0.4 and >=3pt off high after +20 | 18121 | -0.59 [-1.72,+0.55] (1.62) | 7747 | +0.27 [-1.47,+2.02] (2.50) | +0.16 (2.50) | -20,226|18,447 | +16.18|-16.77 | 12994 (72%) | -1.14 | 0.54>0.73 | 1.00|1.00 | -1.62|-1.10|-0.41 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |


### 6e. How the cells died (count of cells failing each gate, all 3840 cells)

| gate | cells failing |
|---|---|
| RC_p>0.05 | 3840 |
| NOTC<=0 | 3839 |
| paired_CI_excludes0 | 3834 |
| mean_up | 3578 |
| 2x_cost<=0 | 3433 |
| holdout_sign_agrees | 2747 |
| SPAN2<=0 | 2363 |
| maxDD_not_worse | 1490 |
| placebo>=0.90 | 945 |
| neighbours_agree(no grid) | 560 |
| neighbours_agree | 380 |
| year_share>60% | 305 |
| n_PRE<100 | 192 |
| placebo<0.95 | 82 |


## 7. By ENTRY session (pooled over the six stack books) for the JADE control, the best-in-sample and the best-holdout pooled rule

**F10_m20_r3_t8** - JADE min profit 20, 3 of 4, trail 8

| win | key | n | delta | MDE | usd_wk |
|---|---|---|---|---|---|
| PRE | ASIA | 3832 | -0.89 | 3.03 | -5,546 |
| PRE | LONDON | 2627 | -0.80 | 3.38 | -3,773 |
| PRE | PRE | 396 | -1.17 | 7.86 | -1,404 |
| PRE | NY-AM | 1941 | -2.65 | 3.94 | -9,784 |
| PRE | NY-PM | 1400 | -1.88 | 3.42 | -4,140 |
| PRE | CLOSE | 9 | +0.00 | 0.00 | 0 |
| HOLD | ASIA | 1789 | -0.86 | 4.72 | -4,084 |
| HOLD | LONDON | 1051 | -0.14 | 5.33 | 1,820 |
| HOLD | PRE | 119 | +4.36 | 15.40 | 1,891 |
| HOLD | NY-AM | 865 | -2.06 | 4.98 | -7,070 |
| HOLD | NY-PM | 515 | +1.12 | 5.55 | 5,073 |
| X | ASIA | 1375 | -0.46 | 4.87 | -3,772 |
| X | LONDON | 914 | -2.90 | 5.85 | -8,270 |
| X | PRE | 208 | -2.26 | 11.68 | -1,645 |
| X | NY-AM | 1172 | -0.24 | 5.12 | 394 |
| X | NY-PM | 849 | +3.12 | 5.07 | 8,155 |

**F10_m40_r3_t4** - JADE min profit 40, 3 of 4, trail 4

| win | key | n | delta | MDE | usd_wk |
|---|---|---|---|---|---|
| PRE | ASIA | 3832 | +0.27 | 1.75 | 3,039 |
| PRE | LONDON | 2627 | -0.11 | 1.92 | -1,324 |
| PRE | PRE | 396 | -0.18 | 4.53 | -617 |
| PRE | NY-AM | 1941 | -1.31 | 2.22 | -5,197 |
| PRE | NY-PM | 1400 | -0.19 | 2.12 | -29 |
| PRE | CLOSE | 9 | +0.00 | 0.00 | 0 |
| HOLD | ASIA | 1789 | +0.23 | 2.71 | 2,218 |
| HOLD | LONDON | 1051 | +0.29 | 2.95 | 1,300 |
| HOLD | PRE | 119 | +0.54 | 6.04 | -65 |
| HOLD | NY-AM | 865 | -0.61 | 2.72 | -1,986 |
| HOLD | NY-PM | 515 | +0.65 | 3.03 | 3,624 |
| X | ASIA | 1375 | -0.72 | 2.92 | -4,360 |
| X | LONDON | 914 | -1.11 | 3.36 | -3,091 |
| X | PRE | 208 | -1.91 | 7.12 | -1,190 |
| X | NY-AM | 1172 | -0.12 | 3.05 | 37 |
| X | NY-PM | 849 | +1.78 | 2.90 | 4,767 |

**F9e_a30_w120_t0.4** - efficiency exit: ER(120s)<0.4 and >=3pt off high after +30

| win | key | n | delta | MDE | usd_wk |
|---|---|---|---|---|---|
| PRE | ASIA | 3832 | +0.42 | 2.40 | 5,601 |
| PRE | LONDON | 2627 | +0.24 | 2.75 | 960 |
| PRE | PRE | 396 | -0.67 | 6.61 | -734 |
| PRE | NY-AM | 1941 | -1.21 | 3.08 | -4,533 |
| PRE | NY-PM | 1400 | -0.59 | 2.91 | -1,019 |
| PRE | CLOSE | 9 | +0.00 | 0.00 | 0 |
| HOLD | ASIA | 1789 | +0.79 | 4.07 | 7,752 |
| HOLD | LONDON | 1051 | +0.35 | 4.33 | 2,018 |
| HOLD | PRE | 119 | +2.22 | 12.82 | 1,056 |
| HOLD | NY-AM | 865 | -0.93 | 3.82 | -2,836 |
| HOLD | NY-PM | 515 | +1.92 | 4.56 | 6,676 |
| X | ASIA | 1375 | +0.40 | 4.00 | 210 |
| X | LONDON | 914 | -1.15 | 4.76 | -3,207 |
| X | PRE | 208 | -2.51 | 10.36 | -1,536 |
| X | NY-AM | 1172 | -0.71 | 3.99 | -2,354 |
| X | NY-PM | 849 | +2.24 | 3.98 | 5,537 |


## 8. By calendar year (pooled over the six stack books; 2023 = X span only from April, 2024 mixes X and PRE, 2026 = January to 6 February)

**F10_m20_r3_t8**

| win | key | n | delta | MDE | usd_wk |
|---|---|---|---|---|---|
| PRE | 2024 | 6040 | -1.54 | 2.30 | -16,030 |
| PRE | 2025 | 4165 | -1.07 | 2.53 | -8,617 |
| HOLD | 2025 | 3474 | -0.81 | 2.93 | -8,040 |
| HOLD | 2026 | 869 | +0.50 | 6.15 | 5,671 |
| X | 2023 | 3988 | +0.24 | 2.74 | 3,419 |
| X | 2024 | 533 | -4.42 | 7.12 | -8,558 |

**F10_m40_r3_t4**

| win | key | n | delta | MDE | usd_wk |
|---|---|---|---|---|---|
| PRE | 2024 | 6040 | -0.61 | 1.30 | -6,501 |
| PRE | 2025 | 4165 | +0.37 | 1.51 | 2,373 |
| HOLD | 2025 | 3474 | -0.21 | 1.54 | -2,095 |
| HOLD | 2026 | 869 | +1.52 | 4.07 | 7,186 |
| X | 2023 | 3988 | +0.03 | 1.64 | -338 |
| X | 2024 | 533 | -2.12 | 3.70 | -3,499 |

**F9e_a30_w120_t0.4**

| win | key | n | delta | MDE | usd_wk |
|---|---|---|---|---|---|
| PRE | 2024 | 6040 | -0.57 | 1.80 | -3,852 |
| PRE | 2025 | 4165 | +0.54 | 2.11 | 4,126 |
| HOLD | 2025 | 3474 | +0.11 | 2.39 | 4,117 |
| HOLD | 2026 | 869 | +2.12 | 5.54 | 10,550 |
| X | 2023 | 3988 | +0.43 | 2.21 | 4,439 |
| X | 2024 | 533 | -3.17 | 5.60 | -5,790 |


Full per-book, per-session, per-year tables for all 192 rules: splits_B.parquet (columns stream, rule, win, split, key, n, mean, mde, usd_wk).


### 6f. One line per book: best rule IN-SAMPLE and best rule HOLDOUT (one row per stream, duplicates removed) with the gates that killed it

| stream | role | rule | PRE | HOLD | X | verdict | failed |
|---|---|---|---|---|---|---|---|
| B3_NQ | best PRE | F7_t60_x10 | +8.83 (59.31) | -59.83 (109.51) | -30.97 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05,n_PRE<100 |
| B3_NQ | best HOLD | F7_t20_x10 | -10.06 (59.12) | -26.40 (88.12) | -33.52 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05,n_PRE<100 |
| D6_HM_t75_s90_NYAM | best PRE | F6_tf5_a30 | -1.49 (5.64) | -1.83 (7.82) | -2.85 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_HM_t75_s90_NYAM | best HOLD | F7_t60_x20 | -3.15 (5.17) | +1.56 (7.55) | -1.60 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_KB_t60_s75_ASIA | best PRE | F7_t60_x10 | -1.74 (5.36) | -3.90 (7.46) | -0.02 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_KB_t60_s75_ASIA | best HOLD | F6_tf5_a10 | -4.74 (5.37) | +1.06 (8.26) | -2.12 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_PB7_PB5_ASIA | best PRE | F10_m30_r4_t16 | -2.28 (5.41) | +0.13 (6.72) | -1.28 | DEAD | mean_up,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_PB7_PB5_ASIA | best HOLD | F10_m20_r4_t12 | -3.11 (6.23) | +1.62 (7.42) | +0.48 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| D6_TB4B_ASIA | best PRE | F10_m40_r4_t4 | +0.14 (3.78) | +2.11 (5.88) | -1.10 | DEAD | neighbours_agree,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_TB4B_ASIA | best HOLD | F8_a20_n60 | -3.38 (6.31) | +9.16 (10.46) | -0.81 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_TB4W_03_ASIA | best PRE | F10_m40_r4_t4 | -0.18 (2.49) | +3.13 (4.07) | -0.02 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_TB4W_03_ASIA | best HOLD | F10_m40_r4_t4 | -0.18 (2.49) | +3.13 (4.07) | -0.02 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| DN | best PRE | F9e_a30_w300_t0.4 | +0.58 (2.71) | +0.99 (4.09) | +0.81 | DEAD | paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| DN | best HOLD | F10_m30_r3_t4 | -0.18 (2.68) | +1.23 (4.08) | +0.71 | DEAD | mean_up,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| EM | best PRE | F9e_a20_w300_t0.4 | +1.24 (4.38) | +0.54 (7.04) | -1.28 | DEAD | paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| EM | best HOLD | F9e_a30_w300_t0.4 | +0.45 (3.83) | +2.08 (6.09) | +0.09 | DEAD | neighbours_agree,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| HM | best PRE | F9e_a30_w300_t0.3 | +1.26 (2.87) | -0.62 (3.98) | -1.08 | DEAD | holdout_sign_agrees,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| HM | best HOLD | F7_t60_x20 | -1.02 (2.80) | +2.12 (4.14) | -0.40 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| KB | best PRE | F10_m40_r3_t4 | -0.30 (2.06) | -0.54 (3.04) | -0.22 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| KB | best HOLD | F10_m40_r4_t4 | -0.45 (1.80) | -0.26 (2.68) | -0.71 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| MA | best PRE | F10_m40_r4_t4 | -0.89 (2.39) | -2.09 (3.78) | +0.18 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| MA | best HOLD | F7_t60_x10 | -1.24 (3.12) | -0.36 (4.49) | -0.40 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| MV | best PRE | F10_m40_r3_t4 | +0.14 (1.99) | -0.06 (2.94) | +0.95 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| MV | best HOLD | F9e_a20_w120_t0.2 | -1.37 (2.89) | +1.65 (4.53) | +1.33 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| O6_LV_RN_BH | best PRE | F7_t20_x20 | -0.02 (7.46) | +1.71 (7.22) | -4.95 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| O6_LV_RN_BH | best HOLD | F7_t20_x30 | -1.20 (7.93) | +2.00 (8.11) | -2.91 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| O6_OR15m_stp_le1 | best PRE | F7_t60_x10 | -1.19 (4.98) | +1.89 (6.55) | +0.28 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| O6_OR15m_stp_le1 | best HOLD | F7_t60_x10 | -1.19 (4.98) | +1.89 (6.55) | +0.28 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| O6_OR30m_stp_ge0.5 | best PRE | F7_t60_x10 | -0.52 (3.46) | -1.37 (4.28) | -0.90 | DEAD | mean_up,holdout_sign_agrees,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| O6_OR30m_stp_ge0.5 | best HOLD | F8_a10_n60 | -7.96 (8.35) | +2.54 (13.08) | +0.69 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| PB | best PRE | F7_t60_x30 | +1.46 (2.21) | -2.22 (3.33) | -2.76 | DEAD | holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| PB | best HOLD | F9e_a30_w300_t0.3 | +0.50 (2.40) | +0.58 (3.71) | -1.19 | DEAD | paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| PE | best PRE | F7_t60_x10 | -0.01 (2.48) | -2.09 (3.73) | -0.83 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| PE | best HOLD | F9e_a30_w300_t0.4 | -1.23 (2.61) | +0.07 (4.07) | -0.58 | DEAD | mean_up,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| SM | best PRE | F10_m40_r3_t4 | +0.74 (3.39) | +3.09 (5.73) | -0.01 | DEAD | neighbours_agree,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| SM | best HOLD | F9e_a20_w120_t0.2 | -1.62 (4.73) | +3.51 (8.14) | +1.14 | DEAD | mean_up,paired_CI_excludes0,2x_cost<=0,year_share>60%,NOTC<=0,RC_p>0.05 |
| ST | best PRE | F9e_a30_w120_t0.4 | -0.14 (2.89) | +1.79 (4.31) | -0.69 | DEAD | mean_up,paired_CI_excludes0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| ST | best HOLD | F9e_a20_w300_t0.2 | -0.99 (3.17) | +1.84 (4.77) | -0.73 | DEAD | mean_up,paired_CI_excludes0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| WT | best PRE | F9e_a30_w120_t0.4 | +0.67 (0.71) | +1.62 (1.19) | +0.45 | DEAD | year_share>60%,NOTC<=0,RC_p>0.05 |
| WT | best HOLD | F9e_a20_w120_t0.2 | +0.29 (1.30) | +1.69 (2.01) | +0.63 | DEAD | paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |


## 6g. Price-basis sensitivity (pooled over the 11 intraday books, pts/trade): the MEASURED target correction flatters every early exit

N = no target correction (limit target filled at the level), M = MEASURED primary, MW = market exits at the live-measured 0.995 pt, C = CONSERVATIVE label. The P9 target correction (about -0.9 pt in 2023-24, -3.7 to -3.8 pts in 2025-26) is applied to every bracket target exit and to nothing else, so a rule that exits before the target avoids it; on N the same rules lose.

| rule | N_PRE | M_PRE | MW_PRE | C_PRE | N_HOLD | M_HOLD | MW_HOLD | C_HOLD | cost_per_added_exit_M |
|---|---|---|---|---|---|---|---|---|---|
| F10_m20_r3_t8 | -2.24 | -1.25 | -1.51 | -1.13 | -2.38 | -0.64 | -0.90 | -0.55 | -1.10 |
| F10_m40_r3_t4 | -0.79 | -0.06 | -0.38 | +0.04 | -1.28 | +0.03 | -0.29 | +0.11 | -1.67 |
| F9e_a30_w120_t0.4 | -1.16 | -0.14 | -0.59 | +0.00 | -1.35 | +0.45 | -0.00 | +0.70 | -1.67 |
| F1_a20_t20 | -2.58 | -1.75 | -1.73 | -1.76 | -2.51 | -1.08 | -1.06 | -1.09 | -0.43 |
| F2_a20_p33 | -2.52 | -1.49 | -1.47 | -1.50 | -2.82 | -1.02 | -1.00 | -1.03 | -0.48 |
| F3_tf5_m1.5_a20 | -2.10 | -1.50 | -1.48 | -1.51 | -2.39 | -1.29 | -1.26 | -1.29 | -0.33 |
| F7_t30_x10 | -1.14 | -0.70 | -1.07 | -0.57 | -1.70 | -0.85 | -1.22 | -0.74 | -1.32 |
| F8_a20_n300 | -1.67 | -0.87 | -1.29 | -0.76 | -1.83 | -0.40 | -0.82 | -0.27 | -1.53 |
| F11_x30_t20 | -1.38 | -1.20 | -1.18 | -1.21 | -1.50 | -1.19 | -1.17 | -1.20 | -0.06 |


Cost of the added exits: a rule market exit costs 0.25 pt (M) / 0.995 pt (MW) / 0.5 pt plus a 3-s delay (C); a trailing or tightened stop exit costs the measured stop walk (0.85 / 1.13 / 1.74 / 1.71 pts for 2023..2026 at 10 lots, +0.5 on C). The last column is the change in friction per ADDED exit relative to the bracket exit it replaces (negative = the added exit is cheaper than the bracket target/stop on the MEASURED basis, which is the target-correction artefact above).


### 6h. Supplementary TIMING-MATCHED placebo (added after the prereg freeze; no verdict depends on it): armed trades exit at market at the rule's own exit rate AND the rule's own arm-to-exit delay distribution; 30 draws; rank = share of draws below the rule (0.5 = no better than random timing)

| stream | rule | PRE | HOLD | X |
|---|---|---|---|---|
| B3_NQ | F10_m20_r3_t8 | -20.17 vs plc -18.20 (rank 0.20) | -61.09 vs plc -62.89 (rank 0.73) | -38.51 vs plc -36.91 (rank 0.07) |
| D6_HM_t75_s90_NYAM | F10_m20_r3_t8 | -7.02 vs plc -6.37 (rank 0.17) | -2.55 vs plc -3.26 (rank 0.80) | -6.83 vs plc -6.10 (rank 0.27) |
| D6_KB_t60_s75_ASIA | F10_m20_r3_t8 | -5.42 vs plc -4.43 (rank 0.03) | -1.06 vs plc +0.08 (rank 0.07) | -0.11 vs plc +0.15 (rank 0.20) |
| D6_PB7_PB5_ASIA | F10_m20_r3_t8 | -5.57 vs plc -4.94 (rank 0.07) | -3.43 vs plc -2.21 (rank 0.03) | -1.40 vs plc -1.01 (rank 0.27) |
| D6_TB4B_ASIA | F10_m20_r3_t8 | -3.91 vs plc -3.51 (rank 0.23) | +8.21 vs plc +8.40 (rank 0.47) | -1.21 vs plc -0.76 (rank 0.27) |
| D6_TB4W_03_ASIA | F10_m20_r3_t8 | -3.55 vs plc -2.95 (rank 0.10) | +0.17 vs plc +2.06 (rank 0.00) | +2.46 vs plc +3.09 (rank 0.20) |
| DN | F10_m20_r3_t8 | -0.92 vs plc -0.38 (rank 0.03) | +0.26 vs plc +0.66 (rank 0.10) | +0.84 vs plc +1.33 (rank 0.20) |
| EM | F10_m20_r3_t8 | -0.05 vs plc +0.76 (rank 0.00) | -0.52 vs plc +0.30 (rank 0.17) | -2.24 vs plc -1.36 (rank 0.00) |
| HM | F10_m20_r3_t8 | -0.39 vs plc +0.20 (rank 0.03) | +0.19 vs plc +0.93 (rank 0.07) | +0.17 vs plc +0.52 (rank 0.17) |
| KB | F10_m20_r3_t8 | -2.67 vs plc -2.01 (rank 0.00) | -3.63 vs plc -2.45 (rank 0.00) | +0.02 vs plc +0.52 (rank 0.17) |
| MA | F10_m20_r3_t8 | -2.27 vs plc -1.60 (rank 0.03) | -3.82 vs plc -2.03 (rank 0.00) | -1.05 vs plc -0.15 (rank 0.07) |
| MV | F10_m20_r3_t8 | -2.13 vs plc -1.45 (rank 0.03) | +0.68 vs plc +1.01 (rank 0.33) | +0.83 vs plc +0.85 (rank 0.47) |
| O6_LV_RN_BH | F10_m20_r3_t8 | -9.08 vs plc -7.21 (rank 0.07) | -2.06 vs plc -1.68 (rank 0.50) | +1.86 vs plc +1.71 (rank 0.50) |
| O6_OR15m_stp_le1 | F10_m20_r3_t8 | -7.14 vs plc -5.51 (rank 0.10) | -5.79 vs plc -4.07 (rank 0.13) | +2.94 vs plc +3.34 (rank 0.40) |
| O6_OR30m_stp_ge0.5 | F10_m20_r3_t8 | -5.07 vs plc -4.75 (rank 0.40) | -0.47 vs plc -1.23 (rank 0.80) | -3.21 vs plc -2.01 (rank 0.00) |
| PB | F10_m20_r3_t8 | -0.27 vs plc +0.31 (rank 0.00) | -1.51 vs plc -0.77 (rank 0.00) | -1.52 vs plc -1.48 (rank 0.50) |
| PE | F10_m20_r3_t8 | -1.95 vs plc -1.33 (rank 0.00) | -1.44 vs plc -0.58 (rank 0.00) | -0.43 vs plc -0.25 (rank 0.27) |
| SM | F10_m20_r3_t8 | -1.90 vs plc -1.38 (rank 0.17) | +1.75 vs plc +2.83 (rank 0.13) | -0.09 vs plc +0.68 (rank 0.07) |
| ST | F10_m20_r3_t8 | -1.45 vs plc -1.03 (rank 0.10) | +0.51 vs plc +1.12 (rank 0.13) | -1.52 vs plc -1.23 (rank 0.37) |
| WT | F10_m20_r3_t8 | -0.33 vs plc +0.15 (rank 0.00) | +0.35 vs plc +0.90 (rank 0.07) | -0.00 vs plc +0.27 (rank 0.27) |
| PB | F7_t60_x30 | +1.46 vs plc +0.67 (rank 1.00) | -2.22 vs plc -1.24 (rank 0.13) | -2.76 vs plc -1.35 (rank 0.00) |
| HM | F9e_a30_w300_t0.3 | +1.26 vs plc +0.96 (rank 0.93) | -0.62 vs plc -0.70 (rank 0.63) | -1.08 vs plc -1.11 (rank 0.47) |
| HM | F9e_a30_w300_t0.4 | +1.26 vs plc +0.98 (rank 0.93) | -0.62 vs plc -0.69 (rank 0.53) | -1.08 vs plc -1.02 (rank 0.40) |
| HM | F9e_a30_w300_t0.2 | +1.25 vs plc +1.00 (rank 0.87) | -0.63 vs plc -0.69 (rank 0.57) | -1.04 vs plc -1.02 (rank 0.40) |
| EM | F9e_a20_w300_t0.4 | +1.24 vs plc +0.50 (rank 1.00) | +0.54 vs plc +1.00 (rank 0.13) | -1.28 vs plc -1.09 (rank 0.33) |
| EM | F9e_a20_w300_t0.3 | +1.24 vs plc +0.57 (rank 1.00) | +0.54 vs plc +0.98 (rank 0.27) | -1.28 vs plc -1.15 (rank 0.50) |
| EM | F12_eff_st | +1.24 vs plc +0.57 (rank 0.97) | +0.54 vs plc +1.01 (rank 0.20) | -1.28 vs plc -1.21 (rank 0.43) |
| EM | F9e_a20_w300_t0.2 | +1.23 vs plc +0.49 (rank 0.97) | +0.56 vs plc +0.97 (rank 0.20) | -1.27 vs plc -1.07 (rank 0.33) |
| PB | F7_t60_x10 | +1.20 vs plc +0.41 (rank 0.97) | -1.94 vs plc -0.89 (rank 0.00) | -2.28 vs plc -0.70 (rank 0.07) |
| HM | F9e_a30_w120_t0.4 | +1.08 vs plc +1.06 (rank 0.67) | -0.64 vs plc -0.71 (rank 0.60) | -1.04 vs plc -1.12 (rank 0.67) |
| D6_TB4B_ASIA | F8_a20_n60 | -3.38 vs plc -3.80 (rank 0.90) | +9.16 vs plc +8.74 (rank 0.70) | -0.81 vs plc -0.59 (rank 0.33) |
| D6_TB4B_ASIA | F10_m20_r3_t4 | -3.30 vs plc -3.71 (rank 0.80) | +9.04 vs plc +8.52 (rank 0.87) | -0.42 vs plc -0.68 (rank 0.70) |
| D6_TB4B_ASIA | F12_gb50_st300 | -3.26 vs plc -3.52 (rank 0.73) | +9.03 vs plc +8.31 (rank 0.77) | -0.69 vs plc -0.68 (rank 0.47) |
| D6_TB4B_ASIA | F8_a20_n300 | -3.21 vs plc -3.02 (rank 0.37) | +9.00 vs plc +7.67 (rank 0.90) | -0.33 vs plc -0.72 (rank 0.70) |
| D6_TB4B_ASIA | F9v_a20_w120_p6 | -3.63 vs plc -3.10 (rank 0.17) | +8.97 vs plc +8.34 (rank 0.70) | -0.13 vs plc -0.82 (rank 0.77) |
| D6_TB4B_ASIA | F8_a10_n300 | -4.84 vs plc -4.73 (rank 0.37) | +8.84 vs plc +7.83 (rank 0.90) | -0.44 vs plc -0.56 (rank 0.50) |
| D6_TB4B_ASIA | F12_lad3_st600 | -3.45 vs plc -3.29 (rank 0.40) | +8.81 vs plc +8.24 (rank 0.70) | -0.95 vs plc -0.30 (rank 0.23) |
| D6_TB4B_ASIA | F8_a20_n120 | -3.18 vs plc -3.33 (rank 0.67) | +8.77 vs plc +8.31 (rank 0.73) | -0.68 vs plc -0.76 (rank 0.50) |
| D6_TB4B_ASIA | F1_a20_t20 | -3.84 vs plc -2.50 (rank 0.07) | +8.76 vs plc +6.52 (rank 1.00) | -1.58 vs plc -0.60 (rank 0.20) |
| D6_TB4B_ASIA | F9e_a20_w300_t0.4 | -3.62 vs plc -3.66 (rank 0.50) | +8.75 vs plc +8.88 (rank 0.33) | -0.77 vs plc -0.69 (rank 0.37) |


### 6i. Live JADE delta by book and ENTRY session, pts/trade (MDE; n), whole sample 2023-04..2026-02-06

| stream | ASIA | LONDON | PRE | NY-AM | NY-PM | CLOSE |
|---|---|---|---|---|---|---|
| B3_NQ | n<5 | n<5 | n<5 | n<5 | n<5 | -35.08 (45.6; n 180) |
| D6_HM_t75_s90_NYAM | n<5 | n<5 | n<5 | -5.85 (5.9; n 780) | n<5 | n<5 |
| D6_KB_t60_s75_ASIA | -3.30 (4.0; n 1268) | n<5 | n<5 | n<5 | n<5 | n<5 |
| D6_PB7_PB5_ASIA | -4.10 (5.1; n 671) | n<5 | n<5 | n<5 | n<5 | n<5 |
| D6_TB4B_ASIA | -0.41 (4.8; n 843) | n<5 | n<5 | n<5 | n<5 | n<5 |
| D6_TB4W_03_ASIA | -1.57 (3.4; n 1419) | n<5 | n<5 | n<5 | n<5 | n<5 |
| DN | -1.83 (4.8; n 833) | -0.42 (5.3; n 682) | -1.11 (9.5; n 186) | +1.07 (4.1; n 980) | +0.38 (5.0; n 540) | -1.33 (14.8; n 51) |
| EM | +0.80 (6.0; n 531) | -0.63 (6.3; n 413) | -2.81 (13.1; n 89) | -2.96 (6.8; n 356) | +0.05 (6.7; n 264) | -8.42 (17.0; n 7) |
| HM | -0.68 (4.0; n 1117) | +0.18 (5.1; n 680) | +1.22 (13.5; n 95) | -1.42 (5.1; n 564) | +2.10 (5.3; n 462) | +0.00 (0.0; n 6) |
| KB | -2.10 (3.7; n 1274) | -2.39 (4.9; n 712) | +0.02 (11.7; n 123) | -2.45 (4.4; n 819) | -2.56 (4.9; n 509) | +0.00 (0.0; n 7) |
| MA | -2.13 (5.1; n 681) | -3.37 (6.2; n 441) | +5.48 (13.3; n 99) | -3.34 (6.3; n 406) | -2.50 (7.1; n 279) | n<5 |
| MV | -0.89 (3.9; n 1144) | -1.93 (4.7; n 763) | +3.45 (8.1; n 252) | -0.76 (4.1; n 958) | -1.51 (5.0; n 510) | n<5 |
| O6_LV_RN_BH | n<5 | n<5 | n<5 | -4.19 (7.3; n 293) | n<5 | n<5 |
| O6_OR15m_stp_le1 | n<5 | n<5 | n<5 | -3.80 (6.7; n 361) | n<5 | n<5 |
| O6_OR30m_stp_ge0.5 | n<5 | n<5 | n<5 | -3.56 (5.3; n 594) | n<5 | n<5 |
| PB | -0.34 (4.0; n 1139) | -1.98 (4.7; n 828) | -0.66 (9.1; n 225) | -2.03 (4.0; n 1043) | +1.23 (4.1; n 804) | -0.47 (28.9; n 10) |
| PE | -0.28 (3.8; n 1193) | -1.80 (4.7; n 721) | +1.49 (10.7; n 138) | -3.46 (4.8; n 689) | -1.91 (4.6; n 507) | n<5 |
| SM | -3.07 (6.0; n 470) | +0.65 (6.3; n 470) | -1.27 (17.6; n 64) | -1.13 (8.3; n 259) | +2.70 (8.2; n 194) | n<5 |
| ST | -0.47 (4.0; n 1198) | -1.27 (5.2; n 695) | -5.75 (10.0; n 146) | -1.12 (4.6; n 794) | -0.19 (5.4; n 401) | n<5 |
| WT | +0.09 (1.6; n 1744) | -1.09 (1.7; n 1314) | +1.14 (5.0; n 157) | -0.98 (2.1; n 853) | +2.10 (2.5; n 691) | n<5 |


### 6j. Live JADE delta by book and calendar year, pts/trade (MDE; n); 2023 = Apr-Dec, 2026 = Jan to 6 Feb

| stream | 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|
| B3_NQ | -34.98 (54.1; n 57) | +10.76 (81.8; n 67) | -93.60 (93.9; n 47) | -71.36 (297.5; n 9) |
| D6_HM_t75_s90_NYAM | -8.42 (13.9; n 138) | -7.77 (10.2; n 275) | -3.38 (9.1; n 327) | -4.04 (24.9; n 40) |
| D6_KB_t60_s75_ASIA | -0.18 (10.2; n 217) | -5.24 (6.6; n 397) | -3.16 (6.0; n 580) | -3.13 (17.6; n 74) |
| D6_PB7_PB5_ASIA | +0.22 (13.2; n 116) | -5.15 (9.2; n 218) | -6.36 (7.4; n 286) | +3.18 (17.9; n 51) |
| D6_TB4B_ASIA | +0.40 (10.5; n 170) | -5.06 (8.0; n 274) | +2.37 (7.4; n 363) | +3.10 (24.7; n 36) |
| D6_TB4W_03_ASIA | +2.48 (9.6; n 220) | -2.98 (6.5; n 438) | -1.97 (4.7; n 672) | -0.83 (10.8; n 91) |
| DN | +1.32 (5.2; n 642) | -0.58 (4.0; n 1097) | -0.41 (3.4; n 1387) | -3.20 (11.9; n 146) |
| EM | -1.62 (6.4; n 374) | -2.28 (5.2; n 583) | +1.44 (5.2; n 637) | -2.51 (16.3; n 66) |
| HM | +1.19 (5.3; n 581) | -0.64 (4.0; n 1018) | -0.99 (3.6; n 1206) | +6.67 (12.8; n 119) |
| KB | +0.23 (4.7; n 733) | -3.11 (3.7; n 1178) | -2.38 (3.3; n 1378) | -5.84 (9.8; n 155) |
| MA | -0.99 (6.3; n 410) | -3.49 (4.8; n 666) | -1.69 (4.8; n 751) | -5.67 (16.2; n 79) |
| MV | +1.22 (4.9; n 658) | -3.61 (3.6; n 1282) | +0.27 (3.3; n 1511) | +1.77 (9.5; n 176) |
| O6_LV_RN_BH | +4.88 (16.3; n 73) | -10.98 (11.4; n 96) | -3.78 (12.3; n 111) | -8.38 (20.4; n 13) |
| O6_OR15m_stp_le1 | +2.27 (12.3; n 102) | -5.27 (12.1; n 121) | -5.59 (11.5; n 127) | -23.28 (17.7; n 11) |
| O6_OR30m_stp_ge0.5 | -1.37 (10.8; n 152) | -7.16 (8.9; n 213) | -2.58 (8.7; n 206) | +6.45 (29.6; n 23) |
| PB | -0.62 (4.6; n 725) | -0.01 (3.6; n 1356) | -1.50 (3.1; n 1773) | -1.01 (9.4; n 195) |
| PE | +0.45 (4.8; n 694) | -3.00 (3.8; n 1115) | -1.43 (3.4; n 1292) | +0.74 (11.0; n 147) |
| SM | +0.42 (7.0; n 344) | -2.30 (5.6; n 535) | -0.25 (5.8; n 522) | +4.04 (19.7; n 56) |
| ST | -1.24 (5.0; n 662) | -1.39 (4.1; n 1091) | -0.78 (3.5; n 1341) | +0.93 (11.4; n 140) |
| WT | +0.48 (2.2; n 974) | -0.76 (1.6; n 1636) | +0.11 (1.4; n 1900) | +0.33 (3.6; n 252) |

## 9. Stack level: one rule applied to every stack book at once (ST HM WT KB SM PE), weekly series

Rules shown: the live JADE control, the best rule by IN-SAMPLE pooled $/wk (F9e_a30_w300_t0.3: efficiency exit: ER(300s)<0.3 and >=3pt off high after +30) and the best by HOLDOUT pooled $/wk (F9e_a20_w120_t0.2: efficiency exit: ER(120s)<0.2 and >=3pt off high after +20; selected on the holdout, labelled, not a candidate). Series = trade P&L at the stack lots on the MEASURED basis, bucketed by the label week of the EXIT. "hold-to-bracket stack" has no TH loss rule and no locks (this sim); "stack as it is" is the actual stack trade table P&L (TH cuts and lock engine, dv2a stack_trades); "overlay" = actual stack + (rule - hold) weekly delta. Locks (-2R/+5R, give-back arm, week floor) are NOT re-run on the rule streams: labelled.

| win | series | weeks | mean | sd | maxdd | worst | worst20 | d_mean | d_sd | d_maxdd | d_worst20 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | stack as it is (actual, TH+locks) | 75 | 46,332 | 133,291 | 409,229 | -306,664 | -2,333,434 |  |  |  |  |
| PRE | stack hold-to-bracket (this sim, no TH, no locks) | 75 | 24,519 | 136,379 | 529,072 | -334,490 | -2,748,994 |  |  |  |  |
| HOLD | stack as it is (actual, TH+locks) | 32 | 53,670 | 153,219 | 578,442 | -318,557 | -742,938 |  |  |  |  |
| HOLD | stack hold-to-bracket (this sim, no TH, no locks) | 32 | 7,993 | 155,374 | 657,134 | -351,290 | -1,677,723 |  |  |  |  |
| X | stack as it is (actual, TH+locks) | 44 | 19,608 | 113,430 | 542,017 | -157,300 | -1,722,161 |  |  |  |  |
| X | stack hold-to-bracket (this sim, no TH, no locks) | 44 | 13,711 | 117,832 | 591,176 | -169,370 | -1,934,792 |  |  |  |  |
| PRE | stack + F10_m20_r3_t8 | 75 | -2,053 | 69,702 | 422,838 | -165,362 | -1,780,987 | -26,572 | -66,677 | -106,234 | 968,007 |
| PRE | actual stack + (F10_m20_r3_t8 - hold) overlay | 75 | 19,760 | 66,286 | 238,981 | -140,707 | -1,277,300 | -26,572 | -67,005 | -170,248 | 1,056,135 |
| HOLD | stack + F10_m20_r3_t8 | 32 | 5,917 | 74,906 | 279,578 | -154,981 | -791,745 | -2,076 | -80,468 | -377,556 | 885,978 |
| HOLD | actual stack + (F10_m20_r3_t8 - hold) overlay | 32 | 51,594 | 76,840 | 200,886 | -118,679 | 62,980 | -2,076 | -76,379 | -377,556 | 805,917 |
| X | stack + F10_m20_r3_t8 | 44 | 10,567 | 76,708 | 447,308 | -184,313 | -1,128,931 | -3,145 | -41,124 | -143,868 | 805,861 |
| X | actual stack + (F10_m20_r3_t8 - hold) overlay | 44 | 16,464 | 74,780 | 356,089 | -163,769 | -903,852 | -3,145 | -38,650 | -185,928 | 818,309 |
| PRE | stack + F9e_a30_w300_t0.3 | 75 | 23,966 | 90,292 | 356,527 | -206,273 | -1,745,728 | -553 | -46,088 | -172,546 | 1,003,266 |
| PRE | actual stack + (F9e_a30_w300_t0.3 - hold) overlay | 75 | 45,779 | 89,060 | 210,729 | -178,446 | -1,314,939 | -553 | -44,231 | -198,500 | 1,018,496 |
| HOLD | stack + F9e_a30_w300_t0.3 | 32 | 21,677 | 103,391 | 428,370 | -228,765 | -822,746 | 13,684 | -51,983 | -228,764 | 854,977 |
| HOLD | actual stack + (F9e_a30_w300_t0.3 - hold) overlay | 32 | 67,354 | 105,720 | 349,678 | -196,033 | 78,627 | 13,684 | -47,499 | -228,764 | 821,565 |
| X | stack + F9e_a30_w300_t0.3 | 44 | 13,253 | 89,966 | 331,887 | -164,245 | -1,302,654 | -458 | -27,865 | -259,289 | 632,138 |
| X | actual stack + (F9e_a30_w300_t0.3 - hold) overlay | 44 | 19,150 | 89,781 | 264,234 | -158,328 | -1,125,187 | -458 | -23,650 | -277,783 | 596,974 |
| PRE | stack + F9e_a20_w120_t0.2 | 75 | 8,597 | 66,124 | 306,939 | -148,910 | -1,531,234 | -15,922 | -70,256 | -222,133 | 1,217,760 |
| PRE | actual stack + (F9e_a20_w120_t0.2 - hold) overlay | 75 | 30,410 | 63,543 | 170,883 | -117,885 | -1,071,983 | -15,922 | -69,748 | -238,346 | 1,261,452 |
| HOLD | stack + F9e_a20_w120_t0.2 | 32 | 28,934 | 76,650 | 220,994 | -124,969 | -392,563 | 20,940 | -78,725 | -436,140 | 1,285,160 |
| HOLD | actual stack + (F9e_a20_w120_t0.2 - hold) overlay | 32 | 74,611 | 79,466 | 142,302 | -89,844 | 496,664 | 20,940 | -73,752 | -436,140 | 1,239,602 |
| X | stack + F9e_a20_w120_t0.2 | 44 | 19,666 | 73,470 | 369,393 | -172,188 | -879,781 | 5,955 | -44,361 | -221,783 | 1,055,011 |
| X | actual stack + (F9e_a20_w120_t0.2 - hold) overlay | 44 | 25,563 | 72,228 | 295,889 | -151,645 | -709,167 | 5,955 | -41,202 | -246,127 | 1,012,994 |


### 9b. Does the stack-level variance reduction beat random exits at the same exit rate? (30 placebo draws per rule, all six books, weekly series, MEASURED basis)

| win | rule | sd | placebo_sd | mean | placebo_mean | maxdd | placebo_maxdd | worst20 | placebo_worst20 |
|---|---|---|---|---|---|---|---|---|---|
| PRE | F10_m20_r3_t8 | 69,702 | 86,572 [82,227,91,551] | -2,053 | -68,734 | 422,838 | 5,221,482 | -1,780,987 | -3,603,598 |
| HOLD | F10_m20_r3_t8 | 74,906 | 89,718 [82,597,96,277] | 5,917 | -47,317 | 279,578 | 1,590,722 | -791,745 | -1,979,697 |
| X | F10_m20_r3_t8 | 76,708 | 84,914 [79,977,90,065] | 10,567 | -42,208 | 447,308 | 1,857,147 | -1,128,931 | -2,381,395 |
| PRE | F9e_a30_w300_t0.3 | 90,292 | 99,190 [96,167,102,363] | 23,966 | -64,742 | 356,527 | 4,957,538 | -1,745,728 | -3,815,830 |
| HOLD | F9e_a30_w300_t0.3 | 103,391 | 107,928 [104,037,113,933] | 21,677 | -56,828 | 428,370 | 1,892,479 | -822,746 | -2,418,081 |
| X | F9e_a30_w300_t0.3 | 89,966 | 92,846 [88,267,97,116] | 13,253 | -49,343 | 331,887 | 2,171,070 | -1,302,654 | -2,694,357 |
| PRE | F9e_a20_w120_t0.2 | 66,124 | 85,266 [79,232,90,829] | 8,597 | -74,273 | 306,939 | 5,627,498 | -1,531,234 | -3,676,496 |
| HOLD | F9e_a20_w120_t0.2 | 76,650 | 84,578 [78,698,93,795] | 28,934 | -50,342 | 220,994 | 1,676,218 | -392,563 | -1,997,240 |
| X | F9e_a20_w120_t0.2 | 73,470 | 84,440 [79,096,90,127] | 19,666 | -46,486 | 369,393 | 2,045,369 | -879,781 | -2,424,340 |


Timing-matched placebo (rule exit rate and arm-to-exit delay distribution kept, 30 draws, median [5%,95%]):

| win | rule | sd | placebo_sd | mean | placebo_mean | maxdd | placebo_maxdd | worst20 | placebo_worst20 |
|---|---|---|---|---|---|---|---|---|---|
| PRE | F10_m20_r3_t8 | 69,702 | 74,611 [71,895,78,784] | -2,053 | 9,488 [4,571,13,251] | 422,838 | 334,384 | -1,780,987 | -1,658,046 |
| HOLD | F10_m20_r3_t8 | 74,906 | 83,091 [76,627,86,883] | 5,917 | 19,868 [16,737,26,698] | 279,578 | 294,459 | -791,745 | -576,326 |
| X | F10_m20_r3_t8 | 76,708 | 78,789 [76,068,85,371] | 10,567 | 16,093 [11,895,20,503] | 447,308 | 439,795 | -1,128,931 | -1,061,056 |
| PRE | F9e_a30_w300_t0.3 | 90,292 | 91,032 [88,453,94,037] | 23,966 | 23,627 [21,419,26,892] | 356,527 | 362,699 | -1,745,728 | -1,750,287 |
| HOLD | F9e_a30_w300_t0.3 | 103,391 | 105,417 [101,934,109,012] | 21,677 | 21,198 [16,980,24,598] | 428,370 | 456,017 | -822,746 | -821,391 |
| X | F9e_a30_w300_t0.3 | 89,966 | 91,100 [87,835,92,513] | 13,253 | 12,443 [10,015,16,540] | 331,887 | 342,581 | -1,302,654 | -1,330,407 |
| PRE | F9e_a20_w120_t0.2 | 66,124 | 66,383 [64,483,68,371] | 8,597 | 11,862 [8,958,13,259] | 306,939 | 259,617 | -1,531,234 | -1,430,315 |
| HOLD | F9e_a20_w120_t0.2 | 76,650 | 78,043 [74,323,80,161] | 28,934 | 26,087 [23,936,30,104] | 220,994 | 234,264 | -392,563 | -459,978 |
| X | F9e_a20_w120_t0.2 | 73,470 | 74,321 [71,803,76,637] | 19,666 | 18,518 [16,089,20,668] | 369,393 | 389,687 | -879,781 | -916,925 |
