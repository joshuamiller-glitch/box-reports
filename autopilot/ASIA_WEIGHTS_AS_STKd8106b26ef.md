# ASIA_WEIGHTS_AS_STKd8106b26ef - whole-lot weight search, TRULY BARE stack TL3_ALN_AS_STKd8106b26ef (W-WEIGHTS, 2026-11-23 01:44Z)

**HEADLINE.** Best whole-lot vector at 20 lots total: 3-8-2-6-1 (lots MF1..MF5): raw L6M ulcer 13015 vs 15873 for equal 4-4-4-4-4 and 39892 vs 38613 $/wk; at equal L6M ulcer (analytic scaling k=1.22) 48650 vs 38613 $/wk (+26%). Unconstrained best: 1-6-1-2-1 at equal L6M ulcer 71688 $/wk (+86% vs equal weights).
**BUT NOT STABLE.** The best vectors win only 0.16-0.34 of the 14-day blocks against equal weights (floor 0.58) and the 182-day walk-forward re-pick wins 0.2/0.225 of blocks: a recent-window winner that does not repeat, so the weight edge is NOT proven; equal weights stay the build default and the pin is unchanged. Exact-engine verification: done, see the table at the bottom.

Order 2210Z (Josh: "so all the books magically have the same weight?" / "yes to both"). Books: MF1 Lb0e6dfa3.BRF40_80; MF2 L385f4f2e.J502; MF3 L92a90948; MF4 L6b373671.BRP60; MF5 L578701ed.BRF30_90. Research only; truly bare (R0: no StackCut / BookLock / caps / stops / sizer / zones / Trade Health), 1-lot-unit fills at the stated lots, net of engine fees.

**Method.** The bare stack runs the five books independently, so a lots vector = SUM over books of that book's daily P&L at its own lots. Per-book series come from uniform-lot bare stack runs at lots [1, 2, 3, 4, 5, 6, 7, 8] (lots 1/2/4 = the bare-fit base sets, 3/5/6/7/8 = new WU sets), split by the trade `book` column. Fills at size and no-overlap make this an approximation (trade counts drift by a few per 7,800 across lot sizes), so the top vectors are checked by EXACT engine runs below. Grid: 0..8 whole lots per book (lots [1, 2, 3, 4, 5, 6, 7, 8] available; 0 = book dropped).

**Basis (recents).** Every vector is scaled by a common fractional k to the reference's L6M ULCER (equal recent risk) and ranked on scaled L6M $/wk, drawdown first: scaled L6M max drawdown and worst week no more than 15% worse than the reference, L3M ulcer no more than 15% worse; prior years are a CHECK only (blocked only by a negative year in 2023/24/25 or persistence < 0.58). Reference = equal weights at 4 lots per book (20 lots total). Cells: ulcer / max DD / worst week / worst day / $ per week. L6M = 202605-202610, L3M = 202608-202610. Persistence = share of 14-day blocks in which the pick beats the reference (drawdown first); walk-forward = re-pick every 14 days on the trailing 182 days, score the next block against equal weights.

### Equal weights (the reference rows, raw, no scaling)

| weights (lots MF1..MF5) | total lots | k | L6M | L3M | 2023 | 2024 | 2025 | blocks | no negative year | 15% guard |
|---|---|---|---|---|---|---|---|---|---|---|
| 1-1-1-1-1 (equal 1-1-1-1-1 (5 lots)) | 5 | 1.00 | 3101 / -9450 / -4971 / -6578 / 10834 | 3375 / -9283 / -1858 / -6578 / 10600 | 5200 / -11178 / -7756 / -4718 / 1042 | 4545 / -16311 / -8171 / -8853 / 1917 | 6567 / -17403 / -9888 / -11445 / 1982 | 0.065 | yes | yes |
| 2-2-2-2-2 (equal 2-2-2-2-2 (10 lots)) | 10 | 1.00 | 7070 / -21015 / -19862 / -13215 / 20495 | 7361 / -21015 / -6171 / -13215 / 20067 | 10615 / -22507 / -15616 / -9477 / 2030 | 10096 / -37462 / -20786 / -17860 / 3565 | 13729 / -37467 / -23895 / -24160 / 3516 | 0.065 | yes | yes |
| 4-4-4-4-4 (equal weights 4-4-4-4-4 (20 lots)) | 20 | 1.00 | 15873 / -52366 / -40859 / -32739 / 38613 | 16860 / -52366 / -22627 / -26585 / 39296 | 20618 / -46348 / -26737 / -19054 / 3876 | 20923 / -77184 / -42246 / -36320 / 6671 | 32579 / -91844 / -64733 / -47595 / 5269 | 1.0 | yes | yes |

