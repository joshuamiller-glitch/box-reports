# DS3_REDO_R11_REENTRY - re-entry after a win / after a target on the state base (T-STACK-REDO R11)  [FIRST-ORDER SCREEN; PRE-PROOF until entry match >= .85; no PASS claims]
Generated 2026-11-10 07:31 UTC (elapsed 47 s). Base S1b-COMB 21,135 trades (43 months, ROLL-EXCL). Code code/th_stack_r9/r11_score.py. Registry /mnt/l2/l2vast/_th_joint/layers/reentry/topK.json; M tables /mnt/l2/l2vast/_th_sz/M_R11.npz.

## 0. Definition
- FLAGGED trade j = its signal comes within N min (5/10/15/30/60/120) after a Target exit of the SAME side, of the same book ("own") or of any book ("any"). Policy FULL (live = reference) / HALF / SKIP on flagged trades. These are lot-multiplier tables keyed on the signal second: exact in table mode (queue prefix R11_), first-order here is a screen (mean overstated for up-size only; these are down-only).
- CONTINUATION (labelled variant, ADDS trades, not a lot rule): after a Target, limit re-entry on a pullback of k pts (5/10/20/30) within 60 min, 60/60 bracket, stop slip 2.45 pt, fee 4.84/lot, lots = x0.5 or x1.0 of the target trade, 1-s high/low path (same-second stop/target ambiguity resolved against us). Its equal-mean row scales all lots, as for every cell.
- After a cut or a stop: see the cooldown family L (SZ_L.md, cde_exact.py): not duplicated here.
- Placebo (table cells): the multiplier changes permuted among the flagged-eligible trades of the same book x session; (continuation) the synthetic P&L re-assigned to random days. Ranking key = mean(eq-mean maxDD cut L6M, L3M, L1M). Family max-stat over every R11 cell.

## 1. What follows a target (descriptive; baseline = unflagged trades of the same book)
| book | N min | flagged n | flagged mean $ | flagged win % | unflagged mean $ | unflagged win % | per-lot mean $ flagged / unflagged |
|---|---|---|---|---|---|---|---|
| K7 | 15 | 806 | 79 | 47 | 56 | 46 | 48 / 44 |
| K7 | 60 | 1995 | 107 | 48 | 40 | 46 | 69 / 35 |
| M7 | 15 | 415 | 109 | 46 | -8 | 41 | 103 / 1 |
| M7 | 60 | 1193 | -56 | 39 | 24 | 42 | -24 / 22 |
| P7 | 15 | 707 | 311 | 49 | 233 | 49 | 98 / 63 |
| P7 | 60 | 1786 | 229 | 48 | 251 | 49 | 77 / 63 |
| H7 | 15 | 16 | 1392 | 62 | 140 | 48 | 347 / 95 |
| H7 | 60 | 21 | 1289 | 57 | 136 | 48 | 237 / 96 |
| A7 | 15 | 215 | 45 | 49 | 124 | 52 | 45 / 124 |
| A7 | 60 | 254 | 122 | 52 | 106 | 51 | 122 / 106 |

Share of all trades flagged (own / any): N=5 4.4% / 8.2%, N=10 7.2% / 13.3%, N=15 10.2% / 18.1%, N=30 17.8% / 28.6%, N=60 24.9% / 37.7%, N=120 30.8% / 45.6%

