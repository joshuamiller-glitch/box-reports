# DS3_C2_REGIME - T-NEXT C2: the 2025 trend-regime loss of JN04 / JP07 (SZ-CDE, 2026-11-11 02:24Z)

> **TESTING DEFECT FOUND AND FIXED (SZ-CDE own, 2026-11-11 00:4xZ): the first rule-mode leave-one-out (JN04LPB_C2_RM_*) was launched with the rbjobs launcher, which does not apply the rule-mode hooks (jnrule LOT/SIGQ/REG, cde STACK); minus LOT / SIGQ / REG / STACK came out IDENTICAL to the dollar in all windows, the identical-to-the-dollar test. All 154 cell-months are void (runs_rf_void_cde) and the sets are re-run with jbjobs (JointRep); section B2 fills as the re-run lands.**

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
| minus LOT | 18519 (all 14957) / 45597 / -1447 (all-weeks -370) / +28.2 | 16987 (all 14822) / 59462 / -2046 (all-weeks -2823) / +27.5 | months missing | months missing |
| minus SIGQ | 18519 (all 14957) / 45597 / -1447 (all-weeks -370) / +28.2 | 16987 (all 14822) / 59462 / -2046 (all-weeks -2823) / +27.5 | months missing | months missing |
| minus REG | 18519 (all 14957) / 45597 / -1447 (all-weeks -370) / +28.2 | 16987 (all 14822) / 59462 / -2046 (all-weeks -2823) / +27.5 | months missing | months missing |
| minus STACK | 19711 (all 16055) / 46099 / -255 (all-weeks +728) / +27.4 | 18821 (all 16456) / 54544 / -418 (all-weeks -1189) / +33.5 | months missing | months missing |
| minus table 7,4,0,4,0,0 | 15100 (all 14442) / 57213 / +239 (all-weeks -885) / +10.0 | 18370 (all 15898) / 58521 / -953 (all-weeks -1747) / +28.6 | months missing | months missing |
| minus day cap (P7 loss cap 16,800) | 14595 (all 14434) / 49001 / +310 (all-weeks -893) / +22.9 | 17322 (all 15153) / 56242 / -1702 (all-weeks -2492) / +31.4 | months missing | months missing |
| minus P7 cut 40/5x/w5/p3 | 18631 (all 15421) / 45624 / -1335 (all-weeks +94) / +28.2 | 17792 (all 15027) / 56866 / -3940 (all-weeks -2618) / +30.6 | months missing | months missing |

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


SZ-CDE C2 processes (IJK driver state_sizer_ijk rbjobs masters, 1 worker each (3 workers, about 10 GB per exact worker), memory gate 62 GB): c2_a=1252421, c2_b=1252423, c2_rsa=1167576 (not running)

| set | candidate | months | L1M / L3M / L6M cut vs LPB_BASE | L6M d mean | (b) eq-mean L6M cut | HOLD cut / d mean | PRE cut / d mean | X' cut / d mean | GAP cut / d mean | H2-2024 cut / d mean | WF vs live: beats % / OOS cut / d mean | WF vs JN04RM: beats % | Rule 2a label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| LPB_JN04 | LPB_JN04 (all four layers, always on, table mode) | 43 | +77.5 / +6.3 / +6.3 | +3324 | +26.2 | +8.2 / +1164 | +36.5 / -875 | +57.1 / +2352 | +14.0 / -1235 | +55.3 / -1849 | 81% / +27.2% / -1302 | n/a | OK-PRIOR (allow 16%, WF 81%) [old -1k rule: OK-PRIOR] |
| JN04RM | JN04RM (rule mode, the JN04 reference) | 43 | +47.2 / +46.0 / +46.0 | -1701 | +48.1 | +7.7 / -3658 | +32.9 / -1840 | +47.7 / -357 | +38.4 / -160 | +47.7 / -1540 | 90% / +26.9% / -2991 | 0% (cut +0.0%, d mean +0) | OK-PRIOR (allow 25%, WF 90%) [old -1k rule: RECENT-ONLY] |
| JN04LPB_C2_RS_FER | LOT off when F_ER (trend day, ER>=0.30) | 22 | na / na / na | na | na | months missing | months missing | months missing | months missing | months missing | n/a (months 22 of 43) | n/a | incomplete |
| JN04LPB_C2_RS_NFER2 | LOT off when NOT F_ER2 (6.5 h ER<0.25) | 22 | na / na / na | na | na | months missing | months missing | months missing | months missing | months missing | n/a (months 22 of 43) | n/a | incomplete |
| JN04LPB_C2_RS_NFPRIOR | LOT off when NOT F_PRIOR (prior day trend<0.6) | 22 | na / na / na | na | na | months missing | months missing | months missing | months missing | months missing | n/a (months 22 of 43) | n/a | incomplete |
