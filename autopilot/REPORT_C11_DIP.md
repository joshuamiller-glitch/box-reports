# REPORT C11-DIP - ES RSI(2) dip-buy, one clean-only-selected cell

**Verdict (original, superseded by section 10 ERA re-issue): LEAD (not FOUND). All seven pair-window gates pass for the one pre-selected cell (ES RSI(2)<5 & close>SMA200, exit after 5 bars, 3xATR20 stop), but it is small-sample (23 trades in the pair window) and FAILS the scaled 2013-2022 replication required by the FOUND rule (2013-2022 standalone weekly Sharpe 0.08, additive uplift at 20% +0.01 vs the +0.10 gate, worst week 27% worse vs 20% allowed).** Headline: additive 20% uplift +0.27 / +1.06 / +0.25 (clean / H1 / H2), 2013-2026 Sharpe 0.80 but only 0.08 over 2013-2022. FOUND 0, LEAD 1 (previous T4-B/AMEND lead, now with plateau and 2x-slippage evidence and a failed replication). Runtime: selection 40 s, scoring 1-2 min on 5 workers.

## 1. Protocol (pre-registered in PREREG_AUTOPILOT.md, Cycle 11, before any run)
- Candidates: the 64 T4-B B1 cells (NQ/ES/RTY/YM x RSI(2)<{5,10} x exit {RSI>65, RSI>80, 3 bars, 5 bars} x stop {2,3} ATR20), rebuilt from 1-minute bars 2013-2026 (16:00 ET to 16:00 ET daily bars, difference back-adjusted at contract rolls; RTY from 2017). Fill model: entry and exit at the bar close (market-on-close fiction as in T4 B), stop filled at min(stop, open) minus one extra tick, 1 tick/side + $4.36 per contract round trip; 2x slippage = 2 ticks/side.
- Selection rule (written before scoring, clean 2023-08-01..2025-07-31 only): among cells with >= 10 clean trades, highest clean weekly Sharpe of 1-contract net P&L. 58 of 64 cells eligible; **selected ES dip_rsi5_days5_stop3 (clean Sharpe 1.81, 14 clean trades)**; runner-up ES dip_rsi5_days5_stop2 1.48, next ES dip_rsi10_days5_stop3 1.30 (file `outputs/autopilot/c11/dip_selection_clean_only.csv`). It is the same cell T4 B had singled out. Disclosure: T4 B and AMEND had already shown full-window numbers for this family, so H1/H2 were not virgin for it; the verdict is not softened for that.
- Pair = B.Cfg(wk_floor=8,wk_loss_pb=None) computed in a clean process (t3_score first). Sleeve scaled so its clean weekly sigma equals the pair's (100% share = pair-equivalent risk = 30.3 ES contracts-equivalent); additive = pair 8/8 + share x sleeve; constant-risk = (1-share) x pair + share x sleeve (16-contract-equivalent total).

## 2. Standalone (1 ES contract)
| span | net $ | $/yr | weekly Sharpe | MAR | maxDD $ | worst week $ | CVaR5 $ |
|---|---|---|---|---|---|---|---|
| clean | 54,476 | 26,553 | 1.81 | 6.9 | 7,879 | -3,342 | -1,575 |
| H1 | 38,103 | 71,657 | 3.72 | 5.6 | 6,750 | -3,562 | -1,781 |
| H2 | 13,283 | 18,911 | 1.21 | 1.9 | 7,054 | -4,942 | -2,954 |
| all | 105,862 | 32,219 | 2.05 | 13.4 | 7,879 | -4,942 | -2,102 |

Pair-window trades (2023-08..2026-10): **23** -> **SMALL-SAMPLE flag (< 100)**. Weekly correlation with the pair +0.05 (clean +0.16, H1 -0.11, H2 -0.11); in the pair's worst-decile weeks (17 weeks) correlation +0.10, but the sleeve averages $-3,321 there (positive in 0% of them): income stream, not a hedge. Beta to the pair +0.06.

