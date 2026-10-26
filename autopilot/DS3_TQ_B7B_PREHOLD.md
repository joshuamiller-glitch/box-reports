# D3Q group B7B PRE-HOLDOUT text 2026-10-26T17:11:02Z
WF-PRE 2024-02..2025-06 only; holdout 2025-07+ and second holdout 2023-04..2024-01 NOT discussed in this text (computed in the same run, looked at together after this line). MAPPED execution.
n trades whole sample; tpw trades/wk (PRE); wk = PRE weekly mean $ at 10 lots; sh annualised weekly Sharpe; ci = week-block bootstrap 95% CI of PRE weekly mean; dST/dHM = weekly mean difference vs ST10/HM10; mde = 2.8 x SE of the PRE weekly mean; plc = timing-destroyed placebo rank (per-trade mean, PRE); x2 = PRE weekly mean at 2x cost.

               cell       flag     n    tpw   win       wk    sh     ci_lo     ci_hi  corrST  corrHM       dST       dHM       mde   plc       x2  PRE_pass
0    TB7L_ES_w1_lag  EXEC-ONLY   927   2.28  0.54  1771.56  0.72  -2251.32   5703.27   -0.06   -0.03 -10470.90  -7650.92   5720.12  0.95  1503.78     False
1    TB7L_ES_w3_lag  EXEC-ONLY   838   2.07  0.48 -1338.55 -0.65  -4673.13   2080.69   -0.08   -0.16 -13581.01 -10761.03   4832.02   NaN -1382.81     False
2    TB7L_ES_w5_lag  EXEC-ONLY   777   1.87  0.54  1215.59  0.55  -2498.94   5167.68   -0.01    0.05 -11026.87  -8206.89   5182.00  0.92   796.68     False
3   TB7L_RTY_w1_lag  EXEC-ONLY  4057  14.51  0.49 -1811.28 -0.30 -11452.30   8721.80    0.14    0.08 -14053.74 -11233.76  14089.19   NaN -3902.85     False
4   TB7L_RTY_w3_lag  EXEC-ONLY  3498  13.12  0.48 -4565.88 -0.80 -14761.71   5318.56    0.04    0.05 -16808.34 -13988.36  13264.88   NaN -6512.80     False
5   TB7L_RTY_w5_lag  EXEC-ONLY  3082  12.64  0.49 -1558.73 -0.29 -10379.19   6298.41    0.11    0.00 -13801.19 -10981.21  12376.47   NaN -2894.24     False
6    TB7L_ES_w3_all  EXEC-ONLY  4895  15.36  0.50   104.61  0.02  -9753.73  10698.41   -0.02    0.11 -12137.85  -9317.87  14648.49  0.65 -1339.27     False
7   TB7L_RTY_w3_all  EXEC-ONLY  4331  13.85  0.49 -3961.56 -0.66 -13035.55   6080.31   -0.10   -0.13 -16204.02 -13384.04  13939.34   NaN -5133.88     False
8   TB7L_ES_w3_fade  EXEC-ONLY   838   2.04  0.49  -347.30 -0.19  -3654.84   2661.98    0.14    0.11 -12589.76  -9769.78   4369.70   NaN  -467.94     False
9  TB7L_RTY_w3_fade  EXEC-ONLY  3498  13.32  0.49 -4127.68 -0.71 -13240.48   5736.65   -0.02   -0.07 -16370.13 -13550.15  13582.86   NaN -3940.72     False

PRE-pass cells (wk>0, CI>0, tpw>=3, placebo>=0.95): []
