# DS3_THP_C3_PREHOLD - THPC3 stage A, PRE-only (20240201..20250630) IN-SAMPLE selection tables. HOLD and X are not read.

Prereg l2vast/ds3/prereg/THPC3_prereg.md (sha in DECISIONS.md, amendment A1). Warm-up fit-only 20230403..20230630.

## PROFIT: 1234 cells; PRE>0 in 10; White RC p (PRE, all cells) 0.988; per family {"bocpd_adapt": 0.965, "bocpd_fixed": 0.987, "btab": 0.889, "cusum_adapt": 0.949, "cusum_fixed": 0.874, "hmm": 0.769, "ogbm": 0.905, "rlog": 0.977, "rls": 0.985}

cells per family: {"hmm": 640, "rlog": 140, "rls": 100, "btab": 80, "cusum_adapt": 80, "bocpd_adapt": 80, "ogbm": 60, "cusum_fixed": 36, "bocpd_fixed": 18}

Top 10 by PRE (IN-SAMPLE selection): cell | PRE pts/trade [CI] (MDE) | exit rate | placebo ranks (shuffled|random) | failed PRE-gates

* btab|disc0.9995|pooled|z1|m2|take | +0.091 [-0.25,+0.43] (MDE 0.49) | 0.09 | 1.00|0.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05
* hmm|K3|2w|1d|flip|q0.6|a1 | +0.060 [-0.66,+0.78] (MDE 1.02) | 0.38 | nan|0.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05
* btab|disc0.9995|pooled|z1|m1|take | +0.054 [-0.34,+0.45] (MDE 0.57) | 0.12 | 0.90|0.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05
* hmm|K3|2w|1d|flip|q0.85|a1 | +0.034 [-0.66,+0.73] (MDE 0.99) | 0.36 | nan|0.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05
* cusum_adapt|YTD|1m|pooled | +0.024 [-0.52,+0.57] (MDE 0.78) | 0.26 | 0.10|0.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05
* bocpd_adapt|12m|1m|pooled | +0.017 [-0.17,+0.21] (MDE 0.27) | 0.04 | 1.00|0.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05
* cusum_adapt|YTD|1w|pooled | +0.013 [-0.53,+0.56] (MDE 0.78) | 0.27 | 0.10|0.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05
* cusum_fixed|35|{'X': 2, 'k': 2, 'h': 3} | +0.011 [-0.27,+0.29] (MDE 0.40) | 0.06 | nan|0.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05
* bocpd_adapt|12m|1d|pooled | +0.005 [-0.19,+0.20] (MDE 0.27) | 0.04 | 1.00|0.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05
* bocpd_adapt|12m|1w|pooled | +0.000 [-0.19,+0.19] (MDE 0.28) | 0.04 | 0.00|0.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05

Best per family (PRE): 

* bocpd_adapt: bocpd_adapt|12m|1m|pooled +0.017 [-0.17,+0.21] (MDE 0.27)
* bocpd_fixed: bocpd_fixed|17|{'hz': 1, 'p': 2, 'X': 2} -0.196 [-0.48,+0.09] (MDE 0.41)
* btab: btab|disc0.9995|pooled|z1|m2|take +0.091 [-0.25,+0.43] (MDE 0.49)
* cusum_adapt: cusum_adapt|YTD|1m|pooled +0.024 [-0.52,+0.57] (MDE 0.78)
* cusum_fixed: cusum_fixed|35|{'X': 2, 'k': 2, 'h': 3} +0.011 [-0.27,+0.29] (MDE 0.40)
* hmm: hmm|K3|2w|1d|flip|q0.6|a1 +0.060 [-0.66,+0.78] (MDE 1.02)
* ogbm: ogbm|lr0.05|phi0.99|pooled|m8|take -0.252 [-1.06,+0.56] (MDE 1.16)
* rlog: rlog|lr0.02|rho0.99|pooled|m8|take -0.664 [-1.62,+0.29] (MDE 1.36)
* rls: rls|lam0.99|perbook|m0|take -1.128 [-2.31,+0.05] (MDE 1.69)

