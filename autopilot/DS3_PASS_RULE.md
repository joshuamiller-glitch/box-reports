# DS3_PASS_RULE - calibrated pass rule, ulcer-primary tiers and re-score of the candidates (W-PR2), FIRST PASS
VERDICT (data ends 2026-10-30; FIRST PASS 23:33Z; ulcer index primary; all six windows of the three closest candidates landed; engine-exact draws landed for M7 London cap 3 only): (1) H7 NY AM give-back 40/40: window tier CONFIRMED and 50/40 FAIL on arithmetic controls, but NEITHER IS MEANINGFUL - the recent windows hold 9-15 affected trades; the pooled 43 months (123 changed trades) show ulcer 0.9% WORSE than JL2, mean -563 $/wk with a 90% interval of -1,086..-149 and P(ulcer lower) 0.34: do not take it Live on this evidence. (2) M7 London cap 3: FAIL on the windows (GAP mean percentile 0.23 under the 0.25 floor, L6M/L3M P(ulcer lower) 0.20/0.12 because it is worse than JL2 in L6M); pooled 43 months ulcer 4.6% lower, P(ulcer lower) 0.78, mean -110 $/wk (interval -711..+362): a modest, unproven candidate; against 30 engine-exact draws its L6M/L3M ulcer and mean percentiles are 1.00 (random blocks of the same rate are far worse), PREUW 0.43/0.53. (3) The morning rule detects a real 10% / 20% max-DD cut only 5-13% of the time, so every 'not confirmed' it issued is VOID. Everything else: see the top table; engine-exact draws for the other candidates NOT landed yet.

Header line (desk standard 5): trials counted: step 1 = 8 planted kinds x 200 seeds + 2 noise kinds x 800 seeds x 2 control families; cut-off grid of 300 settings on noise only; candidates = 22 cells (22 trials of the corrected rule, no family correction here: see the W-DV block for White/SPA/DSR/BH/PBO); correction method: percentile among 200 controls + week-clustered bootstrap; PBO: not applicable (no fitted choice except the tier cut-offs, tuned on noise); numbers shown: in-sample (12 months HOLD+L6M of JL2 engine results), NOT walk-forward or untouched. Fees: engine dollars are base lots with engine fees; x1.75 live and $4.84 RT columns are scale factors shown in the tables.

Honest reading of two LEAD calls: the P7 Asia 50/40 give-back has ulcer worse than JL2 by 8-17% and L6M max DD 36% deeper; it reaches LEAD only because mean percentile (a random-delta control with the same trade count) is high. A LEAD that makes the stack worse on the primary statistic is not a lead; treat it as FAIL until the engine controls land.

## Step 1 - power and false positives of the CURRENT rule and of the tiers (planted edges and noise on JL2)

**What is engine-exact and what is path-arithmetic.** ENGINE-EXACT: the base is the exact-engine trade list of TL3_EV_JN05W2JL2 (JL2), 18,979 trades 2023-04..2026-10 (trades.parquet of runs_rf); its windows reproduce the page references (HOLD 2025-11..2026-04 stack max DD -74,402, L6M -22,565). PATH-ARITHMETIC: every planted and noise rule below re-weights each JL2 trade's OWN P&L (size/exit-type effect); there is NO engine re-run, so no freed-book replacement (path effect) and no re-entry. This is right for size and exit rules and optimistic for skip rules (the path effect would add noise to real skip cells). Engine re-runs of about 1,500 planted sets were not available at the 21:00Z mark, so step 1 is arithmetic by design (directive: plants can be built from the engine's own trade future R).

