# DS3_SIZER_DRAWDOWN_ANATOMY_Q1A - where the drawdown sits under the live Q1-A ladder (BASE-4, 2026-11-03T15:59Z)

Base = ts2 (run_v13t_ts2: V13T_LIVE in the LIVE lot order session -> A06 slot -> B02 -> ER Q1-A (x1.0 if ER>=0.30 else x0.5) -> zone HALF last; lock R never scaled under Q1-A; lock none = per-book locks). Every trade of the 6 live books in the episode; ER = the ER(20) value at the signal; mult = the Q1-A multiplier (x1.0 / x0.5; zone half, slot, B02 flagged separately); lots = contracts traded (integer); "net at x1" = the same trade rescaled linearly to the lots with the ER ladder off (slot, B02, zone half applied, rounded): an approximation that keeps the same trades, the same exits and the same locks, so it is NOT the same as the ladder-OFF engine run, which is reported beside it. Exit type: stop / target / cut (TH-L2 loss cut) / lock (per-book week floor or day give-back flattened it) / flat (session flat). Table only, no recommendation.

## Summary (all three episodes)
net of the 6 live books summed from the trades; the 11-book day series also holds the X1-X5 cells (not trade-resolved), which is why it differs; ladder OFF = a separate engine run (same locks / cuts, lots x1, the trade set can differ); x1-rescaled = the same trades rescaled linearly.
| episode | label days | trades | trade net $ (live ladder) | 11-book day series $ | ladder OFF engine run $ | same trades at x1 $ | ER>=0.30 (x1.0) trades net | ER<0.30 (x0.5) trades net (at x1) | ER>=0.30 share of gross loss / of trades |
|---|---|---|---|---|---|---|---|---|---|
| Episode A | 20260720..20260911 | 1229 | -140,019 | -104,809 | -72,659 | -138,248 | -141,028 | 1,009 (x1: 2,780) | 63% / 37% |
| Episode B1 | 20250203..20250228 | 352 | -164,605 | -88,180 | -75,014 | -152,738 | -201,180 | 36,574 (x1: 48,441) | 77% / 46% |
| Episode B2 | 20240801..20250131 | 2485 | 428,721 | 345,777 | 407,304 | 530,636 | 319,208 | 109,512 (x1: 211,428) | 69% / 45% |


## Episode A: the 2026 drawdown, peak week 202630 -> trough week 202637 (weekly-cumulative maxDD of the F9/L6M window $104,809; the lead called it W28-W39)

1229 trades, 20260720..20260911. Net P&L of the episode at the live ladder: $-140,019 (day-series check $-104,809); weekly-cumulative maxDD inside it $104,809; the same period with the ladder OFF (separate engine run, lots x1): $-72,659; the SAME trades rescaled to x1 lots (size-neutral, linear in lots): $-138,248. Gross loss (sum of losing trades) $-1,522,971, gross win $1,382,952.

### By ER bucket / multiplier (the sizer question)
| bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| ER<0.30 (x0.5) | 772 | 1353 | 1,009 | -1% | -560,322 | 561,331 | 2,780 | -967,722 |
| ER>=0.30 (x1.0) | 457 | 1335 | -141,028 | 101% | -962,649 | 821,621 | -141,028 | -962,649 |

### By book
| book | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| HM | 159 | 341 | -19,805 | 14% | -179,183 | 159,377 | -9,857 | -246,939 |
| KB | 425 | 499 | -60,590 | 43% | -295,532 | 234,942 | -74,672 | -357,734 |
| MV | 196 | 245 | -40,162 | 29% | -144,785 | 104,623 | -44,464 | -179,934 |
| PB | 84 | 84 | 3,309 | -2% | -70,272 | 73,581 | 3,309 | -70,272 |
| PE | 264 | 1249 | -54,936 | 39% | -699,996 | 645,060 | -34,654 | -896,948 |
| SM | 101 | 270 | 32,164 | -23% | -133,205 | 165,369 | 22,089 | -178,545 |

### By session
| session | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| asia | 601 | 1472 | -21,831 | 16% | -810,813 | 788,982 | -11,979 | -1,048,511 |
| london | 430 | 1010 | -85,674 | 61% | -591,932 | 506,258 | -90,250 | -754,406 |
| nyam | 142 | 142 | -21,214 | 15% | -79,015 | 57,802 | -21,214 | -79,015 |
| nypm | 56 | 64 | -11,301 | 8% | -41,211 | 29,910 | -14,805 | -48,439 |

