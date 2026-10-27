# REPORT DS2-FIRM v5 - THE RISK LAYER (trackFIRM, 2026-10-22); research only

Prereg: l2vast/PREREG_DS2_FIRM_V5.md (frozen before scoring; sha in DECISIONS; F_P 3,363 -> 3,368). Engine: riskeng (stateful 1-s simulator, validated within 0.1% of the hard-lock engine: WF 24,978 vs 24,975, maxDD 401.6k vs 401.3k). Fixed-60 cells use the exact corrected-P9 points (no L2 layer needed); non-60 options use direct-replay points (replayed EM/S14x1 entries + XS4/XJ/XS0 exits, per-fold arm choice) and are compared with the live pair run through the same replay policy (RB: IS 13.7k, WF 28.4k / 106.2k / 371k, L8W 45.7k / 219k). Benchmark = corrected P9 (WF 25.0k / SD 104.5k / maxDD 401k / worst -137k; L8W 34.2k / 109.4k / 267k; IS 13.7k / 95.9k / 407k).

**Deviations from the frozen prereg (stated, not hidden):** (1) D1 lock sets are a structured 360-point factorial (per-book rule live/off x combined cap hard/soft-8/off x week floor {8,10,12,off,5R} x give-back {live, keep 67%, arm 3R, soft-8} x arm-after-N-trades {0,2,3}) built from the A-B elements, not the "top 180 singles + 180 pairwise combinations"; same count, same elements. (2) A2 per-book scope and the A1 per-book scope limit are implemented as a single limit applied to all entries when either book breaches. (3) The B3 session pattern, day-of-week and VIX patterns are run; B2 uses the live-lock run's prior weekly SD. (4) HMM is replaced by a 3-component Gaussian mixture in V6 (not here). (5) D1 options with the W3 centres need the union replay (see V4 W3/W5); where these sections say PENDING they were not available when this file was written.

## (1) Pareto front and the objective (D1)


Objective (WF mean >= benchmark AND maxDD <= 0.7 x benchmark): 0 of 23040 cells pass. Relaxed (mean >= benchmark AND maxDD < benchmark): 856 cells; the lowest WF maxDD reached by any cell with mean >= benchmark is 287.3k = 0.72 x benchmark.

**Pareto front (WF mean up, SD down, maxDD down); 854 non-dominated cells; listing the 25 with mean >= benchmark mean ranked by maxDD**

| option | lock set | session lots | window | WF mean / SD / maxDD / worst | L8W mean / maxDD | IS mean / maxDD | maxDD / bench |
|---|---|---|---|---|---|---|---|
| live60_P9 | pblive|capoff|wk12|gb1|N2 | 14/10/10 | live | 25.5k / 93.1k / 287.3k / -184.8k | 56.1k / 182.6k | 13.2k / 304.9k | 0.72 |
| live60_P9 | pblive|capsoft8|wk12|gb1|N2 | 14/10/10 | live | 25.3k / 92.7k / 287.3k / -184.8k | 55.0k / 182.6k | 13.2k / 304.9k | 0.72 |
| live60_P9 | pblive|capsoft8|wkoff|gb1|N2 | 14/10/10 | live | 25.3k / 92.7k / 287.3k / -184.8k | 55.0k / 182.6k | 13.2k / 304.9k | 0.72 |
| live60_P9 | pblive|capoff|wkoff|gb1|N2 | 14/10/10 | live | 25.5k / 93.1k / 287.3k / -184.8k | 56.1k / 182.6k | 13.2k / 304.9k | 0.72 |
| live60_P9 | pblive|capoff|wkoff|gb1|N0 | 14/10/10 | live | 25.1k / 92.5k / 298.9k / -184.8k | 61.3k / 182.6k | 13.4k / 309.3k | 0.74 |
| live60_P9 | pblive|capoff|wk12|gb1|N0 | 14/10/10 | live | 25.1k / 92.5k / 298.9k / -184.8k | 61.3k / 182.6k | 13.4k / 309.3k | 0.74 |
| centreHonest | pblive|capoff|wk5|gb0|N2 | 14/8/10 | live | 31.7k / 102.9k / 299.8k / -87.4k | 37.5k / 248.4k | 5.9k / 420.7k | 0.81 |
| centreHonest | pblive|capsoft8|wk5|gb0|N2 | 14/8/10 | live | 31.2k / 101.7k / 299.8k / -87.4k | 36.9k / 248.4k | 5.8k / 420.7k | 0.81 |
| centreHonest | pblive|capoff|wk5|gb0|N0 | 14/8/10 | live | 31.9k / 101.2k / 300.3k / -87.4k | 44.5k / 248.4k | 6.0k / 420.7k | 0.81 |
| centreHonest | pblive|capsoft8|wk5|gb0|N0 | 14/8/10 | live | 31.5k / 100.0k / 300.3k / -87.4k | 44.0k / 248.4k | 6.0k / 420.7k | 0.81 |
| live60 | pboff|capoff|wk10|gb0|N3 | 14/10/8 | live | 39.6k / 115.9k / 301.1k / -172.3k | 64.1k / 263.6k | 8.6k / 440.6k | 0.81 |
| live60 | pboff|caphard|wk10|gb0|N2 | 14/10/8 | live | 36.1k / 110.8k / 301.1k / -172.3k | 52.7k / 258.9k | 9.1k / 449.4k | 0.81 |
| live60 | pboff|caphard|wk10|gb0|N3 | 14/10/8 | live | 39.3k / 111.3k / 301.1k / -172.3k | 61.9k / 263.6k | 8.6k / 440.6k | 0.81 |
| live60 | pboff|capsoft8|wk10|gb0|N3 | 14/10/8 | live | 39.5k / 115.7k / 301.1k / -172.3k | 63.6k / 263.6k | 8.6k / 440.6k | 0.81 |
| centreHonest | pblive|caphard|wk5|gb0|N0 | 14/8/10 | live | 29.7k / 96.3k / 301.7k / -87.4k | 41.8k / 248.4k | 5.7k / 420.7k | 0.81 |
| live60_P9 | pboff|caphard|wk10|gb0|N2 | 14/10/8 | live | 35.2k / 110.7k / 302.7k / -172.3k | 44.6k / 288.5k | 9.1k / 450.2k | 0.75 |
| live60_P9 | pboff|caphard|wk10|gb0|N3 | 14/10/8 | live | 38.3k / 111.2k / 302.7k / -172.3k | 53.7k / 293.4k | 8.6k / 441.4k | 0.75 |
| centreHonest | pblive|caphard|wk5|gb0|N0 | 14/10/8 | live | 28.8k / 92.8k / 305.7k / -91.2k | 30.5k / 282.9k | 9.4k / 362.8k | 0.82 |
| centreHonest | pblive|capoff|wk5|gb0|N0 | 14/10/8 | live | 30.7k / 97.4k / 305.7k / -91.2k | 32.1k / 282.9k | 9.7k / 362.8k | 0.82 |
| centreHonest | pblive|capsoft8|wk5|gb0|N0 | 14/10/8 | live | 30.7k / 97.3k / 305.7k / -91.2k | 32.1k / 282.9k | 9.7k / 362.8k | 0.82 |
| centreHonest | pblive|caphard|wk5|gb0|N2 | 14/10/8 | live | 29.0k / 94.5k / 305.7k / -91.2k | 28.8k / 282.9k | 8.5k / 362.8k | 0.82 |
| centreHonest | pblive|capoff|wk5|gb0|N2 | 14/10/8 | live | 31.1k / 99.4k / 305.7k / -91.2k | 30.4k / 282.9k | 8.8k / 362.8k | 0.82 |
| centreHonest | pblive|capsoft8|wk5|gb0|N2 | 14/10/8 | live | 31.0k / 99.2k / 305.7k / -91.2k | 30.4k / 282.9k | 8.8k / 362.8k | 0.82 |
| live60 | pboff|caphard|wk10|gb0|N3 | 14/10/10 | live | 39.8k / 117.3k / 308.3k / -170.0k | 58.3k / 278.7k | 9.5k / 462.3k | 0.83 |
| live60 | pboff|capsoft8|wk10|gb0|N3 | 14/10/10 | live | 40.4k / 121.3k / 308.3k / -170.0k | 61.3k / 278.7k | 9.5k / 462.3k | 0.83 |

