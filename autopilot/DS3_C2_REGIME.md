# DS3_C2_REGIME - T-NEXT C2: the 2025 trend-regime loss of JN04 / JP07 (SZ-CDE, 2026-11-11 11:25Z)

> **TESTING DEFECT FOUND AND FIXED (SZ-CDE own, 2026-11-11 00:4xZ): the first rule-mode leave-one-out (JN04LPB_C2_RM_*) was launched with the rbjobs launcher, which does not apply the rule-mode hooks (jnrule LOT/SIGQ/REG, cde STACK); minus LOT / SIGQ / REG / STACK came out IDENTICAL to the dollar in all windows, the identical-to-the-dollar test. All 154 cell-months are void (runs_rf_void_cde) and the sets are re-run with jbjobs (JointRep); section B2 fills as the re-run lands. SECOND DEFECT (2026-11-11 03:3xZ): the jbjobs re-run, with 7 rule-mode sets per month in ONE batch, still gave identical minus-LOT / SIGQ / REG rows: later sets in a rule-mode batch inherit the first set's jnrule behaviour (proved by mlog multiplier counts and a solo re-run); all batch results are void and the leave-one-out is re-run one set per job.**

> **CONVENTIONS (agreed with SZ-IJK 21:4xZ): d mean = weekly mean difference cell minus reference with the carrying week (largest |cell - reference| weekly delta) dropped, the sz_core / Z.score_daily convention; the all-weeks d mean is in brackets because a single week can move the carry-dropped number by several $k/wk (GAP has 17 weeks). maxDD / cuts on all weeks. Windows are calendar-month based here (GAP 202507-202510, H2-2024 202407-202412, HOLD 202511-202610, L6M 202605-202610), sz_core windows start on 2026-05-12 / 2025-11-10 (so L6M / HOLD d means differ from SZ-IJK by a week at the edge). Label: PRE-PROOF; post-hoc; Shadow only; no PASS claims. Exact engine ROLLFIX1 rows; mean $/wk = carrying week dropped (largest |cell - NEVER-CUT| week), the all-weeks mean is shown beside it because GAP has only 17 weeks. Leave-one-out rows are DIAGNOSTIC reference rows (standing rule: every layer stays ON). Prereg: autopilot/SZ_C2_PREREG.md (+ Addendum 1).**

## A. Leave-one-out on the S1b-COMB base (existing exact runs; reference = patched S1-COMB; d mean / cut vs S1-COMB)

| layer left out | GAP 2025-07..10: mean (all-weeks mean) / maxDD / d mean / cut | H2-2024: mean / maxDD / d mean / cut | HOLD: mean / maxDD / d mean / cut | L6M: mean / maxDD / d mean / cut |
|--|--|--|--|--|
| JN04 (all four layers) | 11919 (all 13865) / 70270 / -4296 (all-weeks -7148) / -1.2 | 18408 (all 15628) / 58316 / -9251 (all-weeks -7430) / +39.6 | 18007 (all 17331) / 54141 / -1485 (all-weeks -269) / +45.6 | 30592 (all 28709) / 45203 / +5062 (all-weeks +3301) / +43.4 |
| minus LOT (P7 Calmar gate) | 21751 (all 17533) / 58112 / -2259 (all-weeks -3479) / +16.3 | 17514 (all 16731) / 97046 / -5491 (all-weeks -6327) / -0.5 | 18817 (all 18264) / 61673 / -327 (all-weeks +664) / +38.0 | 29869 (all 27055) / 61673 / +3338 (all-weeks +1646) / +22.8 |
| minus SIGQ (dA gate) | 11911 (all 13801) / 62899 / -4304 (all-weeks -7211) / +9.4 | 19621 (all 16652) / 60540 / -8037 (all-weeks -6405) / +37.3 | 17825 (all 16878) / 54647 / -1634 (all-weeks -722) / +45.1 | 31048 (all 28587) / 44068 / +4931 (all-weeks +3179) / +44.9 |
| minus REG (P7 ATR regime) | 15894 (all 16020) / 73722 / -3239 (all-weeks -4993) / -6.2 | 21188 (all 18056) / 63377 / -3728 (all-weeks -5001) / +34.4 | 17629 (all 16812) / 61413 / -1954 (all-weeks -788) / +38.3 | 30470 (all 28289) / 61413 / +1729 (all-weeks +2880) / +23.1 |
| minus STACK (London same-side cap 6) | 12625 (all 14844) / 66621 / -3590 (all-weeks -6169) / +4.0 | 19692 (all 16750) / 59746 / -7966 (all-weeks -6307) / +38.1 | 16401 (all 15723) / 61984 / -3126 (all-weeks -1876) / +37.7 | 28196 (all 26342) / 52545 / -545 (all-weeks +934) / +34.2 |