### By lots bucket
| lots bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| 1 | 629 | 629 | -32,404 | 23% | -356,322 | 323,918 | -49,778 | -462,360 |
| 2-3 | 295 | 590 | -96,778 | 69% | -344,043 | 247,265 | -99,992 | -478,242 |
| 4-6 | 222 | 888 | 50,282 | -36% | -416,264 | 466,545 | 72,642 | -583,427 |
| 7+ | 83 | 581 | -61,119 | 44% | -406,343 | 345,224 | -61,119 | -406,343 |

### By split add filled
| split add filled | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| False | 175 | 283 | 127,966 | -91% | -92,884 | 220,850 | 175,041 | -101,025 |
| True | 1054 | 2405 | -267,985 | 191% | -1,430,088 | 1,162,102 | -313,289 | -1,829,346 |

### By exit type
| exit type | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| cut | 735 | 1694 | -1,410,512 | 1007% | -1,441,197 | 30,685 | -1,804,890 | -1,846,757 |
| flat | 1 | 1 | -52 | 0% | -52 | 0 | -52 | -52 |
| lock | 45 | 50 | -15,589 | 11% | -16,780 | 1,191 | -16,172 | -17,363 |
| stop | 35 | 35 | -64,942 | 46% | -64,942 | 0 | -66,200 | -66,200 |
| target | 413 | 908 | 1,351,076 | -965% | 0 | 1,351,076 | 1,749,066 | 0 |

### By side (+1 long)
| side (+1 long) | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| -1.0 | 603 | 1346 | -74,936 | 54% | -778,881 | 703,945 | -65,960 | -978,340 |
| 1.0 | 626 | 1342 | -65,084 | 46% | -744,091 | 679,007 | -72,288 | -952,031 |

### Book x ER bucket (net $)
| book | ER<0.30 (x0.5) | ER>=0.30 (x1.0) |
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
| 20260806 | PE | asia | S | 0.47 | 7 | x1 | -10,258 | -10,258 | cut | add |  |
| 20260729 | PE | asia | S | 0.36 | 7 | x1 | -9,642 | -9,642 | cut | add |  |
| 20260720 | PE | asia | L | 0.30 | 7 | x1 | -9,199 | -9,199 | cut | add |  |
| 20260729 | PE | asia | S | 0.52 | 7 | x1 | -9,037 | -9,037 | cut | add |  |
| 20260730 | PE | london | L | 0.39 | 7 | x1 | -8,502 | -8,502 | cut | add |  |
| 20260730 | PE | asia | L | 0.39 | 7 | x1 | -8,409 | -8,409 | cut | add |  |
| 20260824 | PE | london | S | 0.52 | 7 | x1 | -8,080 | -8,080 | cut | add |  |
| 20260902 | PE | london | S | 0.39 | 4 | x1 | -8,080 | -8,080 | cut | add |  |
| 20260827 | PE | asia | L | 0.69 | 7 | x1 | -7,926 | -7,926 | cut | add |  |
| 20260904 | PE | asia | S | 0.37 | 7 | x1 | -7,849 | -7,849 | cut | add |  |
| 20260817 | PE | london | L | 0.49 | 7 | x1 | -7,796 | -7,796 | cut | add |  |
| 20260826 | PE | asia | L | 0.36 | 7 | x1 | -7,698 | -7,698 | cut | add |  |
| 20260909 | PE | london | S | 0.59 | 7 | x1 | -7,488 | -7,488 | cut | add |  |
| 20260729 | PE | asia | S | 0.44 | 7 | x1 | -7,481 | -7,481 | cut | add |  |
| 20260728 | PE | asia | S | 0.39 | 7 | x1 | -7,480 | -7,480 | cut | add |  |
| 20260731 | PE | asia | L | 0.54 | 7 | x1 | -7,433 | -7,433 | cut | add |  |
| 20260729 | PE | london | L | 0.47 | 7 | x1 | -7,424 | -7,424 | cut | add |  |
| 20260904 | PE | london | S | 0.40 | 7 | x1 | -7,368 | -7,368 | cut | add |  |
| 20260818 | PE | asia | S | 0.51 | 7 | x1 | -7,328 | -7,328 | cut | add |  |
| 20260831 | PE | london | L | 0.43 | 7 | x1 | -7,313 | -7,313 | cut | add |  |
| 20260903 | PE | asia | L | 0.33 | 7 | x1 | -7,185 | -7,185 | cut | add |  |
| 20260812 | PE | london | L | 0.43 | 7 | x1 | -7,181 | -7,181 | cut | add |  |
| 20260908 | PE | london | S | 0.46 | 7 | x1 | -7,168 | -7,168 | cut | add |  |
| 20260805 | PE | london | S | 0.49 | 7 | x1 | -7,165 | -7,165 | cut | add |  |
| 20260827 | PE | london | L | 0.43 | 7 | x1 | -7,095 | -7,095 | cut | add |  |
| 20260821 | PE | london | L | 0.39 | 4 | x1 | -7,085 | -7,085 | cut | add |  |
| 20260902 | PE | london | L | 0.37 | 7 | x1 | -7,073 | -7,073 | cut | add |  |
| 20260820 | PE | london | S | 0.43 | 7 | x1 | -7,047 | -7,047 | cut | add |  |
| 20260819 | PE | london | L | 0.51 | 7 | x1 | -7,034 | -7,034 | cut | add |  |
| 20260820 | PE | asia | L | 0.63 | 7 | x1 | -7,025 | -7,025 | cut | add |  |

