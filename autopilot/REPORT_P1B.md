# REPORT P1B - bracket-scaled re-run of the 5-minute NQ ensemble and the ES dip-buy lead, 2013-2026

**Verdict: NO (diagnostic, not a candidate). Scaling the bracket does not rescue the 5-minute ensemble on 2013-2022: standalone weekly Sharpe 2013-22 is -1.25 (a, real cost) / -0.19 (a, cost scaled with the bracket) / +0.26 (a, gross) vs +0.07 at the fixed 60-pt bracket; its additive uplift to the same-scaling pair on 2013-22 at 20% share is -0.27 / -0.04 / +0.06 (needs +0.10). The ES dip-buy lead has no price-level-dependent stop; it is scaling-invariant (2013-22 Sharpe 0.17-0.27, 42 trades; the edge is 2023+).** Scaling a (60 x raw price/20000) is the most faithful (see below).

Runtime: ensemble 5-worker pool, seconds (numba) + scoring ~2 min; ES < 1 min. Pre-registered in PREREG_AUTOPILOT.md (CYCLE 11) before the first run. Code: code/census/night_ins/ap_p1b_ens.py, ap_p1b_score.py, ap_p1b_es.py. Outputs: outputs/autopilot/p1b/{ENS_all.csv, ENS_tables.txt, ENS_uplift.csv, ES_all.csv, ES_tables.txt}.

## (i) 5-minute NQ ensemble
**Method.** The 5 primary members of C3-H3 (delta books replaced by their `none` twins; same signals via b10_gsig), 1-min NQ back-adjusted long series, same engine as C3-H3 with the stop = target = bracket taken per signal bar (fixed 60 / a / b / c exactly as in P1: a = 60 x raw price/20000 with raw = adj - later roll gaps; b = 0.2109 x ADR20; c = 10.57 x ATR120; rounded to 0.25, min 0.5). Size = R/(bracket x $20) contracts so every full stop = R = $12,000 (10 NQ at 60 pts, same as the live recipe); per-book 5R/-2R daily rule. **Fidelity: fixed/real reproduces the C3-H3 ensemble to 5e-17 (corr 1.0; 2013-22 Sharpe 0.068 = 0.068).**
Costs: real = 1 tick/side-equivalent (0.5 pt RT x $20) + $2.49/side per contract on the scaled number of contracts (cost in R rises as the bracket shrinks); scaled = cost x bracket/60 (constant cost in R); gross = 0. Clean-window member weekly std from the real-cost run of each scaling is used for the equal-risk ensemble (C3-H3 convention). Net $ below = average book at R = $12k; Sharpe = equal-risk ensemble.

Summary (weekly Sharpe of the ensemble; full per-year tables for all 12 combinations in ENS_tables.txt, ENS_all.csv):
| scaling | cost | 2013-22 | 2023-26 | clean | H1 | H2 | maxDD R 2013-22 | 2013-22 net R |
|---|---|---|---|---|---|---|---|---|
| fixed | real | +0.07 | 0.61 | 0.50 | 1.96 | 1.13 | 31.9 | +10.5 |
| fixed | gross | +0.45 | 1.07 | 0.96 | 2.30 | 1.71 | 27.5 | +62.2 |
| a | real | -1.25 | 0.41 | 0.74 | 0.89 | 0.37 | 252 | -240 |
| a | scaled | -0.19 | 0.42 | 0.78 | 0.82 | 0.23 | 78.6 | -35.5 |
| a | gross | +0.26 | 0.94 | 1.31 | 1.22 | 0.78 | 49.0 | +52.6 |
| b | real / scaled / gross | -1.66 / -0.45 / -0.00 | -0.17 / -0.21 / 0.19 | -0.42 / -0.44 / 0.05 | 1.80 / 1.75 / 1.97 | 0.23 / 0.05 / 0.34 | 345 / 133 / 90 | -323 / -87 / -0.5 |
| c | real / scaled / gross | -2.08 / -0.44 / +0.05 | -0.42 / -0.40 / 0.00 | -0.56 / -0.50 / -0.09 | 1.50 / 1.48 / 1.85 | -0.08 / -0.26 / 0.15 | 415 / 114 / 57 | -388 / -79 / +8.6 |

