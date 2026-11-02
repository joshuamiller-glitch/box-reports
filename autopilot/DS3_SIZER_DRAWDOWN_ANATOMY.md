# DS3_SIZER_DRAWDOWN_ANATOMY - what a sizer could possibly fix (BASE-4, 2026-11-02T18:54Z)

Base = T-SIZER base (run_v13t_ts: V13T_LIVE + live ER(20) 5-min ladder x1.5 if ER>=0.30 else x0.5, zone HALF, sequential rounding, lock R scaled only when mult > 1; lock none = per-book locks). Every trade of the 6 live books in the episode; ER = the ER(20) value at the signal; mult = the ladder multiplier (zone half separate, flagged); lots = contracts traded (integer); "net at x1" = the same trade rescaled linearly to the session lots without the ladder (session lots after zone half, rounded): an approximation that keeps the same trades, the same exits and the same locks, so it is NOT the same as the ladder-OFF engine run, which is reported beside it. Exit type: stop / target / cut (TH-L2 loss cut) / lock (per-book week floor or day give-back flattened it) / flat (session flat). Table only, no recommendation.

## Summary (all three episodes)
net of the 6 live books summed from the trades; the 11-book day series also holds the X1-X5 cells (not trade-resolved), which is why it differs; ladder OFF = a separate engine run (same locks / cuts, lots x1, the trade set can differ); x1-rescaled = the same trades rescaled linearly.
| episode | label days | trades | trade net $ (live ladder) | 11-book day series $ | ladder OFF engine run $ | same trades at x1 $ | x1.5 trades net (at x1) | x0.5 trades net (at x1) | x1.5 share of gross loss / of trades |
|---|---|---|---|---|---|---|---|---|---|
| Episode A | 20260720..20260911 | 1229 | -140,019 | -170,420 | -73,564 | -86,326 | -141,028 (x1: -90,954) | 1,009 (x1: 4,629) | 63% / 37% |
| Episode B1 | 20250203..20250228 | 352 | -164,605 | -160,713 | -61,568 | -77,434 | -201,180 (x1: -128,371) | 36,574 (x1: 50,937) | 77% / 46% |
| Episode B2 | 20240801..20250131 | 2485 | 428,721 | 498,251 | 435,204 | 392,488 | 319,208 (x1: 188,600) | 109,512 (x1: 203,888) | 69% / 45% |


## Episode A: the 2026 drawdown, peak week 202630 -> trough week 202637 (weekly-cumulative maxDD of the F9/L6M window $170,420; the lead called it W28-W39)

1229 trades, 20260720..20260911. Net P&L of the episode at the live ladder: $-140,019 (day-series check $-170,420); weekly-cumulative maxDD inside it $170,420; the same period with the ladder OFF (separate engine run, lots x1): $-73,564; the SAME trades rescaled to x1 lots (size-neutral, linear in lots): $-86,326. Gross loss (sum of losing trades) $-1,522,971, gross win $1,382,952.

### By ER bucket / multiplier (the sizer question)
| bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| ER<0.30 (x0.5) | 772 | 1372 | 1,009 | -1% | -560,322 | 561,331 | 4,629 | -993,763 |
| ER>=0.30 (x1.5) | 457 | 2193 | -141,028 | 101% | -962,649 | 821,621 | -90,954 | -611,390 |

### By book
| book | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| HM | 159 | 437 | -19,805 | 14% | -179,183 | 159,377 | 1,079 | -209,353 |
| KB | 425 | 681 | -60,590 | 43% | -295,532 | 234,942 | -61,697 | -325,405 |
| MV | 196 | 321 | -40,162 | 29% | -144,785 | 104,623 | -33,049 | -144,561 |
| PB | 84 | 131 | 3,309 | -2% | -70,272 | 73,581 | 1,235 | -45,630 |
| PE | 264 | 1639 | -54,936 | 39% | -699,996 | 645,060 | -3,516 | -730,947 |
| SM | 101 | 356 | 32,164 | -23% | -133,205 | 165,369 | 9,622 | -149,256 |

