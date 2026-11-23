# NYAM_WEIGHTS_TL3_ALN_NY_STKd8b76ecd35 - whole-lot weight search, TRULY BARE stack TL3_ALN_NY_STKd8b76ecd35 (W-WEIGHTS, 2026-11-23 04:41Z)

**HEADLINE.** Best whole-lot vector at 20 lots total: 4-3-1-7-5 (lots MF1..MF5): raw L6M ulcer 12254 vs 19560 for equal 4-4-4-4-4 and 22236 vs 25731 $/wk; at equal L6M ulcer (analytic scaling k=1.60) 35494 vs 25731 $/wk (+38%). Unconstrained best: 3-2-1-4-2 at equal L6M ulcer 40349 $/wk (+57% vs equal weights).
**BUT NOT STABLE.** The best vectors win only 0.14-0.26 of the 14-day blocks against equal weights (floor 0.58) and the 182-day walk-forward re-pick wins 0.162/0.112 of blocks: a recent-window winner that does not repeat, so the weight edge is NOT proven; equal weights stay the build default and the pin is unchanged. Exact-engine verification: done, see the table at the bottom.

Order 2210Z (Josh: "so all the books magically have the same weight?" / "yes to both"). Books: MF1 L8cfda948.BRF90_30; MF2 Lf0346d55.BRP60; MF3 L7cc56d99; MF4 Lbb254083.BRP45; MF5 L8f11883e.BRF30_90. Research only; truly bare (R0: no StackCut / BookLock / caps / stops / sizer / zones / Trade Health), 1-lot-unit fills at the stated lots, net of engine fees.

**Method.** The bare stack runs the five books independently, so a lots vector = SUM over books of that book's daily P&L at its own lots. Per-book series come from uniform-lot bare stack runs at lots [1, 2, 3, 4, 5, 6, 7, 8] (lots 1/2/4 = the bare-fit base sets, 3/5/6/7/8 = new WU sets), split by the trade `book` column. Fills at size and no-overlap make this an approximation (trade counts drift by a few per 7,800 across lot sizes), so the top vectors are checked by EXACT engine runs below. Grid: 0..8 whole lots per book (lots [1, 2, 3, 4, 5, 6, 7, 8] available; 0 = book dropped).

**Basis (recents).** Every vector is scaled by a common fractional k to the reference's L6M ULCER (equal recent risk) and ranked on scaled L6M $/wk, drawdown first: scaled L6M max drawdown and worst week no more than 15% worse than the reference, L3M ulcer no more than 15% worse; prior years are a CHECK only (blocked only by a negative year in 2023/24/25 or persistence < 0.58). Reference = equal weights at 4 lots per book (20 lots total). Cells: ulcer / max DD / worst week / worst day / $ per week. L6M = 202605-202610, L3M = 202608-202610. Persistence = share of 14-day blocks in which the pick beats the reference (drawdown first); walk-forward = re-pick every 14 days on the trailing 182 days, score the next block against equal weights.

### Equal weights (the reference rows, raw, no scaling)

| weights (lots MF1..MF5) | total lots | k | L6M | L3M | 2023 | 2024 | 2025 | blocks | no negative year | 15% guard |
|---|---|---|---|---|---|---|---|---|---|---|
| 1-1-1-1-1 (equal 1-1-1-1-1 (5 lots)) | 5 | 1.00 | 4373 / -15007 / -14493 / -7608 / 7495 | 3540 / -9765 / -3445 / -7157 / 6747 | 11211 / -31342 / -13132 / -12462 / 2016 | 10677 / -31020 / -19393 / -10792 / 2349 | 15583 / -59504 / -30226 / -17236 / 3561 | 0.054 | yes | yes |
| 2-2-2-2-2 (equal 2-2-2-2-2 (10 lots)) | 10 | 1.00 | 9222 / -34859 / -33890 / -15819 / 14123 | 7270 / -19455 / -6945 / -14238 / 12677 | 22493 / -62813 / -26310 / -24950 / 3907 | 22637 / -65834 / -38807 / -21624 / 4539 | 31230 / -119229 / -60727 / -34541 / 6952 | 0.075 | yes | yes |
| 4-4-4-4-4 (equal weights 4-4-4-4-4 (20 lots)) | 20 | 1.00 | 19560 / -77843 / -68225 / -32003 / 25731 | 14653 / -39186 / -14470 / -28677 / 25076 | 44936 / -125977 / -52645 / -49750 / 7643 | 46867 / -133809 / -77999 / -43995 / 8327 | 63097 / -239127 / -121983 / -68998 / 13063 | 1.0 | yes | yes |

