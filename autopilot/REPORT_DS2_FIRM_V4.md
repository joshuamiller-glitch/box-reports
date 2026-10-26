# REPORT DS2-FIRM v4 - lock portfolio, re-centring, vol brackets with chosen locks, session size, joint cell, replay bias (trackFIRM, 2026-10-22); research only

Prereg: l2vast/PREREG_DS2_FIRM_V4.md (frozen before scoring). Benchmark = corrected P9 14/14, $4.84: WF 25.0k / SD 104.5k / maxDD 401k / worst -137k; L8W 34.2k / 109.4k / 267k; IS 13.7k / 95.9k / 407k. **Which cells need the L2 execution layer:** W1 and W4 (fixed 60 pt, live signals) do NOT - trades, brackets, windows, locks are exact on the 1-s tape and the P9 points are the exact corrected table (only the fill of a lock flatten is modelled: +0.5 / +1.0 pt sensitivity changes means by < 1.2k); W2 (ATR brackets), W3 (other signal cells) and W5 (joint) DO: they use the path table to screen and DIRECT L2 replay (raw mbp-10, EM/S14x1 entries, XS4/XJ/XS0 stop exits, per-fold arm choice) to decide - replays done: ATR20/T2H/k1.0 (45 months), the W3 centre trades (45 months, 9,609 unique new trades). The replay policy is restricted to the replayed arms, so a replay cell is compared with the live pair through the same policy (RB: WF 28.4k / 106.2k / 371k; L8W 45.8k / 219k; IS 13.7k / 407k), and the P9 benchmark; the ATR20/T2H/k0.8 trades (22.8k) were NOT replayed (the sibling k=1.0 flips its DD sign), so its survivors are mapping-only and flagged.

## W1 - lock portfolio


Which cells need the L2 execution layer: none of W1. Trades, brackets and P9 execution points of the live pair are the exact benchmark table, locks run on the 1-s tape; the only modelled element is the fill of a lock flatten (next printed second, 0.5 pt slip, original-engine convention). The sensitivity table below adds +0.5 / +1.0 pt adverse slip to every lock-flattened row; conclusions do not change. The mapping-vs-replay bias applies only to non-60 brackets (W2, W3 new signals, W5).

Locks: pb = per-book day -2R/+5R; cap = combined 8R; gb = give-back arm 2R keep 50% (tick clock); wk8 = week floor 8R; wk5 = week floor 5R ($84k). With wk8 and wk5 together the tighter 5R applies. Vol-defined R = dollar R at fixed 60 pt / 14 lots (identical by construction).

**All 32 subsets (sorted by WF maxDD; the benchmark = pb+cap+gb+wk8). Folds: number of the 11 read windows in which the subset beats the benchmark on mean / on maxDD.**

| locks | WF mean | WF SD | WF maxDD | WF worst | L8W mean | L8W SD | L8W maxDD | IS mean | IS maxDD | folds mean/DD better | WF d mean | WF d maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| pb+cap+gb | 29.2k | 101.9k | 325.0k | -211.3k | 34.2k | 109.4k | 267.1k | 18.8k | 293.4k | 8/4 | 4.2k | -76.3k |
| pb+gb | 34.7k | 111.3k | 325.0k | -211.3k | 41.6k | 123.4k | 267.1k | 19.0k | 293.4k | 10/4 | 9.8k | -76.3k |
| pb+gb+wk8 | 30.1k | 113.7k | 370.0k | -137.1k | 41.6k | 123.4k | 267.1k | 13.9k | 407.3k | 10/1 | 5.1k | -31.3k |
| pb+cap+gb+wk8 | 25.0k | 104.5k | 401.3k | -137.1k | 34.2k | 109.4k | 267.1k | 13.7k | 407.3k | 0/0 | 0.0k | 0.0k |
| pb+gb+wk5 | 26.5k | 111.0k | 479.3k | -145.0k | 27.5k | 132.8k | 335.0k | 13.4k | 442.8k | 7/6 | 1.6k | 78.0k |
| pb+gb+wk8+wk5 | 26.5k | 111.0k | 479.3k | -145.0k | 27.5k | 132.8k | 335.0k | 13.4k | 442.8k | 7/6 | 1.6k | 78.0k |
| pb+cap+gb+wk8+wk5 | 22.1k | 101.2k | 479.3k | -145.0k | 20.1k | 118.9k | 335.0k | 13.1k | 442.8k | 4/6 | -2.8k | 78.0k |
| pb+cap+gb+wk5 | 22.1k | 101.2k | 479.3k | -145.0k | 20.1k | 118.9k | 335.0k | 13.1k | 442.8k | 4/6 | -2.8k | 78.0k |
| gb | 36.6k | 135.6k | 494.0k | -316.6k | 49.8k | 192.4k | 352.8k | 16.8k | 403.4k | 9/4 | 11.6k | 92.7k |
| cap+gb | 28.8k | 121.3k | 494.0k | -316.6k | 29.8k | 150.8k | 352.8k | 16.5k | 403.4k | 8/4 | 3.9k | 92.7k |
| gb+wk8 | 31.4k | 134.1k | 505.7k | -140.6k | 58.4k | 180.6k | 284.2k | 3.4k | 660.6k | 7/4 | 6.5k | 104.4k |
| cap+gb+wk8 | 24.0k | 119.9k | 505.7k | -140.6k | 38.4k | 136.9k | 284.2k | 3.1k | 660.6k | 6/4 | -1.0k | 104.4k |
| pb+cap+wk8 | 39.5k | 135.3k | 646.5k | -137.2k | 68.8k | 186.6k | 498.4k | 1.3k | 621.3k | 8/1 | 14.5k | 245.2k |
| pb+cap+wk5 | 36.9k | 127.8k | 663.3k | -97.6k | 71.2k | 175.0k | 352.8k | 0.0k | 498.2k | 7/1 | 11.9k | 262.0k |
| pb+cap+wk8+wk5 | 36.9k | 127.8k | 663.3k | -97.6k | 71.2k | 175.0k | 352.8k | 0.0k | 498.2k | 7/1 | 11.9k | 262.0k |
| pb+wk8+wk5 | 40.1k | 134.4k | 735.4k | -102.9k | 67.8k | 179.8k | 275.2k | -0.5k | 498.2k | 7/1 | 15.1k | 334.1k |
| pb+wk5 | 40.1k | 134.4k | 735.4k | -102.9k | 67.8k | 179.8k | 275.2k | -0.5k | 498.2k | 7/1 | 15.1k | 334.1k |
| pb+cap | 39.3k | 142.3k | 761.2k | -296.0k | 43.6k | 219.6k | 699.4k | 4.8k | 639.0k | 7/1 | 14.3k | 359.9k |
| pb+wk8 | 44.9k | 141.1k | 762.2k | -137.2k | 70.3k | 188.6k | 402.3k | 1.6k | 648.6k | 9/1 | 19.9k | 361.0k |
| cap+wk8+wk5 | 29.6k | 140.4k | 818.3k | -91.7k | 80.5k | 188.1k | 366.9k | -19.8k | 1363.6k | 5/1 | 4.7k | 417.0k |
| cap+wk5 | 29.6k | 140.4k | 818.3k | -91.7k | 80.5k | 188.1k | 366.9k | -19.8k | 1363.6k | 5/1 | 4.7k | 417.0k |
| wk5 | 34.1k | 150.4k | 818.3k | -91.7k | 76.4k | 193.3k | 256.5k | -19.8k | 1363.6k | 7/1 | 9.1k | 417.0k |
| wk8+wk5 | 34.1k | 150.4k | 818.3k | -91.7k | 76.4k | 193.3k | 256.5k | -19.8k | 1363.6k | 7/1 | 9.1k | 417.0k |
| cap+wk8 | 38.0k | 152.6k | 839.4k | -142.5k | 107.8k | 201.3k | 481.3k | -1.0k | 670.2k | 7/1 | 13.0k | 438.1k |
| wk8 | 41.7k | 161.9k | 885.6k | -142.5k | 106.6k | 208.7k | 369.0k | -0.5k | 670.2k | 8/1 | 16.8k | 484.3k |
| pb | 44.3k | 149.5k | 895.0k | -296.0k | 28.4k | 242.5k | 737.1k | 5.0k | 639.0k | 8/1 | 19.3k | 493.7k |
| cap | 43.1k | 160.4k | 903.6k | -458.8k | 71.4k | 256.4k | 772.4k | 4.3k | 754.2k | 8/2 | 18.1k | 502.3k |
| gb+wk5 | 28.2k | 127.5k | 935.8k | -89.3k | 33.5k | 179.3k | 223.5k | 0.4k | 866.0k | 5/5 | 3.2k | 534.6k |
| gb+wk8+wk5 | 28.2k | 127.5k | 935.8k | -89.3k | 33.5k | 179.3k | 223.5k | 0.4k | 866.0k | 5/5 | 3.2k | 534.6k |
| cap+gb+wk8+wk5 | 20.7k | 112.5k | 935.8k | -89.3k | 13.5k | 130.8k | 223.5k | -0.4k | 866.0k | 4/5 | -4.3k | 534.6k |
| cap+gb+wk5 | 20.7k | 112.5k | 935.8k | -89.3k | 13.5k | 130.8k | 223.5k | -0.4k | 866.0k | 4/5 | -4.3k | 534.6k |
| none | 46.9k | 171.8k | 1037.3k | -458.8k | 53.5k | 287.7k | 793.3k | 4.9k | 754.2k | 9/2 | 21.9k | 636.0k |