Per-year weekly Sharpe (real cost / cost scaled / gross), scaling a (faithful):
| | 2013 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 | 25 | 26 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| real | -2.00 | -1.71 | -2.35 | -3.05 | -0.48 | -2.07 | -1.26 | 0.61 | -0.08 | -0.54 | -1.71 | 0.57 | 0.75 | 1.08 |
| scaled | 0.35 | -0.07 | -0.62 | -1.48 | 0.44 | -1.10 | -0.50 | 1.23 | 0.10 | -0.20 | -1.43 | 0.60 | 0.71 | 0.95 |
| gross | 0.77 | 0.32 | -0.13 | -1.06 | 0.84 | -0.61 | -0.07 | 1.68 | 0.51 | 0.39 | -0.77 | 1.02 | 1.25 | 1.50 |
| net R (real) | -35.3 | -31.2 | -43.4 | -59.8 | -7.9 | -39.6 | -23.9 | 13.0 | -1.1 | -11.1 | -25.1 | 10.1 | 16.3 | 20.0 |
| trades/day (all 5 books) | 2.33 | 2.26 | 2.76 | 2.69 | 1.89 | 3.03 | 2.73 | 3.93 | 2.88 | 3.91 | 2.88 | 2.75 | 2.96 | 3.39 |
| median bracket (pts) | 9 | 11.5 | 13.3 | 13.5 | 17.5 | 20.8 | 23 | 30.5 | 42 | 37.3 | 44.3 | 57.3 | 65.5 | 86.5 |
Mean gross pts/trade in bracket units over 2013-22 is a +0.008, b -0.000, c +0.001, fixed +0.015 (ENS_all.csv column pts_bracket; it is cost-independent; clean +0.03); i.e. the per-trade gross expectancy is zero before 2023 and the loss under real costs is entirely the cost share of a 9-25-pt bracket. Fixed 60 (reference): per-year Sharpe -0.64 1.09 -0.64 0.01 0.00 0.66 -1.98 1.03 1.06 -0.83 -1.31 0.37 1.05 1.79 (identical to the C3-H3 table); b and c per-year rows in ENS_tables.txt are worse than a in every 2013-19 year under real cost and no better gross.

**Which scaling is faithful.** a (proportional to price): it is the only one that changes nothing but the unit of price (a 60-pt stop at 20,000 is 0.3%); it keeps trades/day stable (1.9-3.9) and the bracket path smooth (9 -> 86 pts). b/c tie the bracket to realised range, so the bracket shrinks in quiet years (7-13 pts 2013-16) and the exit mix changes (strategy no longer the same system), and they are worse in 2023-26 too (-0.17/-0.42 vs +0.41), i.e. they are not even the same strategy at the live end. The honest cost reading is the middle row (cost scaled with the bracket = same cost in R as the live era): under it nothing positive survives before 2023 (-0.19). Real costs at 9-25 pt brackets are a genuine feature of the market in 2013-19 (1 tick + commission is 3-10% of the bracket), not an artefact. **Conclusion: under every scaling and every cost mode the pre-2023 gross expectancy is ~0 (pts/bracket <= +0.015), as for the live pair in P1; the 5-min ensemble's apparent 2023+ edge is not a scaling artefact being revealed.**

### Additive uplift of the ensemble to the pair, 2013-2022, scaled brackets (against the same-scaling pair series in outputs/autopilot/p1/; share = fraction of the pair's clean weekly std, C3-H3 convention)
| scaling / cost | pair Sh 13-22 | ens Sh 13-22 | corr | up @10% | @20% | @30% | @50% | years >= +0.10 @20% |
|---|---|---|---|---|---|---|---|---|
| a / real | -1.38 | -1.26 | -0.07 | -0.147 | -0.272 | -0.373 | -0.502 | 1 |
| a / scaled | -0.38 | -0.19 | -0.10 | -0.024 | -0.042 | -0.055 | -0.065 | 2 |
| a / gross | +0.06 | +0.26 | -0.11 | +0.030 | +0.059 | +0.086 | +0.130 | 5 |
| b / real | -1.56 | -1.66 | -0.10 | -0.193 | -0.364 | -0.508 | -0.707 | 1 |
| b / scaled | -0.31 | -0.45 | -0.11 | -0.050 | -0.096 | -0.136 | -0.198 | 3 |
| b / gross | +0.05 | -0.00 | -0.11 | 0.000 | 0.000 | -0.001 | -0.004 | 5 |
| c / real | -2.04 | -2.08 | -0.11 | -0.208 | -0.397 | -0.563 | -0.816 | 1 |
| c / scaled | -0.79 | -0.44 | -0.17 | -0.048 | -0.090 | -0.125 | -0.173 | 2 |
| c / gross | -0.28 | +0.05 | -0.17 | 0.001 | 0.005 | 0.011 | 0.028 | 2 |
| fixed / real (live pair) | -0.78 | +0.07 | -0.19 | -0.005 | +0.001 | +0.015 | +0.068 | 4 |
Required: +0.10 on 2013-22 and >= 6 of 10 years at +0.10 (C3-H3 pre-stated reading). **Fails everywhere**; only the zero-cost fixed or a-gross cells approach it at 50% share (a gross +0.13 at 50%, 6/10 years) and zero cost is not tradable. Uplift in 2023-26 (clean/H1/H2/all, same scaling, a/real @20%): +0.17 / +0.11 / +0.13 / +0.09 - positive only in the recent era. Full table with by-year uplift: ENS_uplift.csv. (Insurance metric set for the live-era sleeve is in REPORT_C3_H3.md; unchanged by this diagnostic. Fill model: market at next 1-min open, stop-first, 1 tick/side + commission as above, executable at NTB/Rithmic as before; no new margin.)

