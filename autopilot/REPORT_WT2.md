# REPORT WT2 - follow-up on WT-10 (ATR14 / mult 3 / no EMA / 10-min / 60-60, TH off): plateau, own-rules separate account, era, replication

**Verdict (re-issued under GATE AMENDMENT 2 - ERA): LEAD, not FOUND, not FOUND-PENDING.** The plateau gate still fails at the exact +-25% definition (one-at-a-time 3/8 = 0.375; with the 2-parameter corners 6/32 = 0.188), and **none of the modern-era replications holds**: H0 (2023-02..07) uplift -0.09 (needs the same sign and >= +0.19), ES and RTY median uplifts ~0 / negative, the odd/even-month split fails (odd-month uplift +0.07 = 18% of the full +0.37), newest live weeks: none beyond 2026-10-13 yet. The separate-account sleeve itself is fine on every other gate with its OWN rules (worst week met at every share). ERA FLAG: **negative pre-2023** (gross edge absent, not cost-eaten). Runtime about 2 h on 7 workers; same engines and verification as REPORT_WT.md (pre-registered in PREREG_AUTOPILOT.md, 'WT2 follow-up' and 'WT2 addition', before any run).

## 1. Plateau, exact +-25% (no new tuning)
Cell C* = ATR 14 / mult 3.0 / no EMA / 10-min / bracket 60 (NQ, 8 lots, 1-second engine, sleeve own rules on). Neighbours: ATR 11 and 18 (10.5/17.5 rounded), mult 2.25/3.75, bracket 45/75, timeframe 7/13 min. Uplift = all-in additive weekly-Sharpe uplift at 20% share (C* = 0.373); keep = >= 75% of it (0.280).

| kind | moved | spec | up_all | clean | H1 | H2 | sh | keep75 |
|---|---|---|---|---|---|---|---|---|
| C* | nan | nan | 0.37 | 0.37 | 0.42 | 0.31 | 2.05 | True |
| D1 | an | {'an': 11} | 0.34 | 0.43 | 0.26 | 0.08 | 1.80 | True |
| D1 | an | {'an': 18} | 0.28 | 0.23 | 0.27 | 0.44 | 1.55 | True |
| D1 | m | {'m': 2.25} | 0.19 | 0.18 | 0.54 | -0.04 | 1.06 | False |
| D1 | m | {'m': 3.75} | 0.05 | 0.16 | -0.45 | 0.03 | 0.54 | False |
| D1 | br | {'br': 45.0} | 0.36 | 0.29 | 0.28 | 0.58 | 1.90 | True |
| D1 | br | {'br': 75.0} | 0.21 | 0.24 | 0.32 | 0.05 | 1.40 | False |
| D1 | tf | {'tf': 7} | 0.15 | 0.11 | 0.73 | -0.11 | 0.86 | False |
| D1 | tf | {'tf': 13} | 0.18 | 0.25 | -0.03 | 0.07 | 1.13 | False |
| D2 | an+m | {'an': 11, 'm': 2.25} | 0.12 | 0.10 | 0.47 | -0.06 | 0.87 | False |
| D2 | an+m | {'an': 11, 'm': 3.75} | 0.03 | 0.21 | -0.61 | -0.08 | 0.47 | False |
| D2 | an+m | {'an': 18, 'm': 2.25} | 0.12 | 0.09 | 0.70 | -0.16 | 0.76 | False |
| D2 | an+m | {'an': 18, 'm': 3.75} | 0.12 | 0.24 | -0.32 | 0.02 | 0.92 | False |
| D2 | an+br | {'an': 11, 'br': 45.0} | 0.37 | 0.28 | 0.37 | 0.62 | 1.86 | True |
| D2 | an+br | {'an': 11, 'br': 75.0} | 0.18 | 0.24 | 0.20 | 0.01 | 1.15 | False |
| D2 | an+br | {'an': 18, 'br': 45.0} | 0.38 | 0.17 | 0.75 | 0.77 | 1.90 | True |
| D2 | an+br | {'an': 18, 'br': 75.0} | 0.21 | 0.21 | 0.33 | 0.13 | 1.26 | False |
| D2 | an+tf | {'an': 11, 'tf': 7} | 0.20 | 0.19 | 0.44 | 0.05 | 0.96 | False |
| D2 | an+tf | {'an': 11, 'tf': 13} | 0.17 | 0.21 | -0.01 | 0.13 | 0.93 | False |
| D2 | an+tf | {'an': 18, 'tf': 7} | 0.17 | 0.09 | 0.92 | -0.09 | 0.88 | False |
| D2 | an+tf | {'an': 18, 'tf': 13} | 0.10 | 0.21 | -0.15 | -0.08 | 0.81 | False |
| D2 | m+br | {'m': 2.25, 'br': 45.0} | 0.19 | 0.01 | 0.95 | 0.28 | 0.97 | False |
| D2 | m+br | {'m': 2.25, 'br': 75.0} | 0.10 | 0.08 | 0.43 | -0.09 | 0.54 | False |
| D2 | m+br | {'m': 3.75, 'br': 45.0} | 0.10 | 0.22 | -0.33 | -0.03 | 0.65 | False |
| D2 | m+br | {'m': 3.75, 'br': 75.0} | -0.02 | 0.06 | -0.35 | -0.10 | 0.40 | False |
| D2 | m+tf | {'m': 2.25, 'tf': 7} | -0.10 | -0.15 | -0.20 | 0.04 | -0.70 | False |
| D2 | m+tf | {'m': 2.25, 'tf': 13} | 0.36 | 0.39 | 0.54 | 0.16 | 1.95 | True |
| D2 | m+tf | {'m': 3.75, 'tf': 7} | 0.26 | 0.34 | 0.48 | -0.15 | 1.46 | False |
| D2 | m+tf | {'m': 3.75, 'tf': 13} | -0.09 | 0.04 | -0.46 | -0.24 | -0.01 | False |
| D2 | br+tf | {'br': 45.0, 'tf': 7} | 0.15 | 0.06 | 0.26 | 0.29 | 0.88 | False |
| D2 | br+tf | {'br': 45.0, 'tf': 13} | 0.10 | 0.08 | 0.35 | 0.07 | 0.75 | False |
| D2 | br+tf | {'br': 75.0, 'tf': 7} | 0.18 | 0.19 | 0.04 | 0.21 | 1.05 | False |
| D2 | br+tf | {'br': 75.0, 'tf': 13} | 0.11 | 0.10 | 0.10 | 0.10 | 0.80 | False |