**What each lock earns: benchmark minus that lock (paired, exact), with 200 random-trigger placebo worlds** (placebo = the lock replaced by a random-time lock with the same in-situ fire frequency; rank = share of placebo worlds the REAL config beats; for maxDD rank = share of placebo worlds with a larger maxDD than the real config)

| lock removed | config without it | WF mean (delta vs live) | WF SD | WF maxDD (delta) | WF worst | L8W mean / maxDD | IS mean / maxDD | folds better: mean / maxDD | boot90 CI of weekly mean delta (without - live) | placebo WF mean (mean +- sd) / maxDD | real-vs-placebo rank mean / maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|
| pb | cap+gb+wk8 | 24.0k (-1.0k) | 119.9k | 505.7k (+104k) | -140.6k | 38.4k / 284.2k | 3.1k / 660.6k | 6 / 4 | [-8.0k, 6.3k], halves -2.2k/-0.0k | 22.1k +- 6.3k / 673.8k | 0.67 / 0.99 |
| cap | pb+gb+wk8 | 30.1k (+5.1k) | 113.7k | 370.0k (-31k) | -137.1k | 41.6k / 267.1k | 13.9k / 407.3k | 10 / 1 | [2.7k, 7.9k], halves 6.1k/4.3k | 29.9k +- 1.4k / 378.8k | 0.00 / 0.13 |
| gb | pb+cap+wk8 | 39.5k (+14.5k) | 135.3k | 646.5k (+245k) | -137.2k | 68.8k / 498.4k | 1.3k / 621.3k | 8 / 1 | [0.5k, 27.4k], halves 4.7k/22.6k | 33.5k +- 5.5k / 653.2k | 0.05 / 0.99 |
| wk8 | pb+cap+gb | 29.2k (+4.2k) | 101.9k | 325.0k (-76k) | -211.3k | 34.2k / 267.1k | 18.8k / 293.4k | 8 / 4 | [0.7k, 8.3k], halves 6.9k/2.0k | 27.4k +- 2.0k / 357.9k | 0.12 / 0.15 |
| cap+wk8 | pb+gb | 34.7k (+9.8k) | 111.3k | 325.0k (-76k) | -211.3k | 41.6k / 267.1k | 19.0k / 293.4k | 10 / 4 | [5.3k, 15.1k], halves 14.1k/6.2k | 31.9k +- 2.7k / 361.9k | 0.01 / 0.18 |

Week floor 5R ($84k) instead of 8R: WF 22.1k / SD 101.2k / maxDD 479.3k / worst -145.0k; L8W 20.1k / maxDD 335.0k - worse than 8R on every line.

**WEEK-FLOOR FINDING (confirmed on the exact engine).** Live minus the week floor (pb+cap+gb): WF 29.2k vs 25.0k (+4.2k/wk), maxDD 325.0k vs 401.3k (-76k), SD 101.9k vs 104.5k, worst week -211.3k vs -137.1k (the floor's one real job: it caps the worst week); IS 18.8k/293.4k vs 13.7k/407.3k; L8W identical (the floor did not fire in the last 8 weeks, so L8W cannot confirm or refute). Bootstrap 90% CI of the WF weekly mean delta [0.7k, 8.3k], halves 6.9k / 2.0k; better in 8 of 11 folds on mean and 4 of 11 on maxDD. Placebo (200 random-time week locks with the floor's in-situ fire frequency 0.135 per week): real floor ranks mean 0.125, maxDD 0.150 - the real floor fires at systematically worse times than random. Lock-flatten slip +1.0 pt on both configs: see sensitivity table. Weekly mean +4.2k and maxDD -76k WITHOUT the floor, bought at a worst week of -211.3k instead of -137.1k.

