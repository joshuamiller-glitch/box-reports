# DS3_ZONES_3_HALF_FINAL_V13T - is any line worth SKIP vs HALF on PRE + L6M together, or is HALF D20 final? (Z1; 2026-11-02 14:08Z)

Base V13T = D7 V13Z with the five take lines OFF (lines=empty), lock none (per-book locks only), fill basis N, new cap 20261031. POST-HOC, no PASS, Shadow only. Prereg ZONES3_S1_addendum3_V13T_HALFFINAL (sha 15ce2722...) in DECISIONS.md. Drawdown first; windows L1M/L2M view only; worst-20 marked * when the window has < 20 weeks. "Left out" = the shipped HALF layer without that line (OTE-62: without its B73 D30 action). Episodes recomputed on V13T (largest drawdown episode of the shipped HALF layer in each window, ISO weeks peak..recovery) and removed from every variant before the cut is recomputed. Phase-averaged = trading days shifted 0..4 before bucketing into 5-day blocks. Equal-risk mean is the linear approximation (~).

## ANSWER
(answer pending)

## 1. Whole layer on V13T: NONE vs HALF vs SKIP
| window (weeks) | carrying episode of the HALF layer (ISO peak..trough, depth $k, recovered?) | NONE maxDD | HALF maxDD (cut) | SKIP maxDD (cut) | phase-avg maxDD NONE / HALF / SKIP | maxDD with the episode dropped: NONE / HALF / SKIP (cuts) | worst-20 NONE / HALF / SKIP | Calmar NONE / HALF / SKIP | mean $k/wk NONE / HALF / SKIP (HALF-NONE, SKIP-NONE MDE) | ulcer NONE / HALF / SKIP | CVaR5 NONE / HALF / SKIP | equal-risk mean d (~linear) HALF / SKIP |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1M (view) (5) | 202644..202644, 98, open | 99 | 98 (+2%) | 97 (+3%) | 97 / 93 / 91 | 8 / 33 (-315%) / 36 (-356%) | 86 / 64 / 60 * | 0.17 / 0.13 / 0.13 | 17.1 / 12.7 / 12.1 (-4.4, -5.0; 14.6) | 41 / 42 / 42 | -99 / -98 / -97 | -4.4 / -5.0 |
| L2M (view) (9) | 202644..202644, 98, open | 99 | 98 (+2%) | 97 (+3%) | 97 / 93 / 94 | 53 / 51 (+4%) / 68 (-28%) | 216 / 211 / 192 * | 0.24 / 0.24 / 0.22 | 24.0 / 23.4 / 21.3 (-0.6, -2.7; 8.9) | 38 / 38 / 40 | -99 / -98 / -97 | -0.6 / -2.7 |
| L3M (13) | 202644..202644, 98, open | 99 | 98 (+2%) | 97 (+3%) | 103 / 93 / 97 | 79 / 60 (+24%) / 82 (-3%) | 189 / 201 / 177 * | 0.15 / 0.16 / 0.14 | 14.6 / 15.5 / 13.7 (+0.9, -0.9; 6.6) | 46 / 39 / 46 | -99 / -98 / -97 | +0.9 / -0.9 |
| L6M (27) | 202629..202637, 132, recovered | 165 | 132 (+20%) | 159 (+4%) | 161 / 126 / 146 | 99 / 98 (+2%) / 97 (+3%) | 111 / 120 / 99 | 0.22 / 0.28 / 0.21 | 36.6 / 37.1 / 34.1 (+0.5, -2.5; 5.9) | 72 / 59 / 68 | -99 / -98 / -97 | +0.5 / -2.5 |
| HOLD (52) | 202606..202608, 139, recovered | 165 | 139 (+15%) | 159 (+4%) | 162 / 135 / 149 | 165 / 132 (+20%) / 159 (+4%) | -583 / -541 / -543 | 0.19 / 0.22 / 0.18 | 31.2 / 31.2 / 28.6 (-0.0, -2.6; 4.0) | 64 / 54 / 61 | -85 / -79 / -80 | +2.4 / -0.5 |
| MID (12) | 202607..202608, 51, recovered | 64 | 51 (+20%) | 60 (+5%) | 68 / 65 / 66 | 31 / 23 (+25%) / 19 (+40%) | 301 / 280 / 243 * | 0.39 / 0.46 / 0.34 | 25.1 / 23.3 / 20.2 (-1.8, -4.9; 9.7) | 21 / 19 / 22 | -37 / -38 / -45 | -1.8 / -4.9 |
| PRE (75) | 202435..202437, 166, recovered | 165 | 166 (-1%) | 155 (+6%) | 171 / 167 / 152 | 145 / 131 (+9%) / 129 (+11%) | -840 / -753 / -704 | 0.10 / 0.10 / 0.12 | 16.7 / 17.1 / 18.8 (+0.5, +2.1; 3.0) | 48 / 45 / 43 | -77 / -70 / -68 | +2.4 / +5.8 |
| X' (44) | 202342..202347, 91, recovered | 77 | 91 (-19%) | 105 (-38%) | 79 / 91 / 102 | 77 / 66 (+13%) / 51 (+33%) | -467 / -446 / -414 | 0.07 / 0.05 / 0.06 | 5.3 / 4.7 / 6.0 (-0.6, +0.7; 3.6) | 34 / 37 / 37 | -56 / -48 / -50 | -0.4 / +1.5 |