**Top 20 by the relaxed objective ranked by WF SD, with fold stability (number of the 11 folds in which the cell is in the top quartile of ALL screened cells on weekly mean / on maxDD)**

| option | lock set | lots | win | WF mean / SD / maxDD | L8W mean / maxDD | IS mean | top-quartile folds mean / DD |
|---|---|---|---|---|---|---|---|
| ATR_R10000_f4 | pblive|capsoft8|wk8|gb0|N0 | 14/8/10 | live | 28.5k / 71.3k / 327.9k | 62.4k / 116.4k | -12.2k | 2 / 6 |
| ATR_R10000_f4 | pblive|capsoft8|wk8|gb0|N2 | 14/8/10 | live | 28.5k / 71.3k / 327.9k | 62.4k / 116.4k | -12.2k | 2 / 6 |
| ATR_R10000_f4 | pblive|capoff|wk8|gb0|N0 | 14/8/10 | live | 28.5k / 71.3k / 327.9k | 62.4k / 116.4k | -12.2k | 2 / 6 |
| ATR_R10000_f4 | pblive|capoff|wk8|gb0|N2 | 14/8/10 | live | 28.5k / 71.3k / 327.9k | 62.4k / 116.4k | -12.2k | 2 / 6 |
| ATR_R10000_f4 | pblive|capsoft8|wk8|gb0|N3 | 14/8/10 | live | 28.5k / 71.3k / 327.9k | 62.4k / 116.4k | -12.2k | 2 / 6 |
| ATR_R10000_f4 | pblive|capoff|wk8|gb0|N3 | 14/8/10 | live | 28.5k / 71.3k / 327.9k | 62.4k / 116.4k | -12.2k | 2 / 6 |
| ATR_R10000_f8 | pblive|caphard|wk8|gb0|N3 | 14/8/10 | live | 29.1k / 81.6k / 324.7k | 71.5k / 115.7k | -12.2k | 4 / 3 |
| ATR_R10000_f8 | pblive|caphard|wk8|gb0|N0 | 14/8/10 | live | 29.1k / 81.7k / 324.7k | 71.5k / 115.7k | -12.2k | 3 / 3 |
| ATR_R10000_f8 | pblive|caphard|wk8|gb0|N2 | 14/8/10 | live | 29.1k / 81.7k / 324.7k | 71.5k / 115.7k | -12.2k | 3 / 3 |
| ATR_R10000_f8 | pblive|capsoft8|wk8|gb0|N3 | 14/8/10 | live | 29.2k / 81.7k / 324.7k | 72.5k / 115.7k | -12.2k | 4 / 3 |
| ATR_R10000_f8 | pblive|capoff|wk8|gb0|N3 | 14/8/10 | live | 29.2k / 81.7k / 324.7k | 72.5k / 115.7k | -12.2k | 4 / 3 |
| ATR_R10000_f8 | pblive|capsoft8|wk8|gb0|N0 | 14/8/10 | live | 29.2k / 81.8k / 324.7k | 72.5k / 115.7k | -12.2k | 3 / 3 |
| ATR_R10000_f8 | pblive|capoff|wk8|gb0|N0 | 14/8/10 | live | 29.2k / 81.8k / 324.7k | 72.5k / 115.7k | -12.2k | 3 / 3 |
| ATR_R10000_f8 | pblive|capoff|wk8|gb0|N2 | 14/8/10 | live | 29.2k / 81.8k / 324.7k | 72.5k / 115.7k | -12.2k | 3 / 3 |
| ATR_R10000_f8 | pblive|capsoft8|wk8|gb0|N2 | 14/8/10 | live | 29.2k / 81.8k / 324.7k | 72.5k / 115.7k | -12.2k | 3 / 3 |
| ATR_R10000_f8 | pblive|caphard|wkoff|gb0|N2 | 14/8/10 | live | 29.0k / 82.1k / 330.8k | 71.5k / 115.7k | -13.0k | 3 / 3 |
| ATR_R10000_f8 | pblive|caphard|wk12|gb0|N2 | 14/8/10 | live | 29.0k / 82.1k / 330.8k | 71.5k / 115.7k | -13.3k | 3 / 3 |
| ATR_R10000_f8 | pblive|caphard|wkoff|gb0|N0 | 14/8/10 | live | 29.0k / 82.1k / 330.8k | 71.5k / 115.7k | -13.0k | 3 / 3 |
| ATR_R10000_f8 | pblive|caphard|wk12|gb0|N0 | 14/8/10 | live | 29.0k / 82.1k / 330.8k | 71.5k / 115.7k | -13.3k | 3 / 3 |
| ATR_R10000_f8 | pblive|caphard|wk12|gb0|N3 | 14/8/10 | live | 29.0k / 82.2k / 330.8k | 71.5k / 115.7k | -13.3k | 3 / 3 |

**500-world nulls (placebo locks with the same in-situ fire hazard; random-subset down-sizing of the same share) on the top 20 + the three exact best cells; D2 rule: keep only cells in the top quartile of all screened cells in >= 8 of 11 folds on mean or on maxDD**

