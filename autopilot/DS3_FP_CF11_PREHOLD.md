# D3FP confirmation group CF11 (bases ST,KB,PB3B_R5_P1,SBS) PRE-HOLDOUT text 2026-10-28T02:05:19Z
WF-PRE 2024-02..2025-06 keys only (lift = mean(kept) - mean(all) pts/trade, label-day-block bootstrap CI, plc_rank = random-removal rank, wk_d_pre = weekly $ kept book minus base book); WF / HOLD / SPAN2 keys of the result file were NOT read when this text was written.

| cell                     |   take |   n_kept_pre |   n_mirror_pre |   lift_pre | ci              |    mde |   mirror_lift |   win_kept |   win_all |   plc_rank |   wk_d_pre | note                              |
|:-------------------------|-------:|-------------:|---------------:|-----------:|:----------------|-------:|--------------:|-----------:|----------:|-----------:|-----------:|:----------------------------------|
| CF_ST_AB3_3m_k5          |  0.005 |           11 |           3009 |      -7.26 | [-39.57, 24.65] |  44.7  |          0.03 |      0.545 |     0.518 |       0.34 |     -12405 | nan                               |
| CF_ST_AB3_3m_k15         |  0.016 |           43 |           2977 |      -2.3  | [-19.38, 14.86] |  23.74 |          0.03 |      0.512 |     0.518 |       0.37 |     -12311 | nan                               |
| CF_KB_AB3_3m_k5          |  0.01  |           30 |           3063 |      -8.01 | [-27.82, 12.2]  |  28.04 |          0.08 |      0.433 |     0.526 |       0.24 |     -16530 | nan                               |
| CF_KB_AB3_3m_k15         |  0.022 |           65 |           3028 |      -1.21 | [-14.18, 12.52] |  19.14 |          0.03 |      0.508 |     0.526 |       0.45 |     -15950 | nan                               |
| CF_PB3B_R5_P1_AB3_3m_k5  |  0.005 |           11 |           3038 |     -17.16 | [-49.85, 18.66] |  51.17 |          0.06 |      0.364 |     0.51  |       0.16 |      -8478 | nan                               |
| CF_PB3B_R5_P1_AB3_3m_k15 |  0.024 |           62 |           2987 |      -1.46 | [-16.03, 13.61] |  21.63 |          0.03 |      0.5   |     0.51  |       0.42 |      -8200 | nan                               |
| CF_SBS_AB3_3m_k5         |  0.004 |            7 |           1244 |     nan    | nan             | nan    |        nan    |    nan     |   nan     |     nan    |        nan | under 30 kept/mirror trades in WF |
| CF_SBS_AB3_3m_k15        |  0.016 |           20 |           1231 |      -9.7  | [-17.9, -1.03]  |  12.06 |          0.16 |      0.05  |     0.189 |       0.14 |      -4496 | nan                               |
