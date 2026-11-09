# DS3_SIZER_EXHAUST - T-SIZER-EXHAUST ranked tables (SZ-CORE, 2026-11-09 14:19Z)

**Label: base S1b-COMB (live D7 v1.5 with the seven state-cut lines), controls NOCUT / UNIF where the owner ran them; first-order unless stage says S2 (exact); entries not live-matched (entry match < .85); in-sample; PRE-PROOF. Post-hoc, Shadow only, no PASS claims.**

Windows as of 2026-11-09 (L6M 20260512-, HOLD 20251111-, PRE 20240201-20250630, X' 20230401-20240131). Cut = maxDD cut vs Q1-A in % (+ = shallower); equal-mean = every cell scaled by one global factor so its L6M mean equals Q1-A's; worst-20 cut = change of the sum of the 20 worst weeks. Placebo = same-count down-sizing within book x session; family p = max-stat over the owner family set (own-draw p in the placebo column). Ranking key: equal-mean L6M maxDD cut (drawdown first), mean is the tie-break. Down-only = live candidates; UP rows are reported only.

**Audit note (SZ-CORE 2026-11-09):** several owner ledgers dropped the carrying weeks (202629-39) from the weekly vector BEFORE computing maxDD (directive: all weeks for maxDD, carrying week dropped from means only). Their L6M/HOLD cuts are overstated (e.g. J pair 18fe3fdc2530: owner 100% L6M cut = 0 maxDD in 14 retained weeks; sz_core all-weeks rescoring gives +37%). The sz_core rescoring of finalists is in the finalist table; ledger numbers are owner numbers until rescored.

## Scoreboard

| family | cells | down-only | LEAD | LEAD+ (placebo ok) | CANDIDATE |
|--|--|--|--|--|--|
| A ER family | 16290 | 12240 | 7194 | 923 | 0 |
| B Volatility target | 3994 | 3626 | 403 | 536 | 0 |
| C Equal-risk / parity | 28 | 16 | 14 | 0 | 2 |
| D Equity-curve / state | 160 | 146 | 68 | 0 | 7 |
| E Exposure / concentration | 74 | 74 | 37 | 0 | 4 |
| F Time / session | 118 | 118 | 27 | 7 | 0 |
| G Signal quality | 890 | 890 | 371 | 39 | 0 |
| H Regime | 149 | 149 | 58 | 13 | 0 |
| I Book-level recent performance | 188 | 186 | 91 | 0 | 0 |
| J Combinations | 883 | 883 | 615 | 0 | 261 |
| K P7 | 368 | 368 | 210 | 0 | 67 |

## Reference rows (exact engine, vs exact Q1-A; from the S3 re-runs, PRE/X' not complete)

| reference cell | L6M cut % / d mean | HOLD cut % / d mean | MID cut % / d mean |
|--|--|--|--|
| ZL-1 vol-target | +37.2 / -351 | +21.1 / -1595 | +11.3 / -2842 |
| old ladder L (x0.5/x1.5) | -76.3 / +83 | -41.5 / +674 | -37.2 / +3089 |
| B (x1/x1.5, up only) | -68.9 / +2024 | -52.6 / +2862 | -71.6 / +31 |
| sizer off (x1) | +7.2 / -391 | -38.6 / -1058 | -55.8 / -5182 |
| MV-london override | -1.3 / +7 | +6.8 / +195 | -0.8 / -117 |

## Family A - ER family

ER family: 16290 cells (12240 down-only); best by equal-mean L6M maxDD cut: ER-NQ er_nq_b3_n14 t2 [0.6, 0.0, 1.0] cuts L6M maxDD +83% at equal lots (d mean -10512 $/wk) and +67% at equal mean (PRE +14%, X' +19%); placebo p 0.05, family p 1.00, WF n/a -> LEAD.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-NQ er_nq_b3_n14 t2 | [0.6, 0.0, 1.0] | +83 / +21 / +55 / +58 | -30 | +85 | -10512 | +67 / -53 / +14 / +19 | 42.4 | 91% | 0.05 | 1.00 |  | -103485 | S1 | LEAD |
| ER-NQ er_nq_b5_n45 t2 | [0.25, 0.0, 1.0] | +64 / +1 / +44 / -8 | -52 | +63 | -4365 | +55 / -22 / +31 / -34 | 32.2 | 79% | 0.03 | 1.00 |  | -38280 | S1 | LEAD |
| ER-NQ er_nq_b3_n14 t2 | [0.55, 0.0, 1.0] | +66 / +26 / +47 / +37 | -3 | +75 | -6998 | +49 / -11 / +20 / +6 | 27.4 | 88% | 0.09 | 1.00 |  | -91335 | S1 | LEAD |
| ER-NQ er_nq_b30_n10 t2 | [0.5, 0.0, 1.0] | +52 / -12 / +17 / +35 | -53 | +61 | -1968 | +47 / -23 / +9 / +29 | 26.2 | 78% | 0.03 | 1.00 |  | -72540 | S1 | LEAD |
| ER-NQ er_nq_b5_n60 t3 | [0.2, 0.4, 0.25, 0.5, 1.0] | +58 / +1 / +46 / +30 | +1 | +60 | -4590 | +47 / -25 / +31 / +11 | 26.1 | 35% | 0.02 | 1.00 |  | -35797 | S1 | LEAD+ (placebo ok; WF n/a or fail) |
| ER-NQ er_nq_b30_n10 t2 | [0.5, 0.0, 1.0] | +63 / +25 / +44 / +45 | -55 | +61 | -6723 | +46 / -10 / +18 / +20 | 25.5 | 70% | 0.03 | 1.00 |  | -75660 | S1 | LEAD |
| ER-NQ er_nq_b5_n45 t2 | [0.25, 0.0, 1.0] | +65 / +27 / +51 / -1 | -82 | +63 | -8154 | +45 / -15 / +23 / -59 | 26.5 | 73% | 0.08 | 1.00 |  | -49405 | S1 | LEAD |
| ER-NQ er_nq_b5_n5 t2 | [0.1, 0.0, 1.0] | +17 / -30 / -3 / -31 | +157 | +29 | +11724 | +45 / +14 / +31 / +13 | 27.6 | 44% | 0.02 | 1.00 |  | -25004 | S1 | no |
| ER-NQ er_nq_b5_n5 t2 | [0.1, 0.0, 1.0] | +36 / -9 / +8 / +9 | +62 | +42 | +3125 | +44 / +5 / +20 / +21 | 24.8 | 10% | 0.06 | 1.00 |  | -32210 | S1 | LEAD+ (placebo ok; WF n/a or fail) |
| ER-xinst er_max2_b15_n20 t3 | [0.35, 0.45, 0.25, 0.5, 1.0] | +44 / -24 / +35 / +11 | +22 | +57 | -300 | +44 / -26 / +34 / +10 | 27.4 | 33% | 0.02 | 1.00 |  | -32510 | S1 | LEAD+ (placebo ok; WF n/a or fail) |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER-NQ er_nq_b15_n14 t2 | [0.55, 0.5, 1.5] | +21 / +2 / -18 / -57 | +51 | +38 | +9453 | +44 / +30 / +17 / -12 | 26.7 | 32% | 0.05 | 1.00 |  | +46687 | S1 | UP (report) |
| ER-NQ er_nq_b15_n14 t2 | [0.5, 0.5, 1.5] | +10 / -9 / +10 / -59 | +53 | +28 | +11306 | +39 / +26 / +39 / -8 | 25.2 | 36% | 0.02 | 1.00 |  | +64797 | S1 | UP (report) |
| ER-NQ er_nq_b3_n14 t2 | [0.55, 0.5, 1.5] | +21 / -21 / +30 / -25 | +110 | +30 | +7608 | +38 / +6 / +46 / +3 | 28.4 | 34% | 0.02 | 1.00 |  | -11846 | S1 | UP (report) |

## Family B - Volatility target

Volatility target: 3994 cells (3626 down-only); best by equal-mean L6M maxDD cut: VOL-pool vr_park_w10_g20 stepv [1.25, 0.0] cuts L6M maxDD +53% at equal lots (d mean +3560 $/wk) and +59% at equal mean (PRE +56%, X' +71%); placebo p 0.02, family p 0.28, WF n/a -> LEAD+ (placebo ok; WF n/a or fail).

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VOL-pool vr_park_w10_g20 stepv | [1.25, 0.0] | +53 / +58 / +49 / +67 | +35 | +64 | +3560 | +59 / +63 / +56 / +71 | 35.8 | 56% | 0.02 | 0.28 |  | -48050 | S1 | LEAD+ (placebo ok; WF n/a or fail) |
| VOL-pool vr_gk_w10_g20 stepv | [1.25, 0.0] | +54 / +59 / +58 / +55 | +7 | +66 | +2243 | +58 / +63 / +62 / +59 | 34.8 | 56% | 0.02 | 0.28 |  | -63235 | S1 | LEAD+ (placebo ok; WF n/a or fail) |
| VOL-pool vr_ewma5_l90_g20 stepv | [1.25, 0.0] | +51 / +48 / +47 / +47 | +56 | +66 | +3658 | +57 / +55 / +54 / +54 | 35.7 | 54% | 0.02 | 0.57 |  | -86585 | S1 | LEAD+ (placebo ok; WF n/a or fail) |
| VOL-pool vr_atr_b1_n5_g20 stepv | [1.25, 0.0] | +32 / +30 / +21 / +56 | +96 | +66 | +13166 | +57 / +56 / +50 / +72 | 34.0 | 78% | 0.02 | 0.32 |  | -13954 | S1 | LEAD+ (placebo ok; WF n/a or fail) |
| VOL-pool vr_rv1_w10_g20 stepv | [1.25, 0.0] | +47 / +14 / -38 / +52 | +141 | +59 | +5702 | +56 / +29 / -14 / +60 | 39.2 | 78% | 0.03 | 0.40 |  | -53054 | S1 | no |
| VOL-pool vr_gk_w10_g20 stepv | [1.25, 0.0] | +33 / +46 / +48 / +47 | +47 | +54 | +11037 | +54 / +63 / +65 / +64 | 33.4 | 77% | 0.02 | 0.12 |  | -36404 | S1 | LEAD+ (placebo ok; WF n/a or fail) |
| VOL-pool vr_rv5_w48_bk stepv | [1.25, 0.0] | +22 / +7 / +20 / +9 | +130 | +50 | +15192 | +54 / +44 / +52 / +46 | 31.6 | 63% | 0.02 | 0.71 |  | -87274 | S1 | LEAD+ (placebo ok; WF n/a or fail) |
| VOL-pool vr_atr_b15_n5_g20 stepv | [1.25, 0.0] | +28 / +38 / +36 / +51 | +94 | +43 | +12779 | +54 / +60 / +58 / +68 | 32.9 | 75% | 0.02 | 0.28 |  | -70190 | S1 | LEAD+ (placebo ok; WF n/a or fail) |
| VOL-pool vr_atr_b1_n5_g20 stepv | [1.25, 0.0] | +48 / +47 / +47 / +67 | +24 | +66 | +2579 | +53 / +52 / +52 / +71 | 31.0 | 58% | 0.03 | 0.68 |  | -42935 | S1 | LEAD+ (placebo ok; WF n/a or fail) |
| VOL-pool vr_atr_b15_n5_g20 stepv | [1.25, 0.0] | +47 / +49 / +55 / +62 | +22 | +55 | +1720 | +51 / +53 / +58 / +65 | 31.1 | 51% | 0.02 | 0.28 |  | -80055 | S1 | LEAD+ (placebo ok; WF n/a or fail) |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| VOL-pool vr_gk_w10_g20 pow | [1.0, 0.5, 1.5] | +30 / +26 / +34 / +32 | +77 | +36 | +5653 | +45 / +42 / +48 / +46 | 25.3 | 36% | 0.02 | 0.97 |  | -20343 | S1 | UP (report) |
| VOL-pool vr_atr_b15_n5_g20 pow | [1.0, 0.5, 1.5] | +26 / +21 / +16 / +31 | +50 | +29 | +7156 | +43 / +40 / +36 / +47 | 26.7 | 38% | 0.02 | 1.00 |  | -23055 | S1 | UP (report) |
| VOL-pool vr_park_w10_g20 pow | [1.0, 0.5, 1.5] | +31 / +25 / +30 / +32 | +61 | +34 | +4187 | +42 / +37 / +41 / +43 | 24.0 | 36% | 0.02 | 1.00 |  | -18559 | S1 | UP (report) |

## Family C - Equal-risk / parity

Equal-risk / parity: 28 cells (16 down-only); best by equal-mean L6M maxDD cut: riskcap_per_trade R$3600 cuts L6M maxDD +31% at equal lots (d mean -8513 $/wk) and +2% at equal mean (PRE +18%, X' +31%); placebo p 0.02, family p 1.00, WF +32 -> LEAD.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| riskcap_per_trade | R$3600 | +31 / +34 / +42 / +51 | -8 | +12 | -8513 | +2 / +7 / +18 / +31 | 19.4 | 22% | 0.02 | 1.00 | +32 | -38377 | S1 | LEAD |
| volparity_down | win120_refmed | +56 / +31 / +46 / +37 | +33 | +4 | -16574 | -2 / -61 / -24 / -46 | 18.5 | 30% | 0.04 | 1.00 | +32 |  | S1 | CANDIDATE (own-p only; family p 1.00) |
| riskcap_per_trade | R$4800 | +20 / +14 / +21 / +19 | -16 | +2 | -6658 | -4 / -11 / -2 / -6 | 18.3 | 8% | 0.31 | 1.00 | +32 | -27016 | S1 | LEAD |
| volparity_down | win60_refmed | +56 / +28 / +49 / +32 | +39 | -4 | -16945 | -6 / -73 / -21 / -62 | 17.9 | 30% | 0.09 | 1.00 | +32 |  | S1 | CANDIDATE (own-p only; family p 1.00) |
| riskcap_per_trade | R$6000 | +14 / +9 / +17 / +18 | -17 | -3 | -5889 | -7 / -14 / -3 / -3 | 17.7 | 7% | 0.43 | 1.00 | +32 | -17840 | S1 | LEAD |
| riskcap_per_trade | R$2400 | +33 / +38 / +55 / +64 | +21 | -6 | -13123 | -22 / -12 / +17 / +34 | 15.5 | 24% | 0.34 | 1.00 | +32 | -51309 | S1 | LEAD |
| volparity_down | win20_refmin | +57 / +50 / +70 / +74 | +46 | -8 | -18825 | -22 / -40 / +15 / +28 | 15.5 | 39% | 0.26 | 1.00 | +32 |  | S1 | LEAD |
| esparity_down | last100tr_refmin | +57 / +50 / +70 / +68 | +47 | -7 | -18926 | -22 / -42 / +14 / +10 | 15.5 | 39% | 0.20 | 1.00 | +32 |  | S1 | LEAD |
| esparity_down | last50tr_refmin | +57 / +50 / +70 / +72 | +47 | -7 | -18847 | -22 / -41 / +15 / +22 | 15.5 | 39% | 0.22 | 1.00 | +32 |  | S1 | LEAD |
| volparity_down | win60_refmin | +57 / +50 / +70 / +37 | +46 | -7 | -18851 | -22 / -43 / +15 / -77 | 15.5 | 39% | 0.17 | 1.00 | +32 |  | S1 | LEAD |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| volparity_up | win60_refmed_clip.5-1.5 | +35 / +16 / +45 / +20 | -2 | +11 | -10504 | -2 / -31 / +14 / -26 | 18.7 | 39% | 0.18 | 1.00 | +32 |  | S1 | UP (report) |
| volparity_up | win20_refmin_clip.5-1.5 | +47 / +39 / +43 / +54 | +26 | +1 | -14104 | -2 / -18 / -10 / +11 | 18.6 | 39% | 0.18 | 1.00 | +32 |  | S1 | UP (report) |
| volparity_up | win120_refmin_clip.5-1.5 | +47 / +39 / +43 / +29 | +26 | +1 | -14106 | -2 / -18 / -10 / -38 | 18.6 | 38% | 0.20 | 1.00 | +32 |  | S1 | UP (report) |

## Family D - Equity-curve / state

Equity-curve / state: 160 cells (146 down-only); best by equal-mean L6M maxDD cut: week_loss_stack X20000_f0.00 cuts L6M maxDD +44% at equal lots (d mean -2097 $/wk) and +40% at equal mean (PRE +4%, X' -54%); placebo p 0.01, family p 1.00, WF +46 -> LEAD.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| week_loss_stack | X20000_f0.00 | +44 / +14 / +11 / -42 | +3 | +44 | -2097 | +40 / +7 / +4 / -54 | 31.6 | 24% | 0.01 | 1.00 | +46 | +0 | S1 | LEAD |
| dayloss_stack$ | X16000_f0.00 | +30 / -49 / +18 / +5 | -33 | +35 | +498 | +31 / -47 / +19 / +7 | 27.5 | 9% | 0.02 | 1.00 | +46 | +0 | S1 | LEAD |
| eqdd_book_20d_R | Y1R_f0.50_sticky | +47 / +41 / +45 / +48 | +26 | +25 | -8535 | +24 / +16 / +22 / +27 | 25.1 | 33% | 0.04 | 0.76 | +46 | +0 | S1 | CANDIDATE (own-p only; family p 0.76) |
| eqdd_stack_20d | Y10000_f0.50_live | +41 / +37 / +43 / +13 | +29 | +17 | -6609 | +24 / +18 / +26 / -12 | 24.8 | 26% | 0.03 | 1.00 | +46 | +0 | S1 | CANDIDATE (own-p only; family p 1.00) |
| eqdd_book_20d_R | Y4R_f0.25_sticky | +44 / +25 / +51 / +36 | +40 | +33 | -8025 | +23 / -3 / +33 / +12 | 24.7 | 29% | 0.05 | 1.00 | +46 | +0 | S1 | CANDIDATE (own-p only; family p 1.00) |
| eqdd_stack_20d | Y20000_f0.50_live | +36 / +26 / +42 / +14 | +23 | +11 | -5357 | +22 / +9 / +29 / -5 | 24.3 | 21% | 0.02 | 1.00 | +46 | +0 | S1 | CANDIDATE (own-p only; family p 1.00) |
| week_loss_stack | X10000_f0.50 | +24 / +7 / +36 / -49 | +7 | +24 | -1497 | +20 / +2 / +32 / -57 | 23.6 | 10% | 0.02 | 1.00 | +46 | +0 | S1 | LEAD |
| eqdd_book_20d_R | Y1R_f0.50_live | +36 / +41 / +42 / +19 | +24 | +15 | -6564 | +17 / +24 / +25 / -4 | 22.9 | 27% | 0.02 | 1.00 | +46 | +0 | S1 | CANDIDATE (own-p only; family p 1.00) |
| dayloss_book_R | X1.0R_f0.00 | +23 / -17 / +14 / +9 | -2 | +30 | -3451 | +12 / -33 / +2 / -3 | 21.6 | 15% | 0.17 | 1.00 | +46 | -8785 | S1 | LEAD |
| lock_daycap_loss | loss1R(live2) | +23 / -17 / +14 / +9 | -2 | +30 | -3451 | +12 / -33 / +2 / -3 | 21.6 | 15% | 0.16 | 1.00 | +46 | -8785 | S1 | LEAD |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| eqdd_stack_UP_at_high | Y20000_f0.50_up1.25 | +36 / +28 / +40 / -14 | +32 | +13 | -4836 | +23 / +14 / +29 / -37 | 24.6 | 29% | 0.04 | 1.00 | +46 | +25118 | S1 | UP (report) |
| antimartingale_UP | book_n4_x1.25 | -1 / -1 / +1 / -7 | +1 | -3 | -186 | -2 / -1 / +0 / -8 | 18.6 | 2% | 0.11 | 1.00 | +46 | +0 | S1 | UP (report) |
| antimartingale_UP | book_n4_x1.50 | -1 / -1 / +2 / -9 | +10 | -5 | -739 | -3 / -3 / -1 / -12 | 18.4 | 5% | 0.07 | 1.00 | +46 | -655 | S1 | UP (report) |

## Family E - Exposure / concentration

Exposure / concentration: 74 cells (74 down-only); best by equal-mean L6M maxDD cut: corr_same_side N30min_f0.5_ge1_others cuts L6M maxDD +37% at equal lots (d mean -6495 $/wk) and +19% at equal mean (PRE +10%, X' -13%); placebo p 0.06, family p 1.00, WF +11 -> CANDIDATE (own-p only; family p 1.00).

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| corr_same_side | N30min_f0.5_ge1_others | +37 / +16 / +30 / +13 | +23 | +21 | -6495 | +19 / -8 / +10 / -13 | 23.5 | 19% | 0.06 | 1.00 | +11 | -35277 | S1 | CANDIDATE (own-p only; family p 1.00) |
| newentry_haircut_day_dd | Y15000_f0.0 | +31 / -42 / +39 / -34 | +11 | +17 | -5255 | +16 / -73 / +25 / -64 | 22.5 | 19% | 0.14 | 1.00 | +11 | +0 | S1 | LEAD |
| total_lots_cap | cap4_skip | +58 / +11 / +71 / +39 | +40 | +34 | -14993 | +13 / -84 / +40 / -26 | 21.8 | 32% | 0.03 | 1.00 | +11 | -73240 | S1 | CANDIDATE (own-p only; family p 1.00) |
| same_side_lots_cap | cap6_skip | +41 / +40 / +45 / +55 | -1 | +44 | -9614 | +12 / +10 / +18 / +33 | 21.6 | 15% | 0.05 | 1.00 | +11 | -53550 | S1 | LEAD |
| total_lots_cap | cap6_skip | +41 / +46 / +45 / +40 | +8 | +40 | -10409 | +8 / +16 / +15 / +7 | 20.7 | 18% | 0.06 | 1.00 | +11 | -52835 | S1 | CANDIDATE (own-p only; family p 1.00) |
| same_side_lots_cap | cap4_trunc | +52 / +27 / +40 / +47 | +35 | +25 | -14135 | +7 / -41 / -17 / -3 | 20.4 | 39% | 0.08 | 1.00 | +11 | -35944 | S1 | CANDIDATE (own-p only; family p 1.00) |
| newentry_haircut_day_dd | Y15000_f0.5 | +12 / -24 / +29 / -0 | +0 | +11 | -1616 | +7 / -31 / +25 / -6 | 20.4 | 4% | 0.13 | 1.00 | +11 | +0 | S1 | LEAD |
| same_side_lots_cap | cap12_skip | +6 / -1 / +2 / -21 | +4 | +4 | +105 | +7 / -1 / +3 / -20 | 20.3 | 1% | 0.03 | 1.00 | +11 | -18780 | S1 | LEAD |
| newentry_haircut_day_dd | Y24000_f0.0 | +1 / -19 / +29 / -3 | -25 | +21 | +1689 | +7 / -13 / +32 / +2 | 20.3 | 5% | 0.12 | 1.00 | +11 | +0 | S1 | LEAD |
| total_lots_cap | cap12_skip | +6 / -1 / +2 / -21 | +2 | +4 | -128 | +6 / -1 / +2 / -21 | 20.2 | 2% | 0.12 | 1.00 | +11 | -27180 | S1 | LEAD |

## Family F - Time / session

Time / session: 118 cells (118 down-only); best by equal-mean L6M maxDD cut: dow {"dow": 2, "m": 0} cuts L6M maxDD +51% at equal lots (d mean -74 $/wk) and +51% at equal mean (PRE +3%, X' +35%); placebo p 0.01, family p 1.00, WF n/a -> LEAD+ (placebo ok; WF n/a or fail).

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| dow | {"dow": 2, "m": 0} | +51 / +27 / +4 / +35 | +43 |  | -74 | +51 / +27 / +3 / +35 |  | 20% | 0.01 | 1.00 |  | -104810 | S1 | LEAD+ (placebo ok; WF n/a or fail) |
| slot48 | {"m": 0, "slot": 8} | +12 / -3 / -1 / -12 | +68 |  | +1921 | +19 / +4 / +6 / -3 |  | 3% | 0.29 | 1.00 |  | +0 | S1 | no |
| dow | {"dow": 2, "m": 0.5} | +15 / +11 / +6 / +23 | +45 |  | -552 | +13 / +8 / +4 / +21 |  | 7% | 0.05 | 1.00 |  | -37680 | S1 | LEAD+ (placebo ok; WF n/a or fail) |
| slot48 | {"m": 0, "slot": 40} | +12 / -6 / -8 / +16 | +48 |  | -282 | +11 / -7 / -10 / +15 |  | 3% | 0.05 | 1.00 |  | +0 | S1 | no |
| slot48 | {"m": 0, "slot": 10} | +9 / +3 / +5 / +4 | +55 |  | +235 | +10 / +4 / +6 / +4 |  | 2% | 0.29 | 1.00 |  | +0 | S1 | LEAD |
| slot48 | {"m": 0.5, "slot": 15} | +6 / -4 / +3 / +0 | +48 |  | +844 | +9 / -1 / +6 / +4 |  | 1% | 0.02 | 1.00 |  | +0 | S1 | LEAD+ (placebo ok; WF n/a or fail) |
| slot48 | {"m": 0, "slot": 22} | +8 / +4 / +5 / +9 | +57 |  | +274 | +9 / +5 / +6 / +10 |  | 5% | 0.30 | 1.00 |  | +0 | S1 | LEAD |
| slot48 | {"m": 0, "slot": 15} | +2 / -21 / +9 / +2 | +59 |  | +1839 | +9 / -13 / +16 / +9 |  | 2% | 0.07 | 1.00 |  | +0 | S1 | LEAD+ (placebo ok; WF n/a or fail) |
| slot48 | {"m": 0.5, "slot": 8} | +6 / -3 / +2 / -2 | +50 |  | +651 | +8 / -0 / +4 / +1 |  | 1% | 0.17 | 1.00 |  | +0 | S1 | LEAD |
| slot48 | {"m": 0, "slot": 20} | +4 / +11 / +3 / +35 | +65 |  | +1052 | +8 / +15 / +7 / +38 |  | 9% | 0.18 | 1.00 |  | +0 | S1 | LEAD |

## Family G - Signal quality

Signal quality: 890 cells (890 down-only); best by equal-mean L6M maxDD cut: qgate {"feat": "nA40", "m": 0, "q": 0.1, "tail": "low"} cuts L6M maxDD +90% at equal lots (d mean -13857 $/wk) and +77% at equal mean (PRE -11%, X' -137%); placebo p 0.33, family p 1.00, WF n/a -> LEAD.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| qgate | {"feat": "nA40", "m": 0, "q": 0.1, "tail": "low"} | +90 / +18 / +53 / +0 | -17 |  | -13857 | +77 / -95 / -11 / -137 |  | 68% | 0.33 | 1.00 |  | +0 | S1 | LEAD |
| qgate | {"feat": "nA40", "m": 0, "q": 0.3, "tail": "low"} | +90 / +18 / +53 / +0 | -17 |  | -13857 | +77 / -95 / -11 / -137 |  | 68% | 0.27 | 1.00 |  | +0 | S1 | LEAD |
| qgate | {"feat": "nA40", "m": 0, "q": 0.5, "tail": "low"} | +90 / +18 / +53 / +0 | -17 |  | -13857 | +77 / -95 / -11 / -137 |  | 68% | 0.22 | 1.00 |  | +0 | S1 | LEAD |
| qgate | {"feat": "nA40", "m": 0, "q": 0.2, "tail": "low"} | +90 / +18 / +53 / +0 | -17 |  | -13857 | +77 / -95 / -11 / -137 |  | 68% | 0.36 | 1.00 |  | +0 | S1 | LEAD |
| qgate_x_er | {"er": "erlow", "feat": "dA", "m": 0, "q": 0.5, "tail": "high"} | +28 / -2 / -8 / +0 | +84 |  | +2389 | +35 / +8 / +1 / +9 |  | 22% | 0.10 | 1.00 |  | +0 | S1 | no |
| qgate_x_er | {"er": "erhigh", "feat": "dip30", "m": 0, "q": 0.5, "tail": "high"} | +31 / -1 / +50 / +0 | +79 |  | +1132 | +34 / +3 / +52 / +5 |  | 20% | 0.04 | 1.00 |  | +0 | S1 | LEAD+ (placebo ok; WF n/a or fail) |
| qgate_x_er | {"er": "erhigh", "feat": "f_r_ab8", "m": 0, "q": 0.5, "tail": "low"} | +46 / +4 / +17 / +0 | +22 |  | -5442 | +30 / -24 / -7 / -29 |  | 17% | 0.22 | 1.00 |  | +0 | S1 | LEAD |
| qgate | {"feat": "nA40", "m": 0.5, "q": 0.1, "tail": "low"} | +41 / +30 / +38 / +0 | +37 |  | -4071 | +29 / +16 / +25 / -20 |  | 28% | 0.09 | 1.00 |  | +0 | S1 | LEAD+ (placebo ok; WF n/a or fail) |
| qgate | {"feat": "nA40", "m": 0.5, "q": 0.5, "tail": "low"} | +41 / +30 / +38 / +0 | +37 |  | -4071 | +29 / +16 / +25 / -20 |  | 28% | 0.06 | 1.00 |  | +0 | S1 | LEAD+ (placebo ok; WF n/a or fail) |
| qgate | {"feat": "nA40", "m": 0.5, "q": 0.3, "tail": "low"} | +41 / +30 / +38 / +0 | +37 |  | -4071 | +29 / +16 / +25 / -20 |  | 28% | 0.12 | 1.00 |  | +0 | S1 | LEAD |

## Family H - Regime

Regime: 149 cells (149 down-only); best by equal-mean L6M maxDD cut: regime {"cond": "prior_range_day", "m": 0} cuts L6M maxDD +39% at equal lots (d mean -2176 $/wk) and +33% at equal mean (PRE -1%, X' -128%); placebo p 0.60, family p 1.00, WF n/a -> LEAD.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| regime | {"cond": "prior_range_day", "m": 0} | +39 / +1 / +9 / -107 | +27 |  | -2176 | +33 / -9 / -1 / -128 |  | 29% | 0.60 | 1.00 |  | +0 | S1 | LEAD |
| regime | {"cond": "on_ratio_ge0.8", "m": 0} | +41 / -19 / +44 / -74 | +33 |  | -3105 | +32 / -36 / +35 / -100 |  | 35% | 0.86 | 1.00 |  | +0 | S1 | LEAD |
| regime | {"cond": "adx5_ge20", "m": 0.5} | +41 / +20 / +38 / +43 | +39 |  | -3885 | +30 / +5 / +26 / +32 |  | 30% | 0.02 | 1.00 |  | +0 | S1 | LEAD+ (placebo ok; WF n/a or fail) |
| regime | {"cond": "on_ratio_ge0.8", "m": 0.5} | +23 / +8 / +31 / +1 | +54 |  | +271 | +24 / +9 / +32 / +2 |  | 11% | 0.06 | 1.00 |  | +0 | S1 | LEAD+ (placebo ok; WF n/a or fail) |
| regime | {"cond": "on_ratio_ge1.0", "m": 0.5} | +21 / +4 / +15 / +4 | +52 |  | +187 | +22 / +4 / +16 / +5 |  | 7% | 0.11 | 1.00 |  | +0 | S1 | LEAD |
| regime | {"cond": "on_ratio_ge0.4", "m": 0.5} | +32 / +23 / +43 / +32 | +33 |  | -4012 | +18 / +8 / +32 / +18 |  | 25% | 0.16 | 1.00 |  | +0 | S1 | LEAD |
| regime | {"cond": "prior_close_high", "m": 0.5} | +18 / -4 / +4 / -5 | +44 |  | +24 | +18 / -4 / +4 / -5 |  | 10% | 0.13 | 1.00 |  | +0 | S1 | LEAD |
| regime | {"cond": "od_against_ge0.05", "m": 0} | +9 / +3 / +13 / -30 | +73 |  | +2382 | +18 / +12 / +20 / -18 |  | 9% | 0.40 | 1.00 |  | +0 | S1 | LEAD |
| regime | {"cond": "gap_with_ge0.25", "m": 0.5} | +35 / +16 / +16 / +8 | +2 |  | -5318 | +17 / -8 / -8 / -18 |  | 16% | 0.60 | 1.00 |  | +0 | S1 | LEAD |
| regime | {"cond": "od_with_ge0.05", "m": 0} | +21 / +17 / -0 / +29 | +50 |  | -1411 | +16 / +12 / -7 / +25 |  | 17% | 0.67 | 1.00 |  | +0 | S1 | no |

## Family I - Book-level recent performance

Book-level recent performance: 188 cells (186 down-only); best by equal-mean L6M maxDD cut: I5 stack rolling Calmar {"D": 20, "mult": 0.0, "x": 3.0} cuts L6M maxDD +68% at equal lots (d mean -10667 $/wk) and +53% at equal mean (PRE +37%, X' +23%); placebo p 0.08, family p 1.00, WF +39 -> LEAD.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| I5 stack rolling Calmar | {"D": 20, "mult": 0.0, "x": 3.0} | +68 / +24 / +58 / +49 | -33 | +68 | -10667 | +53 / -13 / +37 / +23 | 44.4 | 72% | 0.08 | 1.00 | +39 | -104810 | S1-first-order | LEAD |
| I5 stack rolling Calmar | {"D": 10, "mult": 0.0, "x": 2.0} | +57 / +7 / +55 / +70 | -24 | +30 | -7874 | +42 / -23 / +41 / +60 | 36.5 | 63% | 0.09 | 1.00 | +39 | -104810 | S1-first-order | LEAD |
| I5 stack rolling Calmar | {"D": 20, "mult": 0.5, "x": 3.0} | +36 / +33 / +36 / +31 | -11 | +36 | -3462 | +29 / +25 / +29 / +22 | 29.5 | 28% | 0.10 | 0.95 | +39 | -37680 | S1-first-order | LEAD |
| I3 book rolling Calmar | {"D": 10, "mult": 0.0, "x": 0.0} | +31 / +20 / +17 / +10 | -3 | +25 | -951 | +29 / +18 / +14 / +7 | 29.4 | 37% | 0.14 | 0.99 | +39 | -67075 | S1-first-order | LEAD |
| I5 stack rolling Calmar | {"D": 10, "mult": 0.5, "x": 2.0} | +30 / +33 / +43 / +41 | -3 | +22 | -1111 | +28 / +31 / +41 / +39 | 29.1 | 25% | 0.11 | 0.97 | +39 | -37680 | S1-first-order | LEAD |
| I3 book rolling Calmar | {"D": 10, "mult": 0.5, "x": 2.0} | +34 / +31 / +46 / +38 | -11 | +23 | -3488 | +26 / +23 / +39 / +31 | 28.5 | 28% | 0.15 | 1.00 | +39 | -38365 | S1-first-order | LEAD |
| I3 book rolling Calmar | {"D": 10, "mult": 0.0, "x": 2.0} | +58 / +38 / +41 / +9 | -44 | +41 | -14076 | +25 / -9 / -5 / -63 | 28.1 | 74% | 0.22 | 1.00 | +39 | -105580 | S1-first-order | LEAD |
| I3 book rolling Calmar | {"D": 10, "mult": 0.0, "x": 0.5} | +38 / -18 / +52 / -65 | -17 | +12 | -5619 | +25 / -44 / +42 / -100 | 28.1 | 51% | 0.20 | 1.00 | +39 | -102520 | S1-first-order | LEAD |
| I5 stack rolling Calmar | {"D": 10, "mult": 0.0, "x": 3.0} | +57 / +65 / +55 / +70 | -42 | +55 | -13491 | +25 / +40 / +23 / +48 | 28.0 | 73% | 0.15 | 1.00 | +39 | -104810 | S1-first-order | LEAD |
| I3 book rolling Calmar | {"D": 10, "mult": 0.5, "x": 0.0} | +23 / +29 / +36 / +15 | +0 | +15 | +42 | +23 / +29 / +36 / +15 | 27.4 | 14% | 0.12 | 0.95 | +39 | -24939 | S1-first-order | LEAD |

Up-allowed rows (reported, never promoted): top 3 by equal-mean cut.

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| I6 up-allowed hot x1.5 / cold x0.5 | {"N": 8, "thr_R": 2} | +5 / -9 / -10 / -10 | +0 | -20 | +105 | +5 / -9 / -10 / -10 | 22.2 | 34% | 0.40 | 1.00 | +39 | +2320 | S1-first-order | UP (report) |
| I6 up-allowed hot x1.5 / cold x0.5 | {"N": 8, "thr_R": 4} | -18 / +4 / -4 / -0 | -13 | -18 | -4090 | -35 / -9 / -19 / -15 | 15.5 | 11% | 0.93 | 1.00 | +39 | -280 | S1-first-order | UP (report) |

## Family J - Combinations

Combinations: 883 cells (883 down-only); best by equal-mean L6M maxDD cut: J pair min {"a": "ext-AB:3aa2207bf733", "b": "ext-G:1d9d637a3a48"} cuts L6M maxDD +100% at equal lots (d mean +245 $/wk) and +100% at equal mean (PRE +51%, X' +42%); placebo p 0.02, family p 0.83, WF +29 -> CANDIDATE (own-p only; family p 0.83).

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| J pair min | {"a": "ext-AB:3aa2207bf733", "b": "ext-G:1d9d637a3a48"} | +100 / +60 / +51 / +42 | +1 | +100 | +245 | +100 / +60 / +51 / +42 |  | 51% | 0.02 | 0.83 | +29 |  | S1-first-order | CANDIDATE (own-p only; family p 0.83) |
| J pair product | {"a": "ext-AB:3aa2207bf733", "b": "ext-G:1d9d637a3a48"} | +100 / +60 / +51 / +42 | +1 | +100 | +245 | +100 / +60 / +51 / +42 |  | 51% | 0.02 | 0.83 | +29 |  | S1-first-order | CANDIDATE (own-p only; family p 0.83) |
| J pair min | {"a": "ext-AB:1b5942ac8cd6", "b": "ext-G:1d9d637a3a48"} | +99 / +58 / +60 / +48 | -10 | +99 | -3098 | +99 / +53 / +56 / +42 | 1747.8 | 66% | 0.02 | 0.98 | +29 |  | S1-first-order | LEAD |
| J pair product | {"a": "ext-AB:1b5942ac8cd6", "b": "ext-G:1d9d637a3a48"} | +99 / +58 / +60 / +48 | -10 | +99 | -3098 | +99 / +53 / +56 / +42 | 1747.8 | 66% | 0.02 | 0.98 | +29 |  | S1-first-order | LEAD |
| J pair min | {"a": "ext-AB:3aa2207bf733", "b": "ext-D:D|dayloss_book_R|X1.0R_f0.00| | +98 / +13 / +52 / +29 | -10 | +99 | -3150 | +98 / +4 / +46 / +21 | 1229.0 | 39% | 0.02 | 0.73 | +29 |  | S1-first-order | LEAD |
| J pair product | {"a": "ext-AB:3aa2207bf733", "b": "ext-D:D|lock_daycap_loss|loss1R(liv | +98 / +13 / +52 / +29 | -10 | +99 | -3150 | +98 / +4 / +46 / +21 | 1229.0 | 39% | 0.02 | 0.73 | +29 |  | S1-first-order | LEAD |
| J pair min | {"a": "ext-AB:3aa2207bf733", "b": "ext-D:D|lock_daycap_loss|loss1R(liv | +98 / +13 / +52 / +29 | -10 | +99 | -3150 | +98 / +4 / +46 / +21 | 1229.0 | 39% | 0.02 | 0.73 | +29 |  | S1-first-order | LEAD |
| J pair product | {"a": "ext-AB:3aa2207bf733", "b": "ext-D:D|dayloss_book_R|X1.0R_f0.00| | +98 / +13 / +52 / +29 | -10 | +99 | -3150 | +98 / +4 / +46 / +21 | 1229.0 | 39% | 0.02 | 0.73 | +29 |  | S1-first-order | LEAD |
| J pair min | {"a": "ext-AB:cbcff1082b3a", "b": "ext-E:E|total_lots_cap|cap4_skip|se | +97 / -11 / +64 / +18 | +11 | +97 | +3583 | +97 / -0 / +67 / +26 | 689.1 | 45% | 0.02 | 0.02 | +29 |  | S1-first-order | CANDIDATE |
| J pair product | {"a": "ext-AB:cbcff1082b3a", "b": "ext-E:E|total_lots_cap|cap4_skip|se | +97 / -11 / +64 / +18 | +11 | +97 | +3583 | +97 / -0 / +67 / +26 | 689.1 | 45% | 0.02 | 0.02 | +29 |  | S1-first-order | CANDIDATE |

## Family K - P7

P7: 368 cells (368 down-only); best by equal-mean L6M maxDD cut: K6 ext-AB on P7 only {"cell": "c1d4e97d2d2c", "orig": "ext ext-AB {\"cell\": \"c1 cuts L6M maxDD +61% at equal lots (d mean +750 $/wk) and +62% at equal mean (PRE +39%, X' +5%); placebo p 0.02, family p 0.25, WF +44 -> CANDIDATE (own-p only; family p 0.25).

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K6 ext-AB on P7 only | {"cell": "c1d4e97d2d2c", "orig": "ext ext-AB {\"cell\": \"c1d4e97d2d2c | +61 / +37 / +37 / +3 | +2 | +58 | +750 | +62 / +39 / +39 / +5 | 55.4 | 11% | 0.02 | 0.25 | +44 |  | S1-first-order | CANDIDATE (own-p only; family p 0.25) |
| K6 ext-AB on P7 only | {"cell": "591e9de19fa5", "orig": "ext ext-AB {\"cell\": \"591e9de19fa5 | +59 / +34 / +38 / +7 | -1 | +58 | -248 | +58 / +33 / +38 / +6 | 50.3 | 9% | 0.03 | 0.16 | +44 |  | S1-first-order | LEAD |
| K6 ext-H on P7 only | {"cell": "91f3aa5bc2bd", "orig": "ext ext-H {\"cell\": \"91f3aa5bc2bd\ | +52 / +27 / +36 / +3 | +6 | +58 | +2055 | +55 / +32 / +40 / +9 | 46.6 | 9% | 0.03 | 0.33 | +44 |  | S1-first-order | CANDIDATE (own-p only; family p 0.33) |
| K6 ext-H on P7 only | {"cell": "e18edff4f8d3", "orig": "ext ext-H {\"cell\": \"e18edff4f8d3\ | +52 / +27 / +36 / +3 | +6 | +58 | +2055 | +55 / +32 / +40 / +9 | 46.6 | 9% | 0.03 | 0.33 | +44 |  | S1-first-order | CANDIDATE (own-p only; family p 0.33) |
| K6 ext-AB on P7 only | {"cell": "e9c5da0df842", "orig": "ext ext-AB {\"cell\": \"e9c5da0df842 | +51 / +25 / +37 / +18 | +5 | +53 | +1673 | +53 / +29 / +40 / +22 | 45.1 | 8% | 0.03 | 0.33 | +44 |  | S1-first-order | CANDIDATE (own-p only; family p 0.33) |
| K2 P7 first-in-session vs later | {"first": 1.0, "later": 0.0} | +66 / -34 / +58 / -1 | -35 | +59 | -11201 | +47 / -106 / +35 / -55 | 40.0 | 14% | 0.03 | 0.97 | +39 | -79775 | S1-first-order | LEAD |
| K6 I on P7 only | {"cell": "375f8bd0e8af", "orig": "I5 stack rolling Calmar {\"D\": 20,  | +58 / +43 / +54 / +9 | -21 | +52 | -6715 | +47 / +28 / +42 / -15 | 40.0 | 18% | 0.07 | 0.92 | +44 | -86010 | S1-first-order | LEAD |
| K6 ext-H on P7 only | {"cell": "308960e02253", "orig": "ext ext-H {\"cell\": \"308960e02253\ | +42 / +10 / +5 / +13 | +9 | +39 | +2746 | +47 / +17 / +12 / +20 | 39.5 | 7% | 0.02 | 0.02 | +44 |  | S1-first-order | CANDIDATE |
| K6 ext-AB on P7 only | {"cell": "4eb07bf9928b", "orig": "ext ext-AB {\"cell\": \"4eb07bf9928b | +40 / +37 / +43 / +21 | +8 | +44 | +2625 | +45 / +42 / +47 / +27 | 38.1 | 8% | 0.03 | 0.36 | +44 |  | S1-first-order | CANDIDATE (own-p only; family p 0.36) |
| K6 ext-AB on P7 only | {"cell": "dfa98761b49b", "orig": "ext ext-AB {\"cell\": \"dfa98761b49b | +47 / +31 / +42 / +27 | -5 | +41 | -1492 | +45 / +27 / +40 / +24 | 38.1 | 8% | 0.05 | 0.85 | +44 |  | S1-first-order | LEAD |

## Cross-family finalists (CANDIDATE / LEAD+ labels, top 25 by equal-mean L6M cut)

| technique | params | maxDD cut % L6M/HOLD/PRE/X' | worst-20 cut % L6M | Ulcer cut % L6M | d mean $/wk L6M | equal-mean cut % L6M/HOLD/PRE/X' | Calmar L6M | lot-change share | placebo p | family p | WF cut % | live week d$ | stage | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| J pair product | {"a": "ext-AB:3aa2207bf733", "b": "ext-G:1d9d637a3a48"} | +100 / +60 / +51 / +42 | +1 | +100 | +245 | +100 / +60 / +51 / +42 |  | 51% | 0.02 | 0.83 | +29 |  | S1-first-order | CANDIDATE (own-p only; family p 0.83) |
| J pair min | {"a": "ext-AB:3aa2207bf733", "b": "ext-G:1d9d637a3a48"} | +100 / +60 / +51 / +42 | +1 | +100 | +245 | +100 / +60 / +51 / +42 |  | 51% | 0.02 | 0.83 | +29 |  | S1-first-order | CANDIDATE (own-p only; family p 0.83) |
| J pair min | {"a": "ext-AB:cbcff1082b3a", "b": "ext-E:E|total_lots_cap|cap4_skip|se | +97 / -11 / +64 / +18 | +11 | +97 | +3583 | +97 / -0 / +67 / +26 | 689.1 | 45% | 0.02 | 0.02 | +29 |  | S1-first-order | CANDIDATE |
| J pair product | {"a": "ext-AB:cbcff1082b3a", "b": "ext-E:E|total_lots_cap|cap4_skip|se | +97 / -11 / +64 / +18 | +11 | +97 | +3583 | +97 / -0 / +67 / +26 | 689.1 | 45% | 0.02 | 0.02 | +29 |  | S1-first-order | CANDIDATE |
| J pair product | {"a": "ext-E:E|total_lots_cap|cap4_skip|sess_london", "b": "ext-H:91f3 | +92 / -28 / +57 / +39 | +2 | +94 | +774 | +92 / -25 / +58 / +41 | 255.2 | 54% | 0.02 | 0.02 | +29 |  | S1-first-order | CANDIDATE |
| J pair min | {"a": "ext-E:E|total_lots_cap|cap4_skip|sess_london", "b": "ext-H:91f3 | +92 / -28 / +57 / +39 | +2 | +94 | +774 | +92 / -25 / +58 / +41 | 255.2 | 54% | 0.02 | 0.02 | +29 |  | S1-first-order | CANDIDATE |
| J pair min | {"a": "ext-AB:cbcff1082b3a", "b": "ext-G:1d9d637a3a48"} | +89 / +67 / +29 / +32 | +7 | +91 | +2338 | +90 / +69 / +34 / +37 | 204.0 | 45% | 0.02 | 0.83 | +29 |  | S1-first-order | CANDIDATE (own-p only; family p 0.83) |
| J pair product | {"a": "ext-AB:cbcff1082b3a", "b": "ext-G:1d9d637a3a48"} | +89 / +67 / +29 / +32 | +7 | +91 | +2338 | +90 / +69 / +34 / +37 | 204.0 | 45% | 0.02 | 0.83 | +29 |  | S1-first-order | CANDIDATE (own-p only; family p 0.83) |
| J pair min | {"a": "ext-E:E|newentry_haircut_day_dd|Y24000_f0.0|ALL", "b": "ext-H:9 | +88 / +41 / +43 / +35 | +3 | +91 | +1026 | +88 / +43 / +44 / +37 | 178.2 | 41% | 0.02 | 0.02 | +29 |  | S1-first-order | CANDIDATE |
| J pair product | {"a": "ext-E:E|newentry_haircut_day_dd|Y24000_f0.0|ALL", "b": "ext-H:9 | +88 / +41 / +43 / +35 | +3 | +91 | +1026 | +88 / +43 / +44 / +37 | 178.2 | 41% | 0.02 | 0.02 | +29 |  | S1-first-order | CANDIDATE |
| J pair min | {"a": "ext-G:1d9d637a3a48", "b": "ext-H:e18edff4f8d3"} | +85 / +40 / +7 / +16 | +10 | +85 | +3252 | +86 / +46 / +16 / +24 | 151.3 | 30% | 0.02 | 0.76 | +29 |  | S1-first-order | CANDIDATE (own-p only; family p 0.76) |
| J pair product | {"a": "ext-G:1d9d637a3a48", "b": "ext-H:e18edff4f8d3"} | +85 / +40 / +7 / +16 | +10 | +85 | +3252 | +86 / +46 / +16 / +24 | 151.3 | 30% | 0.02 | 0.76 | +29 |  | S1-first-order | CANDIDATE (own-p only; family p 0.76) |
| J pair min | {"a": "ext-AB:cbcff1082b3a", "b": "ext-H:308960e02253"} | +85 / +54 / +39 / +29 | +5 | +86 | +1518 | +86 / +56 / +42 / +32 | 150.3 | 35% | 0.02 | 0.02 | +29 |  | S1-first-order | CANDIDATE |
| J pair product | {"a": "ext-AB:cbcff1082b3a", "b": "ext-H:308960e02253"} | +85 / +54 / +39 / +29 | +5 | +86 | +1518 | +86 / +56 / +42 / +32 | 150.3 | 35% | 0.02 | 0.02 | +29 |  | S1-first-order | CANDIDATE |
| J pair min | {"a": "ext-AB:cbcff1082b3a", "b": "ext-E:E|total_lots_cap|cap4_trunc|s | +84 / +15 / +63 / +33 | +10 | +88 | +3327 | +86 / +23 / +66 / +39 | 147.9 | 48% | 0.02 | 0.02 | +29 |  | S1-first-order | CANDIDATE |
| J pair product | {"a": "ext-AB:cbcff1082b3a", "b": "ext-E:E|total_lots_cap|cap4_trunc|s | +84 / +15 / +63 / +33 | +10 | +88 | +3327 | +86 / +23 / +66 / +39 | 147.9 | 48% | 0.02 | 0.02 | +29 |  | S1-first-order | CANDIDATE |
| J pair product | {"a": "ext-AB:cbcff1082b3a", "b": "ext-E:E|newentry_haircut_day_dd|Y24 | +84 / +47 / +44 / +35 | +12 | +88 | +3895 | +86 / +53 / +50 / +42 | 147.3 | 32% | 0.02 | 0.02 | +29 |  | S1-first-order | CANDIDATE |
| J pair min | {"a": "ext-AB:cbcff1082b3a", "b": "ext-E:E|newentry_haircut_day_dd|Y24 | +84 / +47 / +44 / +35 | +12 | +88 | +3895 | +86 / +53 / +50 / +42 | 147.3 | 32% | 0.02 | 0.02 | +29 |  | S1-first-order | CANDIDATE |
| J pair product | {"a": "ext-AB:3aa2207bf733", "b": "ext-E:E|total_lots_cap|cap4_trunc|s | +85 / +16 / +66 / +43 | +2 | +89 | +496 | +85 / +18 / +67 / +44 | 139.8 | 54% | 0.02 | 0.73 | +29 |  | S1-first-order | CANDIDATE (own-p only; family p 0.73) |
| J pair min | {"a": "ext-AB:3aa2207bf733", "b": "ext-E:E|total_lots_cap|cap4_trunc|s | +85 / +16 / +66 / +43 | +2 | +89 | +496 | +85 / +18 / +67 / +44 | 139.8 | 54% | 0.02 | 0.73 | +29 |  | S1-first-order | CANDIDATE (own-p only; family p 0.73) |
| J pair min | {"a": "ext-AB:cbcff1082b3a", "b": "ext-D:D|dayloss_stack$|X16000_f0.00 | +84 / +27 / +54 / +24 | +3 | +88 | +1068 | +85 / +29 / +56 / +26 | 135.8 | 35% | 0.02 | 0.02 | +29 |  | S1-first-order | CANDIDATE |
| J pair product | {"a": "ext-AB:cbcff1082b3a", "b": "ext-D:D|dayloss_stack$|X16000_f0.00 | +84 / +27 / +54 / +24 | +3 | +88 | +1068 | +85 / +29 / +56 / +26 | 135.8 | 35% | 0.02 | 0.02 | +29 |  | S1-first-order | CANDIDATE |
| J pair min | {"a": "ext-E:E|total_lots_cap|cap4_trunc|sess_london", "b": "ext-H:91f | +80 / +10 / +59 / +53 | +2 | +85 | +764 | +80 / +12 / +60 / +54 | 106.3 | 57% | 0.02 | 0.12 | +29 |  | S1-first-order | CANDIDATE (own-p only; family p 0.12) |
| J pair product | {"a": "ext-E:E|total_lots_cap|cap4_trunc|sess_london", "b": "ext-H:91f | +80 / +10 / +59 / +53 | +2 | +85 | +764 | +80 / +12 / +60 / +54 | 106.3 | 57% | 0.02 | 0.12 | +29 |  | S1-first-order | CANDIDATE (own-p only; family p 0.12) |
| J pair min | {"a": "ext-AB:cbcff1082b3a", "b": "ext-F:8a2dbfb34401"} | +78 / +40 / +43 / +15 | +0 | +79 | +42 | +78 / +40 / +43 / +15 | 95.9 | 32% | 0.02 | 0.02 | +29 |  | S1-first-order | CANDIDATE |
