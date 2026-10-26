# REPORT DS2-50 (trackDS50) - fifty further pair mechanisms
Research only; nothing live; UNTOUCHED unread; replay and data end 2026-10-16 (forward weeks from 2026-10-19 not read). PREREG: outputs/l2vast/PREREG_DS2_50.md (sha256 92d5274e...34f7, frozen before scoring). Cells CSV (corrected, primary): outputs/l2vast/pairP2/ds50/corr/summary_cells.csv (as-built: ds50/summary_cells.csv) (all 413 gated rows, IS/WF/L8W columns); per-item: corr/summary_items.csv.

## Bottom line (CORRECTED benchmark = primary; as-built = secondary column)
- RESCORED 2026-10-22 on the corrected P9 points table (verify_x/P9_fixed_pts.npy, VERIFY_X.md: exit-table mapping bug fixed). Everything here is on the corrected benchmark unless a column says as-built (the earlier run on the buggy table, kept in ds50/summary_cells.csv).
- 413 gated rows (409 pre-registered cells; item 47 reports 2 portfolio views per cell) over 50 families. **0 cells pass gates a-d. 0 LEAD, 0 CONFIRMED, no LEADS_FROZEN_DS50.json, no forward shadow.** Best-of-F line 0.95^(1/3331)=0.999985 is unreachable with <=500 reps: NOT cleared.
- 22 cells beat the corrected benchmark on net AND maxDD in both WF and L8W (as-built: 15). None clears gate c (shuffled-date rank >= .95 on BOTH delta mean and -delta maxDD). Closest: R31_PC_equity_top_shorts8 (rank .994 / .928 at 500 reps; gate d passes, bootstrap lo +$797), R32_RTH_pos_SToff (.98 / .71, gate d passes), R31_PC_equity_top_longs8 (.95 / .59, gate d passes): mean-significant but the maxDD statistic fails the null, so NOT leads (and put/call is a 3-feature x 4-tilt family of 20 cells). The as-built single gate a-c passer R22_first3_8 no longer holds on the corrected benchmark (rank .80 / .48): it was a benchmark-bug artefact.
- Repeated maxDD deltas (e.g. -$29,852, -$37,549, -$71,728 across unrelated cells) = switch to another drawdown episode, mechanical; the null on -deltaMaxDD discriminates.
- Risk block (37-44, 48-50): nothing beats. NAM $85k halt (corrected benchmark): fires on 32 label days in 953, WF -$190/wk (c=0) / -$315/wk (3 pts), maxDD +$34k; with a -4R floor NAM fires only 2 times (the floor fires 173 times), cost -$259/wk, maxDD +$42k. Item 49 restart <= -$977/wk. Item 39 opposite-only after lock +$7.0k/wk (variant B) but maxDD +$273k.
- New books: ES/YM pair loses at market cost and at NQ-relative cost (standalone about -$13k to -$15k/wk at NQ-relative cost; every add-on view negative); ES/NQ spread and VWAP-band fade lose standalone. NQ minute-bar control through the same code: WF $32.3k/wk, Sharpe 2.19.

## Benchmark and exit table used
CORRECTED benchmark (live DualStrat2 spec, ds2lib snapshot engine, corrected P9 points = verify_x/P9_fixed_pts.npy): WF OOS (142 wk) $24,848/wk, SD $104,185, maxDD $399,445, worst -$137,064; L8W $34,525/wk, maxDD $266,515 (matches VERIFY_X.md). As-built (buggy table): $37,068 / $103,015 / $369,648 / -$138,415; L8W $51,330 / $257,231. Entire pipeline re-run on the corrected table (outputs in ds50/corr/): all cells, stage-1 N1 nulls (100 reps, every gate-a passer), stage-2 (500 reps) for cells with both ranks >= .90 (R18_top_8, R18_top_skip, R31_PC_equity_top_shorts8, S11_last60_LONDON, S8_ESflip5_size8), gate d, WF-selected lines. Switch: env F50_P9PTS=<npy> and F50_OUT=<dir>. Engine validation unchanged (bit-identical to ds2lib on both tables).