**Give-back variants and session-scoped give-back (subsets containing gb; WF mean / SD / maxDD / worst; L8W mean / maxDD; IS mean / maxDD)**

| config | variant | WF mean / SD / maxDD / worst | L8W mean / maxDD | IS mean / maxDD |
|---|---|---|---|---|
| pb+cap+gb | base arm2R keep50 | 29.2k / 101.9k / 325.0k / -211.3k | 34.2k / 267.1k | 18.8k / 293.4k |
| pb+cap+gb | gb2R_k67 | 25.2k / 96.0k / 381.4k / -208.1k | 54.2k / 246.8k | 14.7k / 473.6k |
| pb+cap+gb | gb3R_k50 | 34.4k / 123.9k / 522.4k / -289.8k | 56.3k / 420.6k | 14.8k / 526.5k |
| pb+cap+gb | gb3R_k67 | 28.7k / 116.0k / 522.4k / -278.3k | 40.5k / 403.1k | 19.3k / 421.1k |
| pb+cap+gb | gb_asia | 39.3k / 131.1k / 597.8k / -258.9k | 79.1k / 416.5k | 6.7k / 535.5k |
| pb+cap+gb | gb_rth | 30.8k / 120.7k / 525.8k / -247.6k | 32.3k / 414.9k | 15.5k / 372.0k |
| pb+cap+gb+wk8 | base arm2R keep50 | 25.0k / 104.5k / 401.3k / -137.1k | 34.2k / 267.1k | 13.7k / 407.3k |
| pb+cap+gb+wk8 | gb2R_k67 | 21.6k / 97.7k / 537.0k / -137.5k | 54.2k / 246.8k | 12.7k / 496.6k |
| pb+cap+gb+wk8 | gb3R_k50 | 31.4k / 123.0k / 685.8k / -137.5k | 56.3k / 420.6k | 7.9k / 632.0k |
| pb+cap+gb+wk8 | gb3R_k67 | 25.8k / 115.2k / 607.1k / -140.2k | 42.3k / 388.6k | 12.1k / 544.5k |
| pb+cap+gb+wk8 | gb_asia | 37.0k / 129.4k / 650.5k / -137.2k | 84.6k / 372.0k | 1.3k / 619.9k |
| pb+cap+gb+wk8 | gb_rth | 25.6k / 121.2k / 570.2k / -137.1k | 22.5k / 441.3k | 9.9k / 498.0k |
| gb | base arm2R keep50 | 36.6k / 135.6k / 494.0k / -316.6k | 49.8k / 352.8k | 16.8k / 403.4k |
| gb | gb2R_k67 | 26.2k / 118.6k / 575.6k / -290.5k | 72.9k / 339.7k | 13.7k / 559.5k |
| gb | gb3R_k50 | 40.0k / 157.9k / 881.2k / -452.7k | 64.6k / 530.6k | 14.1k / 641.1k |
| gb | gb3R_k67 | 30.0k / 145.1k / 887.0k / -441.1k | 60.7k / 501.6k | 19.1k / 535.8k |
| gb | gb_asia | 51.9k / 163.7k / 909.6k / -326.4k | 101.7k / 461.1k | 6.9k / 650.2k |
| gb | gb_rth | 34.0k / 153.7k / 642.8k / -397.6k | 33.4k / 500.6k | 13.6k / 427.5k |
| pb+gb | base arm2R keep50 | 34.7k / 111.3k / 325.0k / -211.3k | 41.6k / 267.1k | 19.0k / 293.4k |
| pb+gb | gb2R_k67 | 26.2k / 97.6k / 381.4k / -208.1k | 61.6k / 246.8k | 14.9k / 473.6k |
| pb+gb | gb3R_k50 | 40.6k / 133.4k / 522.4k / -289.8k | 59.0k / 420.6k | 15.1k / 526.5k |
| pb+gb | gb3R_k67 | 30.0k / 118.4k / 522.4k / -278.3k | 48.0k / 403.1k | 19.5k / 421.1k |
| pb+gb | gb_asia | 46.0k / 139.3k / 565.8k / -258.9k | 88.4k / 416.5k | 7.0k / 535.5k |
| pb+gb | gb_rth | 36.6k / 129.5k / 508.9k / -247.6k | 31.8k / 414.9k | 15.7k / 372.0k |

**Lock-flatten extra slip sensitivity (+0.5 / +1.0 pt adverse on every lock-flattened row)**

| config | extra | WF mean / maxDD | L8W mean / maxDD |
|---|---|---|---|
| pb+cap+gb+wk8 | +0.5 pt | 24.4k / 405.6k | 33.5k / 267.7k |
| pb+cap+gb+wk8 | +1.0 pt | 23.8k / 408.8k | 32.8k / 268.3k |
| pb+cap+gb | +0.5 pt | 28.5k / 325.7k | 33.5k / 267.7k |
| pb+cap+gb | +1.0 pt | 27.9k / 326.4k | 32.8k / 268.3k |
| cap+gb+wk8 | +0.5 pt | 23.4k / 506.6k | 37.6k / 285.2k |
| cap+gb+wk8 | +1.0 pt | 22.8k / 510.1k | 37.0k / 283.9k |
| pb+gb+wk8 | +0.5 pt | 29.5k / 371.5k | 40.9k / 267.7k |
| pb+gb+wk8 | +1.0 pt | 28.9k / 371.9k | 40.2k / 268.3k |
| gb | +0.5 pt | 35.9k / 498.0k | 49.0k / 353.5k |
| gb | +1.0 pt | 35.2k / 502.1k | 48.2k / 354.2k |
| pb+gb | +0.5 pt | 34.1k / 325.7k | 40.9k / 267.7k |
| pb+gb | +1.0 pt | 33.6k / 326.4k | 40.2k / 268.3k |
| none | +0.5 pt | 46.9k / 1037.3k | 53.5k / 793.3k |
| none | +1.0 pt | 46.9k / 1037.3k | 53.5k / 793.3k |
| pb+cap+gb+wk5 | +0.5 pt | 21.6k / 481.7k | 19.3k / 336.1k |
| pb+cap+gb+wk5 | +1.0 pt | 21.1k / 484.9k | 18.9k / 334.3k |
| pb+cap+gb+wk8 | +0 | 25.0k / 401.3k | 34.2k / 267.1k |
| pb+cap+gb | +0 | 29.2k / 325.0k | 34.2k / 267.1k |

