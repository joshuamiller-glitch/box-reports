# DS3_SIZER_DRAWDOWN_ANATOMY_Q1A - where the drawdown sits under the live Q1-A ladder (BASE-4, 2026-11-03T16:01Z)

Base = ts2 (run_v13t_ts2: V13T_LIVE in the LIVE lot order session -> A06 slot -> B02 -> ER Q1-A (x1.0 if ER>=0.30 else x0.5) -> zone HALF last; lock R never scaled under Q1-A; lock none = per-book locks). Every trade of the 6 live books in the episode; ER = the ER(20) value at the signal; mult = the Q1-A multiplier (x1.0 / x0.5; zone half, slot, B02 flagged separately); lots = contracts traded (integer); "net at x1" = the same trade rescaled linearly to the lots with the ER ladder off (slot, B02, zone half applied, rounded): an approximation that keeps the same trades, the same exits and the same locks, so it is NOT the same as the ladder-OFF engine run, which is reported beside it. Exit type: stop / target / cut (TH-L2 loss cut) / lock (per-book week floor or day give-back flattened it) / flat (session flat). Table only, no recommendation.

## Summary (all three episodes)
net of the 6 live books summed from the trades; the 11-book day series also holds the X1-X5 cells (not trade-resolved), which is why it differs; ladder OFF = a separate engine run (same locks / cuts, lots x1, the trade set can differ); x1-rescaled = the same trades rescaled linearly.
| episode | label days | trades | trade net $ (live ladder) | 11-book day series $ | ladder OFF engine run $ | same trades at x1 $ | ER>=0.30 (x1.0) trades net | ER<0.30 (x0.5) trades net (at x1) | ER>=0.30 share of gross loss / of trades |
|---|---|---|---|---|---|---|---|---|---|
| Episode A | 20260720..20260911 | 1484 | -104,809 | -104,809 | -72,659 | -97,080 | -105,361 | 552 (x1: 8,281) | 50% / 36% |
| Episode B1 | 20250203..20250228 | 441 | -88,180 | -88,180 | -75,014 | -83,029 | -107,636 | 19,456 (x1: 24,607) | 63% / 45% |
| Episode B2 | 20240801..20250131 | 2878 | 345,777 | 345,777 | 407,304 | 445,685 | 186,426 | 159,351 (x1: 259,260) | 57% / 43% |


## Episode A: the 2026 drawdown, peak week 202630 -> trough week 202637 (weekly-cumulative maxDD of the F9/L6M window $104,809; the lead called it W28-W39)

1484 trades, 20260720..20260911. Net P&L of the episode at the live ladder: $-104,809 (day-series check $-104,809); weekly-cumulative maxDD inside it $104,809; the same period with the ladder OFF (separate engine run, lots x1): $-72,659; the SAME trades rescaled to x1 lots (size-neutral, linear in lots): $-97,080. Gross loss (sum of losing trades) $-1,323,579, gross win $1,218,771.

### By ER bucket / multiplier (the sizer question)
| bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| ER<0.30 (x0.5) | 948 | 1591 | 552 | -1% | -664,592 | 665,144 | 8,281 | -1,096,038 |
| ER>=0.30 (x1.0) | 536 | 1473 | -105,361 | 101% | -658,988 | 553,627 | -105,361 | -658,988 |

### By book
| book | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| HM | 229 | 425 | -17,277 | 16% | -181,757 | 164,480 | -7,799 | -252,491 |
| KB | 515 | 591 | -51,642 | 49% | -260,583 | 208,942 | -69,649 | -327,965 |
| MV | 257 | 306 | -24,945 | 24% | -136,117 | 111,172 | -28,566 | -170,585 |
| PB | 89 | 89 | -7,704 | 7% | -57,557 | 49,853 | -7,704 | -57,557 |
| PE | 293 | 1383 | -22,956 | 22% | -584,876 | 561,920 | 6,998 | -798,399 |
| SM | 101 | 270 | 19,715 | -19% | -102,689 | 122,404 | 9,640 | -148,029 |