**D1 (one at a time): 3 of 8 keep = 0.375; D1+D2 (32 cells): 6 keep = 0.188; corners only: 3 of 24 = 0.125. Gate (>= 0.75) FAILS under both definitions.** The edge survives a +-25% move in ATR period and a tighter bracket, but not a move of the multiplier (2.25: 0.19, 3.75: 0.05) or the timeframe (7: 0.15, 13: 0.18) or a wider bracket (75: 0.22). The earlier REPORT_WT (tf 8/12) gave 4/8; at the pre-registered tf 7/13 it is 3/8.

## 2. WT-10 as a separate account, with its own rules
Sleeve = WT alone, 60-pt bracket, per-book 5R/-2R day rule at WT's own R (60 x contracts x $20), own day lock (cap 8R / arm 2R / give-back 67%), own week floor (8R, and a tight 4R variant), no netting with the pair, TH off. Rules, costs and P&L are linear in contracts, so a size-n sleeve is n/8 of the 8-lot run with the rules in its own R. Share = sleeve weekly vol as a fraction of the pair's clean weekly vol (20% share = 3.4 NQ contracts).

| rules | share | sleeve_contracts | up_clean | up_H1 | up_H2 | up_all | pair_worst_week | sleeve_worst_week | combo_worst_week | ww_chg_pct | limit_pct | pass_ww | sleeve_ww_share_of_pair | sleeve_maxdd |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| floor8R | 0.10 | 1.72 | 0.19 | 0.24 | 0.17 | 0.20 | -82,524 | -12,658 | -84,666 | 2.60 | 10.00 | True | 0.15 | 45,869 |
| floor8R | 0.20 | 3.45 | 0.37 | 0.42 | 0.31 | 0.37 | -82,524 | -25,317 | -91,127 | 10.42 | 20.00 | True | 0.31 | 91,739 |
| floor8R | 0.30 | 5.17 | 0.52 | 0.57 | 0.41 | 0.52 | -82,524 | -37,975 | -97,983 | 18.73 | 30.00 | True | 0.46 | 137,608 |
| floor8R | 0.50 | 8.62 | 0.75 | 0.76 | 0.54 | 0.73 | -82,524 | -63,292 | -111,695 | 35.35 | 50.00 | True | 0.77 | 229,347 |
| floor4R | 0.10 | 1.74 | 0.19 | 0.24 | 0.10 | 0.18 | -82,524 | -8,822 | -85,780 | 3.95 | 10.00 | True | 0.11 | 56,041 |
| floor4R | 0.20 | 3.49 | 0.36 | 0.43 | 0.18 | 0.34 | -82,524 | -17,644 | -94,302 | 14.27 | 20.00 | True | 0.21 | 112,081 |
| floor4R | 0.30 | 5.23 | 0.50 | 0.58 | 0.22 | 0.47 | -82,524 | -26,466 | -102,823 | 24.60 | 30.00 | True | 0.32 | 168,122 |
| floor4R | 0.50 | 8.72 | 0.73 | 0.77 | 0.22 | 0.65 | -82,524 | -44,111 | -119,866 | 45.25 | 50.00 | True | 0.53 | 280,203 |