## 2. Table cells on ALL books, by N and policy (own / any)
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R11_any_N30_ALL_SKIP | any N=30 SKIP | ALL | 6052 | -572380 | 1739 | 49.7 | 53.4/88.3/100.0 | 32.5 | -28.5 | 9.4 | 0.01/0.01 | 80.6 |
| R11_own_N120_ALL_SKIP | own N=120 SKIP | ALL | 6514 | -674424 | -3602 | 58.7 | 50.5/50.5/90.9 | 44.7 | 8.7 | -2.9 | 0.01/0.01 | 64.0 |
| R11_any_N60_ALL_SKIP | any N=60 SKIP | ALL | 7959 | -745401 | -4467 | 39.6 | 24.5/49.7/100.0 | 41.0 | -12.0 | -40.0 | 0.01/0.01 | 58.1 |
| R11_own_N60_ALL_SKIP | own N=60 SKIP | ALL | 5253 | -605034 | -3465 | 44.0 | 33.4/33.4/100.0 | 45.1 | -3.2 | -17.5 | 0.01/0.01 | 55.6 |
| R11_any_N120_ALL_SKIP | any N=120 SKIP | ALL | 9636 | -937224 | -7895 | 44.3 | 14.0/38.5/100.0 | 39.8 | 3.0 | -66.5 | 0.01/0.01 | 50.8 |
| R11_own_N30_ALL_SKIP | own N=30 SKIP | ALL | 3770 | -544849 | -1888 | 28.9 | 22.2/22.2/91.1 | 33.0 | -17.7 | -6.4 | 0.01/0.01 | 45.1 |
| R11_any_N30_ALL_HALF | any N=30 HALF | ALL | 2836 | -128334 | -1029 | 26.7 | 23.9/36.8/54.7 | 26.6 | -7.8 | 39.6 | 0.01/0.02 | 38.5 |
| R11_any_N120_ALL_HALF | any N=120 HALF | ALL | 4128 | -242164 | -2141 | 34.1 | 27.1/27.2/57.6 | 37.0 | 8.6 | 3.4 | 0.01/0.01 | 37.3 |
| R11_any_N60_ALL_HALF | any N=60 HALF | ALL | 3668 | -167652 | -1014 | 25.5 | 21.9/23.9/54.0 | 38.0 | 4.9 | 16.9 | 0.01/0.01 | 33.3 |
| R11_own_N120_ALL_HALF | own N=120 HALF | ALL | 2952 | -178779 | -1120 | 25.2 | 21.2/21.2/42.0 | 21.7 | 13.4 | 19.0 | 0.01/0.02 | 28.1 |
| R11_own_N60_ALL_HALF | own N=60 HALF | ALL | 2530 | -167465 | -971 | 18.0 | 14.2/14.2/42.2 | 20.8 | 9.5 | 20.0 | 0.01/0.03 | 23.5 |
| R11_own_N30_ALL_HALF | own N=30 HALF | ALL | 1855 | -164593 | -760 | 15.5 | 12.5/12.5/42.0 | 13.3 | -1.5 | 18.4 | 0.02/0.10 | 22.4 |

## 3. Best table cell per book

**K7**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R11_own_N5_K7_HALF | own N=5 HALF | K7 | 99 | -12610 | 126 | -0.1 | 0.5/0.5/0.5 | -0.3 | -0.9 | -0.2 | 0.27/0.53 | 0.5 |
| R11_own_N10_K7_HALF | own N=10 HALF | K7 | 140 | -16312 | 108 | -0.1 | 0.4/0.4/0.5 | -1.1 | 0.8 | -0.5 | 0.27/0.71 | 0.4 |

**M7**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R11_any_N60_M7_SKIP | any N=60 SKIP | M7 | 1832 | 69583 | 954 | 8.1 | 11.3/11.3/11.2 | 8.7 | 2.4 | 31.5 | 0.06/0.13 | 11.3 |
| R11_any_N30_M7_SKIP | any N=30 SKIP | M7 | 1293 | 53033 | 704 | 8.7 | 11.0/11.0/10.9 | 3.5 | -2.8 | 29.3 | 0.04/0.24 | 11.0 |

**U7**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R11_any_N10_U7_SKIP | any N=10 SKIP | U7 | 216 | 39189 | 1976 | 19.7 | 25.2/25.2/25.1 | 12.4 | -2.8 | 22.3 | 0.01/0.14 | 25.2 |
| R11_any_N15_U7_SKIP | any N=15 SKIP | U7 | 233 | 25221 | 1825 | 17.9 | 23.1/23.1/24.7 | 14.0 | -2.8 | 20.0 | 0.01/0.11 | 23.7 |

**P7**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R11_any_N120_P7_SKIP | any N=120 SKIP | P7 | 2807 | -566060 | -5367 | 46.8 | 30.0/30.0/100.0 | 38.6 | 12.7 | -40.4 | 0.01/0.01 | 53.3 |
| R11_any_N30_P7_SKIP | any N=30 SKIP | P7 | 1862 | -363981 | -3962 | 38.6 | 28.3/41.1/90.0 | 30.3 | -23.4 | 13.4 | 0.01/0.01 | 53.1 |

