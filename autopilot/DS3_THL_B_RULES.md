# DS3_THL_B_RULES - T-TH-LOSS section B: the loss-side rule grids vs hold-to-stop (THLB)

Research only; no live, execution-server or chart change. Prereg l2vast/ds3/prereg/THLB_prereg.md sha256 9ebc50f0f9bf67dfc36e880e53c0c7629a5f7a8a4b32f78ec1c690ba8756787b (rules_table.json sha256 e60d4abb289bcd9603267ae7b194f0ea543f599d046550a8748659aeb6132f17), logged in DECISIONS.md before any scored cell; PRE-only text DS3_THL_B_PREHOLD.md (sha256 7ad5c9f8bee3b3d862fe95d8cfa9f21d2a3a769818b6a68e40bb7ac1b86db961, DECISIONS.md); one logged holdout look per group L1..L8 (tracks THLB_L1..L8 in l2vast/struct48/ledger/holdout_looks.jsonl). UNTOUCHED (trade dates after 2026-02-06) never read. Fees per FEES.md ($4.84/contract RT, identical in both arms, they cancel in every paired delta). No account ids appear. Code l2vast/ds3/code/thl_rules/ (thl_kern.py kernel, thl_lib.py streams and pricing, thl_run.py, thl_ana.py, thl_pool.py, thl_stack.py, thl_wf.py, thl_wfrep.py, thl_rep.py, thl_repA.py; the thpr_*.py originals are untouched); results l2vast/ds3/out/thl/rules/ (cells_B.parquet = every stream x rule cell, splits_B.parquet = by session and year, pooled_ALL_B.parquet / pooled_STACK6_B.parquet, stack_B.csv, wf_table.csv, wf_trades.parquet, sealed_*.npz).

## Verdict

**0 PASS, 0 CANDIDATE, 3,476 DEAD of 3,476 stream x rule cells (22 streams x 158 rules). Pooled over the 11 intraday books (ST HM WT KB SM PE EM PB DN MV MA): 0 / 0 / 158 DEAD; pooled over the six stack books: 0 / 0 / 158 DEAD. The walk-forward re-selection chain (3-month and 1-month trailing windows, weekly steps) does not beat hold-to-stop either: 90 of 92 chain variants are WF-DEAD and the two WF-WEAK ones (PB, 1-month window) are +0.54 and +0.07 pts/trade with CIs spanning 0.**