### By session
| session | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| asia | 601 | 1913 | -21,831 | 16% | -810,813 | 788,982 | -6,416 | -875,744 |
| london | 430 | 1361 | -85,674 | 61% | -591,932 | 506,258 | -56,847 | -627,180 |
| nyam | 142 | 200 | -21,214 | 15% | -79,015 | 57,802 | -12,670 | -54,013 |
| nypm | 56 | 91 | -11,301 | 8% | -41,211 | 29,910 | -10,392 | -48,215 |

### By lots bucket
| lots bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| 1 | 472 | 472 | -21,877 | 16% | -199,526 | 177,649 | -35,158 | -331,806 |
| 2-3 | 440 | 1056 | -85,505 | 61% | -469,255 | 383,750 | -57,458 | -458,447 |
| 4-6 | 230 | 1080 | 37,069 | -26% | -425,886 | 462,956 | 50,649 | -542,343 |
| 7+ | 87 | 957 | -69,707 | 50% | -428,304 | 358,597 | -44,359 | -272,557 |

### By split add filled
| split add filled | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| False | 175 | 380 | 127,966 | -91% | -92,884 | 220,850 | 151,925 | -72,369 |
| True | 1054 | 3185 | -267,985 | 191% | -1,430,088 | 1,162,102 | -238,251 | -1,532,784 |

### By exit type
| exit type | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| cut | 735 | 2257 | -1,410,512 | 1007% | -1,441,197 | 30,685 | -1,513,274 | -1,549,805 |
| flat | 1 | 1 | -52 | 0% | -52 | 0 | -105 | -105 |
| lock | 45 | 67 | -15,589 | 11% | -16,780 | 1,191 | -10,250 | -10,986 |
| stop | 35 | 53 | -64,942 | 46% | -64,942 | 0 | -44,258 | -44,258 |
| target | 413 | 1187 | 1,351,076 | -965% | 0 | 1,351,076 | 1,481,561 | 0 |

### By side (+1 long)
| side (+1 long) | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| -1.0 | 603 | 1786 | -74,936 | 54% | -778,881 | 703,945 | -39,480 | -810,609 |
| 1.0 | 626 | 1779 | -65,084 | 46% | -744,091 | 679,007 | -46,845 | -794,544 |

### Book x ER bucket (net $)
| book | ER<0.30 (x0.5) | ER>=0.30 (x1.5) |
|---|---|---|
| HM | 9,867 | -29,672 |
| KB | -18,155 | -42,435 |
| MV | -8,733 | -31,429 |
| PB | -839 | 4,148 |
| PE | 27,735 | -82,671 |
| SM | -8,866 | 41,030 |

