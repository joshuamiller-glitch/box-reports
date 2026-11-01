# DS3_BETTER_BASE - the D7 v1.0d base as a daily-series engine, tied out to the Sunday composite (BASE-1, T-BETTER, 2026-11-01 15:41Z). POST-HOC / CONSISTENCY LABELS, NO PASS CLAIM

Capped 20260206, UNTOUCHED never read, no post-cap file opened. Engine `l2vast/ds3/code/d7base/d7lib.py` on `oneconv/oc_lib.py` + `sundaystack2/ss2_lib.py` (both unchanged; hooks live in d7lib). Outputs `l2vast/ds3/out/d7base/` (README.md = API). Prereg `l2vast/ds3/prereg/BASE1_prereg.md` sha256 8129f1779c76737707db513fea1460deca476ec4cc97de3047f0ae8624b8dd5a (in DECISIONS.md before any statistic beyond the tie-out). Units: $k per week unless stated; windows L3M 14 / L6M 28 / HOLD 32 / PRE 75 / X' 44 / ALL 149 weeks; a risk cell reads `mean / maxDD / weekly SD` (maxDD = weekly-cumulative peak-to-trough); worst-20 = sum of the 20 worst weeks (tail windows only); Calmar = mean/maxDD; MDE = 2.8 x SE (level: of the weekly mean; delta: of the paired weekly difference), `*` = beyond MDE.

## Page 1

**Plain sentence.** The engine reproduces the Sunday composite and every stored series I could reach to 0.00 $/day (19 checks, table 1), and with the D7-only pieces switched on it gives the base numbers below. **The base as literally mapped (both TH-L2 rules simulated as described in section 4) has L6M mean 18.2k with maxDD 84.8k; the same base without the two TH-L2 rules has 48.9k with maxDD 29.9k (Sunday composite 41.1k / 22.9k). The TH-L2 mapping is therefore the single largest assumption in the base and the part most in need of the user's confirmation (question in MORNING.md).** Every other D7 piece moves the L6M mean by less than its MDE (table 3). All of it is post-hoc on windows that were looked at.

### Table 1 - TIE-OUT (all D7-only pieces switched off = `d7lib.TIE`; max |engine - stored| per day over 745 label days)

| check | stored series | max abs diff $/day | L6M level $k (stored) |
|---|---|---|---|
| COMP6 parity lock off | oc_res / onset / eint1dd / l2cut pkl | 0.00 | 41.137 |
| COMP6 parity lock 12 | oc_res / onset / eint1dd / l2cut pkl | 0.00 | 32.281 |
| COMP6 parity lock 20 | oc_res / onset / eint1dd / l2cut pkl | 0.00 | 34.837 |
| COMP6 parity lock 30 | oc_res / onset / eint1dd / l2cut pkl | 0.00 | 38.361 |
| COMP6 parity 12R m0=0.5 | oc_res / onset / eint1dd / l2cut pkl | 0.00 | 32.525 |
| COMP6 slip 0.45 | oc_res / onset / eint1dd / l2cut pkl | 0.00 | 40.665 |
| ON set parity lock off | oc_res / onset / eint1dd / l2cut pkl | 0.00 | 22.225 |
| ON set parity lock 12 | oc_res / onset / eint1dd / l2cut pkl | 0.00 | 16.280 |
| ON set parity lock 20 | oc_res / onset / eint1dd / l2cut pkl | 0.00 | 19.984 |
| ON set parity lock 30 | oc_res / onset / eint1dd / l2cut pkl | 0.00 | 22.225 |
| ON+ER(P6,K6) parity lock off | oc_res / onset / eint1dd / l2cut pkl | 0.00 | 31.811 |
| ON set join 2.45 | oc_res / onset / eint1dd / l2cut pkl | 0.00 | 20.880 |
| EF-2 composite HM_skipBot3_sig_slope A | oc_res / onset / eint1dd / l2cut pkl | 0.00 | 40.158 |
| EF-2 composite KB_skipTop3_sig_st1_dist_atr A | oc_res / onset / eint1dd / l2cut pkl | 0.00 | 41.265 |
| EF-2 composite PE_sizeHi A (full 1.5/0.5) | oc_res / onset / eint1dd / l2cut pkl | 0.00 | 43.300 |
| AS-IS unlocked (join 2.45) | oc_res / onset / eint1dd / l2cut pkl | 0.00 | 21.715 |
| ON set C1 delta vs as-is L6M ($k, MDE) | derived | - | ON set C1 delta vs as-is L6M = +0.5 (9.8) $k (DS3_ON_SET: +0.5 (9.8)) |
| AS-IS + L2SL U1 (A30 w5 mult20 newext0) vs A5 real_U1 | oc_res / onset / eint1dd / l2cut pkl | 0.00 | 15.760 |
| AS-IS + L2SL U3 (mult100) vs A5 real_U3 | oc_res / onset / eint1dd / l2cut pkl | 0.00 | 15.442 |

The Sunday composite C1 level (lock off) L3M/L6M/HOLD/PRE/X' = 34.4 / 41.1 / 38.6 / 23.1 / 8.0 (table 2 last row, DS3_ONE_CONVENTION table A2) and the 12R/20R/30R rows (32.3 / 34.8 / 38.4 L6M) tie exactly. The EF-2 rule rows tie the eint1dd composite series; the as-is + L2SL U1/U3 rows tie the A5 exact-engine series, which is the check on the exit-injection hook.

