# REPORT C5-M1 — LONG-HISTORY-SELECTED INTRADAY FAMILIES (NQ and ES)

**Verdict: NO. 0 FOUND, 0 LEAD.** Selection on 2013-2022 finds a real-looking but weak structure in-sample (NQ: more cells pass the 7-of-10-years rule than chance; ES: a better top-10 than chance), and **none of it carries into the pair window** (2023-08..2026-10): every one of the 16 selected cells fails the additive gate at every share, and not one is positive-uplift on clean, H1 and H2 together.

## What was run
- **Pre-registered** in `PREREG_AUTOPILOT.md` ('CYCLE 5' and 'C5-M1 grid', written before the first full simulation; only 8 smoke-test cells had run, results not inspected).
- **Data:** purchased Databento 1-minute continuous front (.v.0) bars, 2013-01-02..2026-10-13, NQ and ES. Roll handling: difference back-adjustment at the 55 instrument_id changes (gap = first open of the new contract minus last close of the old; earlier bars shifted); every trade is flat by the 16:55 ET bar open, so no trade spans a roll. 5/15-min bars on the ET DST clock, trading day = ET + 6 h.
- **Grid:** 1,464 cells per instrument (2,928 total): 21 rules (EMA cross x3, MACD zero-cross x3, Supertrend x3, Donchian x3, linreg slope x3, RSI MR x3, VWAP-distance MR x2, opening-range breakout) x {5,15} min x 6 exits (opposite/EOD, bracket 60/90 NQ pts [ES x 0.3], time stop 60/120/240) x sessions {all, RTH, Globex} x EMA200 {off,on}.
- **Costs / fills:** NQ 1 tick/side, ES 0.5 tick/side, $4.36 per contract round trip, 8 contracts, entry at the next bar open, stop-first fills, targets without slippage (as V5 P2). 2x slippage re-run for the selected cells.
- **Selection (2013-2022 only):** >= 300 trades; positive weekly Sharpe in >= 7 of the 10 calendar years; rank by 2013-2022 weekly Sharpe; top 10 per instrument. NQ had 81 cells pass the year rule, ES 28 (so only 10 of 28 on ES were taken, all 10 reported). **All 20 selected cells are reported below; none was dropped.** Clean/H1/H2 were read once, after selection.
- **Sleeve scaling:** each cell's daily P&L is scaled so its 2013-2022 weekly volatility equals the pair's clean weekly volatility (no use of H1/H2). Pair = `B.Cfg(wk_floor=8, wk_loss_pb=None)` computed in a clean process (t3_score).

## False-survivor test (timing-destroyed replicates, 100 per instrument, full grid)
Replicates keep each cell's event count, put the events at random bar ends with alternating sides, and rerun the identical selection (>= 300 trades, 7-of-10 rule, ranking).

| inst | real cells passing 7-of-10 | replicate mean passing | p (rep >= real) | real top-10 mean Sharpe | replicate top-10 mean | p | real best | replicate best (mean) | p | real passing 9-of-10 | replicate mean |
|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ | 81 | 51.9 (median 52, max 66) | 0.00 | 0.78 | 0.77 | 0.48 | 0.95 | 1.01 | 0.67 | 5 | 1.5 |
| ES | 28 | 29.1 (median 29, max 47) | 0.62 | 0.65 | 0.53 | 0.02 | 1.08 | 0.77 | 0.01 | 2 | 0.6 |

Reading: **NQ** has more year-consistent cells than any of the 100 replicates (81 vs a replicate maximum of 66), but its top-10 Sharpe (0.78) is exactly what the replicates produce (0.77, p=0.48): the family has broad mild year-consistency, not a standout cell. **ES** passes the year rule about as often as chance (p=0.62) but its top-10 mean (0.65) and best cell (1.08) are above the replicates (p=0.02, 0.01), driven by the 5-min linreg-slope(50) RTH bracket cells.

## The 20 selected cells read in the pair window
Columns: Sharpe 2013-22 (selection span); standalone weekly Sharpe in clean / H1 / H2; additive uplift in weekly Sharpe at a 20% share of the pair's risk (sleeve at the pair's clean volatility) on clean / H1 / H2; worst-decile correlation with the pair; own random-entry null rank on the pair-window Sharpe; bootstrap 90% lower bound of the all-in uplift; plateau = share of the +-25% parameter neighbours that keep >= 75% of the all-in uplift; 2x slippage; amended FOUND gate at 20% (uplift >= +0.10 on each span, worst week within share, own null p95, bootstrap > 0, worst-decile corr <= +0.30).