**Plain answer.** No loss-side rule beats hold-to-stop on identical entries, pooled or on any book that clears the gates, in-sample or in the holdout, on the MEASURED basis. Pooled over the 11 intraday books (18,121 PRE trades, 7,747 HOLD trades) not one of the 158 rules has a positive PRE delta (best: efficiency-against exits that fire on 0.0% of trades, -0.03 pts/trade; best that actually cuts: cut after 60 cumulative minutes below -10, -0.04 [-0.62,+0.55], MDE 0.83, 25% of trades cut), and the White reality check on PRE (best of 158) has p = 0.987. The live loss rule (15 pts adverse, 3 of 3 conditions, 30 s) costs -1.00 pts/trade IN-SAMPLE [-2.05,+0.04] (MDE 1.49, -$39.1k/wk at the books' lots) and -1.13 in the HOLDOUT [-2.75,+0.49] (MDE 2.31, -$40.9k/wk) over the 11 books: it cuts 66% of trades, drops the win rate from 0.54 to 0.31, saves +15.3 pts per trade-average on the trades it helps and forfeits -16.3 on the rest, and about one trade in three that it cuts (32%) would have gone on to the target. Its PRE delta is negative on 19 of 22 streams (CI excludes 0 on 6) and negative on 16 of 22 in the holdout (CI excludes 0 on none: the holdout is under-powered, not reassuring). This agrees with the earlier fixed-rule result (DS3_TH_LOSS.md: KB -1.41, SM -2.50, PE -1.05, MV -1.98, MA -2.74, DN -1.64 PRE, mapped basis; here KB -2.08, SM -2.40, PE -0.84, MV -2.10, MA -2.35, DN -0.72 on the MEASURED basis): same sign, same size. Prior results are cited, not re-run: DS3_TH_LOSS.md (fixed live loss rule, no book helped) and DS3_THP_B_RULES.md (profit-side classic grids, 3,840/3,840 DEAD).

**What looks like a positive and is not.** (1) 445 of 3,476 cells have a positive PRE delta (chance expectation is of that order for a grid this size with an average delta of -1); only 5 have a PRE CI above zero (chance count 87) and all 5 die: PB L3 (MAE>=20/30, cut if under 50% recovery after 60 s) is +2.07 and +1.75 PRE but -2.16 and -1.97 in the HOLDOUT, -1.47 in the X span and fails year_share, SPAN2, NOTC and RC; two B3_NQ efficiency cells have n_PRE 78; one CR cell is +0.09. (2) The best pooled rules are "efficiency against" exits that almost never fire (cut share 0-2%), so their delta is near 0 by construction, not skill. (3) **Nearest miss, HM only.** On HM the deeper live-rule variants (adverse 20-30 pts, 3 of 3, window 10-30 s) are positive in PRE, HOLD and X at once: L6_a30_r3_w10 +1.37 / +1.82 / +0.06 pts/trade (+$5.7k / +$8.0k per week at 10 lots), L6_a30_r3_w30 +1.19 / +1.92 / +1.43, L6_a25_r3_w30 +0.91 / +1.76 / +1.27; 57 of the 158 HM rules are positive in all three windows; the placebo rank is 0.95-1.00, the N and C bases stay positive, the neighbours agree, the largest year share is 43-56%, and maxDD is $200k better. They are DEAD because the PRE CI includes zero (MDE 2.0) and the best-of-158 reality check on HM is p = 0.266; those are the only two gates they fail, and with two failures the CANDIDATE rule (at most one) is not met. Not softened. HM is the weakest book (hold-to-stop +0.35 PRE, -0.43 HOLD), the same rules are negative on the other books (pooled L6_a30_r3_w10 -0.23 PRE, +0.15 HOLD), and this is one book in 22: a lead for a pre-registered HM-only re-test, not a result. (4) Stack-level variance reduction is reproduced by timing-matched random cuts (section 9b): cutting early reduces weekly SD by itself.

**Walk-forward (section W).** Re-selecting the best rule each week on the trailing 3 months of closed trades (one rule for all 11 books) gives -0.13 pts/trade PRE [-0.68,+0.42] (MDE 0.78) and -0.84 HOLD [-2.04,+0.37] (MDE 1.72); on the trailing 1 month -0.89 / -0.29; each book picking its own rule -0.63 / -0.47 (3 months) and -0.73 / -0.36 (1 month). The WITH-HOLD policy (apply a rule only if its trailing delta is positive) is the same to two decimals. The chain beats a randomly drawn rule each week in PRE (placebo rank 0.99-1.00 at 3 months) but not in the HOLDOUT (rank 0.50-0.59), and never beats doing nothing. What it keys on drifts: 2024H1 stall under water -30, 2024H2 time under water and MAE-recovery, 2025H1 efficiency-against or hold, 2025H2 and 2026 the live-rule family at 20-30 pts and a 10-s window (W4). By entry session the pooled 3-month chain is positive only in the PRE-market session (+2.21, MDE 2.76), ASIA (+0.02) and CLOSE (+1.68, n 55) and negative in LONDON, NY-AM and NY-PM.

**Plain sentence for the directive.** Re-fitting weekly on the trailing 3 months (or 1 month), the classic loss-rule chain saves nothing out of sample: -0.13 pts/trade in-sample and -0.84 in the holdout (pooled 11 books, MDE 0.8 and 1.7), costs about $4k/wk in-sample and $25k/wk in the holdout, and nothing beats the stop. The only coherent exception is a deeper, slower-to-fire version of the live rule on HM, which fails the confidence and best-of-158 gates.

**Basis and scope caveats (read before using any number).** MEASURED = stop walk by year at 10 lots (also for tightened stops), rule market exit at the close of the decision second minus 1 tick (0-s delay; the live rule exits one second later, covered by the C basis with a 3-s delay and 2 ticks), limit targets at touch plus the P9 target correction by year; N / MW / C shown, CONSERVATIVE is a label. Hold-to-stop here means the stored bracket intact (stop, target and 16:55 flat), so the pair differs only by the loss-side rule. Locks (-2R/+5R, give-back arm, week floor) and the re-entry effect (a cut that frees a book for a new entry) are NOT in the stack-level series; section D of the directive is a later task. Not scored: ES and RTY basket legs (no 1-s path in the box; flagged); the B3 NQ leg is scored at 1 lot over multi-day holds with no stop (n_PRE 78). CR (median stop 11.5 pts) and D6 SM_t60_sst (median stop 20) are scored but flagged SHORT-STOP and excluded from the pooled sets: cuts deeper than the stop never arm there. The session cells (six D6, three O6) are small (n_PRE 134-800). The walk-forward needs 3 months of history, so the chain starts 2024-02 and has no X span. The learned policies (directive section C), the dataset (A), the joint policy (D) and the policy file (E) are not part of this file.

## 1. Scope: streams, sample sizes, the hold-to-stop baseline (MEASURED basis, net pts/trade after the 0.242-pt fee)

| stream | trades | PRE | HOLD | X | lots | stop_med | tgt_med | base_net_PRE | base_net_HOLD | win_PRE | win_HOLD | RC_p |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B3_NQ | 180 | 78 | 36 | 66 | 1.0 | 1e+09 | 1e+09 | +25.48 | +84.18 | 0.60 | 0.64 | 0.137 |
| CR | 2694 | 1337 | 575 | 782 | 10.0 | 11.5 | 30.25 | -1.04 | -3.22 | 0.31 | 0.29 | 0.082 |
| D6_HM_t75_s90_NYAM | 780 | 427 | 197 | 156 | 10.0 | 90 | 75 | +10.77 | +5.80 | 0.62 | 0.58 | 1.000 |
| D6_KB_t60_s75_ASIA | 1268 | 704 | 321 | 243 | 10.0 | 75 | 60 | +5.42 | +0.59 | 0.61 | 0.58 | 1.000 |
| D6_PB7_PB5_ASIA | 671 | 342 | 192 | 137 | 10.0 | 60 | 60 | +10.71 | +1.64 | 0.61 | 0.54 | 0.713 |
| D6_SM_t60_sst_ASIA | 524 | 264 | 123 | 137 | 10.0 | 20 | 60 | +6.32 | -0.14 | 0.41 | 0.34 | 0.387 |
| D6_TB4B_ASIA | 843 | 450 | 200 | 193 | 10.0 | 60 | 60 | +7.32 | -7.70 | 0.58 | 0.46 | 1.000 |
| D6_TB4W_03_ASIA | 1421 | 800 | 369 | 252 | 10.0 | 60 | 60 | +4.37 | -0.05 | 0.56 | 0.53 | 0.927 |
| DN | 3272 | 1762 | 782 | 728 | 10.0 | 60 | 60 | +2.97 | +2.72 | 0.54 | 0.54 | 0.865 |
| EM | 1660 | 871 | 366 | 423 | 10.0 | 60 | 60 | +2.03 | +2.02 | 0.54 | 0.55 | 0.875 |
| HM | 2924 | 1561 | 698 | 665 | 10.0 | 60 | 60 | +0.35 | -0.43 | 0.52 | 0.52 | 0.266 |
| KB | 3444 | 1854 | 756 | 834 | 5.2 | 60 | 60 | +3.66 | +2.52 | 0.55 | 0.55 | 0.879 |
| MA | 1906 | 997 | 446 | 463 | 10.0 | 60 | 60 | +1.96 | +3.49 | 0.53 | 0.56 | 0.764 |
| MV | 3627 | 2025 | 845 | 757 | 10.0 | 60 | 60 | +1.96 | -2.24 | 0.53 | 0.50 | 1.000 |
| O6_LV_RN_BH | 293 | 134 | 78 | 81 | 10.0 | 60 | 60 | +11.59 | +4.37 | 0.62 | 0.55 | 0.491 |
| O6_OR15m_stp_le1 | 361 | 179 | 72 | 110 | 10.0 | 60 | 60 | +14.10 | +6.96 | 0.64 | 0.58 | 1.000 |
| O6_OR30m_stp_ge0.5 | 594 | 297 | 125 | 172 | 10.0 | 60 | 60 | +14.85 | +4.18 | 0.64 | 0.56 | 1.000 |
| PB | 4049 | 2261 | 965 | 823 | 10.0 | 60 | 60 | -1.43 | +3.27 | 0.50 | 0.55 | 0.194 |
| PE | 3248 | 1732 | 731 | 785 | 5.6 | 60 | 60 | +1.34 | +2.04 | 0.53 | 0.54 | 0.687 |
| SM | 1457 | 774 | 294 | 389 | 7.4 | 60 | 60 | +3.38 | -0.37 | 0.55 | 0.52 | 1.000 |
| ST | 3234 | 1717 | 765 | 752 | 10.0 | 60 | 60 | +1.15 | +1.08 | 0.52 | 0.54 | 0.990 |
| WT | 4762 | 2567 | 1099 | 1096 | 7.0 | 45 | 33.75 | -0.47 | -0.98 | 0.59 | 0.60 | 0.975 |


NOT SCORED: basket legs ES and RTY (no 1-s path in the box; only the NQ leg of B3 is scored, as B3_NQ, multi-day, no stop, 1 lot, labelled). SHORT-STOP streams scored but excluded from the pooled sets: CR (single-leg simplification of a scale-out book, 8-24 pt stops) and D6_SM_t60_sst_ASIA (stop median 20): the deeper rules (cut depth >= stop) never arm there.

## 2. Multiplicity statement

Rules tried: 158 (8 groups) x 22 streams = 3476 cells, each with 20 placebo draws (69520 placebo runs); pooled cells 2 x 158. Cells with PRE delta > 0: 445 of 3476; with PRE CI lower bound > 0: 5 (chance count at 2.5% one-sided = 87); with PRE > 0 AND HOLD > 0: 210 (chance if independent ~ 869 at 25%, far more if the same bias moves both windows). White reality check on PRE, best of 158 per stream (p): B3_NQ 0.137, CR 0.082, D6_HM_t75_s90_NYAM 1.000, D6_KB_t60_s75_ASIA 1.000, D6_PB7_PB5_ASIA 0.713, D6_SM_t60_sst_ASIA 0.387, D6_TB4B_ASIA 1.000, D6_TB4W_03_ASIA 0.927, DN 0.865, EM 0.875, HM 0.266, KB 0.879, MA 0.764, MV 1.000, O6_LV_RN_BH 0.491, O6_OR15m_stp_le1 1.000, O6_OR30m_stp_ge0.5 1.000, PB 0.194, PE 0.687, SM 1.000, ST 0.990, WT 0.975. Pooled over the 11 intraday books RC p = 0.987 (best rule L2_x10_t60, t -0.12); six stack books RC p = 0.952. Best-of-N therefore applies to every positive number below: a cell with a positive PRE delta is expected by chance in a grid this size.

## 3.IN-SAMPLE mean paired delta, pts/trade, mean over the rules of each group - IN-SAMPLE (PRE 2024-02..2025-06, raw)

| fam | B3_NQ | CR | D6_HM_t75_s90_NYAM | D6_KB_t60_s75_ASIA | D6_PB7_PB5_ASIA | D6_SM_t60_sst_ASIA | D6_TB4B_ASIA | D6_TB4W_03_ASIA | DN | EM | HM | KB | MA | MV | O6_LV_RN_BH | O6_OR15m_stp_le1 | O6_OR30m_stp_ge0.5 | PB | PE | SM | ST | WT | ALL(11 books) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1 | -17.97 | +0.04 | -7.96 | -5.39 | -6.53 | -0.89 | -3.61 | -2.12 | -0.69 | -1.11 | +0.10 | -2.27 | -1.75 | -1.95 | -6.46 | -7.72 | -6.98 | +0.64 | -1.03 | -2.73 | -1.38 | -0.49 | -1.15 |
| L2 | -3.41 | +0.06 | -2.75 | -4.18 | -5.14 | -0.17 | -2.02 | -1.88 | -0.62 | -0.28 | +0.37 | -0.87 | -1.78 | -0.98 | -0.61 | -2.71 | -2.24 | +0.94 | -0.15 | -1.85 | -0.83 | -0.24 | -0.57 |
| L3 | -3.54 | -0.06 | -4.76 | -4.64 | -6.00 | -0.64 | -2.34 | -2.18 | -0.74 | -0.41 | +0.09 | -1.71 | -1.69 | -1.41 | -3.00 | -5.82 | -4.59 | +0.99 | -0.65 | -1.86 | -1.15 | -0.26 | -0.80 |
| L4 | +4.19 | -0.02 | -3.54 | -4.76 | -5.59 | -0.58 | -2.75 | -2.15 | -0.77 | -0.43 | +0.11 | -1.41 | -1.69 | -1.69 | -1.77 | -3.96 | -3.54 | +0.54 | -0.52 | -1.92 | -1.09 | -0.38 | -0.84 |
| L5 | -5.13 | -0.03 | -4.89 | -3.45 | -4.93 | -0.75 | -2.54 | -1.64 | -0.49 | -0.79 | -0.33 | -1.40 | -1.24 | -1.36 | -5.22 | -5.32 | -4.08 | +0.17 | -1.01 | -1.76 | -0.87 | -0.38 | -0.86 |
| L6 | -15.51 | +0.00 | -7.71 | -5.18 | -6.57 | -1.15 | -2.91 | -2.16 | -0.86 | -0.79 | +0.10 | -2.08 | -1.76 | -2.06 | -6.74 | -7.63 | -6.30 | +0.70 | -1.22 | -2.35 | -1.39 | -0.42 | -1.10 |
| L7 | -9.05 | -0.08 | -6.33 | -5.96 | -6.58 | -0.81 | -3.57 | -2.99 | -1.46 | -1.53 | -0.62 | -2.44 | -2.43 | -2.53 | -3.80 | -6.66 | -5.27 | -0.16 | -1.61 | -2.72 | -1.82 | -1.00 | -1.66 |
| L8 | -12.68 | +0.02 | -5.51 | -3.67 | -4.47 | -0.58 | -2.39 | -1.52 | -0.52 | -0.74 | +0.07 | -1.51 | -1.17 | -1.36 | -4.41 | -5.29 | -4.71 | +0.45 | -0.74 | -1.79 | -0.97 | -0.34 | -0.78 |

## 3.HOLDOUT mean paired delta, pts/trade, mean over the rules of each group - HOLDOUT (2025-07-01..2026-02-06, one look per group)

| fam | B3_NQ | CR | D6_HM_t75_s90_NYAM | D6_KB_t60_s75_ASIA | D6_PB7_PB5_ASIA | D6_SM_t60_sst_ASIA | D6_TB4B_ASIA | D6_TB4W_03_ASIA | DN | EM | HM | KB | MA | MV | O6_LV_RN_BH | O6_OR15m_stp_le1 | O6_OR30m_stp_ge0.5 | PB | PE | SM | ST | WT | ALL(11 books) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1 | -61.96 | +0.40 | -0.90 | -2.79 | +0.39 | +1.09 | +3.08 | +0.85 | -2.21 | -0.93 | +0.66 | -2.19 | -1.93 | +0.18 | -0.13 | -0.14 | -3.26 | -1.47 | -2.49 | +1.36 | -0.02 | -0.66 | -0.88 |
| L2 | -55.19 | +0.03 | +0.75 | -2.50 | -0.51 | +0.98 | +3.56 | +0.43 | -1.21 | +0.55 | +1.03 | -2.05 | -0.69 | +0.45 | -1.39 | +0.12 | -2.18 | -1.28 | -2.03 | +0.93 | -0.56 | -0.51 | -0.49 |
| L3 | -60.47 | +0.18 | +0.58 | -2.94 | +0.28 | +0.50 | +3.45 | +1.15 | -1.53 | +0.61 | +0.85 | -2.24 | -1.06 | +0.26 | -0.50 | -0.64 | -2.75 | -1.75 | -2.26 | +0.76 | -0.21 | -0.61 | -0.65 |
| L4 | -56.92 | +0.11 | -0.67 | -2.85 | +0.72 | +0.49 | +2.42 | +0.79 | -1.76 | +0.67 | +0.73 | -2.07 | -0.50 | +0.46 | -0.36 | -0.39 | -1.55 | -1.07 | -2.65 | +1.18 | -0.69 | -0.50 | -0.56 |
| L5 | -32.28 | +0.18 | -0.87 | -2.12 | +0.17 | +0.61 | +2.57 | +0.37 | -1.49 | -0.48 | +0.60 | -1.37 | -1.05 | +0.16 | -0.25 | -0.77 | -1.59 | -0.98 | -1.91 | +0.52 | -0.30 | -0.58 | -0.63 |
| L6 | -61.78 | +0.36 | -0.14 | -3.61 | +0.05 | +1.09 | +3.81 | +0.59 | -2.10 | -0.50 | +1.17 | -2.45 | -1.52 | +0.35 | +0.21 | -1.23 | -3.56 | -1.40 | -2.53 | +1.52 | -0.26 | -0.57 | -0.75 |
| L7 | -66.42 | -0.03 | -0.67 | -3.96 | -0.37 | +0.94 | +1.83 | -0.72 | -2.58 | -0.70 | +0.38 | -2.76 | -2.29 | -0.47 | +0.15 | -1.19 | -3.62 | -2.30 | -3.17 | +1.15 | -1.36 | -1.42 | -1.41 |
| L8 | -42.56 | +0.28 | -0.42 | -2.04 | +0.31 | +0.78 | +2.11 | +0.57 | -1.51 | -0.59 | +0.55 | -1.50 | -1.23 | +0.17 | -0.04 | -0.18 | -2.27 | -0.94 | -1.70 | +1.03 | -0.04 | -0.45 | -0.56 |

## 3.X mean paired delta, pts/trade, mean over the rules of each group - X span (2023-04..2024-01)

| fam | B3_NQ | CR | D6_HM_t75_s90_NYAM | D6_KB_t60_s75_ASIA | D6_PB7_PB5_ASIA | D6_SM_t60_sst_ASIA | D6_TB4B_ASIA | D6_TB4W_03_ASIA | DN | EM | HM | KB | MA | MV | O6_LV_RN_BH | O6_OR15m_stp_le1 | O6_OR30m_stp_ge0.5 | PB | PE | SM | ST | WT | ALL(11 books) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1 | -30.79 | -0.12 | -7.16 | -0.16 | +0.31 | -0.12 | +2.91 | +0.51 | +0.52 | +0.04 | -0.18 | +1.46 | +0.25 | +2.29 | +1.76 | +3.53 | +1.42 | -1.60 | -0.81 | +1.09 | -1.43 | -0.32 | +0.12 |
| L2 | -30.57 | -0.03 | -5.18 | -0.47 | +0.41 | -0.66 | +2.67 | +0.26 | -0.06 | +0.09 | -0.02 | +1.19 | +0.37 | +1.85 | -1.53 | +0.21 | +0.39 | -0.48 | +0.25 | +0.78 | -1.17 | -0.25 | +0.23 |
| L3 | -28.68 | -0.04 | -6.46 | -0.40 | +0.57 | -0.59 | +3.07 | +0.79 | +0.11 | -0.09 | +0.20 | +1.21 | -0.08 | +1.67 | -1.40 | +1.71 | +1.38 | -1.18 | -0.40 | +1.07 | -1.05 | -0.16 | +0.12 |
| L4 | -24.57 | -0.10 | -3.56 | -0.74 | +0.62 | -0.28 | +2.73 | +0.83 | -0.03 | -0.13 | +0.25 | +1.00 | +0.07 | +1.99 | -2.04 | -0.34 | +1.69 | -0.79 | +0.11 | +1.42 | -0.81 | +0.22 | +0.30 |
| L5 | -21.90 | -0.14 | -4.09 | +0.35 | +0.27 | -0.64 | +1.73 | +0.65 | +0.30 | +0.04 | -0.28 | +0.96 | +0.27 | +1.24 | +0.85 | +2.46 | +0.64 | -1.06 | -0.55 | +0.23 | -0.86 | -0.14 | +0.01 |
| L6 | -31.07 | -0.18 | -7.67 | -0.09 | +0.87 | -0.26 | +3.29 | +1.03 | +0.65 | +0.26 | +0.25 | +1.50 | +0.21 | +2.36 | +0.70 | +3.30 | +1.51 | -1.38 | -0.52 | +1.31 | -0.99 | -0.24 | +0.31 |
| L7 | -28.03 | -0.20 | -8.56 | -0.59 | -0.43 | -0.46 | +2.97 | +0.75 | -0.00 | +0.14 | -0.09 | +1.01 | +0.16 | +1.80 | +0.61 | +1.92 | -0.14 | -1.93 | -0.35 | +0.36 | -1.73 | -0.52 | -0.11 |
| L8 | -21.43 | -0.08 | -4.93 | -0.12 | +0.27 | -0.09 | +1.99 | +0.41 | +0.37 | +0.12 | -0.05 | +1.04 | +0.24 | +1.61 | +1.22 | +2.35 | +0.95 | -1.12 | -0.48 | +0.73 | -0.92 | -0.21 | +0.12 |

## 3c. Saved loss vs forfeited recovery by rule group, pooled over the 11 intraday books (means over the rules of the group; cut_that_would_hit_target = share of the cut trades whose hold-to-stop exit was the target)

| group | rules | PRE_delta_mean | PRE_delta_best | HOLD_delta_mean | HOLD_delta_best | cut_share_PRE | cut_that_would_hit_target_PRE | saved_loss_per_trade_PRE | forfeited_recovery_per_trade_PRE | win_base_PRE | win_rule_PRE | usd_wk_PRE_mean | usd_wk_HOLD_mean |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1 | 5 | -0.99 | -0.27 | -0.98 | -0.23 | 68% | 30% | +15.63 | -16.63 | 0.54 | 0.31 | -38,143 | -34,674 |
| L2 | 15 | -0.43 | -0.04 | -0.64 | +0.16 | 44% | 29% | +10.02 | -10.44 | 0.54 | 0.39 | -16,654 | -19,876 |
| L3 | 18 | -0.67 | -0.33 | -0.81 | -0.04 | 53% | 31% | +12.42 | -13.10 | 0.54 | 0.36 | -25,879 | -26,862 |
| L4 | 12 | -0.73 | -0.18 | -0.74 | +0.01 | 49% | 26% | +10.06 | -10.80 | 0.54 | 0.40 | -29,230 | -23,496 |
| L5 | 18 | -0.76 | -0.03 | -0.69 | +0.19 | 42% | 47% | +10.32 | -11.08 | 0.54 | 0.38 | -29,769 | -24,328 |
| L6 | 60 | -0.97 | -0.23 | -0.88 | +0.15 | 67% | 32% | +15.58 | -16.56 | 0.54 | 0.31 | -37,678 | -29,433 |
| L7 | 22 | -1.54 | -0.28 | -1.59 | -0.54 | 61% | 28% | +12.88 | -14.41 | 0.54 | 0.35 | -61,716 | -59,654 |
| L8 | 8 | -0.68 | -0.14 | -0.64 | -0.12 | 71% | 33% | +10.68 | -11.37 | 0.54 | 0.48 | -26,258 | -22,223 |

## 4. The live loss-side Trade Health rule L6_a15_r3_w30 (15 pts adverse, 3 of 3 conditions, 30 s) vs hold-to-stop, per book (IN-SAMPLE and HOLDOUT side by side)

| stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B3_NQ | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 78 | -5.73 [-54.70,+43.24] (69.96) | 36 | -57.76 [-133.92,+18.41] (108.81) | -35.90 (49.54) | -119|-1,300 | +74.59|-80.32 | 65 (83%) | 0%|0% | +0.00 | 0.60>0.17 | 0.80|0.20 | -5.73|-5.73|-6.01 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05,n_PRE<100 |
| CR | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 1337 | +0.13 [-0.55,+0.81] (0.97) | 575 | -0.40 [-1.57,+0.76] (1.66) | -0.21 (0.81) | 463|-1,444 | +1.63|-1.50 | 188 (14%) | 18%|20% | -0.18 | 0.31>0.28 | 0.90|0.15 | +0.08|+0.03|+0.18 | DEAD | holdout_sign_agrees,placebo<0.95,neighbours_agree,paired_CI_excludes0,maxDD_not_worse,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_HM_t75_s90_NYAM | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 427 | -6.10 [-12.21,+0.02] (8.74) | 197 | +0.76 [-7.37,+8.89] (11.61) | -8.99 (13.19) | -6,941|940 | +21.23|-27.32 | 287 (67%) | 39%|33% | -0.89 | 0.62>0.31 | 0.65|0.70 | -6.67|-6.53|-5.77 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_KB_t60_s75_ASIA | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 704 | -4.08 [-7.87,-0.29] (5.41) | 321 | -4.52 [-10.41,+1.36] (8.41) | -0.26 (8.95) | -7,655|-9,075 | +18.91|-22.98 | 467 (66%) | 42%|44% | -1.02 | 0.61>0.32 | 0.40|0.10 | -4.74|-4.55|-3.86 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_PB7_PB5_ASIA | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 342 | -6.37 [-11.38,-1.35] (7.16) | 192 | -1.00 [-7.07,+5.08] (8.68) | +2.84 (9.52) | -5,808|-1,194 | +13.66|-20.03 | 214 (63%) | 41%|34% | -0.95 | 0.61>0.35 | 0.55|0.40 | -6.97|-6.83|-6.27 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| D6_SM_t60_sst_ASIA | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 264 | -1.77 [-5.18,+1.65] (4.88) | 123 | +1.06 [-2.59,+4.71] (5.21) | -1.09 (3.28) | -1,244|815 | +4.70|-6.46 | 96 (36%) | 22%|16% | -0.48 | 0.41>0.33 | 0.00|0.60 | -1.96|-2.03|-1.62 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_TB4B_ASIA | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 450 | -3.39 [-7.60,+0.81] (6.01) | 200 | +4.73 [-1.40,+10.87] (8.77) | +5.00 (7.65) | -4,071|5,917 | +14.80|-18.20 | 286 (64%) | 36%|27% | -0.91 | 0.58>0.35 | 0.05|0.90 | -3.90|-3.86|-3.19 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| D6_TB4W_03_ASIA | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 800 | -1.65 [-4.62,+1.31] (4.23) | 369 | +0.85 [-3.54,+5.25] (6.27) | +2.37 (7.35) | -3,526|1,970 | +15.82|-17.47 | 520 (65%) | 34%|33% | -1.00 | 0.56>0.33 | 0.35|0.90 | -2.20|-2.13|-1.43 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| DN | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 1762 | -0.72 [-2.73,+1.29] (2.87) | 782 | -2.57 [-5.64,+0.49] (4.38) | +1.12 (4.36) | -3,376|-12,572 | +15.64|-16.36 | 1126 (64%) | 32%|34% | -0.87 | 0.54>0.33 | 0.35|0.05 | -1.18|-1.17|-0.49 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| EM | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 871 | -0.26 [-3.14,+2.62] (4.11) | 366 | -1.40 [-5.91,+3.11] (6.44) | +0.08 (5.71) | -608|-3,197 | +16.40|-16.66 | 575 (66%) | 31%|33% | -0.83 | 0.54>0.31 | 0.45|0.10 | -0.67|-0.73|-0.06 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| HM | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 1561 | +0.32 [-1.89,+2.54] (3.17) | 698 | -0.57 [-3.83,+2.69] (4.65) | +0.93 (4.57) | 1,346|-2,495 | +17.06|-16.74 | 1067 (68%) | 30%|30% | -0.90 | 0.52>0.30 | 0.75|0.15 | -0.13|-0.16|+0.58 | DEAD | holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| KB | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 1854 | -2.08 [-4.09,-0.07] (2.88) | 756 | -2.51 [-5.85,+0.84] (4.78) | +1.12 (4.11) | -5,285|-4,764 | +15.91|-17.99 | 1240 (67%) | 33%|34% | -0.92 | 0.55>0.31 | 0.20|0.45 | -2.59|-2.55|-1.78 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| MA | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 997 | -2.35 [-5.18,+0.48] (4.04) | 446 | -1.96 [-6.09,+2.18] (5.91) | +0.36 (5.64) | -6,240|-5,459 | +15.94|-18.29 | 679 (68%) | 33%|33% | -0.88 | 0.53>0.29 | 0.05|0.25 | -2.81|-2.83|-2.18 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| MV | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 2025 | -2.10 [-4.07,-0.13] (2.81) | 845 | +0.92 [-1.98,+3.83] (4.15) | +1.42 (4.40) | -11,320|4,876 | +16.30|-18.40 | 1390 (69%) | 33%|30% | -0.93 | 0.53>0.29 | 0.20|0.80 | -2.60|-2.58|-1.87 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| O6_LV_RN_BH | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 134 | -7.69 [-15.40,+0.02] (11.01) | 78 | -1.19 [-9.68,+7.30] (12.13) | +0.52 (14.35) | -2,749|-581 | +12.82|-20.52 | 80 (60%) | 42%|31% | -0.76 | 0.62>0.35 | 0.40|0.20 | -8.15|-8.13|-7.09 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| O6_OR15m_stp_le1 | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 179 | -9.17 [-15.60,-2.73] (9.19) | 72 | -4.51 [-13.98,+4.97] (13.53) | +2.95 (11.94) | -4,375|-2,028 | +11.08|-20.24 | 104 (58%) | 42%|35% | -0.77 | 0.64>0.37 | 0.05|0.05 | -9.66|-9.58|-9.01 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| O6_OR30m_stp_ge0.5 | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 297 | -6.94 [-11.87,-2.01] (7.04) | 125 | -5.05 [-12.74,+2.63] (10.98) | +2.09 (9.21) | -5,495|-3,948 | +11.68|-18.62 | 166 (56%) | 42%|35% | -0.67 | 0.64>0.40 | 0.20|0.45 | -7.34|-7.34|-6.85 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| PB | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 2261 | +0.10 [-1.75,+1.94] (2.63) | 965 | -1.38 [-4.07,+1.31] (3.84) | +0.03 (4.28) | 575|-8,321 | +17.13|-17.04 | 1556 (69%) | 31%|33% | -0.94 | 0.50>0.28 | 0.15|0.50 | -0.40|-0.39|+0.37 | DEAD | holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| PE | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 1732 | -0.84 [-2.95,+1.28] (3.02) | 731 | -2.28 [-5.49,+0.93] (4.59) | +0.02 (4.19) | -2,163|-5,417 | +16.73|-17.57 | 1186 (68%) | 32%|34% | -0.92 | 0.53>0.30 | 0.50|0.40 | -1.32|-1.33|-0.54 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| SM | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 774 | -2.40 [-5.62,+0.81] (4.60) | 294 | +1.18 [-3.52,+5.87] (6.70) | +0.54 (6.05) | -3,838|2,091 | +16.10|-18.51 | 520 (67%) | 35%|30% | -0.87 | 0.55>0.30 | 0.20|0.65 | -2.88|-2.89|-2.18 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| ST | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 1717 | -0.98 [-3.07,+1.10] (2.98) | 765 | -0.32 [-3.55,+2.91] (4.61) | +0.27 (4.29) | -4,501|-1,546 | +16.55|-17.53 | 1176 (68%) | 31%|31% | -0.93 | 0.52>0.30 | 0.25|0.20 | -1.47|-1.47|-0.79 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| WT | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 2567 | -0.77 [-1.78,+0.24] (1.44) | 1099 | -0.86 [-2.42,+0.71] (2.24) | +0.01 (2.15) | -3,690|-4,111 | +8.77|-9.54 | 1423 (55%) | 34%|35% | -0.75 | 0.59>0.40 | 0.00|0.00 | -1.16|-1.18|-0.58 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,NOTC<=0,RC_p>0.05 |


Pooled (cluster = label day x session across books):

| stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 11 BOOKS | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 18121 | -1.00 [-2.05,+0.04] (1.49) | 7747 | -1.13 [-2.75,+0.49] (2.31) | +0.53 (2.16) | -39,100|-40,914 | +15.34|-16.34 | 11938 (66%) | 32%|33% | -0.89 | 0.54>0.31 | 0.00|0.05 | -1.47|-1.47|-0.77 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| STACK6 | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 10205 | -1.01 [-2.12,+0.10] (1.59) | 4343 | -1.11 [-2.88,+0.67] (2.54) | +0.44 (2.26) | -18,130|-16,242 | +14.55|-15.56 | 6612 (65%) | 32%|33% | -0.87 | 0.55>0.32 | 0.00|0.05 | -1.47|-1.47|-0.77 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,NOTC<=0,RC_p>0.05 |


## 5. Per book: LIVE control, best rule by IN-SAMPLE delta, best rule by HOLDOUT delta (regardless of verdict)

### B3_NQ

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | B3_NQ | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 78 | -5.73 [-54.70,+43.24] (69.96) | 36 | -57.76 [-133.92,+18.41] (108.81) | -35.90 (49.54) | -119|-1,300 | +74.59|-80.32 | 65 (83%) | 0%|0% | +0.00 | 0.60>0.17 | 0.80|0.20 | -5.73|-5.73|-6.01 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05,n_PRE<100 |
| best IN-SAMPLE | B3_NQ | L5e_x10_w120_t0.5 | efficiency against: below -10 and directional ER(120s)>=0.5 against | 78 | +32.71 [+2.65,+62.77] (42.94) | 36 | +6.11 [-28.91,+41.13] (50.02) | -15.91 (27.67) | 680|138 | +44.70|-11.99 | 24 (31%) | 0%|0% | +0.00 | 0.60>0.50 | 1.00|0.80 | +32.71|+32.71|+33.05 | DEAD | year_share>60%,SPAN2<=0,RC_p>0.05,n_PRE<100 |
| best HOLDOUT | B3_NQ | L5e_x10_w120_t0.5 | efficiency against: below -10 and directional ER(120s)>=0.5 against | 78 | +32.71 [+2.65,+62.77] (42.94) | 36 | +6.11 [-28.91,+41.13] (50.02) | -15.91 (27.67) | 680|138 | +44.70|-11.99 | 24 (31%) | 0%|0% | +0.00 | 0.60>0.50 | 1.00|0.80 | +32.71|+32.71|+33.05 | DEAD | year_share>60%,SPAN2<=0,RC_p>0.05,n_PRE<100 |

### CR

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | CR | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 1337 | +0.13 [-0.55,+0.81] (0.97) | 575 | -0.40 [-1.57,+0.76] (1.66) | -0.21 (0.81) | 463|-1,444 | +1.63|-1.50 | 188 (14%) | 18%|20% | -0.18 | 0.31>0.28 | 0.90|0.15 | +0.08|+0.03|+0.18 | DEAD | holdout_sign_agrees,placebo<0.95,neighbours_agree,paired_CI_excludes0,maxDD_not_worse,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | CR | L2_x5_t5 | cut after 5 cumulative min below -5 | 1337 | +0.29 [-0.28,+0.86] (0.82) | 575 | +0.58 [-0.38,+1.53] (1.36) | -0.37 (0.86) | 1,036|2,082 | +1.73|-1.44 | 222 (17%) | 19%|16% | -0.21 | 0.31>0.28 | 0.95|0.75 | +0.23|+0.17|+0.33 | DEAD | neighbours_agree,paired_CI_excludes0,year_share>60%,SPAN2<=0,RC_p>0.05 |
| best HOLDOUT | CR | L6_a10_r1_w120 | live TH loss grid: adverse 10, 1 of 3, window 120s | 1337 | -0.05 [-1.12,+1.02] (1.53) | 575 | +1.38 [-0.10,+2.86] (2.12) | -0.24 (1.15) | -179|4,959 | +4.16|-4.21 | 539 (40%) | 21%|14% | -0.51 | 0.31>0.24 | 0.80|0.75 | -0.22|-0.35|+0.05 | DEAD | mean_up,placebo>=0.90,neighbours_agree,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |

### D6_HM_t75_s90_NYAM

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | D6_HM_t75_s90_NYAM | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 427 | -6.10 [-12.21,+0.02] (8.74) | 197 | +0.76 [-7.37,+8.89] (11.61) | -8.99 (13.19) | -6,941|940 | +21.23|-27.32 | 287 (67%) | 39%|33% | -0.89 | 0.62>0.31 | 0.65|0.70 | -6.67|-6.53|-5.77 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | D6_HM_t75_s90_NYAM | L5e_x20_w300_t0.7 | efficiency against: below -20 and directional ER(300s)>=0.7 against | 427 | +0.00 [+0.00,+0.00] (0.00) | 197 | +0.00 [+0.00,+0.00] (0.00) | +0.00 (0.00) | 0|0 | +0.00|+0.00 | 0 (0%) | 0%|0% | +0.00 | 0.62>0.62 | 0.00|0.00 | +0.00|+0.00|+0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | D6_HM_t75_s90_NYAM | L6_a20_r3_w10 | live TH loss grid: adverse 20, 3 of 3, window 10s | 427 | -6.65 [-12.74,-0.57] (8.69) | 197 | +3.35 [-4.41,+11.11] (11.08) | -8.76 (13.03) | -7,577|4,125 | +20.66|-27.32 | 281 (66%) | 38%|30% | -0.88 | 0.62>0.33 | 0.35|0.95 | -7.22|-7.09|-6.25 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |

### D6_KB_t60_s75_ASIA

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | D6_KB_t60_s75_ASIA | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 704 | -4.08 [-7.87,-0.29] (5.41) | 321 | -4.52 [-10.41,+1.36] (8.41) | -0.26 (8.95) | -7,655|-9,075 | +18.91|-22.98 | 467 (66%) | 42%|44% | -1.02 | 0.61>0.32 | 0.40|0.10 | -4.74|-4.55|-3.86 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | D6_KB_t60_s75_ASIA | L5e_x20_w300_t0.7 | efficiency against: below -20 and directional ER(300s)>=0.7 against | 704 | -0.14 [-0.41,+0.13] (0.38) | 321 | +0.00 [+0.00,+0.00] (0.00) | -0.03 (0.09) | -257|0 | +0.00|-0.14 | 1 (0%) | 100%|0% | -0.00 | 0.61>0.61 | 0.05|0.50 | -0.14|-0.14|-0.14 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | D6_KB_t60_s75_ASIA | L5e_x10_w120_t0.7 | efficiency against: below -10 and directional ER(120s)>=0.7 against | 704 | -0.98 [-2.45,+0.48] (2.09) | 321 | +0.22 [-1.66,+2.10] (2.68) | -0.25 (3.88) | -1,842|444 | +2.15|-3.13 | 57 (8%) | 44%|33% | -0.08 | 0.61>0.57 | 0.00|0.80 | -1.03|-1.04|-0.96 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |

### D6_PB7_PB5_ASIA

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | D6_PB7_PB5_ASIA | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 342 | -6.37 [-11.38,-1.35] (7.16) | 192 | -1.00 [-7.07,+5.08] (8.68) | +2.84 (9.52) | -5,808|-1,194 | +13.66|-20.03 | 214 (63%) | 41%|34% | -0.95 | 0.61>0.35 | 0.55|0.40 | -6.97|-6.83|-6.27 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | D6_PB7_PB5_ASIA | L5e_x10_w300_t0.5 | efficiency against: below -10 and directional ER(300s)>=0.5 against | 342 | +0.15 [-0.14,+0.43] (0.41) | 192 | +0.00 [+0.00,+0.00] (0.00) | +0.00 (0.00) | 133|0 | +0.15|+0.00 | 1 (0%) | 0%|0% | -0.00 | 0.61>0.61 | 0.95|0.53 | +0.15|+0.14|+0.14 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | D6_PB7_PB5_ASIA | L3_m30_y25_n900 | MAE>=30: cut if recovery < 25% of MAE 900s after the MAE | 342 | -2.42 [-5.93,+1.09] (5.01) | 192 | +3.29 [-0.50,+7.08] (5.42) | +0.47 (8.33) | -2,204|3,944 | +7.36|-9.78 | 128 (37%) | 30%|18% | -0.51 | 0.61>0.49 | 0.85|1.00 | -2.67|-2.69|-2.32 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |

### D6_SM_t60_sst_ASIA

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | D6_SM_t60_sst_ASIA | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 264 | -1.77 [-5.18,+1.65] (4.88) | 123 | +1.06 [-2.59,+4.71] (5.21) | -1.09 (3.28) | -1,244|815 | +4.70|-6.46 | 96 (36%) | 22%|16% | -0.48 | 0.41>0.33 | 0.00|0.60 | -1.96|-2.03|-1.62 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | D6_SM_t60_sst_ASIA | L2_x10_t60 | cut after 60 cumulative min below -10 | 264 | +1.11 [-0.16,+2.38] (1.82) | 123 | +0.40 [-2.33,+3.12] (3.89) | -0.47 (2.39) | 782|305 | +1.77|-0.66 | 25 (9%) | 8%|25% | -0.10 | 0.41>0.40 | 0.95|0.70 | +1.09|+1.05|+1.20 | DEAD | paired_CI_excludes0,SPAN2<=0,RC_p>0.05 |
| best HOLDOUT | D6_SM_t60_sst_ASIA | L5v_x10_w120_p10 | velocity against: below -10 and 10 pts adverse over 120s | 264 | -1.18 [-4.82,+2.47] (5.21) | 123 | +3.06 [-1.55,+7.66] (6.58) | -1.54 (4.45) | -829|2,349 | +6.99|-8.17 | 137 (52%) | 21%|13% | -0.69 | 0.41>0.30 | 0.45|1.00 | -1.46|-1.55|-0.69 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |

### D6_TB4B_ASIA

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | D6_TB4B_ASIA | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 450 | -3.39 [-7.60,+0.81] (6.01) | 200 | +4.73 [-1.40,+10.87] (8.77) | +5.00 (7.65) | -4,071|5,917 | +14.80|-18.20 | 286 (64%) | 36%|27% | -0.91 | 0.58>0.35 | 0.05|0.90 | -3.90|-3.86|-3.19 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | D6_TB4B_ASIA | L5e_x20_w300_t0.7 | efficiency against: below -20 and directional ER(300s)>=0.7 against | 450 | +0.00 [+0.00,+0.00] (0.00) | 200 | +0.00 [+0.00,+0.00] (0.00) | +0.00 (0.00) | 0|0 | +0.00|+0.00 | 0 (0%) | 0%|0% | +0.00 | 0.58>0.58 | 0.00|0.00 | +0.00|+0.00|+0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | D6_TB4B_ASIA | L6_a10_r3_w60 | live TH loss grid: adverse 10, 3 of 3, window 60s | 450 | -4.50 [-9.38,+0.38] (6.97) | 200 | +6.89 [+0.21,+13.57] (9.54) | +3.44 (9.40) | -5,401|8,610 | +18.39|-22.89 | 326 (72%) | 43%|31% | -1.06 | 0.58>0.26 | 0.00|1.00 | -5.18|-5.04|-4.22 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |

### D6_TB4W_03_ASIA

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | D6_TB4W_03_ASIA | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 800 | -1.65 [-4.62,+1.31] (4.23) | 369 | +0.85 [-3.54,+5.25] (6.27) | +2.37 (7.35) | -3,526|1,970 | +15.82|-17.47 | 520 (65%) | 34%|33% | -1.00 | 0.56>0.33 | 0.35|0.90 | -2.20|-2.13|-1.43 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | D6_TB4W_03_ASIA | L6_a30_r3_w30 | live TH loss grid: adverse 30, 3 of 3, window 30s | 800 | +0.48 [-1.76,+2.72] (3.20) | 369 | +2.34 [-0.98,+5.67] (4.75) | +1.13 (5.84) | 1,023|5,401 | +9.91|-9.43 | 397 (50%) | 21%|18% | -0.69 | 0.56>0.45 | 0.90|0.85 | +0.23|+0.11|+0.64 | DEAD | placebo<0.95,neighbours_agree,paired_CI_excludes0,year_share>60%,RC_p>0.05 |
| best HOLDOUT | D6_TB4W_03_ASIA | L3_m30_y25_n900 | MAE>=30: cut if recovery < 25% of MAE 900s after the MAE | 800 | -0.97 [-3.26,+1.32] (3.28) | 369 | +3.25 [+0.74,+5.77] (3.59) | +1.00 (6.51) | -2,065|7,504 | +8.48|-9.45 | 323 (40%) | 26%|17% | -0.55 | 0.56>0.45 | 0.20|1.00 | -1.21|-1.27|-0.82 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |

### DN

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | DN | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 1762 | -0.72 [-2.73,+1.29] (2.87) | 782 | -2.57 [-5.64,+0.49] (4.38) | +1.12 (4.36) | -3,376|-12,572 | +15.64|-16.36 | 1126 (64%) | 32%|34% | -0.87 | 0.54>0.33 | 0.35|0.05 | -1.18|-1.17|-0.49 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | DN | L2_x5_t5 | cut after 5 cumulative min below -5 | 1762 | +0.22 [-1.87,+2.30] (2.97) | 782 | -2.21 [-5.33,+0.91] (4.46) | -0.90 (4.93) | 1,010|-10,800 | +17.12|-16.90 | 1145 (65%) | 35%|39% | -0.87 | 0.54>0.30 | 0.85|0.00 | -0.28|-0.24|+0.34 | DEAD | holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | DN | L5e_x10_w120_t0.5 | efficiency against: below -10 and directional ER(120s)>=0.5 against | 1762 | -0.40 [-1.04,+0.25] (0.91) | 782 | +0.51 [-0.44,+1.45] (1.35) | +0.08 (1.51) | -1,856|2,480 | +1.32|-1.71 | 98 (6%) | 40%|25% | -0.07 | 0.54>0.52 | 0.00|1.00 | -0.44|-0.43|-0.37 | DEAD | mean_up,placebo>=0.90,neighbours_agree,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |

### EM

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | EM | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 871 | -0.26 [-3.14,+2.62] (4.11) | 366 | -1.40 [-5.91,+3.11] (6.44) | +0.08 (5.71) | -608|-3,197 | +16.40|-16.66 | 575 (66%) | 31%|33% | -0.83 | 0.54>0.31 | 0.45|0.10 | -0.67|-0.73|-0.06 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | EM | L3_m30_y50_n300 | MAE>=30: cut if recovery < 50% of MAE 300s after the MAE | 871 | +0.79 [-1.45,+3.02] (3.19) | 366 | +2.02 [-1.50,+5.55] (5.04) | +0.01 (4.81) | 1,823|4,625 | +10.67|-9.89 | 400 (46%) | 24%|25% | -0.55 | 0.54>0.41 | 0.80|0.95 | +0.56|+0.46|+0.93 | DEAD | placebo>=0.90,paired_CI_excludes0,year_share>60%,RC_p>0.05 |
| best HOLDOUT | EM | L4_x30_n300 | stall under water: below -30, no new MAE and recovery <= 2 pts for 300s | 871 | +0.25 [-1.43,+1.93] (2.40) | 366 | +2.75 [+0.41,+5.08] (3.33) | -0.24 (4.02) | 577|6,280 | +5.85|-5.60 | 301 (35%) | 16%|11% | -0.38 | 0.54>0.47 | 0.55|1.00 | +0.15|+0.00|+0.40 | DEAD | placebo>=0.90,neighbours_agree,paired_CI_excludes0,year_share>60%,SPAN2<=0,RC_p>0.05 |

### HM

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | HM | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 1561 | +0.32 [-1.89,+2.54] (3.17) | 698 | -0.57 [-3.83,+2.69] (4.65) | +0.93 (4.57) | 1,346|-2,495 | +17.06|-16.74 | 1067 (68%) | 30%|30% | -0.90 | 0.52>0.30 | 0.75|0.15 | -0.13|-0.16|+0.58 | DEAD | holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | HM | L6_a30_r3_w10 | live TH loss grid: adverse 30, 3 of 3, window 10s | 1561 | +1.37 [-0.05,+2.79] (2.03) | 698 | +1.82 [-0.10,+3.75] (2.75) | +0.06 (2.92) | 5,690|7,961 | +8.24|-6.87 | 692 (44%) | 15%|12% | -0.53 | 0.52>0.44 | 1.00|0.95 | +1.22|+1.06|+1.45 | DEAD | paired_CI_excludes0,RC_p>0.05 |
| best HOLDOUT | HM | L6_a25_r2_w10 | live TH loss grid: adverse 25, 2 of 3, window 10s | 1561 | +0.31 [-1.88,+2.50] (3.12) | 698 | +2.66 [-0.44,+5.76] (4.43) | +0.85 (4.45) | 1,285|11,602 | +16.55|-16.25 | 1055 (68%) | 28%|24% | -0.88 | 0.52>0.32 | 0.55|0.75 | -0.10|-0.17|+0.56 | DEAD | placebo>=0.90,paired_CI_excludes0,NOTC<=0,RC_p>0.05 |

### KB

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | KB | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 1854 | -2.08 [-4.09,-0.07] (2.88) | 756 | -2.51 [-5.85,+0.84] (4.78) | +1.12 (4.11) | -5,285|-4,764 | +15.91|-17.99 | 1240 (67%) | 33%|34% | -0.92 | 0.55>0.31 | 0.20|0.45 | -2.59|-2.55|-1.78 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | KB | L2_x5_t60 | cut after 60 cumulative min below -5 | 1854 | +0.44 [-0.89,+1.76] (1.90) | 756 | -1.98 [-4.18,+0.21] (3.14) | +0.40 (3.28) | 1,401|-3,996 | +7.72|-7.29 | 605 (33%) | 27%|34% | -0.39 | 0.55>0.45 | 1.00|0.05 | +0.25|+0.22|+0.49 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | KB | L5e_x10_w120_t0.7 | efficiency against: below -10 and directional ER(120s)>=0.7 against | 1854 | -0.21 [-0.66,+0.25] (0.65) | 756 | +0.17 [-0.43,+0.77] (0.86) | -0.34 (0.95) | -453|319 | +0.68|-0.89 | 54 (3%) | 35%|27% | -0.03 | 0.55>0.53 | 0.05|0.90 | -0.23|-0.23|-0.20 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |

### MA

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | MA | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 997 | -2.35 [-5.18,+0.48] (4.04) | 446 | -1.96 [-6.09,+2.18] (5.91) | +0.36 (5.64) | -6,240|-5,459 | +15.94|-18.29 | 679 (68%) | 33%|33% | -0.88 | 0.53>0.29 | 0.05|0.25 | -2.81|-2.83|-2.18 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | MA | L5e_x20_w120_t0.5 | efficiency against: below -20 and directional ER(120s)>=0.5 against | 997 | +0.26 [-0.50,+1.02] (1.09) | 446 | +0.43 [-0.64,+1.50] (1.53) | +0.78 (0.91) | 693|1,211 | +1.43|-1.16 | 59 (6%) | 22%|19% | -0.07 | 0.53>0.52 | 0.95|0.90 | +0.23|+0.22|+0.29 | DEAD | neighbours_agree,paired_CI_excludes0,year_share>60%,RC_p>0.05 |
| best HOLDOUT | MA | L4_x30_n300 | stall under water: below -30, no new MAE and recovery <= 2 pts for 300s | 997 | -0.61 [-2.29,+1.07] (2.40) | 446 | +0.96 [-1.45,+3.37] (3.44) | -0.15 (3.74) | -1,628|2,681 | +5.83|-6.44 | 350 (35%) | 18%|15% | -0.42 | 0.53>0.47 | 0.55|0.80 | -0.75|-0.86|-0.47 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |

### MV

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | MV | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 2025 | -2.10 [-4.07,-0.13] (2.81) | 845 | +0.92 [-1.98,+3.83] (4.15) | +1.42 (4.40) | -11,320|4,876 | +16.30|-18.40 | 1390 (69%) | 33%|30% | -0.93 | 0.53>0.29 | 0.20|0.80 | -2.60|-2.58|-1.87 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | MV | L5e_x20_w300_t0.7 | efficiency against: below -20 and directional ER(300s)>=0.7 against | 2025 | -0.05 [-0.13,+0.04] (0.13) | 845 | +0.00 [+0.00,+0.00] (0.00) | +0.00 (0.00) | -244|0 | +0.00|-0.05 | 1 (0%) | 100%|0% | -0.00 | 0.53>0.53 | 0.00|0.50 | -0.05|-0.05|-0.05 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | MV | L6_a20_r3_w60 | live TH loss grid: adverse 20, 3 of 3, window 60s | 2025 | -1.91 [-3.71,-0.10] (2.58) | 845 | +1.60 [-0.98,+4.18] (3.69) | +1.98 (4.08) | -10,296|8,446 | +13.69|-15.59 | 1251 (62%) | 29%|25% | -0.81 | 0.53>0.34 | 0.00|0.95 | -2.30|-2.34|-1.64 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,NOTC<=0,RC_p>0.05 |

### O6_LV_RN_BH

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | O6_LV_RN_BH | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 134 | -7.69 [-15.40,+0.02] (11.01) | 78 | -1.19 [-9.68,+7.30] (12.13) | +0.52 (14.35) | -2,749|-581 | +12.82|-20.52 | 80 (60%) | 42%|31% | -0.76 | 0.62>0.35 | 0.40|0.20 | -8.15|-8.13|-7.09 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | O6_LV_RN_BH | L6_a30_r3_w60 | live TH loss grid: adverse 30, 3 of 3, window 60s | 134 | +2.78 [-0.98,+6.54] (5.37) | 78 | +1.32 [-3.99,+6.63] (7.59) | -2.95 (11.48) | 994|643 | +6.54|-3.75 | 43 (32%) | 9%|15% | -0.37 | 0.62>0.57 | 0.95|0.50 | +2.71|+2.55|+3.14 | DEAD | neighbours_agree,paired_CI_excludes0,maxDD_not_worse,SPAN2<=0,RC_p>0.05 |
| best HOLDOUT | O6_LV_RN_BH | L5v_x20_w120_p6 | velocity against: below -20 and 6 pts adverse over 120s | 134 | -8.26 [-16.31,-0.21] (11.50) | 78 | +5.25 [-2.93,+13.43] (11.69) | +1.66 (14.31) | -2,951|2,558 | +14.01|-22.27 | 87 (65%) | 41%|24% | -0.90 | 0.62>0.34 | 0.20|1.00 | -8.82|-8.73|-7.93 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |

### O6_OR15m_stp_le1

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | O6_OR15m_stp_le1 | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 179 | -9.17 [-15.60,-2.73] (9.19) | 72 | -4.51 [-13.98,+4.97] (13.53) | +2.95 (11.94) | -4,375|-2,028 | +11.08|-20.24 | 104 (58%) | 42%|35% | -0.77 | 0.64>0.37 | 0.05|0.05 | -9.66|-9.58|-9.01 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | O6_OR15m_stp_le1 | L5e_x20_w300_t0.7 | efficiency against: below -20 and directional ER(300s)>=0.7 against | 179 | +0.00 [+0.00,+0.00] (0.00) | 72 | +0.00 [+0.00,+0.00] (0.00) | +0.00 (0.00) | 0|0 | +0.00|+0.00 | 0 (0%) | 0%|0% | +0.00 | 0.64>0.64 | 0.00|0.00 | +0.00|+0.00|+0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | O6_OR15m_stp_le1 | L2_x5_t30 | cut after 30 cumulative min below -5 | 179 | -2.27 [-6.02,+1.48] (5.36) | 72 | +3.13 [-1.32,+7.58] (6.36) | -1.57 (8.27) | -1,084|1,410 | +4.40|-6.67 | 42 (23%) | 31%|17% | -0.24 | 0.64>0.54 | 0.10|1.00 | -2.39|-2.42|-2.26 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |

### O6_OR30m_stp_ge0.5

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | O6_OR30m_stp_ge0.5 | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 297 | -6.94 [-11.87,-2.01] (7.04) | 125 | -5.05 [-12.74,+2.63] (10.98) | +2.09 (9.21) | -5,495|-3,948 | +11.68|-18.62 | 166 (56%) | 42%|35% | -0.67 | 0.64>0.40 | 0.20|0.45 | -7.34|-7.34|-6.85 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | O6_OR30m_stp_ge0.5 | L5e_x20_w300_t0.7 | efficiency against: below -20 and directional ER(300s)>=0.7 against | 297 | +0.00 [+0.00,+0.00] (0.00) | 125 | +0.00 [+0.00,+0.00] (0.00) | +0.00 (0.00) | 0|0 | +0.00|+0.00 | 0 (0%) | 0%|0% | +0.00 | 0.64>0.64 | 0.00|0.00 | +0.00|+0.00|+0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | O6_OR30m_stp_ge0.5 | L4_x10_n600 | stall under water: below -10, no new MAE and recovery <= 2 pts for 600s | 297 | -4.20 [-7.29,-1.10] (4.42) | 125 | +1.10 [-2.41,+4.60] (5.00) | +1.76 (5.71) | -3,323|856 | +3.63|-7.82 | 72 (24%) | 36%|20% | -0.27 | 0.64>0.54 | 0.00|0.95 | -4.36|-4.36|-4.02 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |

### PB

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | PB | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 2261 | +0.10 [-1.75,+1.94] (2.63) | 965 | -1.38 [-4.07,+1.31] (3.84) | +0.03 (4.28) | 575|-8,321 | +17.13|-17.04 | 1556 (69%) | 31%|33% | -0.94 | 0.50>0.28 | 0.15|0.50 | -0.40|-0.39|+0.37 | DEAD | holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | PB | L3_m20_y50_n60 | MAE>=20: cut if recovery < 50% of MAE 60s after the MAE | 2261 | +2.07 [+0.24,+3.90] (2.61) | 965 | -2.16 [-4.93,+0.61] (3.96) | -1.47 (4.36) | 12,472|-13,032 | +18.12|-16.05 | 1529 (68%) | 30%|35% | -0.93 | 0.50>0.29 | 1.00|0.10 | +1.59|+1.59|+2.19 | DEAD | holdout_sign_agrees,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | PB | L6_a25_r3_w10 | live TH loss grid: adverse 25, 3 of 3, window 10s | 2261 | +1.13 [-0.28,+2.55] (2.02) | 965 | +0.87 [-1.18,+2.92] (2.93) | -1.10 (3.24) | 6,843|5,265 | +10.67|-9.54 | 1146 (51%) | 20%|21% | -0.66 | 0.50>0.39 | 0.70|1.00 | +0.88|+0.77|+1.34 | DEAD | placebo>=0.90,paired_CI_excludes0,year_share>60%,SPAN2<=0,RC_p>0.05 |

### PE

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | PE | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 1732 | -0.84 [-2.95,+1.28] (3.02) | 731 | -2.28 [-5.49,+0.93] (4.59) | +0.02 (4.19) | -2,163|-5,417 | +16.73|-17.57 | 1186 (68%) | 32%|34% | -0.92 | 0.53>0.30 | 0.50|0.40 | -1.32|-1.33|-0.54 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | PE | L2_x20_t60 | cut after 60 cumulative min below -20 | 1732 | +0.52 [-0.40,+1.43] (1.31) | 731 | +0.77 [-0.49,+2.03] (1.80) | +0.59 (2.25) | 849|1,828 | +3.65|-3.13 | 316 (18%) | 18%|16% | -0.20 | 0.53>0.49 | 1.00|1.00 | +0.45|+0.39|+0.57 | DEAD | paired_CI_excludes0,maxDD_not_worse,RC_p>0.05 |
| best HOLDOUT | PE | L2_x20_t60 | cut after 60 cumulative min below -20 | 1732 | +0.52 [-0.40,+1.43] (1.31) | 731 | +0.77 [-0.49,+2.03] (1.80) | +0.59 (2.25) | 849|1,828 | +3.65|-3.13 | 316 (18%) | 18%|16% | -0.20 | 0.53>0.49 | 1.00|1.00 | +0.45|+0.39|+0.57 | DEAD | paired_CI_excludes0,maxDD_not_worse,RC_p>0.05 |

### SM

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | SM | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 774 | -2.40 [-5.62,+0.81] (4.60) | 294 | +1.18 [-3.52,+5.87] (6.70) | +0.54 (6.05) | -3,838|2,091 | +16.10|-18.51 | 520 (67%) | 35%|30% | -0.87 | 0.55>0.30 | 0.20|0.65 | -2.88|-2.89|-2.18 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | SM | L5e_x20_w300_t0.7 | efficiency against: below -20 and directional ER(300s)>=0.7 against | 774 | +0.00 [+0.00,+0.00] (0.00) | 294 | +0.00 [+0.00,+0.00] (0.00) | +0.00 (0.00) | 0|0 | +0.00|+0.00 | 0 (0%) | 0%|0% | +0.00 | 0.55>0.55 | 0.00|0.00 | +0.00|+0.00|+0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | SM | L2_x20_t5 | cut after 5 cumulative min below -20 | 774 | -2.04 [-4.81,+0.72] (3.95) | 294 | +3.16 [-0.74,+7.06] (5.57) | +2.35 (5.13) | -2,946|4,800 | +11.53|-13.57 | 423 (55%) | 28%|21% | -0.68 | 0.55>0.38 | 0.10|1.00 | -2.36|-2.44|-1.97 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |

### ST

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | ST | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 1717 | -0.98 [-3.07,+1.10] (2.98) | 765 | -0.32 [-3.55,+2.91] (4.61) | +0.27 (4.29) | -4,501|-1,546 | +16.55|-17.53 | 1176 (68%) | 31%|31% | -0.93 | 0.52>0.30 | 0.25|0.20 | -1.47|-1.47|-0.79 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | ST | L5e_x20_w120_t0.5 | efficiency against: below -20 and directional ER(120s)>=0.5 against | 1717 | -0.01 [-0.66,+0.63] (0.92) | 765 | +0.21 [-0.63,+1.05] (1.20) | -0.21 (1.22) | -60|1,014 | +1.45|-1.47 | 110 (6%) | 26%|23% | -0.07 | 0.52>0.51 | 0.35|0.90 | -0.04|-0.06|+0.02 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | ST | L1_x40 | market cut when unrealised <= -40 | 1717 | -0.86 [-2.43,+0.71] (2.24) | 765 | +1.89 [-0.22,+4.00] (3.02) | -1.06 (3.31) | -3,918|9,030 | +8.99|-9.84 | 958 (56%) | 17%|13% | -0.71 | 0.52>0.42 | 0.35|1.00 | -1.08|-1.26|-0.50 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,SPAN2<=0,NOTC<=0,RC_p>0.05 |

### WT

| role | stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LIVE TH loss | WT | L6_a15_r3_w30 | live TH loss grid: adverse 15, 3 of 3, window 30s | 2567 | -0.77 [-1.78,+0.24] (1.44) | 1099 | -0.86 [-2.42,+0.71] (2.24) | +0.01 (2.15) | -3,690|-4,111 | +8.77|-9.54 | 1423 (55%) | 34%|35% | -0.75 | 0.59>0.40 | 0.00|0.00 | -1.16|-1.18|-0.58 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| best IN-SAMPLE | WT | L4_x30_n120 | stall under water: below -30, no new MAE and recovery <= 2 pts for 120s | 2567 | +0.08 [-0.52,+0.68] (0.85) | 1099 | -0.56 [-1.54,+0.43] (1.41) | +0.90 (1.23) | 386|-2,684 | +3.16|-3.08 | 803 (31%) | 15%|18% | -0.38 | 0.59>0.54 | 0.80|0.15 | -0.02|-0.15|+0.21 | DEAD | holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0,maxDD_not_worse,NOTC<=0,RC_p>0.05 |
| best HOLDOUT | WT | L6_a20_r3_w10 | live TH loss grid: adverse 20, 3 of 3, window 10s | 2567 | -0.09 [-0.83,+0.65] (1.05) | 1099 | +0.43 [-0.70,+1.56] (1.62) | +0.17 (1.57) | -431|2,075 | +4.90|-4.99 | 895 (35%) | 25%|24% | -0.47 | 0.59>0.50 | 0.50|0.95 | -0.28|-0.35|+0.06 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |

## 6. Top 10 cells by IN-SAMPLE delta (n_PRE >= 100) and top 10 by HOLDOUT delta (n_HOLD >= 50), regardless of verdict, with what killed each

### 6a. Top 10 by IN-SAMPLE (PRE) delta

| stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates | boot CI PRE|HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| O6_LV_RN_BH | L6_a30_r3_w60 | live TH loss grid: adverse 30, 3 of 3, window 60s | 134 | +2.78 [-0.98,+6.54] (5.37) | 78 | +1.32 [-3.99,+6.63] (7.59) | -2.95 (11.48) | 994|643 | +6.54|-3.75 | 43 (32%) | 9%|15% | -0.37 | 0.62>0.57 | 0.95|0.50 | +2.71|+2.55|+3.14 | DEAD | neighbours_agree,paired_CI_excludes0,maxDD_not_worse,SPAN2<=0,RC_p>0.05 | [-1.12,+6.23]|[-4.44,+6.28] |
| O6_LV_RN_BH | L4_x30_n60 | stall under water: below -30, no new MAE and recovery <= 2 pts for 60s | 134 | +2.29 [-1.11,+5.69] (4.86) | 78 | -0.60 [-6.05,+4.86] (7.79) | -0.50 (10.27) | 819|-291 | +5.43|-3.14 | 38 (28%) | 8%|17% | -0.31 | 0.62>0.58 | 0.95|0.35 | +2.25|+2.09|+2.12 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-1.46,+5.31]|[-6.66,+4.50] |
| O6_LV_RN_BH | L6_a30_r3_w30 | live TH loss grid: adverse 30, 3 of 3, window 30s | 134 | +2.26 [-2.09,+6.61] (6.22) | 78 | +2.22 [-3.87,+8.31] (8.70) | -1.35 (11.50) | 807|1,083 | +7.43|-5.17 | 48 (36%) | 15%|15% | -0.47 | 0.62>0.56 | 1.00|0.80 | +2.11|+2.00|+2.76 | DEAD | neighbours_agree,paired_CI_excludes0,maxDD_not_worse,year_share>60%,SPAN2<=0,RC_p>0.05 | [-1.93,+6.17]|[-4.13,+7.95] |
| PB | L3_m20_y50_n60 | MAE>=20: cut if recovery < 50% of MAE 60s after the MAE | 2261 | +2.07 [+0.24,+3.90] (2.61) | 965 | -2.16 [-4.93,+0.61] (3.96) | -1.47 (4.36) | 12,472|-13,032 | +18.12|-16.05 | 1529 (68%) | 30%|35% | -0.93 | 0.50>0.29 | 1.00|0.10 | +1.59|+1.59|+2.19 | DEAD | holdout_sign_agrees,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [+0.13,+4.00]|[-4.97,+0.55] |
| O6_LV_RN_BH | L6_a30_r3_w120 | live TH loss grid: adverse 30, 3 of 3, window 120s | 134 | +1.99 [-1.37,+5.35] (4.80) | 78 | -0.54 [-5.73,+4.65] (7.42) | -4.68 (10.67) | 712|-262 | +5.07|-3.08 | 34 (25%) | 9%|18% | -0.26 | 0.62>0.58 | 1.00|0.55 | +1.95|+1.81|+2.27 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0,maxDD_not_worse,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-1.67,+4.96]|[-6.38,+4.02] |
| O6_LV_RN_BH | L2_x20_t5 | cut after 5 cumulative min below -20 | 134 | +1.94 [-1.65,+5.54] (5.14) | 78 | -0.45 [-5.50,+4.59] (7.21) | -0.61 (10.83) | 695|-220 | +5.44|-3.50 | 33 (25%) | 12%|24% | -0.26 | 0.62>0.57 | 1.00|0.55 | +1.89|+1.77|+1.99 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-1.87,+5.33]|[-6.43,+4.44] |
| PB | L3_m30_y50_n60 | MAE>=30: cut if recovery < 50% of MAE 60s after the MAE | 2261 | +1.75 [+0.18,+3.31] (2.24) | 965 | -1.97 [-4.39,+0.46] (3.46) | -0.48 (3.77) | 10,530|-11,861 | +13.64|-11.89 | 1307 (58%) | 23%|28% | -0.77 | 0.50>0.36 | 0.95|0.05 | +1.42|+1.33|+1.87 | DEAD | holdout_sign_agrees,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [+0.24,+3.28]|[-4.40,+0.30] |
| PB | L3_m20_y25_n60 | MAE>=20: cut if recovery < 25% of MAE 60s after the MAE | 2261 | +1.56 [-0.20,+3.33] (2.52) | 965 | -2.07 [-4.70,+0.57] (3.76) | -1.20 (4.26) | 9,429|-12,469 | +16.81|-15.24 | 1486 (66%) | 28%|33% | -0.88 | 0.50>0.31 | 0.70|0.10 | +1.14|+1.10|+1.73 | DEAD | holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-0.27,+3.35]|[-4.85,+0.45] |
| PB | L6_a25_r3_w30 | live TH loss grid: adverse 25, 3 of 3, window 30s | 2261 | +1.45 [-0.07,+2.96] (2.17) | 965 | -0.71 [-2.98,+1.55] (3.23) | -0.67 (3.66) | 8,726|-4,306 | +12.75|-11.30 | 1300 (57%) | 22%|24% | -0.75 | 0.50>0.37 | 0.70|0.60 | +1.15|+1.04|+1.65 | DEAD | holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 | [-0.02,+3.04]|[-3.12,+1.48] |
| HM | L6_a30_r3_w10 | live TH loss grid: adverse 30, 3 of 3, window 10s | 1561 | +1.37 [-0.05,+2.79] (2.03) | 698 | +1.82 [-0.10,+3.75] (2.75) | +0.06 (2.92) | 5,690|7,961 | +8.24|-6.87 | 692 (44%) | 15%|12% | -0.53 | 0.52>0.44 | 1.00|0.95 | +1.22|+1.06|+1.45 | DEAD | paired_CI_excludes0,RC_p>0.05 | [-0.05,+2.67]|[-0.15,+3.56] |


