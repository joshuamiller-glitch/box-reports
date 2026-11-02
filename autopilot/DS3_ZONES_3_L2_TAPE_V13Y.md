# DS3_ZONES_3_L2_TAPE_V13Y - the tape leads re-run on the FIXED base D7 V13Y (ZL-2)

V13Y = V13X + the add-fill ordering fix (BASE-4): base F9 maxDD lock none 132.6k -> 96.2k, 12R 78.5k -> 52.8k. Every V13X page of ZL-2 carries a DEFECT-BASE banner; this page is the V13Y re-run of the leads and the 583-cell lock-none screen. maxDD change vs the base of each frame, V13X -> V13Y.

## 1. Leads: V13X -> V13Y (maxDD change F9 / L6M / HOLD / MID / PRE / X')

**LOCK NONE (headline)**
| cell | F9 | L6M | HOLD | MID | PRE | X' | label change |
|---|---|---|---|---|---|---|---|
| A40 TLP_p25_4h skip | -19% -> -27% | -19% -> -27% | -1% -> +8% | -18% -> +14% | -8% -> -8% | +18% -> -5% |  |
| A30 TCD_ext half | -46% -> -60% | -52% -> -60% | -7% -> -2% | +13% -> +28% | +10% -> +31% | -15% -> -16% |  |
| A40 TCD_ext skip | -54% -> -54% | -54% -> -59% | -15% -> -0% | -2% -> +48% | +52% -> +83% | -27% -> -23% |  |
| A40 TVP_poc_day skip | +2% -> +11% | +2% -> +11% | +3% -> +12% | +19% -> +39% | +4% -> +12% | -13% -> -22% |  |
| A40 TLQ_SES_asia half | -7% -> -8% | -7% -> -8% | +1% -> +14% | -2% -> +24% | -13% -> -6% | -7% -> -13% |  |
| A40 TPF_poc_sw15 skip | -21% -> -23% | -21% -> -23% | -17% -> -11% | -13% -> -20% | +9% -> +17% | -41% -> -29% |  |
| A40 TPF_val_sess skip | -20% -> -29% | -20% -> -29% | -12% -> -5% | -15% -> +30% | +20% -> +23% | -36% -> -4% |  |
| A40 TVP_poc skip | +4% -> +20% | +4% -> +20% | +4% -> +12% | +19% -> +39% | +7% -> +15% | -2% -> -19% |  |

**12R combined lock**
| cell | F9 | L6M | HOLD | MID | PRE | X' | label change |
|---|---|---|---|---|---|---|---|
| A40 TLP_p25_4h skip | -12% -> -1% | -6% -> -1% | -18% -> -15% | -18% -> -9% | -35% -> -17% | -12% -> -19% |  |
| A30 TCD_ext half | -20% -> -6% | -15% -> -6% | -22% -> -9% | -44% -> -14% | -10% -> -20% | +6% -> +53% |  |
| A40 TCD_ext skip | +1% -> +35% | +1% -> +15% | -23% -> +3% | -35% -> -0% | +15% -> -2% | -45% -> -25% |  |
| A40 TVP_poc_day skip | -23% -> -0% | -19% -> -0% | -35% -> -19% | -33% -> -40% | -31% -> -33% | -39% -> -24% |  |
| A40 TLQ_SES_asia half | -9% -> +1% | -5% -> +1% | -9% -> +0% | -9% -> -12% | -15% -> -20% | +0% -> -6% |  |
| A40 TPF_poc_sw15 skip | +11% -> +16% | +2% -> +1% | -24% -> +1% | +11% -> +17% | -8% -> -20% | -56% -> -49% |  |
| A40 TPF_val_sess skip | +30% -> +31% | +38% -> +31% | -14% -> -11% | -13% -> -34% | -6% -> -8% | -20% -> -39% |  |
| A40 TVP_poc skip | -21% -> -0% | -16% -> -0% | -43% -> -19% | -33% -> -40% | -37% -> -34% | -10% -> -20% |  |

## 2. Row-level placebo ranks on V13Y (lock none; random rows, same count per day, 100 draws; share of draws the real cut beats)
| cell | F9 | L3M | HOLD | PRE | draws |
|---|---|---|---|---|---|
| A40 TLP_p25_4h skip | 0.84 | 0.99 | 0.44 | 0.99 | 100 |
| A30 TCD_ext half | 1.00 | 0.73 | 0.67 | 0.15 | 100 |
| A40 TVP_poc_day skip | 0.18 | 0.45 | 0.17 | 0.13 | 100 |
| A40 TLQ_SES_asia half | 0.77 | 0.80 | 0.08 | 0.82 | 100 |
| A40 TPF_poc_sw15 skip | 0.92 | 0.90 | 0.94 | 0.14 | 100 |
| A40 TCP_hvn1_60d skip | 0.87 | 0.36 | 0.23 | 0.02 | 100 |