### By session
| session | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| asia | 637 | 1598 | -22,707 | 22% | -686,477 | 663,770 | -11,136 | -946,201 |
| london | 446 | 1056 | -60,081 | 57% | -458,021 | 397,940 | -60,004 | -620,874 |
| nyam | 333 | 333 | -10,873 | 10% | -143,633 | 132,760 | -10,873 | -143,633 |
| nypm | 68 | 77 | -11,148 | 11% | -35,448 | 24,301 | -15,066 | -44,318 |

### By lots bucket
| lots bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| 1 | 845 | 845 | -40,636 | 39% | -382,254 | 341,618 | -59,397 | -490,933 |
| 2-3 | 305 | 610 | -57,155 | 55% | -269,694 | 212,539 | -57,910 | -403,150 |
| 4-6 | 243 | 972 | 41,733 | -40% | -386,330 | 428,063 | 68,978 | -575,642 |
| 7+ | 91 | 637 | -48,750 | 47% | -285,301 | 236,550 | -48,750 | -285,301 |

### By split add filled
| split add filled | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| False | 208 | 327 | 108,391 | -103% | -80,564 | 188,955 | 159,403 | -91,461 |
| True | 1276 | 2737 | -213,199 | 203% | -1,243,015 | 1,029,816 | -256,483 | -1,663,565 |

### By exit type
| exit type | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| cut | 914 | 1943 | -1,224,348 | 1168% | -1,251,472 | 27,125 | -1,638,131 | -1,676,437 |
| flat | 1 | 1 | -52 | 0% | -52 | 0 | -52 | -52 |
| lock | 9 | 22 | -10,795 | 10% | -10,795 | 0 | -12,205 | -12,205 |
| stop | 46 | 49 | -61,259 | 58% | -61,259 | 0 | -66,332 | -66,332 |
| target | 514 | 1049 | 1,191,646 | -1137% | 0 | 1,191,646 | 1,619,640 | 0 |

### By side (+1 long)
| side (+1 long) | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| -1.0 | 734 | 1541 | -86,697 | 83% | -686,569 | 599,872 | -75,776 | -902,445 |
| 1.0 | 750 | 1523 | -18,111 | 17% | -637,010 | 618,899 | -21,303 | -852,581 |

### Book x ER bucket (net $)
| book | ER<0.30 (x0.5) | ER>=0.30 (x1.0) |
|---|---|---|
| HM | 6,272 | -23,549 |
| KB | -19,569 | -32,073 |
| MV | -12,733 | -12,212 |
| PB | -3,587 | -4,117 |
| PE | 39,036 | -61,992 |
| SM | -8,866 | 28,581 |