### 6b. Top 10 by HOLDOUT delta

| stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates | boot CI PRE|HOLD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| D6_TB4B_ASIA | L6_a10_r3_w60 | live TH loss grid: adverse 10, 3 of 3, window 60s | 450 | -4.50 [-9.38,+0.38] (6.97) | 200 | +6.89 [+0.21,+13.57] (9.54) | +3.44 (9.40) | -5,401|8,610 | +18.39|-22.89 | 326 (72%) | 43%|31% | -1.06 | 0.58>0.26 | 0.00|1.00 | -5.18|-5.04|-4.22 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 | [-9.69,+0.02]|[+0.24,+13.43] |
| D6_TB4B_ASIA | L6_a10_r3_w30 | live TH loss grid: adverse 10, 3 of 3, window 30s | 450 | -3.61 [-8.15,+0.93] (6.48) | 200 | +6.59 [+0.15,+13.02] (9.19) | +3.35 (8.44) | -4,335|8,235 | +16.57|-20.18 | 306 (68%) | 39%|29% | -1.00 | 0.58>0.31 | 0.05|0.95 | -4.21|-4.12|-3.41 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 | [-8.45,+0.53]|[-0.14,+12.95] |
| D6_TB4B_ASIA | L6_a10_r3_w10 | live TH loss grid: adverse 10, 3 of 3, window 10s | 450 | -1.26 [-4.56,+2.03] (4.71) | 200 | +6.46 [+1.87,+11.05] (6.56) | +1.41 (5.67) | -1,518|8,073 | +9.61|-10.87 | 195 (43%) | 32%|19% | -0.64 | 0.58>0.44 | 0.45|1.00 | -1.59|-1.59|-1.34 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 | [-4.52,+1.91]|[+2.11,+10.74] |
| D6_TB4B_ASIA | L3_m10_y50_n60 | MAE>=10: cut if recovery < 50% of MAE 60s after the MAE | 450 | -4.33 [-9.48,+0.83] (7.36) | 200 | +6.31 [-0.95,+13.57] (10.37) | +1.00 (10.63) | -5,193|7,886 | +20.71|-25.04 | 354 (79%) | 46%|36% | -1.18 | 0.58>0.21 | 0.10|0.90 | -5.13|-4.91|-4.22 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 | [-9.48,+0.41]|[-0.85,+13.48] |
| D6_TB4B_ASIA | L5v_x10_w120_p6 | velocity against: below -10 and 6 pts adverse over 120s | 450 | -4.29 [-9.40,+0.82] (7.30) | 200 | +6.27 [-0.74,+13.28] (10.01) | +0.70 (10.28) | -5,147|7,833 | +20.46|-24.75 | 348 (77%) | 45%|36% | -1.17 | 0.58>0.22 | 0.20|0.75 | -5.07|-4.86|-3.97 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 | [-9.59,+0.32]|[-0.63,+13.17] |
| D6_TB4B_ASIA | L6_a10_r1_w10 | live TH loss grid: adverse 10, 1 of 3, window 10s | 450 | -4.54 [-9.71,+0.62] (7.38) | 200 | +6.14 [-1.13,+13.41] (10.39) | +0.56 (10.61) | -5,452|7,680 | +21.42|-25.96 | 363 (81%) | 47%|38% | -1.24 | 0.58>0.20 | 0.85|0.85 | -5.40|-5.14|-4.39 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 | [-9.86,+0.25]|[-1.13,+13.29] |
| D6_TB4B_ASIA | L2_x5_t5 | cut after 5 cumulative min below -5 | 450 | -4.11 [-9.09,+0.86] (7.11) | 200 | +6.08 [-1.13,+13.28] (10.30) | +1.37 (10.57) | -4,937|7,596 | +20.18|-24.30 | 345 (77%) | 46%|36% | -1.12 | 0.58>0.22 | 0.45|0.45 | -4.86|-4.68|-3.85 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 | [-8.99,+0.43]|[-1.14,+13.23] |
| D6_TB4B_ASIA | L6_a10_r2_w120 | live TH loss grid: adverse 10, 2 of 3, window 120s | 450 | -4.75 [-9.94,+0.44] (7.41) | 200 | +6.03 [-1.21,+13.27] (10.34) | +0.72 (10.54) | -5,703|7,536 | +21.20|-25.96 | 361 (80%) | 47%|38% | -1.23 | 0.58>0.20 | 0.10|0.65 | -5.60|-5.35|-4.49 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 | [-10.11,+0.03]|[-1.14,+13.18] |
| D6_TB4B_ASIA | L6_a10_r1_w120 | live TH loss grid: adverse 10, 1 of 3, window 120s | 450 | -4.58 [-9.78,+0.62] (7.43) | 200 | +6.03 [-1.21,+13.26] (10.33) | +0.48 (10.62) | -5,497|7,531 | +21.32|-25.90 | 361 (80%) | 47%|38% | -1.23 | 0.58>0.21 | 0.45|0.50 | -5.43|-5.17|-4.46 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 | [-9.84,+0.23]|[-1.11,+13.14] |
| D6_TB4B_ASIA | L6_a10_r1_w30 | live TH loss grid: adverse 10, 1 of 3, window 30s | 450 | -4.34 [-9.53,+0.85] (7.42) | 200 | +6.00 [-1.28,+13.28] (10.40) | +0.50 (10.62) | -5,209|7,497 | +21.46|-25.80 | 362 (80%) | 47%|38% | -1.23 | 0.58>0.20 | 0.90|0.05 | -5.19|-4.94|-4.31 | DEAD | mean_up,placebo<0.95,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 | [-9.63,+0.44]|[-1.31,+13.27] |


