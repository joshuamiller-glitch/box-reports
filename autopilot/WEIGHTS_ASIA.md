# WEIGHTS_ASIA - weight search on book-alone sums (W-LAYERS, 2026-11-22 06:32Z)

Prereg: autopilot/WEIGHTS_PREREG.md (sha in DECISIONS.md). A mix is the SUM of weight x book-alone daily P&L (42 months, 1 lot); no stack interaction; engine check pending.
Run 2026-11-22 06:32Z; pool hash (asia pool file) c6188a6c2818; dynamic scopes (loop finals): FINAL_asia_own_d8_nol3_w, FINAL_asia_stay_d8+asia_stay_d8_nol3+asia_stay_d8_nol3_w.

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

Equal-weight reference: worst prior-year max DD -21315. Cells `ulcer / max DD / worst week / $/wk` at 1 lot x scale k; every mix scaled to the reference's worst-prior-year max DD (k shown).

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| equal weights | 1/1/1 | 1.00 | 3919 / -11810 / -10890 / 7523 | 3715 / -9947 / -6030 / 7722 | 4212 / -10951 / -5576 / 770 | 5258 / -16854 / -5936 / 1576 | 8760 / -21315 / -16039 / 791 | - |
| top 1 | 1/2/1.5 | 0.67 | 4123 / -11842 / -10212 / 7661 | 4217 / -11842 / -6175 / 7822 | 4345 / -10380 / -5577 / 876 | 4648 / -13606 / -5556 / 1590 | 8784 / -21315 / -13325 / 641 | 0.452 |
| top 2 | 1.5/4/3 | 0.35 | 4071 / -11943 / -9371 / 7569 | 4227 / -11943 / -5817 / 7741 | 4284 / -9952 / -5390 / 879 | 4482 / -12785 / -5305 / 1546 | 8658 / -21315 / -12153 / 577 | 0.441 |
| top 3 | 1.5/3/2 | 0.45 | 4192 / -12000 / -10509 / 7479 | 4271 / -12000 / -6410 / 7602 | 4330 / -10186 / -5554 / 879 | 4527 / -12569 / -5447 / 1578 | 8688 / -21315 / -12993 / 626 | 0.452 |
| top 4 | 3/4/4 | 0.27 | 3705 / -10947 / -9772 / 7470 | 3687 / -10107 / -5542 / 7692 | 4094 / -10468 / -5359 / 778 | 4923 / -16019 / -5649 / 1527 | 8495 / -21315 / -14611 / 712 | 0.624 |
| top 5 | 2/3/3 | 0.37 | 3633 / -10601 / -9334 / 7432 | 3674 / -10141 / -5348 / 7661 | 4046 / -10263 / -5266 / 778 | 4801 / -15671 / -5529 / 1505 | 8405 / -21315 / -14046 / 681 | 0.613 |

