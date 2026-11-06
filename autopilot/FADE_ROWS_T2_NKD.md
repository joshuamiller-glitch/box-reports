
# FADE_ROWS_T2_NKD: series NKD stage-1 top cells 2026-11-05 20:16Z
| instrument | session | family | params | L1M | L3M | L6M | HOLD | MID | PRE | X' | maxDD (R) | Calmar (R/yr / maxDD) | corr to NQ stack | stack gain (Calmar HOLD / PRE at 1x) | placebo / family | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NKD | nyam | F1_keltner | b10_ema13_atr20_m2.5 $1200/1R/T120 | +0.32 | +0.19 | +0.32 | +0.27 | +0.01 | -0.14 | +0.11 | 49.8 | -0.05 | +0.06 | 0.24->0.24 / 0.20->0.20 | pending | STAGE-1 clear+tolerant CAP-BREACH; family null pending |
| NKD | nyam | F1_keltner | b10_ema13_atr20_m2.5 $1200/1.5R/T120 | +0.30 | +0.10 | +0.31 | +0.28 | +0.07 | -0.14 | +0.08 | 54.1 | -0.05 | +0.08 | 0.24->0.24 / 0.20->0.20 | pending | STAGE-1 clear+tolerant CAP-BREACH; family null pending |
| NKD | nyam | F1_keltner | b10_ema13_atr20_m2.5 $1200/2R/T120 | +0.30 | +0.10 | +0.25 | +0.24 | +0.11 | -0.14 | +0.08 | 59.2 | -0.05 | +0.08 | 0.24->0.24 / 0.20->0.20 | pending | STAGE-1 clear+tolerant CAP-BREACH; family null pending |
| NKD | nyam | F1_keltner | b10_ema13_atr20_m2.5 $1200/noTP/T120 | +0.30 | +0.10 | +0.25 | +0.22 | +0.11 | -0.14 | +0.08 | 59.2 | -0.05 | +0.08 | 0.24->0.24 / 0.20->0.20 | pending | STAGE-1 clear+tolerant CAP-BREACH; family null pending |
| NKD | nyam | F1_keltner | b10_ema13_atr20_m2.5 $2400/1R/T120 | +0.15 | +0.03 | +0.12 | +0.12 | +0.09 | -0.07 | +0.05 | 24.2 | -0.05 | +0.07 | 0.24->0.24 / 0.20->0.20 | pending | STAGE-1 clear+tolerant CAP-BREACH; family null pending |
| NKD | nyam | F1_keltner | b10_ema13_atr20_m2.5 $2400/noTP/T120 | +0.15 | +0.03 | +0.12 | +0.10 | +0.09 | -0.07 | +0.05 | 24.9 | -0.05 | +0.06 | 0.24->0.24 / 0.20->0.20 | pending | STAGE-1 clear+tolerant CAP-BREACH; family null pending |

FEE CORRECTION (S4b, 2026-11-06 02:22Z; autopilot/FEE_AUDIT_INSTR2.md): the NKD stage-1 grid charged no per-contract fee ($4.84 = 0.968 pt per round trip). Rerun with the fee: tolerant cells 102 -> 100, tolerant + persistent 0 -> 0, best full-sample t 1.10 -> 0.92, median cell mean R -0.168 -> -0.183. The verdict (no NKD cell passes; CAP-BREACH) is unchanged.
