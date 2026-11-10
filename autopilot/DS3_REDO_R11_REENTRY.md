# DS3_REDO_R11_REENTRY - re-entry after a win / after a target on the state base (T-STACK-REDO R11)  [FIRST-ORDER SCREEN; PRE-PROOF until entry match >= .85; no PASS claims]
<!--SUMMARY-->
**FINAL (draft status 2026-11-10 17:09 UTC): exact-row status as of now - L6M complete for every row below; PRE/X' months are still landing in the SZ queue (refresh in order r9_score, r10_score, r11_score, exact_append when they do).** PRE-PROOF (entry match < .85); no PASS claims; stop-fill caveat applies.

| setting | live value | best exact row | holds OOS (L6M / L3M / L1M / HOLD / PRE under the 25% floor / X' / bi-weekly WF) | change recommended | panel field |
|---|---|---|---|---|---|
| re-entry after a Target (same side, any book, within 30 min) | FULL, no rule | R11_any_N30_ALL_SKIP | maxDD cut L6M 19.0, L3M 23.9, L1M 23.8; HOLD n/a; PRE 18.5 (d mean -1557.7/wk; NEW 2a(25%): OK-PRIOR (PRE d mean -1558 vs floor -3175, live PRE 12701/wk)); X' n/a; WF 36 / 18.5 | no (L6M d mean +1481/wk; see verdict) | no panel field (lot-multiplier table / policy line needed) |
| re-entry after a Target (same book, 120 min) | FULL | R11_own_N120_ALL_SKIP | maxDD cut L6M 0.3, L3M 0.3, L1M 0.2; HOLD n/a; PRE 29.6 (d mean -1138.6/wk; NEW 2a(25%): OK-PRIOR (PRE d mean -1139 vs floor -3175, live PRE 12701/wk)); X' n/a; WF 59 / 29.6 | no (L6M d mean +862/wk; see verdict) | same |
<!--/SUMMARY-->

**CAVEAT (stop fills / stop exits):** the engine fills a native stop 1.9 pt better than the stop level; live native stops were 1.28 pt worse, join 2.45 pt worse (old stack). Conflict / re-entry deltas that depend on a stopped trade inherit this optimism; netting exits use mid -/+ 0.80 pt market. Exact rows use the ROLL-FIXED engine; first-order rows use ROLL-EXCL weights of the old base list.
Generated 2026-11-10 17:09 UTC (elapsed 47 s). Base S1b-COMB 21,135 trades (43 months, ROLL-EXCL). Code code/th_stack_r9/r11_score.py. Registry /mnt/l2/l2vast/_th_joint/layers/reentry/topK.json; M tables /mnt/l2/l2vast/_th_sz/M_R11.npz.

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
| R11_any_N30_ALL_SKIP | 80.6 | 49.7 | 1739 | 32.5 / -3257 | 35 | 19.3 | OK-PRIOR (old -$1k: RECENT-ONLY) | 0.99 |
| R11_own_N120_ALL_SKIP | 64.0 | 58.7 | -3602 | 44.7 / -5347 | 65 | 39.5 | RECENT-ONLY (old -$1k: RECENT-ONLY) | 0.88 |
| R11_any_N60_ALL_SKIP | 58.1 | 39.6 | -4467 | 41.0 / -4451 | 53 | 29.1 | RECENT-ONLY (old -$1k: RECENT-ONLY) | 0.90 |
| R11_own_N60_ALL_SKIP | 55.6 | 44.0 | -3465 | 45.1 / -2576 | 62 | 27.6 | OK-PRIOR (old -$1k: RECENT-ONLY) | 0.87 |
| R11_any_N120_P7_SKIP | 53.3 | 46.8 | -5367 | 38.6 / -3304 | 69 | 29.1 | OK-PRIOR (old -$1k: RECENT-ONLY) | 0.98 |
| R11_any_N30_P7_SKIP | 53.1 | 38.6 | -3962 | 30.3 / -606 | 16 | 29.1 | OK-PRIOR (old -$1k: OK-PRIOR) | 1.00 |
| R11_any_N120_ALL_SKIP | 50.8 | 44.3 | -7895 | 39.8 / -6298 | 62 | 38.2 | RECENT-ONLY (old -$1k: RECENT-ONLY) | 0.92 |
| R11_own_N120_P7_SKIP | 46.3 | 38.1 | -3688 | 39.4 / -4014 | 66 | 31.2 | RECENT-ONLY (old -$1k: RECENT-ONLY) | 0.83 |
| R11_own_N30_ALL_SKIP | 45.1 | 28.9 | -1888 | 33.0 / -1795 | 32 | 29.1 | OK-PRIOR (old -$1k: RECENT-ONLY) | 0.92 |
| R11_any_N30_sess_london_SKIP | 44.8 | 28.6 | 1690 | 36.2 / 54 | 36 | 29.1 | OK-PRIOR (old -$1k: OK-PRIOR) | 1.00 |

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
Exact engine, SZ queue (hooks netting_hooks.py / exit_hooks.py or M_R11 table mode), cuts vs the exact S1b-COMB list (all weeks, ROLL-EXCL); a window is reported only when all its months are done. Months done per set: R11_any_N30_ALL_SKIP 32, R11_own_N120_ALL_SKIP 32, R11_any_N60_ALL_SKIP 6
| set | months | L6M cut % | L6M d mean $/wk | L6M w20 cut % | L6M eq-mean cut % | L3M cut % | L1M cut % | PRE cut % | PRE d mean | X' cut % | bi-weekly WF beat % / cut % (exact, own block) | label (rule 2a) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R11_any_N30_ALL_SKIP | 32 | 19.0 | 1481.3 | 2.2 | 24.0 | 23.9 | 23.8 | 18.5 | -1557.7 | n/a | 36 / 18.5 | NEW 2a(25%): OK-PRIOR (PRE d mean -1558 vs floor -3175, live PRE 12701/wk) | OLD(-$1k): RECENT-ONLY |
| R11_own_N120_ALL_SKIP | 32 | 0.3 | 862.4 | -5.8 | 4.0 | 0.3 | 0.2 | 29.6 | -1138.6 | n/a | 59 / 29.6 | NEW 2a(25%): OK-PRIOR (PRE d mean -1139 vs floor -3175, live PRE 12701/wk) | OLD(-$1k): RECENT-ONLY |
| R11_any_N60_ALL_SKIP | 6 | -6.4 | -4575.6 | -79.2 | -33.8 | -6.4 | -6.5 | n/a | n/a | n/a | n/a (block < 8 months) | PRIOR-UNKNOWN (PRE pending) |
Label: [EXACT partial] until L6M, PRE and X' are all present; first-order rows above stay SCREEN ONLY.

## FINAL-DRAFT VERDICT (auto-updated with the exact rows above)
FULL re-entry (live) stays. Exact: SKIP of a same-side signal within 30 min of ANY book's Target (R11_any_N30_ALL_SKIP) cuts L6M maxDD 19.0% at +$1,481/wk and PRE maxDD 18.5% (PRE d mean -$1,558/wk): OK-PRIOR under the new 25% floor (OLD -$1k floor: RECENT-ONLY). Its bi-weekly WF beats live in only 36% of refit periods, so it is a LEAD (recents + prior ok), not a CANDIDATE; X' and the remaining months are still pending. Own-book N120 and any-book N60 do not hold. Not a panel change. (draft generated 2026-11-10 17:09 UTC)

## CALIBRATED STOP-FILL / MARKET-EXIT SLIP MODEL (T-NEXT D2, post-processing; engine NOT rebuilt)
Source: ONLY data/live_frozen/StratTrades_DS7_<acct>_BLINDWEEK_reconstructed.csv (187 trades, 2026-11-01..05) against the 1-s owned-tape mid (entry offset vs tape mid on 99 trades: mean -0.03 pt, sd 2.35, so clock and contract line up). Adverse slip = fill vs mid at the fill second (long exit sells: mid - fill).
| exit type | n (frozen) | adverse slip vs fill-second mid, pts: mean (SE) [2-SE band] | median | engine convention | calibrated value used | band |
|---|---|---|---|---|---|---|
| market cut (ThL2Cut / PolicyCut / ThL2Trail) | 94 | 1.19 (0.21) [0.78, 1.60] | 0.88 | StateCut = mid -/+ 0.80 | **1.19** | 0.80-1.60 |
| BookLock market | 3 | 0.88 (0.52) [-0.17, 1.92] | 1.12 | same 0.80 | 1.19 (use the cut figure: n=3, band covers it) | 0.80-1.60 |
| StackCut market | 0 | no stack cut in the frozen week | n/a | same 0.80 | 1.19 (assumed = market cut) | 0.80-1.60 |
| stop, native 80 level (stall, no strategy join) | 2 | vs the native 80 trigger: M7 0.75, K7 3.00 -> mean 1.88 (SE 1.12); vs fill-second mid 2.31 | n/a | engine native stop fill: 1.9 pt BETTER than the level (cost -1.9) | **1.4** (pooled native: 8 old-stack stops at 1.28 + these 2) | 1.0-3.0 |
| stop, JoinThenMarket (_StopJoin / Fallback) | 0 | no join exit in the frozen file | n/a | engine mix of join fills and fallbacks, -0.5 pt pooled | 2.45 (old-stack, 21 stops, UNVALIDATED here) | 1.0-3.0 |

Honest uncertainty: the two frozen stops are Tuesday-stall exits (entered 01:48-02:04 ET, exited 02:47-02:55 after the platform gap), 0.75 and 3.00 pt past the native level: n=2 cannot fit a slip, the 2-SE band is wider than the 1.0-3.0 sensitivity band, and they are not representative of normal stops. The market-cut figure is well supported (n=94, SE 0.21): about 1.2 pt vs the fill-second mid (2.7 pt vs the mid one second before the fill, i.e. the price runs while the order travels). The engine convention (0.80) is therefore ~0.4 pt too cheap per market exit; the engine stop fills are ~3.3 pt too cheap per native stop at the central value.

Restatement method (no engine change): every base trade whose exit is Stop / StopJoin / StopJoinFallback (and whose engine cost vs the level is < 8 pt; catastrophe and gap fills left as run) has its P&L shifted by -(s - cost_engine) x lots x $20; StateCut / StackCut / BookLock by -(m - 0.80) x lots x $20; s in {1.0, 1.4, 1.875, 2.45, 3.0}, m = 1.19 (market band 0.8 / 1.6 at s = 1.4). All first-order cells (R9, R10, R11) are re-scored on the shifted base, ranking key as before. R9 live-calibrated native cost is set to s.


### Restated first-order rows (R11 re-entry tables and continuation): key = mean(eq-mean maxDD cut L6M/L3M/L1M); L6M cut % / d mean $/wk per calibration
| cell | uncalibrated key | uncal L6M cut / d mean | C10 (s=1.0,m=1.19) | C14 (s=1.4,m=1.19) | C19 (s=1.875,m=1.19) | C245 (s=2.45,m=1.19) | C30 (s=3.0,m=1.19) | C14m08 (s=1.4,m=0.8) | C14m16 (s=1.4,m=1.6) |
|---|---|---|---|---|---|---|---|---|---|
| R11_any_N30_ALL_SKIP | 80.6 | 49.7 / +1739 | 82.7 key, 54.0 cut / +3537 | 82.8 key, 54.2 cut / +3656 | 82.9 key, 54.4 cut / +3798 | 83.1 key, 54.7 cut / +3969 | 83.3 key, 55.0 cut / +4133 | 82.2 key, 54.1 cut / +3101 | 83.7 key, 55.3 cut / +4239 |
| R11_own_N120_ALL_SKIP | 64.0 | 58.7 / -3602 | 64.7 key, 57.1 cut / -1786 | 64.5 key, 56.7 cut / -1684 | 64.4 key, 56.4 cut / -1564 | 64.2 key, 56.0 cut / -1417 | 64.1 key, 55.6 cut / -1277 | 64.1 key, 57.2 cut / -2258 | 65.5 key, 57.2 cut / -1082 |
| R11_any_N60_ALL_SKIP | 58.1 | 39.6 / -4467 | 63.9 key, 43.6 cut / -2385 | 64.3 key, 43.8 cut / -2244 | 64.7 key, 44.1 cut / -2077 | 65.2 key, 44.4 cut / -1876 | 65.5 key, 44.7 cut / -1682 | 62.8 key, 43.3 cut / -2910 | 66.3 key, 45.5 cut / -1545 |
| R11_own_N60_ALL_SKIP | 55.6 | 44.0 / -3465 | 54.9 key, 40.8 cut / -1927 | 54.8 key, 40.6 cut / -1845 | 54.6 key, 40.3 cut / -1747 | 54.4 key, 39.9 cut / -1628 | 54.3 key, 39.6 cut / -1514 | 54.3 key, 40.8 cut / -2332 | 55.9 key, 41.6 cut / -1332 |
| R11_any_N120_P7_SKIP | 53.3 | 46.8 / -5367 | 53.1 key, 44.9 cut / -3903 | 52.6 key, 44.6 cut / -3865 | 52.1 key, 44.3 cut / -3819 | 51.5 key, 43.9 cut / -3763 | 50.9 key, 43.6 cut / -3710 | 52.6 key, 45.0 cut / -4352 | 53.3 key, 45.5 cut / -3352 |
| R11_any_N30_P7_SKIP | 53.1 | 38.6 / -3962 | 51.4 key, 42.5 cut / -2781 | 50.8 key, 42.1 cut / -2754 | 50.0 key, 41.4 cut / -2720 | 49.0 key, 40.6 cut / -2680 | 48.0 key, 39.9 cut / -2642 | 51.6 key, 42.4 cut / -3110 | 50.2 key, 42.1 cut / -2379 |
| R11_any_N120_ALL_SKIP | 50.8 | 44.3 / -7895 | 57.0 key, 48.2 cut / -5527 | 57.4 key, 48.4 cut / -5357 | 57.8 key, 48.7 cut / -5156 | 58.3 key, 48.8 cut / -4911 | 58.8 key, 48.8 cut / -4678 | 55.5 key, 47.8 cut / -6133 | 59.5 key, 49.4 cut / -4542 |
| R11_own_N120_P7_SKIP | 46.3 | 38.1 / -3688 | 46.1 key, 36.9 cut / -2375 | 45.7 key, 36.6 cut / -2341 | 45.2 key, 36.3 cut / -2301 | 44.5 key, 36.0 cut / -2253 | 44.0 key, 35.7 cut / -2207 | 45.8 key, 36.9 cut / -2737 | 46.2 key, 37.7 cut / -1925 |
| R11C_H7_k5_f1.0 | 18.6 | 7.3 / +1807 | 18.9 key, 6.4 cut / +1807 | 18.9 key, 6.4 cut / +1807 | 18.9 key, 6.3 cut / +1807 | 19.0 key, 6.2 cut / +1807 | 19.0 key, 6.2 cut / +1807 | 18.8 key, 6.5 cut / +1807 | 19.7 key, 8.2 cut / +1807 |

Rank of the uncalibrated top cell R11_any_N30_ALL_SKIP on the calibrated bases: C10: rank 1 of 318; C14: rank 1 of 318; C19: rank 1 of 318; C245: rank 1 of 318; C30: rank 1 of 318; C14m08: rank 1 of 318; C14m16: rank 1 of 318.

### EXACT sets restated by post-processing (s=1.40, m=1.19; ROLL-EXCL weights; windows only where every month is done): maxDD cut % / d mean $/wk, uncalibrated in brackets
| set | months | L6M | L3M | L1M | PRE |
|---|---|---|---|---|---|
| R11_any_N30_ALL_SKIP | 32 | 25.8 / +2524 (19.0 / +1501) | 27.1 / +3117 (23.9 / +2405) | 22.5 / +6436 (23.8 / +6334) | 18.0 / -2673 (18.5 / -1783) |
| R11_own_N120_ALL_SKIP | 32 | 5.3 / +1563 (0.3 / +882) | 5.3 / -5706 (0.3 / -6129) | -0.7 / -190 (0.2 / +45) | 27.6 / -1012 (29.6 / -1363) |
| R11_any_N60_ALL_SKIP | 6 | 3.1 / -3692 (-6.4 / -4556) | 3.1 / -6127 (-6.4 / -6716) | -3.0 / -279 (-6.5 / -407) | n/a |

### EXACT sets restated by post-processing (s=3.00, m=1.19; ROLL-EXCL weights; windows only where every month is done): maxDD cut % / d mean $/wk, uncalibrated in brackets
| set | months | L6M | L3M | L1M | PRE |
|---|---|---|---|---|---|
| R11_any_N30_ALL_SKIP | 32 | 26.7 / +2734 (19.0 / +1501) | 26.6 / +3202 (23.9 / +2405) | 22.3 / +6596 (23.8 / +6334) | 20.4 / -2576 (18.5 / -1783) |
| R11_own_N120_ALL_SKIP | 32 | 5.2 / +1642 (0.3 / +882) | 5.1 / -5703 (0.3 / -6129) | -0.5 / -158 (0.2 / +45) | 30.6 / -951 (29.6 / -1363) |
| R11_any_N60_ALL_SKIP | 6 | 3.3 / -3477 (-6.4 / -4556) | 3.3 / -6047 (-6.4 / -6716) | -1.3 / -130 (-6.5 / -407) | n/a |

### What the Monday file must contain to validate the calibration (>= 20 stops)
- >= 20 stop exits (target 30+), >= 10 in each stop mode actually installed (native stop-market, _StopJoin fills, _StopJoinFallback), spread over >= 3 sessions and not inside a platform stall; the strategy and native stop prices per trade (fields: strategy stop level, native/catastrophe level, order route, exit name) and the `STOP touched` timestamp from the strategy log (forward_register or NT8 log) so that slip is measured from the touch, not from the fill clock.
- For every exit (stop, cut, BookLock, StackCut, target): order-submit, ack and fill timestamps (ms) and fill price per partial fill; the market-cut and BookLock figures then split into latency vs price drift.
- The panel StStopExitMode / HmStopExitMode / StopJoinSecs / CatastrophePts as installed that week (this decides which mode each book is in).
- Acceptance: pooled stop slip within 1.0-3.0 pt with SE <= 0.4 pt at n >= 20; the market-cut figure within 1.2 +/- 0.4 pt; otherwise the calibrated table is revised and every row above re-stated.
- PROPOSAL (not executed; needs the user): engine change for the post-FINAL rebuild - native stop fill = walk of the book LAT_BOOK after the touch with a measured per-mode slip (central 1.4 pt native, 2.45 pt join-fallback blend) instead of the zero-latency pre-print walk; StateCut COST 0.80 -> 1.19 vs the fill-second mid; join fill probability calibrated to the live p_fallback 0.57.

