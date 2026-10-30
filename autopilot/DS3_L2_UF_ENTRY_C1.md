# DS3_L2_UF_ENTRY_C1 - L2-UNTIL-FOUND cycle 1, ENTRY side: the 70/30 split as base (agent UF-ENTRY, 2026-10-30)
Research only; no live/execution change; UNTOUCHED never read. Prereg autopilot/UF_ENTRY_C1_prereg.md sha256 d3990e55013cce00861a1453be98c43599b6de295b91ea4de5c2ce425528c536 (DECISIONS.md, before any cell statistic), 280 cells spec sha256 27141cbebf8cf57a9265cd8be7eb467746e7f095055c0bb66bb4cf3cda02f75b; PRE-only selection file out/uf/entry_c1/pre_sel.json (copy autopilot/UF_ENTRY_C1_PRESEL.json) sha256 e0677a905206f1b69b4b20caff49aa1aa5d5e330da4a1bd07f5ff833e17b8885 logged before the recent look; ONE look at 2026/L6M/HOLD (stage B). Own masks: 2026 = 20260101..0206 (~5 real weeks: a sign, not a size), L6M 20250801..0206, HOLD 20250701..0206, PRE 20240201..20250630, X' 20230401..20240131; WINMASK/WINS unused, every frame cut at 20260206.
Units: Delta $/week on the exact lock engine (ST HM WT KB SM PE, L2SJ/EQR engine, plain sum at live lots) at EQUAL RISK (EQR frame A: lots scaled by c* with the sweep cost so that worst-20-weeks over WF = PRE u HOLD equals the comparison series; c* in the last column), (MDE80 = 2.8 SE) in parentheses. Base = the 70/30 split (F .7, dip 3, 1of8 default gates, veto imb5<=-0.40, risk-capped remainder, stop at the original level, target re-based). Reproduction check before the prereg: split vs market N: c* 1.064, L6M +22.6k, HOLD +22.6k, PRE +7.7k (published), M c1 +13.3k/+11.6k/+7.6k, LIVE-CAL c1 +15.1k/+16.0k (= LIVE_CAL_SUMMARY). Bases: N (no target correction) primary, M beside, L = LIVE-CAL (N + stop-class exits 2.45 pt instead of 1.01; LIVE_CAL_SUMMARY; live evidence on targets: 11 touched targets, all filled, none marginal; M-vs-N for marginal touches undecided). +pt/fill = extra adverse cost per remainder lot-fill (0/1/2), applied to the cell AND to the split it is compared with.

