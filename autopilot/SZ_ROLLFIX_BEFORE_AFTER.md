# SZ_ROLLFIX_BEFORE_AFTER - ROLLFIX1 base vs the ROLL-EXCL / raw S1b bases (SZ-CORE)

Engine ROLLFIX1 = flatten at every contract roll + 5-minute entry blackout (code/th_sz/sz_exact_roll.py); 14 roll months rebuilt, the other 29 months are hard links (bit-identical). Windows as of 2026-11-09, all weeks, USD/week mean (carry-dropped convention of Z.score_daily with live = itself, so mean here is the plain window mean), maxDD / worst-20 on all weeks. Old trade lists kept: base_b (alias base_b_rollexcl).

## COMB

| window | maxDD before (ROLL-EXCL) | maxDD before (raw) | maxDD after | mean before (ROLL-EXCL) | mean before (raw) | mean after |
|--|--|--|--|--|--|--|
| L1M | 79821 | 79821 | 79821 | -26607 | -26607 | -26607 |
| L2M | 79821 | 79821 | 79821 | +30483 | +30326 | +30623 |
| L3M | 79907 | 79907 | 79907 | +17459 | +17354 | +17552 |
| L6M | 79907 | 79907 | 79907 | +22948 | +22996 | +22949 |
| HOLD | 99496 | 99496 | 99496 | +15901 | +15522 | +16391 |
| MID | 67340 | 88531 | 67975 | +13046 | +11120 | +12989 |
| PRE | 140288 | 140288 | 140288 | +14626 | +14777 | +14408 |
| X' | 128944 | 116941 | 137520 | +1800 | +2181 | +1645 |

Trades: 21135 before, 21163 after.

## NOCUT

| window | maxDD before (ROLL-EXCL) | maxDD before (raw) | maxDD after | mean before (ROLL-EXCL) | mean before (raw) | mean after |
|--|--|--|--|--|--|--|
| L1M | 115144 | 115144 | 115144 | -38381 | -38381 | -38381 |
| L2M | 115144 | 115144 | 115144 | +25065 | +24907 | +27074 |
| L3M | 127264 | 127264 | 127264 | +9693 | +9588 | +11032 |
| L6M | 182380 | 182380 | 182380 | +14632 | +14665 | +15218 |
| HOLD | 182380 | 182380 | 182380 | +11257 | +10840 | +11643 |
| MID | 114170 | 135361 | 114420 | +7812 | +5886 | +7790 |
| PRE | 127656 | 127656 | 127656 | +13466 | +13618 | +13281 |
| X' | 141889 | 129112 | 139796 | +1970 | +2351 | +2074 |

Trades: 18960 before, 18981 after.

## UNIF

| window | maxDD before (ROLL-EXCL) | maxDD before (raw) | maxDD after | mean before (ROLL-EXCL) | mean before (raw) | mean after |
|--|--|--|--|--|--|--|
| L1M | 106459 | 106459 | 106459 | -35486 | -35486 | -35486 |
| L2M | 106459 | 106459 | 106459 | +25012 | +24854 | +26227 |
| L3M | 147790 | 147790 | 147790 | +4642 | +4537 | +5452 |
| L6M | 174856 | 174856 | 174856 | +12989 | +13037 | +13371 |
| HOLD | 174856 | 174856 | 174856 | +11275 | +10865 | +11440 |
| MID | 96285 | 117476 | 96920 | +14460 | +12534 | +14403 |
| PRE | 134464 | 134464 | 134464 | +14790 | +14942 | +14611 |
| X' | 137804 | 125099 | 149703 | +2223 | +2603 | +2001 |

Trades: 19797 before, 19822 after.

## HOLD

| window | maxDD before (ROLL-EXCL) | maxDD before (raw) | maxDD after | mean before (ROLL-EXCL) | mean before (raw) | mean after |
|--|--|--|--|--|--|--|
| L1M | 62660 | 62660 | 62660 | -20887 | -20887 | -20887 |
| L2M | 62660 | 62660 | 62660 | +31177 | +31177 | +31548 |
| L3M | 98881 | 98881 | 98881 | +13145 | +13145 | +13393 |
| L6M | 119980 | 119980 | 119980 | +18758 | +18758 | +18737 |
| HOLD | 119980 | 119980 | 119980 | +14270 | +14270 | +14957 |
| MID | 90857 | 90857 | 70301 | +14614 | +14614 | +16483 |
| PRE | 155580 | 155580 | 158295 | +8602 | +8602 | +8423 |
| X' | 75870 | 75870 | 78398 | +5247 | +5247 | +4769 |

Trades: 23855 before, 23901 after.

