# REPORT FA3 - forward power: how many live weeks each lead needs

Written 2026-10-17 by research worker FA. Analysis only; the frozen predictions in PRED.json / PRED_EXTRA.json / PRED_FVG.json were not touched and no gate moved. Code: code/census/night_ins/ap_fa3.py; table: outputs/autopilot/forward/FA3_power.csv.

## 1. Method

For each of the 21 leads in FORWARD.md: mu = frozen (selection-deflated) predicted mean weekly uplift; the **block-bootstrap SD** is taken from the frozen 90% CI of the mean (10,000 circular block bootstraps, block 4 weeks, 167 estimation weeks): SE = (hi - lo) / (2 x 1.645), effective weekly SD sigma = SE x sqrt(167). This keeps the week-to-week dependence the iid SD ignores (column "SD inflation"). Weeks for 80% power at one-sided 5%: n = ((1.645 + 0.842) x sigma / mu)^2 = 6.18 (sigma/mu)^2, i.e. the live cumulative mean must reach z >= 1.645 with 80% probability if the prediction is exactly right. The implied date counts n weeks of scoring from the freeze: date = 2026-10-16 (end of the stub week W42, 0.6 week scored) + 7 x ceil(n - 0.6) days. Note FORWARD.md's own "weeks for 80% power" uses the looser one-sided 10% (z = 1.28), so its numbers are smaller; this report uses the 5% test the task specifies.

## 2. Result

| lead | family | mean $/wk (frozen) | block-boot SD $/wk | SD inflation vs iid | SNR /wk | weeks for 80% power, 1-sided 5% | implied date | weeks if true mean = 50% of predicted | weeks if true mean = 90%-CI lower bound | power at 52 wk | power at 78 wk | within a year |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| FVG_E1 | FVG | 6,832.0 | 12,451.0 | 0.950 | 0.549 | 21 | 2027-03-05 | 82 | 34 | 0.990 | 1.000 | yes |
| FVG_IMP3 | FVG | 8,087.0 | 15,994.0 | 1.090 | 0.506 | 24 | 2027-04-02 | 97 | 42 | 0.980 | 1.000 | yes |
| FVG_P1 | FVG | 4,535.0 | 10,190.0 | 0.830 | 0.445 | 31 | 2027-05-21 | 125 | 59 | 0.940 | 0.990 | yes |
| RW12P | K4 | 2,064.0 | 6,988.0 | 0.930 | 0.295 | 71 | 2028-02-25 | 284 | 201 | 0.690 | 0.830 | NO |
| BTCWT | BTC trend | 3,477.0 | 11,842.0 | 1.000 | 0.294 | 72 | 2028-03-03 | 287 | 223 | 0.680 | 0.830 | NO |
| ESDIP | dip-buy | 3,831.0 | 13,200.0 | 0.980 | 0.290 | 73 | 2028-03-10 | 294 | 220 | 0.670 | 0.820 | NO |
| SW4 | RTY fade | 3,160.0 | 14,514.0 | 1.050 | 0.218 | 130 | 2029-04-13 | 522 | 753 | 0.470 | 0.610 | NO |
| L93 | GC fade | 4,836.0 | 22,638.0 | 0.980 | 0.214 | 135 | 2029-05-18 | 542 | 721 | 0.460 | 0.600 | NO |
| RX5 | K4 | 1,011.0 | 4,900.0 | 0.920 | 0.206 | 145 | 2029-07-27 | 581 | 775 | 0.440 | 0.570 | NO |
| K4V2 | K4 | 891.0 | 4,813.0 | 1.040 | 0.185 | 180 | 2030-03-29 | 722 | 1240 | 0.380 | 0.500 | NO |
| WT10 | NQ trend | 1,788.0 | 9,822.0 | 1.180 | 0.182 | 186 | 2030-05-10 | 746 | never | 0.370 | 0.490 | NO |
| SW20 | RTY flow | 2,096.0 | 12,358.0 | 0.900 | 0.170 | 215 | 2030-11-29 | 859 | never | 0.340 | 0.440 | NO |
| RW5 | K4 (pair-side) | 5,020.0 | 30,550.0 | 1.120 | 0.164 | 229 | 2031-03-07 | 916 | never | 0.320 | 0.420 | NO |
| Q20 | RTY fade | 2,159.0 | 13,678.0 | 1.060 | 0.158 | 248 | 2031-07-18 | 993 | never | 0.310 | 0.400 | NO |
| H11B | pair-side | 1,806.0 | 12,826.0 | 0.970 | 0.141 | 312 | 2032-10-08 | 1248 | never | 0.260 | 0.340 | NO |
| W6FADE | gap fade | 1,938.0 | 15,847.0 | 1.000 | 0.122 | 413 | 2034-09-15 | >1,500 | never | 0.220 | 0.290 | NO |
| Z3FADE | gap fade | 1,699.0 | 14,416.0 | 1.080 | 0.118 | 445 | 2035-04-27 | >1,500 | never | 0.210 | 0.270 | NO |
| Q12 | NQ fade | 1,505.0 | 13,908.0 | 0.990 | 0.108 | 528 | 2036-11-28 | >1,500 | never | 0.190 | 0.250 | NO |
| T1B | gap fade | 1,641.0 | 16,898.0 | 1.010 | 0.097 | 656 | 2039-05-13 | >1,500 | never | 0.170 | 0.220 | NO |
| Q5ENS | XS momentum | 809.0 | 11,240.0 | 0.940 | 0.072 | 1193 | 2049-08-27 | >1,500 | never | 0.130 | 0.160 | NO |
| PERS30 | pair-side | 1,389.0 | 57,812.0 | 1.050 | 0.024 | >1,500 | never (>28 y) | >1,500 | never | 0.070 | 0.080 | NO |