## 3. Additive and constant-risk scoring (all shares; `t3_verdict` includes the circular-shift null, which is REPORTED, not gating, under the amendment)
| framing | share | clean | H1 | H2 | all_in | ww_chg_pct | boot90 | shift_p95 | net_pct | ww_impr | cvar5_impr | t3_verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| add | 10% | 0.15 | 0.57 | 0.14 | 0.20 | 1.85 | [+0.11, +0.30] | 0.24 | 11.95 | -1.85 | -0.72 | NO |
| add | 20% | 0.27 | 1.06 | 0.25 | 0.37 | 3.70 | [+0.20, +0.56] | 0.45 | 23.89 | -3.70 | -1.51 | NO |
| add | 30% | 0.38 | 1.44 | 0.34 | 0.51 | 5.56 | [+0.27, +0.77] | 0.64 | 35.84 | -5.56 | -2.36 | NO |
| add | 50% | 0.53 | 1.91 | 0.43 | 0.70 | 9.89 | [+0.35, +1.09] | 0.90 | 59.74 | -9.89 | -4.44 | NO |
| const | 10% | 0.16 | 0.63 | 0.15 | 0.22 | -8.15 | [+0.12, +0.33] | 0.26 | 1.95 | 8.15 | 9.28 | NO |
| const | 20% | 0.33 | 1.26 | 0.30 | 0.44 | -16.30 | [+0.24, +0.67] | 0.55 | 3.89 | 16.30 | 18.48 | NO |
| const | 30% | 0.49 | 1.78 | 0.41 | 0.64 | -24.44 | [+0.33, +0.99] | 0.82 | 5.84 | 24.44 | 27.41 | INSURANCE |
| const | 50% | 0.69 | 2.09 | 0.34 | 0.84 | -24.44 | [+0.30, +1.43] | 1.11 | 9.74 | 24.44 | 39.38 | INSURANCE |

Worst-week limit in the additive framing is the share itself; it holds at every share (change +1.9% .. +9.9%).

## 4. Seven gates at 20% share
| gate | result | number |
|---|---|---|
| 1 pre-registered, one clean-only cell | PASS | selection rule in PREREG before scoring |
| 2 selection touched only clean | PASS (with the disclosure above) | |
| 3 uplift >= +0.10 clean/H1/H2, worst week within share | PASS | +0.27 / +1.06 / +0.25; worst week +3.7% (limit 20%) |
| 4 own random-date null p95 on standalone Sharpe | PASS | real 2.05 vs p95 1.22 (median 0.35), rank 0.999, 1000 draws of 23 random signals with the same exits |
| 4 bootstrap 90% CI of all-in uplift > 0 | PASS | [+0.20, +0.56] |
| 4 circular-shift null (reported only) | not passed | uplift +0.37 vs p95 +0.45 |
| 5 plateau (+-25% neighbours) | PASS | 88% of 8 neighbours keep >= 75% of the all-in uplift |
| 5 2x slippage | PASS | uplift +0.27 / +1.05 / +0.25; standalone all-in Sharpe 2.04 |
| 6 worst-decile corr <= +0.30 | PASS | +0.10 |
| 7 executable spec | PASS | section 8 |
| REPLICATION (AUTOPILOT addition: pre-registered re-test on data selection never touched, scaled 2013-2022 history; uplift sign and magnitude must hold) | **FAIL** | section 6 |
| small-sample (< 100 trades in pair window) | FLAG | 23 trades |

## 5. Plateau detail (all-in uplift base +0.37 at 20%)
| change | trades | clean | H1 | H2 | all_in | keeps75 |
|---|---|---|---|---|---|---|
| lo=3.75 | 44 | 0.12 | 1.07 | 0.12 | 0.25 | False |
| lo=6.25 | 79 | 0.26 | 1.28 | 0.23 | 0.37 | True |
| sma_n=150 | 63 | 0.23 | 1.11 | 0.26 | 0.35 | True |
| sma_n=250 | 66 | 0.27 | 1.06 | 0.15 | 0.34 | True |
| ex=('days', 4) | 65 | 0.20 | 0.83 | 0.44 | 0.32 | True |
| ex=('days', 6) | 65 | 0.20 | 1.05 | 0.36 | 0.34 | True |
| sk=2.25 | 67 | 0.22 | 1.00 | 0.24 | 0.32 | True |
| sk=3.75 | 65 | 0.27 | 1.06 | 0.25 | 0.37 | True |

