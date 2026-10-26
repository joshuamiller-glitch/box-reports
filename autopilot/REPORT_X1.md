# REPORT X1

> **UPDATE 2026-10-16: compression-breakout results (X1, Y6, B2-D) are NOT CONFIRMED under path-resolved 30-min execution (REPORT_Z1.md); the daily-bar fill model resolved 52% of triggers (both-touch days) incorrectly. Lead withdrawn.**

**LEAD (not FOUND) - X1 cost-screened compression breakout, 1-day hold, ATR stop 2-3, 16 screened markets: standalone Sharpe 2013-22 1.35 (10 of 10 years positive), pair window 1.33 (clean 0.67 / H1 1.17 / H2 3.35), own random-entry null rank 1.00 in both; additive uplift at 20% share +0.12/+0.23/+0.37 on clean/H1/H2 (all-in +0.20), bootstrap 90% lo +0.02, worst-decile corr -0.14, plateau 0.75. Fails: G3 at 10% share (clean +0.07), worst week not within the share (+13% at 10%, +32% at 20%), bootstrap lo < 0 at 50% share, 2x slippage (clean uplift +0.04); excluded-market replication weak (pair-window Sharpe -0.08). FOUND 0. 8 cells, ~1 min (7 workers).**


## Protocol
Pre-registered (PREREG_AUTOPILOT.md, "B2356 FOLLOW-ON X1-X5", 2026-10-16T14:21Z, rule text frozen before any X run; ideas logged in RESEARCH_LOG.md with priors). Same engine, selection (2013-2022 only: >= 300 trades, >= 7 of 10 positive years, top 3), scaling (2013-22 weekly vol -> pair clean weekly vol), nulls, bootstrap, plateau, 2x slippage, baseline B.Cfg(wk_floor=8, wk_loss_pb=None) (clean 1.46 / H1 2.83 / H2 2.30) as B2/B6. Idea X1: union setup (NR7 OR inside day OR range-pctile <= 10%) x hold {1,2} x ATR stop {2,3} x market set {SCREENED (16 markets with 2 ticks + commission <= 3% of median 2013-22 ATR20: ES NQ RTY YM GC SI HG PL CL NG RB HO 6E 6J 6B 6A), ALL26} = 8 cells; neighbours: hold/stop x0.75/1.25 and screen threshold 0.0225/0.0375.

Fill model: stop-entry orders fill at the trigger level (at the bar open on a gap), market entries at the bar open, time exits at the bar close (daily) / the open of the last 30-min bar of the label day (intraday), stop exits at the stop price (gap-through at the open), stop tested first on the entry bar; one position at a time per instrument per cell; slippage 1 tick per side plus commission (T4 A table per product for daily, $4.36 per contract round trip intraday), 2x slippage = 2 ticks per side; one extra round trip for a roll inside a trade. Back-adjusted continuous prices (volume-front). No queue model.

Gate checklist legend: G1 pre-registered (PREREG_AUTOPILOT.md, CAPACITY BACKLOG B2/B3/B5/B6, 2026-10-16T14:06Z, before any run); G2 selection on 2013-2022 only (strictly before clean), clean/H1/H2 read once after selection; G3 additive Sharpe uplift >= +0.10 on clean, H1 and H2 separately with worst week within the share, at 10/20/30/50%; G4 own random-entry null p95 on standalone pair-window Sharpe and bootstrap 90% lo > 0; G5 plateau (+-25%) and 2x slippage (uplift still >= +0.10 on clean/H1/H2 at 20%); G6 worst-decile-week correlation <= +0.30; G7 executable spec.

## Development (2013-2022) - all 8 cells
| cell           |   trades_2013_22 |   sh_2013_22 |   yrs_pos |
|:---------------|-----------------:|-------------:|----------:|
| X1_h1_k2_SCR   |            10053 |         1.35 |        10 |
| X1_h1_k3_SCR   |            10053 |         1.33 |        10 |
| X1_h1_k2_ALL26 |            16281 |         1.18 |        10 |
| X1_h1_k3_ALL26 |            16281 |         1.17 |        10 |
| X1_h2_k3_SCR   |             9794 |         1.11 |         9 |
| X1_h2_k2_SCR   |             9794 |         1.1  |         9 |
| X1_h2_k3_ALL26 |            15635 |         0.78 |         8 |
| X1_h2_k2_ALL26 |            15635 |         0.78 |         9 |

