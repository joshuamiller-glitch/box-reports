# DS3_ORB_RSI2_COMPLETE - D1's three open items, completed under DRAWDOWN FIRST (A12, 2026-11-01)

**COMPLETION of D1 (DS3_ORB_ASIA_D7), not a holdout. POST-HOC. Shadow/paper only. No PASS claim.** Selection windows are D1's; every sleeve/cell is the one D1 chose. Prereg `l2vast/ds3/prereg/A12_ORBRSI2_COMPLETE_prereg.md` sha256 f039b38d6e5d07422808d56f80376a9ec81810422f874883c9a371173130a14c (in DECISIONS.md before any A12 statistic; dead_lookup first: sleeves/cells EXACT in RE5_STRUCT48 / D1_ORB (scored on the mean), ORB_ASIA_15 and GSHORT_t90 NOT FOUND; DEAD_CELLS appended after, never rebuilt). Cap label day 20260206. Engine = oc_lib / dd_lib unchanged, live lots; tie-out of the lock-stash to the stored COMP|{off,12R,20R,30R} and ASIS|{off,12R,20R,30R} series: max daily diff 0.0 (<=3e-11). NQ fees are PROXIES in FEES.md (exchange+NFA not published): every NQ result is capped at CANDIDATE. ES uses the NT-published $4.84 RT standard (not a proxy) but is also held at CANDIDATE here (post-hoc, new placebo). Windows L3M 14 / L6M 28 / HOLD 32 / PRE 75 / X' 44 / ALL 149 weeks; maxDD $k weekly-cumulative; worst-20 only shown where >= 40 weeks (PRE, X', ALL). Composite L6M maxDD (23k) is the single week 2026-01-19, so a sleeve cannot cut it.

## BOTTOM LINE
1. **0 of 656 scored rows (11 sleeves/cells x lots x 2 frames x 4 lock states x 2 routings) is a full RISK-KEEP** (L6M maxDD cut >= 20% with mean inside MDE AND placebo beaten AND PRE and X' both cut >= 20%): tiers {'NO': 593, 'VOLUME-EFFECT': 31, 'L6M-ONLY': 24, 'PRE/X-CUT-ONLY': 8}. Nothing is promoted.
2. **(a) ES RSI2_t10 placebo (new, ES bars from cache_te2):** real per-contract weekly mean ranks 0.990 vs 200 same-count random-day placebos in PRE+X', 0.980 PRE, 0.875 X', 0.995 HOLD and L6M, 1.000 ALL: it clears 0.95 everywhere except X' (0.875). NQ RSI2_t10 re-derived with contract-roll pairs excluded: 0.950 PRE+X' (D1: 0.945). **GSHORT_t90** random-day rank 0.735 PRE+X' (D1 0.705) and 0.87 when the placebo days are drawn only where the stack's trailing-4-week P&L < 0 (gate on): the RSI>90 trigger adds nothing demonstrable beyond the stack-loss gate. Risk-level placebo (added to the composite, no lock): ES 8.6 lots COMP rank_dd L6M/PRE/X'/ALL = 0.17/0.17/0.00/0.17; ASIS rank_dd L6M/PRE/X'/ALL = 0.04/0.17/0.00/0.00.
3. **(b) Direct basis:** only 2 of the 5 program cells have a complete direct L2 replay (both PB7 cells, 99.8% of capped trades replayed; D1 had them as mapped). On direct the recent means are much lower than mapped: PB7 HMA55 W60 s-3 L3M/L6M/HOLD $834/$1,764/$1,754 per contract-week (mapped 1,211/2,064/1,930); PB7 PB5 depth W15 s-3 $230/$1,411/$1,286 (mapped 1,238/2,188/2,020, L3M ratio 0.19). **TB4A_time_03 'direct' has only 2% replay coverage (D1 listed it as mapped-eligible: it is effectively MAPPED); TB4W_10 has 6 of 37 months; TR3_DON15_S has none**: their direct replay (9,590 trades) is frozen by the replay governor's priority mode (SIGSTOP of every non-priority orchestrator, gov_priority.on, user ruling 2026-10-27). I did not evade it; rows + script are ready (STRUCTURAL QUESTION in MORNING.md). Those three rows are MAPPED-labelled, blind routing only. At 5-10 lots every program cell deepens the composite tail (table in section 4); none is RISK-KEEP.
4. **(c) Lock interplay:** the sleeve's drawdown value is real only without the lock. NQ IBS 4.2 lots on the composite (A4's lead, tie-out PRE 241->155, X' 121->79 reproduced) cuts PRE 36% / X' 34% without a lock (placebo rank 0.00 / 0.04); routed into the combined lock it keeps PRE 16% / X' 35% at 20R and PRE 12% / X' 35% at 30R, but at 12R PRE 18% with X' turning into an 18% deepening (120 -> 142). RSI2 sleeves (NQ, NQRSI2C, ES): with the lock seeing them (R2) the PRE cut disappears at every lock multiple (the lock cancels 30 of ~72 RSI2 entries at 12R) and the X' cut survives only at 20R/30R (NQ +26..30%, ES +19%); at 12R it is gone (0..7%). ORB: no drawdown value at any lot or lock; at 17.2 lots the routed lock makes X' maxDD 121 -> 323 (12R) / 316 (20R).
5. Routing matters in both directions: the lock fires in 70-83 of 149 weeks at 12R, so a sleeve inside the lock loses about 40% of its entries at 12R (NQ RSI2: 30 of 72 cancelled at 12R, 16 at 20R, 10 at 30R); the lock also changes the STACK's own P&L when the sleeve's MTM tips it earlier (butterfly effect, e.g. ORB 17.2 lots X' stack maxDD).

## PAGE 1 - sleeve | lots | no-lock / 12R / 20R / 30R maxDD before->after by window | placebo rank | RISK-KEEP
Composite = Sunday composite (six pieces). Cells are $k maxDD base->after in L6M, PRE, X', ALL. **Routing: none = sleeve added to the unlocked stack; 12R/20R/30R for the NQ/ES sleeves and the two direct PB7 cells = R2 (the sleeve's open MTM and realised P&L are inside the combined week lock; on a fire its open positions are flattened at the mark of ks+1 and its later entries of that week are cancelled); the three MAPPED cells (TB4A, TB4W, TR3) = R1 (sleeve P&L added unchanged to the locked stack).** Placebo = 200 same-count random-time draws pushed through the SAME routing; rank_dd = share of placebo draws with a smaller maxDD change (<= 0.05 beats chance; four values per cell: none · 12R · 20R · 30R). Tiers: FULL / L6M-ONLY (L6M cut + mean ok + placebo beaten, PRE or X' disagree) / VOLUME-EFFECT (cut but placebo not beaten) / PRE/X-CUT-ONLY / NO.

### Composite
| sleeve | lots | no-lock | 12R | 20R | 30R | placebo rank_dd (L6M/PRE/X'/ALL), no-lock · 12R · 20R · 30R | RISK-KEEP none / 12R / 20R / 30R |
|---|---|---|---|---|---|---|---|
| ORB_ASIA_15 s60 (LIVE-CAL, NQ) | 1 | L6M 23→23 · PRE 241→243 · X' 121→121 · ALL 241→243 | L6M 27→25 · PRE 233→232 · X' 120→121 · ALL 233→232 | L6M 64→64 · PRE 190→190 · X' 133→136 · ALL 190→190 | L6M 37→37 · PRE 208→209 · X' 133→135 · ALL 208→209 | 0.26/0.68/0.57/0.67 · 0.01/0.28/0.67/0.28 · 0.35/0.42/1.00/0.42 · 0.06/0.45/0.97/0.45 | NO / NO / NO / NO |
| ORB_ASIA_15 s60 (LIVE-CAL, NQ) | 3 | L6M 23→23 · PRE 241→247 · X' 121→121 · ALL 241→247 | L6M 27→23 · PRE 233→229 · X' 120→123 · ALL 233→229 | L6M 64→64 · PRE 190→173 · X' 133→118 · ALL 190→173 | L6M 37→37 · PRE 208→210 · X' 133→140 · ALL 208→210 | 0.21/0.64/0.53/0.63 · 0.01/0.23/0.67/0.23 · 0.36/0.07/0.00/0.07 · 0.12/0.41/0.82/0.41 | NO / NO / NO / NO |
| ORB_ASIA_15 s60 (LIVE-CAL, NQ) | 5 | L6M 23→23 · PRE 241→251 · X' 121→122 · ALL 241→251 | L6M 27→23 · PRE 233→229 · X' 120→204 · ALL 233→229 | L6M 64→64 · PRE 190→180 · X' 133→135 · ALL 190→180 | L6M 37→37 · PRE 208→212 · X' 133→155 · ALL 208→212 | 0.20/0.62/0.47/0.63 · 0.01/0.38/0.97/0.38 · 0.36/0.22/0.51/0.22 · 0.12/0.57/0.83/0.56 | NO / NO / NO / NO |
| ORB_ASIA_15 s60 (LIVE-CAL, NQ) | 17.2 | L6M 23→23 · PRE 241→276 · X' 121→153 · ALL 241→276 | L6M 27→31 · PRE 233→216 · X' 120→323 · ALL 233→363 | L6M 64→64 · PRE 190→209 · X' 133→316 · ALL 190→335 | L6M 37→41 · PRE 208→248 · X' 133→186 · ALL 208→248 | 0.04/0.56/0.59/0.56 · 0.13/0.29/0.96/0.96 · 0.30/0.39/0.94/0.86 · 0.40/0.43/0.65/0.40 | NO / NO / NO / NO |
| NQ RSI2_t10 | 1 | L6M 23→23 · PRE 241→237 · X' 121→113 · ALL 241→237 | L6M 27→23 · PRE 233→233 · X' 120→120 · ALL 233→233 | L6M 64→64 · PRE 190→190 · X' 133→126 · ALL 190→190 | L6M 37→37 · PRE 208→208 · X' 133→126 · ALL 208→208 | 0.26/0.33/0.02/0.33 · 0.00/0.30/0.36/0.33 · 0.20/0.55/0.01/0.57 · 0.03/0.54/0.01/0.54 | NO / NO / NO / NO |
| NQ RSI2_t10 | 3 | L6M 23→23 · PRE 241→228 · X' 121→99 · ALL 241→228 | L6M 27→23 · PRE 233→233 · X' 120→120 · ALL 233→233 | L6M 64→64 · PRE 190→190 · X' 133→112 · ALL 190→190 | L6M 37→37 · PRE 208→208 · X' 133→112 · ALL 208→208 | 0.18/0.26/0.02/0.26 · 0.01/0.42/0.62/0.38 · 0.09/0.46/0.01/0.48 · 0.03/0.47/0.01/0.51 | NO / NO / NO / NO |
| NQ RSI2_t10 | 5.2 | L6M 23→23 · PRE 241→219 · X' 121→84 · ALL 241→219 | L6M 27→23 · PRE 233→233 · X' 120→120 · ALL 233→233 | L6M 64→64 · PRE 190→190 · X' 133→99 · ALL 190→190 | L6M 37→37 · PRE 208→208 · X' 133→96 · ALL 208→208 | 0.12/0.23/0.01/0.23 · 0.01/0.50/0.31/0.53 · 0.14/0.36/0.01/0.35 · 0.02/0.36/0.00/0.37 | NO / NO / NO / NO |
| NQ RSI2C_s20 | 1 | L6M 23→23 · PRE 241→237 · X' 121→113 · ALL 241→237 | L6M 27→23 · PRE 233→233 · X' 120→120 · ALL 233→233 | L6M 64→64 · PRE 190→190 · X' 133→126 · ALL 190→190 | L6M 37→37 · PRE 208→208 · X' 133→126 · ALL 208→208 | 0.30/0.26/0.05/0.26 · 0.00/0.29/0.37/0.31 · 0.19/0.52/0.01/0.53 · 0.07/0.56/0.03/0.55 | NO / NO / NO / NO |
| NQ RSI2C_s20 | 3 | L6M 23→23 · PRE 241→228 · X' 121→99 · ALL 241→228 | L6M 27→23 · PRE 233→233 · X' 120→120 · ALL 233→233 | L6M 64→64 · PRE 190→190 · X' 133→112 · ALL 190→190 | L6M 37→37 · PRE 208→208 · X' 133→112 · ALL 208→208 | 0.23/0.22/0.04/0.22 · 0.00/0.37/0.57/0.34 · 0.07/0.39/0.01/0.41 · 0.04/0.49/0.03/0.51 | NO / NO / NO / NO |
| NQ RSI2C_s20 | 6.7 | L6M 23→39 · PRE 241→212 · X' 121→78 · ALL 241→212 | L6M 27→39 · PRE 233→233 · X' 120→120 · ALL 233→233 | L6M 64→64 · PRE 190→190 · X' 133→99 · ALL 190→190 | L6M 37→39 · PRE 208→208 · X' 133→93 · ALL 208→208 | 0.39/0.14/0.03/0.14 · 0.42/0.51/0.46/0.50 · 0.14/0.28/0.03/0.27 · 0.50/0.30/0.03/0.30 | NO / NO / NO / NO |
| ES RSI2_t10 | 1 | L6M 23→23 · PRE 241→238 · X' 121→114 · ALL 241→238 | L6M 27→24 · PRE 233→233 · X' 120→118 · ALL 233→233 | L6M 64→64 · PRE 190→190 · X' 133→130 · ALL 190→190 | L6M 37→37 · PRE 208→208 · X' 133→130 · ALL 208→208 | 0.27/0.26/0.03/0.26 · 0.05/0.23/0.12/0.25 · 0.17/0.59/0.08/0.65 · 0.48/0.59/0.10/0.59 | NO / NO / NO / NO |
| ES RSI2_t10 | 3 | L6M 23→23 · PRE 241→232 · X' 121→101 · ALL 241→232 | L6M 27→23 · PRE 233→233 · X' 120→114 · ALL 233→233 | L6M 64→64 · PRE 190→190 · X' 133→124 · ALL 190→190 | L6M 37→37 · PRE 208→208 · X' 133→124 · ALL 208→208 | 0.24/0.26/0.03/0.26 · 0.00/0.24/0.17/0.33 · 0.17/0.60/0.07/0.58 · 0.42/0.54/0.09/0.52 | NO / NO / NO / NO |
| ES RSI2_t10 | 8.6 | L6M 23→23 · PRE 241→216 · X' 121→66 · ALL 241→216 | L6M 27→23 · PRE 233→233 · X' 120→111 · ALL 233→233 | L6M 64→64 · PRE 190→190 · X' 133→108 · ALL 190→190 | L6M 37→37 · PRE 208→208 · X' 133→108 · ALL 208→208 | 0.17/0.17/0.00/0.17 · 0.00/0.27/0.01/0.34 · 0.17/0.39/0.10/0.38 · 0.35/0.41/0.06/0.41 | NO / NO / NO / NO |
| NQ IBS_t20_n1 | 1 | L6M 23→23 · PRE 241→219 · X' 121→111 · ALL 241→219 | L6M 27→23 · PRE 233→223 · X' 120→147 · ALL 233→223 | L6M 64→63 · PRE 190→176 · X' 133→122 · ALL 190→176 | L6M 37→37 · PRE 208→194 · X' 133→122 · ALL 208→194 | 0.36/0.01/0.11/0.01 · 0.00/0.00/0.87/0.00 · 0.20/0.02/0.04/0.02 · 0.49/0.03/0.06/0.03 | NO / NO / NO / NO |
| NQ IBS_t20_n1 | 3 | L6M 23→23 · PRE 241→177 · X' 121→91 · ALL 241→177 | L6M 27→23 · PRE 233→203 · X' 120→144 · ALL 233→203 | L6M 64→59 · PRE 190→158 · X' 133→100 · ALL 190→158 | L6M 37→37 · PRE 208→179 · X' 133→100 · ALL 208→179 | 0.28/0.00/0.07/0.00 · 0.00/0.04/0.78/0.04 · 0.10/0.04/0.04/0.03 · 0.30/0.03/0.06/0.03 | PRE/X-CUT-ONLY / NO / NO / NO |
| NQ IBS_t20_n1 | 3.9 | L6M 23→23 · PRE 241→161 · X' 121→82 · ALL 241→161 | L6M 27→23 · PRE 233→194 · X' 120→142 · ALL 233→194 | L6M 64→58 · PRE 190→159 · X' 133→90 · ALL 190→159 | L6M 37→37 · PRE 208→181 · X' 133→90 · ALL 208→181 | 0.21/0.00/0.06/0.00 · 0.01/0.04/0.71/0.04 · 0.21/0.10/0.04/0.07 · 0.36/0.07/0.04/0.07 | PRE/X-CUT-ONLY / NO / NO / NO |
| NQ IBS_t20_n1 | 4.2 | L6M 23→23 · PRE 241→155 · X' 121→79 · ALL 241→155 | L6M 27→23 · PRE 233→191 · X' 120→142 · ALL 233→191 | L6M 64→58 · PRE 190→160 · X' 133→86 · ALL 190→160 | L6M 37→37 · PRE 208→182 · X' 133→86 · ALL 208→182 | 0.21/0.00/0.04/0.00 · 0.01/0.03/0.70/0.03 · 0.21/0.11/0.04/0.07 · 0.36/0.10/0.03/0.10 | PRE/X-CUT-ONLY / NO / NO / NO |
| NQ GSHORT_t90 | 1 | L6M 23→21 · PRE 241→241 · X' 121→125 · ALL 241→241 | L6M 27→27 · PRE 233→231 · X' 120→117 · ALL 233→231 | L6M 64→64 · PRE 190→189 · X' 133→133 · ALL 190→189 | L6M 37→37 · PRE 208→207 · X' 133→137 · ALL 208→207 | 0.00/0.34/0.74/0.34 · 0.00/0.03/0.11/0.03 · 0.21/0.12/0.41/0.12 · 0.00/0.20/0.80/0.20 | NO / NO / NO / NO |
| NQ GSHORT_t90 | 3 | L6M 23→21 · PRE 241→239 · X' 121→133 · ALL 241→239 | L6M 27→27 · PRE 233→237 · X' 120→112 · ALL 233→237 | L6M 64→64 · PRE 190→186 · X' 133→133 · ALL 190→186 | L6M 37→37 · PRE 208→205 · X' 133→146 · ALL 208→205 | 0.00/0.32/0.70/0.32 · 0.00/0.75/0.09/0.75 · 0.28/0.10/0.32/0.10 · 0.00/0.17/0.71/0.17 | NO / NO / NO / NO |
| NQ GSHORT_t90 | 5 | L6M 23→21 · PRE 241→238 · X' 121→141 · ALL 241→238 | L6M 27→27 · PRE 233→234 · X' 120→111 · ALL 233→234 | L6M 64→64 · PRE 190→185 · X' 133→133 · ALL 190→185 | L6M 37→37 · PRE 208→203 · X' 133→154 · ALL 208→203 | 0.00/0.29/0.69/0.29 · 0.00/0.60/0.02/0.60 · 0.25/0.09/0.28/0.08 · 0.00/0.12/0.62/0.12 | NO / NO / NO / NO |
| NQ GSHORT_t90 | 15.6 | L6M 23→21 · PRE 241→231 · X' 121→186 · ALL 241→231 | L6M 27→65 · PRE 233→222 · X' 120→200 · ALL 233→222 | L6M 64→64 · PRE 190→173 · X' 133→133 · ALL 190→173 | L6M 37→72 · PRE 208→193 · X' 133→207 · ALL 208→207 | 0.00/0.14/0.58/0.10 · 0.54/0.04/0.75/0.03 · 0.12/0.01/0.16/0.01 · 0.53/0.05/0.67/0.04 | NO / NO / NO / NO |
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 1 | L6M 23→24 · PRE 241→250 · X' 121→125 · ALL 241→250 | L6M 27→43 · PRE 233→240 · X' 120→147 · ALL 233→240 | L6M 64→26 · PRE 190→192 · X' 133→107 · ALL 190→192 | L6M 37→37 · PRE 208→218 · X' 133→129 · ALL 208→218 | 0.28/0.38/0.38/0.38 · 0.62/0.51/0.46/0.51 · 0.17/0.33/0.14/0.33 · 0.45/0.57/0.14/0.57 | NO / NO / VOLUME-EFFECT / NO |
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 3 | L6M 23→31 · PRE 241→268 · X' 121→135 · ALL 241→268 | L6M 27→72 · PRE 233→231 · X' 120→151 · ALL 233→231 | L6M 64→49 · PRE 190→180 · X' 133→113 · ALL 190→180 | L6M 37→103 · PRE 208→238 · X' 133→143 · ALL 208→238 | 0.21/0.33/0.28/0.32 · 0.93/0.46/0.17/0.27 · 0.54/0.11/0.10/0.07 · 0.99/0.36/0.19/0.31 | NO / NO / VOLUME-EFFECT / NO |
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 5 | L6M 23→60 · PRE 241→290 · X' 121→145 · ALL 241→290 | L6M 27→74 · PRE 233→244 · X' 120→160 · ALL 233→244 | L6M 64→54 · PRE 190→283 · X' 133→123 · ALL 190→283 | L6M 37→113 · PRE 208→262 · X' 133→137 · ALL 208→262 | 0.47/0.27/0.18/0.20 · 0.58/0.43/0.08/0.11 · 0.31/0.47/0.04/0.28 · 0.94/0.28/0.09/0.15 | NO / NO / NO / NO |
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 10 | L6M 23→133 · PRE 241→346 · X' 121→173 · ALL 241→346 | L6M 27→87 · PRE 233→308 · X' 120→197 · ALL 233→308 | L6M 64→77 · PRE 190→398 · X' 133→260 · ALL 190→398 | L6M 37→161 · PRE 208→425 · X' 133→147 · ALL 208→425 | 0.41/0.10/0.04/0.01 · 0.12/0.28/0.04/0.04 · 0.05/0.40/0.18/0.14 · 0.65/0.34/0.00/0.12 | NO / NO / NO / NO |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 1 | L6M 23→26 · PRE 241→237 · X' 121→128 · ALL 241→237 | L6M 27→44 · PRE 233→240 · X' 120→145 · ALL 233→240 | L6M 64→26 · PRE 190→189 · X' 133→109 · ALL 190→189 | L6M 37→36 · PRE 208→211 · X' 133→139 · ALL 208→211 | 0.40/0.20/0.53/0.20 · 0.89/0.47/0.41/0.47 · 0.25/0.28/0.14/0.28 · 0.10/0.39/0.29/0.39 | NO / NO / VOLUME-EFFECT / NO |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 3 | L6M 23→33 · PRE 241→229 · X' 121→145 · ALL 241→229 | L6M 27→43 · PRE 233→220 · X' 120→221 · ALL 233→221 | L6M 64→37 · PRE 190→210 · X' 133→197 · ALL 190→210 | L6M 37→37 · PRE 208→208 · X' 133→212 · ALL 208→212 | 0.24/0.14/0.39/0.14 · 0.19/0.37/0.57/0.22 · 0.36/0.36/0.66/0.28 · 0.34/0.18/0.72/0.16 | NO / NO / VOLUME-EFFECT / NO |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 5 | L6M 23→46 · PRE 241→221 · X' 121→167 · ALL 241→221 | L6M 27→58 · PRE 233→218 · X' 120→339 · ALL 233→339 | L6M 64→53 · PRE 190→329 · X' 133→259 · ALL 190→329 | L6M 37→102 · PRE 208→199 · X' 133→184 · ALL 208→199 | 0.21/0.10/0.34/0.07 · 0.34/0.35/0.78/0.68 · 0.34/0.71/0.61/0.56 · 0.91/0.06/0.30/0.01 | NO / NO / NO / NO |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 10 | L6M 23→95 · PRE 241→242 · X' 121→221 · ALL 241→242 | L6M 27→80 · PRE 233→230 · X' 120→356 · ALL 233→356 | L6M 64→73 · PRE 190→369 · X' 133→246 · ALL 190→369 | L6M 37→72 · PRE 208→288 · X' 133→295 · ALL 208→295 | 0.17/0.03/0.14/0.00 · 0.12/0.10/0.52/0.20 · 0.07/0.35/0.19/0.14 · 0.04/0.10/0.29/0.02 | NO / NO / NO / NO |
| TB4A time 30s ST3 SW38 T2 (MAPPED) | 1 | L6M 23→28 · PRE 241→254 · X' 121→125 · ALL 241→254 | L6M 27→26 · PRE 233→235 · X' 120→127 · ALL 233→235 | L6M 64→55 · PRE 190→192 · X' 133→138 · ALL 190→192 | L6M 37→39 · PRE 208→216 · X' 133→138 · ALL 208→216 | 0.42/0.41/0.39/0.41 · 0.06/0.17/0.33/0.17 · 0.07/0.07/0.27/0.07 · 0.26/0.20/0.32/0.20 | NO / NO / NO / NO |
| TB4A time 30s ST3 SW38 T2 (MAPPED) | 3 | L6M 23→40 · PRE 241→279 · X' 121→135 · ALL 241→279 | L6M 27→34 · PRE 233→239 · X' 120→141 · ALL 233→239 | L6M 64→40 · PRE 190→197 · X' 133→147 · ALL 190→197 | L6M 37→43 · PRE 208→232 · X' 133→147 · ALL 208→232 | 0.29/0.30/0.28/0.29 · 0.01/0.09/0.12/0.05 · 0.00/0.02/0.20/0.01 · 0.11/0.06/0.22/0.05 | NO / NO / L6M-ONLY / NO |
| TB4A time 30s ST3 SW38 T2 (MAPPED) | 5 | L6M 23→52 · PRE 241→304 · X' 121→144 · ALL 241→304 | L6M 27→46 · PRE 233→254 · X' 120→173 · ALL 233→254 | L6M 64→52 · PRE 190→204 · X' 133→157 · ALL 190→204 | L6M 37→52 · PRE 208→248 · X' 133→157 · ALL 208→248 | 0.14/0.20/0.14/0.15 · 0.01/0.04/0.10/0.01 · 0.01/0.01/0.10/0.00 · 0.07/0.03/0.10/0.01 | NO / NO / NO / NO |
| TB4A time 30s ST3 SW38 T2 (MAPPED) | 10 | L6M 23→84 · PRE 241→366 · X' 121→174 · ALL 241→366 | L6M 27→77 · PRE 233→305 · X' 120→268 · ALL 233→305 | L6M 64→84 · PRE 190→265 · X' 133→187 · ALL 190→275 | L6M 37→84 · PRE 208→296 · X' 133→187 · ALL 208→317 | 0.01/0.05/0.02/0.01 · 0.00/0.00/0.07/0.00 · 0.00/0.00/0.01/0.00 · 0.01/0.00/0.02/0.00 | NO / NO / NO / NO |
| TB4W_10 volume500 ST10 (MAPPED) | 1 | L6M 23→34 · PRE 241→238 · X' 121→133 · ALL 241→238 | L6M 27→27 · PRE 233→226 · X' 120→123 · ALL 233→226 | L6M 64→68 · PRE 190→184 · X' 133→145 · ALL 190→184 | L6M 37→39 · PRE 208→205 · X' 133→146 · ALL 208→205 | 0.69/0.11/0.55/0.11 · 0.06/0.07/0.28/0.07 · 0.57/0.02/0.38/0.02 · 0.20/0.04/0.42/0.04 | NO / NO / NO / NO |
| TB4W_10 volume500 ST10 (MAPPED) | 3 | L6M 23→58 · PRE 241→233 · X' 121→158 · ALL 241→233 | L6M 27→52 · PRE 233→214 · X' 120→148 · ALL 233→214 | L6M 64→86 · PRE 190→172 · X' 133→170 · ALL 190→172 | L6M 37→58 · PRE 208→199 · X' 133→171 · ALL 208→199 | 0.50/0.06/0.35/0.04 · 0.18/0.01/0.12/0.01 · 0.43/0.00/0.28/0.00 · 0.28/0.01/0.31/0.01 | NO / NO / NO / NO |
| TB4W_10 volume500 ST10 (MAPPED) | 5 | L6M 23→83 · PRE 241→227 · X' 121→186 · ALL 241→227 | L6M 27→76 · PRE 233→204 · X' 120→172 · ALL 233→204 | L6M 64→108 · PRE 190→175 · X' 133→195 · ALL 190→195 | L6M 37→83 · PRE 208→194 · X' 133→198 · ALL 208→198 | 0.33/0.01/0.30/0.00 · 0.11/0.01/0.09/0.00 · 0.23/0.00/0.20/0.00 · 0.21/0.00/0.26/0.00 | NO / NO / NO / NO |
| TB4W_10 volume500 ST10 (MAPPED) | 10 | L6M 23→144 · PRE 241→277 · X' 121→259 · ALL 241→277 | L6M 27→138 · PRE 233→199 · X' 120→233 · ALL 233→233 | L6M 64→165 · PRE 190→245 · X' 133→258 · ALL 190→258 | L6M 37→151 · PRE 208→247 · X' 133→271 · ALL 208→271 | 0.07/0.00/0.10/0.00 · 0.04/0.00/0.04/0.00 · 0.07/0.00/0.06/0.00 · 0.07/0.00/0.10/0.00 | NO / NO / NO / NO |
| TR3_DON15_S (MAPPED) | 1 | L6M 23→23 · PRE 241→234 · X' 121→130 · ALL 241→234 | L6M 27→28 · PRE 233→215 · X' 120→129 · ALL 233→215 | L6M 64→59 · PRE 190→172 · X' 133→142 · ALL 190→172 | L6M 37→41 · PRE 208→195 · X' 133→142 · ALL 208→195 | 0.20/0.14/0.56/0.14 · 0.23/0.05/0.37/0.05 · 0.11/0.01/0.41/0.01 · 0.46/0.06/0.53/0.06 | NO / NO / NO / NO |
| TR3_DON15_S (MAPPED) | 3 | L6M 23→24 · PRE 241→228 · X' 121→149 · ALL 241→228 | L6M 27→37 · PRE 233→186 · X' 120→146 · ALL 233→186 | L6M 64→54 · PRE 190→185 · X' 133→161 · ALL 190→185 | L6M 37→50 · PRE 208→204 · X' 133→161 · ALL 208→204 | 0.04/0.10/0.45/0.10 · 0.07/0.03/0.15/0.01 · 0.10/0.05/0.28/0.01 · 0.34/0.07/0.33/0.05 | NO / NO / NO / NO |
| TR3_DON15_S (MAPPED) | 5 | L6M 23→30 · PRE 241→237 · X' 121→168 · ALL 241→237 | L6M 27→46 · PRE 233→189 · X' 120→164 · ALL 233→189 | L6M 64→56 · PRE 190→211 · X' 133→180 · ALL 190→211 | L6M 37→60 · PRE 208→230 · X' 133→181 · ALL 208→230 | 0.03/0.09/0.31/0.06 · 0.03/0.03/0.07/0.01 · 0.04/0.07/0.22/0.01 · 0.19/0.09/0.26/0.04 | NO / NO / NO / NO |
| TR3_DON15_S (MAPPED) | 10 | L6M 23→50 · PRE 241→262 · X' 121→224 · ALL 241→299 | L6M 27→69 · PRE 233→247 · X' 120→221 · ALL 233→247 | L6M 64→70 · PRE 190→275 · X' 133→229 · ALL 190→275 | L6M 37→82 · PRE 208→294 · X' 133→236 · ALL 208→294 | 0.01/0.04/0.10/0.01 · 0.00/0.01/0.03/0.00 · 0.01/0.01/0.07/0.01 · 0.05/0.03/0.09/0.01 | NO / NO / NO / NO |

### As-is stack
| sleeve | lots | no-lock | 12R | 20R | 30R | placebo rank_dd (L6M/PRE/X'/ALL), no-lock · 12R · 20R · 30R | RISK-KEEP none / 12R / 20R / 30R |
|---|---|---|---|---|---|---|---|
| ORB_ASIA_15 s60 (LIVE-CAL, NQ) | 1 | L6M 88→86 · PRE 162→165 · X' 317→324 · ALL 317→324 | L6M 116→116 · PRE 276→234 · X' 436→466 · ALL 436→466 | L6M 96→96 · PRE 229→228 · X' 463→469 · ALL 463→469 | L6M 73→73 · PRE 145→146 · X' 318→324 · ALL 318→324 | 0.10/0.73/0.80/0.80 · 0.07/0.01/0.67/0.67 · 0.15/0.24/0.62/0.62 · 0.78/0.71/0.73/0.73 | NO / NO / NO / NO |
| ORB_ASIA_15 s60 (LIVE-CAL, NQ) | 3 | L6M 88→83 · PRE 162→172 · X' 317→338 · ALL 317→338 | L6M 116→116 · PRE 276→244 · X' 436→475 · ALL 436→475 | L6M 96→96 · PRE 229→228 · X' 463→485 · ALL 463→485 | L6M 73→72 · PRE 145→145 · X' 318→335 · ALL 318→335 | 0.10/0.71/0.80/0.80 · 0.17/0.09/0.67/0.62 · 0.19/0.24/0.56/0.56 · 0.36/0.46/0.62/0.62 | NO / NO / NO / NO |
| ORB_ASIA_15 s60 (LIVE-CAL, NQ) | 5 | L6M 88→79 · PRE 162→179 · X' 317→352 · ALL 317→352 | L6M 116→116 · PRE 276→326 · X' 436→547 · ALL 436→574 | L6M 96→96 · PRE 229→226 · X' 463→501 · ALL 463→501 | L6M 73→72 · PRE 145→145 · X' 318→351 · ALL 318→351 | 0.10/0.71/0.79/0.79 · 0.21/0.76/0.93/0.88 · 0.14/0.19/0.65/0.64 · 0.41/0.20/0.64/0.64 | NO / NO / NO / NO |
| ORB_ASIA_15 s60 (LIVE-CAL, NQ) | 17.2 | L6M 88→58 · PRE 162→219 · X' 317→440 · ALL 317→440 | L6M 116→116 · PRE 276→314 · X' 436→641 · ALL 436→721 | L6M 96→96 · PRE 229→221 · X' 463→645 · ALL 463→645 | L6M 73→58 · PRE 145→232 · X' 318→547 · ALL 318→547 | 0.07/0.63/0.78/0.77 · 0.16/0.38/0.94/0.80 · 0.47/0.14/0.83/0.69 · 0.06/0.62/0.90/0.89 | VOLUME-EFFECT / NO / NO / VOLUME-EFFECT |
| NQ RSI2_t10 | 1 | L6M 88→81 · PRE 162→158 · X' 317→307 · ALL 317→307 | L6M 116→116 · PRE 276→270 · X' 436→435 · ALL 436→435 | L6M 96→96 · PRE 229→229 · X' 463→461 · ALL 463→461 | L6M 73→72 · PRE 145→145 · X' 318→308 · ALL 318→308 | 0.07/0.33/0.15/0.15 · 0.00/0.48/0.48/0.47 · 0.09/0.69/0.56/0.56 · 0.23/0.12/0.13/0.13 | NO / NO / NO / NO |
| NQ RSI2_t10 | 3 | L6M 88→68 · PRE 162→149 · X' 317→287 · ALL 317→287 | L6M 116→116 · PRE 276→260 · X' 436→438 · ALL 436→438 | L6M 96→96 · PRE 229→229 · X' 463→457 · ALL 463→457 | L6M 73→90 · PRE 145→145 · X' 318→288 · ALL 318→288 | 0.07/0.27/0.09/0.09 · 0.10/0.41/0.58/0.53 · 0.09/0.72/0.55/0.54 · 0.70/0.10/0.05/0.05 | VOLUME-EFFECT / NO / NO / NO |
| NQ RSI2_t10 | 5.2 | L6M 88→53 · PRE 162→146 · X' 317→265 · ALL 317→265 | L6M 116→116 · PRE 276→261 · X' 436→444 · ALL 436→444 | L6M 96→96 · PRE 229→229 · X' 463→452 · ALL 463→452 | L6M 73→75 · PRE 145→145 · X' 318→278 · ALL 318→278 | 0.04/0.18/0.08/0.07 · 0.09/0.52/0.67/0.59 · 0.05/0.60/0.57/0.56 · 0.42/0.05/0.07/0.07 | L6M-ONLY / NO / NO / NO |
| NQ RSI2C_s20 | 1 | L6M 88→81 · PRE 162→158 · X' 317→307 · ALL 317→307 | L6M 116→116 · PRE 276→270 · X' 436→435 · ALL 436→435 | L6M 96→96 · PRE 229→229 · X' 463→461 · ALL 463→461 | L6M 73→72 · PRE 145→145 · X' 318→308 · ALL 318→308 | 0.07/0.26/0.15/0.15 · 0.00/0.46/0.53/0.53 · 0.10/0.63/0.59/0.59 · 0.29/0.10/0.14/0.14 | NO / NO / NO / NO |
| NQ RSI2C_s20 | 3 | L6M 88→68 · PRE 162→149 · X' 317→287 · ALL 317→287 | L6M 116→116 · PRE 276→260 · X' 436→438 · ALL 436→438 | L6M 96→96 · PRE 229→229 · X' 463→457 · ALL 463→457 | L6M 73→90 · PRE 145→145 · X' 318→288 · ALL 318→288 | 0.07/0.23/0.12/0.12 · 0.12/0.40/0.57/0.51 · 0.12/0.64/0.56/0.55 · 0.70/0.10/0.06/0.06 | VOLUME-EFFECT / NO / NO / NO |
| NQ RSI2C_s20 | 6.7 | L6M 88→56 · PRE 162→146 · X' 317→250 · ALL 317→250 | L6M 116→116 · PRE 276→366 · X' 436→456 · ALL 436→505 | L6M 96→96 · PRE 229→229 · X' 463→468 · ALL 463→468 | L6M 73→73 · PRE 145→158 · X' 318→324 · ALL 318→324 | 0.07/0.13/0.10/0.08 · 0.52/0.90/0.67/0.81 · 0.07/0.50/0.63/0.59 · 0.29/0.40/0.37/0.37 | VOLUME-EFFECT / NO / NO / NO |
| ES RSI2_t10 | 1 | L6M 88→84 · PRE 162→159 · X' 317→307 · ALL 317→307 | L6M 116→116 · PRE 276→269 · X' 436→441 · ALL 436→441 | L6M 96→96 · PRE 229→229 · X' 463→459 · ALL 463→459 | L6M 73→72 · PRE 145→145 · X' 318→310 · ALL 318→310 | 0.04/0.27/0.05/0.05 · 0.01/0.35/0.76/0.76 · 0.04/0.69/0.41/0.41 · 0.04/0.20/0.10/0.10 | NO / NO / NO / NO |
| ES RSI2_t10 | 3 | L6M 88→76 · PRE 162→153 · X' 317→287 · ALL 317→287 | L6M 116→116 · PRE 276→255 · X' 436→451 · ALL 436→451 | L6M 96→96 · PRE 229→229 · X' 463→453 · ALL 463→453 | L6M 73→72 · PRE 145→145 · X' 318→295 · ALL 318→295 | 0.04/0.26/0.01/0.01 · 0.08/0.23/0.71/0.70 · 0.04/0.58/0.35/0.35 · 0.12/0.17/0.03/0.03 | NO / NO / NO / NO |
| ES RSI2_t10 | 8.6 | L6M 88→54 · PRE 162→146 · X' 317→237 · ALL 317→237 | L6M 116→116 · PRE 276→311 · X' 436→486 · ALL 436→528 | L6M 96→96 · PRE 229→229 · X' 463→438 · ALL 463→438 | L6M 73→54 · PRE 145→145 · X' 318→296 · ALL 318→296 | 0.04/0.17/0.00/0.00 · 0.06/0.83/0.80/0.92 · 0.03/0.60/0.40/0.39 · 0.04/0.15/0.14/0.14 | L6M-ONLY / NO / NO / L6M-ONLY |
| NQ IBS_t20_n1 | 1 | L6M 88→81 · PRE 162→139 · X' 317→293 · ALL 317→293 | L6M 116→116 · PRE 276→250 · X' 436→423 · ALL 436→423 | L6M 96→96 · PRE 229→219 · X' 463→440 · ALL 463→440 | L6M 73→72 · PRE 145→145 · X' 318→298 · ALL 318→298 | 0.09/0.01/0.10/0.10 · 0.65/0.12/0.15/0.14 · 0.00/0.23/0.24/0.24 · 0.22/0.23/0.13/0.13 | NO / NO / NO / NO |
| NQ IBS_t20_n1 | 3 | L6M 88→68 · PRE 162→121 · X' 317→258 · ALL 317→258 | L6M 116→117 · PRE 276→199 · X' 436→408 · ALL 436→408 | L6M 96→49 · PRE 229→200 · X' 463→459 · ALL 463→459 | L6M 73→68 · PRE 145→145 · X' 318→333 · ALL 318→333 | 0.08/0.03/0.10/0.10 · 0.67/0.07/0.23/0.20 · 0.00/0.15/0.62/0.61 · 0.04/0.14/0.44/0.44 | VOLUME-EFFECT / NO / L6M-ONLY / NO |
| NQ IBS_t20_n1 | 3.9 | L6M 88→62 · PRE 162→113 · X' 317→242 · ALL 317→242 | L6M 116→116 · PRE 276→176 · X' 436→390 · ALL 436→390 | L6M 96→48 · PRE 229→191 · X' 463→437 · ALL 463→437 | L6M 73→62 · PRE 145→145 · X' 318→310 · ALL 318→310 | 0.06/0.01/0.10/0.09 · 0.59/0.05/0.17/0.15 · 0.01/0.12/0.52/0.49 · 0.04/0.14/0.27/0.27 | VOLUME-EFFECT / NO / L6M-ONLY / NO |
| NQ IBS_t20_n1 | 4.2 | L6M 88→60 · PRE 162→111 · X' 317→237 · ALL 317→237 | L6M 116→115 · PRE 276→168 · X' 436→384 · ALL 436→384 | L6M 96→48 · PRE 229→188 · X' 463→431 · ALL 463→431 | L6M 73→60 · PRE 145→145 · X' 318→305 · ALL 318→305 | 0.06/0.01/0.10/0.08 · 0.15/0.04/0.15/0.14 · 0.00/0.12/0.47/0.46 · 0.04/0.15/0.26/0.26 | VOLUME-EFFECT / NO / L6M-ONLY / NO |
| NQ GSHORT_t90 | 1 | L6M 88→88 · PRE 162→161 · X' 317→321 · ALL 317→321 | L6M 116→114 · PRE 276→269 · X' 436→438 · ALL 436→438 | L6M 96→94 · PRE 229→229 · X' 463→467 · ALL 463→467 | L6M 73→73 · PRE 145→145 · X' 318→322 · ALL 318→322 | 0.00/0.34/0.65/0.65 · 0.00/0.14/0.62/0.61 · 0.00/0.10/0.59/0.59 · 0.00/0.26/0.69/0.69 | NO / NO / NO / NO |
| NQ GSHORT_t90 | 3 | L6M 88→88 · PRE 162→160 · X' 317→329 · ALL 317→329 | L6M 116→109 · PRE 276→266 · X' 436→443 · ALL 436→443 | L6M 96→90 · PRE 229→227 · X' 463→475 · ALL 463→475 | L6M 73→73 · PRE 145→145 · X' 318→330 · ALL 318→330 | 0.00/0.32/0.64/0.64 · 0.00/0.14/0.61/0.45 · 0.00/0.10/0.59/0.57 · 0.37/0.10/0.67/0.67 | NO / NO / NO / NO |
| NQ GSHORT_t90 | 5 | L6M 88→88 · PRE 162→159 · X' 317→337 · ALL 317→337 | L6M 116→105 · PRE 276→267 · X' 436→449 · ALL 436→449 | L6M 96→85 · PRE 229→226 · X' 463→483 · ALL 463→483 | L6M 73→73 · PRE 145→145 · X' 318→338 · ALL 318→338 | 0.00/0.30/0.63/0.63 · 0.01/0.14/0.63/0.38 · 0.00/0.09/0.57/0.55 · 0.59/0.10/0.61/0.61 | NO / NO / NO / NO |
| NQ GSHORT_t90 | 15.6 | L6M 88→88 · PRE 162→173 · X' 317→380 · ALL 317→380 | L6M 116→105 · PRE 276→293 · X' 436→468 · ALL 436→480 | L6M 96→61 · PRE 229→248 · X' 463→529 · ALL 463→547 | L6M 73→73 · PRE 145→181 · X' 318→395 · ALL 318→395 | 0.00/0.10/0.59/0.44 · 0.01/0.16/0.65/0.34 · 0.00/0.16/0.68/0.52 · 0.00/0.17/0.65/0.59 | NO / NO / L6M-ONLY / NO |
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 1 | L6M 88→89 · PRE 162→173 · X' 317→308 · ALL 317→308 | L6M 116→118 · PRE 276→220 · X' 436→509 · ALL 436→509 | L6M 96→97 · PRE 229→236 · X' 463→421 · ALL 463→421 | L6M 73→72 · PRE 145→183 · X' 318→346 · ALL 318→346 | 0.45/0.41/0.05/0.05 · 0.98/0.03/0.65/0.49 · 0.61/0.48/0.00/0.00 · 0.80/0.48/0.23/0.23 | NO / NO / NO / NO |
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 3 | L6M 88→90 · PRE 162→195 · X' 317→303 · ALL 317→303 | L6M 116→116 · PRE 276→337 · X' 436→474 · ALL 436→595 | L6M 96→96 · PRE 229→250 · X' 463→386 · ALL 463→386 | L6M 73→73 · PRE 145→324 · X' 318→326 · ALL 318→326 | 0.39/0.32/0.06/0.06 · 0.39/0.27/0.23/0.27 · 0.40/0.23/0.01/0.00 · 0.62/0.71/0.06/0.04 | NO / NO / NO / NO |
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 5 | L6M 88→93 · PRE 162→216 · X' 317→299 · ALL 317→299 | L6M 116→117 · PRE 276→322 · X' 436→519 · ALL 436→625 | L6M 96→169 · PRE 229→263 · X' 463→362 · ALL 463→362 | L6M 73→72 · PRE 145→328 · X' 318→349 · ALL 318→349 | 0.23/0.18/0.05/0.03 · 0.34/0.17/0.35/0.20 · 0.83/0.12/0.01/0.01 · 0.08/0.49/0.05/0.03 | NO / NO / NO / NO |
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 10 | L6M 88→169 · PRE 162→271 · X' 317→312 · ALL 317→312 | L6M 116→118 · PRE 276→447 · X' 436→580 · ALL 436→838 | L6M 96→176 · PRE 229→349 · X' 463→466 · ALL 463→466 | L6M 73→175 · PRE 145→329 · X' 318→239 · ALL 318→329 | 0.19/0.04/0.04/0.00 · 0.07/0.24/0.48/0.35 · 0.33/0.06/0.11/0.01 · 0.23/0.04/0.00/0.00 | NO / NO / NO / NO |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 1 | L6M 88→88 · PRE 162→153 · X' 317→307 · ALL 317→307 | L6M 116→117 · PRE 276→236 · X' 436→516 · ALL 436→516 | L6M 96→97 · PRE 229→218 · X' 463→484 · ALL 463→484 | L6M 73→72 · PRE 145→183 · X' 318→363 · ALL 318→363 | 0.34/0.10/0.07/0.07 · 0.80/0.10/0.76/0.61 · 0.56/0.03/0.21/0.20 · 0.01/0.40/0.54/0.54 | NO / NO / NO / NO |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 3 | L6M 88→89 · PRE 162→145 · X' 317→300 · ALL 317→300 | L6M 116→118 · PRE 276→232 · X' 436→629 · ALL 436→629 | L6M 96→99 · PRE 229→204 · X' 463→455 · ALL 463→455 | L6M 73→88 · PRE 145→279 · X' 318→439 · ALL 318→439 | 0.30/0.07/0.09/0.09 · 0.65/0.06/0.94/0.40 · 0.75/0.04/0.07/0.06 · 0.88/0.69/0.52/0.47 | NO / NO / NO / NO |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 5 | L6M 88→90 · PRE 162→151 · X' 317→294 · ALL 317→294 | L6M 116→117 · PRE 276→244 · X' 436→659 · ALL 436→659 | L6M 96→97 · PRE 229→255 · X' 463→398 · ALL 463→398 | L6M 73→83 · PRE 145→252 · X' 318→395 · ALL 318→395 | 0.18/0.04/0.08/0.06 · 0.38/0.05/0.89/0.27 · 0.30/0.12/0.06/0.02 · 0.39/0.27/0.16/0.10 | NO / NO / NO / NO |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 10 | L6M 88→122 · PRE 162→277 · X' 317→278 · ALL 317→278 | L6M 116→177 · PRE 276→370 · X' 436→561 · ALL 436→561 | L6M 96→160 · PRE 229→204 · X' 463→522 · ALL 463→522 | L6M 73→144 · PRE 145→217 · X' 318→531 · ALL 318→531 | 0.08/0.08/0.01/0.00 · 0.41/0.18/0.52/0.12 · 0.28/0.00/0.20/0.04 · 0.15/0.01/0.19/0.04 | NO / NO / NO / NO |
| TB4A time 30s ST3 SW38 T2 (MAPPED) | 1 | L6M 88→94 · PRE 162→174 · X' 317→317 · ALL 317→317 | L6M 116→106 · PRE 276→256 · X' 436→437 · ALL 436→437 | L6M 96→101 · PRE 229→241 · X' 463→464 · ALL 463→464 | L6M 73→79 · PRE 145→143 · X' 318→319 · ALL 318→319 | 0.70/0.29/0.08/0.08 · 0.02/0.01/0.10/0.03 · 0.55/0.30/0.10/0.09 · 0.70/0.08/0.08/0.08 | NO / NO / NO / NO |
| TB4A time 30s ST3 SW38 T2 (MAPPED) | 3 | L6M 88→107 · PRE 162→197 · X' 317→319 · ALL 317→319 | L6M 116→104 · PRE 276→254 · X' 436→439 · ALL 436→439 | L6M 96→110 · PRE 229→264 · X' 463→466 · ALL 463→466 | L6M 73→91 · PRE 145→163 · X' 318→321 · ALL 318→321 | 0.59/0.20/0.07/0.06 · 0.04/0.01/0.09/0.02 · 0.45/0.19/0.07/0.03 · 0.56/0.07/0.07/0.06 | NO / NO / NO / NO |
| TB4A time 30s ST3 SW38 T2 (MAPPED) | 5 | L6M 88→119 · PRE 162→220 · X' 317→321 · ALL 317→321 | L6M 116→115 · PRE 276→279 · X' 436→441 · ALL 436→441 | L6M 96→119 · PRE 229→287 · X' 463→468 · ALL 463→468 | L6M 73→104 · PRE 145→187 · X' 318→323 · ALL 318→323 | 0.28/0.09/0.06/0.01 · 0.01/0.01/0.07/0.00 · 0.15/0.09/0.06/0.03 · 0.21/0.02/0.06/0.01 | NO / NO / NO / NO |
| TB4A time 30s ST3 SW38 T2 (MAPPED) | 10 | L6M 88→150 · PRE 162→287 · X' 317→326 · ALL 317→370 | L6M 116→143 · PRE 276→348 · X' 436→446 · ALL 436→446 | L6M 96→141 · PRE 229→350 · X' 463→473 · ALL 463→473 | L6M 73→135 · PRE 145→306 · X' 318→328 · ALL 318→365 | 0.03/0.00/0.03/0.00 · 0.01/0.00/0.04/0.00 · 0.01/0.01/0.04/0.00 · 0.01/0.01/0.03/0.00 | NO / NO / NO / NO |
| TB4W_10 volume500 ST10 (MAPPED) | 1 | L6M 88→100 · PRE 162→159 · X' 317→316 · ALL 317→316 | L6M 116→113 · PRE 276→231 · X' 436→433 · ALL 436→433 | L6M 96→80 · PRE 229→227 · X' 463→460 · ALL 463→460 | L6M 73→85 · PRE 145→151 · X' 318→317 · ALL 318→317 | 0.85/0.09/0.12/0.12 · 0.10/0.00/0.14/0.04 · 0.01/0.09/0.14/0.09 · 0.85/0.23/0.12/0.12 | NO / NO / NO / NO |
| TB4W_10 volume500 ST10 (MAPPED) | 3 | L6M 88→125 · PRE 162→154 · X' 317→329 · ALL 317→329 | L6M 116→129 · PRE 276→204 · X' 436→427 · ALL 436→427 | L6M 96→86 · PRE 229→222 · X' 463→460 · ALL 463→460 | L6M 73→109 · PRE 145→164 · X' 318→330 · ALL 318→330 | 0.65/0.03/0.12/0.07 · 0.06/0.00/0.14/0.01 · 0.10/0.01/0.11/0.03 · 0.60/0.04/0.12/0.07 | NO / NO / NO / NO |
| TB4W_10 volume500 ST10 (MAPPED) | 5 | L6M 88→149 · PRE 162→158 · X' 317→341 · ALL 317→341 | L6M 116→145 · PRE 276→202 · X' 436→422 · ALL 436→422 | L6M 96→110 · PRE 229→216 · X' 463→472 · ALL 463→472 | L6M 73→134 · PRE 145→176 · X' 318→342 · ALL 318→342 | 0.34/0.00/0.10/0.03 · 0.03/0.00/0.11/0.01 · 0.05/0.00/0.10/0.02 · 0.28/0.00/0.10/0.03 | NO / NO / NO / NO |
| TB4W_10 volume500 ST10 (MAPPED) | 10 | L6M 88→255 · PRE 162→228 · X' 317→372 · ALL 317→372 | L6M 116→223 · PRE 276→220 · X' 436→407 · ALL 436→407 | L6M 96→216 · PRE 229→215 · X' 463→503 · ALL 463→503 | L6M 73→239 · PRE 145→238 · X' 318→373 · ALL 318→373 | 0.11/0.00/0.07/0.00 · 0.03/0.00/0.04/0.00 · 0.04/0.00/0.08/0.00 · 0.10/0.00/0.07/0.00 | NO / NO / NO / NO |
| TR3_DON15_S (MAPPED) | 1 | L6M 88→78 · PRE 162→155 · X' 317→316 · ALL 317→316 | L6M 116→120 · PRE 276→229 · X' 436→429 · ALL 436→429 | L6M 96→98 · PRE 229→222 · X' 463→456 · ALL 463→456 | L6M 73→62 · PRE 145→151 · X' 318→317 · ALL 318→317 | 0.03/0.12/0.07/0.07 · 0.36/0.00/0.07/0.02 · 0.42/0.12/0.06/0.06 · 0.03/0.45/0.07/0.07 | NO / NO / NO / NO |
| TR3_DON15_S (MAPPED) | 3 | L6M 88→58 · PRE 162→142 · X' 317→326 · ALL 317→326 | L6M 116→127 · PRE 276→176 · X' 436→413 · ALL 436→413 | L6M 96→102 · PRE 229→209 · X' 463→458 · ALL 463→458 | L6M 73→42 · PRE 145→164 · X' 318→328 · ALL 318→328 | 0.01/0.06/0.07/0.06 · 0.23/0.00/0.06/0.01 · 0.41/0.07/0.06/0.03 · 0.01/0.20/0.07/0.06 | L6M-ONLY / NO / NO / L6M-ONLY |
| TR3_DON15_S (MAPPED) | 5 | L6M 88→49 · PRE 162→140 · X' 317→337 · ALL 317→337 | L6M 116→135 · PRE 276→157 · X' 436→398 · ALL 436→398 | L6M 96→105 · PRE 229→195 · X' 463→468 · ALL 463→468 | L6M 73→49 · PRE 145→177 · X' 318→339 · ALL 318→339 | 0.01/0.01/0.07/0.06 · 0.10/0.00/0.04/0.01 · 0.21/0.01/0.07/0.02 · 0.01/0.07/0.07/0.06 | L6M-ONLY / NO / NO / L6M-ONLY |
| TR3_DON15_S (MAPPED) | 10 | L6M 88→80 · PRE 162→179 · X' 317→365 · ALL 317→365 | L6M 116→158 · PRE 276→191 · X' 436→396 · ALL 436→396 | L6M 96→116 · PRE 229→215 · X' 463→496 · ALL 463→496 | L6M 73→80 · PRE 145→208 · X' 318→366 · ALL 318→366 | 0.00/0.01/0.05/0.00 · 0.01/0.00/0.04/0.00 · 0.02/0.00/0.04/0.00 · 0.00/0.01/0.05/0.00 | NO / NO / NO / NO |

## 2. Does the drawdown value survive the lock? (PRE / X' / ALL maxDD cut %, + = smaller maxDD; R1 = blind, R2 = routed)
Rule: carries value only if BOTH PRE and X' cut > 5% without a lock; survives lock F if both cuts keep >= half their no-lock size. Composite:

| sleeve | lots | route | maxDD cut % none (PRE / X' / ALL) | 12R | 20R | 30R | value survives? (PRE and X' cut >= half of no-lock cut, > 0) |
|---|---|---|---|---|---|---|---|
| ORB_ASIA_15 s60 (LIVE-CAL, NQ) | 3 | R1 | -3 / -1 / -3 | -2 / -3 / -2 | -2 / -1 / -2 | -3 / -1 / -3 | no PRE+X' value to carry (no-lock cut PRE -3% / X' -1%) |
| ORB_ASIA_15 s60 (LIVE-CAL, NQ) | 3 | R2 | -3 / -1 / -3 | +1 / -3 / +1 | +9 / +11 / +9 | -1 / -5 / -1 | no PRE+X' value to carry (no-lock cut PRE -3% / X' -1%) |
| ORB_ASIA_15 s60 (LIVE-CAL, NQ) | 17.2 | R1 | -15 / -27 / -15 | -11 / -49 / -11 | -14 / -50 / -14 | -17 / -39 / -17 | no PRE+X' value to carry (no-lock cut PRE -15% / X' -27%) |
| ORB_ASIA_15 s60 (LIVE-CAL, NQ) | 17.2 | R2 | -15 / -27 / -15 | +7 / -170 / -56 | -10 / -138 / -76 | -20 / -40 / -20 | no PRE+X' value to carry (no-lock cut PRE -15% / X' -27%) |
| NQ RSI2_t10 | 3 | R1 | +5 / +18 / +5 | +6 / +4 / +6 | +7 / +16 / +7 | +6 / +16 / +6 | 12R NO, 20R yes, 30R yes |
| NQ RSI2_t10 | 3 | R2 | +5 / +18 / +5 | +0 / -0 / +0 | -0 / +16 / -0 | +0 / +16 / +0 | 12R NO, 20R NO, 30R NO |
| NQ RSI2_t10 | 5.2 | R1 | +9 / +30 / +9 | +10 / -0 / +10 | +11 / +28 / +11 | +9 / +27 / +9 | 12R NO, 20R yes, 30R yes |
| NQ RSI2_t10 | 5.2 | R2 | +9 / +30 / +9 | +0 / +0 / +0 | -0 / +26 / +0 | +0 / +27 / +0 | 12R NO, 20R NO, 30R NO |
| NQ RSI2C_s20 | 3 | R1 | +5 / +18 / +5 | +6 / +4 / +6 | +7 / +16 / +7 | +6 / +16 / +6 | 12R NO, 20R yes, 30R yes |
| NQ RSI2C_s20 | 3 | R2 | +5 / +18 / +5 | +0 / -0 / +0 | -0 / +16 / -0 | +0 / +16 / +0 | 12R NO, 20R NO, 30R NO |
| NQ RSI2C_s20 | 6.7 | R1 | +12 / +36 / +12 | +12 / -10 / +12 | +7 / +30 / +7 | +6 / +30 / +6 | 12R NO, 20R yes, 30R NO |
| NQ RSI2C_s20 | 6.7 | R2 | +12 / +36 / +12 | +0 / -0 / +0 | +0 / +26 / -0 | +0 / +30 / +0 | 12R NO, 20R NO, 30R NO |
| ES RSI2_t10 | 3 | R1 | +4 / +16 / +4 | +4 / +21 / +4 | +5 / +15 / +5 | +4 / +15 / +4 | no PRE+X' value to carry (no-lock cut PRE +4% / X' +16%) |
| ES RSI2_t10 | 3 | R2 | +4 / +16 / +4 | +0 / +4 / +0 | -0 / +7 / -0 | +0 / +7 / +0 | no PRE+X' value to carry (no-lock cut PRE +4% / X' +16%) |
| ES RSI2_t10 | 8.6 | R1 | +11 / +46 / +11 | +11 / +19 / +11 | +13 / +36 / +13 | +12 / +36 / +12 | 12R NO, 20R yes, 30R yes |
| ES RSI2_t10 | 8.6 | R2 | +11 / +46 / +11 | +0 / +7 / +0 | +0 / +19 / +0 | +0 / +19 / +0 | 12R NO, 20R NO, 30R NO |
| NQ IBS_t20_n1 | 3.9 | R1 | +33 / +32 / +33 | +26 / +19 / +26 | +13 / +29 / +13 | +12 / +29 / +12 | 12R yes, 20R NO, 30R NO |
| NQ IBS_t20_n1 | 3.9 | R2 | +33 / +32 / +33 | +16 / -19 / +16 | +16 / +33 / +16 | +13 / +33 / +13 | 12R NO, 20R NO, 30R NO |
| NQ IBS_t20_n1 | 4.2 | R1 | +36 / +34 / +36 | +28 / +18 / +28 | +13 / +31 / +13 | +11 / +31 / +11 | 12R yes, 20R NO, 30R NO |
| NQ IBS_t20_n1 | 4.2 | R2 | +36 / +34 / +36 | +18 / -18 / +18 | +16 / +35 / +16 | +12 / +35 / +12 | 12R NO, 20R NO, 30R NO |
| NQ GSHORT_t90 | 3 | R1 | +1 / -10 / +1 | +16 / -4 / +16 | +12 / -9 / +12 | +1 / -9 / +1 | no PRE+X' value to carry (no-lock cut PRE +1% / X' -10%) |
| NQ GSHORT_t90 | 3 | R2 | +1 / -10 / +1 | -2 / +6 / -2 | +2 / +0 / +2 | +1 / -9 / +1 | no PRE+X' value to carry (no-lock cut PRE +1% / X' -10%) |
| NQ GSHORT_t90 | 15.6 | R1 | +4 / -54 / +4 | +21 / -47 / +21 | +6 / -49 / -4 | +2 / -49 / +2 | no PRE+X' value to carry (no-lock cut PRE +4% / X' -54%) |
| NQ GSHORT_t90 | 15.6 | R2 | +4 / -54 / +4 | +4 / -67 / +4 | +9 / +0 / +9 | +7 / -56 / +0 | no PRE+X' value to carry (no-lock cut PRE +4% / X' -54%) |
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 3 | R1 | -11 / -12 / -11 | -8 / -14 / -8 | -7 / -11 / -7 | -4 / -11 / -4 | no PRE+X' value to carry (no-lock cut PRE -11% / X' -12%) |
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 3 | R2 | -11 / -12 / -11 | +1 / -26 / +1 | +5 / +15 / +5 | -15 / -8 / -15 | no PRE+X' value to carry (no-lock cut PRE -11% / X' -12%) |
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 10 | R1 | -43 / -43 / -43 | -44 / -66 / -44 | -46 / -41 / -46 | -34 / -41 / -34 | no PRE+X' value to carry (no-lock cut PRE -43% / X' -43%) |
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 10 | R2 | -43 / -43 / -43 | -32 / -65 / -32 | -110 / -96 / -110 | -104 / -11 / -104 | no PRE+X' value to carry (no-lock cut PRE -43% / X' -43%) |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 3 | R1 | +5 / -20 / +5 | +26 / -9 / +26 | +2 / -17 / +2 | +1 / -18 / +1 | no PRE+X' value to carry (no-lock cut PRE +5% / X' -20%) |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 3 | R2 | +5 / -20 / +5 | +5 / -85 / +5 | -11 / -48 / -11 | +0 / -59 / -2 | no PRE+X' value to carry (no-lock cut PRE +5% / X' -20%) |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 10 | R1 | -0 / -83 / -0 | -7 / -109 / -7 | -46 / -77 / -46 | -43 / -75 / -43 | no PRE+X' value to carry (no-lock cut PRE -0% / X' -83%) |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 10 | R2 | -0 / -83 / -0 | +1 / -198 / -53 | -94 / -85 / -94 | -39 / -122 / -42 | no PRE+X' value to carry (no-lock cut PRE -0% / X' -83%) |
| TB4A time 30s ST3 SW38 T2 (MAPPED) | 3 | R1 | -16 / -12 / -16 | -3 / -18 / -3 | -4 / -11 / -4 | -11 / -11 / -11 | no PRE+X' value to carry (no-lock cut PRE -16% / X' -12%) |
| TB4A time 30s ST3 SW38 T2 (MAPPED) | 10 | R1 | -52 / -45 / -52 | -31 / -124 / -31 | -39 / -40 / -45 | -42 / -40 / -53 | no PRE+X' value to carry (no-lock cut PRE -52% / X' -45%) |
| TB4W_10 volume500 ST10 (MAPPED) | 3 | R1 | +4 / -31 / +4 | +8 / -23 / +8 | +10 / -28 / +10 | +4 / -28 / +4 | no PRE+X' value to carry (no-lock cut PRE +4% / X' -31%) |
| TB4W_10 volume500 ST10 (MAPPED) | 10 | R1 | -15 / -115 / -15 | +14 / -94 / +0 | -29 / -94 / -36 | -19 / -104 / -31 | no PRE+X' value to carry (no-lock cut PRE -15% / X' -115%) |
| TR3_DON15_S (MAPPED) | 3 | R1 | +6 / -23 / +6 | +20 / -22 / +20 | +2 / -21 / +2 | +2 / -21 / +2 | no PRE+X' value to carry (no-lock cut PRE +6% / X' -23%) |
| TR3_DON15_S (MAPPED) | 10 | R1 | -8 / -86 / -24 | -6 / -85 / -6 | -45 / -72 / -45 | -42 / -78 / -42 | no PRE+X' value to carry (no-lock cut PRE -8% / X' -86%) |