**Best-of-F (White reality check over all 128 lock configurations, 4-week-block bootstrap, 2,000 draws; family of the W1 grid):** best by WF weekly mean delta: gb|gb_asia (+26.9k/wk), reality-check p = 0.012; best by WF maxDD improvement: pb+gb+wk5|gb2R_k67 (91k better), p = 0.999 (20-day-block bootstrap of the daily path, 1,000 draws). The F_P-adjusted line (0.05/3,363 = 1.5e-5) is not resolvable with these draws; a p-value above 0.05 means the best config is not distinguishable from the best of 128 equivalent configs by chance.

**Configs that beat the benchmark on WF net AND maxDD (and IS mean):** pb+gb (WF +9.8k/-76k, L8W +7.4k/+0k, IS +5.3k/-114k); pb+gb+wk8 (WF +5.1k/-31k, L8W +7.4k/+0k, IS +0.2k/+0k); pb+cap+gb (WF +4.2k/-76k, L8W +0.0k/+0k, IS +5.1k/-114k)


## W3 - parameter re-centring


Live (single|221) re-run: WF 25.0k/104.5k/401.3k, L8W 34.2k/267.1k, IS 13.7k/407.3k (benchmark WF 25.0k/401.3k).

**(a) Each single cell, WF weekly mean / maxDD ($k) by EMA level (rows ATR length, columns HMA slow)**

EMA 150

| ATR \ HMA slow | 44 | 50 | 55 | 60 | 66 |
|---|---|---|---|---|---|
| 96 | 26/521 | 35/411 | 37/396 | 38/408 | 34/402 |
| 108 | 28/522 | 34/354 | 36/397 | 35/447 | 33/425 |
| 120 | 26/499 | 31/336 | 35/384 | 34/442 | 32/444 |
| 132 | 23/496 | 31/353 | 34/394 | 32/423 | 31/446 |
| 144 | 24/516 | 31/357 | 32/397 | 34/424 | 31/441 |

EMA 200

| ATR \ HMA slow | 44 | 50 | 55 | 60 | 66 |
|---|---|---|---|---|---|
| 96 | 27/421 | 31/402 | 32/379 | 38/460 | 33/352 |
| 108 | 28/437 | 30/389 | 29/428 | 36/495 | 33/349 |
| 120 | 27/413 | 28/373 | 25/401* | 33/503 | 33/326 |
| 132 | 25/423 | 25/426 | 25/478 | 30/438 | 29/357 |
| 144 | 25/429 | 24/431 | 27/495 | 31/491 | 29/357 |

EMA 250

| ATR \ HMA slow | 44 | 50 | 55 | 60 | 66 |
|---|---|---|---|---|---|
| 96 | 27/670 | 29/574 | 30/598 | 38/699 | 37/530 |
| 108 | 27/679 | 29/561 | 30/628 | 40/674 | 35/620 |
| 120 | 23/656 | 28/605 | 26/554 | 38/652 | 33/496 |
| 132 | 22/561 | 25/579 | 27/546 | 33/594 | 31/523 |
| 144 | 26/503 | 26/510 | 28/491 | 37/611 | 32/468 |

Live cell rank in the grid by WF weekly mean: 67 of 75 (88% of cells beat it); by IS mean 22; grid mean WF 30.5k vs live 25.0k, grid mean IS 11.2k vs live 13.7k; IS-WF rank correlation across the 75 cells -0.31. EMA effect (mean WF by EMA): 150: 31.9k, 200: 29.3k, 250: 30.4k.

**Live cell rank in the grid per fold (read window weekly mean among the 75 single cells; 1 = best)**

| fold | read window | live mean | rank / 75 | grid median |
|---|---|---|---|---|
| 1 | 20240201..20240430 | -7.0k | 63 | 11.1k |
| 2 | 20240501..20240731 | 38.7k | 43 | 39.7k |
| 3 | 20240801..20241031 | -0.5k | 27 | -2.7k |
| 4 | 20241101..20250131 | 14.7k | 70 | 36.3k |
| 5 | 20250201..20250430 | 49.9k | 30 | 43.8k |
| 6 | 20250501..20250731 | 3.9k | 49 | 12.1k |
| 7 | 20250801..20251031 | 21.2k | 66 | 34.2k |
| 8 | 20251101..20260131 | 22.1k | 50 | 25.3k |
| 9 | 20260201..20260430 | 53.3k | 10 | 36.3k |
| 10 | 20260501..20260731 | 28.4k | 58 | 40.2k |
| 11 | 20260801..20261016 | 47.7k | 50 | 52.0k |

Live is in the top quartile (rank <= 19) in 1 of 11 folds; median rank 50.

**(b) Neighbourhood averages (nearest 10/20/40 pair cells, fractional lots summing to 14 per book) vs single cells and random same-size subsets (100 each)**

| set | n | WF mean (mean / sd / max) | WF SD (mean) | WF maxDD (mean / sd / min) | L8W mean | IS mean |
|---|---|---|---|---|---|---|
| single cells | 75 | 30.5k / 4.3k / 40.2k | 104.3k | 475.6k / 95.0k / 326.5k | 34.9k | 11.2k |
| 10-cell centred ensembles | 75 | 31.9k / 3.1k / 39.1k | 103.9k | 431.9k / 60.1k / 337.4k | 28.5k | 10.8k |
| random 10-cell subsets | 100 | 33.0k / 1.9k / 37.8k | 103.6k | 417.8k / 51.5k / 331.1k | 29.7k | 11.0k |
| 20-cell centred | 75 | 32.1k / 3.4k / 37.9k | 104.0k | 417.0k / 52.9k / 346.9k | 25.1k | 11.6k |
| random 20-cell | 100 | 33.2k / 2.0k / 38.8k | 102.8k | 407.2k / 43.6k / 340.0k | 29.0k | 11.0k |
| 40-cell centred | 75 | 33.7k / 3.0k / 39.6k | 103.3k | 385.3k / 38.4k / 323.5k | 28.6k | 11.3k |
| random 40-cell | 100 | 33.0k / 1.3k / 36.6k | 102.2k | 403.0k / 34.4k / 347.0k | 27.7k | 10.8k |

Live-centred 10-cell ensemble: WF 31.1k/105.2k/462.4k, L8W 35.7k/309.0k, IS 11.9k/527.0k; rank among 100 random same-size subsets: mean 0.16, maxDD (lower is better) 0.23; among the 75 centred ensembles: mean 0.35, maxDD 0.27.
Live-centred 20-cell ensemble: WF 32.8k/103.1k/359.7k, L8W 26.9k/339.3k, IS 14.2k/608.9k; rank among 100 random same-size subsets: mean 0.40, maxDD (lower is better) 0.90; among the 75 centred ensembles: mean 0.53, maxDD 0.87.
Live-centred 40-cell ensemble: WF 32.1k/101.2k/356.0k, L8W 29.8k/356.0k, IS 13.9k/598.3k; rank among 100 random same-size subsets: mean 0.21, maxDD (lower is better) 0.98; among the 75 centred ensembles: mean 0.37, maxDD 0.65.