### Best whole-lot vectors with the stack total fixed at 20 lots - RAW at their own lots

| weights (lots MF1..MF5) | total lots | k | L6M | L3M | 2023 | 2024 | 2025 | blocks | no negative year | 15% guard |
|---|---|---|---|---|---|---|---|---|---|---|
| 4-3-1-7-5 (rank 1) | 20 | 1.00 | 12254 / -45459 / -32759 / -25840 / 22236 | 10528 / -42152 / -32759 / -17647 / 19685 | 68059 / -161706 / -51120 / -30790 / 4710 | 41516 / -125215 / -69214 / -42285 / 8343 | 43985 / -150111 / -78327 / -54491 / 10351 | 0.194 | yes | yes |
| 3-4-2-6-5 (rank 2) | 20 | 1.00 | 13112 / -43936 / -43936 / -31502 / 23315 | 10957 / -36606 / -27069 / -17902 / 20929 | 55709 / -150561 / -54377 / -38025 / 5344 | 38540 / -110467 / -73184 / -35875 / 9150 | 48716 / -178288 / -86702 / -55811 / 11131 | 0.183 | yes | yes |
| 4-3-1-6-6 (rank 3) | 20 | 1.00 | 12822 / -45155 / -30075 / -23230 / 22661 | 10976 / -40032 / -30075 / -17617 / 20676 | 67563 / -163325 / -49345 / -31385 / 4659 | 42116 / -126780 / -72199 / -42630 / 8334 | 44381 / -151435 / -78912 / -52279 / 10485 | 0.258 | yes | yes |

### Best whole-lot vectors with the stack total fixed at 20 lots - SCALED to the reference's L6M ulcer (analytic, fractional lots) beside equal weights

| weights (lots MF1..MF5) | total lots | k | L6M | L3M | 2023 | 2024 | 2025 | blocks | no negative year | 15% guard |
|---|---|---|---|---|---|---|---|---|---|---|
| 4-3-1-7-5 (rank 1) | 20 | 1.60 | 19560 / -72563 / -52291 / -41246 / 35494 | 16804 / -67283 / -52291 / -28168 / 31421 | 108637 / -258117 / -81599 / -49147 / 7518 | 66268 / -199869 / -110481 / -67496 / 13317 | 70209 / -239609 / -125026 / -86979 / 16522 | 0.194 | yes | yes |
| 3-4-2-6-5 (rank 2) | 20 | 1.49 | 19560 / -65542 / -65542 / -46994 / 34780 | 16345 / -54608 / -40380 / -26705 / 31222 | 83106 / -224604 / -81118 / -56724 / 7972 | 57492 / -164793 / -109174 / -53517 / 13649 | 72673 / -265967 / -129340 / -83257 / 16606 | 0.183 | yes | yes |
| 4-3-1-6-6 (rank 3) | 20 | 1.53 | 19560 / -68885 / -45879 / -35437 / 34569 | 16744 / -61069 / -45879 / -26875 / 31541 | 103067 / -249154 / -75277 / -47878 / 7107 | 64248 / -193403 / -110140 / -65033 / 12713 | 67704 / -231016 / -120381 / -79752 / 15995 | 0.258 | yes | yes |
| 4-4-4-4-4 (equal weights (ref)) | 20 | 1.00 | 19560 / -77843 / -68225 / -32003 / 25731 | 14653 / -39186 / -14470 / -28677 / 25076 | 44936 / -125977 / -52645 / -49750 / 7643 | 46867 / -133809 / -77999 / -43995 / 8327 | 63097 / -239127 / -121983 / -68998 / 13063 | 1.0 | yes | yes |

### Best unconstrained whole-lot vectors (any total, 0..8 per book) - RAW at their own lots

