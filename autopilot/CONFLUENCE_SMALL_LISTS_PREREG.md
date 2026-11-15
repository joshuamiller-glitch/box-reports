# T-CONFLUENCE pre-specified small lists (W-CF3), registered BEFORE scoring, 2026-11-15
Rule of construction: one item per family (trend, level, VWAP, volume/tape, momentum), chosen by definition (the plain, standard item of each family at one timeframe), NOT by looking at outcomes. Each item is a single yes/no column of the joined library (block|column); unknown counts as no. Score = number of yes (0-5); rules: all 5, at least 4, at least 3. Scored per book-session cell and stack-wide with the step 5 controls (matched-count, windows, floors, W44-removed, bootstrap, then the exact engine for any that pass). Reported separately from searched lists. No tuning; a changed list is a new list with its own sha.

SL1 (5/15-min, session anchors): trend A|c_A_trend_15m ; level B|c_B_with_PDC ; vwap D|c_D_sess_side ; volume 2FG|c_F_cd5_pos ; momentum E|c_E_ret15_with
SL2 (slower / higher timeframe): trend A|c_A_trend_60m ; level B|c_B_with_MOPEN ; vwap D|c_D_weekly_side ; volume 2FG|c_F_rvol15_ge1.0 ; momentum E|c_E_er60_ge0.3_with
SL3 (faster): trend A|c_A_trend_5m ; level B|c_B_with_OR15H ; vwap D|c_D_vwap_rth0930_side ; volume 2FG|c_F_volrise5_ge1.0 ; momentum M|m_rsi14_5m_side
USER_SET_V0 variants: none until the user corrects a setting (then USER_SET_V1 is registered separately); V0 stays as registered (sha 13e2d06bd31c20a1).