**(c) Walk-forward-chosen centre per fold (best fit-window weekly Sharpe; read window concatenated)**

| rule | WF mean | WF SD | WF maxDD | WF worst | L8W mean | L8W maxDD | picks by fold |
|---|---|---|---|---|---|---|---|
| WF-chosen single | 25.7k | 102.9k | 629.3k | -141.7k | 41.5k | 243.0k | 222 200 040 040 140 010 030 132 132 241 132 |
| WF-chosen ens10 | 27.9k | 103.7k | 472.0k | -182.5k | 12.4k | 357.9k | 301 300 042 140 140 220 432 440 342 240 102 |
| WF-chosen ens20 | 31.5k | 102.2k | 402.9k | -138.4k | 26.6k | 364.8k | 301 301 001 240 240 230 432 240 332 142 142 |
| WF-chosen ens40 | 31.9k | 104.9k | 373.1k | -148.4k | 24.1k | 373.1k | 301 422 402 142 241 230 230 330 342 332 112 |

**(d) Robust centre = interior cell with the highest MINIMUM of the weekly Sharpe over its 8 in-plane neighbours (same EMA)**

| selection | centre (ATR/HMA/EMA) | min-neighbour Sharpe | centre single: WF mean/SD/maxDD | L8W mean/maxDD | IS mean/maxDD | beats live on net AND DD in WF | in L8W | centred 20-cell ensemble WF | L8W |
|---|---|---|---|---|---|---|---|---|---|
| IS only (honest) | 132/50/150 | 0.99 | 30.7k/105.1k/352.6k | 31.5k/319.9k | 16.7k/345.9k | True | False | 28.2k/410.2k | 10.3k/397.8k |
| IS+WF (contaminated) | 132/60/150 | 1.60 | 32.1k/105.9k/423.1k | 50.2k/258.4k | 9.3k/465.4k | False | True | 30.0k/352.2k | 37.4k/287.8k |

The honest (IS-selected) robust centre must be compared with the live cell, which was itself an IS pick: on the mapping screen the test above says whether it beats live out of sample; any cell that passes is replayed directly (section W6) before it is called.

Single cells beating the live cell on WF and L8W mean AND maxDD (mapping): 3 of 75: 120/66/200, 132/66/200, 144/66/200


**W3 direct-replay test of the robust centres** (pair = ST cell + HM cell sharing the EMA; replayed trades; 14/14/14, live locks; benchmark RB = live pair through the same replay policy):

| cell | points | WF mean / SD / maxDD | L8W mean / maxDD | IS mean / maxDD | beats RB on WF mean & maxDD | on L8W |
|---|---|---|---|---|---|---|
| live (RB) | direct | 28.4k / 106.2k / 371.4k | 45.8k / 218.6k | 13.7k / 407.5k | - | - |
| live (RB) | P9exact | 25.0k / 104.5k / 401.6k | 34.2k / 267.1k | 13.7k / 407.5k | - | - |
| HONEST robust centre 132/50/150 (selected on IS only) | direct | 30.5k / 105.6k / 384.6k | 29.0k / 297.8k | 13.4k / 379.0k | False | False |
| HONEST robust centre 132/50/150 (selected on IS only) | mapping | 29.5k / 106.7k / 314.3k | 31.3k / 314.3k | 17.6k / 395.7k | True | False |
| cluster centre 120/66/200 (post-hoc, 3 mapping winners) | direct | 29.3k / 103.1k / 399.8k | 46.1k / 211.8k | 4.2k / 643.7k | False | True |
| cluster centre 120/66/200 (post-hoc, 3 mapping winners) | mapping | 34.3k / 101.7k / 279.8k | 48.6k / 240.9k | 6.4k / 644.2k | True | True |

Verdict W3: on the mapping screen the honest centre beat live on WF net and DD; on DIRECT replay it does not (maxDD +13k worse than RB, L8W mean 29.0k vs 45.8k): the sign of the DD improvement flips -> discarded (W6). The cluster centre also fails (WF maxDD 400k vs 371k; IS 4.2k vs 13.7k). The live cell is a poor local choice in WF (rank 67 of 75, top quartile in 1 of 11 folds) but it was IS rank 22: the grid is flat and noisy (IS-WF rank correlation -0.31), so no re-centring survives replay. This is a parameter change that did NOT pass, so nothing here is live-eligible.

## W2 - ATR20-scaled brackets with the chosen locks

144 mapping cells (horizon {2h, session, daily} x k {0.8, 1.0, 1.25} x floor {4,8} x R$ {8k,10k} x locks {none, pb+gb in vol-unit R, pb+cap+gb vol-unit, live}); WF mean by horizon (mean over cells): 2h 28.2k..34.9k, session 8.0k..14.5k, daily 1.3k..5.7k: only the 2-hour horizon is viable. Cells that beat the benchmark on mapping (WF and L8W mean and maxDD): ATR20_T2H_k0.8|R8000|fl4|live, ATR20_T2H_k1.0|R8000|fl4|live, ATR20_T2H_k1.0|R8000|fl8|live, ATR20_T2H_k1.0|R10000|fl4|live, ATR20_T2H_k1.0|R10000|fl8|live. Mapping vs DIRECT replay for each (live locks):

| cell | mapping WF mean / SD / maxDD | direct-replay WF mean / SD / maxDD | direct L8W mean / maxDD | direct IS mean | DD sign vs RB (371k) |
|---|---|---|---|---|---|
| ATR20_T2H_k1.0 / R8000 / fl4 | 32.5k / 78.5k / 309.9k | 26.8k / 78.3k / 558.8k | 87.3k / 88.5k | -6.3k | FLIPS (worse than RB) |
| ATR20_T2H_k1.0 / R8000 / fl8 | 33.8k / 89.5k / 362.2k | 29.9k / 92.4k / 566.1k | 98.7k / 87.8k | -5.9k | FLIPS (worse than RB) |
| ATR20_T2H_k1.0 / R10000 / fl4 | 35.1k / 86.4k / 388.5k | 29.6k / 86.9k / 545.9k | 70.9k / 170.7k | -1.9k | FLIPS (worse than RB) |
| ATR20_T2H_k1.0 / R10000 / fl8 | 34.8k / 94.0k / 375.6k | 28.7k / 97.5k / 538.8k | 65.9k / 174.1k | -1.9k | FLIPS (worse than RB) |
| ATR20_T2H_k0.8 / R8000 / fl4 | 28.3k / 81.0k / 392.9k | NOT REPLAYED (sibling k=1.0 flips) | - | - | unverified |

