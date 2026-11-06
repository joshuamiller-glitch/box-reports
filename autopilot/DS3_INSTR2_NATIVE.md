

# DS3_INSTR2_NATIVE: T-INSTR-2 addendum A, ZN / ZB native event books (N1 08:30 release, N2 13:00 auction, N3 15:00 settle; refunding weeks as day sets) - interim 1, 2026-11-05 21:19Z
Owner S4b. Prereg autopilot/T2_NATIVE_ZNZB_PREREG.md (sha256 dd941871bcc8a0eab501dc21d5edc33d9780d1d2a654bfc2d7cd9462fdf69421 in DECISIONS.md; n_tested 29,232 in T2NATIVE_NTESTED.md, written before the grids ran); code l2vast/ds3/code/t2/ (t2n.py, t2n_gate.py, t2n_null.py; same simulator and look-ahead-audited primitives as the BTC / NKD grids; every reference price is a completed bar close and every event clock is an epoch lookup); cells /mnt/l2/l2vast/ds3_t2n/. Calendar: DISCOVER_CALENDAR.csv (CPI 47, NFP 47, PPI 47, retail 48, GDP 44, PCE 44, claims 208 Thursdays, Treasury auctions with the 13:00 ET bid close from the FiscalData cache; refunding weeks = Feb / May / Aug / Nov weeks with a 3Y, 10Y and 30Y auction: 14 weeks, 42 auctions); event dates are never inferred from prices. Day sets in the sample: BIG830 228, CPI_NFP 84, CLAIMS 716 (rule Thursdays before 2023), A10 64, A30 50, ALLAUC 330, RFUND 42, ALL 3,554 trading days, RFUNDWEEK 70, MONTHEND 56. Dead-ledger check before: 'auction' / 'refund' 0 rows, 'settle' / 'release' rows are NQ books only; INSTR_RF (K7 / U7 / H7 on ZN) is a transfer test, not event books. 13-year check: only N3 (every trading day) and the claims-Thursday release set run before 2023; N1 other releases and N2 auctions have no pre-2023 calendar by design.

