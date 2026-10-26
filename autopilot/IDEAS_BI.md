# IDEAS_BI - 25 candidate ideas (worker BK, 2026-10-17), written BEFORE any BI run
Keyword search (LEDGER, GAPMAP, GAPMAP_UPDATES, BACKLOG, BACKLOG2, IDEAS_FV15, PREREG_AUTOPILOT, every REPORT_*.md): hits in brackets; "novel" = no report tests the mechanism. Data for all: 1-minute NQ/ES/RTY/YM continuous series (data/databento, data/autopilot/ohlcv1m), pair rows (ROWS_corrected_engine), VIX/VIX3M daily (data/gap/vix). Sign = predicted sign of the effect from the cited literature (a run against the sign is reported but is not a pre-registered success).
RUN (ten): BI1-BI10 below. NOT RUN (fifteen): reasons given.

| # | idea | mechanism / literature | novelty (keyword hits) | status |
|---|---|---|---|---|
| 1 | Same-half-hour persistence | returns in half-hour h on previous days predict half-hour h today (Heston-Korajczyk-Sadka 2010, intraday periodicity from institutional programmes) ; sign: WITH | novel (0) | BI1 |
| 2 | Overnight/RTH tug-of-war | the overnight return reverses in the next RTH session while the RTH return continues in the next overnight session (Lou-Polk-Skouras 2019, clientele); sign: RTH after overnight AGAINST, overnight after RTH WITH | novel as a two-leg sleeve (overnight drift/gap sleeves exist; the decomposition does not) | BI2 |
| 3 | Intraday NQ/ES(RTY) ratio mean reversion | index futures share one factor; a relative move of one against the other beyond its noise reverts (ETF-arbitrage / pairs literature, Gatev et al. 2006), traded on the lagging-leg; sign: AGAINST (convergence) | novel (hits are pair-limit entries, not ratio MR) | BI3 |
| 4 | High-volume-day next-day premium | days of abnormal volume are followed by positive returns (Gervais-Kaniel-Mingelgrin 2001 high-volume return premium, visibility); sign: LONG | novel (0) | BI4 |
| 5 | Prior-week high/low break or rejection | weekly extremes are stop/limit clusters and institutional anchors (George-Hwang 52-week-high anchoring at the weekly scale); sign: WITH (break continuation) | novel (0) | BI5 |
| 6 | Daily cross-index lead-lag | small-cap/value-heavy indices lead large-cap growth at 1 day (Hou 2007 lead-lag in information diffusion; Lo-MacKinlay cross-autocorrelation); sign: WITH driver | novel (0) | BI6 |
| 7 | Semi-monthly payday windows | payroll/pension inflows around the 1st and 15th lift equity index returns (Ogden 2003 liquidity-cycle hypothesis); sign: LONG | novel (1 hit, TOM only) | BI7 |
| 8 | Range-shock day next-day drift | a day with range >> ATR is followed by a vol-risk-premium/liquidity-restoration drift (Nagel 2012 evaporating liquidity; Bollerslev-Tauchen-Zhou VRP); sign: LONG, or against the shock day sign | novel (0) | BI8 |
| 9 | Overnight vs RTH decomposition filter of the pair | pair entries aligned with a continuing component vs the reversing component of the tug-of-war; overlay; sign: entries aligned with the prior RTH return keep more (UP), aligned with the overnight move less | novel as a pair filter (0) | BI9 (overlay 1) |
| 10 | Time-since-last-flip tilt of the pair | flips arriving soon after another pair entry signal a whipsaw regime (clustering of signals, Hawkes-type order-flow clustering); overlay; sign: short gap -> weaker | novel (0) | BI10 (overlay 2) |
| 11 | Flip-conditioned holding period (time exit) | time stop after a flip | covered (C2-G1 time stops, J0A stagnation stop) | skipped |
| 12 | Flip clustering count tilt | count of entries in 60/120 min | folded into BI10 (gap features) | skipped |
| 13 | VIX term-structure slope next-day | VRP/stress | covered (N3, PX34, J8, PY2) | skipped |
| 14 | Variance risk premium (VIX - RV) | VRP | covered (K9) | skipped |
| 15 | Pre-FOMC drift | Lucca-Moench | covered (G3/N2/C2-G3) | skipped |
| 16 | Pre-holiday drift | | covered (T5/X1) | skipped |
| 17 | First-30 -> last-30 intraday momentum | Gao et al. | covered (C3-H1) | skipped |
| 18 | Realised semivariance asymmetry | Feunou et al. | covered (FV16 I1) | skipped |
| 19 | Lag-1 autocorrelation regime | | covered (SW23) | skipped |
| 20 | Volume-spike bar continuation | | covered (SW6, Q15) | skipped |
| 21 | Opening-range breakout | Crabel | covered (113 hits) | skipped |
| 22 | NR7/inside-day breakout | | covered (34/17 hits) | skipped |
| 23 | Connors streak / RSI2 reversal | | covered (40 hits) | skipped |
| 24 | Dollar-neutral NQ-ES spread (two legs) | pairs | needs a two-leg harness; BI3 trades the single lagging leg instead | deferred |
| 25 | Hour-of-day return seasonality (pure) | data-mining prone, no mechanism beyond BI1 | skipped |

