> **DEFECT BASE (V13X):** every cut, rank, lead and withdrawal on this page was computed on D7 V13X, which dropped the TH-L2 loss cut and take-line exits that came before the resting add filled (846 rows; BASE-4 fixed it in V13Y). Treat all numbers here as 'defect base (V13X)'; the V13Y re-run of the leads is in progress and will supersede them.

# DS3_ZONES_3_B7_ASIA_CUBE - zone x vol tercile x session cube (Asia is the product in 2026), V13X, ZL-2

Window F9 = Feb-Oct 2026 (38 weeks). Cube = stored per-book x per-session daily series of the engine (6 core books x 6 sessions). Effect = cell minus base (candidates) or layer-on minus layer-off (the shipped 8-line layer: `zone=False, ote62=none` run on the same engine). Mean = $k per week, maxDD = change of that session's own maxDD. Vol terciles = weeks ranked by the weekly mean target distance of the engine rows (T1 calm .. T3 volatile). Lock none (user's literal frame, headline) and 12R beside.

## LOCK NONE (headline)
| cell | tag | rows | asia: mean / maxDD | london: mean / maxDD | nyam: mean / maxDD | nypm: mean / maxDD | Asia mean by vol tercile T1/T2/T3 | Asia mean by book (KB PE SM HM MV PB) |
|---|---|---|---|---|---|---|---|---|---|
| SHIPPED LAYER (8 lines: 7 x half at D20 + OTE-62 B73 D30) | shipped |  | -1.1 / -6% | +0.2 / -15% | +0.2 / -4% | +0.0 / +1% | -1.1 / -0.9 / -1.3 | -0.0 -0.5 -0.1 -0.0 +0.0 -0.5 |
| A40 TLQ_SES_asia half | small lead | 4643 | -0.2 / +5% | +0.6 / +15% | +0.3 / -3% | -0.1 / +2% | +0.0 / -0.4 / -0.1 | +0.0 -0.1 -0.0 -0.0 +0.0 -0.0 |
| A40 TLP_p25_4h skip | small lead | 5110 | -0.5 / -6% | +2.9 / -3% | -0.1 / +3% | +0.3 / -20% | -0.1 / -1.4 / -0.1 | +0.1 -0.5 -0.0 -0.1 +0.0 +0.1 |
| A40 TVP_poc_day skip | 12R lead only | 1768 | +0.1 / +10% | +0.5 / +10% | -0.2 / -6% | +0.0 / -0% | +1.1 / -1.2 / +0.3 | +0.0 +0.5 -0.3 -0.2 +0.0 +0.1 |
| A25 TCD_ext skip | band-rule passer | 11984 | -0.3 / -27% | +1.2 / -24% | +1.5 / -35% | +0.5 / -30% | +7.3 / -1.6 / -6.8 | -0.1 -1.0 -0.1 +0.4 +0.0 +0.5 |
| A30 TCD_ext skip | band-rule passer | 13563 | -1.2 / -19% | +2.0 / -16% | +1.7 / -35% | +0.5 / -31% | +3.6 / -0.2 / -6.9 | -0.2 -1.8 -0.3 +0.5 +0.0 +0.6 |
| VAR TCD_ext age1h skip A40 | band-rule passer | 11044 | -1.4 / -47% | +0.7 / -15% | +1.3 / -24% | +0.3 / -12% | +2.4 / -2.7 / -3.9 | -0.5 -1.1 -0.5 +0.3 +0.0 +0.4 |
| A40 TCD_ext skip | band-rule passer | 15965 | -1.2 / -35% | +1.7 / -1% | +1.1 / -13% | +0.3 / -21% | +1.8 / -1.6 / -3.9 | -0.3 -1.3 -0.3 +0.3 +0.0 +0.4 |
| VAR TCD_ext age24h skip A40 | band-rule passer | 15965 | -1.2 / -35% | +1.7 / -1% | +1.1 / -13% | +0.3 / -21% | +1.8 / -1.6 / -3.9 | -0.3 -1.3 -0.3 +0.3 +0.0 +0.4 |
| A30 TCD_ext half | band-rule passer | 13563 | -0.3 / -33% | +1.5 / -14% | +1.1 / +28% | +0.1 / -8% | +2.1 / +0.4 / -3.3 | -0.1 -0.7 -0.2 +0.3 +0.0 +0.3 |
| VAR TCD_ext age24h half A30 | band-rule passer | 13563 | -0.3 / -33% | +1.5 / -14% | +1.1 / +28% | +0.1 / -8% | +2.1 / +0.4 / -3.3 | -0.1 -0.7 -0.2 +0.3 +0.0 +0.3 |
| A40 TCD_ext half | band-rule passer | 15965 | +0.1 / -47% | +1.4 / -12% | +1.1 / -0% | +0.1 / -5% | +1.5 / +0.1 / -1.4 | -0.1 -0.2 -0.2 +0.2 +0.0 +0.3 |
| A50 TCD_ext half | band-rule passer | 17805 | -0.3 / -47% | +1.7 / -11% | +0.9 / -6% | +0.0 / +0% | +1.5 / -0.6 / -1.8 | -0.2 -0.3 -0.3 +0.2 +0.0 +0.3 |
| A60 TCD_ext half | band-rule passer | 19375 | -0.5 / -48% | +1.2 / -17% | +1.0 / -3% | -0.0 / +2% | +1.1 / -1.1 / -1.6 | -0.2 -0.6 -0.3 +0.2 +0.0 +0.3 |
| A20 TCD_cdlo skip | band-rule passer | 4170 | +1.8 / -24% | +0.1 / +2% | +0.8 / +18% | +0.1 / -5% | +6.4 / -3.8 / +2.3 | -0.2 +1.6 -0.1 +0.4 +0.0 +0.1 |
| A40 TCD_cdhi skip | band-rule passer | 8807 | -2.0 / -50% | +1.4 / -18% | +1.3 / -35% | +0.3 / -17% | -1.9 / +0.7 / -4.4 | -0.0 -2.2 +0.2 -0.2 +0.0 +0.4 |
| VAR TCD_ext age1h half A30 | band-rule passer | 9792 | -0.6 / -38% | +1.5 / -11% | +1.5 / -8% | +0.1 / -7% | +1.6 / +0.0 / -3.3 | -0.1 -0.7 -0.3 +0.3 +0.0 +0.2 |
| A20 TVP_lvn_sess skip | band-rule passer | 18233 | -3.8 / -23% | +1.6 / -23% | -0.6 / +40% | +0.6 / -35% | -7.2 / -0.0 / -3.9 | +0.2 -1.1 -1.2 -2.0 +0.0 +0.3 |
| VAR TCD_ext strMid skip A40 | band-rule passer | 5983 | -1.5 / -41% | +0.7 / -16% | -0.3 / +25% | -0.0 / +4% | -0.3 / -1.7 / -2.4 | +0.0 -1.8 +0.1 +0.5 +0.0 -0.3 |
| VAR TPF_poc_sw15 age4h skip A40 | band-rule passer | 3421 | +0.5 / -11% | -0.1 / -8% | +0.1 / -11% | +0.0 / -2% | +1.2 / -1.5 / +1.5 | +0.4 +0.2 +0.0 -0.2 +0.0 +0.0 |
| VAR TPF_poc_sw15 age24h skip A40 | band-rule passer | 3440 | +0.5 / -11% | -0.1 / -8% | +0.1 / -11% | +0.0 / -2% | +1.2 / -1.5 / +1.5 | +0.4 +0.2 +0.0 -0.2 +0.0 +0.0 |
| A40 TPF_poc_sw15 skip | band-rule passer | 3485 | +0.5 / -11% | -0.1 / -8% | +0.1 / -11% | +0.0 / -2% | +1.2 / -1.5 / +1.5 | +0.4 +0.2 +0.0 -0.2 +0.0 +0.0 |
| VAR TPF_val_sess strMid skip A40 | band-rule passer | 1130 | +0.5 / -20% | -0.8 / +13% | -0.4 / +44% | +0.3 / -17% | +2.1 / -0.4 / -0.3 | -0.1 +0.6 -0.1 +0.0 +0.0 +0.0 |
| A40 TPF_val_sess skip | band-rule passer | 3315 | +0.2 / -25% | -0.2 / +8% | -0.4 / +44% | +0.2 / -14% | +2.2 / +0.2 / -1.7 | -0.2 +1.0 -0.8 -0.0 +0.0 +0.2 |
| VAR TPF_val_sess age4h skip A40 | band-rule passer | 2440 | +0.0 / -15% | +0.2 / -3% | -0.3 / +38% | +0.2 / -12% | +1.5 / -0.6 / -0.9 | -0.2 +0.4 -0.2 +0.0 +0.0 +0.0 |
| A10 TCD_ext skip | band-rule passer | 5592 | -0.4 / -17% | -0.6 / -2% | +0.0 / +3% | +0.1 / -1% | +3.6 / -1.3 / -3.7 | +0.2 -0.7 -0.2 +0.1 +0.0 +0.2 |
| VAR TPF_val_sess age24h skip A40 | band-rule passer | 3102 | -0.5 / -20% | -0.2 / +7% | -0.4 / +38% | +0.2 / -14% | +1.2 / -0.9 / -1.7 | -0.2 +0.5 -0.7 -0.1 +0.0 +0.1 |
| A40 TPF_hvn0_sw15 skip | band-rule passer | 3357 | +0.9 / -13% | -0.6 / +14% | -0.0 / -16% | -0.0 / -3% | +2.7 / -0.8 / +0.6 | +0.4 +0.5 +0.0 -0.1 +0.0 +0.0 |
| A40 TPF_lvn0_sw15 skip | band-rule passer | 2787 | +0.6 / -18% | -0.9 / +5% | +0.1 / +12% | +0.2 / -13% | +1.4 / +1.3 / -0.7 | +0.1 +0.3 -0.2 +0.1 +0.0 +0.3 |
| VAR TLP_p25_4h strMid skip A40 | band-rule passer | 1901 | -0.4 / -11% | +1.0 / -3% | -0.1 / -4% | +0.2 / -11% | +0.1 / -0.7 / -0.6 | +0.1 -0.5 +0.0 -0.0 +0.0 +0.0 |

