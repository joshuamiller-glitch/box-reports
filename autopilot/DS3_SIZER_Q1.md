# DS3_SIZER_Q1 - first question: the live ER ladder L vs size-down-only A vs x1.5-only B (C = off, REFERENCE ONLY) (ZL-2, 2026-11-02T18:32Z; analysis only, the user decides)
FRAME: T-SIZER live-faithful base = D7 v1.3 exact on V13T_LIVE costs (take lines off, market exits 0.80, stops 2.45 pt worse, cancel-on-exit, per-book locks only) with the ER ladder passed as a multiplier, SEQUENTIAL rounding (session lots -> zone half -> x ER, rounded once, min 1) and day/week lock R scaled only when the multiplier exceeds 1 (BASE-4 run_v13t_ts). A06 slot halving is NOT modelled; the zone half is assumed to act before ER (like the slot halving); the clip at 1 includes the zone-half factor. The same cells on V13T_LIVE (single rounding, lock R scaled by the running-max multiplier) are shown beside in section 9. Prereg SIZER_Q1_PREREG.md sha256 77ec7b169ac862003d306ea2ceebb3ae3bf91660846a48acea05ac18b0dda21f + ADDENDUM1 sha256 1158880d9385fc723f1bf561a177c626c4551621ad9381878f59caa715b2a816 (both in DECISIONS.md before any Q1 result). Framing per the user: the ER sizer is a KEEP; "is there a better ER-based variant"; off is reference only.

**ANSWER (frame: T-SIZER base = V13T_LIVE costs, SEQUENTIAL rounding, lock R scaled only when mult > 1, A06 slot halving not modelled, zone half assumed before ER, per-book locks only; weekly composite of the six core books).** Should the x1.5 side stay live tonight? By the pre-registered rule the x1.5 side is NOT SUPPORTED as a risk-adjusted add, but it does not lose money: it adds +10.9k/wk in L6M (38.5k vs 27.6k for the size-down-only variant A) and +5.1k/wk in PRE, at the price of a deeper maxDD (L6M 170k vs 111k, PRE 161k vs 95k, MID 46k vs 58k the other way), and at EQUAL RISK the size-down-only variant A matches or edges L in L6M, HOLD and PRE (equal-risk means 39.4k / 33.5k / 19.5k vs L 37.6k / 31.8k / 17.8k, differences inside the +-10% fit noise) while L is better in MID and X'. Against random up-sizing, the ER-selected x1.5 earns more dollars in HOLD and PRE (placebo mean rank 0.94-0.99) but not clearly in L6M (0.88-0.92 < 0.95). Is there a better ER-based variant? A (x1.0 instead of x1.5 on high ER, x0.5 on low ER) beats L on maxDD in L6M (-35%) and PRE (-41%), also with the W29-W39 episode dropped (L6M -25%), at a mean cost of -10.9k/wk in L6M (inside the MDE 14.3k; with W29-W39 dropped -19.6k vs MDE 20.1k) and -5.1k/wk in PRE (MDE 6.5k); but random size-downs with the same distribution cut L6M maxDD as much (placebo cut rank 0.00-0.06) so A's drawdown benefit is mostly "less size", not better selection (its dollars beat random down-sizing, rank 0.90-0.99 in L6M/HOLD, 0.88-0.90 in PRE). FLAG raised for A (see section 10); the user decides tonight. The ER sizer stays a KEEP; sizer off is a reference only.**