## B. Leave-one-out on the LIVE-PANEL base (LPB: P7 day cap 8,400 + table 7,4,0,4,0,0 + P7 cut 40/5x/w5/p3); reference = LPB_BASE (SZ-CORE) / LPB_EMPTY; d mean / cut vs LPB_BASE

| layer left out | GAP 2025-07..10: mean (all-weeks mean) / maxDD / d mean / cut | H2-2024: mean / maxDD / d mean / cut | HOLD: mean / maxDD / d mean / cut | L6M: mean / maxDD / d mean / cut |
|--|--|--|--|--|
| LPB_JN04 (all four layers + base items) | 9935 (all 12229) / 54667 / -1235 (all-weeks -3098) / +14.0 | 16855 (all 14874) / 36624 / -1849 (all-weeks -2771) / +55.3 | 16084 (all 15759) / 72382 / +1164 (all-weeks +223) / +8.2 | 25256 (all 24225) / 72382 / +3324 (all-weeks +4780) / +6.3 |
| JN04RM (rule-mode JN04 on the live-panel base; the JN04 reference where it exists) | 16667 (all 13566) / 39147 / -160 (all-weeks -1761) / +38.4 | 17374 (all 15143) / 42854 / -1540 (all-weeks -2502) / +47.7 | 13213 (all 12627) / 72757 / -3658 (all-weeks -2908) / +7.7 | 20689 (all 19195) / 41699 / -1701 (all-weeks -249) / +46.0 |
| minus LOT | 9588 (all 12806) / 54166 / -1582 (all-weeks -2521) / +14.8 | months missing | months missing | months missing |
| minus SIGQ | 9791 (all 12093) / 57734 / -1379 (all-weeks -3234) / +9.1 | months missing | months missing | months missing |
| minus REG | months missing | months missing | months missing | months missing |
| minus STACK | months missing | months missing | months missing | months missing |
| minus table 7,4,0,4,0,0 (P7 table back to 7,7,0,7,0,0) | months missing | months missing | months missing | months missing |
| minus day cap (P7 loss cap back to 16,800) | months missing | months missing | months missing | months missing |
| minus P7 cut 40/5x/w5/p3 (back to the S1-COMB P7 cell) | months missing | months missing | months missing | months missing |

## B2. Leave-one-out in RULE MODE on the live-panel base (JN04RM = the live-form rule JN04: LOT Calmar gate, SIGQ dA gate, REG ATR gate inside the engine, STACK = London same-side cap 6); reference LPB_BASE; the faithful version of B (B is table mode)