## 2. Placebos (100 draws per kind; A random-level same-count, B same-volume random, C shuffled-day)
| context | maxDD cut PRE / L6M / HOLD / MID / X' | placebo rank of the cut, A random-level / B same-volume / C shuffled-day: PRE | L6M | HOLD | MID | X' (n draws) |
|---|---|---|---|---|---|---|
| whole HALF layer vs zone off | -1% / +20% / +15% / +20% / -19% | 0.703/0.743/0.574 | 0.317/0.475/0.307 | 0.238/0.396/0.238 | 0.356/0.277/0.248 | 0.861/0.871/0.861 (100/100/100) |
| whole SKIP layer vs zone off | +6% / +4% / +4% / +5% / -38% | 0.386/0.446/0.327 | 0.624/0.653/0.634 | 0.505/0.535/0.545 | 0.584/0.535/0.653 | 0.891/0.812/0.861 (100/100/100) |
| kijun1h HALF (marginal vs left out) | +4% / +2% / -0% / -1% / -4% | 0.119/0.139/0.158 | 0.465/0.356/0.564 | 0.545/0.455/0.485 | 0.703/0.723/0.624 | 0.871/0.792/0.851 (100/100/100) |
| PDmid HALF (marginal vs left out) | +0% / +5% / +0% / +0% / -36% | 0.822/0.832/0.792 | 0.119/0.119/0.139 | 0.416/0.584/0.426 | 0.812/0.941/0.842 | 1.000/1.000/1.000 (100/100/100) |
| CRT4h HALF (marginal vs left out) | +1% / +8% / +14% / +31% / -23% | 0.594/0.406/0.653 | 0.218/0.198/0.178 | 0.079/0.030/0.059 | 0.030/0.040/0.010 | 0.960/0.980/0.980 (100/100/100) |
| KCup4h HALF (marginal vs left out) | +0% / +1% / +0% / +0% / -4% | 0.505/0.485/0.427 | 0.386/0.426/0.354 | 0.584/0.554/0.542 | 0.782/0.752/0.865 | 0.871/0.743/0.927 (100/100/95) |
| camH3 HALF (marginal vs left out) | +1% / +1% / -1% / -17% / -3% | 0.366/0.465/- | 0.277/0.436/- | 0.406/0.475/- | 0.970/0.931/- | 0.782/0.673/- (100/100/0) |
| OTE705 HALF (marginal vs left out) | -9% / +0% / -5% / -17% / +2% | 1.000/1.000/- | 0.727/0.613/- | 0.727/0.645/- | 1.000/0.903/- | 0.636/0.419/- (10/30/0) |
| OTE79 HALF (marginal vs left out) | -3% / +3% / -3% / -10% / +4% | -/-/- | -/-/- | -/-/- | -/-/- | -/-/- (0/0/0) |
| OTE62 as D20 HALF line (vs left out) | +1% / -15% / -5% / +13% / +1% | -/-/- | -/-/- | -/-/- | -/-/- | -/-/- (0/0/0) |

