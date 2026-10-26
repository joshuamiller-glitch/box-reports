# REPORT L90 - ST / HM signals on a composite ES+NQ price path, executed on ES (BACKLOG2 item 90)

**Verdict: NO. FOUND 0, LEAD 0.** The composite-signal books on ES have all-in weekly Sharpe -1.73 / -0.51 / +0.05 at bracket multipliers 0.75 / 1.0 / 1.25 (x0.193 x ADR20) and every additive uplift at 10-50% share is negative on H1 and H2; the plain-ES control books are equally negative (-1.05 / -1.09 / -0.25). Composite signals do not rescue the ES books.

Pre-registered in PREREG_AUTOPILOT.md ('BACKLOG2 GROUP L', L90). Construction: composite 1-minute OHLC = 0.5 x (ES + k x NQ) with k = 0.2789 (ratio of mean closes, clean span), NQ forward-filled onto ES minutes; the live ST (ATR 120 / 2.0 / EMA 200 supertrend flip) and HM (HMA 20/55 of close minus session VWAP) signals of d1_f4_core computed on the composite and executed on ES with ES fills, ES ADR20 bracket k = 0.193 x {0.75, 1.0, 1.25} (stop = target), equal R = $9,600 per full stop, independent books, live-style rules (per-book 5R/-2R day, combined day lock 8R/arm 2R/keep 33%, week floor -8R) as in d1_f4_core.account. Fill model: next 1-minute open, 1 tick adverse per side, $4.36 per contract round trip, stop-first on 1-minute bars, flat at the 16:55 ET open. No selection (3 pre-registered cells, all shown). Baseline pair B.Cfg(wk_floor=8, wk_loss_pb=None) in a clean process (1.46 / 2.83 / 2.30).

## Standalone and additive (all 6 books)
| book | k (x0.193 ADR) | trades | Sharpe clean | H1 | H2 | all-in | uplift@10% clean/H1/H2 | @20% | @30% | @50% | wd corr |
|---|---|---|---|---|---|---|---|---|---|---|---|
| composite | 0.75 | 15,358 | -2.06 | -1.99 | -0.70 | -1.73 | -0.24/-0.36/-0.18 | -0.47/-0.70/-0.36 | -0.68/-1.00/-0.53 | -1.05/-1.51/-0.82 | +0.06 |
| composite | 1.00 | 11,419 | -0.21 | -1.25 | -0.74 | -0.51 | -0.09/-0.25/-0.22 | -0.18/-0.50/-0.43 | -0.26/-0.74/-0.62 | -0.42/-1.17/-0.94 | -0.24 |
| composite | 1.25 | 8,902 | +0.71 | -0.80 | -1.09 | +0.05 | +0.01/-0.18/-0.22 | +0.01/-0.37/-0.42 | 0.00/-0.55/-0.61 | -0.03/-0.90/-0.95 | +0.03 |
| plain ES | 0.75 | 15,552 | -0.31 | -2.78 | -2.13 | -1.05 | -0.10/-0.44/-0.30 | -0.20/-0.85/-0.57 | -0.30/-1.22/-0.83 | -0.47/-1.84/-1.28 | -0.01 |
| plain ES | 1.00 | 11,552 | -0.73 | -1.79 | -1.52 | -1.09 | -0.13/-0.32/-0.26 | -0.26/-0.64/-0.49 | -0.38/-0.93/-0.71 | -0.59/-1.45/-1.10 | -0.40 |
| plain ES | 1.25 | 8,952 | +0.23 | -0.16 | -1.73 | -0.25 | -0.03/-0.15/-0.23 | -0.07/-0.30/-0.46 | -0.11/-0.46/-0.67 | -0.20/-0.74/-1.05 | -0.02 |

Random-entry null (40 replicates with the same event counts per book, p95 of the all-in standalone Sharpe): -2.20 / -1.64 / -0.82 at k = 0.75 / 1.0 / 1.25; the composite books are above the null (-1.73 vs -2.20, -0.51 vs -1.64, +0.05 vs -0.82) only in the sense that random entries lose to cost faster, and no book has a positive uplift on H1 or H2. Bootstrap, plateau and 2x slippage are moot (no book has any positive H1/H2 uplift).

## Insurance and constant-risk framing
Not computed: the additive uplift is negative on every span and share, so no constant-risk version can improve CVaR5 or the worst week without a large net loss (INSURANCE would need net cost >= -5%; the books lose money).

## ERA flag
Not available: the d1_f4 ES series on disk (data/databento/ES) starts 2023-02, so the 2013-22 scaled re-test cannot be run for this book; the cost/size context from the B-family ES results is that ES 5-15 minute books lose in every era available (see REPORT_B1: ES median selection Sharpe -5.3 to -1.7 by bar size in 2013-22).

## Executability
ES is a CME contract (NinjaTrader Brokerage via Rithmic expected). The composite signal needs an NQ and an ES data series inside one NT8 strategy (multi-series), doable; nothing passes so no margin decision.

Library: L90_composite_ES_k*, L90_plain_ES_k* saved via lib_save (outputs/library). Code ap_l90.py. Runtime about 40 minutes (HMA rolling on 1M bars dominates).

DONE L90
