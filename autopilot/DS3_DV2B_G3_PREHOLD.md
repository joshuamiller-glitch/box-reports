# D3D2B pre-holdout text G3 (WFPRE 2024-02-01..2025-06-30 only; conservative tick basis; equal risk $1000/trade; fees $4.84 RT/leg, WEAK proxies except ES/NQ)

Prereg l2vast/ds3/prereg/DV2B_G3_prereg.md. HOLD / WF / 2023 span NOT read. Placebo (a) random sign same clock, (b) random clock same rule, 40 draws. F=15; best-of-F p95 of (b) effect null = 208.

| cell | n | tr/wk | mean $/wk [95% CI] (MDE) | 2x mean | (a) eff rank [CI] (MDE) | (b) eff rank [CI] (MDE) | paired-a R [CI] (MDE) | yr share | pre-failed |
|---|---|---|---|---|---|---|---|---|---|
| LAG1000_NQ/ES | 179 | 2.4 | -599 [-927,-271] (469) | -752 | -423 0.00 [-722,-114] (450) | -359 0.00 [-686,-65] (451) | -0.177 [-0.309,-0.046] (0.187) | nan | mean_up,beats_a,beats_b,cost2x_pre,year_share |
| LAG1000_RTY/ES | 180 | 2.4 | -86 [-472,300] (551) | -252 | 40 0.68 [-357,428] (552) | 11 0.53 [-397,401] (538) | +0.016 [-0.152,+0.185] (0.241) | nan | mean_up,beats_a,beats_b,cost2x_pre,year_share |
| LAG1000_YM/ES | 180 | 2.4 | -314 [-600,-28] (409) | -504 | -107 0.35 [-368,208] (411) | -139 0.05 [-381,109] (366) | -0.044 [-0.183,+0.095] (0.199) | nan | mean_up,beats_a,beats_b,cost2x_pre,year_share |
| LAG1000_NQ/RTY | 184 | 2.5 | -174 [-458,109] (405) | -258 | -108 0.30 [-369,184] (402) | -20 0.38 [-248,220] (356) | -0.044 [-0.183,+0.096] (0.199) | nan | mean_up,beats_a,beats_b,cost2x_pre,year_share |
| LAG1000_ALL4 | 180 | 2.4 | -41 [-248,166] (296) | -87 | -0 0.47 [-200,194] (300) | 12 0.55 [-190,199] (296) | -0.000 [-0.100,+0.099] (0.142) | nan | mean_up,beats_a,beats_b,cost2x_pre,year_share |
| LAG1130_NQ/ES | 174 | 2.3 | -250 [-448,-52] (282) | -356 | -155 0.07 [-332,32] (271) | 13 0.55 [-98,130] (161) | -0.067 [-0.151,+0.018] (0.121) | nan | mean_up,beats_a,beats_b,cost2x_pre,year_share |
| LAG1130_RTY/ES | 174 | 2.3 | -119 [-316,79] (282) | -215 | -18 0.42 [-206,166] (285) | -8 0.50 [-110,95] (147) | -0.008 [-0.091,+0.076] (0.120) | nan | mean_up,beats_a,beats_b,cost2x_pre,year_share |
| LAG1130_YM/ES | 183 | 2.4 | -228 [-431,-26] (289) | -365 | -109 0.15 [-309,95] (296) | -33 0.30 [-150,72] (154) | -0.045 [-0.145,+0.056] (0.144) | nan | mean_up,beats_a,beats_b,cost2x_pre,year_share |
| LAG1130_NQ/RTY | 173 | 2.3 | -159 [-325,7] (237) | -214 | -107 0.12 [-269,57] (235) | -12 0.45 [-106,85] (141) | -0.046 [-0.121,+0.028] (0.107) | nan | mean_up,beats_a,beats_b,cost2x_pre,year_share |
| LAG1130_ALL4 | 174 | 2.3 | -117 [-245,11] (183) | -150 | -77 0.15 [-196,53] (194) | -63 0.17 [-151,19] (125) | -0.033 [-0.090,+0.023] (0.081) | nan | mean_up,beats_a,beats_b,cost2x_pre,year_share |
| LAG1400_NQ/ES | 169 | 2.3 | -123 [-232,-15] (155) | -201 | -42 0.17 [-160,66] (165) | 122 1.00 [10,240] (167) | -0.019 [-0.066,+0.029] (0.068) | nan | mean_up,beats_a,cost2x_pre,year_share |
| LAG1400_RTY/ES | 173 | 2.3 | 23 [-117,163] (200) | -64 | 104 0.95 [-26,237] (192) | 114 0.95 [6,230] (158) | +0.045 [-0.013,+0.104] (0.084) | 1.22 | beats_a,cost2x_pre,year_share |
| LAG1400_YM/ES | 175 | 2.3 | -151 [-268,-33] (168) | -257 | -37 0.12 [-155,77] (165) | 34 0.70 [-116,169] (215) | -0.016 [-0.063,+0.030] (0.066) | nan | mean_up,beats_a,beats_b,cost2x_pre,year_share |
| LAG1400_NQ/RTY | 171 | 2.3 | -70 [-201,60] (187) | -116 | -26 0.35 [-156,98] (187) | 60 0.75 [-59,182] (180) | -0.012 [-0.065,+0.042] (0.077) | nan | mean_up,beats_a,beats_b,cost2x_pre,year_share |
| LAG1400_ALL4 | 165 | 2.2 | -47 [-125,31] (112) | -73 | -16 0.40 [-92,56] (112) | 12 0.57 [-73,82] (111) | -0.007 [-0.038,+0.024] (0.044) | nan | mean_up,beats_a,beats_b,cost2x_pre,year_share |
| POOL_LAG1000 | 723 | 9.6 | -1,173 [-1,934,-413] (1,087) | -1,766 | -598 0.07 [-1,343,146] (1,085) | -507 0.00 [-1,237,191] (1,029) | -0.062 [-0.135,+0.011] (0.104) | nan | mean_up,beats_a,beats_b,cost2x_pre,year_share |
| POOL_LAG1130 | 704 | 9.4 | -756 [-1,294,-217] (770) | -1,151 | -389 0.03 [-894,131] (748) | -40 0.30 [-322,250] (416) | -0.041 [-0.085,+0.002] (0.062) | nan | mean_up,beats_a,beats_b,cost2x_pre,year_share |
| POOL_LAG1400 | 688 | 9.2 | -321 [-671,28] (499) | -637 | -2 0.50 [-350,343] (509) | 331 1.00 [77,605] (402) | -0.000 [-0.026,+0.026] (0.037) | nan | mean_up,beats_a,cost2x_pre,year_share |
