# REPORT C2-G4 — calendar / seasonal sleeves on the non-index daily universe
Autopilot cycle 2. Rules frozen in `PREREG_AUTOPILOT.md` ("C2-G4 FROZEN RULES", 2026-10-15T22:10Z) before any return data was loaded for the test (only a loader smoke test on ZN prices). No date was tuned; no other rule was examined. 7 rules / 14 instrument sleeves, all reported.

## Verdict
**FOUND: 0. LEADS: 0 new.** No sleeve passes the pre-stated gates. The one interesting structure is historical: three of the seven independent rules beat their own random-date null in the a-priori 2013-2022 holdout and then did not carry into 2023-2026 (below). That is decay, not a new return stream.

## Method (fill model and slippage stated)
- Data: Databento `ohlcv-1d` continuous volume-front (`.v.0`, `.v.1` for roll spreads), back-adjusted with the T4 A loader (`t4_a_core.build`); UTC-day bars (not trading days), 2013-01-02..2026-10-14. 13 instruments: ZN ZB ZF NG HO RB CL ZC ZS ZW GC SI HE.
- Window [s,e]: enter at the OPEN of trading day s, exit at the CLOSE of day e; day P&L = open->close inside the window plus the close->open gaps strictly inside it. Fill: at the bar open/close price, 1 tick/side plus per-product commission (T4 A table, an assumption) and one extra round trip when a roll falls inside the window. No queue/gap model.
- Sizing: ATR20 vol target (1% of $700k per ATR, fractional contracts); each sleeve is then scaled so its clean-span weekly volatility equals the pair's (scale k below). Seasonal sleeves are sparse, so k is 2-11x and the implied sizes are large (margin table).
- Pair baseline: `B.Cfg(wk_floor=8, wk_loss_pb=None)` (clean 1.46 / H1 2.83 / H2 2.30), computed in a clean process; a robustness line vs `B.Cfg()` is in the last table.
- Spans: 2013-2022 (the a-priori untouched holdout for these a-priori rules), clean 2023-08..2025-07, H1, H2, pair window = 2023-08..2026-10-13. Sharpe = weekly, annualised sqrt(52), all weeks (zero-P&L weeks included). Sleeves with no window inside a span show n/a (R2, R5 have no H2 window; R4L no H1).
- Own null: random dates, same number of windows per calendar year and same length in trading days, same side, 501 draws; the same random calendar fraction is shared across instruments in a sleeve. Rank = share of null draws below the real Sharpe.
- Gate (pre-stated): a sleeve counts only if its rank is >= 0.95 BOTH in 2013-2022 and in the pair window, then T3 additive gates (+0.10 Sharpe on clean, H1, H2; worst week within the share; bootstrap 90% lo > 0; worst-decile corr <= +0.30), plateau, 2x slippage. Small-sample flag applies to every sleeve (<100 trades in the pair window; the 2013-2026 Sharpe is the primary evidence).

## 1. Standalone and own-null
| sleeve | Sh 2013-22 | rank vs own null (p95 level) | Sh clean | Sh H1 | Sh H2 | Sh pair window | rank pair window (null p95) | Sh 2013-26 |
|---|---|---|---|---|---|---|---|---|
| R1 bonds month-end (ZN,ZB,ZF) | 0.29 | 0.95 (0.30) | 1.43 | -2.07 | -1.40 | 0.18 | 0.83 (0.61) | 0.28 |
| R2 winter energy (NG,HO) Oct-Dec | -0.45 | 0.06 (0.45) | -0.33 | -0.18 | n/a | -0.23 | 0.50 (0.38) | -0.40 |
| R3 driving season (RB,CL) Feb-Apr | 0.10 | 0.68 (0.46) | -0.34 | -0.26 | 1.70 | 0.62 | 0.85 (0.78) | 0.23 |
| R4 grains LONG Mar1-Jun15 | 0.14 | 0.75 (0.39) | 0.02 | n/a | -0.92 | -0.31 | 0.35 (0.39) | 0.04 |
| R4 grains SHORT Jul-Sep | 0.48 | 0.94 (0.51) | 0.72 | 0.33 | -1.20 | -0.07 | 0.41 (0.79) | 0.31 |
| R4 grains L+S | 0.39 | 0.96 (0.35) | 0.50 | 0.33 | -1.53 | -0.26 | 0.50 (0.56) | 0.22 |
| R5 gold/silver Sep-Nov | -0.72 | 0.02 (0.31) | 0.39 | 2.74 | n/a | 0.99 | 0.76 (1.35) | -0.14 |
| R6 lean hogs Feb-Jun | 0.06 | 0.82 (0.26) | -0.32 | 1.36 | -2.00 | -0.64 | 0.30 (0.12) | -0.07 |
| R7 gold Monday short | 0.44 | 0.98 (0.35) | 0.35 | -2.62 | 0.18 | -0.32 | 0.66 (0.29) | 0.21 |
| ALL rules, equal risk | 0.06 | 0.87 (0.21) | 0.71 | 1.39 | -0.00 | 0.51 | 0.88 (0.63) | 0.15 |