Multiplicity: 8 cells x 5% = 0.4 expected chance passes. All 8 cells are eligible; the 1-day cells dominate (hold 2 is weaker); the screened sets beat ALL26 in 2013-22 and in the pair window (as the cost rationale predicts).

### Standalone and own random-entry null (203 draws)
| cell | Sh 2013-22 | yrs>0 /10 | clean | H1 | H2 | pair win | 2013-26 | null p95 (pair win) | rank | null p95 (2013-22) | rank |
|---|---|---|---|---|---|---|---|---|---|---|---|
| X1_h1_k2_SCR | 1.35 | 10 | 0.67 | 1.17 | 3.35 | 1.33 | 1.25 | 0.08 | 1.00 | -0.43 | 1.00 |
| X1_h1_k3_SCR | 1.33 | 10 | 0.72 | 1.15 | 3.39 | 1.36 | 1.25 | 0.37 | 1.00 | -0.41 | 1.00 |
| X1_h1_k2_ALL26 | 1.18 | 10 | 0.63 | -0.45 | 2.71 | 1.01 | 1.09 | -0.69 | 1.00 | -1.72 | 1.00 |

### Additive framing (pair unchanged, sleeve at 10/20/30/50% of pair risk)
| cell | k | share | dSh clean | H1 | H2 | all-in | ww chg % | boot 90% lo | shift-null rank | wd corr | corr all | verdict(T3) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X1_h1_k2_SCR | 2.2 | 10% | 0.07 | 0.14 | 0.20 | 0.11 | 13 | 0.02 | 0.32 | -0.14 | 0.03 | NO |
| X1_h1_k2_SCR | 2.2 | 20% | 0.12 | 0.23 | 0.37 | 0.20 | 32 | 0.02 | 0.32 | -0.14 | 0.03 | NO |
| X1_h1_k2_SCR | 2.2 | 30% | 0.16 | 0.29 | 0.52 | 0.27 | 51 | 0.01 | 0.32 | -0.14 | 0.03 | NO |
| X1_h1_k2_SCR | 2.2 | 50% | 0.20 | 0.31 | 0.74 | 0.36 | 89 | -0.06 | 0.32 | -0.14 | 0.03 | NO |
| X1_h1_k3_SCR | 2.2 | 10% | 0.07 | 0.13 | 0.20 | 0.11 | 13 | 0.02 | 0.34 | -0.14 | 0.03 | NO |
| X1_h1_k3_SCR | 2.2 | 20% | 0.13 | 0.23 | 0.37 | 0.21 | 33 | 0.03 | 0.34 | -0.14 | 0.03 | NO |
| X1_h1_k3_SCR | 2.2 | 30% | 0.18 | 0.28 | 0.52 | 0.28 | 53 | 0.02 | 0.34 | -0.14 | 0.03 | NO |
| X1_h1_k3_SCR | 2.2 | 50% | 0.22 | 0.30 | 0.74 | 0.38 | 93 | -0.04 | 0.34 | -0.14 | 0.03 | NO |
| X1_h1_k2_ALL26 | 1.7 | 10% | 0.05 | -0.02 | 0.17 | 0.07 | 8 | -0.02 | 0.13 | -0.05 | 0.10 | NO |
| X1_h1_k2_ALL26 | 1.7 | 20% | 0.09 | -0.08 | 0.31 | 0.12 | 22 | -0.05 | 0.13 | -0.05 | 0.10 | NO |
| X1_h1_k2_ALL26 | 1.7 | 30% | 0.11 | -0.15 | 0.42 | 0.15 | 36 | -0.09 | 0.13 | -0.05 | 0.10 | NO |
| X1_h1_k2_ALL26 | 1.7 | 50% | 0.12 | -0.36 | 0.56 | 0.17 | 65 | -0.20 | 0.13 | -0.05 | 0.10 | NO |