## 0. Plain verdict
* **Nothing beats the split. 0 of 268 new cells clears the split in all five windows with a size above its MDE; at +0 pt/fill only 8 cells are >= 0 vs the split in all five windows on N, and 6 of those 8 are the split itself in disguise (4 hma_sp regime cells whose switch was always OFF, delta 0.0; skip-if-imb<-0.4 = 0.0; skip-if-imb<-0.2 +0.9k L6M); the two non-trivial ones are +1.1k (st1_age regime) and +2.3k L6M / 0.0 HOLD (resting-limit F.9 X8), both inside MDE**. White RC over the 268 new cells vs the split (N): L6M maxt 3.06, p 0.519, cum-adj p 1.000; HOLD maxt 2.49, p 0.558, cum-adj p 1.000; PRE maxt 0.71, p 0.994, cum-adj p 1.000 (best cells: DLT_10_30 add at 8 pt, thick-book half split, two-add 50/50 - all PRE-negative). The cumulative-adjusted p uses N_cum = 143,584 stored cells (81,198 distinct specs) + 268; it is 1.0 everywhere.
* **What moved is the cost fragility, not the mean.** PRE-selected cell `UF1|G1|F=0.9|X=8|N=0` (90% at market at the signal, 10% risk-capped on a plain 8-pt dip, veto imb5<=-0.40, no gate; rank 1 by SEL t = 2.44 among cells >= 0 vs the split in PRE and X' and >= 0 vs market at +1 pt in PRE and X'; 6 such cells, all F=.8-.9 with X 5-8): vs market on N it makes L6M +24.4k (15.1k), HOLD +21.7k (17.0k), PRE +9.0k (10.6k), X' +10.7k (9.5k), 2026 +32.1k (41.5k) - the same as the split (+22.6k/+22.6k/+7.7k/+3.3k) - and at +2 pt per remainder fill it still makes +19.4k / +17.1k / +3.5k / +6.7k, where the split falls to +1.8k / +3.1k / -8.6k / -6.7k (break-even of the split about +1 pt in PRE, +2.5 in HOLD). Versus the split itself it is flat at +0 pt (L6M +1.6k (14.4k), HOLD -0.8k (13.5k), PRE +1.2k (9.1k), X' +6.9k (8.8k), 2026 +10.9k (29.9k)) and +11.3k / +7.9k / +6.9k / +10.4k at +1 pt, +17.8k / +14.0k / +12.2k / +13.5k at +2 pt.
* Honest tier: against the split floor the cell does NOT beat it at the measured cost (HOLD sign negative, CI(PRE) [-5.0k, +7.7k] includes 0, RC p 0.5): **BEST-AVAILABLE-NEGATIVE as an improvement over the split at +0 pt**. As a rule vs market entry (the split's own claim) it is **CANDIDATE-RECENT**: >= 0 in all five windows on N, L and M, at +0, +1 and +2 pt; CI(PRE) vs market [+1.5k, +16.5k] excludes 0 (the split's was [-0.3k, +15.3k]); fails placebo (no book information in the rule: a size/price mix - non-gated cells fail by prereg), maxDD(engine) (748k vs 651k HOLD), RC (single-test t 4.5 L6M; cumulative-adjusted p 0.38 L6M, 1.0 HOLD) and no independent forward evidence. Not PASS.
* **The split's gate is informative against the placebo (new)**: random gate at the same add-fill rate and book bits shuffled within label day (20 draws each, delta vs the real split at equal risk): the real split ranks 1.00 / 1.00 / 1.00 in L6M / HOLD / PRE (0.95/0.85 in 2026, 0.65/0.55 in X'). The earlier L2SE placebo (same-fill-count Bernoulli per second, rank 0.79 PRE) was a different construction; both are reported. At F=0.9 X=8 the gate is worthless (N=1 vs N=0 identical, placebo rank 0.20/0.15/0.45).
* Everything else in the cycle is dead or noise: L2-event add triggers (-8.5k L6M avg vs split, PRE -14.1k; absorption/iceberg fire too rarely at 1-s), first-pullback basis (-30k, the clear loser), remainder expiry (-10k: the late dips are the profitable ones), remainder chase (-10k), resting limit at the level (-8.4k avg; F.9 X8 variant = the selected cell +2.3k L6M), thin/thick book condition (-1.6k avg; thick book keeps the add, thin does not: thick1.0 half split +15.2k L6M but PRE -5.7k), book-sized remainder (-3.3k), conditional limit-join (+0.4k avg, noise), two adds (+2.1k L6M avg, PRE -5.2k).
* **EINT1 regime sizer (G11):** the explicit walk-forward switch (refit quarterly, trailing 12 m of closed trades) turned OFF for sig_st1_age at 2024-10 and again from 2025-04 (trailing top-minus-bottom tercile spread of market-entry pts negative: -1.29, -0.40, -0.97, -0.01, -0.39 pts at the refits 2024-10, 2025-04, 2025-07, 2025-10, 2026-01), for htf_vwap_atr in 2025-07 and 2025-10 (-0.12, -0.10), and the hma_sp switch never turned on (cells identical to the split). The trailing-12-month spread of measured market-entry pts does not show the EINT1 recent-regime pattern, so the switch adds only +0.1k L6M (MDE 14k) vs the split. Not checked in detail: htf_gap_eth logs (see meta.pkl RLOG). The EINT1 pattern is visible with hindsight terciles; a causal trailing switch lags or misses it.
* Not run: MBO order lifetimes / queue position / fleeting-order share (no MBO tables on disk; only mbp-10 1-s and 100 ms 5-level), 250 ms evaluation (price path is 1 s). LIVE-CAL columns below.