**Plants (from each trade's own future outcome).** Information score per trade x = d * z + AR(1, rho 0.7) noise in time order, z = rank-normal of the trade's own P&L (loser-ness for DD plants, winner-ness for mean plants); flagged = top 25% of x. DD plant: flagged trades scaled to 50% (size cut / early exit), unflagged trades scaled up multiplicatively so the full-history mean is exactly flat; the information level d is bisected so the expected cut of stack max DD (average of HOLD and L6M) is 5.0 / 10.0 / 20.0% (d = 0.038 / 0.051 / 0.085). Mean plant: lot-neutral tilt (flagged x1.5, others x0.833), d bisected so the expected mean gain is +3.0 / +6.0% (d = 0.0099 / 0.0175). Realised effect varies per seed (shown, mean +- sd). The DD plant is at flat mean (realised mean change about -0.4%); the mean plant is at DD equal to the controls (realised DD vs JL2 is -11 to -12%, the same as noise, because a random size tilt alone moves DD by +-12 points).

**Controls** (persistent draw: one uniform per 5-minute bucket per book and side; flag share 25% equal to the plant; flag share equals the plant by construction in this arithmetic). Family A: the same cut/tilt mechanism with random flags and mean restored to equal (random reallocation of the same size). Family B (the realistic skip/exit control): the plain random cut with the mean left to fall. 30 controls per candidate (the CURRENT rule uses the first 6). Noise = the same mechanism with random flags (family A equal-mean; B plain cut), so noise against its own controls is exchangeable.

**CURRENT rule** = real DD better than all 6 controls in HOLD and in L6M, and mean not below -5% of JL2 in both. **Tiers (ulcer index is the primary drawdown statistic, user order 20:28Z)** (percentile = share of 30 controls the real beats; ulcer = RMS of daily drawdown, also max DD, worst week and mean per window; recent windows L6M, L3M; older HOLD, GAP, PREUW, X'; P(ulcer lower) from 2,000 week-clustered bootstrap resamples of the paired weekly path vs JL2 on L6M, ulcer of the weekly cumulative path):
CONFIRMED: >= conf_hi percentile on ulcer or mean in L6M and in L3M, the other >= conf_other, P(ulcer lower, L6M) >= conf_pdd, ulcer percentile >= conf_old in HOLD and the older windows. LEAD: >= 0.75 percentile on ulcer or mean in L6M and L3M, nothing (ulcer or mean) below 0.25 in any window. FAIL otherwise.
Directive starting cut-offs: conf_hi 0.90, conf_other 0.40, conf_pdd 0.80, conf_old 0.25, LEAD 0.75 / 0.25.
**FINAL cut-offs (tuned on 800 pooled noise seeds per noise family and control family: CONFIRMED false positive <= 3.5%; pooled because a 400-seed tune / 400-seed validate split showed selection bias of about 1-2 points): conf_hi 0.85, conf_other 0.25, conf_pdd 0.80, conf_old 0.25, LEAD hi 0.75, LEAD floor 0.25** (change vs directive: conf_hi .90 -> .85, conf_other .40 -> .25). Measured CONFIRMED false positive 1.8-4.2% (fresh seeds, per family), LEAD-or-better 4.0-6.5%.

<!-- PR2:BEGIN -->
## RE-SCORE UNDER THE CALIBRATED RULE (W-PR2, FIRST PASS, ulcer index primary; data ends 2026-10-30; written 13:41 UTC)

**Every "not confirmed" issued under the 11-16 morning rule (beat all 6 controls on max DD in HOLD and L6M) is VOID as a negative result: that rule detects a real 10% / 20% max-DD cut only 5-13% of the time (DS3_PASS_RULE.md step 1).** Tiers below use ulcer index (RMS of daily drawdown; + = lower ulcer than JL2) and mean, percentile among 200 persistent-draw controls (PATH ARITHMETIC delta-permutation controls, not engine runs; 0 of the 30 engine-exact draws have landed; engine draws queued on server 2), week-clustered bootstrap (2,000 resamples). Cut-offs (tuned so noise reaches CONFIRMED under 5%): CONFIRMED needs ulcer-or-mean percentile >= 0.85 in L6M and L3M with the other >= 0.25, P(ulcer lower, L6M) >= 0.80, ulcer percentile >= 0.25 in the older windows run; LEAD needs >= 0.75 in L6M and L3M and nothing below 0.25 in any window run. A candidate whose older windows (GAP, PREUW, X') were not run cannot be issued CONFIRMED ("PROVISIONAL"). Old verdict = what its source page said.

| candidate | OLD verdict | NEW tier | ulcer JL2 -> real (lower = better), HOLD / L6M / L3M | pct ulcer, HOLD / L6M / L3M | P(ulcer lower) HOLD / L6M | P(max DD shallower) HOLD / L6M | 90% interval of mean change $/wk base (L6M; HOLD) | d mean $/wk base (x1.75; $4.84) L6M | max DD cut %, HOLD / L6M | DV block bootstrap, 12 months (W-DV): median DD / 95th pct DD / P(DD > 2x avg weekly profit) | not LEAD because |
|---|---|---|---|---|---|---|---|---|---|---|---|
| give-back H7 Asia 40% / 40pt | ENGINE ONLY (not CONFIRMED; controls rs101-103 are diluted copies) | **FAIL (windows GAP,PREUW,X' not run)** | 24530 -> 23683 (+3.5%) / 8356 -> 8568 (-2.5%) / 9798 -> 10189 (-4.0%) | 0.93 / 0.65 / 0.62 | 0.55 / 0.35 | 0.60 / 0.37 | -1691..-6; -373..+1131 | -841 (-1472; -840) | +3.6% / -6.0% | -59228 / -95725 / 1.00 | L6M best pct 0.65<0.75; L3M best pct 0.68<0.75; L6M mean pct 0.15<0.25 |
| give-back H7 Asia 60% / 30pt | ENGINE ONLY (not CONFIRMED) | **FAIL (windows GAP,PREUW,X' not run)** | 24530 -> 24376 (+0.6%) / 8356 -> 8590 (-2.8%) / 9798 -> 10364 (-5.8%) | 0.76 / 0.62 / 0.50 | 0.57 / 0.46 | 0.54 / 0.37 | -2555..-110; +166..+1818 | -1271 (-2224; -1265) | +2.7% / -10.9% | -59140 / -96289 / 1.00 | L6M best pct 0.62<0.75; L3M best pct 0.50<0.75; L3M mean pct 0.07<0.25; L6M mean pct 0.04<0.25 |
| give-back K7 NY AM 40% / 40pt | ENGINE ONLY (not CONFIRMED) | **FAIL (windows GAP,PREUW,X' not run)** | 24530 -> 23854 (+2.8%) / 8356 -> 8418 (-0.7%) / 9798 -> 9867 (-0.7%) | 0.47 / 0.34 / 0.39 | 0.68 / 0.55 | 0.73 / 0.43 | -324..+879; -350..+578 | +263 (+460; +257) | -1.2% / -2.0% | -59882 / -95754 / 1.00 | L6M best pct 0.39<0.75; HOLD mean pct 0.10<0.25 |
| give-back K7 NY AM 50% / 20pt | ENGINE ONLY (not CONFIRMED) | **FAIL (windows GAP,PREUW,X' not run)** | 24530 -> 25085 (-2.3%) / 8356 -> 8686 (-4.0%) / 9798 -> 10294 (-5.1%) | 0.28 / 0.17 / 0.18 | 0.42 / 0.18 | 0.43 / 0.17 | -999..+313; -1412..+523 | -345 (-603; -354) | -5.3% / -7.9% | -62101 / -99494 / 1.00 | L6M best pct 0.17<0.75; L3M best pct 0.64<0.75; L3M ulcer pct 0.18<0.25; L6M mean pct 0.06<0.25; HOLD mean pct 0.04<0.25 |
| give-back P7 Asia 40% / 40pt | ENGINE ONLY (not CONFIRMED; L6M DD -40%) | **FAIL (windows GAP,PREUW,X' not run)** | 24530 -> 27326 (-11.4%) / 8356 -> 9882 (-18.3%) / 9798 -> 12052 (-23.0%) | 0.86 / 0.81 / 0.74 | 0.34 / 0.17 | 0.29 / 0.12 | -4492..-1364; -1471..+2390 | -2989 (-5232; -3022) | -0.4% / -40.2% | -60164 / -103010 / 1.00 | L3M best pct 0.74<0.75 |
| give-back P7 Asia 50% / 40pt | ENGINE ONLY (not CONFIRMED; L6M DD -36%) | **LEAD (older windows GAP,PREUW,X' not run)** | 24530 -> 26443 (-7.8%) / 8356 -> 9416 (-12.7%) / 9798 -> 11470 (-17.1%) | 0.90 / 0.88 / 0.80 | 0.27 / 0.22 | 0.22 / 0.27 | -3969..+101; -1634..+2135 | -1978 (-3462; -2002) | -1.5% / -36.2% | -59294 / -101238 / 1.00 | LEAD floor met |
| give-back P7 NY AM 40% / 30pt | ENGINE ONLY (not CONFIRMED) | **FAIL (windows GAP,PREUW,X' not run)** | 24530 -> 24320 (+0.9%) / 8356 -> 8363 (-0.1%) / 9798 -> 9809 (-0.1%) | 0.79 / 0.74 / 0.64 | 0.54 / 0.03 | 0.53 / 0.49 | -757..+71; -539..+180 | -308 (-538; -308) | +1.6% / +0.0% | -61010 / -96717 / 1.00 | L6M best pct 0.74<0.75; L3M best pct 0.64<0.75; L3M mean pct 0.21<0.25; L6M mean pct 0.20<0.25 |
| A7 Asia fixed target 45 / stop 60 | ENGINE ONLY (not CONFIRMED; HOLD DD +0.1%, L6M +4.7%) | **FAIL (windows GAP,PREUW,X' not run)** | 24530 -> 24934 (-1.7%) / 8356 -> 8574 (-2.6%) / 9798 -> 9688 (+1.1%) | 0.51 / 0.43 / 0.69 | 0.52 / 0.56 | 0.50 / 0.72 | -1297..+249; -618..+846 | -572 (-1001; -580) | +0.1% / +4.7% | -59856 / -97322 / 1.00 | L6M best pct 0.43<0.75; L3M best pct 0.69<0.75; L3M mean pct 0.15<0.25; L6M mean pct 0.09<0.25 |
| against-the-day (VWAP) skip, all books | not scored under old rule (persistent controls aK84s1-3 built; INVALID-or-unverified list) | **FAIL (windows GAP not run)** | 24530 -> 27238 (-11.0%) / 8356 -> 9711 (-16.2%) / 9798 -> 11824 (-20.7%) | 0.17 / 0.21 / 0.23 | 0.34 / 0.14 | 0.37 / 0.16 | -3675..+2785; -1346..+1790 | -493 (-864; -470) | +3.1% / -26.3% | -64731 / -104596 / 1.00 | L3M ulcer pct 0.23<0.25; L6M ulcer pct 0.21<0.25; HOLD ulcer pct 0.17<0.25; X' ulcer pct 0.23<0.25 |
| against-the-day target 20 (3-of-4 vote), M7 NY AM | ENGINE ONLY (zero effect in HOLD/L6M) | **FAIL (windows GAP,PREUW,X' not run)** | 24530 -> 24530 (+0.0%) / 8356 -> 8356 (+0.0%) / 9798 -> 9798 (+0.0%) | 0.50 / 0.50 / 0.50 | 0.00 / 0.00 | 0.50 / 0.50 | +0..+0; +0..+0 | +0 (+0; +0) | +0.0% / +0.0% | -61074 / -97706 / 1.00 | L6M best pct 0.50<0.75; L3M best pct 0.50<0.75 |
| against-the-day target 20 (3-of-4 vote), O7 NY AM | ENGINE ONLY (zero effect in HOLD/L6M) | **FAIL (windows GAP,PREUW,X' not run)** | 24530 -> 24530 (+0.0%) / 8356 -> 8356 (+0.0%) / 9798 -> 9798 (+0.0%) | 0.50 / 0.50 / 0.50 | 0.00 / 0.00 | 0.50 / 0.50 | +0..+0; +0..+0 | +0 (+0; +0) | +0.0% / +0.0% | -61074 / -97706 / 1.00 | L6M best pct 0.50<0.75; L3M best pct 0.50<0.75 |
| U7 Asia fixed 40x40 | VOID (fixsub controls not persistent); beats-random statements withdrawn | **FAIL (windows GAP not run)** | 24530 -> 24627 (-0.4%) / 8356 -> 7484 (+10.4%) / 9798 -> 8684 (+11.4%) | 0.71 / 0.99 / 0.97 | 0.55 / 0.86 | 0.53 / 0.84 | -775..+3144; -1498..+3558 | +1151 (+2014; +1116) | +9.7% / +12.6% | -54731 / -89125 / 0.98 | PREUW ulcer pct 0.24<0.25; X' mean pct 0.03<0.25 |
| A7 Asia fixed 40x40 (morning bracket cell) | ENGINE ONLY / VOID (fixsub controls not persistent) | **FAIL (windows GAP,PREUW,X' not run)** | 24530 -> 29317 (-19.5%) / 8356 -> 10388 (-24.3%) / 9798 -> 12852 (-31.2%) | 0.01 / 0.03 / 0.03 | 0.25 / 0.88 | 0.37 / 0.63 | -3135..+1084; -3945..+1146 | -1060 (-1855; -1078) | +2.9% / -45.2% | -66845 / -104522 / 1.00 | L6M best pct 0.18<0.75; L3M best pct 0.03<0.75; L3M mean pct 0.01<0.25; L6M ulcer pct 0.03<0.25; HOLD ulcer pct 0.01<0.25 |
| K7 NY AM fixed 40x40 (morning bracket cell) | ENGINE ONLY / VOID (fixsub controls not persistent) | **FAIL (windows GAP,PREUW,X' not run)** | 24530 -> 26560 (-8.3%) / 8356 -> 8556 (-2.4%) / 9798 -> 10118 (-3.3%) | 0.10 / 0.34 / 0.34 | 0.10 / 0.26 | 0.19 / 0.20 | -376..+1411; -1424..+500 | +489 (+856; +466) | -14.2% / -5.3% | -65546 / -103317 / 1.00 | L6M best pct 0.59<0.75; HOLD mean pct 0.05<0.25 |
| K7 NY AM fixed 40x60 (morning bracket cell) | ENGINE ONLY / VOID (fixsub controls not persistent) | **FAIL (windows HOLD,GAP,X' not run)** | n/a / 8356 -> 8489 (-1.6%) / 9798 -> 9962 (-1.7%) | n/a / 0.34 / 0.38 | n/a / 0.32 | n/a / 0.20 | -275..+1033; n/a | +377 (+659; +371) | n/a / -5.3% | not in DV table | PREUW mean pct 0.20<0.25 |
| K7 London fixed 40x60 (morning bracket cell) | ENGINE ONLY / VOID (fixsub controls not persistent) | **FAIL (windows GAP,PREUW,X' not run)** | 24530 -> 26957 (-9.9%) / 8356 -> 8578 (-2.6%) / 9798 -> 9510 (+2.9%) | 0.23 / 0.68 / 0.86 | 0.46 / 0.61 | 0.54 / 0.47 | -2491..-237; -1295..+957 | -1410 (-2468; -1421) | -2.3% / +2.6% | -62242 / -99017 / 1.00 | L6M best pct 0.68<0.75; L3M mean pct 0.09<0.25; L6M mean pct 0.01<0.25; HOLD ulcer pct 0.23<0.25 |
| London skip k=1.25 true points, M7+P7 | UNVERIFIED (PD controls not run; RK controls INVALID) | **FAIL** | 24530 -> 26600 (-8.4%) / 8356 -> 7257 (+13.2%) / 9798 -> 7786 (+20.5%) | 0.17 / 0.96 / 0.99 | 0.67 / 0.95 | 0.60 / 0.97 | -518..+2867; -1412..+1107 | +1200 (+2100; +1240) | -8.6% / +0.2% | -62212 / -97117 / 0.99 | HOLD ulcer pct 0.17<0.25 |
| London skip k=1.25 with UC, M7+P7 | UNVERIFIED (RKUC controls INVALID) | **LEAD (older windows PREUW,X' not run)** | 24530 -> 24548 (-0.1%) / 8356 -> 7567 (+9.4%) / 9798 -> 8141 (+16.9%) | 0.49 / 0.82 / 0.90 | 0.71 / 0.79 | 0.64 / 0.83 | -1356..+2168; -1402..+1362 | +408 (+714; +459) | +0.8% / +0.2% | not in DV table | LEAD floor met |
| M7 London cap 3 (block entry after 3 closes) | NOT PASS under the morning rule: DD worse than best control in HOLD (-70,924 vs -63,564) and L6M (-23,715 vs -22,397); placebos partly INVALID (keep 0.70-0.73 vs 0.62) | **FAIL** | 24530 -> 22302 (+9.1%) / 8356 -> 8055 (+3.6%) / 9798 -> 9454 (+3.5%) | 0.98 / 0.69 / 0.55 | 0.97 / 0.20 | 0.96 / 0.18 | +771..+2655; -654..+1108 | +1747 (+3058; +1768) | +4.7% / -5.1% | -59277 / -90315 / 0.99 | GAP mean pct 0.23<0.25 |
| give-back H7 NY AM 40% / 40pt | ENGINE ONLY (not CONFIRMED) | **CONFIRMED** | 24530 -> 24257 (+1.1%) / 8356 -> 8076 (+3.3%) / 9798 -> 9368 (+4.4%) | 0.87 / 1.00 / 1.00 | 0.66 / 0.88 | 0.57 / 0.87 | -171..+354; -191..+329 | +82 (+143; +82) | +2.5% / +0.0% | -60523 / -96415 / 1.00 | LEAD floor met |
| give-back H7 NY AM 50% / 40pt | ENGINE ONLY (not CONFIRMED) | **FAIL** | 24530 -> 24246 (+1.2%) / 8356 -> 8112 (+2.9%) / 9798 -> 9424 (+3.8%) | 0.88 / 1.00 / 0.99 | 0.65 / 0.88 | 0.57 / 0.86 | -134..+355; -203..+296 | +97 (+169; +97) | +2.4% / +0.0% | -60685 / -96554 / 1.00 | GAP mean pct 0.22<0.25; PREUW ulcer pct 0.21<0.25 |
| JL2 reference (for scale) | - | - | HOLD 24530 / L6M 8356 / L3M 9798 | - | - | - | - | - | - | -61074 / -97706 / 1.00 | - |
| the three profit lines, as designed vs as coded | not scored (replay only: DS3_PROFIT_LINES_REPLAY.md) | **NOT ENOUGH CONTROLS YET** (no engine cell of either version exists on JL2; /mnt/l2/l2vast/_jointexit has identity cells only) | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | not finished |

**Detectable mean effect (power floor).** The paired weekly P&L difference of a typical candidate has a standard error of the mean change of about the 90% interval half-width / 1.645; the effect detectable at 80% power (one-sided 5%) is 2.49 x SE. From the candidates above, that floor in L6M (27 weeks) is 1426 $/wk base and in HOLD (26 weeks) 1460 $/wk base (median over candidates with changed trades); JL2 earns about 22,076 $/wk in L6M and 8,359 in HOLD. Planted mean gains confirm it: of planted +3 / +6 / +10 / +20 / +40% mean gains, the 90% interval of the mean change excludes zero in BOTH HOLD and L6M for 2 / 4 / 8 / 44 / 98% of seeds, and the tiers (ulcer+mean) reach LEAD-or-better for 11 / 16 / 29 / 66 / 90%. **Plain: a rule that touches one book x session needs about +1,000 $/wk base (pooled HOLD+L6M, 53 weeks; about +7% of the average stack mean of 15,000 $/wk) to be proven at 80% power, and a rule that re-weights a quarter of all trades needs about +30% (+5,000 $/wk). Smaller mean gains - including every +3% / +6% effect - cannot be proven on 12 months; they need the full 43 months or live incubation.**

Engine-exact vs arithmetic: real cells and JL2 are exact-engine trade lists. Controls are 200 persistent-bucket draws (one draw per 5-minute bucket per book and side, realised affected share within 0.05 of the real rule, printed in the detail table); exit/size/target/label rules deal the real rule's per-lot P&L deltas to random trades, skip rules remove random trades. They have no freed-book replacement trades and do not match minutes-since-entry or open profit at exit, so the exit-rule control is approximate until the engine controls land. The first scoring pass ran before its prereg line was appended to DECISIONS.md.
## Older-window progress for the two closest candidates (real cells landing from server 2; arithmetic controls unless engine draws are noted)

| candidate | window | landed | JL2 trades in scope | real trades in scope | trades that differ from JL2 | weeks touched | ulcer change vs JL2 | pct ulcer / mean | P(ulcer lower) | tier |
|---|---|---|---|---|---|---|---|---|---|---|
| M7 London cap 3 (block entry after 3 closes) | L6M | yes | 512 | 349 | 163 | 26 | +3.6% | 0.69 / 1.00 | 0.20 | FAIL |
| M7 London cap 3 (block entry after 3 closes) | L3M | yes | 236 | 175 | 61 | 13 | +3.5% | 0.55 / 0.99 | 0.12 |  |
| M7 London cap 3 (block entry after 3 closes) | HOLD | yes | 451 | 325 | 126 | 22 | +9.1% | 0.98 / 0.74 | 0.97 |  |
| M7 London cap 3 (block entry after 3 closes) | GAP | yes | 135 | 125 | 10 | 6 | +1.4% | 0.51 / 0.23 | 0.65 |  |
| M7 London cap 3 (block entry after 3 closes) | PREUW | yes | 568 | 451 | 117 | 30 | +7.8% | 0.78 / 0.98 | 0.85 |  |
| M7 London cap 3 (block entry after 3 closes) | X' | yes | 689 | 653 | 36 | 11 | +0.3% | 0.65 / 0.55 | 0.73 |  |
| M7 London cap 3 (block entry after 3 closes) | **tier now** | | | | | | | | | **FAIL** |
| give-back H7 NY AM 40% / 40pt | L6M | yes | 38 | 38 | 15 | 13 | +3.3% | 1.00 / 0.86 | 0.88 | CONFIRMED |
| give-back H7 NY AM 40% / 40pt | L3M | yes | 18 | 18 | 9 | 8 | +4.4% | 1.00 / 0.88 | 0.66 |  |
| give-back H7 NY AM 40% / 40pt | HOLD | yes | 40 | 41 | 13 | 10 | +1.1% | 0.87 / 0.82 | 0.66 |  |
| give-back H7 NY AM 40% / 40pt | GAP | yes | 26 | 26 | 9 | 8 | +0.5% | 0.68 / 0.30 | 0.57 |  |
| give-back H7 NY AM 40% / 40pt | PREUW | yes | 76 | 77 | 36 | 24 | -3.0% | 0.27 / 0.35 | 0.41 |  |
| give-back H7 NY AM 40% / 40pt | X' | yes | 169 | 169 | 50 | 41 | -0.1% | 0.72 / 0.40 | 0.42 |  |
| give-back H7 NY AM 40% / 40pt | **tier now** | | | | | | | | | **CONFIRMED** |
| give-back H7 NY AM 50% / 40pt | L6M | yes | 38 | 38 | 12 | 11 | +2.9% | 1.00 / 0.84 | 0.88 | FAIL |
| give-back H7 NY AM 50% / 40pt | L3M | yes | 18 | 18 | 8 | 7 | +3.8% | 0.99 / 0.82 | 0.65 |  |
| give-back H7 NY AM 50% / 40pt | HOLD | yes | 40 | 40 | 11 | 9 | +1.2% | 0.88 / 0.78 | 0.65 |  |
| give-back H7 NY AM 50% / 40pt | GAP | yes | 26 | 26 | 8 | 7 | +0.4% | 0.68 / 0.22 | 0.51 |  |
| give-back H7 NY AM 50% / 40pt | PREUW | yes | 76 | 76 | 33 | 23 | -3.5% | 0.21 / 0.23 | 0.36 |  |
| give-back H7 NY AM 50% / 40pt | X' | yes | 169 | 169 | 45 | 36 | -0.1% | 0.77 / 0.39 | 0.37 |  |
| give-back H7 NY AM 50% / 40pt | **tier now** | | | | | | | | | **FAIL** |

Meaning at small counts: H7 NY AM has 78 JL2 trades in the 12 months (23-28 differ from JL2); a 6-month window holds about a dozen affected trades in a handful of weeks, so a percentile among controls that change the same number of random trades is mostly the luck of which weeks are touched. Treat any H7 NY AM tier below 40 affected trades per window as NOT MEANINGFUL (it can neither confirm nor reject); only the pooled 43-month count (about 100 affected trades) can carry a verdict.

## Pooled 43 months (2023-04..2026-10, 187 weeks) vs JL2, the two H7 NY AM give-backs and M7 London cap 3

| cell | ulcer JL2 -> real | max DD JL2 -> real | mean $/wk change | affected trades | boot P(ulcer lower) / P(max DD shallower) | 90% interval mean change |
|---|---|---|---|---|---|---|
| H7 NY AM 40/40 | 20293 -> 20482 (-0.9%) | -74402 -> -72608 | -563 | 123 changed + 486 skipped | 0.34 / 0.54 | -1086 .. -149 |
| H7 NY AM 50/40 | 20293 -> 20523 (-1.1%) | -74402 -> -72658 | -589 | 109 changed + 485 skipped | 0.29 / 0.53 | -1115 .. -172 |
| M7 London cap 3 | 20293 -> 19365 (+4.6%) | -74402 -> -71239 | -110 | 14 changed + 950 skipped | 0.78 / 0.78 | -711 .. +362 |

## Engine-exact draws landed so far (TL3_PC_<ID>_S1..S30 = JL2 + persistent-draw control hook; 30 draws asked per candidate)

A draw counts in a window only if every month of the window landed and its realised share pooled over all months it shares with the real cell (>= 12 months) is within 0.05 (strict; 0.10 relaxed in brackets) of the real rule share over the same months (per-window shares of 10-40 trades are too noisy for a 0.05 test; they are displayed). Percentiles are among valid draws; a window with fewer than 10 valid draws is excluded from the tier ("not enough valid draws").

Note: the M7 London cap draws realise a share about 0.03-0.06 below the real rule (calibrated on two pilot months), so many windows fail the strict 0.05 test; both readings are shown. Candidates with no draws yet are marked NOT ENOUGH CONTROLS YET.

| candidate | window | real share | draws landed (of 30) | valid strict [relaxed] | control share mean | pct ulcer / mean / max DD (strict) | P(ulcer lower) vs JL2 | engine tier (strict) |
|---|---|---|---|---|---|---|---|---|
| give-back H7 NY AM 40/40 (v2 p) | L3M | 0.500 | 30 | 21 [30] | 0.27 | 0.90 / 1.00 / 0.50 | 0.66 |  |
| give-back H7 NY AM 40/40 (v2 p) | L6M | 0.395 | 30 | 21 [30] | 0.229 | 0.95 / 0.95 / 0.50 | 0.88 |  |
| give-back H7 NY AM 40/40 (v2 p) | HOLD | 0.325 | 30 | 21 [30] | 0.282 | 0.86 / 0.62 / 1.00 | 0.66 |  |
| give-back H7 NY AM 40/40 (v2 p) | GAP | 0.346 | 30 | 21 [30] | 0.446 | 0.48 / 0.81 / 0.57 | 0.57 |  |
| give-back H7 NY AM 40/40 (v2 p) | PREUW | 0.474 | 30 | 21 [30] | 0.356 | 0.38 / 0.38 / 0.43 | 0.41 |  |
| give-back H7 NY AM 40/40 (v2 p) | X' | 0.296 | 30 | 21 [30] | 0.425 | 0.24 / 0.43 / 0.86 | 0.42 |  |
| give-back H7 NY AM 40/40 (v2 p) | pooled validity (months shared with the real cell >= 12): 30 draws pooled, 21 valid, control share 0.374 vs real 0.352 | | | | | | | |
| give-back H7 NY AM 40/40 (v2 p) | **tier (engine draws, strict 0.05)** | | | | | | | **FAIL** |
| give-back H7 NY AM 40/40 (v2 p) | tier (engine draws, relaxed 0.10; share bias of the draws, see note) | | | | | | | FAIL |
| give-back H7 NY AM 50/40 (v2 p) | L3M | 0.444 | 30 | 19 [30] | 0.239 | 0.74 / 1.00 / 0.50 | 0.65 |  |
| give-back H7 NY AM 50/40 (v2 p) | L6M | 0.316 | 30 | 19 [30] | 0.205 | 0.89 / 1.00 / 0.50 | 0.88 |  |
| give-back H7 NY AM 50/40 (v2 p) | HOLD | 0.275 | 30 | 19 [30] | 0.267 | 0.84 / 0.58 / 1.00 | 0.65 |  |
| give-back H7 NY AM 50/40 (v2 p) | GAP | 0.308 | 30 | 19 [30] | 0.399 | 0.42 / 0.58 / 0.34 | 0.51 |  |
| give-back H7 NY AM 50/40 (v2 p) | PREUW | 0.434 | 30 | 19 [30] | 0.318 | 0.21 / 0.11 / 0.26 | 0.36 |  |
| give-back H7 NY AM 50/40 (v2 p) | X' | 0.266 | 30 | 19 [30] | 0.393 | 0.05 / 0.26 / 0.89 | 0.37 |  |
| give-back H7 NY AM 50/40 (v2 p) | pooled validity (months shared with the real cell >= 12): 30 draws pooled, 19 valid, control share 0.342 vs real 0.312 | | | | | | | |
| give-back H7 NY AM 50/40 (v2 p) | **tier (engine draws, strict 0.05)** | | | | | | | **FAIL** |
| give-back H7 NY AM 50/40 (v2 p) | tier (engine draws, relaxed 0.10; share bias of the draws, see note) | | | | | | | FAIL |
| M7 London cap 3 | L3M | 0.353 | 30 | 30 [30] | 0.342 | 1.00 / 1.00 / 0.97 | 0.12 |  |
| M7 London cap 3 | L6M | 0.421 | 30 | 30 [30] | 0.365 | 1.00 / 1.00 / 0.97 | 0.20 |  |
| M7 London cap 3 | HOLD | 0.388 | 30 | 30 [30] | 0.322 | 0.60 / 0.13 / 0.23 | 0.97 |  |
| M7 London cap 3 | GAP | 0.145 | 30 | 30 [30] | 0.211 | 0.13 / 0.00 / 0.10 | 0.65 |  |
| M7 London cap 3 | PREUW | 0.310 | 30 | 30 [30] | 0.3 | 0.43 / 0.53 / 0.33 | 0.85 |  |
| M7 London cap 3 | X' | 0.117 | 30 | 30 [30] | 0.239 | 0.83 / 0.53 / 0.67 | 0.73 |  |
| M7 London cap 3 | pooled validity (months shared with the real cell >= 12): 30 draws pooled, 30 valid, control share 0.305 vs real 0.308 | | | | | | | |
| M7 London cap 3 | **tier (engine draws, strict 0.05)** | | | | | | | **FAIL** |
| M7 London cap 3 | tier (engine draws, relaxed 0.10; share bias of the draws, see note) | | | | | | | FAIL |
| London skip k=1.25 UC M7+P7 | L3M | 0.349 | 30 | 0 [30] | 0.297 | not enough valid draws | - |  |
| London skip k=1.25 UC M7+P7 | L6M | 0.351 | 30 | 0 [30] | 0.327 | not enough valid draws | - |  |
| London skip k=1.25 UC M7+P7 | HOLD | 0.411 | 30 | 0 [30] | 0.293 | not enough valid draws | - |  |
| London skip k=1.25 UC M7+P7 | GAP | 0.558 | 0 | 0 [0] | None | not enough valid draws | - |  |
| London skip k=1.25 UC M7+P7 | PREUW | real cell not landed | - | - | - | - | - | - |
| London skip k=1.25 UC M7+P7 | X' | real cell not landed | - | - | - | - | - | - |
| London skip k=1.25 UC M7+P7 | pooled validity (months shared with the real cell >= 12): 30 draws pooled, 0 valid, control share 0.312 vs real 0.378 | | | | | | | |
| London skip k=1.25 UC M7+P7 | **tier (engine draws, strict 0.05)** | | | | | | | **NOT FINISHED (recent windows missing)** |
| London skip k=1.25 UC M7+P7 | tier (engine draws, relaxed 0.10; share bias of the draws, see note) | | | | | | | LEAD (older windows GAP,PREUW,X' not run) |
| give-back P7 Asia 50/40 | L3M | 0.289 | 30 | 0 [0] | 0.492 | not enough valid draws | - |  |
| give-back P7 Asia 50/40 | L6M | 0.286 | 30 | 0 [0] | 0.396 | not enough valid draws | - |  |
| give-back P7 Asia 50/40 | HOLD | 0.254 | 30 | 0 [0] | 0.635 | not enough valid draws | - |  |
| give-back P7 Asia 50/40 | GAP | 0.343 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back P7 Asia 50/40 | PREUW | 0.288 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back P7 Asia 50/40 | X' | 0.289 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back P7 Asia 50/40 | pooled validity (months shared with the real cell >= 12): 30 draws pooled, 0 valid, control share 0.490 vs real 0.273 | | | | | | | |
| give-back P7 Asia 50/40 | **tier (engine draws, strict 0.05)** | | | | | | | **NOT FINISHED (recent windows missing)** |
| give-back P7 Asia 50/40 | tier (engine draws, relaxed 0.10; share bias of the draws, see note) | | | | | | | NOT FINISHED (recent windows missing) |
| London skip k=1.25 true pts M7+P7 | L3M | 0.280 | 30 | 19 [30] | 0.242 | 1.00 / 1.00 / 1.00 | 0.87 |  |
| London skip k=1.25 true pts M7+P7 | L6M | 0.283 | 30 | 19 [30] | 0.269 | 1.00 / 1.00 / 1.00 | 0.95 |  |
| London skip k=1.25 true pts M7+P7 | HOLD | 0.327 | 30 | 19 [30] | 0.239 | 0.16 / 0.11 / 0.11 | 0.67 |  |
| London skip k=1.25 true pts M7+P7 | GAP | 0.488 | 0 | 0 [0] | None | not enough valid draws | - |  |
| London skip k=1.25 true pts M7+P7 | PREUW | 0.434 | 0 | 0 [0] | None | not enough valid draws | - |  |
| London skip k=1.25 true pts M7+P7 | X' | 0.402 | 0 | 0 [0] | None | not enough valid draws | - |  |
| London skip k=1.25 true pts M7+P7 | pooled validity (months shared with the real cell >= 12): 30 draws pooled, 19 valid, control share 0.256 vs real 0.303 | | | | | | | |
| London skip k=1.25 true pts M7+P7 | **tier (engine draws, strict 0.05)** | | | | | | | **FAIL (windows GAP,PREUW,X' not run)** |
| London skip k=1.25 true pts M7+P7 | tier (engine draws, relaxed 0.10; share bias of the draws, see note) | | | | | | | FAIL (windows GAP,PREUW,X' not run) |
| give-back K7 NY AM 40/40 | L3M | 0.312 | 30 | 26 [30] | 0.301 | 0.31 / 1.00 / 0.38 | 0.10 |  |
| give-back K7 NY AM 40/40 | L6M | 0.322 | 30 | 26 [30] | 0.268 | 0.23 / 0.88 / 0.38 | 0.55 |  |
| give-back K7 NY AM 40/40 | HOLD | 0.292 | 30 | 26 [30] | 0.302 | 0.92 / 0.96 / 0.81 | 0.68 |  |
| give-back K7 NY AM 40/40 | GAP | 0.347 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back K7 NY AM 40/40 | PREUW | 0.342 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back K7 NY AM 40/40 | X' | 0.300 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back K7 NY AM 40/40 | pooled validity (months shared with the real cell >= 12): 30 draws pooled, 26 valid, control share 0.287 vs real 0.306 | | | | | | | |
| give-back K7 NY AM 40/40 | **tier (engine draws, strict 0.05)** | | | | | | | **FAIL (windows GAP,PREUW,X' not run)** |
| give-back K7 NY AM 40/40 | tier (engine draws, relaxed 0.10; share bias of the draws, see note) | | | | | | | FAIL (windows GAP,PREUW,X' not run) |
| A7 Asia target 45 | L3M | 0.412 | 30 | 0 [3] | 0.623 | not enough valid draws | - |  |
| A7 Asia target 45 | L6M | 0.459 | 30 | 0 [3] | 0.552 | not enough valid draws | - |  |
| A7 Asia target 45 | HOLD | 0.507 | 30 | 0 [3] | 0.787 | not enough valid draws | - |  |
| A7 Asia target 45 | GAP | 0.469 | 0 | 0 [0] | None | not enough valid draws | - |  |
| A7 Asia target 45 | PREUW | 0.587 | 0 | 0 [0] | None | not enough valid draws | - |  |
| A7 Asia target 45 | X' | 0.554 | 0 | 0 [0] | None | not enough valid draws | - |  |
| A7 Asia target 45 | pooled validity (months shared with the real cell >= 12): 30 draws pooled, 0 valid, control share 0.640 vs real 0.477 | | | | | | | |
| A7 Asia target 45 | **tier (engine draws, strict 0.05)** | | | | | | | **NOT FINISHED (recent windows missing)** |
| A7 Asia target 45 | tier (engine draws, relaxed 0.10; share bias of the draws, see note) | | | | | | | NOT FINISHED (recent windows missing) |
| U7 Asia 40x40 | L3M | 0.931 | 30 | 0 [0] | 0.622 | not enough valid draws | - |  |
| U7 Asia 40x40 | L6M | 0.930 | 0 | 0 [0] | None | not enough valid draws | - |  |
| U7 Asia 40x40 | HOLD | 0.945 | 0 | 0 [0] | None | not enough valid draws | - |  |
| U7 Asia 40x40 | GAP | 1.000 | 0 | 0 [0] | None | not enough valid draws | - |  |
| U7 Asia 40x40 | PREUW | 0.985 | 0 | 0 [0] | None | not enough valid draws | - |  |
| U7 Asia 40x40 | X' | 0.982 | 0 | 0 [0] | None | not enough valid draws | - |  |
| U7 Asia 40x40 | pooled validity (months shared with the real cell >= 12): 0 draws pooled, 0 valid, control share n/a vs real n/a | | | | | | | |
| U7 Asia 40x40 | **tier (engine draws, strict 0.05)** | | | | | | | **NOT FINISHED (recent windows missing)** |
| U7 Asia 40x40 | tier (engine draws, relaxed 0.10; share bias of the draws, see note) | | | | | | | NOT FINISHED (recent windows missing) |
| against-the-day VWAP skip all books | L3M | 0.033 | 30 | 30 [30] | 0.054 | 0.73 / 1.00 / 0.83 | 0.00 |  |
| against-the-day VWAP skip all books | L6M | 0.036 | 30 | 30 [30] | 0.055 | 0.67 / 0.90 / 0.83 | 0.14 |  |
| against-the-day VWAP skip all books | HOLD | 0.035 | 30 | 30 [30] | 0.041 | 0.27 / 0.70 / 0.57 | 0.34 |  |
| against-the-day VWAP skip all books | GAP | 0.023 | 0 | 0 [0] | None | not enough valid draws | - |  |
| against-the-day VWAP skip all books | PREUW | 0.028 | 0 | 0 [0] | None | not enough valid draws | - |  |
| against-the-day VWAP skip all books | X' | 0.018 | 0 | 0 [0] | None | not enough valid draws | - |  |
| against-the-day VWAP skip all books | pooled validity (months shared with the real cell >= 12): 30 draws pooled, 30 valid, control share 0.049 vs real 0.036 | | | | | | | |
| against-the-day VWAP skip all books | **tier (engine draws, strict 0.05)** | | | | | | | **LEAD (older windows GAP,PREUW,X' not run)** |
| against-the-day VWAP skip all books | tier (engine draws, relaxed 0.10; share bias of the draws, see note) | | | | | | | LEAD (older windows GAP,PREUW,X' not run) |
| give-back K7 NY AM 50/20 | L3M | 0.578 | 30 | 0 [0] | 0.983 | not enough valid draws | - |  |
| give-back K7 NY AM 50/20 | L6M | 0.574 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back K7 NY AM 50/20 | HOLD | 0.531 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back K7 NY AM 50/20 | GAP | 0.629 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back K7 NY AM 50/20 | PREUW | 0.584 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back K7 NY AM 50/20 | X' | 0.585 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back K7 NY AM 50/20 | pooled validity (months shared with the real cell >= 12): 0 draws pooled, 0 valid, control share n/a vs real n/a | | | | | | | |
| give-back K7 NY AM 50/20 | **tier (engine draws, strict 0.05)** | | | | | | | **NOT FINISHED (recent windows missing)** |
| give-back K7 NY AM 50/20 | tier (engine draws, relaxed 0.10; share bias of the draws, see note) | | | | | | | NOT FINISHED (recent windows missing) |
| give-back P7 Asia 40/40 | L3M | 0.322 | 30 | 0 [0] | 0.386 | not enough valid draws | - |  |
| give-back P7 Asia 40/40 | L6M | 0.321 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back P7 Asia 40/40 | HOLD | 0.296 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back P7 Asia 40/40 | GAP | 0.382 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back P7 Asia 40/40 | PREUW | 0.315 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back P7 Asia 40/40 | X' | 0.320 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back P7 Asia 40/40 | pooled validity (months shared with the real cell >= 12): 0 draws pooled, 0 valid, control share n/a vs real n/a | | | | | | | |
| give-back P7 Asia 40/40 | **tier (engine draws, strict 0.05)** | | | | | | | **NOT FINISHED (recent windows missing)** |
| give-back P7 Asia 40/40 | tier (engine draws, relaxed 0.10; share bias of the draws, see note) | | | | | | | NOT FINISHED (recent windows missing) |
| give-back H7 Asia 40/40 | L3M | 0.303 | 30 | 0 [0] | 0.343 | not enough valid draws | - |  |
| give-back H7 Asia 40/40 | L6M | 0.381 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back H7 Asia 40/40 | HOLD | 0.298 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back H7 Asia 40/40 | GAP | 0.269 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back H7 Asia 40/40 | PREUW | 0.387 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back H7 Asia 40/40 | X' | 0.387 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back H7 Asia 40/40 | pooled validity (months shared with the real cell >= 12): 0 draws pooled, 0 valid, control share n/a vs real n/a | | | | | | | |
| give-back H7 Asia 40/40 | **tier (engine draws, strict 0.05)** | | | | | | | **NOT FINISHED (recent windows missing)** |
| give-back H7 Asia 40/40 | tier (engine draws, relaxed 0.10; share bias of the draws, see note) | | | | | | | NOT FINISHED (recent windows missing) |
| give-back H7 Asia 60/30 | L3M | 0.439 | 30 | 0 [0] | 0.439 | not enough valid draws | - |  |
| give-back H7 Asia 60/30 | L6M | 0.460 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back H7 Asia 60/30 | HOLD | 0.351 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back H7 Asia 60/30 | GAP | 0.462 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back H7 Asia 60/30 | PREUW | 0.423 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back H7 Asia 60/30 | X' | 0.490 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back H7 Asia 60/30 | pooled validity (months shared with the real cell >= 12): 0 draws pooled, 0 valid, control share n/a vs real n/a | | | | | | | |
| give-back H7 Asia 60/30 | **tier (engine draws, strict 0.05)** | | | | | | | **NOT FINISHED (recent windows missing)** |
| give-back H7 Asia 60/30 | tier (engine draws, relaxed 0.10; share bias of the draws, see note) | | | | | | | NOT FINISHED (recent windows missing) |
| give-back P7 NY AM 40/30 | L3M | 0.483 | 30 | 0 [0] | 0.656 | not enough valid draws | - |  |
| give-back P7 NY AM 40/30 | L6M | 0.442 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back P7 NY AM 40/30 | HOLD | 0.500 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back P7 NY AM 40/30 | GAP | 0.438 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back P7 NY AM 40/30 | PREUW | 0.310 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back P7 NY AM 40/30 | X' | 0.494 | 0 | 0 [0] | None | not enough valid draws | - |  |
| give-back P7 NY AM 40/30 | pooled validity (months shared with the real cell >= 12): 0 draws pooled, 0 valid, control share n/a vs real n/a | | | | | | | |
| give-back P7 NY AM 40/30 | **tier (engine draws, strict 0.05)** | | | | | | | **NOT FINISHED (recent windows missing)** |
| give-back P7 NY AM 40/30 | tier (engine draws, relaxed 0.10; share bias of the draws, see note) | | | | | | | NOT FINISHED (recent windows missing) |

<!-- PR2:END -->

#### Control family A: controls restored to equal mean (random reallocation of the same size)

| planted rule | realised DD cut vs JL2 (avg HOLD, L6M; mean +- sd across seeds) | realised mean change | CURRENT rule pass, 20 seeds | CURRENT rule pass, 200 seeds | tiers DIRECTIVE cut-offs: CONFIRMED / LEAD-or-better, 200 | tiers TUNED cut-offs: CONFIRMED / LEAD-or-better, 200 |
|---|---|---|---|---|---|---|
| dd5 | +5.4% +- 10.6 | -0.3% | 20% (4/20) | 12% | 6% / 11% | 12% / 15% |
| dd10 | +10.7% +- 9.1 | -0.4% | 10% (2/20) | 13% | 9% / 12% | 14% / 15% |
| dd20 | +20.8% +- 7.0 | -0.5% | 10% (2/20) | 12% | 2% / 3% | 7% / 7% |
| mean3 | -12.3% +- 12.5 | +3.7% | 5% (1/20) | 4% | 1% / 11% | 2% / 11% |
| mean6 | -10.7% +- 12.3 | +6.5% | 5% (1/20) | 5% | 2% / 16% | 3% / 16% |
| mean10 | -8.6% +- 11.8 | +10.2% | 5% (1/20) | 8% | 7% / 29% | 8% / 29% |
| mean20 | -4.2% +- 11.0 | +20.2% | 5% (1/20) | 12% | 22% / 66% | 22% / 66% |
| mean40 | +4.1% +- 9.4 | +40.0% | 30% (6/20) | 29% | 56% / 90% | 56% / 90% |
| noise_dd (FALSE POSITIVE) | n/a | n/a | 0% (0/20) | 1.2% (400) | 1.5% / 3.8% | 2.5% / 4.8% ; fresh 400 seeds: 2.5% / 4.0% |
| noise_mean (FALSE POSITIVE) | n/a | n/a | 0% (0/20) | 1.5% (400) | 2.0% / 4.2% | 2.2% / 4.5% ; fresh 400 seeds: 1.8% / 4.5% |

#### Control family B: controls are the plain random cut (mean falls)

| planted rule | realised DD cut vs JL2 (avg HOLD, L6M; mean +- sd across seeds) | realised mean change | CURRENT rule pass, 20 seeds | CURRENT rule pass, 200 seeds | tiers DIRECTIVE cut-offs: CONFIRMED / LEAD-or-better, 200 | tiers TUNED cut-offs: CONFIRMED / LEAD-or-better, 200 |
|---|---|---|---|---|---|---|
| dd5 | +5.4% +- 10.6 | -0.3% | 5% (1/20) | 3% | 18% / 36% | 19% / 36% |
| dd10 | +10.7% +- 9.1 | -0.4% | 0% (0/20) | 5% | 33% / 54% | 35% / 54% |
| dd20 | +20.8% +- 7.0 | -0.5% | 5% (1/20) | 6% | 69% / 92% | 76% / 92% |
| mean3 | -12.3% +- 12.5 | +3.7% | 5% (1/20) | 4% | 1% / 11% | 2% / 11% |
| mean6 | -10.7% +- 12.3 | +6.5% | 5% (1/20) | 5% | 2% / 16% | 3% / 16% |
| mean10 | -8.6% +- 11.8 | +10.2% | 5% (1/20) | 8% | 7% / 29% | 8% / 29% |
| mean20 | -4.2% +- 11.0 | +20.2% | 5% (1/20) | 12% | 22% / 66% | 22% / 66% |
| mean40 | +4.1% +- 9.4 | +40.0% | 30% (6/20) | 29% | 56% / 90% | 56% / 90% |
| noise_dd (FALSE POSITIVE) | n/a | n/a | 0% (0/20) | 0.0% (400) | 1.8% / 4.5% | 2.5% / 4.5% ; fresh 400 seeds: 4.2% / 6.5% |
| noise_mean (FALSE POSITIVE) | n/a | n/a | 0% (0/20) | 1.5% (400) | 2.0% / 4.2% | 2.2% / 4.5% ; fresh 400 seeds: 1.8% / 4.5% |

#### Mean-effect detectability (80%% power floor), 200 seeds

| planted mean gain | tiers (ulcer+mean) CONFIRMED / LEAD-or-better, family A | same, family B | 90%% interval of mean change excludes 0 in BOTH HOLD and L6M | mean percentile >= 90th in BOTH HOLD and L6M |
|---|---|---|---|---|
| mean3 (realised +3.7%) | 2% / 11% | 2% / 11% | 2% | 6% |
| mean6 (realised +6.5%) | 3% / 16% | 3% / 16% | 4% | 12% |
| mean10 (realised +10.2%) | 8% / 29% | 8% / 29% | 8% | 24% |
| mean20 (realised +20.2%) | 22% / 66% | 22% / 66% | 44% | 66% |
| mean40 (realised +40.0%) | 56% / 90% | 56% / 90% | 98% | 99% |

Reading the step-1 tables: CURRENT rule = share of seeds passing the morning rule (20 seeds as ordered, 200 for precision); tier columns give CONFIRMED / LEAD-or-better under the ulcer tiers (LEAD-or-better includes CONFIRMED). The 10% DD plant passes the current rule in 2 of 20 seeds (family A) and 0 of 20 (family B).

**Plain statements.** (1) The morning rule's power on a true 10% DD cut at flat mean is 13% (family A) / 5% (family B): it rejects real effects. (2) The cause is noise: the DD cut of a random rule of the same frequency varies with sd 7-17 points between draws, and max DD sits in a few weeks. (3) With ulcer as the primary statistic the CONFIRMED tier keeps false positives under 5% and reaches 35% power at a 10% cut and 76% at 20% against plain random-cut controls (family B, the right control for skip and exit rules), but only 14% / 7% against equal-mean random reallocation (family A, a much harder control that also rewards random up-sizing of unflagged trades). (4) Mean gains: of planted +3 / +6 / +10 / +20 / +40% mean gains the 90% interval of the mean change excludes 0 in both HOLD and L6M for 2 / 4 / 8 / 44 / 98% of seeds. At 80% power the floor for these broad plants (25% of all trades re-weighted) is about +30% of the stack mean (about +5,000 $/wk base); for a rule that touches one book x session the paired-week SE gives about +1,000 $/wk base (about +7%). Small mean gains cannot be proven on 12 months and need the full 43 months or live incubation. (5) Max DD alone is the weaker statistic: percentile at >= 90th in both HOLD and L6M has power 35 / 52 / 88% for 5 / 10 / 20% cuts at 3.5% false positive, ulcer 49 / 72 / 97%.

Code: code/th_passrule (pr_lib.py, pr_plant.py, pr_step1.py, pr_report2.py, pr_cands.py, pr_run26.py, pr_tab27.py); raw results /mnt/l2/l2vast/_passrule. The prereg line was appended to DECISIONS.md after the first scoring pass had run (the page keeps this note); no threshold was changed after seeing candidate results.


## Engine-exact controls (status)
Hook built: code/th_passrule/pc_hooks.py (outermost hook on JL2; persistent draw = one crc32 uniform per seed, kind, book, side and 300-second bucket): `skip` (random skip at the real rule's skipped share), `count` (random block only after >= 1 close in the book x Globex-day x session instance, at the real block rate; M7 London cap 3 stand-in), `rx` (random exit: a drawn trade takes one (minutes since entry, open profit points) pair from the real rule's early exits and exits at market at the first second with both reached; same share, same minutes distribution; open profit is a floor so the realised open-profit distribution is measured and printed). Parameters measured from the real cells (pc_params.json): e.g. H7 NY AM 40/40 early-exit share 0.359 (28 of 78), M7 London block rate 0.406 of entries with >= 1 close, London skip UC 0.379, P7 Asia 50/40 0.273.
Sets TL3_PC_<ID>_S<k> (JL2 + pc_hooks). Queue /mnt/l2/l2vast/_s2/pc_pending.txt appended LAST in /mnt/l2/l2vast/_s2/QUEUES.txt (behind D10 / BD deadline sets, T-JOINT-EXIT, EV, REBUILD, FLOW, CONFL). Step A (queued): identity cell TL3_PC_ID (p = 0, must equal JL2 on 202610) and 15 calibration pilots TL3_PC_<ID>_S0 on 202609-202610 to calibrate p so the realised share is within 0.05 of the real rule. Step B (after the pilots read): 30 draws x 12 months (202511..202610) per candidate in tier order: H7 NY AM x2, M7 London cap 3, London skip UC, P7 Asia 50/40, London skip true points, K7 NY AM, A7 T45, U7 40x40, VWAP skip, then the rest. Nothing from 202611 on. The scorer pc_score.py rebuilds the tier table from the landed draws (valid = realised share within 0.05; invalid draws excluded and counted). Until then the table above uses the arithmetic controls and says so.

## Steps 2-6 detail (ulcer first, then max DD, worst week, mean; x1.75 live and $4.84 repriced)

| candidate | window | ulcer JL2 -> real (change) | pct ulcer / max DD / worst wk / mean (n=200) | pct ulcer real-arith | boot P(ulcer lower) / P(max DD shallower) / P(worst wk better) | max DD JL2 -> real (cut %) | worst week JL2 -> real | d mean/wk (x1.75; $4.84) | 90% interval mean change | MDE 80% | W44 removed: ulcer change, pct ulcer, P(ulcer lower) | DV bootstrap H12 (real cell): median DD / 95th DD / P(DD>2x avg wk profit) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| give-back H7 Asia 40% / 40pt | L6M | 8356 -> 8568 (-2.5%) | 0.65 / 0.77 / 0.73 / 0.15 | n/a | 0.35 / 0.37 / 0.41 | -22565 -> -23908 (-6.0%) | -13430 -> -13430 | -841 (-1472; -840) | -1691 .. -6 | 1276 | -2.5%, 0.66, 0.47 |  |
| give-back H7 Asia 40% / 40pt | L3M | 9798 -> 10189 (-4.0%) | 0.62 / 0.77 / 0.71 / 0.68 | n/a | 0.03 / 0.21 / 0.35 | -22565 -> -23908 (-6.0%) | -13430 -> -13430 | -131 (-228; -127) | -911 .. +699 | 1218 | -4.5%, 0.62, 0.05 |  |
| give-back H7 Asia 40% / 40pt | HOLD | 24530 -> 23683 (+3.5%) | 0.93 / 0.85 / 0.82 / 0.95 | n/a | 0.55 / 0.60 / 0.93 | -74402 -> -71746 (+3.6%) | -31211 -> -31074 | +378 (+661; +377) | -373 .. +1131 | 1138 | +3.5%, 0.93, 0.56 |  |
| give-back H7 Asia 60% / 30pt | L6M | 8356 -> 8590 (-2.8%) | 0.62 / 0.61 / 0.70 / 0.04 | n/a | 0.46 / 0.37 / 0.40 | -22565 -> -25023 (-10.9%) | -13430 -> -13430 | -1271 (-2224; -1265) | -2555 .. -110 | 1851 | -3.2%, 0.60, 0.54 |  |
| give-back H7 Asia 60% / 30pt | L3M | 9798 -> 10364 (-5.8%) | 0.50 / 0.61 / 0.67 / 0.07 | n/a | 0.00 / 0.14 / 0.33 | -22565 -> -25023 (-10.9%) | -13430 -> -13430 | -1263 (-2210; -1255) | -2448 .. -30 | 1830 | -7.3%, 0.52, 0.00 |  |
| give-back H7 Asia 60% / 30pt | HOLD | 24530 -> 24376 (+0.6%) | 0.76 / 0.69 / 0.38 / 0.99 | n/a | 0.57 / 0.54 / 0.31 | -74402 -> -72429 (+2.7%) | -31211 -> -33394 | +1033 (+1808; +1030) | +166 .. +1818 | 1251 | +0.6%, 0.76, 0.59 |  |
| give-back K7 NY AM 40% / 40pt | L6M | 8356 -> 8418 (-0.7%) | 0.34 / 0.67 / 0.56 / 0.39 | n/a | 0.55 / 0.43 / 0.39 | -22565 -> -23010 (-2.0%) | -13430 -> -13430 | +263 (+460; +257) | -324 .. +879 | 910 | -0.5%, 0.42, 0.64 |  |
| give-back K7 NY AM 40% / 40pt | L3M | 9798 -> 9867 (-0.7%) | 0.39 / 0.67 / 0.56 / 0.89 | n/a | 0.10 / 0.23 / 0.35 | -22565 -> -23010 (-2.0%) | -13430 -> -13430 | +925 (+1619; +918) | +134 .. +1617 | 1122 | -0.3%, 0.46, 0.13 |  |
| give-back K7 NY AM 40% / 40pt | HOLD | 24530 -> 23854 (+2.8%) | 0.47 / 0.20 / 0.78 / 0.10 | n/a | 0.68 / 0.73 / 0.95 | -74402 -> -75309 (-1.2%) | -31211 -> -30699 | +125 (+218; +118) | -350 .. +578 | 702 | +2.8%, 0.47, 0.67 |  |
| give-back K7 NY AM 50% / 20pt | L6M | 8356 -> 8686 (-4.0%) | 0.17 / 0.28 / 0.30 / 0.06 | n/a | 0.18 / 0.17 / 0.06 | -22565 -> -24340 (-7.9%) | -13430 -> -14211 | -345 (-603; -354) | -999 .. +313 | 993 | -3.2%, 0.26, 0.35 |  |
| give-back K7 NY AM 50% / 20pt | L3M | 9798 -> 10294 (-5.1%) | 0.18 / 0.28 / 0.30 / 0.64 | n/a | 0.00 / 0.03 / 0.01 | -22565 -> -24340 (-7.9%) | -13430 -> -14211 | +283 (+496; +270) | -444 .. +976 | 1074 | -4.3%, 0.29, 0.00 |  |
| give-back K7 NY AM 50% / 20pt | HOLD | 24530 -> 25085 (-2.3%) | 0.28 / 0.12 / 0.58 / 0.04 | n/a | 0.42 / 0.43 / 0.29 | -74402 -> -78354 (-5.3%) | -31211 -> -31604 | -356 (-622; -370) | -1412 .. +523 | 1464 | -2.3%, 0.28, 0.41 |  |
| give-back P7 Asia 40% / 40pt | L6M | 8356 -> 9882 (-18.3%) | 0.81 / 0.59 / 0.52 / 0.52 | n/a | 0.17 / 0.12 / 0.03 | -22565 -> -31640 (-40.2%) | -13430 -> -18172 | -2989 (-5232; -3022) | -4492 .. -1364 | 2368 | -21.9%, 0.81, 0.15 |  |
| give-back P7 Asia 40% / 40pt | L3M | 9798 -> 12052 (-23.0%) | 0.74 / 0.57 / 0.39 / 0.74 | n/a | 0.09 / 0.09 / 0.07 | -22565 -> -31640 (-40.2%) | -13430 -> -18172 | -1171 (-2049; -1215) | -2808 .. +538 | 2532 | -29.9%, 0.72, 0.00 |  |
| give-back P7 Asia 40% / 40pt | HOLD | 24530 -> 27326 (-11.4%) | 0.86 / 0.78 / 0.58 / 0.98 | n/a | 0.34 / 0.29 / 0.04 | -74402 -> -74710 (-0.4%) | -31211 -> -35108 | +317 (+555; +290) | -1471 .. +2390 | 2922 | -11.4%, 0.86, 0.35 |  |
| give-back P7 Asia 50% / 40pt | L6M | 8356 -> 9416 (-12.7%) | 0.88 / 0.64 / 0.63 / 0.67 | n/a | 0.22 / 0.27 / 0.12 | -22565 -> -30727 (-36.2%) | -13430 -> -17244 | -1978 (-3462; -2002) | -3969 .. +101 | 3080 | -15.8%, 0.85, 0.13 |  |
| give-back P7 Asia 50% / 40pt | L3M | 9798 -> 11470 (-17.1%) | 0.80 / 0.61 / 0.51 / 0.74 | n/a | 0.27 / 0.34 / 0.30 | -22565 -> -30727 (-36.2%) | -13430 -> -17244 | -1029 (-1801; -1060) | -3303 .. +1355 | 3525 | -23.2%, 0.77, 0.00 |  |
| give-back P7 Asia 50% / 40pt | HOLD | 24530 -> 26443 (-7.8%) | 0.90 / 0.78 / 0.58 / 0.97 | n/a | 0.27 / 0.22 / 0.03 | -74402 -> -75505 (-1.5%) | -31211 -> -34923 | +80 (+139; +59) | -1634 .. +2135 | 2852 | -7.8%, 0.90, 0.30 |  |
| give-back P7 NY AM 40% / 30pt | L6M | 8356 -> 8363 (-0.1%) | 0.74 / 0.76 / 0.60 / 0.20 | n/a | 0.03 / 0.49 / 0.50 | -22565 -> -22565 (+0.0%) | -13430 -> -13430 | -308 (-538; -308) | -757 .. +71 | 627 | -0.1%, 0.74, 0.02 |  |
| give-back P7 NY AM 40% / 30pt | L3M | 9798 -> 9809 (-0.1%) | 0.64 / 0.76 / 0.60 / 0.21 | n/a | 0.01 / 0.48 / 0.50 | -22565 -> -22565 (+0.0%) | -13430 -> -13430 | -491 (-859; -491) | -1324 .. +260 | 1199 | -0.1%, 0.64, 0.00 |  |
| give-back P7 NY AM 40% / 30pt | HOLD | 24530 -> 24320 (+0.9%) | 0.79 / 0.79 / 0.55 / 0.47 | n/a | 0.54 / 0.53 / 0.31 | -74402 -> -73222 (+1.6%) | -31211 -> -31662 | -132 (-231; -133) | -539 .. +180 | 544 | +0.9%, 0.79, 0.53 |  |
| A7 Asia fixed target 45 / stop 60 | L6M | 8356 -> 8574 (-2.6%) | 0.43 / 0.95 / 0.70 / 0.09 | n/a | 0.56 / 0.72 / 0.91 | -22565 -> -21503 (+4.7%) | -13430 -> -13002 | -572 (-1001; -580) | -1297 .. +249 | 1170 | -4.0%, 0.34, 0.28 |  |
| A7 Asia fixed target 45 / stop 60 | L3M | 9798 -> 9688 (+1.1%) | 0.69 / 0.95 / 0.70 / 0.15 | n/a | 0.84 / 0.93 / 0.95 | -22565 -> -21503 (+4.7%) | -13430 -> -13002 | -568 (-994; -577) | -1587 .. +498 | 1578 | -0.1%, 0.62, 0.54 |  |
| A7 Asia fixed target 45 / stop 60 | HOLD | 24530 -> 24934 (-1.7%) | 0.51 / 0.54 / 0.78 / 0.61 | n/a | 0.52 / 0.50 / 0.66 | -74402 -> -74364 (+0.1%) | -31211 -> -31106 | +87 (+152; +86) | -618 .. +846 | 1108 | -1.7%, 0.51, 0.53 |  |
| against-the-day (VWAP) skip, all books | L6M | 8356 -> 9711 (-16.2%) | 0.21 / 0.35 / 0.07 / 0.94 | n/a | 0.14 / 0.16 / 0.10 | -22565 -> -28494 (-26.3%) | -13430 -> -23429 | -493 (-864; -470) | -3675 .. +2785 | 4889 | -16.7%, 0.28, 0.39 |  |
| against-the-day (VWAP) skip, all books | L3M | 9798 -> 11824 (-20.7%) | 0.23 / 0.34 / 0.04 / 0.94 | n/a | 0.00 / 0.03 / 0.02 | -22565 -> -28494 (-26.3%) | -13430 -> -23429 | +1158 (+2027; +1177) | -3483 .. +6121 | 7269 | -22.8%, 0.28, 0.00 |  |
| against-the-day (VWAP) skip, all books | HOLD | 24530 -> 27238 (-11.0%) | 0.17 / 0.24 / 0.40 / 0.83 | n/a | 0.34 / 0.37 / 0.32 | -74402 -> -72108 (+3.1%) | -31211 -> -31437 | +207 (+362; +229) | -1346 .. +1790 | 2373 | -11.0%, 0.17, 0.34 |  |
| against-the-day target 20 (3-of-4 vote), M7 NY AM | L6M | 8356 -> 8356 (+0.0%) | 0.50 / 0.50 / 0.50 / 0.50 | n/a | 0.00 / 0.50 / 0.50 | -22565 -> -22565 (+0.0%) | -13430 -> -13430 | +0 (+0; +0) | +0 .. +0 | 0 | +0.0%, 0.50, 0.00 |  |
| against-the-day target 20 (3-of-4 vote), M7 NY AM | L3M | 9798 -> 9798 (+0.0%) | 0.50 / 0.50 / 0.50 / 0.50 | n/a | 0.00 / 0.50 / 0.50 | -22565 -> -22565 (+0.0%) | -13430 -> -13430 | +0 (+0; +0) | +0 .. +0 | 0 | +0.0%, 0.50, 0.00 |  |
| against-the-day target 20 (3-of-4 vote), M7 NY AM | HOLD | 24530 -> 24530 (+0.0%) | 0.50 / 0.50 / 0.50 / 0.50 | n/a | 0.00 / 0.50 / 0.50 | -74402 -> -74402 (+0.0%) | -31211 -> -31211 | +0 (+0; +0) | +0 .. +0 | 0 | +0.0%, 0.50, 0.00 |  |
| against-the-day target 20 (3-of-4 vote), O7 NY AM | L6M | 8356 -> 8356 (+0.0%) | 0.50 / 0.50 / 0.50 / 0.50 | n/a | 0.00 / 0.50 / 0.50 | -22565 -> -22565 (+0.0%) | -13430 -> -13430 | +0 (+0; +0) | +0 .. +0 | 0 | +0.0%, 0.50, 0.00 |  |
| against-the-day target 20 (3-of-4 vote), O7 NY AM | L3M | 9798 -> 9798 (+0.0%) | 0.50 / 0.50 / 0.50 / 0.50 | n/a | 0.00 / 0.50 / 0.50 | -22565 -> -22565 (+0.0%) | -13430 -> -13430 | +0 (+0; +0) | +0 .. +0 | 0 | +0.0%, 0.50, 0.00 |  |
| against-the-day target 20 (3-of-4 vote), O7 NY AM | HOLD | 24530 -> 24530 (+0.0%) | 0.50 / 0.50 / 0.50 / 0.50 | n/a | 0.00 / 0.50 / 0.50 | -74402 -> -74402 (+0.0%) | -31211 -> -31211 | +0 (+0; +0) | +0 .. +0 | 0 | +0.0%, 0.50, 0.00 |  |
| U7 Asia fixed 40x40 | L6M | 8356 -> 7484 (+10.4%) | 0.99 / 1.00 / 0.95 / 0.87 | n/a | 0.86 / 0.84 / 0.91 | -22565 -> -19715 (+12.6%) | -13430 -> -10253 | +1151 (+2014; +1116) | -775 .. +3144 | 2966 | +9.0%, 0.96, 0.64 |  |
| U7 Asia fixed 40x40 | L3M | 9798 -> 8684 (+11.4%) | 0.97 / 1.00 / 0.97 / 0.88 | n/a | 0.87 / 0.94 / 0.95 | -22565 -> -19400 (+14.0%) | -13430 -> -6939 | +1716 (+3004; +1682) | -645 .. +3781 | 3349 | +9.3%, 0.92, 0.62 |  |
| U7 Asia fixed 40x40 | HOLD | 24530 -> 24627 (-0.4%) | 0.71 / 0.80 / 0.56 / 0.84 | n/a | 0.55 / 0.53 / 0.26 | -74402 -> -67152 (+9.7%) | -31211 -> -33286 | +1155 (+2022; +1124) | -1498 .. +3558 | 3826 | -0.4%, 0.71, 0.56 |  |
| A7 Asia fixed 40x40 (morning bracket cell) | L6M | 8356 -> 10388 (-24.3%) | 0.03 / 0.03 / 0.72 / 0.18 | n/a | 0.88 / 0.63 / 0.33 | -22565 -> -32772 (-45.2%) | -13430 -> -13709 | -1060 (-1855; -1078) | -3135 .. +1084 | 3193 | -31.6%, 0.01, 0.77 |  |
| A7 Asia fixed 40x40 (morning bracket cell) | L3M | 9798 -> 12852 (-31.2%) | 0.03 / 0.03 / 0.71 / 0.01 | n/a | 0.58 / 0.42 / 0.25 | -22565 -> -32772 (-45.2%) | -13430 -> -13709 | -2417 (-4230; -2433) | -5549 .. +749 | 4766 | -43.9%, 0.01, 0.11 |  |
| A7 Asia fixed 40x40 (morning bracket cell) | HOLD | 24530 -> 29317 (-19.5%) | 0.01 / 0.78 / 0.98 / 0.01 | n/a | 0.25 / 0.37 / 0.96 | -74402 -> -72222 (+2.9%) | -31211 -> -28915 | -1305 (-2284; -1304) | -3945 .. +1146 | 3853 | -19.5%, 0.01, 0.25 |  |
| K7 NY AM fixed 40x40 (morning bracket cell) | L6M | 8356 -> 8556 (-2.4%) | 0.34 / 0.44 / 0.25 / 0.59 | n/a | 0.26 / 0.20 / 0.03 | -22565 -> -23765 (-5.3%) | -13430 -> -14595 | +489 (+856; +466) | -376 .. +1411 | 1353 | -1.9%, 0.42, 0.35 |  |
| K7 NY AM fixed 40x40 (morning bracket cell) | L3M | 9798 -> 10118 (-3.3%) | 0.34 / 0.45 / 0.25 / 0.92 | n/a | 0.01 / 0.03 / 0.02 | -22565 -> -23765 (-5.3%) | -13430 -> -14595 | +1524 (+2667; +1498) | +224 .. +2664 | 1847 | -2.7%, 0.42, 0.01 |  |
| K7 NY AM fixed 40x40 (morning bracket cell) | HOLD | 24530 -> 26560 (-8.3%) | 0.10 / 0.01 / 0.12 / 0.05 | n/a | 0.10 / 0.19 / 0.31 | -74402 -> -84992 (-14.2%) | -31211 -> -35148 | -431 (-754; -460) | -1424 .. +500 | 1456 | -8.3%, 0.10, 0.10 |  |
| K7 NY AM fixed 40x60 (morning bracket cell) | L6M | 8356 -> 8489 (-1.6%) | 0.34 / 0.11 / 0.40 / 0.76 | n/a | 0.32 / 0.20 / 0.03 | -22565 -> -23765 (-5.3%) | -13430 -> -13831 | +377 (+659; +371) | -275 .. +1033 | 990 | -0.9%, 0.45, 0.49 |  |
| K7 NY AM fixed 40x60 (morning bracket cell) | L3M | 9798 -> 9962 (-1.7%) | 0.38 / 0.11 / 0.40 / 0.97 | n/a | 0.02 / 0.04 / 0.02 | -22565 -> -23765 (-5.3%) | -13430 -> -13831 | +1118 (+1957; +1110) | +258 .. +1888 | 1234 | -0.6%, 0.48, 0.01 |  |
| K7 London fixed 40x60 (morning bracket cell) | L6M | 8356 -> 8578 (-2.6%) | 0.68 / 0.93 / 0.41 / 0.01 | n/a | 0.61 / 0.47 / 0.32 | -22565 -> -21970 (+2.6%) | -13430 -> -14936 | -1410 (-2468; -1421) | -2491 .. -237 | 1706 | -6.7%, 0.45, 0.23 |  |
| K7 London fixed 40x60 (morning bracket cell) | L3M | 9798 -> 9510 (+2.9%) | 0.86 / 0.93 / 0.41 / 0.09 | n/a | 0.51 / 0.40 / 0.24 | -22565 -> -21970 (+2.6%) | -13430 -> -14936 | -1390 (-2432; -1405) | -2474 .. -60 | 1827 | -2.2%, 0.73, 0.00 |  |
| K7 London fixed 40x60 (morning bracket cell) | HOLD | 24530 -> 26957 (-9.9%) | 0.23 / 0.46 / 0.88 / 0.63 | n/a | 0.46 / 0.54 / 0.97 | -74402 -> -76096 (-2.3%) | -31211 -> -30842 | -194 (-339; -201) | -1295 .. +957 | 1705 | -9.9%, 0.23, 0.47 |  |
| London skip k=1.25 true points, M7+P7 | L6M | 8356 -> 7257 (+13.2%) | 0.96 / 0.57 / 0.56 / 0.96 | n/a | 0.95 / 0.97 / 0.99 | -22565 -> -22508 (+0.2%) | -13430 -> -12590 | +1200 (+2100; +1240) | -518 .. +2867 | 2562 | +11.3%, 0.90, 0.84 |  |
| London skip k=1.25 true points, M7+P7 | L3M | 9798 -> 7786 (+20.5%) | 0.99 / 0.57 / 0.49 / 0.99 | n/a | 0.87 / 0.94 / 0.96 | -22565 -> -22508 (+0.2%) | -13430 -> -12590 | +2205 (+3859; +2247) | -502 .. +4580 | 3846 | +19.6%, 0.94, 0.63 |  |
| London skip k=1.25 true points, M7+P7 | HOLD | 24530 -> 26600 (-8.4%) | 0.17 / 0.03 / 0.05 / 0.57 | n/a | 0.67 / 0.60 / 0.35 | -74402 -> -80811 (-8.6%) | -31211 -> -37377 | -101 (-177; -66) | -1412 .. +1107 | 1907 | -8.4%, 0.17, 0.66 |  |
| London skip k=1.25 true points, M7+P7 | GAP | 21125 -> 19185 (+9.2%) | 0.60 / 0.61 / 0.59 / 0.33 | n/a | 0.90 / 0.97 / 1.00 | -55206 -> -48734 (+11.7%) | -43527 -> -41740 | +122 (+213; +158) | -2594 .. +2650 | 3969 | +9.2%, 0.60, 0.91 |  |
| London skip k=1.25 with UC, M7+P7 | L6M | 8356 -> 7567 (+9.4%) | 0.82 / 0.56 / 0.67 / 0.82 | n/a | 0.79 / 0.83 / 0.91 | -22565 -> -22508 (+0.2%) | -13430 -> -12590 | +408 (+714; +459) | -1356 .. +2168 | 2668 | +6.9%, 0.61, 0.57 |  |
| London skip k=1.25 with UC, M7+P7 | L3M | 9798 -> 8141 (+16.9%) | 0.90 / 0.56 / 0.58 / 0.91 | n/a | 0.83 / 0.92 / 0.96 | -22565 -> -22508 (+0.2%) | -13430 -> -12590 | +895 (+1566; +949) | -1885 .. +3538 | 4104 | +14.9%, 0.76, 0.57 |  |
| London skip k=1.25 with UC, M7+P7 | HOLD | 24530 -> 24548 (-0.1%) | 0.49 / 0.33 / 0.24 / 0.58 | n/a | 0.71 / 0.64 / 0.34 | -74402 -> -73823 (+0.8%) | -31211 -> -34751 | -63 (-110; -21) | -1402 .. +1362 | 2092 | -0.1%, 0.49, 0.72 |  |
| London skip k=1.25 with UC, M7+P7 | GAP | 21125 -> 17779 (+15.8%) | 0.81 / 0.89 / 0.70 / 0.34 | n/a | 0.94 / 0.98 / 1.00 | -55206 -> -43490 (+21.2%) | -43527 -> -40390 | +466 (+816; +508) | -2501 .. +3147 | 4275 | +15.8%, 0.81, 0.94 |  |
| M7 London cap 3 (block entry after 3 closes) | L6M | 8356 -> 8055 (+3.6%) | 0.69 / 0.25 / 0.17 / 1.00 | n/a | 0.20 / 0.18 / 0.10 | -22565 -> -23715 (-5.1%) | -13430 -> -15143 | +1747 (+3058; +1768) | +771 .. +2655 | 1426 | +5.2%, 0.81, 0.31 |  |
| M7 London cap 3 (block entry after 3 closes) | L3M | 9798 -> 9454 (+3.5%) | 0.55 / 0.25 / 0.17 / 0.99 | n/a | 0.12 / 0.11 / 0.07 | -22565 -> -23715 (-5.1%) | -13430 -> -15143 | +1271 (+2224; +1284) | -61 .. +2512 | 1947 | +6.1%, 0.68, 0.06 |  |
| M7 London cap 3 (block entry after 3 closes) | HOLD | 24530 -> 22302 (+9.1%) | 0.98 / 0.76 / 0.72 / 0.74 | n/a | 0.97 / 0.96 / 1.00 | -74402 -> -70924 (+4.7%) | -31211 -> -30596 | +264 (+461; +278) | -654 .. +1108 | 1333 | +9.1%, 0.98, 0.98 |  |
| M7 London cap 3 (block entry after 3 closes) | GAP | 21125 -> 20825 (+1.4%) | 0.51 / 0.56 / 0.51 / 0.23 | n/a | 0.65 / 0.65 / 0.54 | -55206 -> -53876 (+2.4%) | -43527 -> -43527 | -120 (-209; -115) | -691 .. +360 | 795 | +1.4%, 0.51, 0.65 |  |
| give-back H7 NY AM 40% / 40pt | L6M | 8356 -> 8076 (+3.3%) | 1.00 / 0.68 / 0.93 / 0.86 | n/a | 0.88 / 0.87 / 0.86 | -22565 -> -22565 (+0.0%) | -13430 -> -11690 | +82 (+143; +82) | -171 .. +354 | 397 | +4.0%, 1.00, 0.84 |  |
| give-back H7 NY AM 40% / 40pt | L3M | 9798 -> 9368 (+4.4%) | 1.00 / 0.68 / 0.93 / 0.88 | n/a | 0.66 / 0.80 / 0.83 | -22565 -> -22565 (+0.0%) | -13430 -> -11690 | +130 (+228; +130) | -263 .. +561 | 623 | +5.8%, 1.00, 0.63 |  |
| give-back H7 NY AM 40% / 40pt | HOLD | 24530 -> 24257 (+1.1%) | 0.87 / 0.98 / 0.68 / 0.82 | n/a | 0.66 / 0.57 / 0.50 | -74402 -> -72537 (+2.5%) | -31211 -> -31211 | +72 (+125; +71) | -191 .. +329 | 394 | +1.1%, 0.87, 0.68 |  |
| give-back H7 NY AM 40% / 40pt | GAP | 21125 -> 21022 (+0.5%) | 0.68 / 0.68 / 0.77 / 0.30 | n/a | 0.57 / 0.69 / 0.81 | -55206 -> -55031 (+0.3%) | -43527 -> -42687 | -157 (-275; -156) | -331 .. +48 | 286 | +0.5%, 0.68, 0.56 |  |
| give-back H7 NY AM 50% / 40pt | L6M | 8356 -> 8112 (+2.9%) | 1.00 / 0.67 / 0.94 / 0.84 | n/a | 0.88 / 0.86 / 0.86 | -22565 -> -22565 (+0.0%) | -13430 -> -11775 | +97 (+169; +97) | -134 .. +355 | 370 | +3.5%, 1.00, 0.84 |  |
| give-back H7 NY AM 50% / 40pt | L3M | 9798 -> 9424 (+3.8%) | 0.99 / 0.67 / 0.94 / 0.82 | n/a | 0.65 / 0.80 / 0.83 | -22565 -> -22565 (+0.0%) | -13430 -> -11775 | +111 (+194; +111) | -278 .. +536 | 616 | +5.0%, 0.99, 0.63 |  |
| give-back H7 NY AM 50% / 40pt | HOLD | 24530 -> 24246 (+1.2%) | 0.88 / 0.98 / 0.65 / 0.78 | n/a | 0.65 / 0.57 / 0.50 | -74402 -> -72627 (+2.4%) | -31211 -> -31211 | +48 (+84; +48) | -203 .. +296 | 378 | +1.2%, 0.88, 0.66 |  |
| give-back H7 NY AM 50% / 40pt | GAP | 21125 -> 21041 (+0.4%) | 0.68 / 0.68 / 0.80 / 0.22 | n/a | 0.51 / 0.65 / 0.81 | -55206 -> -55076 (+0.2%) | -43527 -> -42697 | -238 (-417; -237) | -410 .. -22 | 294 | +0.4%, 0.68, 0.49 |  |

| candidate | affected share real / ctrl mean (n draws, redraws) | new trades (path effect) |
|---|---|---|
| give-back H7 Asia 40% / 40pt | 0.348 / 0.349 (200, 31) delta-type | 20 |
| give-back H7 Asia 60% / 30pt | 0.416 / 0.416 (200, 31) delta-type | 41 |
| give-back K7 NY AM 40% / 40pt | 0.328 / 0.329 (200, 5) delta-type | 123 |
| give-back K7 NY AM 50% / 20pt | 0.566 / 0.565 (200, 5) delta-type | 193 |
| give-back P7 Asia 40% / 40pt | 0.381 / 0.382 (200, 1) delta-type | 486 |
| give-back P7 Asia 50% / 40pt | 0.340 / 0.341 (200, 0) delta-type | 436 |
| give-back P7 NY AM 40% / 30pt | 0.493 / 0.491 (200, 134) delta-type | 8 |
| A7 Asia fixed target 45 / stop 60 | 0.658 / 0.659 (200, 0) delta-type | 251 |
| against-the-day (VWAP) skip, all books | 0.125 / 0.125 (200, 0) skip-type | 1584 |
| against-the-day target 20 (3-of-4 vote), M7 NY AM | 0.000 / 0.000 (200, 0) delta-type | 0 |
| against-the-day target 20 (3-of-4 vote), O7 NY AM | 0.000 / 0.000 (200, 0) delta-type | 0 |
| U7 Asia fixed 40x40 | 0.995 / 0.995 (200, 0) delta-type | 694 |
| A7 Asia fixed 40x40 (morning bracket cell) | 0.974 / 0.974 (200, 0) delta-type | 961 |
| K7 NY AM fixed 40x40 (morning bracket cell) | 0.946 / 0.947 (200, 0) delta-type | 332 |
| K7 NY AM fixed 40x60 (morning bracket cell) | 0.522 / 0.523 (200, 1) delta-type | 280 |
| K7 London fixed 40x60 (morning bracket cell) | 0.556 / 0.557 (200, 1) delta-type | 402 |
| London skip k=1.25 true points, M7+P7 | 0.373 / 0.374 (200, 0) skip-type | 346 |
| London skip k=1.25 with UC, M7+P7 | 0.440 / 0.440 (200, 0) skip-type | 279 |
| M7 London cap 3 (block entry after 3 closes) | 0.192 / 0.192 (200, 0) skip-type | 141 |
| give-back H7 NY AM 40% / 40pt | 0.352 / 0.353 (200, 8) delta-type | 3 |
| give-back H7 NY AM 50% / 40pt | 0.312 / 0.314 (200, 6) delta-type | 1 |

Notes. (a) Verdict uses W44-included windows; where the W44-removed result differs, the result rests on one week. (b) Affected share counts every trade whose P&L differs from JL2 in that book x session, including lot/stack path changes. (c) Small cells (H7 NY AM, P7 NY AM) need many redraws to hit the 0.05 share tolerance. (d) against-the-day T20 rows change no engine trades. (e) U7/A7/K7 fixed brackets touch most trades: control = permutation of the rule deltas across the same trades; the stop change is not reproduced by the control. (f) DV bootstrap column is W-DV's stationary block bootstrap of 52 weekly P&L (H12 window), when the cell is in DV_DD_TABLE.csv.

<!-- WDV:BEGIN -->
## W-DV section: validation columns (owner W-DV; FIRST PASS; written 2026-11-16 20:18Z; do not edit between the markers)

VERDICT (data ends 2026-10-31; FIRST PASS; engine cells H12 = 2025-11..2026-10, IN-SAMPLE): JL2 drawdown is a distribution, not 74,402: bootstrap median 61,074 and 95th percentile 97,706 (live x1.75 at $4.84: 109,265 and 176,986; observed 133,301); the 95th percentile is 1.3x the single observed number. No candidate moves the 95th-percentile DD by more than 9%: U7 asia 40x40 -8.8%, M7 London cap 3 -7.6% (both with a mean gain of +7% / +7%), the 9 give-back lines -5% to +2%, A7 target 45 -0.4%, against-the-day M7/O7 nyam 0 (the engine never changes a trade), session-VWAP skip +7% (worse). None of the four families (give-back, fixed bracket, against-the-day, M7 London cap / re-entry) is significant after snooping at its real trial count (RC p .26-.88, DSR .03-.17 at N_used; BH 10% survivors none).

HEADER LINE (template for every page): `Validation: trials counted N_low..N_used (TRIALS_LEDGER.csv family id); correction = White RC + Hansen SPA (2,000 stationary-bootstrap resamples) + deflated Sharpe at the real trial count + BH 10% on survivor lists; PBO = x.xx (CSCV S blocks, purge 1 wk) or "not fitted"; number shown is IN-SAMPLE | WALK-FORWARD | UNTOUCHED (stamp data end).`

### 1. Drawdown as a distribution (first table; JL2 first, then each candidate)
Method: stationary block bootstrap (B = 5,000, seed 0) of the DAILY P&L path with whole weeks as blocks; mean block length b (weeks, column b) = Politis-White / Patton optimal length from the autocorrelation of the cell's own weekly P&L (about 1.0-1.3 weeks on H12, 1.7-2.7 on HOLD: weekly P&L has almost no autocorrelation, so the blocks are short and the table is close to an iid week resample); paths have the window length; drawdown from a zero start; "obs DD (page basis)" = observed daily-cumulative max DD with the peak starting at the first value, the convention of the DS3 pages (ties out: JL2 HOLD 74,402, L6M 22,565). Thresholds 1x/2x/3x = multiples of the cell's own average weekly profit (second set: JL2's average, one common scale). Median DD in average weeks of profit is shown because 1x-3x are small multiples of a weekly profit and are exceeded in almost every draw on 6-12 month windows; the number to size lots from is the 95th percentile. Dollars: BASE lots, engine fee $1.18; last column = live x1.75 lots at $4.84 RT. H12 = 2025-11..2026-10 (HOLD+L6M months, 52 weeks); a window is shown only when the cell has every month of it (so no ALL rows for 12-month cells). Small windows: HOLD has 26 weeks and L6M 27, so their percentiles are rough; H12 is the main row. Cells = full-stack runs (candidate rule alone altered inside the JL2 stack).

| window | cell | wks | b | obs DD (page basis) | median DD (in avg weeks of profit) | 95th pct DD | P(DD>1x) | P(>2x) | P(>3x) | same, thresholds at JL2 avg (1x/2x/3x) | avg $/wk | worst wk | live x1.75 @4.84: obs / median / 95th DD, avg $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| H12 | JL2 | 52 | 1.1 | -74,402 | -61,074 (4.0) | -97,706 | 1.00 | 1.00 | 0.86 | same | 15,316 | -31,211 | -133,301 / -109,265 / -176,986, 25,522 |
| H12 | A7 asia target 45 | 52 | 1.0 | -74,364 | -59,856 (4.0) | -97,322 | 1.00 | 1.00 | 0.88 | 1.00/1.00/0.87 | 15,069 | -31,106 | -133,248 / -107,531 / -176,159, 25,083 |
| H12 | ATD M7 nyam T20 | 52 | 1.1 | -74,402 | -61,074 (4.0) | -97,706 | 1.00 | 1.00 | 0.86 | 1.00/1.00/0.86 | 15,316 | -31,211 | -133,301 / -109,265 / -176,986, 25,522 |
| H12 | ATD O7 nyam T20 | 52 | 1.1 | -74,402 | -61,074 (4.0) | -97,706 | 1.00 | 1.00 | 0.86 | 1.00/1.00/0.86 | 15,316 | -31,211 | -133,301 / -109,265 / -176,986, 25,522 |
| H12 | ATD O7 nyam T25 | 52 | 1.1 | -74,402 | -61,074 (4.0) | -97,706 | 1.00 | 1.00 | 0.86 | 1.00/1.00/0.86 | 15,316 | -31,211 | -133,301 / -109,265 / -176,986, 25,522 |
| H12 | ATD session-VWAP skip (all books) | 52 | 1.3 | -72,108 | -64,731 (4.3) | -104,596 | 1.00 | 1.00 | 0.92 | 1.00/1.00/0.92 | 15,169 | -31,437 | -129,204 / -116,888 / -190,049, 25,305 |
| H12 | GB H7 asia 40/B40 | 52 | 1.0 | -71,746 | -59,228 (3.9) | -95,725 | 1.00 | 1.00 | 0.87 | 1.00/1.00/0.86 | 15,078 | -31,074 | -128,660 / -107,049 / -173,775, 25,107 |
| H12 | GB H7 asia 60/B30 | 52 | 1.0 | -72,429 | -59,140 (3.9) | -96,289 | 1.00 | 1.00 | 0.86 | 1.00/1.00/0.85 | 15,187 | -33,394 | -129,869 / -106,227 / -174,328, 25,299 |
| H12 | GB H7 nyam 40/B40 | 52 | 1.2 | -72,537 | -60,523 (3.9) | -96,415 | 1.00 | 1.00 | 0.86 | 1.00/1.00/0.87 | 15,392 | -31,211 | -130,037 / -108,723 / -174,463, 25,657 |
| H12 | GB H7 nyam 50/B40 | 52 | 1.2 | -72,627 | -60,685 (3.9) | -96,554 | 1.00 | 1.00 | 0.87 | 1.00/1.00/0.87 | 15,388 | -31,211 | -130,195 / -108,841 / -174,474, 25,650 |
| H12 | GB K7 nyam 40/B40 | 52 | 1.0 | -75,309 | -59,882 (3.9) | -95,754 | 1.00 | 1.00 | 0.84 | 1.00/1.00/0.85 | 15,510 | -30,699 | -134,929 / -106,696 / -174,008, 25,853 |
| H12 | GB K7 nyam 50/B20 | 52 | 1.2 | -78,354 | -62,101 (4.1) | -99,494 | 1.00 | 1.00 | 0.90 | 1.00/1.00/0.89 | 14,964 | -31,604 | -140,335 / -112,173 / -178,720, 24,888 |
| H12 | GB P7 asia 40/B40 | 52 | 1.0 | -74,710 | -60,164 (4.3) | -103,010 | 1.00 | 1.00 | 0.91 | 1.00/1.00/0.85 | 13,962 | -35,108 | -133,970 / -108,849 / -186,887, 23,101 |
| H12 | GB P7 asia 50/B40 | 52 | 1.0 | -75,505 | -59,294 (4.1) | -101,238 | 1.00 | 1.00 | 0.90 | 1.00/1.00/0.84 | 14,355 | -34,923 | -135,350 / -107,449 / -183,733, 23,802 |
| H12 | GB P7 nyam 40/B30 | 52 | 1.2 | -73,222 | -61,010 (4.0) | -96,717 | 1.00 | 1.00 | 0.88 | 1.00/1.00/0.87 | 15,094 | -31,662 | -131,237 / -109,265 / -176,279, 25,135 |
| H12 | M7 London cap 3 | 52 | 1.3 | -70,924 | -59,277 (3.6) | -90,315 | 1.00 | 0.99 | 0.74 | 1.00/1.00/0.81 | 16,330 | -30,596 | -127,174 / -105,246 / -163,646, 27,328 |
| H12 | U7 asia 40x40 | 52 | 1.0 | -67,152 | -54,731 (3.3) | -89,125 | 1.00 | 0.98 | 0.66 | 1.00/0.99/0.74 | 16,472 | -33,286 | -120,737 / -99,106 / -161,839, 27,481 |
| HOLD | JL2 | 26 | 2.3 | -74,402 | -72,692 (8.7) | -114,451 | 1.00 | 1.00 | 1.00 | same | 8,313 | -31,211 | -133,301 / -131,665 / -208,631, 13,428 |
| HOLD | A7 asia target 45 | 26 | 2.4 | -74,364 | -72,900 (8.7) | -112,782 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,399 | -31,106 | -133,248 / -132,393 / -205,659, 13,577 |
| HOLD | ATD M7 nyam T20 | 26 | 2.3 | -74,402 | -72,692 (8.7) | -114,451 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,313 | -31,211 | -133,301 / -131,665 / -208,631, 13,428 |
| HOLD | ATD O7 nyam T20 | 26 | 2.3 | -74,402 | -72,692 (8.7) | -114,451 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,313 | -31,211 | -133,301 / -131,665 / -208,631, 13,428 |
| HOLD | ATD O7 nyam T25 | 26 | 2.3 | -74,402 | -72,692 (8.7) | -114,451 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,313 | -31,211 | -133,301 / -131,665 / -208,631, 13,428 |
| HOLD | ATD session-VWAP skip (all books) | 26 | 2.1 | -72,108 | -72,108 (8.5) | -117,665 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,518 | -31,437 | -129,204 / -129,204 / -214,995, 13,826 |
| HOLD | GB H7 asia 40/B40 | 26 | 2.7 | -71,746 | -71,746 (8.3) | -108,361 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,688 | -31,074 | -128,660 / -128,660 / -198,162, 14,084 |
| HOLD | GB H7 asia 60/B30 | 26 | 2.0 | -72,429 | -70,680 (7.6) | -115,209 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 9,340 | -33,394 | -129,869 / -128,414 / -208,797, 15,220 |
| HOLD | GB H7 nyam 40/B40 | 26 | 2.2 | -72,537 | -71,487 (8.5) | -114,206 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,384 | -31,211 | -130,037 / -130,037 / -207,790, 13,552 |
| HOLD | GB H7 nyam 50/B40 | 26 | 2.3 | -72,627 | -72,126 (8.6) | -113,960 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,361 | -31,211 | -130,195 / -130,195 / -207,464, 13,512 |
| HOLD | GB K7 nyam 40/B40 | 26 | 2.6 | -75,309 | -72,311 (8.6) | -111,304 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,437 | -30,699 | -134,929 / -130,851 / -201,217, 13,633 |
| HOLD | GB K7 nyam 50/B20 | 26 | 2.1 | -78,354 | -73,322 (9.2) | -118,287 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 7,959 | -31,604 | -140,335 / -131,970 / -216,228, 12,785 |
| HOLD | GB P7 asia 40/B40 | 26 | 1.4 | -74,710 | -69,087 (8.0) | -124,180 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,628 | -35,108 | -133,970 / -124,485 / -228,598, 13,933 |
| HOLD | GB P7 asia 50/B40 | 26 | 2.2 | -75,505 | -70,689 (8.4) | -120,095 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,392 | -34,923 | -135,350 / -128,701 / -218,564, 13,530 |
| HOLD | GB P7 nyam 40/B30 | 26 | 2.3 | -73,222 | -72,082 (8.8) | -113,105 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,182 | -31,662 | -131,237 / -131,211 / -205,486, 13,198 |
| HOLD | M7 London cap 3 | 26 | 2.1 | -70,924 | -66,354 (7.7) | -103,621 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,575 | -30,596 | -127,174 / -120,758 / -190,859, 13,912 |
| HOLD | U7 asia 40x40 | 26 | 2.3 | -67,152 | -67,152 (7.1) | -107,004 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 9,462 | -33,286 | -120,737 / -120,737 / -196,587, 15,383 |
| L6M | JL2 | 27 | 1.2 | -22,565 | -31,058 (1.4) | -46,726 | 0.92 | 0.09 | 0.00 | same | 21,492 | -13,430 | -40,872 / -55,574 / -85,039, 36,223 |
| L6M | A7 asia target 45 | 27 | 1.2 | -21,503 | -32,032 (1.5) | -47,069 | 0.95 | 0.12 | 0.00 | 0.93/0.10/0.00 | 20,935 | -13,002 | -41,290 / -57,537 / -84,902, 35,235 |
| L6M | ATD M7 nyam T20 | 27 | 1.2 | -22,565 | -31,058 (1.4) | -46,726 | 0.92 | 0.09 | 0.00 | 0.92/0.09/0.00 | 21,492 | -13,430 | -40,872 / -55,574 / -85,039, 36,223 |
| L6M | ATD O7 nyam T20 | 27 | 1.2 | -22,565 | -31,058 (1.4) | -46,726 | 0.92 | 0.09 | 0.00 | 0.92/0.09/0.00 | 21,492 | -13,430 | -40,872 / -55,574 / -85,039, 36,223 |
| L6M | ATD O7 nyam T25 | 27 | 1.2 | -22,565 | -31,058 (1.4) | -46,726 | 0.92 | 0.09 | 0.00 | 0.92/0.09/0.00 | 21,492 | -13,430 | -40,872 / -55,574 / -85,039, 36,223 |
| L6M | ATD session-VWAP skip (all books) | 27 | 1.4 | -28,494 | -36,617 (1.7) | -60,699 | 0.99 | 0.33 | 0.04 | 0.99/0.31/0.03 | 21,011 | -23,429 | -51,900 / -66,311 / -110,292, 35,423 |
| L6M | GB H7 asia 40/B40 | 27 | 1.1 | -23,908 | -30,957 (1.5) | -46,927 | 0.93 | 0.12 | 0.00 | 0.92/0.09/0.00 | 20,673 | -13,430 | -43,898 / -55,910 / -85,516, 34,791 |
| L6M | GB H7 asia 60/B30 | 27 | 1.1 | -25,023 | -30,957 (1.5) | -46,377 | 0.95 | 0.13 | 0.00 | 0.93/0.09/0.00 | 20,254 | -13,430 | -47,418 / -56,282 / -84,604, 34,068 |
| L6M | GB H7 nyam 40/B40 | 27 | 1.2 | -22,565 | -30,464 (1.4) | -45,448 | 0.91 | 0.07 | 0.00 | 0.91/0.08/0.00 | 21,571 | -11,690 | -40,872 / -54,539 / -82,470, 36,362 |
| L6M | GB H7 nyam 50/B40 | 27 | 1.2 | -22,565 | -30,522 (1.4) | -45,571 | 0.91 | 0.08 | 0.00 | 0.91/0.08/0.00 | 21,586 | -11,775 | -40,872 / -54,539 / -83,167, 36,388 |
| L6M | GB K7 nyam 40/B40 | 27 | 1.1 | -23,010 | -31,058 (1.4) | -45,770 | 0.91 | 0.07 | 0.00 | 0.91/0.08/0.00 | 21,748 | -13,430 | -41,650 / -55,898 / -83,502, 36,662 |
| L6M | GB K7 nyam 50/B20 | 27 | 1.2 | -24,340 | -31,490 (1.5) | -48,527 | 0.93 | 0.11 | 0.00 | 0.92/0.11/0.00 | 21,156 | -14,211 | -43,978 / -57,284 / -86,935, 35,621 |
| L6M | GB P7 asia 40/B40 | 27 | 1.0 | -31,640 | -32,155 (1.7) | -50,147 | 0.98 | 0.34 | 0.02 | 0.97/0.13/0.01 | 18,581 | -18,172 | -56,172 / -57,575 / -90,604, 31,074 |
| L6M | GB P7 asia 50/B40 | 27 | 1.0 | -30,727 | -31,495 (1.6) | -48,477 | 0.98 | 0.20 | 0.01 | 0.96/0.11/0.00 | 19,566 | -17,244 | -54,523 / -56,557 / -87,419, 32,811 |
| L6M | GB P7 nyam 40/B30 | 27 | 1.2 | -22,565 | -31,058 (1.5) | -46,727 | 0.92 | 0.10 | 0.00 | 0.92/0.09/0.00 | 21,192 | -13,430 | -40,872 / -55,611 / -85,391, 35,699 |
| L6M | M7 London cap 3 | 27 | 1.1 | -23,715 | -30,372 (1.3) | -45,430 | 0.87 | 0.04 | 0.00 | 0.91/0.08/0.00 | 23,193 | -15,143 | -42,637 / -54,518 / -82,649, 39,235 |
| L6M | U7 asia 40x40 | 27 | 1.0 | -19,715 | -28,199 (1.2) | -38,927 | 0.83 | 0.01 | 0.00 | 0.86/0.02/0.00 | 22,612 | -10,253 | -35,143 / -51,003 / -70,347, 38,113 |
| ALL | JL2 | 187 | 1.3 | -74,402 | -87,918 (10.0) | -137,833 | 1.00 | 1.00 | 1.00 | same | 8,803 | -43,527 | -133,301 / -159,439 / -251,045, 14,510 |

### 2. Whole-family data-snooping and PBO (H12 window unless stated; weekly P&L differences vs the family benchmark)
Counting method and uncertainty: autopilot/TRIALS_LEDGER.csv (engine run dirs + replay rules x 15 scopes; +-30%; not a registered log). N engine = variants that reached the exact engine; N total = replay screens (the family the winner was picked from). DSR is computed on the winner's weekly difference series (per-week Sharpe, not annualised) with the variance of the family's trial Sharpes. RC / SPA are one-sided tests that the BEST variant beats the benchmark in MEAN weekly P&L; "downside-weeks" repeats them on the change in the base's worst-quartile weeks only (a mean-type statistic that speaks to drawdown, because no valid snooping test on max DD itself exists in this library: a shift-null DD reality check was built and failed its own unit test, size .10, power .11, and was removed). BH 10% runs on per-variant one-sided bootstrap p-values of the mean. PBO: CSCV, S blocks, all C(S,S/2) splits (3,000 random splits when more), 1-week purge on the train side, metric = Sharpe of the weekly difference; on 52 weeks the blocks are 3-4 weeks long, so PBO is a weak, noisy read there. A fitted choice with PBO above 0.5 is not a result.

| family (base, window) | K variants (N engine / N total) | best by mean | White RC p | Hansen SPA p | DSR at N engine / N total | downside-weeks RC p / SPA p | BH 10% survivors | PBO S=12/14/16 (slope S=16; weeks per block) | verdict on snooping |
|--|--|--|--|--|--|--|--|--|--|
| giveback (D10 gb, JL2) (JL2, H12) | 9 (9 / 135) | bK7_sam_JL2_gb40B40 +195/wk (SR 0.11/wk) | 0.85 | 0.78 | 0.28 / 0.06 | 0.56 / 0.34 | none | 0.56 / 0.59 / 0.57 (slope -0.37; 3.2 wk) | NOT significant after snooping |
| fixed bracket/target (D10 pol_fx, JL2) (JL2, H12) | 5 (5 / 225) | bU7_sas_JL2_pol_fx40x40 +1,156/wk (SR 0.16/wk) | 0.26 | 0.46 | 0.44 / 0.03 | 0.29 / 0.53 | none | 0.51 / 0.37 / 0.46 (slope 0.01; 3.2 wk) | NOT significant after snooping |
| against-the-day (D10 dd*, JL2) HOLD (JL2, HOLD) | 28 (28 / 60) | JL2_ddsess_w_aT30 +1,360/wk (SR 0.16/wk) | 0.67 | 0.76 | 0.23 / 0.17 | 0.11 / 0.14 | none | 0.52 / n/a / n/a (slope n/a; 1.6 wk) | NOT significant after snooping |
| M7 London cap / re-entry (RA, JN05W2 base) (JN05W2, H12) | 14 (14 / 258) | TL3_RA_LCAP20 +319/wk (SR 0.10/wk) | 0.88 | 0.78 | 0.21 / 0.04 | 0.04 / 0.13 | none | 0.45 / 0.29 / 0.35 (slope -0.43; 3.2 wk) | NOT significant after snooping |

Unit-test evidence (null pass rate near nominal, planted power; code/th_validate/TEST_RESULTS.txt): RC/SPA size .06/.08 iid at T=187, K=20 (anti-conservative with autocorrelation: SPA .16 at phi .3, flagged), power .68/.70 at t about 3.4, SPA .86 vs RC .46 with 19 poor alternatives; DSR null pass .002-.05 vs naive .64-.99 at N=20-100; BH realised FDR .08; PBO .56 on noise vs .07 planted; DD bootstrap within 1% (median) / 0.3% (95th) of truth for iid weeks and 6.7% bias vs 37.6% for iid resample when weeks are AR(.5).
<!-- WDV:END -->