Worst week of pair + sleeve vs the pair alone: +2.6% / +10.4% / +18.7% / +35.3% at 10/20/30/50% share (limit = the share): **passes at every share with the 8R floor** (the earlier +10.4% at 20% was already with the sleeve's own rules); the 4R floor keeps it inside the share too (+3.9 / +14.3 / +24.6 / +45.3%) but costs uplift (H2 +0.18 vs +0.31 at 20%). The sleeve's own worst week is 15% / 31% / 46% / 77% of the pair's worst week.

### Two-account totals, sizes 2/3/4/6 NQ, pair at 8/8 and at 6/6 (all-in 2023-08..2026-10; spans below)
| pair | cell | net | sharpe | sortino | mar | maxdd | worst_week | cvar5 | cvar10 | neg_wk | wd_corr_sleeve | all_corr_sleeve | gross_contracts_max |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 8/8 | pair alone | 2,685,011 | 1.86 | 3.63 | 9.59 | 280,110 | -82,524 | -79,220 | -78,243 | 42.86 | nan | nan | 16 |
| 8/8 | pair+WT2 | 3,037,152 | 2.08 | 4.22 | 12.37 | 245,568 | -85,688 | -81,956 | -78,578 | 41.67 | -0.20 | -0.00 | 18 |
| 8/8 | pair+WT3 | 3,213,223 | 2.19 | 4.50 | 14.07 | 228,297 | -89,389 | -83,748 | -79,000 | 41.07 | -0.20 | -0.00 | 19 |
| 8/8 | pair+WT4 | 3,389,294 | 2.28 | 4.74 | 15.38 | 220,418 | -93,325 | -85,712 | -79,749 | 38.69 | -0.20 | -0.00 | 20 |
| 8/8 | pair+WT6 | 3,741,435 | 2.44 | 5.15 | 17.13 | 218,389 | -101,280 | -90,598 | -82,199 | 36.31 | -0.20 | -0.00 | 22 |
| 8/8 | pair+WT4 (entry@signal close) | 3,353,348 | 2.26 | 4.70 | 15.19 | 220,758 | -93,349 | -85,278 | -79,560 | 38.69 | -0.19 | -0.01 | 20 |
| 6/6 | pair alone | 2,124,786 | 1.64 | 3.00 | 6.72 | 316,358 | -78,642 | -77,944 | -77,570 | 41.67 | nan | nan | 12 |
| 6/6 | pair+WT2 | 2,476,927 | 1.90 | 3.61 | 8.79 | 281,817 | -85,053 | -78,891 | -75,832 | 39.29 | -0.41 | 0.00 | 14 |
| 6/6 | pair+WT3 | 2,652,998 | 2.01 | 3.90 | 9.26 | 286,483 | -89,031 | -79,791 | -75,622 | 37.50 | -0.41 | 0.00 | 15 |
| 6/6 | pair+WT4 | 2,829,069 | 2.11 | 4.16 | 9.64 | 293,320 | -93,008 | -81,351 | -75,844 | 37.50 | -0.41 | 0.00 | 16 |
| 6/6 | pair+WT6 | 3,181,210 | 2.28 | 4.63 | 10.36 | 306,994 | -100,963 | -84,873 | -77,590 | 40.48 | -0.41 | 0.00 | 18 |
| 6/6 | pair+WT4 (entry@signal close) | 2,793,122 | 2.09 | 4.12 | 9.68 | 288,472 | -87,820 | -80,835 | -75,597 | 38.10 | -0.41 | -0.01 | 16 |

Weekly Sharpe by span:

| pair | cell | clean | H1 | H2 |
|---|---|---|---|---|
| 6/6 | pair alone | 1.17 | 3.70 | 1.72 |
| 6/6 | pair+WT2 | 1.42 | 4.04 | 1.90 |
| 6/6 | pair+WT3 | 1.54 | 4.18 | 1.98 |
| 6/6 | pair+WT4 | 1.64 | 4.29 | 2.06 |
| 6/6 | pair+WT4 (entry@signal close) | 1.63 | 4.25 | 2.01 |
| 6/6 | pair+WT6 | 1.82 | 4.44 | 2.17 |
| 8/8 | pair alone | 1.46 | 2.83 | 2.30 |
| 8/8 | pair+WT2 | 1.68 | 3.10 | 2.49 |
| 8/8 | pair+WT3 | 1.78 | 3.21 | 2.57 |
| 8/8 | pair+WT4 | 1.88 | 3.30 | 2.64 |
| 8/8 | pair+WT4 (entry@signal close) | 1.86 | 3.28 | 2.61 |
| 8/8 | pair+WT6 | 2.04 | 3.46 | 2.75 |

Margin: no per-contract NQ margin source is on this box, so none is asserted. Added exposure: +2/+3/+4/+6 contracts on top of 16 (8/8) or 12 (6/6) maximum gross contracts, i.e. +12.5% .. +37.5% (8/8) or +17% .. +50% (6/6), held through the Globex night (flat 16:55-18:00 only). Margin = added contracts x the account's per-contract NQ requirement (to be filled from the broker's current schedule).
Reading: every size improves Sharpe on all three spans against both pair sizes (8/8: 1.86 -> 2.08/2.19/2.28/2.44; 6/6: 1.64 -> 1.90/2.01/2.11/2.28), reduces %neg weeks and (8/8) max drawdown (280k -> 246k/228k/220k/218k) but worsens the worst week (-$82.5k -> -$85.7k/-$89.4k/-$93.3k/-$101.3k, +4% .. +23%) and CVaR5 slightly; sleeve-vs-pair correlation 0.00 all weeks, -0.20 (8/8) / -0.41 (6/6) in the worst-decile weeks.