## Shortlist: beats benchmark on net AND maxDD in BOTH WF and L8W (22 cells on the corrected benchmark; ranked by WF delta mean)
weekly $ at 14/14; Δ vs benchmark; null = shuffled-date (N1) rank on delta WF mean / -delta WF maxDD with reps; fire/mo = benchmark rows changed per month (WF).

| cell | WF mean | WF SD | WF maxDD | WF Sh | worst wk | tr/wk | WF Δmean | WF ΔmaxDD | L8W mean | L8W maxDD | L8W Δmean | L8W ΔmaxDD | IS mean | IS maxDD | fire/mo | N1 rank mean / dd (reps) | gates a b c d | as-built WF Δmean / ΔmaxDD (beats?) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R31_PC_equity_top_shorts8 | 31,469 | 106,973 | 352,281 | 2.12 | -137,064 | 39.1 | 6,621 | -47,165 | 58,950 | 193,883 | 24,425 | -72,632 | 13,259 | 478,886 | 25.5 | 0.994 / 0.928 (500) | Y Y n Y | 3,233 / -9,730 (Y) |
| R31_PC_equity_top_longs8 | 30,163 | 105,676 | 386,844 | 2.06 | -140,118 | 39.5 | 5,315 | -12,601 | 43,964 | 180,259 | 9,440 | -86,256 | 12,227 | 475,276 | 25.6 | 0.950 / 0.590 (100) | Y Y n Y | 4,044 / -6,790 (Y) |
| S1_0.8_1.25_1.0 | 30,010 | 108,146 | 369,594 | 2.00 | -136,913 | 37.0 | 5,162 | -29,852 | 69,229 | 146,644 | 34,704 | -119,871 | -1,726 | 681,830 | nan | n/a | Y Y n n | 3,485 / 11,239 (n) |
| R36_prev4R_skip | 29,815 | 100,935 | 369,594 | 2.13 | -137,064 | 35.9 | 4,968 | -29,852 | 49,124 | 195,975 | 14,599 | -70,540 | 17,613 | 340,133 | 9.3 | 1.000 / 0.800 (100) | Y Y n n | -2,094 / 0 (n) |
| R16_CHOP14_off1_ST | 29,710 | 99,060 | 397,027 | 2.16 | -137,064 | 31.9 | 4,862 | -2,418 | 44,593 | 219,487 | 10,068 | -47,028 | 11,331 | 405,313 | 27.4 | 1.000 / 0.600 (100) | Y Y n n | 2,912 / -69,287 (Y) |
| R32_RTH_pos_SToff | 29,186 | 103,395 | 386,031 | 2.04 | -136,913 | 34.9 | 4,339 | -13,415 | 44,317 | 243,321 | 9,792 | -23,194 | 11,648 | 389,418 | 6.0 | 0.980 / 0.710 (100) | Y Y n Y | 241 / 19,447 (n) |
| R18_nr720_top8 | 28,750 | 104,479 | 381,015 | 1.98 | -145,280 | 40.6 | 3,903 | -18,430 | 36,484 | 264,720 | 1,960 | -1,794 | 17,301 | 264,268 | 54.2 | 0.860 / 0.750 (100) | Y Y n n | 1,138 / -34,591 (Y) |
| R32_all_pos_size8 | 28,735 | 95,022 | 327,621 | 2.18 | -137,853 | 50.0 | 3,887 | -71,825 | 48,411 | 205,870 | 13,887 | -60,645 | 7,372 | 388,708 | 90.4 | 0.740 / 0.930 (100) | Y Y n n | -280 / -50,932 (n) |
| S1_1.25_0.8_1.0 | 27,597 | 107,526 | 398,136 | 1.85 | -136,913 | 35.9 | 2,750 | -1,309 | 60,875 | 133,939 | 26,351 | -132,575 | -1,127 | 650,528 | nan | n/a | Y Y n n | 2,511 / 25,242 (n) |
| R29_VIX5d_t0_size8 | 27,501 | 98,224 | 383,856 | 2.02 | -137,064 | 43.0 | 2,654 | -15,589 | 48,439 | 239,375 | 13,915 | -27,140 | 16,254 | 443,485 | 51.2 | 0.760 / 0.540 (100) | Y Y n n | 3,259 / -85,426 (Y) |
| R22_first3_8 | 27,396 | 99,198 | 386,379 | 1.99 | -137,064 | 39.5 | 2,548 | -13,066 | 44,119 | 195,540 | 9,595 | -70,975 | 10,779 | 505,617 | 22.0 | 0.800 / 0.480 (100) | Y Y n n | 3,144 / -75,162 (Y) |
| R36_prev4R_size8 | 27,300 | 102,169 | 369,594 | 1.93 | -137,064 | 37.1 | 2,453 | -29,852 | 37,293 | 252,400 | 2,768 | -14,115 | 15,284 | 342,937 | 8.6 | 0.910 / 0.830 (100) | Y Y n n | -884 / 0 (n) |
| S1_1.0_1.25_1.0 | 26,868 | 105,762 | 369,594 | 1.83 | -137,064 | 35.7 | 2,020 | -29,852 | 77,381 | 121,811 | 42,857 | -144,704 | 650 | 597,359 | nan | n/a | Y Y n n | 548 / 11,239 (n) |
| R22_TOM5_8 | 26,743 | 98,219 | 361,896 | 1.96 | -137,064 | 41.8 | 1,896 | -37,549 | 46,952 | 175,403 | 12,428 | -91,112 | 6,974 | 543,879 | 36.5 | 0.740 / 0.700 (100) | Y Y n n | 1,252 / -54,175 (Y) |
| R18_nr7_20 | 26,467 | 104,560 | 389,833 | 1.83 | -145,280 | 34.3 | 1,620 | -9,613 | 36,840 | 264,720 | 2,316 | -1,794 | 15,915 | 286,396 | 23.0 | 0.690 / 0.780 (100) | Y Y n n | -331 / 6,957 (n) |
| S11_last30_LONDON | 25,898 | 105,073 | 328,942 | 1.78 | -138,828 | 35.9 | 1,051 | -70,503 | 34,870 | 263,369 | 345 | -3,146 | 14,605 | 341,991 | 4.1 | 0.660 / 1.000 (100) | Y Y n n | 210 / -73,388 (Y) |
| R16_CHOP14_off1_both | 25,806 | 89,780 | 368,891 | 2.07 | -137,261 | 24.7 | 958 | -30,554 | 58,595 | 56,052 | 24,070 | -210,462 | 14,218 | 347,925 | 49.0 | 0.960 / 0.710 (100) | Y Y n n | -845 / -85,426 (n) |
| R25_all7_skipAsiaLon | 25,723 | 100,084 | 361,896 | 1.85 | -137,064 | 35.3 | 875 | -37,549 | 36,224 | 252,923 | 1,699 | -13,592 | 4,593 | 485,889 | 9.6 | 0.770 / 0.930 (100) | Y Y n n | 2,568 / -75,162 (Y) |
| R31_PC_total_top_shorts8 | 25,705 | 105,185 | 375,959 | 1.76 | -138,984 | 39.0 | 857 | -23,487 | 38,955 | 236,662 | 4,430 | -29,852 | 19,790 | 395,046 | 25.3 | 0.690 / 0.720 (100) | Y Y n n | -920 / -45,289 (n) |
| R24_PCE_W60 | 25,544 | 103,859 | 362,889 | 1.77 | -137,064 | 35.7 | 697 | -36,556 | 36,550 | 250,314 | 2,025 | -16,201 | 11,692 | 423,977 | 0.7 | 0.860 / 0.970 (100) | Y Y n n | 485 / -23,211 (Y) |
| R24_PCE_W30 | 25,314 | 104,180 | 399,333 | 1.75 | -137,064 | 35.8 | 467 | -112 | 36,550 | 250,314 | 2,025 | -16,201 | 12,591 | 421,273 | 0.4 | 0.810 / 0.860 (100) | Y Y n n | 363 / 0 (n) |
| R22_last2_8 | 25,081 | 102,341 | 379,064 | 1.77 | -139,469 | 38.4 | 233 | -20,381 | 37,358 | 246,378 | 2,833 | -20,137 | 10,045 | 438,394 | 14.7 | 0.540 / 0.630 (100) | Y Y n n | -1,897 / -3,547 (n) |