| weights (lots MF1..MF5) | total lots | k | L6M | L3M | 2023 | 2024 | 2025 | blocks | no negative year | 15% guard |
|---|---|---|---|---|---|---|---|---|---|---|
| 3-2-1-4-2 (rank 1) | 12 | 1.00 | 7727 / -25513 / -19146 / -15143 / 15940 | 6532 / -24501 / -19146 / -12530 / 12651 | 35403 / -88206 / -32541 / -22304 / 3597 | 26321 / -80685 / -41470 / -22197 / 5280 | 30258 / -102933 / -56184 / -37611 / 6926 | 0.14 | yes | yes |
| 3-2-1-4-1 (rank 2) | 11 | 1.00 | 7282 / -23937 / -19182 / -14533 / 14991 | 6217 / -23937 / -19182 / -12530 / 11417 | 33249 / -83580 / -31847 / -21824 / 3486 | 24976 / -76684 / -36897 / -22197 / 4842 | 30420 / -100537 / -53940 / -37611 / 6405 | 0.14 | yes | yes |
| 2-1-1-3-2 (rank 3) | 9 | 1.00 | 5778 / -18053 / -17313 / -10310 / 11890 | 4610 / -13760 / -10669 / -9434 / 10160 | 22576 / -61419 / -21026 / -15086 / 2847 | 18652 / -58251 / -31049 / -15798 / 3863 | 20675 / -74872 / -44249 / -28498 / 5239 | 0.237 | yes | yes |

### Best unconstrained whole-lot vectors (any total, 0..8 per book) - SCALED to the reference's L6M ulcer (analytic, fractional lots) beside equal weights

| weights (lots MF1..MF5) | total lots | k | L6M | L3M | 2023 | 2024 | 2025 | blocks | no negative year | 15% guard |
|---|---|---|---|---|---|---|---|---|---|---|
| 3-2-1-4-2 (rank 1) | 12 | 2.53 | 19560 / -64580 / -48464 / -38331 / 40349 | 16535 / -62019 / -48464 / -31716 / 32023 | 89615 / -223274 / -82370 / -56457 / 9106 | 66626 / -204236 / -104972 / -56186 / 13364 | 76590 / -260553 / -142217 / -95204 / 17532 | 0.14 | yes | yes |
| 3-2-1-4-1 (rank 2) | 11 | 2.69 | 19560 / -64295 / -51523 / -39037 / 40268 | 16700 / -64295 / -51523 / -33655 / 30666 | 89309 / -224499 / -85542 / -58620 / 9363 | 67087 / -205978 / -99106 / -59622 / 13006 | 81709 / -270047 / -144885 / -101024 / 17205 | 0.14 | yes | yes |
| 2-1-1-3-2 (rank 3) | 9 | 3.39 | 19560 / -61110 / -58605 / -34901 / 40249 | 15606 / -46580 / -36115 / -31935 / 34394 | 76419 / -207904 / -71175 / -51065 / 9638 | 63138 / -197181 / -105101 / -53477 / 13077 | 69985 / -253445 / -149785 / -96467 / 17736 | 0.237 | yes | yes |
| 4-4-4-4-4 (equal weights (ref)) | 20 | 1.00 | 19560 / -77843 / -68225 / -32003 / 25731 | 14653 / -39186 / -14470 / -28677 / 25076 | 44936 / -125977 / -52645 / -49750 / 7643 | 46867 / -133809 / -77999 / -43995 / 8327 | 63097 / -239127 / -121983 / -68998 / 13063 | 1.0 | yes | yes |

### Best with total 10 lots - RAW at their own lots

| weights (lots MF1..MF5) | total lots | k | L6M | L3M | 2023 | 2024 | 2025 | blocks | no negative year | 15% guard |
|---|---|---|---|---|---|---|---|---|---|---|
| 2-1-1-4-2 (rank 1) | 10 | 1.00 | 6008 / -20651 / -19582 / -12560 / 12281 | 4772 / -16489 / -13398 / -9256 / 10481 | 25622 / -70916 / -23565 / -16716 / 3057 | 19956 / -61931 / -32713 / -16663 / 4317 | 21430 / -75662 / -46053 / -30327 / 5549 | 0.215 | yes | yes |
| 3-2-1-3-1 (rank 2) | 10 | 1.00 | 7180 / -21951 / -16453 / -14533 / 14601 | 6097 / -21208 / -16453 / -12465 / 11096 | 30727 / -74618 / -29308 / -21939 / 3276 | 24282 / -73552 / -35233 / -21332 / 4389 | 30676 / -100851 / -52136 / -34972 / 6095 | 0.151 | yes | yes |
| 2-1-1-3-3 (rank 3) | 10 | 1.00 | 6385 / -20357 / -16387 / -10609 / 12846 | 5265 / -14340 / -10648 / -10609 / 11439 | 25266 / -66752 / -21725 / -16696 / 2957 | 20313 / -62351 / -35647 / -16640 / 4285 | 21319 / -78510 / -46538 / -30232 / 5743 | 0.226 | yes | yes |

