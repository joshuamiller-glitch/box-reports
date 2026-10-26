# REPORT C7-P1 — LONG-HISTORY-SELECTED INTRADAY FAMILIES ON ZN, ZB, 6E, 6J, GC, CL

**Verdict: NO. 0 FOUND, 0 LEAD.** Of the 31 cells that passed the 2013-2022 selection rule (not the 60 hoped for: the 7-of-10-years rule leaves 0 / 3 / 6 / 10 / 2 / 10 cells on ZN / ZB / 6E / 6J / GC / CL), **none reaches +0.10 Sharpe uplift on clean, H1 and H2 together at any share**; 0 of 31 pass the amended gate at 10, 20, 30 or 50%. The standalone pair-window Sharpe is negative for 21 of 31 cells (median -0.21). ZB, 6E and 6J show a year-consistent structure in 2013-2022 that is more than chance (below), but it does not exist in 2023-2026.

## What was run
- **Pre-registered** in `PREREG_AUTOPILOT.md` ('CYCLE 7' and 'C7-P1 exact grid', appended before the first full run).
- **Data:** purchased 1-minute continuous front (.v.0) bars 2013-01..2026-10 for the six instruments (data/autopilot/ohlcv1m), difference back-adjustment at instrument_id changes, ET DST clock, label day = ET+6h, flat at the 16:55 ET bar open. CL events on 2020-04-17..04-23 invalidated (negative-price episode); the CL series itself contains the negative prints and the adjusted history is therefore shifted by that episode's roll gap (flagged).
- **Grid:** 1,120 cells per instrument (6,720 total): 2 timeframes x 20 rules (EMA x3, MACD x3, Supertrend x3, Donchian x3, linreg x3, RSI MR x3, VWAP-distance MR x2) x 7 exits (opposite; bracket k x 0.193 x prior-20-day mean range with k = 2/3, 1, 3/2; time stops 60/120/240) x 2 sessions x EMA200 off/on.
- **Costs / fills (state of the model):** slippage ticks/side ZN 0.5, ZB 0.5, 6E 0.5, 6J 0.5, GC 1, CL 1; commission $4.36 per contract round trip (assumption); entry at the next bar open, stop-first, targets without slippage, 1 contract unit then scaled. Contract constants (tick, $/point): ZN 1/64, 1000; ZB 1/32, 1000; 6E 0.00005, 125000; 6J 0.0000005, 12.5M; GC 0.10, 100; CL 0.01, 1000. Point value and slippage are passed to the simulator as arguments (the C5-M1 numba-globals bug does not recur; verified by the 2x-slippage run changing the numbers).
- **Selection (2013-2022 only):** >= 300 trades, positive weekly Sharpe in >= 7 of the 10 calendar years, ranked by 2013-2022 weekly Sharpe, top 10 per instrument. Sleeve P&L scaled so its 2013-2022 weekly volatility equals the pair's clean weekly volatility.
- **Pair:** `B.Cfg(wk_floor=8, wk_loss_pb=None)` computed in a clean process (t3_score). Uplift = change in weekly Sharpe of pair + 20% x sleeve.

## False-survivor test (timing-destroyed replicates)
50 replicates per instrument on a fixed random third of the grid (373 of 1,120 cells; counts scaled x3): random bar ends, alternating sides, same event count, identical selection.

| inst | real cells passing 7-of-10 | replicate mean passing (scaled; max) | p (rep >= real) | real top-10 mean Sharpe | replicate top-10 mean | best real / replicate-mean best | p (best) |
|---|---|---|---|---|---|---|---|
| ZN | 0 | 0.0 (max 0) | n/a | n/a | n/a | n/a | n/a |
| ZB | 3 | 0.1 (max 3) | 0.02 | 0.19 | 0.03 | 0.31 / 0.03 | 0.00 |
| 6E | 6 | 2.2 (max 12) | 0.08 | 0.20 | 0.17 | 0.53 / 0.18 | 0.04 |
| 6J | 11 | 1.3 (max 6) | 0.00 | 0.39 | 0.20 | 0.62 / 0.23 | 0.00 |
| GC | 2 | 2.3 (max 9) | 0.54 | 0.36 | 0.22 | 0.40 / 0.26 | 0.10 |
| CL | 16 | 8.0 (max 18) | 0.02 | 0.35 | 0.23 | 0.54 / 0.39 | 0.20 |