Instrument sleeves:
| instrument sleeve | Sh 2013-22 | Sh pair window | Sh 2013-26 |
|---|---|---|---|
| R1:ZN | 0.16 | 0.14 | 0.17 |
| R1:ZB | 0.25 | -0.06 | 0.20 |
| R1:ZF | 0.42 | 0.49 | 0.44 |
| R2:NG | -0.36 | -0.11 | -0.30 |
| R2:HO | -0.36 | -0.29 | -0.34 |
| R3:RB | 0.19 | 0.84 | 0.33 |
| R3:CL | 0.01 | 0.41 | 0.12 |
| R4L:ZC | 0.14 | -0.53 | 0.04 |
| R4L:ZS | 0.19 | -0.05 | 0.12 |
| R4L:ZW | -0.00 | -0.12 | -0.06 |
| R4S:ZC | 0.61 | -0.33 | 0.34 |
| R4S:ZS | 0.25 | -0.15 | 0.15 |
| R4S:ZW | 0.42 | 0.28 | 0.36 |
| R5:GC | -0.73 | 0.93 | -0.15 |
| R5:SI | -0.65 | 0.91 | -0.12 |
| R6:HE | 0.06 | -0.64 | -0.07 |
| R7:GC | 0.44 | -0.32 | 0.21 |

**Multiplicity.** At p95 the expected count of rules beating their null by chance is 0.35 of 7 independent rules (R1, R2, R3, R4, R5, R6, R7). Observed in 2013-2022: R1 (rank 0.95), R4 (0.96; short leg 0.94), R7 (0.98) = 3 of 7, binomial p ~ 0.004. So there is something in 2013-2022 for bond month-end, grain weather/harvest and the gold-Monday effect. In the pair window none of them reaches the null's 95th percentile (ranks 0.83, 0.50, 0.66) and R4 and R7 have negative Sharpe. That is the gold/bond/grain seasonals fading after 2022, or luck in the first sample; the 2013-2026 Sharpe is 0.21-0.28.

## 2. Additive framing (pair 8/8 + 20% share), vs the live pair
| sleeve | k (scale to pair clean vol) | dSharpe clean | H1 | H2 | all | ww chg % | own-shift rank | boot 90% lo | worst-decile corr | verdict |
|---|---|---|---|---|---|---|---|---|---|---|
| R1 bonds month-end (ZN,ZB,ZF) | 6.3 | 0.23 | -0.38 | -0.46 | -0.02 | 29 | 0.25 | -0.20 | -0.19 | NO |
| R2 winter energy (NG,HO) Oct-Dec | 6.4 | -0.10 | -0.12 | 0.00 | -0.09 | 0 | 0.68 | -0.32 | -0.01 | UNSCORED (does not cover H2) |
| R3 driving season (RB,CL) Feb-Apr | 5.4 | -0.07 | -0.02 | 0.56 | 0.11 | 73 | 0.59 | -0.14 | 0.46 | NO |
| R4 grains LONG Mar1-Jun15 | 5.4 | -0.02 | 0.00 | -0.31 | -0.09 | 32 | 0.84 | -0.31 | 0.15 | UNSCORED (does not cover H1) |
| R4 grains SHORT Jul-Sep | 6.0 | 0.16 | -0.08 | -0.67 | -0.06 | 80 | 0.73 | -0.33 | 0.29 | NO |
| R4 grains L+S | 4.0 | 0.10 | -0.05 | -0.64 | -0.08 | 44 | 0.85 | -0.33 | 0.25 | NO |
| R5 gold/silver Sep-Nov | 4.1 | 0.06 | 0.79 | 0.00 | 0.18 | 52 | 0.55 | -0.04 | -0.11 | UNSCORED (does not cover H2) |
| R6 lean hogs Feb-Jun | 9.1 | -0.09 | 0.16 | -0.45 | -0.14 | 41 | 0.71 | -0.33 | -0.41 | NO |
| R7 gold Monday short | 10.7 | 0.06 | -0.90 | -0.01 | -0.09 | 24 | 0.59 | -0.28 | 0.18 | NO |
| ALL rules, equal risk | 2.2 | 0.14 | 0.32 | -0.16 | 0.10 | 45 | 0.81 | -0.14 | 0.28 | NO |