### Best with total 10 lots - SCALED to the reference's L6M ulcer (analytic, fractional lots) beside equal weights

| weights (lots MF1..MF5) | total lots | k | L6M | L3M | 2023 | 2024 | 2025 | blocks | no negative year | 15% guard |
|---|---|---|---|---|---|---|---|---|---|---|
| 2-1-1-4-2 (rank 1) | 10 | 3.26 | 19560 / -67229 / -63748 / -40888 / 39980 | 15535 / -53681 / -43617 / -30135 / 34122 | 83413 / -230870 / -76717 / -54420 / 9951 | 64968 / -201617 / -106497 / -54246 / 14053 | 69766 / -246319 / -149926 / -98731 / 18066 | 0.215 | yes | yes |
| 3-2-1-3-1 (rank 2) | 10 | 2.72 | 19560 / -59801 / -44823 / -39593 / 39777 | 16611 / -57776 / -44823 / -33958 / 30229 | 83709 / -203281 / -79843 / -59769 / 8925 | 66151 / -200376 / -95984 / -58115 / 11956 | 83571 / -274747 / -142034 / -95274 / 16606 | 0.151 | yes | yes |
| 2-1-1-3-3 (rank 3) | 10 | 3.06 | 19560 / -62358 / -50197 / -32498 / 39352 | 16127 / -43926 / -32619 / -32498 / 35042 | 77397 / -204481 / -66551 / -51145 / 9057 | 62224 / -190998 / -109197 / -50974 / 13128 | 65305 / -240497 / -142558 / -92610 / 17593 | 0.226 | yes | yes |
| 4-4-4-4-4 (equal weights (ref)) | 20 | 1.00 | 19560 / -77843 / -68225 / -32003 / 25731 | 14653 / -39186 / -14470 / -28677 / 25076 | 44936 / -125977 / -52645 / -49750 / 7643 | 46867 / -133809 / -77999 / -43995 / 8327 | 63097 / -239127 / -121983 / -68998 / 13063 | 1.0 | yes | yes |

### Best with total 5 lots - RAW at their own lots

| weights (lots MF1..MF5) | total lots | k | L6M | L3M | 2023 | 2024 | 2025 | blocks | no negative year | 15% guard |
|---|---|---|---|---|---|---|---|---|---|---|
| 2-1-1-1-0 (rank 1) | 5 | 1.00 | 5108 / -17705 / -14128 / -10328 / 8571 | 4143 / -12022 / -5488 / -8881 / 6862 | 14313 / -34838 / -14601 / -14377 / 2274 | 17078 / -50115 / -18639 / -14078 / 2089 | 21124 / -71022 / -36254 / -21445 / 3606 | 0.28 | yes | yes |
| 3-1-0-1-0 (rank 2) | 5 | 1.00 | 5797 / -23777 / -12341 / -11118 / 9024 | 4913 / -15807 / -12341 / -10331 / 6154 | 29760 / -74084 / -15774 / -11977 / 1617 | 24529 / -66539 / -21957 / -23994 / 1967 | 28722 / -74101 / -30743 / -25934 / 3065 | 0.333 | yes | yes |
| 1-1-1-2-0 (rank 3) | 5 | 1.00 | 4631 / -20542 / -18017 / -10152 / 7136 | 3550 / -9265 / -6105 / -7138 / 5700 | 13564 / -38751 / -14957 / -11872 / 2083 | 11491 / -33250 / -17061 / -11468 / 2407 | 15235 / -56610 / -29786 / -18785 / 3432 | 0.462 | yes | yes |

### Best with total 5 lots - SCALED to the reference's L6M ulcer (analytic, fractional lots) beside equal weights

