# DS3_GAPS_G3 — PRESS THE TREND DAY (GAPS item G3) — W-G3

Generated 2026-11-13 00:01Z. Shadow only, no PASS claim. Prereg autopilot/GAPS_G3_PREREG.md (sha line in DECISIONS.md). Hook code/th_g3/g3_hooks.py (outermost layer; rules in the prereg). Exact engine, one set per job, TP engine, tag GAPS. Each cell = base + ONE press rule, reference = its own base on the same months. Bases: **L = JN05W2** (43/43 months), **N = JN05W2_NOCUT** (16/43), J = JN05W2J (43/43), NJ = JN05W2J_NOCUT (11/43). Months done per G3 set: 54 sets, 360 month-runs.

**Caveat on every row:** the engine state cut fires in the engine but did NOT fire live on 11-11 (autopilot/DS3_P7_CUT_FIDELITY.md); the N / NJ rows (state cut off) are the live-realistic world. Cells judged first on the trend-week clause (best 5 AND best 20 weeks) and drawdown.

## Identity gate

G3_ID99_L (press trigger never true) on 202610 must equal JN05W2 (598 trades, net 25,943.82): DONE - see check below

Result: 598 trades net 25943.82 vs JN05W2 598 trades net 25943.82 -> **IDENTICAL**

## 0. Trend-week clause (first): base's best 5 and best 20 weeks kept, winning weeks turned losing, per window

