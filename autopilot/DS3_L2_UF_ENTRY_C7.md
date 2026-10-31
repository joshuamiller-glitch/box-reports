# DS3_L2_UF_ENTRY_C7 - L2-UNTIL-FOUND cycle 7, ENTRY: execution realism of the 70/30 split's add (agent UF-ENTRY, 2026-10-31)
Research only; UNTOUCHED never read; no live data read (only the sanctioned aggregate LIVE_CAL_SUMMARY.md calibration numbers). Prereg autopilot/UF_ENTRY_C7_prereg.md sha256 813a65815b7c8bc29d0376533933a3bf2517da4de518e1fbfb36aa93167afe0b (before any cycle-7 statistic). Method = a QUEUE-POSITION-FREE market-order model on the 1-s tape and the mbp-10 1-s table (bid_px, ask_px, best sizes): add event = trigger second T of the split (F .7, dip 3, 1-of-8 gate; 27,293 events); slice j (1 lot each, 2-s gaps) is sent at T + d + 2j and fills at the prevailing quote of that second (buy at the ask, sell at the bid); slippage = side x (fill - sim fill), sim fill = last trade price of the trigger second + 1 tick (the fill assumed by every earlier score). Positive = adverse. Prices come from the 1-s table itself (the path series SC is offset-adjusted vs the table: median offset 1,710 pts, so tape and table levels are not mixed). A 1-lot order is assumed filled at the touch (best size < 1 never occurs; best size is 1-2 contracts at the median touch, so the chance that others deplete it during the 1-3 s latency is NOT modelled: upper-bound stress below).