## 1. The table (headline frame, phase 0, weekly composite of the six core books)
| window | cell | mean $k/wk | maxDD $k | worst-20 $k | ulcer $k | CVaR5 $k | Calmar | maxDD cut vs L | d mean vs L (MDE) $k/wk |
|--|--|--|--|--|--|--|--|--|--|
| L6M | L live ladder (x0.5 <.30, x1.5 >=.30) | 38.5 | 170.4 | 99.7 | 69.8 | -70.9 | 0.23 | +0.0% | +0.0 (0.0) |
| L6M | A size-down only (x0.5 <.30, x1 above) | 27.6 | 110.6 | 100.3 | 45.8 | -56.1 | 0.25 | +35.1% | -10.9 (14.3) |
| L6M | B x1.5 only (x1 <.30, x1.5 above) | 40.7 | 217.2 | 103.7 | 95.0 | -92.6 | 0.19 | -27.4% | +2.1 (11.4) |
| L6M | C off (x1) REFERENCE ONLY | 27.6 | 88.4 | 88.2 | 36.5 | -66.1 | 0.31 | +48.1% | -10.9 (20.2) |
| HOLD | L live ladder (x0.5 <.30, x1.5 >=.30) | 32.2 | 170.4 | -558.3 | 59.2 | -75.6 | 0.19 | +0.0% | +0.0 (0.0) |
| HOLD | A size-down only (x0.5 <.30, x1 above) | 23.7 | 117.3 | -375.8 | 42.7 | -57.1 | 0.20 | +31.2% | -8.4 (8.5) |
| HOLD | B x1.5 only (x1 <.30, x1.5 above) | 34.8 | 217.2 | -671.7 | 85.9 | -96.5 | 0.16 | -27.4% | +2.6 (7.7) |
| HOLD | C off (x1) REFERENCE ONLY | 21.9 | 198.9 | -523.4 | 67.7 | -72.5 | 0.11 | -16.7% | -10.3 (12.2) |
| MID | L live ladder (x0.5 <.30, x1.5 >=.30) | 23.5 | 45.5 | nan | 15.1 | -22.7 | 0.52 | +0.0% | +0.0 (0.0) |
| MID | A size-down only (x0.5 <.30, x1 above) | 17.8 | 58.2 | nan | 18.6 | -29.1 | 0.31 | -28.0% | -5.7 (10.0) |
| MID | B x1.5 only (x1 <.30, x1.5 above) | 23.2 | 108.1 | nan | 36.5 | -54.0 | 0.21 | -137.5% | -0.3 (14.5) |
| MID | C off (x1) REFERENCE ONLY | 4.4 | 143.4 | nan | 78.5 | -71.7 | 0.03 | -215.3% | -19.1 (15.1) |
| PRE | L live ladder (x0.5 <.30, x1.5 >=.30) | 18.0 | 160.7 | -823.0 | 49.1 | -76.0 | 0.11 | +0.0% | +0.0 (0.0) |
| PRE | A size-down only (x0.5 <.30, x1 above) | 13.0 | 94.8 | -497.6 | 26.8 | -49.2 | 0.14 | +41.0% | -5.1 (6.5) |
| PRE | B x1.5 only (x1 <.30, x1.5 above) | 20.5 | 127.5 | -813.1 | 42.5 | -74.4 | 0.16 | +20.7% | +2.5 (5.8) |
| PRE | C off (x1) REFERENCE ONLY | 14.4 | 120.6 | -668.1 | 34.2 | -55.3 | 0.12 | +24.9% | -3.7 (8.7) |
| X' | L live ladder (x0.5 <.30, x1.5 >=.30) | 5.1 | 72.8 | -444.8 | 31.3 | -51.1 | 0.07 | +0.0% | +0.0 (0.0) |
| X' | A size-down only (x0.5 <.30, x1 above) | 3.9 | 60.1 | -297.2 | 23.2 | -37.0 | 0.07 | +17.4% | -1.1 (4.6) |
| X' | B x1.5 only (x1 <.30, x1.5 above) | 6.7 | 104.6 | -462.4 | 40.4 | -56.6 | 0.06 | -43.6% | +1.7 (4.0) |
| X' | C off (x1) REFERENCE ONLY | 4.6 | 114.6 | -354.3 | 40.7 | -45.7 | 0.04 | -57.4% | -0.5 (6.4) |
| F9 | L live ladder (x0.5 <.30, x1.5 >=.30) | 34.8 | 170.4 | -313.4 | 59.7 | -70.9 | 0.20 | +0.0% | +0.0 (0.0) |
| F9 | A size-down only (x0.5 <.30, x1 above) | 25.2 | 110.6 | -184.5 | 40.3 | -56.1 | 0.23 | +35.1% | -9.6 (10.6) |
| F9 | B x1.5 only (x1 <.30, x1.5 above) | 36.2 | 217.2 | -373.0 | 83.2 | -92.6 | 0.17 | -27.4% | +1.4 (9.2) |
| F9 | C off (x1) REFERENCE ONLY | 21.0 | 143.4 | -345.7 | 54.8 | -77.4 | 0.15 | +15.8% | -13.8 (15.1) |

