# DS3_SIZER_DRAWDOWN_ANATOMY - what a sizer could possibly fix (BASE-4, 2026-11-03T16:02Z)

Base = T-SIZER base (run_v13t_ts: V13T_LIVE + live ER(20) 5-min ladder x1.5 if ER>=0.30 else x0.5, zone HALF, sequential rounding, lock R scaled only when mult > 1; lock none = per-book locks). Every trade of the 6 live books in the episode; ER = the ER(20) value at the signal; mult = the ladder multiplier (zone half separate, flagged); lots = contracts traded (integer); "net at x1" = the same trade rescaled linearly to the session lots without the ladder (session lots after zone half, rounded): an approximation that keeps the same trades, the same exits and the same locks, so it is NOT the same as the ladder-OFF engine run, which is reported beside it. Exit type: stop / target / cut (TH-L2 loss cut) / lock (per-book week floor or day give-back flattened it) / flat (session flat). Table only, no recommendation.

## Summary (all three episodes)
net of the 6 live books summed from the trades; the 11-book day series also holds the X1-X5 cells (not trade-resolved), which is why it differs; ladder OFF = a separate engine run (same locks / cuts, lots x1, the trade set can differ); x1-rescaled = the same trades rescaled linearly.
| episode | label days | trades | trade net $ (live ladder) | 11-book day series $ | ladder OFF engine run $ | same trades at x1 $ | x1.5 trades net (at x1) | x0.5 trades net (at x1) | x1.5 share of gross loss / of trades |
|---|---|---|---|---|---|---|---|---|---|
| Episode A | 20260720..20260911 | 1462 | -170,420 | -170,420 | -73,564 | -93,405 | -180,139 (x1: -115,430) | 9,719 (x1: 22,025) | 62% / 36% |
| Episode B1 | 20250203..20250228 | 445 | -160,713 | -160,713 | -61,568 | -81,877 | -191,048 (x1: -124,331) | 30,335 (x1: 42,454) | 74% / 44% |
| Episode B2 | 20240801..20250131 | 2813 | 498,251 | 498,251 | 435,204 | 457,529 | 350,604 (x1: 204,721) | 147,647 (x1: 252,808) | 68% / 43% |


## Episode A: the 2026 drawdown, peak week 202630 -> trough week 202637 (weekly-cumulative maxDD of the F9/L6M window $170,420; the lead called it W28-W39)

1462 trades, 20260720..20260911. Net P&L of the episode at the live ladder: $-170,420 (day-series check $-170,420); weekly-cumulative maxDD inside it $170,420; the same period with the ladder OFF (separate engine run, lots x1): $-73,564; the SAME trades rescaled to x1 lots (size-neutral, linear in lots): $-93,405. Gross loss (sum of losing trades) $-1,782,620, gross win $1,612,200.

### By ER bucket / multiplier (the sizer question)
| bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| ER<0.30 (x0.5) | 934 | 1618 | 9,719 | -6% | -671,933 | 681,652 | 22,025 | -1,146,238 |
| ER>=0.30 (x1.5) | 528 | 2471 | -180,139 | 106% | -1,110,687 | 930,548 | -115,430 | -699,016 |

### By book
| book | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| HM | 223 | 536 | -37,990 | 22% | -234,336 | 196,346 | -14,573 | -256,795 |
| KB | 495 | 781 | -83,782 | 49% | -349,019 | 265,236 | -82,980 | -371,644 |
| MV | 246 | 386 | -26,598 | 16% | -170,295 | 143,697 | -27,244 | -166,131 |
| PB | 93 | 142 | -5,290 | 3% | -86,042 | 80,752 | -3,243 | -56,682 |
| PE | 304 | 1888 | -48,923 | 29% | -809,724 | 760,800 | 25,013 | -844,746 |
| SM | 101 | 356 | 32,164 | -19% | -133,205 | 165,369 | 9,622 | -149,256 |

### By session
| session | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| asia | 643 | 2080 | -42,336 | 25% | -900,757 | 858,421 | -15,034 | -969,354 |
| london | 458 | 1502 | -83,217 | 49% | -654,696 | 571,478 | -40,838 | -688,735 |
| nyam | 294 | 397 | -27,091 | 16% | -175,980 | 148,889 | -17,845 | -128,572 |
| nypm | 67 | 110 | -17,776 | 10% | -51,188 | 33,412 | -19,687 | -58,593 |

