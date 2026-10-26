# REPORT DS2-FIRM v3 (trackFIRM, 2026-10-22) - marginal lots, locks, ensemble, down-only sizing, refine, vol-target/Kelly, replay reconciliation; research only

Prereg: l2vast/PREREG_DS2_FIRM_V3.md (frozen before scoring; sha in autopilot/DECISIONS.md) on top of PREREG_DS2_FIRM_V2.md + addenda. Benchmark = corrected P9, 14/14, $4.84 fees, windows 18:00-18:05 + 15:00-16:54, live locks (per-book -2R/+5R, combined 8R, give-back 2R/keep 50% on the 1-s clock, week floor 8R), WF 24,975/wk SD 104.5k maxDD 401k worst -137k; L8W 34.2k / 109.4k / 267.1k; IS 13.7k / 95.9k / 407.3k. All figures $/wk at 14/14 scale. **Exactness:** V3 and the V4/V1(a) cells use the exact P9 execution points of the 60-pt benchmark rows (no mapping error); cells with a non-60 bracket (V1 b-d, V2, V5, V6) regenerate trades exactly on the 1-s tape but map the P9 execution layer from direct L2 replay deltas (abs error ~0.25 pts/trade, about +-$3k/wk, and re-seeding the mapping moves a cell's WF mean by about +-3k); V7 is the direct replay of one such cell. "Path table" = the exact per-signal 1-s regeneration (gen_rows); no separate MFE/MAE table is needed.

## V3 MARGINAL-LOT CURVE (first)


**A. live locks, S113 cost (credit<14)**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 2.7k/28.2k/197.5k | 16.0k | 48.8k | 259.1k | -125.2k | 2.37 | 82 |  | 22.6k | 79.6k | 209.7k | -87.6k |
| 6 | 3.5k/44.3k/323.7k | 21.4k | 70.3k | 378.9k | -134.5k | 2.19 | 72 | +2.67k | 22.7k | 113.9k | 327.3k | -134.4k |
| 8 | 4.0k/56.5k/411.7k | 28.4k | 86.3k | 375.6k | -136.8k | 2.38 | 61 | +3.54k | 42.0k | 111.7k | 274.6k | -122.5k |
| 10 | 11.7k/70.0k/360.7k | 25.3k | 103.1k | 381.7k | -148.6k | 1.77 | 51 | -1.59k | 34.4k | 100.7k | 259.4k | -92.0k |
| 12 | 14.8k/82.3k/360.5k | 26.5k | 109.1k | 372.7k | -138.4k | 1.75 | 43 | +0.65k | 39.3k | 82.9k | 204.6k | -95.8k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.79k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.2k/101.3k/434.3k | 21.6k | 101.3k | 367.8k | -136.7k | 1.54 | 30 | -1.68k | 18.9k | 125.2k | 325.3k | -135.1k |
| 20 | 12.0k/115.7k/377.8k | 24.6k | 106.6k | 524.8k | -146.1k | 1.66 | 25 | +0.75k | 31.4k | 122.1k | 266.0k | -134.0k |

**B. live locks, S113 cost, NO credit below 14**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 1.0k/28.2k/215.5k | 12.3k | 48.8k | 274.4k | -134.7k | 1.83 | 82 |  | 18.3k | 79.2k | 220.7k | -91.7k |
| 6 | 1.6k/44.2k/340.5k | 17.4k | 69.9k | 387.8k | -134.6k | 1.80 | 72 | +2.55k | 19.4k | 112.5k | 335.0k | -134.6k |
| 8 | 2.2k/56.4k/426.7k | 25.3k | 85.4k | 404.4k | -135.6k | 2.14 | 61 | +3.94k | 40.1k | 112.5k | 282.5k | -120.7k |
| 10 | 10.4k/69.9k/371.8k | 23.3k | 103.2k | 427.1k | -149.5k | 1.63 | 51 | -1.00k | 34.0k | 99.4k | 264.4k | -89.4k |
| 12 | 13.8k/82.3k/366.2k | 25.2k | 108.9k | 372.8k | -139.4k | 1.67 | 43 | +0.95k | 37.9k | 82.6k | 207.5k | -96.4k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.11k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.2k/101.3k/434.3k | 21.6k | 101.3k | 367.8k | -136.7k | 1.54 | 30 | -1.68k | 18.9k | 125.2k | 325.3k | -135.1k |
| 20 | 12.0k/115.7k/377.8k | 24.6k | 106.6k | 524.8k | -146.1k | 1.66 | 25 | +0.75k | 31.4k | 122.1k | 266.0k | -134.0k |

**C. live locks, size cost OFF**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 1.0k/28.2k/215.5k | 12.3k | 48.8k | 274.4k | -134.7k | 1.83 | 82 |  | 18.3k | 79.2k | 220.7k | -91.7k |
| 6 | 1.6k/44.2k/340.5k | 17.4k | 69.9k | 387.8k | -134.6k | 1.80 | 72 | +2.55k | 19.4k | 112.5k | 335.0k | -134.6k |
| 8 | 2.2k/56.4k/426.7k | 25.3k | 85.4k | 404.4k | -135.6k | 2.14 | 61 | +3.94k | 40.1k | 112.5k | 282.5k | -120.7k |
| 10 | 10.4k/69.9k/371.8k | 23.3k | 103.2k | 427.1k | -149.5k | 1.63 | 51 | -1.00k | 34.0k | 99.4k | 264.4k | -89.4k |
| 12 | 13.8k/82.3k/366.2k | 25.2k | 108.9k | 372.8k | -139.4k | 1.67 | 43 | +0.95k | 37.9k | 82.6k | 207.5k | -96.4k |
| 14 | 13.7k/95.9k/407.3k | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 36 | -0.11k | 34.2k | 109.4k | 267.1k | -98.9k |
| 16 | 15.8k/101.3k/427.3k | 21.6k | 100.7k | 363.4k | -137.5k | 1.54 | 30 | -1.70k | 19.5k | 125.6k | 324.8k | -135.5k |
| 20 | 13.0k/115.1k/375.7k | 27.2k | 108.3k | 506.3k | -145.3k | 1.81 | 25 | +1.40k | 30.4k | 118.9k | 262.4k | -134.8k |

**D. LOCKS OFF (pure signal + bracket + size), S113 cost**

| lots | IS mean/SD/maxDD | WF mean | WF SD | WF maxDD | WF worst wk | WF Sharpe | WF trades/wk | marginal WF $/wk per lot (vs prev size) | L8W mean | L8W SD | L8W maxDD | L8W worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 4 | 3.2k/29.0k/197.5k | 17.0k | 49.1k | 279.8k | -123.8k | 2.49 | 84 |  | 19.9k | 82.4k | 213.5k | -102.3k |
| 6 | 4.2k/43.5k/301.7k | 24.4k | 73.7k | 424.6k | -187.9k | 2.39 | 84 | +3.71k | 28.5k | 123.5k | 324.2k | -154.9k |
| 8 | 4.9k/58.0k/409.4k | 31.1k | 98.2k | 572.8k | -253.4k | 2.28 | 84 | +3.35k | 36.1k | 164.6k | 437.5k | -208.4k |
| 10 | 5.3k/72.5k/520.7k | 37.1k | 122.7k | 724.3k | -320.4k | 2.18 | 84 | +2.99k | 42.8k | 205.6k | 553.5k | -262.9k |
| 12 | 5.2k/87.1k/635.6k | 42.3k | 147.2k | 879.2k | -388.9k | 2.07 | 84 | +2.63k | 48.6k | 246.7k | 672.1k | -318.3k |
| 14 | 4.9k/101.7k/754.2k | 46.9k | 171.8k | 1037.3k | -458.8k | 1.97 | 84 | +2.27k | 53.5k | 287.7k | 793.3k | -374.6k |
| 16 | 4.1k/116.2k/876.2k | 50.7k | 196.3k | 1236.2k | -530.2k | 1.86 | 84 | +1.91k | 57.5k | 328.7k | 917.2k | -431.9k |
| 20 | 1.6k/145.4k/1131.2k | 56.1k | 245.3k | 1753.3k | -677.4k | 1.65 | 84 | +1.36k | 62.7k | 410.5k | 1172.9k | -549.3k |

**E. Per entry session (uniform L both books, live locks): weekly realised P&L of the trades entered in each session / trades per week**

| lots | WF ASIA | WF LONDON | WF NY | L8W ASIA | L8W LONDON | L8W NY | IS ASIA | IS LONDON | IS NY |
|---|---|---|---|---|---|---|---|---|---|
| 4 | 6.7k (21) | 2.5k (23) | 6.8k (37) | 12.0k (29) | 8.6k (36) | 2.0k (39) | 1.4k (9) | 2.7k (10) | -1.3k (22) |
| 6 | 10.4k (21) | 3.2k (21) | 7.8k (30) | 20.4k (27) | 15.3k (31) | -13.0k (26) | 2.0k (9) | 3.4k (10) | -1.8k (21) |
| 8 | 14.5k (20) | 5.5k (18) | 8.4k (23) | 30.5k (28) | 15.4k (27) | -3.9k (18) | 2.4k (9) | 4.6k (10) | -3.0k (20) |
| 10 | 14.9k (19) | 3.0k (15) | 7.3k (16) | 23.2k (26) | 24.2k (21) | -12.9k (13) | 3.7k (9) | 5.0k (9) | 3.0k (16) |
| 12 | 16.0k (18) | 4.6k (13) | 5.9k (12) | 15.4k (25) | 44.6k (18) | -20.8k (8) | 5.0k (9) | 9.0k (9) | 0.8k (14) |
| 14 | 18.2k (17) | 2.5k (10) | 4.3k (8) | 30.0k (23) | 11.1k (13) | -6.9k (5) | 2.4k (9) | 10.3k (8) | 1.0k (10) |
| 16 | 14.6k (16) | 5.0k (8) | 2.1k (6) | 13.9k (19) | 16.0k (7) | -11.0k (3) | 1.0k (9) | 11.3k (7) | 2.9k (9) |
| 20 | 15.2k (15) | 6.8k (6) | 2.5k (4) | 14.3k (18) | 20.7k (6) | -3.6k (2) | -1.7k (8) | 8.9k (6) | 4.7k (7) |

**F. Size varied in ONE session only (other sessions 14 lots): WF weekly mean / maxDD (L8W mean)**

| lots in session | ASIA | LONDON | NY |
|---|---|---|---|
| 4 | 10.9k / 739.1k (13.4k) | 26.1k / 397.4k (15.0k) | 25.1k / 468.4k (37.1k) |
| 6 | 16.9k / 725.8k (66.3k) | 27.1k / 402.1k (16.9k) | 26.3k / 460.8k (36.9k) |
| 8 | 21.5k / 573.8k (61.0k) | 26.0k / 316.1k (33.9k) | 26.6k / 484.8k (36.1k) |
| 10 | 27.0k / 504.6k (63.6k) | 28.0k / 377.5k (50.1k) | 27.5k / 497.5k (33.7k) |
| 12 | 28.1k / 491.5k (56.6k) | 27.6k / 410.7k (49.0k) | 29.0k / 409.3k (32.7k) |
| 14 | 25.0k / 401.3k (34.2k) | 25.0k / 401.3k (34.2k) | 25.0k / 401.3k (34.2k) |
| 16 | 28.0k / 393.0k (8.4k) | 26.5k / 439.7k (35.1k) | 24.4k / 433.8k (33.0k) |
| 20 | 25.0k / 390.5k (11.7k) | 25.6k / 604.3k (43.2k) | 26.2k / 444.9k (39.6k) |

**V3 reading.** (1) With the live locks the weekly mean is flat from 6 to 20 lots (WF 21-28k, best at 8 lots 28.4k, benchmark 14 lots 25.0k, 20 lots 24.6k); the marginal lot is worth +2.7k/+3.5k/week at 4->8 lots and ~0 (-1.7k..+0.7k, within noise) above 8; SD rises 49k -> 107k and maxDD 259k -> 525k, so Sharpe falls 2.4 -> 1.7. The reason is mechanical: fixed-dollar locks fire after fewer trades as size rises (trades/week 82 -> 25) so extra lots mostly shorten the trading day. (2) Locks OFF the mean is nearly linear (marginal +2.3k/lot at 14, declining as the S113 surface bites) but SD 172k, maxDD 1.04M, worst week -459k at 14 lots: the locks, not the signal, define the live risk. (3) By session: ASIA improves with size up to ~14 lots (WF 6.7k @4 -> 18.2k @14, flat after), LONDON is flat/noisy (2.5-6.8k), NY is the one that does NOT pay marginal lots (WF 8.4k @8 -> 4.3k @14 -> 2.5k @20; trades/wk 23 -> 4): the NY entries are being crowded out by locks fired earlier in the day. Varying size in one session only (table F) tells the same: ASIA 10-14 lots is best (28.1k @12), NY and LONDON are insensitive. (4) The no-credit variant (B) and cost-off variant (C) change the 4-8 lot rows by 2-5k but not the shape; S113 cost at 16-20 lots costs 0-2.6k/wk. (5) IS differs: IS mean rises with lots up to 16 (2.7k @4 -> 15.2k @16) while WF peaks at 8: IS and WF disagree on the optimum, so there is no stable maximum - lots 8-14 are statistically indistinguishable in income and only maxDD/SD argue for fewer lots.

## V1 LOCKS IN VOL UNITS, LOCKS OFF, ONE AT A TIME


Lock configs: OFF = pure signal+bracket+size; each lock alone; pb = per-book day -2R/+5R; cap = combined 8R; gb = give-back arm 2R keep 50% (tick clock); week = 8R floor (5R = $84k). usd = thresholds in live dollars (R=$16.8k at 14/14); vol = thresholds in the group's first-entry dollar risk (lots x bracket x $20; identical to usd for (a)).

**(a) live 60 pt / 14 lots (exact P9)**

| locks | unit | WF mean | WF SD | WF maxDD | WF worst | L8W mean | L8W SD | L8W maxDD | day locks fired |
|---|---|---|---|---|---|---|---|---|---|
| OFF | usd | 46.9k | 171.8k | 1037.3k | -458.8k | 53.5k | 287.7k | 793.3k | 0 |
| pb_only | usd | 44.3k | 149.5k | 895.0k | -296.0k | 28.4k | 242.5k | 737.1k | 0 |
| pb_only | vol | 44.3k | 149.5k | 895.0k | -296.0k | 28.4k | 242.5k | 737.1k | 0 |
| cap_only | usd | 43.1k | 160.4k | 903.6k | -458.8k | 71.4k | 256.4k | 772.4k | 87 |
| cap_only | vol | 43.1k | 160.4k | 903.6k | -458.8k | 71.4k | 256.4k | 772.4k | 87 |
| giveback_only | usd | 36.6k | 135.6k | 494.0k | -316.6k | 49.8k | 192.4k | 352.8k | 509 |
| giveback_only | vol | 36.6k | 135.6k | 494.0k | -316.6k | 49.8k | 192.4k | 352.8k | 509 |
| week_only | usd | 41.7k | 161.9k | 885.6k | -142.5k | 106.6k | 208.7k | 369.0k | 53 |
| week_only | vol | 41.7k | 161.9k | 885.6k | -142.5k | 106.6k | 208.7k | 369.0k | 53 |
| pb+cap | usd | 39.3k | 142.3k | 761.2k | -296.0k | 43.6k | 219.6k | 699.4k | 72 |
| pb+cap | vol | 39.3k | 142.3k | 761.2k | -296.0k | 43.6k | 219.6k | 699.4k | 72 |
| pb+cap+gb | usd | 29.2k | 101.9k | 325.0k | -211.3k | 34.2k | 109.4k | 267.1k | 490 |
| pb+cap+gb | vol | 29.2k | 101.9k | 325.0k | -211.3k | 34.2k | 109.4k | 267.1k | 490 |
| full_live | usd | 25.0k | 104.5k | 401.3k | -137.1k | 34.2k | 109.4k | 267.1k | 490 |
| full_live | vol | 25.0k | 104.5k | 401.3k | -137.1k | 34.2k | 109.4k | 267.1k | 490 |
| full_week5R | usd | 22.1k | 101.2k | 479.3k | -145.0k | 20.1k | 118.9k | 335.0k | 490 |
| full_week5R | vol | 22.1k | 101.2k | 479.3k | -145.0k | 20.1k | 118.9k | 335.0k | 490 |

**(b) RIDGE/T2H k1.0 clamped bracket, 14 lots**

| locks | unit | WF mean | WF SD | WF maxDD | WF worst | L8W mean | L8W SD | L8W maxDD | day locks fired |
|---|---|---|---|---|---|---|---|---|---|
| OFF | usd | 24.8k | 227.6k | 1283.4k | -586.8k | 21.1k | 409.2k | 982.2k | 0 |
| pb_only | usd | 34.9k | 183.2k | 1004.4k | -430.5k | 7.6k | 291.2k | 797.6k | 0 |
| pb_only | vol | 25.1k | 165.3k | 901.0k | -373.3k | 45.9k | 276.3k | 690.8k | 0 |
| cap_only | usd | 19.9k | 197.1k | 1414.0k | -576.1k | 0.2k | 293.9k | 897.2k | 128 |
| cap_only | vol | 14.6k | 182.9k | 1641.3k | -597.8k | 26.5k | 275.7k | 803.8k | 345 |
| giveback_only | usd | 21.1k | 146.5k | 828.6k | -455.4k | 58.9k | 85.6k | 234.6k | 538 |
| giveback_only | vol | 18.2k | 123.4k | 595.4k | -463.1k | 63.6k | 71.0k | 182.9k | 741 |
| week_only | usd | 23.2k | 193.4k | 977.4k | -142.4k | 85.2k | 324.8k | 513.1k | 70 |
| week_only | vol | 31.4k | 185.3k | 702.0k | -300.4k | 90.0k | 319.6k | 418.1k | 122 |
| pb+cap | usd | 32.5k | 166.0k | 917.0k | -358.8k | 14.8k | 223.5k | 774.5k | 101 |
| pb+cap | vol | 16.5k | 145.1k | 1010.6k | -350.2k | 50.1k | 214.6k | 665.5k | 240 |
| pb+cap+gb | usd | 23.0k | 114.1k | 719.3k | -322.2k | 32.1k | 130.4k | 403.3k | 526 |
| pb+cap+gb | vol | 10.9k | 85.3k | 591.7k | -236.6k | 20.4k | 97.9k | 294.9k | 659 |
| full_live | usd | 19.7k | 111.4k | 669.9k | -141.4k | 40.3k | 110.5k | 288.4k | 526 |
| full_live | vol | 8.4k | 84.5k | 721.5k | -273.1k | 22.8k | 93.8k | 270.3k | 659 |
| full_week5R | usd | 16.9k | 104.7k | 569.3k | -101.2k | 50.8k | 92.5k | 204.8k | 526 |
| full_week5R | vol | 9.4k | 77.6k | 707.7k | -188.8k | 27.5k | 80.4k | 212.5k | 659 |

**(c) ATR20/T2H k1.0 unclamped, R$10k, cap14, floor4**

| locks | unit | WF mean | WF SD | WF maxDD | WF worst | L8W mean | L8W SD | L8W maxDD | day locks fired |
|---|---|---|---|---|---|---|---|---|---|
| OFF | usd | 37.5k | 101.1k | 440.0k | -276.5k | 54.6k | 137.3k | 406.1k | 0 |
| pb_only | usd | 37.9k | 94.2k | 452.2k | -185.3k | 47.2k | 131.4k | 417.2k | 0 |
| pb_only | vol | 25.7k | 78.7k | 411.4k | -152.1k | 22.9k | 111.9k | 409.5k | 0 |
| cap_only | usd | 37.7k | 100.6k | 440.0k | -276.5k | 49.7k | 132.8k | 406.1k | 11 |
| cap_only | vol | 30.2k | 94.4k | 460.6k | -276.5k | 58.6k | 134.4k | 406.1k | 234 |
| giveback_only | usd | 35.2k | 93.4k | 364.3k | -226.4k | 67.0k | 118.1k | 241.4k | 316 |
| giveback_only | vol | 22.4k | 75.9k | 363.9k | -200.7k | 59.8k | 96.4k | 153.3k | 701 |
| week_only | usd | 36.0k | 101.2k | 435.5k | -138.5k | 58.1k | 130.8k | 347.6k | 22 |
| week_only | vol | 33.3k | 93.1k | 359.7k | -84.5k | 69.0k | 114.2k | 260.3k | 80 |
| pb+cap | usd | 38.1k | 94.0k | 452.2k | -185.3k | 44.7k | 129.6k | 417.2k | 9 |
| pb+cap | vol | 24.2k | 74.8k | 424.8k | -152.1k | 29.7k | 111.4k | 409.5k | 170 |
| pb+cap+gb | usd | 35.3k | 86.7k | 376.0k | -183.1k | 53.9k | 105.8k | 263.3k | 321 |
| pb+cap+gb | vol | 15.7k | 57.5k | 222.7k | -137.1k | 13.4k | 80.3k | 211.6k | 619 |
| full_live | usd | 35.1k | 86.4k | 388.5k | -139.0k | 54.0k | 105.5k | 255.9k | 321 |
| full_live | vol | 16.0k | 55.2k | 197.1k | -83.3k | 13.3k | 75.6k | 180.3k | 619 |
| full_week5R | usd | 33.5k | 85.1k | 336.2k | -88.1k | 53.2k | 104.9k | 237.1k | 321 |
| full_week5R | vol | 11.6k | 53.2k | 277.8k | -52.6k | 14.7k | 66.2k | 135.1k | 619 |

**(d) FIRM RIDGE/T2H k1.0, R$16.8k, cap28**

| locks | unit | WF mean | WF SD | WF maxDD | WF worst | L8W mean | L8W SD | L8W maxDD | day locks fired |
|---|---|---|---|---|---|---|---|---|---|
| OFF | usd | 26.9k | 177.4k | 957.8k | -361.7k | 53.1k | 259.3k | 628.3k | 0 |
| pb_only | usd | 29.1k | 160.2k | 845.0k | -315.3k | 30.1k | 224.4k | 620.2k | 0 |
| pb_only | vol | 27.3k | 155.3k | 823.5k | -306.6k | 24.0k | 230.0k | 648.9k | 0 |
| cap_only | usd | 22.8k | 167.3k | 958.2k | -361.7k | 48.7k | 230.5k | 628.3k | 81 |
| cap_only | vol | 21.9k | 166.3k | 954.5k | -361.7k | 48.3k | 230.2k | 628.3k | 102 |
| giveback_only | usd | 7.9k | 127.5k | 1142.7k | -332.0k | 40.5k | 114.9k | 357.7k | 572 |
| giveback_only | vol | 8.8k | 125.2k | 1164.4k | -332.0k | 42.4k | 115.2k | 357.7k | 609 |
| week_only | usd | 23.0k | 167.0k | 841.2k | -138.4k | 75.8k | 231.3k | 425.1k | 68 |
| week_only | vol | 23.7k | 165.5k | 820.0k | -138.6k | 76.3k | 230.7k | 422.0k | 76 |
| pb+cap | usd | 25.0k | 154.1k | 889.1k | -315.3k | 32.7k | 210.4k | 620.2k | 75 |
| pb+cap | vol | 23.0k | 148.4k | 854.5k | -306.6k | 25.6k | 214.1k | 648.9k | 91 |
| pb+cap+gb | usd | 6.7k | 106.3k | 961.6k | -281.6k | 13.3k | 119.6k | 331.2k | 546 |
| pb+cap+gb | vol | 7.0k | 99.6k | 887.2k | -278.9k | 3.5k | 122.6k | 357.5k | 557 |
| full_live | usd | 5.5k | 102.1k | 852.9k | -137.1k | 18.6k | 103.4k | 256.0k | 546 |
| full_live | vol | 4.9k | 95.0k | 650.8k | -141.3k | 8.4k | 108.5k | 272.7k | 557 |
| full_week5R | usd | 3.8k | 95.1k | 813.0k | -94.5k | 24.1k | 91.3k | 179.6k | 546 |
| full_week5R | vol | 4.0k | 87.6k | 632.1k | -92.4k | 15.7k | 93.4k | 194.4k | 557 |

**Pure vol-normalisation effect (locks OFF), scaled to the live pair's locks-OFF WF mean 46.9k:**

| cell (locks OFF) | WF mean | WF SD | WF maxDD | WF worst | at equal mean (vs live locks-OFF): SD | maxDD | worst | L8W SD at same m |
|---|---|---|---|---|---|---|---|---|
| (a) live 60 pt / 14 lots (exact P9) | 46.9k | 171.8k | 1037.3k | -458.8k | **171.8k** | 1037.3k | -458.8k | 287.7k |
| (b) RIDGE/T2H k1.0 clamped bracket, 14 lots | 24.8k | 227.6k | 1283.4k | -586.8k | **430.1k** | 2425.6k | -1109.1k | 773.4k |
| (c) ATR20/T2H k1.0 unclamped, R$10k, cap14, floor4 | 37.5k | 101.1k | 440.0k | -276.5k | **126.5k** | 550.6k | -345.9k | 171.7k |
| (d) FIRM RIDGE/T2H k1.0, R$16.8k, cap28 | 26.9k | 177.4k | 957.8k | -361.7k | **308.7k** | 1666.7k | -629.5k | 451.2k |

**Which lock truncates, and what it costs in mean (live 60/14, WF):** +OFF: SD 171.8k, maxDD 1037.3k, mean 46.9k; +pb_only: SD 149.5k, maxDD 895.0k, mean 44.3k; +cap_only: SD 160.4k, maxDD 903.6k, mean 43.1k; +giveback_only: SD 135.6k, maxDD 494.0k, mean 36.6k; +week_only: SD 161.9k, maxDD 885.6k, mean 41.7k; +pb+cap+gb: SD 101.9k, maxDD 325.0k, mean 29.2k; +full_live: SD 104.5k, maxDD 401.3k, mean 25.0k

**k x R$ map, ATR20_un (T2H), locks OFF: WF mean/SD/maxDD ($k), cap 28**

| k | R$10k | R$12k | R$14k | R$16.8k | R$21k | R$25k |
|---|---|---|---|---|---|---|
| 0.6 | 0/142/1687 | -5/167/2304 | -9/190/2863 | -13/218/3496 | -18/252/4231 | -21/277/4922 |
| 0.8 | 27/120/805 | 27/142/1001 | 28/163/1169 | 27/190/1362 | 28/224/1605 | 29/250/1774 |
| 1.0 | 37/107/450 | 41/126/559 | 45/145/673 | 50/171/830 | 55/208/1071 | 59/238/1248 |
| 1.25 | 23/99/618 | 25/117/746 | 28/135/891 | 31/160/1072 | 35/195/1397 | 37/225/1660 |
| 1.5 | 14/91/760 | 15/107/877 | 17/124/1017 | 18/147/1234 | 21/179/1497 | 21/210/1886 |
| 2.0 | 10/93/723 | 13/104/771 | 14/118/833 | 16/138/939 | 18/171/1144 | 21/201/1330 |
| 2.5 | 11/92/752 | 12/100/756 | 14/109/753 | 16/125/837 | 19/151/979 | 22/177/1125 |

**k x R$ map, ATR20_un (T2H), all locks in vol-unit R: WF mean/SD/maxDD ($k), cap 28**

| k | R$10k | R$12k | R$14k | R$16.8k | R$21k | R$25k |
|---|---|---|---|---|---|---|
| 0.6 | -7/58/1229 | -8/64/1527 | -8/70/1538 | -12/73/1943 | -11/78/1851 | -10/79/1782 |
| 0.8 | 2/65/747 | 1/75/868 | 0/84/898 | -1/94/1070 | -0/102/1120 | -0/106/1244 |
| 1.0 | 17/63/297 | 17/74/467 | 20/84/522 | 21/95/627 | 23/109/624 | 23/117/615 |
| 1.25 | 12/65/432 | 12/76/507 | 13/88/613 | 14/103/813 | 15/122/999 | 14/136/1355 |
| 1.5 | 8/60/399 | 10/72/461 | 10/82/623 | 11/97/765 | 11/118/1041 | 10/136/1405 |
| 2.0 | 6/62/416 | 9/73/421 | 10/84/520 | 12/100/646 | 12/125/973 | 13/148/1328 |
| 2.5 | 12/65/377 | 14/74/377 | 16/85/416 | 16/100/500 | 18/122/622 | 21/145/758 |

**k x R$ map, ATR20_un (T2H), live dollar locks: WF mean/SD/maxDD ($k), cap 28**

| k | R$10k | R$12k | R$14k | R$16.8k | R$21k | R$25k |
|---|---|---|---|---|---|---|
| 0.6 | -4/99/1489 | -9/101/1937 | -7/106/1724 | -12/105/2148 | -12/107/2181 | -12/108/2229 |
| 0.8 | 21/100/665 | 16/108/861 | 12/113/1015 | 1/113/1301 | -4/114/1655 | -1/118/1485 |
| 1.0 | 35/90/339 | 34/99/370 | 32/104/476 | 25/105/517 | 21/110/646 | 19/112/767 |
| 1.25 | 22/82/510 | 20/89/651 | 21/97/658 | 15/105/798 | 12/109/916 | 10/117/1225 |
| 1.5 | 13/82/638 | 17/86/587 | 14/95/541 | 11/98/673 | 8/101/725 | 4/109/994 |
| 2.0 | 10/83/676 | 11/90/678 | 12/97/529 | 10/102/752 | 11/108/735 | 8/108/828 |
| 2.5 | 14/79/488 | 17/85/476 | 16/92/523 | 16/99/474 | 21/104/569 | 20/113/584 |

**k x R$ map, RIDGE_cl (T2H), locks OFF: WF mean/SD/maxDD ($k), cap 28**

| k | R$10k | R$12k | R$14k | R$16.8k | R$21k | R$25k |
|---|---|---|---|---|---|---|
| 0.6 | 17/131/764 | 15/158/991 | 10/184/1397 | 9/209/1689 | 6/242/2044 | 6/267/2188 |
| 0.8 | 21/119/686 | 21/141/848 | 20/165/1058 | 20/193/1311 | 23/228/1577 | 25/260/1715 |
| 1.0 | 22/109/507 | 24/129/616 | 26/151/753 | 27/177/958 | 30/214/1173 | 34/243/1344 |
| 1.25 | 11/104/797 | 11/120/963 | 12/142/1203 | 11/168/1592 | 11/203/2090 | 12/235/2532 |
| 1.5 | 16/92/514 | 19/103/584 | 21/123/713 | 23/147/834 | 27/178/1029 | 30/206/1234 |
| 2.0 | 6/77/486 | 8/84/494 | 8/100/630 | 9/121/757 | 11/146/953 | 11/169/1128 |
| 2.5 | 3/74/653 | 3/79/686 | 4/96/838 | 4/115/1012 | 4/138/1233 | 4/159/1424 |

**k x R$ map, RIDGE_cl (T2H), all locks in vol-unit R: WF mean/SD/maxDD ($k), cap 28**

| k | R$10k | R$12k | R$14k | R$16.8k | R$21k | R$25k |
|---|---|---|---|---|---|---|
| 0.6 | 2/66/498 | -1/79/662 | -5/91/1183 | -5/100/1220 | -3/104/1207 | -2/108/1316 |
| 0.8 | 8/70/495 | 8/83/618 | 6/98/878 | 7/110/1032 | 8/118/1017 | 10/128/1011 |
| 1.0 | 9/60/348 | 7/71/489 | 9/83/552 | 5/95/651 | 7/108/852 | 8/117/861 |
| 1.25 | 9/64/411 | 9/77/567 | 9/88/580 | 8/101/795 | 7/121/978 | 9/137/1033 |
| 1.5 | 13/59/313 | 13/71/369 | 13/81/373 | 16/97/460 | 17/120/571 | 18/137/691 |
| 2.0 | 8/59/360 | 9/70/331 | 10/81/410 | 12/98/501 | 16/121/606 | 17/143/692 |
| 2.5 | 7/58/480 | 9/65/575 | 10/77/663 | 10/91/813 | 13/110/914 | 13/134/1328 |

**k x R$ map, RIDGE_cl (T2H), live dollar locks: WF mean/SD/maxDD ($k), cap 28**

| k | R$10k | R$12k | R$14k | R$16.8k | R$21k | R$25k |
|---|---|---|---|---|---|---|
| 0.6 | 10/107/883 | 11/110/924 | -2/115/1544 | -4/116/1620 | 1/118/1318 | 3/121/1338 |
| 0.8 | 16/103/608 | 17/109/672 | 9/117/1192 | 5/123/1329 | 5/119/1442 | 7/126/1474 |
| 1.0 | 15/92/548 | 16/99/578 | 11/99/650 | 6/102/853 | 5/110/1012 | 2/117/1001 |
| 1.25 | 11/88/743 | 14/94/698 | 14/101/612 | 7/104/937 | 8/108/825 | 3/113/1139 |
| 1.5 | 19/81/431 | 19/86/474 | 18/94/506 | 15/98/469 | 17/114/612 | 12/112/843 |
| 2.0 | 9/70/400 | 11/77/384 | 11/90/511 | 14/97/529 | 14/108/498 | 15/114/594 |
| 2.5 | 7/66/494 | 10/71/507 | 12/83/557 | 14/87/707 | 13/96/590 | 10/109/838 |


**V1 reading.** The truncation is done by the **give-back arm**: alone it takes the live pair's SD 172k -> 136k and maxDD 1.04M -> 494k for 10k/wk of mean; with the per-book and combined caps it reaches SD 102k / maxDD 325k / mean 29k. The week floor 8R adds nothing to SD, costs 4.2k/wk of mean and raises maxDD (325k -> 401k) on top of the others (it only trims the worst week, -211k -> -137k). The vol-normalisation effect is invisible under the dollar locks and visible with locks OFF: ATR20-scaled brackets with constant-dollar sizing (R$10k cap 14) give SD 101k / maxDD 440k at WF 37.5k vs the live pair 172k / 1.04M at 46.9k - **at equal mean SD 126.5k (-26%), maxDD 551k (-47%), worst week -346k (-25%)** (path-table mapping; the locks-OFF version was not replayed, and V7 shows the mapping understates the ATR20 family maxDD by 115-245k with locks ON, so read the maxDD figure as an upper bound on the gain). So vol-normalisation does lower the pure-signal SD; but the same cells under the live dollar locks land at SD 86k/maxDD 389k/mean 35k (the locks then do the work for both). RIDGE/T2H clamped brackets and the firm cell do not show the effect (equal-mean SD 430k / 309k): the benefit is specific to ATR20-scaled brackets. Putting every rule in the trade's own vol-unit R makes locks tighter in dollars for small-R trades and cuts SD to 55k but also the mean to 16k (ATR20 cell) - no improvement in SD per mean.

## V4 ENSEMBLE


| cell | WF mean | WF SD | WF maxDD | WF worst | WF Sharpe | L8W mean | L8W SD | L8W maxDD | IS mean | IS maxDD |
|---|---|---|---|---|---|---|---|---|---|---|
| BENCHMARK (live cell, exact) | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 34.2k | 109.4k | 267.1k | 13.7k | 407.3k |
| live cell re-run | 25.0k | 104.5k | 401.3k | -137.1k | 1.72 | 34.2k | 109.4k | 267.1k | 13.7k | 407.3k |
| 10-cell ensemble around live | 34.1k | 102.5k | 348.3k | -137.4k | 2.40 | 43.4k | 90.8k | 279.5k | 6.7k | 599.4k |
| 20-cell ensemble around live | 35.9k | 104.4k | 350.9k | -138.1k | 2.48 | 43.5k | 99.2k | 289.7k | 6.5k | 586.6k |
| 40-cell ensemble around live | 32.5k | 105.6k | 501.9k | -136.9k | 2.22 | 30.0k | 101.6k | 333.9k | 8.1k | 506.1k |

**Distribution over the 25 centres (idx 2..6 x 2..6 of the 9x9 grids) and 75 random ST/HM centre combinations:**

| set | n | WF mean (mean / sd / min / max) | WF SD (mean) | WF maxDD (mean / sd) | L8W mean (mean) | IS mean (mean) |
|---|---|---|---|---|---|---|
| single pairs (ST c, HM c) | 25 | 28.6k / 4.7k / 20.9k / 40.2k | 103.4k | 497.7k / 92.0k | 34.3k | 3.4k |
| 10-cell ensembles | 25 | 31.7k / 3.0k / 26.1k / 38.9k | 103.7k | 473.6k / 94.3k | 42.0k | 2.6k |
| 20-cell ensembles | 25 | 32.3k / 2.2k / 29.4k / 37.2k | 104.5k | 466.7k / 76.5k | 42.6k | 2.8k |
| 40-cell ensembles | 25 | 32.3k / 1.6k / 29.1k / 34.5k | 105.3k | 495.4k / 81.4k | 44.3k | 3.9k |
| 20-cell random ST/HM centre mixes | 75 | 31.6k / 3.5k / 21.7k / 38.0k | 104.9k | 495.3k / 79.2k | 41.9k | 2.8k |

**Neighbourhood map: where is the live cell weak?** WF weekly mean ($k) of ONE cell varied with the other book at its live setting (live marked *; IS in brackets for the row/col totals). ST: rows ATR length, columns multiplier; HM: rows fast length a, columns slow length b.

*ST (ATR x mult)* WF mean / maxDD (k)

| | 1.2 | 1.4 | 1.6 | 1.8 | 2.0 | 2.2 | 2.4 | 2.6 | 2.8 |
|---|---|---|---|---|---|---|---|---|---|
| 72 | 27/596 | 30/467 | 35/446 | 35/527 | 30/453 | 30/476 | 26/434 | 25/430 | 28/339 |
| 84 | 29/541 | 29/495 | 36/441 | 30/542 | 31/585 | 30/415 | 21/463 | 27/401 | 22/431 |
| 96 | 29/543 | 30/489 | 36/473 | 31/532 | 32/379 | 29/369 | 22/467 | 28/433 | 23/483 |
| 108 | 27/570 | 31/540 | 36/474 | 31/490 | 29/428 | 29/563 | 21/498 | 24/500 | 23/544 |
| 120 | 27/569 | 27/564 | 32/470 | 26/520 | 25/401* | 29/475 | 22/477 | 23/439 | 27/523 |
| 132 | 27/610 | 29/686 | 33/470 | 22/667 | 25/478 | 28/403 | 23/466 | 24/463 | 27/594 |
| 144 | 28/498 | 29/683 | 34/470 | 25/502 | 27/495 | 25/428 | 26/447 | 26/541 | 27/629 |
| 156 | 26/554 | 31/690 | 31/480 | 29/476 | 26/497 | 29/451 | 27/457 | 26/526 | 28/568 |
| 168 | 26/540 | 32/582 | 33/441 | 32/476 | 28/442 | 30/425 | 29/448 | 24/692 | 28/600 |

*HM (a x b)* WF mean / maxDD (k)

| | 33 | 39 | 44 | 50 | 55 | 61 | 66 | 72 | 77 |
|---|---|---|---|---|---|---|---|---|---|
| 12 | 28/594 | 29/457 | 33/477 | 29/511 | 36/573 | 36/354 | 36/554 | 29/700 | 25/604 |
| 14 | 25/581 | 27/463 | 27/439 | 30/471 | 34/459 | 35/381 | 33/366 | 28/727 | 24/535 |
| 16 | 25/493 | 31/567 | 25/413 | 27/440 | 30/450 | 33/395 | 30/416 | 31/379 | 27/546 |
| 18 | 29/558 | 28/560 | 19/574 | 26/460 | 25/611 | 28/525 | 37/323 | 29/482 | 32/445 |
| 20 | 25/737 | 20/634 | 27/413 | 28/373 | 25/401* | 32/465 | 33/326 | 33/453 | 23/471 |
| 22 | 21/625 | 25/614 | 28/442 | 26/474 | 31/382 | 29/510 | 27/498 | 33/477 | 29/451 |
| 24 | 22/748 | 25/465 | 36/425 | 29/465 | 34/383 | 30/490 | 28/590 | 29/520 | 33/422 |
| 26 | 21/534 | 31/413 | 35/535 | 23/457 | 31/355 | 24/532 | 24/581 | 24/567 | 24/712 |
| 28 | 27/506 | 29/494 | 26/422 | 25/445 | 30/523 | 27/482 | 20/784 | 18/712 | 18/633 |

ST: mean over the 3x3 neighbourhood of the live cell (WF) 27.1k vs live 25.0k; best 3x3-smoothed cell: (0,3); share of grid cells with WF mean above live: 0.80; IS mean live 13.7k vs grid mean 3.7k

HM: mean over the 3x3 neighbourhood of the live cell (WF) 27.8k vs live 25.0k; best 3x3-smoothed cell: (0,5); share of grid cells with WF mean above live: 0.77; IS mean live 13.7k vs grid mean 9.5k

**Robust plateau centre** (argmax of the 3x3-smoothed mean of IS and WF weekly Sharpe over the 25 centres): centre idx (5, 3) = ST ATR 132 mult 1.8 / HM 22 x 50 (the live pair is idx (4,4)); single pair there WF 21.5k/101.3k/585.9k L8W 24.4k; 20-cell ensemble there WF 34.7k/100.6k/417.1k L8W 20.5k/341.1k. NB this centre is chosen with IS+WF (selection-contaminated); the walk-forward choice below is the honest version.

**Walk-forward-chosen neighbourhood** (per 12/3/3 fold: the centre with the best fit-window weekly Sharpe among the 25; its read-window P&L concatenated; locks state not carried across folds, so approximate):

| rule | WF mean | WF SD | WF maxDD | WF worst | L8W mean | L8W maxDD | centre picks by fold |
|---|---|---|---|---|---|---|---|
| WF-chosen ens20 | 32.3k | 98.9k | 571.3k | -136.7k | 20.7k | 307.5k | 64 33 33 35 35 35 35 63 63 63 63 |
| WF-chosen single | 33.2k | 98.1k | 543.8k | -136.4k | 25.1k | 211.8k | 33 33 53 45 45 62 62 62 62 62 22 |
| WF-chosen ens10 | 29.3k | 98.6k | 514.5k | -136.5k | 38.0k | 289.1k | 64 43 33 44 35 25 35 25 62 54 65 |
| WF-chosen ens40 | 31.1k | 101.0k | 489.5k | -138.1k | 15.5k | 408.1k | 53 32 32 34 32 25 25 62 63 64 63 |

**Fold stability: 20-cell live-centred ensemble minus live cell, per 12/3/3 read window (weekly mean delta / maxDD delta)**

| fold | read window | live mean | ens20 mean | delta | live maxDD | ens20 maxDD | delta |
|---|---|---|---|---|---|---|---|
| 1 | 20240201..20240430 | -7.0k | -2.4k | 4.6k | 261.3k | 255.8k | -5.5k |
| 2 | 20240501..20240731 | 38.7k | 63.4k | 24.8k | 171.0k | 159.9k | -11.1k |
| 3 | 20240801..20241031 | -0.5k | 3.6k | 4.0k | 362.5k | 263.4k | -99.0k |
| 4 | 20241101..20250131 | 14.7k | 25.5k | 10.7k | 308.3k | 310.0k | 1.7k |
| 5 | 20250201..20250430 | 49.9k | 58.1k | 8.1k | 134.1k | 160.2k | 26.1k |
| 6 | 20250501..20250731 | 3.9k | 2.7k | -1.2k | 249.6k | 292.7k | 43.1k |
| 7 | 20250801..20251031 | 21.2k | 37.6k | 16.4k | 193.8k | 145.9k | -47.9k |
| 8 | 20251101..20260131 | 22.1k | 34.1k | 11.9k | 263.3k | 250.9k | -12.4k |
| 9 | 20260201..20260430 | 53.3k | 44.5k | -8.8k | 173.1k | 235.7k | 62.6k |
| 10 | 20260501..20260731 | 28.4k | 51.0k | 22.7k | 221.6k | 156.6k | -65.0k |
| 11 | 20260801..20261016 | 47.7k | 71.3k | 23.5k | 267.1k | 273.4k | 6.3k |

Ensemble beats live on weekly mean in 9 of 11 folds.

**Significance.** 4-week block bootstrap 90% CI of the weekly delta (20-cell ensemble minus live cell, WF): [2.3k, 19.1k]; halves 8.2k / 13.2k. Null = random-neighbourhood ensembles (100 ensembles: 25 centred + 75 random mixes; the shuffled-date null is not defined for a parameter average and was not run): live-centred ensemble ranks 0.88 on WF mean and 0.97 on WF maxDD among them. 4 of the 100 20-cell ensembles beat the benchmark on WF AND L8W mean and maxDD (gate a+b); best-of-F over those 100 ensembles: live-centred is not the best (best WF mean 38.0k). Weekly SD: single pairs 103.4k vs ensembles 104.5k: no variance reduction.

**Is the live cell a poor local choice?** live WF 25.0k vs mean of its 24 grid-neighbour pairs; 20 of the 25 single pairs beat it on WF mean, IS live 13.7k vs pairs' IS mean 3.4k. See the maps above: the live cell is not on a cliff, WF differences between neighbours (sd 4.7k) are as large as the ensemble gain, and the IS ordering differs from the WF ordering (corr of IS and WF means over the 25 pairs -0.22), so no parameter move is supported.


## V2 / V5 / V6

### V2 DOWN-ONLY VOL SIZING (cap 14, floor {4,6,8}, R$ {10k,12k,16.8k}; brackets fixed 60 and ATR20/T2H unclamped k {0.8,1.0,1.25}); ATR20 rows use the replay-delta P9 mapping, fixed-60 rows are exact

Benchmark: WF 25.0k / 104.5k / 401.3k / -137.1k; L8W 34.2k / 109.4k / 267.1k. 'usd' = live dollar locks; 'vol' = locks in the trade's own R.

**locks: usd**

| cell | WF mean / SD / maxDD / worst | at EQUAL mean: SD / maxDD / worst | L8W mean / SD / maxDD | WF avg lots |
|---|---|---|---|---|
| fixed60 R$10k fl4 | 28.4k / 86.3k / 375.6k / -136.8k | 75.8k / 329.9k / -120.1k | 42.0k / 111.7k / 274.6k | 8.0 |
| fixed60 R$10k fl6 | 28.4k / 86.3k / 375.6k / -136.8k | 75.8k / 329.9k / -120.1k | 42.0k / 111.7k / 274.6k | 8.0 |
| fixed60 R$10k fl8 | 28.4k / 86.3k / 375.6k / -136.8k | 75.8k / 329.9k / -120.1k | 42.0k / 111.7k / 274.6k | 8.0 |
| fixed60 R$12k fl4 | 25.3k / 103.1k / 381.7k / -148.6k | 102.0k / 377.5k / -147.0k | 34.4k / 100.7k / 259.4k | 10.0 |
| fixed60 R$12k fl6 | 25.3k / 103.1k / 381.7k / -148.6k | 102.0k / 377.5k / -147.0k | 34.4k / 100.7k / 259.4k | 10.0 |
| fixed60 R$12k fl8 | 25.3k / 103.1k / 381.7k / -148.6k | 102.0k / 377.5k / -147.0k | 34.4k / 100.7k / 259.4k | 10.0 |
| fixed60 R$16.8k fl4 | 25.0k / 104.5k / 401.3k / -137.1k | 104.5k / 401.3k / -137.1k | 34.2k / 109.4k / 267.1k | 14.0 |
| fixed60 R$16.8k fl6 | 25.0k / 104.5k / 401.3k / -137.1k | 104.5k / 401.3k / -137.1k | 34.2k / 109.4k / 267.1k | 14.0 |
| fixed60 R$16.8k fl8 | 25.0k / 104.5k / 401.3k / -137.1k | 104.5k / 401.3k / -137.1k | 34.2k / 109.4k / 267.1k | 14.0 |
| ATR20_k0.8 R$10k fl4 | 29.9k / 91.6k / 478.8k / -135.6k | 76.5k / 400.0k / -113.3k | 60.9k / 137.7k / 293.9k | 11.9 |
| ATR20_k0.8 R$10k fl6 | 30.2k / 93.9k / 478.8k / -135.6k | 77.6k / 396.0k / -112.2k | 60.9k / 137.7k / 293.9k | 11.9 |
| ATR20_k0.8 R$10k fl8 | 29.2k / 96.7k / 478.8k / -135.3k | 82.6k / 408.9k / -115.5k | 61.8k / 139.8k / 301.0k | 12.1 |
| ATR20_k0.8 R$12k fl4 | 28.9k / 97.4k / 508.5k / -137.5k | 84.3k / 439.8k / -119.0k | 72.5k / 132.6k / 253.4k | 12.8 |
| ATR20_k0.8 R$12k fl6 | 29.0k / 99.0k / 508.5k / -137.5k | 85.4k / 438.6k / -118.6k | 72.5k / 132.6k / 253.4k | 12.9 |
| ATR20_k0.8 R$12k fl8 | 29.1k / 98.5k / 508.6k / -137.5k | 84.5k / 436.3k / -118.0k | 72.8k / 132.4k / 251.4k | 13.0 |
| ATR20_k0.8 R$16.8k fl4 | 28.1k / 103.9k / 544.4k / -143.2k | 92.4k / 484.1k / -127.3k | 86.5k / 141.0k / 249.2k | 13.8 |
| ATR20_k0.8 R$16.8k fl6 | 28.1k / 103.9k / 544.4k / -143.2k | 92.4k / 484.1k / -127.3k | 86.5k / 141.0k / 249.2k | 13.8 |
| ATR20_k0.8 R$16.8k fl8 | 28.1k / 103.8k / 544.4k / -143.2k | 92.4k / 484.5k / -127.4k | 86.5k / 141.0k / 249.2k | 13.8 |
| ATR20_k1.0 R$10k fl4 | 35.1k / 86.4k / 388.5k / -139.0k | 61.5k / 276.6k / -98.9k | 54.0k / 105.5k / 255.9k | 10.5 |
| ATR20_k1.0 R$10k fl6 | 35.4k / 89.5k / 382.5k / -139.0k | 63.2k / 269.9k / -98.1k | 54.5k / 106.6k / 259.2k | 10.7 |
| ATR20_k1.0 R$10k fl8 | 34.8k / 94.0k / 375.6k / -139.8k | 67.5k / 269.8k / -100.4k | 53.8k / 111.5k / 264.1k | 11.1 |
| ATR20_k1.0 R$12k fl4 | 35.9k / 93.2k / 410.7k / -137.6k | 64.8k / 285.6k / -95.7k | 57.3k / 104.4k / 239.9k | 11.9 |
| ATR20_k1.0 R$12k fl6 | 35.6k / 94.8k / 410.7k / -137.4k | 66.4k / 287.8k / -96.3k | 57.3k / 104.4k / 239.9k | 11.9 |
| ATR20_k1.0 R$12k fl8 | 35.2k / 97.8k / 410.7k / -140.2k | 69.4k / 291.5k / -99.5k | 53.9k / 105.4k / 238.0k | 12.1 |
| ATR20_k1.0 R$16.8k fl4 | 34.5k / 101.7k / 469.0k / -142.3k | 73.5k / 339.2k / -102.9k | 50.2k / 128.8k / 316.2k | 13.4 |
| ATR20_k1.0 R$16.8k fl6 | 34.6k / 101.8k / 469.0k / -142.3k | 73.4k / 338.5k / -102.7k | 50.2k / 128.8k / 316.2k | 13.4 |
| ATR20_k1.0 R$16.8k fl8 | 34.4k / 102.3k / 469.0k / -142.3k | 74.2k / 340.4k / -103.3k | 50.2k / 128.8k / 316.2k | 13.4 |
| ATR20_k1.25 R$10k fl4 | 22.5k / 82.0k / 514.5k / -138.7k | 90.9k / 570.9k / -153.9k | 26.6k / 117.7k / 370.5k | 9.1 |
| ATR20_k1.25 R$10k fl6 | 23.5k / 86.2k / 569.1k / -139.0k | 91.6k / 604.6k / -147.6k | 28.7k / 123.7k / 378.4k | 9.4 |
| ATR20_k1.25 R$10k fl8 | 26.1k / 91.5k / 680.3k / -135.8k | 87.5k / 650.9k / -129.9k | 23.3k / 117.9k / 396.6k | 10.2 |
| ATR20_k1.25 R$12k fl4 | 26.3k / 87.1k / 534.9k / -136.7k | 82.8k / 508.6k / -129.9k | 26.5k / 116.0k / 364.7k | 10.5 |
| ATR20_k1.25 R$12k fl6 | 26.5k / 89.2k / 592.6k / -136.6k | 84.0k / 558.3k / -128.7k | 25.7k / 117.0k / 371.2k | 10.6 |
| ATR20_k1.25 R$12k fl8 | 26.7k / 92.6k / 684.8k / -137.1k | 86.7k / 641.2k / -128.4k | 24.1k / 127.3k / 420.7k | 11.0 |
| ATR20_k1.25 R$16.8k fl4 | 26.5k / 96.8k / 570.8k / -139.7k | 91.1k / 537.2k / -131.5k | 19.7k / 112.0k / 369.0k | 12.6 |
| ATR20_k1.25 R$16.8k fl6 | 27.1k / 97.4k / 575.1k / -139.7k | 90.0k / 530.9k / -129.0k | 19.7k / 112.0k / 369.0k | 12.6 |
| ATR20_k1.25 R$16.8k fl8 | 25.9k / 99.0k / 602.0k / -139.8k | 95.4k / 580.0k / -134.7k | 19.1k / 112.9k / 371.1k | 12.7 |

**locks: vol**

| cell | WF mean / SD / maxDD / worst | at EQUAL mean: SD / maxDD / worst | L8W mean / SD / maxDD | WF avg lots |
|---|---|---|---|---|
| fixed60 R$10k fl4 | 17.2k / 59.4k / 213.6k / -78.1k | 86.1k / 309.6k / -113.1k | 23.0k / 61.5k / 148.8k | 8.0 |
| fixed60 R$10k fl6 | 17.2k / 59.4k / 213.6k / -78.1k | 86.1k / 309.6k / -113.1k | 23.0k / 61.5k / 148.8k | 8.0 |
| fixed60 R$10k fl8 | 17.2k / 59.4k / 213.6k / -78.1k | 86.1k / 309.6k / -113.1k | 23.0k / 61.5k / 148.8k | 8.0 |
| fixed60 R$12k fl4 | 20.4k / 73.4k / 281.0k / -97.4k | 89.8k / 343.8k / -119.1k | 23.8k / 76.3k / 187.3k | 10.0 |
| fixed60 R$12k fl6 | 20.4k / 73.4k / 281.0k / -97.4k | 89.8k / 343.8k / -119.1k | 23.8k / 76.3k / 187.3k | 10.0 |
| fixed60 R$12k fl8 | 20.4k / 73.4k / 281.0k / -97.4k | 89.8k / 343.8k / -119.1k | 23.8k / 76.3k / 187.3k | 10.0 |
| fixed60 R$16.8k fl4 | 25.0k / 104.5k / 401.3k / -137.1k | 104.5k / 401.3k / -137.1k | 34.2k / 109.4k / 267.1k | 14.0 |
| fixed60 R$16.8k fl6 | 25.0k / 104.5k / 401.3k / -137.1k | 104.5k / 401.3k / -137.1k | 34.2k / 109.4k / 267.1k | 14.0 |
| fixed60 R$16.8k fl8 | 25.0k / 104.5k / 401.3k / -137.1k | 104.5k / 401.3k / -137.1k | 34.2k / 109.4k / 267.1k | 14.0 |
| ATR20_k0.8 R$10k fl4 | 4.4k / 51.9k / 393.4k / -88.7k | 293.9k / 2227.4k / -502.5k | 0.6k / 73.8k / 222.0k | 12.6 |
| ATR20_k0.8 R$10k fl6 | 4.2k / 52.2k / 394.9k / -88.8k | 309.1k / 2337.1k / -525.2k | 0.6k / 73.8k / 222.0k | 12.6 |
| ATR20_k0.8 R$10k fl8 | 4.1k / 53.0k / 390.5k / -84.4k | 320.9k / 2363.7k / -510.6k | 0.5k / 74.1k / 225.5k | 12.8 |
| ATR20_k0.8 R$12k fl4 | 5.2k / 54.2k / 390.2k / -92.2k | 262.7k / 1891.0k / -447.0k | -0.1k / 76.4k / 239.7k | 13.1 |
| ATR20_k0.8 R$12k fl6 | 5.2k / 54.5k / 390.2k / -92.3k | 261.8k / 1874.5k / -443.4k | -0.1k / 76.4k / 239.7k | 13.2 |
| ATR20_k0.8 R$12k fl8 | 4.1k / 55.1k / 408.7k / -96.9k | 337.0k / 2500.2k / -593.1k | -0.3k / 76.4k / 241.7k | 13.3 |
| ATR20_k0.8 R$16.8k fl4 | 4.9k / 55.5k / 384.7k / -105.2k | 284.5k / 1973.6k / -539.9k | 0.7k / 77.1k / 240.3k | 13.8 |
| ATR20_k0.8 R$16.8k fl6 | 4.9k / 55.5k / 384.7k / -105.2k | 284.5k / 1973.6k / -539.9k | 0.7k / 77.1k / 240.3k | 13.8 |
| ATR20_k0.8 R$16.8k fl8 | 5.0k / 55.7k / 383.4k / -105.7k | 278.4k / 1917.3k / -528.7k | 0.7k / 77.1k / 240.3k | 13.8 |
| ATR20_k1.0 R$10k fl4 | 16.0k / 55.2k / 197.1k / -83.3k | 86.0k / 307.4k / -129.9k | 13.3k / 75.6k / 180.3k | 11.4 |
| ATR20_k1.0 R$10k fl6 | 16.2k / 55.2k / 201.6k / -85.1k | 85.4k / 311.6k / -131.6k | 14.0k / 76.6k / 178.7k | 11.6 |
| ATR20_k1.0 R$10k fl8 | 15.2k / 55.6k / 206.9k / -90.0k | 91.2k / 339.1k / -147.5k | 16.0k / 79.3k / 184.0k | 11.9 |
| ATR20_k1.0 R$12k fl4 | 16.0k / 59.9k / 228.2k / -100.0k | 93.6k / 356.5k / -156.3k | 16.8k / 82.9k / 187.4k | 12.3 |
| ATR20_k1.0 R$12k fl6 | 15.4k / 60.4k / 235.4k / -100.9k | 97.7k / 380.6k / -163.1k | 16.8k / 82.9k / 187.4k | 12.4 |
| ATR20_k1.0 R$12k fl8 | 15.7k / 59.5k / 248.7k / -101.3k | 94.5k / 394.8k / -160.8k | 15.8k / 83.5k / 187.1k | 12.6 |
| ATR20_k1.0 R$16.8k fl4 | 15.3k / 62.5k / 278.1k / -132.5k | 102.2k / 455.0k / -216.7k | 19.0k / 79.7k / 166.6k | 13.4 |
| ATR20_k1.0 R$16.8k fl6 | 15.3k / 62.6k / 281.9k / -135.0k | 102.0k / 459.3k / -219.9k | 19.0k / 79.7k / 166.6k | 13.4 |
| ATR20_k1.0 R$16.8k fl8 | 15.2k / 63.2k / 289.4k / -134.4k | 104.0k / 476.6k / -221.3k | 19.1k / 79.7k / 166.6k | 13.4 |
| ATR20_k1.25 R$10k fl4 | 11.0k / 60.5k / 442.2k / -85.2k | 137.4k / 1003.1k / -193.3k | 14.6k / 67.6k / 219.6k | 9.8 |
| ATR20_k1.25 R$10k fl6 | 9.5k / 62.8k / 456.1k / -85.3k | 164.7k / 1195.0k / -223.4k | 11.8k / 71.7k / 236.9k | 10.2 |
| ATR20_k1.25 R$10k fl8 | 10.8k / 65.9k / 488.2k / -112.4k | 151.7k / 1124.2k / -258.7k | 13.1k / 77.0k / 254.9k | 10.8 |
| ATR20_k1.25 R$12k fl4 | 10.3k / 66.7k / 540.3k / -98.2k | 160.9k / 1304.1k / -237.1k | 12.2k / 81.5k / 280.5k | 10.9 |
| ATR20_k1.25 R$12k fl6 | 9.4k / 68.6k / 561.4k / -99.3k | 182.5k / 1492.3k / -264.1k | 12.1k / 82.0k / 280.2k | 11.1 |
| ATR20_k1.25 R$12k fl8 | 9.8k / 71.1k / 575.0k / -112.4k | 180.7k / 1460.3k / -285.4k | 12.4k / 86.1k / 292.8k | 11.5 |
| ATR20_k1.25 R$16.8k fl4 | 13.5k / 76.6k / 552.8k / -135.5k | 141.7k / 1021.9k / -250.5k | 15.3k / 93.7k / 320.9k | 12.5 |
| ATR20_k1.25 R$16.8k fl6 | 13.7k / 77.5k / 552.8k / -137.0k | 140.9k / 1004.8k / -249.0k | 15.3k / 93.7k / 320.9k | 12.6 |
| ATR20_k1.25 R$16.8k fl8 | 12.8k / 79.0k / 576.3k / -140.3k | 154.4k / 1126.9k / -274.3k | 14.2k / 95.3k / 328.2k | 12.8 |

V2 answer: down-only sizing on the unchanged 60-pt bracket (fixed60) gives WF 28.4k at best with the live locks (it is just 8-14 lots = the V3 curve; floors are inert because lots are constant), i.e. no gain from vol sizing there; the gain appears only with ATR20 brackets (k=1.0: WF 35-36k, SD 86-94k, maxDD 389-411k vs 25.0k/104.5k/401k), and it is k-specific: k=0.8 and 1.25 are far weaker (table). Equal-mean SD of the k=1.0 cells 61-65k.

### V5 REFINE THE BEST CELL (ATR20/T2H unclamped; k x R$ x cap x floor; live dollar locks and vol-unit locks)

**k x R$ plateau (cap 14, floor 4, live locks): WF mean / SD / maxDD (L8W mean)** - the plateau test: neighbours of k=1.0

| k | R$8k | R$10k | R$12k | R$16.8k |
|---|---|---|---|---|
| 0.8 | 28/81/393 (61) | 30/92/479 (61) | 29/97/509 (73) | 28/104/544 (86) |
| 0.9 | 32/86/458 (78) | 34/97/477 (82) | 38/104/527 (88) | 37/109/526 (87) |
| 1.0 | 33/78/310 (74) | 35/86/389 (54) | 36/93/411 (57) | 35/102/469 (50) |
| 1.1 | 21/76/526 (19) | 22/85/516 (27) | 28/91/574 (33) | 30/101/501 (26) |
| 1.25 | 17/73/441 (19) | 23/82/515 (27) | 26/87/535 (27) | 27/97/571 (20) |

**Same, locks in vol-unit R:**

| k | R$8k | R$10k | R$12k | R$16.8k |
|---|---|---|---|---|
| 0.8 | 5/47/350 (0) | 4/52/393 (1) | 5/54/390 (-0) | 5/55/385 (1) |
| 0.9 | 11/51/261 (19) | 10/57/344 (27) | 11/61/368 (21) | 10/64/410 (17) |
| 1.0 | 13/48/211 (18) | 16/55/197 (13) | 16/60/228 (17) | 15/62/278 (19) |
| 1.1 | 11/50/299 (8) | 12/59/368 (8) | 13/64/432 (11) | 15/73/439 (3) |
| 1.25 | 8/51/406 (13) | 11/61/442 (15) | 10/67/540 (12) | 14/77/553 (15) |

**Top 12 of the 240 V5 cells by equal-mean SD (selected; live locks):**

| cell | WF mean / SD / maxDD / worst | at EQUAL mean: SD / maxDD / worst | L8W mean / SD / maxDD | WF avg lots |
|---|---|---|---|---|
| ATR20_k1.0 R$8k cap14 fl4 | 32.5k / 78.5k / 309.9k / -137.4k | 60.3k / 238.0k / -105.5k | 74.1k / 95.5k / 178.5k | 8.9 |
| ATR20_k1.0 R$10k cap14 fl4 | 35.1k / 86.4k / 388.5k / -139.0k | 61.5k / 276.6k / -98.9k | 54.0k / 105.5k / 255.9k | 10.5 |
| ATR20_k1.0 R$8k cap20 fl4 | 32.4k / 80.4k / 316.2k / -137.3k | 61.9k / 243.4k / -105.7k | 74.1k / 95.5k / 178.5k | 9.5 |
| ATR20_k1.0 R$10k cap20 fl4 | 35.0k / 89.1k / 358.1k / -139.0k | 63.5k / 255.4k / -99.1k | 55.2k / 102.4k / 245.8k | 11.8 |
| ATR20_k1.0 R$12k cap14 fl4 | 35.9k / 93.2k / 410.7k / -137.6k | 64.8k / 285.6k / -95.7k | 57.3k / 104.4k / 239.9k | 11.9 |
| ATR20_k1.0 R$8k cap14 fl8 | 33.8k / 89.5k / 362.2k / -136.1k | 66.1k / 267.7k / -100.6k | 78.8k / 109.0k / 200.6k | 10.0 |
| ATR20_k1.0 R$10k cap14 fl8 | 34.8k / 94.0k / 375.6k / -139.8k | 67.5k / 269.8k / -100.4k | 53.8k / 111.5k / 264.1k | 11.1 |
| ATR20_k1.0 R$8k cap20 fl8 | 33.7k / 91.5k / 362.2k / -135.8k | 67.7k / 268.2k / -100.5k | 78.8k / 109.0k / 200.6k | 10.7 |
| ATR20_k0.9 R$8k cap14 fl4 | 31.5k / 85.9k / 457.8k / -135.2k | 68.1k / 362.7k / -107.1k | 78.1k / 116.6k / 193.1k | 9.6 |
| ATR20_k0.9 R$12k cap14 fl4 | 37.5k / 104.1k / 527.3k / -137.6k | 69.3k / 351.0k / -91.6k | 88.0k / 129.7k / 222.2k | 12.3 |
| ATR20_k1.0 R$12k cap14 fl8 | 35.2k / 97.8k / 410.7k / -140.2k | 69.4k / 291.5k / -99.5k | 53.9k / 105.4k / 238.0k | 12.1 |
| ATR20_k1.0 R$10k cap20 fl8 | 34.7k / 96.8k / 355.8k / -136.5k | 69.7k / 256.3k / -98.3k | 54.9k / 109.0k / 256.6k | 12.5 |

Gate a+b (beat benchmark on WF and L8W mean and maxDD) in the V5 grid: 11 of 60 usd cells, 0 vol-lock cells; all passers have k=1.0 (k=0.9/1.1/0.8/1.25 pass: 1).

**Session-specific k (kASIA-kLONDON-kNY in {0.8,1.0,1.25}^3; ATR20/T2H unclamped, R$10k cap14 floor4)** - top 8 / reference 1.0-1.0-1.0 by WF mean (live locks):

| ks | unit | WF mean / SD / maxDD | equal-mean SD | L8W mean / maxDD |
|---|---|---|---|---|
| 0-1.0-1.0 | usd | 35.1k / 86.4k / 388.5k | 61.5k | 54.0k / 255.9k |
| 0-0.8-1.0 | usd | 35.0k / 87.4k / 621.2k | 62.3k | 63.5k / 253.0k |
| 0-1.0-1.25 | usd | 33.9k / 87.6k / 492.8k | 64.5k | 56.4k / 246.1k |
| 0-1.0-0.8 | usd | 33.1k / 90.6k / 460.9k | 68.4k | 50.5k / 321.7k |
| 0-0.8-1.25 | usd | 32.9k / 88.4k / 593.7k | 67.1k | 68.7k / 233.3k |
| 8-0.8-1.0 | usd | 31.8k / 90.7k / 437.0k | 71.2k | 64.5k / 273.7k |
| 8-1.0-1.0 | usd | 31.1k / 93.7k / 435.7k | 75.2k | 55.3k / 259.9k |
| 0-0.8-0.8 | usd | 30.8k / 90.8k / 708.5k | 73.6k | 62.5k / 329.7k |
| 0-1.0-1.0 | usd | 35.1k / 86.4k / 388.5k | 61.5k | 54.0k / 255.9k |
- mean WF over the other two sessions' k, by ASIA k: 0.8: 28.6k, 1.0: 31.8k, 1.25: 24.7k
- mean WF over the other two sessions' k, by LONDON k: 0.8: 29.2k, 1.0: 30.3k, 1.25: 25.6k
- mean WF over the other two sessions' k, by NY k: 0.8: 27.8k, 1.0: 29.4k, 1.25: 27.8k

### V6 PORTFOLIO VOL TARGET (3.3) AND KELLY / DD-CONTROL (3.5) ON TOP OF V2 (cap 14, floor 4, live locks) and the v2 numbers

| cell | WF mean / SD / maxDD / worst | equal-mean SD / maxDD | L8W mean / SD / maxDD | avg lots |
|---|---|---|---|---|
| V6 / fixed60 / R10000 / base / usd | 28.4k / 86.3k / 375.6k / -136.8k | 75.8k / 329.9k | 42.0k / 111.7k / 274.6k | 8.0 |
| V6 / fixed60 / R10000 / 3.3_vt60k / usd | 20.5k / 78.6k / 326.9k / -135.5k | 95.9k / 399.0k | 30.0k / 97.4k / 236.7k | 5.9 |
| V6 / fixed60 / R10000 / 3.3_vt75k / usd | 26.0k / 88.1k / 379.6k / -136.5k | 84.5k / 364.0k | 50.9k / 106.3k / 201.7k | 7.1 |
| V6 / fixed60 / R10000 / 3.3_vt90k / usd | 30.8k / 92.0k / 367.8k / -136.5k | 74.7k / 298.6k | 50.8k / 104.2k / 240.7k | 8.3 |
| V6 / fixed60 / R10000 / 3.5_kelly0.25 / usd | 25.9k / 85.1k / 371.7k / -134.7k | 81.9k / 357.8k | 37.4k / 116.3k / 291.8k | 7.6 |
| V6 / fixed60 / R10000 / 3.5_kelly0.25_dd / usd | 22.5k / 77.0k / 353.8k / -134.7k | 85.7k / 393.6k | 21.1k / 93.9k / 284.3k | 6.2 |
| V6 / fixed60 / R10000 / 3.5_kelly0.5 / usd | 23.1k / 104.2k / 418.7k / -138.3k | 112.5k / 451.9k | 36.6k / 117.6k / 306.1k | 11.2 |
| V6 / fixed60 / R10000 / 3.5_kelly0.5_dd / usd | 15.3k / 91.6k / 452.7k / -138.3k | 149.0k / 736.8k | 20.3k / 95.3k / 298.7k | 8.3 |
| V6 / fixed60 / R10000 / 3.5_dd_only / usd | 22.1k / 78.2k / 375.8k / -136.8k | 88.4k / 425.1k | 21.8k / 96.5k / 298.4k | 6.6 |
| V6 / ATR20_k1.0 / R12000 / base / usd | 35.9k / 93.2k / 410.7k / -137.6k | 64.8k / 285.6k | 57.3k / 104.4k / 239.9k | 11.9 |
| V6 / ATR20_k1.0 / R12000 / 3.3_vt60k / usd | 30.9k / 83.1k / 354.3k / -137.8k | 67.1k / 286.2k | 49.4k / 96.0k / 209.1k | 8.4 |
| V6 / ATR20_k1.0 / R12000 / 3.3_vt75k / usd | 31.2k / 87.3k / 465.7k / -138.8k | 69.8k / 372.4k | 58.2k / 96.4k / 213.5k | 9.9 |
| V6 / ATR20_k1.0 / R12000 / 3.3_vt90k / usd | 32.2k / 90.8k / 421.8k / -139.8k | 70.4k / 327.3k | 56.1k / 100.8k / 231.8k | 11.1 |
| V6 / ATR20_k1.0 / R12000 / 3.5_kelly0.25 / usd | 36.0k / 83.3k / 348.8k / -136.1k | 57.8k / 242.0k | 74.1k / 95.5k / 178.5k | 9.8 |
| V6 / ATR20_k1.0 / R12000 / 3.5_kelly0.25_dd / usd | 31.4k / 76.5k / 271.6k / -135.0k | 60.8k / 215.7k | 70.2k / 94.4k / 178.5k | 8.6 |
| V6 / ATR20_k1.0 / R12000 / 3.5_kelly0.5 / usd | 32.6k / 96.2k / 460.5k / -138.6k | 73.8k / 353.2k | 58.1k / 94.3k / 184.5k | 12.3 |
| V6 / ATR20_k1.0 / R12000 / 3.5_kelly0.5_dd / usd | 30.9k / 89.4k / 442.2k / -136.5k | 72.3k / 357.3k | 54.2k / 92.6k / 184.5k | 10.8 |
| V6 / ATR20_k1.0 / R12000 / 3.5_dd_only / usd | 30.3k / 83.7k / 426.8k / -136.3k | 69.1k / 352.2k | 50.2k / 108.0k / 257.3k | 9.5 |
| V6 / ATR20_k1.0 / R10000 / base / usd | 35.1k / 86.4k / 388.5k / -139.0k | 61.5k / 276.6k | 54.0k / 105.5k / 255.9k | 10.5 |
| V6 / ATR20_k1.0 / R10000 / 3.3_vt60k / usd | 31.5k / 78.2k / 340.1k / -136.0k | 62.1k / 269.9k | 45.0k / 88.4k / 230.3k | 8.3 |
| V6 / ATR20_k1.0 / R10000 / 3.3_vt75k / usd | 33.4k / 86.8k / 406.2k / -136.9k | 64.8k / 303.5k | 47.4k / 102.2k / 266.3k | 9.6 |
| V6 / ATR20_k1.0 / R10000 / 3.3_vt90k / usd | 29.6k / 90.0k / 460.2k / -138.3k | 76.1k / 388.9k | 44.6k / 119.4k / 310.0k | 10.7 |
| V6 / ATR20_k1.0 / R10000 / 3.5_kelly0.25 / usd | 36.0k / 83.3k / 348.8k / -136.1k | 57.8k / 242.0k | 74.1k / 95.5k / 178.5k | 9.8 |
| V6 / ATR20_k1.0 / R10000 / 3.5_kelly0.25_dd / usd | 31.4k / 76.5k / 271.6k / -135.0k | 60.8k / 215.7k | 70.2k / 94.4k / 178.5k | 8.6 |
| V6 / ATR20_k1.0 / R10000 / 3.5_kelly0.5 / usd | 32.6k / 96.2k / 460.5k / -138.6k | 73.8k / 353.2k | 58.1k / 94.3k / 184.5k | 12.3 |
| V6 / ATR20_k1.0 / R10000 / 3.5_kelly0.5_dd / usd | 30.9k / 89.4k / 442.2k / -136.5k | 72.3k / 357.3k | 54.2k / 92.6k / 184.5k | 10.8 |
| V6 / ATR20_k1.0 / R10000 / 3.5_dd_only / usd | 31.0k / 77.8k / 316.2k / -138.9k | 62.8k / 255.0k | 41.9k / 98.3k / 263.6k | 8.9 |

v2 results (omitted from the v2 verdict), firm bracket R$16.8k cap 28 and fixed 60 bases: firm|3.3_vt60k: WF 17.5k/SD 92.2k/maxDD 536.6k; firm|3.3_vt75k: WF 13.9k/SD 95.9k/maxDD 626.6k; firm|3.3_vt90k: WF 11.8k/SD 100.0k/maxDD 830.1k; firm|3.5_kelly0.25: WF 16.9k/SD 84.9k/maxDD 466.0k; firm|3.5_kelly0.25_dd: WF 13.5k/SD 76.7k/maxDD 431.1k; firm|3.5_kelly0.5: WF 13.2k/SD 95.2k/maxDD 746.7k; firm|3.5_kelly0.5_dd: WF 11.0k/SD 82.0k/maxDD 517.8k; firm|3.5_dd_only: WF 14.3k/SD 90.5k/maxDD 507.3k; fixed60|3.3_vt60k: WF 24.7k/SD 84.4k/maxDD 380.0k; fixed60|3.3_vt75k: WF 27.1k/SD 97.4k/maxDD 386.3k; fixed60|3.3_vt90k: WF 25.9k/SD 104.0k/maxDD 435.9k; fixed60|3.5_kelly0.25: WF 25.9k/SD 85.1k/maxDD 371.7k; fixed60|3.5_kelly0.25_dd: WF 22.5k/SD 77.0k/maxDD 353.8k; fixed60|3.5_kelly0.5: WF 17.9k/SD 102.7k/maxDD 464.4k; fixed60|3.5_kelly0.5_dd: WF 18.0k/SD 92.2k/maxDD 357.2k; fixed60|3.5_dd_only: WF 17.2k/SD 93.6k/maxDD 422.2k


**V5 null N1 (shuffled forecast, wrap >= 20 label days, whole cell regenerated; 200 worlds, common shift; single approximation seed so real values differ slightly from the 3-seed tables above):**

| cell | WF mean / SD / maxDD | L8W mean / maxDD | rank mean | rank maxDD | rank scaled-SD | rank L8W mean |
|---|---|---|---|---|---|---|
| ATR20_T2H_k0.8_un_r1.0 / R10000c14f4 | 27.8k / 93.3k / 547.4k | 56.4k / 272.5k | 1.00 | 0.91 | 1.00 | 0.93 |
| ATR20_T2H_k0.8_un_r1.0 / R12000c14f4 | 26.8k / 99.1k / 558.4k | 69.1k / 238.1k | 0.99 | 0.90 | 0.99 | 0.95 |
| ATR20_T2H_k0.8_un_r1.0 / R8000c14f4 | 28.8k / 82.1k / 377.3k | 67.5k / 182.6k | 1.00 | 0.99 | 1.00 | 0.96 |
| ATR20_T2H_k0.8_un_r1.0 / R8000c20f4 | 24.4k / 86.3k / 605.9k | 63.3k / 194.0k | 0.99 | 0.92 | 1.00 | 0.95 |
| ATR20_T2H_k0.9_un_r1.0 / R10000c14f4 | 31.2k / 95.8k / 414.7k | 62.6k / 315.0k | 0.99 | 0.97 | 0.99 | 0.97 |
| ATR20_T2H_k0.9_un_r1.0 / R12000c14f4 | 34.6k / 106.4k / 441.0k | 71.7k / 315.1k | 0.99 | 0.98 | 0.99 | 0.98 |
| ATR20_T2H_k0.9_un_r1.0 / R8000c14f4 | 28.6k / 86.3k / 503.0k | 58.3k / 310.7k | 0.99 | 0.84 | 0.99 | 0.94 |
| ATR20_T2H_k0.9_un_r1.0 / R8000c20f4 | 29.5k / 89.1k / 562.1k | 58.3k / 310.7k | 1.00 | 0.86 | 1.00 | 0.94 |
| ATR20_T2H_k1.0_un_r1.0 / R10000c14f4 | 31.1k / 83.6k / 421.0k | 49.6k / 292.5k | 0.98 | 0.96 | 0.99 | 0.86 |
| ATR20_T2H_k1.0_un_r1.0 / R12000c14f4 | 33.2k / 93.1k / 475.0k | 51.1k / 291.0k | 0.99 | 0.93 | 0.99 | 0.81 |
| ATR20_T2H_k1.0_un_r1.0 / R8000c14f4 | 31.5k / 75.9k / 241.8k | 69.4k / 213.6k | 1.00 | 1.00 | 1.00 | 0.99 |
| ATR20_T2H_k1.0_un_r1.0 / R8000c20f4 | 30.9k / 78.4k / 281.8k | 69.4k / 213.6k | 1.00 | 1.00 | 1.00 | 0.99 |
| ATR20_T2H_k1.1_un_r1.0 / R10000c14f4 | 19.7k / 82.1k / 539.6k | 21.6k / 436.1k | 0.56 | 0.59 | 0.70 | 0.49 |
| ATR20_T2H_k1.1_un_r1.0 / R12000c14f4 | 24.9k / 87.2k / 573.7k | 16.0k / 417.9k | 0.79 | 0.69 | 0.93 | 0.36 |
| ATR20_T2H_k1.1_un_r1.0 / R8000c14f4 | 19.6k / 74.6k / 485.1k | 29.8k / 379.1k | 0.57 | 0.59 | 0.72 | 0.62 |
| ATR20_T2H_k1.1_un_r1.0 / R8000c20f4 | 18.3k / 76.3k / 485.1k | 29.8k / 379.1k | 0.59 | 0.74 | 0.72 | 0.56 |
| ATR20_T2H_k1.25_un_r1.0 / R10000c14f4 | 18.6k / 79.5k / 571.2k | 32.8k / 355.8k | 0.35 | 0.41 | 0.55 | 0.58 |
| ATR20_T2H_k1.25_un_r1.0 / R12000c14f4 | 23.2k / 85.0k / 572.7k | 39.9k / 329.1k | 0.57 | 0.49 | 0.81 | 0.59 |
| ATR20_T2H_k1.25_un_r1.0 / R8000c14f4 | 14.1k / 71.0k / 421.9k | 24.9k / 368.9k | 0.12 | 0.71 | 0.25 | 0.51 |
| ATR20_T2H_k1.25_un_r1.0 / R8000c20f4 | 14.0k / 71.4k / 421.9k | 24.9k / 368.9k | 0.23 | 0.76 | 0.37 | 0.48 |

Best-of-F over this family (20 variants, family-world scan: max WF mean subject to L8W mean > benchmark): real 34.6k exceeds 99.5% of the 200 null-world maxima (null maxima: median 20.9k, 95th pct 29.5k, max 34.8k); worlds with no qualifying variant count as 0. The resolution with <=200 worlds is 0.5%, the Bonferroni line 1-0.05/3,358 = 0.99998 would need >10^5 worlds and is NOT demonstrated; no tail extrapolation is attempted (the maxima are not normal). The family covers only the ATR20/T2H neighbourhood, not the rest of the ~4,700-cell v2 grid from which it was picked.

## V7 DIRECT L2 REPLAY AND RECONCILIATION

DIRECT REPLAY (R10k_c14; 45 of 45 months replayed; arms EM/S14x1 entry + XS4/XJ/XS0 stop exits chosen per fold/book on the fit window, EM market execution before 2024-02 as in the benchmark table; unreplayed rows fall back to natural pts):
- IS: mean -1.9k / SD 75.6k / maxDD 552.9k / worst -135.2k / Sharpe -0.19 / trades/wk 71 / avg lots 12.8 / max 14 / peak 28  (benchmark: 13.7k / 95.9k / 407.3k / -136.3k)
- WF: mean 29.6k / SD 86.9k / maxDD 545.9k / worst -135.1k / Sharpe 2.45 / trades/wk 72 / avg lots 10.5 / max 14 / peak 28  (benchmark: 25.0k / 104.5k / 401.3k / -137.1k)
- L8W: mean 70.9k / SD 78.0k / maxDD 170.7k / worst -29.2k / Sharpe 6.56 / trades/wk 79 / avg lots 10.6 / max 14 / peak 28  (benchmark: 34.2k / 109.4k / 267.1k / -98.9k)
- equal-mean (WF): m=0.84, SD 73.4k, maxDD 461.1k, worst -114.2k; L8W at same m: SD 65.9k, maxDD 144.2k
- gate a (WF mean>bench and maxDD<bench): False; gate b (L8W): True; gate d: boot90 CI of WF weekly delta-mean [-6.9k, 13.7k], halves 2.3k / 6.4k; null N1 rank (from the approximate-mapping worlds): see null table

DIRECT REPLAY (R10k_c28; 45 of 45 months replayed; arms EM/S14x1 entry + XS4/XJ/XS0 stop exits chosen per fold/book on the fit window, EM market execution before 2024-02 as in the benchmark table; unreplayed rows fall back to natural pts):
- IS: mean -17.7k / SD 90.3k / maxDD 1343.1k / worst -140.6k / Sharpe -1.41 / trades/wk 61 / avg lots 18.2 / max 28 / peak 56  (benchmark: 13.7k / 95.9k / 407.3k / -136.3k)
- WF: mean 25.4k / SD 87.5k / maxDD 436.3k / worst -136.5k / Sharpe 2.09 / trades/wk 66 / avg lots 12.4 / max 28 / peak 56  (benchmark: 25.0k / 104.5k / 401.3k / -137.1k)
- L8W: mean 71.0k / SD 79.9k / maxDD 176.8k / worst -32.9k / Sharpe 6.41 / trades/wk 76 / avg lots 10.8 / max 15 / peak 30  (benchmark: 34.2k / 109.4k / 267.1k / -98.9k)
- equal-mean (WF): m=0.99, SD 86.1k, maxDD 429.8k, worst -134.4k; L8W at same m: SD 78.7k, maxDD 174.2k
- gate a (WF mean>bench and maxDD<bench): False; gate b (L8W): True; gate d: boot90 CI of WF weekly delta-mean [-10.8k, 10.1k], halves -4.8k / 4.6k; null N1 rank (from the approximate-mapping worlds): see null table

DIRECT REPLAY (R8k_c14; 45 of 45 months replayed; arms EM/S14x1 entry + XS4/XJ/XS0 stop exits chosen per fold/book on the fit window, EM market execution before 2024-02 as in the benchmark table; unreplayed rows fall back to natural pts):
- IS: mean -6.3k / SD 71.6k / maxDD 763.4k / worst -135.6k / Sharpe -0.64 / trades/wk 74 / avg lots 11.3 / max 14 / peak 28  (benchmark: 13.7k / 95.9k / 407.3k / -136.3k)
- WF: mean 26.8k / SD 78.3k / maxDD 558.8k / worst -135.3k / Sharpe 2.47 / trades/wk 81 / avg lots 8.9 / max 14 / peak 28  (benchmark: 25.0k / 104.5k / 401.3k / -137.1k)
- L8W: mean 87.3k / SD 83.3k / maxDD 88.5k / worst -43.4k / Sharpe 7.56 / trades/wk 98 / avg lots 8.2 / max 12 / peak 24  (benchmark: 34.2k / 109.4k / 267.1k / -98.9k)
- equal-mean (WF): m=0.93, SD 73.0k, maxDD 520.9k, worst -126.1k; L8W at same m: SD 77.7k, maxDD 82.5k
- gate a (WF mean>bench and maxDD<bench): False; gate b (L8W): True; gate d: boot90 CI of WF weekly delta-mean [-9.3k, 9.9k], halves -0.6k / 3.8k; null N1 rank (from the approximate-mapping worlds): see null table

DIRECT REPLAY (R12k_c14; 45 of 45 months replayed; arms EM/S14x1 entry + XS4/XJ/XS0 stop exits chosen per fold/book on the fit window, EM market execution before 2024-02 as in the benchmark table; unreplayed rows fall back to natural pts):
- IS: mean -3.3k / SD 78.7k / maxDD 550.9k / worst -135.2k / Sharpe -0.30 / trades/wk 69 / avg lots 13.6 / max 14 / peak 28  (benchmark: 13.7k / 95.9k / 407.3k / -136.3k)
- WF: mean 28.2k / SD 93.6k / maxDD 557.9k / worst -137.0k / Sharpe 2.17 / trades/wk 66 / avg lots 11.9 / max 14 / peak 28  (benchmark: 25.0k / 104.5k / 401.3k / -137.1k)
- L8W: mean 66.8k / SD 88.8k / maxDD 186.2k / worst -65.3k / Sharpe 5.43 / trades/wk 71 / avg lots 12.0 / max 14 / peak 28  (benchmark: 34.2k / 109.4k / 267.1k / -98.9k)
- equal-mean (WF): m=0.89, SD 82.9k, maxDD 494.3k, worst -121.4k; L8W at same m: SD 78.7k, maxDD 165.0k
- gate a (WF mean>bench and maxDD<bench): False; gate b (L8W): True; gate d: boot90 CI of WF weekly delta-mean [-8.7k, 13.6k], halves 1.5k / 4.6k; null N1 rank (from the approximate-mapping worlds): see null table

V7 RECONCILIATION (mean / SD / maxDD, 14/14 $/wk; mapping = v2 replay-delta path-table result averaged over 8 seeds, replay = direct L2 replay of all 45 months):
- R10k_c14: path-table mapping (8-seed mean) vs direct replay -- IS 7.8k/70.7k/344.7k vs -1.9k/75.6k/552.9k; WF 34.0k/82.5k/431.3k vs 29.6k/86.9k/545.9k; L8W 62.1k/95.5k/199.7k vs 70.9k/78.0k/170.7k; WF daily corr 0.947, weekly corr 0.954
- R10k_c28: path-table mapping (8-seed mean) vs direct replay -- IS -5.3k/87.3k/876.0k vs -17.7k/90.3k/1343.1k; WF 32.7k/85.9k/333.6k vs 25.4k/87.5k/436.3k; L8W 61.2k/94.2k/196.4k vs 71.0k/79.9k/176.8k; WF daily corr 0.938, weekly corr 0.946
- R8k_c14: path-table mapping (8-seed mean) vs direct replay -- IS 3.0k/69.8k/403.9k vs -6.3k/71.6k/763.4k; WF 31.9k/75.1k/314.8k vs 26.8k/78.3k/558.8k; L8W 80.6k/86.9k/132.6k vs 87.3k/83.3k/88.5k; WF daily corr 0.950, weekly corr 0.944

Replay mechanics: raw mbp-10 via exec_engine_l2 (prop queue model, 5 ms latency, no self-impact), EM and S14x1 entry arms with per-fill bracket, XS4/XJ/XS0 stop-exit arms with the corrected id mapping; policy arm per fold/book chosen on the fit window as p9_t9.choose but over the two arms replayed (EM, S14x1) - the benchmark table chose among six entry arms, a small difference; before the first read window (2024-02) execution is EM market, as in the benchmark table, which penalises tight brackets in IS. Gate lines are computed vs the benchmark exact series; null ranks come from the path-table worlds (same cell, shuffled forecast) and are therefore indicative for the replay.


## VERDICT (v3)

**1. Live size (V3).** The live 14-lot size is not supported by the marginal-lot curve. With the live fixed-dollar locks the walk-forward weekly mean is flat from 6 to 20 lots (21-28k/wk; 8 lots 28.4k, 14 lots 25.0k, 20 lots 24.6k) while SD (49k -> 107k), maxDD (259k -> 525k) and worst week grow with size, and trades/week collapse (82 -> 25) because the locks fire earlier. Lots 9-14 do pay in ASIA (WF 14.5k @8 -> 18.2k @14) and do not pay in NY (8.4k @8 -> 4.3k @14 -> 2.5k @20), LONDON is flat. IS peaks at 16 lots, WF at 8: there is no stable optimum; 8 lots earns 28.4k with SD 86k / maxDD 376k (vs 25.0k / 104.5k / 401k at 14), 10-12 lots are equal to 14 within noise, but this is a lock-interplay result (the benefit is that the dollar locks bind less), it is not null-testable, and IS disagrees. A per-session size (ASIA 12-14, NY/LONDON 8-10) is the only data-supported refinement (table F: ASIA at 12 lots 28.1k vs 25.0k), still single-look.

**2. Locks (V1).** The give-back arm is the lock that truncates (SD 172k -> 136k alone, maxDD 1.04M -> 494k, 10k/wk of mean); per-book and combined caps barely matter on their own; the week floor 8R adds no SD reduction, costs 4.2k/wk and raises maxDD (325k -> 401k) on top of the rest. With locks OFF, ATR20-scaled brackets + constant-dollar sizing reduce the pure-signal SD at equal mean by 26% and maxDD by 47% (path-table figures; see V7 for the direct-replay version): the dollar locks mask this. Vol-unit R for every lock cuts SD to ~55k but cuts the mean to 16k as well.

**3. Ensemble (V4).** The 20-cell ensemble around the live parameters has WF 35.9k vs 25.0k, with weekly SD unchanged (~104k), a bootstrap CI vs live of [+2.3k, +19.1k], 9 of 11 folds better, but: IS worse (6.5k vs 13.7k), L8W maxDD worse (290k vs 267k), null rank 0.88/0.97 against 100 random-neighbourhood ensembles, and the live cell sits below 20 of 25 grid neighbours in WF but far above them in IS (13.7k vs 3.4k): the live parameters were tuned on 2023 data and regress to the neighbourhood mean out of sample. The plateau is wide and flat (WF 21-40k across the whole 9x9 maps with no cliff); the IS-WF rank correlation is -0.22, so there is no supported parameter move; the robust centre by smoothed IS+WF Sharpe is ST ATR 132 / mult 1.8, HM 22 x 50 (selection-contaminated), and the walk-forward-chosen neighbourhood (WF 29-33k) is no better than the plain ensemble. Not a LEAD (gate c, b). It is the cheapest hedge against the live cell being a lucky in-sample pick, at no SD change; it needs 20 strategy instances or netted positions (MNQ 1/10 granularity) and was not run with replay-validated costs.

**4. The ATR20 cell (V2/V5/V7).** On the path-table mapping ATR20/T2H/k=1.0 (unclamped), R$8-10k, cap 14, floor 4 beat the benchmark on WF and L8W mean and maxDD (23 of 240 V5 cells; all at k=1.0; k=1.1 and 1.25 fail; null ranks 0.97-1.00 on mean, maxDD, scaled SD for k<=1.0 and ~0.1-0.8 for k>=1.1 over 200 worlds; best-of-F beats all 200 null-world family maxima). **The direct L2 replay (V7, 45 months, EM execution before 2024-02 and per-fold arm choice after, as the benchmark table) does not confirm the maxDD claim:** R$10k cap14: WF 29.6k / SD 86.9k / maxDD 545.9k (benchmark 25.0k / 104.5k / 401.3k), L8W 70.9k / 78.0k / 170.7k (34.2k / 109.4k / 267.1k), IS -1.9k / 75.6k / 552.9k (13.7k / 95.9k / 407.3k). The mapping overstates the WF mean by 4-7k/wk and understates maxDD by 115-245k (daily correlation 0.94-0.95), because the tight ATR20 brackets (median 44 pts, down to 15) are execution-cost sensitive and the mapping has no sample of the worst clustered days. Direct-replay result: weekly SD is lower (86.9k vs 104.5k, -17%; at equal WF mean 73k, -30%), mean +4.6k/wk (bootstrap CI [-6.9k, +13.7k] includes zero, gate d fails), WF maxDD +145k worse (gate a fails), L8W much better, IS negative. => not a LEAD, not CONFIRMED, and the vol-normalisation SD benefit is real in SD but does not translate into a drawdown-better, income-equal pair.

**5. V6.** Re-run on top of V2 (cap 14, floor 4, live locks, path-table mapping): portfolio vol-targeting (3.3) lowers SD and mean together (fixed-60 8-lot base 28.4k/86.3k/376k -> 60k target 20.5k/78.6k/327k; ATR20 R$10k base 35.1k/86.4k/389k -> 31.5k/78.2k/340k); Kelly 0.5 and DD-only do not help (mean down, SD ~equal or up). The one V6 cell worth a replay is Kelly 0.25 (+ DD overlay) on the ATR20 base: WF 36.0k/83.3k/349k and 31.4k/76.5k/272k with the overlay, L8W 74.1k/178.5k and 70.2k/178.5k (mean multiplier from trailing 26-week closed-trade edge, prior trades only). It is single-look, un-nulled and path-table-only; V7 shows the mapping overstates the WF mean by 4-7k and understates maxDD by 115-245k for this bracket family, so its 272k maxDD should be read as ~400-500k. On the v2 firm base (28-lot size-cost problem) the same rules improve the cell (5.5k -> 14-17k) simply by shrinking lots.

**6. Net.** Nothing passes gates a-d and best-of-F on the direct replay; nothing is live, no shadow, no frozen leads JSON, no DS2_VOL_SPEC.md. What the data does support: (i) the live locks, not the signal, set weekly SD, and the give-back arm does most of it; (ii) the week floor 8R and the 14-lot size are not earning their keep in WF; (iii) the live parameter cell is an in-sample pick that regresses to its neighbourhood; (iv) ATR20-scaled brackets lower SD but need a different execution (tight stops, market-order costs) before they could help. F_P: 3,352 + 6 (V1..V6) = 3,358.