### Best whole-lot vectors with the stack total fixed at 20 lots - RAW at their own lots

| weights (lots MF1..MF5) | total lots | k | L6M | L3M | 2023 | 2024 | 2025 | blocks | no negative year | 15% guard |
|---|---|---|---|---|---|---|---|---|---|---|
| 3-8-2-6-1 (rank 1) | 20 | 1.00 | 13015 / -48008 / -19806 / -38986 / 39892 | 13986 / -42933 / -10506 / -38986 / 43542 | 23141 / -53024 / -22324 / -18221 / 2329 | 29320 / -95667 / -36673 / -25070 / 5408 | 34352 / -92130 / -58292 / -36721 / 5312 | 0.323 | yes | yes |
| 3-8-3-5-1 (rank 2) | 20 | 1.00 | 12546 / -47104 / -20536 / -30302 / 38293 | 13761 / -42918 / -11511 / -30302 / 42220 | 20913 / -47852 / -18395 / -18001 / 2275 | 28975 / -97214 / -36868 / -25070 / 5483 | 32601 / -90772 / -61847 / -34200 / 5833 | 0.312 | yes | yes |
| 4-8-2-4-2 (rank 3) | 20 | 1.00 | 13645 / -51425 / -21945 / -27591 / 41125 | 16103 / -51425 / -19252 / -26848 / 42874 | 19036 / -45616 / -17485 / -18275 / 3056 | 25801 / -82718 / -42800 / -32997 / 5937 | 32736 / -89653 / -67758 / -39979 / 5511 | 0.344 | yes | yes |

### Best whole-lot vectors with the stack total fixed at 20 lots - SCALED to the reference's L6M ulcer (analytic, fractional lots) beside equal weights

| weights (lots MF1..MF5) | total lots | k | L6M | L3M | 2023 | 2024 | 2025 | blocks | no negative year | 15% guard |
|---|---|---|---|---|---|---|---|---|---|---|
| 3-8-2-6-1 (rank 1) | 20 | 1.22 | 15873 / -58549 / -24154 / -47546 / 48650 | 17056 / -52360 / -12812 / -47546 / 53103 | 28222 / -64667 / -27225 / -22221 / 2840 | 35758 / -116673 / -44725 / -30574 / 6595 | 41894 / -112359 / -71092 / -44784 / 6479 | 0.323 | yes | yes |
| 3-8-3-5-1 (rank 2) | 20 | 1.27 | 15873 / -59592 / -25980 / -38336 / 48445 | 17410 / -54297 / -14562 / -38336 / 53413 | 26457 / -60539 / -23271 / -22773 / 2878 | 36657 / -122988 / -46642 / -31716 / 6936 | 41244 / -114838 / -78245 / -43268 / 7379 | 0.312 | yes | yes |
| 4-8-2-4-2 (rank 3) | 20 | 1.16 | 15873 / -59818 / -25527 / -32094 / 47837 | 18731 / -59818 / -22394 / -31230 / 49872 | 22143 / -53061 / -20339 / -21258 / 3555 | 30013 / -96219 / -49785 / -38383 / 6906 | 38078 / -104286 / -78817 / -46504 / 6410 | 0.344 | yes | yes |
| 4-4-4-4-4 (equal weights (ref)) | 20 | 1.00 | 15873 / -52366 / -40859 / -32739 / 38613 | 16860 / -52366 / -22627 / -26585 / 39296 | 20618 / -46348 / -26737 / -19054 / 3876 | 20923 / -77184 / -42246 / -36320 / 6671 | 32579 / -91844 / -64733 / -47595 / 5269 | 1.0 | yes | yes |

### Best unconstrained whole-lot vectors (any total, 0..8 per book) - RAW at their own lots

