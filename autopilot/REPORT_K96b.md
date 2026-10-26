# REPORT K96b - HM STOP-ENTRY AT THE CAUSAL FLIP LEVEL +1 TICK, ST AT MARKET (variant of K96)
**Verdict: LEAD. LEAD (gate 3 only plus own null; NOT FOUND). HM stop-entry (causal flip level +1 tick, one-shot) with ST unchanged at market: weekly Sharpe uplift +0.721 clean / +0.661 H1 / +0.245 H2 (all three above +0.10), all-in +0.619; own null passes (all-in p95 +0.42, rank 1.00); fails bootstrap by a hair (CI [-0.005, +1.28]), plateau 0.67 of 3, 2x slippage H2 -0.09, H0 +0.05, alternating months +1.33/-0.03: replication 0 of 2**

## Set-up and fill model
- Engine: the corrected order-level account (copy of nt8sim.acct: per-book busy, FIFO netting against opposite lots, persistent protective orders, orphan fills, force-close) re-run on 1-second bars with entries at (bar i, second k, price) instead of (bar i+1, open). Control: the same code in market mode (entry at the next open of every live signal) reproduces the 13,103 live rows and the account exactly (1.46/2.83/2.30; 0 differences). Trigger level for the signal bar i from the state at the close of bar i-1: ST long max(dn[i-1], ema200[i-1]) while trend[i-1] = -1 (short mirrored with up/ema); HM long the smallest close c' with a_i(c') > b_i(c'), b_i(c') > b[i-1], c' > ema[i-1] (a, b affine in c' through the HMA end weights 0.1074/0.0268; validated: for confirmed flips the close is beyond the level in 98.1% of rows, and the +1 tick level is touched inside the signal bar in 97.8%; the remaining about 8% of pair rows are orphan-opened lots with no signal). Buy-stop at level + 1 tick (sell-stop at level - 1 tick), fill price max(level+tick, previous second close) for buys, at the first 1-second bar that reaches it; entry windows (BLOCKED signal bars) as live; 60/60 bracket from the fill second; account slippage 1 tick/side + $34.88 per 8 lots as every row; 2x = SLIP_PT 1.0.
- Variant registered in PREREG_AUTOPILOT.md (K96b) AFTER a diagnostic split by book that showed clean/H1/H2/all-in for it, so those spans are non-virgin; H0 and the alternating-month halves were not printed before. The VWAP of the bar is held at its previous value (what an order placed at the bar start can know). ST rows exactly as live; HM entries are one-shot stop-entries at the causal level +1 tick. Single cell; plateau +0 / +2 ticks / re-arm; null: the same HM trigger bars filled at a random second at or after the first touch (100 draws, full account re-run each, the mixed ST market rows unchanged).

## Grid, uplift per cell (weekly Sharpe vs the live pair; all spans printed for transparency, only the clean-selected cell was read for H1/H2)
| cell | clean | H1 | H2 | all-in |
|---|---|---|---|---|
| HM_stop_oneshot **(selected)** | +0.721 | +0.661 | +0.245 | +0.619 |

## Result for the carried cell: HM_stop_oneshot
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 2.18 | +0.721 | +1.034 |
| H1 | 2.83 | 3.49 | +0.661 | +0.635 |
| H2 | 2.30 | 2.54 | +0.245 | -0.095 |
| all | 1.86 | 2.47 | +0.619 | +0.730 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: PASS
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): PASS
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank): clean +0.721 vs +0.474 / 1.00; H1 +0.661 vs +1.037 / 0.75; H2 +0.245 vs +0.335 / 0.92; all +0.619 vs +0.422 / 1.00
- bootstrap 90% CI of all-in uplift: [-0.005, +1.280]
- plateau: 0.67 of 3 neighbours keep >= 75% of the all-in uplift; neighbours: +0 ticks +0.475; +2 ticks +0.803; re-arm +0.460
- alternating-month split (pre-registered): select HM_stop_oneshot (-0.026) reads +1.327 on the other half; select HM_stop_oneshot (+1.327) reads -0.026 on the other half
- H0 (2023-02-10..07-31) uplift: +0.053; replications counted (alt-month, H0): 0 of 2 needed (newest live weeks and ES/RTY not available / not applicable for this pair-row family)
- worst-week (candidate vs pair): clean -80.2k vs -81.9k; H1 -77.2k vs -78.3k; H2 -79.4k vs -82.5k; all -80.2k vs -82.5k; weekly corr with pair 0.756 (pair change, no hedge claim; worst-decile corr n/a)

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 2.18 | 4.26 | 5.40 | -78.2k | -77.7k | 360k | -80.2k | 40.0 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 3.49 | 8.34 | 3.85 | -71.5k | -67.5k | 197k | -77.2k | 25.0 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 cand | 2.54 | 5.55 | 5.01 | -78.3k | -74.8k | 162k | -79.4k | 38.9 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all cand | 2.47 | 5.06 | 9.77 | -78.1k | -77.5k | 360k | -80.2k | 37.5 |

## Reading
The HM cross level is a few points from price, so entering on the touch buys the cross price instead of the bar close with few extra false triggers (21698 HM events vs about 22,000 live HM signals); the clean uplift (+0.72) beats a timing-destroyed fill at a random second at or after the touch (p95 +0.47) which means the level itself, not just 'enter earlier', carries the gain. But the evidence does not replicate: H0 +0.05 (needs >= 0.36), alternating-month select-odd/read-even +1.33 and select-even/read-odd -0.03 (the effect sits in the even months), bootstrap lower bound -0.005, plateau: +0 ticks +0.48, +2 ticks +0.80, re-arm +0.46 all-in but only 2 of 3 keep 75% of the +0.62, and 2x slippage turns H2 to -0.09. It is a LEAD to be watched on live weeks (FORWARD protocol) after an HM-only stop-entry is paper-run; promotion needs two independent replications: newest live weeks and H0/alternating-month on new data.

## Executability / era / replication
NT8: stop-entry orders at a computed price are executable (ST level from the band and EMA, HM level from the closed-form HMA end weights), placed at each bar start and cancelled at the bar end; NinjaTrader Brokerage via Rithmic handles stop-market entries (slippage risk is the 1 tick/side assumed plus gaps through the stop). The strategy's signal state machine would have to be replaced by touch logic (substantial change to DualStrat). Margin unchanged (same lots, 8/8). Era: pair rows start 2023-02; H0 reported; pre-2023 n/a. Files: code/census/night_ins/ap_k96_core.py, ap_k96.py, ap_k96b.py, ap_k96_rep.py; outputs/autopilot/k96/, k96b/.

DONE K96b