### Table 2 - the base risk line (mean / maxDD / SD, $k per week), lock OFF headline, with the combined lock switches

**BASE-literal = D7 v1.0d as stated, both TH-L2 rules simulated as mapped:**

| row | L3M | L6M | HOLD | PRE | X' | ALL |
|---|---|---|---|---|---|---|
| BASE | 15.1 / 84.8 / 51.1 | 18.2 / 84.8 / 39.6 | 18.2 / 84.8 / 42.6 | 14.1 / 190.7 / 46.7 | 5.2 / 126.5 / 27.2 | 12.5 / 190.7 / 41.4 |
| BASE lock 12R | 12.1 / 72.1 / 45.4 | 16.1 / 72.1 / 36.5 | 16.8 / 72.1 / 39.8 | 9.2 / 191.5 / 41.5 | 4.6 / 113.8 / 26.1 | 9.6 / 191.5 / 37.6 |
| BASE lock 20R | 16.0 / 82.4 / 47.0 | 17.5 / 82.4 / 37.9 | 17.3 / 82.4 / 41.5 | 9.5 / 193.9 / 45.1 | 3.8 / 110.0 / 26.9 | 9.6 / 193.9 / 40.2 |
| BASE lock 30R | 17.1 / 53.4 / 46.7 | 19.2 / 53.4 / 36.8 | 18.9 / 67.7 / 40.7 | 13.4 / 190.3 / 45.8 | 5.3 / 112.6 / 26.9 | 12.3 / 190.3 / 40.4 |
| TIE = Sunday composite (all D7-only off, parity) | 34.4 / 21.4 / 44.7 | 41.1 / 22.9 / 42.7 | 38.6 / 97.0 / 51.8 | 23.1 / 241.2 / 55.7 | 8.0 / 120.5 / 32.6 | 22.3 / 241.2 / 50.3 |

Worst-20 ($k, sum of the 20 worst weeks) PRE / X' / ALL: BASE: -759 / -392 / -957; TIE = Sunday composite (all D7-only off, parity): -875 / -420 / -1098.

**BASE-noTH = the same base with the two TH-L2 rules off (every other D7 piece on):**

| row | L3M | L6M | HOLD | PRE | X' | ALL |
|---|---|---|---|---|---|---|
| BASE | 40.7 / 29.9 / 52.9 | 48.9 / 29.9 / 41.4 | 46.2 / 71.3 / 50.1 | 22.9 / 244.5 / 64.7 | 6.2 / 113.9 / 33.7 | 23.3 / 244.5 / 56.0 |
| BASE lock 12R | 31.5 / 40.6 / 59.6 | 43.4 / 40.6 / 47.4 | 41.6 / 40.6 / 51.4 | 19.1 / 117.4 / 57.9 | 2.1 / 122.5 / 29.2 | 19.2 / 122.5 / 51.6 |
| BASE lock 20R | 37.0 / 37.6 / 57.0 | 47.0 / 37.6 / 44.3 | 44.8 / 74.5 / 52.0 | 18.9 / 202.4 / 60.7 | 1.8 / 180.6 / 32.8 | 19.7 / 202.4 / 54.3 |
| BASE lock 30R | 40.7 / 29.9 / 52.9 | 48.9 / 29.9 / 41.4 | 45.9 / 80.0 / 50.7 | 21.1 / 200.7 / 63.5 | 5.7 / 134.8 / 33.4 | 22.2 / 200.7 / 55.5 |

Worst-20 PRE / X' / ALL: -1071 / -486 / -1262.

**Base MDE (level, 2.8 x SE of the weekly mean, $k/wk) L3M / L6M / HOLD / PRE / X' / ALL:** BASE-literal 38.2 / 20.9 / 21.1 / 15.1 / 11.5 / 9.5; BASE-noTH 39.6 / 21.9 / 24.8 / 20.9 / 14.2 / 12.9. Calmar L3M/L6M/HOLD/PRE/X'/ALL: literal 0.18 / 0.21 / 0.21 / 0.07 / 0.04 / 0.07; noTH 1.36 / 1.64 / 0.65 / 0.09 / 0.05 / 0.10. The L3M/L6M maxDD of the recent windows is a one-to-three-week episode; no significance is claimed on any risk line.

### Table 3 - leave-one-out (variant minus BASE, mean change $k/wk with paired MDE; `-piece` = piece switched off; so a positive number means the base is better WITHOUT the piece)

**On BASE-literal:**