### Worst 30 trades
| label day | book | session | side | ER(20) | lots | mult | net $ | net at x1 $ | exit | entry | zone |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 20260806 | PE | asia | S | 0.47 | 11 | x1.5 | -10,258 | -6,528 | cut | add |  |
| 20260729 | PE | asia | S | 0.36 | 11 | x1.5 | -9,642 | -6,136 | cut | add |  |
| 20260720 | PE | asia | L | 0.30 | 11 | x1.5 | -9,199 | -5,854 | cut | add |  |
| 20260729 | PE | asia | S | 0.52 | 11 | x1.5 | -9,037 | -5,751 | cut | add |  |
| 20260730 | PE | london | L | 0.39 | 11 | x1.5 | -8,502 | -5,410 | cut | add |  |
| 20260730 | PE | asia | L | 0.39 | 11 | x1.5 | -8,409 | -5,351 | cut | add |  |
| 20260824 | PE | london | S | 0.52 | 11 | x1.5 | -8,080 | -5,142 | cut | add |  |
| 20260902 | PE | london | S | 0.39 | 11 | x1.5 | -8,080 | -5,142 | cut | add |  |
| 20260827 | PE | asia | L | 0.69 | 11 | x1.5 | -7,926 | -5,044 | cut | add |  |
| 20260904 | PE | asia | S | 0.37 | 11 | x1.5 | -7,849 | -4,995 | cut | add |  |
| 20260817 | PE | london | L | 0.49 | 11 | x1.5 | -7,796 | -4,961 | cut | add |  |
| 20260826 | PE | asia | L | 0.36 | 11 | x1.5 | -7,698 | -4,899 | cut | add |  |
| 20260909 | PE | london | S | 0.59 | 11 | x1.5 | -7,488 | -4,765 | cut | add |  |
| 20260729 | PE | asia | S | 0.44 | 11 | x1.5 | -7,481 | -4,761 | cut | add |  |
| 20260728 | PE | asia | S | 0.39 | 11 | x1.5 | -7,480 | -4,760 | cut | add |  |
| 20260731 | PE | asia | L | 0.54 | 11 | x1.5 | -7,433 | -4,730 | cut | add |  |
| 20260729 | PE | london | L | 0.47 | 11 | x1.5 | -7,424 | -4,725 | cut | add |  |
| 20260904 | PE | london | S | 0.40 | 11 | x1.5 | -7,368 | -4,689 | cut | add |  |
| 20260818 | PE | asia | S | 0.51 | 11 | x1.5 | -7,328 | -4,664 | cut | add |  |
| 20260831 | PE | london | L | 0.43 | 11 | x1.5 | -7,313 | -4,654 | cut | add |  |
| 20260903 | PE | asia | L | 0.33 | 11 | x1.5 | -7,185 | -4,572 | cut | add |  |
| 20260812 | PE | london | L | 0.43 | 11 | x1.5 | -7,181 | -4,570 | cut | add |  |
| 20260908 | PE | london | S | 0.46 | 11 | x1.5 | -7,168 | -4,562 | cut | add |  |
| 20260805 | PE | london | S | 0.49 | 11 | x1.5 | -7,165 | -4,559 | cut | add |  |
| 20260827 | PE | london | L | 0.43 | 11 | x1.5 | -7,095 | -4,515 | cut | add |  |
| 20260821 | PE | london | L | 0.39 | 11 | x1.5 | -7,085 | -4,509 | cut | add |  |
| 20260902 | PE | london | L | 0.37 | 11 | x1.5 | -7,073 | -4,501 | cut | add |  |
| 20260820 | PE | london | S | 0.43 | 11 | x1.5 | -7,047 | -4,485 | cut | add |  |
| 20260819 | PE | london | L | 0.51 | 11 | x1.5 | -7,034 | -4,476 | cut | add |  |
| 20260820 | PE | asia | L | 0.63 | 11 | x1.5 | -7,025 | -4,471 | cut | add |  |

### Worst 10 days
| label day | day net $ | trades | lots | day net at x1 $ | share of trades at x1.5 | mean ER |
|---|---|---|---|---|---|---|
| 20260720 | -53,219 | 47 | 133 | -47,436 | 34% | 0.22 |
| 20260730 | -43,085 | 54 | 162 | -25,860 | 33% | 0.25 |
| 20260806 | -38,770 | 37 | 95 | -37,749 | 30% | 0.20 |
| 20260819 | -38,263 | 31 | 92 | -28,513 | 42% | 0.25 |
| 20260907 | -26,865 | 15 | 48 | -26,207 | 47% | 0.27 |
| 20260828 | -26,714 | 14 | 52 | -21,731 | 57% | 0.32 |
| 20260903 | -25,426 | 30 | 95 | -22,346 | 53% | 0.32 |
| 20260803 | -22,812 | 36 | 80 | -33,551 | 22% | 0.22 |
| 20260904 | -22,359 | 21 | 72 | -7,637 | 29% | 0.25 |
| 20260902 | -21,565 | 21 | 71 | -16,004 | 38% | 0.22 |

### Size effect in one line
x1.5 trades (457): net $-141,028 (at x1: $-90,954, so the 1.5 multiplier moved $-50,074); x0.5 trades (772): net $1,009 (at x1: $4,629, the 0.5 multiplier moved $-3,620); loss share: x1.5 trades carry 63% of the gross loss, x0.5 trades 37% (their share of trades 37% / 63%).

## Episode B1: the PRE drawdown, peak week 202506 -> trough week 202509 (maxDD $160,713)

352 trades, 20250203..20250228. Net P&L of the episode at the live ladder: $-164,605 (day-series check $-160,713); weekly-cumulative maxDD inside it $160,713; the same period with the ladder OFF (separate engine run, lots x1): $-61,568; the SAME trades rescaled to x1 lots (size-neutral, linear in lots): $-77,434. Gross loss (sum of losing trades) $-553,391, gross win $388,786.

