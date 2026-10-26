# REPORT PA3 - K96b CURE: FRESH PRE-REGISTERED HM STOP-ENTRY GRID (offset x order lifetime, 1-second engine, selection-corrected null)
**Verdict: LEAD. selected o2_L60 (offset 2 ticks, order life 60 min from run start; indistinguishable from RUN, +0.980/+0.654/+0.306 clean/H1/H2, all-in +0.803) passes uplift, bootstrap (CI [+0.20, +1.46]), worst week and the all-in null, but FAILS the selection-corrected clean null (clean +0.98 vs p95 +1.02, rank 0.91), plateau 2/3, 2x slippage H2 -0.05, alternating-month retention (0.22 and 0.29 vs 0.96 and 1.50, required >= 50%) and H0 (-0.07); replications 0 of 2, FOUND 0; no better than K96b. And 64% of the fills are market orders because the level was already breached at placement: true resting stop orders alone give +0.06/-0.14/+0.42**

## Set-up and fill model
- Engine: the K96 order-level account on 1-second bars (copy ap_pa3_core.py of ap_k96_core.py; entries at (bar, second, price)); control in market mode reproduces the live account (weekly Sharpe 1.46/2.83/2.30, zero daily difference from 2023-02-11; one pre-window boundary lot on 2023-02-09/10 differs by 5,655 USD and is outside every gate span except the first H0 days). ST at market exactly as live; HM only as stop-market entries. Pre-registered in PREREG_AUTOPILOT.md ('PA-K96B / PA3') before any cell ran.
- HM level for bar i from the state at the close of bar i-1 (causal VWAP, held at its previous value), re-quoted every bar; one-shot per regime run; order lifetime counted from the first bar of the run ({5,15,30,60 min, RUN = until the run ends}); offset {0,1,2} ticks beyond the level (15 cells). Fill: first 1-second bar reaching the order price, price max(order, previous-second close) for buys (gap-through fills at the gap), 60/60 bracket from the fill second, account slippage 1 tick/side + 34.88 per 8 lots, 2x = SLIP_PT 1.0. Orders that never fill in their window are lost trades: no market fallback, the account simply does not trade (counts below). BLOCKED bars as live. Book busy/netting as live.
- Selection: max clean uplift over the 15 cells. Plateau (pre-registered, discrete): one-step neighbours along offset and lifetime, keep = all-in uplift >= 75% of selected AND clean > 0; pass if >= 75% keep. Null (pre-registered, selection-corrected): 100 replicates, in each every cell's fills are re-drawn to a uniformly random second at or after the touch (shared draws across cells), all 15 cells re-run, the same max-clean selection applied, and the SELECTED replicate cell's uplifts form the null (selected cells in the replicates: o2_L5 79, o2_L60 6, o0_L5 6, o1_L5 6, o2_L30 3).
- DISCLOSURE: K96b (the single cell o1_RUN) already showed clean/H1/H2/all-in, H0 and both alternating-month halves, so every span and both replication windows are non-virgin for this family; the cap is FOUND-PENDING pending >= 8 new live weeks (none exist: rows end 2026-10-12, bars 2026-10-12 19:59; ES/RTY not run: the pair-row account is NQ-only). Replication therefore cannot be counted as virgin evidence.
- Files: code/census/night_ins/ap_pa3_core.py, ap_pa3.py, ap_pa3_rep.py, ap_pa3_watch.py; outputs/autopilot/pa3/ (pa3_all.pkl, pa3_summary.json, split_marketable.json, run.log, WATCH_LATEST.md). Runtime 8 min on a pool of 5 (+ 40 s import). Era: pair rows start 2023-02; H0 reported; pre-2023 n/a. ES/RTY replication not run.

## Grid, uplift per cell (weekly Sharpe vs the live pair; all spans printed for transparency, only the clean-selected cell was read for H1/H2)
| cell | clean | H1 | H2 | all-in | HM fills / lost live HM signals (of 5448) / trades |
|---|---|---|---|---|---|
| o0_L5 | +0.639 | -0.392 | -0.473 | +0.228 | 4103 / 4550 / 6101 |
| o0_L15 | +0.318 | -0.996 | -1.260 | -0.239 | 16265 / 1967 / 6925 |
| o0_L30 | +0.528 | +0.716 | -0.323 | +0.359 | 21411 / 681 / 7306 |
| o0_L60 | +0.505 | +1.171 | -0.045 | +0.475 | 22097 / 501 / 7393 |
| o0_LRUN | +0.505 | +1.171 | -0.045 | +0.475 | 22102 / 498 / 7393 |
| o1_L5 | +0.635 | -0.689 | -0.485 | +0.172 | 4002 / 4555 / 6078 |
| o1_L15 | +0.319 | -1.110 | -1.209 | -0.240 | 15990 / 1977 / 6938 |
| o1_L30 | +0.704 | +0.594 | -0.019 | +0.534 | 21024 / 692 / 7352 |
| o1_L60 | +0.721 | +0.661 | +0.245 | +0.619 | 21693 / 512 / 7428 |
| o1_LRUN | +0.721 | +0.661 | +0.245 | +0.619 | 21697 / 509 / 7428 |
| o2_L5 | +0.693 | -0.504 | -0.779 | +0.166 | 3888 / 4568 / 6076 |
| o2_L15 | +0.451 | -1.367 | -0.947 | -0.124 | 15674 / 1989 / 6945 |
| o2_L30 | +0.777 | -0.216 | +0.037 | +0.480 | 20592 / 710 / 7339 |
| o2_L60 **(selected)** | +0.980 | +0.654 | +0.306 | +0.803 | 21245 / 527 / 7480 |
| o2_LRUN | +0.980 | +0.654 | +0.306 | +0.803 | 21249 / 524 / 7480 |

