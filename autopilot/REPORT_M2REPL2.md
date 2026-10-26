# REPORT M2REPL2 - second-instrument / unread clock-parameter replication for the follow-up families (pre-registered in PREREG_AUTOPILOT.md BLOCK 'M2-REPL2' before any cell was run)

Each replication family went through the METHOD-2 harness once (fit 12 / read 3 / step 3, tilt, sign-flip family null 200 replicates, gates a-d, net-exposure check); PASS = gates a-d AND OOS Sharpe >= 0.5 x the parent; labels: a new instrument is a replication, a new parameter/clock set on the same instrument and window is robustness only. Unread checks are quoted in the pre-registration (result-file listings and report greps).

| family | label | parent (OOS Sh) | threshold | cells | OOS Sharpe | null rank | boot lo | halves net | gates a/b/c/d | max abs beta corr | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|
| R-BM13N | robustness (never-read clocks 14:40/14:50) | BM13_NQ (1.77) | 0.89 | 12 | 0.81 | 0.890 | -0.026 | -0.6 / 34.9 | 1000 | 0.07 | **FAIL** |
| R-BM13X | replication (new instruments) | BM13_NQ (1.77) | 0.89 | 36 | -0.59 | 0.225 | -4.968 | 12.5 / -247.7 | 0 | 0.34 | **FAIL** |
| R-B7X | replication (new instruments) | B7 (1.95) | 0.97 | 2304 | -1.15 | 0.045 | -0.151 | -5.1 / -7.2 | 0 | 0.10 | **FAIL** |
| R-B1X | replication (new instruments) | B1 / B1leg_BTC (1.71) | 0.85 | 900 | 0.26 | 0.685 | -0.082 | 4.6 / -0.3 | 1000 | 0.06 | **FAIL** |
| R-C10X-lr | replication (new instrument ZB) | C10S1_CL:240_lr (1.66) | 0.83 | 20 | -1.41 | 0.015 | -0.539 | -19.5 / -23.6 | 0 | 0.01 | **FAIL** |
| R-C10X-macd | replication (new instrument ZB) | C10S1_CL:240_macd (1.38) | 0.69 | 20 | -0.49 | 0.200 | -0.326 | -4.1 / -10.9 | 0 | 0.05 | **FAIL** |
| R-C10P-lr | robustness (CL, lr windows 40/60) | C10S1_CL:240_lr (1.66) | 0.83 | 40 | -0.25 | 0.355 | -0.340 | -6.2 / -4.2 | 0 | 0.02 | **FAIL** |
| R-C10P-macd | robustness (CL, macd 8/17 and 19/39) | C10S1_CL:240_macd (1.38) | 0.69 | 40 | 0.42 | 0.775 | -0.081 | 7.8 / 8.3 | 1001 | 0.08 | **FAIL** |
| R-WTR30 | robustness (unread ATR/m pairs) | WT432:ATR30_m4 (1.26) | 0.63 | 144 | 1.07 | 0.950 | +0.011 | 10.2 / 14.4 | 1111 | 0.14 | **PASS** |
| R-WTR20 | robustness (unread ATR/m pairs) | WT432:ATR20_m4 (1.19) | 0.59 | 144 | 1.03 | 0.950 | +0.010 | 11.3 / 11.5 | 1111 | 0.10 | **PASS** |
| R-WTR10 | robustness (unread ATR/m pairs) | WT432:ATR10_m3 (1.00) | 0.50 | 144 | 0.84 | 0.925 | -0.014 | 7.0 / 10.9 | 1001 | 0.04 | **FAIL** |
| R-C11R | robustness (RSI 3/15, SMA 150/250) | C11DIP (1.43) | 0.71 | 192 | 1.24 | 0.985 | +0.059 | 3.9 / 33.8 | 1111 | 0.50 | **BETA: sign-flip invalid (needs drift-matched null)** |

## Reading