## (ii) ES dip-buy lead (T4 B: RSI(2)<5 and close>SMA200 on 16:00-ET daily bars, exit after 5 days, stop 3 x ATR20)
**Price-level audit.** The signal (RSI, SMA200 compared with close), the stop (3 x ATR20 of the same daily bars = a volatility multiple, already level-free) and the exit (5 bars) are level-free. Only two things depend on the price level: (1) the size (1 ES contract is 3.7x more notional in 2026 than in 2013: ES 1,440 -> 6,900) and (2) the cost share (fixed $ tick+commission vs a stop of 3 x ATR: ~$2,200 in 2013 vs ~$9,000 now, i.e. cost in R is ~4x larger in 2013). No bracket re-scaling exists to apply. Scalings tested: fixed = 1 contract; a = constant notional (contracts = 5,496/raw price); b = constant dollar risk ($9,600 per full stop, ATR-based). Cost modes real / scaled (x ATR/clean-median ATR) / gross. Warm-up: ES long series starts 2013-01-02 so the first signals are in 2013-10 (SMA200 + RSI).
Result (lead cell, 67 trades 2013-2026, 42 in 2013-22): weekly Sharpe real cost 2013-22 = 0.17 (fixed) / 0.18 (a) / 0.24 (b); 2023-26 = 1.88 / 1.83 / 1.90; clean 1.81 / 1.83 / 1.88; H1 3.72 / 3.71 / 3.77; H2 1.21 / 1.16 / 1.17. Net R 2013-22 +3.5 R (maxDD 4.3 R), 2023-26 +11.1 R (maxDD 0.72 R). Cost mode barely matters (ES cost ~0.01-0.05 R per trade; gross vs real net R 3.85 vs 3.51 in 2013-22). Expectancy 0.08 R/trade 2013-22 vs 0.44 R/trade 2023-26; pts in bracket units 0.09 vs 0.45; trades/day 0.02-0.03 every era (no drift). Per-year Sharpe (fixed, real): 2013 0.78(1 trade) 14 -1.48 15 2.03 16 0.82 17 1.79 18 -0.80 19 -0.83 20 0.35 21 1.48 22 -1.09 23 0.05 24 2.88 25 1.51 26 2.03; 6 of the 10 years 2013-22 positive (5 excluding the 1-trade 2013) but the 2013-22 aggregate is thin (0.17; bootstrap on 42 trades will be wide). Siblings (context, not selected): stop2 2013-22 Sharpe 0.34-0.49 (45 trades), rsi10 0.37-0.38 (76 trades).
**Reading.** Scaling is not the issue; the lead is faithful at all three sizings and its pre-2023 history is weakly positive (+3.5 R over 10 years, expectancy 5x lower than 2023+), consistent with a real but small mean-reversion edge that has been much stronger since 2023 - small-sample (<100 trades in any pair window; 67 over 13 years) and still LEAD-status only (circular-shift and worst-decile gates unchanged from REPORT_T4_B.md). Per-year table incl. net R, $, maxDD R, trades/day for all 9 scaling x cost combinations: ES_tables.txt.

Executability: both are NT8-codable as before (5-min ensemble per C3-H3; ES daily at NTB/Rithmic, margin ES ~$13k). Nothing here changes a candidate verdict.
DONE P1B
