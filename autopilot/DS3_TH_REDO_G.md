> **VOID — engine failed Gate 0.** (user order 2026-11-08 15:00Z: this page is WITHDRAWN as a finding; the engine reproduces the live cut at 14% strict agreement and cannot rank cut rules, including "the live cell stays". No TH ranking from this page may be quoted. Original content below, unchanged. Backup: /mnt/l2/l2vast/_th_void_backup/)

# DS3_TH_REDO_G - program G, learned TH rule, REPLICA engine, 2023-04..2026-10 (TH-G)
**cut-input agreement with live: 14% at 0% false (best FIT-selected convention) / literal reading 45 of 92 within +-2 s with 23 false; engine Gate 0 NOT passed; PRE-PROOF**

No PASS claim. Research only. Private tree /mnt/l2/l2vast/_th_redo_replica/G/ (rows/, out/, fin/, logs/). Code code/th_redo/thG_{rec,data,fit,stats,final,fin,engine_score}.py (shas in DECISIONS.md; thG_final.py gained the fragile() function after the sha line, selection code unchanged). Seal manifest ds3_all_ea/manifest_after.json sha 759f2258daac9d28... before and after. Prereg G addendum-1 sha 641dbb4d..., adoption fb6d42b6; dead_lookup before (no replica learned-TH rows), 12 cells appended (THG_REPLICA_PREPROOF).

## 1. Result
No learned rule qualifies. The best hand rule from E does not exist (A, B, C, D found nothing), so the comparison is the live rule (HOLD, L2 cut at the live cell). 432 candidates (6 books x loss/profit side x h 30/60/120 s x tree/shallow GBDT x 3 seeds x 2 exit rates). The predictable part of "hold h more seconds minus exit now" is very small: for typical (book, side) the lowest 5% of predictions realise y = +0.9 pt against +0.8 pt overall (exit cost 0.8 pt). Best purged-CV statistic Z_S = min(z_L6M, z_PRE) = 1.72 (SM loss); the shuffled-label family null (W=12) has median max 1.10, 95th pct 1.86, max 2.22, so the smallest family p over all 432 is 0.154 and none reaches 0.10. Nothing goes to MORNING.md.

On the exact replica (12 finalists, 43 months) seven finalists (G01, G02, G03, G04, G06, G08, G10) are nominally positive on both L6M and PRE, but by $3-270 per week with 47-590 exits, small against the live stack; G01/G03/G06/G08 also pass recent pass, tolerant gate and drawdown first and are placebo-clean (random exits of the same count are far worse), yet each fails the family gate (p 0.15 or worse) and G03/G08 fire on 58 trades. They are LEADS at most, not rules. Loss-side deltas on L1M are negative for the larger ones (G02 -3.1k, G07 -3.8k).

## 2. Method (deviations stated)
* Rows: HOLD world of the replica per month chunk (10 warm-up days, engine flat at month start), rules_replica record=True, 32 L1+L2 features per open book every 5th wall second (stated subsample of "every evaluation second"; 16.0 M rows in the 14 live units, 23,788 trades).
* Label (future path only): y_h = pts(t+h) - (pts(t) - 0.8) on the same trade's realised later rows, or the realised exit if the trade closes within h; features are the row at t. Side loss = unrealised < 0, profit = >= 0.
* Learners: tree (<= 6 leaves) and GBDT (depth 3, 50 iterations), 120k-row training subsample per fit, 3 seeds. GP learner NOT run. Monotone sign constraints NOT applied. Rule: exit (market) when predicted y < c, c = min(0, training-prediction quantile at row fire rate 0.3% / 0.1%). The first draft threshold (q-quantile of |y|, 0.7/0.85) never fired and was replaced before any rule score was read.
* Validation: purged blocked CV by month (6 folds, 5-day purge, max hold 4.04 d) gives every window out of sample; purged walk-forward (24 months, quarterly refit, 2025-04 onward) is the causal check for L1M..L6M/HOLD/MID. PRE and X' are only CV (trained partly on later data). Engine models: CV fold model before 2025-04, walk-forward model from 2025-04.
* Nulls: family = label-shifted worlds (W=12, not 200), statistic max Z_S over the 432; random-exit placebo with the same exit count, 1,000 draws. Tier S has no re-entry cascade and overstates large (e.g. G05 +172k Tier S vs +0.3k/wk on the engine).
* Engine: RuleG (AddToPath, live L2 cut kept), 12 finalists x 43 months = 516 replays; HOLD = recorder run (G03 reproduces HOLD exactly where it never fires). Finalists chosen by a frozen rule before any engine number (DECISIONS.md).
* Not run: the exact-engine perturbation set (pulled multiple, cancel scale, window) and the FIT convention set; history carries only the literal reading. Substitute: Tier S timing-fragility proxy (exit moved -5/+5/+10 s). Fragile-$ share above the 30% cap: G04 (0.47), G07 (0.85; robust-only fails the 50% rule).

