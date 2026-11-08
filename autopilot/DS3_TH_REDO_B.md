# DS3_TH_REDO_B - program B, LOSS side L1 (price-path Trade Health grid) on the REPLICA engine, 2023-04..2026-10
**cut-input agreement with live: 14% at 0% false (best FIT-selected convention) / literal reading 45 of 92 within +-2 s with 23 false; engine Gate 0 NOT passed; PRE-PROOF**

Owner TH-B, 2026-11-08. Research only, Shadow only, no PASS claim, nothing here reaches THP_POLICY_D7. Prereg: TH_REDO_PREREG_B.md (addendum 1, sha a9320dd8...) as adapted by TH_REDO_PREREG_ADOPTION_REPLICA2.md (replica engine, Tier S then finalists, Tier 1 limited to 40, robustness set). Prereg shas logged in DECISIONS.md before any score. Seal manifest_after.json sha 759f2258... unchanged (checked at the end).

## Result in plain sentences
1. No B rule qualifies. None of the 11 finalists is placebo-clean AND beats the live L2 cut on L6M and PRE with the carrying week dropped AND keeps its sign across the convention set AND holds on the exact engine. Nothing goes to MORNING.md.
2. In the Tier S screen (14,580 cells, 7,290 distinct: req 4 behaves as req 3 because the live code caps votes at 3) the large positive S of the best pooled cells is mostly the removal of the live L2 cut, not path skill: against the silent convention (alpha 0, no L2 cut) most of them turn negative, and random exits at armed instants score the same (placebo p 1.0 for every S-ranked finalist).
3. Only a small family of KB cells (elig 30-40 pt, 15-s momentum 8 pt + stall, 10-s evaluation) is placebo-clean and family-clean in Tier S (family p .0099 = the floor of 200 worlds, S about +950 $/week, KB alone). On the exact engine (F01-F03) they are about 0 on L6M (-37, -150, +164 $/wk), +430 HOLD, +1.1k..1.6k PRE, negative on X' and L1M: not a rule that beats the live cut on both L6M and PRE with margin; 99% of their cuts are fragile under a +-2 s input offset, only 3 of 7 perturbation/convention runs keep the sign at half size, and they fail drawdown first on the engine.
4. The closest on the exact engine is F10 (KB, elig 20, 15-s momentum 8 pt, stall 30 s/6 pt, efficiency 60 s < .4, 10-s evaluation): positive on L1M..L6M, HOLD, MID, PRE (+1.3k, +2.6k, +2.2k, +0.9k, +1.4k, +1.0k, +1.6k per week) and -440 on X', but Tier S placebo p is 1.0 and its walk-forward is not separate evidence; it is a LEAD for a forward log only.
5. Tier S overstates by a wide margin (e.g. F06 Tier S S=+2.9k, engine L6M -4.0k): cuts that stay open instead of being cut by the L2 rule change the later signals (cascade), which Tier S holds fixed. Engine numbers are the ones to read.