### Worst 10 days
| label day | day net $ | trades | lots | day net at x1 $ | share of trades at x1.5 | mean ER |
|---|---|---|---|---|---|---|
| 20260720 | -53,219 | 47 | 100 | -60,755 | 0% | 0.22 |
| 20260730 | -43,085 | 54 | 127 | -41,580 | 0% | 0.25 |
| 20260806 | -38,770 | 37 | 72 | -47,866 | 0% | 0.20 |
| 20260819 | -38,263 | 31 | 71 | -40,310 | 0% | 0.25 |
| 20260907 | -26,865 | 15 | 37 | -33,178 | 0% | 0.27 |
| 20260828 | -26,714 | 14 | 34 | -29,325 | 0% | 0.32 |
| 20260903 | -25,426 | 30 | 69 | -29,606 | 0% | 0.32 |
| 20260803 | -22,812 | 36 | 66 | -36,215 | 0% | 0.22 |
| 20260904 | -22,359 | 21 | 53 | -16,850 | 0% | 0.25 |
| 20260902 | -21,565 | 21 | 51 | -22,525 | 0% | 0.22 |

### Size effect in one line
ER>=0.30 trades at x1.0 (457): net $-141,028; ER<0.30 trades at x0.5 (772): net $1,009 (at x1: $2,780, so the 0.5 multiplier moved $-1,771); share of the gross loss: ER>=0.30 63%, ER<0.30 37% (their share of trades 37% / 63%).

## Episode B1: the PRE drawdown, peak week 202506 -> trough week 202509 (maxDD $88,180)

352 trades, 20250203..20250228. Net P&L of the episode at the live ladder: $-164,605 (day-series check $-88,180); weekly-cumulative maxDD inside it $88,180; the same period with the ladder OFF (separate engine run, lots x1): $-75,014; the SAME trades rescaled to x1 lots (size-neutral, linear in lots): $-152,738. Gross loss (sum of losing trades) $-553,391, gross win $388,786.

### By ER bucket / multiplier (the sizer question)
| bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| ER<0.30 (x0.5) | 189 | 324 | 36,574 | -22% | -125,444 | 162,019 | 48,441 | -222,014 |
| ER>=0.30 (x1.0) | 163 | 499 | -201,180 | 122% | -427,947 | 226,767 | -201,180 | -427,947 |

### By book
| book | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| HM | 43 | 84 | -9,784 | 6% | -51,757 | 41,973 | -11,092 | -66,889 |
| KB | 122 | 144 | -17,712 | 11% | -83,621 | 65,909 | -17,532 | -98,694 |
| MV | 48 | 64 | -31,587 | 19% | -50,038 | 18,451 | -34,420 | -54,599 |
| PB | 18 | 18 | -3,007 | 2% | -16,489 | 13,482 | -3,007 | -16,489 |
| PE | 91 | 437 | -109,971 | 67% | -310,072 | 200,102 | -94,120 | -361,580 |
| SM | 30 | 76 | 7,456 | -5% | -41,413 | 48,869 | 7,433 | -51,710 |