| cell | base | window | top-5 base $ | top-5 cell $ | kept % | top-20 kept % | winning weeks turned losing | weeks |
|--|--|--|--|--|--|--|--|--|
| G3_R2_ct_L | JN05W2 | HOLD | 340478 | 345415 | 101.5 | 105.0 | 2 of 37 | 52 |
| G3_R2_lf70_L | JN05W2 | HOLD | 340478 | 342504 | 100.6 | 101.2 | 0 of 37 | 52 |
| G3_S3_sz125_L | JN05W2 | HOLD | 340478 | 320978 | 94.3 | 100.7 | 1 of 37 | 52 |
| G3_S3_tg90_L | JN05W2 | HOLD | 340478 | 273229 | 80.2 | 86.9 | 3 of 37 | 52 |
| G3_S5_sz15_L | JN05W2 | HOLD | 340478 | 340785 | 100.1 | 97.6 | 0 of 37 | 52 |
| G3_R2_all_L | JN05W2 | L1M | 2425 | 12658 | 522.0 | 522.0 | 0 of 2 | 4 |
| G3_R2_ct_L | JN05W2 | L1M | 2425 | 5386 | 222.1 | 222.1 | 0 of 2 | 4 |
| G3_R2_lf70_L | JN05W2 | L1M | 2425 | 8788 | 362.4 | 362.4 | 0 of 2 | 4 |
| G3_R2_sz15_L | JN05W2 | L1M | 2425 | 18002 | 742.3 | 742.3 | 0 of 2 | 4 |
| G3_R2_tg90_L | JN05W2 | L1M | 2425 | 29509 | 1216.8 | 1216.8 | 0 of 2 | 4 |
| G3_R3_all_L | JN05W2 | L1M | 2425 | 38147 | 1573.0 | 1573.0 | 0 of 2 | 4 |
| G3_R3_ct_L | JN05W2 | L1M | 2425 | 5386 | 222.1 | 222.1 | 0 of 2 | 4 |
| G3_R3_lf70_L | JN05W2 | L1M | 2425 | 4268 | 176.0 | 176.0 | 0 of 2 | 4 |
| G3_R3_sz15_L | JN05W2 | L1M | 2425 | 29845 | 1230.6 | 1230.6 | 0 of 2 | 4 |
| G3_R3_sz15_N | JN05W2_NOCUT | L1M | -8485 | 12447 | -146.7 | -146.7 | 0 of 2 | 4 |
| G3_R3_tg90_L | JN05W2 | L1M | 2425 | 33576 | 1384.5 | 1384.5 | 0 of 2 | 4 |
| G3_R3_tg90_N | JN05W2_NOCUT | L1M | -8485 | 43421 | -511.7 | -511.7 | 0 of 2 | 4 |
| G3_S2_all_L | JN05W2 | L1M | 2425 | 32550 | 1342.2 | 1342.2 | 0 of 2 | 4 |
| G3_S2_ct_L | JN05W2 | L1M | 2425 | 17733 | 731.2 | 731.2 | 0 of 2 | 4 |
| G3_S2_ct_N | JN05W2_NOCUT | L1M | -8485 | 41343 | -487.2 | -487.2 | 0 of 2 | 4 |
| G3_S2_lf70_L | JN05W2 | L1M | 2425 | 11606 | 478.6 | 478.6 | 0 of 2 | 4 |
| G3_S2_sz15_L | JN05W2 | L1M | 2425 | 42175 | 1739.0 | 1739.0 | 0 of 2 | 4 |
| G3_S2_tg90_L | JN05W2 | L1M | 2425 | 3159 | 130.2 | 130.2 | 0 of 2 | 4 |
| G3_S3_all_L | JN05W2 | L1M | 2425 | 40069 | 1652.2 | 1652.2 | 0 of 2 | 4 |
| G3_S3_ct_L | JN05W2 | L1M | 2425 | 11897 | 490.5 | 490.5 | 0 of 2 | 4 |
| G3_S3_lf60_L | JN05W2 | L1M | 2425 | 5999 | 247.4 | 247.4 | 0 of 2 | 4 |
| G3_S3_lf70_L | JN05W2 | L1M | 2425 | 11606 | 478.6 | 478.6 | 0 of 2 | 4 |
| G3_S3_lf75_L | JN05W2 | L1M | 2425 | 5241 | 216.1 | 216.1 | 0 of 2 | 4 |
| G3_S3_sz125_L | JN05W2 | L1M | 2425 | 5962 | 245.8 | 245.8 | 0 of 2 | 4 |
| G3_S3_sz125_N | JN05W2_NOCUT | L1M | -8485 | -11346 | 133.7 | 133.7 | 0 of 2 | 4 |
| G3_S3_sz15_L | JN05W2 | L1M | 2425 | 31842 | 1313.0 | 1313.0 | 0 of 2 | 4 |
| G3_S3_sz20_L | JN05W2 | L1M | 2425 | 28557 | 1177.5 | 1177.5 | 0 of 2 | 4 |
| G3_S3_tg120_L | JN05W2 | L1M | 2425 | 24356 | 1004.3 | 1004.3 | 0 of 2 | 4 |
| G3_S3_tg75_L | JN05W2 | L1M | 2425 | 10575 | 436.0 | 436.0 | 0 of 2 | 4 |
| G3_S3_tg90_L | JN05W2 | L1M | 2425 | 29500 | 1216.4 | 1216.4 | 0 of 2 | 4 |
| G3_S5_all_L | JN05W2 | L1M | 2425 | 16116 | 664.5 | 664.5 | 0 of 2 | 4 |
| G3_S5_all_N | JN05W2_NOCUT | L1M | -8485 | 4882 | -57.5 | -57.5 | 0 of 2 | 4 |
| G3_S5_ct_L | JN05W2 | L1M | 2425 | 39899 | 1645.2 | 1645.2 | 0 of 2 | 4 |
| G3_S5_lf70_L | JN05W2 | L1M | 2425 | 13218 | 545.0 | 545.0 | 0 of 2 | 4 |
| G3_S5_sz15_L | JN05W2 | L1M | 2425 | 31769 | 1310.0 | 1310.0 | 0 of 2 | 4 |
| G3_S5_tg90_L | JN05W2 | L1M | 2425 | 20483 | 844.6 | 844.6 | 0 of 2 | 4 |
| G3_R2_all_L | JN05W2 | L3M | 209474 | 224299 | 107.1 | 89.6 | 1 of 9 | 13 |
| G3_R2_ct_L | JN05W2 | L3M | 209474 | 215227 | 102.7 | 99.5 | 0 of 9 | 13 |
| G3_R2_lf70_L | JN05W2 | L3M | 209474 | 210238 | 100.4 | 103.0 | 0 of 9 | 13 |
| G3_R2_sz15_L | JN05W2 | L3M | 209474 | 209155 | 99.8 | 85.1 | 1 of 9 | 13 |
| G3_R2_tg90_L | JN05W2 | L3M | 209474 | 231871 | 110.7 | 116.5 | 0 of 9 | 13 |
| G3_R3_all_L | JN05W2 | L3M | 209474 | 228844 | 109.2 | 123.9 | 0 of 9 | 13 |
| G3_R3_ct_L | JN05W2 | L3M | 209474 | 214746 | 102.5 | 101.9 | 0 of 9 | 13 |
| G3_R3_lf70_L | JN05W2 | L3M | 209474 | 217044 | 103.6 | 104.1 | 0 of 9 | 13 |
| G3_R3_sz15_L | JN05W2 | L3M | 209474 | 213707 | 102.0 | 103.4 | 0 of 9 | 13 |
| G3_R3_sz15_N | JN05W2_NOCUT | L3M | 219873 | 248534 | 113.0 | 119.9 | 0 of 8 | 13 |
| G3_R3_tg90_L | JN05W2 | L3M | 209474 | 228544 | 109.1 | 116.2 | 0 of 9 | 13 |
| G3_R3_tg90_N | JN05W2_NOCUT | L3M | 219873 | 218549 | 99.4 | 110.1 | 0 of 8 | 13 |
| G3_S2_all_L | JN05W2 | L3M | 209474 | 192407 | 91.9 | 91.1 | 0 of 9 | 13 |
| G3_S2_ct_L | JN05W2 | L3M | 209474 | 231830 | 110.7 | 119.2 | 0 of 9 | 13 |
| G3_S2_ct_N | JN05W2_NOCUT | L3M | 219873 | 250333 | 113.9 | 146.6 | 0 of 8 | 13 |
| G3_S2_lf70_L | JN05W2 | L3M | 209474 | 204838 | 97.8 | 102.2 | 0 of 9 | 13 |
| G3_S2_sz15_L | JN05W2 | L3M | 209474 | 269437 | 128.6 | 121.4 | 0 of 9 | 13 |
| G3_S2_tg90_L | JN05W2 | L3M | 209474 | 131341 | 62.7 | 59.6 | 0 of 9 | 13 |
| G3_S3_all_L | JN05W2 | L3M | 209474 | 194417 | 92.8 | 89.5 | 1 of 9 | 13 |
| G3_S3_ct_L | JN05W2 | L3M | 209474 | 211689 | 101.1 | 109.3 | 0 of 9 | 13 |
| G3_S3_lf60_L | JN05W2 | L3M | 209474 | 206374 | 98.5 | 99.7 | 0 of 9 | 13 |
| G3_S3_lf70_L | JN05W2 | L3M | 209474 | 204838 | 97.8 | 102.2 | 0 of 9 | 13 |
| G3_S3_lf75_L | JN05W2 | L3M | 209474 | 202941 | 96.9 | 101.1 | 0 of 9 | 13 |
| G3_S3_sz125_L | JN05W2 | L3M | 209474 | 228873 | 109.3 | 106.2 | 0 of 9 | 13 |
| G3_S3_sz15_L | JN05W2 | L3M | 209474 | 256308 | 122.4 | 112.1 | 0 of 9 | 13 |
| G3_S3_sz20_L | JN05W2 | L3M | 209474 | 235385 | 112.4 | 106.3 | 0 of 9 | 13 |
| G3_S3_tg120_L | JN05W2 | L3M | 209474 | 149394 | 71.3 | 77.0 | 0 of 9 | 13 |
| G3_S3_tg75_L | JN05W2 | L3M | 209474 | 137841 | 65.8 | 67.7 | 0 of 9 | 13 |
| G3_S3_tg90_L | JN05W2 | L3M | 209474 | 141185 | 67.4 | 70.8 | 0 of 9 | 13 |
| G3_S5_all_L | JN05W2 | L3M | 209474 | 192757 | 92.0 | 86.2 | 0 of 9 | 13 |
| G3_S5_all_N | JN05W2_NOCUT | L3M | 219873 | 181208 | 82.4 | 90.4 | 0 of 8 | 13 |
| G3_S5_ct_L | JN05W2 | L3M | 209474 | 238607 | 113.9 | 124.3 | 0 of 9 | 13 |
| G3_S5_lf70_L | JN05W2 | L3M | 209474 | 204838 | 97.8 | 102.7 | 0 of 9 | 13 |
| G3_S5_sz15_L | JN05W2 | L3M | 209474 | 262393 | 125.3 | 119.1 | 0 of 9 | 13 |
| G3_S5_tg90_L | JN05W2 | L3M | 209474 | 165282 | 78.9 | 84.7 | 0 of 9 | 13 |
| G3_R2_all_L | JN05W2 | L6M | 337218 | 325139 | 96.4 | 94.8 | 2 of 19 | 26 |
| G3_R2_ct_L | JN05W2 | L6M | 337218 | 330527 | 98.0 | 102.4 | 0 of 19 | 26 |
| G3_R2_lf70_L | JN05W2 | L6M | 337218 | 342681 | 101.6 | 101.2 | 0 of 19 | 26 |
| G3_R2_sz15_L | JN05W2 | L6M | 337218 | 317417 | 94.1 | 97.4 | 1 of 19 | 26 |
| G3_R2_tg90_L | JN05W2 | L6M | 337218 | 312264 | 92.6 | 92.8 | 1 of 19 | 26 |
| G3_R3_all_L | JN05W2 | L6M | 337218 | 343177 | 101.8 | 105.0 | 1 of 19 | 26 |
| G3_R3_ct_L | JN05W2 | L6M | 337218 | 335015 | 99.3 | 101.0 | 0 of 19 | 26 |
| G3_R3_lf70_L | JN05W2 | L6M | 337218 | 342376 | 101.5 | 101.5 | 0 of 19 | 26 |
| G3_R3_sz15_L | JN05W2 | L6M | 337218 | 327787 | 97.2 | 102.7 | 0 of 19 | 26 |
| G3_R3_tg90_L | JN05W2 | L6M | 337218 | 331321 | 98.3 | 99.0 | 0 of 19 | 26 |
| G3_S2_all_L | JN05W2 | L6M | 337218 | 284378 | 84.3 | 92.2 | 0 of 19 | 26 |
| G3_S2_ct_L | JN05W2 | L6M | 337218 | 327688 | 97.2 | 102.0 | 0 of 19 | 26 |
| G3_S2_lf70_L | JN05W2 | L6M | 337218 | 319929 | 94.9 | 97.4 | 0 of 19 | 26 |
| G3_S2_sz15_L | JN05W2 | L6M | 337218 | 319115 | 94.6 | 98.9 | 0 of 19 | 26 |
| G3_S2_tg90_L | JN05W2 | L6M | 337218 | 291394 | 86.4 | 79.4 | 1 of 19 | 26 |
| G3_S3_all_L | JN05W2 | L6M | 337218 | 271902 | 80.6 | 87.6 | 1 of 19 | 26 |
| G3_S3_ct_L | JN05W2 | L6M | 337218 | 320749 | 95.1 | 101.8 | 0 of 19 | 26 |
| G3_S3_lf60_L | JN05W2 | L6M | 337218 | 331695 | 98.4 | 99.3 | 0 of 19 | 26 |
| G3_S3_lf70_L | JN05W2 | L6M | 337218 | 319929 | 94.9 | 97.4 | 0 of 19 | 26 |
| G3_S3_lf75_L | JN05W2 | L6M | 337218 | 324783 | 96.3 | 97.9 | 0 of 19 | 26 |
| G3_S3_sz125_L | JN05W2 | L6M | 337218 | 313412 | 92.9 | 98.6 | 0 of 19 | 26 |
| G3_S3_sz15_L | JN05W2 | L6M | 337218 | 319845 | 94.8 | 97.4 | 0 of 19 | 26 |
| G3_S3_sz20_L | JN05W2 | L6M | 337218 | 318106 | 94.3 | 97.0 | 0 of 19 | 26 |
| G3_S3_tg120_L | JN05W2 | L6M | 337218 | 245248 | 72.7 | 77.6 | 1 of 19 | 26 |
| G3_S3_tg75_L | JN05W2 | L6M | 337218 | 318540 | 94.5 | 86.7 | 0 of 19 | 26 |
| G3_S3_tg90_L | JN05W2 | L6M | 337218 | 282152 | 83.7 | 79.7 | 1 of 19 | 26 |
| G3_S5_all_L | JN05W2 | L6M | 337218 | 243777 | 72.3 | 75.4 | 1 of 19 | 26 |
| G3_S5_ct_L | JN05W2 | L6M | 337218 | 329136 | 97.6 | 103.2 | 0 of 19 | 26 |
| G3_S5_lf70_L | JN05W2 | L6M | 337218 | 319929 | 94.9 | 97.3 | 0 of 19 | 26 |
| G3_S5_sz15_L | JN05W2 | L6M | 337218 | 310336 | 92.0 | 96.3 | 0 of 19 | 26 |
| G3_S5_tg90_L | JN05W2 | L6M | 337218 | 268206 | 79.5 | 82.8 | 1 of 19 | 26 |