| option | lock set | lots | WF mean / SD / maxDD | placebo rank mean / maxDD | down-size rank mean / maxDD | D2 top-quartile folds mean / DD | D2 verdict |
|---|---|---|---|---|---|---|---|
| ATR_R10000_f4 | pblive|capsoft8|wk8|gb0|N0 | 14/8/10 | 28.5k / 71.3k / 327.9k | 1.00 / 0.71 | 0.95 / 1.00 | 2 / 6 | DISCARD (not top-quartile in >= 8 folds) |
| ATR_R10000_f4 | pblive|capsoft8|wk8|gb0|N2 | 14/8/10 | 28.5k / 71.3k / 327.9k | 1.00 / 0.71 | 0.95 / 1.00 | 2 / 6 | DISCARD (not top-quartile in >= 8 folds) |
| ATR_R10000_f4 | pblive|capoff|wk8|gb0|N0 | 14/8/10 | 28.5k / 71.3k / 327.9k | 0.99 / 0.73 | 0.95 / 1.00 | 2 / 6 | DISCARD (not top-quartile in >= 8 folds) |
| ATR_R10000_f4 | pblive|capoff|wk8|gb0|N2 | 14/8/10 | 28.5k / 71.3k / 327.9k | 0.99 / 0.73 | 0.95 / 1.00 | 2 / 6 | DISCARD (not top-quartile in >= 8 folds) |
| ATR_R10000_f4 | pblive|capsoft8|wk8|gb0|N3 | 14/8/10 | 28.5k / 71.3k / 327.9k | 1.00 / 0.72 | 0.95 / 1.00 | 2 / 6 | DISCARD (not top-quartile in >= 8 folds) |
| ATR_R10000_f4 | pblive|capoff|wk8|gb0|N3 | 14/8/10 | 28.5k / 71.3k / 327.9k | 0.99 / 0.73 | 0.95 / 1.00 | 2 / 6 | DISCARD (not top-quartile in >= 8 folds) |
| ATR_R10000_f8 | pblive|caphard|wk8|gb0|N3 | 14/8/10 | 29.1k / 81.6k / 324.7k | 0.99 / 0.94 | 0.98 / 1.00 | 4 / 3 | DISCARD (not top-quartile in >= 8 folds) |
| ATR_R10000_f8 | pblive|caphard|wk8|gb0|N0 | 14/8/10 | 29.1k / 81.7k / 324.7k | 0.99 / 0.94 | 0.98 / 1.00 | 3 / 3 | DISCARD (not top-quartile in >= 8 folds) |
| ATR_R10000_f8 | pblive|caphard|wk8|gb0|N2 | 14/8/10 | 29.1k / 81.7k / 324.7k | 0.99 / 0.94 | 0.98 / 1.00 | 3 / 3 | DISCARD (not top-quartile in >= 8 folds) |
| ATR_R10000_f8 | pblive|capsoft8|wk8|gb0|N3 | 14/8/10 | 29.2k / 81.7k / 324.7k | 1.00 / 0.95 | 0.99 / 1.00 | 4 / 3 | DISCARD (not top-quartile in >= 8 folds) |
| ATR_R10000_f8 | pblive|capoff|wk8|gb0|N3 | 14/8/10 | 29.2k / 81.7k / 324.7k | 0.99 / 0.93 | 0.99 / 1.00 | 4 / 3 | DISCARD (not top-quartile in >= 8 folds) |
| ATR_R10000_f8 | pblive|capsoft8|wk8|gb0|N0 | 14/8/10 | 29.2k / 81.8k / 324.7k | 1.00 / 0.95 | 0.98 / 1.00 | 3 / 3 | DISCARD (not top-quartile in >= 8 folds) |
| ATR_R10000_f8 | pblive|capoff|wk8|gb0|N0 | 14/8/10 | 29.2k / 81.8k / 324.7k | 0.99 / 0.93 | 0.98 / 1.00 | 3 / 3 | DISCARD (not top-quartile in >= 8 folds) |
| ATR_R10000_f8 | pblive|capoff|wk8|gb0|N2 | 14/8/10 | 29.2k / 81.8k / 324.7k | 0.99 / 0.93 | 0.98 / 1.00 | 3 / 3 | DISCARD (not top-quartile in >= 8 folds) |
| ATR_R10000_f8 | pblive|capsoft8|wk8|gb0|N2 | 14/8/10 | 29.2k / 81.8k / 324.7k | 1.00 / 0.95 | 0.98 / 1.00 | 3 / 3 | DISCARD (not top-quartile in >= 8 folds) |
| ATR_R10000_f8 | pblive|caphard|wkoff|gb0|N2 | 14/8/10 | 29.0k / 82.1k / 330.8k | 0.99 / 0.93 | 0.97 / 1.00 | 3 / 3 | DISCARD (not top-quartile in >= 8 folds) |
| ATR_R10000_f8 | pblive|caphard|wk12|gb0|N2 | 14/8/10 | 29.0k / 82.1k / 330.8k | 1.00 / 0.94 | 0.97 / 1.00 | 3 / 3 | DISCARD (not top-quartile in >= 8 folds) |
| ATR_R10000_f8 | pblive|caphard|wkoff|gb0|N0 | 14/8/10 | 29.0k / 82.1k / 330.8k | 0.99 / 0.93 | 0.97 / 1.00 | 3 / 3 | DISCARD (not top-quartile in >= 8 folds) |
| ATR_R10000_f8 | pblive|caphard|wk12|gb0|N0 | 14/8/10 | 29.0k / 82.1k / 330.8k | 1.00 / 0.94 | 0.97 / 1.00 | 3 / 3 | DISCARD (not top-quartile in >= 8 folds) |
| ATR_R10000_f8 | pblive|caphard|wk12|gb0|N3 | 14/8/10 | 29.0k / 82.2k / 330.8k | 1.00 / 0.94 | 0.97 / 1.00 | 3 / 3 | DISCARD (not top-quartile in >= 8 folds) |
| live60_P9 | pblive|capoff|wk12|gb1|N2 | 14/10/10 | 25.5k / 93.1k / 287.3k | 0.42 / 1.00 | 0.98 / 1.00 | 2 / 3 | DISCARD (not top-quartile in >= 8 folds) |
| live60_P9 | pblive|capoff|wkoff|gb0|N0 | 14/14/14 | 34.7k / 111.3k / 325.0k | 0.83 / 1.00 | 0.00 / 0.00 | 5 / 2 | DISCARD (not top-quartile in >= 8 folds) |
| live60_P9 | pblive|capoff|wk12|gb1|N0 | 14/10/10 | 25.1k / 92.5k / 298.9k | 0.39 / 1.00 | 0.96 / 1.00 | 3 / 3 | DISCARD (not top-quartile in >= 8 folds) |

**D3 frozen holdout: selection uses data <= 2025-06-30 only (cells with H1 mean >= live and H1 maxDD < live, ranked by H1 SD), top 5 scored on 2025-07..2026-10 (H2), live pair through the same policy for comparison: H2 mean 34.5k / SD 110.1k / maxDD 263.3k**

| option | lock set | lots | win | H1 mean / maxDD | H2 mean / SD / maxDD | H2 beats live on mean and maxDD |
|---|---|---|---|---|---|---|
| live60 | pblive|caphard|wkoff|gb0|N2 | 14/10/8 | live | 19.4k / 347.0k | 38.8k / 105.6k / 254.4k | True |
| live60 | pblive|caphard|wk12|gb0|N2 | 14/10/8 | live | 19.4k / 347.0k | 38.7k / 105.9k / 262.9k | True |
| centreHonest | pblive|caphard|wkoff|gb0|N0 | 14/10/8 | live | 19.3k / 333.0k | 37.8k / 105.4k / 341.5k | False |
| centreHonest | pblive|caphard|wk12|gb0|N0 | 14/10/8 | live | 19.0k / 314.9k | 37.6k / 105.8k / 353.3k | False |
| centreHonest | pblive|caphard|wkoff|gb0|N2 | 14/10/8 | live | 19.5k / 333.0k | 39.6k / 104.5k / 341.5k | False |

Selection-bias check over ALL screened cells (not just the top 5): 207 cells beat live on H1 mean and maxDD; of those 44 also beat it on H2 (21%).

## (2) Per-block findings

### Block A - soft locks

**A1 (108 cells)**: 0 beat live on WF mean AND maxDD. Softening every halt into a size step costs mean and does not buy drawdown: the lowest-maxDD soft cells (day steps 8-0 with give-back-to-0 and week-8: WF 24.0k / 99.6k / 338k but L8W 14.1k) are worse than live in L8W; the give-back must stay a hard flatten (its removal is what blows maxDD, see W1).

