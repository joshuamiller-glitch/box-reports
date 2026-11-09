# DS3_TH_S3_SIZER_S1B - S3: Q1-A vs the ER ladder on the S1b base (S345-RUN, 2026-11-09)

**Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF**

Prereg: autopilot/DS3_TH_S345_S1B_PREREG.md (sha in DECISIONS.md before scoring). Supersedes DS3_TH_STATE_S3_SIZER.md (S1 timer-close base, untouched). Windows as of 2026-10-31 (instr2_eval), carrying weeks dropped, drawdown first, MDE shown; all post-hoc, Shadow only, no PASS claims.

## Summary (S1B-COMB = the live cell; first-order unless marked exact)
- Q1-A (ER<0.30 x0.5, else x1) against the ladder: Q1-A has the shallowest maxDD of the up-size cells. maxDD cut of each cell vs Q1-A on L6M / HOLD / PRE / X': L -46 / -31 / -48 / -20, B -59 / -66 / -51 / -68, C (sizer off) -27 / -36 / -8 / -67 (negative = deeper maxDD than Q1-A). Same signs on S1B-NOCUT (L -42 / -38 / -66 / -14, B -64 / -50 / -51 / -69, C -33 / -21 / +12 / -57) and S1B-UNIF (L -47 / -34 / -61 / -15, B -55 / -58 / -50 / -74, C -37 / -50 / +10 / -63); C on PRE is the only positive cut of a up-size/off cell (never-cut and UNIF), not on COMB. L, B, C raise the mean ($/wk d mean on L6M: L +10210, B +19841, C +9631, first-order) at the price of maxDD.
- Best cell by drawdown first: ZL-1 vol-target (down-only on Q1-A): cut +29 / +26 / +20 / +33 (L6M / HOLD / PRE / X') on S1B-COMB, +33 / +5 / +28 / +37 on NOCUT, +28 / +9 / +24 / +36 on UNIF, mean -881 / -838 / -1172 $/wk on L6M / HOLD / PRE (COMB, MDE L6M 32105), so it is a drawdown-for-mean trade, not mean-keeping. MV-london override: cut +2 / +2 / +3 / -1 on COMB, inside the noise, mean about 0.
- Walk-forward (monthly 2024-01..2026-10, 26 trailing weeks, 7-day embargo, picks lowest maxDD): picks the vol-target every month; OOS maxDD cut +19.7% vs Q1-A (mean -1291 $/wk) on COMB. Family null (max over the 5 non-reference cells, within book x session permutations of the lot ratios, 300 draws): vol-target p_family L6M 0.50 / PRE 0.89 (own-draw p 0.11 / 0.36) - not below .10 on either window.
- Held-out live week (frozen file, 180 of 187 rows in the DS7 books, first-order): no losing day for any cell (maxDD 0); totals Q1-A $104810, L $149174, B $178163, C $133799, vol-target $79101. The week cannot separate cells on drawdown.
- EXACT engine re-runs (state_sizer_b.py, S1b tick engine) run in the background; Table 4 appears once a window is complete (regression month identical). Until then every cell number above is first-order.
- The only drawdown-first lead (vol-target) does not clear the family null, gives up mean, and the tolerant gate on its increment is False on COMB; no cell is an ENTER candidate here (post-hoc, PRE-PROOF).

## S1B-COMB (21135 trades; base lots reproduced by the chain for 93.5%)

Table 1 (S1B-COMB): $/week mean | maxDD | cut vs Q1-A (+ = shallower) | d mean vs Q1-A, carrying weeks dropped; MDE(L6M) of Q1-A 32105. FIRST-ORDER (pnl per planned lot x new lots). [Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| cell | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|--|--|--|--|--|--|--|--|--|
| Q1-A (ref) | +9069 / 79821 / +0.0% / +0 | +15336 / 79821 / +0.0% / +0 | +15336 / 79821 / +0.0% / +0 | +28728 / 79821 / +0.0% / +0 | +18084 / 99496 / +0.0% / +0 | +14328 / 88531 / +0.0% / +0 | +16287 / 140288 / +0.0% / +0 | +3367 / 73108 / +0.0% / +0 |
| L (x0.5/x1.5) | +11429 / 116699 / -46.2% / +2360 | +18174 / 116699 / -46.2% / +2838 | +18174 / 116699 / -46.2% / +2838 | +38938 / 116699 / -46.2% / +10210 | +26098 / 130207 / -30.9% / +8015 | +23077 / 116067 / -31.1% / +8749 | +23920 / 207515 / -47.9% / +7633 | +4736 / 87598 / -19.8% / +1369 |
| B (x1/x1.5) | +15987 / 126963 / -59.1% / +6918 | +26214 / 126963 / -59.1% / +10878 | +26214 / 126963 / -59.1% / +10878 | +48569 / 126963 / -59.1% / +19841 | +31863 / 165603 / -66.4% / +13779 | +26333 / 131650 / -48.7% / +12006 | +27779 / 212116 / -51.2% / +11492 | +5205 / 122743 / -67.9% / +1838 |
| C (sizer off) | +13627 / 90085 / -12.9% / +4558 | +23376 / 90085 / -12.9% / +8040 | +23376 / 90085 / -12.9% / +8040 | +38359 / 101228 / -26.8% / +9631 | +23848 / 134892 / -35.6% / +5765 | +17585 / 118527 / -33.9% / +3257 | +20146 / 151592 / -8.1% / +3859 | +3836 / 121805 / -66.6% / +469 |
| MV-london ER<0.50 x0.5 | +9152 / 78311 / +1.9% / +83 | +15204 / 78311 / +1.9% / -132 | +15204 / 78311 / +1.9% / -132 | +28957 / 78311 / +1.9% / +228 | +18467 / 97422 / +2.1% / +383 | +14489 / 84383 / +4.7% / +161 | +16200 / 136763 / +2.5% / -87 | +3525 / 73541 / -0.6% / +158 |
| ZL-1 vol-target | +10997 / 56462 / +29.3% / +1928 | +14014 / 56462 / +29.3% / -1321 | +14014 / 56462 / +29.3% / -1321 | +27848 / 56462 / +29.3% / -881 | +17246 / 73548 / +26.1% / -838 | +12375 / 71767 / +18.9% / -1953 | +15115 / 112622 / +19.7% / -1172 | +3547 / 48745 / +33.3% / +180 |

Table 2 (S1B-COMB): drawdown-first, tolerant gate on the increment (cell minus Q1-A), placebo ranks (100 draws, lot ratios permuted within book x session; rank = share of draws with a smaller cut or mean), equal-DD mean (Q1-A: 28728 / 18084 / 16287). [Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| cell | dd_first_ok | tolerant_incr | cut_L6M | cut_HOLD | cut_PRE | cut_X' | rank_cut_L6M | rank_cut_PRE | rank_mean_L6M | rank_mean_PRE | share_changed | eq-DD mean L6M/HOLD/PRE |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| L (x0.5/x1.5) | False | True | -46.2 | -30.9 | -47.9 | -19.8 | 0.21 | 0.02 | 0.81 | 1.00 | 0.41 | 29754 / 19943 / 18278 |
| B (x1/x1.5) | False | True | -59.1 | -66.4 | -51.2 | -67.9 | 0.92 | 1.00 | 0.40 | 0.57 | 0.79 | 29181 / 19144 / 16690 |
| C (sizer off) | False | True | -26.8 | -35.6 | -8.1 | -66.6 | 0.80 | 0.99 | 0.18 | 0.02 | 0.39 | 28294 / 17591 / 14860 |
| MV-london ER<0.50 x0.5 | True | False | 1.9 | 2.1 | 2.5 | -0.59 | 0.61 | 0.67 | 0.58 | 0.25 | 0.02 | 29573 / 18860 / 16545 |
| ZL-1 vol-target | True | False | 29.3 | 26.1 | 19.7 | 33.3 | 0.87 | 0.62 | 0.88 | 0.76 | 0.18 | 37672 / 23331 / 20447 |

Table 3 (S1B-COMB): best cell per book, first-order (Q1-A itself wins a book where every alternative deepens a window). [Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| book | best cell (max of min cut L6M/HOLD/PRE) | min cut % | cut L6M/HOLD/PRE % | Q1-A L6M mean/wk |
|--|--|--|--|--|
| HM | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | +2271 |
| KB | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | +6228 |
| MV | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | -1730 |
| OD | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | -58 |
| PB | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | +734 |
| PE | ZL-1 vol-target | 20.4 | +20.4 / +38.4 / +22.6 | +19899 |
| SM | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | +1382 |

## S1B-NOCUT (18960 trades; base lots reproduced by the chain for 93.6%)

Table 1 (S1B-NOCUT): $/week mean | maxDD | cut vs Q1-A (+ = shallower) | d mean vs Q1-A, carrying weeks dropped; MDE(L6M) of Q1-A 37020. FIRST-ORDER (pnl per planned lot x new lots). [Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| cell | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|--|--|--|--|--|--|--|--|--|
| Q1-A (ref) | -6805 / 115144 / +0.0% / +0 | +3537 / 115144 / +0.0% / +0 | +3537 / 115144 / +0.0% / +0 | +21323 / 115144 / +0.0% / +0 | +14830 / 135361 / +0.0% / +0 | +9475 / 135361 / +0.0% / +0 | +14785 / 127656 / +0.0% / +0 | +3308 / 91973 / +0.0% / +0 |
| L (x0.5/x1.5) | -8214 / 163726 / -42.2% / -1409 | +3890 / 163726 / -42.2% / +353 | +3890 / 163726 / -42.2% / +353 | +29844 / 163726 / -42.2% / +8521 | +22723 / 186645 / -37.9% / +7893 | +16553 / 186645 / -37.9% / +7077 | +21260 / 212095 / -66.1% / +6475 | +4388 / 105142 / -14.3% / +1080 |
| B (x1/x1.5) | -12060 / 188865 / -64.0% / -5255 | +3981 / 188865 / -64.0% / +444 | +3981 / 188865 / -64.0% / +444 | +34881 / 188865 / -64.0% / +13558 | +25801 / 202408 / -49.5% / +10971 | +19311 / 202408 / -49.5% / +9836 | +25092 / 193250 / -51.4% / +10307 | +5268 / 155655 / -69.2% / +1960 |
| C (sizer off) | -10652 / 140282 / -21.8% / -3846 | +3628 / 140282 / -21.8% / +91 | +3628 / 140282 / -21.8% / +91 | +26360 / 152763 / -32.7% / +5037 | +17908 / 163437 / -20.7% / +3078 | +12234 / 163437 / -20.7% / +2759 | +18617 / 112193 / +12.1% / +3832 | +4188 / 144575 / -57.2% / +880 |
| MV-london ER<0.50 x0.5 | -5886 / 111458 / +3.2% / +919 | +3987 / 111458 / +3.2% / +450 | +3987 / 111458 / +3.2% / +450 | +22281 / 111458 / +3.2% / +958 | +15178 / 135254 / +0.1% / +348 | +8921 / 135254 / +0.1% / -555 | +14909 / 121376 / +4.9% / +124 | +3527 / 90927 / +1.1% / +219 |
| ZL-1 vol-target | -1206 / 77596 / +32.6% / +5599 | +6036 / 77596 / +32.6% / +2499 | +6036 / 77596 / +32.6% / +2499 | +23371 / 77596 / +32.6% / +2048 | +14301 / 128513 / +5.1% / -529 | +6295 / 128513 / +5.1% / -3180 | +13312 / 92238 / +27.7% / -1473 | +2852 / 58311 / +36.6% / -456 |

Table 2 (S1B-NOCUT): drawdown-first, tolerant gate on the increment (cell minus Q1-A), placebo ranks (100 draws, lot ratios permuted within book x session; rank = share of draws with a smaller cut or mean), equal-DD mean (Q1-A: 21323 / 14830 / 14785). [Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| cell | dd_first_ok | tolerant_incr | cut_L6M | cut_HOLD | cut_PRE | cut_X' | rank_cut_L6M | rank_cut_PRE | rank_mean_L6M | rank_mean_PRE | share_changed | eq-DD mean L6M/HOLD/PRE |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| L (x0.5/x1.5) | False | True | -42.2 | -37.9 | -66.2 | -14.3 | 0.18 | 0.01 | 0.80 | 0.94 | 0.43 | 21644 / 16479 / 15418 |
| B (x1/x1.5) | False | True | -64.0 | -49.5 | -51.4 | -69.2 | 0.82 | 1.00 | 0.37 | 0.57 | 0.80 | 23327 / 17254 / 16780 |
| C (sizer off) | False | True | -32.7 | -20.7 | 12.1 | -57.2 | 0.88 | 1.00 | 0.18 | 0.10 | 0.37 | 21832 / 14832 / 15419 |
| MV-london ER<0.50 x0.5 | True | True | 3.2 | 0.08 | 4.9 | 1.14 | 0.90 | 0.88 | 0.97 | 0.65 | 0.03 | 22299 / 15190 / 14921 |
| ZL-1 vol-target | True | True | 32.6 | 5.1 | 27.7 | 36.6 | 0.98 | 0.93 | 0.97 | 0.49 | 0.18 | 24616 / 15063 / 14021 |

Table 3 (S1B-NOCUT): best cell per book, first-order (Q1-A itself wins a book where every alternative deepens a window). [Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| book | best cell (max of min cut L6M/HOLD/PRE) | min cut % | cut L6M/HOLD/PRE % | Q1-A L6M mean/wk |
|--|--|--|--|--|
| HM | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | +1575 |
| KB | ZL-1 vol-target | 4.5 | +14.0 / +4.5 / +6.0 | +5948 |
| MV | MV-london ER<0.50 x0.5 | 22.1 | +30.1 / +30.1 / +22.1 | -1215 |
| OD | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | -124 |
| PB | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | +1390 |
| PE | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | +11273 |
| SM | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | +2476 |

## S1B-UNIF (19797 trades; base lots reproduced by the chain for 93.5%)

Table 1 (S1B-UNIF): $/week mean | maxDD | cut vs Q1-A (+ = shallower) | d mean vs Q1-A, carrying weeks dropped; MDE(L6M) of Q1-A 33838. FIRST-ORDER (pnl per planned lot x new lots). [Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| cell | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|--|--|--|--|--|--|--|--|--|
| Q1-A (ref) | -7733 / 106459 / +0.0% / +0 | +2663 / 106459 / +0.0% / +0 | +2663 / 106459 / +0.0% / +0 | +18428 / 106459 / +0.0% / +0 | +15417 / 117476 / +0.0% / +0 | +16531 / 117476 / +0.0% / +0 | +16087 / 134464 / +0.0% / +0 | +4117 / 80778 / +0.0% / +0 |
| L (x0.5/x1.5) | -10813 / 157026 / -47.5% / -3079 | +3640 / 157026 / -47.5% / +977 | +3640 / 157026 / -47.5% / +977 | +27198 / 157026 / -47.5% / +8771 | +25316 / 157026 / -33.7% / +9899 | +28533 / 151349 / -28.8% / +12003 | +23525 / 215996 / -60.6% / +7438 | +5423 / 93286 / -15.5% / +1306 |
| B (x1/x1.5) | -11029 / 165429 / -55.4% / -3296 | +5211 / 165429 / -55.4% / +2548 | +5211 / 165429 / -55.4% / +2548 | +30455 / 165429 / -55.4% / +12027 | +26013 / 185274 / -57.7% / +10596 | +28699 / 181792 / -54.7% / +12169 | +27365 / 201891 / -50.1% / +11278 | +6361 / 140460 / -73.9% / +2243 |
| C (sizer off) | -7950 / 114861 / -7.9% / -216 | +4233 / 114861 / -7.9% / +1570 | +4233 / 114861 / -7.9% / +1570 | +21684 / 145905 / -37.1% / +3257 | +16113 / 176279 / -50.1% / +696 | +16697 / 176279 / -50.1% / +166 | +19927 / 120358 / +10.5% / +3840 | +5055 / 131450 / -62.7% / +938 |
| MV-london ER<0.50 x0.5 | -7113 / 103189 / +3.1% / +620 | +3190 / 103189 / +3.1% / +527 | +3190 / 103189 / +3.1% / +527 | +19025 / 103189 / +3.1% / +598 | +15563 / 116103 / +1.2% / +146 | +15867 / 116103 / +1.2% / -663 | +16134 / 129368 / +3.8% / +47 | +4337 / 79732 / +1.3% / +219 |
| ZL-1 vol-target | -3847 / 77147 / +27.5% / +3886 | +3009 / 77147 / +27.5% / +347 | +3009 / 77147 / +27.5% / +347 | +20092 / 77147 / +27.5% / +1664 | +14655 / 106439 / +9.4% / -761 | +12678 / 106439 / +9.4% / -3852 | +14735 / 102284 / +23.9% / -1352 | +3288 / 51370 / +36.4% / -829 |

Table 2 (S1B-UNIF): drawdown-first, tolerant gate on the increment (cell minus Q1-A), placebo ranks (100 draws, lot ratios permuted within book x session; rank = share of draws with a smaller cut or mean), equal-DD mean (Q1-A: 18428 / 15417 / 16087). [Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| cell | dd_first_ok | tolerant_incr | cut_L6M | cut_HOLD | cut_PRE | cut_X' | rank_cut_L6M | rank_cut_PRE | rank_mean_L6M | rank_mean_PRE | share_changed | eq-DD mean L6M/HOLD/PRE |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| L (x0.5/x1.5) | False | True | -47.5 | -33.7 | -60.6 | -15.5 | 0.10 | 0.01 | 0.87 | 0.99 | 0.42 | 20348 / 18940 / 17600 |
| B (x1/x1.5) | False | True | -55.4 | -57.7 | -50.1 | -73.9 | 0.97 | 1.00 | 0.39 | 0.65 | 0.79 | 19311 / 16494 / 17351 |
| C (sizer off) | False | True | -37.0 | -50.0 | 10.5 | -62.7 | 0.67 | 1.00 | 0.15 | 0.02 | 0.38 | 14451 / 10738 / 13280 |
| MV-london ER<0.50 x0.5 | True | True | 3.1 | 1.17 | 3.8 | 1.29 | 0.86 | 0.78 | 0.89 | 0.57 | 0.03 | 19251 / 15747 / 16325 |
| ZL-1 vol-target | True | True | 27.5 | 9.4 | 23.9 | 36.4 | 0.91 | 0.74 | 0.96 | 0.59 | 0.18 | 22175 / 16175 / 16263 |

Table 3 (S1B-UNIF): best cell per book, first-order (Q1-A itself wins a book where every alternative deepens a window). [Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| book | best cell (max of min cut L6M/HOLD/PRE) | min cut % | cut L6M/HOLD/PRE % | Q1-A L6M mean/wk |
|--|--|--|--|--|
| HM | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | +1036 |
| KB | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | +4997 |
| MV | MV-london ER<0.50 x0.5 | 21.9 | +24.1 / +24.1 / +21.9 | -1142 |
| OD | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | -124 |
| PB | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | +1187 |
| PE | ZL-1 vol-target | 15.3 | +15.8 / +15.3 / +28.9 | +11824 |
| SM | Q1-A (ref) | 0.00 | +0.0 / +0.0 / +0.0 | +649 |

## Walk-forward and family null (S1B-COMB first-order; the other two bases in the CSVs)

Walk-forward OOS 2024-01..2026-10 (carrying weeks dropped; weekly): per fixed cell and for the picked series WF. [Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| series | n_weeks | mean_wk | maxdd | worst20 | mde | cut_vs_ref_pct | dmean_vs_ref |
|--|--|--|--|--|--|--|--|
| Q1A | 133 | 17664.8 | 140288.2 | -1045576.1 | 10046.2 | 0.00 | 0.00 |
| L | 133 | 25833.6 | 207514.7 | -1439419.8 | 14138.5 | -47.9 | 8168.9 |
| B | 133 | 30081.1 | 212115.8 | -1655240.7 | 16450.9 | -51.2 | 12416.3 |
| C | 133 | 21912.2 | 151592.4 | -1285786.0 | 12828.9 | -8.1 | 4247.5 |
| BK_MV:london:0.50:0.5:1.0 | 133 | 17770.6 | 136763.4 | -1021237.0 | 9914.0 | 2.5 | 105.8 |
| VT_ZL1 | 133 | 16373.8 | 112622.2 | -838084.5 | 8493.6 | 19.7 | -1290.9 |
| WF | 133 | 16373.8 | 112622.2 | -838084.5 | 8493.6 | 19.7 | -1290.9 |

Picks: VT_ZL1 34 (months).

Family null: cut statistic vs own placebo draws and vs the max over cells (z-standardised).

| cell | window | cut_obs | null_mean | null_sd | p_own | p_family |
|--|--|--|--|--|--|--|
| L | L6M | -46.2 | -29.9 | 19.0 | 0.80 | 1.00 |
| B | L6M | -59.1 | -74.6 | 12.4 | 0.10 | 0.41 |
| C | L6M | -26.8 | -49.8 | 24.3 | 0.19 | 0.63 |
| BK_MV:london:0.50:0.5:1.0 | L6M | 1.9 | 0.85 | 2.0 | 0.31 | 0.85 |
| VT_ZL1 | L6M | 29.3 | 17.8 | 10.3 | 0.11 | 0.49 |
| L | PRE | -47.9 | -24.1 | 12.9 | 0.96 | 1.00 |
| B | PRE | -51.2 | -75.0 | 8.9 | 0.02 | 0.03 |
| C | PRE | -8.1 | -48.4 | 18.5 | 0.02 | 0.06 |
| BK_MV:london:0.50:0.5:1.0 | PRE | 2.5 | 1.49 | 1.7 | 0.29 | 0.75 |
| VT_ZL1 | PRE | 19.7 | 16.8 | 7.8 | 0.35 | 0.89 |

S1B-NOCUT WF: WF series cut +5.1% mean -1235 (picks VT_ZL1 34).

S1B-UNIF WF: WF series cut +20.8% mean -1281 (picks VT_ZL1 34).

## Held-out live week (frozen file, first-order lots)

| cell | n_trades | chain_ok | mean_lots | live_week_total | live_week_maxdd_daily | worst_day |
|--|--|--|--|--|--|--|
| Q1-A (ref) | 180 | 0.91 | 2.3 | 104810.0 | 0.00 | 16660.0 |
| L (x0.5/x1.5) | 180 | 0.91 | 3.1 | 149174.1 | 0.00 | 25210.4 |
| B (x1/x1.5) | 180 | 0.91 | 3.8 | 178162.9 | 0.00 | 28452.9 |
| C (sizer off) | 180 | 0.91 | 3.0 | 133798.8 | 0.00 | 19902.5 |
| MV-london ER<0.50 x0.5 | 180 | 0.91 | 2.3 | 104810.0 | 0.00 | 16660.0 |
| ZL-1 vol-target | 180 | 0.91 | 1.8 | 79101.4 | 0.00 | 15658.3 |

No losing day for any cell: maxDD 0 on all; separates by total and worst day only (up-size adds $, down-size gives up $ in a winning week). [Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

## Exact engine re-runs (code/th_state_s345/state_sizer_b.py = S1b tick engine with the sizer override in trend_size)

Regression (state_sizer_b_regress.py; all columns, order-insensitive): explicit Q1-A sizer (thr .30, lo .5, hi 1.0) == S1b S1-COMB trade list, month 202305: IDENTICAL (260 trades, net_fee -37429.42). Cells run exactly: X_L (x0.5/x1.5), X_B (x1.0/x1.5), X_C (x1.0), X_MVL (MV London ER<0.50 x0.5), X_VT (ZL-1 vol-target); 5 non-reference cells.

Table 4 (S1B-COMB): exact re-run vs S1B-COMB (= exact Q1-A), d mean $/wk / maxDD cut %, next to first-order; only windows whose months are all present. [Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| cell | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|--|--|--|--|--|--|--|--|--|
| X_VT | -5160 / +37.2% ; first-order +1928 / +29.3% | -6712 / +37.2% ; first-order -1321 / +29.3% | -6712 / +37.2% ; first-order -1321 / +29.3% | -351 / +37.2% ; first-order -881 / +29.3% | -1595 / +21.1% ; first-order -838 / +26.1% | -2842 / +11.3% ; first-order -1953 / +18.9% |  |  |
| X_L | -14529 / -76.3% ; first-order +2360 / -46.2% | -11380 / -76.3% ; first-order +2838 / -46.2% | -11380 / -76.3% ; first-order +2838 / -46.2% | +83 / -76.3% ; first-order +10210 / -46.2% | +674 / -41.5% ; first-order +8015 / -30.9% | +3089 / -37.2% ; first-order +8749 / -31.1% |  |  |
| X_B | -14049 / -68.9% ; first-order +6918 / -59.1% | -10739 / -68.9% ; first-order +10878 / -59.1% | -10739 / -68.9% ; first-order +10878 / -59.1% | +2024 / -68.9% ; first-order +19841 / -59.1% | +2862 / -52.6% ; first-order +13779 / -66.4% | +31 / -71.6% ; first-order +12006 / -48.7% |  |  |
| X_C | -5850 / +18.5% ; first-order +4558 / -12.9% | -1375 / +18.5% ; first-order +8040 / -12.9% | -1375 / +18.5% ; first-order +8040 / -12.9% | -391 / +7.2% ; first-order +9631 / -26.8% | -1058 / -38.6% ; first-order +5765 / -35.6% | -5182 / -55.8% ; first-order +3257 / -33.9% |  |  |
| X_MVL | -495 / -1.3% ; first-order +83 / +1.9% | -543 / -1.3% ; first-order -132 / +1.9% | -543 / -1.3% ; first-order -132 / +1.9% | +7 / -1.3% ; first-order +228 / +1.9% | +195 / +6.8% ; first-order +383 / +2.1% | -117 / -0.8% ; first-order +161 / +4.7% |  |  |

## Versus the superseded S1 (timer) page

| cell | S1 (timer) cut L6M/HOLD/PRE | S1b (tick) cut L6M/HOLD/PRE |
|--|--|--|
| L (x0.5/x1.5) | -42.3 / -30.4 / -48.5 | -46.2 / -30.9 / -47.9 |
| B (x1/x1.5) | -72.4 / -65.2 / -52.4 | -59.1 / -66.4 / -51.2 |
| C (sizer off) | -59.9 / -38.5 / -9.3 | -26.8 / -35.6 / -8.1 |
| ZL-1 vol-target | +19.5 / +20.4 / +22.7 | +29.3 / +26.1 / +19.7 |


## Caveats
- First-order scaling (pnl per planned lot x new lots) overstates up-size gains (caps, locks, sliced fills and TH timing do not scale); the DD ranking is the usable part; exact rows are the check. The S3 triple and features keyed to V13T rows are not ported. Entries are not live-matched (match < .85): PRE-PROOF. L2M and L3M coincide after the carrying weeks are dropped. Windows are as of 2026-10-31 (data to 2026-10-30 in the daily frame; the Nov live week is only the held-out row).