As-is:

| sleeve | lots | route | maxDD cut % none (PRE / X' / ALL) | 12R | 20R | 30R | value survives? (PRE and X' cut >= half of no-lock cut, > 0) |
|---|---|---|---|---|---|---|---|
| ORB_ASIA_15 s60 (LIVE-CAL, NQ) | 3 | R1 | -6 / -7 / -7 | +7 / -5 / -5 | -4 / -5 / -5 | +1 / -7 / -7 | no PRE+X' value to carry (no-lock cut PRE -6% / X' -7%) |
| ORB_ASIA_15 s60 (LIVE-CAL, NQ) | 3 | R2 | -6 / -7 / -7 | +12 / -9 / -9 | +1 / -5 / -5 | -0 / -6 / -6 | no PRE+X' value to carry (no-lock cut PRE -6% / X' -7%) |
| ORB_ASIA_15 s60 (LIVE-CAL, NQ) | 17.2 | R1 | -35 / -39 / -39 | +2 / -28 / -28 | -25 / -27 / -27 | -35 / -39 / -39 | no PRE+X' value to carry (no-lock cut PRE -35% / X' -39%) |
| ORB_ASIA_15 s60 (LIVE-CAL, NQ) | 17.2 | R2 | -35 / -39 / -39 | -14 / -47 / -65 | +4 / -39 / -39 | -60 / -72 / -72 | no PRE+X' value to carry (no-lock cut PRE -35% / X' -39%) |
| NQ RSI2_t10 | 3 | R1 | +8 / +9 / +9 | +18 / +7 / +7 | +6 / +6 / +6 | +5 / +9 / +9 | 12R yes, 20R yes, 30R yes |
| NQ RSI2_t10 | 3 | R2 | +8 / +9 / +9 | +6 / -0 / -0 | -0 / +1 / +1 | +0 / +9 / +9 | 12R NO, 20R NO, 30R NO |
| NQ RSI2_t10 | 5.2 | R1 | +10 / +16 / +16 | +31 / +12 / +12 | +10 / +11 / +11 | +7 / +16 / +16 | 12R yes, 20R yes, 30R yes |
| NQ RSI2_t10 | 5.2 | R2 | +10 / +16 / +16 | +6 / -2 / -2 | -0 / +2 / +2 | +0 / +12 / +12 | 12R NO, 20R NO, 30R NO |
| NQ RSI2C_s20 | 3 | R1 | +8 / +9 / +9 | +18 / +7 / +7 | +6 / +6 / +6 | +5 / +9 / +9 | 12R yes, 20R yes, 30R yes |
| NQ RSI2C_s20 | 3 | R2 | +8 / +9 / +9 | +6 / -0 / -0 | -0 / +1 / +1 | +0 / +9 / +9 | 12R NO, 20R NO, 30R NO |
| NQ RSI2C_s20 | 6.7 | R1 | +10 / +21 / +21 | +40 / +14 / +14 | +13 / +14 / +14 | +7 / +21 / +21 | 12R yes, 20R yes, 30R yes |
| NQ RSI2C_s20 | 6.7 | R2 | +10 / +21 / +21 | -33 / -5 / -16 | -0 / -1 / -1 | -9 / -2 / -2 | 12R NO, 20R NO, 30R NO |
| ES RSI2_t10 | 3 | R1 | +5 / +9 / +9 | +14 / +7 / +7 | +4 / +6 / +6 | +1 / +9 / +9 | 12R yes, 20R yes, 30R NO |
| ES RSI2_t10 | 3 | R2 | +5 / +9 / +9 | +8 / -3 / -3 | +0 / +2 / +2 | +0 / +7 / +7 | 12R NO, 20R NO, 30R NO |
| ES RSI2_t10 | 8.6 | R1 | +10 / +25 / +25 | +38 / +19 / +19 | +11 / +18 / +18 | +4 / +25 / +25 | 12R yes, 20R yes, 30R NO |
| ES RSI2_t10 | 8.6 | R2 | +10 / +25 / +25 | -13 / -11 / -21 | -0 / +5 / +5 | +0 / +7 / +7 | 12R NO, 20R NO, 30R NO |
| NQ IBS_t20_n1 | 3.9 | R1 | +30 / +23 / +23 | +11 / +24 / +24 | +38 / +19 / +19 | -26 / +23 / +23 | 12R NO, 20R yes, 30R NO |
| NQ IBS_t20_n1 | 3.9 | R2 | +30 / +23 / +23 | +36 / +11 / +11 | +17 / +6 / +6 | +0 / +2 / +2 | 12R NO, 20R NO, 30R NO |
| NQ IBS_t20_n1 | 4.2 | R1 | +32 / +25 / +25 | +12 / +26 / +26 | +39 / +21 / +21 | -28 / +25 / +25 | 12R NO, 20R yes, 30R NO |
| NQ IBS_t20_n1 | 4.2 | R2 | +32 / +25 / +25 | +39 / +12 / +12 | +18 / +7 / +7 | +0 / +4 / +4 | 12R NO, 20R NO, 30R NO |
| NQ GSHORT_t90 | 3 | R1 | +1 / -4 / -4 | +11 / -3 / -3 | +1 / -3 / -3 | +0 / -4 / -4 | no PRE+X' value to carry (no-lock cut PRE +1% / X' -4%) |
| NQ GSHORT_t90 | 3 | R2 | +1 / -4 / -4 | +3 / -2 / -2 | +1 / -3 / -3 | +0 / -4 / -4 | no PRE+X' value to carry (no-lock cut PRE +1% / X' -4%) |
| NQ GSHORT_t90 | 15.6 | R1 | -7 / -20 / -20 | -18 / -14 / -21 | -12 / -14 / -21 | -17 / -20 / -20 | no PRE+X' value to carry (no-lock cut PRE -7% / X' -20%) |
| NQ GSHORT_t90 | 15.6 | R2 | -7 / -20 / -20 | -6 / -7 / -10 | -8 / -14 / -18 | -25 / -24 / -24 | no PRE+X' value to carry (no-lock cut PRE -7% / X' -20%) |
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 3 | R1 | -20 / +4 / +4 | +35 / +18 / +18 | -14 / +6 / +6 | -11 / +4 / +4 | no PRE+X' value to carry (no-lock cut PRE -20% / X' +4%) |
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 3 | R2 | -20 / +4 / +4 | -22 / -9 / -36 | -9 / +17 / +17 | -123 / -3 / -3 | no PRE+X' value to carry (no-lock cut PRE -20% / X' +4%) |
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 10 | R1 | -67 / +1 / +1 | +9 / +23 / +23 | -48 / +10 / +10 | -63 / +1 / +1 | no PRE+X' value to carry (no-lock cut PRE -67% / X' +1%) |
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 10 | R2 | -67 / +1 / +1 | -62 / -33 / -92 | -52 / -1 / -1 | -127 / +25 / -4 | no PRE+X' value to carry (no-lock cut PRE -67% / X' +1%) |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 3 | R1 | +10 / +5 / +5 | +49 / +20 / +20 | +7 / +7 / +7 | -5 / +5 / +5 | 12R yes, 20R yes, 30R NO |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 3 | R2 | +10 / +5 / +5 | +16 / -44 / -44 | +11 / +2 / +2 | -92 / -38 / -38 | 12R NO, 20R NO, 30R NO |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 10 | R1 | -71 / +12 / +12 | +1 / +29 / +29 | -18 / +12 / +12 | -103 / +12 / +7 | no PRE+X' value to carry (no-lock cut PRE -71% / X' +12%) |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 10 | R2 | -71 / +12 / +12 | -34 / -28 / -28 | +11 / -13 / -13 | -50 / -67 / -67 | no PRE+X' value to carry (no-lock cut PRE -71% / X' +12%) |
| TB4A time 30s ST3 SW38 T2 (MAPPED) | 3 | R1 | -22 / -1 / -1 | +8 / -1 / -1 | -15 / -1 / -1 | -12 / -1 / -1 | no PRE+X' value to carry (no-lock cut PRE -22% / X' -1%) |
| TB4A time 30s ST3 SW38 T2 (MAPPED) | 10 | R1 | -77 / -3 / -17 | -26 / -2 / -2 | -53 / -2 / -2 | -111 / -3 / -15 | no PRE+X' value to carry (no-lock cut PRE -77% / X' -3%) |
| TB4W_10 volume500 ST10 (MAPPED) | 3 | R1 | +5 / -4 / -4 | +26 / +2 / +2 | +3 / +1 / +1 | -13 / -4 / -4 | no PRE+X' value to carry (no-lock cut PRE +5% / X' -4%) |
| TB4W_10 volume500 ST10 (MAPPED) | 10 | R1 | -41 / -18 / -18 | +20 / +7 / +7 | +6 / -9 / -9 | -64 / -18 / -18 | no PRE+X' value to carry (no-lock cut PRE -41% / X' -18%) |
| TR3_DON15_S (MAPPED) | 3 | R1 | +13 / -3 / -3 | +36 / +5 / +5 | +9 / +1 / +1 | -13 / -3 / -3 | no PRE+X' value to carry (no-lock cut PRE +13% / X' -3%) |
| TR3_DON15_S (MAPPED) | 10 | R1 | -11 / -15 / -15 | +31 / +9 / +9 | +6 / -7 / -7 | -44 / -15 / -15 | no PRE+X' value to carry (no-lock cut PRE -11% / X' -15%) |

