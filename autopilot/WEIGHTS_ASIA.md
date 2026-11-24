# WEIGHTS_ASIA - weight search on book-alone sums (W-LAYERS, 2026-11-24 00:19Z)

Prereg: autopilot/WEIGHTS_PREREG.md (sha in DECISIONS.md). A mix is the SUM of weight x book-alone daily P&L (42 months, 1 lot); no stack interaction; engine check pending.
Run 2026-11-24 00:19Z; pool hash (asia pool file) 702689600825; dynamic scopes (loop finals): FINAL_asia_own_d8_nol3+asia_own_d8_nol3_recent_w, FINAL_asia_own_d8_nol3_w, FINAL_asia_stay_d8_nol3_recent_w_stayclause_1700+asia_stay_d8_nol3_w.

### Scope A - members J502 (7 mixes; weight grid [0, 0.25, 0.5, 1, 1.5, 2, 3, 4]; SUM of book-alone series, no stack interaction)

Equal-weight reference: worst prior-year max DD -11407. Cells `ulcer / max DD / worst week / $/wk` at 1 lot x scale k; every mix scaled to the reference's worst-prior-year max DD (k shown).

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| equal weights | 1 | 1.00 | 495 / -1915 / -1600 / 2157 | 519 / -1915 / -219 / 2514 | 2321 / -4696 / -2024 / 40 | 4258 / -11407 / -3539 / 217 | 4370 / -10172 / -3904 / 179 | - |