### Worst 30 trades
| label day | book | session | side | ER(20) | lots | mult | net $ | net at x1 $ | exit | entry | zone |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 20260724 | PE | london | S | 0.44 | 7 | x1 | -8,239 | -8,239 | cut | add |  |
| 20260806 | PE | asia | S | 0.47 | 7 | x1 | -6,528 | -6,528 | cut | add |  |
| 20260729 | PE | asia | S | 0.36 | 7 | x1 | -6,136 | -6,136 | cut | add |  |
| 20260720 | PE | asia | L | 0.30 | 7 | x1 | -5,854 | -5,854 | cut | add |  |
| 20260729 | PE | asia | S | 0.52 | 7 | x1 | -5,751 | -5,751 | cut | add |  |
| 20260730 | PE | london | L | 0.39 | 7 | x1 | -5,410 | -5,410 | cut | add |  |
| 20260730 | PE | asia | L | 0.39 | 7 | x1 | -5,351 | -5,351 | cut | add |  |
| 20260824 | PE | london | S | 0.52 | 7 | x1 | -5,142 | -5,142 | cut | add |  |
| 20260911 | PE | london | L | 0.08 | 4 | x0.5 | -5,086 | -8,901 | stop | add |  |
| 20260827 | PE | asia | L | 0.69 | 7 | x1 | -5,044 | -5,044 | cut | add |  |
| 20260904 | PE | asia | S | 0.37 | 7 | x1 | -4,995 | -4,995 | cut | add |  |
| 20260817 | PE | london | L | 0.49 | 7 | x1 | -4,961 | -4,961 | cut | add |  |
| 20260826 | PE | asia | L | 0.36 | 7 | x1 | -4,899 | -4,899 | cut | add |  |
| 20260909 | PE | london | S | 0.59 | 7 | x1 | -4,765 | -4,765 | cut | add |  |
| 20260729 | PE | asia | S | 0.44 | 7 | x1 | -4,761 | -4,761 | cut | add |  |
| 20260728 | PE | asia | S | 0.39 | 7 | x1 | -4,760 | -4,760 | cut | add |  |
| 20260731 | PE | asia | L | 0.54 | 7 | x1 | -4,730 | -4,730 | cut | add |  |
| 20260729 | PE | london | L | 0.47 | 7 | x1 | -4,725 | -4,725 | cut | add |  |
| 20260904 | PE | london | S | 0.40 | 7 | x1 | -4,689 | -4,689 | cut | add |  |
| 20260818 | PE | asia | S | 0.51 | 7 | x1 | -4,664 | -4,664 | cut | add |  |
| 20260831 | PE | london | L | 0.43 | 7 | x1 | -4,654 | -4,654 | cut | add |  |
| 20260723 | PE | asia | S | 0.57 | 7 | x1 | -4,618 | -4,618 | cut | add |  |
| 20260903 | PE | asia | L | 0.33 | 7 | x1 | -4,572 | -4,572 | cut | add |  |
| 20260812 | PE | london | L | 0.43 | 7 | x1 | -4,570 | -4,570 | cut | add |  |
| 20260805 | PE | london | S | 0.49 | 7 | x1 | -4,559 | -4,559 | cut | add |  |
| 20260827 | PE | london | L | 0.43 | 7 | x1 | -4,515 | -4,515 | cut | add |  |
| 20260724 | PE | london | L | 0.42 | 7 | x1 | -4,501 | -4,501 | cut | add |  |
| 20260902 | PE | london | L | 0.37 | 7 | x1 | -4,501 | -4,501 | cut | add |  |
| 20260820 | PE | london | S | 0.43 | 7 | x1 | -4,485 | -4,485 | cut | add |  |
| 20260819 | PE | london | L | 0.51 | 7 | x1 | -4,476 | -4,476 | cut | add |  |

### Worst 10 days
| label day | day net $ | trades | lots | day net at x1 $ | share of trades at x1.5 | mean ER |
|---|---|---|---|---|---|---|
| 20260720 | -36,582 | 53 | 106 | -44,322 | 0% | 0.21 |
| 20260806 | -35,625 | 47 | 91 | -43,727 | 0% | 0.22 |
| 20260819 | -29,081 | 42 | 82 | -31,163 | 0% | 0.25 |
| 20260728 | -26,091 | 53 | 114 | -38,142 | 0% | 0.23 |
| 20260903 | -22,495 | 34 | 73 | -26,675 | 0% | 0.33 |
| 20260907 | -20,546 | 16 | 38 | -26,860 | 0% | 0.28 |
| 20260803 | -19,605 | 43 | 73 | -31,238 | 0% | 0.21 |
| 20260828 | -18,602 | 24 | 44 | -21,213 | 0% | 0.25 |
| 20260814 | -15,626 | 19 | 35 | -24,256 | 0% | 0.27 |
| 20260904 | -15,120 | 26 | 58 | -12,033 | 0% | 0.23 |

### Size effect in one line
ER>=0.30 trades at x1.0 (536): net $-105,361; ER<0.30 trades at x0.5 (948): net $552 (at x1: $8,281, so the 0.5 multiplier moved $-7,729); share of the gross loss: ER>=0.30 50%, ER<0.30 50% (their share of trades 36% / 64%).

## Episode B1: the PRE drawdown, peak week 202506 -> trough week 202509 (maxDD $88,180)

441 trades, 20250203..20250228. Net P&L of the episode at the live ladder: $-88,180 (day-series check $-88,180); weekly-cumulative maxDD inside it $88,180; the same period with the ladder OFF (separate engine run, lots x1): $-75,014; the SAME trades rescaled to x1 lots (size-neutral, linear in lots): $-83,029. Gross loss (sum of losing trades) $-441,692, gross win $353,512.