| cell | WF mean / SD / maxDD / worst | L8W mean / maxDD | IS mean / maxDD | WF d mean / d maxDD | L8W d mean / d maxDD |
|---|---|---|---|---|---|
| A1 / d8-0 / gb0 / wk8 / sc0 | 24.0k / 99.6k / 337.9k / -183.8k | 14.1k / 337.9k | 16.6k / 300.3k | -1.0k / -64k | -20.1k / +71k |
| A1 / d8-0 / gb0 / wk8 / sc1 | 19.9k / 108.2k / 339.2k / -225.3k | 32.7k / 270.5k | 15.1k / 402.4k | -5.0k / -62k | -1.5k / +3k |
| A1 / d8-4 / gb0 / wk8 / sc1 | 21.4k / 108.9k / 349.3k / -225.3k | 31.3k / 285.4k | 16.2k / 385.3k | -3.5k / -52k | -2.9k / +18k |
| A1 / d6-4 / gb0 / wk8 / sc1 | 20.4k / 105.0k / 350.8k / -214.0k | 32.4k / 243.1k | 18.9k / 399.5k | -4.6k / -51k | -1.9k / -24k |
| A1 / d6-4 / gb0 / wk4 / sc1 | 20.6k / 104.1k / 350.8k / -177.1k | 32.4k / 243.1k | 17.4k / 404.9k | -4.4k / -51k | -1.9k / -24k |
| A1 / d6-2 / gb0 / wk8 / sc1 | 20.0k / 105.0k / 350.8k / -214.0k | 31.7k / 243.1k | 18.9k / 399.5k | -4.9k / -51k | -2.5k / -24k |
| A1 / d6-2 / gb0 / wk4 / sc1 | 20.4k / 104.1k / 350.8k / -177.1k | 31.7k / 243.1k | 17.4k / 404.9k | -4.6k / -51k | -2.5k / -24k |
| A1 / d6-0 / gb0 / wk4 / sc1 | 19.3k / 104.9k / 350.8k / -177.1k | 31.7k / 243.1k | 17.2k / 404.9k | -5.6k / -51k | -2.5k / -24k |


**A2 signal-side filters after a give-back lock**: 4 cells, 0 beat live on WF mean and maxDD.

| cell | WF mean / SD / maxDD / worst | L8W mean / maxDD | IS mean / maxDD | WF d mean / d maxDD | L8W d mean / d maxDD |
|---|---|---|---|---|---|
| A2 / sig1 / halt_sess | 24.1k / 104.4k / 402.8k / -137.1k | 33.0k / 266.5k | 12.5k / 464.6k | -0.8k / +1k | -1.2k / -1k |
| A2 / sig2 / halt_sess | 24.1k / 104.4k / 402.8k / -137.1k | 33.0k / 266.5k | 12.5k / 464.6k | -0.8k / +1k | -1.2k / -1k |
| A2 / sig1 / halt_1h | 23.2k / 103.9k / 406.9k / -137.1k | 31.2k / 274.2k | 12.2k / 466.3k | -1.8k / +5k | -3.0k / +7k |
| A2 / sig2 / halt_1h | 23.2k / 103.9k / 406.9k / -137.1k | 31.2k / 274.2k | 12.2k / 466.3k | -1.8k / +5k | -3.0k / +7k |


**A3 halt-duration grid (give-back x cap, 36 cells)**: 36 cells, 0 beat live on WF mean and maxDD.

| cell | WF mean / SD / maxDD / worst | L8W mean / maxDD | IS mean / maxDD | WF d mean / d maxDD | L8W d mean / d maxDD |
|---|---|---|---|---|---|
| A3 / gb_nextsess / cap_nextsess | 24.6k / 104.5k / 401.9k / -137.1k | 33.6k / 267.5k | 13.7k / 407.4k | -0.4k / +0k | -0.7k / +0k |
| A3 / gb_nextsess / cap_2h | 24.6k / 104.5k / 402.1k / -137.1k | 33.5k / 267.5k | 13.7k / 407.4k | -0.4k / +0k | -0.7k / +0k |
| A3 / gb_nextRTH / cap_nextsess | 24.2k / 104.4k / 402.3k / -137.1k | 33.6k / 267.1k | 12.5k / 465.2k | -0.8k / +1k | -0.6k / -0k |
| A3 / gb_nextRTH / cap_2h | 24.2k / 104.4k / 402.5k / -137.1k | 33.6k / 267.1k | 12.5k / 465.2k | -0.8k / +1k | -0.6k / -0k |
| A3 / gb_sess / cap_nextsess | 24.0k / 104.4k / 402.5k / -137.1k | 33.6k / 268.2k | 12.5k / 465.3k | -1.0k / +1k | -0.6k / +1k |
| A3 / gb_nextsess / cap_nextRTH | 24.7k / 104.6k / 402.6k / -137.1k | 33.6k / 267.5k | 13.7k / 407.4k | -0.3k / +1k | -0.6k / +0k |


**A4 softened profit locks / trailing give-back**: 28 cells, 2 beat live on WF mean and maxDD.

| cell | WF mean / SD / maxDD / worst | L8W mean / maxDD | IS mean / maxDD | WF d mean / d maxDD | L8W d mean / d maxDD |
|---|---|---|---|---|---|
| A4 / pbwin0 / cap1 / trailNone | 28.2k / 110.4k / 370.0k / -137.1k | 39.7k / 267.1k | 13.8k / 407.5k | +3.2k / -32k | +5.4k / +0k |
| A4 / pbwin1 / cap1 / trailNone | 28.4k / 111.2k / 370.0k / -137.1k | 44.1k / 267.1k | 13.8k / 407.5k | +3.4k / -32k | +9.9k / +0k |
| A4 / pbwin1 / cap0 / trailNone | 25.0k / 104.0k / 401.6k / -137.1k | 32.7k / 267.1k | 13.7k / 407.5k | +0.1k / +0k | -1.5k / +0k |
| A4 / pbwin0 / cap0 / trailNone | 25.0k / 104.5k / 401.6k / -137.1k | 34.2k / 267.1k | 13.7k / 407.5k | +0.0k / +0k | +0.0k / +0k |
| A4 / pbwin1 / cap0 / trail(0.33, 4) | 34.0k / 127.6k / 520.5k / -139.3k | 34.2k / 424.6k | 0.9k / 533.3k | +9.0k / +119k | -0.0k / +157k |
| A4 / pbwin0 / cap0 / trail(0.33, 4) | 33.4k / 128.0k / 549.2k / -139.3k | 34.5k / 424.6k | 0.8k / 533.3k | +8.4k / +148k | +0.3k / +157k |


A2/A3 reading: signal-side re-entry restrictions and halt durations other than "rest of day" only move mean by -0.3k to -3.7k with no DD gain (shorter halts re-enter into the same losing regime); A4: softening the combined cap into 8 lots (+3.2k, -32k maxDD vs live) is the one profit-side softening that helps, same as removing the cap in W1; any trailing give-back at 8 or 4 lots raises maxDD by 150-400k.

### Block B - adaptive levels


**B2 levels in strategy-vol units** (arm / floors = live x m x trailing-4-week-SD ratio): 9 cells; beat live on WF mean AND maxDD: 2.

| cell | WF mean / SD / maxDD / worst | L8W mean / maxDD | IS mean / maxDD | WF d mean / d maxDD | L8W d mean / d maxDD |
|---|---|---|---|---|---|
| B2 / m1.0 / floors | 24.6k / 104.1k / 325.0k / -210.2k | 33.6k / 267.1k | 12.6k / 430.5k | -0.4k / -77k | -0.6k / +0k |
| B2 / m1.5 / floors | 29.4k / 108.6k / 325.0k / -236.3k | 41.5k / 267.1k | 19.7k / 293.6k | +4.4k / -77k | +7.3k / +0k |
| B2 / m2.0 / floors | 30.6k / 110.4k / 331.4k / -220.7k | 41.6k / 267.1k | 18.5k / 293.6k | +5.6k / -70k | +7.4k / +0k |
| B2 / m1.0 / both | 22.2k / 112.3k / 589.5k / -217.0k | 39.0k / 259.0k | 11.5k / 442.3k | -2.8k / +188k | +4.8k / -8k |
| B2 / m1.5 / both | 34.2k / 128.8k / 639.4k / -296.0k | 37.6k / 603.2k | 9.9k / 507.3k | +9.2k / +238k | +3.4k / +336k |
| B2 / m1.0 / arm | 20.8k / 107.9k / 659.4k / -137.1k | 39.6k / 259.0k | 10.8k / 464.3k | -4.2k / +258k | +5.4k / -8k |