| weights (lots MF1..MF5) | total lots | k | L6M | L3M | 2023 | 2024 | 2025 | blocks | no negative year | 15% guard |
|---|---|---|---|---|---|---|---|---|---|---|
| 2-1-1-1-0 (rank 1) | 5 | 3.83 | 19560 / -67795 / -54100 / -39549 / 32821 | 15864 / -46036 / -21013 / -34007 / 26275 | 54806 / -133403 / -55909 / -55053 / 8708 | 65397 / -191901 / -71373 / -53909 / 8001 | 80888 / -271959 / -138825 / -82118 / 13807 | 0.28 | yes | yes |
| 3-1-0-1-0 (rank 2) | 5 | 3.37 | 19560 / -80226 / -41639 / -37512 / 30450 | 16576 / -53334 / -41639 / -34860 / 20766 | 100413 / -249966 / -53222 / -40411 / 5455 | 82762 / -224511 / -74086 / -80960 / 6637 | 96911 / -250024 / -103729 / -87503 / 10342 | 0.333 | yes | yes |
| 1-1-1-2-0 (rank 3) | 5 | 4.22 | 19560 / -86762 / -76099 / -42881 / 30142 | 14994 / -39132 / -25784 / -30150 / 24074 | 57291 / -163671 / -63175 / -50145 / 8800 | 48535 / -140438 / -72061 / -48439 / 10166 | 64346 / -239100 / -125805 / -79343 / 14495 | 0.462 | yes | yes |
| 4-4-4-4-4 (equal weights (ref)) | 20 | 1.00 | 19560 / -77843 / -68225 / -32003 / 25731 | 14653 / -39186 / -14470 / -28677 / 25076 | 44936 / -125977 / -52645 / -49750 / 7643 | 46867 / -133809 / -77999 / -43995 / 8327 | 63097 / -239127 / -121983 / -68998 / 13063 | 1.0 | yes | yes |

### Walk-forward vs equal weights

| scope | share of 14-day blocks won | blocks scored |
|---|---|---|
| total20 | 0.162 | 80 |
| unconstrained | 0.112 | 80 |

Floor 0.58 (drawdown first).

### Exact engine verification

| vector (lots MF1..MF5) | source | L6M ulcer / max DD / worst wk / worst day / $ wk | L3M $ wk | 2023 / 2024 / 2025 $ wk | gap vs analytic (L6M $ wk, ulcer) |
|---|---|---|---|---|---|
| 4-3-1-7-5 (total20) | analytic | 12254 / -45459 / -32759 / -25840 / 22236 | 19685 | 4710 / 8343 / 10351 | |
| 4-3-1-7-5 | EXACT engine | 12254 / -45459 / -32759 / -25840 / 22236 | 19685 | 4710 / 8343 / 10351 | +0.0% $/wk, +0.0% ulcer |
| 3-4-2-6-5 (total20) | analytic | 13112 / -43936 / -43936 / -31502 / 23315 | 20929 | 5344 / 9150 / 11131 | |
| 3-4-2-6-5 | EXACT engine | 13112 / -43936 / -43936 / -31502 / 23315 | 20929 | 5344 / 9150 / 11131 | +0.0% $/wk, -0.0% ulcer |
| 4-3-1-6-6 (total20) | analytic | 12822 / -45155 / -30075 / -23230 / 22661 | 20676 | 4659 / 8334 / 10485 | |
| 4-3-1-6-6 | EXACT engine | 12822 / -45155 / -30075 / -23230 / 22661 | 20676 | 4659 / 8334 / 10485 | +0.0% $/wk, -0.0% ulcer |
| 3-2-1-4-2 (unconstrained) | analytic | 7727 / -25513 / -19146 / -15143 / 15940 | 12651 | 3597 / 5280 / 6926 | |
| 3-2-1-4-2 | EXACT engine | 7727 / -25513 / -19146 / -15143 / 15940 | 12651 | 3597 / 5280 / 6926 | +0.0% $/wk, -0.0% ulcer |

### Controls

The 30 date-shift controls are shown for the EQUAL-weight stack on the stack pages (29 of 30 beaten for the 5-book Asia stack). Controls for weighted mixes need a control set per weight vector (30 x 42 engine months each) and were NOT run: shown, not a gate.