## LOSS: 1234 cells; PRE>0 in 20; White RC p (PRE, all cells) 0.972; per family {"bocpd_adapt": 0.988, "bocpd_fixed": 0.836, "btab": 1.0, "cusum_adapt": 0.999, "cusum_fixed": 0.997, "hmm": 0.982, "ogbm": 0.665, "rlog": 0.94, "rls": 0.761}

cells per family: {"hmm": 640, "rlog": 140, "rls": 100, "btab": 80, "cusum_adapt": 80, "bocpd_adapt": 80, "ogbm": 60, "cusum_fixed": 36, "bocpd_fixed": 18}

Top 10 by PRE (IN-SAMPLE selection): cell | PRE pts/trade [CI] (MDE) | exit rate | placebo ranks (shuffled|random) | failed PRE-gates

* ogbm|lr0.2|phi0.999|pooled|m8|take | +0.202 [-0.44,+0.84] (MDE 0.91) | 0.33 | 0.00|1.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05
* ogbm|lr0.2|phi0.999|pooled|m4|take | +0.191 [-0.52,+0.90] (MDE 1.01) | 0.40 | 0.00|1.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05
* ogbm|lr0.2|phi0.999|pooled|m1|take | +0.170 [-0.59,+0.93] (MDE 1.08) | 0.44 | 0.00|1.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05
* ogbm|lr0.2|phi0.999|pooled|m2|take | +0.163 [-0.58,+0.90] (MDE 1.06) | 0.43 | 0.00|1.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05
* ogbm|lr0.2|phi0.999|pooled|m1|tt | +0.120 [-0.65,+0.89] (MDE 1.10) | 0.46 | 0.00|1.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05
* ogbm|lr0.2|phi0.999|pooled|m2|tt | +0.093 [-0.66,+0.85] (MDE 1.08) | 0.45 | 0.00|1.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05
* ogbm|lr0.2|phi0.99|pooled|m0|take | +0.085 [-0.63,+0.80] (MDE 1.02) | 0.38 | 0.00|1.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05
* ogbm|lr0.2|phi0.999|pooled|m0|take | +0.082 [-0.69,+0.86] (MDE 1.11) | 0.46 | 0.00|1.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05
* ogbm|lr0.2|phi0.999|pooled|m4|tt | +0.082 [-0.66,+0.82] (MDE 1.06) | 0.44 | 0.00|1.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05
* ogbm|lr0.2|phi0.999|pooled|m0|tt | +0.071 [-0.71,+0.85] (MDE 1.11) | 0.46 | 0.00|1.00 | paired_CI_excludes0,placebo>=0.90,neighbours_agree,RC_p>0.05

Best per family (PRE): 

* bocpd_adapt: bocpd_adapt|12m|1m|pooled -0.132 [-0.58,+0.31] (MDE 0.63)
* bocpd_fixed: bocpd_fixed|17|{'hz': 1, 'p': 2, 'X': 2} -0.040 [-0.49,+0.41] (MDE 0.64)
* btab: btab|disc1.0|pooled|z1|m8|take +0.000 [+0.00,+0.00] (MDE 0.00)
* cusum_adapt: cusum_adapt|12m|1m|pooled -0.253 [-0.69,+0.18] (MDE 0.62)
* cusum_fixed: cusum_fixed|23|{'X': 1, 'k': 2, 'h': 3} -0.416 [-0.98,+0.15] (MDE 0.81)
* hmm: hmm|K3|1w|1w|level|q0.6|a1 -0.351 [-1.06,+0.36] (MDE 1.01)
* ogbm: ogbm|lr0.2|phi0.999|pooled|m8|take +0.202 [-0.44,+0.84] (MDE 0.91)
* rlog: rlog|lr0.02|rho0.99|pooled|m8|take -0.344 [-1.13,+0.44] (MDE 1.12)
* rls: rls|lam0.995|perbook|m8|take +0.047 [-0.55,+0.65] (MDE 0.86)