## 1. Windows (maxDD cut %, equal-mean cut %, d mean $/wk all weeks, carry week NOT dropped)

| cell | window | DD cut % | eq-mean cut % | d mean/wk | mean/wk | base mean/wk | months |
|--|--|--|--|--|--|--|--|
| G3_R2_all_L | L1M | -38.7 | -47.6 | 2558 | 3165 | 606 | 6 |
| G3_R2_all_L | L3M | -96.5 | -109.1 | -1663 | 14352 | 16015 | 6 |
| G3_R2_all_L | L6M | -96.5 | -109.1 | -3558 | 21579 | 25137 | 6 |
| G3_R2_ct_L | HOLD | -4.3 | -7.0 | 833 | 18323 | 17489 | 13 |
| G3_R2_ct_L | L1M | 0.0 | -2.6 | 740 | 1346 | 606 | 13 |
| G3_R2_ct_L | L3M | -2.2 | -4.8 | -80 | 15935 | 16015 | 13 |
| G3_R2_ct_L | L6M | -2.2 | -4.8 | -43 | 25094 | 25137 | 13 |
| G3_R2_lf70_L | HOLD | 1.1 | 4.0 | 444 | 17934 | 17489 | 12 |
| G3_R2_lf70_L | L1M | -2.2 | 0.8 | 1591 | 2197 | 606 | 12 |
| G3_R2_lf70_L | L3M | -2.2 | 0.8 | 483 | 16498 | 16015 | 12 |
| G3_R2_lf70_L | L6M | -2.2 | 0.8 | 393 | 25530 | 25137 | 12 |
| G3_R2_sz15_L | L1M | -27.6 | -35.7 | 3894 | 4501 | 606 | 6 |
| G3_R2_sz15_L | L3M | -27.6 | -35.7 | -2390 | 13625 | 16015 | 6 |
| G3_R2_sz15_L | L6M | -27.6 | -35.7 | -602 | 24535 | 25137 | 6 |
| G3_R2_tg90_L | L1M | -0.0 | -3.5 | 6771 | 7377 | 606 | 6 |
| G3_R2_tg90_L | L3M | -5.4 | -9.1 | 2638 | 18654 | 16015 | 6 |
| G3_R2_tg90_L | L6M | -5.4 | -9.1 | -2677 | 22460 | 25137 | 6 |
| G3_R3_all_L | L1M | -38.7 | -40.8 | 8931 | 9537 | 606 | 7 |
| G3_R3_all_L | L3M | -38.7 | -40.8 | 3820 | 19835 | 16015 | 7 |
| G3_R3_all_L | L6M | -38.7 | -40.8 | 1000 | 26137 | 25137 | 7 |
| G3_R3_ct_L | L1M | 0.0 | -1.5 | 740 | 1346 | 606 | 6 |
| G3_R3_ct_L | L3M | 0.0 | -1.5 | 306 | 16321 | 16015 | 6 |
| G3_R3_ct_L | L6M | 0.0 | -1.5 | 23 | 25160 | 25137 | 6 |
| G3_R3_lf70_L | L1M | -2.2 | 1.1 | 461 | 1067 | 606 | 8 |
| G3_R3_lf70_L | L3M | -2.2 | 1.1 | 659 | 16674 | 16015 | 8 |
| G3_R3_lf70_L | L6M | -2.2 | 1.1 | 466 | 25603 | 25137 | 8 |
| G3_R3_sz15_L | L1M | -20.1 | -20.3 | 6855 | 7461 | 606 | 9 |
| G3_R3_sz15_L | L3M | -20.1 | -20.3 | 544 | 16559 | 16015 | 9 |
| G3_R3_sz15_L | L6M | -20.1 | -20.3 | 1010 | 26147 | 25137 | 9 |
| G3_R3_sz15_N | L1M | -43.1 | 28.0 | 5233 | 3112 | -2121 | 6 |
| G3_R3_sz15_N | L3M | -77.9 | 10.5 | 2880 | 17339 | 14459 | 6 |
| G3_R3_tg90_L | L1M | 0.8 | -3.5 | 7788 | 8394 | 606 | 10 |
| G3_R3_tg90_L | L3M | -15.3 | -20.4 | 2597 | 18612 | 16015 | 10 |
| G3_R3_tg90_L | L6M | -15.3 | -20.4 | -352 | 24784 | 25137 | 10 |
| G3_R3_tg90_N | L1M | 58.7 | 76.6 | 12976 | 10855 | -2121 | 6 |
| G3_R3_tg90_N | L3M | -90.3 | -7.9 | 1462 | 15921 | 14459 | 6 |
| G3_S2_all_L | L1M | -39.0 | -51.4 | 7531 | 8138 | 606 | 6 |
| G3_S2_all_L | L3M | -61.0 | -75.5 | -1418 | 14597 | 16015 | 6 |
| G3_S2_all_L | L6M | -61.0 | -75.5 | -3422 | 21715 | 25137 | 6 |
| G3_S2_ct_L | L1M | -30.0 | -24.4 | 3827 | 4433 | 606 | 8 |
| G3_S2_ct_L | L3M | -30.0 | -24.4 | 3078 | 19093 | 16015 | 8 |
| G3_S2_ct_L | L6M | -30.0 | -24.4 | 65 | 25202 | 25137 | 8 |
| G3_S2_ct_N | L1M | -9.9 | 61.6 | 12457 | 10336 | -2121 | 6 |
| G3_S2_ct_N | L3M | -28.9 | 55.0 | 6744 | 21203 | 14459 | 6 |
| G3_S2_lf70_L | L1M | -2.2 | -3.4 | 2295 | 2902 | 606 | 10 |
| G3_S2_lf70_L | L3M | -2.2 | -3.4 | 346 | 16361 | 16015 | 10 |
| G3_S2_lf70_L | L6M | -2.2 | -3.4 | -685 | 24452 | 25137 | 10 |
| G3_S2_sz15_L | L1M | -17.9 | -31.5 | 9937 | 10544 | 606 | 7 |
| G3_S2_sz15_L | L3M | -17.9 | -31.5 | 3434 | 19449 | 16015 | 7 |
| G3_S2_sz15_L | L6M | -17.9 | -31.5 | -1435 | 23701 | 25137 | 7 |
| G3_S2_tg90_L | L1M | -0.9 | -29.3 | 183 | 790 | 606 | 6 |
| G3_S2_tg90_L | L3M | -5.2 | -34.8 | -6476 | 9539 | 16015 | 6 |
| G3_S2_tg90_L | L6M | -5.2 | -34.8 | -6682 | 18455 | 25137 | 6 |
| G3_S3_all_L | L1M | -1.0 | -14.9 | 9411 | 10017 | 606 | 10 |
| G3_S3_all_L | L3M | -73.4 | -97.3 | -1688 | 14327 | 16015 | 10 |
| G3_S3_all_L | L6M | -73.4 | -97.3 | -4287 | 20850 | 25137 | 10 |
| G3_S3_ct_L | L1M | -43.9 | -54.0 | 2368 | 2974 | 606 | 6 |
| G3_S3_ct_L | L3M | -43.9 | -54.0 | 1489 | 17504 | 16015 | 6 |
| G3_S3_ct_L | L6M | -43.9 | -54.0 | -467 | 24670 | 25137 | 6 |
| G3_S3_lf60_L | L1M | -3.7 | -3.4 | 894 | 1500 | 606 | 8 |
| G3_S3_lf60_L | L3M | -3.7 | -3.4 | -53 | 15962 | 16015 | 8 |
| G3_S3_lf60_L | L6M | -3.7 | -3.4 | -199 | 24938 | 25137 | 8 |
| G3_S3_lf70_L | L1M | -2.2 | -3.3 | 2295 | 2902 | 606 | 10 |
| G3_S3_lf70_L | L3M | -2.2 | -3.3 | 346 | 16361 | 16015 | 10 |
| G3_S3_lf70_L | L6M | -2.2 | -3.3 | -657 | 24480 | 25137 | 10 |
| G3_S3_lf75_L | L1M | -1.0 | -0.9 | 704 | 1310 | 606 | 10 |
| G3_S3_lf75_L | L3M | -1.0 | -0.9 | 174 | 16189 | 16015 | 10 |
| G3_S3_lf75_L | L6M | -1.0 | -0.9 | -402 | 24735 | 25137 | 10 |
| G3_S3_sz125_L | HOLD | 3.4 | 2.7 | -160 | 17330 | 17489 | 12 |
| G3_S3_sz125_L | L1M | -8.1 | -8.8 | 884 | 1490 | 606 | 12 |
| G3_S3_sz125_L | L3M | -8.1 | -8.8 | 987 | 17003 | 16015 | 12 |
| G3_S3_sz125_L | L6M | -8.1 | -8.8 | -725 | 24412 | 25137 | 12 |
| G3_S3_sz125_N | L1M | -21.4 | 64.3 | -715 | -2836 | -2121 | 6 |
| G3_S3_sz15_L | L1M | -14.9 | -23.2 | 7354 | 7961 | 606 | 11 |
| G3_S3_sz15_L | L3M | -18.1 | -26.6 | 1940 | 17955 | 16015 | 11 |
| G3_S3_sz15_L | L6M | -18.1 | -26.6 | -2262 | 22875 | 25137 | 11 |
| G3_S3_sz20_L | L1M | -11.1 | -17.0 | 6533 | 7139 | 606 | 7 |
| G3_S3_sz20_L | L3M | -25.8 | -32.6 | 1017 | 17032 | 16015 | 7 |
| G3_S3_sz20_L | L6M | -25.8 | -32.6 | -2442 | 22695 | 25137 | 7 |
| G3_S3_tg120_L | L1M | 11.7 | -17.8 | 5483 | 6089 | 606 | 10 |
| G3_S3_tg120_L | L3M | -4.4 | -39.4 | -3682 | 12334 | 16015 | 10 |
| G3_S3_tg120_L | L6M | -4.4 | -39.4 | -7280 | 17857 | 25137 | 10 |
| G3_S3_tg75_L | L1M | 10.0 | -3.7 | 2037 | 2644 | 606 | 6 |
| G3_S3_tg75_L | L3M | 2.6 | -12.2 | -5178 | 10837 | 16015 | 6 |
| G3_S3_tg75_L | L6M | 2.6 | -12.2 | -4135 | 21002 | 25137 | 6 |
| G3_S3_tg90_L | HOLD | 10.4 | -8.8 | -1812 | 15677 | 17489 | 12 |
| G3_S3_tg90_L | L1M | 31.1 | 16.3 | 6769 | 7375 | 606 | 12 |
| G3_S3_tg90_L | L3M | 9.1 | -10.4 | -4684 | 11331 | 16015 | 12 |
| G3_S3_tg90_L | L6M | 9.1 | -10.4 | -5678 | 19459 | 25137 | 12 |
| G3_S5_all_L | L1M | -22.6 | -66.1 | 3423 | 4029 | 606 | 8 |
| G3_S5_all_L | L3M | -64.0 | -122.2 | -2207 | 13808 | 16015 | 8 |
| G3_S5_all_L | L6M | -64.0 | -122.2 | -7990 | 17147 | 25137 | 8 |
| G3_S5_all_N | L1M | -66.5 | 1.5 | 3342 | 1220 | -2121 | 6 |
| G3_S5_all_N | L3M | -66.5 | 1.5 | -1381 | 13078 | 14459 | 6 |
| G3_S5_ct_L | L1M | -7.2 | -9.5 | 9368 | 9975 | 606 | 10 |
| G3_S5_ct_L | L3M | -7.2 | -9.5 | 3899 | 19914 | 16015 | 10 |
| G3_S5_ct_L | L6M | -7.2 | -9.5 | 516 | 25653 | 25137 | 10 |
| G3_S5_lf70_L | L1M | 2.3 | 1.2 | 2698 | 3305 | 606 | 6 |
| G3_S5_lf70_L | L3M | 2.3 | 1.2 | 426 | 16441 | 16015 | 6 |
| G3_S5_lf70_L | L6M | 2.3 | 1.2 | -664 | 24473 | 25137 | 6 |
| G3_S5_sz15_L | HOLD | 6.2 | -0.7 | -660 | 16830 | 17489 | 12 |
| G3_S5_sz15_L | L1M | -12.7 | -20.9 | 7336 | 7942 | 606 | 12 |
| G3_S5_sz15_L | L3M | -12.7 | -20.9 | 3056 | 19071 | 16015 | 12 |
| G3_S5_sz15_L | L6M | -12.7 | -20.9 | -2575 | 22562 | 25137 | 12 |
| G3_S5_tg90_L | L1M | 8.7 | -8.0 | 4514 | 5121 | 606 | 11 |
| G3_S5_tg90_L | L3M | 8.7 | -8.0 | -2455 | 13560 | 16015 | 11 |
| G3_S5_tg90_L | L6M | 8.7 | -8.0 | -4894 | 20243 | 25137 | 11 |