### (i) Entry timing
Harness: signal at the 10-minute bar close, market entry at the open of the next 1-minute bar. NT8 on a 10-minute chart with on-bar-close logic submits the market order when the bar closes and the fill is the first tick of the next bar - the same instant, price = the 10-min bar close print (within a tick of the next 1-min open). Variant run: entry price = the signal bar's last 1-minute close instead of the next open (pts shifted by side x (open_next - close_signal), bracket levels not shifted): sleeve Sharpe 2.05 -> 1.91, pair + WT4 at 8/8 2.28 -> 2.26 (clean 1.88 -> 1.86, H1 3.30 -> 3.28, H2 2.64 -> 2.61), at 6/6 2.11 -> 2.09. The difference is small; a real NT8 fill sits between the two. Not simulated: NT8 evaluating the 60/60 bracket on 10-minute bars instead of ticks (the engine uses seconds, as for ST/HM).

## 3. Era: why -1.38 on 2013-22 at faithful scaling and +1.82 in 2023-26
By year (scaling a: bracket 60 x price/20000, 1-minute engine):

| year | median_price | atr14_10m_pts | atr_pct | br_a_pts | br_a_over_atr | a_trades_day | a_win% | a_pts_per_trade | a_hold_min | a_netR | a_sharpe |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 2,013 | 3,008 | 2.33 | 0.08 | 9.02 | 3.88 | 1.84 | 44.69 | -0.80 | 185.00 | -77.47 | -3.96 |
| 2,014 | 3,816 | 2.92 | 0.08 | 11.45 | 3.92 | 1.88 | 50.90 | 0.25 | 157.00 | -18.72 | -0.87 |
| 2,015 | 4,434 | 4.34 | 0.10 | 13.30 | 3.06 | 2.15 | 48.76 | -0.53 | 103.00 | -50.19 | -2.33 |
| 2,016 | 4,530 | 4.10 | 0.09 | 13.59 | 3.31 | 2.05 | 48.51 | -0.37 | 119.00 | -41.26 | -1.74 |
| 2,017 | 5,797 | 3.20 | 0.06 | 17.39 | 5.43 | 1.73 | 48.94 | 0.02 | 284.00 | -19.78 | -1.05 |
| 2,018 | 6,965 | 7.66 | 0.11 | 20.89 | 2.73 | 2.32 | 51.72 | 0.75 | 88.50 | 0.48 | 0.03 |
| 2,019 | 7,688 | 6.97 | 0.09 | 23.06 | 3.31 | 2.08 | 46.88 | -1.70 | 128.50 | -55.79 | -2.48 |
| 2,020 | 10,352 | 16.72 | 0.16 | 31.06 | 1.86 | 2.50 | 49.60 | -0.30 | 45.00 | -17.50 | -0.59 |
| 2,021 | 14,556 | 14.64 | 0.10 | 43.67 | 2.98 | 2.20 | 52.15 | 1.48 | 103.00 | 9.83 | 0.44 |
| 2,022 | 12,434 | 23.09 | 0.19 | 37.30 | 1.62 | 2.54 | 48.13 | -1.27 | 37.00 | -39.24 | -1.58 |
| 2,023 | 14,824 | 13.74 | 0.09 | 44.47 | 3.24 | 2.27 | 54.17 | 4.00 | 89.00 | 41.55 | 1.84 |
| 2,024 | 19,092 | 17.86 | 0.09 | 57.28 | 3.21 | 2.22 | 54.68 | 5.12 | 125.00 | 41.27 | 1.88 |
| 2,025 | 22,856 | 23.61 | 0.10 | 68.57 | 2.90 | 2.09 | 54.34 | 6.07 | 97.00 | 39.79 | 1.72 |
| 2,026 | 28,908 | 34.87 | 0.12 | 86.72 | 2.49 | 2.61 | 51.86 | 4.02 | 84.00 | 18.27 | 1.06 |

