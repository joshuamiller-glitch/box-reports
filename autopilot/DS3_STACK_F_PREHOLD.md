# DS3 STACK F - PRE-only text (D3SKF). HOLD/X read only after this file is hashed and the look logged.

Prereg: l2vast/ds3/prereg/STK_F_prereg.md sha256 392cad1b74b0583a9e39827d9dea708697aebbe15ae6f9624ec589c14a882df1. PRE = 74 label weeks 2024-02..2025-06.

| rule | PRE standalone d_mean $/wk | MDE | delta on PRE worst-20 set (W20P) $ |
|---|---|---|---|
| A03 | +1,923 | 3,168 | +97,866 |
| A06 | +10,563 | 12,104 | +592,179 |
| B02 | +514 | 5,947 | +192,517 |
| D40 | +2,197 | 6,417 | +313,194 |
| C1 | -6,811 | 10,613 | +362,615 |
| HM5R | +2,681 | 19,962 | +708,342 |
| HM5M | +1,340 | 9,981 | +354,171 |

Section picks: {'A': 'A06', 'B': 'B02', 'C': 'C1', 'D': 'D40', 'E': 'HM5R'}. Stack order (PRE d_mean > 0, descending): ['A06', 'HM5R', 'D40', 'B02']. C1 (B1_CONS2) has PRE d_mean < 0 and is not stacked.

Cumulative PRE (APPROXIMATE additive deltas):
| after | d_mean | MDE | W20P delta |
|---|---|---|---|
| A06 | +10,563 | 12,104 | +592,179 |
| HM5R | +13,243 | 25,276 | +1,300,521 |
| D40 | +15,440 | 28,176 | +1,613,715 |
| B02 | +15,416 | 28,543 | +1,728,462 |

PRE placebo (4 random-placement rules, 200 draws, permuted within PRE): W20P delta observed +1,728,462 vs placebo mean +299,256, p95 +826,320, rank 1.000. Note: permutation keeps each rule's sum, so the PRE rank mainly tests placement on the PRE worst weeks (these rules were chosen on the same PRE data in their own sections).

Admission and gates at the HOLD look are as in the prereg (sections 2-4).