Null coverage (corrected benchmark): stage 1 (100 N1 reps) for every cell passing gate a (WF delta mean>0, delta maxDD<0, Sharpe up): blocks 1, 2, 3a; stage 2 (500 reps) for cells with both ranks >= .90; Engine cells S1_0.8_1.25_1.0, S1_1.0_1.25_1.0 and S1_1.25_0.8_1.0 (item 1 regime-switched parameters) beat the corrected benchmark in both windows but have no null (decision-vector nulls do not apply; the PREREG tercile-shift null was NOT run) and their bootstrap lower bounds are negative (-$934, -$3,693, -$4,618), so gate d fails: not leads. New books: no cell passes gate a. Cells without a rank (n/a) failed gate a at their stage-0 screen or are the stage-1-only entries marked above.

## One line per item (best cell by WF delta mean; family WF-selected line = per-fold fit-Sharpe selection incl. "none")
| item | cells | beats-both | gate a | best cell | WF Δmean | WF ΔmaxDD | L8W Δmean | L8W ΔmaxDD | WF-selected Δmean (L8W) |
|---|---|---|---|---|---|---|---|---|---|
| 1 | 26 | 3 | 3 | S1_0.8_1.25_1.0 | 5,162 | -29,852 | 34,704 | -119,871 | -8,010 (-12,666) |
| 2 | 3 | 0 | 1 | S2_intrabar_HM | 6,737 | -11,822 | -7,736 | 121,109 | 443 (-7,736) |
| 3 | 9 | 0 | 0 | S3_a_ST | -309 | 164,987 | 30,497 | -99,582 | -6,105 (-34,360) |
| 4 | 4 | 0 | 0 | S4_W60_size8 | 847 | 1,680 | 12,503 | -53,557 | -3,983 (12,503) |
| 5 | 8 | 0 | 1 | S5_atr_8_14_14 | 8,263 | 64,131 | 2,474 | 1,116 | 2,763 (2,474) |
| 6 | 12 | 0 | 0 | S6_session_both_size8 | 5,556 | 3,661 | -8,791 | 15,874 | -2,577 (-12,593) |
| 7 | 4 | 0 | 0 | S7_start570_size8 | -62 | 5,061 | -897 | 0 | -384 (0) |
| 8 | 6 | 0 | 2 | S8_ESflip5_size8 | 6,588 | -83,251 | 5,390 | 43,046 | -891 (5,390) |
| 9 | 6 | 0 | 1 | S9_X20_ST | 6,941 | 70,815 | 32,834 | -76,914 | 2,635 (32,834) |
| 10 | 6 | 0 | 0 | S10_w5_uncond | -5,142 | 546,132 | 34,481 | -54,741 | -2,987 (34,481) |
| 11 | 8 | 1 | 6 | S11_last60_LONDON | 3,984 | -70,256 | -6,670 | 14,131 | 4,554 (-1,919) |
| 12 | 6 | 0 | 2 | S12_to1655_thr90 | 4,440 | 69,548 | 1,014 | 0 | 3,400 (1,014) |
| 13 | 7 | 0 | 1 | S13_lt1_8 | 1,476 | -87,978 | -11,740 | -3,585 | -9,750 (-11,740) |
| 14 | 8 | 0 | 0 | S14_hi_8 | 6,934 | 26,129 | 12,780 | 0 | 3,936 (12,780) |
| 15 | 9 | 0 | 0 | S15_4h_HM | 5,111 | 128,503 | 10,724 | -44,255 | 3,056 (10,724) |
| 16 | 18 | 2 | 4 | R16_CHOP14_off1_HM | 5,051 | -22,186 | -3,696 | -18,730 | -2,869 (10,938) |
| 17 | 9 | 0 | 0 | R17_counter8 | 2,538 | 78,913 | -606 | -105,509 | -11,965 (-606) |
| 18 | 8 | 2 | 5 | R18_nr720_top8 | 3,903 | -18,430 | 1,960 | -1,794 | 4,348 (-356) |
| 19 | 10 | 0 | 1 | R19_m0.25_fill_skip | 930 | 0 | 523 | 0 | -868 (-3,321) |
| 20 | 6 | 0 | 0 | R20_q5_shr | 1,215 | 91,056 | -9,824 | 45,552 | -1,870 (16,963) |
| 21 | 8 | 0 | 0 | R21_Mon_8 | 351 | 107,429 | 5,260 | 7,886 | -8,145 (-8,774) |
| 22 | 8 | 3 | 3 | R22_last2_20 | 3,144 | 17,086 | 24,797 | -127,131 | 3,076 (12,428) |
| 23 | 12 | 0 | 7 | R23_any3_size8 | 3,543 | -54,916 | -6,972 | 78,015 | 11 (-4,881) |
| 24 | 12 | 2 | 3 | R24_CONF_W60 | 1,616 | 0 | -516 | 0 | -1,280 (-516) |
| 25 | 9 | 1 | 1 | R25_all7_skipAsia | 1,247 | 59,651 | 13,147 | -81,196 | 2,126 (1,699) |
| 26 | 12 | 0 | 3 | R26_after_size8 | 1,493 | -6,147 | -650 | 5,198 | -129 (12,817) |
| 27 | 4 | 0 | 0 | R27_sun_to20_skip | 3,699 | 101,357 | 18,358 | 5,080 | 3,275 (3,351) |
| 28 | 4 | 0 | 1 | R28_rollFri_skip | 451 | -27,440 | -2,219 | 0 | -438 (-5,085) |
| 29 | 12 | 1 | 2 | R29_VVIX_t1_size8 | 2,930 | 10,937 | -4,546 | 0 | 1,426 (-3,644) |
| 30 | 4 | 0 | 0 | R30_inv_size8 | 408 | 0 | 0 | 0 | -4,716 (0) |
| 31 | 20 | 3 | 7 | R31_PC_equity_top_shorts8 | 6,621 | -47,165 | 24,425 | -72,632 | -223 (-9,699) |
| 32 | 12 | 2 | 4 | R32_RTH_pos_SToff | 4,339 | -13,415 | 9,792 | -23,194 | -4,195 (13,887) |
| 33 | 6 | 0 | 0 | R33_sma20_longs8_below | -2,070 | 316,742 | -9,940 | 49,315 | -6,312 (-20,686) |
| 34 | 12 | 0 | 1 | R34_ZN_p99 | 2,484 | 13,364 | -5,941 | -25,543 | -1,536 (15,871) |
| 35 | 6 | 0 | 0 | R35_btc_t2_size8 | 3,297 | 30,770 | -1,928 | -38,290 | 743 (-11,320) |
| 36 | 6 | 2 | 2 | R36_prev4R_skip | 4,968 | -29,852 | 14,599 | -70,540 | 2,917 (14,599) |
| 37 | 6 | 0 | 0 | I37_p1.0_combo_week | 5,134 | 41,741 | 4,284 | -7,011 | -574 (4,284) |
| 38 | 6 | 0 | 1 | I38_W20_60min | 24 | -13,760 | -7,555 | 2,040 | -2,367 (0) |
| 39 | 4 | 0 | 0 | I39_B_sess_anylock | 7,024 | 272,911 | 23,692 | 136,603 | -3,127 (0) |
| 40 | 4 | 0 | 0 | I40_K3_3sess | -1,316 | -5,419 | -9,966 | -27,010 | -161 (0) |
| 41 | 5 | 0 | 1 | I41_n10_size8 | 1,142 | -89,418 | 10,804 | 43,512 | -5,884 (10,804) |
| 42 | 4 | 0 | 1 | I42_samebook_17 | 1,150 | -8,397 | -2,578 | 83,451 | -2,877 (-2,578) |
| 43 | 6 | 0 | 0 | I43_w13_d0.5 | 1,666 | 126,575 | -17,770 | 89,892 | 1,148 (-17,770) |
| 44 | 8 | 0 | 1 | I44_STboth_HMETH | 1,334 | 143,284 | 5,429 | -34,151 | 3,681 (5,429) |
| 45 | 12 | 0 | 0 | B45_k3_RR60_chop | -567 | -29,852 | -7,560 | -33,157 | -1,546 (0) |
| 46 | 8 | 0 | 0 | B46_W390_z2.0_zero | -23,685 | 488,893 | -28,091 | 91,431 | 0 (0) |
| 47 | 8 | 0 | 0 | B47_ES_nqrel_add100 | -13,212 | 75,533 | -15,893 | 45,446 | 0 (0) |
| 48 | 6 | 0 | 0 | I48_N6_floor5_NAM_c3 | 13 | 33,368 | 1,972 | -15,780 | -601 (-9,166) |
| 49 | 6 | 0 | 0 | I49_Wed_-4R | -405 | 0 | 0 | 0 | 0 (0) |
| 50 | 10 | 0 | 3 | I50_round100_X5_skip | 5,348 | -62,457 | 24,690 | 70,473 | 2,143 (25,811) |

