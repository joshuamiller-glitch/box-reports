# CF4_PLANT - planted-edge power of the CF4 each-alone pipeline

A synthetic condition with a known edge (continuous AUC a against the signal R, AR(1) rho 0.7 noise, yes = top 20% of the planted score) goes through the identical cf4_zw rule (universe 83591 signals in_pos=0, nonsense 99th-percentile bar per cell, same sign every year with >=30 per side, L6M same sign, >= 8 weeks). 10 replicates per AUC; pass rate = share of (replicate x cell) tests that pass alone.

| continuous AUC | binary lift in R (ALL cell) | median zw (ALL) | pass rate ALL cell | pass rate book cells | pass rate session cells | pass rate book x session cells |
|---|---|---|---|---|---|---|
| 0.505 | 0.031 | 2.7 | 0.40 | 0.13 | 0.02 | 0.01 |
| 0.510 | 0.054 | 4.2 | 0.90 | 0.24 | 0.20 | 0.03 |
| 0.520 | 0.107 | 8.6 | 1.00 | 0.63 | 0.60 | 0.14 |
| 0.530 | 0.166 | 13.0 | 1.00 | 0.76 | 0.88 | 0.35 |
| 0.550 | 0.279 | 21.9 | 1.00 | 0.86 | 1.00 | 0.62 |
| 0.580 | 0.442 | 36.0 | 1.00 | 0.87 | 1.00 | 0.74 |

**Power statement: the pooled (ALL) cell passes a planted condition half the time or more from a binary lift of about 0.03-0.05 R per signal (continuous AUC 0.505-0.510) and nearly always from 0.1 R; the book cells need about 0.1-0.17 R, the session cells about 0.1-0.15 R and the book x session cells about 0.17-0.28 R to be found in 35-60% of tries. The median |lift| of the real CF4 conditions that did pass alone is 0.038 R in ALL cells, 0.069 (book), 0.077 (session) and 0.124 (book x session). So: edges of the size the pipeline can see in the pooled cells (>= ~0.03-0.05 R) are found, and the passing counts sit at 1-2x the nonsense rate; book x session edges below ~0.15 R per signal could exist and would NOT be detected individually. "No block clearly above controls" therefore means "no single condition with a detectable edge beyond the controls", not "no edge at all".**
