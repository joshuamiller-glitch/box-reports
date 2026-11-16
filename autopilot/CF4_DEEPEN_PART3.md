# CF4_DEEPEN_PART3 - ladder inputs from PASSED items only, table-level replication in other cells, and timeframe consistency

**Verdict (data ends 2026-11-11) line (): strict ladder from PASSED items only (pooled over books, in_pos=0 signals): R per unit lot 0.031 full / 0.029 L6M vs base 0.019 / 0.009, the unselected nonsense ladder 0.017 / 0.011 and the random ladder with the same lot distribution 0.019 / 0.012, BUT a nonsense ladder built with the same selection pressure (best-|zw| of 200 controls per cell) gives 0.035 / 0.026: the real ladder beats unselected nonsense and random but NOT selection-matched nonsense on the full history (in-sample selection); the broad item set saturates at x2 for nearly every signal and is not informative. Passed states replicate poorly in other cells (section 2); only a minority of single-timeframe passers are consistent across timeframes (section 3). Table level and in-sample; the engine ladder is W-CF3's.**

LADDER FILE: /mnt/l2/l2vast/_confl/cols_cf4/cf4_ladder.parquet (key sid=sig_id, all 193,245 signals). Items per cell = Part 1 states that passed alone in the signal's book x session cell ("strict") or in its book x session, book, session or pooled cell ("broad"), counted when the signal is on the KEPT side (state yes if lift>0, state no if lift<0), plus the W-CF2 L3 arrival-imbalance LOW item (lo_w30_v_p20) for books U7, P7, O7, M7, A7. USER_SET_V0 items are not included (their exact columns are W-CF1/W-CF3's): add their count to n_strict. Columns: n_strict / n_broad (agree count), m_strict / m_broad (ladder: 0 agree = x0.5, 1 = x1, 2 = x1.5, 3+ = x2; cells without any passed item = x1; apply the book's live cap in the engine), m_nsA_* (matched nonsense ladder: the same number of items per cell drawn at random from the 200 nonsense controls with random orientation), m_nsB_* (best-|zw| nonsense items per cell with the same count, oriented by their own lift = the same selection pressure), m_rand_* (the real ladder permuted within book x session x month = same lot distribution).

## Ladder screen (risk-neutral R per unit lot = sum(m x R) / sum(m), in_pos=0 universe; base_R = unweighted mean R)

| items | group | window | n signals | base R | ladder R | nonsense A R | nonsense B R | random R | mean multiplier |
|---|---|---|---|---|---|---|---|---|---|
| strict | ALL signals with items | full | 79001 | 0.019 | 0.031 | 0.016 | 0.034 | 0.018 | 1.05 |
| strict | ALL signals with items | L6M | 15959 | 0.011 | 0.029 | 0.011 | 0.026 | 0.013 | 1.08 |
| strict | book A7 | full | 17422 | 0.022 | 0.028 | 0.023 | 0.038 | 0.019 | 0.79 |
| strict | book A7 | L6M | 2855 | -0.002 | 0.016 | 0.010 | 0.025 | 0.002 | 0.76 |
| strict | book H7 | full | 3225 | 0.046 | 0.052 | 0.044 | 0.056 | 0.041 | 0.99 |
| strict | book H7 | L6M | 545 | 0.040 | 0.052 | 0.032 | 0.046 | 0.040 | 1.00 |
| strict | book K7 | full | 15034 | 0.010 | 0.028 | 0.013 | 0.029 | 0.016 | 1.53 |
| strict | book K7 | L6M | 3759 | -0.012 | 0.009 | -0.010 | 0.003 | -0.002 | 1.55 |
| strict | book M7 | full | 16544 | 0.008 | 0.027 | 0.004 | 0.029 | 0.012 | 0.96 |
| strict | book M7 | L6M | 3253 | -0.004 | 0.033 | 0.002 | 0.022 | 0.005 | 0.95 |
| strict | book O7 | full | 512 | 0.231 | 0.266 | 0.236 | 0.275 | 0.265 | 0.59 |
| strict | book P7 | full | 28005 | 0.018 | 0.027 | 0.013 | 0.030 | 0.014 | 1.04 |
| strict | book P7 | L6M | 5807 | 0.028 | 0.039 | 0.027 | 0.036 | 0.024 | 1.05 |
| strict | book U7 | full | 2595 | 0.048 | 0.076 | 0.053 | 0.073 | 0.055 | 0.66 |
| strict | book U7 | L6M | 470 | 0.059 | 0.086 | 0.042 | 0.082 | 0.063 | 0.65 |
| broad | ALL signals with items | full | 83337 | 0.019 | 0.019 | 0.019 | 0.021 | 0.019 | 2.00 |
| broad | ALL signals with items | L6M | 16757 | 0.010 | 0.010 | 0.011 | 0.012 | 0.010 | 2.00 |
| broad | book A7 | full | 17422 | 0.022 | 0.022 | 0.022 | 0.025 | 0.022 | 2.00 |
| broad | book A7 | L6M | 2855 | -0.002 | -0.002 | -0.002 | 0.002 | -0.002 | 2.00 |
| broad | book H7 | full | 3225 | 0.046 | 0.046 | 0.045 | 0.049 | 0.046 | 2.00 |
| broad | book H7 | L6M | 545 | 0.040 | 0.041 | 0.037 | 0.042 | 0.041 | 2.00 |
| broad | book K7 | full | 15034 | 0.010 | 0.011 | 0.010 | 0.012 | 0.010 | 2.00 |
| broad | book K7 | L6M | 3759 | -0.012 | -0.012 | -0.012 | -0.010 | -0.012 | 2.00 |
| broad | book M7 | full | 16544 | 0.008 | 0.008 | 0.008 | 0.008 | 0.008 | 2.00 |
| broad | book M7 | L6M | 3253 | -0.004 | -0.004 | -0.004 | -0.004 | -0.004 | 2.00 |
| broad | book O7 | full | 512 | 0.231 | 0.231 | 0.234 | 0.236 | 0.231 | 2.00 |
| broad | book P7 | full | 28005 | 0.018 | 0.018 | 0.018 | 0.019 | 0.018 | 2.00 |
| broad | book P7 | L6M | 5807 | 0.028 | 0.028 | 0.030 | 0.029 | 0.028 | 2.00 |
| broad | book U7 | full | 2595 | 0.048 | 0.047 | 0.049 | 0.056 | 0.047 | 1.99 |
| broad | book U7 | L6M | 470 | 0.059 | 0.059 | 0.063 | 0.067 | 0.057 | 1.99 |

## Part 2 item 6 at table level: do the passing states hold in OTHER book x session cells?

The signal universe contains 7 books (P7, M7, K7, A7, H7, U7, O7); S7 and X1-X8 signals are not in signals_all.parquet, so they cannot be tested here. For each of the 92 passing states, all other book x session cells with n_yes >= 100 (2218 cell-tests in total): share with the same lift sign 0.57 (0.50 = no transfer), cells with the same sign and |zw|>2: 86 (chance under no transfer ~ 55), cells that pass the full rule: 0. Per-state CSV: /mnt/l2/l2vast/_confl/cf4_candidates/state_replication.csv.

| state | other cells | same sign | same sign and |zw|>2 | pass |
|---|---|---|---|---|
| c4_st_15m_macd_with_rising | 35 | 0.69 | 2 | 0 |
| c4_st_15m_rsi14_ext_against | 25 | 0.76 | 1 | 0 |
| c4_st_15m_rsi14_mid | 35 | 0.74 | 0 | 0 |
| c4_st_15m_rsi2_xin_against | 22 | 0.41 | 1 | 0 |
| c4_st_15m_rsi2_xin_with | 24 | 0.67 | 0 | 0 |
| c4_st_15m_sqzk10_fa_9p | 31 | 0.58 | 0 | 0 |
| c4_st_15m_sqzk10_fw_4_8 | 9 | 0.44 | 0 | 0 |
| c4_st_15m_sqzk10_mom_with_slope_with | 32 | 0.50 | 2 | 0 |
| c4_st_15m_sqzk10_none30 | 35 | 0.46 | 3 | 0 |
| c4_st_15m_sqzk10_slope_against | 25 | 0.56 | 0 | 0 |
| c4_st_15m_sqzk10_slope_with | 35 | 0.60 | 0 | 0 |
| c4_st_15m_sqzk15_fw_9p | 28 | 0.43 | 2 | 0 |
| c4_st_15m_sqzk15_mom_with_slope_with | 32 | 0.50 | 2 | 0 |
| c4_st_15m_sqzk15_on_1_5 | 26 | 0.69 | 3 | 0 |
| c4_st_15m_sqzk15_slope_against | 25 | 0.56 | 0 | 0 |

## Which of the 125 passers are consistent across timeframes?

Consistent = the same state (same name on 1m, 5m, 15m, 60m) keeps the sign of the lift on >= 3 of the 4 timeframes in the same cell and has |zw|>2 with that sign on >= 2: 13 of 114 single-timeframe-state passers (13 distinct states); the remaining 101 are single-timeframe results. The 11 passers from the agreement family (D, counts over the 4 timeframes) are timeframe-agreeing by construction. Details: /mnt/l2/l2vast/_confl/cf4_candidates/state_tf_consistency.csv.

| cell | book | sess | state | timeframes same sign (of 4) | with |zw|>2 | passing | status |
|---|---|---|---|---|---|---|---|
| book | M7 |  | c4_st_15m_sqzk20_on_13p | 3 | 2 | 1 | consistent |
| book | M7 |  | c4_st_15m_sqzk20_fa_4_8 | 3 | 2 | 2 | consistent |
| book | M7 |  | c4_st_60m_sqzk20_fa_4_8 | 3 | 2 | 2 | consistent |
| book_sess | A7 | 5 | c4_st_15m_sqzk15_fw_9p | 3 | 2 | 1 | consistent |
| book_sess | K7 | 0 | c4_st_5m_sqzk10_fa_9p | 3 | 2 | 2 | consistent |
| book_sess | K7 | 0 | c4_st_15m_sqzk10_fa_9p | 3 | 2 | 2 | consistent |
| book_sess | K7 | 1 | c4_st_5m_sqzk10_mom_against_slope_with | 3 | 2 | 1 | consistent |
| book_sess | K7 | 1 | c4_st_5m_sqzk15_mom_against_slope_with | 3 | 2 | 1 | consistent |
| book_sess | K7 | 1 | c4_st_5m_sqzk20_mom_against_slope_with | 3 | 2 | 1 | consistent |
| book_sess | K7 | 4 | c4_st_15m_rsi14_mid | 3 | 2 | 2 | consistent |
| book_sess | K7 | 4 | c4_st_60m_rsi14_mid | 3 | 2 | 2 | consistent |
| book_sess | M7 | 2 | c4_st_60m_macd_hist_with | 3 | 2 | 1 | consistent |
| book_sess | M7 | 2 | c4_st_60m_macd_hist_against | 3 | 2 | 1 | consistent |