## What was run
* Engine: REPLICA (adapter of HIST-PIPE day files, ITER14 settings, month chunks with 10 warm-up days, engine flat at each month start, 970 validated day files; config of the settled D7 week assumed for 3.7 years). Rule code: rules_replica.RuleReplica3 `l1loss` (literal port of ManageLoss, 100-ms samples). HOLD and NO-CUT worlds are TH-A's determinism-checked runs (identical trade lists reproduced by my recorder: 917 / 689 trades in 2026-10).
* Tier S (all 14,580 B1 cells x 6 books + pooled x 2 modes): one recorder pass (code/th_redo/thB_rec.py) writes one row per open trade per wall second once the adverse extreme is >= 10 pt (78.2 M rows, 23,788 trades, 23,282 in the 14 live units); a cell is a filter (thB_core.fire_b). Stated approximations: evaluation clock = wall-second grid (engine: first print >= freq s after the previous evaluation); entries and later signals held fixed (no re-entry cascade); one state per trade (engine resets it at adds). Placebo: 200 shared-seed worlds, same cut trades moved to a random armed instant; Westfall-Young family p over all 87,480 unit-cells per mode; purged monthly walk-forward over all cells.
* Modes: ALONE = path rule replaces the L2 loss cut (rules_replica l2loss False; the prereg's "ReplacePath" wording is ambiguous: in D7 ReplacePath = path TH off, L2 on = HOLD, so the path-only reading is named ALONE here); ADDTO = L2 cut kept + path (AddToPath). Baseline = HOLD (live L2 rule, literal reading). Unit = book (6) of the 14 live book x session units; windows asof 2026-10-30; stats with carrying week dropped (decision) and not dropped (nodrop in the pickles).
* Convention robustness set: the FIT conventions exist only on the blind week (not in the history pipeline), so the history baseline is bracketed by alpha = share of live L2 cuts present: 1 (literal reading = HOLD), 0.14 (best FIT-selected convention, linear mix), 0 (silent limit = NO-CUT). Perturbation set limited to what B can see: input clock offset +-2 s, fill offset +-2 s (pulled multiple / cancel scale / window perturbations do not touch the path rule). Sign rule: benefit keeps sign and >= 50% of nominal in >= 80% of the 7 runs; fragile cut = absent or moves > 10 s under an input offset.
* Tier 1 (exact engine, whole history, 43 months, 11 finalists x 43 = 473 runs): top Tier S by S=min(L6M,PRE) passing drawdown first, <= 2 per (elig, req, scope, mode) [F04-F08, F09, F10, F11 addto] plus the placebo/family-clean KB cells outside the S ranking [F01-F03]. 11 of the 40 allowed (compute). B3 against A's finalists NOT run: A published no finalist list; the fallback (ALONE vs ADDTO) is what is reported.

## Table 1 - Tier 1 finalists on the exact engine (stack $/week delta vs HOLD, carrying week dropped, windows L1M L2M L3M L6M HOLD MID PRE X')
_cut-input agreement with live: 14% at 0% false (best FIT-selected convention) / literal reading 45 of 92 within +-2 s with 23 false; engine Gate 0 NOT passed; PRE-PROOF_

| id | cell | scope | mode | LossExits | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | DD first (L6M,PRE) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| F01 | elig40 req3 mom15/8 stall30/2 eff30<0.40 f10 | KB | alone | 149 | -2944 | +3594 | +530 | -37 | +427 | +660 | +1543 | -485 | NO |
| F02 | elig40 req3 mom15/8 stall60/2 eff30<0.40 f10 | KB | alone | 114 | -2976 | +3594 | +566 | -150 | +376 | +629 | +1585 | -492 | NO |
| F03 | elig30 req3 mom15/8 stall90/2 eff30<0.30 f10 | KB | alone | 122 | -3130 | +3409 | +530 | +164 | +390 | +783 | +1122 | -592 | NO |
| F04 | elig40 req3 mom60/3 stall30/2 eff30<0.30 f1 | PE | alone | 2152 | -7987 | -2337 | -1449 | +1262 | -728 | -3755 | +4420 | -224 | yes |
| F05 | elig40 req3 mom60/3 stall30/4 eff60<0.40 f10 | PE | alone | 2156 | -4557 | -5476 | +1717 | +1852 | +742 | -279 | +2291 | +90 | NO |
| F06 | elig15 req3 mom15/8 stall30/2 eff30<0.30 f1 | pooled | alone | 3836 | -11804 | -8976 | -2523 | -4008 | -6454 | -11400 | +2895 | -2325 | NO |
| F07 | elig40 req3 mom60/5 stall30/4 eff60<0.40 f1 | pooled | alone | 9360 | +1182 | +1129 | +2763 | +2569 | +3289 | -941 | +5219 | -2926 | yes |
| F08 | elig10 req3 mom60/8 stall30/2 eff30<0.40 f10 | PE | alone | 1622 | -7970 | +2064 | +3160 | +643 | -1783 | -8767 | +1866 | -2880 | yes |
| F09 | elig15 req3 mom15/8 stall90/6 eff60<0.40 f10 | KB | alone | 1348 | +229 | +673 | -1526 | +38 | +1348 | +2855 | +979 | -728 | NO |
| F10 | elig20 req3 mom15/8 stall30/6 eff60<0.40 f10 | KB | alone | 1430 | +1298 | +2552 | +2166 | +911 | +1355 | +1003 | +1608 | -440 | NO |
| F11 | elig40 req2 mom15/5 stall30/2 eff30<0.30 f10 | PE | addto | 721 | -1716 | +586 | -284 | +893 | +2801 | +4167 | +484 | -972 | NO |

Table 1b nodrop (carrying week kept) L6M / PRE: F01 +1252/+1194; F02 +1144/+1235; F03 +1483/+1393; F04 -6/+3767; F05 +3018/+3030; F06 -1164/+3820; F07 +4019/+6390; F08 +2634/+1013; F09 +1425/+1221; F10 +2026/+1399; F11 +1810/+889

## Table 2 - the same finalists in Tier S (S = min(L6M,PRE), tests)
_cut-input agreement with live: 14% at 0% false (best FIT-selected convention) / literal reading 45 of 92 within +-2 s with 23 false; engine Gate 0 NOT passed; PRE-PROOF_

| id | S $/wk | placebo p | family p | WF (scope, $) vs random mean | alpha 1 / .14 / 0 S | PS runs ok /7 | sign stable over alpha | fragile cuts (n share, $ share) | robust-only same sign >=50% | Tier S L1M..X' |
|--|--|--|--|--|--|--|--|--|--|--|
| F01 | +954 | 0.010 | 0.010 | +121480 vs -26635 | +954 / +39 / +0 | 3 | True | 0.99, 0.70 | False | -3171 +129 -18 +955 +621 +479 +1242 -571 |
| F02 | +924 | 0.010 | 0.010 | +121480 vs -26635 | +924 / +9 / +23 | 3 | True | 0.99, -2.67 | True | -3171 +129 -30 +924 +593 +465 +1265 -598 |
| F03 | +805 | 0.025 | 0.806 | +121480 vs -26635 | +805 / +16 / -33 | 3 | False | 0.99, n/a | False | -3235 +39 -85 +806 +468 +282 +1242 -602 |
| F04 | +2353 | 1.000 | 1.000 | +92 vs -256564 | +2353 / +1506 / +1214 | 6 | True | 0.30, 0.03 | True | -53 +1058 +2814 +2354 +2156 +5093 +2661 -1629 |
| F05 | +2494 | 1.000 | 1.000 | +92 vs -256564 | +2494 / +985 / +563 | 3 | True | 0.87, 0.60 | False | +1751 +488 +2388 +2494 +784 +2081 +3105 -1247 |
| F06 | +2857 | 1.000 | 1.000 | +284417 vs -400532 | +2857 / +370 / -431 | 4 | False | 0.33, -23.47 | True | -4066 +10769 +10282 +2857 +846 -11694 +4722 -2817 |
| F07 | +4308 | 1.000 | 1.000 | +284417 vs -400532 | +4308 / +71 / -730 | 4 | False | 0.26, 1.08 | False | +345 +1612 +3570 +4362 +3190 +2651 +4309 -1973 |
| F08 | +1920 | 1.000 | 1.000 | +92 vs -256564 | +1920 / +1082 / +767 | 5 | True | 0.92, 1.53 | False | -1799 +472 +336 +1920 -632 -5014 +1977 -1016 |
| F09 | +1351 | 1.000 | 1.000 | +121480 vs -26635 | +1351 / +361 / +183 | 5 | True | 0.86, 0.78 | False | -1376 +213 +682 +1487 +1081 +2300 +1351 -7 |
| F10 | +1176 | 1.000 | 1.000 | +121480 vs -26635 | +1176 / +267 / +68 | 4 | True | 0.88, 0.69 | False | -167 +858 +897 +1176 +877 +2821 +1252 -503 |
| F11 | +1095 | 1.000 | 1.000 | -100552 vs -368894 | +1095 / -766 / -993 | 5 | False | 0.89, 0.82 | False | -911 +1603 +2378 +2592 +1522 +356 +1095 -277 |

## Verdicts (policy_rules.enters with Tier S p-values and walk-forward; every one is a no)
* F01: enters=False (engine recent_pass=False tolerant=True drawdown_first=False; placebo p 0.010, family p 0.010).
* F02: enters=False (engine recent_pass=False tolerant=True drawdown_first=False; placebo p 0.010, family p 0.010).
* F03: enters=False (engine recent_pass=False tolerant=True drawdown_first=False; placebo p 0.025, family p 0.806).
* F04: enters=False (engine recent_pass=False tolerant=True drawdown_first=True; placebo p 1.000, family p 1.000).
* F05: enters=False (engine recent_pass=False tolerant=True drawdown_first=False; placebo p 1.000, family p 1.000).
* F06: enters=False (engine recent_pass=False tolerant=True drawdown_first=False; placebo p 1.000, family p 1.000).
* F07: enters=False (engine recent_pass=True tolerant=False drawdown_first=True; placebo p 1.000, family p 1.000).
* F08: enters=False (engine recent_pass=False tolerant=True drawdown_first=True; placebo p 1.000, family p 1.000).
* F09: enters=False (engine recent_pass=False tolerant=True drawdown_first=False; placebo p 1.000, family p 1.000).
* F10: enters=False (engine recent_pass=True tolerant=True drawdown_first=False; placebo p 1.000, family p 1.000).
* F11: enters=False (engine recent_pass=False tolerant=True drawdown_first=False; placebo p 1.000, family p 1.000).

## B2 - the 18 THL_BOOKS cells re-scored (Tier S, S and windows $/wk vs HOLD)
_cut-input agreement with live: 14% at 0% false (best FIT-selected convention) / literal reading 45 of 92 within +-2 s with 23 false; engine Gate 0 NOT passed; PRE-PROOF_

| cell | mode | cuts | S | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|--|--|--|--|--|--|--|--|--|--|--|--|
| KB_TH_LIVE | alone | 5215 | -230 | -2996 | +870 | +460 | -230 | -1133 | -3889 | +52 | +54 |
| KB_MAE15 | alone | 6788 | -1036 | -3896 | +1114 | +476 | -1036 | -1557 | -2716 | -923 | +184 |
| SM_TH_LIVE | alone | 888 | -969 | -1681 | -307 | -227 | -969 | -226 | -28 | -732 | +252 |
| SM_MAE15 | alone | 1134 | -2104 | -1647 | -637 | -1123 | -2105 | -1290 | -855 | +302 | -402 |
| PE_TH_LIVE | alone | 3580 | -2544 | -3576 | -5489 | -1012 | -1485 | -3028 | +519 | -2545 | +3217 |
| PE_MAE15 | alone | 4686 | -9944 | +2790 | -1011 | -2192 | -9945 | -9361 | -7663 | -7165 | +545 |
| MV_TH_LIVE | alone | 3007 | -641 | +475 | -12 | +1362 | +752 | +27 | -1227 | -642 | +16 |
| MV_MAE15 | alone | 3859 | -522 | +610 | +781 | -222 | +653 | -570 | -2888 | -523 | -55 |
| KB_TH_LIVE | addto | 5215 | -546 | -2601 | +273 | -255 | -546 | -1282 | -3458 | -124 | +208 |
| KB_MAE15 | addto | 6788 | -1036 | -3896 | +1114 | +476 | -1036 | -1557 | -2716 | -923 | +184 |
| SM_TH_LIVE | addto | 888 | -1103 | -1339 | -481 | -373 | -1104 | -269 | +361 | -235 | -41 |
| SM_MAE15 | addto | 1134 | -2104 | -1647 | -637 | -1123 | -2105 | -1290 | -855 | +302 | -402 |
| PE_TH_LIVE | addto | 3580 | -3134 | -676 | -3816 | -342 | -2014 | -2906 | +922 | -3135 | +4532 |
| PE_MAE15 | addto | 4686 | -9945 | +2790 | -1014 | -2195 | -9946 | -9359 | -7647 | -7139 | +568 |
| MV_TH_LIVE | addto | 3007 | -546 | +925 | +455 | +1293 | +611 | -27 | -1705 | -546 | -266 |
| MV_MAE15 | addto | 3859 | -526 | +610 | +781 | -222 | +653 | -570 | -2888 | -526 | -55 |

Mapped 8 of 18 (KB, SM, PE, MV x TH_LIVE, MAE15). UNMAPPED 10: KB_TIME_ONLY, SM_TIME_ONLY, PE_TIME_ONLY, MV_TIME_ONLY (count-matched random-exit placebo, not a rule; the placebo worlds of Tier S play that role), MA_TH_LIVE, MA_MAE15, MA_TIME_ONLY, DN_TH_LIVE, DN_MAE15, DN_TIME_ONLY (the replica has no MA or DN book). The published 960-cell screen / 0-of-4,800 re-read on the proven engine: not done (no proven engine).

## Stage-1 counts
ALONE: pooled cells with S>0 1944 of 14,580, best pooled S +4373 $/wk, unit-cells screened 87480, min pooled family p 1.000. ADDTO: pooled S>0 1700, best pooled S +720, min pooled family p 0.313 (no ADDTO cell is family-clean). Live HOLD total in range (14 units) +1808718, NO-CUT natural +2228360 (the replica's L2 cut costs money over the 3.7 years against natural exits; this is the A-side question and is why ALONE looks good).
48 ALONE unit-cells have placebo p <= .10 (36 are PE with negative S, 8 KB positive); family p <= .10: only the 4 KB cells (identical pairs, req 3 = req 4) with p .0099.

## Caveats (all PRE-PROOF)
* Cut input: B alone does not use the L2 cut input at all; every L2-dependent statement (HOLD baseline, ADDTO) inherits the 14% / 0% false and 45-of-92 / 23-false label above. FIT conventions were not re-run over history (they exist for the blind week only): bracketed by alpha.
* Month chunks restart flat; history config is the settled D7 week; 100-ms causal book; Gate 0 not passed.
* One engine run per finalist (no 9-phase lock ladder on this engine); 11 finalists, not 40.
* Files: code/th_redo/thB_rec.py, thB_core.py, thB_stage1.py, thB_select.py, thB_fin.py, thB_engine_score.py; private /mnt/l2/l2vast/_th_redo_replica/B/ (hist, out, fin).


## Addendum (B3, run by TH-A on the lead's order, 2026-11-08)
**cut-input agreement with live: 14% at 0% false (best FIT-selected convention) / literal reading 45 of 92 within +-2 s with 23 false cuts; engine Gate 0 NOT passed; PRE-PROOF**

B3 was not run in the first B pass because A had no list. Now run: B finalists F07 and F10 (B's rule dicts, fin.json) merged with A's P05, P06, P07, P11, P24 (AddToPath, rules_replica.merge_rules), full replica, 12 recent months then 43 for the 7 survivors. Result in plain words: F10 + an A rule (KB scope) is positive on all recent windows and PRE/X', best B3_F10_P11 (L6M +3,188, PRE +190 USD/week, drawdown-first and tolerant gate met, L6M above its MDE 2,686, PRE below MDE); F07 stacks fail drawdown-first. No placebo/family/convention null exists for the stack and F10 alone has Tier S placebo p 1.0, so it is a lead, not a rule. Table and details: autopilot/DS3_TH_REDO_A.md, Addendum 3. Cells: /mnt/l2/l2vast/_th_redo_replica/out/fin3.json; results B3_finalists.csv.