## 1. SETTINGS TABLE (recent windows first; Delta $/wk at equal risk, MDE80 in parentheses)
Selection: PRE-selected cell chosen on SEL = PRE u X' only (not on the looked windows). Rows: the selected cell, the floor (split vs market), and the best-in-hindsight L6M-ranked cells vs the split (SELECTED ON LOOKED DATA, stated as such).
| row | basis | +pt/fill | ref | 2026 (~5 wk) | L6M | HOLD | PRE | X' | c* |
|--|--|--|--|--|--|--|--|--|--|
| F.9 X8 N0 (PRE-selected) | N | 0 | vs split | +10.9k (29.9k) | +1.6k (14.4k) | -0.8k (13.5k) | +1.2k (9.1k) | +6.9k (8.8k) | 1.027 |
| F.9 X8 N0 (PRE-selected) | N | 0 | vs market | +32.1k (41.5k) | +24.4k (15.1k) | +21.7k (17.0k) | +9.0k (10.6k) | +10.7k (9.5k) | 1.093 |
| F.9 X8 N0 (PRE-selected) | N | 1 | vs split | +11.7k (26.2k) | +11.3k (12.0k) | +7.9k (12.5k) | +6.9k (9.7k) | +10.4k (9.3k) | 1.049 |
| F.9 X8 N0 (PRE-selected) | N | 1 | vs market | +30.2k (39.4k) | +21.7k (14.5k) | +19.2k (16.1k) | +6.4k (10.3k) | +8.5k (9.3k) | 1.079 |
| F.9 X8 N0 (PRE-selected) | N | 2 | vs split | +16.7k (35.4k) | +17.8k (14.5k) | +14.0k (14.5k) | +12.2k (10.0k) | +13.5k (9.7k) | 1.078 |
| F.9 X8 N0 (PRE-selected) | N | 2 | vs market | +27.0k (37.4k) | +19.4k (14.2k) | +17.1k (15.5k) | +3.5k (10.2k) | +6.7k (9.3k) | 1.068 |
| F.9 X8 N0 (PRE-selected) | L | 0 | vs split | +4.7k (47.6k) | +3.1k (13.1k) | +1.1k (12.1k) | +0.2k (8.8k) | +5.3k (8.6k) | 1.017 |
| F.9 X8 N0 (PRE-selected) | L | 0 | vs market | +21.0k (40.8k) | +22.0k (15.2k) | +20.0k (15.8k) | +6.7k (10.5k) | +8.5k (9.3k) | 1.072 |
| F.9 X8 N0 (PRE-selected) | L | 1 | vs split | +1.8k (42.2k) | +8.9k (13.3k) | +6.4k (12.8k) | +3.6k (9.4k) | +7.9k (8.8k) | 1.041 |
| F.9 X8 N0 (PRE-selected) | L | 1 | vs market | +14.8k (31.7k) | +18.5k (14.1k) | +16.8k (14.4k) | +2.7k (10.3k) | +6.4k (9.1k) | 1.055 |
| F.9 X8 N0 (PRE-selected) | L | 2 | vs split | -4.9k (34.8k) | +10.8k (13.0k) | +8.6k (12.3k) | +8.5k (9.8k) | +11.0k (9.2k) | 1.068 |
| F.9 X8 N0 (PRE-selected) | L | 2 | vs market | +5.6k (32.0k) | +13.2k (14.6k) | +12.1k (14.5k) | +0.1k (10.2k) | +4.9k (9.1k) | 1.044 |
| F.9 X8 N0 (PRE-selected) | M | 0 | vs split | -15.2k (25.7k) | +1.5k (15.2k) | -0.6k (14.6k) | +1.0k (9.6k) | +5.7k (8.8k) | 1.045 |
| F.9 X8 N0 (PRE-selected) | M | 0 | vs market | +4.3k (35.4k) | +14.9k (17.0k) | +11.1k (16.4k) | +8.8k (11.6k) | +8.5k (9.4k) | 1.048 |
| F.9 X8 N0 (PRE-selected) | M | 1 | vs split | -16.4k (34.0k) | +5.3k (17.1k) | +2.9k (16.8k) | +8.1k (10.1k) | +8.1k (8.9k) | 1.076 |
| F.9 X8 N0 (PRE-selected) | M | 1 | vs market | +2.7k (34.7k) | +12.4k (16.6k) | +8.7k (16.0k) | +6.7k (11.1k) | +7.1k (9.4k) | 1.042 |
| F.9 X8 N0 (PRE-selected) | M | 2 | vs split | -9.7k (32.2k) | +8.3k (17.5k) | +5.4k (17.7k) | +15.9k (11.1k) | +11.9k (9.9k) | 1.112 |
| F.9 X8 N0 (PRE-selected) | M | 2 | vs market | +3.6k (34.6k) | +10.1k (16.4k) | +6.3k (15.7k) | +5.3k (10.9k) | +5.6k (9.4k) | 1.035 |
| 70/30 split (floor) | N | 0 | vs market | +20.5k (43.8k) | +22.6k (16.4k) | +22.6k (16.0k) | +7.7k (11.4k) | +3.3k (8.8k) | 1.064 |
| 70/30 split (floor) | N | 1 | vs market | +18.2k (39.5k) | +10.1k (15.5k) | +11.1k (14.8k) | -0.8k (11.4k) | -2.2k (8.7k) | 1.029 |
| 70/30 split (floor) | N | 2 | vs market | +10.4k (39.1k) | +1.8k (16.1k) | +3.1k (14.8k) | -8.6k (11.9k) | -6.7k (8.6k) | 0.991 |
| 70/30 split (floor) | L | 0 | vs market | +16.0k (44.4k) | +18.7k (15.9k) | +18.9k (15.5k) | +6.5k (11.9k) | +3.0k (8.8k) | 1.054 |
| 70/30 split (floor) | L | 1 | vs market | +13.0k (39.9k) | +9.4k (15.5k) | +10.4k (14.6k) | -1.0k (11.4k) | -1.7k (8.6k) | 1.014 |
| 70/30 split (floor) | L | 2 | vs market | +10.3k (36.4k) | +2.7k (16.1k) | +3.7k (14.6k) | -8.3k (11.2k) | -5.9k (8.7k) | 0.978 |
| 70/30 split (floor) | M | 0 | vs market | +19.5k (41.7k) | +13.4k (14.5k) | +11.6k (14.0k) | +7.8k (11.3k) | +2.8k (8.4k) | 1.003 |
| 70/30 split (floor) | M | 1 | vs market | +18.5k (44.1k) | +7.3k (14.5k) | +5.9k (14.2k) | -1.2k (11.5k) | -0.7k (8.5k) | 0.968 |
| 70/30 split (floor) | M | 2 | vs market | +12.6k (42.7k) | +2.4k (13.7k) | +1.3k (14.1k) | -9.5k (11.7k) | -5.5k (9.2k) | 0.931 |

