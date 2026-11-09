# DS3_TH_S5_STACKGATES_S1B - S5: every stack-gain gate on the S1b base stack (S345-RUN, 2026-11-09)

**Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF**

Prereg: autopilot/DS3_TH_S345_S1B_PREREG.md. Supersedes DS3_TH_STATE_S5_STACKGATES.md (S1 timer base, untouched). Post-hoc, Shadow only, no PASS claims.

Stack = V2 daily $ of the S1b trade list (live lots, fee $4.84 RT inside, label day by exit, 17:00 ET roll); V0 for the correlation (V0 and V2 coincide on a replica base, entries in the V2 time blocks removed: S1B-COMB 506, S1B-NOCUT 506, S1B-UNIF 506). Frames: all stored finalist frames (/mnt/l2/l2vast/instr2_trades, net_usd at the evaluator equal-risk lots, 6734). Gates are the unchanged instr2_eval functions: tolerant gate (L3M and L6M mean > 0; PRE and X' mean >= -0.5 MDE; carrying weeks dropped), k* (largest scale keeping the stack HOLD maxDD), stack Calmar gain dCalmar at k* > 0 in HOLD and L6M (carry-dropped), corr to V0/V2 (daily and weekly) <= 0.30. The tolerant gate is stack-independent; the placebo, family null and walk-forward parts of the T-INSTR-2 bar do not depend on the stack and are not re-run. The stored frames end before the live week (held-out live week: n/a per finalist).

## Summary
- Counts (frames / tolerant / tolerant + stack Calmar gain / + corr <= .30): S1B-COMB 6734 / 374 / 209 / 209; S1B-NOCUT 6734 / 374 / 212 / 212; S1B-UNIF 6734 / 374 / 212 / 212. S1 (timer) COMB page: 6734 / 374 / 186 / 186.
- Gain frames (tolerant + stack gain + corr <= .30): on all three S1b bases 148, on at least one 275, S1b-COMB and S1-timer-COMB both 185 (COMB-only S1b 24, timer-only 1). Max corr among tolerant frames 0.258 on COMB.
- Versus the published stack (same frames on PUB-V2): 211 tolerant frames have a stack gain on PUB-V2, 209 on S1B-COMB (34 gained, 36 lost).
- Reading: gain status moves with the base stack (148 of 275 frames gain on all three S1b bases, i.e. about half are base-robust); a frame that gains on one base and not another may be changing status through the stack drawdown it is measured against, not through the frame. Candidates are listed for the lead, not promoted: the placebo / family / WF bar of T-INSTR-2 is the original frame bar and is not re-run here.

## Counts

| base | frames | tolerant | tolerant + stack Calmar gain | ... and corr <= 0.30 |
|--|--|--|--|--|
| S1B-COMB | 6734 | 374 | 209 | 209 |
| S1B-NOCUT | 6734 | 374 | 212 | 212 |
| S1B-UNIF | 6734 | 374 | 212 | 212 |
| S1 timer COMB (superseded) | 6734 | 374 | 186 | 186 |
| PUB-V2 (published stack, 3,000 frames) | 3000 | 272 | 170 | 170 |

## Stack-gain frames by family (tolerant + gain + corr)

[Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| file | S1B-COMB | S1B-NOCUT | S1B-UNIF | tolerant frames (S1B-COMB) |
|--|--|--|--|--|
| GC | 57 | 45 | 46 | 77 |
| RTY | 48 | 44 | 43 | 76 |
| YM | 29 | 25 | 25 | 54 |
| DAILY | 23 | 22 | 22 | 26 |
| CL | 14 | 25 | 25 | 28 |
| ES | 8 | 5 | 5 | 17 |
| MBT | 6 | 9 | 8 | 10 |
| 6E | 6 | 8 | 8 | 9 |
| MBT_native | 5 | 5 | 5 | 9 |
| 6J | 4 | 4 | 4 | 19 |
| BTC_native | 4 | 3 | 3 | 8 |
| BTC | 3 | 5 | 5 | 6 |
| NQ | 2 | 12 | 13 | 16 |

## Top 30 gain frames on S1B-COMB by dCalmar(HOLD)+dCalmar(L6M) (full list of 209: /mnt/l2/l2vast/_th_state/s345/S1B-COMB/s5_candidates.csv)

[Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| frame | n | k* | dCalmar HOLD | dCalmar L6M | corr max | gain on all 3 S1b bases | gain on S1 timer COMB |
|--|--|--|--|--|--|--|--|
| DAILY/NKD_MA_50_200.parquet | 27.0 | 5.0 | 0.15 | 0.51 | 0.12 | True | True |
| DAILY/NKD_DON_N100_SAR.parquet | 13.0 | 5.0 | 0.14 | 0.51 | 0.14 | True | True |
| GC/6764d7ecabfd_donchian.parquet | 13974.0 | 4.6 | 0.13 | 0.22 | 0.04 | True | True |
| GC/GC__HMAV__nyam__b5-n34__usd1200__R2__T120.parquet | 1006.0 | 5.0 | 0.16 | 0.11 | 0.06 | True | True |
| DAILY/CL_DON_N20_SAR.parquet | 74.0 | 5.0 | 0.06 | 0.20 | 0.16 | True | True |
| DAILY/CL_MA_10_50.parquet | 96.0 | 5.0 | 0.06 | 0.20 | 0.07 | True | True |
| GC/GC__PB__asia__b2-e34-m1.0__usd2400__R1.5__T120.parquet | 2668.0 | 5.0 | 0.11 | 0.12 | 0.05 | True | True |
| DAILY/ES_TSMOM_L126_vol.parquet | 87.0 | 5.0 | 0.06 | 0.15 | 0.10 | True | True |
| GC/GC__PB__asia__b2-e34-m1.0__usd2400__R2__T120.parquet | 2649.0 | 5.0 | 0.12 | 0.09 | 0.05 | True | False |
| DAILY/GC_DON_N20_SAR.parquet | 79.0 | 5.0 | 0.16 | 0.06 | 0.06 | True | True |
| YM/YM__K_b1_ema13_atr7_m1.0__1__nyam__D600__2.0__120.parquet | 3789.0 | 5.0 | 0.06 | 0.13 | 0.11 | True | True |
| YM/YM__K_b1_ema13_atr7_m1.0__1__nyam__D600__1.0__120.parquet | 3789.0 | 5.0 | 0.09 | 0.10 | 0.08 | True | True |
| GC/GC__KELT__nyam__b10-e13-n7-m0.5__atr2__R1__T120.parquet | 742.0 | 5.0 | 0.10 | 0.08 | 0.05 | True | True |
| YM/YM__K_b1_ema13_atr7_m1.0__1__nyam__D600__1.5__120.parquet | 3789.0 | 5.0 | 0.06 | 0.12 | 0.12 | True | True |
| GC/e3b2eecdd2f5_donchian.parquet | 3114.0 | 5.0 | 0.08 | 0.09 | 0.02 | True | True |
| DAILY/GC_MA_10_50.parquet | 85.0 | 5.0 | 0.12 | 0.05 | 0.07 | True | True |
| GC/cc2fa003aba0_vwap_reclaim.parquet | 1787.0 | 5.0 | 0.05 | 0.11 | 0.04 | False | True |
| BTC/FIND_BTC_lrs_close_rev_h30_seed1_atr3.0_None_30.parquet | 810.0 | 5.0 | 0.08 | 0.07 | 0.08 | True | True |
| GC/GC__KELT__nyam__b10-e13-n7-m0.5__atr2__R2__T60.parquet | 759.0 | 5.0 | 0.07 | 0.08 | 0.05 | True | True |
| RTY/RTY__K_b3_ema34_atr7_m2.0__1__pre__D600__1.5__120.parquet | 823.0 | 5.0 | 0.04 | 0.11 | 0.07 | True | True |
| GC/GC__VWR__nyam__b5-k1.5__usd2400__R2__T120.parquet | 305.0 | 5.0 | 0.06 | 0.09 | 0.08 | True | True |
| YM/YM__K_b1_ema13_atr7_m1.0__1__nyam__A2__2.0__60.parquet | 7786.0 | 5.0 | 0.07 | 0.08 | 0.04 | False | True |
| BTC_native/BTC_native_79_atr6_2R_60_sympathy.parquet | 819.0 | 4.6 | 0.01 | 0.14 | 0.14 | True | True |
| GC/GC__KELT__nyam__b10-e13-n20-m0.5__atr2__R1__T120.parquet | 782.0 | 5.0 | 0.09 | 0.05 | 0.02 | True | True |
| GC/GC__PB__asia__b2-e34-m1.5__usd2400__R1__T120.parquet | 2759.0 | 2.9 | 0.04 | 0.10 | 0.08 | True | True |
| GC/GC__DON__asia__b10-n40__atr6__R1__T120.parquet | 248.0 | 5.0 | 0.11 | 0.02 | 0.11 | True | True |
| GC/T2F_GC|VR_nypm_15m|fade|z01.5_f1.0_tm1.0.parquet | 316.0 | 5.0 | 0.05 | 0.08 | 0.08 | True | True |
| GC/T2F_GC|AC_nypm_15m_all|fade|z01.5_f1.0_tm1.0.parquet | 316.0 | 5.0 | 0.05 | 0.08 | 0.08 | True | True |
| RTY/RTY__MV_b15_thr0.25_k3__1__pre__D600__1.5__30.parquet | 2079.0 | 5.0 | 0.02 | 0.11 | 0.01 | False | True |
| GC/GC__DON__asia__b10-n40__atr6__R1.5__T120.parquet | 248.0 | 5.0 | 0.11 | 0.01 | 0.10 | True | True |

## S3 / S4 variants as increment pseudo-books (indicative; no meaningful k* for an increment; dCalmar at k = 1, stack = the reference variant of the same base)

[Label: base S1b = replica engine ITER14 + tick bar close with TH-L2-S (COMB per-book) as live L2 cut; entries not live-matched (entry match < .85); in-sample base; PRE-PROOF]

| base | src | variant | tolerant (increment) | dCalmar L6M | dCalmar HOLD | dCalmar PRE | dCalmar X' | d mean L6M | d mean PRE |
|--|--|--|--|--|--|--|--|--|--|
| S1B-COMB | s3 | L | True | -0.03 | 0.02 | -0.00 | 0.01 | 10209.8 | 7632.8 |
| S1B-COMB | s3 | B | True | 0.02 | 0.01 | 0.01 | -0.00 | 19840.9 | 11492.1 |
| S1B-COMB | s3 | C | True | 0.02 | -0.01 | 0.02 | -0.01 | 9631.1 | 3859.3 |
| S1B-COMB | s3 | BK_MV:london:0.50:0.5:1.0 | False | 0.01 | 0.01 | 0.00 | 0.00 | 228.4 | -87.2 |
| S1B-COMB | s3 | VT_ZL1 | False | 0.13 | 0.05 | 0.02 | 0.03 | -880.5 | -1172.2 |
| S1B-COMB | s4 | ZOFF | False | -0.01 | -0.01 | -0.00 | -0.01 | 1641.6 | -65.7 |
| S1B-COMB | s4 | open20 half | False | 0.10 | 0.01 | 0.02 | 0.01 | -8368.5 | -4656.5 |
| S1B-COMB | s4 | open40 half | False | 0.21 | 0.04 | 0.03 | 0.00 | -4668.4 | -3100.7 |
| S1B-COMB | s4 | open60 half | False | 0.21 | 0.00 | 0.04 | 0.04 | -2094.3 | -1732.5 |
| S1B-COMB | s4 | openA40 half | False | 0.20 | 0.05 | 0.02 | 0.00 | -5425.5 | -4109.5 |
| S1B-COMB | s4 | openA60 half | False | 0.19 | 0.02 | 0.02 | 0.00 | -5202.5 | -3536.2 |
| S1B-COMB | s4 | sopen40 half | False | 0.18 | 0.01 | 0.03 | 0.01 | -3031.8 | -3290.8 |
| S1B-NOCUT | s3 | L | True | -0.00 | 0.01 | -0.02 | 0.01 | 8520.7 | 6474.7 |
| S1B-NOCUT | s3 | B | True | -0.00 | 0.02 | 0.01 | -0.00 | 13557.6 | 10306.9 |
| S1B-NOCUT | s3 | C | True | -0.01 | 0.00 | 0.05 | -0.01 | 5036.9 | 3832.2 |
| S1B-NOCUT | s3 | BK_MV:london:0.50:0.5:1.0 | True | 0.01 | 0.00 | 0.01 | 0.00 | 957.9 | 124.2 |
| S1B-NOCUT | s3 | VT_ZL1 | True | 0.12 | 0.00 | 0.03 | 0.01 | 2047.5 | -1473.5 |
| S1B-NOCUT | s4 | ZOFF | False | -0.00 | 0.00 | -0.01 | -0.01 | 1372.7 | 31.7 |
| S1B-NOCUT | s4 | open20 half | False | 0.04 | 0.00 | 0.00 | 0.02 | -5065.7 | -4063.0 |
| S1B-NOCUT | s4 | open40 half | False | 0.10 | -0.00 | 0.04 | 0.01 | -1057.5 | -2539.1 |
| S1B-NOCUT | s4 | open60 half | True | 0.10 | -0.03 | 0.05 | 0.04 | 541.1 | -1179.0 |
| S1B-NOCUT | s4 | openA40 half | False | 0.11 | 0.01 | 0.04 | 0.00 | -1280.5 | -3123.2 |
| S1B-NOCUT | s4 | openA60 half | False | 0.07 | -0.01 | 0.05 | 0.01 | -1939.6 | -2452.6 |
| S1B-NOCUT | s4 | sopen40 half | False | 0.08 | -0.01 | 0.03 | 0.02 | -453.1 | -2931.0 |
| S1B-UNIF | s3 | L | True | 0.00 | 0.03 | -0.01 | 0.01 | 8770.7 | 7438.3 |
| S1B-UNIF | s3 | B | True | 0.01 | 0.01 | 0.02 | -0.01 | 12027.4 | 11278.1 |
| S1B-UNIF | s3 | C | True | -0.02 | -0.04 | 0.05 | -0.01 | 3256.6 | 3839.8 |
| S1B-UNIF | s3 | BK_MV:london:0.50:0.5:1.0 | True | 0.01 | 0.00 | 0.01 | 0.00 | 598.0 | 47.2 |
| S1B-UNIF | s3 | VT_ZL1 | True | 0.09 | 0.01 | 0.02 | 0.01 | 1664.3 | -1351.9 |
| S1B-UNIF | s4 | ZOFF | True | 0.01 | -0.00 | -0.01 | -0.01 | 1850.7 | 141.0 |
| S1B-UNIF | s4 | open20 half | False | 0.05 | -0.01 | 0.01 | 0.02 | -4360.3 | -4421.9 |
| S1B-UNIF | s4 | open40 half | False | 0.08 | -0.02 | 0.03 | 0.02 | -1353.8 | -2677.9 |
| S1B-UNIF | s4 | open60 half | True | 0.09 | -0.02 | 0.05 | 0.05 | 597.7 | -1309.2 |
| S1B-UNIF | s4 | openA40 half | False | 0.07 | -0.01 | 0.03 | 0.00 | -2002.0 | -3372.8 |
| S1B-UNIF | s4 | openA60 half | False | 0.07 | -0.01 | 0.04 | 0.01 | -2195.5 | -2737.3 |
| S1B-UNIF | s4 | sopen40 half | False | 0.06 | -0.01 | 0.02 | 0.02 | -246.4 | -2963.8 |

## Caveats
- Frames are the stored finalist frames (re-costed), not the evaluator originals; WATCH items without frames (Monday long, CMD4, RTY) are not scored. The stack changes with the base, so gain status moves; function identity with instr2_eval is exact. Entries not live-matched; PRE-PROOF.