| layer left out | GAP 2025-07..10: mean (all-weeks mean) / maxDD / d mean / cut | H2-2024: mean / maxDD / d mean / cut | HOLD: mean / maxDD / d mean / cut | L6M: mean / maxDD / d mean / cut |
|--|--|--|--|--|
| JN04RM (all four layers, rule mode) | 16667 (all 13566) / 39147 / -160 (all-weeks -1761) / +38.4 | 17374 (all 15143) / 42854 / -1540 (all-weeks -2502) / +47.7 | 13213 (all 12627) / 72757 / -3658 (all-weeks -2908) / +7.7 | 20689 (all 19195) / 41699 / -1701 (all-weeks -249) / +46.0 |
| minus LOT | 18519 (all 14957) / 45597 / -1447 (all-weeks -370) / +28.2 | 16987 (all 14822) / 59462 / -2046 (all-weeks -2823) / +27.5 | 15521 (all 15410) / 94681 / -761 (all-weeks -125) / -20.1 | 23188 (all 22655) / 60603 / +2231 (all-weeks +3210) / +21.5 |
| minus SIGQ | 16132 (all 13057) / 39219 / -699 (all-weeks -2270) / +38.3 | 17487 (all 15112) / 47621 / -1840 (all-weeks -2534) / +41.9 | 11376 (all 12428) / 76223 / -2601 (all-weeks -3107) / +3.3 | 16308 (all 18257) / 42691 / -246 (all-weeks -1188) / +44.7 |
| minus REG | 18271 (all 14655) / 46819 / -2166 (all-weeks -672) / +26.3 | 18987 (all 16578) / 46053 / +20 (all-weeks -1067) / +43.8 | 13139 (all 12968) / 70373 / -3681 (all-weeks -2567) / +10.7 | 19962 (all 19341) / 51586 / -2321 (all-weeks -104) / +33.2 |
| minus STACK | 11506 (all 14033) / 43081 / +336 (all-weeks -1294) / +32.2 | 18305 (all 16057) / 42390 / -2684 (all-weeks -1588) / +48.3 | 13474 (all 12812) / 71587 / -3397 (all-weeks -2723) / +9.2 | 20769 (all 19128) / 51246 / -1621 (all-weeks -316) / +33.6 |
| minus table 7,4,0,4,0,0 | 10399 (all 13298) / 53044 / -771 (all-weeks -2029) / +16.5 | 17946 (all 15596) / 45520 / -965 (all-weeks -2050) / +44.5 | 14004 (all 13263) / 65426 / -2867 (all-weeks -2272) / +17.0 | 20979 (all 19189) / 51225 / -1412 (all-weeks -256) / +33.7 |
| minus day cap (P7 loss cap 16,800) | 16787 (all 13679) / 39147 / -111 (all-weeks -1648) / +38.4 | 17250 (all 15024) / 42854 / -1665 (all-weeks -2621) / +47.7 | 13911 (all 13311) / 72757 / -2960 (all-weeks -2224) / +7.7 | 21721 (all 20186) / 42604 / -669 (all-weeks +741) / +44.8 |
| minus P7 cut 40/5x/w5/p3 | 17634 (all 14611) / 36790 / +903 (all-weeks -716) / +42.1 | 17059 (all 14642) / 48198 / -2076 (all-weeks -3003) / +41.2 | 12514 (all 11437) / 76284 / -3491 (all-weeks -4098) / +3.2 | 21085 (all 18545) / 45378 / +498 (all-weeks -899) / +41.2 |

## F. Reading of the rule-mode leave-one-out (change when the layer is left OUT, relative to JN04RM; cuts in percentage points, d mean in $/wk all-weeks)

| layer left out | GAP all-weeks d mean change | GAP cut change | H2-2024 cut change | HOLD cut change | L6M cut change | reading |
|--|--|--|--|--|--|--|
| LOT (P7 Calmar gate) | +1391 | -10.2 | -20.3 | -27.8 | -24.5 | removing it improves the GAP all-weeks mean by 1391 $/wk and changes the L6M / HOLD cut by -24.5 / -27.8 points: the layer buys recents protection at a GAP mean cost |
| SIGQ (dA gate) | -509 | -0.1 | -5.8 | -4.4 | -1.3 | removing it changes the GAP mean by -509 $/wk, L6M cut by -1.3, HOLD cut by -4.4 points |
| REG (P7 ATR gate) | +1088 | -12.1 | -3.9 | +3.0 | -12.8 | removing it improves the GAP all-weeks mean by 1088 $/wk and changes the L6M / HOLD cut by -12.8 / 3.0 points: the layer buys recents protection at a GAP mean cost |
| STACK (London cap 6) | +467 | -6.2 | +0.6 | +1.5 | -12.4 | removing it improves the GAP all-weeks mean by 467 $/wk and changes the L6M / HOLD cut by -12.4 / 1.5 points: the layer buys recents protection at a GAP mean cost |
| 7/4/4 table | -268 | -21.9 | -3.3 | +9.3 | -12.3 | removing it changes the GAP mean by -268 $/wk, L6M cut by -12.3, HOLD cut by 9.3 points |
| day cap 8,400 | +113 | +0.0 | -0.0 | +0.0 | -1.2 | removing it changes the GAP mean by 113 $/wk and the L6M / HOLD cut by -1.2 / 0.0 points: little effect |
| P7 cut 40/5x/w5/p3 | +1044 | +3.7 | -6.5 | -4.5 | -4.8 | removing it improves the GAP all-weeks mean by 1044 $/wk and changes the L6M / HOLD cut by -4.8 / -4.5 points: the layer buys recents protection at a GAP mean cost |


## C. Where does the LOT gate cost money? (S1b exact runs JN04 vs JD01, P7 signals, split by the regime flags; flags are causal at the signal second)