Verdict W2: every viable cell at 14/14/14 session sizes flips the sign of the DD improvement on direct replay (WF maxDD 539-566k vs RB 371k vs P9 401k), although weekly SD stays lower (78-97k vs 106k) and L8W is far better (66-99k, maxDD 88-174k) and IS is negative (EM market execution on tight brackets). The vol-unit lock variants lose the mean (WF 2-15k); combined with London/NY size cuts (W5, 14/8/10) the ATR brackets reach the lowest direct WF maxDD of any option (273-278k vs RB 371k, L8W maxDD 131-143k) - but their WF mean is 5-9k below RB and their IS is -8k to -13k with maxDD 0.76-0.95M, so they fail the mean criterion and the IS window.

## W4 - session size


| lots A/L/N | locks | WF mean / SD / maxDD / worst | L8W mean / maxDD | IS mean / maxDD | WF d mean | WF d maxDD | L8W d mean | L8W d maxDD |
|---|---|---|---|---|---|---|---|---|
| 14/10/10 | pb+gb | 34.2k / 106.9k / 317.1k / -188.8k | 58.2k / 206.1k | 12.9k / 324.6k | +9.2k | -84k | +24.0k | -61k |
| 14/10/10 | pb+cap+gb | 31.6k / 102.0k / 317.1k / -188.8k | 52.3k / 206.1k | 12.9k / 324.6k | +6.6k | -84k | +18.1k | -61k |
| 14/8/10 | pb+gb | 31.4k / 104.0k / 317.8k / -186.3k | 38.1k / 317.8k | 8.6k / 387.5k | +6.5k | -84k | +3.9k | +51k |
| 14/14/14 | pb+cap+gb | 29.2k / 101.9k / 325.0k / -211.3k | 34.2k / 267.1k | 18.8k / 293.4k | +4.2k | -76k | +0.0k | +0k |
| 14/14/14 | pb+gb | 34.7k / 111.3k / 325.0k / -211.3k | 41.6k / 267.1k | 19.0k / 293.4k | +9.8k | -76k | +7.4k | +0k |
| 14/8/10 | pb+cap+gb | 29.2k / 100.4k / 326.8k / -186.3k | 32.6k / 317.8k | 8.6k / 387.5k | +4.2k | -75k | -1.6k | +51k |
| 14/10/8 | pb+gb | 32.8k / 102.6k / 329.6k / -192.3k | 55.7k / 204.4k | 12.6k / 323.8k | +7.8k | -72k | +21.5k | -63k |
| 14/8/8 | pb+gb | 30.4k / 98.4k / 332.4k / -182.9k | 40.3k / 281.9k | 10.5k / 390.2k | +5.4k | -69k | +6.1k | +15k |
| 14/8/6 | pb+cap+gb | 28.4k / 91.7k / 342.5k / -181.7k | 37.4k / 254.9k | 8.3k / 382.8k | +3.4k | -59k | +3.2k | -12k |
| 14/8/6 | pb+gb | 29.3k / 93.5k / 343.4k / -181.7k | 41.1k / 254.9k | 8.3k / 382.8k | +4.3k | -58k | +6.9k | -12k |
| 14/10/8 | pb+cap+gb | 30.8k / 98.2k / 344.0k / -192.3k | 51.1k / 204.4k | 12.6k / 323.8k | +5.8k | -57k | +16.9k | -63k |
| 14/8/8 | pb+cap+gb | 28.9k / 95.7k / 344.4k / -182.9k | 35.8k / 281.9k | 10.5k / 390.2k | +3.9k | -57k | +1.6k | +15k |
| 14/10/6 | pb+gb | 31.7k / 98.4k / 355.6k / -188.3k | 55.6k / 191.1k | 11.3k / 329.0k | +6.8k | -46k | +21.4k | -76k |
| 14/10/6 | pb+cap+gb | 30.3k / 95.3k / 356.5k / -188.3k | 51.9k / 191.1k | 11.3k / 329.0k | +5.4k | -45k | +17.7k | -76k |
| 14/8/10 | live | 26.7k / 102.8k / 359.7k / -136.1k | 32.6k / 317.8k | 6.7k / 415.4k | +1.7k | -42k | -1.6k | +51k |
| 14/14/10 | pb+gb | 32.6k / 109.5k / 368.2k / -221.7k | 40.0k / 272.9k | 16.8k / 312.0k | +7.6k | -33k | +5.8k | +6k |

With the LIVE locks the best session-size cells: 14/8/10: WF 26.7k/359.7k, L8W 32.6k/317.8k; 14/8/6: WF 26.0k/389.6k, L8W 37.4k/254.9k; 14/14/14: WF 25.0k/401.3k, L8W 34.2k/267.1k; 14/8/8: WF 26.3k/423.9k, L8W 35.8k/281.9k. Session sizing is a lock-interplay effect: the gains are mostly the same as removing cap/week locks (W1); London/NY at 10 lots with pb+gb gives WF +9.2k / maxDD -84k, L8W +24.0k / -61k, IS -0.7k / -83k.

500-world nulls on the W4/W1 finalists (exact engine): pblive|capoff|wk12|gb1|N2 @ 14/10/10: placebo-lock maxDD rank 1.00, random-subset down-size mean rank 0.98 / maxDD rank 1.00; pblive|capoff|wk12|gb1|N0 @ 14/10/10: placebo-lock maxDD rank 1.00, random-subset down-size mean rank 0.96 / maxDD rank 1.00; pblive|capsoft8|wk12|gb1|N2 @ 14/8/10: placebo-lock maxDD rank 1.00, random-subset down-size mean rank 1.00 / maxDD rank 1.00; pboff|capoff|wkoff|gb0|N0 @ 14/14/14: placebo-lock maxDD rank 0.99, random-subset down-size mean rank 0.00 / maxDD rank 0.00; pblive|capoff|wkoff|gb0|N0 @ 14/14/14: placebo-lock maxDD rank 1.00, random-subset down-size mean rank 0.00 / maxDD rank 0.00. The London/NY-specific down-sizing beats random down-sizing of the same share of trades (rank >= 0.96) - so the session choice is not just "smaller is better"; but 14/10/10 and 14/10/8 ranks are one-look and the gain is again drawdown, not income.

## W5 - joint cell (W1 locks x W3 centre x W4 session size x W2 bracket), DIRECT-replay points (60 cells; RB and P9 comparisons)