## 6. Long history and replication
2013-2026 standalone, same rule on the 1-minute-built 16:00 ET bars (1 ES contract): 65 trades, weekly Sharpe 0.80, $7,992/yr. **2013-2022 only: 40 trades, weekly Sharpe 0.08** (the T4-B UTC-day-bar figure was 0.55 over 2013-2026; this rebuild with proper 16:00 ET closes gives 0.80 all-in, and the pre-2023 part is flat). Per year:
| year | trades | net | wk_sharpe | wins | stops |
|---|---|---|---|---|---|
| 2013.00 | 1.00 | -454.36 | -0.26 | 0.00 | 0.00 |
| 2014.00 | 5.00 | -4669.93 | -1.55 | 0.20 | 1.00 |
| 2015.00 | 6.00 | 6261.34 | 2.03 | 1.00 | 0.00 |
| 2016.00 | 3.00 | 2686.92 | 0.83 | 1.00 | 0.00 |
| 2017.00 | 4.00 | 2820.06 | 1.70 | 0.75 | 0.00 |
| 2018.00 | 5.00 | -11491.80 | -1.32 | 0.40 | 3.00 |
| 2019.00 | 3.00 | -3723.08 | -0.83 | 0.33 | 1.00 |
| 2020.00 | 5.00 | 4235.07 | 0.35 | 0.60 | 1.00 |
| 2021.00 | 6.00 | 20311.34 | 1.50 | 0.83 | 0.00 |
| 2022.00 | 2.00 | -9793.09 | -1.08 | 0.00 | 1.00 |
| 2023.00 | 6.00 | 323.84 | 0.05 | 0.50 | 0.00 |
| 2024.00 | 9.00 | 57910.76 | 2.88 | 1.00 | 0.00 |
| 2025.00 | 5.00 | 19490.70 | 1.51 | 0.80 | 0.00 |
| 2026.00 | 5.00 | 28553.20 | 2.03 | 1.00 | 0.00 |

Replication: the same sleeve (same scale factor) added at share s to the C3-H2 1-minute-engine pair series 2013-2022 (entry match to the live engine 90%; that pair loses money there, weekly Sharpe -0.78): uplift in weekly Sharpe all 2013-2022, and per year:
| share | all_2013_22 | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 10% | 0.00 | -0.01 | -0.09 | 0.09 | 0.05 | 0.06 | -0.12 | -0.04 | 0.02 | 0.15 | -0.06 |
| 20% | 0.01 | -0.02 | -0.18 | 0.18 | 0.09 | 0.11 | -0.23 | -0.08 | 0.04 | 0.31 | -0.11 |
| 30% | 0.03 | -0.02 | -0.27 | 0.27 | 0.14 | 0.17 | -0.33 | -0.12 | 0.08 | 0.48 | -0.15 |
| 50% | 0.06 | -0.03 | -0.41 | 0.43 | 0.22 | 0.28 | -0.48 | -0.21 | 0.18 | 0.80 | -0.20 |

At 20% the 2013-2022 uplift is +0.013 (needs >= +0.10), positive in 5 of 10 years, and the pair's worst week deepens from $-80,246 to $-102,138 (+27%, share limit 20%). The 2023-2026 edge (23 trades; 2024 alone has Sharpe 2.9 on 9 trades) is not visible in 2013-2022 (40 trades, Sharpe 0.08; 2018 and 2022 lose money, 2018 with 3 of 5 trades stopped). That is a regime-specific or sample-luck pattern; the amended FOUND rule requires the replication, so the cell stays a LEAD.