## ZN (native event books; 1-min proxy; costs 1 tick entry / 2 ticks stop / 1 tick flat + $2.42 half fee)
Cells with n >= 80: 6972 of 10920 (174 signal sets x 84 brackets; sets with < 30 events dropped). Share of cells with positive full-sample mean R: 0.008; median mean R -0.139; best full-sample t 0.67. Tolerant gate (L6M, HOLD > 0 with n >= 8 / 15; MID, PRE, X' not below -0.5 MDE where n_w >= 15): 270 cells, all in N1_release; N2_auction 0, N3_settle 0. With persistence (> 60% of calendar quarters positive): 20 cells; their full-sample mean R is negative (best -0.0 to -0.7 R) and the old windows are mostly thin (n_w < 15), so they are NOW-ONLY = REGIME, not leads.
Family null (random side per signal, same entries and brackets, 100 worlds, per-world max vectors saved in /mnt/l2/l2vast/ds3_t2n/ZN_null.pkl): tolerant cells per world median 78 (5-95% 9-219), observed 270 (p 0.02); clear cells per world median 0, observed 20 (p 0.02); max over cells of min(t_L6M, t_HOLD): null median 1.87, 95th 2.75, observed 1.68 (p 0.61); max full-sample t: null median 0.25, 95th 1.14, observed 0.67 (p 0.22).
By book:

```
            cells  mean_pos  tol  clear  best_t    med
fam                                                   
N1_release   3528     0.017  270     20   0.666 -0.115
N2_auction    924     0.000    0      0  -1.235 -0.159
N3_settle    2520     0.000    0      0  -4.195 -0.157
```
Best five cells by full-sample t:

```
       fam                     par              br  n  mean   mde     t  m_L6M  m_HOLD  m_MID  m_PRE  m_X'
N1_release CPI_NFP_T0844_k0.5_fade  $600/noTP/T120 83 0.029 0.123 0.666  0.140   0.068 -0.041 -0.070 0.058
N1_release CPI_NFP_T0844_k0.5_fade  $600/1.5R/T120 83 0.029 0.123 0.666  0.140   0.068 -0.041 -0.070 0.058
N1_release CPI_NFP_T0844_k0.5_fade    $600/2R/T120 83 0.029 0.123 0.666  0.140   0.068 -0.041 -0.070 0.058
N1_release CPI_NFP_T0834_k0.5_fade   $1200/2R/T120 83 0.016 0.069 0.637  0.056   0.059  0.002 -0.032 0.014
N1_release CPI_NFP_T0834_k0.5_fade $2400/noTP/T120 83 0.008 0.035 0.637  0.028   0.030  0.001 -0.016 0.007
```

## ZB (native event books; 1-min proxy; costs 1 tick entry / 2 ticks stop / 1 tick flat + $2.42 half fee)
Cells with n >= 80: 6972 of 11340 (174 signal sets x 84 brackets; sets with < 30 events dropped). Share of cells with positive full-sample mean R: 0.005; median mean R -0.143; best full-sample t 0.89. Tolerant gate (L6M, HOLD > 0 with n >= 8 / 15; MID, PRE, X' not below -0.5 MDE where n_w >= 15): 162 cells, all in N1_release; N2_auction 0, N3_settle 0. With persistence (> 60% of calendar quarters positive): 17 cells; their full-sample mean R is negative (best -0.0 to -0.7 R) and the old windows are mostly thin (n_w < 15), so they are NOW-ONLY = REGIME, not leads.
Family null (random side per signal, same entries and brackets, 100 worlds, per-world max vectors saved in /mnt/l2/l2vast/ds3_t2n/ZB_null.pkl): tolerant cells per world median 68 (5-95% 13-174), observed 162 (p 0.09); clear cells per world median 0, observed 17 (p 0.05); max over cells of min(t_L6M, t_HOLD): null median 1.79, 95th 2.42, observed 1.10 (p 0.93); max full-sample t: null median 0.49, 95th 1.50, observed 0.89 (p 0.28).
By book:

```
            cells  mean_pos  tol  clear  best_t    med
fam                                                   
N1_release   3528     0.011  162     17   0.889 -0.139
N2_auction    924     0.000    0      0  -1.538 -0.152
N3_settle    2520     0.000    0      0  -4.594 -0.145
```
Best five cells by full-sample t:

```
       fam                     par              br  n  mean   mde     t  m_L6M  m_HOLD  m_MID  m_PRE  m_X'
N1_release CPI_NFP_T0834_k0.5_fade   $2400/2R/T120 80 0.022 0.070 0.889  0.030   0.037  0.005 -0.039 0.153
N1_release CPI_NFP_T0834_k0.5_fade   $2400/1R/T120 80 0.022 0.070 0.889  0.030   0.037  0.005 -0.039 0.153
N1_release CPI_NFP_T0834_k0.5_fade $2400/noTP/T120 80 0.022 0.070 0.889  0.030   0.037  0.005 -0.039 0.153
N1_release CPI_NFP_T0834_k0.5_fade $2400/1.5R/T120 80 0.022 0.070 0.889  0.030   0.037  0.005 -0.039 0.153
N1_release CPI_NFP_T0834_k0.5_fade    6ATR/2R/T120 80 0.053 0.206 0.717  0.119   0.144  0.011 -0.090 0.347
```

**Plain sentence, ZN and ZB:** the native Treasury event books do not exist after costs: more than 99% of the cells have a negative full-sample mean R (median -0.14 R per trade), the best full-sample t is 0.67 (ZN) and 0.89 (ZB), the 13:00 auction books (N2) and the 15:00 settle fades (N3, 13-year sample) have no cell that passes even the tolerant gate, and the only tolerant cells are the CPI / NFP fade after the 08:30 release (n = 80-83 events), whose recent windows are positive but whose full-sample mean is negative (ZN -0.7 R at its best-gated cell; MDE 0.3-0.5 R): a recent-window pattern in 3.6 years of 84 events, NOW-ONLY = REGIME, not a lead. The random-side family null is at or above the observed counts and maxima. No finalists, so no frames, no walk-forward and no stack test were needed; correlation to the NQ stack is not computed for cells that fail the full-sample sign.
Correction note (S4b, native ZN/ZB interim 1): the plain sentence says the family null is 'at or above the observed counts and maxima'. That is true for the MAXIMA (max min(t_L6M, t_HOLD): ZN observed 1.68 vs null median 1.87, p 0.61; ZB 1.10 vs 1.79, p 0.93; max full-sample t: ZN 0.67 vs null 95th 1.14, p 0.22; ZB 0.89 vs 1.50, p 0.28) but NOT for the COUNTS: tolerant cells ZN 270 vs null median 78 (p 0.02) and ZB 162 vs 68 (p 0.09); tolerant + persistent cells ZN 20 vs null median 0 (p 0.02), ZB 17 vs 0 (p 0.05). The excess comes from one correlated cluster of brackets on the CPI / NFP fade set (84 events, 80-83 trades, the same signal set under 84 brackets), whose old windows are thin, and whose full-sample mean R is negative (so the cells fail the sign of the pooled sample): it is a recent-window cluster in 3.6 years of 84 events (NOW-ONLY = REGIME), the maxima say it is no stronger than random-side selection, and it is not a lead. The all-instrument family count is reported when the T-INSTR-2 pages are merged.

## GC native books (S4a) - stage 2 result
Base: GC.v.0 1-min additive back-adjusted, kernel evalk, Z2 sessions, proxy costs, prereg T2_NATIVE_GC_PREREG.md (sha 73f306cc...).
Families: London AM/PM fix drift and reaction, COMEX 08:20 opening range (5/15/30), gold vs (6E, ZN) divergence. 2,142 cells, 355 tolerant-gate passers (null p_count .015 side / .025 shift; max HOLD mean $1,011 within null, p .40 / .11).
Stage 2 (40 finalists through the evaluator): 40 of 40 FAIL. Best placebo p_book .02-.05 only for AMFIX_pre_k0.5_fade usd1200, but its 13-year percent-frame result is -$85k to -$88k with 0 of 11 years positive. Every finalist is negative over 2013-2026; no finalist has a positive 13-year total.
Plain sentence: GC native books show no edge that survives the evaluator; the gate-passer excess is a 2026-only regime effect, same as the generic GC grid. No PASS claimed. Shadow only.
Not run (and not worth it with 0 positive 13y totals): WF selector per group G1..G4 on GC_native_W.npy is queued behind ALLINST.

# DS3_INSTR2_NATIVE - BLOCK crypto / NKD native books (ZL-1, user addendum A, 2026-11-05). Research only. No PASS claim. Shadow only.

**Plain sentence: none of the native crypto / Nikkei books clears the diversifier bar - MBT (the tradable crypto leg): the Sunday-open gap and Sunday-open range books never have L3M and L6M both positive, the 09:30 NQ-sympathy fade (BTC against NQ's first 5 minutes) is positive in 2026 but placebo p_book >= 0.18, funding-time books are near zero; NKD: the Tokyo 15-minute opening-range FAILED-break fade (ATR6, 2R) earns +$1.4k a week in L6M but loses in 2024-25 and before 2023 and its placebo p_book is 0.60 (CAP-BREACH anyway), the BoJ decision-day book has 11-15 events and no NOW-ONLY cell; BTC standard has one cell with p_book 0.06 / p_family 0.04 (funding-time 08:00 UTC +5 min against the last hour, 3 ATR, 1R, 240 min) that is not tolerant (PRE -$700 a week) and is CAP-BREACH: REGIME, no lead.**
Books (scope T2_NATIVE_scope.md sha256 88410ae53d667c6055c48f14bde30f2cfbca17affe12aaa5ab2a4bfd4f5c8ae6, DECISIONS.md before any cell): BTC/MBT H1 Sunday-open gap (go / fade), H2 funding time 00/08/16 UTC, H3 09:30 ET sympathy with NQ, H4 Sunday-open range break / fade; NKD H5 Tokyo opening range (break / fade / failed), H6 Tokyo lunch break, H7 Tokyo close drift, H8 BoJ decision days. Already dead at these horizons and not repeated (WHAT_IS_DEAD_20261105.md): DIS-C weekend jump vs NQ, T-INSTR transfers of the six NQ books to BTC / MBT / NKD, DS3_INSTR K7/U7/H7 on BTC and NKD. BoJ decision days used (published calendar as known; 2026 dates after my knowledge cutoff to be verified): 20230118, 20230310, 20230428, 20230616, 20230728, 20230922, 20231031, 20231219, 20240123, 20240319, 20240426, 20240614, 20240731, 20240920, 20241031, 20241219, 20250124, 20250319, 20250501, 20250617, 20250731, 20250919, 20251030, 20251219, 20260123, 20260319, 20260428, 20260616, 20260731, 20260918, 20261030. Code l2vast/ds3/code/t2native/ (native.py, native_grid.py, native_stage2.py, native_stage3.py, native_finish.py); output /mnt/l2/l2vast/instr2_native_<sym>/; ledger T2_MBT / T2_BTC / T2_NKD_NATIVE; rows FADE_ROWS_T2_NATIVE.md.

## MBT
Cells 2304 (stage 1; ledger T2_MBT), NOW-ONLY 283 (12.3%), tolerant-lite 134, median L6M $-7/wk. Finalists 30 through instr2_eval (placebos x100 forward-only, family size 2304, walk-forward over the same book family, corr to stack V0/V2): gate_v2a pass 4, p_book <= .10: 0 (min 0.16), p_family <= .10: 0 (min 0.39, a lower bound over the finalists only), walk-forward positive at both lookbacks 0, max corr to stack 0.27. Registry total 1,877,139. Frames with entry / stop / target prices: /mnt/l2/l2vast/instr2_trades/MBT_native/ (30).
| book | cells | NOW-ONLY share | tolerant-lite share | median L6M $/wk | median HOLD $/wk |
|--|--|--|--|--|--|
| funding_time | 1152 | 14.4% | 6.5% | -15 | -11 |
| sunday_gap | 576 | 0.0% | 0.0% | -0 | -1 |
| sunday_range | 144 | 0.0% | 0.0% | -1 | -4 |
| sympathy | 432 | 27.1% | 13.7% | -80 | -59 |

| book | params | bracket | n | lots | L1M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | gate_v2a | p_book | p_family | max corr |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| funding_time | {'hour': 0, 'o': 5, 'L': 60, 'mode': 'wi | ('atr', 2) 1R T120 | 621 | 1.0 | -9 | 2 | -3 | 3 | -26 | -6 | -6 | 244 | n | 0.16 | 0.39 | 0.11 |
| sympathy | {'N': 5, 'thr': 0.0, 'mode': 'against'} | ('atr', 6) 1R T120 | 796 | 6.9 | 249 | 224 | 91 | 144 | 280 | -119 | 21 | 2267 | Y | 0.18 | 0.78 | 0.04 |
| sympathy | {'N': 5, 'thr': 0.0, 'mode': 'against'} | ('atr', 6) 1R T60 | 796 | 6.9 | 31 | 146 | 84 | 88 | 68 | -178 | -102 | 1150 | n | 0.21 | 0.80 | 0.04 |
| sympathy | {'N': 5, 'thr': 0.0, 'mode': 'against'} | ('atr', 6) 2R T120 | 796 | 6.9 | 585 | 530 | 231 | 173 | 33 | -157 | -26 | 2767 | Y | 0.21 | 0.85 | 0.05 |
| funding_time | {'hour': 8, 'o': 5, 'L': 60, 'mode': 'ag | ('atr', 2) 1R T240 | 578 | 1.0 | 3 | -5 | -2 | -1 | -13 | -14 | -1 | 240 | n | 0.23 | 0.91 | 0.09 |
| funding_time | {'hour': 0, 'o': 15, 'L': 60, 'mode': 'a | ('atr', 4) 1R T240 | 617 | 1.0 | 4 | 0 | 14 | 13 | 42 | -15 | -14 | 162 | n | 0.24 | 0.87 | 0.13 |
| funding_time | {'hour': 0, 'o': -30, 'L': 240, 'mode':  | ('atr', 6) 1R T240 | 465 | 1.0 | 12 | -1 | 2 | 0 | -2 | -19 | -0 | 277 | n | 0.31 | 1.00 | 0.05 |
| sympathy | {'N': 5, 'thr': 20.0, 'mode': 'against'} | ('atr', 6) 1R T120 | 488 | 6.9 | 632 | 607 | 130 | 114 | 169 | -76 | 114 | 2597 | Y | 0.33 | 0.95 | 0.11 |

## BTC **CAP-BREACH** (1.7% participation cap < 1 contract in every session; equal-risk lots WITHOUT the cap; reported, never a lead)
Cells 2304 (stage 1; ledger T2_BTC), NOW-ONLY 453 (19.7%), tolerant-lite 318, median L6M $-55/wk. Finalists 30 through instr2_eval (placebos x100 forward-only, family size 2304, walk-forward over the same book family, corr to stack V0/V2): gate_v2a pass 8, p_book <= .10: 1 (min 0.06), p_family <= .10: 1 (min 0.04, a lower bound over the finalists only), walk-forward positive at both lookbacks 2, max corr to stack 0.17. Registry total 1,879,443. Frames with entry / stop / target prices: /mnt/l2/l2vast/instr2_trades/BTC_native/ (30).
| book | cells | NOW-ONLY share | tolerant-lite share | median L6M $/wk | median HOLD $/wk |
|--|--|--|--|--|--|
| funding_time | 1152 | 27.3% | 19.7% | -149 | -61 |
| sunday_gap | 576 | 0.0% | 0.0% | 15 | 2 |
| sunday_range | 144 | 0.0% | 0.0% | 18 | -6 |
| sympathy | 432 | 32.2% | 21.1% | -182 | -157 |

| book | params | bracket | n | lots | L1M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | gate_v2a | p_book | p_family | max corr |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| funding_time | {'hour': 8, 'o': 5, 'L': 60, 'mode': 'ag | ('atr', 3) 1R T240 | 454 | 1.1 | 987 | 555 | 1012 | 399 | -142 | -700 | -579 | 6584 | n | 0.06 | 0.66 | 0.04 |
| funding_time | {'hour': 0, 'o': 5, 'L': 240, 'mode': 'w | ('atr', 4) 1R T240 | 326 | 1.0 | 2314 | 1963 | 958 | 541 | -116 | -604 | -258 | 5964 | n | 0.15 | 0.98 | 0.04 |
| funding_time | {'hour': 8, 'o': 5, 'L': 60, 'mode': 'ag | ('atr', 4) 1R T240 | 454 | 1.1 | 1327 | 640 | 1074 | 325 | -927 | -460 | -759 | 8459 | n | 0.15 | 0.91 | 0.07 |
| funding_time | {'hour': 0, 'o': 5, 'L': 60, 'mode': 'wi | ('atr', 2) 2R T60 | 422 | 1.1 | 168 | 472 | 358 | 893 | -137 | -236 | -671 | 5228 | n | 0.16 | 0.14 | 0.13 |
| sympathy | {'N': 5, 'thr': 0.0, 'mode': 'against'} | ('atr', 6) 2R T60 | 802 | 1.0 | 1624 | 2891 | 1078 | 799 | -74 | -1310 | -1091 | 6299 | n | 0.24 | 0.96 | 0.06 |
| funding_time | {'hour': 0, 'o': 5, 'L': 60, 'mode': 'wi | ('atr', 2) 1R T240 | 422 | 1.1 | -167 | -28 | 174 | 522 | -479 | 62 | -529 | 7013 | n | 0.28 | 0.88 | 0.11 |
| sympathy | {'N': 5, 'thr': 0.0, 'mode': 'against'} | ('atr', 6) 2R T120 | 802 | 1.0 | 4759 | 4495 | 1400 | 976 | -324 | -1044 | -458 | 18448 | Y | 0.29 | 0.99 | 0.08 |
| sympathy | {'N': 5, 'thr': 0.0, 'mode': 'against'} | ('atr', 6) 1R T60 | 802 | 1.0 | 1254 | 2031 | 731 | 633 | 349 | -1268 | -687 | 9852 | n | 0.30 | 0.96 | 0.06 |

## NKD **CAP-BREACH** (1.7% participation cap < 1 contract in every session; equal-risk lots WITHOUT the cap; reported, never a lead)
Cells 552 (stage 1; ledger T2_NKD_NATIVE), NOW-ONLY 126 (22.8%), tolerant-lite 50, median L6M $-36/wk. Finalists 15 through instr2_eval (placebos x100 forward-only, family size 552, walk-forward over the same book family, corr to stack V0/V2): gate_v2a pass 0, p_book <= .10: 0 (min 0.30), p_family <= .10: 0 (min 0.22, a lower bound over the finalists only), walk-forward positive at both lookbacks 2, max corr to stack 0.22. Registry total 1,879,995. Frames with entry / stop / target prices: /mnt/l2/l2vast/instr2_trades/NKD_native/ (15).
| book | cells | NOW-ONLY share | tolerant-lite share | median L6M $/wk | median HOLD $/wk |
|--|--|--|--|--|--|
| boj_day | 144 | 0.0% | 0.0% | -3 | 3 |
| tokyo_close | 96 | 40.6% | 21.9% | -71 | -68 |
| tokyo_lunch | 96 | 15.6% | 3.1% | -49 | -43 |
| tokyo_or | 216 | 33.3% | 12.0% | -21 | -128 |

| book | params | bracket | n | lots | L1M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | gate_v2a | p_book | p_family | max corr |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| tokyo_or | {'R': 60, 'mode': 'break'} | ('atr', 2) 2R T120 | 713 | 1.9 | 323 | 667 | 595 | 26 | -195 | -810 | -855 | 3349 | n | 0.30 | 0.96 | 0.18 |
| tokyo_or | {'R': 60, 'mode': 'break'} | ('atr', 2) 2R T60 | 713 | 1.9 | -32 | 252 | 340 | -28 | 184 | -817 | -860 | 3198 | n | 0.32 | 0.94 | 0.18 |
| tokyo_lunch | {'mode': 'go', 'resume_min': 0} | ('atr', 2) 2R T60 | 330 | 2.3 | 23 | 23 | -24 | 14 | -337 | -283 | -555 | 2460 | n | 0.39 | 0.74 | 0.22 |
| tokyo_or | {'R': 60, 'mode': 'break'} | ('atr', 2) 1R T120 | 713 | 1.9 | 453 | 627 | 435 | -56 | 151 | -992 | -540 | 2924 | n | 0.39 | 0.98 | 0.17 |
| tokyo_or | {'R': 15, 'mode': 'failed'} | ('atr', 6) 2R T60 | 656 | 1.0 | 590 | 888 | 1443 | 527 | 554 | -424 | -216 | 5094 | n | 0.60 | 0.24 | 0.13 |
| tokyo_or | {'R': 15, 'mode': 'failed'} | ('atr', 4) 2R T60 | 656 | 1.2 | 400 | 698 | 1074 | 363 | 454 | -483 | -358 | 5469 | n | 0.61 | 0.37 | 0.11 |
| tokyo_or | {'R': 15, 'mode': 'failed'} | ('atr', 6) 1R T60 | 662 | 1.0 | 590 | 888 | 1244 | 424 | 467 | -420 | -205 | 5094 | n | 0.65 | 0.22 | 0.10 |
| tokyo_close | {'mode': 'with', 'thr_atr': 0.0} | ('atr', 4) 2R T60 | 467 | 1.4 | 321 | 321 | 55 | 117 | 220 | -341 | -267 | 4069 | n | 0.83 | 0.29 | 0.08 |

13-year percent-frame check (NKD 1-minute 2013-06..2023-03, Tokyo books only): tokyo_or {'R': 15, 'mode': 'failed'}: mean/trade -55.9, years+ 1/11; tokyo_or {'R': 15, 'mode': 'failed'}: mean/trade -55.8, years+ 1/11; tokyo_or {'R': 15, 'mode': 'failed'}: mean/trade -53.9, years+ 1/11; tokyo_or {'R': 60, 'mode': 'break'}: mean/trade -45.5, years+ 2/11; tokyo_close {'mode': 'with', 'thr_atr': : mean/trade 2.6, years+ 5/11; tokyo_close {'mode': 'with', 'thr_atr': : mean/trade 2.6, years+ 5/11; tokyo_close {'mode': 'with', 'thr_atr': : mean/trade 2.6, years+ 5/11; tokyo_or {'R': 60, 'mode': 'break'}: mean/trade -28.9, years+ 4/11

## UPDATE (S4a, 2026-11-06): GC native books, Z2 purged walk-forward selector per group, ledger and rows
Ledger T2_NATIVE_GC (2,142 cells) appended; rows autopilot/FADE_ROWS_T2_NATIVE_GC.md (40 finalists, all FAIL). Z2 wf_selector.py on /mnt/l2/l2vast/ds3_t2/GC_native_W.npy with the groups as sessions (G1 London AM fix, G2 PM fix, G3 08:20 opening range, G4 gold-yield divergence), lookbacks 26 and 52 weeks, OOS 2024-01..2026-10, structural n >= 300 eligibility (378 / 504 / 378 candidate cells; G4 has none with n >= 300, its cells have 138-270 trades), 200 random-cell and 200 permutation placebos (code wf_native.py, results GC_native_wfres.pkl):
| group | lookback | pick | OOS mean $/wk | maxDD $ | L6M $/wk | HOLD $/wk | PRE $/wk | p random cell | p permuted | p bootstrap |
|--|--|--|--|--|--|--|--|--|--|--|
| G1 AM fix | 26 | top1 / top3 | -78 / -41 | 23,115 / 18,682 | 681 / 540 | 77 / 120 | -175 / -138 | .33 / .12 | .78 / .66 | .77 / .67 |
| G1 AM fix | 52 | top1 / top3 | +70 / +113 | 11,505 / 11,099 | 423 / 372 | 121 / 253 | -229 / -176 | .09 / .005 | .30 / .15 | .31 / .17 |
| G2 PM fix | 26 | top1 / top3 | +45 / -69 | 31,180 / 42,936 | 25 / -27 | 120 / 38 | 109 / -40 | .19 / .43 | .13 / .42 | .40 / .70 |
| G2 PM fix | 52 | top1 / top3 | -114 / -200 | 33,745 / 40,517 | 61 / -344 | 200 / 51 | -333 / -371 | .58 / .92 | .53 / .77 | .80 / .91 |
| G3 08:20 range | 26 | top1 / top3 | -404 / -341 | 76,377 / 70,459 | 598 / 597 | -140 / -40 | -625 / -675 | .93 / .96 | .92 / .91 | .99 / .99 |
| G3 08:20 range | 52 | top1 / top3 | -25 / +27 | 17,976 / 18,237 | 433 / 607 | 112 / 337 | -64 / -115 | .29 / .10 | .19 / .07 | .60 / .43 |
**Plain sentence: the walk-forward selector finds no money in the GC native books either: of 12 selector variants 4 have a positive out-of-sample mean (G1 52-week top-1 +$70 and top-3 +$113 a week, G2 26-week top-1 +$45, G3 52-week top-3 +$27); the best (G1, 52 weeks, top-3) has p 0.005 against a random cell but 0.15 against permuted weeks and a bootstrap p of 0.17, a PRE of -$176 a week, and the cells behind it all failed the evaluator (DS3_INSTR2_NATIVE.md GC block) - best-of-F, no lead. No PASS; Shadow only.**