## 3. acceptance_p7 and behavioural scorecard (cells with >= 6 months; partial sets count only covered sessions)

- G3_R2_all_L: ACCEPT G3_R2_all_L PASS fails=1/20
- G3_R2_ct_L: ACCEPT G3_R2_ct_L PASS fails=2/20
- G3_R2_lf70_L: ACCEPT G3_R2_lf70_L PASS fails=1/20
- G3_R2_sz15_L: ACCEPT G3_R2_sz15_L PASS fails=1/20
- G3_R2_tg90_L: ACCEPT G3_R2_tg90_L PASS fails=1/20
- G3_R3_all_L: ACCEPT G3_R3_all_L PASS fails=1/20
- G3_R3_ct_L: ACCEPT G3_R3_ct_L PASS fails=1/20
- G3_R3_lf70_L: ACCEPT G3_R3_lf70_L PASS fails=1/20
- G3_R3_sz15_L: ACCEPT G3_R3_sz15_L PASS fails=1/20
- G3_R3_sz15_N: ACCEPT G3_R3_sz15_N PASS fails=1/20
- G3_R3_tg90_L: ACCEPT G3_R3_tg90_L PASS fails=1/20
- G3_R3_tg90_N: ACCEPT G3_R3_tg90_N PASS fails=1/20
- G3_S2_all_L: ACCEPT G3_S2_all_L PASS fails=1/20
- G3_S2_ct_L: ACCEPT G3_S2_ct_L PASS fails=1/20
- G3_S2_ct_N: ACCEPT G3_S2_ct_N FAIL fails=3/20
- G3_S2_lf70_L: ACCEPT G3_S2_lf70_L PASS fails=1/20
- G3_S2_sz15_L: ACCEPT G3_S2_sz15_L PASS fails=1/20
- G3_S2_tg90_L: ACCEPT G3_S2_tg90_L PASS fails=1/20
- G3_S3_all_L: ACCEPT G3_S3_all_L PASS fails=1/20
- G3_S3_ct_L: ACCEPT G3_S3_ct_L PASS fails=1/20
- G3_S3_lf60_L: ACCEPT G3_S3_lf60_L PASS fails=1/20
- G3_S3_lf70_L: ACCEPT G3_S3_lf70_L PASS fails=1/20
- G3_S3_lf75_L: ACCEPT G3_S3_lf75_L PASS fails=1/20
- G3_S3_sz125_L: ACCEPT G3_S3_sz125_L PASS fails=1/20
- G3_S3_sz125_N: ACCEPT G3_S3_sz125_N PASS fails=1/20
- G3_S3_sz15_L: ACCEPT G3_S3_sz15_L PASS fails=1/20
- G3_S3_sz20_L: ACCEPT G3_S3_sz20_L PASS fails=1/20
- G3_S3_tg120_L: ACCEPT G3_S3_tg120_L PASS fails=1/20
- G3_S3_tg75_L: ACCEPT G3_S3_tg75_L PASS fails=1/20
- G3_S3_tg90_L: ACCEPT G3_S3_tg90_L PASS fails=1/20
- G3_S5_all_L: ACCEPT G3_S5_all_L PASS fails=1/20
- G3_S5_all_N: ACCEPT G3_S5_all_N PASS fails=1/20
- G3_S5_ct_L: ACCEPT G3_S5_ct_L PASS fails=1/20
- G3_S5_lf70_L: ACCEPT G3_S5_lf70_L PASS fails=1/20
- G3_S5_sz15_L: ACCEPT G3_S5_sz15_L PASS fails=1/20
- G3_S5_tg90_L: ACCEPT G3_S5_tg90_L PASS fails=1/20

