# DS3_GAPS_G3 — PRESS THE TREND DAY (GAPS item G3) — W-G3

Generated 2026-11-12 21:29Z. Shadow only, no PASS claim. Prereg autopilot/GAPS_G3_PREREG.md (sha line in DECISIONS.md). Hook code/th_g3/g3_hooks.py (outermost layer; rules in the prereg). Exact engine, one set per job, TP engine, tag GAPS. Each cell = base + ONE press rule, reference = its own base on the same months. Bases: **L = JN05W2** (43/43 months), **N = JN05W2_NOCUT** (10/43), J = JN05W2J (43/43), NJ = JN05W2J_NOCUT (6/43). Months done per G3 set: 35 sets, 138 month-runs.

**Caveat on every row:** the engine state cut fires in the engine but did NOT fire live on 11-11 (autopilot/DS3_P7_CUT_FIDELITY.md); the N / NJ rows (state cut off) are the live-realistic world. Cells judged first on the trend-week clause (best 5 AND best 20 weeks) and drawdown.

## Identity gate

G3_ID99_L (press trigger never true) on 202610 must equal JN05W2 (598 trades, net 25,943.82): DONE - see check below

Result: 598 trades net 25943.82 vs JN05W2 598 trades net 25943.82 -> **IDENTICAL**

## 0. Trend-week clause (first): base's best 5 and best 20 weeks kept, winning weeks turned losing, per window

| cell | base | window | top-5 base $ | top-5 cell $ | kept % | top-20 kept % | winning weeks turned losing | weeks |
|--|--|--|--|--|--|--|--|--|
| G3_R2_ct_L | JN05W2 | L1M | 2425 | 5386 | 222.1 | 222.1 | 0 of 2 | 4 |
| G3_R2_lf70_L | JN05W2 | L1M | 2425 | 8788 | 362.4 | 362.4 | 0 of 2 | 4 |
| G3_R3_tg90_L | JN05W2 | L1M | 2425 | 33576 | 1384.5 | 1384.5 | 0 of 2 | 4 |
| G3_S2_lf70_L | JN05W2 | L1M | 2425 | 11606 | 478.6 | 478.6 | 0 of 2 | 4 |
| G3_S3_lf75_L | JN05W2 | L1M | 2425 | 5241 | 216.1 | 216.1 | 0 of 2 | 4 |
| G3_S3_sz125_L | JN05W2 | L1M | 2425 | 5962 | 245.8 | 245.8 | 0 of 2 | 4 |
| G3_S3_tg90_L | JN05W2 | L1M | 2425 | 29500 | 1216.4 | 1216.4 | 0 of 2 | 4 |
| G3_S5_sz15_L | JN05W2 | L1M | 2425 | 31769 | 1310.0 | 1310.0 | 0 of 2 | 4 |
| G3_R2_ct_L | JN05W2 | L3M | 209474 | 215227 | 102.7 | 99.5 | 0 of 9 | 13 |
| G3_R2_lf70_L | JN05W2 | L3M | 209474 | 210238 | 100.4 | 103.0 | 0 of 9 | 13 |
| G3_R3_tg90_L | JN05W2 | L3M | 209474 | 228544 | 109.1 | 116.2 | 0 of 9 | 13 |
| G3_S2_lf70_L | JN05W2 | L3M | 209474 | 204838 | 97.8 | 102.2 | 0 of 9 | 13 |
| G3_S3_lf75_L | JN05W2 | L3M | 209474 | 202941 | 96.9 | 101.1 | 0 of 9 | 13 |
| G3_S3_sz125_L | JN05W2 | L3M | 209474 | 228873 | 109.3 | 106.2 | 0 of 9 | 13 |
| G3_S3_tg90_L | JN05W2 | L3M | 209474 | 141185 | 67.4 | 70.8 | 0 of 9 | 13 |
| G3_S5_sz15_L | JN05W2 | L3M | 209474 | 262393 | 125.3 | 119.1 | 0 of 9 | 13 |
| G3_R2_ct_L | JN05W2 | L6M | 337218 | 330527 | 98.0 | 102.4 | 0 of 19 | 26 |
| G3_R2_lf70_L | JN05W2 | L6M | 337218 | 342681 | 101.6 | 101.2 | 0 of 19 | 26 |
| G3_R3_tg90_L | JN05W2 | L6M | 337218 | 331321 | 98.3 | 99.0 | 0 of 19 | 26 |
| G3_S2_lf70_L | JN05W2 | L6M | 337218 | 319929 | 94.9 | 97.4 | 0 of 19 | 26 |
| G3_S3_lf75_L | JN05W2 | L6M | 337218 | 324783 | 96.3 | 97.9 | 0 of 19 | 26 |
| G3_S3_sz125_L | JN05W2 | L6M | 337218 | 313412 | 92.9 | 98.6 | 0 of 19 | 26 |
| G3_S3_tg90_L | JN05W2 | L6M | 337218 | 282152 | 83.7 | 79.7 | 1 of 19 | 26 |
| G3_S5_sz15_L | JN05W2 | L6M | 337218 | 310336 | 92.0 | 96.3 | 0 of 19 | 26 |