Reading: (i) IBS is the only sleeve with a PRE+X' cut that beats chance without a lock (rank_dd PRE 0.00, X' 0.04); routed into 20R/30R it keeps 16%/12% PRE and 35% X' (placebo X' 0.04/0.03 holds, PRE rank 0.11/0.10 does not), at 12R it does not survive. (ii) The RSI2 sleeves' cut is an X' (2023-24) cut; the PRE cut is 5-12% without a lock and zero once the lock sees the sleeve. (iii) Blind (R1) values look better than routed ones because the sleeve then trades through weeks the lock has already shut: that is the number to quote only if the sleeve is run as a separate paper strategy outside the lock. (iv) Deepening sleeves (ORB, program cells at >= 5 lots) stay deepening under every lock.

## 3. (a) ES / GSHORT placebos (mean level, 200 draws, same count, same calendar quarter; D1 method; PRE+X' = XP)
| sleeve / placebo | XP (PRE+X') | X' | PRE | HOLD | L6M | L3M | ALL | real $/ct/wk (XP · PRE · HOLD · L6M) |
|---|---|---|---|---|---|---|---|---|
| ES RSI2_t10, all days | 0.990 | 0.875 | 0.980 | 0.995 | 0.995 | 0.970 | 1.000 | 429 · 552 · 857 · 979 |
| NQ RSI2_t10 (re-derived, rolls excluded), all days | 0.950 | 0.565 | 0.970 | 0.910 | 0.920 | 0.890 | 0.985 | 628 · 921 · 949 · 1085 |
| NQ RSI2C_s20 (stopless placebo proxy), all days | 0.905 | 0.590 | 0.920 | 0.890 | 0.900 | 0.870 | 0.945 | 490 · 704 · 910 · 1040 |
| NQ GSHORT_t90, all days | 0.735 | 0.380 | 0.760 | 0.860 | 0.805 | 0.470 | 0.840 | 29 · 112 · 422 · 338 |
| ORB_ASIA_15 s60 (random-time, bar sim), all days | 0.670 | 0.230 | 0.860 | 0.990 | 1.000 | 0.970 | 0.955 | 3 · 114 · 545 · 696 |
| NQ GSHORT_t90, gate-aware | 0.870 | 0.475 | 0.865 | 0.915 | 0.875 | 0.130 | 0.925 | 29 · 112 · 422 · 338 |

ES bars: `cache_te2/ES_adj.npz` sliced to label day <= 20260206 at load (the npz is one file with the full history; post-cap rows dropped on load and never inspected); 15:56 ET open-to-open points reproduce the 73 stored ES_RSI2_t10 trades in the capped window (max |diff| 0.5 pt, mean 0.16). NQ placebo pairs spanning contract rolls are excluded (D1 included them). RSI2C_s20 uses the stopless RSI2 placebo (stop path not simulated: proxy, labelled). Gate-aware GSHORT uses the as-is stack's trailing 4 complete ISO weeks (not Set A exactly).

## 4. (b) Program cells at 1 / 3 / 5 / 10 lots
Direct basis = exec_engine_l2 replay (S10x1 + XJ3, exact per-book locks, 10 lots) rebuilt through the program's own run_rows with the library truncated at the cap: tie-out to TP/direct_daily.parquet 0.0 (cap slice). Series scaled linearly from 10 lots; $/wk are per-contract x lots.

| cell (basis) | lots | maxDD ALL base→after: none / 12R / 20R / 30R (composite, routed R2 for DIRECT cells, blind R1 for MAPPED) | PRE worst-20 none → 12R | ΔL6M mean (MDE) no-lock | placebo rank_dd PRE/X'/ALL (no-lock) | tier none / 12R |
|---|---|---|---|---|---|---|
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 1 | 241→250 / 233→240 / 190→192 / 208→218 | -875→-919 → -608→-639 | +1.8 (2.9) | 0.38/0.38/0.38 | NO / NO |
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 3 | 241→268 / 233→231 / 190→180 / 208→238 | -875→-1041 → -608→-716 | +5.3 (8.8) | 0.33/0.28/0.32 | NO / NO |
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 5 | 241→290 / 233→244 / 190→283 / 208→262 | -875→-1197 → -608→-698 | +8.8 (14.6) | 0.27/0.18/0.20 | NO / NO |
| PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT) | 10 | 241→346 / 233→308 / 190→398 / 208→425 | -875→-1616 → -608→-828 | +17.6 (29.2) | 0.10/0.04/0.01 | NO / NO |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 1 | 241→237 / 233→240 / 190→189 / 208→211 | -875→-877 → -608→-635 | +1.4 (3.1) | 0.20/0.53/0.20 | NO / NO |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 3 | 241→229 / 233→221 / 190→210 / 208→212 | -875→-933 → -608→-675 | +4.2 (9.4) | 0.14/0.39/0.14 | NO / NO |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 5 | 241→221 / 233→339 / 190→329 / 208→199 | -875→-1040 → -608→-678 | +7.1 (15.6) | 0.10/0.34/0.07 | NO / NO |
| PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT) | 10 | 241→242 / 233→356 / 190→369 / 208→295 | -875→-1426 → -608→-760 | +14.1 (31.2) | 0.03/0.14/0.00 | NO / NO |
| TB4A time 30s ST3 SW38 T2 (MAPPED) | 1 | 241→254 / 233→235 / 190→192 / 208→216 | -875→-891 → -608→-635 | +2.6 (3.1) | 0.41/0.39/0.41 | NO / NO |
| TB4A time 30s ST3 SW38 T2 (MAPPED) | 3 | 241→279 / 233→239 / 190→197 / 208→232 | -875→-963 → -608→-736 | +7.7 (9.3) | 0.30/0.28/0.29 | NO / NO |
| TB4A time 30s ST3 SW38 T2 (MAPPED) | 5 | 241→304 / 233→254 / 190→204 / 208→248 | -875→-1051 → -608→-865 | +12.8 (15.5) | 0.20/0.14/0.15 | NO / NO |
| TB4A time 30s ST3 SW38 T2 (MAPPED) | 10 | 241→366 / 233→305 / 190→275 / 208→317 | -875→-1352 → -608→-1210 | +25.7 (31.1) | 0.05/0.02/0.01 | NO / NO |
| TB4W_10 volume500 ST10 (MAPPED) | 1 | 241→238 / 233→226 / 190→184 / 208→205 | -875→-895 → -608→-624 | +3.0 (3.5) | 0.11/0.55/0.11 | NO / NO |
| TB4W_10 volume500 ST10 (MAPPED) | 3 | 241→233 / 233→214 / 190→172 / 208→199 | -875→-970 → -608→-721 | +9.0 (10.4) | 0.06/0.35/0.04 | NO / NO |
| TB4W_10 volume500 ST10 (MAPPED) | 5 | 241→227 / 233→204 / 190→195 / 208→198 | -875→-1071 → -608→-843 | +15.0 (17.3) | 0.01/0.30/0.00 | NO / NO |
| TB4W_10 volume500 ST10 (MAPPED) | 10 | 241→277 / 233→233 / 190→258 / 208→271 | -875→-1361 → -608→-1197 | +30.0 (34.6) | 0.00/0.10/0.00 | NO / NO |
| TR3_DON15_S (MAPPED) | 1 | 241→234 / 233→215 / 190→172 / 208→195 | -875→-917 → -608→-624 | +3.2 (2.5) | 0.14/0.56/0.14 | NO / NO |
| TR3_DON15_S (MAPPED) | 3 | 241→228 / 233→186 / 190→185 / 208→204 | -875→-1012 → -608→-706 | +9.5 (7.4) | 0.10/0.45/0.10 | NO / NO |
| TR3_DON15_S (MAPPED) | 5 | 241→237 / 233→189 / 190→211 / 208→230 | -875→-1125 → -608→-840 | +15.8 (12.3) | 0.09/0.31/0.06 | NO / NO |
| TR3_DON15_S (MAPPED) | 10 | 241→299 / 233→247 / 190→275 / 208→294 | -875→-1474 → -608→-1206 | +31.6 (24.7) | 0.04/0.10/0.01 | NO / NO |

