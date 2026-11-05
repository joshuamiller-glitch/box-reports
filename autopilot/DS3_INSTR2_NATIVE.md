

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
