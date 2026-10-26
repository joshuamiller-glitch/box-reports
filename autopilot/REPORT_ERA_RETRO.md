# REPORT ERA-RETRO - retroactive pass under GATE AMENDMENT 2 (B2356 worker)

**Result: 79 B2356-worker families re-selected on CLEAN only (2013-22 ignored); 104 cells in 48 families read on H1/H2 once; ZERO pass all gates (FOUND 0, FOUND-PENDING 0 from this pass). Four new LEADs: Q5 / Q10 / Q9 (cross-sectional momentum / low-vol-reversal books) and W4 (Monday equity-index drift, fails more gates). The ES dip-buy lead (C11-DIP) becomes FOUND-PENDING-REPLICATED (REPORT_C11_REP2.md).**

Protocol: pre-registered in PREREG_AUTOPILOT.md ("ERA RETRO PASS"): eligible = weekly Sharpe > 0 in BOTH halves of clean and >= 40 pair-window trades; top 3 by clean weekly Sharpe per family (per kind/timeframe where the original script did); H1/H2 read once; scale = pair clean vol using the sleeve's clean vol; own random-entry null (203 draws), bootstrap, plateau (+-25%), 2x slippage, wd corr, circular-shift null for hedge claims; baseline B.Cfg(wk_floor=8, wk_loss_pb=None). Code: SEL=clean mode of ap_b2356_core/ap_*_run.py; outputs outputs/autopilot/b2356c/ (ERA_summary.csv per family, ERA_detail.csv per cell, *_era.pkl cost decompositions). Books saved to the library: family B2356ERA (104 books, volmatch size).

Families with NO clean-eligible cell (nothing consistent in both clean halves with >= 40 trades): 31 of 79: B3, Q6, R2, R3, R4, R5, R6, R7, R8, S2, S4, S6, S7, S8, S9, T2, T3, T5, V2, V7, W2, W3, Y3, Y4, Y7, Y8, Y9, Z4, Z5, Z6, Z8.

ERA FLAG distribution over the 104 cells (2013-22 Sharpe at zero cost / fixed cost / price-scaled cost; scaled = costs x median raw-price ratio 2013-22 : 2023-26 of the traded markets, approximate): {'positive pre-2023': 58, 'negative pre-2023': 30, 'gross-positive, cost-negative pre-2023': 16}. Flag rule: net > +0.1 = positive pre-2023; gross > +0.1 but net <= +0.1 = gross-positive, cost-negative; else negative. Cost decomposition caveat: B3 and the Z1/U2/dip engines are not covered by the cost factors.

## Cells with uplift >= +0.10 on clean, H1 and H2 at 20% share (the only near-misses)
| family | cell | pair-win Sharpe | null rank | uplift@20% clean/H1/H2 | boot lo | wd corr | worst wk chg | plateau | shift null | ERA flag (2013-22 gross / net / price-scaled Sharpe) | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Q10 | Q10_mom_20_XS_0_as_M_h19_COM | 1.25 | 1.00 | 0.21/0.18/0.26 | 0.06 | -0.02 | 19% | 0.50 | see report | gross-positive, cost-negative pre-2023: 0.12 / 0.03 / 0.05 | G3 at some shares (10%: clean uplift < 0.10 / worst week > share at larger shares); plateau (0.50); hedge claim: shift null applies |
| Q5 | Q5_mom_25_XS_4_as_M_h19_MACRO12 | 1.63 | 1.00 | 0.30/0.44/0.12 | 0.11 | -0.41 | 15% | 0.50 | see report | positive pre-2023: 0.54 / 0.46 / 0.47 | G3 at some shares (10%: clean uplift < 0.10 / worst week > share at larger shares); plateau (0.50); hedge claim: shift null applies |
| Q9 | Q9_lowvol_20_XS_0_rev_M_h19_ALL26 | 1.38 | 1.00 | 0.19/0.12/0.46 | 0.07 | -0.27 | 20% | n/a | see report | positive pre-2023: 0.37 / 0.25 / 0.26 | G3 at some shares (10%: clean uplift < 0.10 / worst week > share at larger shares); plateau (no neighbours defined); hedge claim: shift null applies |
| W4 | W4_0_EQ_h1_EQ | 1.59 | 1.00 | 0.22/0.47/0.25 | 0.08 | +0.42 | 43% | n/a | see report | positive pre-2023: 0.56 / 0.41 / 0.48 | G3 at some shares (10%: clean uplift < 0.10 / worst week > share at larger shares); plateau (no neighbours defined); wd corr +0.42 > 0.30 |