### By session
| session | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| asia | 136 | 349 | 5,836 | -4% | -202,402 | 208,238 | 11,640 | -249,857 |
| london | 109 | 296 | -133,561 | 81% | -223,992 | 90,431 | -145,055 | -259,119 |
| nyam | 83 | 151 | -28,784 | 17% | -109,806 | 81,023 | -11,296 | -119,535 |
| nypm | 24 | 27 | -8,097 | 5% | -17,191 | 9,094 | -8,027 | -21,450 |

### By lots bucket
| lots bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| 1 | 174 | 174 | -6,727 | 4% | -100,393 | 93,665 | -10,029 | -126,630 |
| 2-3 | 84 | 168 | -46,434 | 28% | -112,789 | 66,355 | -45,569 | -145,519 |
| 4-6 | 59 | 236 | -17,030 | 10% | -143,084 | 126,054 | -2,726 | -180,686 |
| 7+ | 35 | 245 | -94,414 | 57% | -197,126 | 102,712 | -94,414 | -197,126 |

### By split add filled
| split add filled | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| False | 44 | 69 | 22,806 | -14% | -25,695 | 48,500 | 28,879 | -30,019 |
| True | 308 | 754 | -187,411 | 114% | -527,697 | 340,286 | -181,618 | -619,942 |

### By exit type
| exit type | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| cut | 202 | 500 | -479,404 | 291% | -481,131 | 1,728 | -570,312 | -573,767 |
| flat | 4 | 13 | -6,367 | 4% | -6,886 | 519 | -6,367 | -6,886 |
| lock | 15 | 29 | -10,900 | 7% | -11,345 | 446 | -11,064 | -11,509 |
| stop | 14 | 25 | -54,029 | 33% | -54,029 | 0 | -57,798 | -57,798 |
| target | 117 | 256 | 386,094 | -235% | 0 | 386,094 | 492,803 | 0 |

### By side (+1 long)
| side (+1 long) | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| -1.0 | 161 | 409 | -105,479 | 64% | -287,197 | 181,719 | -116,862 | -333,326 |
| 1.0 | 191 | 414 | -59,127 | 36% | -266,194 | 207,067 | -35,877 | -316,634 |