Direct vs mapped (D1) per contract, the two cells that have a direct replay:

| cell | window | direct $/ct/wk | mapped (D1) | direct/mapped | maxDD direct vs mapped $k (1 ct) |
|---|---|---|---|---|---|
| PB7A | L3M | 834 | 1211 | 0.69 | 17.1 vs 17.4 |
| PB7A | L6M | 1764 | 2064 | 0.85 | 17.1 vs 17.4 |
| PB7A | HOLD | 1754 | 1930 | 0.91 | 17.1 vs 18.3 |
| PB7A | PRE | 1427 | 1479 | 0.97 | 24.3 vs 16.7 |
| PB7A | X' | 745 | 375 | 1.99 | 13.7 vs 13.9 |
| PB7A | ALL | 1315 | 1269 | 1.04 | 24.3 vs 18.3 |
| PB7B | L3M | 230 | 1238 | 0.19 | 9.8 vs 5.5 |
| PB7B | L6M | 1411 | 2188 | 0.64 | 16.8 vs 9.9 |
| PB7B | HOLD | 1286 | 2020 | 0.64 | 16.8 vs 9.9 |
| PB7B | PRE | 1103 | 1315 | 0.84 | 41.1 vs 29.8 |
| PB7B | X' | 1093 | 1141 | 0.96 | 17.1 vs 13.7 |
| PB7B | ALL | 1154 | 1433 | 0.81 | 41.1 vs 29.8 |