### By lots bucket
| lots bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| 1 | 602 | 602 | -32,780 | 19% | -267,154 | 234,374 | -51,852 | -405,844 |
| 2-3 | 501 | 1185 | -95,569 | 56% | -538,530 | 442,961 | -64,215 | -503,411 |
| 4-6 | 259 | 1202 | 40,971 | -24% | -481,857 | 522,828 | 75,507 | -620,949 |
| 7+ | 100 | 1100 | -83,042 | 49% | -495,079 | 412,037 | -52,845 | -315,050 |

### By split add filled
| split add filled | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| False | 205 | 427 | 135,996 | -80% | -112,410 | 248,406 | 167,765 | -90,042 |
| True | 1257 | 3662 | -306,416 | 180% | -1,670,210 | 1,363,794 | -261,170 | -1,755,212 |

### By exit type
| exit type | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| cut | 897 | 2612 | -1,649,678 | 968% | -1,683,913 | 34,235 | -1,735,439 | -1,773,745 |
| flat | 1 | 1 | -52 | 0% | -52 | 0 | -105 | -105 |
| lock | 14 | 24 | -9,323 | 5% | -9,803 | 480 | -4,813 | -5,073 |
| stop | 46 | 71 | -88,852 | 52% | -88,852 | 0 | -66,332 | -66,332 |
| target | 504 | 1381 | 1,577,485 | -926% | 0 | 1,577,485 | 1,713,283 | 0 |

### By side (+1 long)
| side (+1 long) | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| -1.0 | 734 | 2097 | -109,400 | 64% | -936,316 | 826,916 | -46,806 | -947,853 |
| 1.0 | 728 | 1992 | -61,020 | 36% | -846,305 | 785,284 | -46,599 | -897,402 |

### Book x ER bucket (net $)
| book | ER<0.30 (x0.5) | ER>=0.30 (x1.5) |
|---|---|---|
| HM | 6,085 | -44,075 |
| KB | -25,291 | -58,491 |
| MV | -10,688 | -15,910 |
| PB | -1,197 | -4,093 |
| PE | 49,676 | -98,599 |
| SM | -8,866 | 41,030 |

### Worst 30 trades
| label day | book | session | side | ER(20) | lots | mult | net $ | net at x1 $ | exit | entry | zone |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 20260724 | PE | london | S | 0.44 | 11 | x1.5 | -12,947 | -8,239 | cut | add |  |
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
| 20260723 | PE | asia | S | 0.57 | 11 | x1.5 | -7,257 | -4,618 | cut | add |  |
| 20260903 | PE | asia | L | 0.33 | 11 | x1.5 | -7,185 | -4,572 | cut | add |  |
| 20260812 | PE | london | L | 0.43 | 11 | x1.5 | -7,181 | -4,570 | cut | add |  |
| 20260908 | PE | london | S | 0.46 | 11 | x1.5 | -7,168 | -4,562 | cut | add |  |
| 20260805 | PE | london | S | 0.49 | 11 | x1.5 | -7,165 | -4,559 | cut | add |  |
| 20260827 | PE | london | L | 0.43 | 11 | x1.5 | -7,095 | -4,515 | cut | add |  |
| 20260821 | PE | london | L | 0.39 | 11 | x1.5 | -7,085 | -4,509 | cut | add |  |
| 20260724 | PE | london | L | 0.42 | 11 | x1.5 | -7,073 | -4,501 | cut | add |  |
| 20260902 | PE | london | L | 0.37 | 11 | x1.5 | -7,073 | -4,501 | cut | add |  |

### Worst 10 days
| label day | day net $ | trades | lots | day net at x1 $ | share of trades at x1.5 | mean ER |
|---|---|---|---|---|---|---|
| 20260720 | -54,929 | 48 | 134 | -48,518 | 33% | 0.22 |
| 20260806 | -50,721 | 46 | 118 | -45,295 | 30% | 0.21 |
| 20260819 | -47,551 | 38 | 103 | -33,733 | 45% | 0.25 |
| 20260730 | -43,726 | 55 | 164 | -26,180 | 35% | 0.25 |
| 20260907 | -28,276 | 16 | 50 | -26,912 | 50% | 0.28 |
| 20260903 | -28,075 | 32 | 98 | -24,298 | 53% | 0.33 |
| 20260828 | -27,619 | 24 | 62 | -23,134 | 33% | 0.25 |
| 20260904 | -24,406 | 26 | 78 | -10,304 | 27% | 0.23 |
| 20260803 | -22,316 | 43 | 87 | -32,555 | 19% | 0.21 |
| 20260902 | -21,956 | 21 | 71 | -16,395 | 38% | 0.22 |