| variant (vs BASE) | dMean L3M | dMean L6M | dMean HOLD | dMean PRE | dMean X' | dMean ALL |
|---|---|---|---|---|---|---|
| -split 70/30 (market entries) | +0.5 (13.9) | +1.7 (7.3) | +1.2 (6.8) | +0.8 (4.0) | +3.9 (5.6) | +1.8 (3.0) |
| -PE 45-s | -6.6 (23.4) | -3.9 (13.4) | -3.4 (11.7) | -2.9 (7.5) | -1.9 (7.0) | -2.7 (5.0) |
| -ER sizer | +9.6 (19.6) | +1.8 (11.8) | +2.1 (10.4) | -1.0 (6.9) | -2.2 (5.7) | -0.7 (4.4) |
| -Asia cut 50% | -0.2 (0.4) | +0.0 (0.4) | -0.1 (0.4) | -0.1 (0.1) | -0.2 (0.4) | -0.1 (0.2) |
| -zone set (7 lines + OTE62 B73) | -0.4 (7.1) | -2.3 (5.7) | -1.4 (6.3) | -3.6 (5.5) | -1.5 (5.8) | -2.6 (3.5) |
| -OTE62 B73 (line dropped) | -3.4 (5.5) | -1.8 (3.0) | -1.6 (2.6) | -1.5 (1.9) | -0.7 (2.0) | -1.3 (1.3)* |
| OTE62 skip D20 instead of B73 D30 | -3.7 (5.9) | -2.2 (3.2) | -2.0 (2.8) | -0.5 (1.9) | -0.7 (1.5) | -0.9 (1.2) |
| OTE62 WT D30 instead of B73 | -2.8 (7.8) | -2.0 (5.9) | -1.8 (5.2) | -0.4 (2.0) | -0.1 (1.0) | -0.6 (1.5) |
| stop parity (A/B mix) instead of Native | -0.2 (0.1)* | -0.2 (0.1)* | -0.1 (0.1)* | -0.1 (0.1)* | -0.1 (0.1)* | -0.1 (0.0)* |
| stop join 2.45 every day | -0.3 (0.1)* | -0.3 (0.1)* | -0.3 (0.1)* | -0.3 (0.1)* | -0.5 (0.8) | -0.4 (0.2)* |
| -sig HM skipBot3 slope | +4.0 (7.4) | +1.9 (4.1) | +1.9 (3.7) | +1.8 (1.6)* | +0.1 (1.7) | +1.3 (1.2)* |
| -sig KB skipTop3 st1_dist | +0.4 (3.2) | +0.0 (2.4) | -0.3 (2.2) | +0.4 (1.9) | +0.7 (1.4) | +0.3 (1.1) |
| -sig PE sizeHi st1_dist | +2.0 (13.4) | +2.0 (7.5) | +1.7 (6.5) | +0.7 (5.6) | +1.0 (3.8) | +1.0 (3.3) |
| -all 3 signal-state rules | +6.5 (14.6) | +3.9 (8.3) | +3.3 (7.5) | +2.9 (5.5) | +1.8 (4.2) | +2.7 (3.4) |
| -TH-L2 loss (-30/5s/30x) | +19.6 (27.1) | +18.3 (15.6)* | +14.5 (14.9) | +6.0 (9.4) | +1.1 (8.2) | +6.4 (6.3)* |
| -TH-L2 profit (30/30 path rule) | +7.5 (20.1) | +7.4 (12.7) | +8.5 (12.0) | +5.1 (6.4) | +1.1 (6.6) | +4.7 (4.6)* |
| -both TH-L2 rules | +25.6 (32.9) | +30.7 (18.2)* | +28.0 (17.4)* | +8.8 (12.1) | +1.0 (11.6) | +10.7 (8.2)* |
| -X1..X5 (all) | -5.8 (8.2) | -3.6 (5.2) | -3.6 (4.6) | -1.7 (3.1) | -1.0 (3.0) | -1.9 (2.0) |
| -X1 | -1.6 (3.9) | -0.9 (2.8) | -1.0 (2.5) | -1.2 (1.4) | -0.4 (1.4) | -0.9 (1.0) |
| -X2 | -0.7 (2.7) | -0.7 (1.8) | -0.5 (1.6) | -0.1 (1.2) | +0.0 (1.2) | -0.2 (0.8) |
| -X3 | -0.3 (3.0) | -0.1 (2.2) | -0.1 (2.0) | -0.0 (1.3) | -0.0 (1.3) | -0.0 (0.9) |
| -X4 | -1.8 (3.4) | -0.8 (2.2) | -0.6 (2.0) | -0.1 (1.2) | -0.1 (1.5) | -0.2 (0.9) |
| -X5 | -1.4 (3.0) | -1.2 (2.0) | -1.4 (1.9) | -0.3 (1.4) | -0.5 (1.1) | -0.6 (0.9) |
| +THL L6_a30_r3_w10 on HM (D6 line) | +0.0 (0.1) | +0.1 (0.1) | +0.1 (0.3) | +0.0 (0.3) | +0.1 (0.2) | +0.1 (0.2) |
| sig assignment B (warm 2025-02) | -1.0 (1.3) | -0.7 (1.0) | -0.9 (1.0) | +2.3 (3.1) | +1.8 (4.2) | +1.5 (2.0) |
| sig assignment C (frozen 12m cut) | -0.9 (1.2) | -0.3 (1.2) | -0.6 (1.2) | +0.0 (0.9) | -0.4 (1.9) | -0.2 (0.8) |
| TIE = Sunday composite (all D7-only off, parity) | +19.3 (35.9) | +22.9 (22.3)* | +20.4 (20.8) | +9.0 (12.5) | +2.8 (12.7) | +9.7 (8.6)* |

**On BASE-noTH (isolates the other pieces from the TH-L2 mapping):**

