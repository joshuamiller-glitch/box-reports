# DS3_SIZER final plain sentences, filled from the master table by the integrator (2026-11-03 17:17Z); numbers regenerate every 25 min; hand-written notes at the end are S4a's. Post-hoc, Shadow only; the user decides.

1. The live sizer should stay as Q1-A (ER(20) on 5-min below 0.30 -> x0.5, else x1.0) unless a cell beats it on L6M AND PRE with the carrying week dropped, passes no-harm and the PA9 band, and is placebo-clean. Register: SIZER_LEAD_REGISTER.md. Policy draft: sizer_policy_DRAFT.txt (live Q1-A, no change).

2. Family by family (rows vs Q1-A; 'base' column of the master says ts2 or the owner's older ts base):

- SIZER_ADD (ER at the add, ZL-2 Q6): 3 rows, 0 keep Q1-A's mean (strict), 0 meet the L6M+PRE cut rule, 0 also clear no-harm and the PA9 band. No row keeps the mean of Q1-A. Sentence: the ER sizer should stay as Q1-A for this family.
- SIZER_Q2(vs Q1-A): 52 rows, 42 keep Q1-A's mean (strict), 0 meet the L6M+PRE cut rule, 0 also clear no-harm and the PA9 band. Best mean-keeping by (cut L6M + cut PRE)/2: T_0.20_0.60 (asis (adds the x1.5 side to Q1-A)) L6M +0.274, PRE -0.019. Sentence: the ER sizer should stay as Q1-A for this family.
- SIZER_Q2/Q3 as adds to Q1-A (ZL-2 Q6): 12 rows, 6 keep Q1-A's mean (strict), 0 meet the L6M+PRE cut rule, 0 also clear no-harm and the PA9 band. Best mean-keeping by (cut L6M + cut PRE)/2: T_0.25_0.60 (per owner) L6M +0.317, PRE -0.061. Sentence: the ER sizer should stay as Q1-A for this family.
- SIZER_Q6 (ER variants vs Q1-A): 23 rows, 0 keep Q1-A's mean (strict), 0 meet the L6M+PRE cut rule, 0 also clear no-harm and the PA9 band. No row keeps the mean of Q1-A. Sentence: the ER sizer should stay as Q1-A for this family.
- SIZER_S1: 1150 rows, 430 keep Q1-A's mean (strict), 8 meet the L6M+PRE cut rule, 0 also clear no-harm and the PA9 band. Best mean-keeping by (cut L6M + cut PRE)/2: ('g12', 'er_10m_14', 'SIG', 'B') (down) L6M +0.348, PRE +0.028. Sentence: the ER sizer should stay as Q1-A for this family.
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