Same ranking at equal L6M ulcer (every mix scaled to the reference's L6M ulcer):

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| top 1 | 0.5/0.25/3 | 2.00 | 3919 / -13416 / -8441 / 16818 | 3787 / -13416 / 149 / 18866 | 13389 / -30295 / -13055 / 703 | 25397 / -73952 / -20040 / 2303 | 23643 / -68639 / -34467 / 1643 | 0.183 |
| top 2 | 0.25/0.25/1.5 | 3.61 | 3919 / -13381 / -7890 / 16516 | 4055 / -13381 / -1662 / 18306 | 11569 / -27879 / -10408 / 873 | 21189 / -65680 / -16795 / 2400 | 21714 / -64410 / -32075 / 1523 | 0.172 |
| top 3 | 0.25/0/2 | 3.33 | 3919 / -13227 / -9469 / 16415 | 3720 / -13227 / 1226 / 18775 | 15987 / -32402 / -15552 / 433 | 30010 / -81789 / -23837 / 1990 | 27723 / -75042 / -34418 / 1635 | 0.215 |
| top 4 | 0.5/0/3 | 2.03 | 3919 / -12254 / -8307 / 15653 | 3547 / -12254 / 1941 / 17808 | 14865 / -31030 / -14869 / 448 | 28005 / -76654 / -21904 / 1988 | 25389 / -71106 / -34078 / 1631 | 0.194 |
| top 5 | 1/0.5/4 | 1.20 | 3919 / -12900 / -6288 / 14990 | 3647 / -11495 / -98 / 16589 | 10941 / -26447 / -10800 / 748 | 20378 / -61324 / -15546 / 2241 | 19040 / -58120 / -31958 / 1539 | 0.161 |

BEST MIX AMONG THOSE WITH BLOCK PERSISTENCE >= 0.58 (321 mixes pass the guard and 0.58): 

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| best passing | 3/4/4 | 0.27 | 3705 / -10947 / -9772 / 7470 | 3687 / -10107 / -5542 / 7692 | 4094 / -10468 / -5359 / 778 | 4923 / -16019 / -5649 / 1527 | 8495 / -21315 / -14611 / 712 | 0.624 |

GATES for the top mix (equal-risk ranking): walk-forward persistence 0.263 over 80 periods (equal weights was the pick in 0; gate >= 0.58); prior-year band 2023 GREEN (-10%), 2024 GREEN (-14%), 2025 AMBER (+19%); null: PENDING (needs random-entry book series, ~2,000 sm); 27/30: not computed (shown only).

### Scope UNION - members J502, L7c368a4f, La010c3eb, L578701ed (4095 mixes; weight grid [0, 0.25, 0.5, 1, 1.5, 2, 3, 4]; SUM of book-alone series, no stack interaction)

Equal-weight reference: worst prior-year max DD -37295. Cells `ulcer / max DD / worst week / $/wk` at 1 lot x scale k; every mix scaled to the reference's worst-prior-year max DD (k shown).

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| equal weights | 1/1/1/1 | 1.00 | 5566 / -17718 / -14837 / 8384 | 4350 / -14313 / -2788 / 8628 | 3780 / -10067 / -4076 / 1228 | 8626 / -28328 / -9893 / 1971 | 13948 / -37295 / -17602 / 866 | - |
| top 1 | 4/3/0/2 | 0.56 | 5343 / -17615 / -14271 / 12308 | 4860 / -13812 / -6959 / 12923 | 7000 / -19495 / -8355 / 1028 | 10302 / -35148 / -9835 / 2392 | 13923 / -37295 / -28200 / 1392 | 0.226 |
| top 2 | 3/2/0/1.5 | 0.77 | 5061 / -16739 / -13185 / 12129 | 4720 / -13257 / -6429 / 12763 | 6804 / -18755 / -8078 / 1013 | 9945 / -34418 / -9523 / 2323 | 13583 / -37295 / -26929 / 1324 | 0.258 |
| top 3 | 2/2/0/1 | 0.99 | 5787 / -18787 / -16185 / 12012 | 4957 / -14391 / -7894 / 12540 | 7114 / -20201 / -8556 / 1002 | 10604 / -34867 / -10034 / 2422 | 14574 / -37295 / -29737 / 1483 | 0.215 |
| top 4 | 3/2/0.25/2 | 0.68 | 5309 / -16991 / -14135 / 11826 | 4995 / -13456 / -6503 / 12346 | 6127 / -16625 / -7681 / 1150 | 9166 / -31772 / -9276 / 2354 | 13787 / -37295 / -24694 / 1208 | 0.29 |
| top 5 | 4/3/0.25/2 | 0.53 | 5195 / -17221 / -14057 / 11784 | 4643 / -13130 / -6164 / 12373 | 6511 / -18452 / -7692 / 1036 | 10235 / -34857 / -9555 / 2320 | 13767 / -37295 / -26945 / 1330 | 0.237 |

Same ranking at equal L6M ulcer (every mix scaled to the reference's L6M ulcer):

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| top 1 | 4/1/0/0.25 | 1.78 | 5566 / -17190 / -9132 / 21080 | 4867 / -15921 / 1630 / 23529 | 16843 / -39011 / -17503 / 881 | 32193 / -92711 / -24517 / 3031 | 29228 / -87809 / -46803 / 2261 | 0.161 |
| top 2 | 4/1/0.25/0.25 | 1.67 | 5566 / -17762 / -9565 / 20142 | 4855 / -17249 / 1390 / 22458 | 14913 / -36280 / -16420 / 1019 | 31625 / -91803 / -24119 / 3010 | 29850 / -89140 / -44574 / 2153 | 0.151 |
| top 3 | 4/1/0/0 | 1.81 | 5566 / -17654 / -8992 / 20042 | 4593 / -15463 / 3452 / 22584 | 18417 / -40453 / -19130 / 654 | 34497 / -95104 / -26164 / 2752 | 30790 / -90018 / -46500 / 2253 | 0.183 |
| top 4 | 4/1/0.25/0 | 1.69 | 5566 / -16497 / -9628 / 19093 | 4737 / -16456 / 2424 / 21487 | 15958 / -37232 / -17872 / 805 | 33641 / -93721 / -25573 / 2739 | 31274 / -91067 / -44114 / 2137 | 0.183 |
| top 5 | 4/1/0.5/0.5 | 1.47 | 5566 / -18676 / -9827 / 19014 | 4970 / -18584 / -364 / 21008 | 12105 / -31741 / -13237 / 1253 | 27536 / -83615 / -21014 / 3038 | 27554 / -83097 / -40338 / 1943 | 0.14 |

BEST MIX AMONG THOSE WITH BLOCK PERSISTENCE >= 0.58 (1590 mixes pass the guard and 0.58): 

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| best passing | 2/0.25/0/0.5 | 1.53 | 2419 / -8179 / -4776 / 9739 | 2644 / -8179 / -2133 / 10717 | 6169 / -15347 / -4766 / 601 | 10750 / -35484 / -8684 / 1449 | 12680 / -37295 / -17317 / 812 | 0.613 |

GATES for the top mix (equal-risk ranking): walk-forward persistence 0.175 over 80 periods (equal weights was the pick in 0; gate >= 0.58); prior-year band 2023 RED (+55%), 2024 GREEN (-2%), 2025 GREEN (-61%); null: PENDING (needs random-entry book series, ~2,000 sm); 27/30: not computed (shown only).

### Scope FINAL_asia_own_d8_nol3_w - members Lb0e6dfa3, L385f4f2e, L92a90948, L6b373671, L578701ed (32767 mixes; weight grid [0, 0.25, 0.5, 1, 1.5, 2, 3, 4]; SUM of book-alone series, no stack interaction)

Equal-weight reference: worst prior-year max DD -17403. Cells `ulcer / max DD / worst week / $/wk` at 1 lot x scale k; every mix scaled to the reference's worst-prior-year max DD (k shown).

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| equal weights | 1/1/1/1/1 | 1.00 | 3086 / -9450 / -4971 / 10869 | 3366 / -9283 / -1858 / 10614 | 5200 / -11178 / -7756 / 1042 | 4545 / -16311 / -8171 / 1917 | 6567 / -17403 / -9888 / 1982 | - |
| top 1 | 4/3/1.5/4/4 | 0.29 | 3435 / -10457 / -4589 / 11549 | 3721 / -10457 / -2388 / 10766 | 5045 / -12001 / -6925 / 1188 | 4872 / -17403 / -8198 / 1971 | 6883 / -17125 / -9596 / 1904 | 0.376 |
| top 2 | 4/3/2/4/4 | 0.29 | 3426 / -10447 / -4901 / 11549 | 3719 / -10447 / -2330 / 10848 | 5143 / -11964 / -7265 / 1181 | 4845 / -17403 / -8111 / 1994 | 6846 / -17085 / -9427 / 1958 | 0.344 |
| top 3 | 4/3/3/4/4 | 0.28 | 3442 / -10429 / -5511 / 11549 | 3737 / -10429 / -2218 / 11009 | 5423 / -11954 / -7930 / 1167 | 4805 / -17403 / -8362 / 2039 | 6852 / -17032 / -9128 / 2063 | 0.183 |
| top 4 | 3/2/2/3/3 | 0.39 | 3505 / -10619 / -5586 / 11532 | 3794 / -10619 / -2304 / 10894 | 5393 / -12046 / -7805 / 1187 | 4830 / -17403 / -8234 / 2037 | 6819 / -17224 / -9454 / 2045 | 0.258 |
| top 5 | 3/2/1.5/3/3 | 0.39 | 3502 / -10634 / -5173 / 11532 | 3788 / -10634 / -2381 / 10785 | 5205 / -12080 / -7353 / 1197 | 4863 / -17403 / -8152 / 2007 | 6830 / -17280 / -9681 / 1973 | 0.333 |

Same ranking at equal L6M ulcer (every mix scaled to the reference's L6M ulcer):

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| top 1 | 1/3/0/1.5/1.5 | 0.79 | 3086 / -9765 / -5698 / 13531 | 3216 / -9765 / -2561 / 13437 | 5482 / -12663 / -6086 / 1112 | 6493 / -21881 / -8826 / 2016 | 8933 / -26906 / -11995 / 1725 | 0.344 |
| top 2 | 0.25/1/0/0.5/0.5 | 2.46 | 3086 / -10466 / -5597 / 13441 | 3056 / -10466 / -2751 / 13556 | 5762 / -12731 / -6176 / 1076 | 6792 / -23704 / -8365 / 1989 | 9454 / -29048 / -12337 / 1650 | 0.333 |
| top 3 | 1/3/1/2/1.5 | 0.71 | 3086 / -10508 / -5643 / 13410 | 3174 / -10508 / -1655 / 13713 | 6140 / -13840 / -7931 / 1038 | 6815 / -23955 / -9261 / 2083 | 8650 / -26649 / -13238 / 2088 | 0.183 |
| top 4 | 1.5/3/1/2/1.5 | 0.65 | 3086 / -9163 / -5700 / 13308 | 3410 / -9163 / -1377 / 13247 | 5709 / -13399 / -7525 / 1081 | 6287 / -20466 / -9795 / 2082 | 8204 / -24794 / -12366 / 2147 | 0.183 |
| top 5 | 1.5/3/0.5/2/1.5 | 0.66 | 3086 / -9681 / -5547 / 13305 | 3406 / -9681 / -1487 / 13068 | 5533 / -13381 / -6732 / 1093 | 6196 / -19349 / -9506 / 2025 | 8192 / -24506 / -11399 / 2021 | 0.237 |

BEST MIX AMONG THOSE WITH BLOCK PERSISTENCE >= 0.58 (14268 mixes pass the guard and 0.58): 

| mix | weights | k | L6M | L3M | 2023 | 2024 | 2025 | persistence |
|---|---|---|---|---|---|---|---|---|
| best passing | 4/4/1.5/3/4 | 0.28 | 3152 / -10166 / -4504 / 11185 | 3513 / -10166 / -2647 / 10516 | 4440 / -10599 / -6410 / 1142 | 4592 / -17090 / -7977 / 1910 | 6804 / -17403 / -9755 / 1742 | 0.581 |

GATES for the top mix (equal-risk ranking): walk-forward persistence 0.225 over 80 periods (equal weights was the pick in 0; gate >= 0.58); prior-year band 2023 GREEN (-18%), 2024 GREEN (+4%), 2025 GREEN (+8%); null: PENDING (needs random-entry book series, ~2,000 sm); 27/30: not computed (shown only).

### Scope FINAL_asia_stay_d8+asia_stay_d8_nol3+asia_stay_d8_nol3_w - members Lb0e6dfa3 (7 mixes; weight grid [0, 0.25, 0.5, 1, 1.5, 2, 3, 4]; SUM of book-alone series, no stack interaction)

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