### Book x ER bucket (net $)
| book | ER<0.30 (x0.5) | ER>=0.30 (x1.0) |
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
| 20250224 | PE | nyam | S | 0.52 | 4 | x1 | -17,721 | -17,721 | stop | add |  |
| 20250227 | PE | nyam | S | 0.58 | 7 | x1 | -9,953 | -9,953 | stop | add |  |
| 20250204 | PE | nyam | L | 0.60 | 7 | x1 | -8,817 | -8,817 | cut | add |  |
| 20250218 | PE | london | L | 0.63 | 7 | x1 | -8,596 | -8,596 | cut | add |  |
| 20250205 | PE | london | S | 0.50 | 7 | x1 | -8,445 | -8,445 | cut | add |  |
| 20250224 | PE | asia | L | 0.40 | 7 | x1 | -8,248 | -8,248 | cut | add |  |
| 20250228 | PE | asia | S | 0.39 | 7 | x1 | -8,205 | -8,205 | cut | add |  |
| 20250210 | PE | asia | L | 0.55 | 7 | x1 | -8,117 | -8,117 | cut | add |  |
| 20250204 | PE | london | L | 0.36 | 7 | x1 | -8,087 | -8,087 | cut | add |  |
| 20250214 | PE | london | S | 0.43 | 7 | x1 | -7,961 | -7,961 | cut | add |  |
| 20250218 | PE | asia | S | 0.40 | 7 | x1 | -7,898 | -7,898 | cut | add |  |
| 20250204 | PE | asia | L | 0.40 | 7 | x1 | -7,815 | -7,815 | cut | add |  |
| 20250227 | PE | nyam | S | 0.43 | 7 | x1 | -7,507 | -7,507 | cut | add |  |
| 20250227 | PE | london | L | 0.55 | 7 | x1 | -7,353 | -7,353 | cut | add |  |
| 20250210 | PE | nyam | L | 0.38 | 7 | x1 | -7,340 | -7,340 | cut | add |  |
| 20250204 | PE | london | L | 0.31 | 7 | x1 | -7,305 | -7,305 | cut | add |  |
| 20250228 | PE | london | L | 0.36 | 4 | x1 | -7,216 | -7,216 | cut | add |  |
| 20250224 | PE | london | S | 0.48 | 7 | x1 | -6,967 | -6,967 | cut | add |  |
| 20250211 | PE | london | S | 0.49 | 7 | x1 | -6,961 | -6,961 | cut | add |  |
| 20250213 | PE | london | S | 0.40 | 7 | x1 | -6,922 | -6,922 | cut | add |  |
| 20250213 | PE | nyam | L | 0.34 | 7 | x1 | -6,917 | -6,917 | cut | add |  |
| 20250206 | PE | london | S | 0.41 | 7 | x1 | -6,914 | -6,914 | cut | add |  |
| 20250218 | PE | nyam | S | 0.45 | 4 | x1 | -6,874 | -6,874 | cut | add |  |
| 20250213 | PE | london | S | 0.60 | 4 | x1 | -6,866 | -6,866 | cut | add |  |
| 20250225 | PE | london | L | 0.46 | 7 | x1 | -6,835 | -6,835 | lock | add |  |
| 20250213 | PE | asia | L | 0.35 | 7 | x1 | -6,758 | -6,758 | cut | add |  |
| 20250203 | PE | london | L | 0.39 | 4 | x1 | -6,701 | -6,701 | cut | add |  |
| 20250204 | PE | asia | S | 0.35 | 7 | x1 | -6,683 | -6,683 | cut | add |  |
| 20250227 | PE | asia | L | 0.37 | 7 | x1 | -6,329 | -6,329 | cut | add |  |
| 20250203 | PE | asia | S | 0.52 | 7 | x1 | -6,130 | -6,130 | cut | add |  |

### Worst 10 days
| label day | day net $ | trades | lots | day net at x1 $ | share of trades at x1.5 | mean ER |
|---|---|---|---|---|---|---|
| 20250224 | -44,148 | 22 | 51 | -47,335 | 0% | 0.32 |
| 20250204 | -36,170 | 26 | 85 | -32,092 | 0% | 0.30 |
| 20250228 | -36,051 | 25 | 59 | -41,414 | 0% | 0.24 |
| 20250218 | -21,656 | 18 | 43 | -18,849 | 0% | 0.34 |
| 20250205 | -17,800 | 21 | 42 | -17,835 | 0% | 0.28 |
| 20250206 | -16,747 | 9 | 24 | -15,610 | 0% | 0.37 |
| 20250219 | -13,512 | 14 | 21 | -20,517 | 0% | 0.30 |
| 20250213 | -12,981 | 30 | 77 | -9,621 | 0% | 0.34 |
| 20250212 | -9,986 | 14 | 18 | -15,207 | 0% | 0.32 |
| 20250227 | -6,274 | 22 | 72 | -6,971 | 0% | 0.31 |

### Size effect in one line
ER>=0.30 trades at x1.0 (163): net $-201,180; ER<0.30 trades at x0.5 (189): net $36,574 (at x1: $48,441, so the 0.5 multiplier moved $-11,867); share of the gross loss: ER>=0.30 77%, ER<0.30 23% (their share of trades 46% / 54%).

## Episode B2: 2024-08-01..2025-01-31 (PRE middle third, as ordered; contains the carrying weeks 202434-202451)

2485 trades, 20240801..20250131. Net P&L of the episode at the live ladder: $428,721 (day-series check $345,777); weekly-cumulative maxDD inside it $73,959; the same period with the ladder OFF (separate engine run, lots x1): $407,304; the SAME trades rescaled to x1 lots (size-neutral, linear in lots): $530,636. Gross loss (sum of losing trades) $-3,267,833, gross win $3,696,554.

### By ER bucket / multiplier (the sizer question)
| bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| ER<0.30 (x0.5) | 1359 | 2347 | 109,512 | 26% | -1,003,056 | 1,112,569 | 211,428 | -1,676,500 |
| ER>=0.30 (x1.0) | 1126 | 3373 | 319,208 | 74% | -2,264,777 | 2,583,985 | 319,208 | -2,264,777 |