| window | flag | flag value | P7 signals | LOT effect (JN04 - JD01) $ | JN04 P7 $ | JD01 P7 $ |
|--|--|--|--|--|--|--|
| GAP | F_ER | True | 29 | -1465 | +3077 | +4542 |
| GAP | F_ER | False | 401 | -66489 | +100891 | +167380 |
| GAP | F_ER2 | True | 62 | +11652 | +42 | -11610 |
| GAP | F_ER2 | False | 368 | -79607 | +103926 | +183532 |
| GAP | F_PRIOR | True | 162 | -8687 | +51120 | +59807 |
| GAP | F_PRIOR | False | 268 | -59268 | +52848 | +112115 |
| H2-2024 | F_ER | True | 49 | +1612 | +39543 | +37931 |
| H2-2024 | F_ER | False | 699 | -31398 | +62574 | +93972 |
| H2-2024 | F_ER2 | True | 99 | +1673 | +92912 | +91239 |
| H2-2024 | F_ER2 | False | 649 | -31459 | +9205 | +40664 |
| H2-2024 | F_PRIOR | True | 278 | +4100 | +67662 | +63562 |
| H2-2024 | F_PRIOR | False | 470 | -33886 | +34455 | +68341 |
| HOLD | F_ER | True | 220 | -23358 | +142940 | +166298 |
| HOLD | F_ER | False | 2281 | -24611 | +487895 | +512506 |
| HOLD | F_ER2 | True | 334 | -11184 | +156220 | +167404 |
| HOLD | F_ER2 | False | 2167 | -36785 | +474615 | +511400 |
| HOLD | F_PRIOR | True | 894 | -1466 | +258108 | +259574 |
| HOLD | F_PRIOR | False | 1607 | -46503 | +372727 | +419230 |

## D. Signal-level mixture screen (S1b, JD01 outcome where LOT is off, JN04 elsewhere; ranks candidates, not a verdict)

| candidate | GAP mean / maxDD | H2-2024 mean / maxDD | HOLD mean / maxDD | L6M mean / maxDD |
|--|--|--|--|--|
| JN04 (LOT on everywhere) | 11919 / 70270 | 18408 / 58316 | 18007 / 54141 | 30592 / 45203 |
| JD01 (LOT off everywhere) | 21751 / 58112 | 17514 / 97046 | 18817 / 61673 | 29869 / 61673 |
| LOT off when F_ER (trend day) | 12005 / 66024 | 18208 / 61321 | 18515 / 52728 | 30993 / 40481 |
| LOT off when F_ER2 (trend 6.5h) | 10951 / 73437 | 18340 / 67969 | 18315 / 53810 | 31176 / 41490 |
| LOT off when F_PRIOR (prior day trend) | 12122 / 64786 | 15627 / 76980 | 18517 / 64103 | 29785 / 60018 |
| LOT off when NOT F_ER | 21959 / 60436 | 17535 / 88930 | 18310 / 68944 | 29553 / 68944 |
| LOT off when NOT F_ER2 | 22377 / 53022 | 20139 / 99780 | 18602 / 66423 | 29460 / 66423 |
| LOT off when NOT F_PRIOR | 21302 / 61673 | 19447 / 91168 | 18908 / 57722 | 30631 / 57722 |

## E. Exact regime stacks on the live-panel base (43 months)


SZ-CDE C2 processes (IJK driver state_sizer_ijk rbjobs masters, 1 worker each (3 workers, about 10 GB per exact worker), memory gate 62 GB): c2_a=1362513 (not running), c2_b=1362514 (not running), c2_rsa=1167576 (not running), c2_rsb=1529462 (not running), jx_a=1596463, jx_b=1603451