| variant (vs BASE) | dMean L3M | dMean L6M | dMean HOLD | dMean PRE | dMean X' | dMean ALL |
|---|---|---|---|---|---|---|
| -split 70/30 (market entries) | -0.7 (5.4) | -0.4 (4.4) | -0.8 (3.9) | +1.5 (5.0) | +0.3 (2.5) | +0.7 (2.7) |
| -PE 45-s | -3.3 (24.4) | -1.7 (12.6) | -2.8 (11.3) | +2.4 (6.0) | -2.0 (6.1) | +0.0 (4.3) |
| -ER sizer | -0.7 (15.9) | -7.2 (11.1) | -6.3 (11.0) | -1.9 (10.3) | -2.4 (9.5) | -3.0 (6.3) |
| -Asia cut 50% | +1.4 (6.7) | +0.6 (3.3) | +0.3 (3.0) | +1.9 (2.9) | -0.8 (1.6) | +0.8 (1.7) |
| -zone set (7 lines + OTE62 B73) | +2.1 (10.5) | -2.2 (8.1) | -2.2 (8.5) | -4.6 (8.9) | -3.1 (8.5) | -3.7 (5.4) |
| -OTE62 B73 (line dropped) | -0.4 (2.5) | -0.4 (1.8) | -0.4 (1.6) | +0.2 (1.3) | -0.1 (0.3) | -0.0 (0.7) |
| OTE62 skip D20 instead of B73 D30 | -2.5 (5.6) | -1.6 (3.2) | -1.5 (2.8) | -0.6 (2.1) | +0.2 (2.0) | -0.6 (1.4) |
| OTE62 WT D30 instead of B73 | -1.6 (6.9) | -2.3 (6.9) | -2.1 (6.0) | -0.7 (3.2) | +0.4 (2.3) | -0.7 (2.2) |
| stop parity (A/B mix) instead of Native | -1.5 (0.7)* | -1.2 (0.4)* | -1.1 (0.4)* | -1.0 (1.6) | -0.8 (0.2)* | -1.0 (0.8)* |
| stop join 2.45 every day | -2.8 (0.9)* | -2.1 (0.9)* | -2.1 (0.8)* | -1.9 (1.9)* | -1.5 (0.3)* | -1.8 (1.0)* |
| -sig HM skipBot3 slope | +1.7 (10.6) | +1.3 (5.6) | +2.0 (4.9) | +1.5 (2.1) | +0.3 (2.2) | +1.3 (1.6) |
| -sig KB skipTop3 st1_dist | -2.8 (4.8) | -0.9 (3.7) | -1.0 (3.5) | +0.9 (2.7) | +1.0 (2.0) | +0.5 (1.7) |
| -sig PE sizeHi st1_dist | +2.9 (21.8) | -1.5 (11.7) | -2.2 (10.7) | +2.4 (8.4) | +2.4 (5.1) | +1.4 (5.0) |
| -all 3 signal-state rules | +2.0 (21.2) | -1.2 (11.5) | -1.3 (10.3) | +4.7 (9.1) | +3.9 (5.2) | +3.2 (5.3) |
| -X1..X5 (all) | -5.8 (8.2) | -3.6 (5.2) | -3.6 (4.6) | -1.7 (3.1) | -1.0 (3.0) | -1.9 (2.0) |
| -X1 | -1.6 (3.9) | -0.9 (2.8) | -1.0 (2.5) | -1.2 (1.4) | -0.4 (1.4) | -0.9 (1.0) |
| -X2 | -0.7 (2.7) | -0.7 (1.8) | -0.5 (1.6) | -0.1 (1.2) | +0.0 (1.2) | -0.2 (0.8) |
| -X3 | -0.3 (3.0) | -0.1 (2.2) | -0.1 (2.0) | -0.0 (1.3) | -0.0 (1.3) | -0.0 (0.9) |
| -X4 | -1.8 (3.4) | -0.8 (2.2) | -0.6 (2.0) | -0.1 (1.2) | -0.1 (1.5) | -0.2 (0.9) |
| -X5 | -1.4 (3.0) | -1.2 (2.0) | -1.4 (1.9) | -0.3 (1.4) | -0.5 (1.1) | -0.6 (0.9) |
| +THL L6_a30_r3_w10 on HM (D6 line) | -0.5 (4.7) | -0.6 (2.6) | -0.1 (2.3) | +0.5 (2.0) | +0.0 (1.4) | +0.2 (1.2) |
| sig assignment B (warm 2025-02) | -1.7 (2.2) | -1.1 (1.4) | -1.7 (1.6)* | +1.0 (8.2) | +3.9 (5.2) | +1.3 (4.4) |
| sig assignment C (frozen 12m cut) | -1.5 (2.1) | -1.1 (1.3) | -1.3 (1.2)* | -0.3 (1.4) | +0.5 (3.1) | -0.3 (1.2) |

**maxDD and Calmar of the same variants - BASE-noTH** ($k; maxDD change % vs BASE in brackets):