### By ER bucket / multiplier (the sizer question)
| bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| ER<0.30 (x0.5) | 189 | 337 | 36,574 | -22% | -125,444 | 162,019 | 50,937 | -225,154 |
| ER>=0.30 (x1.5) | 163 | 832 | -201,180 | 122% | -427,947 | 226,767 | -128,371 | -270,695 |

### By book
| book | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| HM | 43 | 115 | -9,784 | 6% | -51,757 | 41,973 | -8,224 | -54,203 |
| KB | 122 | 197 | -17,712 | 11% | -83,621 | 65,909 | -3,778 | -82,209 |
| MV | 48 | 92 | -31,587 | 19% | -50,038 | 18,451 | -24,369 | -38,983 |
| PB | 18 | 30 | -3,007 | 2% | -16,489 | 13,482 | 1,652 | -8,245 |
| PE | 91 | 628 | -109,971 | 67% | -310,072 | 200,102 | -47,656 | -270,872 |
| SM | 30 | 107 | 7,456 | -5% | -41,413 | 48,869 | 4,941 | -41,337 |

### By session
| session | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| asia | 136 | 474 | 5,836 | -4% | -202,402 | 208,238 | 18,320 | -195,684 |
| london | 109 | 430 | -133,561 | 81% | -223,992 | 90,431 | -102,773 | -199,281 |
| nyam | 83 | 229 | -28,784 | 17% | -109,806 | 81,023 | 8,590 | -82,360 |
| nypm | 24 | 36 | -8,097 | 5% | -17,191 | 9,094 | -1,571 | -18,524 |

### By lots bucket
| lots bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| 1 | 115 | 115 | 15,062 | -9% | -39,408 | 54,470 | 13,982 | -66,965 |
| 2-3 | 137 | 328 | -75,063 | 46% | -164,633 | 89,570 | -52,218 | -143,174 |
| 4-6 | 60 | 286 | 35,188 | -21% | -106,846 | 142,034 | 49,761 | -131,389 |
| 7+ | 40 | 440 | -139,793 | 85% | -242,504 | 102,712 | -88,959 | -154,321 |

### By split add filled
| split add filled | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| False | 44 | 98 | 22,806 | -14% | -25,695 | 48,500 | 25,732 | -22,051 |
| True | 308 | 1071 | -187,411 | 114% | -527,697 | 340,286 | -103,166 | -473,798 |

### By exit type
| exit type | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| cut | 202 | 724 | -479,404 | 291% | -481,131 | 1,728 | -443,715 | -447,170 |
| flat | 4 | 21 | -6,367 | 4% | -6,886 | 519 | -3,855 | -4,201 |
| lock | 15 | 39 | -10,900 | 7% | -11,345 | 446 | -6,962 | -7,408 |
| stop | 14 | 46 | -54,029 | 33% | -54,029 | 0 | -37,071 | -37,071 |
| target | 117 | 339 | 386,094 | -235% | 0 | 386,094 | 414,169 | 0 |

### By side (+1 long)
| side (+1 long) | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| -1.0 | 161 | 590 | -105,479 | 64% | -287,197 | 181,719 | -85,448 | -254,839 |
| 1.0 | 191 | 579 | -59,127 | 36% | -266,194 | 207,067 | 8,014 | -241,010 |

### Book x ER bucket (net $)
| book | ER<0.30 (x0.5) | ER>=0.30 (x1.5) |
|---|---|---|
| HM | 162 | -9,946 |
| KB | 13,341 | -31,053 |
| MV | -3,835 | -27,752 |
| PB | 6,311 | -9,318 |
| PE | 20,619 | -130,589 |
| SM | -22 | 7,478 |

