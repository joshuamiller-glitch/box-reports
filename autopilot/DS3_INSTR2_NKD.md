

# DS3_INSTR2_NKD: T-INSTR-2 section 1, NKD own grid - interim 1 (stage 1: grid screen), 2026-11-05 20:16Z
Owner S4b. Prereg autopilot/T2_NKD_PREREG.md (sha256 77b3e9fc667a1902a893b10941da270864acda6c61da8e2817bed1007ad68552), n_tested 144,648 (T2NKD_NTESTED.md) written before the grid ran; code l2vast/ds3/code/t2/ (same engine; T2_REFPX=40000 percent-frame costs and fixed-$ stops, so the 2013-2022 years use scaled costs); cells /mnt/l2/l2vast/ds3_t2/NKD_cells.parquet; finalist trade frames /mnt/l2/l2vast/instr2_trades/NKD/. **CAP-BREACH:** the 1.7% cap is 0.12-0.37 contracts per 5 min in every session (INSTR2_SESSIONS.md), so no NKD result can qualify as a diversifier under the user's execution cap at 1 lot. Look-ahead audit: the same truncation test (0 failures in 1,369 checks on MBT; the code is shared; the NKD run uses the same functions). 13-year check: data 2013-01..2026-10 (3.29M 1-min bars), yearly windows Y13..Y26 and P13 in the cell table.
## Stage-1 summary
| series | cells (n>=30) | n>=150 | recent gate | tolerant | tolerant + persistence | share of cells with mean R > 0 | best full-sample t | cells t>3 |
|---|---|---|---|---|---|---|---|---|
| NKD CAP-BREACH | 144564 | 143976 | 1438 | 102 | 0 | 0.000 | 1.10 | 0 |

By session (cells passing each gate):

```
        g_recent  tolerant  clear
ses                              
all            2         0      0
asia          76         1      0
london        44         0      0
nyam        1115        78      0
nypm         122         0      0
pre           79        23      0
```
## Ranked table (best by full-sample t, none clears; mean R by window)
| instrument | session | family | params | L1M | L3M | L6M | HOLD | MID | PRE | X' | maxDD (R) | Calmar (R/yr / maxDD) | corr to NQ stack | stack gain (Calmar HOLD / PRE at 1x) | placebo / family | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NKD | nyam | F1_keltner | b10_ema13_atr20_m2.5 $1200/1R/T120 | +0.32 | +0.19 | +0.32 | +0.27 | +0.01 | -0.14 | +0.11 | 49.8 | -0.05 | +0.06 | 0.24->0.24 / 0.20->0.20 | pending | STAGE-1 clear+tolerant CAP-BREACH; family null pending |
| NKD | nyam | F1_keltner | b10_ema13_atr20_m2.5 $1200/1.5R/T120 | +0.30 | +0.10 | +0.31 | +0.28 | +0.07 | -0.14 | +0.08 | 54.1 | -0.05 | +0.08 | 0.24->0.24 / 0.20->0.20 | pending | STAGE-1 clear+tolerant CAP-BREACH; family null pending |
| NKD | nyam | F1_keltner | b10_ema13_atr20_m2.5 $1200/2R/T120 | +0.30 | +0.10 | +0.25 | +0.24 | +0.11 | -0.14 | +0.08 | 59.2 | -0.05 | +0.08 | 0.24->0.24 / 0.20->0.20 | pending | STAGE-1 clear+tolerant CAP-BREACH; family null pending |
| NKD | nyam | F1_keltner | b10_ema13_atr20_m2.5 $1200/noTP/T120 | +0.30 | +0.10 | +0.25 | +0.22 | +0.11 | -0.14 | +0.08 | 59.2 | -0.05 | +0.08 | 0.24->0.24 / 0.20->0.20 | pending | STAGE-1 clear+tolerant CAP-BREACH; family null pending |
| NKD | nyam | F1_keltner | b10_ema13_atr20_m2.5 $2400/1R/T120 | +0.15 | +0.03 | +0.12 | +0.12 | +0.09 | -0.07 | +0.05 | 24.2 | -0.05 | +0.07 | 0.24->0.24 / 0.20->0.20 | pending | STAGE-1 clear+tolerant CAP-BREACH; family null pending |
| NKD | nyam | F1_keltner | b10_ema13_atr20_m2.5 $2400/noTP/T120 | +0.15 | +0.03 | +0.12 | +0.10 | +0.09 | -0.07 | +0.05 | 24.9 | -0.05 | +0.06 | 0.24->0.24 / 0.20->0.20 | pending | STAGE-1 clear+tolerant CAP-BREACH; family null pending |

**Plain sentence (interim, stage 1):** NKD loses money after costs in essentially every cell: no cell of the 144,564 has a positive full-sample mean R (median -0.17 R per trade), the best full-sample t is 1.10, zero cells pass the tolerant gate with persistence, and the 102 cells that pass the tolerant gate alone are all negative over the full 13 years; with the cap below one contract in every session NKD cannot be a diversifier on this evidence. The family null for NKD is not needed to reject (the observed best t is 1.1; a random-side null on 144,564 cells would put the max above that), and it is still queued at a reduced world count under the 3-worker rule.

Note (S4b, fee omission disclosed in the crypto follow-up): the stage-1 grids for BTC / MBT / NKD charged points-denominated slippage only (2 ticks entry, 3 ticks stop, 2 ticks flat), no per-contract fee. For NKD the proxy fee of $4.84 per round trip is about 0.008 R on a 120-point ($600) stop and 0.002 R on a $2,400 stop, negligible against the median mean R of -0.17, so no NKD conclusion changes. For MBT the fee ($1.78 per lot) is 0.03-0.06 R and lowers the cluster's t from 2.0-2.7 to 1.1-1.9 (see the crypto follow-up block in DS3_INSTR2_BTC.md); the other MBT / BTCM stage-1 counts (tolerant and persistent cells) are therefore upper bounds.

FEE CORRECTION (S4b, 2026-11-06 02:22Z; autopilot/FEE_AUDIT_INSTR2.md): the NKD stage-1 grid charged no per-contract fee ($4.84 = 0.968 pt per round trip). Rerun with the fee: tolerant cells 102 -> 100, tolerant + persistent 0 -> 0, best full-sample t 1.10 -> 0.92, median cell mean R -0.168 -> -0.183. The verdict (no NKD cell passes; CAP-BREACH) is unchanged.