**B3 regime-conditional levels**: 6 cells; beat live on WF mean AND maxDD: 1.

| cell | WF mean / SD / maxDD / worst | L8W mean / maxDD | IS mean / maxDD | WF d mean / d maxDD | L8W d mean / d maxDD |
|---|---|---|---|---|---|
| B3 / friTight | 25.0k / 100.0k / 359.0k / -137.1k | 42.1k / 162.7k | 8.5k / 484.8k | +0.1k / -43k | +7.9k / -104k |
| B3 / friLoose | 27.0k / 107.9k / 407.7k / -170.2k | 28.3k / 267.1k | 12.6k / 447.5k | +2.1k / +6k | -5.9k / +0k |
| B3 / vixLooseHigh | 28.2k / 118.6k / 428.4k / -168.8k | 35.2k / 267.1k | 9.8k / 420.8k | +3.3k / +27k | +1.0k / +0k |
| B3 / asiaTight | 29.5k / 99.4k / 497.0k / -149.2k | 34.1k / 161.8k | 10.2k / 457.2k | +4.5k / +95k | -0.1k / -105k |
| B3 / vixTightHigh | 27.6k / 102.0k / 502.1k / -168.8k | 34.2k / 267.1k | 14.8k / 393.7k | +2.7k / +100k | +0.0k / +0k |
| B3 / asiaLoose | 20.9k / 95.5k / 603.0k / -168.8k | 29.7k / 223.0k | 18.6k / 315.9k | -4.1k / +201k | -4.5k / -44k |


**B4 arm only after N closed trades**: 3 cells; beat live on WF mean AND maxDD: 0.

| cell | WF mean / SD / maxDD / worst | L8W mean / maxDD | IS mean / maxDD | WF d mean / d maxDD | L8W d mean / d maxDD |
|---|---|---|---|---|---|
| B4 / N2 | 26.2k / 105.7k / 404.7k / -137.6k | 29.8k / 267.1k | 13.5k / 407.5k | +1.2k / +3k | -4.4k / +0k |
| B4 / N3 | 33.2k / 111.5k / 425.1k / -138.3k | 38.8k / 272.1k | 10.6k / 481.9k | +8.3k / +23k | +4.6k / +5k |
| B4 / N4 | 36.5k / 117.4k / 461.0k / -137.1k | 50.4k / 267.0k | 6.9k / 623.7k | +11.5k / +59k | +16.2k / -0k |


**B5 peak basis**: 3 cells; beat live on WF mean AND maxDD: 0.

| cell | WF mean / SD / maxDD / worst | L8W mean / maxDD | IS mean / maxDD | WF d mean / d maxDD | L8W d mean / d maxDD |
|---|---|---|---|---|---|
| B5 / haircut10 | 25.7k / 109.9k / 431.8k / -136.3k | 57.1k / 262.1k | 15.4k / 406.4k | +0.7k / +30k | +22.9k / -5k |
| B5 / haircut20 | 27.0k / 110.5k / 459.4k / -136.3k | 58.3k / 256.3k | 9.6k / 615.5k | +2.0k / +58k | +24.1k / -11k |
| B5 / realized | 39.8k / 129.9k / 591.2k / -137.4k | 62.8k / 442.4k | 1.7k / 698.8k | +14.8k / +190k | +28.6k / +175k |


**B6 week-floor alternatives**: 5 cells; beat live on WF mean AND maxDD: 2.

| cell | WF mean / SD / maxDD / worst | L8W mean / maxDD | IS mean / maxDD | WF d mean / d maxDD | L8W d mean / d maxDD |
|---|---|---|---|---|---|
| B6 / nofloor | 29.2k / 102.0k / 325.0k / -211.3k | 34.2k / 267.1k | 18.7k / 293.6k | +4.2k / -77k | +0.0k / +0k |
| B6 / wk12R | 28.8k / 102.8k / 325.0k / -202.3k | 34.2k / 267.1k | 18.7k / 293.6k | +3.8k / -77k | +0.0k / +0k |
| B6 / wk10R | 27.3k / 104.6k / 403.8k / -171.6k | 34.2k / 267.1k | 17.7k / 293.6k | +2.3k / +2k | +0.0k / +0k |
| B6 / nofloor+A1step | 26.8k / 119.7k / 587.4k / -272.6k | -5.2k / 517.4k | 15.0k / 446.5k | +1.8k / +186k | -39.4k / +250k |
| B6 / rolling5 | 19.7k / 102.9k / 664.1k / -192.8k | 33.5k / 272.6k | 12.8k / 462.1k | -5.3k / +262k | -0.7k / +5k |


B reading: the only B cells that beat live on both are the ones that loosen or remove the week floor (B2 floors m=1.5/2.0, B6 wk12R / no floor / rolling-5 fails): the same finding as W1. B4 (arm after N=3-4 trades) raises mean (+8k / +11k) at the price of +23k / +59k maxDD; B5 realised-only peak raises mean +15k and maxDD +190k. Nothing in B lowers maxDD without the week-floor effect.

### Block C - risk budgets and overlays

**C1/C2 budgets (locks OFF, no halts)**

| cell | WF mean / SD / maxDD / worst | L8W mean / maxDD | IS mean / maxDD | WF d mean / d maxDD | L8W d mean / d maxDD |
|---|---|---|---|---|---|
| C1 / day30k / wk100k | 30.8k / 123.7k / 742.5k / -101.1k | 8.1k / 297.9k | 3.4k / 447.5k | +5.8k / +341k | -26.1k / +31k |
| C1 / day0k / wk134k | 42.3k / 160.7k / 811.3k / -136.0k | 107.0k / 365.8k | -6.6k / 672.5k | +17.4k / +410k | +72.8k / +99k |
| C1 / day0k / wk100k | 39.4k / 154.0k / 816.0k / -102.7k | 114.7k / 298.2k | -13.3k / 1124.9k | +14.4k / +414k | +80.5k / +31k |
| C1 / day0k / wk170k | 41.6k / 167.2k / 861.7k / -174.6k | 98.1k / 436.8k | -0.6k / 791.9k | +16.7k / +460k | +63.9k / +170k |
| C1 / day40k / wk100k | 36.3k / 132.6k / 877.6k / -101.1k | 6.3k / 299.4k | -3.2k / 481.9k | +11.3k / +476k | -27.9k / +32k |
| C1 / day30k / wk134k | 30.2k / 127.4k / 903.1k / -134.8k | -11.7k / 388.1k | 0.6k / 542.9k | +5.2k / +501k | -45.9k / +121k |
| C1 / day30k / wk170k | 30.7k / 128.5k / 962.6k / -150.1k | 3.3k / 417.4k | 4.3k / 416.0k | +5.7k / +561k | -30.9k / +150k |
| C1 / day30k / wk0k | 30.7k / 128.5k / 962.6k / -150.1k | 3.3k / 417.4k | 4.3k / 416.0k | +5.7k / +561k | -30.9k / +150k |
| C1 / day50k / wk100k | 36.6k / 135.7k / 981.6k / -100.4k | 20.7k / 298.1k | 1.3k / 437.5k | +11.6k / +580k | -13.5k / +31k |
| C1 / day40k / wk134k | 37.0k / 137.2k / 1026.7k / -135.3k | 17.4k / 402.4k | 2.1k / 507.9k | +12.1k / +625k | -16.8k / +135k |
| NOLOCK | 46.9k / 171.8k / 1037.3k / -458.8k | 53.5k / 793.3k | 4.9k / 754.2k | +21.9k / +636k | +19.3k / +526k |
| C1 / day50k / wk134k | 33.4k / 142.0k / 1131.4k / -134.9k | -0.4k / 399.2k | 4.2k / 459.9k | +8.4k / +730k | -34.6k / +132k |
| C1 / day50k / wk170k | 38.6k / 142.4k / 1138.1k / -170.5k | 35.2k / 510.7k | 4.4k / 490.1k | +13.6k / +736k | +1.0k / +244k |
| C1 / day40k / wk170k | 35.9k / 139.9k / 1212.0k / -170.0k | 19.0k / 496.6k | 3.5k / 500.6k | +10.9k / +810k | -15.2k / +229k |
| C1 / day50k / wk0k | 37.1k / 145.5k / 1290.9k / -246.1k | 16.1k / 663.6k | 6.2k / 493.5k | +12.2k / +889k | -18.1k / +396k |
| C1 / day40k / wk0k | 35.2k / 141.6k / 1325.3k / -200.9k | 11.3k / 557.8k | 5.1k / 434.9k | +10.2k / +924k | -22.9k / +291k |