### NQ (top 10)
| # | cell | yrs>0 of 10 | Sharpe 2013-22 | clean | H1 | H2 | trades pair win | up20 clean | up20 H1 | up20 H2 | wd corr | own-null rank (pair win) | boot lo | plateau | 2x slip: standalone / up20 c,H1,H2 | amended gate @20% |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 15m orb[30] exit=brk90 rth ema200 | 7 | 0.95 | 0.67 | 0.65 | -0.41 | 584 | +0.04 | -0.17 | -0.46 | +0.40 | 0.72 | -0.34 | 0.00 | 0.33 / +0.02,-0.20,-0.47 | NO |
| 2 | 5m macd[19, 39] exit=brk90 rth | 9 | 0.95 | 0.77 | 2.35 | -0.76 | 870 | +0.19 | +0.44 | -0.18 | -0.36 | 0.96 | -0.14 | 0.33 | 0.64 / +0.17,+0.41,-0.21 | NO |
| 3 | 5m macd[19, 39] exit=brk60 rth | 9 | 0.89 | 1.58 | -0.06 | 0.27 | 1014 | +0.39 | -0.41 | +0.21 | +0.23 | 0.95 | -0.05 | 0.33 | 0.82 / +0.35,-0.44,+0.17 | NO |
| 4 | 15m orb[30] exit=brk60 rth ema200 | 7 | 0.80 | 0.42 | 1.10 | -0.16 | 584 | -0.02 | -0.14 | -0.28 | +0.32 | 0.72 | -0.32 | 0.00 | 0.30 / -0.04,-0.17,-0.31 | NO |
| 5 | 5m lr[50] exit=brk90 rth | 9 | 0.73 | 0.23 | 1.15 | -0.96 | 861 | +0.04 | -0.12 | -0.48 | -0.07 | 0.54 | -0.37 | 0.00 | -0.01 / +0.01,-0.15,-0.51 | NO |
| 6 | 5m macd[12, 26] exit=brk90 rth ema200 | 8 | 0.72 | 1.60 | 0.08 | 1.09 | 843 | +0.42 | -0.32 | +0.02 | +0.32 | 0.97 | -0.06 | 0.17 | 1.16 / +0.39,-0.34,-0.01 | NO |
| 7 | 5m st[14, 3] exit=opp rth ema200 | 7 | 0.70 | -0.20 | 1.82 | -0.20 | 1003 | -0.25 | +0.16 | -0.51 | +0.27 | 0.40 | -0.56 | 0.00 | 0.08 / -0.28,+0.13,-0.54 | NO |
| 8 | 5m macd[19, 39] exit=brk60 rth ema200 | 7 | 0.69 | 0.96 | -0.35 | -0.10 | 783 | +0.24 | -0.44 | -0.11 | +0.41 | 0.73 | -0.18 | 0.83 | 0.37 / +0.21,-0.47,-0.14 | NO |
| 9 | 15m don[100] exit=time240 rth ema200 | 8 | 0.68 | 1.25 | 0.76 | -1.18 | 175 | +0.27 | +0.47 | -0.54 | -0.32 | 0.89 | -0.29 | 0.50 | 0.69 / +0.26,+0.46,-0.55 | NO |
| 10 | 5m ema[20, 60] exit=brk90 rth ema200 | 7 | 0.67 | 0.24 | 2.38 | -1.81 | 647 | -0.01 | +0.32 | -0.70 | +0.08 | 0.37 | -0.39 | 0.00 | -0.04 / -0.03,+0.30,-0.72 | NO |

### ES (top 10 of the 28 cells that passed the year rule)
| # | cell | yrs>0 of 10 | Sharpe 2013-22 | clean | H1 | H2 | trades pair win | up20 clean | up20 H1 | up20 H2 | wd corr | own-null rank (pair win) | boot lo | plateau | 2x slip: standalone / up20 c,H1,H2 | amended gate @20% |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 5m lr[50] exit=brk90 rth | 9 | 1.08 | 0.30 | 0.15 | -1.29 | 791 | +0.04 | -0.35 | -0.45 | -0.16 | 0.55 | -0.38 | 0.00 | -0.23 / -0.00,-0.39,-0.49 | NO |
| 2 | 5m lr[50] exit=brk90 rth ema200 | 7 | 0.83 | -0.05 | 0.77 | -0.74 | 607 | -0.04 | -0.22 | -0.35 | -0.01 | 0.42 | -0.39 | 0.00 | -0.19 / -0.08,-0.26,-0.39 | NO |
| 3 | 5m lr[50] exit=brk60 rth | 9 | 0.77 | 0.73 | 0.14 | -1.24 | 874 | +0.12 | -0.37 | -0.37 | -0.25 | 0.80 | -0.31 | 0.00 | -0.02 / +0.07,-0.43,-0.43 | NO |
| 4 | 15m vw[2] exit=time60 rth ema200 | 7 | 0.72 | -1.24 | -2.53 | -1.57 | 122 | -0.39 | -1.67 | -0.50 | -0.62 | 0.00 | -0.97 | 0.00 | -1.66 / -0.43,-1.71,-0.52 | NO |
| 5 | 5m don[50] exit=brk60 rth ema200 | 8 | 0.59 | 0.27 | -2.00 | 0.03 | 567 | -0.01 | -0.74 | -0.16 | +0.17 | 0.37 | -0.40 | 0.00 | -0.34 / -0.06,-0.79,-0.20 | NO |
| 6 | 15m rsi[14, 30] exit=time60 all ema200 | 7 | 0.58 | -0.79 | 0.27 | -0.85 | 178 | -0.35 | +0.19 | -0.34 | -0.20 | 0.44 | -0.64 | 0.00 | -0.80 / -0.40,+0.12,-0.40 | NO |
| 7 | 15m vw[2] exit=time120 rth ema200 | 7 | 0.57 | -0.94 | -2.80 | -2.15 | 114 | -0.20 | -1.23 | -0.79 | -0.22 | 0.00 | -0.80 | 0.00 | -1.64 / -0.22,-1.25,-0.80 | NO |
| 8 | 5m lr[50] exit=brk60 rth ema200 | 7 | 0.49 | 0.49 | 0.56 | -0.90 | 658 | +0.07 | -0.28 | -0.31 | -0.14 | 0.57 | -0.30 | 0.00 | 0.01 / +0.03,-0.33,-0.36 | NO |
| 9 | 15m vw[2] exit=time240 rth ema200 | 7 | 0.43 | -0.69 | -2.42 | -0.55 | 109 | -0.14 | -1.21 | -0.07 | +0.46 | 0.05 | -0.57 | 0.00 | -1.12 / -0.15,-1.23,-0.08 | NO |
| 10 | 15m rsi[14, 30] exit=time120 all ema200 | 8 | 0.41 | -0.07 | -0.05 | -1.17 | 164 | -0.02 | -0.27 | -0.51 | -0.17 | 0.55 | -0.43 | 0.00 | -0.47 / -0.06,-0.31,-0.55 | NO |