## 7. Insurance metric set (weekly P&L, $)
| book | span | net | weekly_sharpe | sortino | MAR | maxDD | worst_week | CVaR5 | CVaR10 | pct_neg_wk |
|---|---|---|---|---|---|---|---|---|---|---|
| pair | clean | 1329959 | 1.46 | 2.78 | 4.75 | 280110 | -81874 | -78736 | -78009 | 42.86 |
| pair | H1 | 593797 | 2.83 | 6.09 | 3.91 | 151713 | -78287 | -77610 | -66030 | 39.29 |
| pair | H2 | 761254 | 2.30 | 4.69 | 3.50 | 217425 | -82524 | -81089 | -79185 | 44.44 |
| pair | all | 2685011 | 1.86 | 3.63 | 9.59 | 280110 | -82524 | -79220 | -78243 | 42.86 |
| add 20% | clean | 1660104 | 1.73 | 3.50 | 5.53 | 300363 | -82576 | -80035 | -78757 | 41.90 |
| add 20% | H1 | 824715 | 3.88 | 9.99 | 6.68 | 123502 | -78287 | -60679 | -54743 | 28.57 |
| add 20% | H2 | 841751 | 2.55 | 5.47 | 3.87 | 217425 | -85581 | -82617 | -79949 | 47.22 |
| add 20% | all | 3326570 | 2.22 | 4.65 | 11.08 | 300363 | -85581 | -80414 | -78907 | 41.07 |
| add 30% | clean | 1825176 | 1.84 | 3.82 | 5.88 | 310489 | -85278 | -80797 | -79235 | 40.95 |
| add 30% | H1 | 940174 | 4.27 | 11.96 | 7.61 | 123502 | -78287 | -60579 | -54343 | 28.57 |
| add 30% | H2 | 881999 | 2.63 | 5.72 | 4.06 | 217425 | -87109 | -83381 | -80331 | 44.44 |
| add 30% | all | 3647349 | 2.36 | 5.09 | 11.75 | 310489 | -87109 | -81093 | -79308 | 39.88 |
| const 20% | clean | 1394112 | 1.79 | 3.66 | 5.71 | 244341 | -67141 | -64302 | -63175 | 40.95 |
| const 20% | H1 | 705956 | 4.09 | 10.98 | 7.15 | 98801 | -62630 | -48463 | -43474 | 28.57 |
| const 20% | H2 | 689500 | 2.59 | 5.61 | 3.96 | 173940 | -69076 | -66399 | -64112 | 47.22 |
| const 20% | all | 2789568 | 2.30 | 4.88 | 11.42 | 244341 | -69076 | -64582 | -63273 | 40.48 |
| const 30% | clean | 1426189 | 1.95 | 4.22 | 6.30 | 226456 | -62127 | -57437 | -55944 | 41.90 |
| const 30% | H1 | 762035 | 4.61 | 14.27 | 8.81 | 86451 | -54801 | -42405 | -38040 | 28.57 |
| const 30% | H2 | 653623 | 2.70 | 5.93 | 4.29 | 152198 | -62352 | -59055 | -56576 | 41.67 |
| const 30% | all | 2841846 | 2.50 | 5.61 | 12.55 | 226456 | -62352 | -57504 | -55907 | 39.88 |

Constant-risk: at 30% share the t3 verdict is INSURANCE (worst week +24.4%, CVaR5 +27.4%, net +5.8%, clean/H1 not worse), as in T4 B; the flag arises because the pair shrinks by 30% in the pair's worst weeks while a 23-trade sleeve fills in, so it rests on 23 trades and fails the replication; I do not claim it.