Bracket / ATR is 2.5-5.4 in every year (the scaling works), so the bracket is not the issue; **what changes is the win rate and the points per trade**: win rate 42-51% and mean trade -1.7..+0.75 pt before 2023 against 54-55% and +4..+6 pt in 2023-2026, while the 10-minute ATR rises from 2-8 pt (0.06-0.11% of price) to 14-35 pt (0.09-0.12%) - relative volatility is not larger now, but intraday trends beyond the 3 x ATR trail persisted much more (hold time falls from 100-800 minutes to 85-170).

### Cost decomposition (scaling a; per trade in bracket units; "fixed cost" = 1 tick/side + $4.36/contract as live, "price-scaled" = cost x price/20000)
| year | median_price | tick_bp | trades_day | gross_ticks_per_trade | gross_bracket_units_per_trade | net_fixedcost_R_per_trade | net_pricescaledcost_R_per_trade | cost_R_per_trade_fixed | cost_R_per_trade_scaled |
|---|---|---|---|---|---|---|---|---|---|
| 2,013 | 3,008 | 0.83 | 1.85 | -2.96 | -0.08 | -0.17 | -0.09 | 0.09 | 0.01 |
| 2,014 | 3,816 | 0.66 | 1.88 | 1.01 | 0.02 | -0.04 | 0.01 | 0.06 | 0.01 |
| 2,015 | 4,434 | 0.56 | 2.15 | -1.94 | -0.04 | -0.10 | -0.05 | 0.06 | 0.02 |
| 2,016 | 4,530 | 0.55 | 2.05 | -1.47 | -0.02 | -0.08 | -0.04 | 0.06 | 0.01 |
| 2,017 | 5,798 | 0.43 | 1.73 | 0.07 | -0.00 | -0.05 | -0.02 | 0.04 | 0.01 |
| 2,018 | 6,965 | 0.36 | 2.32 | 2.85 | 0.03 | 0.00 | 0.02 | 0.03 | 0.01 |
| 2,019 | 7,688 | 0.33 | 2.08 | -6.80 | -0.07 | -0.11 | -0.09 | 0.03 | 0.02 |
| 2,020 | 10,353 | 0.24 | 2.50 | -1.37 | -0.01 | -0.03 | -0.02 | 0.02 | 0.01 |
| 2,021 | 14,559 | 0.17 | 2.20 | 5.91 | 0.04 | 0.02 | 0.02 | 0.02 | 0.02 |
| 2,022 | 12,434 | 0.20 | 2.53 | -4.85 | -0.03 | -0.06 | -0.05 | 0.03 | 0.02 |
| 2,023 | 14,823 | 0.17 | 2.27 | 16.23 | 0.09 | 0.07 | 0.08 | 0.02 | 0.01 |
| 2,024 | 19,092 | 0.13 | 2.22 | 20.50 | 0.09 | 0.07 | 0.07 | 0.01 | 0.01 |
| 2,025 | 22,856 | 0.11 | 2.09 | 24.27 | 0.09 | 0.08 | 0.08 | 0.01 | 0.01 |
| 2,026 | 28,908 | 0.09 | 2.61 | 16.09 | 0.05 | 0.04 | 0.03 | 0.01 | 0.01 |