## Result for the carried cell: o2_L60
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 2.44 | +0.980 | +1.111 |
| H1 | 2.83 | 3.48 | +0.654 | +0.632 |
| H2 | 2.30 | 2.60 | +0.306 | -0.054 |
| all | 1.86 | 2.66 | +0.803 | +0.792 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: PASS
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: PASS
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank): clean +0.980 vs +1.021 / 0.91; H1 +0.654 vs -0.129 / 1.00; H2 +0.306 vs -0.130 / 1.00; all +0.803 vs +0.365 / 1.00
- bootstrap 90% CI of all-in uplift: [+0.198, +1.459]
- plateau: 0.67 of 3 neighbours keep >= 75% of the all-in uplift; neighbours: o1_L60 +0.619; o2_L30 +0.480; o2_LRUN +0.803
- alternating-month split (pre-registered): select o2_L5 (+0.964) reads +0.217 on the other half; select o2_L60 (+1.500) reads +0.292 on the other half
- H0 (2023-02-10..07-31) uplift: -0.072; replications counted (alt-month, H0): 0 of 2 needed (newest live weeks and ES/RTY not available / not applicable for this pair-row family)
- worst-week (candidate vs pair): clean -80.3k vs -81.9k; H1 -77.1k vs -78.3k; H2 -79.5k vs -82.5k; all -80.3k vs -82.5k; weekly corr with pair 0.768 (pair change, no hedge claim; worst-decile corr n/a)

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 2.44 | 4.87 | 6.94 | -78.6k | -78.0k | 310k | -80.3k | 38.1 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 3.48 | 8.66 | 4.01 | -71.5k | -67.5k | 195k | -77.1k | 25.0 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 cand | 2.60 | 5.73 | 4.98 | -78.4k | -74.8k | 165k | -79.5k | 38.9 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all cand | 2.66 | 5.56 | 12.12 | -78.5k | -77.0k | 310k | -80.3k | 36.3 |

