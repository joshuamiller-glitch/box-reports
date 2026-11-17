# BAR SWAP fidelity (W-SWA): live time-bar signal library vs engine raw chassis S0

Rule: engine trade sig_ts (s) found in the library signal set, same side, within 2 s. Time bars K7 3 min, M7 1 min, U7 10 min, built from the MBO trades table; bar closes at the first print of the next bar (NT8 behaviour; the boundary convention alone missed 5-25% of Asia signals by 2-14 s of sparse tape). Months covered = trades-table coverage when run (extractor still building).

Per book x session (all covered months):

|                  |   n |   hit |   rate |
|:-----------------|----:|------:|-------:|
| ('K7', 'asia')   | 915 |   913 | 0.9978 |
| ('K7', 'london') | 708 |   708 | 1      |
| ('K7', 'nyam')   | 676 |   676 | 1      |
| ('K7', 'nypm')   | 596 |   596 | 1      |
| ('M7', 'london') | 872 |   872 | 1      |
| ('M7', 'nyam')   | 622 |   620 | 0.9968 |
| ('U7', 'asia')   | 264 |   264 | 1      |
| ('U7', 'london') | 256 |   255 | 0.9961 |

Per month (ALL sessions):

|   month |     K7 |     M7 |       U7 |
|--------:|-------:|-------:|---------:|
|  202304 | 1      | 1      |   1      |
|  202305 | 1      | 1      |   1      |
|  202306 | 1      | 0.9848 |   1      |
|  202307 | 1      | 1      |   1      |
|  202308 | 1      | 1      |   1      |
|  202309 | 1      | 1      | nan      |
|  202310 | 1      | 1      |   1      |
|  202311 | 1      | 1      |   1      |
|  202312 | 1      | 1      |   1      |
|  202401 | 1      | 1      |   1      |
|  202402 | 1      | 1      |   1      |
|  202605 | 0.9926 | 1      |   0.9808 |
|  202606 | 1      | 0.9942 |   1      |
|  202607 | 1      | 1      |   1      |
|  202608 | 1      | 1      |   1      |
|  202609 | 1      | 1      |   1      |
|  202610 | 1      | 1      |   1      |
