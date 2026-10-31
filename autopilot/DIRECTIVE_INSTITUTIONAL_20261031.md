# DIRECTIVE T-INSTITUTIONAL (user, 2026-10-31 ~16:00Z), saved verbatim

T-INSTITUTIONAL — what the ledger does NOT contain yet: the things a desk uses that we have not scored; one deep, pre-registered pass (user, 2026-10-31 ~16:00Z)

Research only. PLAN36 rules + QUANT-LAYER on every candidate; prereg per section with sha256 before scoring; PRE+X' selection, ONE recent look; dead cells; placebos named per section; per contract first, session column, measured fills; the T-SIXTY three columns (STRICT / TOLERANT / NOW-ONLY) on every result; rows to RECENT_WINS. Runs after T-SIXTY section 1 in the 80-90% order; interim by Sun 12:00Z, then it continues past the deadline as a standing program (the user is not stopping on Sunday). First step of every section: a DATA line — what is on disk, what is derivable, what must be bought (quote, no purchase without the user's OK).

Why (read the ledger first)

RECENT_WINS today is 857 visible rows / 14,741 ledger rows from these families: candle confirmations, L2 entry/exit gates, policy rules, stack partials, zones, trend terciles, signal decay, meta-labels, structure sleeves, splits, dip entries, lot factors, ensembles. Every one of them is a rule about OUR signal and OUR trade. Almost nothing in the ledger describes WHO ELSE is in the market and what they have to do — which is what an institutional desk actually trades around. That is the gap. Sections below are ordered by how likely the data is on disk.

A. Auction / market-profile day structure (derivable from the 1-min and 1-s data on disk)

Initial balance (first 60 min of RTH, and 30-min variant); open location vs the prior day's value area (above / inside / below VA; VA = 70% of volume-at-price of the prior RTH day; also vs the prior day's range and the overnight range); IB extension (price trades beyond IB by 0.5 / 1 / 2 × IB); day type ex-ante at 10:30 / 11:00 (trend / normal-variation / neutral / non-trend by the classic IB rules); single prints and poor highs/lows (unfinished auction) as targets and as no-fade zones; the overnight inventory (ON session VWAP vs open: long/short inventory that must be corrected). Score each as (i) a REGIME for the live books (which books to run / size at 10:30 by the day type), (ii) a TARGET chooser (the opposite VA edge / the prior poor high), (iii) a STANDALONE book (open-outside-value → trade back to value; IB break with ON-inventory agreement; the "80% rule"). Placebos: shuffled prior-day values; time-shifted IB.

B. Institutional execution footprints (derivable from the tape and mbp-10)

Working algos (VWAP / TWAP / POV) leave persistent, same-signed aggressor volume with small prints at a steady rate. Build the detector: rolling 5 / 15 / 30-min signed-volume autocorrelation, run length of same-sign minute deltas, participation rate (aggressor volume / total) stability, print-size distribution (many small vs few large), re-loading at a price (the iceberg family already scored, re-used). State = "an institutional buyer/seller is working" with confidence. Score: (i) as a direction filter for the live books (only take signals WITH the working algo; skip or size down against), (ii) as a standalone "ride the algo" book (enter with it on pullbacks to its average price, exit when the footprint stops), (iii) the END of the footprint as an exit/reverse signal. Placebos: shuffled minute deltas within the day; time-shifted state. Also the MOC: the 15:50-16:00 imbalance behaviour (direction of the 15:30-15:50 move vs the close) as a close-window book and as a reason for the 14:40-15:00 skip the Sunday brief found.

C. Cross-market state at minutes-to-hours (not the seconds lead-lag already scored)

NQ vs ES relative strength over 30 / 60 / 120 min (beta-adjusted residual, z-score) as a regime: NQ-led days vs ES-led days vs divergence days; RTY and ZN (on disk) as risk-on/off confirmation; the NQ/ES residual mean reversion as a standalone pair book (ratio z ≥ 2 → fade the residual with the two legs; is it tradeable at our costs); gold/oil/bonds direction at the NY open as a day-type input; the DXY if derivable. Score per live book: do NQ signals pay more when ES/RTY/ZN agree at the HOUR scale (not the second)? Placebos: time-shifted cross-market series.

