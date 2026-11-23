<!-- PR2:BEGIN -->
## RE-SCORE UNDER THE CALIBRATED RULE (W-PR2, FIRST PASS, ulcer index primary; data ends 2026-10-30; written 19:26 UTC)

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