## Reading
The 15-cell grid is dominated by one effect: longer order lifetimes help (5/15-minute lifetimes fail on H1/H2: o1_L5 -0.69/-0.49, o1_L15 -1.11/-1.21 because most live HM signals, 4,568 of 5,448 at 5 minutes, happen after the order expired and are lost trades) and offsets of 1-2 ticks help on clean; lifetime 60 and RUN coincide (97% of fills occur within 30 minutes of the run start, median 10; lifetimes 60 and RUN differ by 4 events). Selection moved from the K96b cell (o1_RUN, +0.721) to o2_L60 (+0.980) on clean, with H1 +0.654 and H2 +0.306 essentially as before: the extra 2 ticks buy clean points only. Selection-corrected null: the random-fill replicates (fills at a random second at or after the touch) average +0.77 on clean but -0.62/-0.75 on H1/H2; the selected real cell beats the null p95 on H1, H2 and all-in but not on clean (+0.98 vs p95 +1.02, rank 0.91): the clean gain is within what random fills after the same triggers produce, so on the span used for selection the specific entry price adds little over 'trade the touch bar at some later time', which is the opposite of the K96b reading (that null had no selection correction and no lifetime axis). Fill rate: of the 67,941 runs with an eligible bar inside 60 minutes only 31% fill (the rest are lost trades: price never reaches the level), and 527 of 5,448 live HM market signals (9.7%) have no stop fill by their signal bar; those lost trades averaged +0.23 pts against +2.30 for the kept ones, so unfilled orders are not where the money is lost.
Decomposition (report-only diagnostic after the run, not selection): of the 21,245 fills of the selected cell 13629 (64%) are marketable at placement (the first second of the bar is already beyond the order price, so a buy-stop below the market cannot rest; it would have to be sent as a market order at the bar open, i.e. the 'stop-entry' is for most trades an anticipatory market entry at the next bar's open using the intrabar-updated HMA/VWAP cross level, one bar earlier than the live close-confirmed signal). Running only the true resting-stop fills (7,616 events) gives clean +0.06 / H1 -0.14 / H2 +0.42, only the marketable fills +0.36 / -1.28 / -1.03: neither half carries the effect, the uplift lives in the combination, which is more consistent with account-level netting/busy interactions (which entry takes the book first) than with a clean 'better price' mechanism. Stop-market slippage stress (report-only, trigger unchanged): fills 1 tick worse: +0.72/+0.78/+0.36; 2 ticks worse: +0.69/+0.67/+0.07 (H2 falls to the gate line at 2 ticks); the real 2x-slippage test fails on H2 (-0.05).
Verdict: LEAD (non-virgin; FOUND-PENDING not reached: gates failed: selection-corrected clean null, plateau 0.67 of 3 (neighbours o1_L60 all-in +0.62, o2_L30 +0.48 (below 75% of +0.80), o2_LRUN +0.80), 2x slippage H2, alternating-month retention, H0). The fresh treatment (lifetimes, offsets, 1-second fills with lost trades, selection-corrected null) did not rescue K96b; it removed the one thing in its favour (the null pass on clean). Recommendation: do not implement; leave on watch only (ap_pa3_watch.py, watermark 20261013) and do not spend further grid cells on this family.

## Executability / era / replication
NT8 implementation spec (HM stop-entry; not recommended, written for completeness)
- Order type: for each bar (Calculate = OnBarClose is NOT enough; the order must be live inside the bar, so submit at the first tick of the new bar from OnBarUpdate with IsFirstTickOfBar, or run Calculate.OnEachTick): compute the causal level L from the closed HM state (a, b of the previous bar, ema, previous VWAP; the closed-form HMA end weights wa=0.1074 wb=0.0268; price c' solving a(c')>b(c') and b(c')>b[i-1]; level + offset ticks). Use SubmitOrderUnmanaged / EnterLongStopMarket(0, qty, stopPrice, name) (managed: EnterLongStopMarket with a unique signal name; re-quote by calling it again with a new price on the next bar: the managed approach modifies a working order of the same signal name). Stop-market (not stop-limit): a limit cap leaves the order unfilled in a fast move and the live-pair edge is entry timing, so a non-fill is the costlier failure.
- Marketable case (64% of fills in the test): a buy-stop below the current ask (or sell-stop above the bid) is rejected by NT8/Rithmic or converted by the broker. The strategy must test the price: if Ask >= L(buy) submit EnterLong market (or limit at ask), else submit the stop. The 1-second model fills these at the previous-second close at bar start, so this branch is part of the tested result.
- OCO: a long and a short entry are never working together (long needs a<=b, short needs a>=b), but the stale-side order must be cancelled when the regime flips (CancelOrder on the opposite entry in the same OnBarUpdate). On a fill, attach the 60/60 bracket as a stop-market and a limit with the same OCO id (SetStopLoss/SetProfitTarget in managed mode, or ExitLongStopMarket + ExitLongLimit with a shared OCO string in unmanaged mode); cancel any remaining entry order of that book. The ST market entries and their brackets are unchanged.
- Lifetime: cancel at expiry (60 min from the first bar of the run, or at the run end) with CancelOrder; also cancel at TimeBlock/entry-window end (live BLOCKED bars) and on session end; order TIF = Day; the strategy must not leave resting orders over the 17:00 ET maintenance halt.
- Gaps: NT8 (live, Rithmic) a stop-market is triggered when the market trades at or through the stop and fills at the next available price: through a gap or after the maintenance halt the fill is at the open/first trade, worse than the stop price (the sim uses max(order, previous second close); the observed overshoot is large only for the marketable branch). In NT8 backtests (Strategy Analyzer) fills for stop orders are at the stop price or the next tick/bar open: do not trust the NT8 backtest for this strategy; use the 1-second replay (ap_pa3_core.acct_se) as the reference. Set Order Fill Resolution to Tick in any NT8 backtest.
- Rithmic stop-entry slippage: no stop-slippage data exist on this box (no live fills for stop entries in rows or logs); the model uses 1 tick/side. The stop-market stress in this study shows the effect holds at +1 tick (H2 +0.36) and weakens at +2 ticks (H2 +0.07). NQ stop-market slippage of 1 tick in liquid hours is typical, 2-4 ticks around news and the 08:30/09:30 opens; Rithmic stop orders sit in the exchange order book as stop orders (CME-native stops for NQ) in normal operation, but NinjaTrader's server-side vs strategy-side stop handling matters: strategy-side stops (NT8 simulated stops via Rithmic, e.g. when the 'Stop' order type is handled by NinjaTrader on connection loss) are held in NT8 and sent as market orders on touch, adding a data-latency delay. Verify with a paper run: 20 trading days of logged fill-vs-trigger prices before any decision.
- Margin: unchanged (same lots, 8/8); a resting order consumes no extra margin on CME until filled. Substantial change to DualStrat: the signal state machine is replaced by touch logic plus order management (re-quote every bar, expiry, marketable test); not recommended given the verdict.


DONE PA3