D. Volatility-market state (options data: INVENTORY FIRST — likely a purchase)

Dealer gamma regime (positive gamma → pinning/mean-reversion, negative → trending), 0DTE flow proxies, VIX/VXN term structure, implied vs realised vol spread, the opex / monthly expiration cycle, vol-of-vol. If options data is not on disk: (i) quote the cheapest source (CBOE/Databento options summary; daily GEX proxies are small), (ii) meanwhile build the REALISED proxies — intraday mean-reversion strength (variance ratio at 5/30 min), range compression, the open-to-10:30 realised vol vs the implied-equivalent from the prior day's range — and score them as the regime for trend vs fade books. Deliver the quote and the proxy results; the user decides on the purchase.

E. Cash-market lead (equities data: INVENTORY FIRST)

QQQ / SPY NBBO and the top-10 NDX names (NVDA, AAPL, MSFT, AMZN, META, GOOGL, AVGO, TSLA …): index-arb basis deviations, the cash open (09:30:00 prints) vs futures, breadth of the leaders at the open (how many up on the first 5 min), the leader that moves first. If not on disk: quote one month of QQQ + 10 names mbp-1 (Databento XNAS.ITCH) and state what the test would be; do not buy.

F. Flow calendar (release calendar exists; extend)

Month-end / quarter-end rebalancing windows (last 2 days, 15:00-16:00 flows), index rebalance days (NDX quarterly, Russell June), the roll week (NQ expiry: volume migration, basis moves, the Thursday roll), Treasury auction 13:00 settlements, Fed blackout vs speaker days, the opex Friday morning; TWAP-heavy windows (the 10:00 and 15:00 "institutional clocks"). Score each as a state for the live books (take / skip / size / re-bracket) and as a close-window book where the window itself has drift. Placebos: shuffled calendar days of the same weekday.

G. Order-flow toxicity as a sizer (mbp-10 on disk; extends the L2 cycles)

VPIN / bulk-volume toxicity at 50-contract buckets, multi-level OFI (Cont), the trade-to-book ratio, cancel ratio (cancels / adds per minute = spoof-like activity), hidden-liquidity rate (prints inside the spread or beyond the displayed size): as a REGIME for sizing all books (toxic tape → half lots; quiet informed tape → full) and as a stop-placement input (do not rest the stop where the cancel ratio is extreme). Report IC per feature at 1 / 5 / 30 min horizons and the sizer's stack line with the running-max locks.

H. Minute-of-day alpha (derivable)

The return and vol surface by minute-of-day × day-of-week over 2023-26 (the desk's "time-of-day" sheet): where the drift is, where the vol is, where the books' signals pay; the live books' brackets re-scaled by the minute-of-day vol (a 60-pt stop at 09:35 is not a 60-pt stop at 13:00); entries shifted to the drift minutes. Walk-forward (fit on the trailing 6 months, score the next month). Placebos: shuffled minute labels.

I. Robustness standard for THIS program (stricter because the families are new)

Every section: PRE+X' selection with ONE recent look; purged k-fold with embargo on the standalone books; the shuffled-state and time-shifted placebos; the 1-s / 3-s decision delay; capacity (mbp-10 depth at the fire seconds); the TOLERANT gate from T-SIXTY as the headline tier, STRICT and NOW-ONLY beside it; per session; the stack line on the SS-2 engine at live lots with the D6 running-max locks; the persistence score and shrunk size for every row that enters the ledger; dead cells logged. Nothing promoted; everything labelled; the forward-register row written for anything TOLERANT-positive.

J. Report

DS3_INST_<section>.md per section as they land (DATA line first), DS3_INSTITUTIONAL.md as the rolling summary with one plain sentence per section ("working-algo footprint: a buyer is detectable X% of RTH minutes; signals with him pay +Y per contract vs −Z against, L6M, placebo rank W; as a filter on the stack +$k/wk"), a PURCHASE table (source, slice, cost, what it unlocks) for the user's OK, rows to RECENT_WINS, a section in the Sunday brief v6 for whatever has landed, MORNING.md every 2 h. The program does not stop at the Sunday deadline.