### Constant-risk framing
| cell | share | all net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar impr | H1 ww/cvar impr | verdict |
|---|---|---|---|---|---|---|---|---|
| X1_h1_k2_SCR | 10% | -3.2 | -3.3 | 4.6 | 9.1 | -4/4 | -6/4 | NO |
| X1_h1_k2_SCR | 20% | -6.4 | -12.9 | 7.5 | 18.1 | -14/7 | -12/8 | NO |
| X1_h1_k2_SCR | 30% | -9.5 | -22.5 | 9.9 | 14.3 | -23/9 | -18/12 | NO |
| X1_h1_k2_SCR | 50% | -15.9 | -41.8 | 7.6 | -5.9 | -43/5 | -30/17 | NO |
| X1_h1_k3_SCR | 10% | -3.1 | -4.1 | 4.5 | 9.1 | -5/4 | -6/4 | NO |
| X1_h1_k3_SCR | 20% | -6.1 | -14.5 | 7.5 | 18.2 | -15/7 | -12/8 | NO |
| X1_h1_k3_SCR | 30% | -9.2 | -25.0 | 9.8 | 18.7 | -26/9 | -18/12 | NO |
| X1_h1_k3_SCR | 50% | -15.3 | -45.9 | 8.0 | 1.4 | -47/6 | -30/18 | NO |
| X1_h1_k2_ALL26 | 10% | -4.8 | 1.6 | 5.7 | 7.9 | 1/4 | 3/9 | NO |
| X1_h1_k2_ALL26 | 20% | -9.6 | -3.3 | 10.0 | 15.8 | -4/7 | 5/19 | NO |
| X1_h1_k2_ALL26 | 30% | -14.3 | -8.1 | 12.7 | 21.1 | -9/9 | 8/28 | NO |
| X1_h1_k2_ALL26 | 50% | -23.9 | -17.8 | 13.8 | 24.3 | -19/9 | 13/33 | NO |

### Plateau, 2x slippage, alternate baseline B.Cfg()
| cell | base all-in uplift @20% | neighbours | share keeping >=75% | min / median neighbour all-in | 2x slip uplift clean/H1/H2/all | 2x slip standalone pair-win Sh | alt-baseline B.Cfg() uplift clean/H1/H2/all |
|---|---|---|---|---|---|---|---|
| X1_h1_k2_SCR | 0.20 | 4 | 0.75 | 0.11 / 0.19 | 0.04 / 0.15 / 0.31 / 0.13 | 0.91 | 0.13 / 0.21 / 0.37 / 0.21 |
| X1_h1_k3_SCR | 0.21 | 4 | 0.75 | 0.11 / 0.20 | 0.05 / 0.14 / 0.31 / 0.13 | 0.94 | 0.14 / 0.20 / 0.37 / 0.21 |
| X1_h1_k2_ALL26 | 0.12 | 2 | 1.00 | 0.10 / 0.11 | -0.11 / -0.37 / 0.15 / -0.08 | -0.08 | 0.09 / -0.05 / 0.30 / 0.13 |

### Gates
| cell | G3 add >=+0.10 clean,H1,H2 & worst week, at 10/20/30/50% | G4 own-null p95 | G4 bootstrap lo>0 (all shares) | G5 plateau | G5 2x slip | G6 wd corr<=0.30 | verdict |
|---|---|---|---|---|---|---|---|
| X1_h1_k2_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | PASS (0.75) | fail | PASS (-0.14) | NO |
| X1_h1_k3_SCR | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | PASS (0.75) | fail | PASS (-0.14) | NO |
| X1_h1_k2_ALL26 | 10%:fail, 20%:fail, 30%:fail, 50%:fail | PASS | fail | PASS (1.00) | fail | PASS (-0.05) | NO |