### Same table, resting-limit variant of the selected mix (`G4 rest F=0.9 X=8 exp=0`, limit at the dip level from the signal, 1-tick through fill; fill at the level has no slippage but is the optimistic convention)
| row | basis | +pt/fill | ref | 2026 (~5 wk) | L6M | HOLD | PRE | X' | c* |
|--|--|--|--|--|--|--|--|--|--|
| F.9 X8 rest-limit | N | 0 | vs split | +11.1k (27.6k) | +2.3k (14.7k) | +0.0k (13.7k) | +1.4k (8.5k) | +6.1k (8.9k) | 1.032 |
| F.9 X8 rest-limit | N | 0 | vs market | +32.2k (40.0k) | +25.0k (15.8k) | +22.6k (17.5k) | +9.2k (10.4k) | +9.8k (9.4k) | 1.098 |
| F.9 X8 rest-limit | N | 1 | vs split | +10.7k (25.2k) | +11.5k (13.2k) | +8.3k (13.3k) | +7.2k (9.3k) | +10.0k (9.5k) | 1.054 |
| F.9 X8 rest-limit | N | 1 | vs market | +29.2k (36.4k) | +21.9k (14.9k) | +19.7k (16.4k) | +6.6k (10.2k) | +8.1k (9.2k) | 1.084 |
| F.9 X8 rest-limit | N | 2 | vs split | +16.0k (32.7k) | +17.8k (14.8k) | +14.4k (14.6k) | +13.3k (10.1k) | +13.2k (10.0k) | 1.082 |
| F.9 X8 rest-limit | N | 2 | vs market | +26.2k (35.2k) | +19.4k (14.2k) | +17.4k (15.5k) | +4.5k (10.0k) | +6.3k (9.1k) | 1.072 |
| F.9 X8 rest-limit | L | 0 | vs split | -2.2k (35.6k) | -0.0k (12.0k) | -1.5k (10.9k) | -1.2k (8.7k) | +4.2k (8.7k) | 1.001 |
| F.9 X8 rest-limit | L | 0 | vs market | +13.6k (34.0k) | +18.6k (14.4k) | +17.3k (14.6k) | +5.2k (9.8k) | +7.4k (9.0k) | 1.056 |
| F.9 X8 rest-limit | L | 1 | vs split | -1.2k (33.8k) | +5.7k (12.7k) | +3.7k (11.9k) | +3.4k (9.1k) | +7.4k (8.7k) | 1.031 |
| F.9 X8 rest-limit | L | 1 | vs market | +11.8k (32.1k) | +15.2k (13.9k) | +14.1k (13.9k) | +2.5k (9.8k) | +5.8k (8.8k) | 1.045 |
| F.9 X8 rest-limit | L | 2 | vs split | -1.8k (34.0k) | +7.9k (12.6k) | +6.2k (11.6k) | +8.1k (9.5k) | +10.4k (9.0k) | 1.055 |
| F.9 X8 rest-limit | L | 2 | vs market | +8.5k (27.8k) | +10.4k (13.9k) | +9.8k (13.6k) | -0.4k (9.7k) | +4.2k (8.7k) | 1.032 |
| F.9 X8 rest-limit | M | 0 | vs split | -14.8k (25.2k) | +0.2k (14.9k) | -1.4k (13.9k) | -0.4k (9.0k) | +4.9k (8.9k) | 1.041 |
| F.9 X8 rest-limit | M | 0 | vs market | +4.6k (35.1k) | +13.7k (17.2k) | +10.3k (16.5k) | +7.3k (11.6k) | +7.7k (9.5k) | 1.045 |
| F.9 X8 rest-limit | M | 1 | vs split | -16.0k (32.8k) | +4.5k (16.8k) | +2.5k (16.0k) | +6.5k (9.2k) | +7.3k (8.8k) | 1.068 |
| F.9 X8 rest-limit | M | 1 | vs market | +3.0k (34.4k) | +11.6k (16.8k) | +8.4k (16.0k) | +5.1k (11.2k) | +6.4k (9.4k) | 1.034 |
| F.9 X8 rest-limit | M | 2 | vs split | -9.8k (30.2k) | +8.3k (17.0k) | +6.1k (16.9k) | +13.9k (10.3k) | +10.9k (9.5k) | 1.095 |
| F.9 X8 rest-limit | M | 2 | vs market | +3.4k (34.2k) | +10.1k (16.3k) | +7.0k (15.5k) | +3.5k (10.2k) | +4.7k (9.3k) | 1.020 |

