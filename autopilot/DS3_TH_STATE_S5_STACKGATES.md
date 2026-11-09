# DS3_TH_STATE_S5_STACKGATES - S5: every stack-gain gate on the TH-L2-S engine base stack (S345-RUN, 2026-11-09)

**Label: base = replica engine with TH-L2-S as live L2 cut (COMB per-book); entries not live-matched (entry match being closed by ENTRY-MATCH); in-sample base; PRE-PROOF**

Stack = V2 daily $ of the base trade list (live lots, fee included, label day by exit, 17:00 ET roll); V0 for the correlation. Frames: all 6,734 stored finalist frames (/mnt/l2/l2vast/instr2_trades, net_usd at the evaluator equal-risk lots). Gates are the unchanged instr2_eval functions: tolerant gate (L3M and L6M mean > 0; PRE and X' mean >= -0.5 MDE; carrying weeks dropped), k* (largest scale keeping the stack HOLD maxDD), stack Calmar gain dCalmar at k* > 0 in HOLD and L6M (carry-dropped), correlation to V0/V2 (daily and weekly) <= 0.30. The tolerant gate is stack-independent (374 frames on every base). Placebo / family / walk-forward are NOT re-run (stack-independent except the Calmar-gain statistic).

## Counts

| base | frames | tolerant | tolerant + stack Calmar gain | ... and corr <= 0.30 |
|--|--|--|--|--|
| S1-COMB | 6734 | 374 | 186 | 186 |
| S1-UNIF | 6734 | 374 | 194 | 194 |
| PLAIN6060 | 6734 | 374 | 183 | 183 |
| OLD-BASE (replica HOLD, plumbing only) | 6734 | 374 | 216 | 216 |
| PUB-V2 (published stack, 3,000 frames) | 3000 | 272 | 170 | 170 |

Gain frames on all three bases: 113; on at least one: 254. Versus the published stack (same 6,734 frames scored on PUB-V2): 211 tolerant frames have a stack gain on PUB-V2, 186 on S1-COMB (25 gained, 50 lost); across all frames 430 change gain status. Max corr among tolerant frames 0.237 (S1-COMB). k* median 4.78 (k* = 0 for 118 tolerant frames: no scale keeps the stack HOLD maxDD).

## Stack-gain frames by family (tolerant + gain + corr)

| file | S1-COMB | S1-UNIF | PLAIN6060 | tolerant frames (S1-COMB) |
|--|--|--|--|--|
| GC | 48 | 41 | 41 | 77 |
| RTY | 45 | 43 | 30 | 76 |
| YM | 29 | 24 | 24 | 54 |
| DAILY | 23 | 22 | 21 | 26 |
| CL | 11 | 18 | 18 | 28 |
| MBT_native | 6 | 6 | 9 | 9 |
| 6E | 6 | 8 | 8 | 9 |
| ES | 5 | 5 | 6 | 17 |
| 6J | 4 | 4 | 5 | 19 |
| BTC_native | 3 | 1 | 1 | 8 |
| BTC | 3 | 5 | 5 | 6 |
| NQ | 2 | 12 | 12 | 16 |
| MBT | 1 | 5 | 3 | 10 |

## Stack-gain table: top 30 gain frames on S1-COMB by dCalmar(HOLD)+dCalmar(L6M) (full list of 186: /mnt/l2/l2vast/_th_state/s345/S1-COMB/s5_candidates.csv)

| frame | n | k* | dCalmar HOLD | dCalmar L6M | corr max | PUB-V2 dCal HOLD | PUB-V2 dCal L6M | gain on all 3 bases |
|--|--|--|--|--|--|--|--|--|
| DAILY/NKD_MA_50_200.parquet | 27.0 | 5.0 | 0.1 | 0.6 | 0.1 | 0.2 | 0.7 | True |
| DAILY/NKD_DON_N100_SAR.parquet | 13.0 | 5.0 | 0.1 | 0.6 | 0.1 | 0.2 | 0.7 | True |
| GC/6764d7ecabfd_donchian.parquet | 13974.0 | 4.0 | 0.1 | 0.4 | 0.0 | 0.3 | 0.3 | True |
| GC/GC__HMAV__nyam__b5-n34__usd1200__R2__T120.parquet | 1006.0 | 5.0 | 0.2 | 0.2 | 0.0 | 0.3 | 0.1 | True |
| DAILY/CL_DON_N20_SAR.parquet | 74.0 | 5.0 | 0.1 | 0.3 | 0.1 | 0.1 | 0.3 | True |
| DAILY/CL_MA_10_50.parquet | 96.0 | 5.0 | 0.1 | 0.2 | 0.1 | 0.1 | 0.3 | True |
| GC/GC__KELT__nyam__b10-e13-n7-m0.5__atr2__R1__T120.parquet | 742.0 | 5.0 | 0.1 | 0.2 | 0.1 | 0.2 | 0.1 | True |
| GC/e3b2eecdd2f5_donchian.parquet | 3114.0 | 5.0 | 0.1 | 0.2 | 0.0 | 0.1 | 0.1 | True |
| GC/GC__KELT__nyam__b10-e13-n7-m0.5__atr2__R2__T60.parquet | 759.0 | 5.0 | 0.1 | 0.2 | 0.1 | 0.1 | 0.1 | True |
| DAILY/ES_TSMOM_L126_vol.parquet | 87.0 | 5.0 | 0.1 | 0.2 | 0.1 | 0.1 | 0.2 | True |
| GC/GC__KELT__nyam__b10-e13-n20-m0.5__atr2__R1__T120.parquet | 782.0 | 5.0 | 0.1 | 0.2 | 0.0 | 0.1 | 0.1 | True |
| GC/cc2fa003aba0_vwap_reclaim.parquet | 1787.0 | 3.8 | 0.0 | 0.2 | 0.0 | 0.1 | 0.1 | False |
| DAILY/GC_DON_N20_SAR.parquet | 79.0 | 5.0 | 0.2 | 0.1 | 0.0 | 0.2 | 0.1 | True |
| CL/9903d3c1211b_vwap_reclaim.parquet | 5430.0 | 5.0 | 0.1 | 0.2 | 0.1 | 0.2 | 0.1 | True |
| CL/CL_321_pre_usd600_1.5R_120_pullback_band.parquet | 818.0 | 5.0 | 0.0 | 0.2 | 0.1 | 0.1 | 0.1 | True |
| RTY/RTY__MV_b15_thr0.25_k3__1__pre__D600__1.5__30.parquet | 2079.0 | 5.0 | 0.0 | 0.2 | 0.0 | 0.0 | 0.1 | False |
| YM/YM__K_b1_ema13_atr7_m1.0__1__nyam__D600__1.0__120.parquet | 3789.0 | 5.0 | 0.1 | 0.1 | 0.1 | 0.1 | 0.1 | True |
| GC/GC__SUPT__nyam__b5-n14-m3.0__atr3__R2__T60.parquet | 651.0 | 5.0 | 0.1 | 0.1 | 0.1 | 0.1 | 0.1 | True |
| ES/T2F_ES|VR_london_120m|fade|z01.5_f0.5_tm2.0.parquet | 198.0 | 4.0 | 0.0 | 0.2 | 0.1 | 0.0 | 0.1 | False |
| GC/GC__VWR__nyam__b5-k1.5__usd2400__R2__T120.parquet | 305.0 | 4.6 | 0.1 | 0.1 | 0.1 | 0.3 | 0.1 | True |
| YM/1f63209890b3_vwap_reclaim.parquet | 4581.0 | 5.0 | 0.1 | 0.1 | 0.0 | 0.1 | 0.1 | True |
| ES/T2F_ES|VR_london_120m|fade|z01.5_f0.5_tm1.0.parquet | 198.0 | 4.0 | 0.0 | 0.2 | 0.1 | 0.0 | 0.1 | False |
| DAILY/GC_MA_10_50.parquet | 85.0 | 5.0 | 0.1 | 0.1 | 0.1 | 0.1 | 0.1 | True |
| RTY/RTY__K_b3_ema21_atr14_m2.0__1__pre__D1200__1.5__60.parquet | 1220.0 | 5.0 | 0.0 | 0.2 | 0.1 | 0.0 | 0.0 | True |
| GC/GC__SUPT__nyam__b5-n10-m3.0__atr4__R1.5__T60.parquet | 596.0 | 4.2 | 0.0 | 0.1 | 0.1 | 0.1 | 0.1 | True |
| GC/5ae4b631c93d_donchian.parquet | 9345.0 | 2.6 | 0.0 | 0.1 | 0.1 | 0.0 | 0.0 | True |
| RTY/RTY__K_b3_ema13_atr7_m2.0__1__pre__A2__1.0__60.parquet | 827.0 | 5.0 | 0.0 | 0.2 | 0.1 | 0.0 | 0.0 | True |
| CL/40d3eb437a35_vwap_reclaim.parquet | 5151.0 | 5.0 | 0.0 | 0.1 | 0.1 | 0.1 | 0.0 | False |
| GC/GC__PB__asia__b2-e34-m1.0__usd2400__R1.5__T120.parquet | 2668.0 | 5.0 | 0.1 | 0.0 | 0.0 | 0.2 | 0.1 | True |
| YM/YM__K_b1_ema13_atr7_m1.0__1__nyam__A2__2.0__60.parquet | 7786.0 | 3.8 | 0.0 | 0.1 | 0.0 | 0.3 | 0.1 | False |

## S3 / S4 variants as increment pseudo-books (indicative; the increment series has no meaningful k*; dCalmar at k = 1, stack = the reference variant of the same base)

| base | src | variant | tolerant (increment) | dCalmar L6M | dCalmar HOLD | dCalmar PRE | dCalmar X' | d mean L6M | d mean PRE |
|--|--|--|--|--|--|--|--|--|--|
| S1-COMB | s3 | L | True | -0.0 | 0.0 | 0.0 | 0.0 | 10567.0 | 7910.6 |
| S1-COMB | s3 | B | True | -0.0 | 0.0 | 0.0 | -0.0 | 21090.2 | 11291.4 |
| S1-COMB | s3 | C | True | -0.1 | -0.0 | 0.0 | -0.0 | 10523.1 | 3380.8 |
| S1-COMB | s3 | BK_MV:london:0.50:0.5:1.0 | False | 0.0 | 0.0 | 0.0 | 0.0 | 162.6 | -109.9 |
| S1-COMB | s3 | VT_ZL1 | False | 0.1 | 0.0 | 0.0 | 0.0 | -1289.0 | -1185.1 |
| S1-COMB | s4 | ZOFF | False | 0.0 | -0.0 | -0.0 | -0.0 | 2061.6 | -79.2 |
| S1-COMB | s4 | open20 half | False | 0.0 | -0.0 | 0.0 | 0.0 | -9165.8 | -4586.9 |
| S1-COMB | s4 | open40 half | False | 0.1 | 0.0 | 0.0 | 0.0 | -5244.2 | -3067.4 |
| S1-COMB | s4 | open60 half | False | 0.1 | -0.0 | 0.0 | 0.0 | -2592.9 | -1685.5 |
| S1-COMB | s4 | openA40 half | False | 0.1 | 0.0 | 0.0 | 0.0 | -6363.7 | -4053.6 |
| S1-COMB | s4 | openA60 half | False | 0.1 | 0.0 | 0.0 | -0.0 | -5889.8 | -3478.1 |
| S1-COMB | s4 | sopen40 half | False | 0.1 | -0.0 | 0.0 | 0.0 | -3568.6 | -3295.9 |
| S1-UNIF | s3 | L | True | 0.0 | 0.0 | -0.0 | 0.0 | 9681.8 | 7518.8 |
| S1-UNIF | s3 | B | True | -0.0 | 0.0 | 0.0 | -0.0 | 12847.8 | 10884.9 |
| S1-UNIF | s3 | C | True | -0.1 | -0.0 | 0.1 | -0.0 | 3166.0 | 3366.1 |
| S1-UNIF | s3 | BK_MV:london:0.50:0.5:1.0 | True | 0.0 | -0.0 | 0.0 | 0.0 | 488.5 | 54.2 |
| S1-UNIF | s3 | VT_ZL1 | False | 0.1 | 0.0 | 0.0 | 0.0 | 1448.9 | -1172.7 |
| S1-UNIF | s4 | ZOFF | True | 0.0 | -0.0 | -0.0 | -0.0 | 2309.4 | 129.1 |
| S1-UNIF | s4 | open20 half | False | 0.0 | -0.0 | 0.0 | 0.0 | -4942.0 | -4216.3 |
| S1-UNIF | s4 | open40 half | False | 0.1 | -0.0 | 0.0 | 0.0 | -1708.2 | -2504.4 |
| S1-UNIF | s4 | open60 half | False | 0.1 | -0.0 | 0.1 | 0.1 | 245.6 | -1062.1 |
| S1-UNIF | s4 | openA40 half | False | 0.1 | -0.0 | 0.0 | 0.0 | -2401.0 | -3204.3 |
| S1-UNIF | s4 | openA60 half | False | 0.1 | -0.0 | 0.1 | 0.0 | -2567.7 | -2573.1 |
| S1-UNIF | s4 | sopen40 half | False | 0.1 | -0.0 | 0.0 | 0.0 | -636.6 | -2847.7 |
| PLAIN6060 | s3 | L | True | -0.0 | 0.0 | -0.0 | 0.0 | 8546.2 | 6656.4 |
| PLAIN6060 | s3 | B | True | -0.0 | 0.0 | 0.0 | -0.0 | 13695.3 | 9799.9 |
| PLAIN6060 | s3 | C | True | -0.0 | -0.0 | 0.0 | -0.0 | 5149.1 | 3143.4 |
| PLAIN6060 | s3 | BK_MV:london:0.50:0.5:1.0 | True | 0.0 | -0.0 | -0.0 | 0.0 | 879.4 | 108.6 |
| PLAIN6060 | s3 | VT_ZL1 | True | 0.1 | 0.0 | 0.0 | 0.0 | 2106.6 | -1308.9 |
| PLAIN6060 | s4 | ZOFF | False | -0.0 | 0.0 | -0.0 | -0.0 | 1429.4 | 55.3 |
| PLAIN6060 | s4 | open20 half | False | 0.0 | 0.0 | -0.0 | 0.0 | -5464.2 | -3836.1 |
| PLAIN6060 | s4 | open40 half | False | 0.1 | -0.0 | 0.0 | 0.0 | -1388.5 | -2367.7 |
| PLAIN6060 | s4 | open60 half | True | 0.1 | -0.0 | 0.0 | 0.0 | 132.1 | -1021.3 |
| PLAIN6060 | s4 | openA40 half | False | 0.1 | 0.0 | 0.0 | 0.0 | -1657.8 | -2952.2 |
| PLAIN6060 | s4 | openA60 half | False | 0.1 | -0.0 | 0.0 | 0.0 | -2364.5 | -2298.6 |
| PLAIN6060 | s4 | sopen40 half | False | 0.1 | -0.0 | 0.0 | 0.0 | -900.2 | -2783.4 |
