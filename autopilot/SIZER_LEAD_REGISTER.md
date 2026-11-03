# SIZER LEAD REGISTER vs Q1-A (2026-11-03 14:21Z)

Flag rule: cut > 0 on L6M AND PRE vs Q1-A, carrying week dropped still > 0 on both, mean >= Q1-A on L6M and PRE (strict). Candidates are those that also pass no-harm (PA9 band flip-5, where PA9 exists) and are then taken to placebos / equal-risk / exposure. Post-hoc, Shadow only.

3 rows meet the rule; 3 also pass no-harm and 0 also clear the PA9 band (L6M .219, PRE .099).

| program         | cell                                | variant   |   mean_lots |   cut_L6M |   cut_PRE |   cut_HOLD |   cut_MID |   cut_X' |   drop_L6M |   drop_PRE |   dmean_L6M |   dmean_PRE |   pa9_L6M |   pa9_PRE | harm_ok   | label                                      |
|:----------------|:------------------------------------|:----------|------------:|----------:|----------:|-----------:|----------:|---------:|-----------:|-----------:|------------:|------------:|----------:|----------:|:----------|:-------------------------------------------|
| SIZER_S2V(Q1-A) | V|pk_ratio_20d|LIN|UP|DIR|1.0       | modifier  |       2.427 |     0.011 |     0.04  |      0.038 |     0.027 |   -0.064 |      0.017 |      0.027 |     133.9   |     470.675 |     0.012 |     0.027 | True      | INSIDE NOISE BAND / FAILS NO-HARM / no PA9 |
| SIZER_S2V(Q1-A) | V|range_so_far_ratio|SIG|UP|DIR|1.0 | modifier  |       2.436 |     0.025 |     0.014 |      0.055 |    -0.013 |   -0.048 |      0.004 |      0.007 |     627.93  |     361.187 |     0.033 |     0.007 | True      | INSIDE NOISE BAND / FAILS NO-HARM / no PA9 |
| SIZER_S2V(Q1-A) | V|rv_ratio_30m|LIN|UP|DIR|1.0       | modifier  |       2.427 |     0.001 |     0.022 |      0.049 |     0.049 |   -0.023 |      0.013 |      0.02  |     103.703 |     360.515 |     0.001 |     0.02  | True      | INSIDE NOISE BAND / FAILS NO-HARM / no PA9 |
