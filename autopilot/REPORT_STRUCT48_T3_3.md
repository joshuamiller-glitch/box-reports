# REPORT STRUCT48 T3.3 - different horizon on NQ (swing / overnight drift / weekly-open breakout)
Prereg: l2vast/struct48/prereg/T3_3.md (frozen, in DECISIONS.md, 58 trials in ledger). Engines code/t33lib.py, registry code/t33cells.py, scorer code/t33run.py. Rows rows/T3_3_pre.json.
Look-ahead audit (audit/T3_3_trunc.json): 360 random cuts per rule (ST x2, BO x2, overnight all 10 filter variants, weekly k=0.5/1.0): 0 mismatches. Daily filters use dates < trade date only.
Caveat: overnight trades spanning a contract roll are skipped (roll calendar assumed known in advance); pool note: corepool FIFO head blocked tickets for a while, audit was run unpooled as one nice'd process.

## PRE-HOLDOUT TEXT (written before the holdout was scored; window WF-PRE 2024-02..2025-06, 74 weeks)
Nothing passes pre-holdout. Set A (weekly SD ~100k) dwarfs 1-4 lot sleeves (SD 6-20k/wk unit lots 2), so integer-lot versions move the portfolio by ~0.5-3k/wk at most; the SD-matched portfolios (k up to ~10x lots) raise mean but at ratio 1.0 raise maxDD +25..150% (the sleeve's own drawdown is added at equal risk), and maxDD -10% is reached in only one cell-ratio row (ON_none@0.25: -14.4%), which fails CI, placebo (0.84), year share (1.36) and holdout. 
Weak-positive sleeves: ON_VT (VIX9D/VIX<1 overnight): standalone +2,399/wk (WF-PRE, unit lots 2), corr 0.22, portfolio mean up, CI of portfolio-minus-A excludes 0 at all ratios, placebo rank 0.968, 2x-cost ok, year share 0.54; its only failures pre-holdout are p1 (maxDD down >=10%: -7.3% at 0.25, -6.7% at 0.5, +28% at 1.0) and p4 (holdout, not yet scored). ST10_3 (2/5 days): small positive, fails CI/placebo/year share. BO20 and weekly k=0.5 are negative; WK k=1.0 and ON_PD5, ON_VT+PD5 are not distinguishable from random.
Full per-cell tables below; failed conditions listed per cell x ratio.

### Stage pre (score window WFPRE); every primary cell (20) x 3 risk ratios. Integer-lot = Set A + lots x unit sleeve.

| cell | stand mean/wk | stand SD | corr | stand plc rank | INT d_mean | INT d_maxDD | INT CI | INT plc | nb agree | DSR | ratio | port d_mean | port maxDD % | port ci | port plc | 2x | yr max | HOLD stand mean | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ST10_3_t2_L2 | 601 | 6066 | 0.02 | 0.88 | 601 | -19590 | [-774,1846] | 0.88 | False | 0.20 | 0.25 | 2415 | -7.8 | [-3112,7419] | 0.82 | True | 0.95 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t2_L2 | 601 | 6066 | 0.02 | 0.88 | 601 | -19590 | [-774,1846] | 0.88 | False | 0.22 | 0.5 | 4830 | 14.2 | [-6225,14838] | 0.82 | True | 0.95 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t2_L2 | 601 | 6066 | 0.02 | 0.88 | 601 | -19590 | [-774,1846] | 0.88 | False | 0.20 | 1.0 | 9661 | 73.2 | [-12449,29677] | 0.82 | True | 0.95 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t2_L4 | 1202 | 12132 | 0.02 | 0.88 | 1202 | -31256 | [-1548,3691] | 0.88 | False | 0.20 | 0.25 | 2415 | -7.8 | [-3112,7419] | 0.82 | True | 0.95 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t2_L4 | 1202 | 12132 | 0.02 | 0.88 | 1202 | -31256 | [-1548,3691] | 0.88 | False | 0.22 | 0.5 | 4830 | 14.2 | [-6225,14838] | 0.82 | True | 0.95 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t2_L4 | 1202 | 12132 | 0.02 | 0.88 | 1202 | -31256 | [-1548,3691] | 0.88 | False | 0.20 | 1.0 | 9661 | 73.2 | [-12449,29677] | 0.82 | True | 0.95 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| BO20_t2_L2 | -402 | 10184 | -0.14 | 0.34 | -402 | 8478 | [-2807,2023] | 0.34 | False | 0.15 | 0.25 | -961 | 5.1 | [-6720,4843] | 0.34 | False | None | None | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t2_L2 | -402 | 10184 | -0.14 | 0.34 | -402 | 8478 | [-2807,2023] | 0.34 | False | 0.11 | 0.5 | -1923 | 14.0 | [-13439,9686] | 0.34 | False | None | None | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t2_L2 | -402 | 10184 | -0.14 | 0.34 | -402 | 8478 | [-2807,2023] | 0.34 | False | 0.05 | 1.0 | -3846 | 52.0 | [-26879,19373] | 0.34 | False | None | None | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t2_L4 | -803 | 20368 | -0.14 | 0.34 | -803 | 16957 | [-5613,4046] | 0.34 | False | 0.15 | 0.25 | -961 | 5.1 | [-6720,4843] | 0.34 | False | None | None | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t2_L4 | -803 | 20368 | -0.14 | 0.34 | -803 | 16957 | [-5613,4046] | 0.34 | False | 0.11 | 0.5 | -1923 | 14.0 | [-13439,9686] | 0.34 | False | None | None | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t2_L4 | -803 | 20368 | -0.14 | 0.34 | -803 | 16957 | [-5613,4046] | 0.34 | False | 0.05 | 1.0 | -3846 | 52.0 | [-26879,19373] | 0.34 | False | None | None | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| ST10_3_t5_L2 | 571 | 7563 | -0.05 | 0.76 | 571 | -6470 | [-1094,2231] | 0.76 | True | 0.20 | 0.25 | 1841 | -3.3 | [-3526,7192] | 0.72 | True | 0.81 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t5_L2 | 571 | 7563 | -0.05 | 0.76 | 571 | -6470 | [-1094,2231] | 0.76 | True | 0.21 | 0.5 | 3682 | 22.1 | [-7053,14383] | 0.72 | True | 0.81 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t5_L2 | 571 | 7563 | -0.05 | 0.76 | 571 | -6470 | [-1094,2231] | 0.76 | True | 0.18 | 1.0 | 7364 | 72.9 | [-14105,28767] | 0.72 | True | 0.81 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t5_L4 | 1142 | 15126 | -0.05 | 0.76 | 1142 | -12941 | [-2188,4461] | 0.76 | True | 0.20 | 0.25 | 1841 | -3.3 | [-3526,7192] | 0.72 | True | 0.81 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t5_L4 | 1142 | 15126 | -0.05 | 0.76 | 1142 | -12941 | [-2188,4461] | 0.76 | True | 0.21 | 0.5 | 3682 | 22.1 | [-7053,14383] | 0.72 | True | 0.81 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t5_L4 | 1142 | 15126 | -0.05 | 0.76 | 1142 | -12941 | [-2188,4461] | 0.76 | True | 0.18 | 1.0 | 7364 | 72.9 | [-14105,28767] | 0.72 | True | 0.81 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| BO20_t5_L2 | -372 | 9936 | -0.29 | 0.38 | -372 | -1821 | [-2680,1810] | 0.38 | True | 0.16 | 0.25 | -912 | 7.9 | [-6576,4441] | 0.37 | False | None | None | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t5_L2 | -372 | 9936 | -0.29 | 0.38 | -372 | -1821 | [-2680,1810] | 0.38 | True | 0.14 | 0.5 | -1824 | 38.0 | [-13152,8883] | 0.37 | False | None | None | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t5_L2 | -372 | 9936 | -0.29 | 0.38 | -372 | -1821 | [-2680,1810] | 0.38 | True | 0.07 | 1.0 | -3649 | 132.5 | [-26304,17765] | 0.37 | False | None | None | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t5_L4 | -743 | 19872 | -0.29 | 0.38 | -743 | 9191 | [-5359,3620] | 0.38 | True | 0.16 | 0.25 | -912 | 7.9 | [-6576,4441] | 0.37 | False | None | None | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t5_L4 | -743 | 19872 | -0.29 | 0.38 | -743 | 9191 | [-5359,3620] | 0.38 | True | 0.14 | 0.5 | -1824 | 38.0 | [-13152,8883] | 0.37 | False | None | None | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t5_L4 | -743 | 19872 | -0.29 | 0.38 | -743 | 9191 | [-5359,3620] | 0.38 | True | 0.07 | 1.0 | -3649 | 132.5 | [-26304,17765] | 0.37 | False | None | None | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| ON_none_L2 | 1625 | 15546 | 0.21 | 0.85 | 1625 | -43538 | [-1975,5083] | 0.85 | True | 0.19 | 0.25 | 2548 | -14.4 | [-3097,7972] | 0.84 | True | 1.36 | None | p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_none_L2 | 1625 | 15546 | 0.21 | 0.85 | 1625 | -43538 | [-1975,5083] | 0.85 | True | 0.19 | 0.5 | 5097 | 15.4 | [-6194,15943] | 0.84 | True | 1.36 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_none_L2 | 1625 | 15546 | 0.21 | 0.85 | 1625 | -43538 | [-1975,5083] | 0.85 | True | 0.18 | 1.0 | 10194 | 112.3 | [-12389,31886] | 0.84 | True | 1.36 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_none_L4 | 3250 | 31093 | 0.21 | 0.85 | 3250 | -62917 | [-3949,10165] | 0.85 | True | 0.19 | 0.25 | 2548 | -14.4 | [-3097,7972] | 0.84 | True | 1.36 | None | p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_none_L4 | 3250 | 31093 | 0.21 | 0.85 | 3250 | -62917 | [-3949,10165] | 0.85 | True | 0.19 | 0.5 | 5097 | 15.4 | [-6194,15943] | 0.84 | True | 1.36 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_none_L4 | 3250 | 31093 | 0.21 | 0.85 | 3250 | -62917 | [-3949,10165] | 0.85 | True | 0.18 | 1.0 | 10194 | 112.3 | [-12389,31886] | 0.84 | True | 1.36 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_VT_L2 | 2399 | 9970 | 0.22 | 0.91 | 2399 | -22691 | [97,4803] | 0.91 | True | 0.27 | 0.25 | 5867 | -7.3 | [237,11747] | 0.97 | True | 0.54 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos |
| ON_VT_L2 | 2399 | 9970 | 0.22 | 0.91 | 2399 | -22691 | [97,4803] | 0.91 | True | 0.35 | 0.5 | 11734 | -6.7 | [473,23494] | 0.97 | True | 0.54 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos |
| ON_VT_L2 | 2399 | 9970 | 0.22 | 0.91 | 2399 | -22691 | [97,4803] | 0.91 | True | 0.42 | 1.0 | 23467 | 28.4 | [946,46988] | 0.97 | True | 0.54 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos |
| ON_VT_L4 | 4798 | 19939 | 0.22 | 0.91 | 4798 | -29520 | [193,9606] | 0.91 | True | 0.27 | 0.25 | 5867 | -7.3 | [237,11747] | 0.97 | True | 0.54 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos |
| ON_VT_L4 | 4798 | 19939 | 0.22 | 0.91 | 4798 | -29520 | [193,9606] | 0.91 | True | 0.35 | 0.5 | 11734 | -6.7 | [473,23494] | 0.97 | True | 0.54 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos |
| ON_VT_L4 | 4798 | 19939 | 0.22 | 0.91 | 4798 | -29520 | [193,9606] | 0.91 | True | 0.42 | 1.0 | 23467 | 28.4 | [946,46988] | 0.97 | True | 0.54 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos |
| ON_PD5_L2 | 355 | 9669 | 0.11 | 0.24 | 355 | -1579 | [-1831,2532] | 0.24 | True | 0.16 | 0.25 | 894 | -1.0 | [-4618,6385] | 0.27 | True | 1.98 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_PD5_L2 | 355 | 9669 | 0.11 | 0.24 | 355 | -1579 | [-1831,2532] | 0.24 | True | 0.15 | 0.5 | 1788 | 3.4 | [-9237,12770] | 0.27 | True | 1.98 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_PD5_L2 | 355 | 9669 | 0.11 | 0.24 | 355 | -1579 | [-1831,2532] | 0.24 | True | 0.10 | 1.0 | 3577 | 25.2 | [-18473,25539] | 0.27 | True | 1.98 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_PD5_L4 | 709 | 19337 | 0.11 | 0.24 | 709 | -3158 | [-3663,5064] | 0.24 | True | 0.16 | 0.25 | 894 | -1.0 | [-4618,6385] | 0.27 | True | 1.98 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_PD5_L4 | 709 | 19337 | 0.11 | 0.24 | 709 | -3158 | [-3663,5064] | 0.24 | True | 0.15 | 0.5 | 1788 | 3.4 | [-9237,12770] | 0.27 | True | 1.98 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_PD5_L4 | 709 | 19337 | 0.11 | 0.24 | 709 | -3158 | [-3663,5064] | 0.24 | True | 0.10 | 1.0 | 3577 | 25.2 | [-18473,25539] | 0.27 | True | 1.98 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_VT+PD5_L2 | 638 | 8320 | 0.19 | 0.47 | 638 | -10217 | [-1196,2641] | 0.47 | True | 0.18 | 0.25 | 1871 | -7.2 | [-3506,7741] | 0.54 | True | 0.79 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_VT+PD5_L2 | 638 | 8320 | 0.19 | 0.47 | 638 | -10217 | [-1196,2641] | 0.47 | True | 0.17 | 0.5 | 3742 | -6.5 | [-7012,15481] | 0.54 | True | 0.79 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_VT+PD5_L2 | 638 | 8320 | 0.19 | 0.47 | 638 | -10217 | [-1196,2641] | 0.47 | True | 0.14 | 1.0 | 7484 | 31.8 | [-14024,30962] | 0.54 | True | 0.79 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_VT+PD5_L4 | 1277 | 16640 | 0.19 | 0.47 | 1277 | -20434 | [-2393,5282] | 0.47 | True | 0.18 | 0.25 | 1871 | -7.2 | [-3506,7741] | 0.54 | True | 0.79 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_VT+PD5_L4 | 1277 | 16640 | 0.19 | 0.47 | 1277 | -20434 | [-2393,5282] | 0.47 | True | 0.17 | 0.5 | 3742 | -6.5 | [-7012,15481] | 0.54 | True | 0.79 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_VT+PD5_L4 | 1277 | 16640 | 0.19 | 0.47 | 1277 | -20434 | [-2393,5282] | 0.47 | True | 0.14 | 1.0 | 7484 | 31.8 | [-14024,30962] | 0.54 | True | 0.79 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| WK_k0.5_L2 | -2275 | 20458 | -0.04 | 0.16 | -2275 | -1747 | [-6766,2007] | 0.16 | True | 0.11 | 0.25 | -2711 | -0.5 | [-8064,2392] | 0.17 | False | None | None | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| WK_k0.5_L2 | -2275 | 20458 | -0.04 | 0.16 | -2275 | -1747 | [-6766,2007] | 0.16 | True | 0.06 | 0.5 | -5423 | 27.7 | [-16128,4783] | 0.17 | False | None | None | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| WK_k0.5_L2 | -2275 | 20458 | -0.04 | 0.16 | -2275 | -1747 | [-6766,2007] | 0.16 | True | 0.02 | 1.0 | -10846 | 148.5 | [-32256,9566] | 0.17 | False | None | None | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| WK_k0.5_L4 | -4550 | 40917 | -0.04 | 0.16 | -4550 | 40474 | [-13532,4013] | 0.16 | True | 0.11 | 0.25 | -2711 | -0.5 | [-8064,2392] | 0.17 | False | None | None | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| WK_k0.5_L4 | -4550 | 40917 | -0.04 | 0.16 | -4550 | 40474 | [-13532,4013] | 0.16 | True | 0.06 | 0.5 | -5423 | 27.7 | [-16128,4783] | 0.17 | False | None | None | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| WK_k0.5_L4 | -4550 | 40917 | -0.04 | 0.16 | -4550 | 40474 | [-13532,4013] | 0.16 | True | 0.02 | 1.0 | -10846 | 148.5 | [-32256,9566] | 0.17 | False | None | None | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| WK_k1.0_L2 | 658 | 16150 | 0.03 | 0.59 | 658 | -25367 | [-2873,4000] | 0.59 | False | 0.17 | 0.25 | 994 | -5.6 | [-4338,6039] | 0.6 | True | 0.8 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| WK_k1.0_L2 | 658 | 16150 | 0.03 | 0.59 | 658 | -25367 | [-2873,4000] | 0.59 | False | 0.16 | 0.5 | 1988 | -3.4 | [-8676,12078] | 0.6 | True | 0.8 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| WK_k1.0_L2 | 658 | 16150 | 0.03 | 0.59 | 658 | -25367 | [-2873,4000] | 0.59 | False | 0.11 | 1.0 | 3976 | 35.8 | [-17352,24155] | 0.6 | True | 0.8 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| WK_k1.0_L4 | 1317 | 32299 | 0.03 | 0.59 | 1317 | -19478 | [-5746,7999] | 0.59 | False | 0.17 | 0.25 | 994 | -5.6 | [-4338,6039] | 0.6 | True | 0.8 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| WK_k1.0_L4 | 1317 | 32299 | 0.03 | 0.59 | 1317 | -19478 | [-5746,7999] | 0.59 | False | 0.16 | 0.5 | 1988 | -3.4 | [-8676,12078] | 0.6 | True | 0.8 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| WK_k1.0_L4 | 1317 | 32299 | 0.03 | 0.59 | 1317 | -19478 | [-5746,7999] | 0.59 | False | 0.11 | 1.0 | 3976 | 35.8 | [-17352,24155] | 0.6 | True | 0.8 | None | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |

Neighbour cells (unit sleeves at lots 2/4):

| cell | stand mean/wk | d_mean | d_maxDD |
|---|---|---|---|
| ST10_2.5_t2_L2 | -1 | -1 | -7421 |
| ST10_2.5_t2_L4 | -2 | -2 | -14841 |
| ST14_3_t2_L2 | 354 | 354 | -21961 |
| ST14_3_t2_L4 | 709 | 709 | -35997 |
| BO15_t2_L2 | 26 | 26 | 16488 |
| BO15_t2_L4 | 52 | 52 | 32976 |
| BO30_t2_L2 | -72 | -72 | 8478 |
| BO30_t2_L4 | -143 | -143 | 16957 |
| ST10_2.5_t5_L2 | 65 | 65 | -25161 |
| ST10_2.5_t5_L4 | 131 | 131 | -38917 |
| ST14_3_t5_L2 | 775 | 775 | -6470 |
| ST14_3_t5_L4 | 1550 | 1550 | -12941 |
| BO15_t5_L2 | -1114 | -1114 | 19842 |
| BO15_t5_L4 | -2227 | -2227 | 39684 |
| BO30_t5_L2 | -399 | -399 | -1821 |
| BO30_t5_L4 | -799 | -799 | -3642 |
| ON_none@1550_L2 | 1881 | 1881 | -37398 |
| ON_none@1550_L4 | 3762 | 3762 | -54065 |
| ON_none@1559_L2 | 1820 | 1820 | -49861 |
| ON_none@1559_L4 | 3640 | 3640 | -48057 |
| ON_VT_a1_L2 | 1780 | 1780 | -43289 |
| ON_VT_a1_L4 | 3559 | 3559 | -16094 |
| ON_VT_a2_L2 | 1240 | 1240 | -39419 |
| ON_VT_a2_L4 | 2479 | 2479 | -8353 |
| ON_PD3_L2 | 325 | 325 | 4871 |
| ON_PD3_L4 | 650 | 650 | 9741 |
| ON_PDup_L2 | 284 | 284 | -8779 |
| ON_PDup_L4 | 568 | 568 | -17559 |
| ON_VT_a2+PD5_L2 | 248 | 248 | -1579 |
| ON_VT_a2+PD5_L4 | 497 | 497 | -3158 |
| ON_VT+PD3_L2 | 772 | 772 | -2147 |
| ON_VT+PD3_L4 | 1544 | 1544 | -4294 |
| WK_k0.25_L2 | -782 | -782 | -10238 |
| WK_k0.25_L4 | -1564 | -1564 | 13759 |
| WK_k0.75_L2 | -458 | -458 | -29307 |
| WK_k0.75_L4 | -916 | -916 | -27358 |
| WK_k1.5_L2 | -866 | -866 | -16892 |
| WK_k1.5_L4 | -1732 | -1732 | 38847 |


## FINAL (WF 2024-02+ incl. HOLD 2025-07+; holdout scored once, look logged in ledger/holdout_looks.jsonl)
VERDICT: no T3.3 cell PASSES (0 of 20 cells x 3 ratios; integer-lot common PASS also 0/20). Only overnight drift is real: ON_none standalone +2,358/wk at 2 lots WF, HOLD +3,132; ON_VT +2,223/wk, HOLD +1,996, corr ~0 with Set A. Best portfolio row: ON_VT@0.25-0.5: CI excludes 0 ([137,8729] at 0.25), mean +4,220/+8,439 per wk, 2x-cost ok, holdout positive, corr -0.03; fails p1 (maxDD only -7.4%/-7.0% vs the required -10%), placebo rank 0.85 (<0.95) and year share >60%. ON_none@0.25: maxDD -14.5%, placebo 0.97, mean +3,738, holdout positive, but CI [-428,7963] includes 0 (the only failed condition). DSR (ledger total ~27.9k trials) 0.4-0.5 for these, <0.95 everywhere. Swing ST: tiny positive WF, holdout ~0/negative, placebo 0.6-0.77. BO20 and weekly-open breakout: negative mean after cost, holdout negative.
Sizing note: sleeves are small (1-4 lots NQ; unit weekly SD 6-20k vs Set A ~100k), so integer-lot versions barely move the portfolio; SD-matched versions add their own drawdown (maxDD +25..160% at ratio 1.0) and cannot meet p1 for these Sharpe levels.
Per-stage tables (WF window): see below. Weekly unit series per sleeve (incl. 19 neighbour sleeves) in l2vast/struct48/out/T3_3/*.npz for T3.4 (unit_weekly on the Set A week axis; ON_VT, ON_none are the candidates).

### Stage final (score window WF); every primary cell (20) x 3 risk ratios. Integer-lot = Set A + lots x unit sleeve.

| cell | stand mean/wk | stand SD | corr | stand plc rank | INT d_mean | INT d_maxDD | INT CI | INT plc | nb agree | DSR | ratio | port d_mean | port maxDD % | port ci | port plc | 2x | yr max | HOLD stand mean | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ST10_3_t2_L2 | 338 | 5434 | 0.06 | 0.77 | 338 | -19590 | [-556,1130] | 0.77 | False | 0.30 | 0.25 | 1625 | -7.8 | [-2674,5434] | 0.77 | True | 0.89 | 21 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t2_L2 | 338 | 5434 | 0.06 | 0.77 | 338 | -19590 | [-556,1130] | 0.77 | False | 0.27 | 0.5 | 3249 | 25.8 | [-5349,10867] | 0.77 | True | 0.89 | 21 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t2_L2 | 338 | 5434 | 0.06 | 0.77 | 338 | -19590 | [-556,1130] | 0.77 | False | 0.17 | 1.0 | 6498 | 96.3 | [-10697,21735] | 0.77 | True | 0.89 | 21 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t2_L4 | 676 | 10869 | 0.06 | 0.77 | 676 | -31256 | [-1112,2260] | 0.77 | False | 0.30 | 0.25 | 1625 | -7.8 | [-2674,5434] | 0.77 | True | 0.89 | 21 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t2_L4 | 676 | 10869 | 0.06 | 0.77 | 676 | -31256 | [-1112,2260] | 0.77 | False | 0.27 | 0.5 | 3249 | 25.8 | [-5349,10867] | 0.77 | True | 0.89 | 21 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t2_L4 | 676 | 10869 | 0.06 | 0.77 | 676 | -31256 | [-1112,2260] | 0.77 | False | 0.17 | 1.0 | 6498 | 96.3 | [-10697,21735] | 0.77 | True | 0.89 | 21 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| BO20_t2_L2 | -1076 | 12121 | -0.02 | 0.16 | -1076 | 8478 | [-3037,996] | 0.16 | True | 0.18 | 0.25 | -2319 | 4.6 | [-6547,2148] | 0.17 | False | None | -902 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t2_L2 | -1076 | 12121 | -0.02 | 0.16 | -1076 | 8478 | [-3037,996] | 0.16 | True | 0.08 | 0.5 | -4639 | 10.2 | [-13094,4296] | 0.17 | False | None | -902 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t2_L2 | -1076 | 12121 | -0.02 | 0.16 | -1076 | 8478 | [-3037,996] | 0.16 | True | 0.01 | 1.0 | -9277 | 79.1 | [-26187,8592] | 0.17 | False | None | -902 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t2_L4 | -2152 | 24242 | -0.02 | 0.16 | -2152 | 16957 | [-6074,1993] | 0.16 | True | 0.18 | 0.25 | -2319 | 4.6 | [-6547,2148] | 0.17 | False | None | -902 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t2_L4 | -2152 | 24242 | -0.02 | 0.16 | -2152 | 16957 | [-6074,1993] | 0.16 | True | 0.08 | 0.5 | -4639 | 10.2 | [-13094,4296] | 0.17 | False | None | -902 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t2_L4 | -2152 | 24242 | -0.02 | 0.16 | -2152 | 16957 | [-6074,1993] | 0.16 | True | 0.01 | 1.0 | -9277 | 79.1 | [-26187,8592] | 0.17 | False | None | -902 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| ST10_3_t5_L2 | 176 | 8535 | 0.09 | 0.61 | 176 | -6470 | [-1258,1485] | 0.61 | False | 0.25 | 0.25 | 540 | -4.6 | [-3853,4546] | 0.6 | True | 1.68 | -131 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t5_L2 | 176 | 8535 | 0.09 | 0.61 | 176 | -6470 | [-1258,1485] | 0.61 | False | 0.19 | 0.5 | 1079 | 20.8 | [-7705,9091] | 0.6 | True | 1.68 | -131 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t5_L2 | 176 | 8535 | 0.09 | 0.61 | 176 | -6470 | [-1258,1485] | 0.61 | False | 0.08 | 1.0 | 2158 | 87.3 | [-15411,18183] | 0.6 | True | 1.68 | -131 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t5_L4 | 353 | 17070 | 0.09 | 0.61 | 353 | -12941 | [-2517,2970] | 0.61 | False | 0.25 | 0.25 | 540 | -4.6 | [-3853,4546] | 0.6 | True | 1.68 | -131 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t5_L4 | 353 | 17070 | 0.09 | 0.61 | 353 | -12941 | [-2517,2970] | 0.61 | False | 0.19 | 0.5 | 1079 | 20.8 | [-7705,9091] | 0.6 | True | 1.68 | -131 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ST10_3_t5_L4 | 353 | 17070 | 0.09 | 0.61 | 353 | -12941 | [-2517,2970] | 0.61 | False | 0.08 | 1.0 | 2158 | 87.3 | [-15411,18183] | 0.6 | True | 1.68 | -131 | p1_maxdd_down_10pct,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| BO20_t5_L2 | -447 | 13984 | -0.06 | 0.42 | -447 | -1821 | [-2803,1769] | 0.42 | True | 0.23 | 0.25 | -836 | 0.7 | [-5238,3306] | 0.43 | False | None | -262 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t5_L2 | -447 | 13984 | -0.06 | 0.42 | -447 | -1821 | [-2803,1769] | 0.42 | True | 0.15 | 0.5 | -1671 | 23.6 | [-10476,6612] | 0.43 | False | None | -262 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t5_L2 | -447 | 13984 | -0.06 | 0.42 | -447 | -1821 | [-2803,1769] | 0.42 | True | 0.04 | 1.0 | -3342 | 94.5 | [-20951,13224] | 0.43 | False | None | -262 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t5_L4 | -894 | 27968 | -0.06 | 0.42 | -894 | 9191 | [-5606,3538] | 0.42 | True | 0.23 | 0.25 | -836 | 0.7 | [-5238,3306] | 0.43 | False | None | -262 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t5_L4 | -894 | 27968 | -0.06 | 0.42 | -894 | 9191 | [-5606,3538] | 0.42 | True | 0.15 | 0.5 | -1671 | 23.6 | [-10476,6612] | 0.43 | False | None | -262 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| BO20_t5_L4 | -894 | 27968 | -0.06 | 0.42 | -894 | 9191 | [-5606,3538] | 0.42 | True | 0.04 | 1.0 | -3342 | 94.5 | [-20951,13224] | 0.43 | False | None | -262 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| ON_none_L2 | 2358 | 16484 | -0.00 | 0.96 | 2358 | -43538 | [-270,5023] | 0.96 | True | 0.40 | 0.25 | 3738 | -14.5 | [-428,7963] | 0.97 | True | 0.5 | 1566 | p5_ci_excludes0 |
| ON_none_L2 | 2358 | 16484 | -0.00 | 0.96 | 2358 | -43538 | [-270,5023] | 0.96 | True | 0.46 | 0.5 | 7476 | 16.4 | [-856,15926] | 0.97 | True | 0.5 | 1566 | p1_maxdd_down_10pct,p5_ci_excludes0 |
| ON_none_L2 | 2358 | 16484 | -0.00 | 0.96 | 2358 | -43538 | [-270,5023] | 0.96 | True | 0.42 | 1.0 | 14951 | 114.7 | [-1712,31852] | 0.97 | True | 0.5 | 1566 | p1_maxdd_down_10pct,p5_ci_excludes0 |
| ON_none_L4 | 4716 | 32968 | -0.00 | 0.96 | 4716 | -62917 | [-540,10046] | 0.96 | True | 0.40 | 0.25 | 3738 | -14.5 | [-428,7963] | 0.97 | True | 0.5 | 1566 | p5_ci_excludes0 |
| ON_none_L4 | 4716 | 32968 | -0.00 | 0.96 | 4716 | -62917 | [-540,10046] | 0.96 | True | 0.46 | 0.5 | 7476 | 16.4 | [-856,15926] | 0.97 | True | 0.5 | 1566 | p1_maxdd_down_10pct,p5_ci_excludes0 |
| ON_none_L4 | 4716 | 32968 | -0.00 | 0.96 | 4716 | -62917 | [-540,10046] | 0.96 | True | 0.42 | 1.0 | 14951 | 114.7 | [-1712,31852] | 0.97 | True | 0.5 | 1566 | p1_maxdd_down_10pct,p5_ci_excludes0 |
| ON_VT_L2 | 2223 | 13764 | -0.03 | 0.75 | 2223 | -22691 | [72,4598] | 0.75 | True | 0.43 | 0.25 | 4220 | -7.4 | [137,8729] | 0.85 | True | 0.68 | 998 | p1_maxdd_down_10pct,p6_placebo_ge95,year_ok |
| ON_VT_L2 | 2223 | 13764 | -0.03 | 0.75 | 2223 | -22691 | [72,4598] | 0.75 | True | 0.51 | 0.5 | 8439 | -7.0 | [275,17457] | 0.85 | True | 0.68 | 998 | p1_maxdd_down_10pct,p6_placebo_ge95,year_ok |
| ON_VT_L2 | 2223 | 13764 | -0.03 | 0.75 | 2223 | -22691 | [72,4598] | 0.75 | True | 0.50 | 1.0 | 16879 | 28.1 | [549,34915] | 0.85 | True | 0.68 | 998 | p1_maxdd_down_10pct,p6_placebo_ge95,year_ok |
| ON_VT_L4 | 4445 | 27529 | -0.03 | 0.75 | 4445 | -29520 | [145,9196] | 0.75 | True | 0.43 | 0.25 | 4220 | -7.4 | [137,8729] | 0.85 | True | 0.68 | 998 | p1_maxdd_down_10pct,p6_placebo_ge95,year_ok |
| ON_VT_L4 | 4445 | 27529 | -0.03 | 0.75 | 4445 | -29520 | [145,9196] | 0.75 | True | 0.51 | 0.5 | 8439 | -7.0 | [275,17457] | 0.85 | True | 0.68 | 998 | p1_maxdd_down_10pct,p6_placebo_ge95,year_ok |
| ON_VT_L4 | 4445 | 27529 | -0.03 | 0.75 | 4445 | -29520 | [145,9196] | 0.75 | True | 0.50 | 1.0 | 16879 | 28.1 | [549,34915] | 0.85 | True | 0.68 | 998 | p1_maxdd_down_10pct,p6_placebo_ge95,year_ok |
| ON_PD5_L2 | 513 | 12300 | -0.03 | 0.11 | 513 | -1579 | [-1507,2571] | 0.11 | True | 0.30 | 0.25 | 1091 | -0.8 | [-3202,5463] | 0.12 | True | 0.72 | 341 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_PD5_L2 | 513 | 12300 | -0.03 | 0.11 | 513 | -1579 | [-1507,2571] | 0.11 | True | 0.27 | 0.5 | 2182 | 1.7 | [-6403,10925] | 0.12 | True | 0.72 | 341 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_PD5_L2 | 513 | 12300 | -0.03 | 0.11 | 513 | -1579 | [-1507,2571] | 0.11 | True | 0.15 | 1.0 | 4363 | 56.3 | [-12807,21851] | 0.12 | True | 0.72 | 341 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_PD5_L4 | 1027 | 24600 | -0.03 | 0.11 | 1027 | -3158 | [-3014,5143] | 0.11 | True | 0.30 | 0.25 | 1091 | -0.8 | [-3202,5463] | 0.12 | True | 0.72 | 341 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_PD5_L4 | 1027 | 24600 | -0.03 | 0.11 | 1027 | -3158 | [-3014,5143] | 0.11 | True | 0.27 | 0.5 | 2182 | 1.7 | [-6403,10925] | 0.12 | True | 0.72 | 341 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_PD5_L4 | 1027 | 24600 | -0.03 | 0.11 | 1027 | -3158 | [-3014,5143] | 0.11 | True | 0.15 | 1.0 | 4363 | 56.3 | [-12807,21851] | 0.12 | True | 0.72 | 341 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_VT+PD5_L2 | 445 | 11174 | -0.01 | 0.14 | 445 | -10217 | [-1396,2364] | 0.14 | True | 0.30 | 0.25 | 1040 | -6.0 | [-3266,5530] | 0.16 | True | 1.17 | 112 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_VT+PD5_L2 | 445 | 11174 | -0.01 | 0.14 | 445 | -10217 | [-1396,2364] | 0.14 | True | 0.26 | 0.5 | 2081 | 0.3 | [-6531,11059] | 0.16 | True | 1.17 | 112 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_VT+PD5_L2 | 445 | 11174 | -0.01 | 0.14 | 445 | -10217 | [-1396,2364] | 0.14 | True | 0.14 | 1.0 | 4162 | 78.0 | [-13062,22118] | 0.16 | True | 1.17 | 112 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_VT+PD5_L4 | 890 | 22347 | -0.01 | 0.14 | 890 | -20434 | [-2793,4729] | 0.14 | True | 0.30 | 0.25 | 1040 | -6.0 | [-3266,5530] | 0.16 | True | 1.17 | 112 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_VT+PD5_L4 | 890 | 22347 | -0.01 | 0.14 | 890 | -20434 | [-2793,4729] | 0.14 | True | 0.26 | 0.5 | 2081 | 0.3 | [-6531,11059] | 0.16 | True | 1.17 | 112 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| ON_VT+PD5_L4 | 890 | 22347 | -0.01 | 0.14 | 890 | -20434 | [-2793,4729] | 0.14 | True | 0.14 | 1.0 | 4162 | 78.0 | [-13062,22118] | 0.16 | True | 1.17 | 112 | p1_maxdd_down_10pct,p5_ci_excludes0,p6_placebo_ge95,year_ok |
| WK_k0.5_L2 | -2865 | 21865 | -0.02 | 0.06 | -2865 | -1747 | [-6572,766] | 0.06 | True | 0.15 | 0.25 | -3423 | -0.5 | [-7854,916] | 0.06 | False | None | -1736 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| WK_k0.5_L2 | -2865 | 21865 | -0.02 | 0.06 | -2865 | -1747 | [-6572,766] | 0.06 | True | 0.06 | 0.5 | -6847 | 28.0 | [-15708,1831] | 0.06 | False | None | -1736 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| WK_k0.5_L2 | -2865 | 21865 | -0.02 | 0.06 | -2865 | -1747 | [-6572,766] | 0.06 | True | 0.01 | 1.0 | -13694 | 163.2 | [-31415,3663] | 0.06 | False | None | -1736 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| WK_k0.5_L4 | -5729 | 43731 | -0.02 | 0.06 | -5729 | 44700 | [-13144,1532] | 0.06 | True | 0.15 | 0.25 | -3423 | -0.5 | [-7854,916] | 0.06 | False | None | -1736 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| WK_k0.5_L4 | -5729 | 43731 | -0.02 | 0.06 | -5729 | 44700 | [-13144,1532] | 0.06 | True | 0.06 | 0.5 | -6847 | 28.0 | [-15708,1831] | 0.06 | False | None | -1736 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| WK_k0.5_L4 | -5729 | 43731 | -0.02 | 0.06 | -5729 | 44700 | [-13144,1532] | 0.06 | True | 0.01 | 1.0 | -13694 | 163.2 | [-31415,3663] | 0.06 | False | None | -1736 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| WK_k1.0_L2 | -666 | 18233 | 0.12 | 0.27 | -666 | -25367 | [-3803,2222] | 0.27 | True | 0.20 | 0.25 | -954 | -5.7 | [-5450,3185] | 0.29 | False | None | -1058 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| WK_k1.0_L2 | -666 | 18233 | 0.12 | 0.27 | -666 | -25367 | [-3803,2222] | 0.27 | True | 0.12 | 0.5 | -1909 | 18.5 | [-10901,6370] | 0.29 | False | None | -1058 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| WK_k1.0_L2 | -666 | 18233 | 0.12 | 0.27 | -666 | -25367 | [-3803,2222] | 0.27 | True | 0.03 | 1.0 | -3817 | 94.0 | [-21801,12739] | 0.29 | False | None | -1058 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| WK_k1.0_L4 | -1332 | 36466 | 0.12 | 0.27 | -1332 | -17165 | [-7606,4445] | 0.27 | True | 0.20 | 0.25 | -954 | -5.7 | [-5450,3185] | 0.29 | False | None | -1058 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| WK_k1.0_L4 | -1332 | 36466 | 0.12 | 0.27 | -1332 | -17165 | [-7606,4445] | 0.27 | True | 0.12 | 0.5 | -1909 | 18.5 | [-10901,6370] | 0.29 | False | None | -1058 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |
| WK_k1.0_L4 | -1332 | 36466 | 0.12 | 0.27 | -1332 | -17165 | [-7606,4445] | 0.27 | True | 0.03 | 1.0 | -3817 | 94.0 | [-21801,12739] | 0.29 | False | None | -1058 | p1_maxdd_down_10pct,p2_mean_not_down,p4_stand_hold_mean_pos,p5_ci_excludes0,p6_placebo_ge95,x2_ok,year_ok |

Neighbour cells (unit sleeves at lots 2/4):

| cell | stand mean/wk | d_mean | d_maxDD |
|---|---|---|---|
| ST10_2.5_t2_L2 | -446 | -446 | -7421 |
| ST10_2.5_t2_L4 | -892 | -892 | -14841 |
| ST14_3_t2_L2 | -194 | -194 | -21961 |
| ST14_3_t2_L4 | -387 | -387 | -35997 |
| BO15_t2_L2 | -829 | -829 | 16488 |
| BO15_t2_L4 | -1659 | -1659 | 32976 |
| BO30_t2_L2 | -764 | -764 | 8478 |
| BO30_t2_L4 | -1527 | -1527 | 16957 |
| ST10_2.5_t5_L2 | -504 | -504 | -25161 |
| ST10_2.5_t5_L4 | -1009 | -1009 | -38917 |
| ST14_3_t5_L2 | 96 | 96 | -6470 |
| ST14_3_t5_L4 | 192 | 192 | -12941 |
| BO15_t5_L2 | -1023 | -1023 | 19842 |
| BO15_t5_L4 | -2045 | -2045 | 39684 |
| BO30_t5_L2 | -792 | -792 | -1821 |
| BO30_t5_L4 | -1583 | -1583 | -3642 |
| ON_none@1550_L2 | 2396 | 2396 | -37398 |
| ON_none@1550_L4 | 4792 | 4792 | -54065 |
| ON_none@1559_L2 | 2465 | 2465 | -49861 |
| ON_none@1559_L4 | 4930 | 4930 | -48057 |
| ON_VT_a1_L2 | 1969 | 1969 | -43289 |
| ON_VT_a1_L4 | 3937 | 3937 | -16094 |
| ON_VT_a2_L2 | 2155 | 2155 | -39419 |
| ON_VT_a2_L4 | 4309 | 4309 | -8353 |
| ON_PD3_L2 | 816 | 816 | 4871 |
| ON_PD3_L4 | 1633 | 1633 | 9741 |
| ON_PDup_L2 | 256 | 256 | -8779 |
| ON_PDup_L4 | 512 | 512 | -17559 |
| ON_VT_a2+PD5_L2 | 457 | 457 | -1579 |
| ON_VT_a2+PD5_L4 | 915 | 915 | -3158 |
| ON_VT+PD3_L2 | 769 | 769 | -2147 |
| ON_VT+PD3_L4 | 1538 | 1538 | -4294 |
| WK_k0.25_L2 | -1096 | -1096 | -10238 |
| WK_k0.25_L4 | -2191 | -2191 | 26600 |
| WK_k0.75_L2 | -1073 | -1073 | -29307 |
| WK_k0.75_L4 | -2146 | -2146 | -27358 |
| WK_k1.5_L2 | -831 | -831 | -16892 |
| WK_k1.5_L4 | -1663 | -1663 | 38847 |


## Extra IS evidence 2013-01..2023-02-09 (outside WF scoring), unit = 1 lot, after cost
| sleeve | total $ | weekly mean | weekly SD | weekly maxDD | years+/years |
|---|---|---|---|---|---|
| ST10_3_t2 | 26981 | 380 | 2813 | 9579 | 7/11 |
| BO20_t2 | -32271 | -130 | 3261 | 62221 | 4/11 |
| ST10_3_t5 | -10543 | -148 | 3572 | 33614 | 6/11 |
| BO20_t5 | 14812 | 72 | 3991 | 43176 | 6/11 |
| ON_none | 88881 | 168 | 2751 | 78472 | 8/11 |
| ON_VT | 83198 | 174 | 2115 | 47869 | 9/11 |
| ON_PD5 | 33068 | 69 | 1715 | 44111 | 8/11 |
| ON_VT+PD5 | 25141 | 58 | 1655 | 41499 | 9/11 |
| WK_k0.5 | -124323 | -240 | 4466 | 267967 | 6/11 |
| WK_k1.0 | -90480 | -203 | 3773 | 110677 | 2/11 |

Overnight drift positive over 11 earlier years (ON_VT 9/11 years positive, ON_none 8/11); weekly-open breakout negative in both eras; swing sign not stable (ST t2 positive, t5 negative; BO the reverse). The 1d_NQ_v_0 file on disk holds only 5 rows (not usable); history comes from the 1-min file.