| variant | maxDD L3M (chg%) | maxDD L6M (chg%) | maxDD HOLD (chg%) | maxDD PRE (chg%) | maxDD X' (chg%) | maxDD ALL (chg%) | Calmar L3M | Calmar L6M | Calmar HOLD | Calmar PRE | Calmar X' | Calmar ALL |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BASE | 29.9 (+0%) | 29.9 (+0%) | 71.3 (+0%) | 244.5 (+0%) | 113.9 (+0%) | 244.5 (+0%) | 1.36 | 1.64 | 0.65 | 0.09 | 0.05 | 0.10 |
| -split 70/30 (market entries) | 47.5 (+59%) | 47.5 (+59%) | 84.8 (+19%) | 256.9 (+5%) | 103.1 (-9%) | 256.9 (+5%) | 0.84 | 1.02 | 0.54 | 0.09 | 0.06 | 0.09 |
| -PE 45-s | 36.4 (+22%) | 36.4 (+22%) | 95.3 (+34%) | 188.2 (-23%) | 159.8 (+40%) | 188.2 (-23%) | 1.03 | 1.30 | 0.45 | 0.13 | 0.03 | 0.12 |
| -ER sizer | 17.9 (-40%) | 17.9 (-40%) | 45.1 (-37%) | 209.0 (-15%) | 174.4 (+53%) | 209.0 (-15%) | 2.23 | 2.32 | 0.88 | 0.10 | 0.02 | 0.10 |
| -Asia cut 50% | 31.3 (+5%) | 31.3 (+5%) | 78.8 (+10%) | 247.8 (+1%) | 138.0 (+21%) | 247.8 (+1%) | 1.35 | 1.58 | 0.59 | 0.10 | 0.04 | 0.10 |
| -zone set (7 lines + OTE62 B73) | 37.0 (+24%) | 37.0 (+24%) | 133.3 (+87%) | 309.6 (+27%) | 102.4 (-10%) | 309.6 (+27%) | 1.16 | 1.26 | 0.33 | 0.06 | 0.03 | 0.06 |
| -OTE62 B73 (line dropped) | 30.4 (+2%) | 30.4 (+2%) | 72.2 (+1%) | 256.5 (+5%) | 110.3 (-3%) | 256.5 (+5%) | 1.33 | 1.59 | 0.63 | 0.09 | 0.06 | 0.09 |
| OTE62 skip D20 instead of B73 D30 | 31.0 (+4%) | 31.0 (+4%) | 72.0 (+1%) | 215.8 (-12%) | 122.8 (+8%) | 215.8 (-12%) | 1.23 | 1.52 | 0.62 | 0.10 | 0.05 | 0.11 |
| OTE62 WT D30 instead of B73 | 36.7 (+23%) | 36.7 (+23%) | 69.6 (-2%) | 254.2 (+4%) | 101.4 (-11%) | 254.2 (+4%) | 1.07 | 1.27 | 0.63 | 0.09 | 0.07 | 0.09 |
| stop parity (A/B mix) instead of Native | 31.9 (+7%) | 31.9 (+7%) | 72.4 (+2%) | 255.7 (+5%) | 122.3 (+7%) | 255.7 (+5%) | 1.23 | 1.50 | 0.62 | 0.09 | 0.04 | 0.09 |
| stop join 2.45 every day | 32.8 (+10%) | 32.8 (+10%) | 76.2 (+7%) | 237.0 (-3%) | 127.9 (+12%) | 237.0 (-3%) | 1.16 | 1.43 | 0.58 | 0.09 | 0.04 | 0.09 |
| -sig HM skipBot3 slope | 29.4 (-2%) | 22.8 (-24%) | 57.5 (-19%) | 212.3 (-13%) | 113.3 (-1%) | 212.3 (-13%) | 1.44 | 2.20 | 0.84 | 0.11 | 0.06 | 0.12 |
| -sig KB skipTop3 st1_dist | 45.0 (+51%) | 45.0 (+51%) | 88.2 (+24%) | 230.3 (-6%) | 109.4 (-4%) | 230.3 (-6%) | 0.84 | 1.07 | 0.51 | 0.10 | 0.07 | 0.10 |

(Full level grids for every variant and window, incl. worst-20, SD, Calmar: `out/d7base/loo_table_literal.csv`, `loo_table_noTH.csv`.)

### Table 4 - bridge: Sunday composite to the base, one piece added at a time (cumulative; mean / maxDD / SD $k/wk)

| step | L3M | L6M | HOLD | PRE | X' | ALL |
|---|---|---|---|---|---|---|
| Sunday composite (TIE: parity stop, 8-line skip D20) | 34.4 / 21.4 / 44.7 | 41.1 / 22.9 / 42.7 | 38.6 / 97.0 / 51.8 | 23.1 / 241.2 / 55.7 | 8.0 / 120.5 / 32.6 | 22.3 / 241.2 / 50.3 |
| + Native stop every day | 36.1 / 14.3 / 44.3 | 42.4 / 21.1 / 42.3 | 39.8 / 95.4 / 51.5 | 24.3 / 230.2 / 55.6 | 8.8 / 113.3 / 32.5 | 23.4 / 230.2 / 50.2 |
| + OTE-62 B73 at D30 (7 lines skip D20) | 36.9 / 15.5 / 46.7 | 44.1 / 21.1 / 41.3 | 41.2 / 98.2 / 50.8 | 25.8 / 254.7 / 56.2 | 9.0 / 104.6 / 33.2 | 24.5 / 254.7 / 50.6 |
| + HM skipBot3 slope | 35.2 / 31.7 / 47.9 | 42.9 / 31.7 / 44.0 | 39.4 / 112.0 / 53.0 | 24.5 / 285.1 / 55.1 | 8.6 / 102.8 / 31.6 | 23.3 / 285.1 / 50.0 |
| + KB skipTop3 st1_dist | 37.8 / 31.2 / 47.0 | 43.8 / 31.2 / 43.5 | 40.3 / 94.9 / 51.0 | 23.6 / 299.2 / 55.1 | 7.5 / 117.9 / 31.3 | 22.8 / 299.2 / 49.7 |
| + PE sizeHi st1_dist | 34.9 / 23.6 / 50.2 | 45.3 / 23.6 / 41.2 | 42.6 / 74.9 / 49.8 | 21.1 / 236.5 / 62.0 | 5.2 / 144.5 / 34.0 | 21.3 / 236.5 / 54.3 |
| + X1..X5 at 2 lots | 40.7 / 29.9 / 52.9 | 48.9 / 29.9 / 41.4 | 46.2 / 71.3 / 50.1 | 22.9 / 244.5 / 64.7 | 6.2 / 113.9 / 33.7 | 23.3 / 244.5 / 56.0 |
| + TH-L2 loss (-30/5s/30x)  [= D7 base without the profit rule] | 22.7 / 54.8 / 47.9 | 25.6 / 54.8 / 41.4 | 26.7 / 54.8 / 47.8 | 19.1 / 191.5 / 52.0 | 6.3 / 149.4 / 30.3 | 17.2 / 191.5 / 46.5 |
| + TH-L2 profit (30/30 path rule)  [= D7 BASE literal] | 15.1 / 84.8 / 51.1 | 18.2 / 84.8 / 39.6 | 18.2 / 84.8 / 42.6 | 14.1 / 190.7 / 46.7 | 5.2 / 126.5 / 27.2 | 12.5 / 190.7 / 41.4 |

