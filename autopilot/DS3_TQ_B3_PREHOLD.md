# D3Q group B3 PRE-HOLDOUT text 2026-10-26T16:45:46Z
WF-PRE 2024-02..2025-06 only; holdout 2025-07+ and second holdout 2023-04..2024-01 NOT discussed in this text (computed in the same run, looked at together after this line). MAPPED execution.
n trades whole sample; tpw trades/wk (PRE); wk = PRE weekly mean $ at 10 lots; sh annualised weekly Sharpe; ci = week-block bootstrap 95% CI of PRE weekly mean; dST/dHM = weekly mean difference vs ST10/HM10; mde = 2.8 x SE of the PRE weekly mean; plc = timing-destroyed placebo rank (per-trade mean, PRE); x2 = PRE weekly mean at 2x cost.

                   cell       flag     n    tpw   win       wk    sh     ci_lo     ci_hi  corrST  corrHM       dST       dHM       mde   plc       x2  PRE_pass
0       TB3_don3_cdb_W3  NT8-ticks  5770  23.35  0.49 -1537.00 -0.20 -14246.74  11224.10    0.09    0.20 -13779.46 -10959.48  17843.39   NaN -3139.30     False
1       TB3_don3_ofi_W3  EXEC-ONLY  1560   7.25  0.53  5341.40  1.29  -1479.40  12529.23    0.07   -0.05  -6901.06  -4081.08   9680.45  0.98  4066.15     False
2     TB3_don3_burst_W3  NT8-ticks   513   2.63  0.47 -1732.08 -0.67  -6085.18   2249.51    0.00    0.08 -13974.54 -11154.56   6021.16   NaN -1906.17     False
3   TB3_don3_sweep15_W5   NT8-bars  1137   5.32  0.51  1241.83  0.37  -4162.37   6838.14   -0.08   -0.08 -11000.62  -8180.64   7745.46  0.82   529.79     False
4       TB3_don5_cdb_W3  NT8-ticks  4577  20.41  0.50  -909.68 -0.15 -11174.75   8774.91    0.28    0.39 -13152.14 -10332.16  13970.93   NaN -4290.64     False
5       TB3_don5_ofi_W3  EXEC-ONLY  1080   5.41  0.54  4264.85  1.15  -2160.89  10532.90    0.27    0.19  -7977.61  -5157.63   8637.39  0.95  3519.82     False
6     TB3_don5_burst_W3  NT8-ticks   356   1.93  0.45 -2262.58 -0.99  -6177.78   1431.49    0.02    0.08 -14505.03 -11685.05   5351.98   NaN -2379.15     False
7      TB3_kelt5_cdb_W3  NT8-ticks  3703  16.76  0.50 -1130.54 -0.18 -11503.06   9227.20    0.11    0.31 -13372.99 -10553.01  14761.78   NaN -2307.12     False
8      TB3_kelt5_ofi_W3  EXEC-ONLY   889   4.25  0.55  4604.25  1.56   -240.72   9265.13    0.21    0.10  -7638.20  -4818.22   6902.88  0.95  3987.18     False
9    TB3_kelt5_burst_W3  NT8-ticks   293   1.59  0.52   729.76  0.35  -2653.39   4053.06    0.07    0.18 -11512.70  -8692.72   4796.69  0.65   573.51     False
10       TB3_st5_cdb_W3  NT8-ticks  1778   8.60  0.49 -4130.84 -0.85 -12377.44   3544.34    0.02    0.12 -16373.30 -13553.32  11318.47   NaN -5181.65     False
11       TB3_st5_ofi_W3  EXEC-ONLY   468   2.31  0.57  3346.28  1.28   -805.31   7617.73    0.34    0.07  -8896.18  -6076.20   6113.20  1.00  2956.56     False
12      TB3_hma5_cdb_W3  NT8-ticks  3046  14.01  0.50  -123.97 -0.02  -9155.01   8781.97    0.11    0.20 -12366.43  -9546.45  13175.52   NaN -1526.97     False
13  TB3_hma5_sweep15_W3   NT8-bars  1785   8.73  0.48 -5896.70 -1.16 -14806.26   3207.42   -0.14   -0.27 -18139.16 -15319.18  11819.17   NaN -6964.94     False
14  TB3_hma5_sweep30_W3   NT8-bars  1005   5.09  0.49 -2859.77 -0.88  -8290.71   2935.79   -0.16   -0.26 -15102.22 -12282.24   7618.43   NaN -3393.53     False
15      TB3_hma5_ofi_W3  EXEC-ONLY   664   3.07  0.50  -161.17 -0.06  -4475.00   4083.15   -0.00   -0.14 -12403.63  -9583.65   6220.64   NaN  -491.01     False
16      TB3_don3_cdb_W1  NT8-ticks  2585  12.45  0.51  1688.13  0.36  -5712.80   9236.24    0.06    0.18 -10554.33  -7734.35  11057.65  0.65   254.67     False
17      TB3_don3_cdb_W5  NT8-ticks  6356  24.33  0.49 -2323.61 -0.34 -13599.09   8046.45    0.17    0.29 -14566.07 -11746.09  15887.89   NaN -5400.05     False
18      TB3_don3_ofi_W1  EXEC-ONLY   480   2.32  0.55  2564.90  1.11  -1236.26   6446.16    0.08    0.10  -9677.56  -6857.58   5408.90  0.92  1978.93     False
19       TB3_cdb_ofi_W3  EXEC-ONLY  1521   6.87  0.56  8571.59  2.12   2016.27  15387.35    0.27    0.20  -3670.87   -850.89   9418.65  1.00  7511.71      True
20     TB3_cdb_burst_W3  NT8-ticks   633   3.12  0.44 -4668.74 -1.68  -9116.92      6.37    0.08    0.11 -16911.19 -14091.21   6486.89   NaN -4851.47     False

PRE-pass cells (wk>0, CI>0, tpw>=3, placebo>=0.95): ['TB3_cdb_ofi_W3']
