# ASIA FADE TABLE (bare, L6M 2026-05..10, L3M 08..10; $/wk, ulcer, max DD, worst week; stack sets x4 lots divided by 4 = 1-lot units; fade sizes 0.25/0.5/1 = 1/2/4 lots vs members at 4 lots)

## On Asia final STKd8da2eb47b (4 books)

| set | L6M $/wk | L3M $/wk | L6M ulcer | L6M max DD | L6M worst wk |
|---|---|---|---|---|---|
| WITHOUT fade (BF4_BASE /4) | 6833 | 5619 | 3528 | -12811 | -5197 |
| Le001fe42 P45 size 0.25 | 7455 | 6357 | 3618 | -13138 | -5146 |
| Le001fe42 P45 size 0.5 | 8043 | 7013 | 3708 | -13450 | -5078 |
| Le001fe42 P45 size 1 | 9179 | 8372 | 4031 | -14127 | -4977 |
| L1acc170a P45 size 0.25 | 7361 | 5979 | 3305 | -11897 | -5366 |
| L1acc170a P45 size 0.5 | 7830 | 6347 | 3341 | -11591 | -5537 |
| L1acc170a P45 size 1 | 8297 | 6713 | 4236 | -17269 | -10193 |
| L302f2cbb P60 size 0.25 | 7325 | 5998 | 3377 | -13300 | -5197 |
| L302f2cbb P60 size 0.5 | 7805 | 6351 | 3372 | -13944 | -5197 |
| L302f2cbb P60 size 1 | 8694 | 6928 | 3634 | -15682 | -5197 |
| L051dcad5 P30 size 0.25 | 7291 | 5995 | 3378 | -13086 | -5201 |
| L051dcad5 P30 size 0.5 | 7619 | 6239 | 3352 | -13370 | -5208 |
| L051dcad5 P30 size 1 | 8231 | 6761 | 3525 | -13966 | -5224 |
| Le3823c3e P45 size 0.25 | 7225 | 5833 | 3350 | -12918 | -5421 |
| Le3823c3e P45 size 0.5 | 7608 | 6038 | 3325 | -13043 | -5645 |
| Le3823c3e P45 size 1 | 8262 | 6243 | 3603 | -14142 | -6095 |

## On J502 alone

| set | L6M $/wk | L3M $/wk | L6M ulcer | L6M max DD | L6M worst wk |
|---|---|---|---|---|---|
| WITHOUT fade (BF4_BASE /4) | 2105 | 2489 | 546 | -1940 | -1635 |
| Le001fe42 P45 size 0.25 | 2727 | 3226 | 652 | -2218 | -1583 |
| Le001fe42 P45 size 0.5 | 3315 | 3882 | 894 | -3250 | -1516 |
| Le001fe42 P45 size 1 | 4452 | 5241 | 1632 | -5513 | -1942 |
| L1acc170a P45 size 0.25 | 2634 | 2848 | 574 | -2199 | -1803 |
| L1acc170a P45 size 0.5 | 3103 | 3216 | 889 | -3528 | -1975 |
| L1acc170a P45 size 1 | 3569 | 3583 | 2159 | -8598 | -5771 |
| L302f2cbb P60 size 0.25 | 2598 | 2867 | 709 | -2696 | -1635 |
| L302f2cbb P60 size 0.5 | 3077 | 3220 | 1038 | -3660 | -1972 |
| L302f2cbb P60 size 1 | 3967 | 3797 | 1870 | -5629 | -4279 |
| L051dcad5 P30 size 0.25 | 2563 | 2864 | 624 | -2796 | -1638 |
| L051dcad5 P30 size 0.5 | 2892 | 3109 | 866 | -4560 | -1646 |
| L051dcad5 P30 size 1 | 3503 | 3631 | 1598 | -8136 | -2245 |
| Le3823c3e P45 size 0.25 | 2498 | 2703 | 696 | -2612 | -1858 |
| Le3823c3e P45 size 0.5 | 2880 | 2908 | 956 | -3994 | -2808 |
| Le3823c3e P45 size 1 | 3534 | 3112 | 1623 | -6811 | -5635 |

## Each fade alone (1 lot, R0BR set) and daily L6M correlation with the stack (BF1_BASE)

| fade | bar / trigger | bracket | L6M $/wk | L3M $/wk | ulcer | max DD | worst wk | corr with stack (daily) |
|---|---|---|---|---|---|---|---|---|
| Le001fe42 | mrenko_20 trendline reject_native tol1.0 body | P45 | 2487 | 2950 | 1979 | -6481 | -3756 | 0.09 |
| L1acc170a | kagi_20 vwap false_break M3 k0.5 | P45 | 2113 | 1439 | 2279 | -5967 | -2647 | 0.20 |
| L302f2cbb | time_m_60 fib60 reject_native tol0.5 body | P60 | 1971 | 1515 | 2215 | -6292 | -4604 | 0.25 |
| L051dcad5 | pnf_14 piv_wf false_break_native M2 k0.5 | P30 | 1832 | 1502 | 2128 | -6976 | -2613 | 0.16 |
| Le3823c3e | vsess_450 gaps false_break_native M2 k0.5 | P45 | 1570 | 856 | 2135 | -5904 | -5573 | 0.20 |