## 2. Ranking vs L: rank key = maxDD among cells with mean >= L mean (tolerance = paired MDE), L6M then PRE (C excluded)
| cell | L6M mean ok? | L6M maxDD cut | PRE mean ok? | PRE maxDD cut | HOLD cut | F9 cut | X' cut | eligible |
|--|--|--|--|--|--|--|--|--|
| A size-down only (x0.5 <.30, x1 above) | yes (-10.9k, MDE 14.3k) | +35.1% | yes (-5.1k, MDE 6.5k) | +41.0% | +31.2% | +35.1% | +17.4% | yes |
| B x1.5 only (x1 <.30, x1.5 above) | yes (+2.1k, MDE 11.4k) | -27.4% | yes (+2.5k, MDE 5.8k) | +20.7% | -27.4% | -27.4% | -43.6% | yes |

## 3. Phase-averaged (9 lock-reset phases) cut vs L, final V13T PA9 band (tl_band_final.csv, n=100): flip 2% = L6M 18.8 HOLD 18.2 MID 21.2 PRE 7.8 X' 14.5; flip 5% = 21.9 / 20.5 / 32.2 / 9.9 / 18.2
| cell | PA9 L6M | HOLD | MID | PRE | X' | SD L6M | drop-carry L6M / PRE / X' | pass flip2 | no-harm |
|--|--|--|--|--|--|--|--|--|--|
| A size-down only (x0.5 <.30, x1 above) | +35.1 | +31.2 | -28.0 | +41.0 | +17.4 | 0.0 | +24.5 / +41.0 / +42.0 | True | False |
| B x1.5 only (x1 <.30, x1.5 above) | -27.4 | -27.4 | -137.5 | +20.7 | -43.6 | 0.0 | -26.8 / +20.7 / -2.8 | False | False |
| C off (x1) REFERENCE ONLY | +48.1 | -16.7 | -215.3 | +24.9 | -57.4 | 0.0 | +25.3 / +24.9 / +18.2 | True | False |
(Phase averaging is moot on this base: with the lock R scaled only upward the 12R week floor never binds, the 9-phase results are identical to phase 0 (engine difference 0.0 $, SD 0); on the V13T_LIVE frame of section 9 the phases do differ.)

## 4. Equal-risk mean (lot scale search, linear fits over lscale 0.6..2.0; cell mean at the live ladder's fitted maxDD) and equal-mean-lots (lscale so mean effective lots = L's 3.20)
| window | L mean (fit) | A equal-risk mean | B equal-risk mean | C ref | A at equal lots: mean / maxDD | B at equal lots: mean / maxDD | L actual mean / maxDD |
|--|--|--|--|--|--|--|--|
| L6M | 37.6k | 39.4k | 35.7k | 51.7k | 34.7k / 194.6k (x1.429) | 33.1k / 154.1k (x0.833) | 38.5k / 170.4k |
| HOLD | 31.8k | 33.5k | 27.6k | 20.6k | 31.3k / 194.6k (x1.429) | 29.4k / 173.2k (x0.833) | 32.2k / 170.4k |
| MID | 23.2k | 11.9k | 10.4k | 3.5k | 25.6k / 80.7k (x1.429) | 21.6k / 82.8k (x0.833) | 23.5k / 45.5k |
| PRE | 17.8k | 19.5k | 25.5k | 19.2k | 16.8k / 150.6k (x1.429) | 18.1k / 111.9k (x0.833) | 18.0k / 160.7k |
| X' | 5.1k | 4.4k | 4.6k | 2.8k | 4.6k / 81.8k (x1.429) | 5.6k / 91.1k (x0.833) | 5.1k / 72.8k |
| F9 | 34.0k | 35.9k | 31.9k | 28.1k | 32.7k / 194.6k (x1.429) | 30.4k / 154.1k (x0.833) | 34.8k / 170.4k |
(equal-risk fits carry about +-10% noise because of integer lots; equal-mean-lots rows are single engine runs.)

## 5. Weeks 2026 W29-W39 dropped (base and cell; only 2026 windows change), mean $k/wk / maxDD $k and maxDD cut vs L
| window | L | A | B | C ref |
|--|--|--|--|--|
| L6M | 63.7 / 93.1 | 44.1 / 70.3 (+24.5%) | 66.9 / 117.4 (-26.1%) | 39.8 / 69.6 (+25.3%) |
| HOLD | 40.3 / 130.4 | 29.1 / 117.3 (+10.0%) | 43.4 / 212.5 (-63.0%) | 25.1 / 198.9 (-52.6%) |
| F9 | 48.2 / 93.1 | 34.0 / 70.3 (+24.5%) | 49.9 / 117.4 (-26.1%) | 25.5 / 143.4 (-54.1%) |
| MID (no change) | 23.5 / 45.5 | 17.8 / 58.2 (-28.0%) | 23.2 / 108.1 (-137.5%) | 4.4 / 143.4 (-215.3%) |
| PRE (no change) | 18.0 / 160.7 | 13.0 / 94.8 (+41.0%) | 20.5 / 127.5 (+20.7%) | 14.4 / 120.6 (+24.9%) |
| X' (no change) | 5.1 / 72.8 | 3.9 / 60.1 (+17.4%) | 6.7 / 104.6 (-43.6%) | 4.6 / 114.6 (-57.4%) |

