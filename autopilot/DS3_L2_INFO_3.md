# DS3_L2_INFO_3 - INFO cycle 3: is there L2 information not yet scored that carries IC in the 2025-26 regime? (2026-10-31)
Prereg autopilot/DS3_L2_INFO_3_PREREG.md sha256 9012b89db2dc6a739bb303cf71d798209fd7dee51909c3aa16af52a64f2c43d7 (before any statistic); selection (PRE+X' only) files n3_sel_*.json sha256 6ccb2bbf.. a7804801.. cf1cce69.. 3b95fa95.. logged in DECISIONS.md before the one recent look. dead_lookup 0 hits. Masks capped 20260206, UNTOUCHED never read, 3 workers, OMP/MKL=1.

## Page 1 - verdict
1. **Null.** Fifty new features (1-5 s ES/RTY returns and lead vs NQ, ES/RTY micro-price offset / divergence / L1-L3 imbalance and 3-s OFI, NQ L1 time-to-exhaust and cancel share, spread-regime) were scored on 1,800 cells (4 states x 9 horizons). They carry IC of 0.02-0.07 at 1-5 s, like the known carrier, and nothing beyond it: the incremental walk-forward models (carrier + context vs carrier + context + 50 new, ridge and LightGBM, 5 s and 30 s; 64 state x model x target x window cells) have a dIC CI that excludes 0 in 12 cells: 6 are NEGATIVE (the new block hurts: sig ridge/LightGBM at 5 s in PRE/HOLD/L6M, profit 30 s in PRE, loss ridge 5 s L6M), 3 are positive only in PRE (unconditional, not repeated in L6M/HOLD/2026), and 2 are positive in the recent windows - signal-second ridge at 30 s, L6M +0.017 [+0.002,+0.029] and HOLD +0.017 [+0.004,+0.033] (PRE -0.000, 2026 +0.009 within MDE 0.049, LightGBM on the same data +0.012 [-0.007,+0.036]) - one ridge cell out of 16 recent model/target/state pairs, not a finding (a 30-s IC of 0.02 is a gross of about 0.3 pt vs 1.49).
2. **Most of the 'new' IC is the old carrier.** The PRE+X'-selected feature in profit / loss / unconditional at 1-15 s is `es_mo_div` / `rty_mo_div` = ES (RTY) micro-price offset MINUS the NQ micro-price offset; its IC (-0.062 at 1 s in profit, -0.061 under water, -0.045 unconditional) is the NQ micro-offset carrier (+0.06 in cycle 2) with the sign flipped; the ES/RTY half adds nothing in the incremental test.
3. **Genuinely different, but inside the cost:** (a) signal second: NQ L1 time-to-exhaust ahead (`q_tte_ahd`, how long the queue in front of the move lasts at the current consumption) has IC -0.058 (1 s) / -0.059 (2 s) in L6M (MDE 0.032-0.034; PRE -0.074 / -0.051; placebo rank 1/201; time-shifted -0.026; shuffled +0.015): a thick, slowly consumed far queue means a worse next seconds for the signal; implied gross 0.23-0.29 pt per action vs round trip 1.49, break-even IC 0.29-0.38. (b) signal second: ES 10-s return with the signal direction +0.057 (3 s), RTY 3-s return +0.037 at 5 s and 30 s (PRE +0.027 / +0.024), implied gross 0.26-0.52 pt vs 1.49. All are one sigma level from their PRE value.
4. **Regime (2025-26 vs PRE):** the L6M-minus-PRE difference of the 36 selected cells has |z| < 2 in 33 of 36 (z up to 2.2 in 3 cells: unc es_r5 5 s, unc es_r10 60 s, prof rty_mo_div 60 s); there is NO second regime in L2 information. The 'doubled signal' regime does not show in any new L2 feature (sig-state IC rises from 0.03 to 0.04-0.06 at 1-3 s but within MDE 0.03).
5. **Gap unchanged:** best implied gross per action 0.52 pt (sig, 30 s, rty_r3) vs cost 1.49, i.e. break-even IC 0.107 vs 0.037; profit / loss best 0.09-0.12 pt vs 0.995. No rule candidate, nothing for DS3_THL2_NEEDS.md. Cross-asset depth at 1-10 s, queue-position proxies and spread regime are now CLOSED as sources of information for the three sides.

## 1. Selected new-feature cell per state x horizon (chosen on PRE+X'; IC Spearman, side-signed; MDE = 2.8 x day-cluster SE; placebo rank = |IC| among 200 within-day shuffles of the feature, L6M)
| side   |   h s | feature      |   IC_PRE |   IC_X' |   IC_HOLD |   IC_L6M |   IC_2026 |   MDE (2.8se) | L6M-PRE         |   IC lag60 |   IC shuf |   gross pt/action |   cost |   break-even IC | placebo rank   |
|:-------|------:|:-------------|---------:|--------:|----------:|---------:|----------:|--------------:|:----------------|-----------:|----------:|------------------:|-------:|----------------:|:---------------|
| ENTRY  |     1 | q_tte_ahd    |   -0.083 |  -0.052 |    -0.068 |   -0.058 |    -0.090 |         0.032 | +0.025 (z +1.8) |     -0.026 |     0.015 |             0.230 |  1.492 |           0.379 | 1/201          |
| ENTRY  |     2 | q_tte_ahd    |   -0.050 |  -0.054 |    -0.059 |   -0.055 |    -0.080 |         0.034 | -0.006 (z -0.4) |     -0.024 |     0.002 |             0.287 |  1.492 |           0.288 | 1/201          |
| ENTRY  |     3 | es_r10       |    0.037 |   0.035 |     0.063 |    0.057 |     0.065 |         0.031 | +0.020 (z +1.5) |     -0.015 |    -0.007 |             0.337 |  1.492 |           0.253 | 1/201          |
| ENTRY  |     5 | rty_r3       |    0.027 |   0.028 |     0.040 |    0.037 |     0.068 |         0.035 | +0.010 (z +0.7) |      0.007 |     0.006 |             0.257 |  1.492 |           0.213 | 1/201          |
| ENTRY  |    10 | es_ofi3      |    0.019 |   0.016 |     0.034 |    0.032 |     0.058 |         0.030 | +0.014 (z +1.1) |     -0.025 |     0.022 |             0.294 |  1.492 |           0.165 | 1/201          |
| ENTRY  |    15 | q_tte_ahd    |   -0.020 |  -0.015 |    -0.022 |   -0.023 |    -0.044 |         0.032 | -0.003 (z -0.2) |     -0.020 |    -0.009 |             0.243 |  1.492 |           0.141 | 6/201          |
| ENTRY  |    20 | rty_imb3     |    0.013 |   0.030 |     0.001 |    0.002 |    -0.003 |         0.030 | -0.011 (z -0.9) |      0.001 |    -0.002 |             0.027 |  1.492 |           0.125 | 161/201        |
| ENTRY  |    30 | rty_r3       |    0.024 |   0.008 |     0.034 |    0.037 |     0.038 |         0.035 | +0.014 (z +1.0) |     -0.002 |     0.011 |             0.520 |  1.492 |           0.107 | 1/201          |
| ENTRY  |    60 | rty_imb3     |    0.018 |   0.031 |     0.014 |    0.016 |    -0.002 |         0.028 | -0.003 (z -0.2) |      0.007 |    -0.006 |             0.282 |  1.492 |           0.082 | 33/201         |
| PROFIT |     1 | es_mo_div    |   -0.057 |  -0.083 |    -0.064 |   -0.062 |    -0.064 |         0.015 | -0.005 (z -0.8) |     -0.006 |     0.000 |             0.094 |  0.995 |           0.653 | 1/201          |
| PROFIT |     2 | es_mo_div    |   -0.046 |  -0.068 |    -0.045 |   -0.043 |    -0.045 |         0.014 | +0.002 (z +0.4) |     -0.010 |    -0.002 |             0.092 |  0.995 |           0.470 | 1/201          |
| PROFIT |     3 | es_mo_div    |   -0.039 |  -0.059 |    -0.039 |   -0.038 |    -0.041 |         0.013 | +0.001 (z +0.1) |     -0.009 |    -0.001 |             0.094 |  0.995 |           0.406 | 1/201          |
| PROFIT |     5 | es_mo_div    |   -0.034 |  -0.048 |    -0.034 |   -0.034 |    -0.042 |         0.014 | +0.001 (z +0.1) |     -0.010 |    -0.001 |             0.100 |  0.995 |           0.335 | 1/201          |
| PROFIT |    10 | es_mo_div    |   -0.027 |  -0.037 |    -0.026 |   -0.025 |    -0.023 |         0.014 | +0.002 (z +0.3) |     -0.011 |     0.003 |             0.099 |  0.995 |           0.251 | 1/201          |
| PROFIT |    15 | es_mo_div    |   -0.026 |  -0.036 |    -0.022 |   -0.021 |    -0.026 |         0.014 | +0.005 (z +0.9) |     -0.009 |     0.004 |             0.097 |  0.995 |           0.213 | 1/201          |
| PROFIT |    20 | es_mo_div    |   -0.026 |  -0.032 |    -0.019 |   -0.019 |    -0.027 |         0.013 | +0.007 (z +1.2) |     -0.008 |     0.001 |             0.104 |  0.995 |           0.186 | 1/201          |
| PROFIT |    30 | rty_mo_div   |   -0.022 |  -0.027 |    -0.014 |   -0.015 |    -0.014 |         0.012 | +0.006 (z +1.2) |     -0.003 |     0.000 |             0.099 |  0.995 |           0.156 | 1/201          |
| PROFIT |    60 | rty_mo_div   |   -0.014 |  -0.020 |    -0.001 |   -0.002 |    -0.005 |         0.014 | +0.012 (z +2.1) |      0.002 |     0.002 |             0.020 |  0.995 |           0.116 | 69/201         |
| LOSS   |     1 | es_mo_div    |   -0.055 |  -0.078 |    -0.059 |   -0.061 |    -0.049 |         0.019 | -0.007 (z -0.8) |     -0.002 |    -0.000 |             0.119 |  0.995 |           0.514 | 1/201          |
| LOSS   |     2 | es_mo_div    |   -0.050 |  -0.067 |    -0.040 |   -0.041 |    -0.017 |         0.021 | +0.009 (z +1.1) |     -0.004 |    -0.007 |             0.103 |  0.995 |           0.395 | 1/201          |
| LOSS   |     3 | es_mo_div    |   -0.044 |  -0.062 |    -0.035 |   -0.034 |    -0.014 |         0.020 | +0.009 (z +1.2) |     -0.005 |    -0.007 |             0.099 |  0.995 |           0.347 | 1/201          |
| LOSS   |     5 | es_mo_div    |   -0.035 |  -0.051 |    -0.028 |   -0.028 |     0.002 |         0.019 | +0.007 (z +0.9) |     -0.007 |    -0.005 |             0.096 |  0.995 |           0.290 | 1/201          |
| LOSS   |    10 | rty_mo_div   |   -0.028 |  -0.050 |    -0.019 |   -0.018 |    -0.003 |         0.019 | +0.009 (z +1.2) |     -0.001 |    -0.002 |             0.083 |  0.995 |           0.218 | 1/201          |
| LOSS   |    15 | rty_mo_div   |   -0.025 |  -0.043 |    -0.014 |   -0.015 |     0.000 |         0.018 | +0.011 (z +1.4) |      0.000 |    -0.003 |             0.077 |  0.995 |           0.189 | 1/201          |
| LOSS   |    20 | rty_mo_div   |   -0.024 |  -0.038 |    -0.015 |   -0.014 |     0.004 |         0.019 | +0.010 (z +1.2) |     -0.002 |    -0.003 |             0.083 |  0.995 |           0.167 | 1/201          |
| LOSS   |    30 | rty_mo_div   |   -0.020 |  -0.026 |    -0.008 |   -0.008 |     0.021 |         0.022 | +0.012 (z +1.3) |     -0.002 |    -0.003 |             0.057 |  0.995 |           0.142 | 5/201          |
| LOSS   |    60 | q_l1_ahd_rel |   -0.013 |  -0.019 |    -0.004 |   -0.003 |     0.013 |         0.018 | +0.010 (z +1.4) |      0.008 |     0.001 |             0.031 |  0.995 |           0.105 | 59/201         |
| uncond |     1 | es_mo_div    |   -0.038 |  -0.047 |    -0.045 |   -0.045 |    -0.030 |         0.012 | -0.007 (z -1.4) |     -0.006 |     0.008 |             0.120 |  1.492 |           0.564 | 1/201          |
| uncond |     2 | es_r10       |   -0.022 |  -0.050 |    -0.013 |   -0.019 |    -0.004 |         0.018 | +0.003 (z +0.5) |      0.001 |     0.001 |             0.069 |  1.492 |           0.406 | 1/201          |
| uncond |     3 | es_r10       |   -0.021 |  -0.046 |    -0.013 |   -0.019 |     0.005 |         0.017 | +0.002 (z +0.3) |     -0.002 |    -0.001 |             0.082 |  1.492 |           0.348 | 1/201          |
| uncond |     5 | es_r5        |   -0.025 |  -0.033 |    -0.009 |   -0.012 |     0.006 |         0.015 | +0.013 (z +2.1) |     -0.001 |     0.000 |             0.062 |  1.492 |           0.282 | 1/201          |
| uncond |    10 | es_r5        |   -0.019 |  -0.029 |    -0.014 |   -0.015 |    -0.004 |         0.014 | +0.003 (z +0.6) |     -0.002 |     0.004 |             0.108 |  1.492 |           0.210 | 2/201          |
| uncond |    15 | es_r5        |   -0.022 |  -0.028 |    -0.016 |   -0.016 |    -0.006 |         0.014 | +0.006 (z +1.0) |     -0.001 |    -0.000 |             0.131 |  1.492 |           0.180 | 1/201          |
| uncond |    20 | es_r5        |   -0.020 |  -0.024 |    -0.013 |   -0.012 |    -0.004 |         0.014 | +0.008 (z +1.4) |     -0.001 |     0.000 |             0.113 |  1.492 |           0.158 | 2/201          |
| uncond |    30 | es_r10       |   -0.013 |  -0.024 |    -0.016 |   -0.015 |     0.002 |         0.014 | -0.002 (z -0.4) |      0.001 |     0.002 |             0.168 |  1.492 |           0.133 | 1/201          |
| uncond |    60 | es_r10       |   -0.009 |  -0.019 |     0.001 |    0.003 |     0.005 |         0.013 | +0.011 (z +2.2) |      0.004 |     0.005 |             0.039 |  1.492 |           0.100 | 106/201        |

Multiplicity (BH within state x window over 50 features x 9 horizons = 450 tests): L6M q<0.05: sig 139, prof 197, uw 41, unc 119 of 450 (about 22 expected by chance); these are large clusters of one signal (the carrier and its ES/RTY copies). Cumulative this cycle: 1,800 univariate + 16 model cells; cumulative with cycles 1-2 about 14.3k cells.

## 2. Incremental information beyond the carrier (walk-forward, 10 quarterly refits; windows PRE (OOS), L6M, 2026)
| state   | model   | target   | win   |   IC_base |   IC_full | dIC [95% CI]              |   MDE_dIC |   IC_full_shuf |   IC_full_lag |
|:--------|:--------|:---------|:------|----------:|----------:|:--------------------------|----------:|---------------:|--------------:|
| sig     | R       | s5       | PRE   |    0.0414 |    0.0222 | -0.0192 [-0.0300,-0.0089] |    0.0155 |         0.0208 |        0.0247 |
| sig     | R       | s5       | L6M   |    0.0434 |    0.0268 | -0.0166 [-0.0273,-0.0070] |    0.0154 |         0.0310 |        0.0420 |
| sig     | R       | s5       | 2026  |    0.0881 |    0.0696 | -0.0185 [-0.0394,+0.0021] |    0.0317 |         0.0441 |        0.0755 |
| sig     | R       | s30      | PRE   |    0.0065 |    0.0062 | -0.0003 [-0.0151,+0.0129] |    0.0197 |         0.0071 |        0.0081 |
| sig     | R       | s30      | L6M   |    0.0053 |    0.0219 | +0.0166 [+0.0016,+0.0293] |    0.0206 |         0.0053 |        0.0109 |
| sig     | R       | s30      | 2026  |    0.0637 |    0.0729 | +0.0092 [-0.0239,+0.0466] |    0.0492 |         0.0731 |        0.0371 |
| sig     | G       | s5       | PRE   |    0.0402 |    0.0224 | -0.0178 [-0.0330,-0.0030] |    0.0217 |         0.0107 |        0.0096 |
| sig     | G       | s5       | L6M   |    0.0387 |    0.0457 | +0.0070 [-0.0167,+0.0295] |    0.0335 |         0.0032 |        0.0324 |
| sig     | G       | s5       | 2026  |    0.0481 |    0.0250 | -0.0230 [-0.0705,+0.0240] |    0.0661 |         0.0062 |        0.0369 |
| sig     | G       | s30      | PRE   |    0.0073 |    0.0082 | +0.0009 [-0.0132,+0.0138] |    0.0203 |         0.0040 |        0.0125 |
| sig     | G       | s30      | L6M   |    0.0088 |    0.0206 | +0.0119 [-0.0074,+0.0356] |    0.0296 |         0.0006 |        0.0165 |
| sig     | G       | s30      | 2026  |    0.0575 |    0.0691 | +0.0116 [-0.0412,+0.0623] |    0.0772 |         0.0593 |        0.0709 |
| prof    | R       | s5       | PRE   |    0.0345 |    0.0343 | -0.0002 [-0.0041,+0.0037] |    0.0056 |         0.0204 |        0.0237 |
| prof    | R       | s5       | L6M   |    0.0506 |    0.0478 | -0.0028 [-0.0098,+0.0035] |    0.0097 |         0.0310 |        0.0306 |
| prof    | R       | s5       | 2026  |    0.0509 |    0.0511 | +0.0003 [-0.0154,+0.0174] |    0.0237 |         0.0371 |        0.0391 |
| prof    | R       | s30      | PRE   |    0.0243 |    0.0175 | -0.0069 [-0.0116,-0.0018] |    0.0072 |         0.0157 |        0.0199 |
| prof    | R       | s30      | L6M   |    0.0285 |    0.0260 | -0.0025 [-0.0108,+0.0046] |    0.0114 |         0.0206 |        0.0117 |
| prof    | R       | s30      | 2026  |    0.0315 |    0.0298 | -0.0017 [-0.0202,+0.0150] |    0.0257 |         0.0232 |        0.0213 |
| prof    | G       | s5       | PRE   |    0.0374 |    0.0397 | +0.0023 [-0.0045,+0.0083] |    0.0087 |         0.0202 |        0.0217 |
| prof    | G       | s5       | L6M   |    0.0480 |    0.0521 | +0.0041 [-0.0052,+0.0139] |    0.0142 |         0.0285 |        0.0347 |
| prof    | G       | s5       | 2026  |    0.0500 |    0.0609 | +0.0109 [-0.0078,+0.0258] |    0.0253 |         0.0229 |        0.0365 |
| prof    | G       | s30      | PRE   |    0.0215 |    0.0108 | -0.0107 [-0.0180,-0.0032] |    0.0108 |         0.0066 |        0.0103 |
| prof    | G       | s30      | L6M   |    0.0207 |    0.0278 | +0.0072 [-0.0052,+0.0198] |    0.0181 |         0.0124 |        0.0242 |
| prof    | G       | s30      | 2026  |    0.0223 |    0.0383 | +0.0160 [-0.0114,+0.0437] |    0.0407 |         0.0162 |        0.0225 |
| uw      | R       | s5       | PRE   |    0.0416 |    0.0394 | -0.0022 [-0.0087,+0.0032] |    0.0082 |         0.0303 |        0.0304 |
| uw      | R       | s5       | L6M   |    0.0393 |    0.0302 | -0.0092 [-0.0178,-0.0013] |    0.0120 |         0.0261 |        0.0328 |
| uw      | R       | s5       | 2026  |    0.0173 |    0.0096 | -0.0077 [-0.0291,+0.0177] |    0.0350 |         0.0206 |        0.0391 |
| uw      | R       | s30      | PRE   |    0.0127 |    0.0135 | +0.0009 [-0.0069,+0.0086] |    0.0116 |         0.0053 |        0.0086 |
| uw      | R       | s30      | L6M   |    0.0098 |    0.0085 | -0.0014 [-0.0117,+0.0087] |    0.0139 |         0.0089 |        0.0087 |
| uw      | R       | s30      | 2026  |   -0.0097 |    0.0029 | +0.0126 [-0.0104,+0.0374] |    0.0341 |         0.0070 |       -0.0110 |
| uw      | G       | s5       | PRE   |    0.0417 |    0.0360 | -0.0056 [-0.0139,+0.0016] |    0.0107 |         0.0255 |        0.0285 |
| uw      | G       | s5       | L6M   |    0.0300 |    0.0350 | +0.0050 [-0.0075,+0.0186] |    0.0184 |         0.0204 |        0.0230 |
| uw      | G       | s5       | 2026  |    0.0121 |    0.0204 | +0.0083 [-0.0191,+0.0391] |    0.0410 |         0.0145 |        0.0236 |
| uw      | G       | s30      | PRE   |    0.0100 |    0.0143 | +0.0043 [-0.0039,+0.0135] |    0.0128 |         0.0063 |        0.0083 |
| uw      | G       | s30      | L6M   |    0.0155 |    0.0127 | -0.0028 [-0.0159,+0.0091] |    0.0184 |         0.0055 |        0.0190 |
| uw      | G       | s30      | 2026  |   -0.0080 |    0.0014 | +0.0095 [-0.0217,+0.0410] |    0.0478 |         0.0023 |        0.0222 |
| unc     | R       | s5       | PRE   |    0.0139 |    0.0229 | +0.0090 [+0.0047,+0.0133] |    0.0062 |         0.0044 |        0.0081 |
| unc     | R       | s5       | L6M   |    0.0032 |    0.0017 | -0.0015 [-0.0100,+0.0079] |    0.0130 |        -0.0164 |       -0.0107 |
| unc     | R       | s5       | 2026  |    0.0211 |    0.0180 | -0.0031 [-0.0201,+0.0148] |    0.0240 |         0.0303 |        0.0268 |
| unc     | R       | s30      | PRE   |   -0.0006 |    0.0121 | +0.0127 [+0.0071,+0.0185] |    0.0082 |        -0.0070 |       -0.0034 |
| unc     | R       | s30      | L6M   |   -0.0019 |   -0.0023 | -0.0004 [-0.0088,+0.0073] |    0.0120 |        -0.0128 |       -0.0218 |
| unc     | R       | s30      | 2026  |    0.0121 |    0.0060 | -0.0060 [-0.0219,+0.0092] |    0.0213 |         0.0070 |        0.0000 |
| unc     | G       | s5       | PRE   |    0.0201 |    0.0266 | +0.0066 [+0.0013,+0.0111] |    0.0072 |         0.0086 |        0.0118 |
| unc     | G       | s5       | L6M   |    0.0199 |    0.0212 | +0.0013 [-0.0078,+0.0119] |    0.0143 |         0.0013 |        0.0091 |
| unc     | G       | s5       | 2026  |    0.0208 |    0.0194 | -0.0014 [-0.0194,+0.0180] |    0.0275 |         0.0198 |        0.0250 |
| unc     | G       | s30      | PRE   |    0.0099 |    0.0106 | +0.0007 [-0.0049,+0.0067] |    0.0081 |         0.0013 |        0.0055 |
| unc     | G       | s30      | L6M   |    0.0107 |    0.0032 | -0.0075 [-0.0169,+0.0028] |    0.0139 |         0.0023 |       -0.0053 |
| unc     | G       | s30      | 2026  |    0.0182 |    0.0020 | -0.0162 [-0.0352,+0.0029] |    0.0285 |         0.0106 |       -0.0046 |

Shuffled-block and time-shifted-block columns are the placebos of the FULL model (new features permuted within day / taken from 60 s earlier). The full model is not above its placebos by more than the MDE in any state, and it is below the base for sig at 5 s (PRE -0.019 [-0.030,-0.009], L6M -0.017).

## 3. Descriptive top-10 per state (L6M and HOLD, |IC|, with q and PRE IC) - not selection
Saved in out/uf/info/tables/C3_top10_descriptive.csv; the leaders are es_mo_div / rty_mo_div (carrier), q_tte_ahd and es/rty returns in the signal state.

## 4. Limits
* One fill-free information measurement: mid-to-mid moves, no execution; no trade-level P&L was run because no cell approaches the cost (implied gross <= 0.52 pt vs 0.995-1.49).
* ES/RTY tables exist only from 2023-08 (NaN before), so X' loses its first months for the cross-asset features.
* Sub-second (100-ms) lead-lag was not testable here: the 1-s tables aggregate it; the 100ms tables exist for some days only and would need a separate build.
* Code: l2vast/ds3/code/info/info3_feat.py, info3_an.py, info3_mod.py, info3_rep.py. Tables: out/uf/info/tables/C3_*.csv, n3_ic_*.parquet.