**C3 drawdown-control overlay, Kelly 0.25 (+DD overlay), C4 target-vol (live locks and per-book+give-back locks)**

| cell | WF mean / SD / maxDD / worst | L8W mean / maxDD | IS mean / maxDD | WF d mean / d maxDD | L8W d mean / d maxDD |
|---|---|---|---|---|---|
| C3 / kelly0.25_dd / live | 18.4k / 75.7k / 313.5k / -135.4k | 18.9k / 286.4k | 2.7k / 264.3k | -6.6k / -88k | -15.3k / +19k |
| C3 / kelly0.25_dd / pb+gb | 17.9k / 78.0k / 313.5k / -230.7k | 18.9k / 286.4k | 2.7k / 264.3k | -7.0k / -88k | -15.3k / +19k |
| C0 / base / pb+gb | 34.7k / 111.3k / 325.0k / -211.3k | 41.6k / 267.1k | 19.0k / 293.6k | +9.8k / -77k | +7.4k / +0k |
| C4 / vt75k / live | 25.9k / 95.9k / 349.5k / -135.7k | 29.3k / 249.0k | 10.8k / 452.2k | +0.9k / -52k | -4.9k / -18k |
| C4 / vt90k / pb+gb | 31.9k / 100.8k / 358.3k / -211.3k | 35.2k / 246.6k | 20.3k / 287.4k | +7.0k / -43k | +1.0k / -20k |
| C4 / vt60k / pb+gb | 27.4k / 90.1k / 359.4k / -151.8k | 30.5k / 316.3k | 9.8k / 401.5k | +2.5k / -42k | -3.7k / +49k |
| C4 / vt60k / live | 19.9k / 88.2k / 389.0k / -150.6k | 26.1k / 389.0k | 7.9k / 427.9k | -5.1k / -13k | -8.1k / +122k |
| C0 / base / live | 25.0k / 104.5k / 401.6k / -137.1k | 34.2k / 267.1k | 13.7k / 407.5k | +0.0k / +0k | +0.0k / +0k |
| C3 / kelly0.25 / pb+gb | 22.3k / 87.4k / 402.0k / -230.7k | 36.8k / 293.0k | 0.8k / 462.0k | -2.7k / +0k | +2.6k / +26k |
| C4 / vt90k / live | 25.0k / 105.7k / 406.4k / -137.1k | 26.1k / 293.5k | 10.6k / 513.6k | +0.0k / +5k | -8.1k / +26k |
| C3 / kelly0.25 / live | 22.1k / 85.1k / 417.8k / -135.4k | 35.2k / 293.0k | 1.3k / 435.6k | -2.8k / +16k | +1.0k / +26k |
| C4 / vt75k / pb+gb | 30.4k / 99.6k / 419.7k / -211.3k | 27.4k / 361.7k | 14.4k / 327.5k | +5.4k / +18k | -6.8k / +95k |
| C3 / dd_overlay / pb+gb | 19.8k / 96.3k / 439.7k / -211.3k | 31.8k / 307.8k | 3.5k / 439.9k | -5.2k / +38k | -2.4k / +41k |
| C3 / dd_overlay / live | 14.7k / 88.9k / 448.8k / -137.1k | 24.4k / 307.8k | 0.3k / 559.9k | -10.3k / +47k | -9.8k / +41k |


C reading: budgets cap the worst week but not the maxDD (0.74-1.3M); the overlays and target-vol shrink SD and mean together; Kelly 0.25 + DD overlay reaches maxDD 313k but at 18.4k mean and a weaker L8W (18.9k) - it is the only C cell with a DD gain and it gives up 6.6k/wk.

### Block D - see (1): the joint screen with fold stability and the frozen H1->H2 holdout.

### Block E - plateau


**ST book**: 405 cells; live book alone WF 19.8k / SD 80.6k / maxDD 368.8k (IS 5.7k); share of cells beating the live book on WF mean 26%, on mean AND maxDD 2%; grid mean WF 16.8k vs live 19.8k; live WF-mean rank 107 of 405; IS-WF rank correlation across cells 0.10.
  plateau criterion 'mean': largest contiguous region (3x3-neighbourhood >= 80% beating) = 10 cells at third-axis index 0 (EMA=100), ATR [84, 96, 108, 120, 132, 144] x mult [1.4, 1.6, 1.8]; live cell inside: False
  plateau criterion 'mean+maxDD': no contiguous region reaches 80%.
  robust centre (max over cells of the MIN over 8 neighbours, WF mean): ATR=84, mult=1.6, EMA=100: min-neighbour 23.6k, centre WF 25.6k/348.5k, IS 1.0k (live 19.8k/368.8k). Selected on WF itself: contaminated; a fold-wise version needs per-fold series (not stored).

**HM book**: 162 cells; live book alone WF 11.9k / SD 76.8k / maxDD 501.3k (IS 1.1k); share of cells beating the live book on WF mean 90%, on mean AND maxDD 73%; grid mean WF 18.0k vs live 11.9k; live WF-mean rank 146 of 162; IS-WF rank correlation across cells -0.28.
  plateau criterion 'mean': largest contiguous region (3x3-neighbourhood >= 80% beating) = 49 cells at third-axis index 0 (anchor=0), fast [14, 16, 18, 20, 22, 24, 26] x slow [39, 44, 50, 55, 61, 66, 72]; live cell inside: True
  plateau criterion 'mean+maxDD': largest contiguous region (3x3-neighbourhood >= 80% beating) = 20 cells at third-axis index 0 (anchor=0), fast [14, 16, 18, 20, 22, 24, 26] x slow [39, 44, 50, 55, 61, 66, 72]; live cell inside: False
  robust centre (max over cells of the MIN over 8 neighbours, WF mean): fast=14, slow=39, anchor=0: min-neighbour 19.9k, centre WF 20.4k/497.5k, IS -4.0k (live 11.9k/501.3k). Selected on WF itself: contaminated; a fold-wise version needs per-fold series (not stored).

**E2 ensemble over the plateau vs 200 random same-size regions (mapping screen)**

| ensemble | WF mean / SD / maxDD | L8W mean / maxDD | rank of mean | rank of maxDD (lower better) among random |
|---|---|---|---|---|
| HMplateau+liveST | 30.1k / 99.5k / 528.9k | 53.7k / 244.0k | 0.75 | 0.00 |
| STplateau+liveHM | 41.8k / 108.4k / 421.0k | 76.1k / 173.2k | 1.00 | 0.41 |
| both books | 35.0k / 89.4k / 404.6k | 60.6k / 142.4k | - | - |

live pair through the same path: 25.0k / 104.5k / 401.6k. E2 reading: averaging over the ST plateau (10 cells, EMA 100) lifts the WF mean (rank 1.00 among 200 random 10-cell ST sets) but not the maxDD (421k; rank 0.41), the HM plateau (49 cells) leaves mean at the random level and worsens maxDD (529k); neither is a drawdown improvement and neither was replayed (mapping screen; only the W3 union trades were replayed), so E2 is not a candidate.

