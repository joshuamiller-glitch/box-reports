## RATES-MOM STRESS (S4a, 2026-11-06): ZF / ZT daily momentum, stressed like the CL cell - follow-up on best-of-F cells
Prereg l2vast/ds3/prereg/RATES_MOM_STRESS_prereg.md sha256 8ae2c02534d2aeb72d3dd76cb0d02b50ca45f32fd354e27207691822b154fdac (filed before any statistic). Code l2vast/ds3/code/t2s4a/rates_stress.py, rates_stress2.py; results /mnt/l2/l2vast/ds3_daily6/rates_stress_*.pkl, rates_fine.pkl. The engine reproduces the earlier cells (ZF L126 vol 18,713; ZF L252 1-lot 13,402; ZT L252 vol 96,637). Products: ZF, ZT (daily6 builds, anchor 14:55 ET) and ZN, ZB (FIND_DAILY builds, 15:55 ET) as the rates group.
**Plain sentence: the ZF / ZT momentum result is not on a plateau and does not survive the stress: the 13-year profit sits on a narrow band of lookbacks (189-231 days; L = 126, 168 and 252 next to it are flat or weak, and only 2-3 of 8 lookbacks pass the pre-stated Calmar >= 0.10 test, 5 were required), 98-99% of the net of the L189 books comes from their three best trades (the other 74-77 trades sum to about +$1k to +$3k, win rate 29-31%), 76-78% from three years (2022, 2020, 2024 / 2026), the walk-forward OOS drops to +$47k (ZF) and +$34k (ZT) without 2022, and the four rates books are one bet (effective 1.6-1.7 independent bets, P&L correlations 0.4-0.9) whose only significant version (L189, common-flip null p 0.015 before the correction for choosing the best of 8 lookbacks, about 0.12 after) is the post-hoc best lookback. At the lots the vol target implies (5-6 contracts, the cap) the books are worth $0-300 a week against the live stack's $28k, so there is no WATCH spec and nothing for ZL-2 to register.**
### S1 plateau surface (128 cells per product; trailing stop = m x monthly sigma from the best close, flat until the signal flips)
Pre-stated plateau rule on the reference sizing ($1,200 vol lots, no stop): (a) >= 5 of 8 lookbacks with 13-year net > 0 and Calmar >= .10; (b) >= 4 of 8 the same ex-2022; (c) neighbour median Calmar >= 50% of the best cell. Result: ZF a = 2, b = 1, best L189 Calmar 0.34, neighbour median 0.16 (< 0.17): FAIL; ZT a = 3, b = 2, best L189 0.38, neighbours 0.16 (< 0.19): FAIL; ZN a = 2, b = 2, (c) 0.13 vs 0.13 passes but (a) and (b) fail; ZB a = 1, b = 1: FAIL. **No product survives at a plateau.**
**ZF** - Calmar, vol lots $1,200, by trailing stop (columns: none, 1.0, 1.5, 2.0 x monthly sigma):
| L | 0.0 | 1.0 | 1.5 | 2.0 |
|--|--|--|--|--|
| 21 | -0.06 | -0.05 | -0.06 | -0.06 |
| 42 | 0.11 | 0.07 | 0.11 | 0.11 |
| 63 | -0.01 | -0.05 | -0.01 | -0.00 |
| 84 | 0.01 | -0.01 | 0.02 | 0.01 |
| 126 | 0.01 | -0.03 | 0.05 | 0.04 |
| 189 | 0.34 | 0.15 | 0.18 | 0.25 |
| 252 | 0.05 | -0.03 | -0.02 | -0.01 |
| 315 | 0.09 | -0.04 | 0.01 | 0.09 |

**ZF** - Calmar, no stop, by sizing (600 / 1,200 / 2,400 daily-sigma target, 1 lot), full sample:
| L | 600 | 1200 | 2400 | 1lot |
|--|--|--|--|--|
| 21 | -0.05 | -0.06 | -0.06 | -0.06 |
| 42 | 0.11 | 0.11 | 0.10 | 0.09 |
| 63 | -0.01 | -0.01 | -0.02 | -0.02 |
| 84 | 0.01 | 0.01 | 0.00 | 0.00 |
| 126 | 0.02 | 0.01 | 0.02 | 0.02 |
| 189 | 0.31 | 0.34 | 0.44 | 0.44 |
| 252 | 0.02 | 0.05 | 0.08 | 0.08 |
| 315 | 0.08 | 0.09 | 0.14 | 0.14 |