## 1. Windows (maxDD cut %, equal-mean cut %, d mean $/wk all weeks, carry week NOT dropped)

| cell | window | DD cut % | eq-mean cut % | d mean/wk | mean/wk | base mean/wk | months |
|--|--|--|--|--|--|--|--|
| G3_R2_ct_L | L1M | 0.0 | -2.6 | 740 | 1346 | 606 | 7 |
| G3_R2_ct_L | L3M | -2.2 | -4.8 | -80 | 15935 | 16015 | 7 |
| G3_R2_ct_L | L6M | -2.2 | -4.8 | -43 | 25094 | 25137 | 7 |
| G3_R2_lf70_L | L1M | -2.2 | 0.8 | 1591 | 2197 | 606 | 6 |
| G3_R2_lf70_L | L3M | -2.2 | 0.8 | 483 | 16498 | 16015 | 6 |
| G3_R2_lf70_L | L6M | -2.2 | 0.8 | 393 | 25530 | 25137 | 6 |
| G3_R3_tg90_L | L1M | 0.8 | -3.5 | 7788 | 8394 | 606 | 6 |
| G3_R3_tg90_L | L3M | -15.3 | -20.4 | 2597 | 18612 | 16015 | 6 |
| G3_R3_tg90_L | L6M | -15.3 | -20.4 | -352 | 24784 | 25137 | 6 |
| G3_S2_lf70_L | L1M | -2.2 | -3.4 | 2295 | 2902 | 606 | 6 |
| G3_S2_lf70_L | L3M | -2.2 | -3.4 | 346 | 16361 | 16015 | 6 |
| G3_S2_lf70_L | L6M | -2.2 | -3.4 | -685 | 24452 | 25137 | 6 |
| G3_S3_lf75_L | L1M | -1.0 | -0.9 | 704 | 1310 | 606 | 6 |
| G3_S3_lf75_L | L3M | -1.0 | -0.9 | 174 | 16189 | 16015 | 6 |
| G3_S3_lf75_L | L6M | -1.0 | -0.9 | -402 | 24735 | 25137 | 6 |
| G3_S3_sz125_L | L1M | -8.1 | -8.8 | 884 | 1490 | 606 | 6 |
| G3_S3_sz125_L | L3M | -8.1 | -8.8 | 987 | 17003 | 16015 | 6 |
| G3_S3_sz125_L | L6M | -8.1 | -8.8 | -725 | 24412 | 25137 | 6 |
| G3_S3_tg90_L | L1M | 31.1 | 16.3 | 6769 | 7375 | 606 | 6 |
| G3_S3_tg90_L | L3M | 9.1 | -10.4 | -4684 | 11331 | 16015 | 6 |
| G3_S3_tg90_L | L6M | 9.1 | -10.4 | -5678 | 19459 | 25137 | 6 |
| G3_S5_sz15_L | L1M | -12.7 | -20.9 | 7336 | 7942 | 606 | 6 |
| G3_S5_sz15_L | L3M | -12.7 | -20.9 | 3056 | 19071 | 16015 | 6 |
| G3_S5_sz15_L | L6M | -12.7 | -20.9 | -2575 | 22562 | 25137 | 6 |

## 3. acceptance_p7 and behavioural scorecard (cells with >= 6 months; partial sets count only covered sessions)

- G3_R2_ct_L: ACCEPT G3_R2_ct_L PASS fails=2/20
- G3_R2_lf70_L: ACCEPT G3_R2_lf70_L PASS fails=1/20
- G3_R3_tg90_L: ACCEPT G3_R3_tg90_L PASS fails=1/20
- G3_S2_lf70_L: ACCEPT G3_S2_lf70_L PASS fails=1/20
- G3_S3_lf75_L: ACCEPT G3_S3_lf75_L PASS fails=1/20
- G3_S3_sz125_L: ACCEPT G3_S3_sz125_L PASS fails=1/20
- G3_S3_tg90_L: ACCEPT G3_S3_tg90_L PASS fails=1/20
- G3_S5_sz15_L: ACCEPT G3_S5_sz15_L PASS fails=1/20

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