| set | candidate | months | L1M / L3M / L6M cut vs LPB_BASE | L6M d mean | (b) eq-mean L6M cut | HOLD cut / d mean | PRE cut / d mean | X' cut / d mean | GAP cut / d mean | H2-2024 cut / d mean | WF vs live: beats % / OOS cut / d mean | WF vs JN04RM: beats % | Rule 2a label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| LPB_JN04 | LPB_JN04 (all four layers, always on, table mode) | 43 | +77.5 / +6.3 / +6.3 | +3324 | +26.2 | +8.2 / +1164 | +36.5 / -875 | +57.1 / +2352 | +14.0 / -1235 | +55.3 / -1849 | 81% / +27.2% / -1302 | n/a | OK-PRIOR (allow 16%, WF 81%) [old -1k rule: OK-PRIOR] |
| JN04RM | JN04RM (rule mode, the JN04 reference) | 43 | +47.2 / +46.0 / +46.0 | -1701 | +48.1 | +7.7 / -3658 | +32.9 / -1840 | +47.7 / -357 | +38.4 / -160 | +47.7 / -1540 | 90% / +26.9% / -2991 | 0% (cut +0.0%, d mean +0) | OK-PRIOR (allow 25%, WF 90%) [old -1k rule: RECENT-ONLY] |
| JN04LPB_C2_RS_FER | LOT off when F_ER (trend day, ER>=0.30) | 43 | +74.3 / +4.9 / +4.9 | +2923 | +23.8 | +6.8 / +1389 | +38.3 / -704 | +56.3 / +2399 | +11.2 / -1206 | +42.3 / -2033 | 82% / +26.1% / -1147 | 20% (cut -1.0%, d mean +1441) | OK-PRIOR (allow 15%, WF 82%) [old -1k rule: OK-PRIOR] |
| JN04LPB_C2_RS_NFER2 | LOT off when NOT F_ER2 (6.5 h ER<0.25) | 43 | +46.0 / +4.1 / +4.1 | +4283 | +30.5 | -14.1 / +777 | +35.3 / -247 | +28.2 / +1978 | +17.5 / -785 | +21.4 / -2914 | 65% / +9.6% / -1046 | 10% (cut -23.6%, d mean +569) | OK-PRIOR (allow 15%, WF 65%) [old -1k rule: OK-PRIOR] |
| JN04LPB_C2_RS_NFPRIOR | LOT off when NOT F_PRIOR (prior day trend<0.6) | 43 | +81.1 / +1.1 / +1.1 | +3726 | +24.7 | -9.3 / +31 | +33.6 / -47 | +44.1 / +2045 | +14.8 / -914 | +19.4 / -3909 | 70% / +13.4% / -1008 | 9% (cut +0.0%, d mean +434) | OK-PRIOR (allow 15%, WF 70%) [old -1k rule: OK-PRIOR] |

## G. Conclusion (C2; exact, rule-mode leave-one-out and table-mode regime stacks on the live-panel base; first-order screens in sections C and D; every number vs LPB_BASE unless stated)

1. **Which layer causes the 2025 loss?** None alone. In rule mode (the live form) JN04RM costs about $1.8k/wk (all-weeks) in GAP 2025-07..10 with a stack maxDD cut of +38.4%. The cost is spread over LOT (leaving it out improves the GAP mean by $1.4k/wk), REG ($1.1k) and the P7 cut ($1.0k); each of those layers also provides recents drawdown protection (L6M cut +5 to +25 points; HOLD cut +28 points for LOT). SIGQ and the day cap barely matter. The $7-9k/wk loss quoted in T-NEXT is on the S1b base (and a carry-week convention); on the live-panel base it is about 1.8k/wk (rule mode) or 3.1k/wk (table mode), all-weeks.
2. **Does a regime switch fix it?** No. Three causal regime flags switched LOT off (table mode, exact, 43 months): on trend days (F_ER) the stack is essentially LPB_JN04 (L6M cut +4.9 vs +6.3, HOLD +6.8 vs +8.2, GAP +11.2 vs +14.0, H2-2024 +42.3 vs +55.3); with LOT off when the 6.5 h ER is LOW (NFER2) or the previous day was not a trend day (NFPRIOR) the GAP mean improves by about $0.3-0.5k/wk but the HOLD cut turns negative (-14.1 / -9.3) and H2-2024 falls (+21.4 / +19.4). The bi-weekly WF against the JN04RM reference beats it in only 20% / 10% / 9% of periods; against live (LPB_BASE) the best is 82% (F_ER, the same as LPB_JN04). Label: none of the three stacks is a candidate (they do not beat JN04 at equal mean on HOLD and H2-2024; recents-only gains on L6M equal-mean for NFER2: +30.5 vs +26.2 are not confirmed by HOLD / WF).
3. **What goes to DS3_JOINT_2:** keep the four JN04 layers as they are; the GAP cost is the price of the recents protection and no per-regime LOT switch tested here removes it without losing HOLD / H2-2024. REFIT note: the bi-weekly procedure should keep LOT.
4. **Caveats:** two own testing defects (launcher without rule hooks; rule-mode batch leak) were found by the identical-to-the-dollar test, all affected rows are void and re-run (DECISIONS.md); regime stacks are table mode (the live LOT is day-based in rule mode, so a signal-level regime flag could not be expressed there); first-order screens C and D are not verdicts.