### By ER bucket / multiplier (the sizer question)
| bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| ER<0.30 (x0.5) | 244 | 396 | 19,456 | -22% | -162,026 | 181,482 | 24,607 | -267,836 |
| ER>=0.30 (x1.0) | 197 | 554 | -107,636 | 122% | -279,667 | 172,030 | -107,636 | -279,667 |

### By book
| book | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| HM | 60 | 102 | -3,218 | 4% | -44,080 | 40,862 | -5,878 | -59,770 |
| KB | 150 | 175 | -11,961 | 14% | -76,158 | 64,197 | -13,880 | -90,826 |
| MV | 79 | 95 | -20,366 | 23% | -49,196 | 28,831 | -24,303 | -56,091 |
| PB | 19 | 19 | 1,826 | -2% | -10,125 | 11,952 | 1,826 | -10,125 |
| PE | 103 | 483 | -56,416 | 64% | -231,092 | 174,676 | -41,509 | -289,354 |
| SM | 30 | 76 | 1,954 | -2% | -31,041 | 32,995 | 715 | -41,337 |

### By session
| session | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| asia | 147 | 373 | 4,013 | -5% | -162,453 | 166,466 | 6,287 | -217,514 |
| london | 117 | 309 | -94,223 | 107% | -163,009 | 68,785 | -107,416 | -199,847 |
| nyam | 149 | 236 | 5,965 | -7% | -101,881 | 107,846 | 22,664 | -113,338 |
| nypm | 28 | 32 | -3,935 | 4% | -14,350 | 10,415 | -4,564 | -16,804 |

### By lots bucket
| lots bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| 1 | 247 | 247 | 3,293 | -4% | -105,499 | 108,793 | -3,638 | -132,080 |
| 2-3 | 92 | 184 | -26,617 | 30% | -88,512 | 61,895 | -20,951 | -122,252 |
| 4-6 | 65 | 260 | -6,235 | 7% | -115,037 | 108,803 | 182 | -160,526 |
| 7+ | 37 | 259 | -58,623 | 66% | -132,644 | 74,021 | -58,623 | -132,644 |

### By split add filled
| split add filled | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| False | 50 | 75 | 22,669 | -26% | -17,966 | 40,635 | 28,743 | -22,290 |
| True | 391 | 875 | -110,850 | 126% | -423,726 | 312,877 | -111,772 | -525,212 |

### By exit type
| exit type | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| cut | 271 | 603 | -396,203 | 449% | -401,875 | 5,672 | -495,038 | -502,438 |
| flat | 4 | 13 | -3,855 | 4% | -4,201 | 346 | -3,855 | -4,201 |
| lock | 1 | 7 | -3,789 | 4% | -3,789 | 0 | -3,789 | -3,789 |
| stop | 15 | 27 | -31,827 | 36% | -31,827 | 0 | -37,075 | -37,075 |
| target | 150 | 300 | 347,494 | -394% | 0 | 347,494 | 456,728 | 0 |

### By side (+1 long)
| side (+1 long) | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| -1.0 | 210 | 482 | -56,750 | 64% | -228,072 | 171,322 | -68,313 | -279,018 |
| 1.0 | 231 | 468 | -31,430 | 36% | -213,621 | 182,190 | -14,716 | -268,484 |

### Book x ER bucket (net $)
| book | ER<0.30 (x0.5) | ER>=0.30 (x1.0) |
|---|---|---|
| HM | -3,013 | -205 |
| KB | 3,632 | -15,593 |
| MV | -4,141 | -16,225 |
| PB | 7,171 | -5,345 |
| PE | 17,046 | -73,462 |
| SM | -1,239 | 3,193 |