| weights (lots MF1..MF5) | total lots | k | L6M | L3M | 2023 | 2024 | 2025 | blocks | no negative year | 15% guard |
|---|---|---|---|---|---|---|---|---|---|---|
| 1-6-1-2-1 (rank 1) | 11 | 1.00 | 5165 / -19111 / -12672 / -14183 / 23329 | 6258 / -19111 / -6939 / -14183 / 25068 | 11699 / -29304 / -11018 / -11347 / 1238 | 19396 / -66369 / -20077 / -14842 / 3068 | 20457 / -65662 / -29663 / -18390 / 3055 | 0.194 | yes | yes |
| 1-5-1-2-1 (rank 2) | 10 | 1.00 | 4800 / -17307 / -11052 / -13796 / 21234 | 5726 / -17307 / -5845 / -13796 / 22616 | 10235 / -25086 / -10649 / -10208 / 1220 | 15748 / -55737 / -16974 / -13632 / 2890 | 16924 / -55066 / -25644 / -14601 / 2946 | 0.161 | yes | yes |
| 0-6-1-1-1 (rank 3) | 9 | 1.00 | 4175 / -13489 / -11117 / -12070 / 18325 | 4705 / -13489 / -8657 / -12070 / 21035 | 12584 / -30205 / -9438 / -10383 / 786 | 22452 / -70684 / -20724 / -11273 / 2363 | 24957 / -71525 / -29161 / -19828 / 1938 | 0.28 | yes | yes |

### Best unconstrained whole-lot vectors (any total, 0..8 per book) - SCALED to the reference's L6M ulcer (analytic, fractional lots) beside equal weights

| weights (lots MF1..MF5) | total lots | k | L6M | L3M | 2023 | 2024 | 2025 | blocks | no negative year | 15% guard |
|---|---|---|---|---|---|---|---|---|---|---|
| 1-6-1-2-1 (rank 1) | 11 | 3.07 | 15873 / -58727 / -38941 / -43583 / 71688 | 19229 / -58727 / -21324 / -43583 / 77033 | 35950 / -90048 / -33859 / -34870 / 3804 | 59602 / -203946 / -61695 / -45608 / 9428 | 62864 / -201774 / -91152 / -56511 / 9388 | 0.194 | yes | yes |
| 1-5-1-2-1 (rank 2) | 10 | 3.31 | 15873 / -57224 / -36545 / -45617 / 70211 | 18933 / -57224 / -19326 / -45617 / 74780 | 33842 / -82945 / -35210 / -33751 / 4033 | 52070 / -184294 / -56124 / -45074 / 9557 | 55961 / -182077 / -84791 / -48277 / 9740 | 0.161 | yes | yes |
| 0-6-1-1-1 (rank 3) | 9 | 3.80 | 15873 / -51277 / -42263 / -45884 / 69662 | 17886 / -51277 / -32910 / -45884 / 79964 | 47836 / -114822 / -35880 / -39471 / 2989 | 85352 / -268704 / -78781 / -42853 / 8982 | 94874 / -271901 / -110854 / -75376 / 7368 | 0.28 | yes | yes |
| 4-4-4-4-4 (equal weights (ref)) | 20 | 1.00 | 15873 / -52366 / -40859 / -32739 / 38613 | 16860 / -52366 / -22627 / -26585 / 39296 | 20618 / -46348 / -26737 / -19054 / 3876 | 20923 / -77184 / -42246 / -36320 / 6671 | 32579 / -91844 / -64733 / -47595 / 5269 | 1.0 | yes | yes |

### Best with total 10 lots - RAW at their own lots

| weights (lots MF1..MF5) | total lots | k | L6M | L3M | 2023 | 2024 | 2025 | blocks | no negative year | 15% guard |
|---|---|---|---|---|---|---|---|---|---|---|
| 1-5-1-2-1 (rank 1) | 10 | 1.00 | 4800 / -17307 / -11052 / -13796 / 21234 | 5726 / -17307 / -5845 / -13796 / 22616 | 10235 / -25086 / -10649 / -10208 / 1220 | 15748 / -55737 / -16974 / -13632 / 2890 | 16924 / -55066 / -25644 / -14601 / 2946 | 0.161 | yes | yes |
| 0-6-1-2-1 (rank 2) | 10 | 1.00 | 4695 / -15391 / -11117 / -15391 / 20360 | 4967 / -15391 / -7386 / -15391 / 23138 | 13855 / -34147 / -11583 / -11328 / 852 | 22273 / -71176 / -20743 / -13662 / 2562 | 24343 / -73030 / -29090 / -18657 / 2365 | 0.194 | yes | yes |
| 1-7-0-1-1 (rank 3) | 10 | 1.00 | 5411 / -20128 / -13627 / -13627 / 22387 | 6391 / -20128 / -9590 / -13490 / 24832 | 11825 / -29248 / -12072 / -10828 / 1172 | 21594 / -71210 / -21232 / -16052 / 2788 | 24750 / -72437 / -30309 / -21747 / 2258 | 0.323 | yes | yes |

