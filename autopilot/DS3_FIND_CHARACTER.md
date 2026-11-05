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