Basis status of the five cells: PB7 HMA55 W60 s-3 DIRECT (99.8% replayed); PB7 PB5 depth W15 s-3 DIRECT (99.8%); TB4A_time_03 MAPPED (direct coverage 2% in pb4/direct_final, effectively mapped); TB4W_10 MAPPED (replays exist for 2023-02..07 only); TR3_DON15_S MAPPED (no replay). Program-cell placebo = same simulator (DS2 bracket 60 pt / 1.0R, flat 16:55, 1-min bars, independent trades, LIVE-CAL cost) for real entries replayed and 200 random-time draws; ranks in the table compare the cell's own series (direct or mapped) to the placebo distribution, `rank_dd_rsim` in the CSV compares the same-simulator real.

## 5. Detail at the headline lots (composite, no lock; every window)

**NQ IBS_t20_n1, 4.2 lots, composite, no lock** (mean $k/wk base->after, Δ and MDE, `*` beyond MDE; equal-risk = c-scaled so ALL worst-20 matches the base)

| window | mean base→after $k/wk | Δmean (MDE) | maxDD $k | worst-20 $k | SD $k | Calmar | mean/worst-20 | equal-risk Δmean |
|---|---|---|---|---|---|---|---|---|
| L3M | 34.4→42.1 | +7.7 (13.9) | 21→18 | n/a | 44.7→46.3 | 1.61→2.35 | nan→nan | +5.8 |
| L6M | 41.1→47.3 | +6.2 (9.7) | 23→23 | n/a | 42.7→46.3 | 1.80→2.07 | nan→nan | +4.1 |
| HOLD | 38.6→44.0 | +5.4 (8.5) | 97→97 | n/a | 51.8→52.2 | 0.40→0.45 | nan→nan | +3.5 |
| PRE | 23.1→26.2 | +3.1 (9.3) | 241→155 | -875→-877 | 55.7→58.3 | 0.10→0.17 | 0.026→0.030 | +1.9 |
| X' | 8.0→11.3 | +3.4 (5.9) | 121→79 | -420→-473 | 32.6→38.3 | 0.07→0.14 | 0.019→0.024 | +2.9 |
| ALL | 22.3→26.0 | +3.7 (5.3) | 241→155 | -1098→-1149 | 50.3→53.1 | 0.09→0.17 | 0.020→0.023 |  |