Benchmark RB (direct, live locks, 14/14/14): WF 28.4k / 106.2k / 371.4k; L8W 45.8k / 218.6k; IS 13.7k / 407.5k. 2 of 60 cells beat RB on WF AND L8W mean and maxDD; 8 on WF alone.

| option | locks | lots | WF mean / SD / maxDD | L8W mean / maxDD | IS mean / maxDD | d WF mean / d maxDD | both windows |
|---|---|---|---|---|---|---|---|
| ATR_R8000_f4 | BEST5 | 14/8/10 | 19.7k / 62.6k / 273.4k | 54.1k / 132.1k | -13.0k / 941.1k | -8.7k / -98k | False |
| ATR_R8000_f4 | live | 14/8/10 | 23.0k / 65.1k / 277.8k | 58.8k / 142.8k | -11.6k / 865.2k | -5.4k / -94k | False |
| ATR_R8000_f4 | pb+gb | 14/8/10 | 23.2k / 64.7k / 277.8k | 58.8k / 142.8k | -12.2k / 898.8k | -5.2k / -94k | False |
| ATR_R8000_f4 | pb+gb | 14/10/10 | 22.8k / 67.6k / 295.5k | 65.7k / 142.8k | -10.8k / 856.1k | -5.6k / -76k | False |
| ATR_R8000_f4 | live | 14/10/8 | 20.9k / 63.2k / 303.8k | 63.7k / 130.7k | -8.0k / 756.0k | -7.5k / -68k | False |
| ATR_R8000_f4 | pb+gb | 14/10/8 | 21.1k / 62.7k / 303.8k | 63.7k / 130.7k | -9.2k / 815.5k | -7.3k / -68k | False |
| ATR_R8000_f4 | live | 14/10/10 | 22.3k / 68.5k / 308.2k | 61.5k / 158.4k | -9.6k / 794.2k | -6.0k / -63k | False |
| live60 | BEST5 | 14/10/8 | 23.6k / 90.4k / 318.3k | 59.9k / 160.9k | 10.4k / 303.6k | -4.7k / -53k | False |
| ATR_R8000_f4 | BEST5 | 14/10/10 | 19.1k / 65.6k / 324.0k | 57.6k / 136.5k | -11.1k / 892.9k | -9.3k / -47k | False |
| live60 | BEST5 | 14/8/10 | 27.7k / 94.4k / 324.7k | 54.8k / 264.5k | 11.7k / 314.3k | -0.7k / -47k | False |
| ATR_R10000_f4 | live | 14/8/10 | 28.3k / 70.9k / 327.9k | 61.5k / 116.4k | -12.2k / 913.0k | -0.0k / -43k | False |
| ATR_R10000_f4 | pb+gb | 14/8/10 | 28.3k / 71.7k / 327.9k | 62.4k / 116.4k | -13.0k / 952.2k | -0.1k / -43k | False |
| ATR_R8000_f4 | BEST5 | 14/10/8 | 17.8k / 61.5k / 329.1k | 57.2k / 124.4k | -10.4k / 866.3k | -10.6k / -42k | False |
| live60 | pb+gb | 14/10/8 | 32.0k / 102.9k / 330.6k | 60.6k / 169.9k | 11.6k / 334.3k | +3.6k / -41k | True |

Cells that beat RB on both windows (mean and maxDD): live60/pb+gb/14/10/10 (WF 33.2k/332.1k, L8W 63.3k/167.8k, IS 12.0k/332.2k); live60/pb+gb/14/10/8 (WF 32.0k/330.6k, L8W 60.6k/169.9k, IS 11.6k/334.3k).

500-world nulls on the D1 top-20 plus the three exact best cells (placebo locks / random-subset down-sizing): see REPORT_DS2_FIRM_V5.md section (1) and the table below.

| option | lock set | lots | WF mean / maxDD | placebo-lock rank mean / maxDD | down-size-null rank mean / maxDD |
|---|---|---|---|---|---|
| ATR_R10000_f4 | pblive|capsoft8|wk8|gb0|N0 | 14/8/10 | 28.5k / 327.9k | 1.00 / 0.71 | 0.95 / 1.00 |
| ATR_R10000_f4 | pblive|capsoft8|wk8|gb0|N2 | 14/8/10 | 28.5k / 327.9k | 1.00 / 0.71 | 0.95 / 1.00 |
| ATR_R10000_f4 | pblive|capoff|wk8|gb0|N0 | 14/8/10 | 28.5k / 327.9k | 0.99 / 0.73 | 0.95 / 1.00 |
| ATR_R10000_f4 | pblive|capoff|wk8|gb0|N2 | 14/8/10 | 28.5k / 327.9k | 0.99 / 0.73 | 0.95 / 1.00 |
| ATR_R10000_f4 | pblive|capsoft8|wk8|gb0|N3 | 14/8/10 | 28.5k / 327.9k | 1.00 / 0.72 | 0.95 / 1.00 |
| ATR_R10000_f4 | pblive|capoff|wk8|gb0|N3 | 14/8/10 | 28.5k / 327.9k | 0.99 / 0.73 | 0.95 / 1.00 |
| ATR_R10000_f8 | pblive|caphard|wk8|gb0|N3 | 14/8/10 | 29.1k / 324.7k | 0.99 / 0.94 | 0.98 / 1.00 |
| ATR_R10000_f8 | pblive|caphard|wk8|gb0|N0 | 14/8/10 | 29.1k / 324.7k | 0.99 / 0.94 | 0.98 / 1.00 |
| ATR_R10000_f8 | pblive|caphard|wk8|gb0|N2 | 14/8/10 | 29.1k / 324.7k | 0.99 / 0.94 | 0.98 / 1.00 |
| ATR_R10000_f8 | pblive|capsoft8|wk8|gb0|N3 | 14/8/10 | 29.2k / 324.7k | 1.00 / 0.95 | 0.99 / 1.00 |
| ATR_R10000_f8 | pblive|capoff|wk8|gb0|N3 | 14/8/10 | 29.2k / 324.7k | 0.99 / 0.93 | 0.99 / 1.00 |
| ATR_R10000_f8 | pblive|capsoft8|wk8|gb0|N0 | 14/8/10 | 29.2k / 324.7k | 1.00 / 0.95 | 0.98 / 1.00 |
| ATR_R10000_f8 | pblive|capoff|wk8|gb0|N0 | 14/8/10 | 29.2k / 324.7k | 0.99 / 0.93 | 0.98 / 1.00 |
| ATR_R10000_f8 | pblive|capoff|wk8|gb0|N2 | 14/8/10 | 29.2k / 324.7k | 0.99 / 0.93 | 0.98 / 1.00 |
| ATR_R10000_f8 | pblive|capsoft8|wk8|gb0|N2 | 14/8/10 | 29.2k / 324.7k | 1.00 / 0.95 | 0.98 / 1.00 |
| ATR_R10000_f8 | pblive|caphard|wkoff|gb0|N2 | 14/8/10 | 29.0k / 330.8k | 0.99 / 0.93 | 0.97 / 1.00 |
| ATR_R10000_f8 | pblive|caphard|wk12|gb0|N2 | 14/8/10 | 29.0k / 330.8k | 1.00 / 0.94 | 0.97 / 1.00 |
| ATR_R10000_f8 | pblive|caphard|wkoff|gb0|N0 | 14/8/10 | 29.0k / 330.8k | 0.99 / 0.93 | 0.97 / 1.00 |
| ATR_R10000_f8 | pblive|caphard|wk12|gb0|N0 | 14/8/10 | 29.0k / 330.8k | 1.00 / 0.94 | 0.97 / 1.00 |
| ATR_R10000_f8 | pblive|caphard|wk12|gb0|N3 | 14/8/10 | 29.0k / 330.8k | 1.00 / 0.94 | 0.97 / 1.00 |
| live60_P9 | pblive|capoff|wk12|gb1|N2 | 14/10/10 | 25.5k / 287.3k | 0.42 / 1.00 | 0.98 / 1.00 |
| live60_P9 | pblive|capoff|wkoff|gb0|N0 | 14/14/14 | 34.7k / 325.0k | 0.83 / 1.00 | 0.00 / 0.00 |
| live60_P9 | pblive|capoff|wk12|gb1|N0 | 14/10/10 | 25.1k / 298.9k | 0.39 / 1.00 | 0.96 / 1.00 |