### L6M-ranked best cells vs the split, N basis, +0 pt (SELECTED ON LOOKED DATA; every one is PRE-negative)
| cid | cell | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|
| 67 | UF1|G2|F=0.7|X=8|ev=DLT_10_30 | +70.1k (73.5k) | +17.2k (25.9k) | +12.6k (23.5k) | -9.0k (14.4k) | +1.5k (13.8k) |
| 142 | UF1|G5|F=0.5|X=3|thick1.0|N=1 | +48.7k (42.9k) | +15.2k (22.6k) | +12.7k (20.0k) | -5.7k (13.9k) | -6.2k (11.8k) |
| 147 | UF1|G5|F=0.5|X=5|thick1.0|N=1 | +49.3k (46.6k) | +12.8k (26.2k) | +10.9k (23.4k) | -12.7k (16.0k) | +3.1k (14.9k) |
| 94 | UF1|G3|F=0.5|X1=3|X2=8|N=0 | +25.8k (33.6k) | +12.2k (13.4k) | +10.7k (12.0k) | -7.1k (13.0k) | +1.8k (11.9k) |
| 75 | UF1|G2|F=0.7|X=8|ev=SWEEP | +58.1k (52.7k) | +11.4k (22.8k) | +7.6k (20.5k) | -8.9k (15.2k) | +1.9k (14.5k) |
| 74 | UF1|G2|F=0.7|X=5|ev=SWEEP | +27.2k (33.2k) | +10.8k (20.8k) | +8.3k (18.7k) | -3.7k (9.8k) | +1.7k (12.3k) |
| 63 | UF1|G2|F=0.7|X=8|ev=DLT_5_10 | +37.9k (65.0k) | +9.4k (22.5k) | +5.8k (20.2k) | -5.0k (12.9k) | +2.5k (12.6k) |
| 83 | UF1|G2|F=0.5|X=5|ev=DLT_5_10 | +44.0k (51.7k) | +9.2k (23.4k) | +6.9k (21.0k) | -3.8k (15.7k) | +2.4k (15.1k) |
| 119 | UF1|G4|rest|F=0.7|X=8|exp=0 | +39.4k (25.1k) | +9.2k (15.2k) | +7.1k (13.6k) | -4.2k (11.7k) | +5.0k (10.1k) |
| 14 | UF1|G1|F=0.6|X=8|N=0 | +36.4k (48.7k) | +8.7k (19.4k) | +5.4k (17.5k) | -8.1k (15.5k) | +4.9k (12.6k) |