**ZF** - Calmar EX-2022, no stop, by sizing:
| L | 600 | 1200 | 2400 | 1lot |
|--|--|--|--|--|
| 21 | -0.06 | -0.06 | -0.06 | -0.06 |
| 42 | 0.08 | 0.08 | 0.06 | 0.06 |
| 63 | -0.02 | -0.03 | -0.04 | -0.05 |
| 84 | -0.02 | -0.02 | -0.04 | -0.04 |
| 126 | -0.01 | -0.02 | -0.03 | -0.03 |
| 189 | 0.24 | 0.25 | 0.28 | 0.29 |
| 252 | -0.03 | -0.01 | 0.00 | 0.01 |
| 315 | 0.03 | 0.03 | 0.05 | 0.05 |
**ZT** - Calmar, vol lots $1,200, by trailing stop (columns: none, 1.0, 1.5, 2.0 x monthly sigma):
| L | 0.0 | 1.0 | 1.5 | 2.0 |
|--|--|--|--|--|
| 21 | -0.06 | -0.06 | -0.06 | -0.06 |
| 42 | 0.01 | -0.01 | 0.01 | 0.01 |
| 63 | 0.03 | 0.02 | 0.02 | 0.02 |
| 84 | 0.03 | 0.02 | 0.04 | 0.03 |
| 126 | -0.01 | -0.05 | -0.03 | -0.00 |
| 189 | 0.38 | 0.08 | 0.19 | 0.19 |
| 252 | 0.14 | -0.05 | 0.03 | 0.06 |
| 315 | 0.30 | 0.11 | 0.23 | 0.24 |

**ZT** - Calmar, no stop, by sizing (600 / 1,200 / 2,400 daily-sigma target, 1 lot), full sample:
| L | 600 | 1200 | 2400 | 1lot |
|--|--|--|--|--|
| 21 | -0.07 | -0.06 | -0.06 | -0.06 |
| 42 | -0.02 | 0.01 | 0.03 | 0.03 |
| 63 | 0.03 | 0.03 | 0.01 | 0.00 |
| 84 | 0.00 | 0.03 | 0.04 | 0.05 |
| 126 | -0.01 | -0.01 | -0.00 | -0.00 |
| 189 | 0.34 | 0.38 | 0.40 | 0.40 |
| 252 | 0.13 | 0.14 | 0.17 | 0.18 |
| 315 | 0.28 | 0.30 | 0.32 | 0.33 |

