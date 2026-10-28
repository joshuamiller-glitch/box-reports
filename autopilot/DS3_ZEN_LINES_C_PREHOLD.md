# DS3_ZEN_LINES_C_PREHOLD - pre-holdout list (D3ZLN, 2026-10-28T18:26:45Z)

PRE-only (2024-02-01..2025-06-30). LINES_C entry-line search (regime 5m EMA200 = R1, and the best LINES_B line = BBEST), entry = hold candle at the line, 15-pt stop + nearest swing, PRIMARY, flat 14:00.
The cells below go to ONE logged holdout look at HOLD 2025-07-01..2026-02-06 and then X 2023-04-01..2024-01-31. Nothing in HOLD/X has been read for these cells. Selection rule: top by PRE effect vs random-in-regime among n >= 100.

| # | cell | n PRE | mean net1 | effect vs random-in-regime | CI lo | MDE80 | win | break-even |
|---|---|---|---|---|---|---|---|---|
| 1 | C|time_1m|VIDYA_50_close|tol5|BBEST | 109 | 2.008 | 3.400 | 0.853 | 3.973 | 0.661 | 0.579 |
| 2 | C|time_30s|SMMA_144_close|tol2|BBEST | 109 | 1.560 | 2.952 | 0.281 | 3.877 | 0.670 | 0.604 |
| 3 | C|time_1m|EMA_200_close|tol5|BBEST | 109 | 1.509 | 2.901 | 0.106 | 4.660 | 0.679 | 0.615 |
| 4 | C|time_1m|SMA_144_close|tol5|BBEST | 116 | 1.129 | 2.521 | 0.251 | 3.460 | 0.664 | 0.615 |
| 5 | C|time_1m|KAMA_200_close|tol5|BBEST | 118 | 1.048 | 2.440 | -0.096 | 3.754 | 0.653 | 0.609 |
| 6 | C|time_1m|SMMA_89_close|tol5|BBEST | 122 | 0.948 | 2.340 | -0.788 | 4.957 | 0.648 | 0.608 |
| 7 | C|time_3m|T3_233_close|tol2|R1 | 352 | 0.516 | 2.327 | 0.858 | 2.190 | 0.602 | 0.582 |
| 8 | C|time_1m|KAMA_377_hl2|tol5|BBEST | 115 | 0.910 | 2.302 | -0.040 | 3.375 | 0.652 | 0.613 |
| 9 | C|time_30s|WMA_377_close|tol2|BBEST | 107 | 0.763 | 2.156 | -0.164 | 3.658 | 0.626 | 0.595 |
| 10 | C|time_1m|ALMA_100_hl2|tol2|BBEST | 134 | 0.755 | 2.148 | 0.133 | 2.774 | 0.687 | 0.654 |
| 11 | C|time_1m|VIDYA_89_hl2|tol5|BBEST | 104 | 0.730 | 2.122 | -1.316 | 5.563 | 0.635 | 0.605 |
| 12 | C|time_15s|VIDYA_200_close|tol2|BBEST | 132 | 0.667 | 2.060 | -0.128 | 3.377 | 0.629 | 0.601 |
| 13 | C|time_30s|EMA_377_close|tol5|BBEST | 149 | 0.660 | 2.052 | -0.425 | 3.649 | 0.644 | 0.617 |
| 14 | C|time_30s|VIDYA_100_close|tol2|BBEST | 113 | 0.641 | 2.033 | -0.721 | 3.970 | 0.628 | 0.602 |
| 15 | C|time_1m|TMA_100_close|tol5|BBEST | 114 | 0.584 | 1.976 | 0.043 | 2.983 | 0.632 | 0.607 |
| 16 | C|time_1m|VIDYA_20_hl2|tol2|BBEST | 114 | 0.578 | 1.970 | -0.226 | 2.970 | 0.658 | 0.633 |
| 17 | C|time_1m|ALMA_100_hl2|tol5|BBEST | 191 | 0.552 | 1.944 | 0.263 | 2.471 | 0.691 | 0.666 |
| 18 | C|time_1m|KAMA_233_hl2|tol5|BBEST | 109 | 0.551 | 1.944 | -1.388 | 4.626 | 0.633 | 0.610 |
| 19 | C|tick_1000|EMA_100_close|tol5|BBEST | 111 | 0.526 | 1.918 | -0.593 | 3.577 | 0.649 | 0.626 |
| 20 | C|time_30s|EMA_377_close|tol2|BBEST | 117 | 0.517 | 1.909 | -0.579 | 3.764 | 0.667 | 0.644 |
| 21 | C|time_1m|SMMA_34_close|tol2|BBEST | 113 | 0.440 | 1.832 | -0.595 | 3.587 | 0.655 | 0.636 |
| 22 | C|time_1m|WMA_55_close|tol5|BBEST | 209 | 0.413 | 1.805 | 0.314 | 2.105 | 0.699 | 0.680 |
| 23 | C|time_1m|KAMA_50_hl2|tol2|BBEST | 130 | 0.379 | 1.771 | -0.341 | 3.129 | 0.669 | 0.653 |
| 24 | C|time_1m|KAMA_89_hl2|tol2|BBEST | 110 | 0.369 | 1.761 | -0.377 | 3.104 | 0.673 | 0.656 |
| 25 | C|time_30s|VIDYA_144_close|tol5|BBEST | 126 | 0.368 | 1.760 | -1.040 | 4.389 | 0.635 | 0.620 |
| 26 | C|time_30s|SMA_233_close|tol2|BBEST | 113 | 0.365 | 1.757 | -0.712 | 3.259 | 0.690 | 0.673 |
| 27 | C|time_3m|T3_233_close|tol5|R1 | 460 | -0.069 | 1.742 | 0.568 | 1.796 | 0.583 | 0.585 |
| 28 | C|time_1m|WMA_233_close|tol5|BBEST | 109 | 0.285 | 1.677 | -1.169 | 4.417 | 0.578 | 0.567 |
| 29 | C|time_30s|TMA_233_close|tol5|BBEST | 141 | 0.235 | 1.627 | -0.515 | 3.044 | 0.645 | 0.635 |
| 30 | C|time_30s|T3_233_close|tol5|BBEST | 123 | 0.212 | 1.604 | 0.098 | 2.335 | 0.650 | 0.641 |
| 31 | C|time_3m|TMA_377_close|tol5|R1 | 511 | -0.440 | 1.371 | 0.258 | 1.594 | 0.585 | 0.603 |
| 32 | C|time_3m|TMA_377_close|tol2|R1 | 372 | -0.447 | 1.363 | -0.039 | 2.008 | 0.581 | 0.598 |
| 33 | C|time_3m|SMMA_377_close|tol2|R1 | 288 | -0.488 | 1.323 | -0.221 | 2.247 | 0.573 | 0.592 |
| 34 | C|time_3m|TMA_34_close|tol2|R1 | 705 | -0.597 | 1.213 | 0.338 | 1.295 | 0.620 | 0.646 |
| 35 | C|time_2m|T3_377_close|tol2|R1 | 373 | -0.671 | 1.139 | -0.374 | 2.256 | 0.568 | 0.595 |
| 36 | C|time_3m|ZLEMA_233_close|tol2|R1 | 603 | -0.687 | 1.124 | 0.137 | 1.392 | 0.579 | 0.607 |
| 37 | C|time_3m|VIDYA_377_hl2|tol2|R1 | 266 | -0.808 | 1.003 | -0.616 | 2.365 | 0.560 | 0.592 |
| 38 | C|time_3m|LSMA_233_close|tol2|R1 | 578 | -0.822 | 0.988 | -0.031 | 1.488 | 0.571 | 0.604 |

PRE-stage family reality check over N = 4,712 (3652 cells with n >= 100): studentised max-statistic p of the best cell = 0.739 (raw-max p 0.411). The list is the top 30 by PRE effect (prereg rule) PLUS the top 10 cells with regime R1 not already in it (8 added) so that the 5-min-EMA200-regime results face the holdout too (directive: regime fixed at EMA200 "and separately" the best B line); the added cells are counted as holdout reads, disclosed.