Averages: **2013-22 gross -0.0172 R/trade (about -1 tick), net at fixed cost -0.0617, net at price-scaled cost -0.0307; 2023-26 gross +0.0784 R (+19 ticks), net +0.0651 / +0.0654.** Plain statement: **this is a gross-edge loss, not a fixed-dollar cost eating a gross edge**: before 2023 the gross edge is about zero (positive only in 2014, 2018, 2021 at +0.02..+0.04 R) and even with cost scaled to the price level the net stays negative (-0.031 R/trade); the fixed dollar cost adds roughly another -0.03 R/trade in 2013-2017 (cost/bracket 0.06-0.09 R vs 0.01-0.02 R scaled) and turns 2014 and 2018 negative. ERA FLAG: **negative pre-2023**. Weekly results of the pair and WT-10 are uncorrelated (2013-22 weekly corr 0.09, 2023-26 0.05; WT-LIVE 0.47/0.41), but their **years coincide**: yearly net R correlation 0.84 (0.87 on 2013-22 alone); both are negative in 2013-17, 2019, 2022; WT-10 is better than the pair in 2023 (+42 R vs -47 R). So WT's bad years are the pair's bad years (same trend-regime dependence) while its weeks are not the pair's weeks.

| year | pair_netR | pair_sh | WT10_netR | WT10_sh | WTLIVE_netR | WTLIVE_sh | wk_corr_WT10 | wk_corr_WTLIVE |
|---|---|---|---|---|---|---|---|---|
| 2,013 | -137.29 | -3.44 | -77.47 | -3.96 | -114.59 | -3.97 | 0.11 | 0.55 |
| 2,014 | -77.69 | -1.99 | -18.72 | -0.87 | -56.36 | -1.77 | -0.16 | 0.66 |
| 2,015 | -69.03 | -1.53 | -50.19 | -2.33 | -36.13 | -0.95 | 0.33 | 0.59 |
| 2,016 | -140.06 | -3.73 | -41.26 | -1.74 | -60.07 | -2.38 | 0.19 | 0.24 |
| 2,017 | -22.11 | -0.59 | -19.78 | -1.05 | -2.43 | -0.11 | 0.03 | 0.47 |
| 2,018 | 24.66 | 0.50 | 0.48 | 0.03 | -48.81 | -1.54 | 0.25 | 0.39 |
| 2,019 | -105.16 | -2.41 | -55.79 | -2.48 | -34.34 | -1.30 | -0.03 | 0.41 |
| 2,020 | 0.34 | 0.01 | -17.50 | -0.59 | -61.90 | -1.71 | -0.03 | 0.43 |
| 2,021 | 39.30 | 0.85 | 9.83 | 0.44 | 10.75 | 0.40 | -0.01 | 0.48 |
| 2,022 | -118.13 | -2.39 | -39.24 | -1.58 | -74.71 | -2.16 | 0.08 | 0.41 |
| 2,023 | -47.23 | -1.18 | 41.55 | 1.84 | -19.99 | -0.61 | 0.18 | 0.26 |
| 2,024 | 111.39 | 2.55 | 41.27 | 1.88 | 71.15 | 1.82 | -0.03 | 0.37 |
| 2,025 | 119.82 | 2.14 | 39.79 | 1.72 | 53.51 | 1.68 | -0.08 | 0.50 |
| 2,026 | 42.01 | 0.98 | 18.27 | 1.06 | -2.40 | -0.10 | 0.24 | 0.48 |