## 3. Which leads can never be confirmed by weekly P&L within a year

**18 of 21 leads need more than 52 live weeks even if their frozen prediction is exactly right; only 3 do not** (FVG_E1, FVG_IMP3, FVG_P1). Ordered by weeks needed:

* **Within about 5-8 months** (if the prediction holds): FVG_E1 (21 wk, 2027-03-05), FVG_IMP3 (24 wk, 2027-04-02), FVG_P1 (31 wk, 2027-05-21). These are one family (weekly correlation +0.82 P1/E1, FA2): one confirmation, not three. All rest on limit-fill assumptions, so a failure of the fill model also removes all three.
* **1.3 to 1.5 years**: RW12P, BTCWT, ESDIP (about 71-73 weeks). ESDIP is trade-limited: the repo rule counts closed trades (21 trades, >= 16 winners); with ~7 trades a year that is ~3 years. The exact binomial for 80% power at 5% needs **17 trades (>= 14 wins) if the true win rate is the pair-window 87%, 85 trades (>= 59 wins) if it is 73%** (H0 60%), i.e. 2.4 years or 12 years at 7.2 trades per year. Weekly P&L cannot confirm it within a year.
* **2.5 to 4 years** (130-190 weeks): SW4, L93, RX5, K4V2, WT10 (and RW5, SW20, Q20, 215-250 weeks): the frozen promotion rule asks z >= 1.645 at 78 weeks, where the power if the prediction is true is only 0.44-0.61 for these (table, "repo rule" below). If the true mean is half the prediction the wait quadruples.
* **Effectively never** by weekly P&L: H11B (312 weeks, 2032), W6FADE, Z3FADE, Q12, T1B (410-660 weeks, 2034-2039), Q5ENS (1,190 weeks), PERS30 (10,700 weeks). PERS30's weekly SD ($58k) is 24x its mean uplift ($1,389): it can only be judged by its mechanism (the entries it removes), not by weekly P&L. The H11B halt and the gap fades are in the same position.