## 4. Descriptive first-order screen on JN05W2's own L6M trades (history UNMODIFIED; 4,169 trades, 26 weeks; only a prior, exact is the verdict)

For each trigger: entries taken while the press is on, same-side as the press vs counter-trend, their net P&L (JN05W2 as run), and the rough change a rule would make (x1.5 size on same-side = +0.5 x same-side net; skip counter-trend = - counter-trend net).

| trig   |   n_all |   n_same |   n_ct |   same_net |   same_mean |   same_win |   ct_net |   ct_mean |   ct_win |   est_x15 |   est_skipct |   n_weeks |
|:-------|--------:|---------:|-------:|-----------:|------------:|-----------:|---------:|----------:|---------:|----------:|-------------:|----------:|
| S2     |    4169 |     1403 |    687 |   38494.3  |       27.44 |       0.4  | 35755.6  |     52.05 |     0.42 |  19247.1  |    -35755.6  |        26 |
| S3     |    4169 |     1315 |    625 |   45548.9  |       34.64 |       0.4  | 38353.9  |     61.37 |     0.42 |  22774.4  |    -38353.9  |        26 |
| S5     |    4169 |     1125 |    535 |   21786.3  |       19.37 |       0.4  | 46072.8  |     86.12 |     0.43 |  10893.2  |    -46072.8  |        26 |
| R2     |    4169 |      951 |    100 |    4820.08 |        5.07 |       0.41 |  4591.78 |     45.92 |     0.47 |   2410.04 |     -4591.78 |        26 |
| R3     |    4169 |      609 |     64 |   20247.9  |       33.25 |       0.42 |  4675.28 |     73.05 |     0.44 |  10124    |     -4675.28 |        26 |