Insurance metric set (sleeve scaled to the pair's clean weekly volatility; combined book = pair + 30% sleeve in the additive framing; pair alone for reference; $ on $700k):

| cell | span | sleeve (scaled) Sh | net $ | worst wk $ | CVaR5 $ | CVaR10 $ | maxDD $ | Sortino | MAR | %neg wk | pair+30% add: Sh | worst wk | CVaR5 | maxDD | MAR | %neg wk | pair alone: Sh | worst wk | CVaR5 | maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X1_h1_k2_SCR | clean | 0.67 | 573,185 | -156,776 | -120,506 | -97,757 | 598,389 | 1.04 | 0.96 | 51 | 1.62 | -124,291 | -94,279 | 288,051 | 5.21 | 43 | 1.46 | -81,874 | -78,736 | 280,110 |
| X1_h1_k2_SCR | H1 | 1.17 | 273,188 | -125,562 | -119,755 | -114,428 | 271,573 | 1.72 | 1.01 | 29 | 3.12 | -115,956 | -91,261 | 170,968 | 3.95 | 32 | 2.83 | -78,287 | -77,610 | 151,713 |
| X1_h1_k2_SCR | H2 | 3.35 | 985,273 | -82,781 | -71,827 | -56,471 | 165,741 | 9.21 | 5.94 | 35 | 2.78 | -84,196 | -83,080 | 229,384 | 4.61 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| X1_h1_k2_SCR | all | 1.33 | 1,831,646 | -156,776 | -118,480 | -95,906 | 598,389 | 2.21 | 3.06 | 43 | 2.13 | -124,291 | -94,474 | 288,051 | 11.23 | 40 | 1.86 | -82,524 | -79,220 | 280,110 |
| X1_h1_k3_SCR | clean | 0.72 | 614,185 | -163,545 | -120,452 | -100,030 | 547,218 | 1.11 | 1.12 | 51 | 1.64 | -126,322 | -94,392 | 287,654 | 5.26 | 42 | 1.46 | -81,874 | -78,736 | 280,110 |
| X1_h1_k3_SCR | H1 | 1.15 | 264,572 | -124,897 | -113,932 | -110,066 | 269,771 | 1.71 | 0.98 | 29 | 3.11 | -115,756 | -91,201 | 170,692 | 3.94 | 32 | 2.83 | -78,287 | -77,610 | 151,713 |
| X1_h1_k3_SCR | H2 | 3.39 | 984,093 | -75,647 | -68,023 | -54,409 | 157,962 | 9.59 | 6.23 | 35 | 2.78 | -84,143 | -83,056 | 229,291 | 4.61 | 38 | 2.26 | -82,524 | -81,089 | 217,425 |
| X1_h1_k3_SCR | all | 1.36 | 1,862,851 | -163,545 | -116,990 | -96,128 | 547,218 | 2.27 | 3.40 | 43 | 2.14 | -126,322 | -94,512 | 287,654 | 11.28 | 39 | 1.86 | -82,524 | -79,220 | 280,110 |
| X1_h1_k2_ALL26 | clean | 0.63 | 515,942 | -133,864 | -111,954 | -95,417 | 445,137 | 0.96 | 1.16 | 49 | 1.57 | -112,389 | -94,000 | 297,865 | 4.98 | 44 | 1.46 | -81,874 | -78,736 | 280,110 |
| X1_h1_k2_ALL26 | H1 | -0.45 | -91,564 | -137,511 | -119,480 | -102,526 | 403,068 | -0.59 | -0.23 | 43 | 2.68 | -95,656 | -79,109 | 173,544 | 3.26 | 39 | 2.83 | -78,287 | -77,610 | 151,713 |
| X1_h1_k2_ALL26 | H2 | 2.71 | 976,615 | -77,124 | -75,454 | -65,205 | 302,372 | 7.34 | 3.23 | 41 | 2.68 | -83,614 | -78,514 | 234,830 | 4.49 | 41 | 2.26 | -82,524 | -81,089 | 217,425 |
| X1_h1_k2_ALL26 | all | 1.01 | 1,400,993 | -137,511 | -111,648 | -92,209 | 445,137 | 1.70 | 3.15 | 45 | 2.01 | -112,389 | -91,713 | 297,865 | 10.43 | 42 | 1.86 | -82,524 | -79,220 | 280,110 |


## Diagnostics (reported, not gated; appended to the pre-registration before they were computed)
Per-calendar-year weekly Sharpe of X1_h1_k2_SCR, 2013-2026 (2026 to 2026-10-14; 2023 is partly clean):

| 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1.29 | 2.13 | 0.54 | 0.59 | 1.06 | 0.74 | 2.04 | 2.09 | 1.29 | 1.41 | -0.62 | 0.12 | 1.81 | 2.79 |

Per-market (X1_h1_k2_SCR, 1-day): 

| market   |   net_2013_22 |   net_pairwin |   sh_2013_22 |   sh_pairwin |   cost_ratio |   share_pairwin |
|:---------|--------------:|--------------:|-------------:|-------------:|-------------:|----------------:|
| ES       |      211010   |      87318.2  |         0.54 |         0.72 |         0.02 |            0.1  |
| NQ       |      345603   |     109161    |         0.92 |         0.91 |         0.01 |            0.13 |
| RTY      |      148296   |     -15568.4  |         0.52 |        -0.17 |         0.01 |           -0.02 |
| YM       |       58992.6 |      55768.9  |         0.16 |         0.49 |         0.01 |            0.07 |
| GC       |      199854   |     104504    |         0.49 |         0.75 |         0.02 |            0.12 |
| SI       |      308502   |     180096    |         0.76 |         1.44 |         0.03 |            0.21 |
| HG       |     -104216   |     154291    |        -0.3  |         1.2  |         0.02 |            0.18 |
| PL       |      300699   |      -5916.47 |         0.81 |        -0.04 |         0.02 |           -0.01 |
| CL       |       92442.2 |       4617.75 |         0.25 |         0.04 |         0.02 |            0.01 |
| NG       |       98096.5 |      19329.9  |         0.28 |         0.18 |         0.03 |            0.02 |
| RB       |      374413   |     -10921.3  |         1.02 |        -0.11 |         0.01 |           -0.01 |
| HO       |      224079   |     103947    |         0.58 |         0.96 |         0.01 |            0.12 |
| 6E       |       40797.4 |      39026.8  |         0.11 |         0.34 |         0.02 |            0.05 |
| 6J       |      340798   |      54155.6  |         0.89 |         0.46 |         0.02 |            0.06 |
| 6B       |       27197.6 |     -24329.6  |         0.08 |        -0.21 |         0.03 |           -0.03 |
| 6A       |      134135   |     -16030.3  |         0.38 |        -0.15 |         0.02 |           -0.02 |

Pair-window P&L share is spread across ES, NQ, GC, SI, HG, HO (10-21% each); RTY, PL, RB, 6B, 6A are small negatives. 2013-22 and the pair window rank the markets differently (RB 1.02 -> -0.11, HG -0.30 -> 1.20): the portfolio edge is the common breakout effect, not a few markets.

Second-instrument-set replication (the same frozen cell on the 10 markets EXCLUDED by the ex-ante screen: ZN ZB ZF ZT 6C ZC ZS ZW LE HE): Sharpe 2013-22 0.21, clean 0.15, H1 -2.44, H2 1.14, pair window -0.08, 2013-26 0.20. The effect does not replicate on rates/grains/livestock (costlier relative to ATR, different microstructure): the lead is specific to the 16 liquid index/metal/energy/FX markets. That limits how much weight the 16-market result can bear and is the main reason this stays a LEAD.

## Verdict and reading
- FOUND 0; LEAD. The strongest candidate of the B2356 worker's batch: a diversified 1-day compression-breakout book that passes the own-null (G4a), plateau (0.75), worst-decile correlation (-0.14) and has additive uplift of +0.12-0.20 (clean), +0.23-0.31 (H1), +0.37-0.74 (H2) at 20-50% share with bootstrap lo +0.01..+0.03 at 20-30%.
- Gates not met: (G3) at 10% share clean uplift is +0.07 and the worst week is worse by more than the share (13% > 10%, 32% > 20%) because the sleeve's own worst week is 1.3x the pair's; (G4b) bootstrap lo is < 0 at 50% share; (G5) 2x slippage: uplift +0.04/+0.15/+0.31 (clean/H1/H2) < +0.10 on clean, standalone pair-window Sharpe still 0.91; constant-risk framing: net cost 3-16%, worst week 3-46% worse: not INSURANCE. 2023 was a losing year (-0.62), the clean uplift depends on late-2024/2025.
- Not tuned after the read. To become FOUND it needs: a smaller gross-to-cost sensitivity (e.g. a pre-registered limit-order/entry-improvement variant), or an independent window (2026-10 onward) to replicate; both need new pre-registered work. Rolling data extension (weekly) will re-score it automatically if added to the list.

## Executability (G7)
Spec: after the daily close (CME 17:00 ET session close; this study used UTC-day bars, i.e. 19/20:00 ET boundaries - NT8 daily bars with a custom session template or a 1440-minute series anchored at 20:00 ET must be used and the backtest re-checked), flag the day if (range < min of previous 6 ranges) OR (inside day) OR (range <= 2nd smallest of the last 20); for each flagged market in {ES NQ RTY YM GC SI HG PL CL NG RB HO 6E 6J 6B 6A} (micros for MES/MNQ/M2K/MYM/MGC/SIL/MCL/M6E... for granular size) place an OCO buy-stop at the flagged day's high and sell-stop at its low for the next session, ATR(20) stop 2-3 ATR from the fill, market-on-close exit at the end of that session (1 day), one position per market. Sizing $7,000 per ATR20 per trade times k=2.2 at 100% of pair vol; at 20% share ~3.1k$ ATR-risk per trade, roughly 3 trades/day across 16 markets. Margin at 20% share is small (a handful of outright contracts per market or micros). Needs a new multi-instrument daily NT8 strategy (not DualStrat); fill risk: stop orders on thin overnight books for HG/PL/NG/6B/6A and the CME holiday sessions.


DONE X1