Reading: 6J (11 cells vs 1.3 expected, p=0.00), ZB (3 vs 0.06, p=0.02) and CL (16 vs 8, p=0.02) have more year-consistent cells than timing-destroyed grids; 6E and GC do not. The cells are mean-reversion (RSI(14,30), VWAP z=3) on the 15-minute bars with the EMA200 filter, which is the same family in every instrument. These are in-sample selection results; the point of this test is the next section.

## The 31 selected cells read in the pair window (clean 2023-08..2025-07, H1, H2 read once)
Columns: weekly Sharpe 2013-22 (selection span); standalone weekly Sharpe clean/H1/H2; additive uplift in weekly Sharpe at 20% share (clean/H1/H2); worst-decile correlation with the pair; rank of the pair-window standalone Sharpe against 100 random-entry (timing-destroyed) draws; bootstrap 5th percentile of the all-in uplift; plateau share (+-25% neighbours keeping 75% of the all-in uplift); 2x slippage; amended gate.

| inst | # | cell | yrs>0 of 10 | Sharpe 2013-22 | clean | H1 | H2 | trades pair win | up20 clean | up20 H1 | up20 H2 | wd corr | own-null rank (pair win) | boot lo | plateau | 2x slip: standalone / up20 c,H1,H2 | amended gate @20% |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6E | 1 | 15m rsi[14, 30] exit=time120 all ema200 | 7 | 0.53 | 0.54 | -0.13 | 1.24 | 137 | +0.09 | -0.14 | +0.09 | -0.47 | 1.00 | -0.06 | 0.33 | 0.30 / +0.05,-0.17,+0.06 | NO |
| 6E | 2 | 15m vw[3] exit=brk2/3 all ema200 | 7 | 0.28 | 0.62 | 0.12 | 0.74 | 175 | +0.06 | -0.01 | +0.01 | -0.18 | 1.00 | -0.14 | 0.75 | 0.29 / +0.00,-0.07,-0.04 | NO |
| 6E | 3 | 15m rsi[14, 30] exit=time240 day | 7 | 0.12 | 0.64 | -1.03 | 0.57 | 572 | +0.11 | -0.20 | +0.07 | +0.41 | 0.97 | -0.07 | 0.50 | 0.10 / +0.07,-0.24,+0.03 | NO |
| 6E | 4 | 5m rsi[14, 30] exit=time240 all | 7 | 0.11 | -0.95 | 0.94 | -1.44 | 2493 | -0.21 | +0.17 | -0.13 | +0.28 | 0.79 | -0.32 | 0.00 | -1.44 / -0.32,+0.04,-0.25 | NO |
| 6E | 5 | 15m rsi[5, 20] exit=time60 day ema200 | 7 | 0.10 | -0.10 | -1.15 | 0.23 | 274 | -0.03 | -0.34 | -0.01 | -0.01 | 0.96 | -0.20 | 0.00 | -0.71 / -0.09,-0.41,-0.07 | NO |
| 6E | 6 | 5m macd[19, 39] exit=time120 day ema200 | 7 | 0.07 | -0.27 | 0.91 | -0.17 | 867 | -0.04 | +0.09 | -0.02 | +0.11 | 0.95 | -0.15 | 0.00 | -0.56 / -0.11,+0.01,-0.09 | NO |
| 6J | 1 | 15m vw[3] exit=brk1.5 all ema200 | 7 | 0.62 | 0.25 | -1.10 | 1.20 | 136 | -0.01 | -0.05 | +0.14 | +0.15 | 0.98 | -0.16 | 0.00 | 0.13 / -0.04,-0.08,+0.12 | NO |
| 6J | 2 | 15m don[50] exit=time60 day ema200 | 7 | 0.53 | -0.54 | -0.86 | -0.69 | 190 | -0.13 | -0.31 | -0.04 | -0.21 | 0.41 | -0.27 | 0.00 | -0.91 / -0.18,-0.35,-0.08 | NO |
| 6J | 3 | 15m vw[3] exit=time240 all ema200 | 8 | 0.51 | -0.26 | -0.90 | 2.38 | 151 | -0.15 | -0.38 | +0.26 | +0.32 | 0.80 | -0.39 | 0.00 | -0.27 / -0.20,-0.42,+0.24 | NO |
| 6J | 4 | 15m vw[3] exit=time120 all ema200 | 7 | 0.50 | 0.01 | -0.75 | 1.01 | 173 | -0.08 | -0.37 | +0.11 | +0.32 | 0.96 | -0.33 | 0.00 | -0.28 / -0.14,-0.43,+0.07 | NO |
| 6J | 5 | 15m st[14, 3] exit=opp all ema200 | 7 | 0.44 | -0.33 | -1.12 | -0.87 | 1094 | -0.14 | -0.19 | -0.21 | +0.32 | 0.33 | -0.36 | 0.00 | -0.91 / -0.20,-0.28,-0.28 | NO |
| 6J | 6 | 15m rsi[14, 30] exit=time120 all ema200 | 8 | 0.30 | 1.12 | -1.64 | -0.43 | 157 | +0.22 | -0.25 | -0.15 | +0.23 | 1.00 | -0.09 | 0.17 | 0.24 / +0.17,-0.29,-0.19 | NO |
| 6J | 7 | 15m don[100] exit=time60 day ema200 | 7 | 0.30 | -1.33 | 0.12 | -1.10 | 161 | -0.20 | -0.13 | -0.17 | -0.05 | 0.13 | -0.31 | 0.00 | -1.37 / -0.25,-0.18,-0.20 | NO |
| 6J | 8 | 5m rsi[14, 30] exit=opp all ema200 | 7 | 0.26 | -0.57 | 0.58 | 2.77 | 347 | -0.14 | +0.03 | +0.30 | +0.10 | 1.00 | -0.19 | 0.00 | -0.19 / -0.18,-0.02,+0.26 | NO |
| 6J | 9 | 15m don[50] exit=time120 day ema200 | 7 | 0.25 | -0.74 | -0.72 | 0.10 | 188 | -0.13 | -0.29 | -0.01 | -0.19 | 0.44 | -0.25 | 0.00 | -0.89 / -0.17,-0.32,-0.04 | NO |
| 6J | 10 | 5m vw[3] exit=opp all ema200 | 7 | 0.18 | -0.94 | -1.27 | -0.00 | 193 | -0.16 | -0.33 | +0.06 | +0.19 | 0.99 | -0.28 | 0.00 | -1.03 / -0.19,-0.35,+0.03 | NO |
| CL | 1 | 15m lr[80] exit=opp all ema200 | 8 | 0.54 | 0.02 | -2.63 | 1.55 | 615 | -0.03 | -0.36 | +0.46 | -0.28 | 0.90 | -0.15 | 1.00 | 0.04 / -0.08,-0.42,+0.41 | NO |
| CL | 2 | 5m vw[2] exit=brk1.0 all ema200 | 7 | 0.43 | -0.41 | -2.10 | 0.35 | 691 | -0.12 | -0.32 | -0.04 | +0.17 | 0.99 | -0.34 | 0.00 | -0.71 / -0.22,-0.42,-0.12 | NO |
| CL | 3 | 15m lr[80] exit=opp all | 7 | 0.42 | -0.76 | -2.83 | 1.11 | 991 | -0.15 | -0.37 | +0.34 | -0.25 | 0.50 | -0.26 | 0.00 | -0.63 / -0.22,-0.46,+0.28 | NO |
| CL | 4 | 15m lr[50] exit=time120 day ema200 | 8 | 0.42 | -0.54 | -1.96 | -1.09 | 358 | -0.15 | -0.55 | -0.64 | -0.02 | 0.13 | -0.57 | 0.00 | -1.16 / -0.24,-0.63,-0.70 | NO |
| CL | 5 | 15m rsi[14, 30] exit=time60 all ema200 | 7 | 0.37 | -0.42 | -0.86 | 0.32 | 210 | -0.07 | -0.14 | -0.00 | -0.03 | 0.96 | -0.28 | 0.00 | -0.61 / -0.17,-0.25,-0.08 | NO |
| CL | 6 | 5m vw[2] exit=brk1.5 all ema200 | 7 | 0.35 | -0.57 | -1.94 | 0.20 | 625 | -0.14 | -0.20 | -0.04 | -0.00 | 0.79 | -0.32 | 0.00 | -0.72 / -0.20,-0.27,-0.10 | NO |
| CL | 7 | 15m rsi[5, 20] exit=opp day ema200 | 7 | 0.32 | -1.46 | 0.79 | 1.14 | 242 | -0.22 | +0.01 | +0.20 | -0.13 | 0.63 | -0.27 | 0.00 | -0.38 / -0.25,-0.04,+0.17 | NO |
| CL | 8 | 15m macd[19, 39] exit=opp day ema200 | 7 | 0.27 | 0.02 | -3.92 | -1.19 | 439 | -0.05 | -0.29 | -0.46 | +0.13 | 0.20 | -0.38 | 0.00 | -0.89 / -0.11,-0.35,-0.51 | NO |
| CL | 9 | 15m st[10, 2] exit=opp day ema200 | 7 | 0.24 | -0.65 | -1.83 | 1.17 | 799 | -0.13 | -0.21 | +0.24 | -0.06 | 0.63 | -0.27 | 0.00 | -0.52 / -0.22,-0.30,+0.17 | NO |
| CL | 10 | 5m st[14, 3] exit=opp day ema200 | 7 | 0.18 | -0.56 | -1.63 | -0.03 | 1245 | -0.11 | -0.22 | -0.34 | -0.06 | 0.56 | -0.37 | 0.00 | -0.90 / -0.23,-0.34,-0.42 | NO |
| GC | 1 | 15m rsi[14, 30] exit=brk1.5 all ema200 | 7 | 0.40 | -0.04 | 0.72 | -2.56 | 134 | -0.08 | +0.09 | -2.09 | -0.01 | 0.04 | -1.09 | 0.00 | -0.80 / -0.11,+0.06,-2.10 | NO |
| GC | 2 | 15m rsi[14, 30] exit=time60 all ema200 | 7 | 0.31 | -0.79 | -0.69 | 1.06 | 145 | -0.30 | -2.15 | +0.04 | -0.19 | 0.47 | -1.32 | 0.00 | -0.38 / -0.38,-2.20,-0.01 | NO |
| ZB | 1 | 15m rsi[14, 30] exit=brk1.0 all ema200 | 7 | 0.31 | 0.88 | 0.35 | -1.34 | 152 | +0.15 | +0.03 | -0.30 | +0.02 | 1.00 | -0.13 | 0.00 | -0.24 / +0.04,-0.03,-0.40 | NO |
| ZB | 2 | 15m rsi[14, 30] exit=brk1.5 all ema200 | 7 | 0.19 | 0.35 | 0.64 | -0.96 | 146 | +0.02 | +0.08 | -0.21 | +0.08 | 1.00 | -0.18 | 0.00 | -0.32 / -0.06,+0.04,-0.28 | NO |
| ZB | 3 | 15m vw[3] exit=brk1.0 all ema200 | 8 | 0.06 | 0.55 | -0.19 | 0.84 | 125 | +0.06 | -0.09 | +0.03 | +0.18 | 1.00 | -0.15 | 0.50 | -0.04 / -0.06,-0.16,-0.04 | NO |

