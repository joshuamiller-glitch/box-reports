# DS3_ZONES_3_L2_TAPE_LP_AGAINST - flag #2 (large print AGAINST the trade): multiplicity null, overlap with ZL-1's BT swing flip, time structure, walk-forward (ZL-2, D7 V13Y)

Rule `LP_AGAINST_25_4h_D40`: skip when a fresh single print >= 25 contracts of the last 4 h whose aggressor side is OPPOSITE to the trade lies between entry and target within min(40 pts, target distance): 2,614 of 88,490 engine rows. Statistic everywhere: SAVED DOLLARS = minus the sum of the V13Y realised net $ of the TAKEN rows the rule would skip ($k). Post-hoc, Shadow only.

## 1. Multiplicity null (ZL-1 bnull2 method): 2001 same-density families
Null families (667 each): OFFSET (every >=25-lot print level shifted by U(-80,+80) pts), SHUFFLED-DAY (each print takes the offset-from-price of a random print of another label day), SIDEFLIP (each print's aggressor side flipped at random). Each is pushed through the same rule (fresh, 4 h, opposite side, D40) and thinned to about the real row count (median 2789 rows vs 2,614). Rank = share of null families whose statistic is >= the real one (small = real beats the nulls).
| frame | statistic | real ($k) | null median | null p95 | null p99 | null max | rank vs ALL | vs offset | vs shuffled-day | vs side-flip |
|---|---|---|---|---|---|---|---|---|---|---|
| lock none | L6M | +76.7 | +32.2 | +72.7 | +90.1 | +108.1 | 0.039 | 0.001 | 0.046 | 0.070 |
| lock none | HOLD | +90.6 | +46.0 | +106.0 | +127.8 | +164.4 | 0.120 | 0.010 | 0.267 | 0.084 |
| lock none | PRE | +73.1 | +3.1 | +73.0 | +101.0 | +148.5 | 0.050 | 0.001 | 0.130 | 0.018 |
| lock none | X' | -4.2 | -15.9 | +47.4 | +74.9 | +135.6 | 0.376 | 0.345 | 0.354 | 0.430 |
| lock none | min(L6M,HOLD,PRE) | +73.1 | -3.1 | +49.0 | +65.6 | +91.0 | 0.004 | 0.000 | 0.007 | 0.004 |
| lock none | min(L6M,HOLD,PRE,X') | -4.2 | -31.8 | +18.2 | +37.6 | +63.1 | 0.201 | 0.019 | 0.276 | 0.309 |
| 12R | L6M | +46.1 | +18.4 | +50.9 | +64.5 | +76.7 | 0.086 | 0.012 | 0.088 | 0.157 |
| 12R | HOLD | +59.8 | +25.3 | +74.5 | +92.4 | +127.4 | 0.123 | 0.021 | 0.241 | 0.108 |
| 12R | PRE | +95.3 | +38.9 | +96.4 | +118.1 | +150.6 | 0.053 | 0.000 | 0.070 | 0.090 |
| 12R | X' | -4.6 | -9.1 | +51.4 | +78.6 | +119.9 | 0.452 | 0.457 | 0.649 | 0.250 |
| 12R | min(L6M,HOLD,PRE) | +46.1 | +6.5 | +44.3 | +55.7 | +68.0 | 0.041 | 0.000 | 0.040 | 0.082 |
| 12R | min(L6M,HOLD,PRE,X') | -4.6 | -24.2 | +21.5 | +33.4 | +51.8 | 0.282 | 0.049 | 0.573 | 0.225 |

Reading: over L6M, HOLD and PRE the rule saves $73k at the minimum (lock none) and only 0.4% of the null families do as well (4.1% in 12R); once X' is included (it saves -$4k, the skipped X' rows are break-even) the rank is 0.20 (lock none) / 0.28 (12R). **Multiplicity:** the number of cells/definitions I looked at is about 760 (583 screened cells + 36 large-print variants + the 144-setting grid); for the best of n tests a single-rule rank of 0.004 becomes 1-(1-0.004)^760 = 0.95: **not significant after the search**, and not significant at all when X' is in the statistic. The aggressor-side-flipped version of the same rule (the print's aggressor = trade side, the real rule with sides swapped) saves only $17k / $19k in L6M / HOLD and LOSES $72k in PRE: the effect is specific to the OPPOSITE aggressor.

## 2. Overlap and union with ZL-1's BT swing flip (V13Y taken trades; BT mask F10 4h D40 from ZL-1)
Rows (all engine rows): LP_against 2,614, BT 2,819, intersection 212, Jaccard 0.04. Among taken trades the Jaccard is 0.01-0.08: the two rules flag almost entirely different trades. Saved $k (lock none | 12R):
| window | LP alone | BT alone | UNION | INTERSECTION | Jaccard (taken) | share of LP rows in BT | 12R: LP | BT | UNION |
|---|---|---|---|---|---|---|---|---|---|
| L3M | +36.7 | +30.4 | +68.5 | -1.3 | 0.01 | 4% | +31.2 | +24.8 | +57.3 |
| L6M | +76.7 | +69.8 | +144.9 | +1.5 | 0.02 | 5% | +46.1 | +70.1 | +114.7 |
| HOLD | +90.6 | +74.9 | +170.9 | -5.3 | 0.03 | 7% | +59.8 | +107.1 | +170.7 |
| MID | -1.1 | +17.9 | +17.4 | -0.7 | 0.06 | 15% | +3.4 | +47.3 | +52.7 |
| PRE | +73.1 | +103.4 | +169.6 | +6.9 | 0.07 | 19% | +95.3 | +123.1 | +213.3 |
| X' | -4.2 | +50.1 | +37.3 | +8.6 | 0.07 | 14% | -4.6 | +66.3 | +60.9 |
Per year (saved $k, lock none): 2023: LP -4.2 / BT +56.9 / union +34.6; 2024: LP +54.9 / BT +29.3 / union +92.4; 2025: LP +8.5 / BT +28.0 / union +37.4; 2026: LP +78.7 / BT +89.2 / union +167.0. 12R: 2023: LP -4.0 / BT +64.1 / union +51.5; 2024: LP +55.9 / BT +83.9 / union +146.4; 2025: LP +33.1 / BT +16.8 / union +49.7; 2026: LP +54.7 / BT +122.4 / union +177.6.
The union saves almost exactly the sum of the two (HOLD $171k = 91 + 75 - 5 overlap): independent information. BT is stronger in 2023 and PRE, LP_against in 2024 and 2026.

## 3. Time structure, books/sessions, and the exits
Saved $k per quarter (lock none; rows skipped and their mean $ vs the other taken rows): 2023Q2 -2.2 (35 rows, +62/row vs -19); 2023Q3 -15.5 (43 rows, +361/row vs +1); 2023Q4 +13.6 (57 rows, -238/row vs +79); 2024Q1 -13.3 (48 rows, +278/row vs +97); 2024Q2 +7.0 (47 rows, -149/row vs +115); 2024Q3 +46.6 (52 rows, -897/row vs +157); 2024Q4 +14.6 (19 rows, -770/row vs +161); 2025Q1 +19.3 (39 rows, -494/row vs +11); 2025Q2 -1.1 (38 rows, +28/row vs +210); 2025Q3 -22.5 (42 rows, +537/row vs +215); 2025Q4 +12.8 (54 rows, -238/row vs +205); 2026Q1 +0.7 (58 rows, -12/row vs +75); 2026Q2 +26.8 (65 rows, -413/row vs +316); 2026Q3 +28.0 (55 rows, -508/row vs +70); 2026Q4 +23.3 (25 rows, -931/row vs +145). Positive in 10 of 15 quarters; the negative ones are 2023Q2-Q3, 2024Q1 and 2025Q2-Q3.

Saved $k by book x session (lock none, all years): 
| book | asia | london | nyam | nypm |
|---|---|---|---|---|
| HM | +11.0 | -0.0 | -1.8 | -0.0 |
| KB | +14.9 | +18.8 | -20.2 | +17.2 |
| MV | -0.0 | +2.9 | -0.6 | -0.0 |
| PB | -4.1 | -0.0 | -0.0 | -0.0 |
| PE | +15.9 | +71.9 | -2.3 | -0.0 |
| SM | +8.6 | +5.6 | -0.0 | -0.0 |
PE London carries $72k of the $107k total, KB Asia/London/NY-PM +$51k offset by KB NY-AM -$20k.

Are the skipped losers already cut early by the take / loss-cut lines? (mean V13Y realised $ per taken row, rows taken in all three runs)
| window | group | rows | V13Y full | take lines OFF | take lines AND TH-L2 loss cut OFF |
|---|---|---|---|---|---|
| L6M | LP_against rows | 90 | -603 | -323 | +79 |
| L6M | other rows | 3353 | +205 | +269 | +229 |
| HOLD | LP_against rows | 169 | -254 | -115 | -152 |
| HOLD | other rows | 5881 | +207 | +260 | +260 |
| PRE | LP_against rows | 194 | -359 | -240 | -618 |
| PRE | other rows | 5410 | +169 | +232 | +294 |
| X' | LP_against rows | 130 | +72 | +27 | +175 |
| X' | other rows | 2216 | +28 | +65 | +47 |
Reading: the LP_against rows lose in L6M/HOLD/PRE with the exit lines OFF too (-$115 to -$618 per row in HOLD/PRE), so the shipped exits do not "already cure" them; with the lines ON they lose MORE in L6M (-$603 vs -$323), i.e. the take lines/loss cut do not rescue them. (The engine record's exit field is not comparable to the library bracket exit, so a direct "exited early" share could not be read.)

## 4. Walk-forward restricted to the smaller family (purged, 34 months 2024-01..2026-10, trailing 12 months, engine-free scoring on V13Y realised $)
| family | policy | OOS excess $ over random skipping | t | positive months | 2024 | 2025 | 2026 |
|---|---|---|---|---|---|---|---|
| opposite side, size 10/25/50 x window 1h/4h/24h x reach 20/40/60 (27 settings) | trailing-12m choice | +87902 | 0.48 | 19/34 | +30445 | +88730 | -31273 |
| opposite side, size 10/25/50 x window 1h/4h/24h x reach 20/40/60 (27 settings) | fixed T25 4h D40 | +236780 | 3.51 | 25/34 | +83778 | +40206 | +112795 |
| opposite side, size 10/25/50 x window 1h/4h/24h x reach 20/40/60 (27 settings) | random setting | +226138 | 1.95 | 22/34 | +130349 | +52413 | +43377 |
| opposite side, size 25/50 only (18 settings: no volume-heavy 10-lot drift) | trailing-12m choice | +223160 | 2.95 | 21/34 | +72735 | +16748 | +133677 |
| opposite side, size 25/50 only (18 settings: no volume-heavy 10-lot drift) | fixed T25 4h D40 | +236780 | 3.51 | 25/34 | +83778 | +40206 | +112795 |
| opposite side, size 25/50 only (18 settings: no volume-heavy 10-lot drift) | random setting | +167082 | 2.23 | 22/34 | +121795 | -23261 | +68549 |
Reading: with the 10-lot settings in the family the selection drifts to them and the choice earns little (+$88k, t 0.5); restricted to 25/50-lot settings the trailing-12-month CHOICE earns +$223k (t 2.95, 21/34 months) and is positive in 2024, 2025 and 2026 - the fixed rule earns +$237k (t 3.5). The out-of-sample benefit of the definition is therefore real in the dollar-per-row sense on 2024-26; it is a 2024-26 effect (X' is flat), and after the multiplicity of the search it has an adjusted p of about 0.95 on the minimum statistic.

## 5. Verdict
Flag #2 is a genuine row-level finding on 2024-26 (skipped rows lose money in L6M, HOLD and PRE, with the exit lines on or off, in every year since 2024, independent of BT's rows, specific to the opposite aggressor), and it does NOT clear the best-of-N multiplicity bar once X' is included or the search size is counted. Label: LEAD (Shadow) - keep it in the forward log (ZL2_LP25_4H_D40, now with the side field), do not act on it.