### The 10 best cells by SEL t (PRE-only ranking) vs the split, N, +0 pt
| cid | cell | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|
| 28 | UF1|G1|F=0.8|X=5|N=0 | +3.4k (29.0k) | -1.3k (11.4k) | -3.1k (10.5k) | -0.1k (6.7k) | +0.6k (6.9k) |
| 29 | UF1|G1|F=0.8|X=5|N=1 | +3.2k (25.6k) | -0.2k (11.8k) | -2.0k (10.9k) | -1.0k (7.5k) | +0.7k (7.1k) |
| 36 | UF1|G1|F=0.9|X=5|N=0 | +8.8k (20.1k) | -3.5k (11.1k) | -4.7k (10.1k) | +1.3k (8.0k) | +0.7k (6.5k) |
| 38 | UF1|G1|F=0.9|X=8|N=0 | +10.9k (29.9k) | +1.6k (14.4k) | -0.8k (13.5k) | +1.2k (9.1k) | +6.9k (8.8k) |
| 39 | UF1|G1|F=0.9|X=8|N=1 | +11.0k (29.1k) | +1.6k (14.1k) | -1.2k (13.4k) | +0.7k (9.1k) | +6.0k (9.0k) |
| 127 | UF1|G4|rest|F=0.9|X=8|exp=0 | +11.1k (27.6k) | +2.3k (14.7k) | +0.0k (13.7k) | +1.4k (8.5k) | +6.1k (8.9k) |


## 2. Family map (mean over the family's new cells, delta vs the split, N basis, equal risk)
| family | n | Y26 | L6M | HOLD | PRE | X |
|--|--|--|--|--|--|--|
| G1 | 28 | +5.3k | -5.2k | -5.4k | -3.3k | -0.5k |
| G10 | 24 | +6.1k | +0.4k | -0.0k | -2.6k | +0.7k |
| G11 | 20 | +2.1k | +0.1k | -0.2k | -1.4k | -0.9k |
| G2 | 48 | +17.7k | -8.5k | -9.3k | -14.1k | -3.3k |
| G3 | 16 | +17.8k | +2.1k | +0.9k | -5.2k | +1.6k |
| G4 | 36 | +4.8k | -8.4k | -9.0k | -8.1k | -1.0k |
| G5 | 20 | +18.1k | -1.6k | -3.5k | -10.0k | -1.5k |
| G6 | 12 | +18.7k | -3.3k | -4.0k | -8.8k | -1.0k |
| G7 | 24 | +0.7k | -10.1k | -10.0k | -10.4k | -5.5k |
| G8 | 8 | -6.2k | -10.1k | -9.5k | -11.4k | -6.2k |
| G9 | 32 | -12.8k | -30.3k | -30.5k | -24.1k | -15.6k |

| family (+1 pt per remainder fill, vs split at +1) | Y26 | L6M | HOLD | PRE | X |
|--|--|--|--|--|--|
| G1 | +2.9k | +0.0k | -0.8k | -1.7k | +0.8k |
| G10 | +5.7k | +3.8k | +2.8k | -1.5k | +0.8k |
| G11 | +2.0k | +1.0k | +0.7k | -0.9k | -0.5k |
| G2 | +14.6k | -3.2k | -4.6k | -12.1k | -2.1k |
| G3 | +12.1k | +4.2k | +2.3k | -6.8k | +0.4k |
| G4 | +2.9k | -4.1k | -5.1k | -7.1k | -0.7k |
| G5 | +11.9k | +1.0k | -1.5k | -10.2k | -2.2k |
| G6 | +13.6k | +0.0k | -1.3k | -9.0k | -2.1k |
| G7 | -3.4k | -6.3k | -6.8k | -10.2k | -5.1k |
| G8 | -6.8k | -3.9k | -4.0k | -7.4k | -4.3k |
| G9 | -16.0k | -25.3k | -26.1k | -22.1k | -14.0k |