## 4. Replication on modern-era data not used for selection (pre-registered)
**(a) ES and RTY, same spec, 2023-02..2026-10** (1-minute engine of d1_f4_core, bracket = 0.2109 x ADR20 = the NQ clean ratio, equal R, 1 tick/side + $4.36; ATR {10,14,18} x tf {8,10,12}, all 9 cells per instrument reported, none selected; NQ comparator in the same engine):

| sym | up20_clean | up20_H1 | up20_H2 | up20_all | sh_all | sh_clean | sh_H1 | sh_H2 |
|---|---|---|---|---|---|---|---|---|
| ES | 0.03 | 0.08 | -0.13 | -0.01 | -0.10 | 0.14 | 0.18 | -0.45 |
| NQ | 0.18 | 0.32 | 0.01 | 0.17 | 1.09 | 1.19 | 1.82 | 0.21 |
| RTY | -0.22 | 0.11 | 0.06 | -0.12 | -0.39 | -0.97 | 0.57 | 0.04 |

Cells with positive 20% uplift on all three spans (of 9): ES 0, NQ 5, RTY 0. NQ in this lower-fidelity engine: median uplift +0.18/+0.32/+0.01 (H2 collapses to zero with an ADR bracket and the 1-minute fills). **ES: median standalone Sharpe -0.1, uplift +0.03/+0.08/-0.13; RTY: -0.39, -0.22/+0.11/+0.06. Replication FAILS on both instruments.** Full table: `outputs/autopilot/wt/WT2_rep.csv`.

**(b) H0 window 2023-02-10..2023-07-31** (26 weeks, before the clean span; pair Sharpe 0.67 there; scaling from clean):

| cell | weeks | sleeve_sh | pair_sh | combo_sh | up20 |
|---|---|---|---|---|---|
| (10, 3.0, 0, 10, 'X1') | 26 | -0.49 | 0.67 | 0.56 | -0.12 |
| (10, 3.0, 100, 10, 'X1') | 26 | 0.80 | 0.67 | 0.81 | 0.14 |
| (10, 3.0, 200, 10, 'X1') | 26 | 1.68 | 0.67 | 1.00 | 0.33 |
| (10, 4.0, 0, 5, 'X2') | 26 | -1.87 | 0.67 | 0.36 | -0.31 |
| (14, 3.0, 0, 10, 'X1') | 26 | -0.31 | 0.67 | 0.58 | -0.09 |
| (14, 3.0, 0, 10, 'X2') | 26 | -1.24 | 0.67 | 0.50 | -0.17 |
| (14, 3.0, 100, 10, 'X1') | 26 | 0.30 | 0.67 | 0.69 | 0.02 |
| (14, 4.0, 0, 5, 'X2') | 26 | -3.13 | 0.67 | 0.28 | -0.39 |
| (14, 4.0, 100, 5, 'X2') | 26 | -1.09 | 0.67 | 0.50 | -0.17 |
| (20, 2.0, 100, 1, 'X1') | 26 | -1.42 | 0.67 | 0.41 | -0.26 |
| (20, 4.0, 0, 5, 'X2') | 26 | -2.52 | 0.67 | 0.34 | -0.33 |

C* sleeve Sharpe -0.31 and uplift **-0.09** (clean was +0.37): FAILS (WT-LIVE -0.26, also fails). Only the cells with EMA 100/200 on 10-min bars are positive in H0.

**(c) Alternating-month split within 2023-08..2026-10** (select on odd months, read on even, then reverse; full 432-cell selection redone on the selecting months, eligible >= 150 trades per half and Sharpe > 0; uplift at 20%):

| select | read | n_eligible | sel_top1 | sel_top1_up | read_top1_up | sel_top10_mean_up | read_top10_mean_up | read_top10_pos_share | Cstar_up_on_select_months | Cstar_up_on_read_months |
|---|---|---|---|---|---|---|---|---|---|---|
| odd | even | 262 | {'an': 10, 'm': 3.0, 'ema': 200, 'tf': 5, 'exit': 'X1'} | 0.35 | -0.06 | 0.29 | -0.13 | 0.10 | 0.07 | 0.61 |
| even | odd | 226 | {'an': 14, 'm': 3.0, 'ema': 0, 'tf': 10, 'exit': 'X1'} | 0.61 | 0.07 | 0.45 | -0.02 | 0.60 | 0.61 | 0.07 |