### Worst 30 trades
| label day | book | session | side | ER(20) | lots | mult | net $ | net at x1 $ | exit | entry | zone |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 20250224 | PE | nyam | S | 0.52 | 11 | x1.5 | -17,721 | -11,277 | stop | add |  |
| 20250227 | PE | nyam | S | 0.58 | 11 | x1.5 | -9,953 | -6,334 | stop | add |  |
| 20250204 | PE | nyam | L | 0.60 | 11 | x1.5 | -8,817 | -5,611 | cut | add |  |
| 20250218 | PE | london | L | 0.63 | 11 | x1.5 | -8,596 | -5,470 | cut | add |  |
| 20250205 | PE | london | S | 0.50 | 11 | x1.5 | -8,445 | -5,374 | cut | add |  |
| 20250224 | PE | asia | L | 0.40 | 11 | x1.5 | -8,248 | -5,249 | cut | add |  |
| 20250228 | PE | asia | S | 0.39 | 11 | x1.5 | -8,205 | -5,222 | cut | add |  |
| 20250210 | PE | asia | L | 0.55 | 11 | x1.5 | -8,117 | -5,165 | cut | add |  |
| 20250204 | PE | london | L | 0.36 | 11 | x1.5 | -8,087 | -5,146 | cut | add |  |
| 20250214 | PE | london | S | 0.43 | 11 | x1.5 | -7,961 | -5,066 | cut | add |  |
| 20250218 | PE | asia | S | 0.40 | 11 | x1.5 | -7,898 | -5,026 | cut | add |  |
| 20250204 | PE | asia | L | 0.40 | 11 | x1.5 | -7,815 | -4,973 | cut | add |  |
| 20250227 | PE | nyam | S | 0.43 | 11 | x1.5 | -7,507 | -4,777 | cut | add |  |
| 20250227 | PE | london | L | 0.55 | 11 | x1.5 | -7,353 | -4,679 | cut | add |  |
| 20250210 | PE | nyam | L | 0.38 | 11 | x1.5 | -7,340 | -4,671 | cut | add |  |
| 20250204 | PE | london | L | 0.31 | 11 | x1.5 | -7,305 | -4,648 | cut | add |  |
| 20250228 | PE | london | L | 0.36 | 11 | x1.5 | -7,216 | -4,592 | cut | add |  |
| 20250224 | PE | london | S | 0.48 | 11 | x1.5 | -6,967 | -4,434 | cut | add |  |
| 20250211 | PE | london | S | 0.49 | 11 | x1.5 | -6,961 | -4,430 | cut | add |  |
| 20250213 | PE | london | S | 0.40 | 11 | x1.5 | -6,922 | -4,405 | cut | add |  |
| 20250213 | PE | nyam | L | 0.34 | 11 | x1.5 | -6,917 | -4,402 | cut | add |  |
| 20250206 | PE | london | S | 0.41 | 11 | x1.5 | -6,914 | -4,400 | cut | add |  |
| 20250218 | PE | nyam | S | 0.45 | 11 | x1.5 | -6,874 | -4,374 | cut | add |  |
| 20250213 | PE | london | S | 0.60 | 11 | x1.5 | -6,866 | -4,369 | cut | add |  |
| 20250225 | PE | london | L | 0.46 | 11 | x1.5 | -6,835 | -4,349 | lock | add |  |
| 20250213 | PE | asia | L | 0.35 | 11 | x1.5 | -6,758 | -4,300 | cut | add |  |
| 20250203 | PE | london | L | 0.39 | 11 | x1.5 | -6,701 | -4,264 | cut | add |  |
| 20250204 | PE | asia | S | 0.35 | 11 | x1.5 | -6,683 | -4,253 | cut | add |  |
| 20250227 | PE | asia | L | 0.37 | 11 | x1.5 | -6,329 | -4,027 | cut | add |  |
| 20250203 | PE | asia | S | 0.52 | 11 | x1.5 | -6,130 | -3,901 | cut | add |  |

### Worst 10 days
| label day | day net $ | trades | lots | day net at x1 $ | share of trades at x1.5 | mean ER |
|---|---|---|---|---|---|---|
| 20250224 | -44,148 | 22 | 82 | -30,711 | 59% | 0.32 |
| 20250204 | -36,170 | 26 | 120 | -17,751 | 62% | 0.30 |
| 20250228 | -36,051 | 25 | 79 | -29,204 | 32% | 0.24 |
| 20250218 | -21,656 | 18 | 69 | -10,511 | 56% | 0.34 |
| 20250205 | -17,800 | 21 | 52 | -10,731 | 33% | 0.28 |
| 20250206 | -16,747 | 9 | 34 | -9,463 | 56% | 0.37 |
| 20250219 | -13,512 | 14 | 34 | -17,905 | 57% | 0.30 |
| 20250213 | -12,981 | 30 | 115 | -1,439 | 57% | 0.34 |
| 20250212 | -9,986 | 14 | 26 | -11,232 | 57% | 0.32 |
| 20250227 | -6,274 | 22 | 98 | -2,808 | 45% | 0.31 |