### Size effect in one line
x1.5 trades (528): net $-180,139 (at x1: $-115,430, so the 1.5 multiplier moved $-64,709); x0.5 trades (934): net $9,719 (at x1: $22,025, the 0.5 multiplier moved $-12,306); loss share: x1.5 trades carry 62% of the gross loss, x0.5 trades 38% (their share of trades 36% / 64%).

## Episode B1: the PRE drawdown, peak week 202506 -> trough week 202509 (maxDD $160,713)

445 trades, 20250203..20250228. Net P&L of the episode at the live ladder: $-160,713 (day-series check $-160,713); weekly-cumulative maxDD inside it $160,713; the same period with the ladder OFF (separate engine run, lots x1): $-61,568; the SAME trades rescaled to x1 lots (size-neutral, linear in lots): $-81,877. Gross loss (sum of losing trades) $-643,408, gross win $482,695.

### By ER bucket / multiplier (the sizer question)
| bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| ER<0.30 (x0.5) | 249 | 423 | 30,335 | -19% | -169,608 | 199,943 | 42,454 | -289,589 |
| ER>=0.30 (x1.5) | 196 | 932 | -191,048 | 119% | -473,800 | 282,752 | -124,331 | -298,149 |

### By book
| book | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| HM | 60 | 142 | -903 | 1% | -60,071 | 59,168 | -5,511 | -62,439 |
| KB | 156 | 253 | -24,963 | 16% | -112,371 | 87,408 | -14,470 | -109,453 |
| MV | 77 | 127 | -30,122 | 19% | -67,032 | 36,910 | -24,893 | -55,454 |
| PB | 19 | 32 | -3,519 | 2% | -20,251 | 16,732 | 1,826 | -10,125 |
| PE | 103 | 694 | -108,662 | 68% | -342,270 | 233,608 | -43,770 | -308,928 |
| SM | 30 | 107 | 7,456 | -5% | -41,413 | 48,869 | 4,941 | -41,337 |

### By session
| session | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| asia | 147 | 503 | -4,731 | 3% | -224,253 | 219,522 | 7,253 | -222,029 |
| london | 117 | 449 | -144,479 | 90% | -236,140 | 91,661 | -111,524 | -210,491 |
| nyam | 143 | 342 | -1,748 | 1% | -154,997 | 153,249 | 26,722 | -125,368 |
| nypm | 38 | 61 | -9,755 | 6% | -28,018 | 18,263 | -4,329 | -29,850 |

### By lots bucket
| lots bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| 1 | 165 | 165 | 7,573 | -5% | -66,745 | 74,318 | 2,190 | -101,675 |
| 2-3 | 168 | 398 | -59,957 | 37% | -194,952 | 134,995 | -38,688 | -161,968 |
| 4-6 | 70 | 330 | 25,238 | -16% | -131,826 | 157,064 | 39,618 | -165,075 |
| 7+ | 42 | 462 | -133,568 | 83% | -249,887 | 116,319 | -84,998 | -159,019 |

### By split add filled
| split add filled | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| False | 51 | 108 | 27,192 | -17% | -29,936 | 57,129 | 29,129 | -24,892 |
| True | 394 | 1247 | -187,906 | 117% | -613,472 | 425,567 | -111,007 | -562,845 |

### By exit type
| exit type | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| cut | 271 | 854 | -556,816 | 346% | -566,433 | 9,617 | -526,067 | -533,466 |
| flat | 4 | 21 | -6,367 | 4% | -6,886 | 519 | -3,855 | -4,201 |
| lock | 2 | 22 | -9,343 | 6% | -9,343 | 0 | -5,945 | -5,945 |
| stop | 15 | 50 | -60,747 | 38% | -60,747 | 0 | -44,125 | -44,125 |
| target | 153 | 408 | 472,559 | -294% | 0 | 472,559 | 498,114 | 0 |

### By side (+1 long)
| side (+1 long) | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| -1.0 | 212 | 703 | -78,742 | 49% | -331,226 | 252,484 | -66,405 | -301,057 |
| 1.0 | 233 | 652 | -81,972 | 51% | -312,183 | 230,211 | -15,472 | -286,681 |

### Book x ER bucket (net $)
| book | ER<0.30 (x0.5) | ER>=0.30 (x1.5) |
|---|---|---|
| HM | -2,205 | 1,302 |
| KB | 7,119 | -32,083 |
| MV | -4,141 | -25,982 |
| PB | 7,171 | -10,690 |
| PE | 22,413 | -131,075 |
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
| 20250221 | PE | nyam | S | 0.66 | 11 | x1.5 | -7,382 | -4,698 | cut | add |  |
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