Small positive WF-selected lines exist in several families (up to about +$4.5k/wk WF, mostly folds choosing none); none has an N1 rank >= .95 on both statistics.

## NOT RUN / limits
- 24: GDP and retail-sales 08:30 windows NOT RUN (no verified calendar; see QUESTIONS Q13); ISM/PCE/consumer-confidence classes run from rules and flagged UNVERIFIED; Treasury auctions use the verified schedule (free API).
- 28: execution on the new front after roll NOT RUN (second-contract L2 not in the P9 replay); skip Thu/Fri cells run.
- 47: ES/YM at P9-grade execution NOT RUN; run with market 1-tick costs and NQ-relative cost, 1-min bar brackets (stop-first), minute-clock locks. NQ minute-bar control through the same code: WF $32.3k/wk, Sharpe 2.19 (corrected 1-s tick benchmark $24.8k).
- Put/call and SKEW lagged one extra day (T-2) because their publication time is unverified; VIX family T-1. GEX only from 10:00 ET and through 2026-10-13. Earnings dates = EDGAR 8-K Item 2.02 filing dates (after 16:00 ET).
- Deviations from PREREG wording: item 3 armed state resets at the label-day boundary; item 39 no further combo-lock monitoring after the opposite-only window opens; item 14/36 as specified; item 2 HM intrabar is the affine approximation (baseline coverage 99.7%/99.5%); causality log ds50/causal_check.log: 0 mismatches on signals (2 randomised-future cuts), VWAP/session H-L/elapsed/rolling-high-low (200 rows) and daily ATR20/CHOP14 (40 days) - smaller samples than the 2,000 rows promised (stated); item 45 halted-state uses benchmark lock times and per-book day limits from kept rows; item 48 "last night" incident details not on disk (parametric 3 pts per NAM fire).
- Row-level approximation: skipped rows do not release swallowed signals.

## Timeline
Initial run on the as-built table, then full RESCORE on the corrected table (primary). Blocks scored in order Risk -> Regime -> Signal (3a row-level, 3b engine) -> Books; progress in autopilot/DS2_50_PROGRESS.md.