**H7**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R11_own_N120_H7_SKIP | own N=120 SKIP | H7 | 42 | -23746 | 113 | 0.0 | 0.5/0.5/0.5 | -2.6 | -0.0 | 2.7 | 1.00/0.80 | 0.5 |
| R11_own_N120_H7_HALF | own N=120 HALF | H7 | 24 | -12337 | 13 | 0.0 | 0.1/0.1/0.1 | -0.9 | 0.0 | 0.7 | 1.00/0.79 | 0.1 |

**A7**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R11_any_N60_A7_SKIP | any N=60 SKIP | A7 | 487 | -46356 | 71 | 3.2 | 3.6/3.6/8.2 | -3.0 | -0.0 | 4.1 | 0.03/0.76 | 5.1 |
| R11_any_N30_A7_SKIP | any N=30 SKIP | A7 | 448 | -46936 | 43 | 3.2 | 3.4/3.4/7.2 | -3.0 | -0.0 | 4.8 | 0.02/0.84 | 4.7 |

**O7**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R11_any_N120_O7_SKIP | any N=120 SKIP | O7 | 220 | -32199 | -113 | 0.0 | -0.5/-0.5/3.2 | 0.0 | -1.1 | -3.0 | 0.50/1.00 | 0.7 |
| R11_any_N60_O7_SKIP | any N=60 SKIP | O7 | 155 | -32459 | 82 | 0.0 | 0.3/0.3/0.3 | 0.0 | -2.0 | -1.4 | 1.00/1.00 | 0.3 |

## 4. Best table cell per session (flagged trades of that session)

**asia**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R11_any_N30_sess_asia_SKIP | any N=30 SKIP | sess_asia | 1784 | -493639 | -3392 | 9.1 | -7.6/-7.6/47.1 | 8.4 | -4.2 | -41.6 | 0.01/0.13 | 10.6 |
| R11_own_N120_sess_asia_HALF | own N=120 HALF | sess_asia | 921 | -172587 | -975 | 0.5 | -4.1/-4.1/26.0 | 4.2 | -2.5 | 5.1 | 0.09/0.13 | 5.9 |

**london**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R11_any_N30_sess_london_SKIP | any N=30 SKIP | sess_london | 2082 | 33903 | 1690 | 28.6 | 32.9/50.7/50.7 | 36.2 | -5.4 | 49.3 | 0.01/0.01 | 44.8 |
| R11_any_N60_sess_london_SKIP | any N=60 SKIP | sess_london | 2728 | 26243 | 306 | 33.3 | 34.1/44.1/44.0 | 34.5 | 2.4 | 51.6 | 0.01/0.02 | 40.7 |

**nyam**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R11_any_N60_sess_nyam_SKIP | any N=60 SKIP | sess_nyam | 2547 | -39308 | 208 | 9.6 | 10.4/10.4/33.9 | 12.6 | -12.5 | 46.3 | 0.05/0.07 | 18.2 |
| R11_any_N30_sess_nyam_SKIP | any N=30 SKIP | sess_nyam | 1817 | -87423 | 987 | 10.1 | 13.6/13.6/18.9 | 2.5 | -26.0 | 45.4 | 0.02/0.19 | 15.4 |

**nypm**
| cell | policy | scope | n aff | d$ total | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | X' cut % | w20 cut L6M % | p plc L6M/PRE | key |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R11_own_N5_sess_nypm_HALF | own N=5 HALF | sess_nypm | 31 | -1866 | 92 | 0.0 | 0.4/0.4/0.4 | 0.0 | 0.0 | -0.7 | 0.76/0.92 | 0.4 |
| R11_own_N10_sess_nypm_HALF | own N=10 HALF | sess_nypm | 44 | -2358 | 92 | 0.0 | 0.4/0.4/0.4 | -0.9 | 0.9 | -0.7 | 0.76/0.83 | 0.4 |