## Page 1 - the answer
1. **Modelled live add slippage per lot: +0.25 pt (95% CI +0.20 .. +0.29) beyond the simulated fill, for decision delays of 1, 2 or 3 s and 1-5 one-lot slices at 2-s gaps (the range is +0.24 .. +0.28 across all of them); in the recent windows +0.28 [+0.20, +0.37] (L6M and HOLD), PRE +0.30, X' +0.05, 2026 +0.38.** That is +0.50 pt per lot against the last trade price, of which 0.25 is the 1-tick the simulation already charged. By session (d=2, 2 slices): Asia +0.46 [+0.40,+0.52], London +0.35 [+0.28,+0.42], NY-AM +0.12, NY-PM +0.10 (thin books; median spread 0.75 vs 0.50). By book at the live add size (d=2): KB (2 lots -> 1) +0.25, PE (7 -> 2) +0.24, SM (4 -> 1) +0.20, HM (4 -> 1) +0.19, ST (10 -> 3) +0.31, WT (7 -> 2) +0.25. The tail is the risk: 27% of events cost more than 1 pt, 13% more than 2 pt (90th percentile 2.5 pt) - when the spread is wide the market add pays it (spread quartile 4: +0.79; regression: +0.29 pt per pt of spread, t 13; R2 only 0.012).
2. **Calibration against the live aggregate.** The same model applied to market-class EXITS at random under-water seconds costs +0.42 / +0.44 / +0.48 pt versus the path last price (d = 1/2/3 s); live LossExit (market, n=123, 14 with path) is +0.80 +- 0.22 (M assumes 1.0). The model is low by a factor 1.8 (1.3-2.3 with the live SE): applied as a stress multiplier the add slippage is **+0.45 pt per lot (upper +0.57)**. Cuts happen in faster markets than random under-water seconds, so the factor is a stress, not a measurement.
3. **Effect on the stack (equal risk vs market entry, N basis, d=2 s, integer live lots):** the split falls from +21.4k / +21.6k / +5.9k / +2.8k (L6M / HOLD / PRE / X', no extra cost) to **+12.5k / +13.5k / +3.5k / +2.9k** with the modelled slippage and **+11.7k / +13.1k / +0.6k / +2.3k** with the x1.8 calibration; on the LIVE-CAL basis +14.2k / +14.8k / +2.4k / +2.2k and +9.0k / +10.7k / -1.9k / +1.7k (MDE 10-17k). The state-dependent slippage is worth more than its mean: the slippage is large exactly on the bounce events that win (the price runs away while the order waits), so the stack loses the equivalent of a UNIFORM cost of about 0.55 pt (0.65 calibrated), not 0.25. Break-evens from cycle 1 (+1.0 pt PRE, +2.3 pt L6M, uniform cost) are therefore cleared on L6M and HOLD with a wide margin and on PRE by about 0.3-0.4 pt.
4. **Integer lots change the split.** Live add contracts = L - round(0.7 L): KB (2 lots) 1/1 = a 50/50 split, SM (4) 3/1, HM (4) 3/1 but HM NY-AM (2) 1/1, PE (7) 5/2, ST (10) 7/3, WT (7) 5/2; base C (90/10 at 8) rounds to 2/0 and 4/0, i.e. MARKET for KB, SM, HM, and 6/1 only for PE. Integer rounding costs the N-basis split about 3.1k L6M versus the ideal 70/30 (12.5k vs 15.6k at d=2, equal risk).
5. **Per book (stack c=1 delta vs market, N, integer lots, d=2):** ST +3.3k L6M / +4.1k HOLD (MDE 8k), WT +3.7k / +3.8k (5-6k), SM +3.0k / +3.3k (4.7k), HM +0.8k / +1.4k, PE +0.8k / +0.2k, **KB -3.0k / -2.4k / -3.1k PRE (MDE 7.6k / 6.8k / 3.8k)**: at 2 lots the split is a 50/50 and it LOSES on KB in every window; plain market (or no split) on K6 is better in these numbers. HM and PE are neutral at the live lots.
6. **Split 70/30 versus base C (90/10 at 8) once the add pays the modelled slippage** (paired stack c=1 delta, C minus S, N): ideal F +5.2k L6M / +2.5k HOLD / +1.6k PRE / +6.3k X' (d=2) and +3.6k / +1.3k / +2.5k / +6.1k (x1.8); integer lots +6.6k / +4.7k / +3.9k / +5.1k and +5.1k / +3.2k / +4.9k / +5.1k (MDE 8-17k per window: positive in every window, inside MDE in each). C is insensitive to the slippage (L6M EQR vs market +23.5k -> +22.8k at x1.8) because it adds 0.10 lot per trade instead of 0.30. Unlike the no-cost case (C - S = -0.5k L6M, -2.6k HOLD), C wins in all four windows under realistic add costs. Recommendation for Sunday: base C is not implementable at 2-4 live lots (it rounds to market for K6, U6, H6), so the live choice there is split vs plain market, and the per-book table says: drop the add on K6 (the 1/1 split loses vs market in every window), keep it on U6 (+3.0k L6M, MDE 4.7k) and H6 / P6 (about 0, no harm), and consider C only on P6 (6/1) where it is implementable.
7. Model limits (stated): market-order model with no queue/latency jump (best size at the touch is 1-2 contracts, so a 3-s latency can lose the displayed size: upper-bound stress is the x2.3 row); one tick per level walk is not needed for 1 lot; the dip cell is the split's gate cell, C's slippage uses the split's per (book, session) means (its dip is 8 pt, probably a faster market, so the calibration multiplier applies); resting-limit add: SP2 found market better at X=3 (+17.6k vs +7.3k) and I did not re-run it.

## 1. Modelled slippage per added lot
| decision delay | slices n | modelled extra slippage per added lot (pts, vs close+1 tick) [95% CI] | optimistic bound (quote 1 s earlier) | path drift during delays |
|--|--|--|--|--|
| 1 s | 1 | +0.246 [+0.202,+0.290] | +0.266 | +0.017 |
| 1 s | 2 | +0.247 [+0.204,+0.290] | +0.251 | +0.035 |
| 1 s | 3 | +0.249 [+0.206,+0.293] | +0.253 | +0.046 |
| 1 s | 5 | +0.269 [+0.218,+0.319] | +0.265 | +0.075 |
| 2 s | 1 | +0.237 [+0.193,+0.280] | +0.246 | +0.021 |
| 2 s | 2 | +0.246 [+0.201,+0.292] | +0.247 | +0.043 |
| 2 s | 3 | +0.257 [+0.209,+0.304] | +0.249 | +0.059 |
| 2 s | 5 | +0.272 [+0.220,+0.325] | +0.269 | +0.083 |
| 3 s | 1 | +0.249 [+0.198,+0.299] | +0.237 | +0.052 |
| 3 s | 2 | +0.251 [+0.200,+0.302] | +0.246 | +0.060 |
| 3 s | 3 | +0.266 [+0.216,+0.316] | +0.257 | +0.079 |
| 3 s | 5 | +0.284 [+0.232,+0.336] | +0.272 | +0.101 |

| window (d=2 s, 2 slices) | extra slippage per lot [CI] | n events |
|--|--|--|
| Y26 | +0.380 [+0.187,+0.573] | 1398 |
| L6M | +0.281 [+0.195,+0.367] | 6115 |
| HOLD | +0.281 [+0.200,+0.362] | 6749 |
| PRE | +0.300 [+0.228,+0.371] | 15217 |
| X | +0.050 [-0.003,+0.103] | 5327 |

By book at the live add size:
| book (live lots -> add contracts) | d=1 | d=2 | d=3 | d=2 x calibration 1.8 | events |
|--|--|--|--|--|--|
| KB (2 -> 1) | +0.248 [+0.171,+0.325] | +0.246 [+0.152,+0.341] | +0.235 [+0.136,+0.334] | +0.443 | 5054 |
| PE (7 -> 2) | +0.266 [+0.183,+0.349] | +0.239 [+0.153,+0.324] | +0.253 [+0.148,+0.358] | +0.429 | 5017 |
| SM (4 -> 1) | +0.259 [+0.181,+0.338] | +0.202 [+0.113,+0.290] | +0.196 [+0.080,+0.313] | +0.363 | 1584 |
| HM (4 -> 1) | +0.184 [+0.123,+0.244] | +0.186 [+0.118,+0.254] | +0.217 [+0.133,+0.301] | +0.335 | 3854 |
| ST (10 -> 3) | +0.282 [+0.204,+0.359] | +0.307 [+0.219,+0.395] | +0.310 [+0.217,+0.402] | +0.552 | 5004 |
| WT (7 -> 2) | +0.247 [+0.189,+0.305] | +0.254 [+0.185,+0.322] | +0.269 [+0.195,+0.344] | +0.456 | 6780 |

By D6 session:
| session (d=2, 2 slices) | extra slippage per lot [CI] | events | median spread | median best size |
|--|--|--|--|--|
| asia | +0.458 [+0.395,+0.520] | 6860 | 0.75 | 1 |
| close | +0.917 [+0.024,+1.811] | 53 | 0.50 | 2 |
| london | +0.348 [+0.276,+0.421] | 5654 | 0.75 | 1 |
| nyam | +0.123 [+0.042,+0.203] | 7648 | 0.50 | 2 |
| nypm | +0.104 [+0.023,+0.186] | 5468 | 0.50 | 2 |
| pre | +0.034 [-0.388,+0.456] | 1610 | 0.75 | 1 |

The book at the touch (regression and quintiles; best size and spread are the displayed quote at the trigger second):
| regressor (slippage per lot, d=2, 2 slices) | coef | t |
|--|--|--|
| const | +0.4285 | +5.1 |
| log_bestsz | -0.1048 | -2.8 |
| spread | +0.2890 | +13.3 |
| rel | -0.1048 | -1.5 |
| vol30 | -0.0299 | -9.7 |
| s_london | -0.0782 | -1.5 |
| s_nyam | -0.1029 | -2.0 |
| s_nypm | -0.1506 | -2.6 |
| s_pre | -0.3168 | -3.8 |
| s_close | +0.6662 | +1.6 |
R2 0.012; n 27293

| best-size quintile (1 = thinnest) | mean slippage per lot | | spread quartile | mean slippage per lot |
|--|--|--|--|--|
| 1 | +0.282 | | 1 | +0.044 |
| 2 | +0.097 | | 2 | +0.266 |
| 3 | +nan | | 3 | +0.231 |
| 4 | +nan | | 4 | +0.789 |

90th percentile of the event slippage per lot: 2.500; share of events above 1.0 pt: 0.271; above 2.0 pt: 0.134
## 2. Calibration vs the live aggregate (LIVE_CAL_SUMMARY)
| calibration (market-class exit at random under-water seconds, cost vs the path last price) | modelled mean (quote 0 s / 1 s earlier) | n |
|--|--|--|
| delay 1 s | +0.418 / +0.392 (SE 0.007) | 43789 |
| delay 2 s | +0.444 / +0.418 (SE 0.010) | 43789 |
| delay 3 s | +0.475 / +0.444 (SE 0.012) | 43789 |
| live LossExit (LIVE_CAL_SUMMARY, market, n=123 / 14 with path) | +0.80 +- 0.22 | 14 |

## 3. Stack under the modelled slippage (lock engine, research lots; delta vs market entry; c=1 stack $/wk (MDE) and equal-risk deltas)
N basis:
| base / lots | cost scenario | 2026 | L6M | HOLD | PRE | X' | equal-risk L6M / HOLD / PRE / X' |
|--|--|--|--|--|--|--|--|
| split 70/30@3, ideal F | sim (no extra cost) | +18.1k (41k) | +17.6k (17k) | +18.4k (15k) | +3.8k (11k) | +2.2k (8k) | +22.6 / +22.6 / +7.7 / +3.3 |
| split 70/30@3, ideal F | model d=1 s | +8.2k (43k) | +11.7k (16k) | +13.0k (15k) | +0.9k (10k) | +2.1k (8k) | +15.8 / +16.4 / +4.2 / +3.1 |
| split 70/30@3, ideal F | model d=2 s | +10.3k (42k) | +11.6k (16k) | +13.0k (15k) | +1.2k (10k) | +1.8k (8k) | +15.6 / +16.3 / +4.4 / +2.8 |
| split 70/30@3, ideal F | model d=3 s | +19.2k (32k) | +12.5k (15k) | +13.8k (14k) | +1.7k (10k) | +1.0k (9k) | +16.8 / +17.3 / +5.1 / +1.9 |
| split 70/30@3, ideal F | model d=2 s x1.8 (live-exit calibration) | +22.8k (46k) | +12.7k (17k) | +13.7k (15k) | -0.1k (11k) | +1.3k (9k) | +14.3 / +15.0 / +1.1 / +1.7 |
| split 70/30@3, ideal F | model d=2 s x2.3 (calibration upper) | +22.1k (47k) | +11.4k (17k) | +12.9k (16k) | +0.1k (11k) | +1.4k (9k) | +13.7 / +14.8 / +2.0 / +1.9 |
| split 70/30@3, integer live lots | sim (no extra cost) | +18.1k (41k) | +16.3k (18k) | +17.3k (17k) | +2.0k (11k) | +1.6k (8k) | +21.4 / +21.6 / +5.9 / +2.8 |
| split 70/30@3, integer live lots | model d=1 s | +10.2k (43k) | +10.2k (17k) | +11.7k (16k) | +0.3k (11k) | +2.1k (8k) | +14.8 / +15.6 / +4.0 / +3.2 |
| split 70/30@3, integer live lots | model d=2 s | +10.3k (42k) | +8.6k (17k) | +10.3k (16k) | +0.3k (11k) | +1.9k (8k) | +12.5 / +13.5 / +3.5 / +2.9 |
| split 70/30@3, integer live lots | model d=3 s | +17.9k (34k) | +9.1k (17k) | +10.8k (16k) | +1.1k (11k) | +1.0k (9k) | +13.1 / +14.2 / +4.5 / +2.0 |
| split 70/30@3, integer live lots | model d=2 s x1.8 (live-exit calibration) | +20.1k (48k) | +9.7k (18k) | +11.5k (17k) | -1.0k (11k) | +1.8k (9k) | +11.7 / +13.1 / +0.6 / +2.3 |
| split 70/30@3, integer live lots | model d=2 s x2.3 (calibration upper) | +19.3k (49k) | +8.4k (19k) | +10.4k (17k) | -0.6k (11k) | +2.0k (9k) | +10.7 / +12.4 / +1.3 / +2.6 |
| C 90/10@8, ideal F | sim (no extra cost) | +27.7k (26k) | +17.1k (13k) | +15.8k (13k) | +3.3k (10k) | +8.4k (9k) | +24.4 / +21.7 / +9.0 / +10.7 |
| C 90/10@8, ideal F | model d=1 s | +27.8k (27k) | +16.8k (13k) | +15.5k (13k) | +2.8k (10k) | +8.1k (9k) | +23.6 / +21.0 / +8.1 / +10.2 |
| C 90/10@8, ideal F | model d=2 s | +27.8k (27k) | +16.8k (13k) | +15.5k (13k) | +2.8k (10k) | +8.1k (9k) | +23.5 / +21.0 / +8.0 / +10.2 |
| C 90/10@8, ideal F | model d=3 s | +27.7k (27k) | +16.8k (13k) | +15.4k (13k) | +2.8k (10k) | +8.1k (9k) | +23.5 / +20.9 / +8.0 / +10.2 |
| C 90/10@8, ideal F | model d=2 s x1.8 (live-exit calibration) | +27.3k (26k) | +16.3k (13k) | +15.0k (13k) | +2.4k (10k) | +7.4k (9k) | +22.8 / +20.3 / +7.5 / +9.4 |
| C 90/10@8, ideal F | model d=2 s x2.3 (calibration upper) | +27.0k (26k) | +16.0k (13k) | +14.7k (13k) | +2.1k (10k) | +7.2k (9k) | +22.4 / +19.9 / +7.1 / +9.1 |
| C 90/10@8, integer live lots | sim (no extra cost) | +27.8k (46k) | +15.4k (16k) | +15.2k (15k) | +4.5k (10k) | +7.2k (8k) | +23.7 / +22.1 / +11.3 / +9.8 |
| C 90/10@8, integer live lots | model d=1 s | +27.8k (46k) | +15.2k (16k) | +15.0k (15k) | +4.2k (10k) | +7.0k (8k) | +23.3 / +21.7 / +10.8 / +9.5 |
| C 90/10@8, integer live lots | model d=2 s | +27.8k (46k) | +15.2k (16k) | +15.0k (15k) | +4.2k (10k) | +7.0k (8k) | +23.3 / +21.7 / +10.8 / +9.4 |
| C 90/10@8, integer live lots | model d=3 s | +27.8k (46k) | +15.2k (16k) | +15.0k (15k) | +4.2k (10k) | +7.0k (8k) | +23.3 / +21.7 / +10.8 / +9.4 |
| C 90/10@8, integer live lots | model d=2 s x1.8 (live-exit calibration) | +27.4k (46k) | +14.9k (16k) | +14.7k (15k) | +3.9k (10k) | +6.9k (8k) | +22.9 / +21.3 / +10.4 / +9.3 |
| C 90/10@8, integer live lots | model d=2 s x2.3 (calibration upper) | +27.3k (46k) | +14.6k (16k) | +14.5k (15k) | +3.5k (10k) | +6.8k (8k) | +22.4 / +20.9 / +9.8 / +9.1 |

LIVE-CAL basis:
| base / lots | cost scenario | 2026 | L6M | HOLD | PRE | X' | equal-risk L6M / HOLD / PRE / X' |
|--|--|--|--|--|--|--|--|
| split 70/30@3, ideal F | sim (no extra cost) | +14.6k (40k) | +15.1k (16k) | +16.0k (15k) | +3.8k (11k) | +2.5k (8k) | +18.7 / +18.9 / +6.5 / +3.0 |
| split 70/30@3, ideal F | model d=1 s | +16.8k (39k) | +13.7k (16k) | +14.6k (15k) | +1.5k (10k) | +2.2k (8k) | +16.8 / +17.1 / +3.8 / +2.7 |
| split 70/30@3, ideal F | model d=2 s | +12.6k (40k) | +12.7k (16k) | +13.7k (15k) | +1.4k (10k) | +2.2k (8k) | +16.0 / +16.4 / +3.9 / +2.7 |
| split 70/30@3, ideal F | model d=3 s | +12.6k (37k) | +12.4k (15k) | +13.4k (14k) | +1.7k (10k) | +1.5k (9k) | +15.5 / +16.0 / +4.1 / +2.0 |
| split 70/30@3, ideal F | model d=2 s x1.8 (live-exit calibration) | +7.8k (43k) | +10.3k (17k) | +11.4k (15k) | -1.2k (10k) | +1.6k (9k) | +11.1 / +12.1 / -0.6 / +1.7 |
| split 70/30@3, ideal F | model d=2 s x2.3 (calibration upper) | +7.4k (44k) | +8.8k (16k) | +10.4k (15k) | -0.9k (10k) | +1.6k (9k) | +9.0 / +10.6 / -0.7 / +1.6 |
| split 70/30@3, integer live lots | sim (no extra cost) | +15.1k (41k) | +13.9k (17k) | +14.9k (16k) | +3.1k (11k) | +2.2k (8k) | +17.4 / +17.8 / +5.8 / +2.7 |
| split 70/30@3, integer live lots | model d=1 s | +17.3k (40k) | +12.4k (17k) | +13.5k (16k) | +0.9k (11k) | +1.7k (8k) | +15.7 / +16.1 / +3.4 / +2.2 |
| split 70/30@3, integer live lots | model d=2 s | +12.5k (41k) | +11.1k (17k) | +12.3k (16k) | +0.1k (11k) | +1.7k (8k) | +14.2 / +14.8 / +2.4 / +2.2 |
| split 70/30@3, integer live lots | model d=3 s | +11.2k (38k) | +10.9k (16k) | +12.1k (15k) | -0.8k (11k) | +1.1k (9k) | +13.8 / +14.5 / +1.4 / +1.5 |
| split 70/30@3, integer live lots | model d=2 s x1.8 (live-exit calibration) | +7.2k (42k) | +8.3k (17k) | +10.1k (16k) | -2.4k (11k) | +1.6k (8k) | +9.0 / +10.7 / -1.9 / +1.7 |
| split 70/30@3, integer live lots | model d=2 s x2.3 (calibration upper) | +4.9k (43k) | +6.6k (17k) | +8.4k (16k) | -2.2k (11k) | +1.4k (9k) | +6.3 / +8.2 / -2.4 / +1.3 |
| C 90/10@8, ideal F | sim (no extra cost) | +18.8k (29k) | +17.1k (13k) | +16.1k (13k) | +3.1k (10k) | +7.5k (9k) | +22.0 / +20.0 / +6.7 / +8.5 |
| C 90/10@8, ideal F | model d=1 s | +18.2k (29k) | +16.7k (13k) | +15.7k (13k) | +2.1k (10k) | +7.2k (9k) | +21.3 / +19.4 / +5.5 / +8.2 |
| C 90/10@8, ideal F | model d=2 s | +18.2k (29k) | +16.7k (13k) | +15.7k (13k) | +2.1k (10k) | +7.2k (9k) | +21.3 / +19.4 / +5.5 / +8.2 |
| C 90/10@8, ideal F | model d=3 s | +18.2k (29k) | +16.6k (13k) | +15.7k (13k) | +2.1k (10k) | +7.2k (9k) | +21.3 / +19.3 / +5.5 / +8.2 |
| C 90/10@8, ideal F | model d=2 s x1.8 (live-exit calibration) | +17.8k (29k) | +16.4k (13k) | +15.4k (13k) | +1.3k (10k) | +6.4k (9k) | +20.3 / +18.5 / +4.2 / +7.2 |
| C 90/10@8, ideal F | model d=2 s x2.3 (calibration upper) | +18.0k (28k) | +16.2k (13k) | +15.2k (13k) | +0.9k (10k) | +6.2k (9k) | +20.1 / +18.3 / +3.6 / +7.0 |
| C 90/10@8, integer live lots | sim (no extra cost) | +14.1k (34k) | +14.7k (16k) | +14.2k (15k) | +5.5k (10k) | +7.7k (9k) | +20.7 / +19.1 / +10.3 / +9.0 |
| C 90/10@8, integer live lots | model d=1 s | +13.7k (34k) | +14.0k (16k) | +13.6k (15k) | +5.1k (10k) | +7.4k (9k) | +19.9 / +18.3 / +9.8 / +8.8 |
| C 90/10@8, integer live lots | model d=2 s | +13.7k (34k) | +14.0k (16k) | +13.6k (15k) | +5.1k (10k) | +7.4k (9k) | +19.9 / +18.3 / +9.8 / +8.8 |
| C 90/10@8, integer live lots | model d=3 s | +13.7k (34k) | +14.0k (16k) | +13.6k (15k) | +5.1k (10k) | +7.4k (9k) | +19.9 / +18.3 / +9.8 / +8.8 |
| C 90/10@8, integer live lots | model d=2 s x1.8 (live-exit calibration) | +13.2k (34k) | +13.7k (16k) | +13.3k (15k) | +4.4k (9k) | +7.2k (9k) | +18.9 / +17.5 / +8.5 / +8.4 |
| C 90/10@8, integer live lots | model d=2 s x2.3 (calibration upper) | +13.2k (34k) | +13.6k (16k) | +13.2k (15k) | +4.0k (9k) | +7.1k (9k) | +18.8 / +17.3 / +8.1 / +8.2 |

### C minus split (paired stack c=1 delta, $/wk, MDE)
| basis | lots | cost scenario | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|--|
| N | ideal | sim (no extra cost) | +9.6k (26k) | -0.5k (13k) | -2.6k (12k) | -0.5k (9k) | +6.2k (9k) |
| N | ideal | model d=2 s | +17.5k (28k) | +5.2k (12k) | +2.5k (11k) | +1.6k (8k) | +6.3k (9k) |
| N | ideal | model d=2 s x1.8 (live-exit calibration) | +4.5k (31k) | +3.6k (12k) | +1.3k (11k) | +2.5k (10k) | +6.1k (10k) |
| N | int | sim (no extra cost) | +9.7k (51k) | -1.0k (18k) | -2.1k (16k) | +2.5k (10k) | +5.6k (9k) |
| N | int | model d=2 s | +17.5k (57k) | +6.6k (18k) | +4.7k (17k) | +3.9k (9k) | +5.1k (9k) |
| N | int | model d=2 s x1.8 (live-exit calibration) | +7.3k (50k) | +5.1k (16k) | +3.2k (15k) | +4.9k (10k) | +5.1k (9k) |
| L | ideal | sim (no extra cost) | +4.2k (46k) | +2.0k (13k) | +0.2k (11k) | -0.7k (9k) | +5.0k (9k) |
| L | ideal | model d=2 s | +5.6k (46k) | +3.9k (13k) | +1.9k (12k) | +0.7k (9k) | +5.0k (9k) |
| L | ideal | model d=2 s x1.8 (live-exit calibration) | +10.0k (47k) | +6.1k (14k) | +4.0k (13k) | +2.6k (9k) | +4.8k (9k) |
| L | int | sim (no extra cost) | -0.9k (56k) | +0.7k (16k) | -0.7k (15k) | +2.4k (10k) | +5.4k (9k) |
| L | int | model d=2 s | +1.2k (56k) | +2.9k (16k) | +1.3k (15k) | +5.0k (10k) | +5.7k (9k) |
| L | int | model d=2 s x1.8 (live-exit calibration) | +6.0k (61k) | +5.4k (17k) | +3.2k (16k) | +6.7k (11k) | +5.6k (9k) |

### Per book (split, integer live lots, N, c=1 delta vs market $/wk)
| book (live lots -> add) | cost scenario | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|
| ST | model d=2 s | +7.2k (23.0k) | +3.3k (8.5k) | +4.1k (8.3k) | -0.1k (6.1k) | +0.7k (4.6k) |
| HM | model d=2 s | +3.8k (24.2k) | +0.8k (7.4k) | +1.4k (6.9k) | +0.2k (4.8k) | -0.1k (3.5k) |
| WT | model d=2 s | +2.3k (10.7k) | +3.7k (5.7k) | +3.8k (5.3k) | +1.7k (3.9k) | -1.8k (2.3k) |
| KB | model d=2 s | -1.5k (18.0k) | -3.0k (7.6k) | -2.4k (6.8k) | -3.1k (3.8k) | +1.3k (3.8k) |
| SM | model d=2 s | +1.8k (7.3k) | +3.0k (4.7k) | +3.3k (4.6k) | +0.2k (1.7k) | -0.9k (1.3k) |
| PE | model d=2 s | -3.2k (23.5k) | +0.8k (6.9k) | +0.2k (6.3k) | +1.5k (3.3k) | +2.7k (2.9k) |
| ST | model d=2 s x1.8 (live-exit calibration) | +16.6k (37.5k) | +5.2k (10.8k) | +5.6k (10.1k) | -1.5k (6.6k) | +1.0k (4.7k) |
| HM | model d=2 s x1.8 (live-exit calibration) | +3.6k (24.1k) | +0.9k (7.7k) | +1.5k (7.1k) | +0.4k (5.0k) | -0.1k (3.5k) |
| WT | model d=2 s x1.8 (live-exit calibration) | +4.1k (16.4k) | +4.0k (6.2k) | +3.9k (5.7k) | +1.3k (3.6k) | -2.1k (2.6k) |
| KB | model d=2 s x1.8 (live-exit calibration) | -1.9k (18.1k) | -3.4k (7.6k) | -2.8k (6.8k) | -2.9k (3.8k) | +1.5k (4.0k) |
| SM | model d=2 s x1.8 (live-exit calibration) | +1.7k (7.4k) | +2.9k (4.9k) | +3.2k (4.7k) | +0.2k (1.7k) | -0.9k (1.3k) |
| PE | model d=2 s x1.8 (live-exit calibration) | -4.1k (23.0k) | +0.2k (6.4k) | -0.0k (5.6k) | +1.6k (3.3k) | +2.5k (2.9k) |

## 4. Not done / next
Q5 (cross-day causal-tag size modifier) not started (time). A queue-position model needs order-level data (not on disk): the displayed best size at the touch is 1-2 contracts in the median event, so live partial fills / price improvement at 1-lot clips are the open risk; the 11/11 live target fills are limit orders and say nothing about this market add. Files: code l2vast/ds3/code/uf/ufe7_quote.py, ufe7_slip.py, ufe7_tables.py, ufe7_stack.py, ufe7_more.py, ufe7_report.py; outputs l2vast/ds3/out/uf/entry_c7/.