## 6. Per book x session x vol-tercile (F9 and ALL; cell minus L, $ per day; MDE paired; n taken signals) - by book (F9), full table in sizer_cache/q1ts/split_*.csv
**A size-down only (x0.5 <.30, x1 above) vs L, F9, by book:**
| book | n | d $/day (sum of cells) |
|--|--|--|
| HM | 760 | -1050 |
| KB | 1605 | +504 |
| MV | 889 | -103 |
| PB | 418 | -372 |
| PE | 1278 | -3130 |
| SM | 422 | -871 |
Largest cells: PE asia tercile 2: -1994/day (n 358, MDE 1987); PE london tercile 2: -1168/day (n 208, MDE 2039); PE asia tercile 1: -916/day (n 221, MDE 1607); PE london tercile 0: +888/day (n 133, MDE 868)

**B x1.5 only (x1 <.30, x1.5 above) vs L, F9, by book:**
| book | n | d $/day (sum of cells) |
|--|--|--|
| HM | 760 | +203 |
| KB | 1605 | +21 |
| MV | 889 | -593 |
| PB | 418 | +0 |
| PE | 1278 | +1092 |
| SM | 422 | -255 |
Largest cells: PE asia tercile 2: +839/day (n 358, MDE 1517); PE london tercile 2: +701/day (n 208, MDE 1935); HM asia tercile 2: +658/day (n 282, MDE 830); HM asia tercile 0: -578/day (n 169, MDE 757)