## 5. Continuation variant (pullback re-entry after a target; ADDED trades)
| cell | k pts | lots frac | scope | trades added | mean $/trade | win % | L6M mean d | L6M maxDD cut % | eq cut L6M/L3M/L1M | PRE cut % | p plc L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| R11C_H7_k5_f1.0 | k=5 | frac=1.0 | H7 | 473 | 135 | 55 | 1807 | 7.3 | 13.9/13.9/28.0 | 4.9 | 0.03 |
| R11C_H7_k10_f1.0 | k=10 | frac=1.0 | H7 | 427 | 92 | 55 | 832 | 7.3 | 10.2/10.2/23.4 | 4.9 | 0.07 |
| R11C_H7_k5_f0.5 | k=5 | frac=0.5 | H7 | 473 | 95 | 55 | 728 | 5.8 | 8.4/8.4/17.2 | 3.3 | 0.03 |
| R11C_H7_k10_f0.5 | k=10 | frac=0.5 | H7 | 427 | 74 | 55 | 783 | 5.8 | 8.7/8.7/16.0 | 3.3 | 0.05 |
| R11C_H7_k30_f1.0 | k=30 | frac=1.0 | H7 | 250 | -77 | 50 | 635 | 4.3 | 6.9/6.9/8.3 | 2.5 | 0.04 |
| R11C_H7_k20_f1.0 | k=20 | frac=1.0 | H7 | 333 | -40 | 53 | 270 | 2.7 | 3.7/3.7/8.3 | -0.2 | 0.12 |
| R11C_M7_k30_f0.5 | k=30 | frac=0.5 | M7 | 1066 | 42 | 53 | 209 | 4.0 | 4.9/4.9/4.8 | -1.4 | 0.14 |
| R11C_A7_k5_f0.5 | k=5 | frac=0.5 | A7 | 526 | 115 | 56 | 902 | -4.9 | -1.5/-1.5/14.5 | 1.6 | 0.79 |
| R11C_A7_k5_f1.0 | k=5 | frac=1.0 | A7 | 526 | 115 | 56 | 902 | -4.9 | -1.5/-1.5/14.5 | 1.6 | 0.82 |
| R11C_H7_k20_f0.5 | k=20 | frac=0.5 | H7 | 333 | -14 | 53 | 257 | 1.3 | 2.3/2.3/5.3 | -0.2 | 0.12 |
| R11C_H7_k30_f0.5 | k=30 | frac=0.5 | H7 | 250 | -40 | 50 | 274 | 1.3 | 2.5/2.5/4.0 | 1.6 | 0.14 |
| R11C_A7_k20_f0.5 | k=20 | frac=0.5 | A7 | 351 | 35 | 53 | 311 | -1.8 | -0.5/-0.5/6.8 | -1.0 | 0.51 |
| R11C_A7_k20_f1.0 | k=20 | frac=1.0 | A7 | 351 | 35 | 53 | 311 | -1.8 | -0.5/-0.5/6.8 | -1.0 | 0.44 |
| R11C_A7_k10_f0.5 | k=10 | frac=0.5 | A7 | 462 | 94 | 55 | 328 | -3.4 | -1.8/-1.8/8.5 | 0.7 | 0.72 |

## 6. Top 10 overall: bi-weekly WF (cell vs live), prior label (rule 2a), family p
| cell | key | L6M cut % | dmean L6M | PRE cut / dmean | WF2w beat % | WF2w cut % | label | p fam |
|---|---|---|---|---|---|---|---|---|
| R11_any_N30_ALL_SKIP | 80.6 | 49.7 | 1739 | 32.5 / -3257 | 35 | 19.3 | RECENT-ONLY | 0.99 |
| R11_own_N120_ALL_SKIP | 64.0 | 58.7 | -3602 | 44.7 / -5347 | 65 | 39.5 | RECENT-ONLY | 0.88 |
| R11_any_N60_ALL_SKIP | 58.1 | 39.6 | -4467 | 41.0 / -4451 | 53 | 29.1 | RECENT-ONLY | 0.90 |
| R11_own_N60_ALL_SKIP | 55.6 | 44.0 | -3465 | 45.1 / -2576 | 62 | 27.6 | RECENT-ONLY | 0.87 |
| R11_any_N120_P7_SKIP | 53.3 | 46.8 | -5367 | 38.6 / -3304 | 69 | 29.1 | RECENT-ONLY | 0.98 |
| R11_any_N30_P7_SKIP | 53.1 | 38.6 | -3962 | 30.3 / -606 | 16 | 29.1 | OK-PRIOR | 1.00 |
| R11_any_N120_ALL_SKIP | 50.8 | 44.3 | -7895 | 39.8 / -6298 | 62 | 38.2 | RECENT-ONLY | 0.92 |
| R11_own_N120_P7_SKIP | 46.3 | 38.1 | -3688 | 39.4 / -4014 | 66 | 31.2 | RECENT-ONLY | 0.83 |
| R11_own_N30_ALL_SKIP | 45.1 | 28.9 | -1888 | 33.0 / -1795 | 32 | 29.1 | RECENT-ONLY | 0.92 |
| R11_any_N30_sess_london_SKIP | 44.8 | 28.6 | 1690 | 36.2 / 54 | 36 | 29.1 | OK-PRIOR | 1.00 |