### Block F - F1 PENDING: the live StratTrades_DualStrat2 file is not on disk (Friday 10-23, supplied by the user). The reconciliation script is ready (firm/f1_recon.py, wraps l2vast/pairP2/live_vs_replay_p9.py); it reports PENDING without the file and fabricates nothing. When the file lands: join rate live (3/8) vs replay (78%), per-trade slip, and the XJ stop-join saving re-based on the live join rate, then D1's top 20 re-run at that cost.

## (3) Best configuration found - DualStrat2 parameter sheet (exact cell, fixed 60 pt, corrected-P9 points; no L2 layer needed)

| parameter | live | candidate BEST5 |
|---|---|---|
| bracket | 60 pt stop = target | 60 pt (unchanged) |
| lots | 14 / 14 | Asia 14, London 10, NY 10 (per book) |
| per-book day lock | -2R / +5R (R = $16.8k) | unchanged |
| combined day cap | +8R, flatten + halt | REMOVED |
| give-back arm / keep | arm 2R, keep 50%, tick clock, from first trade | arm 2R, keep 67%, armed only after >= 2 closed trades in the day |
| week floor | -8R, halt to Monday | -12R (never fires in the 45 months: equivalent to OFF) |
| signals / windows / EMA | unchanged | unchanged |

Scores: WF 25.5k / SD 93.1k / maxDD 287k / worst -185k; L8W 56.1k / 183k; IS 13.2k / 305k (benchmark 25.0k / 104.5k / 401k / -137k; 34.2k / 267k; 13.7k / 407k). Nulls (500 worlds): placebo locks with the same in-situ fire hazard: maxDD rank 1.00 (placebo mean maxDD 623k), mean rank 0.42 (income not better than random locks); random-subset down-sizing of the same share: mean rank 0.98, maxDD rank 1.00. F-count: this cell is one of the 23,040 screened D1 cells (20,160 prereg + the exact-P9 option and the f8 ATR variants) inside 3,368 F_P families (prior families included in the deflation). Parameters changed vs live: 8 (3 for the simpler 'remove cap and week floor' set). Deflated Sharpe: BEST5 0.66 (SR0 0.239), remove-cap-and-week-floor (3 parameters) 0.82 (WF 34.7k / SD 111k / maxDD 325k, L8W 41.6k / 267k, IS 19.0k / 293k). Honest probability it is noise: about 34% for BEST5 and 18% for the 3-parameter set (1 - DSR; the 500-world placebo ranks are conditional on the locks having any timing skill at all, which the give-back plainly has). Worst week widens from -137k to -185k / -211k: the week floor was doing that job. Fold stability (D2): the best exact cell is top-quartile (of all 23,040 screened cells) in 2 of 11 folds on mean and 3 of 11 on maxDD; the 3-parameter 'remove cap and week floor' set in 5 / 2: by the frozen D2 rule (>= 8 of 11 folds) EVERY screened finalist is discarded, i.e. the parameter sheet above is the best configuration FOUND, not one that survives the prereg filters. Frozen holdout (selection <= 2025-06-30): of the top-5 H1 picks 2 beat live on H2 mean and maxDD (the 3 W3-centre picks fail), and over ALL 207 H1 winners only 44 (21%) persist on H2.
## (4) Verdict
No cell meets the strict objective (WF mean >= benchmark AND maxDD <= 0.7 x benchmark): the closest has maxDD 0.72 x benchmark. The give-back arm is the only lock with real value; the combined cap and the week floor cost income and drawdown in WF (W1, confirmed on the exact engine with 200 placebo worlds). Soft locks, adaptive levels, budgets, overlays do not beat the best hard-lock set. The practical candidate is a table/parameter change (remove cap and week floor, or the 8-parameter BEST5), with the widened worst week as the stated cost; it does NOT pass D2 fold stability or the 0.7x objective, so it is a lead for a Sim week, not a finding. F1 (live fill truth) is pending.

<!--F1-ADDENDUM-BEGIN-->
## F1 addendum - live vs replay (rewritten on each data/live push; latest run below)

### F1 addendum (data/live first push; generated 2026-10-27 22:11Z; live window 0001-01-01..2026-10-26, 82 DualStrat2 trades)

**Live stop exits: N = 21** (StopJoin filled 8, StopJoinFallback 12, StopJoinRejected 1; plus 19 targets and 2 ComboLock exits). **Join rate** (filled / filled+fallback, rejected excluded) = 8/20 = **0.40, exact 95% CI [0.19, 0.64]**; counting the position-limit reject as a failure 8/21 = 0.38 [0.18, 0.62]. Replay assumption 0.78 lies OUTSIDE the live interval. 1 join attempt(s) were rejected by the broker (counted separately; the retained trace is the connect-time order history with state Rejected and no reason text - the position-limit cause is taken from the user). Earlier count quoted as '3/8' is not what the CSV shows.

Join-order lifecycle (NT8 trace, orders since 10-21, N = 12 join orders): 6 filled completely (median working time 0.9 s), 1 partly filled then fallback, 5 not filled at all before the fallback (median working time 3.2 s = the timeout); lots joined 86 of 155 exit lots (lot-weighted join share 0.55); 5 market fallback orders (69 lots).

**Exit slip vs the nominal stop level (entry average -/+ 60 pt; + = better than the stop), live vs replay expectation (2026 replay stops):**

| exit type | live N | live mean (95% CI) | replay mean |
|---|---|---|---|
| StopJoin filled | 8 | +0.52 (-0.32, +1.36) | -0.52 (XJ arm; market arm -1.74) |
| StopJoinFallback (market) | 12 | -4.46 (-6.29, -2.63) | -1.74 (XJ arm; market arm -1.74) |
| all stop exits | 21 | -2.45 (-3.95, -0.95) | -0.52 (XJ arm; market arm -1.74) |

Live stop exits are -1.93 pt worse than the replay's XJ expectation per stop exit (live fallback market exits -4.46 vs replay market -1.74); with N = 21 the interval is wide - do not over-read. **Entry slip: PENDING** ({'note': 'tape mids from the 10-19..10-23 L2 extension (join_recon2, 2026-10-25); pts per lot, + = adverse; exchange clock = log stamp - 27 ms', 'ST_HM_14lot_vs_slice_mid': {'n': 29, 'mean': 0.458, 'ci': [0.244, 0.672]}, 'ST_HM_14lot_replay_vs_slice_mid': {'n': 29, 'mean': 0.529, 'ci': [0.466, 0.592]}, 'ST_HM_14lot_vs_mid_T0': {'n': 29, 'mean': -0.411, 'ci': [-2.452, 1.63]}, 'traced21_live': {'n': 21, 'mean': 0.591, 'ci': [0.422, 0.76]}, 'traced21_replay': {'n': 21, 'mean': 0.56, 'ci': [0.49, 0.629]}, 'ST_HM_8lot_vs_slice_mid': {'n': 11, 'mean': 0.075, 'ci': [-0.196, 0.346]}, 'ST_HM_8lot_replay': {'n': 11, 'mean': 0.321, 'ci': [0.286, 0.356]}, 'slice_exact_match': 0.8257489864632723, 'slice_px_diff': -0.013123582766439913}).

**Re-score at the measured join rate** (replay-policy points on the live 60-pt trades; XJ gain x live/replay where the per-fold policy chose XJ; last column additionally charges the live exit shortfall of -1.93 pt on every stop exit): WF mean / SD / maxDD; L8W mean / maxDD

