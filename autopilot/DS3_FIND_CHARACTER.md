# DS3_FIND_CHARACTER.md - T-FIND Step 1 character map per instrument (append-only; CHAR-A pages ES RTY YM NQ; CHAR-B/CHAR-C pages for the rest). Shared library: l2vast/ds3/code/find/char_lib.py (landed 2026-11-05T21:24Z, prereg sha256 980bedf6bad3f1669de9efb93831fa4622d88577c892d9359b7f57ba93c9dbcf in DECISIONS.md).

## RTY - character map (CHAR-A, 2026-11-05T22:08Z)
Base: RTY CME front-month (.v.0) 1-min bars from 2017-07 to 2026-10, percent frame (multiplicative roll-adjusted), 1-min approximation (no tick path), 2143 usable label days; ET clock, sessions asia 18:00-02:00 / london 02:00-08:30 / pre 08:30-09:30 / nyam 09:30-12:00 / nypm 12:00-15:00 / close 15:00-16:55. Nulls: within-year shuffled-day (AC B=300; structure B=100 worlds; levels recomputed on the shuffled path; round numbers 60 random grid phases); p_family = Westfall-Young max-|z| over the block (AC family 153 cells, structure family 92 cells). `**` p_family<=.05, `*` <=.10. Prereg sha256 980bedf6bad3f1669de9efb93831fa4622d88577c892d9359b7f57ba93c9dbcf. Descriptive only: no PASS, nothing live.

### Plain paragraph
At 1 minute every session has negative autocorrelation (-0.038 to +0.000; bid-ask bounce / last-print noise, not a tradable edge by itself). asia: reverts at 5 min (-0.021). london: reverts at 5 min (-0.009). pre: reverts at 5/30 min (-0.036, -0.101). Day types (RTH): 47% trend days (efficiency ratio >= .5; shuffled null 46%, p_fam 1.000), 23% range days (<.25; null 26%, p_fam 0.574); the IB (09:30-10:30) is extended on one side only on 77% of days and on both on 17%, and a one-sided extension closes beyond the IB edge 63% of the time (null 63%). RTH variance ratio at 30 min 0.986 (shuffled null 0.998, p_fam 1.000); Hurst 0.499. The RTH range forms 9:30 (43%), 10:00 (25%), 11:00 (10%) of the range increments. No level (prior-day H/L, overnight H/L, IB edge, VWAP +-1/2 sigma, round numbers) beats its shuffled-day family null for bounce vs break-through. Failed-break follow-through beating the null: none. Room (median 3xATR14(5m) $ / round-trip cost $20 per lot): asia 7.9x, london 9.7x, pre 13.3x, nyam 26.5x, nypm 21.1x, close 18.0x (1xATR5 room 8.8x in nyam, 2.6x in asia).

### 1. Autocorrelation of h-min returns (corr(past h, next h), both inside the session), pooled; cell = corr (pre-2023 mean | 2023+ mean) p_family
| session | 1 min | 5 min | 15 min | 30 min | 60 min | 120 min |
|--|--|--|--|--|--|--|
| asia | -0.038 (-0.044|-0.029) p0.003** ys1.00 | -0.021 (-0.029|-0.018) p0.003** ys0.90 | -0.007 (-0.008|-0.017) p0.993 ys0.70 | -0.002 (-0.002|-0.013) p1.000 ys0.70 | -0.006 (-0.003|-0.001) p1.000 ys0.70 | -0.018 (-0.041|+0.010) p1.000 ys0.70 |
| london | -0.019 (-0.030|-0.008) p0.003** ys1.00 | -0.009 (-0.019|-0.007) p0.013** ys0.80 | -0.009 (+0.002|-0.014) p0.771 ys0.70 | -0.005 (-0.014|-0.007) p1.000 ys0.60 | -0.007 (-0.022|+0.012) p1.000 ys0.50 | -0.019 (-0.006|+0.005) p1.000 ys0.60 |
| pre | -0.023 (-0.027|-0.018) p0.003** ys0.90 | -0.036 (-0.027|-0.042) p0.003** ys0.90 | -0.032 (-0.047|-0.030) p0.243 ys0.90 | -0.101 (-0.026|-0.175) p0.013** ys0.80 | - | - |
| nyam | +0.000 (+0.013|-0.020) p1.000 ys0.40 | -0.005 (-0.003|-0.005) p1.000 ys0.60 | +0.006 (+0.040|-0.001) p1.000 ys0.60 | +0.006 (+0.009|+0.004) p1.000 ys0.50 | -0.018 (-0.045|+0.016) p1.000 ys0.70 | - |
| nypm | -0.005 (-0.001|-0.018) p0.243 ys0.70 | -0.008 (-0.013|-0.009) p0.953 ys0.70 | -0.000 (-0.012|+0.007) p1.000 ys0.60 | +0.002 (+0.016|+0.008) p1.000 ys0.60 | -0.007 (-0.010|+0.017) p1.000 ys0.50 | - |
| close | -0.007 (+0.003|-0.009) p0.621 ys0.70 | -0.007 (-0.009|-0.009) p1.000 ys0.70 | +0.006 (-0.000|-0.022) p1.000 ys0.60 | +0.008 (+0.024|-0.060) p1.000 ys0.50 | - | - |

Hour cells (h >= 5) beating the family null, top 14 by |z| (hour = ET hour of the decision bar):
| h | session | hour ET | corr | z | p_family | year sign share | pre-2023 | 2023+ |
|--|--|--|--|--|--|--|--|--|
| 5 | asia | 22 | -0.040 | -7.9 | 0.003 | 0.80 | -0.035 | -0.030 |
| 5 | asia | 23 | -0.039 | -7.0 | 0.003 | 0.90 | -0.029 | -0.039 |
| 5 | pre | 09 | -0.056 | -6.7 | 0.003 | 0.90 | -0.030 | -0.069 |
| 5 | asia | 18 | -0.035 | -6.7 | 0.003 | 0.80 | -0.035 | -0.028 |
| 15 | pre | 09 | -0.095 | -6.5 | 0.003 | 0.90 | -0.139 | -0.061 |
| 5 | asia | 01 | -0.029 | -5.7 | 0.003 | 0.80 | -0.050 | -0.003 |
| 5 | close | 16 | -0.034 | -5.5 | 0.003 | 0.90 | -0.045 | -0.064 |
| 15 | asia | 18 | -0.041 | -4.9 | 0.007 | 0.70 | -0.040 | -0.018 |
| 30 | asia | 18 | -0.068 | -4.8 | 0.013 | 0.80 | -0.064 | -0.096 |
| 15 | asia | 00 | +0.046 | +4.6 | 0.013 | 0.50 | +0.019 | -0.002 |
| 60 | asia | 23 | -0.068 | -4.5 | 0.013 | 0.50 | -0.074 | +0.021 |
| 30 | pre | 08 | -0.101 | -4.5 | 0.013 | 0.80 | -0.026 | -0.175 |
| 30 | asia | 00 | +0.063 | +4.4 | 0.013 | 0.40 | +0.031 | -0.041 |
| 60 | asia | 20 | +0.068 | +4.1 | 0.013 | 0.60 | +0.035 | +0.060 |

### 2. Variance ratio VR(q) and Hurst (1.0 = random walk; <1 reverting; edge-bias corrected), cell = value (null) p_family
| session | VR5 | VR15 | VR30 | VR60 | VR120 | Hurst |
|--|--|--|--|--|--|--|
| asia | 0.919 (0.999) p0.016** | 0.888 (0.999) p0.016** | 0.884 (0.999) p0.016** | 0.888 (0.999) p0.016** | 0.887 (1.000) p0.016** | 0.495 (0.500) p0.508 |
| london | 0.964 (0.999) p0.016** | 0.948 (0.999) p0.016** | 0.940 (0.999) p0.016** | 0.938 (1.000) p0.016** | 0.939 (0.999) p0.049** | 0.496 (0.500) p1.000 |
| pre | 0.946 (1.000) p0.016** | 0.898 (1.001) p0.016** | - | - | - | 0.476 (0.500) p0.016** |
| nyam | 0.999 (0.999) p1.000 | 0.990 (0.997) p1.000 | 0.994 (0.996) p1.000 | - | - | 0.498 (0.499) p1.000 |
| nypm | 0.986 (1.000) p0.016** | 0.975 (0.999) p0.033** | 0.968 (0.999) p0.393 | 0.971 (1.000) p1.000 | - | 0.497 (0.500) p1.000 |
| close | 0.983 (0.999) p0.082* | 0.971 (0.998) p0.279 | 0.986 (0.999) p1.000 | - | - | 0.500 (0.500) p1.000 |
| rth | 0.996 (1.000) p1.000 | 0.986 (0.998) p0.541 | 0.986 (0.998) p1.000 | 0.988 (0.998) p1.000 | 0.988 (0.998) p1.000 | 0.499 (0.500) p1.000 |

### 3. Day types (ex-post labels of the RTH day)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| day|trend | 0.475 | 2143 | 0.460 | +1.5 | 1.000 | 0.70 | 0.489 | 0.459 | stable |
| day|range | 0.233 | 2143 | 0.256 | -2.5 | 0.574 | 0.80 | 0.193 | 0.265 | stable |
| day|er | 0.474 | 2143 | 0.464 | +1.9 | 0.984 | 0.80 | 0.491 | 0.463 | stable |
| day|ib_none | 0.056 | 2143 | 0.036 | +4.5 | 0.016** | 0.90 | 0.050 | 0.063 | stable |
| day|ib_one | 0.769 | 2143 | 0.739 | +3.5 | 0.049** | 0.70 | 0.753 | 0.784 | stable |
| day|ib_both | 0.175 | 2143 | 0.225 | -6.7 | 0.016** | 0.90 | 0.197 | 0.153 | stable |
| day|ib_one_closebeyond | 0.633 | 1648 | 0.628 | +0.4 | 1.000 | 0.50 | 0.678 | 0.603 | unstable |

### 4. 1A -> 2A continuation vs give-back-half from the session open (A = 3 x ATR14(5m)); value = P(continue | resolved)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| cont|asia | 0.340 | 1159 | 0.359 | -1.6 | 1.000 | 0.70 | 0.328 | 0.336 | stable |
| cont|london | 0.352 | 2137 | 0.373 | -2.1 | 0.918 | 0.80 | 0.322 | 0.352 | stable |
| cont|pre | 0.374 | 872 | 0.359 | +1.0 | 1.000 | 0.40 | 0.313 | 0.426 | REGIME(2023+ only) |
| cont|nyam | 0.373 | 2089 | 0.344 | +2.6 | 0.541 | 0.70 | 0.380 | 0.369 | stable |
| cont|nypm | 0.268 | 686 | 0.268 | +0.0 | 1.000 | 0.50 | 0.249 | 0.279 | REGIME(2023+ only) |
| cont|close | 0.253 | 558 | 0.249 | +0.3 | 1.000 | 0.60 | 0.274 | 0.209 | stable |
| cont|rth | 0.373 | 2122 | 0.345 | +2.5 | 0.541 | 0.70 | 0.381 | 0.370 | stable |

### 5. Gap fill by size bucket (b0 .05-.10, b1 .10-.25, b2 .25-.50, b3 >.50 of the 20-day mean RTH range); day = filled during RTH, h1 = within 60 min
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| gap|b0|day | 0.889 | 208 | 0.899 | -0.4 | 1.000 | 0.40 | 0.906 | 0.903 | unstable |
| gap|b0|h1 | 0.841 | 208 | 0.828 | +0.4 | 1.000 | 0.70 | 0.872 | 0.849 | stable |
| gap|b1|day | 0.745 | 585 | 0.775 | -1.6 | 1.000 | 0.70 | 0.791 | 0.732 | REGIME(2023+ only) |
| gap|b1|h1 | 0.615 | 585 | 0.629 | -0.6 | 1.000 | 0.40 | 0.626 | 0.610 | unstable |
| gap|b2|day | 0.557 | 639 | 0.555 | +0.1 | 1.000 | 0.50 | 0.519 | 0.587 | REGIME(2023+ only) |
| gap|b2|h1 | 0.366 | 639 | 0.329 | +2.1 | 0.918 | 0.80 | 0.360 | 0.394 | stable |
| gap|b3|day | 0.305 | 492 | 0.263 | +2.5 | 0.574 | 0.90 | 0.385 | 0.273 | stable |
| gap|b3|h1 | 0.102 | 492 | 0.082 | +1.9 | 1.000 | 0.70 | 0.084 | 0.112 | stable |

### 6. Level reaction: first touch -> bounce (0.5A reverse) vs break-through (0.5A beyond) within 60 min; value = P(bounce)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| rx|PD|asia | 0.433 | 742 | 0.457 | -1.4 | 1.000 | 0.80 | 0.410 | 0.463 | stable |
| rx|PD|london | 0.496 | 1004 | 0.478 | +1.2 | 1.000 | 0.70 | 0.514 | 0.524 | stable |
| rx|PD|pre | 0.467 | 583 | 0.478 | -0.6 | 1.000 | 0.60 | 0.489 | 0.449 | REGIME(2023+ only) |
| rx|PD|nyam | 0.474 | 1415 | 0.494 | -1.9 | 1.000 | 0.60 | 0.454 | 0.502 | stable |
| rx|PD|nypm | 0.484 | 690 | 0.496 | -0.7 | 1.000 | 0.50 | 0.432 | 0.491 | unstable |
| rx|PD|close | 0.477 | 426 | 0.494 | -0.7 | 1.000 | 0.70 | 0.495 | 0.452 | REGIME(2023+ only) |
| rx|ON|nyam | 0.494 | 2261 | 0.493 | +0.2 | 1.000 | 0.60 | 0.509 | 0.499 | stable |
| rx|ON|nypm | 0.503 | 907 | 0.494 | +0.6 | 1.000 | 0.50 | 0.400 | 0.538 | REGIME(2023+ only) |
| rx|ON|close | 0.488 | 535 | 0.492 | -0.2 | 1.000 | 0.40 | 0.506 | 0.501 | unstable |
| rx|IB|nyam | 0.483 | 1477 | 0.499 | -1.4 | 1.000 | 0.80 | 0.487 | 0.487 | stable |
| rx|IB|nypm | 0.481 | 1145 | 0.494 | -1.0 | 1.000 | 0.50 | 0.500 | 0.486 | REGIME(2023+ only) |
| rx|IB|close | 0.492 | 697 | 0.491 | +0.0 | 1.000 | 0.40 | 0.432 | 0.534 | REGIME(2023+ only) |
| rx|VW1|nyam | 0.492 | 3022 | 0.495 | -0.3 | 1.000 | 0.60 | 0.515 | 0.486 | REGIME(2023+ only) |
| rx|VW1|nypm | 0.492 | 1829 | 0.494 | -0.2 | 1.000 | 0.60 | 0.506 | 0.478 | REGIME(2023+ only) |
| rx|VW1|close | 0.485 | 1290 | 0.494 | -0.6 | 1.000 | 0.60 | 0.466 | 0.500 | stable |
| rx|VW2|nyam | 0.480 | 2103 | 0.502 | -2.3 | 0.672 | 0.80 | 0.466 | 0.495 | stable |
| rx|VW2|nypm | 0.475 | 1047 | 0.495 | -1.6 | 1.000 | 0.80 | 0.487 | 0.463 | stable |
| rx|VW2|close | 0.498 | 558 | 0.494 | +0.2 | 1.000 | 0.40 | 0.439 | 0.562 | REGIME(2023+ only) |
| rx|RN|asia | 0.475 | 33200 | 0.476 | -0.4 | 1.000 | 0.50 | 0.458 | 0.479 | unstable |
| rx|RN|london | 0.484 | 49315 | 0.484 | +0.3 | 1.000 | 0.60 | 0.480 | 0.487 | REGIME(2023+ only) |
| rx|RN|pre | 0.496 | 13349 | 0.495 | +0.1 | 1.000 | 0.60 | 0.508 | 0.495 | stable |
| rx|RN|nyam | 0.495 | 52512 | 0.496 | -0.5 | 1.000 | 0.60 | 0.493 | 0.491 | stable |
| rx|RN|nypm | 0.493 | 36530 | 0.495 | -1.1 | 1.000 | 0.60 | 0.481 | 0.490 | stable |
| rx|RN|close | 0.491 | 13550 | 0.496 | -1.7 | 1.000 | 0.80 | 0.483 | 0.495 | stable |

### 7. Failed break (close .25A beyond, back inside within 10 bars): fade follow-through P(0.5A back before 0.5A out)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| fb|PD|asia | 0.513 | 435 | 0.499 | +0.7 | 1.000 | 0.50 | 0.465 | 0.516 | REGIME(2023+ only) |
| fb|PD|london | 0.498 | 729 | 0.500 | -0.1 | 1.000 | 0.60 | 0.543 | 0.491 | REGIME(2023+ only) |
| fb|PD|pre | 0.458 | 336 | 0.504 | -1.5 | 1.000 | 0.70 | 0.461 | 0.454 | stable |
| fb|PD|nyam | 0.532 | 930 | 0.500 | +1.9 | 1.000 | 0.80 | 0.496 | 0.547 | REGIME(2023+ only) |
| fb|PD|nypm | 0.480 | 417 | 0.501 | -1.1 | 1.000 | 0.80 | 0.504 | 0.444 | REGIME(2023+ only) |
| fb|PD|close | 0.440 | 218 | 0.498 | -1.8 | 1.000 | 0.70 | 0.370 | 0.459 | stable |
| fb|ON|nyam | 0.496 | 1149 | 0.500 | -0.3 | 1.000 | 0.50 | 0.522 | 0.475 | REGIME(2023+ only) |
| fb|ON|nypm | 0.496 | 522 | 0.500 | -0.2 | 1.000 | 0.30 | 0.496 | 0.496 | unstable |
| fb|ON|close | 0.455 | 288 | 0.500 | -1.6 | 1.000 | 0.60 | 0.531 | 0.473 | REGIME(2023+ only) |
| fb|IB|nyam | 0.493 | 479 | 0.499 | -0.3 | 1.000 | 0.30 | 0.499 | 0.502 | unstable |
| fb|IB|nypm | 0.490 | 661 | 0.499 | -0.6 | 1.000 | 0.60 | 0.486 | 0.496 | stable |
| fb|IB|close | 0.471 | 314 | 0.498 | -1.0 | 1.000 | 0.60 | 0.401 | 0.531 | stable |

### 8. Where the range forms
RTH range increments by bin: 9:30 42.9%, 10:00 24.7%, 11:00 10.2%, 12:00 6.4%, 13:00 4.9%, 14:00 5.1%, 15:00 5.9%
Label-day range increments by ET hour (percent of the day): 00h 1.2, 01h 1.6, 02h 2.7, 03h 4.8, 04h 3.7, 05h 2.5, 06h 2.4, 07h 2.4, 08h 6.7, 09h 15.2, 10h 11.5, 11h 5.8, 12h 3.7, 13h 2.9, 14h 3.3, 15h 3.8, 16h 1.0, 18h 8.5, 19h 4.4, 20h 5.2, 21h 3.6, 22h 1.9, 23h 1.3

### 9. Room and liquidity (all years, raw-frame $, 1 lot)
| session | ATR14(5m) $ | A=3xATR5 $ | RT cost $ | room(1 ATR5) | room(A) | median 5-min vol | 1.7% cap (contracts/5min) | lots for $1,200 at 3xATR5 stop |
|--|--|--|--|--|--|--|--|--|
| asia | 52 | 157 | 20 | 2.64 | 7.93 | 36 | 0.6 | 7.6 |
| london | 64 | 192 | 20 | 3.23 | 9.70 | 109 | 1.9 | 6.2 |
| pre | 88 | 264 | 20 | 4.44 | 13.33 | 394 | 6.7 | 4.5 |
| nyam | 175 | 525 | 20 | 8.82 | 26.45 | 1790 | 30.4 | 2.3 |
| nypm | 140 | 419 | 20 | 7.04 | 21.11 | 866 | 14.7 | 2.9 |
| close | 119 | 358 | 20 | 6.01 | 18.04 | 873 | 14.8 | 3.4 |

room(A) by year: asia: 2017:3.9 2018:5.2 2019:4.9 2020:11.5 2021:10.7 2022:10.3 2023:5.4 2024:7.1 2025:8.7 2026:11.0; london: 2017:3.8 2018:5.5 2019:4.9 2020:13.0 2021:12.1 2022:13.2 2023:8.3 2024:10.1 2025:10.0 2026:13.1; pre: 2017:4.9 2018:7.0 2019:6.2 2020:14.5 2021:15.9 2022:16.8 2023:12.2 2024:15.5 2025:14.1 2026:18.5; nyam: 2017:12.3 2018:16.2 2019:15.3 2020:25.9 2021:32.2 2022:33.9 2023:25.2 2024:29.1 2025:28.2 2026:35.0; nypm: 2017:11.2 2018:15.1 2019:13.3 2020:21.4 2021:25.2 2022:28.2 2023:18.8 2024:21.5 2025:23.2 2026:27.0; close: 2017:9.8 2018:13.6 2019:11.3 2020:21.1 2021:22.3 2022:24.4 2023:15.3 2024:18.2 2025:18.8 2026:20.2

### 10. Versus NQ
Contemporaneous correlation of h-min returns (normalised): asia: 1m 0.72 5m 0.81 15m 0.83 30m 0.84 60m 0.85; london: 1m 0.72 5m 0.76 15m 0.77 30m 0.78 60m 0.78; pre: 1m 0.66 5m 0.68 15m 0.69; nyam: 1m 0.61 5m 0.61 15m 0.60 30m 0.59; nypm: 1m 0.76 5m 0.78 15m 0.79 30m 0.79; close: 1m 0.71 5m 0.72 15m 0.74

Lead/lag (1-15 min, family 180 cells; corr of 1-min normalised returns): cells beating the family null (top 10 by |z|; "NQ->X" = NQ leads RTY):
| direction | session | lag min | corr | z | p_family | year sign share |
|--|--|--|--|--|--|--|
| NQ->RTY | asia | 1 | +0.0551 | +44.0 | 0.010 | 1.00 |
| NQ->RTY | london | 1 | +0.0276 | +23.5 | 0.010 | 1.00 |
| NQ->RTY | close | 1 | +0.0164 | +7.0 | 0.010 | 0.90 |
| NQ->RTY | nypm | 1 | +0.0088 | +5.8 | 0.010 | 0.60 |
| RTY->NQ | close | 4 | +0.0110 | +5.4 | 0.010 | 0.90 |
| RTY->NQ | london | 2 | -0.0062 | -5.2 | 0.010 | 0.80 |
| RTY->NQ | close | 1 | +0.0110 | +4.3 | 0.020 | 0.80 |
| RTY->NQ | pre | 1 | -0.0140 | -4.2 | 0.020 | 0.90 |

### 11. Map rows that become book candidates under the FROZEN rule (p_family <= .05 AND room_A(session) > 2.0)
| map row | direction | stat | p_family | room_A | year sign share | stability | 1.7% cap >= 1 contract/5min in session |
|--|--|--|--|--|--|--|--|
| AC|asia|5m | reversion | -0.021 | 0.003 | 7.9 | 0.90 |  | NO (illiquid) |
| AC|london|5m | reversion | -0.009 | 0.013 | 9.7 | 0.80 |  | yes |
| AC|pre|5m | reversion | -0.036 | 0.003 | 13.3 | 0.90 |  | yes |
| AC|pre|30m | reversion | -0.101 | 0.013 | 13.3 | 0.80 |  | yes |
| vr|asia|5 | reversion | +0.919 | 0.016 | 7.9 | 1.00 | stable | NO (illiquid) |
| vr|asia|15 | reversion | +0.888 | 0.016 | 7.9 | 1.00 | stable | NO (illiquid) |
| vr|asia|30 | reversion | +0.884 | 0.016 | 7.9 | 0.90 | stable | NO (illiquid) |
| vr|asia|60 | reversion | +0.888 | 0.016 | 7.9 | 0.90 | stable | NO (illiquid) |
| vr|asia|120 | reversion | +0.887 | 0.016 | 7.9 | 1.00 | stable | NO (illiquid) |
| vr|london|5 | reversion | +0.964 | 0.016 | 9.7 | 1.00 | stable | yes |
| vr|london|15 | reversion | +0.948 | 0.016 | 9.7 | 1.00 | stable | yes |
| vr|london|30 | reversion | +0.940 | 0.016 | 9.7 | 1.00 | stable | yes |
| vr|london|60 | reversion | +0.938 | 0.016 | 9.7 | 0.90 | stable | yes |
| vr|london|120 | reversion | +0.939 | 0.049 | 9.7 | 0.90 | stable | yes |
| vr|pre|5 | reversion | +0.946 | 0.016 | 13.3 | 0.90 | stable | yes |
| vr|pre|15 | reversion | +0.898 | 0.016 | 13.3 | 0.90 | stable | yes |
| hurst|pre | reversion | +0.476 | 0.016 | 13.3 | 1.00 | stable | yes |
| vr|nypm|5 | reversion | +0.986 | 0.016 | 21.1 | 0.70 | stable | yes |
| vr|nypm|15 | reversion | +0.975 | 0.033 | 21.1 | 0.90 | stable | yes |


## NQ - character map (CHAR-A, 2026-11-05T22:15Z)
Base: NQ CME front-month (.v.0) 1-min bars from 2013-01 to 2026-10, percent frame (multiplicative roll-adjusted), 1-min approximation (no tick path), 3451 usable label days; ET clock, sessions asia 18:00-02:00 / london 02:00-08:30 / pre 08:30-09:30 / nyam 09:30-12:00 / nypm 12:00-15:00 / close 15:00-16:55. Nulls: within-year shuffled-day (AC B=300; structure B=100 worlds; levels recomputed on the shuffled path; round numbers 60 random grid phases); p_family = Westfall-Young max-|z| over the block (AC family 153 cells, structure family 92 cells). `**` p_family<=.05, `*` <=.10. Prereg sha256 980bedf6bad3f1669de9efb93831fa4622d88577c892d9359b7f57ba93c9dbcf. Descriptive only: no PASS, nothing live.

### Plain paragraph
At 1 minute every session has negative autocorrelation (-0.029 to -0.002; bid-ask bounce / last-print noise, not a tradable edge by itself). asia: reverts at 5 min (-0.012) and trends at 60 min (+0.024). london: reverts at 5 min (-0.012). pre: reverts at 5 min (-0.031). nypm: reverts at 5 min (-0.016). close: trends at 30 min (+0.047). Day types (RTH): 48% trend days (efficiency ratio >= .5; shuffled null 46%, p_fam 0.885), 24% range days (<.25; null 26%, p_fam 1.000); the IB (09:30-10:30) is extended on one side only on 74% of days and on both on 22%, and a one-sided extension closes beyond the IB edge 65% of the time (null 64%). RTH variance ratio at 30 min 0.975 (shuffled null 1.000, p_fam 0.016); Hurst 0.503. The RTH range forms 9:30 (41%), 10:00 (24%), 11:00 (11%) of the range increments. Level reactions that beat the family null: PD|asia bounces 40% of touches (less, i.e. breaks through more than the shuffled null 46%). Failed-break follow-through beating the null: none. Room (median 3xATR14(5m) $ / round-trip cost $45 per lot): asia 6.3x, london 7.6x, pre 9.2x, nyam 17.0x, nypm 15.0x, close 14.1x (1xATR5 room 5.7x in nyam, 2.1x in asia).

### 1. Autocorrelation of h-min returns (corr(past h, next h), both inside the session), pooled; cell = corr (pre-2023 mean | 2023+ mean) p_family
| session | 1 min | 5 min | 15 min | 30 min | 60 min | 120 min |
|--|--|--|--|--|--|--|
| asia | -0.029 (-0.038|-0.014) p0.003** ys0.93 | -0.012 (-0.017|-0.014) p0.003** ys0.71 | -0.000 (-0.005|-0.002) p1.000 ys0.50 | +0.012 (+0.005|+0.007) p0.648 ys0.50 | +0.024 (+0.014|+0.016) p0.033** ys0.43 | +0.014 (-0.007|-0.005) p1.000 ys0.21 |
| london | -0.019 (-0.025|-0.006) p0.003** ys0.86 | -0.012 (-0.011|-0.017) p0.003** ys0.93 | +0.000 (+0.004|-0.009) p1.000 ys0.43 | +0.001 (+0.001|-0.000) p1.000 ys0.43 | -0.005 (-0.005|-0.008) p1.000 ys0.64 | -0.036 (-0.035|-0.034) p0.352 ys0.79 |
| pre | -0.028 (-0.029|-0.025) p0.003** ys0.93 | -0.031 (-0.034|-0.029) p0.003** ys1.00 | -0.021 (-0.022|-0.015) p0.957 ys0.57 | -0.054 (-0.019|-0.120) p0.166 ys0.86 | - | - |
| nyam | -0.002 (-0.001|-0.001) p1.000 ys0.57 | -0.001 (-0.002|+0.000) p1.000 ys0.50 | +0.005 (+0.006|+0.005) p1.000 ys0.71 | +0.016 (+0.015|+0.017) p0.970 ys0.64 | +0.023 (+0.016|+0.042) p1.000 ys0.71 | - |
| nypm | -0.010 (-0.007|-0.014) p0.003** ys0.64 | -0.016 (-0.020|-0.010) p0.003** ys0.93 | -0.004 (-0.010|+0.014) p1.000 ys0.36 | +0.014 (+0.009|+0.016) p0.993 ys0.57 | +0.027 (+0.023|+0.034) p0.884 ys0.79 | - |
| close | -0.003 (-0.009|+0.009) p1.000 ys0.64 | +0.003 (+0.003|+0.007) p1.000 ys0.50 | +0.013 (+0.021|-0.016) p0.937 ys0.64 | +0.047 (+0.051|+0.004) p0.003** ys0.79 | - | - |

Hour cells (h >= 5) beating the family null, top 14 by |z| (hour = ET hour of the decision bar):
| h | session | hour ET | corr | z | p_family | year sign share | pre-2023 | 2023+ |
|--|--|--|--|--|--|--|--|--|
| 5 | pre | 09 | -0.046 | -7.6 | 0.003 | 1.00 | -0.047 | -0.044 |
| 5 | asia | 23 | -0.028 | -6.8 | 0.003 | 0.93 | -0.034 | -0.037 |
| 5 | nypm | 14 | -0.025 | -5.6 | 0.003 | 0.79 | -0.032 | +0.001 |
| 60 | asia | 21 | +0.069 | +4.8 | 0.003 | 0.57 | +0.043 | +0.001 |
| 15 | asia | 23 | -0.035 | -4.7 | 0.003 | 0.71 | -0.023 | -0.036 |
| 120 | asia | 19 | -0.075 | -4.7 | 0.003 | 0.79 | -0.088 | -0.020 |
| 30 | close | 16 | +0.067 | +4.6 | 0.003 | 0.71 | +0.097 | -0.026 |
| 5 | london | 02 | -0.017 | -4.3 | 0.007 | 0.71 | -0.021 | -0.006 |
| 15 | pre | 09 | -0.048 | -4.2 | 0.007 | 0.64 | -0.045 | -0.056 |
| 15 | asia | 18 | -0.031 | -4.2 | 0.007 | 0.79 | -0.042 | -0.012 |
| 30 | asia | 22 | +0.042 | +4.1 | 0.010 | 0.36 | +0.039 | -0.003 |
| 5 | asia | 01 | -0.017 | -4.1 | 0.010 | 0.79 | -0.032 | +0.006 |
| 15 | london | 02 | -0.028 | -4.0 | 0.013 | 0.86 | -0.045 | +0.007 |
| 5 | asia | 19 | -0.016 | -4.0 | 0.013 | 0.64 | -0.027 | -0.009 |

### 2. Variance ratio VR(q) and Hurst (1.0 = random walk; <1 reverting; edge-bias corrected), cell = value (null) p_family
| session | VR5 | VR15 | VR30 | VR60 | VR120 | Hurst |
|--|--|--|--|--|--|--|
| asia | 0.937 (0.999) p0.016** | 0.919 (0.999) p0.016** | 0.920 (0.999) p0.016** | 0.937 (1.000) p0.016** | 0.970 (1.002) p0.213 | 0.505 (0.500) p0.213 |
| london | 0.960 (1.000) p0.016** | 0.944 (0.999) p0.016** | 0.945 (0.998) p0.016** | 0.948 (0.997) p0.016** | 0.943 (0.998) p0.016** | 0.498 (0.500) p1.000 |
| pre | 0.930 (0.999) p0.016** | 0.890 (0.999) p0.016** | - | - | - | 0.480 (0.500) p0.016** |
| nyam | 0.998 (1.001) p1.000 | 0.989 (1.000) p1.000 | 0.990 (1.000) p1.000 | - | - | 0.498 (0.500) p1.000 |
| nypm | 0.973 (1.000) p0.016** | 0.952 (0.999) p0.016** | 0.946 (0.999) p0.016** | 0.962 (0.999) p0.131 | - | 0.497 (0.500) p1.000 |
| close | 0.994 (0.999) p1.000 | 1.004 (0.998) p1.000 | 1.027 (0.997) p0.443 | - | - | 0.509 (0.499) p0.082* |
| rth | 0.988 (1.000) p0.016** | 0.974 (1.000) p0.016** | 0.975 (1.000) p0.016** | 0.985 (0.999) p1.000 | 1.008 (0.999) p1.000 | 0.503 (0.500) p1.000 |

### 3. Day types (ex-post labels of the RTH day)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| day|trend | 0.480 | 3451 | 0.460 | +2.2 | 0.885 | 0.64 | 0.477 | 0.486 | stable |
| day|range | 0.242 | 3451 | 0.256 | -1.7 | 1.000 | 0.71 | 0.240 | 0.247 | stable |
| day|er | 0.476 | 3451 | 0.463 | +2.6 | 0.443 | 0.71 | 0.475 | 0.476 | stable |
| day|ib_none | 0.042 | 3451 | 0.025 | +7.0 | 0.016** | 0.79 | 0.045 | 0.037 | stable |
| day|ib_one | 0.737 | 3451 | 0.719 | +2.3 | 0.869 | 0.71 | 0.726 | 0.765 | stable |
| day|ib_both | 0.221 | 3451 | 0.256 | -4.6 | 0.016** | 0.79 | 0.230 | 0.198 | stable |
| day|ib_one_closebeyond | 0.652 | 2542 | 0.644 | +0.8 | 1.000 | 0.57 | 0.666 | 0.617 | unstable |

### 4. 1A -> 2A continuation vs give-back-half from the session open (A = 3 x ATR14(5m)); value = P(continue | resolved)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| cont|asia | 0.372 | 1813 | 0.347 | +2.6 | 0.492 | 0.57 | 0.363 | 0.380 | unstable |
| cont|london | 0.349 | 3427 | 0.354 | -0.6 | 1.000 | 0.57 | 0.354 | 0.336 | REGIME(2023+ only) |
| cont|pre | 0.348 | 1261 | 0.325 | +2.2 | 0.934 | 0.50 | 0.320 | 0.397 | REGIME(2023+ only) |
| cont|nyam | 0.353 | 3380 | 0.344 | +1.1 | 1.000 | 0.64 | 0.353 | 0.351 | stable |
| cont|nypm | 0.303 | 1238 | 0.273 | +3.1 | 0.164 | 0.86 | 0.294 | 0.327 | stable |
| cont|close | 0.310 | 1053 | 0.264 | +3.5 | 0.066* | 0.71 | 0.331 | 0.250 | stable |
| cont|rth | 0.354 | 3428 | 0.345 | +1.2 | 1.000 | 0.64 | 0.356 | 0.351 | stable |

### 5. Gap fill by size bucket (b0 .05-.10, b1 .10-.25, b2 .25-.50, b3 >.50 of the 20-day mean RTH range); day = filled during RTH, h1 = within 60 min
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| gap|b0|day | 0.885 | 358 | 0.901 | -0.9 | 1.000 | 0.71 | 0.880 | 0.891 | stable |
| gap|b0|h1 | 0.818 | 358 | 0.826 | -0.4 | 1.000 | 0.57 | 0.808 | 0.832 | unstable |
| gap|b1|day | 0.760 | 880 | 0.772 | -0.8 | 1.000 | 0.57 | 0.769 | 0.737 | unstable |
| gap|b1|h1 | 0.611 | 880 | 0.612 | -0.1 | 1.000 | 0.29 | 0.622 | 0.590 | REGIME(2023+ only) |
| gap|b2|day | 0.545 | 950 | 0.550 | -0.3 | 1.000 | 0.64 | 0.551 | 0.524 | REGIME(2023+ only) |
| gap|b2|h1 | 0.332 | 950 | 0.306 | +1.8 | 1.000 | 0.57 | 0.335 | 0.325 | unstable |
| gap|b3|day | 0.308 | 919 | 0.262 | +3.6 | 0.066* | 0.71 | 0.317 | 0.303 | stable |
| gap|b3|h1 | 0.091 | 919 | 0.071 | +2.7 | 0.393 | 0.64 | 0.094 | 0.092 | stable |

### 6. Level reaction: first touch -> bounce (0.5A reverse) vs break-through (0.5A beyond) within 60 min; value = P(bounce)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| rx|PD|asia | 0.402 | 1288 | 0.465 | -4.8 | 0.016** | 0.86 | 0.416 | 0.400 | stable |
| rx|PD|london | 0.488 | 1605 | 0.489 | -0.0 | 1.000 | 0.50 | 0.489 | 0.493 | unstable |
| rx|PD|pre | 0.506 | 846 | 0.487 | +1.1 | 1.000 | 0.50 | 0.526 | 0.464 | unstable |
| rx|PD|nyam | 0.488 | 2205 | 0.497 | -0.8 | 1.000 | 0.71 | 0.491 | 0.479 | stable |
| rx|PD|nypm | 0.502 | 1229 | 0.494 | +0.6 | 1.000 | 0.64 | 0.506 | 0.502 | stable |
| rx|PD|close | 0.481 | 756 | 0.492 | -0.5 | 1.000 | 0.50 | 0.465 | 0.528 | unstable |
| rx|ON|nyam | 0.500 | 3495 | 0.497 | +0.3 | 1.000 | 0.50 | 0.499 | 0.500 | unstable |
| rx|ON|nypm | 0.501 | 1616 | 0.497 | +0.3 | 1.000 | 0.50 | 0.507 | 0.494 | unstable |
| rx|ON|close | 0.520 | 1015 | 0.495 | +1.5 | 1.000 | 0.57 | 0.528 | 0.498 | unstable |
| rx|IB|nyam | 0.471 | 2512 | 0.497 | -3.1 | 0.213 | 0.79 | 0.463 | 0.494 | stable |
| rx|IB|nypm | 0.500 | 2038 | 0.497 | +0.2 | 1.000 | 0.64 | 0.490 | 0.525 | REGIME(2023+ only) |
| rx|IB|close | 0.500 | 1247 | 0.496 | +0.3 | 1.000 | 0.43 | 0.491 | 0.526 | REGIME(2023+ only) |
| rx|VW1|nyam | 0.498 | 5117 | 0.497 | +0.0 | 1.000 | 0.57 | 0.495 | 0.502 | REGIME(2023+ only) |
| rx|VW1|nypm | 0.491 | 3156 | 0.498 | -0.8 | 1.000 | 0.71 | 0.484 | 0.511 | stable |
| rx|VW1|close | 0.496 | 2194 | 0.495 | +0.2 | 1.000 | 0.43 | 0.487 | 0.523 | REGIME(2023+ only) |
| rx|VW2|nyam | 0.513 | 3607 | 0.503 | +1.2 | 1.000 | 0.50 | 0.507 | 0.528 | unstable |
| rx|VW2|nypm | 0.479 | 1861 | 0.498 | -1.9 | 1.000 | 0.71 | 0.473 | 0.489 | stable |
| rx|VW2|close | 0.489 | 1220 | 0.497 | -0.5 | 1.000 | 0.57 | 0.488 | 0.502 | unstable |
| rx|RN|asia | 0.486 | 31698 | 0.492 | -1.9 | 1.000 | 0.71 | 0.477 | 0.497 | stable |
| rx|RN|london | 0.493 | 40931 | 0.495 | -0.8 | 1.000 | 0.57 | 0.485 | 0.497 | unstable |
| rx|RN|pre | 0.492 | 10530 | 0.499 | -1.3 | 1.000 | 0.64 | 0.488 | 0.501 | stable |
| rx|RN|nyam | 0.497 | 41120 | 0.499 | -0.7 | 1.000 | 0.71 | 0.488 | 0.503 | stable |
| rx|RN|nypm | 0.502 | 29883 | 0.499 | +1.0 | 1.000 | 0.57 | 0.503 | 0.502 | unstable |
| rx|RN|close | 0.491 | 12000 | 0.495 | -1.1 | 1.000 | 0.50 | 0.485 | 0.499 | unstable |

### 7. Failed break (close .25A beyond, back inside within 10 bars): fade follow-through P(0.5A back before 0.5A out)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| fb|PD|asia | 0.508 | 730 | 0.495 | +0.8 | 1.000 | 0.50 | 0.481 | 0.554 | REGIME(2023+ only) |
| fb|PD|london | 0.485 | 1107 | 0.500 | -1.0 | 1.000 | 0.57 | 0.481 | 0.504 | unstable |
| fb|PD|pre | 0.497 | 493 | 0.499 | -0.1 | 1.000 | 0.57 | 0.496 | 0.539 | unstable |
| fb|PD|nyam | 0.519 | 1445 | 0.500 | +1.3 | 1.000 | 0.71 | 0.519 | 0.520 | stable |
| fb|PD|nypm | 0.520 | 766 | 0.500 | +1.1 | 1.000 | 0.64 | 0.529 | 0.488 | stable |
| fb|PD|close | 0.493 | 383 | 0.501 | -0.3 | 1.000 | 0.57 | 0.467 | 0.570 | unstable |
| fb|ON|nyam | 0.530 | 1765 | 0.501 | +2.5 | 0.557 | 0.71 | 0.519 | 0.559 | stable |
| fb|ON|nypm | 0.523 | 982 | 0.501 | +1.3 | 1.000 | 0.57 | 0.529 | 0.516 | unstable |
| fb|ON|close | 0.500 | 522 | 0.498 | +0.1 | 1.000 | 0.43 | 0.517 | 0.458 | unstable |
| fb|IB|nyam | 0.494 | 705 | 0.499 | -0.3 | 1.000 | 0.50 | 0.486 | 0.514 | unstable |
| fb|IB|nypm | 0.504 | 1180 | 0.503 | +0.1 | 1.000 | 0.57 | 0.507 | 0.499 | unstable |
| fb|IB|close | 0.486 | 634 | 0.499 | -0.7 | 1.000 | 0.36 | 0.474 | 0.510 | unstable |

### 8. Where the range forms
RTH range increments by bin: 9:30 41.4%, 10:00 23.7%, 11:00 10.8%, 12:00 6.3%, 13:00 5.2%, 14:00 5.9%, 15:00 6.7%
Label-day range increments by ET hour (percent of the day): 00h 1.4, 01h 1.9, 02h 2.9, 03h 5.2, 04h 3.7, 05h 2.6, 06h 2.0, 07h 2.5, 08h 5.1, 09h 12.7, 10h 10.7, 11h 5.9, 12h 3.6, 13h 3.1, 14h 3.7, 15h 4.3, 16h 2.0, 18h 9.1, 19h 4.3, 20h 5.6, 21h 4.0, 22h 2.4, 23h 1.5

### 9. Room and liquidity (all years, raw-frame $, 1 lot)
| session | ATR14(5m) $ | A=3xATR5 $ | RT cost $ | room(1 ATR5) | room(A) | median 5-min vol | 1.7% cap (contracts/5min) | lots for $1,200 at 3xATR5 stop |
|--|--|--|--|--|--|--|--|--|
| asia | 95 | 285 | 45 | 2.12 | 6.35 | 172 | 2.9 | 4.2 |
| london | 114 | 341 | 45 | 2.53 | 7.60 | 387 | 6.6 | 3.5 |
| pre | 137 | 411 | 45 | 3.05 | 9.16 | 1057 | 18.0 | 2.9 |
| nyam | 254 | 761 | 45 | 5.66 | 16.98 | 5000 | 85.0 | 1.6 |
| nypm | 225 | 674 | 45 | 5.01 | 15.03 | 2483 | 42.2 | 1.8 |
| close | 211 | 633 | 45 | 4.70 | 14.11 | 1796 | 30.5 | 1.9 |

room(A) by year: asia: 2013:1.2 2014:1.4 2015:2.1 2016:2.3 2017:2.0 2018:5.0 2019:5.0 2020:12.2 2021:9.5 2022:14.0 2023:8.1 2024:10.5 2025:15.5 2026:26.1; london: 2013:1.6 2014:2.0 2015:3.1 2016:3.1 2017:2.2 2018:5.3 2019:5.2 2020:12.8 2021:10.8 2022:18.0 2023:11.0 2024:13.1 2025:17.2 2026:27.3; pre: 2013:2.0 2014:2.6 2015:3.7 2016:3.1 2017:2.7 2018:6.2 2019:6.4 2020:13.6 2021:12.9 2022:22.0 2023:15.1 2024:17.7 2025:22.5 2026:32.8; nyam: 2013:4.1 2014:5.5 2015:7.2 2016:6.4 2017:5.8 2018:12.8 2019:11.5 2020:25.2 2021:25.5 2022:42.7 2023:28.8 2024:33.1 2025:41.1 2026:58.6; nypm: 2013:3.4 2014:4.6 2015:6.2 2016:5.7 2017:4.9 2018:12.0 2019:9.5 2020:21.8 2021:21.3 2022:35.7 2023:24.3 2024:29.2 2025:35.6 2026:45.2; close: 2013:3.5 2014:4.2 2015:6.2 2016:5.5 2017:4.6 2018:11.4 2019:9.0 2020:22.4 2021:19.1 2022:32.2 2023:21.0 2024:25.5 2025:30.0 2026:36.0

### 11. Map rows that become book candidates under the FROZEN rule (p_family <= .05 AND room_A(session) > 2.0)
| map row | direction | stat | p_family | room_A | year sign share | stability | 1.7% cap >= 1 contract/5min in session |
|--|--|--|--|--|--|--|--|
| AC|asia|5m | reversion | -0.012 | 0.003 | 6.3 | 0.71 |  | yes |
| AC|london|5m | reversion | -0.012 | 0.003 | 7.6 | 0.93 |  | yes |
| AC|pre|5m | reversion | -0.031 | 0.003 | 9.2 | 1.00 |  | yes |
| AC|nypm|5m | reversion | -0.016 | 0.003 | 15.0 | 0.93 |  | yes |
| AC|close|30m | momentum | +0.047 | 0.003 | 14.1 | 0.79 |  | yes |
| AC|asia|60m | momentum | +0.024 | 0.033 | 6.3 | 0.43 |  | yes |
| rx|PD|asia | level-break | +0.402 | 0.016 | 6.3 | 0.86 | stable | yes |
| vr|asia|5 | reversion | +0.937 | 0.016 | 6.3 | 1.00 | stable | yes |
| vr|asia|15 | reversion | +0.919 | 0.016 | 6.3 | 0.93 | stable | yes |
| vr|asia|30 | reversion | +0.920 | 0.016 | 6.3 | 0.93 | stable | yes |
| vr|asia|60 | reversion | +0.937 | 0.016 | 6.3 | 0.71 | stable | yes |
| vr|london|5 | reversion | +0.960 | 0.016 | 7.6 | 1.00 | stable | yes |
| vr|london|15 | reversion | +0.944 | 0.016 | 7.6 | 1.00 | stable | yes |
| vr|london|30 | reversion | +0.945 | 0.016 | 7.6 | 1.00 | stable | yes |
| vr|london|60 | reversion | +0.948 | 0.016 | 7.6 | 0.93 | stable | yes |
| vr|london|120 | reversion | +0.943 | 0.016 | 7.6 | 0.79 | stable | yes |
| vr|pre|5 | reversion | +0.930 | 0.016 | 9.2 | 0.86 | stable | yes |
| vr|pre|15 | reversion | +0.890 | 0.016 | 9.2 | 1.00 | stable | yes |
| hurst|pre | reversion | +0.480 | 0.016 | 9.2 | 0.93 | stable | yes |
| vr|nypm|5 | reversion | +0.973 | 0.016 | 15.0 | 0.93 | stable | yes |
| vr|nypm|15 | reversion | +0.952 | 0.016 | 15.0 | 1.00 | stable | yes |
| vr|nypm|30 | reversion | +0.946 | 0.016 | 15.0 | 0.86 | stable | yes |
| vr|rth|5 | reversion | +0.988 | 0.016 | 17.0 | 0.64 | stable | yes |
| vr|rth|15 | reversion | +0.974 | 0.016 | 17.0 | 0.86 | stable | yes |
| vr|rth|30 | reversion | +0.975 | 0.016 | 17.0 | 0.79 | stable | yes |


## ES - character map (CHAR-A, 2026-11-05T22:15Z)
Base: ES CME front-month (.v.0) 1-min bars from 2013-01 to 2026-10, percent frame (multiplicative roll-adjusted), 1-min approximation (no tick path), 3494 usable label days; ET clock, sessions asia 18:00-02:00 / london 02:00-08:30 / pre 08:30-09:30 / nyam 09:30-12:00 / nypm 12:00-15:00 / close 15:00-16:55. Nulls: within-year shuffled-day (AC B=300; structure B=100 worlds; levels recomputed on the shuffled path; round numbers 60 random grid phases); p_family = Westfall-Young max-|z| over the block (AC family 153 cells, structure family 92 cells). `**` p_family<=.05, `*` <=.10. Prereg sha256 980bedf6bad3f1669de9efb93831fa4622d88577c892d9359b7f57ba93c9dbcf. Descriptive only: no PASS, nothing live.

### Plain paragraph
At 1 minute every session has negative autocorrelation (-0.085 to -0.026; bid-ask bounce / last-print noise, not a tradable edge by itself). asia: reverts at 5/15 min (-0.029, -0.011). london: reverts at 5/15 min (-0.029, -0.016). pre: reverts at 5 min (-0.038). nyam: reverts at 5 min (-0.016). nypm: reverts at 5 min (-0.026). close: trends at 30 min (+0.052). Day types (RTH): 47% trend days (efficiency ratio >= .5; shuffled null 46%, p_fam 1.000), 26% range days (<.25; null 26%, p_fam 1.000); the IB (09:30-10:30) is extended on one side only on 70% of days and on both on 28%, and a one-sided extension closes beyond the IB edge 67% of the time (null 68%). RTH variance ratio at 30 min 0.915 (shuffled null 1.000, p_fam 0.016); Hurst 0.500. The RTH range forms 9:30 (36%), 10:00 (24%), 11:00 (12%) of the range increments. Level reactions that beat the family null: ON|nypm bounces 54% of touches (more than the shuffled null 50%); ON|close bounces 54% of touches (more than the shuffled null 50%). Failed-break follow-through beating the null: none. Room (median 3xATR14(5m) $ / round-trip cost $42 per lot): asia 4.6x, london 5.4x, pre 6.6x, nyam 10.8x, nypm 10.0x, close 10.1x (1xATR5 room 3.6x in nyam, 1.5x in asia).

### 1. Autocorrelation of h-min returns (corr(past h, next h), both inside the session), pooled; cell = corr (pre-2023 mean | 2023+ mean) p_family
| session | 1 min | 5 min | 15 min | 30 min | 60 min | 120 min |
|--|--|--|--|--|--|--|
| asia | -0.085 (-0.107|-0.034) p0.003** ys1.00 | -0.029 (-0.042|-0.022) p0.003** ys1.00 | -0.011 (-0.016|-0.018) p0.023** ys0.64 | -0.002 (-0.008|-0.009) p1.000 ys0.57 | +0.006 (-0.008|+0.011) p1.000 ys0.43 | +0.008 (-0.013|+0.012) p1.000 ys0.36 |
| london | -0.062 (-0.080|-0.015) p0.003** ys1.00 | -0.029 (-0.033|-0.026) p0.003** ys1.00 | -0.016 (-0.018|-0.014) p0.003** ys0.79 | -0.009 (-0.018|+0.009) p0.934 ys0.64 | -0.015 (-0.021|-0.002) p0.930 ys0.71 | -0.037 (-0.041|-0.015) p0.086* ys0.57 |
| pre | -0.055 (-0.067|-0.032) p0.003** ys1.00 | -0.038 (-0.051|-0.017) p0.003** ys0.93 | -0.027 (-0.029|-0.024) p0.233 ys0.64 | -0.043 (-0.006|-0.114) p0.744 ys0.71 | - | - |
| nyam | -0.026 (-0.034|-0.011) p0.003** ys0.79 | -0.016 (-0.020|-0.006) p0.003** ys0.93 | +0.003 (-0.000|+0.005) p1.000 ys0.57 | +0.006 (-0.010|+0.035) p1.000 ys0.43 | +0.019 (+0.004|+0.050) p1.000 ys0.57 | - |
| nypm | -0.038 (-0.047|-0.019) p0.003** ys0.86 | -0.026 (-0.035|-0.014) p0.003** ys0.93 | -0.006 (-0.014|+0.012) p1.000 ys0.43 | +0.020 (+0.011|+0.032) p0.179 ys0.64 | +0.024 (+0.015|+0.034) p0.977 ys0.57 | - |
| close | -0.027 (-0.043|+0.001) p0.003** ys0.79 | -0.009 (-0.015|+0.002) p0.731 ys0.64 | +0.015 (+0.023|-0.017) p0.777 ys0.64 | +0.052 (+0.061|-0.014) p0.003** ys0.64 | - | - |

Hour cells (h >= 5) beating the family null, top 14 by |z| (hour = ET hour of the decision bar):
| h | session | hour ET | corr | z | p_family | year sign share | pre-2023 | 2023+ |
|--|--|--|--|--|--|--|--|--|
| 5 | asia | 23 | -0.044 | -11.8 | 0.003 | 0.93 | -0.059 | -0.034 |
| 5 | london | 07 | -0.043 | -11.1 | 0.003 | 0.93 | -0.048 | -0.037 |
| 5 | asia | 01 | -0.036 | -8.7 | 0.003 | 0.79 | -0.060 | +0.004 |
| 5 | asia | 00 | -0.035 | -8.6 | 0.003 | 0.86 | -0.053 | -0.029 |
| 5 | london | 05 | -0.031 | -8.6 | 0.003 | 0.86 | -0.028 | -0.044 |
| 5 | asia | 22 | -0.034 | -8.4 | 0.003 | 0.86 | -0.048 | -0.042 |
| 5 | asia | 18 | -0.034 | -8.1 | 0.003 | 0.86 | -0.049 | -0.027 |
| 5 | london | 02 | -0.031 | -7.2 | 0.003 | 0.86 | -0.041 | -0.012 |
| 15 | london | 02 | -0.053 | -7.2 | 0.003 | 0.79 | -0.077 | +0.003 |
| 5 | nypm | 12 | -0.031 | -7.1 | 0.003 | 0.86 | -0.036 | -0.032 |
| 5 | london | 06 | -0.026 | -7.1 | 0.003 | 0.86 | -0.042 | -0.001 |
| 5 | asia | 19 | -0.029 | -6.9 | 0.003 | 0.64 | -0.050 | -0.011 |
| 5 | pre | 09 | -0.041 | -6.7 | 0.003 | 0.86 | -0.048 | -0.034 |
| 30 | close | 16 | +0.090 | +6.6 | 0.003 | 0.79 | +0.144 | -0.054 |

### 2. Variance ratio VR(q) and Hurst (1.0 = random walk; <1 reverting; edge-bias corrected), cell = value (null) p_family
| session | VR5 | VR15 | VR30 | VR60 | VR120 | Hurst |
|--|--|--|--|--|--|--|
| asia | 0.846 (0.999) p0.016** | 0.807 (0.999) p0.016** | 0.799 (0.999) p0.016** | 0.803 (0.999) p0.016** | 0.816 (1.001) p0.016** | 0.494 (0.500) p0.016** |
| london | 0.890 (0.999) p0.016** | 0.852 (0.999) p0.016** | 0.840 (0.998) p0.016** | 0.835 (0.997) p0.016** | 0.825 (0.997) p0.016** | 0.489 (0.500) p0.016** |
| pre | 0.893 (1.000) p0.016** | 0.843 (0.999) p0.016** | - | - | - | 0.474 (0.500) p0.016** |
| nyam | 0.953 (1.001) p0.016** | 0.928 (1.000) p0.016** | 0.927 (1.001) p0.016** | - | - | 0.492 (0.500) p0.049** |
| nypm | 0.924 (0.999) p0.016** | 0.892 (0.999) p0.016** | 0.884 (0.998) p0.016** | 0.905 (0.998) p0.016** | - | 0.495 (0.500) p0.787 |
| close | 0.951 (0.999) p0.016** | 0.944 (0.999) p0.016** | 0.971 (0.999) p0.770 | - | - | 0.505 (0.500) p1.000 |
| rth | 0.943 (1.000) p0.016** | 0.915 (1.000) p0.016** | 0.915 (1.000) p0.016** | 0.923 (0.999) p0.016** | 0.947 (0.999) p0.016** | 0.500 (0.500) p1.000 |

### 3. Day types (ex-post labels of the RTH day)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| day|trend | 0.468 | 3494 | 0.460 | +0.9 | 1.000 | 0.64 | 0.467 | 0.470 | stable |
| day|range | 0.262 | 3494 | 0.257 | +0.8 | 1.000 | 0.64 | 0.257 | 0.277 | stable |
| day|er | 0.466 | 3494 | 0.463 | +0.8 | 1.000 | 0.57 | 0.467 | 0.463 | unstable |
| day|ib_none | 0.023 | 3494 | 0.014 | +4.8 | 0.016** | 0.93 | 0.025 | 0.020 | stable |
| day|ib_one | 0.696 | 3494 | 0.661 | +4.4 | 0.016** | 0.79 | 0.700 | 0.691 | stable |
| day|ib_both | 0.280 | 3494 | 0.326 | -5.6 | 0.016** | 0.79 | 0.276 | 0.289 | stable |
| day|ib_one_closebeyond | 0.674 | 2433 | 0.685 | -1.2 | 1.000 | 0.71 | 0.679 | 0.665 | stable |

### 4. 1A -> 2A continuation vs give-back-half from the session open (A = 3 x ATR14(5m)); value = P(continue | resolved)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| cont|asia | 0.339 | 1719 | 0.341 | -0.3 | 1.000 | 0.43 | 0.343 | 0.315 | REGIME(2023+ only) |
| cont|london | 0.321 | 3478 | 0.343 | -2.9 | 0.213 | 0.71 | 0.315 | 0.334 | stable |
| cont|pre | 0.334 | 1146 | 0.309 | +2.4 | 0.721 | 0.64 | 0.311 | 0.373 | stable |
| cont|nyam | 0.329 | 3315 | 0.338 | -1.1 | 1.000 | 0.57 | 0.330 | 0.328 | unstable |
| cont|nypm | 0.293 | 1364 | 0.282 | +1.2 | 1.000 | 0.64 | 0.280 | 0.335 | REGIME(2023+ only) |
| cont|close | 0.276 | 1179 | 0.261 | +1.1 | 1.000 | 0.57 | 0.291 | 0.221 | unstable |
| cont|rth | 0.334 | 3450 | 0.339 | -0.8 | 1.000 | 0.64 | 0.333 | 0.336 | stable |

### 5. Gap fill by size bucket (b0 .05-.10, b1 .10-.25, b2 .25-.50, b3 >.50 of the 20-day mean RTH range); day = filled during RTH, h1 = within 60 min
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| gap|b0|day | 0.889 | 333 | 0.899 | -0.5 | 1.000 | 0.43 | 0.867 | 0.934 | unstable |
| gap|b0|h1 | 0.811 | 333 | 0.803 | +0.3 | 1.000 | 0.64 | 0.775 | 0.876 | REGIME(2023+ only) |
| gap|b1|day | 0.782 | 866 | 0.769 | +0.9 | 1.000 | 0.50 | 0.786 | 0.775 | unstable |
| gap|b1|h1 | 0.605 | 866 | 0.571 | +2.0 | 0.951 | 0.64 | 0.619 | 0.571 | stable |
| gap|b2|day | 0.542 | 984 | 0.549 | -0.5 | 1.000 | 0.50 | 0.535 | 0.557 | unstable |
| gap|b2|h1 | 0.268 | 984 | 0.258 | +0.8 | 1.000 | 0.50 | 0.275 | 0.251 | unstable |
| gap|b3|day | 0.271 | 986 | 0.242 | +2.3 | 0.787 | 0.71 | 0.263 | 0.303 | stable |
| gap|b3|h1 | 0.070 | 986 | 0.045 | +4.3 | 0.016** | 0.79 | 0.066 | 0.083 | stable |

### 6. Level reaction: first touch -> bounce (0.5A reverse) vs break-through (0.5A beyond) within 60 min; value = P(bounce)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| rx|PD|asia | 0.447 | 1341 | 0.470 | -1.8 | 1.000 | 0.57 | 0.449 | 0.466 | unstable |
| rx|PD|london | 0.516 | 1734 | 0.495 | +1.9 | 0.984 | 0.64 | 0.519 | 0.507 | stable |
| rx|PD|pre | 0.520 | 927 | 0.495 | +1.5 | 1.000 | 0.71 | 0.521 | 0.519 | stable |
| rx|PD|nyam | 0.510 | 2070 | 0.499 | +1.0 | 1.000 | 0.64 | 0.517 | 0.490 | stable |
| rx|PD|nypm | 0.506 | 1303 | 0.498 | +0.5 | 1.000 | 0.50 | 0.516 | 0.485 | unstable |
| rx|PD|close | 0.529 | 859 | 0.497 | +1.9 | 0.984 | 0.71 | 0.538 | 0.496 | stable |
| rx|ON|nyam | 0.516 | 3187 | 0.501 | +1.5 | 1.000 | 0.64 | 0.523 | 0.501 | stable |
| rx|ON|nypm | 0.536 | 1682 | 0.497 | +3.7 | 0.033** | 0.93 | 0.544 | 0.511 | stable |
| rx|ON|close | 0.543 | 1104 | 0.498 | +3.4 | 0.049** | 0.71 | 0.534 | 0.562 | stable |
| rx|IB|nyam | 0.489 | 2781 | 0.499 | -1.0 | 1.000 | 0.79 | 0.490 | 0.486 | stable |
| rx|IB|nypm | 0.528 | 2231 | 0.500 | +3.1 | 0.098* | 0.86 | 0.519 | 0.552 | stable |
| rx|IB|close | 0.513 | 1408 | 0.498 | +1.3 | 1.000 | 0.64 | 0.515 | 0.512 | stable |
| rx|VW1|nyam | 0.490 | 5294 | 0.498 | -1.2 | 1.000 | 0.64 | 0.489 | 0.490 | stable |
| rx|VW1|nypm | 0.505 | 3384 | 0.498 | +0.8 | 1.000 | 0.50 | 0.514 | 0.493 | unstable |
| rx|VW1|close | 0.515 | 2501 | 0.498 | +1.9 | 0.984 | 0.64 | 0.510 | 0.535 | stable |
| rx|VW2|nyam | 0.512 | 3925 | 0.505 | +0.9 | 1.000 | 0.43 | 0.509 | 0.521 | unstable |
| rx|VW2|nypm | 0.490 | 2209 | 0.501 | -1.3 | 1.000 | 0.79 | 0.477 | 0.521 | stable |
| rx|VW2|close | 0.491 | 1402 | 0.500 | -0.8 | 1.000 | 0.50 | 0.494 | 0.482 | unstable |
| rx|RN|asia | 0.492 | 32165 | 0.494 | -0.6 | 1.000 | 0.57 | 0.492 | 0.488 | unstable |
| rx|RN|london | 0.494 | 43305 | 0.497 | -1.0 | 1.000 | 0.71 | 0.495 | 0.493 | stable |
| rx|RN|pre | 0.492 | 9961 | 0.499 | -1.3 | 1.000 | 0.64 | 0.484 | 0.498 | stable |
| rx|RN|nyam | 0.502 | 37856 | 0.501 | +0.5 | 1.000 | 0.57 | 0.501 | 0.504 | unstable |
| rx|RN|nypm | 0.504 | 31062 | 0.499 | +1.5 | 1.000 | 0.57 | 0.503 | 0.505 | unstable |
| rx|RN|close | 0.497 | 13168 | 0.499 | -0.9 | 1.000 | 0.71 | 0.495 | 0.501 | stable |

### 7. Failed break (close .25A beyond, back inside within 10 bars): fade follow-through P(0.5A back before 0.5A out)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| fb|PD|asia | 0.496 | 705 | 0.498 | -0.1 | 1.000 | 0.57 | 0.483 | 0.519 | unstable |
| fb|PD|london | 0.498 | 1141 | 0.497 | +0.1 | 1.000 | 0.50 | 0.490 | 0.500 | REGIME(2023+ only) |
| fb|PD|pre | 0.483 | 476 | 0.498 | -0.7 | 1.000 | 0.57 | 0.479 | 0.523 | unstable |
| fb|PD|nyam | 0.508 | 1326 | 0.499 | +0.6 | 1.000 | 0.64 | 0.525 | 0.469 | stable |
| fb|PD|nypm | 0.490 | 817 | 0.501 | -0.6 | 1.000 | 0.57 | 0.496 | 0.473 | unstable |
| fb|PD|close | 0.505 | 424 | 0.498 | +0.3 | 1.000 | 0.57 | 0.496 | 0.517 | REGIME(2023+ only) |
| fb|ON|nyam | 0.516 | 1463 | 0.499 | +1.2 | 1.000 | 0.57 | 0.511 | 0.527 | unstable |
| fb|ON|nypm | 0.519 | 968 | 0.499 | +1.3 | 1.000 | 0.50 | 0.506 | 0.531 | unstable |
| fb|ON|close | 0.480 | 531 | 0.496 | -0.9 | 1.000 | 0.64 | 0.466 | 0.510 | stable |
| fb|IB|nyam | 0.495 | 745 | 0.501 | -0.4 | 1.000 | 0.57 | 0.517 | 0.448 | REGIME(2023+ only) |
| fb|IB|nypm | 0.494 | 1244 | 0.502 | -0.6 | 1.000 | 0.57 | 0.483 | 0.519 | unstable |
| fb|IB|close | 0.506 | 725 | 0.498 | +0.4 | 1.000 | 0.57 | 0.506 | 0.513 | unstable |

### 8. Where the range forms
RTH range increments by bin: 9:30 35.8%, 10:00 24.1%, 11:00 11.6%, 12:00 7.1%, 13:00 5.9%, 14:00 7.0%, 15:00 8.5%
Label-day range increments by ET hour (percent of the day): 00h 1.4, 01h 1.9, 02h 3.1, 03h 5.6, 04h 3.8, 05h 2.7, 06h 2.4, 07h 2.6, 08h 5.4, 09h 9.3, 10h 9.1, 11h 5.6, 12h 3.7, 13h 3.4, 14h 4.2, 15h 5.3, 16h 1.5, 18h 10.2, 19h 4.7, 20h 5.7, 21h 4.2, 22h 2.4, 23h 1.6

### 9. Room and liquidity (all years, raw-frame $, 1 lot)
| session | ATR14(5m) $ | A=3xATR5 $ | RT cost $ | room(1 ATR5) | room(A) | median 5-min vol | 1.7% cap (contracts/5min) | lots for $1,200 at 3xATR5 stop |
|--|--|--|--|--|--|--|--|--|
| asia | 64 | 193 | 42 | 1.52 | 4.56 | 409 | 7.0 | 6.2 |
| london | 76 | 229 | 42 | 1.81 | 5.42 | 1203 | 20.5 | 5.2 |
| pre | 93 | 280 | 42 | 2.21 | 6.62 | 3358 | 57.1 | 4.3 |
| nyam | 152 | 457 | 42 | 3.59 | 10.78 | 16349 | 277.9 | 2.6 |
| nypm | 141 | 423 | 42 | 3.33 | 10.00 | 8315 | 141.4 | 2.8 |
| close | 142 | 426 | 42 | 3.35 | 10.05 | 8111 | 137.9 | 2.8 |

room(A) by year: asia: 2013:2.0 2014:2.0 2015:2.7 2016:2.8 2017:2.1 2018:4.2 2019:4.1 2020:8.9 2021:6.0 2022:9.5 2023:4.9 2024:5.5 2025:8.6 2026:10.8; london: 2013:2.5 2014:2.7 2015:3.9 2016:3.7 2017:2.4 2018:4.5 2019:4.2 2020:9.6 2021:6.7 2022:12.1 2023:6.7 2024:6.7 2025:9.5 2026:11.6; pre: 2013:3.2 2014:3.5 2015:4.6 2016:4.0 2017:2.8 2018:5.3 2019:5.1 2020:9.9 2021:7.8 2022:14.7 2023:9.4 2024:9.5 2025:12.8 2026:15.2; nyam: 2013:5.1 2014:5.9 2015:7.5 2016:6.4 2017:4.8 2018:9.2 2019:8.5 2020:15.3 2021:13.0 2022:25.5 2023:15.6 2024:16.1 2025:21.5 2026:25.3; nypm: 2013:4.3 2014:5.1 2015:6.6 2016:5.8 2017:4.3 2018:9.0 2019:7.5 2020:13.5 2021:11.3 2022:22.8 2023:14.1 2024:15.3 2025:19.9 2026:21.7; close: 2013:4.6 2014:4.9 2015:6.7 2016:5.9 2017:4.3 2018:9.5 2019:7.5 2020:15.4 2021:11.3 2022:22.0 2023:13.1 2024:14.6 2025:17.6 2026:18.0

### 10. Versus NQ
Contemporaneous correlation of h-min returns (normalised): asia: 1m 0.81 5m 0.91 15m 0.93 30m 0.94 60m 0.95; london: 1m 0.85 5m 0.91 15m 0.92 30m 0.93 60m 0.93; pre: 1m 0.85 5m 0.89 15m 0.89; nyam: 1m 0.87 5m 0.88 15m 0.88 30m 0.87; nypm: 1m 0.90 5m 0.93 15m 0.93 30m 0.93; close: 1m 0.88 5m 0.91 15m 0.92

Lead/lag (1-15 min, family 180 cells; corr of 1-min normalised returns): cells beating the family null (top 10 by |z|; "NQ->X" = NQ leads ES):
| direction | session | lag min | corr | z | p_family | year sign share |
|--|--|--|--|--|--|--|
| ES->NQ | asia | 1 | +0.0102 | +10.7 | 0.010 | 0.71 |
| NQ->ES | nypm | 1 | -0.0104 | -9.1 | 0.010 | 0.71 |
| NQ->ES | london | 2 | -0.0065 | -7.3 | 0.010 | 0.86 |
| ES->NQ | pre | 1 | -0.0149 | -7.2 | 0.010 | 0.86 |
| NQ->ES | pre | 1 | -0.0138 | -6.4 | 0.010 | 0.79 |
| ES->NQ | close | 1 | +0.0105 | +6.1 | 0.010 | 0.71 |
| NQ->ES | nypm | 3 | -0.0072 | -5.2 | 0.010 | 0.86 |
| NQ->ES | nypm | 2 | -0.0066 | -5.2 | 0.010 | 0.71 |
| NQ->ES | asia | 2 | -0.0050 | -5.1 | 0.010 | 0.86 |
| ES->NQ | asia | 4 | +0.0038 | +4.6 | 0.010 | 0.57 |

### 11. Map rows that become book candidates under the FROZEN rule (p_family <= .05 AND room_A(session) > 2.0)
| map row | direction | stat | p_family | room_A | year sign share | stability | 1.7% cap >= 1 contract/5min in session |
|--|--|--|--|--|--|--|--|
| AC|asia|5m | reversion | -0.029 | 0.003 | 4.6 | 1.00 |  | yes |
| AC|london|5m | reversion | -0.029 | 0.003 | 5.4 | 1.00 |  | yes |
| AC|pre|5m | reversion | -0.038 | 0.003 | 6.6 | 0.93 |  | yes |
| AC|nyam|5m | reversion | -0.016 | 0.003 | 10.8 | 0.93 |  | yes |
| AC|nypm|5m | reversion | -0.026 | 0.003 | 10.0 | 0.93 |  | yes |
| AC|asia|15m | reversion | -0.011 | 0.023 | 4.6 | 0.64 |  | yes |
| AC|london|15m | reversion | -0.016 | 0.003 | 5.4 | 0.79 |  | yes |
| AC|close|30m | momentum | +0.052 | 0.003 | 10.1 | 0.64 |  | yes |
| rx|ON|nypm | level-bounce | +0.536 | 0.033 | 10.0 | 0.93 | stable | yes |
| rx|ON|close | level-bounce | +0.543 | 0.049 | 10.1 | 0.71 | stable | yes |
| gap|b3|h1 | level-bounce | +0.070 | 0.016 | 10.8 | 0.79 | stable | yes |
| vr|asia|5 | reversion | +0.846 | 0.016 | 4.6 | 1.00 | stable | yes |
| vr|asia|15 | reversion | +0.807 | 0.016 | 4.6 | 1.00 | stable | yes |
| vr|asia|30 | reversion | +0.799 | 0.016 | 4.6 | 1.00 | stable | yes |
| vr|asia|60 | reversion | +0.803 | 0.016 | 4.6 | 0.93 | stable | yes |
| vr|asia|120 | reversion | +0.816 | 0.016 | 4.6 | 0.93 | stable | yes |
| hurst|asia | reversion | +0.494 | 0.016 | 4.6 | 0.64 | stable | yes |
| vr|london|5 | reversion | +0.890 | 0.016 | 5.4 | 1.00 | stable | yes |
| vr|london|15 | reversion | +0.852 | 0.016 | 5.4 | 1.00 | stable | yes |
| vr|london|30 | reversion | +0.840 | 0.016 | 5.4 | 1.00 | stable | yes |
| vr|london|60 | reversion | +0.835 | 0.016 | 5.4 | 0.93 | stable | yes |
| vr|london|120 | reversion | +0.825 | 0.016 | 5.4 | 0.93 | stable | yes |
| hurst|london | reversion | +0.489 | 0.016 | 5.4 | 0.86 | stable | yes |
| vr|pre|5 | reversion | +0.893 | 0.016 | 6.6 | 0.93 | stable | yes |
| vr|pre|15 | reversion | +0.843 | 0.016 | 6.6 | 1.00 | stable | yes |
| hurst|pre | reversion | +0.474 | 0.016 | 6.6 | 0.79 | stable | yes |
| vr|nyam|5 | reversion | +0.953 | 0.016 | 10.8 | 0.86 | stable | yes |
| vr|nyam|15 | reversion | +0.928 | 0.016 | 10.8 | 1.00 | stable | yes |
| vr|nyam|30 | reversion | +0.927 | 0.016 | 10.8 | 0.79 | stable | yes |
| hurst|nyam | reversion | +0.492 | 0.049 | 10.8 | 0.71 | stable | yes |
| vr|nypm|5 | reversion | +0.924 | 0.016 | 10.0 | 0.93 | stable | yes |
| vr|nypm|15 | reversion | +0.892 | 0.016 | 10.0 | 1.00 | stable | yes |
| vr|nypm|30 | reversion | +0.884 | 0.016 | 10.0 | 1.00 | stable | yes |
| vr|nypm|60 | reversion | +0.905 | 0.016 | 10.0 | 0.79 | stable | yes |
| vr|close|5 | reversion | +0.951 | 0.016 | 10.1 | 0.79 | stable | yes |
| vr|close|15 | reversion | +0.944 | 0.016 | 10.1 | 0.64 | stable | yes |
| vr|rth|5 | reversion | +0.943 | 0.016 | 10.8 | 0.86 | stable | yes |
| vr|rth|15 | reversion | +0.915 | 0.016 | 10.8 | 0.93 | stable | yes |
| vr|rth|30 | reversion | +0.915 | 0.016 | 10.8 | 0.86 | stable | yes |
| vr|rth|60 | reversion | +0.923 | 0.016 | 10.8 | 0.86 | stable | yes |
| vr|rth|120 | reversion | +0.947 | 0.016 | 10.8 | 0.71 | stable | yes |


## YM - character map (CHAR-A, 2026-11-05T22:17Z)
Base: YM CME front-month (.v.0) 1-min bars from 2013-01 to 2026-10, percent frame (multiplicative roll-adjusted), 1-min approximation (no tick path), 3443 usable label days; ET clock, sessions asia 18:00-02:00 / london 02:00-08:30 / pre 08:30-09:30 / nyam 09:30-12:00 / nypm 12:00-15:00 / close 15:00-16:55. Nulls: within-year shuffled-day (AC B=300; structure B=100 worlds; levels recomputed on the shuffled path; round numbers 60 random grid phases); p_family = Westfall-Young max-|z| over the block (AC family 153 cells, structure family 92 cells). `**` p_family<=.05, `*` <=.10. Prereg sha256 980bedf6bad3f1669de9efb93831fa4622d88577c892d9359b7f57ba93c9dbcf. Descriptive only: no PASS, nothing live.

### Plain paragraph
At 1 minute every session has negative autocorrelation (-0.039 to -0.011; bid-ask bounce / last-print noise, not a tradable edge by itself). asia: reverts at 5/15 min (-0.019, -0.012). london: reverts at 5 min (-0.014). pre: reverts at 5 min (-0.017). nypm: reverts at 5 min (-0.012). close: reverts at 5 min (-0.020). Day types (RTH): 45% trend days (efficiency ratio >= .5; shuffled null 46%, p_fam 1.000), 27% range days (<.25; null 26%, p_fam 1.000); the IB (09:30-10:30) is extended on one side only on 72% of days and on both on 24%, and a one-sided extension closes beyond the IB edge 63% of the time (null 66%). RTH variance ratio at 30 min 0.965 (shuffled null 0.998, p_fam 0.016); Hurst 0.504. The RTH range forms 9:30 (40%), 10:00 (23%), 11:00 (11%) of the range increments. No level (prior-day H/L, overnight H/L, IB edge, VWAP +-1/2 sigma, round numbers) beats its shuffled-day family null for bounce vs break-through. Failed-break follow-through beating the null: none. Room (median 3xATR14(5m) $ / round-trip cost $20 per lot): asia 7.1x, london 8.9x, pre 11.1x, nyam 19.8x, nypm 17.3x, close 16.7x (1xATR5 room 6.6x in nyam, 2.4x in asia).

### 1. Autocorrelation of h-min returns (corr(past h, next h), both inside the session), pooled; cell = corr (pre-2023 mean | 2023+ mean) p_family
| session | 1 min | 5 min | 15 min | 30 min | 60 min | 120 min |
|--|--|--|--|--|--|--|
| asia | -0.039 (-0.042|-0.038) p0.003** ys1.00 | -0.019 (-0.021|-0.028) p0.003** ys0.86 | -0.012 (-0.012|-0.030) p0.027** ys0.79 | -0.003 (-0.005|-0.017) p1.000 ys0.71 | +0.003 (-0.008|+0.015) p1.000 ys0.43 | +0.013 (-0.005|+0.024) p1.000 ys0.43 |
| london | -0.025 (-0.031|-0.010) p0.003** ys0.86 | -0.014 (-0.015|-0.012) p0.003** ys1.00 | -0.006 (-0.008|-0.002) p0.967 ys0.57 | -0.003 (-0.008|+0.013) p1.000 ys0.43 | -0.009 (-0.017|+0.009) p1.000 ys0.64 | -0.016 (-0.025|+0.023) p1.000 ys0.50 |
| pre | -0.021 (-0.022|-0.016) p0.003** ys0.79 | -0.017 (-0.027|+0.003) p0.030** ys0.64 | -0.017 (-0.023|-0.010) p1.000 ys0.71 | -0.021 (+0.010|-0.086) p1.000 ys0.57 | - | - |
| nyam | -0.011 (-0.010|-0.009) p0.003** ys0.71 | -0.005 (-0.008|+0.001) p1.000 ys0.57 | +0.010 (+0.009|+0.010) p0.990 ys0.50 | +0.004 (-0.007|+0.027) p1.000 ys0.57 | +0.009 (+0.011|+0.000) p1.000 ys0.43 | - |
| nypm | -0.019 (-0.017|-0.023) p0.003** ys0.86 | -0.012 (-0.019|+0.001) p0.007** ys0.64 | +0.002 (-0.006|+0.019) p1.000 ys0.64 | +0.020 (+0.013|+0.029) p0.355 ys0.71 | +0.018 (+0.011|+0.015) p1.000 ys0.64 | - |
| close | -0.013 (-0.019|-0.004) p0.003** ys0.79 | -0.020 (-0.028|+0.002) p0.003** ys0.64 | -0.005 (-0.001|-0.032) p1.000 ys0.71 | +0.017 (+0.034|-0.065) p0.997 ys0.64 | - | - |

Hour cells (h >= 5) beating the family null, top 14 by |z| (hour = ET hour of the decision bar):
| h | session | hour ET | corr | z | p_family | year sign share | pre-2023 | 2023+ |
|--|--|--|--|--|--|--|--|--|
| 5 | close | 16 | -0.042 | -8.2 | 0.003 | 0.93 | -0.044 | -0.045 |
| 5 | asia | 18 | -0.031 | -7.3 | 0.003 | 0.71 | -0.036 | -0.042 |
| 15 | london | 02 | -0.051 | -7.0 | 0.003 | 0.79 | -0.067 | +0.010 |
| 15 | asia | 01 | -0.051 | -6.3 | 0.003 | 0.64 | -0.064 | -0.005 |
| 15 | asia | 18 | -0.042 | -6.2 | 0.003 | 1.00 | -0.052 | -0.033 |
| 60 | asia | 23 | -0.075 | -6.1 | 0.003 | 0.71 | -0.078 | +0.016 |
| 5 | asia | 23 | -0.023 | -5.6 | 0.003 | 0.86 | -0.029 | -0.031 |
| 5 | asia | 01 | -0.026 | -5.5 | 0.003 | 0.71 | -0.031 | -0.017 |
| 5 | london | 02 | -0.022 | -5.4 | 0.003 | 0.79 | -0.027 | -0.005 |
| 30 | asia | 01 | -0.074 | -5.3 | 0.003 | 0.71 | -0.087 | -0.041 |
| 120 | asia | 23 | -0.077 | -5.3 | 0.003 | 0.71 | -0.098 | +0.017 |
| 5 | asia | 19 | -0.021 | -5.0 | 0.003 | 0.71 | -0.032 | -0.011 |
| 120 | asia | 21 | +0.081 | +5.0 | 0.003 | 0.64 | +0.063 | -0.001 |
| 5 | asia | 22 | -0.021 | -4.9 | 0.003 | 0.86 | -0.022 | -0.050 |

### 2. Variance ratio VR(q) and Hurst (1.0 = random walk; <1 reverting; edge-bias corrected), cell = value (null) p_family
| session | VR5 | VR15 | VR30 | VR60 | VR120 | Hurst |
|--|--|--|--|--|--|--|
| asia | 0.919 (1.000) p0.016** | 0.891 (0.999) p0.016** | 0.885 (0.999) p0.016** | 0.889 (0.999) p0.016** | 0.902 (1.000) p0.016** | 0.497 (0.500) p1.000 |
| london | 0.953 (1.000) p0.016** | 0.932 (0.999) p0.016** | 0.927 (0.999) p0.016** | 0.925 (0.999) p0.016** | 0.918 (0.999) p0.016** | 0.495 (0.500) p0.230 |
| pre | 0.959 (1.000) p0.016** | 0.933 (1.000) p0.016** | - | - | - | 0.488 (0.500) p0.115 |
| nyam | 0.978 (1.000) p0.016** | 0.969 (0.999) p0.016** | 0.973 (0.998) p0.377 | - | - | 0.498 (0.499) p1.000 |
| nypm | 0.961 (0.999) p0.016** | 0.947 (0.999) p0.016** | 0.947 (0.998) p0.016** | 0.970 (0.998) p0.902 | - | 0.501 (0.500) p1.000 |
| close | 0.966 (1.000) p0.016** | 0.939 (1.000) p0.016** | 0.941 (0.999) p0.016** | - | - | 0.492 (0.500) p0.721 |
| rth | 0.972 (1.000) p0.016** | 0.960 (0.999) p0.016** | 0.965 (0.998) p0.016** | 0.977 (0.999) p0.672 | 0.996 (0.999) p1.000 | 0.504 (0.500) p0.967 |

### 3. Day types (ex-post labels of the RTH day)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| day|trend | 0.453 | 3443 | 0.462 | -1.2 | 1.000 | 0.50 | 0.456 | 0.440 | unstable |
| day|range | 0.268 | 3443 | 0.256 | +1.6 | 1.000 | 0.57 | 0.269 | 0.268 | unstable |
| day|er | 0.457 | 3443 | 0.465 | -1.8 | 0.967 | 0.50 | 0.461 | 0.446 | unstable |
| day|ib_none | 0.042 | 3443 | 0.022 | +8.5 | 0.016** | 0.93 | 0.041 | 0.046 | stable |
| day|ib_one | 0.716 | 3443 | 0.697 | +2.7 | 0.443 | 0.71 | 0.711 | 0.732 | stable |
| day|ib_both | 0.242 | 3443 | 0.281 | -5.8 | 0.016** | 0.71 | 0.248 | 0.221 | stable |
| day|ib_one_closebeyond | 0.634 | 2465 | 0.660 | -2.7 | 0.443 | 0.64 | 0.642 | 0.612 | stable |

### 4. 1A -> 2A continuation vs give-back-half from the session open (A = 3 x ATR14(5m)); value = P(continue | resolved)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| cont|asia | 0.360 | 1697 | 0.350 | +1.1 | 1.000 | 0.57 | 0.358 | 0.334 | unstable |
| cont|london | 0.334 | 3433 | 0.364 | -3.6 | 0.016** | 0.79 | 0.325 | 0.358 | stable |
| cont|pre | 0.350 | 1352 | 0.331 | +1.7 | 0.984 | 0.43 | 0.343 | 0.354 | unstable |
| cont|nyam | 0.352 | 3345 | 0.349 | +0.3 | 1.000 | 0.57 | 0.359 | 0.333 | unstable |
| cont|nypm | 0.299 | 1330 | 0.288 | +1.0 | 1.000 | 0.57 | 0.286 | 0.335 | REGIME(2023+ only) |
| cont|close | 0.285 | 1181 | 0.272 | +1.2 | 1.000 | 0.50 | 0.291 | 0.251 | unstable |
| cont|rth | 0.352 | 3414 | 0.349 | +0.3 | 1.000 | 0.57 | 0.359 | 0.334 | unstable |

### 5. Gap fill by size bucket (b0 .05-.10, b1 .10-.25, b2 .25-.50, b3 >.50 of the 20-day mean RTH range); day = filled during RTH, h1 = within 60 min
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| gap|b0|day | 0.913 | 334 | 0.894 | +1.1 | 1.000 | 0.57 | 0.903 | 0.904 | unstable |
| gap|b0|h1 | 0.838 | 334 | 0.806 | +1.3 | 1.000 | 0.57 | 0.833 | 0.828 | unstable |
| gap|b1|day | 0.772 | 867 | 0.765 | +0.4 | 1.000 | 0.50 | 0.763 | 0.788 | REGIME(2023+ only) |
| gap|b1|h1 | 0.603 | 867 | 0.589 | +0.9 | 1.000 | 0.57 | 0.593 | 0.625 | unstable |
| gap|b2|day | 0.551 | 937 | 0.549 | +0.1 | 1.000 | 0.57 | 0.531 | 0.602 | REGIME(2023+ only) |
| gap|b2|h1 | 0.293 | 937 | 0.287 | +0.5 | 1.000 | 0.43 | 0.288 | 0.323 | unstable |
| gap|b3|day | 0.276 | 980 | 0.252 | +1.7 | 1.000 | 0.71 | 0.277 | 0.289 | stable |
| gap|b3|h1 | 0.074 | 980 | 0.060 | +2.2 | 0.902 | 0.64 | 0.072 | 0.082 | stable |

### 6. Level reaction: first touch -> bounce (0.5A reverse) vs break-through (0.5A beyond) within 60 min; value = P(bounce)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| rx|PD|asia | 0.441 | 1289 | 0.460 | -1.5 | 1.000 | 0.50 | 0.433 | 0.469 | unstable |
| rx|PD|london | 0.503 | 1750 | 0.483 | +1.7 | 1.000 | 0.57 | 0.493 | 0.531 | unstable |
| rx|PD|pre | 0.486 | 862 | 0.486 | +0.0 | 1.000 | 0.57 | 0.480 | 0.497 | REGIME(2023+ only) |
| rx|PD|nyam | 0.496 | 2050 | 0.492 | +0.4 | 1.000 | 0.50 | 0.491 | 0.508 | REGIME(2023+ only) |
| rx|PD|nypm | 0.516 | 1180 | 0.495 | +1.4 | 1.000 | 0.57 | 0.512 | 0.533 | unstable |
| rx|PD|close | 0.504 | 827 | 0.491 | +0.8 | 1.000 | 0.57 | 0.501 | 0.499 | unstable |
| rx|ON|nyam | 0.483 | 3260 | 0.492 | -1.0 | 1.000 | 0.43 | 0.477 | 0.497 | unstable |
| rx|ON|nypm | 0.518 | 1571 | 0.492 | +2.0 | 0.967 | 0.86 | 0.515 | 0.519 | stable |
| rx|ON|close | 0.511 | 1048 | 0.492 | +1.2 | 1.000 | 0.64 | 0.526 | 0.471 | stable |
| rx|IB|nyam | 0.477 | 2550 | 0.495 | -2.0 | 0.967 | 0.57 | 0.474 | 0.492 | unstable |
| rx|IB|nypm | 0.490 | 2147 | 0.492 | -0.2 | 1.000 | 0.57 | 0.494 | 0.489 | REGIME(2023+ only) |
| rx|IB|close | 0.525 | 1337 | 0.493 | +2.3 | 0.770 | 0.79 | 0.523 | 0.532 | stable |
| rx|VW1|nyam | 0.497 | 5007 | 0.494 | +0.4 | 1.000 | 0.64 | 0.498 | 0.490 | stable |
| rx|VW1|nypm | 0.503 | 3294 | 0.492 | +1.3 | 1.000 | 0.64 | 0.499 | 0.513 | stable |
| rx|VW1|close | 0.508 | 2332 | 0.492 | +1.6 | 1.000 | 0.64 | 0.503 | 0.519 | stable |
| rx|VW2|nyam | 0.508 | 3602 | 0.500 | +1.0 | 1.000 | 0.50 | 0.504 | 0.525 | unstable |
| rx|VW2|nypm | 0.473 | 2056 | 0.493 | -2.1 | 0.967 | 0.71 | 0.466 | 0.485 | stable |
| rx|VW2|close | 0.497 | 1302 | 0.496 | +0.0 | 1.000 | 0.57 | 0.486 | 0.545 | REGIME(2023+ only) |
| rx|RN|asia | 0.483 | 22690 | 0.483 | +0.2 | 1.000 | 0.57 | 0.477 | 0.477 | unstable |
| rx|RN|london | 0.486 | 30037 | 0.488 | -0.7 | 1.000 | 0.64 | 0.485 | 0.484 | stable |
| rx|RN|pre | 0.483 | 6838 | 0.490 | -1.2 | 1.000 | 0.57 | 0.478 | 0.488 | unstable |
| rx|RN|nyam | 0.489 | 28465 | 0.493 | -1.8 | 0.984 | 0.57 | 0.492 | 0.487 | unstable |
| rx|RN|nypm | 0.495 | 22380 | 0.493 | +0.5 | 1.000 | 0.64 | 0.499 | 0.488 | stable |
| rx|RN|close | 0.492 | 9051 | 0.495 | -0.8 | 1.000 | 0.57 | 0.489 | 0.496 | unstable |

### 7. Failed break (close .25A beyond, back inside within 10 bars): fade follow-through P(0.5A back before 0.5A out)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| fb|PD|asia | 0.509 | 685 | 0.501 | +0.5 | 1.000 | 0.43 | 0.520 | 0.499 | unstable |
| fb|PD|london | 0.498 | 1168 | 0.499 | -0.0 | 1.000 | 0.64 | 0.479 | 0.553 | stable |
| fb|PD|pre | 0.523 | 472 | 0.500 | +0.9 | 1.000 | 0.64 | 0.513 | 0.534 | stable |
| fb|PD|nyam | 0.516 | 1325 | 0.500 | +1.1 | 1.000 | 0.57 | 0.507 | 0.548 | unstable |
| fb|PD|nypm | 0.538 | 769 | 0.501 | +2.1 | 0.918 | 0.93 | 0.528 | 0.568 | stable |
| fb|PD|close | 0.507 | 450 | 0.500 | +0.3 | 1.000 | 0.57 | 0.508 | 0.471 | unstable |
| fb|ON|nyam | 0.519 | 1623 | 0.500 | +1.5 | 1.000 | 0.64 | 0.509 | 0.541 | stable |
| fb|ON|nypm | 0.521 | 960 | 0.499 | +1.3 | 1.000 | 0.71 | 0.506 | 0.557 | stable |
| fb|ON|close | 0.494 | 538 | 0.503 | -0.4 | 1.000 | 0.43 | 0.519 | 0.432 | REGIME(2023+ only) |
| fb|IB|nyam | 0.471 | 698 | 0.499 | -1.6 | 1.000 | 0.64 | 0.478 | 0.451 | stable |
| fb|IB|nypm | 0.493 | 1214 | 0.501 | -0.6 | 1.000 | 0.64 | 0.486 | 0.515 | stable |
| fb|IB|close | 0.503 | 682 | 0.502 | +0.0 | 1.000 | 0.50 | 0.492 | 0.532 | REGIME(2023+ only) |

### 8. Where the range forms
RTH range increments by bin: 9:30 39.9%, 10:00 22.5%, 11:00 11.4%, 12:00 6.7%, 13:00 5.6%, 14:00 6.5%, 15:00 7.4%
Label-day range increments by ET hour (percent of the day): 00h nan, 01h nan, 02h nan, 03h nan, 04h nan, 05h nan, 06h nan, 07h nan, 08h nan, 09h nan, 10h nan, 11h nan, 12h nan, 13h nan, 14h nan, 15h nan, 16h nan, 18h nan, 19h nan, 20h nan, 21h nan, 22h nan, 23h nan

### 9. Room and liquidity (all years, raw-frame $, 1 lot)
| session | ATR14(5m) $ | A=3xATR5 $ | RT cost $ | room(1 ATR5) | room(A) | median 5-min vol | 1.7% cap (contracts/5min) | lots for $1,200 at 3xATR5 stop |
|--|--|--|--|--|--|--|--|--|
| asia | 47 | 141 | 20 | 2.38 | 7.13 | 65 | 1.1 | 8.5 |
| london | 59 | 176 | 20 | 2.96 | 8.87 | 190 | 3.2 | 6.8 |
| pre | 73 | 220 | 20 | 3.70 | 11.11 | 413 | 7.0 | 5.4 |
| nyam | 131 | 392 | 20 | 6.59 | 19.77 | 1573 | 26.7 | 3.1 |
| nypm | 114 | 343 | 20 | 5.75 | 17.26 | 734 | 12.5 | 3.5 |
| close | 110 | 331 | 20 | 5.56 | 16.68 | 604 | 10.3 | 3.6 |

room(A) by year: asia: 2013:2.9 2014:2.9 2015:4.2 2016:4.4 2017:3.3 2018:8.6 2019:7.7 2020:16.0 2021:9.8 2022:13.7 2023:6.7 2024:6.8 2025:10.9 2026:12.4; london: 2013:3.7 2014:4.2 2015:6.5 2016:5.8 2017:3.7 2018:9.2 2019:8.2 2020:17.7 2021:11.3 2022:17.7 2023:9.9 2024:9.3 2025:12.5 2026:16.2; pre: 2013:4.5 2014:5.3 2015:7.7 2016:6.2 2017:4.5 2018:10.7 2019:10.0 2020:18.2 2021:13.1 2022:21.0 2023:13.5 2024:13.5 2025:16.8 2026:23.2; nyam: 2013:8.5 2014:10.0 2015:13.2 2016:10.9 2017:8.4 2018:18.6 2019:16.7 2020:28.2 2021:23.4 2022:37.3 2023:24.7 2024:28.3 2025:33.9 2026:43.1; nypm: 2013:7.0 2014:8.3 2015:11.2 2016:9.6 2017:7.1 2018:18.2 2019:14.4 2020:24.0 2021:18.1 2022:33.4 2023:21.4 2024:23.8 2025:30.2 2026:32.2; close: 2013:7.5 2014:8.1 2015:11.2 2016:9.7 2017:6.8 2018:18.5 2019:14.0 2020:26.6 2021:17.6 2022:32.8 2023:19.5 2024:21.7 2025:25.5 2026:24.9

### 10. Versus NQ
Contemporaneous correlation of h-min returns (normalised): asia: 1m 0.77 5m 0.84 15m 0.86 30m 0.87 60m 0.88; london: 1m 0.78 5m 0.81 15m 0.82 30m 0.82 60m 0.82; pre: 1m 0.73 5m 0.75 15m 0.75; nyam: 1m 0.66 5m 0.65 15m 0.64 30m 0.63; nypm: 1m 0.83 5m 0.83 15m 0.84 30m 0.84; close: 1m 0.79 5m 0.81 15m 0.82

Lead/lag (1-15 min, family 180 cells; corr of 1-min normalised returns): cells beating the family null (top 10 by |z|; "NQ->X" = NQ leads YM):
| direction | session | lag min | corr | z | p_family | year sign share |
|--|--|--|--|--|--|--|
| NQ->YM | asia | 1 | +0.0206 | +23.6 | 0.010 | 0.93 |
| YM->NQ | asia | 1 | +0.0085 | +9.6 | 0.010 | 0.71 |
| NQ->YM | london | 1 | +0.0063 | +7.6 | 0.010 | 0.71 |
| YM->NQ | pre | 1 | -0.0154 | -7.6 | 0.010 | 0.79 |
| YM->NQ | nyam | 1 | -0.0095 | -5.3 | 0.010 | 0.79 |
| NQ->YM | london | 10 | +0.0043 | +4.7 | 0.010 | 0.79 |
| NQ->YM | nypm | 1 | -0.0069 | -4.7 | 0.010 | 0.71 |
| YM->NQ | close | 1 | +0.0092 | +4.7 | 0.010 | 0.71 |
| NQ->YM | london | 6 | -0.0045 | -4.6 | 0.010 | 0.86 |
| YM->NQ | pre | 9 | -0.0079 | -4.5 | 0.010 | 0.79 |

### 11. Map rows that become book candidates under the FROZEN rule (p_family <= .05 AND room_A(session) > 2.0)
| map row | direction | stat | p_family | room_A | year sign share | stability | 1.7% cap >= 1 contract/5min in session |
|--|--|--|--|--|--|--|--|
| AC|asia|5m | reversion | -0.019 | 0.003 | 7.1 | 0.86 |  | yes |
| AC|london|5m | reversion | -0.014 | 0.003 | 8.9 | 1.00 |  | yes |
| AC|pre|5m | reversion | -0.017 | 0.030 | 11.1 | 0.64 |  | yes |
| AC|nypm|5m | reversion | -0.012 | 0.007 | 17.3 | 0.64 |  | yes |
| AC|close|5m | reversion | -0.020 | 0.003 | 16.7 | 0.64 |  | yes |
| AC|asia|15m | reversion | -0.012 | 0.027 | 7.1 | 0.79 |  | yes |
| vr|asia|5 | reversion | +0.919 | 0.016 | 7.1 | 1.00 | stable | yes |
| vr|asia|15 | reversion | +0.891 | 0.016 | 7.1 | 1.00 | stable | yes |
| vr|asia|30 | reversion | +0.885 | 0.016 | 7.1 | 1.00 | stable | yes |
| vr|asia|60 | reversion | +0.889 | 0.016 | 7.1 | 0.93 | stable | yes |
| vr|asia|120 | reversion | +0.902 | 0.016 | 7.1 | 0.86 | stable | yes |
| vr|london|5 | reversion | +0.953 | 0.016 | 8.9 | 1.00 | stable | yes |
| vr|london|15 | reversion | +0.932 | 0.016 | 8.9 | 1.00 | stable | yes |
| vr|london|30 | reversion | +0.927 | 0.016 | 8.9 | 0.86 | stable | yes |
| vr|london|60 | reversion | +0.925 | 0.016 | 8.9 | 0.86 | stable | yes |
| vr|london|120 | reversion | +0.918 | 0.016 | 8.9 | 0.71 | stable | yes |
| vr|pre|5 | reversion | +0.959 | 0.016 | 11.1 | 0.93 | stable | yes |
| vr|pre|15 | reversion | +0.933 | 0.016 | 11.1 | 0.86 | stable | yes |
| vr|nyam|5 | reversion | +0.978 | 0.016 | 19.8 | 0.79 | stable | yes |
| vr|nyam|15 | reversion | +0.969 | 0.016 | 19.8 | 0.71 | stable | yes |
| vr|nypm|5 | reversion | +0.961 | 0.016 | 17.3 | 0.86 | stable | yes |
| vr|nypm|15 | reversion | +0.947 | 0.016 | 17.3 | 0.93 | stable | yes |
| vr|nypm|30 | reversion | +0.947 | 0.016 | 17.3 | 0.79 | stable | yes |
| vr|close|5 | reversion | +0.966 | 0.016 | 16.7 | 0.93 | stable | yes |
| vr|close|15 | reversion | +0.939 | 0.016 | 16.7 | 1.00 | stable | yes |
| vr|close|30 | reversion | +0.941 | 0.016 | 16.7 | 0.86 | stable | yes |
| vr|rth|5 | reversion | +0.972 | 0.016 | 19.8 | 0.86 | stable | yes |
| vr|rth|15 | reversion | +0.960 | 0.016 | 19.8 | 0.86 | stable | yes |
| vr|rth|30 | reversion | +0.965 | 0.016 | 19.8 | 0.79 | stable | yes |


## GC - character map (CHAR-B via CHAR-A char_lib, 2026-11-05T23:30Z)
Base: GC CME front-month (.v.0) 1-min bars from 2013-01 to 2026-10, percent frame (multiplicative roll-adjusted), 1-min approximation (no tick path), 3380 usable label days; ET clock, sessions asia 18:00-02:00 / london 02:00-08:30 / pre 08:30-09:30 / nyam 09:30-12:00 / nypm 12:00-15:00 / close 15:00-16:55. Nulls: within-year shuffled-day (AC B=300; structure B=100 worlds; levels recomputed on the shuffled path; round numbers 60 random grid phases); p_family = Westfall-Young max-|z| over the block (AC family 153 cells, structure family 92 cells). `**` p_family<=.05, `*` <=.10. Prereg sha256 980bedf6bad3f1669de9efb93831fa4622d88577c892d9359b7f57ba93c9dbcf. Descriptive only: no PASS, nothing live.

### Plain paragraph
At 1 minute every session has negative autocorrelation (-0.062 to -0.013; bid-ask bounce / last-print noise, not a tradable edge by itself). asia: reverts at 5/60 min (-0.022, -0.022). london: reverts at 5/15/30 min (-0.021, -0.021, -0.016). pre: reverts at 5 min (-0.022). nypm: reverts at 5/15 min (-0.020, -0.015). close: reverts at 5/15/30 min (-0.053, -0.041, -0.056). Day types (RTH): 41% trend days (efficiency ratio >= .5; shuffled null 46%, p_fam 0.016), 28% range days (<.25; null 26%, p_fam 0.016); the IB (09:30-10:30) is extended on one side only on 75% of days and on both on 17%, and a one-sided extension closes beyond the IB edge 57% of the time (null 64%). RTH variance ratio at 30 min 0.923 (shuffled null 0.998, p_fam 0.016); Hurst 0.492. The RTH range forms 9:30 (41%), 10:00 (29%), 11:00 (11%) of the range increments. Level reactions that beat the family null: VW1|nyam bounces 47% of touches (less, i.e. breaks through more than the shuffled null 49%). Failed-break follow-through beating the null: IB|close 38% (null 50%). Room (median 3xATR14(5m) $ / round-trip cost $35 per lot): asia 6.6x, london 8.8x, pre 13.9x, nyam 15.9x, nypm 10.8x, close 7.6x (1xATR5 room 5.3x in nyam, 2.2x in asia).

### 1. Autocorrelation of h-min returns (corr(past h, next h), both inside the session), pooled; cell = corr (pre-2023 mean | 2023+ mean) p_family
| session | 1 min | 5 min | 15 min | 30 min | 60 min | 120 min |
|--|--|--|--|--|--|--|
| asia | -0.043 (-0.050|-0.031) p0.003** ys1.00 | -0.022 (-0.032|-0.004) p0.003** ys0.93 | -0.009 (-0.013|-0.007) p0.146 ys0.71 | -0.009 (-0.009|-0.015) p0.741 ys0.71 | -0.022 (-0.024|-0.035) p0.023** ys0.93 | -0.019 (-0.026|-0.033) p0.973 ys0.71 |
| london | -0.031 (-0.039|-0.011) p0.003** ys1.00 | -0.021 (-0.024|-0.015) p0.003** ys0.93 | -0.021 (-0.022|-0.020) p0.003** ys0.93 | -0.016 (-0.023|+0.004) p0.027** ys0.86 | -0.008 (-0.012|-0.005) p1.000 ys0.57 | +0.011 (+0.010|+0.014) p1.000 ys0.64 |
| pre | -0.017 (-0.023|-0.008) p0.003** ys0.79 | -0.022 (-0.032|-0.004) p0.007** ys0.64 | +0.003 (-0.006|+0.013) p1.000 ys0.57 | -0.008 (-0.007|-0.017) p1.000 ys0.50 | - | - |
| nyam | -0.013 (-0.020|-0.001) p0.003** ys0.71 | -0.010 (-0.011|-0.011) p0.189 ys0.93 | +0.001 (+0.004|-0.014) p1.000 ys0.43 | +0.007 (+0.007|-0.004) p1.000 ys0.64 | +0.005 (-0.004|+0.016) p1.000 ys0.57 | - |
| nypm | -0.037 (-0.045|-0.013) p0.003** ys1.00 | -0.020 (-0.023|-0.014) p0.003** ys0.93 | -0.015 (-0.014|-0.027) p0.040** ys0.79 | -0.005 (-0.001|-0.032) p1.000 ys0.57 | -0.023 (-0.031|-0.021) p1.000 ys0.64 | - |
| close | -0.062 (-0.065|-0.057) p0.003** ys1.00 | -0.053 (-0.060|-0.028) p0.003** ys1.00 | -0.041 (-0.046|-0.016) p0.003** ys0.71 | -0.056 (-0.069|-0.015) p0.003** ys0.86 | - | - |

Hour cells (h >= 5) beating the family null, top 14 by |z| (hour = ET hour of the decision bar):
| h | session | hour ET | corr | z | p_family | year sign share | pre-2023 | 2023+ |
|--|--|--|--|--|--|--|--|--|
| 5 | close | 16 | -0.063 | -14.8 | 0.003 | 1.00 | -0.075 | -0.027 |
| 5 | asia | 23 | -0.045 | -11.7 | 0.003 | 0.93 | -0.052 | -0.050 |
| 5 | close | 15 | -0.049 | -11.1 | 0.003 | 0.93 | -0.055 | -0.026 |
| 5 | asia | 22 | -0.038 | -9.9 | 0.003 | 0.93 | -0.051 | -0.016 |
| 5 | asia | 18 | -0.040 | -9.4 | 0.003 | 0.86 | -0.047 | -0.020 |
| 15 | asia | 18 | -0.068 | -9.4 | 0.003 | 0.79 | -0.040 | -0.141 |
| 5 | asia | 19 | -0.035 | -8.4 | 0.003 | 0.71 | -0.058 | +0.002 |
| 5 | london | 05 | -0.031 | -7.9 | 0.003 | 0.93 | -0.041 | -0.019 |
| 60 | asia | 18 | -0.145 | -7.9 | 0.003 | 0.86 | -0.137 | -0.150 |
| 5 | asia | 00 | -0.031 | -7.8 | 0.003 | 0.86 | -0.046 | -0.004 |
| 5 | nypm | 12 | -0.031 | -7.2 | 0.003 | 0.93 | -0.034 | -0.029 |
| 5 | london | 04 | -0.029 | -6.8 | 0.003 | 0.93 | -0.034 | -0.023 |
| 5 | london | 07 | -0.028 | -6.8 | 0.003 | 0.93 | -0.029 | -0.022 |
| 15 | close | 16 | -0.044 | -5.9 | 0.003 | 0.79 | -0.045 | -0.017 |

### 2. Variance ratio VR(q) and Hurst (1.0 = random walk; <1 reverting; edge-bias corrected), cell = value (null) p_family
| session | VR5 | VR15 | VR30 | VR60 | VR120 | Hurst |
|--|--|--|--|--|--|--|
| asia | 0.911 (1.000) p0.016** | 0.885 (1.000) p0.016** | 0.877 (1.000) p0.016** | 0.871 (1.000) p0.016** | 0.862 (0.999) p0.016** | 0.492 (0.500) p0.016** |
| london | 0.934 (1.000) p0.016** | 0.900 (1.000) p0.016** | 0.877 (1.000) p0.016** | 0.860 (1.000) p0.016** | 0.850 (1.001) p0.016** | 0.485 (0.500) p0.016** |
| pre | 0.950 (1.000) p0.016** | 0.919 (1.001) p0.016** | - | - | - | 0.485 (0.500) p0.016** |
| nyam | 0.970 (1.000) p0.016** | 0.958 (0.999) p0.016** | 0.959 (0.999) p0.016** | - | - | 0.497 (0.500) p1.000 |
| nypm | 0.922 (0.999) p0.016** | 0.893 (0.999) p0.016** | 0.876 (0.998) p0.016** | 0.870 (0.996) p0.016** | - | 0.488 (0.499) p0.016** |
| close | 0.875 (0.999) p0.016** | 0.807 (0.998) p0.016** | 0.770 (0.997) p0.016** | - | - | 0.464 (0.500) p0.016** |
| rth | 0.950 (0.999) p0.016** | 0.929 (0.999) p0.016** | 0.923 (0.998) p0.016** | 0.918 (0.998) p0.016** | 0.898 (0.997) p0.016** | 0.492 (0.500) p0.016** |

### 3. Day types (ex-post labels of the RTH day)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| day|trend | 0.412 | 3380 | 0.458 | -5.4 | 0.016** | 0.93 | 0.408 | 0.420 | stable |
| day|range | 0.285 | 3380 | 0.257 | +3.5 | 0.016** | 0.93 | 0.284 | 0.288 | stable |
| day|er | 0.433 | 3380 | 0.463 | -6.8 | 0.016** | 0.93 | 0.432 | 0.434 | stable |
| day|ib_none | 0.085 | 3380 | 0.030 | +20.3 | 0.016** | 1.00 | 0.090 | 0.071 | stable |
| day|ib_one | 0.745 | 3380 | 0.714 | +3.8 | 0.016** | 0.71 | 0.731 | 0.780 | stable |
| day|ib_both | 0.170 | 3380 | 0.256 | -11.3 | 0.016** | 1.00 | 0.179 | 0.148 | stable |
| day|ib_one_closebeyond | 0.572 | 2519 | 0.644 | -6.5 | 0.016** | 1.00 | 0.567 | 0.583 | stable |

### 4. 1A -> 2A continuation vs give-back-half from the session open (A = 3 x ATR14(5m)); value = P(continue | resolved)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| cont|asia | 0.334 | 3268 | 0.383 | -5.9 | 0.016** | 1.00 | 0.334 | 0.336 | stable |
| cont|london | 0.355 | 3334 | 0.342 | +1.7 | 1.000 | 0.64 | 0.358 | 0.348 | stable |
| cont|pre | 0.373 | 1564 | 0.331 | +3.9 | 0.016** | 0.86 | 0.361 | 0.400 | stable |
| cont|nyam | 0.317 | 2158 | 0.309 | +0.8 | 1.000 | 0.50 | 0.317 | 0.316 | unstable |
| cont|nypm | 0.276 | 961 | 0.267 | +0.8 | 1.000 | 0.57 | 0.280 | 0.249 | unstable |
| cont|close | 0.247 | 635 | 0.246 | +0.1 | 1.000 | 0.57 | 0.238 | 0.271 | REGIME(2023+ only) |
| cont|rth | 0.331 | 2738 | 0.331 | -0.0 | 1.000 | 0.50 | 0.333 | 0.324 | REGIME(2023+ only) |

### 5. Gap fill by size bucket (b0 .05-.10, b1 .10-.25, b2 .25-.50, b3 >.50 of the 20-day mean RTH range); day = filled during RTH, h1 = within 60 min
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| gap|b0|day | 0.900 | 211 | 0.902 | -0.1 | 1.000 | 0.43 | 0.916 | 0.871 | REGIME(2023+ only) |
| gap|b0|h1 | 0.844 | 211 | 0.828 | +0.6 | 1.000 | 0.64 | 0.854 | 0.831 | stable |
| gap|b1|day | 0.730 | 585 | 0.773 | -2.1 | 0.951 | 0.86 | 0.736 | 0.710 | stable |
| gap|b1|h1 | 0.593 | 585 | 0.614 | -1.0 | 1.000 | 0.71 | 0.581 | 0.614 | stable |
| gap|b2|day | 0.505 | 792 | 0.546 | -2.4 | 0.623 | 0.86 | 0.508 | 0.497 | stable |
| gap|b2|h1 | 0.280 | 792 | 0.299 | -1.0 | 1.000 | 0.71 | 0.275 | 0.293 | stable |
| gap|b3|day | 0.178 | 1579 | 0.176 | +0.2 | 1.000 | 0.64 | 0.182 | 0.170 | stable |
| gap|b3|h1 | 0.062 | 1579 | 0.041 | +4.6 | 0.016** | 0.86 | 0.063 | 0.061 | stable |

### 6. Level reaction: first touch -> bounce (0.5A reverse) vs break-through (0.5A beyond) within 60 min; value = P(bounce)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| rx|PD|asia | 0.489 | 2257 | 0.487 | +0.2 | 1.000 | 0.57 | 0.506 | 0.442 | unstable |
| rx|PD|london | 0.497 | 2182 | 0.496 | +0.2 | 1.000 | 0.57 | 0.499 | 0.492 | unstable |
| rx|PD|pre | 0.492 | 1311 | 0.492 | +0.0 | 1.000 | 0.50 | 0.511 | 0.439 | unstable |
| rx|PD|nyam | 0.491 | 1590 | 0.496 | -0.4 | 1.000 | 0.43 | 0.496 | 0.475 | unstable |
| rx|PD|nypm | 0.524 | 860 | 0.496 | +1.8 | 1.000 | 0.86 | 0.532 | 0.505 | stable |
| rx|PD|close | 0.480 | 352 | 0.484 | -0.2 | 1.000 | 0.57 | 0.497 | 0.425 | REGIME(2023+ only) |
| rx|ON|nyam | 0.476 | 2019 | 0.498 | -1.8 | 1.000 | 0.71 | 0.467 | 0.497 | stable |
| rx|ON|nypm | 0.493 | 984 | 0.498 | -0.4 | 1.000 | 0.64 | 0.492 | 0.500 | stable |
| rx|ON|close | 0.484 | 457 | 0.488 | -0.2 | 1.000 | 0.57 | 0.496 | 0.493 | unstable |
| rx|IB|nyam | 0.469 | 2238 | 0.496 | -3.1 | 0.082* | 0.79 | 0.472 | 0.457 | stable |
| rx|IB|nypm | 0.515 | 1740 | 0.496 | +1.8 | 1.000 | 0.79 | 0.510 | 0.524 | stable |
| rx|IB|close | 0.531 | 762 | 0.487 | +2.7 | 0.295 | 0.57 | 0.541 | 0.492 | unstable |
| rx|VW1|nyam | 0.470 | 4657 | 0.491 | -3.8 | 0.016** | 0.71 | 0.463 | 0.489 | stable |
| rx|VW1|nypm | 0.501 | 2659 | 0.495 | +0.8 | 1.000 | 0.43 | 0.508 | 0.488 | unstable |
| rx|VW1|close | 0.501 | 1440 | 0.487 | +1.0 | 1.000 | 0.64 | 0.503 | 0.501 | stable |
| rx|VW2|nyam | 0.514 | 3447 | 0.506 | +1.1 | 1.000 | 0.50 | 0.505 | 0.536 | REGIME(2023+ only) |
| rx|VW2|nypm | 0.515 | 1682 | 0.497 | +1.9 | 0.984 | 0.64 | 0.516 | 0.515 | stable |
| rx|VW2|close | 0.502 | 733 | 0.487 | +1.1 | 1.000 | 0.71 | 0.523 | 0.466 | stable |
| rx|RN|asia | 0.487 | 69369 | 0.491 | -2.0 | 0.984 | 0.71 | 0.484 | 0.483 | stable |
| rx|RN|london | 0.490 | 73106 | 0.494 | -1.8 | 1.000 | 0.71 | 0.485 | 0.492 | stable |
| rx|RN|pre | 0.496 | 21131 | 0.499 | -0.8 | 1.000 | 0.64 | 0.489 | 0.503 | stable |
| rx|RN|nyam | 0.493 | 39862 | 0.495 | -1.0 | 1.000 | 0.64 | 0.488 | 0.500 | stable |
| rx|RN|nypm | 0.497 | 27078 | 0.497 | -0.1 | 1.000 | 0.50 | 0.491 | 0.501 | unstable |
| rx|RN|close | 0.491 | 8971 | 0.492 | -0.2 | 1.000 | 0.57 | 0.491 | 0.480 | unstable |

### 7. Failed break (close .25A beyond, back inside within 10 bars): fade follow-through P(0.5A back before 0.5A out)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| fb|PD|asia | 0.506 | 1234 | 0.499 | +0.6 | 1.000 | 0.71 | 0.498 | 0.527 | REGIME(2023+ only) |
| fb|PD|london | 0.499 | 1418 | 0.497 | +0.1 | 1.000 | 0.57 | 0.490 | 0.524 | REGIME(2023+ only) |
| fb|PD|pre | 0.502 | 713 | 0.496 | +0.3 | 1.000 | 0.57 | 0.504 | 0.482 | unstable |
| fb|PD|nyam | 0.516 | 883 | 0.501 | +1.0 | 1.000 | 0.57 | 0.520 | 0.496 | unstable |
| fb|PD|nypm | 0.487 | 474 | 0.497 | -0.5 | 1.000 | 0.50 | 0.472 | 0.521 | unstable |
| fb|PD|close | 0.404 | 156 | 0.500 | -3.0 | 0.098* | 0.86 | 0.419 | 0.385 | stable |
| fb|ON|nyam | 0.507 | 674 | 0.499 | +0.5 | 1.000 | 0.50 | 0.526 | 0.457 | unstable |
| fb|ON|nypm | 0.511 | 491 | 0.500 | +0.6 | 1.000 | 0.50 | 0.486 | 0.579 | REGIME(2023+ only) |
| fb|ON|close | 0.451 | 195 | 0.498 | -1.3 | 1.000 | 0.57 | 0.464 | 0.468 | unstable |
| fb|IB|nyam | 0.455 | 481 | 0.501 | -2.5 | 0.574 | 0.71 | 0.489 | 0.371 | stable |
| fb|IB|nypm | 0.507 | 838 | 0.501 | +0.4 | 1.000 | 0.50 | 0.490 | 0.512 | REGIME(2023+ only) |
| fb|IB|close | 0.384 | 341 | 0.499 | -4.8 | 0.016** | 0.86 | 0.420 | 0.332 | stable |

### 8. Where the range forms
RTH range increments by bin: 9:30 41.0%, 10:00 29.0%, 11:00 11.3%, 12:00 5.8%, 13:00 5.0%, 14:00 4.8%, 15:00 3.2%
Label-day range increments by ET hour (percent of the day): 00h 2.2, 01h 3.3, 02h 4.7, 03h 5.2, 04h 3.7, 05h 2.8, 06h 2.6, 07h 3.3, 08h 9.9, 09h 7.2, 10h 6.6, 11h 3.3, 12h 1.9, 13h 1.6, 14h 2.1, 15h 1.3, 16h 0.5, 18h 10.5, 19h 5.5, 20h 8.0, 21h 8.0, 22h 3.5, 23h 2.1

### 9. Room and liquidity (all years, raw-frame $, 1 lot)
| session | ATR14(5m) $ | A=3xATR5 $ | RT cost $ | room(1 ATR5) | room(A) | median 5-min vol | 1.7% cap (contracts/5min) | lots for $1,200 at 3xATR5 stop |
|--|--|--|--|--|--|--|--|--|
| asia | 76 | 228 | 35 | 2.19 | 6.56 | 192 | 3.3 | 5.3 |
| london | 103 | 308 | 35 | 2.95 | 8.84 | 432 | 7.3 | 3.9 |
| pre | 161 | 484 | 35 | 4.63 | 13.89 | 1280 | 21.8 | 2.5 |
| nyam | 185 | 554 | 35 | 5.30 | 15.91 | 1236 | 21.0 | 2.2 |
| nypm | 125 | 375 | 35 | 3.59 | 10.76 | 486 | 8.3 | 3.2 |
| close | 88 | 265 | 35 | 2.54 | 7.62 | 189 | 3.2 | 4.5 |

room(A) by year: asia: 2013:6.7 2014:4.8 2015:4.4 2016:5.9 2017:4.1 2018:4.1 2019:4.2 2020:10.2 2021:7.0 2022:7.6 2023:6.7 2024:10.1 2025:21.6 2026:41.9; london: 2013:9.5 2014:6.8 2015:6.2 2016:6.8 2017:4.9 2018:5.3 2019:5.6 2020:13.2 2021:9.9 2022:10.9 2023:9.3 2024:13.3 2025:23.5 2026:41.2; pre: 2013:15.3 2014:10.9 2015:10.3 2016:10.5 2017:7.4 2018:7.5 2019:8.8 2020:19.0 2021:16.1 2022:16.8 2023:14.5 2024:19.3 2025:31.4 2026:53.9; nyam: 2013:16.3 2014:11.2 2015:11.4 2016:12.0 2017:8.8 2018:8.4 2019:10.0 2020:22.8 2021:19.0 2022:19.5 2023:18.4 2024:25.1 2025:38.6 2026:67.8; nypm: 2013:11.7 2014:7.9 2015:7.7 2016:8.9 2017:6.7 2018:6.4 2019:7.2 2020:15.5 2021:11.2 2022:12.4 2023:12.0 2024:17.1 2025:26.4 2026:49.3; close: 2013:7.9 2014:5.7 2015:5.2 2016:6.7 2017:5.1 2018:4.7 2019:5.2 2020:10.9 2021:7.1 2022:8.9 2023:7.6 2024:11.0 2025:18.8 2026:35.7

### 10. Versus NQ
Contemporaneous correlation of h-min returns (normalised): asia: 1m -0.01 5m -0.01 15m -0.02 30m -0.02 60m -0.02; london: 1m 0.01 5m 0.01 15m 0.01 30m 0.00 60m -0.01; pre: 1m 0.08 5m 0.09 15m 0.10; nyam: 1m -0.01 5m -0.00 15m -0.01 30m -0.01; nypm: 1m 0.04 5m 0.05 15m 0.07 30m 0.06; close: 1m 0.01 5m 0.01 15m 0.03

Lead/lag (1-15 min, family 180 cells; corr of 1-min normalised returns): cells beating the family null (top 10 by |z|; "NQ->X" = NQ leads GC):
| direction | session | lag min | corr | z | p_family | year sign share |
|--|--|--|--|--|--|--|
| GC->NQ | pre | 1 | +0.0121 | +5.3 | 0.010 | 0.64 |
| NQ->GC | asia | 8 | -0.0040 | -5.0 | 0.010 | 0.64 |
| GC->NQ | london | 13 | +0.0037 | +4.3 | 0.010 | 0.79 |
| NQ->GC | london | 1 | -0.0032 | -3.7 | 0.040 | 0.64 |
| GC->NQ | london | 1 | +0.0032 | +3.7 | 0.040 | 0.64 |
| NQ->GC | nypm | 2 | +0.0045 | +3.6 | 0.050 | 0.86 |
| GC->NQ | close | 4 | +0.0065 | +3.5 | 0.050 | 0.79 |

### 11. Map rows that become book candidates under the FROZEN rule (p_family <= .05 AND room_A(session) > 2.0)
| map row | direction | stat | p_family | room_A | year sign share | stability | 1.7% cap >= 1 contract/5min in session |
|--|--|--|--|--|--|--|--|
| AC|asia|5m | reversion | -0.022 | 0.003 | 6.6 | 0.93 |  | yes |
| AC|london|5m | reversion | -0.021 | 0.003 | 8.8 | 0.93 |  | yes |
| AC|pre|5m | reversion | -0.022 | 0.007 | 13.9 | 0.64 |  | yes |
| AC|nypm|5m | reversion | -0.020 | 0.003 | 10.8 | 0.93 |  | yes |
| AC|close|5m | reversion | -0.053 | 0.003 | 7.6 | 1.00 |  | yes |
| AC|london|15m | reversion | -0.021 | 0.003 | 8.8 | 0.93 |  | yes |
| AC|nypm|15m | reversion | -0.015 | 0.040 | 10.8 | 0.79 |  | yes |
| AC|close|15m | reversion | -0.041 | 0.003 | 7.6 | 0.71 |  | yes |
| AC|london|30m | reversion | -0.016 | 0.027 | 8.8 | 0.86 |  | yes |
| AC|close|30m | reversion | -0.056 | 0.003 | 7.6 | 0.86 |  | yes |
| AC|asia|60m | reversion | -0.022 | 0.023 | 6.6 | 0.93 |  | yes |
| fb|IB|close | level-break | +0.384 | 0.016 | 7.6 | 0.86 | stable | yes |
| rx|VW1|nyam | level-break | +0.470 | 0.016 | 15.9 | 0.71 | stable | yes |
| gap|b3|h1 | level-bounce | +0.062 | 0.016 | 15.9 | 0.86 | stable | yes |
| vr|asia|5 | reversion | +0.911 | 0.016 | 6.6 | 1.00 | stable | yes |
| vr|asia|15 | reversion | +0.885 | 0.016 | 6.6 | 1.00 | stable | yes |
| vr|asia|30 | reversion | +0.877 | 0.016 | 6.6 | 1.00 | stable | yes |
| vr|asia|60 | reversion | +0.871 | 0.016 | 6.6 | 1.00 | stable | yes |
| vr|asia|120 | reversion | +0.862 | 0.016 | 6.6 | 0.93 | stable | yes |
| hurst|asia | reversion | +0.492 | 0.016 | 6.6 | 0.93 | stable | yes |
| vr|london|5 | reversion | +0.934 | 0.016 | 8.8 | 1.00 | stable | yes |
| vr|london|15 | reversion | +0.900 | 0.016 | 8.8 | 1.00 | stable | yes |
| vr|london|30 | reversion | +0.877 | 0.016 | 8.8 | 1.00 | stable | yes |
| vr|london|60 | reversion | +0.860 | 0.016 | 8.8 | 1.00 | stable | yes |
| vr|london|120 | reversion | +0.850 | 0.016 | 8.8 | 0.93 | stable | yes |
| hurst|london | reversion | +0.485 | 0.016 | 8.8 | 0.93 | stable | yes |
| vr|pre|5 | reversion | +0.950 | 0.016 | 13.9 | 0.93 | stable | yes |
| vr|pre|15 | reversion | +0.919 | 0.016 | 13.9 | 0.93 | stable | yes |
| hurst|pre | reversion | +0.485 | 0.016 | 13.9 | 0.71 | stable | yes |
| vr|nyam|5 | reversion | +0.970 | 0.016 | 15.9 | 0.79 | stable | yes |
| vr|nyam|15 | reversion | +0.958 | 0.016 | 15.9 | 0.71 | stable | yes |
| vr|nyam|30 | reversion | +0.959 | 0.016 | 15.9 | 0.79 | stable | yes |
| vr|nypm|5 | reversion | +0.922 | 0.016 | 10.8 | 1.00 | stable | yes |
| vr|nypm|15 | reversion | +0.893 | 0.016 | 10.8 | 1.00 | stable | yes |
| vr|nypm|30 | reversion | +0.876 | 0.016 | 10.8 | 1.00 | stable | yes |
| vr|nypm|60 | reversion | +0.870 | 0.016 | 10.8 | 0.93 | stable | yes |
| hurst|nypm | reversion | +0.488 | 0.016 | 10.8 | 0.79 | stable | yes |
| vr|close|5 | reversion | +0.875 | 0.016 | 7.6 | 1.00 | stable | yes |
| vr|close|15 | reversion | +0.807 | 0.016 | 7.6 | 1.00 | stable | yes |
| vr|close|30 | reversion | +0.770 | 0.016 | 7.6 | 1.00 | stable | yes |
| hurst|close | reversion | +0.464 | 0.016 | 7.6 | 0.86 | stable | yes |
| vr|rth|5 | reversion | +0.950 | 0.016 | 15.9 | 1.00 | stable | yes |
| vr|rth|15 | reversion | +0.929 | 0.016 | 15.9 | 1.00 | stable | yes |
| vr|rth|30 | reversion | +0.923 | 0.016 | 15.9 | 1.00 | stable | yes |
| vr|rth|60 | reversion | +0.918 | 0.016 | 15.9 | 0.86 | stable | yes |
| vr|rth|120 | reversion | +0.898 | 0.016 | 15.9 | 0.79 | stable | yes |
| hurst|rth | reversion | +0.492 | 0.016 | 15.9 | 0.79 | stable | yes |

CHAR-B note (GC): library and frozen rule unchanged from CHAR-A (prereg sha 980bedf6..), CHAR-B scope sha e649ef5d.. in DECISIONS. Added constants: round-number grid GC 10 pts / CL 1.00 / ZN 0.5 / ZB 1.0 (my assumption), cost = PROXY-STD fee $4.84 RT + 1 tick in + 2 ticks stop out (FEES.md has no GC entry; no fee edge claimed). The 1-minute negative autocorrelation is partly last-print/bid-ask noise: the books (evaluator) pay the measured-proxy cost to find out whether the 5-60 min reversion survives it. Data end 2026-10-16 (no 10-17..30 bars for these four).

## CL - character map (CHAR-B via CHAR-A char_lib, 2026-11-05T23:30Z)
Base: CL CME front-month (.v.0) 1-min bars from 2013-01 to 2026-10, percent frame (multiplicative roll-adjusted), 1-min approximation (no tick path), 3448 usable label days; ET clock, sessions asia 18:00-02:00 / london 02:00-08:30 / pre 08:30-09:30 / nyam 09:30-12:00 / nypm 12:00-15:00 / close 15:00-16:55. Nulls: within-year shuffled-day (AC B=300; structure B=100 worlds; levels recomputed on the shuffled path; round numbers 60 random grid phases); p_family = Westfall-Young max-|z| over the block (AC family 153 cells, structure family 92 cells). `**` p_family<=.05, `*` <=.10. Prereg sha256 980bedf6bad3f1669de9efb93831fa4622d88577c892d9359b7f57ba93c9dbcf. Descriptive only: no PASS, nothing live.

### Plain paragraph
At 1 minute every session has negative autocorrelation (-0.060 to -0.012; bid-ask bounce / last-print noise, not a tradable edge by itself). asia: reverts at 5 min (-0.027). london: reverts at 5 min (-0.012). nypm: reverts at 5 min (-0.019). close: reverts at 5/30 min (-0.024, -0.073). Day types (RTH): 44% trend days (efficiency ratio >= .5; shuffled null 46%, p_fam 1.000), 26% range days (<.25; null 26%, p_fam 1.000); the IB (09:30-10:30) is extended on one side only on 66% of days and on both on 32%, and a one-sided extension closes beyond the IB edge 69% of the time (null 71%). RTH variance ratio at 30 min 0.931 (shuffled null 0.998, p_fam 0.016); Hurst 0.501. The RTH range forms 9:30 (32%), 10:00 (30%), 11:00 (16%) of the range increments. Level reactions that beat the family null: PD|asia bounces 42% of touches (less, i.e. breaks through more than the shuffled null 47%); RN|asia bounces 48% of touches (less, i.e. breaks through more than the shuffled null 49%); RN|close bounces 47% of touches (less, i.e. breaks through more than the shuffled null 50%). Failed-break follow-through beating the null: PD|london 46% (null 50%). Room (median 3xATR14(5m) $ / round-trip cost $35 per lot): asia 4.6x, london 7.4x, pre 10.5x, nyam 14.7x, nypm 13.0x, close 8.4x (1xATR5 room 4.9x in nyam, 1.5x in asia).

### 1. Autocorrelation of h-min returns (corr(past h, next h), both inside the session), pooled; cell = corr (pre-2023 mean | 2023+ mean) p_family
| session | 1 min | 5 min | 15 min | 30 min | 60 min | 120 min |
|--|--|--|--|--|--|--|
| asia | -0.056 (-0.070|-0.038) p0.003** ys1.00 | -0.027 (-0.038|-0.018) p0.003** ys0.93 | -0.006 (-0.020|+0.010) p0.900 ys0.71 | +0.006 (-0.004|+0.009) p1.000 ys0.36 | +0.004 (+0.006|-0.009) p1.000 ys0.50 | +0.014 (+0.009|-0.023) p1.000 ys0.43 |
| london | -0.028 (-0.036|-0.012) p0.003** ys1.00 | -0.012 (-0.015|-0.006) p0.003** ys0.86 | +0.001 (-0.004|+0.007) p1.000 ys0.36 | +0.003 (-0.004|+0.016) p1.000 ys0.57 | +0.002 (+0.003|-0.005) p1.000 ys0.64 | +0.007 (-0.008|+0.034) p1.000 ys0.50 |
| pre | -0.014 (-0.023|+0.006) p0.007** ys0.71 | -0.010 (-0.012|-0.006) p0.907 ys0.57 | -0.007 (-0.006|-0.017) p1.000 ys0.57 | -0.063 (-0.063|-0.082) p0.076* ys0.93 | - | - |
| nyam | -0.012 (-0.016|-0.001) p0.003** ys0.64 | -0.006 (-0.007|-0.008) p1.000 ys0.71 | +0.005 (+0.007|-0.007) p1.000 ys0.50 | +0.013 (+0.016|-0.005) p1.000 ys0.64 | +0.023 (+0.020|+0.035) p1.000 ys0.50 | - |
| nypm | -0.036 (-0.042|-0.007) p0.003** ys0.86 | -0.019 (-0.021|-0.010) p0.003** ys0.86 | -0.009 (-0.009|-0.011) p1.000 ys0.57 | -0.000 (-0.002|-0.004) p1.000 ys0.57 | +0.021 (+0.027|-0.019) p1.000 ys0.64 | - |
| close | -0.060 (-0.072|-0.029) p0.003** ys1.00 | -0.024 (-0.033|-0.001) p0.003** ys0.79 | -0.014 (-0.018|-0.015) p0.944 ys0.64 | -0.073 (-0.054|-0.079) p0.003** ys0.79 | - | - |

Hour cells (h >= 5) beating the family null, top 14 by |z| (hour = ET hour of the decision bar):
| h | session | hour ET | corr | z | p_family | year sign share | pre-2023 | 2023+ |
|--|--|--|--|--|--|--|--|--|
| 5 | asia | 18 | -0.053 | -10.8 | 0.003 | 0.93 | -0.056 | -0.062 |
| 5 | asia | 22 | -0.044 | -10.6 | 0.003 | 0.93 | -0.048 | -0.026 |
| 5 | asia | 00 | -0.044 | -10.6 | 0.003 | 0.93 | -0.065 | -0.034 |
| 5 | close | 15 | -0.036 | -8.3 | 0.003 | 0.79 | -0.060 | +0.008 |
| 30 | close | 15 | -0.104 | -8.2 | 0.003 | 0.86 | -0.083 | -0.098 |
| 5 | london | 02 | -0.034 | -8.0 | 0.003 | 0.86 | -0.042 | -0.016 |
| 5 | asia | 23 | -0.029 | -7.0 | 0.003 | 0.86 | -0.048 | -0.023 |
| 5 | nypm | 12 | -0.030 | -6.8 | 0.003 | 0.79 | -0.031 | -0.027 |
| 15 | asia | 18 | -0.043 | -6.1 | 0.007 | 0.79 | -0.062 | -0.025 |
| 5 | asia | 19 | -0.024 | -5.6 | 0.007 | 0.71 | -0.038 | -0.005 |
| 15 | asia | 00 | -0.039 | -5.2 | 0.013 | 0.71 | -0.033 | -0.064 |
| 5 | london | 03 | -0.022 | -5.1 | 0.013 | 0.79 | -0.031 | -0.008 |
| 60 | asia | 23 | +0.065 | +4.9 | 0.013 | 0.50 | +0.015 | +0.017 |
| 5 | asia | 01 | -0.020 | -4.5 | 0.023 | 0.71 | -0.038 | -0.004 |

### 2. Variance ratio VR(q) and Hurst (1.0 = random walk; <1 reverting; edge-bias corrected), cell = value (null) p_family
| session | VR5 | VR15 | VR30 | VR60 | VR120 | Hurst |
|--|--|--|--|--|--|--|
| asia | 0.892 (1.000) p0.016** | 0.864 (0.999) p0.016** | 0.860 (0.999) p0.016** | 0.869 (0.999) p0.016** | 0.884 (0.999) p0.016** | 0.499 (0.500) p1.000 |
| london | 0.948 (1.000) p0.016** | 0.934 (0.999) p0.016** | 0.936 (0.999) p0.016** | 0.943 (1.000) p0.016** | 0.955 (1.001) p0.016** | 0.501 (0.500) p1.000 |
| pre | 0.974 (0.999) p0.016** | 0.964 (0.998) p0.279 | - | - | - | 0.496 (0.500) p1.000 |
| nyam | 0.972 (0.999) p0.016** | 0.964 (0.998) p0.016** | 0.968 (0.997) p0.180 | - | - | 0.498 (0.499) p1.000 |
| nypm | 0.929 (1.000) p0.016** | 0.904 (1.000) p0.016** | 0.898 (0.999) p0.016** | 0.903 (0.999) p0.016** | - | 0.494 (0.500) p0.770 |
| close | 0.890 (0.999) p0.016** | 0.864 (0.998) p0.016** | 0.854 (0.998) p0.016** | - | - | 0.488 (0.500) p0.016** |
| rth | 0.951 (0.999) p0.016** | 0.933 (0.998) p0.016** | 0.931 (0.998) p0.016** | 0.937 (0.997) p0.016** | 0.956 (0.997) p0.049** | 0.501 (0.500) p1.000 |

### 3. Day types (ex-post labels of the RTH day)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| day|trend | 0.442 | 3448 | 0.455 | -1.6 | 1.000 | 0.50 | 0.440 | 0.444 | unstable |
| day|range | 0.259 | 3448 | 0.258 | +0.1 | 1.000 | 0.43 | 0.262 | 0.255 | unstable |
| day|er | 0.454 | 3448 | 0.460 | -1.4 | 1.000 | 0.50 | 0.451 | 0.457 | unstable |
| day|ib_none | 0.026 | 3448 | 0.008 | +11.9 | 0.016** | 1.00 | 0.025 | 0.025 | stable |
| day|ib_one | 0.658 | 3448 | 0.620 | +4.9 | 0.016** | 0.79 | 0.658 | 0.655 | stable |
| day|ib_both | 0.316 | 3448 | 0.372 | -7.1 | 0.016** | 0.86 | 0.318 | 0.319 | stable |
| day|ib_one_closebeyond | 0.687 | 2269 | 0.714 | -3.0 | 0.180 | 0.79 | 0.686 | 0.687 | stable |

### 4. 1A -> 2A continuation vs give-back-half from the session open (A = 3 x ATR14(5m)); value = P(continue | resolved)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| cont|asia | 0.345 | 2648 | 0.378 | -3.9 | 0.016** | 0.86 | 0.331 | 0.366 | stable |
| cont|london | 0.334 | 3441 | 0.350 | -2.0 | 0.967 | 0.57 | 0.328 | 0.353 | unstable |
| cont|pre | 0.272 | 1733 | 0.271 | +0.1 | 1.000 | 0.43 | 0.272 | 0.267 | unstable |
| cont|nyam | 0.330 | 2651 | 0.317 | +1.5 | 1.000 | 0.71 | 0.329 | 0.329 | stable |
| cont|nypm | 0.305 | 1208 | 0.254 | +4.5 | 0.016** | 0.71 | 0.302 | 0.316 | stable |
| cont|close | 0.341 | 217 | 0.274 | +2.4 | 0.672 | 0.43 | 0.332 | 0.365 | unstable |
| cont|rth | 0.344 | 3201 | 0.329 | +1.9 | 1.000 | 0.79 | 0.342 | 0.349 | stable |

### 5. Gap fill by size bucket (b0 .05-.10, b1 .10-.25, b2 .25-.50, b3 >.50 of the 20-day mean RTH range); day = filled during RTH, h1 = within 60 min
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| gap|b0|day | 0.907 | 259 | 0.901 | +0.3 | 1.000 | 0.43 | 0.887 | 0.970 | REGIME(2023+ only) |
| gap|b0|h1 | 0.788 | 259 | 0.791 | -0.1 | 1.000 | 0.50 | 0.786 | 0.793 | unstable |
| gap|b1|day | 0.746 | 669 | 0.777 | -1.7 | 1.000 | 0.79 | 0.737 | 0.779 | stable |
| gap|b1|h1 | 0.519 | 669 | 0.553 | -1.8 | 1.000 | 0.71 | 0.513 | 0.536 | stable |
| gap|b2|day | 0.539 | 975 | 0.547 | -0.4 | 1.000 | 0.57 | 0.540 | 0.524 | unstable |
| gap|b2|h1 | 0.236 | 975 | 0.222 | +1.0 | 1.000 | 0.57 | 0.238 | 0.224 | unstable |
| gap|b3|day | 0.221 | 1314 | 0.210 | +1.0 | 1.000 | 0.57 | 0.230 | 0.200 | unstable |
| gap|b3|h1 | 0.037 | 1314 | 0.026 | +3.0 | 0.180 | 0.79 | 0.041 | 0.027 | stable |

### 6. Level reaction: first touch -> bounce (0.5A reverse) vs break-through (0.5A beyond) within 60 min; value = P(bounce)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| rx|PD|asia | 0.424 | 1487 | 0.474 | -4.7 | 0.016** | 0.79 | 0.417 | 0.445 | stable |
| rx|PD|london | 0.471 | 2264 | 0.490 | -1.8 | 1.000 | 0.64 | 0.461 | 0.489 | stable |
| rx|PD|pre | 0.503 | 1172 | 0.503 | +0.1 | 1.000 | 0.36 | 0.508 | 0.480 | unstable |
| rx|PD|nyam | 0.509 | 1906 | 0.501 | +0.7 | 1.000 | 0.57 | 0.518 | 0.492 | unstable |
| rx|PD|nypm | 0.536 | 1098 | 0.507 | +1.9 | 1.000 | 0.71 | 0.534 | 0.535 | stable |
| rx|PD|close | 0.469 | 239 | 0.502 | -1.1 | 1.000 | 0.50 | 0.481 | 0.468 | unstable |
| rx|ON|nyam | 0.494 | 2747 | 0.506 | -1.3 | 1.000 | 0.71 | 0.502 | 0.464 | stable |
| rx|ON|nypm | 0.485 | 1415 | 0.508 | -1.7 | 1.000 | 0.64 | 0.499 | 0.436 | stable |
| rx|ON|close | 0.509 | 340 | 0.505 | +0.1 | 1.000 | 0.50 | 0.522 | 0.503 | unstable |
| rx|IB|nyam | 0.475 | 3372 | 0.501 | -3.2 | 0.148 | 0.64 | 0.478 | 0.469 | stable |
| rx|IB|nypm | 0.501 | 2009 | 0.508 | -0.7 | 1.000 | 0.64 | 0.491 | 0.523 | stable |
| rx|IB|close | 0.539 | 412 | 0.501 | +2.0 | 0.984 | 0.71 | 0.539 | 0.554 | stable |
| rx|VW1|nyam | 0.497 | 5531 | 0.499 | -0.4 | 1.000 | 0.50 | 0.497 | 0.500 | unstable |
| rx|VW1|nypm | 0.512 | 3204 | 0.506 | +0.7 | 1.000 | 0.71 | 0.517 | 0.499 | stable |
| rx|VW1|close | 0.477 | 791 | 0.504 | -1.7 | 1.000 | 0.57 | 0.497 | 0.449 | unstable |
| rx|VW2|nyam | 0.519 | 4382 | 0.511 | +1.1 | 1.000 | 0.57 | 0.523 | 0.506 | unstable |
| rx|VW2|nypm | 0.502 | 2006 | 0.512 | -1.1 | 1.000 | 0.57 | 0.495 | 0.503 | unstable |
| rx|VW2|close | 0.487 | 437 | 0.505 | -0.9 | 1.000 | 0.64 | 0.462 | 0.540 | stable |
| rx|RN|asia | 0.479 | 33650 | 0.488 | -3.6 | 0.016** | 0.79 | 0.483 | 0.469 | stable |
| rx|RN|london | 0.486 | 58268 | 0.492 | -2.2 | 0.836 | 0.71 | 0.485 | 0.482 | stable |
| rx|RN|pre | 0.493 | 16030 | 0.500 | -1.6 | 1.000 | 0.64 | 0.490 | 0.497 | stable |
| rx|RN|nyam | 0.493 | 38005 | 0.498 | -1.5 | 1.000 | 0.64 | 0.494 | 0.491 | stable |
| rx|RN|nypm | 0.496 | 29394 | 0.507 | -3.2 | 0.148 | 0.71 | 0.501 | 0.482 | stable |
| rx|RN|close | 0.474 | 4728 | 0.498 | -3.4 | 0.049** | 0.86 | 0.474 | 0.477 | stable |

### 7. Failed break (close .25A beyond, back inside within 10 bars): fade follow-through P(0.5A back before 0.5A out)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| fb|PD|asia | 0.460 | 803 | 0.500 | -2.6 | 0.492 | 0.71 | 0.443 | 0.477 | stable |
| fb|PD|london | 0.456 | 1488 | 0.498 | -3.6 | 0.016** | 0.79 | 0.440 | 0.494 | stable |
| fb|PD|pre | 0.504 | 675 | 0.498 | +0.3 | 1.000 | 0.43 | 0.502 | 0.502 | unstable |
| fb|PD|nyam | 0.541 | 1115 | 0.499 | +2.8 | 0.377 | 0.86 | 0.553 | 0.514 | stable |
| fb|PD|nypm | 0.502 | 612 | 0.500 | +0.1 | 1.000 | 0.50 | 0.509 | 0.493 | unstable |
| fb|PD|close | 0.438 | 96 | 0.492 | -1.1 | 1.000 | 0.36 | 0.415 | 0.625 | unstable |
| fb|ON|nyam | 0.507 | 1100 | 0.502 | +0.4 | 1.000 | 0.57 | 0.511 | 0.506 | unstable |
| fb|ON|nypm | 0.494 | 723 | 0.503 | -0.5 | 1.000 | 0.36 | 0.487 | 0.511 | unstable |
| fb|ON|close | 0.533 | 107 | 0.499 | +0.8 | 1.000 | 0.64 | 0.460 | 0.635 | REGIME(2023+ only) |
| fb|IB|nyam | 0.517 | 989 | 0.499 | +1.0 | 1.000 | 0.64 | 0.528 | 0.500 | stable |
| fb|IB|nypm | 0.486 | 1051 | 0.502 | -1.2 | 1.000 | 0.57 | 0.492 | 0.470 | unstable |
| fb|IB|close | 0.471 | 155 | 0.503 | -1.0 | 1.000 | 0.57 | 0.395 | 0.583 | unstable |

### 8. Where the range forms
RTH range increments by bin: 9:30 32.4%, 10:00 29.8%, 11:00 16.1%, 12:00 7.5%, 13:00 6.0%, 14:00 6.6%, 15:00 1.6%
Label-day range increments by ET hour (percent of the day): 00h 1.4, 01h 2.1, 02h 3.3, 03h 6.0, 04h 6.1, 05h 4.8, 06h 3.7, 07h 3.7, 08h 5.9, 09h 9.7, 10h 8.9, 11h 6.6, 12h 3.4, 13h 3.1, 14h 3.4, 15h 0.8, 16h 0.9, 18h 8.9, 19h 3.1, 20h 5.6, 21h 4.7, 22h 2.4, 23h 1.5

### 9. Room and liquidity (all years, raw-frame $, 1 lot)
| session | ATR14(5m) $ | A=3xATR5 $ | RT cost $ | room(1 ATR5) | room(A) | median 5-min vol | 1.7% cap (contracts/5min) | lots for $1,200 at 3xATR5 stop |
|--|--|--|--|--|--|--|--|--|
| asia | 54 | 162 | 35 | 1.55 | 4.64 | 125 | 2.1 | 7.4 |
| london | 86 | 259 | 35 | 2.48 | 7.45 | 574 | 9.8 | 4.6 |
| pre | 122 | 367 | 35 | 3.51 | 10.54 | 1975 | 33.6 | 3.3 |
| nyam | 170 | 511 | 35 | 4.89 | 14.68 | 2581 | 43.9 | 2.3 |
| nypm | 151 | 454 | 35 | 4.35 | 13.04 | 1467 | 24.9 | 2.6 |
| close | 97 | 292 | 35 | 2.79 | 8.37 | 302 | 5.1 | 4.1 |

room(A) by year: asia: 2013:4.4 2014:3.8 2015:4.5 2016:4.0 2017:2.5 2018:3.8 2019:4.0 2020:5.4 2021:5.6 2022:10.9 2023:5.4 2024:4.3 2025:4.2 2026:12.3; london: 2013:6.7 2014:5.7 2015:7.4 2016:6.1 2017:4.7 2018:6.0 2019:6.3 2020:7.6 2021:8.7 2022:18.0 2023:10.1 2024:8.3 2025:7.5 2026:18.7; pre: 2013:12.0 2014:10.0 2015:11.8 2016:8.8 2017:6.3 2018:8.2 2019:8.4 2020:9.4 2021:11.5 2022:23.4 2023:13.4 2024:11.2 2025:9.1 2026:22.2; nyam: 2013:16.1 2014:14.1 2015:16.6 2016:12.1 2017:8.7 2018:12.6 2019:12.2 2020:12.5 2021:15.8 2022:31.0 2023:19.1 2024:15.6 2025:12.1 2026:25.5; nypm: 2013:15.6 2014:14.1 2015:16.2 2016:10.1 2017:7.4 2018:11.2 2019:10.5 2020:10.7 2021:12.3 2022:26.0 2023:16.3 2024:13.1 2025:10.1 2026:22.5; close: 2013:11.6 2014:10.3 2015:11.2 2016:6.7 2017:4.7 2018:7.0 2019:6.8 2020:7.5 2021:7.6 2022:17.0 2023:9.1 2024:7.6 2025:6.2 2026:16.3

### 10. Versus NQ
Contemporaneous correlation of h-min returns (normalised): asia: 1m 0.16 5m 0.19 15m 0.21 30m 0.21 60m 0.21; london: 1m 0.16 5m 0.17 15m 0.16 30m 0.16 60m 0.18; pre: 1m 0.13 5m 0.14 15m 0.13; nyam: 1m 0.17 5m 0.18 15m 0.18 30m 0.18; nypm: 1m 0.17 5m 0.18 15m 0.17 30m 0.17; close: 1m 0.14 5m 0.16 15m 0.16

Lead/lag (1-15 min, family 180 cells; corr of 1-min normalised returns): cells beating the family null (top 10 by |z|; "NQ->X" = NQ leads CL):
| direction | session | lag min | corr | z | p_family | year sign share |
|--|--|--|--|--|--|--|
| NQ->CL | asia | 1 | +0.0196 | +18.4 | 0.010 | 0.93 |
| NQ->CL | london | 1 | +0.0054 | +6.8 | 0.010 | 0.71 |
| NQ->CL | close | 1 | +0.0083 | +5.6 | 0.010 | 0.79 |
| NQ->CL | nyam | 1 | +0.0080 | +5.5 | 0.010 | 0.93 |
| CL->NQ | asia | 8 | +0.0038 | +4.5 | 0.010 | 0.71 |
| NQ->CL | asia | 2 | +0.0038 | +4.3 | 0.010 | 0.79 |
| NQ->CL | nypm | 2 | -0.0051 | -4.2 | 0.010 | 0.79 |
| NQ->CL | asia | 8 | +0.0032 | +3.8 | 0.020 | 0.86 |

### 11. Map rows that become book candidates under the FROZEN rule (p_family <= .05 AND room_A(session) > 2.0)
| map row | direction | stat | p_family | room_A | year sign share | stability | 1.7% cap >= 1 contract/5min in session |
|--|--|--|--|--|--|--|--|
| AC|asia|5m | reversion | -0.027 | 0.003 | 4.6 | 0.93 |  | yes |
| AC|london|5m | reversion | -0.012 | 0.003 | 7.4 | 0.86 |  | yes |
| AC|nypm|5m | reversion | -0.019 | 0.003 | 13.0 | 0.86 |  | yes |
| AC|close|5m | reversion | -0.024 | 0.003 | 8.4 | 0.79 |  | yes |
| AC|close|30m | reversion | -0.073 | 0.003 | 8.4 | 0.79 |  | yes |
| rx|PD|asia | level-break | +0.424 | 0.016 | 4.6 | 0.79 | stable | yes |
| fb|PD|london | level-break | +0.456 | 0.016 | 7.4 | 0.79 | stable | yes |
| vr|asia|5 | reversion | +0.892 | 0.016 | 4.6 | 1.00 | stable | yes |
| vr|asia|15 | reversion | +0.864 | 0.016 | 4.6 | 1.00 | stable | yes |
| vr|asia|30 | reversion | +0.860 | 0.016 | 4.6 | 0.93 | stable | yes |
| vr|asia|60 | reversion | +0.869 | 0.016 | 4.6 | 0.93 | stable | yes |
| vr|asia|120 | reversion | +0.884 | 0.016 | 4.6 | 0.86 | stable | yes |
| vr|london|5 | reversion | +0.948 | 0.016 | 7.4 | 1.00 | stable | yes |
| vr|london|15 | reversion | +0.934 | 0.016 | 7.4 | 1.00 | stable | yes |
| vr|london|30 | reversion | +0.936 | 0.016 | 7.4 | 0.86 | stable | yes |
| vr|london|60 | reversion | +0.943 | 0.016 | 7.4 | 0.79 | stable | yes |
| vr|london|120 | reversion | +0.955 | 0.016 | 7.4 | 0.79 | stable | yes |
| vr|pre|5 | reversion | +0.974 | 0.016 | 10.5 | 0.71 | stable | yes |
| vr|nyam|5 | reversion | +0.972 | 0.016 | 14.7 | 0.71 | stable | yes |
| vr|nyam|15 | reversion | +0.964 | 0.016 | 14.7 | 0.86 | stable | yes |
| vr|nypm|5 | reversion | +0.929 | 0.016 | 13.0 | 0.93 | stable | yes |
| vr|nypm|15 | reversion | +0.904 | 0.016 | 13.0 | 0.93 | stable | yes |
| vr|nypm|30 | reversion | +0.898 | 0.016 | 13.0 | 1.00 | stable | yes |
| vr|nypm|60 | reversion | +0.903 | 0.016 | 13.0 | 0.71 | stable | yes |
| vr|close|5 | reversion | +0.890 | 0.016 | 8.4 | 1.00 | stable | yes |
| vr|close|15 | reversion | +0.864 | 0.016 | 8.4 | 1.00 | stable | yes |
| vr|close|30 | reversion | +0.854 | 0.016 | 8.4 | 0.93 | stable | yes |
| hurst|close | reversion | +0.488 | 0.016 | 8.4 | 0.71 | stable | yes |
| vr|rth|5 | reversion | +0.951 | 0.016 | 14.7 | 0.93 | stable | yes |
| vr|rth|15 | reversion | +0.933 | 0.016 | 14.7 | 1.00 | stable | yes |
| vr|rth|30 | reversion | +0.931 | 0.016 | 14.7 | 0.93 | stable | yes |
| vr|rth|60 | reversion | +0.937 | 0.016 | 14.7 | 0.93 | stable | yes |
| vr|rth|120 | reversion | +0.956 | 0.049 | 14.7 | 0.71 | stable | yes |
| rx|RN|asia | level-break | +0.479 | 0.016 | 4.6 | 0.79 | stable | yes |
| rx|RN|close | level-break | +0.474 | 0.049 | 8.4 | 0.86 | stable | yes |

CHAR-B note (CL): library and frozen rule unchanged from CHAR-A (prereg sha 980bedf6..), CHAR-B scope sha e649ef5d.. in DECISIONS. Added constants: round-number grid GC 10 pts / CL 1.00 / ZN 0.5 / ZB 1.0 (my assumption), cost = PROXY-STD fee $4.84 RT + 1 tick in + 2 ticks stop out (FEES.md has no CL entry; no fee edge claimed). The 1-minute negative autocorrelation is partly last-print/bid-ask noise: the books (evaluator) pay the measured-proxy cost to find out whether the 5-60 min reversion survives it. Data end 2026-10-16 (no 10-17..30 bars for these four).

## ZN - character map (CHAR-B via CHAR-A char_lib, 2026-11-05T23:30Z)
Base: ZN CME front-month (.v.0) 1-min bars from 2013-01 to 2026-10, percent frame (multiplicative roll-adjusted), 1-min approximation (no tick path), 3298 usable label days; ET clock, sessions asia 18:00-02:00 / london 02:00-08:30 / pre 08:30-09:30 / nyam 09:30-12:00 / nypm 12:00-15:00 / close 15:00-16:55. Nulls: within-year shuffled-day (AC B=300; structure B=100 worlds; levels recomputed on the shuffled path; round numbers 60 random grid phases); p_family = Westfall-Young max-|z| over the block (AC family 153 cells, structure family 92 cells). `**` p_family<=.05, `*` <=.10. Prereg sha256 980bedf6bad3f1669de9efb93831fa4622d88577c892d9359b7f57ba93c9dbcf. Descriptive only: no PASS, nothing live.

### Plain paragraph
At 1 minute every session has negative autocorrelation (-0.260 to -0.114; bid-ask bounce / last-print noise, not a tradable edge by itself). asia: reverts at 5/15/30 min (-0.147, -0.077, -0.037). london: reverts at 5/15/30/60/120 min (-0.098, -0.054, -0.042, -0.026, -0.041). pre: reverts at 5 min (-0.060). nyam: reverts at 5 min (-0.061). nypm: reverts at 5/15/30 min (-0.098, -0.055, -0.035). close: reverts at 5/15 min (-0.135, -0.063). Day types (RTH): 45% trend days (efficiency ratio >= .5; shuffled null 46%, p_fam 1.000), 26% range days (<.25; null 26%, p_fam 1.000); the IB (09:30-10:30) is extended on one side only on 72% of days and on both on 22%, and a one-sided extension closes beyond the IB edge 61% of the time (null 71%). RTH variance ratio at 30 min 0.573 (shuffled null 1.000, p_fam 0.016); Hurst 0.464. The RTH range forms 9:30 (36%), 10:00 (28%), 11:00 (12%) of the range increments. Level reactions that beat the family null: PD|asia bounces 64% of touches (more than the shuffled null 46%); PD|london bounces 62% of touches (more than the shuffled null 49%); PD|nyam bounces 55% of touches (more than the shuffled null 50%); PD|nypm bounces 59% of touches (more than the shuffled null 50%); PD|close bounces 64% of touches (more than the shuffled null 50%); ON|nypm bounces 56% of touches (more than the shuffled null 50%); ON|close bounces 59% of touches (more than the shuffled null 50%); IB|nyam bounces 58% of touches (more than the shuffled null 51%); IB|nypm bounces 60% of touches (more than the shuffled null 50%); IB|close bounces 63% of touches (more than the shuffled null 50%); VW2|nyam bounces 54% of touches (more than the shuffled null 51%); VW2|close bounces 56% of touches (more than the shuffled null 51%). Failed-break follow-through beating the null: PD|asia 35% (null 50%); PD|london 40% (null 50%); PD|nypm 43% (null 50%); PD|close 37% (null 50%); ON|nyam 43% (null 50%); ON|nypm 39% (null 50%); ON|close 34% (null 50%); IB|nyam 44% (null 50%); IB|nypm 41% (null 50%); IB|close 38% (null 50%). Room (median 3xATR14(5m) $ / round-trip cost $52 per lot): asia 1.2x, london 1.7x, pre 2.6x, nyam 2.8x, nypm 2.3x, close 2.0x (1xATR5 room 0.9x in nyam, 0.4x in asia).

### 1. Autocorrelation of h-min returns (corr(past h, next h), both inside the session), pooled; cell = corr (pre-2023 mean | 2023+ mean) p_family
| session | 1 min | 5 min | 15 min | 30 min | 60 min | 120 min |
|--|--|--|--|--|--|--|
| asia | -0.216 (-0.207|-0.238) p0.003** ys1.00 | -0.147 (-0.147|-0.166) p0.003** ys1.00 | -0.077 (-0.078|-0.096) p0.003** ys1.00 | -0.037 (-0.042|-0.050) p0.003** ys0.93 | -0.018 (-0.026|-0.030) p0.156 ys0.71 | -0.008 (-0.025|-0.045) p1.000 ys0.79 |
| london | -0.213 (-0.210|-0.222) p0.003** ys1.00 | -0.098 (-0.098|-0.110) p0.003** ys1.00 | -0.054 (-0.055|-0.060) p0.003** ys1.00 | -0.042 (-0.045|-0.040) p0.003** ys1.00 | -0.026 (-0.031|-0.018) p0.020** ys0.79 | -0.041 (-0.051|-0.030) p0.020** ys0.79 |
| pre | -0.114 (-0.122|-0.114) p0.003** ys1.00 | -0.060 (-0.064|-0.055) p0.003** ys1.00 | -0.015 (-0.026|-0.006) p1.000 ys0.57 | -0.023 (-0.006|-0.075) p1.000 ys0.64 | - | - |
| nyam | -0.157 (-0.162|-0.154) p0.003** ys1.00 | -0.061 (-0.066|-0.057) p0.003** ys1.00 | -0.019 (-0.018|-0.025) p0.056* ys0.93 | -0.014 (-0.016|-0.010) p1.000 ys0.64 | +0.006 (+0.013|-0.012) p1.000 ys0.64 | - |
| nypm | -0.213 (-0.208|-0.222) p0.003** ys1.00 | -0.098 (-0.100|-0.102) p0.003** ys1.00 | -0.055 (-0.062|-0.040) p0.003** ys1.00 | -0.035 (-0.036|-0.037) p0.013** ys0.86 | -0.023 (-0.027|-0.036) p1.000 ys0.71 | - |
| close | -0.260 (-0.256|-0.263) p0.003** ys1.00 | -0.135 (-0.133|-0.148) p0.003** ys1.00 | -0.063 (-0.059|-0.084) p0.003** ys1.00 | -0.014 (-0.014|-0.012) p1.000 ys0.79 | - | - |

Hour cells (h >= 5) beating the family null, top 14 by |z| (hour = ET hour of the decision bar):
| h | session | hour ET | corr | z | p_family | year sign share | pre-2023 | 2023+ |
|--|--|--|--|--|--|--|--|--|
| 5 | asia | 23 | -0.199 | -58.7 | 0.003 | 1.00 | -0.200 | -0.220 |
| 5 | asia | 00 | -0.194 | -50.2 | 0.003 | 1.00 | -0.192 | -0.226 |
| 5 | asia | 22 | -0.168 | -47.5 | 0.003 | 1.00 | -0.170 | -0.205 |
| 5 | asia | 01 | -0.167 | -45.4 | 0.003 | 1.00 | -0.171 | -0.173 |
| 5 | asia | 18 | -0.135 | -41.3 | 0.003 | 1.00 | -0.130 | -0.162 |
| 5 | london | 06 | -0.131 | -40.3 | 0.003 | 1.00 | -0.130 | -0.147 |
| 5 | close | 15 | -0.135 | -39.5 | 0.003 | 1.00 | -0.135 | -0.146 |
| 5 | london | 05 | -0.131 | -37.1 | 0.003 | 1.00 | -0.131 | -0.149 |
| 5 | close | 16 | -0.135 | -34.1 | 0.003 | 1.00 | -0.130 | -0.151 |
| 5 | asia | 19 | -0.127 | -34.1 | 0.003 | 1.00 | -0.131 | -0.138 |
| 5 | asia | 21 | -0.120 | -33.8 | 0.003 | 1.00 | -0.116 | -0.157 |
| 5 | asia | 20 | -0.114 | -32.1 | 0.003 | 1.00 | -0.122 | -0.112 |
| 5 | nypm | 12 | -0.114 | -29.6 | 0.003 | 1.00 | -0.118 | -0.110 |
| 5 | london | 04 | -0.109 | -28.3 | 0.003 | 1.00 | -0.105 | -0.131 |

### 2. Variance ratio VR(q) and Hurst (1.0 = random walk; <1 reverting; edge-bias corrected), cell = value (null) p_family
| session | VR5 | VR15 | VR30 | VR60 | VR120 | Hurst |
|--|--|--|--|--|--|--|
| asia | 0.587 (0.999) p0.016** | 0.465 (0.999) p0.016** | 0.428 (0.999) p0.016** | 0.414 (0.999) p0.016** | 0.410 (0.999) p0.016** | 0.444 (0.500) p0.016** |
| london | 0.633 (0.998) p0.016** | 0.542 (0.997) p0.016** | 0.508 (0.997) p0.016** | 0.483 (0.997) p0.016** | 0.461 (0.998) p0.016** | 0.451 (0.500) p0.016** |
| pre | 0.794 (0.999) p0.016** | 0.724 (0.999) p0.016** | - | - | - | 0.458 (0.500) p0.016** |
| nyam | 0.735 (1.000) p0.016** | 0.675 (1.001) p0.016** | 0.660 (1.001) p0.016** | - | - | 0.469 (0.500) p0.016** |
| nypm | 0.637 (0.999) p0.016** | 0.551 (0.999) p0.016** | 0.519 (0.999) p0.016** | 0.504 (0.998) p0.016** | - | 0.452 (0.500) p0.016** |
| close | 0.556 (0.998) p0.016** | 0.452 (0.998) p0.016** | 0.423 (0.998) p0.016** | - | - | 0.422 (0.500) p0.016** |
| rth | 0.675 (0.999) p0.016** | 0.598 (1.000) p0.016** | 0.573 (1.000) p0.016** | 0.551 (1.000) p0.016** | 0.537 (0.998) p0.016** | 0.464 (0.500) p0.016** |

### 3. Day types (ex-post labels of the RTH day)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| day|trend | 0.446 | 3298 | 0.458 | -1.2 | 1.000 | 0.71 | 0.447 | 0.445 | stable |
| day|range | 0.260 | 3298 | 0.259 | +0.1 | 1.000 | 0.50 | 0.260 | 0.261 | unstable |
| day|er | 0.454 | 3298 | 0.461 | -1.3 | 1.000 | 0.93 | 0.454 | 0.455 | stable |
| day|ib_none | 0.055 | 3298 | 0.009 | +26.7 | 0.016** | 1.00 | 0.049 | 0.068 | stable |
| day|ib_one | 0.722 | 3298 | 0.623 | +11.6 | 0.016** | 1.00 | 0.717 | 0.734 | stable |
| day|ib_both | 0.223 | 3298 | 0.367 | -17.2 | 0.016** | 1.00 | 0.234 | 0.198 | stable |
| day|ib_one_closebeyond | 0.614 | 2381 | 0.707 | -9.9 | 0.016** | 1.00 | 0.618 | 0.603 | stable |

### 4. 1A -> 2A continuation vs give-back-half from the session open (A = 3 x ATR14(5m)); value = P(continue | resolved)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| cont|asia | 0.329 | 2095 | 0.356 | -2.7 | 0.393 | 0.64 | 0.324 | 0.344 | stable |
| cont|london | 0.307 | 3285 | 0.347 | -4.6 | 0.016** | 0.93 | 0.307 | 0.304 | stable |
| cont|pre | 0.381 | 1312 | 0.332 | +4.3 | 0.016** | 0.86 | 0.365 | 0.398 | stable |
| cont|nyam | 0.293 | 1644 | 0.292 | +0.0 | 1.000 | 0.57 | 0.294 | 0.286 | unstable |
| cont|nypm | 0.281 | 1045 | 0.282 | -0.1 | 1.000 | 0.50 | 0.296 | 0.239 | REGIME(2023+ only) |
| cont|close | 0.249 | 394 | 0.210 | +2.6 | 0.508 | 0.64 | 0.240 | 0.257 | stable |
| cont|rth | 0.315 | 2510 | 0.327 | -1.4 | 1.000 | 0.57 | 0.318 | 0.306 | unstable |

### 5. Gap fill by size bucket (b0 .05-.10, b1 .10-.25, b2 .25-.50, b3 >.50 of the 20-day mean RTH range); day = filled during RTH, h1 = within 60 min
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| gap|b0|day | 0.911 | 158 | 0.905 | +0.3 | 1.000 | 0.71 | 0.903 | 0.946 | REGIME(2023+ only) |
| gap|b0|h1 | 0.854 | 158 | 0.805 | +1.7 | 1.000 | 0.79 | 0.838 | 0.915 | stable |
| gap|b1|day | 0.758 | 516 | 0.777 | -1.1 | 1.000 | 0.64 | 0.733 | 0.816 | stable |
| gap|b1|h1 | 0.605 | 516 | 0.560 | +1.9 | 0.984 | 0.79 | 0.581 | 0.672 | stable |
| gap|b2|day | 0.521 | 827 | 0.553 | -1.6 | 1.000 | 0.71 | 0.513 | 0.536 | stable |
| gap|b2|h1 | 0.296 | 827 | 0.231 | +4.2 | 0.016** | 0.93 | 0.269 | 0.370 | stable |
| gap|b3|day | 0.203 | 1627 | 0.182 | +2.3 | 0.738 | 0.79 | 0.206 | 0.203 | stable |
| gap|b3|h1 | 0.041 | 1627 | 0.022 | +5.5 | 0.016** | 0.93 | 0.037 | 0.049 | stable |

### 6. Level reaction: first touch -> bounce (0.5A reverse) vs break-through (0.5A beyond) within 60 min; value = P(bounce)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| rx|PD|asia | 0.640 | 1652 | 0.463 | +15.0 | 0.016** | 1.00 | 0.644 | 0.627 | stable |
| rx|PD|london | 0.619 | 2332 | 0.491 | +14.0 | 0.016** | 1.00 | 0.637 | 0.570 | stable |
| rx|PD|pre | 0.512 | 1442 | 0.486 | +1.9 | 0.984 | 0.71 | 0.509 | 0.517 | stable |
| rx|PD|nyam | 0.554 | 1510 | 0.501 | +5.0 | 0.016** | 0.86 | 0.553 | 0.553 | stable |
| rx|PD|nypm | 0.589 | 1017 | 0.502 | +5.9 | 0.016** | 1.00 | 0.601 | 0.555 | stable |
| rx|PD|close | 0.638 | 426 | 0.498 | +7.7 | 0.016** | 0.93 | 0.627 | 0.658 | stable |
| rx|ON|nyam | 0.538 | 2092 | 0.505 | +2.9 | 0.197 | 0.79 | 0.532 | 0.552 | stable |
| rx|ON|nypm | 0.560 | 1248 | 0.504 | +4.2 | 0.016** | 0.86 | 0.564 | 0.548 | stable |
| rx|ON|close | 0.595 | 607 | 0.503 | +4.7 | 0.016** | 0.93 | 0.598 | 0.574 | stable |
| rx|IB|nyam | 0.575 | 2506 | 0.505 | +7.7 | 0.016** | 1.00 | 0.574 | 0.577 | stable |
| rx|IB|nypm | 0.600 | 2082 | 0.504 | +9.5 | 0.016** | 1.00 | 0.605 | 0.587 | stable |
| rx|IB|close | 0.625 | 907 | 0.505 | +9.8 | 0.016** | 1.00 | 0.627 | 0.623 | stable |
| rx|VW1|nyam | 0.495 | 4586 | 0.493 | +0.3 | 1.000 | 0.50 | 0.493 | 0.498 | REGIME(2023+ only) |
| rx|VW1|nypm | 0.519 | 2982 | 0.505 | +1.8 | 1.000 | 0.71 | 0.515 | 0.529 | stable |
| rx|VW1|close | 0.501 | 1664 | 0.502 | -0.1 | 1.000 | 0.50 | 0.509 | 0.485 | REGIME(2023+ only) |
| rx|VW2|nyam | 0.544 | 3513 | 0.507 | +5.1 | 0.016** | 0.86 | 0.550 | 0.526 | stable |
| rx|VW2|nypm | 0.534 | 2019 | 0.509 | +2.9 | 0.246 | 0.64 | 0.540 | 0.525 | stable |
| rx|VW2|close | 0.555 | 787 | 0.509 | +3.5 | 0.016** | 0.79 | 0.554 | 0.568 | stable |
| rx|RN|asia | 0.485 | 20773 | 0.487 | -0.4 | 1.000 | 0.50 | 0.480 | 0.495 | unstable |
| rx|RN|london | 0.497 | 34594 | 0.500 | -1.0 | 1.000 | 0.64 | 0.496 | 0.503 | stable |
| rx|RN|pre | 0.501 | 9709 | 0.497 | +0.8 | 1.000 | 0.57 | 0.497 | 0.511 | unstable |
| rx|RN|nyam | 0.497 | 17993 | 0.505 | -2.0 | 0.984 | 0.64 | 0.497 | 0.495 | stable |
| rx|RN|nypm | 0.500 | 16795 | 0.507 | -1.8 | 1.000 | 0.57 | 0.501 | 0.499 | unstable |
| rx|RN|close | 0.512 | 6486 | 0.508 | +0.7 | 1.000 | 0.43 | 0.516 | 0.514 | unstable |

### 7. Failed break (close .25A beyond, back inside within 10 bars): fade follow-through P(0.5A back before 0.5A out)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| fb|PD|asia | 0.354 | 752 | 0.499 | -10.5 | 0.016** | 1.00 | 0.359 | 0.319 | stable |
| fb|PD|london | 0.395 | 1404 | 0.500 | -10.4 | 0.016** | 1.00 | 0.407 | 0.361 | stable |
| fb|PD|pre | 0.490 | 731 | 0.501 | -0.6 | 1.000 | 0.71 | 0.456 | 0.544 | stable |
| fb|PD|nyam | 0.453 | 749 | 0.500 | -2.9 | 0.197 | 0.57 | 0.450 | 0.464 | unstable |
| fb|PD|nypm | 0.431 | 534 | 0.499 | -3.4 | 0.016** | 0.86 | 0.414 | 0.461 | stable |
| fb|PD|close | 0.373 | 169 | 0.498 | -5.1 | 0.016** | 0.71 | 0.375 | 0.276 | stable |
| fb|ON|nyam | 0.431 | 615 | 0.500 | -4.0 | 0.016** | 0.86 | 0.409 | 0.447 | stable |
| fb|ON|nypm | 0.387 | 576 | 0.498 | -6.6 | 0.016** | 0.93 | 0.385 | 0.384 | stable |
| fb|ON|close | 0.338 | 216 | 0.498 | -5.8 | 0.016** | 1.00 | 0.346 | 0.278 | stable |
| fb|IB|nyam | 0.442 | 462 | 0.502 | -3.5 | 0.016** | 0.71 | 0.429 | 0.496 | stable |
| fb|IB|nypm | 0.407 | 934 | 0.501 | -6.8 | 0.016** | 0.93 | 0.396 | 0.433 | stable |
| fb|IB|close | 0.377 | 337 | 0.501 | -5.7 | 0.016** | 1.00 | 0.344 | 0.418 | stable |

### 8. Where the range forms
RTH range increments by bin: 9:30 36.0%, 10:00 27.6%, 11:00 12.1%, 12:00 6.8%, 13:00 7.3%, 14:00 6.5%, 15:00 3.8%
Label-day range increments by ET hour (percent of the day): 00h 1.5, 01h 2.0, 02h 4.9, 03h 6.4, 04h 4.1, 05h 2.9, 06h 2.4, 07h 3.6, 08h 13.4, 09h 7.2, 10h 6.7, 11h 3.5, 12h 2.4, 13h 2.8, 14h 3.0, 15h 1.6, 16h 1.2, 18h 9.9, 19h 5.5, 20h 6.6, 21h 4.1, 22h 2.4, 23h 1.8

### 9. Room and liquidity (all years, raw-frame $, 1 lot)
| session | ATR14(5m) $ | A=3xATR5 $ | RT cost $ | room(1 ATR5) | room(A) | median 5-min vol | 1.7% cap (contracts/5min) | lots for $1,200 at 3xATR5 stop |
|--|--|--|--|--|--|--|--|--|
| asia | 21 | 63 | 52 | 0.41 | 1.22 | 516 | 8.8 | 19.0 |
| london | 29 | 87 | 52 | 0.56 | 1.68 | 2789 | 47.4 | 13.8 |
| pre | 44 | 132 | 52 | 0.85 | 2.55 | 11030 | 187.5 | 9.1 |
| nyam | 48 | 145 | 52 | 0.94 | 2.81 | 10492 | 178.4 | 8.3 |
| nypm | 39 | 117 | 52 | 0.76 | 2.27 | 5792 | 98.5 | 10.2 |
| close | 34 | 101 | 52 | 0.65 | 1.95 | 3615 | 61.5 | 11.9 |

room(A) by year: asia: 2013:1.2 2014:1.0 2015:1.1 2016:1.3 2017:1.1 2018:1.0 2019:1.2 2020:1.2 2021:1.2 2022:1.9 2023:1.5 2024:1.3 2025:1.2 2026:1.2; london: 2013:1.7 2014:1.6 2015:1.9 2016:1.8 2017:1.5 2018:1.4 2019:1.6 2020:1.6 2021:1.7 2022:2.5 2023:2.0 2024:1.7 2025:1.6 2026:1.5; pre: 2013:2.6 2014:2.5 2015:3.1 2016:2.5 2017:2.1 2018:2.0 2019:2.3 2020:2.1 2021:2.4 2022:3.9 2023:3.4 2024:2.7 2025:2.5 2026:2.4; nyam: 2013:2.8 2014:2.7 2015:3.2 2016:2.8 2017:2.4 2018:2.2 2019:2.5 2020:2.4 2021:2.7 2022:4.4 2023:3.8 2024:3.0 2025:2.8 2026:2.7; nypm: 2013:2.4 2014:2.2 2015:2.6 2016:2.3 2017:2.0 2018:1.9 2019:2.1 2020:2.0 2021:2.1 2022:3.2 2023:2.8 2024:2.3 2025:2.3 2026:2.2; close: 2013:2.0 2014:1.8 2015:2.2 2016:2.0 2017:1.7 2018:1.6 2019:1.8 2020:1.8 2021:1.8 2022:2.8 2023:2.3 2024:1.9 2025:1.9 2026:1.8

### 10. Versus NQ
Contemporaneous correlation of h-min returns (normalised): asia: 1m -0.13 5m -0.23 15m -0.28 30m -0.29 60m -0.31; london: 1m -0.10 5m -0.15 15m -0.16 30m -0.18 60m -0.21; pre: 1m 0.04 5m 0.06 15m 0.07; nyam: 1m -0.15 5m -0.18 15m -0.19 30m -0.19; nypm: 1m -0.10 5m -0.12 15m -0.10 30m -0.09; close: 1m -0.10 5m -0.15 15m -0.16

Lead/lag (1-15 min, family 180 cells; corr of 1-min normalised returns): cells beating the family null (top 10 by |z|; "NQ->X" = NQ leads ZN):
| direction | session | lag min | corr | z | p_family | year sign share |
|--|--|--|--|--|--|--|
| NQ->ZN | asia | 1 | -0.0379 | -43.1 | 0.010 | 0.86 |
| NQ->ZN | london | 1 | -0.0172 | -18.9 | 0.010 | 0.79 |
| NQ->ZN | nyam | 1 | -0.0165 | -10.3 | 0.010 | 0.93 |
| ZN->NQ | pre | 1 | +0.0229 | +8.4 | 0.010 | 0.93 |
| NQ->ZN | nypm | 1 | -0.0103 | -8.0 | 0.010 | 0.79 |
| NQ->ZN | asia | 2 | -0.0061 | -7.4 | 0.010 | 0.71 |
| NQ->ZN | asia | 3 | -0.0050 | -6.3 | 0.010 | 0.86 |
| NQ->ZN | close | 1 | -0.0096 | -5.3 | 0.010 | 0.79 |
| ZN->NQ | nypm | 1 | +0.0057 | +4.8 | 0.010 | 0.71 |
| ZN->NQ | nypm | 4 | +0.0053 | +4.7 | 0.010 | 0.71 |

### 11. Map rows that become book candidates under the FROZEN rule (p_family <= .05 AND room_A(session) > 2.0)
| map row | direction | stat | p_family | room_A | year sign share | stability | 1.7% cap >= 1 contract/5min in session |
|--|--|--|--|--|--|--|--|
| AC|pre|5m | reversion | -0.060 | 0.003 | 2.6 | 1.00 |  | yes |
| AC|nyam|5m | reversion | -0.061 | 0.003 | 2.8 | 1.00 |  | yes |
| AC|nypm|5m | reversion | -0.098 | 0.003 | 2.3 | 1.00 |  | yes |
| AC|nypm|15m | reversion | -0.055 | 0.003 | 2.3 | 1.00 |  | yes |
| AC|nypm|30m | reversion | -0.035 | 0.013 | 2.3 | 0.86 |  | yes |
| rx|PD|nyam | level-bounce | +0.554 | 0.016 | 2.8 | 0.86 | stable | yes |
| rx|PD|nypm | level-bounce | +0.589 | 0.016 | 2.3 | 1.00 | stable | yes |
| fb|PD|nypm | level-break | +0.431 | 0.016 | 2.3 | 0.86 | stable | yes |
| fb|ON|nyam | level-break | +0.431 | 0.016 | 2.8 | 0.86 | stable | yes |
| rx|ON|nypm | level-bounce | +0.560 | 0.016 | 2.3 | 0.86 | stable | yes |
| fb|ON|nypm | level-break | +0.387 | 0.016 | 2.3 | 0.93 | stable | yes |
| rx|IB|nyam | level-bounce | +0.575 | 0.016 | 2.8 | 1.00 | stable | yes |
| fb|IB|nyam | level-break | +0.442 | 0.016 | 2.8 | 0.71 | stable | yes |
| rx|IB|nypm | level-bounce | +0.600 | 0.016 | 2.3 | 1.00 | stable | yes |
| fb|IB|nypm | level-break | +0.407 | 0.016 | 2.3 | 0.93 | stable | yes |
| rx|VW2|nyam | level-bounce | +0.544 | 0.016 | 2.8 | 0.86 | stable | yes |
| gap|b2|h1 | level-bounce | +0.296 | 0.016 | 2.8 | 0.93 | stable | yes |
| gap|b3|h1 | level-bounce | +0.041 | 0.016 | 2.8 | 0.93 | stable | yes |
| vr|pre|5 | reversion | +0.794 | 0.016 | 2.6 | 1.00 | stable | yes |
| vr|pre|15 | reversion | +0.724 | 0.016 | 2.6 | 1.00 | stable | yes |
| hurst|pre | reversion | +0.458 | 0.016 | 2.6 | 1.00 | stable | yes |
| vr|nyam|5 | reversion | +0.735 | 0.016 | 2.8 | 1.00 | stable | yes |
| vr|nyam|15 | reversion | +0.675 | 0.016 | 2.8 | 1.00 | stable | yes |
| vr|nyam|30 | reversion | +0.660 | 0.016 | 2.8 | 1.00 | stable | yes |
| hurst|nyam | reversion | +0.469 | 0.016 | 2.8 | 1.00 | stable | yes |
| vr|nypm|5 | reversion | +0.637 | 0.016 | 2.3 | 1.00 | stable | yes |
| vr|nypm|15 | reversion | +0.551 | 0.016 | 2.3 | 1.00 | stable | yes |
| vr|nypm|30 | reversion | +0.519 | 0.016 | 2.3 | 1.00 | stable | yes |
| vr|nypm|60 | reversion | +0.504 | 0.016 | 2.3 | 1.00 | stable | yes |
| hurst|nypm | reversion | +0.452 | 0.016 | 2.3 | 1.00 | stable | yes |
| vr|rth|5 | reversion | +0.675 | 0.016 | 2.8 | 1.00 | stable | yes |
| vr|rth|15 | reversion | +0.598 | 0.016 | 2.8 | 1.00 | stable | yes |
| vr|rth|30 | reversion | +0.573 | 0.016 | 2.8 | 1.00 | stable | yes |
| vr|rth|60 | reversion | +0.551 | 0.016 | 2.8 | 1.00 | stable | yes |
| vr|rth|120 | reversion | +0.537 | 0.016 | 2.8 | 1.00 | stable | yes |
| hurst|rth | reversion | +0.464 | 0.016 | 2.8 | 1.00 | stable | yes |

CHAR-B note (ZN): library and frozen rule unchanged from CHAR-A (prereg sha 980bedf6..), CHAR-B scope sha e649ef5d.. in DECISIONS. Added constants: round-number grid GC 10 pts / CL 1.00 / ZN 0.5 / ZB 1.0 (my assumption), cost = PROXY-STD fee $4.84 RT + 1 tick in + 2 ticks stop out (FEES.md has no ZN entry; no fee edge claimed). The 1-minute negative autocorrelation is partly last-print/bid-ask noise: the books (evaluator) pay the measured-proxy cost to find out whether the 5-60 min reversion survives it. Data end 2026-10-16 (no 10-17..30 bars for these four).

## ZB - character map (CHAR-B via CHAR-A char_lib, 2026-11-05T23:26Z)
Base: ZB CME front-month (.v.0) 1-min bars from 2013-01 to 2026-10, percent frame (multiplicative roll-adjusted), 1-min approximation (no tick path), 3215 usable label days; ET clock, sessions asia 18:00-02:00 / london 02:00-08:30 / pre 08:30-09:30 / nyam 09:30-12:00 / nypm 12:00-15:00 / close 15:00-16:55. Nulls: within-year shuffled-day (AC B=300; structure B=100 worlds; levels recomputed on the shuffled path; round numbers 60 random grid phases); p_family = Westfall-Young max-|z| over the block (AC family 153 cells, structure family 92 cells). `**` p_family<=.05, `*` <=.10. Prereg sha256 980bedf6bad3f1669de9efb93831fa4622d88577c892d9359b7f57ba93c9dbcf. Descriptive only: no PASS, nothing live.

### Plain paragraph
At 1 minute every session has negative autocorrelation (-0.201 to -0.076; bid-ask bounce / last-print noise, not a tradable edge by itself). asia: reverts at 5/15/30/60 min (-0.111, -0.053, -0.022, -0.023). london: reverts at 5/15/30/120 min (-0.064, -0.036, -0.028, -0.046). pre: reverts at 5 min (-0.026). nyam: reverts at 5 min (-0.039). nypm: reverts at 5/15/30 min (-0.078, -0.047, -0.035). close: reverts at 5/15 min (-0.104, -0.056). Day types (RTH): 46% trend days (efficiency ratio >= .5; shuffled null 46%, p_fam 1.000), 25% range days (<.25; null 26%, p_fam 1.000); the IB (09:30-10:30) is extended on one side only on 72% of days and on both on 24%, and a one-sided extension closes beyond the IB edge 63% of the time (null 70%). RTH variance ratio at 30 min 0.671 (shuffled null 0.999, p_fam 0.016); Hurst 0.473. The RTH range forms 9:30 (36%), 10:00 (27%), 11:00 (12%) of the range increments. Level reactions that beat the family null: PD|asia bounces 60% of touches (more than the shuffled null 43%); PD|london bounces 58% of touches (more than the shuffled null 46%); PD|nypm bounces 57% of touches (more than the shuffled null 49%); PD|close bounces 59% of touches (more than the shuffled null 49%); ON|nypm bounces 54% of touches (more than the shuffled null 49%); ON|close bounces 59% of touches (more than the shuffled null 49%); IB|nyam bounces 55% of touches (more than the shuffled null 49%); IB|nypm bounces 56% of touches (more than the shuffled null 49%); IB|close bounces 59% of touches (more than the shuffled null 49%). Failed-break follow-through beating the null: PD|asia 39% (null 50%); PD|london 42% (null 50%); PD|close 39% (null 50%); ON|nypm 43% (null 50%); ON|close 39% (null 50%); IB|nypm 43% (null 50%); IB|close 42% (null 50%). Room (median 3xATR14(5m) $ / round-trip cost $99 per lot): asia 1.2x, london 1.7x, pre 2.9x, nyam 3.2x, nypm 2.6x, close 2.2x (1xATR5 room 1.1x in nyam, 0.4x in asia).

### 1. Autocorrelation of h-min returns (corr(past h, next h), both inside the session), pooled; cell = corr (pre-2023 mean | 2023+ mean) p_family
| session | 1 min | 5 min | 15 min | 30 min | 60 min | 120 min |
|--|--|--|--|--|--|--|
| asia | -0.141 (-0.130|-0.172) p0.003** ys1.00 | -0.111 (-0.108|-0.142) p0.003** ys1.00 | -0.053 (-0.058|-0.069) p0.003** ys0.93 | -0.022 (-0.033|-0.023) p0.003** ys0.79 | -0.023 (-0.033|-0.022) p0.017** ys0.86 | -0.013 (-0.028|-0.027) p1.000 ys0.79 |
| london | -0.133 (-0.122|-0.163) p0.003** ys1.00 | -0.064 (-0.060|-0.084) p0.003** ys1.00 | -0.036 (-0.037|-0.044) p0.003** ys0.93 | -0.028 (-0.031|-0.024) p0.003** ys0.86 | -0.023 (-0.028|-0.005) p0.063* ys0.71 | -0.046 (-0.054|-0.022) p0.020** ys0.79 |
| pre | -0.076 (-0.076|-0.085) p0.003** ys1.00 | -0.026 (-0.028|-0.024) p0.003** ys0.93 | -0.004 (-0.006|-0.018) p1.000 ys0.64 | -0.004 (+0.013|-0.062) p1.000 ys0.71 | - | - |
| nyam | -0.104 (-0.102|-0.114) p0.003** ys1.00 | -0.039 (-0.041|-0.042) p0.003** ys1.00 | -0.006 (-0.001|-0.025) p1.000 ys0.64 | +0.002 (+0.004|-0.005) p1.000 ys0.64 | +0.026 (+0.035|+0.011) p1.000 ys0.57 | - |
| nypm | -0.157 (-0.147|-0.183) p0.003** ys1.00 | -0.078 (-0.075|-0.093) p0.003** ys1.00 | -0.047 (-0.051|-0.038) p0.003** ys1.00 | -0.035 (-0.036|-0.042) p0.003** ys0.86 | -0.027 (-0.027|-0.037) p0.990 ys0.79 | - |
| close | -0.201 (-0.187|-0.236) p0.003** ys1.00 | -0.104 (-0.100|-0.125) p0.003** ys1.00 | -0.056 (-0.054|-0.067) p0.003** ys1.00 | -0.018 (-0.029|+0.007) p1.000 ys0.71 | - | - |

Hour cells (h >= 5) beating the family null, top 14 by |z| (hour = ET hour of the decision bar):
| h | session | hour ET | corr | z | p_family | year sign share | pre-2023 | 2023+ |
|--|--|--|--|--|--|--|--|--|
| 5 | asia | 00 | -0.143 | -37.5 | 0.003 | 0.93 | -0.129 | -0.208 |
| 5 | asia | 23 | -0.149 | -37.0 | 0.003 | 1.00 | -0.145 | -0.181 |
| 5 | asia | 18 | -0.129 | -31.8 | 0.003 | 1.00 | -0.122 | -0.170 |
| 5 | asia | 22 | -0.120 | -30.7 | 0.003 | 0.86 | -0.116 | -0.171 |
| 5 | asia | 01 | -0.116 | -29.8 | 0.003 | 0.93 | -0.122 | -0.129 |
| 5 | asia | 19 | -0.103 | -26.9 | 0.003 | 1.00 | -0.108 | -0.115 |
| 5 | close | 15 | -0.105 | -25.6 | 0.003 | 1.00 | -0.101 | -0.126 |
| 5 | close | 16 | -0.102 | -25.2 | 0.003 | 1.00 | -0.098 | -0.127 |
| 5 | london | 05 | -0.093 | -23.9 | 0.003 | 1.00 | -0.089 | -0.114 |
| 5 | london | 06 | -0.090 | -23.4 | 0.003 | 1.00 | -0.082 | -0.123 |
| 5 | asia | 21 | -0.087 | -21.3 | 0.003 | 0.93 | -0.080 | -0.135 |
| 5 | asia | 20 | -0.079 | -21.1 | 0.003 | 1.00 | -0.084 | -0.086 |
| 5 | nypm | 12 | -0.081 | -20.7 | 0.003 | 1.00 | -0.080 | -0.089 |
| 5 | nypm | 14 | -0.084 | -20.3 | 0.003 | 1.00 | -0.081 | -0.106 |

### 2. Variance ratio VR(q) and Hurst (1.0 = random walk; <1 reverting; edge-bias corrected), cell = value (null) p_family
| session | VR5 | VR15 | VR30 | VR60 | VR120 | Hurst |
|--|--|--|--|--|--|--|
| asia | 0.703 (0.999) p0.016** | 0.593 (0.999) p0.016** | 0.563 (0.999) p0.016** | 0.554 (0.999) p0.016** | 0.546 (1.000) p0.016** | 0.461 (0.500) p0.016** |
| london | 0.754 (0.999) p0.016** | 0.682 (0.999) p0.016** | 0.653 (0.999) p0.016** | 0.634 (0.999) p0.016** | 0.615 (1.000) p0.016** | 0.469 (0.500) p0.016** |
| pre | 0.862 (0.999) p0.016** | 0.829 (0.998) p0.016** | - | - | - | 0.482 (0.500) p0.016** |
| nyam | 0.817 (0.999) p0.016** | 0.775 (0.999) p0.016** | 0.769 (0.999) p0.016** | - | - | 0.482 (0.500) p0.016** |
| nypm | 0.716 (0.998) p0.016** | 0.639 (0.998) p0.016** | 0.608 (0.998) p0.016** | 0.589 (0.997) p0.016** | - | 0.460 (0.500) p0.016** |
| close | 0.642 (0.999) p0.016** | 0.549 (1.000) p0.016** | 0.521 (1.000) p0.016** | - | - | 0.440 (0.500) p0.016** |
| rth | 0.757 (0.999) p0.016** | 0.693 (0.999) p0.016** | 0.671 (0.999) p0.016** | 0.652 (0.998) p0.016** | 0.638 (0.997) p0.016** | 0.473 (0.500) p0.016** |

### 3. Day types (ex-post labels of the RTH day)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| day|trend | 0.460 | 3215 | 0.460 | +0.1 | 1.000 | 0.57 | 0.462 | 0.457 | unstable |
| day|range | 0.251 | 3215 | 0.256 | -0.7 | 1.000 | 0.64 | 0.253 | 0.249 | stable |
| day|er | 0.462 | 3215 | 0.464 | -0.4 | 1.000 | 0.57 | 0.464 | 0.456 | unstable |
| day|ib_none | 0.043 | 3215 | 0.010 | +20.1 | 0.016** | 1.00 | 0.036 | 0.059 | stable |
| day|ib_one | 0.717 | 3215 | 0.636 | +9.8 | 0.016** | 1.00 | 0.716 | 0.720 | stable |
| day|ib_both | 0.240 | 3215 | 0.354 | -13.8 | 0.016** | 1.00 | 0.248 | 0.221 | stable |
| day|ib_one_closebeyond | 0.633 | 2305 | 0.704 | -6.8 | 0.016** | 1.00 | 0.638 | 0.622 | stable |

### 4. 1A -> 2A continuation vs give-back-half from the session open (A = 3 x ATR14(5m)); value = P(continue | resolved)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| cont|asia | 0.344 | 2034 | 0.370 | -2.4 | 0.689 | 0.71 | 0.334 | 0.363 | stable |
| cont|london | 0.356 | 3214 | 0.406 | -5.7 | 0.016** | 0.93 | 0.366 | 0.326 | stable |
| cont|pre | 0.367 | 1596 | 0.342 | +2.2 | 0.820 | 0.64 | 0.350 | 0.403 | stable |
| cont|nyam | 0.309 | 1903 | 0.312 | -0.3 | 1.000 | 0.50 | 0.318 | 0.288 | REGIME(2023+ only) |
| cont|nypm | 0.288 | 1216 | 0.296 | -0.9 | 1.000 | 0.64 | 0.289 | 0.274 | stable |
| cont|close | 0.240 | 576 | 0.243 | -0.2 | 1.000 | 0.71 | 0.237 | 0.238 | stable |
| cont|rth | 0.328 | 2706 | 0.337 | -0.9 | 1.000 | 0.71 | 0.335 | 0.310 | stable |

### 5. Gap fill by size bucket (b0 .05-.10, b1 .10-.25, b2 .25-.50, b3 >.50 of the 20-day mean RTH range); day = filled during RTH, h1 = within 60 min
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| gap|b0|day | 0.868 | 159 | 0.899 | -1.5 | 1.000 | 0.57 | 0.827 | 0.956 | unstable |
| gap|b0|h1 | 0.786 | 159 | 0.797 | -0.4 | 1.000 | 0.57 | 0.747 | 0.880 | unstable |
| gap|b1|day | 0.748 | 484 | 0.776 | -1.6 | 1.000 | 0.79 | 0.728 | 0.808 | stable |
| gap|b1|h1 | 0.583 | 484 | 0.564 | +0.9 | 1.000 | 0.64 | 0.561 | 0.647 | REGIME(2023+ only) |
| gap|b2|day | 0.552 | 822 | 0.553 | -0.0 | 1.000 | 0.57 | 0.535 | 0.582 | unstable |
| gap|b2|h1 | 0.300 | 822 | 0.241 | +3.7 | 0.033** | 0.71 | 0.275 | 0.353 | stable |
| gap|b3|day | 0.223 | 1575 | 0.194 | +2.9 | 0.230 | 0.79 | 0.231 | 0.212 | stable |
| gap|b3|h1 | 0.047 | 1575 | 0.026 | +5.5 | 0.016** | 1.00 | 0.046 | 0.048 | stable |

### 6. Level reaction: first touch -> bounce (0.5A reverse) vs break-through (0.5A beyond) within 60 min; value = P(bounce)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| rx|PD|asia | 0.603 | 1506 | 0.430 | +13.1 | 0.016** | 1.00 | 0.608 | 0.593 | stable |
| rx|PD|london | 0.585 | 2280 | 0.459 | +12.5 | 0.016** | 1.00 | 0.588 | 0.585 | stable |
| rx|PD|pre | 0.526 | 1406 | 0.479 | +3.3 | 0.098* | 0.64 | 0.522 | 0.528 | stable |
| rx|PD|nyam | 0.531 | 1534 | 0.489 | +2.9 | 0.279 | 0.86 | 0.527 | 0.545 | stable |
| rx|PD|nypm | 0.573 | 1048 | 0.490 | +6.1 | 0.016** | 1.00 | 0.573 | 0.578 | stable |
| rx|PD|close | 0.591 | 482 | 0.487 | +5.2 | 0.016** | 0.79 | 0.593 | 0.585 | stable |
| rx|ON|nyam | 0.528 | 2203 | 0.492 | +3.5 | 0.066* | 0.86 | 0.525 | 0.538 | stable |
| rx|ON|nypm | 0.543 | 1333 | 0.491 | +4.0 | 0.016** | 0.93 | 0.541 | 0.545 | stable |
| rx|ON|close | 0.587 | 646 | 0.489 | +5.2 | 0.016** | 0.93 | 0.582 | 0.607 | stable |
| rx|IB|nyam | 0.546 | 2656 | 0.493 | +5.5 | 0.016** | 0.93 | 0.543 | 0.552 | stable |
| rx|IB|nypm | 0.560 | 2092 | 0.491 | +6.3 | 0.016** | 1.00 | 0.552 | 0.590 | stable |
| rx|IB|close | 0.591 | 1007 | 0.487 | +7.2 | 0.016** | 1.00 | 0.593 | 0.596 | stable |
| rx|VW1|nyam | 0.492 | 4652 | 0.485 | +1.0 | 1.000 | 0.50 | 0.492 | 0.491 | unstable |
| rx|VW1|nypm | 0.489 | 3077 | 0.490 | -0.1 | 1.000 | 0.43 | 0.493 | 0.481 | REGIME(2023+ only) |
| rx|VW1|close | 0.487 | 1854 | 0.489 | -0.2 | 1.000 | 0.43 | 0.485 | 0.498 | unstable |
| rx|VW2|nyam | 0.525 | 3559 | 0.499 | +3.4 | 0.082* | 0.86 | 0.524 | 0.530 | stable |
| rx|VW2|nypm | 0.519 | 2052 | 0.496 | +2.5 | 0.590 | 0.71 | 0.531 | 0.493 | stable |
| rx|VW2|close | 0.544 | 845 | 0.494 | +3.3 | 0.082* | 0.79 | 0.542 | 0.561 | stable |
| rx|RN|asia | 0.461 | 15708 | 0.463 | -0.8 | 1.000 | 0.57 | 0.455 | 0.472 | unstable |
| rx|RN|london | 0.473 | 30453 | 0.476 | -1.1 | 1.000 | 0.64 | 0.472 | 0.480 | stable |
| rx|RN|pre | 0.490 | 9456 | 0.485 | +1.3 | 1.000 | 0.43 | 0.493 | 0.486 | unstable |
| rx|RN|nyam | 0.493 | 18769 | 0.488 | +1.3 | 1.000 | 0.57 | 0.495 | 0.494 | unstable |
| rx|RN|nypm | 0.490 | 15957 | 0.493 | -0.7 | 1.000 | 0.57 | 0.492 | 0.487 | unstable |
| rx|RN|close | 0.495 | 6242 | 0.496 | -0.2 | 1.000 | 0.43 | 0.495 | 0.500 | unstable |

### 7. Failed break (close .25A beyond, back inside within 10 bars): fade follow-through P(0.5A back before 0.5A out)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| fb|PD|asia | 0.394 | 779 | 0.500 | -6.8 | 0.016** | 0.93 | 0.418 | 0.348 | stable |
| fb|PD|london | 0.415 | 1506 | 0.500 | -6.8 | 0.016** | 0.93 | 0.413 | 0.410 | stable |
| fb|PD|pre | 0.495 | 764 | 0.499 | -0.2 | 1.000 | 0.57 | 0.462 | 0.551 | unstable |
| fb|PD|nyam | 0.507 | 856 | 0.497 | +0.6 | 1.000 | 0.57 | 0.522 | 0.474 | unstable |
| fb|PD|nypm | 0.481 | 580 | 0.499 | -1.1 | 1.000 | 0.71 | 0.491 | 0.443 | stable |
| fb|PD|close | 0.392 | 212 | 0.503 | -4.6 | 0.016** | 0.93 | 0.405 | 0.331 | stable |
| fb|ON|nyam | 0.470 | 724 | 0.500 | -1.9 | 1.000 | 0.71 | 0.451 | 0.523 | stable |
| fb|ON|nypm | 0.425 | 691 | 0.501 | -4.9 | 0.016** | 0.93 | 0.427 | 0.427 | stable |
| fb|ON|close | 0.388 | 263 | 0.501 | -4.8 | 0.016** | 0.93 | 0.377 | 0.389 | stable |
| fb|IB|nyam | 0.465 | 594 | 0.500 | -2.2 | 0.869 | 0.64 | 0.456 | 0.470 | stable |
| fb|IB|nypm | 0.433 | 1063 | 0.500 | -5.9 | 0.016** | 0.86 | 0.429 | 0.435 | stable |
| fb|IB|close | 0.419 | 425 | 0.500 | -4.0 | 0.016** | 0.86 | 0.359 | 0.506 | stable |

### 8. Where the range forms
RTH range increments by bin: 9:30 36.1%, 10:00 27.1%, 11:00 12.4%, 12:00 6.9%, 13:00 7.4%, 14:00 6.0%, 15:00 3.9%
Label-day range increments by ET hour (percent of the day): 00h 1.5, 01h 1.9, 02h 4.9, 03h 6.7, 04h 4.4, 05h 3.0, 06h 2.5, 07h 3.9, 08h 13.0, 09h 7.8, 10h 6.8, 11h 4.1, 12h 2.5, 13h 3.0, 14h 2.7, 15h 1.7, 16h 1.2, 18h 8.7, 19h 5.1, 20h 6.4, 21h 4.0, 22h 2.4, 23h 1.8

### 9. Room and liquidity (all years, raw-frame $, 1 lot)
| session | ATR14(5m) $ | A=3xATR5 $ | RT cost $ | room(1 ATR5) | room(A) | median 5-min vol | 1.7% cap (contracts/5min) | lots for $1,200 at 3xATR5 stop |
|--|--|--|--|--|--|--|--|--|
| asia | 39 | 116 | 99 | 0.39 | 1.18 | 90 | 1.5 | 10.3 |
| london | 56 | 167 | 99 | 0.56 | 1.69 | 534 | 9.1 | 7.2 |
| pre | 94 | 283 | 99 | 0.96 | 2.87 | 2616 | 44.5 | 4.2 |
| nyam | 106 | 319 | 99 | 1.08 | 3.24 | 2536 | 43.1 | 3.8 |
| nypm | 84 | 252 | 99 | 0.85 | 2.55 | 1463 | 24.9 | 4.8 |
| close | 72 | 216 | 99 | 0.73 | 2.19 | 940 | 16.0 | 5.5 |

room(A) by year: asia: 2013:1.0 2014:0.8 2015:1.2 2016:1.4 2017:1.1 2018:1.0 2019:1.1 2020:1.5 2021:1.3 2022:1.7 2023:1.3 2024:1.1 2025:1.0 2026:1.1; london: 2013:1.5 2014:1.3 2015:2.2 2016:2.1 2017:1.5 2018:1.5 2019:1.6 2020:2.0 2021:1.9 2022:2.4 2023:1.9 2024:1.5 2025:1.5 2026:1.4; pre: 2013:2.6 2014:2.3 2015:3.9 2016:3.4 2017:2.6 2018:2.3 2019:2.5 2020:3.0 2021:3.0 2022:4.1 2023:3.4 2024:2.7 2025:2.5 2026:2.3; nyam: 2013:2.8 2014:2.5 2015:4.3 2016:4.0 2017:2.9 2018:2.6 2019:2.8 2020:3.4 2021:3.4 2022:4.8 2023:4.0 2024:3.1 2025:2.9 2026:2.5; nypm: 2013:2.4 2014:2.1 2015:3.5 2016:3.2 2017:2.4 2018:2.2 2019:2.2 2020:2.7 2021:2.5 2022:3.4 2023:2.8 2024:2.4 2025:2.2 2026:2.0; close: 2013:2.0 2014:1.8 2015:3.0 2016:2.8 2017:2.1 2018:1.9 2019:2.0 2020:2.4 2021:2.2 2022:3.0 2023:2.3 2024:2.0 2025:1.9 2026:1.8

### 10. Versus NQ
Contemporaneous correlation of h-min returns (normalised): asia: 1m -0.14 5m -0.23 15m -0.27 30m -0.28 60m -0.30; london: 1m -0.12 5m -0.15 15m -0.16 30m -0.17 60m -0.21; pre: 1m 0.03 5m 0.05 15m 0.06; nyam: 1m -0.16 5m -0.18 15m -0.18 30m -0.17; nypm: 1m -0.11 5m -0.13 15m -0.12 30m -0.11; close: 1m -0.11 5m -0.15 15m -0.16

Lead/lag (1-15 min, family 180 cells; corr of 1-min normalised returns): cells beating the family null (top 10 by |z|; "NQ->X" = NQ leads ZB):
| direction | session | lag min | corr | z | p_family | year sign share |
|--|--|--|--|--|--|--|
| NQ->ZB | asia | 1 | -0.0440 | -47.4 | 0.010 | 0.86 |
| NQ->ZB | london | 1 | -0.0195 | -20.4 | 0.010 | 0.71 |
| ZB->NQ | pre | 1 | +0.0242 | +11.5 | 0.010 | 0.93 |
| NQ->ZB | nyam | 1 | -0.0140 | -9.1 | 0.010 | 0.93 |
| NQ->ZB | asia | 2 | -0.0071 | -7.6 | 0.010 | 0.64 |
| NQ->ZB | asia | 3 | -0.0045 | -5.8 | 0.010 | 0.71 |
| ZB->NQ | nypm | 4 | +0.0069 | +5.3 | 0.010 | 0.86 |
| NQ->ZB | close | 1 | -0.0088 | -5.2 | 0.010 | 0.79 |
| NQ->ZB | nypm | 1 | -0.0067 | -5.1 | 0.010 | 0.64 |
| NQ->ZB | asia | 8 | -0.0036 | -4.7 | 0.010 | 0.79 |

### 11. Map rows that become book candidates under the FROZEN rule (p_family <= .05 AND room_A(session) > 2.0)
| map row | direction | stat | p_family | room_A | year sign share | stability | 1.7% cap >= 1 contract/5min in session |
|--|--|--|--|--|--|--|--|
| AC|pre|5m | reversion | -0.026 | 0.003 | 2.9 | 0.93 |  | yes |
| AC|nyam|5m | reversion | -0.039 | 0.003 | 3.2 | 1.00 |  | yes |
| AC|nypm|5m | reversion | -0.078 | 0.003 | 2.6 | 1.00 |  | yes |
| AC|close|5m | reversion | -0.104 | 0.003 | 2.2 | 1.00 |  | yes |
| AC|nypm|15m | reversion | -0.047 | 0.003 | 2.6 | 1.00 |  | yes |
| AC|close|15m | reversion | -0.056 | 0.003 | 2.2 | 1.00 |  | yes |
| AC|nypm|30m | reversion | -0.035 | 0.003 | 2.6 | 0.86 |  | yes |
| rx|PD|nypm | level-bounce | +0.573 | 0.016 | 2.6 | 1.00 | stable | yes |
| rx|PD|close | level-bounce | +0.591 | 0.016 | 2.2 | 0.79 | stable | yes |
| fb|PD|close | level-break | +0.392 | 0.016 | 2.2 | 0.93 | stable | yes |
| rx|ON|nypm | level-bounce | +0.543 | 0.016 | 2.6 | 0.93 | stable | yes |
| fb|ON|nypm | level-break | +0.425 | 0.016 | 2.6 | 0.93 | stable | yes |
| rx|ON|close | level-bounce | +0.587 | 0.016 | 2.2 | 0.93 | stable | yes |
| fb|ON|close | level-break | +0.388 | 0.016 | 2.2 | 0.93 | stable | yes |
| rx|IB|nyam | level-bounce | +0.546 | 0.016 | 3.2 | 0.93 | stable | yes |
| rx|IB|nypm | level-bounce | +0.560 | 0.016 | 2.6 | 1.00 | stable | yes |
| fb|IB|nypm | level-break | +0.433 | 0.016 | 2.6 | 0.86 | stable | yes |
| rx|IB|close | level-bounce | +0.591 | 0.016 | 2.2 | 1.00 | stable | yes |
| fb|IB|close | level-break | +0.419 | 0.016 | 2.2 | 0.86 | stable | yes |
| gap|b2|h1 | level-bounce | +0.300 | 0.033 | 3.2 | 0.71 | stable | yes |
| gap|b3|h1 | level-bounce | +0.047 | 0.016 | 3.2 | 1.00 | stable | yes |
| vr|pre|5 | reversion | +0.862 | 0.016 | 2.9 | 1.00 | stable | yes |
| vr|pre|15 | reversion | +0.829 | 0.016 | 2.9 | 1.00 | stable | yes |
| hurst|pre | reversion | +0.482 | 0.016 | 2.9 | 0.93 | stable | yes |
| vr|nyam|5 | reversion | +0.817 | 0.016 | 3.2 | 1.00 | stable | yes |
| vr|nyam|15 | reversion | +0.775 | 0.016 | 3.2 | 1.00 | stable | yes |
| vr|nyam|30 | reversion | +0.769 | 0.016 | 3.2 | 1.00 | stable | yes |
| hurst|nyam | reversion | +0.482 | 0.016 | 3.2 | 0.93 | stable | yes |
| vr|nypm|5 | reversion | +0.716 | 0.016 | 2.6 | 1.00 | stable | yes |
| vr|nypm|15 | reversion | +0.639 | 0.016 | 2.6 | 1.00 | stable | yes |
| vr|nypm|30 | reversion | +0.608 | 0.016 | 2.6 | 1.00 | stable | yes |
| vr|nypm|60 | reversion | +0.589 | 0.016 | 2.6 | 1.00 | stable | yes |
| hurst|nypm | reversion | +0.460 | 0.016 | 2.6 | 1.00 | stable | yes |
| vr|close|5 | reversion | +0.642 | 0.016 | 2.2 | 1.00 | stable | yes |
| vr|close|15 | reversion | +0.549 | 0.016 | 2.2 | 1.00 | stable | yes |
| vr|close|30 | reversion | +0.521 | 0.016 | 2.2 | 1.00 | stable | yes |
| hurst|close | reversion | +0.440 | 0.016 | 2.2 | 1.00 | stable | yes |
| vr|rth|5 | reversion | +0.757 | 0.016 | 3.2 | 1.00 | stable | yes |
| vr|rth|15 | reversion | +0.693 | 0.016 | 3.2 | 1.00 | stable | yes |
| vr|rth|30 | reversion | +0.671 | 0.016 | 3.2 | 1.00 | stable | yes |
| vr|rth|60 | reversion | +0.652 | 0.016 | 3.2 | 1.00 | stable | yes |
| vr|rth|120 | reversion | +0.638 | 0.016 | 3.2 | 1.00 | stable | yes |
| hurst|rth | reversion | +0.473 | 0.016 | 3.2 | 1.00 | stable | yes |

CHAR-B note (ZB): library and frozen rule unchanged from CHAR-A (prereg sha 980bedf6..), CHAR-B scope sha e649ef5d.. in DECISIONS. Added constants: round-number grid GC 10 pts / CL 1.00 / ZN 0.5 / ZB 1.0 (my assumption), cost = PROXY-STD fee $4.84 RT + 1 tick in + 2 ticks stop out (FEES.md has no ZB entry; no fee edge claimed). The 1-minute negative autocorrelation is partly last-print/bid-ask noise: the books (evaluator) pay the measured-proxy cost to find out whether the 5-60 min reversion survives it. Data end 2026-10-16 (no 10-17..30 bars for these four).


## 6E - character map (CHAR-C, 2026-11-05T23:31Z)
Base: 6E CME front-month (.v.0) 1-min bars from 2013-01 to 2026-10, percent frame (multiplicative roll-adjusted), 1-min approximation (no tick path), 3472 usable label days; ET clock, sessions asia 18:00-02:00 / london 02:00-08:30 / pre 08:30-09:30 / nyam 09:30-12:00 / nypm 12:00-15:00 / close 15:00-16:55. Nulls: within-year shuffled-day (AC B=300; structure B=100 worlds; levels recomputed on the shuffled path; round numbers 60 random grid phases); p_family = Westfall-Young max-|z| over the block (AC family 153 cells, structure family 92 cells). `**` p_family<=.05, `*` <=.10. Prereg sha256 980bedf6bad3f1669de9efb93831fa4622d88577c892d9359b7f57ba93c9dbcf. Descriptive only: no PASS, nothing live.

### Plain paragraph (CHAR-C)
6E (euro FX) is a mean-reverting range instrument from 1 to about 30 minutes in every session and a random walk beyond an hour. The correlation of the last 5-minute return with the next 5-minute return is negative in all six sessions (-0.026 pre to -0.096 close; p_family .003 against 300 within-year shuffled-day worlds over a 153-cell family; same sign in 11-14 of 14 years), strongest in the NY afternoon and the 15:00-16:55 close (-0.096 / -0.074 / -0.061 at 5 / 15 / 30 min), and gone at 60 and 120 minutes (|corr| <= 0.022, p_family 0.93-1.0). Variance ratios agree (VR(30) .53 close, .64 NY-PM, .84 NY-AM and London, .77 Asia; Hurst .43-.49) but most of the 1-5 minute part is last-trade bid-ask bounce on a one-tick spread, and what is left to harvest is small: fading a 1-sigma move earns $1.5-8.8 per signal at 5-30 minutes (best NY-PM 5 minutes $8.8 = 0.37 x the $24.0 round trip), so gross edge is 0.06-0.37 x cost in every session. Day type is a coin flip against the null (trend days 42% vs null 43%, range days 28% vs 28%), but the 09:30-10:30 range is extended on exactly one side on 68% of days (null 61%) and on both sides only 26% (null 37%), and a one-sided extension closes beyond the IB edge 61% of the time (null 68%): extensions fail. The day's range forms at the 08:00 ET US-data / ECB-fix hour (8.9% of range increments) and the 03:00 London open (8.8%), then 18:00 (7.8%), 20:00 (7.0%), 02:00 and 10:00 (6.6% each). Levels: prior-day high/low touched in Asia bounce 53% (null 46%, 13 of 14 years), but in the NY sessions prior-day and overnight highs/lows break through more than the null (overnight high/low NY-AM bounce 50% vs 56%); VWAP +-2 sigma touches bounce 56% / 60% (null 54%) in NY-AM / close in only 57-64% of years; and after a failed break of the prior-day, overnight or IB level in NY-PM / close the break RESUMES (fade works 34-44% vs 50% null) - breaks are sticky. Calendar drift: EUR sells 07:30-08:00 ET (-0.8 bp = -$11.4 per lot, t -5.5, p_family < .001, 13 of 14 years) and 06:30-07:00 (-0.5 bp, p_family < .001), worth 0.48 x and 0.29 x cost. Room: 3 x ATR14(5m) = 3.7x (Asia), 6.7x (London), 8.6x (pre), 9.8x (NY-AM), 7.1x (NY-PM), 5.0x (close) the $24.0 round trip (one ATR5 only 1.2-3.3x); the 1.7% cap is 2.1 (Asia) to 21.3 (NY-AM) contracts per 5 minutes, enough for the 5-14 lots a $1,200 stop needs from London to NY-PM, binding in Asia and the close. NQ correlation +0.07 to +0.18, no lead-lag above 0.01. The book that fits is a large-excursion (>= 2-3 ATR5 in 5-15 minutes) fade in London / pre / NY-AM / NY-PM, plus break-continuation after failed breaks in NY-PM / close; neither clears (DS3_FIND.md).

### Generated summary (page.py of CHAR-A, same numbers)
At 1 minute every session has negative autocorrelation (-0.184 to -0.043; bid-ask bounce / last-print noise, not a tradable edge by itself). asia: reverts at 5/15 min (-0.047, -0.027). london: reverts at 5/15/30 min (-0.029, -0.018, -0.022). pre: reverts at 5 min (-0.026). nyam: reverts at 5 min (-0.031). nypm: reverts at 5/15 min (-0.059, -0.030). close: reverts at 5/15/30 min (-0.096, -0.074, -0.061). Day types (RTH): 42% trend days (efficiency ratio >= .5; shuffled null 43%, p_fam 1.000), 28% range days (<.25; null 28%, p_fam 1.000); the IB (09:30-10:30) is extended on one side only on 68% of days and on both on 26%, and a one-sided extension closes beyond the IB edge 61% of the time (null 68%). RTH variance ratio at 30 min 0.734 (shuffled null 0.999, p_fam 0.016); Hurst 0.475. The RTH range forms 9:30 (35%), 10:00 (33%), 11:00 (12%) of the range increments. Level reactions that beat the family null: PD|asia bounces 53% of touches (more than the shuffled null 46%); ON|nyam bounces 50% of touches (less, i.e. breaks through more than the shuffled null 56%); VW2|nyam bounces 56% of touches (more than the shuffled null 54%); VW2|close bounces 60% of touches (more than the shuffled null 54%). Failed-break follow-through beating the null: PD|nypm 44% (null 50%); PD|close 34% (null 50%); ON|close 37% (null 50%); IB|nypm 44% (null 50%); IB|close 42% (null 50%). Room (median 3xATR14(5m) $ / round-trip cost $24 per lot): asia 3.7x, london 6.7x, pre 8.6x, nyam 9.8x, nypm 7.1x, close 5.0x (1xATR5 room 3.3x in nyam, 1.2x in asia).

### 1. Autocorrelation of h-min returns (corr(past h, next h), both inside the session), pooled; cell = corr (pre-2023 mean | 2023+ mean) p_family
| session | 1 min | 5 min | 15 min | 30 min | 60 min | 120 min |
|--|--|--|--|--|--|--|
| asia | -0.074 (-0.087|-0.044) p0.003** ys1.00 | -0.047 (-0.062|-0.025) p0.003** ys1.00 | -0.027 (-0.041|-0.006) p0.003** ys0.86 | -0.015 (-0.031|+0.006) p0.056* ys0.79 | +0.001 (-0.021|+0.008) p1.000 ys0.29 | +0.022 (-0.023|+0.027) p0.934 ys0.36 |
| london | -0.062 (-0.072|-0.018) p0.003** ys1.00 | -0.029 (-0.036|-0.016) p0.003** ys1.00 | -0.018 (-0.019|-0.019) p0.003** ys1.00 | -0.022 (-0.024|-0.020) p0.017** ys1.00 | -0.005 (-0.013|+0.015) p1.000 ys0.64 | -0.006 (-0.010|-0.003) p1.000 ys0.71 |
| pre | -0.043 (-0.049|-0.021) p0.003** ys1.00 | -0.026 (-0.023|-0.034) p0.003** ys0.86 | +0.002 (+0.012|-0.034) p1.000 ys0.50 | +0.003 (+0.011|-0.028) p1.000 ys0.43 | - | - |
| nyam | -0.061 (-0.070|-0.017) p0.003** ys1.00 | -0.031 (-0.038|-0.021) p0.003** ys1.00 | -0.015 (-0.018|-0.012) p0.312 ys0.86 | -0.016 (-0.017|-0.022) p0.990 ys0.79 | -0.005 (-0.005|-0.008) p1.000 ys0.50 | - |
| nypm | -0.149 (-0.117|-0.026) p0.003** ys1.00 | -0.059 (-0.072|-0.007) p0.003** ys0.79 | -0.030 (-0.037|-0.019) p0.003** ys0.71 | -0.007 (-0.004|-0.023) p1.000 ys0.57 | -0.014 (-0.012|-0.028) p1.000 ys0.71 | - |
| close | -0.184 (-0.141|-0.051) p0.003** ys1.00 | -0.096 (-0.106|-0.034) p0.003** ys1.00 | -0.074 (-0.082|-0.053) p0.003** ys1.00 | -0.061 (-0.054|-0.090) p0.003** ys0.93 | - | - |

Hour cells (h >= 5) beating the family null, top 14 by |z| (hour = ET hour of the decision bar):
| h | session | hour ET | corr | z | p_family | year sign share | pre-2023 | 2023+ |
|--|--|--|--|--|--|--|--|--|
| 5 | close | 16 | -0.129 | -31.4 | 0.003 | 1.00 | -0.132 | -0.055 |
| 5 | asia | 00 | -0.077 | -20.5 | 0.003 | 1.00 | -0.091 | -0.048 |
| 5 | close | 15 | -0.078 | -19.6 | 0.003 | 0.79 | -0.091 | -0.022 |
| 5 | nypm | 12 | -0.076 | -18.9 | 0.003 | 0.93 | -0.081 | -0.049 |
| 5 | asia | 18 | -0.069 | -16.8 | 0.003 | 0.93 | -0.088 | -0.024 |
| 5 | asia | 23 | -0.061 | -15.4 | 0.003 | 0.93 | -0.084 | -0.043 |
| 5 | nypm | 13 | -0.055 | -14.8 | 0.003 | 0.64 | -0.072 | +0.014 |
| 5 | nyam | 11 | -0.054 | -13.1 | 0.003 | 1.00 | -0.069 | -0.025 |
| 5 | london | 07 | -0.049 | -12.1 | 0.003 | 0.93 | -0.054 | -0.047 |
| 15 | close | 16 | -0.095 | -11.9 | 0.003 | 0.71 | -0.108 | -0.033 |
| 5 | asia | 19 | -0.041 | -10.9 | 0.003 | 0.71 | -0.068 | +0.017 |
| 5 | asia | 20 | -0.042 | -10.9 | 0.003 | 1.00 | -0.053 | -0.031 |
| 5 | nypm | 14 | -0.047 | -10.8 | 0.003 | 0.57 | -0.065 | +0.016 |
| 5 | asia | 01 | -0.042 | -10.4 | 0.003 | 0.79 | -0.054 | -0.030 |

### 2. Variance ratio VR(q) and Hurst (1.0 = random walk; <1 reverting; edge-bias corrected), cell = value (null) p_family
| session | VR5 | VR15 | VR30 | VR60 | VR120 | Hurst |
|--|--|--|--|--|--|--|
| asia | 0.853 (1.000) p0.016** | 0.794 (0.999) p0.016** | 0.773 (0.999) p0.016** | 0.765 (0.998) p0.016** | 0.771 (0.998) p0.016** | 0.484 (0.500) p0.016** |
| london | 0.891 (0.999) p0.016** | 0.854 (0.997) p0.016** | 0.841 (0.997) p0.016** | 0.826 (0.996) p0.016** | 0.824 (0.998) p0.016** | 0.487 (0.500) p0.016** |
| pre | 0.914 (0.999) p0.016** | 0.880 (0.996) p0.016** | - | - | - | 0.483 (0.499) p0.016** |
| nyam | 0.888 (0.998) p0.016** | 0.851 (0.998) p0.016** | 0.837 (0.999) p0.016** | - | - | 0.483 (0.500) p0.016** |
| nypm | 0.728 (0.999) p0.016** | 0.667 (0.999) p0.016** | 0.643 (0.999) p0.016** | 0.639 (0.999) p0.016** | - | 0.473 (0.500) p0.016** |
| close | 0.665 (0.999) p0.016** | 0.567 (0.998) p0.016** | 0.525 (0.998) p0.016** | - | - | 0.434 (0.500) p0.016** |
| rth | 0.808 (0.999) p0.016** | 0.756 (0.999) p0.016** | 0.734 (0.999) p0.016** | 0.713 (0.999) p0.016** | 0.687 (0.998) p0.016** | 0.475 (0.500) p0.016** |

### 3. Day types (ex-post labels of the RTH day)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| day|trend | 0.423 | 3472 | 0.431 | -0.9 | 1.000 | 0.43 | 0.416 | 0.435 | unstable |
| day|range | 0.282 | 3472 | 0.278 | +0.6 | 1.000 | 0.50 | 0.288 | 0.270 | unstable |
| day|er | 0.439 | 3472 | 0.446 | -1.5 | 1.000 | 0.43 | 0.434 | 0.451 | unstable |
| day|ib_none | 0.055 | 3472 | 0.016 | +18.5 | 0.016** | 1.00 | 0.055 | 0.056 | stable |
| day|ib_one | 0.683 | 3472 | 0.610 | +10.4 | 0.016** | 0.93 | 0.671 | 0.709 | stable |
| day|ib_both | 0.262 | 3472 | 0.374 | -16.5 | 0.016** | 1.00 | 0.274 | 0.235 | stable |
| day|ib_one_closebeyond | 0.606 | 2371 | 0.678 | -7.2 | 0.016** | 0.86 | 0.589 | 0.638 | stable |

### 4. 1A -> 2A continuation vs give-back-half from the session open (A = 3 x ATR14(5m)); value = P(continue | resolved)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| cont|asia | 0.346 | 3007 | 0.384 | -4.8 | 0.016** | 0.71 | 0.335 | 0.373 | stable |
| cont|london | 0.333 | 3462 | 0.356 | -2.9 | 0.148 | 0.71 | 0.327 | 0.346 | stable |
| cont|pre | 0.337 | 1415 | 0.311 | +2.9 | 0.098* | 0.71 | 0.324 | 0.375 | stable |
| cont|nyam | 0.283 | 2153 | 0.278 | +0.5 | 1.000 | 0.64 | 0.277 | 0.288 | REGIME(2023+ only) |
| cont|nypm | 0.254 | 952 | 0.271 | -1.7 | 1.000 | 0.57 | 0.255 | 0.288 | unstable |
| cont|close | 0.268 | 664 | 0.289 | -1.4 | 1.000 | 0.71 | 0.251 | 0.246 | stable |
| cont|rth | 0.298 | 2813 | 0.304 | -0.6 | 1.000 | 0.57 | 0.290 | 0.311 | unstable |

### 5. Gap fill by size bucket (b0 .05-.10, b1 .10-.25, b2 .25-.50, b3 >.50 of the 20-day mean RTH range); day = filled during RTH, h1 = within 60 min
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| gap|b0|day | 0.869 | 175 | 0.916 | -2.3 | 0.787 | 0.79 | 0.867 | 0.862 | stable |
| gap|b0|h1 | 0.760 | 175 | 0.796 | -1.1 | 1.000 | 0.57 | 0.746 | 0.776 | unstable |
| gap|b1|day | 0.731 | 536 | 0.793 | -4.0 | 0.016** | 0.79 | 0.727 | 0.747 | stable |
| gap|b1|h1 | 0.582 | 536 | 0.531 | +2.4 | 0.672 | 0.64 | 0.568 | 0.625 | stable |
| gap|b2|day | 0.502 | 805 | 0.558 | -3.2 | 0.016** | 0.71 | 0.512 | 0.466 | stable |
| gap|b2|h1 | 0.251 | 805 | 0.223 | +2.1 | 0.902 | 0.57 | 0.254 | 0.227 | unstable |
| gap|b3|day | 0.198 | 1767 | 0.177 | +2.3 | 0.689 | 0.50 | 0.220 | 0.160 | unstable |
| gap|b3|h1 | 0.044 | 1767 | 0.028 | +3.9 | 0.016** | 0.79 | 0.049 | 0.036 | stable |

### 6. Level reaction: first touch -> bounce (0.5A reverse) vs break-through (0.5A beyond) within 60 min; value = P(bounce)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| rx|PD|asia | 0.534 | 1965 | 0.464 | +6.9 | 0.016** | 0.93 | 0.535 | 0.526 | stable |
| rx|PD|london | 0.512 | 2884 | 0.507 | +0.5 | 1.000 | 0.57 | 0.521 | 0.495 | unstable |
| rx|PD|pre | 0.482 | 1284 | 0.505 | -1.9 | 0.951 | 0.64 | 0.486 | 0.484 | stable |
| rx|PD|nyam | 0.529 | 1594 | 0.530 | -0.1 | 1.000 | 0.57 | 0.543 | 0.505 | REGIME(2023+ only) |
| rx|PD|nypm | 0.536 | 911 | 0.553 | -1.1 | 1.000 | 0.79 | 0.543 | 0.507 | stable |
| rx|PD|close | 0.505 | 426 | 0.536 | -1.6 | 1.000 | 0.64 | 0.503 | 0.543 | stable |
| rx|ON|nyam | 0.502 | 2084 | 0.558 | -5.9 | 0.016** | 0.79 | 0.514 | 0.473 | stable |
| rx|ON|nypm | 0.535 | 1100 | 0.568 | -2.9 | 0.148 | 0.71 | 0.525 | 0.551 | stable |
| rx|ON|close | 0.574 | 479 | 0.541 | +1.8 | 1.000 | 0.64 | 0.593 | 0.517 | stable |
| rx|IB|nyam | 0.562 | 2987 | 0.547 | +2.0 | 0.918 | 0.29 | 0.571 | 0.541 | unstable |
| rx|IB|nypm | 0.541 | 1983 | 0.552 | -1.1 | 1.000 | 0.79 | 0.555 | 0.473 | REGIME(2023+ only) |
| rx|IB|close | 0.560 | 915 | 0.528 | +2.2 | 0.803 | 0.36 | 0.545 | 0.499 | unstable |
| rx|VW1|nyam | 0.505 | 5374 | 0.508 | -0.5 | 1.000 | 0.64 | 0.513 | 0.488 | REGIME(2023+ only) |
| rx|VW1|nypm | 0.525 | 3024 | 0.531 | -0.7 | 1.000 | 0.64 | 0.536 | 0.475 | REGIME(2023+ only) |
| rx|VW1|close | 0.552 | 1659 | 0.517 | +2.9 | 0.098* | 0.64 | 0.572 | 0.470 | stable |
| rx|VW2|nyam | 0.561 | 4280 | 0.538 | +3.2 | 0.016** | 0.64 | 0.566 | 0.548 | stable |
| rx|VW2|nypm | 0.563 | 1921 | 0.557 | +0.7 | 1.000 | 0.29 | 0.561 | 0.536 | unstable |
| rx|VW2|close | 0.599 | 773 | 0.536 | +4.8 | 0.016** | 0.57 | 0.613 | 0.441 | unstable |
| rx|RN|asia | 0.478 | 27746 | 0.479 | -0.5 | 1.000 | 0.64 | 0.480 | 0.473 | REGIME(2023+ only) |
| rx|RN|london | 0.495 | 50957 | 0.496 | -0.6 | 1.000 | 0.71 | 0.496 | 0.483 | REGIME(2023+ only) |
| rx|RN|pre | 0.494 | 12260 | 0.498 | -1.0 | 1.000 | 0.71 | 0.495 | 0.478 | stable |
| rx|RN|nyam | 0.495 | 24820 | 0.504 | -2.1 | 0.902 | 0.86 | 0.495 | 0.486 | stable |
| rx|RN|nypm | 0.503 | 16348 | 0.504 | -0.3 | 1.000 | 0.79 | 0.502 | 0.494 | stable |
| rx|RN|close | 0.503 | 5229 | 0.506 | -0.5 | 1.000 | 0.71 | 0.509 | 0.470 | REGIME(2023+ only) |

### 7. Failed break (close .25A beyond, back inside within 10 bars): fade follow-through P(0.5A back before 0.5A out)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| fb|PD|asia | 0.485 | 1141 | 0.501 | -1.3 | 1.000 | 0.71 | 0.484 | 0.468 | stable |
| fb|PD|london | 0.494 | 1945 | 0.500 | -0.6 | 1.000 | 0.57 | 0.496 | 0.494 | unstable |
| fb|PD|pre | 0.506 | 656 | 0.499 | +0.4 | 1.000 | 0.57 | 0.507 | 0.527 | unstable |
| fb|PD|nyam | 0.484 | 932 | 0.501 | -1.1 | 1.000 | 0.64 | 0.487 | 0.486 | stable |
| fb|PD|nypm | 0.436 | 532 | 0.500 | -3.2 | 0.016** | 0.71 | 0.431 | 0.432 | stable |
| fb|PD|close | 0.336 | 211 | 0.502 | -5.2 | 0.016** | 0.79 | 0.319 | 0.495 | stable |
| fb|ON|nyam | 0.501 | 796 | 0.500 | +0.1 | 1.000 | 0.43 | 0.514 | 0.483 | unstable |
| fb|ON|nypm | 0.464 | 547 | 0.503 | -2.3 | 0.787 | 0.64 | 0.436 | 0.512 | stable |
| fb|ON|close | 0.371 | 237 | 0.499 | -4.2 | 0.016** | 0.93 | 0.387 | 0.338 | stable |
| fb|IB|nyam | 0.493 | 702 | 0.503 | -0.6 | 1.000 | 0.64 | 0.498 | 0.461 | stable |
| fb|IB|nypm | 0.438 | 957 | 0.501 | -4.3 | 0.016** | 0.93 | 0.438 | 0.428 | stable |
| fb|IB|close | 0.421 | 399 | 0.502 | -3.3 | 0.016** | 0.71 | 0.380 | 0.541 | stable |

### 8. Where the range forms
RTH range increments by bin: 9:30 35.3%, 10:00 33.1%, 11:00 12.0%, 12:00 6.6%, 13:00 5.2%, 14:00 5.3%, 15:00 2.5%
Label-day range increments by ET hour (percent of the day): 00h 1.7, 01h 3.0, 02h 6.6, 03h 8.8, 04h 6.4, 05h 4.3, 06h 3.6, 07h 3.8, 08h 8.9, 09h 5.8, 10h 6.6, 11h 3.3, 12h 1.9, 13h 1.6, 14h 2.3, 15h 1.0, 16h 0.5, 18h 7.8, 19h 5.3, 20h 7.0, 21h 4.8, 22h 3.0, 23h 1.8

### 9. Room and liquidity (all years, raw-frame $, 1 lot)
| session | ATR14(5m) $ | A=3xATR5 $ | RT cost $ | room(1 ATR5) | room(A) | median 5-min vol | 1.7% cap (contracts/5min) | lots for $1,200 at 3xATR5 stop |
|--|--|--|--|--|--|--|--|--|
| asia | 29 | 88 | 24 | 1.23 | 3.68 | 121 | 2.1 | 13.6 |
| london | 54 | 161 | 24 | 2.23 | 6.70 | 634 | 10.8 | 7.5 |
| pre | 69 | 206 | 24 | 2.87 | 8.60 | 1153 | 19.6 | 5.8 |
| nyam | 79 | 236 | 24 | 3.28 | 9.83 | 1253 | 21.3 | 5.1 |
| nypm | 57 | 171 | 24 | 2.37 | 7.12 | 489 | 8.3 | 7.0 |
| close | 40 | 119 | 24 | 1.66 | 4.98 | 217 | 3.7 | 10.1 |

room(A) by year: asia: 2013:5.0 2014:3.5 2015:5.7 2016:4.2 2017:3.7 2018:4.0 2019:2.4 2020:3.8 2021:2.9 2022:4.9 2023:3.3 2024:2.5 2025:4.0 2026:3.0; london: 2013:9.2 2014:6.8 2015:11.3 2016:7.2 2017:6.6 2018:7.8 2019:4.7 2020:7.4 2021:5.6 2022:9.0 2023:6.3 2024:4.7 2025:6.3 2026:4.8; pre: 2013:12.9 2014:10.1 2015:15.4 2016:9.2 2017:7.9 2018:9.1 2019:5.9 2020:8.7 2021:6.8 2022:11.1 2023:8.2 2024:6.4 2025:7.9 2026:6.2; nyam: 2013:14.5 2014:11.1 2015:16.9 2016:10.7 2017:8.6 2018:10.0 2019:6.9 2020:10.4 2021:8.0 2022:12.5 2023:9.7 2024:7.5 2025:9.4 2026:7.3; nypm: 2013:10.6 2014:7.9 2015:12.8 2016:8.0 2017:6.8 2018:7.8 2019:5.2 2020:7.0 2021:5.4 2022:8.9 2023:6.6 2024:5.1 2025:6.9 2026:5.5; close: 2013:7.7 2014:5.6 2015:9.3 2016:5.6 2017:5.0 2018:5.4 2019:3.5 2020:5.0 2021:3.6 2022:6.2 2023:4.3 2024:3.4 2025:4.7 2026:3.7

### 10. Versus NQ
Contemporaneous correlation of h-min returns (normalised): asia: 1m 0.08 5m 0.10 15m 0.10 30m 0.10 60m 0.10; london: 1m 0.09 5m 0.10 15m 0.10 30m 0.10 60m 0.10; pre: 1m 0.13 5m 0.14 15m 0.14; nyam: 1m 0.07 5m 0.08 15m 0.08 30m 0.07; nypm: 1m 0.11 5m 0.14 15m 0.17 30m 0.18; close: 1m 0.08 5m 0.10 15m 0.12

Lead/lag (1-15 min, family 180 cells; corr of 1-min normalised returns): cells beating the family null (top 10 by |z|; "NQ->X" = NQ leads 6E):
| direction | session | lag min | corr | z | p_family | year sign share |
|--|--|--|--|--|--|--|
| NQ->6E | asia | 1 | +0.0046 | +5.9 | 0.010 | 0.57 |
| 6E->NQ | asia | 1 | +0.0049 | +5.7 | 0.010 | 0.79 |
| NQ->6E | close | 1 | +0.0087 | +5.5 | 0.010 | 0.86 |
| 6E->NQ | london | 1 | +0.0051 | +5.4 | 0.010 | 0.79 |
| 6E->NQ | pre | 1 | +0.0103 | +5.2 | 0.010 | 0.79 |
| NQ->6E | nypm | 4 | +0.0052 | +4.6 | 0.010 | 0.64 |
| NQ->6E | nypm | 1 | +0.0052 | +4.5 | 0.010 | 0.71 |
| 6E->NQ | nypm | 2 | +0.0049 | +4.3 | 0.010 | 0.79 |
| 6E->NQ | asia | 6 | +0.0031 | +4.3 | 0.010 | 0.71 |
| 6E->NQ | asia | 15 | +0.0037 | +4.1 | 0.010 | 0.71 |

### 11. Map rows that become book candidates under the FROZEN rule (p_family <= .05 AND room_A(session) > 2.0)
| map row | direction | stat | p_family | room_A | year sign share | stability | 1.7% cap >= 1 contract/5min in session |
|--|--|--|--|--|--|--|--|
| AC|asia|5m | reversion | -0.047 | 0.003 | 3.7 | 1.00 |  | yes |
| AC|london|5m | reversion | -0.029 | 0.003 | 6.7 | 1.00 |  | yes |
| AC|pre|5m | reversion | -0.026 | 0.003 | 8.6 | 0.86 |  | yes |
| AC|nyam|5m | reversion | -0.031 | 0.003 | 9.8 | 1.00 |  | yes |
| AC|nypm|5m | reversion | -0.059 | 0.003 | 7.1 | 0.79 |  | yes |
| AC|close|5m | reversion | -0.096 | 0.003 | 5.0 | 1.00 |  | yes |
| AC|asia|15m | reversion | -0.027 | 0.003 | 3.7 | 0.86 |  | yes |
| AC|london|15m | reversion | -0.018 | 0.003 | 6.7 | 1.00 |  | yes |
| AC|nypm|15m | reversion | -0.030 | 0.003 | 7.1 | 0.71 |  | yes |
| AC|close|15m | reversion | -0.074 | 0.003 | 5.0 | 1.00 |  | yes |
| AC|london|30m | reversion | -0.022 | 0.017 | 6.7 | 1.00 |  | yes |
| AC|close|30m | reversion | -0.061 | 0.003 | 5.0 | 0.93 |  | yes |
| rx|PD|asia | level-bounce | +0.534 | 0.016 | 3.7 | 0.93 | stable | yes |
| fb|PD|nypm | level-break | +0.436 | 0.016 | 7.1 | 0.71 | stable | yes |
| fb|PD|close | level-break | +0.336 | 0.016 | 5.0 | 0.79 | stable | yes |
| rx|ON|nyam | level-break | +0.502 | 0.016 | 9.8 | 0.79 | stable | yes |
| fb|ON|close | level-break | +0.371 | 0.016 | 5.0 | 0.93 | stable | yes |
| fb|IB|nypm | level-break | +0.438 | 0.016 | 7.1 | 0.93 | stable | yes |
| fb|IB|close | level-break | +0.421 | 0.016 | 5.0 | 0.71 | stable | yes |
| rx|VW2|nyam | level-bounce | +0.561 | 0.016 | 9.8 | 0.64 | stable | yes |
| rx|VW2|close | level-bounce | +0.599 | 0.016 | 5.0 | 0.57 | unstable | yes |
| gap|b1|day | level-break | +0.731 | 0.016 | 9.8 | 0.79 | stable | yes |
| gap|b2|day | level-break | +0.502 | 0.016 | 9.8 | 0.71 | stable | yes |
| gap|b3|h1 | level-bounce | +0.044 | 0.016 | 9.8 | 0.79 | stable | yes |
| vr|asia|5 | reversion | +0.853 | 0.016 | 3.7 | 1.00 | stable | yes |
| vr|asia|15 | reversion | +0.794 | 0.016 | 3.7 | 1.00 | stable | yes |
| vr|asia|30 | reversion | +0.773 | 0.016 | 3.7 | 1.00 | stable | yes |
| vr|asia|60 | reversion | +0.765 | 0.016 | 3.7 | 1.00 | stable | yes |
| vr|asia|120 | reversion | +0.771 | 0.016 | 3.7 | 0.93 | stable | yes |
| hurst|asia | reversion | +0.484 | 0.016 | 3.7 | 0.79 | stable | yes |
| vr|london|5 | reversion | +0.891 | 0.016 | 6.7 | 1.00 | stable | yes |
| vr|london|15 | reversion | +0.854 | 0.016 | 6.7 | 1.00 | stable | yes |
| vr|london|30 | reversion | +0.841 | 0.016 | 6.7 | 1.00 | stable | yes |
| vr|london|60 | reversion | +0.826 | 0.016 | 6.7 | 1.00 | stable | yes |
| vr|london|120 | reversion | +0.824 | 0.016 | 6.7 | 1.00 | stable | yes |
| hurst|london | reversion | +0.487 | 0.016 | 6.7 | 1.00 | stable | yes |
| vr|pre|5 | reversion | +0.914 | 0.016 | 8.6 | 1.00 | stable | yes |
| vr|pre|15 | reversion | +0.880 | 0.016 | 8.6 | 0.86 | stable | yes |
| hurst|pre | reversion | +0.483 | 0.016 | 8.6 | 0.86 | stable | yes |
| vr|nyam|5 | reversion | +0.888 | 0.016 | 9.8 | 1.00 | stable | yes |
| vr|nyam|15 | reversion | +0.851 | 0.016 | 9.8 | 1.00 | stable | yes |
| vr|nyam|30 | reversion | +0.837 | 0.016 | 9.8 | 1.00 | stable | yes |
| hurst|nyam | reversion | +0.483 | 0.016 | 9.8 | 0.93 | stable | yes |
| vr|nypm|5 | reversion | +0.728 | 0.016 | 7.1 | 1.00 | stable | yes |
| vr|nypm|15 | reversion | +0.667 | 0.016 | 7.1 | 1.00 | stable | yes |
| vr|nypm|30 | reversion | +0.643 | 0.016 | 7.1 | 1.00 | stable | yes |
| vr|nypm|60 | reversion | +0.639 | 0.016 | 7.1 | 0.93 | stable | yes |
| hurst|nypm | reversion | +0.473 | 0.016 | 7.1 | 0.86 | stable | yes |
| vr|close|5 | reversion | +0.665 | 0.016 | 5.0 | 1.00 | stable | yes |
| vr|close|15 | reversion | +0.567 | 0.016 | 5.0 | 1.00 | stable | yes |
| vr|close|30 | reversion | +0.525 | 0.016 | 5.0 | 1.00 | stable | yes |
| hurst|close | reversion | +0.434 | 0.016 | 5.0 | 1.00 | stable | yes |
| vr|rth|5 | reversion | +0.808 | 0.016 | 9.8 | 1.00 | stable | yes |
| vr|rth|15 | reversion | +0.756 | 0.016 | 9.8 | 1.00 | stable | yes |
| vr|rth|30 | reversion | +0.734 | 0.016 | 9.8 | 1.00 | stable | yes |
| vr|rth|60 | reversion | +0.713 | 0.016 | 9.8 | 1.00 | stable | yes |
| vr|rth|120 | reversion | +0.687 | 0.016 | 9.8 | 1.00 | stable | yes |
| hurst|rth | reversion | +0.475 | 0.016 | 9.8 | 0.93 | stable | yes |

### 12. CHAR-C complements
Data note: bars are the CHAR-C bad-print-repaired copy (cc_clean.py, MORNING_FLAGS 2026-11-05); for 6E/6J the 2013-2015 years carried ~2% bars with highs/lows/closes >10 sigma outside the neighbours, which would have driven VR/Hurst and level-touch rates (raw 6E NY-PM VR(30) .16 -> .64 after repair).

Gross edge per signal (CHAR-C own cross-check cc_ac.py: past-h move >= 1 sigma, mean of sign x next-h move in $/lot, repaired bars, 15-minute decision points; shuffled-day family null on 153+ cells) against the round-trip cost $24.00:

| session | 5 min: edge $ (x cost) | 15 min: edge $ (x cost) | 30 min: edge $ (x cost) | 60 min: edge $ (x cost) |
|--|--|--|--|--|
| asia | -2.1 (0.09x) | -1.8 (0.07x) | -2.4 (0.10x) | -3.2 (0.13x) |
| london | -2.3 (0.10x) | -1.5 (0.06x) | -3.4 (0.14x) | -2.1 (0.09x) |
| pre | -2.7 (0.11x) | -4.4 (0.18x) | -3.4 (0.14x) | -1.9 (0.08x) |
| nyam | -3.5 (0.14x) | -5.2 (0.22x) | -4.4 (0.18x) | -4.1 (0.17x) |
| nypm | -8.8 (0.37x) | -4.2 (0.18x) | -3.4 (0.14x) | +0.3 (0.01x) |
| close | -5.4 (0.22x) | -6.4 (0.27x) | -4.5 (0.19x) | -2.9 (0.12x) |

Time-of-day drift map (cc_tod.py, signed 30-minute returns by ET slot, sign-flip-by-day null, 2000 worlds, family = slots): wd 06:30: -0.47 bp, -7.0 $/lot (0.29x cost), t -4.1, p_family 0.000, same sign 71% of 14 years; wd 07:30: -0.80 bp, -11.4 $/lot (0.48x cost), t -5.5, p_family 0.000, same sign 93% of 14 years; wd 22:00: +0.32 bp, +4.7 $/lot (0.20x cost), t 3.8, p_family 0.004, same sign 71% of 14 years; wd 01:30: -0.29 bp, -4.2 $/lot (0.18x cost), t -3.4, p_family 0.024, same sign 79% of 14 years.


## 6J - character map (CHAR-C, 2026-11-05T23:31Z)
Base: 6J CME front-month (.v.0) 1-min bars from 2013-01 to 2026-10, percent frame (multiplicative roll-adjusted), 1-min approximation (no tick path), 3405 usable label days; ET clock, sessions asia 18:00-02:00 / london 02:00-08:30 / pre 08:30-09:30 / nyam 09:30-12:00 / nypm 12:00-15:00 / close 15:00-16:55. Nulls: within-year shuffled-day (AC B=300; structure B=100 worlds; levels recomputed on the shuffled path; round numbers 60 random grid phases); p_family = Westfall-Young max-|z| over the block (AC family 153 cells, structure family 92 cells). `**` p_family<=.05, `*` <=.10. Prereg sha256 980bedf6bad3f1669de9efb93831fa4622d88577c892d9359b7f57ba93c9dbcf. Descriptive only: no PASS, nothing live.

### Plain paragraph (CHAR-C)
6J (yen FX) behaves like 6E but weaker above 5 minutes: the lag correlation is negative at 1 and 5 minutes in all six sessions (5-minute -0.018 pre to -0.094 close, NY-PM -0.071; p_family <= .023; same sign in 10-14 of 14 years), at 15 minutes only in Asia (-0.012), NY-PM (-0.028) and the close (-0.026), and absent from 30 minutes on (|corr| <= .037, p_family 0.78-1.0). VR(30) is .58 in the close, .60 NY-PM and .83-.84 elsewhere (Hurst .46-.49), again largely bid-ask bounce, and the gross edge of fading a 1-sigma move is $0.3-9.0 per signal (NY-PM 5 minutes $9.0 = 0.36 x the $25.0 round trip; close 5 / 15 minutes $4.7 / $5.8). Trend days 41% (null 43%, p_family .26), range days 28% (null 28%); the IB is extended on one side 69% (null 60%), both 25% (null 38%), and the extension closes beyond the edge 61% (null 68%). Levels: IB-edge touches in the close bounce 61% (null 51%; 13 of 14 years), VWAP +-1 sigma in the close 55% (null 50%) and +-2 sigma in NY-AM / close 55% / 57% (null 53% / 52%), prior-day H/L in Asia 51% vs 47% (p_family .049), overnight H/L in NY-AM / NY-PM break through more (51% vs 55% / 56%); after a 1-A move from the 08:30 start the continuation is more likely than the null (39% vs 36%), in NY-PM less (29% vs 32%); 09:30 gaps of .10-.25 of the daily range fill within an hour 58% of the time (null 48%, n 483). No 30-minute drift slot passes (best 16:00 ET -0.3 bp, p_family .087). Room: 3 x ATR5 = 3.9x / 4.4x / 5.5x / 6.5x / 4.7x / 3.5x the $25.0 round trip from Asia to the close (one ATR5 1.2-2.2x); cap 3.4 (Asia) to 12.5 (NY-AM) contracts per 5 minutes against 7-14 lots needed. Versus NQ the correlation is NEGATIVE (-0.13 to -0.29 in Asia, London, NY and the close; yen up when NQ is down; ~0 in the pre-NY hour); the 6J books scored below show -0.04 to +0.08 weekly correlation to the NQ stack. The book that fits is a 5-minute excursion fade (>= 2-3 ATR5) in pre / NY-AM / NY-PM and an IB-edge / VWAP fade in the close; none clears (DS3_FIND.md).

### Generated summary (page.py of CHAR-A, same numbers)
At 1 minute every session has negative autocorrelation (-0.186 to -0.048; bid-ask bounce / last-print noise, not a tradable edge by itself). asia: reverts at 5/15 min (-0.030, -0.012). london: reverts at 5 min (-0.031). pre: reverts at 5 min (-0.018). nyam: reverts at 5 min (-0.029). nypm: reverts at 5/15 min (-0.071, -0.028). close: reverts at 5/15 min (-0.094, -0.026). Day types (RTH): 41% trend days (efficiency ratio >= .5; shuffled null 43%, p_fam 0.262), 28% range days (<.25; null 27%, p_fam 1.000); the IB (09:30-10:30) is extended on one side only on 69% of days and on both on 25%, and a one-sided extension closes beyond the IB edge 61% of the time (null 68%). RTH variance ratio at 30 min 0.704 (shuffled null 0.999, p_fam 0.016); Hurst 0.475. The RTH range forms 9:30 (36%), 10:00 (31%), 11:00 (12%) of the range increments. Level reactions that beat the family null: PD|asia bounces 51% of touches (more than the shuffled null 47%); ON|nyam bounces 51% of touches (less, i.e. breaks through more than the shuffled null 55%); ON|nypm bounces 51% of touches (less, i.e. breaks through more than the shuffled null 56%); IB|close bounces 61% of touches (more than the shuffled null 51%); VW1|close bounces 55% of touches (more than the shuffled null 50%); VW2|nyam bounces 55% of touches (more than the shuffled null 53%); VW2|close bounces 57% of touches (more than the shuffled null 52%); RN|london bounces 48% of touches (less, i.e. breaks through more than the shuffled null 49%). Failed-break follow-through beating the null: none. Room (median 3xATR14(5m) $ / round-trip cost $25 per lot): asia 3.9x, london 4.4x, pre 5.5x, nyam 6.5x, nypm 4.7x, close 3.5x (1xATR5 room 2.2x in nyam, 1.3x in asia).

### 1. Autocorrelation of h-min returns (corr(past h, next h), both inside the session), pooled; cell = corr (pre-2023 mean | 2023+ mean) p_family
| session | 1 min | 5 min | 15 min | 30 min | 60 min | 120 min |
|--|--|--|--|--|--|--|
| asia | -0.062 (-0.070|-0.048) p0.003** ys1.00 | -0.030 (-0.037|-0.016) p0.003** ys0.93 | -0.012 (-0.019|+0.000) p0.013** ys0.79 | -0.008 (-0.005|-0.019) p1.000 ys0.71 | -0.001 (-0.007|-0.002) p1.000 ys0.57 | +0.001 (-0.010|+0.002) p1.000 ys0.29 |
| london | -0.069 (-0.078|-0.036) p0.003** ys1.00 | -0.031 (-0.040|-0.018) p0.003** ys1.00 | -0.007 (-0.018|+0.009) p1.000 ys0.57 | +0.002 (-0.012|+0.018) p1.000 ys0.43 | +0.015 (-0.002|+0.044) p0.977 ys0.50 | +0.037 (+0.027|+0.063) p0.272 ys0.86 |
| pre | -0.048 (-0.057|-0.024) p0.003** ys0.86 | -0.018 (-0.027|-0.015) p0.023** ys0.71 | -0.021 (-0.023|-0.040) p0.950 ys0.57 | +0.019 (+0.019|+0.029) p1.000 ys0.64 | - | - |
| nyam | -0.072 (-0.077|-0.029) p0.003** ys0.93 | -0.029 (-0.039|-0.013) p0.003** ys0.86 | -0.002 (-0.010|+0.012) p1.000 ys0.57 | -0.004 (+0.002|-0.042) p1.000 ys0.57 | -0.022 (-0.032|-0.031) p1.000 ys0.79 | - |
| nypm | -0.182 (-0.133|-0.051) p0.003** ys1.00 | -0.071 (-0.072|-0.028) p0.003** ys0.79 | -0.028 (-0.038|-0.014) p0.007** ys0.57 | -0.004 (-0.005|-0.026) p1.000 ys0.57 | -0.009 (-0.005|-0.040) p1.000 ys0.50 | - |
| close | -0.186 (-0.139|-0.085) p0.003** ys1.00 | -0.094 (-0.105|-0.025) p0.003** ys0.93 | -0.026 (-0.082|+0.090) p0.007** ys0.86 | -0.022 (-0.055|+0.024) p0.781 ys0.71 | - | - |

Hour cells (h >= 5) beating the family null, top 14 by |z| (hour = ET hour of the decision bar):
| h | session | hour ET | corr | z | p_family | year sign share | pre-2023 | 2023+ |
|--|--|--|--|--|--|--|--|--|
| 5 | close | 16 | -0.099 | -23.3 | 0.003 | 0.86 | -0.126 | +0.005 |
| 5 | close | 15 | -0.090 | -22.5 | 0.003 | 0.93 | -0.092 | -0.055 |
| 5 | nypm | 12 | -0.077 | -18.8 | 0.003 | 0.79 | -0.072 | -0.055 |
| 5 | nypm | 13 | -0.070 | -18.5 | 0.003 | 0.71 | -0.070 | -0.026 |
| 5 | nypm | 14 | -0.066 | -16.3 | 0.003 | 0.64 | -0.075 | -0.004 |
| 5 | nyam | 11 | -0.049 | -12.4 | 0.003 | 0.86 | -0.061 | -0.030 |
| 5 | asia | 18 | -0.043 | -12.2 | 0.003 | 0.86 | -0.056 | -0.027 |
| 5 | london | 05 | -0.049 | -12.0 | 0.003 | 0.86 | -0.052 | -0.046 |
| 5 | asia | 22 | -0.049 | -12.0 | 0.003 | 1.00 | -0.054 | -0.046 |
| 5 | london | 06 | -0.044 | -11.6 | 0.003 | 0.93 | -0.052 | -0.035 |
| 5 | asia | 23 | -0.044 | -11.4 | 0.003 | 0.86 | -0.050 | -0.029 |
| 5 | asia | 01 | -0.047 | -11.0 | 0.003 | 0.93 | -0.061 | -0.023 |
| 5 | london | 07 | -0.042 | -10.9 | 0.003 | 0.79 | -0.049 | -0.040 |
| 15 | asia | 18 | -0.061 | -8.8 | 0.003 | 0.86 | -0.079 | -0.033 |

### 2. Variance ratio VR(q) and Hurst (1.0 = random walk; <1 reverting; edge-bias corrected), cell = value (null) p_family
| session | VR5 | VR15 | VR30 | VR60 | VR120 | Hurst |
|--|--|--|--|--|--|--|
| asia | 0.881 (1.000) p0.016** | 0.846 (0.999) p0.016** | 0.837 (0.999) p0.016** | 0.835 (0.998) p0.016** | 0.840 (0.999) p0.016** | 0.493 (0.500) p0.016** |
| london | 0.877 (1.000) p0.016** | 0.839 (0.999) p0.016** | 0.834 (0.998) p0.016** | 0.836 (0.999) p0.016** | 0.843 (1.001) p0.016** | 0.494 (0.500) p0.049** |
| pre | 0.905 (1.001) p0.016** | 0.876 (0.999) p0.016** | - | - | - | 0.485 (0.499) p0.016** |
| nyam | 0.874 (1.000) p0.016** | 0.840 (0.999) p0.016** | 0.840 (1.000) p0.016** | - | - | 0.488 (0.500) p0.016** |
| nypm | 0.684 (0.998) p0.016** | 0.618 (0.998) p0.016** | 0.595 (0.999) p0.016** | 0.596 (0.999) p0.016** | - | 0.471 (0.500) p0.016** |
| close | 0.675 (0.999) p0.016** | 0.590 (1.000) p0.016** | 0.583 (1.002) p0.016** | - | - | 0.457 (0.501) p0.016** |
| rth | 0.775 (0.999) p0.016** | 0.719 (0.999) p0.016** | 0.704 (0.999) p0.016** | 0.681 (1.000) p0.016** | 0.657 (1.000) p0.016** | 0.475 (0.500) p0.016** |

### 3. Day types (ex-post labels of the RTH day)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| day|trend | 0.412 | 3405 | 0.434 | -2.7 | 0.262 | 0.64 | 0.398 | 0.444 | stable |
| day|range | 0.283 | 3405 | 0.275 | +1.2 | 1.000 | 0.43 | 0.286 | 0.281 | unstable |
| day|er | 0.434 | 3405 | 0.448 | -3.5 | 0.016** | 0.57 | 0.428 | 0.448 | unstable |
| day|ib_none | 0.059 | 3405 | 0.021 | +17.0 | 0.016** | 0.86 | 0.061 | 0.054 | stable |
| day|ib_one | 0.694 | 3405 | 0.601 | +12.9 | 0.016** | 1.00 | 0.685 | 0.714 | stable |
| day|ib_both | 0.246 | 3405 | 0.378 | -17.9 | 0.016** | 1.00 | 0.254 | 0.233 | stable |
| day|ib_one_closebeyond | 0.610 | 2364 | 0.682 | -7.3 | 0.016** | 0.86 | 0.609 | 0.604 | stable |

### 4. 1A -> 2A continuation vs give-back-half from the session open (A = 3 x ATR14(5m)); value = P(continue | resolved)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| cont|asia | 0.391 | 3247 | 0.392 | -0.2 | 1.000 | 0.57 | 0.390 | 0.393 | unstable |
| cont|london | 0.341 | 3327 | 0.361 | -2.5 | 0.492 | 0.71 | 0.344 | 0.332 | stable |
| cont|pre | 0.387 | 1577 | 0.355 | +3.6 | 0.016** | 0.64 | 0.379 | 0.407 | stable |
| cont|nyam | 0.311 | 2343 | 0.320 | -1.1 | 1.000 | 0.57 | 0.302 | 0.328 | unstable |
| cont|nypm | 0.290 | 1143 | 0.324 | -3.2 | 0.049** | 0.79 | 0.300 | 0.242 | stable |
| cont|close | 0.279 | 811 | 0.313 | -2.7 | 0.361 | 0.71 | 0.265 | 0.296 | stable |
| cont|rth | 0.319 | 2890 | 0.336 | -2.2 | 0.869 | 0.57 | 0.311 | 0.332 | unstable |

### 5. Gap fill by size bucket (b0 .05-.10, b1 .10-.25, b2 .25-.50, b3 >.50 of the 20-day mean RTH range); day = filled during RTH, h1 = within 60 min
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| gap|b0|day | 0.878 | 205 | 0.910 | -1.5 | 1.000 | 0.64 | 0.890 | 0.871 | stable |
| gap|b0|h1 | 0.785 | 205 | 0.747 | +1.0 | 1.000 | 0.79 | 0.790 | 0.793 | stable |
| gap|b1|day | 0.754 | 483 | 0.784 | -1.6 | 1.000 | 0.64 | 0.763 | 0.706 | stable |
| gap|b1|h1 | 0.580 | 483 | 0.483 | +4.6 | 0.016** | 0.86 | 0.587 | 0.579 | stable |
| gap|b2|day | 0.516 | 692 | 0.551 | -1.9 | 0.984 | 0.79 | 0.523 | 0.499 | stable |
| gap|b2|h1 | 0.249 | 692 | 0.214 | +2.2 | 0.852 | 0.71 | 0.243 | 0.268 | stable |
| gap|b3|day | 0.174 | 1849 | 0.163 | +1.4 | 1.000 | 0.50 | 0.196 | 0.134 | unstable |
| gap|b3|h1 | 0.043 | 1849 | 0.028 | +3.7 | 0.016** | 0.79 | 0.047 | 0.041 | stable |

### 6. Level reaction: first touch -> bounce (0.5A reverse) vs break-through (0.5A beyond) within 60 min; value = P(bounce)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| rx|PD|asia | 0.507 | 2924 | 0.474 | +3.2 | 0.049** | 0.86 | 0.508 | 0.510 | stable |
| rx|PD|london | 0.524 | 2192 | 0.505 | +1.6 | 1.000 | 0.57 | 0.515 | 0.552 | unstable |
| rx|PD|pre | 0.507 | 1107 | 0.495 | +0.8 | 1.000 | 0.57 | 0.506 | 0.512 | unstable |
| rx|PD|nyam | 0.509 | 1425 | 0.526 | -1.3 | 1.000 | 0.50 | 0.513 | 0.503 | unstable |
| rx|PD|nypm | 0.518 | 861 | 0.549 | -2.3 | 0.689 | 0.71 | 0.510 | 0.535 | stable |
| rx|PD|close | 0.538 | 422 | 0.519 | +1.0 | 1.000 | 0.57 | 0.557 | 0.545 | unstable |
| rx|ON|nyam | 0.514 | 1922 | 0.548 | -3.8 | 0.016** | 0.64 | 0.516 | 0.519 | stable |
| rx|ON|nypm | 0.514 | 1043 | 0.556 | -3.5 | 0.016** | 0.71 | 0.517 | 0.480 | stable |
| rx|ON|close | 0.530 | 500 | 0.523 | +0.4 | 1.000 | 0.64 | 0.535 | 0.506 | stable |
| rx|IB|nyam | 0.545 | 2851 | 0.534 | +1.4 | 1.000 | 0.43 | 0.552 | 0.526 | unstable |
| rx|IB|nypm | 0.545 | 2053 | 0.535 | +0.9 | 1.000 | 0.29 | 0.552 | 0.497 | unstable |
| rx|IB|close | 0.614 | 1001 | 0.507 | +7.6 | 0.016** | 0.93 | 0.601 | 0.619 | stable |
| rx|VW1|nyam | 0.482 | 5194 | 0.498 | -2.9 | 0.164 | 0.64 | 0.485 | 0.475 | stable |
| rx|VW1|nypm | 0.515 | 3034 | 0.518 | -0.3 | 1.000 | 0.79 | 0.523 | 0.473 | REGIME(2023+ only) |
| rx|VW1|close | 0.552 | 1881 | 0.499 | +4.8 | 0.016** | 0.93 | 0.559 | 0.521 | stable |
| rx|VW2|nyam | 0.554 | 4012 | 0.525 | +4.5 | 0.016** | 0.79 | 0.550 | 0.566 | stable |
| rx|VW2|nypm | 0.542 | 1983 | 0.542 | -0.1 | 1.000 | 0.64 | 0.548 | 0.520 | REGIME(2023+ only) |
| rx|VW2|close | 0.572 | 844 | 0.517 | +3.7 | 0.016** | 0.71 | 0.575 | 0.527 | stable |
| rx|RN|asia | 0.485 | 34118 | 0.484 | +0.4 | 1.000 | 0.57 | 0.487 | 0.480 | unstable |
| rx|RN|london | 0.480 | 33442 | 0.489 | -3.2 | 0.049** | 0.71 | 0.485 | 0.460 | stable |
| rx|RN|pre | 0.491 | 8071 | 0.492 | -0.3 | 1.000 | 0.57 | 0.491 | 0.481 | unstable |
| rx|RN|nyam | 0.500 | 17619 | 0.495 | +1.5 | 1.000 | 0.43 | 0.499 | 0.495 | unstable |
| rx|RN|nypm | 0.491 | 11864 | 0.491 | -0.0 | 1.000 | 0.57 | 0.493 | 0.487 | REGIME(2023+ only) |
| rx|RN|close | 0.498 | 4633 | 0.490 | +1.4 | 1.000 | 0.57 | 0.499 | 0.481 | unstable |

### 7. Failed break (close .25A beyond, back inside within 10 bars): fade follow-through P(0.5A back before 0.5A out)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| fb|PD|asia | 0.482 | 1733 | 0.498 | -1.2 | 1.000 | 0.50 | 0.485 | 0.481 | unstable |
| fb|PD|london | 0.477 | 1582 | 0.503 | -2.1 | 0.885 | 0.79 | 0.474 | 0.487 | stable |
| fb|PD|pre | 0.509 | 597 | 0.501 | +0.4 | 1.000 | 0.50 | 0.520 | 0.484 | unstable |
| fb|PD|nyam | 0.462 | 849 | 0.500 | -2.3 | 0.803 | 0.93 | 0.455 | 0.478 | stable |
| fb|PD|nypm | 0.450 | 544 | 0.500 | -2.3 | 0.754 | 0.57 | 0.449 | 0.458 | unstable |
| fb|PD|close | 0.435 | 232 | 0.502 | -2.1 | 0.885 | 0.57 | 0.465 | 0.466 | unstable |
| fb|ON|nyam | 0.488 | 701 | 0.500 | -0.6 | 1.000 | 0.57 | 0.503 | 0.486 | REGIME(2023+ only) |
| fb|ON|nypm | 0.475 | 526 | 0.497 | -1.2 | 1.000 | 0.57 | 0.504 | 0.383 | REGIME(2023+ only) |
| fb|ON|close | 0.395 | 238 | 0.499 | -3.0 | 0.148 | 0.79 | 0.415 | 0.389 | stable |
| fb|IB|nyam | 0.472 | 672 | 0.499 | -1.8 | 1.000 | 0.64 | 0.486 | 0.413 | stable |
| fb|IB|nypm | 0.465 | 937 | 0.498 | -2.4 | 0.639 | 0.71 | 0.460 | 0.472 | stable |
| fb|IB|close | 0.485 | 482 | 0.498 | -0.6 | 1.000 | 0.43 | 0.481 | 0.493 | unstable |

### 8. Where the range forms
RTH range increments by bin: 9:30 36.2%, 10:00 31.3%, 11:00 11.7%, 12:00 6.6%, 13:00 5.1%, 14:00 6.0%, 15:00 3.1%
Label-day range increments by ET hour (percent of the day): 00h nan, 01h nan, 02h nan, 03h nan, 04h nan, 05h nan, 06h nan, 07h nan, 08h nan, 09h nan, 10h nan, 11h nan, 12h nan, 13h nan, 14h nan, 15h nan, 16h nan, 18h nan, 19h nan, 20h nan, 21h nan, 22h nan, 23h nan

### 9. Room and liquidity (all years, raw-frame $, 1 lot)
| session | ATR14(5m) $ | A=3xATR5 $ | RT cost $ | room(1 ATR5) | room(A) | median 5-min vol | 1.7% cap (contracts/5min) | lots for $1,200 at 3xATR5 stop |
|--|--|--|--|--|--|--|--|--|
| asia | 33 | 98 | 25 | 1.30 | 3.91 | 202 | 3.4 | 12.3 |
| london | 36 | 109 | 25 | 1.46 | 4.38 | 328 | 5.6 | 11.0 |
| pre | 46 | 137 | 25 | 1.83 | 5.50 | 653 | 11.1 | 8.7 |
| nyam | 54 | 162 | 25 | 2.16 | 6.49 | 736 | 12.5 | 7.4 |
| nypm | 39 | 118 | 25 | 1.57 | 4.71 | 316 | 5.4 | 10.2 |
| close | 30 | 89 | 25 | 1.18 | 3.54 | 165 | 2.8 | 13.6 |

room(A) by year: asia: 2013:8.1 2014:4.3 2015:3.7 2016:6.6 2017:4.3 2018:3.9 2019:3.0 2020:3.4 2021:2.7 2022:4.4 2023:3.7 2024:3.5 2025:3.9 2026:2.5; london: 2013:8.7 2014:4.6 2015:4.4 2016:6.8 2017:4.8 2018:4.0 2019:3.0 2020:3.9 2021:3.6 2022:5.1 2023:4.6 2024:3.9 2025:4.1 2026:2.8; pre: 2013:11.0 2014:6.6 2015:5.8 2016:7.6 2017:6.1 2018:4.7 2019:3.9 2020:4.8 2021:4.7 2022:6.5 2023:6.1 2024:5.0 2025:4.8 2026:3.2; nyam: 2013:12.4 2014:7.7 2015:6.6 2016:9.1 2017:7.4 2018:5.8 2019:4.8 2020:5.8 2021:5.4 2022:7.2 2023:7.0 2024:5.8 2025:5.8 2026:3.7; nypm: 2013:9.7 2014:5.7 2015:5.1 2016:7.0 2017:5.9 2018:4.9 2019:3.7 2020:4.1 2021:3.4 2022:4.8 2023:4.3 2024:3.8 2025:4.1 2026:2.9; close: 2013:8.3 2014:4.5 2015:4.1 2016:5.5 2017:4.7 2018:3.9 2019:3.0 2020:3.0 2021:2.4 2022:3.4 2023:2.9 2024:2.6 2025:2.9 2026:2.2

### 10. Versus NQ
Contemporaneous correlation of h-min returns (normalised): asia: 1m -0.19 5m -0.24 15m -0.26 30m -0.27 60m -0.29; london: 1m -0.16 5m -0.18 15m -0.19 30m -0.20 60m -0.22; pre: 1m 0.00 5m 0.02 15m 0.03; nyam: 1m -0.18 5m -0.21 15m -0.21 30m -0.22; nypm: 1m -0.13 5m -0.17 15m -0.16 30m -0.16; close: 1m -0.14 5m -0.19 15m -0.21

Lead/lag (1-15 min, family 180 cells; corr of 1-min normalised returns): cells beating the family null (top 10 by |z|; "NQ->X" = NQ leads 6J):
| direction | session | lag min | corr | z | p_family | year sign share |
|--|--|--|--|--|--|--|
| NQ->6J | asia | 1 | -0.0163 | -22.5 | 0.010 | 0.93 |
| 6J->NQ | asia | 1 | -0.0096 | -12.9 | 0.010 | 0.71 |
| NQ->6J | london | 1 | -0.0095 | -11.0 | 0.010 | 0.93 |
| NQ->6J | nyam | 1 | -0.0113 | -7.7 | 0.010 | 1.00 |
| NQ->6J | nypm | 1 | -0.0083 | -7.3 | 0.010 | 0.86 |
| 6J->NQ | pre | 1 | +0.0149 | +6.4 | 0.010 | 0.86 |
| 6J->NQ | nypm | 1 | +0.0057 | +4.3 | 0.020 | 0.79 |
| 6J->NQ | asia | 4 | -0.0038 | -4.2 | 0.020 | 0.71 |
| NQ->6J | london | 4 | -0.0036 | -4.1 | 0.020 | 0.71 |
| NQ->6J | asia | 3 | -0.0033 | -3.9 | 0.030 | 0.93 |

### 11. Map rows that become book candidates under the FROZEN rule (p_family <= .05 AND room_A(session) > 2.0)
| map row | direction | stat | p_family | room_A | year sign share | stability | 1.7% cap >= 1 contract/5min in session |
|--|--|--|--|--|--|--|--|
| AC|asia|5m | reversion | -0.030 | 0.003 | 3.9 | 0.93 |  | yes |
| AC|london|5m | reversion | -0.031 | 0.003 | 4.4 | 1.00 |  | yes |
| AC|pre|5m | reversion | -0.018 | 0.023 | 5.5 | 0.71 |  | yes |
| AC|nyam|5m | reversion | -0.029 | 0.003 | 6.5 | 0.86 |  | yes |
| AC|nypm|5m | reversion | -0.071 | 0.003 | 4.7 | 0.79 |  | yes |
| AC|close|5m | reversion | -0.094 | 0.003 | 3.5 | 0.93 |  | yes |
| AC|asia|15m | reversion | -0.012 | 0.013 | 3.9 | 0.79 |  | yes |
| AC|nypm|15m | reversion | -0.028 | 0.007 | 4.7 | 0.57 |  | yes |
| AC|close|15m | reversion | -0.026 | 0.007 | 3.5 | 0.86 |  | yes |
| rx|PD|asia | level-bounce | +0.507 | 0.049 | 3.9 | 0.86 | stable | yes |
| rx|ON|nyam | level-break | +0.514 | 0.016 | 6.5 | 0.64 | stable | yes |
| rx|ON|nypm | level-break | +0.514 | 0.016 | 4.7 | 0.71 | stable | yes |
| rx|IB|close | level-bounce | +0.614 | 0.016 | 3.5 | 0.93 | stable | yes |
| rx|VW1|close | level-bounce | +0.552 | 0.016 | 3.5 | 0.93 | stable | yes |
| rx|VW2|nyam | level-bounce | +0.554 | 0.016 | 6.5 | 0.79 | stable | yes |
| rx|VW2|close | level-bounce | +0.572 | 0.016 | 3.5 | 0.71 | stable | yes |
| gap|b1|h1 | level-bounce | +0.580 | 0.016 | 6.5 | 0.86 | stable | yes |
| gap|b3|h1 | level-bounce | +0.043 | 0.016 | 6.5 | 0.79 | stable | yes |
| vr|asia|5 | reversion | +0.881 | 0.016 | 3.9 | 1.00 | stable | yes |
| vr|asia|15 | reversion | +0.846 | 0.016 | 3.9 | 1.00 | stable | yes |
| vr|asia|30 | reversion | +0.837 | 0.016 | 3.9 | 1.00 | stable | yes |
| vr|asia|60 | reversion | +0.835 | 0.016 | 3.9 | 1.00 | stable | yes |
| vr|asia|120 | reversion | +0.840 | 0.016 | 3.9 | 0.93 | stable | yes |
| hurst|asia | reversion | +0.493 | 0.016 | 3.9 | 0.86 | stable | yes |
| vr|london|5 | reversion | +0.877 | 0.016 | 4.4 | 1.00 | stable | yes |
| vr|london|15 | reversion | +0.839 | 0.016 | 4.4 | 1.00 | stable | yes |
| vr|london|30 | reversion | +0.834 | 0.016 | 4.4 | 1.00 | stable | yes |
| vr|london|60 | reversion | +0.836 | 0.016 | 4.4 | 0.93 | stable | yes |
| vr|london|120 | reversion | +0.843 | 0.016 | 4.4 | 0.86 | stable | yes |
| hurst|london | reversion | +0.494 | 0.049 | 4.4 | 0.57 | unstable | yes |
| vr|pre|5 | reversion | +0.905 | 0.016 | 5.5 | 0.93 | stable | yes |
| vr|pre|15 | reversion | +0.876 | 0.016 | 5.5 | 0.86 | stable | yes |
| hurst|pre | reversion | +0.485 | 0.016 | 5.5 | 0.71 | stable | yes |
| vr|nyam|5 | reversion | +0.874 | 0.016 | 6.5 | 1.00 | stable | yes |
| vr|nyam|15 | reversion | +0.840 | 0.016 | 6.5 | 1.00 | stable | yes |
| vr|nyam|30 | reversion | +0.840 | 0.016 | 6.5 | 0.86 | stable | yes |
| hurst|nyam | reversion | +0.488 | 0.016 | 6.5 | 0.79 | stable | yes |
| vr|nypm|5 | reversion | +0.684 | 0.016 | 4.7 | 1.00 | stable | yes |
| vr|nypm|15 | reversion | +0.618 | 0.016 | 4.7 | 0.93 | stable | yes |
| vr|nypm|30 | reversion | +0.595 | 0.016 | 4.7 | 1.00 | stable | yes |
| vr|nypm|60 | reversion | +0.596 | 0.016 | 4.7 | 0.86 | stable | yes |
| hurst|nypm | reversion | +0.471 | 0.016 | 4.7 | 0.71 | stable | yes |
| vr|close|5 | reversion | +0.675 | 0.016 | 3.5 | 1.00 | stable | yes |
| vr|close|15 | reversion | +0.590 | 0.016 | 3.5 | 1.00 | stable | yes |
| vr|close|30 | reversion | +0.583 | 0.016 | 3.5 | 0.93 | stable | yes |
| hurst|close | reversion | +0.457 | 0.016 | 3.5 | 0.86 | stable | yes |
| vr|rth|5 | reversion | +0.775 | 0.016 | 6.5 | 1.00 | stable | yes |
| vr|rth|15 | reversion | +0.719 | 0.016 | 6.5 | 1.00 | stable | yes |
| vr|rth|30 | reversion | +0.704 | 0.016 | 6.5 | 1.00 | stable | yes |
| vr|rth|60 | reversion | +0.681 | 0.016 | 6.5 | 1.00 | stable | yes |
| vr|rth|120 | reversion | +0.657 | 0.016 | 6.5 | 1.00 | stable | yes |
| hurst|rth | reversion | +0.475 | 0.016 | 6.5 | 0.86 | stable | yes |
| rx|RN|london | level-break | +0.480 | 0.049 | 4.4 | 0.71 | stable | yes |

### 12. CHAR-C complements
Data note: bars are the CHAR-C bad-print-repaired copy (cc_clean.py, MORNING_FLAGS 2026-11-05); for 6E/6J the 2013-2015 years carried ~2% bars with highs/lows/closes >10 sigma outside the neighbours, which would have driven VR/Hurst and level-touch rates (raw 6E NY-PM VR(30) .16 -> .64 after repair).

Gross edge per signal (CHAR-C own cross-check cc_ac.py: past-h move >= 1 sigma, mean of sign x next-h move in $/lot, repaired bars, 15-minute decision points; shuffled-day family null on 153+ cells) against the round-trip cost $25.00:

| session | 5 min: edge $ (x cost) | 15 min: edge $ (x cost) | 30 min: edge $ (x cost) | 60 min: edge $ (x cost) |
|--|--|--|--|--|
| asia | -1.7 (0.07x) | -0.7 (0.03x) | -0.4 (0.02x) | -1.0 (0.04x) |
| london | -1.4 (0.06x) | -0.9 (0.03x) | -0.3 (0.01x) | +1.4 (0.06x) |
| pre | -0.7 (0.03x) | -0.4 (0.02x) | -2.1 (0.09x) | +1.8 (0.07x) |
| nyam | -3.0 (0.12x) | -0.6 (0.02x) | -2.4 (0.10x) | +1.2 (0.05x) |
| nypm | -9.0 (0.36x) | -2.7 (0.11x) | -1.9 (0.08x) | +0.6 (0.02x) |
| close | -4.7 (0.19x) | -5.8 (0.23x) | -1.9 (0.07x) | -4.7 (0.19x) |

Time-of-day drift map (cc_tod.py, signed 30-minute returns by ET slot, sign-flip-by-day null, 2000 worlds, family = slots): wd 16:00: -0.30 bp, -3.2 $/lot (0.14x cost), t -3.1, p_family 0.087, same sign 79% of 14 years; wd 06:30: -0.32 bp, -3.6 $/lot (0.15x cost), t -2.9, p_family 0.152, same sign 86% of 14 years; wd 22:00: +0.43 bp, +4.8 $/lot (0.20x cost), t 2.6, p_family 0.344, same sign 64% of 14 years; wd 15:30: -0.25 bp, -2.0 $/lot (0.09x cost), t -2.6, p_family 0.380, same sign 64% of 14 years.


## MBT - character map (CHAR-C, 2026-11-05T23:31Z)
Base: MBT CME front-month (.v.0) 1-min bars from 2022-01 to 2026-10, percent frame (multiplicative roll-adjusted), 1-min approximation (no tick path), 607 usable label days; ET clock, sessions asia 18:00-02:00 / london 02:00-08:30 / pre 08:30-09:30 / nyam 09:30-12:00 / nypm 12:00-15:00 / close 15:00-16:55. Nulls: within-year shuffled-day (AC B=300; structure B=100 worlds; levels recomputed on the shuffled path; round numbers 60 random grid phases); p_family = Westfall-Young max-|z| over the block (AC family 153 cells, structure family 92 cells). `**` p_family<=.05, `*` <=.10. Prereg sha256 980bedf6bad3f1669de9efb93831fa4622d88577c892d9359b7f57ba93c9dbcf. Descriptive only: no PASS, nothing live.

### Plain paragraph (CHAR-C)
MBT (micro bitcoin, $0.1 per point; BTC standard $5 per point as the cap-breach cross-check) trades around the clock and reverts at 1-5 minutes in five of six sessions and not in NY-AM: the 5-minute lag correlation is -0.050 (pre-NY hour), -0.038 (London), -0.029 (NY-PM), -0.020 (Asia), -0.044 (close) with p_family .003 (BTC: -0.045 London, -0.061 pre, -0.057 close, -0.031 NY-PM, -0.024 Asia, p_family .003), NY-AM -0.004 (p_family 1.0), and only the pre-NY hour reaches 15 minutes (-0.068, p_family .066, not under .05); 30-120 minutes show no MBT row under p_family .05 (largest |corr| .086, pre-NY hour at 30 minutes, p_family .997) and a mild unconfirmed 60-minute momentum in the NY sessions in BTC (+0.08, p_family .16-.55). Variance ratios are .83-.93 outside NY-AM and 1.00 inside it (Hurst .45-.51); trend days 44% (null 46%), range days 24% (null 26%), only the two-sided IB extension is rarer than the null (24% vs 30%). No level (prior-day, overnight, IB, VWAP, round thousands) beats its family null in MBT; BTC adds only a London excursion fade (continuation 40% vs 46%). Weekends: 36 Saturday / Sunday-evening block-by-horizon cells show nothing (smallest p_family .995 BTC, .90 MBT) and no 30-minute drift slot (weekday or weekend) passes (best |t| 2.2-2.4 vs a null 95th percentile of 3.3); Sunday-open gap, funding-time, 09:30 sympathy and Sunday range books are ZL-1's (T2_NATIVE) and the earlier DIS-C. Edge per signal is tiny: fading a 1-sigma move earns $0.1-1.3 per MBT signal at 5-30 minutes against the $4.28 round trip (0.01-0.31 x) and $0.5-60 per BTC signal against $129.8 (0.00-0.46 x). Room: MBT one ATR5 is 2.6-5.2 x cost and 3 x ATR5 7.8-15.4 x (BTC 3.0-6.2 x); the real constraint is liquidity: the 1.7% cap is 1.0-1.05 MBT contracts per 5 minutes in London / Asia, 2.8-3.0 pre / NY-PM / close and 5.8 in NY-AM, while a $1,200 stop needs 18-36 lots, so realised risk per trade is $40-350 and weekly P&L is of the order of tens of dollars; BTC standard is below one contract per 5 minutes everywhere (0.12-0.88) and cannot be traded inside the cap. Versus NQ: +0.47 to +0.52 at 1-30 minutes in NY, 0.22-0.36 in Asia / London, NQ leads by one minute (+0.02 to +0.05 MBT, +0.05 to +0.08 BTC, same sign every year. The book that fits is the 5-minute excursion fade in Asia / London / pre / NY-PM / close at 1-5 lots; it does not clear (DS3_FIND.md).

### Generated summary (page.py of CHAR-A, same numbers)
At 1 minute every session has negative autocorrelation (-0.043 to -0.011; bid-ask bounce / last-print noise, not a tradable edge by itself). asia: reverts at 5 min (-0.020). london: reverts at 5 min (-0.038). pre: reverts at 5 min (-0.050). nypm: reverts at 5 min (-0.029). close: reverts at 5 min (-0.044). Day types (RTH): 44% trend days (efficiency ratio >= .5; shuffled null 46%, p_fam 1.000), 24% range days (<.25; null 26%, p_fam 1.000); the IB (09:30-10:30) is extended on one side only on 73% of days and on both on 24%, and a one-sided extension closes beyond the IB edge 64% of the time (null 68%). RTH variance ratio at 30 min 0.933 (shuffled null 0.998, p_fam 0.016); Hurst 0.493. The RTH range forms 9:30 (38%), 10:00 (26%), 11:00 (13%) of the range increments. No level (prior-day H/L, overnight H/L, IB edge, VWAP +-1/2 sigma, round numbers) beats its shuffled-day family null for bounce vs break-through. Failed-break follow-through beating the null: none. Room (median 3xATR14(5m) $ / round-trip cost $4 per lot): asia 9.4x, london 7.8x, pre 9.5x, nyam 15.4x, nypm 13.9x, close 11.9x (1xATR5 room 5.1x in nyam, 3.1x in asia).

### 1. Autocorrelation of h-min returns (corr(past h, next h), both inside the session), pooled; cell = corr (pre-2023 mean | 2023+ mean) p_family
| session | 1 min | 5 min | 15 min | 30 min | 60 min | 120 min |
|--|--|--|--|--|--|--|
| asia | -0.026 (+0.022|-0.027) p0.003** ys0.75 | -0.020 (+0.023|-0.021) p0.003** ys0.75 | -0.009 (+0.080|-0.010) p1.000 ys0.75 | +0.011 (+0.191|+0.010) p1.000 ys0.75 | +0.001 (+0.193|-0.003) p1.000 ys0.50 | -0.001 (+0.317|-0.010) p1.000 ys0.50 |
| london | -0.030 (+0.025|-0.030) p0.003** ys0.75 | -0.038 (-0.055|-0.036) p0.003** ys1.00 | -0.007 (+0.025|-0.008) p1.000 ys0.75 | -0.006 (+0.007|-0.007) p1.000 ys0.50 | +0.006 (-0.149|+0.009) p1.000 ys0.25 | -0.008 (-0.043|-0.008) p1.000 ys0.75 |
| pre | -0.043 (+0.092|-0.043) p0.003** ys0.75 | -0.050 (+0.172|-0.051) p0.003** ys0.75 | -0.068 (-0.477|-0.061) p0.066* ys0.75 | -0.086 (-0.561|-0.086) p0.997 ys1.00 | - | - |
| nyam | -0.011 (+0.026|-0.012) p0.236 ys0.75 | -0.004 (+0.010|-0.005) p1.000 ys0.50 | +0.036 (-0.131|+0.036) p0.439 ys0.75 | +0.020 (-0.209|+0.020) p1.000 ys0.50 | +0.049 (+0.037|+0.048) p1.000 ys1.00 | - |
| nypm | -0.034 (-0.030|-0.033) p0.003** ys1.00 | -0.029 (-0.002|-0.031) p0.003** ys1.00 | -0.024 (+0.106|-0.026) p0.990 ys0.75 | -0.029 (+0.078|-0.033) p1.000 ys0.50 | -0.021 (+0.678|-0.042) p1.000 ys0.25 | - |
| close | -0.034 (+0.078|-0.035) p0.003** ys0.75 | -0.044 (+0.125|-0.045) p0.003** ys0.75 | -0.020 (-0.345|-0.019) p1.000 ys1.00 | -0.048 (-0.353|-0.046) p0.940 ys1.00 | - | - |

Hour cells (h >= 5) beating the family null, top 14 by |z| (hour = ET hour of the decision bar):
| h | session | hour ET | corr | z | p_family | year sign share | pre-2023 | 2023+ |
|--|--|--|--|--|--|--|--|--|
| 5 | asia | 00 | -0.062 | -6.7 | 0.003 | 1.00 | -0.182 | -0.062 |
| 5 | close | 16 | -0.063 | -6.5 | 0.003 | 0.75 | +0.191 | -0.069 |
| 5 | london | 08 | -0.082 | -5.6 | 0.003 | 0.75 | +0.052 | -0.086 |
| 5 | london | 07 | -0.048 | -5.2 | 0.003 | 1.00 | -0.117 | -0.051 |
| 5 | london | 05 | -0.049 | -5.0 | 0.003 | 1.00 | -0.194 | -0.048 |
| 5 | london | 06 | -0.044 | -4.9 | 0.003 | 0.75 | +0.047 | -0.043 |
| 5 | pre | 09 | -0.071 | -4.8 | 0.003 | 1.00 | -0.458 | -0.065 |
| 15 | london | 05 | -0.071 | -4.8 | 0.003 | 1.00 | -0.459 | -0.068 |
| 15 | london | 07 | -0.067 | -4.5 | 0.007 | 1.00 | -0.062 | -0.068 |
| 15 | pre | 08 | -0.101 | -4.0 | 0.020 | 0.75 | -0.604 | -0.092 |

### 2. Variance ratio VR(q) and Hurst (1.0 = random walk; <1 reverting; edge-bias corrected), cell = value (null) p_family
| session | VR5 | VR15 | VR30 | VR60 | VR120 | Hurst |
|--|--|--|--|--|--|--|
| asia | 0.930 (1.001) p0.016** | 0.902 (0.999) p0.016** | 0.890 (0.997) p0.016** | 0.897 (0.998) p0.016** | 0.901 (0.998) p0.016** | 0.495 (0.499) p1.000 |
| london | 0.927 (1.000) p0.016** | 0.876 (0.999) p0.016** | 0.867 (0.999) p0.016** | 0.870 (0.998) p0.016** | 0.879 (0.997) p0.016** | 0.492 (0.499) p1.000 |
| pre | 0.920 (0.999) p0.016** | 0.829 (0.998) p0.016** | - | - | - | 0.453 (0.499) p0.016** |
| nyam | 0.995 (1.000) p1.000 | 0.997 (0.998) p1.000 | 1.022 (0.997) p1.000 | - | - | 0.507 (0.499) p1.000 |
| nypm | 0.925 (0.999) p0.016** | 0.883 (0.999) p0.016** | 0.856 (1.001) p0.016** | 0.841 (1.000) p0.016** | - | 0.480 (0.500) p0.066* |
| close | 0.926 (0.999) p0.016** | 0.856 (1.003) p0.016** | 0.842 (1.007) p0.016** | - | - | 0.473 (0.502) p0.016** |
| rth | 0.963 (1.000) p0.016** | 0.940 (0.998) p0.016** | 0.933 (0.998) p0.016** | 0.922 (0.998) p0.016** | 0.921 (0.997) p0.180 | 0.493 (0.500) p1.000 |

### 3. Day types (ex-post labels of the RTH day)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| day|trend | 0.443 | 607 | 0.464 | -1.0 | 1.000 | 0.50 | 1.000 | 0.438 | REGIME(2023+ only) |
| day|range | 0.244 | 607 | 0.255 | -0.7 | 1.000 | 0.50 | 0.000 | 0.245 | unstable |
| day|er | 0.453 | 607 | 0.465 | -1.1 | 1.000 | 0.50 | 0.676 | 0.451 | REGIME(2023+ only) |
| day|ib_none | 0.026 | 607 | 0.016 | +2.3 | 0.836 | 0.75 | 0.333 | 0.027 | stable |
| day|ib_one | 0.731 | 607 | 0.680 | +2.9 | 0.180 | 0.75 | 0.333 | 0.732 | REGIME(2023+ only) |
| day|ib_both | 0.242 | 607 | 0.304 | -3.6 | 0.016** | 0.75 | 0.333 | 0.242 | REGIME(2023+ only) |
| day|ib_one_closebeyond | 0.640 | 444 | 0.677 | -1.4 | 1.000 | 0.50 | 1.000 | 0.631 | REGIME(2023+ only) |

### 4. 1A -> 2A continuation vs give-back-half from the session open (A = 3 x ATR14(5m)); value = P(continue | resolved)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| cont|asia | 0.377 | 554 | 0.430 | -3.1 | 0.082* | 0.75 | 0.667 | 0.374 | REGIME(2023+ only) |
| cont|london | 0.389 | 581 | 0.376 | +0.7 | 1.000 | 0.50 | 0.000 | 0.393 | REGIME(2023+ only) |
| cont|pre | 0.332 | 274 | 0.338 | -0.2 | 1.000 | 0.25 | 1.000 | 0.334 | REGIME(2023+ only) |
| cont|nyam | 0.329 | 583 | 0.356 | -1.3 | 1.000 | 1.00 | 0.000 | 0.332 | stable |
| cont|nypm | 0.294 | 272 | 0.300 | -0.2 | 1.000 | 0.25 | 1.000 | 0.275 | REGIME(2023+ only) |
| cont|close | 0.321 | 193 | 0.297 | +0.8 | 1.000 | 1.00 | 0.500 | 0.326 | stable |
| cont|rth | 0.338 | 601 | 0.358 | -1.0 | 1.000 | 1.00 | 0.000 | 0.341 | stable |

### 5. Gap fill by size bucket (b0 .05-.10, b1 .10-.25, b2 .25-.50, b3 >.50 of the 20-day mean RTH range); day = filled during RTH, h1 = within 60 min
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| gap|b0|day | 0.938 | 32 | 0.896 | +0.7 | 1.000 | 1.00 | 1.000 | 0.949 | stable |
| gap|b0|h1 | 0.812 | 32 | 0.811 | +0.0 | 1.000 | 0.75 | 1.000 | 0.846 | stable |
| gap|b1|day | 0.770 | 87 | 0.779 | -0.2 | 1.000 | 0.50 | 1.000 | 0.776 | REGIME(2023+ only) |
| gap|b1|h1 | 0.575 | 87 | 0.600 | -0.5 | 1.000 | 0.50 | 0.000 | 0.580 | unstable |
| gap|b2|day | 0.485 | 163 | 0.557 | -1.6 | 1.000 | 0.75 | nan | 0.480 | short history |
| gap|b2|h1 | 0.233 | 163 | 0.274 | -1.1 | 1.000 | 0.50 | nan | 0.233 | short history |
| gap|b3|day | 0.187 | 289 | 0.196 | -0.4 | 1.000 | 0.75 | 0.000 | 0.187 | stable |
| gap|b3|h1 | 0.031 | 289 | 0.035 | -0.3 | 1.000 | 0.75 | 0.000 | 0.032 | stable |

### 6. Level reaction: first touch -> bounce (0.5A reverse) vs break-through (0.5A beyond) within 60 min; value = P(bounce)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| rx|PD|asia | 0.377 | 401 | 0.430 | -2.3 | 0.770 | 1.00 | 0.333 | 0.376 | stable |
| rx|PD|london | 0.426 | 282 | 0.460 | -1.2 | 1.000 | 0.75 | 0.000 | 0.428 | stable |
| rx|PD|pre | 0.467 | 137 | 0.474 | -0.2 | 1.000 | 0.50 | 1.000 | 0.494 | unstable |
| rx|PD|nyam | 0.446 | 325 | 0.484 | -1.3 | 1.000 | 0.75 | 0.000 | 0.451 | stable |
| rx|PD|nypm | 0.459 | 183 | 0.476 | -0.6 | 1.000 | 0.25 | nan | 0.465 | short history |
| rx|PD|close | 0.440 | 109 | 0.474 | -0.8 | 1.000 | 0.75 | 0.000 | 0.449 | stable |
| rx|ON|nyam | 0.447 | 465 | 0.484 | -1.5 | 1.000 | 0.75 | 1.000 | 0.449 | REGIME(2023+ only) |
| rx|ON|nypm | 0.428 | 264 | 0.481 | -1.7 | 1.000 | 0.75 | 0.000 | 0.455 | stable |
| rx|ON|close | 0.557 | 158 | 0.484 | +1.7 | 1.000 | 0.75 | 1.000 | 0.557 | stable |
| rx|IB|nyam | 0.443 | 517 | 0.485 | -2.0 | 0.984 | 0.75 | 0.000 | 0.448 | stable |
| rx|IB|nypm | 0.490 | 386 | 0.480 | +0.4 | 1.000 | 0.50 | 1.000 | 0.495 | unstable |
| rx|IB|close | 0.493 | 207 | 0.478 | +0.5 | 1.000 | 0.25 | 0.000 | 0.498 | REGIME(2023+ only) |
| rx|VW1|nyam | 0.472 | 917 | 0.483 | -0.7 | 1.000 | 0.75 | 0.200 | 0.475 | stable |
| rx|VW1|nypm | 0.483 | 613 | 0.485 | -0.1 | 1.000 | 0.50 | 0.000 | 0.486 | unstable |
| rx|VW1|close | 0.522 | 385 | 0.481 | +1.8 | 1.000 | 0.75 | 0.333 | 0.520 | REGIME(2023+ only) |
| rx|VW2|nyam | 0.468 | 667 | 0.491 | -1.3 | 1.000 | 1.00 | 0.250 | 0.470 | stable |
| rx|VW2|nypm | 0.531 | 356 | 0.485 | +2.0 | 0.984 | 1.00 | 1.000 | 0.534 | stable |
| rx|VW2|close | 0.580 | 176 | 0.477 | +3.2 | 0.082* | 1.00 | 1.000 | 0.582 | stable |
| rx|RN|asia | 0.468 | 13385 | 0.467 | +0.2 | 1.000 | 0.50 | 0.378 | 0.468 | REGIME(2023+ only) |
| rx|RN|london | 0.475 | 10424 | 0.469 | +1.6 | 1.000 | 0.50 | 0.429 | 0.474 | REGIME(2023+ only) |
| rx|RN|pre | 0.482 | 2882 | 0.489 | -1.1 | 1.000 | 0.75 | 0.368 | 0.484 | stable |
| rx|RN|nyam | 0.487 | 9858 | 0.481 | +1.3 | 1.000 | 0.75 | 0.485 | 0.488 | stable |
| rx|RN|nypm | 0.488 | 7427 | 0.485 | +0.6 | 1.000 | 0.75 | 0.562 | 0.485 | stable |
| rx|RN|close | 0.470 | 3312 | 0.485 | -1.6 | 1.000 | 0.50 | 0.500 | 0.478 | REGIME(2023+ only) |

### 7. Failed break (close .25A beyond, back inside within 10 bars): fade follow-through P(0.5A back before 0.5A out)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| fb|PD|asia | 0.518 | 226 | 0.495 | +0.8 | 1.000 | 0.25 | 0.000 | 0.516 | REGIME(2023+ only) |
| fb|PD|london | 0.521 | 194 | 0.497 | +0.8 | 1.000 | 0.50 | 0.000 | 0.521 | REGIME(2023+ only) |
| fb|PD|pre | 0.450 | 80 | 0.498 | -1.0 | 1.000 | 0.75 | 0.000 | 0.473 | stable |
| fb|PD|nyam | 0.519 | 208 | 0.503 | +0.5 | 1.000 | 0.50 | 0.000 | 0.523 | REGIME(2023+ only) |
| fb|PD|nypm | 0.500 | 122 | 0.495 | +0.1 | 1.000 | 0.25 | nan | 0.506 | short history |
| fb|PD|close | 0.379 | 66 | 0.488 | -2.2 | 0.852 | 1.00 | 0.000 | 0.390 | stable |
| fb|ON|nyam | 0.521 | 238 | 0.498 | +0.7 | 1.000 | 0.75 | 1.000 | 0.509 | stable |
| fb|ON|nypm | 0.428 | 166 | 0.498 | -1.5 | 1.000 | 0.75 | nan | 0.434 | short history |
| fb|ON|close | 0.456 | 90 | 0.508 | -1.0 | 1.000 | 0.25 | 1.000 | 0.473 | REGIME(2023+ only) |
| fb|IB|nyam | 0.427 | 164 | 0.504 | -2.4 | 0.689 | 0.75 | 1.000 | 0.424 | REGIME(2023+ only) |
| fb|IB|nypm | 0.490 | 243 | 0.501 | -0.4 | 1.000 | 0.50 | nan | 0.490 | short history |
| fb|IB|close | 0.402 | 127 | 0.503 | -2.9 | 0.131 | 1.00 | 0.000 | 0.404 | stable |

### 8. Where the range forms
RTH range increments by bin: 9:30 37.7%, 10:00 25.9%, 11:00 12.5%, 12:00 7.3%, 13:00 6.0%, 14:00 5.5%, 15:00 5.0%
Label-day range increments by ET hour (percent of the day): 00h 2.7, 01h 2.7, 02h 2.7, 03h 3.1, 04h 3.2, 05h 2.2, 06h 1.9, 07h 2.2, 08h 3.7, 09h 6.8, 10h 6.9, 11h 4.9, 12h 3.1, 13h 2.7, 14h 2.7, 15h 2.5, 16h 1.4, 18h 14.6, 19h 7.4, 20h 7.6, 21h 6.3, 22h 4.8, 23h 3.7

### 9. Room and liquidity (all years, raw-frame $, 1 lot)
| session | ATR14(5m) $ | A=3xATR5 $ | RT cost $ | room(1 ATR5) | room(A) | median 5-min vol | 1.7% cap (contracts/5min) | lots for $1,200 at 3xATR5 stop |
|--|--|--|--|--|--|--|--|--|
| asia | 13 | 40 | 4 | 3.14 | 9.42 | 62 | 1.1 | 29.8 |
| london | 11 | 33 | 4 | 2.59 | 7.78 | 58 | 1.0 | 36.1 |
| pre | 14 | 41 | 4 | 3.18 | 9.54 | 164 | 2.8 | 29.4 |
| nyam | 22 | 66 | 4 | 5.15 | 15.44 | 342 | 5.8 | 18.2 |
| nypm | 20 | 59 | 4 | 4.62 | 13.86 | 174 | 3.0 | 20.2 |
| close | 17 | 51 | 4 | 3.95 | 11.85 | 168 | 2.9 | 23.7 |

room(A) by year: asia: 2022:7.8 2023:5.1 2024:8.7 2025:11.4 2026:8.2; london: 2022:6.7 2023:4.2 2024:7.1 2025:9.2 2026:7.2; pre: 2022:8.6 2023:4.8 2024:9.4 2025:11.1 2026:8.6; nyam: 2022:11.5 2023:7.5 2024:14.6 2025:18.6 2026:14.2; nypm: 2022:9.8 2023:7.0 2024:13.2 2025:16.6 2026:12.2; close: 2022:9.8 2023:6.0 2024:11.8 2025:14.8 2026:9.6

### 10. Versus NQ
Contemporaneous correlation of h-min returns (normalised): asia: 1m 0.22 5m 0.28 15m 0.31 30m 0.32 60m 0.34; london: 1m 0.25 5m 0.30 15m 0.34 30m 0.36 60m 0.36; pre: 1m 0.33 5m 0.40 15m 0.41; nyam: 1m 0.47 5m 0.50 15m 0.50 30m 0.52; nypm: 1m 0.44 5m 0.48 15m 0.51 30m 0.51; close: 1m 0.32 5m 0.36 15m 0.35

Lead/lag (1-15 min, family 180 cells; corr of 1-min normalised returns): cells beating the family null (top 10 by |z|; "NQ->X" = NQ leads MBT):
| direction | session | lag min | corr | z | p_family | year sign share |
|--|--|--|--|--|--|--|
| NQ->MBT | london | 1 | +0.0488 | +25.4 | 0.010 | 1.00 |
| NQ->MBT | asia | 1 | +0.0421 | +23.9 | 0.010 | 1.00 |
| NQ->MBT | nypm | 1 | +0.0231 | +7.7 | 0.010 | 1.00 |
| NQ->MBT | nyam | 1 | +0.0262 | +7.1 | 0.010 | 1.00 |
| NQ->MBT | close | 1 | +0.0225 | +5.8 | 0.010 | 1.00 |
| NQ->MBT | pre | 1 | +0.0284 | +4.7 | 0.010 | 1.00 |
| NQ->MBT | asia | 4 | +0.0083 | +4.5 | 0.010 | 1.00 |
| MBT->NQ | close | 1 | +0.0153 | +4.4 | 0.010 | 1.00 |
| MBT->NQ | asia | 1 | +0.0079 | +3.9 | 0.020 | 1.00 |
| MBT->NQ | pre | 6 | +0.0225 | +3.9 | 0.020 | 1.00 |

### 11. Map rows that become book candidates under the FROZEN rule (p_family <= .05 AND room_A(session) > 2.0)
| map row | direction | stat | p_family | room_A | year sign share | stability | 1.7% cap >= 1 contract/5min in session |
|--|--|--|--|--|--|--|--|
| AC|asia|5m | reversion | -0.020 | 0.003 | 9.4 | 0.75 |  | yes |
| AC|london|5m | reversion | -0.038 | 0.003 | 7.8 | 1.00 |  | NO (illiquid) |
| AC|pre|5m | reversion | -0.050 | 0.003 | 9.5 | 0.75 |  | yes |
| AC|nypm|5m | reversion | -0.029 | 0.003 | 13.9 | 1.00 |  | yes |
| AC|close|5m | reversion | -0.044 | 0.003 | 11.9 | 0.75 |  | yes |
| vr|asia|5 | reversion | +0.930 | 0.016 | 9.4 | 1.00 | stable | yes |
| vr|asia|15 | reversion | +0.902 | 0.016 | 9.4 | 1.00 | stable | yes |
| vr|asia|30 | reversion | +0.890 | 0.016 | 9.4 | 0.75 | REGIME(2023+ only) | yes |
| vr|asia|60 | reversion | +0.897 | 0.016 | 9.4 | 0.75 | REGIME(2023+ only) | yes |
| vr|asia|120 | reversion | +0.901 | 0.016 | 9.4 | 0.75 | REGIME(2023+ only) | yes |
| vr|london|5 | reversion | +0.927 | 0.016 | 7.8 | 1.00 | stable | NO (illiquid) |
| vr|london|15 | reversion | +0.876 | 0.016 | 7.8 | 1.00 | stable | NO (illiquid) |
| vr|london|30 | reversion | +0.867 | 0.016 | 7.8 | 1.00 | stable | NO (illiquid) |
| vr|london|60 | reversion | +0.870 | 0.016 | 7.8 | 1.00 | stable | NO (illiquid) |
| vr|london|120 | reversion | +0.879 | 0.016 | 7.8 | 1.00 | stable | NO (illiquid) |
| vr|pre|5 | reversion | +0.920 | 0.016 | 9.5 | 0.75 | REGIME(2023+ only) | yes |
| vr|pre|15 | reversion | +0.829 | 0.016 | 9.5 | 0.75 | REGIME(2023+ only) | yes |
| hurst|pre | reversion | +0.453 | 0.016 | 9.5 | 0.75 | REGIME(2023+ only) | yes |
| vr|nypm|5 | reversion | +0.925 | 0.016 | 13.9 | 1.00 | stable | yes |
| vr|nypm|15 | reversion | +0.883 | 0.016 | 13.9 | 0.75 | REGIME(2023+ only) | yes |
| vr|nypm|30 | reversion | +0.856 | 0.016 | 13.9 | 0.75 | REGIME(2023+ only) | yes |
| vr|nypm|60 | reversion | +0.841 | 0.016 | 13.9 | 0.75 | REGIME(2023+ only) | yes |
| vr|close|5 | reversion | +0.926 | 0.016 | 11.9 | 0.75 | REGIME(2023+ only) | yes |
| vr|close|15 | reversion | +0.856 | 0.016 | 11.9 | 0.75 | REGIME(2023+ only) | yes |
| vr|close|30 | reversion | +0.842 | 0.016 | 11.9 | 1.00 | stable | yes |
| hurst|close | reversion | +0.473 | 0.016 | 11.9 | 1.00 | stable | yes |
| vr|rth|5 | reversion | +0.963 | 0.016 | 15.4 | 1.00 | stable | yes |
| vr|rth|15 | reversion | +0.940 | 0.016 | 15.4 | 0.75 | REGIME(2023+ only) | yes |
| vr|rth|30 | reversion | +0.933 | 0.016 | 15.4 | 0.75 | REGIME(2023+ only) | yes |
| vr|rth|60 | reversion | +0.922 | 0.016 | 15.4 | 1.00 | stable | yes |

### 12. CHAR-C complements
Data note: bars are the CHAR-C bad-print-repaired copy (cc_clean.py, MORNING_FLAGS 2026-11-05); for 6E/6J the 2013-2015 years carried ~2% bars with highs/lows/closes >10 sigma outside the neighbours, which would have driven VR/Hurst and level-touch rates (raw 6E NY-PM VR(30) .16 -> .64 after repair).

Gross edge per signal (CHAR-C own cross-check cc_ac.py: past-h move >= 1 sigma, mean of sign x next-h move in $/lot, repaired bars, 15-minute decision points; shuffled-day family null on 153+ cells) against the round-trip cost $4.28:

| session | 5 min: edge $ (x cost) | 15 min: edge $ (x cost) | 30 min: edge $ (x cost) | 60 min: edge $ (x cost) |
|--|--|--|--|--|
| asia | -0.5 (0.12x) | -0.8 (0.18x) | +0.2 (0.04x) | -0.4 (0.10x) |
| london | -0.6 (0.14x) | -0.1 (0.02x) | +0.3 (0.07x) | +0.7 (0.16x) |
| pre | -0.9 (0.20x) | -0.9 (0.21x) | -0.9 (0.22x) | -1.7 (0.39x) |
| nyam | -1.3 (0.31x) | -0.3 (0.06x) | +0.6 (0.15x) | +2.2 (0.51x) |
| nypm | -0.8 (0.20x) | -1.1 (0.27x) | -1.0 (0.23x) | +0.3 (0.08x) |
| close | +0.1 (0.01x) | +0.2 (0.04x) | -0.2 (0.06x) | -2.5 (0.58x) |

Time-of-day drift map (cc_tod.py, signed 30-minute returns by ET slot, sign-flip-by-day null, 2000 worlds, family = slots): wd 08:30: -3.32 bp, -2.1 $/lot (0.49x cost), t -2.2, p_family 0.748, same sign 100% of 5 years; wd 04:00: +2.42 bp, +1.7 $/lot (0.41x cost), t 2.2, p_family 0.792, same sign 100% of 5 years; wd 16:00: +2.43 bp, +2.0 $/lot (0.46x cost), t 1.9, p_family 0.945, same sign 100% of 5 years; we 19:30: -4.24 bp, -2.7 $/lot (0.64x cost), t -1.7, p_family 0.997, same sign 80% of 5 years.


## BTC - character map (CHAR-C, 2026-11-05T23:31Z)
Base: BTC CME front-month (.v.0) 1-min bars from 2022-01 to 2026-10, percent frame (multiplicative roll-adjusted), 1-min approximation (no tick path), 974 usable label days; ET clock, sessions asia 18:00-02:00 / london 02:00-08:30 / pre 08:30-09:30 / nyam 09:30-12:00 / nypm 12:00-15:00 / close 15:00-16:55. Nulls: within-year shuffled-day (AC B=300; structure B=100 worlds; levels recomputed on the shuffled path; round numbers 60 random grid phases); p_family = Westfall-Young max-|z| over the block (AC family 153 cells, structure family 92 cells). `**` p_family<=.05, `*` <=.10. Prereg sha256 980bedf6bad3f1669de9efb93831fa4622d88577c892d9359b7f57ba93c9dbcf. Descriptive only: no PASS, nothing live.

### Plain paragraph (CHAR-C)
BTC standard (5 BTC, $5 per point; CME) is the CAP-BREACH cross-check of MBT and has the same character: reversion at 1-5 minutes in Asia, London, pre-NY, NY-PM and the close (5-minute -0.024 / -0.045 / -0.061 / -0.031 / -0.057, p_family .003; NY-AM -0.013, p_family .87), nothing at 15 minutes or longer that survives the family correction (a mild +0.08 60-minute momentum in NY-PM and NY-AM, p_family .16 and .55), VR .83-.97, no weekend structure (smallest p_family .995 over 36 cells), no time-of-day drift (best |t| 2.4 vs null 3.3). The $129.8 round trip is 0.16-0.33 of one ATR5 (ATR5 $392-799, room 3.0-6.2x) and the cap is 0.12-0.88 contracts per 5 minutes in every session (one lot exceeds it by 1.1-8x), so BTC is reported, never a lead; the usable crypto leg is MBT (page above). Details and numbers: the MBT paragraph; generated tables below are the BTC series.

### Generated summary (page.py of CHAR-A, same numbers)
At 1 minute every session has negative autocorrelation (-0.039 to -0.004; bid-ask bounce / last-print noise, not a tradable edge by itself). asia: reverts at 5/15 min (-0.024, -0.023). london: reverts at 5 min (-0.045). pre: reverts at 5 min (-0.061). nypm: reverts at 5 min (-0.031). close: reverts at 5 min (-0.057). Day types (RTH): 44% trend days (efficiency ratio >= .5; shuffled null 47%, p_fam 1.000), 26% range days (<.25; null 25%, p_fam 1.000); the IB (09:30-10:30) is extended on one side only on 72% of days and on both on 25%, and a one-sided extension closes beyond the IB edge 67% of the time (null 69%). RTH variance ratio at 30 min 0.933 (shuffled null 0.998, p_fam 0.016); Hurst 0.504. The RTH range forms 9:30 (36%), 10:00 (25%), 11:00 (13%) of the range increments. No level (prior-day H/L, overnight H/L, IB edge, VWAP +-1/2 sigma, round numbers) beats its shuffled-day family null for bounce vs break-through. Failed-break follow-through beating the null: none. Room (median 3xATR14(5m) $ / round-trip cost $130 per lot): asia 10.3x, london 9.1x, pre 11.4x, nyam 18.5x, nypm 16.5x, close 14.1x (1xATR5 room 6.2x in nyam, 3.4x in asia).

### 1. Autocorrelation of h-min returns (corr(past h, next h), both inside the session), pooled; cell = corr (pre-2023 mean | 2023+ mean) p_family
| session | 1 min | 5 min | 15 min | 30 min | 60 min | 120 min |
|--|--|--|--|--|--|--|
| asia | -0.005 (+0.006|-0.007) p0.631 ys0.60 | -0.024 (-0.035|-0.022) p0.003** ys1.00 | -0.023 (-0.008|-0.027) p0.003** ys1.00 | -0.003 (+0.053|-0.018) p1.000 ys0.60 | -0.004 (+0.058|-0.023) p1.000 ys0.60 | +0.005 (+0.059|-0.014) p1.000 ys0.60 |
| london | -0.004 (+0.013|-0.009) p0.611 ys0.60 | -0.045 (-0.055|-0.041) p0.003** ys1.00 | -0.017 (-0.039|-0.011) p0.209 ys1.00 | -0.013 (-0.032|-0.010) p1.000 ys0.80 | -0.006 (-0.027|-0.001) p1.000 ys0.60 | -0.001 (-0.005|+0.001) p1.000 ys0.60 |
| pre | -0.039 (-0.016|-0.045) p0.003** ys1.00 | -0.061 (-0.054|-0.060) p0.003** ys1.00 | -0.011 (+0.083|-0.040) p1.000 ys0.40 | -0.058 (+0.021|-0.091) p0.997 ys0.80 | - | - |
| nyam | -0.009 (-0.006|-0.010) p0.246 ys1.00 | -0.013 (-0.012|-0.014) p0.867 ys0.80 | +0.028 (+0.034|+0.025) p0.492 ys0.80 | +0.040 (+0.073|+0.035) p0.581 ys1.00 | +0.084 (+0.069|+0.090) p0.551 ys1.00 | - |
| nypm | -0.024 (-0.016|-0.025) p0.003** ys1.00 | -0.031 (-0.010|-0.036) p0.003** ys1.00 | -0.012 (+0.026|-0.024) p1.000 ys0.60 | +0.022 (+0.146|-0.015) p1.000 ys0.40 | +0.080 (+0.318|-0.007) p0.156 ys0.80 | - |
| close | -0.017 (-0.014|-0.019) p0.003** ys1.00 | -0.057 (-0.059|-0.056) p0.003** ys1.00 | -0.011 (+0.006|-0.017) p1.000 ys0.60 | -0.015 (+0.062|-0.035) p1.000 ys0.80 | - | - |

Hour cells (h >= 5) beating the family null, top 14 by |z| (hour = ET hour of the decision bar):
| h | session | hour ET | corr | z | p_family | year sign share | pre-2023 | 2023+ |
|--|--|--|--|--|--|--|--|--|
| 5 | london | 07 | -0.086 | -12.1 | 0.003 | 0.80 | -0.153 | -0.064 |
| 5 | close | 16 | -0.080 | -10.5 | 0.003 | 1.00 | -0.037 | -0.092 |
| 5 | asia | 00 | -0.067 | -9.4 | 0.003 | 1.00 | -0.109 | -0.058 |
| 5 | london | 08 | -0.097 | -8.2 | 0.003 | 1.00 | -0.150 | -0.083 |
| 5 | pre | 09 | -0.088 | -7.5 | 0.003 | 1.00 | -0.109 | -0.079 |
| 5 | london | 06 | -0.049 | -7.1 | 0.003 | 1.00 | -0.070 | -0.043 |
| 5 | asia | 18 | -0.049 | -6.6 | 0.003 | 1.00 | -0.073 | -0.042 |
| 15 | london | 07 | -0.080 | -6.6 | 0.003 | 1.00 | -0.096 | -0.070 |
| 60 | london | 07 | -0.174 | -6.5 | 0.003 | 1.00 | -0.236 | -0.156 |
| 5 | london | 05 | -0.048 | -6.3 | 0.003 | 1.00 | -0.066 | -0.043 |
| 5 | close | 15 | -0.040 | -5.1 | 0.003 | 1.00 | -0.075 | -0.029 |
| 5 | nyam | 11 | -0.037 | -5.0 | 0.003 | 1.00 | -0.021 | -0.040 |
| 30 | london | 07 | -0.074 | -4.7 | 0.003 | 1.00 | -0.034 | -0.085 |
| 5 | nypm | 13 | -0.035 | -4.7 | 0.003 | 1.00 | -0.066 | -0.027 |

### 2. Variance ratio VR(q) and Hurst (1.0 = random walk; <1 reverting; edge-bias corrected), cell = value (null) p_family
| session | VR5 | VR15 | VR30 | VR60 | VR120 | Hurst |
|--|--|--|--|--|--|--|
| asia | 0.972 (1.001) p0.016** | 0.936 (1.000) p0.016** | 0.913 (1.000) p0.016** | 0.911 (1.001) p0.016** | 0.918 (1.002) p0.016** | 0.490 (0.500) p0.295 |
| london | 0.956 (1.000) p0.016** | 0.895 (1.000) p0.016** | 0.881 (1.000) p0.016** | 0.877 (1.000) p0.016** | 0.889 (1.000) p0.016** | 0.488 (0.500) p0.148 |
| pre | 0.904 (1.000) p0.016** | 0.840 (0.998) p0.016** | - | - | - | 0.466 (0.499) p0.016** |
| nyam | 0.975 (0.998) p0.016** | 0.962 (0.997) p0.475 | 0.985 (0.996) p1.000 | - | - | 0.502 (0.499) p1.000 |
| nypm | 0.940 (1.000) p0.016** | 0.905 (1.000) p0.016** | 0.893 (1.000) p0.016** | 0.910 (1.004) p0.016** | - | 0.492 (0.501) p1.000 |
| close | 0.927 (1.001) p0.016** | 0.846 (1.002) p0.016** | 0.832 (1.005) p0.016** | - | - | 0.469 (0.501) p0.016** |
| rth | 0.958 (0.999) p0.016** | 0.932 (0.998) p0.016** | 0.933 (0.998) p0.016** | 0.953 (0.999) p0.361 | 0.984 (1.002) p1.000 | 0.504 (0.500) p1.000 |

### 3. Day types (ex-post labels of the RTH day)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| day|trend | 0.441 | 974 | 0.468 | -1.8 | 1.000 | 0.80 | 0.440 | 0.439 | stable |
| day|range | 0.263 | 974 | 0.252 | +0.8 | 1.000 | 0.60 | 0.286 | 0.259 | stable |
| day|er | 0.453 | 974 | 0.469 | -2.0 | 1.000 | 0.80 | 0.453 | 0.451 | stable |
| day|ib_none | 0.029 | 974 | 0.014 | +4.2 | 0.016** | 0.80 | 0.054 | 0.025 | stable |
| day|ib_one | 0.725 | 974 | 0.651 | +4.4 | 0.016** | 1.00 | 0.696 | 0.730 | stable |
| day|ib_both | 0.246 | 974 | 0.335 | -5.3 | 0.016** | 1.00 | 0.250 | 0.245 | stable |
| day|ib_one_closebeyond | 0.671 | 706 | 0.693 | -1.1 | 1.000 | 0.40 | 0.701 | 0.661 | REGIME(2023+ only) |

### 4. 1A -> 2A continuation vs give-back-half from the session open (A = 3 x ATR14(5m)); value = P(continue | resolved)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| cont|asia | 0.457 | 892 | 0.483 | -1.7 | 1.000 | 0.80 | 0.481 | 0.450 | stable |
| cont|london | 0.399 | 955 | 0.458 | -3.5 | 0.033** | 0.80 | 0.417 | 0.393 | stable |
| cont|pre | 0.419 | 480 | 0.426 | -0.4 | 1.000 | 0.60 | 0.459 | 0.412 | REGIME(2023+ only) |
| cont|nyam | 0.357 | 905 | 0.385 | -1.7 | 1.000 | 0.80 | 0.319 | 0.366 | stable |
| cont|nypm | 0.369 | 534 | 0.340 | +1.6 | 1.000 | 0.60 | 0.424 | 0.351 | stable |
| cont|close | 0.351 | 396 | 0.328 | +1.2 | 1.000 | 0.40 | 0.310 | 0.357 | REGIME(2023+ only) |
| cont|rth | 0.360 | 960 | 0.386 | -1.5 | 1.000 | 0.80 | 0.333 | 0.367 | stable |

### 5. Gap fill by size bucket (b0 .05-.10, b1 .10-.25, b2 .25-.50, b3 >.50 of the 20-day mean RTH range); day = filled during RTH, h1 = within 60 min
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| gap|b0|day | 0.833 | 54 | 0.890 | -1.4 | 1.000 | 0.60 | 0.727 | 0.862 | stable |
| gap|b0|h1 | 0.704 | 54 | 0.786 | -1.5 | 1.000 | 0.80 | 0.455 | 0.767 | stable |
| gap|b1|day | 0.772 | 158 | 0.772 | -0.0 | 1.000 | 0.80 | 0.727 | 0.792 | stable |
| gap|b1|h1 | 0.557 | 158 | 0.566 | -0.3 | 1.000 | 0.60 | 0.515 | 0.581 | stable |
| gap|b2|day | 0.480 | 246 | 0.554 | -2.5 | 0.672 | 1.00 | 0.474 | 0.478 | stable |
| gap|b2|h1 | 0.215 | 246 | 0.258 | -1.5 | 1.000 | 1.00 | 0.184 | 0.221 | stable |
| gap|b3|day | 0.185 | 464 | 0.226 | -2.1 | 0.951 | 0.60 | 0.256 | 0.167 | REGIME(2023+ only) |
| gap|b3|h1 | 0.030 | 464 | 0.039 | -1.0 | 1.000 | 0.60 | 0.049 | 0.025 | REGIME(2023+ only) |

### 6. Level reaction: first touch -> bounce (0.5A reverse) vs break-through (0.5A beyond) within 60 min; value = P(bounce)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| rx|PD|asia | 0.318 | 628 | 0.372 | -2.8 | 0.426 | 0.80 | 0.341 | 0.311 | stable |
| rx|PD|london | 0.405 | 442 | 0.410 | -0.2 | 1.000 | 0.40 | 0.488 | 0.384 | REGIME(2023+ only) |
| rx|PD|pre | 0.443 | 210 | 0.450 | -0.2 | 1.000 | 0.40 | 0.381 | 0.476 | unstable |
| rx|PD|nyam | 0.414 | 474 | 0.466 | -2.4 | 0.770 | 1.00 | 0.383 | 0.418 | stable |
| rx|PD|nypm | 0.493 | 304 | 0.468 | +1.1 | 1.000 | 0.80 | 0.474 | 0.501 | stable |
| rx|PD|close | 0.451 | 164 | 0.459 | -0.2 | 1.000 | 0.60 | 0.593 | 0.428 | REGIME(2023+ only) |
| rx|ON|nyam | 0.446 | 697 | 0.463 | -0.9 | 1.000 | 0.60 | 0.426 | 0.451 | stable |
| rx|ON|nypm | 0.425 | 431 | 0.467 | -1.9 | 1.000 | 0.80 | 0.419 | 0.442 | stable |
| rx|ON|close | 0.515 | 264 | 0.464 | +1.6 | 1.000 | 0.60 | 0.580 | 0.505 | stable |
| rx|IB|nyam | 0.420 | 830 | 0.475 | -3.2 | 0.066* | 1.00 | 0.417 | 0.422 | stable |
| rx|IB|nypm | 0.466 | 665 | 0.468 | -0.1 | 1.000 | 0.60 | 0.462 | 0.470 | stable |
| rx|IB|close | 0.448 | 346 | 0.462 | -0.6 | 1.000 | 0.60 | 0.356 | 0.473 | stable |
| rx|VW1|nyam | 0.463 | 1485 | 0.470 | -0.6 | 1.000 | 0.80 | 0.461 | 0.463 | stable |
| rx|VW1|nypm | 0.467 | 1046 | 0.469 | -0.2 | 1.000 | 0.60 | 0.429 | 0.476 | stable |
| rx|VW1|close | 0.478 | 649 | 0.461 | +0.9 | 1.000 | 0.40 | 0.454 | 0.484 | REGIME(2023+ only) |
| rx|VW2|nyam | 0.446 | 1043 | 0.481 | -2.3 | 0.902 | 0.60 | 0.427 | 0.451 | stable |
| rx|VW2|nypm | 0.475 | 617 | 0.469 | +0.3 | 1.000 | 0.40 | 0.450 | 0.488 | REGIME(2023+ only) |
| rx|VW2|close | 0.466 | 298 | 0.462 | +0.2 | 1.000 | 0.60 | 0.417 | 0.486 | REGIME(2023+ only) |
| rx|RN|asia | 0.426 | 11327 | 0.428 | -0.9 | 1.000 | 0.80 | 0.403 | 0.427 | stable |
| rx|RN|london | 0.436 | 9688 | 0.440 | -1.1 | 1.000 | 0.80 | 0.411 | 0.439 | stable |
| rx|RN|pre | 0.461 | 2831 | 0.464 | -0.4 | 1.000 | 0.40 | 0.464 | 0.472 | unstable |
| rx|RN|nyam | 0.465 | 10344 | 0.464 | +0.4 | 1.000 | 0.80 | 0.467 | 0.466 | stable |
| rx|RN|nypm | 0.471 | 7876 | 0.468 | +0.5 | 1.000 | 0.60 | 0.442 | 0.478 | REGIME(2023+ only) |
| rx|RN|close | 0.455 | 3705 | 0.469 | -1.8 | 1.000 | 0.80 | 0.430 | 0.453 | stable |

### 7. Failed break (close .25A beyond, back inside within 10 bars): fade follow-through P(0.5A back before 0.5A out)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| fb|PD|asia | 0.469 | 341 | 0.502 | -1.2 | 1.000 | 0.80 | 0.403 | 0.484 | stable |
| fb|PD|london | 0.467 | 304 | 0.497 | -1.3 | 1.000 | 0.60 | 0.508 | 0.452 | REGIME(2023+ only) |
| fb|PD|pre | 0.469 | 130 | 0.500 | -0.8 | 1.000 | 0.80 | 0.429 | 0.482 | stable |
| fb|PD|nyam | 0.448 | 328 | 0.499 | -1.9 | 1.000 | 0.80 | 0.388 | 0.453 | stable |
| fb|PD|nypm | 0.530 | 202 | 0.501 | +0.9 | 1.000 | 0.60 | 0.462 | 0.557 | REGIME(2023+ only) |
| fb|PD|close | 0.451 | 102 | 0.496 | -1.0 | 1.000 | 0.80 | 0.667 | 0.395 | REGIME(2023+ only) |
| fb|ON|nyam | 0.504 | 361 | 0.503 | +0.0 | 1.000 | 0.60 | 0.605 | 0.482 | stable |
| fb|ON|nypm | 0.444 | 275 | 0.502 | -2.2 | 0.934 | 0.80 | 0.410 | 0.453 | stable |
| fb|ON|close | 0.483 | 151 | 0.508 | -0.6 | 1.000 | 0.40 | 0.522 | 0.487 | REGIME(2023+ only) |
| fb|IB|nyam | 0.415 | 272 | 0.496 | -3.0 | 0.164 | 0.80 | 0.303 | 0.432 | stable |
| fb|IB|nypm | 0.512 | 408 | 0.499 | +0.6 | 1.000 | 0.80 | 0.528 | 0.508 | stable |
| fb|IB|close | 0.461 | 204 | 0.505 | -1.3 | 1.000 | 0.80 | 0.370 | 0.477 | stable |

### 8. Where the range forms
RTH range increments by bin: 9:30 36.0%, 10:00 24.9%, 11:00 12.6%, 12:00 8.0%, 13:00 6.6%, 14:00 6.3%, 15:00 5.6%
Label-day range increments by ET hour (percent of the day): 00h 2.4, 01h 2.2, 02h 2.8, 03h 2.9, 04h 3.2, 05h 2.4, 06h 2.2, 07h 2.1, 08h 3.9, 09h 5.9, 10h 6.5, 11h 4.8, 12h 3.2, 13h 2.8, 14h 3.0, 15h 2.8, 16h 1.7, 18h 16.7, 19h 7.3, 20h 7.5, 21h 6.2, 22h 4.7, 23h 3.1

### 9. Room and liquidity (all years, raw-frame $, 1 lot)
| session | ATR14(5m) $ | A=3xATR5 $ | RT cost $ | room(1 ATR5) | room(A) | median 5-min vol | 1.7% cap (contracts/5min) | lots for $1,200 at 3xATR5 stop |
|--|--|--|--|--|--|--|--|--|
| asia | 445 | 1335 | 130 | 3.43 | 10.28 | 7 | 0.1 | 0.9 |
| london | 392 | 1177 | 130 | 3.02 | 9.06 | 10 | 0.2 | 1.0 |
| pre | 494 | 1482 | 130 | 3.80 | 11.41 | 28 | 0.5 | 0.8 |
| nyam | 799 | 2397 | 130 | 6.15 | 18.46 | 52 | 0.9 | 0.5 |
| nypm | 716 | 2148 | 130 | 5.51 | 16.54 | 30 | 0.5 | 0.6 |
| close | 612 | 1836 | 130 | 4.71 | 14.14 | 23 | 0.4 | 0.7 |

room(A) by year: asia: 2022:6.3 2023:4.3 2024:12.4 2025:16.0 2026:11.5; london: 2022:5.8 2023:3.6 2024:10.7 2025:13.2 2026:10.2; pre: 2022:7.4 2023:5.3 2024:14.3 2025:16.0 2026:12.7; nyam: 2022:9.8 2023:7.4 2024:22.7 2025:28.8 2026:21.7; nypm: 2022:8.7 2023:6.9 2024:20.5 2025:25.6 2026:18.6; close: 2022:8.3 2023:6.4 2024:18.5 2025:22.7 2026:14.5

### 10. Versus NQ
Contemporaneous correlation of h-min returns (normalised): asia: 1m 0.15 5m 0.24 15m 0.28 30m 0.31 60m 0.32; london: 1m 0.19 5m 0.28 15m 0.32 30m 0.34 60m 0.35; pre: 1m 0.33 5m 0.41 15m 0.44; nyam: 1m 0.43 5m 0.49 15m 0.49 30m 0.51; nypm: 1m 0.38 5m 0.45 15m 0.47 30m 0.48; close: 1m 0.28 5m 0.33 15m 0.35

Lead/lag (1-15 min, family 180 cells; corr of 1-min normalised returns): cells beating the family null (top 10 by |z|; "NQ->X" = NQ leads BTC):
| direction | session | lag min | corr | z | p_family | year sign share |
|--|--|--|--|--|--|--|
| NQ->BTC | london | 1 | +0.0756 | +41.2 | 0.010 | 1.00 |
| NQ->BTC | asia | 1 | +0.0677 | +39.5 | 0.010 | 1.00 |
| NQ->BTC | nypm | 1 | +0.0662 | +29.9 | 0.010 | 1.00 |
| NQ->BTC | nyam | 1 | +0.0648 | +24.5 | 0.010 | 1.00 |
| NQ->BTC | close | 1 | +0.0461 | +14.6 | 0.010 | 1.00 |
| NQ->BTC | london | 2 | +0.0195 | +12.9 | 0.010 | 1.00 |
| NQ->BTC | asia | 2 | +0.0195 | +12.0 | 0.010 | 1.00 |
| NQ->BTC | pre | 1 | +0.0554 | +12.0 | 0.010 | 1.00 |
| NQ->BTC | asia | 3 | +0.0113 | +7.7 | 0.010 | 1.00 |
| NQ->BTC | asia | 4 | +0.0081 | +6.0 | 0.010 | 1.00 |

### 11. Map rows that become book candidates under the FROZEN rule (p_family <= .05 AND room_A(session) > 2.0)
| map row | direction | stat | p_family | room_A | year sign share | stability | 1.7% cap >= 1 contract/5min in session |
|--|--|--|--|--|--|--|--|
| AC|asia|5m | reversion | -0.024 | 0.003 | 10.3 | 1.00 |  | NO (illiquid) |
| AC|london|5m | reversion | -0.045 | 0.003 | 9.1 | 1.00 |  | NO (illiquid) |
| AC|pre|5m | reversion | -0.061 | 0.003 | 11.4 | 1.00 |  | NO (illiquid) |
| AC|nypm|5m | reversion | -0.031 | 0.003 | 16.5 | 1.00 |  | NO (illiquid) |
| AC|close|5m | reversion | -0.057 | 0.003 | 14.1 | 1.00 |  | NO (illiquid) |
| AC|asia|15m | reversion | -0.023 | 0.003 | 10.3 | 1.00 |  | NO (illiquid) |
| vr|asia|5 | reversion | +0.972 | 0.016 | 10.3 | 1.00 | stable | NO (illiquid) |
| vr|asia|15 | reversion | +0.936 | 0.016 | 10.3 | 1.00 | stable | NO (illiquid) |
| vr|asia|30 | reversion | +0.913 | 0.016 | 10.3 | 1.00 | stable | NO (illiquid) |
| vr|asia|60 | reversion | +0.911 | 0.016 | 10.3 | 0.80 | REGIME(2023+ only) | NO (illiquid) |
| vr|asia|120 | reversion | +0.918 | 0.016 | 10.3 | 0.80 | REGIME(2023+ only) | NO (illiquid) |
| vr|london|5 | reversion | +0.956 | 0.016 | 9.1 | 1.00 | stable | NO (illiquid) |
| vr|london|15 | reversion | +0.895 | 0.016 | 9.1 | 1.00 | stable | NO (illiquid) |
| vr|london|30 | reversion | +0.881 | 0.016 | 9.1 | 1.00 | stable | NO (illiquid) |
| vr|london|60 | reversion | +0.877 | 0.016 | 9.1 | 1.00 | stable | NO (illiquid) |
| vr|london|120 | reversion | +0.889 | 0.016 | 9.1 | 0.80 | stable | NO (illiquid) |
| vr|pre|5 | reversion | +0.904 | 0.016 | 11.4 | 1.00 | stable | NO (illiquid) |
| vr|pre|15 | reversion | +0.840 | 0.016 | 11.4 | 1.00 | stable | NO (illiquid) |
| hurst|pre | reversion | +0.466 | 0.016 | 11.4 | 0.80 | stable | NO (illiquid) |
| vr|nyam|5 | reversion | +0.975 | 0.016 | 18.5 | 1.00 | stable | NO (illiquid) |
| vr|nypm|5 | reversion | +0.940 | 0.016 | 16.5 | 1.00 | stable | NO (illiquid) |
| vr|nypm|15 | reversion | +0.905 | 0.016 | 16.5 | 1.00 | stable | NO (illiquid) |
| vr|nypm|30 | reversion | +0.893 | 0.016 | 16.5 | 0.80 | REGIME(2023+ only) | NO (illiquid) |
| vr|nypm|60 | reversion | +0.910 | 0.016 | 16.5 | 0.80 | REGIME(2023+ only) | NO (illiquid) |
| vr|close|5 | reversion | +0.927 | 0.016 | 14.1 | 1.00 | stable | NO (illiquid) |
| vr|close|15 | reversion | +0.846 | 0.016 | 14.1 | 1.00 | stable | NO (illiquid) |
| vr|close|30 | reversion | +0.832 | 0.016 | 14.1 | 1.00 | stable | NO (illiquid) |
| hurst|close | reversion | +0.469 | 0.016 | 14.1 | 1.00 | stable | NO (illiquid) |
| vr|rth|5 | reversion | +0.958 | 0.016 | 18.5 | 1.00 | stable | NO (illiquid) |
| vr|rth|15 | reversion | +0.932 | 0.016 | 18.5 | 1.00 | stable | NO (illiquid) |
| vr|rth|30 | reversion | +0.933 | 0.016 | 18.5 | 1.00 | stable | NO (illiquid) |

### 12. CHAR-C complements
Data note: bars are the CHAR-C bad-print-repaired copy (cc_clean.py, MORNING_FLAGS 2026-11-05); for 6E/6J the 2013-2015 years carried ~2% bars with highs/lows/closes >10 sigma outside the neighbours, which would have driven VR/Hurst and level-touch rates (raw 6E NY-PM VR(30) .16 -> .64 after repair).

Gross edge per signal (CHAR-C own cross-check cc_ac.py: past-h move >= 1 sigma, mean of sign x next-h move in $/lot, repaired bars, 15-minute decision points; shuffled-day family null on 153+ cells) against the round-trip cost $129.84:

| session | 5 min: edge $ (x cost) | 15 min: edge $ (x cost) | 30 min: edge $ (x cost) | 60 min: edge $ (x cost) |
|--|--|--|--|--|
| asia | -16.3 (0.13x) | -42.6 (0.33x) | +2.8 (0.02x) | -31.1 (0.24x) |
| london | -26.1 (0.20x) | -1.5 (0.01x) | +1.7 (0.01x) | +22.5 (0.17x) |
| pre | -60.2 (0.46x) | -46.7 (0.36x) | -52.6 (0.41x) | -59.1 (0.46x) |
| nyam | -59.4 (0.46x) | -15.0 (0.12x) | +51.7 (0.40x) | +99.0 (0.76x) |
| nypm | -46.9 (0.36x) | -55.2 (0.43x) | -59.4 (0.46x) | +2.4 (0.02x) |
| close | +0.5 (0.00x) | +6.3 (0.05x) | -18.7 (0.14x) | -121.0 (0.93x) |

Time-of-day drift map (cc_tod.py, signed 30-minute returns by ET slot, sign-flip-by-day null, 2000 worlds, family = slots): wd 04:00: +2.50 bp, +92.7 $/lot (0.71x cost), t 2.4, p_family 0.649, same sign 100% of 5 years; wd 08:30: -3.31 bp, -102.0 $/lot (0.79x cost), t -2.3, p_family 0.721, same sign 100% of 5 years; wd 16:00: +2.48 bp, +99.4 $/lot (0.77x cost), t 2.0, p_family 0.942, same sign 100% of 5 years; we 19:30: -4.46 bp, -160.2 $/lot (1.23x cost), t -1.7, p_family 0.998, same sign 80% of 5 years.


## NKD - character map (CHAR-C, 2026-11-05T23:31Z)
Base: NKD CME front-month (.v.0) 1-min bars from 2013-01 to 2026-10, percent frame (multiplicative roll-adjusted), 1-min approximation (no tick path), 2535 usable label days; ET clock, sessions asia 18:00-02:00 / london 02:00-08:30 / pre 08:30-09:30 / nyam 09:30-12:00 / nypm 12:00-15:00 / close 15:00-16:55. Nulls: within-year shuffled-day (AC B=300; structure B=100 worlds; levels recomputed on the shuffled path; round numbers 60 random grid phases); p_family = Westfall-Young max-|z| over the block (AC family 153 cells, structure family 92 cells). `**` p_family<=.05, `*` <=.10. Prereg sha256 980bedf6bad3f1669de9efb93831fa4622d88577c892d9359b7f57ba93c9dbcf. Descriptive only: no PASS, nothing live.

### Plain paragraph (CHAR-C)
NKD (Nikkei 225 in USD on CME, $5 per point) is a thin follower of NQ whose range is made in Tokyo hours: 47% of the label day's range forms in the three hours 18:00-21:00 ET (14% / 16% / 17%), the contemporaneous correlation with NQ is 0.41-0.62 on 1-minute returns and 0.56-0.78 on 15-30 minute returns depending on the session, and NQ leads NKD by one minute (corr +0.07 Asia, +0.125 London, +0.14 NY-PM, 14 of 14 years) which is worth a few dollars per signal against the $129.8 round trip. The 1.7% participation cap is 0.2-0.8 contracts per 5 minutes in every session in the char_lib room table (0.12-0.37 in INSTR2_SESSIONS; CAP-BREACH: one lot is 1.3-5 x the cap) and the round trip is 1.3-2.0 x one ATR5; 3 x ATR5 is 2.2x (Asia) and 2.25x (NY-AM) the cost, 1.5-1.8x elsewhere, so only Asia and NY-AM pass the room > 2 rule on the pooled 13 years (4.3-7.6x in 2025-26). Lag correlation is weakly negative at 1-5 minutes in every session (5-minute -0.018 to -0.038; p_family .003) and at 15 minutes in London only (-0.016, p_family .010); variance ratios .87-.95 and Hurst .48-.50 (Asia, NY-AM and NY-PM are random walks above 30 minutes). Day types equal the null (trend days 45% vs 48%; IB extended one side 70% vs 70%). The structural regularities are level touches: prior-day H/L bounce 46-51% against 41-44% in Asia / London / pre / NY-AM (year-sign .79-.86), overnight H/L in the close 50% vs 42%, IB edges in NY-PM / close 49% vs 43% / 42%, VWAP -1 sigma in the close 46% vs 41%; and the 1-A move from the session open continues LESS than null (Asia 43.5% vs 49.7%, close 34% vs 40%, pre 40% vs 45%): excursions get faded. No 30-minute drift slot passes (best 06:30 ET +0.6 bp, p_family .22). Gross edge of fading a 1-sigma move is $0.0-13.8 per signal (<= 0.11 x cost). The book that fits is the prior-day-level fade and the 5-minute excursion fade in Asia and NY-AM, both CAP-BREACH; neither clears (DS3_FIND.md).

### Generated summary (page.py of CHAR-A, same numbers)
At 1 minute every session has negative autocorrelation (-0.038 to -0.019; bid-ask bounce / last-print noise, not a tradable edge by itself). asia: reverts at 5 min (-0.018). london: reverts at 5/15 min (-0.026, -0.016). pre: reverts at 5 min (-0.038). nyam: reverts at 5 min (-0.019). nypm: reverts at 5 min (-0.023). close: reverts at 5 min (-0.033). Day types (RTH): 46% trend days (efficiency ratio >= .5; shuffled null 48%, p_fam 0.639), 25% range days (<.25; null 25%, p_fam 1.000); the IB (09:30-10:30) is extended on one side only on 70% of days and on both on 27%, and a one-sided extension closes beyond the IB edge 67% of the time (null 67%). RTH variance ratio at 30 min 0.921 (shuffled null 0.998, p_fam 0.016); Hurst 0.502. The RTH range forms 9:30 (35%), 10:00 (26%), 11:00 (12%) of the range increments. Level reactions that beat the family null: PD|asia bounces 46% of touches (more than the shuffled null 41%); PD|london bounces 50% of touches (more than the shuffled null 42%); PD|pre bounces 49% of touches (more than the shuffled null 42%); PD|nyam bounces 51% of touches (more than the shuffled null 44%); ON|close bounces 50% of touches (more than the shuffled null 42%); IB|nypm bounces 49% of touches (more than the shuffled null 43%); IB|close bounces 49% of touches (more than the shuffled null 42%); VW1|close bounces 46% of touches (more than the shuffled null 41%). Failed-break follow-through beating the null: none. Room (median 3xATR14(5m) $ / round-trip cost $130 per lot): asia 2.2x, london 1.7x, pre 1.5x, nyam 2.2x, nypm 1.8x, close 1.7x (1xATR5 room 0.7x in nyam, 0.7x in asia).

### 1. Autocorrelation of h-min returns (corr(past h, next h), both inside the session), pooled; cell = corr (pre-2023 mean | 2023+ mean) p_family
| session | 1 min | 5 min | 15 min | 30 min | 60 min | 120 min |
|--|--|--|--|--|--|--|
| asia | -0.020 (-0.022|-0.009) p0.003** ys0.93 | -0.018 (-0.017|-0.022) p0.003** ys1.00 | -0.003 (-0.003|-0.005) p1.000 ys0.64 | +0.009 (+0.009|-0.001) p0.977 ys0.50 | +0.022 (+0.023|+0.009) p0.110 ys0.71 | +0.024 (+0.036|-0.026) p0.997 ys0.64 |
| london | -0.019 (-0.024|-0.001) p0.003** ys0.79 | -0.026 (-0.028|-0.022) p0.003** ys1.00 | -0.016 (-0.027|+0.005) p0.010** ys0.79 | -0.006 (-0.017|+0.029) p1.000 ys0.64 | -0.001 (-0.007|+0.003) p1.000 ys0.50 | -0.015 (-0.019|-0.006) p1.000 ys0.64 |
| pre | -0.038 (-0.043|-0.022) p0.003** ys0.93 | -0.038 (-0.034|-0.038) p0.003** ys0.93 | -0.023 (-0.032|-0.015) p0.990 ys0.79 | +0.011 (+0.024|-0.078) p1.000 ys0.43 | - | - |
| nyam | -0.029 (-0.033|-0.015) p0.003** ys1.00 | -0.019 (-0.019|-0.016) p0.003** ys1.00 | +0.004 (-0.000|+0.006) p1.000 ys0.50 | +0.011 (+0.004|+0.016) p1.000 ys0.71 | +0.007 (-0.004|+0.021) p1.000 ys0.43 | - |
| nypm | -0.026 (-0.026|-0.020) p0.003** ys0.93 | -0.023 (-0.025|-0.022) p0.003** ys1.00 | +0.006 (+0.005|-0.001) p1.000 ys0.50 | +0.027 (+0.027|+0.021) p0.153 ys0.57 | +0.030 (+0.022|+0.049) p0.983 ys0.71 | - |
| close | -0.031 (-0.039|-0.004) p0.003** ys0.93 | -0.033 (-0.051|+0.028) p0.003** ys0.79 | -0.021 (-0.040|+0.008) p0.465 ys0.57 | -0.002 (-0.012|+0.009) p1.000 ys0.57 | - | - |

Hour cells (h >= 5) beating the family null, top 14 by |z| (hour = ET hour of the decision bar):
| h | session | hour ET | corr | z | p_family | year sign share | pre-2023 | 2023+ |
|--|--|--|--|--|--|--|--|--|
| 5 | close | 16 | -0.053 | -10.2 | 0.003 | 0.86 | -0.084 | +0.021 |
| 5 | asia | 18 | -0.043 | -9.8 | 0.003 | 1.00 | -0.046 | -0.045 |
| 5 | pre | 09 | -0.056 | -8.3 | 0.003 | 0.86 | -0.056 | -0.063 |
| 5 | nypm | 12 | -0.038 | -7.6 | 0.003 | 1.00 | -0.041 | -0.042 |
| 5 | london | 08 | -0.048 | -7.3 | 0.003 | 0.86 | -0.060 | -0.047 |
| 5 | london | 06 | -0.033 | -7.2 | 0.003 | 0.79 | -0.036 | -0.044 |
| 15 | pre | 09 | -0.091 | -6.6 | 0.003 | 0.93 | -0.106 | -0.040 |
| 5 | london | 07 | -0.032 | -6.3 | 0.003 | 1.00 | -0.035 | -0.023 |
| 15 | london | 02 | -0.050 | -5.9 | 0.003 | 0.71 | -0.080 | +0.023 |
| 5 | london | 02 | -0.029 | -5.8 | 0.003 | 0.79 | -0.032 | -0.015 |
| 5 | asia | 23 | -0.028 | -5.6 | 0.003 | 0.93 | -0.023 | -0.039 |
| 15 | close | 16 | -0.054 | -5.2 | 0.003 | 0.71 | -0.090 | +0.026 |
| 5 | close | 15 | -0.024 | -5.0 | 0.003 | 0.79 | -0.037 | +0.030 |
| 15 | asia | 18 | -0.042 | -5.0 | 0.003 | 1.00 | -0.040 | -0.060 |

### 2. Variance ratio VR(q) and Hurst (1.0 = random walk; <1 reverting; edge-bias corrected), cell = value (null) p_family
| session | VR5 | VR15 | VR30 | VR60 | VR120 | Hurst |
|--|--|--|--|--|--|--|
| asia | 0.953 (1.000) p0.016** | 0.928 (1.000) p0.016** | 0.926 (0.999) p0.016** | 0.936 (0.999) p0.016** | 0.954 (0.998) p0.230 | 0.500 (0.500) p1.000 |
| london | 0.947 (1.000) p0.016** | 0.909 (0.999) p0.016** | 0.897 (0.999) p0.016** | 0.896 (0.998) p0.016** | 0.903 (0.998) p0.016** | 0.492 (0.500) p0.131 |
| pre | 0.912 (0.999) p0.016** | 0.866 (0.998) p0.016** | - | - | - | 0.477 (0.500) p0.016** |
| nyam | 0.941 (1.000) p0.016** | 0.917 (0.998) p0.016** | 0.922 (0.998) p0.016** | - | - | 0.494 (0.499) p0.967 |
| nypm | 0.938 (1.000) p0.016** | 0.911 (0.999) p0.016** | 0.909 (0.998) p0.016** | 0.945 (0.998) p0.016** | - | 0.500 (0.500) p1.000 |
| close | 0.927 (1.000) p0.016** | 0.882 (0.999) p0.016** | 0.867 (0.997) p0.016** | - | - | 0.481 (0.499) p0.016** |
| rth | 0.940 (1.000) p0.016** | 0.915 (0.999) p0.016** | 0.921 (0.998) p0.016** | 0.931 (0.998) p0.016** | 0.950 (0.998) p0.230 | 0.502 (0.500) p1.000 |

### 3. Day types (ex-post labels of the RTH day)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| day|trend | 0.455 | 2535 | 0.478 | -2.5 | 0.639 | 0.64 | 0.450 | 0.480 | stable |
| day|range | 0.251 | 2535 | 0.248 | +0.5 | 1.000 | 0.43 | 0.266 | 0.202 | unstable |
| day|er | 0.470 | 2535 | 0.477 | -1.4 | 1.000 | 0.57 | 0.465 | 0.491 | unstable |
| day|ib_none | 0.033 | 2535 | 0.023 | +3.3 | 0.066* | 0.64 | 0.030 | 0.044 | stable |
| day|ib_one | 0.697 | 2535 | 0.699 | -0.1 | 1.000 | 0.43 | 0.689 | 0.738 | unstable |
| day|ib_both | 0.269 | 2535 | 0.278 | -1.0 | 1.000 | 0.71 | 0.281 | 0.218 | REGIME(2023+ only) |
| day|ib_one_closebeyond | 0.673 | 1768 | 0.673 | -0.0 | 1.000 | 0.50 | 0.680 | 0.661 | REGIME(2023+ only) |

### 4. 1A -> 2A continuation vs give-back-half from the session open (A = 3 x ATR14(5m)); value = P(continue | resolved)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| cont|asia | 0.435 | 2516 | 0.497 | -5.8 | 0.016** | 0.86 | 0.446 | 0.425 | stable |
| cont|london | 0.367 | 2242 | 0.406 | -3.7 | 0.033** | 0.79 | 0.362 | 0.361 | stable |
| cont|pre | 0.403 | 1175 | 0.450 | -4.1 | 0.016** | 0.86 | 0.394 | 0.428 | stable |
| cont|nyam | 0.386 | 2410 | 0.414 | -2.8 | 0.344 | 0.57 | 0.380 | 0.419 | unstable |
| cont|nypm | 0.347 | 1303 | 0.354 | -0.6 | 1.000 | 0.64 | 0.349 | 0.359 | stable |
| cont|close | 0.342 | 1419 | 0.403 | -5.2 | 0.016** | 0.71 | 0.342 | 0.353 | stable |
| cont|rth | 0.389 | 2501 | 0.414 | -2.5 | 0.672 | 0.57 | 0.384 | 0.422 | unstable |

### 5. Gap fill by size bucket (b0 .05-.10, b1 .10-.25, b2 .25-.50, b3 >.50 of the 20-day mean RTH range); day = filled during RTH, h1 = within 60 min
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| gap|b0|day | 0.924 | 92 | 0.885 | +1.4 | 1.000 | 0.64 | 0.939 | 0.833 | stable |
| gap|b0|h1 | 0.837 | 92 | 0.792 | +1.3 | 1.000 | 0.57 | 0.842 | 0.750 | unstable |
| gap|b1|day | 0.720 | 264 | 0.758 | -1.6 | 1.000 | 0.57 | 0.712 | 0.751 | unstable |
| gap|b1|h1 | 0.561 | 264 | 0.578 | -0.6 | 1.000 | 0.50 | 0.549 | 0.627 | unstable |
| gap|b2|day | 0.537 | 462 | 0.540 | -0.1 | 1.000 | 0.50 | 0.499 | 0.650 | unstable |
| gap|b2|h1 | 0.266 | 462 | 0.273 | -0.3 | 1.000 | 0.64 | 0.230 | 0.424 | stable |
| gap|b3|day | 0.151 | 1631 | 0.152 | -0.1 | 1.000 | 0.43 | 0.149 | 0.186 | unstable |
| gap|b3|h1 | 0.028 | 1631 | 0.030 | -0.6 | 1.000 | 0.64 | 0.025 | 0.045 | stable |

### 6. Level reaction: first touch -> bounce (0.5A reverse) vs break-through (0.5A beyond) within 60 min; value = P(bounce)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| rx|PD|asia | 0.464 | 2771 | 0.413 | +5.2 | 0.016** | 0.86 | 0.468 | 0.428 | stable |
| rx|PD|london | 0.502 | 1177 | 0.422 | +5.8 | 0.016** | 0.86 | 0.505 | 0.478 | stable |
| rx|PD|pre | 0.491 | 460 | 0.416 | +3.5 | 0.049** | 0.79 | 0.498 | 0.489 | stable |
| rx|PD|nyam | 0.507 | 984 | 0.441 | +4.6 | 0.016** | 0.79 | 0.507 | 0.487 | stable |
| rx|PD|nypm | 0.483 | 664 | 0.428 | +2.8 | 0.361 | 0.86 | 0.475 | 0.524 | stable |
| rx|PD|close | 0.483 | 437 | 0.419 | +2.6 | 0.443 | 0.86 | 0.481 | 0.481 | stable |
| rx|ON|nyam | 0.476 | 1276 | 0.442 | +2.7 | 0.377 | 0.64 | 0.488 | 0.427 | stable |
| rx|ON|nypm | 0.490 | 775 | 0.430 | +3.3 | 0.066* | 0.71 | 0.507 | 0.442 | stable |
| rx|ON|close | 0.501 | 539 | 0.415 | +4.1 | 0.016** | 0.79 | 0.519 | 0.407 | stable |
| rx|IB|nyam | 0.479 | 2269 | 0.446 | +3.2 | 0.082* | 0.79 | 0.493 | 0.425 | stable |
| rx|IB|nypm | 0.490 | 1718 | 0.430 | +4.8 | 0.016** | 0.93 | 0.493 | 0.470 | stable |
| rx|IB|close | 0.492 | 1068 | 0.416 | +5.4 | 0.016** | 0.71 | 0.495 | 0.452 | stable |
| rx|VW1|nyam | 0.440 | 3905 | 0.444 | -0.4 | 1.000 | 0.50 | 0.447 | 0.408 | REGIME(2023+ only) |
| rx|VW1|nypm | 0.457 | 2528 | 0.429 | +2.7 | 0.361 | 0.79 | 0.458 | 0.458 | stable |
| rx|VW1|close | 0.458 | 1721 | 0.414 | +3.6 | 0.033** | 0.86 | 0.462 | 0.452 | stable |
| rx|VW2|nyam | 0.473 | 2845 | 0.456 | +2.1 | 0.951 | 0.71 | 0.478 | 0.456 | stable |
| rx|VW2|nypm | 0.452 | 1607 | 0.434 | +1.5 | 1.000 | 0.57 | 0.444 | 0.456 | unstable |
| rx|VW2|close | 0.454 | 1019 | 0.420 | +2.3 | 0.770 | 0.57 | 0.453 | 0.399 | unstable |
| rx|RN|asia | 0.439 | 18193 | 0.442 | -0.9 | 1.000 | 0.64 | 0.438 | 0.439 | stable |
| rx|RN|london | 0.440 | 10183 | 0.442 | -0.5 | 1.000 | 0.71 | 0.444 | 0.435 | REGIME(2023+ only) |
| rx|RN|pre | 0.455 | 1854 | 0.449 | +0.6 | 1.000 | 0.64 | 0.482 | 0.438 | stable |
| rx|RN|nyam | 0.455 | 7214 | 0.453 | +0.5 | 1.000 | 0.36 | 0.458 | 0.449 | unstable |
| rx|RN|nypm | 0.455 | 4512 | 0.447 | +1.5 | 1.000 | 0.71 | 0.446 | 0.455 | REGIME(2023+ only) |
| rx|RN|close | 0.438 | 2186 | 0.434 | +0.5 | 1.000 | 0.50 | 0.445 | 0.425 | unstable |

### 7. Failed break (close .25A beyond, back inside within 10 bars): fade follow-through P(0.5A back before 0.5A out)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| fb|PD|asia | 0.495 | 1857 | 0.500 | -0.4 | 1.000 | 0.57 | 0.500 | 0.485 | unstable |
| fb|PD|london | 0.478 | 903 | 0.498 | -1.3 | 1.000 | 0.57 | 0.483 | 0.478 | unstable |
| fb|PD|pre | 0.508 | 295 | 0.503 | +0.2 | 1.000 | 0.43 | 0.486 | 0.549 | REGIME(2023+ only) |
| fb|PD|nyam | 0.499 | 706 | 0.500 | -0.1 | 1.000 | 0.57 | 0.486 | 0.534 | unstable |
| fb|PD|nypm | 0.446 | 453 | 0.500 | -2.6 | 0.459 | 0.71 | 0.422 | 0.477 | stable |
| fb|PD|close | 0.452 | 272 | 0.501 | -1.7 | 1.000 | 0.79 | 0.421 | 0.478 | stable |
| fb|ON|nyam | 0.480 | 598 | 0.501 | -1.2 | 1.000 | 0.71 | 0.464 | 0.494 | stable |
| fb|ON|nypm | 0.481 | 453 | 0.502 | -0.9 | 1.000 | 0.64 | 0.461 | 0.501 | stable |
| fb|ON|close | 0.445 | 321 | 0.498 | -1.7 | 1.000 | 0.64 | 0.468 | 0.374 | stable |
| fb|IB|nyam | 0.472 | 818 | 0.499 | -1.6 | 1.000 | 0.64 | 0.468 | 0.465 | stable |
| fb|IB|nypm | 0.462 | 1041 | 0.502 | -2.7 | 0.410 | 0.86 | 0.439 | 0.530 | stable |
| fb|IB|close | 0.444 | 655 | 0.499 | -2.5 | 0.656 | 0.64 | 0.425 | 0.495 | stable |

### 8. Where the range forms
RTH range increments by bin: 9:30 35.2%, 10:00 26.5%, 11:00 12.3%, 12:00 6.7%, 13:00 6.0%, 14:00 6.5%, 15:00 6.8%
Label-day range increments by ET hour (percent of the day): 00h 3.3, 01h 3.5, 02h 2.6, 03h 3.4, 04h 2.2, 05h 1.6, 06h 1.1, 07h 1.0, 08h 2.1, 09h 2.8, 10h 3.6, 11h 2.4, 12h 1.5, 13h 1.5, 14h 1.7, 15h 1.8, 16h 0.9, 18h 14.0, 19h 15.6, 20h 17.3, 21h 7.7, 22h 4.5, 23h 4.1

### 9. Room and liquidity (all years, raw-frame $, 1 lot)
| session | ATR14(5m) $ | A=3xATR5 $ | RT cost $ | room(1 ATR5) | room(A) | median 5-min vol | 1.7% cap (contracts/5min) | lots for $1,200 at 3xATR5 stop |
|--|--|--|--|--|--|--|--|--|
| asia | 96 | 287 | 130 | 0.74 | 2.21 | 17 | 0.3 | 4.2 |
| london | 75 | 224 | 130 | 0.58 | 1.73 | 16 | 0.3 | 5.4 |
| pre | 66 | 197 | 130 | 0.50 | 1.51 | 23 | 0.4 | 6.1 |
| nyam | 97 | 292 | 130 | 0.75 | 2.25 | 46 | 0.8 | 4.1 |
| nypm | 79 | 237 | 130 | 0.61 | 1.83 | 16 | 0.3 | 5.1 |
| close | 74 | 221 | 130 | 0.57 | 1.70 | 12 | 0.2 | 5.4 |

room(A) by year: asia: 2013:1.7 2014:1.5 2015:1.6 2016:1.9 2017:1.3 2018:2.1 2019:1.5 2020:2.3 2021:3.0 2022:2.6 2023:2.8 2024:4.0 2025:4.4 2026:8.7; london: 2013:1.4 2014:1.2 2015:1.5 2016:1.6 2017:1.0 2018:1.5 2019:1.1 2020:2.0 2021:2.1 2022:1.9 2023:2.0 2024:2.7 2025:3.2 2026:7.4; pre: 2013:1.1 2014:1.1 2015:1.2 2016:1.3 2017:0.9 2018:1.3 2019:1.1 2020:1.6 2021:1.7 2022:1.8 2023:1.8 2024:2.6 2025:3.1 2026:7.0; nyam: 2013:1.6 2014:1.6 2015:1.7 2016:1.7 2017:1.3 2018:2.0 2019:1.6 2020:2.2 2021:2.6 2022:3.0 2023:2.8 2024:4.0 2025:4.8 2026:10.3; nypm: 2013:1.3 2014:1.3 2015:1.4 2016:1.4 2017:1.1 2018:1.7 2019:1.2 2020:1.7 2021:1.9 2022:2.5 2023:2.1 2024:3.3 2025:3.8 2026:7.4; close: 2013:1.3 2014:1.2 2015:1.4 2016:1.3 2017:0.9 2018:1.6 2019:1.1 2020:1.7 2021:1.9 2022:2.4 2023:1.7 2024:2.7 2025:3.1 2026:5.5

### 10. Versus NQ
Contemporaneous correlation of h-min returns (normalised): asia: 1m 0.41 5m 0.52 15m 0.56 30m 0.58 60m 0.60; london: 1m 0.47 5m 0.62 15m 0.68 30m 0.70 60m 0.71; pre: 1m 0.51 5m 0.61 15m 0.64; nyam: 1m 0.62 5m 0.72 15m 0.73 30m 0.74; nypm: 1m 0.57 5m 0.73 15m 0.77 30m 0.78; close: 1m 0.50 5m 0.65 15m 0.70

Lead/lag (1-15 min, family 180 cells; corr of 1-min normalised returns): cells beating the family null (top 10 by |z|; "NQ->X" = NQ leads NKD):
| direction | session | lag min | corr | z | p_family | year sign share |
|--|--|--|--|--|--|--|
| NQ->NKD | london | 1 | +0.1246 | +109.0 | 0.010 | 1.00 |
| NQ->NKD | nypm | 1 | +0.1406 | +89.3 | 0.010 | 1.00 |
| NQ->NKD | asia | 1 | +0.0745 | +76.3 | 0.010 | 1.00 |
| NQ->NKD | close | 1 | +0.1288 | +61.4 | 0.010 | 1.00 |
| NQ->NKD | nyam | 1 | +0.0966 | +52.9 | 0.010 | 1.00 |
| NQ->NKD | pre | 1 | +0.0906 | +36.6 | 0.010 | 1.00 |
| NQ->NKD | london | 2 | +0.0249 | +23.1 | 0.010 | 1.00 |
| NKD->NQ | asia | 1 | +0.0139 | +14.0 | 0.010 | 0.86 |
| NQ->NKD | nypm | 2 | +0.0202 | +13.5 | 0.010 | 1.00 |
| NQ->NKD | asia | 2 | +0.0124 | +12.9 | 0.010 | 1.00 |

### 11. Map rows that become book candidates under the FROZEN rule (p_family <= .05 AND room_A(session) > 2.0)
| map row | direction | stat | p_family | room_A | year sign share | stability | 1.7% cap >= 1 contract/5min in session |
|--|--|--|--|--|--|--|--|
| AC|asia|5m | reversion | -0.018 | 0.003 | 2.2 | 1.00 |  | NO (illiquid) |
| AC|nyam|5m | reversion | -0.019 | 0.003 | 2.2 | 1.00 |  | NO (illiquid) |
| rx|PD|asia | level-bounce | +0.464 | 0.016 | 2.2 | 0.86 | stable | NO (illiquid) |
| rx|PD|nyam | level-bounce | +0.507 | 0.016 | 2.2 | 0.79 | stable | NO (illiquid) |
| vr|asia|5 | reversion | +0.953 | 0.016 | 2.2 | 1.00 | stable | NO (illiquid) |
| vr|asia|15 | reversion | +0.928 | 0.016 | 2.2 | 1.00 | stable | NO (illiquid) |
| vr|asia|30 | reversion | +0.926 | 0.016 | 2.2 | 1.00 | stable | NO (illiquid) |
| vr|asia|60 | reversion | +0.936 | 0.016 | 2.2 | 0.93 | stable | NO (illiquid) |
| vr|nyam|5 | reversion | +0.941 | 0.016 | 2.2 | 1.00 | stable | NO (illiquid) |
| vr|nyam|15 | reversion | +0.917 | 0.016 | 2.2 | 1.00 | stable | NO (illiquid) |
| vr|nyam|30 | reversion | +0.922 | 0.016 | 2.2 | 1.00 | stable | NO (illiquid) |
| vr|rth|5 | reversion | +0.940 | 0.016 | 2.2 | 1.00 | stable | NO (illiquid) |
| vr|rth|15 | reversion | +0.915 | 0.016 | 2.2 | 1.00 | stable | NO (illiquid) |
| vr|rth|30 | reversion | +0.921 | 0.016 | 2.2 | 1.00 | stable | NO (illiquid) |
| vr|rth|60 | reversion | +0.931 | 0.016 | 2.2 | 0.93 | stable | NO (illiquid) |

### 12. CHAR-C complements
Data note: bars are the CHAR-C bad-print-repaired copy (cc_clean.py, MORNING_FLAGS 2026-11-05); for 6E/6J the 2013-2015 years carried ~2% bars with highs/lows/closes >10 sigma outside the neighbours, which would have driven VR/Hurst and level-touch rates (raw 6E NY-PM VR(30) .16 -> .64 after repair).

Gross edge per signal (CHAR-C own cross-check cc_ac.py: past-h move >= 1 sigma, mean of sign x next-h move in $/lot, repaired bars, 15-minute decision points; shuffled-day family null on 153+ cells) against the round-trip cost $129.84:

| session | 5 min: edge $ (x cost) | 15 min: edge $ (x cost) | 30 min: edge $ (x cost) | 60 min: edge $ (x cost) |
|--|--|--|--|--|
| asia | -4.4 (0.03x) | -0.7 (0.01x) | -1.8 (0.01x) | +4.6 (0.04x) |
| london | -2.3 (0.02x) | -1.4 (0.01x) | -5.3 (0.04x) | -2.0 (0.02x) |
| pre | -2.9 (0.02x) | +0.0 (0.00x) | -1.9 (0.01x) | -13.8 (0.11x) |
| nyam | -8.2 (0.06x) | -0.8 (0.01x) | +3.2 (0.02x) | +4.0 (0.03x) |
| nypm | -5.6 (0.04x) | -7.5 (0.06x) | -4.1 (0.03x) | -4.0 (0.03x) |
| close | -3.3 (0.03x) | +1.1 (0.01x) | +1.6 (0.01x) | +1.7 (0.01x) |

Time-of-day drift map (cc_tod.py, signed 30-minute returns by ET slot, sign-flip-by-day null, 2000 worlds, family = slots): wd 06:30: +0.64 bp, +8.3 $/lot (0.06x cost), t 2.8, p_family 0.221, same sign 86% of 14 years; wd 13:30: +0.68 bp, +11.0 $/lot (0.08x cost), t 2.4, p_family 0.568, same sign 93% of 14 years; wd 02:00: +0.73 bp, +8.1 $/lot (0.06x cost), t 2.0, p_family 0.893, same sign 79% of 14 years; wd 14:30: +0.61 bp, +4.7 $/lot (0.04x cost), t 2.0, p_family 0.908, same sign 57% of 14 years.

## GC CL ZN ZB - event-day reaction tables (CHAR-B, descriptive, 2026-11-05)
Calendars from public rules (findb/fb_cal.py: EIA Wed 10:30 with holiday-week Thursday decided at 10:31; CL expiry = 3 bd before the 25th rule, expiry WEEK Mon-Fri; NFP third-Friday-after-reference-week rule 35/43 matched; 2023+ CPI/claims/10Y-30Y auction dates from DISCOVER_CALENDAR.csv; refunding Wed dated 6-12; 'OPEC Monday' has no public-rule date so it is every Monday 18:00 reopen, ASSUMPTION). Statistic = mean(sign(r1)*r2)/sd(r2): r1 = log move from the pre-event close to the reaction bar, r2 = the move from the reaction bar to the follow time; >0 continuation, <0 reversal. Null = same-size random day sets with the same day-of-week mix, 2,000 draws; family = Bonferroni over the 25 tests. Frame: percent (log returns on raw within-contract closes, roll bars excluded), 1-min, base GC/CL/ZN/ZB .v.0 2013-01..2026-10-16.
| instrument | event window | n days | stat | null mean | z | p raw | p family (Bonf, 25) | mean abs reaction bp |
|--|--|--|--|--|--|--|--|--|
| CL | EIA 10:30 react 10:35, follow to 11:30 | 707 | +0.024 | +0.008 | +0.43 | 0.671 | 1.00 | 43.0 |
| CL | EIA follow to 14:00 | 707 | +0.010 | -0.015 | +0.70 | 0.479 | 1.00 | 43.0 |
| CL | EIA day 11:00-14:00 drift sign of 10:30-11:00 | 711 | +0.012 | +0.007 | +0.15 | 0.887 | 1.00 | 65.8 |
| CL | expiry week open 09:00 react 09:15 follow 12:00 | 805 | +0.039 | +0.016 | +0.70 | 0.474 | 1.00 | 33.9 |
| CL | Monday 18:00 gap open react 18:15 follow 20:00 | 666 | +0.012 | +0.012 | +0.00 | 0.995 | 1.00 | 15.2 |
| CL | 14:30 settlement window: 14:00-14:30 move continues to 14:35 | 3408 | -0.014 | -0.014 | -0.00 | 0.997 | 1.00 | 38.2 |
| GC | London AM fix 05:30: -30..-0 move then 05:30..06:00 | 3447 | -0.052 | -0.052 | -0.01 | 0.994 | 1.00 | 8.6 |
| GC | London PM fix 10:00: 09:30..10:00 move then 10:00..10:30 | 3486 | +0.018 | +0.017 | +0.02 | 0.987 | 1.00 | 19.5 |
| GC | NFP 08:30 react 08:35 follow 10:00 | 157 | -0.030 | -0.031 | +0.01 | 0.990 | 1.00 | 44.6 |
| GC | CPI 08:30 react 08:35 follow 10:00 | 42 | -0.134 | +0.008 | -1.17 | 0.243 | 1.00 | 38.7 |
| GC | 08:20 COMEX open react 08:35 follow 09:30 | 3496 | +0.005 | +0.005 | +0.04 | 0.968 | 1.00 | 16.8 |
| ZN | NFP 08:30 react 08:35 follow 10:00 | 157 | -0.051 | -0.020 | -0.53 | 0.593 | 1.00 | 24.4 |
| ZN | CPI 08:30 react 08:35 follow 10:00 | 42 | -0.103 | +0.005 | -0.95 | 0.348 | 1.00 | 29.8 |
| ZN | claims 08:30 react 08:35 follow 09:30 | 175 | -0.027 | -0.016 | -0.16 | 0.862 | 1.00 | 11.0 |
| ZN | 10y/30y auction day 13:00: 12:00-13:00 move then 13:00-13:30 | 102 | -0.027 | +0.000 | -0.38 | 0.699 | 1.00 | 4.9 |
| ZN | refunding Wed same | 50 | +0.016 | +0.011 | +0.06 | 0.947 | 1.00 | 5.3 |
| ZN | settle fade 15:00: 14:30-15:00 then 15:00-15:30 | 2972 | -0.007 | -0.007 | +0.03 | 0.968 | 1.00 | 4.3 |
| ZN | month-end 15:00 settle | 151 | +0.057 | -0.002 | +0.88 | 0.377 | 1.00 | 5.7 |
| ZB | NFP 08:30 react 08:35 follow 10:00 | 155 | -0.022 | -0.020 | -0.04 | 0.961 | 1.00 | 35.6 |
| ZB | CPI 08:30 react 08:35 follow 10:00 | 42 | -0.018 | +0.031 | -0.41 | 0.688 | 1.00 | 42.3 |
| ZB | claims 08:30 react 08:35 follow 09:30 | 176 | +0.009 | +0.022 | -0.20 | 0.838 | 1.00 | 15.9 |
| ZB | 10y/30y auction day 13:00: 12:00-13:00 move then 13:00-13:30 | 102 | +0.039 | +0.003 | +0.60 | 0.539 | 1.00 | 9.8 |
| ZB | refunding Wed same | 48 | +0.121 | -0.004 | +1.27 | 0.196 | 1.00 | 11.7 |
| ZB | settle fade 15:00: 14:30-15:00 then 15:00-15:30 | 3010 | -0.012 | -0.011 | -0.06 | 0.962 | 1.00 | 8.0 |
| ZB | month-end 15:00 settle | 145 | -0.011 | -0.004 | -0.12 | 0.908 | 1.00 | 10.9 |

Plain reading: none of the 25 event-clock windows (EIA, expiry week, Monday reopen, 14:30 settle, London fixes, NFP/CPI/claims, 10Y/30Y auctions, refunding, 15:00 settle, month-end) shows a continuation or reversal beyond the same-size random-day null (smallest raw p = 0.196 apart from the all-day control rows; family p = 1.00). The event bars are large (CL EIA 10:30 reaction 43 bp mean absolute, GC NFP 45 bp, ZB NFP 36 bp) but the move after the reaction is a coin flip, so the Addendum A event books (S4a CL/GC, S4b ZN/ZB) have no map support at this horizon from CHAR-B; they stay with their owners.

## 1b-b (CHAR-A): level sweeps / absorption on the 1-second book tables, ES RTY (NQ control), 2023-08..2026-10 -- NO PRE-2023 EVIDENCE (L2 starts 2023-08)
Prereg l2vast/ds3/prereg/T_FIND_TICKMAP_prereg.md sha256 081e392b3c5dba6e11bf244c1f465ede0684fcc8426124397d65c3c4d210e326 (DECISIONS.md, before any number). Base: 1-s mid of the front contract per label day, reference mid[t0+1] (1 s latency), level touch = first mid cross from the natural side per level per session, 'burst' = 5-s traded volume >= prior-day 90th pct. F = mean(approach-direction x (mid[t0+1+h]-mid[t0+1])) in ticks (positive = follow-through, negative = fade). Null: within-month level transplant, B=60 draws, round numbers 60 random grid phases; p_family = Westfall-Young max-|z| over 240 cells. Truncation test: 0 failures in 282 (ES) / 252 (RTY) cuts; negative control (IB used before complete) fails 19/282 and 18/252.

### ES: 240 cells, 2 with p_family<=.05, 3 <=.10
| level | session | class | h (s) | n | F ticks | null | z | p_family | period sign share | spread ticks | net ticks (market in/out, fee 4.84) | room | frozen rule |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| PD | nyam | burst | 5 | 428 | +0.75 | -0.06 | +4.0 | 0.033 | 1.00 | 1.0 | -0.64 | 2.3 | no (net<=0 or room<=2) |
| PD | nyam | burst | 60 | 428 | +2.55 | +0.15 | +3.7 | 0.049 | 0.75 | 1.0 | +1.17 | 6.7 | PASS->book |
| PD | nyam | all | 60 | 557 | +1.90 | +0.05 | +3.4 | 0.082 | 0.75 | - | - | - | no (p_family>.05) |
| PD | nyam | all | 5 | 557 | +0.48 | -0.05 | +3.2 | 0.197 | 0.75 | - | - | - | no (p_family>.05) |
| PD | nyam | all | 30 | 557 | +1.20 | +0.06 | +3.0 | 0.393 | 1.00 | - | - | - | no (p_family>.05) |
| PD | nyam | burst | 30 | 428 | +1.52 | +0.08 | +2.9 | 0.459 | 0.75 | - | - | - | no (p_family>.05) |
| PD | london | all | 1800 | 396 | +0.54 | -3.54 | +2.9 | 0.557 | 1.00 | - | - | - | no (p_family>.05) |
| PD | pre | burst | 1800 | 83 | -1.31 | -14.14 | +2.5 | 0.902 | 0.75 | - | - | - | no (p_family>.05) |

Books from the rows that pass the frozen rule (ES): 6 cells on the 1-s path (6 per row: stop 1.0/1.5/2.0 x expanding median move, target none or 1R, time stop = h), L6M>0 and HOLD>0: 0, tolerant 0, BAR CLEARED 0, best family p 0.01.

### RTY: 240 cells, 3 with p_family<=.05, 3 <=.10
| level | session | class | h (s) | n | F ticks | null | z | p_family | period sign share | spread ticks | net ticks (market in/out, fee 4.84) | room | frozen rule |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| PD | pre | burst | 1800 | 105 | +13.37 | -29.40 | +4.3 | 0.016 | 1.00 | 4.0 | +8.40 | 16.7 | PASS->book |
| PD | pre | burst | 300 | 105 | +6.14 | -17.41 | +4.4 | 0.016 | 1.00 | 4.0 | +1.17 | 11.8 | PASS->book |
| PD | pre | all | 300 | 260 | +2.01 | -7.73 | +3.9 | 0.033 | 1.00 | 2.0 | -0.96 | 11.7 | no (net<=0 or room<=2) |
| VW2 | close | all | 1800 | 208 | -12.15 | -1.96 | -3.1 | 0.246 | 0.75 | - | - | - | no (p_family>.05) |
| PD | pre | burst | 30 | 105 | +12.30 | -1.95 | +3.1 | 0.295 | 1.00 | - | - | - | no (p_family>.05) |
| PD | pre | all | 60 | 260 | +5.59 | -1.12 | +3.0 | 0.361 | 1.00 | - | - | - | no (p_family>.05) |
| PD | pre | all | 1800 | 260 | -0.94 | -15.07 | +3.0 | 0.410 | 1.00 | - | - | - | no (p_family>.05) |
| PD | pre | all | 30 | 260 | +4.56 | -0.76 | +2.9 | 0.508 | 1.00 | - | - | - | no (p_family>.05) |

Books from the rows that pass the frozen rule (RTY): 12 cells on the 1-s path (6 per row: stop 1.0/1.5/2.0 x expanding median move, target none or 1R, time stop = h), L6M>0 and HOLD>0: 12, tolerant 8, BAR CLEARED 0, best family p 0.49.

### NQ (control): 240 cells, 3 with p_family<=.05, 3 <=.10
| level | session | class | h (s) | n | F ticks | null | z | p_family | period sign share | spread ticks | net ticks (market in/out, fee 4.84) | room | frozen rule |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| IB | nypm | all | 5 | 728 | +2.07 | -0.28 | +4.2 | 0.016 | 1.00 | 2.0 | -0.89 | 3.3 | no (net<=0 or room<=2) |
| PD | nyam | all | 30 | 673 | +5.47 | -0.08 | +3.5 | 0.033 | 0.80 | 2.0 | +2.50 | 12.4 | PASS->book |
| PD | pre | burst | 1800 | 111 | +24.94 | -48.88 | +3.4 | 0.033 | 1.00 | 4.0 | +19.97 | 31.4 | PASS->book |
| PD | nyam | burst | 30 | 598 | +5.96 | +0.07 | +3.1 | 0.311 | 0.80 | - | - | - | no (p_family>.05) |
| PD | nyam | burst | 60 | 598 | +8.63 | +0.65 | +3.0 | 0.328 | 0.60 | - | - | - | no (p_family>.05) |
| PD | nyam | all | 60 | 673 | +7.22 | +0.37 | +3.0 | 0.426 | 0.60 | - | - | - | no (p_family>.05) |
| IB | nypm | burst | 5 | 360 | +2.76 | -0.50 | +3.0 | 0.426 | 0.80 | - | - | - | no (p_family>.05) |
| PD | pre | all | 300 | 274 | +4.11 | -13.34 | +2.8 | 0.656 | 1.00 | - | - | - | no (p_family>.05) |

Books from the rows that pass the frozen rule (NQ): 12 cells on the 1-s path (6 per row: stop 1.0/1.5/2.0 x expanding median move, target none or 1R, time stop = h), L6M>0 and HOLD>0: 0, tolerant 1, BAR CLEARED 0, best family p 0.60.

Plain paragraph: At tick scale the one regularity that survives the family correction is that the first touch of the PRIOR-DAY HIGH/LOW in the 09:30-12:00 session is followed by CONTINUATION (ES, NQ) -- after a volume burst ES drifts +0.75 tick in 5 s and +2.6 ticks (about $32) in 60 s beyond the touch, against a null of about 0 -- and RTY/NQ pre-market (08:30-09:30) touches of the prior-day level continue +6 to +25 ticks over 5-30 min; the 1-min map (bounce vs 0.5A reversal) could not see it because the move is 2-3 ticks. IB-edge touches in 12:00-15:00 give NQ +2 ticks in 5 s. Overnight-high/low, VWAP +-1/2 sigma and round numbers show nothing beyond the null. It does not turn into money: ES 60 s needs 1.4 ticks of cost per round trip (net +1.2 on the mid-to-mid average) but the bracketed books on the 1-s prints lose (HOLD -$91..-264/wk, placebo p_book 0.01-0.03 i.e. systematically worse than random-side) because entry on the first print at/after t0+1 gives back the drift and stops cut the winners; RTY pre-market books are positive in L1M..PRE but have 95 trades, X' is negative and the placebo p_book is .12-.87; NQ control books lose. Nothing clears; Shadow only. The other 1b blocks (a) imbalance/OFI, (c) flow bursts, (d) passive entries, (e) cost ratio are owned by ZL-1, Z1, ZL-2.
CORRECTION to the 1b-b ES sentence (CHAR-A): the ES prior-day-level books lose money in absolute terms (HOLD -$91..-264/wk, PRE -$361..-671/wk, X' negative) but beat the random-side/shifted placebos (placebo p_book 0.01-0.03; the placebos lose more because they pay the same costs with no drift), so the tick-scale follow-through is real but smaller than the round-trip cost plus the first-print entry give-up; it is not 'worse than random'. The best family p of 0.01 for ES is over a 6-cell family and is not a lead (L6M and HOLD are negative, so the tolerant gate fails).

## 1b-c - trade-size and aggressor-flow bursts: ES, RTY, NQ control (Z1, 2026-11-06)
Prereg l2vast/ds3/prereg/FIND_1BC_prereg.md sha256 b6879c2e2cfb453b08f79e8c3d0904273297b1bbc3d7ab963da23f05a9cf8e51 (logged in DECISIONS.md before any outcome). Data: tables/<SYM>/1s 2023-08-01..2026-10-30 (833 label days; NO pre-2023 evidence; X' window is partial 2023-08..2024-01). Features: large-print net (class-2 prints), sweep net, buy-sell imbalance, run (sign count) over w = 1,5,15,60,300 s; event when |stat| exceeds the trailing-20-day same-ET-hour q = .95/.99 quantile; horizons 5, 15, 60, 300, 900 s; entry = quote 1 s after the decision, cost = measured spread at entry and exit (half each) + $4.84 fee; one event per max(w,h) s. 10,440 cells per instrument (6 sessions + 23 ET hours, continuation and reversal), n >= 300 events to be scored. Null = 200 shuffled-day worlds (days permuted within the calendar month, forward move taken at the same second-of-day), family = max net t over all scored cells. Truncation test (24 random day/second cuts per instrument): 24/24 ES, 24/24 RTY, 24/24 NQ. Code l2vast/ds3/code/find1bc/ (engine.py, run.py, analyze.py, test_trunc.py, book.py); cells /mnt/l2/l2vast/find_1bc/<SYM>_cells.parquet.
Plain paragraph: **ES, RTY and NQ do not show a net-of-cost continuation or reversal after size or flow bursts at 1 s .. 15 min.** Pooled over the six sessions the average gross move after a burst (in ticks, in the burst direction) is within about +-0.4 tick at every horizon up to 15 min on ES (large-print +0.00/-0.01/-0.02/-0.15/-0.35 at 5/15/60/300/900 s; sweep and imbalance slightly negative = mild reversal; run about 0), RTY within +-0.25 tick except sweep -0.25 at 900 s, NQ within +-1.0 tick (sweep -1.0 tick at 300 s, large-print +0.2 at 60 s, run +0.7 at 900 s). The cost to trade it (measured half-spreads at entry and exit plus fee) is 1.4 ticks on ES, 2.6-3.0 on RTY and 3.7-4.0 on NQ, so the room is negative almost everywhere: net > 0 in 87 of 10,388 scored ES cells, 55 of 9,738 RTY, 270 of 10,416 NQ.
| instrument | cells scored | net>0 | best cell (feature, w, q, h, group, side) | n | gross / cost / net ticks | net t | family p | joint p (3 inst.) | halves net |
|---|---|---|---|---|---|---|---|---|---|
| ES | 10,388 | 87 | F2 sweep net, 60 s, q .99, 900 s, ET 12:00-12:59, reversal | 547 | 4.89 / 1.44 / +3.46 | 2.40 | 0.050 | 0.39 | +1.85 / +4.87 |
| RTY | 9,738 | 55 | F3 imbalance, 300 s, q .99, 900 s, ET 12, reversal | 546 | 5.06 / 2.65 / +2.41 | 1.23 | 0.54 | - | +4.05 / +0.83 |
| NQ (control) | 10,416 | 270 | F1 large-print, 300 s, q .99, 300 s, ET 09, continuation | 515 | 20.6 / 3.7 / +16.9 | 2.76 | 0.104 | - | +5.8 / +29.5 |
World max net t: median 1.52 / 1.27 / 2.29 and 95th percentile 2.28 / 1.99 / 2.99 (ES / RTY / NQ); the true maxima are 2.40 / 1.23 / 2.76. One cell clears the ES instrument-family null at p .05 (it passes my frozen 'beats the null' rule: family p <= .10, net > 0 in both halves, n >= 300); against the joint ES+RTY+NQ family it has p .39. Its neighbours (w 15 and 300, q .95, h 300) are all negative or near zero net (-0.3 .. +0.6 ticks; only h = 900 s is positive), so there is no plateau. Cells with net > 0 and per-cell p <= .05: 66 ES, 45 RTY, 129 NQ out of 10,000 cells each, consistent with the multiplicity.
**Book from the frozen rule (one ES row):** sweep-buy burst reversal, 60 s sweep net above the trailing q .99, ET 12:00-12:59, fade it at the 1-s-delayed quote, 900 s time stop, stop 3 x trailing-20-day median 5-min range, equal-risk lots R $1,200, instr2_eval windows L1M..X' (545 trades, mean +$30.8/trade at 1 lot): L1M -$632/wk (5 weeks), L3M -$1,037 (carry dropped), L6M -$160 (16 wk), HOLD +$99 (41 wk), MID +$299 (12), PRE +$18 (71), X' +$189 (23); gate FAILS (NOW-ONLY: L3M and L6M not both > 0), persistence 50%, stack Calmar not up. Placebo and walk-forward not run because the gate fails first. Label NEGATIVE (recent windows negative; spike without plateau; joint family p .39). No PASS claim.

### CHAR-C addendum to the 6J and NKD pages: 1-second tape (2026-11-06)
The purchased 1-s tapes exist (/mnt/l2/l2vast/ds3/discover_data/, SPEND.json LEAN_20261103) and aggregate exactly to the owned 1-min bars (100% equal O/H/L/C), so every 1-min number above is unchanged for 2023-04..2026-10. On the 1-s grid 6J reverts at 5-60 seconds in every session (lag correlation -0.024 to -0.093, p_family .003; the close and NY-PM keep -0.03 at 5 minutes), which is the last-print bid-ask bounce itself; NKD shows nothing sub-minute beyond |0.037| (thin prints). Details and the 1-s book re-run: DS3_FIND.md section 'on the 1-SECOND path'.

## 1b-DEEP (CHAR-A): first touch of the prior-day H/L after a volume burst -> continuation (RTY 08:30-09:30, ES 09:30-12:00, NQ control). LABEL: REGIME / WATCH (does not clear the bar). No pre-2023 evidence on the 1-s data; the 1-min proxy fails calibration.
Prereg l2vast/ds3/prereg/T_FIND_1BDEEP_prereg.md (sha256 in DECISIONS.md 2026-11-06, filed before any deep number). Data 2023-08..2026-10 1-s tables; the 1-s tables cannot resolve 0.5 s latency, so the latency grid is 0/1/2/3 s.

### (1) Plateau surface. Mid-to-mid net (ticks) = F - median spread at the touch - fee (ES 0.39, RTY/NQ 0.97 ticks), 27 nodes per hold = burst q {.80,.90,.95} x touch buffer {0,1,2 ticks} x latency {1,2,3 s}; cost +-1 tick shown in the cost column of deep_surface.csv. PLATEAU = base node net>0 and >=70% of nodes net>0.
| instrument | session | hold s | n (base) | F base | net base | net base +1 tick cost | share of 27 nodes net>0 | share incl. cost +-1 | label |
|--|--|--|--|--|--|--|--|--|--|
| ES | nyam | 30 | 428 | +1.52 | +0.13 | -0.87 | 0.15 | 0.38 | SPIKE/NO |
| ES | nyam | 60 | 428 | +2.55 | +1.17 | +0.17 | 1.00 | 0.77 | PLATEAU |
| ES | nyam | 300 | 428 | +2.68 | +1.30 | +0.30 | 0.74 | 0.63 | PLATEAU |
| ES | nyam | 1800 | 428 | +4.64 | +3.25 | +2.25 | 0.89 | 0.91 | PLATEAU |
| NQ | nyam | 30 | 598 | +5.96 | +2.99 | +1.99 | 1.00 | 0.96 | PLATEAU |
| NQ | nyam | 60 | 598 | +8.63 | +5.67 | +4.67 | 1.00 | 1.00 | PLATEAU |
| NQ | nyam | 300 | 598 | +11.57 | +8.60 | +7.60 | 1.00 | 1.00 | PLATEAU |
| NQ | nyam | 1800 | 598 | +2.64 | -0.33 | -1.33 | 0.04 | 0.06 | SPIKE/NO |
| NQ | pre | 30 | 111 | +4.32 | -0.64 | -1.64 | 0.30 | 0.35 | SPIKE/NO |
| NQ | pre | 60 | 111 | +11.88 | +6.91 | +5.91 | 1.00 | 0.99 | PLATEAU |
| NQ | pre | 300 | 111 | +10.70 | +5.73 | +4.73 | 1.00 | 0.99 | PLATEAU |
| NQ | pre | 1800 | 111 | +24.94 | +19.97 | +18.97 | 1.00 | 1.00 | PLATEAU |
| RTY | pre | 30 | 105 | +12.30 | +7.33 | +6.33 | 1.00 | 0.99 | PLATEAU |
| RTY | pre | 60 | 105 | +12.94 | +7.97 | +6.97 | 1.00 | 1.00 | PLATEAU |
| RTY | pre | 300 | 105 | +6.14 | +1.17 | +0.17 | 0.44 | 0.43 | SPIKE/NO |
| RTY | pre | 1800 | 105 | +13.37 | +8.40 | +7.40 | 0.74 | 0.73 | PLATEAU |
Reading: the RTY pre-market rows are a plateau in the burst threshold only for q>=.90 (q=.80 gives net <= 0 at 300 s and ~+1.5 ticks at 1800 s; the effect rises with burst intensity), the touch buffer (confirmed breaks are weaker than the bare touch) and latency 2-3 s costs 2-3 ticks of 1800 s edge; ES helps at 60 s and 1800 s (net +1.2 / +3.3) and fails at 30 s; NQ nyam passes at 30-300 s and fails at 1800 s. All maps are mid-to-mid and from ONE selected row of 240 (selection bias); the nodes are strongly correlated.

### Book surface (1-s prints, 3 stops x 2 targets x latency 1/2/3 s x cost -1/0/+1 tick = 54 nodes per row, no placebos, $/wk at equal-risk $1,200 lots, carry dropped)
| instrument | session | hold s | HOLD>0 share | L6M>0 share | PRE>0 share | all three >0 | median HOLD $/wk | HOLD>0 at cost +1 tick |
|--|--|--|--|--|--|--|--|--|
| ES | nyam | 60 | 0.24 | 0.20 | 0.00 | 0.00 | -195 | 0.00 |
| NQ | nyam | 30 | 0.00 | 0.22 | 0.00 | 0.00 | -144 | 0.00 |
| NQ | pre | 1800 | 0.06 | 0.17 | 0.83 | 0.00 | -94 | 0.06 |
| RTY | pre | 300 | 0.69 | 1.00 | 0.65 | 0.50 | +23 | 0.67 |
| RTY | pre | 1800 | 0.91 | 1.00 | 0.59 | 0.52 | +105 | 0.83 |
Only RTY pre-market is a book-level plateau (HOLD>0 in 69% (300 s) and 91% (1800 s) of nodes, L6M>0 in all, PRE>0 in 59-65%); ES and NQ map rows do not survive the 1-s book (median HOLD -$195 / -$144 /wk): the map-to-book gap is entry on the first print plus stops.

### (2) Pre-2023 1-min proxy (percent frame; 1-min volume at the touch bar >= q* x prior-day RTH 1-min 90th pct; outcome close-to-close 5 / 30 min after the touch minute, in ticks at the 2023-26 price). Calibration on 2023-08..2026-10 (best-F1 q*):
| instrument | session | q* | 1-s events | proxy events | matched | recall | precision | weekly corr h300 | weekly corr h1800 | verdict |
|--|--|--|--|--|--|--|--|--|--|--|
| NQ | nyam | 0.5 | 598 | 547 | 489 | 0.82 | 0.89 | 0.77 | 0.85 | NO FORMAL VERDICT (weekly corr < .90) |
| ES | nyam | 0.75 | 428 | 476 | 384 | 0.90 | 0.81 | 0.67 | 0.79 | NO FORMAL VERDICT (weekly corr < .90) |
| RTY | pre | 0.75 | 105 | 107 | 81 | 0.77 | 0.76 | 0.59 | 0.77 | NO FORMAL VERDICT (weekly corr < .90) |
| NQ | pre | 0.5 | 111 | 105 | 75 | 0.68 | 0.71 | 0.56 | 0.74 | NO FORMAL VERDICT (weekly corr < .90) |
Because no row reaches weekly corr .90, the yearly tables below are INFORMAL (labelled, not a verdict). Mean 30-min continuation after the touch+burst in ticks (se in brackets), proxy:
* ES nyam: 2013: -2.4 (4.0, n 149); 2014: -3.5 (3.8, n 142); 2015: +1.1 (4.5, n 136); 2016: +3.9 (4.8, n 133); 2017: +2.0 (2.9, n 136); 2018: -3.1 (5.0, n 121); 2019: +4.9 (4.5, n 131); 2020: -10.5 (8.1, n 117); 2021: +5.7 (4.0, n 134); 2022: -0.2 (9.9, n 140); 2023: +6.9 (4.1, n 156); 2024: -2.9 (3.6, n 145); 2025: +2.9 (5.2, n 138); 2026: +1.3 (5.2, n 125)
* NQ nyam: 2013: -17.5 (15.6, n 154); 2014: -3.4 (18.7, n 167); 2015: -10.0 (20.6, n 144); 2016: -3.7 (16.1, n 169); 2017: -27.2 (14.4, n 168); 2018: +10.3 (23.9, n 160); 2019: +38.6 (20.7, n 157); 2020: +37.8 (31.8, n 159); 2021: -33.7 (24.1, n 164); 2022: +3.2 (38.7, n 176); 2023: +12.6 (21.6, n 181); 2024: -12.7 (18.0, n 161); 2025: -49.0 (32.8, n 163); 2026: +31.7 (24.2, n 141)
* NQ pre: 2013: +6.6 (40.0, n 13); 2014: -1.9 (35.9, n 17); 2015: +22.4 (60.0, n 20); 2016: -22.4 (43.2, n 14); 2017: -24.8 (27.9, n 19); 2018: -55.1 (74.9, n 14); 2019: +100.3 (60.2, n 19); 2020: +9.7 (87.8, n 22); 2021: -40.5 (38.9, n 20); 2022: +106.3 (83.5, n 38); 2023: -47.7 (47.4, n 44); 2024: +22.1 (32.4, n 37); 2025: +60.9 (46.4, n 25); 2026: +21.8 (38.9, n 27)
* RTY pre: 2018: -42.2 (25.7, n 6); 2019: +29.6 (13.4, n 8); 2020: +107.8 (63.5, n 5); 2021: -59.1 (16.9, n 12); 2022: +81.9 (19.1, n 22); 2023: +20.9 (23.9, n 25); 2024: -8.3 (17.2, n 45); 2025: -34.2 (15.2, n 29); 2026: -2.3 (21.5, n 22)
Reading: no year before 2023 is distinguishable from zero for ES (every |mean| < 1.5 se except none) and the RTY pre-market proxy has 5-45 events per year with se 13-64 ticks; NQ nyam/pre bounce between +-40 ticks with se 15-80. There is no pre-2023 evidence for or against the effect; the 2024-26 RTY proxy means are -8 / -34 / -2 ticks (30 min), opposite in sign to the 1-s events, i.e. the proxy does not reproduce the 1-s result (weekly corr .74-.77), so it cannot be used to extend the sample.

### (3) RTY book anatomy
Trade counts: 95 trades in 34 of 39 months (2024: 45, 2025: 28, 2026: 22, none in 2023 because the causal scale needs 10 prior events: the first 10 touches (Aug-Dec 2023, ~10 events) are burn-in). X' (2023-04..2024-01, data only from 2023-08) therefore holds 3 trades, all in 2024-01, total -$2,216 (m1.0) / -$507 (m1.5) at 1 lot-equal-risk: X' 'negative' is 3 trades in one month, not a regime. Burn-in 5 events does not change HOLD>0 share (0.69 / 0.91) or the count (~100). Per cell (m1.5, no target, 1800 s): L1M +1113, L6M +605, HOLD +179, MID -293, PRE +53, X' -22 $/wk; by year net $ 2024 +4,987, 2025 -3,522, 2026 +6,269 (not persistent by year). Walk-forward of its own parameters: positive for m1.5/1800 s (6 m: +$72/wk OOS, p_rand .27; 12 m: +$28/wk, p_rand .50) but negative for m1.0/300 s (-$18 / -$15). Placebo p_book .12-.87 (best .12, m2.0/1800 s); family p 1.00 over the 12 RTY cells. Correlation to the NQ stack: |corr| <= .09 (V0 and V2, daily/weekly). Stack Calmar with carry dropped: dCalmar HOLD +0.013, L6M +0.050 at k*=5, but MID -0.031 and PRE -0.024 (not up in all windows). Tolerant gate: fails on min sample (L3M trades 7/10, L6M 13/20, PRE 57/60).

### (4) Passive-entry variant: ZL-2's 1b-d queue model had not landed in MORNING.md at scoring time; NOT run (no own queue model substituted, to keep to the prereg). To be added when it lands.

LABEL: REGIME / WATCH. RTY pre-market prior-day-level continuation after a burst is a real tick-scale effect with a plateau in the 1-s book on 2023-08..2026-10 and zero correlation to the NQ stack, but it has ~100 trades, placebo p_book .12+, family p 1.0, no calibrated pre-2023 evidence and unstable yearly sign; it does not clear. ES and NQ-control map rows do not survive the 1-s book.

## 1b-a - L2 depth imbalance, microprice and order-flow imbalance at 1/5/15/60 s (ZL-1; prereg l2vast/ds3/prereg/FIND_1BA_prereg.md; library l1ba.py; 1-s mbp-10 tables, 2023-08..2026-10-30, NO pre-2023 evidence)

Design: 12 features x 4 horizons x (23 ET hours + 6 sessions) x 2 extreme classes = 2,784 cells per instrument; classes (10%/90% per half-hour) and the direction of each cell are frozen on DISCOVERY 2023-08..2025-06 and scored once on TEST 2025-07..2026-10; costs = measured half-spread at entry and exit + $4.84 fee, entry 1 s after the decision; null = days permuted within calendar month (200 worlds), Westfall-Young max-z over all cells of the instrument. A row beats the null only if p_family <= .10 AND net > 0 AND gross > 0 in discovery and test.

### ES
Scored cells 2784; cells with family p <= .10: 370 (gross structure real vs the shuffled null); cells with test net > 0: 0; rows that BEAT the null (p <= .10, net > 0 both halves): 0. Null maximum z median 3.28, 95th percentile 4.01. Median quoted spread 1.00 ticks, fee 0.39 ticks, so a taker round trip costs about 1.39 ticks (spread + fee) before any slippage beyond the touch.

| session | h s | best gross ticks (test, frozen dir) | feature / class | its net ticks | its p_family | best net ticks in session | feature / class |
|--|--|--|--|--|--|--|--|
| asia | 1 | +0.042 | imb1 e0 | -1.48 | 0.005 | -1.48 | imb1 e0 |
| asia | 5 | +0.087 | imb1 e0 | -1.43 | 0.005 | -1.43 | imb1 e0 |
| asia | 15 | +0.096 | imb1 e1 | -1.43 | 0.005 | -1.43 | imb1 e1 |
| asia | 60 | +0.090 | micro_dev e1 | -1.45 | 0.005 | -1.43 | imb1 e1 |
| london | 1 | +0.036 | imb1 e1 | -1.49 | 0.005 | -1.49 | imb1 e0 |
| london | 5 | +0.065 | imb1 e1 | -1.46 | 0.005 | -1.46 | imb1 e0 |
| london | 15 | +0.079 | micro_dev e1 | -1.46 | 0.005 | -1.45 | imb1 e1 |
| london | 60 | +0.108 | micro_dev e1 | -1.43 | 0.005 | -1.42 | imb5 e1 |
| pre | 1 | +0.027 | micro_dev e0 | -1.48 | 1.000 | -1.46 | imb1 e0 |
| pre | 5 | +0.043 | ofi1_w5 e0 | -1.44 | 0.383 | -1.44 | ofi5_w1 e0 |
| pre | 15 | +0.117 | ofi5_w15 e1 | -1.37 | 1.000 | -1.37 | ofi5_w15 e1 |
| pre | 60 | +0.274 | ofi5_w15 e1 | -1.21 | 1.000 | -1.21 | ofi5_w15 e1 |
| nyam | 1 | +0.011 | imb5 e1 | -1.43 | 1.000 | -1.42 | ofi1_w5 e1 |
| nyam | 5 | +0.026 | imb10 e1 | -1.42 | 1.000 | -1.41 | ofi1_w1 e0 |
| nyam | 15 | +0.072 | imb10 e1 | -1.37 | 1.000 | -1.36 | ofi1_w60 e1 |
| nyam | 60 | +0.129 | ofi5_w60 e1 | -1.30 | 1.000 | -1.30 | ofi5_w60 e1 |
| nypm | 1 | +0.015 | micro_dev e0 | -1.41 | 0.030 | -1.40 | ofi5_w1 e0 |
| nypm | 5 | +0.032 | imb1 e0 | -1.39 | 0.005 | -1.39 | imb1 e0 |
| nypm | 15 | +0.033 | micro_dev e1 | -1.43 | 1.000 | -1.39 | ofi1_w15 e1 |
| nypm | 60 | +0.130 | imb10 e1 | -1.31 | 1.000 | -1.29 | ofi1_w60 e1 |
| close | 1 | +0.030 | micro_dev e1 | -1.41 | 0.005 | -1.40 | imb1 e1 |
| close | 5 | +0.058 | micro_dev e0 | -1.38 | 0.005 | -1.37 | imb1 e1 |
| close | 15 | +0.077 | ofi5_w60 e1 | -1.35 | 0.965 | -1.35 | ofi5_w60 e1 |
| close | 60 | +0.317 | imb10 e0 | -1.13 | 0.672 | -1.13 | imb10 e0 |

Best six cells by test net: imb10 h60 h15 e0: gross disc +0.010 test +0.380 net -1.05 z 1.9 p 1.000 (n 26726); ofi5_w60 h60 h09 e1: gross disc +0.176 test +0.359 net -1.09 z 1.9 p 1.000 (n 36083); imb10 h60 s_close e0: gross disc +0.070 test +0.317 net -1.13 z 3.1 p 0.672 (n 74558); imb10 h60 h16 e1: gross disc +0.086 test +0.300 net -1.16 z 2.6 p 0.995 (n 51225); imb5 h60 h16 e1: gross disc +0.131 test +0.291 net -1.17 z 3.5 p 0.328 (n 49637); ofi5_w60 h60 h14 e0: gross disc +0.051 test +0.245 net -1.17 z 1.9 p 1.000 (n 38951)

**ES: the thing it does is that depth imbalance, microprice deviation and order flow at 1-60 s carry a small real forward mid-price signal (best frozen test gross 0.38 ticks; 370 cells beat the shuffled-day family null on gross structure); the book that fits would be a 1-60 s taker book, and it does not clear because a taker round trip costs about 1.4 ticks (spread 1.00 + fee 0.39) against that gross, best test net -1.05 ticks, 0 cells with net > 0.**

### RTY
Scored cells 2784; cells with family p <= .10: 265 (gross structure real vs the shuffled null); cells with test net > 0: 0; rows that BEAT the null (p <= .10, net > 0 both halves): 0. Null maximum z median 3.19, 95th percentile 3.96. Median quoted spread 2.00 ticks, fee 0.97 ticks, so a taker round trip costs about 2.97 ticks (spread + fee) before any slippage beyond the touch.

| session | h s | best gross ticks (test, frozen dir) | feature / class | its net ticks | its p_family | best net ticks in session | feature / class |
|--|--|--|--|--|--|--|--|
| asia | 1 | +0.050 | imb1 e0 | -3.30 | 0.005 | -3.30 | imb1 e1 |
| asia | 5 | +0.122 | imb1 e0 | -3.24 | 0.005 | -3.24 | imb1 e0 |
| asia | 15 | +0.158 | imb1 e0 | -3.21 | 0.005 | -3.21 | imb1 e0 |
| asia | 60 | +0.181 | imb1 e0 | -3.20 | 0.005 | -3.20 | imb1 e0 |
| london | 1 | +0.043 | imb1 e1 | -3.23 | 0.005 | -3.23 | imb1 e1 |
| london | 5 | +0.089 | imb1 e1 | -3.20 | 0.005 | -3.20 | imb1 e1 |
| london | 15 | +0.095 | imb1 e1 | -3.20 | 0.005 | -3.20 | imb1 e1 |
| london | 60 | +0.186 | imb10 e0 | -3.30 | 0.975 | -3.15 | imb1 e1 |
| pre | 1 | +0.036 | micro_dev e1 | -3.28 | 1.000 | -3.01 | imb1 e0 |
| pre | 5 | +0.075 | ofi1_w15 e1 | -3.01 | 0.965 | -2.98 | imb1 e0 |
| pre | 15 | +0.156 | ofi1_w60 e1 | -2.93 | 1.000 | -2.93 | ofi1_w15 e1 |
| pre | 60 | +0.263 | ofi1_w60 e1 | -2.81 | 1.000 | -2.81 | ofi1_w15 e1 |
| nyam | 1 | +0.015 | ofi5_w5 e0 | -2.65 | 0.005 | -2.64 | ofi5_w60 e0 |
| nyam | 5 | +0.048 | ofi1_w60 e0 | -2.62 | 0.005 | -2.61 | ofi5_w60 e0 |
| nyam | 15 | +0.135 | ofi1_w60 e0 | -2.53 | 0.050 | -2.53 | ofi1_w60 e0 |
| nyam | 60 | +0.266 | ofi1_w60 e0 | -2.40 | 1.000 | -2.40 | ofi1_w60 e0 |
| nypm | 1 | +0.014 | imb5 e0 | -2.83 | 1.000 | -2.55 | imb1 e1 |
| nypm | 5 | +0.028 | imb5 e0 | -2.82 | 1.000 | -2.56 | imb1 e1 |
| nypm | 15 | +0.050 | imb5 e0 | -2.80 | 1.000 | -2.55 | imb1 e1 |
| nypm | 60 | +0.079 | imb10 e0 | -2.79 | 1.000 | -2.52 | ofi5_w60 e0 |
| close | 1 | +0.018 | micro_dev e0 | -2.73 | 1.000 | -2.49 | imb1 e0 |
| close | 5 | +0.049 | micro_dev e0 | -2.69 | 1.000 | -2.49 | imb1 e1 |
| close | 15 | +0.098 | micro_dev e0 | -2.64 | 1.000 | -2.46 | imb1 e0 |
| close | 60 | +0.157 | micro_dev e0 | -2.58 | 1.000 | -2.42 | imb1 e1 |

Best six cells by test net: ofi1_w60 h60 h09 e0: gross disc +0.107 test +0.656 net -2.14 z 2.3 p 1.000 (n 69484); ofi1_w15 h60 h09 e0: gross disc +0.025 test +0.597 net -2.20 z 3.7 p 0.154 (n 71887); ofi5_w15 h60 h09 e0: gross disc +0.071 test +0.553 net -2.24 z 3.1 p 0.567 (n 61091); ofi5_w60 h60 h09 e0: gross disc +0.136 test +0.516 net -2.28 z 1.4 p 1.000 (n 57825); imb10 h60 h09 e0: gross disc +0.101 test +0.561 net -2.36 z 2.1 p 1.000 (n 48182); imb10 h60 h14 e1: gross disc +0.030 test +0.303 net -2.36 z 1.2 p 1.000 (n 51840)

**RTY: the thing it does is that depth imbalance, microprice deviation and order flow at 1-60 s carry a small real forward mid-price signal (best frozen test gross 0.66 ticks; 265 cells beat the shuffled-day family null on gross structure); the book that fits would be a 1-60 s taker book, and it does not clear because a taker round trip costs about 3.0 ticks (spread 2.00 + fee 0.97) against that gross, best test net -2.14 ticks, 0 cells with net > 0.**

### NQ
Scored cells 2784; cells with family p <= .10: 29 (gross structure real vs the shuffled null); cells with test net > 0: 0; rows that BEAT the null (p <= .10, net > 0 both halves): 0. Null maximum z median 3.25, 95th percentile 3.89. Median quoted spread 3.00 ticks, fee 0.97 ticks, so a taker round trip costs about 3.97 ticks (spread + fee) before any slippage beyond the touch.

| session | h s | best gross ticks (test, frozen dir) | feature / class | its net ticks | its p_family | best net ticks in session | feature / class |
|--|--|--|--|--|--|--|--|
| asia | 1 | +0.035 | imb1 e0 | -5.08 | 1.000 | -4.93 | imb5 e0 |
| asia | 5 | +0.058 | micro_dev e0 | -5.72 | 1.000 | -4.92 | imb5 e0 |
| asia | 15 | +0.101 | micro_dev e1 | -5.50 | 1.000 | -4.89 | imb1 e1 |
| asia | 60 | +0.350 | ofi1_w60 e1 | -5.16 | 1.000 | -4.82 | imb5 e0 |
| london | 1 | +0.020 | ofi1_w15 e1 | -5.16 | 1.000 | -4.71 | imb5 e0 |
| london | 5 | +0.041 | imb1 e0 | -4.74 | 0.358 | -4.71 | imb5 e0 |
| london | 15 | +0.155 | ofi5_w15 e0 | -4.96 | 1.000 | -4.75 | imb10 e0 |
| london | 60 | +0.222 | ofi1_w60 e1 | -4.96 | 1.000 | -4.64 | imb5 e0 |
| pre | 1 | +0.043 | ofi5_w15 e0 | -4.35 | 1.000 | -4.00 | imb1 e1 |
| pre | 5 | +0.212 | ofi5_w60 e1 | -4.19 | 1.000 | -3.95 | imb1 e0 |
| pre | 15 | +0.518 | ofi5_w15 e1 | -3.87 | 1.000 | -3.79 | imb1 e0 |
| pre | 60 | +1.276 | ofi5_w15 e1 | -3.09 | 1.000 | -3.09 | ofi5_w15 e1 |
| nyam | 1 | +0.027 | ofi1_w15 e1 | -3.82 | 1.000 | -3.56 | imb1 e1 |
| nyam | 5 | +0.121 | ofi5_w1 e1 | -3.72 | 0.995 | -3.52 | imb1 e1 |
| nyam | 15 | +0.330 | ofi1_w15 e0 | -3.61 | 1.000 | -3.47 | imb1 e1 |
| nyam | 60 | +1.257 | ofi1_w60 e1 | -2.56 | 1.000 | -2.56 | ofi1_w60 e1 |
| nypm | 1 | +0.019 | imb5 e1 | -4.04 | 1.000 | -3.53 | ofi5_w1 e0 |
| nypm | 5 | +0.091 | ofi5_w15 e1 | -3.45 | 0.980 | -3.45 | ofi5_w15 e1 |
| nypm | 15 | +0.120 | ofi5_w1 e0 | -3.42 | 0.149 | -3.42 | ofi5_w1 e0 |
| nypm | 60 | +0.302 | imb10 e0 | -3.81 | 1.000 | -3.40 | ofi5_w1 e0 |
| close | 1 | +0.037 | ofi1_w15 e1 | -3.99 | 1.000 | -3.55 | imb1 e0 |
| close | 5 | +0.110 | imb10 e1 | -3.89 | 1.000 | -3.52 | imb1 e0 |
| close | 15 | +0.361 | ofi5_w60 e1 | -3.64 | 1.000 | -3.49 | imb1 e1 |
| close | 60 | +0.397 | ofi5_w60 e1 | -3.60 | 1.000 | -3.27 | imb1 e1 |

Best six cells by test net: ofi1_w60 h60 h09 e0: gross disc +0.515 test +2.790 net -1.46 z 2.9 p 0.881 (n 81525); ofi1_w60 h60 h13 e1: gross disc +0.042 test +1.107 net -2.45 z 1.6 p 1.000 (n 73671); ofi1_w60 h60 h10 e1: gross disc +1.074 test +1.422 net -2.45 z 1.2 p 1.000 (n 79850); ofi1_w60 h60 s_nyam e1: gross disc +0.548 test +1.257 net -2.56 z 1.8 p 1.000 (n 206069); ofi5_w15 h60 h14 e1: gross disc +0.698 test +0.971 net -2.58 z 1.5 p 1.000 (n 50254); ofi5_w5 h60 h14 e1: gross disc +0.407 test +0.844 net -2.70 z 1.6 p 1.000 (n 55056)

**NQ: the thing it does is that depth imbalance, microprice deviation and order flow at 1-60 s carry a small real forward mid-price signal (best frozen test gross 2.79 ticks; 29 cells beat the shuffled-day family null on gross structure); the book that fits would be a 1-60 s taker book, and it does not clear because a taker round trip costs about 4.0 ticks (spread 3.00 + fee 0.97) against that gross, best test net -1.46 ticks, 0 cells with net > 0.**

(1b-a correction note, ZL-1: the "median quoted spread" in the three 1b-a blocks above was sampled over 18:00-10:40 ET and so mixes the wider overnight book. Over RTH 09:30-16:00 ET the median quoted spread is ES 1.0 tick, RTY 2.0 ticks, NQ 2.0 ticks (mean 1.04 / 1.75 / 2.65); with the fee ($4.84 = 0.39 / 0.97 / 0.97 ticks) a taker round trip costs about ES 1.4, RTY 3.0, NQ 3.0 ticks in RTH. The cell nets use the measured spread at each fill, so the table values are unaffected; only the sentence's cost figure is.)

## 1b-d - queue-position-aware PASSIVE entries and exits (maker side) on the 1b-a gross-structure cells (ZL-1; prereg l2vast/ds3/prereg/FIND_1BD_prereg.md + addendum 1; library maker.py, maker_study.py; events_L13 store, RTH only, 2023-08..2026-10, NO pre-2023 evidence)

Model: join the touch on the side of the frozen direction, arrival 1.0 s after the decision (ts is the bin END), queue ahead = displayed touch size at arrival, trades at our price deplete it, fill-removal rows are matched before any cancel is counted, cancels ahead proportional (sensitivities none / all), timeout 2h, adverse cancel at -1 tick (+1 s latency); after the fill hold h s, exit passive at the opposite touch (wait h s, then taker fallback). Net = captured half-spread - adverse selection - fee $4.84, per ORDER PLACED (unfilled count 0). Null = the same orders shifted forward 120-1800 s on the same day, 100 worlds, Westfall-Young max-z over the selected cells; a cell beats the null only if p_family <= .10 on the test half AND per-order net > 0 in BOTH halves AND >= 300 test fills.

### ES (28 cells selected from the 2784 1b-a cells with family p <= .10, positive gross in both halves, RTH groups; 493 discovery / 346 test days with events)
Per filled order, test half, fill-weighted mean over the selected cells (ticks): captured half-spread +0.49; adverse selection after the fill at +1 s -0.51, +5 s -0.49, +h -0.45; fee -0.39; net per fill (passive exit) -0.53, (taker exit) see column; fill rate 0.73; net per ORDER PLACED -0.35 (discovery -0.44). Cells with net per order > 0: test 1 of 28, discovery 0 of 28, both 0. Cells that BEAT the null: 0. Null max z median 2.00, 95th percentile 2.74.

Sensitivities (test, mean net per order over cells): proportional cancels -0.36; no cancel benefit (conservative) -0.48; all cancels ahead (optimistic) -0.26; join one tick back -0.09 (fill rate 0.20); taker exit instead of passive exit -0.60.

| group | cells | mean fill rate | mean net/order test | best net/order test | mean net/fill |
|--|--|--|--|--|--|
| h12 | 1 | 0.57 | -0.47 | -0.47 | -0.82 |
| h13 | 4 | 0.63 | -0.40 | -0.37 | -0.65 |
| h14 | 2 | 0.75 | -0.43 | -0.37 | -0.58 |
| s_close | 13 | 0.74 | -0.36 | +0.50 | -0.53 |
| s_nypm | 8 | 0.64 | -0.33 | -0.19 | -0.55 |

Top five by z: ofi5_w5 h60 s_close e1: test net/order +0.50 (disc -0.22), fill 0.94, z 4.0, p_family 0.010; imb1 h5 s_nypm e0: test net/order -0.26 (disc -0.39), fill 0.75, z 2.4, p_family 0.168; imb1 h15 s_nypm e1: test net/order -0.19 (disc -0.44), fill 0.86, z 2.0, p_family 0.535; micro_dev h1 s_nypm e0: test net/order -0.32 (disc -0.38), fill 0.47, z 1.7, p_family 0.802; ofi5_w1 h1 s_nypm e0: test net/order -0.33 (disc -0.42), fill 0.54, z 1.6, p_family 0.802
Cells with p_family <= .10 that FAIL the both-halves rule (test-half only, not leads): ofi5_w5 h60 s_close e1: test +0.50, discovery -0.22

**ES: the thing it does is that the 1-60 s L2 structure is real but small, and a passive order captures only the half-spread (+0.49 ticks per fill); adverse selection after the fill (-0.45 ticks at +h) and the fee (-0.39) take more than that, so net is -0.53 ticks per fill and -0.35 per order placed; the book that fits would be a queue-aware maker book at the touch, and it does not clear because 0 of 28 selected cells beat the null (net positive in both halves and family p <= .10).**

### RTY (94 cells selected from the 2784 1b-a cells with family p <= .10, positive gross in both halves, RTH groups; 488 discovery / 343 test days with events)
Per filled order, test half, fill-weighted mean over the selected cells (ticks): captured half-spread +0.38; adverse selection after the fill at +1 s -0.63, +5 s -0.58, +h -0.57; fee -0.97; net per fill (passive exit) -1.65, (taker exit) see column; fill rate 0.60; net per ORDER PLACED -0.97 (discovery -0.96). Cells with net per order > 0: test 1 of 94, discovery 0 of 94, both 0. Cells that BEAT the null: 0. Null max z median 2.39, 95th percentile 2.97.

Sensitivities (test, mean net per order over cells): proportional cancels -0.95; no cancel benefit (conservative) -0.92; all cancels ahead (optimistic) -0.94; join one tick back -0.46 (fill rate 0.30); taker exit instead of passive exit -1.13.

| group | cells | mean fill rate | mean net/order test | best net/order test | mean net/fill |
|--|--|--|--|--|--|
| h09 | 7 | 0.77 | -1.01 | +0.01 | -1.33 |
| h10 | 9 | 0.58 | -1.03 | -0.89 | -1.78 |
| h11 | 1 | 0.64 | -1.00 | -1.00 | -1.57 |
| h12 | 7 | 0.48 | -0.86 | -0.73 | -1.83 |
| h13 | 18 | 0.52 | -0.87 | -0.61 | -1.70 |
| h14 | 1 | 0.35 | -0.67 | -0.67 | -1.94 |
| h15 | 1 | 0.42 | -0.73 | -0.73 | -1.72 |
| s_close | 8 | 0.65 | -0.90 | -0.63 | -1.42 |
| s_nyam | 21 | 0.64 | -1.07 | -0.78 | -1.70 |
| s_nypm | 21 | 0.51 | -0.90 | -0.60 | -1.81 |

Top five by z: ofi1_w60 h15 h09 e0: test net/order +0.01 (disc -0.66), fill 0.84, z 4.8, p_family 0.010; ofi5_w1 h5 s_nyam e0: test net/order -0.83 (disc -1.11), fill 0.66, z 2.5, p_family 0.386; ofi5_w5 h15 h13 e0: test net/order -0.61 (disc -0.73), fill 0.67, z 2.5, p_family 0.406; ofi5_w60 h1 h09 e0: test net/order -0.93 (disc -1.08), fill 0.69, z 2.3, p_family 0.574; ofi1_w60 h15 s_nyam e0: test net/order -0.78 (disc -0.91), fill 0.73, z 2.3, p_family 0.604
Cells with p_family <= .10 that FAIL the both-halves rule (test-half only, not leads): ofi1_w60 h15 h09 e0: test +0.01, discovery -0.66

**RTY: the thing it does is that the 1-60 s L2 structure is real but small, and a passive order captures only the half-spread (+0.38 ticks per fill); adverse selection after the fill (-0.57 ticks at +h) and the fee (-0.97) take more than that, so net is -1.65 ticks per fill and -0.97 per order placed; the book that fits would be a queue-aware maker book at the touch, and it does not clear because 0 of 94 selected cells beat the null (net positive in both halves and family p <= .10).**

### NQ (8 cells selected from the 2784 1b-a cells with family p <= .10, positive gross in both halves, RTH groups; 493 discovery / 346 test days with events)
Per filled order, test half, fill-weighted mean over the selected cells (ticks): captured half-spread +0.38; adverse selection after the fill at +1 s -0.88, +5 s -1.24, +h -1.02; fee -0.97; net per fill (passive exit) -2.57, (taker exit) see column; fill rate 0.69; net per ORDER PLACED -1.79 (discovery -1.45). Cells with net per order > 0: test 0 of 8, discovery 0 of 8, both 0. Cells that BEAT the null: 0. Null max z median 1.31, 95th percentile 2.44.

Sensitivities (test, mean net per order over cells): proportional cancels -1.77; no cancel benefit (conservative) -2.10; all cancels ahead (optimistic) -1.77; join one tick back -1.33 (fill rate 0.54); taker exit instead of passive exit -2.05.

| group | cells | mean fill rate | mean net/order test | best net/order test | mean net/fill |
|--|--|--|--|--|--|
| h11 | 1 | 0.69 | -1.74 | -1.74 | -2.51 |
| h12 | 1 | 0.66 | -1.44 | -1.44 | -2.17 |
| h13 | 1 | 0.75 | -1.87 | -1.87 | -2.48 |
| h14 | 1 | 0.59 | -1.58 | -1.58 | -2.68 |
| h15 | 1 | 0.65 | -1.66 | -1.66 | -2.56 |
| s_close | 2 | 0.72 | -1.91 | -1.73 | -2.65 |
| s_nyam | 1 | 0.72 | -2.08 | -2.08 | -2.87 |

Top five by z: imb1 h1 h12 e1: test net/order -1.44 (disc -1.36), fill 0.66, z 0.7, p_family 0.881; imb1 h1 h11 e0: test net/order -1.74 (disc -1.74), fill 0.69, z 0.1, p_family 0.990; imb1 h1 s_nyam e1: test net/order -2.08 (disc -1.58), fill 0.72, z -0.3, p_family 1.000; imb1 h1 h14 e0: test net/order -1.58 (disc -1.29), fill 0.59, z -0.4, p_family 1.000; imb1 h1 h15 e0: test net/order -1.66 (disc -1.35), fill 0.65, z -0.7, p_family 1.000

**NQ: the thing it does is that the 1-60 s L2 structure is real but small, and a passive order captures only the half-spread (+0.38 ticks per fill); adverse selection after the fill (-1.02 ticks at +h) and the fee (-0.97) take more than that, so net is -2.57 ticks per fill and -1.79 per order placed; the book that fits would be a queue-aware maker book at the touch, and it does not clear because 0 of 8 selected cells beat the null (net positive in both halves and family p <= .10).**

BLOCKED (not a negative result): CHAR-A's RTY pre-market prior-day-level + burst continuation (and any pre-09:30 or overnight cell): the events_L13 store has RTH events only, so a queue simulation is impossible; re-reducing the kept raw months with l2v_reduce.py --night would unblock it (cost: compute only).

## 1b-d (maker side) - RTY and NQ runs of ZL-1's queue-position model (Z1, 2026-11-06)
ZL-1 owns the model and prereg (FIND_1BD_prereg.md sha256 3097a16a2a85559fba0eeb09d346dc8136fa4e29214a52962bb99483b66f923f, addendum 1 ec914d67...); I ran maker_study.py unchanged (W = 100 forward-shift worlds, K = 4 orders per cell and day, truncation 24/24 on RTY and 24/24 on NQ before any number was read). Event store = RTH only, 2023-08..2026-10-30, no pre-2023 evidence; tick data begin 2023-08. Discovery half 2023-08..2025-06, test half 2025-07..2026-10.
| instrument | 1b-a cells selected (family p <= .10, gross > 0 both halves, RTH group) | median fill rate | median net per order placed (test, exit P) | median capture / adverse at h per fill (ticks) | cells net > 0 test / both halves | cells with p_family <= .10 | cells that BEAT the null |
|---|---|---|---|---|---|---|---|
| RTY | 94 of 2,784 | 0.58 | -0.94 | +0.38 / -0.62 | 1 / 0 | 1 | 0 |
| NQ | 8 of ~2,800 | 0.68 | -1.73 | +0.38 / -0.93 | 0 / 0 | 0 | 0 |
The one RTY cell with p_family .01 (ofi1 w60, h 15, ET 09, long) is +0.011 ticks per order in the test half and -0.66 in discovery: it beats the null but not zero. Reading: the passive side captures about 0.4 tick of spread per fill but pays about 0.6-0.9 tick adverse selection over the hold, misses 30-40% of fills, and still pays the fee, so the 1b-a gross structure is not tradeable passively either (RTY -0.9, NQ -1.7 ticks per order placed). No book is built.
**CHAR-A prior-day-level continuation:** RTY pre-market (08:30-09:30 ET) is BLOCKED: the event store holds RTH events only (09:30-16:00), the passive model cannot be run there (needs a re-reduction with the night option). NQ nyam (CHAR-A 1b-DEEP base node: burst q .90, buffer 0, 598 events 2023-08..2026-10, selected as one row of 240): the same model, unchanged, applied to those events with hold 30 / 60 / 300 s (order at the touch second, direction = continuation, joins the touch, same forward-shift null, W = 100):
| hold s | placed (disc / test) | fills test | net per order disc | net per order test | null mean test | z test | p_family test (3 cells) | taker net per order test |
|---|---|---|---|---|---|---|---|---|
| 30 | 274 / 175 | 156 | +4.61 | +5.40 | -2.75 | 2.1 | 0.069 | +4.33 |
| 60 | 274 / 175 | 156 | +6.96 | +2.61 | -3.01 | 1.1 | 0.337 | +4.87 |
| 300 | 274 / 175 | 158 | +13.45 | +1.82 | -1.86 | 0.4 | 0.713 | -0.87 |
Fill rate 0.89 (most orders fill because price runs through the level); capture +0.73 tick, adverse over the hold +4.8 .. +15 (disc) and +6.8 / +7.3 / +0.1 (test), i.e. the touch continuation is real in the sample but the passive entry adds about the same as a taker entry (taker +4.3 / +4.9 at 30 / 60 s). The prereg rule 'fills >= 300 in the test half' fails (156), so formally no cell beats the null; the 30-s node is the only one with p_family <= .10 in test (0.069) and discovery (0.020). It rests on 175 test orders from one selected row of 240 (selection bias, noted by CHAR-A), and CHAR-A's 1-s book for the same row is negative at HOLD (median -$144/wk). Label: WATCH (underpowered, unconfirmed), not a lead; no PASS claim.

### 1b-d fee sensitivity (ZL-1): what per-side fee would make the passive model break even?
Pre-fee result = net ticks per fill (passive exit, test half) + the $4.84 round-trip fee in ticks; break-even fee = pre-fee ticks x tick value, per side = half of it. A NEGATIVE break-even fee means the model loses even at zero fee and would need a rebate of that size per side.

| instrument | cells | fee now ($ RT) | pre-fee net per fill (ticks) | break-even round-trip fee ($) | break-even per side ($) | pre-fee net per ORDER placed (ticks) | break-even per side on per-order basis ($) | best single cell pre-fee per fill (ticks) / per side ($) |
|--|--|--|--|--|--|--|--|--|
| ES | 28 | 4.84 | -0.14 | -1.77 | -0.88 | -0.10 | -0.61 | +0.92 / +5.72 |
| RTY | 94 | 4.84 | -0.68 | -3.41 | -1.70 | -0.39 | -0.98 | +0.98 / +2.45 |
| NQ | 8 | 4.84 | -1.61 | -8.03 | -4.02 | -1.11 | -2.77 | -1.20 / -3.01 |

# RV block - relative-value spread character maps (CHAR-B, 2026-11-06). Prereg l2vast/ds3/prereg/FIND_RV_prereg.md sha256 fa5c5c13e62de0d398fd0a27c2e76f437fa60d703cb60042fb7813fa2e933b6c + addendum1 (integer hedge unit). Pairs ES-RTY, ES-YM, RTY-YM, ZN-ZB, 6E-6J; GC-CL descriptive only. Q14 (NQ-vs-ES, dead) and DISC_A not repeated.

## RV ESRTY - relative-value spread character map (CHAR-B via char_lib, 2026-11-06T01:13Z)
Base: RV_ESRTY CME front-month (.v.0) 1-min bars from 2017-01 to 2026-10, percent frame (multiplicative roll-adjusted), 1-min approximation (no tick path), 2143 usable label days; ET clock, sessions asia 18:00-02:00 / london 02:00-08:30 / pre 08:30-09:30 / nyam 09:30-12:00 / nypm 12:00-15:00 / close 15:00-16:55. Nulls: within-year shuffled-day (AC B=300; structure B=100 worlds; levels recomputed on the shuffled path; round numbers 60 random grid phases); p_family = Westfall-Young max-|z| over the block (AC family 153 cells, structure family 92 cells). `**` p_family<=.05, `*` <=.10. Prereg sha256 980bedf6bad3f1669de9efb93831fa4622d88577c892d9359b7f57ba93c9dbcf. Descriptive only: no PASS, nothing live.

### Plain paragraph
At 1 minute every session has negative autocorrelation (-0.247 to -0.025; bid-ask bounce / last-print noise, not a tradable edge by itself). asia: reverts at 5/15/30/60 min (-0.133, -0.075, -0.048, -0.037). london: reverts at 5/15/30/60 min (-0.083, -0.047, -0.029, -0.038). pre: reverts at 5 min (-0.057). nyam: reverts at 5 min (-0.015). nypm: reverts at 5/15 min (-0.049, -0.021). close: reverts at 5 min (-0.027). Day types (RTH): 52% trend days (efficiency ratio >= .5; shuffled null 50%, p_fam 0.852), 21% range days (<.25; null 24%, p_fam 0.279); the IB (09:30-10:30) is extended on one side only on 76% of days and on both on 20%, and a one-sided extension closes beyond the IB edge 65% of the time (null 66%). RTH variance ratio at 30 min 0.871 (shuffled null 1.000, p_fam 0.016); Hurst 0.488. The RTH range forms 9:30 (48%), 10:00 (21%), 11:00 (9%) of the range increments. Level reactions that beat the family null: PD|london bounces 47% of touches (more than the shuffled null 40%). Failed-break follow-through beating the null: PD|asia 38% (null 50%). Room (median 3xATR14(5m) $ / round-trip cost $167 per lot): asia 1.7x, london 1.8x, pre 2.3x, nyam 4.8x, nypm 4.0x, close 3.8x (1xATR5 room 1.6x in nyam, 0.6x in asia).

### 1. Autocorrelation of h-min returns (corr(past h, next h), both inside the session), pooled; cell = corr (pre-2023 mean | 2023+ mean) p_family
| session | 1 min | 5 min | 15 min | 30 min | 60 min | 120 min |
|--|--|--|--|--|--|--|
| asia | -0.247 (-0.263|-0.207) p0.003** ys1.00 | -0.133 (-0.163|-0.110) p0.003** ys1.00 | -0.075 (-0.101|-0.069) p0.003** ys1.00 | -0.048 (-0.079|-0.043) p0.003** ys1.00 | -0.037 (-0.053|-0.030) p0.010** ys0.70 | -0.012 (-0.050|-0.002) p1.000 ys0.70 |
| london | -0.178 (-0.240|-0.118) p0.003** ys1.00 | -0.083 (-0.118|-0.065) p0.003** ys1.00 | -0.047 (-0.046|-0.044) p0.003** ys1.00 | -0.029 (-0.030|-0.010) p0.007** ys0.70 | -0.038 (-0.048|-0.031) p0.013** ys1.00 | -0.050 (-0.064|-0.045) p0.053* ys0.90 |
| pre | -0.088 (-0.133|-0.061) p0.003** ys1.00 | -0.057 (-0.065|-0.043) p0.003** ys0.90 | -0.031 (-0.071|-0.001) p0.233 ys0.60 | -0.039 (-0.096|-0.004) p1.000 ys0.80 | - | - |
| nyam | -0.025 (-0.042|-0.019) p0.003** ys1.00 | -0.015 (-0.036|-0.009) p0.030** ys0.90 | +0.004 (-0.029|+0.014) p1.000 ys0.50 | +0.014 (-0.029|+0.027) p1.000 ys0.60 | +0.020 (+0.027|+0.031) p1.000 ys0.50 | - |
| nypm | -0.070 (-0.090|-0.055) p0.003** ys1.00 | -0.049 (-0.065|-0.040) p0.003** ys1.00 | -0.021 (-0.027|+0.006) p0.030** ys0.50 | +0.006 (-0.022|+0.022) p1.000 ys0.40 | +0.014 (-0.080|+0.040) p1.000 ys0.50 | - |
| close | -0.062 (-0.089|-0.037) p0.003** ys1.00 | -0.027 (-0.032|-0.026) p0.003** ys0.90 | -0.009 (-0.040|-0.012) p1.000 ys0.70 | +0.018 (+0.028|-0.009) p1.000 ys0.60 | - | - |

Hour cells (h >= 5) beating the family null, top 14 by |z| (hour = ET hour of the decision bar):
| h | session | hour ET | corr | z | p_family | year sign share | pre-2023 | 2023+ |
|--|--|--|--|--|--|--|--|--|
| 5 | asia | 23 | -0.172 | -40.5 | 0.003 | 1.00 | -0.209 | -0.129 |
| 5 | asia | 00 | -0.160 | -34.1 | 0.003 | 1.00 | -0.198 | -0.125 |
| 5 | asia | 22 | -0.155 | -33.9 | 0.003 | 1.00 | -0.201 | -0.118 |
| 5 | asia | 01 | -0.134 | -28.9 | 0.003 | 1.00 | -0.165 | -0.094 |
| 5 | asia | 21 | -0.119 | -27.3 | 0.003 | 1.00 | -0.157 | -0.099 |
| 5 | asia | 19 | -0.122 | -24.8 | 0.003 | 1.00 | -0.160 | -0.095 |
| 5 | asia | 18 | -0.124 | -24.3 | 0.003 | 1.00 | -0.137 | -0.116 |
| 5 | asia | 20 | -0.116 | -24.0 | 0.003 | 1.00 | -0.140 | -0.112 |
| 5 | london | 02 | -0.101 | -21.3 | 0.003 | 1.00 | -0.152 | -0.076 |
| 5 | london | 06 | -0.085 | -18.1 | 0.003 | 1.00 | -0.142 | -0.065 |
| 5 | london | 07 | -0.094 | -17.9 | 0.003 | 1.00 | -0.110 | -0.081 |
| 5 | london | 05 | -0.083 | -17.6 | 0.003 | 1.00 | -0.096 | -0.059 |
| 5 | london | 03 | -0.072 | -13.8 | 0.003 | 1.00 | -0.116 | -0.060 |
| 5 | nypm | 13 | -0.062 | -13.0 | 0.003 | 1.00 | -0.073 | -0.055 |

### 2. Variance ratio VR(q) and Hurst (1.0 = random walk; <1 reverting; edge-bias corrected), cell = value (null) p_family
| session | VR5 | VR15 | VR30 | VR60 | VR120 | Hurst |
|--|--|--|--|--|--|--|
| asia | 0.562 (0.998) p0.016** | 0.453 (0.998) p0.016** | 0.415 (1.000) p0.016** | 0.393 (1.001) p0.016** | 0.383 (1.001) p0.016** | 0.440 (0.501) p0.016** |
| london | 0.692 (0.998) p0.016** | 0.611 (0.997) p0.016** | 0.582 (0.996) p0.016** | 0.568 (0.996) p0.016** | 0.549 (0.995) p0.016** | 0.464 (0.500) p0.016** |
| pre | 0.826 (0.999) p0.016** | 0.754 (0.999) p0.016** | - | - | - | 0.459 (0.500) p0.016** |
| nyam | 0.950 (1.000) p0.016** | 0.927 (1.000) p0.016** | 0.922 (1.001) p0.016** | - | - | 0.492 (0.500) p0.262 |
| nypm | 0.862 (0.999) p0.016** | 0.805 (0.998) p0.016** | 0.787 (0.997) p0.016** | 0.787 (0.996) p0.016** | - | 0.481 (0.499) p0.016** |
| close | 0.888 (0.998) p0.016** | 0.855 (0.997) p0.016** | 0.859 (0.998) p0.016** | - | - | 0.490 (0.500) p0.557 |
| rth | 0.921 (1.000) p0.016** | 0.885 (0.999) p0.016** | 0.871 (1.000) p0.016** | 0.862 (1.000) p0.016** | 0.855 (1.001) p0.016** | 0.488 (0.500) p0.016** |

### 3. Day types (ex-post labels of the RTH day)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| day|trend | 0.521 | 2143 | 0.499 | +2.2 | 0.852 | 0.70 | 0.498 | 0.521 | REGIME(2023+ only) |
| day|range | 0.211 | 2143 | 0.239 | -2.8 | 0.279 | 0.90 | 0.223 | 0.194 | stable |
| day|er | 0.516 | 2143 | 0.494 | +3.7 | 0.033** | 0.70 | 0.500 | 0.526 | stable |
| day|ib_none | 0.042 | 2143 | 0.032 | +2.5 | 0.574 | 0.60 | 0.037 | 0.053 | stable |
| day|ib_one | 0.759 | 2143 | 0.726 | +3.5 | 0.066* | 0.80 | 0.748 | 0.772 | stable |
| day|ib_both | 0.199 | 2143 | 0.241 | -4.8 | 0.016** | 0.80 | 0.215 | 0.175 | stable |
| day|ib_one_closebeyond | 0.653 | 1626 | 0.657 | -0.4 | 1.000 | 0.60 | 0.640 | 0.654 | stable |

### 4. 1A -> 2A continuation vs give-back-half from the session open (A = 3 x ATR14(5m)); value = P(continue | resolved)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| cont|asia | 0.346 | 800 | 0.409 | -5.3 | 0.016** | 0.90 | 0.319 | 0.352 | stable |
| cont|london | 0.329 | 2122 | 0.439 | -10.9 | 0.016** | 0.90 | 0.285 | 0.356 | stable |
| cont|pre | 0.364 | 1155 | 0.455 | -6.5 | 0.016** | 1.00 | 0.301 | 0.395 | stable |
| cont|nyam | 0.547 | 2129 | 0.530 | +1.6 | 1.000 | 0.70 | 0.550 | 0.557 | stable |
| cont|nypm | 0.307 | 1142 | 0.376 | -5.3 | 0.016** | 1.00 | 0.295 | 0.337 | stable |
| cont|close | 0.370 | 1238 | 0.427 | -4.7 | 0.016** | 0.80 | 0.381 | 0.375 | stable |
| cont|rth | 0.546 | 2141 | 0.530 | +1.6 | 1.000 | 0.60 | 0.550 | 0.556 | stable |

### 5. Gap fill by size bucket (b0 .05-.10, b1 .10-.25, b2 .25-.50, b3 >.50 of the 20-day mean RTH range); day = filled during RTH, h1 = within 60 min
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| gap|b0|day | 0.834 | 253 | 0.848 | -0.6 | 1.000 | 0.50 | 0.868 | 0.838 | REGIME(2023+ only) |
| gap|b0|h1 | 0.755 | 253 | 0.750 | +0.2 | 1.000 | 0.60 | 0.807 | 0.740 | stable |
| gap|b1|day | 0.716 | 666 | 0.746 | -1.6 | 1.000 | 0.60 | 0.683 | 0.754 | stable |
| gap|b1|h1 | 0.589 | 666 | 0.584 | +0.2 | 1.000 | 0.50 | 0.516 | 0.635 | REGIME(2023+ only) |
| gap|b2|day | 0.560 | 598 | 0.547 | +0.8 | 1.000 | 0.50 | 0.546 | 0.581 | REGIME(2023+ only) |
| gap|b2|h1 | 0.363 | 598 | 0.318 | +2.4 | 0.738 | 0.90 | 0.347 | 0.406 | stable |
| gap|b3|day | 0.299 | 371 | 0.262 | +2.2 | 0.852 | 0.70 | 0.298 | 0.309 | stable |
| gap|b3|h1 | 0.100 | 371 | 0.080 | +1.9 | 0.967 | 0.70 | 0.150 | 0.092 | stable |

### 6. Level reaction: first touch -> bounce (0.5A reverse) vs break-through (0.5A beyond) within 60 min; value = P(bounce)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| rx|PD|asia | 0.435 | 543 | 0.385 | +3.1 | 0.197 | 0.90 | 0.454 | 0.410 | stable |
| rx|PD|london | 0.467 | 833 | 0.402 | +3.9 | 0.033** | 0.90 | 0.456 | 0.452 | stable |
| rx|PD|pre | 0.401 | 509 | 0.388 | +0.5 | 1.000 | 0.50 | 0.425 | 0.361 | unstable |
| rx|PD|nyam | 0.340 | 1454 | 0.359 | -1.4 | 1.000 | 0.50 | 0.354 | 0.340 | unstable |
| rx|PD|nypm | 0.426 | 749 | 0.417 | +0.5 | 1.000 | 0.50 | 0.409 | 0.427 | REGIME(2023+ only) |
| rx|PD|close | 0.414 | 527 | 0.390 | +1.1 | 1.000 | 0.70 | 0.464 | 0.432 | stable |
| rx|ON|nyam | 0.320 | 2351 | 0.344 | -2.6 | 0.541 | 0.70 | 0.328 | 0.316 | stable |
| rx|ON|nypm | 0.455 | 1002 | 0.423 | +2.1 | 0.852 | 0.80 | 0.478 | 0.452 | stable |
| rx|ON|close | 0.399 | 724 | 0.392 | +0.4 | 1.000 | 0.60 | 0.469 | 0.367 | stable |
| rx|IB|nyam | 0.429 | 1638 | 0.417 | +1.0 | 1.000 | 0.60 | 0.420 | 0.446 | stable |
| rx|IB|nypm | 0.428 | 1309 | 0.421 | +0.5 | 1.000 | 0.50 | 0.417 | 0.433 | REGIME(2023+ only) |
| rx|IB|close | 0.402 | 909 | 0.394 | +0.4 | 1.000 | 0.50 | 0.393 | 0.392 | unstable |
| rx|VW1|nyam | 0.421 | 2921 | 0.408 | +1.5 | 1.000 | 0.70 | 0.433 | 0.416 | stable |
| rx|VW1|nypm | 0.440 | 2089 | 0.422 | +1.6 | 1.000 | 0.60 | 0.426 | 0.452 | stable |
| rx|VW1|close | 0.431 | 1552 | 0.393 | +3.2 | 0.131 | 0.90 | 0.455 | 0.418 | stable |
| rx|VW2|nyam | 0.416 | 1823 | 0.408 | +0.8 | 1.000 | 0.80 | 0.444 | 0.426 | stable |
| rx|VW2|nypm | 0.461 | 1127 | 0.421 | +2.7 | 0.361 | 0.80 | 0.468 | 0.443 | stable |
| rx|VW2|close | 0.424 | 783 | 0.388 | +2.2 | 0.852 | 0.70 | 0.486 | 0.367 | stable |
| rx|RN|asia | 0.449 | 7865 | 0.451 | -1.3 | 1.000 | 0.60 | 0.451 | 0.446 | REGIME(2023+ only) |
| rx|RN|london | 0.442 | 10011 | 0.442 | -0.2 | 1.000 | 0.70 | 0.445 | 0.435 | REGIME(2023+ only) |
| rx|RN|pre | 0.426 | 2451 | 0.419 | +1.6 | 1.000 | 0.60 | 0.361 | 0.422 | REGIME(2023+ only) |
| rx|RN|nyam | 0.397 | 9868 | 0.400 | -1.4 | 1.000 | 0.60 | 0.401 | 0.396 | REGIME(2023+ only) |
| rx|RN|nypm | 0.437 | 7402 | 0.436 | +0.3 | 1.000 | 0.50 | 0.438 | 0.440 | unstable |
| rx|RN|close | 0.400 | 3437 | 0.404 | -1.1 | 1.000 | 0.50 | 0.413 | 0.400 | REGIME(2023+ only) |

### 7. Failed break (close .25A beyond, back inside within 10 bars): fade follow-through P(0.5A back before 0.5A out)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| fb|PD|asia | 0.377 | 403 | 0.500 | -6.4 | 0.016** | 1.00 | 0.319 | 0.429 | stable |
| fb|PD|london | 0.432 | 669 | 0.500 | -3.6 | 0.066* | 0.80 | 0.412 | 0.436 | stable |
| fb|PD|pre | 0.440 | 373 | 0.501 | -2.1 | 0.918 | 0.90 | 0.411 | 0.437 | stable |
| fb|PD|nyam | 0.468 | 1072 | 0.500 | -2.0 | 0.934 | 0.60 | 0.476 | 0.485 | stable |
| fb|PD|nypm | 0.457 | 564 | 0.497 | -1.8 | 0.984 | 0.80 | 0.466 | 0.432 | stable |
| fb|PD|close | 0.458 | 391 | 0.498 | -1.7 | 0.984 | 0.50 | 0.495 | 0.473 | unstable |
| fb|ON|nyam | 0.488 | 1563 | 0.500 | -0.9 | 1.000 | 0.60 | 0.448 | 0.520 | stable |
| fb|ON|nypm | 0.493 | 755 | 0.497 | -0.2 | 1.000 | 0.50 | 0.489 | 0.513 | unstable |
| fb|ON|close | 0.455 | 527 | 0.498 | -2.0 | 0.934 | 0.70 | 0.475 | 0.423 | stable |
| fb|IB|nyam | 0.455 | 797 | 0.499 | -2.6 | 0.541 | 0.80 | 0.431 | 0.466 | stable |
| fb|IB|nypm | 0.456 | 927 | 0.498 | -2.3 | 0.803 | 0.90 | 0.436 | 0.468 | stable |
| fb|IB|close | 0.451 | 657 | 0.502 | -2.9 | 0.262 | 0.90 | 0.400 | 0.460 | stable |

### 8. Where the range forms
RTH range increments by bin: 9:30 47.9%, 10:00 20.9%, 11:00 9.4%, 12:00 5.6%, 13:00 4.3%, 14:00 4.6%, 15:00 7.1%
Label-day range increments by ET hour (percent of the day): 00h 1.0, 01h 1.3, 02h 2.1, 03h 3.2, 04h 2.9, 05h 2.2, 06h 1.9, 07h 2.2, 08h 4.1, 09h 20.6, 10h 11.9, 11h 6.1, 12h 3.7, 13h 3.0, 14h 3.1, 15h 5.1, 16h 1.7, 18h 11.9, 19h 3.3, 20h 3.5, 21h 2.4, 22h 1.5, 23h 1.1

### 9. Room and liquidity (all years, raw-frame $, 1 lot)
| session | ATR14(5m) $ | A=3xATR5 $ | RT cost $ | room(1 ATR5) | room(A) | median 5-min vol | 1.7% cap (contracts/5min) | lots for $1,200 at 3xATR5 stop |
|--|--|--|--|--|--|--|--|--|
| asia | 94 | 283 | 167 | 0.57 | 1.70 | 36 | 0.0 | 4.2 |
| london | 100 | 299 | 167 | 0.60 | 1.80 | 109 | 0.7 | 4.0 |
| pre | 128 | 385 | 167 | 0.77 | 2.31 | 394 | 2.7 | 3.1 |
| nyam | 265 | 794 | 167 | 1.59 | 4.76 | 1790 | 10.3 | 1.5 |
| nypm | 225 | 675 | 167 | 1.35 | 4.05 | 865 | 4.7 | 1.8 |
| close | 210 | 631 | 167 | 1.26 | 3.79 | 872 | 5.0 | 1.9 |

room(A) by year: asia: 2017:1.2 2018:1.3 2019:1.2 2020:1.6 2021:1.7 2022:1.6 2023:1.5 2024:2.6 2025:2.4 2026:2.5; london: 2017:1.2 2018:1.3 2019:1.2 2020:1.7 2021:1.9 2022:1.6 2023:1.6 2024:3.3 2025:2.9 2026:2.6; pre: 2017:1.3 2018:1.6 2019:1.5 2020:2.0 2021:2.4 2022:1.9 2023:2.3 2024:4.9 2025:4.0 2026:3.3; nyam: 2017:2.5 2018:3.2 2019:3.1 2020:4.0 2021:4.9 2022:4.9 2023:5.0 2024:8.2 2025:7.7 2026:6.9; nypm: 2017:2.3 2018:3.0 2019:2.9 2020:3.5 2021:4.0 2022:3.7 2023:3.9 2024:6.5 2025:5.9 2026:5.0; close: 2017:2.3 2018:3.0 2019:2.7 2020:3.5 2021:3.7 2022:3.4 2023:3.6 2024:6.4 2025:5.3 2026:4.4

### 11. Map rows that become book candidates under the FROZEN rule (p_family <= .05 AND room_A(session) > 2.0)
| map row | direction | stat | p_family | room_A | year sign share | stability | 1.7% cap >= 1 contract/5min in session |
|--|--|--|--|--|--|--|--|
| AC|pre|5m | reversion | -0.057 | 0.003 | 2.3 | 0.90 |  | yes |
| AC|nyam|5m | reversion | -0.015 | 0.030 | 4.8 | 0.90 |  | yes |
| AC|nypm|5m | reversion | -0.049 | 0.003 | 4.0 | 1.00 |  | yes |
| AC|close|5m | reversion | -0.027 | 0.003 | 3.8 | 0.90 |  | yes |
| AC|nypm|15m | reversion | -0.021 | 0.030 | 4.0 | 0.50 |  | yes |
| vr|pre|5 | reversion | +0.826 | 0.016 | 2.3 | 1.00 | stable | yes |
| vr|pre|15 | reversion | +0.754 | 0.016 | 2.3 | 1.00 | stable | yes |
| hurst|pre | reversion | +0.459 | 0.016 | 2.3 | 1.00 | stable | yes |
| vr|nyam|5 | reversion | +0.950 | 0.016 | 4.8 | 1.00 | stable | yes |
| vr|nyam|15 | reversion | +0.927 | 0.016 | 4.8 | 1.00 | stable | yes |
| vr|nyam|30 | reversion | +0.922 | 0.016 | 4.8 | 1.00 | stable | yes |
| vr|nypm|5 | reversion | +0.862 | 0.016 | 4.0 | 1.00 | stable | yes |
| vr|nypm|15 | reversion | +0.805 | 0.016 | 4.0 | 1.00 | stable | yes |
| vr|nypm|30 | reversion | +0.787 | 0.016 | 4.0 | 1.00 | stable | yes |
| vr|nypm|60 | reversion | +0.787 | 0.016 | 4.0 | 0.90 | stable | yes |
| hurst|nypm | reversion | +0.481 | 0.016 | 4.0 | 0.90 | stable | yes |
| vr|close|5 | reversion | +0.888 | 0.016 | 3.8 | 1.00 | stable | yes |
| vr|close|15 | reversion | +0.855 | 0.016 | 3.8 | 0.90 | stable | yes |
| vr|close|30 | reversion | +0.859 | 0.016 | 3.8 | 0.80 | stable | yes |
| vr|rth|5 | reversion | +0.921 | 0.016 | 4.8 | 1.00 | stable | yes |
| vr|rth|15 | reversion | +0.885 | 0.016 | 4.8 | 1.00 | stable | yes |
| vr|rth|30 | reversion | +0.871 | 0.016 | 4.8 | 1.00 | stable | yes |
| vr|rth|60 | reversion | +0.862 | 0.016 | 4.8 | 1.00 | stable | yes |
| vr|rth|120 | reversion | +0.855 | 0.016 | 4.8 | 0.90 | stable | yes |
| hurst|rth | reversion | +0.488 | 0.016 | 4.8 | 0.90 | stable | yes |

### RV extra: spread half-life (AR(1) of x minus its 120-min mean, 5-min sampling) and stability
| session | phi(5 min) all years | half-life min | years with half-life < 60 min / years |
|--|--|--|--|
| asia | 0.904 | 34 | 10 / 10 |
| london | 0.920 | 41 | 10 / 10 |
| nyam | 0.935 | 51 | 7 / 10 |
| nypm | 0.927 | 46 | 8 / 10 |
| close | 0.930 | 48 | 6 / 9 |

RV note: spread = causal beta-hedged pseudo-price of the two legs (beta from the previous 20 label days of 5-min returns; prereg sha fa5c5c13.. + addendum 1); sessions analysed have both legs printing in >= 90% of minutes: asia, london, pre, nyam, nypm, close. Round-number rows are meaningless for a spread and not used. Cost/room are for the integer hedge unit (a:b contracts) with BOTH legs paid (PROXY-STD fees, 1 tick in + 2 ticks stop slip per leg). Base: 1-min .v.0 percent frame, data end 2026-10-16.

## RV ESYM - relative-value spread character map (CHAR-B via char_lib, 2026-11-06T01:14Z)
Base: RV_ESYM CME front-month (.v.0) 1-min bars from 2013-01 to 2026-10, percent frame (multiplicative roll-adjusted), 1-min approximation (no tick path), 3425 usable label days; ET clock, sessions asia 18:00-02:00 / london 02:00-08:30 / pre 08:30-09:30 / nyam 09:30-12:00 / nypm 12:00-15:00 / close 15:00-16:55. Nulls: within-year shuffled-day (AC B=300; structure B=100 worlds; levels recomputed on the shuffled path; round numbers 60 random grid phases); p_family = Westfall-Young max-|z| over the block (AC family 153 cells, structure family 92 cells). `**` p_family<=.05, `*` <=.10. Prereg sha256 980bedf6bad3f1669de9efb93831fa4622d88577c892d9359b7f57ba93c9dbcf. Descriptive only: no PASS, nothing live.

### Plain paragraph
At 1 minute every session has negative autocorrelation (-0.331 to -0.064; bid-ask bounce / last-print noise, not a tradable edge by itself). asia: reverts at 5/15/30/60 min (-0.224, -0.126, -0.085, -0.040). london: reverts at 5/15/30 min (-0.126, -0.060, -0.037). pre: reverts at 5/15 min (-0.114, -0.054). nypm: reverts at 5/15 min (-0.078, -0.029). close: reverts at 5/15 min (-0.070, -0.035). Day types (RTH): 50% trend days (efficiency ratio >= .5; shuffled null 49%, p_fam 1.000), 22% range days (<.25; null 24%, p_fam 0.967); the IB (09:30-10:30) is extended on one side only on 77% of days and on both on 16%, and a one-sided extension closes beyond the IB edge 60% of the time (null 65%). RTH variance ratio at 30 min 0.741 (shuffled null 0.998, p_fam 0.016); Hurst 0.479. The RTH range forms 9:30 (53%), 10:00 (20%), 11:00 (9%) of the range increments. Level reactions that beat the family null: PD|asia bounces 52% of touches (more than the shuffled null 40%); PD|london bounces 49% of touches (more than the shuffled null 41%); ON|nypm bounces 47% of touches (more than the shuffled null 43%); VW1|close bounces 44% of touches (more than the shuffled null 41%); VW2|nypm bounces 49% of touches (more than the shuffled null 43%); VW2|close bounces 46% of touches (more than the shuffled null 40%). Failed-break follow-through beating the null: PD|asia 33% (null 50%); PD|london 36% (null 50%); PD|pre 42% (null 50%); PD|nypm 41% (null 50%); PD|close 42% (null 50%); ON|nypm 43% (null 50%); ON|close 41% (null 50%); IB|nyam 42% (null 50%); IB|nypm 38% (null 50%); IB|close 40% (null 50%). Room (median 3xATR14(5m) $ / round-trip cost $62 per lot): asia 1.8x, london 2.0x, pre 2.5x, nyam 4.3x, nypm 3.5x, close nanx (1xATR5 room 1.4x in nyam, 0.6x in asia).

### 1. Autocorrelation of h-min returns (corr(past h, next h), both inside the session), pooled; cell = corr (pre-2023 mean | 2023+ mean) p_family
| session | 1 min | 5 min | 15 min | 30 min | 60 min | 120 min |
|--|--|--|--|--|--|--|
| asia | -0.331 (-0.356|-0.230) p0.003** ys1.00 | -0.224 (-0.283|-0.111) p0.003** ys1.00 | -0.126 (-0.201|-0.054) p0.003** ys1.00 | -0.085 (-0.159|-0.035) p0.003** ys0.86 | -0.040 (-0.110|+0.001) p0.003** ys0.71 | -0.017 (-0.076|-0.003) p1.000 ys0.79 |
| london | -0.277 (-0.325|-0.134) p0.003** ys1.00 | -0.126 (-0.194|-0.043) p0.003** ys1.00 | -0.060 (-0.120|-0.017) p0.003** ys1.00 | -0.037 (-0.092|-0.005) p0.003** ys0.79 | -0.017 (-0.065|+0.012) p0.963 ys0.71 | -0.022 (-0.064|-0.021) p1.000 ys0.79 |
| pre | -0.198 (-0.261|-0.091) p0.003** ys1.00 | -0.114 (-0.160|-0.073) p0.003** ys1.00 | -0.054 (-0.083|-0.042) p0.003** ys0.93 | -0.067 (-0.098|-0.023) p0.063* ys0.86 | - | - |
| nyam | -0.064 (-0.134|-0.013) p0.003** ys0.86 | -0.010 (-0.040|+0.006) p0.628 ys0.71 | +0.004 (-0.014|+0.015) p1.000 ys0.43 | +0.021 (+0.029|+0.013) p0.947 ys0.93 | +0.002 (+0.018|-0.008) p1.000 ys0.57 | - |
| nypm | -0.185 (-0.240|-0.080) p0.003** ys1.00 | -0.078 (-0.119|-0.043) p0.003** ys1.00 | -0.029 (-0.060|+0.005) p0.003** ys0.71 | +0.001 (+0.000|+0.007) p1.000 ys0.50 | +0.022 (+0.026|+0.018) p1.000 ys0.57 | - |
| close | -0.170 (-0.228|-0.061) p0.003** ys1.00 | -0.070 (-0.108|-0.034) p0.003** ys1.00 | -0.035 (-0.064|-0.016) p0.003** ys0.86 | +0.009 (-0.023|+0.019) p1.000 ys0.36 | - | - |

Hour cells (h >= 5) beating the family null, top 14 by |z| (hour = ET hour of the decision bar):
| h | session | hour ET | corr | z | p_family | year sign share | pre-2023 | 2023+ |
|--|--|--|--|--|--|--|--|--|
| 5 | asia | 23 | -0.255 | -80.5 | 0.003 | 1.00 | -0.294 | -0.153 |
| 5 | asia | 00 | -0.240 | -75.3 | 0.003 | 1.00 | -0.289 | -0.126 |
| 5 | asia | 22 | -0.241 | -72.2 | 0.003 | 1.00 | -0.288 | -0.145 |
| 5 | asia | 19 | -0.232 | -66.7 | 0.003 | 1.00 | -0.301 | -0.106 |
| 5 | asia | 21 | -0.221 | -64.8 | 0.003 | 1.00 | -0.280 | -0.113 |
| 5 | asia | 01 | -0.230 | -63.3 | 0.003 | 1.00 | -0.290 | -0.097 |
| 5 | london | 02 | -0.200 | -58.5 | 0.003 | 1.00 | -0.256 | -0.090 |
| 5 | asia | 20 | -0.208 | -56.5 | 0.003 | 1.00 | -0.289 | -0.101 |
| 5 | asia | 18 | -0.193 | -54.0 | 0.003 | 1.00 | -0.263 | -0.095 |
| 5 | london | 03 | -0.153 | -44.5 | 0.003 | 1.00 | -0.222 | -0.065 |
| 5 | london | 05 | -0.159 | -43.2 | 0.003 | 1.00 | -0.237 | -0.057 |
| 5 | london | 04 | -0.109 | -26.5 | 0.003 | 0.86 | -0.201 | -0.022 |
| 5 | london | 07 | -0.095 | -24.8 | 0.003 | 1.00 | -0.141 | -0.045 |
| 15 | asia | 23 | -0.143 | -23.1 | 0.003 | 1.00 | -0.200 | -0.089 |

### 2. Variance ratio VR(q) and Hurst (1.0 = random walk; <1 reverting; edge-bias corrected), cell = value (null) p_family
| session | VR5 | VR15 | VR30 | VR60 | VR120 | Hurst |
|--|--|--|--|--|--|--|
| asia | 0.423 (0.998) p0.016** | 0.290 (0.998) p0.016** | 0.250 (0.998) p0.016** | 0.228 (0.999) p0.016** | 0.221 (0.999) p0.016** | 0.398 (0.500) p0.016** |
| london | 0.536 (0.998) p0.016** | 0.444 (0.998) p0.016** | 0.419 (0.998) p0.016** | 0.408 (0.998) p0.016** | 0.399 (0.998) p0.016** | 0.454 (0.500) p0.016** |
| pre | 0.637 (0.998) p0.016** | 0.518 (0.996) p0.016** | - | - | - | 0.406 (0.499) p0.016** |
| nyam | 0.897 (1.000) p0.016** | 0.874 (0.999) p0.016** | 0.864 (0.998) p0.016** | - | - | 0.489 (0.500) p0.016** |
| nypm | 0.689 (0.999) p0.016** | 0.617 (0.998) p0.016** | 0.597 (0.998) p0.016** | 0.599 (0.998) p0.016** | - | 0.471 (0.500) p0.016** |
| close | 0.711 (0.999) p0.016** | 0.645 (0.998) p0.016** | 0.634 (0.997) p0.016** | - | - | 0.467 (0.500) p0.016** |
| rth | 0.814 (0.999) p0.016** | 0.763 (0.998) p0.016** | 0.741 (0.998) p0.016** | 0.727 (0.998) p0.016** | 0.713 (0.997) p0.016** | 0.479 (0.500) p0.016** |

### 3. Day types (ex-post labels of the RTH day)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| day|trend | 0.505 | 3425 | 0.494 | +1.3 | 1.000 | 0.64 | 0.499 | 0.518 | stable |
| day|range | 0.225 | 3425 | 0.240 | -2.0 | 0.967 | 0.64 | 0.230 | 0.210 | stable |
| day|er | 0.511 | 3425 | 0.491 | +4.5 | 0.016** | 0.79 | 0.506 | 0.524 | stable |
| day|ib_none | 0.072 | 3425 | 0.041 | +8.6 | 0.016** | 0.86 | 0.063 | 0.096 | stable |
| day|ib_one | 0.765 | 3425 | 0.724 | +5.5 | 0.016** | 0.93 | 0.754 | 0.792 | stable |
| day|ib_both | 0.163 | 3425 | 0.235 | -10.6 | 0.016** | 0.93 | 0.183 | 0.112 | stable |
| day|ib_one_closebeyond | 0.605 | 2621 | 0.653 | -5.3 | 0.016** | 0.86 | 0.607 | 0.596 | stable |

### 4. 1A -> 2A continuation vs give-back-half from the session open (A = 3 x ATR14(5m)); value = P(continue | resolved)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| cont|asia | 0.277 | 1355 | 0.406 | -16.2 | 0.016** | 0.86 | 0.166 | 0.376 | stable |
| cont|london | 0.272 | 3115 | 0.422 | -17.9 | 0.016** | 1.00 | 0.213 | 0.378 | stable |
| cont|pre | 0.344 | 1216 | 0.414 | -6.9 | 0.016** | 0.79 | 0.247 | 0.416 | stable |
| cont|nyam | 0.541 | 3290 | 0.493 | +6.6 | 0.016** | 0.79 | 0.517 | 0.596 | stable |
| cont|nypm | 0.308 | 1399 | 0.366 | -6.3 | 0.016** | 1.00 | 0.291 | 0.347 | stable |
| cont|close | 0.307 | 1444 | 0.404 | -9.3 | 0.016** | 0.93 | 0.263 | 0.372 | stable |
| cont|rth | 0.535 | 3390 | 0.491 | +6.2 | 0.016** | 0.79 | 0.512 | 0.594 | stable |

### 5. Gap fill by size bucket (b0 .05-.10, b1 .10-.25, b2 .25-.50, b3 >.50 of the 20-day mean RTH range); day = filled during RTH, h1 = within 60 min
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| gap|b0|day | 0.843 | 381 | 0.852 | -0.4 | 1.000 | 0.64 | 0.848 | 0.816 | stable |
| gap|b0|h1 | 0.764 | 381 | 0.756 | +0.3 | 1.000 | 0.50 | 0.768 | 0.749 | unstable |
| gap|b1|day | 0.756 | 980 | 0.744 | +0.6 | 1.000 | 0.43 | 0.751 | 0.773 | unstable |
| gap|b1|h1 | 0.631 | 980 | 0.590 | +1.7 | 0.984 | 0.79 | 0.619 | 0.664 | stable |
| gap|b2|day | 0.585 | 1001 | 0.543 | +2.4 | 0.738 | 0.86 | 0.582 | 0.602 | stable |
| gap|b2|h1 | 0.426 | 1001 | 0.323 | +6.4 | 0.016** | 1.00 | 0.411 | 0.473 | stable |
| gap|b3|day | 0.287 | 694 | 0.209 | +8.6 | 0.016** | 1.00 | 0.306 | 0.261 | stable |
| gap|b3|h1 | 0.161 | 694 | 0.061 | +17.2 | 0.016** | 1.00 | 0.177 | 0.145 | stable |

### 6. Level reaction: first touch -> bounce (0.5A reverse) vs break-through (0.5A beyond) within 60 min; value = P(bounce)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| rx|PD|asia | 0.524 | 934 | 0.401 | +12.7 | 0.016** | 0.86 | 0.564 | 0.478 | stable |
| rx|PD|london | 0.491 | 1537 | 0.413 | +7.1 | 0.016** | 1.00 | 0.514 | 0.439 | stable |
| rx|PD|pre | 0.455 | 943 | 0.405 | +2.9 | 0.295 | 0.71 | 0.477 | 0.392 | stable |
| rx|PD|nyam | 0.369 | 2316 | 0.374 | -0.4 | 1.000 | 0.50 | 0.383 | 0.335 | REGIME(2023+ only) |
| rx|PD|nypm | 0.434 | 1095 | 0.430 | +0.2 | 1.000 | 0.43 | 0.442 | 0.395 | unstable |
| rx|PD|close | 0.450 | 826 | 0.402 | +3.3 | 0.098* | 0.71 | 0.441 | 0.464 | stable |
| rx|ON|nyam | 0.350 | 3641 | 0.359 | -0.9 | 1.000 | 0.50 | 0.359 | 0.331 | unstable |
| rx|ON|nypm | 0.472 | 1379 | 0.428 | +3.8 | 0.016** | 0.79 | 0.484 | 0.432 | stable |
| rx|ON|close | 0.440 | 1016 | 0.402 | +2.8 | 0.311 | 0.79 | 0.434 | 0.439 | stable |
| rx|IB|nyam | 0.444 | 2426 | 0.424 | +2.1 | 0.918 | 0.64 | 0.456 | 0.418 | stable |
| rx|IB|nypm | 0.442 | 1881 | 0.427 | +1.5 | 1.000 | 0.57 | 0.450 | 0.420 | unstable |
| rx|IB|close | 0.440 | 1299 | 0.405 | +3.5 | 0.082* | 0.64 | 0.457 | 0.390 | stable |
| rx|VW1|nyam | 0.435 | 4344 | 0.418 | +2.5 | 0.656 | 0.71 | 0.431 | 0.444 | stable |
| rx|VW1|nypm | 0.456 | 3149 | 0.428 | +3.3 | 0.098* | 0.71 | 0.471 | 0.409 | stable |
| rx|VW1|close | 0.445 | 2364 | 0.407 | +3.6 | 0.049** | 0.71 | 0.458 | 0.401 | stable |
| rx|VW2|nyam | 0.439 | 2613 | 0.424 | +2.0 | 0.967 | 0.64 | 0.441 | 0.443 | stable |
| rx|VW2|nypm | 0.489 | 1572 | 0.430 | +6.1 | 0.016** | 0.86 | 0.502 | 0.447 | stable |
| rx|VW2|close | 0.461 | 1110 | 0.403 | +4.7 | 0.016** | 0.79 | 0.473 | 0.426 | stable |
| rx|RN|asia | 0.464 | 7394 | 0.464 | -0.0 | 1.000 | 0.43 | 0.476 | 0.443 | REGIME(2023+ only) |
| rx|RN|london | 0.456 | 8606 | 0.456 | +0.2 | 1.000 | 0.57 | 0.468 | 0.434 | unstable |
| rx|RN|pre | 0.443 | 1972 | 0.442 | +0.2 | 1.000 | 0.50 | 0.450 | 0.423 | unstable |
| rx|RN|nyam | 0.408 | 6811 | 0.407 | +0.1 | 1.000 | 0.43 | 0.418 | 0.394 | unstable |
| rx|RN|nypm | 0.450 | 4770 | 0.448 | +0.7 | 1.000 | 0.50 | 0.457 | 0.437 | unstable |
| rx|RN|close | 0.423 | 2249 | 0.428 | -1.3 | 1.000 | 0.57 | 0.435 | 0.404 | REGIME(2023+ only) |

### 7. Failed break (close .25A beyond, back inside within 10 bars): fade follow-through P(0.5A back before 0.5A out)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| fb|PD|asia | 0.327 | 682 | 0.499 | -15.2 | 0.016** | 1.00 | 0.283 | 0.381 | stable |
| fb|PD|london | 0.363 | 1195 | 0.500 | -12.2 | 0.016** | 1.00 | 0.317 | 0.446 | stable |
| fb|PD|pre | 0.421 | 648 | 0.501 | -3.8 | 0.016** | 0.79 | 0.438 | 0.397 | stable |
| fb|PD|nyam | 0.481 | 1735 | 0.499 | -1.2 | 1.000 | 0.79 | 0.482 | 0.478 | stable |
| fb|PD|nypm | 0.407 | 805 | 0.503 | -5.9 | 0.016** | 0.86 | 0.404 | 0.436 | stable |
| fb|PD|close | 0.421 | 579 | 0.499 | -4.0 | 0.016** | 0.86 | 0.401 | 0.487 | stable |
| fb|ON|nyam | 0.491 | 2288 | 0.499 | -0.6 | 1.000 | 0.64 | 0.477 | 0.520 | stable |
| fb|ON|nypm | 0.433 | 1085 | 0.500 | -4.2 | 0.016** | 0.79 | 0.429 | 0.450 | stable |
| fb|ON|close | 0.409 | 740 | 0.500 | -4.8 | 0.016** | 0.93 | 0.379 | 0.503 | stable |
| fb|IB|nyam | 0.424 | 1073 | 0.498 | -5.1 | 0.016** | 0.79 | 0.401 | 0.488 | stable |
| fb|IB|nypm | 0.384 | 1361 | 0.501 | -10.2 | 0.016** | 1.00 | 0.361 | 0.450 | stable |
| fb|IB|close | 0.403 | 925 | 0.501 | -6.2 | 0.016** | 0.93 | 0.378 | 0.474 | stable |

### 8. Where the range forms
RTH range increments by bin: 9:30 53.3%, 10:00 20.2%, 11:00 8.7%, 12:00 5.5%, 13:00 4.1%, 14:00 3.7%, 15:00 4.4%
Label-day range increments by ET hour (percent of the day): 00h 1.1, 01h 1.4, 02h 2.1, 03h 2.9, 04h 3.2, 05h 2.2, 06h 2.3, 07h 3.1, 08h 4.4, 09h 20.3, 10h 10.9, 11h 5.3, 12h 3.4, 13h 2.7, 14h 2.5, 15h 2.9, 16h 2.4, 18h 14.8, 19h 3.3, 20h 3.4, 21h 2.4, 22h 1.7, 23h 1.3

### 9. Room and liquidity (all years, raw-frame $, 1 lot)
| session | ATR14(5m) $ | A=3xATR5 $ | RT cost $ | room(1 ATR5) | room(A) | median 5-min vol | 1.7% cap (contracts/5min) | lots for $1,200 at 3xATR5 stop |
|--|--|--|--|--|--|--|--|--|
| asia | 38 | 113 | 62 | 0.61 | 1.82 | 64 | 0.0 | 10.6 |
| london | 41 | 123 | 62 | 0.66 | 1.97 | 189 | 1.0 | 9.8 |
| pre | 52 | 156 | 62 | 0.84 | 2.51 | 413 | 4.0 | 7.7 |
| nyam | 90 | 270 | 62 | 1.45 | 4.35 | 1575 | 17.0 | 4.4 |
| nypm | 73 | 219 | 62 | 1.17 | 3.52 | 734 | 7.0 | 5.5 |
| close | nan | nan | nan | nan | nan | nan | nan | nan |

room(A) by year: asia: 2013:0.8 2014:1.3 2015:1.1 2016:0.7 2017:0.8 2018:1.1 2019:1.0 2020:1.6 2021:1.6 2022:1.4 2023:1.1 2024:3.4 2025:1.8 2026:4.8; london: 2013:0.8 2014:1.1 2015:1.0 2016:0.7 2017:0.9 2018:1.1 2019:1.0 2020:1.6 2021:1.7 2022:1.5 2023:1.3 2024:3.9 2025:2.0 2026:4.6; pre: 2013:1.0 2014:1.5 2015:1.1 2016:0.8 2017:1.0 2018:1.3 2019:1.1 2020:1.8 2021:2.2 2022:1.8 2023:1.8 2024:5.3 2025:2.6 2026:5.5; nyam: 2013:1.2 2014:2.0 2015:1.6 2016:1.1 2017:1.4 2018:2.1 2019:1.8 2020:3.2 2021:4.3 2022:3.8 2023:3.7 2024:9.6 2025:4.9 2026:11.8; nypm: 2013:1.1 2014:1.7 2015:1.3 2016:1.0 2017:1.2 2018:1.8 2019:1.5 2020:2.5 2021:3.3 2022:2.6 2023:2.5 2024:7.4 2025:3.5 2026:8.8; close: 

### 11. Map rows that become book candidates under the FROZEN rule (p_family <= .05 AND room_A(session) > 2.0)
| map row | direction | stat | p_family | room_A | year sign share | stability | 1.7% cap >= 1 contract/5min in session |
|--|--|--|--|--|--|--|--|
| AC|pre|5m | reversion | -0.114 | 0.003 | 2.5 | 1.00 |  | yes |
| AC|nypm|5m | reversion | -0.078 | 0.003 | 3.5 | 1.00 |  | yes |
| AC|pre|15m | reversion | -0.054 | 0.003 | 2.5 | 0.93 |  | yes |
| AC|nypm|15m | reversion | -0.029 | 0.003 | 3.5 | 0.71 |  | yes |
| fb|PD|pre | level-break | +0.421 | 0.016 | 2.5 | 0.79 | stable | yes |
| fb|PD|nypm | level-break | +0.407 | 0.016 | 3.5 | 0.86 | stable | yes |
| fb|PD|close | level-break | +0.421 | 0.016 | nan | 0.86 | stable | NO (illiquid) |
| rx|ON|nypm | level-bounce | +0.472 | 0.016 | 3.5 | 0.79 | stable | yes |
| fb|ON|nypm | level-break | +0.433 | 0.016 | 3.5 | 0.79 | stable | yes |
| fb|ON|close | level-break | +0.409 | 0.016 | nan | 0.93 | stable | NO (illiquid) |
| fb|IB|nyam | level-break | +0.424 | 0.016 | 4.3 | 0.79 | stable | yes |
| fb|IB|nypm | level-break | +0.384 | 0.016 | 3.5 | 1.00 | stable | yes |
| fb|IB|close | level-break | +0.403 | 0.016 | nan | 0.93 | stable | NO (illiquid) |
| rx|VW1|close | level-bounce | +0.445 | 0.049 | nan | 0.71 | stable | NO (illiquid) |
| rx|VW2|nypm | level-bounce | +0.489 | 0.016 | 3.5 | 0.86 | stable | yes |
| rx|VW2|close | level-bounce | +0.461 | 0.016 | nan | 0.79 | stable | NO (illiquid) |
| gap|b2|h1 | level-bounce | +0.426 | 0.016 | 4.3 | 1.00 | stable | yes |
| gap|b3|day | level-bounce | +0.287 | 0.016 | 4.3 | 1.00 | stable | yes |
| gap|b3|h1 | level-bounce | +0.161 | 0.016 | 4.3 | 1.00 | stable | yes |
| vr|pre|5 | reversion | +0.637 | 0.016 | 2.5 | 1.00 | stable | yes |
| vr|pre|15 | reversion | +0.518 | 0.016 | 2.5 | 1.00 | stable | yes |
| hurst|pre | reversion | +0.406 | 0.016 | 2.5 | 1.00 | stable | yes |
| vr|nyam|5 | reversion | +0.897 | 0.016 | 4.3 | 0.93 | stable | yes |
| vr|nyam|15 | reversion | +0.874 | 0.016 | 4.3 | 0.86 | stable | yes |
| vr|nyam|30 | reversion | +0.864 | 0.016 | 4.3 | 0.79 | stable | yes |
| hurst|nyam | reversion | +0.489 | 0.016 | 4.3 | 0.64 | stable | yes |
| vr|nypm|5 | reversion | +0.689 | 0.016 | 3.5 | 1.00 | stable | yes |
| vr|nypm|15 | reversion | +0.617 | 0.016 | 3.5 | 1.00 | stable | yes |
| vr|nypm|30 | reversion | +0.597 | 0.016 | 3.5 | 1.00 | stable | yes |
| vr|nypm|60 | reversion | +0.599 | 0.016 | 3.5 | 1.00 | stable | yes |
| hurst|nypm | reversion | +0.471 | 0.016 | 3.5 | 1.00 | stable | yes |
| vr|close|5 | reversion | +0.711 | 0.016 | nan | 1.00 | stable | NO (illiquid) |
| vr|close|15 | reversion | +0.645 | 0.016 | nan | 1.00 | stable | NO (illiquid) |
| vr|close|30 | reversion | +0.634 | 0.016 | nan | 1.00 | stable | NO (illiquid) |
| hurst|close | reversion | +0.467 | 0.016 | nan | 0.93 | stable | NO (illiquid) |
| vr|rth|5 | reversion | +0.814 | 0.016 | 4.3 | 1.00 | stable | yes |
| vr|rth|15 | reversion | +0.763 | 0.016 | 4.3 | 1.00 | stable | yes |
| vr|rth|30 | reversion | +0.741 | 0.016 | 4.3 | 1.00 | stable | yes |
| vr|rth|60 | reversion | +0.727 | 0.016 | 4.3 | 1.00 | stable | yes |
| vr|rth|120 | reversion | +0.713 | 0.016 | 4.3 | 0.93 | stable | yes |
| hurst|rth | reversion | +0.479 | 0.016 | 4.3 | 0.93 | stable | yes |

### RV extra: spread half-life (AR(1) of x minus its 120-min mean, 5-min sampling) and stability
| session | phi(5 min) all years | half-life min | years with half-life < 60 min / years |
|--|--|--|--|
| asia | 0.884 | 28 | 13 / 14 |
| london | 0.922 | 43 | 13 / 14 |
| nyam | 0.938 | 54 | 13 / 14 |
| nypm | 0.927 | 46 | 14 / 14 |

RV note: spread = causal beta-hedged pseudo-price of the two legs (beta from the previous 20 label days of 5-min returns; prereg sha fa5c5c13.. + addendum 1); sessions analysed have both legs printing in >= 90% of minutes: asia, london, pre, nyam, nypm. Round-number rows are meaningless for a spread and not used. Cost/room are for the integer hedge unit (a:b contracts) with BOTH legs paid (PROXY-STD fees, 1 tick in + 2 ticks stop slip per leg). Base: 1-min .v.0 percent frame, data end 2026-10-16.

## RV RTYYM - relative-value spread character map (CHAR-B via char_lib, 2026-11-06T01:13Z)
Base: RV_RTYYM CME front-month (.v.0) 1-min bars from 2017-01 to 2026-10, percent frame (multiplicative roll-adjusted), 1-min approximation (no tick path), 2126 usable label days; ET clock, sessions asia 18:00-02:00 / london 02:00-08:30 / pre 08:30-09:30 / nyam 09:30-12:00 / nypm 12:00-15:00 / close 15:00-16:55. Nulls: within-year shuffled-day (AC B=300; structure B=100 worlds; levels recomputed on the shuffled path; round numbers 60 random grid phases); p_family = Westfall-Young max-|z| over the block (AC family 153 cells, structure family 92 cells). `**` p_family<=.05, `*` <=.10. Prereg sha256 980bedf6bad3f1669de9efb93831fa4622d88577c892d9359b7f57ba93c9dbcf. Descriptive only: no PASS, nothing live.

### Plain paragraph
At 1 minute every session has negative autocorrelation (-0.251 to -0.011; bid-ask bounce / last-print noise, not a tradable edge by itself). asia: reverts at 5/15/30/60 min (-0.155, -0.084, -0.064, -0.065). london: reverts at 5/15/30 min (-0.057, -0.037, -0.038). pre: reverts at 5 min (-0.060). nypm: reverts at 5 min (-0.033). close: reverts at 5/15/30 min (-0.043, -0.032, -0.062). Day types (RTH): 48% trend days (efficiency ratio >= .5; shuffled null 50%, p_fam 0.984), 26% range days (<.25; null 24%, p_fam 0.344); the IB (09:30-10:30) is extended on one side only on 77% of days and on both on 16%, and a one-sided extension closes beyond the IB edge 60% of the time (null 62%). RTH variance ratio at 30 min 0.915 (shuffled null 0.998, p_fam 0.016); Hurst 0.486. The RTH range forms 9:30 (53%), 10:00 (22%), 11:00 (8%) of the range increments. Level reactions that beat the family null: PD|asia bounces 48% of touches (more than the shuffled null 38%); PD|london bounces 46% of touches (more than the shuffled null 40%). Failed-break follow-through beating the null: PD|asia 41% (null 50%); PD|london 43% (null 50%). Room (median 3xATR14(5m) $ / round-trip cost $99 per lot): asia 2.0x, london 2.1x, pre 3.0x, nyam 7.1x, nypm 5.4x, close 4.6x (1xATR5 room 2.4x in nyam, 0.7x in asia).

### 1. Autocorrelation of h-min returns (corr(past h, next h), both inside the session), pooled; cell = corr (pre-2023 mean | 2023+ mean) p_family
| session | 1 min | 5 min | 15 min | 30 min | 60 min | 120 min |
|--|--|--|--|--|--|--|
| asia | -0.251 (-0.281|-0.200) p0.003** ys1.00 | -0.155 (-0.196|-0.110) p0.003** ys1.00 | -0.084 (-0.103|-0.063) p0.003** ys1.00 | -0.064 (-0.080|-0.055) p0.003** ys0.90 | -0.065 (-0.054|-0.073) p0.003** ys0.90 | -0.038 (-0.039|-0.027) p0.179 ys0.70 |
| london | -0.155 (-0.214|-0.097) p0.003** ys1.00 | -0.057 (-0.100|-0.025) p0.003** ys1.00 | -0.037 (-0.054|-0.022) p0.003** ys1.00 | -0.038 (-0.066|-0.013) p0.003** ys0.90 | -0.021 (-0.046|+0.000) p0.980 ys0.70 | -0.022 (-0.078|+0.016) p1.000 ys0.70 |
| pre | -0.061 (-0.095|-0.034) p0.003** ys1.00 | -0.060 (-0.063|-0.056) p0.003** ys0.90 | -0.036 (-0.062|-0.015) p0.186 ys0.80 | -0.082 (-0.111|-0.073) p0.213 ys1.00 | - | - |
| nyam | -0.011 (-0.012|-0.025) p0.017** ys0.70 | -0.001 (-0.006|-0.009) p1.000 ys0.70 | -0.007 (-0.006|-0.012) p1.000 ys0.50 | +0.009 (-0.005|-0.008) p1.000 ys0.50 | -0.031 (-0.043|-0.035) p1.000 ys0.70 | - |
| nypm | -0.050 (-0.041|-0.056) p0.003** ys1.00 | -0.033 (-0.028|-0.047) p0.003** ys1.00 | -0.022 (-0.015|-0.030) p0.063* ys0.80 | -0.019 (+0.024|-0.042) p0.997 ys0.70 | -0.005 (-0.013|+0.025) p1.000 ys0.30 | - |
| close | -0.070 (-0.072|-0.053) p0.003** ys1.00 | -0.043 (-0.047|-0.035) p0.003** ys1.00 | -0.032 (-0.066|-0.017) p0.047** ys0.90 | -0.062 (-0.086|-0.047) p0.013** ys1.00 | - | - |

Hour cells (h >= 5) beating the family null, top 14 by |z| (hour = ET hour of the decision bar):
| h | session | hour ET | corr | z | p_family | year sign share | pre-2023 | 2023+ |
|--|--|--|--|--|--|--|--|--|
| 5 | asia | 23 | -0.182 | -42.4 | 0.003 | 1.00 | -0.223 | -0.141 |
| 5 | asia | 01 | -0.191 | -41.7 | 0.003 | 1.00 | -0.228 | -0.138 |
| 5 | asia | 22 | -0.174 | -39.5 | 0.003 | 1.00 | -0.199 | -0.121 |
| 5 | asia | 00 | -0.156 | -36.5 | 0.003 | 1.00 | -0.189 | -0.129 |
| 5 | asia | 18 | -0.164 | -31.4 | 0.003 | 1.00 | -0.193 | -0.129 |
| 5 | asia | 19 | -0.144 | -30.3 | 0.003 | 1.00 | -0.197 | -0.084 |
| 5 | asia | 21 | -0.143 | -30.3 | 0.003 | 1.00 | -0.200 | -0.091 |
| 5 | london | 02 | -0.136 | -28.0 | 0.003 | 1.00 | -0.178 | -0.106 |
| 5 | asia | 20 | -0.122 | -23.8 | 0.003 | 1.00 | -0.171 | -0.088 |
| 5 | close | 16 | -0.088 | -15.4 | 0.003 | 1.00 | -0.104 | -0.065 |
| 15 | asia | 23 | -0.124 | -14.9 | 0.003 | 1.00 | -0.157 | -0.079 |
| 5 | london | 03 | -0.076 | -14.3 | 0.003 | 0.90 | -0.136 | -0.039 |
| 15 | asia | 19 | -0.112 | -13.7 | 0.003 | 0.80 | -0.117 | -0.075 |
| 5 | london | 05 | -0.061 | -12.4 | 0.003 | 0.90 | -0.117 | -0.016 |

### 2. Variance ratio VR(q) and Hurst (1.0 = random walk; <1 reverting; edge-bias corrected), cell = value (null) p_family
| session | VR5 | VR15 | VR30 | VR60 | VR120 | Hurst |
|--|--|--|--|--|--|--|
| asia | 0.552 (0.998) p0.016** | 0.431 (0.998) p0.016** | 0.394 (0.998) p0.016** | 0.370 (0.999) p0.016** | 0.348 (0.998) p0.016** | 0.429 (0.500) p0.016** |
| london | 0.734 (0.999) p0.016** | 0.673 (0.999) p0.016** | 0.649 (0.999) p0.016** | 0.632 (0.999) p0.016** | 0.625 (0.998) p0.016** | 0.474 (0.500) p0.016** |
| pre | 0.864 (1.000) p0.016** | 0.790 (1.000) p0.016** | - | - | - | 0.459 (0.500) p0.016** |
| nyam | 0.983 (0.999) p0.016** | 0.975 (0.998) p0.148 | 0.959 (0.998) p0.049** | - | - | 0.493 (0.500) p0.787 |
| nypm | 0.903 (0.999) p0.016** | 0.857 (0.998) p0.016** | 0.832 (0.997) p0.016** | 0.807 (0.997) p0.016** | - | 0.478 (0.499) p0.016** |
| close | 0.868 (0.999) p0.016** | 0.813 (0.999) p0.016** | 0.788 (0.998) p0.016** | - | - | 0.473 (0.500) p0.016** |
| rth | 0.959 (0.999) p0.016** | 0.937 (0.998) p0.016** | 0.915 (0.998) p0.016** | 0.901 (0.998) p0.016** | 0.874 (0.997) p0.016** | 0.486 (0.500) p0.016** |

### 3. Day types (ex-post labels of the RTH day)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| day|trend | 0.479 | 2126 | 0.498 | -1.9 | 0.984 | 0.70 | 0.486 | 0.474 | stable |
| day|range | 0.261 | 2126 | 0.238 | +2.7 | 0.344 | 0.80 | 0.223 | 0.281 | REGIME(2023+ only) |
| day|er | 0.490 | 2126 | 0.493 | -0.6 | 1.000 | 0.60 | 0.492 | 0.489 | stable |
| day|ib_none | 0.073 | 2126 | 0.059 | +2.9 | 0.279 | 0.50 | 0.050 | 0.102 | REGIME(2023+ only) |
| day|ib_one | 0.767 | 2126 | 0.769 | -0.2 | 1.000 | 0.40 | 0.746 | 0.767 | unstable |
| day|ib_both | 0.160 | 2126 | 0.172 | -1.5 | 1.000 | 0.60 | 0.203 | 0.131 | REGIME(2023+ only) |
| day|ib_one_closebeyond | 0.600 | 1631 | 0.620 | -1.8 | 1.000 | 0.50 | 0.630 | 0.582 | REGIME(2023+ only) |

### 4. 1A -> 2A continuation vs give-back-half from the session open (A = 3 x ATR14(5m)); value = P(continue | resolved)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| cont|asia | 0.268 | 675 | 0.403 | -13.3 | 0.016** | 1.00 | 0.198 | 0.299 | stable |
| cont|london | 0.310 | 2116 | 0.448 | -12.8 | 0.016** | 1.00 | 0.293 | 0.344 | stable |
| cont|pre | 0.409 | 1259 | 0.483 | -5.6 | 0.016** | 0.80 | 0.365 | 0.474 | stable |
| cont|nyam | 0.582 | 2108 | 0.561 | +1.9 | 0.967 | 0.60 | 0.600 | 0.563 | stable |
| cont|nypm | 0.307 | 973 | 0.356 | -3.5 | 0.049** | 0.80 | 0.348 | 0.282 | stable |
| cont|close | 0.355 | 1079 | 0.407 | -3.9 | 0.033** | 1.00 | 0.352 | 0.364 | stable |
| cont|rth | 0.582 | 2119 | 0.561 | +1.9 | 0.967 | 0.60 | 0.600 | 0.565 | stable |

### 5. Gap fill by size bucket (b0 .05-.10, b1 .10-.25, b2 .25-.50, b3 >.50 of the 20-day mean RTH range); day = filled during RTH, h1 = within 60 min
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| gap|b0|day | 0.818 | 307 | 0.847 | -1.2 | 1.000 | 0.50 | 0.789 | 0.833 | unstable |
| gap|b0|h1 | 0.730 | 307 | 0.768 | -1.3 | 1.000 | 0.70 | 0.705 | 0.764 | stable |
| gap|b1|day | 0.751 | 674 | 0.743 | +0.4 | 1.000 | 0.50 | 0.751 | 0.734 | unstable |
| gap|b1|h1 | 0.645 | 674 | 0.615 | +1.5 | 1.000 | 0.80 | 0.649 | 0.655 | stable |
| gap|b2|day | 0.578 | 533 | 0.551 | +1.4 | 1.000 | 0.80 | 0.596 | 0.578 | stable |
| gap|b2|h1 | 0.413 | 533 | 0.366 | +2.3 | 0.787 | 0.80 | 0.409 | 0.397 | stable |
| gap|b3|day | 0.364 | 280 | 0.274 | +4.7 | 0.016** | 0.70 | 0.272 | 0.373 | REGIME(2023+ only) |
| gap|b3|h1 | 0.189 | 280 | 0.115 | +5.3 | 0.016** | 0.70 | 0.194 | 0.180 | stable |

### 6. Level reaction: first touch -> bounce (0.5A reverse) vs break-through (0.5A beyond) within 60 min; value = P(bounce)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| rx|PD|asia | 0.475 | 408 | 0.384 | +4.7 | 0.016** | 0.80 | 0.529 | 0.431 | stable |
| rx|PD|london | 0.463 | 792 | 0.400 | +4.2 | 0.016** | 0.80 | 0.427 | 0.451 | stable |
| rx|PD|pre | 0.401 | 544 | 0.367 | +1.7 | 1.000 | 0.60 | 0.410 | 0.366 | stable |
| rx|PD|nyam | 0.336 | 1588 | 0.353 | -1.2 | 1.000 | 0.60 | 0.309 | 0.357 | stable |
| rx|PD|nypm | 0.441 | 700 | 0.426 | +1.0 | 1.000 | 0.50 | 0.439 | 0.431 | unstable |
| rx|PD|close | 0.431 | 478 | 0.401 | +1.5 | 1.000 | 0.60 | 0.393 | 0.428 | REGIME(2023+ only) |
| rx|ON|nyam | 0.319 | 2551 | 0.324 | -0.5 | 1.000 | 0.70 | 0.303 | 0.349 | stable |
| rx|ON|nypm | 0.405 | 912 | 0.423 | -1.2 | 1.000 | 0.80 | 0.361 | 0.437 | stable |
| rx|ON|close | 0.411 | 577 | 0.400 | +0.6 | 1.000 | 0.80 | 0.394 | 0.435 | REGIME(2023+ only) |
| rx|IB|nyam | 0.434 | 1558 | 0.420 | +1.3 | 1.000 | 0.90 | 0.445 | 0.426 | stable |
| rx|IB|nypm | 0.442 | 1143 | 0.424 | +1.2 | 1.000 | 0.60 | 0.414 | 0.489 | REGIME(2023+ only) |
| rx|IB|close | 0.444 | 710 | 0.401 | +2.4 | 0.705 | 0.90 | 0.465 | 0.451 | stable |
| rx|VW1|nyam | 0.422 | 2767 | 0.405 | +2.1 | 0.934 | 0.70 | 0.425 | 0.426 | stable |
| rx|VW1|nypm | 0.428 | 1818 | 0.423 | +0.6 | 1.000 | 0.50 | 0.408 | 0.430 | REGIME(2023+ only) |
| rx|VW1|close | 0.433 | 1338 | 0.402 | +2.5 | 0.639 | 0.80 | 0.449 | 0.416 | stable |
| rx|VW2|nyam | 0.430 | 1745 | 0.411 | +2.0 | 0.951 | 0.70 | 0.445 | 0.433 | stable |
| rx|VW2|nypm | 0.458 | 896 | 0.425 | +2.2 | 0.820 | 0.70 | 0.445 | 0.472 | stable |
| rx|VW2|close | 0.447 | 523 | 0.395 | +2.6 | 0.525 | 0.80 | 0.473 | 0.436 | stable |
| rx|RN|asia | 0.452 | 4936 | 0.456 | -2.3 | 0.754 | 0.70 | 0.459 | 0.447 | REGIME(2023+ only) |
| rx|RN|london | 0.439 | 6933 | 0.440 | -0.6 | 1.000 | 0.50 | 0.452 | 0.418 | REGIME(2023+ only) |
| rx|RN|pre | 0.399 | 1615 | 0.414 | -2.7 | 0.344 | 0.90 | 0.399 | 0.391 | stable |
| rx|RN|nyam | 0.395 | 7455 | 0.394 | +0.2 | 1.000 | 0.60 | 0.389 | 0.396 | REGIME(2023+ only) |
| rx|RN|nypm | 0.439 | 4720 | 0.435 | +1.5 | 1.000 | 0.80 | 0.429 | 0.442 | REGIME(2023+ only) |
| rx|RN|close | 0.418 | 2117 | 0.413 | +1.3 | 1.000 | 0.80 | 0.419 | 0.413 | stable |

### 7. Failed break (close .25A beyond, back inside within 10 bars): fade follow-through P(0.5A back before 0.5A out)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| fb|PD|asia | 0.415 | 340 | 0.499 | -4.0 | 0.016** | 0.70 | 0.406 | 0.428 | stable |
| fb|PD|london | 0.427 | 623 | 0.501 | -4.4 | 0.016** | 1.00 | 0.335 | 0.439 | stable |
| fb|PD|pre | 0.457 | 385 | 0.498 | -1.7 | 1.000 | 0.80 | 0.411 | 0.457 | stable |
| fb|PD|nyam | 0.509 | 1150 | 0.497 | +0.8 | 1.000 | 0.70 | 0.534 | 0.499 | stable |
| fb|PD|nypm | 0.532 | 543 | 0.498 | +1.6 | 1.000 | 0.90 | 0.542 | 0.527 | stable |
| fb|PD|close | 0.461 | 358 | 0.499 | -1.4 | 1.000 | 0.70 | 0.432 | 0.489 | stable |
| fb|ON|nyam | 0.497 | 1742 | 0.499 | -0.2 | 1.000 | 0.50 | 0.495 | 0.520 | unstable |
| fb|ON|nypm | 0.479 | 685 | 0.503 | -1.2 | 1.000 | 0.60 | 0.472 | 0.478 | stable |
| fb|ON|close | 0.468 | 462 | 0.503 | -1.5 | 1.000 | 0.80 | 0.469 | 0.446 | stable |
| fb|IB|nyam | 0.508 | 730 | 0.499 | +0.5 | 1.000 | 0.60 | 0.503 | 0.496 | stable |
| fb|IB|nypm | 0.463 | 794 | 0.502 | -2.3 | 0.754 | 0.80 | 0.460 | 0.460 | stable |
| fb|IB|close | 0.465 | 523 | 0.501 | -1.6 | 1.000 | 0.70 | 0.366 | 0.503 | stable |

### 8. Where the range forms
RTH range increments by bin: 9:30 53.2%, 10:00 21.7%, 11:00 8.5%, 12:00 5.0%, 13:00 3.5%, 14:00 3.5%, 15:00 4.6%
Label-day range increments by ET hour (percent of the day): 00h 0.7, 01h 0.8, 02h 1.4, 03h 2.6, 04h 2.9, 05h 2.2, 06h 2.6, 07h 2.8, 08h 5.5, 09h 26.2, 10h 13.7, 11h 5.9, 12h 3.6, 13h 2.5, 14h 2.5, 15h 3.4, 16h 0.9, 18h 10.5, 19h 2.7, 20h 2.6, 21h 1.9, 22h 1.2, 23h 0.9

### 9. Room and liquidity (all years, raw-frame $, 1 lot)
| session | ATR14(5m) $ | A=3xATR5 $ | RT cost $ | room(1 ATR5) | room(A) | median 5-min vol | 1.7% cap (contracts/5min) | lots for $1,200 at 3xATR5 stop |
|--|--|--|--|--|--|--|--|--|
| asia | 66 | 199 | 99 | 0.67 | 2.01 | 29 | 0.0 | 6.0 |
| london | 71 | 213 | 99 | 0.72 | 2.15 | 91 | 0.5 | 5.6 |
| pre | 101 | 302 | 99 | 1.02 | 3.05 | 289 | 2.0 | 4.0 |
| nyam | 236 | 707 | 99 | 2.37 | 7.12 | 1298 | 8.5 | 1.7 |
| nypm | 178 | 535 | 99 | 1.80 | 5.39 | 605 | 3.5 | 2.2 |
| close | 152 | 455 | 99 | 1.53 | 4.58 | 533 | 3.0 | 2.6 |

room(A) by year: asia: 2017:1.1 2018:2.0 2019:1.9 2020:2.5 2021:4.9 2022:2.5 2023:1.6 2024:2.4 2025:2.5 2026:3.1; london: 2017:1.1 2018:1.8 2019:1.8 2020:2.5 2021:4.9 2022:2.4 2023:1.9 2024:3.4 2025:3.1 2026:3.4; pre: 2017:1.5 2018:2.3 2019:2.4 2020:3.3 2021:6.9 2022:3.1 2023:3.0 2024:5.4 2025:4.5 2026:4.7; nyam: 2017:4.0 2018:6.3 2019:6.6 2020:6.8 2021:14.2 2022:9.5 2023:7.7 2024:10.1 2025:8.7 2026:10.1; nypm: 2017:3.5 2018:5.5 2019:5.7 2020:5.5 2021:12.4 2022:7.0 2023:5.3 2024:6.8 2025:6.4 2026:7.2; close: 2017:3.3 2018:4.7 2019:4.9 2020:4.9 2021:10.7 2022:5.8 2023:4.2 2024:6.0 2025:5.5 2026:6.2

### 11. Map rows that become book candidates under the FROZEN rule (p_family <= .05 AND room_A(session) > 2.0)
| map row | direction | stat | p_family | room_A | year sign share | stability | 1.7% cap >= 1 contract/5min in session |
|--|--|--|--|--|--|--|--|
| AC|asia|5m | reversion | -0.155 | 0.003 | 2.0 | 1.00 |  | NO (illiquid) |
| AC|london|5m | reversion | -0.057 | 0.003 | 2.1 | 1.00 |  | NO (illiquid) |
| AC|pre|5m | reversion | -0.060 | 0.003 | 3.0 | 0.90 |  | yes |
| AC|nypm|5m | reversion | -0.033 | 0.003 | 5.4 | 1.00 |  | yes |
| AC|close|5m | reversion | -0.043 | 0.003 | 4.6 | 1.00 |  | yes |
| AC|asia|15m | reversion | -0.084 | 0.003 | 2.0 | 1.00 |  | NO (illiquid) |
| AC|london|15m | reversion | -0.037 | 0.003 | 2.1 | 1.00 |  | NO (illiquid) |
| AC|close|15m | reversion | -0.032 | 0.047 | 4.6 | 0.90 |  | yes |
| AC|asia|30m | reversion | -0.064 | 0.003 | 2.0 | 0.90 |  | NO (illiquid) |
| AC|london|30m | reversion | -0.038 | 0.003 | 2.1 | 0.90 |  | NO (illiquid) |
| AC|close|30m | reversion | -0.062 | 0.013 | 4.6 | 1.00 |  | yes |
| AC|asia|60m | reversion | -0.065 | 0.003 | 2.0 | 0.90 |  | NO (illiquid) |
| rx|PD|asia | level-bounce | +0.475 | 0.016 | 2.0 | 0.80 | stable | NO (illiquid) |
| fb|PD|asia | level-break | +0.415 | 0.016 | 2.0 | 0.70 | stable | NO (illiquid) |
| rx|PD|london | level-bounce | +0.463 | 0.016 | 2.1 | 0.80 | stable | NO (illiquid) |
| fb|PD|london | level-break | +0.427 | 0.016 | 2.1 | 1.00 | stable | NO (illiquid) |
| gap|b3|day | level-bounce | +0.364 | 0.016 | 7.1 | 0.70 | REGIME(2023+ only) | yes |
| gap|b3|h1 | level-bounce | +0.189 | 0.016 | 7.1 | 0.70 | stable | yes |
| vr|asia|5 | reversion | +0.552 | 0.016 | 2.0 | 1.00 | stable | NO (illiquid) |
| vr|asia|15 | reversion | +0.431 | 0.016 | 2.0 | 1.00 | stable | NO (illiquid) |
| vr|asia|30 | reversion | +0.394 | 0.016 | 2.0 | 1.00 | stable | NO (illiquid) |
| vr|asia|60 | reversion | +0.370 | 0.016 | 2.0 | 1.00 | stable | NO (illiquid) |
| vr|asia|120 | reversion | +0.348 | 0.016 | 2.0 | 1.00 | stable | NO (illiquid) |
| hurst|asia | reversion | +0.429 | 0.016 | 2.0 | 1.00 | stable | NO (illiquid) |
| vr|london|5 | reversion | +0.734 | 0.016 | 2.1 | 1.00 | stable | NO (illiquid) |
| vr|london|15 | reversion | +0.673 | 0.016 | 2.1 | 1.00 | stable | NO (illiquid) |
| vr|london|30 | reversion | +0.649 | 0.016 | 2.1 | 1.00 | stable | NO (illiquid) |
| vr|london|60 | reversion | +0.632 | 0.016 | 2.1 | 1.00 | stable | NO (illiquid) |
| vr|london|120 | reversion | +0.625 | 0.016 | 2.1 | 1.00 | stable | NO (illiquid) |
| hurst|london | reversion | +0.474 | 0.016 | 2.1 | 0.90 | stable | NO (illiquid) |
| vr|pre|5 | reversion | +0.864 | 0.016 | 3.0 | 0.90 | stable | yes |
| vr|pre|15 | reversion | +0.790 | 0.016 | 3.0 | 0.80 | stable | yes |
| hurst|pre | reversion | +0.459 | 0.016 | 3.0 | 0.80 | stable | yes |
| vr|nyam|5 | reversion | +0.983 | 0.016 | 7.1 | 0.80 | stable | yes |
| vr|nyam|30 | reversion | +0.959 | 0.049 | 7.1 | 0.80 | stable | yes |
| vr|nypm|5 | reversion | +0.903 | 0.016 | 5.4 | 1.00 | stable | yes |
| vr|nypm|15 | reversion | +0.857 | 0.016 | 5.4 | 1.00 | stable | yes |
| vr|nypm|30 | reversion | +0.832 | 0.016 | 5.4 | 1.00 | stable | yes |
| vr|nypm|60 | reversion | +0.807 | 0.016 | 5.4 | 0.90 | stable | yes |
| hurst|nypm | reversion | +0.478 | 0.016 | 5.4 | 0.90 | stable | yes |
| vr|close|5 | reversion | +0.868 | 0.016 | 4.6 | 1.00 | stable | yes |
| vr|close|15 | reversion | +0.813 | 0.016 | 4.6 | 1.00 | stable | yes |
| vr|close|30 | reversion | +0.788 | 0.016 | 4.6 | 1.00 | stable | yes |
| hurst|close | reversion | +0.473 | 0.016 | 4.6 | 1.00 | stable | yes |
| vr|rth|5 | reversion | +0.959 | 0.016 | 7.1 | 0.90 | stable | yes |
| vr|rth|15 | reversion | +0.937 | 0.016 | 7.1 | 0.90 | stable | yes |
| vr|rth|30 | reversion | +0.915 | 0.016 | 7.1 | 1.00 | stable | yes |
| vr|rth|60 | reversion | +0.901 | 0.016 | 7.1 | 1.00 | stable | yes |
| vr|rth|120 | reversion | +0.874 | 0.016 | 7.1 | 1.00 | stable | yes |
| hurst|rth | reversion | +0.486 | 0.016 | 7.1 | 0.80 | stable | yes |

### RV extra: spread half-life (AR(1) of x minus its 120-min mean, 5-min sampling) and stability
| session | phi(5 min) all years | half-life min | years with half-life < 60 min / years |
|--|--|--|--|
| asia | 0.899 | 33 | 10 / 10 |
| london | 0.929 | 47 | 10 / 10 |
| nyam | 0.934 | 51 | 10 / 10 |
| nypm | 0.926 | 45 | 10 / 10 |
| close | 0.917 | 40 | 10 / 10 |

RV note: spread = causal beta-hedged pseudo-price of the two legs (beta from the previous 20 label days of 5-min returns; prereg sha fa5c5c13.. + addendum 1); sessions analysed have both legs printing in >= 90% of minutes: asia, london, pre, nyam, nypm, close. Round-number rows are meaningless for a spread and not used. Cost/room are for the integer hedge unit (a:b contracts) with BOTH legs paid (PROXY-STD fees, 1 tick in + 2 ticks stop slip per leg). Base: 1-min .v.0 percent frame, data end 2026-10-16.

## RV ZNZB - relative-value spread character map (CHAR-B via char_lib, 2026-11-06T01:14Z)
Base: RV_ZNZB CME front-month (.v.0) 1-min bars from 2013-01 to 2026-10, percent frame (multiplicative roll-adjusted), 1-min approximation (no tick path), 3140 usable label days; ET clock, sessions asia 18:00-02:00 / london 02:00-08:30 / pre 08:30-09:30 / nyam 09:30-12:00 / nypm 12:00-15:00 / close 15:00-16:55. Nulls: within-year shuffled-day (AC B=300; structure B=100 worlds; levels recomputed on the shuffled path; round numbers 60 random grid phases); p_family = Westfall-Young max-|z| over the block (AC family 153 cells, structure family 92 cells). `**` p_family<=.05, `*` <=.10. Prereg sha256 980bedf6bad3f1669de9efb93831fa4622d88577c892d9359b7f57ba93c9dbcf. Descriptive only: no PASS, nothing live.

### Plain paragraph
At 1 minute every session has negative autocorrelation (-0.397 to -0.290; bid-ask bounce / last-print noise, not a tradable edge by itself). asia: reverts at 5/15/30/60/120 min (-0.354, -0.295, -0.221, -0.151, -0.081). london: reverts at 5/15/30/60/120 min (-0.325, -0.205, -0.164, -0.144, -0.104). pre: reverts at 5/15 min (-0.203, -0.100). nyam: reverts at 5/15/30/60 min (-0.244, -0.139, -0.100, -0.070). nypm: reverts at 5/15/30/60 min (-0.273, -0.151, -0.087, -0.077). close: reverts at 5/15/30 min (-0.329, -0.232, -0.200). Day types (RTH): 40% trend days (efficiency ratio >= .5; shuffled null 48%, p_fam 0.016), 30% range days (<.25; null 24%, p_fam 0.016); the IB (09:30-10:30) is extended on one side only on 62% of days and on both on 36%, and a one-sided extension closes beyond the IB edge 61% of the time (null 78%). RTH variance ratio at 30 min 0.186 (shuffled null 0.996, p_fam 0.016); Hurst 0.377. The RTH range forms 9:30 (41%), 10:00 (23%), 11:00 (11%) of the range increments. Level reactions that beat the family null: PD|asia bounces 73% of touches (more than the shuffled null 37%); PD|london bounces 64% of touches (more than the shuffled null 39%); PD|nyam bounces 52% of touches (more than the shuffled null 42%); PD|nypm bounces 50% of touches (more than the shuffled null 42%); PD|close bounces 52% of touches (more than the shuffled null 41%); ON|nyam bounces 62% of touches (more than the shuffled null 42%); ON|nypm bounces 54% of touches (more than the shuffled null 42%); ON|close bounces 57% of touches (more than the shuffled null 41%); IB|nyam bounces 67% of touches (more than the shuffled null 42%); IB|nypm bounces 60% of touches (more than the shuffled null 42%); IB|close bounces 55% of touches (more than the shuffled null 41%); VW1|nyam bounces 58% of touches (more than the shuffled null 42%); VW1|nypm bounces 57% of touches (more than the shuffled null 42%); VW1|close bounces 56% of touches (more than the shuffled null 41%); VW2|nyam bounces 68% of touches (more than the shuffled null 43%); VW2|nypm bounces 68% of touches (more than the shuffled null 43%); VW2|close bounces 75% of touches (more than the shuffled null 42%). Failed-break follow-through beating the null: PD|asia 22% (null 50%); PD|london 25% (null 50%); PD|pre 33% (null 50%); PD|nyam 29% (null 50%); PD|nypm 21% (null 50%); PD|close 14% (null 50%); ON|nyam 27% (null 50%); ON|nypm 23% (null 50%); ON|close 20% (null 50%); IB|nyam 28% (null 50%); IB|nypm 24% (null 50%); IB|close 20% (null 50%). Room (median 3xATR14(5m) $ / round-trip cost $254 per lot): asia nanx, london 0.6x, pre 0.8x, nyam 0.8x, nypm 0.8x, close 0.7x (1xATR5 room 0.3x in nyam, nanx in asia).

### 1. Autocorrelation of h-min returns (corr(past h, next h), both inside the session), pooled; cell = corr (pre-2023 mean | 2023+ mean) p_family
| session | 1 min | 5 min | 15 min | 30 min | 60 min | 120 min |
|--|--|--|--|--|--|--|
| asia | -0.290 (-0.281|-0.296) p0.003** ys1.00 | -0.354 (-0.343|-0.388) p0.003** ys1.00 | -0.295 (-0.290|-0.333) p0.003** ys1.00 | -0.221 (-0.225|-0.257) p0.003** ys1.00 | -0.151 (-0.151|-0.227) p0.003** ys0.93 | -0.081 (-0.092|-0.207) p0.003** ys0.86 |
| london | -0.391 (-0.390|-0.394) p0.003** ys1.00 | -0.325 (-0.319|-0.347) p0.003** ys1.00 | -0.205 (-0.205|-0.239) p0.003** ys1.00 | -0.164 (-0.169|-0.178) p0.003** ys1.00 | -0.144 (-0.148|-0.135) p0.003** ys1.00 | -0.104 (-0.095|-0.153) p0.003** ys0.86 |
| pre | -0.350 (-0.354|-0.347) p0.003** ys1.00 | -0.203 (-0.222|-0.198) p0.003** ys1.00 | -0.100 (-0.121|-0.094) p0.003** ys1.00 | -0.057 (-0.075|-0.066) p0.439 ys0.93 | - | - |
| nyam | -0.394 (-0.392|-0.400) p0.003** ys1.00 | -0.244 (-0.251|-0.251) p0.003** ys1.00 | -0.139 (-0.142|-0.155) p0.003** ys1.00 | -0.100 (-0.119|-0.090) p0.003** ys0.93 | -0.070 (-0.095|-0.066) p0.003** ys0.93 | - |
| nypm | -0.397 (-0.391|-0.410) p0.003** ys1.00 | -0.273 (-0.267|-0.306) p0.003** ys1.00 | -0.151 (-0.148|-0.187) p0.003** ys1.00 | -0.087 (-0.086|-0.113) p0.003** ys0.93 | -0.077 (-0.091|-0.096) p0.003** ys0.93 | - |
| close | -0.397 (-0.392|-0.406) p0.003** ys1.00 | -0.329 (-0.327|-0.349) p0.003** ys1.00 | -0.232 (-0.232|-0.247) p0.003** ys1.00 | -0.200 (-0.198|-0.214) p0.003** ys1.00 | - | - |

Hour cells (h >= 5) beating the family null, top 14 by |z| (hour = ET hour of the decision bar):
| h | session | hour ET | corr | z | p_family | year sign share | pre-2023 | 2023+ |
|--|--|--|--|--|--|--|--|--|
| 5 | london | 06 | -0.352 | -119.9 | 0.003 | 1.00 | -0.344 | -0.377 |
| 5 | london | 05 | -0.347 | -118.3 | 0.003 | 1.00 | -0.341 | -0.371 |
| 5 | asia | 21 | -0.353 | -116.0 | 0.003 | 1.00 | -0.338 | -0.402 |
| 5 | asia | 00 | -0.370 | -115.7 | 0.003 | 1.00 | -0.353 | -0.408 |
| 5 | asia | 23 | -0.374 | -112.6 | 0.003 | 1.00 | -0.357 | -0.413 |
| 5 | london | 02 | -0.338 | -110.9 | 0.003 | 1.00 | -0.339 | -0.351 |
| 5 | london | 04 | -0.343 | -109.9 | 0.003 | 1.00 | -0.332 | -0.378 |
| 5 | asia | 01 | -0.372 | -109.1 | 0.003 | 1.00 | -0.355 | -0.411 |
| 5 | asia | 22 | -0.369 | -108.6 | 0.003 | 1.00 | -0.357 | -0.404 |
| 5 | london | 03 | -0.325 | -106.7 | 0.003 | 1.00 | -0.321 | -0.356 |
| 5 | asia | 20 | -0.351 | -104.6 | 0.003 | 1.00 | -0.341 | -0.383 |
| 5 | asia | 19 | -0.348 | -102.5 | 0.003 | 1.00 | -0.344 | -0.365 |
| 5 | close | 15 | -0.321 | -101.3 | 0.003 | 1.00 | -0.318 | -0.340 |
| 5 | london | 07 | -0.306 | -99.6 | 0.003 | 1.00 | -0.303 | -0.324 |

### 2. Variance ratio VR(q) and Hurst (1.0 = random walk; <1 reverting; edge-bias corrected), cell = value (null) p_family
| session | VR5 | VR15 | VR30 | VR60 | VR120 | Hurst |
|--|--|--|--|--|--|--|
| asia | 0.412 (0.998) p0.016** | 0.208 (0.997) p0.016** | 0.146 (0.997) p0.016** | 0.113 (0.997) p0.016** | 0.096 (0.998) p0.016** | 0.268 (0.500) p0.016** |
| london | 0.323 (0.998) p0.016** | 0.181 (0.997) p0.016** | 0.142 (0.997) p0.016** | 0.117 (0.997) p0.016** | 0.097 (0.997) p0.016** | 0.314 (0.500) p0.016** |
| pre | 0.418 (0.997) p0.016** | 0.293 (0.997) p0.016** | - | - | - | 0.339 (0.500) p0.016** |
| nyam | 0.359 (0.998) p0.016** | 0.241 (0.997) p0.016** | 0.209 (0.997) p0.016** | - | - | 0.346 (0.500) p0.016** |
| nypm | 0.340 (0.997) p0.016** | 0.216 (0.997) p0.016** | 0.183 (0.996) p0.016** | 0.171 (0.995) p0.016** | - | 0.360 (0.499) p0.016** |
| close | 0.319 (0.998) p0.016** | 0.175 (0.998) p0.016** | 0.134 (0.998) p0.016** | - | - | 0.255 (0.500) p0.016** |
| rth | 0.344 (0.998) p0.016** | 0.220 (0.997) p0.016** | 0.186 (0.996) p0.016** | 0.167 (0.995) p0.016** | 0.156 (0.995) p0.016** | 0.377 (0.500) p0.016** |

### 3. Day types (ex-post labels of the RTH day)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| day|trend | 0.401 | 3140 | 0.484 | -9.6 | 0.016** | 1.00 | 0.392 | 0.420 | stable |
| day|range | 0.301 | 3140 | 0.244 | +7.4 | 0.016** | 0.93 | 0.304 | 0.298 | stable |
| day|er | 0.422 | 3140 | 0.481 | -12.0 | 0.016** | 1.00 | 0.419 | 0.428 | stable |
| day|ib_none | 0.016 | 3140 | 0.002 | +16.8 | 0.016** | 1.00 | 0.014 | 0.019 | stable |
| day|ib_one | 0.621 | 3140 | 0.542 | +9.1 | 0.016** | 1.00 | 0.610 | 0.645 | stable |
| day|ib_both | 0.364 | 3140 | 0.456 | -10.6 | 0.016** | 1.00 | 0.376 | 0.336 | stable |
| day|ib_one_closebeyond | 0.614 | 1949 | 0.784 | -19.4 | 0.016** | 1.00 | 0.624 | 0.583 | stable |

### 4. 1A -> 2A continuation vs give-back-half from the session open (A = 3 x ATR14(5m)); value = P(continue | resolved)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| cont|asia | 0.152 | 947 | 0.403 | -24.7 | 0.016** | 1.00 | 0.156 | 0.126 | stable |
| cont|london | 0.118 | 2778 | 0.495 | -42.0 | 0.016** | 1.00 | 0.121 | 0.110 | stable |
| cont|pre | 0.409 | 702 | 0.411 | -0.2 | 1.000 | 0.57 | 0.378 | 0.452 | unstable |
| cont|nyam | 0.194 | 1087 | 0.396 | -21.1 | 0.016** | 1.00 | 0.161 | 0.226 | stable |
| cont|nypm | 0.227 | 856 | 0.394 | -19.2 | 0.016** | 1.00 | 0.228 | 0.215 | stable |
| cont|close | 0.125 | 288 | 0.377 | -21.1 | 0.016** | 1.00 | 0.122 | 0.143 | stable |
| cont|rth | 0.221 | 2136 | 0.403 | -21.2 | 0.016** | 1.00 | 0.209 | 0.234 | stable |

### 5. Gap fill by size bucket (b0 .05-.10, b1 .10-.25, b2 .25-.50, b3 >.50 of the 20-day mean RTH range); day = filled during RTH, h1 = within 60 min
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| gap|b0|day | 0.919 | 209 | 0.884 | +1.3 | 1.000 | 0.64 | 0.922 | 0.904 | stable |
| gap|b0|h1 | 0.809 | 209 | 0.720 | +2.2 | 0.852 | 0.71 | 0.803 | 0.799 | stable |
| gap|b1|day | 0.769 | 635 | 0.763 | +0.3 | 1.000 | 0.43 | 0.782 | 0.722 | unstable |
| gap|b1|h1 | 0.554 | 635 | 0.478 | +3.3 | 0.115 | 0.79 | 0.562 | 0.537 | stable |
| gap|b2|day | 0.525 | 804 | 0.552 | -1.4 | 1.000 | 0.64 | 0.528 | 0.513 | stable |
| gap|b2|h1 | 0.250 | 804 | 0.166 | +5.7 | 0.016** | 1.00 | 0.257 | 0.233 | stable |
| gap|b3|day | 0.204 | 1238 | 0.190 | +1.3 | 1.000 | 0.79 | 0.210 | 0.191 | stable |
| gap|b3|h1 | 0.041 | 1238 | 0.010 | +12.2 | 0.016** | 0.93 | 0.036 | 0.050 | stable |

### 6. Level reaction: first touch -> bounce (0.5A reverse) vs break-through (0.5A beyond) within 60 min; value = P(bounce)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| rx|PD|asia | 0.729 | 1387 | 0.365 | +35.3 | 0.016** | 1.00 | 0.739 | 0.691 | stable |
| rx|PD|london | 0.642 | 2107 | 0.390 | +27.2 | 0.016** | 1.00 | 0.633 | 0.662 | stable |
| rx|PD|pre | 0.432 | 1336 | 0.396 | +2.4 | 0.770 | 0.86 | 0.449 | 0.399 | stable |
| rx|PD|nyam | 0.518 | 1538 | 0.423 | +7.2 | 0.016** | 1.00 | 0.525 | 0.503 | stable |
| rx|PD|nypm | 0.504 | 1249 | 0.420 | +6.1 | 0.016** | 1.00 | 0.500 | 0.512 | stable |
| rx|PD|close | 0.516 | 707 | 0.411 | +6.1 | 0.016** | 0.93 | 0.528 | 0.484 | stable |
| rx|ON|nyam | 0.616 | 1818 | 0.424 | +16.6 | 0.016** | 1.00 | 0.634 | 0.594 | stable |
| rx|ON|nypm | 0.541 | 1395 | 0.420 | +10.0 | 0.016** | 1.00 | 0.551 | 0.519 | stable |
| rx|ON|close | 0.570 | 827 | 0.411 | +11.1 | 0.016** | 1.00 | 0.573 | 0.566 | stable |
| rx|IB|nyam | 0.668 | 2407 | 0.425 | +27.0 | 0.016** | 1.00 | 0.675 | 0.668 | stable |
| rx|IB|nypm | 0.598 | 2259 | 0.421 | +20.0 | 0.016** | 1.00 | 0.590 | 0.631 | stable |
| rx|IB|close | 0.551 | 1275 | 0.412 | +11.0 | 0.016** | 1.00 | 0.529 | 0.598 | stable |
| rx|VW1|nyam | 0.575 | 4199 | 0.418 | +22.0 | 0.016** | 1.00 | 0.579 | 0.573 | stable |
| rx|VW1|nypm | 0.572 | 3156 | 0.422 | +17.7 | 0.016** | 1.00 | 0.575 | 0.571 | stable |
| rx|VW1|close | 0.560 | 2067 | 0.413 | +13.9 | 0.016** | 1.00 | 0.543 | 0.596 | stable |
| rx|VW2|nyam | 0.677 | 3179 | 0.427 | +32.7 | 0.016** | 1.00 | 0.688 | 0.660 | stable |
| rx|VW2|nypm | 0.681 | 2251 | 0.426 | +27.6 | 0.016** | 1.00 | 0.676 | 0.708 | stable |
| rx|VW2|close | 0.748 | 1170 | 0.417 | +28.7 | 0.016** | 1.00 | 0.748 | 0.756 | stable |
| rx|RN|asia | 0.472 | 4281 | 0.474 | -0.9 | 1.000 | 0.57 | 0.467 | 0.479 | unstable |
| rx|RN|london | 0.476 | 6730 | 0.477 | -0.2 | 1.000 | 0.57 | 0.472 | 0.480 | unstable |
| rx|RN|pre | 0.450 | 1343 | 0.453 | -0.7 | 1.000 | 0.71 | 0.452 | 0.435 | stable |
| rx|RN|nyam | 0.467 | 3029 | 0.470 | -1.4 | 1.000 | 0.64 | 0.464 | 0.467 | stable |
| rx|RN|nypm | 0.475 | 3037 | 0.474 | +0.4 | 1.000 | 0.71 | 0.472 | 0.477 | REGIME(2023+ only) |
| rx|RN|close | 0.476 | 1267 | 0.473 | +1.0 | 1.000 | 0.50 | 0.471 | 0.482 | REGIME(2023+ only) |

### 7. Failed break (close .25A beyond, back inside within 10 bars): fade follow-through P(0.5A back before 0.5A out)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| fb|PD|asia | 0.219 | 908 | 0.500 | -19.1 | 0.016** | 1.00 | 0.228 | 0.197 | stable |
| fb|PD|london | 0.249 | 1581 | 0.501 | -24.3 | 0.016** | 1.00 | 0.247 | 0.250 | stable |
| fb|PD|pre | 0.327 | 851 | 0.498 | -9.1 | 0.016** | 1.00 | 0.315 | 0.348 | stable |
| fb|PD|nyam | 0.289 | 1072 | 0.500 | -17.1 | 0.016** | 1.00 | 0.283 | 0.292 | stable |
| fb|PD|nypm | 0.211 | 942 | 0.501 | -20.0 | 0.016** | 1.00 | 0.209 | 0.215 | stable |
| fb|PD|close | 0.143 | 511 | 0.499 | -17.6 | 0.016** | 1.00 | 0.148 | 0.145 | stable |
| fb|ON|nyam | 0.273 | 962 | 0.500 | -15.6 | 0.016** | 1.00 | 0.277 | 0.241 | stable |
| fb|ON|nypm | 0.231 | 985 | 0.502 | -19.1 | 0.016** | 1.00 | 0.250 | 0.180 | stable |
| fb|ON|close | 0.203 | 580 | 0.499 | -15.2 | 0.016** | 1.00 | 0.207 | 0.188 | stable |
| fb|IB|nyam | 0.283 | 976 | 0.500 | -18.0 | 0.016** | 1.00 | 0.277 | 0.253 | stable |
| fb|IB|nypm | 0.244 | 1618 | 0.500 | -27.8 | 0.016** | 1.00 | 0.250 | 0.213 | stable |
| fb|IB|close | 0.203 | 905 | 0.500 | -18.3 | 0.016** | 1.00 | 0.208 | 0.185 | stable |

### 8. Where the range forms
RTH range increments by bin: 9:30 40.6%, 10:00 23.0%, 11:00 10.9%, 12:00 7.1%, 13:00 6.9%, 14:00 6.9%, 15:00 4.6%
Label-day range increments by ET hour (percent of the day): 00h 1.4, 01h 1.7, 02h 3.2, 03h 4.0, 04h 3.2, 05h 2.5, 06h 2.2, 07h 3.1, 08h 10.3, 09h 6.2, 10h 5.9, 11h 3.4, 12h 2.6, 13h 2.8, 14h 3.5, 15h 2.2, 16h 1.3, 18h 23.0, 19h 5.3, 20h 4.9, 21h 3.4, 22h 2.2, 23h 1.6

### 9. Room and liquidity (all years, raw-frame $, 1 lot)
| session | ATR14(5m) $ | A=3xATR5 $ | RT cost $ | room(1 ATR5) | room(A) | median 5-min vol | 1.7% cap (contracts/5min) | lots for $1,200 at 3xATR5 stop |
|--|--|--|--|--|--|--|--|--|
| asia | nan | nan | nan | nan | nan | nan | nan | nan |
| london | 51 | 154 | 254 | 0.20 | 0.61 | 452 | 11.0 | 7.8 |
| pre | 64 | 192 | 254 | 0.25 | 0.76 | 2486 | 55.0 | 6.3 |
| nyam | 67 | 202 | 254 | 0.26 | 0.79 | 2373 | 52.0 | 6.0 |
| nypm | 64 | 192 | 254 | 0.25 | 0.76 | 1239 | 33.0 | 6.2 |
| close | 63 | 189 | 254 | 0.25 | 0.74 | 730 | 27.0 | 6.4 |

room(A) by year: asia: ; london: 2013:0.6 2014:0.6 2015:0.7 2016:0.7 2017:0.6 2018:0.6 2019:0.6 2020:0.6 2021:0.7 2022:0.7 2023:0.6 2024:0.6 2025:0.6 2026:0.5; pre: 2013:0.8 2014:0.7 2015:0.8 2016:0.8 2017:0.8 2018:0.8 2019:0.8 2020:0.7 2021:0.8 2022:0.9 2023:0.8 2024:0.7 2025:0.8 2026:0.7; nyam: 2013:0.9 2014:0.8 2015:0.9 2016:0.9 2017:0.8 2018:0.8 2019:0.8 2020:0.8 2021:0.9 2022:1.0 2023:0.9 2024:0.7 2025:0.8 2026:0.7; nypm: 2013:0.8 2014:0.7 2015:0.8 2016:0.8 2017:0.8 2018:0.8 2019:0.8 2020:0.8 2021:0.8 2022:0.9 2023:0.8 2024:0.7 2025:0.8 2026:0.7; close: 2013:0.8 2014:0.7 2015:0.8 2016:0.8 2017:0.8 2018:0.8 2019:0.8 2020:0.8 2021:0.8 2022:0.8 2023:0.8 2024:0.7 2025:0.7 2026:0.7

### 11. Map rows that become book candidates under the FROZEN rule (p_family <= .05 AND room_A(session) > 2.0)
| map row | direction | stat | p_family | room_A | year sign share | stability | 1.7% cap >= 1 contract/5min in session |
|--|--|--|--|--|--|--|--|
| rx|PD|asia | level-bounce | +0.729 | 0.016 | nan | 1.00 | stable | NO (illiquid) |
| fb|PD|asia | level-break | +0.219 | 0.016 | nan | 1.00 | stable | NO (illiquid) |
| vr|asia|5 | reversion | +0.412 | 0.016 | nan | 1.00 | stable | NO (illiquid) |
| vr|asia|15 | reversion | +0.208 | 0.016 | nan | 1.00 | stable | NO (illiquid) |
| vr|asia|30 | reversion | +0.146 | 0.016 | nan | 1.00 | stable | NO (illiquid) |
| vr|asia|60 | reversion | +0.113 | 0.016 | nan | 1.00 | stable | NO (illiquid) |
| vr|asia|120 | reversion | +0.096 | 0.016 | nan | 1.00 | stable | NO (illiquid) |
| hurst|asia | reversion | +0.268 | 0.016 | nan | 1.00 | stable | NO (illiquid) |

### RV extra: spread half-life (AR(1) of x minus its 120-min mean, 5-min sampling) and stability
| session | phi(5 min) all years | half-life min | years with half-life < 60 min / years |
|--|--|--|--|
| london | 0.827 | 18 | 14 / 14 |
| nyam | 0.872 | 25 | 14 / 14 |
| nypm | 0.887 | 29 | 14 / 14 |
| close | 0.783 | 14 | 14 / 14 |

RV note: spread = causal beta-hedged pseudo-price of the two legs (beta from the previous 20 label days of 5-min returns; prereg sha fa5c5c13.. + addendum 1); sessions analysed have both legs printing in >= 90% of minutes: london, pre, nyam, nypm, close. Round-number rows are meaningless for a spread and not used. Cost/room are for the integer hedge unit (a:b contracts) with BOTH legs paid (PROXY-STD fees, 1 tick in + 2 ticks stop slip per leg). Base: 1-min .v.0 percent frame, data end 2026-10-16.

## RV 6E6J - relative-value spread character map (CHAR-B via char_lib, 2026-11-06T01:13Z)
Base: RV_6E6J CME front-month (.v.0) 1-min bars from 2013-01 to 2026-10, percent frame (multiplicative roll-adjusted), 1-min approximation (no tick path), 3290 usable label days; ET clock, sessions asia 18:00-02:00 / london 02:00-08:30 / pre 08:30-09:30 / nyam 09:30-12:00 / nypm 12:00-15:00 / close 15:00-16:55. Nulls: within-year shuffled-day (AC B=300; structure B=100 worlds; levels recomputed on the shuffled path; round numbers 60 random grid phases); p_family = Westfall-Young max-|z| over the block (AC family 153 cells, structure family 92 cells). `**` p_family<=.05, `*` <=.10. Prereg sha256 980bedf6bad3f1669de9efb93831fa4622d88577c892d9359b7f57ba93c9dbcf. Descriptive only: no PASS, nothing live.

### Plain paragraph
At 1 minute every session has negative autocorrelation (-0.230 to -0.069; bid-ask bounce / last-print noise, not a tradable edge by itself). asia: reverts at 5/15/30 min (-0.060, -0.037, -0.028). london: reverts at 5 min (-0.029). pre: reverts at 5 min (-0.024). nyam: reverts at 5 min (-0.037). nypm: reverts at 5/15 min (-0.083, -0.035). close: reverts at 5/15/30 min (-0.137, -0.091, -0.058). Day types (RTH): 46% trend days (efficiency ratio >= .5; shuffled null 51%, p_fam 0.016), 26% range days (<.25; null 23%, p_fam 0.049); the IB (09:30-10:30) is extended on one side only on 67% of days and on both on 30%, and a one-sided extension closes beyond the IB edge 66% of the time (null 72%). RTH variance ratio at 30 min 0.653 (shuffled null 0.998, p_fam 0.016); Hurst 0.472. The RTH range forms 9:30 (36%), 10:00 (32%), 11:00 (12%) of the range increments. Level reactions that beat the family null: PD|asia bounces 44% of touches (more than the shuffled null 37%); ON|nypm bounces 46% of touches (more than the shuffled null 35%); ON|close bounces 42% of touches (more than the shuffled null 35%); IB|nyam bounces 43% of touches (more than the shuffled null 40%); IB|nypm bounces 42% of touches (more than the shuffled null 37%); IB|close bounces 43% of touches (more than the shuffled null 36%); VW1|nyam bounces 44% of touches (more than the shuffled null 40%); VW1|nypm bounces 43% of touches (more than the shuffled null 38%); VW1|close bounces 42% of touches (more than the shuffled null 37%); VW2|nyam bounces 46% of touches (more than the shuffled null 39%); VW2|nypm bounces 44% of touches (more than the shuffled null 35%); VW2|close bounces 44% of touches (more than the shuffled null 35%). Failed-break follow-through beating the null: PD|nyam 42% (null 50%); PD|nypm 40% (null 50%); PD|close 31% (null 50%); ON|close 41% (null 50%); IB|nypm 44% (null 50%); IB|close 37% (null 50%). Room (median 3xATR14(5m) $ / round-trip cost $97 per lot): asia 2.0x, london 3.3x, pre 3.9x, nyam 4.3x, nypm 3.2x, close 2.3x (1xATR5 room 1.4x in nyam, 0.7x in asia).

### 1. Autocorrelation of h-min returns (corr(past h, next h), both inside the session), pooled; cell = corr (pre-2023 mean | 2023+ mean) p_family
| session | 1 min | 5 min | 15 min | 30 min | 60 min | 120 min |
|--|--|--|--|--|--|--|
| asia | -0.104 (-0.112|-0.097) p0.003** ys1.00 | -0.060 (-0.074|-0.047) p0.003** ys1.00 | -0.037 (-0.051|-0.014) p0.003** ys0.86 | -0.028 (-0.043|-0.003) p0.003** ys0.86 | -0.012 (-0.031|+0.002) p0.990 ys0.79 | -0.011 (-0.044|+0.011) p1.000 ys0.79 |
| london | -0.074 (-0.089|-0.035) p0.003** ys1.00 | -0.029 (-0.039|-0.017) p0.003** ys1.00 | -0.010 (-0.015|-0.001) p0.243 ys0.86 | -0.006 (-0.013|+0.009) p1.000 ys0.57 | +0.013 (+0.002|+0.038) p1.000 ys0.64 | +0.013 (+0.002|+0.036) p1.000 ys0.57 |
| pre | -0.069 (-0.078|-0.042) p0.003** ys1.00 | -0.024 (-0.020|-0.044) p0.007** ys0.71 | +0.017 (+0.026|-0.016) p1.000 ys0.64 | +0.018 (+0.031|-0.014) p1.000 ys0.57 | - | - |
| nyam | -0.091 (-0.105|-0.031) p0.003** ys1.00 | -0.037 (-0.051|-0.026) p0.003** ys1.00 | -0.016 (-0.022|-0.008) p0.236 ys0.79 | -0.003 (-0.008|-0.006) p1.000 ys0.50 | +0.010 (+0.010|+0.010) p1.000 ys0.57 | - |
| nypm | -0.209 (-0.151|-0.066) p0.003** ys1.00 | -0.083 (-0.090|-0.031) p0.003** ys0.86 | -0.035 (-0.039|-0.033) p0.003** ys0.86 | -0.008 (-0.013|-0.005) p1.000 ys0.57 | -0.018 (-0.027|-0.015) p1.000 ys0.64 | - |
| close | -0.230 (-0.170|-0.097) p0.003** ys1.00 | -0.137 (-0.139|-0.067) p0.003** ys1.00 | -0.091 (-0.104|-0.053) p0.003** ys1.00 | -0.058 (-0.058|-0.072) p0.003** ys0.93 | - | - |

Hour cells (h >= 5) beating the family null, top 14 by |z| (hour = ET hour of the decision bar):
| h | session | hour ET | corr | z | p_family | year sign share | pre-2023 | 2023+ |
|--|--|--|--|--|--|--|--|--|
| 5 | close | 16 | -0.171 | -39.7 | 0.003 | 1.00 | -0.170 | -0.096 |
| 5 | close | 15 | -0.115 | -28.8 | 0.003 | 1.00 | -0.119 | -0.051 |
| 5 | nypm | 12 | -0.093 | -24.2 | 0.003 | 1.00 | -0.099 | -0.061 |
| 5 | asia | 18 | -0.088 | -20.8 | 0.003 | 1.00 | -0.098 | -0.070 |
| 5 | nypm | 13 | -0.084 | -20.0 | 0.003 | 0.79 | -0.092 | -0.018 |
| 5 | nypm | 14 | -0.072 | -17.9 | 0.003 | 0.79 | -0.079 | -0.009 |
| 5 | nyam | 11 | -0.069 | -16.5 | 0.003 | 0.93 | -0.087 | -0.048 |
| 5 | asia | 19 | -0.066 | -16.2 | 0.003 | 0.93 | -0.084 | -0.027 |
| 5 | asia | 00 | -0.068 | -15.6 | 0.003 | 0.86 | -0.079 | -0.041 |
| 5 | asia | 20 | -0.063 | -15.6 | 0.003 | 1.00 | -0.077 | -0.046 |
| 5 | asia | 23 | -0.065 | -15.4 | 0.003 | 0.93 | -0.098 | -0.045 |
| 5 | london | 07 | -0.058 | -13.7 | 0.003 | 0.93 | -0.061 | -0.073 |
| 15 | close | 16 | -0.103 | -13.7 | 0.003 | 0.93 | -0.135 | -0.010 |
| 15 | close | 15 | -0.084 | -13.2 | 0.003 | 1.00 | -0.086 | -0.078 |

### 2. Variance ratio VR(q) and Hurst (1.0 = random walk; <1 reverting; edge-bias corrected), cell = value (null) p_family
| session | VR5 | VR15 | VR30 | VR60 | VR120 | Hurst |
|--|--|--|--|--|--|--|
| asia | 0.802 (0.999) p0.016** | 0.730 (0.998) p0.016** | 0.703 (0.997) p0.016** | 0.686 (0.996) p0.016** | 0.686 (0.995) p0.016** | 0.475 (0.499) p0.016** |
| london | 0.874 (0.998) p0.016** | 0.840 (0.997) p0.016** | 0.834 (0.997) p0.016** | 0.835 (0.996) p0.016** | 0.848 (0.996) p0.016** | 0.495 (0.500) p0.639 |
| pre | 0.878 (0.999) p0.016** | 0.855 (0.999) p0.016** | - | - | - | 0.488 (0.500) p0.098* |
| nyam | 0.846 (0.999) p0.016** | 0.802 (0.998) p0.016** | 0.791 (0.999) p0.016** | - | - | 0.481 (0.500) p0.016** |
| nypm | 0.642 (0.998) p0.016** | 0.568 (0.998) p0.016** | 0.545 (0.998) p0.016** | 0.542 (0.998) p0.016** | - | 0.465 (0.500) p0.016** |
| close | 0.589 (0.998) p0.016** | 0.473 (0.997) p0.016** | 0.430 (0.996) p0.016** | - | - | 0.411 (0.499) p0.016** |
| rth | 0.739 (0.998) p0.016** | 0.675 (0.998) p0.016** | 0.653 (0.998) p0.016** | 0.637 (0.999) p0.016** | 0.613 (0.997) p0.016** | 0.472 (0.500) p0.016** |

### 3. Day types (ex-post labels of the RTH day)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| day|trend | 0.456 | 3290 | 0.510 | -5.9 | 0.016** | 0.79 | 0.446 | 0.469 | stable |
| day|range | 0.261 | 3290 | 0.230 | +4.0 | 0.049** | 0.64 | 0.270 | 0.245 | stable |
| day|er | 0.464 | 3290 | 0.500 | -7.2 | 0.016** | 0.86 | 0.458 | 0.474 | stable |
| day|ib_none | 0.033 | 3290 | 0.013 | +12.2 | 0.016** | 0.93 | 0.035 | 0.033 | stable |
| day|ib_one | 0.665 | 3290 | 0.627 | +4.7 | 0.016** | 0.79 | 0.646 | 0.702 | stable |
| day|ib_both | 0.302 | 3290 | 0.360 | -7.3 | 0.016** | 0.86 | 0.320 | 0.266 | stable |
| day|ib_one_closebeyond | 0.664 | 2188 | 0.723 | -6.2 | 0.016** | 0.93 | 0.661 | 0.669 | stable |

### 4. 1A -> 2A continuation vs give-back-half from the session open (A = 3 x ATR14(5m)); value = P(continue | resolved)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| cont|asia | 0.374 | 3113 | 0.471 | -11.2 | 0.016** | 1.00 | 0.364 | 0.393 | stable |
| cont|london | 0.418 | 3288 | 0.461 | -4.7 | 0.016** | 0.93 | 0.407 | 0.445 | stable |
| cont|pre | 0.429 | 1584 | 0.488 | -5.7 | 0.016** | 0.79 | 0.424 | 0.429 | stable |
| cont|nyam | 0.401 | 2578 | 0.445 | -4.6 | 0.016** | 0.79 | 0.402 | 0.385 | stable |
| cont|nypm | 0.357 | 1446 | 0.464 | -10.7 | 0.016** | 0.93 | 0.374 | 0.312 | stable |
| cont|close | 0.336 | 1000 | 0.477 | -11.0 | 0.016** | 0.86 | 0.343 | 0.278 | stable |
| cont|rth | 0.402 | 3050 | 0.448 | -5.3 | 0.016** | 0.86 | 0.403 | 0.388 | stable |

### 5. Gap fill by size bucket (b0 .05-.10, b1 .10-.25, b2 .25-.50, b3 >.50 of the 20-day mean RTH range); day = filled during RTH, h1 = within 60 min
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| gap|b0|day | 0.869 | 153 | 0.856 | +0.5 | 1.000 | 0.50 | 0.851 | 0.913 | REGIME(2023+ only) |
| gap|b0|h1 | 0.765 | 153 | 0.665 | +2.9 | 0.197 | 0.86 | 0.759 | 0.793 | stable |
| gap|b1|day | 0.733 | 475 | 0.724 | +0.4 | 1.000 | 0.50 | 0.723 | 0.763 | REGIME(2023+ only) |
| gap|b1|h1 | 0.512 | 475 | 0.441 | +3.0 | 0.164 | 0.71 | 0.491 | 0.579 | stable |
| gap|b2|day | 0.476 | 685 | 0.528 | -2.9 | 0.246 | 0.71 | 0.490 | 0.432 | stable |
| gap|b2|h1 | 0.197 | 685 | 0.202 | -0.3 | 1.000 | 0.57 | 0.204 | 0.184 | REGIME(2023+ only) |
| gap|b3|day | 0.183 | 1823 | 0.169 | +1.5 | 1.000 | 0.50 | 0.203 | 0.161 | unstable |
| gap|b3|h1 | 0.038 | 1823 | 0.024 | +4.0 | 0.033** | 0.71 | 0.044 | 0.035 | stable |

### 6. Level reaction: first touch -> bounce (0.5A reverse) vs break-through (0.5A beyond) within 60 min; value = P(bounce)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| rx|PD|asia | 0.441 | 2093 | 0.366 | +7.0 | 0.016** | 0.86 | 0.443 | 0.425 | stable |
| rx|PD|london | 0.412 | 2835 | 0.389 | +2.3 | 0.803 | 0.79 | 0.418 | 0.404 | stable |
| rx|PD|pre | 0.391 | 1120 | 0.373 | +1.2 | 1.000 | 0.64 | 0.387 | 0.400 | stable |
| rx|PD|nyam | 0.400 | 1555 | 0.394 | +0.5 | 1.000 | 0.43 | 0.389 | 0.436 | REGIME(2023+ only) |
| rx|PD|nypm | 0.384 | 975 | 0.356 | +1.9 | 0.984 | 0.64 | 0.376 | 0.402 | stable |
| rx|PD|close | 0.369 | 529 | 0.354 | +0.6 | 1.000 | 0.64 | 0.388 | 0.385 | stable |
| rx|ON|nyam | 0.420 | 2036 | 0.386 | +3.2 | 0.115 | 0.86 | 0.426 | 0.411 | stable |
| rx|ON|nypm | 0.458 | 1164 | 0.347 | +8.7 | 0.016** | 1.00 | 0.449 | 0.484 | stable |
| rx|ON|close | 0.424 | 557 | 0.349 | +3.6 | 0.049** | 0.79 | 0.415 | 0.466 | stable |
| rx|IB|nyam | 0.430 | 3014 | 0.396 | +4.3 | 0.016** | 0.86 | 0.432 | 0.432 | stable |
| rx|IB|nypm | 0.423 | 2161 | 0.366 | +6.0 | 0.016** | 0.93 | 0.436 | 0.382 | stable |
| rx|IB|close | 0.425 | 1025 | 0.362 | +4.3 | 0.016** | 0.93 | 0.430 | 0.421 | stable |
| rx|VW1|nyam | 0.438 | 5104 | 0.396 | +6.6 | 0.016** | 1.00 | 0.434 | 0.447 | stable |
| rx|VW1|nypm | 0.428 | 3145 | 0.375 | +6.1 | 0.016** | 0.93 | 0.428 | 0.420 | stable |
| rx|VW1|close | 0.416 | 1712 | 0.373 | +3.9 | 0.049** | 0.93 | 0.410 | 0.443 | stable |
| rx|VW2|nyam | 0.456 | 3686 | 0.392 | +8.1 | 0.016** | 1.00 | 0.454 | 0.462 | stable |
| rx|VW2|nypm | 0.436 | 1899 | 0.352 | +8.3 | 0.016** | 1.00 | 0.421 | 0.465 | stable |
| rx|VW2|close | 0.443 | 810 | 0.345 | +6.0 | 0.016** | 1.00 | 0.456 | 0.456 | stable |
| rx|RN|asia | 0.424 | 7126 | 0.425 | -0.5 | 1.000 | 0.57 | 0.422 | 0.430 | unstable |
| rx|RN|london | 0.419 | 11002 | 0.419 | +0.1 | 1.000 | 0.57 | 0.419 | 0.424 | REGIME(2023+ only) |
| rx|RN|pre | 0.403 | 2262 | 0.406 | -0.5 | 1.000 | 0.57 | 0.402 | 0.409 | unstable |
| rx|RN|nyam | 0.420 | 5055 | 0.421 | -0.3 | 1.000 | 0.50 | 0.418 | 0.427 | unstable |
| rx|RN|nypm | 0.423 | 3971 | 0.427 | -1.0 | 1.000 | 0.71 | 0.426 | 0.417 | stable |
| rx|RN|close | 0.411 | 1559 | 0.406 | +0.6 | 1.000 | 0.71 | 0.406 | 0.428 | stable |

### 7. Failed break (close .25A beyond, back inside within 10 bars): fade follow-through P(0.5A back before 0.5A out)
| cell | value | n | null | z | p_family | ys | pre-2023 | 2023+ | read |
|--|--|--|--|--|--|--|--|--|--|
| fb|PD|asia | 0.479 | 1547 | 0.499 | -1.6 | 1.000 | 0.64 | 0.477 | 0.471 | stable |
| fb|PD|london | 0.473 | 2267 | 0.499 | -2.5 | 0.590 | 0.64 | 0.467 | 0.482 | stable |
| fb|PD|pre | 0.460 | 785 | 0.503 | -2.5 | 0.541 | 0.64 | 0.455 | 0.477 | stable |
| fb|PD|nyam | 0.423 | 1195 | 0.499 | -6.2 | 0.016** | 0.93 | 0.410 | 0.450 | stable |
| fb|PD|nypm | 0.404 | 736 | 0.500 | -5.1 | 0.016** | 0.79 | 0.395 | 0.454 | stable |
| fb|PD|close | 0.305 | 390 | 0.499 | -7.8 | 0.016** | 0.93 | 0.292 | 0.368 | stable |
| fb|ON|nyam | 0.491 | 1082 | 0.498 | -0.5 | 1.000 | 0.57 | 0.484 | 0.509 | unstable |
| fb|ON|nypm | 0.476 | 804 | 0.499 | -1.4 | 1.000 | 0.57 | 0.464 | 0.541 | unstable |
| fb|ON|close | 0.405 | 395 | 0.502 | -4.0 | 0.033** | 0.86 | 0.414 | 0.423 | stable |
| fb|IB|nyam | 0.472 | 1431 | 0.501 | -2.0 | 0.984 | 0.79 | 0.475 | 0.455 | stable |
| fb|IB|nypm | 0.444 | 1488 | 0.500 | -4.9 | 0.016** | 0.93 | 0.436 | 0.454 | stable |
| fb|IB|close | 0.370 | 706 | 0.498 | -7.2 | 0.016** | 0.93 | 0.354 | 0.429 | stable |

### 8. Where the range forms
RTH range increments by bin: 9:30 35.5%, 10:00 32.0%, 11:00 12.3%, 12:00 6.8%, 13:00 5.3%, 14:00 5.0%, 15:00 3.0%
Label-day range increments by ET hour (percent of the day): 00h 2.0, 01h 2.8, 02h 6.2, 03h 8.7, 04h 6.6, 05h 4.4, 06h 3.5, 07h 3.6, 08h 6.3, 09h 5.2, 10h 6.0, 11h 3.1, 12h 1.9, 13h 1.6, 14h 2.0, 15h 1.0, 16h 0.7, 18h 11.4, 19h 5.8, 20h 7.2, 21h 4.9, 22h 3.0, 23h 2.0

### 9. Room and liquidity (all years, raw-frame $, 1 lot)
| session | ATR14(5m) $ | A=3xATR5 $ | RT cost $ | room(1 ATR5) | room(A) | median 5-min vol | 1.7% cap (contracts/5min) | lots for $1,200 at 3xATR5 stop |
|--|--|--|--|--|--|--|--|--|
| asia | 64 | 193 | 97 | 0.66 | 1.99 | 84 | 0.7 | 6.2 |
| london | 107 | 321 | 97 | 1.10 | 3.31 | 274 | 2.7 | 3.7 |
| pre | 127 | 380 | 97 | 1.30 | 3.91 | 562 | 5.3 | 3.2 |
| nyam | 141 | 422 | 97 | 1.45 | 4.35 | 643 | 6.3 | 2.8 |
| nypm | 104 | 312 | 97 | 1.07 | 3.22 | 244 | 2.7 | 3.8 |
| close | 76 | 227 | 97 | 0.78 | 2.34 | 105 | 1.0 | 5.3 |

room(A) by year: asia: 2013:2.9 2014:2.0 2015:2.7 2016:2.3 2017:1.8 2018:1.9 2019:1.5 2020:1.6 2021:1.4 2022:2.7 2023:1.7 2024:1.4 2025:1.8 2026:1.6; london: 2013:4.9 2014:3.5 2015:4.7 2016:3.8 2017:2.9 2018:3.4 2019:2.6 2020:3.0 2021:2.5 2022:4.6 2023:2.9 2024:2.4 2025:2.7 2026:2.4; pre: 2013:6.2 2014:4.4 2015:5.7 2016:4.4 2017:3.2 2018:3.8 2019:3.2 2020:3.4 2021:3.0 2022:5.4 2023:3.5 2024:2.9 2025:3.4 2026:2.8; nyam: 2013:6.8 2014:4.7 2015:5.9 2016:4.9 2017:3.4 2018:4.1 2019:3.5 2020:3.9 2021:3.4 2022:6.0 2023:4.0 2024:3.3 2025:3.7 2026:3.1; nypm: 2013:5.0 2014:3.6 2015:4.7 2016:3.7 2017:2.7 2018:3.3 2019:2.6 2020:2.7 2021:2.3 2022:4.4 2023:2.7 2024:2.3 2025:2.7 2026:2.4; close: 2013:3.9 2014:2.7 2015:3.7 2016:2.8 2017:2.1 2018:2.3 2019:1.8 2020:2.0 2021:1.7 2022:3.1 2023:1.9 2024:1.6 2025:2.1 2026:1.7

### 11. Map rows that become book candidates under the FROZEN rule (p_family <= .05 AND room_A(session) > 2.0)
| map row | direction | stat | p_family | room_A | year sign share | stability | 1.7% cap >= 1 contract/5min in session |
|--|--|--|--|--|--|--|--|
| AC|london|5m | reversion | -0.029 | 0.003 | 3.3 | 1.00 |  | yes |
| AC|pre|5m | reversion | -0.024 | 0.007 | 3.9 | 0.71 |  | yes |
| AC|nyam|5m | reversion | -0.037 | 0.003 | 4.3 | 1.00 |  | yes |
| AC|nypm|5m | reversion | -0.083 | 0.003 | 3.2 | 0.86 |  | yes |
| AC|close|5m | reversion | -0.137 | 0.003 | 2.3 | 1.00 |  | yes |
| AC|nypm|15m | reversion | -0.035 | 0.003 | 3.2 | 0.86 |  | yes |
| AC|close|15m | reversion | -0.091 | 0.003 | 2.3 | 1.00 |  | yes |
| AC|close|30m | reversion | -0.058 | 0.003 | 2.3 | 0.93 |  | yes |
| fb|PD|nyam | level-break | +0.423 | 0.016 | 4.3 | 0.93 | stable | yes |
| fb|PD|nypm | level-break | +0.404 | 0.016 | 3.2 | 0.79 | stable | yes |
| fb|PD|close | level-break | +0.305 | 0.016 | 2.3 | 0.93 | stable | yes |
| rx|ON|nypm | level-bounce | +0.458 | 0.016 | 3.2 | 1.00 | stable | yes |
| rx|ON|close | level-bounce | +0.424 | 0.049 | 2.3 | 0.79 | stable | yes |
| fb|ON|close | level-break | +0.405 | 0.033 | 2.3 | 0.86 | stable | yes |
| rx|IB|nyam | level-bounce | +0.430 | 0.016 | 4.3 | 0.86 | stable | yes |
| rx|IB|nypm | level-bounce | +0.423 | 0.016 | 3.2 | 0.93 | stable | yes |
| fb|IB|nypm | level-break | +0.444 | 0.016 | 3.2 | 0.93 | stable | yes |
| rx|IB|close | level-bounce | +0.425 | 0.016 | 2.3 | 0.93 | stable | yes |
| fb|IB|close | level-break | +0.370 | 0.016 | 2.3 | 0.93 | stable | yes |
| rx|VW1|nyam | level-bounce | +0.438 | 0.016 | 4.3 | 1.00 | stable | yes |
| rx|VW1|nypm | level-bounce | +0.428 | 0.016 | 3.2 | 0.93 | stable | yes |
| rx|VW1|close | level-bounce | +0.416 | 0.049 | 2.3 | 0.93 | stable | yes |
| rx|VW2|nyam | level-bounce | +0.456 | 0.016 | 4.3 | 1.00 | stable | yes |
| rx|VW2|nypm | level-bounce | +0.436 | 0.016 | 3.2 | 1.00 | stable | yes |
| rx|VW2|close | level-bounce | +0.443 | 0.016 | 2.3 | 1.00 | stable | yes |
| gap|b3|h1 | level-bounce | +0.038 | 0.033 | 4.3 | 0.71 | stable | yes |
| vr|london|5 | reversion | +0.874 | 0.016 | 3.3 | 1.00 | stable | yes |
| vr|london|15 | reversion | +0.840 | 0.016 | 3.3 | 1.00 | stable | yes |
| vr|london|30 | reversion | +0.834 | 0.016 | 3.3 | 1.00 | stable | yes |
| vr|london|60 | reversion | +0.835 | 0.016 | 3.3 | 1.00 | stable | yes |
| vr|london|120 | reversion | +0.848 | 0.016 | 3.3 | 0.93 | stable | yes |
| vr|pre|5 | reversion | +0.878 | 0.016 | 3.9 | 1.00 | stable | yes |
| vr|pre|15 | reversion | +0.855 | 0.016 | 3.9 | 0.93 | stable | yes |
| vr|nyam|5 | reversion | +0.846 | 0.016 | 4.3 | 1.00 | stable | yes |
| vr|nyam|15 | reversion | +0.802 | 0.016 | 4.3 | 1.00 | stable | yes |
| vr|nyam|30 | reversion | +0.791 | 0.016 | 4.3 | 1.00 | stable | yes |
| hurst|nyam | reversion | +0.481 | 0.016 | 4.3 | 1.00 | stable | yes |
| vr|nypm|5 | reversion | +0.642 | 0.016 | 3.2 | 1.00 | stable | yes |
| vr|nypm|15 | reversion | +0.568 | 0.016 | 3.2 | 0.93 | stable | yes |
| vr|nypm|30 | reversion | +0.545 | 0.016 | 3.2 | 1.00 | stable | yes |
| vr|nypm|60 | reversion | +0.542 | 0.016 | 3.2 | 0.93 | stable | yes |
| hurst|nypm | reversion | +0.465 | 0.016 | 3.2 | 0.79 | stable | yes |
| vr|close|5 | reversion | +0.589 | 0.016 | 2.3 | 1.00 | stable | yes |
| vr|close|15 | reversion | +0.473 | 0.016 | 2.3 | 1.00 | stable | yes |
| vr|close|30 | reversion | +0.430 | 0.016 | 2.3 | 1.00 | stable | yes |
| hurst|close | reversion | +0.411 | 0.016 | 2.3 | 1.00 | stable | yes |
| vr|rth|5 | reversion | +0.739 | 0.016 | 4.3 | 1.00 | stable | yes |
| vr|rth|15 | reversion | +0.675 | 0.016 | 4.3 | 1.00 | stable | yes |
| vr|rth|30 | reversion | +0.653 | 0.016 | 4.3 | 1.00 | stable | yes |
| vr|rth|60 | reversion | +0.637 | 0.016 | 4.3 | 1.00 | stable | yes |
| vr|rth|120 | reversion | +0.613 | 0.016 | 4.3 | 1.00 | stable | yes |
| hurst|rth | reversion | +0.472 | 0.016 | 4.3 | 0.86 | stable | yes |

### RV extra: spread half-life (AR(1) of x minus its 120-min mean, 5-min sampling) and stability
| session | phi(5 min) all years | half-life min | years with half-life < 60 min / years |
|--|--|--|--|
| asia | 0.925 | 44 | 14 / 14 |
| london | 0.928 | 46 | 13 / 14 |
| nyam | 0.917 | 40 | 13 / 14 |
| nypm | 0.806 | 16 | 11 / 14 |
| close | 0.768 | 13 | 12 / 14 |

RV note: spread = causal beta-hedged pseudo-price of the two legs (beta from the previous 20 label days of 5-min returns; prereg sha fa5c5c13.. + addendum 1); sessions analysed have both legs printing in >= 90% of minutes: asia, london, pre, nyam, nypm, close. Round-number rows are meaningless for a spread and not used. Cost/room are for the integer hedge unit (a:b contracts) with BOTH legs paid (PROXY-STD fees, 1 tick in + 2 ticks stop slip per leg). Base: 1-min .v.0 percent frame, data end 2026-10-16.

## RV GC-CL - descriptive correlation only (CHAR-B, 2026-11-06)
Correlation of non-overlapping h-minute log returns of GC and CL by session, percent frame, 1-min .v.0, 2013-01..2026-10-16. Plain reading: GC and CL are essentially uncorrelated (all-years 0.04-0.07, NY-AM 60-min 0.07; 2023+ is slightly NEGATIVE in london/close/nypm), and the NY-AM 60-min correlation flips sign by year (-0.22 in 2019 to +0.35 in 2022; -0.13 in 2026), so there is no stable hedge ratio and therefore no spread to trade; no book built.
| session | h min | 2013-2022 | 2023+ | all |
|--|--|--|--|--|
| asia | 5 | +0.057 | +0.007 | +0.038 |
| asia | 15 | +0.082 | -0.009 | +0.049 |
| asia | 60 | +0.105 | +0.009 | +0.071 |
| close | 5 | +0.058 | -0.124 | -0.005 |
| close | 15 | +0.051 | -0.118 | -0.010 |
| close | 60 | +0.102 | -0.048 | +0.043 |
| london | 5 | +0.103 | -0.093 | +0.044 |
| london | 15 | +0.105 | -0.116 | +0.036 |
| london | 60 | +0.101 | -0.144 | +0.027 |
| nyam | 5 | +0.097 | -0.005 | +0.066 |
| nyam | 15 | +0.091 | +0.010 | +0.067 |
| nyam | 60 | +0.095 | +0.015 | +0.071 |
| nypm | 5 | +0.076 | -0.060 | +0.044 |
| nypm | 15 | +0.089 | -0.064 | +0.049 |
| nypm | 60 | +0.080 | -0.089 | +0.038 |
| pre | 5 | +0.110 | -0.022 | +0.073 |
| pre | 15 | +0.111 | -0.023 | +0.073 |

## 1s-LRS (CHAR-A): tick-scale learned-rule search on the 1-second book tables, ES RTY NQ(control), 2023-08..2026-10 -- NO PRE-2023 EVIDENCE; first test month 2024-05 (X' = no data)
Prereg l2vast/ds3/prereg/T_FIND_1SLRS_prereg.md sha256 100519f33c35ba1204829a8a5437d2e051fe5847eafe357eb234d58c66c2a832 (DECISIONS.md, before any fit). 21 causal 1-s features (returns 5/30/300 s, spread, depth imbalance 1/5/10, microprice offset, OFI 5/30 s, aggressor flow 5/30 s, size-burst and sweep net flow, burst vs prior-day q90, distance to prior-day H/L, overnight H/L and VWAP in prior-day-range units, hour), targets = mid move 30/60/300/1800 s after a 1 s latency, <=6-leaf monotone tree (mom +1 / rev -1), 9-month training windows with purge, 3 seeds (70% subsamples), signal only when |prediction| exceeds the live spread + fee and the training 80th percentile of |pred|, one position, 1-s prints, stop 1.5 training-sd, time stop h, equal-$ $1,200 lots, participation cap. Feature truncation test: 0 failures in 3,948 (ES) and 3,528 (RTY) comparisons; a look-ahead rolling window as negative control fails 778/3,948. Small GP: not run (no GP in the lrs machinery; stated). Cells: session (pre/nyam/nypm/close) x h x mode x seed; each family max-stat is over all cells of the instrument.
| instrument | cells with >=30 trades | positive in L6M and HOLD | tolerant gate | BAR CLEARED | best family p | median HOLD $/wk | median trades |
|--|--|--|--|--|--|--|--|
| ES | 69 | 2 | 0 | 0 | 0.98 | -621 | 1,909 |
| RTY | 77 | 2 | 0 | 0 | 0.01 (one cell, see below) | -544 | 1,523 |
| NQ (control) | 96 | 9 | 0 | 0 | 1.00 | -895 | 2,452 |
Plain sentence: a tree over the 1-s book and flow features can predict the next 30 s-30 min move a little, but not by more than the 1.4-tick (ES) / 2.4-tick (RTY, NQ) round-trip cost on a stable basis: the median cell loses $500-900/wk at equal risk, the few cells that are positive in L6M and HOLD (ES close fade 1800 s; NQ close/nyam fade 1800 s; RTY pre-market momentum 300 s) are negative in PRE (-$270..-1,100/wk), so they are NOW-ONLY REGIME, and the three seeds of a cell disagree. The only family-p hit is RTY pre-market momentum 300 s seed 0 (L6M +318, HOLD +904, MID +940, PRE -1,098 $/wk; placebo p_book .10, family .01 over 77 cells) but seeds 1 and 2 are negative or flat (HOLD +330 / +65, p_book .99 / .21), the walk-forward of its own parameters is negative (6 m -148, 12 m -275 $/wk) and persistence is 38%: not a lead, consistent with the RTY pre-market continuation WATCH item (it is the same session). Nothing clears; Shadow only. Rows in DS3_FIND.md, ledger T2F_<SYM>_1S_LRS, frames with stop/target prices in /mnt/l2/l2vast/instr2_trades/<SYM>/. 1b-c (Z1) was negative and is not repeated; 1b-a (ZL-1) and 1b-d (ZL-2) rows had not landed in MORNING.md when scoring ran and are NOT incorporated (to be added if they produce candidates).

#### 1b-d addendum 2 - per-order anatomy and books of the cells that beat the shifted-time null (ZL-1)
Per filled order, ticks of the instrument, fee $4.84 included, no protective stop vs the map->book stop (3 x the discovery sd of the h-second mid move, min 2 ticks); t = mean / (sd / sqrt(n)) over orders (not day-clustered: at most one order per day and side). Taker-exit column = the same fills exited at the touch instead of passively.

| instrument | session | hold s | stop | orders | fills | mean ticks | sd | t | worst | first / second half | taker-exit mean | captured / fill | adverse(+h) / fill | median queue ahead |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ES | nyam | 60 | none | 369 | 357 | +2.40 | 15.3 | 2.96 | -101 | +2.61 / +2.11 | +1.90 | +0.51 | +2.20 | 32 |
| ES | nyam | 60 | stop 36t | 369 | 357 | +2.05 | 12.5 | 3.10 | -43 | +1.73 / +2.49 | +1.57 | +0.51 | +2.20 | 32 |
| ES | nyam | 300 | none | 369 | 363 | +3.07 | 26.4 | 2.22 | -99 | +3.04 / +3.12 | +2.67 | +0.51 | +2.94 | 32 |
| ES | nyam | 300 | stop 58t | 369 | 363 | +3.20 | 25.9 | 2.35 | -75 | +3.04 / +3.41 | +2.82 | +0.51 | +2.94 | 32 |
| ES | nyam | 1800 | none | 369 | 364 | +5.72 | 57.1 | 1.91 | -200 | +4.87 / +6.84 | +4.79 | +0.51 | +5.15 | 32 |
| ES | nyam | 1800 | stop 143t | 369 | 364 | +5.55 | 57.1 | 1.85 | -160 | +4.94 / +6.36 | +4.65 | +0.51 | +5.15 | 32 |
| NQ | nyam | 30 | none | 515 | 477 | +4.01 | 46.6 | 1.88 | -147 | +3.02 / +6.06 | +2.56 | +0.73 | +4.24 | 2 |
| NQ | nyam | 30 | stop 112t | 515 | 477 | +3.12 | 47.2 | 1.45 | -142 | +2.24 / +4.94 | +1.81 | +0.73 | +4.24 | 2 |
| NQ | nyam | 60 | none | 515 | 477 | +4.17 | 75.4 | 1.21 | -634 | +4.78 / +2.92 | +4.15 | +0.73 | +5.63 | 2 |
| NQ | nyam | 60 | stop 165t | 515 | 477 | +3.50 | 68.8 | 1.11 | -203 | +3.01 / +4.50 | +2.75 | +0.73 | +5.63 | 2 |
| NQ | nyam | 300 | none | 515 | 481 | +7.60 | 161.9 | 1.03 | -1806 | +10.33 / +2.02 | +6.41 | +0.72 | +7.54 | 2 |
| NQ | nyam | 300 | stop 423t | 515 | 481 | +8.48 | 139.1 | 1.34 | -494 | +11.69 / +1.92 | +7.41 | +0.72 | +7.54 | 2 |
| RTY | pre | 300 | none | 104 | 86 | +1.19 | 82.3 | 0.13 | -248 | -2.43 / +7.97 | -0.35 | +1.19 | +1.10 | 3 |
| RTY | pre | 300 | stop 299t | 104 | 86 | -0.39 | 87.5 | -0.04 | -313 | -4.86 / +7.97 | -1.85 | +1.19 | +1.10 | 3 |
| RTY | pre | 1800 | none | 104 | 86 | +10.82 | 116.2 | 0.86 | -379 | -1.34 / +33.53 | +8.66 | +1.19 | +8.87 | 3 |
| RTY | pre | 1800 | stop 396t | 104 | 86 | +10.57 | 117.0 | 0.84 | -401 | -1.74 / +33.53 | +8.43 | +1.19 | +8.87 | 3 |

Multiplicity: the cells are 8 rows picked from CHAR-A's family of 240 per instrument after seeing its map. Against the 8-cell shifted-time family null the ES nyam rows have p_family .005-.02 and NQ nyam 30/60 s .01/.07; against the 240-cell selection family the best cell p (.005) x 240 exceeds 1, so selection alone can produce them. Per-order t-statistics are 1.9-3.1 (ES) and 1.2-1.9 (NQ) before any selection discount.

Books through instr2_eval (stop version, equal-risk lots $1,200 with the session participation cap, placebos NOT run - there is no bar simulator for passive fills; the shifted-time null above plays that role; F=240; no pre-2023 evidence: tick data begin 2023-08, X' partial):

| book | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | corr V0/V2 (daily) | stack k* | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ES nyam h=60 passive | +13 | -139 | -139 | +189 | +171 | +60 | +123 | +83 | -0.00 / -0.00 | 0.00 | FAIL: NOW-ONLY fails (L3M/L6M mean not both > 0) |
| ES nyam h=300 passive | +93 | +198 | +198 | +434 | +182 | -278 | +168 | +12 | 0.01 / 0.02 | 0.00 | pass |
| ES nyam h=1800 passive | +357 | +564 | +564 | +182 | +282 | +219 | +71 | +10 | 0.03 / 0.03 | 5.00 | pass |
| NQ nyam h=30 passive | +262 | +478 | +478 | +381 | +264 | +200 | +111 | +202 | -0.02 / -0.04 | 5.00 | pass |
| NQ nyam h=60 passive | +186 | +505 | +505 | +49 | +16 | +103 | +94 | +61 | 0.00 / -0.01 | 5.00 | pass |

**Plain sentence: with queue-aware passive entries and exits, CHAR-A's prior-day-level + burst continuation turns from a taker plateau that failed the 1-s book into a small positive passive result on ES NY-AM (+2.0 to +5.5 ticks per filled order after fees, positive in every window L1M..X', ~0 correlation to the stack, stack Calmar up at weight 5 for the 30-minute hold) and NQ NY-AM 30 s (+3.1 ticks, positive in all eight windows); it is a REGIME / WATCH candidate, not a lead: 8 rows picked from a family of 240, per-order t 1.2-3.1, 369 / 515 orders over 3.3 years, no pre-2023 evidence, and the result rests on the queue model (proportional cancels; the none-ahead sensitivity and a real-fill check would be needed). RTY pre-market, where the taker book had its plateau, does not beat the shifted-time null (p_family .27-.93) once costs and adverse selection are charged. NQ pre-market pending the NQ night store.**

(1b-d addendum 2 precision note, ZL-1: 'positive in every window L1M..X'' holds only for ES nyam h=1800 and NQ nyam h=30. ES h=60 has L2M/L3M -139 and fails the NOW-ONLY gate; ES h=300 has MID -278; NQ h=60 is positive in all windows but tiny (HOLD +16). Stack k* = 5 for ES h=1800, NQ h=30 and NQ h=60, 0 for ES h=60/300.)

## 1S-FIX (CHAR-A, 2026-11-06T03:2xZ): CORRECTION of every CHAR-A tick-scale book (1b-b T2F1B_*, 1b-DEEP book surface, 1-s learned-rule search T2F_*|1SLRS_*) after audit D1 (autopilot/REPRO_AUDIT_FIND.md): the shared simulator exited a 1-s book 60 s early / on the first bar. LABEL: every number in the 1b-b, 1b-DEEP and 1s-LRS blocks above is SUPERSEDED by this block where they differ.
Prereg addendum l2vast/ds3/prereg/T_FIND_1SFIX_prereg.md sha256 4938d882cd2fa5b9f3ae466225f66877c8c0834834fc30c1090b526c3ca7f555 (DECISIONS.md, before any corrected number); re-run of already-seen cells, so BEST-OF-F unless the full bar is cleared. Simulator: code/instr2/instr2_eval_1s.py generated from the untouched shared instr2_eval.py (md5 54d7350b...); exit convention on every corrected block (one convention, per review note N4): sub-minute time stop = market order at the first 1-s bar with ts >= entry_ts + tstop, FILLED AT THAT BAR'S OPEN, exit_ts = that bar's ts; deadline clock starts at entry_ts (N2); 1-minute or wider bars keep the original branch (N3); explicit bar_s_arg added (N1). Tests: planted time stops 30/60/300/1800 s, sparse path, stop-first, byte equality with the original on 1-min bars, truncation 0/20; ZL-2 independent review ACCEPT. Placebos in the corrected runs re-simulate with the corrected simulator. Same signals, stops, costs, seeds, 100 worlds x shift5/side/days. New cell ids end in '_1sfix'; the 272 frames were regenerated under new names in /mnt/l2/l2vast/instr2_trades/<SYM>/ (ES 75, RTY 89, NQ 108; old frames kept). Z1 confirmed none of its cells went through the 1-s bar simulator; ZL-1/ZL-2 were asked in MORNING.md.

### Which labels change (corrected vs superseded)
| item | superseded (buggy) result | corrected result (instr2_eval_1s) | label now |
|--|--|--|--|
| ES prior-day H/L touch + burst, 60 s (T2F1B_ES, 6 cells) | HOLD -$91..-264/wk, L6M -25..-102, 'loses money as a 1-s book' | HOLD +$13..+605 (5 of 6 > 0; one -43), L6M +176/+89/+128/+148/-10 (5 of 6 > 0) BUT PRE (2024-02..2025-06) -$87..-971 and X' negative in all 6; tolerant gate FAILS (persistence 12-38%); own-parameter walk-forward negative (6m -92, 12m -56); placebo p_book .08-.56 (the HOLD/L6M statistics alone are .01-.11, the stack-gain statistic is the weak one); family p .58 (75-cell corrected set), .05-.26 over the 6 book cells alone; plateau surface HOLD>0 57%, L6M>0 59%, PRE>0 15%, all three 13% | REGIME/WATCH: positive since 2025-11 (L6M/HOLD), negative 2024-25; NOT a plateau; the sentence 'loses money as a 1-s book' in DS3_FIND_FINAL.md is WRONG and is superseded |
| NQ (control) prior-day H/L touch, NY-AM, 30 s (T2F1B_NQ, 6 cells) | HOLD -$106..-265/wk | L6M +199..+673, HOLD +207..+738, PRE +8..+139 (all 6 > 0), X' +374/-120/+269/+137/+195/+220, MID -142..; tolerant gate PASSES in all 6 (persistence .88-1.0); own-parameter walk-forward positive on both lookbacks in all 6 (6m +182..+292, 12m +92..+292); corr to the NQ stack .03-.07; stack Calmar dCalmar at k* 0.000..+0.04 (not up in 4 of 6); placebo p_book .16-.73 (HOLD/L6M statistics alone .01-.25), family p .54-1.00 over the 108 corrected cells, .05-.58 over the 12 book cells; surface HOLD>0 and L6M>0 in 100% of 54 nodes, PRE>0 46% (all three 46%) | NEW WATCH (NQ is the control and the stack's own market; first corrected tick-scale row that passes the tolerant gate and walk-forward; fails the frozen placebo/family/plateau rule: plateau needs PRE>0, family p > .10) |
| RTY pre-market PD touch + burst, 1800 s (T2F1B_RTY, 6 cells) | HOLD +$157..+242, L6M +265..+770, family 1.00 | HOLD +$7..+220, L6M +174..+682, PRE +13..+115, X' -162..+35; tolerant gate passes for 5 of 6 variants (min sample L3M/L6M still marginal in the others), walk-forward positive both lookbacks, placebo p_book .24-.59, family p 1.00 (89 cells) / .67-.95 (12 book cells); surface HOLD>0 91%, L6M>0 100%, PRE>0 61%, all three 54% (unchanged) | REGIME/WATCH unchanged (WATCH_RTY_PREMARKET_SPEC.md stands) |
| RTY pre-market PD touch + burst, 300 s | HOLD +$19..+78 | HOLD -54..+38, L6M -61..+133; surface HOLD>0 20% | collapses: NOT a plateau; the 1800 s horizon is the only one that holds |
| NQ pre-market PD touch + burst, 1800 s | negative | negative (HOLD -330..-35; surface HOLD>0 7%) | NULL (unchanged) |
| 1-s learned-rule search (instr2/lrs-style trees, 96 cells per instrument; 69 / 77 / 96 with >= 30 trades) | ES 69 cells median HOLD -$621, 2 positive in L6M and HOLD, 0 tolerant; RTY 77, -$544, 2, 0; NQ 96, -$895, 9, 0; best family p .80 / .97 / 1.0 | ES median HOLD -$790, 3 positive in L6M and HOLD, 0 with PRE>0, 0 tolerant; RTY -$566, 6 positive (1 with PRE>0), 0 tolerant; NQ -$994, 12 positive (1 with PRE>0), 0 tolerant; walk-forward positive on both lookbacks in 0 / 1 / 5 cells; combined corrected set (book + LRS cells) best family p ES .58, RTY .76, NQ .55 | NULL: the learned-rule conclusion is unchanged (median cell still loses $566-994/wk; no cell has a family p near .10); the earlier '1s-LRS' block's counts are superseded by these |

Bar on the corrected sets (family = book cells + LRS cells of the instrument, 100 worlds): ES 75 cells, positive in L6M and HOLD 7, positive also in PRE 0, tolerant 0, walk-forward both lookbacks 0, placebo p_book <= .10 in 1, best family p 0.584, BAR CLEARED 0. RTY 89 cells: 14 / 9 / tolerant 7 / WF both 7 / p_book <= .10 in 1 / best family p 0.762 / CLEARED 0. NQ (control) 108 cells: 18 / 7 / tolerant 7 / WF both 11 / p_book <= .10 in 0 / best family p 0.545 / CLEARED 0. Ranked rows with every window, maxDD, corr to the stack, stack dCalmar, placebo/family p, walk-forward: DS3_FIND.md (blocks '1S-FIX corrected tick-scale candidate set'); per-world max vectors /mnt/l2/l2vast/ds3/out/find/tick_<SYM>/fix_world_max.npz; surfaces tick_<SYM>/deep_book_surface_fix.csv; ledger programs T2F1B_<SYM>_FIX, T2F_<SYM>_1S_LRS_FIX, T2F_<SYM>_1B_DEEP_FIX appended (old programs untouched).
No cell clears the bar. The one thing the correction changes is that the tick-scale prior-day-level continuation is not a loser: it is a small positive in 2025-11..2026 on ES (60 s) and over 2023-08..2026 on NQ (30 s, the control), flat-to-fragile on RTY pre-market (1800 s only). All three remain best-of-F REGIME/WATCH; the NQ NY-AM 30 s row is the one to re-test forward first (needs no new data; NQ tick tables already arrive) -- a WATCH spec for it has NOT been written yet and would be preregistered separately.

### 1b-d addendum 2 UPDATE (NQ pre-market added; the NQ night store rebuilt after the back/ collision; this table SUPERSEDES the 8-cell table above) - CHAR-A prior-day-level + burst continuation under the passive queue model (ZL-1; prereg l2vast/ds3/prereg/FIND_1BD_addendum2.md; pre-market event store events_pre built from the kept raw mbp-10 with l2v_pre_events.py, validated exactly against events_L13)
Cells are ROWS PICKED AFTER SEEING CHAR-A's map (1 of its 240 per instrument; selection bias stated). Events: first touch of the prior-day RTH high/low by the 1-s mid, buffer 0, burst >= 90% quantile, direction = approach; passive entry 1 s after the touch, hold h, passive exit, fee $4.84 RT; null = same orders shifted forward 120-1800 s on the same day (200 worlds), Westfall-Young over the 11 cells tested.

| instrument | session | hold s | events | placed disc / test | fill rate | net per order disc | net per order test | net per fill | taker-exit net per order | captured half-spread / fill | adverse at +h / fill | z | p cell | p family | beats the null |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ES | nyam | 60 | 428 | 210 / 159 | 0.97 | +2.54 | +2.03 | +2.40 | +1.84 | +0.51 | +2.20 | 4.7 | 0.005 | 0.005 | YES |
| ES | nyam | 300 | 428 | 210 / 159 | 0.98 | +2.98 | +3.08 | +3.07 | +2.63 | +0.51 | +2.94 | 3.0 | 0.010 | 0.025 | YES |
| ES | nyam | 1800 | 428 | 210 / 159 | 0.99 | +4.80 | +6.75 | +5.72 | +4.73 | +0.51 | +5.15 | 3.1 | 0.005 | 0.025 | YES |
| NQ | nyam | 30 | 598 | 340 / 175 | 0.93 | +2.85 | +5.40 | +4.01 | +2.38 | +0.73 | +4.24 | 3.5 | 0.005 | 0.010 | YES |
| NQ | nyam | 60 | 598 | 340 / 175 | 0.93 | +4.51 | +2.61 | +4.17 | +3.84 | +0.73 | +5.63 | 2.6 | 0.010 | 0.090 | YES |
| NQ | nyam | 300 | 598 | 340 / 175 | 0.93 | +9.81 | +1.82 | +7.60 | +5.99 | +0.72 | +7.54 | 2.3 | 0.005 | 0.144 | no |
| NQ | pre | 60 | 111 | 62 / 31 | 0.86 | +9.00 | +6.51 | +9.49 | +6.86 | +3.17 | +7.83 | 2.3 | 0.010 | 0.144 | no |
| NQ | pre | 300 | 111 | 62 / 31 | 0.89 | +15.19 | +14.25 | +16.67 | +18.77 | +3.19 | +19.17 | 1.8 | 0.050 | 0.358 | no |
| NQ | pre | 1800 | 111 | 62 / 31 | 0.90 | +47.72 | +21.16 | +43.03 | +36.32 | +3.15 | +39.39 | 3.5 | 0.005 | 0.010 | YES |
| RTY | pre | 300 | 105 | 69 / 35 | 0.83 | -1.97 | +6.83 | +1.19 | -0.29 | +1.19 | +1.10 | 0.5 | 0.299 | 0.985 | no |
| RTY | pre | 1800 | 105 | 69 / 35 | 0.83 | -1.09 | +28.74 | +10.82 | +7.16 | +1.19 | +8.87 | 1.8 | 0.040 | 0.368 | no |

**6 of 11 CHAR-A cells beat the null under the passive model (family p <= .10, net per order > 0 in both halves, >= 30 fills); see the table for which.**

(1b-d addendum 2 update note, ZL-1: with the NQ night store rebuilt, NQ pre-market h=1800 also BEATS the shifted-time 11-cell null mechanically (p_family .010; per-order net +47.7 disc / +21.2 test NQ ticks, 84 fills) but its per-order t is 1.6 (sd 232 ticks), the 3 x sd stop is 595 ticks (about $2,975 per lot), and through instr2_eval it fails the tolerant gate: L6M -207 and HOLD -94 $/wk, positive only in L1M-L3M, PRE +92, X' +150, corr -0.03, stack k* = 0. NQ pre h=60/300 do not beat the null (p_family .14/.36). RTY pre unchanged (no). So of the 11 cells, 6 pass the mechanical rule; only ES nyam h=300/1800 and NQ nyam h=30/60 give books that pass the tolerant gate, and only ES h=1800 and NQ h=30 are positive in all 8 windows. ES events_pre store is still being rebuilt (not needed by any cell).)

## EVENTS-1S - scheduled-release response at 1-s with L2 spreads: ES, NQ (control), RTY (Z1, 2026-11-06)
Prereg l2vast/ds3/prereg/T2F_EV1S_prereg.md sha256 293fb7dcb28435e9efa763655e4d157cad90271c86aff67f5646ebc8e5bf9165 (DECISIONS.md, filed before any outcome). Data: 1-s tables, ts = bin END, 2023-08-01..2026-10-30, no pre-2023 evidence; calendar = DISCOVER_CALENDAR.csv dates and clock times only (actual/consensus/prior never read). Events and counts (identical for the three instruments, first 20 label days dropped): 08:30 ET CLAIMS 163, CPI 36, GDP 37, NFP 37, PCE 37, PPI 36, RETAIL 37; 10:00 ISM 76; 14:00 FOMC decision 25 (about 12 a year per type except claims: SMALL N). Causal identification: volume shock = trades in [S, S+5) >= 3 x the median of the same window on the previous 20 days. Shock shares: NFP 81-97%, CPI 83-92%, PPI 78-92%, claims about 53%, FOMC 32-72%, ISM 3-45%, GDP/PCE/retail 35-59%. Direction from the first D = 5/10/30 s move (information through S+D only), entry at the quote 1 s later (never before :06), exit 5 s .. 30 min later, cost = measured half-spreads at both fills + $4.84. Truncation test (24 random events per instrument, rows after S+D removed): 24/24 ES, RTY, NQ. 960 / 1,152 / 1,024 cells scored (ES / RTY / NQ; min 15 events). Null = same clock on non-event days (500 worlds, same counts), Westfall-Young max-t across all scored cells.
**Release microstructure (medians):** the spread is 2-4x its pre-release level in the first 5 s (ES 2x, RTY 3-5x on CPI/NFP, NQ 3-4x), still 1.5-3x at 30 s, back to normal by 5 min and 0.5-0.9x of the (widened) pre-release spread at 15 min. Volume in [S, S+5) is 10-14x normal for CPI/NFP/PPI, 6x RTY / 2.7x ES FOMC, 1.4-4.6x for the rest. Depth refill and microprice drift were NOT extracted (only spread and volume).
**Response curves (continuation gross ticks, all events, decision at 30 s; ES / NQ / RTY):** CPI +7 / +30 / +28 at 30 s but -7 / -24 / +1 at 5 min and -13 / -64 / +1 at 30 min (a burst then a give-back); FOMC +10 / +47 / +21 at 30 s, +5 / +26 / +33 at 5 min, +6 / +52 / +47 at 30 min (continuation at every horizon on all three, 25 events); ISM -15 / -66 / -11 at 30 min (reversal); NFP +3 / +40 / +11 at 5 min and +7 / +67 / +1 at 30 min; CLAIMS, GDP, PCE, PPI, RETAIL about zero. Round-trip cost at these moments is 1.6-2.5 ticks (ES), 3.7-12 (RTY), 5-12 (NQ).
| instrument | cells | net > 0 | cells with per-cell p <= .05 | cells with family p <= .10 | beats the null (family, both halves positive, room > 2) | world max t (median / p95) | best cell |
|---|---|---|---|---|---|---|---|
| ES | 960 | 203 | 175 | 0 | 0 | 2.46 / 3.46 | PCE all D10 900 s cont t 2.04, family p .86 |
| NQ | 1,024 | 229 | 91 | 0 | 0 | 2.65 / 3.46 | GDP shock D10 30 s rev t 2.83, family p .32 |
| RTY | 1,152 | 272 | 277 | 2 | 2 | 2.15 / 2.95 | FOMC shock D30 120 s cont t 3.02, family p .044 |
The two RTY rows that beat the null: FOMC decision with a volume shock, decision at 30 s, hold 120 s, continuation (18 events, +45 ticks gross, 4.3 cost, +41 net, +45 / +35 in the two halves, p_family .044) and CPI with a volume shock, 30 s, hold 30 s, continuation (30 events, +33 gross, 7.2 cost, +25.5 net, +42 / +13 in the halves, p_family .098). The same direction is positive but not significant on ES and NQ (CPI +7 / +30 ticks at 30 s). Per-cell p for shock cells is not meaningful (control days rarely carry a shock, so the shock cells have few control events) and is set aside; the family p uses all scored cells.
**Books (frozen map -> book rule, RTY only, instr2_eval_1s, 1 lot, taker, stop 3 x trailing 30-s mid range min 4 ticks, +1 tick on stops):** RTY FOMC-shock D30 h120: 18 trades, +$132 per trade (7 stops), PRE +$155/wk (10 trades), X' +$65 (2), HOLD +$109 (1), L6M +$280 (1), L3M 1 trade; RTY CPI-shock D30 h30: 30 trades, +$112 per trade, PRE +$205/wk (12), X' +$45 (2), MID -$83 (3), HOLD -$33 (7), L6M -$92 (2). Both fail the minimum sample (L6M 3 and 5 trades against 20; L3M 1-2 against 10), NOW-ONLY and persistence (50% / 25%); weekly correlation to the NQ stack +0.09 / -0.10. Passive variants not run: the taker nets already beat the cost (room 4.5x and 10x), and the 08:30 releases are outside ZL-1's RTH event store; the 14:00 FOMC passive variant would add nothing at 18 events.
Plain sentences: ES: the release moves the price about 7 ticks in the first 30 s for CPI and 10 for FOMC and gives most of it back or nothing more; nothing clears (0 of 960 cells) and the book would be 25-37 events a year with 1.6-2.5 ticks of cost, so no book. NQ: the same pattern is larger in ticks (CPI +30, FOMC +47 gross) but no cell clears (control); ISM reverses at 30 min but family p .6. RTY: continuation after CPI and FOMC volume shocks clears the family at p .044 / .098 with 18 and 30 events, positive in both halves and 4-10x the cost, but the recent windows hold 1-5 trades, so there is no formal verdict. Label: RTY FOMC-shock continuation and CPI-shock continuation = PER-CELL/FAMILY-MARGINAL, SMALL N (REGIME/WATCH; the recent window cannot confirm); ES, NQ NEGATIVE. No PASS claim.

## 1b-d addendum 3 - paying for the selection: the passive queue model on the WHOLE CHAR-A level-touch family (ZL-1; prereg l2vast/ds3/prereg/FIND_1BD_addendum3.md sha256 13a70adccb27533b0b5128868c1fa2f087250b43601b60b09753a92c226a40ff; code maker_family.py, maker_sens.py, maker.py rest_x / eval_order_x; no pre-2023 evidence)

Design: every cell of CHAR-A's events_b family (level type x session x class all/burst x hold 5/30/60/300/1800 s; cells with >= 30 discovery events), direction FROZEN on the discovery half (sign of the mean CHAR-A move: continuation or fade), statistic = net ticks per order placed on the TEST half 2025-07..2026-10 only, null = the same test orders shifted forward 120-1800 s on the same day (200 worlds), Westfall-Young max-z over all scored cells of the instrument. Orders are simulated only inside the event-store coverage (ET 04:00:30 to 16:00 minus the order life): asia and London before 04:00 are NOT covered, so those cells have too few covered orders and drop out (counts per cell in the cell tables).

| instrument | scored cells | cells with test net > 0 | cells p_cell <= .10 (expected under no edge about 10% of cells) | cells p_family <= .10 | best p_family | cells that BEAT the null |
|--|--|--|--|--|--|--|
| ES | 149 | 56 | 32 (15 expected) | 2 | 0.005 | 1 |
| RTY | 147 | 36 | 29 (15 expected) | 8 | 0.005 | 2 |
| NQ | 152 | 53 | 33 (15 expected) | 3 | 0.060 | 0 |

Joint family over the three instruments (per-world maximum of the three nulls): best z 6.47 (RTY), joint p_family 0.005; null maximum median 2.89, p95 3.67.

### ES - top eight cells by z (test half)
| level | session | class | hold s | direction | test orders | fill rate | net/order discovery | net/order test | z | p cell | p family | beats |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| IB | nypm | all | 300 | continue | 257 | 0.99 | +0.88 | +2.91 | 4.2 | 0.005 | 0.005 | YES |
| VW2 | nyam | burst | 1800 | fade | 286 | 0.98 | +0.40 | -2.97 | 3.4 | 0.005 | 0.030 | no |
| IB | nyam | burst | 5 | fade | 200 | 0.92 | -0.62 | +0.29 | 3.0 | 0.005 | 0.134 | no |
| IB | nypm | all | 60 | continue | 257 | 0.97 | -0.25 | +0.94 | 3.0 | 0.010 | 0.149 | no |
| IB | nypm | burst | 300 | continue | 121 | 0.98 | +1.63 | +3.62 | 2.8 | 0.005 | 0.234 | no |
| PD | nyam | burst | 60 | continue | 181 | 0.97 | +1.85 | +2.34 | 2.6 | 0.015 | 0.433 | no |
| IB | nyam | all | 5 | fade | 326 | 0.92 | -0.46 | +0.04 | 2.6 | 0.010 | 0.438 | no |
| PD | nyam | all | 5 | continue | 238 | 0.91 | -0.59 | +0.22 | 2.6 | 0.005 | 0.448 | no |

The addendum-2 cells in the family (PD, burst, ES): nyam h5: test net +0.39 (disc -0.48), p cell 0.005, p family 0.478; nyam h30: test net +0.85 (disc +0.92), p cell 0.060, p family 0.995; nyam h60: test net +2.34 (disc +1.85), p cell 0.015, p family 0.433; nyam h300: test net +3.01 (disc +2.48), p cell 0.040, p family 0.995; nyam h1800: test net +6.11 (disc +3.58), p cell 0.080, p family 1.000

### RTY - top eight cells by z (test half)
| level | session | class | hold s | direction | test orders | fill rate | net/order discovery | net/order test | z | p cell | p family | beats |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| PD | pre | all | 60 | continue | 98 | 0.65 | +1.22 | +6.46 | 6.5 | 0.005 | 0.005 | YES |
| PD | pre | burst | 5 | continue | 35 | 0.80 | +0.14 | +4.45 | 6.1 | 0.005 | 0.005 | no |
| PD | pre | burst | 30 | continue | 35 | 0.83 | +3.47 | +10.20 | 6.0 | 0.005 | 0.005 | no |
| PD | pre | all | 30 | continue | 98 | 0.64 | +1.02 | +3.83 | 5.7 | 0.005 | 0.005 | YES |
| PD | pre | all | 5 | continue | 98 | 0.56 | -0.32 | +1.24 | 5.6 | 0.005 | 0.005 | no |
| PD | pre | burst | 60 | continue | 35 | 0.83 | +4.17 | +10.88 | 4.5 | 0.005 | 0.005 | no |
| IB | close | all | 30 | fade | 106 | 0.71 | -0.58 | +2.13 | 4.0 | 0.005 | 0.010 | no |
| IB | close | burst | 30 | fade | 34 | 0.82 | -0.63 | +7.97 | 4.0 | 0.005 | 0.010 | no |

The addendum-2 cells in the family (PD, burst, RTY): nyam h5: test net -1.89 (disc -1.84), p cell 0.856, p family 1.000; nyam h30: test net -0.20 (disc -0.24), p cell 0.129, p family 1.000; nyam h60: test net -6.07 (disc -0.74), p cell 1.000, p family 1.000; nyam h300: test net -6.78 (disc -2.47), p cell 0.980, p family 1.000; nyam h1800: test net -7.32 (disc -5.45), p cell 0.731, p family 1.000; pre h5: test net +4.45 (disc +0.14), p cell 0.005, p family 0.005; pre h30: test net +10.20 (disc +3.47), p cell 0.005, p family 0.005; pre h60: test net +10.88 (disc +4.17), p cell 0.005, p family 0.005; pre h300: test net +6.83 (disc -1.97), p cell 0.114, p family 1.000; pre h1800: test net +28.74 (disc -1.09), p cell 0.005, p family 0.303

### NQ - top eight cells by z (test half)
| level | session | class | hold s | direction | test orders | fill rate | net/order discovery | net/order test | z | p cell | p family | beats |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VW2 | nypm | burst | 300 | continue | 105 | 0.95 | -1.30 | +33.22 | 3.4 | 0.005 | 0.060 | no |
| IB | nypm | burst | 30 | continue | 102 | 0.86 | -0.42 | +9.93 | 3.4 | 0.005 | 0.085 | no |
| IB | nypm | all | 30 | continue | 224 | 0.83 | -1.09 | +4.48 | 3.3 | 0.005 | 0.100 | no |
| ON | nyam | burst | 300 | fade | 308 | 0.95 | +1.12 | +20.57 | 3.2 | 0.005 | 0.124 | no |
| ON | nyam | all | 300 | fade | 342 | 0.94 | -1.37 | +17.91 | 3.0 | 0.005 | 0.184 | no |
| IB | nyam | all | 5 | fade | 302 | 0.91 | -1.07 | +0.63 | 2.9 | 0.010 | 0.234 | no |
| VW1 | nyam | burst | 5 | fade | 329 | 0.88 | -1.21 | +0.98 | 2.9 | 0.010 | 0.254 | no |
| IB | nyam | burst | 5 | fade | 247 | 0.91 | -0.65 | +0.73 | 2.7 | 0.010 | 0.358 | no |

The addendum-2 cells in the family (PD, burst, NQ): nyam h5: test net -1.61 (disc +1.16), p cell 0.284, p family 1.000; nyam h30: test net +5.56 (disc +4.22), p cell 0.015, p family 0.781; nyam h60: test net +6.72 (disc +7.53), p cell 0.030, p family 0.985; nyam h300: test net +2.70 (disc +11.37), p cell 0.279, p family 1.000; nyam h1800: test net -19.64 (disc +12.60), p cell 0.786, p family 1.000; pre h5: test net -11.75 (disc +7.01), p cell 1.000, p family 1.000; pre h30: test net -5.26 (disc -3.41), p cell 0.716, p family 1.000; pre h60: test net +6.51 (disc +9.00), p cell 0.154, p family 1.000; pre h300: test net +14.25 (disc +15.19), p cell 0.149, p family 1.000; pre h1800: test net +21.16 (disc +47.72), p cell 0.214, p family 1.000

### Pessimistic queue sensitivities for the six cells of addendum 2 (net ticks per order placed, both halves pooled, fee included; each scenario has its own 200-world forward-shift null; p cell in the second table)
| cell | S0 base | S1 no cancel benefit | S2 through-print fills only | S3 exit +1 tick adverse | S4 queue x1.3 | S5 queue x0.7 | S6 cancel latency 2 s | S8 combined (S1+S3+S4+S6) |
|--|--|--|--|--|--|--|--|--|
| ES nyam h1800 | +5.64 | +4.26 | +3.41 | +4.65 | +5.64 | +5.71 | +5.67 | +3.85 |
| ES nyam h300 | +3.02 | +2.59 | +1.38 | +2.04 | +3.03 | +3.23 | +3.06 | +1.33 |
| ES nyam h60 | +2.32 | +1.65 | +0.82 | +1.35 | +2.31 | +2.48 | +2.32 | +0.74 |
| NQ nyam h30 | +3.72 | +3.26 | +2.38 | +2.79 | +3.71 | +4.00 | +3.33 | +2.03 |
| NQ nyam h60 | +3.86 | +3.15 | +2.92 | +2.94 | +3.91 | +4.01 | +3.70 | +2.13 |
| NQ pre h1800 | +38.87 | +39.61 | +40.61 | +37.96 | +38.87 | +38.93 | +36.53 | +34.86 |

| cell | S0 base | S1 no cancel benefit | S2 through-print fills only | S3 exit +1 tick adverse | S4 queue x1.3 | S5 queue x0.7 | S6 cancel latency 2 s | S8 combined (S1+S3+S4+S6) |
|--|--|--|--|--|--|--|--|--|
| ES nyam h1800 | 0.015 | 0.020 | 0.030 | 0.015 | 0.015 | 0.015 | 0.015 | 0.015 |
| ES nyam h300 | 0.005 | 0.005 | 0.025 | 0.005 | 0.005 | 0.005 | 0.005 | 0.010 |
| ES nyam h60 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 |
| NQ nyam h30 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 |
| NQ nyam h60 | 0.015 | 0.010 | 0.010 | 0.015 | 0.015 | 0.010 | 0.010 | 0.010 |
| NQ pre h1800 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 | 0.010 | 0.005 | 0.005 |

Fill rates under S0 / S2 (through-print fills only) / S8: ES nyam h1800 0.99 / 0.71 / 0.90; ES nyam h300 0.98 / 0.70 / 0.88; ES nyam h60 0.97 / 0.69 / 0.87; NQ nyam h30 0.93 / 0.86 / 0.92; NQ nyam h60 0.93 / 0.86 / 0.92; NQ pre h1800 0.90 / 0.86 / 0.90. S7 (50% partial fill) scales net per order and fee by 0.5 and leaves the sign and p unchanged: S0 x 0.5 = ES nyam h1800 +2.82, ES nyam h300 +1.51, ES nyam h60 +1.16, NQ nyam h30 +1.86, NQ nyam h60 +1.93, NQ pre h1800 +19.43.

### Tape check: is the fill real? (fills of the real world, base model)
| cell | fills | through-print fill | tape confirms (level prints >= queue ahead) | tape CANNOT confirm (relies on modeled cancels ahead) | net/fill through | net/fill confirmed | net/fill unconfirmed | median queue ahead | median level print volume before fill |
|--|--|--|--|--|--|--|--|--|--|
| ES nyam h60 | 357 | 2.8% | 10.4% | 86.8% | +18.21 | -2.09 | +2.42 | 32 | 12 |
| ES nyam h300 | 363 | 2.8% | 10.5% | 86.8% | +10.61 | -0.33 | +3.24 | 32 | 12 |
| ES nyam h1800 | 364 | 2.7% | 10.4% | 86.8% | +10.91 | +18.45 | +4.02 | 32 | 12 |
| NQ nyam h30 | 477 | 36.7% | 30.4% | 32.9% | +12.46 | +2.16 | -3.69 | 2 | 1 |
| NQ nyam h60 | 477 | 36.7% | 30.4% | 32.9% | +15.31 | +0.36 | -4.73 | 2 | 1 |
| NQ pre h1800 | 84 | 40.5% | 32.1% | 27.4% | +96.97 | -1.30 | +15.34 | 2 | 1 |

### Pre-2023 and the L2 quote (metadata only, nothing bought)
There is NO pre-2023 evidence in this program: the event store begins 2023-08 (ES / RTY; NQ 1-s tables 2023-02) and X' is only partly covered. Databento mbp-10 (GLBX.MDP3, free metadata.get_cost; key from the login shell, never printed; no batch job, no download):

| span | ES USD | ES GB | NQ USD | NQ GB |
|--|--|--|--|--|
| 2022-08-01..2023-08-01 | 420 | 903 | 391 | 840 |
| 2020-01-01..2023-08-01 | 1348 | 2894 | 1242 | 2667 |
| 2017-06-01..2023-08-01 | 1816 | 3899 | 1674 | 3596 |

For scale: autopilot/SPEND.json shows the $8,000 cap with about $7,227 spent and a documented balance of $711.74 (DISCOVER_QUOTES_4), so ONE year of ES ($420) or of NQ ($391) fits and both together ($811) do not; the 2022-08..2023-07 year would give an X' window plus 2022 H2 for the same cells. The quote covers the full 23-hour day; the store used here needs ET 04:00-16:00 only, but Databento prices the requested time range, so day-window requests would save roughly the share of overnight records only. DECISION FOR THE USER; ZL-1 bought nothing.

### Pessimistic sensitivities for the family cells that BEAT the null (and the two PD burst comparators), TEST half only, net ticks per order placed, fee included (p cell in the second table)
| cell | S0 base | S1 no cancel benefit | S2 through-print fills only | S3 exit +1 tick adverse | S4 queue x1.3 | S5 queue x0.7 | S6 cancel latency 2 s | S8 combined (S1+S3+S4+S6) |
|--|--|--|--|--|--|--|--|--|
| ES IB nypm all 300 | +2.91 | +2.61 | +2.19 | +1.92 | +2.94 | +2.91 | +2.91 | +1.80 |
| ES PD nyam burst 60 | +2.34 | +1.42 | +0.40 | +1.37 | +2.32 | +2.48 | +2.34 | +0.25 |
| NQ PD nyam burst 30 | +5.56 | +5.81 | +4.40 | +4.66 | +5.56 | +8.01 | +4.90 | +4.19 |
| NQ PD nyam burst 60 | +6.72 | +5.43 | +6.21 | +5.82 | +6.72 | +8.44 | +6.21 | +4.17 |
| RTY PD pre all 30 | +3.83 | +2.77 | +2.41 | +3.18 | +3.86 | +4.42 | +3.22 | +1.62 |
| RTY PD pre all 60 | +6.46 | +6.73 | +6.29 | +5.81 | +6.48 | +6.39 | +6.18 | +5.65 |

| cell | S0 base | S1 no cancel benefit | S2 through-print fills only | S3 exit +1 tick adverse | S4 queue x1.3 | S5 queue x0.7 | S6 cancel latency 2 s | S8 combined (S1+S3+S4+S6) |
|--|--|--|--|--|--|--|--|--|
| ES IB nypm all 300 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 |
| ES PD nyam burst 60 | 0.010 | 0.015 | 0.060 | 0.010 | 0.010 | 0.005 | 0.010 | 0.020 |
| NQ PD nyam burst 30 | 0.020 | 0.010 | 0.025 | 0.020 | 0.020 | 0.005 | 0.020 | 0.010 |
| NQ PD nyam burst 60 | 0.050 | 0.060 | 0.020 | 0.050 | 0.050 | 0.025 | 0.055 | 0.065 |
| RTY PD pre all 30 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 |
| RTY PD pre all 60 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 | 0.005 |

### Books of the family cells that beat the null (stop 3 x discovery sd of CHAR-A's move, min 2 ticks; both halves; equal-risk lots with the session cap; placebos not run; no pre-2023 evidence; F = 720)
| book | orders | fills | net/fill ticks | t | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | corr V0/V2 | stack k* | gate |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| RTY PD pre all 30 | 258 | 185 | +2.60 | 0.93 | +170 | +171 | +171 | +51 | +75 | +45 | +45 | -38 | -0.03 / -0.03 | 5.0 | FAIL: X' mean -38 < -0.5 MDE (-28); min sample X' (trades 29/40, active weeks 18/20) |
| RTY PD pre all 60 | 258 | 188 | +4.50 | 1.33 | +135 | +137 | +137 | +28 | +63 | +108 | +22 | -29 | -0.04 / -0.04 | 5.0 | FAIL: X' mean -29 < -0.5 MDE (-18); min sample X' (trades 29/40, active weeks 18/20) |
| ES IB nypm all 300 | 683 | 662 | +1.58 | 1.88 | -294 | -827 | -827 | +220 | +428 | +661 | +92 | -32 | 0.02 / 0.01 | 5.0 | FAIL: NOW-ONLY fails (L3M/L6M mean not both > 0) |
| ES PD nyam burst 60 | 428 | 416 | +1.82 | 2.98 | +66 | -34 | -34 | +165 | +180 | +65 | +66 | +20 | -0.01 / -0.02 | 0.0 | FAIL: NOW-ONLY fails (L3M/L6M mean not both > 0) |

**Plain sentence: paying for the selection removes the ES / NQ NY-AM prior-day-level result. Across CHAR-A's whole level-touch family (149 / 147 / 152 scored cells for ES / RTY / NQ, direction frozen on the discovery half, test half only, 200 forward same-day shifts, Westfall-Young over every cell) the best family p is .005 (ES IB-edge continuation in NY-PM, 300 s), .005 (RTY prior-day-level continuation in the 08:30 pre-market, 5-60 s) and .060 (NQ); the cells that beat the null are 1 (ES), 2 (RTY) and 0 (NQ). The six addendum-2 cells do NOT survive it: ES PD-burst NY-AM h60 / 300 / 1800 have family p .43 / .995 / n.s. and NQ h30 / h60 .78 / .985, because 149 cells with ~2x the expected number of p<=.10 cells (32 / 29 / 33 against ~15) let selection alone produce them. They stay positive under every pessimistic queue scenario (S8 combined +0.7 to +3.9 ticks per order, p cell <= .03) and only 3% of ES fills are through-prints and 10% are confirmed by level prints >= the queue ahead, so 87% of the modeled ES fills rely on cancels ahead that the tape cannot show. Label stays REGIME / WATCH; no lead, no book; RTY pre-market PD continuation (the one cell family that survives both the family test and every scenario, test net +3.8 to +6.5 ticks per order, 98 test orders) fails the X' window and the tolerant gate in dollars (X' -38 / -29 per week) and has per-order t 0.9-1.3 over all fills.**

(Precision note for the addendum-3 sentence, ZL-1: the exact family p of the addendum-2 cells in the whole-family test: ES PD nyam burst h5: test +0.39 disc -0.48 p_cell 0.005 p_family 0.478 (181 test orders); ES PD nyam burst h30: test +0.85 disc +0.92 p_cell 0.060 p_family 0.995 (181 test orders); ES PD nyam burst h60: test +2.34 disc +1.85 p_cell 0.015 p_family 0.433 (181 test orders); ES PD nyam burst h300: test +3.01 disc +2.48 p_cell 0.040 p_family 0.995 (181 test orders); ES PD nyam burst h1800: test +6.11 disc +3.58 p_cell 0.080 p_family 1.000 (181 test orders); NQ PD nyam burst h5: test -1.61 disc +1.16 p_cell 0.284 p_family 1.000 (214 test orders); NQ PD nyam burst h30: test +5.56 disc +4.22 p_cell 0.015 p_family 0.781 (214 test orders); NQ PD nyam burst h60: test +6.72 disc +7.53 p_cell 0.030 p_family 0.985 (214 test orders); NQ PD nyam burst h300: test +2.70 disc +11.37 p_cell 0.279 p_family 1.000 (214 test orders); NQ PD nyam burst h1800: test -19.64 disc +12.60 p_cell 0.786 p_family 1.000 (214 test orders); NQ PD pre burst h5: test -11.75 disc +7.01 p_cell 1.000 p_family 1.000 (31 test orders); NQ PD pre burst h30: test -5.26 disc -3.41 p_cell 0.716 p_family 1.000 (31 test orders); NQ PD pre burst h60: test +6.51 disc +9.00 p_cell 0.154 p_family 1.000 (31 test orders); NQ PD pre burst h300: test +14.25 disc +15.19 p_cell 0.149 p_family 1.000 (31 test orders); NQ PD pre burst h1800: test +21.16 disc +47.72 p_cell 0.214 p_family 1.000 (31 test orders). The "n.s." for ES h1800 in the sentence is the value in this list.)

## R1 (CHAR-A, 2026-11-06T05:40Z): is the tick-scale level-touch continuation STRUCTURAL across deep markets or INDEX-only? 1-second OHLCV bars, GC CL ZN 6J NKD (test) and ES NQ RTY (bar-based control). Shadow only, no PASS, no pre-2023 evidence. VERDICT: INDEX-ONLY (and only NQ strongly).
Prereg l2vast/ds3/prereg/T_FIND_R1_prereg.md sha256 5ba429c6c2d06def5e1b4ba75ac6c4d3abee2bb56304fca413fe816b33daaf3c (DECISIONS.md, before any R1 number). Data (all owned, no NO-DATA product): instr_1s bars GC 24.7M, CL, ZN, ES, NQ, RTY (2023-07..2026-10-16, continuous .v.0, roll label days skipped) and the purchased 6J / NKD 1-s tapes (front id per label day). Events: first touch per level per session of PD / ON / IB / VWAP+-1,2 sigma and round numbers on bar highs/lows (prior close on the near side), outcome = approach-direction move of the open of the first bar >= touch+1+h over the open of the first bar >= touch+1, h 5 s..30 min, classes all/burst; 160 cells per product, 750-830 usable label days, 1,200-1,780 prior-day-level events per product (CHAR-A R1 events pkl). Nulls (B=100 each): A = within-month level transplant (events re-detected on the real path; round numbers random grid phase), B = shuffled-day outcomes (same touch second and direction, forward move read from another day of the month); the cell's p is the larger (more conservative) of the two pooled Westfall-Young family p. Pooling: Stouffer z over the products with >= 30 events, non-index family (5 products, 160 cells; null max z median 2.76 (A) / 2.87 (B), p95 3.46 / 3.68) and index family (3 products; p95 3.79 / 4.25).
| family | cells | p_family <= .05 | p_family <= .10 | p_A <= .05 | p_B <= .05 |
|--|--|--|--|--|--|
| INDEX | 160 | 0 | 2 | 2 | 2 |
| NONINDEX | 160 | 0 | 0 | 4 | 9 |

Prior-day-level touch, NY-AM (09:30-12:00), all touches, forward move in ticks in the approach direction (F), with the z against the level-transplant null (zA) and the shuffled-day-outcome null (zB); n = events:
| product | tick $ | 30 s F (zA / zB) | 60 s F (zA / zB) | 60 s after a volume burst F | pre-market 300 s F (zA / zB) | pre-market 1800 s F (zA / zB) | n NY-AM |
|--|--|--|--|--|--|--|--|
| GC | 10 | +1.04 (1.6 / 1.2) | +1.26 (1.5 / 1.0) | -0.41 | +2.68 (2.8 / 1.5) | +2.31 (4.1 / 1.0) | 445 |
| CL | 10 | +0.58 (1.0 / 2.6) | +0.87 (1.3 / 2.6) | +1.22 | +0.27 (1.5 / 0.3) | -1.51 (1.3 / -0.2) | 432 |
| ZN | 15.625 | +0.08 (1.4 / 1.7) | +0.20 (1.8 / 3.3) | +0.39 | -0.64 (0.2 / -2.5) | -0.84 (2.3 / -2.1) | 452 |
| 6J | 6.25 | -0.23 (-1.0 / -2.5) | -0.39 (-0.9 / -3.0) | -0.56 | +0.62 (3.2 / 1.2) | +1.79 (5.7 / 2.2) | 393 |
| NKD | 25 | +0.05 (-0.4 / 0.3) | -0.10 (-0.3 / -0.2) | -1.27 | +1.85 (2.6 / 2.6) | +0.89 (1.2 / 0.9) | 318 |
| ES | 12.5 | +1.34 (3.5 / 4.3) | +1.78 (3.1 / 4.1) | +2.23 | -1.58 (1.6 / -1.9) | -4.60 (1.8 / -2.7) | 550 |
| NQ | 5 | +5.98 (3.0 / 2.5) | +9.59 (3.2 / 3.0) | +11.30 | -3.54 (1.4 / -0.1) | -3.56 (1.8 / -0.3) | 562 |
| RTY | 5 | -0.34 (0.2 / -0.0) | -0.07 (0.4 / -0.1) | -0.70 | +0.84 (2.9 / 0.7) | -4.05 (2.7 / -1.0) | 586 |

Pooled non-index family, best cells (by p_family; none <= .10): ON|nypm|all|60s pooled zA +2.8 / zB +4.2, p_family 0.44; PD|nypm|all|60s pooled zA -2.8 / zB -6.0, p_family 0.49; ON|nypm|all|300s pooled zA +2.6 / zB +4.4, p_family 0.60; VW2|nypm|all|300s pooled zA -2.4 / zB -2.8, p_family 0.82; VW2|nyam|all|5s pooled zA +2.4 / zB +5.5, p_family 0.87. Several cells have pA_family <= .05 (pre-market PD touches +2 to +3 ticks on GC, 6J, NKD at 300-1800 s) but the shuffled-day-outcome null B removes them (pB_family 1.00): the same-clock drift after an up-touch is as large as the effect. Index control, bar-based: PD|NY-AM|all|30 s pooled zA 3.9 / zB 4.0 (pA .05, pB .10) and 60 s (.06 / .10): p_family .10, the only index cells <= .10, driven by NQ (+6.0 / +9.6 ticks), ES (+1.3 / +1.8), RTY about 0.

Plain sentences per product (R1): **GC:** no continuation at NY-AM (30/60 s +1.0 / +1.3 ticks = $10-13 gross, z 1.2-1.6, 3x below its $35 proxy cost); the pre-market PD touch is +2.7 / +2.3 ticks at 300 / 1800 s against the transplant null (z 2.8 / 4.1) but not against shuffled days (z 1.5 / 1.0). **CL:** +0.6 / +0.9 ticks ($6-9), not significant. **ZN:** about 0 (+0.08 / +0.20 tick of 1/64 = $1-3); level touches in rates do not continue (the 1-min map's PD bounce 55-64% is a reversion). **6J:** negative in NY-AM (-0.2 / -0.4 tick, reversal), positive pre-market only against one null. **NKD:** about 0 (and CAP-BREACH, 0 contracts per 5 minutes). **ES:** weak continuation +1.3 / +1.8 ticks (z 3-4 on both nulls; $17-22 vs a 1.39-tick taker cost); **NQ:** strong +6.0 / +9.6 ticks ($30-48 vs 3.97 ticks) -- the CHAR-A 1b-b/1b-DEEP finding reproduced with BAR data; **RTY:** none in NY-AM, and the bar-based pre-market PD touch does NOT reproduce the L2 +13 ticks / 30 min (bar 300 s +0.84, 1800 s -4.05). **Verdict: INDEX-ONLY (NQ >> ES > RTY ~ 0); NOT structural across deep markets**; the non-index pooled family has 0 cells at p_family <= .10 and 0 cells that survive both nulls. By the frozen rule no book was built (needs a pooled non-index cell at p_family <= .05). Consequence for the WATCH items: NQ NY-AM prior-day-level continuation (WATCH_NQ_PDL_SPEC.md) stays the single live-market hypothesis; the RTY pre-market item has no bar-based support; the cross-product replication fails, so the effect should be read as an equity-index (NQ in particular) microstructure/regime feature. Files: /mnt/l2/l2vast/ds3/out/find/xprod/ (per-product cells, nulls, events, pooled.csv), code xprod_pdl.py, xprod_pool.py; ledger T2F_R1_<SYM>.