## 3. Gates, placebo, RC, tails for the PRE-selected cell
* Placebo (delta vs the real split at equal risk; rank = share of placebo draws the real cell beats):
| cell | placebo | 2026 | L6M | HOLD | PRE | X' | note |
|--|--|--|--|--|--|--|--|
| UF1|G1|F=0.7|X=3|N=1 | P1 random gate, same add rate (20 draws), rank | 0.95 | 1.00 | 1.00 | 1.00 | 0.65 | real delta vs split 0.0, 0.0, 0.0, 0.0, 0.0k |
| UF1|G1|F=0.7|X=3|N=1 | P2 book shuffled within day (20 draws), rank | 0.85 | 1.00 | 1.00 | 1.00 | 0.55 | real delta vs split 0.0, 0.0, 0.0, 0.0, 0.0k |
| UF1|G1|F=0.9|X=8|N=1 | P1 random gate, same add rate (20 draws), rank | 0.05 | 0.20 | 0.15 | 0.45 | 0.25 | real delta vs split 11.0, 1.6, -1.2, 0.7, 6.0k |
| UF1|G1|F=0.9|X=8|N=1 | P2 book shuffled within day (20 draws), rank | 0.00 | 0.20 | 0.15 | 0.25 | 0.35 | real delta vs split 11.0, 1.6, -1.2, 0.7, 6.0k |
| UF1|G10|joinIfWith0.3|T=5|F=0.7|X=3 | P1 random gate, same add rate (20 draws), rank | 0.95 | 1.00 | 1.00 | 0.95 | 0.55 | real delta vs split 0.1, -0.4, -1.2, -0.2, -0.1k |
| UF1|G10|joinIfWith0.3|T=5|F=0.7|X=3 | P2 book shuffled within day (20 draws), rank | 0.85 | 1.00 | 1.00 | 0.95 | 0.55 | real delta vs split 0.1, -0.4, -1.2, -0.2, -0.1k |
| UF1|G11|WF3m|sig_st1_age|Fhi=0.9|Flo=0.7 | P1 random gate, same add rate (20 draws), rank | 0.95 | 1.00 | 1.00 | 0.80 | 0.65 | real delta vs split 0.5, 1.1, 0.9, 0.3, 0.7k |
| UF1|G11|WF3m|sig_st1_age|Fhi=0.9|Flo=0.7 | P2 book shuffled within day (20 draws), rank | 0.85 | 1.00 | 1.00 | 0.80 | 0.50 | real delta vs split 0.5, 1.1, 0.9, 0.3, 0.7k |

  `UF1|G1|F=0.9|X=8|N=0` and the rest-limit variant have no book information (N=0, price-only dip): placebo not applicable = FAIL by prereg. G11 and G10 cells that equal the split by construction rank like the split.
* V2 gates vs the split / vs market: mean_up (PRE>0) yes/yes; holdout_sign (HOLD>0) NO (-0.8k) / yes; SPAN2 (X'>0) yes/yes; CI(PRE lo>0) NO / yes; cost (+1, +2 pt) yes/yes; year_share <= 60% 0.61 (fail) / 0.41 (pass); maxDD(engine, HOLD) 703k vs split 625k fail; neighbours (F .8-.9, X 5-8, N=0, PRE sign vs split): F=0.8 X=5 PRE -0.1k, F=0.8 X=8 PRE -5.3k, F=0.9 X=5 PRE +1.3k -> mixed; RC fail; placebo n/a fail.
* Tail HOLD (sd / worst-20 weeks sum, at c*): selected 184k / -0.83M vs split 169k / -0.63M. Year sums of the delta vs the split (k$): 2023 +225, 2024 +167, 2025 -90, 2026 +66.
* RC over the cycle's 268 new cells (sign: bootstrap of centred weekly deltas, 4000 draws, max t), delta vs the split: N L6M maxt 3.06, p 0.519, cum-adj p 1.000; N HOLD maxt 2.49, p 0.558, cum-adj p 1.000; M L6M maxt 2.70, p 0.583, cum-adj p 1.000; LIVE-CAL L6M maxt 2.59, p 0.488, cum-adj p 1.000. Delta vs market (the split family's own claim): N L6M maxt 4.73, p 0.008, cum-adj p 0.988; N HOLD maxt 4.52, p 0.011, cum-adj p 0.997; best cell `UF1|G5|F=0.7|X=5|thick0.7|N=1` - a split cell. Cumulative adjustment: 1-(1-p)^((143,584+268)/268), conservative because the stored cells are correlated neighbours (the distinct-spec count 81,198 gives 0.92 for the same line). The selected cell, single test vs market N L6M: t 4.50, Sidak over N_cum p 0.38; vs the split N L6M: t 0.32.
* Session cells (row attribution, N basis, c=1, delta vs the split, $k/wk; no per-cell MDE, all inside the stack MDE 14k):
| D6 session cell | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| KB asia | +1.5k | +0.4k | +0.5k | -0.0k | -0.1k |
| PE london | +1.4k | +0.7k | +0.8k | -0.1k | +0.3k |
| HM asia | +2.7k | +1.3k | +1.1k | +0.4k | -1.3k |
| HM nyam | -0.5k | +0.4k | +0.3k | -1.2k | +0.0k |
| SM asia | -0.1k | -0.3k | -0.8k | +0.3k | +0.5k |
| SM london | +0.1k | -0.0k | +0.1k | -0.4k | +0.1k |
| ST asia | +1.0k | +0.6k | -0.4k | +1.6k | +0.6k |
| WT london | -1.1k | -1.4k | -1.1k | -0.5k | +0.8k |
| PE asia | +3.4k | +1.0k | +1.0k | -0.3k | +0.2k |

