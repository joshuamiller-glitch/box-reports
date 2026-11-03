# DS3_SIZER FINAL DRAFT (S4a integrator, 2026-11-03 22:23Z); for the lead; numbers in section 2 regenerate every 25 min. Post-hoc, Shadow only; the user decides.

## 1. Answer
The live sizer stays as Q1-A (ER(20) on 5-min < 0.30 -> x0.5, else x1.0; live since 2026-11-02 19:30Z). Across S1, S1B, S1 hysteresis, S2, S2V (+hybrid/mean), S3, Q2-Q6, stack and the ER-at-the-add cells restated against Q1-A on the live-lot-order base (ts2) (S3X lock rows and S4b add cells not yet restated) no cell beats Q1-A on L6M AND PRE with the carrying week dropped, passes no-harm and the PA9 band, and is placebo-clean. sizer_policy proposal: live Q1-A ladder, no change (draft: autopilot/sizer_policy_DRAFT.txt).

## 2. Family by family (from the master table; base column says ts2 or the owner's older ts base)
 (rows vs Q1-A; 'base' column of the master says ts2 or the owner's older ts base):

- SIZER_ADD (ER at the add, ZL-2 Q6): 3 rows, 0 keep Q1-A's mean (strict), 0 meet the L6M+PRE cut rule, 0 also clear no-harm and the PA9 band. No row keeps the mean of Q1-A. Sentence: the ER sizer should stay as Q1-A for this family.
- SIZER_Q2(vs Q1-A): 52 rows, 42 keep Q1-A's mean (strict), 0 meet the L6M+PRE cut rule, 0 also clear no-harm and the PA9 band. Best mean-keeping by (cut L6M + cut PRE)/2: T_0.20_0.60 (asis (adds the x1.5 side to Q1-A)) L6M +0.274, PRE -0.019. Sentence: the ER sizer should stay as Q1-A for this family.
- SIZER_Q2/Q3 as adds to Q1-A (ZL-2 Q6): 12 rows, 6 keep Q1-A's mean (strict), 0 meet the L6M+PRE cut rule, 0 also clear no-harm and the PA9 band. Best mean-keeping by (cut L6M + cut PRE)/2: T_0.25_0.60 (per owner) L6M +0.317, PRE -0.061. Sentence: the ER sizer should stay as Q1-A for this family.
- SIZER_Q6 (ER variants vs Q1-A): 23 rows, 0 keep Q1-A's mean (strict), 0 meet the L6M+PRE cut rule, 0 also clear no-harm and the PA9 band. No row keeps the mean of Q1-A. Sentence: the ER sizer should stay as Q1-A for this family.
- SIZER_S1: 1996 rows, 999 keep Q1-A's mean (strict), 10 meet the L6M+PRE cut rule, 0 also clear no-harm and the PA9 band. Best mean-keeping by (cut L6M + cut PRE)/2: ('g12', 'er_10m_14', 'SIG', 'B') (down) L6M +0.348, PRE +0.028. Sentence: the ER sizer should stay as Q1-A for this family.
- SIZER_S1B(A): 160 rows, 92 keep Q1-A's mean (strict), 1 meet the L6M+PRE cut rule, 0 also clear no-harm and the PA9 band. Best mean-keeping by (cut L6M + cut PRE)/2: A|PE|asia|t0.35_0.75_1.25 (down) L6M +0.096, PRE +0.051. Sentence: the ER sizer should stay as Q1-A for this family.
- SIZER_S1_HYST: 148 rows, 84 keep Q1-A's mean (strict), 0 meet the L6M+PRE cut rule, 0 also clear no-harm and the PA9 band. Best mean-keeping by (cut L6M + cut PRE)/2: fam#38 (down) L6M +0.307, PRE +0.032. Sentence: the ER sizer should stay as Q1-A for this family.
- SIZER_S2(on Q1-A): 100 rows, 0 keep Q1-A's mean (strict), 0 meet the L6M+PRE cut rule, 0 also clear no-harm and the PA9 band. No row keeps the mean of Q1-A. Sentence: the ER sizer should stay as Q1-A for this family.
- SIZER_S2V(Q1-A): 389 rows, 111 keep Q1-A's mean (strict), 4 meet the L6M+PRE cut rule, 0 also clear no-harm and the PA9 band. Best mean-keeping by (cut L6M + cut PRE)/2: R|ATR|(0.3, 0.2, 0.2) (modifier) L6M +0.351, PRE +0.067. Sentence: the ER sizer should stay as Q1-A for this family.
- SIZER_S3(Q1-A): 114 rows, 82 keep Q1-A's mean (strict), 0 meet the L6M+PRE cut rule, 0 also clear no-harm and the PA9 band. Best mean-keeping by (cut L6M + cut PRE)/2: 3.2 pair er_2m_50 + ahead_rel MINDOWN (combo) L6M -0.029, PRE -0.097. Sentence: the ER sizer should stay as Q1-A for this family.
- STACK (BASE-4 Q1-A): 54 rows, 28 keep Q1-A's mean (strict), 0 meet the L6M+PRE cut rule, 0 also clear no-harm and the PA9 band. Best mean-keeping by (cut L6M + cut PRE)/2: cap17 (per owner) L6M +0.010, PRE +0.000. Sentence: the ER sizer should stay as Q1-A for this family.

3. Exposure (SIZER_EXPOSURE.md, ts2): Q1-A mean lots 2.31, worst day 18 net lots / $21.6k stack risk; 3-tier T_0.25_0.60 25 / $31.2k; K_PE 22 / $26.4k; KB-asia cell 19 / $22.8k.

## S4a notes (hand-written)
- S1 (21 ER windows x rank mappings, 998 cells) and S1B/hysteresis vs Q1-A on ts2: no cell clears the evidence bar. Closest at the drawdown level: S1 ers_5m_20 LIN B at exact equal mean lots (cut L6M .425, PRE .048, carry-dropped L6M .244, mean +951/+129 per week, PA9 L6M .373 / PRE .068 / MID -.026): L6M is large but PRE is inside the flip-5 band (.099); placebos at equal lots are being run (SIZER_EQLOTS_Q1A_S1TOP10.md). S1 ers_5m_20 SIG A beats 100/100 placebos on PRE only and fails no-harm.
- The cut on L6M of 'down' variants is mostly what random re-sizing gives (median placebo L6M cut 0.29 to 0.38).
- Equal-lots placebo result for S1 ers_5m_20 LIN B (100 draws x perm/dayshuf/ar1, rescaled to Q1-A's mean lots 2.311): cut rank L6M 0.83-0.85, PRE 0.62-0.71 (bar 0.90) -> NOT placebo-clean; mean rank 0.96-1.00. No FLAG. (SIZER_EQLOTS_Q1A_S1_ERS5M20_LINB_PLACEBO.csv)



## 3. Near-miss registered (implementable)
ZL-1 time-based vol-target, down-only, on Q1-A: m = clip(Q1A x min(1, max(0.5, M20/ATR14_5m)), 0.25, 1.0), M20 = median ATR14(5m) over all 5-min bars of the previous 20 label days. PA9 L6M/PRE/MID/X' 32.9/30.6/21.9/+16.1, carry-dropped 35.7/32.5, lots 2.0 vs 2.31, exposure unchanged, total -$341k. NEAR-MISS, not flagged: matched-lots random-drop rank .55 on L6M (1.00 on PRE), family null p .30, PE carries it, unstable walk-forward, positive dollar months 15/43. Shadow-only note in the policy draft; Q1-A stays. Full caveats: SIZER_LEAD_REGISTER.md.

## 4. Live-universe correction of S1 / S2 cells (SIZER_UNIVERSE_AUDIT.md)
The ranks (S4a ranks_book / ranks_c / roll250), the rank-hysteresis tier state, ZL-1's vol-target median and S4b's bk_* P&L features were built over all 88,490 engine signal rows; the live box sees 27,902 live-session signals and fills 21,397. Rebuilt on the live universe (ranks_live.parquet) and on taken history (ranks_taken.parquet) and re-scored on ts2 vs Q1-A (top 20 cells per family):

| family   | universe   |   cells |   mean_keeping |   cut_rule |   cut_rule_and_no_harm |
|:---------|:-----------|--------:|---------------:|-----------:|-----------------------:|
| HYST     | live       |      13 |              7 |          0 |                      0 |
| HYST     | old        |      13 |             13 |          0 |                      0 |
| HYST     | taken      |      13 |              8 |          0 |                      0 |
| S1       | live       |      20 |             18 |          1 |                      1 |
| S1       | old        |      20 |             20 |          0 |                      0 |
| S1       | taken      |      20 |             17 |          1 |                      1 |
| S2       | live       |      20 |              0 |          0 |                      0 |
| S2       | old        |      20 |              0 |          0 |                      0 |
| S2       | taken      |      20 |              0 |          0 |                      0 |
| S2V      | live       |      20 |             16 |          0 |                      0 |
| S2V      | old        |      20 |             20 |          1 |                      1 |
| S2V      | taken      |      20 |             13 |          0 |                      0 |

No lead or flag of S1 / S1B / S1_HYST / S2 changes status; the four S2V cut-rule rows lose it on the live universe. Not rebuilt: S4b bk_* features (S4b asked), ZL-1 R| regime cells, Z3's S3 combinations (Z3 re-running on ranks_live and pool_inputs_s1_live.csv). confirm_n15 (S4b) was retracted for the same universe error.

## 4b. Carrying-week constants corrected (Z2 audit, verified)
The harness constants drop PRE = 2024 W34-W51 (episode of the old x1.5-ladder base). The Q1-A ts2 core's own maxDD episodes are L6M 2026 W30-W37 (inside the dropped W27-38), PRE 2025 W06-W09 and X' 2023 W29-W36 (inside its window). All ts2 rows are regenerated with PRE = 2025 W06-09: S1 rows meeting the L6M+PRE+carry-dropped rule fall from 11 to 0 (the S1B cell A|MV|london t0.50_0.5_1.0 is the only row left: cuts 3.8% / 5.0%, far inside the PA9 band). Owner rows whose PRE drop used the old weeks (ZL-1, ZL-2 Q6, Z3) carry drop_PRE withheld (blank) until regenerated by the owners.

## 5. Exposure (SIZER_EXPOSURE.md, ts2)
Q1-A: mean lots 2.31 (formula over taken rows; engine 2.14), worst day 18 net lots / $21.6k stack risk; 3-tier T_0.25_0.60: 25 / $31.2k; K_PE: 22 / $26.4k; Q1-A + KB-asia S1B rule: 19 / $22.8k.

## 6. Questions open to the user
1. Real order latency: every cell is scored on the 1-second grid with the modelled cost model (market exits 0.80 pt, stops 2.45 pt worse); a real latency between ER computation and the order, and for any sizer change, is not modelled. Does the user want a latency sensitivity?
2. Rank hysteresis (ER percentile with margin) and every rank mapping: none survives on ts2 / live universe; does the user want any of them Shadow-logged anyway, or closed?
3. The ZL-1 vol-target near-miss: log it Shadow-only, or close it?
4. PA9 / flip-5 noise band: calibrated on the old x1.5 ladder; should it be re-calibrated on Q1-A (ts2) before final judgements (a smaller base drawdown makes bands harder or easier)?
5. Sizer x lock under Q1-A (section 3.5, Z1): result pending at the time of this draft.
6. Add-side sizer (addendum 2.1): ER at the add cells under Q1-A are closed by ZL-2's Q6 (no cell keeps the mean); does the user accept closing it?
7. Combination / learned-mapping work (3.2 / 3.3, Z3) re-run on the live universe: result pending.
8. Cells still on the old base or old universe in the master table: S2V R| cells, S4b bk_* features, Z3 combinations (flagged in the base / universe columns).
9. Not changing (user answers, for the record): PE split kept everywhere; ER gap handling live (no session-break neutralise); lock none for headlines, 12R floor + 2R/50% give-back unchanged; BT swing flip Shadow (first Monday read 2026-11-09).

## 7. Files
SIZER_MASTER_TABLE.md/.csv (Q1-A), SIZER_LEAD_REGISTER.md, SIZER_UNIVERSE_AUDIT.md, SIZER_EXPOSURE.md/.csv, SIZER_VS_Q1A_S1FAMILY.md, SIZER_EQLOTS_Q1A_S1TOP10.md, SIZER_TOP_S1_PLACEBO_EQRISK_Q1A.md, sizer_policy_DRAFT.txt, pool_inputs_s1_live.csv (/mnt/l2/l2vast/ds3_sizer/). Older x1.5-ladder tables: *_OLDREF.