**NQ RSI2_t10, 5.2 lots, composite, no lock** (mean $k/wk base->after, Δ and MDE, `*` beyond MDE; equal-risk = c-scaled so ALL worst-20 matches the base)

| window | mean base→after $k/wk | Δmean (MDE) | maxDD $k | worst-20 $k | SD $k | Calmar | mean/worst-20 | equal-risk Δmean |
|---|---|---|---|---|---|---|---|---|
| L3M | 34.4→41.4 | +7.0 (11.2) | 21→10 | n/a | 44.7→46.0 | 1.61→4.10 | nan→nan | +7.1 |
| L6M | 41.1→46.8 | +5.6 (9.8) | 23→23 | n/a | 42.7→48.3 | 1.80→2.04 | nan→nan | +5.7 |
| HOLD | 38.6→43.5 | +4.9 (8.6) | 97→97 | n/a | 51.8→53.1 | 0.40→0.45 | nan→nan | +5.0 |
| PRE | 23.1→27.9 | +4.8 (9.3) | 241→219 | -875→-853 | 55.7→60.7 | 0.10→0.13 | 0.026→0.033 | +4.8 |
| X' | 8.0→8.5 | +0.6 (4.4) | 121→84 | -420→-472 | 32.6→35.7 | 0.07→0.10 | 0.019→0.018 | +0.6 |
| ALL | 22.3→25.9 | +3.6 (5.2) | 241→219 | -1098→-1096 | 50.3→54.3 | 0.09→0.12 | 0.020→0.024 |  |