### API (full text in `out/d7base/README.md`)
```
import sys; sys.path.insert(0,'l2vast/ds3/code/d7base'); import d7lib as D   # run with python3 -I
r = D.run({'comb':12, 'sig_pe':False})      # overrides of D.BASE (documented there); ~1.5-2 s warm, ~7-9 s first call (numba + data)
r['cube']   # (11 books K6 P6 U6 H6 M6 A6 X1..X5, 6 entry sessions, 745 label days) $/day;  r['total'] = cube.sum((0,1));  D.stats(r['total'],'L6M')
D.run(D.TIE)   # the Sunday composite;  D.run({'asis':True,'stop':'join', ...}) the as-is frame
```

## 5. Pieces that could not be simulated exactly - nearest substitute and likely error

| piece | substitute used | likely error (size, sign) |
|---|---|---|
| TH-L2 profit '30/30' | NOT a ledger cell; path rule: open profit >= +30 pts for > 30 s then trail 30 behind the extreme (market exit 0.995), no order-book condition. Nearest ledger family L2SP arm pts30 / d30 / trail30 | LARGE and unsigned: removing it changes the L6M mean by +7.4k (MDE 12.7k) in the literal base; any book condition (thick book) would make it fire less often, so this is an upper bound on its damage. Sensitivity of the mapping (trail 20/40, lock 0/10, take) in section 6. Needs the user's definition |
| TH-L2 loss '-30/5 s/30x' | L2SL A=30 w=5 pulled-multiple 30 (exact reconstruction of the ledger rule at a threshold that is not on the ledger grid), market exit 0.995, per-second | exact in the as-is frame (A5 U1/U3 series reproduced to 0.00 $/day). In the composite: filled-lot scaling and re-evaluation from the actual entry for PE/B73 rows are my additions (error: PE rows ~1,600 re-evaluated; sign unknown, size well inside the +18k L6M effect). It tightens the stop to about -30 on ~98% of the trades that reach -30 (A5), so most of its effect is a price-path stop, not an order-book effect |
| OTE-62 B73 at D30 | one engine row per fired signal (entry at the signal, total lots, add px/index carried), N-basis costs; lock MTM on the average-price target | small: B73 vs skip-D20 vs dropped are all inside MDE (-1.8 / -2.2 / 0 on L6M vs MDE 3.0-3.2); PE-NY rows within 30 pts keep PE treatment |
| signal-state rules, live warm-up | assignment A (full history since 2023-04, min 100 prior); D7 warms the expanding rank from the chart's history (length unknown); B (warm from 2025-02) shown | A vs B differ by -0.7 / +2.3 / +1.8 $k/wk in L6M / PRE / X' (inside MDE); thresholds file EF-3 'C' is the research 12-month cut computed INSIDE the windows (flatters PRE/X') |
| X1-X5 | library series of the five identity cells in table order, 2 lots flat, M-basis net pts x $20; outside the lock engine, ER sizer and stack cut; 11 replayed-hour label days uncorrected | the X names/order are assumed. Locks in D7 would also cut X trades (not modelled): the X effect is overstated in lock-on rows. L6M +3.6k (MDE 5.2k) from the five |
| combined week lock | switches off / 12 / 20 / 30 (x R_K6, m0 1.0/0.5) | D7's own multiple is not stated; the lock does not see X books |
| Native stops | model input 1.28 vs 2.45 on stop exits (not a fill simulation) | Native worth +0.2-0.3k/wk L6M over parity/join; the live evidence is z 1.6, n 21 vs 8 (ON_SET) |
| ER(20) | 5-min Kaufman ER at the signal, thresholds 0.30 / 1.5 / 0.5 | engine bar and thresholds are the ONE_CONVENTION ones; D7's ER bar is not restated |
| O6 | excluded | - |

## 6. Sensitivity of the TH-L2 profit mapping (literal base otherwise; mean / maxDD $k)

| profit rule | L3M | L6M | HOLD | PRE | X' | ALL |
|---|---|---|---|---|---|---|
| none (no profit rule) | 22.7 / 54.8 / 47.9 | 25.6 / 54.8 / 41.4 | 26.7 / 54.8 / 47.8 | 19.1 / 191.5 / 52.0 | 6.3 / 149.4 / 30.3 | 17.2 / 191.5 / 46.5 |
| BASE: arm +30 >30 s, trail 30 | 15.1 / 84.8 / 51.1 | 18.2 / 84.8 / 39.6 | 18.2 / 84.8 / 42.6 | 14.1 / 190.7 / 46.7 | 5.2 / 126.5 / 27.2 | 12.5 / 190.7 / 41.4 |
| arm +30 >30 s, trail 20 | 17.0 / 76.2 / 50.7 | 18.5 / 76.2 / 41.9 | 17.9 / 76.2 / 42.4 | 12.6 / 190.3 / 44.6 | 5.0 / 119.2 / 25.8 | 11.7 / 190.3 / 39.8 |
| arm +30 >30 s, trail 40 | 20.3 / 67.5 / 46.3 | 21.3 / 67.5 / 37.5 | 21.1 / 67.5 / 42.5 | 14.3 / 200.1 / 49.9 | 7.2 / 139.7 / 29.6 | 13.9 / 200.1 / 43.7 |
| arm +30 >30 s, lock 0 (exit at entry) | 18.7 / 77.8 / 47.4 | 21.4 / 77.8 / 36.7 | 22.0 / 77.8 / 43.3 | 14.3 / 211.8 / 49.8 | 5.3 / 159.9 / 29.2 | 13.5 / 211.8 / 43.8 |
| arm +30 >30 s, lock +10 | 19.4 / 69.9 / 45.5 | 22.6 / 69.9 / 37.0 | 22.3 / 69.9 / 41.4 | 14.0 / 202.6 / 47.9 | 5.1 / 126.4 / 27.0 | 13.3 / 202.6 / 41.9 |
| arm +30 >30 s, take at the arm (30-pt target) | 19.5 / 77.6 / 46.8 | 19.3 / 77.6 / 41.6 | 20.9 / 77.6 / 43.4 | 12.6 / 155.7 / 44.2 | 2.5 / 130.5 / 25.4 | 11.6 / 155.7 / 40.1 |
| arm 70% of target, take (p70 take, dur 0) | 22.1 / 56.6 / 49.2 | 24.1 / 56.6 / 42.5 | 25.7 / 56.6 / 45.1 | 17.1 / 169.6 / 46.7 | 5.6 / 117.0 / 28.7 | 15.8 / 169.6 / 42.6 |
| arm 90% of target, take (dur 0) | 24.6 / 91.4 / 54.1 | 26.6 / 91.4 / 46.4 | 27.6 / 91.4 / 51.0 | 19.3 / 193.8 / 51.0 | 6.4 / 180.2 / 31.9 | 17.5 / 193.8 / 47.1 |
| arm +30, dur 0, trail 30 | 14.7 / 73.8 / 44.8 | 17.9 / 73.8 / 35.3 | 18.3 / 73.8 / 38.9 | 13.9 / 181.2 / 43.1 | 4.6 / 116.4 / 26.8 | 12.3 / 181.2 / 38.5 |

## 7. Null generator (shuffled labels; best-of-N Calmar gain by chance)

**Pool 'noTH' (760 draws; skip/size/zone shuffled-label draws through D.run on BASE-noTH).** Calmar gain (draw minus base) of the best of N draws, mean [5%, 95%] over 5,000 resamples:

| N (grid size) | selected on | L6M gain (selection stat) | HOLD | PRE | X' | ALL |
|---|---|---|---|---|---|---|
| 10 | L6M | +0.545 [+0.037, +1.266] | +0.039 [-0.127, +0.195] | -0.000 [-0.015, +0.013] | -0.001 [-0.025, +0.024] | +0.000 [-0.013, +0.010] |
| 10 | PRE+X | -0.170 [-0.948, +0.799] | +0.013 [-0.248, +0.265] | +0.010 [-0.009, +0.042] | +0.018 [-0.009, +0.054] | +0.008 [-0.007, +0.029] |
| 36 | L6M | +1.016 [+0.395, +1.886] | +0.067 [-0.179, +0.779] | -0.002 [-0.016, +0.014] | -0.002 [-0.036, +0.029] | -0.001 [-0.014, +0.013] |
| 36 | PRE+X | -0.281 [-1.012, +0.899] | +0.007 [-0.248, +0.265] | +0.014 [-0.009, +0.047] | +0.032 [-0.007, +0.057] | +0.012 [-0.007, +0.035] |
| 100 | L6M | +1.488 [+0.691, +3.238] | +0.139 [-0.179, +0.779] | -0.005 [-0.034, +0.014] | -0.005 [-0.037, +0.055] | -0.003 [-0.023, +0.013] |
| 100 | PRE+X | -0.402 [-1.012, +0.820] | -0.014 [-0.248, +0.265] | +0.016 [-0.009, +0.047] | +0.047 [+0.011, +0.117] | +0.014 [-0.003, +0.035] |
| 360 | L6M | +2.242 [+1.145, +3.238] | +0.347 [+0.058, +0.779] | -0.002 [-0.016, +0.014] | -0.009 [-0.036, +0.010] | +0.000 [-0.013, +0.013] |
| 360 | PRE+X | -0.352 [-0.942, +0.188] | +0.003 [-0.248, +0.159] | +0.016 [-0.009, +0.047] | +0.071 [+0.011, +0.117] | +0.016 [+0.000, +0.035] |

Base Calmar L6M 1.64, HOLD 0.65, PRE 0.09, X' 0.05, ALL 0.10. Read: a grid of N shuffled-label rules, ranked on L6M Calmar, delivers the 'L6M' column by chance; a real rule must beat that (and its PRE+X' honest-selection row) to be more than the best of N noise.