Reading: Q5 (25-day cross-sectional momentum, long top-4 / short bottom-4 of 12 macro markets, monthly rebalance, 19-day hold) passes G3 at 20/30/50% (not at 10%: the clean-selected uplift scales linearly), own null (rank 1.00), bootstrap (lo +0.11, > 0 at all shares), 2x slippage, wd corr (-0.41); fails the plateau (2 of 4 neighbours keep 75% of the uplift: the 19-day lookback and breadth 3 do not) and, being a hedge claim, the circular-shift null (rank 0.63). It is the same family as R9 / Q3 (63-252 day) / Q10: cross-sectional momentum at monthly rebalance shows up in several adjacent specifications, which is the argument for a pre-registered ENSEMBLE book of the whole grid (planned) rather than for any single cell. Q10 is the commodity-only version; Q9 buys HIGH-volatility markets (reversal of the low-vol rank) - plausible as the commodity/vol factor loading of the momentum book (not tested for overlap). W4 is a calendar drift (Monday, equity indices, signed on 2013-22 means) with wd corr +0.42 and worst week 43% worse at 20%: fails G6.

## Families that were screened OUT on the 2013-22 dev screen and have now been read (13)
| family | best clean-selected cell | pair-win Sharpe | uplift@20% clean/H1/H2 | ERA flag |
|---|---|---|---|---|
| R1 | R1_60_3_h3_SCR | 1.10 | 0.25/0.33/-0.02 | negative pre-2023 |
| T1 | T1_0.25_1_fade | 0.83 | 0.12/-0.11/0.20 | positive pre-2023 |
| T4 | T4_1.0_follow | 0.59 | 0.10/-0.61/0.23 | positive pre-2023 |
| T6 | T6__h1_FX | 1.26 | 0.17/-0.03/0.38 | positive pre-2023 |
| V1 | V1_NQ_1.5_h1_ES | 0.49 | 0.08/0.10/-0.13 | gross-positive, cost-negative pre-2023 |
| V9 | V9_2.0_0.5_h5_ALL26 | 0.55 | -0.00/0.44/-0.00 | gross-positive, cost-negative pre-2023 |
| W1 | W1_660_ATR | 0.61 | 0.08/0.12/-0.29 | gross-positive, cost-negative pre-2023 |
| X2 | X2_1_1.5_0.35_h1_EQ4 | 0.64 | 0.07/-0.04/0.14 | negative pre-2023 |
| Y10 | Y10_3.0_follow_h8_M6 | 0.33 | 0.04/-0.16/-0.17 | gross-positive, cost-negative pre-2023 |
| Y1 | Y1_4_fade_h3_ALL26 | 0.36 | 0.12/-0.21/-0.09 | gross-positive, cost-negative pre-2023 |
| Z10 | Z10_1.3_5_h3_SCR | 0.19 | 0.01/-0.10/0.07 | negative pre-2023 |
| Z2 | Z2_IDw_h3_ALL26 | 0.20 | 0.12/0.14/-0.09 | positive pre-2023 |
| Z9 | Z9_narrow_k1_M6 | 0.42 | 0.10/-0.36/0.10 | positive pre-2023 |

All 13 remain NO under the full gates. Largest: T6 (weekend gap fade in FX, +0.17/-0.03/+0.38), R1 (kurtosis reversal, +0.25/+0.33/-0.02), Z2 (weekly-compression breakout), none consistent across spans.

## What the clean-only selection changed for families that WERE read before
The weekend-gap family (W6/Z3/T1/V3/V4/V10) is selected with the same signs (H1 negative): unchanged LEAD-weak. X1/Y6/B2-D (daily-bar compression breakouts) re-select but are withdrawn on path-resolution grounds (REPORT_Z1.md), not era. B2-D, X1: unchanged NO.

DONE ERA-RETRO
