# DS3_BRACKET_DD_BUILD - non-fixed target rules per book x session, engine on TL3_EV_JN05W2JL2 (written 03:10Z)
<!-- PR2:BEGIN -->
## RE-SCORE UNDER THE CALIBRATED RULE (W-PR2, FIRST PASS, ulcer index primary; data ends 2026-10-30; written 03:51 UTC)

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

**Plain: this table carries only what the engine has finished. A row is CONFIRMED only when the real cell beats all 6 controls on max DD in HOLD AND L6M with mean not more than 5% below the reference; otherwise ENGINE ONLY (controls missing or not beaten) or REPLAY ONLY (replay rows of W-RP / W-RP2 / W-LB2 / W-BD2 are on DS3_TARGET_REPLAY*.md and DS3_BRACKET_DD_D.md). "Keep 58" is not a deliverable: every row names the best non-fixed rule found so far.**

Basis: JL2 base, whole-stack drawdown vs the reference (+ = smaller drawdown), $ per week base lots (x1.75 live; $4.84 repriced), HOLD = 2025-11..2026-04, L6M = 2026-05..10, only that book in that session altered; stop and lots at live values (all rules here leave the 60-point stop unchanged, so constant-risk lots are the same). Controls: placebo = the rule on a persistent-draw random subset (one draw per 5-minute bucket per book and side) of ALL signals at the cell share (day-direction rule: the label shifted 11/23/37 sessions); matched = the rule on a persistent 50% random subset of the cell's own signals (day-direction rule: random labels with the real against-day share). Realised control keep shares are in each control cell trade counts.