Same ranking at equal L6M ulcer (every mix scaled to the reference's L6M ulcer):

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|

BEST MIX AMONG THOSE WITH BLOCK PERSISTENCE >= 0.58: NONE passes (0 mixes pass the L6M guard and the 0.58 persistence together).

No distinct mix: with 1 member(s) every weight vector in the grid is the reference direction (or has no other direction passing the L6M guard): the only choice is a common SCALE, and at equal worst-prior-year max drawdown the scale is fixed by the basis (k = 1 for the reference itself). Sizing A to its worst prior year = its own 2024 max DD -11407.

GATES for the top mix (equal-risk ranking): walk-forward persistence 1.0 over 62 periods (equal weights was the pick in 18; gate >= 0.58); prior-year band ; null: PENDING (needs random-entry book series, ~2,000 sm); 27/30: not computed (shown only).

### Scope B - members L7c368a4f, La010c3eb (63 mixes; weight grid [0, 0.25, 0.5, 1, 1.5, 2, 3, 4]; SUM of book-alone series, no stack interaction)

Equal-weight reference: worst prior-year max DD -31090. Cells `ulcer / max DD / worst week / $/wk` at 1 lot x scale k; every mix scaled to the reference's worst-prior-year max DD (k shown).

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| equal weights | 1/1 | 1.00 | 4667 / -13774 / -11356 / 3318 | 3629 / -10667 / -3716 / 3339 | 2720 / -7215 / -2853 / 662 | 9489 / -25656 / -7527 / 1050 | 14402 / -31090 / -11666 / 604 | - |
| top 1 | 3/2 | 0.42 | 4824 / -14375 / -12659 / 3821 | 3800 / -10549 / -3704 / 3830 | 3291 / -7943 / -3123 / 642 | 9682 / -26115 / -7188 / 1157 | 14409 / -31090 / -14052 / 729 | 0.194 |
| top 2 | 2/1.5 | 0.59 | 4760 / -14256 / -12324 / 3687 | 3760 / -10628 / -3723 / 3700 | 3085 / -7729 / -2943 / 650 | 9660 / -26086 / -7318 / 1130 | 14460 / -31090 / -13401 / 695 | 0.194 |
| top 3 | 1.5/2 | 0.55 | 4698 / -14120 / -10459 / 2975 | 3535 / -10704 / -3709 / 3006 | 2441 / -6739 / -3125 / 672 | 9350 / -25392 / -7720 / 975 | 14386 / -31090 / -10759 / 519 | 0.753 |
| top 4 | 2/3 | 0.38 | 4731 / -14619 / -10119 / 2846 | 3506 / -10718 / -3706 / 2879 | 2344 / -6558 / -3229 / 676 | 9302 / -25364 / -7794 / 947 | 14391 / -31090 / -10679 / 487 | 0.753 |
| top 5 | 0.5/1 | 1.22 | 4854 / -15729 / -9362 / 2557 | 3496 / -10749 / -3701 / 2597 | 2220 / -6399 / -3458 / 685 | 9203 / -25302 / -7957 / 884 | 14415 / -31090 / -10501 / 416 | 0.731 |

Same ranking at equal L6M ulcer (every mix scaled to the reference's L6M ulcer):

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| top 1 | 1/0.5 | 1.31 | 4667 / -13369 / -12280 / 3778 | 3569 / -9445 / -3336 / 3778 | 3585 / -9018 / -3244 / 566 | 8890 / -23874 / -6266 / 1115 | 13043 / -28724 / -14245 / 741 | 0.376 |
| top 2 | 4/1.5 | 0.34 | 4667 / -13273 / -12008 / 3754 | 3410 / -8875 / -3243 / 3746 | 3980 / -10355 / -3350 / 507 | 8293 / -22137 / -5542 / 1084 | 11998 / -26899 / -14439 / 752 | 0.419 |
| top 3 | 1.5/0.5 | 0.90 | 4667 / -13532 / -11843 / 3724 | 3340 / -8699 / -3442 / 3713 | 4106 / -10755 / -3367 / 483 | 8042 / -21405 / -5259 / 1067 | 11569 / -26108 / -14420 / 751 | 0.441 |
| top 4 | 3/2 | 0.41 | 4667 / -13907 / -12247 / 3697 | 3677 / -10206 / -3583 / 3705 | 3184 / -7685 / -3021 / 621 | 9367 / -25265 / -6954 / 1120 | 13940 / -30078 / -13594 / 706 | 0.28 |
| top 5 | 2/1.5 | 0.58 | 4667 / -13976 / -12083 / 3615 | 3686 / -10419 / -3650 / 3627 | 3024 / -7578 / -2885 / 637 | 9471 / -25575 / -7175 / 1108 | 14176 / -30481 / -13138 / 681 | 0.247 |

BEST MIX AMONG THOSE WITH BLOCK PERSISTENCE >= 0.58 (9 mixes pass the guard and 0.58): 

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| best passing | 1.5/2 | 0.55 | 4698 / -14120 / -10459 / 2975 | 3535 / -10704 / -3709 / 3006 | 2441 / -6739 / -3125 / 672 | 9350 / -25392 / -7720 / 975 | 14386 / -31090 / -10759 / 519 | 0.753 |

GATES for the top mix (equal-risk ranking): walk-forward persistence 0.288 over 73 periods (equal weights was the pick in 7; gate >= 0.58); prior-year band 2023 AMBER (+20%), 2024 GREEN (-8%), 2025 GREEN (-21%); null: PENDING (needs random-entry book series, ~2,000 sm); 27/30: not computed (shown only).

### Scope C - members L7c368a4f, L578701ed, J502 (511 mixes; weight grid [0, 0.25, 0.5, 1, 1.5, 2, 3, 4]; SUM of book-alone series, no stack interaction)

Equal-weight reference: worst prior-year max DD -24258. Cells `ulcer / max DD / worst week / $/wk` at 1 lot x scale k; every mix scaled to the reference's worst-prior-year max DD (k shown).

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| equal weights | 1/1/1 | 1.00 | 3689 / -10998 / -5733 / 6821 | 4268 / -10998 / -5377 / 5562 | 2923 / -8559 / -3717 / 996 | 8370 / -23827 / -5706 / 911 | 8169 / -24258 / -19114 / 1238 | - |
| top 1 | 1.5/2/4 | 0.47 | 2998 / -9330 / -3562 / 7867 | 3799 / -9330 / -3562 / 7024 | 3481 / -10289 / -3468 / 927 | 7880 / -24258 / -5841 / 907 | 9104 / -23744 / -19276 / 1209 | 0.473 |
| top 2 | 1/1.5/3 | 0.64 | 2993 / -9389 / -3760 / 7852 | 3844 / -9389 / -3760 / 6991 | 3430 / -10117 / -3349 / 932 | 7855 / -24258 / -5748 / 876 | 9173 / -24005 / -18910 / 1195 | 0.484 |
| top 3 | 1.5/1.5/3 | 0.58 | 2999 / -8996 / -3272 / 7761 | 3639 / -8996 / -3203 / 6981 | 3568 / -10730 / -3723 / 896 | 7997 / -24258 / -5982 / 975 | 8953 / -23635 / -19896 / 1225 | 0.484 |
| top 4 | 1/2/3 | 0.57 | 3435 / -11092 / -4796 / 7607 | 4509 / -11092 / -4796 / 6388 | 2994 / -8669 / -3161 / 1043 | 7863 / -24258 / -5495 / 790 | 9152 / -24171 / -18262 / 1213 | 0.473 |
| top 5 | 1.5/2/3 | 0.52 | 3354 / -10621 / -3997 / 7575 | 4216 / -10621 / -3997 / 6457 | 3141 / -9274 / -3527 / 1004 | 8074 / -23910 / -5750 / 890 | 8781 / -24258 / -19276 / 1243 | 0.452 |

Same ranking at equal L6M ulcer (every mix scaled to the reference's L6M ulcer):

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| top 1 | 0.5/0.25/2 | 2.41 | 3689 / -12490 / -5010 / 14688 | 3995 / -12332 / -774 / 15422 | 10376 / -25323 / -10725 / 890 | 20826 / -62026 / -15828 / 1858 | 19541 / -56684 / -34068 / 1821 | 0.172 |
| top 2 | 1/0.25/4 | 1.24 | 3689 / -12207 / -5682 / 14482 | 3543 / -11487 / 788 / 15736 | 11411 / -26514 / -12122 / 685 | 22582 / -64760 / -17178 / 1907 | 20523 / -60251 / -33595 / 1716 | 0.172 |
| top 3 | 0.5/0.25/1.5 | 2.65 | 3689 / -12223 / -3390 / 13292 | 3984 / -11103 / -1004 / 13626 | 8746 / -22585 / -9111 / 926 | 17464 / -53090 / -12715 / 1756 | 17088 / -48967 / -32288 / 1765 | 0.151 |
| top 4 | 0.25/0/1 | 4.79 | 3689 / -11703 / -5961 / 13286 | 3045 / -10250 / 2288 / 14971 | 12208 / -26817 / -12681 / 434 | 22869 / -63045 / -17344 / 1824 | 20411 / -59674 / -30825 / 1494 | 0.194 |
| top 5 | 1/0.25/3 | 1.39 | 3689 / -12082 / -4134 / 13212 | 3455 / -10764 / 722 / 14118 | 9902 / -24345 / -10754 / 711 | 19469 / -56627 / -14305 / 1833 | 18114 / -53420 / -32182 / 1671 | 0.172 |

BEST MIX AMONG THOSE WITH BLOCK PERSISTENCE >= 0.58 (114 mixes pass the guard and 0.58): 

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| best passing | 0.25/0.5/1 | 1.90 | 2838 / -8972 / -3946 / 7372 | 3732 / -8972 / -3946 / 6525 | 3143 / -9191 / -2918 / 889 | 7370 / -22874 / -5231 / 762 | 8820 / -24258 / -17091 / 1097 | 0.602 |

GATES for the top mix (equal-risk ranking): walk-forward persistence 0.263 over 80 periods (equal weights was the pick in 0; gate >= 0.58); prior-year band 2023 AMBER (+22%), 2024 GREEN (-6%), 2025 GREEN (+12%); null: PENDING (needs random-entry book series, ~2,000 sm); 27/30: not computed (shown only).

### Scope UNION - members J502, L7c368a4f, La010c3eb, L578701ed (4095 mixes; weight grid [0, 0.25, 0.5, 1, 1.5, 2, 3, 4]; SUM of book-alone series, no stack interaction)

Equal-weight reference: worst prior-year max DD -37944. Cells `ulcer / max DD / worst week / $/wk` at 1 lot x scale k; every mix scaled to the reference's worst-prior-year max DD (k shown).

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| equal weights | 1/1/1/1 | 1.00 | 4293 / -13827 / -9679 / 7682 | 4581 / -11472 / -4961 / 6468 | 2733 / -8332 / -3642 / 1455 | 11598 / -34209 / -7459 / 1307 | 13842 / -37944 / -20678 / 1314 | - |
| top 1 | 4/2/0/1.5 | 0.68 | 4002 / -12044 / -5021 / 11379 | 4644 / -12044 / -3846 / 10699 | 5879 / -17288 / -5597 / 1145 | 12170 / -37944 / -8887 / 1510 | 13604 / -37364 / -29360 / 1735 | 0.301 |
| top 2 | 3/1.5/0.25/1.5 | 0.83 | 4317 / -12830 / -5527 / 11346 | 5152 / -12830 / -4329 / 10233 | 4942 / -15393 / -5001 / 1384 | 12156 / -37533 / -8967 / 1485 | 13888 / -37944 / -28955 / 1779 | 0.333 |
| top 3 | 4/1.5/0/1.5 | 0.72 | 3792 / -11187 / -3615 / 11248 | 4632 / -11187 / -3615 / 10531 | 5643 / -16178 / -5075 / 1147 | 11951 / -37944 / -8452 / 1374 | 13176 / -35934 / -27667 / 1660 | 0.366 |
| top 4 | 0.5/0.5/0/0.25 | 3.91 | 5249 / -15628 / -10942 / 11176 | 5117 / -14530 / -7157 / 10272 | 5927 / -18253 / -6632 / 1211 | 13217 / -37944 / -9543 / 1742 | 14420 / -37463 / -32371 / 1902 | 0.204 |
| top 5 | 4/3/0.25/2 | 0.54 | 4616 / -13609 / -8622 / 11138 | 5022 / -13609 / -5517 / 10158 | 5345 / -16756 / -5758 / 1290 | 12707 / -37825 / -9242 / 1625 | 14018 / -37944 / -30524 / 1826 | 0.258 |

Same ranking at equal L6M ulcer (every mix scaled to the reference's L6M ulcer):

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| top 1 | 4/0.5/0/0 | 1.82 | 4293 / -14491 / -10374 / 17984 | 4075 / -14491 / 1343 / 20570 | 17516 / -35499 / -17038 / 475 | 32879 / -89609 / -26116 / 2181 | 30374 / -82217 / -37708 / 1792 | 0.237 |
| top 2 | 3/0.5/0/0 | 2.23 | 4293 / -13426 / -9101 / 17149 | 3886 / -13426 / 2127 / 19510 | 16287 / -33996 / -16291 / 491 | 30682 / -83982 / -23998 / 2178 | 27817 / -77904 / -37336 / 1787 | 0.247 |
| top 3 | 2/0.5/0/0.25 | 2.80 | 4293 / -14534 / -5830 / 17091 | 4649 / -14350 / -901 / 17945 | 12075 / -29468 / -12480 / 1036 | 24235 / -72177 / -18418 / 2162 | 22739 / -65960 / -39644 / 2119 | 0.194 |
| top 4 | 4/0.5/0.25/0 | 1.69 | 4293 / -14245 / -10116 / 17014 | 4130 / -14245 / -299 / 19427 | 14984 / -32117 / -15770 / 633 | 31825 / -87808 / -25302 / 2186 | 29891 / -82918 / -35572 / 1691 | 0.237 |
| top 5 | 4/1/0/0.25 | 1.45 | 4293 / -14205 / -6612 / 16852 | 4123 / -13367 / 917 / 18311 | 13278 / -30853 / -14105 / 797 | 26277 / -75358 / -19989 / 2219 | 23882 / -70111 / -39093 / 1997 | 0.194 |

BEST MIX AMONG THOSE WITH BLOCK PERSISTENCE >= 0.58 (937 mixes pass the guard and 0.58): 

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| best passing | 4/0/0.25/1 | 0.82 | 2489 / -8842 / -4161 / 9069 | 3253 / -8842 / -3877 / 8943 | 4869 / -12377 / -3884 / 843 | 11800 / -37944 / -9971 / 826 | 14157 / -37293 / -17327 / 1040 | 0.581 |

GATES for the top mix (equal-risk ranking): walk-forward persistence 0.175 over 80 periods (equal weights was the pick in 0; gate >= 0.58); prior-year band 2023 RED (+63%), 2024 GREEN (-10%), 2025 GREEN (-34%); null: PENDING (needs random-entry book series, ~2,000 sm); 27/30: not computed (shown only).

### Scope FINAL_asia_own_d8_nol3+asia_own_d8_nol3_recent_w - members L385f4f2e (7 mixes; weight grid [0, 0.25, 0.5, 1, 1.5, 2, 3, 4]; SUM of book-alone series, no stack interaction)

Equal-weight reference: worst prior-year max DD -11407. Cells `ulcer / max DD / worst week / $/wk` at 1 lot x scale k; every mix scaled to the reference's worst-prior-year max DD (k shown).

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| equal weights | 1 | 1.00 | 495 / -1915 / -1600 / 2157 | 519 / -1915 / -219 / 2514 | 2321 / -4696 / -2024 / 40 | 4258 / -11407 / -3539 / 217 | 4370 / -10172 / -3904 / 179 | - |

Same ranking at equal L6M ulcer (every mix scaled to the reference's L6M ulcer):

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|

BEST MIX AMONG THOSE WITH BLOCK PERSISTENCE >= 0.58: NONE passes (0 mixes pass the L6M guard and the 0.58 persistence together).

No distinct mix: with 1 member(s) every weight vector in the grid is the reference direction (or has no other direction passing the L6M guard): the only choice is a common SCALE, and at equal worst-prior-year max drawdown the scale is fixed by the basis (k = 1 for the reference itself). Sizing A to its worst prior year = its own 2024 max DD -11407.

GATES for the top mix (equal-risk ranking): walk-forward persistence 1.0 over 62 periods (equal weights was the pick in 18; gate >= 0.58); prior-year band ; null: PENDING (needs random-entry book series, ~2,000 sm); 27/30: not computed (shown only).

### Scope FINAL_asia_own_d8_nol3_w - members Lb0e6dfa3, L385f4f2e, L9c2622b0, L4aaacdb2 (4095 mixes; weight grid [0, 0.25, 0.5, 1, 1.5, 2, 3, 4]; SUM of book-alone series, no stack interaction)

Equal-weight reference: worst prior-year max DD -15575. Cells `ulcer / max DD / worst week / $/wk` at 1 lot x scale k; every mix scaled to the reference's worst-prior-year max DD (k shown).

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| equal weights | 1/1/1/1 | 1.00 | 2618 / -8577 / -5079 / 7503 | 2874 / -8526 / 1248 / 6341 | 2825 / -6313 / -3586 / 931 | 5723 / -15575 / -7296 / 1234 | 5950 / -14678 / -9221 / 1441 | - |
| top 1 | 1.5/1.5/1/1 | 0.82 | 2755 / -9636 / -5463 / 8262 | 3163 / -9636 / 652 / 7028 | 2970 / -7862 / -3694 / 939 | 5810 / -15575 / -7167 / 1310 | 6235 / -15000 / -9294 / 1539 | 0.366 |
| top 2 | 2/2/1/1.5 | 0.64 | 2683 / -9393 / -5460 / 8261 | 3074 / -9393 / 884 / 7030 | 2924 / -7417 / -3520 / 934 | 5688 / -15413 / -6548 / 1276 | 5969 / -15575 / -8781 / 1527 | 0.398 |
| top 3 | 0.5/0.5/0.25/0.5 | 2.51 | 2653 / -9015 / -5529 / 8257 | 2958 / -9015 / 1360 / 7001 | 2964 / -7492 / -3497 / 979 | 5796 / -15268 / -6412 / 1272 | 5843 / -15575 / -8689 / 1541 | 0.398 |
| top 4 | 3/3/1.5/2 | 0.43 | 2689 / -9499 / -5423 / 8242 | 3108 / -9499 / 665 / 7021 | 2907 / -7754 / -3519 / 917 | 5650 / -15575 / -6578 / 1275 | 6007 / -15536 / -8790 / 1518 | 0.43 |
| top 5 | 3/3/1.5/4 | 0.41 | 2634 / -9537 / -5609 / 8240 | 2822 / -8522 / 1317 / 6955 | 3036 / -8038 / -3463 / 1035 | 5996 / -15575 / -6231 / 1264 | 5724 / -15553 / -8800 / 1558 | 0.366 |

Same ranking at equal L6M ulcer (every mix scaled to the reference's L6M ulcer):

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| top 1 | 2/3/0.5/0.25 | 0.67 | 2618 / -9810 / -5838 / 9010 | 3197 / -9810 / 503 / 8202 | 3210 / -10143 / -4363 / 731 | 6391 / -18814 / -8563 / 1272 | 6797 / -17479 / -10097 / 1451 | 0.441 |
| top 2 | 3/4/0.5/1.5 | 0.46 | 2618 / -9421 / -5833 / 8911 | 3136 / -9421 / 1073 / 7946 | 3077 / -8538 / -3955 / 821 | 6165 / -17344 / -8604 / 1255 | 6324 / -16717 / -9222 / 1491 | 0.43 |
| top 3 | 3/4/1/1 | 0.44 | 2618 / -9774 / -5772 / 8850 | 3164 / -9774 / 641 / 7886 | 3079 / -9310 / -4119 / 809 | 6115 / -17703 / -7959 / 1288 | 6514 / -15978 / -9753 / 1493 | 0.419 |
| top 4 | 2/3/1.5/0.5 | 0.57 | 2618 / -9831 / -5839 / 8828 | 3144 / -9831 / 771 / 7931 | 3165 / -9503 / -4663 / 825 | 7148 / -21816 / -9152 / 1349 | 7195 / -17353 / -11137 / 1503 | 0.355 |
| top 5 | 2/3/0.5/0 | 0.66 | 2618 / -9791 / -5674 / 8816 | 3208 / -9791 / 154 / 8044 | 3189 / -10490 / -4285 / 688 | 6404 / -18726 / -8462 / 1246 | 6790 / -17650 / -9931 / 1409 | 0.452 |

BEST MIX AMONG THOSE WITH BLOCK PERSISTENCE >= 0.58 (2453 mixes pass the guard and 0.58): 

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| best passing | 3/4/1/1.5 | 0.38 | 2244 / -8296 / -5076 / 7714 | 2689 / -8296 / 948 / 6855 | 2648 / -7469 / -3573 / 735 | 5359 / -15575 / -6846 / 1121 | 5543 / -13941 / -8444 / 1312 | 0.602 |

GATES for the top mix (equal-risk ranking): walk-forward persistence 0.175 over 80 periods (equal weights was the pick in 0; gate >= 0.58); prior-year band 2023 GREEN (+4%), 2024 GREEN (-4%), 2025 GREEN (-2%); null: PENDING (needs random-entry book series, ~2,000 sm); 27/30: not computed (shown only).

### Scope FINAL_asia_stay_d8_nol3_recent_w_stayclause_1700+asia_stay_d8_nol3_w - members Lb0e6dfa3 (7 mixes; weight grid [0, 0.25, 0.5, 1, 1.5, 2, 3, 4]; SUM of book-alone series, no stack interaction)

Equal-weight reference: worst prior-year max DD -12361. Cells `ulcer / max DD / worst week / $/wk` at 1 lot x scale k; every mix scaled to the reference's worst-prior-year max DD (k shown).

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| equal weights | 1 | 1.00 | 2647 / -8614 / -4590 / 2969 | 3041 / -8614 / -3461 / 1930 | 2944 / -9402 / -2099 / 386 | 4048 / -10907 / -5123 / 506 | 4306 / -12361 / -5081 / 690 | - |

Same ranking at equal L6M ulcer (every mix scaled to the reference's L6M ulcer):

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|

BEST MIX AMONG THOSE WITH BLOCK PERSISTENCE >= 0.58: NONE passes (0 mixes pass the L6M guard and the 0.58 persistence together).

No distinct mix: with 1 member(s) every weight vector in the grid is the reference direction (or has no other direction passing the L6M guard): the only choice is a common SCALE, and at equal worst-prior-year max drawdown the scale is fixed by the basis (k = 1 for the reference itself). Sizing A to its worst prior year = its own 2024 max DD -12361.

GATES for the top mix (equal-risk ranking): walk-forward persistence 1.0 over 65 periods (equal weights was the pick in 15; gate >= 0.58); prior-year band ; null: PENDING (needs random-entry book series, ~2,000 sm); 27/30: not computed (shown only).