**NQ RSI2C_s20, 6.7 lots, composite, no lock** (mean $k/wk base->after, Δ and MDE, `*` beyond MDE; equal-risk = c-scaled so ALL worst-20 matches the base)

| window | mean base→after $k/wk | Δmean (MDE) | maxDD $k | worst-20 $k | SD $k | Calmar | mean/worst-20 | equal-risk Δmean |
|---|---|---|---|---|---|---|---|---|
| L3M | 34.4→43.4 | +9.0 (14.4) | 21→10 | n/a | 44.7→47.2 | 1.61→4.30 | nan→nan | +8.7 |
| L6M | 41.1→48.1 | +7.0 (13.1) | 23→39 | n/a | 42.7→51.6 | 1.80→1.24 | nan→nan | +6.6 |
| HOLD | 38.6→44.7 | +6.1 (11.5) | 97→97 | n/a | 51.8→54.4 | 0.40→0.46 | nan→nan | +5.8 |
| PRE | 23.1→27.8 | +4.7 (8.6) | 241→212 | -875→-854 | 55.7→60.0 | 0.10→0.13 | 0.026→0.033 | +4.5 |
| X' | 8.0→8.7 | +0.8 (5.7) | 121→78 | -420→-489 | 32.6→37.1 | 0.07→0.11 | 0.019→0.018 | +0.7 |
| ALL | 22.3→26.2 | +3.9 (5.2) | 241→212 | -1098→-1106 | 50.3→54.5 | 0.09→0.12 | 0.020→0.024 |  |