### Size effect in one line
x1.5 trades (163): net $-201,180 (at x1: $-128,371, so the 1.5 multiplier moved $-72,809); x0.5 trades (189): net $36,574 (at x1: $50,937, the 0.5 multiplier moved $-14,363); loss share: x1.5 trades carry 77% of the gross loss, x0.5 trades 23% (their share of trades 46% / 54%).

## Episode B2: 2024-08-01..2025-01-31 (PRE middle third, as ordered; contains the carrying weeks 202434-202451)

2485 trades, 20240801..20250131. Net P&L of the episode at the live ladder: $428,721 (day-series check $498,251); weekly-cumulative maxDD inside it $155,639; the same period with the ladder OFF (separate engine run, lots x1): $435,204; the SAME trades rescaled to x1 lots (size-neutral, linear in lots): $392,488. Gross loss (sum of losing trades) $-3,267,833, gross win $3,696,554.

### By ER bucket / multiplier (the sizer question)
| bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| ER<0.30 (x0.5) | 1359 | 2450 | 109,512 | 26% | -1,003,056 | 1,112,569 | 203,888 | -1,705,293 |
| ER>=0.30 (x1.5) | 1126 | 5626 | 319,208 | 74% | -2,264,777 | 2,583,985 | 188,600 | -1,433,920 |

### By book
| book | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| HM | 344 | 893 | 33,339 | 8% | -360,717 | 394,056 | -5,236 | -396,396 |
| KB | 787 | 1297 | 60,269 | 14% | -505,133 | 565,402 | 48,206 | -502,946 |
| MV | 414 | 693 | 55,460 | 13% | -262,648 | 318,108 | 43,722 | -215,662 |
| PB | 121 | 206 | 43,580 | 10% | -87,456 | 131,036 | 18,467 | -55,575 |
| PE | 628 | 4272 | 158,373 | 37% | -1,769,708 | 1,928,082 | 164,150 | -1,729,856 |
| SM | 191 | 715 | 77,699 | 18% | -282,171 | 359,870 | 123,179 | -238,777 |

### By session
| session | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| asia | 985 | 3553 | 305,260 | 71% | -1,416,767 | 1,722,027 | 288,796 | -1,382,238 |
| london | 652 | 2472 | -18,731 | -4% | -1,054,276 | 1,035,545 | 57,915 | -970,906 |
| nyam | 694 | 1795 | 155,433 | 36% | -689,244 | 844,678 | 50,563 | -671,717 |
| nypm | 154 | 256 | -13,241 | -3% | -107,546 | 94,305 | -4,786 | -114,352 |

### By lots bucket
| lots bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| 1 | 846 | 846 | 20,734 | 5% | -336,340 | 357,074 | 39,326 | -493,343 |
| 2-3 | 915 | 2174 | 186,115 | 43% | -848,754 | 1,034,869 | 153,076 | -766,192 |
| 4-6 | 466 | 2218 | 85,178 | 20% | -919,727 | 1,004,906 | 113,099 | -1,139,579 |
| 7+ | 258 | 2838 | 136,693 | 32% | -1,163,012 | 1,299,705 | 86,986 | -740,098 |

### By split add filled
| split add filled | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| False | 316 | 845 | 323,329 | 75% | -174,881 | 498,210 | 282,954 | -141,027 |
| True | 2169 | 7231 | 105,392 | 25% | -3,092,952 | 3,198,344 | 109,534 | -2,998,186 |

### By exit type
| exit type | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| cut | 1341 | 4508 | -2,870,180 | -669% | -2,970,541 | 100,361 | -2,775,925 | -2,872,732 |
| flat | 13 | 32 | 6,290 | 1% | -2,734 | 9,023 | 5,323 | -2,872 |
| lock | 88 | 171 | -55,212 | -13% | -57,320 | 2,109 | -40,715 | -42,694 |
| stop | 76 | 216 | -237,238 | -55% | -237,238 | 0 | -220,914 | -220,914 |
| target | 967 | 3149 | 3,585,061 | 836% | 0 | 3,585,061 | 3,424,719 | 0 |