Column notes: 'ww chg %' = change in |worst week| (positive = worse; the gate allows at most the 20% share); 'own-shift rank' = circular-shift null rank (reported, not the gate). The same table vs `B.Cfg()` (robustness line):
| sleeve | clean | H1 | H2 | all | boot lo |
|---|---|---|---|---|---|
| R1 | 0.22 | -0.32 | -0.44 | -0.01 | -0.20 |
| R3 | -0.07 | -0.01 | 0.68 | 0.14 | -0.11 |
| R4 | 0.11 | -0.00 | -0.61 | -0.07 | -0.31 |
| R5 | 0.07 | 0.78 | 0.00 | 0.18 | -0.03 |
| R7 | 0.06 | -0.68 | -0.00 | -0.08 | -0.26 |
| ALL | 0.15 | 0.26 | -0.09 | 0.12 | -0.12 |

No sleeve lifts Sharpe by >= 0.10 in clean, H1 and H2 together. R1's clean uplift (+0.23) is paid for by H1 (-0.38) and H2 (-0.46). R5 (gold/silver autumn) is a good H1 (+0.79) from one autumn and has no H2 window, 2013-22 Sharpe -0.72: not evidence. Worst-decile weekly correlation with the pair is between -0.41 and +0.46 on 17 weeks, i.e. no hedge claim can be made (R3 +0.46 fails gate 6). All bootstrap lower bounds are negative or about zero.

## 3. Constant-risk (30% share)
| sleeve | all net % | worst week impr % | CVaR5 impr % | max DD impr % | verdict |
|---|---|---|---|---|---|
| R1 bonds month-end (ZN,ZB,ZF) | -26.8 | -18.5 | 13.4 | 19.8 | NO |
| R2 winter energy (NG,HO) Oct-Dec | -34.3 | -63.9 | 10.6 | -19.7 | NO |
| R3 driving season (RB,CL) Feb-Apr | -8.8 | -82.3 | 4.9 | 0.7 | NO |
| R4 grains LONG Mar1-Jun15 | -35.8 | -21.2 | 11.2 | -24.3 | NO |
| R4 grains SHORT Jul-Sep | -31.5 | -116.0 | 5.4 | -29.9 | NO |
| R4 grains L+S | -35.3 | -61.2 | 10.9 | -38.2 | NO |
| R5 gold/silver Sep-Nov | -11.8 | -51.9 | 9.3 | 0.6 | NO |
| R6 lean hogs Feb-Jun | -40.2 | -36.2 | 8.4 | 11.4 | NO |
| R7 gold Monday short | -35.2 | -10.8 | 10.4 | 7.9 | NO |
| ALL rules, equal risk | -18.5 | -39.5 | 2.3 | 7.5 | NO |

Every sleeve costs 9-40% of net (limit 5%); worst week is worse in every case. No INSURANCE.

