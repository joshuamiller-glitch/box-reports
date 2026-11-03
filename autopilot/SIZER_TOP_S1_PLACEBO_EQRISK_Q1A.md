# S1 top cells vs Q1-A on ts2: placebos at the same mean lots and equal-risk (S4a, 2026-11-03 16:43Z)

Variant 'down' (x1.5 side removed). Placebo rank = share of draws below the real cell (perm within book x session, dayshuf; each draw rescaled to the cell's mean lots; 100 draws). Equal-risk: lot-scale scan (0.8..1.2, linear fits) - mean of the cell at the lot scale where its maxDD equals Q1-A's, minus Q1-A's mean, $/wk. Post-hoc, Shadow only.

|                       | 0                                | 1                                | 2                                   | 3                                   | 4                                   |
|:----------------------|:---------------------------------|:---------------------------------|:------------------------------------|:------------------------------------|:------------------------------------|
| cell                  | ('g12', 'er_10m_14', 'LIN', 'A') | ('g12', 'er_10m_14', 'SIG', 'B') | ('g13', 'ers_5m_20', 1, 'LIN', 'C') | ('g13', 'ers_5m_20', 1, 'SIG', 'A') | ('g13', 'ers_5m_20', 1, 'SIG', 'B') |
| cut_L6M               | 0.411                            | 0.348                            | 0.364                               | 0.083                               | 0.234                               |
| cut_PRE               | -0.05                            | 0.028                            | 0.006                               | 0.103                               | 0.027                               |
| dmean_L6M             | 603.158                          | 1547.657                         | 1007.028                            | 650.054                             | 1164.08                             |
| dmean_PRE             | 414.421                          | 74.064                           | 52.71                               | 1388.348                            | 1125.809                            |
| drop_L6M              | 0.029                            | 0.095                            | -0.065                              | 0.079                               | 0.069                               |
| pa9_L6M               | 0.193                            | 0.157                            | 0.262                               | 0.142                               | 0.242                               |
| pa9_PRE               | 0.006                            | 0.028                            | 0.001                               | -0.002                              | -0.012                              |
| pa9_MID               | -0.607                           | -0.576                           | -0.081                              | -0.182                              | -0.186                              |
| mean_lots             | 2.686                            | 2.535                            | 2.37                                | 2.62                                | 2.53                                |
| n_perm                | 100                              | 100                              | 100                                 | 100                                 | 100                                 |
| rk_cutL6M_perm        | 0.93                             | 0.73                             | 0.38                                | 0.11                                | 0.34                                |
| rk_cutPRE_perm        | 0.87                             | 0.86                             | 0.51                                | 1.0                                 | 0.86                                |
| rk_meanL6M_perm       | 0.83                             | 0.96                             | 0.96                                | 0.81                                | 0.84                                |
| rk_meanPRE_perm       | 0.57                             | 0.72                             | 0.98                                | 1.0                                 | 0.98                                |
| plcmed_cutL6M_perm    | 0.307                            | 0.292                            | 0.38                                | 0.313                               | 0.307                               |
| plcmed_cutPRE_perm    | -0.151                           | -0.113                           | -0.001                              | -0.138                              | -0.098                              |
| n_dayshuf             | 100                              | 100                              | 100                                 | 100                                 | 100                                 |
| rk_cutL6M_dayshuf     | 0.94                             | 0.79                             | 0.4                                 | 0.04                                | 0.29                                |
| rk_cutPRE_dayshuf     | 0.85                             | 0.83                             | 0.58                                | 1.0                                 | 0.85                                |
| rk_meanL6M_dayshuf    | 0.88                             | 0.95                             | 0.97                                | 0.84                                | 0.83                                |
| rk_meanPRE_dayshuf    | 0.54                             | 0.67                             | 0.92                                | 0.92                                | 0.87                                |
| plcmed_cutL6M_dayshuf | 0.278                            | 0.27                             | 0.403                               | 0.326                               | 0.288                               |
| plcmed_cutPRE_dayshuf | -0.168                           | -0.133                           | -0.019                              | -0.113                              | -0.106                              |
| eqrisk_ls_L6M         | 1.277                            | 1.962                            | 1.339                               | 1.153                               | 1.476                               |
| eqrisk_dmean_L6M      | 6708.511                         | 24620.665                        | 6619.543                            | 3603.785                            | 13090.094                           |
| eqrisk_ls_PRE         | 0.991                            | 1.089                            | 1.222                               | 1.088                               | 0.905                               |
| eqrisk_dmean_PRE      | 1295.853                         | 1564.575                         | 2251.884                            | 3022.702                            | 966.722                             |
