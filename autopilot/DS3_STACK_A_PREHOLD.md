# DS3_STACK_A pre-holdout text. Prereg l2vast/ds3/prereg/D3SKA_prereg.md sha256 ffc0d180053e1428541fe4241b2b5edf49b03efd2fb2975f7eae9060945a53dd. Written BEFORE any HOLD / X / FULL number was opened.
PRE (WFPRE 2024-02..2025-06, 75 wk) only. Base stack: weekly mean 44,127, SD 131,184, maxDD 477,701, worst -306,664. LM = lot-matched, MM = mean-matched (constants fixed on PRE). Slot lists were selected on PRE, so the PRE gain of a cell is in-sample by construction; the random-slot placebo is therefore informative only on HOLD / X. The 200 random + 2 shifted placebos are in the sealed file; nothing after PRE has been read.
| cell | entries affected | raw d_mean | LM d_mean [CI iid] (MDE) | LM d_SD | LM d_maxDD | LM d_worst | LM $ saved in PRE 20 worst wks / $ per wk in the other wks | rand-slot rank / shifted(+30,-30) d_mean | MM d_mean | PRE G1,G3,G4,G7 |
|---|---|---|---|---|---|---|---|---|---|---|
| A01_blk_strict_pool | 1.7% | -203 | -49 [-4,285,+4,127] (MDE 5,962) | +1,229 | -59,036 | +27,242 | +3,042 / -122 | 0.50 / +2,274,+2,103 | -0 | 0100 |
| A02_blk_loose_pool | 25.0% | +2,760 | +8,112 [-6,663,+22,837] (MDE 21,509) | +4,061 | +52,563 | +76,173 | +284,411 / +5,891 | 0.98 / -10,021,+444 | +0 | 1011 |
| A03_blk_strict_book | 0.9% | +1,898 | +1,985 [-76,+4,217] (MDE 3,135) | +912 | +5,389 | -580 | +93,689 / +1,003 | 0.91 / +78,-550 | -0 | 1001 |
| A04_blk_loose_book | 24.1% | +12,473 | +16,351 [+2,898,+30,252] (MDE 19,850) | -11,015 | -66,597 | +125,420 | +1,138,222 / +1,602 | 1.00 / -1,346,-16,377 | +0 | 1111 |
| A05_half_loose_pool | 25.0% | +6,078 | +9,955 [-535,+20,551] (MDE 15,366) | +1,852 | -38,476 | +39,628 | +251,831 / +8,996 | 0.99 / +4,085,+9,600 | -0 | 1111 |
| A06_half_loose_book | 24.1% | +10,093 | +14,531 [+6,199,+23,073] (MDE 12,059) | +337 | -24,956 | +51,756 | +449,108 / +11,649 | 1.00 / +4,182,-4,489 | +0 | 1111 |
| A07_blk_loose_pool_rng | 3.2% | -3,385 | -2,670 [-8,636,+3,373] (MDE 8,743) | +697 | +80,267 | -5,383 | +36,584 / -4,306 | 0.63 / +677,-2,184 | -0 | 0000 |
| A08_blk_loose_book_rng | 3.7% | -4,343 | -3,731 [-10,176,+2,051] (MDE 8,815) | -2,054 | +22,632 | -4,715 | +149,839 / -7,812 | 0.37 / +1,447,-360 | +0 | 0000 |
| A09_half_loose_pool_rng | 3.2% | -3,037 | -2,530 [-7,473,+1,474] (MDE 6,539) | -1,406 | -25,078 | -3,783 | +29,973 / -3,995 | 0.38 / -726,+64 | -0 | 0000 |
| A10_ctl_blk_top14_pool | 47.2% | -51,960 | -53,649 [-78,401,-28,648] (MDE 35,801) | +16,369 | +1,130,981 | -99,996 | +223,228 / -77,216 | nan / +nan,+nan | +nan | 0000 |