## Grids, frozen (ten runs)
Pipeline for BI1-BI8: the SW sleeve pipeline (clean-only selection: >= 100 clean trades (MINTR 60 for the daily-cadence BI4-BI8, small-sample flag < 100), weekly Sharpe > 0 in BOTH clean halves, top 10 per instrument; H1/H2 read once; own random-entry null (200 replicates on the selected cell, 200 replicates of the whole-grid false-selection test); additive framing at 10/20/30/50% with bootstrap, worst-decile corr, plateau +-25%, 2x slippage, ERA flag with gross / net fixed / net price-scaled cost; instruments ES NQ RTY YM (cross-instrument replication is built in: a cell that is a LEAD on one instrument is read on the others in the table); sizing: 1 contract scaled to the pair's clean weekly sigma). Fill: signal at bar close, entry next 1-min open, 1 tick/side + $4.36/contract; time exits at the open of the exit minute. Replication leg: H0 2023-02..07 and alternating-month split computed for any LEAD by ap_bi_rep (reported when needed).
- BI1: slots start {09:30,10:00,...,15:00} (13) x K prior days {1,5} (mean of the same-slot 30-min open-to-close return) x dir {with, against}; hold 30 min; 52 cells. Neighbours: K x0.75/x1.25 (rounded).
- BI2: leg RTH (entry 09:30, sign of the prior Globex return 18:00-09:29; hold {120 min, flat 16:55}) or ON (entry 18:00, sign of the prior RTH return 09:30-15:59; hold until 09:25 = 925 min) x threshold {0, 0.15 x ATR20 of RTH range} x dir {with, against}; 12 cells. Neighbours: threshold x0.75/x1.25, hold x0.75/x1.25 (RTH 120 only).
- BI3: L {30,60,120} min x thr {1.5,2.5} (|own_move - driver_move| in own sigma units, move z as ap_sw_common.own_move/driver_move; driver ES for NQ/RTY/YM, NQ for ES) x H {15,30,60} x dir {against, with}; crossing events only; 36 cells. Neighbours: L, thr, H x0.75/x1.25.
- BI4: day volume (label-day sum) percentile among the previous N label days {20,60} >= p {80,90} x mode {long, with-day-sign, against-day-sign}; enter next RTH open, hold flat; 12 cells. Neighbours: p +-10 points (70/90, 80/100 clipped) and N x0.75/x1.25.
- BI5: level = prior ISO-week high (long break / short fade) or low (short break / long fade); event = first 1-min close beyond level +- b x ATR20(range) during RTH 09:35-15:30; b {0,0.1} x dir {with, against} x hold {60,120,flat}; 12 cells. Neighbours: b x0.75/x1.25 (b=0: +0.05), hold x0.75/x1.25.
- BI6: driver {RTY,YM} (target ES/NQ; ES,YM for RTY; RTY,NQ for YM) prior label-day RTH return z (/ 20d sd) with |z| >= th {0,0.5} x dir {with, against} x hold {flat, 120 min}; entry next RTH open; 16 cells. Neighbours: th x0.75/x1.25 (0.5 only), hold x0.75/x1.25.
- BI7: anchor {1st trading day of month, first trading day on/after the 15th} x offset k {-1,0,+1} trading days x hold {flat (open to close), 2 days} x dir {long, short}; 24 cells. Neighbours: hold only (2d -> 1.5 not defined; offset +-1 as neighbours).
- BI8: range/ATR20 of the previous label day >= x {1.5,2.0} x mode {long, with-day-sign, against-day-sign} x hold {flat, 2 days}; 12 cells. Neighbours: x x0.75/x1.25.
- BI9 (pair overlay 1): states at the entry (strictly before): ON = (price at entry minute-1 / last RTH close - 1) / ATR20-of-RTH-range-in-%; RTHP = (last completed RTH close / its open - 1) / same; features side x ON and side x RTHP; terciles frozen on clean; schemes COUNTER_DOWN / ALIGN_UP / TWO; 6 cells; ES/RTY cross-leg via ap_bk_xi-style harness. Neighbours: share 25/42% and ATR window 15/25.
- BI10 (pair overlay 2): features g1 = -ln(minutes since the previous entry of the same book), g2 = -ln(minutes since the previous entry of either book), g3 = -ln(minutes since the previous entry in the opposite direction) (all from earlier rows only); tercile edges frozen on clean; schemes HIGH_DOWN (short-gap tercile x0.5) / HIGH_UP (x1.5) / TWO_V; 9 cells; ES/RTY cross-leg likewise. Neighbours: share 25/42%.
Priors: each <= 3% for FOUND. Expected false FOUND across ten ~0.1-0.3.