**Pool 'literal' (760 draws; skip/size/zone shuffled-label draws through D.run on BASE-literal).** Calmar gain (draw minus base) of the best of N draws, mean [5%, 95%] over 5,000 resamples:

| N (grid size) | selected on | L6M gain (selection stat) | HOLD | PRE | X' | ALL |
|---|---|---|---|---|---|---|
| 10 | L6M | +0.073 [+0.014, +0.180] | +0.062 [+0.010, +0.133] | -0.004 [-0.033, +0.025] | +0.008 [-0.015, +0.076] | -0.001 [-0.024, +0.026] |
| 10 | PRE+X | +0.024 [-0.070, +0.157] | +0.021 [-0.060, +0.121] | +0.005 [-0.020, +0.026] | +0.024 [-0.006, +0.082] | +0.005 [-0.010, +0.026] |
| 36 | L6M | +0.126 [+0.053, +0.212] | +0.096 [+0.049, +0.149] | -0.003 [-0.034, +0.026] | +0.014 [-0.016, +0.082] | +0.002 [-0.025, +0.032] |
| 36 | PRE+X | +0.040 [-0.079, +0.174] | +0.037 [-0.061, +0.146] | +0.006 [-0.020, +0.036] | +0.050 [-0.001, +0.095] | +0.008 [-0.013, +0.032] |
| 100 | L6M | +0.170 [+0.103, +0.240] | +0.107 [+0.057, +0.175] | -0.001 [-0.034, +0.026] | +0.014 [-0.013, +0.078] | +0.004 [-0.025, +0.032] |
| 100 | PRE+X | +0.047 [-0.079, +0.157] | +0.045 [-0.060, +0.146] | +0.005 [-0.020, +0.025] | +0.073 [+0.025, +0.114] | +0.010 [-0.013, +0.034] |
| 360 | L6M | +0.211 [+0.174, +0.240] | +0.089 [+0.057, +0.136] | -0.004 [-0.034, +0.026] | +0.000 [-0.013, +0.078] | +0.002 [-0.025, +0.032] |
| 360 | PRE+X | +0.050 [-0.004, +0.157] | +0.050 [+0.001, +0.146] | +0.005 [-0.020, +0.017] | +0.092 [+0.063, +0.114] | +0.011 [-0.008, +0.034] |