**ES RSI2_t10, 8.6 lots, composite, no lock** (mean $k/wk base->after, Δ and MDE, `*` beyond MDE; equal-risk = c-scaled so ALL worst-20 matches the base)

| window | mean base→after $k/wk | Δmean (MDE) | maxDD $k | worst-20 $k | SD $k | Calmar | mean/worst-20 | equal-risk Δmean |
|---|---|---|---|---|---|---|---|---|
| L3M | 34.4→44.7 | +10.3 (13.8) | 21→10 | n/a | 44.7→43.5 | 1.61→4.43 | nan→nan | +10.3 |
| L6M | 41.1→49.6 | +8.4 (10.4) | 23→23 | n/a | 42.7→48.5 | 1.80→2.16 | nan→nan | +8.4 |
| HOLD | 38.6→45.9 | +7.4 (9.2) | 97→97 | n/a | 51.8→53.7 | 0.40→0.47 | nan→nan | +7.3 |
| PRE | 23.1→27.8 | +4.7 (9.1) | 241→216 | -875→-843 | 55.7→61.9 | 0.10→0.13 | 0.026→0.033 | +4.7 |
| X' | 8.0→9.8 | +1.8 (5.5) | 121→66 | -420→-488 | 32.6→36.7 | 0.07→0.15 | 0.019→0.020 | +1.8 |
| ALL | 22.3→26.8 | +4.5 (5.2) | 241→216 | -1098→-1099 | 50.3→55.4 | 0.09→0.12 | 0.020→0.024 |  |

**ORB_ASIA_15 s60 (LIVE-CAL, NQ), 17.2 lots, composite, no lock** (mean $k/wk base->after, Δ and MDE, `*` beyond MDE; equal-risk = c-scaled so ALL worst-20 matches the base)

| window | mean base→after $k/wk | Δmean (MDE) | maxDD $k | worst-20 $k | SD $k | Calmar | mean/worst-20 | equal-risk Δmean |
|---|---|---|---|---|---|---|---|---|
| L3M | 34.4→46.2 | +11.8 (24.3) | 21→19 | n/a | 44.7→49.5 | 1.61→2.38 | nan→nan | +3.7 |
| L6M | 41.1→53.1 | +12.0 (14.0) | 23→23 | n/a | 42.7→47.8 | 1.80→2.32 | nan→nan | +2.6 |
| HOLD | 38.6→47.9 | +9.4 (13.1) | 97→141 | n/a | 51.8→60.5 | 0.40→0.34 | nan→nan | +0.9 |
| PRE | 23.1→25.1 | +2.0 (8.1) | 241→276 | -875→-1120 | 55.7→69.5 | 0.10→0.09 | 0.026→0.022 | -2.5 |
| X' | 8.0→4.7 | -3.2 (7.2) | 121→153 | -420→-518 | 32.6→35.5 | 0.07→0.03 | 0.019→0.009 | -4.0 |
| ALL | 22.3→24.3 | +2.1 (5.4) | 241→276 | -1098→-1333 | 50.3→61.4 | 0.09→0.09 | 0.020→0.018 |  |

**PB7 HMA55 EMA1 T2 W60 s-3 (DIRECT), 10 lots, composite, no lock** (mean $k/wk base->after, Δ and MDE, `*` beyond MDE; equal-risk = c-scaled so ALL worst-20 matches the base)

| window | mean base→after $k/wk | Δmean (MDE) | maxDD $k | worst-20 $k | SD $k | Calmar | mean/worst-20 | equal-risk Δmean |
|---|---|---|---|---|---|---|---|---|
| L3M | 34.4→42.7 | +8.3 (46.2) | 21→133 | n/a | 44.7→95.1 | 1.61→0.32 | nan→nan | -12.7 |
| L6M | 41.1→58.8 | +17.6 (29.2) | 23→133 | n/a | 42.7→87.6 | 1.80→0.44 | nan→nan | -11.3 |
| HOLD | 38.6→56.1 | +17.5 (29.6) | 97→243 | n/a | 51.8→102.8 | 0.40→0.23 | nan→nan | -10.1 |
| PRE | 23.1→37.4 | +14.3 (18.2) | 241→346 | -875→-1616 | 55.7→95.2 | 0.10→0.11 | 0.026→0.023 | -4.1 |
| X' | 8.0→15.4 | +7.5 (19.6) | 121→173 | -420→-814 | 32.6→65.0 | 0.07→0.09 | 0.019→0.019 | -0.1 |
| ALL | 22.3→35.4 | +13.2 (12.4)* | 241→346 | -1098→-2161 | 50.3→90.0 | 0.09→0.10 | 0.020→0.016 |  |

**PB7 PB5 depth_atr0.5 W15 s-3 (DIRECT), 10 lots, composite, no lock** (mean $k/wk base->after, Δ and MDE, `*` beyond MDE; equal-risk = c-scaled so ALL worst-20 matches the base)

| window | mean base→after $k/wk | Δmean (MDE) | maxDD $k | worst-20 $k | SD $k | Calmar | mean/worst-20 | equal-risk Δmean |
|---|---|---|---|---|---|---|---|---|
| L3M | 34.4→36.7 | +2.3 (34.1) | 21→95 | n/a | 44.7→73.9 | 1.61→0.38 | nan→nan | -13.9 |
| L6M | 41.1→55.2 | +14.1 (31.2) | 23→95 | n/a | 42.7→78.3 | 1.80→0.58 | nan→nan | -10.3 |
| HOLD | 38.6→51.4 | +12.9 (29.5) | 97→189 | n/a | 51.8→90.9 | 0.40→0.27 | nan→nan | -9.8 |
| PRE | 23.1→34.1 | +11.0 (16.9) | 241→242 | -875→-1426 | 55.7→90.6 | 0.10→0.14 | 0.026→0.024 | -4.0 |
| X' | 8.0→18.9 | +10.9 (17.4) | 121→221 | -420→-674 | 32.6→63.0 | 0.07→0.09 | 0.019→0.028 | +2.6 |
| ALL | 22.3→33.8 | +11.5 (11.8) | 241→242 | -1098→-1965 | 50.3→84.5 | 0.09→0.14 | 0.020→0.017 |  |

**NQ IBS_t20_n1, 4.2 lots, composite, 20R lock, sleeve routed (R2)**

| window | mean base→after $k/wk | Δmean (MDE) | maxDD $k | worst-20 $k | SD $k | Calmar | mean/worst-20 | equal-risk Δmean |
|---|---|---|---|---|---|---|---|---|
| L3M | 23.8→30.5 | +6.7 (14.3) | 64→58 | n/a | 54.7→57.0 | 0.37→0.53 | nan→nan | +6.2 |
| L6M | 34.8→39.5 | +4.7 (9.5) | 64→58 | n/a | 50.0→54.1 | 0.54→0.69 | nan→nan | +4.1 |
| HOLD | 32.0→36.1 | +4.1 (8.4) | 65→65 | n/a | 55.1→56.3 | 0.49→0.56 | nan→nan | +3.5 |
| PRE | 15.9→17.4 | +1.5 (7.5) | 190→160 | -754→-791 | 53.3→55.7 | 0.08→0.11 | 0.021→0.022 | +1.3 |
| X' | 3.3→9.3 | +6.0 (6.1) | 133→86 | -537→-484 | 32.6→36.5 | 0.02→0.11 | 0.006→0.019 | +5.9 |
| ALL | 15.8→19.3 | +3.4 (4.5) | 190→160 | -910→-924 | 49.7→51.9 | 0.08→0.12 | 0.017→0.021 |  |

All other lots / locks / frames / routings: `l2vast/ds3/out/orbcomplete/a12_metrics_long.csv` (3,936 rows: maxDD, worst-20, SD, Calmar, mean/worst-20, Δmean+MDE, equal-risk Δmean, placebo ranks, per window) and `a12_labels.csv` (656 tier rows).

## 6. Routing and method, exactly
* Lock = oc_lib combined week lock: stack MTM (all six books, every second) <= -F x R_K6, R_K6 = K6 lots x running-max-today x 60 x 20; week = ISO week of the ENTRY label day. Per frame and lock the engine is run once and the lock loop is re-run from the stash with a sleeve overlay (`code/orbcomplete/a12_lock.py`). R2 adds the sleeve to the MTM at every second (NQ sleeves: engine second prices; ES: ES 1-min closes forward-filled; PB7 cells: kept direct trades with the engine second path), realised sleeve P&L at its exit, flattens open sleeve positions at the mark of ks+1 on a fire (cost = the sleeve's round trip per contract: NQ RSI2/IBS/GSHORT $14.84, ES $29.84, ORB $44.64, PB7 cells $4.84 floor because the second-path estimate of the direct slippage was below it) and cancels sleeve entries later in that week. No-fire weeks are the stored sleeve P&L (tie-out 0.0). R1 = D1's convention.
* Cancel/truncate counts at 12R (composite): NQ RSI2 30 cancelled / 6 truncated of 72; ES RSI2 30 / 7 of 73; IBS 45 / 12; ORB 3 lots 24 / 6 of 130; PB7 HMA55 10 lots 1,710 cancelled / 77 truncated of 3,258 (52% of its entries); the lock fires in 70-78 of 149 composite weeks at 12R (71 without a sleeve).
* Equal-risk: base+sleeve scaled by one factor so the ALL worst-20 equals the base's (D1's linear convention, not the engine lot table).

## 7. Limits and disclosures
1. Direct replay of TB4W_10 and TR3_DON15_S not done (frozen governor; STRUCTURAL QUESTION open). TB4A has no real direct basis. Their rows here are MAPPED and R1-only.
2. The routed lock introduces butterfly effects on the stack (a sleeve MTM tipping a fire minutes earlier changes the stack's flatten price); these are real consequences of the rule but noisy: the routed placebo (200 draws through the same routing) is the yardstick.
3. L6M (and L3M/HOLD) composite maxDD is one week; `L6M-ONLY` therefore means the cut happened at that week, not a trend.
4. RSI2C placebo is a stopless proxy; PB7 truncation cost floor; the ORB placebo is the bar simulator (D1).
5. Loading stored series files (ES_adj.npz, TP/pb4 direct daily and tabs, struct48 trades) reads the whole file then slices at the cap; no post-cap value was inspected or kept. The library arrays of the TE machinery were truncated at the cap (TE_TRUNC=1059591 bars). The raw L2 month files were not opened by A12.
6. 11 NQ tape-defect label days remain as in D1.

Files: `autopilot/DS3_ORB_RSI2_COMPLETE.md`, `l2vast/ds3/out/orbcomplete/` (run1_*.pkl, run2_*.pkl, a12_metrics_long.csv, a12_labels.csv, a_placebo_means.csv, b_direct_vs_mapped.csv, prog_tp_tables.pkl, direct_rows.parquet, direct_tabs.pkl, dead_lookup.txt, frag_*.md), code `l2vast/ds3/code/orbcomplete/` (a12_lock.py, a12_sleeves.py, a12_plc.py, a12_run1.py, a12_run2.py, a12_prog_build.py, a12_a_placebo.py, a12_es.py, a12_metrics.py, a12_build_doc.py, a12_write_md.py, a12_rows.py, a12_direct.py (blocked)).