### 6c. Pooled over the 11 intraday books: top 10 rules by IN-SAMPLE delta

| stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 11 BOOKS | L5e_x10_w300_t0.7 | efficiency against: below -10 and directional ER(300s)>=0.7 against | 18121 | -0.03 [-0.09,+0.03] (0.09) | 7747 | +0.00 [+0.00,+0.00] (0.00) | +0.01 (0.03) | -1,251|0 | +0.00|-0.03 | 7 (0%) | 100%|0% | -0.00 | 0.54>0.54 | 0.00|0.50 | -0.03|-0.03|-0.03 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | L5e_x20_w300_t0.7 | efficiency against: below -20 and directional ER(300s)>=0.7 against | 18121 | -0.03 [-0.09,+0.03] (0.09) | 7747 | +0.00 [+0.00,+0.00] (0.00) | +0.01 (0.03) | -1,254|0 | +0.00|-0.03 | 7 (0%) | 100%|0% | -0.00 | 0.54>0.54 | 0.00|0.47 | -0.03|-0.03|-0.03 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | L2_x10_t60 | cut after 60 cumulative min below -10 | 18121 | -0.04 [-0.62,+0.55] (0.83) | 7747 | -0.40 [-1.26,+0.46] (1.23) | +0.52 (1.39) | -2,679|-11,174 | +5.42|-5.45 | 4539 (25%) | 27%|28% | -0.29 | 0.54>0.47 | 0.80|0.10 | -0.17|-0.21|+0.02 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | L5e_x10_w300_t0.5 | efficiency against: below -10 and directional ER(300s)>=0.5 against | 18121 | -0.04 [-0.12,+0.04] (0.12) | 7747 | +0.01 [-0.01,+0.02] (0.02) | +0.02 (0.04) | -1,511|388 | +0.02|-0.06 | 22 (0%) | 64%|14% | -0.00 | 0.54>0.54 | 0.00|0.90 | -0.04|-0.04|-0.04 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | L5e_x20_w300_t0.5 | efficiency against: below -20 and directional ER(300s)>=0.5 against | 18121 | -0.05 [-0.12,+0.03] (0.11) | 7747 | +0.01 [-0.01,+0.02] (0.02) | +0.01 (0.03) | -1,938|388 | +0.01|-0.05 | 15 (0%) | 80%|14% | -0.00 | 0.54>0.54 | 0.00|0.90 | -0.05|-0.05|-0.05 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | L2_x5_t60 | cut after 60 cumulative min below -5 | 18121 | -0.10 [-0.77,+0.56] (0.95) | 7747 | -0.53 [-1.52,+0.47] (1.42) | +0.25 (1.56) | -5,558|-15,856 | +6.85|-6.95 | 5469 (30%) | 30%|31% | -0.36 | 0.54>0.44 | 0.90|0.10 | -0.29|-0.31|-0.03 | DEAD | mean_up,holdout_sign_agrees,placebo<0.95,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | L2_x20_t60 | cut after 60 cumulative min below -20 | 18121 | -0.12 [-0.53,+0.30] (0.59) | 7747 | +0.16 [-0.43,+0.74] (0.84) | +0.29 (1.06) | -5,539|8,828 | +2.85|-2.96 | 2738 (15%) | 22%|20% | -0.17 | 0.54>0.50 | 0.15|1.00 | -0.18|-0.22|-0.08 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | L5e_x20_w120_t0.7 | efficiency against: below -20 and directional ER(120s)>=0.7 against | 18121 | -0.12 [-0.28,+0.03] (0.22) | 7747 | +0.01 [-0.26,+0.29] (0.39) | -0.15 (0.39) | -5,171|1,655 | +0.22|-0.34 | 215 (1%) | 33%|26% | -0.01 | 0.54>0.53 | 0.00|0.70 | -0.13|-0.13|-0.12 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | L8_p40 | half cut at -40, rest to bracket | 18121 | -0.14 [-0.46,+0.19] (0.47) | 7747 | -0.12 [-0.63,+0.40] (0.74) | +0.21 (0.70) | -4,181|-4,209 | +3.96|-4.09 | 9581 (53%) | 15%|16% | -0.33 | 0.54>0.53 | 0.10|0.60 | -0.23|-0.33|-0.02 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | L5e_x10_w120_t0.7 | efficiency against: below -10 and directional ER(120s)>=0.7 against | 18121 | -0.14 [-0.35,+0.07] (0.30) | 7747 | +0.19 [-0.13,+0.50] (0.45) | -0.26 (0.52) | -5,939|9,694 | +0.51|-0.65 | 425 (2%) | 36%|25% | -0.02 | 0.54>0.53 | 0.00|1.00 | -0.15|-0.16|-0.13 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |


### 6d. Pooled over the 11 intraday books: top 10 rules by HOLDOUT delta

| stream | rule | what | PRE n | PRE d [CI] (MDE) | HOLD n | HOLD d [CI] (MDE) | X d (MDE) | $/wk PRE|HOLD | saved|forfeited PRE | exits added PRE | cut->target (base exit) PRE|HOLD | exit friction chg pts/trade | win base>rule PRE | plc PRE|HOLD | N|MW|C PRE | verdict | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 11 BOOKS | L5e_x10_w120_t0.7 | efficiency against: below -10 and directional ER(120s)>=0.7 against | 18121 | -0.14 [-0.35,+0.07] (0.30) | 7747 | +0.19 [-0.13,+0.50] (0.45) | -0.26 (0.52) | -5,939|9,694 | +0.51|-0.65 | 425 (2%) | 36%|25% | -0.02 | 0.54>0.53 | 0.00|1.00 | -0.15|-0.16|-0.13 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | L2_x20_t60 | cut after 60 cumulative min below -20 | 18121 | -0.12 [-0.53,+0.30] (0.59) | 7747 | +0.16 [-0.43,+0.74] (0.84) | +0.29 (1.06) | -5,539|8,828 | +2.85|-2.96 | 2738 (15%) | 22%|20% | -0.17 | 0.54>0.50 | 0.15|1.00 | -0.18|-0.22|-0.08 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | L6_a30_r3_w10 | live TH loss grid: adverse 30, 3 of 3, window 10s | 18121 | -0.23 [-0.90,+0.45] (0.96) | 7747 | +0.15 [-0.84,+1.13] (1.41) | +0.49 (1.36) | -6,593|11,172 | +7.14|-7.37 | 7450 (41%) | 18%|18% | -0.52 | 0.54>0.45 | 0.60|0.95 | -0.40|-0.52|-0.11 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | L5e_x20_w120_t0.5 | efficiency against: below -20 and directional ER(120s)>=0.5 against | 18121 | -0.16 [-0.45,+0.12] (0.41) | 7747 | +0.15 [-0.31,+0.60] (0.65) | +0.01 (0.60) | -7,066|8,880 | +1.01|-1.17 | 884 (5%) | 29%|24% | -0.06 | 0.54>0.52 | 0.00|1.00 | -0.19|-0.20|-0.14 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | L6_a20_r3_w10 | live TH loss grid: adverse 20, 3 of 3, window 10s | 18121 | -0.56 [-1.41,+0.28] (1.21) | 7747 | +0.14 [-1.07,+1.34] (1.72) | +0.66 (1.70) | -21,748|10,139 | +10.45|-11.01 | 9086 (50%) | 26%|24% | -0.66 | 0.54>0.40 | 0.05|1.00 | -0.86|-0.92|-0.38 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | L5e_x10_w120_t0.5 | efficiency against: below -10 and directional ER(120s)>=0.5 against | 18121 | -0.44 [-0.84,-0.04] (0.57) | 7747 | +0.13 [-0.44,+0.71] (0.82) | +0.01 (0.86) | -19,468|9,252 | +1.90|-2.34 | 1515 (8%) | 38%|32% | -0.10 | 0.54>0.50 | 0.00|1.00 | -0.50|-0.50|-0.41 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | L6_a25_r3_w10 | live TH loss grid: adverse 25, 3 of 3, window 10s | 18121 | -0.38 [-1.15,+0.39] (1.10) | 7747 | +0.09 [-1.03,+1.20] (1.59) | +0.55 (1.52) | -13,233|7,752 | +8.80|-9.18 | 8270 (46%) | 22%|21% | -0.59 | 0.54>0.43 | 0.25|0.80 | -0.61|-0.70|-0.22 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | L5e_x20_w120_t0.7 | efficiency against: below -20 and directional ER(120s)>=0.7 against | 18121 | -0.12 [-0.28,+0.03] (0.22) | 7747 | +0.01 [-0.26,+0.29] (0.39) | -0.15 (0.39) | -5,171|1,655 | +0.22|-0.34 | 215 (1%) | 33%|26% | -0.01 | 0.54>0.53 | 0.00|0.70 | -0.13|-0.13|-0.12 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | L5e_x10_w300_t0.5 | efficiency against: below -10 and directional ER(300s)>=0.5 against | 18121 | -0.04 [-0.12,+0.04] (0.12) | 7747 | +0.01 [-0.01,+0.02] (0.02) | +0.02 (0.04) | -1,511|388 | +0.02|-0.06 | 22 (0%) | 64%|14% | -0.00 | 0.54>0.54 | 0.00|0.90 | -0.04|-0.04|-0.04 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| 11 BOOKS | L5e_x20_w300_t0.5 | efficiency against: below -20 and directional ER(300s)>=0.5 against | 18121 | -0.05 [-0.12,+0.03] (0.11) | 7747 | +0.01 [-0.01,+0.02] (0.02) | +0.01 (0.03) | -1,938|388 | +0.01|-0.05 | 15 (0%) | 80%|14% | -0.00 | 0.54>0.54 | 0.00|0.90 | -0.05|-0.05|-0.05 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |


### 6e. How the cells died (count of cells failing each gate, all 3476 cells)

| gate | cells failing |
|---|---|
| RC_p>0.05 | 3476 |
| paired_CI_excludes0 | 3471 |
| NOTC<=0 | 3350 |
| placebo>=0.90 | 3262 |
| mean_up | 3031 |
| 2x_cost<=0 | 2911 |
| holdout_sign_agrees | 2174 |
| SPAN2<=0 | 1691 |
| maxDD_not_worse | 1072 |
| neighbours_agree | 535 |
| year_share>60% | 396 |
| n_PRE<100 | 158 |
| placebo<0.95 | 81 |
| neighbours_agree(no grid) | 66 |


## 7. By ENTRY session (pooled over the six stack books) for the LIVE control, the best-in-sample and the best-holdout pooled rule

**L6_a15_r3_w30** - live TH loss grid: adverse 15, 3 of 3, window 30s

| win | key | n | delta | MDE | usd_wk |
|---|---|---|---|---|---|
| PRE | ASIA | 3832 | -1.36 | 2.64 | -9,802 |
| PRE | LONDON | 2627 | -0.18 | 3.30 | -693 |
| PRE | PRE | 396 | -3.34 | 8.09 | -3,210 |
| PRE | NY-AM | 1941 | -1.18 | 3.64 | -3,125 |
| PRE | NY-PM | 1400 | -0.74 | 3.59 | -1,300 |
| PRE | CLOSE | 9 | +0.00 | 0.00 | 0 |
| HOLD | ASIA | 1789 | -0.81 | 4.34 | -3,489 |
| HOLD | LONDON | 1051 | -2.51 | 5.12 | -10,691 |
| HOLD | PRE | 119 | +7.42 | 12.21 | 4,195 |
| HOLD | NY-AM | 865 | -1.36 | 5.43 | -3,464 |
| HOLD | NY-PM | 515 | -0.83 | 5.71 | -2,792 |
| X | ASIA | 1375 | +2.16 | 3.86 | 10,011 |
| X | LONDON | 914 | -0.56 | 5.30 | -1,843 |
| X | PRE | 208 | +0.40 | 10.76 | 1,090 |
| X | NY-AM | 1172 | -0.27 | 4.83 | -576 |
| X | NY-PM | 849 | -0.27 | 4.65 | -1,552 |

**L5e_x10_w300_t0.7** - efficiency against: below -10 and directional ER(300s)>=0.7 against

| win | key | n | delta | MDE | usd_wk |
|---|---|---|---|---|---|
| PRE | ASIA | 3832 | -0.11 | 0.30 | -798 |
| PRE | LONDON | 2627 | +0.00 | 0.00 | 0 |
| PRE | PRE | 396 | +0.00 | 0.00 | 0 |
| PRE | NY-AM | 1941 | +0.00 | 0.00 | 0 |
| PRE | NY-PM | 1400 | +0.00 | 0.00 | 0 |
| PRE | CLOSE | 9 | +0.00 | 0.00 | 0 |
| HOLD | ASIA | 1789 | +0.00 | 0.00 | 0 |
| HOLD | LONDON | 1051 | +0.00 | 0.00 | 0 |
| HOLD | PRE | 119 | +0.00 | 0.00 | 0 |
| HOLD | NY-AM | 865 | +0.00 | 0.00 | 0 |
| HOLD | NY-PM | 515 | +0.00 | 0.00 | 0 |
| X | ASIA | 1375 | +0.05 | 0.10 | 189 |
| X | LONDON | 914 | +0.00 | 0.00 | 0 |
| X | PRE | 208 | +0.00 | 0.00 | 0 |
| X | NY-AM | 1172 | +0.00 | 0.00 | 0 |
| X | NY-PM | 849 | +0.00 | 0.00 | 0 |

**L5e_x10_w120_t0.7** - efficiency against: below -10 and directional ER(120s)>=0.7 against

| win | key | n | delta | MDE | usd_wk |
|---|---|---|---|---|---|
| PRE | ASIA | 3832 | -0.56 | 0.98 | -4,913 |
| PRE | LONDON | 2627 | +0.06 | 0.26 | 375 |
| PRE | PRE | 396 | +0.00 | 0.00 | 0 |
| PRE | NY-AM | 1941 | +0.00 | 0.00 | 0 |
| PRE | NY-PM | 1400 | +0.00 | 0.00 | 0 |
| PRE | CLOSE | 9 | +0.00 | 0.00 | 0 |
| HOLD | ASIA | 1789 | +0.05 | 1.21 | 1,310 |
| HOLD | LONDON | 1051 | +0.10 | 0.21 | 443 |
| HOLD | PRE | 119 | +0.00 | 0.00 | 0 |
| HOLD | NY-AM | 865 | +0.00 | 0.00 | 0 |
| HOLD | NY-PM | 515 | +0.00 | 0.00 | 0 |
| X | ASIA | 1375 | -1.38 | 1.97 | -7,473 |
| X | LONDON | 914 | +0.02 | 0.04 | 37 |
| X | PRE | 208 | +0.00 | 0.00 | 0 |
| X | NY-AM | 1172 | +0.00 | 0.00 | 0 |
| X | NY-PM | 849 | +0.00 | 0.00 | 0 |


## 8. By calendar year (pooled over the six stack books; 2023 = X span only from April, 2024 mixes X and PRE, 2026 = January to 6 February)

**L6_a15_r3_w30**

| win | key | n | delta | MDE | usd_wk |
|---|---|---|---|---|---|
| PRE | 2024 | 6040 | -0.67 | 2.07 | -7,066 |
| PRE | 2025 | 4165 | -1.51 | 2.48 | -11,064 |
| HOLD | 2025 | 3474 | -1.03 | 2.76 | -12,941 |
| HOLD | 2026 | 869 | -1.39 | 6.34 | -3,301 |
| X | 2023 | 3988 | +0.42 | 2.42 | 5,213 |
| X | 2024 | 533 | +0.62 | 6.28 | 1,916 |

**L5e_x10_w300_t0.7**

| win | key | n | delta | MDE | usd_wk |
|---|---|---|---|---|---|
| PRE | 2024 | 6040 | -0.07 | 0.19 | -798 |
| PRE | 2025 | 4165 | +0.00 | 0.00 | 0 |
| HOLD | 2025 | 3474 | +0.00 | 0.00 | 0 |
| HOLD | 2026 | 869 | +0.00 | 0.00 | 0 |
| X | 2023 | 3988 | +0.02 | 0.03 | 189 |
| X | 2024 | 533 | +0.00 | 0.00 | 0 |

**L5e_x10_w120_t0.7**

| win | key | n | delta | MDE | usd_wk |
|---|---|---|---|---|---|
| PRE | 2024 | 6040 | -0.30 | 0.60 | -4,295 |
| PRE | 2025 | 4165 | -0.04 | 0.28 | -244 |
| HOLD | 2025 | 3474 | -0.04 | 0.60 | 44 |
| HOLD | 2026 | 869 | +0.39 | 0.73 | 1,710 |
| X | 2023 | 3988 | -0.43 | 0.66 | -6,861 |
| X | 2024 | 533 | -0.29 | 1.19 | -574 |


Full per-book, per-session, per-year tables for all 158 rules: splits_B.parquet (columns stream, rule, win, split, key, n, mean, mde, usd_wk).


### 6f. One line per book: best rule IN-SAMPLE and best rule HOLDOUT (one row per stream, duplicates removed) with the gates that killed it

| stream | role | rule | PRE | HOLD | X | verdict | failed |
|---|---|---|---|---|---|---|---|
| B3_NQ | best PRE | L5e_x10_w120_t0.5 | +32.71 (42.94) | +6.11 (50.02) | -15.91 | DEAD | year_share>60%,SPAN2<=0,RC_p>0.05,n_PRE<100 |
| B3_NQ | best HOLD | L5e_x10_w120_t0.5 | +32.71 (42.94) | +6.11 (50.02) | -15.91 | DEAD | year_share>60%,SPAN2<=0,RC_p>0.05,n_PRE<100 |
| CR | best PRE | L2_x5_t5 | +0.29 (0.82) | +0.58 (1.36) | -0.37 | DEAD | neighbours_agree,paired_CI_excludes0,year_share>60%,SPAN2<=0,RC_p>0.05 |
| CR | best HOLD | L6_a10_r1_w120 | -0.05 (1.53) | +1.38 (2.12) | -0.24 | DEAD | mean_up,placebo>=0.90,neighbours_agree,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_HM_t75_s90_NYAM | best PRE | L5e_x20_w300_t0.7 | +0.00 (0.00) | +0.00 (0.00) | +0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_HM_t75_s90_NYAM | best HOLD | L6_a20_r3_w10 | -6.65 (8.69) | +3.35 (11.08) | -8.76 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_KB_t60_s75_ASIA | best PRE | L5e_x20_w300_t0.7 | -0.14 (0.38) | +0.00 (0.00) | -0.03 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_KB_t60_s75_ASIA | best HOLD | L5e_x10_w120_t0.7 | -0.98 (2.09) | +0.22 (2.68) | -0.25 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_PB7_PB5_ASIA | best PRE | L5e_x10_w300_t0.5 | +0.15 (0.41) | +0.00 (0.00) | +0.00 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_PB7_PB5_ASIA | best HOLD | L3_m30_y25_n900 | -2.42 (5.01) | +3.29 (5.42) | +0.47 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| D6_SM_t60_sst_ASIA | best PRE | L2_x10_t60 | +1.11 (1.82) | +0.40 (3.89) | -0.47 | DEAD | paired_CI_excludes0,SPAN2<=0,RC_p>0.05 |
| D6_SM_t60_sst_ASIA | best HOLD | L5v_x10_w120_p10 | -1.18 (5.21) | +3.06 (6.58) | -1.54 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_TB4B_ASIA | best PRE | L5e_x20_w300_t0.7 | +0.00 (0.00) | +0.00 (0.00) | +0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| D6_TB4B_ASIA | best HOLD | L6_a10_r3_w60 | -4.50 (6.97) | +6.89 (9.54) | +3.44 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| D6_TB4W_03_ASIA | best PRE | L6_a30_r3_w30 | +0.48 (3.20) | +2.34 (4.75) | +1.13 | DEAD | placebo<0.95,neighbours_agree,paired_CI_excludes0,year_share>60%,RC_p>0.05 |
| D6_TB4W_03_ASIA | best HOLD | L3_m30_y25_n900 | -0.97 (3.28) | +3.25 (3.59) | +1.00 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |
| DN | best PRE | L2_x5_t5 | +0.22 (2.97) | -2.21 (4.46) | -0.90 | DEAD | holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| DN | best HOLD | L5e_x10_w120_t0.5 | -0.40 (0.91) | +0.51 (1.35) | +0.08 | DEAD | mean_up,placebo>=0.90,neighbours_agree,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| EM | best PRE | L3_m30_y50_n300 | +0.79 (3.19) | +2.02 (5.04) | +0.01 | DEAD | placebo>=0.90,paired_CI_excludes0,year_share>60%,RC_p>0.05 |
| EM | best HOLD | L4_x30_n300 | +0.25 (2.40) | +2.75 (3.33) | -0.24 | DEAD | placebo>=0.90,neighbours_agree,paired_CI_excludes0,year_share>60%,SPAN2<=0,RC_p>0.05 |
| HM | best PRE | L6_a30_r3_w10 | +1.37 (2.03) | +1.82 (2.75) | +0.06 | DEAD | paired_CI_excludes0,RC_p>0.05 |
| HM | best HOLD | L6_a25_r2_w10 | +0.31 (3.12) | +2.66 (4.43) | +0.85 | DEAD | placebo>=0.90,paired_CI_excludes0,NOTC<=0,RC_p>0.05 |
| KB | best PRE | L2_x5_t60 | +0.44 (1.90) | -1.98 (3.14) | +0.40 | DEAD | holdout_sign_agrees,neighbours_agree,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| KB | best HOLD | L5e_x10_w120_t0.7 | -0.21 (0.65) | +0.17 (0.86) | -0.34 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| MA | best PRE | L5e_x20_w120_t0.5 | +0.26 (1.09) | +0.43 (1.53) | +0.78 | DEAD | neighbours_agree,paired_CI_excludes0,year_share>60%,RC_p>0.05 |
| MA | best HOLD | L4_x30_n300 | -0.61 (2.40) | +0.96 (3.44) | -0.15 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| MV | best PRE | L5e_x20_w300_t0.7 | -0.05 (0.13) | +0.00 (0.00) | +0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| MV | best HOLD | L6_a20_r3_w60 | -1.91 (2.58) | +1.60 (3.69) | +1.98 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| O6_LV_RN_BH | best PRE | L6_a30_r3_w60 | +2.78 (5.37) | +1.32 (7.59) | -2.95 | DEAD | neighbours_agree,paired_CI_excludes0,maxDD_not_worse,SPAN2<=0,RC_p>0.05 |
| O6_LV_RN_BH | best HOLD | L5v_x20_w120_p6 | -8.26 (11.50) | +5.25 (11.69) | +1.66 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| O6_OR15m_stp_le1 | best PRE | L5e_x20_w300_t0.7 | +0.00 (0.00) | +0.00 (0.00) | +0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| O6_OR15m_stp_le1 | best HOLD | L2_x5_t30 | -2.27 (5.36) | +3.13 (6.36) | -1.57 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,maxDD_not_worse,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| O6_OR30m_stp_ge0.5 | best PRE | L5e_x20_w300_t0.7 | +0.00 (0.00) | +0.00 (0.00) | +0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| O6_OR30m_stp_ge0.5 | best HOLD | L4_x10_n600 | -4.20 (4.42) | +1.10 (5.00) | +1.76 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| PB | best PRE | L3_m20_y50_n60 | +2.07 (2.61) | -2.16 (3.96) | -1.47 | DEAD | holdout_sign_agrees,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| PB | best HOLD | L6_a25_r3_w10 | +1.13 (2.02) | +0.87 (2.93) | -1.10 | DEAD | placebo>=0.90,paired_CI_excludes0,year_share>60%,SPAN2<=0,RC_p>0.05 |
| PE | best PRE | L2_x20_t60 | +0.52 (1.31) | +0.77 (1.80) | +0.59 | DEAD | paired_CI_excludes0,maxDD_not_worse,RC_p>0.05 |
| PE | best HOLD | L2_x20_t60 | +0.52 (1.31) | +0.77 (1.80) | +0.59 | DEAD | paired_CI_excludes0,maxDD_not_worse,RC_p>0.05 |
| SM | best PRE | L5e_x20_w300_t0.7 | +0.00 (0.00) | +0.00 (0.00) | +0.00 | DEAD | mean_up,holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0,2x_cost<=0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| SM | best HOLD | L2_x20_t5 | -2.04 (3.95) | +3.16 (5.57) | +2.35 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,2x_cost<=0,NOTC<=0,RC_p>0.05 |
| ST | best PRE | L5e_x20_w120_t0.5 | -0.01 (0.92) | +0.21 (1.20) | -0.21 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,year_share>60%,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| ST | best HOLD | L1_x40 | -0.86 (2.24) | +1.89 (3.02) | -1.06 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,SPAN2<=0,NOTC<=0,RC_p>0.05 |
| WT | best PRE | L4_x30_n120 | +0.08 (0.85) | -0.56 (1.41) | +0.90 | DEAD | holdout_sign_agrees,placebo>=0.90,neighbours_agree,paired_CI_excludes0,maxDD_not_worse,NOTC<=0,RC_p>0.05 |
| WT | best HOLD | L6_a20_r3_w10 | -0.09 (1.05) | +0.43 (1.62) | +0.17 | DEAD | mean_up,placebo>=0.90,paired_CI_excludes0,year_share>60%,NOTC<=0,RC_p>0.05 |


## 6g. Price-basis sensitivity (pooled over the 11 intraday books, pts/trade): price-basis N / M / MW / C

N = no target correction (limit target filled at the level), M = MEASURED primary, MW = market exits at the live-measured 0.995 pt, C = CONSERVATIVE label. The P9 target correction (about -0.9 pt in 2023-24, -3.7 to -3.8 pts in 2025-26) is applied to every bracket target exit and to nothing else, so a rule that cuts a trade that would have gone on to the target forfeits a target that the correction has already cheapened; the N column removes that.

| rule | N_PRE | M_PRE | MW_PRE | C_PRE | N_HOLD | M_HOLD | MW_HOLD | C_HOLD | cost_per_added_exit_M |
|---|---|---|---|---|---|---|---|---|---|
| L6_a15_r3_w30 | -1.47 | -1.00 | -1.47 | -0.77 | -1.92 | -1.13 | -1.59 | -0.94 | -1.34 |
| L5e_x10_w300_t0.7 | -0.03 | -0.03 | -0.03 | -0.03 | +0.00 | +0.00 | +0.00 | +0.00 | -0.78 |
| L5e_x10_w120_t0.7 | -0.15 | -0.14 | -0.16 | -0.13 | +0.16 | +0.19 | +0.17 | +0.19 | -1.06 |
| L1_x15 | -1.93 | -1.30 | -1.84 | -1.02 | -2.50 | -1.42 | -1.95 | -1.11 | -1.39 |
| L1_x30 | -1.12 | -0.79 | -1.22 | -0.49 | -1.02 | -0.48 | -0.91 | -0.19 | -1.31 |
| L3_m20_y50_n300 | -0.89 | -0.50 | -0.90 | -0.31 | -1.59 | -0.92 | -1.29 | -0.77 | -1.32 |
| L4_x20_n300 | -1.04 | -0.80 | -1.12 | -0.63 | -0.99 | -0.60 | -0.90 | -0.47 | -1.25 |
| L7s_x30 | -1.74 | -1.39 | -1.38 | -1.40 | -1.82 | -1.26 | -1.24 | -1.27 | -0.17 |
| L8_p15 | -0.96 | -0.65 | -0.92 | -0.51 | -1.25 | -0.71 | -0.98 | -0.56 | -0.69 |


Cost of the added exits: a rule market exit costs 0.25 pt (M) / 0.995 pt (MW) / 0.5 pt plus a 3-s delay (C); a trailing or tightened stop exit costs the measured stop walk (0.85 / 1.13 / 1.74 / 1.71 pts for 2023..2026 at 10 lots, +0.5 on C). The last column is the change in friction per ADDED exit relative to the bracket exit it replaces (negative = the added exit is cheaper than the bracket exit it replaces on the MEASURED basis).


### 6i. Live TH-loss delta by book and ENTRY session, pts/trade (MDE; n), whole sample 2023-04..2026-02-06