K4V2, RX5, RW12P and RW5 are ONE signal (K4 family), the FVG trio is one family, W6/Z3/T1b are one gap-fade family and SW4/Q20 share RTY: counting each family once, **the 21 leads are about 13-14 independent confirmations (FA2), and only one family (FVG) can be confirmed in 2026-27.**

## 4. What the frozen promotion rule can and cannot do

| lead | repo rule | power of that rule if prediction true | repo n80 (z=1.28, 1-sided 10%) |
|---|---|---|---|
| FVG_E1 | 17 wk, z>=1.28 | 0.840 | 17.0 |
| FVG_IMP3 | 15 wk, z>=1.28 | 0.750 | 15.0 |
| FVG_P1 | 33 wk, z>=1.28 | 0.900 | 33.0 |
| RW12P | 60 wk, z>=1.28 | 0.840 | 60.0 |
| BTCWT | 53 wk, z>=1.28 | 0.800 | 53.0 |
| ESDIP | 21 trades, >=16 wins |  |  |
| SW4 | 78 wk, z>=1.645 | 0.610 | 86.0 |
| L93 | 78 wk, z>=1.645 | 0.600 | 104.0 |
| RX5 | 78 wk, z>=1.645 | 0.570 | 125.0 |
| K4V2 | 78 wk, z>=1.645 | 0.500 | 121.0 |
| WT10 | 78 wk, z>=1.645 | 0.490 | 99.0 |
| SW20 | 78 wk, z>=1.645 | 0.440 | 195.0 |
| RW5 | 78 wk, z>=1.645 | 0.420 | 134.0 |
| Q20 | 78 wk, z>=1.645 | 0.400 | 160.0 |
| H11B | 78 wk, z>=1.645 | 0.340 | 240.0 |
| W6FADE | 78 wk, z>=1.645 | 0.290 | 301.0 |
| Z3FADE | 78 wk, z>=1.645 | 0.270 | 276.0 |
| Q12 | 78 wk, z>=1.645 | 0.250 | 393.0 |
| T1B | 78 wk, z>=1.645 | 0.220 | 466.0 |
| Q5ENS | 78 wk, z>=1.645 | 0.160 | 976.0 |
| PERS30 | 78 wk, z>=1.645 | 0.080 | 7,050.0 |

Where the repo rule is z >= 1.645 at N = 78 weeks, its power under the lead's own prediction is the "power at 78 wk" column above: 0.40-0.62 for K4V2, RX5, WT10, L93, SW4, SW20, RW5, Q20 (so even a real lead is promoted only about half the time), under 0.35 for H11B, W6/Z3, Q12, T1B, Q5ENS and PERS30 (promotion is essentially impossible), and 0.75-0.90 for the FVG leads, RW12P and BTCWT, whose rules use z 1.28 at N = 15-60 weeks. Conversely, if all 21 leads were null the expected number of false promotions under their own rules is about 1.35 (15 rules at z 1.645 = 0.75, 5 at z 1.28 = 0.5, ESDIP binomial 0.1); counting the K4, FVG and gap-fade families once each it is about 0.9. A promotion of one lead is therefore weak evidence by itself.

## 5. Caveats

1. The prediction is a deflated in-sample mean on a 167-week window that includes the selection span; the true mean is probably lower for most leads (the OOS-only mean is higher for FVG and WT10, lower for SW4, SW20 and Q5ENS in the FORWARD.md detail table). The "50% of predicted" column shows the 4x wait. The sigma uses the block bootstrap of the estimation window, not a live estimate.
2. n80 assumes a weekly SD that is stationary; live SD for the trend/fade sleeves can differ. Zero-trade weeks (frac_zero in FORWARD.md: K4 65%, ESDIP 76%, H11B 82%) make the weekly distribution non-normal, so the normal approximation is optimistic for those.
3. Only one live stub week (W42, 0.6 week) is scored, so no live power statement can be made yet; all dates are conditional on the frozen predictions.

DONE FA3