### By book
| book | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| HM | 344 | 653 | 33,339 | 8% | -360,717 | 394,056 | 16,271 | -475,753 |
| KB | 787 | 922 | 60,269 | 14% | -505,133 | 565,402 | 63,852 | -583,431 |
| MV | 414 | 506 | 55,460 | 13% | -262,648 | 318,108 | 63,797 | -284,071 |
| PB | 121 | 121 | 43,580 | 10% | -87,456 | 131,036 | 43,580 | -87,456 |
| PE | 628 | 3015 | 158,373 | 37% | -1,769,708 | 1,928,082 | 212,477 | -2,191,032 |
| SM | 191 | 503 | 77,699 | 18% | -282,171 | 359,870 | 130,661 | -319,534 |

### By session
| session | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| asia | 985 | 2591 | 305,260 | 71% | -1,416,767 | 1,722,027 | 373,157 | -1,734,573 |
| london | 652 | 1678 | -18,731 | -4% | -1,054,276 | 1,035,545 | 29,732 | -1,245,832 |
| nyam | 694 | 1267 | 155,433 | 36% | -689,244 | 844,678 | 133,822 | -836,845 |
| nypm | 154 | 184 | -13,241 | -3% | -107,546 | 94,305 | -6,075 | -124,027 |

### By lots bucket
| lots bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| 1 | 1290 | 1290 | 128,145 | 30% | -693,070 | 821,215 | 137,693 | -835,419 |
| 2-3 | 520 | 1040 | 108,376 | 25% | -576,331 | 684,708 | 192,715 | -781,148 |
| 4-6 | 445 | 1780 | 120,218 | 28% | -946,612 | 1,066,830 | 128,245 | -1,272,890 |
| 7+ | 230 | 1610 | 71,982 | 17% | -1,051,820 | 1,123,802 | 71,982 | -1,051,820 |

### By split add filled
| split add filled | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| False | 316 | 577 | 323,329 | 75% | -174,881 | 498,210 | 378,987 | -193,290 |
| True | 2169 | 5143 | 105,392 | 25% | -3,092,952 | 3,198,344 | 151,649 | -3,747,987 |

### By exit type
| exit type | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| cut | 1341 | 3203 | -2,870,180 | -669% | -2,970,541 | 100,361 | -3,476,177 | -3,593,564 |
| flat | 13 | 26 | 6,290 | 1% | -2,734 | 9,023 | 7,477 | -2,897 |
| lock | 88 | 128 | -55,212 | -13% | -57,320 | 2,109 | -58,505 | -60,614 |
| stop | 76 | 149 | -237,238 | -55% | -237,238 | 0 | -284,201 | -284,201 |
| target | 967 | 2214 | 3,585,061 | 836% | 0 | 3,585,061 | 4,342,044 | 0 |

### By side (+1 long)
| side (+1 long) | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| -1.0 | 1177 | 2758 | 170,788 | 40% | -1,607,715 | 1,778,502 | 144,962 | -1,993,456 |
| 1.0 | 1308 | 2962 | 257,933 | 60% | -1,660,119 | 1,918,052 | 385,674 | -1,947,820 |

