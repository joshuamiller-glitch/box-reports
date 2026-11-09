# DS3_TH_STATE_S3_SIZER - S3: Q1-A vs the ER ladder on the TH-L2-S engine base (S345-RUN, 2026-11-09)

**Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched (entry match being closed by ENTRY-MATCH); in-sample base; PRE-PROOF**

**Summary (S1-COMB; windows as of 2026-10-31; carrying weeks dropped; drawdown first; no PASS words; preregistered in DS3_TH_STATE_S345_PREREG.md, sha in DECISIONS.md)**
- Q1-A vs the ladder (cells L, B, C): Q1-A has the shallowest maxDD. First-order, L deepens maxDD by 42 / 30 / 49 / 27% (L6M / HOLD / PRE / X'), B by 72 / 65 / 52 / 67%, C (sizer off) by 60 / 39 / 9 / 70%; so Q1-A is shallower than L by 30 / 23 / 33 / 21%. Same direction as the published V13T comparison (Q1-A vs L PA9 +38.0 L6M, +43.5 PRE) and as OLD-BASE (+14.6 / +34.2), smaller than V13T. Same sign on S1-UNIF and PLAIN6060.
- EXACT re-runs (new subclass state_sizer.py, regression identical at default lots; 5 cells = all non-reference cells; windows L1M-L6M, HOLD, MID complete, PRE and X' still running in the background): L deepens maxDD by 109 / 47 / 40% (L6M / HOLD / MID), B by 118 / 75 / 75%, C by 21 / 37 / 37%. The exact d mean is NOT the first-order d mean: L -4.1k / -1.2k per week (first-order +10.6k / +8.2k), B -0.9k / +2.2k (+21.1k / +13.6k), C -0.4k / -0.7k (+10.5k / +5.3k) on L6M / HOLD. The first-order scaling overstates the gain of up-size cells by 11-22k/wk on L6M (caps, locks, sliced fills, TH timing do not scale per lot); its DD ranking agrees with the exact one.
- Best cell overall by drawdown first: ZL-1 vol-target (down-only on Q1-A). First-order cut +19.5 / +20.4 / +22.7 / +29.6% (L6M / HOLD / PRE / X'), exact +16.5 / +13.9% (L6M / HOLD, MID +13.9%); mean -1.4k / -1.7k per week (exact L6M / HOLD) so it is not strict mean-keeping; placebo ranks (cut) 0.91 / 0.80 (L6M / PRE) are below 0.95; the tolerant gate on its increment fails (L3M / L6M increment mean negative). Mean-keeping best = Q1-A itself (the MV-London override moves nothing: exact +3.5% L6M, -1.9% HOLD, mean about 0).
- Best cell per book (Tables 3 and 5): exact, HM, MV and SM take the vol-target; KB, OD, PB and PE stay at Q1-A (every alternative deepens a window). First-order per-book picks are in Table 3 of each base.
- Versus the published near-misses: ZL-1 vol-target published cut +35.7 / +17.4% (L6M / PRE carry-dropped), mean -0.3k / -2.6k -> new base same sign (cut > 0 both windows, mean below Q1-A), cut smaller on L6M and larger on PRE; S1B(A) MV-london published +3.8 / +5.0% -> new +1.7 / +2.4% first-order, +3.5% exact L6M (inside noise on both). The S3 triple (ers_5m_20 + rv_pct_5d + er_3m_14) is not ported (features keyed to the V13T rows).
- Held-out live week (first-order): all cells win every day (maxDD 0); Q1-A $104.8k, L $149.2k, B $178.2k, C $133.8k, ZL-1 $79.1k: the week cannot separate cells on drawdown and favours up-size (and first-order overstates it).
- Not done / caveats: PRE and X' exact windows pending (background job); equal-risk lscale scan, PA9, walk-forward and exposure table are not ported (blocker 3 of S345_PREP); L2M and L3M coincide once the carrying weeks 202629-202639 are dropped; entries not live-matched.


## S1-COMB (21067 trades; lot chain reproduced for 93.7% of trades)

Table 1 (S1-COMB): $/week mean | maxDD | cut vs Q1-A (+ = shallower maxDD) | d mean vs Q1-A, carrying weeks dropped. Cells are FIRST-ORDER estimates (pnl per planned lot x new lots). [Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched (entry match being closed by ENTRY-MATCH); in-sample base; PRE-PROOF]

| cell | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|--|--|--|--|--|--|--|--|--|
| Q1-A (ref) | +14427 / 54881 / +0.0% / +0 | +20837 / 54881 / +0.0% / +0 | +20837 / 54881 / +0.0% / +0 | +29662 / 60492 / +0.0% / +0 | +17842 / 102765 / +0.0% / +0 | +12530 / 102765 / +0.0% / +0 | +16103 / 146318 / +0.0% / +0 | +3475 / 69227 / +0.0% / +0 |
| L (x0.5/x1.5) | +18541 / 86080 / -56.8% / +4114 | +25605 / 86080 / -56.8% / +4767 | +25605 / 86080 / -56.8% / +4767 | +40229 / 86080 / -42.3% / +10567 | +26087 / 133982 / -30.4% / +8246 | +21570 / 126306 / -22.9% / +9040 | +24013 / 217315 / -48.5% / +7911 | +5045 / 87610 / -26.6% / +1570 |
| B (x1/x1.5) | +25226 / 87423 / -59.3% / +10798 | +35739 / 87423 / -59.3% / +14902 | +35739 / 87423 / -59.3% / +14902 | +50752 / 104260 / -72.4% / +21090 | +31429 / 169799 / -65.2% / +13588 | +23270 / 157220 / -53.0% / +10740 | +27394 / 222969 / -52.4% / +11291 | +5489 / 115580 / -67.0% / +2014 |
| C (sizer off) | +21111 / 56224 / -2.4% / +6684 | +30972 / 56224 / -2.4% / +10135 | +30972 / 56224 / -2.4% / +10135 | +40185 / 96733 / -59.9% / +10523 | +23183 / 142361 / -38.5% / +5342 | +14229 / 142361 / -38.5% / +1699 | +19483 / 159914 / -9.3% / +3381 | +3920 / 117720 / -70.1% / +445 |
| MV-london ER<0.50 x0.5 | +14507 / 55423 / -1.0% / +80 | +20697 / 55423 / -1.0% / -140 | +20697 / 55423 / -1.0% / -140 | +29825 / 59454 / +1.7% / +163 | +18046 / 101109 / +1.6% / +205 | +12342 / 101109 / +1.6% / -188 | +15993 / 142753 / +2.4% / -110 | +3633 / 69675 / -0.6% / +158 |
| ZL-1 vol-target | +14630 / 48690 / +11.3% / +202 | +17796 / 48690 / +11.3% / -3041 | +17796 / 48690 / +11.3% / -3041 | +28373 / 48690 / +19.5% / -1289 | +17065 / 81760 / +20.4% / -777 | +10863 / 81760 / +20.4% / -1668 | +14918 / 113174 / +22.7% / -1185 | +3678 / 48765 / +29.6% / +203 |

L2M and L3M coincide after the carrying weeks 202629-202639 are dropped (same weeks remain); L1M differs only through the partial weeks at the window edge.

Table 2 (S1-COMB): drawdown-first / tolerant gate on the increment (cell minus Q1-A) / placebo (100 draws: permute the cell-to-Q1-A lot ratios within book x session; rank = share of draws with a smaller cut or mean) / equal-DD mean (cell mean x HOLD maxDD(Q1-A)/HOLD maxDD(cell); Q1-A: 29662 / 17842 / 16103). [Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched (entry match being closed by ENTRY-MATCH); in-sample base; PRE-PROOF]

| cell | dd_first_ok | tolerant_incr | cut_L6M | cut_HOLD | cut_PRE | cut_X' | rank_cut_L6M | rank_cut_PRE | rank_mean_L6M | rank_mean_PRE | share_changed | eq-DD mean L6M/HOLD/PRE |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| L (x0.5/x1.5) | False | True | -42.3 | -30.4 | -48.5 | -26.6 | 0.28 | 0.01 | 0.87 | 1.00 | 0.41 | 30856 / 20009 / 18418 |
| B (x1/x1.5) | False | True | -72.3 | -65.2 | -52.4 | -67.0 | 0.69 | 1.00 | 0.58 | 0.51 | 0.79 | 30716 / 19021 / 16579 |
| C (sizer off) | False | True | -59.9 | -38.5 | -9.3 | -70.0 | 0.43 | 0.99 | 0.32 | 0.01 | 0.39 | 29008 / 16735 / 14064 |
| MV-london ER<0.50 x0.5 | True | False | 1.7 | 1.6 | 2.4 | -0.65 | 0.60 | 0.75 | 0.42 | 0.18 | 0.02 | 30313 / 18342 / 16255 |
| ZL-1 vol-target | True | False | 19.5 | 20.4 | 22.6 | 29.6 | 0.91 | 0.80 | 0.85 | 0.76 | 0.18 | 35662 / 21449 / 18750 |

Q1-A vs L (the published Q1 comparison): Q1-A maxDD is shallower than L by +29.7% / +23.3% / +32.7% / +21.0% (L6M / HOLD / PRE / X') at a cost of +10567 $/week mean (L6M).

Table 3 (S1-COMB): best cell per book (cells scored: Q1-A, L, B, C, MV-london override, ZL-1; the override and the vol-target are in the per-book rows as they act; Q1-A itself wins a book where every alternative deepens a window). [Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched (entry match being closed by ENTRY-MATCH); in-sample base; PRE-PROOF]

| book | best cell (drawdown first: max of min cut L6M/HOLD/PRE) | min cut % | cut L6M/HOLD/PRE % | best L6M Calmar cell | Q1-A L6M mean/wk |
|--|--|--|--|--|--|
| HM | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | ZL-1 vol-target | +2699 |
| KB | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | L (x0.5/x1.5) | +5725 |
| MV | MV-london ER<0.50 x0.5 | 14.3 | +14.8 / +14.3 / +16.0 | ZL-1 vol-target | -1914 |
| OD | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | L (x0.5/x1.5) | -252 |
| PB | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | Q1-A (ref) | +1052 |
| PE | ZL-1 vol-target | 0.30 | +0.3 / +32.0 / +25.8 | C (sizer off) | +20897 |
| SM | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | L (x0.5/x1.5) | +1455 |

## S1-UNIF (19746 trades; lot chain reproduced for 93.8% of trades)

Table 1 (S1-UNIF): $/week mean | maxDD | cut vs Q1-A (+ = shallower maxDD) | d mean vs Q1-A, carrying weeks dropped. Cells are FIRST-ORDER estimates (pnl per planned lot x new lots). [Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched (entry match being closed by ENTRY-MATCH); in-sample base; PRE-PROOF]

| cell | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|--|--|--|--|--|--|--|--|--|
| Q1-A (ref) | -3142 / 82746 / +0.0% / +0 | +7815 / 82746 / +0.0% / +0 | +7815 / 82746 / +0.0% / +0 | +20019 / 86991 / +0.0% / +0 | +15465 / 121584 / +0.0% / +0 | +15348 / 121584 / +0.0% / +0 | +15579 / 133766 / +0.0% / +0 | +3991 / 77094 / +0.0% / +0 |
| L (x0.5/x1.5) | -4262 / 123066 / -48.7% / -1120 | +10943 / 123066 / -48.7% / +3128 | +10943 / 123066 / -48.7% / +3128 | +29701 / 123066 / -41.5% / +9682 | +25855 / 155763 / -28.1% / +10390 | +27290 / 155763 / -28.1% / +11941 | +23097 / 218972 / -63.7% / +7519 | +5387 / 88469 / -14.8% / +1396 |
| B (x1/x1.5) | -3163 / 125795 / -52.0% / -21 | +14152 / 125795 / -52.0% / +6336 | +14152 / 125795 / -52.0% / +6336 | +32867 / 152613 / -75.4% / +12848 | +25903 / 193011 / -58.7% / +10438 | +27004 / 193011 / -58.7% / +11656 | +26464 / 196189 / -46.7% / +10885 | +6248 / 133661 / -73.4% / +2257 |
| C (sizer off) | -2043 / 85475 / -3.3% / +1099 | +11024 / 85475 / -3.3% / +3209 | +11024 / 85475 / -3.3% / +3209 | +23185 / 147874 / -70.0% / +3166 | +15513 / 185903 / -52.9% / +48 | +15063 / 185903 / -52.9% / -285 | +18945 / 110983 / +17.0% / +3366 | +4852 / 127719 / -65.7% / +861 |
| MV-london ER<0.50 x0.5 | -2522 / 79507 / +3.9% / +620 | +8338 / 79507 / +3.9% / +523 | +8338 / 79507 / +3.9% / +523 | +20508 / 87762 / -0.9% / +489 | +15438 / 124155 / -2.1% / -27 | +14352 / 124155 / -2.1% / -996 | +15633 / 127080 / +5.0% / +54 | +4210 / 76063 / +1.3% / +219 |
| ZL-1 vol-target | +107 / 63149 / +23.7% / +3249 | +7474 / 63149 / +23.7% / -341 | +7474 / 63149 / +23.7% / -341 | +21468 / 63149 / +27.4% / +1449 | +14765 / 109466 / +10.0% / -700 | +11961 / 109466 / +10.0% / -3387 | +14406 / 93110 / +30.4% / -1173 | +3189 / 48923 / +36.5% / -803 |

L2M and L3M coincide after the carrying weeks 202629-202639 are dropped (same weeks remain); L1M differs only through the partial weeks at the window edge.

Table 2 (S1-UNIF): drawdown-first / tolerant gate on the increment (cell minus Q1-A) / placebo (100 draws: permute the cell-to-Q1-A lot ratios within book x session; rank = share of draws with a smaller cut or mean) / equal-DD mean (cell mean x HOLD maxDD(Q1-A)/HOLD maxDD(cell); Q1-A: 20019 / 15465 / 15579). [Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched (entry match being closed by ENTRY-MATCH); in-sample base; PRE-PROOF]

| cell | dd_first_ok | tolerant_incr | cut_L6M | cut_HOLD | cut_PRE | cut_X' | rank_cut_L6M | rank_cut_PRE | rank_mean_L6M | rank_mean_PRE | share_changed | eq-DD mean L6M/HOLD/PRE |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| L (x0.5/x1.5) | False | True | -41.5 | -28.1 | -63.7 | -14.8 | 0.30 | 0.00 | 0.91 | 1.00 | 0.42 | 23184 / 20182 / 18029 |
| B (x1/x1.5) | False | True | -75.4 | -58.8 | -46.7 | -73.4 | 0.52 | 1.00 | 0.37 | 0.56 | 0.79 | 20704 / 16317 / 16670 |
| C (sizer off) | False | True | -70.0 | -52.9 | 17.0 | -65.7 | 0.21 | 1.00 | 0.12 | 0.02 | 0.38 | 15164 / 10146 / 12390 |
| MV-london ER<0.50 x0.5 | False | True | -0.89 | -2.1 | 5.0 | 1.34 | 0.34 | 0.89 | 0.85 | 0.54 | 0.03 | 20083 / 15119 / 15309 |
| ZL-1 vol-target | True | False | 27.4 | 10.0 | 30.4 | 36.5 | 0.99 | 0.94 | 0.98 | 0.69 | 0.18 | 23845 / 16400 / 16001 |

Q1-A vs L (the published Q1 comparison): Q1-A maxDD is shallower than L by +29.3% / +21.9% / +38.9% / +12.9% (L6M / HOLD / PRE / X') at a cost of +9682 $/week mean (L6M).

Table 3 (S1-UNIF): best cell per book (cells scored: Q1-A, L, B, C, MV-london override, ZL-1; the override and the vol-target are in the per-book rows as they act; Q1-A itself wins a book where every alternative deepens a window). [Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched (entry match being closed by ENTRY-MATCH); in-sample base; PRE-PROOF]

| book | best cell (drawdown first: max of min cut L6M/HOLD/PRE) | min cut % | cut L6M/HOLD/PRE % | best L6M Calmar cell | Q1-A L6M mean/wk |
|--|--|--|--|--|--|
| HM | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | ZL-1 vol-target | +1095 |
| KB | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | L (x0.5/x1.5) | +4962 |
| MV | MV-london ER<0.50 x0.5 | 22.1 | +23.8 / +23.8 / +22.1 | ZL-1 vol-target | -1200 |
| OD | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | L (x0.5/x1.5) | -313 |
| PB | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | Q1-A (ref) | +1389 |
| PE | ZL-1 vol-target | 7.9 | +7.9 / +15.5 / +28.0 | ZL-1 vol-target | +13420 |
| SM | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | L (x0.5/x1.5) | +667 |

## PLAIN6060 (18880 trades; lot chain reproduced for 93.8% of trades)

Table 1 (PLAIN6060): $/week mean | maxDD | cut vs Q1-A (+ = shallower maxDD) | d mean vs Q1-A, carrying weeks dropped. Cells are FIRST-ORDER estimates (pnl per planned lot x new lots). [Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched (entry match being closed by ENTRY-MATCH); in-sample base; PRE-PROOF]

| cell | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|--|--|--|--|--|--|--|--|--|
| Q1-A (ref) | -4709 / 102732 / +0.0% / +0 | +5880 / 102732 / +0.0% / +0 | +5880 / 102732 / +0.0% / +0 | +21781 / 102732 / +0.0% / +0 | +15277 / 144329 / +0.0% / +0 | +8853 / 144329 / +0.0% / +0 | +14055 / 136226 / +0.0% / +0 | +3182 / 88259 / +0.0% / +0 |
| L (x0.5/x1.5) | -5492 / 145094 / -41.2% / -783 | +6997 / 145094 / -41.2% / +1117 | +6997 / 145094 / -41.2% / +1117 | +30328 / 145094 / -41.2% / +8546 | +23405 / 185843 / -28.8% / +8128 | +16017 / 185843 / -28.8% / +7164 | +20712 / 229557 / -68.5% / +6656 | +4352 / 99807 / -13.1% / +1170 |
| B (x1/x1.5) | -8138 / 167719 / -63.3% / -3429 | +8285 / 167719 / -63.3% / +2404 | +8285 / 167719 / -63.3% / +2404 | +35477 / 173942 / -69.3% / +13695 | +26308 / 219328 / -52.0% / +11031 | +18171 / 219328 / -52.0% / +9319 | +23855 / 197691 / -45.1% / +9800 | +5155 / 148821 / -68.6% / +1973 |
| C (sizer off) | -7355 / 125357 / -22.0% / -2646 | +7168 / 125357 / -22.0% / +1287 | +7168 / 125357 / -22.0% / +1287 | +26931 / 155093 / -51.0% / +5149 | +18180 / 183817 / -27.4% / +2903 | +11008 / 183817 / -27.4% / +2155 | +17199 / 114309 / +16.1% / +3143 | +3985 / 140813 / -59.5% / +803 |
| MV-london ER<0.50 x0.5 | -3791 / 99076 / +3.6% / +918 | +6327 / 99076 / +3.6% / +446 | +6327 / 99076 / +3.6% / +446 | +22661 / 100727 / +2.0% / +879 | +15430 / 146822 / -1.7% / +153 | +7848 / 146822 / -1.7% / -1005 | +14164 / 137674 / -1.1% / +109 | +3401 / 87228 / +1.2% / +219 |
| ZL-1 vol-target | +550 / 67783 / +34.0% / +5259 | +8033 / 67783 / +34.0% / +2153 | +8033 / 67783 / +34.0% / +2153 | +23888 / 67783 / +34.0% / +2107 | +14418 / 127935 / +11.4% / -859 | +5489 / 127935 / +11.4% / -3364 | +12746 / 104748 / +23.1% / -1309 | +2753 / 55515 / +37.1% / -429 |

L2M and L3M coincide after the carrying weeks 202629-202639 are dropped (same weeks remain); L1M differs only through the partial weeks at the window edge.

Table 2 (PLAIN6060): drawdown-first / tolerant gate on the increment (cell minus Q1-A) / placebo (100 draws: permute the cell-to-Q1-A lot ratios within book x session; rank = share of draws with a smaller cut or mean) / equal-DD mean (cell mean x HOLD maxDD(Q1-A)/HOLD maxDD(cell); Q1-A: 21781 / 15277 / 14055). [Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched (entry match being closed by ENTRY-MATCH); in-sample base; PRE-PROOF]

| cell | dd_first_ok | tolerant_incr | cut_L6M | cut_HOLD | cut_PRE | cut_X' | rank_cut_L6M | rank_cut_PRE | rank_mean_L6M | rank_mean_PRE | share_changed | eq-DD mean L6M/HOLD/PRE |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| L (x0.5/x1.5) | False | True | -41.2 | -28.8 | -68.5 | -13.1 | 0.27 | 0.01 | 0.71 | 1.00 | 0.43 | 23553 / 18177 / 16085 |
| B (x1/x1.5) | False | True | -69.3 | -52.0 | -45.1 | -68.6 | 0.84 | 1.00 | 0.36 | 0.58 | 0.80 | 23346 / 17312 / 15698 |
| C (sizer off) | False | True | -51.0 | -27.4 | 16.1 | -59.5 | 0.69 | 1.00 | 0.26 | 0.07 | 0.37 | 21145 / 14274 / 13504 |
| MV-london ER<0.50 x0.5 | False | True | 1.9 | -1.7 | -1.06 | 1.17 | 0.78 | 0.18 | 0.98 | 0.65 | 0.03 | 22276 / 15168 / 13923 |
| ZL-1 vol-target | True | True | 34.0 | 11.4 | 23.1 | 37.1 | 0.99 | 0.87 | 0.94 | 0.50 | 0.18 | 26949 / 16266 / 14380 |

Q1-A vs L (the published Q1 comparison): Q1-A maxDD is shallower than L by +29.2% / +22.3% / +40.7% / +11.6% (L6M / HOLD / PRE / X') at a cost of +8546 $/week mean (L6M).

Table 3 (PLAIN6060): best cell per book (cells scored: Q1-A, L, B, C, MV-london override, ZL-1; the override and the vol-target are in the per-book rows as they act; Q1-A itself wins a book where every alternative deepens a window). [Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched (entry match being closed by ENTRY-MATCH); in-sample base; PRE-PROOF]

| book | best cell (drawdown first: max of min cut L6M/HOLD/PRE) | min cut % | cut L6M/HOLD/PRE % | best L6M Calmar cell | Q1-A L6M mean/wk |
|--|--|--|--|--|--|
| HM | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | ZL-1 vol-target | +1620 |
| KB | ZL-1 vol-target | 3.7 | +14.0 / +3.7 / +10.0 | L (x0.5/x1.5) | +5936 |
| MV | MV-london ER<0.50 x0.5 | 22.8 | +29.8 / +29.8 / +22.8 | MV-london ER<0.50 x0.5 | -1225 |
| OD | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | L (x0.5/x1.5) | -313 |
| PB | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | Q1-A (ref) | +1440 |
| PE | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | ZL-1 vol-target | +11801 |
| SM | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | ZL-1 vol-target | +2522 |

## Held-out live week (2026-11-01..11-05, frozen file, 180 of 187 rows in the DS7 books; first-order lots; same ER ladders on the live signals) [Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched (entry match being closed by ENTRY-MATCH); in-sample base; PRE-PROOF]

| cell | n_trades | chain_ok | mean_lots | live_week_total | live_week_maxdd_daily | worst_day |
|--|--|--|--|--|--|--|
| Q1-A (ref) | 180 | 0.91 | 2.3 | 104810.0 | 0.00 | 16660.0 |
| L (x0.5/x1.5) | 180 | 0.91 | 3.1 | 149174.1 | 0.00 | 25210.4 |
| B (x1/x1.5) | 180 | 0.91 | 3.8 | 178162.9 | 0.00 | 28452.9 |
| C (sizer off) | 180 | 0.91 | 3.0 | 133798.8 | 0.00 | 19902.5 |
| MV-london ER<0.50 x0.5 | 180 | 0.91 | 2.3 | 104810.0 | 0.00 | 16660.0 |
| ZL-1 vol-target | 180 | 0.91 | 1.8 | 79101.4 | 0.00 | 15658.3 |

The live week has no losing day for any cell, so maxDD is zero; the cells are separated by total and worst day only. Down-size cells (ZL-1) give up $ in a winning week; up-size cells add $ (the week is not a drawdown test).

## Exact engine re-runs (code/th_state_s345/state_sizer.py; subclass of state_base.StateBaseRep overriding trend_size; sim.py/rules_replica.py/state_base.py unchanged)


Regression (new file code/th_state_s345/state_sizer_regress.py; all columns, order-insensitive): no sizer key == S1-COMB IDENTICAL (202305, 260 trades, net_fee -37464.42); explicit Q1-A sizer (thr .30, lo .5, hi 1.0) == S1-COMB IDENTICAL (202305 and 202610, 260 and 810 trades). So the subclass changes nothing at default lots. Cells run exactly: X_L (x0.5/x1.5), X_B (x1.0/x1.5), X_C (x1.0), X_MVL (MV London ER<0.50 x0.5 override), X_VT (ZL-1 vol-target); 5 cells = all non-reference cells. Two cell-months (X_MVL 202610, X_B 202509) were run twice at once by two pools, quarantined and re-run alone (the re-run of X_MVL 202610 reproduced the earlier L6M numbers exactly).


Table 4 (S1-COMB): exact re-run vs S1-COMB (= exact Q1-A) as d mean $/wk / maxDD cut %, next to the first-order estimate; only windows whose months are all present are listed. [Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched (entry match being closed by ENTRY-MATCH); in-sample base; PRE-PROOF]

| cell | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|--|--|--|--|--|--|--|--|--|
| X_VT | -9105 / +8.0% ; first-order +202 / +11.3% | -10667 / +8.0% ; first-order -3041 / +11.3% | -10667 / +8.0% ; first-order -3041 / +11.3% | -1364 / +16.5% ; first-order -1289 / +19.5% | -1701 / +13.9% ; first-order -777 / +20.4% | -2211 / +13.9% ; first-order -1668 / +20.4% |  |  |
| X_L | -18953 / -130.0% ; first-order +4114 / -56.8% | -15780 / -130.0% ; first-order +4767 / -56.8% | -15780 / -130.0% ; first-order +4767 / -56.8% | -4104 / -108.7% ; first-order +10567 / -42.3% | -1233 / -47.0% ; first-order +8246 / -30.4% | +2073 / -39.7% ; first-order +9040 / -22.9% |  |  |
| X_B | -19205 / -134.9% ; first-order +10798 / -59.3% | -15424 / -134.9% ; first-order +14902 / -59.3% | -15424 / -134.9% ; first-order +14902 / -59.3% | -941 / -117.7% ; first-order +21090 / -72.4% | +2165 / -75.1% ; first-order +13588 / -65.2% | +853 / -75.1% ; first-order +10740 / -53.0% |  |  |
| X_C | -9330 / -4.4% ; first-order +6684 / -2.4% | -4671 / -4.4% ; first-order +10135 / -2.4% | -4671 / -4.4% ; first-order +10135 / -2.4% | -403 / -21.4% ; first-order +10523 / -59.9% | -706 / -37.4% ; first-order +5342 / -38.5% | -3596 / -37.4% ; first-order +1699 / -38.5% |  |  |
| X_MVL | -513 / -4.4% ; first-order +80 / -1.0% | -581 / -4.4% ; first-order -140 / -1.0% | -581 / -4.4% ; first-order -140 / -1.0% | +105 / +3.5% ; first-order +163 / +1.7% | +11 / -1.9% ; first-order +205 / +1.6% | -644 / -1.9% ; first-order -188 / +1.6% |  |  |

Table 5 (S1-COMB, exact): per book, maxDD cut % / d mean $/wk vs exact Q1-A (carry-dropped) for L6M | HOLD (PRE and X' are added to the selection when all their months are present). X_VT = ZL-1 vol-target, X_MVL = MV-london override. [Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched (entry match being closed by ENTRY-MATCH); in-sample base; PRE-PROOF]

| book | best exact cell (max of min cut over L6M/HOLD) | min cut % | X_VT cut/dmean L6M ; HOLD | X_L cut/dmean L6M ; HOLD | X_B cut/dmean L6M ; HOLD | X_C cut/dmean L6M ; HOLD | X_MVL cut/dmean L6M ; HOLD |
|--|--|--|--|--|--|--|--|
| HM | X_VT | 6.5 | +22.8 / -452 ; +6.5 / -266 | -12.3 / -314 ; -54.1 / -483 | -124.3 / -758 ; -61.2 / -469 | -112.0 / -482 ; -10.8 / -35 | +0.0 / +0 ; +0.0 / +0 |
| KB | Q1-A (ref) | 0.00 | +24.2 / +941 ; -3.9 / +246 | -221.9 / +1173 ; -25.1 / +917 | -123.0 / +2507 ; -77.7 / +1854 | -31.3 / -30 ; -28.4 / +40 | +0.0 / +0 ; +0.0 / +0 |
| MV | X_VT | 11.7 | +11.7 / +296 ; +14.6 / +220 | -30.6 / -825 ; -62.7 / -762 | -89.6 / -1745 ; -53.4 / -416 | -79.2 / -1478 ; -21.4 / +303 | +14.9 / +105 ; +3.8 / +11 |
| OD | Q1-A (ref) | 0.00 | +0.0 / +0 ; +0.0 / +0 | +0.0 / +0 ; +0.0 / +0 | +0.0 / +0 ; +0.0 / +0 | +0.0 / +0 ; +0.0 / +0 | +0.0 / +0 ; +0.0 / +0 |
| PB | Q1-A (ref) | 0.00 | +0.0 / +39 ; +0.0 / +15 | +0.0 / +0 ; -17.6 / -35 | -6.6 / -114 ; +0.1 / -33 | -6.6 / -114 ; +0.0 / -33 | +0.0 / +0 ; +0.0 / +0 |
| PE | Q1-A (ref) | 0.00 | -10.0 / -2516 ; +27.1 / -1436 | -105.1 / -5709 ; -32.1 / -1774 | -132.2 / -2885 ; -56.2 / +933 | +3.0 / +509 ; -59.7 / -728 | +0.0 / +0 ; +0.0 / +0 |
| SM | X_VT | 13.3 | +29.2 / +328 ; +13.3 / -480 | +10.8 / +1571 ; -16.4 / +905 | -30.8 / +2054 ; -61.8 / +296 | -8.5 / +1192 ; -53.8 / -253 | +0.0 / +0 ; +0.0 / +0 |
