# D3CFA pre-holdout text RVW1 - RVW1 on NQ (reference), ES, YM, RTY, POOL=ES+YM+RTY (WFPRE 2024-02-01..2025-06-30 only; conservative tick basis R2; equal risk $1000/trade; fees $4.84 RT: ES solid, NQ proxy, YM/RTY WEAK proxies)

Prereg l2vast/ds3/prereg/CFA_RVW1_prereg.md. HOLD / WF / 2023 span NOT read yet. Placebo (a) random direction same clock, (b) random clock same rule, 40 draws.

| inst | n | tr/wk | fill rate | mean $/wk [95% CI] (MDE) | meanR | win | 2x mean | (a) eff rank [CI] (MDE) | (b) eff rank [CI] (MDE) | paired-a R [CI] (MDE) | yr share | pre-failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ | 223 | 3.0 | 0.96 | 520 [119,920] (572) | +0.175 | 0.61 | 475 | 614 1.00 [197,1,052] (588) | 587 1.00 [132,1,076] (663) | +0.188 [+0.067,+0.308] (0.172) n223 | 0.63 | year_share |
| ES | 222 | 3.0 | 0.92 | 92 [-282,465] (533) | +0.031 | 0.53 | -34 | 426 1.00 [62,814] (527) | 431 1.00 [10,866] (623) | +0.111 [-0.009,+0.232] (0.172) n222 | 1.81 | cost2x_pre,year_share |
| YM | 221 | 2.9 | 0.93 | -72 [-429,285] (510) | -0.024 | 0.48 | -177 | 125 0.82 [-232,490] (517) | 293 0.95 [-112,694] (558) | +0.020 [-0.098,+0.139] (0.170) n221 | nan | mean_up,beats_a,beats_b,cost2x_pre,year_share |
| RTY | 202 | 2.7 | 0.91 | 120 [-247,487] (524) | +0.045 | 0.53 | -12 | 449 1.00 [73,828] (529) | 397 1.00 [-51,830] (591) | +0.135 [+0.008,+0.261] (0.180) n202 | 1.20 | beats_b,cost2x_pre,year_share |
| POOL | 645 | 8.6 | 0.92 | 140 [-797,1,077] (1,339) | +0.016 | 0.51 | -223 | 1,000 1.00 [63,1,974] (1,354) | 1,121 1.00 [117,2,183] (1,446) | +0.087 [+0.017,+0.158] (0.100) n645 | 2.57 | cost2x_pre,year_share |