### Book x ER bucket (net $)
| book | ER<0.30 (x0.5) | ER>=0.30 (x1.0) |
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
| 20241220 | PE | nyam | L | 0.59 | 7 | x1 | -16,848 | -16,848 | lock | add |  |
| 20240909 | PE | nyam | L | 0.39 | 7 | x1 | -16,011 | -16,011 | stop | add |  |
| 20241206 | PE | nyam | L | 0.47 | 7 | x1 | -14,240 | -14,240 | cut | add |  |
| 20240813 | PE | nyam | L | 0.55 | 7 | x1 | -13,807 | -13,807 | cut | add |  |
| 20240924 | PE | nyam | S | 0.48 | 7 | x1 | -13,774 | -13,774 | stop | no add |  |
| 20240905 | PE | nyam | L | 0.49 | 7 | x1 | -11,194 | -11,194 | cut | add |  |
| 20250120 | PE | london | S | 0.33 | 7 | x1 | -10,688 | -10,688 | cut | add |  |
| 20240906 | PE | london | L | 0.39 | 7 | x1 | -9,655 | -9,655 | stop | no add |  |
| 20241008 | PE | asia | S | 0.32 | 7 | x1 | -9,611 | -9,611 | cut | add |  |
| 20240913 | PE | asia | L | 0.51 | 7 | x1 | -9,428 | -9,428 | cut | add |  |
| 20241014 | PE | nyam | L | 0.70 | 7 | x1 | -9,413 | -9,413 | stop | add |  |
| 20250106 | PE | london | L | 0.44 | 7 | x1 | -9,367 | -9,367 | cut | add |  |
| 20241007 | PE | london | S | 0.32 | 4 | x1 | -8,925 | -8,925 | cut | add |  |
| 20241120 | PE | nyam | S | 0.79 | 4 | x1 | -8,843 | -8,843 | stop | add |  |
| 20240802 | PE | asia | S | 0.34 | 7 | x1 | -8,842 | -8,842 | cut | add |  |
| 20240812 | PE | asia | L | 0.38 | 7 | x1 | -8,820 | -8,820 | cut | add |  |
| 20250128 | PE | asia | L | 0.58 | 7 | x1 | -8,670 | -8,670 | cut | add |  |
| 20240823 | PE | asia | S | 0.36 | 7 | x1 | -8,583 | -8,583 | cut | add |  |
| 20240815 | PE | asia | L | 0.48 | 7 | x1 | -8,563 | -8,563 | cut | add |  |
| 20241018 | PE | asia | S | 0.37 | 7 | x1 | -8,540 | -8,540 | cut | add |  |
| 20250130 | PE | london | L | 0.57 | 4 | x1 | -8,429 | -8,429 | cut | add |  |
| 20240822 | PE | asia | L | 0.39 | 7 | x1 | -8,360 | -8,360 | cut | add |  |
| 20240827 | PE | london | S | 0.40 | 7 | x1 | -8,342 | -8,342 | cut | add |  |
| 20241126 | PE | asia | L | 0.57 | 7 | x1 | -8,317 | -8,317 | cut | add |  |
| 20241105 | PE | london | L | 0.40 | 7 | x1 | -8,284 | -8,284 | cut | add |  |
| 20240919 | PE | asia | S | 0.37 | 7 | x1 | -8,234 | -8,234 | cut | add |  |
| 20240807 | PE | asia | S | 0.47 | 7 | x1 | -8,227 | -8,227 | cut | add |  |
| 20250108 | PE | london | L | 0.39 | 7 | x1 | -8,185 | -8,185 | cut | add |  |
| 20240925 | PE | nyam | L | 0.64 | 4 | x1 | -8,182 | -8,182 | cut | add |  |
| 20250114 | PE | london | L | 0.38 | 4 | x1 | -8,171 | -8,171 | cut | add |  |

### Worst 10 days
| label day | day net $ | trades | lots | day net at x1 $ | share of trades at x1.5 | mean ER |
|---|---|---|---|---|---|---|
| 20240905 | -56,662 | 27 | 71 | -61,306 | 0% | 0.26 |
| 20250128 | -47,507 | 23 | 59 | -58,702 | 0% | 0.29 |
| 20250120 | -44,361 | 13 | 39 | -48,281 | 0% | 0.33 |
| 20240930 | -40,248 | 22 | 55 | -48,703 | 0% | 0.32 |
| 20240906 | -38,202 | 26 | 63 | -33,639 | 0% | 0.34 |
| 20250108 | -37,511 | 20 | 53 | -44,757 | 0% | 0.26 |
| 20241231 | -37,274 | 21 | 52 | -38,070 | 0% | 0.33 |
| 20241002 | -33,599 | 23 | 57 | -36,436 | 0% | 0.26 |
| 20241122 | -32,324 | 22 | 42 | -37,169 | 0% | 0.30 |
| 20241113 | -28,397 | 13 | 36 | -27,297 | 0% | 0.28 |

### Size effect in one line
ER>=0.30 trades at x1.0 (1126): net $319,208; ER<0.30 trades at x0.5 (1359): net $109,512 (at x1: $211,428, so the 0.5 multiplier moved $-101,916); share of the gross loss: ER>=0.30 69%, ER<0.30 31% (their share of trades 45% / 55%).