## 8. Executability, sensitivity, margin
- Spec: ES (or MES at 1/10 size) daily bars on a 16:00 ET session template (one daily bar = 18:00 ET to 16:00 ET); at the 15:59 close compute RSI(2, Wilder) and SMA(200) of the bar closes and ATR(20) of bar high-low ranges; if RSI(2) < 5 and close > SMA200 and flat: buy at the close (MOC), place a protective sell stop at close - 3 x ATR(20); exit at the close 5 bars later (market) or on the stop; one position; roll with the front month. Sizing 30.3 contract-equivalents at 100% share -> 6.1 ES (61 MES) at 20%. Margin ~ $13,000 per ES (assumption, not checked against NinjaTrader's schedule) = ~$79k at 20%; overnight margin applies (positions are held 5 days). Executable at NinjaTrader Brokerage via Rithmic: yes expected (CME equity-index futures, general knowledge). Needs a new small daily NT8 strategy (not DualStrat): MOC-style entry is approximated by a market order in the last seconds of the 15:59 bar.
- Sensitivity (not a gate): entering at the NEXT open instead of the signal close gives uplift +0.27 / +0.79 / +0.32 (all-in +0.35), standalone Sharpe 2.11 on 23 trades, so the MOC fiction is not carrying the result.
- Limits: 23 trades; every pair-window trade is long in a rising market; a single 3 ATR gap-down year would reverse it; costs are placeholders; signal and fill share the same close.

## 9. Conclusion
The cell is the strongest small-sample income sleeve found so far in the pair window (all gates except replication pass, and the replication is the one that a 23-trade sample should fail). It goes to CANDIDATES.md as a LEAD with failed gate: replication/small-sample. Recommended next step: none beyond watching it live in paper at <= 10% share (it costs margin only), because more history does not exist.

Code: ap_c11_dip_core.py, ap_c11_dip_sel.py, ap_c11_dip_score.py, ap_c11_dip_repl.py, ap_c11_dip_rep.py; data outputs/autopilot/c11/.

## 10. ERA re-issue (GATE AMENDMENT 2, 2026-10-16; replication tests pre-registered in PREREG_AUTOPILOT.md before they were run; single registered cell, no re-selection)
**Re-issued verdict: FOUND under the amended gates, flagged SMALL-SAMPLE (23 trades in the pair window) and with a weak replication.** Gates 3-7 are unchanged and pass (section 4); 2013-2022 no longer gates. Replication needs >= 2 of 4 modern-era tests to hold (same sign, >= 50% of the +0.37 all-in reference, i.e. >= +0.18):
| test | result | holds |
|---|---|---|
| RA newest live weeks (2026-08-17..10-13) | 1 trade, uplift +0.14 | not testable (< 3 trades) |
| RB H0 2023-02-09..07-31 | 2 trades, uplift -0.00 | no (and too thin to mean anything) |
| RC cross-instrument 2023-08..2026-10, same rule, same scaling | NQ +0.22 (22 trades, standalone Sharpe 1.11), RTY +0.33 (18 trades, 1.28), YM +0.15 (21 trades, 0.91) | yes, 2 of 3 clear +0.18 |
| RD alternating-month split (odd / even months of 2023-08..2026-10; one cell, nothing to select, each half is a read) | odd +0.32, even +0.39 | yes |
Two of four hold (RC, RD) so the replication condition is met on the letter. Honest reading: RC instruments are strongly correlated with ES (the same index dip days), and RD halves share the same 23 trades in one rising market, so neither is independent evidence of a persistent edge; RA and RB had too few trades to test. Treat as FOUND at small size, not as proven.

**ERA FLAG: positive pre-2023.** 2013-2022 (40 trades, 1 ES contract): gross +$186 per trade, net at fixed cost +$155, net at price-scaled cost +$168 (ES averaged 3,572 then vs 6,424 in 2023-26, so a scaled cost is lower than fixed in the old era; costs are not what hides the edge). 2023-2026 (25 trades): gross +$4,281, net fixed +$4,251, net scaled +$4,252 per trade. The per-trade edge is about 23x larger in the modern era, mostly because the index moved ~1.8x and the dip bounces were large in 2024-26; pre-2023 is positive but economically negligible (weekly Sharpe 0.08).
**Mechanism (one sentence):** in an uptrend (close > SMA200) a 2-day sell-off to RSI(2) < 5 is forced/mechanical selling that mean-reverts within about a week, which retail-flow and dip-buying liquidity in the current regime has made reliable. It plausibly depends on current structure (the 2013-2022 edge is much smaller).
**Small-sample flag:** 23 trades in the pair window (< 100).

DONE C11-DIP