### By side (+1 long)
| side (+1 long) | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| -1.0 | 1177 | 3888 | 170,788 | 40% | -1,607,715 | 1,778,502 | 60,981 | -1,623,994 |
| 1.0 | 1308 | 4188 | 257,933 | 60% | -1,660,119 | 1,918,052 | 331,507 | -1,515,219 |

### Book x ER bucket (net $)
| book | ER<0.30 (x0.5) | ER>=0.30 (x1.5) |
|---|---|---|
| HM | -18,642 | 51,981 |
| KB | 7,781 | 52,488 |
| MV | 16,705 | 38,756 |
| PB | -6,646 | 50,225 |
| PE | 56,779 | 101,594 |
| SM | 53,535 | 24,164 |

### Worst 30 trades
| label day | book | session | side | ER(20) | lots | mult | net $ | net at x1 $ | exit | entry | zone |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 20241220 | PE | nyam | L | 0.59 | 11 | x1.5 | -16,848 | -10,721 | lock | add |  |
| 20240909 | PE | nyam | L | 0.39 | 11 | x1.5 | -16,011 | -10,189 | stop | add |  |
| 20241206 | PE | nyam | L | 0.47 | 11 | x1.5 | -14,240 | -9,062 | cut | add |  |
| 20240813 | PE | nyam | L | 0.55 | 11 | x1.5 | -13,807 | -8,786 | cut | add |  |
| 20240924 | PE | nyam | S | 0.48 | 11 | x1.5 | -13,774 | -8,765 | stop | no add |  |
| 20240905 | PE | nyam | L | 0.49 | 11 | x1.5 | -11,194 | -7,124 | cut | add |  |
| 20250120 | PE | london | S | 0.33 | 11 | x1.5 | -10,688 | -6,802 | cut | add |  |
| 20240906 | PE | london | L | 0.39 | 11 | x1.5 | -9,655 | -6,144 | stop | no add |  |
| 20241008 | PE | asia | S | 0.32 | 11 | x1.5 | -9,611 | -6,116 | cut | add |  |
| 20240913 | PE | asia | L | 0.51 | 11 | x1.5 | -9,428 | -5,999 | cut | add |  |
| 20241014 | PE | nyam | L | 0.70 | 11 | x1.5 | -9,413 | -5,990 | stop | add |  |
| 20250106 | PE | london | L | 0.44 | 11 | x1.5 | -9,367 | -5,961 | cut | add |  |
| 20241007 | PE | london | S | 0.32 | 11 | x1.5 | -8,925 | -5,679 | cut | add |  |
| 20241120 | PE | nyam | S | 0.79 | 11 | x1.5 | -8,843 | -5,628 | stop | add |  |
| 20240802 | PE | asia | S | 0.34 | 11 | x1.5 | -8,842 | -5,627 | cut | add |  |
| 20240812 | PE | asia | L | 0.38 | 11 | x1.5 | -8,820 | -5,613 | cut | add |  |
| 20250128 | PE | asia | L | 0.58 | 11 | x1.5 | -8,670 | -5,517 | cut | add |  |
| 20240823 | PE | asia | S | 0.36 | 11 | x1.5 | -8,583 | -5,462 | cut | add |  |
| 20240815 | PE | asia | L | 0.48 | 11 | x1.5 | -8,563 | -5,449 | cut | add |  |
| 20241018 | PE | asia | S | 0.37 | 11 | x1.5 | -8,540 | -5,435 | cut | add |  |
| 20250130 | PE | london | L | 0.57 | 11 | x1.5 | -8,429 | -5,364 | cut | add |  |
| 20240822 | PE | asia | L | 0.39 | 11 | x1.5 | -8,360 | -5,320 | cut | add |  |
| 20240827 | PE | london | S | 0.40 | 11 | x1.5 | -8,342 | -5,308 | cut | add |  |
| 20241126 | PE | asia | L | 0.57 | 11 | x1.5 | -8,317 | -5,293 | cut | add |  |
| 20241105 | PE | london | L | 0.40 | 11 | x1.5 | -8,284 | -5,272 | cut | add |  |
| 20240919 | PE | asia | S | 0.37 | 11 | x1.5 | -8,234 | -5,240 | cut | add |  |
| 20240807 | PE | asia | S | 0.47 | 11 | x1.5 | -8,227 | -5,235 | cut | add |  |
| 20250108 | PE | london | L | 0.39 | 11 | x1.5 | -8,185 | -5,209 | cut | add |  |
| 20240925 | PE | nyam | L | 0.64 | 11 | x1.5 | -8,182 | -5,207 | cut | add |  |
| 20250114 | PE | london | L | 0.38 | 11 | x1.5 | -8,171 | -5,200 | cut | add |  |