### Best with total 10 lots - SCALED to the reference's L6M ulcer (analytic, fractional lots) beside equal weights

| weights (lots MF1..MF5) | total lots | k | L6M | L3M | 2023 | 2024 | 2025 | blocks | no negative year | 15% guard |
|---|---|---|---|---|---|---|---|---|---|---|
| 1-5-1-2-1 (rank 1) | 10 | 3.31 | 15873 / -57224 / -36545 / -45617 / 70211 | 18933 / -57224 / -19326 / -45617 / 74780 | 33842 / -82945 / -35210 / -33751 / 4033 | 52070 / -184294 / -56124 / -45074 / 9557 | 55961 / -182077 / -84791 / -48277 / 9740 | 0.161 | yes | yes |
| 0-6-1-2-1 (rank 2) | 10 | 3.38 | 15873 / -52039 / -37589 / -52039 / 68839 | 16794 / -52039 / -24974 / -52039 / 78233 | 46847 / -115455 / -39164 / -38300 / 2882 | 75308 / -240654 / -70134 / -46194 / 8663 | 82306 / -246920 / -98356 / -63079 / 7995 | 0.194 | yes | yes |
| 1-7-0-1-1 (rank 3) | 10 | 2.93 | 15873 / -59040 / -39970 / -39970 / 65665 | 18747 / -59040 / -28129 / -39569 / 72836 | 34684 / -85790 / -35410 / -31759 / 3437 | 63338 / -208872 / -62278 / -47082 / 8177 | 72597 / -212469 / -88900 / -63786 / 6624 | 0.323 | yes | yes |
| 4-4-4-4-4 (equal weights (ref)) | 20 | 1.00 | 15873 / -52366 / -40859 / -32739 / 38613 | 16860 / -52366 / -22627 / -26585 / 39296 | 20618 / -46348 / -26737 / -19054 / 3876 | 20923 / -77184 / -42246 / -36320 / 6671 | 32579 / -91844 / -64733 / -47595 / 5269 | 1.0 | yes | yes |

### Best with total 5 lots - RAW at their own lots

| weights (lots MF1..MF5) | total lots | k | L6M | L3M | 2023 | 2024 | 2025 | blocks | no negative year | 15% guard |
|---|---|---|---|---|---|---|---|---|---|---|
| 0-4-0-1-0 (rank 1) | 5 | 1.00 | 2454 / -8163 / -6539 / -7214 / 10642 | 2720 / -8163 / -2772 / -7214 / 12209 | 9775 / -20440 / -9096 / -5479 / 204 | 16407 / -45646 / -14272 / -6789 / 1035 | 16597 / -45375 / -15641 / -13402 / 1147 | 0.269 | yes | yes |
| 0-3-0-1-1 (rank 2) | 5 | 1.00 | 2922 / -9308 / -5690 / -9308 / 11465 | 2982 / -9308 / -5690 / -9308 / 12521 | 6734 / -16597 / -6691 / -6249 / 707 | 8865 / -32140 / -8656 / -8093 / 1555 | 12191 / -37783 / -13865 / -9453 / 1099 | 0.258 | yes | yes |
| 0-3-1-1-0 (rank 3) | 5 | 1.00 | 2337 / -7563 / -5604 / -7174 / 9168 | 2389 / -7563 / -1528 / -7174 / 10887 | 7110 / -17345 / -6302 / -5064 / 193 | 13164 / -38262 / -12812 / -5704 / 1114 | 13023 / -36049 / -15146 / -10927 / 1491 | 0.247 | yes | yes |

### Best with total 5 lots - SCALED to the reference's L6M ulcer (analytic, fractional lots) beside equal weights