| stream | ASIA | LONDON | PRE | NY-AM | NY-PM | CLOSE |
|---|---|---|---|---|---|---|
| B3_NQ | n<5 | n<5 | n<5 | n<5 | n<5 | -27.20 (41.5; n 180) |
| CR | -0.01 (1.1; n 729) | -0.50 (0.9; n 850) | +0.45 (1.4; n 233) | +0.49 (1.8; n 558) | -0.53 (2.6; n 324) | n<5 |
| D6_HM_t75_s90_NYAM | n<5 | n<5 | n<5 | -4.94 (6.2; n 780) | n<5 | n<5 |
| D6_KB_t60_s75_ASIA | -3.46 (4.1; n 1268) | n<5 | n<5 | n<5 | n<5 | n<5 |
| D6_PB7_PB5_ASIA | -2.95 (4.8; n 671) | n<5 | n<5 | n<5 | n<5 | n<5 |
| D6_SM_t60_sst_ASIA | -0.93 (2.9; n 524) | n<5 | n<5 | n<5 | n<5 | n<5 |
| D6_TB4B_ASIA | +0.46 (4.2; n 843) | n<5 | n<5 | n<5 | n<5 | n<5 |
| D6_TB4W_03_ASIA | -0.35 (3.2; n 1419) | n<5 | n<5 | n<5 | n<5 | n<5 |
| DN | -1.60 (4.3; n 833) | -0.74 (4.9; n 682) | -1.84 (9.4; n 186) | -0.96 (3.8; n 980) | +1.12 (4.6; n 540) | +0.97 (14.0; n 51) |
| EM | +1.70 (5.1; n 531) | -2.09 (6.3; n 413) | -2.10 (13.4; n 89) | -2.40 (6.6; n 356) | +1.00 (6.7; n 264) | +4.55 (29.5; n 7) |
| HM | -0.18 (3.6; n 1117) | +0.42 (5.1; n 680) | +2.04 (12.8; n 95) | +1.18 (5.1; n 564) | -0.47 (5.3; n 462) | +0.00 (0.0; n 6) |
| KB | -0.70 (3.5; n 1274) | -1.29 (4.7; n 712) | -3.91 (11.4; n 123) | -1.53 (4.5; n 819) | -2.51 (4.8; n 509) | +0.00 (0.0; n 7) |
| MA | +0.39 (4.8; n 681) | -4.78 (6.4; n 441) | +2.54 (12.8; n 99) | -1.92 (6.0; n 406) | -2.44 (7.1; n 279) | n<5 |
| MV | +0.77 (3.5; n 1144) | -1.62 (4.7; n 763) | +2.96 (7.8; n 252) | -2.36 (4.1; n 958) | -1.01 (5.3; n 510) | n<5 |
| O6_LV_RN_BH | n<5 | n<5 | n<5 | -3.69 (7.2; n 293) | n<5 | n<5 |
| O6_OR15m_stp_le1 | n<5 | n<5 | n<5 | -4.54 (6.5; n 361) | n<5 | n<5 |
| O6_OR30m_stp_ge0.5 | n<5 | n<5 | n<5 | -3.93 (5.0; n 594) | n<5 | n<5 |
| PB | +0.12 (3.6; n 1139) | -1.41 (4.6; n 828) | +3.73 (8.1; n 225) | -1.10 (3.8; n 1043) | +0.29 (4.0; n 804) | +1.18 (34.6; n 10) |
| PE | -0.52 (3.5; n 1193) | -0.20 (4.9; n 721) | +3.87 (10.3; n 138) | -2.50 (4.9; n 689) | -2.27 (5.0; n 507) | n<5 |
| SM | -1.82 (5.5; n 470) | -0.48 (5.9; n 470) | -8.94 (18.0; n 64) | -1.59 (8.0; n 259) | +3.90 (7.5; n 194) | n<5 |
| ST | -0.08 (3.6; n 1198) | -1.52 (5.1; n 695) | -1.24 (10.4; n 146) | +0.24 (4.3; n 794) | -1.46 (5.3; n 401) | n<5 |
| WT | -0.59 (1.7; n 1744) | -1.19 (2.0; n 1314) | +0.95 (5.8; n 157) | -1.45 (2.6; n 853) | +1.13 (2.8; n 691) | n<5 |


### 6j. Live TH-loss delta by book and calendar year, pts/trade (MDE; n); 2023 = Apr-Dec, 2026 = Jan to 6 Feb

| stream | 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|
| B3_NQ | -29.11 (52.2; n 57) | +13.70 (71.4; n 67) | -74.81 (86.0; n 47) | -70.92 (296.4; n 9) |
| CR | -0.23 (0.9; n 697) | -0.35 (1.1; n 953) | +0.23 (1.2; n 958) | +0.70 (4.5; n 86) |
| D6_HM_t75_s90_NYAM | -12.97 (14.2; n 138) | -5.00 (10.8; n 275) | -1.94 (9.6; n 327) | -1.46 (25.2; n 40) |
| D6_KB_t60_s75_ASIA | -1.92 (9.6; n 217) | -3.18 (7.2; n 397) | -3.53 (6.0; n 580) | -8.94 (18.3; n 74) |
| D6_PB7_PB5_ASIA | +2.39 (10.6; n 116) | -3.45 (8.5; n 218) | -5.78 (7.9; n 286) | +2.86 (14.2; n 51) |
| D6_SM_t60_sst_ASIA | -1.31 (3.6; n 125) | -0.66 (3.9; n 187) | -1.09 (6.4; n 188) | +0.28 (13.0; n 24) |
| D6_TB4B_ASIA | +4.43 (8.5; n 170) | -2.27 (7.4; n 274) | -0.03 (6.7; n 363) | +7.33 (20.7; n 36) |
| D6_TB4W_03_ASIA | +1.42 (8.1; n 220) | -1.23 (5.9; n 438) | -0.30 (4.6; n 672) | +0.22 (10.1; n 91) |
| DN | +1.05 (4.7; n 642) | -0.17 (3.5; n 1097) | -0.99 (3.3; n 1387) | -10.77 (10.7; n 146) |
| EM | +0.64 (5.9; n 374) | -2.64 (5.2; n 583) | +1.01 (4.8; n 637) | -0.71 (13.9; n 66) |
| HM | +0.55 (4.9; n 581) | +0.70 (3.8; n 1018) | -0.49 (3.6; n 1206) | +2.42 (12.2; n 119) |
| KB | +1.67 (4.4; n 733) | -1.36 (3.5; n 1178) | -2.77 (3.4; n 1378) | -3.96 (10.8; n 155) |
| MA | -0.00 (6.1; n 410) | -2.93 (4.8; n 666) | -1.08 (4.6; n 751) | -3.66 (14.8; n 79) |
| MV | +1.95 (4.6; n 658) | -2.07 (3.5; n 1282) | -0.97 (3.2; n 1511) | +2.51 (9.0; n 176) |
| O6_LV_RN_BH | +3.18 (14.5; n 73) | -10.67 (13.6; n 96) | -1.92 (10.9; n 111) | -5.98 (25.7; n 13) |
| O6_OR15m_stp_le1 | +2.27 (12.5; n 102) | -8.11 (11.3; n 121) | -6.27 (10.5; n 127) | -8.52 (33.5; n 11) |
| O6_OR30m_stp_ge0.5 | +1.02 (10.1; n 152) | -6.88 (8.9; n 213) | -3.46 (7.7; n 206) | -13.48 (26.3; n 23) |
| PB | -0.43 (4.6; n 725) | +1.37 (3.4; n 1356) | -1.16 (2.9; n 1773) | -2.95 (8.6; n 195) |
| PE | -0.20 (4.4; n 694) | -0.28 (3.7; n 1115) | -1.80 (3.5; n 1292) | -2.19 (11.5; n 147) |
| SM | +1.17 (6.3; n 344) | -2.53 (5.6; n 535) | -1.10 (5.2; n 522) | +3.93 (15.3; n 56) |
| ST | -0.25 (4.6; n 662) | +0.45 (3.7; n 1091) | -1.47 (3.4; n 1341) | -0.60 (12.1; n 140) |
| WT | +0.03 (2.3; n 974) | -1.00 (1.8; n 1636) | -0.31 (1.6; n 1900) | -2.78 (5.1; n 252) |

## 9. Stack level: one rule applied to every stack book at once (ST HM WT KB SM PE), weekly series

Rules shown: the live TH-loss control, the best rule by IN-SAMPLE pooled $/wk (L2_x5_t60: cut after 60 cumulative min below -5) and the best by HOLDOUT pooled $/wk (L6_a20_r3_w10: live TH loss grid: adverse 20, 3 of 3, window 10s; selected on the holdout, labelled, not a candidate). Series = trade P&L at the stack lots on the MEASURED basis, bucketed by the label week of the EXIT. "hold-to-stop stack" has no TH loss rule and no locks (this sim); "stack as it is" is the actual stack trade table P&L (TH cuts and lock engine, dv2a stack_trades); "overlay" = actual stack + (rule - hold) weekly delta. Locks (-2R/+5R, give-back arm, week floor) are NOT re-run on the rule streams: labelled.

| win | series | weeks | mean | sd | maxdd | worst | worst20 | d_mean | d_sd | d_maxdd | d_worst20 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PRE | stack as it is (actual, TH+locks) | 75 | 46,332 | 133,291 | 409,229 | -306,664 | -2,333,434 |  |  |  |  |
| PRE | stack hold-to-stop (this sim, no TH, no locks) | 75 | 24,519 | 136,379 | 529,072 | -334,490 | -2,748,994 |  |  |  |  |
| HOLD | stack as it is (actual, TH+locks) | 32 | 53,670 | 153,219 | 578,442 | -318,557 | -742,938 |  |  |  |  |
| HOLD | stack hold-to-stop (this sim, no TH, no locks) | 32 | 7,993 | 155,374 | 657,134 | -351,290 | -1,677,723 |  |  |  |  |
| X | stack as it is (actual, TH+locks) | 44 | 19,608 | 113,430 | 542,017 | -157,300 | -1,722,161 |  |  |  |  |
| X | stack hold-to-stop (this sim, no TH, no locks) | 44 | 13,711 | 117,832 | 591,176 | -169,370 | -1,934,792 |  |  |  |  |
| PRE | stack + L6_a15_r3_w30 | 75 | 5,865 | 94,777 | 834,069 | -195,344 | -2,150,240 | -18,654 | -41,603 | 304,996 | 598,755 |
| PRE | actual stack + (L6_a15_r3_w30 - hold) overlay | 75 | 27,678 | 96,356 | 364,215 | -225,593 | -1,740,739 | -18,654 | -36,934 | -45,014 | 592,695 |
| HOLD | stack + L6_a15_r3_w30 | 32 | -7,585 | 93,339 | 407,451 | -205,946 | -1,244,393 | -15,578 | -62,036 | -249,683 | 433,330 |
| HOLD | actual stack + (L6_a15_r3_w30 - hold) overlay | 32 | 38,092 | 94,431 | 238,799 | -186,757 | -282,937 | -15,578 | -58,788 | -339,643 | 460,001 |
| X | stack + L6_a15_r3_w30 | 44 | 20,352 | 80,877 | 214,598 | -125,416 | -946,017 | 6,640 | -36,954 | -376,577 | 988,775 |
| X | actual stack + (L6_a15_r3_w30 - hold) overlay | 44 | 26,248 | 80,470 | 170,576 | -96,647 | -829,382 | 6,640 | -32,960 | -371,440 | 892,780 |
| PRE | stack + L2_x5_t60 | 75 | 25,759 | 119,959 | 416,646 | -248,409 | -2,307,599 | 1,240 | -16,421 | -112,426 | 441,395 |
| PRE | actual stack + (L2_x5_t60 - hold) overlay | 75 | 47,573 | 117,282 | 329,102 | -219,824 | -1,866,962 | 1,240 | -16,009 | -80,127 | 466,472 |
| HOLD | stack + L2_x5_t60 | 32 | -2,750 | 134,131 | 538,601 | -265,773 | -1,545,690 | -10,743 | -21,244 | -118,533 | 132,033 |
| HOLD | actual stack + (L2_x5_t60 - hold) overlay | 32 | 42,927 | 131,038 | 459,909 | -233,041 | -652,840 | -10,743 | -22,181 | -118,533 | 90,097 |
| X | stack + L2_x5_t60 | 44 | 13,867 | 103,428 | 552,424 | -157,407 | -1,549,412 | 155 | -14,403 | -38,752 | 385,380 |
| X | actual stack + (L2_x5_t60 - hold) overlay | 44 | 19,763 | 100,223 | 334,704 | -139,563 | -1,420,933 | 155 | -13,207 | -207,313 | 301,229 |
| PRE | stack + L6_a20_r3_w10 | 75 | 16,276 | 108,970 | 436,411 | -254,884 | -2,370,847 | -8,243 | -27,409 | -92,661 | 378,148 |
| PRE | actual stack + (L6_a20_r3_w10 - hold) overlay | 75 | 38,089 | 109,828 | 319,268 | -238,685 | -1,953,864 | -8,243 | -23,463 | -89,961 | 379,571 |
| HOLD | stack + L6_a20_r3_w10 | 32 | 25,445 | 131,945 | 519,742 | -231,753 | -1,080,112 | 17,451 | -23,430 | -137,393 | 597,611 |
| HOLD | actual stack + (L6_a20_r3_w10 - hold) overlay | 32 | 71,121 | 133,846 | 441,050 | -199,021 | -196,009 | 17,451 | -19,373 | -137,393 | 546,929 |
| X | stack + L6_a20_r3_w10 | 44 | 22,032 | 101,875 | 448,471 | -173,141 | -1,367,964 | 8,321 | -15,956 | -142,705 | 566,828 |
| X | actual stack + (L6_a20_r3_w10 - hold) overlay | 44 | 27,929 | 101,017 | 395,186 | -157,725 | -1,268,716 | 8,321 | -12,413 | -146,831 | 453,445 |


### 9b. Does the stack-level variance reduction beat random exits at the same exit rate? (20 timing-matched placebo draws per rule, all six books, weekly series, MEASURED basis)

| win | rule | sd | placebo_sd | mean | placebo_mean | maxdd | placebo_maxdd | worst20 | placebo_worst20 |
|---|---|---|---|---|---|---|---|---|---|
| PRE | L6_a15_r3_w30 | 94,777 | 91,458 [84,471,95,956] | 5,865 | 10,468 | 834,069 | 454,983 | -2,150,240 | -1,971,917 |
| HOLD | L6_a15_r3_w30 | 93,339 | 95,185 [91,373,102,721] | -7,585 | 3,081 | 407,451 | 345,118 | -1,244,393 | -1,061,627 |
| X | L6_a15_r3_w30 | 80,877 | 86,325 [78,834,91,865] | 20,352 | 10,647 | 214,598 | 496,005 | -946,017 | -1,306,285 |
| PRE | L2_x5_t60 | 119,959 | 124,023 [118,960,130,616] | 25,759 | 17,256 | 416,646 | 550,321 | -2,307,599 | -2,545,488 |
| HOLD | L2_x5_t60 | 134,131 | 140,199 [132,080,147,762] | -2,750 | 3,564 | 538,601 | 601,886 | -1,545,690 | -1,540,510 |
| X | L2_x5_t60 | 103,428 | 106,522 [99,041,113,126] | 13,867 | 11,774 | 552,424 | 546,563 | -1,549,412 | -1,703,287 |
| PRE | L6_a20_r3_w10 | 108,970 | 103,437 [97,875,112,320] | 16,276 | 17,930 | 436,411 | 374,062 | -2,370,847 | -2,181,336 |
| HOLD | L6_a20_r3_w10 | 131,945 | 120,563 [113,032,127,911] | 25,445 | 3,892 | 519,742 | 471,515 | -1,080,112 | -1,313,759 |
| X | L6_a20_r3_w10 | 101,875 | 98,232 [91,073,103,245] | 22,032 | 10,836 | 448,471 | 564,390 | -1,367,964 | -1,530,480 |


# W. Walk-forward re-selection (Stage B)

### W1. Walk-forward chain, pooled over the 11 intraday books (one rule per week for all books jointly) and per-book selection summed over the 11 books

Pooled selection (one rule chosen per week from the joint trailing window of all 11 books):

| scope | window | policy | span | n | delta_pts | CI | MDE | usd_wk | placebo_rank | random_rule_chain | share_trades_cut_rule |
|---|---|---|---|---|---|---|---|---|---|---|---|
| POOL11 | 1-month | FORCED best | PRE | 18121 | -0.89 | [-1.64,-0.14] | 1.07 | -36,122 | 0.56 | -0.93 | 100% |
| POOL11 | 1-month | FORCED best | HOLD | 7747 | -0.29 | [-1.44,+0.86] | 1.64 | -4,159 | 0.95 | -0.93 | 100% |
| POOL11 | 1-month | WITH-HOLD | PRE | 18121 | -0.85 | [-1.60,-0.10] | 1.07 | -34,694 | 0.52 | -0.85 | 93% |
| POOL11 | 1-month | WITH-HOLD | HOLD | 7747 | -0.29 | [-1.44,+0.86] | 1.64 | -4,182 | 0.90 | -0.91 | 97% |
| POOL11 | 3-month | FORCED best | PRE | 18121 | -0.13 | [-0.68,+0.42] | 0.78 | -4,425 | 1.00 | -0.89 | 100% |
| POOL11 | 3-month | FORCED best | HOLD | 7747 | -0.84 | [-2.04,+0.37] | 1.72 | -24,801 | 0.59 | -0.93 | 100% |
| POOL11 | 3-month | WITH-HOLD | PRE | 18121 | -0.13 | [-0.68,+0.42] | 0.78 | -4,425 | 0.99 | -0.85 | 86% |
| POOL11 | 3-month | WITH-HOLD | HOLD | 7747 | -0.84 | [-2.04,+0.37] | 1.72 | -24,801 | 0.50 | -0.81 | 100% |


Per-book selection (each book chooses its own rule each week), 11 books stacked:

| selection | window | policy | span | n | delta_pts | CI | MDE | usd_wk |
|---|---|---|---|---|---|---|---|---|
| per-book | 3-month | FORCED best | PRE | 18121 | -0.63 | [-1.26,+0.00] | 0.90 | -26,057 |
| per-book | 3-month | FORCED best | HOLD | 7747 | -0.47 | [-1.51,+0.57] | 1.49 | -14,695 |
| per-book | 3-month | WITH-HOLD | PRE | 18121 | -0.63 | [-1.27,+0.00] | 0.90 | -26,239 |
| per-book | 3-month | WITH-HOLD | HOLD | 7747 | -0.47 | [-1.51,+0.57] | 1.49 | -14,695 |
| per-book | 1-month | FORCED best | PRE | 18121 | -0.73 | [-1.48,+0.02] | 1.08 | -29,926 |
| per-book | 1-month | FORCED best | HOLD | 7747 | -0.36 | [-1.53,+0.81] | 1.67 | -10,340 |
| per-book | 1-month | WITH-HOLD | PRE | 18121 | -0.73 | [-1.48,+0.02] | 1.07 | -30,005 |
| per-book | 1-month | WITH-HOLD | HOLD | 7747 | -0.36 | [-1.53,+0.81] | 1.67 | -10,260 |


Fixed comparators over the full PRE / HOLD span of the 11 books (pts/trade):

| comparator | PRE | HOLD |
|---|---|---|
| live TH loss L6_a15_r3_w30 (fixed) | -1.00 [-2.05,+0.04] (MDE 1.49) | -1.13 [-2.75,+0.49] (MDE 2.31) |
| best fixed rule by PRE (in-sample selection, L5e_x10_w300_t0.7) | -0.03 [-0.09,+0.03] | +0.00 [+0.00,+0.00] |
| best fixed rule by HOLD (selected on holdout, labelled, L5e_x10_w120_t0.7) | -0.14 [-0.35,+0.07] | +0.19 [-0.13,+0.50] |
| do nothing (hold-to-stop) | +0.00 | +0.00 |


### W2. Walk-forward chain per stream (both spans) and its tier (WF-LEAD = both spans positive, pooled PRE+HOLD CI above 0, placebo rank >= 0.95 in both; WF-WEAK = both spans positive only; else WF-DEAD)