Full per-share results, constant-risk framing and per-year Sharpe: `outputs/autopilot/c5/m1/score_top_NQ.csv`, `score_top_ES.csv`, `sel_all_*.csv`.

## Findings
- **Uplift gate:** 0 of 20 cells reach +0.10 on clean, H1 and H2 together at any share (best NQ cells: MACD(12,26) bracket-90 EMA200 clean +0.42 / H1 -0.32 / H2 +0.02; MACD(19,39) bracket-60 clean +0.39 / H1 -0.41 / H2 +0.21). The H1 uplift at 20% is negative for 15 of 20 cells and the H2 uplift for 18 of 20.
- **Pair-window standalone:** the long-history winners are mostly positive on clean but fall apart in H1/H2 (e.g. NQ MACD(19,39) bracket-90: clean 0.77, H1 2.35, H2 -0.76). ES cells are near zero or negative all-in.
- **Own null:** 3 NQ cells reach rank >= 0.95 on the pair-window Sharpe (MACD(19,39) bracket-90 0.96, bracket-60 0.95, MACD(12,26) bracket-90 EMA200 0.97) and none of the ES cells does; none of those 3 passes the uplift test. Bootstrap lower bounds are negative for all 20.
- **Plateau:** the best plateau shares are 0.83 (NQ MACD(19,39) bracket-60 EMA200) and 0.50 (Donchian 100), but those cells fail the uplift gate; for the rest the neighbourhood is thinner than the cell.
- **2x slippage:** pair-window standalone Sharpe falls by 0.05-0.1 (NQ) and 0.1-0.3 (ES); no cell becomes a pass.
- **Correlation with the pair:** worst-decile correlation ranges -0.36 to +0.41 (NQ) and -0.62 to +0.46 (ES) on 17 weeks; the ones that are negative are not the ones with a positive uplift. Not a hedge.
- **Interpretation:** a 7-of-10-years rule on NQ intraday trend-following in RTH isolates a mildly persistent but unexploitable structure (top-10 Sharpe 0.78 with the null at 0.77); the 2013-2022 edge of the best cells does not carry into 2023-2026 over the spans that matter for the pair. Together with C3-H2/H3 (the pair and the 5-minute family have no 2013-2022 edge), the data say these intraday trend books are regime-specific.

## Fill model and limits
Fill model: 1-minute bars, next-bar-open entries, stop-first, 1 tick/side NQ and 0.5 tick/side ES (+ $4.36 RT commission, my assumption), 2x tested. No netting against the pair's lots. ES brackets are NQ brackets x 0.3 (not independently tuned). Back-adjusted prices (difference) for signals; P&L is computed on adjusted prices, which is exact within a day. The 1-minute engine has not been reconciled to NT8 for these rules (see C3-H2: ~90% entry match for the pair's own logic).
**Engineering note:** the first ES pass used NQ constants for point value and slippage because numba froze module globals in the cached simulator; found by checking that the 2x-slippage run reproduced the 1x numbers, fixed by passing the constants as arguments, and **everything reported here was re-run after the fix** (NQ results were unaffected).

**Executability:** all cells are NQ/ES futures strategies (CME, Rithmic Y). None would be proposed: nothing passes. Margin not computed.

**Runtime:** simulation of the 2 x 1,464 cells took 12 s on 8 workers each; 100 replicates per instrument ~13 min on 8 workers each (concurrent); scoring + nulls + plateau ~1 min per instrument; total ~25 min compute.

DONE C5_M1
