# REPORT K96 - STOP-ENTRY ORDERS AT THE FLIP LEVEL +1 TICK INSTEAD OF MARKET AT BAR CLOSE (1-second engine), live pair
**Verdict: NO. FOUND 0. Upper bound A (confirmed flips only, no false triggers) is +1.69/+2.19/+2.71 weekly Sharpe, an artefact of entering 5.6 pts better on every confirmed flip; with the false triggers simulated the pre-registered cells fail on clean: selected one-shot -0.198 clean / +1.282 H1 / +1.343 H2 (needed +0.10 each), all-in +0.344, bootstrap CI [-0.35, +1.08], re-arm -0.358/+1.952/+0.751. Variant K96b (HM stop-entry only, ST at market, causal VWAP): +0.72/+0.66/+0.25 = LEAD (see REPORT_K96b.md), not FOUND**

## Set-up and fill model
- Engine: the corrected order-level account (copy of nt8sim.acct: per-book busy, FIFO netting against opposite lots, persistent protective orders, orphan fills, force-close) re-run on 1-second bars with entries at (bar i, second k, price) instead of (bar i+1, open). Control: the same code in market mode (entry at the next open of every live signal) reproduces the 13,103 live rows and the account exactly (1.46/2.83/2.30; 0 differences). Trigger level for the signal bar i from the state at the close of bar i-1: ST long max(dn[i-1], ema200[i-1]) while trend[i-1] = -1 (short mirrored with up/ema); HM long the smallest close c' with a_i(c') > b_i(c'), b_i(c') > b[i-1], c' > ema[i-1] (a, b affine in c' through the HMA end weights 0.1074/0.0268; validated: for confirmed flips the close is beyond the level in 98.1% of rows, and the +1 tick level is touched inside the signal bar in 97.8%; the remaining about 8% of pair rows are orphan-opened lots with no signal). Buy-stop at level + 1 tick (sell-stop at level - 1 tick), fill price max(level+tick, previous second close) for buys, at the first 1-second bar that reaches it; entry windows (BLOCKED signal bars) as live; 60/60 bracket from the fill second; account slippage 1 tick/side + $34.88 per 8 lots as every row; 2x = SLIP_PT 1.0.
- Cells: (A) UPPER BOUND, diagnostic, not a candidate: live rows (confirmed flips only) with the entry moved to the first touch second; (B) one-shot: first touch per regime run per book (ST trend run, HM a<=b / a>b run); (C) re-arm: the order is re-placed every bar while the precondition holds and the book is flat. Candidates B and C, selection clean-only. The pre-registered rule: if A fails the clean gate, B and C are not run (A passed). Null as registered: the same trigger bars filled by a market order at a uniformly random second of the bar (100 draws); disclosed flaw: such a fill can precede the touch (a cheaper long than the stop price), so the null is favourable to itself (mean all-in uplift +0.78); the K96b variant uses a random second AT OR AFTER the touch. Plateau: +0 and +2 ticks.

## Grid, uplift per cell (weekly Sharpe vs the live pair; all spans printed for transparency, only the clean-selected cell was read for H1/H2)
| cell | clean | H1 | H2 | all-in | events / opened / netted / busy |
|---|---|---|---|---|---|
| oneshot **(selected)** | -0.198 | +1.282 | +1.343 | +0.344 | 54862 / 12140 / 1487 / 41235 |
| rearm | -0.358 | +1.952 | +0.751 | +0.217 | 80416 / 12316 / 1571 / 66529 |

## Result for the carried cell: oneshot
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.26 | -0.198 | -0.068 |
| H1 | 2.83 | 4.11 | +1.282 | +1.382 |
| H2 | 2.30 | 3.64 | +1.343 | +1.366 |
| all | 1.86 | 2.20 | +0.344 | +0.448 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: PASS
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank): clean -0.198 vs +1.074 / 0.00; H1 +1.282 vs +2.355 / 0.62; H2 +1.343 vs +1.525 / 0.86; all +0.344 vs +1.137 / 0.04
- bootstrap 90% CI of all-in uplift: [-0.349, +1.077]
- plateau: 1.00 of 2 neighbours keep >= 75% of the all-in uplift; neighbours: +0 ticks +0.282; +2 ticks +0.337
- alternating-month split (pre-registered): select oneshot (-0.238) reads -0.128 on the other half; select rearm (+0.000) reads -0.644 on the other half
- H0 (2023-02-10..07-31) uplift: +1.030; replications counted (alt-month, H0): 1 of 2 needed (newest live weeks and ES/RTY not available / not applicable for this pair-row family)
- worst-week (candidate vs pair): clean -81.4k vs -81.9k; H1 -80.7k vs -78.3k; H2 -77.9k vs -82.5k; all -81.4k vs -82.5k; weekly corr with pair 0.699 (pair change, no hedge claim; worst-decile corr n/a)

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.26 | 2.21 | 2.01 | -79.2k | -78.6k | 574k | -81.4k | 43.8 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 4.11 | 9.66 | 6.60 | -67.7k | -61.7k | 135k | -80.7k | 25.0 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 cand | 3.64 | 8.97 | 5.91 | -77.9k | -71.0k | 199k | -77.9k | 36.1 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all cand | 2.20 | 4.28 | 5.61 | -79.1k | -78.4k | 574k | -81.4k | 39.3 |

## Reading
Entering at the flip level instead of at the close pays about 5.6 points on each confirmed flip, so a replay of the live rows (cell A) looks spectacular (+1.69/+2.19/+2.71); the whole gain is the selection bias of only counting touches the close confirmed. Once every touch is traded (54,862 one-shot events, 80,416 re-arm events against about 58,000 live signals) the benefit is gone on the 24-month clean span (-0.20 one-shot, -0.36 re-arm), although H1 (+1.28) and H2 (+1.34) and H0 (+1.03) are positive and large: the sign is not stable across spans, the all-in bootstrap CI is [-0.35, +1.08] and the alternating-month halves are negative. A split by book (diagnostic, not selection) puts the problem on ST: ST stop + HM market = -0.05/-0.23/-0.10; HM stop + ST market = +0.36/+0.59/+0.25 (non-causal VWAP) and +0.72/+0.66/+0.25 (causal VWAP). That is the K96b variant, pre-registered after this diagnostic, reported separately. Mechanism: the ST band is 2 ATR(120) from price, so a touch is more often a failed break; the HM cross level is close to price and the touch is mostly confirmed. 2x slippage: one-shot -0.07/+1.38/+1.37.

## Executability / era / replication
NT8: stop-entry orders at a computed price are executable (ST level from the band and EMA, HM level from the closed-form HMA end weights), placed at each bar start and cancelled at the bar end; NinjaTrader Brokerage via Rithmic handles stop-market entries (slippage risk is the 1 tick/side assumed plus gaps through the stop). The strategy's signal state machine would have to be replaced by touch logic (substantial change to DualStrat). Margin unchanged (same lots, 8/8). Era: pair rows start 2023-02; H0 reported; pre-2023 n/a. Files: code/census/night_ins/ap_k96_core.py, ap_k96.py, ap_k96b.py, ap_k96_rep.py; outputs/autopilot/k96/, k96b/.

DONE K96