| book x session | rule (replay rank) | HOLD engine: max DD (ref), worst wk, d net/wk (x1.75; $4.84) | L6M engine | controls HOLD / L6M (DD cut %, 6 of 6) | label | exact implementation |
|---|---|---|---|---|---|---|
| A7 asia | fixed target 45, stop 60 (a_T45) | -74364 (-74402; +0.1%), ww -31106, +87 (+152; +86) | -21503 (-22565; +4.7%), ww -13002, -572 (-1001; -580) | HOLD [+1.7, -0.5, -4.6, +0.5, +4.2, +0.7] real +0.1%; L6M [+1.3, -3.3, -35.2, -1.1, +9.1, -6.2] real +4.7% | ENGINE ONLY | `bracket A7 asia stop=60 target=45` (grammar supports it; place it ABOVE any `bracket A7 * ...` line, first matching bracket line wins; lots unchanged because the stop is unchanged) |
| H7 asia | give-back exit 60% of best once best >= 30 pts (k_F60_B30) | -72429 (-74402; +2.7%), ww -33394, +1033 (+1808; +1030) | -25023 (-22565; -10.9%), ww -13430, -1271 (-2224; -1265) | HOLD [+2.7, +0.0, -8.1, +5.6, -0.1, -5.1] real +2.7%; L6M [-7.8, -9.1, -36.9, +0.2, -3.3, -5.4] real -10.9% | ENGINE ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 30 points and open profit <= (1 - 0.60) x best (give-back 60%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| H7 asia | give-back exit 40% of best once best >= 40 pts (k_F40_B40) | -71746 (-74402; +3.6%), ww -31074, +378 (+661; +377) | -23908 (-22565; -6.0%), ww -13430, -841 (-1472; -840) | HOLD [-1.5, +0.0, -3.9, +3.4, -3.3, -1.4] real +3.6%; L6M [+0.0, -5.3, -0.8, +0.0, +0.0, -3.0] real -6.0% | ENGINE ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 40 points and open profit <= (1 - 0.40) x best (give-back 40%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| H7 nyam | give-back exit 40% of best once best >= 40 pts (k_F40_B40) | -72537 (-74402; +2.5%), ww -31211, +72 (+125; +71) | -22565 (-22565; +0.0%), ww -11690, +82 (+143; +82) | HOLD [-0.7, +0.0, -1.4, +0.0, +2.5, +2.5] real +2.5%; L6M [+0.0, -4.2, -0.8, +0.0, +0.0, +0.0] real +0.0% | ENGINE ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 40 points and open profit <= (1 - 0.40) x best (give-back 40%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| H7 nyam | give-back exit 50% of best once best >= 40 pts (k_F50_B40) | -72627 (-74402; +2.4%), ww -31211, +48 (+84; +48) | -22565 (-22565; +0.0%), ww -11775, +97 (+169; +97) | HOLD [-0.9, +0.0, -1.6, +0.0, +2.4, +2.4] real +2.4%; L6M [+0.0, -5.8, -1.2, +0.0, +0.0, +0.0] real +0.0% | ENGINE ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 40 points and open profit <= (1 - 0.50) x best (give-back 50%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| K7 nyam | give-back exit 40% of best once best >= 40 pts (k_F40_B40) | -75309 (-74402; -1.2%), ww -30699, +125 (+218; +118) | -23010 (-22565; -2.0%), ww -13430, +263 (+460; +257) | HOLD [-0.3, +0.7, -4.7, -3.9, -0.9, +1.3] real -1.2%; L6M [+0.6, -22.7, -0.8, +0.0, -2.0, -2.0] real -2.0% | ENGINE ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 40 points and open profit <= (1 - 0.40) x best (give-back 40%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| K7 nyam | give-back exit 50% of best once best >= 20 pts (k_F50_B20) | -78354 (-74402; -5.3%), ww -31604, -356 (-622; -370) | -24340 (-22565; -7.9%), ww -14211, -345 (-603; -354) | HOLD [+7.5, -6.2, -6.3, -9.9, -3.6, -2.0] real -5.3%; L6M [-5.8, -41.7, -36.5, +0.0, -3.9, -7.9] real -7.9% | ENGINE ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 20 points and open profit <= (1 - 0.50) x best (give-back 50%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| M7 nyam | 3-of-4 day-direction vote; AGAINST the day target 20, WITH the day unchanged (d_against_T20) | -74402 (-74402; +0.0%), ww -31211, +0 (+0; +0) | -22565 (-22565; +0.0%), ww -13430, +0 (+0; +0) | HOLD [+0.4, +4.4, -2.8, -0.4, +1.5, -1.1] real +0.0%; L6M [-3.5, -8.7, -1.4, -3.5, +0.0, +0.0] real +0.0% | ENGINE ONLY | CODE CHANGE in DS7.cs (not in the policy grammar): at the signal second compute the 3-of-4 day direction; when the trade is AGAINST it set TradeTgtPts = 20 (stop and lots unchanged) |
| O7 nyam | 3-of-4 day-direction vote; AGAINST the day target 20, WITH the day unchanged (d_against_T20) | -74402 (-74402; +0.0%), ww -31211, +0 (+0; +0) | -22565 (-22565; +0.0%), ww -13430, +0 (+0; +0) | HOLD [+0.0, +0.0, -0.4, +0.0, +0.0, +0.0] real +0.0%; L6M [-2.1, -0.1, -0.1, +0.0, +0.0, +0.0] real +0.0% | ENGINE ONLY | CODE CHANGE in DS7.cs (not in the policy grammar): at the signal second compute the 3-of-4 day direction; when the trade is AGAINST it set TradeTgtPts = 20 (stop and lots unchanged) |
| O7 nyam | 3-of-4 day-direction vote; AGAINST the day target 25, WITH the day unchanged (d_against_T25) | -74402 (-74402; +0.0%), ww -31211, +0 (+0; +0) | -22565 (-22565; +0.0%), ww -13430, +0 (+0; +0) | HOLD [+0.0, +0.0, -0.1, +0.0, +0.0, +0.0] real +0.0%; L6M [-1.2, +0.0, +0.0, +0.0, +0.0, +0.0] real +0.0% | ENGINE ONLY | CODE CHANGE in DS7.cs (not in the policy grammar): at the signal second compute the 3-of-4 day direction; when the trade is AGAINST it set TradeTgtPts = 25 (stop and lots unchanged) |
| P7 asia | give-back exit 50% of best once best >= 40 pts (k_F50_B40) | -75505 (-74402; -1.5%), ww -34923, +80 (+139; +59) | -30727 (-22565; -36.2%), ww -17244, -1978 (-3462; -2002) | HOLD [-0.7, +1.3, +3.2, +13.0, +2.8, +3.1] real -1.5%; L6M [+1.8, -5.5, -1.9, -1.0, -9.1, -9.1] real -36.2% | ENGINE ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 40 points and open profit <= (1 - 0.50) x best (give-back 50%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| P7 asia | give-back exit 40% of best once best >= 40 pts (k_F40_B40) | -74710 (-74402; -0.4%), ww -35108, +317 (+555; +290) | -31640 (-22565; -40.2%), ww -18172, -2989 (-5232; -3022) | HOLD [-1.7, +1.7, -0.4, +12.1, +2.2, +2.5] real -0.4%; L6M [-1.6, -12.4, -8.7, +2.8, -8.7, -13.5] real -40.2% | ENGINE ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 40 points and open profit <= (1 - 0.40) x best (give-back 40%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| P7 nyam | give-back exit 40% of best once best >= 30 pts (k_F40_B30) | -73222 (-74402; +1.6%), ww -31662, -132 (-231; -133) | -22565 (-22565; +0.0%), ww -13430, -308 (-538; -308) | HOLD [+7.6, -3.8, -11.4, +2.0, +0.9, -1.0] real +1.6%; L6M [+0.6, -11.3, -62.9, +0.0, +0.0, +0.0] real +0.0% | ENGINE ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 30 points and open profit <= (1 - 0.40) x best (give-back 40%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |

Rows owned by W-BD2 (b half-off, c step-down, e HAR remaining range, f atr/squeeze state, g trail) are in autopilot/DS3_BRACKET_DD_BUILD_D.md and DS3_BRACKET_DD_D.md. Families h (structure targets), i (book/tape) and j (other markets) are REPLAY ONLY in this file: h needs tape-derived levels per second, i and j need per-second feature files; they were not built as engine sets.

## Worked examples (3 altered trades per engine cell, L6M, Eastern time)
**A7 asia, a_T45**
- entry 2026-05-04 21:22:02 ET at 27808.75, exit 00:03:19 ET at 27853.75 (Target), lots 1, net $899.
- entry 2026-05-05 18:15:01 ET at 28260.25, exit 18:52:09 ET at 28305.25 (Target), lots 1, net $899.
- entry 2026-05-07 21:17:01 ET at 28761.25, exit 01:30:13 ET at 28806.25 (Target), lots 1, net $899.

**H7 asia, k_F60_B30**
- entry 2026-04-30 19:50:01 ET at 27615.00, exit 22:33:57 ET at 27632.50 (D10GiveBack), lots 1, net $349.
- entry 2026-05-06 23:40:01 ET at 28692.00, exit 02:06:56 ET at 28708.25 (D10GiveBack), lots 1, net $324.
- entry 2026-05-19 20:15:01 ET at 28830.75, exit 20:17:28 ET at 28817.75 (D10GiveBack), lots 1, net $259.

**H7 asia, k_F40_B40**
- entry 2026-04-30 19:50:01 ET at 27615.00, exit 21:41:24 ET at 27641.50 (D10GiveBack), lots 1, net $529.
- entry 2026-05-06 23:40:01 ET at 28692.00, exit 02:46:10 ET at 28726.50 (D10GiveBack), lots 1, net $689.
- entry 2026-05-19 22:45:01 ET at 28886.12, exit 23:11:36 ET at 28861.25 (D10GiveBack), lots 2, net $993.

**H7 nyam, k_F40_B40**
- entry 2026-05-05 11:50:01 ET at 28142.00, exit 14:51:52 ET at 28168.50 (D10GiveBack), lots 1, net $529.
- entry 2026-05-19 10:20:01 ET at 28711.75, exit 10:22:30 ET at 28677.50 (D10GiveBack), lots 1, net $684.
- entry 2026-05-26 10:10:01 ET at 30003.75, exit 10:21:43 ET at 30039.25 (D10GiveBack), lots 1, net $709.

**H7 nyam, k_F50_B40**
- entry 2026-05-05 11:50:01 ET at 28142.00, exit 14:52:20 ET at 28163.75 (D10GiveBack), lots 1, net $434.
- entry 2026-05-19 10:20:01 ET at 28711.75, exit 10:23:07 ET at 28686.75 (D10GiveBack), lots 1, net $499.
- entry 2026-06-29 10:05:01 ET at 29542.00, exit 10:07:12 ET at 29510.25 (D10GiveBack), lots 1, net $634.

**K7 nyam, k_F40_B40**
- entry 2026-05-01 10:36:01 ET at 27803.50, exit 10:38:31 ET at 27771.50 (D10GiveBack), lots 1, net $639.
- entry 2026-05-01 11:21:01 ET at 27860.25, exit 11:50:31 ET at 27884.75 (D10GiveBack), lots 1, net $489.
- entry 2026-05-05 11:15:01 ET at 28132.75, exit 14:52:13 ET at 28165.50 (D10GiveBack), lots 1, net $654.

**K7 nyam, k_F50_B20**
- entry 2026-05-01 10:36:01 ET at 27803.50, exit 10:37:06 ET at 27785.00 (D10GiveBack), lots 1, net $369.
- entry 2026-05-01 11:21:01 ET at 27860.25, exit 11:50:31 ET at 27879.50 (D10GiveBack), lots 1, net $384.
- entry 2026-05-05 11:15:01 ET at 28132.75, exit 14:53:15 ET at 28159.75 (D10GiveBack), lots 1, net $539.

**M7 nyam, d_against_T20**
- entry 2026-05-01 10:20:01 ET at 27878.50, exit 10:33:08 ET at 27831.33 (StateCut), lots 1, net $-945. day direction at the signal second (sess/18:00/VWAP/60m/vote) = [1, 1, 1, 1, 1]; side +1
- entry 2026-05-01 11:21:01 ET at 27860.25, exit 12:33:12 ET at 27822.83 (StateCut), lots 1, net $-750. day direction at the signal second (sess/18:00/VWAP/60m/vote) = [1, 1, 1, -1, 1]; side +1
- entry 2026-05-05 10:02:01 ET at 28097.75, exit 10:15:07 ET at 28038.00 (StopJoin), lots 1, net $-1196. day direction at the signal second (sess/18:00/VWAP/60m/vote) = [1, 1, 1, 1, 1]; side +1

**O7 nyam, d_against_T20**
- entry 2026-05-01 09:42:01 ET at 27785.00, exit 09:59:59 ET at 27875.00 (Target), lots 1, net $1799. day direction at the signal second (sess/18:00/VWAP/60m/vote) = [1, 1, 1, 1, 1]; side +1
- entry 2026-05-05 09:43:01 ET at 28066.75, exit 12:27:49 ET at 28108.50 (BookLock), lots 1, net $834. day direction at the signal second (sess/18:00/VWAP/60m/vote) = [1, 1, 1, 1, 1]; side +1
- entry 2026-05-06 09:43:01 ET at 28439.25, exit 10:06:54 ET at 28401.75 (Stop), lots 1, net $-751. day direction at the signal second (sess/18:00/VWAP/60m/vote) = [1, 1, 1, -1, 1]; side +1

**O7 nyam, d_against_T25**
- entry 2026-05-01 09:42:01 ET at 27785.00, exit 09:59:59 ET at 27875.00 (Target), lots 1, net $1799. day direction at the signal second (sess/18:00/VWAP/60m/vote) = [1, 1, 1, 1, 1]; side +1
- entry 2026-05-05 09:43:01 ET at 28066.75, exit 12:27:49 ET at 28108.50 (BookLock), lots 1, net $834. day direction at the signal second (sess/18:00/VWAP/60m/vote) = [1, 1, 1, 1, 1]; side +1
- entry 2026-05-06 09:43:01 ET at 28439.25, exit 10:06:54 ET at 28401.75 (Stop), lots 1, net $-751. day direction at the signal second (sess/18:00/VWAP/60m/vote) = [1, 1, 1, -1, 1]; side +1

**P7 asia, k_F50_B40**
- entry 2026-04-30 19:13:02 ET at 27589.75, exit 21:01:52 ET at 27614.75 (D10GiveBack), lots 2, net $998.
- entry 2026-04-30 21:12:01 ET at 27633.88, exit 23:36:13 ET at 27652.94 (D10GiveBack), lots 4, net $1520.
- entry 2026-05-03 20:06:01 ET at 27844.81, exit 21:04:02 ET at 27871.56 (D10GiveBack), lots 4, net $2135.

**P7 asia, k_F40_B40**
- entry 2026-04-30 19:13:02 ET at 27589.75, exit 21:01:48 ET at 27617.00 (D10GiveBack), lots 2, net $1088.
- entry 2026-04-30 21:12:01 ET at 27633.88, exit 23:32:33 ET at 27656.94 (D10GiveBack), lots 4, net $1840.
- entry 2026-05-01 00:16:24 ET at 27630.81, exit 03:52:40 ET at 27602.50 (D10GiveBack), lots 4, net $2260.

**P7 nyam, k_F40_B30**
- entry 2026-05-06 10:50:16 ET at 28536.25, exit 11:37:04 ET at 28566.75 (D10GiveBack), lots 1, net $609.
- entry 2026-05-13 11:40:31 ET at 29339.75, exit 11:45:21 ET at 29368.00 (D10GiveBack), lots 1, net $564.
- entry 2026-05-26 11:40:31 ET at 29973.50, exit 11:51:00 ET at 29948.50 (D10GiveBack), lots 1, net $499.

## Merged section from W-RA (M7 London cap 3) (DS3_BRACKET_DD_BUILD_RA.md)
# DS3_BRACKET_DD_BUILD_RA - M7 London cap 3 on the live-equivalent base JN05W2JL2 (W-RA)

**VERDICT (drawdown first; pass rule = real cell beats ALL its controls on stack max DD in HOLD and L6M and mean not worse than -5%; missing controls = not finished): HOLD: stack DD real -70924 vs ref -74402, best control -63564 -> does NOT beat all controls on DD; mean +1012 $/wk (6.6% of ref) -> ok | L6M: stack DD real -23715 vs ref -22565, best control -22397 -> does NOT beat all controls on DD; mean +1747 $/wk (7.9% of ref) -> ok. No PASS claim until the controls are in.**

Built epoch 1794886056. Cells: TL3_RA_JL2_M7L_CAP3 (rule: M7, London session 02:00-08:29 ET, block entry once 3 M7 trades closed in the Globex-day session; spec autopilot/SPEC_M7_LONDON_CAP3.md) vs reference TL3_EV_JN05W2JL2. Controls: PL1-3 = random block drawn once per signal second at block rate 0.703 (M7 London, entries with >=1 close); PP1-3 = persistent draw (one draw per session instance and number of closes, so a blocked idea is not redrawn at the next signal; p 0.208 = open-loop keep of cap 3 on the JL2 reference sequence, 0.594). Dollars are base-lot engine net_fee at $1.18/contract RT; columns x175 = live lots; d_mean_484 = mean change repriced at $4.84/contract. Drawdown from cumulative daily P&L of the scope. PATH EFFECT = FREED-BOOK REPLACEMENT (generic): the controls are the baseline.

identity of the placebo branch (PP with p=0, 202610): 642 trades net 27487.58 vs JL2 642 net 27487.58 -> IDENTICAL

Windows landed (cells present / 7) : HOLD 7/7, L6M 7/7, L3M 7/7, GAP 7/7, PREUW 7/7, X' 7/7

## STACK (all books), drawdown first

| win | cell | dd | dd_ref | dd_cut_pct | dd_x175 | ww | ww_ref | stops_wk | stops_ref | d_mean | d_mean_x175 | d_mean_484 | best5 | w2l | n | n_ref |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HOLD | M7L_CAP3 | -70923.9 | -74401.8 | 4.7 | -124116.8 | -30595.5 | -31210.9 | 10.3 | 10.5 | 1011.6 | 1770.3 | 1029.2 | 1.0 | 1 | 7166 | 7380 |
| HOLD | PL1_M7L_CAP3 | -67021.1 | -74401.8 | 9.9 | -117286.9 | -34187.6 | -31210.9 | 10.4 | 10.5 | 124.1 | 217.1 | 140.9 | 1.0 | 2 | 7171 | 7380 |
| HOLD | PL2_M7L_CAP3 | -63564.4 | -74401.8 | 14.6 | -111237.8 | -30872.9 | -31210.9 | 10.4 | 10.5 | -100.7 | -176.3 | -82.6 | 1.0 | 2 | 7163 | 7380 |
| HOLD | PL3_M7L_CAP3 | -65459.9 | -74401.8 | 12.0 | -114554.8 | -29477.7 | -31210.9 | 10.5 | 10.5 | 741.6 | 1297.8 | 758.3 | 1.0 | 3 | 7172 | 7380 |
| HOLD | PP1_M7L_CAP3 | -64352.7 | -74401.8 | 13.5 | -112617.3 | -31210.9 | -31210.9 | 10.4 | 10.5 | 814.0 | 1424.4 | 831.8 | 1.0 | 1 | 7168 | 7380 |
| HOLD | PP2_M7L_CAP3 | -64370.5 | -74401.8 | 13.5 | -112648.4 | -31210.9 | -31210.9 | 10.4 | 10.5 | 343.8 | 601.6 | 363.3 | 1.0 | 1 | 7145 | 7380 |
| HOLD | PP3_M7L_CAP3 | -66190.1 | -74401.8 | 11.0 | -115832.7 | -30595.5 | -31210.9 | 10.3 | 10.5 | 361.9 | 633.3 | 382.9 | 1.0 | 1 | 7118 | 7380 |
| L6M | M7L_CAP3 | -23715.3 | -22564.6 | -5.1 | -41501.7 | -15143.1 | -13429.6 | 10.7 | 10.9 | 1747.4 | 3057.9 | 1768.0 | 1.1 | 0 | 4034 | 4161 |
| L6M | PL1_M7L_CAP3 | -22396.6 | -22564.6 | 0.7 | -39194.0 | -13152.1 | -13429.6 | 10.7 | 10.9 | 108.5 | 189.9 | 125.9 | 1.0 | 1 | 4047 | 4161 |
| L6M | PL2_M7L_CAP3 | -24637.3 | -22564.6 | -9.2 | -43115.3 | -15048.0 | -13429.6 | 10.7 | 10.9 | -519.3 | -908.8 | -498.7 | 1.0 | 1 | 4028 | 4161 |
| L6M | PL3_M7L_CAP3 | -26199.5 | -22564.6 | -16.1 | -45849.1 | -13323.1 | -13429.6 | 11.0 | 10.9 | 578.6 | 1012.6 | 599.1 | 1.0 | 1 | 4031 | 4161 |
| L6M | PP1_M7L_CAP3 | -23763.4 | -22564.6 | -5.3 | -41586.0 | -12293.9 | -13429.6 | 10.8 | 10.9 | 1203.7 | 2106.5 | 1225.0 | 1.0 | 0 | 4031 | 4161 |
| L6M | PP2_M7L_CAP3 | -23587.9 | -22564.6 | -4.5 | -41278.8 | -13066.6 | -13429.6 | 10.8 | 10.9 | 942.6 | 1649.6 | 965.5 | 1.0 | 0 | 4023 | 4161 |
| L6M | PP3_M7L_CAP3 | -25538.1 | -22564.6 | -13.2 | -44691.7 | -15196.0 | -13429.6 | 10.6 | 10.9 | 738.8 | 1292.8 | 763.7 | 1.1 | 1 | 4001 | 4161 |
| L3M | M7L_CAP3 | -23715.3 | -22564.6 | -5.1 | -41501.7 | -15143.1 | -13429.6 | 10.3 | 10.3 | 1270.7 | 2223.8 | 1284.4 | 1.0 | 0 | 1870 | 1913 |
| L3M | PL1_M7L_CAP3 | -22396.6 | -22564.6 | 0.7 | -39194.0 | -13152.1 | -13429.6 | 10.3 | 10.3 | -769.6 | -1346.8 | -757.9 | 1.0 | 1 | 1870 | 1913 |
| L3M | PL2_M7L_CAP3 | -24637.3 | -22564.6 | -9.2 | -43115.3 | -15048.0 | -13429.6 | 10.3 | 10.3 | -1024.2 | -1792.3 | -1011.6 | 1.0 | 1 | 1870 | 1913 |
| L3M | PL3_M7L_CAP3 | -26199.5 | -22564.6 | -16.1 | -45849.1 | -13323.1 | -13429.6 | 10.6 | 10.3 | 116.0 | 203.0 | 133.0 | 1.0 | 1 | 1855 | 1913 |
| L3M | PP1_M7L_CAP3 | -23763.4 | -22564.6 | -5.3 | -41586.0 | -12293.9 | -13429.6 | 10.4 | 10.3 | -152.4 | -266.7 | -135.7 | 0.9 | 0 | 1861 | 1913 |
| L3M | PP2_M7L_CAP3 | -23587.9 | -22564.6 | -4.5 | -41278.8 | -13066.6 | -13429.6 | 10.4 | 10.3 | 275.9 | 482.9 | 294.6 | 1.0 | 0 | 1853 | 1913 |
| L3M | PP3_M7L_CAP3 | -25538.1 | -22564.6 | -13.2 | -44691.7 | -15196.0 | -13429.6 | 10.3 | 10.3 | -545.3 | -954.2 | -525.8 | 1.0 | 1 | 1851 | 1913 |
| GAP | M7L_CAP3 | -53876.2 | -55205.5 | 2.4 | -94283.3 | -43527.4 | -43527.4 | 9.7 | 9.8 | -119.6 | -209.3 | -116.0 | 1.0 | 0 | 1092 | 1102 |
| GAP | PL1_M7L_CAP3 | -51171.8 | -55205.5 | 7.3 | -89550.7 | -42512.8 | -43527.4 | 9.7 | 9.8 | 81.0 | 141.7 | 87.7 | 1.0 | 1 | 1084 | 1102 |
| GAP | PL2_M7L_CAP3 | -50183.8 | -55205.5 | 9.1 | -87821.7 | -41524.8 | -43527.4 | 9.5 | 9.8 | 448.4 | 784.6 | 455.6 | 1.0 | 1 | 1085 | 1102 |
| GAP | PL3_M7L_CAP3 | -49183.7 | -55205.5 | 10.9 | -86071.4 | -42416.9 | -43527.4 | 9.7 | 9.8 | 468.2 | 819.4 | 474.7 | 1.0 | 1 | 1083 | 1102 |
| GAP | PP1_M7L_CAP3 | -55205.5 | -55205.5 | 0.0 | -96609.7 | -43527.4 | -43527.4 | 9.8 | 9.8 | -458.4 | -802.3 | -452.6 | 1.0 | 0 | 1086 | 1102 |
| GAP | PP2_M7L_CAP3 | -53876.2 | -55205.5 | 2.4 | -94283.3 | -43527.4 | -43527.4 | 9.7 | 9.8 | -479.9 | -839.8 | -472.7 | 1.0 | 1 | 1082 | 1102 |
| GAP | PP3_M7L_CAP3 | -51781.0 | -55205.5 | 6.2 | -90616.7 | -39543.8 | -43527.4 | 9.5 | 9.8 | 46.4 | 81.2 | 53.7 | 1.0 | 0 | 1080 | 1102 |
| PREUW | M7L_CAP3 | -71239.3 | -70931.2 | -0.4 | -124668.7 | -25913.0 | -28957.8 | 8.8 | 9.0 | 457.6 | 800.8 | 466.3 | 1.0 | 0 | 4125 | 4201 |
| PREUW | PL1_M7L_CAP3 | -71572.0 | -70931.2 | -0.9 | -125250.9 | -25279.2 | -28957.8 | 8.8 | 9.0 | 44.6 | 78.1 | 53.5 | 1.0 | 0 | 4112 | 4201 |
| PREUW | PL2_M7L_CAP3 | -66798.6 | -70931.2 | 5.8 | -116897.5 | -23067.5 | -28957.8 | 8.8 | 9.0 | 313.0 | 547.7 | 323.2 | 1.0 | 0 | 4106 | 4201 |
| PREUW | PL3_M7L_CAP3 | -69367.0 | -70931.2 | 2.2 | -121392.3 | -25066.1 | -28957.8 | 8.8 | 9.0 | 668.4 | 1169.6 | 681.0 | 1.0 | 2 | 4090 | 4201 |
| PREUW | PP1_M7L_CAP3 | -75969.0 | -70931.2 | -7.1 | -132945.8 | -26041.9 | -28957.8 | 8.8 | 9.0 | 398.6 | 697.5 | 409.5 | 1.0 | 1 | 4109 | 4201 |
| PREUW | PP2_M7L_CAP3 | -69377.5 | -70931.2 | 2.2 | -121410.6 | -23094.2 | -28957.8 | 8.8 | 9.0 | 275.0 | 481.2 | 285.0 | 1.0 | 0 | 4114 | 4201 |
| PREUW | PP3_M7L_CAP3 | -61325.2 | -70931.2 | 13.5 | -107319.1 | -21884.5 | -28957.8 | 8.8 | 9.0 | 566.4 | 991.2 | 578.3 | 1.0 | 0 | 4096 | 4201 |
| X' | M7L_CAP3 | -70353.1 | -73618.0 | 4.4 | -123117.9 | -35303.7 | -37051.8 | 9.9 | 9.9 | 107.7 | 188.4 | 109.2 | 1.0 | 0 | 5787 | 5816 |
| X' | PL1_M7L_CAP3 | -69835.4 | -73618.0 | 5.1 | -122212.0 | -31337.3 | -37051.8 | 9.8 | 9.9 | 148.9 | 260.5 | 154.6 | 1.0 | 1 | 5724 | 5816 |
| X' | PL2_M7L_CAP3 | -70475.1 | -73618.0 | 4.3 | -123331.5 | -30138.5 | -37051.8 | 9.8 | 9.9 | 109.7 | 191.9 | 115.1 | 1.0 | 0 | 5729 | 5816 |
| X' | PL3_M7L_CAP3 | -73458.9 | -73618.0 | 0.2 | -128553.1 | -35092.6 | -37051.8 | 9.8 | 9.9 | 149.0 | 260.8 | 154.4 | 1.0 | 0 | 5727 | 5816 |
| X' | PP1_M7L_CAP3 | -71241.4 | -73618.0 | 3.2 | -124672.5 | -36289.6 | -37051.8 | 9.8 | 9.9 | 266.7 | 466.7 | 271.7 | 1.0 | 0 | 5726 | 5816 |
| X' | PP2_M7L_CAP3 | -72189.9 | -73618.0 | 1.9 | -126332.4 | -36373.4 | -37051.8 | 9.8 | 9.9 | 309.0 | 540.7 | 313.7 | 1.0 | 0 | 5736 | 5816 |
| X' | PP3_M7L_CAP3 | -70186.7 | -73618.0 | 4.7 | -122826.8 | -35137.4 | -37051.8 | 9.8 | 9.9 | 334.0 | 584.5 | 339.1 | 1.0 | 1 | 5727 | 5816 |

## M7 LONDON slice, drawdown first

| win | cell | dd | dd_ref | dd_cut_pct | dd_x175 | ww | ww_ref | stops_wk | stops_ref | d_mean | d_mean_x175 | d_mean_484 | best5 | w2l | n | n_ref |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HOLD | M7L_CAP3 | -13877.0 | -54248.4 | 74.4 | -24284.7 | -9211.1 | -14641.5 | 0.4 | 0.7 | 1086.3 | 1901.0 | 1110.2 | 0.9 | 3 | 674 | 963 |
| HOLD | PL1_M7L_CAP3 | -28451.4 | -54248.4 | 47.6 | -49789.9 | -8662.4 | -14641.5 | 0.4 | 0.7 | 752.2 | 1316.3 | 778.3 | 0.7 | 5 | 652 | 963 |
| HOLD | PL2_M7L_CAP3 | -32327.4 | -54248.4 | 40.4 | -56572.9 | -8255.8 | -14641.5 | 0.4 | 0.7 | 660.1 | 1155.1 | 685.3 | 0.7 | 4 | 669 | 963 |
| HOLD | PL3_M7L_CAP3 | -24580.7 | -54248.4 | 54.7 | -43016.3 | -9363.7 | -14641.5 | 0.6 | 0.7 | 905.2 | 1584.1 | 929.6 | 1.1 | 7 | 658 | 963 |
| HOLD | PP1_M7L_CAP3 | -27757.4 | -54248.4 | 48.8 | -48575.5 | -8986.9 | -14641.5 | 0.4 | 0.7 | 892.4 | 1561.7 | 920.1 | 0.8 | 5 | 632 | 963 |
| HOLD | PP2_M7L_CAP3 | -29760.3 | -54248.4 | 45.1 | -52080.5 | -10579.7 | -14641.5 | 0.4 | 0.7 | 378.0 | 661.6 | 407.3 | 0.8 | 5 | 612 | 963 |
| HOLD | PP3_M7L_CAP3 | -16954.8 | -54248.4 | 68.7 | -29670.9 | -10917.8 | -14641.5 | 0.4 | 0.7 | 687.9 | 1203.8 | 718.0 | 0.9 | 6 | 599 | 963 |
| L6M | M7L_CAP3 | -13877.0 | -37263.0 | 62.8 | -24284.7 | -9189.1 | -14641.5 | 0.5 | 0.8 | 1945.3 | 3404.3 | 1971.5 | 1.1 | 1 | 349 | 512 |
| L6M | PL1_M7L_CAP3 | -16003.8 | -37263.0 | 57.1 | -28006.7 | -8087.7 | -14641.5 | 0.3 | 0.8 | 893.4 | 1563.5 | 920.7 | 0.7 | 2 | 346 | 512 |
| L6M | PL2_M7L_CAP3 | -16954.1 | -37263.0 | 54.5 | -29669.6 | -8093.4 | -14641.5 | 0.4 | 0.8 | 747.2 | 1307.7 | 774.1 | 0.6 | 2 | 349 | 512 |
| L6M | PL3_M7L_CAP3 | -24580.7 | -37263.0 | 34.0 | -43016.3 | -9363.7 | -14641.5 | 0.7 | 0.8 | 880.4 | 1540.8 | 908.0 | 0.7 | 4 | 337 | 512 |
| L6M | PP1_M7L_CAP3 | -15532.6 | -37263.0 | 58.3 | -27182.1 | -6278.5 | -14641.5 | 0.5 | 0.8 | 1279.5 | 2239.2 | 1310.6 | 0.7 | 2 | 324 | 512 |
| L6M | PP2_M7L_CAP3 | -15034.0 | -37263.0 | 59.7 | -26309.5 | -8244.5 | -14641.5 | 0.5 | 0.8 | 1033.5 | 1808.6 | 1065.3 | 0.8 | 2 | 318 | 512 |
| L6M | PP3_M7L_CAP3 | -15664.7 | -37263.0 | 58.0 | -27413.2 | -8690.5 | -14641.5 | 0.3 | 0.8 | 1115.3 | 1951.8 | 1148.7 | 0.9 | 3 | 305 | 512 |
| L3M | M7L_CAP3 | -13877.0 | -23405.7 | 40.7 | -24284.7 | -9189.1 | -14641.5 | 0.7 | 0.9 | 1706.1 | 2985.6 | 1725.8 | 1.1 | 1 | 175 | 236 |
| L3M | PL1_M7L_CAP3 | -16003.8 | -23405.7 | 31.6 | -28006.7 | -8087.7 | -14641.5 | 0.5 | 0.9 | 706.1 | 1235.6 | 730.0 | 0.9 | 1 | 161 | 236 |
| L3M | PL2_M7L_CAP3 | -16954.1 | -23405.7 | 27.6 | -29669.6 | -8093.4 | -14641.5 | 0.6 | 0.9 | 548.5 | 959.8 | 571.0 | 0.8 | 0 | 167 | 236 |
| L3M | PL3_M7L_CAP3 | -16507.1 | -23405.7 | 29.5 | -28887.5 | -9363.7 | -14641.5 | 0.8 | 0.9 | 545.9 | 955.2 | 567.3 | 0.7 | 2 | 164 | 236 |
| L3M | PP1_M7L_CAP3 | -15532.6 | -23405.7 | 33.6 | -27182.1 | -6278.5 | -14641.5 | 0.8 | 0.9 | 589.5 | 1031.6 | 613.7 | 0.8 | 1 | 164 | 236 |
| L3M | PP2_M7L_CAP3 | -15034.0 | -23405.7 | 35.8 | -26309.5 | -8244.5 | -14641.5 | 0.8 | 0.9 | 884.4 | 1547.7 | 909.8 | 0.8 | 1 | 158 | 236 |
| L3M | PP3_M7L_CAP3 | -15664.7 | -23405.7 | 33.1 | -27413.2 | -8690.5 | -14641.5 | 0.6 | 0.9 | 449.6 | 786.7 | 480.2 | 0.8 | 2 | 144 | 236 |
| GAP | M7L_CAP3 | -21963.8 | -19185.5 | -14.5 | -38436.7 | -9801.7 | -9801.7 | 0.7 | 0.8 | -119.6 | -209.3 | -116.0 | 0.8 | 1 | 125 | 135 |
| GAP | PL1_M7L_CAP3 | -19304.0 | -19185.5 | -0.6 | -33782.0 | -8025.8 | -9801.7 | 0.8 | 0.8 | 37.2 | 65.1 | 45.6 | 0.7 | 2 | 113 | 135 |
| GAP | PL2_M7L_CAP3 | -17811.8 | -19185.5 | 7.2 | -31170.7 | -8025.8 | -9801.7 | 0.6 | 0.8 | 398.7 | 697.7 | 407.6 | 0.8 | 2 | 113 | 135 |
| GAP | PL3_M7L_CAP3 | -14019.9 | -19185.5 | 26.9 | -24534.8 | -8407.3 | -9801.7 | 0.8 | 0.8 | 472.9 | 827.6 | 480.7 | 0.6 | 2 | 113 | 135 |
| GAP | PP1_M7L_CAP3 | -26409.5 | -19185.5 | -37.7 | -46216.7 | -9801.7 | -9801.7 | 0.8 | 0.8 | -549.7 | -961.9 | -543.5 | 0.6 | 1 | 118 | 135 |
| GAP | PP2_M7L_CAP3 | -26627.6 | -19185.5 | -38.8 | -46598.4 | -11000.5 | -9801.7 | 0.8 | 0.8 | -571.1 | -999.5 | -563.6 | 0.6 | 1 | 114 | 135 |
| GAP | PP3_M7L_CAP3 | -20478.4 | -19185.5 | -6.7 | -35837.2 | -8407.3 | -9801.7 | 0.5 | 0.8 | 155.6 | 272.3 | 164.0 | 0.8 | 1 | 110 | 135 |
| PREUW | M7L_CAP3 | -27579.8 | -27201.4 | -1.4 | -48264.7 | -9547.4 | -9750.3 | 0.9 | 1.2 | -61.3 | -107.3 | -48.3 | 0.7 | 4 | 451 | 568 |
| PREUW | PL1_M7L_CAP3 | -25913.7 | -27201.4 | 4.7 | -45348.9 | -7592.4 | -9750.3 | 0.9 | 1.2 | -199.5 | -349.2 | -184.6 | 0.7 | 5 | 428 | 568 |
| PREUW | PL2_M7L_CAP3 | -21065.7 | -27201.4 | 22.6 | -36864.9 | -7165.3 | -9750.3 | 0.9 | 1.2 | -10.7 | -18.7 | 4.7 | 0.8 | 5 | 428 | 568 |
| PREUW | PL3_M7L_CAP3 | -17690.8 | -27201.4 | 35.0 | -30959.0 | -5309.8 | -9750.3 | 0.9 | 1.2 | 224.0 | 391.9 | 242.5 | 0.3 | 2 | 407 | 568 |
| PREUW | PP1_M7L_CAP3 | -30520.1 | -27201.4 | -12.2 | -53410.2 | -7016.3 | -9750.3 | 0.8 | 1.2 | -219.2 | -383.6 | -200.5 | 0.6 | 5 | 401 | 568 |
| PREUW | PP2_M7L_CAP3 | -26211.7 | -27201.4 | 3.6 | -45870.4 | -7036.7 | -9750.3 | 0.9 | 1.2 | -337.7 | -590.9 | -320.5 | 0.6 | 1 | 414 | 568 |
| PREUW | PP3_M7L_CAP3 | -16130.4 | -27201.4 | 40.7 | -28228.3 | -6637.5 | -9750.3 | 0.8 | 1.2 | 193.0 | 337.7 | 212.1 | 0.7 | 4 | 396 | 568 |
| X' | M7L_CAP3 | -56843.4 | -69240.2 | 17.9 | -99476.0 | -6448.3 | -7313.8 | 1.2 | 1.3 | 175.9 | 307.8 | 177.8 | 1.0 | 0 | 653 | 689 |
| X' | PL1_M7L_CAP3 | -60393.7 | -69240.2 | 12.8 | -105688.9 | -7067.9 | -7313.8 | 1.1 | 1.3 | 204.7 | 358.2 | 211.0 | 0.6 | 4 | 587 | 689 |
| X' | PL2_M7L_CAP3 | -66223.6 | -69240.2 | 4.4 | -115891.3 | -7067.9 | -7313.8 | 1.1 | 1.3 | 143.4 | 251.0 | 149.2 | 0.7 | 1 | 597 | 689 |
| X' | PL3_M7L_CAP3 | -28549.3 | -69240.2 | 58.8 | -49961.2 | -5736.1 | -7313.8 | 1.1 | 1.3 | 313.9 | 549.3 | 319.7 | 0.7 | 4 | 593 | 689 |
| X' | PP1_M7L_CAP3 | -50669.3 | -69240.2 | 26.8 | -88671.3 | -7075.6 | -7313.8 | 1.1 | 1.3 | 326.8 | 571.9 | 332.7 | 0.9 | 1 | 584 | 689 |
| X' | PP2_M7L_CAP3 | -51289.4 | -69240.2 | 25.9 | -89756.5 | -7075.6 | -7313.8 | 1.1 | 1.3 | 336.7 | 589.2 | 342.5 | 0.9 | 0 | 587 | 689 |
| X' | PP3_M7L_CAP3 | -51763.7 | -69240.2 | 25.2 | -90586.5 | -6448.3 | -7313.8 | 1.1 | 1.3 | 325.3 | 569.3 | 331.4 | 1.0 | 1 | 582 | 689 |

## With week 2026-W44 removed from both sides

| win | cell | scope | dd | dd_ref | dd_cut_pct | d_ww | d_mean |
|---|---|---|---|---|---|---|---|
| HOLD | M7L_CAP3 | M7:london | -13877.0 | -54248.4 | 74.4 | 5430.4 | 1105.9 |
| HOLD | PL1_M7L_CAP3 | M7:london | -28451.4 | -54248.4 | 47.6 | 5979.1 | 748.5 |
| HOLD | PL2_M7L_CAP3 | M7:london | -32327.4 | -54248.4 | 40.4 | 6385.7 | 669.3 |
| HOLD | PL3_M7L_CAP3 | M7:london | -24580.7 | -54248.4 | 54.7 | 5277.8 | 948.5 |
| HOLD | PP1_M7L_CAP3 | M7:london | -27757.4 | -54248.4 | 48.8 | 5654.6 | 915.4 |
| HOLD | PP2_M7L_CAP3 | M7:london | -29760.3 | -54248.4 | 45.1 | 4061.8 | 397.7 |
| HOLD | PP3_M7L_CAP3 | M7:london | -16954.8 | -54248.4 | 68.7 | 3723.7 | 694.3 |
| L3M | M7L_CAP3 | M7:london | -13877.0 | -23405.7 | 40.7 | 5452.4 | 1783.9 |
| L3M | PL1_M7L_CAP3 | M7:london | -16003.8 | -23405.7 | 31.6 | 6553.8 | 691.6 |
| L3M | PL2_M7L_CAP3 | M7:london | -16954.1 | -23405.7 | 27.6 | 6548.1 | 585.3 |
| L3M | PL3_M7L_CAP3 | M7:london | -16507.1 | -23405.7 | 29.5 | 5277.8 | 717.6 |
| L3M | PP1_M7L_CAP3 | M7:london | -15532.6 | -23405.7 | 33.6 | 8363.0 | 680.7 |
| L3M | PP2_M7L_CAP3 | M7:london | -15034.0 | -23405.7 | 35.8 | 6397.0 | 962.3 |
| L3M | PP3_M7L_CAP3 | M7:london | -15664.7 | -23405.7 | 33.1 | 5951.0 | 474.9 |
| L6M | M7L_CAP3 | M7:london | -13877.0 | -37263.0 | 62.8 | 5452.4 | 1984.3 |
| L6M | PL1_M7L_CAP3 | M7:london | -16003.8 | -37263.0 | 57.1 | 6553.8 | 886.2 |
| L6M | PL2_M7L_CAP3 | M7:london | -16954.1 | -37263.0 | 54.5 | 6548.1 | 765.7 |
| L6M | PL3_M7L_CAP3 | M7:london | -24580.7 | -37263.0 | 34.0 | 5277.8 | 966.3 |
| L6M | PP1_M7L_CAP3 | M7:london | -15532.6 | -37263.0 | 58.3 | 8363.0 | 1325.2 |
| L6M | PP2_M7L_CAP3 | M7:london | -15034.0 | -37263.0 | 59.7 | 6397.0 | 1072.4 |
| L6M | PP3_M7L_CAP3 | M7:london | -15664.7 | -37263.0 | 58.0 | 5951.0 | 1128.0 |
| HOLD | M7L_CAP3 | all | -70923.9 | -74401.8 | 4.7 | 615.4 | 1031.2 |
| HOLD | PL1_M7L_CAP3 | all | -67021.1 | -74401.8 | 9.9 | -2976.6 | 120.4 |
| HOLD | PL2_M7L_CAP3 | all | -63564.4 | -74401.8 | 14.6 | 338.0 | -91.4 |
| HOLD | PL3_M7L_CAP3 | all | -65459.9 | -74401.8 | 12.0 | 1733.2 | 749.7 |
| HOLD | PP1_M7L_CAP3 | all | -64352.7 | -74401.8 | 13.5 | 0.0 | 836.9 |
| HOLD | PP2_M7L_CAP3 | all | -64370.5 | -74401.8 | 13.5 | 0.0 | 363.4 |
| HOLD | PP3_M7L_CAP3 | all | -66190.1 | -74401.8 | 11.0 | 615.4 | 368.3 |
| L3M | M7L_CAP3 | all | -23715.3 | -22508.4 | -5.4 | -1713.5 | 1348.6 |
| L3M | PL1_M7L_CAP3 | all | -21542.6 | -22508.4 | 4.3 | 277.5 | -784.1 |
| L3M | PL2_M7L_CAP3 | all | -24637.3 | -22508.4 | -9.5 | -1618.4 | -987.3 |
| L3M | PL3_M7L_CAP3 | all | -26199.5 | -22508.4 | -16.4 | 106.5 | 148.4 |
| L3M | PP1_M7L_CAP3 | all | -18805.6 | -22508.4 | 16.5 | 2472.9 | -61.2 |
| L3M | PP2_M7L_CAP3 | all | -21422.1 | -22508.4 | 4.8 | 363.0 | 353.8 |
| L3M | PP3_M7L_CAP3 | all | -25538.1 | -22508.4 | -13.5 | -1766.4 | -519.9 |
| L6M | M7L_CAP3 | all | -23715.3 | -22508.4 | -5.4 | -1713.5 | 1786.3 |
| L6M | PL1_M7L_CAP3 | all | -21542.6 | -22508.4 | 4.3 | 277.5 | 101.3 |
| L6M | PL2_M7L_CAP3 | all | -24637.3 | -22508.4 | -9.5 | -1618.4 | -500.9 |
| L6M | PL3_M7L_CAP3 | all | -26199.5 | -22508.4 | -16.4 | 106.5 | 594.8 |
| L6M | PP1_M7L_CAP3 | all | -19463.8 | -22508.4 | 13.5 | 2472.9 | 1249.3 |
| L6M | PP2_M7L_CAP3 | all | -21422.1 | -22508.4 | 4.8 | 363.0 | 981.6 |
| L6M | PP3_M7L_CAP3 | all | -25538.1 | -22508.4 | -13.5 | -1766.4 | 751.4 |

## Placebo validity: realized M7 London keep share (entries with >=1 earlier close in the instance) vs the real cell, HOLD

A control is INVALID when its kept-entry count differs from the real cell by more than 5%.

| control | kept_n_ge2 | real_kept_n_ge2 | ratio_to_real | trades | real_trades | INVALID_CONTROL |
|---|---|---|---|---|---|---|
| PL1_M7L_CAP3 | 401 | 423 | 0.948 | 652 | 674 | True |
| PL2_M7L_CAP3 | 418 | 423 | 0.988 | 669 | 674 | False |
| PL3_M7L_CAP3 | 407 | 423 | 0.962 | 658 | 674 | False |
| PP1_M7L_CAP3 | 381 | 423 | 0.901 | 632 | 674 | True |
| PP2_M7L_CAP3 | 361 | 423 | 0.853 | 612 | 674 | True |
| PP3_M7L_CAP3 | 348 | 423 | 0.823 | 599 | 674 | True |

## Week-clustered statistics, M7 London slice, HOLD (52 weeks; delta vs reference)

| cell | weeks | mean_wk | t_cluster | ci90_lo | ci90_hi | pos_weeks | mean_noW44 | mean_wo_top3 | dd_ref | dd_cell | P_dd_shallower |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7L_CAP3 | 52 | 1089.25 | 2.64 | 431.62 | 1766.69 | 0.62 | 1130.67 | 615.01 | -48166.20 | -11416.62 | 0.99 |
| PL1_M7L_CAP3 | 52 | 754.23 | 1.77 | 48.12 | 1455.79 | 0.56 | 765.28 | 321.35 | -48166.20 | -27663.08 | 0.95 |
| PL2_M7L_CAP3 | 52 | 661.87 | 1.56 | -38.24 | 1344.24 | 0.52 | 684.34 | 250.51 | -48166.20 | -31539.08 | 0.93 |
| PL3_M7L_CAP3 | 52 | 907.71 | 2.13 | 211.08 | 1599.63 | 0.60 | 969.76 | 578.53 | -48166.20 | -19751.14 | 0.98 |
| PP1_M7L_CAP3 | 52 | 894.85 | 1.87 | 144.35 | 1691.06 | 0.54 | 935.90 | 415.62 | -48166.20 | -24070.96 | 0.95 |
| PP2_M7L_CAP3 | 52 | 379.08 | 0.88 | -303.16 | 1081.07 | 0.52 | 406.57 | -67.15 | -48166.20 | -24229.10 | 0.90 |
| PP3_M7L_CAP3 | 52 | 689.75 | 1.71 | 60.52 | 1356.88 | 0.50 | 709.81 | 263.01 | -48166.20 | -14668.32 | 0.97 |

## Earlier statements about random placebos (see DS3_REENTRY_ALL.md 5a)
See autopilot/RA_PLACEBO_VOID_LIST.md.