## 4. What was learned
1. The split gain is not improved by any L2 add trigger, size, expiry or basis tried; it is a plateau in F and X. Moving the mix toward market (F .9) and deeper (X 8) gives the same gain at ~1/3 of the remainder fills, so the cost-per-fill sensitivity falls to a third: at +2 pt the cell is still +19.4k L6M vs market where the split is +1.8k. This is the one actionable, cost-robust finding: if the live +1 tick remainder fill is in doubt, F .9 / X 8 / no gate is a better-conditioned version of the same idea (the stop-class cost 2.45 pt (LIVE-CAL) changes nothing in the ranking: vs market L +22.0k L6M, +20.0k HOLD, +6.7k PRE, +8.5k X').
2. The gate matters only at the split's own parameters (F .7, X 3, 1of8): random same-rate gate and shuffled book both lose to it in L6M/HOLD/PRE (rank 1.00, 20 draws). It does not matter at F .9 / X 8.
3. Late and shallow-dip behaviours are the losers: first pullback from the high (-30k), expiry (-10k), chase (-10k), rare L2 events (ABS/ICE 1-s proxies fire too rarely; DLT_10_30 at 8 pt is the best event +17.2k L6M but PRE -9.0k, a looked-data lead only).
4. EINT1's recent-regime pattern cannot be harvested by an explicit trailing-12m switch: the switch is OFF in the recent months (see section 0). A hindsight-tercile regime would be in-sample.
5. Thick-book condition at the add gives the largest recent vs-market numbers (RC best, t 4.7 L6M) but those are the split's numbers; vs the split it is -1.6k L6M on average and PRE-negative.
## 5. Caveats
* 2026 is ~5 weeks (MDE 30-45k): read as a sign. Equal-risk c* is calibrated on WF = PRE u HOLD (EQR standard), so the c* of the cell uses HOLD data; the selection stage used c on SEL = PRE u X' only.
* Placebo draws = 20 (rank resolution 0.05); P1 for gate cells matches the add-fill share, not the SEL fill count. Resting-limit cells use the 1-tick through-fill convention (no queue model; fill at the level without slippage is optimistic). Two-add rows use the average of the two add prices as the engine entry price.
* The 11 cells that repeat L2SE F5 rows (F .5/.7 x X 3/5/8 x N 0/1 except the base) and the ADDUW near-repeat (F .5 X 5 N0) were scored as controls and excluded from selection and from the RC; they reproduce the published rows.
* Walk-forward chains fit only on trades closed before each refit (G11: 2023-10-01 then quarterly).
## 6. Files
code l2vast/ds3/code/uf/ufe_kernel.py (kernel), ufe_lib.py (engine/EQR), ufe_cells.py, ufe_regime.py, ufe_run.py (stage 0), ufe_stageA.py (SEL-only selection), ufe_stageB.py (the look), ufe_stageC.py (placebos), ufe_rc.py, ufe_gates.py, ufe_report.py; outputs l2vast/ds3/out/uf/entry_c1/ (D/SW/BK npy, pre_sel.json, stageA_table.pkl, stageB_res.pkl, stageB_table.pkl, rc.pkl, gates.pkl, placebo_*.pkl); cells l2vast/ds3/prereg/UF_ENTRY_C1_cells.csv.