## 3. Table 1 - finalists on the exact engine ($/week stack delta vs HOLD, carrying week dropped)
_cut-input agreement with live: 14% at 0% false (best FIT-selected convention) / literal reading 45 of 92 within +-2 s with 23 false; engine Gate 0 NOT passed; PRE-PROOF_
| id | book side h learner seed rate | exits | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | L6M nodrop | PRE nodrop | DD first | recent | tolerant | enters |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| G01 | SM loss h60 gbdt s0 r0.001 | 79 | -239 | +366 | +36 | +234 | -311 | -514 | +32 | -195 | +39 | -43 | True | True | True | False |
| G02 | PE loss h60 gbdt s2 r0.001 | 590 | -3078 | +324 | +496 | +272 | +229 | +68 | +24 | +7 | -485 | +769 | False | True | True | False |
| G03 | HM loss h120 gbdt s0 r0.001 | 58 | +0 | +30 | +129 | +85 | +77 | +11 | +31 | +9 | +34 | +4 | True | True | True | False |
| G04 | MV loss h120 gbdt s1 r0.001 | 240 | -706 | -211 | -263 | +92 | -126 | -265 | +84 | +0 | -84 | +156 | True | False | True | False |
| G05 | PE profit h120 gbdt s2 r0.001 | 755 | +5817 | -403 | +162 | +298 | +731 | -3200 | -624 | -89 | -770 | -865 | True | True | True | False |
| G06 | KB loss h120 gbdt s1 r0.001 | 587 | -147 | +534 | +256 | +22 | -27 | -331 | +106 | -30 | +320 | +235 | True | True | True | False |
| G07 | PE loss h120 gbdt s2 r0.001 | 491 | -3847 | +1262 | +1350 | -233 | -1057 | -3566 | -143 | +0 | -1096 | +320 | False | False | True | False |
| G08 | HM loss h60 gbdt s2 r0.001 | 58 | +0 | +94 | +62 | +78 | +21 | +0 | +46 | +87 | +28 | +4 | True | True | True | False |
| G09 | PE profit h120 gbdt s1 r0.003 | 2029 | -3579 | -2931 | +314 | -2749 | -2739 | +493 | -406 | -856 | -3847 | +215 | True | False | False | False |
| G10 | SM loss h120 gbdt s0 r0.001 | 47 | +927 | -116 | -20 | +82 | -386 | -25 | +3 | +36 | -144 | -134 | False | False | True | False |
| G11 | MV profit h120 gbdt s2 r0.001 | 415 | +463 | -257 | -260 | +4 | +44 | +610 | -40 | +81 | -158 | -169 | False | False | True | False |
| G12 | PB loss h120 gbdt s0 r0.001 | 60 | -24 | +0 | -25 | -60 | +1 | -28 | +19 | +0 | +88 | -21 | False | False | True | False |

## 4. Table 2 - Tier S tests and fragility proxy
_cut-input agreement with live: 14% at 0% false (best FIT-selected convention) / literal reading 45 of 92 within +-2 s with 23 false; engine Gate 0 NOT passed; PRE-PROOF_
(p_family column of the last run is in section 1: all finalists >= 0.154, G01 = 0.154.)
| id | TierS Z_S | p_family(W=12) | placebo p (1000) | WF L6M $/wk (TierS) | fragile cuts n/share$ | robust-only same sign>=50% | Tier S CV benefit total $ |
|--|--|--|--|--|--|--|--|
| G01 | 1.72 | >=0.154 | 0.005 | +351 | 0/51, -0.00 | True | -12622 |
| G02 | 1.53 | >=0.154 | 0.001 | +93 | 24/539, 0.12 | True | +35458 |
| G03 | 1.18 | >=0.154 | 0.001 | +82 | 4/60, -1.68 | True | -178 |
| G04 | 0.97 | >=0.154 | 0.001 | +10 | 32/314, 0.47 | True | +15629 |
| G05 | 0.85 | >=0.154 | 0.988 | -175 | 8/763, -0.05 | True | +171863 |
| G06 | 0.76 | >=0.154 | 0.001 | -239 | 22/495, 0.26 | True | +10629 |
| G07 | 0.73 | >=0.154 | 0.001 | +232 | 33/519, 0.85 | False | +13432 |
| G08 | 0.69 | >=0.154 | 0.015 | +80 | 8/63, -0.41 | True | -1561 |
| G09 | 0.61 | >=0.154 | 1.000 | +4969 | 15/1616, -0.16 | True | -98074 |
| G10 | 0.50 | >=0.154 | 0.023 | +99 | 2/45, -0.02 | True | -19405 |
| G11 | 0.36 | >=0.154 | 0.956 | -206 | 6/279, -0.07 | True | +25503 |
| G12 | 0.06 | >=0.154 | 0.013 | +217 | 3/66, -0.05 | True | -5701 |

## 5. Feature importance per book (tree impurity, mean over 36 tree fits per book; GBDT permutation on fold 2, h=60, seed 0)
* KB: tree atr5 .23, pulled_mult15 .11, elapsed_s .08, pulled_mult2 .07, med_level .06; GBDT mae, sec_since_mae, mom60, elapsed_s, delta10.
* PE: atr5 .21, pulled_mult15 .10, med_level .09, pulled_mult5 .07, elapsed_s .07; GBDT med_level, recov_pts, sec_since_mfe, delta10, mfe.
* SM: atr5 .22, pulled_mult15 .14, elapsed_s .08, pulled_mult5 .08, sec_since_mae .05; GBDT elapsed_s, mfe, atr5, ahead_rel, pulled_mult5.
* HM: atr5 .27, pulled_mult15 .10, med_level .10, elapsed_s .06, pulled5 .05; GBDT pulled_mult2, sec_since_mae, pct_stp, ahead_rel, pull_pts.
* MV: atr5 .35, pulled_mult15 .09, med_level .08, sec_since_mae .05, pulled_mult5 .05; GBDT pull_pts, elapsed_s, med_level, mae, mom30.
* PB: atr5 .16, pulled_mult15 .12, mom60 .12, sec_since_mfe .11, med_level .09; GBDT atr5, sec_since_mae, sec_since_mfe, mom30, eff120.
Across books the trees split first on volatility (atr5), long-window pulled support and elapsed time: regime and clock variables, not an event signature; the importance is of fit to a tiny signal, not evidence of one.

## 6. Policy-line sentence
No learned rule beats the live rule: policy file unchanged (loss side stays the live L2 cut, profit side empty).