## 3. Per line: HALF vs SKIP vs left out (marginal-in-layer)
| line | action | maxDD cut vs the line left out: PRE / L6M / HOLD / MID / X' | same, carrying episode dropped: PRE / L6M | phase-avg maxDD $k PRE / L6M | mean d vs left-out $k/wk (MDE) PRE / L6M | worst-20 PRE b>a |
|---|---|---|---|---|---|---|
| kijun1h | HALF | +4% / +2% / -0% / -1% / -4% | +0% / +1% | 167 / 126 | +0.4 (1.2) / +0.1 (1.1) | -776 > -753 |
| kijun1h | SKIP | +13% / -2% / -6% / -17% / -2% | -1% / +3% | 149 / 130 | +1.2 (2.3) / -1.0 (2.9) | -776 > -719 |
| PDmid | HALF | +0% / +5% / +0% / +0% / -36% | -0% / +0% | 167 / 126 | -0.0 (0.4) / -0.2 (1.5) | -755 > -753 |
| PDmid | SKIP | +1% / +13% / +2% / +5% / -58% | -6% / -3% | 162 / 119 | -0.4 (1.2) / -1.7 (5.7) | -755 > -756 |
| CRT4h | HALF | +1% / +8% / +14% / +31% / -23% | +1% / -2% | 167 / 126 | +0.5 (1.0) / -0.0 (1.6) | -746 > -753 |
| CRT4h | SKIP | +2% / +2% / -0% / -0% / -7% | -7% / -5% | 164 / 134 | +1.4 (2.0) / -0.5 (3.0) | -746 > -759 |
| KCup4h | HALF | +0% / +1% / +0% / +0% / -4% | +4% / +0% | 167 / 126 | +0.4 (1.5) / +0.1 (0.3) | -765 > -753 |
| KCup4h | SKIP | +1% / +1% / +0% / +0% / -11% | +5% / -0% | 164 / 125 | +0.2 (2.1) / +0.2 (1.2) | -765 > -743 |
| camH3 | HALF | +1% / +1% / -1% / -17% / -3% | +4% / +0% | 167 / 126 | +0.1 (1.0) / -0.2 (1.0) | -773 > -753 |
| camH3 | SKIP | +4% / -8% / -5% / -23% / -10% | +16% / +0% | 163 / 136 | +0.4 (2.4) / -0.7 (2.3) | -773 > -721 |
| OTE705 | HALF | -9% / +0% / -5% / -17% / +2% | -4% / +2% | 167 / 126 | +0.2 (1.0) / -0.0 (2.1) | -745 > -753 |
| OTE705 | SKIP | -5% / -8% / -8% / -24% / -3% | -9% / +2% | 161 / 136 | +0.2 (2.2) / +0.2 (3.4) | -745 > -722 |
| OTE79 | HALF | -3% / +3% / -3% / -10% / +4% | +0% / +1% | 167 / 126 | -0.1 (0.9) / +1.8 (4.4) | -740 > -753 |
| OTE79 | SKIP | -5% / -15% / -15% / -14% / -1% | -2% / +4% | 170 / 145 | +0.2 (2.1) / +1.5 (4.9) | -740 > -737 |
| OTE62 | HALF D20 | +1% / -15% / -5% / +13% / +1% | +1% / +7% | 163 / 147 | -0.2 (0.8) / -0.9 (2.1) | -755 > -747 |
| OTE62 | SKIP D20 | -1% / -44% / -31% / +15% / +18% | +2% / -4% | 166 / 180 | -0.7 (2.4) / -3.1 (5.3) | -755 > -779 |

## 4. SKIP instead of HALF per line (gain over HALF; placebo = same number of random rows skipped instead)
| line | SKIP - HALF maxDD cut (pp), carrying episode dropped: PRE / L6M | not dropped: PRE / L6M / HOLD / MID / X' | mean d SKIP-HALF $k/wk (MDE) PRE / L6M | random-row skip placebo (same row count skipped instead; share of draws with at least this gain A / B (n)): PRE / L6M | worth SKIP? (rule: both PRE and L6M > +3 pp with the episode dropped, mean not below -0.5 MDE, placebo rank <= 0.10) |
|---|---|---|---|---|---|
| kijun1h | -2.0 / +1.9 | +9.6 / -4.5 / -5.1 / -15.3 / +2.3 | +0.8 (1.3) / -1.3 (2.5) | A - / - ; B - / - (0/0) | no |
| PDmid | -5.5 / -3.0 | +1.1 / +8.7 / +2.3 / +4.9 / -16.3 | -0.5 (0.9) / -3.2 (7.0) | A - / - ; B - / - (0/0) | no |
| CRT4h | -7.9 / -2.3 | +1.3 / -6.2 / -16.8 / -45.7 / +13.0 | +1.1 (1.5) / -0.3 (2.2) | A - / - ; B - / - (0/0) | no |
| KCup4h | +1.6 / -0.1 | +0.4 / +0.3 / +0.0 / +0.0 / -6.8 | -0.3 (1.5) / -0.0 (1.3) | A - / - ; B - / - (0/0) | no |
| camH3 | +12.6 / +0.0 | +2.5 / -9.2 / -3.6 / -5.2 / -7.4 | +0.5 (1.8) / +0.2 (1.7) | A - / - ; B - / - (0/0) | no |
| OTE705 | -4.8 / +0.0 | +4.2 / -8.0 / -2.6 / -6.2 / -4.7 | -0.1 (2.0) / +1.3 (3.0) | A - / - ; B - / - (0/0) | no |
| OTE79 | -2.0 / +2.6 | -1.7 / -18.1 / -12.1 / -4.1 / -5.5 | +0.5 (1.6) / +0.4 (1.9) | A - / - ; B - / - (0/0) | no |
| OTE62 | +0.4 / -12.2 | -1.8 / -25.2 / -25.2 / +1.8 / +17.8 | -0.5 (2.1) / -0.6 (5.1) | A - / - ; B - / - (0/0) | no |

