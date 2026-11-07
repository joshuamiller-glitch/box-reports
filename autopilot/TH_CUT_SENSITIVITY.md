# TH_CUT_SENSITIVITY - SENS-TH (PRE-PROOF, diagnostics only, no PASS claim, nothing tuned to the live week)
2026-11-07. Question: how much would a TH rule table built on the live-exact cut evaluator (zl2_cut_eval / evaltrade11, ~55% within-10-s agreement with live) be distorted by the evaluator's uncertain inputs?
Base: ws11 r11 (rebuild11, prereg 460c06c1; 197 closed trades, +48,893, 106 cuts = 99 ThL2Cut + 7 PolicyCut; re-run bit-identical to ws11_r11.pkl). Method: private copy /mnt/l2/l2vast/_sens_th/ws11_sens.py = ws11.py plus an env hook that perturbs ONLY the cut-evaluator inputs; the whole engine (locks, busy, fills) re-runs per perturbation (3 s each). Prereg /mnt/l2/l2vast/_sens_th/PREREG_SENS_TH.md sha256 7e0331ef... logged in DECISIONS.md before any perturbed run. Frozen file sha 424c68da... (engine reads it as before). Seal: ds3_all_ea/manifest_after.json sha 759f2258... identical before/after; nothing written outside /mnt/l2/l2vast/_sens_th/. Read-only access to ds3_g2_blind SS/SC and tape tables as in BASE-10. Data: sens_summary.csv, cut_fragility.csv, gap_cutmismatch.csv in that directory.

## 1. Per-perturbation table (vs base)
cuts = ThL2Cut+PolicyCut; cut $ = net of the cut trades; cmh = cut-minus-hold = cut trade net minus the same (book, signal) trade in the engine no-cut run (74 of 106 base cuts have a hold counterpart; the rest differ in lock/busy sequence). Per-trade = mean cmh over matched cuts.
| run | trades | cuts | cut $ | total net | d total | cmh sum (n matched) | cmh $/trade | base cuts lost | new cuts | cut time moved >10 s |
|--|--|--|--|--|--|--|--|--|--|--|
| base | 197 | 106 | -178,760 | 48,893 | 0 | -92,265 (74) | -1,247 | - | - | - |
| clock/fill offset -3..+3 s (6 runs) | 197 | 106 | -178,760 | 48,893 | 0 | -92,265 | -1,247 | 0 | 0 | 0 |
| print-order shift -2 | 196 | 105 | -180,287 | 46,420 | -2,472 | -89,684 (73) | -1,229 | 3 | 2 | 6 |
| shift -1 | 189 | 99 | -162,465 | 48,332 | -560 | -83,478 (70) | -1,193 | 8 | 1 | 3 |
| shift +1 | 197 | 106 | -179,820 | 47,833 | -1,060 | -93,295 (74) | -1,261 | 0 | 0 | 1 |
| shift +2 | 198 | 107 | -180,756 | 46,896 | -1,996 | -93,245 (74) | -1,260 | 2 | 3 | 2 |
| pulled multiple 25 | 190 | 102 | -163,495 | 56,237 | +7,345 | -87,708 (73) | -1,202 | 5 | 1 | 15 |
| pulled multiple 35 | 169 | 88 | -144,335 | 62,575 | +13,683 | -73,243 (65) | -1,127 | 20 | 2 | 6 |
| cancel scale 0.8 (thinner/hidden pulls fewer) | 168 | 87 | -143,541 | 63,405 | +14,512 | -74,622 (65) | -1,148 | 21 | 2 | 9 |
| cancel scale 1.25 | 187 | 100 | -162,066 | 56,466 | +7,574 | -88,594 (71) | -1,248 | 8 | 2 | 16 |
| cancel scale 1.5 | 189 | 103 | -162,419 | 52,513 | +3,621 | -87,774 (71) | -1,236 | 9 | 6 | 20 |
| MedLevel x0.8 / x1.25 | = cancel 1.25 / 0.8 (ratio rule) | | | | | | | | | |
| MedLevel warm-start stream | 197 | 106 | -178,760 | 48,893 | 0 | -92,265 | -1,247 | 0 | 0 | 0 |
| window 4 s | 170 | 90 | -143,168 | 64,938 | +16,045 | -72,697 (65) | -1,118 | 18 | 2 | 7 |
| window 6 s | 200 | 108 | -178,711 | 45,833 | -3,060 | -89,179 (74) | -1,205 | 2 | 4 | 10 |
| no cut (hold all) | 140 | 0 | 0 | 118,714 | +69,822 | - | - | 106 | 0 | - |
Notes. (a) Clock/fill offsets change nothing at all (checked the hook is live: -120 s moves the week to -55k). The decision depends on relative time only (1-s throttles, 5-s window); consistent with the earlier entry-lag variants. (b) Warm MedLevel changes nothing (converged within minutes; stream hash differs). (c) Level-size scaling that scales book and cancels together is invariant (ratio); only the asymmetric versions matter. Cancel x0.8 equals MedLevel x1.25. (d) The engine with NO cut earns +118.7k (live: +104.1k); the cut costs the engine about 70k in total and -1.1k to -1.3k per matched cut trade in every perturbation.
Reading: the engine total moves -3k..+16k (about -6%..+33% of base) and cut count 87..108 under plausible inputs; dollars-per-cut-trade is stable (-1.1k..-1.3k). The SIGN of "cut minus hold" never changes; the cut COUNT and the set of trades cut do.

