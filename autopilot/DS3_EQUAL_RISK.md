# DS3_EQUAL_RISK - every stack rule family re-scored at EQUAL RISK (lots scaled by one factor so worst-20-weeks / maxDD / SD equal the stack as it is), agent EQR, 2026-10-30
Research only; no live/execution change; UNTOUCHED (label day > 2026-02-06) never read; every frame cut to label day <= 20260206 at extraction. Own masks (s48score.WINMASK / vs_lib.WINS never used): Y26 = 20260101..20260206 (6 week keys, about 5 real weeks: read as a sign, not a size), L6M 20250801..20260206, HOLD 20250701..20260206, PRE 20240201..20250630, X' 20230401..20240131; WF = PRE u HOLD = 20240201..20260206 (106 weeks) is the window on which the lot factor is calibrated. MDE (2.8 x SE of the paired weekly delta) sits in parentheses beside every delta.
Prereg `l2vast/ds3/prereg/EQUAL_RISK_prereg.md` sha256 1f28f561c70f96d3bcf6da544796142d00236bb70691b3fb32f210cd10d2d37d (DECISIONS.md, written before any equal-risk quantity was computed; published delta tables of the earlier reports had been read); universe 156 rule series + 10 bases, id list sha256 7d627d43774f14c474e645b5162f5ee77934112eb93491f5d108e31f59390605; 153 unique after removing 3 duplicates (C|F|A03 = C|A|A03, C|F|A06 = C|A|A06, C|F|D40 = C|D|D_L40s). Code `l2vast/ds3/code/equal_risk/` (er_extract, er_extract2, er_lpstack, er_engine, er_frameA, er_profiles, er_fixed, er_placebo, er_lib, er_run, er_post, er_verify, er_report); outputs `l2vast/ds3/out/equal_risk/`.

## 0. Plain verdict
* 97 of the 153 unique series (the directive's qualifier set: lowered the mean AND lowered SD, maxDD or worst-20 at their own lots) are flagged in section 1; the table in section 2 scores all of them. Tier counts after the post-hoc upstream-search gate G10: 19 CANDIDATE, 64 CANDIDATE-RECENT, 70 DEAD. **No family is PASS** (two reach PASS on the prereg gates, H E on the N basis and H EL on the N basis, and both fail G10: the entry cell was picked out of 2,179 with a search RC p of 0.11).
* 83 of 153 series are >= 0 vs the stack at equal worst-20-weeks in Y26, L6M and HOLD (G1); but the bootstrap CI on the WF equal-risk delta excludes 0 only for 15, the placebo (random skip / random exit at the same SD, scaled to equal risk) is beaten at rank >= 0.95 in L6M, HOLD and WF for 20, and the reality-check adjusted p over the 153 families is <= 0.05 for 7 (global White RC p 0.0018, best family G|ADDUW|B1_PRE#1022 t 4.24).
* Equal risk does not transfer out of sample. Calibrating the lot factor on PRE only (worst-20 of 75 weeks) and measuring HOLD (section 6): the rule is at its scale in PRE by construction, but in HOLD the realized worst-20 and SD at that factor are usually WORSE than the stack's (see the oos columns); worst-20-weeks on ~100 weeks is a noisy statistic and the factor CIs (section 2) span roughly +-20-30%.
* The honest rows (PRE-selected or pre-specified, N basis where a profit rule is in): H E (70/30 split) at equal worst-20-weeks, A|H|E|N runs 1.06x lots (95% CI 0.98-1.17) and makes +22.6k $/wk more than the stack as it is in L6M (MDE 16.4k), +22.6k in HOLD, +7.7k in PRE; H EL N at equal worst-20-weeks, A|H|EL|N runs 1.18x lots (95% CI 1.00-1.43) and makes +26.3k $/wk more than the stack as it is in L6M (MDE 49.0k), +18.5k in HOLD, +25.3k in PRE; H P N (plain 70% take, no target correction) at equal worst-20-weeks, A|H|P|N runs 1.10x lots (95% CI 0.92-1.34) and makes -3.5k $/wk less than the stack as it is in L6M (MDE 49.8k), -1.8k in HOLD, -29.0k in PRE; H EPL N at equal worst-20-weeks, A|H|EPL|N runs 1.19x lots (95% CI 1.00-1.44) and makes -5.9k $/wk less than the stack as it is in L6M (MDE 64.0k), -11.4k in HOLD, -12.5k in PRE.
* The M-basis profit-take families look good at equal risk only through the target-fill correction: at equal worst-20-weeks, A|H|P|M runs 1.20x lots (95% CI 1.05-1.43) and makes +39.4k $/wk more than the stack as it is in L6M (MDE 48.1k), +37.9k in HOLD, +0.6k in PRE; the same rule on the N basis: at equal worst-20-weeks, A|H|P|N runs 1.10x lots (95% CI 0.92-1.34) and makes -3.5k $/wk less than the stack as it is in L6M (MDE 49.8k), -1.8k in HOLD, -29.0k in PRE. The random-exit placebo shows the artefact: its equal-risk L6M delta is -6.6k on M versus -17.6k on N (the M-N gap of +10.9k is what an early market exit gains from not paying the target-fill correction).
* Share of series with equal-risk delta >= 0 (worst-20 matched): PRE-selected / pre-specified / registered (128 series): Y26 73%, L6M 55%, HOLD 52%, PRE 51% (in-sample for the selection), X' 39%; ranked on looked data (25 series): Y26 84%, L6M 80%, HOLD 84%, PRE 8%, X' 24%. Placebo rules scaled to equal risk (random skip / random exit, M basis): L6M 37% / 27%, HOLD 37% / 23%, PRE 10% / 2%. So the real families sit above the placebos but near a coin flip out of sample, and the looked-data rows are positive exactly where they were looked at (L6M, HOLD) and negative in PRE (8%) and X' (24%).
* Median equal-risk delta by frame (PRE-selected / registered series only), L6M / HOLD / PRE: A (n=14) +15.4k / +11.5k / +7.7k; B (n=27) -23.6k / -19.5k / -8.3k; C (n=27) +5.5k / +3.6k / +2.2k; D (n=8) -31.6k / -26.9k / -35.4k; EA (n=30) +2.6k / +2.4k / +1.3k; EB (n=11) +1.2k / +0.9k / +0.1k; F (n=7) -7.1k / -6.6k / +1.4k; G (n=2) +20.4k / +18.5k / +30.0k; H (n=2) +0.3k / -0.4k / -0.5k. Frames: A L2SE joint, B dvg (L2SL, EXP2), C STK, D DIPENTRY, EA/EB session locks, F CUTWAIT, G ADDUW, H L2SP.

## 1. The directive's set: rules that lowered the mean AND lowered stack SD / maxDD / worst-20 (at their own lots, WF 106 weeks)
| series | frame | selection | WF mean rule / stack | SD | maxDD | worst-20 sum | down on |
|--|--|--|--|--|--|--|--|
| A|B|EL|M | A | looked(L6M-ranked) | +16.7k / +22.2k | 108k / 141k | 1018k / 746k | -2725k / -3669k | SD,w20 |
| A|B|EL|N | A | looked(L6M-ranked) | +37.2k / +55.7k | 110k / 150k | 635k / 704k | -2389k / -3308k | SD,maxDD,w20 |
| A|B|EPL|M | A | looked(L6M-ranked) | +16.9k / +22.2k | 101k / 141k | 722k / 746k | -2643k / -3669k | SD,maxDD,w20 |
| A|B|EPL|N | A | looked(L6M-ranked) | +22.1k / +55.7k | 101k / 150k | 567k / 704k | -2533k / -3308k | SD,maxDD,w20 |
| A|B|EP|N | A | looked(L6M-ranked) | +34.8k / +55.7k | 109k / 150k | 475k / 704k | -2442k / -3308k | SD,maxDD,w20 |
| A|B|E|N | A | looked(L6M-ranked) | +52.7k / +55.7k | 114k / 150k | 491k / 704k | -2309k / -3308k | SD,maxDD,w20 |
| A|B|L|M | A | looked(L6M-ranked) | +18.1k / +22.2k | 136k / 141k | 698k / 746k | -3516k / -3669k | SD,maxDD,w20 |
| A|B|L|N | A | looked(L6M-ranked) | +47.5k / +55.7k | 140k / 150k | 557k / 704k | -3028k / -3308k | SD,maxDD,w20 |
| A|B|PL|N | A | looked(L6M-ranked) | +31.1k / +55.7k | 128k / 150k | 522k / 704k | -3004k / -3308k | SD,maxDD,w20 |
| A|B|P|N | A | looked(L6M-ranked) | +38.5k / +55.7k | 132k / 150k | 548k / 704k | -3057k / -3308k | SD,maxDD,w20 |
| A|H|EPL|N | A | PRE-selected | +36.6k / +55.7k | 119k / 150k | 673k / 704k | -2789k / -3308k | SD,maxDD,w20 |
| A|H|EP|N | A | PRE-selected | +33.2k / +55.7k | 124k / 150k | 563k / 704k | -2978k / -3308k | SD,maxDD,w20 |
| A|H|PL|N | A | PRE-selected | +34.2k / +55.7k | 121k / 150k | 639k / 704k | -2827k / -3308k | SD,maxDD,w20 |
| A|H|P|N | A | PRE-selected | +31.4k / +55.7k | 125k / 150k | 523k / 704k | -2997k / -3308k | SD,maxDD,w20 |
| B|EXP2|B_FROZEN | B | PRE-selected | +24.6k / +47.1k | 124k / 138k | 795k / 601k | -3057k / -3077k | SD,w20 |
| B|EXP2|B_FROZEN_L | B | PRE-selected | -11.7k / +47.1k | 118k / 138k | 2278k / 601k | -3676k / -3077k | SD |
| B|EXP2|B_FROZEN_P | B | PRE-selected | +33.9k / +47.1k | 115k / 138k | 496k / 601k | -2570k / -3077k | SD,maxDD,w20 |
| B|EXP2|B_FROZEN_P_L | B | PRE-selected | -5.0k / +47.1k | 115k / 138k | 1901k / 601k | -3445k / -3077k | SD |
| B|EXP2|B_U1 | B | PRE-selected | +14.8k / +47.1k | 132k / 138k | 966k / 601k | -3331k / -3077k | SD |
| B|EXP2|B_U1_L | B | PRE-selected | -4.2k / +47.1k | 123k / 138k | 2018k / 601k | -3414k / -3077k | SD |
| B|EXP2|B_U1_P | B | PRE-selected | +20.1k / +47.1k | 127k / 138k | 769k / 601k | -3060k / -3077k | SD,w20 |
| B|EXP2|B_U1_P_L | B | PRE-selected | -6.0k / +47.1k | 123k / 138k | 2184k / 601k | -3388k / -3077k | SD |
| B|EXP2|B_U2 | B | PRE-selected | +18.6k / +47.1k | 127k / 138k | 837k / 601k | -3290k / -3077k | SD |
| B|EXP2|B_U2_L | B | PRE-selected | +0.6k / +47.1k | 124k / 138k | 2033k / 601k | -3627k / -3077k | SD |
| B|EXP2|B_U2_P | B | PRE-selected | +17.5k / +47.1k | 127k / 138k | 834k / 601k | -3209k / -3077k | SD |
| B|EXP2|B_U2_P_L | B | PRE-selected | +1.5k / +47.1k | 127k / 138k | 2025k / 601k | -3652k / -3077k | SD |
| B|EXP2|B_U3_L | B | PRE-selected | +36.6k / +47.1k | 129k / 138k | 552k / 601k | -2923k / -3077k | SD,maxDD,w20 |
| B|EXP2|B_U3_P | B | PRE-selected | +43.0k / +47.1k | 138k / 138k | 587k / 601k | -3129k / -3077k | SD,maxDD |
| B|EXP2|B_U3_P_L | B | PRE-selected | +30.3k / +47.1k | 125k / 138k | 512k / 601k | -3019k / -3077k | SD,maxDD,w20 |
| B|EXP2|L | B | PRE-selected | +33.4k / +47.1k | 127k / 138k | 512k / 601k | -2915k / -3077k | SD,maxDD,w20 |
| B|EXP2|P | B | PRE-selected | +41.5k / +47.1k | 137k / 138k | 565k / 601k | -3133k / -3077k | SD,maxDD |
| B|EXP2|P_L | B | PRE-selected | +28.2k / +47.1k | 122k / 138k | 507k / 601k | -2981k / -3077k | SD,maxDD,w20 |
| B|L2SL|ALL_PRE | B | PRE-selected | +35.1k / +47.1k | 127k / 138k | 643k / 601k | -2888k / -3077k | SD,w20 |
| B|L2SL|COMBO_PRE | B | PRE-selected | +37.5k / +47.1k | 129k / 138k | 666k / 601k | -2984k / -3077k | SD,w20 |
| B|L2SL|COMBO_RANK | B | looked(L6M-ranked) | +31.1k / +47.1k | 125k / 138k | 547k / 601k | -2935k / -3077k | SD,maxDD,w20 |
| B|L2SL|PE_RANK | B | looked(L6M-ranked) | +43.8k / +47.1k | 134k / 138k | 570k / 601k | -3103k / -3077k | SD,maxDD |
| B|L2SL|SM_PRE | B | PRE-selected | +45.7k / +47.1k | 137k / 138k | 603k / 601k | -3128k / -3077k | SD |
| B|L2SL|SM_RANK | B | looked(L6M-ranked) | +44.5k / +47.1k | 136k / 138k | 579k / 601k | -3122k / -3077k | SD,maxDD |
| B|L2SL|ST_PRE | B | PRE-selected | +44.3k / +47.1k | 135k / 138k | 596k / 601k | -3002k / -3077k | SD,maxDD,w20 |
| B|L2SL|ST_RANK | B | looked(L6M-ranked) | +43.1k / +47.1k | 136k / 138k | 562k / 601k | -3077k / -3077k | SD,maxDD,w20 |
| B|L2SL|WT_PRE | B | PRE-selected | +43.4k / +47.1k | 138k / 138k | 608k / 601k | -3137k / -3077k | SD |
| B|L2SL|WT_RANK | B | looked(L6M-ranked) | +43.8k / +47.1k | 136k / 138k | 599k / 601k | -3063k / -3077k | SD,maxDD,w20 |
| C|A|A02 | C | registered grid (not selected) | +45.1k / +46.8k | 123k / 138k | 472k / 578k | -2721k / -3081k | SD,maxDD,w20 |
| C|A|A07 | C | registered grid (not selected) | +43.8k / +46.8k | 135k / 138k | 605k / 578k | -3065k / -3081k | SD,w20 |
| C|A|A08 | C | registered grid (not selected) | +44.9k / +46.8k | 136k / 138k | 599k / 578k | -2960k / -3081k | SD,w20 |
| C|A|A09 | C | registered grid (not selected) | +44.5k / +46.8k | 134k / 138k | 588k / 578k | -3005k / -3081k | SD,w20 |
| C|A|A10 | C | registered grid (not selected) | +0.2k / +46.8k | 122k / 138k | 1216k / 578k | -3541k / -3081k | SD |
| C|D|D_B2s | C | registered grid (not selected) | +25.7k / +46.8k | 94k / 138k | 453k / 578k | -2004k / -3081k | SD,maxDD,w20 |
| C|D|D_B3e | C | registered grid (not selected) | +34.1k / +46.8k | 119k / 138k | 469k / 578k | -2697k / -3081k | SD,maxDD,w20 |
| C|D|D_B3h | C | registered grid (not selected) | +38.6k / +46.8k | 122k / 138k | 503k / 578k | -2640k / -3081k | SD,maxDD,w20 |
| C|D|D_B3s | C | registered grid (not selected) | +34.5k / +46.8k | 116k / 138k | 467k / 578k | -2581k / -3081k | SD,maxDD,w20 |
| C|D|D_B4s | C | registered grid (not selected) | +43.1k / +46.8k | 127k / 138k | 526k / 578k | -2751k / -3081k | SD,maxDD,w20 |
| C|D|D_L20s | C | registered grid (not selected) | +31.2k / +46.8k | 99k / 138k | 506k / 578k | -2110k / -3081k | SD,maxDD,w20 |
| C|D|D_L30s | C | registered grid (not selected) | +36.3k / +46.8k | 118k / 138k | 551k / 578k | -2607k / -3081k | SD,maxDD,w20 |
| C|D|D_L30t | C | registered grid (not selected) | +40.4k / +46.8k | 125k / 138k | 505k / 578k | -2788k / -3081k | SD,maxDD,w20 |
| C|F|C1 | C | registered section-best (PRE-picked) | +41.7k / +46.8k | 124k / 138k | 471k / 578k | -2516k / -3081k | SD,maxDD,w20 |
| D|D6L_alone | D | pre-specified rule | -1.6k / +22.2k | 109k / 141k | 1038k / 746k | -3119k / -3669k | SD,w20 |
| D|JOINT10 | D | pre-specified rule | -13.4k / +22.2k | 92k / 141k | 1673k / 746k | -2794k / -3669k | SD,w20 |
| D|JOINT20 | D | pre-specified rule | -12.0k / +22.2k | 91k / 141k | 1590k / 746k | -2745k / -3669k | SD,w20 |
| D|JOINT3 | D | pre-specified rule | -13.3k / +22.2k | 92k / 141k | 1672k / 746k | -2804k / -3669k | SD,w20 |
| D|LOSS10_alone | D | pre-specified rule | -10.4k / +22.2k | 118k / 141k | 2057k / 746k | -3508k / -3669k | SD,w20 |
| D|LOSS20_alone | D | pre-specified rule | -10.8k / +22.2k | 118k / 141k | 2075k / 746k | -3488k / -3669k | SD,w20 |
| D|LOSS3_alone | D | pre-specified rule | -11.2k / +22.2k | 118k / 141k | 2104k / 746k | -3508k / -3669k | SD,w20 |
| D|PROFIT_alone | D | pre-specified rule | +10.5k / +22.2k | 134k / 141k | 726k / 746k | -3747k / -3669k | SD,maxDD |
| E|SL|HM|NY|P1+L1.5 | EA | registered grid (all 798 cells), picked as insurance-flagged | +50.2k / +50.8k | 139k / 143k | 701k / 731k | -3213k / -3313k | SD,maxDD,w20 |
| E|SL|HM|NY|P1.5+L1.5 | EA | registered grid (all 798 cells), picked as insurance-flagged | +50.4k / +50.8k | 140k / 143k | 711k / 731k | -3227k / -3313k | SD,maxDD,w20 |
| E|SL|PB|NY|G1k70 | EA | registered grid (all 798 cells), picked as insurance-flagged | +50.6k / +50.8k | 138k / 143k | 663k / 731k | -3139k / -3313k | SD,maxDD,w20 |
| E|SL|PB|NY|G2k70 | EA | registered grid (all 798 cells), picked as insurance-flagged | +50.1k / +50.8k | 141k / 143k | 730k / 731k | -3266k / -3313k | SD,maxDD,w20 |
| E|SL|PB|NY|P1 | EA | registered grid (all 798 cells), picked as insurance-flagged | +50.5k / +50.8k | 137k / 143k | 639k / 731k | -3111k / -3313k | SD,maxDD,w20 |
| E|SL|PB|NY|P1+L1 | EA | registered grid (all 798 cells), picked as insurance-flagged | +48.5k / +50.8k | 135k / 143k | 626k / 731k | -3103k / -3313k | SD,maxDD,w20 |
| E|SL|PB|NY|P1+L1.5 | EA | registered grid (all 798 cells), picked as insurance-flagged | +50.0k / +50.8k | 137k / 143k | 630k / 731k | -3130k / -3313k | SD,maxDD,w20 |
| E|SL|PB|NY|P1+L2 | EA | registered grid (all 798 cells), picked as insurance-flagged | +50.5k / +50.8k | 137k / 143k | 627k / 731k | -3104k / -3313k | SD,maxDD,w20 |
| E|SL|PB|NY|P1+N1 | EA | registered grid (all 798 cells), picked as insurance-flagged | +49.0k / +50.8k | 136k / 143k | 633k / 731k | -3165k / -3313k | SD,maxDD,w20 |
| E|SL|PB|NY|P1+N3 | EA | registered grid (all 798 cells), picked as insurance-flagged | +50.5k / +50.8k | 137k / 143k | 639k / 731k | -3105k / -3313k | SD,maxDD,w20 |
| E|SL|PB|NY|P1.5 | EA | registered grid (all 798 cells), picked as insurance-flagged | +49.5k / +50.8k | 139k / 143k | 727k / 731k | -3224k / -3313k | SD,maxDD,w20 |
| E|SL|PB|NY|P1.5+L2 | EA | registered grid (all 798 cells), picked as insurance-flagged | +49.3k / +50.8k | 138k / 143k | 715k / 731k | -3213k / -3313k | SD,maxDD,w20 |
| E|SL|PB|NY|P1.5+N2 | EA | registered grid (all 798 cells), picked as insurance-flagged | +50.3k / +50.8k | 138k / 143k | 684k / 731k | -3191k / -3313k | SD,maxDD,w20 |
| E|SL|PB|NY|P2 | EA | registered grid (all 798 cells), picked as insurance-flagged | +50.0k / +50.8k | 140k / 143k | 722k / 731k | -3254k / -3313k | SD,maxDD,w20 |
| E|SL|PB|NY|P2+L2 | EA | registered grid (all 798 cells), picked as insurance-flagged | +49.8k / +50.8k | 140k / 143k | 710k / 731k | -3243k / -3313k | SD,maxDD,w20 |
| E|SL|PS|London|P1+N2 | EB | registered grid (all 798 cells), picked as insurance-flagged | +46.3k / +46.8k | 136k / 138k | 717k / 737k | -3182k / -3296k | SD,maxDD,w20 |
| E|SL|PS|London|P1+N3 | EB | registered grid (all 798 cells), picked as insurance-flagged | +46.0k / +46.8k | 136k / 138k | 730k / 737k | -3206k / -3296k | SD,maxDD,w20 |
| E|SL|PS|NY|L2 | EB | registered grid (all 798 cells), picked as insurance-flagged | +46.5k / +46.8k | 138k / 138k | 735k / 737k | -3299k / -3296k | SD,maxDD |
| E|SL|PS|NY|P1.5+L1 | EB | registered grid (all 798 cells), picked as insurance-flagged | +46.5k / +46.8k | 136k / 138k | 720k / 737k | -3226k / -3296k | SD,maxDD,w20 |
| E|SL|PS|NY|P2+L1 | EB | registered grid (all 798 cells), picked as insurance-flagged | +46.7k / +46.8k | 137k / 138k | 702k / 737k | -3235k / -3296k | SD,maxDD,w20 |
| E|SL|PS|NY|P2+N1 | EB | registered grid (all 798 cells), picked as insurance-flagged | +46.3k / +46.8k | 137k / 138k | 725k / 737k | -3233k / -3296k | SD,maxDD,w20 |
| E|SL|PS|NY|P3+L1.5 | EB | registered grid (all 798 cells), picked as insurance-flagged | +46.6k / +46.8k | 137k / 138k | 733k / 737k | -3263k / -3296k | SD,maxDD,w20 |
| E|SL|PS|NY|P3+L2 | EB | registered grid (all 798 cells), picked as insurance-flagged | +46.6k / +46.8k | 138k / 138k | 726k / 737k | -3283k / -3296k | SD,maxDD,w20 |
| E|SL|PS|NY|P3+N1 | EB | registered grid (all 798 cells), picked as insurance-flagged | +46.5k / +46.8k | 137k / 138k | 729k / 737k | -3237k / -3296k | SD,maxDD,w20 |
| E|SL|ST|NY|N2 | EA | registered grid (all 798 cells), picked as insurance-flagged | +50.5k / +50.8k | 141k / 143k | 712k / 731k | -3262k / -3313k | SD,maxDD,w20 |
| E|SL|ST|NY|P3+N2 | EA | registered grid (all 798 cells), picked as insurance-flagged | +50.0k / +50.8k | 140k / 143k | 723k / 731k | -3246k / -3313k | SD,maxDD,w20 |
| F|CW|ALL6 | F | PRE-selected | +14.7k / +31.7k | 132k / 162k | 1114k / 776k | -3418k / -4092k | SD,w20 |
| F|CW|KB | F | PRE-selected | +20.4k / +31.7k | 158k / 162k | 796k / 776k | -4216k / -4092k | SD |
| F|CW|PE | F | PRE-selected | +28.9k / +31.7k | 150k / 162k | 704k / 776k | -3727k / -4092k | SD,maxDD,w20 |
| F|CW|ST | F | PRE-selected | +28.9k / +31.7k | 152k / 162k | 695k / 776k | -3714k / -4092k | SD,maxDD,w20 |
| F|CW|WT | F | PRE-selected | +30.8k / +31.7k | 158k / 162k | 888k / 776k | -4010k / -4092k | SD,w20 |
| H|L2SP|ALL_L6M_rank1|N | H | looked(L6M-ranked) | +25.2k / +52.2k | 115k / 138k | 611k / 534k | -2870k / -2966k | SD,w20 |
| H|L2SP|ALL_PRE_selected|N | H | PRE-selected | +42.9k / +52.2k | 124k / 138k | 488k / 534k | -2715k / -2966k | SD,maxDD,w20 |

## 2. MAIN TABLE - every unique family at equal worst-20-weeks (primary), sorted by the equal-risk mean in L6M, HOLD tie-break
Delta = mean $/wk of the rule scaled by c* (lots x c*, locks scale, sweep charged) minus mean of the stack as it is (c = 1), same window, same frame. c* is solved on WF; the CI is a 2000-draw bootstrap over the 106 WF weeks re-solving c* each draw. Tier = prereg tier after the post-hoc upstream gate G10 (tier before in section 8). `sel`: PRE = PRE-selected / pre-specified / registered grid, LOOK = ranked on looked data (L6M), cannot exceed CANDIDATE-RECENT.
| rank | series | sel | c* [95% CI] | Y26 | L6M | HOLD | PRE | X' | WF [95% CI] | tier | failed gates |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | A|B|E|N | LOOK | 1.43 [1.15,1.85] | +117.9k (135.6k) | +90.3k (44.2k) | +80.5k (41.3k) | -6.7k (33.6k) | -12.4k (28.9k) | +19.6k (28.9k) [-9.7k,+57.4k] | CANDIDATE-RECENT | G2,G4,G7,G9,G10 |
| 2 | A|B|EPL|M | LOOK | 1.39 [1.13,1.77] | +141.3k (184.8k) | +81.6k (62.6k) | +76.4k (55.9k) | -30.9k (35.6k) | -4.1k (36.3k) | +1.2k (33.0k) [-22.9k,+28.0k] | CANDIDATE-RECENT | G2,G4,G7,G8,G9,G10 |
| 3 | A|B|EL|N | LOOK | 1.38 [1.09,1.78] | +111.8k (141.9k) | +79.7k (48.6k) | +71.2k (45.4k) | -36.3k (33.3k) | -11.3k (34.3k) | -4.2k (30.4k) [-29.9k,+28.1k] | CANDIDATE-RECENT | G2,G4,G5,G7,G8,G9,G10 |
| 4 | A|B|EP|M | LOOK | 1.44 [1.16,1.82] | +139.8k (184.0k) | +79.3k (65.0k) | +74.5k (57.8k) | -5.0k (35.7k) | -3.6k (33.9k) | +18.9k (32.1k) [-6.8k,+49.6k] | CANDIDATE-RECENT | G2,G4,G7,G8,G9,G10 |
| 5 | A|B|E|M | LOOK | 1.37 [1.14,1.75] | +116.2k (153.8k) | +79.3k (46.8k) | +69.0k (44.1k) | -4.8k (30.2k) | -11.4k (27.3k) | +17.4k (26.7k) [-4.3k,+45.3k] | CANDIDATE-RECENT | G2,G4,G7,G9,G10 |
| 6 | A|B|EL|M | LOOK | 1.35 [1.10,1.65] | +110.6k (147.4k) | +76.3k (51.4k) | +67.5k (48.0k) | -28.5k (29.3k) | -9.7k (33.5k) | +0.2k (27.9k) [-21.1k,+23.5k] | CANDIDATE-RECENT | G2,G4,G7,G9,G10 |
| 7 | H|L2SP|ALL_L6M_rank1|M | LOOK | 1.20 [0.95,1.45] | +98.3k (120.1k) | +56.4k (47.9k) | +48.7k (43.8k) | -14.0k (26.8k) | +0.5k (32.8k) | +4.8k (24.3k) [-16.4k,+26.4k] | CANDIDATE-RECENT | G2,G4,G7,G8,G9,G10 |
| 8 | A|B|PL|M | LOOK | 1.15 [0.98,1.41] | +102.8k (164.9k) | +53.0k (49.4k) | +49.6k (44.2k) | -15.8k (28.6k) | +4.8k (25.8k) | +3.8k (25.5k) [-15.3k,+27.3k] | CANDIDATE-RECENT | G2,G4,G7,G9 |
| 9 | A|H|EP|M | PRE | 1.22 [1.06,1.48] | +71.8k (158.3k) | +43.9k (52.8k) | +39.9k (46.6k) | +4.3k (25.0k) | +6.2k (29.5k) | +15.1k (22.9k) [-2.3k,+38.2k] | CANDIDATE-RECENT | G4,G6,G9,G10 |
| 10 | A|B|EP|N | LOOK | 1.35 [1.06,1.79] | +116.0k (161.6k) | +42.6k (58.7k) | +40.9k (52.2k) | -29.4k (37.6k) | -13.3k (32.8k) | -8.4k (32.0k) [-35.9k,+25.6k] | CANDIDATE-RECENT | G2,G4,G5,G7,G9,G10 |
| 11 | A|B|EPL|N | LOOK | 1.31 [1.01,1.70] | +114.9k (175.5k) | +41.2k (59.7k) | +39.4k (53.4k) | -54.8k (37.7k) | -13.7k (35.3k) | -26.9k (33.2k) [-53.8k,+3.0k] | CANDIDATE-RECENT | G2,G4,G5,G7,G9,G10 |
| 12 | A|H|P|M | PRE | 1.20 [1.05,1.43] | +67.9k (142.4k) | +39.4k (48.1k) | +37.9k (42.4k) | +0.6k (23.9k) | +6.4k (29.0k) | +11.9k (21.6k) [-4.7k,+33.1k] | CANDIDATE-RECENT | G4,G6,G9 |
| 13 | A|H|PL|M | PRE | 1.28 [1.11,1.55] | +91.9k (206.0k) | +38.8k (66.3k) | +31.1k (59.2k) | +14.3k (24.3k) | +14.6k (31.6k) | +19.5k (24.7k) [+0.8k,+45.3k] | CANDIDATE-RECENT | G6,G9 |
| 14 | A|H|EPL|M | PRE | 1.29 [1.10,1.56] | +83.5k (208.0k) | +38.7k (64.0k) | +28.9k (57.8k) | +18.3k (25.0k) | +15.4k (30.5k) | +21.7k (24.7k) [+2.3k,+46.5k] | CANDIDATE-RECENT | G6,G9,G10 |
| 15 | A|B|P|M | LOOK | 1.17 [1.03,1.36] | +45.3k (97.7k) | +34.3k (38.4k) | +33.1k (33.9k) | +2.5k (21.2k) | +9.7k (22.5k) | +11.7k (18.5k) [-1.8k,+29.9k] | CANDIDATE-RECENT | G4,G6,G7,G9 |
| 16 | G|ADDUW|B1_PRE#1022 | PRE | 1.45 [1.13,1.86] | +45.7k (63.0k) | +29.2k (42.3k) | +27.5k (38.8k) | +50.4k (38.2k) | -27.9k (37.4k) | +44.5k (29.4k) [+11.1k,+85.7k] | CANDIDATE-RECENT | G2,G6,G8,G10 |
| 17 | A|B|L|N | LOOK | 1.09 [0.95,1.27] | +61.7k (69.5k) | +27.8k (30.3k) | +27.6k (26.7k) | -17.1k (22.8k) | -2.4k (18.3k) | -3.8k (18.8k) [-21.8k,+15.1k] | CANDIDATE-RECENT | G2,G4,G5,G7,G9 |
| 18 | A|H|EL|N | PRE | 1.18 [1.00,1.43] | +78.4k (102.1k) | +26.3k (49.0k) | +18.5k (45.7k) | +25.3k (18.3k) | +5.5k (17.0k) | +23.5k (18.8k) [+2.2k,+51.8k] | CANDIDATE | G10 |
| 19 | A|B|L|M | LOOK | 1.04 [0.93,1.16] | +53.9k (90.3k) | +25.9k (33.0k) | +23.3k (29.9k) | -14.6k (20.5k) | -3.0k (17.9k) | -3.3k (17.7k) [-17.1k,+10.2k] | CANDIDATE-RECENT | G2,G4,G5,G7,G9 |
| 20 | A|H|E|N | PRE | 1.06 [0.98,1.17] | +20.5k (43.8k) | +22.6k (16.4k) | +22.6k (16.0k) | +7.7k (11.4k) | +3.3k (8.8k) | +12.3k (9.5k) [+2.5k,+24.8k] | CANDIDATE | G10 |
| 21 | A|B|PL|N | LOOK | 1.10 [0.90,1.34] | +68.8k (164.2k) | +19.8k (48.5k) | +19.2k (43.0k) | -38.5k (30.2k) | -2.7k (25.0k) | -21.5k (25.9k) [-43.7k,+2.4k] | CANDIDATE-RECENT | G2,G4,G5,G7,G9 |
| 22 | C|D|D_L20s | PRE | 1.46 [1.18,1.76] | +80.7k (148.1k) | +17.3k (57.7k) | +12.9k (53.4k) | -10.3k (32.2k) | -21.1k (34.5k) | -1.7k (27.5k) [-24.6k,+24.3k] | CANDIDATE-RECENT | G2,G3,G4,G6,G8,G9,G10 |
| 23 | A|H|L|N | PRE | 1.15 [0.97,1.38] | +74.6k (96.8k) | +15.7k (41.0k) | +11.3k (39.9k) | +19.0k (17.8k) | +4.1k (17.7k) | +16.8k (17.4k) [-1.7k,+42.0k] | CANDIDATE-RECENT | G3,G4,G5,G8,G9 |
| 24 | C|A|A05 | PRE | 1.14 [1.01,1.30] | +20.3k (51.2k) | +15.1k (24.4k) | +11.4k (22.8k) | +13.1k (16.1k) | -10.0k (13.7k) | +12.7k (13.3k) [-0.6k,+28.0k] | CANDIDATE-RECENT | G2,G4,G6,G8,G9,G10 |
| 25 | A|H|EL|M | PRE | 1.14 [0.99,1.32] | +63.3k (74.0k) | +15.0k (39.8k) | +7.9k (37.3k) | +23.7k (17.8k) | +4.5k (16.0k) | +19.2k (16.9k) [+5.1k,+37.0k] | CANDIDATE | G5,G9,G10 |
| 26 | B|L2SL|HM_RANK | LOOK | 1.09 [1.03,1.17] | +12.2k (21.8k) | +14.8k (8.9k) | +12.1k (9.7k) | +2.6k (7.2k) | +0.1k (7.9k) | +5.5k (6.0k) [-0.1k,+13.2k] | CANDIDATE-RECENT | G4,G6,G7,G8,G9 |
| 27 | A|H|E|M | PRE | 1.00 [0.94,1.10] | +19.5k (41.7k) | +13.4k (14.5k) | +11.6k (14.0k) | +7.8k (11.3k) | +2.8k (8.4k) | +9.0k (9.0k) [+2.0k,+18.0k] | CANDIDATE | G9,G10 |
| 28 | C|A|A04 | PRE | 1.29 [1.09,1.55] | +50.7k (61.4k) | +13.3k (29.4k) | +7.5k (29.0k) | +29.3k (21.9k) | -0.1k (24.6k) | +22.7k (17.9k) [+4.2k,+46.1k] | CANDIDATE-RECENT | G2,G3,G5,G6,G8,G10 |
| 29 | G|ADDUW|B2_L6Mrank#4 | LOOK | 0.97 [0.89,1.06] | +5.4k (47.5k) | +13.1k (17.9k) | +10.7k (16.3k) | -2.0k (12.8k) | -0.3k (12.8k) | +2.0k (10.4k) [-7.5k,+11.5k] | CANDIDATE-RECENT | G2,G4,G5,G6,G7,G8,G9,G10 |
| 30 | G|ADDUW|B2_PRE#5 | PRE | 1.06 [0.95,1.20] | +4.1k (28.1k) | +11.6k (17.7k) | +9.5k (15.9k) | +9.5k (15.9k) | +5.7k (9.9k) | +9.4k (12.2k) [-2.2k,+23.8k] | CANDIDATE | G4,G6,G8,G9,G10 |
| 31 | H|L2SP|ALL_L6M_rank1|N | LOOK | 1.03 [0.78,1.29] | +52.5k (134.7k) | +11.5k (49.0k) | +7.2k (45.1k) | -40.1k (26.2k) | -10.8k (31.7k) | -26.2k (23.7k) [-48.0k,-4.3k] | CANDIDATE-RECENT | G2,G3,G4,G5,G7,G8,G9,G10 |
| 32 | C|F|A06+HM5R+B02 | PRE | 1.38 [1.11,1.83] | +30.2k (116.4k) | +11.4k (40.6k) | +6.4k (38.5k) | +34.9k (28.5k) | -5.1k (27.9k) | +26.5k (23.4k) [+2.8k,+64.2k] | CANDIDATE-RECENT | G2,G3,G5,G6,G8,G9,G10 |
| 33 | C|F|A06+B02 | PRE | 1.23 [1.11,1.38] | +14.2k (33.3k) | +10.3k (21.6k) | +8.0k (20.9k) | +24.1k (15.7k) | -3.3k (15.2k) | +18.9k (12.9k) [+6.0k,+34.6k] | CANDIDATE-RECENT | G2,G3,G5,G6,G8,G10 |
| 34 | C|F|A06+HM5R | PRE | 1.30 [1.03,1.74] | +27.8k (117.7k) | +9.4k (37.8k) | +4.4k (35.7k) | +29.6k (27.4k) | -8.7k (27.5k) | +22.4k (22.3k) [-2.2k,+60.2k] | CANDIDATE-RECENT | G2,G3,G4,G5,G6,G8,G9,G10 |
| 35 | C|F|C1 | PRE | 1.22 [1.08,1.35] | +14.4k (19.6k) | +8.5k (17.5k) | +10.6k (17.2k) | +2.2k (11.8k) | -3.4k (14.0k) | +4.2k (9.8k) [-6.4k,+14.2k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 36 | B|L2SL|ALL_RANK | LOOK | 0.95 [0.86,1.05] | -2.3k (18.1k) | +8.4k (15.9k) | +6.9k (14.5k) | -6.9k (12.3k) | -4.7k (14.6k) | -2.8k (9.9k) [-13.5k,+6.9k] | DEAD | G1,G2,G4,G5,G6,G7,G8,G9 |
| 37 | E|SL|PB|NY|P1+N3 | PRE | 1.07 [1.03,1.12] | +9.0k (5.2k) | +8.1k (7.8k) | +7.2k (7.2k) | +1.4k (4.7k) | +0.1k (6.8k) | +3.1k (4.0k) [-1.0k,+7.9k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 38 | C|D|D_L30s | PRE | 1.18 [1.02,1.37] | +36.9k (63.2k) | +8.1k (33.0k) | +5.1k (30.0k) | -8.5k (18.2k) | -13.1k (19.6k) | -3.8k (15.7k) [-18.2k,+13.0k] | CANDIDATE-RECENT | G2,G3,G4,G5,G6,G8,G9,G10 |
| 39 | C|F|HM5R+B02 | PRE | 1.24 [1.08,1.51] | +18.2k (77.4k) | +8.0k (30.5k) | +5.6k (28.5k) | +14.0k (20.6k) | +4.8k (20.5k) | +11.3k (16.9k) [-4.4k,+34.7k] | CANDIDATE-RECENT | G3,G4,G5,G6,G8,G9,G10 |
| 40 | E|SL|PB|NY|P1 | PRE | 1.07 [1.02,1.11] | +8.9k (5.3k) | +7.8k (7.8k) | +6.7k (7.1k) | +1.4k (4.7k) | -0.3k (6.6k) | +3.0k (4.0k) [-0.8k,+7.5k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 41 | C|A|A08 | PRE | 1.04 [0.99,1.11] | +24.3k (41.7k) | +7.7k (13.4k) | +6.1k (12.5k) | -2.3k (9.0k) | +0.8k (8.4k) | +0.0k (7.4k) [-6.2k,+6.9k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 42 | F|CW|SM | PRE | 1.00 [0.95,1.05] | +3.2k (32.3k) | +7.5k (12.3k) | +5.6k (11.6k) | -1.9k (9.8k) | +2.1k (9.6k) | +0.4k (7.8k) [-6.2k,+6.2k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 43 | E|SL|PB|NY|P1+L2 | PRE | 1.07 [1.03,1.11] | +9.0k (5.2k) | +7.2k (8.0k) | +6.4k (7.3k) | +1.6k (4.7k) | -0.2k (6.0k) | +3.1k (4.0k) [-1.0k,+7.7k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 44 | C|A|A06 | PRE | 1.16 [1.07,1.29] | +11.6k (30.8k) | +6.6k (17.6k) | +3.4k (16.4k) | +18.9k (12.8k) | -7.6k (12.4k) | +14.4k (10.5k) [+4.5k,+27.7k] | CANDIDATE-RECENT | G2,G3,G5,G6,G8,G10 |
| 45 | E|SL|PB|NY|G1k70 | PRE | 1.06 [1.02,1.10] | +9.2k (5.6k) | +6.4k (7.5k) | +5.5k (6.7k) | +1.5k (4.4k) | +1.1k (5.9k) | +2.7k (3.7k) [-1.0k,+7.3k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 46 | C|A|A03 | PRE | 1.02 [1.00,1.06] | +5.0k (14.0k) | +6.3k (6.2k) | +5.4k (5.7k) | +3.1k (3.4k) | -0.4k (2.8k) | +3.7k (2.9k) [+1.3k,+7.2k] | CANDIDATE-RECENT | G2,G5,G6,G8,G10 |
| 47 | H|L2SP|ALL_PRE_selected|M | PRE | 1.15 [1.07,1.25] | +18.1k (56.9k) | +6.1k (23.2k) | +5.1k (20.7k) | +4.0k (13.5k) | +1.9k (16.1k) | +4.3k (11.3k) [-4.1k,+13.4k] | CANDIDATE-RECENT | G4,G5,G6,G8,G9,G10 |
| 48 | E|SL|PB|NY|P1+L1 | PRE | 1.07 [1.02,1.11] | +4.5k (8.8k) | +6.1k (8.7k) | +5.3k (8.1k) | -0.8k (5.1k) | -1.3k (8.7k) | +1.1k (4.4k) [-3.5k,+5.5k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 49 | E|SL|PB|NY|P1+L1.5 | PRE | 1.06 [1.01,1.11] | +5.4k (10.4k) | +5.9k (7.7k) | +4.9k (7.2k) | +0.9k (4.9k) | -1.4k (6.8k) | +2.1k (4.1k) [-2.3k,+6.8k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 50 | C|F|HM5R | PRE | 1.16 [1.01,1.43] | +15.9k (81.5k) | +5.6k (28.0k) | +3.2k (26.0k) | +9.8k (20.5k) | +0.8k (19.8k) | +7.9k (16.4k) [-7.6k,+32.4k] | CANDIDATE-RECENT | G3,G4,G5,G6,G8,G9,G10 |
| 51 | C|F|HM5M | PRE | 1.11 [1.03,1.23] | +9.8k (38.1k) | +5.5k (13.1k) | +3.6k (12.7k) | +6.5k (9.7k) | +1.1k (9.6k) | +5.6k (7.8k) [-2.4k,+16.1k] | CANDIDATE-RECENT | G3,G4,G5,G6,G8,G9,G10 |
| 52 | C|D|D_B4s | PRE | 1.12 [1.02,1.23] | +19.2k (40.5k) | +5.5k (20.5k) | +3.5k (18.6k) | +0.2k (13.6k) | -8.5k (12.8k) | +1.5k (11.1k) [-8.5k,+12.1k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 53 | C|D|D_L40s | PRE | 1.06 [1.02,1.14] | +12.8k (21.1k) | +5.2k (7.9k) | +3.6k (7.7k) | +5.1k (6.1k) | -3.4k (7.4k) | +4.7k (4.9k) [+0.3k,+11.4k] | CANDIDATE-RECENT | G2,G5,G6,G8,G9,G10 |
| 54 | C|D|D_B2s | PRE | 1.53 [1.17,1.93] | +65.3k (194.0k) | +5.0k (64.1k) | +3.5k (59.5k) | -16.1k (37.5k) | -17.3k (38.2k) | -8.5k (31.6k) [-34.6k,+18.4k] | CANDIDATE-RECENT | G2,G3,G4,G5,G6,G8,G9,G10 |
| 55 | E|SL|PB|NY|P1.5+N2 | PRE | 1.04 [1.01,1.08] | +6.7k (8.2k) | +4.9k (5.5k) | +4.5k (5.4k) | +0.2k (4.1k) | -1.6k (5.6k) | +1.5k (3.4k) [-1.7k,+5.5k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 56 | E|SL|PB|London|P1.5+N1 | PRE | 1.08 [1.01,1.14] | +9.4k (32.6k) | +4.9k (10.1k) | +4.3k (9.1k) | +6.5k (7.3k) | +4.4k (8.4k) | +5.9k (5.8k) [-0.5k,+12.2k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 57 | E|SL|PB|NY|G1k50 | PRE | 1.04 [1.01,1.08] | +8.5k (6.9k) | +4.8k (7.1k) | +4.1k (6.4k) | +2.6k (4.0k) | +1.4k (4.7k) | +3.1k (3.4k) [-0.2k,+6.8k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 58 | E|SL|PB|NY|P1+N1 | PRE | 1.05 [1.01,1.09] | +1.9k (8.8k) | +4.3k (7.3k) | +3.6k (6.9k) | -0.7k (4.9k) | -3.0k (9.2k) | +0.6k (4.1k) [-3.4k,+4.7k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 59 | E|SL|PB|London|P3+N1 | PRE | 1.07 [1.00,1.12] | +3.9k (27.9k) | +4.1k (8.1k) | +3.9k (7.4k) | +5.9k (6.1k) | +2.1k (6.2k) | +5.3k (4.8k) [-0.7k,+11.4k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 60 | C|F|B02 | PRE | 1.06 [1.01,1.11] | +2.2k (10.3k) | +3.7k (8.4k) | +4.3k (9.0k) | +3.9k (6.3k) | +4.3k (8.0k) | +3.6k (5.0k) [-1.0k,+8.8k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 61 | E|SL|PB|London|P2+N1 | PRE | 1.07 [1.00,1.14] | +6.6k (32.2k) | +3.6k (9.3k) | +3.5k (8.4k) | +6.6k (6.1k) | +2.9k (6.6k) | +5.7k (5.0k) [+0.1k,+12.2k] | CANDIDATE | G5,G6,G8,G9,G10 |
| 62 | E|SL|PS|London|P1+N3 | PRE | 1.03 [1.00,1.06] | +14.4k (17.7k) | +3.5k (6.9k) | +3.2k (6.2k) | -0.6k (4.2k) | +0.1k (4.9k) | +0.5k (3.5k) [-2.6k,+4.0k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 63 | E|SL|WT|NY|P2+N1 | PRE | 1.01 [0.98,1.05] | +5.8k (7.7k) | +3.3k (5.8k) | +3.0k (5.3k) | +0.9k (4.4k) | +2.0k (4.8k) | +1.5k (3.5k) [-2.5k,+5.3k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 64 | E|SL|PS|London|P1+N2 | PRE | 1.04 [1.01,1.07] | +9.0k (24.8k) | +3.0k (7.1k) | +2.8k (6.5k) | +0.5k (4.5k) | -0.0k (4.8k) | +1.2k (3.7k) [-2.3k,+4.7k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 65 | E|SL|PB|NY|P1.5 | PRE | 1.03 [1.00,1.06] | +3.7k (10.2k) | +2.9k (4.3k) | +2.4k (4.0k) | -0.9k (3.8k) | -1.3k (5.1k) | +0.1k (3.0k) [-2.7k,+3.2k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 66 | E|SL|PS|NY|P1.5+L1 | PRE | 1.02 [1.00,1.04] | +6.8k (11.7k) | +2.8k (4.8k) | +2.2k (4.6k) | +0.1k (2.8k) | -0.4k (4.0k) | +0.7k (2.4k) [-1.3k,+3.0k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 67 | E|SL|WT|NY|P2 | PRE | 1.02 [1.00,1.03] | +4.5k (5.9k) | +2.6k (3.1k) | +2.4k (2.8k) | +1.1k (2.0k) | +0.4k (2.5k) | +1.5k (1.6k) [+0.0k,+3.2k] | CANDIDATE | G5,G6,G8,G9,G10 |
| 68 | B|L2SL|SM_RANK | LOOK | 0.99 [0.91,1.05] | +5.1k (16.5k) | +2.6k (8.0k) | +2.6k (7.4k) | -5.7k (5.9k) | -1.4k (4.9k) | -3.2k (4.8k) [-9.3k,+2.6k] | CANDIDATE-RECENT | G2,G4,G5,G6,G7,G8,G9 |
| 69 | E|SL|PB|NY|P1.5+L2 | PRE | 1.03 [1.00,1.07] | +4.8k (9.2k) | +2.5k (4.9k) | +2.2k (4.6k) | -0.8k (3.9k) | -1.0k (4.8k) | +0.1k (3.1k) [-3.0k,+3.6k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 70 | E|SL|HM|NY|P1.5+L1.5 | PRE | 1.03 [0.99,1.06] | +6.9k (22.4k) | +2.4k (10.0k) | +2.6k (9.3k) | +0.2k (5.2k) | +0.8k (7.2k) | +1.0k (4.6k) [-3.3k,+5.3k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 71 | F|CW|WT | PRE | 1.02 [0.94,1.08] | -13.3k (30.6k) | +2.3k (11.5k) | -0.7k (12.9k) | -0.1k (9.1k) | -4.7k (9.9k) | -0.3k (7.5k) [-7.3k,+5.9k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 72 | E|SL|PS|NY|P2+N1 | PRE | 1.02 [0.99,1.04] | +6.4k (13.0k) | +2.3k (5.0k) | +1.7k (4.6k) | -0.2k (3.2k) | +0.4k (4.5k) | +0.4k (2.7k) [-2.3k,+2.5k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 73 | E|SL|PS|NY|P2+L1 | PRE | 1.02 [1.00,1.04] | +4.8k (13.5k) | +2.1k (4.4k) | +1.6k (4.1k) | +0.4k (2.6k) | +0.1k (3.6k) | +0.8k (2.2k) [-1.1k,+2.9k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 74 | C|A|A09 | PRE | 1.03 [0.99,1.08] | -1.7k (31.2k) | +2.0k (9.9k) | +1.0k (8.8k) | -2.1k (6.6k) | -0.7k (4.7k) | -1.2k (5.4k) [-5.8k,+4.2k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 75 | E|SL|PB|NY|P2 | PRE | 1.02 [1.00,1.04] | +2.8k (7.3k) | +2.0k (3.1k) | +1.5k (2.9k) | -0.4k (3.0k) | -1.0k (3.8k) | +0.1k (2.3k) [-2.1k,+2.6k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 76 | B|L2SL|COMBO_RANK | LOOK | 1.05 [0.90,1.18] | +3.9k (31.5k) | +1.6k (20.8k) | +2.7k (18.5k) | -21.6k (19.0k) | -9.2k (14.0k) | -14.5k (14.8k) [-28.3k,-1.8k] | CANDIDATE-RECENT | G2,G4,G5,G6,G7,G8,G9 |
| 77 | E|SL|PB|NY|G2k70 | PRE | 1.01 [1.00,1.03] | +2.7k (5.1k) | +1.6k (2.4k) | +1.1k (2.3k) | -0.3k (2.4k) | +0.4k (2.4k) | +0.1k (1.9k) [-1.6k,+2.2k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 78 | E|SL|PB|NY|P2+L2 | PRE | 1.02 [1.00,1.05] | +3.8k (6.7k) | +1.5k (4.0k) | +1.2k (3.6k) | -0.3k (3.2k) | -0.8k (3.5k) | +0.2k (2.5k) [-2.1k,+2.7k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 79 | A|H|L|M | PRE | 1.09 [0.96,1.27] | +55.8k (67.6k) | +1.4k (33.0k) | -4.0k (30.5k) | +11.7k (14.8k) | +2.9k (15.8k) | +7.0k (14.0k) [-4.5k,+22.2k] | DEAD | G1,G3,G4,G5,G8,G9 |
| 80 | C|D|D_L30t | PRE | 1.11 [0.98,1.28] | +9.5k (37.5k) | +1.4k (23.7k) | +0.5k (21.4k) | -3.8k (14.0k) | -10.9k (15.3k) | -2.1k (11.7k) [-13.7k,+11.7k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 81 | E|SL|PS|NY|P3+N1 | PRE | 1.02 [0.99,1.04] | +2.1k (13.0k) | +1.2k (4.1k) | +0.9k (3.8k) | +0.5k (3.2k) | +0.4k (4.5k) | +0.6k (2.5k) [-1.8k,+2.7k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 82 | E|SL|KB|Asia|P3+L2 | PRE | 1.00 [1.00,1.01] | +4.0k (10.8k) | +1.0k (3.2k) | +0.8k (2.8k) | +1.2k (2.8k) | -0.1k (0.3k) | +1.1k (2.1k) [-0.4k,+2.7k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 83 | E|SL|PS|NY|G2k70 | PRE | 1.00 [1.00,1.01] | +3.1k (10.8k) | +0.9k (3.0k) | +0.8k (2.6k) | +0.1k (1.0k) | +0.6k (1.2k) | +0.3k (1.0k) [-0.4k,+1.2k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 84 | E|SL|KB|Asia|P3 | PRE | 1.00 [1.00,1.00] | +3.9k (10.9k) | +0.8k (2.3k) | +0.7k (2.0k) | +0.6k (2.1k) | +0.0k (0.0k) | +0.6k (1.6k) [-0.3k,+1.9k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 85 | E|SL|WT|Asia|P1+L1 | PRE | 1.03 [0.97,1.07] | -7.3k (22.2k) | +0.5k (9.1k) | +0.7k (8.6k) | +2.1k (6.9k) | +1.2k (4.5k) | +1.7k (5.5k) [-3.8k,+6.8k] | DEAD | G1,G3,G4,G5,G6,G8,G9,G10 |
| 86 | B|L2SL|HM_PRE | PRE | 1.04 [0.95,1.14] | +1.1k (29.5k) | +0.4k (13.2k) | -1.2k (13.2k) | +5.4k (9.7k) | -2.5k (8.6k) | +3.4k (8.0k) [-5.0k,+12.8k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| 87 | E|SL|HM|NY|P1+L1.5 | PRE | 1.03 [0.99,1.08] | +4.2k (21.6k) | +0.4k (13.0k) | +1.6k (11.8k) | +0.7k (6.4k) | -0.6k (9.9k) | +1.0k (5.7k) [-4.0k,+6.9k] | CANDIDATE-RECENT | G2,G3,G4,G5,G6,G8,G9,G10 |
| 88 | E|SL|PB|London|P3+L1.5 | PRE | 1.03 [0.98,1.07] | +2.2k (18.1k) | +0.4k (5.1k) | +0.3k (4.6k) | +2.4k (3.6k) | +1.5k (2.6k) | +1.8k (2.9k) [-2.1k,+6.0k] | CANDIDATE-RECENT | G3,G4,G5,G6,G8,G9,G10 |
| 89 | E|SL|PS|NY|P3+L2 | PRE | 1.00 [1.00,1.01] | +0.0k (3.2k) | +0.3k (1.3k) | +0.2k (1.1k) | -0.0k (1.1k) | -0.1k (1.6k) | +0.1k (0.8k) [-0.8k,+1.0k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 90 | C|D|D_B3s | PRE | 1.19 [0.98,1.44] | +22.8k (77.5k) | +0.2k (34.4k) | -1.4k (31.1k) | -8.3k (23.7k) | -11.6k (24.3k) | -5.6k (19.1k) [-23.3k,+14.3k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 91 | C|A|A01 | PRE | 0.99 [0.93,1.05] | -3.0k (19.6k) | +0.1k (8.6k) | +0.9k (7.6k) | -0.3k (5.9k) | -0.9k (4.7k) | +0.0k (4.8k) [-5.7k,+5.4k] | DEAD | G1,G2,G4,G5,G6,G8,G9,G10 |
| 92 | E|SL|PS|NY|P3+L1.5 | PRE | 1.01 [0.99,1.03] | -0.7k (4.5k) | -0.1k (2.2k) | -0.3k (2.0k) | +0.5k (1.6k) | -0.9k (2.7k) | +0.3k (1.3k) [-1.4k,+1.7k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 93 | E|SL|PS|NY|L2 | PRE | 1.00 [0.99,1.01] | -0.2k (2.5k) | -0.1k (1.3k) | -0.1k (1.1k) | -0.3k (0.9k) | -0.1k (1.5k) | -0.3k (0.7k) [-0.9k,+0.4k] | DEAD | G1,G2,G4,G5,G6,G8,G9,G10 |
| 94 | A|B|P|N | LOOK | 1.08 [0.93,1.29] | +13.6k (112.8k) | -0.2k (38.8k) | +1.6k (34.1k) | -20.5k (21.6k) | +1.5k (21.3k) | -14.0k (18.5k) [-30.0k,+4.6k] | DEAD | G1,G2,G4,G5,G6,G7,G8,G9 |
| 95 | B|EXP2|B_U3 | PRE | 1.02 [0.97,1.06] | -9.0k (20.0k) | -0.3k (9.0k) | -0.5k (8.0k) | +5.5k (7.6k) | -1.0k (6.3k) | +3.7k (5.9k) [-1.0k,+9.3k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 96 | C|A|A07 | PRE | 1.01 [0.93,1.10] | -9.0k (43.8k) | -0.3k (18.8k) | -1.7k (16.7k) | -3.4k (8.7k) | -1.2k (8.0k) | -2.8k (7.9k) [-10.4k,+5.6k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 97 | C|D|D_B3e | PRE | 1.14 [0.96,1.38] | +8.3k (67.8k) | -0.5k (30.8k) | -1.9k (28.3k) | -11.5k (21.5k) | -16.4k (21.6k) | -7.8k (17.2k) [-23.5k,+11.6k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 98 | E|SL|ST|Asia|P1.5+N3 | PRE | 1.01 [0.98,1.05] | +18.4k (57.5k) | -0.6k (14.6k) | -0.5k (12.8k) | +3.4k (5.7k) | +0.7k (1.5k) | +2.2k (5.5k) [-2.5k,+7.3k] | DEAD | G1,G3,G4,G5,G6,G8,G9,G10 |
| 99 | B|EXP2|P | PRE | 0.98 [0.82,1.14] | +23.1k (62.4k) | -0.7k (18.5k) | -5.6k (27.9k) | -6.5k (15.3k) | -17.8k (20.7k) | -6.3k (13.7k) [-20.5k,+7.8k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 100 | B|L2SL|SM_PRE | PRE | 0.98 [0.93,1.02] | -1.9k (12.9k) | -1.2k (4.9k) | -1.3k (4.5k) | -2.3k (3.8k) | +1.0k (2.2k) | -2.1k (3.0k) [-6.5k,+1.2k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| 101 | E|SL|PS|London|N2 | PRE | 1.00 [0.98,1.02] | -7.5k (13.3k) | -1.2k (3.3k) | -0.9k (2.9k) | +0.8k (2.1k) | -0.2k (0.9k) | +0.3k (1.7k) [-1.6k,+1.9k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 102 | A|H|EP|N | PRE | 1.11 [0.94,1.35] | +38.4k (154.8k) | -1.5k (51.4k) | -1.5k (44.9k) | -25.8k (25.6k) | -5.3k (28.1k) | -18.8k (22.7k) [-38.1k,+3.9k] | DEAD | G1,G2,G4,G5,G6,G8,G9,G10 |
| 103 | E|SL|ST|NY|N2 | PRE | 1.02 [0.99,1.04] | +3.1k (14.2k) | -1.7k (8.6k) | -1.4k (7.6k) | +1.4k (3.3k) | -2.9k (4.4k) | +0.6k (3.2k) [-2.6k,+3.7k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 104 | E|SL|ST|NY|P3+N2 | PRE | 1.02 [0.99,1.05] | -0.4k (20.8k) | -2.6k (9.4k) | -2.5k (8.3k) | +1.5k (3.6k) | -2.6k (4.2k) | +0.3k (3.6k) [-3.2k,+3.9k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 105 | B|EXP2|B_U3_P | PRE | 0.98 [0.81,1.15] | +13.8k (72.1k) | -2.7k (20.4k) | -7.9k (29.2k) | -3.3k (17.1k) | -19.7k (21.6k) | -4.7k (14.9k) [-21.1k,+11.3k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 106 | E|SL|ST|Asia|P1.5+L2 | PRE | 1.01 [0.98,1.04] | +4.5k (34.4k) | -2.9k (10.4k) | -2.6k (9.1k) | +2.8k (5.7k) | +0.7k (1.5k) | +1.2k (4.9k) [-3.3k,+5.8k] | DEAD | G1,G3,G4,G5,G6,G8,G9,G10 |
| 107 | B|L2SL|KB_RANK | LOOK | 0.98 [0.94,1.00] | -4.7k (9.6k) | -2.9k (3.8k) | -2.7k (3.5k) | -5.7k (4.1k) | +0.6k (4.1k) | -4.9k (3.1k) [-8.8k,-2.3k] | DEAD | G1,G2,G3,G4,G5,G6,G7,G8,G9 |
| 108 | B|L2SL|ST_RANK | LOOK | 1.00 [0.92,1.07] | +5.0k (46.7k) | -3.1k (17.7k) | -1.5k (15.6k) | -4.9k (10.8k) | -5.9k (7.9k) | -3.9k (8.9k) [-12.7k,+4.3k] | DEAD | G1,G2,G3,G4,G5,G6,G7,G8,G9 |
| 109 | B|L2SL|KB_PRE | PRE | 0.97 [0.93,1.01] | +2.7k (6.6k) | -3.2k (5.6k) | -2.6k (5.0k) | -5.3k (3.9k) | -2.3k (3.3k) | -4.5k (3.2k) [-8.6k,-1.2k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| 110 | A|H|P|N | PRE | 1.10 [0.92,1.34] | +29.6k (157.5k) | -3.5k (49.8k) | -1.8k (43.8k) | -29.0k (25.3k) | -5.1k (27.8k) | -21.0k (22.4k) [-38.8k,+0.6k] | DEAD | G1,G2,G4,G5,G6,G8,G9 |
| 111 | F|CW|HM | PRE | 1.03 [0.95,1.13] | +12.6k (46.3k) | -3.5k (24.7k) | -5.3k (23.2k) | +4.5k (12.9k) | +4.5k (14.7k) | +1.6k (11.5k) [-7.6k,+11.8k] | DEAD | G1,G3,G4,G5,G6,G8,G9,G10 |
| 112 | B|L2SL|WT_RANK | LOOK | 1.00 [0.96,1.05] | -11.8k (12.9k) | -3.8k (7.0k) | -3.2k (6.2k) | -2.9k (5.0k) | -0.5k (5.5k) | -3.0k (4.0k) [-7.4k,+0.9k] | DEAD | G1,G2,G3,G4,G5,G6,G7,G8,G9 |
| 113 | C|D|D_B3h | PRE | 1.17 [1.01,1.31] | +3.6k (47.0k) | -4.0k (26.6k) | -6.6k (24.9k) | -0.9k (19.1k) | -9.9k (19.0k) | -1.8k (15.2k) [-16.1k,+12.8k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 114 | B|L2SL|WT_PRE | PRE | 0.98 [0.94,1.01] | -12.5k (24.1k) | -4.5k (6.0k) | -4.4k (5.2k) | -4.5k (3.3k) | +1.5k (2.8k) | -4.5k (2.8k) [-8.2k,-2.0k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| 115 | B|L2SL|PE_PRE | PRE | 1.01 [0.97,1.05] | -4.6k (12.1k) | -4.6k (8.2k) | -3.6k (7.7k) | +2.3k (5.5k) | -1.2k (5.7k) | +0.5k (4.5k) [-4.0k,+4.9k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| 116 | B|L2SL|PE_RANK | LOOK | 0.99 [0.92,1.04] | -1.0k (14.7k) | -4.8k (7.5k) | -3.6k (6.9k) | -3.6k (6.1k) | -1.8k (6.1k) | -3.6k (4.8k) [-9.7k,+1.0k] | DEAD | G1,G2,G3,G4,G5,G6,G7,G8,G9 |
| 117 | B|L2SL|ST_PRE | PRE | 1.03 [0.95,1.10] | +24.5k (44.4k) | -5.5k (20.2k) | -4.5k (17.7k) | -0.3k (5.9k) | -5.3k (8.3k) | -1.6k (6.8k) [-8.7k,+5.4k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| 118 | H|L2SP|ALL_PRE_selected|N | PRE | 1.09 [0.96,1.20] | +6.5k (57.7k) | -5.5k (22.5k) | -5.9k (20.0k) | -5.0k (12.8k) | -2.9k (16.3k) | -5.3k (10.8k) [-17.6k,+5.0k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 119 | A|H|EPL|N | PRE | 1.19 [1.00,1.44] | +48.7k (219.7k) | -5.9k (64.0k) | -11.4k (56.2k) | -12.5k (25.3k) | +3.3k (28.6k) | -12.3k (24.5k) [-33.3k,+12.0k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 120 | E|SL|ST|Asia|P1.5+N2 | PRE | 1.02 [0.98,1.05] | +3.5k (30.2k) | -6.7k (13.1k) | -6.0k (11.5k) | +4.5k (6.2k) | +0.7k (1.6k) | +1.4k (5.7k) [-3.6k,+5.9k] | DEAD | G1,G3,G4,G5,G6,G8,G9,G10 |
| 121 | C|A|A02 | PRE | 1.13 [0.96,1.32] | -6.2k (63.5k) | -7.0k (38.1k) | -5.1k (35.8k) | +8.1k (21.6k) | -17.5k (21.5k) | +4.3k (18.7k) [-13.2k,+23.2k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 122 | F|CW|ST | PRE | 1.10 [0.99,1.22] | +12.7k (46.2k) | -7.1k (24.5k) | -6.6k (22.9k) | +3.0k (15.9k) | -4.0k (17.1k) | +0.1k (13.2k) [-10.5k,+12.1k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 123 | A|H|PL|N | PRE | 1.17 [0.99,1.44] | +49.6k (224.1k) | -7.5k (65.9k) | -10.9k (57.6k) | -17.4k (25.3k) | +2.1k (29.2k) | -15.6k (24.8k) [-35.1k,+9.8k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| 124 | B|EXP2|B_FROZEN_P | PRE | 1.20 [0.88,1.58] | -8.4k (90.8k) | -9.4k (76.5k) | -3.1k (74.1k) | -7.9k (38.8k) | -1.7k (41.4k) | -6.5k (35.2k) [-36.9k,+27.8k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 125 | F|CW|PE | PRE | 1.10 [1.01,1.18] | -1.3k (34.4k) | -11.3k (23.2k) | -8.8k (21.0k) | +3.7k (14.3k) | +3.7k (15.4k) | -0.0k (12.0k) [-9.3k,+9.4k] | DEAD | G1,G3,G4,G5,G6,G8,G9,G10 |
| 126 | D|D6L_alone | PRE | 1.18 [0.91,1.51] | +72.1k (123.8k) | -12.0k (61.9k) | -8.5k (57.7k) | -30.3k (34.4k) | -17.9k (37.0k) | -24.0k (30.0k) [-44.9k,-3.2k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 127 | B|L2SL|ALL_PRE | PRE | 1.07 [0.90,1.27] | +23.6k (24.8k) | -15.8k (32.1k) | -15.2k (28.1k) | -7.2k (14.1k) | -13.6k (15.7k) | -9.7k (13.0k) [-22.8k,+5.3k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| 128 | D|PROFIT_alone | PRE | 0.98 [0.84,1.16] | +27.9k (110.4k) | -16.3k (38.3k) | -16.3k (37.7k) | -9.8k (22.2k) | -1.1k (23.8k) | -11.9k (19.4k) [-26.5k,+3.3k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 129 | B|L2SL|COMBO_PRE | PRE | 1.03 [0.90,1.17] | +9.7k (30.0k) | -17.8k (23.6k) | -17.1k (21.4k) | -4.5k (13.7k) | -8.3k (14.3k) | -8.4k (11.7k) [-20.2k,+3.8k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| 130 | B|EXP2|B_FROZEN | PRE | 1.01 [0.75,1.33] | -13.1k (112.7k) | -19.6k (71.4k) | -14.5k (68.9k) | -25.2k (38.7k) | -1.5k (42.5k) | -22.2k (34.2k) [-48.4k,+8.4k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 131 | B|EXP2|B_U3_L | PRE | 1.05 [0.85,1.26] | -20.0k (75.3k) | -23.6k (37.3k) | -19.7k (35.1k) | -3.6k (27.2k) | -17.1k (23.2k) | -8.5k (22.0k) [-27.3k,+11.9k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 132 | B|EXP2|L | PRE | 1.06 [0.84,1.25] | -17.6k (71.5k) | -24.0k (34.5k) | -19.5k (32.5k) | -8.3k (26.7k) | -14.5k (21.5k) | -11.8k (21.3k) [-31.2k,+7.1k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 133 | B|EXP2|B_U1_P | PRE | 1.01 [0.76,1.23] | -6.6k (183.2k) | -25.9k (61.9k) | -22.2k (57.1k) | -28.5k (35.0k) | -14.7k (36.0k) | -26.8k (30.0k) [-51.5k,-3.2k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 134 | F|CW|KB | PRE | 0.97 [0.84,1.11] | +0.5k (68.7k) | -27.0k (32.0k) | -26.1k (27.6k) | -5.8k (16.7k) | +3.8k (16.7k) | -12.0k (14.6k) [-24.5k,+0.0k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 135 | B|EXP2|B_U1 | PRE | 0.92 [0.72,1.09] | -39.1k (148.5k) | -29.1k (59.4k) | -27.6k (54.5k) | -35.4k (32.7k) | -8.3k (37.5k) | -33.4k (28.2k) [-55.2k,-12.3k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 136 | B|EXP2|B_U3_P_L | PRE | 1.02 [0.79,1.24] | -10.0k (53.8k) | -29.2k (31.8k) | -30.7k (37.7k) | -9.8k (27.2k) | -29.1k (27.9k) | -16.2k (22.4k) [-36.8k,+3.4k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 137 | B|EXP2|P_L | PRE | 1.03 [0.80,1.26] | -7.3k (47.8k) | -29.4k (29.5k) | -30.3k (36.0k) | -12.5k (27.2k) | -26.9k (28.8k) | -18.0k (22.1k) [-38.3k,+1.8k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 138 | D|JOINT3 | PRE | 1.31 [0.99,1.64] | +47.2k (119.1k) | -30.9k (63.1k) | -25.8k (63.2k) | -45.0k (40.6k) | -12.4k (42.4k) | -39.6k (34.5k) [-61.1k,-17.7k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 139 | D|JOINT10 | PRE | 1.31 [1.00,1.65] | +47.2k (119.1k) | -31.2k (63.3k) | -26.1k (63.3k) | -45.0k (40.6k) | -12.0k (42.4k) | -39.8k (34.6k) [-60.5k,-17.6k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 140 | D|JOINT20 | PRE | 1.34 [1.06,1.65] | +46.7k (119.4k) | -32.1k (64.3k) | -27.7k (64.0k) | -42.3k (39.6k) | -10.0k (42.7k) | -38.3k (34.1k) [-59.1k,-16.3k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 141 | D|LOSS20_alone | PRE | 1.05 [0.89,1.22] | -4.5k (87.8k) | -32.8k (41.2k) | -28.1k (37.1k) | -35.4k (29.0k) | +1.4k (33.3k) | -33.6k (23.3k) [-48.8k,-18.2k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 142 | D|LOSS10_alone | PRE | 1.05 [0.89,1.20] | -3.3k (87.6k) | -32.9k (41.6k) | -28.5k (37.8k) | -34.5k (28.9k) | +1.1k (33.4k) | -33.0k (23.4k) [-48.7k,-16.9k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 143 | B|EXP2|B_U2_P | PRE | 0.96 [0.68,1.24] | -44.5k (156.2k) | -33.4k (54.5k) | -28.0k (55.1k) | -30.9k (36.9k) | -18.8k (35.9k) | -30.3k (30.8k) [-54.0k,-2.9k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 144 | D|LOSS3_alone | PRE | 1.05 [0.89,1.20] | -3.2k (87.5k) | -34.0k (42.3k) | -29.3k (38.5k) | -35.4k (28.9k) | +0.9k (33.6k) | -33.9k (23.5k) [-50.5k,-17.9k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 145 | B|EXP2|B_U2 | PRE | 0.94 [0.69,1.19] | -45.2k (156.6k) | -34.0k (56.6k) | -29.6k (54.7k) | -29.3k (35.8k) | -15.2k (35.8k) | -29.7k (30.1k) [-53.1k,-5.8k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 146 | F|CW|ALL6 | PRE | 1.20 [0.88,1.52] | +16.0k (203.4k) | -47.2k (68.1k) | -50.2k (62.1k) | +1.4k (39.0k) | +6.3k (47.1k) | -14.2k (33.8k) [-40.3k,+12.6k] | DEAD | G1,G3,G4,G5,G6,G8,G9,G10 |
| 147 | C|A|A10 | PRE | 0.87 [0.66,1.11] | -25.5k (60.6k) | -51.7k (48.4k) | -40.7k (55.8k) | -51.1k (32.4k) | -9.7k (38.8k) | -46.6k (28.1k) [-65.9k,-26.4k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 148 | B|EXP2|B_U2_L | PRE | 0.85 [0.63,1.05] | -86.1k (116.6k) | -55.0k (43.6k) | -48.1k (44.8k) | -45.3k (34.0k) | -32.7k (38.6k) | -46.6k (27.5k) [-66.9k,-28.2k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 149 | B|EXP2|B_U2_P_L | PRE | 0.84 [0.62,1.08] | -91.1k (110.5k) | -55.7k (43.2k) | -49.9k (46.2k) | -43.4k (35.4k) | -32.8k (39.0k) | -45.8k (28.5k) [-66.4k,-24.9k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 150 | B|EXP2|B_U1_L | PRE | 0.90 [0.66,1.13] | -70.8k (110.4k) | -58.0k (50.4k) | -50.8k (48.1k) | -50.2k (34.8k) | -32.8k (38.8k) | -50.8k (28.4k) [-70.8k,-31.3k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 151 | B|EXP2|B_FROZEN_P_L | PRE | 0.89 [0.64,1.18] | -55.8k (70.9k) | -61.7k (56.8k) | -53.3k (57.4k) | -50.1k (36.6k) | -31.7k (41.9k) | -51.5k (31.0k) [-70.1k,-30.6k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 152 | B|EXP2|B_FROZEN_L | PRE | 0.84 [0.60,1.11] | -57.4k (81.8k) | -62.7k (55.8k) | -53.3k (56.6k) | -57.6k (36.5k) | -36.0k (42.3k) | -56.8k (30.8k) [-77.1k,-35.3k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 153 | B|EXP2|B_U1_P_L | PRE | 0.91 [0.67,1.13] | -64.6k (101.9k) | -63.3k (48.7k) | -55.0k (48.6k) | -50.7k (34.8k) | -31.2k (40.1k) | -52.5k (28.5k) [-71.9k,-33.1k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |

### 2b. Same table restricted to PRE-selected / pre-specified / registered series (no L6M-ranked rows), L6M order
| rank | series | c* [95% CI] | Y26 | L6M | HOLD | PRE | X' | WF [95% CI] | tier | failed gates |
|--|--|--|--|--|--|--|--|--|--|--|
| 1 | A|H|EP|M | 1.22 [1.06,1.48] | +71.8k (158.3k) | +43.9k (52.8k) | +39.9k (46.6k) | +4.3k (25.0k) | +6.2k (29.5k) | +15.1k (22.9k) [-2.3k,+38.2k] | CANDIDATE-RECENT | G4,G6,G9,G10 |
| 2 | A|H|P|M | 1.20 [1.05,1.43] | +67.9k (142.4k) | +39.4k (48.1k) | +37.9k (42.4k) | +0.6k (23.9k) | +6.4k (29.0k) | +11.9k (21.6k) [-4.7k,+33.1k] | CANDIDATE-RECENT | G4,G6,G9 |
| 3 | A|H|PL|M | 1.28 [1.11,1.55] | +91.9k (206.0k) | +38.8k (66.3k) | +31.1k (59.2k) | +14.3k (24.3k) | +14.6k (31.6k) | +19.5k (24.7k) [+0.8k,+45.3k] | CANDIDATE-RECENT | G6,G9 |
| 4 | A|H|EPL|M | 1.29 [1.10,1.56] | +83.5k (208.0k) | +38.7k (64.0k) | +28.9k (57.8k) | +18.3k (25.0k) | +15.4k (30.5k) | +21.7k (24.7k) [+2.3k,+46.5k] | CANDIDATE-RECENT | G6,G9,G10 |
| 5 | G|ADDUW|B1_PRE#1022 | 1.45 [1.13,1.86] | +45.7k (63.0k) | +29.2k (42.3k) | +27.5k (38.8k) | +50.4k (38.2k) | -27.9k (37.4k) | +44.5k (29.4k) [+11.1k,+85.7k] | CANDIDATE-RECENT | G2,G6,G8,G10 |
| 6 | A|H|EL|N | 1.18 [1.00,1.43] | +78.4k (102.1k) | +26.3k (49.0k) | +18.5k (45.7k) | +25.3k (18.3k) | +5.5k (17.0k) | +23.5k (18.8k) [+2.2k,+51.8k] | CANDIDATE | G10 |
| 7 | A|H|E|N | 1.06 [0.98,1.17] | +20.5k (43.8k) | +22.6k (16.4k) | +22.6k (16.0k) | +7.7k (11.4k) | +3.3k (8.8k) | +12.3k (9.5k) [+2.5k,+24.8k] | CANDIDATE | G10 |
| 8 | C|D|D_L20s | 1.46 [1.18,1.76] | +80.7k (148.1k) | +17.3k (57.7k) | +12.9k (53.4k) | -10.3k (32.2k) | -21.1k (34.5k) | -1.7k (27.5k) [-24.6k,+24.3k] | CANDIDATE-RECENT | G2,G3,G4,G6,G8,G9,G10 |
| 9 | A|H|L|N | 1.15 [0.97,1.38] | +74.6k (96.8k) | +15.7k (41.0k) | +11.3k (39.9k) | +19.0k (17.8k) | +4.1k (17.7k) | +16.8k (17.4k) [-1.7k,+42.0k] | CANDIDATE-RECENT | G3,G4,G5,G8,G9 |
| 10 | C|A|A05 | 1.14 [1.01,1.30] | +20.3k (51.2k) | +15.1k (24.4k) | +11.4k (22.8k) | +13.1k (16.1k) | -10.0k (13.7k) | +12.7k (13.3k) [-0.6k,+28.0k] | CANDIDATE-RECENT | G2,G4,G6,G8,G9,G10 |
| 11 | A|H|EL|M | 1.14 [0.99,1.32] | +63.3k (74.0k) | +15.0k (39.8k) | +7.9k (37.3k) | +23.7k (17.8k) | +4.5k (16.0k) | +19.2k (16.9k) [+5.1k,+37.0k] | CANDIDATE | G5,G9,G10 |
| 12 | A|H|E|M | 1.00 [0.94,1.10] | +19.5k (41.7k) | +13.4k (14.5k) | +11.6k (14.0k) | +7.8k (11.3k) | +2.8k (8.4k) | +9.0k (9.0k) [+2.0k,+18.0k] | CANDIDATE | G9,G10 |
| 13 | C|A|A04 | 1.29 [1.09,1.55] | +50.7k (61.4k) | +13.3k (29.4k) | +7.5k (29.0k) | +29.3k (21.9k) | -0.1k (24.6k) | +22.7k (17.9k) [+4.2k,+46.1k] | CANDIDATE-RECENT | G2,G3,G5,G6,G8,G10 |
| 14 | G|ADDUW|B2_PRE#5 | 1.06 [0.95,1.20] | +4.1k (28.1k) | +11.6k (17.7k) | +9.5k (15.9k) | +9.5k (15.9k) | +5.7k (9.9k) | +9.4k (12.2k) [-2.2k,+23.8k] | CANDIDATE | G4,G6,G8,G9,G10 |
| 15 | C|F|A06+HM5R+B02 | 1.38 [1.11,1.83] | +30.2k (116.4k) | +11.4k (40.6k) | +6.4k (38.5k) | +34.9k (28.5k) | -5.1k (27.9k) | +26.5k (23.4k) [+2.8k,+64.2k] | CANDIDATE-RECENT | G2,G3,G5,G6,G8,G9,G10 |
| 16 | C|F|A06+B02 | 1.23 [1.11,1.38] | +14.2k (33.3k) | +10.3k (21.6k) | +8.0k (20.9k) | +24.1k (15.7k) | -3.3k (15.2k) | +18.9k (12.9k) [+6.0k,+34.6k] | CANDIDATE-RECENT | G2,G3,G5,G6,G8,G10 |
| 17 | C|F|A06+HM5R | 1.30 [1.03,1.74] | +27.8k (117.7k) | +9.4k (37.8k) | +4.4k (35.7k) | +29.6k (27.4k) | -8.7k (27.5k) | +22.4k (22.3k) [-2.2k,+60.2k] | CANDIDATE-RECENT | G2,G3,G4,G5,G6,G8,G9,G10 |
| 18 | C|F|C1 | 1.22 [1.08,1.35] | +14.4k (19.6k) | +8.5k (17.5k) | +10.6k (17.2k) | +2.2k (11.8k) | -3.4k (14.0k) | +4.2k (9.8k) [-6.4k,+14.2k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 19 | E|SL|PB|NY|P1+N3 | 1.07 [1.03,1.12] | +9.0k (5.2k) | +8.1k (7.8k) | +7.2k (7.2k) | +1.4k (4.7k) | +0.1k (6.8k) | +3.1k (4.0k) [-1.0k,+7.9k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 20 | C|D|D_L30s | 1.18 [1.02,1.37] | +36.9k (63.2k) | +8.1k (33.0k) | +5.1k (30.0k) | -8.5k (18.2k) | -13.1k (19.6k) | -3.8k (15.7k) [-18.2k,+13.0k] | CANDIDATE-RECENT | G2,G3,G4,G5,G6,G8,G9,G10 |
| 21 | C|F|HM5R+B02 | 1.24 [1.08,1.51] | +18.2k (77.4k) | +8.0k (30.5k) | +5.6k (28.5k) | +14.0k (20.6k) | +4.8k (20.5k) | +11.3k (16.9k) [-4.4k,+34.7k] | CANDIDATE-RECENT | G3,G4,G5,G6,G8,G9,G10 |
| 22 | E|SL|PB|NY|P1 | 1.07 [1.02,1.11] | +8.9k (5.3k) | +7.8k (7.8k) | +6.7k (7.1k) | +1.4k (4.7k) | -0.3k (6.6k) | +3.0k (4.0k) [-0.8k,+7.5k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 23 | C|A|A08 | 1.04 [0.99,1.11] | +24.3k (41.7k) | +7.7k (13.4k) | +6.1k (12.5k) | -2.3k (9.0k) | +0.8k (8.4k) | +0.0k (7.4k) [-6.2k,+6.9k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 24 | F|CW|SM | 1.00 [0.95,1.05] | +3.2k (32.3k) | +7.5k (12.3k) | +5.6k (11.6k) | -1.9k (9.8k) | +2.1k (9.6k) | +0.4k (7.8k) [-6.2k,+6.2k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 25 | E|SL|PB|NY|P1+L2 | 1.07 [1.03,1.11] | +9.0k (5.2k) | +7.2k (8.0k) | +6.4k (7.3k) | +1.6k (4.7k) | -0.2k (6.0k) | +3.1k (4.0k) [-1.0k,+7.7k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 26 | C|A|A06 | 1.16 [1.07,1.29] | +11.6k (30.8k) | +6.6k (17.6k) | +3.4k (16.4k) | +18.9k (12.8k) | -7.6k (12.4k) | +14.4k (10.5k) [+4.5k,+27.7k] | CANDIDATE-RECENT | G2,G3,G5,G6,G8,G10 |
| 27 | E|SL|PB|NY|G1k70 | 1.06 [1.02,1.10] | +9.2k (5.6k) | +6.4k (7.5k) | +5.5k (6.7k) | +1.5k (4.4k) | +1.1k (5.9k) | +2.7k (3.7k) [-1.0k,+7.3k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 28 | C|A|A03 | 1.02 [1.00,1.06] | +5.0k (14.0k) | +6.3k (6.2k) | +5.4k (5.7k) | +3.1k (3.4k) | -0.4k (2.8k) | +3.7k (2.9k) [+1.3k,+7.2k] | CANDIDATE-RECENT | G2,G5,G6,G8,G10 |
| 29 | H|L2SP|ALL_PRE_selected|M | 1.15 [1.07,1.25] | +18.1k (56.9k) | +6.1k (23.2k) | +5.1k (20.7k) | +4.0k (13.5k) | +1.9k (16.1k) | +4.3k (11.3k) [-4.1k,+13.4k] | CANDIDATE-RECENT | G4,G5,G6,G8,G9,G10 |
| 30 | E|SL|PB|NY|P1+L1 | 1.07 [1.02,1.11] | +4.5k (8.8k) | +6.1k (8.7k) | +5.3k (8.1k) | -0.8k (5.1k) | -1.3k (8.7k) | +1.1k (4.4k) [-3.5k,+5.5k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 31 | E|SL|PB|NY|P1+L1.5 | 1.06 [1.01,1.11] | +5.4k (10.4k) | +5.9k (7.7k) | +4.9k (7.2k) | +0.9k (4.9k) | -1.4k (6.8k) | +2.1k (4.1k) [-2.3k,+6.8k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 32 | C|F|HM5R | 1.16 [1.01,1.43] | +15.9k (81.5k) | +5.6k (28.0k) | +3.2k (26.0k) | +9.8k (20.5k) | +0.8k (19.8k) | +7.9k (16.4k) [-7.6k,+32.4k] | CANDIDATE-RECENT | G3,G4,G5,G6,G8,G9,G10 |
| 33 | C|F|HM5M | 1.11 [1.03,1.23] | +9.8k (38.1k) | +5.5k (13.1k) | +3.6k (12.7k) | +6.5k (9.7k) | +1.1k (9.6k) | +5.6k (7.8k) [-2.4k,+16.1k] | CANDIDATE-RECENT | G3,G4,G5,G6,G8,G9,G10 |
| 34 | C|D|D_B4s | 1.12 [1.02,1.23] | +19.2k (40.5k) | +5.5k (20.5k) | +3.5k (18.6k) | +0.2k (13.6k) | -8.5k (12.8k) | +1.5k (11.1k) [-8.5k,+12.1k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 35 | C|D|D_L40s | 1.06 [1.02,1.14] | +12.8k (21.1k) | +5.2k (7.9k) | +3.6k (7.7k) | +5.1k (6.1k) | -3.4k (7.4k) | +4.7k (4.9k) [+0.3k,+11.4k] | CANDIDATE-RECENT | G2,G5,G6,G8,G9,G10 |
| 36 | C|D|D_B2s | 1.53 [1.17,1.93] | +65.3k (194.0k) | +5.0k (64.1k) | +3.5k (59.5k) | -16.1k (37.5k) | -17.3k (38.2k) | -8.5k (31.6k) [-34.6k,+18.4k] | CANDIDATE-RECENT | G2,G3,G4,G5,G6,G8,G9,G10 |
| 37 | E|SL|PB|NY|P1.5+N2 | 1.04 [1.01,1.08] | +6.7k (8.2k) | +4.9k (5.5k) | +4.5k (5.4k) | +0.2k (4.1k) | -1.6k (5.6k) | +1.5k (3.4k) [-1.7k,+5.5k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 38 | E|SL|PB|London|P1.5+N1 | 1.08 [1.01,1.14] | +9.4k (32.6k) | +4.9k (10.1k) | +4.3k (9.1k) | +6.5k (7.3k) | +4.4k (8.4k) | +5.9k (5.8k) [-0.5k,+12.2k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 39 | E|SL|PB|NY|G1k50 | 1.04 [1.01,1.08] | +8.5k (6.9k) | +4.8k (7.1k) | +4.1k (6.4k) | +2.6k (4.0k) | +1.4k (4.7k) | +3.1k (3.4k) [-0.2k,+6.8k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 40 | E|SL|PB|NY|P1+N1 | 1.05 [1.01,1.09] | +1.9k (8.8k) | +4.3k (7.3k) | +3.6k (6.9k) | -0.7k (4.9k) | -3.0k (9.2k) | +0.6k (4.1k) [-3.4k,+4.7k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 41 | E|SL|PB|London|P3+N1 | 1.07 [1.00,1.12] | +3.9k (27.9k) | +4.1k (8.1k) | +3.9k (7.4k) | +5.9k (6.1k) | +2.1k (6.2k) | +5.3k (4.8k) [-0.7k,+11.4k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 42 | C|F|B02 | 1.06 [1.01,1.11] | +2.2k (10.3k) | +3.7k (8.4k) | +4.3k (9.0k) | +3.9k (6.3k) | +4.3k (8.0k) | +3.6k (5.0k) [-1.0k,+8.8k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 43 | E|SL|PB|London|P2+N1 | 1.07 [1.00,1.14] | +6.6k (32.2k) | +3.6k (9.3k) | +3.5k (8.4k) | +6.6k (6.1k) | +2.9k (6.6k) | +5.7k (5.0k) [+0.1k,+12.2k] | CANDIDATE | G5,G6,G8,G9,G10 |
| 44 | E|SL|PS|London|P1+N3 | 1.03 [1.00,1.06] | +14.4k (17.7k) | +3.5k (6.9k) | +3.2k (6.2k) | -0.6k (4.2k) | +0.1k (4.9k) | +0.5k (3.5k) [-2.6k,+4.0k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 45 | E|SL|WT|NY|P2+N1 | 1.01 [0.98,1.05] | +5.8k (7.7k) | +3.3k (5.8k) | +3.0k (5.3k) | +0.9k (4.4k) | +2.0k (4.8k) | +1.5k (3.5k) [-2.5k,+5.3k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 46 | E|SL|PS|London|P1+N2 | 1.04 [1.01,1.07] | +9.0k (24.8k) | +3.0k (7.1k) | +2.8k (6.5k) | +0.5k (4.5k) | -0.0k (4.8k) | +1.2k (3.7k) [-2.3k,+4.7k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 47 | E|SL|PB|NY|P1.5 | 1.03 [1.00,1.06] | +3.7k (10.2k) | +2.9k (4.3k) | +2.4k (4.0k) | -0.9k (3.8k) | -1.3k (5.1k) | +0.1k (3.0k) [-2.7k,+3.2k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 48 | E|SL|PS|NY|P1.5+L1 | 1.02 [1.00,1.04] | +6.8k (11.7k) | +2.8k (4.8k) | +2.2k (4.6k) | +0.1k (2.8k) | -0.4k (4.0k) | +0.7k (2.4k) [-1.3k,+3.0k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 49 | E|SL|WT|NY|P2 | 1.02 [1.00,1.03] | +4.5k (5.9k) | +2.6k (3.1k) | +2.4k (2.8k) | +1.1k (2.0k) | +0.4k (2.5k) | +1.5k (1.6k) [+0.0k,+3.2k] | CANDIDATE | G5,G6,G8,G9,G10 |
| 50 | E|SL|PB|NY|P1.5+L2 | 1.03 [1.00,1.07] | +4.8k (9.2k) | +2.5k (4.9k) | +2.2k (4.6k) | -0.8k (3.9k) | -1.0k (4.8k) | +0.1k (3.1k) [-3.0k,+3.6k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 51 | E|SL|HM|NY|P1.5+L1.5 | 1.03 [0.99,1.06] | +6.9k (22.4k) | +2.4k (10.0k) | +2.6k (9.3k) | +0.2k (5.2k) | +0.8k (7.2k) | +1.0k (4.6k) [-3.3k,+5.3k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 52 | F|CW|WT | 1.02 [0.94,1.08] | -13.3k (30.6k) | +2.3k (11.5k) | -0.7k (12.9k) | -0.1k (9.1k) | -4.7k (9.9k) | -0.3k (7.5k) [-7.3k,+5.9k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 53 | E|SL|PS|NY|P2+N1 | 1.02 [0.99,1.04] | +6.4k (13.0k) | +2.3k (5.0k) | +1.7k (4.6k) | -0.2k (3.2k) | +0.4k (4.5k) | +0.4k (2.7k) [-2.3k,+2.5k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 54 | E|SL|PS|NY|P2+L1 | 1.02 [1.00,1.04] | +4.8k (13.5k) | +2.1k (4.4k) | +1.6k (4.1k) | +0.4k (2.6k) | +0.1k (3.6k) | +0.8k (2.2k) [-1.1k,+2.9k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 55 | C|A|A09 | 1.03 [0.99,1.08] | -1.7k (31.2k) | +2.0k (9.9k) | +1.0k (8.8k) | -2.1k (6.6k) | -0.7k (4.7k) | -1.2k (5.4k) [-5.8k,+4.2k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 56 | E|SL|PB|NY|P2 | 1.02 [1.00,1.04] | +2.8k (7.3k) | +2.0k (3.1k) | +1.5k (2.9k) | -0.4k (3.0k) | -1.0k (3.8k) | +0.1k (2.3k) [-2.1k,+2.6k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 57 | E|SL|PB|NY|G2k70 | 1.01 [1.00,1.03] | +2.7k (5.1k) | +1.6k (2.4k) | +1.1k (2.3k) | -0.3k (2.4k) | +0.4k (2.4k) | +0.1k (1.9k) [-1.6k,+2.2k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 58 | E|SL|PB|NY|P2+L2 | 1.02 [1.00,1.05] | +3.8k (6.7k) | +1.5k (4.0k) | +1.2k (3.6k) | -0.3k (3.2k) | -0.8k (3.5k) | +0.2k (2.5k) [-2.1k,+2.7k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 59 | A|H|L|M | 1.09 [0.96,1.27] | +55.8k (67.6k) | +1.4k (33.0k) | -4.0k (30.5k) | +11.7k (14.8k) | +2.9k (15.8k) | +7.0k (14.0k) [-4.5k,+22.2k] | DEAD | G1,G3,G4,G5,G8,G9 |
| 60 | C|D|D_L30t | 1.11 [0.98,1.28] | +9.5k (37.5k) | +1.4k (23.7k) | +0.5k (21.4k) | -3.8k (14.0k) | -10.9k (15.3k) | -2.1k (11.7k) [-13.7k,+11.7k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 61 | E|SL|PS|NY|P3+N1 | 1.02 [0.99,1.04] | +2.1k (13.0k) | +1.2k (4.1k) | +0.9k (3.8k) | +0.5k (3.2k) | +0.4k (4.5k) | +0.6k (2.5k) [-1.8k,+2.7k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 62 | E|SL|KB|Asia|P3+L2 | 1.00 [1.00,1.01] | +4.0k (10.8k) | +1.0k (3.2k) | +0.8k (2.8k) | +1.2k (2.8k) | -0.1k (0.3k) | +1.1k (2.1k) [-0.4k,+2.7k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 63 | E|SL|PS|NY|G2k70 | 1.00 [1.00,1.01] | +3.1k (10.8k) | +0.9k (3.0k) | +0.8k (2.6k) | +0.1k (1.0k) | +0.6k (1.2k) | +0.3k (1.0k) [-0.4k,+1.2k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 64 | E|SL|KB|Asia|P3 | 1.00 [1.00,1.00] | +3.9k (10.9k) | +0.8k (2.3k) | +0.7k (2.0k) | +0.6k (2.1k) | +0.0k (0.0k) | +0.6k (1.6k) [-0.3k,+1.9k] | CANDIDATE | G4,G5,G6,G8,G9,G10 |
| 65 | E|SL|WT|Asia|P1+L1 | 1.03 [0.97,1.07] | -7.3k (22.2k) | +0.5k (9.1k) | +0.7k (8.6k) | +2.1k (6.9k) | +1.2k (4.5k) | +1.7k (5.5k) [-3.8k,+6.8k] | DEAD | G1,G3,G4,G5,G6,G8,G9,G10 |
| 66 | B|L2SL|HM_PRE | 1.04 [0.95,1.14] | +1.1k (29.5k) | +0.4k (13.2k) | -1.2k (13.2k) | +5.4k (9.7k) | -2.5k (8.6k) | +3.4k (8.0k) [-5.0k,+12.8k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| 67 | E|SL|HM|NY|P1+L1.5 | 1.03 [0.99,1.08] | +4.2k (21.6k) | +0.4k (13.0k) | +1.6k (11.8k) | +0.7k (6.4k) | -0.6k (9.9k) | +1.0k (5.7k) [-4.0k,+6.9k] | CANDIDATE-RECENT | G2,G3,G4,G5,G6,G8,G9,G10 |
| 68 | E|SL|PB|London|P3+L1.5 | 1.03 [0.98,1.07] | +2.2k (18.1k) | +0.4k (5.1k) | +0.3k (4.6k) | +2.4k (3.6k) | +1.5k (2.6k) | +1.8k (2.9k) [-2.1k,+6.0k] | CANDIDATE-RECENT | G3,G4,G5,G6,G8,G9,G10 |
| 69 | E|SL|PS|NY|P3+L2 | 1.00 [1.00,1.01] | +0.0k (3.2k) | +0.3k (1.3k) | +0.2k (1.1k) | -0.0k (1.1k) | -0.1k (1.6k) | +0.1k (0.8k) [-0.8k,+1.0k] | CANDIDATE-RECENT | G2,G4,G5,G6,G8,G9,G10 |
| 70 | C|D|D_B3s | 1.19 [0.98,1.44] | +22.8k (77.5k) | +0.2k (34.4k) | -1.4k (31.1k) | -8.3k (23.7k) | -11.6k (24.3k) | -5.6k (19.1k) [-23.3k,+14.3k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 71 | C|A|A01 | 0.99 [0.93,1.05] | -3.0k (19.6k) | +0.1k (8.6k) | +0.9k (7.6k) | -0.3k (5.9k) | -0.9k (4.7k) | +0.0k (4.8k) [-5.7k,+5.4k] | DEAD | G1,G2,G4,G5,G6,G8,G9,G10 |
| 72 | E|SL|PS|NY|P3+L1.5 | 1.01 [0.99,1.03] | -0.7k (4.5k) | -0.1k (2.2k) | -0.3k (2.0k) | +0.5k (1.6k) | -0.9k (2.7k) | +0.3k (1.3k) [-1.4k,+1.7k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 73 | E|SL|PS|NY|L2 | 1.00 [0.99,1.01] | -0.2k (2.5k) | -0.1k (1.3k) | -0.1k (1.1k) | -0.3k (0.9k) | -0.1k (1.5k) | -0.3k (0.7k) [-0.9k,+0.4k] | DEAD | G1,G2,G4,G5,G6,G8,G9,G10 |
| 74 | B|EXP2|B_U3 | 1.02 [0.97,1.06] | -9.0k (20.0k) | -0.3k (9.0k) | -0.5k (8.0k) | +5.5k (7.6k) | -1.0k (6.3k) | +3.7k (5.9k) [-1.0k,+9.3k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 75 | C|A|A07 | 1.01 [0.93,1.10] | -9.0k (43.8k) | -0.3k (18.8k) | -1.7k (16.7k) | -3.4k (8.7k) | -1.2k (8.0k) | -2.8k (7.9k) [-10.4k,+5.6k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 76 | C|D|D_B3e | 1.14 [0.96,1.38] | +8.3k (67.8k) | -0.5k (30.8k) | -1.9k (28.3k) | -11.5k (21.5k) | -16.4k (21.6k) | -7.8k (17.2k) [-23.5k,+11.6k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 77 | E|SL|ST|Asia|P1.5+N3 | 1.01 [0.98,1.05] | +18.4k (57.5k) | -0.6k (14.6k) | -0.5k (12.8k) | +3.4k (5.7k) | +0.7k (1.5k) | +2.2k (5.5k) [-2.5k,+7.3k] | DEAD | G1,G3,G4,G5,G6,G8,G9,G10 |
| 78 | B|EXP2|P | 0.98 [0.82,1.14] | +23.1k (62.4k) | -0.7k (18.5k) | -5.6k (27.9k) | -6.5k (15.3k) | -17.8k (20.7k) | -6.3k (13.7k) [-20.5k,+7.8k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 79 | B|L2SL|SM_PRE | 0.98 [0.93,1.02] | -1.9k (12.9k) | -1.2k (4.9k) | -1.3k (4.5k) | -2.3k (3.8k) | +1.0k (2.2k) | -2.1k (3.0k) [-6.5k,+1.2k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| 80 | E|SL|PS|London|N2 | 1.00 [0.98,1.02] | -7.5k (13.3k) | -1.2k (3.3k) | -0.9k (2.9k) | +0.8k (2.1k) | -0.2k (0.9k) | +0.3k (1.7k) [-1.6k,+1.9k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 81 | A|H|EP|N | 1.11 [0.94,1.35] | +38.4k (154.8k) | -1.5k (51.4k) | -1.5k (44.9k) | -25.8k (25.6k) | -5.3k (28.1k) | -18.8k (22.7k) [-38.1k,+3.9k] | DEAD | G1,G2,G4,G5,G6,G8,G9,G10 |
| 82 | E|SL|ST|NY|N2 | 1.02 [0.99,1.04] | +3.1k (14.2k) | -1.7k (8.6k) | -1.4k (7.6k) | +1.4k (3.3k) | -2.9k (4.4k) | +0.6k (3.2k) [-2.6k,+3.7k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 83 | E|SL|ST|NY|P3+N2 | 1.02 [0.99,1.05] | -0.4k (20.8k) | -2.6k (9.4k) | -2.5k (8.3k) | +1.5k (3.6k) | -2.6k (4.2k) | +0.3k (3.6k) [-3.2k,+3.9k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 84 | B|EXP2|B_U3_P | 0.98 [0.81,1.15] | +13.8k (72.1k) | -2.7k (20.4k) | -7.9k (29.2k) | -3.3k (17.1k) | -19.7k (21.6k) | -4.7k (14.9k) [-21.1k,+11.3k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 85 | E|SL|ST|Asia|P1.5+L2 | 1.01 [0.98,1.04] | +4.5k (34.4k) | -2.9k (10.4k) | -2.6k (9.1k) | +2.8k (5.7k) | +0.7k (1.5k) | +1.2k (4.9k) [-3.3k,+5.8k] | DEAD | G1,G3,G4,G5,G6,G8,G9,G10 |
| 86 | B|L2SL|KB_PRE | 0.97 [0.93,1.01] | +2.7k (6.6k) | -3.2k (5.6k) | -2.6k (5.0k) | -5.3k (3.9k) | -2.3k (3.3k) | -4.5k (3.2k) [-8.6k,-1.2k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| 87 | A|H|P|N | 1.10 [0.92,1.34] | +29.6k (157.5k) | -3.5k (49.8k) | -1.8k (43.8k) | -29.0k (25.3k) | -5.1k (27.8k) | -21.0k (22.4k) [-38.8k,+0.6k] | DEAD | G1,G2,G4,G5,G6,G8,G9 |
| 88 | F|CW|HM | 1.03 [0.95,1.13] | +12.6k (46.3k) | -3.5k (24.7k) | -5.3k (23.2k) | +4.5k (12.9k) | +4.5k (14.7k) | +1.6k (11.5k) [-7.6k,+11.8k] | DEAD | G1,G3,G4,G5,G6,G8,G9,G10 |
| 89 | C|D|D_B3h | 1.17 [1.01,1.31] | +3.6k (47.0k) | -4.0k (26.6k) | -6.6k (24.9k) | -0.9k (19.1k) | -9.9k (19.0k) | -1.8k (15.2k) [-16.1k,+12.8k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 90 | B|L2SL|WT_PRE | 0.98 [0.94,1.01] | -12.5k (24.1k) | -4.5k (6.0k) | -4.4k (5.2k) | -4.5k (3.3k) | +1.5k (2.8k) | -4.5k (2.8k) [-8.2k,-2.0k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| 91 | B|L2SL|PE_PRE | 1.01 [0.97,1.05] | -4.6k (12.1k) | -4.6k (8.2k) | -3.6k (7.7k) | +2.3k (5.5k) | -1.2k (5.7k) | +0.5k (4.5k) [-4.0k,+4.9k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| 92 | B|L2SL|ST_PRE | 1.03 [0.95,1.10] | +24.5k (44.4k) | -5.5k (20.2k) | -4.5k (17.7k) | -0.3k (5.9k) | -5.3k (8.3k) | -1.6k (6.8k) [-8.7k,+5.4k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| 93 | H|L2SP|ALL_PRE_selected|N | 1.09 [0.96,1.20] | +6.5k (57.7k) | -5.5k (22.5k) | -5.9k (20.0k) | -5.0k (12.8k) | -2.9k (16.3k) | -5.3k (10.8k) [-17.6k,+5.0k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 94 | A|H|EPL|N | 1.19 [1.00,1.44] | +48.7k (219.7k) | -5.9k (64.0k) | -11.4k (56.2k) | -12.5k (25.3k) | +3.3k (28.6k) | -12.3k (24.5k) [-33.3k,+12.0k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 95 | E|SL|ST|Asia|P1.5+N2 | 1.02 [0.98,1.05] | +3.5k (30.2k) | -6.7k (13.1k) | -6.0k (11.5k) | +4.5k (6.2k) | +0.7k (1.6k) | +1.4k (5.7k) [-3.6k,+5.9k] | DEAD | G1,G3,G4,G5,G6,G8,G9,G10 |
| 96 | C|A|A02 | 1.13 [0.96,1.32] | -6.2k (63.5k) | -7.0k (38.1k) | -5.1k (35.8k) | +8.1k (21.6k) | -17.5k (21.5k) | +4.3k (18.7k) [-13.2k,+23.2k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 97 | F|CW|ST | 1.10 [0.99,1.22] | +12.7k (46.2k) | -7.1k (24.5k) | -6.6k (22.9k) | +3.0k (15.9k) | -4.0k (17.1k) | +0.1k (13.2k) [-10.5k,+12.1k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 98 | A|H|PL|N | 1.17 [0.99,1.44] | +49.6k (224.1k) | -7.5k (65.9k) | -10.9k (57.6k) | -17.4k (25.3k) | +2.1k (29.2k) | -15.6k (24.8k) [-35.1k,+9.8k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| 99 | B|EXP2|B_FROZEN_P | 1.20 [0.88,1.58] | -8.4k (90.8k) | -9.4k (76.5k) | -3.1k (74.1k) | -7.9k (38.8k) | -1.7k (41.4k) | -6.5k (35.2k) [-36.9k,+27.8k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 100 | F|CW|PE | 1.10 [1.01,1.18] | -1.3k (34.4k) | -11.3k (23.2k) | -8.8k (21.0k) | +3.7k (14.3k) | +3.7k (15.4k) | -0.0k (12.0k) [-9.3k,+9.4k] | DEAD | G1,G3,G4,G5,G6,G8,G9,G10 |
| 101 | D|D6L_alone | 1.18 [0.91,1.51] | +72.1k (123.8k) | -12.0k (61.9k) | -8.5k (57.7k) | -30.3k (34.4k) | -17.9k (37.0k) | -24.0k (30.0k) [-44.9k,-3.2k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 102 | B|L2SL|ALL_PRE | 1.07 [0.90,1.27] | +23.6k (24.8k) | -15.8k (32.1k) | -15.2k (28.1k) | -7.2k (14.1k) | -13.6k (15.7k) | -9.7k (13.0k) [-22.8k,+5.3k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| 103 | D|PROFIT_alone | 0.98 [0.84,1.16] | +27.9k (110.4k) | -16.3k (38.3k) | -16.3k (37.7k) | -9.8k (22.2k) | -1.1k (23.8k) | -11.9k (19.4k) [-26.5k,+3.3k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 104 | B|L2SL|COMBO_PRE | 1.03 [0.90,1.17] | +9.7k (30.0k) | -17.8k (23.6k) | -17.1k (21.4k) | -4.5k (13.7k) | -8.3k (14.3k) | -8.4k (11.7k) [-20.2k,+3.8k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| 105 | B|EXP2|B_FROZEN | 1.01 [0.75,1.33] | -13.1k (112.7k) | -19.6k (71.4k) | -14.5k (68.9k) | -25.2k (38.7k) | -1.5k (42.5k) | -22.2k (34.2k) [-48.4k,+8.4k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 106 | B|EXP2|B_U3_L | 1.05 [0.85,1.26] | -20.0k (75.3k) | -23.6k (37.3k) | -19.7k (35.1k) | -3.6k (27.2k) | -17.1k (23.2k) | -8.5k (22.0k) [-27.3k,+11.9k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 107 | B|EXP2|L | 1.06 [0.84,1.25] | -17.6k (71.5k) | -24.0k (34.5k) | -19.5k (32.5k) | -8.3k (26.7k) | -14.5k (21.5k) | -11.8k (21.3k) [-31.2k,+7.1k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 108 | B|EXP2|B_U1_P | 1.01 [0.76,1.23] | -6.6k (183.2k) | -25.9k (61.9k) | -22.2k (57.1k) | -28.5k (35.0k) | -14.7k (36.0k) | -26.8k (30.0k) [-51.5k,-3.2k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 109 | F|CW|KB | 0.97 [0.84,1.11] | +0.5k (68.7k) | -27.0k (32.0k) | -26.1k (27.6k) | -5.8k (16.7k) | +3.8k (16.7k) | -12.0k (14.6k) [-24.5k,+0.0k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 110 | B|EXP2|B_U1 | 0.92 [0.72,1.09] | -39.1k (148.5k) | -29.1k (59.4k) | -27.6k (54.5k) | -35.4k (32.7k) | -8.3k (37.5k) | -33.4k (28.2k) [-55.2k,-12.3k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 111 | B|EXP2|B_U3_P_L | 1.02 [0.79,1.24] | -10.0k (53.8k) | -29.2k (31.8k) | -30.7k (37.7k) | -9.8k (27.2k) | -29.1k (27.9k) | -16.2k (22.4k) [-36.8k,+3.4k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 112 | B|EXP2|P_L | 1.03 [0.80,1.26] | -7.3k (47.8k) | -29.4k (29.5k) | -30.3k (36.0k) | -12.5k (27.2k) | -26.9k (28.8k) | -18.0k (22.1k) [-38.3k,+1.8k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 113 | D|JOINT3 | 1.31 [0.99,1.64] | +47.2k (119.1k) | -30.9k (63.1k) | -25.8k (63.2k) | -45.0k (40.6k) | -12.4k (42.4k) | -39.6k (34.5k) [-61.1k,-17.7k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 114 | D|JOINT10 | 1.31 [1.00,1.65] | +47.2k (119.1k) | -31.2k (63.3k) | -26.1k (63.3k) | -45.0k (40.6k) | -12.0k (42.4k) | -39.8k (34.6k) [-60.5k,-17.6k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 115 | D|JOINT20 | 1.34 [1.06,1.65] | +46.7k (119.4k) | -32.1k (64.3k) | -27.7k (64.0k) | -42.3k (39.6k) | -10.0k (42.7k) | -38.3k (34.1k) [-59.1k,-16.3k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 116 | D|LOSS20_alone | 1.05 [0.89,1.22] | -4.5k (87.8k) | -32.8k (41.2k) | -28.1k (37.1k) | -35.4k (29.0k) | +1.4k (33.3k) | -33.6k (23.3k) [-48.8k,-18.2k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 117 | D|LOSS10_alone | 1.05 [0.89,1.20] | -3.3k (87.6k) | -32.9k (41.6k) | -28.5k (37.8k) | -34.5k (28.9k) | +1.1k (33.4k) | -33.0k (23.4k) [-48.7k,-16.9k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 118 | B|EXP2|B_U2_P | 0.96 [0.68,1.24] | -44.5k (156.2k) | -33.4k (54.5k) | -28.0k (55.1k) | -30.9k (36.9k) | -18.8k (35.9k) | -30.3k (30.8k) [-54.0k,-2.9k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 119 | D|LOSS3_alone | 1.05 [0.89,1.20] | -3.2k (87.5k) | -34.0k (42.3k) | -29.3k (38.5k) | -35.4k (28.9k) | +0.9k (33.6k) | -33.9k (23.5k) [-50.5k,-17.9k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 120 | B|EXP2|B_U2 | 0.94 [0.69,1.19] | -45.2k (156.6k) | -34.0k (56.6k) | -29.6k (54.7k) | -29.3k (35.8k) | -15.2k (35.8k) | -29.7k (30.1k) [-53.1k,-5.8k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 121 | F|CW|ALL6 | 1.20 [0.88,1.52] | +16.0k (203.4k) | -47.2k (68.1k) | -50.2k (62.1k) | +1.4k (39.0k) | +6.3k (47.1k) | -14.2k (33.8k) [-40.3k,+12.6k] | DEAD | G1,G3,G4,G5,G6,G8,G9,G10 |
| 122 | C|A|A10 | 0.87 [0.66,1.11] | -25.5k (60.6k) | -51.7k (48.4k) | -40.7k (55.8k) | -51.1k (32.4k) | -9.7k (38.8k) | -46.6k (28.1k) [-65.9k,-26.4k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 123 | B|EXP2|B_U2_L | 0.85 [0.63,1.05] | -86.1k (116.6k) | -55.0k (43.6k) | -48.1k (44.8k) | -45.3k (34.0k) | -32.7k (38.6k) | -46.6k (27.5k) [-66.9k,-28.2k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 124 | B|EXP2|B_U2_P_L | 0.84 [0.62,1.08] | -91.1k (110.5k) | -55.7k (43.2k) | -49.9k (46.2k) | -43.4k (35.4k) | -32.8k (39.0k) | -45.8k (28.5k) [-66.4k,-24.9k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 125 | B|EXP2|B_U1_L | 0.90 [0.66,1.13] | -70.8k (110.4k) | -58.0k (50.4k) | -50.8k (48.1k) | -50.2k (34.8k) | -32.8k (38.8k) | -50.8k (28.4k) [-70.8k,-31.3k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 126 | B|EXP2|B_FROZEN_P_L | 0.89 [0.64,1.18] | -55.8k (70.9k) | -61.7k (56.8k) | -53.3k (57.4k) | -50.1k (36.6k) | -31.7k (41.9k) | -51.5k (31.0k) [-70.1k,-30.6k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 127 | B|EXP2|B_FROZEN_L | 0.84 [0.60,1.11] | -57.4k (81.8k) | -62.7k (55.8k) | -53.3k (56.6k) | -57.6k (36.5k) | -36.0k (42.3k) | -56.8k (30.8k) [-77.1k,-35.3k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |
| 128 | B|EXP2|B_U1_P_L | 0.91 [0.67,1.13] | -64.6k (101.9k) | -63.3k (48.7k) | -55.0k (48.6k) | -50.7k (34.8k) | -31.2k (40.1k) | -52.5k (28.5k) [-71.9k,-33.1k] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9,G10 |

## 3. Per-family verdict lines (L6M first, then HOLD, PRE; absolute means at the scale)
1. **A|B|E|N** (dip-entry (book-own best); looked(L6M-ranked)): at equal worst-20-weeks, A|B|E|N runs 1.43x lots (95% CI 1.15-1.85) and makes +90.3k $/wk more than the stack as it is in L6M (MDE 44.2k), +80.5k in HOLD, -6.7k in PRE; absolute L6M +151.7k vs stack +61.5k, HOLD +128.9k vs +48.3k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.70): rule +63.2k vs scaled stack in L6M (MDE +30.9k), +56.4k in HOLD. maxDD-matched c* 1.43 (L6M +89.9k, HOLD +80.2k); SD-matched c* 1.31 (L6M +77.7k, HOLD +69.9k). [CANDIDATE-RECENT]
2. **A|B|EPL|M** (joint entry+profit+loss; looked(L6M-ranked)): at equal worst-20-weeks, A|B|EPL|M runs 1.39x lots (95% CI 1.13-1.77) and makes +81.6k $/wk more than the stack as it is in L6M (MDE 62.6k), +76.4k in HOLD, -30.9k in PRE; absolute L6M +100.4k vs stack +18.8k, HOLD +85.0k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.72): rule +58.8k vs scaled stack in L6M (MDE +45.1k), +55.1k in HOLD. maxDD-matched c* 1.03 (L6M +55.9k, HOLD +54.7k); SD-matched c* 1.40 (L6M +82.7k, HOLD +77.3k). [CANDIDATE-RECENT]
3. **A|B|EL|N** (entry+loss; looked(L6M-ranked)): at equal worst-20-weeks, A|B|EL|N runs 1.38x lots (95% CI 1.09-1.78) and makes +79.7k $/wk more than the stack as it is in L6M (MDE 48.6k), +71.2k in HOLD, -36.3k in PRE; absolute L6M +141.2k vs stack +61.5k, HOLD +119.6k vs +48.3k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.72): rule +57.6k vs scaled stack in L6M (MDE +35.1k), +51.5k in HOLD. maxDD-matched c* 1.11 (L6M +51.5k, HOLD +47.3k); SD-matched c* 1.37 (L6M +78.2k, HOLD +69.9k). [CANDIDATE-RECENT]
4. **A|B|EP|M** (entry+profit; looked(L6M-ranked)): at equal worst-20-weeks, A|B|EP|M runs 1.44x lots (95% CI 1.16-1.82) and makes +79.3k $/wk more than the stack as it is in L6M (MDE 65.0k), +74.5k in HOLD, -5.0k in PRE; absolute L6M +98.1k vs stack +18.8k, HOLD +83.1k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.69): rule +55.2k vs scaled stack in L6M (MDE +45.0k), +51.8k in HOLD. maxDD-matched c* 1.50 (L6M +83.1k, HOLD +77.6k); SD-matched c* 1.31 (L6M +70.7k, HOLD +67.2k). [CANDIDATE-RECENT]
5. **A|B|E|M** (dip-entry (book-own best); looked(L6M-ranked)): at equal worst-20-weeks, A|B|E|M runs 1.37x lots (95% CI 1.14-1.75) and makes +79.3k $/wk more than the stack as it is in L6M (MDE 46.8k), +69.0k in HOLD, -4.8k in PRE; absolute L6M +98.1k vs stack +18.8k, HOLD +77.5k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.73): rule +58.0k vs scaled stack in L6M (MDE +34.3k), +50.5k in HOLD. maxDD-matched c* 1.05 (L6M +56.7k, HOLD +51.1k); SD-matched c* 1.26 (L6M +72.0k, HOLD +63.2k). [CANDIDATE-RECENT]
6. **A|B|EL|M** (entry+loss; looked(L6M-ranked)): at equal worst-20-weeks, A|B|EL|M runs 1.35x lots (95% CI 1.10-1.65) and makes +76.3k $/wk more than the stack as it is in L6M (MDE 51.4k), +67.5k in HOLD, -28.5k in PRE; absolute L6M +95.2k vs stack +18.8k, HOLD +76.1k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.74): rule +56.7k vs scaled stack in L6M (MDE +38.2k), +50.1k in HOLD. maxDD-matched c* 0.73 (L6M +33.0k, HOLD +32.8k); SD-matched c* 1.31 (L6M +73.9k, HOLD +65.6k). [CANDIDATE-RECENT]
7. **H|L2SP|ALL_L6M_rank1|M** (profit-health exits (L2SP six books); looked(L6M-ranked)): at equal worst-20-weeks, H|L2SP|ALL_L6M_rank1|M runs 1.20x lots (95% CI 0.95-1.45) and makes +56.4k $/wk more than the stack as it is in L6M (MDE 47.9k), +48.7k in HOLD, -14.0k in PRE; absolute L6M +82.8k vs stack +26.4k, HOLD +66.4k vs +17.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.84): rule +47.1k vs scaled stack in L6M (MDE +40.1k), +40.7k in HOLD. maxDD-matched c* 0.92 (L6M +37.0k, HOLD +33.1k); SD-matched c* 1.16 (L6M +53.5k, HOLD +46.4k). [CANDIDATE-RECENT]
8. **A|B|PL|M** (profit+loss; looked(L6M-ranked)): at equal worst-20-weeks, A|B|PL|M runs 1.15x lots (95% CI 0.98-1.41) and makes +53.0k $/wk more than the stack as it is in L6M (MDE 49.4k), +49.6k in HOLD, -15.8k in PRE; absolute L6M +71.8k vs stack +18.8k, HOLD +58.2k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.87): rule +46.0k vs scaled stack in L6M (MDE +42.8k), +43.0k in HOLD. maxDD-matched c* 1.40 (L6M +68.3k, HOLD +62.0k); SD-matched c* 1.11 (L6M +50.4k, HOLD +47.5k). [CANDIDATE-RECENT]
9. **A|H|EP|M** (entry+profit; PRE-selected): at equal worst-20-weeks, A|H|EP|M runs 1.22x lots (95% CI 1.06-1.48) and makes +43.9k $/wk more than the stack as it is in L6M (MDE 52.8k), +39.9k in HOLD, +4.3k in PRE; absolute L6M +62.7k vs stack +18.8k, HOLD +48.4k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.82): rule +36.0k vs scaled stack in L6M (MDE +43.3k), +32.8k in HOLD. maxDD-matched c* 1.32 (L6M +49.2k, HOLD +44.0k); SD-matched c* 1.15 (L6M +40.2k, HOLD +37.1k). [CANDIDATE-RECENT]
10. **A|B|EP|N** (entry+profit; looked(L6M-ranked)): at equal worst-20-weeks, A|B|EP|N runs 1.35x lots (95% CI 1.06-1.79) and makes +42.6k $/wk more than the stack as it is in L6M (MDE 58.7k), +40.9k in HOLD, -29.4k in PRE; absolute L6M +104.1k vs stack +61.5k, HOLD +89.2k vs +48.3k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.74): rule +31.5k vs scaled stack in L6M (MDE +43.3k), +30.2k in HOLD. maxDD-matched c* 1.47 (L6M +51.4k, HOLD +48.3k); SD-matched c* 1.38 (L6M +44.8k, HOLD +42.7k). [CANDIDATE-RECENT]
11. **A|B|EPL|N** (joint entry+profit+loss; looked(L6M-ranked)): at equal worst-20-weeks, A|B|EPL|N runs 1.31x lots (95% CI 1.01-1.70) and makes +41.2k $/wk more than the stack as it is in L6M (MDE 59.7k), +39.4k in HOLD, -54.8k in PRE; absolute L6M +102.6k vs stack +61.5k, HOLD +87.8k vs +48.3k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.77): rule +31.5k vs scaled stack in L6M (MDE +45.7k), +30.2k in HOLD. maxDD-matched c* 1.24 (L6M +36.1k, HOLD +35.1k); SD-matched c* 1.49 (L6M +55.2k, HOLD +51.4k). [CANDIDATE-RECENT]
12. **A|H|P|M** (profit: plain 70% take; PRE-selected): at equal worst-20-weeks, A|H|P|M runs 1.20x lots (95% CI 1.05-1.43) and makes +39.4k $/wk more than the stack as it is in L6M (MDE 48.1k), +37.9k in HOLD, +0.6k in PRE; absolute L6M +58.3k vs stack +18.8k, HOLD +46.4k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.83): rule +32.8k vs scaled stack in L6M (MDE +40.0k), +31.5k in HOLD. maxDD-matched c* 1.42 (L6M +49.9k, HOLD +46.2k); SD-matched c* 1.13 (L6M +35.8k, HOLD +34.9k). [CANDIDATE-RECENT]
13. **A|H|PL|M** (profit+loss; PRE-selected): at equal worst-20-weeks, A|H|PL|M runs 1.28x lots (95% CI 1.11-1.55) and makes +38.8k $/wk more than the stack as it is in L6M (MDE 66.3k), +31.1k in HOLD, +14.3k in PRE; absolute L6M +57.6k vs stack +18.8k, HOLD +39.6k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.78): rule +30.2k vs scaled stack in L6M (MDE +51.6k), +24.2k in HOLD. maxDD-matched c* 1.17 (L6M +33.5k, HOLD +27.4k); SD-matched c* 1.17 (L6M +33.8k, HOLD +27.6k). [CANDIDATE-RECENT]
14. **A|H|EPL|M** (joint entry+profit+loss; PRE-selected): at equal worst-20-weeks, A|H|EPL|M runs 1.29x lots (95% CI 1.10-1.56) and makes +38.7k $/wk more than the stack as it is in L6M (MDE 64.0k), +28.9k in HOLD, +18.3k in PRE; absolute L6M +57.5k vs stack +18.8k, HOLD +37.5k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.78): rule +30.1k vs scaled stack in L6M (MDE +49.7k), +22.5k in HOLD. maxDD-matched c* 1.10 (L6M +30.4k, HOLD +23.5k); SD-matched c* 1.18 (L6M +34.1k, HOLD +25.9k). [CANDIDATE-RECENT]
15. **A|B|P|M** (profit: plain 70% take; looked(L6M-ranked)): at equal worst-20-weeks, A|B|P|M runs 1.17x lots (95% CI 1.03-1.36) and makes +34.3k $/wk more than the stack as it is in L6M (MDE 38.4k), +33.1k in HOLD, +2.5k in PRE; absolute L6M +53.2k vs stack +18.8k, HOLD +41.7k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.86): rule +29.5k vs scaled stack in L6M (MDE +32.9k), +28.4k in HOLD. maxDD-matched c* 1.33 (L6M +41.9k, HOLD +39.0k); SD-matched c* 1.09 (L6M +30.8k, HOLD +30.3k). [CANDIDATE-RECENT]
16. **G|ADDUW|B1_PRE#1022** (staged under-water adds B1_PRE#1022; PRE-selected): at equal worst-20-weeks, G|ADDUW|B1_PRE#1022 runs 1.45x lots (95% CI 1.13-1.86) and makes +29.2k $/wk more than the stack as it is in L6M (MDE 42.3k), +27.5k in HOLD, +50.4k in PRE; absolute L6M +102.9k vs stack +73.7k, HOLD +81.2k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.69): rule +20.5k vs scaled stack in L6M (MDE +29.1k), +19.3k in HOLD. maxDD-matched c* 1.09 (L6M +3.5k, HOLD +7.3k); SD-matched c* 1.11 (L6M +5.5k, HOLD +8.8k). [CANDIDATE-RECENT]
17. **A|B|L|N** (loss: L2SL cut/tighten; looked(L6M-ranked)): at equal worst-20-weeks, A|B|L|N runs 1.09x lots (95% CI 0.95-1.27) and makes +27.8k $/wk more than the stack as it is in L6M (MDE 30.3k), +27.6k in HOLD, -17.1k in PRE; absolute L6M +89.3k vs stack +61.5k, HOLD +75.9k vs +48.3k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.92): rule +25.5k vs scaled stack in L6M (MDE +27.7k), +25.2k in HOLD. maxDD-matched c* 1.26 (L6M +41.8k, HOLD +39.5k); SD-matched c* 1.08 (L6M +26.5k, HOLD +26.4k). [CANDIDATE-RECENT]
18. **A|H|EL|N** (entry+loss; PRE-selected): at equal worst-20-weeks, A|H|EL|N runs 1.18x lots (95% CI 1.00-1.43) and makes +26.3k $/wk more than the stack as it is in L6M (MDE 49.0k), +18.5k in HOLD, +25.3k in PRE; absolute L6M +87.8k vs stack +61.5k, HOLD +66.9k vs +48.3k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.85): rule +22.4k vs scaled stack in L6M (MDE +41.7k), +15.8k in HOLD. maxDD-matched c* 0.96 (L6M +9.8k, HOLD +6.0k); SD-matched c* 1.03 (L6M +15.6k, HOLD +10.4k). [CANDIDATE]
19. **A|B|L|M** (loss: L2SL cut/tighten; looked(L6M-ranked)): at equal worst-20-weeks, A|B|L|M runs 1.04x lots (95% CI 0.93-1.16) and makes +25.9k $/wk more than the stack as it is in L6M (MDE 33.0k), +23.3k in HOLD, -14.6k in PRE; absolute L6M +44.7k vs stack +18.8k, HOLD +31.9k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.96): rule +24.8k vs scaled stack in L6M (MDE +31.6k), +22.4k in HOLD. maxDD-matched c* 1.07 (L6M +27.0k, HOLD +24.1k); SD-matched c* 1.04 (L6M +25.6k, HOLD +23.1k). [CANDIDATE-RECENT]
20. **A|H|E|N** (dip-entry (70/30 split); PRE-selected): at equal worst-20-weeks, A|H|E|N runs 1.06x lots (95% CI 0.98-1.17) and makes +22.6k $/wk more than the stack as it is in L6M (MDE 16.4k), +22.6k in HOLD, +7.7k in PRE; absolute L6M +84.1k vs stack +61.5k, HOLD +70.9k vs +48.3k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.94): rule +21.3k vs scaled stack in L6M (MDE +15.4k), +21.3k in HOLD. maxDD-matched c* 1.13 (L6M +27.6k, HOLD +26.8k); SD-matched c* 1.01 (L6M +18.3k, HOLD +19.0k). [CANDIDATE]
21. **A|B|PL|N** (profit+loss; looked(L6M-ranked)): at equal worst-20-weeks, A|B|PL|N runs 1.10x lots (95% CI 0.90-1.34) and makes +19.8k $/wk more than the stack as it is in L6M (MDE 48.5k), +19.2k in HOLD, -38.5k in PRE; absolute L6M +81.3k vs stack +61.5k, HOLD +67.5k vs +48.3k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.91): rule +18.0k vs scaled stack in L6M (MDE +44.0k), +17.4k in HOLD. maxDD-matched c* 1.35 (L6M +38.0k, HOLD +34.4k); SD-matched c* 1.17 (L6M +25.0k, HOLD +23.5k). [CANDIDATE-RECENT]
22. **C|D|D_L20s** (concurrency cap D_L20s; registered grid (not selected)): at equal worst-20-weeks, C|D|D_L20s runs 1.46x lots (95% CI 1.18-1.76) and makes +17.3k $/wk more than the stack as it is in L6M (MDE 57.7k), +12.9k in HOLD, -10.3k in PRE; absolute L6M +90.9k vs stack +73.7k, HOLD +66.5k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.68): rule +12.3k vs scaled stack in L6M (MDE +39.7k), +9.2k in HOLD. maxDD-matched c* 1.14 (L6M -2.0k, HOLD -1.1k); SD-matched c* 1.40 (L6M +14.0k, HOLD +10.6k). [CANDIDATE-RECENT]
23. **A|H|L|N** (loss: L2SL cut/tighten; PRE-selected): at equal worst-20-weeks, A|H|L|N runs 1.15x lots (95% CI 0.97-1.38) and makes +15.7k $/wk more than the stack as it is in L6M (MDE 41.0k), +11.3k in HOLD, +19.0k in PRE; absolute L6M +77.2k vs stack +61.5k, HOLD +59.7k vs +48.3k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.87): rule +13.7k vs scaled stack in L6M (MDE +35.8k), +9.9k in HOLD. maxDD-matched c* 0.92 (L6M +0.6k, HOLD -0.4k); SD-matched c* 1.02 (L6M +7.5k, HOLD +5.0k). [CANDIDATE-RECENT]
24. **C|A|A05** (slot/pool block-halve A05_half_loose_pool; registered grid (not selected)): at equal worst-20-weeks, C|A|A05 runs 1.14x lots (95% CI 1.01-1.30) and makes +15.1k $/wk more than the stack as it is in L6M (MDE 24.4k), +11.4k in HOLD, +13.1k in PRE; absolute L6M +88.7k vs stack +73.7k, HOLD +65.1k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.87): rule +13.2k vs scaled stack in L6M (MDE +21.3k), +10.0k in HOLD. maxDD-matched c* 1.04 (L6M +7.3k, HOLD +5.7k); SD-matched c* 1.07 (L6M +9.5k, HOLD +7.4k). [CANDIDATE-RECENT]
25. **A|H|EL|M** (entry+loss; PRE-selected): at equal worst-20-weeks, A|H|EL|M runs 1.14x lots (95% CI 0.99-1.32) and makes +15.0k $/wk more than the stack as it is in L6M (MDE 39.8k), +7.9k in HOLD, +23.7k in PRE; absolute L6M +33.8k vs stack +18.8k, HOLD +16.4k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.88): rule +13.2k vs scaled stack in L6M (MDE +35.0k), +6.9k in HOLD. maxDD-matched c* 0.96 (L6M +9.7k, HOLD +5.3k); SD-matched c* 1.02 (L6M +11.6k, HOLD +6.2k). [CANDIDATE]
26. **B|L2SL|HM_RANK** (loss-health L2SL cells (tighten/cut); looked(L6M-ranked)): at equal worst-20-weeks, B|L2SL|HM_RANK runs 1.09x lots (95% CI 1.03-1.17) and makes +14.8k $/wk more than the stack as it is in L6M (MDE 8.9k), +12.1k in HOLD, +2.6k in PRE; absolute L6M +80.5k vs stack +65.7k, HOLD +64.5k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.92): rule +13.6k vs scaled stack in L6M (MDE +8.1k), +11.1k in HOLD. maxDD-matched c* 0.99 (L6M +7.5k, HOLD +6.2k); SD-matched c* 1.05 (L6M +11.6k, HOLD +9.5k). [CANDIDATE-RECENT]
27. **A|H|E|M** (dip-entry (70/30 split); PRE-selected): at equal worst-20-weeks, A|H|E|M runs 1.00x lots (95% CI 0.94-1.10) and makes +13.4k $/wk more than the stack as it is in L6M (MDE 14.5k), +11.6k in HOLD, +7.8k in PRE; absolute L6M +32.2k vs stack +18.8k, HOLD +20.2k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.00): rule +13.4k vs scaled stack in L6M (MDE +14.5k), +11.6k in HOLD. maxDD-matched c* 0.99 (L6M +12.9k, HOLD +11.3k); SD-matched c* 0.97 (L6M +12.2k, HOLD +10.9k). [CANDIDATE]
28. **C|A|A04** (slot/pool block-halve A04_blk_loose_book; registered grid (not selected)): at equal worst-20-weeks, C|A|A04 runs 1.29x lots (95% CI 1.09-1.55) and makes +13.3k $/wk more than the stack as it is in L6M (MDE 29.4k), +7.5k in HOLD, +29.3k in PRE; absolute L6M +86.9k vs stack +73.7k, HOLD +61.1k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.78): rule +10.3k vs scaled stack in L6M (MDE +22.8k), +5.8k in HOLD. maxDD-matched c* 1.00 (L6M -6.2k, HOLD -6.2k); SD-matched c* 1.14 (L6M +3.6k, HOLD +0.7k). [CANDIDATE-RECENT]
29. **G|ADDUW|B2_L6Mrank#4** (staged under-water adds B2_L6Mrank#4; looked(L6M-ranked)): at equal worst-20-weeks, G|ADDUW|B2_L6Mrank#4 runs 0.97x lots (95% CI 0.89-1.06) and makes +13.1k $/wk more than the stack as it is in L6M (MDE 17.9k), +10.7k in HOLD, -2.0k in PRE; absolute L6M +86.7k vs stack +73.7k, HOLD +64.4k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.03): rule +13.5k vs scaled stack in L6M (MDE +18.5k), +11.0k in HOLD. maxDD-matched c* 0.95 (L6M +11.0k, HOLD +9.2k); SD-matched c* 0.93 (L6M +9.4k, HOLD +7.9k). [CANDIDATE-RECENT]
30. **G|ADDUW|B2_PRE#5** (staged under-water adds B2_PRE#5; PRE-selected): at equal worst-20-weeks, G|ADDUW|B2_PRE#5 runs 1.06x lots (95% CI 0.95-1.20) and makes +11.6k $/wk more than the stack as it is in L6M (MDE 17.7k), +9.5k in HOLD, +9.5k in PRE; absolute L6M +85.3k vs stack +73.7k, HOLD +63.2k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.94): rule +10.9k vs scaled stack in L6M (MDE +16.7k), +9.0k in HOLD. maxDD-matched c* 0.99 (L6M +6.2k, HOLD +5.5k); SD-matched c* 0.97 (L6M +4.8k, HOLD +4.4k). [CANDIDATE]
31. **H|L2SP|ALL_L6M_rank1|N** (profit-health exits (L2SP six books); looked(L6M-ranked)): at equal worst-20-weeks, H|L2SP|ALL_L6M_rank1|N runs 1.03x lots (95% CI 0.78-1.29) and makes +11.5k $/wk more than the stack as it is in L6M (MDE 49.0k), +7.2k in HOLD, -40.1k in PRE; absolute L6M +73.9k vs stack +62.3k, HOLD +59.6k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.97): rule +11.1k vs scaled stack in L6M (MDE +47.4k), +6.9k in HOLD. maxDD-matched c* 0.87 (L6M +0.2k, HOLD -2.0k); SD-matched c* 1.20 (L6M +23.4k, HOLD +16.7k). [CANDIDATE-RECENT]
32. **C|F|A06+HM5R+B02** (T-STACK F combine A06+HM5R+B02; PRE-picked, HOLD-admitted): at equal worst-20-weeks, C|F|A06+HM5R+B02 runs 1.38x lots (95% CI 1.11-1.83) and makes +11.4k $/wk more than the stack as it is in L6M (MDE 40.6k), +6.4k in HOLD, +34.9k in PRE; absolute L6M +85.1k vs stack +73.7k, HOLD +60.1k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.72): rule +8.3k vs scaled stack in L6M (MDE +29.4k), +4.6k in HOLD. maxDD-matched c* 1.13 (L6M -4.3k, HOLD -4.7k); SD-matched c* 1.24 (L6M +2.5k, HOLD +0.1k). [CANDIDATE-RECENT]
33. **C|F|A06+B02** (T-STACK F combine A06+B02; PRE-picked): at equal worst-20-weeks, C|F|A06+B02 runs 1.23x lots (95% CI 1.11-1.38) and makes +10.3k $/wk more than the stack as it is in L6M (MDE 21.6k), +8.0k in HOLD, +24.1k in PRE; absolute L6M +84.0k vs stack +73.7k, HOLD +61.7k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.81): rule +8.4k vs scaled stack in L6M (MDE +17.6k), +6.5k in HOLD. maxDD-matched c* 1.05 (L6M -1.6k, HOLD -0.7k); SD-matched c* 1.11 (L6M +2.5k, HOLD +2.3k). [CANDIDATE-RECENT]
34. **C|F|A06+HM5R** (T-STACK F combine A06+HM5R; PRE-picked): at equal worst-20-weeks, C|F|A06+HM5R runs 1.30x lots (95% CI 1.03-1.74) and makes +9.4k $/wk more than the stack as it is in L6M (MDE 37.8k), +4.4k in HOLD, +29.6k in PRE; absolute L6M +83.1k vs stack +73.7k, HOLD +58.1k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.77): rule +7.3k vs scaled stack in L6M (MDE +29.1k), +3.4k in HOLD. maxDD-matched c* 1.09 (L6M -3.9k, HOLD -4.9k); SD-matched c* 1.20 (L6M +3.1k, HOLD +0.0k). [CANDIDATE-RECENT]
35. **C|F|C1** (chop-week C1 B1_CONS2; registered section-best (PRE-picked)): at equal worst-20-weeks, C|F|C1 runs 1.22x lots (95% CI 1.08-1.35) and makes +8.5k $/wk more than the stack as it is in L6M (MDE 17.5k), +10.6k in HOLD, +2.2k in PRE; absolute L6M +82.1k vs stack +73.7k, HOLD +64.3k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.82): rule +6.9k vs scaled stack in L6M (MDE +14.3k), +8.7k in HOLD. maxDD-matched c* 1.23 (L6M +8.8k, HOLD +10.9k); SD-matched c* 1.12 (L6M +1.4k, HOLD +5.1k). [CANDIDATE-RECENT]
36. **B|L2SL|ALL_RANK** (loss-health L2SL cells (tighten/cut); looked(L6M-ranked)): at equal worst-20-weeks, B|L2SL|ALL_RANK runs 0.95x lots (95% CI 0.86-1.05) and makes +8.4k $/wk more than the stack as it is in L6M (MDE 15.9k), +6.9k in HOLD, -6.9k in PRE; absolute L6M +74.0k vs stack +65.7k, HOLD +59.3k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.05): rule +8.8k vs scaled stack in L6M (MDE +16.7k), +7.2k in HOLD. maxDD-matched c* 0.97 (L6M +10.0k, HOLD +8.2k); SD-matched c* 0.99 (L6M +11.0k, HOLD +9.0k). [DEAD]
37. **E|SL|PB|NY|P1+N3** (session-lock NY P1+N3; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PB|NY|P1+N3 runs 1.07x lots (95% CI 1.03-1.12) and makes +8.1k $/wk more than the stack as it is in L6M (MDE 7.8k), +7.2k in HOLD, +1.4k in PRE; absolute L6M +79.0k vs stack +70.8k, HOLD +64.4k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.94): rule +7.6k vs scaled stack in L6M (MDE +7.3k), +6.8k in HOLD. maxDD-matched c* 1.15 (L6M +13.9k, HOLD +11.9k); SD-matched c* 1.04 (L6M +6.4k, HOLD +5.8k). [CANDIDATE]
38. **C|D|D_L30s** (concurrency cap D_L30s; registered grid (not selected)): at equal worst-20-weeks, C|D|D_L30s runs 1.18x lots (95% CI 1.02-1.37) and makes +8.1k $/wk more than the stack as it is in L6M (MDE 33.0k), +5.1k in HOLD, -8.5k in PRE; absolute L6M +81.8k vs stack +73.7k, HOLD +58.7k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.85): rule +6.9k vs scaled stack in L6M (MDE +27.9k), +4.3k in HOLD. maxDD-matched c* 1.05 (L6M -1.0k, HOLD -1.5k); SD-matched c* 1.17 (L6M +7.5k, HOLD +4.6k). [CANDIDATE-RECENT]
39. **C|F|HM5R+B02** (T-STACK F combine HM5R+B02; PRE-picked): at equal worst-20-weeks, C|F|HM5R+B02 runs 1.24x lots (95% CI 1.08-1.51) and makes +8.0k $/wk more than the stack as it is in L6M (MDE 30.5k), +5.6k in HOLD, +14.0k in PRE; absolute L6M +81.7k vs stack +73.7k, HOLD +59.2k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.81): rule +6.5k vs scaled stack in L6M (MDE +24.6k), +4.5k in HOLD. maxDD-matched c* 1.10 (L6M -1.3k, HOLD -1.2k); SD-matched c* 1.17 (L6M +3.3k, HOLD +2.1k). [CANDIDATE-RECENT]
40. **E|SL|PB|NY|P1** (session-lock NY P1; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PB|NY|P1 runs 1.07x lots (95% CI 1.02-1.11) and makes +7.8k $/wk more than the stack as it is in L6M (MDE 7.8k), +6.7k in HOLD, +1.4k in PRE; absolute L6M +78.6k vs stack +70.8k, HOLD +63.9k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.94): rule +7.3k vs scaled stack in L6M (MDE +7.3k), +6.3k in HOLD. maxDD-matched c* 1.15 (L6M +13.7k, HOLD +11.6k); SD-matched c* 1.04 (L6M +6.1k, HOLD +5.4k). [CANDIDATE-RECENT]
41. **C|A|A08** (slot/pool block-halve A08_blk_loose_book_rng; registered grid (not selected)): at equal worst-20-weeks, C|A|A08 runs 1.04x lots (95% CI 0.99-1.11) and makes +7.7k $/wk more than the stack as it is in L6M (MDE 13.4k), +6.1k in HOLD, -2.3k in PRE; absolute L6M +81.4k vs stack +73.7k, HOLD +59.7k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.96): rule +7.4k vs scaled stack in L6M (MDE +12.9k), +5.8k in HOLD. maxDD-matched c* 0.97 (L6M +1.8k, HOLD +1.7k); SD-matched c* 1.02 (L6M +5.8k, HOLD +4.7k). [CANDIDATE-RECENT]
42. **F|CW|SM** (cut-and-wait SM (book PRE-best cell, other books as is); PRE-selected): at equal worst-20-weeks, F|CW|SM runs 1.00x lots (95% CI 0.95-1.05) and makes +7.5k $/wk more than the stack as it is in L6M (MDE 12.3k), +5.6k in HOLD, -1.9k in PRE; absolute L6M +38.0k vs stack +30.5k, HOLD +27.5k vs +21.9k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.00): rule +7.5k vs scaled stack in L6M (MDE +12.3k), +5.6k in HOLD. maxDD-matched c* 0.96 (L6M +6.0k, HOLD +4.5k); SD-matched c* 1.01 (L6M +8.0k, HOLD +6.0k). [CANDIDATE-RECENT]
43. **E|SL|PB|NY|P1+L2** (session-lock NY P1+L2; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PB|NY|P1+L2 runs 1.07x lots (95% CI 1.03-1.11) and makes +7.2k $/wk more than the stack as it is in L6M (MDE 8.0k), +6.4k in HOLD, +1.6k in PRE; absolute L6M +78.0k vs stack +70.8k, HOLD +63.6k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.94): rule +6.7k vs scaled stack in L6M (MDE +7.5k), +6.0k in HOLD. maxDD-matched c* 1.17 (L6M +14.4k, HOLD +12.3k); SD-matched c* 1.04 (L6M +5.5k, HOLD +5.0k). [CANDIDATE-RECENT]
44. **C|A|A06** (slot/pool block-halve A06_half_loose_book; registered grid (not selected)): at equal worst-20-weeks, C|A|A06 runs 1.16x lots (95% CI 1.07-1.29) and makes +6.6k $/wk more than the stack as it is in L6M (MDE 17.6k), +3.4k in HOLD, +18.9k in PRE; absolute L6M +80.2k vs stack +73.7k, HOLD +57.1k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.86): rule +5.7k vs scaled stack in L6M (MDE +15.2k), +3.0k in HOLD. maxDD-matched c* 1.03 (L6M -2.7k, HOLD -3.1k); SD-matched c* 1.08 (L6M +1.1k, HOLD -0.5k). [CANDIDATE-RECENT]
45. **E|SL|PB|NY|G1k70** (session-lock NY G1k70; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PB|NY|G1k70 runs 1.06x lots (95% CI 1.02-1.10) and makes +6.4k $/wk more than the stack as it is in L6M (MDE 7.5k), +5.5k in HOLD, +1.5k in PRE; absolute L6M +77.2k vs stack +70.8k, HOLD +62.7k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.95): rule +6.1k vs scaled stack in L6M (MDE +7.1k), +5.2k in HOLD. maxDD-matched c* 1.10 (L6M +9.8k, HOLD +8.3k); SD-matched c* 1.03 (L6M +4.8k, HOLD +4.2k). [CANDIDATE]
46. **C|A|A03** (slot/pool block-halve A03_blk_strict_book; registered grid (not selected)): at equal worst-20-weeks, C|A|A03 runs 1.02x lots (95% CI 1.00-1.06) and makes +6.3k $/wk more than the stack as it is in L6M (MDE 6.2k), +5.4k in HOLD, +3.1k in PRE; absolute L6M +79.9k vs stack +73.7k, HOLD +59.1k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.98): rule +6.1k vs scaled stack in L6M (MDE +6.1k), +5.3k in HOLD. maxDD-matched c* 1.00 (L6M +4.5k, HOLD +4.1k); SD-matched c* 1.00 (L6M +4.3k, HOLD +4.0k). [CANDIDATE-RECENT]
47. **H|L2SP|ALL_PRE_selected|M** (profit-health exits (L2SP six books); PRE-selected): at equal worst-20-weeks, H|L2SP|ALL_PRE_selected|M runs 1.15x lots (95% CI 1.07-1.25) and makes +6.1k $/wk more than the stack as it is in L6M (MDE 23.2k), +5.1k in HOLD, +4.0k in PRE; absolute L6M +32.5k vs stack +26.4k, HOLD +22.8k vs +17.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.87): rule +5.3k vs scaled stack in L6M (MDE +20.1k), +4.4k in HOLD. maxDD-matched c* 0.99 (L6M +1.4k, HOLD +1.7k); SD-matched c* 1.12 (L6M +5.1k, HOLD +4.3k). [CANDIDATE-RECENT]
48. **E|SL|PB|NY|P1+L1** (session-lock NY P1+L1; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PB|NY|P1+L1 runs 1.07x lots (95% CI 1.02-1.11) and makes +6.1k $/wk more than the stack as it is in L6M (MDE 8.7k), +5.3k in HOLD, -0.8k in PRE; absolute L6M +76.9k vs stack +70.8k, HOLD +62.5k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.94): rule +5.7k vs scaled stack in L6M (MDE +8.2k), +5.0k in HOLD. maxDD-matched c* 1.17 (L6M +13.3k, HOLD +11.2k); SD-matched c* 1.06 (L6M +5.3k, HOLD +4.6k). [CANDIDATE-RECENT]
49. **E|SL|PB|NY|P1+L1.5** (session-lock NY P1+L1.5; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PB|NY|P1+L1.5 runs 1.06x lots (95% CI 1.01-1.11) and makes +5.9k $/wk more than the stack as it is in L6M (MDE 7.7k), +4.9k in HOLD, +0.9k in PRE; absolute L6M +76.7k vs stack +70.8k, HOLD +62.1k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.94): rule +5.6k vs scaled stack in L6M (MDE +7.3k), +4.6k in HOLD. maxDD-matched c* 1.16 (L6M +13.3k, HOLD +10.9k); SD-matched c* 1.04 (L6M +4.8k, HOLD +4.0k). [CANDIDATE-RECENT]
50. **C|F|HM5R** (HM on 5-min bars (HM5 REPL); registered section-best (PRE-picked)): at equal worst-20-weeks, C|F|HM5R runs 1.16x lots (95% CI 1.01-1.43) and makes +5.6k $/wk more than the stack as it is in L6M (MDE 28.0k), +3.2k in HOLD, +9.8k in PRE; absolute L6M +79.2k vs stack +73.7k, HOLD +56.9k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.87): rule +4.8k vs scaled stack in L6M (MDE +24.2k), +2.8k in HOLD. maxDD-matched c* 1.06 (L6M -1.0k, HOLD -1.5k); SD-matched c* 1.13 (L6M +3.5k, HOLD +1.7k). [CANDIDATE-RECENT]
51. **C|F|HM5M** (HM5 MIX; registered section-best (PRE-picked)): at equal worst-20-weeks, C|F|HM5M runs 1.11x lots (95% CI 1.03-1.23) and makes +5.5k $/wk more than the stack as it is in L6M (MDE 13.1k), +3.6k in HOLD, +6.5k in PRE; absolute L6M +79.2k vs stack +73.7k, HOLD +57.3k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.90): rule +5.0k vs scaled stack in L6M (MDE +11.8k), +3.3k in HOLD. maxDD-matched c* 1.03 (L6M -0.5k, HOLD -0.7k); SD-matched c* 1.08 (L6M +3.4k, HOLD +2.1k). [CANDIDATE-RECENT]
52. **C|D|D_B4s** (concurrency cap D_B4s; registered grid (not selected)): at equal worst-20-weeks, C|D|D_B4s runs 1.12x lots (95% CI 1.02-1.23) and makes +5.5k $/wk more than the stack as it is in L6M (MDE 20.5k), +3.5k in HOLD, +0.2k in PRE; absolute L6M +79.1k vs stack +73.7k, HOLD +57.2k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.89): rule +4.9k vs scaled stack in L6M (MDE +18.3k), +3.2k in HOLD. maxDD-matched c* 1.10 (L6M +4.0k, HOLD +2.5k); SD-matched c* 1.09 (L6M +3.6k, HOLD +2.2k). [CANDIDATE-RECENT]
53. **C|D|D_L40s** (concurrency cap D_L40s; registered grid (not selected)): at equal worst-20-weeks, C|D|D_L40s runs 1.06x lots (95% CI 1.02-1.14) and makes +5.2k $/wk more than the stack as it is in L6M (MDE 7.9k), +3.6k in HOLD, +5.1k in PRE; absolute L6M +78.8k vs stack +73.7k, HOLD +57.3k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.94): rule +4.9k vs scaled stack in L6M (MDE +7.4k), +3.4k in HOLD. maxDD-matched c* 1.01 (L6M +1.3k, HOLD +0.7k); SD-matched c* 1.03 (L6M +3.0k, HOLD +2.0k). [CANDIDATE-RECENT]
54. **C|D|D_B2s** (concurrency cap D_B2s; registered grid (not selected)): at equal worst-20-weeks, C|D|D_B2s runs 1.53x lots (95% CI 1.17-1.93) and makes +5.0k $/wk more than the stack as it is in L6M (MDE 64.1k), +3.5k in HOLD, -16.1k in PRE; absolute L6M +78.6k vs stack +73.7k, HOLD +57.2k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.65): rule +4.2k vs scaled stack in L6M (MDE +42.0k), +3.2k in HOLD. maxDD-matched c* 1.28 (L6M -7.1k, HOLD -5.0k); SD-matched c* 1.48 (L6M +2.7k, HOLD +2.0k). [CANDIDATE-RECENT]
55. **E|SL|PB|NY|P1.5+N2** (session-lock NY P1.5+N2; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PB|NY|P1.5+N2 runs 1.04x lots (95% CI 1.01-1.08) and makes +4.9k $/wk more than the stack as it is in L6M (MDE 5.5k), +4.5k in HOLD, +0.2k in PRE; absolute L6M +75.7k vs stack +70.8k, HOLD +61.7k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.96): rule +4.7k vs scaled stack in L6M (MDE +5.3k), +4.3k in HOLD. maxDD-matched c* 1.07 (L6M +7.1k, HOLD +6.3k); SD-matched c* 1.03 (L6M +4.6k, HOLD +4.2k). [CANDIDATE-RECENT]
56. **E|SL|PB|London|P1.5+N1** (session-lock London P1.5+N1; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PB|London|P1.5+N1 runs 1.08x lots (95% CI 1.01-1.14) and makes +4.9k $/wk more than the stack as it is in L6M (MDE 10.1k), +4.3k in HOLD, +6.5k in PRE; absolute L6M +75.7k vs stack +70.8k, HOLD +61.5k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.93): rule +4.5k vs scaled stack in L6M (MDE +9.3k), +4.0k in HOLD. maxDD-matched c* 1.36 (L6M +24.4k, HOLD +20.2k); SD-matched c* 1.03 (L6M +1.4k, HOLD +1.5k). [CANDIDATE]
57. **E|SL|PB|NY|G1k50** (session-lock NY G1k50; registered grid (all 798 cells), picked as CANDIDATE): at equal worst-20-weeks, E|SL|PB|NY|G1k50 runs 1.04x lots (95% CI 1.01-1.08) and makes +4.8k $/wk more than the stack as it is in L6M (MDE 7.1k), +4.1k in HOLD, +2.6k in PRE; absolute L6M +75.6k vs stack +70.8k, HOLD +61.3k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.96): rule +4.6k vs scaled stack in L6M (MDE +6.8k), +3.9k in HOLD. maxDD-matched c* 1.06 (L6M +5.9k, HOLD +5.0k); SD-matched c* 1.02 (L6M +2.8k, HOLD +2.5k). [CANDIDATE]
58. **E|SL|PB|NY|P1+N1** (session-lock NY P1+N1; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PB|NY|P1+N1 runs 1.05x lots (95% CI 1.01-1.09) and makes +4.3k $/wk more than the stack as it is in L6M (MDE 7.3k), +3.6k in HOLD, -0.7k in PRE; absolute L6M +75.1k vs stack +70.8k, HOLD +60.8k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.96): rule +4.1k vs scaled stack in L6M (MDE +7.0k), +3.4k in HOLD. maxDD-matched c* 1.16 (L6M +12.1k, HOLD +9.8k); SD-matched c* 1.05 (L6M +4.5k, HOLD +3.7k). [CANDIDATE-RECENT]
59. **E|SL|PB|London|P3+N1** (session-lock London P3+N1; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PB|London|P3+N1 runs 1.07x lots (95% CI 1.00-1.12) and makes +4.1k $/wk more than the stack as it is in L6M (MDE 8.1k), +3.9k in HOLD, +5.9k in PRE; absolute L6M +74.9k vs stack +70.8k, HOLD +61.1k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.94): rule +3.8k vs scaled stack in L6M (MDE +7.6k), +3.6k in HOLD. maxDD-matched c* 1.28 (L6M +19.5k, HOLD +16.5k); SD-matched c* 1.03 (L6M +1.4k, HOLD +1.7k). [CANDIDATE]
60. **C|F|B02** (range-day halving B02; registered section-best (PRE-picked)): at equal worst-20-weeks, C|F|B02 runs 1.06x lots (95% CI 1.01-1.11) and makes +3.7k $/wk more than the stack as it is in L6M (MDE 8.4k), +4.3k in HOLD, +3.9k in PRE; absolute L6M +77.4k vs stack +73.7k, HOLD +58.0k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.94): rule +3.5k vs scaled stack in L6M (MDE +7.9k), +4.1k in HOLD. maxDD-matched c* 1.03 (L6M +1.1k, HOLD +2.4k); SD-matched c* 1.03 (L6M +1.6k, HOLD +2.8k). [CANDIDATE]
61. **E|SL|PB|London|P2+N1** (session-lock London P2+N1; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PB|London|P2+N1 runs 1.07x lots (95% CI 1.00-1.14) and makes +3.6k $/wk more than the stack as it is in L6M (MDE 9.3k), +3.5k in HOLD, +6.6k in PRE; absolute L6M +74.5k vs stack +70.8k, HOLD +60.7k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.94): rule +3.4k vs scaled stack in L6M (MDE +8.7k), +3.3k in HOLD. maxDD-matched c* 1.32 (L6M +20.8k, HOLD +17.5k); SD-matched c* 1.03 (L6M +0.8k, HOLD +1.2k). [CANDIDATE]
62. **E|SL|PS|London|P1+N3** (session-lock London P1+N3; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PS|London|P1+N3 runs 1.03x lots (95% CI 1.00-1.06) and makes +3.5k $/wk more than the stack as it is in L6M (MDE 6.9k), +3.2k in HOLD, -0.6k in PRE; absolute L6M +76.5k vs stack +73.0k, HOLD +61.0k vs +57.8k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.97): rule +3.4k vs scaled stack in L6M (MDE +6.7k), +3.1k in HOLD. maxDD-matched c* 1.01 (L6M +2.2k, HOLD +2.1k); SD-matched c* 1.02 (L6M +2.8k, HOLD +2.6k). [CANDIDATE-RECENT]
63. **E|SL|WT|NY|P2+N1** (session-lock NY P2+N1; registered grid (all 798 cells), picked as CANDIDATE): at equal worst-20-weeks, E|SL|WT|NY|P2+N1 runs 1.01x lots (95% CI 0.98-1.05) and makes +3.3k $/wk more than the stack as it is in L6M (MDE 5.8k), +3.0k in HOLD, +0.9k in PRE; absolute L6M +74.1k vs stack +70.8k, HOLD +60.2k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.99): rule +3.2k vs scaled stack in L6M (MDE +5.7k), +3.0k in HOLD. maxDD-matched c* 1.04 (L6M +5.4k, HOLD +4.8k); SD-matched c* 1.02 (L6M +3.6k, HOLD +3.2k). [CANDIDATE]
64. **E|SL|PS|London|P1+N2** (session-lock London P1+N2; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PS|London|P1+N2 runs 1.04x lots (95% CI 1.01-1.07) and makes +3.0k $/wk more than the stack as it is in L6M (MDE 7.1k), +2.8k in HOLD, +0.5k in PRE; absolute L6M +76.0k vs stack +73.0k, HOLD +60.6k vs +57.8k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.97): rule +2.9k vs scaled stack in L6M (MDE +6.9k), +2.7k in HOLD. maxDD-matched c* 1.03 (L6M +2.4k, HOLD +2.3k); SD-matched c* 1.02 (L6M +1.8k, HOLD +1.8k). [CANDIDATE-RECENT]
65. **E|SL|PB|NY|P1.5** (session-lock NY P1.5; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PB|NY|P1.5 runs 1.03x lots (95% CI 1.00-1.06) and makes +2.9k $/wk more than the stack as it is in L6M (MDE 4.3k), +2.4k in HOLD, -0.9k in PRE; absolute L6M +73.8k vs stack +70.8k, HOLD +59.6k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.97): rule +2.9k vs scaled stack in L6M (MDE +4.1k), +2.4k in HOLD. maxDD-matched c* 1.01 (L6M +1.4k, HOLD +1.2k); SD-matched c* 1.03 (L6M +3.0k, HOLD +2.5k). [CANDIDATE-RECENT]
66. **E|SL|PS|NY|P1.5+L1** (session-lock NY P1.5+L1; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PS|NY|P1.5+L1 runs 1.02x lots (95% CI 1.00-1.04) and makes +2.8k $/wk more than the stack as it is in L6M (MDE 4.8k), +2.2k in HOLD, +0.1k in PRE; absolute L6M +75.8k vs stack +73.0k, HOLD +60.0k vs +57.8k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.98): rule +2.7k vs scaled stack in L6M (MDE +4.7k), +2.2k in HOLD. maxDD-matched c* 1.02 (L6M +2.9k, HOLD +2.3k); SD-matched c* 1.02 (L6M +2.6k, HOLD +2.1k). [CANDIDATE-RECENT]
67. **E|SL|WT|NY|P2** (session-lock NY P2; registered grid (all 798 cells), picked as CANDIDATE): at equal worst-20-weeks, E|SL|WT|NY|P2 runs 1.02x lots (95% CI 1.00-1.03) and makes +2.6k $/wk more than the stack as it is in L6M (MDE 3.1k), +2.4k in HOLD, +1.1k in PRE; absolute L6M +73.5k vs stack +70.8k, HOLD +59.6k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.98): rule +2.6k vs scaled stack in L6M (MDE +3.1k), +2.4k in HOLD. maxDD-matched c* 1.03 (L6M +3.5k, HOLD +3.1k); SD-matched c* 1.01 (L6M +2.2k, HOLD +2.1k). [CANDIDATE]
68. **B|L2SL|SM_RANK** (loss-health L2SL cells (tighten/cut); looked(L6M-ranked)): at equal worst-20-weeks, B|L2SL|SM_RANK runs 0.99x lots (95% CI 0.91-1.05) and makes +2.6k $/wk more than the stack as it is in L6M (MDE 8.0k), +2.6k in HOLD, -5.7k in PRE; absolute L6M +68.3k vs stack +65.7k, HOLD +55.0k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.01): rule +2.6k vs scaled stack in L6M (MDE +8.2k), +2.6k in HOLD. maxDD-matched c* 1.04 (L6M +6.2k, HOLD +5.5k); SD-matched c* 1.01 (L6M +4.5k, HOLD +4.2k). [CANDIDATE-RECENT]
69. **E|SL|PB|NY|P1.5+L2** (session-lock NY P1.5+L2; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PB|NY|P1.5+L2 runs 1.03x lots (95% CI 1.00-1.07) and makes +2.5k $/wk more than the stack as it is in L6M (MDE 4.9k), +2.2k in HOLD, -0.8k in PRE; absolute L6M +73.3k vs stack +70.8k, HOLD +59.4k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.97): rule +2.4k vs scaled stack in L6M (MDE +4.7k), +2.1k in HOLD. maxDD-matched c* 1.02 (L6M +1.8k, HOLD +1.7k); SD-matched c* 1.03 (L6M +2.5k, HOLD +2.2k). [CANDIDATE-RECENT]
70. **E|SL|HM|NY|P1.5+L1.5** (session-lock NY P1.5+L1.5; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|HM|NY|P1.5+L1.5 runs 1.03x lots (95% CI 0.99-1.06) and makes +2.4k $/wk more than the stack as it is in L6M (MDE 10.0k), +2.6k in HOLD, +0.2k in PRE; absolute L6M +73.2k vs stack +70.8k, HOLD +59.8k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.97): rule +2.3k vs scaled stack in L6M (MDE +9.7k), +2.5k in HOLD. maxDD-matched c* 1.03 (L6M +2.5k, HOLD +2.7k); SD-matched c* 1.02 (L6M +2.0k, HOLD +2.3k). [CANDIDATE]
71. **F|CW|WT** (cut-and-wait WT (book PRE-best cell, other books as is); PRE-selected): at equal worst-20-weeks, F|CW|WT runs 1.02x lots (95% CI 0.94-1.08) and makes +2.3k $/wk more than the stack as it is in L6M (MDE 11.5k), -0.7k in HOLD, -0.1k in PRE; absolute L6M +32.9k vs stack +30.5k, HOLD +21.2k vs +21.9k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.98): rule +2.3k vs scaled stack in L6M (MDE +11.3k), -0.7k in HOLD. maxDD-matched c* 0.87 (L6M -2.3k, HOLD -3.7k); SD-matched c* 1.03 (L6M +2.5k, HOLD -0.6k). [DEAD]
72. **E|SL|PS|NY|P2+N1** (session-lock NY P2+N1; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PS|NY|P2+N1 runs 1.02x lots (95% CI 0.99-1.04) and makes +2.3k $/wk more than the stack as it is in L6M (MDE 5.0k), +1.7k in HOLD, -0.2k in PRE; absolute L6M +75.4k vs stack +73.0k, HOLD +59.5k vs +57.8k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.98): rule +2.3k vs scaled stack in L6M (MDE +4.9k), +1.7k in HOLD. maxDD-matched c* 1.02 (L6M +2.1k, HOLD +1.5k); SD-matched c* 1.01 (L6M +1.8k, HOLD +1.2k). [CANDIDATE-RECENT]
73. **E|SL|PS|NY|P2+L1** (session-lock NY P2+L1; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PS|NY|P2+L1 runs 1.02x lots (95% CI 1.00-1.04) and makes +2.1k $/wk more than the stack as it is in L6M (MDE 4.4k), +1.6k in HOLD, +0.4k in PRE; absolute L6M +75.2k vs stack +73.0k, HOLD +59.4k vs +57.8k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.98): rule +2.1k vs scaled stack in L6M (MDE +4.3k), +1.6k in HOLD. maxDD-matched c* 1.05 (L6M +4.4k, HOLD +3.4k); SD-matched c* 1.01 (L6M +1.7k, HOLD +1.2k). [CANDIDATE]
74. **C|A|A09** (slot/pool block-halve A09_half_loose_pool_rng; registered grid (not selected)): at equal worst-20-weeks, C|A|A09 runs 1.03x lots (95% CI 0.99-1.08) and makes +2.0k $/wk more than the stack as it is in L6M (MDE 9.9k), +1.0k in HOLD, -2.1k in PRE; absolute L6M +75.7k vs stack +73.7k, HOLD +54.6k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.98): rule +2.0k vs scaled stack in L6M (MDE +9.6k), +0.9k in HOLD. maxDD-matched c* 0.98 (L6M -1.0k, HOLD -1.2k); SD-matched c* 1.03 (L6M +2.7k, HOLD +1.5k). [DEAD]
75. **E|SL|PB|NY|P2** (session-lock NY P2; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PB|NY|P2 runs 1.02x lots (95% CI 1.00-1.04) and makes +2.0k $/wk more than the stack as it is in L6M (MDE 3.1k), +1.5k in HOLD, -0.4k in PRE; absolute L6M +72.8k vs stack +70.8k, HOLD +58.7k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.98): rule +1.9k vs scaled stack in L6M (MDE +3.1k), +1.4k in HOLD. maxDD-matched c* 1.01 (L6M +1.6k, HOLD +1.2k); SD-matched c* 1.02 (L6M +2.0k, HOLD +1.5k). [CANDIDATE-RECENT]
76. **B|L2SL|COMBO_RANK** (loss-health L2SL cells (tighten/cut); looked(L6M-ranked)): at equal worst-20-weeks, B|L2SL|COMBO_RANK runs 1.05x lots (95% CI 0.90-1.18) and makes +1.6k $/wk more than the stack as it is in L6M (MDE 20.8k), +2.7k in HOLD, -21.6k in PRE; absolute L6M +67.3k vs stack +65.7k, HOLD +55.1k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.95): rule +1.5k vs scaled stack in L6M (MDE +19.9k), +2.6k in HOLD. maxDD-matched c* 1.10 (L6M +4.9k, HOLD +5.4k); SD-matched c* 1.11 (L6M +5.4k, HOLD +5.8k). [CANDIDATE-RECENT]
77. **E|SL|PB|NY|G2k70** (session-lock NY G2k70; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PB|NY|G2k70 runs 1.01x lots (95% CI 1.00-1.03) and makes +1.6k $/wk more than the stack as it is in L6M (MDE 2.4k), +1.1k in HOLD, -0.3k in PRE; absolute L6M +72.4k vs stack +70.8k, HOLD +58.3k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.99): rule +1.6k vs scaled stack in L6M (MDE +2.4k), +1.1k in HOLD. maxDD-matched c* 1.00 (L6M +0.7k, HOLD +0.3k); SD-matched c* 1.01 (L6M +1.6k, HOLD +1.1k). [CANDIDATE-RECENT]
78. **E|SL|PB|NY|P2+L2** (session-lock NY P2+L2; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PB|NY|P2+L2 runs 1.02x lots (95% CI 1.00-1.05) and makes +1.5k $/wk more than the stack as it is in L6M (MDE 4.0k), +1.2k in HOLD, -0.3k in PRE; absolute L6M +72.3k vs stack +70.8k, HOLD +58.4k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.98): rule +1.5k vs scaled stack in L6M (MDE +3.9k), +1.2k in HOLD. maxDD-matched c* 1.03 (L6M +2.1k, HOLD +1.7k); SD-matched c* 1.02 (L6M +1.5k, HOLD +1.2k). [CANDIDATE-RECENT]
79. **A|H|L|M** (loss: L2SL cut/tighten; PRE-selected): at equal worst-20-weeks, A|H|L|M runs 1.09x lots (95% CI 0.96-1.27) and makes +1.4k $/wk more than the stack as it is in L6M (MDE 33.0k), -4.0k in HOLD, +11.7k in PRE; absolute L6M +20.2k vs stack +18.8k, HOLD +4.6k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.92): rule +1.3k vs scaled stack in L6M (MDE +30.3k), -3.7k in HOLD. maxDD-matched c* 0.93 (L6M -1.5k, HOLD -4.6k); SD-matched c* 1.02 (L6M +0.2k, HOLD -4.2k). [DEAD]
80. **C|D|D_L30t** (concurrency cap D_L30t; registered grid (not selected)): at equal worst-20-weeks, C|D|D_L30t runs 1.11x lots (95% CI 0.98-1.28) and makes +1.4k $/wk more than the stack as it is in L6M (MDE 23.7k), +0.5k in HOLD, -3.8k in PRE; absolute L6M +75.0k vs stack +73.7k, HOLD +54.2k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.90): rule +1.2k vs scaled stack in L6M (MDE +21.4k), +0.5k in HOLD. maxDD-matched c* 1.15 (L6M +4.1k, HOLD +2.5k); SD-matched c* 1.11 (L6M +1.5k, HOLD +0.6k). [CANDIDATE-RECENT]
81. **E|SL|PS|NY|P3+N1** (session-lock NY P3+N1; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PS|NY|P3+N1 runs 1.02x lots (95% CI 0.99-1.04) and makes +1.2k $/wk more than the stack as it is in L6M (MDE 4.1k), +0.9k in HOLD, +0.5k in PRE; absolute L6M +74.3k vs stack +73.0k, HOLD +58.7k vs +57.8k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.98): rule +1.2k vs scaled stack in L6M (MDE +4.0k), +0.8k in HOLD. maxDD-matched c* 1.01 (L6M +0.7k, HOLD +0.4k); SD-matched c* 1.01 (L6M +0.4k, HOLD +0.2k). [CANDIDATE]
82. **E|SL|KB|Asia|P3+L2** (session-lock Asia P3+L2; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|KB|Asia|P3+L2 runs 1.00x lots (95% CI 1.00-1.01) and makes +1.0k $/wk more than the stack as it is in L6M (MDE 3.2k), +0.8k in HOLD, +1.2k in PRE; absolute L6M +71.8k vs stack +70.8k, HOLD +58.0k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.00): rule +1.0k vs scaled stack in L6M (MDE +3.2k), +0.8k in HOLD. maxDD-matched c* 1.00 (L6M +1.1k, HOLD +1.0k); SD-matched c* 1.00 (L6M +1.0k, HOLD +0.8k). [CANDIDATE-RECENT]
83. **E|SL|PS|NY|G2k70** (session-lock NY G2k70; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PS|NY|G2k70 runs 1.00x lots (95% CI 1.00-1.01) and makes +0.9k $/wk more than the stack as it is in L6M (MDE 3.0k), +0.8k in HOLD, +0.1k in PRE; absolute L6M +74.0k vs stack +73.0k, HOLD +58.6k vs +57.8k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.00): rule +0.9k vs scaled stack in L6M (MDE +3.0k), +0.8k in HOLD. maxDD-matched c* 1.01 (L6M +1.5k, HOLD +1.3k); SD-matched c* 1.00 (L6M +0.7k, HOLD +0.6k). [CANDIDATE]
84. **E|SL|KB|Asia|P3** (session-lock Asia P3; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|KB|Asia|P3 runs 1.00x lots (95% CI 1.00-1.00) and makes +0.8k $/wk more than the stack as it is in L6M (MDE 2.3k), +0.7k in HOLD, +0.6k in PRE; absolute L6M +71.7k vs stack +70.8k, HOLD +57.9k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.00): rule +0.8k vs scaled stack in L6M (MDE +2.3k), +0.7k in HOLD. maxDD-matched c* 1.00 (L6M +1.1k, HOLD +1.0k); SD-matched c* 1.00 (L6M +1.0k, HOLD +0.9k). [CANDIDATE]
85. **E|SL|WT|Asia|P1+L1** (session-lock Asia P1+L1; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|WT|Asia|P1+L1 runs 1.03x lots (95% CI 0.97-1.07) and makes +0.5k $/wk more than the stack as it is in L6M (MDE 9.1k), +0.7k in HOLD, +2.1k in PRE; absolute L6M +71.3k vs stack +70.8k, HOLD +57.9k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.97): rule +0.5k vs scaled stack in L6M (MDE +8.9k), +0.7k in HOLD. maxDD-matched c* 1.03 (L6M +0.5k, HOLD +0.8k); SD-matched c* 1.01 (L6M -1.1k, HOLD -0.5k). [DEAD]
86. **B|L2SL|HM_PRE** (loss-health L2SL cells (tighten/cut); PRE-selected): at equal worst-20-weeks, B|L2SL|HM_PRE runs 1.04x lots (95% CI 0.95-1.14) and makes +0.4k $/wk more than the stack as it is in L6M (MDE 13.2k), -1.2k in HOLD, +5.4k in PRE; absolute L6M +66.1k vs stack +65.7k, HOLD +51.3k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.96): rule +0.4k vs scaled stack in L6M (MDE +12.7k), -1.1k in HOLD. maxDD-matched c* 0.90 (L6M -8.7k, HOLD -8.3k); SD-matched c* 1.04 (L6M +0.4k, HOLD -1.2k). [DEAD]
87. **E|SL|HM|NY|P1+L1.5** (session-lock NY P1+L1.5; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|HM|NY|P1+L1.5 runs 1.03x lots (95% CI 0.99-1.08) and makes +0.4k $/wk more than the stack as it is in L6M (MDE 13.0k), +1.6k in HOLD, +0.7k in PRE; absolute L6M +71.2k vs stack +70.8k, HOLD +58.8k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.97): rule +0.4k vs scaled stack in L6M (MDE +12.6k), +1.6k in HOLD. maxDD-matched c* 1.04 (L6M +1.2k, HOLD +2.3k); SD-matched c* 1.02 (L6M -0.3k, HOLD +1.1k). [CANDIDATE-RECENT]
88. **E|SL|PB|London|P3+L1.5** (session-lock London P3+L1.5; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PB|London|P3+L1.5 runs 1.03x lots (95% CI 0.98-1.07) and makes +0.4k $/wk more than the stack as it is in L6M (MDE 5.1k), +0.3k in HOLD, +2.4k in PRE; absolute L6M +71.2k vs stack +70.8k, HOLD +57.5k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.97): rule +0.4k vs scaled stack in L6M (MDE +5.0k), +0.3k in HOLD. maxDD-matched c* 1.02 (L6M +0.2k, HOLD +0.1k); SD-matched c* 1.02 (L6M -0.2k, HOLD -0.2k). [CANDIDATE-RECENT]
89. **E|SL|PS|NY|P3+L2** (session-lock NY P3+L2; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PS|NY|P3+L2 runs 1.00x lots (95% CI 1.00-1.01) and makes +0.3k $/wk more than the stack as it is in L6M (MDE 1.3k), +0.2k in HOLD, -0.0k in PRE; absolute L6M +73.3k vs stack +73.0k, HOLD +58.0k vs +57.8k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.00): rule +0.3k vs scaled stack in L6M (MDE +1.3k), +0.2k in HOLD. maxDD-matched c* 1.02 (L6M +1.1k, HOLD +0.9k); SD-matched c* 1.00 (L6M +0.4k, HOLD +0.3k). [CANDIDATE-RECENT]
90. **C|D|D_B3s** (concurrency cap D_B3s; registered grid (not selected)): at equal worst-20-weeks, C|D|D_B3s runs 1.19x lots (95% CI 0.98-1.44) and makes +0.2k $/wk more than the stack as it is in L6M (MDE 34.4k), -1.4k in HOLD, -8.3k in PRE; absolute L6M +73.8k vs stack +73.7k, HOLD +52.3k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.84): rule +0.1k vs scaled stack in L6M (MDE +28.8k), -1.1k in HOLD. maxDD-matched c* 1.24 (L6M +2.9k, HOLD +0.6k); SD-matched c* 1.19 (L6M -0.0k, HOLD -1.5k). [DEAD]
91. **C|A|A01** (slot/pool block-halve A01_blk_strict_pool; registered grid (not selected)): at equal worst-20-weeks, C|A|A01 runs 0.99x lots (95% CI 0.93-1.05) and makes +0.1k $/wk more than the stack as it is in L6M (MDE 8.6k), +0.9k in HOLD, -0.3k in PRE; absolute L6M +73.8k vs stack +73.7k, HOLD +54.6k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.01): rule +0.1k vs scaled stack in L6M (MDE +8.6k), +0.9k in HOLD. maxDD-matched c* 1.03 (L6M +2.9k, HOLD +2.9k); SD-matched c* 1.00 (L6M +0.4k, HOLD +1.1k). [DEAD]
92. **E|SL|PS|NY|P3+L1.5** (session-lock NY P3+L1.5; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PS|NY|P3+L1.5 runs 1.01x lots (95% CI 0.99-1.03) and makes -0.1k $/wk less than the stack as it is in L6M (MDE 2.2k), -0.3k in HOLD, +0.5k in PRE; absolute L6M +73.0k vs stack +73.0k, HOLD +57.5k vs +57.8k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.99): rule -0.1k vs scaled stack in L6M (MDE +2.1k), -0.3k in HOLD. maxDD-matched c* 1.01 (L6M -0.3k, HOLD -0.6k); SD-matched c* 1.01 (L6M -0.2k, HOLD -0.4k). [DEAD]
93. **E|SL|PS|NY|L2** (session-lock NY L2; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PS|NY|L2 runs 1.00x lots (95% CI 0.99-1.01) and makes -0.1k $/wk less than the stack as it is in L6M (MDE 1.3k), -0.1k in HOLD, -0.3k in PRE; absolute L6M +72.9k vs stack +73.0k, HOLD +57.7k vs +57.8k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.00): rule -0.1k vs scaled stack in L6M (MDE +1.3k), -0.1k in HOLD. maxDD-matched c* 1.00 (L6M +0.2k, HOLD +0.2k); SD-matched c* 1.00 (L6M +0.3k, HOLD +0.3k). [DEAD]
94. **A|B|P|N** (profit: plain 70% take; looked(L6M-ranked)): at equal worst-20-weeks, A|B|P|N runs 1.08x lots (95% CI 0.93-1.29) and makes -0.2k $/wk less than the stack as it is in L6M (MDE 38.8k), +1.6k in HOLD, -20.5k in PRE; absolute L6M +61.3k vs stack +61.5k, HOLD +50.0k vs +48.3k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.92): rule -0.2k vs scaled stack in L6M (MDE +35.8k), +1.5k in HOLD. maxDD-matched c* 1.29 (L6M +11.3k, HOLD +11.0k); SD-matched c* 1.14 (L6M +3.0k, HOLD +4.3k). [DEAD]
95. **B|EXP2|B_U3** (EXP2 joint (bracket tilt/TH profit/TH loss); PRE-selected): at equal worst-20-weeks, B|EXP2|B_U3 runs 1.02x lots (95% CI 0.97-1.06) and makes -0.3k $/wk less than the stack as it is in L6M (MDE 9.0k), -0.5k in HOLD, +5.5k in PRE; absolute L6M +65.4k vs stack +65.7k, HOLD +51.9k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.98): rule -0.3k vs scaled stack in L6M (MDE +8.8k), -0.5k in HOLD. maxDD-matched c* 0.98 (L6M -2.5k, HOLD -2.3k); SD-matched c* 1.00 (L6M -1.5k, HOLD -1.5k). [DEAD]
96. **C|A|A07** (slot/pool block-halve A07_blk_loose_pool_rng; registered grid (not selected)): at equal worst-20-weeks, C|A|A07 runs 1.01x lots (95% CI 0.93-1.10) and makes -0.3k $/wk less than the stack as it is in L6M (MDE 18.8k), -1.7k in HOLD, -3.4k in PRE; absolute L6M +73.4k vs stack +73.7k, HOLD +52.0k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.99): rule -0.3k vs scaled stack in L6M (MDE +18.7k), -1.7k in HOLD. maxDD-matched c* 0.96 (L6M -3.9k, HOLD -4.2k); SD-matched c* 1.03 (L6M +1.4k, HOLD -0.5k). [DEAD]
97. **C|D|D_B3e** (concurrency cap D_B3e; registered grid (not selected)): at equal worst-20-weeks, C|D|D_B3e runs 1.14x lots (95% CI 0.96-1.38) and makes -0.5k $/wk less than the stack as it is in L6M (MDE 30.8k), -1.9k in HOLD, -11.5k in PRE; absolute L6M +73.2k vs stack +73.7k, HOLD +51.8k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.88): rule -0.4k vs scaled stack in L6M (MDE +27.0k), -1.7k in HOLD. maxDD-matched c* 1.23 (L6M +5.4k, HOLD +2.2k); SD-matched c* 1.16 (L6M +0.5k, HOLD -1.2k). [DEAD]
98. **E|SL|ST|Asia|P1.5+N3** (session-lock Asia P1.5+N3; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|ST|Asia|P1.5+N3 runs 1.01x lots (95% CI 0.98-1.05) and makes -0.6k $/wk less than the stack as it is in L6M (MDE 14.6k), -0.5k in HOLD, +3.4k in PRE; absolute L6M +70.3k vs stack +70.8k, HOLD +56.7k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.99): rule -0.6k vs scaled stack in L6M (MDE +14.4k), -0.5k in HOLD. maxDD-matched c* 1.02 (L6M -0.0k, HOLD -0.1k); SD-matched c* 1.00 (L6M -1.5k, HOLD -1.3k). [DEAD]
99. **B|EXP2|P** (EXP2 joint (bracket tilt/TH profit/TH loss); PRE-selected): at equal worst-20-weeks, B|EXP2|P runs 0.98x lots (95% CI 0.82-1.14) and makes -0.7k $/wk less than the stack as it is in L6M (MDE 18.5k), -5.6k in HOLD, -6.5k in PRE; absolute L6M +65.0k vs stack +65.7k, HOLD +46.8k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.02): rule -0.7k vs scaled stack in L6M (MDE +18.8k), -5.7k in HOLD. maxDD-matched c* 1.06 (L6M +4.7k, HOLD -1.7k); SD-matched c* 1.00 (L6M +0.8k, HOLD -4.5k). [DEAD]
100. **B|L2SL|SM_PRE** (loss-health L2SL cells (tighten/cut); PRE-selected): at equal worst-20-weeks, B|L2SL|SM_PRE runs 0.98x lots (95% CI 0.93-1.02) and makes -1.2k $/wk less than the stack as it is in L6M (MDE 4.9k), -1.3k in HOLD, -2.3k in PRE; absolute L6M +64.5k vs stack +65.7k, HOLD +51.2k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.02): rule -1.2k vs scaled stack in L6M (MDE +5.0k), -1.3k in HOLD. maxDD-matched c* 1.00 (L6M -0.3k, HOLD -0.6k); SD-matched c* 1.00 (L6M +0.2k, HOLD -0.2k). [DEAD]
101. **E|SL|PS|London|N2** (session-lock London N2; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|PS|London|N2 runs 1.00x lots (95% CI 0.98-1.02) and makes -1.2k $/wk less than the stack as it is in L6M (MDE 3.3k), -0.9k in HOLD, +0.8k in PRE; absolute L6M +71.8k vs stack +73.0k, HOLD +56.9k vs +57.8k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.00): rule -1.2k vs scaled stack in L6M (MDE +3.3k), -0.9k in HOLD. maxDD-matched c* 1.02 (L6M -0.2k, HOLD -0.1k); SD-matched c* 1.00 (L6M -1.4k, HOLD -1.1k). [DEAD]
102. **A|H|EP|N** (entry+profit; PRE-selected): at equal worst-20-weeks, A|H|EP|N runs 1.11x lots (95% CI 0.94-1.35) and makes -1.5k $/wk less than the stack as it is in L6M (MDE 51.4k), -1.5k in HOLD, -25.8k in PRE; absolute L6M +60.0k vs stack +61.5k, HOLD +46.8k vs +48.3k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.90): rule -1.3k vs scaled stack in L6M (MDE +46.3k), -1.4k in HOLD. maxDD-matched c* 1.25 (L6M +6.1k, HOLD +4.4k); SD-matched c* 1.21 (L6M +4.0k, HOLD +2.7k). [DEAD]
103. **E|SL|ST|NY|N2** (session-lock NY N2; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|ST|NY|N2 runs 1.02x lots (95% CI 0.99-1.04) and makes -1.7k $/wk less than the stack as it is in L6M (MDE 8.6k), -1.4k in HOLD, +1.4k in PRE; absolute L6M +69.1k vs stack +70.8k, HOLD +55.8k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.98): rule -1.7k vs scaled stack in L6M (MDE +8.5k), -1.4k in HOLD. maxDD-matched c* 1.03 (L6M -1.0k, HOLD -0.8k); SD-matched c* 1.01 (L6M -2.2k, HOLD -1.8k). [DEAD]
104. **E|SL|ST|NY|P3+N2** (session-lock NY P3+N2; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|ST|NY|P3+N2 runs 1.02x lots (95% CI 0.99-1.05) and makes -2.6k $/wk less than the stack as it is in L6M (MDE 9.4k), -2.5k in HOLD, +1.5k in PRE; absolute L6M +68.2k vs stack +70.8k, HOLD +54.7k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.98): rule -2.6k vs scaled stack in L6M (MDE +9.3k), -2.5k in HOLD. maxDD-matched c* 1.01 (L6M -3.2k, HOLD -3.0k); SD-matched c* 1.02 (L6M -2.6k, HOLD -2.5k). [DEAD]
105. **B|EXP2|B_U3_P** (EXP2 joint (bracket tilt/TH profit/TH loss); PRE-selected): at equal worst-20-weeks, B|EXP2|B_U3_P runs 0.98x lots (95% CI 0.81-1.15) and makes -2.7k $/wk less than the stack as it is in L6M (MDE 20.4k), -7.9k in HOLD, -3.3k in PRE; absolute L6M +63.0k vs stack +65.7k, HOLD +44.6k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.02): rule -2.7k vs scaled stack in L6M (MDE +20.7k), -8.0k in HOLD. maxDD-matched c* 1.02 (L6M -0.0k, HOLD -6.0k); SD-matched c* 1.00 (L6M -1.5k, HOLD -7.1k). [DEAD]
106. **E|SL|ST|Asia|P1.5+L2** (session-lock Asia P1.5+L2; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|ST|Asia|P1.5+L2 runs 1.01x lots (95% CI 0.98-1.04) and makes -2.9k $/wk less than the stack as it is in L6M (MDE 10.4k), -2.6k in HOLD, +2.8k in PRE; absolute L6M +67.9k vs stack +70.8k, HOLD +54.6k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.99): rule -2.8k vs scaled stack in L6M (MDE +10.2k), -2.5k in HOLD. maxDD-matched c* 1.02 (L6M -2.4k, HOLD -2.2k); SD-matched c* 1.00 (L6M -4.0k, HOLD -3.5k). [DEAD]
107. **B|L2SL|KB_RANK** (loss-health L2SL cells (tighten/cut); looked(L6M-ranked)): at equal worst-20-weeks, B|L2SL|KB_RANK runs 0.98x lots (95% CI 0.94-1.00) and makes -2.9k $/wk less than the stack as it is in L6M (MDE 3.8k), -2.7k in HOLD, -5.7k in PRE; absolute L6M +62.7k vs stack +65.7k, HOLD +49.8k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.02): rule -3.0k vs scaled stack in L6M (MDE +3.9k), -2.7k in HOLD. maxDD-matched c* 0.99 (L6M -2.2k, HOLD -2.1k); SD-matched c* 0.99 (L6M -2.7k, HOLD -2.5k). [DEAD]
108. **B|L2SL|ST_RANK** (loss-health L2SL cells (tighten/cut); looked(L6M-ranked)): at equal worst-20-weeks, B|L2SL|ST_RANK runs 1.00x lots (95% CI 0.92-1.07) and makes -3.1k $/wk less than the stack as it is in L6M (MDE 17.7k), -1.5k in HOLD, -4.9k in PRE; absolute L6M +62.6k vs stack +65.7k, HOLD +50.9k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.00): rule -3.1k vs scaled stack in L6M (MDE +17.6k), -1.5k in HOLD. maxDD-matched c* 1.07 (L6M +1.3k, HOLD +2.0k); SD-matched c* 1.02 (L6M -1.9k, HOLD -0.6k). [DEAD]
109. **B|L2SL|KB_PRE** (loss-health L2SL cells (tighten/cut); PRE-selected): at equal worst-20-weeks, B|L2SL|KB_PRE runs 0.97x lots (95% CI 0.93-1.01) and makes -3.2k $/wk less than the stack as it is in L6M (MDE 5.6k), -2.6k in HOLD, -5.3k in PRE; absolute L6M +62.5k vs stack +65.7k, HOLD +49.9k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.03): rule -3.3k vs scaled stack in L6M (MDE +5.7k), -2.7k in HOLD. maxDD-matched c* 1.00 (L6M -1.9k, HOLD -1.5k); SD-matched c* 0.98 (L6M -2.7k, HOLD -2.2k). [DEAD]
110. **A|H|P|N** (profit: plain 70% take; PRE-selected): at equal worst-20-weeks, A|H|P|N runs 1.10x lots (95% CI 0.92-1.34) and makes -3.5k $/wk less than the stack as it is in L6M (MDE 49.8k), -1.8k in HOLD, -29.0k in PRE; absolute L6M +58.0k vs stack +61.5k, HOLD +46.6k vs +48.3k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.91): rule -3.2k vs scaled stack in L6M (MDE +45.1k), -1.6k in HOLD. maxDD-matched c* 1.35 (L6M +9.2k, HOLD +8.4k); SD-matched c* 1.20 (L6M +1.6k, HOLD +2.3k). [DEAD]
111. **F|CW|HM** (cut-and-wait HM (book PRE-best cell, other books as is); PRE-selected): at equal worst-20-weeks, F|CW|HM runs 1.03x lots (95% CI 0.95-1.13) and makes -3.5k $/wk less than the stack as it is in L6M (MDE 24.7k), -5.3k in HOLD, +4.5k in PRE; absolute L6M +27.0k vs stack +30.5k, HOLD +16.6k vs +21.9k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.97): rule -3.4k vs scaled stack in L6M (MDE +23.9k), -5.1k in HOLD. maxDD-matched c* 0.76 (L6M -10.6k, HOLD -9.6k); SD-matched c* 1.04 (L6M -3.2k, HOLD -5.1k). [DEAD]
112. **B|L2SL|WT_RANK** (loss-health L2SL cells (tighten/cut); looked(L6M-ranked)): at equal worst-20-weeks, B|L2SL|WT_RANK runs 1.00x lots (95% CI 0.96-1.05) and makes -3.8k $/wk less than the stack as it is in L6M (MDE 7.0k), -3.2k in HOLD, -2.9k in PRE; absolute L6M +61.9k vs stack +65.7k, HOLD +49.2k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.00): rule -3.7k vs scaled stack in L6M (MDE +7.0k), -3.2k in HOLD. maxDD-matched c* 1.00 (L6M -3.8k, HOLD -3.3k); SD-matched c* 1.02 (L6M -3.1k, HOLD -2.7k). [DEAD]
113. **C|D|D_B3h** (concurrency cap D_B3h; registered grid (not selected)): at equal worst-20-weeks, C|D|D_B3h runs 1.17x lots (95% CI 1.01-1.31) and makes -4.0k $/wk less than the stack as it is in L6M (MDE 26.6k), -6.6k in HOLD, -0.9k in PRE; absolute L6M +69.6k vs stack +73.7k, HOLD +47.0k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.86): rule -3.5k vs scaled stack in L6M (MDE +22.8k), -5.7k in HOLD. maxDD-matched c* 1.15 (L6M -5.1k, HOLD -7.3k); SD-matched c* 1.13 (L6M -6.0k, HOLD -7.9k). [DEAD]
114. **B|L2SL|WT_PRE** (loss-health L2SL cells (tighten/cut); PRE-selected): at equal worst-20-weeks, B|L2SL|WT_PRE runs 0.98x lots (95% CI 0.94-1.01) and makes -4.5k $/wk less than the stack as it is in L6M (MDE 6.0k), -4.4k in HOLD, -4.5k in PRE; absolute L6M +61.2k vs stack +65.7k, HOLD +48.1k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.02): rule -4.6k vs scaled stack in L6M (MDE +6.1k), -4.5k in HOLD. maxDD-matched c* 0.99 (L6M -4.0k, HOLD -4.0k); SD-matched c* 1.00 (L6M -3.1k, HOLD -3.3k). [DEAD]
115. **B|L2SL|PE_PRE** (loss-health L2SL cells (tighten/cut); PRE-selected): at equal worst-20-weeks, B|L2SL|PE_PRE runs 1.01x lots (95% CI 0.97-1.05) and makes -4.6k $/wk less than the stack as it is in L6M (MDE 8.2k), -3.6k in HOLD, +2.3k in PRE; absolute L6M +61.0k vs stack +65.7k, HOLD +48.8k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.99): rule -4.6k vs scaled stack in L6M (MDE +8.1k), -3.6k in HOLD. maxDD-matched c* 1.02 (L6M -4.1k, HOLD -3.2k); SD-matched c* 1.01 (L6M -4.6k, HOLD -3.6k). [DEAD]
116. **B|L2SL|PE_RANK** (loss-health L2SL cells (tighten/cut); looked(L6M-ranked)): at equal worst-20-weeks, B|L2SL|PE_RANK runs 0.99x lots (95% CI 0.92-1.04) and makes -4.8k $/wk less than the stack as it is in L6M (MDE 7.5k), -3.6k in HOLD, -3.6k in PRE; absolute L6M +60.9k vs stack +65.7k, HOLD +48.9k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.01): rule -4.8k vs scaled stack in L6M (MDE +7.5k), -3.6k in HOLD. maxDD-matched c* 1.05 (L6M -0.9k, HOLD -0.5k); SD-matched c* 1.03 (L6M -2.4k, HOLD -1.7k). [DEAD]
117. **B|L2SL|ST_PRE** (loss-health L2SL cells (tighten/cut); PRE-selected): at equal worst-20-weeks, B|L2SL|ST_PRE runs 1.03x lots (95% CI 0.95-1.10) and makes -5.5k $/wk less than the stack as it is in L6M (MDE 20.2k), -4.5k in HOLD, -0.3k in PRE; absolute L6M +60.2k vs stack +65.7k, HOLD +47.9k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.98): rule -5.4k vs scaled stack in L6M (MDE +19.7k), -4.4k in HOLD. maxDD-matched c* 1.01 (L6M -6.5k, HOLD -5.4k); SD-matched c* 1.02 (L6M -5.5k, HOLD -4.6k). [DEAD]
118. **H|L2SP|ALL_PRE_selected|N** (profit-health exits (L2SP six books); PRE-selected): at equal worst-20-weeks, H|L2SP|ALL_PRE_selected|N runs 1.09x lots (95% CI 0.96-1.20) and makes -5.5k $/wk less than the stack as it is in L6M (MDE 22.5k), -5.9k in HOLD, -5.0k in PRE; absolute L6M +56.8k vs stack +62.3k, HOLD +46.5k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.92): rule -5.1k vs scaled stack in L6M (MDE +20.6k), -5.4k in HOLD. maxDD-matched c* 1.09 (L6M -5.4k, HOLD -5.9k); SD-matched c* 1.11 (L6M -4.6k, HOLD -5.2k). [DEAD]
119. **A|H|EPL|N** (joint entry+profit+loss; PRE-selected): at equal worst-20-weeks, A|H|EPL|N runs 1.19x lots (95% CI 1.00-1.44) and makes -5.9k $/wk less than the stack as it is in L6M (MDE 64.0k), -11.4k in HOLD, -12.5k in PRE; absolute L6M +55.6k vs stack +61.5k, HOLD +36.9k vs +48.3k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.84): rule -5.0k vs scaled stack in L6M (MDE +53.9k), -9.6k in HOLD. maxDD-matched c* 1.05 (L6M -12.5k, HOLD -15.8k); SD-matched c* 1.26 (L6M -2.4k, HOLD -9.0k). [DEAD]
120. **E|SL|ST|Asia|P1.5+N2** (session-lock Asia P1.5+N2; registered grid (all 798 cells), picked as insurance-flagged): at equal worst-20-weeks, E|SL|ST|Asia|P1.5+N2 runs 1.02x lots (95% CI 0.98-1.05) and makes -6.7k $/wk less than the stack as it is in L6M (MDE 13.1k), -6.0k in HOLD, +4.5k in PRE; absolute L6M +64.1k vs stack +70.8k, HOLD +51.2k vs +57.2k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.98): rule -6.6k vs scaled stack in L6M (MDE +12.9k), -5.9k in HOLD. maxDD-matched c* 1.02 (L6M -6.5k, HOLD -5.7k); SD-matched c* 1.00 (L6M -7.6k, HOLD -6.7k). [DEAD]
121. **C|A|A02** (slot/pool block-halve A02_blk_loose_pool; registered grid (not selected)): at equal worst-20-weeks, C|A|A02 runs 1.13x lots (95% CI 0.96-1.32) and makes -7.0k $/wk less than the stack as it is in L6M (MDE 38.1k), -5.1k in HOLD, +8.1k in PRE; absolute L6M +66.6k vs stack +73.7k, HOLD +48.6k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.88): rule -6.2k vs scaled stack in L6M (MDE +33.6k), -4.5k in HOLD. maxDD-matched c* 1.23 (L6M -1.6k, HOLD -1.1k); SD-matched c* 1.12 (L6M -7.6k, HOLD -5.4k). [DEAD]
122. **F|CW|ST** (cut-and-wait ST (book PRE-best cell, other books as is); PRE-selected): at equal worst-20-weeks, F|CW|ST runs 1.10x lots (95% CI 0.99-1.22) and makes -7.1k $/wk less than the stack as it is in L6M (MDE 24.5k), -6.6k in HOLD, +3.0k in PRE; absolute L6M +23.4k vs stack +30.5k, HOLD +15.3k vs +21.9k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.91): rule -6.5k vs scaled stack in L6M (MDE +22.2k), -6.0k in HOLD. maxDD-matched c* 1.12 (L6M -6.8k, HOLD -6.4k); SD-matched c* 1.07 (L6M -7.8k, HOLD -7.1k). [DEAD]
123. **A|H|PL|N** (profit+loss; PRE-selected): at equal worst-20-weeks, A|H|PL|N runs 1.17x lots (95% CI 0.99-1.44) and makes -7.5k $/wk less than the stack as it is in L6M (MDE 65.9k), -10.9k in HOLD, -17.4k in PRE; absolute L6M +53.9k vs stack +61.5k, HOLD +37.4k vs +48.3k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.85): rule -6.4k vs scaled stack in L6M (MDE +56.3k), -9.3k in HOLD. maxDD-matched c* 1.10 (L6M -10.8k, HOLD -13.2k); SD-matched c* 1.25 (L6M -4.1k, HOLD -8.5k). [DEAD]
124. **B|EXP2|B_FROZEN_P** (EXP2 joint (bracket tilt/TH profit/TH loss); PRE-selected): at equal worst-20-weeks, B|EXP2|B_FROZEN_P runs 1.20x lots (95% CI 0.88-1.58) and makes -9.4k $/wk less than the stack as it is in L6M (MDE 76.5k), -3.1k in HOLD, -7.9k in PRE; absolute L6M +56.2k vs stack +65.7k, HOLD +49.4k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.84): rule -7.9k vs scaled stack in L6M (MDE +63.9k), -2.6k in HOLD. maxDD-matched c* 1.21 (L6M -8.7k, HOLD -2.5k); SD-matched c* 1.20 (L6M -9.2k, HOLD -2.9k). [DEAD]
125. **F|CW|PE** (cut-and-wait PE (book PRE-best cell, other books as is); PRE-selected): at equal worst-20-weeks, F|CW|PE runs 1.10x lots (95% CI 1.01-1.18) and makes -11.3k $/wk less than the stack as it is in L6M (MDE 23.2k), -8.8k in HOLD, +3.7k in PRE; absolute L6M +19.2k vs stack +30.5k, HOLD +13.1k vs +21.9k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.91): rule -10.3k vs scaled stack in L6M (MDE +21.1k), -8.0k in HOLD. maxDD-matched c* 1.10 (L6M -11.2k, HOLD -8.8k); SD-matched c* 1.08 (L6M -11.6k, HOLD -9.0k). [DEAD]
126. **D|D6L_alone** (D6-LIVE dip entry (3-of-8 + dip 10 + imb5 veto); pre-specified rule): at equal worst-20-weeks, D|D6L_alone runs 1.18x lots (95% CI 0.91-1.51) and makes -12.0k $/wk less than the stack as it is in L6M (MDE 61.9k), -8.5k in HOLD, -30.3k in PRE; absolute L6M +6.9k vs stack +18.8k, HOLD +0.1k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.85): rule -10.2k vs scaled stack in L6M (MDE +52.7k), -7.2k in HOLD. maxDD-matched c* 0.72 (L6M -14.6k, HOLD -8.5k); SD-matched c* 1.30 (L6M -11.3k, HOLD -8.5k). [DEAD]
127. **B|L2SL|ALL_PRE** (loss-health L2SL cells (tighten/cut); PRE-selected): at equal worst-20-weeks, B|L2SL|ALL_PRE runs 1.07x lots (95% CI 0.90-1.27) and makes -15.8k $/wk less than the stack as it is in L6M (MDE 32.1k), -15.2k in HOLD, -7.2k in PRE; absolute L6M +49.9k vs stack +65.7k, HOLD +37.2k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.94): rule -14.8k vs scaled stack in L6M (MDE +30.2k), -14.3k in HOLD. maxDD-matched c* 0.94 (L6M -21.9k, HOLD -19.8k); SD-matched c* 1.08 (L6M -15.0k, HOLD -14.6k). [DEAD]
128. **D|PROFIT_alone** (ADD2 profit rule; pre-specified rule): at equal worst-20-weeks, D|PROFIT_alone runs 0.98x lots (95% CI 0.84-1.16) and makes -16.3k $/wk less than the stack as it is in L6M (MDE 38.3k), -16.3k in HOLD, -9.8k in PRE; absolute L6M +2.5k vs stack +18.8k, HOLD -7.7k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.02): rule -16.7k vs scaled stack in L6M (MDE +39.1k), -16.7k in HOLD. maxDD-matched c* 1.03 (L6M -16.2k, HOLD -16.7k); SD-matched c* 1.05 (L6M -16.1k, HOLD -16.9k). [DEAD]
129. **B|L2SL|COMBO_PRE** (loss-health L2SL cells (tighten/cut); PRE-selected): at equal worst-20-weeks, B|L2SL|COMBO_PRE runs 1.03x lots (95% CI 0.90-1.17) and makes -17.8k $/wk less than the stack as it is in L6M (MDE 23.6k), -17.1k in HOLD, -4.5k in PRE; absolute L6M +47.9k vs stack +65.7k, HOLD +35.4k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.97): rule -17.3k vs scaled stack in L6M (MDE +22.9k), -16.5k in HOLD. maxDD-matched c* 0.90 (L6M -23.8k, HOLD -21.5k); SD-matched c* 1.07 (L6M -15.8k, HOLD -15.6k). [DEAD]
130. **B|EXP2|B_FROZEN** (EXP2 joint (bracket tilt/TH profit/TH loss); PRE-selected): at equal worst-20-weeks, B|EXP2|B_FROZEN runs 1.01x lots (95% CI 0.75-1.33) and makes -19.6k $/wk less than the stack as it is in L6M (MDE 71.4k), -14.5k in HOLD, -25.2k in PRE; absolute L6M +46.1k vs stack +65.7k, HOLD +37.9k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.99): rule -19.5k vs scaled stack in L6M (MDE +70.9k), -14.4k in HOLD. maxDD-matched c* 0.76 (L6M -31.1k, HOLD -24.0k); SD-matched c* 1.12 (L6M -14.6k, HOLD -10.4k). [DEAD]
131. **B|EXP2|B_U3_L** (EXP2 joint (bracket tilt/TH profit/TH loss); PRE-selected): at equal worst-20-weeks, B|EXP2|B_U3_L runs 1.05x lots (95% CI 0.85-1.26) and makes -23.6k $/wk less than the stack as it is in L6M (MDE 37.3k), -19.7k in HOLD, -3.6k in PRE; absolute L6M +42.1k vs stack +65.7k, HOLD +32.8k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.95): rule -22.4k vs scaled stack in L6M (MDE +35.4k), -18.7k in HOLD. maxDD-matched c* 1.09 (L6M -22.2k, HOLD -18.6k); SD-matched c* 1.07 (L6M -23.0k, HOLD -19.2k). [DEAD]
132. **B|EXP2|L** (EXP2 joint (bracket tilt/TH profit/TH loss); PRE-selected): at equal worst-20-weeks, B|EXP2|L runs 1.06x lots (95% CI 0.84-1.25) and makes -24.0k $/wk less than the stack as it is in L6M (MDE 34.5k), -19.5k in HOLD, -8.3k in PRE; absolute L6M +41.6k vs stack +65.7k, HOLD +33.0k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.95): rule -22.8k vs scaled stack in L6M (MDE +32.7k), -18.4k in HOLD. maxDD-matched c* 1.17 (L6M -19.4k, HOLD -15.8k); SD-matched c* 1.09 (L6M -22.6k, HOLD -18.4k). [DEAD]
133. **B|EXP2|B_U1_P** (EXP2 joint (bracket tilt/TH profit/TH loss); PRE-selected): at equal worst-20-weeks, B|EXP2|B_U1_P runs 1.01x lots (95% CI 0.76-1.23) and makes -25.9k $/wk less than the stack as it is in L6M (MDE 61.9k), -22.2k in HOLD, -28.5k in PRE; absolute L6M +39.8k vs stack +65.7k, HOLD +30.2k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.99): rule -25.8k vs scaled stack in L6M (MDE +61.5k), -22.1k in HOLD. maxDD-matched c* 0.78 (L6M -34.8k, HOLD -29.0k); SD-matched c* 1.09 (L6M -22.6k, HOLD -19.7k). [DEAD]
134. **F|CW|KB** (cut-and-wait KB (book PRE-best cell, other books as is); PRE-selected): at equal worst-20-weeks, F|CW|KB runs 0.97x lots (95% CI 0.84-1.11) and makes -27.0k $/wk less than the stack as it is in L6M (MDE 32.0k), -26.1k in HOLD, -5.8k in PRE; absolute L6M +3.5k vs stack +30.5k, HOLD -4.2k vs +21.9k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.03): rule -27.8k vs scaled stack in L6M (MDE +32.9k), -26.9k in HOLD. maxDD-matched c* 0.98 (L6M -27.0k, HOLD -26.1k); SD-matched c* 1.02 (L6M -26.8k, HOLD -26.3k). [DEAD]
135. **B|EXP2|B_U1** (EXP2 joint (bracket tilt/TH profit/TH loss); PRE-selected): at equal worst-20-weeks, B|EXP2|B_U1 runs 0.92x lots (95% CI 0.72-1.09) and makes -29.1k $/wk less than the stack as it is in L6M (MDE 59.4k), -27.6k in HOLD, -35.4k in PRE; absolute L6M +36.6k vs stack +65.7k, HOLD +24.9k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.08): rule -31.5k vs scaled stack in L6M (MDE +64.3k), -29.8k in HOLD. maxDD-matched c* 0.62 (L6M -41.0k, HOLD -35.7k); SD-matched c* 1.05 (L6M -24.2k, HOLD -24.2k). [DEAD]
136. **B|EXP2|B_U3_P_L** (EXP2 joint (bracket tilt/TH profit/TH loss); PRE-selected): at equal worst-20-weeks, B|EXP2|B_U3_P_L runs 1.02x lots (95% CI 0.79-1.24) and makes -29.2k $/wk less than the stack as it is in L6M (MDE 31.8k), -30.7k in HOLD, -9.8k in PRE; absolute L6M +36.5k vs stack +65.7k, HOLD +21.8k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.98): rule -28.7k vs scaled stack in L6M (MDE +31.2k), -30.1k in HOLD. maxDD-matched c* 1.17 (L6M -23.7k, HOLD -27.4k); SD-matched c* 1.10 (L6M -26.3k, HOLD -28.9k). [DEAD]
137. **B|EXP2|P_L** (EXP2 joint (bracket tilt/TH profit/TH loss); PRE-selected): at equal worst-20-weeks, B|EXP2|P_L runs 1.03x lots (95% CI 0.80-1.26) and makes -29.4k $/wk less than the stack as it is in L6M (MDE 29.5k), -30.3k in HOLD, -12.5k in PRE; absolute L6M +36.2k vs stack +65.7k, HOLD +22.1k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.97): rule -28.5k vs scaled stack in L6M (MDE +28.6k), -29.4k in HOLD. maxDD-matched c* 1.19 (L6M -24.0k, HOLD -27.0k); SD-matched c* 1.13 (L6M -26.0k, HOLD -28.2k). [DEAD]
138. **D|JOINT3** (ADD2 joint 3; pre-specified rule): at equal worst-20-weeks, D|JOINT3 runs 1.31x lots (95% CI 0.99-1.64) and makes -30.9k $/wk less than the stack as it is in L6M (MDE 63.1k), -25.8k in HOLD, -45.0k in PRE; absolute L6M -12.1k vs stack +18.8k, HOLD -17.3k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.76): rule -23.6k vs scaled stack in L6M (MDE +48.2k), -19.7k in HOLD. maxDD-matched c* 0.45 (L6M -22.9k, HOLD -14.5k); SD-matched c* 1.54 (L6M -34.0k, HOLD -29.8k). [DEAD]
139. **D|JOINT10** (ADD2 joint 10; pre-specified rule): at equal worst-20-weeks, D|JOINT10 runs 1.31x lots (95% CI 1.00-1.65) and makes -31.2k $/wk less than the stack as it is in L6M (MDE 63.3k), -26.1k in HOLD, -45.0k in PRE; absolute L6M -12.4k vs stack +18.8k, HOLD -17.6k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.76): rule -23.7k vs scaled stack in L6M (MDE +48.2k), -19.9k in HOLD. maxDD-matched c* 0.45 (L6M -23.0k, HOLD -14.5k); SD-matched c* 1.54 (L6M -34.3k, HOLD -30.2k). [DEAD]
140. **D|JOINT20** (ADD2 joint 20; pre-specified rule): at equal worst-20-weeks, D|JOINT20 runs 1.34x lots (95% CI 1.06-1.65) and makes -32.1k $/wk less than the stack as it is in L6M (MDE 64.3k), -27.7k in HOLD, -42.3k in PRE; absolute L6M -13.2k vs stack +18.8k, HOLD -19.1k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.75): rule -24.0k vs scaled stack in L6M (MDE +48.1k), -20.7k in HOLD. maxDD-matched c* 0.47 (L6M -23.5k, HOLD -15.3k); SD-matched c* 1.55 (L6M -35.3k, HOLD -31.9k). [DEAD]
141. **D|LOSS20_alone** (ADD2 loss rule 20; pre-specified rule): at equal worst-20-weeks, D|LOSS20_alone runs 1.05x lots (95% CI 0.89-1.22) and makes -32.8k $/wk less than the stack as it is in L6M (MDE 41.2k), -28.1k in HOLD, -35.4k in PRE; absolute L6M -14.0k vs stack +18.8k, HOLD -19.6k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.95): rule -31.2k vs scaled stack in L6M (MDE +39.2k), -26.8k in HOLD. maxDD-matched c* 0.36 (L6M -23.6k, HOLD -15.3k); SD-matched c* 1.20 (L6M -34.8k, HOLD -30.9k). [DEAD]
142. **D|LOSS10_alone** (ADD2 loss rule 10; pre-specified rule): at equal worst-20-weeks, D|LOSS10_alone runs 1.05x lots (95% CI 0.89-1.20) and makes -32.9k $/wk less than the stack as it is in L6M (MDE 41.6k), -28.5k in HOLD, -34.5k in PRE; absolute L6M -14.1k vs stack +18.8k, HOLD -20.0k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.96): rule -31.5k vs scaled stack in L6M (MDE +39.8k), -27.3k in HOLD. maxDD-matched c* 0.36 (L6M -23.7k, HOLD -15.5k); SD-matched c* 1.19 (L6M -34.9k, HOLD -31.4k). [DEAD]
143. **B|EXP2|B_U2_P** (EXP2 joint (bracket tilt/TH profit/TH loss); PRE-selected): at equal worst-20-weeks, B|EXP2|B_U2_P runs 0.96x lots (95% CI 0.68-1.24) and makes -33.4k $/wk less than the stack as it is in L6M (MDE 54.5k), -28.0k in HOLD, -30.9k in PRE; absolute L6M +32.3k vs stack +65.7k, HOLD +24.5k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.04): rule -34.8k vs scaled stack in L6M (MDE +56.8k), -29.2k in HOLD. maxDD-matched c* 0.72 (L6M -41.4k, HOLD -34.0k); SD-matched c* 1.09 (L6M -29.0k, HOLD -24.6k). [DEAD]
144. **D|LOSS3_alone** (ADD2 loss rule 3; pre-specified rule): at equal worst-20-weeks, D|LOSS3_alone runs 1.05x lots (95% CI 0.89-1.20) and makes -34.0k $/wk less than the stack as it is in L6M (MDE 42.3k), -29.3k in HOLD, -35.4k in PRE; absolute L6M -15.1k vs stack +18.8k, HOLD -20.7k vs +8.6k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.96): rule -32.5k vs scaled stack in L6M (MDE +40.4k), -28.0k in HOLD. maxDD-matched c* 0.35 (L6M -23.9k, HOLD -15.6k); SD-matched c* 1.19 (L6M -36.1k, HOLD -32.2k). [DEAD]
145. **B|EXP2|B_U2** (EXP2 joint (bracket tilt/TH profit/TH loss); PRE-selected): at equal worst-20-weeks, B|EXP2|B_U2 runs 0.94x lots (95% CI 0.69-1.19) and makes -34.0k $/wk less than the stack as it is in L6M (MDE 56.6k), -29.6k in HOLD, -29.3k in PRE; absolute L6M +31.6k vs stack +65.7k, HOLD +22.8k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.07): rule -36.4k vs scaled stack in L6M (MDE +60.5k), -31.6k in HOLD. maxDD-matched c* 0.72 (L6M -41.4k, HOLD -34.9k); SD-matched c* 1.08 (L6M -29.0k, HOLD -26.0k). [DEAD]
146. **F|CW|ALL6** (cut-and-wait all six PRE-best cells; PRE-selected): at equal worst-20-weeks, F|CW|ALL6 runs 1.20x lots (95% CI 0.88-1.52) and makes -47.2k $/wk less than the stack as it is in L6M (MDE 68.1k), -50.2k in HOLD, +1.4k in PRE; absolute L6M -16.7k vs stack +30.5k, HOLD -28.3k vs +21.9k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 0.84): rule -39.4k vs scaled stack in L6M (MDE +56.9k), -41.9k in HOLD. maxDD-matched c* 0.70 (L6M -40.2k, HOLD -38.4k); SD-matched c* 1.23 (L6M -47.7k, HOLD -51.0k). [DEAD]
147. **C|A|A10** (slot/pool block-halve A10_ctl_blk_top14_pool; registered grid (not selected)): at equal worst-20-weeks, C|A|A10 runs 0.87x lots (95% CI 0.66-1.11) and makes -51.7k $/wk less than the stack as it is in L6M (MDE 48.4k), -40.7k in HOLD, -51.1k in PRE; absolute L6M +22.0k vs stack +73.7k, HOLD +12.9k vs +53.7k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.15): rule -59.4k vs scaled stack in L6M (MDE +55.7k), -46.8k in HOLD. maxDD-matched c* 0.48 (L6M -61.7k, HOLD -46.6k); SD-matched c* 1.14 (L6M -44.9k, HOLD -36.8k). [DEAD]
148. **B|EXP2|B_U2_L** (EXP2 joint (bracket tilt/TH profit/TH loss); PRE-selected): at equal worst-20-weeks, B|EXP2|B_U2_L runs 0.85x lots (95% CI 0.63-1.05) and makes -55.0k $/wk less than the stack as it is in L6M (MDE 43.6k), -48.1k in HOLD, -45.3k in PRE; absolute L6M +10.7k vs stack +65.7k, HOLD +4.4k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.18): rule -64.8k vs scaled stack in L6M (MDE +51.4k), -56.6k in HOLD. maxDD-matched c* 0.30 (L6M -61.9k, HOLD -50.9k); SD-matched c* 1.12 (L6M -51.6k, HOLD -46.7k). [DEAD]
149. **B|EXP2|B_U2_P_L** (EXP2 joint (bracket tilt/TH profit/TH loss); PRE-selected): at equal worst-20-weeks, B|EXP2|B_U2_P_L runs 0.84x lots (95% CI 0.62-1.08) and makes -55.7k $/wk less than the stack as it is in L6M (MDE 43.2k), -49.9k in HOLD, -43.4k in PRE; absolute L6M +10.0k vs stack +65.7k, HOLD +2.6k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.19): rule -66.1k vs scaled stack in L6M (MDE +51.2k), -59.2k in HOLD. maxDD-matched c* 0.30 (L6M -62.2k, HOLD -51.5k); SD-matched c* 1.09 (L6M -52.7k, HOLD -49.1k). [DEAD]
150. **B|EXP2|B_U1_L** (EXP2 joint (bracket tilt/TH profit/TH loss); PRE-selected): at equal worst-20-weeks, B|EXP2|B_U1_L runs 0.90x lots (95% CI 0.66-1.13) and makes -58.0k $/wk less than the stack as it is in L6M (MDE 50.4k), -50.8k in HOLD, -50.2k in PRE; absolute L6M +7.7k vs stack +65.7k, HOLD +1.7k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.11): rule -64.3k vs scaled stack in L6M (MDE +56.0k), -56.3k in HOLD. maxDD-matched c* 0.30 (L6M -63.1k, HOLD -51.9k); SD-matched c* 1.12 (L6M -56.0k, HOLD -50.3k). [DEAD]
151. **B|EXP2|B_FROZEN_P_L** (EXP2 joint (bracket tilt/TH profit/TH loss); PRE-selected): at equal worst-20-weeks, B|EXP2|B_FROZEN_P_L runs 0.89x lots (95% CI 0.64-1.18) and makes -61.7k $/wk less than the stack as it is in L6M (MDE 56.8k), -53.3k in HOLD, -50.1k in PRE; absolute L6M +4.0k vs stack +65.7k, HOLD -0.8k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.12): rule -69.0k vs scaled stack in L6M (MDE +63.6k), -59.6k in HOLD. maxDD-matched c* 0.32 (L6M -64.3k, HOLD -52.7k); SD-matched c* 1.20 (L6M -60.3k, HOLD -53.6k). [DEAD]
152. **B|EXP2|B_FROZEN_L** (EXP2 joint (bracket tilt/TH profit/TH loss); PRE-selected): at equal worst-20-weeks, B|EXP2|B_FROZEN_L runs 0.84x lots (95% CI 0.60-1.11) and makes -62.7k $/wk less than the stack as it is in L6M (MDE 55.8k), -53.3k in HOLD, -57.6k in PRE; absolute L6M +3.0k vs stack +65.7k, HOLD -0.9k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.19): rule -74.9k vs scaled stack in L6M (MDE +66.7k), -63.7k in HOLD. maxDD-matched c* 0.26 (L6M -64.7k, HOLD -52.7k); SD-matched c* 1.17 (L6M -61.5k, HOLD -53.7k). [DEAD]
153. **B|EXP2|B_U1_P_L** (EXP2 joint (bracket tilt/TH profit/TH loss); PRE-selected): at equal worst-20-weeks, B|EXP2|B_U1_P_L runs 0.91x lots (95% CI 0.67-1.13) and makes -63.3k $/wk less than the stack as it is in L6M (MDE 48.7k), -55.0k in HOLD, -50.7k in PRE; absolute L6M +2.4k vs stack +65.7k, HOLD -2.6k vs +52.4k. Reverse (stack scaled DOWN to the rule's own risk, c_S = 1.10): rule -69.7k vs scaled stack in L6M (MDE +53.6k), -60.6k in HOLD. maxDD-matched c* 0.28 (L6M -65.0k, HOLD -53.2k); SD-matched c* 1.13 (L6M -62.7k, HOLD -55.6k). [DEAD]

## 4. Reverse: the stack as it is scaled DOWN to the rule's risk (worst-20 matched)
Delta_rev = rule at its own lots (c = 1) minus the stack at lots x c_S, same window. Positive = the rule beats a simple lot cut of the stack.
| series | c_S | Y26 | L6M | HOLD | PRE | X' | WF [95% CI] |
|--|--|--|--|--|--|--|--|
| A|B|E|N | 0.70 [0.53,0.87] | +82.5k (94.7k) | +63.2k (30.9k) | +56.4k (28.8k) | -4.5k (23.4k) | -8.6k (20.2k) | +13.8k (20.2k) [-8.3k,+34.4k] |
| A|B|EPL|M | 0.72 [0.56,0.88] | +101.8k (133.1k) | +58.8k (45.1k) | +55.1k (40.3k) | -22.3k (25.6k) | -2.9k (26.1k) | +0.9k (23.8k) [-18.9k,+18.5k] |
| A|B|EL|N | 0.72 [0.56,0.92] | +80.8k (102.5k) | +57.6k (35.1k) | +51.5k (32.8k) | -26.2k (24.1k) | -8.2k (24.8k) | -3.0k (21.9k) [-26.6k,+18.0k] |
| A|B|EP|M | 0.69 [0.54,0.86] | +97.1k (127.5k) | +55.2k (45.0k) | +51.8k (40.0k) | -3.3k (24.7k) | -2.4k (23.5k) | +13.3k (22.3k) [-5.5k,+30.4k] |
| A|B|E|M | 0.73 [0.57,0.88] | +85.1k (112.5k) | +58.0k (34.3k) | +50.5k (32.3k) | -3.5k (22.1k) | -8.3k (20.0k) | +12.7k (19.6k) [-3.4k,+28.8k] |
| A|B|EL|M | 0.74 [0.60,0.91] | +82.2k (109.5k) | +56.7k (38.2k) | +50.1k (35.7k) | -21.1k (21.8k) | -7.2k (24.9k) | +0.2k (20.7k) [-18.0k,+16.1k] |
| H|L2SP|ALL_L6M_rank1|M | 0.84 [0.69,1.05] | +82.1k (100.3k) | +47.1k (40.1k) | +40.7k (36.6k) | -11.7k (22.4k) | +0.4k (27.4k) | +4.0k (20.3k) [-16.6k,+19.8k] |
| A|B|PL|M | 0.87 [0.71,1.02] | +89.2k (143.0k) | +46.0k (42.8k) | +43.0k (38.3k) | -13.7k (24.8k) | +4.2k (22.4k) | +3.3k (22.1k) [-14.5k,+20.8k] |
| A|H|EP|M | 0.82 [0.67,0.95] | +59.0k (130.1k) | +36.0k (43.3k) | +32.8k (38.3k) | +3.5k (20.5k) | +5.1k (24.3k) | +12.4k (18.8k) [-2.0k,+27.8k] |
| A|B|EP|N | 0.74 [0.55,0.94] | +85.6k (119.3k) | +31.5k (43.3k) | +30.2k (38.5k) | -21.7k (27.8k) | -9.8k (24.2k) | -6.2k (23.6k) [-33.1k,+17.0k] |
| A|B|EPL|N | 0.77 [0.58,0.99] | +87.9k (134.3k) | +31.5k (45.7k) | +30.2k (40.9k) | -41.9k (28.8k) | -10.5k (27.0k) | -20.6k (25.4k) [-50.8k,+3.0k] |
| A|H|P|M | 0.83 [0.70,0.95] | +56.5k (118.4k) | +32.8k (40.0k) | +31.5k (35.2k) | +0.5k (19.9k) | +5.3k (24.1k) | +9.9k (18.0k) [-4.2k,+24.9k] |
| A|H|PL|M | 0.78 [0.64,0.90] | +71.6k (160.5k) | +30.2k (51.6k) | +24.2k (46.1k) | +11.1k (18.9k) | +11.4k (24.6k) | +15.2k (19.3k) [+0.7k,+30.8k] |
| A|H|EPL|M | 0.78 [0.63,0.91] | +64.8k (161.4k) | +30.1k (49.7k) | +22.5k (44.9k) | +14.2k (19.4k) | +11.9k (23.6k) | +16.8k (19.2k) [+2.1k,+32.2k] |
| A|B|P|M | 0.86 [0.73,0.97] | +38.8k (83.8k) | +29.5k (32.9k) | +28.4k (29.0k) | +2.1k (18.2k) | +8.3k (19.3k) | +10.1k (15.9k) [-1.7k,+23.0k] |
| G|ADDUW|B1_PRE#1022 | 0.69 [0.52,0.88] | +31.8k (43.2k) | +20.5k (29.1k) | +19.3k (26.7k) | +35.0k (26.3k) | -18.9k (25.7k) | +30.9k (20.2k) [+9.4k,+50.7k] |
| A|B|L|N | 0.92 [0.79,1.05] | +56.5k (63.6k) | +25.5k (27.7k) | +25.2k (24.4k) | -15.6k (20.8k) | -2.2k (16.8k) | -3.4k (17.2k) [-22.3k,+12.2k] |
| A|H|EL|N | 0.85 [0.70,1.00] | +66.6k (86.8k) | +22.4k (41.7k) | +15.8k (38.8k) | +21.5k (15.5k) | +4.7k (14.4k) | +19.9k (16.0k) [+2.2k,+38.3k] |
| A|B|L|M | 0.96 [0.86,1.07] | +51.6k (86.6k) | +24.8k (31.6k) | +22.4k (28.6k) | -14.0k (19.7k) | -2.8k (17.2k) | -3.2k (16.9k) [-17.7k,+9.0k] |
| A|H|E|N | 0.94 [0.85,1.02] | +19.2k (41.2k) | +21.3k (15.4k) | +21.3k (15.1k) | +7.3k (10.7k) | +3.1k (8.3k) | +11.6k (9.0k) [+2.6k,+21.3k] |
| A|B|PL|N | 0.91 [0.74,1.11] | +62.5k (149.1k) | +18.0k (44.0k) | +17.4k (39.1k) | -35.0k (27.4k) | -2.4k (22.7k) | -19.5k (23.5k) [-45.4k,+1.9k] |
| C|D|D_L20s | 0.68 [0.56,0.85] | +55.8k (101.7k) | +12.3k (39.7k) | +9.2k (36.6k) | -6.7k (22.1k) | -14.2k (23.7k) | -0.8k (18.9k) [-20.1k,+16.2k] |
| A|H|L|N | 0.87 [0.72,1.04] | +65.1k (84.5k) | +13.7k (35.8k) | +9.9k (34.9k) | +16.5k (15.5k) | +3.6k (15.4k) | +14.7k (15.2k) [-1.7k,+31.6k] |
| C|A|A05 | 0.87 [0.77,0.99] | +17.7k (44.8k) | +13.2k (21.3k) | +10.0k (19.9k) | +11.4k (14.1k) | -8.7k (12.0k) | +11.1k (11.6k) [-0.6k,+22.2k] |
| A|H|EL|M | 0.88 [0.76,1.01] | +55.7k (65.1k) | +13.2k (35.0k) | +6.9k (32.8k) | +20.9k (15.6k) | +4.0k (14.1k) | +16.8k (14.8k) [+5.0k,+29.1k] |
| B|L2SL|HM_RANK | 0.92 [0.85,0.97] | +11.2k (20.0k) | +13.6k (8.1k) | +11.1k (8.9k) | +2.4k (6.6k) | +0.1k (7.3k) | +5.0k (5.5k) [-0.1k,+11.3k] |
| A|H|E|M | 1.00 [0.91,1.06] | +19.5k (41.6k) | +13.4k (14.5k) | +11.6k (14.0k) | +7.7k (11.3k) | +2.8k (8.4k) | +9.0k (9.0k) [+2.1k,+16.7k] |
| C|A|A04 | 0.78 [0.64,0.92] | +39.4k (47.7k) | +10.3k (22.8k) | +5.8k (22.5k) | +22.8k (17.0k) | -0.1k (19.1k) | +17.6k (13.9k) [+3.8k,+31.8k] |
| G|ADDUW|B2_L6Mrank#4 | 1.03 [0.94,1.13] | +5.6k (48.9k) | +13.5k (18.5k) | +11.0k (16.8k) | -2.1k (13.2k) | -0.3k (13.2k) | +2.1k (10.7k) [-8.2k,+11.3k] |
| G|ADDUW|B2_PRE#5 | 0.94 [0.84,1.05] | +3.9k (26.6k) | +10.9k (16.7k) | +9.0k (15.0k) | +9.0k (15.0k) | +5.4k (9.4k) | +8.9k (11.5k) [-2.2k,+20.3k] |
| H|L2SP|ALL_L6M_rank1|N | 0.97 [0.78,1.28] | +50.8k (130.4k) | +11.1k (47.4k) | +6.9k (43.6k) | -38.8k (25.4k) | -10.4k (30.7k) | -25.3k (22.9k) [-58.2k,-3.6k] |
| C|F|A06+HM5R+B02 | 0.72 [0.53,0.90] | +21.8k (84.1k) | +8.3k (29.4k) | +4.6k (27.8k) | +25.2k (20.6k) | -3.7k (20.1k) | +19.1k (16.9k) [+2.3k,+38.2k] |
| C|F|A06+B02 | 0.81 [0.73,0.90] | +11.5k (27.1k) | +8.4k (17.6k) | +6.5k (17.0k) | +19.6k (12.8k) | -2.7k (12.4k) | +15.4k (10.5k) [+5.3k,+25.5k] |
| C|F|A06+HM5R | 0.77 [0.57,0.97] | +21.5k (90.8k) | +7.3k (29.1k) | +3.4k (27.6k) | +22.8k (21.1k) | -6.7k (21.2k) | +17.3k (17.2k) [-2.0k,+37.9k] |
| C|F|C1 | 0.82 [0.74,0.93] | +11.8k (16.0k) | +6.9k (14.3k) | +8.7k (14.1k) | +1.8k (9.6k) | -2.8k (11.5k) | +3.5k (8.0k) [-5.8k,+10.8k] |
| B|L2SL|ALL_RANK | 1.05 [0.95,1.17] | -2.4k (18.9k) | +8.8k (16.7k) | +7.2k (15.2k) | -7.3k (12.9k) | -5.0k (15.3k) | -3.0k (10.4k) [-15.5k,+6.6k] |
| E|SL|PB|NY|P1+N3 | 0.94 [0.90,0.97] | +8.4k (4.9k) | +7.6k (7.3k) | +6.8k (6.8k) | +1.3k (4.4k) | +0.1k (6.4k) | +2.9k (3.8k) [-0.9k,+7.2k] |
| C|D|D_L30s | 0.85 [0.73,0.98] | +31.3k (53.5k) | +6.9k (27.9k) | +4.3k (25.4k) | -7.2k (15.4k) | -11.1k (16.6k) | -3.2k (13.3k) [-17.2k,+9.9k] |
| C|F|HM5R+B02 | 0.81 [0.66,0.93] | +14.7k (62.4k) | +6.5k (24.6k) | +4.5k (23.0k) | +11.3k (16.6k) | +3.9k (16.5k) | +9.1k (13.6k) [-4.0k,+24.2k] |
| E|SL|PB|NY|P1 | 0.94 [0.90,0.98] | +8.3k (5.0k) | +7.3k (7.3k) | +6.3k (6.7k) | +1.3k (4.4k) | -0.3k (6.2k) | +2.8k (3.8k) [-0.8k,+6.8k] |
| C|A|A08 | 0.96 [0.90,1.01] | +23.3k (40.1k) | +7.4k (12.9k) | +5.8k (12.0k) | -2.2k (8.6k) | +0.8k (8.0k) | +0.0k (7.1k) [-6.0k,+6.3k] |
| F|CW|SM | 1.00 [0.96,1.06] | +3.2k (32.2k) | +7.5k (12.3k) | +5.6k (11.6k) | -1.9k (9.8k) | +2.1k (9.5k) | +0.4k (7.8k) [-6.4k,+6.0k] |
| E|SL|PB|NY|P1+L2 | 0.94 [0.90,0.97] | +8.4k (4.9k) | +6.7k (7.5k) | +6.0k (6.8k) | +1.5k (4.4k) | -0.2k (5.7k) | +2.9k (3.8k) [-1.0k,+7.1k] |
| C|A|A06 | 0.86 [0.77,0.94] | +10.0k (26.5k) | +5.7k (15.2k) | +3.0k (14.2k) | +16.4k (11.1k) | -6.5k (10.7k) | +12.5k (9.0k) [+4.1k,+22.0k] |
| E|SL|PB|NY|G1k70 | 0.95 [0.91,0.98] | +8.7k (5.3k) | +6.1k (7.1k) | +5.2k (6.4k) | +1.4k (4.2k) | +1.0k (5.5k) | +2.6k (3.5k) [-1.0k,+6.7k] |
| C|A|A03 | 0.98 [0.95,1.00] | +4.9k (13.6k) | +6.1k (6.1k) | +5.3k (5.6k) | +3.0k (3.3k) | -0.4k (2.7k) | +3.6k (2.9k) [+1.3k,+6.9k] |
| H|L2SP|ALL_PRE_selected|M | 0.87 [0.80,0.94] | +15.7k (49.3k) | +5.3k (20.1k) | +4.4k (17.9k) | +3.4k (11.7k) | +1.7k (13.9k) | +3.8k (9.8k) [-3.8k,+11.2k] |
| E|SL|PB|NY|P1+L1 | 0.94 [0.90,0.98] | +4.2k (8.2k) | +5.7k (8.2k) | +5.0k (7.6k) | -0.7k (4.8k) | -1.2k (8.2k) | +1.0k (4.2k) [-3.4k,+5.0k] |
| E|SL|PB|NY|P1+L1.5 | 0.94 [0.90,0.99] | +5.1k (9.9k) | +5.6k (7.3k) | +4.6k (6.8k) | +0.9k (4.6k) | -1.3k (6.4k) | +2.0k (3.9k) [-2.3k,+6.2k] |
| C|F|HM5R | 0.87 [0.70,0.99] | +13.8k (70.5k) | +4.8k (24.2k) | +2.8k (22.5k) | +8.5k (17.7k) | +0.7k (17.1k) | +6.8k (14.2k) [-7.2k,+23.3k] |
| C|F|HM5M | 0.90 [0.82,0.97] | +8.8k (34.2k) | +5.0k (11.8k) | +3.3k (11.4k) | +5.8k (8.7k) | +1.0k (8.7k) | +5.0k (7.0k) [-2.3k,+13.2k] |
| C|D|D_B4s | 0.89 [0.82,0.98] | +17.2k (36.1k) | +4.9k (18.3k) | +3.2k (16.6k) | +0.2k (12.2k) | -7.6k (11.4k) | +1.4k (9.9k) [-8.2k,+10.1k] |
| C|D|D_L40s | 0.94 [0.88,0.98] | +12.0k (19.9k) | +4.9k (7.4k) | +3.4k (7.2k) | +4.8k (5.8k) | -3.2k (7.0k) | +4.4k (4.6k) [+0.3k,+10.3k] |
| C|D|D_B2s | 0.65 [0.50,0.85] | +43.5k (126.9k) | +4.2k (42.0k) | +3.2k (38.9k) | -9.7k (24.5k) | -10.8k (24.9k) | -4.7k (20.6k) [-28.5k,+12.9k] |
| E|SL|PB|NY|P1.5+N2 | 0.96 [0.93,0.99] | +6.5k (7.9k) | +4.7k (5.3k) | +4.3k (5.2k) | +0.2k (4.0k) | -1.5k (5.4k) | +1.4k (3.2k) [-1.7k,+5.1k] |
| E|SL|PB|London|P1.5+N1 | 0.93 [0.88,0.99] | +8.7k (30.3k) | +4.5k (9.3k) | +4.0k (8.5k) | +6.1k (6.7k) | +4.1k (7.8k) | +5.5k (5.4k) [-0.5k,+10.9k] |
| E|SL|PB|NY|G1k50 | 0.96 [0.93,0.99] | +8.1k (6.6k) | +4.6k (6.8k) | +3.9k (6.1k) | +2.5k (3.8k) | +1.3k (4.5k) | +2.9k (3.2k) [-0.2k,+6.3k] |
| E|SL|PB|NY|P1+N1 | 0.96 [0.92,0.99] | +1.8k (8.4k) | +4.1k (7.0k) | +3.4k (6.6k) | -0.7k (4.6k) | -2.9k (8.8k) | +0.5k (3.9k) [-3.4k,+4.3k] |
| E|SL|PB|London|P3+N1 | 0.94 [0.89,1.00] | +3.6k (26.2k) | +3.8k (7.6k) | +3.6k (6.9k) | +5.5k (5.7k) | +1.9k (5.8k) | +5.0k (4.6k) [-0.7k,+10.1k] |
| C|F|B02 | 0.94 [0.90,0.99] | +2.0k (9.7k) | +3.5k (7.9k) | +4.1k (8.4k) | +3.7k (5.9k) | +4.1k (7.5k) | +3.4k (4.7k) [-1.0k,+8.0k] |
| E|SL|PB|London|P2+N1 | 0.94 [0.88,1.00] | +6.1k (30.1k) | +3.4k (8.7k) | +3.3k (7.9k) | +6.2k (5.7k) | +2.7k (6.1k) | +5.4k (4.7k) [+0.1k,+10.8k] |
| E|SL|PS|London|P1+N3 | 0.97 [0.94,1.00] | +14.0k (17.2k) | +3.4k (6.7k) | +3.1k (6.0k) | -0.6k (4.1k) | +0.1k (4.8k) | +0.5k (3.4k) [-2.6k,+3.7k] |
| E|SL|WT|NY|P2+N1 | 0.99 [0.95,1.02] | +5.7k (7.6k) | +3.2k (5.7k) | +3.0k (5.2k) | +0.8k (4.3k) | +1.9k (4.8k) | +1.5k (3.4k) [-2.5k,+5.1k] |
| E|SL|PS|London|P1+N2 | 0.97 [0.94,1.00] | +8.7k (24.0k) | +2.9k (6.9k) | +2.7k (6.2k) | +0.5k (4.3k) | -0.0k (4.7k) | +1.2k (3.6k) [-2.2k,+4.5k] |
| E|SL|PB|NY|P1.5 | 0.97 [0.94,1.00] | +3.6k (9.9k) | +2.9k (4.1k) | +2.4k (3.9k) | -0.9k (3.7k) | -1.2k (4.9k) | +0.1k (2.9k) [-2.7k,+3.0k] |
| E|SL|PS|NY|P1.5+L1 | 0.98 [0.96,1.00] | +6.7k (11.5k) | +2.7k (4.7k) | +2.2k (4.5k) | +0.1k (2.7k) | -0.3k (3.9k) | +0.7k (2.4k) [-1.3k,+2.9k] |
| E|SL|WT|NY|P2 | 0.98 [0.97,1.00] | +4.5k (5.8k) | +2.6k (3.1k) | +2.4k (2.8k) | +1.1k (1.9k) | +0.4k (2.5k) | +1.5k (1.6k) [+0.0k,+3.1k] |
| B|L2SL|SM_RANK | 1.01 [0.95,1.10] | +5.1k (16.8k) | +2.6k (8.2k) | +2.6k (7.5k) | -5.8k (6.0k) | -1.4k (5.0k) | -3.3k (4.9k) [-10.2k,+2.5k] |
| E|SL|PB|NY|P1.5+L2 | 0.97 [0.94,1.00] | +4.6k (8.9k) | +2.4k (4.7k) | +2.1k (4.4k) | -0.8k (3.8k) | -1.0k (4.6k) | +0.1k (3.0k) [-2.9k,+3.4k] |
| E|SL|HM|NY|P1.5+L1.5 | 0.97 [0.94,1.01] | +6.7k (21.8k) | +2.3k (9.7k) | +2.5k (9.0k) | +0.2k (5.0k) | +0.7k (7.1k) | +0.9k (4.5k) [-3.3k,+5.0k] |
| F|CW|WT | 0.98 [0.92,1.06] | -13.1k (29.9k) | +2.3k (11.3k) | -0.7k (12.7k) | -0.1k (8.9k) | -4.6k (9.7k) | -0.3k (7.3k) [-7.7k,+5.6k] |
| E|SL|PS|NY|P2+N1 | 0.98 [0.97,1.01] | +6.2k (12.8k) | +2.3k (4.9k) | +1.7k (4.5k) | -0.2k (3.2k) | +0.4k (4.5k) | +0.4k (2.6k) [-2.3k,+2.5k] |
| E|SL|PS|NY|P2+L1 | 0.98 [0.96,1.00] | +4.7k (13.2k) | +2.1k (4.3k) | +1.6k (4.0k) | +0.4k (2.6k) | +0.1k (3.6k) | +0.8k (2.2k) [-1.1k,+2.8k] |
| C|A|A09 | 0.98 [0.92,1.01] | -1.7k (30.5k) | +2.0k (9.6k) | +0.9k (8.6k) | -2.1k (6.4k) | -0.6k (4.6k) | -1.2k (5.2k) [-5.8k,+3.9k] |
| E|SL|PB|NY|P2 | 0.98 [0.96,1.00] | +2.8k (7.2k) | +1.9k (3.1k) | +1.4k (2.8k) | -0.4k (3.0k) | -1.0k (3.7k) | +0.1k (2.3k) [-2.1k,+2.5k] |
| B|L2SL|COMBO_RANK | 0.95 [0.84,1.12] | +3.7k (30.1k) | +1.5k (19.9k) | +2.6k (17.7k) | -20.6k (18.1k) | -8.8k (13.4k) | -13.8k (14.1k) [-30.4k,-1.6k] |
| E|SL|PB|NY|G2k70 | 0.99 [0.97,1.00] | +2.7k (5.0k) | +1.6k (2.4k) | +1.1k (2.3k) | -0.3k (2.4k) | +0.4k (2.4k) | +0.1k (1.8k) [-1.6k,+2.1k] |
| E|SL|PB|NY|P2+L2 | 0.98 [0.96,1.00] | +3.8k (6.5k) | +1.5k (3.9k) | +1.2k (3.6k) | -0.3k (3.1k) | -0.7k (3.4k) | +0.2k (2.4k) [-2.0k,+2.6k] |
| A|H|L|M | 0.92 [0.79,1.05] | +51.3k (62.2k) | +1.3k (30.3k) | -3.7k (28.1k) | +10.7k (13.7k) | +2.6k (14.5k) | +6.5k (12.9k) [-4.5k,+18.5k] |
| C|D|D_L30t | 0.90 [0.78,1.02] | +8.6k (33.9k) | +1.2k (21.4k) | +0.5k (19.4k) | -3.5k (12.7k) | -9.9k (13.9k) | -1.9k (10.6k) [-13.7k,+9.4k] |
| E|SL|PS|NY|P3+N1 | 0.98 [0.96,1.01] | +2.0k (12.8k) | +1.2k (4.0k) | +0.8k (3.7k) | +0.5k (3.2k) | +0.4k (4.4k) | +0.6k (2.5k) [-1.8k,+2.6k] |
| E|SL|KB|Asia|P3+L2 | 1.00 [0.99,1.00] | +4.0k (10.8k) | +1.0k (3.2k) | +0.8k (2.8k) | +1.2k (2.8k) | -0.1k (0.3k) | +1.1k (2.1k) [-0.4k,+2.7k] |
| E|SL|PS|NY|G2k70 | 1.00 [0.99,1.00] | +3.1k (10.7k) | +0.9k (3.0k) | +0.8k (2.6k) | +0.1k (0.9k) | +0.6k (1.2k) | +0.3k (1.0k) [-0.4k,+1.2k] |
| E|SL|KB|Asia|P3 | 1.00 [1.00,1.00] | +3.9k (10.9k) | +0.8k (2.3k) | +0.7k (2.0k) | +0.6k (2.1k) | +0.0k (0.0k) | +0.6k (1.6k) [-0.3k,+1.9k] |
| E|SL|WT|Asia|P1+L1 | 0.97 [0.94,1.03] | -7.1k (21.6k) | +0.5k (8.9k) | +0.7k (8.4k) | +2.1k (6.7k) | +1.1k (4.3k) | +1.7k (5.3k) [-3.9k,+6.5k] |
| B|L2SL|HM_PRE | 0.96 [0.88,1.05] | +1.0k (28.4k) | +0.4k (12.7k) | -1.1k (12.7k) | +5.2k (9.4k) | -2.4k (8.2k) | +3.3k (7.7k) [-5.3k,+11.3k] |
| E|SL|HM|NY|P1+L1.5 | 0.97 [0.93,1.01] | +4.0k (20.9k) | +0.4k (12.6k) | +1.6k (11.4k) | +0.7k (6.2k) | -0.5k (9.6k) | +1.0k (5.5k) [-4.0k,+6.4k] |
| E|SL|PB|London|P3+L1.5 | 0.97 [0.93,1.02] | +2.2k (17.6k) | +0.4k (5.0k) | +0.3k (4.5k) | +2.3k (3.5k) | +1.5k (2.5k) | +1.7k (2.8k) [-2.1k,+5.5k] |
| E|SL|PS|NY|P3+L2 | 1.00 [0.99,1.00] | +0.0k (3.2k) | +0.3k (1.3k) | +0.2k (1.1k) | -0.0k (1.1k) | -0.1k (1.6k) | +0.1k (0.8k) [-0.8k,+1.0k] |
| C|D|D_B3s | 0.84 [0.69,1.02] | +19.1k (64.9k) | +0.1k (28.8k) | -1.1k (26.1k) | -6.9k (19.9k) | -9.7k (20.3k) | -4.7k (16.0k) [-23.2k,+10.5k] |
| C|A|A01 | 1.01 [0.95,1.08] | -3.0k (19.7k) | +0.1k (8.6k) | +0.9k (7.7k) | -0.3k (6.0k) | -0.9k (4.7k) | +0.0k (4.8k) [-6.1k,+5.2k] |
| E|SL|PS|NY|P3+L1.5 | 0.99 [0.98,1.01] | -0.7k (4.5k) | -0.1k (2.1k) | -0.3k (2.0k) | +0.5k (1.6k) | -0.9k (2.6k) | +0.3k (1.3k) [-1.4k,+1.6k] |
| E|SL|PS|NY|L2 | 1.00 [0.99,1.01] | -0.2k (2.5k) | -0.1k (1.3k) | -0.1k (1.1k) | -0.3k (0.9k) | -0.1k (1.5k) | -0.3k (0.7k) [-0.9k,+0.4k] |
| A|B|P|N | 0.92 [0.78,1.08] | +12.6k (104.2k) | -0.2k (35.8k) | +1.5k (31.5k) | -19.0k (19.9k) | +1.4k (19.7k) | -13.0k (17.1k) [-31.6k,+3.8k] |
| B|EXP2|B_U3 | 0.98 [0.94,1.03] | -8.8k (19.7k) | -0.3k (8.8k) | -0.5k (7.9k) | +5.4k (7.5k) | -1.0k (6.2k) | +3.7k (5.9k) [-1.0k,+8.9k] |
| C|A|A07 | 0.99 [0.91,1.07] | -8.9k (43.6k) | -0.3k (18.7k) | -1.7k (16.6k) | -3.4k (8.7k) | -1.2k (7.9k) | -2.8k (7.9k) [-11.0k,+5.3k] |
| C|D|D_B3e | 0.88 [0.73,1.05] | +7.3k (59.4k) | -0.4k (27.0k) | -1.7k (24.7k) | -10.1k (18.8k) | -14.4k (18.9k) | -6.9k (15.1k) [-24.4k,+8.5k] |
| E|SL|ST|Asia|P1.5+N3 | 0.99 [0.95,1.02] | +18.1k (56.8k) | -0.6k (14.4k) | -0.5k (12.6k) | +3.3k (5.6k) | +0.7k (1.4k) | +2.2k (5.5k) [-2.5k,+7.0k] |
| B|EXP2|P | 1.02 [0.87,1.22] | +23.5k (63.5k) | -0.7k (18.8k) | -5.7k (28.4k) | -6.6k (15.6k) | -18.1k (21.1k) | -6.4k (13.9k) [-25.0k,+7.0k] |
| B|L2SL|SM_PRE | 1.02 [0.98,1.07] | -2.0k (13.1k) | -1.2k (5.0k) | -1.3k (4.6k) | -2.4k (3.9k) | +1.0k (2.3k) | -2.1k (3.1k) [-6.9k,+1.2k] |
| E|SL|PS|London|N2 | 1.00 [0.98,1.02] | -7.5k (13.2k) | -1.2k (3.3k) | -0.9k (2.9k) | +0.8k (2.1k) | -0.2k (0.9k) | +0.3k (1.7k) [-1.6k,+1.9k] |
| A|H|EP|N | 0.90 [0.74,1.07] | +34.6k (139.4k) | -1.3k (46.3k) | -1.4k (40.4k) | -23.3k (23.0k) | -4.8k (25.3k) | -16.9k (20.5k) [-38.9k,+3.0k] |
| E|SL|ST|NY|N2 | 0.98 [0.96,1.01] | +3.0k (13.9k) | -1.7k (8.5k) | -1.4k (7.4k) | +1.4k (3.2k) | -2.9k (4.3k) | +0.6k (3.2k) [-2.6k,+3.6k] |
| E|SL|ST|NY|P3+N2 | 0.98 [0.95,1.01] | -0.4k (20.4k) | -2.6k (9.3k) | -2.5k (8.1k) | +1.4k (3.5k) | -2.5k (4.1k) | +0.3k (3.5k) [-3.2k,+3.8k] |
| B|EXP2|B_U3_P | 1.02 [0.87,1.23] | +14.0k (73.3k) | -2.7k (20.7k) | -8.0k (29.7k) | -3.4k (17.3k) | -20.0k (21.9k) | -4.8k (15.1k) [-24.9k,+10.1k] |
| E|SL|ST|Asia|P1.5+L2 | 0.99 [0.96,1.02] | +4.5k (34.0k) | -2.8k (10.2k) | -2.5k (9.0k) | +2.8k (5.7k) | +0.7k (1.4k) | +1.2k (4.9k) [-3.4k,+5.5k] |
| B|L2SL|KB_RANK | 1.02 [1.00,1.06] | -4.8k (9.7k) | -3.0k (3.9k) | -2.7k (3.6k) | -5.8k (4.2k) | +0.6k (4.2k) | -4.9k (3.2k) [-9.2k,-2.3k] |
| B|L2SL|ST_RANK | 1.00 [0.93,1.09] | +5.0k (46.7k) | -3.1k (17.6k) | -1.5k (15.6k) | -4.9k (10.8k) | -5.9k (7.9k) | -3.9k (8.9k) [-13.7k,+4.1k] |
| B|L2SL|KB_PRE | 1.03 [0.99,1.08] | +2.8k (6.8k) | -3.3k (5.7k) | -2.7k (5.1k) | -5.4k (4.0k) | -2.3k (3.4k) | -4.6k (3.2k) [-9.3k,-1.2k] |
| A|H|P|N | 0.91 [0.75,1.08] | +26.8k (142.6k) | -3.2k (45.1k) | -1.6k (39.6k) | -26.2k (22.9k) | -4.6k (25.2k) | -19.0k (20.3k) [-40.5k,+0.5k] |
| F|CW|HM | 0.97 [0.88,1.05] | +12.2k (44.8k) | -3.4k (23.9k) | -5.1k (22.4k) | +4.4k (12.5k) | +4.4k (14.2k) | +1.5k (11.1k) [-7.8k,+10.8k] |
| B|L2SL|WT_RANK | 1.00 [0.95,1.05] | -11.8k (12.9k) | -3.7k (7.0k) | -3.2k (6.1k) | -2.9k (4.9k) | -0.5k (5.4k) | -3.0k (3.9k) [-7.7k,+0.9k] |
| C|D|D_B3h | 0.86 [0.76,0.99] | +3.1k (40.2k) | -3.5k (22.8k) | -5.7k (21.3k) | -0.8k (16.4k) | -8.5k (16.2k) | -1.5k (13.1k) [-15.2k,+10.1k] |
| B|L2SL|WT_PRE | 1.02 [0.99,1.06] | -12.7k (24.6k) | -4.6k (6.1k) | -4.5k (5.3k) | -4.6k (3.3k) | +1.6k (2.9k) | -4.6k (2.8k) [-8.7k,-2.0k] |
| B|L2SL|PE_PRE | 0.99 [0.95,1.03] | -4.5k (12.0k) | -4.6k (8.1k) | -3.6k (7.6k) | +2.3k (5.4k) | -1.2k (5.7k) | +0.5k (4.5k) [-4.0k,+4.7k] |
| B|L2SL|PE_RANK | 1.01 [0.96,1.08] | -1.0k (14.8k) | -4.8k (7.5k) | -3.6k (6.9k) | -3.6k (6.2k) | -1.8k (6.2k) | -3.6k (4.8k) [-10.3k,+1.0k] |
| B|L2SL|ST_PRE | 0.98 [0.91,1.05] | +23.9k (43.3k) | -5.4k (19.7k) | -4.4k (17.3k) | -0.3k (5.8k) | -5.1k (8.1k) | -1.6k (6.6k) [-9.0k,+5.0k] |
| H|L2SP|ALL_PRE_selected|N | 0.92 [0.83,1.04] | +5.9k (52.8k) | -5.1k (20.6k) | -5.4k (18.3k) | -4.6k (11.7k) | -2.7k (14.9k) | -4.9k (9.9k) [-18.3k,+4.3k] |
| A|H|EPL|N | 0.84 [0.69,1.00] | +41.1k (185.2k) | -5.0k (53.9k) | -9.6k (47.3k) | -10.5k (21.3k) | +2.8k (24.1k) | -10.4k (20.7k) [-31.7k,+9.1k] |
| E|SL|ST|Asia|P1.5+N2 | 0.98 [0.96,1.02] | +3.4k (29.8k) | -6.6k (12.9k) | -5.9k (11.3k) | +4.5k (6.1k) | +0.7k (1.5k) | +1.4k (5.6k) [-3.6k,+5.7k] |
| C|A|A02 | 0.88 [0.76,1.04] | -5.5k (56.1k) | -6.2k (33.6k) | -4.5k (31.7k) | +7.2k (19.1k) | -15.5k (19.0k) | +3.8k (16.5k) [-13.1k,+18.3k] |
| F|CW|ST | 0.91 [0.82,1.01] | +11.5k (42.0k) | -6.5k (22.2k) | -6.0k (20.8k) | +2.7k (14.4k) | -3.6k (15.5k) | +0.1k (12.0k) [-10.3k,+10.2k] |
| A|H|PL|N | 0.85 [0.69,1.01] | +42.4k (191.5k) | -6.4k (56.3k) | -9.3k (49.2k) | -14.9k (21.6k) | +1.8k (24.9k) | -13.4k (21.2k) [-33.8k,+7.6k] |
| B|EXP2|B_FROZEN_P | 0.84 [0.63,1.13] | -7.0k (75.8k) | -7.9k (63.9k) | -2.6k (61.9k) | -6.6k (32.4k) | -1.4k (34.6k) | -5.4k (29.4k) [-40.0k,+19.7k] |
| F|CW|PE | 0.91 [0.84,0.99] | -1.2k (31.4k) | -10.3k (21.1k) | -8.0k (19.1k) | +3.4k (13.0k) | +3.3k (14.0k) | -0.0k (10.9k) [-8.9k,+8.2k] |
| D|D6L_alone | 0.85 [0.66,1.10] | +61.3k (105.3k) | -10.2k (52.7k) | -7.2k (49.1k) | -25.8k (29.3k) | -15.2k (31.4k) | -20.4k (25.5k) [-45.4k,-2.0k] |
| B|L2SL|ALL_PRE | 0.94 [0.79,1.11] | +22.2k (23.3k) | -14.8k (30.2k) | -14.3k (26.4k) | -6.7k (13.2k) | -12.8k (14.7k) | -9.1k (12.2k) [-24.7k,+4.4k] |
| D|PROFIT_alone | 1.02 [0.86,1.19] | +28.5k (112.7k) | -16.7k (39.1k) | -16.7k (38.6k) | -10.1k (22.7k) | -1.1k (24.3k) | -12.1k (19.8k) [-28.9k,+3.0k] |
| B|L2SL|COMBO_PRE | 0.97 [0.85,1.11] | +9.4k (29.1k) | -17.3k (22.9k) | -16.5k (20.8k) | -4.4k (13.3k) | -8.0k (13.9k) | -8.1k (11.4k) [-21.8k,+3.3k] |
| B|EXP2|B_FROZEN | 0.99 [0.75,1.34] | -13.0k (111.9k) | -19.5k (70.9k) | -14.4k (68.4k) | -25.1k (38.4k) | -1.5k (42.3k) | -22.1k (34.0k) [-61.4k,+6.9k] |
| B|EXP2|B_U3_L | 0.95 [0.80,1.18] | -19.0k (71.5k) | -22.4k (35.4k) | -18.7k (33.3k) | -3.4k (25.8k) | -16.3k (22.0k) | -8.0k (20.9k) [-32.0k,+10.0k] |
| B|EXP2|L | 0.95 [0.80,1.20] | -16.7k (67.7k) | -22.8k (32.7k) | -18.4k (30.8k) | -7.9k (25.3k) | -13.8k (20.3k) | -11.1k (20.2k) [-36.0k,+6.1k] |
| B|EXP2|B_U1_P | 0.99 [0.81,1.31] | -6.6k (182.2k) | -25.8k (61.5k) | -22.1k (56.8k) | -28.3k (34.8k) | -14.6k (35.8k) | -26.7k (29.8k) [-61.8k,-2.5k] |
| F|CW|KB | 1.03 [0.90,1.20] | +0.5k (70.7k) | -27.8k (32.9k) | -26.9k (28.4k) | -5.9k (17.2k) | +4.0k (17.2k) | -12.3k (15.1k) [-28.4k,+0.0k] |
| B|EXP2|B_U1 | 1.08 [0.92,1.39] | -42.3k (160.7k) | -31.5k (64.3k) | -29.8k (59.0k) | -38.3k (35.4k) | -9.0k (40.6k) | -36.1k (30.5k) [-71.7k,-12.4k] |
| B|EXP2|B_U3_P_L | 0.98 [0.81,1.26] | -9.8k (52.8k) | -28.7k (31.2k) | -30.1k (37.0k) | -9.6k (26.6k) | -28.5k (27.3k) | -15.9k (22.0k) [-43.6k,+2.9k] |
| B|EXP2|P_L | 0.97 [0.80,1.25] | -7.0k (46.3k) | -28.5k (28.6k) | -29.4k (34.9k) | -12.1k (26.4k) | -26.1k (27.9k) | -17.4k (21.4k) [-46.4k,+1.4k] |
| D|JOINT3 | 0.76 [0.61,1.01] | +36.1k (91.0k) | -23.6k (48.2k) | -19.7k (48.3k) | -34.4k (31.0k) | -9.5k (32.4k) | -30.3k (26.4k) [-55.3k,-11.2k] |
| D|JOINT10 | 0.76 [0.60,1.00] | +36.0k (90.7k) | -23.7k (48.2k) | -19.9k (48.2k) | -34.3k (30.9k) | -9.2k (32.3k) | -30.3k (26.3k) [-54.2k,-11.5k] |
| D|JOINT20 | 0.75 [0.60,0.95] | +34.9k (89.3k) | -24.0k (48.1k) | -20.7k (47.9k) | -31.6k (29.7k) | -7.5k (31.9k) | -28.6k (25.5k) [-52.0k,-10.4k] |
| D|LOSS20_alone | 0.95 [0.82,1.13] | -4.2k (83.4k) | -31.2k (39.2k) | -26.8k (35.2k) | -33.7k (27.6k) | +1.3k (31.6k) | -31.9k (22.2k) [-50.8k,-16.1k] |
| D|LOSS10_alone | 0.96 [0.83,1.12] | -3.2k (83.8k) | -31.5k (39.8k) | -27.3k (36.1k) | -33.0k (27.7k) | +1.1k (31.9k) | -31.6k (22.4k) [-50.6k,-14.7k] |
| B|EXP2|B_U2_P | 1.04 [0.80,1.46] | -46.4k (162.8k) | -34.8k (56.8k) | -29.2k (57.5k) | -32.2k (38.4k) | -19.6k (37.4k) | -31.6k (32.1k) [-73.2k,-2.4k] |
| D|LOSS3_alone | 0.96 [0.83,1.13] | -3.1k (83.7k) | -32.5k (40.4k) | -28.0k (36.8k) | -33.9k (27.6k) | +0.9k (32.1k) | -32.4k (22.4k) [-51.8k,-16.1k] |
| B|EXP2|B_U2 | 1.07 [0.84,1.45] | -48.3k (167.4k) | -36.4k (60.5k) | -31.6k (58.5k) | -31.4k (38.3k) | -16.3k (38.3k) | -31.8k (32.2k) [-71.4k,-5.3k] |
| F|CW|ALL6 | 0.84 [0.65,1.14] | +13.3k (169.9k) | -39.4k (56.9k) | -41.9k (51.9k) | +1.2k (32.6k) | +5.3k (39.4k) | -11.8k (28.2k) [-40.9k,+9.3k] |
| C|A|A10 | 1.15 [0.90,1.51] | -29.3k (69.7k) | -59.4k (55.7k) | -46.8k (64.1k) | -58.8k (37.3k) | -11.1k (44.6k) | -53.6k (32.3k) [-93.7k,-25.7k] |
| B|EXP2|B_U2_L | 1.18 [0.95,1.57] | -101.5k (137.4k) | -64.8k (51.4k) | -56.6k (52.8k) | -53.4k (40.1k) | -38.5k (45.5k) | -54.9k (32.4k) [-96.1k,-28.5k] |
| B|EXP2|B_U2_P_L | 1.19 [0.92,1.60] | -108.1k (131.1k) | -66.1k (51.2k) | -59.2k (54.8k) | -51.5k (42.1k) | -38.9k (46.3k) | -54.3k (33.9k) [-98.4k,-25.8k] |
| B|EXP2|B_U1_L | 1.11 [0.89,1.51] | -78.5k (122.5k) | -64.3k (56.0k) | -56.3k (53.4k) | -55.7k (38.6k) | -36.4k (43.1k) | -56.4k (31.5k) [-97.4k,-30.5k] |
| B|EXP2|B_FROZEN_P_L | 1.12 [0.85,1.54] | -62.5k (79.4k) | -69.0k (63.6k) | -59.6k (64.3k) | -56.1k (41.0k) | -35.5k (46.9k) | -57.7k (34.7k) [-99.6k,-28.6k] |
| B|EXP2|B_FROZEN_L | 1.19 [0.90,1.65] | -68.5k (97.7k) | -74.9k (66.7k) | -63.7k (67.6k) | -68.8k (43.6k) | -43.0k (50.5k) | -67.9k (36.8k) [-114.9k,-34.5k] |
| B|EXP2|B_U1_P_L | 1.10 [0.88,1.50] | -71.1k (112.2k) | -69.7k (53.6k) | -60.6k (53.5k) | -55.8k (38.3k) | -34.4k (44.2k) | -57.8k (31.4k) [-100.4k,-32.0k] |

## 5. Naive scaling versus the engine rerun, and the fixed-dollar-lock engine
Naive = multiply the weekly series by c (no sweep, no lock effect), c solved on worst-20. Engine rerun = lock engine at lots x c (locks are in R = lots x stop x $20, so they scale with the lots) plus the size-dependent sweep cost of the equal_risk.excess surface charged per filled row. Verified on frame A by actually rerunning de_engine.run_rows at lots x c*: the rerun reproduces the stack worst-20 (WF -3668.9k vs -3668.9k on M basis) and the analytic L6M/HOLD deltas to the cent (er_verify.py, out/equal_risk/verify.pkl); scaled-lock engine = c x series to 3e-11, so the ONLY nonlinearity with locks scaled is the sweep, which is zero up to 14 lots per order and about 0.21 tick per lot beyond. Fixed-$ locks (size x c, R unscaled; frame A) is the pessimistic case: the day entry test, give-back arm and week floor then bind earlier at larger size.
| series | c* naive | c* engine | L6M naive | L6M engine | HOLD naive | HOLD engine | c* fixed-$ locks | L6M fixed-$ | HOLD fixed-$ | PRE fixed-$ |
|--|--|--|--|--|--|--|--|--|--|--|
| A|B|E|N | 1.43 | 1.43 | +90.6k | +90.3k | +80.8k | +80.5k | 1.65 | +25.8k | +22.1k | -28.4k |
| A|B|EPL|M | 1.39 | 1.39 | +81.6k | +81.6k | +76.4k | +76.4k | n/a | n/a | n/a | n/a |
| A|B|EL|N | 1.38 | 1.38 | +79.8k | +79.7k | +71.2k | +71.2k | n/a | n/a | n/a | n/a |
| A|B|EP|M | 1.44 | 1.44 | +79.7k | +79.3k | +74.8k | +74.5k | n/a | n/a | n/a | n/a |
| A|B|E|M | 1.37 | 1.37 | +79.3k | +79.3k | +69.0k | +69.0k | 1.59 | +34.1k | +27.5k | -15.3k |
| A|B|EL|M | 1.35 | 1.35 | +76.4k | +76.3k | +67.5k | +67.5k | 1.75 | +54.6k | +47.7k | -25.6k |
| H|L2SP|ALL_L6M_rank1|M (profile sweep) | 1.20 | 1.20 | +56.4k | +56.4k | +48.7k | +48.7k | not rerun | | | |
| A|B|PL|M | 1.15 | 1.15 | +53.0k | +53.0k | +49.6k | +49.6k | 1.47 | +42.1k | +39.1k | -12.2k |
| A|H|EP|M | 1.22 | 1.22 | +43.9k | +43.9k | +39.9k | +39.9k | 1.41 | +23.4k | +22.0k | +1.3k |
| A|B|EP|N | 1.35 | 1.35 | +42.6k | +42.6k | +40.9k | +40.9k | 1.60 | +18.3k | +17.9k | -38.9k |
| A|B|EPL|N | 1.31 | 1.31 | +41.2k | +41.2k | +39.4k | +39.4k | 1.67 | +41.4k | +37.0k | -49.9k |
| A|H|P|M | 1.20 | 1.20 | +39.4k | +39.4k | +37.9k | +37.9k | 1.36 | +17.3k | +17.8k | +2.7k |
| A|H|PL|M | 1.28 | 1.28 | +38.8k | +38.8k | +31.1k | +31.1k | 1.48 | +18.3k | +10.5k | +17.6k |
| A|H|EPL|M | 1.29 | 1.29 | +38.7k | +38.7k | +28.9k | +28.9k | 1.62 | +21.2k | +12.5k | +23.9k |
| A|B|P|M | 1.17 | 1.17 | +34.3k | +34.3k | +33.1k | +33.1k | 1.26 | +21.4k | +21.5k | +4.4k |
| G|ADDUW|B1_PRE#1022 (profile sweep) | 1.46 | 1.45 | +29.9k | +29.2k | +28.1k | +27.5k | not rerun | | | |
| A|B|L|N | 1.09 | 1.09 | +27.8k | +27.8k | +27.6k | +27.6k | 1.38 | +14.2k | +13.7k | -13.0k |
| A|H|EL|N | 1.18 | 1.18 | +26.3k | +26.3k | +18.5k | +18.5k | 1.51 | +6.5k | +6.6k | +16.5k |
| A|B|L|M | 1.04 | 1.04 | +25.9k | +25.9k | +23.3k | +23.3k | 1.26 | +13.5k | +11.5k | -7.5k |
| A|H|E|N | 1.06 | 1.06 | +22.6k | +22.6k | +22.6k | +22.6k | 1.11 | +13.3k | +13.2k | +2.4k |
| A|B|PL|N | 1.10 | 1.10 | +19.8k | +19.8k | +19.2k | +19.2k | 1.31 | +10.8k | +11.9k | -35.5k |
| C|D|D_L20s (profile sweep) | 1.46 | 1.46 | +17.9k | +17.3k | +13.4k | +12.9k | not rerun | | | |
| A|H|L|N | 1.15 | 1.15 | +15.7k | +15.7k | +11.3k | +11.3k | 1.20 | -4.3k | -6.8k | +14.4k |
| C|A|A05 (profile sweep) | 1.14 | 1.14 | +15.1k | +15.1k | +11.4k | +11.4k | not rerun | | | |
| A|H|EL|M | 1.14 | 1.14 | +15.0k | +15.0k | +7.9k | +7.9k | 1.22 | +11.0k | +6.4k | +19.7k |
| B|L2SL|HM_RANK (profile sweep) | 1.09 | 1.09 | +14.8k | +14.8k | +12.1k | +12.1k | not rerun | | | |
| A|H|E|M | 1.00 | 1.00 | +13.4k | +13.4k | +11.6k | +11.6k | 1.01 | +13.1k | +11.4k | +7.6k |
| C|A|A04 (profile sweep) | 1.29 | 1.29 | +13.3k | +13.3k | +7.5k | +7.5k | not rerun | | | |
| G|ADDUW|B2_L6Mrank#4 (profile sweep) | 0.97 | 0.97 | +13.1k | +13.1k | +10.7k | +10.7k | not rerun | | | |
| G|ADDUW|B2_PRE#5 (profile sweep) | 1.06 | 1.06 | +11.6k | +11.6k | +9.5k | +9.5k | not rerun | | | |
| H|L2SP|ALL_L6M_rank1|N (profile sweep) | 1.03 | 1.03 | +11.5k | +11.5k | +7.2k | +7.2k | not rerun | | | |
| C|F|A06+HM5R+B02 (profile sweep) | 1.38 | 1.38 | +11.4k | +11.4k | +6.4k | +6.4k | not rerun | | | |
| C|F|A06+B02 (profile sweep) | 1.23 | 1.23 | +10.3k | +10.3k | +8.0k | +8.0k | not rerun | | | |
| C|F|A06+HM5R (profile sweep) | 1.30 | 1.30 | +9.4k | +9.4k | +4.4k | +4.4k | not rerun | | | |
| C|F|C1 (profile sweep) | 1.22 | 1.22 | +8.5k | +8.5k | +10.6k | +10.6k | not rerun | | | |
| B|L2SL|ALL_RANK (profile sweep) | 0.95 | 0.95 | +8.4k | +8.4k | +6.9k | +6.9k | not rerun | | | |
| E|SL|PB|NY|P1+N3 (profile sweep) | 1.07 | 1.07 | +8.1k | +8.1k | +7.2k | +7.2k | not rerun | | | |
| C|D|D_L30s (profile sweep) | 1.18 | 1.18 | +8.1k | +8.1k | +5.1k | +5.1k | not rerun | | | |
| C|F|HM5R+B02 (profile sweep) | 1.24 | 1.24 | +8.0k | +8.0k | +5.6k | +5.6k | not rerun | | | |
| E|SL|PB|NY|P1 (profile sweep) | 1.07 | 1.07 | +7.8k | +7.8k | +6.7k | +6.7k | not rerun | | | |
| C|A|A08 (profile sweep) | 1.04 | 1.04 | +7.7k | +7.7k | +6.1k | +6.1k | not rerun | | | |
| F|CW|SM (profile sweep) | 1.00 | 1.00 | +7.5k | +7.5k | +5.6k | +5.6k | not rerun | | | |
| E|SL|PB|NY|P1+L2 (profile sweep) | 1.07 | 1.07 | +7.2k | +7.2k | +6.4k | +6.4k | not rerun | | | |
| C|A|A06 (profile sweep) | 1.16 | 1.16 | +6.6k | +6.6k | +3.4k | +3.4k | not rerun | | | |
| E|SL|PB|NY|G1k70 (profile sweep) | 1.06 | 1.06 | +6.4k | +6.4k | +5.5k | +5.5k | not rerun | | | |
| C|A|A03 (profile sweep) | 1.02 | 1.02 | +6.3k | +6.3k | +5.4k | +5.4k | not rerun | | | |
| H|L2SP|ALL_PRE_selected|M (profile sweep) | 1.15 | 1.15 | +6.1k | +6.1k | +5.1k | +5.1k | not rerun | | | |
| E|SL|PB|NY|P1+L1 (profile sweep) | 1.07 | 1.07 | +6.1k | +6.1k | +5.3k | +5.3k | not rerun | | | |
| E|SL|PB|NY|P1+L1.5 (profile sweep) | 1.06 | 1.06 | +5.9k | +5.9k | +4.9k | +4.9k | not rerun | | | |
| C|F|HM5R (profile sweep) | 1.16 | 1.16 | +5.6k | +5.6k | +3.2k | +3.2k | not rerun | | | |
| C|F|HM5M (profile sweep) | 1.11 | 1.11 | +5.5k | +5.5k | +3.6k | +3.6k | not rerun | | | |
| C|D|D_B4s (profile sweep) | 1.12 | 1.12 | +5.5k | +5.5k | +3.5k | +3.5k | not rerun | | | |
| C|D|D_L40s (profile sweep) | 1.06 | 1.06 | +5.2k | +5.2k | +3.6k | +3.6k | not rerun | | | |
| C|D|D_B2s (profile sweep) | 1.54 | 1.53 | +6.4k | +5.0k | +4.9k | +3.5k | not rerun | | | |
| E|SL|PB|NY|P1.5+N2 (profile sweep) | 1.04 | 1.04 | +4.9k | +4.9k | +4.5k | +4.5k | not rerun | | | |
| E|SL|PB|London|P1.5+N1 (profile sweep) | 1.08 | 1.08 | +4.9k | +4.9k | +4.3k | +4.3k | not rerun | | | |
| E|SL|PB|NY|G1k50 (profile sweep) | 1.04 | 1.04 | +4.8k | +4.8k | +4.1k | +4.1k | not rerun | | | |
| E|SL|PB|NY|P1+N1 (profile sweep) | 1.05 | 1.05 | +4.3k | +4.3k | +3.6k | +3.6k | not rerun | | | |
| E|SL|PB|London|P3+N1 (profile sweep) | 1.07 | 1.07 | +4.1k | +4.1k | +3.9k | +3.9k | not rerun | | | |
| C|F|B02 (profile sweep) | 1.06 | 1.06 | +3.7k | +3.7k | +4.3k | +4.3k | not rerun | | | |
| E|SL|PB|London|P2+N1 (profile sweep) | 1.07 | 1.07 | +3.6k | +3.6k | +3.5k | +3.5k | not rerun | | | |
| E|SL|PS|London|P1+N3 (profile sweep) | 1.03 | 1.03 | +3.5k | +3.5k | +3.2k | +3.2k | not rerun | | | |
| E|SL|WT|NY|P2+N1 (profile sweep) | 1.01 | 1.01 | +3.3k | +3.3k | +3.0k | +3.0k | not rerun | | | |
| E|SL|PS|London|P1+N2 (profile sweep) | 1.04 | 1.04 | +3.0k | +3.0k | +2.8k | +2.8k | not rerun | | | |
| E|SL|PB|NY|P1.5 (profile sweep) | 1.03 | 1.03 | +2.9k | +2.9k | +2.4k | +2.4k | not rerun | | | |
| E|SL|PS|NY|P1.5+L1 (profile sweep) | 1.02 | 1.02 | +2.8k | +2.8k | +2.2k | +2.2k | not rerun | | | |
| E|SL|WT|NY|P2 (profile sweep) | 1.02 | 1.02 | +2.6k | +2.6k | +2.4k | +2.4k | not rerun | | | |
| B|L2SL|SM_RANK (profile sweep) | 0.99 | 0.99 | +2.6k | +2.6k | +2.6k | +2.6k | not rerun | | | |
| E|SL|PB|NY|P1.5+L2 (profile sweep) | 1.03 | 1.03 | +2.5k | +2.5k | +2.2k | +2.2k | not rerun | | | |
| E|SL|HM|NY|P1.5+L1.5 (profile sweep) | 1.03 | 1.03 | +2.4k | +2.4k | +2.6k | +2.6k | not rerun | | | |
| F|CW|WT (profile sweep) | 1.02 | 1.02 | +2.3k | +2.3k | -0.7k | -0.7k | not rerun | | | |
| E|SL|PS|NY|P2+N1 (profile sweep) | 1.02 | 1.02 | +2.3k | +2.3k | +1.7k | +1.7k | not rerun | | | |
| E|SL|PS|NY|P2+L1 (profile sweep) | 1.02 | 1.02 | +2.1k | +2.1k | +1.6k | +1.6k | not rerun | | | |
| C|A|A09 (profile sweep) | 1.03 | 1.03 | +2.0k | +2.0k | +1.0k | +1.0k | not rerun | | | |
| E|SL|PB|NY|P2 (profile sweep) | 1.02 | 1.02 | +2.0k | +2.0k | +1.5k | +1.5k | not rerun | | | |
| B|L2SL|COMBO_RANK (profile sweep) | 1.05 | 1.05 | +1.6k | +1.6k | +2.7k | +2.7k | not rerun | | | |
| E|SL|PB|NY|G2k70 (profile sweep) | 1.01 | 1.01 | +1.6k | +1.6k | +1.1k | +1.1k | not rerun | | | |
| E|SL|PB|NY|P2+L2 (profile sweep) | 1.02 | 1.02 | +1.5k | +1.5k | +1.2k | +1.2k | not rerun | | | |
| A|H|L|M | 1.09 | 1.09 | +1.4k | +1.4k | -4.0k | -4.0k | 1.17 | -1.7k | -5.8k | +15.7k |
| C|D|D_L30t (profile sweep) | 1.11 | 1.11 | +1.4k | +1.4k | +0.5k | +0.5k | not rerun | | | |
| E|SL|PS|NY|P3+N1 (profile sweep) | 1.02 | 1.02 | +1.2k | +1.2k | +0.9k | +0.9k | not rerun | | | |
| E|SL|KB|Asia|P3+L2 (profile sweep) | 1.00 | 1.00 | +1.0k | +1.0k | +0.8k | +0.8k | not rerun | | | |
| E|SL|PS|NY|G2k70 (profile sweep) | 1.00 | 1.00 | +0.9k | +0.9k | +0.8k | +0.8k | not rerun | | | |
| E|SL|KB|Asia|P3 (profile sweep) | 1.00 | 1.00 | +0.8k | +0.8k | +0.7k | +0.7k | not rerun | | | |
| E|SL|WT|Asia|P1+L1 (profile sweep) | 1.03 | 1.03 | +0.5k | +0.5k | +0.7k | +0.7k | not rerun | | | |
| B|L2SL|HM_PRE (profile sweep) | 1.04 | 1.04 | +0.4k | +0.4k | -1.2k | -1.2k | not rerun | | | |
| E|SL|HM|NY|P1+L1.5 (profile sweep) | 1.03 | 1.03 | +0.4k | +0.4k | +1.6k | +1.6k | not rerun | | | |
| E|SL|PB|London|P3+L1.5 (profile sweep) | 1.03 | 1.03 | +0.4k | +0.4k | +0.3k | +0.3k | not rerun | | | |
| E|SL|PS|NY|P3+L2 (profile sweep) | 1.00 | 1.00 | +0.3k | +0.3k | +0.2k | +0.2k | not rerun | | | |
| C|D|D_B3s (profile sweep) | 1.19 | 1.19 | +0.2k | +0.2k | -1.4k | -1.4k | not rerun | | | |
| C|A|A01 (profile sweep) | 0.99 | 0.99 | +0.1k | +0.1k | +0.9k | +0.9k | not rerun | | | |
| E|SL|PS|NY|P3+L1.5 (profile sweep) | 1.01 | 1.01 | -0.1k | -0.1k | -0.3k | -0.3k | not rerun | | | |
| E|SL|PS|NY|L2 (profile sweep) | 1.00 | 1.00 | -0.1k | -0.1k | -0.1k | -0.1k | not rerun | | | |
| A|B|P|N | 1.08 | 1.08 | -0.2k | -0.2k | +1.6k | +1.6k | 1.14 | -10.1k | -7.1k | -20.0k |
| B|EXP2|B_U3 (profile sweep) | 1.02 | 1.02 | -0.3k | -0.3k | -0.5k | -0.5k | not rerun | | | |
| C|A|A07 (profile sweep) | 1.01 | 1.01 | -0.3k | -0.3k | -1.7k | -1.7k | not rerun | | | |
| C|D|D_B3e (profile sweep) | 1.14 | 1.14 | -0.5k | -0.5k | -1.9k | -1.9k | not rerun | | | |
| E|SL|ST|Asia|P1.5+N3 (profile sweep) | 1.01 | 1.01 | -0.6k | -0.6k | -0.5k | -0.5k | not rerun | | | |
| B|EXP2|P (profile sweep) | 0.98 | 0.98 | -0.7k | -0.7k | -5.6k | -5.6k | not rerun | | | |
| B|L2SL|SM_PRE (profile sweep) | 0.98 | 0.98 | -1.2k | -1.2k | -1.3k | -1.3k | not rerun | | | |
| E|SL|PS|London|N2 (profile sweep) | 1.00 | 1.00 | -1.2k | -1.2k | -0.9k | -0.9k | not rerun | | | |
| A|H|EP|N | 1.11 | 1.11 | -1.5k | -1.5k | -1.5k | -1.5k | 1.15 | -7.4k | -7.0k | -26.7k |
| E|SL|ST|NY|N2 (profile sweep) | 1.02 | 1.02 | -1.7k | -1.7k | -1.4k | -1.4k | not rerun | | | |
| E|SL|ST|NY|P3+N2 (profile sweep) | 1.02 | 1.02 | -2.6k | -2.6k | -2.5k | -2.5k | not rerun | | | |
| B|EXP2|B_U3_P (profile sweep) | 0.98 | 0.98 | -2.7k | -2.7k | -7.9k | -7.9k | not rerun | | | |
| E|SL|ST|Asia|P1.5+L2 (profile sweep) | 1.01 | 1.01 | -2.9k | -2.9k | -2.6k | -2.6k | not rerun | | | |
| B|L2SL|KB_RANK (profile sweep) | 0.98 | 0.98 | -2.9k | -2.9k | -2.7k | -2.7k | not rerun | | | |
| B|L2SL|ST_RANK (profile sweep) | 1.00 | 1.00 | -3.1k | -3.1k | -1.5k | -1.5k | not rerun | | | |
| B|L2SL|KB_PRE (profile sweep) | 0.97 | 0.97 | -3.2k | -3.2k | -2.6k | -2.6k | not rerun | | | |
| A|H|P|N | 1.10 | 1.10 | -3.5k | -3.5k | -1.8k | -1.8k | 1.15 | -12.4k | -10.0k | -28.2k |
| F|CW|HM (profile sweep) | 1.03 | 1.03 | -3.5k | -3.5k | -5.3k | -5.3k | not rerun | | | |
| B|L2SL|WT_RANK (profile sweep) | 1.00 | 1.00 | -3.8k | -3.8k | -3.2k | -3.2k | not rerun | | | |
| C|D|D_B3h (profile sweep) | 1.17 | 1.17 | -4.0k | -4.0k | -6.6k | -6.6k | not rerun | | | |
| B|L2SL|WT_PRE (profile sweep) | 0.98 | 0.98 | -4.5k | -4.5k | -4.4k | -4.4k | not rerun | | | |
| B|L2SL|PE_PRE (profile sweep) | 1.01 | 1.01 | -4.6k | -4.6k | -3.6k | -3.6k | not rerun | | | |
| B|L2SL|PE_RANK (profile sweep) | 0.99 | 0.99 | -4.8k | -4.8k | -3.6k | -3.6k | not rerun | | | |
| B|L2SL|ST_PRE (profile sweep) | 1.03 | 1.03 | -5.5k | -5.5k | -4.5k | -4.5k | not rerun | | | |
| H|L2SP|ALL_PRE_selected|N (profile sweep) | 1.09 | 1.09 | -5.5k | -5.5k | -5.9k | -5.9k | not rerun | | | |
| A|H|EPL|N | 1.19 | 1.19 | -5.9k | -5.9k | -11.4k | -11.4k | 1.32 | -7.4k | -13.7k | -10.0k |
| E|SL|ST|Asia|P1.5+N2 (profile sweep) | 1.02 | 1.02 | -6.7k | -6.7k | -6.0k | -6.0k | not rerun | | | |
| C|A|A02 (profile sweep) | 1.13 | 1.13 | -7.0k | -7.0k | -5.1k | -5.1k | not rerun | | | |
| F|CW|ST (profile sweep) | 1.10 | 1.10 | -7.1k | -7.1k | -6.6k | -6.6k | not rerun | | | |
| A|H|PL|N | 1.17 | 1.17 | -7.5k | -7.5k | -10.9k | -10.9k | 1.24 | -11.4k | -15.3k | -16.5k |
| B|EXP2|B_FROZEN_P (profile sweep) | 1.20 | 1.20 | -9.4k | -9.4k | -3.1k | -3.1k | not rerun | | | |
| F|CW|PE (profile sweep) | 1.10 | 1.10 | -11.3k | -11.3k | -8.8k | -8.8k | not rerun | | | |
| D|D6L_alone (profile sweep) | 1.18 | 1.18 | -12.0k | -12.0k | -8.5k | -8.5k | not rerun | | | |
| B|L2SL|ALL_PRE (profile sweep) | 1.07 | 1.07 | -15.8k | -15.8k | -15.2k | -15.2k | not rerun | | | |
| D|PROFIT_alone (profile sweep) | 0.98 | 0.98 | -16.3k | -16.3k | -16.3k | -16.3k | not rerun | | | |
| B|L2SL|COMBO_PRE (profile sweep) | 1.03 | 1.03 | -17.8k | -17.8k | -17.1k | -17.1k | not rerun | | | |
| B|EXP2|B_FROZEN (profile sweep) | 1.01 | 1.01 | -19.6k | -19.6k | -14.5k | -14.5k | not rerun | | | |
| B|EXP2|B_U3_L (profile sweep) | 1.05 | 1.05 | -23.6k | -23.6k | -19.7k | -19.7k | not rerun | | | |
| B|EXP2|L (profile sweep) | 1.06 | 1.06 | -24.0k | -24.0k | -19.5k | -19.5k | not rerun | | | |
| B|EXP2|B_U1_P (profile sweep) | 1.01 | 1.01 | -25.9k | -25.9k | -22.2k | -22.2k | not rerun | | | |
| F|CW|KB (profile sweep) | 0.97 | 0.97 | -27.0k | -27.0k | -26.1k | -26.1k | not rerun | | | |
| B|EXP2|B_U1 (profile sweep) | 0.92 | 0.92 | -29.1k | -29.1k | -27.6k | -27.6k | not rerun | | | |
| B|EXP2|B_U3_P_L (profile sweep) | 1.02 | 1.02 | -29.2k | -29.2k | -30.7k | -30.7k | not rerun | | | |
| B|EXP2|P_L (profile sweep) | 1.03 | 1.03 | -29.4k | -29.4k | -30.3k | -30.3k | not rerun | | | |
| D|JOINT3 (profile sweep) | 1.31 | 1.31 | -30.9k | -30.9k | -25.8k | -25.8k | not rerun | | | |
| D|JOINT10 (profile sweep) | 1.31 | 1.31 | -31.2k | -31.2k | -26.1k | -26.1k | not rerun | | | |
| D|JOINT20 (profile sweep) | 1.34 | 1.34 | -32.1k | -32.1k | -27.7k | -27.7k | not rerun | | | |
| D|LOSS20_alone (profile sweep) | 1.05 | 1.05 | -32.8k | -32.8k | -28.1k | -28.1k | not rerun | | | |
| D|LOSS10_alone (profile sweep) | 1.05 | 1.05 | -32.9k | -32.9k | -28.5k | -28.5k | not rerun | | | |
| B|EXP2|B_U2_P (profile sweep) | 0.96 | 0.96 | -33.4k | -33.4k | -28.0k | -28.0k | not rerun | | | |
| D|LOSS3_alone (profile sweep) | 1.05 | 1.05 | -34.0k | -34.0k | -29.3k | -29.3k | not rerun | | | |
| B|EXP2|B_U2 (profile sweep) | 0.94 | 0.94 | -34.0k | -34.0k | -29.6k | -29.6k | not rerun | | | |
| F|CW|ALL6 (profile sweep) | 1.20 | 1.20 | -47.2k | -47.2k | -50.2k | -50.2k | not rerun | | | |
| C|A|A10 (profile sweep) | 0.87 | 0.87 | -51.7k | -51.7k | -40.7k | -40.7k | not rerun | | | |
| B|EXP2|B_U2_L (profile sweep) | 0.85 | 0.85 | -55.0k | -55.0k | -48.1k | -48.1k | not rerun | | | |
| B|EXP2|B_U2_P_L (profile sweep) | 0.84 | 0.84 | -55.7k | -55.7k | -49.9k | -49.9k | not rerun | | | |
| B|EXP2|B_U1_L (profile sweep) | 0.90 | 0.90 | -58.0k | -58.0k | -50.8k | -50.8k | not rerun | | | |
| B|EXP2|B_FROZEN_P_L (profile sweep) | 0.89 | 0.89 | -61.7k | -61.7k | -53.3k | -53.3k | not rerun | | | |
| B|EXP2|B_FROZEN_L (profile sweep) | 0.84 | 0.84 | -62.7k | -62.7k | -53.3k | -53.3k | not rerun | | | |
| B|EXP2|B_U1_P_L (profile sweep) | 0.91 | 0.91 | -63.3k | -63.3k | -55.0k | -55.0k | not rerun | | | |

## 6. Does equal risk transfer? Scale calibrated on PRE only (worst-20 of 75 weeks), measured in HOLD / L6M (out of sample for the scale)
| series | c_PRE | Y26 | L6M | HOLD | X' | HOLD worst-20 rule / stack | HOLD SD rule / stack | L6M worst-20 rule / stack |
|--|--|--|--|--|--|--|--|--|
| A|B|E|N | 1.24 | +99.3k (138.9k) | +69.6k (43.7k) | +63.0k (39.9k) | -12.8k (25.7k) | 484k / -1095k | 151k / 173k | 1452k / -153k |
| A|B|EPL|M | 1.16 | +121.1k (181.8k) | +65.1k (60.0k) | +62.4k (54.4k) | -4.3k (33.7k) | -25k / -1777k | 122k / 163k | 734k / -882k |
| A|B|EL|N | 1.16 | +90.8k (144.0k) | +57.0k (47.4k) | +52.0k (44.3k) | -12.1k (31.0k) | 346k / -1095k | 141k / 173k | 1275k / -153k |
| A|B|EP|M | 1.27 | +125.9k (182.4k) | +68.1k (61.4k) | +65.0k (54.6k) | -3.7k (31.6k) | -349k / -1777k | 150k / 163k | 552k / -882k |
| A|B|E|M | 1.24 | +106.9k (156.6k) | +69.8k (45.8k) | +61.5k (42.7k) | -10.8k (25.4k) | -353k / -1777k | 146k / 163k | 607k / -882k |
| A|B|EL|M | 1.15 | +97.0k (150.4k) | +62.2k (49.3k) | +56.2k (46.6k) | -9.0k (30.7k) | -309k / -1777k | 133k / 163k | 538k / -882k |
| H|L2SP|ALL_L6M_rank1|M | 1.02 | +84.4k (121.3k) | +44.0k (45.2k) | +38.7k (41.7k) | -0.8k (30.9k) | -346k / -1419k | 128k / 149k | 414k / -628k |
| A|B|PL|M | 1.05 | +95.0k (163.3k) | +46.4k (47.9k) | +44.2k (42.8k) | +3.9k (24.8k) | -733k / -1777k | 146k / 163k | 151k / -882k |
| A|H|EP|M | 1.11 | +67.2k (159.7k) | +38.4k (51.5k) | +35.7k (45.1k) | +5.2k (27.7k) | -958k / -1777k | 148k / 163k | 0k / -882k |
| A|B|EP|N | 1.14 | +94.8k (163.2k) | +26.3k (56.8k) | +26.9k (51.2k) | -13.7k (30.8k) | -122k / -1095k | 135k / 173k | 689k / -153k |
| A|B|EPL|N | 1.04 | +88.0k (174.3k) | +20.6k (59.5k) | +21.8k (54.8k) | -14.2k (33.2k) | 110k / -1095k | 110k / 173k | 789k / -153k |
| A|H|P|M | 1.07 | +62.5k (146.0k) | +32.9k (46.9k) | +32.7k (41.2k) | +5.1k (26.8k) | -986k / -1777k | 142k / 163k | -67k / -882k |
| A|H|PL|M | 1.44 | +100.5k (224.5k) | +45.5k (72.5k) | +35.6k (66.3k) | +16.8k (35.5k) | -1763k / -1777k | 217k / 163k | -359k / -882k |
| A|H|EPL|M | 1.45 | +90.8k (226.8k) | +45.2k (70.0k) | +32.9k (65.0k) | +17.5k (34.0k) | -1820k / -1777k | 216k / 163k | -356k / -882k |
| A|B|P|M | 1.07 | +43.1k (103.5k) | +29.9k (37.6k) | +29.6k (33.1k) | +8.5k (21.2k) | -1150k / -1777k | 149k / 163k | -204k / -882k |
| G|ADDUW|B1_PRE#1022 | 1.40 | +42.2k (63.9k) | +25.6k (40.7k) | +24.8k (37.5k) | -27.3k (36.0k) | -447k / -743k | 163k / 153k | 469k / 262k |
| A|B|L|N | 1.02 | +56.1k (72.1k) | +21.6k (30.2k) | +22.3k (26.6k) | -3.3k (17.6k) | -345k / -1095k | 159k / 173k | 549k / -153k |
| A|H|EL|N | 1.32 | +90.1k (117.1k) | +36.8k (54.6k) | +26.6k (53.1k) | +8.1k (20.8k) | -1326k / -1095k | 228k / 173k | 109k / -153k |
| A|B|L|M | 0.97 | +51.5k (94.2k) | +22.8k (32.3k) | +21.1k (29.8k) | -3.1k (17.5k) | -1024k / -1777k | 146k / 163k | -197k / -882k |
| A|H|E|N | 1.05 | +19.9k (42.7k) | +21.5k (16.3k) | +21.6k (15.7k) | +3.1k (8.6k) | -661k / -1095k | 177k / 173k | 349k / -153k |
| A|B|PL|N | 0.95 | +56.7k (162.8k) | +8.6k (48.4k) | +9.9k (43.6k) | -4.5k (24.4k) | -458k / -1095k | 134k / 173k | 358k / -153k |
| C|D|D_L20s | 1.54 | +88.0k (155.3k) | +22.0k (61.4k) | +16.1k (56.4k) | -21.6k (35.4k) | -985k / -743k | 192k / 153k | 175k / 262k |
| A|H|L|N | 1.26 | +84.2k (103.1k) | +23.6k (44.1k) | +17.5k (45.8k) | +6.1k (21.1k) | -1291k / -1095k | 219k / 173k | 68k / -153k |
| C|A|A05 | 1.17 | +22.0k (52.0k) | +17.2k (24.7k) | +13.0k (23.4k) | -9.8k (13.9k) | -484k / -743k | 164k / 153k | 543k / 262k |
| A|H|EL|M | 1.25 | +67.9k (81.7k) | +18.5k (43.7k) | +9.6k (42.5k) | +5.5k (18.7k) | -2057k / -1777k | 202k / 163k | -834k / -882k |
| B|L2SL|HM_RANK | 1.15 | +15.2k (27.6k) | +19.0k (11.2k) | +15.4k (13.0k) | +1.2k (10.0k) | -634k / -743k | 173k / 152k | 471k / 204k |
| A|H|E|M | 1.01 | +19.5k (41.8k) | +13.6k (14.7k) | +11.8k (14.1k) | +2.9k (8.4k) | -1575k / -1777k | 167k / 163k | -645k / -882k |
| C|A|A04 | 1.55 | +70.7k (88.1k) | +29.6k (38.1k) | +18.7k (41.6k) | +3.0k (31.4k) | -804k / -743k | 214k / 153k | 650k / 262k |
| G|ADDUW|B2_L6Mrank#4 | 0.90 | +1.3k (44.4k) | +7.0k (17.9k) | +6.2k (16.6k) | -1.6k (13.3k) | -500k / -743k | 143k / 153k | 451k / 262k |
| G|ADDUW|B2_PRE#5 | 0.99 | +0.3k (31.6k) | +5.9k (18.3k) | +5.3k (16.2k) | +4.1k (9.7k) | -536k / -743k | 143k / 153k | 420k / 262k |
| H|L2SP|ALL_L6M_rank1|N | 0.84 | +37.0k (136.9k) | -2.1k (48.2k) | -3.9k (46.2k) | -12.2k (31.6k) | -245k / -857k | 107k / 157k | 370k / -22k |
| C|F|A06+HM5R+B02 | 1.73 | +48.6k (148.0k) | +30.0k (49.9k) | +18.7k (52.2k) | -3.5k (36.1k) | -918k / -743k | 216k / 153k | 581k / 262k |
| C|F|A06+B02 | 1.37 | +22.0k (50.9k) | +20.0k (25.5k) | +15.1k (26.9k) | -1.4k (18.1k) | -741k / -743k | 188k / 153k | 513k / 262k |
| C|F|A06+HM5R | 1.58 | +44.6k (142.3k) | +26.4k (44.8k) | +15.9k (46.4k) | -7.3k (34.2k) | -877k / -743k | 205k / 153k | 545k / 262k |
| C|F|C1 | 1.17 | +11.6k (24.6k) | +5.1k (15.9k) | +8.0k (16.2k) | -4.1k (12.5k) | -676k / -743k | 157k / 153k | 267k / 262k |
| B|L2SL|ALL_RANK | 0.96 | -2.0k (19.1k) | +8.8k (16.0k) | +7.3k (14.5k) | -4.6k (14.7k) | -596k / -743k | 152k / 152k | 330k / 204k |
| E|SL|PB|NY|P1+N3 | 1.07 | +9.2k (5.2k) | +8.4k (8.0k) | +7.5k (7.4k) | +0.2k (6.8k) | -564k / -592k | 159k / 150k | 392k / 311k |
| C|D|D_L30s | 1.26 | +42.9k (68.5k) | +13.5k (36.0k) | +8.9k (32.7k) | -12.6k (19.8k) | -801k / -743k | 180k / 153k | 248k / 262k |
| C|F|HM5R+B02 | 1.38 | +26.1k (84.8k) | +16.9k (33.3k) | +12.0k (32.9k) | +7.5k (23.5k) | -770k / -743k | 183k / 153k | 436k / 262k |
| E|SL|PB|NY|P1 | 1.07 | +9.0k (5.3k) | +7.9k (7.9k) | +6.8k (7.2k) | -0.3k (6.6k) | -573k / -592k | 158k / 150k | 385k / 311k |
| C|A|A08 | 1.06 | +25.9k (44.4k) | +9.4k (13.8k) | +7.3k (13.2k) | +1.3k (8.8k) | -670k / -743k | 164k / 153k | 441k / 262k |
| F|CW|SM | 0.94 | +3.3k (40.5k) | +5.1k (13.4k) | +3.9k (13.7k) | +1.4k (9.7k) | -1420k / -1695k | 164k / 181k | -532k / -763k |
| E|SL|PB|NY|P1+L2 | 1.07 | +9.4k (5.2k) | +7.7k (8.3k) | +6.8k (7.6k) | -0.0k (6.1k) | -588k / -592k | 159k / 150k | 367k / 311k |
| C|A|A06 | 1.28 | +18.5k (43.4k) | +15.0k (21.3k) | +9.4k (21.6k) | -6.3k (14.8k) | -796k / -743k | 182k / 153k | 396k / 262k |
| E|SL|PB|NY|G1k70 | 1.06 | +9.2k (5.6k) | +6.4k (7.5k) | +5.5k (6.7k) | +1.1k (5.9k) | -583k / -592k | 157k / 150k | 365k / 311k |
| C|A|A03 | 1.03 | +5.6k (13.7k) | +7.2k (6.4k) | +6.1k (6.0k) | -0.1k (3.0k) | -670k / -743k | 158k / 153k | 372k / 262k |
| H|L2SP|ALL_PRE_selected|M | 1.13 | +17.8k (58.5k) | +5.4k (22.9k) | +4.5k (20.3k) | +1.7k (15.7k) | -1294k / -1419k | 152k / 149k | -470k / -628k |
| E|SL|PB|NY|P1+L1 | 1.08 | +5.0k (7.8k) | +6.9k (9.1k) | +5.9k (8.5k) | -1.1k (8.7k) | -605k / -592k | 158k / 150k | 373k / 311k |
| E|SL|PB|NY|P1+L1.5 | 1.07 | +5.8k (10.3k) | +6.6k (8.0k) | +5.5k (7.6k) | -1.2k (6.8k) | -610k / -592k | 158k / 150k | 360k / 311k |
| C|F|HM5R | 1.25 | +21.7k (85.6k) | +12.1k (29.5k) | +7.9k (28.5k) | +2.5k (21.6k) | -725k / -743k | 173k / 153k | 416k / 262k |
| C|F|HM5M | 1.17 | +12.8k (39.9k) | +9.3k (14.0k) | +6.3k (14.4k) | +2.1k (10.7k) | -694k / -743k | 167k / 153k | 400k / 262k |
| C|D|D_B4s | 1.17 | +22.4k (44.9k) | +8.9k (22.3k) | +6.1k (20.4k) | -8.0k (13.3k) | -831k / -743k | 173k / 153k | 230k / 262k |
| C|D|D_L40s | 1.15 | +18.1k (35.8k) | +11.5k (12.5k) | +8.2k (13.0k) | -2.2k (8.6k) | -834k / -743k | 176k / 153k | 295k / 262k |
| C|D|D_B2s | 1.65 | +74.0k (206.2k) | +10.3k (69.1k) | +7.2k (63.5k) | -17.9k (39.8k) | -1069k / -743k | 191k / 153k | -26k / 262k |
| E|SL|PB|NY|P1.5+N2 | 1.05 | +7.4k (7.7k) | +5.9k (5.8k) | +5.3k (5.8k) | -1.3k (5.6k) | -562k / -592k | 156k / 150k | 392k / 311k |
| E|SL|PB|London|P1.5+N1 | 1.07 | +9.0k (32.2k) | +4.3k (9.8k) | +3.9k (8.9k) | +4.2k (8.3k) | -621k / -592k | 156k / 150k | 312k / 311k |
| E|SL|PB|NY|G1k50 | 1.04 | +8.5k (6.9k) | +4.8k (7.1k) | +4.1k (6.4k) | +1.4k (4.7k) | -616k / -592k | 157k / 150k | 330k / 311k |
| E|SL|PB|NY|P1+N1 | 1.08 | +3.2k (8.9k) | +6.4k (8.2k) | +5.2k (8.0k) | -2.5k (9.1k) | -617k / -592k | 159k / 150k | 374k / 311k |
| E|SL|PB|London|P3+N1 | 1.06 | +3.8k (27.9k) | +3.9k (8.1k) | +3.8k (7.3k) | +2.0k (6.2k) | -601k / -592k | 156k / 150k | 327k / 311k |
| C|F|B02 | 1.07 | +2.7k (11.8k) | +4.4k (8.5k) | +4.9k (9.2k) | +4.6k (8.1k) | -709k / -743k | 159k / 153k | 357k / 262k |
| E|SL|PB|London|P2+N1 | 1.07 | +6.5k (32.2k) | +3.6k (9.3k) | +3.4k (8.4k) | +2.9k (6.6k) | -623k / -592k | 156k / 150k | 313k / 311k |
| E|SL|PS|London|P1+N3 | 1.03 | +14.6k (18.1k) | +3.7k (6.9k) | +3.3k (6.2k) | +0.2k (4.9k) | -496k / -517k | 149k / 144k | 411k / 365k |
| E|SL|WT|NY|P2+N1 | 1.01 | +5.4k (8.8k) | +2.6k (5.9k) | +2.5k (5.2k) | +1.8k (4.9k) | -518k / -592k | 149k / 150k | 413k / 311k |
| E|SL|PS|London|P1+N2 | 1.04 | +9.1k (25.2k) | +3.2k (7.2k) | +3.0k (6.6k) | +0.0k (4.8k) | -524k / -517k | 150k / 144k | 389k / 365k |
| E|SL|PB|NY|P1.5 | 1.03 | +3.9k (10.3k) | +3.2k (4.4k) | +2.7k (4.1k) | -1.2k (5.1k) | -568k / -592k | 153k / 150k | 362k / 311k |
| E|SL|PS|NY|P1.5+L1 | 1.02 | +6.8k (11.7k) | +2.8k (4.8k) | +2.2k (4.6k) | -0.4k (3.9k) | -499k / -517k | 146k / 144k | 414k / 365k |
| E|SL|WT|NY|P2 | 1.01 | +4.4k (5.7k) | +2.5k (3.1k) | +2.3k (2.8k) | +0.3k (2.5k) | -569k / -592k | 151k / 150k | 347k / 311k |
| B|L2SL|SM_RANK | 0.97 | +4.2k (18.7k) | +1.4k (8.4k) | +1.6k (7.9k) | -1.7k (5.0k) | -602k / -743k | 144k / 152k | 276k / 204k |
| E|SL|PB|NY|P1.5+L2 | 1.04 | +5.1k (9.1k) | +3.0k (5.0k) | +2.6k (4.7k) | -0.9k (4.8k) | -586k / -592k | 153k / 150k | 349k / 311k |
| E|SL|HM|NY|P1.5+L1.5 | 1.04 | +7.6k (23.9k) | +3.3k (10.1k) | +3.4k (9.6k) | +1.0k (7.3k) | -589k / -592k | 156k / 150k | 349k / 311k |
| F|CW|WT | 1.01 | -13.1k (32.3k) | +1.9k (11.7k) | -1.0k (13.0k) | -4.7k (10.1k) | -1647k / -1695k | 176k / 181k | -606k / -763k |
| E|SL|PS|NY|P2+N1 | 1.01 | +5.9k (11.9k) | +1.7k (4.8k) | +1.2k (4.4k) | +0.2k (4.5k) | -515k / -517k | 146k / 144k | 399k / 365k |
| E|SL|PS|NY|P2+L1 | 1.02 | +4.9k (13.8k) | +2.3k (4.4k) | +1.7k (4.2k) | +0.1k (3.7k) | -520k / -517k | 147k / 144k | 397k / 365k |
| C|A|A09 | 1.01 | -2.4k (32.1k) | +1.1k (10.2k) | +0.3k (9.1k) | -0.9k (4.6k) | -667k / -743k | 147k / 153k | 360k / 262k |
| E|SL|PB|NY|P2 | 1.02 | +3.1k (7.7k) | +2.4k (3.3k) | +1.8k (3.0k) | -0.9k (3.8k) | -583k / -592k | 153k / 150k | 340k / 311k |
| B|L2SL|COMBO_RANK | 0.98 | +0.4k (34.3k) | -3.0k (21.2k) | -1.1k (19.6k) | -10.0k (13.5k) | -460k / -743k | 134k / 152k | 339k / 204k |
| E|SL|PB|NY|G2k70 | 1.02 | +3.0k (5.9k) | +2.0k (2.6k) | +1.4k (2.5k) | +0.5k (2.5k) | -582k / -592k | 152k / 150k | 338k / 311k |
| E|SL|PB|NY|P2+L2 | 1.03 | +4.3k (7.1k) | +2.1k (4.2k) | +1.7k (3.8k) | -0.6k (3.4k) | -600k / -592k | 153k / 150k | 327k / 311k |
| A|H|L|M | 1.18 | +58.8k (67.9k) | +3.0k (34.2k) | -3.6k (33.0k) | +3.5k (17.7k) | -2010k / -1777k | 182k / 163k | -896k / -882k |
| C|D|D_L30t | 1.14 | +11.3k (39.8k) | +3.5k (24.5k) | +2.1k (22.2k) | -10.7k (15.3k) | -745k / -743k | 164k / 153k | 239k / 262k |
| E|SL|PS|NY|P3+N1 | 1.01 | +1.6k (12.0k) | +0.5k (3.9k) | +0.3k (3.6k) | +0.2k (4.5k) | -522k / -517k | 145k / 144k | 374k / 365k |
| E|SL|KB|Asia|P3+L2 | 1.00 | +3.8k (11.0k) | +0.7k (3.2k) | +0.6k (2.8k) | -0.1k (0.3k) | -578k / -592k | 149k / 150k | 323k / 311k |
| E|SL|PS|NY|G2k70 | 1.01 | +3.3k (11.4k) | +1.2k (3.1k) | +1.0k (2.7k) | +0.7k (1.3k) | -526k / -517k | 146k / 144k | 367k / 365k |
| E|SL|KB|Asia|P3 | 1.00 | +3.9k (10.9k) | +0.8k (2.3k) | +0.7k (2.0k) | +0.0k (0.0k) | -569k / -592k | 150k / 150k | 334k / 311k |
| E|SL|WT|Asia|P1+L1 | 1.04 | -6.7k (23.7k) | +1.6k (9.6k) | +1.7k (9.3k) | +1.5k (4.6k) | -681k / -592k | 160k / 150k | 310k / 311k |
| B|L2SL|HM_PRE | 1.10 | +4.0k (36.7k) | +4.5k (14.4k) | +2.0k (15.9k) | -1.4k (9.2k) | -834k / -743k | 171k / 152k | 191k / 204k |
| E|SL|HM|NY|P1+L1.5 | 1.04 | +4.8k (23.1k) | +1.3k (13.2k) | +2.4k (12.1k) | -0.3k (9.9k) | -655k / -592k | 156k / 150k | 262k / 311k |
| E|SL|PB|London|P3+L1.5 | 1.03 | +2.4k (18.0k) | +0.6k (5.1k) | +0.4k (4.6k) | +1.6k (2.6k) | -599k / -592k | 153k / 150k | 328k / 311k |
| E|SL|PS|NY|P3+L2 | 1.00 | +0.0k (3.2k) | +0.3k (1.3k) | +0.3k (1.1k) | -0.1k (1.6k) | -507k / -517k | 144k / 144k | 379k / 365k |
| C|D|D_B3s | 1.27 | +27.6k (83.0k) | +4.8k (36.9k) | +1.9k (33.3k) | -11.1k (25.0k) | -875k / -743k | 175k / 153k | 127k / 262k |
| C|A|A01 | 1.01 | -2.3k (19.4k) | +1.2k (8.6k) | +1.7k (7.7k) | -0.6k (4.6k) | -665k / -743k | 154k / 153k | 332k / 262k |
| E|SL|PS|NY|P3+L1.5 | 1.01 | -0.8k (4.3k) | -0.2k (2.2k) | -0.5k (2.0k) | -1.0k (2.6k) | -522k / -517k | 144k / 144k | 373k / 365k |
| E|SL|PS|NY|L2 | 1.00 | -0.1k (2.8k) | +0.1k (1.2k) | +0.1k (1.1k) | -0.1k (1.5k) | -509k / -517k | 144k / 144k | 374k / 365k |
| A|B|P|N | 0.98 | +10.5k (118.1k) | -5.9k (39.6k) | -3.0k (35.3k) | -0.1k (20.7k) | -870k / -1095k | 139k / 173k | -3k / -153k |
| B|EXP2|B_U3 | 1.02 | -8.7k (19.9k) | +0.2k (9.0k) | -0.1k (8.0k) | -0.8k (6.3k) | -745k / -743k | 153k / 152k | 227k / 204k |
| C|A|A07 | 0.98 | -10.0k (43.9k) | -1.9k (19.2k) | -2.8k (17.0k) | -1.6k (7.8k) | -613k / -743k | 142k / 153k | 401k / 262k |
| C|D|D_B3e | 1.18 | +10.6k (72.0k) | +2.1k (32.0k) | -0.1k (29.2k) | -16.3k (21.9k) | -818k / -743k | 165k / 153k | 163k / 262k |
| E|SL|ST|Asia|P1.5+N3 | 1.03 | +19.5k (57.5k) | +0.7k (14.7k) | +0.5k (12.9k) | +1.1k (2.2k) | -604k / -592k | 153k / 150k | 331k / 311k |
| B|EXP2|P | 0.91 | +17.9k (56.9k) | -5.5k (18.3k) | -9.1k (28.4k) | -18.0k (20.7k) | -637k / -743k | 131k / 152k | 104k / 204k |
| B|L2SL|SM_PRE | 0.98 | -2.2k (13.4k) | -1.6k (5.1k) | -1.6k (4.7k) | +0.9k (2.3k) | -699k / -743k | 147k / 152k | 196k / 204k |
| E|SL|PS|London|N2 | 1.00 | -7.6k (13.2k) | -1.3k (3.3k) | -1.1k (2.9k) | -0.3k (0.9k) | -546k / -517k | 144k / 144k | 330k / 365k |
| A|H|EP|N | 0.97 | +31.2k (158.0k) | -9.0k (51.7k) | -7.4k (45.7k) | -6.7k (26.7k) | -816k / -1095k | 130k / 173k | 51k / -153k |
| E|SL|ST|NY|N2 | 1.02 | +3.3k (14.2k) | -1.4k (8.6k) | -1.2k (7.6k) | -2.8k (4.4k) | -627k / -592k | 151k / 150k | 292k / 311k |
| E|SL|ST|NY|P3+N2 | 1.02 | -0.2k (20.6k) | -2.4k (9.4k) | -2.3k (8.3k) | -2.5k (4.2k) | -608k / -592k | 149k / 150k | 314k / 311k |
| B|EXP2|B_U3_P | 0.91 | +9.4k (67.3k) | -7.2k (20.6k) | -11.1k (29.7k) | -19.7k (21.7k) | -648k / -743k | 129k / 152k | 129k / 204k |
| E|SL|ST|Asia|P1.5+L2 | 1.02 | +4.9k (34.6k) | -2.3k (10.5k) | -2.1k (9.2k) | +0.9k (1.7k) | -681k / -592k | 153k / 150k | 244k / 311k |
| B|L2SL|KB_RANK | 0.95 | -6.2k (11.3k) | -5.1k (4.9k) | -4.4k (5.1k) | -0.2k (4.8k) | -759k / -743k | 144k / 152k | 147k / 204k |
| B|L2SL|ST_RANK | 1.01 | +5.3k (46.9k) | -2.7k (17.7k) | -1.2k (15.6k) | -5.8k (8.0k) | -719k / -743k | 150k / 152k | 178k / 204k |
| B|L2SL|KB_PRE | 0.95 | +1.6k (8.6k) | -4.7k (5.9k) | -3.7k (5.6k) | -2.7k (3.7k) | -776k / -743k | 146k / 152k | 122k / 204k |
| A|H|P|N | 0.95 | +22.9k (160.4k) | -11.5k (50.3k) | -8.2k (45.1k) | -6.6k (26.3k) | -803k / -1095k | 127k / 173k | 20k / -153k |
| F|CW|HM | 1.11 | +13.2k (41.8k) | -1.6k (25.3k) | -4.1k (25.4k) | +5.5k (15.9k) | -1769k / -1695k | 198k / 181k | -657k / -763k |
| B|L2SL|WT_RANK | 1.01 | -11.6k (13.6k) | -3.5k (7.0k) | -3.0k (6.2k) | -0.4k (5.4k) | -787k / -743k | 152k / 152k | 152k / 204k |
| C|D|D_B3h | 1.21 | +5.6k (50.3k) | -1.7k (27.8k) | -5.1k (25.9k) | -9.5k (19.3k) | -996k / -743k | 168k / 153k | 7k / 262k |
| B|L2SL|WT_PRE | 0.98 | -12.6k (24.0k) | -4.7k (6.1k) | -4.6k (5.3k) | +1.4k (2.9k) | -809k / -743k | 149k / 152k | 121k / 204k |
| B|L2SL|PE_PRE | 1.03 | -3.8k (14.0k) | -3.5k (8.5k) | -2.7k (8.0k) | -0.8k (6.0k) | -829k / -743k | 156k / 152k | 105k / 204k |
| B|L2SL|PE_RANK | 0.97 | -2.0k (17.0k) | -6.2k (8.0k) | -4.7k (7.7k) | -2.2k (6.3k) | -695k / -743k | 143k / 152k | 170k / 204k |
| B|L2SL|ST_PRE | 1.02 | +24.1k (44.3k) | -5.8k (20.2k) | -4.8k (17.7k) | -5.4k (8.2k) | -783k / -743k | 150k / 152k | 107k / 204k |
| H|L2SP|ALL_PRE_selected|N | 1.02 | +4.0k (64.6k) | -9.3k (22.9k) | -9.0k (20.6k) | -4.0k (16.2k) | -819k / -857k | 142k / 157k | -41k / -22k |
| A|H|EPL|N | 1.29 | +54.6k (230.7k) | -1.1k (66.8k) | -8.2k (59.4k) | +5.0k (30.3k) | -1575k / -1095k | 193k / 173k | -265k / -153k |
| E|SL|ST|Asia|P1.5+N2 | 1.02 | +3.7k (30.2k) | -6.5k (13.1k) | -5.7k (11.5k) | +0.8k (1.7k) | -690k / -592k | 149k / 150k | 235k / 311k |
| C|A|A02 | 1.11 | -7.2k (62.8k) | -8.5k (38.1k) | -6.1k (35.7k) | -17.6k (21.4k) | -490k / -743k | 140k / 153k | 333k / 262k |
| F|CW|ST | 1.05 | +12.3k (47.7k) | -8.2k (24.9k) | -7.3k (23.6k) | -4.2k (16.8k) | -1712k / -1695k | 162k / 181k | -860k / -763k |
| A|H|PL|N | 1.28 | +55.9k (236.5k) | -2.6k (69.2k) | -7.5k (61.0k) | +3.8k (31.1k) | -1562k / -1095k | 194k / 173k | -307k / -153k |
| B|EXP2|B_FROZEN_P | 1.24 | -7.0k (94.0k) | -7.4k (78.5k) | -1.3k (75.6k) | -1.0k (41.7k) | -947k / -743k | 166k / 152k | -338k / 204k |
| F|CW|PE | 1.13 | -1.5k (32.6k) | -10.7k (24.2k) | -8.4k (21.9k) | +4.0k (15.7k) | -1997k / -1695k | 193k / 181k | -1096k / -763k |
| D|D6L_alone | 1.07 | +67.0k (121.7k) | -12.6k (59.4k) | -8.5k (56.5k) | -16.7k (36.2k) | -1646k / -1777k | 130k / 163k | -1006k / -882k |
| B|L2SL|ALL_PRE | 1.06 | +23.3k (24.9k) | -16.0k (32.1k) | -15.4k (28.1k) | -13.7k (15.6k) | -1067k / -743k | 149k / 152k | -206k / 204k |
| D|PROFIT_alone | 0.95 | +27.6k (113.0k) | -16.4k (38.2k) | -16.1k (38.0k) | -1.2k (23.6k) | -1816k / -1777k | 132k / 163k | -1151k / -882k |
| B|L2SL|COMBO_PRE | 1.05 | +10.6k (30.7k) | -17.0k (23.6k) | -16.5k (21.7k) | -8.1k (14.5k) | -1069k / -743k | 156k / 152k | -127k / 204k |
| B|EXP2|B_FROZEN | 0.95 | -15.1k (109.8k) | -22.4k (69.0k) | -16.8k (67.2k) | -2.7k (41.9k) | -859k / -743k | 131k / 152k | -309k / 204k |
| B|EXP2|B_U3_L | 1.07 | -19.5k (75.7k) | -22.8k (38.0k) | -19.0k (35.6k) | -17.0k (23.6k) | -1297k / -743k | 158k / 152k | -453k / 204k |
| B|EXP2|L | 1.04 | -18.0k (71.4k) | -24.5k (34.3k) | -19.8k (32.4k) | -14.6k (21.3k) | -1183k / -743k | 149k / 152k | -416k / 204k |
| B|EXP2|B_U1_P | 0.86 | -12.3k (164.9k) | -31.6k (57.7k) | -26.5k (55.2k) | -15.5k (35.9k) | -892k / -743k | 117k / 152k | -346k / 204k |
| F|CW|KB | 1.01 | +0.3k (66.7k) | -26.9k (32.8k) | -26.3k (28.4k) | +4.4k (15.9k) | -2286k / -1695k | 188k / 181k | -1231k / -763k |
| B|EXP2|B_U1 | 0.80 | -40.0k (145.7k) | -33.8k (56.9k) | -30.8k (53.3k) | -9.9k (36.7k) | -932k / -743k | 114k / 152k | -272k / 204k |
| B|EXP2|B_U3_P_L | 1.02 | -10.1k (53.8k) | -29.3k (31.8k) | -30.7k (37.7k) | -29.0k (27.8k) | -1132k / -743k | 131k / 152k | -361k / 204k |
| B|EXP2|P_L | 1.00 | -8.6k (48.0k) | -30.7k (29.2k) | -31.1k (36.2k) | -26.7k (28.4k) | -1086k / -743k | 124k / 152k | -365k / 204k |
| D|JOINT3 | 1.13 | +43.4k (119.0k) | -29.3k (60.3k) | -23.5k (62.1k) | -11.4k (39.9k) | -1737k / -1777k | 112k / 163k | -1265k / -882k |
| D|JOINT10 | 1.14 | +43.5k (119.0k) | -29.6k (60.4k) | -23.8k (62.2k) | -11.1k (40.0k) | -1746k / -1777k | 112k / 163k | -1274k / -882k |
| D|JOINT20 | 1.16 | +43.1k (118.6k) | -30.4k (61.3k) | -25.2k (62.6k) | -9.4k (40.3k) | -1809k / -1777k | 116k / 163k | -1318k / -882k |
| D|LOSS20_alone | 0.98 | -3.0k (93.7k) | -31.9k (41.6k) | -26.9k (37.8k) | +0.9k (32.7k) | -1893k / -1777k | 127k / 163k | -1191k / -882k |
| D|LOSS10_alone | 0.97 | -1.8k (94.2k) | -31.9k (41.9k) | -27.1k (38.7k) | +0.7k (32.7k) | -1880k / -1777k | 124k / 163k | -1189k / -882k |
| B|EXP2|B_U2_P | 0.88 | -44.6k (147.7k) | -36.0k (52.7k) | -30.0k (54.4k) | -19.0k (36.0k) | -898k / -743k | 116k / 152k | -370k / 204k |
| D|LOSS3_alone | 0.96 | -1.5k (95.1k) | -32.7k (42.6k) | -27.6k (39.4k) | +0.4k (32.8k) | -1876k / -1777k | 124k / 163k | -1197k / -882k |
| B|EXP2|B_U2 | 0.84 | -45.3k (148.8k) | -37.3k (54.4k) | -32.0k (54.0k) | -15.8k (35.1k) | -959k / -743k | 111k / 152k | -385k / 204k |
| F|CW|ALL6 | 1.27 | +16.7k (204.4k) | -48.2k (69.8k) | -51.8k (63.8k) | +7.2k (48.0k) | -2634k / -1695k | 184k / 181k | -1641k / -763k |
| C|A|A10 | 0.71 | -30.6k (53.4k) | -55.6k (48.4k) | -43.1k (56.6k) | -11.5k (37.8k) | -767k / -743k | 85k / 153k | -388k / 262k |
| B|EXP2|B_U2_L | 0.78 | -82.7k (112.4k) | -55.9k (43.2k) | -48.4k (45.6k) | -31.7k (38.1k) | -1069k / -743k | 102k / 152k | -573k / 204k |
| B|EXP2|B_U2_P_L | 0.82 | -90.0k (108.3k) | -55.9k (43.0k) | -50.0k (46.3k) | -32.5k (38.9k) | -1155k / -743k | 112k / 152k | -589k / 204k |
| B|EXP2|B_U1_L | 0.82 | -68.6k (113.7k) | -58.6k (49.3k) | -50.9k (48.3k) | -31.7k (38.2k) | -1313k / -743k | 108k / 152k | -787k / 204k |
| B|EXP2|B_FROZEN_P_L | 0.86 | -55.4k (69.5k) | -61.8k (56.0k) | -53.2k (57.2k) | -31.3k (41.8k) | -1250k / -743k | 107k / 152k | -794k / 204k |
| B|EXP2|B_FROZEN_L | 0.74 | -56.1k (82.9k) | -63.0k (54.5k) | -53.2k (56.7k) | -34.3k (41.8k) | -1067k / -743k | 92k / 152k | -697k / 204k |
| B|EXP2|B_U1_P_L | 0.81 | -62.6k (102.0k) | -63.6k (47.5k) | -54.7k (48.9k) | -30.1k (39.7k) | -1415k / -743k | 105k / 152k | -923k / 204k |

## 7. Placebo: random skip / random exit scaled to equal risk, matched on weekly SD
Frame-A engine reruns, M and N basis: a random fraction q = 0.1..0.7 of signals skipped, or probability p = 0.1..0.9 of an exit at a uniform random second of the trade; 10 draws per setting (160 + 160 runs). Each placebo is scaled to equal worst-20 exactly like a rule. The benchmark at a family's SD ratio is the kernel-weighted (bandwidth 0.04) mean and SD of the placebo equal-risk deltas; rank = Normal CDF of (real - placebo mean)/placebo SD. Frames other than A use the frame-A M curve (labelled benchmark).
* placebo M: SD ratio range 0.50-1.03; random skip equal-risk delta WF mean -9.8k; random exit equal-risk delta WF mean -22.6k; exit L6M mean -6.6k, exit HOLD mean -6.4k.
* placebo N: SD ratio range 0.46-0.98; random skip equal-risk delta WF mean -12.9k; random exit equal-risk delta WF mean -32.6k; exit L6M mean -17.6k, exit HOLD mean -16.1k.

| series | SD ratio | placebo L6M mean (SD) | rule L6M | rank | placebo HOLD | rule HOLD | rank | placebo WF | rule WF | rank |
|--|--|--|--|--|--|--|--|--|--|--|
| A|B|E|N | 0.76 | -7.9k (20.6k) | +90.3k | 1.00 | -6.7k (18.7k) | +80.5k | 1.00 | -21.7k (15.4k) | +19.6k | 1.00 |
| A|B|EPL|M | 0.71 | -11.4k (15.1k) | +81.6k | 1.00 | -10.2k (13.5k) | +76.4k | 1.00 | -20.7k (10.0k) | +1.2k | 0.99 |
| A|B|EL|N | 0.73 | -10.5k (20.4k) | +79.7k | 1.00 | -9.2k (18.2k) | +71.2k | 1.00 | -26.5k (15.6k) | -4.2k | 0.92 |
| A|B|EP|M | 0.76 | -8.1k (14.7k) | +79.3k | 1.00 | -7.0k (12.8k) | +74.5k | 1.00 | -18.4k (8.9k) | +18.9k | 1.00 |
| A|B|E|M | 0.79 | -6.5k (13.6k) | +79.3k | 1.00 | -5.7k (11.6k) | +69.0k | 1.00 | -17.0k (9.1k) | +17.4k | 1.00 |
| A|B|EL|M | 0.76 | -8.1k (14.7k) | +76.3k | 1.00 | -7.0k (12.8k) | +67.5k | 1.00 | -18.4k (8.9k) | +0.2k | 0.98 |
| H|L2SP|ALL_L6M_rank1|M | 0.87 | -3.3k (9.7k) | +56.4k | 1.00 | -3.2k (8.6k) | +48.7k | 1.00 | -9.8k (8.2k) | +4.8k | 0.96 |
| A|B|PL|M | 0.90 | -2.5k (8.5k) | +53.0k | 1.00 | -2.4k (7.9k) | +49.6k | 1.00 | -7.8k (6.7k) | +3.8k | 0.96 |
| A|H|EP|M | 0.87 | -3.0k (9.4k) | +43.9k | 1.00 | -3.0k (8.4k) | +39.9k | 1.00 | -9.3k (7.9k) | +15.1k | 1.00 |
| A|B|EP|N | 0.72 | -11.0k (20.2k) | +42.6k | 1.00 | -9.7k (18.0k) | +40.9k | 1.00 | -27.4k (15.7k) | -8.4k | 0.89 |
| A|B|EPL|N | 0.67 | -14.7k (19.8k) | +41.2k | 1.00 | -13.6k (18.2k) | +39.4k | 1.00 | -32.1k (18.0k) | -26.9k | 0.62 |
| A|H|P|M | 0.89 | -2.7k (8.8k) | +39.4k | 1.00 | -2.6k (8.0k) | +37.9k | 1.00 | -8.4k (7.3k) | +11.9k | 1.00 |
| A|H|PL|M | 0.85 | -3.8k (10.4k) | +38.8k | 1.00 | -3.7k (9.1k) | +31.1k | 1.00 | -10.9k (8.7k) | +19.5k | 1.00 |
| A|H|EPL|M | 0.84 | -4.2k (10.9k) | +38.7k | 1.00 | -4.0k (9.4k) | +28.9k | 1.00 | -11.8k (9.0k) | +21.7k | 1.00 |
| A|B|P|M | 0.92 | -2.6k (8.4k) | +34.3k | 1.00 | -2.4k (7.9k) | +33.1k | 1.00 | -7.1k (6.0k) | +11.7k | 1.00 |
| G|ADDUW|B1_PRE#1022 | 0.90 | -2.5k (8.6k) | +29.2k | 1.00 | -2.4k (7.9k) | +27.5k | 1.00 | -7.9k (6.8k) | +44.5k | 1.00 |
| A|B|L|N | 0.93 | -2.7k (10.5k) | +27.8k | 1.00 | -1.4k (9.7k) | +27.6k | 1.00 | -6.8k (9.0k) | -3.8k | 0.63 |
| A|H|EL|N | 0.97 | -2.7k (9.1k) | +26.3k | 1.00 | -1.4k (8.3k) | +18.5k | 0.99 | -5.9k (7.2k) | +23.5k | 1.00 |
| A|B|L|M | 0.96 | -3.8k (8.3k) | +25.9k | 1.00 | -3.3k (7.9k) | +23.3k | 1.00 | -5.8k (5.1k) | -3.3k | 0.68 |
| A|H|E|N | 0.99 | -2.9k (8.5k) | +22.6k | 1.00 | -1.5k (7.6k) | +22.6k | 1.00 | -5.8k (6.2k) | +12.3k | 1.00 |
| A|B|PL|N | 0.85 | -5.0k (13.7k) | +19.8k | 0.96 | -3.7k (13.0k) | +19.2k | 0.96 | -12.6k (10.9k) | -21.5k | 0.21 |
| C|D|D_L20s | 0.72 | -11.3k (15.1k) | +17.3k | 0.97 | -10.1k (13.5k) | +12.9k | 0.96 | -20.5k (10.0k) | -1.7k | 0.97 |
| A|H|L|N | 0.98 | -2.7k (8.9k) | +15.7k | 0.98 | -1.4k (8.0k) | +11.3k | 0.95 | -5.8k (6.8k) | +16.8k | 1.00 |
| C|A|A05 | 0.93 | -2.9k (8.4k) | +15.1k | 0.98 | -2.6k (7.9k) | +11.4k | 0.96 | -6.7k (5.7k) | +12.7k | 1.00 |
| A|H|EL|M | 0.98 | -4.1k (8.2k) | +15.0k | 0.99 | -3.6k (7.9k) | +7.9k | 0.93 | -5.3k (5.0k) | +19.2k | 1.00 |
| B|L2SL|HM_RANK | 0.96 | -3.5k (8.3k) | +14.8k | 0.99 | -3.1k (7.9k) | +12.1k | 0.97 | -6.0k (5.2k) | +5.5k | 0.99 |
| A|H|E|M | 1.04 | -4.4k (7.8k) | +13.4k | 0.99 | -3.7k (8.0k) | +11.6k | 0.97 | -4.3k (5.4k) | +9.0k | 0.99 |
| C|A|A04 | 0.87 | -3.0k (9.3k) | +13.3k | 0.96 | -3.0k (8.3k) | +7.5k | 0.90 | -9.2k (7.9k) | +22.7k | 1.00 |
| G|ADDUW|B2_L6Mrank#4 | 1.08 | -4.3k (7.1k) | +13.1k | 0.99 | -3.6k (7.5k) | +10.7k | 0.97 | -5.5k (5.8k) | +2.0k | 0.90 |
| G|ADDUW|B2_PRE#5 | 1.03 | -4.4k (7.9k) | +11.6k | 0.98 | -3.7k (8.0k) | +9.5k | 0.95 | -4.3k (5.2k) | +9.4k | 1.00 |
| H|L2SP|ALL_L6M_rank1|N | 0.83 | -5.5k (15.1k) | +11.5k | 0.87 | -4.3k (14.2k) | +7.2k | 0.79 | -14.2k (11.7k) | -26.2k | 0.15 |
| C|F|A06+HM5R+B02 | 0.81 | -5.7k (12.9k) | +11.4k | 0.91 | -5.1k (11.0k) | +6.4k | 0.85 | -15.6k (9.3k) | +26.5k | 1.00 |
| C|F|A06+B02 | 0.90 | -2.5k (8.6k) | +10.3k | 0.93 | -2.4k (7.9k) | +8.0k | 0.91 | -7.8k (6.8k) | +18.9k | 1.00 |
| C|F|A06+HM5R | 0.83 | -4.6k (11.5k) | +9.4k | 0.89 | -4.3k (9.8k) | +4.4k | 0.81 | -12.8k (9.2k) | +22.4k | 1.00 |
| C|F|C1 | 0.89 | -2.6k (8.6k) | +8.5k | 0.90 | -2.5k (7.9k) | +10.6k | 0.95 | -8.0k (6.9k) | +4.2k | 0.96 |
| B|L2SL|ALL_RANK | 1.01 | -4.4k (8.0k) | +8.4k | 0.95 | -3.8k (7.9k) | +6.9k | 0.91 | -4.4k (5.1k) | -2.8k | 0.62 |
| E|SL|PB|NY|P1+N3 | 0.96 | -3.6k (8.3k) | +8.1k | 0.92 | -3.1k (7.9k) | +7.2k | 0.91 | -6.0k (5.2k) | +3.1k | 0.96 |
| C|D|D_L30s | 0.85 | -3.8k (10.4k) | +8.1k | 0.87 | -3.7k (9.1k) | +5.1k | 0.83 | -10.9k (8.7k) | -3.8k | 0.79 |
| C|F|HM5R+B02 | 0.86 | -3.6k (10.2k) | +8.0k | 0.87 | -3.5k (8.9k) | +5.6k | 0.85 | -10.6k (8.6k) | +11.3k | 0.99 |
| E|SL|PB|NY|P1 | 0.96 | -3.6k (8.3k) | +7.8k | 0.92 | -3.2k (7.9k) | +6.7k | 0.90 | -5.9k (5.2k) | +3.0k | 0.96 |
| C|A|A08 | 0.98 | -4.2k (8.1k) | +7.7k | 0.93 | -3.6k (7.9k) | +6.1k | 0.89 | -5.1k (5.0k) | +0.0k | 0.85 |
| F|CW|SM | 0.99 | -4.2k (8.1k) | +7.5k | 0.93 | -3.7k (7.9k) | +5.6k | 0.88 | -5.1k (5.0k) | +0.4k | 0.86 |
| E|SL|PB|NY|P1+L2 | 0.96 | -3.6k (8.3k) | +7.2k | 0.90 | -3.1k (7.9k) | +6.4k | 0.89 | -6.0k (5.2k) | +3.1k | 0.96 |
| C|A|A06 | 0.93 | -2.8k (8.4k) | +6.6k | 0.87 | -2.5k (7.9k) | +3.4k | 0.77 | -6.9k (5.8k) | +14.4k | 1.00 |
| E|SL|PB|NY|G1k70 | 0.97 | -3.8k (8.3k) | +6.4k | 0.89 | -3.4k (7.9k) | +5.5k | 0.87 | -5.7k (5.1k) | +2.7k | 0.95 |
| C|A|A03 | 1.00 | -4.4k (8.0k) | +6.3k | 0.91 | -3.8k (7.9k) | +5.4k | 0.88 | -4.6k (5.0k) | +3.7k | 0.95 |
| H|L2SP|ALL_PRE_selected|M | 0.89 | -2.6k (8.7k) | +6.1k | 0.84 | -2.5k (7.9k) | +5.1k | 0.83 | -8.0k (7.0k) | +4.3k | 0.96 |
| E|SL|PB|NY|P1+L1 | 0.95 | -3.3k (8.4k) | +6.1k | 0.87 | -2.9k (7.9k) | +5.3k | 0.85 | -6.3k (5.4k) | +1.1k | 0.92 |
| E|SL|PB|NY|P1+L1.5 | 0.96 | -3.6k (8.3k) | +5.9k | 0.87 | -3.2k (7.9k) | +4.9k | 0.85 | -5.9k (5.2k) | +2.1k | 0.94 |
| C|F|HM5R | 0.89 | -2.6k (8.8k) | +5.6k | 0.83 | -2.6k (8.0k) | +3.2k | 0.77 | -8.3k (7.2k) | +7.9k | 0.99 |
| C|F|HM5M | 0.92 | -2.7k (8.4k) | +5.5k | 0.84 | -2.4k (7.9k) | +3.6k | 0.78 | -7.0k (5.9k) | +5.6k | 0.98 |
| C|D|D_B4s | 0.91 | -2.6k (8.4k) | +5.5k | 0.83 | -2.4k (7.9k) | +3.5k | 0.77 | -7.3k (6.2k) | +1.5k | 0.92 |
| C|D|D_L40s | 0.97 | -3.8k (8.3k) | +5.2k | 0.86 | -3.4k (7.9k) | +3.6k | 0.81 | -5.7k (5.1k) | +4.7k | 0.98 |
| C|D|D_B2s | 0.68 | -11.1k (14.8k) | +5.0k | 0.86 | -10.1k (13.1k) | +3.5k | 0.85 | -23.3k (11.2k) | -8.5k | 0.91 |
| E|SL|PB|NY|P1.5+N2 | 0.97 | -3.9k (8.3k) | +4.9k | 0.86 | -3.4k (7.9k) | +4.5k | 0.84 | -5.7k (5.1k) | +1.5k | 0.92 |
| E|SL|PB|London|P1.5+N1 | 0.97 | -4.0k (8.2k) | +4.9k | 0.86 | -3.5k (7.9k) | +4.3k | 0.84 | -5.5k (5.1k) | +5.9k | 0.99 |
| E|SL|PB|NY|G1k50 | 0.98 | -4.2k (8.1k) | +4.8k | 0.87 | -3.6k (7.9k) | +4.1k | 0.84 | -5.1k (5.0k) | +3.1k | 0.95 |
| E|SL|PB|NY|P1+N1 | 0.95 | -3.4k (8.3k) | +4.3k | 0.82 | -3.0k (7.9k) | +3.6k | 0.80 | -6.1k (5.3k) | +0.6k | 0.90 |
| E|SL|PB|London|P3+N1 | 0.97 | -4.0k (8.2k) | +4.1k | 0.84 | -3.5k (7.9k) | +3.9k | 0.83 | -5.4k (5.1k) | +5.3k | 0.98 |
| C|F|B02 | 0.97 | -3.9k (8.3k) | +3.7k | 0.82 | -3.4k (7.9k) | +4.3k | 0.84 | -5.7k (5.1k) | +3.6k | 0.96 |
| E|SL|PB|London|P2+N1 | 0.97 | -4.0k (8.2k) | +3.6k | 0.82 | -3.4k (7.9k) | +3.5k | 0.81 | -5.5k (5.1k) | +5.7k | 0.99 |
| E|SL|PS|London|P1+N3 | 0.98 | -4.2k (8.2k) | +3.5k | 0.83 | -3.6k (7.9k) | +3.2k | 0.81 | -5.2k (5.0k) | +0.5k | 0.87 |
| E|SL|WT|NY|P2+N1 | 0.98 | -4.2k (8.2k) | +3.3k | 0.82 | -3.6k (7.9k) | +3.0k | 0.80 | -5.2k (5.0k) | +1.5k | 0.91 |
| E|SL|PS|London|P1+N2 | 0.98 | -4.2k (8.2k) | +3.0k | 0.81 | -3.6k (7.9k) | +2.8k | 0.79 | -5.2k (5.0k) | +1.2k | 0.90 |
| E|SL|PB|NY|P1.5 | 0.97 | -4.0k (8.2k) | +2.9k | 0.80 | -3.5k (7.9k) | +2.4k | 0.77 | -5.5k (5.1k) | +0.1k | 0.87 |
| E|SL|PS|NY|P1.5+L1 | 0.98 | -4.2k (8.2k) | +2.8k | 0.80 | -3.6k (7.9k) | +2.2k | 0.77 | -5.2k (5.0k) | +0.7k | 0.88 |
| E|SL|WT|NY|P2 | 0.99 | -4.3k (8.1k) | +2.6k | 0.80 | -3.7k (7.9k) | +2.4k | 0.78 | -4.9k (5.0k) | +1.5k | 0.90 |
| B|L2SL|SM_RANK | 0.99 | -4.2k (8.1k) | +2.6k | 0.80 | -3.7k (7.9k) | +2.6k | 0.79 | -5.1k (5.0k) | -3.2k | 0.64 |
| E|SL|PB|NY|P1.5+L2 | 0.97 | -3.9k (8.2k) | +2.5k | 0.78 | -3.4k (7.9k) | +2.2k | 0.76 | -5.6k (5.1k) | +0.1k | 0.87 |
| E|SL|HM|NY|P1.5+L1.5 | 0.98 | -4.1k (8.2k) | +2.4k | 0.79 | -3.6k (7.9k) | +2.6k | 0.78 | -5.3k (5.0k) | +1.0k | 0.89 |
| F|CW|WT | 0.97 | -4.0k (8.2k) | +2.3k | 0.78 | -3.5k (7.9k) | -0.7k | 0.64 | -5.4k (5.1k) | -0.3k | 0.85 |
| E|SL|PS|NY|P2+N1 | 0.99 | -4.3k (8.1k) | +2.3k | 0.79 | -3.7k (7.9k) | +1.7k | 0.75 | -5.0k (5.0k) | +0.4k | 0.86 |
| E|SL|PS|NY|P2+L1 | 0.99 | -4.3k (8.1k) | +2.1k | 0.78 | -3.7k (7.9k) | +1.6k | 0.75 | -5.0k (5.0k) | +0.8k | 0.88 |
| C|A|A09 | 0.97 | -3.8k (8.3k) | +2.0k | 0.76 | -3.3k (7.9k) | +1.0k | 0.71 | -5.7k (5.1k) | -1.2k | 0.81 |
| E|SL|PB|NY|P2 | 0.98 | -4.2k (8.2k) | +2.0k | 0.77 | -3.6k (7.9k) | +1.5k | 0.74 | -5.2k (5.0k) | +0.1k | 0.86 |
| B|L2SL|COMBO_RANK | 0.90 | -2.5k (8.5k) | +1.6k | 0.69 | -2.4k (7.9k) | +2.7k | 0.74 | -7.7k (6.6k) | -14.5k | 0.15 |
| E|SL|PB|NY|G2k70 | 0.99 | -4.2k (8.1k) | +1.6k | 0.76 | -3.7k (7.9k) | +1.1k | 0.73 | -5.1k (5.0k) | +0.1k | 0.85 |
| E|SL|PB|NY|P2+L2 | 0.98 | -4.1k (8.2k) | +1.5k | 0.75 | -3.6k (7.9k) | +1.2k | 0.73 | -5.3k (5.0k) | +0.2k | 0.86 |
| A|H|L|M | 0.98 | -4.1k (8.2k) | +1.4k | 0.75 | -3.5k (7.9k) | -4.0k | 0.48 | -5.4k (5.0k) | +7.0k | 0.99 |
| C|D|D_L30t | 0.90 | -2.5k (8.5k) | +1.4k | 0.68 | -2.4k (7.9k) | +0.5k | 0.64 | -7.7k (6.6k) | -2.1k | 0.80 |
| E|SL|PS|NY|P3+N1 | 0.99 | -4.3k (8.1k) | +1.2k | 0.75 | -3.7k (7.9k) | +0.9k | 0.72 | -4.9k (5.0k) | +0.6k | 0.86 |
| E|SL|KB|Asia|P3+L2 | 1.00 | -4.4k (8.1k) | +1.0k | 0.75 | -3.8k (7.9k) | +0.8k | 0.72 | -4.7k (5.0k) | +1.1k | 0.88 |
| E|SL|PS|NY|G2k70 | 1.00 | -4.4k (8.0k) | +0.9k | 0.75 | -3.8k (7.9k) | +0.8k | 0.72 | -4.7k (5.0k) | +0.3k | 0.84 |
| E|SL|KB|Asia|P3 | 1.00 | -4.4k (8.1k) | +0.8k | 0.74 | -3.7k (7.9k) | +0.7k | 0.72 | -4.7k (5.0k) | +0.6k | 0.86 |
| E|SL|WT|Asia|P1+L1 | 0.99 | -4.3k (8.1k) | +0.5k | 0.72 | -3.7k (7.9k) | +0.7k | 0.72 | -4.8k (5.0k) | +1.7k | 0.90 |
| B|L2SL|HM_PRE | 0.96 | -3.7k (8.3k) | +0.4k | 0.69 | -3.3k (7.9k) | -1.2k | 0.60 | -5.8k (5.1k) | +3.4k | 0.96 |
| E|SL|HM|NY|P1+L1.5 | 0.98 | -4.1k (8.2k) | +0.4k | 0.71 | -3.6k (7.9k) | +1.6k | 0.75 | -5.3k (5.0k) | +1.0k | 0.89 |
| E|SL|PB|London|P3+L1.5 | 0.98 | -4.2k (8.2k) | +0.4k | 0.71 | -3.6k (7.9k) | +0.3k | 0.69 | -5.2k (5.0k) | +1.8k | 0.92 |
| E|SL|PS|NY|P3+L2 | 1.00 | -4.4k (8.1k) | +0.3k | 0.72 | -3.7k (7.9k) | +0.2k | 0.69 | -4.8k (5.0k) | +0.1k | 0.83 |
| C|D|D_B3s | 0.84 | -4.3k (11.2k) | +0.2k | 0.66 | -4.1k (9.6k) | -1.4k | 0.61 | -12.2k (9.1k) | -5.6k | 0.77 |
| C|A|A01 | 1.00 | -4.4k (8.0k) | +0.1k | 0.71 | -3.8k (7.9k) | +0.9k | 0.72 | -4.6k (5.0k) | +0.0k | 0.82 |
| E|SL|PS|NY|P3+L1.5 | 0.99 | -4.3k (8.1k) | -0.1k | 0.70 | -3.7k (7.9k) | -0.3k | 0.67 | -4.9k (5.0k) | +0.3k | 0.85 |
| E|SL|PS|NY|L2 | 1.00 | -4.4k (8.1k) | -0.1k | 0.70 | -3.7k (7.9k) | -0.1k | 0.68 | -4.8k (5.0k) | -0.3k | 0.82 |
| A|B|P|N | 0.88 | -4.1k (12.6k) | -0.2k | 0.62 | -2.8k (11.9k) | +1.6k | 0.64 | -10.5k (10.5k) | -14.0k | 0.37 |
| B|EXP2|B_U3 | 1.00 | -4.4k (8.0k) | -0.3k | 0.70 | -3.8k (7.9k) | -0.5k | 0.66 | -4.6k (5.1k) | +3.7k | 0.95 |
| C|A|A07 | 0.97 | -4.0k (8.2k) | -0.3k | 0.67 | -3.5k (7.9k) | -1.7k | 0.59 | -5.5k (5.1k) | -2.8k | 0.70 |
| C|D|D_B3e | 0.86 | -3.4k (9.8k) | -0.5k | 0.62 | -3.3k (8.6k) | -1.9k | 0.56 | -10.0k (8.3k) | -7.8k | 0.60 |
| E|SL|ST|Asia|P1.5+N3 | 1.00 | -4.4k (8.0k) | -0.6k | 0.68 | -3.8k (7.9k) | -0.5k | 0.66 | -4.6k (5.0k) | +2.2k | 0.91 |
| B|EXP2|P | 1.00 | -4.4k (8.1k) | -0.7k | 0.68 | -3.7k (7.9k) | -5.6k | 0.41 | -4.8k (5.0k) | -6.3k | 0.38 |
| B|L2SL|SM_PRE | 1.00 | -4.4k (8.1k) | -1.2k | 0.65 | -3.7k (7.9k) | -1.3k | 0.62 | -4.8k (5.0k) | -2.1k | 0.71 |
| E|SL|PS|London|N2 | 1.00 | -4.4k (8.0k) | -1.2k | 0.65 | -3.8k (7.9k) | -0.9k | 0.64 | -4.7k (5.0k) | +0.3k | 0.84 |
| A|H|EP|N | 0.83 | -5.6k (15.8k) | -1.5k | 0.60 | -4.4k (14.8k) | -1.5k | 0.58 | -14.8k (12.1k) | -18.8k | 0.37 |
| E|SL|ST|NY|N2 | 0.99 | -4.3k (8.1k) | -1.7k | 0.62 | -3.7k (7.9k) | -1.4k | 0.61 | -4.9k (5.0k) | +0.6k | 0.86 |
| E|SL|ST|NY|P3+N2 | 0.98 | -4.1k (8.2k) | -2.6k | 0.57 | -3.6k (7.9k) | -2.5k | 0.55 | -5.3k (5.0k) | +0.3k | 0.87 |
| B|EXP2|B_U3_P | 1.00 | -4.4k (8.1k) | -2.7k | 0.59 | -3.8k (7.9k) | -7.9k | 0.30 | -4.7k (5.0k) | -4.7k | 0.50 |
| E|SL|ST|Asia|P1.5+L2 | 1.00 | -4.4k (8.0k) | -2.9k | 0.58 | -3.8k (7.9k) | -2.6k | 0.56 | -4.6k (5.1k) | +1.2k | 0.87 |
| B|L2SL|KB_RANK | 1.01 | -4.4k (8.0k) | -2.9k | 0.57 | -3.8k (7.9k) | -2.7k | 0.55 | -4.4k (5.1k) | -4.9k | 0.46 |
| B|L2SL|ST_RANK | 0.98 | -4.2k (8.2k) | -3.1k | 0.55 | -3.6k (7.9k) | -1.5k | 0.60 | -5.2k (5.0k) | -3.9k | 0.60 |
| B|L2SL|KB_PRE | 1.02 | -4.4k (7.9k) | -3.2k | 0.56 | -3.7k (7.9k) | -2.6k | 0.56 | -4.3k (5.2k) | -4.5k | 0.49 |
| A|H|P|N | 0.83 | -5.5k (15.2k) | -3.5k | 0.55 | -4.3k (14.2k) | -1.8k | 0.57 | -14.2k (11.7k) | -21.0k | 0.28 |
| F|CW|HM | 0.96 | -3.6k (8.3k) | -3.5k | 0.50 | -3.1k (7.9k) | -5.3k | 0.39 | -6.0k (5.2k) | +1.6k | 0.93 |
| B|L2SL|WT_RANK | 0.99 | -4.2k (8.1k) | -3.8k | 0.52 | -3.7k (7.9k) | -3.2k | 0.52 | -5.1k (5.0k) | -3.0k | 0.66 |
| C|D|D_B3h | 0.88 | -2.8k (9.0k) | -4.0k | 0.45 | -2.8k (8.1k) | -6.6k | 0.32 | -8.7k (7.5k) | -1.8k | 0.82 |
| B|L2SL|WT_PRE | 1.00 | -4.4k (8.1k) | -4.5k | 0.50 | -3.7k (7.9k) | -4.4k | 0.47 | -4.7k (5.0k) | -4.5k | 0.52 |
| B|L2SL|PE_PRE | 0.99 | -4.3k (8.1k) | -4.6k | 0.48 | -3.7k (7.9k) | -3.6k | 0.50 | -5.0k (5.0k) | +0.5k | 0.86 |
| B|L2SL|PE_RANK | 0.97 | -3.9k (8.2k) | -4.8k | 0.46 | -3.4k (7.9k) | -3.6k | 0.49 | -5.6k (5.1k) | -3.6k | 0.65 |
| B|L2SL|ST_PRE | 0.98 | -4.1k (8.2k) | -5.5k | 0.43 | -3.5k (7.9k) | -4.5k | 0.45 | -5.4k (5.0k) | -1.6k | 0.77 |
| H|L2SP|ALL_PRE_selected|N | 0.90 | -3.3k (11.6k) | -5.5k | 0.42 | -1.9k (11.0k) | -5.9k | 0.36 | -8.6k (10.1k) | -5.3k | 0.63 |
| A|H|EPL|N | 0.79 | -6.2k (18.9k) | -5.9k | 0.51 | -5.0k (17.5k) | -11.4k | 0.36 | -17.7k (14.3k) | -12.3k | 0.65 |
| E|SL|ST|Asia|P1.5+N2 | 1.00 | -4.4k (8.1k) | -6.7k | 0.39 | -3.8k (7.9k) | -6.0k | 0.39 | -4.7k (5.0k) | +1.4k | 0.89 |
| C|A|A02 | 0.89 | -2.6k (8.7k) | -7.0k | 0.31 | -2.5k (8.0k) | -5.1k | 0.38 | -8.2k (7.1k) | +4.3k | 0.96 |
| F|CW|ST | 0.94 | -3.0k (8.4k) | -7.1k | 0.31 | -2.7k (7.9k) | -6.6k | 0.31 | -6.6k (5.6k) | +0.1k | 0.89 |
| A|H|PL|N | 0.80 | -6.0k (18.0k) | -7.5k | 0.46 | -4.7k (16.7k) | -10.9k | 0.36 | -16.6k (13.6k) | -15.6k | 0.53 |
| B|EXP2|B_FROZEN_P | 0.83 | -4.7k (11.6k) | -9.4k | 0.34 | -4.4k (10.0k) | -3.1k | 0.55 | -13.1k (9.3k) | -6.5k | 0.76 |
| F|CW|PE | 0.93 | -2.8k (8.4k) | -11.3k | 0.15 | -2.5k (7.9k) | -8.8k | 0.21 | -6.9k (5.8k) | -0.0k | 0.88 |
| D|D6L_alone | 0.77 | -7.5k (14.4k) | -12.0k | 0.38 | -6.5k (12.5k) | -8.5k | 0.44 | -18.1k (8.9k) | -24.0k | 0.25 |
| B|L2SL|ALL_PRE | 0.92 | -2.7k (8.4k) | -15.8k | 0.06 | -2.4k (7.9k) | -15.2k | 0.05 | -7.0k (5.9k) | -9.7k | 0.33 |
| D|PROFIT_alone | 0.95 | -3.4k (8.3k) | -16.3k | 0.06 | -3.0k (7.9k) | -16.3k | 0.05 | -6.2k (5.3k) | -11.9k | 0.14 |
| B|L2SL|COMBO_PRE | 0.93 | -2.9k (8.4k) | -17.8k | 0.04 | -2.6k (7.9k) | -17.1k | 0.03 | -6.7k (5.7k) | -8.4k | 0.39 |
| B|EXP2|B_FROZEN | 0.90 | -2.6k (8.6k) | -19.6k | 0.02 | -2.5k (7.9k) | -14.5k | 0.06 | -8.0k (6.9k) | -22.2k | 0.02 |
| B|EXP2|B_U3_L | 0.94 | -3.0k (8.4k) | -23.6k | 0.01 | -2.7k (7.9k) | -19.7k | 0.02 | -6.6k (5.6k) | -8.5k | 0.37 |
| B|EXP2|L | 0.92 | -2.6k (8.4k) | -24.0k | 0.01 | -2.4k (7.9k) | -19.5k | 0.01 | -7.2k (6.1k) | -11.8k | 0.23 |
| B|EXP2|B_U1_P | 0.92 | -2.6k (8.4k) | -25.9k | 0.00 | -2.4k (7.9k) | -22.2k | 0.01 | -7.1k (6.1k) | -26.8k | 0.00 |
| F|CW|KB | 0.98 | -4.1k (8.2k) | -27.0k | 0.00 | -3.5k (7.9k) | -26.1k | 0.00 | -5.3k (5.0k) | -12.0k | 0.09 |
| B|EXP2|B_U1 | 0.95 | -3.5k (8.3k) | -29.1k | 0.00 | -3.1k (7.9k) | -27.6k | 0.00 | -6.1k (5.2k) | -33.4k | 0.00 |
| B|EXP2|B_U3_P_L | 0.91 | -2.5k (8.4k) | -29.2k | 0.00 | -2.4k (7.9k) | -30.7k | 0.00 | -7.5k (6.4k) | -16.2k | 0.09 |
| B|EXP2|P_L | 0.89 | -2.7k (8.9k) | -29.4k | 0.00 | -2.6k (8.1k) | -30.3k | 0.00 | -8.5k (7.3k) | -18.0k | 0.10 |
| D|JOINT3 | 0.65 | -9.5k (15.3k) | -30.9k | 0.08 | -8.5k (13.3k) | -25.8k | 0.10 | -24.8k (12.0k) | -39.6k | 0.11 |
| D|JOINT10 | 0.65 | -9.5k (15.3k) | -31.2k | 0.08 | -8.5k (13.3k) | -26.1k | 0.09 | -24.9k (12.1k) | -39.8k | 0.11 |
| D|JOINT20 | 0.64 | -9.2k (15.4k) | -32.1k | 0.07 | -8.1k (13.3k) | -27.7k | 0.07 | -25.2k (12.2k) | -38.3k | 0.14 |
| D|LOSS20_alone | 0.83 | -4.6k (11.5k) | -32.8k | 0.01 | -4.3k (9.9k) | -28.1k | 0.01 | -12.8k (9.2k) | -33.6k | 0.01 |
| D|LOSS10_alone | 0.84 | -4.5k (11.3k) | -32.9k | 0.01 | -4.2k (9.7k) | -28.5k | 0.01 | -12.5k (9.2k) | -33.0k | 0.01 |
| B|EXP2|B_U2_P | 0.92 | -2.6k (8.4k) | -33.4k | 0.00 | -2.4k (7.9k) | -28.0k | 0.00 | -7.2k (6.1k) | -30.3k | 0.00 |
| D|LOSS3_alone | 0.84 | -4.4k (11.3k) | -34.0k | 0.00 | -4.2k (9.7k) | -29.3k | 0.00 | -12.4k (9.2k) | -33.9k | 0.01 |
| B|EXP2|B_U2 | 0.92 | -2.7k (8.4k) | -34.0k | 0.00 | -2.4k (7.9k) | -29.6k | 0.00 | -7.0k (5.9k) | -29.7k | 0.00 |
| F|CW|ALL6 | 0.81 | -5.5k (12.6k) | -47.2k | 0.00 | -5.0k (10.8k) | -50.2k | 0.00 | -15.1k (9.4k) | -14.2k | 0.54 |
| C|A|A10 | 0.88 | -2.9k (9.1k) | -51.7k | 0.00 | -2.8k (8.2k) | -40.7k | 0.00 | -8.9k (7.6k) | -46.6k | 0.00 |
| B|EXP2|B_U2_L | 0.89 | -2.6k (8.6k) | -55.0k | 0.00 | -2.5k (7.9k) | -48.1k | 0.00 | -8.0k (6.9k) | -46.6k | 0.00 |
| B|EXP2|B_U2_P_L | 0.92 | -2.6k (8.4k) | -55.7k | 0.00 | -2.4k (7.9k) | -49.9k | 0.00 | -7.2k (6.1k) | -45.8k | 0.00 |
| B|EXP2|B_U1_L | 0.89 | -2.6k (8.7k) | -58.0k | 0.00 | -2.5k (8.0k) | -50.8k | 0.00 | -8.2k (7.1k) | -50.8k | 0.00 |
| B|EXP2|B_FROZEN_P_L | 0.84 | -4.5k (11.4k) | -61.7k | 0.00 | -4.3k (9.8k) | -53.3k | 0.00 | -12.7k (9.2k) | -51.5k | 0.00 |
| B|EXP2|B_FROZEN_L | 0.85 | -3.7k (10.3k) | -62.7k | 0.00 | -3.6k (9.0k) | -53.3k | 0.00 | -10.7k (8.7k) | -56.8k | 0.00 |
| B|EXP2|B_U1_P_L | 0.89 | -2.7k (8.8k) | -63.3k | 0.00 | -2.6k (8.0k) | -55.0k | 0.00 | -8.4k (7.2k) | -52.5k | 0.00 |

## 8. Gates, tiers before/after the upstream gate, M versus N basis
G1 equal-risk delta >= 0 in Y26, L6M and HOLD. G2 >= 0 in PRE and X'. G3 same sign for the maxDD-matched and SD-matched factor in L6M and HOLD. G4 bootstrap CI of WF delta lower bound > 0. G5 placebo rank >= 0.95 (L6M, HOLD, WF). G6 N-basis counterpart (frame A, H): L6M and HOLD >= 0 (n/a = untested = fail for PASS). G7 not ranked on looked data. G8 fixed-$ locks keep the sign in L6M and HOLD (frame A only). G9 RC single-step adjusted p <= 0.05 over the 153 families. **G10 (post-hoc amendment A1, disclosed, tightening only):** the upstream cell-search RC p of the source report must be <= 0.05 (E-based cells: L2SE stack RC L6M p 0.11; STK_F best-of-F 1.000; EXP2 RC 0.76; L2SP 0.72; DIPENTRY 0.85; CUTWAIT .26-.99; ADDUW fail; session locks 798/798 fail). PASS = G1-G9; CANDIDATE = G1,G2,G3,G6 (where available),G7 pass and only G4,G5,G6(n/a),G8(n/a),G9 fail; CANDIDATE-RECENT = G1 passes, otherwise; DEAD = G1 fails.
| series | tier prereg | tier after G10 | G1 | G2 | G3 | G4 | G5 | G6 | G7 | G8 | G9 | G10 | RC adj p | upstream |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| A|B|E|N | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | Y | Y | N | Y | N | N | 0.860 | L2SE stack RC L6M p 0.11 (HOLD .18, PRE .77) |
| A|B|EPL|M | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | Y | Y | N | N | N | N | 1.000 | L2SE stack RC L6M p 0.11 (HOLD .18, PRE .77) |
| A|B|EL|N | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | Y | N | N | N | N | 1.000 | L2SE stack RC L6M p 0.11 (HOLD .18, PRE .77) |
| A|B|EP|M | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | Y | Y | N | N | N | N | 0.958 | L2SE stack RC L6M p 0.11 (HOLD .18, PRE .77) |
| A|B|E|M | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | Y | Y | N | Y | N | N | 0.896 | L2SE stack RC L6M p 0.11 (HOLD .18, PRE .77) |
| A|B|EL|M | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | Y | Y | N | Y | N | N | 1.000 | L2SE stack RC L6M p 0.11 (HOLD .18, PRE .77) |
| H|L2SP|ALL_L6M_rank1|M | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | Y | Y | N | n/a | N | N | 1.000 | L2SP pooled White RC (PRE) p 0.72 |
| A|B|PL|M | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | Y | Y | N | Y | N | Y | 1.000 | plain 70% take is a pre-specified reference (not searched); loss cell L2SL RC 0.018 |
| A|H|EP|M | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | Y | Y | N | Y | N | Y | Y | N | N | 0.887 | L2SE stack RC L6M p 0.11 (HOLD .18, PRE .77) |
| A|B|EP|N | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | Y | N | Y | N | N | 1.000 | L2SE stack RC L6M p 0.11 (HOLD .18, PRE .77) |
| A|B|EPL|N | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | Y | N | Y | N | N | 1.000 | L2SE stack RC L6M p 0.11 (HOLD .18, PRE .77) |
| A|H|P|M | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | Y | Y | N | Y | N | Y | Y | N | Y | 0.978 | plain 70% take is a pre-specified reference (not searched) |
| A|H|PL|M | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | Y | Y | Y | Y | N | Y | Y | N | Y | 0.626 | plain 70% take is a pre-specified reference (not searched); loss cell L2SL RC 0.018 |
| A|H|EPL|M | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | Y | Y | Y | Y | N | Y | Y | N | N | 0.419 | L2SE stack RC L6M p 0.11 (HOLD .18, PRE .77) |
| A|B|P|M | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | Y | Y | N | Y | N | N | Y | N | Y | 0.915 | plain 70% take is a pre-specified reference (not searched) |
| G|ADDUW|B1_PRE#1022 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | Y | Y | n/a | Y | n/a | Y | N | 0.002 | ADDUW G9 best-of-F fail on every basis |
| A|B|L|N | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | Y | N | Y | N | Y | 1.000 | L2SL pooled RC L6M p 0.018 (PRE .0015) |
| A|H|EL|N | PASS | CANDIDATE | Y | Y | Y | Y | Y | Y | Y | Y | Y | N | 0.025 | L2SE stack RC L6M p 0.11 (HOLD .18, PRE .77) |
| A|B|L|M | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | Y | N | Y | N | Y | 1.000 | L2SL pooled RC L6M p 0.018 (PRE .0015) |
| A|H|E|N | PASS | CANDIDATE | Y | Y | Y | Y | Y | Y | Y | Y | Y | N | 0.016 | L2SE stack RC L6M p 0.11 (HOLD .18, PRE .77) |
| A|B|PL|N | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | Y | N | Y | N | Y | 1.000 | plain 70% take is a pre-specified reference (not searched); loss cell L2SL RC 0.018 |
| C|D|D_L20s | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | N | N | Y | n/a | Y | n/a | N | N | 1.000 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| A|H|L|N | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | Y | N | N | N | Y | Y | N | N | Y | 0.239 | L2SL pooled RC L6M p 0.018 (PRE .0015) |
| C|A|A05 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | Y | n/a | Y | n/a | N | N | 0.256 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| A|H|EL|M | CANDIDATE | CANDIDATE | Y | Y | Y | Y | N | Y | Y | Y | N | N | 0.069 | L2SE stack RC L6M p 0.11 (HOLD .18, PRE .77) |
| B|L2SL|HM_RANK | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | Y | Y | N | Y | n/a | N | n/a | N | Y | 0.330 | L2SL pooled RC L6M p 0.018 |
| A|H|E|M | CANDIDATE | CANDIDATE | Y | Y | Y | Y | Y | Y | Y | Y | N | N | 0.201 | L2SE stack RC L6M p 0.11 (HOLD .18, PRE .77) |
| C|A|A04 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | N | Y | N | n/a | Y | n/a | Y | N | 0.021 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| G|ADDUW|B2_L6Mrank#4 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | N | n/a | N | N | 1.000 | ADDUW G9 best-of-F fail on every basis |
| G|ADDUW|B2_PRE#5 | CANDIDATE | CANDIDATE | Y | Y | Y | N | Y | n/a | Y | n/a | N | N | 0.655 | ADDUW G9 best-of-F fail on every basis |
| H|L2SP|ALL_L6M_rank1|N | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | N | N | N | Y | N | n/a | N | N | 1.000 | L2SP pooled White RC (PRE) p 0.72 |
| C|F|A06+HM5R+B02 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | N | Y | N | n/a | Y | n/a | N | N | 0.070 | STK_F best-of-F p 1.000 |
| C|F|A06+B02 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | N | Y | N | n/a | Y | n/a | Y | N | 0.003 | STK_F best-of-F p 1.000 |
| C|F|A06+HM5R | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | N | N | N | n/a | Y | n/a | N | N | 0.196 | STK_F best-of-F p 1.000 |
| C|F|C1 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 0.999 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| B|L2SL|ALL_RANK | DEAD | DEAD | N | N | Y | N | N | n/a | N | n/a | N | Y | 1.000 | L2SL pooled RC L6M p 0.018 |
| E|SL|PB|NY|P1+N3 | CANDIDATE | CANDIDATE | Y | Y | Y | N | N | n/a | Y | n/a | N | N | 0.654 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| C|D|D_L30s | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| C|F|HM5R+B02 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | Y | N | N | N | n/a | Y | n/a | N | N | 0.874 | STK_F best-of-F p 1.000 |
| E|SL|PB|NY|P1 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 0.713 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| C|A|A08 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 1.000 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| F|CW|SM | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 1.000 | CUTWAIT RC p 0.26-0.99 per book |
| E|SL|PB|NY|P1+L2 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 0.679 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| C|A|A06 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | N | Y | N | n/a | Y | n/a | Y | N | 0.006 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| E|SL|PB|NY|G1k70 | CANDIDATE | CANDIDATE | Y | Y | Y | N | N | n/a | Y | n/a | N | N | 0.772 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| C|A|A03 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | Y | N | n/a | Y | n/a | Y | N | 0.021 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| H|L2SP|ALL_PRE_selected|M | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | Y | Y | N | N | N | Y | n/a | N | N | 1.000 | L2SP pooled White RC (PRE) p 0.72 |
| E|SL|PB|NY|P1+L1 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|PB|NY|P1+L1.5 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 0.991 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| C|F|HM5R | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | Y | N | N | N | n/a | Y | n/a | N | N | 0.996 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| C|F|HM5M | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | Y | N | N | N | n/a | Y | n/a | N | N | 0.790 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| C|D|D_B4s | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 1.000 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| C|D|D_L40s | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | Y | N | n/a | Y | n/a | N | N | 0.265 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| C|D|D_B2s | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| E|SL|PB|NY|P1.5+N2 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 0.999 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|PB|London|P1.5+N1 | CANDIDATE | CANDIDATE | Y | Y | Y | N | N | n/a | Y | n/a | N | N | 0.170 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|PB|NY|G1k50 | CANDIDATE | CANDIDATE | Y | Y | Y | N | N | n/a | Y | n/a | N | N | 0.355 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|PB|NY|P1+N1 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|PB|London|P3+N1 | CANDIDATE | CANDIDATE | Y | Y | Y | N | N | n/a | Y | n/a | N | N | 0.094 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| C|F|B02 | CANDIDATE | CANDIDATE | Y | Y | Y | N | N | n/a | Y | n/a | N | N | 0.795 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| E|SL|PB|London|P2+N1 | CANDIDATE | CANDIDATE | Y | Y | Y | Y | N | n/a | Y | n/a | N | N | 0.065 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|PS|London|P1+N3 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|WT|NY|P2+N1 | CANDIDATE | CANDIDATE | Y | Y | Y | N | N | n/a | Y | n/a | N | N | 0.999 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|PS|London|P1+N2 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|PB|NY|P1.5 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|PS|NY|P1.5+L1 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|WT|NY|P2 | CANDIDATE | CANDIDATE | Y | Y | Y | Y | N | n/a | Y | n/a | N | N | 0.308 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| B|L2SL|SM_RANK | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | N | n/a | N | Y | 1.000 | L2SL pooled RC L6M p 0.018 |
| E|SL|PB|NY|P1.5+L2 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|HM|NY|P1.5+L1.5 | CANDIDATE | CANDIDATE | Y | Y | Y | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| F|CW|WT | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | CUTWAIT RC p 0.26-0.99 per book |
| E|SL|PS|NY|P2+N1 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|PS|NY|P2+L1 | CANDIDATE | CANDIDATE | Y | Y | Y | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| C|A|A09 | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| E|SL|PB|NY|P2 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| B|L2SL|COMBO_RANK | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | N | n/a | N | Y | 1.000 | L2SL pooled RC L6M p 0.018 |
| E|SL|PB|NY|G2k70 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|PB|NY|P2+L2 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| A|H|L|M | DEAD | DEAD | N | Y | N | N | N | Y | Y | N | N | Y | 0.994 | L2SL pooled RC L6M p 0.018 (PRE .0015) |
| C|D|D_L30t | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 1.000 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| E|SL|PS|NY|P3+N1 | CANDIDATE | CANDIDATE | Y | Y | Y | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|KB|Asia|P3+L2 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 0.993 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|PS|NY|G2k70 | CANDIDATE | CANDIDATE | Y | Y | Y | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|KB|Asia|P3 | CANDIDATE | CANDIDATE | Y | Y | Y | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|WT|Asia|P1+L1 | DEAD | DEAD | N | Y | N | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| B|L2SL|HM_PRE | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | Y | 0.999 | L2SL pooled RC L6M p 0.018 |
| E|SL|HM|NY|P1+L1.5 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|PB|London|P3+L1.5 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | Y | N | N | N | n/a | Y | n/a | N | N | 0.932 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|PS|NY|P3+L2 | CANDIDATE-RECENT | CANDIDATE-RECENT | Y | N | Y | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| C|D|D_B3s | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| C|A|A01 | DEAD | DEAD | N | N | Y | N | N | n/a | Y | n/a | N | N | 1.000 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| E|SL|PS|NY|P3+L1.5 | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|PS|NY|L2 | DEAD | DEAD | N | N | Y | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| A|B|P|N | DEAD | DEAD | N | N | Y | N | N | N | N | N | N | Y | 1.000 | plain 70% take is a pre-specified reference (not searched) |
| B|EXP2|B_U3 | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 0.925 | EXP2 part (b) RC PRE p 0.76; (d) 19 cells all DEAD |
| C|A|A07 | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| C|D|D_B3e | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| E|SL|ST|Asia|P1.5+N3 | DEAD | DEAD | N | Y | N | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| B|EXP2|P | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | EXP2 part (b) RC PRE p 0.76; (d) 19 cells all DEAD |
| B|L2SL|SM_PRE | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | Y | 1.000 | L2SL pooled RC L6M p 0.018 |
| E|SL|PS|London|N2 | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| A|H|EP|N | DEAD | DEAD | N | N | Y | N | N | N | Y | N | N | N | 1.000 | L2SE stack RC L6M p 0.11 (HOLD .18, PRE .77) |
| E|SL|ST|NY|N2 | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| E|SL|ST|NY|P3+N2 | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| B|EXP2|B_U3_P | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | EXP2 part (b) RC PRE p 0.76; (d) 19 cells all DEAD |
| E|SL|ST|Asia|P1.5+L2 | DEAD | DEAD | N | Y | N | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| B|L2SL|KB_RANK | DEAD | DEAD | N | N | N | N | N | n/a | N | n/a | N | Y | 1.000 | L2SL pooled RC L6M p 0.018 |
| B|L2SL|ST_RANK | DEAD | DEAD | N | N | N | N | N | n/a | N | n/a | N | Y | 1.000 | L2SL pooled RC L6M p 0.018 |
| B|L2SL|KB_PRE | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | Y | 1.000 | L2SL pooled RC L6M p 0.018 |
| A|H|P|N | DEAD | DEAD | N | N | Y | N | N | N | Y | N | N | Y | 1.000 | plain 70% take is a pre-specified reference (not searched) |
| F|CW|HM | DEAD | DEAD | N | Y | N | N | N | n/a | Y | n/a | N | N | 1.000 | CUTWAIT RC p 0.26-0.99 per book |
| B|L2SL|WT_RANK | DEAD | DEAD | N | N | N | N | N | n/a | N | n/a | N | Y | 1.000 | L2SL pooled RC L6M p 0.018 |
| C|D|D_B3h | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| B|L2SL|WT_PRE | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | Y | 1.000 | L2SL pooled RC L6M p 0.018 |
| B|L2SL|PE_PRE | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | Y | 1.000 | L2SL pooled RC L6M p 0.018 |
| B|L2SL|PE_RANK | DEAD | DEAD | N | N | N | N | N | n/a | N | n/a | N | Y | 1.000 | L2SL pooled RC L6M p 0.018 |
| B|L2SL|ST_PRE | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | Y | 1.000 | L2SL pooled RC L6M p 0.018 |
| H|L2SP|ALL_PRE_selected|N | DEAD | DEAD | N | N | N | N | N | N | Y | n/a | N | N | 1.000 | L2SP pooled White RC (PRE) p 0.72 |
| A|H|EPL|N | DEAD | DEAD | N | N | N | N | N | N | Y | N | N | N | 1.000 | L2SE stack RC L6M p 0.11 (HOLD .18, PRE .77) |
| E|SL|ST|Asia|P1.5+N2 | DEAD | DEAD | N | Y | N | N | N | n/a | Y | n/a | N | N | 1.000 | T-SESSION-LOCKS G8 family-wise null: 798 of 798 fail |
| C|A|A02 | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| F|CW|ST | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | CUTWAIT RC p 0.26-0.99 per book |
| A|H|PL|N | DEAD | DEAD | N | N | N | N | N | N | Y | N | N | Y | 1.000 | plain 70% take is a pre-specified reference (not searched); loss cell L2SL RC 0.018 |
| B|EXP2|B_FROZEN_P | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | EXP2 part (b) RC PRE p 0.76; (d) 19 cells all DEAD |
| F|CW|PE | DEAD | DEAD | N | Y | N | N | N | n/a | Y | n/a | N | N | 1.000 | CUTWAIT RC p 0.26-0.99 per book |
| D|D6L_alone | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | DIPENTRY best-of-N RC PRE p 0.85 |
| B|L2SL|ALL_PRE | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | Y | 1.000 | L2SL pooled RC L6M p 0.018 |
| D|PROFIT_alone | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | DIPENTRY best-of-N RC PRE p 0.85 |
| B|L2SL|COMBO_PRE | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | Y | 1.000 | L2SL pooled RC L6M p 0.018 |
| B|EXP2|B_FROZEN | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | EXP2 part (b) RC PRE p 0.76; (d) 19 cells all DEAD |
| B|EXP2|B_U3_L | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | EXP2 part (b) RC PRE p 0.76; (d) 19 cells all DEAD |
| B|EXP2|L | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | EXP2 part (b) RC PRE p 0.76; (d) 19 cells all DEAD |
| B|EXP2|B_U1_P | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | EXP2 part (b) RC PRE p 0.76; (d) 19 cells all DEAD |
| F|CW|KB | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | CUTWAIT RC p 0.26-0.99 per book |
| B|EXP2|B_U1 | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | EXP2 part (b) RC PRE p 0.76; (d) 19 cells all DEAD |
| B|EXP2|B_U3_P_L | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | EXP2 part (b) RC PRE p 0.76; (d) 19 cells all DEAD |
| B|EXP2|P_L | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | EXP2 part (b) RC PRE p 0.76; (d) 19 cells all DEAD |
| D|JOINT3 | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | DIPENTRY best-of-N RC PRE p 0.85 |
| D|JOINT10 | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | DIPENTRY best-of-N RC PRE p 0.85 |
| D|JOINT20 | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | DIPENTRY best-of-N RC PRE p 0.85 |
| D|LOSS20_alone | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | DIPENTRY best-of-N RC PRE p 0.85 |
| D|LOSS10_alone | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | DIPENTRY best-of-N RC PRE p 0.85 |
| B|EXP2|B_U2_P | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | EXP2 part (b) RC PRE p 0.76; (d) 19 cells all DEAD |
| D|LOSS3_alone | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | DIPENTRY best-of-N RC PRE p 0.85 |
| B|EXP2|B_U2 | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | EXP2 part (b) RC PRE p 0.76; (d) 19 cells all DEAD |
| F|CW|ALL6 | DEAD | DEAD | N | Y | N | N | N | n/a | Y | n/a | N | N | 1.000 | CUTWAIT RC p 0.26-0.99 per book |
| C|A|A10 | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | section tier DEAD/LEAD, best-of-N not significant (n/r here) |
| B|EXP2|B_U2_L | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | EXP2 part (b) RC PRE p 0.76; (d) 19 cells all DEAD |
| B|EXP2|B_U2_P_L | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | EXP2 part (b) RC PRE p 0.76; (d) 19 cells all DEAD |
| B|EXP2|B_U1_L | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | EXP2 part (b) RC PRE p 0.76; (d) 19 cells all DEAD |
| B|EXP2|B_FROZEN_P_L | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | EXP2 part (b) RC PRE p 0.76; (d) 19 cells all DEAD |
| B|EXP2|B_FROZEN_L | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | EXP2 part (b) RC PRE p 0.76; (d) 19 cells all DEAD |
| B|EXP2|B_U1_P_L | DEAD | DEAD | N | N | N | N | N | n/a | Y | n/a | N | N | 1.000 | EXP2 part (b) RC PRE p 0.76; (d) 19 cells all DEAD |

### M versus N basis (frame A and H, equal-risk delta at worst-20 match, c* in brackets)
| rule | M: c* | L6M | HOLD | PRE | N: c* | L6M | HOLD | PRE |
|--|--|--|--|--|--|--|--|--|
| A|B|EPL | 1.39 | +81.6k (62.6k) | +76.4k (55.9k) | -30.9k (35.6k) | 1.31 | +41.2k (59.7k) | +39.4k (53.4k) | -54.8k (37.7k) |
| A|B|EP | 1.44 | +79.3k (65.0k) | +74.5k (57.8k) | -5.0k (35.7k) | 1.35 | +42.6k (58.7k) | +40.9k (52.2k) | -29.4k (37.6k) |
| A|B|E | 1.37 | +79.3k (46.8k) | +69.0k (44.1k) | -4.8k (30.2k) | 1.43 | +90.3k (44.2k) | +80.5k (41.3k) | -6.7k (33.6k) |
| A|B|EL | 1.35 | +76.3k (51.4k) | +67.5k (48.0k) | -28.5k (29.3k) | 1.38 | +79.7k (48.6k) | +71.2k (45.4k) | -36.3k (33.3k) |
| H|L2SP|ALL_L6M_rank1 | 1.20 | +56.4k (47.9k) | +48.7k (43.8k) | -14.0k (26.8k) | 1.03 | +11.5k (49.0k) | +7.2k (45.1k) | -40.1k (26.2k) |
| A|B|PL | 1.15 | +53.0k (49.4k) | +49.6k (44.2k) | -15.8k (28.6k) | 1.10 | +19.8k (48.5k) | +19.2k (43.0k) | -38.5k (30.2k) |
| A|H|EP | 1.22 | +43.9k (52.8k) | +39.9k (46.6k) | +4.3k (25.0k) | 1.11 | -1.5k (51.4k) | -1.5k (44.9k) | -25.8k (25.6k) |
| A|H|P | 1.20 | +39.4k (48.1k) | +37.9k (42.4k) | +0.6k (23.9k) | 1.10 | -3.5k (49.8k) | -1.8k (43.8k) | -29.0k (25.3k) |
| A|H|PL | 1.28 | +38.8k (66.3k) | +31.1k (59.2k) | +14.3k (24.3k) | 1.17 | -7.5k (65.9k) | -10.9k (57.6k) | -17.4k (25.3k) |
| A|H|EPL | 1.29 | +38.7k (64.0k) | +28.9k (57.8k) | +18.3k (25.0k) | 1.19 | -5.9k (64.0k) | -11.4k (56.2k) | -12.5k (25.3k) |
| A|B|P | 1.17 | +34.3k (38.4k) | +33.1k (33.9k) | +2.5k (21.2k) | 1.08 | -0.2k (38.8k) | +1.6k (34.1k) | -20.5k (21.6k) |
| A|B|L | 1.04 | +25.9k (33.0k) | +23.3k (29.9k) | -14.6k (20.5k) | 1.09 | +27.8k (30.3k) | +27.6k (26.7k) | -17.1k (22.8k) |
| A|H|EL | 1.14 | +15.0k (39.8k) | +7.9k (37.3k) | +23.7k (17.8k) | 1.18 | +26.3k (49.0k) | +18.5k (45.7k) | +25.3k (18.3k) |
| A|H|E | 1.00 | +13.4k (14.5k) | +11.6k (14.0k) | +7.8k (11.3k) | 1.06 | +22.6k (16.4k) | +22.6k (16.0k) | +7.7k (11.4k) |
| H|L2SP|ALL_PRE_selected | 1.15 | +6.1k (23.2k) | +5.1k (20.7k) | +4.0k (13.5k) | 1.09 | -5.5k (22.5k) | -5.9k (20.0k) | -5.0k (12.8k) |
| A|H|L | 1.09 | +1.4k (33.0k) | -4.0k (30.5k) | +11.7k (14.8k) | 1.15 | +15.7k (41.0k) | +11.3k (39.9k) | +19.0k (17.8k) |

## 9. Session / book variants (frame A, rows attributed to the engine book (= D6 book tag) and to the entry session; each attribution is scaled to the equal worst-20 of the SAME book / session of the stack as it is; attribution, not a separate engine run)
Engine book = D6 tag: ST = S6, HM = H6 (DS6), WT = W6, KB = K6, SM = U6, PE = P6. Sessions = session_tag of the trade table (asia, london, nyam, nypm). Delta = L6M / HOLD / PRE, MDE in parentheses; c = the book-level factor.
**A|H|E|M**
| unit | c | L6M | HOLD | PRE | X' | WF |
|--|--|--|--|--|--|--|
| ST | 1.02 | +2.5k (9.4k) | +1.8k (9.1k) | +4.1k (7.7k) | +0.2k (4.1k) | +3.5k (6.1k) |
| HM | 0.99 | +3.0k (5.9k) | +2.9k (5.5k) | +1.8k (4.6k) | +1.7k (3.7k) | +2.2k (3.6k) |
| WT | 0.99 | +2.7k (4.6k) | +2.6k (4.1k) | +1.1k (4.6k) | -1.6k (3.2k) | +1.6k (3.5k) |
| KB | 0.93 | +1.5k (5.2k) | +1.2k (5.0k) | -1.4k (2.2k) | +1.0k (3.3k) | -0.6k (2.2k) |
| SM | 0.97 | +2.7k (4.1k) | +3.0k (4.1k) | -0.2k (1.4k) | -0.8k (1.4k) | +0.8k (1.6k) |
| PE | 1.08 | +1.2k (5.3k) | +0.5k (4.7k) | +2.2k (3.2k) | +2.6k (3.2k) | +1.7k (2.7k) |
| S:asia | 1.00 | +0.9k (6.8k) | +1.4k (6.5k) | -2.1k (3.9k) | +1.3k (3.9k) | -1.1k (3.4k) |
| S:london | 1.00 | +3.4k (5.3k) | +3.0k (4.7k) | +4.4k (6.7k) | -2.1k (3.6k) | +4.0k (4.9k) |
| S:nyam | 0.93 | +2.7k (9.1k) | +2.3k (8.4k) | +2.0k (6.2k) | +2.0k (6.0k) | +2.1k (5.1k) |
| S:nypm | 1.02 | +5.1k (5.3k) | +3.6k (5.1k) | +2.2k (4.2k) | +0.3k (2.5k) | +2.7k (3.3k) |

**A|H|E|N**
| unit | c | L6M | HOLD | PRE | X' | WF |
|--|--|--|--|--|--|--|
| ST | 1.01 | +8.1k (10.3k) | +8.3k (9.7k) | +1.2k (6.3k) | +0.8k (4.6k) | +3.3k (5.4k) |
| HM | 1.00 | +1.8k (7.7k) | +2.4k (7.0k) | +1.4k (5.3k) | +0.4k (4.1k) | +1.7k (4.3k) |
| WT | 1.01 | +4.2k (5.7k) | +4.1k (5.3k) | +1.5k (4.1k) | -1.7k (2.7k) | +2.3k (3.3k) |
| KB | 0.98 | +0.3k (6.9k) | +0.5k (6.1k) | -2.1k (2.7k) | +0.9k (3.5k) | -1.3k (2.7k) |
| SM | 0.97 | +2.8k (4.5k) | +3.0k (4.4k) | -0.0k (1.6k) | -0.9k (1.6k) | +0.9k (1.8k) |
| PE | 1.04 | +0.6k (6.7k) | +0.1k (6.1k) | +2.0k (3.4k) | +2.8k (2.9k) | +1.4k (3.0k) |
| S:asia | 1.01 | -0.1k (7.7k) | +0.6k (7.2k) | -1.8k (5.0k) | +1.2k (4.0k) | -1.1k (4.1k) |
| S:london | 1.01 | +3.9k (7.4k) | +3.3k (6.6k) | +3.7k (4.8k) | -1.3k (4.0k) | +3.6k (3.9k) |
| S:nyam | 1.02 | +11.0k (11.7k) | +10.8k (10.5k) | +1.0k (6.1k) | +0.4k (5.6k) | +4.0k (5.5k) |
| S:nypm | 1.08 | +5.0k (7.7k) | +6.2k (7.8k) | +1.1k (4.6k) | +0.7k (3.3k) | +2.6k (4.1k) |

**A|H|P|N**
| unit | c | L6M | HOLD | PRE | X' | WF |
|--|--|--|--|--|--|--|
| ST | 1.00 | +4.4k (24.4k) | +4.2k (21.6k) | -7.1k (13.2k) | -4.3k (13.2k) | -3.8k (11.4k) |
| HM | 1.00 | -4.1k (16.8k) | -4.0k (15.0k) | -8.3k (11.4k) | -6.3k (10.3k) | -7.1k (9.2k) |
| WT | 0.92 | -0.9k (13.5k) | +0.7k (12.4k) | -4.2k (7.6k) | -0.7k (7.7k) | -2.7k (6.6k) |
| KB | 0.98 | -6.0k (9.5k) | -5.0k (9.2k) | -5.9k (6.1k) | +0.8k (8.1k) | -5.7k (5.1k) |
| SM | 1.18 | +1.0k (7.4k) | +2.1k (6.6k) | -1.9k (4.8k) | +2.0k (6.4k) | -0.7k (3.9k) |
| PE | 1.03 | -3.4k (11.7k) | -3.7k (10.4k) | -3.5k (7.1k) | +2.9k (7.7k) | -3.6k (5.9k) |
| S:asia | 1.21 | -7.3k (33.0k) | -6.9k (29.2k) | -5.9k (12.8k) | -2.5k (18.1k) | -6.3k (12.6k) |
| S:london | 1.03 | -1.9k (14.2k) | -2.9k (13.1k) | -7.8k (10.5k) | -4.5k (10.9k) | -6.4k (8.4k) |
| S:nyam | 0.86 | -0.6k (17.9k) | -0.7k (15.8k) | -10.5k (12.6k) | -3.0k (12.9k) | -7.6k (10.2k) |
| S:nypm | 0.99 | +6.3k (13.2k) | +5.7k (11.9k) | -1.9k (7.2k) | +3.6k (10.0k) | +0.4k (6.2k) |

**A|H|L|N**
| unit | c | L6M | HOLD | PRE | X' | WF |
|--|--|--|--|--|--|--|
| ST | 1.04 | -1.0k (27.6k) | +0.4k (24.2k) | -1.4k (7.2k) | -7.0k (7.5k) | -0.9k (8.8k) |
| HM | 1.18 | +10.4k (17.8k) | +6.0k (18.5k) | +8.9k (10.7k) | -1.5k (12.6k) | +8.1k (9.3k) |
| WT | 1.04 | +3.2k (8.1k) | +2.2k (7.3k) | +1.2k (5.8k) | +2.4k (3.9k) | +1.5k (4.6k) |
| KB | 0.90 | -3.4k (8.8k) | -3.0k (8.1k) | -0.9k (4.5k) | +1.8k (5.2k) | -1.5k (4.0k) |
| SM | 1.18 | +0.7k (8.2k) | +0.6k (7.7k) | +2.6k (4.4k) | +2.5k (3.5k) | +2.0k (3.9k) |
| PE | 0.99 | +0.4k (10.1k) | +1.0k (9.2k) | +2.7k (6.5k) | +4.4k (7.2k) | +2.2k (5.3k) |
| S:asia | 1.07 | +5.1k (17.3k) | +3.0k (16.6k) | +5.4k (9.6k) | -2.3k (9.2k) | +4.7k (8.4k) |
| S:london | 1.12 | +1.6k (21.8k) | -0.3k (19.4k) | +5.5k (8.3k) | +2.1k (7.1k) | +3.8k (8.3k) |
| S:nyam | 1.09 | +7.8k (19.9k) | +7.8k (17.9k) | +2.9k (10.2k) | +0.2k (12.0k) | +4.4k (9.0k) |
| S:nypm | 0.95 | -2.1k (11.2k) | -2.2k (11.2k) | -0.5k (6.3k) | +1.2k (7.7k) | -1.0k (5.5k) |

**A|H|EL|N**
| unit | c | L6M | HOLD | PRE | X' | WF |
|--|--|--|--|--|--|--|
| ST | 1.02 | +6.1k (29.2k) | +4.8k (25.9k) | -0.1k (9.0k) | -6.1k (8.3k) | +1.4k (10.0k) |
| HM | 1.20 | +6.0k (19.4k) | +2.7k (19.6k) | +9.7k (11.8k) | +0.7k (12.3k) | +7.7k (10.2k) |
| WT | 0.97 | +6.0k (8.5k) | +4.6k (7.7k) | +1.2k (6.8k) | -0.3k (4.8k) | +2.2k (5.4k) |
| KB | 0.88 | -4.5k (10.4k) | -3.7k (9.5k) | -1.6k (5.0k) | +1.7k (5.4k) | -2.2k (4.5k) |
| SM | 1.17 | +3.9k (9.3k) | +3.9k (8.3k) | +3.3k (4.8k) | +1.8k (3.4k) | +3.5k (4.2k) |
| PE | 0.99 | -0.8k (8.6k) | -0.9k (8.2k) | +3.8k (7.5k) | +5.6k (7.2k) | +2.4k (5.8k) |
| S:asia | 1.08 | +6.2k (20.9k) | +4.7k (19.6k) | +4.8k (10.2k) | -1.0k (9.4k) | +4.8k (9.2k) |
| S:london | 1.13 | +1.6k (23.6k) | -0.3k (20.9k) | +8.3k (9.5k) | +0.6k (7.6k) | +5.8k (9.2k) |
| S:nyam | 1.15 | +12.3k (21.8k) | +12.1k (19.8k) | +4.8k (11.7k) | -0.0k (12.8k) | +7.0k (10.2k) |
| S:nypm | 0.94 | +1.8k (14.4k) | -0.6k (13.0k) | +0.2k (7.1k) | +0.6k (7.7k) | -0.1k (6.4k) |

**A|H|EPL|N**
| unit | c | L6M | HOLD | PRE | X' | WF |
|--|--|--|--|--|--|--|
| ST | 0.95 | +4.8k (32.8k) | +3.0k (29.0k) | -7.4k (11.7k) | -8.0k (15.5k) | -4.4k (12.0k) |
| HM | 1.23 | -5.8k (24.7k) | -9.7k (22.1k) | +0.4k (13.8k) | -3.2k (14.2k) | -2.6k (11.9k) |
| WT | 0.96 | -0.3k (11.1k) | +0.7k (10.5k) | -1.7k (8.3k) | +1.3k (8.3k) | -1.0k (6.7k) |
| KB | 0.95 | -11.1k (11.4k) | -10.1k (11.0k) | -4.5k (7.2k) | +1.5k (9.3k) | -6.2k (6.1k) |
| SM | 1.31 | +1.9k (10.0k) | +2.2k (9.0k) | +0.5k (6.0k) | +4.4k (6.8k) | +1.0k (5.0k) |
| PE | 0.88 | -3.8k (10.1k) | -3.0k (9.5k) | -4.5k (8.5k) | +5.2k (8.5k) | -4.1k (6.6k) |
| S:asia | 1.35 | -4.1k (37.2k) | -6.1k (33.9k) | -0.9k (15.2k) | -2.7k (16.6k) | -2.5k (14.8k) |
| S:london | 1.01 | -12.2k (22.4k) | -13.2k (19.8k) | -2.9k (12.0k) | -5.1k (12.8k) | -6.1k (10.4k) |
| S:nyam | 1.00 | +4.5k (23.5k) | +1.7k (21.4k) | -6.4k (13.8k) | -0.0k (16.2k) | -4.0k (11.7k) |
| S:nypm | 1.05 | +2.2k (16.1k) | +0.9k (14.5k) | -1.9k (9.0k) | +4.8k (11.8k) | -1.1k (7.7k) |

**A|H|EPL|M**
| unit | c | L6M | HOLD | PRE | X' | WF |
|--|--|--|--|--|--|--|
| ST | 1.03 | +15.6k (33.4k) | +10.9k (30.1k) | +1.2k (11.8k) | -6.0k (16.1k) | +4.2k (12.3k) |
| HM | 1.29 | +1.3k (24.3k) | -3.0k (22.1k) | +6.9k (13.5k) | +0.1k (14.5k) | +4.0k (11.7k) |
| WT | 1.07 | +7.9k (10.9k) | +9.1k (10.3k) | +2.8k (7.7k) | +3.5k (8.3k) | +4.7k (6.3k) |
| KB | 0.96 | -1.4k (10.0k) | -1.0k (9.7k) | -0.6k (6.9k) | +2.8k (9.2k) | -0.7k (5.7k) |
| SM | 1.35 | +5.0k (10.1k) | +5.4k (9.1k) | +2.8k (6.2k) | +5.6k (7.1k) | +3.6k (5.1k) |
| PE | 0.97 | +1.6k (10.9k) | +1.8k (9.8k) | -0.7k (8.4k) | +7.0k (8.6k) | +0.0k (6.6k) |
| S:asia | 1.45 | +16.7k (36.3k) | +13.1k (34.4k) | +11.2k (15.9k) | +0.4k (17.2k) | +11.9k (15.2k) |
| S:london | 1.09 | -0.8k (20.6k) | -2.4k (18.1k) | +5.9k (11.8k) | -3.0k (12.3k) | +3.4k (10.0k) |
| S:nyam | 1.03 | +11.5k (26.8k) | +8.4k (24.1k) | -0.7k (13.5k) | +4.0k (16.3k) | +2.1k (12.0k) |
| S:nypm | 1.05 | +3.9k (14.5k) | +1.4k (13.3k) | -0.1k (9.1k) | +5.6k (11.8k) | +0.4k (7.5k) |

D6 line / session gating (additive lines): NOT re-scored here; the existing D6LINE tables (DS3_SESSION2_D_D6LINE.md) show the NY-AM HM line is positive but inside its MDE and the wider session line does not hedge the stack's 20 worst weeks (add in those weeks negative at every risk level); an add-on line is not a rule on the stack, so the equal-risk comparison there is the stack-add table already printed in that report.

## 10. Honesty
* Worst-20-weeks on ~106 weeks (20 observations = the worst 19% of weeks) is a noisy statistic. Bootstrap 95% CI of c* is roughly +-15-30% around the point value and the CI on the WF equal-risk delta is wide (section 2); the HOLD-out-of-sample check (section 6) shows the matched risk does not hold in HOLD.
* Selection status: H-set E and L cells were chosen on PRE only (E from 2,179 cells, L from 7,840 cells; the upstream RC does not clear), P (plain 70% take) is a pre-specified reference; B-set cells, `_RANK` L2SL cells, `B2_L6Mrank` and every L6M-ranked row were ranked on looked data and are marked LOOK (in-sample for L6M, HOLD and Y26 by construction, and the only honest hint is their PRE and X' columns, which are mostly negative). STK_F layers were each PRE-picked in their own section, A06/HM5R/B02 additionally admitted at the HOLD look.
* Frames: only frame A has exact per-row lots and the real engine rerun; the other frames use the as-is stack's sweep profile (dvg base parts for B/C/E/G/H, frame-A base rows for D/F), which flatters lot-cutting rules slightly (they would pay less sweep when scaled) and penalizes lot-adding rules; sweep is small up to c about 1.4 (zero up to 14 lots per order). Weekly frames (C, G) assign a whole ISO week to a window that contains one of its business days.
* Duplicates counted once: C|F|A03 = C|A|A03, C|F|A06 = C|A|A06, C|F|D40 = C|D|D_L40s.
* NOT rebuilt (no stack-engine series exists; trade-level only): THP/THL/THL2/THPC1/THPC2 tighten and profit chains (they enter through the L2SL tighten cells), EXP1, ABRC1, ADAPTIVE brackets other than the 19 EXP2 joint cells. Those families are not dismissed by absence; they just have no stack series to scale.
* The M basis charges the target-fill correction (1.4/1.5/4.2/4.3 pt) on target fills and not on early market exits: every profit-taking rule gains on M mechanically. The N rows are the ones to believe for profit rules; random exits show the size of the M-basis artefact (section 7).
* Integer contract rounding is not modelled (fractional lots in the engine); a factor of 1.2 on 10 lots is 12 contracts, on 5.2 lots 6.2.
* Session-lock frames (EA/EB) use `sl_stack`, which imports `s48score`, only for S.DAYS and the stack weights; every frame was cut to label day <= 20260206 at extraction before any use, and S.WINMASK / WINS were not used (own masks only). Accepted by the coordinator; no rebuild needed.
