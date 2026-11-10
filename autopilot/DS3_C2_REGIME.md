# DS3_C2_REGIME - T-NEXT C2: the 2025 trend-regime loss of JN04 / JP07 (SZ-CDE, 2026-11-10 17:58Z)

> **Label: PRE-PROOF; post-hoc; Shadow only; no PASS claims. Exact engine ROLLFIX1 rows; mean $/wk = carrying week dropped (largest |cell - NEVER-CUT| week), the all-weeks mean is shown beside it because GAP has only 17 weeks. Leave-one-out rows are DIAGNOSTIC reference rows (standing rule: every layer stays ON). Prereg: autopilot/SZ_C2_PREREG.md (+ Addendum 1).**

## A. Leave-one-out on the S1b-COMB base (existing exact runs; reference = patched S1-COMB; d mean / cut vs S1-COMB)

| layer left out | GAP 2025-07..10: mean (all-weeks mean) / maxDD / d mean / cut | H2-2024: mean / maxDD / d mean / cut | HOLD: mean / maxDD / d mean / cut | L6M: mean / maxDD / d mean / cut |
|--|--|--|--|--|
| JN04 (all four layers) | 11919 (all 13865) / 70270 / -8572 / -1.2 | 18408 (all 15628) / 58316 / -2508 / +39.6 | 18007 (all 17331) / 54141 / -1935 / +45.6 | 30592 (all 28709) / 45203 / +1502 / +43.4 |
| minus LOT (P7 Calmar gate) | 21751 (all 17533) / 58112 / +1260 / +16.3 | 17514 (all 16731) / 97046 / -3401 / -0.5 | 18817 (all 18264) / 61673 / -1125 / +38.0 | 29869 (all 27055) / 61673 / +779 / +22.8 |
| minus SIGQ (dA gate) | 11911 (all 13801) / 62899 / -8580 / +9.4 | 19621 (all 16652) / 60540 / -1295 / +37.3 | 17825 (all 16878) / 54647 / -2117 / +45.1 | 31048 (all 28587) / 44068 / +1958 / +44.9 |
| minus REG (P7 ATR regime) | 15894 (all 16020) / 73722 / -4597 / -6.2 | 21188 (all 18056) / 63377 / +273 / +34.4 | 17629 (all 16812) / 61413 / -2312 / +38.3 | 30470 (all 28289) / 61413 / +1380 / +23.1 |
| minus STACK (London same-side cap 6) | 12625 (all 14844) / 66621 / -7866 / +4.0 | 19692 (all 16750) / 59746 / -1223 / +38.1 | 16401 (all 15723) / 61984 / -3541 / +37.7 | 28196 (all 26342) / 52545 / -894 / +34.2 |

## B. Leave-one-out on the LIVE-PANEL base (LPB: P7 day cap 8,400 + table 7,4,0,4,0,0 + P7 cut 40/5x/w5/p3); reference = LPB_BASE (SZ-CORE) / LPB_EMPTY; d mean / cut vs LPB_BASE

| layer left out | GAP 2025-07..10: mean (all-weeks mean) / maxDD / d mean / cut | H2-2024: mean / maxDD / d mean / cut | HOLD: mean / maxDD / d mean / cut | L6M: mean / maxDD / d mean / cut |
|--|--|--|--|--|
| LPB_JN04 (all four layers + base items) | 9935 (all 12229) / 54667 / -7755 / +14.0 | 16855 (all 14874) / 36624 / -3468 / +55.3 | 16084 (all 15759) / 72382 / +418 / +8.2 | 25256 (all 24225) / 72382 / +5376 / +6.3 |
| minus LOT | 9588 (all 12806) / 54166 / -8103 / +14.8 | months missing | months missing | months missing |
| minus SIGQ | 9791 (all 12093) / 57734 / -7899 / +9.1 | months missing | months missing | months missing |
| minus REG | months missing | months missing | months missing | months missing |
| minus STACK | months missing | months missing | months missing | months missing |
| minus table 7,4,0,4,0,0 (P7 table back to 7,7,0,7,0,0) | months missing | months missing | months missing | months missing |
| minus day cap (P7 loss cap back to 16,800) | months missing | months missing | months missing | months missing |
| minus P7 cut 40/5x/w5/p3 (back to the S1-COMB P7 cell) | months missing | months missing | months missing | months missing |

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

| set | candidate | months | L1M / L3M / L6M cut vs LPB_BASE | L6M d mean | (b) eq-mean L6M cut | HOLD cut / d mean | PRE cut / d mean | X' cut / d mean | GAP cut / d mean | H2-2024 cut / d mean | WF vs live: beats % / OOS cut / d mean | WF vs LPB_JN04: beats % | Rule 2a label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| LPB_JN04 | LPB_JN04 (all four layers, always on) | 43 | +77.5 / +6.3 / +6.3 | +5376 | +26.2 | +8.2 / +418 | +36.5 / -994 | +57.1 / +3517 | +14.0 / -7755 | +55.3 / -3468 | 81% / +27.2% / -1302 | n/a | OK-PRIOR (allow 16%, WF 81%) [old -1k rule: OK-PRIOR] |
| JN04LPB_C2_RS_FER | LOT off when F_ER (trend day, ER>=0.30) | 0 | na / na / na | na | na | months missing | months missing | months missing | months missing | months missing | n/a (months 0 of 43) | n/a | incomplete |
| JN04LPB_C2_RS_NFER2 | LOT off when NOT F_ER2 (6.5 h ER<0.25) | 0 | na / na / na | na | na | months missing | months missing | months missing | months missing | months missing | n/a (months 0 of 43) | n/a | incomplete |
| JN04LPB_C2_RS_NFPRIOR | LOT off when NOT F_PRIOR (prior day trend<0.6) | 0 | na / na / na | na | na | months missing | months missing | months missing | months missing | months missing | n/a (months 0 of 43) | n/a | incomplete |