- **Replication on NEW INSTRUMENTS failed for every family where it was possible:** BM13 on GC/CL/ZN/6E/ZB/HO (OOS Sharpe -0.59, null rank 0.23), B7 on NQ/HO/RB/NG/SI/HG/6E/ZB (-1.15, null rank 0.045), B1 on NQ/6E/SI/HG/HO (0.26, gate b fails), CL 240 lr and macd on ZB (-1.41 and -0.49). These mechanisms are instrument-specific in this window; the CL240, B7 and B1 passes are not evidence of a general edge.
- **Robustness on the same instrument and window:** WT432 ATR30_m4 and ATR20_m4 neighbours pass (R-WTR30 1.07, R-WTR20 1.03: gates a-d pass, null rank 0.95, Sharpe above half of the parent), R-WTR10 fails (0.84, null rank 0.925, bootstrap lower bound negative); BM13 at the unread clocks 14:40/14:50 fails (0.81 vs 0.88, null rank 0.89); CL240 with other lr / macd windows fails (-0.25, 0.42); C11DIP with RSI 3/15 and SMA 150/250 is 1.24 with null rank 0.985 but its OOS series correlates 0.50 with the index daily change, so the sign-flip null is invalid (BETA) and it cannot pass without the drift-matched random-date null.
- **WT432 is the only family with a same-instrument parameter pass, and WT is an NQ trend book correlated with the live pair (OOS corr 0.4-0.6 in REPORT_CONTROL2);** it adds no new instrument evidence.
- Chance expectation for the 12 families at 1.7% each was 0.2 passes; two robustness passes (R-WTR30, R-WTR20, which share the (25,4) pair and are one bet) are above chance but they are NOT independent of their parents (same sample window).
- Consequence for the packs: all twelve packs (B7, B1, B1leg_BTC, C10S1_CL_240_lr/_macd, C11DIP, WT432 x3, BM13_NQ, BM11_NQ, BM12_NQ) stay PROVISIONAL; the forward test (frozen weights, evaluator ap_m2_repl_forward.py) is the independent read. Cell lists, latest-fit weights and OOS weekly bands for every replication family: outputs/methods2/repl2/<family>_cells_weights.csv and <family>_bands.json (for FORWARD.md).

## Matrix extension and packs (a778 follow-ups)

- The library family matrices B7, B1, B1leg_BTC, C10S1_CL:240_lr / :macd, C11DIP and WT432 x3 were rebuilt through 2026-10-16 with the same cell definitions (ap_m2_ext_b.py / _c10 / _c11 / _wt + ap_m2_ext_merge.py): the old days reproduce to a relative difference <= 9e-8 per column (the last 3 old days, which were partial when written, were recomputed), scale per column from the regression on the old days. The C11 daily caches (outputs/autopilot/c11/daily_*.pkl) were rebuilt from the extended 1-minute files (old bars identical, backup in c11/bak_pre_ext20261017/).
- BM13/BM11/BM12 OOS series saved to outputs/methods2/oos/{BM13_NQ,BM11_NQ,BM12_NQ,BM8_RTY,Q37_RTY,BI8_YM}.npz. Weekly bands at the pair-6/6 DD size: BM13_NQ mean $11.5k / SD $46.9k; BM11_NQ $5.6k / $27.7k; BM12_NQ $4.5k / $25.3k (the BM sizes are unrealistic: BM13 corrected 2026-10-18 to 19.1 NQ at the DD size and 5.1 NQ at 20% (the earlier 238 was an 8x error plus a cell weight from 1 fit trade day; BM11 128 and BM12 163 are the same 8x error, confirmed by a027: about 16 and 20 NQ at the DD size)).
- LIVEPACK: 12 PROVISIONAL packs written (FAMILY_SPEC.md in exact NT8 terms, FAMILY_ORDERS_20260626_20261016.csv from the reconciled engines, CELLS_WEIGHTS and BANDS from ap_livepack.py after the extension); validator: 18 packs, 0 errors.

DONE M2REPL2