## 5. D sensitivity (10 / 15 / 20 / 25 / 30 pts = D +-25 / 50%)
| line | action | PRE cut vs left out at D = 10 / 15 / 20 / 25 / 30 | L6M cut at D = 10 / 15 / 20 / 25 / 30 | verdict |
|---|---|---|---|---|
| kijun1h | HALF | +0% / +4% / +4% / +4% / +7% | +1% / -0% / +2% / +1% / -5% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| kijun1h | SKIP | -1% / +7% / +13% / +10% / +16% | +4% / -4% / -2% / -9% / -16% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| PDmid | HALF | +0% / +0% / +0% / +0% / +4% | +3% / +5% / +5% / +5% / +2% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| PDmid | SKIP | -1% / -1% / +1% / +1% / +10% | +6% / +12% / +13% / +5% / +1% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| CRT4h | HALF | +0% / +1% / +1% / +1% / -1% | +3% / +10% / +8% / +9% / +6% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| CRT4h | SKIP | -0% / +1% / +2% / +2% / +2% | +1% / +12% / +2% / +12% / +11% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| KCup4h | HALF | +0% / +0% / +0% / +0% / +0% | +1% / +1% / +1% / -1% / +3% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| KCup4h | SKIP | +0% / +0% / +1% / +1% / +1% | +2% / +2% / +1% / -2% / +6% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| camH3 | HALF | +0% / -1% / +1% / +1% / -0% | +2% / +2% / +1% / +8% / +7% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| camH3 | SKIP | +1% / -0% / +4% / +4% / +1% | +2% / +2% / -8% / -2% / -14% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| OTE705 | HALF | -5% / -9% / -9% / -15% / -15% | -2% / -5% / +0% / -6% / -16% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| OTE705 | SKIP | -5% / -7% / -5% / -11% / -11% | -6% / -8% / -8% / -21% / -50% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| OTE79 | HALF | -4% / -4% / -3% / -4% / -4% | -2% / -1% / +3% / -2% / -4% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| OTE79 | SKIP | -10% / -8% / -5% / -7% / -2% | -0% / -10% / -15% / -19% / -21% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| OTE62 | HALF | +0% / -0% / +1% / -7% / -7% | -5% / -13% / -15% / -15% / -15% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| OTE62 | SKIP | -0% / -1% / -1% / -8% / -11% | -8% / -23% / -44% / -49% / -45% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |

## 6. One-at-a-time (line alone vs zone off)
| line | alone vs zone off: HALF cut PRE / L6M / HOLD / MID / X' | SKIP cut PRE / L6M / HOLD / MID / X' |
|---|---|---|
| kijun1h | +8% / +5% / +5% / +8% / -0% | +11% / +11% / +11% / +37% / -10% |
| PDmid | +5% / +8% / +3% / +2% / -3% | +5% / +15% / +5% / +6% / -18% |
| CRT4h | +1% / +13% / +13% / +45% / +1% | -3% / +4% / +3% / +3% / +4% |
| KCup4h | +0% / +1% / +1% / +0% / +0% | +1% / +0% / +0% / +0% / +3% |
| camH3 | +2% / -3% / -3% / -9% / +3% | +5% / -17% / -17% / -14% / +3% |
| OTE705 | -10% / -1% / -1% / -4% / +12% | -5% / -9% / -9% / -7% / +13% |
| OTE79 | -2% / -0% / -0% / -3% / -4% | -4% / -16% / -16% / -9% / -4% |
| OTE62 | -0% / -14% / -14% / +9% / +9% | -3% / -25% / -25% / +12% / +10% |
