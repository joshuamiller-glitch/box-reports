# SIZER LEAD REGISTER vs Q1-A (2026-11-03 14:46Z)

Flag rule: cut > 0 on L6M AND PRE vs Q1-A, carrying week dropped still > 0 on both, mean >= Q1-A on L6M and PRE (strict). Candidates are those that also pass no-harm (PA9 band flip-5, where PA9 exists) and are then taken to placebos / equal-risk / exposure. Post-hoc, Shadow only.

7 rows meet the rule; 4 also pass no-harm and 0 also clear the PA9 band (L6M .219, PRE .099).

| program         | cell                                | variant   |   mean_lots |   cut_L6M |   cut_PRE |   cut_HOLD |   cut_MID |   cut_X' |   drop_L6M |   drop_PRE |   dmean_L6M |   dmean_PRE |   pa9_L6M |   pa9_PRE | harm_ok   | label                                      |
|:----------------|:------------------------------------|:----------|------------:|----------:|----------:|-----------:|----------:|---------:|-----------:|-----------:|------------:|------------:|----------:|----------:|:----------|:-------------------------------------------|
| SIZER_S1        | ('g12', 'er_10m_14', 'L3', 'C')     | down      |     nan     |     0.137 |     0.008 |     -0.288 |    -0.613 |   -0.161 |      0.158 |      0.008 |     286.652 |     969.264 |     0.05  |    -0.078 | False     | INSIDE NOISE BAND / FAILS NO-HARM / no PA9 |
| SIZER_S1        | ('g12', 'er_10m_14', 'L3', 'C')     | asis      |     nan     |     0.137 |     0.008 |     -0.288 |    -0.613 |   -0.161 |      0.158 |      0.008 |     286.652 |     969.264 |     0.05  |    -0.078 | False     | INSIDE NOISE BAND / FAILS NO-HARM / no PA9 |
| SIZER_S1        | ('g12', 'er_10m_14', 'L3', 'A')     | down      |     nan     |     0.137 |     0.008 |     -0.288 |    -0.613 |   -0.161 |      0.158 |      0.008 |     286.652 |     969.264 |     0.05  |    -0.078 | False     | INSIDE NOISE BAND / FAILS NO-HARM / no PA9 |
| SIZER_S2V(Q1-A) | P|MV|london|0.5|0.5                 | modifier  |       2.383 |     0.012 |     0.046 |     -0.005 |    -0.055 |    0.015 |      0.022 |      0.054 |     143.855 |      51.44  |     0.035 |     0.054 | True      | INSIDE NOISE BAND / FAILS NO-HARM / no PA9 |
| SIZER_S2V(Q1-A) | V|pk_ratio_20d|LIN|UP|DIR|1.0       | modifier  |       2.427 |     0.011 |     0.04  |      0.038 |     0.027 |   -0.064 |      0.017 |      0.027 |     133.9   |     470.675 |     0.012 |     0.027 | True      | INSIDE NOISE BAND / FAILS NO-HARM / no PA9 |
| SIZER_S2V(Q1-A) | V|range_so_far_ratio|SIG|UP|DIR|1.0 | modifier  |       2.436 |     0.025 |     0.014 |      0.055 |    -0.013 |   -0.048 |      0.004 |      0.007 |     627.93  |     361.187 |     0.033 |     0.007 | True      | INSIDE NOISE BAND / FAILS NO-HARM / no PA9 |
| SIZER_S2V(Q1-A) | V|rv_ratio_30m|LIN|UP|DIR|1.0       | modifier  |       2.427 |     0.001 |     0.022 |      0.049 |     0.049 |   -0.023 |      0.013 |      0.02  |     103.703 |     360.515 |     0.001 |     0.02  | True      | INSIDE NOISE BAND / FAILS NO-HARM / no PA9 |