## 4. Plateau (start and end shifted by +-1/+-2 trading days, 24 neighbours)
| sleeve | span | base Sharpe | share of 24 neighbours keeping >=75% | worst neighbour |
|---|---|---|---|---|
| R1 | 2013-22 | 0.29 | 0.50 | -0.39 |
| R1 | pairwin | 0.18 | 0.58 | -0.41 |
| R4S | 2013-22 | 0.48 | 0.71 | 0.33 |
| R4S | pairwin | -0.07 | 0.00 | -0.24 |
| R4 | 2013-22 | 0.39 | 0.79 | 0.21 |
| R4 | pairwin | -0.26 | 0.00 | -0.42 |
| R3 | 2013-22 | 0.10 | 0.58 | 0.02 |
| R3 | pairwin | 0.62 | 1.00 | 0.56 |
| R5 | 2013-22 | -0.72 | 0.00 | -0.79 |
| R5 | pairwin | 0.99 | 1.00 | 0.83 |
| ALL | 2013-22 | -0.00 | 0.00 | -0.25 |
| ALL | pairwin | 0.55 | 0.92 | 0.36 |

R1 keeps 50-58% of neighbours at >=75% of base (fails the 75% gate). R3 and R5 plateaus are good in the pair window but their pair-window Sharpes are single-season effects. R7 is a single-day window: not applicable.

## 5. 2x slippage (Sharpe by span)
| sleeve | Sh 2013-22 | clean | H1 | H2 | pair window | 2013-26 |
|---|---|---|---|---|---|---|
| R1 | 0.08 | 1.21 | -2.30 | -1.62 | -0.07 | 0.07 |
| R4S | 0.46 | 0.70 | 0.32 | -1.21 | -0.08 | 0.30 |
| R4 | 0.37 | 0.47 | 0.32 | -1.55 | -0.28 | 0.20 |
| R3 | 0.10 | -0.35 | -0.27 | 1.70 | 0.62 | 0.23 |
| R5 | -0.72 | 0.39 | 2.73 | n/a | 0.98 | -0.15 |
| ALL | -0.08 | 0.54 | 1.69 | -0.07 | 0.47 | 0.05 |


## 6. Executability and margin
All instruments are CME Group futures (CBOT/NYMEX/COMEX), executable on NT8 at NinjaTrader Brokerage via Rithmic (Y, from general knowledge — product availability not checked against the brokerage list). The strategies would be calendar-driven daily-bar NT8 strategies (enter at the open of a scheduled date, exit at the close), one per rule. Margin below is for the pair-volatility-scaled size (the sizes needed to matter next to an 8/8 NQ book); per-product margins are approximations, metals at an assumed 9% of notional (unverified):
| rule | instrument | contracts at pair-vol scale | margin $ (unverified) |
|---|---|---|---|
| R1 | ZN | 95 | 208,068 |
| R1 | ZB | 42 | 187,729 |
| R1 | ZF | 164 | 245,272 |
| R2 | NG | 46 | 182,614 |
| R2 | HO | 24 | 164,881 |
| R3 | RB | 20 | 141,025 |
| R3 | CL | 24 | 170,837 |
| R4L | ZC | 113 | 226,720 |
| R4L | ZS | 45 | 136,093 |
| R4L | ZW | 57 | 114,891 |
| R4S | ZC | 77 | 153,735 |
| R4S | ZS | 42 | 126,795 |
| R4S | ZW | 50 | 100,773 |
| R5 | GC | 16 | 679,572 |
| R5 | SI | 14 | 454,511 |
| R6 | HE | 100 | 199,343 |
| R7 | GC | 42 | 1,756,707 |

These margins ($0.1-1.8M per rule) show the sleeves are too thin per unit risk to be practical at pair-matched volatility.

## 7. Decisions and limits
- UTC-day bars; the window open/close are the bar open/close of the UTC day (not session open/close).
- The shared-fraction null keeps seasonal exposure structure (long-only) but randomises date; nulls for R4 use the sum of the L and S null draws.
- Everything here is at 1 tick/side; no live-fills calibration exists.
- Code: `code/census/night_ins/ap_c2_g4_run.py`, `ap_c2_g4_score.py`, `ap_c2_g4_alt.py`, `ap_c2_g4_report.py`; data `outputs/autopilot/c2/g4/` (standalone.csv, scored.csv, plateau.csv, margin.csv, alt_baseline.csv, sleeves.pkl, nulls_daily.pkl).
- Runtime: standalone + 8 null sets (501 draws each, 3 workers) 14 s; T3 scoring 5 s; plateau and 2x slippage a few seconds; about 30 s of compute in total.

DONE C2_G4