Per-share and constant-risk results: `outputs/autopilot/c7/p1/score_top_<SYM>.csv`; selection tables `sel_all_<SYM>.csv`.

## Findings
- **Uplift gate:** 0 of 31 cells have +0.10 on clean, H1 and H2 together. Counted separately at 20%: clean >= +0.10 in 3 cells, H1 in 1, H2 in 8; never the same cells. The best clean uplift (6J RSI(14,30) time-120, +0.22) has H1 -0.25 and H2 -0.15.
- **Standalone in the pair window:** only 10 of 31 cells are positive all-in. The 2013-2022 mean-reversion structure (in-sample Sharpe 0.2-0.6) does not persist 2023-2026, and 2x slippage drives the mean all-in Sharpe from -0.18 to -0.51.
- **Own null:** 15 cells rank >= 0.95 against the random-entry null, but this is uninformative here: the random-entry null itself loses to cost in most instruments, so ranking above it does not make a negative or near-zero standalone Sharpe an edge. None of the 15 also passes the uplift or the bootstrap gate.
- **Bootstrap:** 0 of 31 90% intervals have a positive lower bound (best -0.06).
- **Plateau:** 2 cells have plateau >= 0.75 (6E VWAP z=3 bracket 2/3 at 0.75; CL linreg(80) opposite-signal EMA200 at 1.00); neither has a positive uplift on all spans (CL linreg(80): clean -0.03, H1 -0.36, H2 +0.46).
- **Correlation with the pair:** worst-decile correlation ranges -0.47 to +0.41 on 17 weeks (16 cells negative), but the sleeve's mean P&L in those weeks is positive in only 10 cells and no cell has a positive uplift on all spans. Not a hedge.
- **Constant-risk (20% share):** every cell costs net (mean -23%, best -14%) against the 5% limit.
- **Small-sample:** no selected cell has fewer than 100 trades in the pair window (min 125).
- **Interpretation:** selecting on a long history fixes the regime-luck problem of the NQ pair, and what it selects here is a weak mean-reversion regularity in rates and FX (in-sample Sharpe 0.2-0.6) that is not present in 2023-2026. ZN has no cell with 7 positive years among 1,078 eligible cells. Nothing here diversifies the pair.