## 2. Fragile vs robust cuts (base cuts, 106)
Fragile = not cut, or cut time moves >10 s, in any of the SMALL set (offset +-1,+-2; shift +-1; pm 25/35; cancel 0.8/1.25; Med 0.8/1.25; warm). 47 fragile (44%), 59 robust. Number of small-set perturbations that flip a cut: 0:59, 2:8, 3:26, 4:6, 6:1, 7:6 (multiples of the paired runs, since Med x and cancel x are mirror images; the 26 with 3 flips are the marginal ones the evaluator fired on near the 30x line).
By book (fragile/total): P7 17/32, K7 16/34, A7 5/13, M7 4/14, U7 2/3, X4 1/2, X5 1/2, H7 1/2, O7 0/2, X3 0/2. Matched cmh: fragile cuts -31.5k (31 matched), robust -60.7k (43 matched), per matched trade -1,017 vs -1,412.
Engine-vs-live gap link (gap_r11_pairs.csv, 157/159 pairs mapped): the dominant exit gap is 9 matched pairs where the engine cut and live did not (exit part +51,849 of the total pair exit +49,140). Of those, 6 are fragile = +36,977 (71%), 3 robust = +14,871 (29%). 7 of the 9 never flip to hold in any of the 19 perturbed runs (these hold the 29,583 and include the two P7 target trades Wed 19:27 +12.9k and Thu 02:53 +12.5k, plus Wed K7 21:51); the 2 that do flip (K7 Tue 21:39 +3.5k, P7 Sun 19:11 +18.8k) flip only in 4 of 19 runs. So: roughly 70% of the gap dollars sit on fragile cuts under the SMALL set, but the SINGLE biggest items do not go away under any input noise tried (nflip_full=0 for 7 of 9; $29.6k). The gap is therefore partly input noise (it can be moved by 14-16k via the pulled multiple/window) and partly structural (10-level depth, packet ordering, live state we cannot observe). Matched cut-vs-cut pairs: 76 pairs, pair exit -3.1k (30 fragile, -3.0k).

## 3. Design: evaluator-noise robustness requirement for programs A and B (document only)
Intent: a TH rule table is only as good as the evaluator's cut/hold decisions; a rule whose benefit exists only at one setting of uncertain inputs is not usable.
R1 Perturbation set PS (frozen in each prereg): offset +-2 s; print shift +-1; pulled multiple 25 and 35 (as the rule's own threshold is a different thing: the perturbation multiplies the evaluator's cut dollars baseline, not the candidate rule's parameter); cancel scale 0.8 and 1.25 (stands for hidden ranks 11-20 and thinner/thicker book); window 4 and 6 s; warm MedLevel. 10-13 re-evaluations; each costs seconds.
R2 Sign rule: a candidate rule's benefit (rule-minus-baseline P&L on the training sample, net of FEES.md fees) must keep its sign and be >= 50% of its nominal value in >= 80% of PS runs (hard fail if the sign flips in the nominal-direction perturbations pm35 or cancel 0.8, which are the two that moved the engine most).
R3 Fragile-cut share cap: compute fragile cuts as defined in section 2 on the rule table's own cut set. Fragile-cut dollars (cut-minus-hold on fragile cuts, absolute) must be <= 30% of the rule's total claimed benefit, and the benefit recomputed on robust cuts alone must itself have the right sign and >= 50% of the full benefit. (Base engine today: 44% of cuts fragile, 34% of matched cmh dollars.)
R4 No selection on the perturbed runs: PS is for acceptance only; rules are ranked on nominal; ties are not broken by robustness after seeing PS results (one-way gate).
R5 Gap anchor: report the same table split by 'fragile / robust' against live-held trades (engine cut, live not): a rule that improves mainly by removing robust live-disagreeing cuts is flagged structural, not tuned away.
R6 Reporting: sens table (this file's section 1 columns) per finalist; programs A and B claim nothing as PASS unless R2 and R3 hold; Gate 0 status unchanged by this file.
Open (lead's choice): thresholds 80% / 50% / 30% are proposals; the noise set could add the th_eval.csv 20-level calibration once v1.5 data arrives.