### Worst 30 trades
| label day | book | session | side | ER(20) | lots | mult | net $ | net at x1 $ | exit | entry | zone |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 20250224 | PE | nyam | S | 0.52 | 4 | x1 | -6,444 | -6,444 | stop | add |  |
| 20250227 | PE | nyam | S | 0.58 | 7 | x1 | -6,334 | -6,334 | stop | add |  |
| 20250204 | PE | nyam | L | 0.60 | 7 | x1 | -5,611 | -5,611 | cut | add |  |
| 20250218 | PE | london | L | 0.63 | 7 | x1 | -5,470 | -5,470 | cut | add |  |
| 20250205 | PE | london | S | 0.50 | 7 | x1 | -5,374 | -5,374 | cut | add |  |
| 20250224 | PE | asia | L | 0.40 | 7 | x1 | -5,249 | -5,249 | cut | add |  |
| 20250228 | PE | asia | S | 0.39 | 7 | x1 | -5,222 | -5,222 | cut | add |  |
| 20250210 | PE | asia | L | 0.55 | 7 | x1 | -5,165 | -5,165 | cut | add |  |
| 20250204 | PE | london | L | 0.36 | 7 | x1 | -5,146 | -5,146 | cut | add |  |
| 20250214 | PE | london | S | 0.43 | 7 | x1 | -5,066 | -5,066 | cut | add |  |
| 20250218 | PE | asia | S | 0.40 | 7 | x1 | -5,026 | -5,026 | cut | add |  |
| 20250204 | PE | asia | L | 0.40 | 7 | x1 | -4,973 | -4,973 | cut | add |  |
| 20250227 | PE | nyam | S | 0.43 | 7 | x1 | -4,777 | -4,777 | cut | add |  |
| 20250221 | PE | nyam | S | 0.66 | 7 | x1 | -4,698 | -4,698 | cut | add |  |
| 20250227 | PE | london | L | 0.55 | 7 | x1 | -4,679 | -4,679 | cut | add |  |
| 20250210 | PE | nyam | L | 0.38 | 7 | x1 | -4,671 | -4,671 | cut | add |  |
| 20250203 | PE | london | S | 0.34 | 7 | x1 | -4,658 | -4,658 | cut | add |  |
| 20250204 | PE | london | L | 0.31 | 7 | x1 | -4,648 | -4,648 | cut | add |  |
| 20250224 | PE | london | S | 0.48 | 7 | x1 | -4,434 | -4,434 | cut | add |  |
| 20250211 | PE | london | S | 0.49 | 7 | x1 | -4,430 | -4,430 | cut | add |  |
| 20250213 | PE | london | S | 0.40 | 7 | x1 | -4,405 | -4,405 | cut | add |  |
| 20250213 | PE | nyam | L | 0.34 | 7 | x1 | -4,402 | -4,402 | cut | add |  |
| 20250206 | PE | london | S | 0.41 | 7 | x1 | -4,400 | -4,400 | cut | add |  |
| 20250213 | PE | asia | L | 0.35 | 7 | x1 | -4,300 | -4,300 | cut | add |  |
| 20250204 | PE | asia | S | 0.35 | 7 | x1 | -4,253 | -4,253 | cut | add |  |
| 20250227 | PE | asia | L | 0.37 | 7 | x1 | -4,027 | -4,027 | cut | add |  |
| 20250203 | PE | asia | S | 0.52 | 7 | x1 | -3,901 | -3,901 | cut | add |  |
| 20250225 | PE | london | L | 0.46 | 7 | x1 | -3,789 | -3,789 | lock | add |  |
| 20250224 | PE | asia | S | 0.24 | 4 | x0.5 | -3,688 | -6,454 | cut | add |  |
| 20250217 | PE | nyam | S | 0.55 | 7 | x1 | -3,536 | -3,536 | flat | add |  |

### Worst 10 days
| label day | day net $ | trades | lots | day net at x1 $ | share of trades at x1.5 | mean ER |
|---|---|---|---|---|---|---|
| 20250228 | -27,024 | 34 | 67 | -33,867 | 0% | 0.21 |
| 20250224 | -22,343 | 25 | 54 | -25,530 | 0% | 0.34 |
| 20250204 | -20,829 | 28 | 87 | -16,138 | 0% | 0.34 |
| 20250206 | -18,240 | 16 | 33 | -18,371 | 0% | 0.32 |
| 20250218 | -13,950 | 19 | 44 | -13,902 | 0% | 0.34 |
| 20250205 | -9,224 | 22 | 43 | -9,258 | 0% | 0.27 |
| 20250219 | -8,583 | 14 | 21 | -13,188 | 0% | 0.30 |
| 20250212 | -5,656 | 17 | 21 | -10,877 | 0% | 0.30 |
| 20250207 | -4,937 | 25 | 39 | -1,339 | 0% | 0.25 |
| 20250227 | -3,993 | 30 | 80 | -6,970 | 0% | 0.28 |