Best-of-F: the joint family is the 23,040-cell D1 screen (V5); the White reality check on the weekly-mean deltas over 17,280 of those cells is dominated by lock-removal cells (mean +10k/wk); on maxDD the improvement of the best cells (-110k) is NOT separable from the best of the family under a 20-day block bootstrap, so the F-count for any maxDD claim is the family size, not 1.

## W6 - replay bias for the finalists (mapping vs direct replay; discard if the DD improvement changes sign)

| finalist | mapping (or P9 exact) WF mean / maxDD | direct-replay WF mean / maxDD | mapping DD vs its benchmark (P9 401k) | direct DD vs RB (371k) | flips? |
|---|---|---|---|---|---|
| ATR_R8000_f4 / BEST5 / 14/8/10 | 22.9k / 235.2k | 19.7k / 273.4k | -166k | -98k | holds |
| ATR_R8000_f4 / live / 14/8/10 | 27.4k / 225.3k | 23.0k / 277.8k | -176k | -94k | holds |
| ATR_R8000_f4 / pb+gb / 14/8/10 | 27.8k / 225.3k | 23.2k / 277.8k | -176k | -94k | holds |
| ATR_R8000_f4 / pb+gb / 14/10/10 | 27.4k / 249.1k | 22.8k / 295.5k | -152k | -76k | holds |
| ATR_R8000_f4 / live / 14/10/10 | 26.9k / 266.3k | 22.3k / 308.2k | -135k | -63k | holds |
| ATR_R8000_f4 / BEST5 / 14/10/10 | 22.1k / 250.5k | 19.1k / 324.0k | -151k | -47k | holds |
| live60 / BEST5 / 14/8/10 | 27.2k / 308.8k | 27.7k / 324.7k | -93k | -47k | holds |
| ATR_R10000_f4 / live / 14/8/10 | 31.3k / 279.8k | 28.3k / 327.9k | -121k | -43k | holds |
| ATR_R10000_f4 / pb+gb / 14/8/10 | 31.3k / 279.8k | 28.3k / 327.9k | -121k | -43k | holds |
| live60 / BEST5 / 14/10/10 | 25.5k / 287.3k | 25.5k / 331.7k | -114k | -40k | holds |
| live60 / pb+gb / 14/10/10 | 33.1k / 320.1k | 33.2k / 332.1k | -81k | -39k | holds |
| live60 / pb+gb / 14/14/14 | 34.7k / 325.0k | 37.2k / 347.7k | -76k | -24k | holds |
| ATR_R10000_f4 / pb+gb / 14/10/10 | 32.1k / 313.6k | 27.5k / 353.7k | -88k | -18k | holds |
| ATR_R10000_f4 / BEST5 / 14/8/10 | 25.5k / 283.5k | 24.2k / 357.1k | -118k | -14k | holds |
| centreHonest / live / 14/10/10 | 30.3k / 375.5k | 28.6k / 363.2k | -26k | -8k | holds |
| centreHonest / BEST5 / 14/8/10 | 31.7k / 386.7k | 30.9k / 363.5k | -15k | -8k | holds |
| live60 / pb+gb / 14/8/10 | 30.3k / 322.6k | 29.7k / 366.7k | -79k | -5k | holds |
| centreHonest / BEST5 / 14/10/10 | 29.7k / 378.5k | 28.1k / 368.5k | -23k | -3k | holds |
| centreHonest / pb+gb / 14/8/10 | 33.8k / 400.9k | 35.2k / 369.7k | -0k | -2k | holds |
| centreCluster / pb+gb / 14/10/10 | 34.9k / 352.4k | 31.6k / 372.5k | -49k | +1k | FLIP - discard |

1 of the 20 listed finalists flip the sign of the WF maxDD improvement between the mapping/P9-exact screen and direct replay. 'holds' means only that the WF DD improvement keeps its sign - the ATR-bracket cells hold on DD but fail on WF mean (below RB) and IS (negative); the W3 centres flip or fail L8W; the fixed-60 live-signal cells (exact engine) are robust to the execution policy: pb+gb at 14/14/14 is WF 34.7k / 325k under P9 points and 37.2k / 348k under the replay policy (benchmarks 25.0k / 401k and 28.4k / 371k): +9.8k / -76k and +8.8k / -24k.

## Verdict (v4)
(1) W1: the combined cap and the week floor do not earn their keep in WF (exact engine, 200 placebo worlds: the week floor fires at worse-than-random times; removing both: WF +9.8k/wk, maxDD -76k, IS +5.3k/-114k, L8W +7.4k / equal maxDD; bootstrap CI [+5.3k, +15.1k]); the price is the worst week (-211k vs -137k). (2) W3 centres and W2 ATR brackets fail direct replay. (3) W4/W5: the best surviving joint cell is a fixed-60 lock/size change (BEST5 in V5), not a re-centring or a bracket change. (4) F_P: 3,358 + 5 (W1..W5) = 3,363.