| scope | window | policy | span | n | delta_pts | CI | MDE | usd_wk | placebo_rank | random_rule_chain | share_trades_cut_rule |
|---|---|---|---|---|---|---|---|---|---|---|---|
| stream:B3_NQ | 1-month | FORCED best | HOLD | 36 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 1.00 | -56.99 | 0% |
| stream:B3_NQ | 1-month | FORCED best | PRE | 78 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.81 | -10.45 | 0% |
| stream:B3_NQ | 1-month | WITH-HOLD | HOLD | 36 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.50 | +0.00 | 0% |
| stream:B3_NQ | 1-month | WITH-HOLD | PRE | 78 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.50 | +0.00 | 0% |
| stream:B3_NQ | 3-month | FORCED best | HOLD | 36 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 1.00 | -57.57 | 0% |
| stream:B3_NQ | 3-month | FORCED best | PRE | 78 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.86 | -9.74 | 0% |
| stream:B3_NQ | 3-month | WITH-HOLD | HOLD | 36 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.50 | +0.00 | 0% |
| stream:B3_NQ | 3-month | WITH-HOLD | PRE | 78 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.50 | +0.00 | 0% |
| stream:CR | 1-month | FORCED best | HOLD | 575 | +0.14 | [-1.17,+1.45] | 1.87 | 500 | 0.43 | +0.23 | 100% |
| stream:CR | 1-month | FORCED best | PRE | 1337 | -0.41 | [-1.33,+0.51] | 1.32 | -1,459 | 0.06 | -0.02 | 100% |
| stream:CR | 1-month | WITH-HOLD | HOLD | 575 | +0.14 | [-1.17,+1.45] | 1.87 | 500 | 0.40 | +0.22 | 100% |
| stream:CR | 1-month | WITH-HOLD | PRE | 1337 | -0.41 | [-1.33,+0.51] | 1.32 | -1,459 | 0.08 | -0.03 | 100% |
| stream:CR | 3-month | FORCED best | HOLD | 575 | +0.96 | [-0.42,+2.33] | 1.96 | 3,446 | 1.00 | +0.20 | 100% |
| stream:CR | 3-month | FORCED best | PRE | 1337 | -0.22 | [-0.84,+0.40] | 0.89 | -776 | 0.21 | -0.03 | 100% |
| stream:CR | 3-month | WITH-HOLD | HOLD | 575 | +0.96 | [-0.42,+2.33] | 1.96 | 3,446 | 0.98 | +0.22 | 100% |
| stream:CR | 3-month | WITH-HOLD | PRE | 1337 | -0.22 | [-0.84,+0.40] | 0.89 | -776 | 0.21 | -0.02 | 100% |
| stream:D6_HM_t75_s90_NYAM | 1-month | FORCED best | HOLD | 197 | -0.20 | [-4.74,+4.33] | 6.48 | -252 | 0.47 | -0.08 | 24% |
| stream:D6_HM_t75_s90_NYAM | 1-month | FORCED best | PRE | 427 | -1.47 | [-3.76,+0.81] | 3.27 | -1,679 | 1.00 | -5.94 | 27% |
| stream:D6_HM_t75_s90_NYAM | 1-month | WITH-HOLD | HOLD | 197 | -0.20 | [-4.74,+4.33] | 6.48 | -252 | 0.44 | +0.02 | 24% |
| stream:D6_HM_t75_s90_NYAM | 1-month | WITH-HOLD | PRE | 427 | -1.47 | [-3.76,+0.81] | 3.27 | -1,679 | 0.46 | -1.37 | 27% |
| stream:D6_HM_t75_s90_NYAM | 3-month | FORCED best | HOLD | 197 | +0.27 | [-6.27,+6.81] | 9.34 | 327 | 0.66 | -0.45 | 100% |
| stream:D6_HM_t75_s90_NYAM | 3-month | FORCED best | PRE | 427 | -1.77 | [-5.37,+1.82] | 5.14 | -2,019 | 1.00 | -5.88 | 100% |
| stream:D6_HM_t75_s90_NYAM | 3-month | WITH-HOLD | HOLD | 197 | +0.27 | [-6.27,+6.81] | 9.34 | 327 | 0.56 | -0.23 | 97% |
| stream:D6_HM_t75_s90_NYAM | 3-month | WITH-HOLD | PRE | 427 | -1.77 | [-5.37,+1.82] | 5.14 | -2,019 | 0.98 | -4.73 | 73% |
| stream:D6_KB_t60_s75_ASIA | 1-month | FORCED best | HOLD | 321 | -0.93 | [-4.18,+2.32] | 4.65 | -1,865 | 0.97 | -3.26 | 74% |
| stream:D6_KB_t60_s75_ASIA | 1-month | FORCED best | PRE | 704 | -2.54 | [-5.32,+0.24] | 3.97 | -4,766 | 1.00 | -4.81 | 70% |
| stream:D6_KB_t60_s75_ASIA | 1-month | WITH-HOLD | HOLD | 321 | -0.93 | [-4.18,+2.32] | 4.65 | -1,865 | 0.72 | -1.80 | 72% |
| stream:D6_KB_t60_s75_ASIA | 1-month | WITH-HOLD | PRE | 704 | -2.54 | [-5.32,+0.24] | 3.97 | -4,766 | 0.67 | -2.95 | 68% |
| stream:D6_KB_t60_s75_ASIA | 3-month | FORCED best | HOLD | 321 | -2.96 | [-6.44,+0.53] | 4.98 | -5,933 | 0.56 | -3.04 | 100% |
| stream:D6_KB_t60_s75_ASIA | 3-month | FORCED best | PRE | 704 | -2.68 | [-5.17,-0.18] | 3.56 | -5,025 | 0.99 | -4.77 | 100% |
| stream:D6_KB_t60_s75_ASIA | 3-month | WITH-HOLD | HOLD | 321 | -3.02 | [-6.50,+0.46] | 4.97 | -6,052 | 0.29 | -2.18 | 82% |
| stream:D6_KB_t60_s75_ASIA | 3-month | WITH-HOLD | PRE | 704 | -2.58 | [-5.06,-0.09] | 3.55 | -4,841 | 0.79 | -3.48 | 66% |
| stream:D6_PB7_PB5_ASIA | 1-month | FORCED best | HOLD | 192 | -0.24 | [-1.71,+1.24] | 2.11 | -286 | 0.41 | +0.04 | 16% |
| stream:D6_PB7_PB5_ASIA | 1-month | FORCED best | PRE | 342 | -0.77 | [-1.84,+0.30] | 1.52 | -701 | 1.00 | -5.91 | 6% |
| stream:D6_PB7_PB5_ASIA | 1-month | WITH-HOLD | HOLD | 192 | -0.24 | [-1.71,+1.24] | 2.11 | -286 | 0.24 | -0.02 | 16% |
| stream:D6_PB7_PB5_ASIA | 1-month | WITH-HOLD | PRE | 342 | -0.77 | [-1.84,+0.30] | 1.52 | -701 | 0.27 | -0.38 | 5% |
| stream:D6_PB7_PB5_ASIA | 3-month | FORCED best | HOLD | 192 | -0.13 | [-4.00,+3.74] | 5.53 | -154 | 0.48 | +0.05 | 100% |
| stream:D6_PB7_PB5_ASIA | 3-month | FORCED best | PRE | 342 | -5.47 | [-9.16,-1.77] | 5.28 | -4,987 | 0.68 | -5.88 | 100% |
| stream:D6_PB7_PB5_ASIA | 3-month | WITH-HOLD | HOLD | 192 | -0.13 | [-4.00,+3.74] | 5.53 | -154 | 0.55 | -0.08 | 96% |
| stream:D6_PB7_PB5_ASIA | 3-month | WITH-HOLD | PRE | 342 | -5.51 | [-9.20,-1.82] | 5.27 | -5,026 | 0.46 | -5.42 | 84% |
| stream:D6_SM_t60_sst_ASIA | 1-month | FORCED best | HOLD | 123 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.25 | +0.72 | 0% |
| stream:D6_SM_t60_sst_ASIA | 1-month | FORCED best | PRE | 264 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.81 | -0.84 | 0% |
| stream:D6_SM_t60_sst_ASIA | 1-month | WITH-HOLD | HOLD | 123 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.50 | +0.00 | 0% |
| stream:D6_SM_t60_sst_ASIA | 1-month | WITH-HOLD | PRE | 264 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.50 | +0.00 | 0% |
| stream:D6_SM_t60_sst_ASIA | 3-month | FORCED best | HOLD | 123 | -0.77 | [-4.91,+3.37] | 5.91 | -594 | 0.09 | +0.89 | 100% |
| stream:D6_SM_t60_sst_ASIA | 3-month | FORCED best | PRE | 264 | +0.53 | [-2.13,+3.18] | 3.79 | 372 | 0.95 | -0.87 | 100% |
| stream:D6_SM_t60_sst_ASIA | 3-month | WITH-HOLD | HOLD | 123 | -0.77 | [-4.91,+3.37] | 5.91 | -594 | 0.12 | +0.83 | 100% |
| stream:D6_SM_t60_sst_ASIA | 3-month | WITH-HOLD | PRE | 264 | +0.53 | [-2.13,+3.18] | 3.79 | 372 | 0.94 | -0.79 | 100% |
| stream:D6_TB4B_ASIA | 1-month | FORCED best | HOLD | 200 | +1.15 | [-1.51,+3.81] | 3.80 | 1,434 | 0.09 | +3.02 | 28% |
| stream:D6_TB4B_ASIA | 1-month | FORCED best | PRE | 450 | -0.82 | [-3.03,+1.39] | 3.15 | -985 | 0.99 | -2.89 | 33% |
| stream:D6_TB4B_ASIA | 1-month | WITH-HOLD | HOLD | 200 | +1.15 | [-1.51,+3.81] | 3.80 | 1,434 | 0.66 | +0.72 | 28% |
| stream:D6_TB4B_ASIA | 1-month | WITH-HOLD | PRE | 450 | -0.82 | [-3.03,+1.39] | 3.15 | -985 | 0.40 | -0.62 | 32% |
| stream:D6_TB4B_ASIA | 3-month | FORCED best | HOLD | 200 | +3.89 | [-1.78,+9.57] | 8.11 | 4,867 | 0.75 | +3.02 | 100% |
| stream:D6_TB4B_ASIA | 3-month | FORCED best | PRE | 450 | -2.52 | [-6.14,+1.11] | 5.17 | -3,019 | 0.62 | -2.81 | 100% |
| stream:D6_TB4B_ASIA | 3-month | WITH-HOLD | HOLD | 200 | +3.89 | [-1.78,+9.57] | 8.11 | 4,867 | 0.77 | +2.98 | 94% |
| stream:D6_TB4B_ASIA | 3-month | WITH-HOLD | PRE | 450 | -2.52 | [-6.14,+1.11] | 5.17 | -3,019 | 0.58 | -2.69 | 98% |
| stream:D6_TB4W_03_ASIA | 1-month | FORCED best | HOLD | 369 | -0.29 | [-4.02,+3.43] | 5.32 | -674 | 0.27 | +0.41 | 95% |
| stream:D6_TB4W_03_ASIA | 1-month | FORCED best | PRE | 800 | -0.70 | [-3.02,+1.62] | 3.31 | -1,485 | 1.00 | -2.23 | 76% |
| stream:D6_TB4W_03_ASIA | 1-month | WITH-HOLD | HOLD | 369 | -0.29 | [-4.02,+3.43] | 5.32 | -674 | 0.36 | +0.24 | 95% |
| stream:D6_TB4W_03_ASIA | 1-month | WITH-HOLD | PRE | 800 | -0.70 | [-3.02,+1.62] | 3.31 | -1,485 | 0.83 | -1.55 | 76% |
| stream:D6_TB4W_03_ASIA | 3-month | FORCED best | HOLD | 369 | +0.23 | [-3.38,+3.85] | 5.16 | 535 | 0.45 | +0.44 | 100% |
| stream:D6_TB4W_03_ASIA | 3-month | FORCED best | PRE | 800 | -0.61 | [-2.88,+1.67] | 3.25 | -1,297 | 0.97 | -2.16 | 100% |
| stream:D6_TB4W_03_ASIA | 3-month | WITH-HOLD | HOLD | 369 | +0.23 | [-3.38,+3.85] | 5.16 | 535 | 0.43 | +0.46 | 100% |
| stream:D6_TB4W_03_ASIA | 3-month | WITH-HOLD | PRE | 800 | -0.61 | [-2.88,+1.67] | 3.25 | -1,297 | 1.00 | -2.20 | 100% |
| stream:DN | 1-month | FORCED best | HOLD | 782 | -0.48 | [-2.99,+2.02] | 3.58 | -2,369 | 0.92 | -1.84 | 100% |
| stream:DN | 1-month | FORCED best | PRE | 1762 | -0.67 | [-2.47,+1.13] | 2.57 | -3,155 | 0.57 | -0.76 | 100% |
| stream:DN | 1-month | WITH-HOLD | HOLD | 782 | -0.48 | [-2.99,+2.02] | 3.58 | -2,369 | 0.90 | -1.72 | 100% |
| stream:DN | 1-month | WITH-HOLD | PRE | 1762 | -0.71 | [-2.51,+1.08] | 2.57 | -3,354 | 0.53 | -0.76 | 94% |
| stream:DN | 3-month | FORCED best | HOLD | 782 | -2.79 | [-5.32,-0.26] | 3.61 | -13,635 | 0.17 | -1.90 | 100% |
| stream:DN | 3-month | FORCED best | PRE | 1762 | -1.63 | [-3.27,+0.02] | 2.35 | -7,640 | 0.07 | -0.83 | 100% |
| stream:DN | 3-month | WITH-HOLD | HOLD | 782 | -2.79 | [-5.32,-0.26] | 3.61 | -13,635 | 0.18 | -1.87 | 100% |
| stream:DN | 3-month | WITH-HOLD | PRE | 1762 | -1.63 | [-3.27,+0.02] | 2.35 | -7,640 | 0.04 | -0.83 | 98% |
| stream:EM | 1-month | FORCED best | HOLD | 366 | +1.22 | [-2.93,+5.36] | 5.93 | 2,780 | 0.91 | -0.27 | 100% |
| stream:EM | 1-month | FORCED best | PRE | 871 | -0.39 | [-2.76,+1.99] | 3.39 | -898 | 0.69 | -0.77 | 100% |
| stream:EM | 1-month | WITH-HOLD | HOLD | 366 | +1.22 | [-2.93,+5.36] | 5.93 | 2,780 | 0.88 | -0.14 | 100% |
| stream:EM | 1-month | WITH-HOLD | PRE | 871 | -0.38 | [-2.74,+1.99] | 3.38 | -875 | 0.63 | -0.68 | 95% |
| stream:EM | 3-month | FORCED best | HOLD | 366 | -1.37 | [-4.91,+2.16] | 5.05 | -3,142 | 0.15 | -0.11 | 100% |
| stream:EM | 3-month | FORCED best | PRE | 871 | +0.33 | [-1.86,+2.52] | 3.13 | 768 | 0.95 | -0.77 | 100% |
| stream:EM | 3-month | WITH-HOLD | HOLD | 366 | -1.37 | [-4.91,+2.16] | 5.05 | -3,142 | 0.20 | -0.33 | 100% |
| stream:EM | 3-month | WITH-HOLD | PRE | 871 | +0.33 | [-1.86,+2.52] | 3.13 | 768 | 0.91 | -0.69 | 95% |
| stream:HM | 1-month | FORCED best | HOLD | 698 | -0.12 | [-2.88,+2.65] | 3.95 | -507 | 0.17 | +0.79 | 100% |
| stream:HM | 1-month | FORCED best | PRE | 1561 | -0.42 | [-2.27,+1.43] | 2.64 | -1,760 | 0.20 | +0.01 | 100% |
| stream:HM | 1-month | WITH-HOLD | HOLD | 698 | -0.12 | [-2.88,+2.65] | 3.95 | -507 | 0.14 | +0.86 | 100% |
| stream:HM | 1-month | WITH-HOLD | PRE | 1561 | -0.42 | [-2.27,+1.43] | 2.64 | -1,760 | 0.29 | -0.08 | 100% |
| stream:HM | 3-month | FORCED best | HOLD | 698 | +0.85 | [-1.60,+3.29] | 3.49 | 3,688 | 0.47 | +0.89 | 100% |
| stream:HM | 3-month | FORCED best | PRE | 1561 | -0.50 | [-2.38,+1.37] | 2.68 | -2,097 | 0.13 | -0.01 | 100% |
| stream:HM | 3-month | WITH-HOLD | HOLD | 698 | +0.85 | [-1.60,+3.29] | 3.49 | 3,688 | 0.54 | +0.79 | 100% |
| stream:HM | 3-month | WITH-HOLD | PRE | 1561 | -0.50 | [-2.38,+1.37] | 2.68 | -2,097 | 0.21 | -0.09 | 100% |
| stream:KB | 1-month | FORCED best | HOLD | 756 | -1.53 | [-4.36,+1.31] | 4.05 | -3,095 | 0.81 | -2.28 | 100% |
| stream:KB | 1-month | FORCED best | PRE | 1854 | -1.13 | [-2.66,+0.40] | 2.19 | -3,224 | 0.95 | -1.87 | 100% |
| stream:KB | 1-month | WITH-HOLD | HOLD | 756 | -1.53 | [-4.36,+1.31] | 4.05 | -3,095 | 0.71 | -2.02 | 97% |
| stream:KB | 1-month | WITH-HOLD | PRE | 1854 | -1.13 | [-2.66,+0.40] | 2.19 | -3,224 | 0.92 | -1.76 | 96% |
| stream:KB | 3-month | FORCED best | HOLD | 756 | -2.07 | [-4.54,+0.39] | 3.52 | -3,892 | 0.62 | -2.29 | 100% |
| stream:KB | 3-month | FORCED best | PRE | 1854 | -0.64 | [-1.80,+0.52] | 1.66 | -1,559 | 1.00 | -1.86 | 100% |
| stream:KB | 3-month | WITH-HOLD | HOLD | 756 | -2.07 | [-4.54,+0.39] | 3.52 | -3,892 | 0.49 | -2.04 | 100% |
| stream:KB | 3-month | WITH-HOLD | PRE | 1854 | -0.64 | [-1.80,+0.52] | 1.66 | -1,559 | 1.00 | -1.75 | 96% |
| stream:MA | 1-month | FORCED best | HOLD | 446 | -2.20 | [-5.62,+1.21] | 4.88 | -6,143 | 0.14 | -1.24 | 100% |
| stream:MA | 1-month | FORCED best | PRE | 997 | -1.02 | [-3.22,+1.17] | 3.13 | -2,723 | 0.85 | -1.73 | 100% |
| stream:MA | 1-month | WITH-HOLD | HOLD | 446 | -2.20 | [-5.62,+1.21] | 4.88 | -6,143 | 0.17 | -1.25 | 100% |
| stream:MA | 1-month | WITH-HOLD | PRE | 997 | -1.07 | [-3.26,+1.12] | 3.13 | -2,850 | 0.82 | -1.71 | 98% |
| stream:MA | 3-month | FORCED best | HOLD | 446 | -2.25 | [-5.84,+1.33] | 5.12 | -6,285 | 0.20 | -1.46 | 100% |
| stream:MA | 3-month | FORCED best | PRE | 997 | +0.03 | [-1.70,+1.76] | 2.47 | 86 | 0.99 | -1.75 | 100% |
| stream:MA | 3-month | WITH-HOLD | HOLD | 446 | -2.25 | [-5.84,+1.33] | 5.12 | -6,285 | 0.19 | -1.35 | 100% |
| stream:MA | 3-month | WITH-HOLD | PRE | 997 | +0.03 | [-1.70,+1.76] | 2.47 | 86 | 0.99 | -1.80 | 100% |
| stream:MV | 1-month | FORCED best | HOLD | 845 | -0.60 | [-3.26,+2.05] | 3.79 | -3,189 | 0.10 | +0.28 | 100% |
| stream:MV | 1-month | FORCED best | PRE | 2025 | -0.96 | [-2.48,+0.56] | 2.17 | -5,196 | 0.95 | -1.76 | 100% |
| stream:MV | 1-month | WITH-HOLD | HOLD | 845 | -0.60 | [-3.26,+2.05] | 3.79 | -3,189 | 0.21 | +0.17 | 100% |
| stream:MV | 1-month | WITH-HOLD | PRE | 2025 | -0.96 | [-2.48,+0.56] | 2.17 | -5,196 | 0.94 | -1.75 | 97% |
| stream:MV | 3-month | FORCED best | HOLD | 845 | +0.97 | [-1.33,+3.27] | 3.29 | 5,143 | 0.83 | +0.18 | 100% |
| stream:MV | 3-month | FORCED best | PRE | 2025 | -1.43 | [-2.71,-0.15] | 1.83 | -7,732 | 0.78 | -1.79 | 100% |
| stream:MV | 3-month | WITH-HOLD | HOLD | 845 | +0.97 | [-1.33,+3.27] | 3.29 | 5,143 | 0.83 | +0.16 | 100% |
| stream:MV | 3-month | WITH-HOLD | PRE | 2025 | -1.43 | [-2.71,-0.15] | 1.83 | -7,732 | 0.69 | -1.67 | 91% |
| stream:O6_LV_RN_BH | 1-month | FORCED best | HOLD | 78 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.53 | -0.18 | 0% |
| stream:O6_LV_RN_BH | 1-month | FORCED best | PRE | 134 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.99 | -4.61 | 0% |
| stream:O6_LV_RN_BH | 1-month | WITH-HOLD | HOLD | 78 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.50 | +0.00 | 0% |
| stream:O6_LV_RN_BH | 1-month | WITH-HOLD | PRE | 134 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.50 | +0.00 | 0% |
| stream:O6_LV_RN_BH | 3-month | FORCED best | HOLD | 78 | -0.55 | [-6.51,+5.41] | 8.52 | -268 | 0.42 | +0.08 | 58% |
| stream:O6_LV_RN_BH | 3-month | FORCED best | PRE | 134 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 1.00 | -4.55 | 0% |
| stream:O6_LV_RN_BH | 3-month | WITH-HOLD | HOLD | 78 | -0.55 | [-6.51,+5.41] | 8.52 | -268 | 0.31 | -0.07 | 58% |
| stream:O6_LV_RN_BH | 3-month | WITH-HOLD | PRE | 134 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.69 | -0.65 | 0% |
| stream:O6_OR15m_stp_le1 | 1-month | FORCED best | HOLD | 72 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.65 | -0.92 | 0% |
| stream:O6_OR15m_stp_le1 | 1-month | FORCED best | PRE | 179 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 1.00 | -6.03 | 0% |
| stream:O6_OR15m_stp_le1 | 1-month | WITH-HOLD | HOLD | 72 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.50 | +0.00 | 0% |
| stream:O6_OR15m_stp_le1 | 1-month | WITH-HOLD | PRE | 179 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.50 | +0.00 | 0% |
| stream:O6_OR15m_stp_le1 | 3-month | FORCED best | HOLD | 72 | -2.37 | [-8.36,+3.62] | 8.55 | -1,066 | 0.27 | -0.86 | 62% |
| stream:O6_OR15m_stp_le1 | 3-month | FORCED best | PRE | 179 | -1.78 | [-4.75,+1.19] | 4.25 | -851 | 0.99 | -6.01 | 55% |
| stream:O6_OR15m_stp_le1 | 3-month | WITH-HOLD | HOLD | 72 | -2.37 | [-8.36,+3.62] | 8.55 | -1,066 | 0.24 | -0.49 | 62% |
| stream:O6_OR15m_stp_le1 | 3-month | WITH-HOLD | PRE | 179 | -1.78 | [-4.75,+1.19] | 4.25 | -851 | 0.77 | -3.04 | 39% |
| stream:O6_OR30m_stp_ge0.5 | 1-month | FORCED best | HOLD | 125 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.93 | -2.83 | 0% |
| stream:O6_OR30m_stp_ge0.5 | 1-month | FORCED best | PRE | 297 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 1.00 | -5.04 | 0% |
| stream:O6_OR30m_stp_ge0.5 | 1-month | WITH-HOLD | HOLD | 125 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.50 | +0.00 | 0% |
| stream:O6_OR30m_stp_ge0.5 | 1-month | WITH-HOLD | PRE | 297 | +0.00 | [+0.00,+0.00] | 0.00 | 0 | 0.50 | +0.00 | 0% |
| stream:O6_OR30m_stp_ge0.5 | 3-month | FORCED best | HOLD | 125 | -3.43 | [-9.80,+2.94] | 9.10 | -2,681 | 0.32 | -2.61 | 100% |
| stream:O6_OR30m_stp_ge0.5 | 3-month | FORCED best | PRE | 297 | -4.09 | [-7.24,-0.93] | 4.51 | -3,236 | 0.76 | -4.99 | 100% |
| stream:O6_OR30m_stp_ge0.5 | 3-month | WITH-HOLD | HOLD | 125 | -3.43 | [-9.80,+2.94] | 9.10 | -2,681 | 0.29 | -2.30 | 85% |
| stream:O6_OR30m_stp_ge0.5 | 3-month | WITH-HOLD | PRE | 297 | -4.09 | [-7.24,-0.93] | 4.51 | -3,236 | 0.61 | -4.44 | 87% |
| stream:PB | 1-month | FORCED best | HOLD | 965 | +0.07 | [-2.10,+2.24] | 3.10 | 420 | 0.99 | -1.46 | 100% |
| stream:PB | 1-month | FORCED best | PRE | 2261 | +0.54 | [-1.09,+2.18] | 2.34 | 3,260 | 0.49 | +0.52 | 100% |
| stream:PB | 1-month | WITH-HOLD | HOLD | 965 | +0.07 | [-2.10,+2.24] | 3.10 | 420 | 0.96 | -1.37 | 94% |
| stream:PB | 1-month | WITH-HOLD | PRE | 2261 | +0.54 | [-1.09,+2.18] | 2.34 | 3,260 | 0.51 | +0.54 | 100% |
| stream:PB | 3-month | FORCED best | HOLD | 965 | -0.00 | [-2.20,+2.19] | 3.14 | -16 | 0.98 | -1.51 | 100% |
| stream:PB | 3-month | FORCED best | PRE | 2261 | +0.66 | [-0.85,+2.16] | 2.15 | 3,950 | 0.58 | +0.51 | 100% |
| stream:PB | 3-month | WITH-HOLD | HOLD | 965 | -0.00 | [-2.20,+2.19] | 3.14 | -16 | 0.96 | -1.39 | 94% |
| stream:PB | 3-month | WITH-HOLD | PRE | 2261 | +0.66 | [-0.85,+2.16] | 2.15 | 3,950 | 0.57 | +0.56 | 100% |
| stream:PE | 1-month | FORCED best | HOLD | 731 | -1.32 | [-3.73,+1.10] | 3.46 | -2,914 | 0.88 | -2.34 | 100% |
| stream:PE | 1-month | FORCED best | PRE | 1732 | -0.82 | [-2.45,+0.81] | 2.33 | -2,249 | 0.66 | -1.04 | 100% |
| stream:PE | 1-month | WITH-HOLD | HOLD | 731 | -1.32 | [-3.73,+1.10] | 3.46 | -2,914 | 0.94 | -2.43 | 100% |
| stream:PE | 1-month | WITH-HOLD | PRE | 1732 | -0.76 | [-2.39,+0.87] | 2.32 | -2,026 | 0.60 | -0.92 | 98% |
| stream:PE | 3-month | FORCED best | HOLD | 731 | -1.03 | [-2.79,+0.74] | 2.52 | -2,442 | 0.96 | -2.45 | 100% |
| stream:PE | 3-month | FORCED best | PRE | 1732 | -0.86 | [-2.29,+0.57] | 2.05 | -2,407 | 0.55 | -0.96 | 100% |
| stream:PE | 3-month | WITH-HOLD | HOLD | 731 | -1.03 | [-2.79,+0.74] | 2.52 | -2,442 | 0.94 | -2.25 | 92% |
| stream:PE | 3-month | WITH-HOLD | PRE | 1732 | -0.86 | [-2.29,+0.57] | 2.05 | -2,407 | 0.61 | -0.98 | 96% |
| stream:SM | 1-month | FORCED best | HOLD | 294 | +1.08 | [-3.07,+5.23] | 5.93 | 1,677 | 0.46 | +1.15 | 100% |
| stream:SM | 1-month | FORCED best | PRE | 774 | -2.15 | [-4.82,+0.51] | 3.80 | -3,504 | 0.52 | -2.21 | 98% |
| stream:SM | 1-month | WITH-HOLD | HOLD | 294 | +1.08 | [-3.07,+5.23] | 5.93 | 1,677 | 0.51 | +1.11 | 93% |
| stream:SM | 1-month | WITH-HOLD | PRE | 774 | -2.15 | [-4.82,+0.51] | 3.80 | -3,504 | 0.41 | -2.01 | 97% |
| stream:SM | 3-month | FORCED best | HOLD | 294 | +1.33 | [-2.61,+5.26] | 5.63 | 1,882 | 0.52 | +1.27 | 100% |
| stream:SM | 3-month | FORCED best | PRE | 774 | -1.50 | [-3.98,+0.99] | 3.55 | -2,622 | 0.82 | -2.24 | 100% |
| stream:SM | 3-month | WITH-HOLD | HOLD | 294 | +1.33 | [-2.61,+5.26] | 5.63 | 1,882 | 0.60 | +0.98 | 100% |
| stream:SM | 3-month | WITH-HOLD | PRE | 774 | -1.50 | [-3.98,+0.99] | 3.55 | -2,622 | 0.74 | -2.11 | 95% |
| stream:ST | 1-month | FORCED best | HOLD | 765 | +0.79 | [-1.73,+3.30] | 3.59 | 3,761 | 0.97 | -0.47 | 100% |
| stream:ST | 1-month | FORCED best | PRE | 1717 | -2.06 | [-3.74,-0.39] | 2.40 | -9,445 | 0.07 | -1.28 | 100% |
| stream:ST | 1-month | WITH-HOLD | HOLD | 765 | +0.83 | [-1.69,+3.34] | 3.59 | 3,949 | 0.94 | -0.46 | 97% |
| stream:ST | 1-month | WITH-HOLD | PRE | 1717 | -2.06 | [-3.74,-0.39] | 2.40 | -9,445 | 0.09 | -1.31 | 98% |
| stream:ST | 3-month | FORCED best | HOLD | 765 | +1.10 | [-1.13,+3.34] | 3.19 | 5,278 | 0.99 | -0.34 | 100% |
| stream:ST | 3-month | FORCED best | PRE | 1717 | -1.14 | [-2.59,+0.32] | 2.08 | -5,208 | 0.60 | -1.28 | 100% |
| stream:ST | 3-month | WITH-HOLD | HOLD | 765 | +1.10 | [-1.13,+3.34] | 3.19 | 5,278 | 0.96 | -0.46 | 100% |
| stream:ST | 3-month | WITH-HOLD | PRE | 1717 | -1.18 | [-2.63,+0.28] | 2.08 | -5,390 | 0.53 | -1.20 | 93% |
| stream:WT | 1-month | FORCED best | HOLD | 1099 | -0.16 | [-1.52,+1.20] | 1.95 | -761 | 0.86 | -0.65 | 100% |
| stream:WT | 1-month | FORCED best | PRE | 2567 | -0.22 | [-1.09,+0.66] | 1.25 | -1,031 | 0.83 | -0.49 | 100% |
| stream:WT | 1-month | WITH-HOLD | HOLD | 1099 | -0.18 | [-1.54,+1.18] | 1.94 | -868 | 0.89 | -0.66 | 91% |
| stream:WT | 1-month | WITH-HOLD | PRE | 2567 | -0.22 | [-1.09,+0.66] | 1.25 | -1,031 | 0.75 | -0.44 | 100% |
| stream:WT | 3-month | FORCED best | HOLD | 1099 | -0.27 | [-1.58,+1.05] | 1.88 | -1,275 | 0.85 | -0.67 | 100% |
| stream:WT | 3-month | FORCED best | PRE | 2567 | -0.33 | [-1.15,+0.49] | 1.17 | -1,597 | 0.67 | -0.45 | 100% |
| stream:WT | 3-month | WITH-HOLD | HOLD | 1099 | -0.27 | [-1.58,+1.05] | 1.88 | -1,275 | 0.81 | -0.69 | 100% |
| stream:WT | 3-month | WITH-HOLD | PRE | 2567 | -0.33 | [-1.15,+0.49] | 1.17 | -1,597 | 0.67 | -0.44 | 100% |