| weights (lots MF1..MF5) | total lots | k | L6M | L3M | 2023 | 2024 | 2025 | blocks | no negative year | 15% guard |
|---|---|---|---|---|---|---|---|---|---|---|
| 0-4-0-1-0 (rank 1) | 5 | 6.47 | 15873 / -52803 / -42297 / -46664 / 68837 | 17596 / -52803 / -17930 / -46664 / 78976 | 63234 / -132220 / -58842 / -35443 / 1320 | 106133 / -295268 / -92320 / -43916 / 6696 | 107358 / -293517 / -101178 / -86691 / 7418 | 0.269 | yes | yes |
| 0-3-0-1-1 (rank 2) | 5 | 5.43 | 15873 / -50565 / -30909 / -50565 / 62283 | 16202 / -50565 / -30909 / -50565 / 68020 | 36585 / -90167 / -36350 / -33946 / 3839 | 48159 / -174605 / -47024 / -43969 / 8448 | 66231 / -205264 / -75325 / -51357 / 5969 | 0.258 | yes | yes |
| 0-3-1-1-0 (rank 3) | 5 | 6.79 | 15873 / -51376 / -38067 / -48733 / 62277 | 16226 / -51376 / -10381 / -48733 / 73957 | 48296 / -117825 / -42808 / -34401 / 1313 | 89421 / -259911 / -87032 / -38747 / 7569 | 88467 / -244884 / -102888 / -74225 / 10126 | 0.247 | yes | yes |
| 4-4-4-4-4 (equal weights (ref)) | 20 | 1.00 | 15873 / -52366 / -40859 / -32739 / 38613 | 16860 / -52366 / -22627 / -26585 / 39296 | 20618 / -46348 / -26737 / -19054 / 3876 | 20923 / -77184 / -42246 / -36320 / 6671 | 32579 / -91844 / -64733 / -47595 / 5269 | 1.0 | yes | yes |

### Walk-forward vs equal weights

| scope | share of 14-day blocks won | blocks scored |
|---|---|---|
| total20 | 0.2 | 80 |
| unconstrained | 0.225 | 80 |

Floor 0.58 (drawdown first).

### Exact engine verification

| vector (lots MF1..MF5) | source | L6M ulcer / max DD / worst wk / worst day / $ wk | L3M $ wk | 2023 / 2024 / 2025 $ wk | gap vs analytic (L6M $ wk, ulcer) |
|---|---|---|---|---|---|
| 3-8-2-6-1 (total20) | analytic | 13015 / -48008 / -19806 / -38986 / 39892 | 43542 | 2329 / 5408 / 5312 | |
| 3-8-2-6-1 | EXACT engine | 13015 / -48008 / -19806 / -38986 / 39892 | 43542 | 2329 / 5408 / 5312 | +0.0% $/wk, -0.0% ulcer |
| 3-8-3-5-1 (total20) | analytic | 12546 / -47104 / -20536 / -30302 / 38293 | 42220 | 2275 / 5483 / 5833 | |
| 3-8-3-5-1 | EXACT engine | 12546 / -47104 / -20536 / -30302 / 38293 | 42220 | 2275 / 5483 / 5833 | +0.0% $/wk, -0.0% ulcer |
| 4-8-2-4-2 (total20) | analytic | 13645 / -51425 / -21945 / -27591 / 41125 | 42874 | 3056 / 5937 / 5511 | |
| 4-8-2-4-2 | EXACT engine | 13645 / -51425 / -21945 / -27591 / 41125 | 42874 | 3056 / 5937 / 5511 | -0.0% $/wk, +0.0% ulcer |
| 1-6-1-2-1 (unconstrained) | analytic | 5165 / -19111 / -12672 / -14183 / 23329 | 25068 | 1238 / 3068 / 3055 | |
| 1-6-1-2-1 | EXACT engine | 5165 / -19111 / -12672 / -14183 / 23329 | 25068 | 1238 / 3068 / 3055 | +0.0% $/wk, +0.0% ulcer |

### Controls

The 30 date-shift controls are shown for the EQUAL-weight stack on the stack pages (29 of 30 beaten for the 5-book Asia stack). Controls for weighted mixes need a control set per weight vector (30 x 42 engine months each) and were NOT run: shown, not a gate.