**ZT** - Calmar EX-2022, no stop, by sizing:
| L | 600 | 1200 | 2400 | 1lot |
|--|--|--|--|--|
| 21 | -0.07 | -0.07 | -0.07 | -0.07 |
| 42 | -0.05 | -0.03 | -0.03 | -0.02 |
| 63 | -0.01 | -0.02 | -0.03 | -0.04 |
| 84 | -0.05 | -0.04 | -0.04 | -0.03 |
| 126 | -0.04 | -0.04 | -0.04 | -0.04 |
| 189 | 0.25 | 0.25 | 0.25 | 0.26 |
| 252 | 0.08 | 0.07 | 0.08 | 0.09 |
| 315 | 0.19 | 0.19 | 0.19 | 0.20 |
The trailing stop never helps the L189 cells (ZF Calmar 0.34 -> 0.15 / 0.18 / 0.25, ZT 0.38 -> 0.08 / 0.19 / 0.19), and the Calmar is nearly independent of the sizing target (600 / 1,200 / 2,400 / 1 lot), so the vol scaling is not what drives the result.
**Exploratory finer lookback grid (not part of the pre-stated rule, labelled post-hoc):**
| L | ZF | ZT | ZN | ZB | PORT4 net $k | PORT4 Calmar | PORT4 ex-2022 $k | PORT4 Calmar ex-2022 |
|--|--|--|--|--|--|--|--|--|
| 42 | 0.11 | 0.01 | 0.13 | 0.11 | 299 | 0.12 | 216 | 0.09 |
| 63 | -0.01 | 0.03 | 0.00 | 0.02 | 51 | 0.01 | -35 | -0.01 |
| 84 | 0.01 | 0.03 | 0.00 | 0.02 | 60 | 0.01 | -73 | -0.02 |
| 105 | 0.06 | 0.03 | 0.04 | 0.04 | 194 | 0.04 | 25 | 0.01 |
| 126 | 0.01 | -0.01 | -0.01 | 0.01 | 9 | 0.00 | -160 | -0.03 |
| 147 | 0.06 | 0.05 | 0.06 | 0.07 | 260 | 0.07 | 97 | 0.02 |
| 168 | 0.05 | 0.03 | 0.06 | 0.03 | 181 | 0.05 | 23 | 0.01 |
| 189 | 0.34 | 0.38 | 0.25 | -0.01 | 394 | 0.24 | 253 | 0.17 |
| 210 | 0.22 | 0.37 | 0.15 | -0.01 | 354 | 0.17 | 212 | 0.11 |
| 231 | 0.20 | 0.24 | 0.09 | -0.03 | 250 | 0.10 | 90 | 0.04 |
| 252 | 0.05 | 0.14 | -0.04 | -0.06 | -39 | -0.01 | -201 | -0.05 |
| 273 | 0.03 | 0.09 | -0.04 | -0.05 | -8 | -0.00 | -180 | -0.04 |
| 294 | 0.08 | 0.09 | -0.01 | -0.05 | 81 | 0.02 | -92 | -0.02 |
| 315 | 0.09 | 0.30 | 0.01 | -0.05 | 114 | 0.04 | -58 | -0.02 |
| 378 | 0.07 | 0.17 | 0.02 | 0.00 | 175 | 0.05 | 2 | 0.00 |
The good zone is L = 189-231 for ZF and ZT (ZN positive to 210, ZB never): Calmar 0.2-0.4, flanked by 0.03-0.06 at 168 and 0.05-0.14 at 252; as ONE bet (PORT4 = ZF + ZT + ZN + ZB) Calmar 0.24 / 0.17 / 0.10 at 189 / 210 / 231 and 0.17 / 0.11 / 0.04 ex-2022. It is a band about three lookbacks wide out of fifteen tried, not a plateau.
### S2 per year and regime (reference books, $1,200 vol lots, no stop; $k)
| book | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 | 25 | 26 | 13y net | maxDD |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ZF L189 | 3.9 | -11.1 | 11.0 | 4.9 | -19.6 | 13.6 | 17.8 | 35.2 | 9.8 | 46.3 | -1.7 | 27.9 | -12.2 | 15.1 | 140.9 | 29.2 |
| ZF L252 | 0.0 | -11.4 | 8.6 | -15.7 | -14.3 | 2.7 | 10.1 | 35.2 | -7.7 | 46.3 | -0.3 | -2.4 | -23.5 | 10.8 | 38.2 | 57.9 |
| ZT L189 | -1.2 | 6.8 | 6.7 | -5.5 | -0.5 | 5.9 | 5.7 | 26.4 | 1.5 | 52.5 | 2.5 | 20.0 | -9.8 | 24.8 | 135.8 | 25.5 |
| ZT L252 | 0.0 | 6.8 | 5.9 | -1.3 | -1.3 | 4.2 | 1.2 | 27.4 | -0.3 | 52.5 | 2.5 | -7.6 | -18.1 | 24.8 | 96.6 | 49.8 |
| ZN L189 | 3.0 | 4.6 | 0.1 | 4.4 | -24.6 | 23.8 | 26.7 | 21.2 | 12.7 | 33.9 | -7.9 | 22.6 | -3.4 | 15.1 | 132.1 | 36.8 |
Regimes (net $k) 2013-16 / 2017-19 / 2020-22 / 2023-26: ZF L189 8.7 / 11.8 / 91.3 / 29.1; ZF L252 -18.5 / -1.6 / 73.8 / -15.5; ZT L189 6.8 / 11.1 / 80.5 / 37.5; ZT L252 11.3 / 4.1 / 79.6 / 1.6; ZN L189 12.0 / 25.9 / 67.7 / 26.4. The 2013 taper tantrum (May-Sep 2013) is a non-event for L189 / L252 (no position yet: the 189-252 day sign was still flat) and a -$6.8k loss for ZF L126; 2020 pays +$21k to +$35k per book (the COVID rate collapse) and 2022 +$34k to +$53k (the sell-off): 2020-22 is 65-87% of every book's 13-year net.
Ex-2022 and ex-2022-23 (13-year net, Calmar): ZF L189 +$94.6k (0.25) / +$96.3k; ZT L189 +$83.4k (0.25) / +$80.9k; ZN L189 +$98.2k (0.20) / +$106.1k; but ZF L252 -$8.1k, ZF L126 -$27.6k, ZT L252 +$44.2k (0.07), ZT L126 -$65.1k. The walk-forward OOS (annual refit among the 8 TSMOM cells): ZF +$93.7k all years, +$47.4k ex-2022 (Calmar 0.27), +$49.2k ex-2022-23; ZT +$86.3k, +$33.8k ex-2022 (Calmar 0.19), +$31.5k ex-2022-23; the refit picked L126 (ZF, 2018-22) and L252 (ZT) - not the L189 that the surface favours - so the OOS rows and the surface rest on different cells.
### S3 concentration (episodes = runs of constant sign)
| book | episodes | win rate | top-3 trades share of net | net excluding the top 3 | top-3 years share |
|--|--|--|--|--|--|
| ZF L189 | 77 | 29% | 99% | +$1.1k | 78% (2022, 2020, 2024) |
| ZT L189 | 80 | 31% | 98% | +$2.6k | 76% (2022, 2020, 2026) |
| ZT L315 | 54 | 31% | 89% | +$13.4k | 70% |
| ZF L252 | 49 | 27% | 315% | -$83.4k | 242% |
| ZT L252 | 58 | 28% | 127% | -$26.0k | 108% |
### S4 realism: lots, margin, live stack
ZF notional $118k per contract (tick $7.81, daily sigma about $212 per contract); ZT notional $216k per contract (tick $7.81, sigma about $131). The $1,200 daily-sigma target asks for 5.2 ZF and 5.7 ZT contracts on average and sits AT the cap of 6 contracts 58% (ZF) and 82% (ZT) of the days; at $2,400 it is at the cap 97-98% of the days: the 'vol-targeted' books are fixed 6-contract books (ZN 3.6 and ZB 1.6 contracts). Margin is not in the repository: PROXY (T4 assumed ZF $1.5k, ZT $1k per contract, unverified) = $9k and $6k at 6 contracts, notional about $0.7M (ZF) and $1.3M (ZT). Next to the live stack (V2 HOLD $28.2k a week mean, maxDD $91.2k): ZF L189 earns -$73 a week in HOLD, ZT L189 +$162, ZT L252 +$306 (0.6-1.1% of the stack); the stack can absorb k* = 5 books (the search limit) with a Calmar gain of +0.03 to +0.06; weekly correlation to the stack -0.02 to +0.05. Diversifying and immaterial.
### S5 ZF + ZT + ZN + ZB as ONE rates bet
P&L correlations (L189): ZF-ZT 0.77, ZF-ZN 0.84, ZF-ZB 0.58, ZT-ZN 0.61, ZT-ZB 0.39, ZN-ZB 0.75; effective independent bets 1.70 (L189) and 1.59 (L252); the signs agree 87-91% of the days. PORT4 at L189: net $393.9k, maxDD $113.6k, Calmar 0.24, 10 of 14 years positive, +$253.4k ex-2022; at L252: -$39.1k, maxDD $276k. Common-flip null (one shared random sign per calendar month for all four books, 1,000 worlds ids 3000-3999, counts the four as one bet): L189 z 2.14, p 0.015; L252 z 0.22, p 0.40. The L189 result is the best of 8 lookbacks (about 0.12 after the correction) and of a band that the prereg's coarser grid happened to hit.
### S6 regime feature ('momentum works in rates only when the Fed trends')
Causal regime = tercile of |ZT 252-day return| ranked against its own expanding history. P&L by regime tercile (net $k): ZF L189 6.8 (undefined, first 3 years) / 23.8 (low) / 20.7 (mid) / **89.6 (high)**; ZT L189 14.9 / 26.8 / 5.1 / **88.9**; ZN L189 9.1 / 2.0 / 29.1 / **91.8**; ZF L252 2.6 / -24.1 / -28.2 / **+87.9**; ZT L252 16.1 / -2.8 / -7.0 / **+90.4**: 60-100% of every book's profit arrives in the high-trend tercile (1,381 of 3,550 days) - descriptively, the reading holds. It is not usable causally: trading only when the regime is above its expanding median LOWERS the L189 books (ZF 140.9k -> 83.3k, ex-2022 +37.0k with Calmar 0.08; ZT 135.8k -> 86.3k, ex-2022 +33.8k, Calmar 0.07; ZN 132.1k -> 103.5k, ex-2022 Calmar 0.18) because the 252-day filter switches on after the trend began, and helps only the L252 books (ZF 38.2k -> 63.1k, ex-2022 +16.8k; ZT 96.6k -> 89.2k); the walk-forward with the on/off switch as an extra candidate gives no gain (ZF OOS +$118.0k vs +$132.2k without the switch; ZT +$96.1k vs +$96.1k). The pre-stated usability test (conditioned book keeps Calmar >= .10 ex-2022 and the WF OOS ex-2022 stays positive) is met only by ZN. **The regime is a description of where the P&L was, not a feature the walk-forward can use.**
### Verdict and next step
Plateau rule failed for ZF, ZT, ZN and ZB; ex-2022 the surviving cells are the post-hoc L189 band; the one-bet significance (p 0.015) does not survive the choice among 8 lookbacks; the economics are $0-300 a week against a $28k stack. **Label: best-of-F, REGIME-concentrated (2020-22), cells on a narrow ridge. No WATCH_ZF_MOM_SPEC.md is written and ZL-2 has nothing to register.** A genuinely new, separately preregistered test would be the only way to use the L189-231 band (the 2023-2026 years are +$29k to +$38k for the L189 books, so the band is not dead out of sample, but 2023-26 contains the band's own selection).