### Size effect in one line
ER>=0.30 trades at x1.0 (197): net $-107,636; ER<0.30 trades at x0.5 (244): net $19,456 (at x1: $24,607, so the 0.5 multiplier moved $-5,151); share of the gross loss: ER>=0.30 63%, ER<0.30 37% (their share of trades 45% / 55%).

## Episode B2: 2024-08-01..2025-01-31 (PRE middle third, as ordered; contains the carrying weeks 202434-202451)

2878 trades, 20240801..20250131. Net P&L of the episode at the live ladder: $345,777 (day-series check $345,777); weekly-cumulative maxDD inside it $73,959; the same period with the ladder OFF (separate engine run, lots x1): $407,304; the SAME trades rescaled to x1 lots (size-neutral, linear in lots): $445,685. Gross loss (sum of losing trades) $-2,501,604, gross win $2,847,380.

### By ER bucket / multiplier (the sizer question)
| bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| ER<0.30 (x0.5) | 1653 | 2629 | 159,351 | 46% | -1,077,375 | 1,236,726 | 259,260 | -1,712,488 |
| ER>=0.30 (x1.0) | 1225 | 3493 | 186,426 | 54% | -1,424,229 | 1,610,654 | 186,426 | -1,424,229 |

### By book
| book | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| HM | 458 | 770 | 29,870 | 9% | -316,650 | 346,521 | 19,518 | -423,758 |
| KB | 1004 | 1153 | 85,779 | 25% | -448,061 | 533,840 | 96,089 | -532,927 |
| MV | 468 | 560 | 35,777 | 10% | -222,835 | 258,612 | 44,114 | -244,257 |
| PB | 132 | 132 | 33,044 | 10% | -63,390 | 96,434 | 33,044 | -63,390 |
| PE | 625 | 3004 | 95,118 | 28% | -1,257,092 | 1,352,209 | 138,949 | -1,642,081 |
| SM | 191 | 503 | 66,189 | 19% | -193,575 | 259,764 | 113,972 | -230,304 |

### By session
| session | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| asia | 1010 | 2622 | 245,766 | 71% | -1,053,301 | 1,299,068 | 320,967 | -1,365,035 |
| london | 658 | 1665 | -13,975 | -4% | -714,900 | 700,925 | 15,760 | -892,280 |
| nyam | 1009 | 1595 | 116,692 | 34% | -637,061 | 753,752 | 101,577 | -762,951 |
| nypm | 201 | 240 | -2,706 | -1% | -96,341 | 93,635 | 7,381 | -116,451 |

### By lots bucket
| lots bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| 1 | 1669 | 1669 | 146,231 | 42% | -663,475 | 809,707 | 166,866 | -798,953 |
| 2-3 | 538 | 1076 | 79,604 | 23% | -432,372 | 511,976 | 143,312 | -614,378 |
| 4-6 | 440 | 1760 | 71,976 | 21% | -738,576 | 810,551 | 87,541 | -1,056,206 |
| 7+ | 231 | 1617 | 47,966 | 14% | -667,181 | 715,147 | 47,966 | -667,181 |

### By split add filled
| split add filled | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| False | 360 | 616 | 246,959 | 71% | -126,733 | 373,692 | 300,991 | -142,466 |
| True | 2518 | 5506 | 98,818 | 29% | -2,374,870 | 2,473,688 | 144,694 | -2,994,252 |

### By exit type
| exit type | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| cut | 1600 | 3476 | -2,232,000 | -646% | -2,304,291 | 72,291 | -2,813,755 | -2,899,839 |
| flat | 16 | 29 | 5,160 | 1% | -2,183 | 7,343 | 6,445 | -2,347 |
| lock | 16 | 58 | -34,458 | -10% | -34,458 | 0 | -41,672 | -41,672 |
| stop | 78 | 142 | -160,671 | -46% | -160,671 | 0 | -192,859 | -192,859 |
| target | 1168 | 2417 | 2,767,746 | 800% | 0 | 2,767,746 | 3,487,527 | 0 |

