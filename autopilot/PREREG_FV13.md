# PREREG FV13 - IMP3 replication line on untested markets (written before any run)

Date 2026-10-17. Worker: ICT/FV. Code prefix ap_fv_g13*.py. Up to 8 processes.

## Question
Does the IMP3 limit-retrace mechanism (limit at 50% of a 3-bar impulse, depth matters) replicate on markets not yet tested, or is NQ/GC/ES a coincidence?

## Markets (15, 1-min bars from data/autopilot/ohlcv1m and data/t4 crypto, difference back-adjusted by ap_i_load)
YM, 6E, 6J, 6B, ZN, ZB, SI, HG, PL, NG, RB, HO, ZC, BTC, ETH. HG and PL added to the tick/value table at runtime (HG 0.0005 x $25,000; PL 0.1 x $50); nothing purchased.

## Cells (3 per market, 45 total = family size N for the replication line)
A. IMP3 tf3 m1.5 (primary; thr 1.5 ATR)   B. IMP3 tf3 m1.125 (S2 sibling)   C. P1 = FVG tf5 thr 0.25 at CE (2R).
All parameters exactly as for NQ (3 bars, 50% entry, stop beyond bar-1 extreme +0.05 ATR, floor max(0.75 ATR, 30 ticks), cap 4 ATR, 2R target, 20-bar life, hold 360 min, flat 16:55 ET, fill 1 tick through, stop slip 1 tick, $4.36/contract commission). Nothing is tuned per market. Statistic in R units (net of costs), one position at a time per market (existing RU simulator ap_ru_sim.run_S).

## Selection span / reads
Clean 2023-08-01..2025-07-31 only for every decision. Pre-2023 (2013-2022) used only as the ERA flag (net R/trade at fixed cost per year). H1 2025-08-01..2026-02-06 and H2 2026-02-07..2026-10-13 are read once, only for cells that pass the clean depth gate. UNTOUCHED never.

## Roll rule (per instrument)
Roll days = days where the instrument id of the continuous series changes. No placements whose label day is within +-3 trading days of a roll (same rule as NQ).

## Nulls (200 worlds per market, selection-aware)
Null A: depth permutation (entry depth below signal close and stop distance permuted jointly across the market's setups) - the ICT null. Null B: entry fraction redrawn U(0.25,0.75) with original stop (RV1 null). Statistic per world = best clean weekly Sharpe over the market's 3 cells (selection-aware, N=3 per market). "Depth matters" for a market iff best real clean Sharpe (3-cell max) exceeds the p95 of BOTH nulls AND the real cell's clean net R/trade > 0. Per-cell results reported too (cell flag: real > p95 of per-cell null A and B).
Also reported: net R/trade clean, all-sample, at 2x slippage; ERA flag = sign of net R/trade in 2013-2022 (positive/negative, and years positive of 10).

## Count and binomial
k = number of the 15 markets with depth matters. Under "depth never matters" each market passes with prob <= 0.05 (p95 threshold), so P(X>=k) = binomial(15, 0.05). Also reported on all 20 markets tested for the IMP3 mechanism (adding NQ, GC, ES, RTY, CL from RU1), and with the known-selected markets (NQ, GC) removed. Honest reading of cross-market mechanism versus coincidence is stated whichever way it falls; gates are not softened.

## Item 3 gate
A market with depth matters AND clean net R/trade >= 0.05 (also positive at 2x slippage) is eligible for tick replay only if trades are on disk (verified: data/databento/{NQ,ES,GC,CL,RTY,ZN}/trades only; of the 15 only ZN). Otherwise stated as gated by data; no purchases.

## Insurance reporting
For any passing market: R-sized sleeve (R=$9,600 per full stop) dollar figures per market (worst trade/day/week, max DD, at unit and 20% share), plus the NQ IMP3 figures carried from FV12. Constant-risk framing. No uplift-on-pair claim is made for non-NQ instruments (not tradable in the pair account); sleeve-alone metrics only.

## AMENDMENT A1 (before any market result was read; made after a ZN feasibility run showed 10-20 clean trades)
The RU simulator's default 30-tick stop floor (mint=30) makes the 4-ATR stop cap infeasible where ATR is a few ticks (ZN: 10/13/20 clean trades, nothing to test). The NQ spec (LIVE_SPEC) has NO tick floor, only the 0.75 ATR floor. Primary FV13 cells therefore use mint=0 (exact IMP3 spec: floor 0.75 ATR, cap 4 ATR). Costs stay 1 tick stop slip + $4.36/contract, so small-stop markets pay a large cost in R and may show negative net R; that is the honest result. ZN mint=30 trade counts (10/13/20) are disclosed; no other variant is run.