Tier table:

| scope | window | policy | tier |
|---|---|---|---|
| POOL11 | 3-month | FORCED best | WF-DEAD |
| POOL11 | 3-month | WITH-HOLD | WF-DEAD |
| POOL11 | 1-month | FORCED best | WF-DEAD |
| POOL11 | 1-month | WITH-HOLD | WF-DEAD |
| stream:B3_NQ | 3-month | FORCED best | WF-DEAD |
| stream:B3_NQ | 3-month | WITH-HOLD | WF-DEAD |
| stream:B3_NQ | 1-month | FORCED best | WF-DEAD |
| stream:B3_NQ | 1-month | WITH-HOLD | WF-DEAD |
| stream:CR | 3-month | FORCED best | WF-DEAD |
| stream:CR | 3-month | WITH-HOLD | WF-DEAD |
| stream:CR | 1-month | FORCED best | WF-DEAD |
| stream:CR | 1-month | WITH-HOLD | WF-DEAD |
| stream:D6_HM_t75_s90_NYAM | 3-month | FORCED best | WF-DEAD |
| stream:D6_HM_t75_s90_NYAM | 3-month | WITH-HOLD | WF-DEAD |
| stream:D6_HM_t75_s90_NYAM | 1-month | FORCED best | WF-DEAD |
| stream:D6_HM_t75_s90_NYAM | 1-month | WITH-HOLD | WF-DEAD |
| stream:D6_KB_t60_s75_ASIA | 3-month | FORCED best | WF-DEAD |
| stream:D6_KB_t60_s75_ASIA | 3-month | WITH-HOLD | WF-DEAD |
| stream:D6_KB_t60_s75_ASIA | 1-month | FORCED best | WF-DEAD |
| stream:D6_KB_t60_s75_ASIA | 1-month | WITH-HOLD | WF-DEAD |
| stream:D6_PB7_PB5_ASIA | 3-month | FORCED best | WF-DEAD |
| stream:D6_PB7_PB5_ASIA | 3-month | WITH-HOLD | WF-DEAD |
| stream:D6_PB7_PB5_ASIA | 1-month | FORCED best | WF-DEAD |
| stream:D6_PB7_PB5_ASIA | 1-month | WITH-HOLD | WF-DEAD |
| stream:D6_SM_t60_sst_ASIA | 3-month | FORCED best | WF-DEAD |
| stream:D6_SM_t60_sst_ASIA | 3-month | WITH-HOLD | WF-DEAD |
| stream:D6_SM_t60_sst_ASIA | 1-month | FORCED best | WF-DEAD |
| stream:D6_SM_t60_sst_ASIA | 1-month | WITH-HOLD | WF-DEAD |
| stream:D6_TB4B_ASIA | 3-month | FORCED best | WF-DEAD |
| stream:D6_TB4B_ASIA | 3-month | WITH-HOLD | WF-DEAD |
| stream:D6_TB4B_ASIA | 1-month | FORCED best | WF-DEAD |
| stream:D6_TB4B_ASIA | 1-month | WITH-HOLD | WF-DEAD |
| stream:D6_TB4W_03_ASIA | 3-month | FORCED best | WF-DEAD |
| stream:D6_TB4W_03_ASIA | 3-month | WITH-HOLD | WF-DEAD |
| stream:D6_TB4W_03_ASIA | 1-month | FORCED best | WF-DEAD |
| stream:D6_TB4W_03_ASIA | 1-month | WITH-HOLD | WF-DEAD |
| stream:DN | 3-month | FORCED best | WF-DEAD |
| stream:DN | 3-month | WITH-HOLD | WF-DEAD |
| stream:DN | 1-month | FORCED best | WF-DEAD |
| stream:DN | 1-month | WITH-HOLD | WF-DEAD |
| stream:EM | 3-month | FORCED best | WF-DEAD |
| stream:EM | 3-month | WITH-HOLD | WF-DEAD |
| stream:EM | 1-month | FORCED best | WF-DEAD |
| stream:EM | 1-month | WITH-HOLD | WF-DEAD |
| stream:HM | 3-month | FORCED best | WF-DEAD |
| stream:HM | 3-month | WITH-HOLD | WF-DEAD |
| stream:HM | 1-month | FORCED best | WF-DEAD |
| stream:HM | 1-month | WITH-HOLD | WF-DEAD |
| stream:KB | 3-month | FORCED best | WF-DEAD |
| stream:KB | 3-month | WITH-HOLD | WF-DEAD |
| stream:KB | 1-month | FORCED best | WF-DEAD |
| stream:KB | 1-month | WITH-HOLD | WF-DEAD |
| stream:MA | 3-month | FORCED best | WF-DEAD |
| stream:MA | 3-month | WITH-HOLD | WF-DEAD |
| stream:MA | 1-month | FORCED best | WF-DEAD |
| stream:MA | 1-month | WITH-HOLD | WF-DEAD |
| stream:MV | 3-month | FORCED best | WF-DEAD |
| stream:MV | 3-month | WITH-HOLD | WF-DEAD |
| stream:MV | 1-month | FORCED best | WF-DEAD |
| stream:MV | 1-month | WITH-HOLD | WF-DEAD |
| stream:O6_LV_RN_BH | 3-month | FORCED best | WF-DEAD |
| stream:O6_LV_RN_BH | 3-month | WITH-HOLD | WF-DEAD |
| stream:O6_LV_RN_BH | 1-month | FORCED best | WF-DEAD |
| stream:O6_LV_RN_BH | 1-month | WITH-HOLD | WF-DEAD |
| stream:O6_OR15m_stp_le1 | 3-month | FORCED best | WF-DEAD |
| stream:O6_OR15m_stp_le1 | 3-month | WITH-HOLD | WF-DEAD |
| stream:O6_OR15m_stp_le1 | 1-month | FORCED best | WF-DEAD |
| stream:O6_OR15m_stp_le1 | 1-month | WITH-HOLD | WF-DEAD |
| stream:O6_OR30m_stp_ge0.5 | 3-month | FORCED best | WF-DEAD |
| stream:O6_OR30m_stp_ge0.5 | 3-month | WITH-HOLD | WF-DEAD |
| stream:O6_OR30m_stp_ge0.5 | 1-month | FORCED best | WF-DEAD |
| stream:O6_OR30m_stp_ge0.5 | 1-month | WITH-HOLD | WF-DEAD |
| stream:PB | 3-month | FORCED best | WF-DEAD |
| stream:PB | 3-month | WITH-HOLD | WF-DEAD |
| stream:PB | 1-month | FORCED best | WF-WEAK |
| stream:PB | 1-month | WITH-HOLD | WF-WEAK |
| stream:PE | 3-month | FORCED best | WF-DEAD |
| stream:PE | 3-month | WITH-HOLD | WF-DEAD |
| stream:PE | 1-month | FORCED best | WF-DEAD |
| stream:PE | 1-month | WITH-HOLD | WF-DEAD |
| stream:SM | 3-month | FORCED best | WF-DEAD |
| stream:SM | 3-month | WITH-HOLD | WF-DEAD |
| stream:SM | 1-month | FORCED best | WF-DEAD |
| stream:SM | 1-month | WITH-HOLD | WF-DEAD |
| stream:ST | 3-month | FORCED best | WF-DEAD |
| stream:ST | 3-month | WITH-HOLD | WF-DEAD |
| stream:ST | 1-month | FORCED best | WF-DEAD |
| stream:ST | 1-month | WITH-HOLD | WF-DEAD |
| stream:WT | 3-month | FORCED best | WF-DEAD |
| stream:WT | 3-month | WITH-HOLD | WF-DEAD |
| stream:WT | 1-month | FORCED best | WF-DEAD |
| stream:WT | 1-month | WITH-HOLD | WF-DEAD |


### W3. Pooled walk-forward chain by entry session and by calendar year (pooled selection, WITH-HOLD and FORCED, both windows)

| window | policy | split | n | delta_pts | MDE | usd_wk |
|---|---|---|---|---|---|---|
| 3-month | FORCED | session ASIA | 8989 | +0.02 | 1.39 | 1,323 |
| 3-month | FORCED | session LONDON | 6285 | -0.61 | 1.56 | -5,758 |
| 3-month | FORCED | session PRE | 1189 | +2.21 | 2.76 | 4,810 |
| 3-month | FORCED | session NY-AM | 5702 | -0.80 | 1.62 | -5,896 |
| 3-month | FORCED | session NY-PM | 3762 | -0.87 | 1.48 | -5,036 |
| 3-month | FORCED | session CLOSE | 55 | +1.68 | 5.98 | 172 |
| 3-month | FORCED | year 2024 | 10753 | -0.20 | 1.27 | -2,793 |
| 3-month | FORCED | year 2025 | 13698 | -0.36 | 0.93 | -5,266 |
| 3-month | FORCED | year 2026 | 1531 | -1.04 | 3.61 | -2,326 |
| 3-month | WITH-HOLD | session ASIA | 8989 | +0.02 | 1.39 | 1,323 |
| 3-month | WITH-HOLD | session LONDON | 6285 | -0.61 | 1.56 | -5,758 |
| 3-month | WITH-HOLD | session PRE | 1189 | +2.21 | 2.76 | 4,810 |
| 3-month | WITH-HOLD | session NY-AM | 5702 | -0.80 | 1.62 | -5,896 |
| 3-month | WITH-HOLD | session NY-PM | 3762 | -0.87 | 1.48 | -5,036 |
| 3-month | WITH-HOLD | session CLOSE | 55 | +1.68 | 5.98 | 172 |
| 3-month | WITH-HOLD | year 2024 | 10753 | -0.20 | 1.27 | -2,793 |
| 3-month | WITH-HOLD | year 2025 | 13698 | -0.36 | 0.93 | -5,266 |
| 3-month | WITH-HOLD | year 2026 | 1531 | -1.04 | 3.61 | -2,326 |
| 1-month | FORCED | session ASIA | 8989 | -0.67 | 1.62 | -9,599 |
| 1-month | FORCED | session LONDON | 6285 | -0.99 | 2.04 | -8,608 |
| 1-month | FORCED | session PRE | 1189 | +1.44 | 3.43 | 2,847 |
| 1-month | FORCED | session NY-AM | 5702 | -0.58 | 1.83 | -4,176 |
| 1-month | FORCED | session NY-PM | 3762 | -1.25 | 1.74 | -7,341 |
| 1-month | FORCED | session CLOSE | 55 | +0.87 | 9.46 | 89 |
| 1-month | FORCED | year 2024 | 10753 | -0.52 | 1.43 | -8,527 |
| 1-month | FORCED | year 2025 | 13698 | -0.86 | 1.26 | -16,852 |
| 1-month | FORCED | year 2026 | 1531 | -0.77 | 2.43 | -1,409 |
| 1-month | WITH-HOLD | session ASIA | 8989 | -0.59 | 1.61 | -8,605 |
| 1-month | WITH-HOLD | session LONDON | 6285 | -0.99 | 2.04 | -8,608 |
| 1-month | WITH-HOLD | session PRE | 1189 | +1.44 | 3.43 | 2,847 |
| 1-month | WITH-HOLD | session NY-AM | 5702 | -0.58 | 1.83 | -4,176 |
| 1-month | WITH-HOLD | session NY-PM | 3762 | -1.25 | 1.74 | -7,341 |
| 1-month | WITH-HOLD | session CLOSE | 55 | +0.87 | 9.46 | 89 |
| 1-month | WITH-HOLD | year 2024 | 10753 | -0.47 | 1.42 | -7,752 |
| 1-month | WITH-HOLD | year 2025 | 13698 | -0.85 | 1.25 | -16,633 |
| 1-month | WITH-HOLD | year 2026 | 1531 | -0.77 | 2.43 | -1,409 |


### W4. What the pooled chain selects (share of trades by chosen rule family and the five most chosen rules; 3-month WITH-HOLD and FORCED)

**WITH-HOLD** family share of trades: L6 27%, L2 19%, L5 18%, HOLD 10%, L3 10%, L4 9%, L1 4%, L7 3%. Top rules: L6_a30_r3_w10 13%, HOLD 10%, L5e_x20_w120_t0.5 8%, L5e_x10_w120_t0.7 7%, L2_x20_t60 6%.

Drift of the choice by half-year (top 3 rules): 2024H1: L4_x30_n300 31%, L2_x5_t20 11%, L6_a30_r3_w30 10% | 2024H2: L2_x20_t60 25%, L3_m30_y50_n60 17%, L1_x40 16% | 2025H1: HOLD 35%, L5e_x20_w120_t0.5 28%, L5e_x10_w120_t0.7 22% | 2025H2: L6_a30_r3_w10 52%, L6_a30_r3_w30 11%, L6_a25_r3_w30 10% | 2026H1: L6_a20_r3_w10 60%, L6_a25_r2_w120 24%, L5e_x10_w120_t0.7 16%

**FORCED** family share of trades: L5 28%, L6 27%, L2 19%, L3 10%, L4 9%, L1 4%, L7 3%. Top rules: L6_a30_r3_w10 13%, L5e_x20_w120_t0.5 8%, L5e_x10_w120_t0.7 7%, L5e_x10_w300_t0.7 7%, L2_x20_t60 6%.

Drift of the choice by half-year (top 3 rules): 2024H1: L4_x30_n300 31%, L2_x5_t20 11%, L6_a30_r3_w30 10% | 2024H2: L2_x20_t60 25%, L3_m30_y50_n60 17%, L1_x40 16% | 2025H1: L5e_x20_w120_t0.5 28%, L5e_x10_w300_t0.7 24%, L5e_x10_w120_t0.7 22% | 2025H2: L6_a30_r3_w10 52%, L6_a30_r3_w30 11%, L6_a25_r3_w30 10% | 2026H1: L6_a20_r3_w10 60%, L6_a25_r2_w120 24%, L5e_x10_w120_t0.7 16%