## 3. The 583-cell lock-none screen on V13Y (Z3 final lock-off band; the V13Y band of Z3 is not yet published)
Cells scored: 628. Band rule (L6M and PRE-or-X' above the band): flip-2% 19, flip-5% 7; plus no-harm (PRE and MID not worse than -22% / -20%): flip-2% 5, flip-5% 1.
| cell | rows | F9 | L3M | L6M | HOLD | MID | PRE | X' | no harm | placebo F9 / PRE (100 draws) |
|---|---|---|---|---|---|---|---|---|---|---|
| A25 TCD_ext skip | 11984 | +60% | +9% | +60% | +12% | -27% | -39% | +24% | NO |  |
| A30 TCD_ext half | 13563 | +60% | +2% | +60% | +2% | -28% | -31% | +16% | NO | 1.00 / 0.15 |
| A40 TCD_ext skip | 15965 | +54% | -14% | +59% | +0% | -48% | -83% | +23% | NO |  |
| A50 TCD_ext half | 17805 | +57% | +0% | +57% | +1% | -20% | -41% | +24% | NO |  |
| A60 TCD_ext half | 19375 | +53% | +0% | +53% | +8% | -2% | -40% | +22% | NO |  |
| A40 TCD_ext half | 15965 | +48% | +4% | +48% | +4% | -11% | -58% | +28% | NO |  |
| A20 TVP_lvn_sess half | 18233 | +32% | -22% | +43% | -32% | -115% | -54% | +21% | NO |  |
| A10 TCD_ext skip | 5592 | +37% | +30% | +37% | -3% | -32% | -28% | +32% | NO |  |
| A40 TLQ_SWG_f3_1h skip | 16359 | +6% | +17% | +28% | -79% | -198% | +30% | -238% | NO |  |
| A40 TLQ_swg1h skip | 16806 | +9% | +16% | +28% | -76% | -189% | +30% | -251% | NO |  |
| A40 TPF_lvn0_sw15 skip | 2787 | +27% | +21% | +27% | -25% | -86% | -36% | +29% | NO |  |
| A40 TPF_poc_sw15 skip | 3485 | +23% | +16% | +23% | +11% | +20% | -17% | +29% | yes | 0.92 / 0.14 |
| LP T10_1h_any_D40 | 22170 | +23% | -35% | +23% | +8% | -29% | +31% | +24% | NO |  |
| A40 TPF_lvn0_sess skip | 3224 | +22% | +6% | +22% | -1% | -28% | -9% | +22% | NO |  |
| A40 TCP_hvn1_60d skip | 652 | +20% | -9% | +20% | +0% | +0% | -8% | +19% | yes | 0.87 / 0.02 |
| A40 TPF_hvn0_sw15 skip | 3357 | +19% | -10% | +19% | +5% | -15% | +2% | +33% | yes |  |
| A40 TCP_hvn1_60d half | 652 | +19% | +4% | +19% | +0% | +0% | -4% | +16% | yes |  |
| A20 TCD_cdhi half | 5956 | +18% | +2% | +18% | -3% | +3% | -19% | +18% | yes |  |
| A40 TLQ_SWG_f5_1h skip | 11474 | +17% | +18% | +17% | -40% | -109% | +25% | -204% | NO |  |
(cut = 1 - maxDD(cell)/maxDD(base): positive = shallower.) Reading: the cum-delta extremes pass through L6M and X' with PRE and MID strongly negative (not no-harm); the no-harm passers are small TPF/TCP lines whose placebo ranks in PRE are 0.02-0.14 (volume-equivalent or worse than random). Nothing passes band + no-harm + placebo.

## 4. Other V13Y re-runs
* Large-print skip, dollar effect / sensitivity / walk-forward: `DS3_ZONES_3_L2_TAPE_LARGEPRINT_V13Y.md`; the against-the-trade flag: `DS3_ZONES_3_L2_TAPE_LP_AGAINST.md`.
* Row-level heat table with V13Y realised outcomes: `DS3_ZONES_3_ROW_LEVEL_V13Y.md`.