## 7. Placebos (>=100 draws, 3-phase average -4/0/+4 against the phase-matched live base; same cost model; rank = share of draws BELOW the real cell, high = real beats the placebo)
| cell | kind | draws | rank cut L6M / HOLD / MID / PRE / X' | rank mean $ L6M / HOLD / MID / PRE / X' |
|--|--|--|--|--|
| A size-down only (x0.5 <.30, | ar1 | 100 | 0.04 / 0.90 / 0.93 / 0.37 / 0.96 | 0.95 / 0.99 / 0.99 / 0.89 / 0.69 |
| A size-down only (x0.5 <.30, | dayshuf | 100 | 0.00 / 0.91 / 0.94 / 0.45 / 0.95 | 0.92 / 0.99 / 0.94 / 0.90 / 0.62 |
| A size-down only (x0.5 <.30, | perm | 100 | 0.06 / 0.90 / 0.96 / 0.42 / 0.99 | 0.90 / 0.98 / 0.97 / 0.88 / 0.69 |
| B x1.5 only (x1 <.30, x1.5 a | ar1 | 100 | 0.00 / 0.71 / 0.95 / 0.87 / 0.98 | 0.88 / 0.99 / 0.99 / 0.94 / 0.75 |
| B x1.5 only (x1 <.30, x1.5 a | dayshuf | 100 | 0.00 / 0.66 / 0.95 / 0.86 / 0.96 | 0.90 / 0.98 / 0.94 / 0.97 / 0.81 |
| B x1.5 only (x1 <.30, x1.5 a | perm | 100 | 0.00 / 0.75 / 0.94 / 0.85 / 0.98 | 0.92 / 0.96 / 0.96 / 0.96 / 0.81 |
Reading: the x1.5 side (B) earns more dollars than random up-sizing in HOLD and PRE (mean rank 0.94-0.99) and 0.88-0.92 in L6M; A's drawdown cut is no better than random size-downs of the same share (cut rank L6M 0.00-0.06, PRE 0.37-0.45) while its dollars beat random down-sizing (0.88-0.99). Phase 0 only (phase-invariant base).

## 8. Lots distribution and worst single-day exposure (engine run of each cell; positions open at signal seconds; stack risk = lots x stop pts x $20)
| cell | mean lots | max lots | worst net signed lots (day) | worst stack risk $ (day, time) | top-3 risk days |
|--|--|--|--|--|--|
| L live ladder (x0.5 <.30, x1.5 > | 3.01 | 11 | 28 (20240220) | 33,600 (20230623, 2023-06-23 07:20) | 20250618 33,600; 20250806 33,600; 20250623 33,600 |
| A size-down only (x0.5 <.30, x1  | 2.23 | 7 | 18 (20240220) | 21,600 (20230623, 2023-06-23 07:20) | 20260731 21,600; 20230623 21,600; 20250618 21,600 |
| B x1.5 only (x1 <.30, x1.5 above | 3.70 | 11 | 29 (20240715) | 34,800 (20240715, 2024-07-15 11:07) | 20240715 34,800; 20240726 33,600; 20241028 33,600 |
| C off (x1) REFERENCE ONLY | 2.89 | 7 | 20 (20240715) | 24,000 (20230829, 2023-08-29 08:00) | 20240829 24,000; 20241007 24,000; 20260710 24,000 |
Lots distribution per book x session (mean lots / max lots / share of signals at each multiplier incl. zone composites): files sizer_cache/q1ts/lots_dist_{L,A,B}.csv. Live ladder, mean lots by book x session:
| book | asia | london | nyam | nypm |
|--|--|--|--|--|
| HM | 3.1 / 6 | - | 1.4 / 2 | - |
| KB | 1.7 / 3 | 1.7 / 3 | 1.3 / 2 | 1.7 / 3 |
| MV | - | 1.9 / 3 | 1.3 / 2 | - |
| PB | 1.7 / 2 | - | - | - |
| PE | 6.6 / 11 | 6.9 / 11 | 6.5 / 11 | - |
| SM | 4.0 / 6 | 3.6 / 6 | - | - |

## 10. FLAG: cell A (exact definition for a Shadow / code decision, nothing is live)
A = ER sizer with the up-size removed. Bar: 5-minute closes (tick-built 1-minute library bars bucketed by epoch, stamped at the close second; no partial bars); window: ER(20) = |close[0] - close[20]| / sum_{i=0..19} |close[i] - close[i+1]| on the LAST CLOSED 5-minute bar at the signal second; thresholds: ER >= 0.30 -> multiplier 1.0, ER < 0.30 -> multiplier 0.5, ER undefined -> 1.0; applied to all six core books (KB PE SM HM MV PB) in every session (per book / session split in section 6); lots = max(1, floor(rounded_zone_lots * mult + 0.5)) with SEQUENTIAL rounding (session lots -> zone HALF 0.5 on the 7-line D20 set, rounded -> x ER, rounded once, min 1); lock-scaling rule: day give-back / 12R week floor / per-book daily max P&L use R x max(1, running-max unrounded multiplier), i.e. for A they are never scaled (A never exceeds 1); A06 slot halving not modelled. Evidence: L6M maxDD 110.6k vs 170.4k (-35%, with W29-W39 dropped -24.5%), PRE 94.8k vs 160.7k (-41%), HOLD -31%, X' -17%, MID +28% WORSE (58k vs 46k); mean -10.9k/wk L6M (MDE 14.3k), -5.1k/wk PRE (MDE 6.5k), HOLD -8.4k (MDE 8.5k), F9 -9.6k (MDE 10.6k); with W29-W39 dropped L6M -19.6k (MDE 20.1k), HOLD -11.2k (MDE 9.9k, beyond). Weaknesses: placebo cut ranks vs random size-downs 0.00-0.06 (L6M) and 0.37-0.45 (PRE); fails the no-harm test on MID; costs 28% of the L6M mean. B (x1.5 only) does NOT qualify (L6M maxDD +27% deeper).

## 9. Same cells on V13T_LIVE (single rounding, lock R scaled by the running-max multiplier), phase 0, beside the headline
| window | cell | mean $k/wk | maxDD $k | worst-20 $k | ulcer $k | CVaR5 $k | Calmar | maxDD cut vs L | d mean vs L (MDE) $k/wk |
|--|--|--|--|--|--|--|--|--|--|
| L6M | L live ladder (x0.5 <.30, x1.5 >=.30) | 36.7 | 150.7 | 98.6 | 61.3 | -68.3 | 0.24 | +0.0% | +0.0 (0.0) |
| L6M | A size-down only (x0.5 <.30, x1 above) | 25.1 | 92.1 | 81.6 | 40.0 | -57.1 | 0.27 | +38.9% | -11.7 (14.4) |
| L6M | B x1.5 only (x1 <.30, x1.5 above) | 39.8 | 178.2 | 116.3 | 81.4 | -102.6 | 0.22 | -18.2% | +3.1 (13.2) |
| L6M | C off (x1) REFERENCE ONLY | 26.2 | 80.5 | 74.1 | 34.9 | -74.3 | 0.33 | +46.6% | -10.5 (19.9) |
| HOLD | L live ladder (x0.5 <.30, x1.5 >=.30) | 30.4 | 150.7 | -575.0 | 54.2 | -74.1 | 0.20 | +0.0% | +0.0 (0.0) |
| HOLD | A size-down only (x0.5 <.30, x1 above) | 21.8 | 118.5 | -387.1 | 39.8 | -58.0 | 0.18 | +21.4% | -8.6 (8.7) |
| HOLD | B x1.5 only (x1 <.30, x1.5 above) | 34.6 | 208.1 | -642.0 | 77.5 | -105.0 | 0.17 | -38.0% | +4.2 (8.8) |
| HOLD | C off (x1) REFERENCE ONLY | 21.1 | 192.4 | -514.0 | 66.6 | -75.3 | 0.11 | -27.6% | -9.3 (12.2) |
| MID | L live ladder (x0.5 <.30, x1.5 >=.30) | 24.0 | 43.7 | nan | 16.8 | -28.6 | 0.55 | +0.0% | +0.0 (0.0) |
| MID | A size-down only (x0.5 <.30, x1 above) | 16.5 | 58.6 | nan | 19.8 | -29.3 | 0.28 | -34.1% | -7.6 (9.6) |
| MID | B x1.5 only (x1 <.30, x1.5 above) | 25.1 | 98.2 | nan | 33.6 | -49.1 | 0.26 | -124.6% | +1.1 (14.5) |
| MID | C off (x1) REFERENCE ONLY | 4.0 | 135.4 | nan | 74.7 | -67.7 | 0.03 | -209.4% | -20.0 (15.0) |
| PRE | L live ladder (x0.5 <.30, x1.5 >=.30) | 17.3 | 166.2 | -789.9 | 51.0 | -79.1 | 0.10 | +0.0% | +0.0 (0.0) |
| PRE | A size-down only (x0.5 <.30, x1 above) | 12.3 | 91.4 | -503.3 | 28.1 | -51.7 | 0.13 | +45.0% | -5.0 (6.1) |
| PRE | B x1.5 only (x1 <.30, x1.5 above) | 20.2 | 131.3 | -811.0 | 43.3 | -75.7 | 0.15 | +21.0% | +2.9 (5.8) |
| PRE | C off (x1) REFERENCE ONLY | 13.8 | 119.9 | -681.8 | 36.3 | -54.5 | 0.11 | +27.8% | -3.5 (8.7) |
| X' | L live ladder (x0.5 <.30, x1.5 >=.30) | 4.8 | 92.5 | -447.4 | 36.9 | -47.2 | 0.05 | +0.0% | +0.0 (0.0) |
| X' | A size-down only (x0.5 <.30, x1 above) | 3.6 | 65.5 | -297.7 | 25.3 | -36.3 | 0.06 | +29.2% | -1.2 (4.6) |
| X' | B x1.5 only (x1 <.30, x1.5 above) | 7.1 | 111.8 | -459.1 | 41.6 | -56.6 | 0.06 | -20.9% | +2.3 (4.4) |
| X' | C off (x1) REFERENCE ONLY | 4.9 | 119.9 | -358.4 | 43.1 | -45.9 | 0.04 | -29.7% | +0.1 (6.3) |
| F9 | L live ladder (x0.5 <.30, x1.5 >=.30) | 33.7 | 150.7 | -306.9 | 52.8 | -68.3 | 0.22 | +0.0% | +0.0 (0.0) |
| F9 | A size-down only (x0.5 <.30, x1 above) | 23.0 | 92.1 | -208.7 | 35.8 | -57.1 | 0.25 | +38.9% | -10.7 (10.6) |
| F9 | B x1.5 only (x1 <.30, x1.5 above) | 36.2 | 178.2 | -327.8 | 71.6 | -102.6 | 0.20 | -18.2% | +2.5 (10.3) |
| F9 | C off (x1) REFERENCE ONLY | 19.9 | 135.4 | -329.3 | 52.3 | -78.9 | 0.15 | +10.2% | -13.8 (14.9) |

PA9 on that frame (cut vs the V13T_LIVE live ladder): A: +38.0 / +31.3 / -94.8 / +43.5 / +25.4; B: -5.6 / -21.1 / -225.5 / +19.7 / -25.3; C: +51.9 / -12.7 / -360.4 / +28.5 / -35.8
