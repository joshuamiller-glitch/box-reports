# DS3_DEEPEN_LOSS_PLACEBO - persistent-draw controls (bucket 300) for the LA cut/skip rules (W-LA)

**VERDICT (running): 8 control/real rows scored. A control counts only if its fire count is within 20% of the real cut count (cuts) or its keep share within 0.05 of the real rule (skips); otherwise it is NOT count-matched and is re-tuned (q). No rule is a lead until it beats its matched persistent control.**

Draw: one draw per 5-minute bucket per book and side (hash of bucket, side, book, seed), never re-drawn; PC = marked trades are cut at the first losing second after a hashed delay in 0..30 min; PS = random skip p = 0.052 (C_N18 keep share 0.948).

| cell               | win   |   weeks |   flat_wk |   keep |   d_mean_484 |   dd_cut |   dd44_cut |       ww |   cuts_wk |
|:-------------------|:------|--------:|----------:|-------:|-------------:|---------:|-----------:|---------:|----------:|
| TL3_LA_C_N18       | L3M   |      13 |     0     |  0.941 |      994.258 |    7.19  |    -10.553 | -33755.5 |    48.923 |
| TL3_LA_F_K7_AS_D40 | L3M   |      13 |     9.615 |  1.006 |      555.851 |   21.536 |      6.536 | -25118.4 |    51.231 |
| TL3_LA_F_K7_LO_D40 | L3M   |      13 |     6.538 |  1.023 |      851.632 |   11.906 |     12.555 | -32040.3 |    52.769 |
| TL3_LA_F_M7_LO_D40 | L3M   |      13 |     4.077 |  1.01  |      -95.497 |   -0.467 |      4.911 | -36540.5 |    50.077 |
| TL3_LA_C_N18       | L6M   |      26 |     0     |  0.948 |      203.257 |    7.19  |    -10.553 | -33755.5 |    53.5   |
| TL3_LA_F_K7_AS_D40 | L6M   |      26 |    11.269 |  0.997 |      430.694 |   21.536 |      6.536 | -25118.4 |    55.615 |
| TL3_LA_F_K7_LO_D40 | L6M   |      26 |     6.885 |  1.009 |      437.221 |   11.906 |     12.555 | -32040.3 |    56.462 |
| TL3_LA_F_M7_LO_D40 | L6M   |      26 |     4.269 |  1.004 |     -185.141 |   -0.467 |      4.911 | -36540.5 |    54.154 |

Real flat cuts per week (L6M): K7 asia D40 11.27, K7 london D40 6.88, M7 london D40 4.27; C_N18 keep share 0.948.