## Fill model and limits
1-minute bars, next-bar-open entries, stop-first fills; costs and constants as above; commission and the 0.5/1 tick slippage are assumptions, not calibrated to NT8 fills. No netting against the pair's lots. 5- and 15-minute bars are built from clock-aligned 1-minute bars; EMA200 is on the signal timeframe. The false-survivor test uses a third of the grid and 50 replicates, so the replicate counts are scaled and coarse. CL's adjusted history crosses the 2020 negative-price episode.

**Executability / margin:** all six are CME Group futures, so executable at NinjaTrader Brokerage via Rithmic is expected (Y, general knowledge, not checked against the brokerage's product list). Margin per contract is unverified except GC at about 9% of notional (~$37k at ~$4,130, V5 P4); ZN/ZB/6E/6J/CL margins not verified. Nothing is proposed, so no margin decision is needed. Sleeve sizes to match the pair's volatility were large relative to the account for the thin-range instruments (scale factors are in `score_top_*.csv`, column `scale`).

**Runtime:** simulating the 6 x 1,120 cells took about 11 s per instrument on 12 workers (about 1.2 minutes); 6 x 50 replicates about 7 minutes on 10 workers; scoring (100 null draws, 3000-draw bootstrap, plateau, 4 shares) plus the 2x-slippage re-run about 12 minutes on 4 workers concurrently; total about 25 minutes of compute.

DONE C7_P1