### Worst 10 days
| label day | day net $ | trades | lots | day net at x1 $ | share of trades at x1.5 | mean ER |
|---|---|---|---|---|---|---|
| 20250224 | -41,666 | 23 | 84 | -29,471 | 61% | 0.32 |
| 20250228 | -37,711 | 36 | 90 | -31,079 | 22% | 0.21 |
| 20250204 | -36,973 | 29 | 126 | -17,950 | 66% | 0.33 |
| 20250206 | -26,566 | 16 | 45 | -18,371 | 44% | 0.32 |
| 20250218 | -22,887 | 19 | 71 | -11,126 | 58% | 0.34 |
| 20250205 | -16,957 | 22 | 53 | -9,888 | 32% | 0.27 |
| 20250219 | -13,512 | 14 | 34 | -17,905 | 57% | 0.30 |
| 20250213 | -10,522 | 32 | 118 | 1,025 | 56% | 0.34 |
| 20250227 | -7,641 | 30 | 107 | -5,744 | 37% | 0.28 |
| 20250212 | -7,021 | 17 | 30 | -9,793 | 53% | 0.30 |

### Size effect in one line
x1.5 trades (196): net $-191,048 (at x1: $-124,331, so the 1.5 multiplier moved $-66,717); x0.5 trades (249): net $30,335 (at x1: $42,454, the 0.5 multiplier moved $-12,119); loss share: x1.5 trades carry 74% of the gross loss, x0.5 trades 26% (their share of trades 44% / 56%).

## Episode B2: 2024-08-01..2025-01-31 (PRE middle third, as ordered; contains the carrying weeks 202434-202451)

2813 trades, 20240801..20250131. Net P&L of the episode at the live ladder: $498,251 (day-series check $498,251); weekly-cumulative maxDD inside it $155,639; the same period with the ladder OFF (separate engine run, lots x1): $435,204; the SAME trades rescaled to x1 lots (size-neutral, linear in lots): $457,529. Gross loss (sum of losing trades) $-3,475,120, gross win $3,973,371.

### By ER bucket / multiplier (the sizer question)
| bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| ER<0.30 (x0.5) | 1609 | 2716 | 147,647 | 30% | -1,119,875 | 1,267,521 | 252,808 | -1,844,991 |
| ER>=0.30 (x1.5) | 1204 | 5801 | 350,604 | 70% | -2,355,245 | 2,705,850 | 204,721 | -1,485,020 |

### By book
| book | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| HM | 448 | 1019 | 43,246 | 9% | -416,750 | 459,996 | -726 | -447,461 |
| KB | 952 | 1525 | 103,972 | 21% | -593,338 | 697,310 | 96,148 | -584,215 |
| MV | 456 | 746 | 58,796 | 12% | -288,511 | 347,307 | 47,704 | -235,986 |
| PB | 132 | 220 | 63,704 | 13% | -98,091 | 161,795 | 33,593 | -61,646 |
| PE | 634 | 4292 | 150,018 | 30% | -1,797,074 | 1,947,093 | 157,087 | -1,762,468 |
| SM | 191 | 715 | 78,515 | 16% | -281,355 | 359,870 | 123,723 | -238,234 |

### By session
| session | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| asia | 1010 | 3593 | 328,038 | 66% | -1,448,456 | 1,776,494 | 304,323 | -1,409,817 |
| london | 665 | 2495 | -15,885 | -3% | -1,066,733 | 1,050,848 | 65,674 | -985,082 |
| nyam | 943 | 2109 | 192,542 | 39% | -828,557 | 1,021,100 | 77,924 | -794,879 |
| nypm | 195 | 320 | -6,445 | -1% | -131,374 | 124,929 | 9,609 | -140,233 |

### By lots bucket
| lots bucket | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| 1 | 1088 | 1088 | 64,027 | 13% | -437,291 | 501,319 | 96,660 | -604,615 |
| 2-3 | 997 | 2357 | 225,332 | 45% | -928,196 | 1,153,528 | 177,726 | -813,421 |
| 4-6 | 470 | 2234 | 71,013 | 14% | -947,807 | 1,018,820 | 95,402 | -1,172,631 |
| 7+ | 258 | 2838 | 137,879 | 28% | -1,161,825 | 1,299,705 | 87,741 | -739,343 |

