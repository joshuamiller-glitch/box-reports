# D3CFA pre-holdout text DR5M - DR5m on NQ (reference), ES, YM, RTY, POOL=ES+YM+RTY (WFPRE 2024-02-01..2025-06-30 only; conservative tick basis R2; equal risk $1000/trade; fees $4.84 RT: ES solid, NQ proxy, YM/RTY WEAK proxies)

Prereg l2vast/ds3/prereg/CFA_DR5M_prereg.md. HOLD / WF / 2023 span NOT read yet. Placebo (a) random direction same clock, (b) random clock same rule, 40 draws.

| inst | n | tr/wk | fill rate | mean $/wk [95% CI] (MDE) | meanR | win | 2x mean | (a) eff rank [CI] (MDE) | (b) eff rank [CI] (MDE) | paired-a R [CI] (MDE) | yr share | pre-failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ | 170 | 2.3 | 1.00 | 601 [201,1,002] (572) | +0.265 | 0.57 | 584 | 441 0.97 [41,876] (578) | 594 1.00 [205,1,025] (599) | +0.195 [+0.027,+0.362] (0.239) n170 | 0.75 | year_share |
| ES | 168 | 2.2 | 1.00 | 137 [-246,520] (547) | +0.061 | 0.48 | 50 | 172 0.82 [-158,535] (504) | 182 0.90 [-208,623] (608) | +0.077 [-0.089,+0.242] (0.236) n168 | 1.24 | beats_a,beats_b,year_share |
| YM | 162 | 2.2 | 1.00 | -103 [-441,235] (483) | -0.048 | 0.43 | -177 | -74 0.30 [-379,232] (440) | -157 0.15 [-518,245] (554) | -0.034 [-0.195,+0.127] (0.230) n162 | nan | mean_up,beats_a,beats_b,cost2x_pre,year_share |
| RTY | 167 | 2.2 | 1.00 | -434 [-804,-64] (528) | -0.195 | 0.37 | -530 | -270 0.12 [-567,56] (464) | -453 0.00 [-805,-51] (552) | -0.121 [-0.281,+0.038] (0.228) n167 | nan | mean_up,beats_a,beats_b,cost2x_pre,year_share |
| POOL | 497 | 6.6 | 1.00 | -400 [-1,173,373] (1,104) | -0.060 | 0.43 | -657 | -172 0.35 [-817,529] (993) | -428 0.12 [-1,290,537] (1,302) | -0.026 [-0.119,+0.068] (0.134) n497 | nan | mean_up,beats_a,beats_b,cost2x_pre,year_share |