Reading: counter-trend entries during the press are net winners (mean $45-86 vs same-side $5-35), so "skip counter-trend" is negative on its face; sizing same-side entries is the only positive prior and is modest (about +$0.4-0.9k/wk at x1.5 over 26 weeks).

## 5. R at the cell's lots vs fixed dollars (transfer to the user's lots)

Triggers use R fixed = $1,200 (60 pts x $20 x 1 lot). At the user's lots (K7 4, M7 4, U7 7, P7 12/7/7, H7 7, A7 2; caps x1.75) the same 2R/3R/5R lines correspond to 1.75x the dollars if R is lot-scaled; the run triggers (R2/R3: 2 or 3 consecutive same-side Target winners), the 90/75/120-point targets, the give-back keep fractions and the size multiples transfer unchanged. The +5R day-profit cap and the 2R give-back arm are per book in R of that book's base lots, so they scale with lots automatically.

## 6. Live weeks replay

Frozen week (11-02..05) and 11-09..11: the 202611 month (hist day files, state arrays, TP cache) was built by W-T at 13:52Z; the survivors replay uses sets named FW_*. G3 replay of the frozen week for promoted cells is queued behind the L6M/HOLD rows (not run yet). 11-12 raw data exists only to ~08:00Z (Databento licence lag).

## 7. v1.9-style spec

Written only for cells that survive (none yet).