## H. LEAK AUDIT (rule-mode batch leak; 2026-11-11 08:3xZ, SZ-CDE; data: /mnt/l2/l2vast/_th_sz/cde/leak_audit_raw.csv, leak_audit_prefix.csv)
Method: for every rule-mode series in ijk/exact/runs_rf (31 sets carry a jnrule key, 24 have runs, 310 month-runs with mlog.parquet) (1) prefix test: a later set whose mlog.parquet starts with an earlier set's complete mlog of the same month ran in the same batch process and inherited its log (cumulative mlog); (2) layer-count test: mLOT / mSIGQ / mREG < 1 counts must agree with the set's own jnrule config; (3) solo re-runs (batch of 1) of suspect month-runs compared trade by trade.
| series | month-runs | status | evidence |
|--|--|--|--|
| JN04RM | 43 | CLEAN | no cumulative log; all three layers fire in 37 of 43 months |
| JN04LPB_C2_RM_{LOT,SIGQ,REG,STACK,TABLE,DAYCAP,CUT} (one set per job, 7 x 22) | 154 | CLEAN | no cumulative log; LOT-off / SIGQ-off / REG-off sets have mLOT / mSIGQ / mREG < 1 count 0 in all 22 months and the other layers fire in 22 of 22; the first rule-mode runs of these sets (rbjobs launcher, then jbjobs batch of 7) are VOID and moved to ijk/exact/runs_rf_void_cde (never deleted) |
| ZJ_SIGQNOKC_JN04RM | 29 | CLEAN | the only set whose jnrule behaviour differs from JN04RM (dA_exclude KC_up_4h); its log is not a prefix of any other set |
| ZJ_ZNA_* / ZJ_ZS_* (14 sets) 202605-202606 | 14 x 2 | CLEAN | non-cumulative logs |
| ZJ_ZNA_* / ZJ_ZS_* (14 sets) 202607-202610 | 12-ish of 14 per month | LOG VOID, TRADES CLEAN | cumulative mlog.parquet (do not use the logs); all sets in those batches have the IDENTICAL jnrule config, so the leak cannot change a multiplier; four solo re-runs are trade-identical to the batch run to the dollar: ZJ_ZNA_OPEN20 202608 (725 trades, +16,759), ZJ_ZS_D0 202608 (702, +43,212), ZJ_ZNA_COOL_A 202609 (711, +142,535), ZJ_ZNA_STOP_A 202610 (870, +35,696) |
| JX01-JX07 | 0 completed | NOTHING TO VOID, RE-RUN | the pre-compaction runs were deleted by SZ-IJK; JX01/202610 is an incomplete directory (no DONE). Re-run started ONE SET PER JOB (273 jobs, L6M then HOLD then PRE then X-prime), 2 masters x 1 worker, MemAvail gate 62 GB (SZ-CORE queue cannot launch IJK-driver sets, the IJK driver is run directly) |
Hook-class parity checks (2026-11-11 08:3xZ, solo re-run of one month 202608 via sz_exact.py batch, trades compared on book/lots/entry_ns/exit_ns/net_fee/exit_name): PTR_M7_01 (profit M7 sweep_against take; 40-set batch, 778 trades, net 69,093) IDENTICAL; PTR_K7_01 (profit K7 dd lock; same batch as M7_01, different profit line, 743 trades, net 81,740) IDENTICAL; R5_BO_3 (r5_hooks bo cutstop block; multi-set R5/R12 batch, 670 trades, net 10,145) IDENTICAL. Verdict CLEAN for PTR, R5/R7 hook classes (one month each; entry-hook class not separately checked). Logs: /mnt/l2/l2vast/_th_sz/cde/parity_hooks.log; solo copies *_T in exact_b/runs. Together with the zone-hook ZJ checks this is supporting evidence of no cross-set leak. SZ-IJK's run_batch now forks one child per set (fix not yet tested on a batch month by him; I tested one-set-per-job only). DS3_JOINT_2 should use only the CLEAN rows and the trade-clean ZJ rows (not their mlog files).