Odd -> even: the selected top cell (ATR10/3/EMA200/5-min) reads -0.06 on even months, top-10 mean -0.13 (only 1 of 10 positive). Even -> odd: the selected cell is C* itself (+0.61 on even months) and it reads **+0.07 on odd months = 18% of its full-window +0.37 (needs >= 50%)**; top-10 mean -0.02. FAILS. C*'s uplift is concentrated in even-numbered months (Feb/Apr/Jun/Aug/Oct/Dec).

**(d) Newest live weeks:** none after 2026-10-13 (H2 is the newest data), not available.
Count: 0 of 3 available replications hold (need 2). Under Amendment 2 the plateau remains required and also fails.

## 5. Selection-aware accounting
60 timing-destroyed replicates of the whole 432-cell family over the pair window (random entries, same count and hold distribution per cell, same sleeve rules, uplift at 20%): the number of cells passing the uplift gate (>= +0.10 on clean, H1 and H2) has mean **1.10** (median 1, max 5), i.e. a per-cell chance-pass rate of 0.25% and **~1.1 expected false uplift-gate passes per 432-cell family**; top-10-by-clean cells passing all three: mean 0.48; best clean uplift under the null averages 0.32 (max 0.51). Real family: **18 cells pass the uplift gate** (C*, WT-LIVE, WT-B10-like ATR10-30 cells, 5/10-min X1 and X2) against a null maximum of 5 in 60 replicates. So the 2023-26 structure is real as structure (p < 1/60), and C* is its best member; but the full gate set then removes it (plateau, replication). Expected false FOUNDs for this family under all gates: well below 0.01 (the null has ~1 uplift-gate pass; plateau and replication each remove most).

## 6. Gates (FOUND needs all) - WT-10 as a separate-account sleeve, Amendment 2 applied
| gate | WT-10 (C*) |
|---|---|
| 1 pre-registered | PASS |
| 2 selection on clean only; H1/H2 once | PASS |
| 3 uplift >= +0.10 on clean/H1/H2 (10/20/30/50%) | PASS +0.37/+0.42/+0.31 at 20% (and at all shares) |
| 3b worst week not worse than the share, sleeve with own rules | PASS at every share (8R floor) |
| 4 own timing-destroyed null p95; bootstrap | PASS (2.05 vs 0.56); PASS lo +0.19 |
| 5 plateau at exact +-25% | **FAIL** (D1 3/8, D1+D2 6/32) |
| 5 2x slippage | PASS +0.34/+0.41/+0.25 |
| 6 worst-decile corr <= +0.30 | PASS -0.20 |
| 7 NT8 spec + margin | spec yes (REPORT_WT.md); margin: broker schedule not on box |
| Replication (>= 2 of newest weeks / H0 / ES-RTY / alternating month) | **FAIL (0 of 3 available)** |
| ERA flag | negative pre-2023 (gross-edge loss) |
| **Verdict** | **LEAD** |

**Mechanism (one sentence):** a 10-minute Wilder ATR ratchet trail flip (3 x ATR(14)) buys/sells intraday NQ trend persistence beyond a volatility-scaled trail, banked by a symmetric 60-point bracket. **Structure dependence:** yes - the gross edge (+19 ticks/trade) exists only in 2023-2026 when intraday NQ trends persisted (win rate 54-55% vs 42-51% before), it concentrates in even-numbered months and in the clean/H1 stretch, is absent on ES, RTY and in H0, and the pair's bad years are its bad years; treat it as a current-regime trend overlay, not a structural edge.

## 7. B1-style WT on ES/RTY/GC/CL/ZN
Not repeated: REPORT_B1.md already ran WT_MODAL-style signals (ATR-trail exits, 5-30 min) on ES, RTY, GC, CL, ZN (WT cells are NO or diagnostic there); the cell-specific ES/RTY replication above is the relevant addition.

Code: `code/census/night_ins/ap_wt2_a.py` (plateau, own rules), `ap_wt2_sizes.py`, `ap_wt2_era.py`, `ap_wt2_cost.py`, `ap_wt2_rep.py`, `ap_wt2_alt.py`, `ap_wt2_fam.py`, `ap_wt2_write.py`; outputs `outputs/autopilot/wt/WT2_*.csv`.

DONE WT2