### By split add filled
| split add filled | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| False | 357 | 902 | 363,081 | 73% | -189,074 | 552,155 | 311,335 | -152,288 |
| True | 2456 | 7615 | 135,170 | 27% | -3,286,046 | 3,421,216 | 146,194 | -3,177,723 |

### By exit type
| exit type | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| cut | 1549 | 4785 | -3,067,902 | -616% | -3,170,551 | 102,649 | -2,954,997 | -3,053,501 |
| flat | 16 | 35 | 7,077 | 1% | -2,734 | 9,811 | 6,209 | -2,872 |
| lock | 29 | 98 | -43,110 | -9% | -43,384 | 273 | -31,024 | -31,282 |
| stop | 81 | 223 | -258,452 | -52% | -258,452 | 0 | -242,355 | -242,355 |
| target | 1138 | 3376 | 3,860,638 | 775% | 0 | 3,860,638 | 3,679,696 | 0 |

### By side (+1 long)
| side (+1 long) | trades | lots | net $ | share of episode net | gross loss $ | gross win $ | net at x1 $ | gross loss at x1 $ |
|---|---|---|---|---|---|---|---|---|
| -1.0 | 1347 | 4108 | 204,095 | 41% | -1,702,407 | 1,906,502 | 80,963 | -1,717,255 |
| 1.0 | 1466 | 4409 | 294,157 | 59% | -1,772,713 | 2,066,869 | 376,566 | -1,612,756 |

### Book x ER bucket (net $)
| book | ER<0.30 (x0.5) | ER>=0.30 (x1.5) |
|---|---|---|
| HM | -17,800 | 61,047 |
| KB | 32,838 | 71,134 |
| MV | 21,334 | 37,462 |
| PB | 3,483 | 60,221 |
| PE | 54,257 | 95,761 |
| SM | 53,535 | 24,980 |

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
| 20240905 | -49,802 | 35 | 111 | -38,764 | 40% | 0.26 |
| 20250128 | -46,899 | 28 | 84 | -46,665 | 43% | 0.27 |
| 20250120 | -45,960 | 14 | 58 | -35,207 | 57% | 0.32 |
| 20241231 | -43,208 | 23 | 73 | -33,721 | 57% | 0.32 |
| 20240930 | -42,301 | 26 | 78 | -39,374 | 42% | 0.28 |
| 20250108 | -40,383 | 26 | 77 | -37,577 | 31% | 0.21 |
| 20241122 | -35,621 | 26 | 69 | -30,704 | 46% | 0.28 |
| 20241002 | -34,966 | 24 | 78 | -30,716 | 42% | 0.26 |
| 20240906 | -29,330 | 32 | 103 | -9,276 | 50% | 0.33 |
| 20240924 | -28,157 | 23 | 73 | -29,938 | 65% | 0.39 |

### Size effect in one line
x1.5 trades (1204): net $350,604 (at x1: $204,721, so the 1.5 multiplier moved $145,883); x0.5 trades (1609): net $147,647 (at x1: $252,808, the 0.5 multiplier moved $-105,161); loss share: x1.5 trades carry 68% of the gross loss, x0.5 trades 32% (their share of trades 43% / 57%).

## Reading (BASE-4; CORRECTED version 2026-11-03 - the first version of this page read the trade record of the wrong engine run (a plain V13T_LIVE run made by the kernel-reference helper after the ts run), so its trade-level numbers were slightly off; the day-series check below now ties exactly: trade net = 11-book day series in A and B1)
- Old ts base (ladder x0.5 / x1.5). Episode A (2026, peak 202630 -> trough 202637, -170k): the x1.5 trades net -180k (62% of the gross loss on 36% of the trades), the x0.5 trades +10k; the same x1.5 trades at x1 would be -115k, so the 1.5 multiplier added about -65k; the ladder-OFF engine run over the same weeks is -74k against -170k. Episode B1 (PRE, 202506 -> 202509, -161k): x1.5 trades -191k (74% of the gross loss on 44% of the trades), at x1 -124k (the multiplier adds -67k), ladder OFF -62k against -161k. In the net-positive B2 stretch the x1.5 trades earn +351k (+205k at x1). More than half of the ts-era drawdown loss was the size excess of the x1.5 trades; the rest is high-ER trades that lose even at x1.
- The worst 30 trades of every episode were PE (P6) x1.5 trades (11 lots against 7), split add filled, almost all ended by the TH-L2 cut.
- Under the live Q1-A ladder (no x1.5) see DS3_SIZER_DRAWDOWN_ANATOMY_Q1A.md.