Base Calmar L6M 0.21, HOLD 0.21, PRE 0.07, X' 0.04, ALL 0.07. Read: a grid of N shuffled-label rules, ranked on L6M Calmar, delivers the 'L6M' column by chance; a real rule must beat that (and its PRE+X' honest-selection row) to be more than the best of N noise.

Per-kind pools (book x fraction x 40 draws) and the call signature are in README.md section 5; a grid that is mostly one book or one kind should be nulled with `kind=`/`book=`/`frac=`.

## 8. Notes, honesty labels, open questions

* Everything here is POST-HOC / CONSISTENCY on windows that include the recent looked data; no PASS. The leave-one-out says what each piece contributes to THIS base on THESE windows; none of it re-tests or kills a piece (the base is the user's decision).
* Questions put to the user in MORNING.md (queue not paused): (1) the TH-L2 profit rule; (2) X1-X5 identity; (3) base stop = Native every day; (4) lock multiple for the base.
* Tie-out is to 0.00 $/day, i.e. exact reproduction of the same arithmetic, not an independent check of the economics; the independent evidence for each piece is in the original reports.

## 9. TH-L2: helps or hurts in this engine, and the build checks (answer to the lead's S7 note)
* Build checks: the NameError (`_l2sl_shifted`) was a patch slip fixed at ~15:20Z; it never touched the stored tables (those ran the earlier working version, reproduced: BASE-literal L6M 18,200 / maxDD 84,758 re-run after the fix). Zero-change check: with TH-L2 off the engine ties the composite to 0.00 $/day (table 1). Program-own-frame check: the L2SL cut in the as-is frame reproduces A5's exact-engine U1 and U3 series to 0.00 $/day (>> the 1% requirement). The THL HM rule (+0.1k L6M) uses the stored sealed rule arrays. The profit rule has no stored program to tie to (it is my path rule).
* Verdict in this engine: both TH-L2 rules HURT the composite mean and the recent maxDD (removing loss: +18.3k L6M (MDE 15.6)*, removing profit: +7.4k (12.7); both: +30.7k (18.2)*; HOLD +28.0*), and improve the ALL-window maxDD only for the loss rule (ALL 190.7 vs 244.5 without both, worst-20 ALL -957 vs about -1,098). Why: the -30 cut is a stop tightening to -30 on ~98% of trades that reach -30 (A5), so it gives up the recoveries to the 60-pt target that the composite's sized entries (ER x1.5, 7-lot P6) earn; P6 carries it (L6M 25.4k -> 1.1k in the first draft, before the entry-shift fix). The profit mapping trails 30 behind +30, which cuts the 60-pt targets (section 6: the result depends strongly on the rule, p70 take is the mildest). The size of the damage is mapping-dependent, so treat BASE-literal as 'as mapped', BASE-noTH as the reference for every other piece.
* Date axis: this engine is on the OLD CAP (20260206, `D.CAP_LABEL`); days/windows come from the library arrays, so it re-ties when REDO-1 publishes the rebuilt tables (the code has no hard-coded dates other than X-cell parquet inputs, which must be rebuilt from de-duplicated tape).