| cell | replay (78%) | live point 0.40 | live lower 0.19 | live upper 0.64 | point + live exit shortfall |
|---|---|---|---|---|---|
| live locks (benchmark) | 27.2k / 106.7k / 371.4k; 41.2k / 174.8k | 26.8k / 106.9k / 371.0k; 31.0k / 181.7k | 24.5k / 106.8k / 372.5k; 20.6k / 182.4k | 27.6k / 107.7k / 380.8k; 40.5k / 174.8k | 19.8k / 101.1k / 385.7k; 0.8k / 226.9k |
| remove cap + week floor | 35.9k / 113.9k / 347.7k; 47.0k / 185.1k | 34.8k / 114.9k / 343.1k; 36.8k / 192.0k | 31.9k / 114.0k / 346.2k; 26.4k / 192.7k | 36.9k / 114.6k / 346.0k; 46.3k / 185.1k | 23.8k / 111.4k / 388.8k; 1.0k / 257.9k |
| BEST5 | 24.7k / 94.6k / 331.7k; 57.4k / 122.8k | 22.8k / 94.3k / 339.8k; 46.0k / 148.2k | 21.6k / 94.9k / 338.0k; 40.4k / 148.8k | 24.0k / 94.1k / 330.3k; 54.1k / 123.3k | 15.5k / 97.0k / 382.2k; 34.9k / 153.8k |
| USER forward set (cap off, wk12, London/NY 10) | 32.4k / 107.6k / 332.1k; 62.4k / 127.4k | 29.8k / 107.3k / 339.8k; 39.9k / 148.2k | 27.9k / 106.5k / 337.6k; 35.5k / 148.8k | 31.7k / 107.4k / 330.5k; 61.9k / 127.4k | 21.1k / 107.1k / 363.2k; 28.6k / 155.2k |

Ranking check at each scenario (does the candidate still beat the live locks on WF mean AND maxDD?): replay (78%): remove cap + week floor yes, BEST5 no, USER forward set yes; live point 0.40: remove cap + week floor yes, BEST5 no, USER forward set yes; live lower 0.19: remove cap + week floor yes, BEST5 no, USER forward set yes; live upper 0.64: remove cap + week floor yes, BEST5 no, USER forward set yes.

**D1 top-20 (+ exact best cells) re-scored at the measured rate** (all options): benchmark = the live pair (live locks, 14/14/14, live signals) at the same join-rate scale.

| option | lock set | lots | WF mean / maxDD at 78% | at live point | at live lower bound | beats live-at-same-scale (WF mean & maxDD) at 78% / point / lower |
|---|---|---|---|---|---|---|
| ATR_R10000_f4 | pblive|capsoft8|wk8|gb0|N0 | 14/8/10 | 28.3k / 327.9k | 27.0k / 350.2k | 25.7k / 401.8k | yes / yes / no |
| ATR_R10000_f4 | pblive|capsoft8|wk8|gb0|N2 | 14/8/10 | 28.3k / 327.9k | 27.0k / 350.2k | 25.7k / 401.8k | yes / yes / no |
| ATR_R10000_f4 | pblive|capoff|wk8|gb0|N0 | 14/8/10 | 28.3k / 327.9k | 27.0k / 350.2k | 25.7k / 401.8k | yes / yes / no |
| ATR_R10000_f4 | pblive|capoff|wk8|gb0|N2 | 14/8/10 | 28.3k / 327.9k | 27.0k / 350.2k | 25.7k / 401.8k | yes / yes / no |
| ATR_R10000_f4 | pblive|capsoft8|wk8|gb0|N3 | 14/8/10 | 28.3k / 327.9k | 27.0k / 350.2k | 25.7k / 401.8k | yes / yes / no |
| ATR_R10000_f4 | pblive|capoff|wk8|gb0|N3 | 14/8/10 | 28.3k / 327.9k | 27.0k / 350.2k | 25.7k / 401.8k | yes / yes / no |
| ATR_R10000_f8 | pblive|caphard|wk8|gb0|N3 | 14/8/10 | 28.9k / 324.7k | 27.4k / 375.0k | 26.8k / 380.6k | yes / no / no |
| ATR_R10000_f8 | pblive|caphard|wk8|gb0|N0 | 14/8/10 | 28.9k / 324.7k | 27.5k / 375.0k | 26.9k / 380.6k | yes / no / no |
| ATR_R10000_f8 | pblive|caphard|wk8|gb0|N2 | 14/8/10 | 28.9k / 324.7k | 27.5k / 375.0k | 26.9k / 380.6k | yes / no / no |
| ATR_R10000_f8 | pblive|capsoft8|wk8|gb0|N3 | 14/8/10 | 29.0k / 324.7k | 27.5k / 375.0k | 26.8k / 380.6k | yes / no / no |
| ATR_R10000_f8 | pblive|capoff|wk8|gb0|N3 | 14/8/10 | 29.0k / 324.7k | 27.5k / 375.0k | 26.8k / 380.6k | yes / no / no |
| ATR_R10000_f8 | pblive|capsoft8|wk8|gb0|N0 | 14/8/10 | 29.0k / 324.7k | 27.5k / 375.0k | 26.8k / 380.6k | yes / no / no |
| ATR_R10000_f8 | pblive|capoff|wk8|gb0|N0 | 14/8/10 | 29.0k / 324.7k | 27.5k / 375.0k | 26.8k / 380.6k | yes / no / no |
| ATR_R10000_f8 | pblive|capoff|wk8|gb0|N2 | 14/8/10 | 29.0k / 324.7k | 27.5k / 375.0k | 26.8k / 380.6k | yes / no / no |
| ATR_R10000_f8 | pblive|capsoft8|wk8|gb0|N2 | 14/8/10 | 29.0k / 324.7k | 27.5k / 375.0k | 26.8k / 380.6k | yes / no / no |
| ATR_R10000_f8 | pblive|caphard|wkoff|gb0|N2 | 14/8/10 | 28.8k / 330.8k | 27.2k / 375.0k | 27.0k / 380.6k | yes / no / no |
| ATR_R10000_f8 | pblive|caphard|wk12|gb0|N2 | 14/8/10 | 28.8k / 330.8k | 27.2k / 375.0k | 27.0k / 380.6k | yes / no / no |
| ATR_R10000_f8 | pblive|caphard|wkoff|gb0|N0 | 14/8/10 | 28.8k / 330.8k | 27.2k / 375.0k | 27.0k / 380.6k | yes / no / no |
| ATR_R10000_f8 | pblive|caphard|wk12|gb0|N0 | 14/8/10 | 28.8k / 330.8k | 27.2k / 375.0k | 27.0k / 380.6k | yes / no / no |
| ATR_R10000_f8 | pblive|caphard|wk12|gb0|N3 | 14/8/10 | 28.8k / 330.8k | 27.1k / 375.0k | 26.9k / 380.6k | yes / no / no |
| live60_P9 | pblive|capoff|wk12|gb1|N2 | 14/10/10 | 24.7k / 331.7k | 22.8k / 339.8k | 21.6k / 338.0k | no / no / no |
| live60_P9 | pblive|capoff|wkoff|gb0|N0 | 14/14/14 | 35.9k / 347.7k | 34.8k / 343.1k | 31.9k / 346.2k | yes / yes / yes |
| live60_P9 | pblive|capoff|wk12|gb1|N0 | 14/10/10 | 24.3k / 331.7k | 22.4k / 339.8k | 21.2k / 338.0k | no / no / no |

The verdict (beats live at the same scale) is the same at all three scales for 3 of 23 re-scored cells. Because N = 21 the live join rate is not stable enough to re-rank cells; the re-base is a sensitivity, not an estimate.

<!--F1-ADDENDUM-END-->