## 12R combined lock
| cell | tag | rows | asia: mean / maxDD | london: mean / maxDD | nyam: mean / maxDD | nypm: mean / maxDD | Asia mean by vol tercile T1/T2/T3 | Asia mean by book (KB PE SM HM MV PB) |
|---|---|---|---|---|---|---|---|---|---|
| SHIPPED LAYER (8 lines: 7 x half at D20 + OTE-62 B73 D30) | shipped |  | +1.5 / -20% | -0.1 / +1% | +0.6 / -28% | -0.1 / +26% | -0.5 / +0.3 / +4.5 | +0.4 +0.5 -0.5 +1.0 +0.0 +0.0 |
| A40 TLQ_SES_asia half | small lead | 4643 | +0.2 / -9% | +0.8 / +0% | +0.3 / -7% | +0.1 / -7% | +0.5 / -0.1 / +0.3 | +0.1 +0.3 -0.3 +0.1 +0.0 +0.0 |
| A40 TLP_p25_4h skip | small lead | 5110 | -0.2 / +20% | +2.3 / -28% | +0.5 / -32% | +0.0 / -18% | -2.0 / -1.2 / +2.5 | +0.3 -0.8 -0.1 -0.2 +0.0 +0.6 |
| A40 TVP_poc_day skip | 12R lead only | 1768 | +0.8 / -9% | +2.4 / -0% | +0.3 / -43% | -0.0 / +1% | +2.0 / +0.5 / -0.3 | +0.3 +0.3 -0.2 +0.3 +0.0 +0.0 |
| A25 TCD_ext skip | band-rule passer | 11984 | -3.0 / -9% | +2.7 / -36% | +2.0 / -57% | +0.3 / -35% | -0.4 / -5.8 / -3.1 | -0.3 -2.8 +0.2 -0.0 +0.0 -0.1 |
| A30 TCD_ext skip | band-rule passer | 13563 | -2.6 / -9% | +3.0 / -29% | +2.0 / -57% | +0.3 / -38% | -0.9 / -4.4 / -2.7 | -0.2 -2.7 +0.1 +0.2 +0.0 -0.0 |
| A40 TCD_ext skip | band-rule passer | 15965 | -2.8 / -10% | +2.4 / -1% | +1.1 / -37% | +0.2 / -25% | -2.8 / -4.3 / -1.4 | -0.2 -2.6 +0.2 -0.2 +0.0 -0.0 |
| A30 TCD_ext half | band-rule passer | 13563 | -1.0 / -9% | +2.9 / -39% | +1.4 / -11% | +0.1 / -13% | -1.1 / -1.8 / -0.2 | +0.1 -1.8 +0.2 +0.0 +0.0 +0.4 |
| A40 TCD_ext half | band-rule passer | 15965 | -0.5 / -9% | +2.9 / -35% | +1.5 / -35% | +0.1 / -13% | -1.1 / -1.7 / +1.1 | +0.1 -1.2 +0.3 -0.1 +0.0 +0.4 |
| A50 TCD_ext half | band-rule passer | 17805 | -0.8 / -11% | +3.2 / -40% | +1.3 / -40% | +0.1 / -11% | -0.2 / -3.0 / +0.7 | +0.1 -1.2 +0.2 -0.1 +0.0 +0.3 |
| A60 TCD_ext half | band-rule passer | 19375 | -1.6 / -11% | +3.6 / -44% | +1.6 / -35% | -0.0 / -11% | -1.9 / -3.7 / +0.7 | +0.1 -1.7 -0.0 -0.3 +0.0 +0.4 |
| A20 TCD_cdlo skip | band-rule passer | 4170 | +0.2 / -6% | +0.4 / -13% | +1.0 / -8% | +0.1 / -21% | +0.8 / -4.2 / +3.6 | +0.4 -0.9 +0.0 +0.6 +0.0 +0.1 |
| A40 TCD_cdhi skip | band-rule passer | 8807 | -2.5 / -6% | +1.5 / -22% | +1.7 / -58% | +0.1 / -1% | -0.8 / -2.9 / -3.8 | -0.2 -1.8 +0.2 -0.6 +0.0 +0.0 |
| A20 TVP_lvn_sess skip | band-rule passer | 18233 | -2.4 / +39% | +0.8 / -20% | +0.3 / -14% | +0.4 / -51% | -3.8 / +1.3 / -4.4 | +0.4 -1.6 -0.4 -1.1 +0.0 +0.4 |
| A40 TPF_poc_sw15 skip | band-rule passer | 3485 | +0.5 / -1% | -0.6 / -6% | -0.4 / -1% | +0.1 / -10% | +1.7 / -1.4 / +1.1 | +0.3 +0.1 +0.2 -0.2 +0.0 +0.1 |
| A40 TPF_val_sess skip | band-rule passer | 3315 | -1.3 / +12% | -0.4 / -17% | -0.0 / -15% | +0.2 / -19% | -0.6 / -0.5 / -2.7 | +0.0 -0.2 -1.0 -0.1 +0.0 +0.1 |
| A10 TCD_ext skip | band-rule passer | 5592 | -2.6 / -0% | -0.3 / -1% | +0.5 / -26% | +0.2 / -1% | -0.1 / -2.9 / -4.9 | -0.1 -1.8 -0.0 -0.4 +0.0 -0.3 |
| A40 TPF_hvn0_sw15 skip | band-rule passer | 3357 | -0.8 / +4% | +0.3 / -5% | +0.3 / -48% | -0.1 / +11% | +1.0 / -0.8 / -2.6 | +0.2 -0.5 -0.2 -0.1 +0.0 -0.2 |
| A40 TPF_lvn0_sw15 skip | band-rule passer | 2787 | +0.5 / +3% | -0.2 / -5% | -0.1 / +5% | +0.3 / -29% | +0.7 / +0.4 / +0.4 | +0.1 +0.7 -0.4 -0.1 +0.0 +0.2 |

## Reading
* Asia carries the stack in 2026; the shipped layer's Asia effect and each candidate's Asia effect are in the first column pair of each table.
* The Asia-session cut of a candidate is compared with the same session in the shipped layer (first row): a tape line that helps Asia more than the shipped layer and in the calm AND volatile terciles would be the product-relevant one; none of the lock-none passers does this consistently (see the terciles).