Procedure WF over the whole R11 grid: OOS cut 28.9%, d mean -4432 $/wk, beat live in 73% of 74 periods, 74 switches.
Held-out frozen live week: first-order read pending (187 trades; targets 80, flagged follow-ups too few for a verdict). Old-vs-new: R11 was never scored before; no published cell to compare.

## 7. Verdict (screen)
FULL (live) is the reference. A HALF/SKIP table is a candidate only with a lower maxDD at equal mean in L6M/L3M/L1M, OK-PRIOR, WF >= 60% and an exact table-mode run agreeing; the continuation variant is a separate book and goes to the joint stage only as an ADD layer. Exact rows: queued for the top-3 (prefix R11_).

## REFIT 2026-11-22
Trailing 26 weeks, drawdown first: pick **R11_own_N120_ALL_SKIP** (live retained: False).
| cell                  |   maxdd |   worst20 |   ulcer |    mean | live   | prior         |
|:----------------------|--------:|----------:|--------:|--------:|:-------|:--------------|
| R11_own_N120_ALL_SKIP | 33017.5 |  113353   | 10547   | 16909.5 | False  | PRIOR-UNKNOWN |
| R11_any_N30_ALL_SKIP  | 40166.2 |  142393   | 10560.6 | 22461   | False  | PRIOR-UNKNOWN |
| R11_any_N120_P7_SKIP  | 42538.2 |   48170.3 | 13770.3 | 15633.7 | False  | PRIOR-UNKNOWN |
| R11_any_N120_ALL_SKIP | 44485   |   21020.5 | 16014   | 12456.6 | False  | PRIOR-UNKNOWN |
| R11_own_N60_ALL_SKIP  | 44766.5 |   95192.3 | 13881.5 | 17513.6 | False  | PRIOR-UNKNOWN |

## EXACT rows (appended)
Exact engine, SZ queue (hooks netting_hooks.py / exit_hooks.py or M_R11 table mode), cuts vs the exact S1b-COMB list (all weeks, ROLL-EXCL); a window is reported only when all its months are done. Months done per set: R11_any_N30_ALL_SKIP 6, R11_own_N120_ALL_SKIP 6, R11_any_N60_ALL_SKIP 6
| set | months | L6M cut % | L6M d mean $/wk | L6M w20 cut % | L6M eq-mean cut % | L3M cut % | L1M cut % | PRE cut % | PRE d mean | X' cut % |
|---|---|---|---|---|---|---|---|---|---|---|
| R11_any_N30_ALL_SKIP | 6 | 19.0 | 1481.3 | 2.2 | 24.0 | 23.9 | 23.8 | n/a | n/a | n/a |
| R11_own_N120_ALL_SKIP | 6 | 0.3 | 862.4 | -5.8 | 4.0 | 0.3 | 0.2 | n/a | n/a | n/a |
| R11_any_N60_ALL_SKIP | 6 | -6.4 | -4575.6 | -79.2 | -33.8 | -6.4 | -6.5 | n/a | n/a | n/a |
Label: [EXACT partial] until L6M, PRE and X' are all present; first-order rows above stay SCREEN ONLY.