### Worst 10 days
| label day | day net $ | trades | lots | day net at x1 $ | share of trades at x1.5 | mean ER |
|---|---|---|---|---|---|---|
| 20240905 | -56,662 | 27 | 100 | -44,174 | 41% | 0.26 |
| 20250128 | -47,507 | 23 | 79 | -47,273 | 52% | 0.29 |
| 20250120 | -44,361 | 13 | 57 | -34,094 | 62% | 0.33 |
| 20240930 | -40,248 | 22 | 74 | -37,948 | 50% | 0.32 |
| 20240906 | -38,202 | 26 | 95 | -17,097 | 54% | 0.34 |
| 20250108 | -37,511 | 20 | 71 | -34,705 | 40% | 0.26 |
| 20241231 | -37,274 | 21 | 74 | -25,178 | 62% | 0.33 |
| 20241002 | -33,599 | 23 | 76 | -29,971 | 39% | 0.26 |
| 20241122 | -32,324 | 22 | 61 | -28,717 | 55% | 0.30 |
| 20241113 | -28,397 | 13 | 53 | -16,544 | 54% | 0.28 |

### Size effect in one line
x1.5 trades (1126): net $319,208 (at x1: $188,600, so the 1.5 multiplier moved $130,608); x0.5 trades (1359): net $109,512 (at x1: $203,888, the 0.5 multiplier moved $-94,375); loss share: x1.5 trades carry 69% of the gross loss, x0.5 trades 31% (their share of trades 45% / 55%).

## Reading (BASE-4; table only, no recommendation)
- In both drawdown episodes the loss sits in the ER >= 0.30 (x1.5) trades: A (2026, peak 202630 -> trough 202637): x1.5 trades net -141k (63% of the gross loss on 37% of the trades) while the x0.5 trades net about 0 (+1k); B1 (PRE, 202506 -> 202509): x1.5 -201k (77% of the gross loss on 46% of the trades), x0.5 +37k. In B2 (2024-08..2025-01, a net-positive stretch of +429k) the same x1.5 trades earn +319k.
- Size part vs trade part: the same trades at x1 lose -91k (A) and -128k (B1) in the x1.5 group, so the 1.5 multiplier adds -50k and -73k; the x0.5 multiplier removes only 3.6k and 14k of profit in the x0.5 group. The ladder-OFF engine run over the same weeks is -74k (A) and -62k (B1) against -140k / -165k with the ladder (trade sets differ slightly through locks and cuts), so about half the drawdown loss is the size excess of the x1.5 trades and the other half is the loss of those trades at x1 (what a sizer cannot fix by lots alone: the trades are high-ER losers).
- Where: the worst 30 trades of every episode are ALL PE (P6) trades, all at x1.5 (11 lots against 7 at x1), all with the split add filled, 27-30 of 30 ended by the TH-L2 cut. By exit type, the whole gross loss is cut trades (stop and lock exits are 2-5% of the loss). By ER bucket within the book table: PE x1.5 -35k in A (but PE x0.5 +89k).
- What a sizer could possibly fix: the part of the loss that comes from high-ER trades that lose at x1 is selection (is this ER >= 0.30 trade a good one?), not size; the size excess is bounded by the numbers above. A rule that reduced only the PE 11-lot x1.5 cell would address the worst-30 list but is a one-book fit to three episodes (post hoc).
- The trade-level net is the 6 live books; the 11-book day series also holds the X1-X5 cells (not trade-resolved), so the day-series numbers differ by up to -30k in A.