### By side (+1 long)
| side (+1 long) | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| -1.0 | 1382 | 2951 | 97,132 | 28% | -1,243,274 | 1,340,406 | 61,683 | -1,604,280 |
| 1.0 | 1496 | 3171 | 248,645 | 72% | -1,258,330 | 1,506,974 | 384,002 | -1,532,438 |

### Book x ER bucket (net $)
| book | ER<0.30 (x0.5) | ER>=0.30 (x1.0) |
|---|---|---|
| HM | -7,050 | 36,921 |
| KB | 44,672 | 41,107 |
| MV | 20,567 | 15,210 |
| PB | 3,787 | 29,258 |
| PE | 49,020 | 46,098 |
| SM | 48,356 | 17,833 |

### Worst 30 trades
| label day | book | session | side | ER(20) | lots | mult | net $ | net at x1 $ | exit | entry | zone |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 20241206 | PE | nyam | L | 0.47 | 7 | x1 | -9,062 | -9,062 | cut | add |  |
| 20240813 | PE | nyam | L | 0.55 | 7 | x1 | -8,786 | -8,786 | cut | add |  |
| 20240924 | PE | nyam | S | 0.48 | 7 | x1 | -8,765 | -8,765 | stop | no add |  |
| 20241220 | PE | nyam | L | 0.59 | 7 | x1 | -8,236 | -8,236 | lock | add |  |
| 20240830 | PE | nyam | S | 0.25 | 4 | x0.5 | -7,554 | -13,220 | stop | add |  |
| 20240905 | PE | nyam | L | 0.49 | 7 | x1 | -7,124 | -7,124 | cut | add |  |
| 20250120 | PE | london | S | 0.33 | 7 | x1 | -6,802 | -6,802 | cut | add |  |
| 20250130 | PE | nyam | S | 0.16 | 4 | x0.5 | -6,541 | -11,447 | lock | add |  |
| 20240904 | PE | nyam | L | 0.05 | 4 | x0.5 | -6,154 | -10,769 | stop | add |  |
| 20250120 | PE | nyam | L | 0.54 | 7 | x1 | -6,151 | -6,151 | stop | add |  |
| 20240906 | PE | london | L | 0.39 | 7 | x1 | -6,144 | -6,144 | stop | no add |  |
| 20241008 | PE | asia | S | 0.32 | 7 | x1 | -6,116 | -6,116 | cut | add |  |
| 20240913 | PE | asia | L | 0.51 | 7 | x1 | -5,999 | -5,999 | cut | add |  |
| 20241014 | PE | nyam | L | 0.70 | 7 | x1 | -5,990 | -5,990 | stop | add |  |
| 20250106 | PE | london | L | 0.44 | 7 | x1 | -5,961 | -5,961 | cut | add |  |
| 20240802 | PE | asia | S | 0.34 | 7 | x1 | -5,627 | -5,627 | cut | add |  |
| 20240812 | PE | asia | L | 0.38 | 7 | x1 | -5,613 | -5,613 | cut | add |  |
| 20250128 | PE | asia | L | 0.58 | 7 | x1 | -5,517 | -5,517 | cut | add |  |
| 20240823 | PE | asia | S | 0.36 | 7 | x1 | -5,462 | -5,462 | cut | add |  |
| 20240815 | PE | asia | L | 0.48 | 7 | x1 | -5,449 | -5,449 | cut | add |  |
| 20241018 | PE | asia | S | 0.37 | 7 | x1 | -5,435 | -5,435 | cut | add |  |
| 20240822 | PE | asia | L | 0.39 | 7 | x1 | -5,320 | -5,320 | cut | add |  |
| 20240827 | PE | london | S | 0.40 | 7 | x1 | -5,308 | -5,308 | cut | add |  |
| 20241126 | PE | asia | L | 0.57 | 7 | x1 | -5,293 | -5,293 | cut | add |  |
| 20241105 | PE | london | L | 0.40 | 7 | x1 | -5,272 | -5,272 | cut | add |  |
| 20240919 | PE | asia | S | 0.37 | 7 | x1 | -5,240 | -5,240 | cut | add |  |
| 20240807 | PE | asia | S | 0.47 | 7 | x1 | -5,235 | -5,235 | cut | add |  |
| 20250108 | PE | london | L | 0.39 | 7 | x1 | -5,209 | -5,209 | cut | add |  |
| 20240806 | PE | asia | L | 0.34 | 7 | x1 | -5,194 | -5,194 | cut | add |  |
| 20240903 | PE | asia | S | 0.55 | 7 | x1 | -5,191 | -5,191 | cut | add |  |

### Worst 10 days
| label day | day net $ | trades | lots | day net at x1 $ | share of trades at x1.5 | mean ER |
|---|---|---|---|---|---|---|
| 20250120 | -38,106 | 16 | 48 | -42,026 | 0% | 0.33 |
| 20240905 | -33,519 | 39 | 83 | -36,569 | 0% | 0.26 |
| 20250128 | -32,908 | 31 | 67 | -44,104 | 0% | 0.26 |
| 20250108 | -30,331 | 26 | 59 | -37,577 | 0% | 0.21 |
| 20241231 | -29,737 | 24 | 52 | -33,711 | 0% | 0.31 |
| 20240930 | -29,141 | 25 | 55 | -35,347 | 0% | 0.29 |
| 20241002 | -24,776 | 27 | 61 | -29,671 | 0% | 0.25 |
| 20241122 | -24,495 | 26 | 50 | -28,724 | 0% | 0.28 |
| 20240924 | -23,933 | 24 | 51 | -31,404 | 0% | 0.40 |
| 20250129 | -20,653 | 20 | 45 | -25,164 | 0% | 0.23 |

### Size effect in one line
ER>=0.30 trades at x1.0 (1225): net $186,426; ER<0.30 trades at x0.5 (1653): net $159,351 (at x1: $259,260, so the 0.5 multiplier moved $-99,908); share of the gross loss: ER>=0.30 57%, ER<0.30 43% (their share of trades 43% / 57%).

## Reading (BASE-4; table only, no recommendation)
- The remaining drawdown (A: 2026 peak 202630 -> trough 202637, -105k; B1: PRE 202506 -> 202509, -88k) sits entirely in the ER >= 0.30 trades traded at x1.0: A -105k (50% of the gross loss on 36% of the trades; the ER < 0.30 x0.5 trades net +0.6k), B1 -108k (63% of the gross loss on 45% of the trades; the x0.5 trades +19k). In the profitable B2 stretch the ER >= 0.30 trades earn +186k and the x0.5 trades +159k (the x0.5 multiplier gives up about 100k there: +259k at x1).
- The x0.5 multiplier now costs little where it matters (A: it moves -7.7k of the +8.3k those trades would earn at x1; B1: -5k), and the ladder-OFF engine run over the same weeks is -73k (A) and -75k (B1) against -105k and -88k with Q1-A: the Q1-A size-down leaves ~30k (A) and ~13k (B1) of lot-size effect; the rest of the loss is in the trades themselves (at x1 the ER >= 0.30 group is the same -105k / -108k).
- Where: by book A: KB -52k, MV -25k, PE -23k, HM -17k, PB -8k, SM +20k; PE ER >= 0.30 -62k, KB ER >= 0.30 -32k, HM ER >= 0.30 -24k. B1: PE -56k (PE ER >= 0.30 -73k), MV -20k, KB -12k. By session: London -60k (A) and -94k (B1). By exit type: the loss is the TH-L2 cut trades (A cut -1.22M vs target +1.19M gross); stop and lock exits are -61k / -11k in A. Split add filled: -213k in A and -111k in B1, add NOT filled +108k / +23k: the losing trades are the add-filled ones.
- The worst 30 trades of A and B1 are all PE (4 or 7 lots, x1.0 or x0.5), add filled, 26-29 of 30 ended by the cut.
- Trade net = the 11-book day series in all three episodes (the X cells contribute nothing).
